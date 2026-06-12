---
title: "Find other computers?"
date: 2010-02-26
forum: Server Platforms
---

### Post by Booher6194 on 2010-02-26
I have ubuntu server 9.1 installed and was wondering if there was a command line tool to search for other computer (there names) on the network?

Thank you
Booher

---

### Post by joberly on 2010-02-26
sudo nmap -sP 192.168.1.0/24

It will only give you hostnames if they are configured via DNS, or your hosts file.

---

### Post by Jive Turkey on 2010-02-26
The command "arp" might be what you're looking for.

---

### Post by tgalati4 on 2010-02-26
Install rwhod on the other machines and run ruptime to query:

tgalati4@tpad-Gloria7 ~ $ ruptime
gc-developmedown    7+00:48
minty4      down      23:43
tubuntu2      up   18+07:33,     1 user,   load 1.08, 0.63, 0.51
washme        up   53+10:14,     0 users,  load 0.14, 0.11, 0.04


sudo apt-get install rwhod

For a pop-up balloon:

[http://ubuntuforums.org/showthread.php?t=328766&highlight=zenity](http://ubuntuforums.org/showthread.php?t=328766&highlight=zenity)

Although now you can use notify-send to do something similar.  That's an exercise left to the student.

---

