---
title: "Remote desktop"
date: 2014-03-09
forum: Ubuntu Development Version
---

### Post by Double.J on 2014-03-09
Hi all just popped 14.04 onto my system, submitted a few crashes to launchpad but all in all for an alpha, very impressed how far along it is!

I know this is an advanced feature t bring up in an alpha release, but just noticed I cant connect through VNC from my Ipad (Works flawlessly from 12.04 and 13.10) get the message that "the VNC server is not set up to authenticate VNC" in two years of running a remote ubunutu on my ipad I've never seen this. I've never had to do anymore than use the GUI to set up remote desktop before... Just wondering where to start trouble shooting the VNC server?

---

### Post by nimsreny2 on 2014-03-10
Hello Everyone,

I need your help to resolve the issue with VNC - Remore desktop connection. I upgraded my ubuntu from 12.04 LTS to 14.04 (Alpha) today. I was able to connect to Ubuntu desktop (12.04) from my IPAD using HippoRemote LIte or RealVNC before.  But after upgradation to 14.04, this is not working all of a sudden. I tried many options to the best of my knowledge, including but not limited to, changing / restarting my router settings, reinstalling VNC server etc, changing default port 5900 to different and port forwading etc. But none of them worked. 

It seems VINO is not listening to ipv4 connections, may be it conflicts with ipv6.  Could any of you please help me how I can get through this. 


[FONT=Courier New][FONT=Courier New]nims@reny:~$ netstat -alpn | grep :5900
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
tcp        0      0 0.0.0.0:5900            0.0.0.0:*               LISTEN      18615/vino-server
[COLOR="#FF0000"]tcp6       0      0 :::5900                 :::*                    LISTEN      18615/vino-server[/COLOR][/FONT][/FONT]


Thanks!
nimsreny

---

### Post by monkeybrain20122 on 2014-03-10
The purpose of pre-release is to test for bugs, so you should file a bug report. :) This thread should be in the ubunu+1 subforum where the testers may give you better advice.

---

### Post by nimsreny2 on 2014-03-10
Thanks for quick response. I'm new to this forum. Could you please suggest me how I can move this thread to ubunu+1 subforum?

---

### Post by nimsreny2 on 2014-03-10
Hello Everyone,

I need your help to resolve the issue with VNC - Remore desktop  connection. I upgraded my ubuntu from 12.04 LTS to 14.04 (Alpha) today. I  was able to connect to Ubuntu desktop (12.04) from my IPAD using  HippoRemote LIte or RealVNC before.  But after upgradation to 14.04,  this is not working all of a sudden. I tried many options to the best of  my knowledge, including but not limited to, changing / restarting my  router settings, reinstalling VNC server etc, changing default port 5900  to different and port forwading etc. But none of them worked. 

I am not sure, but it seems VINO is not listening to ipv4 connections, may be it conflicts  with ipv6  Could any of you please help me how I can get through this. 


[FONT=Courier New][FONT=Courier New]nims@reny:~$ netstat -alpn | grep :5900
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
tcp        0      0 0.0.0.0:5900            0.0.0.0:*               LISTEN      18615/vino-server
[COLOR=#FF0000]tcp6       0      0 :::5900                 :::*                    LISTEN      18615/vino-server[/COLOR][/FONT][/FONT]


Thanks!
nimsreny

---

### Post by nimsreny2 on 2014-03-10
OKay. I am unable to rmove this thread nor delete. So I posted a thread in ubuntu+1 subform. Below is the link

[http://ubuntuforums.org/showthread.php?t=2210268&p=12952347#post12952347](http://ubuntuforums.org/showthread.php?t=2210268&p=12952347#post12952347)

---

### Post by Double.J on 2014-03-10
Hey this is exactly the same issue as I reported here
[URL="http://ubuntuforums.org/showthread.php?t=2210243"]
http://ubuntuforums.org/showthread.php?t=2210243[/URL]


suggest merging threads?

additionally i also updated from 12.04 using dist-upgrade. I tried all these steps yesterday, no joy either.
this morning before going to work I booted into the live environment and it worked flawlessly. I suspect it is an issue updating from 12.04.

i set it installing a clean 14.04 before i left for work to test further when i get home. Will also test upgrade from  13.10 later then submit data to launchpad.

---

### Post by cariboo on 2014-03-10
Merged two similar threads.

---

### Post by bapoumba on 2014-03-10
Moved to Ubuntu +1.

---

### Post by cariboo on 2014-03-10
Merged another one. :)

---

### Post by nimsreny2 on 2014-03-11
Hi Everyone,

As suggested by many experts, I have reported a bug in launchpad. Here is the link to it. This is still in investigation.

[https://bugs.launchpad.net/ubuntu/+source/vino/+bug/1290666](https://bugs.launchpad.net/ubuntu/+source/vino/+bug/1290666)

Thanks!

---

### Post by nimsreny2 on 2014-03-11
Thanks everyone for their inputs. As advised by experts, the bug has been reported as below.

[https://bugs.launchpad.net/ubuntu/+source/vino/+bug/1290666](https://bugs.launchpad.net/ubuntu/+source/vino/+bug/1290666)
[https://bugzilla.gnome.org/show_bug.cgi?id=726137](https://bugzilla.gnome.org/show_bug.cgi?id=726137)

Thanks!

---

### Post by Herbon on 2014-05-08
I also have a similar issue of not being able to access a device after updating. :(

---

### Post by cariboo on 2014-05-08
@Herbon did you miss the large blue announcement at the top of the page? This sub-forum is for the discussion and problem solving of Utopic. Thread closed.

---

