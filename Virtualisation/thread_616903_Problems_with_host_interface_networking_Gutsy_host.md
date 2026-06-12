---
title: "Problems with host interface networking: Gutsy host/ WinXP guest"
date: 2007-11-18
forum: Virtualisation
---

### Post by painterh on 2007-11-18
Hello.  I have using Ubuntu Gutsy for a couple of months and I have just installed Virtualbox and installed WinXP as guest. I have gone over the user manual and tried to follow the step by step instructions to set up networking for my vm so I can reach my printer and my windows home network (where my printer resides). I have a dual boot system with Ubuntu and Winxp on 2 separate harddrives, but I want to move away from Windows and not have to use it for my bookeeping program hence the need for Virtualbox. I have network access from my virtual machine using NAT, but it appears my attempts to configure a network bridge have been unsuccessful. I'm afraid I have jumped into the deep end of the pool on this one, so if there is anyone who would be kind enough to walk an old fart through it, I would be very grateful. I hope I haven't already screwed something up. Sorry but some of the details in the user manual instructions are confusing to me.  Thanks in advance.

---

### Post by sokraski on 2007-11-21
I'm bumping this.

I am trying to do the same thing so that some programs for work will work on XP guest.  I followed the directions in the virtualbox manual as well as trying some steps on this forum, but with no luck.

---

### Post by jonandrews on 2007-11-22
I've put my simple guide to integrating Ubuntu PC's into a wired Windows home network onto a website:

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

It  may not be fully relevant to your configuration, but it could contain some pointers..

Let me know if it is helpful.

---

### Post by painterh on 2007-11-22
Thanks for the reply and an undoubtedly good guide to networking an Ubuntu PC with a windows home network.  However the problem as I mentioned in my original post is configuring network settings for a "virtual xp machine" running on a Ubuntu host machine to be able to access the windows home network.  I'm having trouble configuring the proper settings for the virtual machine to use "host networking" in order to run my windows bookkeeping software from within Ubuntu without having to reboot back into windows  (dual boot setup) and access my files which are on another window machine in my office.  I really appreciate any help I get from the great people on this forum and for your kind attempt to help.

---

### Post by pressurepoint on 2007-11-27
[These]("http://ubuntuforums.org/archive/index.php/t-523276.html") directions helped me set up host interface networking on both feisty and gutsy.

I found these [URL="https://help.ubuntu.com/community/VirtualBox"[/URL] as well but the former one seemed easier and it worked.

Good luck!!

---

