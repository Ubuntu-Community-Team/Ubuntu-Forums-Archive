---
title: "Sharing Printer from Linux Virtual Server?"
date: 2012-11-04
forum: Virtualisation
---

### Post by xolo80 on 2012-11-04
Hello,
  I'm currently stuck right now trying to share my printer to Windows 7 machines. It is connected (HP 1510) via USB to a Windows 7 machine running Ubuntu Server on VirtualBox. 

I've configured CUPS already, (I followed tutorials since I'm still really new to Linux). I try to log onto the web server of cups using port 631. But, all I see is sharing from a website, or a ip address. Any help is appreciated, thank you very much in advance

---

### Post by gordintoronto on 2012-11-04
This might get you somewhere:
[http://askubuntu.com/questions/140081/virtualbox-doesnt-recognize-usb](http://askubuntu.com/questions/140081/virtualbox-doesnt-recognize-usb) 

Sometimes it is relevant to say what version of Ubuntu you are using. For a server, the 12.04 LTS release is probably the best bet.

That said, I am not a fan of Ubuntu Server. My preference is to install Desktop Ubuntu, then add whatever server packages I need. That way, all the "normal" tools are available to you. If you're running a high-volume web site, Server makes sense.

---

### Post by xolo80 on 2012-11-05
Thank you for the help, I was unaware you could run desktop Ubuntu that way. I just decided to virtualize, and make a home server for educational purposes. I figured the best way to learn to do something is to set up it for myself, and Ubuntu Server seemed to be a popular choice. Thank you again for your help

---

