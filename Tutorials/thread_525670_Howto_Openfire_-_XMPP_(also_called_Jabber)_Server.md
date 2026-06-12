---
title: "Howto: Openfire - XMPP (also called Jabber) Server"
date: 2007-08-14
forum: Tutorials
---

### Post by handband2 on 2007-08-14
**[SIZE="3"]Installing openfire[/SIZE]**
[http://www.igniterealtime.org/projects/openfire/index.jsp](http://www.igniterealtime.org/projects/openfire/index.jsp)

**[SIZE="2"]Install Ubuntu 6.06 LTS LAMP[/SIZE]**
Recommended sites to setup your LAMP server:
[http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)
[https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP](https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP)

Check which version of Java you are running.  [COLOR="Red"]Note the following: the .tar.gz build does not contain a bundled Java runtime (JRE). Therefore, you must have JDK or JRE 1.5.0 (Java 5) or later installed on your system. You can check your java version by typing "java -version" at the command line and (if necessary) upgrade your Java installation by visiting [http://java.sun.com](http://java.sun.com).)[/COLOR]

Java 6 is available for 6.06 LTS via the "backports" repository. If this is a fresh install of Ubuntu, you will need to edit your SOURCES.LIST to enable this repository.
```
$ sudo vi /etc/apt/sources.list
```
Uncomment the following line(s):
Default source.list.
```
# deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
```
Uncommented.
```
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
```
Update system.
```
$ sudo apt-get update
```
Install java6.
```
$ sudo apt-get install sun-java6-bin
```
Check java versions on your system.
```
$ java -version
```
Install java6 If you don't have java already installed.
```
$ sudo apt-get install sun-java6-bin
```
Configure Java. 
```
$ sudo update-alternatives --config java
Select java6 for your default.
[COLOR="Red"]**select /usr/lib/jvm/java-6-sun/jre/bin/java**[/COLOR]
```
To create a database for openfire MySQL, Oracle, Microsoft SQLServer, PostgreSQL, IBM DB2, or HSQLDB can be used.  I chose MySQL since it was installed with my LAMP setup.  

Now use phpmyadmin or the terminal to create the database.  The following is through the terminal.

Login as root
```
$ su
```
Login to MySQL
```
# mysql
```
or the following if you setup a user and a password.
```
# mysql -u [COLOR="Red"]USERNAME[/COLOR] -p
```
Create the database in MySQL
```
# mysql> CREATE DATABASE openfire;
```
```
# mysql> exit
```
Download Openfire to a directory.  I chose the /opt/ directory.
```
# cd /opt
```
Download File or go here to get the most recent: [http://www.igniterealtime.org/downloads/index.jsp#openfire](http://www.igniterealtime.org/downloads/index.jsp#openfire)
```
# wget http://www.igniterealtime.org/downloadServlet?filename=openfire/openfire_3_3_2.tar.gz
```
```
# mv downloadServlet\?filename\=openfire%2Fopenfire_3_3_2.tar.gz openfire_3_3_2.tar.gz 
```
Extract the files.
```
# tar -zxvf openfire_3_3_2.tar.gz
```
Create a symlink
```
# ln -s /opt/openfire/bin/openfire /etc/init.d/
```
Make the symlink executible
```
# chmod +x /etc/init.d/openfire
```
Add openfire to our startup.
```
# update-rc.d openfire defaults
```
Fix the nohup output.
```
# vim /opt/openfire/bin/openfire
```
Modify openfire script with the following: **>../logs/SDTOUT.log 2>../logs/SDTERR.log** into /opt/openfire/bin/openfire

ORIGINAL:
```
nohup "$app_java_home/bin/java" -server -Dinstall4j.jvmDir="$app_java_home" 
-Dexe4j.moduleName="$prg_dir/$progname" $INSTALL4J_ADD_VM_PARAMS 
-classpath "$local_classpath" com.install4j.runtime.Launcher start 
org.jivesoftware.openfire.starter.ServerStarter false false "$prg_dir/../logs/stderror.log" 
"$prg_dir/../logs/stdoutt.log" true true false "" true true 0 0 "" 20 20 "Arial" "0,0,0" 8 500 
"version 3.3.2" 20 40 "Arial" "0,0,0" 8 500 -1 -DopenfireHome=$app_home 
-Dopenfire.lib.dir=$app_home/lib &
```
Goto line **262** of **/opt/openfire/bin/openfire** and insert the following at the end of **nohup ....** with **>../logs/STDOUT.log 2>../logs/STDERR.log**

MODIFIED:
```
nohup "$app_java_home/bin/java" -server -Dinstall4j.jvmDir="$app_java_home" 
-Dexe4j.moduleName="$prg_dir/$progname" $INSTALL4J_ADD_VM_PARAMS 
-classpath "$local_classpath" com.install4j.runtime.Launcher start 
org.jivesoftware.openfire.starter.ServerStarter false false "$prg_dir/../logs/stderror.log" 
"$prg_dir/../logs/stdoutt.log" true true false "" true true 0 0 "" 20 20 "Arial" "0,0,0" 8 500 
"version 3.3.2" 20 40 "Arial" "0,0,0" 8 500 -1 -DopenfireHome=$app_home 
-Dopenfire.lib.dir=$app_home/lib **[COLOR="Red"]>../logs/STDOUT.log 2>../logs/STDERR.log[/COLOR]** &
```
Now lets start Openfire (xmpp-server).  Restart or run the following command to start Openfire:
```
# /opt/openfire/bin/openfire start
```
**Now setup the rest of Openfire through your browser.  **
[http://localhost:9090](http://localhost:9090)

---

### Post by proactiv3 on 2007-08-21
Great tutorial.

I have a question, though. I manage the IT department of a small company (in fact I am the department :???:). Until some months ago we were an 100% **Microsoft** based company, exception made for the creative department that uses **Macintosh**.

My boss asked me to put together a small intranet **Wiki** and I saw the perfect opportunity to give Linux a try (I hate IIS). I installed **Ubuntu**, **Apache**, **MySQL** and **PHP** on an old machine, gave it a static **IP** and it has been functioning since then as an internal Web Server.

Thus I'm loving the experience and the server has had absolutely no problem since then, there are still many co-workers of mine reluctant to accept GNU\Linux as a possible alternative to the Microsoft monopoly (which represents to us an massive investment, just in software licensing).

Today it was given me the chance to, once more, prove the value of this kind of operating system: it was asked me to start an internal instant messaging server. I chose to create the IM server in that same **Ubuntu** machine and I went for an open-source solution: **OpenFire** (once again there are many people relutant to accept this solution as a good solution: there's a mentality that if it's free, it can't be that good).

Because I'm new to this world, I'm having serious difficulties. I've found no relevant documentation in the **Ignite Realtime** foruns, and I started looking in the **Ubuntu Foruns**.

I followed this tutorial (in fact it's very similar to the instructions given by the software creators) and successfully completed all steps, except the last one.

I can't open the **OpenFire** setup page: I assume that it's because I'm running **Apache**. When I type the give URL, it just says that Firefox couldn't connect to the server...

Help would me much appreciated. I've tried to search both Google and the Forum in several different ways, but I found nothing relevant. Once again I'm a complete n00b, so simple language and an explanation to what I'm in fact doing would also be much appreciated.

---

### Post by handband2 on 2007-08-21
poractiv3,

First lets see if OpenFire (xmpp-server) is running.

```
$ sudo netstat -tap
```

You should find the following in the outputted list:
```
tcp6       0      0 *:xmpp-server           *:*                     LISTEN     3729/java           
```

More than likely your PID (the 3729 number) will be different.

If nothing shows up then that means Openfire is not running.  If that is the case restart the server or just start up Openfire with the following command:
```
$ sudo /opt/openfire/bin/openfire start
```

I hope that helps....

---

### Post by proactiv3 on 2007-08-22
Oops! :lolflag:

In fact it wasn't running... Thanks for your time and help. Problem solved.

I'm starting out, sorry for the newbie question.

Regards

---

### Post by handband2 on 2007-08-22
> **proactiv3 said:**
> Oops! :lolflag:

In fact it wasn't running... Thanks for your time and help. Problem solved.

I'm starting out, sorry for the newbie question.

Regards

I'm glad you got it working.  It wasn't a newbie question.  I forgot to add how to start up the xmpp server.  I'll update the howto.

---

### Post by D_2 on 2007-08-29
Anyone know how to get to the admin page other than using [_[COLOR=#bd5900]http://localhost:9090[/COLOR]_]("http://localhost:9090/") I have this on my Ubuntu server that isn't connected to a monitor so I use Putty to get to it and I did try links to get to it but that did get me to the pages but it was kind of hard to read and so i am trying to find a way to get to the page other than using [_[COLOR=#bd5900]http://localhost:9090[/COLOR]_]("http://localhost:9090")
I did try IP of that box (192.168.1.5:9090) but it didn't work.

---

### Post by cdrappier on 2007-08-30
when I do this command: 
```
nohup ls >ls.log 2>&1 &
```
I get this output: 
```
-bash: ls.log: Permission denied

[3]-  Exit 1                  hup ls > ls.log 2>&1 

```
how can i fix it?

also, the nohup.out file has alot of these in it: 
```
java.io.FileNotFoundException: ../lib/jasper-runtime.jar (Permission denied)
```

please halp!

---

### Post by combatwombat_nz on 2007-09-16
cdrappier:

ensure that you are running the commands through sudo.

---

### Post by shanepardue on 2007-09-26
I've had a very rough time with the stability of the Openfire server I've set up recently. I've installed it on two different Ubuntu (7.04) machines and both have very similar issues. The first time a client tries to connect, they get either the invalid username/password error message or the server unreachable message. Usually about two minutes later, the client is able to connect. This wouldn't be so bad, but it seems to happen repeatedly even after the first login, but it's more random thereafter.

Could this be an Ubuntu compatibility issue? I don't think it's a configuration issue or even an openfire one simply because I've used other jabber server software and I experience the same problems.

It's really hard to reproduce the problem after the first login, but it happens enough to not use this in production.

Thank you for your help!

---

### Post by md5hash on 2007-10-02
how can i re-setup the server to use mysql database? currently it is using HSQL Database Engine 1.8.0

---

### Post by FANTAchrist on 2007-10-05
> **shanepardue said:**
> I've had a very rough time with the stability of the Openfire server I've set up recently. I've installed it on two different Ubuntu (7.04) machines and both have very similar issues. The first time a client tries to connect, they get either the invalid username/password error message or the server unreachable message. Usually about two minutes later, the client is able to connect. This wouldn't be so bad, but it seems to happen repeatedly even after the first login, but it's more random thereafter.

Could this be an Ubuntu compatibility issue? I don't think it's a configuration issue or even an openfire one simply because I've used other jabber server software and I experience the same problems.

It's really hard to reproduce the problem after the first login, but it happens enough to not use this in production.

Thank you for your help!

I get the impression Ubuntu doesn't like Openfire, I'm using 6.0.6 and about every 12 hours I get disconnected with  xmpp.client.idle set to -1, I've read up on their forums and others are having the same problem as me but it has yet to be resolved, one person jumped ship to Fedora Core and they say it solved the problem. I'm now using Openfire 3.3.3, while I was using 3.3.2 I was having the same issue as yourself  so I would suggest upgrading  if you haven't.

---

### Post by shanepardue on 2007-10-05
I'm not sure if you read my post in another forum or what, but I also switched to Fedora and had no problem. That was my solution.

---

### Post by FANTAchrist on 2007-10-05
Haha wow... I just found that post and it was you! I feel like a goof now.

---

### Post by ronaldotis on 2007-10-12
Hi,
Apparently I cant get openfire connect to MySQL databse. I'm using Ubuntu 7.04. This is what i have at the database URL:jdbc:mysql://localhost:3306/openfire. Anybody who can help?

---

### Post by HS-L on 2007-11-05
Is there a way to completely reconfigure openfire?
It couldn't login so i deleted the database, but i don't get the configure option anymore....

---

### Post by Hokum83 on 2007-11-07
> **HS-L said:**
> Is there a way to completely reconfigure openfire?
It couldn't login so i deleted the database, but i don't get the configure option anymore....

1. open openfire.xml
2. go to tag <setup>true</setup> and change in on <setup>false</setup>
3. restart openfire

---

### Post by dorath on 2008-02-07
> **D_2 said:**
> Anyone know how to get to the admin page other than using [_[COLOR=#bd5900]http://localhost:9090[/COLOR]_]("http://localhost:9090/") I have this on my Ubuntu server that isn't connected to a monitor so I use Putty to get to it and I did try links to get to it but that did get me to the pages but it was kind of hard to read and so i am trying to find a way to get to the page other than using [_[COLOR=#bd5900]http://localhost:9090[/COLOR]_]("http://localhost:9090")
I did try IP of that box (192.168.1.5:9090) but it didn't work.

A late reply, yes, but I had the same problem last night and others might as well.  To solve this I installed lynx, a text based browser, on the server and was then able to connect to [http://127.0.0.1:9090](http://127.0.0.1:9090) using the same ssh window I had been using to do the install.

I'm at work right now and don't have access to the machine, but I believe that ```
sudo apt-get install lynx
```will do the trick.  It took me a couple minutes to get used to the navigation, but it's really not bad.

---

### Post by goldbuffalo on 2009-06-19
Hello,
My openfire 3.64, everything works but I can't tranfer file with yahoo or MSN, pls HELP!!
 
Thanks alot:popcorn:

---

### Post by anung524 on 2009-08-21
Thanks for the step-by-step tutorial.
Openfire made me go nuts with the "nohup.out" problem.
I followed the instruction, and it worked like a charm.
I'm using Openfire 3.6.4, Ubuntu 9.04 Server, Java JDK 6, and MySQL 5.1.

Thank you very much.. :D

---

### Post by lightnb on 2009-11-02
I'm also trying to get this working, but having no luck. I *think* it's running...

netstat -tap shows:
```
tcp6       0      0 [::]:9092               [::]:*                  LISTEN      1871/java
```

and when I visit
```
http://openfire.mydomain.com:9092/
```
The favicon loads...


But the page is completely blank! The docs say I should see a set-up wizard, but nothing's there. There's nothing exciting in the log files either.

I'm also using Openfire 3.6.4, Ubuntu 9.04 Server, Java JDK 6, and MySQL 5.1.

Any ideas?

---

### Post by EmanresuusernamE on 2009-11-11
They have a .deb package that you can use to greatly simplify installing Openfire.  Try running that instead.  It's much easier, and I had it up and fully running....... However I can't seem to get a user connect just yet. :)

---

### Post by EmanresuusernamE on 2009-11-12
:rolleyes:
Duhhh, I tried installing Jabberd first and it's what was listening on the ports first.  After removing it and restarting Openfire, I can connect just fine.

So the .deb package they have works wonders.  Just install it, then log onto the admin website after it's finished installing to configure Openfire.  It's on:

http://<openfire server>:9090

Don't forget to open the port if you have your firewall set.

---

### Post by bgabga on 2010-09-03
Do not use openfire 3.6.4; you can't log in into web interface!! Use openfire 3.6.3.
I spend a few days to figure out!

---

### Post by Revo___ on 2010-09-04
Have you tried using:

Username: admin
Password: admin

(But you're right - it should better use the credentials you entered at setup)

---

### Post by ojay on 2010-09-22
> **bgabga said:**
> Do not use openfire 3.6.4; you can't log in into web interface!! Use openfire 3.6.3.
I spend a few days to figure out!

I am using 3.6.4 and its working fine, though you are right that after first setup, you won't be able to login to the web interface. for me all i did was to clear my browser cache and use admin as username and the password i created.
So for those that have such problem, just launch another browser and use admin as username and password you created.
OR
issue sudo etc/init.d/openfire restart.... to restart openfire and then try again.

---

### Post by SilverWave on 2011-01-21
> **ojay said:**
> I am using 3.6.4 and its working fine, though you are right that after first setup, you won't be able to login to the web interface. for me all i did was to clear my browser cache and use admin as username and the password i created.
So for those that have such problem, just launch another browser and use admin as username and password you created.
OR
issue sudo etc/init.d/openfire restart.... to restart openfire and then try again.

Hah, that explains the issue I had to day, thought it was me as I got in after a restart.

---

### Post by SilverWave on 2011-01-21
Hmm just did an install to day and all looks good for my purposes, 5 users in a IT department using Pidgin as the client...

Possible roll-out to 25 more if we like it.

One question though:

The domain defaults to the server name so you add users in the form silverw@myserver.

But my server is a dev machine with a confusing name so silverw@srv1234.

It would look better if it was silverw@IM so what are my options?

Note: Just renaming the server would be a pain.

---

### Post by valivarona on 2011-02-04
I successfully installed openfire 3.6.4 on ubuntu 10.10 and it works like a charm after a trick with openjdk instead sun-java6-jre, 
# Attempt to locate JAVA_HOME, code borrowed from jabref package
if [ -z $JAVA_HOME ]
then
        t=/usr/lib/jvm/java-6-openjdk && test -d $t && JAVA_HOME=$t
fi

but when I want to upgrade aptitude.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 openfire : PreDepends: sun-java5-jre but it is not installable or
                        sun-java6-jre but it is not installed
E: Unmet dependencies. Try using -f.

I don't want to remove openfire ..
please help

Valiku

---

### Post by lioncub on 2011-10-21
How enable SSO (Kerberos Authentication)?

---

