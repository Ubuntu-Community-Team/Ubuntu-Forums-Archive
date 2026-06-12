---
title: "PHP execute shell command"
date: 2009-04-01
forum: Server Platforms
---

### Post by mha2908 on 2009-04-01
I've got an Apache2-server with PHP5 installed on Ubuntu Server 8.10. I've tried to run the exec(), shell_exec() and system()-commands with the 'killall java' as the command. Nothing happens. If i type 'whoami' instead it writes out "www-data". How can I give PHP root-access?

Plz tell me in a very understandable language or with an easy guide, as I am NOT very good at Linux.

---

### Post by drubin on 2009-04-01
Hi 

Firstly this is a bad idea. Giving root access to a web scripting lang is asking for a hack attempt on your PC/server.

If you really REALLY and I mean REALLY need this type of access... google apache change users.

But this isn't recommend or approved in any way so I am not going to post the result here.

But maybe a better solution would be run those applications under www-data?

---

### Post by mha2908 on 2009-04-01
Then how will I be able to run the "killall java" from my family-intranet which is protected with .htaccess and .hpasswd? Is there any way to make this possible?

---

### Post by drubin on 2009-04-01
What java application are you wanting to kill? Maybe a better solution would be to let php start that application (it will then have ownership) and then only allow it to kill that proccess id?

Is this is on your inranet.. and doesn't have external access. I would recommend you looking in /etc/apache/envvars if you change, but I still wouldn't recommend using root. 
[PHP]export APACHE_RUN_USER=www-data
export APACHE_RUN_GROUP=www-data[/PHP]

---

### Post by mha2908 on 2009-04-01
simplifying the question: I wanne be able to kill my Vuze from inside an intranet based on PHP. No matter HOW, I just want it to! The vuze-process is run as root as a daemon at start-up ([http://azureuswiki.com/index.php/HeadlessSwingUIAtBoot](http://azureuswiki.com/index.php/HeadlessSwingUIAtBoot)). HOW?

---

### Post by drubin on 2009-04-01
Ok do you use it for a torrent application? Maybe it would be better to run a command line torrent application and just ssh into the server? Would this be an option or does it have to be web bassed. (My solution will still be allowed to stop it via the internet/lan but not from a browser)

---

### Post by mha2908 on 2009-04-01
i am already ssh'ing into the server. But my family is using the torrent-app, too... And there's other commands i wanna try out, so please tell me how to give PHP the correct access...

---

