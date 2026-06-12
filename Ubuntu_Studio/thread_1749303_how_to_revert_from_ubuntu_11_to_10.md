---
title: "how to revert from ubuntu 11 to 10"
date: 2011-05-04
forum: Ubuntu Studio
---

### Post by adamson28 on 2011-05-04
I installed ubuntu 11 from an update not knowning what it is and I do not like it.

Can anyone tell me how to revert back to ubuntu 10 without doing a full install.

Thank you.

---

### Post by Pablo_F on 2011-05-04
What do you dislike about ubuntu natty? If it is the desktop interface (Unity), you can just choose "ubuntu classic" in the login screen.  

Cheers, Pablo

---

### Post by adamson28 on 2011-05-05
Your right that is what I discovered last night thanks for you information.

What do you think of the new interface?

I found it slow and confusing disorganized.

---

### Post by adamson28 on 2011-05-05
How do I access a folder containing .sql file. 
When I try to I get this message  'The folder contents could not be displayed. You do not have the permissions necessary to view the contents of "this file".'

---

### Post by Pablo_F on 2011-05-05
Hi, 

As for Unity, I can't give an opinion because I don't us it. However, if you are interested you can search the internet. There are guides and tips on how to use it.

As for the other question, it would have been better if you opened a new thread because it is completely off-topic. To find the owners (user and group) and permissions of a file, you can use in a terminal:

ls -l /path/to/the/file

If your user has not read access to the file, then you need to gain administration privileges to read it. With nautilus file browser you have to launch "sudo nautilus" from a command line. 

Cheers, Pablo

---

### Post by dazormiq on 2011-05-06
I would still like to know how to revert.  For some reason after I log in, no matter what desktop option I choose, the desktop is blank and it essentially locks up.  When I do a ctrl+alt+f4 all I get is a render error and I have to reboot with the computer power button.

---

### Post by Pablo_F on 2011-05-07
Hi, 

Do you get a clean command line interface with [Ctrl-Alt-F1]?

If so, we will try to help you out but be patient. Otherwise, I suggest you use the 10.10 install CD in "try ubuntu" mode, save your files and do a fresh install. 

Cheers, Pablo

---

