---
title: "How do I delay a wine program startup?"
date: 2010-11-15
forum: Wine
---

### Post by wah fun on 2010-11-15
I am running ubuntu 10.04.1 LTS with wine installed. The system is fully updated. Here is my problem: I have my network manager setup for all users so it auto loads without having to put in the password each time it boots. I have a windows program (that accesses the net) in wine that I want to autostart when ubuntu boots. I set this up in the session manager. Now, everything works except that the wine program loads finishes loading before network manager (a wireless connect so it takes a few seconds) connects. Is there a way that I can delay the wine program load? I am relatively new to linux so give me as much direction as you can. I have searched and have found nothing I can (or know how to) use.

thx

---

### Post by s3MA00RRNY on 2010-11-15
Try this in your startup line:

sleep <number of seconds to wait> ; yourcommand

I'm not sure if it will work. Worth a shot though.

---

### Post by endotherm on 2010-11-15
that will work, but you can;t put compound statements in the startup applications applet, so create a script file and mark it as executable. put somthing like this in the file

```
#!/bin/bash
sleep 30
<your command>

```

then from startup applications, link to the script. I've used this trick with several apps. works well.

---

### Post by ajgreeny on 2010-11-15
You *can* put compound commands in the startup-applications list, but have to do it slightly differently.

I use two of them, one for conky, another for gmail-notify, which otherwise start too soon as well.
```
bash -c "sleep 20; conky"
```The **bash -c** part just tells the system that the command must be run as a bash command rather than as a launcher.  Try it; there's no harm done.  If it does not work for a wine app simply remove it.

---

### Post by wah fun on 2010-11-16
Thank you ajgreeny! That worked perfectly. Little by little I am learning linux and I will certainly tuck this information away in my memory bank. Perhaps I can help someone else.

Have a terrific day.

---

