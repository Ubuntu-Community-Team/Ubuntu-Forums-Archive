---
title: "You Have Chosen To Open"
date: 2011-04-17
forum: Server Platforms
---

### Post by coljohnhannibalsmith on 2011-04-17
Hello,

When I try to access Tomcat6 from Firefox, I get the following message:


You have chosen to open


Which is a: BIN file
from: [http://localhost:8080](http://localhost:8080)

Would you like to save this file?


This is the location of my *Tomcat6-server*; however I still get this message after I completely uninstall *Tomcat6*.  I also get similar messages in Opera and Konqueror; so this is either system related, or the other browsers are sharing *config-files* with FireFox.


I have had similar problems with FireFox in the past, and all I could do was stop going to the site that caused the problem.  I've read that this might be related to MIME types?


Any help appreciated.



Thanks, Hannibal

---

### Post by coljohnhannibalsmith on 2011-04-17
It definitely looks like it's MIME type related.  The last type of file I downloaded last night was a Windows.exe, which I believe is a Binary file.

What gets me though is that my Tomcat6 webroot only has other folders in it, which is probably why there's a blank space in the message where the file name should be.

I've attached a screenshot to illustrate this.



Hannilbal

---

### Post by coljohnhannibalsmith on 2011-04-17
Here's more information:

MIME types can be set in a variety of places, one of which is:

*/etc/mime.types*

Another is in Tomcat6:

*/etc/tomcat6/web.xml*

Also, browser actions can be set in:

*about:config*


Also, I've read that Tomcat6 may be sending the wrong *'content-type'* in the ***http-header***.

When typing [http://localhost:8080/](http://localhost:8080/) into the address field of FireFox, the index.html file that displays the "It Works" message is stored here:

file:///var/lib/tomcat6/webapps/ROOT/index.html

I typed this into the address-bar and the "It-Works" message displayed normally as shown below:


**It works !**

  If you're seeing this page via a web browser, it means you've setup Tomcat successfully. Congratulations!


However, when typing the following into the address-bar:

[http://localhost:8080/ROOT/index.html](http://localhost:8080/ROOT/index.html)

 which forces the display of index.html; the following machine code is displayed:


p&#65533;&#65533;¥ô!-]ñÝHe¹òT8é4;Ü¶ ëLl$×ô    &#8250;¡&#8216;è9&#8226;Äé×GúÅO\&#8221;~5'[G:&#8249;`MáÓS,%*Äfæêâí/C{4}·ü1_&#8212;àÙ$¢Fz^Z7#Wt½?ÒD\Û÷Êàr}ô&#376; Là°Í    ¼´çè


This indicates to me that the wrong content-handler 'is' being used to display this content, which points to the wrong content-type being sent by Tomcat6 in the http-header, or FireFox using the wrong content-handler irregardless of the information present in the http-header.


* Tomcat6 was working prior to this problem; so I know it should work.


* I've completely reinstalled Tomcat6, including deleting the application folders, so that all of the files would be replaced, which I verified.


* I've completely reinstalled FireFox; but did 'not' remove the config files.


* Rebooted several times, with no results.


Prior to Tomcat6 crashing, I had loaded a program into 'wine' which caused a system lock-up twice. I then removed the offending program, and reinstalled Tomcat6 again, with dissapointing results.



It certainly seems like I've got this narrowed down; but if someone could tell me which settings to change, that would be extremely helpful.




Thanks, Hannibal

---

### Post by coljohnhannibalsmith on 2011-04-17
Well, I found a fix; but...

God what a horrible night...  I basically tore my system to shreds trying to solve this...


Here's what I've discovered:

I had to change default ports on Tomcat6 to get it to start working again.  The procedure is as follows:


**Changing default ports**

                                                                                  By default Tomcat 6.0 runs a HTTP connector on port 8080 and an AJP connector on port 8009. You might want to change those default ports to avoid conflict with another server on the system. This is done by changing the following lines in /etc/tomcat6/server.xml:

                   <Connector port="8080" protocol="HTTP/1.1" 
               connectionTimeout="20000" 
               redirectPort="8443" />
...
<Connector port="8009" protocol="AJP/1.3" redirectPort="8443" />


Why I had to do this, when the installation was already running is a
mystery...


Here's what I'm thinking:

In addition to Tomcat6 running on port:8080, I also have 'YaCy' running
nearby on port:8090.  I have no idea if these two were actually stepping
on oneanother, and YaCy was still running fine; but their proximity in port
numbers makes me a little suspicious.

I also recently installed 'gtk-gnutella' and 'gnunet-gtk,' so either
or both of these may have daemons running, that could have affected
Tomcat6.  gtk-gnutella listens on port:21238, so I find it difficult 
to believe that this ap could be the problem.

Lets try gnunet-gtk...  Here we go...  ***It's running on port:8080.***  Guess I need
to change that!

Both of the above aps look pretty dead, so I guess I've got some more trouble-shooting
to do...


Sorry about the stream-of-conciousness writing; but I've been up all night
with this one, and this is about the best I can do right now.


BTW, the best tutorial I've found for configuring Tomcat6 is:

[https://help.ubuntu.com/10.04/serverguide/C/tomcat.html](https://help.ubuntu.com/10.04/serverguide/C/tomcat.html)


The rest are crap...




Hannibal

---

