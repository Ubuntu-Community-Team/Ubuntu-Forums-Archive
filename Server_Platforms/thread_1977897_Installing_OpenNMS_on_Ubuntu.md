---
title: "Installing OpenNMS on Ubuntu"
date: 2012-05-10
forum: Server Platforms
---

### Post by victor1104 on 2012-05-10
Hi Everyone Im just a complete 1% knowledge in ubuntu. I am just learning this only with your help and the net and no one can train me here about ubuntu so please bear with me about this no brainer questions. 
 
Im trying to install opennms unstable version by just following the instructions from [http://www.opennms.org/wiki/Installation:Debian](http://www.opennms.org/wiki/Installation:Debian). 
 
Here are the files im able to download as per requirement:
jdk-7-linux-x64.tar.gz
apache-tomcat-5.5.35-src.tar.gz
rrdtool-1.3.3-src
postgresql-9.0.2.tar.gz
FYI my ubuntu version is only 7.10 \n \1
 
 
Here are the following steps im done:
[FONT=Verdana]My 1st step is I created a details on /etc/apt/sources.list.d/opennms.list as shown below[/FONT][FONT=Verdana]deb [/FONT][[FONT=Verdana]http://debian.opennms.org[/FONT]]("http://debian.opennms.org/")[FONT=Verdana] ***unstable*** maindeb-src [/FONT][[FONT=Verdana]http://debian.opennms.org[/FONT]]("http://debian.opennms.org/")[FONT=Verdana] ***unstable*** main[/FONT][FONT=Verdana]then followed by: wget -O - [http://debian.opennms.org/OPENNMS-GPG-KEY](http://debian.opennms.org/OPENNMS-GPG-KEY) | sudo apt-key add -[/FONT][FONT=Verdana]Then next comes:[/FONT][FONT=Verdana]sudo apt-get updateapt-cache search opennms (showed the list of opennms)[/FONT][FONT=Verdana]I STOPPED at doing the POSTGRESQL. It's not letting me :([/FONT][FONT=Verdana][/FONT] [FONT=Verdana]i typed: **sudo apt-get install postgresql -> says could not find package**[/FONT][FONT=Verdana]i typed: **sudo apt-get install postgresql-9.0.2.tar.gz -> says could not find package**[/FONT][FONT=Verdana][/FONT] [FONT=Verdana]This time I extracted the postgresql-9.0.2.tar.gz[/FONT][FONT=Verdana]then i typed: **sudo apt-get install postgresql-9.0.2 -> says could not find package**[/FONT]**[FONT=Verdana][/FONT]** [FONT=Verdana]I understand that i am not in the right path. Can someone tell me how to please? Im seeing those files I downloaded on the desktop.[/FONT][FONT=Verdana][/FONT] [FONT=Verdana]Thank you all in advance.[/FONT]

---

### Post by lisati on 2012-05-10
Hiya! I've split your support request into its own thread, because a lot can happen in three years.

---

### Post by victor1104 on 2012-05-10
Thank you very much lisati ):P . Any thoughts about my issue? I apologize I dont know why the message above has been compressed so it might really looked hard to read. Let me re-paste and lets see if this will be more better to read :)
 
The main issue is: 
 
[COLOR=black][FONT=Verdana]i typed: **sudo apt-get install postgresql -> says could not find package**[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana][COLOR=black][FONT=Verdana][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana]i typed: **sudo apt-get install postgresql-9.0.2.tar.gz -> says could not find package**[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana][COLOR=black][FONT=Verdana]This time I extracted the postgresql-9.0.2.tar.gz[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR][COLOR=black][FONT=Courier New][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]then i typed: **sudo apt-get install postgresql-9.0.2 -> says could not find package**[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR][COLOR=black][FONT=Courier New][/FONT][/COLOR] 
[COLOR=black][FONT=Courier New] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I understand that i am not in the right path. Can someone tell me how to please? Im seeing those files I downloaded on the desktop.[/FONT][/COLOR][COLOR=black][FONT=Courier New][/FONT][/COLOR]
[COLOR=black][FONT=Courier New] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Thank you all in advance![/FONT][/COLOR]
[/FONT][/COLOR][COLOR=black][FONT=Courier New][/FONT][/COLOR] 
[/FONT][/COLOR][COLOR=black][FONT=Courier New][/FONT][/COLOR]

---

### Post by Habitual on 2012-05-11
[http://www.opennms.org/documentation/installguide.html](http://www.opennms.org/documentation/installguide.html)

---

