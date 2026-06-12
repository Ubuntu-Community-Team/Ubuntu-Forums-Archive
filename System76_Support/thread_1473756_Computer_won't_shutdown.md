---
title: "Computer won't shutdown"
date: 2010-05-05
forum: System76 Support
---

### Post by shaggy_160 on 2010-05-05
When I shut it down the screen goes black, and the keyboard LEDs are turned off. Even the power button on the tower is not lit, but I can hear sound coming from the tower like it is still running. I have to pull the plug to turn it off. I have a system 76 meerkat nettop with Ubuntu 9.10. One day I hibernated my system and I think this is how the issue began. I am new to Linux so I have no idea what the problem is.

:guitar:

---

### Post by registering on 2010-05-06
Do you have any CIFS or NFS shares mounted when you power it off? Up until 9.10 I found Ubuntu would hang forever when I tried to turn it off with these shares mounted in the same manner you're describing (black screen, etc..).

---

### Post by shaggy_160 on 2010-05-21
Thanks for the reply. I'm sorry I haven't replied but I have two jobs and almost no free time! I am still learning how to navigate these forums. In response to your question, I don't think I have anything mounted. The computer's power button and the keyboard look as if the computer is off, but I hear a sound coming from the tower like it is still running. When I push the power button to turn it on, it won't do it. I have to unplug the power cord and to plug it back in before pushing the power button in order to turn it on.

---

### Post by thomasaaron on 2010-05-24
The next time that happens, let it run for a few minutes, then shut it down. Then turn it back on, open a terminal (Applications > Accessories > Terminal) and run this command

```
cat /var/log/syslog >> ~/Desktop/syslog.txt
```

This will create a file on your desktop that you can attach to this thread. Also, make note of the time on your system clock when the computer comes back up.

---

