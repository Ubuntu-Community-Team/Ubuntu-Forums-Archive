---
title: "Permissions"
date: 2010-08-15
forum: Server Platforms
---

### Post by Orange Worker on 2010-08-15
Hello,

I'm trying to edit the "permissions" of multiple folders, but it only seems to work one folder at a time. I've attached a JPEG of what I'm trying to accomplish. Any help is greatly appreciated.

Thanks.

---

### Post by stlsaint on 2010-08-16
use cmd line. Use the chmod command and look into the -R switch for recursive :popcorn:

---

### Post by Orange Worker on 2010-08-16
Hi,

Thanks for your reply. When you say use the cmd line, do you mean through the "terminal" ?

Any possible way to do this through the GUI ? I'm a little worried about writing a 
command as I had someone set my server up and I don't want to take a risk of
ruining anything.

Linux is still really new to me...thanks for your patience.

H

---

### Post by arrrghhh on 2010-08-16
Well on the server edition of Ubuntu, there is no GUI.  So yes, through the terminal would be the preferred method.  It's quicker, and with some trickery you can usually get what you want done in just a line or two of code as opposed to clicking 1,000 times.

Just curious, what is that screenshot taken from, assuming you are running the server edition of Ubuntu?

---

### Post by Orange Worker on 2010-08-17
Thanks for your reply. The developer I had work on my server used:

Ubuntu Linux 10.04 (Server)
Webmin 1.510 (GUI)

I'm not even sure how to access the terminal with the GUI set up. Could you list the steps for me, and the code that I need to change the permissions? I'll pay you for it.

I need to change the permissions often cause my app really wasn't built 
to work efficiently. If I can change this in one shot, then that would be a big help.

Thanks.
H

---

### Post by TheStroj on 2010-08-17
Yes, cmd line is Terminal.

When you open it use 'ls' (without quotes ofcourse) to see whats in the folder where you currently are. Use 'cd' to navigate to folders. Example:

```
cd Music
```

when you're in the folder containing the folder that contains folders that you want to set permissions for (simple: when you're in sub directory of that folder on your picture) use command 'chmod' to change permissions:

```
chmod -R 777 name_of_folder_on_picture
```

ofcourse, you can change permissions with changing that number (777 in this case). -R will change permissions for everything in that folder.

---

### Post by Orange Worker on 2010-08-17
I got it to work. Thank you for all your help!

H

---

### Post by arrrghhh on 2010-08-17
> **Orange Worker said:**
> I got it to work. Thank you for all your help!

Sounds good.  No need to pay anybody, we're a community - we help eachother because at some point each of us came here for help.  Now I offer more help than I ask for, but I just see it as repayment for the help I received previously :D

Could you use the "Thread Tools" drop-down menu to mark this thread [SOLVED] that would be great!  Thanks!

---

### Post by Orange Worker on 2010-08-17
Thanks again to everybody! 

I'm not sure where to find "solved" in the drop down menu, so I manually
typed it in "Title".

---

