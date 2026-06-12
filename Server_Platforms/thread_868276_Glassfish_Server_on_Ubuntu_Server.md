---
title: "Glassfish Server on Ubuntu Server"
date: 2008-07-23
forum: Server Platforms
---

### Post by fballem on 2008-07-23
I have a standard Ubuntu Hardy Server with no GUI installed. I would like to set it up as a Glassfish Server using version 2 of Glassfish, ideally from the original download site.

I do have ssh access from my desktop computer to the Ubuntu Hardy Server.

I am assuming that I should install Netbeans and the Glassfish GUI administration program on the desktop computer.

I am a relative newbie, so specific instructions would be much appreciated.

Many thanks,

---

### Post by tinny on 2008-07-23
Here are some notes that I wrote about 6 months ago about my experience in installing Glass fish on Ubuntu server.

BTW: You dont need NetBeans. Once you are setup you can browse to the admin console of Glassfish. ([http://hostname:4848](http://hostname:4848))

**Install Sun Java JDK 5.0 **

1.At the command line
2.Download and install the Sun Java JDK from the remote repository, 
```

sudo apt-get install sun-java5-jdk 

```
(must have the multi universe repositories setup).

3.APT will now download the required packages and dependences for you and install them. 
4.The installer will ask you to accept the licence agreement. 

**Install Glassfish V2 **

1.Download glassfish
```

wget http://java.net/download/javaee5/v2ur2/promoted/Linux/glassfish-installer-v2ur2-b04-linux.jar

```

Download this file to the parent folder that you want to install glassfish too (e.g. /user/local/). 
2.Execute the installer 
```

sudo java -Xmx256m -jar glassfish-installer-v2ur2-b04-linux.jar

```

accept the licence agreement. 
3.Setup the permissions for the glassfish ant binaries and run the setup file. 
```

cd /usr/local/glassfish 
chmod -R +x lib/ant/bin
lib/ant/bin/ant -f setup.xml

```
4.Starting stopping glassfish
```

cd [GlassFishHome]/bin
./asadmin start-domain domain1
./asadmin stop-domain domain1

```

Let me know how you get on.

---

### Post by fballem on 2008-07-23
> **tinny said:**
> Here are some notes that I wrote about 6 months ago about my experience in installing Glass fish on Ubuntu server.

BTW: You dont need NetBeans. Once you are setup you can browse to the admin console of Glassfish. ([http://hostname:4848](http://hostname:4848))

**Install Sun Java JDK 5.0 **

1.At the command line
2.Download and install the Sun Java JDK from the remote repository, 
```

sudo apt-get install sun-java5-jdk 

```
(must have the multi universe repositories setup).

3.APT will now download the required packages and dependences for you and install them. 
4.The installer will ask you to accept the licence agreement. 

**Install Glassfish V2 **

1.Download glassfish
```

wget http://java.net/download/javaee5/v2ur2/promoted/Linux/glassfish-installer-v2ur2-b04-linux.jar

```

Download this file to the parent folder that you want to install glassfish too (e.g. /user/local/). 
2.Execute the installer 
```

sudo java -Xmx256m -jar glassfish-installer-v2ur2-b04-linux.jar

```

accept the licence agreement. 
3.Setup the permissions for the glassfish ant binaries and run the setup file. 
```

cd /usr/local/glassfish 
chmod -R +x lib/ant/bin
lib/ant/bin/ant -f setup.xml

```
4.Starting stopping glassfish
```

cd [GlassFishHome]/bin
./asadmin start-domain domain1
./asadmin stop-domain domain1

```

Let me know how you get on.

tinny:

Thanks - I made good progress with your help. I'll modify your instructions in a few minutes, but a couple of questions, if I may:

1. I would like to be able to access my server from the desktop. If my server is named server-01, then do I need to do anything on the server itself to be able to enter this in my browser from the desktop?

2. I had to use sudo for most of the commands. I also setup a user 'glassfish' on the server and made that the owner of the directory where the glassfish software was installed. How do I make sure that the server will start up when the server is started?

Thanks!

---

### Post by tinny on 2008-07-23
> 
1. I would like to be able to access my server from the desktop. If my server is named server-01, then do I need to do anything on the server itself to be able to enter this in my browser from the desktop?


No, [http://hostname:4848](http://hostname:4848) should be fine.

> 
2. I had to use sudo for most of the commands. I also setup a user 'glassfish' on the server and made that the owner of the directory where the glassfish software was installed. How do I make sure that the server will start up when the server is started?

You could create a glassfish user and give them permissions to /usr/local/glassfish/... right?

As for a start-up script, I think this is what I did in the past...

Create the following file /etc/init.d/glassfish
```

GLASSFISHHOME=/usr/local/glassfish/glassfish_v2ur2_b04
case "$1" in
start)
    ${GLASSFISHHOME}/bin/asadmin start-domain domain1
    ;;
stop)
    ${GLASSFISHHOME}/bin/asadmin stop-domain domain1
    ;;
restart)
    ${GLASSFISHHOME}/bin/asadmin stop-domain domain1
    ${GLASSFISHHOME}/bin/asadmin start-domain domain1
    ;;
*)
    echo $"usage: $0 {start|stop|restart}"
    exit 1
esac

```

Then

```

sudo update-rc.d glassfish defaults

```

---

### Post by fballem on 2008-07-23
> **tinny said:**
> No, [http://hostname:4848](http://hostname:4848) should be fine.


You could create a glassfish user and give them permissions to /usr/local/glassfish/... right?

As for a start-up script, I think this is what I did in the past...

Create the following file /etc/init.d/glassfish
```

GLASSFISHHOME=/usr/local/glassfish/glassfish_v2ur2_b04
case "$1" in
start)
    ${GLASSFISHHOME}/bin/asadmin start-domain domain1
    ;;
stop)
    ${GLASSFISHHOME}/bin/asadmin stop-domain domain1
    ;;
restart)
    ${GLASSFISHHOME}/bin/asadmin stop-domain domain1
    ${GLASSFISHHOME}/bin/asadmin start-domain domain1
    ;;
*)
    echo $"usage: $0 {start|stop|restart}"
    exit 1
esac

```

Then

```

sudo update-rc.d glassfish defaults

```

1/ I don't think that I can give the glassfish user access until after I have set everything up.

2/ I set up the script and rant the update-rc.d command (whatever that is).

3/ I was able to log in to my server, once I twigged that user is admin and password is adminadmin. I guess I'd better change that.

Thanks, and I'll update the instructions in detail in a few minutes.

---

### Post by fballem on 2008-07-23
I'm adding some detailed notes to these instructions. Once these have been reviewed and updated, I'd like to put them in a WIKI entry, which might make them more accessible.

Problem: I want to install Glassfish version 2 from the Sun site. I have two machines:
[LIST=1]
[*]A laptop, running ubuntu 8.04 as a desktop
[*]A server, running ubuntu 8.04 server. Note that there is no GUI on this server.
[/LIST]

Steps:
[LIST=1]
[*]Install the ubuntu server. Include Open SSH, but none of the other optional software. If you need instructions, please reference [http://www.ubuntugeek.com/ubuntu-804-hardy-heron-lamp-server-setup.html](http://www.ubuntugeek.com/ubuntu-804-hardy-heron-lamp-server-setup.html), but only select the OpenSSH server option, **not** the LAMP server. option. In particular, pay attention to the setup of the static IP address and adding the entry into the /etc/resolv.conf file on the desktop.
[*]reboot the server.
[*]on the desktop, open a terminal and type 'ssh username@servername', where username is the username that you used when setting up the server and servername is the name of the server. You will receive a notification that the certificate requires an exception. Answer 'yes' (type the word in full) and then you will be asked for the password.
[LIST=1]
[*]If there is a problem, then reference the following post: [http://ubuntuforums.org/showthread.php?t=851263](http://ubuntuforums.org/showthread.php?t=851263)
[/LIST]
[*]The terminal is the 'front-end' for the server and you must use command lines. When following the instructions from tinny in this post, check the results. If you get an access error, then put sudo in front of the command.
[/LIST]

Note that on the script, the value for GLASSFISHHOME is /usr/loca/glassfish.

---

### Post by fballem on 2008-07-23
tinny:

Further question - I haven't found either Derby or MySQL on the server. What do I need to do to get these things.

Thanks,

---

### Post by tinny on 2008-07-24
> **fballem said:**
> tinny:

Further question - I haven't found either Derby or MySQL on the server. What do I need to do to get these things.

Thanks,

I haven't tried Derby on a server before. But for MySQL

Install MySQL server. (I think this script gets run automatically for you "mysql_install_db")
```

sudo apt-get install mysql-server

```

Setup the root MySQL user and allow them to connect from anywhere.
```

mysql -u root
>SET PASSWORD FOR 'root'@'%' = PASSWORD('newpwd');
>GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY 'some_pass' WITH GRANT OPTION;

```

Allow MySQL to receive connection from remote hosts.
```

Comment out "bind-address = 127.0.0.1" in /etc/mysql/my.cnf
/etc/init.d/mysql restart

```

Restart the server.
```

/etc/init.d/mysql restart

```

BTW: If you like you can PM me your documentation on this process (GlassFish / MySQL) and Id be happy to review it for you. (I think there are a couple of things that could be improved from your previous post)

---

### Post by fballem on 2008-07-24
> 
BTW: If you like you can PM me your documentation on this process (GlassFish / MySQL) and Id be happy to review it for you. (I think there are a couple of things that could be improved from your previous post)

Thanks for the offer. Could you please tell me what 'PM' is, and how do I do this? I'm still going through a steep learning curve.

Many thanks,

---

### Post by tinny on 2008-07-24
> **fballem said:**
> Thanks for the offer. Could you please tell me what 'PM' is, and how do I do this? I'm still going through a steep learning curve.

Many thanks,

Private message.

---

### Post by fballem on 2008-07-24
Will do on the private message.

I am now trying to set up the server in NetBeans 6.1, which is installed and running on my desktop machine. Apparently I need to register it. So I start Tools | Server | Add Server. I select Glassfish V2 and give it a name. The next screen is attached. Absolutely no clue as to how to continue forward. My server is called ballemco-srv-01 and it is started (I can access it using [http://ballemco-srv-01:4848](http://ballemco-srv-01:4848)).

If you can help, then I would appreciate it.

Thanks

---

### Post by tinny on 2008-07-24
> **fballem said:**
> Will do on the private message.

I am now trying to set up the server in NetBeans 6.1, which is installed and running on my desktop machine. Apparently I need to register it. So I start Tools | Server | Add Server. I select Glassfish V2 and give it a name. The next screen is attached. Absolutely no clue as to how to continue forward. My server is called ballemco-srv-01 and it is started (I can access it using [http://ballemco-srv-01:4848](http://ballemco-srv-01:4848)).

If you can help, then I would appreciate it.

Thanks

To connect to the remote glassfish instance NetBeans needs to have access to a local glassfish instance (needs to use some glassfish jars). I think the platform error message you are getting is telling you that you havent set this step up correctly? (have a look at the path to your current local server registration in NetBeans and use the same platform path). Once this is setup correctly you should be able to click next and then input the remote host name and port number. (host: ballemco-srv-01 port: 4848)

Basically it looks to me like you are on the right track.

---

### Post by fballem on 2008-07-24
> **tinny said:**
> To connect to the remote glassfish instance NetBeans needs to have access to a local glassfish instance (needs to use some glassfish jars). I think the platform error message you are getting is telling you that you havent set this step up correctly? (have a look at the path to your current local server registration in NetBeans and use the same platform path). Once this is setup correctly you should be able to click next and then input the remote host name and port number. (host: ballemco-srv-01 port: 4848)

Basically it looks to me like you are on the right track.

Baby steps:lolflag: I think I'm missing something in my NetBeans setup, because I don't know how to find the 'current local server registration in NetBeans'. If you could guide me in this, I would be most grateful.

Thanks,

---

### Post by tinny on 2008-07-24
Ok sure :)

Go to "services tab" > "Servers" > "GlassFish V2" then right mouse click > "Properties"

The screen you are presented with has a "Connection" tab.

Look for the path for "Domains folder" (On my windows machine C:\Program Files\glassfish-v2ur2\domains ignore the \domains folder) this is your local GlassFish path.

The path you are looking for will be something like <your installation path>/glassfish-v2ur2 (your GlassFish version my be different e.g. glassfish-<version>)

---

### Post by windependence on 2008-07-24
> **tinny said:**
> No, [http://hostname:4848](http://hostname:4848) should be fine.



Actually, he will probably have to put an entry in his hosts file on the desktop machine to access it by name.

-Tim

---

### Post by fballem on 2008-07-24
> **tinny said:**
> Ok sure :)

Go to "services tab" > "Servers" > "GlassFish V2" then right mouse click > "Properties"

The screen you are presented with has a "Connection" tab.

Look for the path for "Domains folder" (On my windows machine C:\Program Files\glassfish-v2ur2\domains ignore the \domains folder) this is your local GlassFish path.

The path you are looking for will be something like <your installation path>/glassfish-v2ur2 (your GlassFish version my be different e.g. glassfish-<version>)

When I go to the Services Tab | Server, there is no Glassfish option. I have a feeling that I might have to fix the installation of NetBeans.

Windependence: Thanks for the note about the server name. If you're referring to the entry in /etc/resolv.conf on the desktop, then that's covered. If you have something else in mind, could you please let me know? I have installed webmin on the server, and I can access it from my browser using the server name. I can also access the Glassfish administration panel on the server using the server name and 4848.

This is a slow painful process and I appreciate the patience.I converted from Windows about a month ago and have decided to resurrect my programming skills (20 years old). I figured that I better get a reasonable environment in place so that I can see the results.

Thanks!

---

### Post by tinny on 2008-07-24
Did you get the GlassFish init script going? You should have defined the path in that script.

E.g.

```

GLASSFISHHOME=/usr/local/glassfish/glassfish_v2ur2_b04

```

---

### Post by fballem on 2008-07-24
> **tinny said:**
> Did you get the GlassFish init script going? You should have defined the path in that script.

E.g.

```

GLASSFISHHOME=/usr/local/glassfish/glassfish_v2ur2_b04

```

Glassfish is installed on the server, not the desktop. And yes, I got the script going on the server.

I am thinking that I need to install glassfish on the desktop, so I'm re-installing NetBeans with the Glassfish option enabled.

---

### Post by fballem on 2008-07-24
so now I was able to identify the server, after re-installing NetBeans with the Glassfish server on the workstation.

Time to start the heavy learning curve. I did promise to document this. What tool do I need to use to build a wiki entry?

---

### Post by fballem on 2008-07-24
by the way, is there a relatively easy way to test this so that we're sure it is working.

I am assuming that I would want something simple in NetBeans, build it, move it to the server, and see it working there. We should probably include that in the documentation.

---

### Post by tinny on 2008-07-24
> **fballem said:**
> by the way, is there a relatively easy way to test this so that we're sure it is working.

I am assuming that I would want something simple in NetBeans, build it, move it to the server, and see it working there. We should probably include that in the documentation.

Yes you could do that (deploy a simple application) or you could just open the new remote server node under the "Servers" node in the services tab. Right clicking on the new remote server will give you the option to "refresh" its status. If it refreshes im guessing it is communicating correctly.

---

### Post by Padrhino on 2008-08-04
I started to installing glassfish step by step but after writing tihs to terminal
```
lib/ant/bin/ant -f setup.xml
```

I get the error message:

```
     
     [exec] Security Store uses: JKS
     [exec] keytool error: java.io.IOException: Invalid keystore format
     [exec]  
     [exec] CLI130 Could not create domain, domain1

BUILD FAILED
/usr/local/glassfish/setup.xml:172: The following error occurred while executing this line:
/usr/local/glassfish/setup.xml:561: exec returned: 1

```

I find something about port 8080 on net. People in other forums says usually Tomcat (or another app) can use this port so this error shows up. I couldn't see tomcat in add/remove applications. As i remember i didn't install tomcat. Also, some people says using sun jdk 1.6 will solve the problem. I've already installed it. But i can't figure out why still i have this problem?

---

### Post by tinny on 2008-08-04
> **Padrhino said:**
> I started to installing glassfish step by step but after writing tihs to terminal
```
lib/ant/bin/ant -f setup.xml
```

I get the error message:

```
     
     [exec] Security Store uses: JKS
     [exec] keytool error: java.io.IOException: Invalid keystore format
     [exec]  
     [exec] CLI130 Could not create domain, domain1

BUILD FAILED
/usr/local/glassfish/setup.xml:172: The following error occurred while executing this line:
/usr/local/glassfish/setup.xml:561: exec returned: 1

```

I find something about port 8080 on net. People in other forums says usually Tomcat (or another app) can use this port so this error shows up. I couldn't see tomcat in add/remove applications. As i remember i didn't install tomcat. Also, some people says using sun jdk 1.6 will solve the problem. I've already installed it. But i can't figure out why still i have this problem?

Did you setup the permissions?


3.Setup the permissions for the glassfish ant binaries and run the setup file.

```

cd /usr/local/glassfish 
chmod -R +x lib/ant/bin
lib/ant/bin/ant -f setup.xml

```

---

### Post by Padrhino on 2008-08-04
yes i did it. The permission of /usr/local/glassfish/lib/ant/bin is

drwxr-xr-x

The same for /usr/local/glassfish/lib/ant and /usr/local/glassfish/lib

And i noticed another thing;
You said 
> Here are some notes that I wrote about 6 months ago about my experience in installing Glassfish on Ubuntu server.

I'm using ubuntu hardy not a server. Is that the problem. Besides without sudo 

```
lib/ant/bin/ant -f setup.xml
```

gives the result

```
BUILD FAILED
/usr/local/glassfish/setup.xml:156: The following error occurred while executing this line:
/usr/local/glassfish/setup.xml:96: java.io.FileNotFoundException: /usr/local/glassfish/passfile (Permission denied)

```

---

### Post by tinny on 2008-08-04
I think you will need to run the "lib/ant/bin/ant -f setup.xml" command as sudo.

Edit: This above command is setting the execute permissions for the Ant binaries that are included with the GlassFish bundle. I really should clean this up and make it a proper HOW TO

---

### Post by Padrhino on 2008-08-05
thank you for replies but i tried it again and again. The result is the same:

```

     [exec] Security Store uses: JKS
     [exec] keytool error: java.io.IOException: Invalid keystore format
     [exec]  
     [exec] CLI130 Could not create domain, domain1

BUILD FAILED
/usr/local/glassfish/setup.xml:172: The following error occurred while executing this line:
/usr/local/glassfish/setup.xml:561: exec returned: 1

```

I'll be waiting for your next HOWTO :)

---

### Post by tinny on 2008-08-05
You installed Sun JDK 5 right?

[http://forums.java.net/jive/thread.jspa?messageID=271690&#65533;&#65533;](http://forums.java.net/jive/thread.jspa?messageID=271690&#65533;&#65533;)

I think you might be using OpenJDK. (Or at least might have a link to it...?)

What is the output of:

```

java -version
javac -version

```

---

### Post by Padrhino on 2008-08-05
Hi, I was using open jdk, you are right. But i had installed sun jdk 6. Now i removed open jdk. Here my java -version and javac - version results:

```

Padrhino@Padrhino:~$ sudo update-alternatives --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
 +        2    /usr/lib/jvm/java-gcj/jre/bin/java
*         3    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 3
Using '/usr/lib/jvm/java-6-sun/jre/bin/java' to provide 'java'.
Padrhino@Padrhino:~$ java -version
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)

Padrhino@Padrhino:~$ javac -version
javac 1.6.0_06

```

Now the error becomes:

```

create.domain:
     [exec] /usr/local/glassfish/bin/asadmin: 19: /usr/lib/jvm/java-6-openjdk/jre/../bin/java: not found

BUILD FAILED
/usr/local/glassfish/setup.xml:172: The following error occurred while executing this line:
/usr/local/glassfish/setup.xml:561: exec returned: 127

```

There is a problem about java classpath, i think.

---

### Post by tinny on 2008-08-05
I think you should remove glassfish and start again. Its still trying to use the Open JRE I think.

> 
/usr/lib/jvm/java-6-openjdk/jre/


Basically I think that your install is all messed up.

---

