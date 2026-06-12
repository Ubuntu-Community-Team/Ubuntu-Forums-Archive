---
title: "How to configure syslog/script to generate email in case of critical issue"
date: 2014-02-20
forum: Ubuntu, Linux and OS Chat
---

### Post by waqas2 on 2014-02-20
Hello ! Everyone! I am very new to linux so need you strong support in this. 


I wanted my linux system to have such script/syslog server that it first telnet into my other system and then execute one command (eg. netstat -an) and if system found their anything with "syn_sent" it should generate an immediate email or some sms. 


Please help to configure such thing


thanks !

---

### Post by TheFu on 2014-02-20
Welcome to the forums.

Telnet is dead for remote access. Only ssh should be used. Telnet is fine for checking remote services are alive, but not for anything with a login.

Linux has a different philosophy than other OSes. Understanding that difference sooner than later will help you solve problems.
[http://blog.jdpfu.com/2012/02/15/beginning-linux-thought-shift-needed](http://blog.jdpfu.com/2012/02/15/beginning-linux-thought-shift-needed) tries to explain.

The parts to the solution are: rsyslog, any MTA (postfix, qmail) and any CLI email client (Mail, pine, alpine, elm, mutt, ...)

Use ssh to run remote commands: **ssh user@server "command optA optB"** It is better if you setup key-based authentication.

Putting the pieces together to make a total solution is how we do it. Sometimes it seems like a hassle, until you've built something from 20 little tools that is completely custom to your needs.
I cannot provide more details for your needs and hope this guidance will get you pointed in the right direction.

---

### Post by SeijiSensei on 2014-02-20
If you want to log traffic, you should learn how to write [iptables rules]("https://help.ubuntu.com/community/IptablesHowTo").  The "LOG" target reports matching packets to syslog.

---

### Post by Lars Noodén on 2014-02-20
Putting togeter little tools to solve a task is the basis of shell scripting.  With this case, it looks like you can focus on two subtasks and then combine them when you have them running.  

One is sending the mail.  On a classic server system with a static ip address and a full set of DNS records, it is fairly simple.  

```

echo "Some warning" | mail -s "heads up" foobar@example.org

```

However, if you do not have such a set up, then you might have to use mutt or similar and go via an outside SMTP server where your client actually has to authenticate.  

The other subtask is running netstat remotely.  IMHO that's pretty easy, even if you  use keys for log in.  

```

ssh user2@xx.yy.zz.aa 'netstat -t | grep -q SYN_SENT'
ssh -i ~/.ssh/mykey user2@xx.yy.zz.aa 'netstat -t | grep -q SYN_SENT'
ssh -i ~/.ssh/mykey user2@xx.yy.zz.aa 'netstat -t | grep -q SYN_SENT' && echo "Send some mail"

```

---

### Post by TheFu on 2014-02-20
Reread the OP - If you want a quick and easy monitor for your log files, check out **logwatch**. You'll still need to setup an MTA or some sort of alarming tool like nagios or OpenNMS.  With those tools, you'd be writing plugins.  Much easier than all the home-grown infrastructure stuff for a normal business.

---

