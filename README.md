# F062 vue+flask 知识图谱抑郁症心理健康问答系统|neo4j

>完整项目收费，可联系QQ: 81040295 微信: mmdsj186011 注明从github来的，谢谢！
也可以关注我的B站： 麦麦大数据 https://space.bilibili.com/1583208775
>关注B站，私信获取！ 
>编号: F062     [麦麦大数据](https://space.bilibili.com/1583208775)

## 1 前言
抑郁症已经成为当今社会刻不容缓需要解决的问题，抑郁症的危害主要有以下几种：1.可导致病人情绪低落：抑郁症的病人长期处于悲观的状态中，感觉不到快乐，总是高兴不起来。2.可导致工作、学习能力下降：抑郁症的患者会出现思维迟缓、反应迟钝、记忆力下降，严重影响工作和学习能力。3.可导致睡眠障碍：抑郁症患者会出现入睡困难或者早醒等睡眠问题。4.可导致各种躯体不适：抑郁症病人常出现头痛、头晕、全身疲乏，食欲减退等症状。抑郁症还会导致厌世倾向，所以说危害是非常大的，那么构建一个抑郁症的知识图谱是很有意义的。
        本文系统主要从各个类型的抑郁症的症状、发病原理、诊断、可以吃什么食物、不宜吃什么食物入手，构建了一个知识图谱，同时在此基础上做了一个简单的问答系统。下面主要从技术、实现功能和问答系统来介绍一下系统。
## 2 演示视频
[video(video-Nkl4Grtl-1691991873975)(type-bilibili)(url-https://player.bilibili.com/player.html?aid=786884300)(image-https://i-blog.csdnimg.cn/blog_migrate/132f97c05dbb45fb96fbeedcba902d2a.jpeg)(title-基于vue+django的 抑郁症知识图谱与问答系统)]

## 3 架构介绍
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/5af8733c79ab46a3b337d9ebbb6e0ee2.jpeg)
### （1）主要技术栈   
 vue + flask + mysql + neo4j 
●vue.js 、 axios
●d3.js（图谱）
●flask、sql-alchemy
●LTP

## 4 实现功能
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/187e34a579594db3af837a1ba434aaec.jpeg)
●抑郁症的知识图谱、模糊检索功能
●问答系统、支持的见第三部分
●修改个人信息、修改头像、短信验证码方式修改密码
●登录与注册、退出登录

### 4.1 支持的问答方式举例
问题：躁狂抑郁症的典型症状？
回答：躁狂状态,哮喘,抑郁状态,心血管疾病,多发性硬化,偏头痛
问题：抑郁症的三大症状？
回答：运动抑制,思维迟缓,情绪低落
问题：绝经与抑郁症的发病原理是什么？
回答：生物学原因,社会心理学假设
问题：抑郁症的诊断
回答：有主动治疗要求,有精神因素诱发,伴有焦虑症状,以往没有发作间歇,无严重的自责,心境抑郁为主要症状,无体重减轻厌食等生物学症状,病前有抑郁性格,无妄想幻觉等精神病性症状,精神运动性抑制不明显
问题：产后期抑郁症忌吃什么？
回答：羊肉,鳗鱼,螃蟹
问题：产后期抑郁症宜吃什么？
回答：坚果类,葵花子,木瓜,优质肉类,深绿色蔬菜,全麦,瘦肉,香瓜,柑橘类,南瓜子,酪梨,花生,蘑菇,谷类,绿色蔬菜,荔枝,豌豆,空心菜,红豆,核桃,马铃薯,猪肉,草鱼,深海鱼,动物肝,麦芽,酵母粉,香蕉,牛奶,番茄
问题：产前抑郁症的治疗方法？
回答：物理治疗,产前抑郁症心理治疗,家人的理解和关心,增强产妇的体质,药物治疗    
### 4.2 登录与注册
登录注册做的是一个可以切换的登录注册界面，点击“去登录”或“去注册”可以切换界面。登录需要验证用户名和密码是否正确，后端通过 Flask-Login 或 JWT 实现会话认证，确保用户身份安全。注册时对用户名唯一性、密码强度进行检查，并将用户信息加密存储于数据库中。
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/d996e1e5f72b4cee8cc165dcfd900e09.png)
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/94f308d18034408cb1df9442b9f3598d.png)
### 4.3 心理知识图谱的构建与导入
本系统从心理学知识文本中提取实体（如心理疾病、症状、治疗方法、心理学流派）和关系（如“患有”、“治疗”、“属于”），构建心理知识图谱。使用 Neo4j 的 APOC 插件或 Python 的 neo4j-driver 库，将结构化的 JSON 或 CSV 数据批量导入图数据库，建立节点（Node）与关系（Relationship）。
重要节点：Disease（疾病）、Symptom（症状）、Treatment（治疗方式）、Theory（心理学理论）
重要关系：HAS_SYMPTOM（患有）、TREATS（治疗）、BELONGS_TO（属于）
数据导入脚本示例使用Python + py2neo 实现批量添加节点与关系。
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/241eceed87664c7f9479292648c6df9a.png)
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/ac1fe82be844491ca47d2761eb7d36f2.png)
### 4.4 图谱可视化展示
前端使用 Neo4j 的原生图谱可视化工具（如 neo4j-browser 或 GraphInsight），或基于 Cytoscape.js、D3.js 构建自定义网页图形展示界面，实现心理图谱的动态渲染。用户可点击节点查看详细信息，拖拽调整布局，通过图谱探索心理知识的关联结构。
可视化功能支持：
图谱缩放、拖拽
节点高亮与颜色分类
关系路径展示
搜索功能定位实体节点
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/17cf9edad362445b8a7f38226bec92d7.png)
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/07d527de47db4626b484393191fc8caf.png)
### 4.5 心理问答系统
用户通过前端输入心理问题（如“抑郁症有哪些症状？”），系统解析问题关键词，转化为 Cypher 查询语句，提交至后端查询 Neo4j 数据库。
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/11fe102fd9c54be5b32198fb03ee5b9f.png)
### 4.6 个人设置
个人设置方面包含了用户信息修改、密码修改功能。
用户信息修改中可以上传头像（支持 .jpg/.png 格式），完成用户的头像个性化设置，也可以修改用户其他信息，如昵称、性别、职业等。
修改密码需要输入用户旧密码和新密码，验证旧密码成功后，就可以完成密码修改，使用哈希加密存储新密码。
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/24cbe2a6bb804e90aa1ed12f9cba437a.png)
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/b9465d96e68447efba902402a1d40481.png)
### 5 代码说明
核心流程包括：
用户输入问题 → 前端提交至后端
后端解析关键词 → 生成Cypher查询语句
调用Neo4j执行查询 → 返回结果集
前端展示结构化问答结果
关键算法包括：关键词提取 + 实体识别 + 图谱查询生成 + 结果解析

4.2 流程图

4.3 代码实例
```python
# 后端：Flask 端点处理心理问答请求
from flask import Flask, request, jsonify
from neo4j import GraphDatabase
import json
app = Flask(__name__)
# Neo4j 配置
NEO4J_URI = "bolt://localhost:7687"
NEO4J_USER = "neo4j"
NEO4J_PASSWORD = "12345678"
driver = GraphDatabase.driver(NEO4J_URI, auth=(NEO4J_USER, NEO4J_PASSWORD))
def execute_cypher(cypher_query):
    with driver.session() as session:
        result = session.run(cypher_query)
        return [record.data() for record in result]
@app.route('/api/answer', methods=['POST'])
def get_answer():
    data = request.get_json()
    question = data.get('question', '')
    
    # 简单关键词提取（可扩展为NLP分词）
    keywords = extract_keywords(question)
    
    # 动态生成Cypher查询
    cypher = generate_cypher(keywords)
    
    if cypher:
        answers = execute_cypher(cypher)
        return jsonify({"success": True, "answers": answers})
    else:
        return jsonify({"success": False, "message": "无法识别问题"}), 400
def extract_keywords(txt):
    # 示例：提取关键词（可后续接入jieba/NLTK）
    keywords = [word for word in txt.split() if len(word) > 1]
    return keywords
def generate_cypher(keywords):
    # 根据关键词生成Cypher查询
    if "症状" in keywords:
        return "MATCH (s:Symptom) RETURN s.name"
    elif "治疗" in keywords:
        return "MATCH (t:Treatment) RETURN t.name"
    elif "疾病" in keywords:
        return "MATCH (d:Disease) RETURN d.name"
    else:
        return None
<SQL>
-- Neo4j 图谱创建语句示例
CREATE CONSTRAINT ON (d:Disease) ASSERT d.name IS UNIQUE;
CREATE CONSTRAINT ON (s:Symptom) ASSERT s.name IS UNIQUE;
CREATE CONSTRAINT ON (t:Treatment) ASSERT t.name IS UNIQUE;
// 示例：添加疾病节点和关系
CREATE (d:Disease {name: "抑郁症"}) 
CREATE (s:Symptom {name: "情绪低落"}) 
CREATE (d)-[:HAS_SYMPTOM]->(s) 
CREATE (t:Treatment {name: "认知行为疗法"}) 
CREATE (d)-[:TREATS]->(t)
```

>文章结尾部分有CSDN官方提供的学长 联系方式名片
>文章结尾部分有CSDN官方提供的学长 联系方式名片
>关注B站，私信获取！ 
>
>编号: F062     [麦麦大数据](https://space.bilibili.com/1583208775)
