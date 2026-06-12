---
title: "Sudoers should be 0440"
date: 2010-08-13
forum: Security
---

### Post by phour10n3 on 2010-08-13
I have looked at a post that is about the same thing, but I have more specific questions about it.

Basically I am using a work laptop with my username A. There are already users on the computer, B, which I know the password for and who have sudo, but I did not. While trying to install mysql I thought it would just be simpler to give A sudo so that i didnt have to su to B. Anyway turns out that sudo had read-only permissions, which I wasnt used to when manipulating it on my computer. So I chmod'ed it to 777, added my name in there, and then closed. 

And thus I have messed it up. It seems to me that while sudoers is 777 no one can sudo, because it is supposed to be 0440....but because of that I cannot chmod sudoers to the proper permissions. So.......yeah.

On the other forum it was suggested that a system re-install or a fix with a boot disk would be necessary. Is this so, and if it is could someone point me in how to chmod sudoers from a boot cd and what to use (I am not going to re-install the operating system, Ill let IT mess with that one if its necessary)

---

### Post by cariboo on 2010-08-14
You can fix your problem by using the Live CD, you should just be able to mount / then adjust the permissions to 100440.

---

### Post by Ryan Dwyer on 2010-08-14
In the future, you can give a user sudo rights by adding them to the admin group. And if you absolutely must edit /etc/sudoers, always run "sudo visudo" instead of editing it directly.

And of course, don't change the permissions on /etc/sudoers.

---

### Post by phour10n3 on 2010-08-14
I know, I know. Ive read so many times to use visudo, but since its like vim I just hate it....completely my own fault. But I just havent encountered permission problems while editing sudoers before, I don't know whats up with that. Seems like something is wrong if you don't have access to it while using sudo. But perhaps another user set it to that.

Will try live cd soon and report.

---

### Post by phour10n3 on 2010-08-14
Solution:
Used live usb boot, then go to places and click on the hard drive (without doing this it doesnt show up in terminal). In terminal to under /media/xxxx where xxxx is an arbitrary number corresponding to your hard drive (I think). From there can edit the sudoers file to its proper status using
sudo chmod 440 sudoers
in /etc.

The end.

---

### Post by cariboo on 2010-08-14
> **phour10n3 said:**
> I know, I know. Ive read so many times to use visudo, but since its like vim I just hate it....completely my own fault. But I just havent encountered permission problems while editing sudoers before, I don't know whats up with that. Seems like something is wrong if you don't have access to it while using sudo. But perhaps another user set it to that.

Will try live cd soon and report.

On my system Maverick 10.10 alpha3, the first time you run visudo, it gives you a choice of which editor you want to use, I personally am not a big fan of vim, so I choose nano. I've seen the same thing in previous versions.

---

