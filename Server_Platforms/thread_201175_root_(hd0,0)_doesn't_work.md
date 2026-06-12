---
title: "root (hd0,0) doesn't work?"
date: 2006-06-21
forum: Server Platforms
---

### Post by ipguru99 on 2006-06-21
Hello all you SATA lovers (haters?)

I tried a dell sc1420 with the built-in raid controller (.. just saying it out loud now makes me want to spit).

Needless to say I turned all the 'raid' stuff off in the bios as so many people have said to do and just went with software raid.  When I boot my server up, it errors with 'file error 15... file not found'.  I know the data is there, I am assuming it is some type of grub problem (a problem with me not knowing how to do it ;-)

I decided to try to mess with it and started by hitting 'e' at the grub stanza.  I just looked at it and thought I would enter the commands by hand and see what failed.  So I hit 'c'.  I entered kernel /vmlin..... , it took it, then initrd /init....

IT WORKED?.. it booted up and everything... and you read correctly, I forgot to put it root (hd0,0) first.

so I added a stanza to grub when I finally got the server up and now it just works with a stanza that only has the 'kernel' line and the 'initrd' line..

So I am happy that I figured something out... wondering if it will help anyone else, but more importantly, is this SAFE?  I am a little confused and don't want to deploy it to the customer unless someone can explain what I did ;-)

Thanks... and thanks to everyone kicking the tires... It is so much easier explaining to all of the people that don't know anything about pc's, why linux is so great... all you have to do is show them Ubuntu!

---

### Post by pdk on 2006-07-13
Hi There. I have the same problem.
My Ubuntu is on the /dev/hdc2.
The install goes fine.
The reboot fails during stage 1.5.
Get rescue cd. Grub is setup perfectly.
The menu.lst is 100%.
Copy the whole thing to a floppy disk.
Boot from the floppy.
I have 2 Xp partitions hd0,0 and hd2,0
Whichever option I choose I get
file system type unknown partition type 0x7
error 15: file not found.
If I try from the command line.
root (hd2,1)
just hangs
I am using version 0.97 I think. I am going to try the latest version.
I tried it all using grub on my hd2,1 as root and grub responded perfectly to all commands.
Frustrated 
Peter K

---

