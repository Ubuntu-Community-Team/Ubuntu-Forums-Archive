---
title: "Problem with VirtualBox"
date: 2015-12-12
forum: Virtualisation
---

### Post by damien27 on 2015-12-12
hey guys, often been surfing here for info for problems ive been thrue with this wunderfull OS. Now i've been running ubuntu since 2004, and only had dual boot once, thats becurse Diablo 3 was released.. But thats not why im posting this. I got a problem nighter me or google seems to solve.

I was trying to compile my own mix of debian ubuntu and fedora, with no succes at all for aboute 15 times, so i gave up and took a beer saw my Ubuntu system going all windows all over.

[ATTACH=CONFIG]266107[/ATTACH]

Thats whos really strange is that i had 14gb swap, seems like VirtualBox has stolen half of my swap, and after that continued to eat my RAM.

and yes ive been trying umont them as sudo, it says:
umount: /dev/ram1: not mounted
And ive also been trying:
lsof | grep '/dev/ram1'
Who dident gave any output.

So i did a 50gb partition from my server, formated it to swap and emulated it as a harddrive then did a 
sudo swapoff -a waited to that one in my bedroom had it. But when her new swap was full it keept filling my ram once again. 
I dont really know what the hell the next step is from now. I really dont wanna reinstall ubuntu, i even feel bad when i have to reboot her.  
And please spare me the comments aboute the harddrive, i dont really need more on my workstation. 

Its a pice of junk computer to be honest, but it was the computer who made me love ubuntu :D
(and yes i know it aint a hardware failure, but i have to defend my love)

So please if anyone got any ideas how to fix this, be my guest.

Hello by the way, my first post. Im damien from sweden, and i cant spell in english very good ;)

---

### Post by QIII on 2015-12-12
Please do not cut and paste large images in your posts.  Use the attachment button in the toolbar above the text input box.  Some of our users have slow internet connections or data transfer quotas.

Also, please use language suitable for polite company.  This is a family friendly forum.

---

### Post by damien27 on 2015-12-12
Sorry. I shall think aboute my both my language and images in the future.

---

