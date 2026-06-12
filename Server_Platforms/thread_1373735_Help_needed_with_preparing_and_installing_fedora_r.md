---
title: "Help needed with preparing and installing fedora repositories"
date: 2010-01-06
forum: Server Platforms
---

### Post by Snow05 on 2010-01-06
Hey there!
 
I'm new to linux, but I do know a bit about it. Still, I seem not to be able to properly install (or configure) Java (JDK) for some reason. And now the installation of fedora repositories is stoped in a way. I found no topic on this issue anywhere on the web, only the documentation.
 
Here's the thing I'm trying to fix for the past two days.
I installed JDK using KPackageKit and also manualy. When I try the command: java -version it shows the correct one, but when writing the command: echo $JAVA_HOME nothing shows up. But it should according to the fedora repositories installing notes: [http://fedora-commons.org/confluence/display/FCR30/Installing+Java](http://fedora-commons.org/confluence/display/FCR30/Installing+Java)
 
I also don't know how to set the environment variables of it like the installation notes state:
[http://fedora-commons.org/confluence/display/FCR30/Installation+and+Configuration+Guide](http://fedora-commons.org/confluence/display/FCR30/Installation+and+Configuration+Guide)
 
So I'd like your help and guidance on this issue since I want to install the Fedora repositories. I will also ask right here, when the next problem occurs. Or maybe if someone is so good to guide me step by step for quick install, cause I think I'll have difficultis all the way. :)
 
p.s.:I use Ubuntu 9.10 Server Edition with KDE.

---

### Post by scottuss on 2010-01-06
Firstly, you mean Ubuntu Server edition, right? You don't have a GUI?

Secondly, you do realise that you can't use the Fedora repositories because they're for Fedora i.e, not Ubuntu?

The JDK (and JRE etc) are all in the Ubuntu repositories

---

### Post by Snow05 on 2010-01-06
> **scottuss said:**
> Firstly, you mean Ubuntu Server edition, right? You don't have a GUI?
 
Secondly, you do realise that you can't use the Fedora repositories because they're for Fedora i.e, not Ubuntu?
 
I did install a GUI,it's KDE. I just now realized I "taged" the topic wrong.
An the Fedora Repositories != linux Fedora.
 
Here's the main page for more information, if needed: [http://www.fedora-commons.org/](http://www.fedora-commons.org/)
 
So before you ask/write question about fedora linux, please see the above links for clarification.

---

### Post by munky99999 on 2010-01-06
Why are you using fedora repos for ubuntu?

---

### Post by munky99999 on 2010-01-06
> **Snow05 said:**
> I did install a GUI,it's KDE. I just now realized I "taged" the topic wrong.
An the Fedora Repositories != linux Fedora.
 
Here's the main page for more information, if needed: [http://www.fedora-commons.org/](http://www.fedora-commons.org/)

Oh wow. That's confusing. They ought to change their name.

So um. Download the Jar file there on their front page in top left.

```
Sudo apt-get install sun-java6-jdk
```

open terminal. cd to the folder your downloaded it to.

```
java -jar fcrepo-installer-3.3.jar
```

---

### Post by Snow05 on 2010-01-06
I did that already, I wrote it in the first post.
 
>  
Here's the thing I'm trying to fix for the past two days.
I installed JDK using KPackageKit and also manualy. When I try the command: java -version it shows the correct one, but when writing the command: echo $JAVA_HOME nothing shows up. But it should according to the fedora repositories installing notes: [http://fedora-commons.org/confluence...nstalling+Java]("http://fedora-commons.org/confluence/display/FCR30/Installing+Java")

I also don't know how to set the environment variables of it like the installation notes state:
[http://fedora-commons.org/confluence...guration+Guide]("http://fedora-commons.org/confluence/display/FCR30/Installation+and+Configuration+Guide")

 
I also had problems because when I tried to update java with something like this:
```
sudo update-alternatives
```
I got an "error" that the documentation file needs to be downloaded.

---

### Post by scottuss on 2010-01-06
Apologies for jumping to the wrong conclusion.

Perhaps you should have been more specific, but perhaps also I should have followed the links.

---

### Post by Snow05 on 2010-01-06
It's OK. Maybe I should used upper case for the name. ;)
 
 
Well, concerning the name they agreed to it.
Check the year 2005 [http://www.fedora-commons.org/about/history](http://www.fedora-commons.org/about/history)
 
Now please help with the java configuration, or I'll go crazy and install Windows instead :D

---

### Post by Snow05 on 2010-01-06
I think I just made a stupid mistake. :( :)
 
I wanted to follow the instructions a bit so I installed the latest java within the jdk1.6.0_17 folder and then moved it to (root)/usr/local/. 
 
I checked if the version is new with java -version, but it doesn't even state the previous version now.
 
Now how to delete the folder in usr/local , since it's in root? :(
 
EDIT:
 
I did delete it now with the following command:" sudo chown username:usergroup /usr/local" . Did I do something wrong that I changed the properties from root to username?

---

### Post by Snow05 on 2010-01-07
So, no one can help? :(

---

### Post by Snow05 on 2010-01-08
> **munky99999 said:**
> Oh wow. That's confusing. They ought to change their name.
 
So um. Download the Jar file there on their front page in top left.
 
```
Sudo apt-get install sun-java6-jdk
```
 
open terminal. cd to the folder your downloaded it to.
 
```
java -jar fcrepo-installer-3.3.jar
```
 
Now I uninstalled (sudo apt-get remove sun-java-*) and reinstalled it with your command.
Checked with java -version and it shows the correct one.
 
How do I set the variables? Since I don't know where did it install the java. This is really confusing... I want that the command "echo $JAVA_HOME" would output something.

---

### Post by Snow05 on 2010-01-11
Hello. I did install the newest java manually, found a lovely tutorial o this site. Now the echo command works.
But since I don't want to mess things up, maybe you can help me with the next step.
 
Making variable paths for fedora and catalina, the instructions are saying this:
 
> This must include the Java and Fedora bin directories. For UNIX derivatives, this will be $FEDORA_HOME/server/bin, $FEDORA_HOME/client/bin and usually $JAVA_HOME/bin. 
 
> If Fedora is configured to use Tomcat, CATALINA_HOME must be set before starting Fedora. If using the quick install option, CATALINA_HOME should be set to $FEDORA_HOME/tomcat
 
For this two I don't know exactly how to do this.
I wrote
```
sudo -i
echo "export FEDORA_HOME=/usr/local/fedora/server/bin" >> /etc/profile
echo "export FEDORA_HOME=/usr/local/fedora/server/bin" >> /etc/bash.bashrc
exit

```
and
```
sudo -i
echo "export CATALINA_HOME=/usr/local/fedora/tomcat" >> /etc/profile
echo "export CATALINA_HOME=/usr/local/fedora/tomcat" >> /etc/bash.bashrc
exit

```
 
But I don't know if that is enough. I think I still have to add the PATH=* sentences. Any help apreciated.

---

### Post by Snow05 on 2010-01-11
Somehow I got the variables set. Now I started Fedora up.
 
But I still think I'll maybe need help to set everything up to work flawlessly.
 
EDIT: Well, I hope this was it.

---

