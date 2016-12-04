# cc98 Crawler

## Snapshot
![Snapshot](https://raw.githubusercontent.com/zjuchenyuan/cc98/master/doc/snapshot.jpg)

## Language
Python3

## Requirement
`pip3 install bs4 requests pymysql`

## Manual

> * 持续性获取最新的帖子

    screen -S cc98
    while [ '1' = '1' ]; do python3 xinling.py; sleep 233; done

> * 获取一个版块(如校园信息100)的历史所有发帖

    python3 xinling.py 100
    
> * 获取全部发帖，注意修改源代码中的workset

    python3 xinling.py all

## Note
EasyLogin is another my project.

Don't forget to turn on the mysqld: `service mysqld start`(Centos) or `service mysql start`(Ubuntu)

In this public version, credentials are hidden in config.py:

1. COOKIE: a dict of name and value in cookies

2. db(): return a database connection

3. myip: randomly choose a source ip for tcp connection, you need to obtain these ip first ^.^

example code for config.py:

    #Example Code for config.py
    import random,pymysql
    COOKIE = {'aspsky':'SOMETHING CREDIENTIAL','BoardList':'BoardID=Show',}
    def db():
        global conn
        conn = pymysql.connect(user='root',passwd='123456',host='localhost',port=3306,db='cc98',charset='utf8',init_command="set NAMES utf8")
        conn.encoding = "utf8"
        return conn
    myip='10.1.2.{}'.format(random.randint(66,99))  #randomly choose a source ip for crawler


## Credits
https://github.com/aploium/mpms

## LICENSE
"Anyone But duanduan"(ABd) license

