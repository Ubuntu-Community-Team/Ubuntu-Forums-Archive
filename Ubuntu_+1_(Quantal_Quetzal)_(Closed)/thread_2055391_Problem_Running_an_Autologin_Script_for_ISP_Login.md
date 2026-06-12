---
title: "Problem Running an Autologin Script for ISP Login"
date: 2012-09-09
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by fantab on 2012-09-09
I use an **Autologin Script to automatically login** to my ISP Account at System Start. 

In 12.04 I had this Script placed in /etc/network/if-up.d and used chmod to run it at system start. However, the said **script is not working in Quantal Quetzal **in spite of replicating the process over and over again.

I need some directions and pointers here to help me get the autologin script going at the system start. 

For reference see _[this thread]("http://ubuntuforums.org/showthread.php?t=2002693")_.

---

### Post by fantab on 2012-09-29
Bump...

---

### Post by steeldriver on 2012-09-29
what have you done so far to diagnose it? have you tried writing a line to a file from within your script to see if it gets that far? or checking the system logs (/var/log/syslog perhaps?)

---

### Post by fantab on 2012-09-29
> **steeldriver said:**
> what have you done so far to diagnose it? have you tried writing a line to a file from within your script to see if it gets that far? or checking the system logs (/var/log/syslog perhaps?)

Well there is nothing in logs, except that I have not found anything related to /if-up.d.

I have also tried to run the script from /NetworkManager/dispatcher.d/script... (because in ARCH it runs from here) .

However, in the logs there is reference to this-  /dispatcher.d/script not being executable. Which is not. Even if I chmod +x it does not work from here.

---

### Post by fantab on 2012-10-03
bump

---

