---
title: "Connect client to server"
date: 2009-02-20
forum: Server Platforms
---

### Post by Olodu on 2009-02-20
Hello Guys,

I am having some problems which I'm sure you guys will be able to help me with. I've installed Ubuntu Server 8.10 and is all working fine. I have also installed Putty on my Windows XP machine which I can use to access the Ubuntu Server. All these
are working fine. I have now installed Ubuntu Desktop on another machine but I am having problems connecting to the server. What am I doing wrong. From the Ubuntu client machine,

I select "Places" and then "Connect To Server".  Ithen enter the name of my Server "LampServer" I then get an error message."Cannot display location "sftp://lampserver/"
I am completely new to Linuxand I am sure the problem is from me. Can someone please help.

---

### Post by cariboo on 2009-02-20
If you also intend on serving files from your server, you will need to install and configure Samba.

Have a look at this [Howto]("http://ubuntuforums.org/showthread.php?t=202605").

Jim

Edit: I guess I didn't read all the through your question, to access the sever using sftp and the server name you have to make an entry in your desktop's /etc/hosts file. You will need an entry something like this:

```
192.168.1.200     Lampserver
```

Substitute you servers ip address.

---

