---
title: "Remote Desktop Access on Amazon EC2 Ubuntu"
date: 2009-09-27
forum: Server Platforms
---

### Post by roozbeh007 on 2009-09-27
Hello Guys.

I am fairly new to Linux so excuse the newbie questions I may ask.
I am trying to install a Linux application on ubuntu server from Amazon EC2 clouds. I would like to have remote desktop access to the server instead of terminal. how can I do that? I know there is a way to enable remote desktop in ubuntu, but i guess it needs to be done through SSH. can any one help me wit that? what are the commands? thanks for any help. god bless.

---

### Post by hessiess on 2009-09-28
Just learn to use the terminal.

---

### Post by amac777 on 2009-09-28
I'm not sure if this will work or not in your situation, but when you ssh to the server, add the -X option like this:

```
ssh -X your.amazon.server.com 
```

Then you can run graphical programs on the server and they will appear on your local desktop (albeit slowly if your internet is slow).

---

### Post by vpuranik on 2010-03-01
Here is  an easy way to enable remote desktop for your ec2 ubuntu instance - [http://aws-musings.com/4-easy-steps-to-enable-remote-desktop-on-your-ubuntu-ec2-instance/](http://aws-musings.com/4-easy-steps-to-enable-remote-desktop-on-your-ubuntu-ec2-instance/)

---

### Post by FunGuyDRW on 2012-12-13
> **hessiess said:**
> Just learn to use the terminal.

In addition to taking much longer than just doing what you already know, not every program runs from the command line. Examples include any java program compiled without defined headless behaviour, and spotify.

---

