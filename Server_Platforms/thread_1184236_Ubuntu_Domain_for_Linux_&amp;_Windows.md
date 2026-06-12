---
title: "Ubuntu Domain for Linux &amp; Windows"
date: 2009-06-10
forum: Server Platforms
---

### Post by slensjk on 2009-06-10
Hello Everybody! 

This is my first post so I hope someone can help me!

I work for a very small company and I made a proposal to switch our environment to Ubuntu boxes, right now I need to implement a test environment with one server and two pc's and if a can make this work we will make the switch.

At this moment we have a Server 2003 Domain with some security policies implemented, what I need is to recreate the same but with Ubuntu.

My question is what do I need to accomplish this?? I basically need authentication, security policies, file and printer sharing, regular things that we do with a Windows Domain for both Ubuntu and Windows. 

I'm not asking for you to give me a step by step on how to do it (although if someone wants to provide me a How To I wont be mad!:D) but at least to orient me on which apps do I need, so I can start expirience on how to configure them.

Also I was wondering (this may sound a little stupid) it will be better to set up my server with the Ubuntu server edition or with a regular edition??

Thanks to all in advance!!!

Best regards.

---

### Post by TuckLive on 2009-06-11
You can use the desktop edition, but it's recommended to use the server edition. If you have to have a GUI then check out [_Webmin_]("http://www.webmin.com/").  Since this will be a production server also use a LTS edition, the latest being 8.04.  The following links below should give you some direction or reference to your other questions:

[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)
[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

---

### Post by slensjk on 2009-06-11
Thanks a lot TuckLive!! I really appreciate your help!

Regards.

---

### Post by koenn on 2009-06-11
> **slensjk said:**
> 
I work for a very small company and I made a proposal to switch our environment to Ubuntu boxes,  ...

At this moment we have a Server 2003 Domain with some security policies implemented, what I need is to recreate the same but with Ubuntu.

My question is what do I need to accomplish this?? I basically need authentication, security policies, file and printer sharing, regular things that we do with a Windows Domain for both Ubuntu and Windows. 


strange that someone would propose to switch from a Windows environment to a Linux environment without knowing what it entails or how to go about it.

Also, the way you describe your problem, i.e. how to use Ubuntu as a "replacement" for Win 2003 Server, is a recipe for disaster in all but the most simple environments.

Anyway, 
- file and printer sharing should be doable (samba, cups)
- authentication is easy, but you probably mean this to include authorization (access control), and possibly in a single-sign-on solution for multiple resources. Still doable, but you'll have to rethink a few things. For starters, it's not clear if you're thinking a Linux only environment, or a mixed Windows-Linux environment, and whether you're still going to maintain that "Windows Domain" you mention. 

-"regular things that we do with a Windows Domain" - would be irrelevant if you're going to be using Linux only, unless you have some specific features or functionality in mind. You going to have to be clear, not in the least to yourself, what you mean by these "regular things"

- same with "security policies on Win2k3 Server" : this is a very Windows-specific implementation of a very Windows-specifiec concept geared towards Windows environments. Sure, you can implement a security policy in a Linux environment, but you'll have to define and design that policy. "Same as what we have now on Windows Server 2003" won't do. 

---
Here's some reading material:
[http://users.telenet.be/mydotcom/howto/linuxsbs/samba4.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/samba4.htm)
[http://users.telenet.be/mydotcom/howto/linuxsbs/samba3.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/samba3.htm)
[http://users.telenet.be/mydotcom/howto/linuxsbs/samba2.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/samba2.htm)

[http://users.telenet.be/mydotcom/howto/linux/migration03.htm](http://users.telenet.be/mydotcom/howto/linux/migration03.htm)
[http://users.telenet.be/mydotcom/howto/linux/migration02.htm](http://users.telenet.be/mydotcom/howto/linux/migration02.htm)

---

### Post by slensjk on 2009-06-12
Thanks Koenn for your answer.

Maybe I didn't make my self very clear, when i'm talking about "regular things" I mean file transfer, authentication, printer sharing, security policies (denied access to certain resources, levels of privileges for certain users, etc), remote access, everithing under the same Domain, for both Windows and Linux.

However I think I have collected enough information to get me starting, I know that this probably won't be easy to achieve but at least I want to give it a try.

I want to thank both of you for take the time to answer my questions, I really appreciate it!

Regards,

slensjk

---

