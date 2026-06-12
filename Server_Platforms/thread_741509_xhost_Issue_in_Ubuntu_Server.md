---
title: "xhost Issue in Ubuntu Server"
date: 2008-03-31
forum: Server Platforms
---

### Post by egonzalez on 2008-03-31
Hi All,

At this time, I've got a clean installation of Ubuntu Server (LAMP) with root access, now, because I need to connect to this server via a remote machine but not using SSH I need to specify the XHOST command, so, I install XHOST by typing:

[COLOR=Olive][B]apt-get install x11-common-utils

[/B][COLOR=Black]Once XHOST is installed, I try to add the remote IP Address of the machine I want to connect from but I've got the following error:

[COLOR=Olive][B]xhost: can not open display

[/B][COLOR=Black]What can I do in order to add the IP address of the remote host by using XHOST? Even more, I've tried the same command (xhost +) to permit all connections but I've got the same error message.

Does anyone know what can I do?


Thanks in advance.
[/COLOR][/COLOR][/COLOR][/COLOR]

---

### Post by Dr Small on 2008-03-31
What is DISPLAY set to?
```
echo $DISPLAY
```

---

### Post by egonzalez on 2008-04-01
Hello Dr. Small,

Thanks a lot for your prompt reply.
As you suggested, I used the command you gave me but I get no output, I mean, although no error is issued a blank output is shown in the console output.

Anything else you can suggest???

Thanks a lot for your help.

---

### Post by Dr Small on 2008-04-01
I am trying to re-read your first post... What do you need xhost for, or what exactly are you trying to do? Generally I would set the DISLPAY to a number, but I don't know how you are wanting to do this.

The default display is :0, so if you wanted to make something appear on another person's display, you would use:
```
set DISPLAY=:0
```

---

### Post by egonzalez on 2008-04-01
Hello Dr. Small,

OK, I understand you want to know why I want to get this working.

In the following link, there is a post (writtem by myself too) trying to explain what I want to do.

[http://ubuntuforums.org/showthread.php?t=741387](http://ubuntuforums.org/showthread.php?t=741387)

Please, read it and let me know what do you think or what can I do.

Once again, thanks a lot for your help.

---

### Post by Dr Small on 2008-04-01
Ok... So all of this is still rather confusing, but can you install a ssh client on the Solaris?

---

### Post by egonzalez on 2008-04-01
No, I can not install a SSH on the solaris machine :-(

---

### Post by Dr Small on 2008-04-01
OpenSSH Portable works on Solaris, so it says:
[http://www.openssh.com/portable.html](http://www.openssh.com/portable.html)

---

### Post by egonzalez on 2008-04-01
The thing here is that I can not install SSH on Solaris because company's requirements and restrictions included with the server's software, that's why I can only use the command:

xterm -display....... blah blah blah

---

