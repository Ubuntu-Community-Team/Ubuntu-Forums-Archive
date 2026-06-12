---
title: "Dont want command help for &quot;one&quot;"
date: 2009-09-16
forum: Server Platforms
---

### Post by santhosh003 on 2009-09-16
Hi
 I am using Ubuntu 9.04 Server.
 I have installed opennebula manually in user defined path.
  When I type the command *one start* I am getting the message as
  
The program 'one' is currently not installed.  You can install it by typing:
sudo apt-get install opennebula
bash: one: command not found

But when I do the same this in Ubuntu 8.10 it's working fine.

 What would be the problem?
 
  what should I do to locate the one command to my user defined path and get rid of this message when I type one start

Thank you very much

---

### Post by lvlint67 on 2009-09-16
I would personally just add the directory you installed it to, to the end of the path varible.

see: [http://ubuntuforums.org/showthread.php?t=317070](http://ubuntuforums.org/showthread.php?t=317070)
for details

---

### Post by santhosh003 on 2009-09-16
Thank u somuch

---

### Post by lvlint67 on 2009-09-16
I take it that worked?

---

