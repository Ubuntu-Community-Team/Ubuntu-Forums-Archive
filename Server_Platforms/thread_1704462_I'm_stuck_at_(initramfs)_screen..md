---
title: "I'm stuck at (initramfs) screen."
date: 2011-03-10
forum: Server Platforms
---

### Post by Nate204 on 2011-03-10
Hello all,

I'm sure this has been posted here before do to the results I've found on google. The only thing is, none of them seem to be helping me. I thought I'd toss it up here in hopes someone can help me get my feet (and my server) back on the ground and running again.

Earlier today, my Server went into read only mode... This was a HUGE setback due to it being a gaming server. All our info stopped updating and saving around 10am...

I started to search around to see what could have gone wrong. I thought possibly one of my HDD was going out, so I came across a little "how-to". 

Here it is:
[My first link]("http://www.linuxquestions.org/questions/linux-general-1/getting-thrown-into-read-only-mode-not-able-to-remount-550832/")

Then, after looking it over.... I jumped to this link:
[Second link]("http://www.cyberciti.biz/faq/can-i-run-fsck-or-e2fsck-when-linux-file-system-is-mounted/")

I went to this step:
"# init 1
# umount /home
# umount /dev/sda"

and restarted...

Now, I'm very very stuck at the (initramfs) screen on boot-up.
I can't do anything. I can try and reboot, but It just brings me right back. If I type a /ls, It shows no /home directory.

I'm still very very new to Linux, and this is somewhat over my head. 

All I was trying to do was check my discs for errors. I have 4 in a RAID 0. I know...no redundancy. EEkkk.

Any suggestions? Is it a simple mount problem? Am I screwed? 

Thanks everyone. I Love how responsive this community is. I appreciate your time and your input =)

Btw... It might be hard to copy/paste errors from the server. I can't remote into it because of this. I have to go over and hand write down any messages it pushes back. I've tried to do Esc. and "exit" while at this screen~ and it gives me an error saying:

Can't open file root/dev/console File Not Found.
followed by something saying Kernel Panic! - Not syncing: Attempted to kill Init.

---

### Post by Nate204 on 2011-03-10
I just tried to boot from a Live CD.... It wont let me. I'll try and get the error.

---

### Post by Nate204 on 2011-03-10
I'm guessing this one must be a toughy~

I still can't get it to go. When trying to boot with the Live CD, it basically bring me back to the same screen as booting without it. It's starting to drive me mad. I feel like it's just a simple setting or edit I need to do to get it to get!

*Sigh*

If anyone reads this and needs more input, just let me know. I really want to get my old data off my RAID at least. I'd even go through the trouble of reinstalling~ I just don't want to lose that data...

---

### Post by Nate204 on 2011-03-11
bump for greatness?

*Note* I tried to launch from two different distros from Live CDs and both wouldn't work. The server simply refuses to start

---

### Post by kidsodateless on 2011-03-11
I had experienced this a couple of months ago.
I got an answer ragarding initramfs here   [http://ubuntuforums.org/archive/index.php/t-1244466.html](http://ubuntuforums.org/archive/index.php/t-1244466.html) 

but the problem is LiveCD doesn't work . you have to boot from LiveCD to be able to mount your file system.

---

### Post by Nate204 on 2011-03-11
I got Gparted to fire up on the server.... It took two tries~ but it finally went. I'm using the "discover file system" on my RAID 0 it found~ and it's taking forever.... It's been over two hours now, and it still acts like it's searching. The four drives together only add up to around 150gb of space. I can't complain to much though.. I'm much further now than I was two hours ago.

Thanks for the suggestion. I'm surprised that no one else had any input on this. I feel like I've almost destroyed my server, and it didn't take much to do it.

Also~ Does anyone know if I can set up a raid to mirror other drives? Such as... Drives one and two mirrored onto just one drive (drive 3)?

---

### Post by Nate204 on 2011-03-11
Well, I'm still going at it!

I booted with a live CD of Gparted last night. I tried the data recovery and after about...god knows how long~ it finished. Unfortunately, it came back with something like:
"...and Unable to read contents of this file system.
Tells me that ext4 needs e2fsprogs v 1.41+." 
Aka: Epic fail FML moment.

I'm kind of stuck now. I'm not positive on what to do. I feel SOO close, but just a tad bit off. Any suggestions?

I just feel like all I need to do, is remount my RAID so Ubuntu boots from it. I swear, it just seems like I doesn't detect it. I'm running a "e2fsck -f -c -v /dev/md126" atm to check for errors.

Thanks to ANYONE who helps. I appreciate it!

---

### Post by Nate204 on 2011-03-11
So... I fixed it?

I used Gparted and checked my RAID for errors. Nothing reported back and It said I didn't have any block problems. I then mounted the raid with the terminal provided~ and found two files called Initrd.img and Initrd.img.old.

I renamed Initrd.img to Initrd.img.bad (was a guess...) and then renamed initrd.img.old to initrd.img.

I then closed the terminal, and rebooted. It brought me back to the dreaded GRUB, and I selected to boot up my latest Ubuntu OS in Safe Mode (?). From there, it brought me to a screen telling me it found an error. I can't recalled exactly what it was, but It asked if I wanted to do a few things, and I chose to update my GRUB.

A click later, and presto! I'm back at my Ubuntu server login!

I guess the sun does shine on a monkeys butt sometimes!
I hope this helps someone at some point. Due to my lack of detail~ I have my doubts.

Thanks!

---

### Post by kidsodateless on 2011-03-11
Yeah!Well done. :D

---

