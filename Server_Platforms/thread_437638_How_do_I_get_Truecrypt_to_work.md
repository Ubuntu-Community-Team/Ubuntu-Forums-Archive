---
title: "How do I get Truecrypt to work?"
date: 2007-05-09
forum: Server Platforms
---

### Post by NET WT on 2007-05-09
Hi, I just installed Truecrypt 4.3a on my Ubuntu 7.04  machine. I followed instructions which I found on this post: 

[http://ubuntuforums.org/showthread.php?t=369293&highlight=How+to+install+truecrypt](http://ubuntuforums.org/showthread.php?t=369293&highlight=How+to+install+truecrypt)

I am now trying to learn how to use it through the terminal. When I try to use it  I get this message: 
"Running with effective user id 0 (set-euid root) is not supported."

I am not sure what this message means. Was I not supposed to type these commands? 

> sudo chmod u+s /usr/bin/truecrypt

---

### Post by NET WT on 2007-05-09
After I installed truecrypt  I typed 

> sudo chmod u+s /usr/bin/truecrypt

Into the terminal, pressed enter. I think that since I installed version 4.3a, and not version 4.2a I think I didn't need to type those commands. How do I undo what I did?

---

### Post by Trevster on 2007-05-10
I did the same thing. I believe what I finally did was > chmod 777 /usr/bin/truecrypt It alows anyone to do what ever they want to the file. Not sure if this is the most elegant way to fix the problem.

After that problem was fixed I had trouble with permissions to access the mounted volumes. I was mounting NTFS truecrypt volumes from my windows drive to /mnt/. I found this page helpfull. See the mounting options.

[http://hype-free.blogspot.com/2007/04/installing-and-using-truecrypt-on.html]("http://hype-free.blogspot.com/2007/04/installing-and-using-truecrypt-on.html")

Good luck I wish I could be more specific.

---

### Post by resonantworks on 2007-05-14
NET WT,

To undo that just type:
**sudo chmod u-s /usr/bin/truecrypt**

The negative-sign removes the 'S' bit.

---

### Post by NET WT on 2007-05-15
resonantworks,

I have already done what Trevster suggested that I do. 
Should I do what you suggest and type: 

> sudo chmod u-s /usr/bin/truecrypt

Or is there anything else that I should type, before I type that command?
To undo what I have already done.

---

