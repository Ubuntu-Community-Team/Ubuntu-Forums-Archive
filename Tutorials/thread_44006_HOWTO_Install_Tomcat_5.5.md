---
title: "HOWTO: Install Tomcat 5.5"
date: 2005-06-24
forum: Tutorials
---

### Post by noodle on 2005-06-24
**Installing Tomcat on Ubuntu**

Versions:
SDK: 1.5
JRE: 1.5
Tomcat: 5.5

**Step 1 – Install JRE and SDK**

Download and install the Java Software Development Kit (SDK) and J2SE Runtime Environment (JRE). These packages are available through Synaptic (the extra repositories have to be added).

Or in terminal type:

```
sudo apt-get install sun-j2re1.5
sudo apt-get install sun-j2sdk1.5
```
 
N.B. SDK is 146MB and JRE is 84.7MB.

You can verify that both items were installed corectly, by checking that you get a response when typing in terminal:

```
java -version
javac -help
```

**Step 2 – Get tomcat**

Download tomcat 5.5 from [http://jakarta.apache.org/site/downloads/](http://jakarta.apache.org/site/downloads/downloads_tomcat-5.cgi) 

In this example I am using jakarta-tomcat-5.5.9.tar.gz

Uncompress the file:

```
tar xvfz jakarta-tomcat-5.5.9.tar.gz 
```

N.B. To make things simpler I also renamed the package to just 'tomcat'. If you do not do this, make sure you adjust these tutorial instructions to the name of your package whenever you see 'tomcat' written. 

**Step 3 – Add tomcat**

Place the uncompressed package in:

/usr/local/

**Step 4 – Set JAVA_HOME and CLASSPATH**

You need to point out where you installed Java SDK. You will have to edit the file '.bashrc'. *Backup this file first!*

In terminal type:

```
gedit ~/.bashrc
```

Add the following lines to the file:

```
#Stuff we added to make tomcat go
export JAVA_HOME=/usr/lib/j2sdk1.5-sun/
export CLASSPATH=/usr/local/tomcat/common/lib/jsp-api.jar:/usr/local/tomcat/common/lib/servlet-api.jar

```
N.B. remember to change the word tomcat to the name of the package you placed in /usr/local.

Save and close. You will have to log out and back in again before these changes take effect. 


[B]The next steps are optional. They are for setting tomcat up to be used as a development environment. Skip to the last step ( Step 8 ) if you just want to start tomcat how it is. 


Step 5 – Change default port number[/B]

Tomcats default port number is 8080. To change it to 80 or another number do the following.

In terminal type:

```
gedit usr/local/tomcat/conf/server.xml
```

Find the lines:

```
<Connector port="8080" ...
	maxThreads="150" minSpareThreads="25" ...
```

Adjust the port number to 80 (or any other port number you want to use), save and close.

**Step 6 – Turn on Servlet reloading**

In terminal type:

```
gedit usr/local/tomcat/conf/context.xml
```

Find:

```
<Context>
```

Change it to: 

```
<Context reloadable="true">
```

Save and close.
[B]
Step 7 – Enable Invoker Servlet[/B]

In terminal type:

```
gedit usr/local/tomcat/conf/web.xml
```

Find and uncomment (remove the <-- and --> wrapped around the tags):
```
 <servlet>
        <servlet-name>invoker</servlet-name>
        <servlet-class>
          org.apache.catalina.servlets.InvokerServlet
        </servlet-class>
        ...
    </servlet>
```

Also find and uncomment:

```
    <servlet-mapping>
        <servlet-name>invoker</servlet-name>
        <url-pattern>/servlet/*</url-pattern>
    </servlet-mapping>
```

Save and close.

**Step 8 – Start tomcat**

Tomcat should now be ready to run.

In terminal type:

```
sh /usr/local/tomcat/bin/startup.sh
```

If everything is working fine, you will see the following lines:

```
Using CATALINA_BASE:   /usr/local/tomcat
Using CATALINA_HOME:   /usr/local/tomcat
Using CATALINA_TMPDIR: /usr/local/tomcat/temp
Using JRE_HOME:       /usr/lib/j2sdk1.5-sun/
```

In your browser head to [http://localhost/](http://localhost/) and test if it is serving. If you didn't change the port number it was serving on, head to [http://localhost:8080/](http://localhost:8080/) 

To stop tomcat type:
```

sh /usr/local/tomcat/bin/shutdown.sh
```


-----

I hope this helped! 8)

If you have any problems, I recommend this site for more details: [http://www.coreservlets.com/](http://www.coreservlets.com/)

---

### Post by RastaMahata on 2005-06-24
great! just in time for my polls project.

Now, to look for eclipse :)

---

### Post by tzutolin on 2005-06-24
[QUOTE=RastaMahata]great! just in time for my polls project.

Now, to look for eclipse :)[/QUOTE]
 Another way to install Tomcat is to install NetBeans ([http://www.netbeans.org](http://www.netbeans.org)) which come with an embeded Tomcat server. All pre-configured :-)

---

### Post by jreymol on 2005-06-27
Thank you, noodle.

I have been able to install Tomcat 5.5 on my ubuntu.

But I want it to run as a service, so I modified a little this process.

1. I omitted step 4
2. I put in /etc/init.d a file called tomcat with this script

```
#!/bin/bash
#
# Startup script for the Tomcat server
#
# chkconfig: - 83 53
# description: Starts and stops the Tomcat daemon.
# processname: tomcat
# pidfile: /var/run/tomcat.pid


# See how we were called.
case $1 in
	start)

		export JAVA_HOME=/usr/lib/j2sdk1.5-sun/
		export CLASSPATH=/usr/local/tomcat/common/lib/servlet-api.jar
		export CLASSPATH=/usr/local/tomcat/common/lib/jsp-api.jar
		sh /usr/local/tomcat/bin/startup.sh
	;;
	stop)
		sh /usr/local/tomcat/bin/shutdown.sh
	;;
	restart)
		sh /usr/local/tomcat/bin/shutdown.sh
		sh /usr/local/tomcat/bin/startup.sh
	;;
	*)
		echo "Usage: /etc/init.d/tomcat start|stop|restart"
	;;
esac

exit 0

```

3. I executed this lines:

```
chmod 755 /etc/init.d/tomcat
ln -s /etc/init.d/tomcat /etc/rc1.d/K99tomcat
ln -s /etc/init.d/tomcat /etc/rc2.d/S99tomcat

```

and now my tomcat is there when I start up my linux  \\:D/ 

BE AWARE: My experience with linux is very, very limited. I cannot be sure this lines of code are perfect. I just can say they work for me.

---

### Post by cope on 2005-07-03
when i follow this it doesn't work.
it loads everything fine, but when i try to connect to localhost:8080 it says connection refused..

any idea what i can do to fix it? 

```

root@dev:/usr/local/tomcat/conf # sh /usr/local/tomcat/bin/startup.sh
Using CATALINA_BASE:   /usr/local/tomcat
Using CATALINA_HOME:   /usr/local/tomcat
Using CATALINA_TMPDIR: /usr/local/tomcat/temp
Using JRE_HOME:       /usr/lib/j2sdk1.5-sun/

```

any ideas?
i followed the how to step by step?

---

### Post by jreymol on 2005-07-04
hello, cope!

I have just started a new tomcat instalation and it works.

have you changed port in step 5?

if you have set 80 as tomcat default port localhost:8080 will say you conection refused just because tomcat isn't listening there.

Have you see logs in tomcat/log?

The only problem I'm having is with my /etc/init.d/tomcat script. Cut an paste from web page to gedit doesn't work because cr+lf are lost. I have cut and paste through windows with notepad and I see it right, but when I transfer it from widows to ubuntu I cannot get it to run.

But seeing your post it seems your tomcat is running. I think it's the port number.

---

### Post by cope on 2005-07-05
[QUOTE=jreymol]hello, cope!

I have just started a new tomcat instalation and it works.

have you changed port in step 5?

if you have set 80 as tomcat default port localhost:8080 will say you conection refused just because tomcat isn't listening there.

Have you see logs in tomcat/log?

The only problem I'm having is with my /etc/init.d/tomcat script. Cut an paste from web page to gedit doesn't work because cr+lf are lost. I have cut and paste through windows with notepad and I see it right, but when I transfer it from widows to ubuntu I cannot get it to run.

But seeing your post it seems your tomcat is running. I think it's the port number.[/QUOTE]
 port number is 8080, i think i had to define the java home in bashrc which i hadn't done. all working fine now.

---

### Post by noodle on 2005-07-15
With bashrc you have to logout and back in again before the changes take effect. 

If you didn't want to alter your bashrc file, you can still start tomcat, by first typing in terminal:

```
export JAVA_HOME=/usr/lib/j2sdk1.5-sun/
export CLASSPATH=/usr/local/tomcat/common/lib/servlet-api.jar:/usr/local/tomcat/common/lib/jsp-api.jar
```

However, this would have to be done everytime you wanted to start tomcat and you were using a new session. On the positive side, using this method is quicker when your setting up tomcat on the fly.

I think jreymol had the best idea, which was running it as a service. And the paths are declared everytime tomcat is started.

Oh, and another tip:

.bashrc is global. You can add the lines to .bash_profile if you just want to add it to declare the paths in your user profile - both will work.

---

### Post by tomaski on 2005-07-17
hey,

i would like to run java, eclipse and tomcat on ubuntu x86, but i don't know which extra repositories to add. which are they and how can i add them ?

any help would be great,

thanks,
tomaski

belgium

---

### Post by noodle on 2005-07-17
I installed all the extra repositories in the [starter guide](http://ubuntuguide.org/#extrarepositories) . I'm not sure whats in which one, but I can get everything I need from just those.

---

### Post by jholder on 2005-07-30
Isn't $CLASSPATH being overwritten by the second export in your examples.  I couldn't get servlets to compile until I changed it to look like this:

<SNIP>

export CLASSPATH=/usr/local/tomcat/common/lib/jsp-api.jar:/usr/local/tomcat/common/lib/servlet-ap i.jar

</SNIP>

---

### Post by dc2447 on 2005-07-30
I wouldn't run tomcat as root personally.

start it like

su - tomcatuser -c"/path/to/tomcat/bin/startup.sh"

---

### Post by noodle on 2005-07-30
[QUOTE=jholder]Isn't $CLASSPATH being overwritten by the second export in your examples.  I couldn't get servlets to compile until I changed it to look like this:

<SNIP>

export CLASSPATH=/usr/local/tomcat/common/lib/jsp-api.jar:/usr/local/tomcat/common/lib/servlet-ap i.jar

</SNIP>[/QUOTE]

You're absoulutly right. I guess I missed that one when I was copying and pasting. I'll fix it up right away.

Thanks for the notice  ;-)

---

### Post by er4z0r on 2005-09-21
[QUOTE=dc2447]I wouldn't run tomcat as root personally.

start it like

su - tomcatuser -c"/path/to/tomcat/bin/startup.sh"[/QUOTE]

I think there even is an option for tomcat or jsvc to give it a user to drop privileges to.
Can anyone please tell me how to create the apropriate user? 

[list]
[*] Did you set a Password?
[*] Did you set a shell?
[*] In general: How do I do this securely?
[/list]

Thanks in advance

---

### Post by theQmaster on 2005-09-27
[QUOTE=er4z0r]I think there even is an option for tomcat or jsvc to give it a user to drop privileges to.
Can anyone please tell me how to create the apropriate user? 

[list]
[*] Did you set a Password?
[*] Did you set a shell?
[*] In general: How do I do this securely?
[/list]

Thanks in advance[/QUOTE]


To create a use use the gnome interface or the kde interface. 
Should be simple. I have a user named tomcat.

There is jsvc true but I when I run it still runs as root.
I have an application that creates files, well the file created is root:root.

I think is due a problem between jsvc code and ubuntu. I remember I had to modify one c source a bit.

Anyone succesfully runs jsvc with low priviledge user ? Don't get me wrong JSVC works great. Does the thing, allows me to set JVM parameters but seems that doesn't switch to a low priviledge user I pass...

theQmaster
Good Stock Images - Stock Photography
[http://www.goodstockimages.com](http://www.goodstockimages.com)

---

### Post by ento on 2005-10-15
When i type  sh /usr/local/tomcat/bin/startup.sh i will get this meassage:
Cannot find /usr/local/tomcat/bin/catalina.sh
This file is needed to run this program

The file is there

/stefan

---

### Post by i23098 on 2005-10-23
[QUOTE=jreymol]
3. I executed this lines:

```
chmod 755 /etc/init.d/tomcat
ln -s /etc/init.d/tomcat /etc/rc1.d/K99tomcat
ln -s /etc/init.d/tomcat /etc/rc2.d/S99tomcat

```

and now my tomcat is there when I start up my linux  \\:D/ 
[/QUOTE]

While trying to understart what the rcX.d are, I've stumble across [this]("http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/") page, which explains you shouldn't make the links yourself but use the update-rc.d command, so, instead of the 2 ln -s you have, I've made:

```

update-rc.d tomcat defaults

```

I'm just a linux newbie and this is my way of saying thank you for this howto :D

---

### Post by i23098 on 2005-10-25
Just one more thing. When I tried to access my first jsp it gave me a class not found exception :???: It only worked when I also put the jasper-runtime.jar in the CLASSPATH of tomcat...

---

### Post by Ultracrat on 2005-11-13
Thank you jreymol!  Your startup script works great for me.  I've been struggling with getting Tomcat to startup on boot for a few hours, so I appreciate your post!

---

### Post by Weird Al on 2006-02-25
Hello. I'm trying to install Tomcat, of course, but:

```
alastair@serverus:~$ sudo apt-get install sun-j2sdk1.5
Reading package lists... Done
Building dependency tree... Done
Package sun-j2sdk1.5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-j2sdk1.5 has no installation candidate
```

It is the same for sun-j2re1.5.

I am running a Breezy server installation. I've added all the repositories the Wiki tells me to, seeing how the starter guide is now out of date.

I also found [this thread](http://ubuntuforums.org/showthread.php?t=14582) which tells me to install libapache-mod-jk, which I did, but now I can't tell if Tomcat is installed or not. I can't open a web browser on the server and trying to connect to port 8080 from another computer says connection refused. 

Further, I still don't know how to install the j2re and j2sdk.

help please :)

---

### Post by running on 2006-03-01
Hi maybe this Help:
[http://www.ubuntuforums.org/showthread.php?t=70428&highlight=sun-j2sdk1.5]("http://www.ubuntuforums.org/showthread.php?t=70428&highlight=sun-j2sdk1.5")

---

### Post by Melladh on 2006-04-03
I'm getting the issue with not reaching tomcat through my browser as well. I installed j2re and j2sdk through the steps with repositories described here
[http://www.ubuntuforums.org/showthread.php?t=75272](http://www.ubuntuforums.org/showthread.php?t=75272)

and everything seems to be working fine. I got the nice printout after telling it to start tomcat and everything, but it doesn't respond when I try to call it. I changed the port to 80, but neither through port 80 nor 8080 does it work.

-------
edit:

Tomcat works now, after a complete reboot and I'm also using the autostart-script provided here... I didn't change anything after my previous statement, and I did log off (but not reboot I must admit) at the correct step in the tutorial.

Oh, and thanks for the tutorial!

---

### Post by joe343 on 2006-04-17
Hi, my webserver was going fine until I rebooted my computer. Now when I go to [http://localhost/](http://localhost/) I get a directory listing of "Index of/" with those 2 entries:
[DIR] Parent Directory 15-Apr-2006 15:22 -
[DIR] apache2-default/ 15-Apr-2006 15:22 -

instead of my webpage that I previously had. If I click on apache2-default/ directory this page appears:
---------------------------------------
[CENTER]If you can see this, it means that the installation of the Apache web server software on this system was successful. You may now add content to this directory and replace this page.

**Seeing this instead of the website you expected?**

This page is here because the site administrator has changed the configuration of this web server. Please contact the person responsible for maintaining this server with questions. The Apache Software Foundation, which wrote the web server software this site administrator is using, has nothing to do with maintaining this site and cannot help resolve configuration issues.[/CENTER]---------------------------------------

What did I do wrong ?
I must have made some config changes somewhere but I don't know where ! I remember changing the owner of the /usr/local/tomcat/webapps/root/ from "root" to myself so I could edit the files. I also renamed the file web.xml to web_bak.xml just to see if it was really needed in the /webapps/root/WEB-INF/ (but I put it back the way is was).

Is there a checklist I could follow, somehing like:
-Make sure I have "this file" in "this directory"
-Make sure "that file" contains "that parameter"
-etc...


Also, I'm putting my website in the /webapps/root/ directory so I just have to type [http://localhost/](http://localhost/) to go to my pages instead of [http://localhost/otherdir/](http://localhost/otherdir/) (if I put my files in /webapps/otherdir). Is this good practice ? If not how to tell the server to go directly to /webapps/otherdir when I type [http://localhost/](http://localhost/) ?

I'm using ubuntu 5.10

---

### Post by noodle on 2006-04-17
I think your problems are occuring because you are running two servers on the same port at the same time. Try changing either Apache2 or the Tomcat server to run on different ports (eg. 80 and 8080). Otherwise, try turning off Apache2 while running tomcat. 

If you want to run both servers at once on the same port, look up the instructions for installing mod_jk or mod_jk2.

---

### Post by The_Artist on 2006-09-11
Thanks for this great and usefull post. I translate it into french on ubuntu-fr.org ! (you're naturally quoted)

---

### Post by noodle on 2006-09-11
> **The_Artist said:**
> Thanks for this great and usefull post. I translate it into french on ubuntu-fr.org ! (you're naturally quoted)

Awesome! I'm glad to see people are finding this HOWTO useful ;)

---

### Post by izm81 on 2006-09-14
I'm using Dapper and I got the following error when I tried starting Tomcat as soon as possible:

```

Using CATALINA_BASE:   /usr/local/apache-tomcat-5.5.17
Using CATALINA_HOME:   /usr/local/apache-tomcat-5.5.17
Using CATALINA_TMPDIR: /usr/local/apache-tomcat-5.5.17/temp
Using JRE_HOME:       /usr/lib/j2sdk1.5-sun
touch: cannot touch `/usr/local/apache-tomcat-5.5.17/logs/catalina.out': No such file or directory
/usr/local/apache-tomcat-5.5.17/bin/catalina.sh: line 258: /usr/local/apache-tomcat-5.5.17/logs/catalina.out: No such file or directory

```

All I had to do was
```
mkdir logs
```

Seems odd it wasn't there to begin with.

---

### Post by bytestor on 2006-09-15
> **cope said:**
> when i follow this it doesn't work.
it loads everything fine, but when i try to connect to localhost:8080 it says connection refused..

any idea what i can do to fix it? 

```

root@dev:/usr/local/tomcat/conf # sh /usr/local/tomcat/bin/startup.sh
Using CATALINA_BASE:   /usr/local/tomcat
Using CATALINA_HOME:   /usr/local/tomcat
Using CATALINA_TMPDIR: /usr/local/tomcat/temp
Using JRE_HOME:       /usr/lib/j2sdk1.5-sun/

```

any ideas?
i followed the how to step by step?



Hi I have the same problem as yours.  I am able to start tomcat but I get connection failed when I use [http://localhost/](http://localhost/)  or [http://localhost:8080/](http://localhost:8080/)

I get the following message when I start tomcat,

 ```

root@Toshiba:~# sh /usr/local/tomcat5/bin/startup.sh
Using CATALINA_BASE:   /usr/local/tomcat5
Using CATALINA_HOME:   /usr/local/tomcat5
Using CATALINA_TMPDIR: /usr/local/tomcat5/temp
Using JAVA_HOME:       /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/
root@Toshiba:~#

```

I am able to follow till step 4, I dont find any code to change port number in server.xml in step5. I find a blank server.xml page when I type 

```
 gedit usr/local/tomcat5/conf/server.xml 
```

The same when I type 
```
 gedit usr/local/tomcat5/conf/context.xml 
``` from step6 and
```
 gedit usr/local/tomcat5/conf/web.xml 
``` 
from step7. All the three xml files are empty. Can anyone plzz tell me what is my problem. I am able to start Tomcat but its not connecting to localhost.

Thanks.

---

### Post by Lod on 2006-09-16
> **bytestor said:**
>  

```
 gedit usr/local/tomcat5/conf/server.xml 
```

The same when I type 
```
 gedit usr/local/tomcat5/conf/context.xml 
``` from step6 and
```
 gedit usr/local/tomcat5/conf/web.xml 
``` 
from step7. All the three xml files are empty. Can anyone plzz tell me what is my problem. I am able to start Tomcat but its not connecting to localhost.

Thanks.Shouldn't there be a '/' in front of the filepath? Like this:
```
gedit /usr/local/tomcat5/conf/server.xml
```Otherwise your os is looking for the files in the wrong places if you're not in the root.

Personally I put the export JAVA_HOME and so in /etc/profile . It is more widely used in your system then (you have to log in again though).

---

### Post by PaulieG on 2006-10-12
All the instructions I could find about installing Tomcat (even 5.5) mention the requirement of installing the Java SDK (JDK).  I'm not sure why this is, since the Tomcat 5.5 release notes specifically say that the JDK is not required, and that JRE suffices.  Anyone care to comment? :-k

---

### Post by redblue on 2006-11-24
First Hello, this is my first post in here and actually my first week with Ubuntu.
I have installed Java and Followed the steps of installing Tomcat but i just cant start it. This is what i get.


```
redblue@proekt:~$ sudo sh /usr/local/jakarta-tomcat-5.0.0/bin/startup.sh
Using CATALINA_BASE:   /usr/local/jakarta-tomcat-5.0.0
Using CATALINA_HOME:   /usr/local/jakarta-tomcat-5.0.0
Using CATALINA_TMPDIR: /usr/local/jakarta-tomcat-5.0.0/temp
Using JAVA_HOME:       /usr/lib/j2sdk1.5-sun/

```


```
redblue@proekt:~$ su - redblue -c"/usr/local/jakarta-tomcat-5.0.0/bin/startup.sh"
The JAVA_HOME environment variable is not defined
This environment variable is needed to run this program

```

hmmm. after all it seems that it is working as a service, but are there any possible problems with the jave after that error?

---

### Post by hasuob on 2007-02-09
redblue, You've added JAVA_HOME to your ~/.bashrc file (after backing it up) right?
You might consider trying the command without the sh in front so it looks like this:
```

sudo /usr/local/jakarta-tomcat-5.0.0/bin/startup.sh

```

See if that helps.

I have a question for anyone who uncommented the invoker servlet from web.xml

I ran tomcat without trouble (got the tomcat page) when I first ran it. Then I stopped the server, uncommented both the servlet and servlet-mapping tags in the web.xml file, and now when I start tomcat and reload the page, I see only a blank screen. When I comment those tags out again, I see the page again. Any Idea what could be happening?

---

### Post by cefn on 2007-06-19
There's a current issue with Tomcat Version 5.5.20-4ubuntu1 as reported here which prevents startup and Tomcat opening a socket to launch its server. Netstat reports that no server has launched even though Tomcat reports no error..

[http://cefn.com/blog/ubuntutomcat.html](http://cefn.com/blog/ubuntutomcat.html)

---

### Post by chinijo on 2007-06-21
hellou, 
i tried  *sudo apt-get install sun-j2rel.5* but...

E: No se pudo bloquear /var/lib/dpkg/lock - open (11 Recurso temporalmente no disponible)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

What's the problem?

---

### Post by edu2004eu on 2007-06-26
None of these advices helped me install tomcat on my Ubuntu, since everything was different. I found a solution [here](http://www.kintespace.com/rasxlog/?p=468). Hope it will be useful to others too.

---

### Post by xaitienle on 2007-07-28
Hi all,

First, I couldn't extract the tomcat in to usr/lib directory. Unbuntu said that I have no right to access. So, I changed the target of extract file to my own directory. It worked fine. What was the problem with my decompression?

Second, in the .bashrc file, I wrote:

```
export JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun/
export CLASSPATH=/home/anhkhoab/Tomcat/apache-tomcat-5.5.23/common/lib/jsp-api.jar:/home/anhkhoab/Tomcat/apache-tomcat-5.5.23/common/lib/servlet-api.jar

```
Then, in the terminal console, I checked a code: 
 ```
sh /home/anhkhoab/Tomcat/apache-tomcat-5.5.23/bin/startuo.sh
```

and the result liked this:

```
Using CATALINA_BASE:   /home/anhkhoab/Tomcat/apache-tomcat-5.5.23
Using CATALINA_HOME:   /home/anhkhoab/Tomcat/apache-tomcat-5.5.23
Using CATALINA_TMPDIR: /home/anhkhoab/Tomcat/apache-tomcat-5.5.23/temp
Using JRE_HOME:       /usr/lib/jvm/java-1.5.0-sun/
touch: cannot touch `/home/anhkhoab/Tomcat/apache-tomcat-5.5.23/logs/catalina.out': No such file or directory
/home/anhkhoab/Tomcat/apache-tomcat-5.5.23/bin/catalina.sh: line 273: /home/anhkhoab/Tomcat/apache-tomcat-5.5.23/logs/catalina.out: No such file or directory
```

I couldn't start the Tomcat. What was my problem?

Best reagards,

---

### Post by amidude on 2007-08-08
I am unable to get through the first part of this process. I get the following error:

sudo apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-j2re1.5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-j2re1.5 has no installation candidate

Am I missing something? Any assistance would be greatly appreciated.

Okay, uninstalled everything and found another site that helped me get it loaded. I'm able to start Tomcat but I can't see anything when I go to [http://localhost:8180/](http://localhost:8180/)

---

### Post by digitalhillbilly on 2007-09-05
Hey amidude... Did you get it working yet? If not, try this method: 

jdk - [http://wiki.openbravo.com/wiki/index.php/Openbravo_Command_Line_Installation#Ubuntu_.2F_Debian_2](http://wiki.openbravo.com/wiki/index.php/Openbravo_Command_Line_Installation#Ubuntu_.2F_Debian_2)

tomcat - 
[http://wiki.openbravo.com/wiki/index.php/Openbravo_Command_Line_Installation#Ubuntu_.2F_Debian_3](http://wiki.openbravo.com/wiki/index.php/Openbravo_Command_Line_Installation#Ubuntu_.2F_Debian_3)

---

### Post by amanjsingh on 2007-09-15
> **bytestor said:**
> Hi I have the same problem as yours.  I am able to start tomcat but I get connection failed when I use [http://localhost/](http://localhost/)  or [http://localhost:8080/](http://localhost:8080/)

I get the following message when I start tomcat,

 ```

root@Toshiba:~# sh /usr/local/tomcat5/bin/startup.sh
Using CATALINA_BASE:   /usr/local/tomcat5
Using CATALINA_HOME:   /usr/local/tomcat5
Using CATALINA_TMPDIR: /usr/local/tomcat5/temp
Using JAVA_HOME:       /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/
root@Toshiba:~#

```


Thanks.

Hi, I have same problem. Tomcat starts (supposedly) but the browser cannot display anything. It says **Unable to connect**. Help.

---

### Post by digitalhillbilly on 2007-09-16
try port 8180

---

### Post by amanjsingh on 2007-09-16
> **digitalhillbilly said:**
> try port 8180

Actually my Java installation was messed up. Someone may be interested in knowing that your JRE path and configuring actual JVM being used are important for Tomcat to run properly.

Configure your correct JVM using - 
```
sudo update-alternatives --config java
```

and set the path using 
```
export JAVA_HOME="path to java directory"
```

And the most important thing being having two installations of Tomcat. version 5 and 5.5 and both were running. So, one service always used to stop the other service.

Now, I am running only one tomcat5.5 and it works fine.

---

### Post by fabiodasoghe on 2007-11-10
Nice tutorial, but maybe it's aimed to a desktop installation.
If someone was interested in a server installation, why not to install the official Tomcat 5.5 repository version? It's as simple as typing:

```
sudo apt-get install sun-java6-jre sun-java6-fonts
sudo apt-get install tomcat5.5
```
Then it won't start (duh!), but a little editing to /etc/default/tomcat5.5 resolves everything:

```
JAVA_HOME=/usr/lib/jvm/java-6-sun/jre
JAVA_OPTS="-Djava.awt.headless=true -Xms64M -Xmx512M -XX:MaxPermSize=128M"
TOMCAT5_SECURITY=no
```

Of course these are my personal settings: they may be different for different purposes.

And with this you get running as user tomcat55 on port 8180. If you want to go on port 80, you have to edit file server.xml and change the port number for the HTTP connector (again, my personal flavour). Thanks to jsvc this now works because it takes care of the user downgrading from root (which is needed to execute the startup script).

It seems in Gutsy there is a little bug in the startup script: [https://bugs.launchpad.net/bugs/161882](https://bugs.launchpad.net/bugs/161882) (there's a fast workaround, while waiting for the patch to be applied in the official package).

At last, I have a question: is there a way to configure jsvc in order to have the stdout and stderr in the old catalina.out file instead of the syslog? Now the Tomcat console log is almost unreadable! :-k

Hope this helps.

Cheers,

Fabio

---

### Post by lowebb on 2007-11-28
Guys need a little help here, I've done this and everything seems to be working fine, but no matter what port I use my web browser cant seem to connect to the server.

Is there something more I have to do to get a basic page up and running here???

---

### Post by lowebb on 2007-11-28
So an update, I've managed to get rid of all errors from the log but its still not starting. Here is the output

28-Nov-2007 21:30:58 org.apache.catalina.core.AprLifecycleListener lifecycleEvent
INFO: The Apache Tomcat Native library which allows optimal performance in production environments was not found on the java.library.path: /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/client:/usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386:/usr/lib/jvm/java-6-sun-1.6.0.03/jre/../lib/i386:/usr/java/packages/lib/i386:/lib:/usr/lib
28-Nov-2007 21:30:59 org.apache.coyote.http11.Http11BaseProtocol init
INFO: Initializing Coyote HTTP/1.1 on http-8180
28-Nov-2007 21:30:59 org.apache.catalina.startup.Catalina load
INFO: Initialization processed in 2080 ms
28-Nov-2007 21:30:59 org.apache.catalina.core.StandardService start
INFO: Starting service Catalina
28-Nov-2007 21:30:59 org.apache.catalina.core.StandardEngine start
INFO: Starting Servlet Engine: Apache Tomcat/5.5
28-Nov-2007 21:30:59 org.apache.catalina.core.StandardHost start
INFO: XML validation disabled
28-Nov-2007 21:30:59 org.apache.coyote.http11.Http11BaseProtocol start
INFO: Starting Coyote HTTP/1.1 on http-8180
28-Nov-2007 21:30:59 org.apache.jk.common.ChannelSocket init
INFO: Port busy 8009 java.net.BindException: Address already in use
28-Nov-2007 21:30:59 org.apache.jk.common.ChannelSocket init
INFO: JK: ajp13 listening on /0.0.0.0:8010
28-Nov-2007 21:31:00 org.apache.jk.server.JkMain start
INFO: Jk running ID=1 time=0/227  config=null
28-Nov-2007 21:31:00 org.apache.catalina.storeconfig.StoreLoader load
INFO: Find registry server-registry.xml at classpath resource
28-Nov-2007 21:31:00 org.apache.catalina.startup.Catalina start
INFO: Server startup in 1093 ms

It never seems to get past server startup in .......


Help me please!!!!!

---

### Post by myharshdesigner on 2007-11-29
it so nice seen easy

---

### Post by lowebb on 2007-11-30
> **myharshdesigner said:**
> it so nice seen easy

Cheers mate, lots of help

---

### Post by james_bandido on 2007-12-04
i have this error :

E: tomcat5.5: subprocess post-installation script returned error exit status 1
E: tomcat5.5-admin: dependency problems - leaving unconfigured
E: tomcat5.5-webapps: dependecny problems - leaving unconfigured

can someone please tell me what i did wrong and what i must do to correct this ? i'm just new and learning the ropes as i go along.

thank you in advance.

---

### Post by shaunbarlow on 2008-01-24
> **james_bandido said:**
> i have this error :

E: tomcat5.5: subprocess post-installation script returned error exit status 1
E: tomcat5.5-admin: dependency problems - leaving unconfigured
E: tomcat5.5-webapps: dependecny problems - leaving unconfigured

can someone please tell me what i did wrong and what i must do to correct this ? i'm just new and learning the ropes as i go along.

thank you in advance.

bump
I have the exact same problem.

I have also  tried installing from the tomcat5.5 package from debian sid as suggested here: [http://groups.google.com.au/group/linux.debian.bugs.rc/browse_thread/thread/d393086692406195/79bf65741e2a2676%2379bf65741e2a2676](http://groups.google.com.au/group/linux.debian.bugs.rc/browse_thread/thread/d393086692406195/79bf65741e2a2676%2379bf65741e2a2676)
and I get the same error. 

Any help would be greatly appreciated.

Cheers,
Shaun

---

### Post by shaunbarlow on 2008-01-24
> **shaunbarlow said:**
> bump
I have the exact same problem.


Solved!
Here are the steps I used. Please proceed with caution, backup before you try this, no guarantees, this is a guide to the steps i took that made it work. There may be something subtle that I did whilst trial and error was happening that i have failed to add here. If anyone has any info to add or corrections to make it would be greatly appreciated.
So disclaimer done, on with the show
in the terminal type:
sudo apt-get install sun-java6-jdk
(press enter)
sudo gedit /etc/init.d/tomcat5.5
(press enter)

in gedit
replace the text
set -e
with
#set -e

save and close 

go to the system menu to system>administration>software sources
click add
copy and paste the following line:
deb [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) unstable main contrib non-free
click add source
click add (again)
paste this:
deb-src [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) unstable main contrib non-free
click add source
click close
if sources prompts you to reload the repos then click reload
if not then in the terminal type:
sudo apt-get update
then type
sudo apt-get install tomcat5.5
follow the prompts and hopefully the package should install without errors

now go back into system>admin>software sources
and remove both of the debian sid repos that we added before
otherwise you will be getting everything from debian sid, which, if you don't know what that is (try googling around the place) then it's probably not a good idea.
Cheers all,
any pointers or erratum are most welcome
Shaun

---

### Post by PremierITA on 2008-02-06
Hello,
i installed tomcat with this procedure, but i'm unable to access Tomcat manager,

why?

Regards.

---

### Post by krepole on 2008-04-07
Did you try [http://localhost:8180/](http://localhost:8180/)  ?

I found these set of instructions from OpenBravo to be quite helpful.

[http://wiki.openbravo.com/wiki/Openbravo_Command_Line_Installation#Apache_Tomcat_installation](http://wiki.openbravo.com/wiki/Openbravo_Command_Line_Installation#Apache_Tomcat_installation)

---

### Post by malaka19 on 2008-07-31
I install tomcat like this. 

but when I try to run it tells 

"Cannot find ./catalina.sh"

please help

---

### Post by malaka19 on 2008-08-02
In ubuntu I followed the instruction to install aexactly like this.
When I run startup.sh it runs ok.
Giving the message

Using CATALINA_BASE:   /usr/local/tomcat
Using CATALINA_HOME:   /usr/local/tomcat
Using CATALINA_TMPDIR: /usr/local/tomcat/temp
Using JRE_HOME:       /usr/lib/jvm/java-6-sun

But when I type localhost/8080 it says failed to connect. I didn't change the default port number.

I am newbie. Please help. I thank you in advance.

---

### Post by vnzorro on 2008-09-09
If you've done everything as above but it doesn't work, try to set JAVA_HOME in catalina.sh
<code>
sudo gedit /usr/local/tomcatxx/bin/catalina.sh
</code>
insert the following line:
JAVA_HOME=/where-you-install-it

hope it works

---

### Post by badperson on 2008-09-28
HI,
I'm having a problem here:

I went through the steps outlined and set my environment variables at the bottom of my .bashrc file as follows:

```
export JAVA_HOME=/usr/bin
export CLASSPATH=/usr/share/tomcat5.5/common/lib/jsp-api.jar:/usr/share/tomcat5.5/common/lib/servlet-api.jar
```

The java and javac executables are in the usr/bin directories; none of the online examples I saw had that directory, but that's where mine are. 

by typing 
sudo bash startup.sh 
I get this:
```
jason@jason-kubuntu:/usr/share/tomcat5.5/bin$ sudo bash startup.sh
Neither the JAVA_HOME nor the JRE_HOME environment variable is defined
At least one of these environment variable is needed to run this program

```

I haven't gone in and changed the port settings and such in the xml file yet, because I just wanted to get this working. Did I take a wrong turn somewhere?
bp

---

### Post by DFHIII on 2008-10-23
In Step 2 - Get tomcat:

I downloaded tomcat to my desktop, the uncompressed it -- I think.  Where was the uncompressed package stored?  Where do I find it to move to /usr/local/ ?

Also, how do I uninstall a package such as this if I need to?

Thanks,

Dan H.

---

### Post by anwoke8204 on 2009-05-17
I keep getting the followning when I try to stop tomcat, I start it, but then can't browse it so I stop it and I get the following

Using CATALINA_BASE:   /usr/share/tomcat5.5
Using CATALINA_HOME:   /usr/share/tomcat5.5
Using CATALINA_TMPDIR: /usr/share/tomcat5.5/temp
Using JRE_HOME:       /usr/lib/jvm/j2sdk1.5-sun/
./catalina.sh: 348: /usr/lib/jvm/j2sdk1.5-sun//bin/java: not found

I have verified that java is in the listed directory, but it for some reason puts a double // in betwen sun and bin.  could that be my issue.  anyone know how I can resolve this issue?

Many thanks,
Andrew

---

### Post by nayanjyoti on 2009-07-22
I am facing a problem when I try to start tomcat 5.5 in ubuntu 8.04.
The following message is shown
/usr/share/tomcat5.5/bin/startup.sh 
Using CATALINA_BASE:   /usr/share/tomcat5.5
Using CATALINA_HOME:   /usr/share/tomcat5.5
Using CATALINA_TMPDIR: /usr/share/tomcat5.5/temp
Using JRE_HOME:       /usr/lib/jvm/java-1.5.0-sun
touch: cannot touch `/usr/share/tomcat5.5/logs/catalina.out': Permission denied
/usr/share/tomcat5.5/bin/catalina.sh: 348: cannot create /usr/share/tomcat5.5/logs/catalina.out: Permission denied
 Please help

---

### Post by MarcioAB on 2009-08-02
Hello, need some help here, please.

Just installed Tomcat5.5 from the repository: apt-get install tomcat5.5

At the end the message is:
* Starting Tomcat servlet engine tomcat5.5  [OK]

But pointing Firefox to 127.0.0.1:8180, shows nothing (a blank screen). I expected to see the Tomcat welcome page.
By the way, if I stop the service ( service tomcat5.5 stop), and point Firefox to 127.0.0.1:8180 a got the expected "Unable to connect" screen.

Any instruction about what else should I do to have it working will be very much welcome.

Thank you
Marcio

---

### Post by uncibex on 2009-09-07
> But pointing Firefox to 127.0.0.1:8180, shows nothing (a blank screen). I expected to see the Tomcat welcome page.
By the way, if I stop the service ( service tomcat5.5 stop), and point Firefox to 127.0.0.1:8180 a got the expected "Unable to connect" screen.

I'm having the same problem and I'm not sure what else I need to set.  Any suggestions?

---

### Post by careertargetph on 2009-09-08
Thanks forgiving me an idea. I encountered this kind of problem while installing tomcat in my pc. I upgrade my tomcat. I'm using now 6.0

---

### Post by nikhilbhardwaj on 2009-09-10
> **jreymol said:**
> 

3. I executed this lines:

```
chmod 755 /etc/init.d/tomcat
ln -s /etc/init.d/tomcat /etc/rc1.d/K99tomcat
ln -s /etc/init.d/tomcat /etc/rc2.d/S99tomcat

```

and now my tomcat is there when I start up my linux  \\:D/ 

BE AWARE: My experience with linux is very, very limited. I cannot be sure this lines of code are perfect. I just can say they work for me.


the lines of code are correct but i'd also like to add these
```

ln -s /etc/init.d/tomcat /etc/rc0.d/K99tomcat
ln -s /etc/init.d/tomcat /etc/rc6.d/K99tomcat

```

this will ensure that tomcat is stopped properly whenever you shutdown or reboot your computer

similar entries can be added to start it for different runlevels too

---

### Post by pieroog on 2010-05-21
Hi, 

I have an application built in Java/GWT which is deployed within Tomcat 5.5 environment. The issue is with its database backened which is written in PHP thus resides on Apache. I've tried to run PHP on Tomcat, but many people disadvised me this approach. 

Is there any way to treat sub-folder of the Tomcat's application as a proxy "gateway" to apache's php services without any Same-Origin-Policy issues? I've seen tons of texts on proxy with Apache to Tomcat, but none that would deal with Tomcat -> proxy-> Apache.

thanks in advance
pieroog

---

### Post by meomike2000 on 2010-05-30
help please. i have installed java and tomcat. all that seams to work fine.
i can type in java - version and i get this

java version "1.6.0_20"
Java(TM) SE Runtime Environment (build 1.6.0_20-b02)
Java HotSpot(TM) Client VM (build 16.3-b01, mixed mode, sharing)


i can type in javac - help and i get the response with all the javac help info...

when i start tomcat via sh /usr/local/tomcat/bin/startup.sh i get this response

Using CATALINA_BASE:   /usr/local/tomcat
Using CATALINA_HOME:   /usr/local/tomcat
Using CATALINA_TMPDIR: /usr/local/tomcat/temp
Using JRE_HOME:        /usr/lib/jvm/java-6-sun/
Using CLASSPATH:       /usr/local/tomcat/bin/bootstrap.jar

i can go to localhost:8080 and i get the tomcat page so i know the server is running correctly.
i can load the sample or localhost:8080/sample and get the sample HelloWorld page and all works well.

i type up this BasicServlet.java and  when i try to compile it i get these errors:

BasicServlet.java:1: package javax.servlet does not exist
import javax.servlet.*;
^
BasicServlet.java:2: package javax.servlet.http does not exist
import javax.servlet.http.*;


any help would be great, thanks mike

Problem solved: was a problem with JAVA_HOME, i missed a directory..... whatyaknow....

---

### Post by duleep on 2010-05-31
my Apache server has folder that contain video files that video files 

owner Apache and files permission are 775

but i try to download using file URL but that give to me "no permission" what is the reason for this?

> 
[root@ucsctv video_source]# ls -l
total 1068824
-rwxrwxrwx 1 apache apache   5713979 Mar 23 15:14 12.wmv
-rwxrwxrwx 1 apache apache  16441804 Mar 23 15:16 13.mp4
-rwxrwxrwx 1 apache apache 734187520 Mar 24 14:44 26.avi
-rwxrwxrwx 1 apache apache 104472900 May  4 11:18 31.avi
-rwxrwxrwx 1 apache apache 102854208 May  5 14:31 32.wmv
-rwxrwxrwx 1 apache apache 108368816 May 24 16:08 34.wmv



---

### Post by Aghilkrishna on 2011-03-02
Hi..... I just followed as mentioned but i got some error message says:

"Cannot find ./catalina.sh
This file is needed to run this program
":confused:

---

### Post by varunaub on 2011-09-03
I am not able to move the Uncompressed package in to the /usr/local/ directory by coping or cut and pasting. 
 Please advice on 
   
                                   **How to move tomcat5 Uncompressed package in to the /usr/local/ directory or is there a better location than this** 
                                       **What is the default setting of privileges and permissions regarding file access in a Linux system**

---

