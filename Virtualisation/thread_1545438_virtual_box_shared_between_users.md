---
title: "virtual box shared between users?"
date: 2010-08-03
forum: Virtualisation
---

### Post by singletrackmind on 2010-08-03
OK guys, I'm trying to win my wife over on the linux idea and need to get a win7  box running for her as a crutch to ween her off the ugly windoz world.  Don't get me wrong I'm a newbie and just now getting the hang of things.  

I have spent hours and hours (ok days) messing with KVM and decided to try virtual box. I was able to get it working. I just build a 10.04 box and put /home on it's own drive. I setup a /home/public/vbox dir for the virtual box files & disks to live in. After building the Win7 box (for my wife) I logged in as her and realized I didn't know how to open the virtual box from her account. I changed the group to vboxusers recursively and set the permissions to 777 out of desperation. Her account is a member of the vboxusers group. I was able to add the virtual drive I created. But still don't know how to load the virtual machine I created under my account. Any suggestions would be greatly appreciate. I did skim through the manual and didn't see anything specific to the topic.

---

### Post by singletrackmind on 2010-08-03
Am I just being stupid? Do I just have to export the vm in my account and import it in hers?

---

### Post by marseille on 2010-08-04
i've been thinking the same thing today, while trying to tweak the kids' new Lucid -- btw, i don't know if there's an easier way to do this (if there is, i hope someone chimes in) -- but on the kids' account, i couldn't ``import'' anything. instead, i had to access the virtual machines i set up from my own account by doing this in *VirtualBox Puel v. 3.2.6*:

[INDENT]*fyi -- this did not work with a live cd i made a ``snapshot'' of (that is still accessible in my account). it only worked with an OS that i installed... dunno why but that's what happened.*[/INDENT]

**S T E P . 1**

> File >> Virtual Media Manager >> Hard Disks >> Add >> 

then i chose the [SIZE="4"]**.vdi**[/SIZE] file i'd made from my own account earlier >> then hit ``OK''


**S T E P . 2**

then i created a not really ``New'' virtual machine like this:

> New (blue button) >> Next >> 
Name | OS | Version (your virtual machine) | Next >> Memory ... | Next >>
Boot Hard Disk (Check) | Use existing hard disk (check radio box) |  pick .vdi file previously made >>
Finish

**S T E P . 3**

> hit ``Start'' (green arrow)


- - -

that loaded up the vdi files i had already made and booted straight into the machines i had previously installed (the live cd snapshot gave me a boot error or something). the one thing that irritates me is that i didn't see a software app i had installed on one of the virtual machines. whether that was because it only had ``windows admin'' privileges, i don't know (but it wouldn't surprise me). i have to try another old app to see where that story goes; or perhaps a virtualbox expert could share some tips:D



ps: in the beginning i thought it was a permissions issue too... the kids' account had ``plugdev'' access so i couldnt figure out why i didn't see the vdi files i made when i went to ``import''. so i changed the permissions on the vdi file (which is probably unnecessary -- i'll have to check) before i found out all i had to do was go into the *virtual media manager* and repeat the process, minus the OS installation drama.

---

### Post by singletrackmind on 2010-08-04
Hmm, interesting. I'm new to the virtual box thing so I'm still learning my way around and the terminology. I don't really understand why I can't just create a virtual computer and then open it under a different account but whatever it take I guess. I should have just made the stupid thing under her account. :-/

Thanks for the reply. I will give your method a try. I have a brand new virtual Win7 box I haven't made any snapshots of or anything, it just has office installed and all the patches. I went to "export the appliance" and it said it was going to take 20 hours so I let it be and went to bed. I will work on it some more later.

---

### Post by marseille on 2010-08-04
ok then... i hope all goes well. fyi, it took me just a few minutes to go through the initial steps to access the vdi files (and that was going slow and reading the directions line by line as if life depended on it). after that was all done it took no more than a few seconds to (repeatedly -- like normal) start up an installed virtual machine.

---

### Post by singletrackmind on 2010-08-05
It was easier than I was making it out to be. All you have to do is add the disk once you have granted permission to it and the create a new machine using the disk image with the OS on it. 
After reading about how to move a machine to a different host it was easy. :)

---

