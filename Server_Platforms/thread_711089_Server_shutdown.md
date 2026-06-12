---
title: "Server shutdown"
date: 2008-02-29
forum: Server Platforms
---

### Post by ripit on 2008-02-29
Hi everyone,

my problem is that sometimes I can't shutdown or restart my server remotly with ssh. I have to go to the server (about 3meters) and push the button. This isn't such a big problem with this server but if happens to one of my others that are placed far away from me it would be.
When i type "sudo shutdown -h now" or "-r" it says system is going down but nothing happens, I can continue working as normal.
Anyone have any ideas what this could be or where to start looking for errors?

---

### Post by banewman on 2008-02-29
As a start the shutdown prog should be in the /sbin dir so check that it is there.
And check that the terminal uses /sbin as a directory for progs with
echo $PATH

---

### Post by davidshere on 2008-02-29
have you tried 
```
sudo reboot
```?

---

### Post by ripit on 2008-02-29
sbin is in the path and  I haven't tried reebot.
The thing is that it only happens sometimes so i can't try anything else before it happens again.
Does anyone know wich log files to look in to maybe find something useful?

Thanks for the answers.

---

### Post by banewman on 2008-02-29
Try in /var/syslog.

---

### Post by Brazen on 2008-02-29
Is there a monitor plugged into that computer?  If you could plug a monitor into it at least temporarily, you might find some usefull information on the console.

---

### Post by tubezninja on 2008-03-01
Sorry, misread the question.

---

