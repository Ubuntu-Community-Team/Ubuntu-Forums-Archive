---
title: "File(s) not visible from BOTH terminal and GUI"
date: 2018-12-14
forum: Server Platforms
---

### Post by mwoosley on 2018-12-14
Hello everyone.  I have discovered another glitch in my setup... I have both an instance of Ubuntu Server (terminal) and recently installed the GUI desktop on the same machine.  The desktop version is Mates.  My problem is I am trying to install Packet Tracer for use in the GUI, but when I go to the terminal after downloading the file into the GUI downloads directory, the file cannot be seen via the terminal interface.  Certainly these directories are common between the 2 interfaces.  I am using the terminal from the GUI as well.  I tried ls -a and that just returns my base directories (no files there yet).  From Mates, I can see the file sitting in the downloads directory.  

I'm at a total loss as to why I can see the file in the GUI but not in the terminal.  I'm sure something isn't linking up right or I might be misunderstanding how this stuff works (very possible).

Thank you to anyone who might be able shed light on this topic.

Best,
Mike

---

### Post by mwoosley on 2018-12-14
Wow, I figured out my mistake.  I created a directory in my Ubuntu terminal a few weeks ago named 'downloads'.  A couple weeks ago, when i installed the GUI, it created another downloads directory named 'Downloads'.  Well, because of this, I was looking in the incorrect directory of my terminal when I should have been looking at the 'OTHER' downloads directory created by the GUI.  

Just goes to show you that Linux is very case-sensitive and we should be careful when trying to figure out where our files are sitting.

Mike

---

