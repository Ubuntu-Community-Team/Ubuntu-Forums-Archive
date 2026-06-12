---
title: "Person connected to my pc"
date: 2009-12-04
forum: Security
---

### Post by dontgetshocked on 2009-12-04
I am unsure of what exactly happened but I did not have firestarter started then but when I cam back to my pc it showed someone connected to my pc.
adsl-158-3-175.asm.bellsouth.net
Which is BellSouth.net

I have a router that is secure, at least I think it is.

Is this anything to be worried about? I disconnected the person .

---

### Post by mikewhatever on 2009-12-05
Please elaborate, on how did you know that someone was connected to your PC.

---

### Post by BkkBonanza on 2009-12-05
show output for "sudo netstat -lntp"
it will list which processes are listening...
if you have a p2p program like Skype installed and running then you will have related connections that are to seemingly random addresses.

---

### Post by dontgetshocked on 2009-12-05
I know because I saw beside my internet connection another connection showing South Western Bell and i have Comcast as my provider.The Ip was different than mine.
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1269/cupsd      
tcp6       0      0 :::139                  :::*                    LISTEN      1212/smbd       
tcp6       0      0 :::5900                 :::*                    LISTEN      1676/vino-server
tcp6       0      0 ::1:631                 :::*                    LISTEN      1269/cupsd      
tcp6       0      0 :::445                  :::*                    LISTEN      1212/smbd       
david@david-desktop:~$ 
This is my output NOW, not then.

---

### Post by lisati on 2009-12-05
edit: never mind

---

### Post by mikewhatever on 2009-12-05
> **dontgetshocked said:**
> I know because I saw beside my internet connection another connection showing South Western Bell and i have Comcast as my provider.The Ip was different than mine. ............


Well, the whole point of internet is for computers being able to connect to each other. Would it surprise you, that while writing posts here, your computer maintains a connection to ubuntuforums.org's IP, which is different from yours?

---

### Post by BkkBonanza on 2009-12-05
The confusing thing here is that no one really knows what you mean by "I saw beside my internet connection"...

Can you desribe more clearly where you saw this info about a second connection? Because this makes all the difference in the world. You may just be confused by some information you saw that doesn't indicate anything wrong. Generally speaking, if you were hacked and someone got into your machine it would not show up anywhere on the screen.

---

### Post by dontgetshocked on 2009-12-05
I have my connection that shows up as a wired internet connecion next to my sound icon so that I know that  I am online is 24/7 and Yes I not too stupid to know the net sites are really ip addresses! However next to my REAL connecxtion icon there was one which I NEVER have seen from south western bell who I dont have ANY deaings with.My mail program, Thunderbird,Firefox and a terminal were open when I saw this.Firefox and Thunderbird are always open but not another internet connection.Hope this makes sense.The terminal scares me.

---

### Post by BkkBonanza on 2009-12-05
That is odd. Can you describe what the second icon looked like? Was it the same as any other icons you have seen, like terminal? Normally you cannot have two connections to two ISPs without quite unusual config changes to support it. It sounds like you don't usually use terminal. So this terminal that was open was not one you opened? Were you installing software at the time? Have you noticed anything since?

---

### Post by dontgetshocked on 2009-12-05
Yes the icon looked like 2 things connected together,(sorry) hard to describe.I am familiar with terminal, it's to me like od dos commands.2 square boxes like SWB usues.Its odd I know bit 2 different sessioms were open.

---

### Post by BkkBonanza on 2009-12-05
Sounds like maybe someone using VNC to control your machine.
From your info above it indicates you're running a VNC server,

tcp6 0 0 :::5900 :::* LISTEN 1676/vino-server

Do you have a specific reason to run that? This program is designed to give other users access and control of your desktop remotely. But it is not by default a secure/encrypted access method. To use it securely you must use good passwords and run it through a tunnel like ssh. 

If it wasn't your intention to enable remote control of your desktop then you should disable or uninstall the VNC server. You only need a client to access and control other machines.

---

### Post by mikewhatever on 2009-12-05
> **dontgetshocked said:**
> I have my connection that shows up as a wired internet connecion next to my sound icon so that I know that  I am online is 24/7 and Yes I not too stupid to know the net sites are really ip addresses! However next to my REAL connecxtion icon there was one which I NEVER have seen from south western bell who I dont have ANY deaings with.My mail program, Thunderbird,Firefox and a terminal were open when I saw this.Firefox and Thunderbird are always open but not another internet connection.Hope this makes sense.The terminal scares me.

I didn't say you were stupid, just needed to squeeze some info out of you to help us help you. Thank you for explaining properly.
The icon in the panel strongly suggests a vnc connection. It would be interesting to look at the history of terminal commands, <history | tail -n 50>, and I'd also recommend disabling remote desktop for now.

---

### Post by arvevans on 2009-12-05
Maybe need to back up a bit here and take a look at the original question and connection information.  

The Internet supplier was given as "Comcast", but no indication of whether Internet access is via wireless, cable, or landline.  

The Service was described as being ADSL, which would indicate it is via landline.

Comcast probably does not operate landline systems, but does sell ADSL services on landline or cable via the local service provider.  Might this person be in an area where ADSL landline service is provided by Southwest Bell?  If YES, then the ADSL connection may very well show as a Southwest Bell connection, even though the authentication server is run by Comcast.
_._

---

