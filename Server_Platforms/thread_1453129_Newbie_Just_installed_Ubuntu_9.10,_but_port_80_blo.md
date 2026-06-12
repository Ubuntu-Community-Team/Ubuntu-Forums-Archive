---
title: "Newbie: Just installed Ubuntu 9.10, but port 80 blocked?"
date: 2010-04-12
forum: Server Platforms
---

### Post by danandjan on 2010-04-12
Hello, I am completely new to Linux.  I installed Ubuntu 9.10 and tomcat 6 java servlet container.  I am trying to run the tomcat server on port 80, so I edited tomcat's configuration file (server.xml) and changed the default port from "8080" to "80".  I launched tomcat server, went to my browser and entered: "http:/myIP/mywebapp", but it says can not find server/location.  Then I edit the server.xml and revert back to port "8080" and then enter: "http://myIP:8080/mywebapp" and everything works fine.  So my guess is some other service is taking up port 80, but I would think not, since I just installed Ubuntu and made sure apache isn't installed or running.

So I went to "System" --> "Administration", then choose "Network Tools".  I then executed Netstat and did not see anything taking up port 80, but I do see port 8080 taken (assuming it is the tomcat server).  Then I also did a Port Scan and entered my IP number. Again, I don't see port 80 taken, but do see 8080 being used.

I had a winxp laptop computer behind home wireless and was running tomcat 6 server fine with it, but it over-heated and died recently.  So I got a used laptop and just installed Ubuntu 9.10.  I have not changed my wireless router settings.  It is the same as before.  So I have ruled out my home's hardware/network equipment.

So here now I sit, wondering what is up?? :-)

For security reasons, is port 80 initially blocked by Ubuntu for some reason?  Is there something I have to do beforehand to free up port 80?
Thanks in advance for any help you can provide.

EDIT/UPDATE:
Errr!  I found this forum post:
[http://ubuntuforums.org/showthread.php?t=803801](http://ubuntuforums.org/showthread.php?t=803801)

According to one of the posters, he states the following:
"All ports below 1024 can only be opened by root. Apache, for example, uses some nice tricks to use port 80 and still be safe. I don't know about Tomcat (I always run it on 8080).

Allowing ports through a firewall (ufw seems to be a tool to control iptables) is something completely different."

Is this TRUE?  That sucks...:-(  Oh well, I guess people will have to type an extra 5 characters in the URL.

-Dan

---

### Post by Iowan on 2010-04-13
I'm hoping your thread gets better support in the Server Platforms forum.
 (A little "bump" might not hurt, either...)

---

### Post by danandjan on 2010-04-14
Thanks.  It turns out it was indeed related to Linux's privilege strictness.  I ran sudo -s command to switch to root user then started the tomcat server.  Now it lets me run port 80.  I just wished there was some kind of error message or some other kind of indication.  Oh well, not like Ubuntu comes with a manual.  Thank goodness for Google although when I was taking CS classes, Google didn't exist back then.  These young people sure got it easy.  :-)

---

