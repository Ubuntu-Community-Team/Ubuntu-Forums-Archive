---
title: "Well lets try this again"
date: 2011-06-03
forum: Virtualisation
---

### Post by ClientAlive on 2011-06-03
I posted on this topic before; but, at that time, had absolutely no clue as to what I was asking about and so didn't really get my issue resolved. I still kinda don't but I've picked up a couple new pieces of terminology and I'm hoping it may make a difference.

The basic question is this:

How can I take my current o/s and make a virtual machine out of it (migrate?)? I use Virtual Box and I don't have a Windows installation (nor do I really want one).

Can anyone please please help me?

:confused:

---

### Post by Bucky Ball on 2011-06-03
Not quite with you. You have one OS installed only? A virtual machine generally runs inside the installed OS of choice. Are you wanting to set up another OS as a virtual machine running in 10.04 LTS?

---

### Post by ClientAlive on 2011-06-03
> **Bucky Ball said:**
> Not quite with you. You have one OS installed only? A virtual machine generally runs inside the installed OS of choice. Are you wanting to set up another OS as a virtual machine running in 10.04 LTS?


Yes. I use Ubuntu 10.04 LTS as my os and I also have Virtual Box installed on it. I need to find a way to make an exact copy of my operating system and get it into Virtual Box as a virtual machine. In the end I would have two identical operating systems. One would by my current/ actual/ host operating system and the other would be a virtual machine of it.

I've seen there is a tremendous amount of information out there about virtualization and have even seen some about "migrating your operating system into a virtual environment." The problem is ether that Windows is the only supported o/s for software that does it for you or that the information requires a much stronger foundation than I have to even begin to understand it. I thought that if someone could give me a general, laymans type idea of what it is I need to be trying to do - then I could actually make some sense out of the information that is out there. As it is I find myself swimming in an ocean of virtualization information with no real direction at all.

:)
-------------

Edit: Only because this is the problem I had communicating in my other threads before this - I'll clarify. I don't want to make a fresh install of Ubuntu 10.04 into Virtual Box. I know how to do that. I want to put this, actual Ubuntu 10.04 intallation into it as an identical copy.

---

### Post by ClientAlive on 2011-06-03
By the way - I can imagine a couple different ways of doing something like that (3 actually) but it doesn't do me any good when it comes to making it happen because I just don't know how.

---

### Post by tgm4883 on 2011-06-03
> **ClientAlive said:**
> By the way - I can imagine a couple different ways of doing something like that (3 actually) but it doesn't do me any good when it comes to making it happen because I just don't know how.

You are looking for "VBoxManage convertfromraw" ( [http://www.virtualbox.org/manual/ch08.html#idp14129072](http://www.virtualbox.org/manual/ch08.html#idp14129072) )

You should be able to follow just step 4 of [http://www.virtualbox.org/wiki/Migrate_Windows#StepByStepInstructionsForWindowsXP](http://www.virtualbox.org/wiki/Migrate_Windows#StepByStepInstructionsForWindowsXP) and get the image made. Note you cannot have the partition that you are converting booted at that time. (ie. You will need to either slave the drive in another machine, or possibly boot from a live disk and save the file to a drive other than the one you are backing up)

---

### Post by SoFl W on 2011-06-03
Thank you for posting that tgm4884, I have seen it before but I forgot about it.  Seems like a lot of work but I wanted to save my old W2K install/data.

Back to the original post...
If I understand ClientAlive he wants to take the Ubuntu machine he is currently using, and make an image of it.  Then take that image and run it as a virtual machine.  A copy of the current install, running inside the current install.  (That is how I understood it)

---

### Post by Derxst on 2011-06-03
You can create an iso of your current system using Remastersys. Then you can boot to the iso and recover your system to the virtual machine.

[http://geekconnection.org/remastersys/]("http://geekconnection.org/remastersys/")

---

### Post by ClientAlive on 2011-06-03
> **tgm4883 said:**
> You are looking for "VBoxManage convertfromraw" ( [http://www.virtualbox.org/manual/ch08.html#idp14129072](http://www.virtualbox.org/manual/ch08.html#idp14129072) )

You should be able to follow just step 4 of [http://www.virtualbox.org/wiki/Migrate_Windows#StepByStepInstructionsForWindowsXP](http://www.virtualbox.org/wiki/Migrate_Windows#StepByStepInstructionsForWindowsXP) and get the image made. Note you cannot have the partition that you are converting booted at that time. (ie. You will need to either slave the drive in another machine, or possibly boot from a live disk and save the file to a drive other than the one you are backing up)


Cool! So it looks like vbox manage is something already a part of vbox (because that's what does the import and export of appliances when you go to: file > Import or file > export  in the vbox file menu)?

But what is this raw image they are talking about? Is that just an iso image? Maybe I could use clonezilla or something like it to make one of those?

Regarding what they talk about at the second link - so I can do that with Linux too? Just use the right file names in that script/ code?

==>  I am now reminded of a problem I cam up against when asking trying to figure this out before . . .

I have only a 40 gig hard drive and my current installation of Ubuntu uses the whole thing (although not all of the space is actually used). With the method discussed at those links - would I need to have the same amount of hard drive space for the vm as I'm using for my current installation? If so, that would be like saying I need my hard drive to be twice as big as it is and I don't have a magic wand I can wave over this laptop that will do that.

Is there a way of accomplishing my goal so that the vm is whatever size I say it should be? (Like smaller than the available space left on my drive). Or does this method work that way anyhow and I don't have to worry about it?

Thanks

---

### Post by ClientAlive on 2011-06-03
> **SoFl W said:**
> Thank you for posting that tgm4884, I have seen it before but I forgot about it.  Seems like a lot of work but I wanted to save my old W2K install/data.

Back to the original post...
If I understand ClientAlive he wants to take the Ubuntu machine he is currently using, and make an image of it.  Then take that image and run it as a virtual machine.  A copy of the current install, running inside the current install.  (That is how I understood it)


Yes, exactly. And the reason is so I can do whatever I want to that one without worrying about breaking my real system. If I need to fix a problem that arises I can trial run it in the vm and the results will be pretty darn close to what would actually happen on the host os (cause they are identical except for one being a vm). If I just want to try some freaky new thing, I can do that in the vm one - no worries. I can even make a snap shot of the thing before I go messing around with it so I have it to go back to over and over till I get what I'm trying to do right.

> **Derxst said:**
> You can create an iso of your current system using Remastersys. Then you can boot to the iso and recover your system to the virtual machine.

[http://geekconnection.org/remastersys/]("http://geekconnection.org/remastersys/")


Gotcha on that one. Thanks. I've only ever used clonezilla before (cause I'm such a newb to it all) but I'm sure I can figure that one out too.

---

### Post by JKyleOKC on 2011-06-04
What you're after is a good idea, but there are a few points that may cause you trouble down the road. They may not, either, so they are not deal-killers -- but you need to be aware of them:

The "hardware" environment in which a VM runs is not at all like the actual physical hardware environment surrounding your real o/s. It's a different CPU, different amount of RAM, different disks (both HD and CD/DVD), different keyboard and mouse, and different network adapters. This means that the kernel modules installed into the VM by the conversion process may be different from those in your actual system, so the two cannot be totally identical.

If a problem or experiment does not involve the kernel modules, the differences ought not have any effect on your results. However, if it DOES (and such things as installing proprietary video drivers will impact the modules) then all bets are off. It may or may not have any effect, and I don't know any way to tell which is which.

Again, you have a good idea here and it's worth pursuing; I'm just pointing out a POSSIBLE problem area down the road...

Earlier you asked about "vbox manage" but it's actually all one word and is a separate program, part of the total vbox package. It allows you even more control over vbox, from the command line, than does the "normal" GUI of vbox. From the vbox GUI, select "help" and then "Content Index" to see the full vbox manual; vboxmanage has a whole chapter devoted to it. Much of the description may be a bit opaque to you at this point, but I think you'll get a lot of information from it and even more as time passes...

---

### Post by ClientAlive on 2011-06-04
> **JKyleOKC said:**
> What you're after is a good idea, but there are a few points that may cause you trouble down the road. They may not, either, so they are not deal-killers -- but you need to be aware of them:

The "hardware" environment in which a VM runs is not at all like the actual physical hardware environment surrounding your real o/s. It's a different CPU, different amount of RAM, different disks (both HD and CD/DVD), different keyboard and mouse, and different network adapters. This means that the kernel modules installed into the VM by the conversion process may be different from those in your actual system, so the two cannot be totally identical.

If a problem or experiment does not involve the kernel modules, the differences ought not have any effect on your results. However, if it DOES (and such things as installing proprietary video drivers will impact the modules) then all bets are off. It may or may not have any effect, and I don't know any way to tell which is which.

Again, you have a good idea here and it's worth pursuing; I'm just pointing out a POSSIBLE problem area down the road...

Earlier you asked about "vbox manage" but it's actually all one word and is a separate program, part of the total vbox package. It allows you even more control over vbox, from the command line, than does the "normal" GUI of vbox. From the vbox GUI, select "help" and then "Content Index" to see the full vbox manual; vboxmanage has a whole chapter devoted to it. Much of the description may be a bit opaque to you at this point, but I think you'll get a lot of information from it and even more as time passes...

Thanks for pointing that out. That's deff something to watch out for. I'm sure it's good to have some idea about those differences in specific situations too. I just figured it's better than nothing and is certainly better than just blazae doing whatever right on my machine when I'm just now learning things or if I don't quite understand some instruction I'm given for something here on the forum.

I had a chance to read that chapter (chapter eight) in the vbox manual last night. Pretty cool stuff. Looks like you can do a lot with it; and, I'm sure, what I'm trying to accomplish too.


> **Derxst said:**
> You can create an iso of your current system using Remastersys. Then you can boot to the iso and recover your system to the virtual machine.

[http://geekconnection.org/remastersys/]("http://geekconnection.org/remastersys/")

Thanks for the tip Derxst. I read everything at that link (for starters). There's just one thing I'm not sure would work with Remastersys and then one question about this overall concept/ strategy I haven't seen a direct answer to yet.

1) Remastersys says it has a 4 gig size limit but my used space is greater than that. Unless I'm misunderstanding some detail of what they are talking about I would need to find way to get my total data size down below that and I don't know if that's feasable for what I'm trying to do. 

> 
Currently there is a size limitation imposed by the genisomage tool in Ubuntu and Debian.  This tool is used to create the iso file.  This limits the maximum single file size for the iso to be set at 4GB which means the entire compressed filesystem.squashfs file(your complete compressed system) must fall under this size.

Reference: [http://geekconnection.org/remastersys/](http://geekconnection.org/remastersys/)


I recall wanting to do something similar using clonezilla. Cloneailla says it uses something called a sarge-image though and I'm not sure if that would be ok. Also, I think it saves the image in compressed form or something so not so sure about that.

My question is about using a recovery disc to do what I'm trying to do. First, I need to be sure I understand correctly what it is. I'm thinknig that it adds an installer into your backed up image so that you literally 'install' the backup when you do the restore. If I'm right about that then why can't I just create the vm by installing it - the same way you make any other virtual machine? The only difference would be that this installation would be my backed up system rather than a fresh install.


**And then there's this . . .**

> **ClientAlive said:**
> ==>  I am now reminded of a problem I came up against when asking/ trying to figure this out before . . .

I have only a 40 gig hard drive and my current installation of Ubuntu uses the whole thing (although not all of the space is actually used). With the method discussed at those links - would I need to have the same amount of hard drive space for the vm as I'm using for my current installation? If so, that would be like saying I need my hard drive to be twice as big as it is and I don't have a magic wand I can wave over this laptop that will do that.

Is there a way of accomplishing my goal so that the vm is whatever size I say it should be? (Like smaller than the available space left on my drive). Or does this method work that way anyhow and I don't have to worry about it?

Thanks

**That is the problem I came up against when I tried to get some answers on doing this before.**

I don't recall where I read it (probably in clonezilla's documentation somewhere) but colonezilla says you need an equal amount of space to restore the clone to. That's what they "said," but when I made an image of my system with it a couple weeks ago the image size was only as big as the used space, not the entire space. I've never tried to restore it because I don't have a second computer to test things on and can't do that to this one for obvious reasons. So what I keep wondering is if they just meant used space or if the thing somehow has information in the image about the disk size and if it doesn't match up it won't run the job.


**==>** Alternatively; and, as far as having the most control over the process, I almost wish I could do this entirely manually. I was reading something in the vbox manual talking about some xml file it creates that has the configuration info in it for the virtual machine? I'm thinking all there is behind the virtual machine is this xml file and a couple entries in a config file or two that vbox uses. Why can't I obtain a template of this xml file, fill in the details with the correct ones for my machine I want to make, make the necessary changes in any config files, and then basically copy and paste the contents of my hard drive into the right folder that vbox uses to store the vm? Basically just dump the fucker right in there.

---

### Post by JKyleOKC on 2011-06-04
> **ClientAlive said:**
> That's what they "said," but when I made an image of my system with it a couple weeks ago the image size was only as big as the used space, not the entire space. I've never tried to restore it because I don't have a second computer to test things on and can't do that to this one for obvious reasons. So what I keep wondering is if they just meant used space or if the thing somehow has information in the image about the disk size and if it doesn't match up it won't run the job.Clonezilla doesn't copy the unused space, so your image is the size it ought to be. Try creating a new VM, giving it a new virtual disk that's a bit larger than your image's used size (if you make the virtual disk dynamic, it will only use disk space when it must rather than grabbing it all at once, and vbox creates its virtual disks in your home directory). Tell the new-VM wizard that it will be a Ubuntu installation but don't actually install anything into it. Then restore your Clonezilla image into that new VM. It ought to accomplish exactly what you're looking for, without risking your real system at all!

It's possible that the differences in environment that I mentioned may pop out of the woodwork and make this approach fail, though. If it does, just delete the new VM and its virtual disk to reclaim the space -- and let us know that it failed, so that we both learn something from the attempt!

---

### Post by ClientAlive on 2011-06-04
> **JKyleOKC said:**
> Clonezilla doesn't copy the unused space, so your image is the size it ought to be. Try creating a new VM, giving it a new virtual disk that's a bit larger than your image's used size (if you make the virtual disk dynamic, it will only use disk space when it must rather than grabbing it all at once, and vbox creates its virtual disks in your home directory). Tell the new-VM wizard that it will be a Ubuntu installation but don't actually install anything into it. Then restore your Clonezilla image into that new VM. It ought to accomplish exactly what you're looking for, without risking your real system at all!

It's possible that the differences in environment that I mentioned may pop out of the woodwork and make this approach fail, though. If it does, just delete the new VM and its virtual disk to reclaim the space -- and let us know that it failed, so that we both learn something from the attempt!


Now this sounds like a plan. I'd even like to do it right now but I'm going to have to find out one more real simple thing first.

Thanks brother.

Jake
:D

---

### Post by ClientAlive on 2011-06-05
**[SIZE="3"]Well glory glory haleluja!!![/SIZE]**

An article almost entirely composed of the things I had questions about. Although you guys basically addressed them all already, it's nice to see it all in one place like this. Thank you all so much for your help on this. I couldn't have done it without you. If anyone ever stumbles on this thread, here are the links I found:

[http://www.pro-9.com/lv/interesting/72-virtual-machine-clone.html](http://www.pro-9.com/lv/interesting/72-virtual-machine-clone.html)

[http://www.ibm.com/developerworks/linux/library/l-clonezilla/index.html?ca=dgr-lnxw100Clonezilla&S_TACT=105AGX59&S_CMP=grlnxw100](http://www.ibm.com/developerworks/linux/library/l-clonezilla/index.html?ca=dgr-lnxw100Clonezilla&S_TACT=105AGX59&S_CMP=grlnxw100)  (this one seems the most promising; but, at this moment says the site is under maintenance. Hope it goes live again soon)

---

### Post by JKyleOKC on 2011-06-05
It looks like both of those links give you the same article -- and it looks very good!

This is essentially a step-by-step procedure for doing what I suggested in outline, in my previous message. She does point out that "your mileage might vary" but it's an excellent tutorial.

---

### Post by ClientAlive on 2011-06-06
> **JKyleOKC said:**
> It looks like both of those links give you the same article -- and it looks very good!

This is essentially a step-by-step procedure for doing what I suggested in outline, in my previous message. She does point out that "your mileage might vary" but it's an excellent tutorial.


I don't know why I didn't notice that sooner. Must have been tired or something. Yeah I think this is going to work. I just have to find the time to sit down and do it.

Yeah, I know it is. I don't know what it is but sometimes I need to see something a couple times before it really sinks in. Maybe I'm getting senile in my old age - lol. (I was born the year the Vietnam war ended - if that tells you anything).

Thanks JKyleOKC. You have a good one man.

:)

---

### Post by JKyleOKC on 2011-06-06
Looks like I must have been about 44 when you were born -- but I stay young mentally by hanging out in places like this...

---

### Post by ClientAlive on 2011-06-07
> **JKyleOKC said:**
> Looks like I must have been about 44 when you were born -- but I stay young mentally by hanging out in places like this...


Just tryin' to keep you on your toes man.

:p

---

### Post by Bucky Ball on 2011-06-07
JKyleOKC, so you are nearly eighty? The Vietnam War ended in 1975. Nice work if so. ;)

---

### Post by JKyleOKC on 2011-06-07
No "nearly" about it; I reached that mark last St. Patrick's Day. I've been into computers since 1959, and full-time since 1965 when I joined G-E's Computer Division. Started as a tech writer due to electronics background and journalism degree, taught myself programming using 110-baud Teletype terminals and G-E's time-sharing system, and finally made the switch into professional programming in the early 80s.

Things are quite different these days from what they were in the mid-60s -- and in most ways, better. I try to use my writing training and background to help explain things that look like frozen mysteries (like the partitioning schemes); it's simply "paying forward" for all the help I've received along the way (and I'm still learning new tricks most every day).

---

### Post by Bucky Ball on 2011-06-07
More strength to ya. I hope I'm still kicking on strong and learning plenty when I reach that milestone. Keep on keepin' on! ;)

---

### Post by ClientAlive on 2011-06-08
> **Bucky Ball said:**
> JKyleOKC, so you are nearly eighty? The Vietnam War ended in 1975. Nice work if so. ;)


I thought it ended in 74 but ok. Guess I was mistaken.

:)

> **JKyleOKC said:**
> No "nearly" about it; I reached that mark last St. Patrick's Day. I've been into computers since 1959, and full-time since 1965 when I joined G-E's Computer Division. Started as a tech writer due to electronics background and journalism degree, taught myself programming using 110-baud Teletype terminals and G-E's time-sharing system, and finally made the switch into professional programming in the early 80s.

Things are quite different these days from what they were in the mid-60s -- and in most ways, better. I try to use my writing training and background to help explain things that look like frozen mysteries (like the partitioning schemes); it's simply "paying forward" for all the help I've received along the way (and I'm still learning new tricks most every day).


Wow JKyleOKC! That's impressive! That's so cool man! What I wouldn't give to have had that experience.

I didn't know computers were around in 59 though. I thought computers didn't come out until like 1980 (with the Apple computer and the Comidore). Maybe I'm just thinking of the PC though.

Remember the old green screen and turtle? That's what they had when I was in grade school.:)

---

### Post by JKyleOKC on 2011-06-08
> **ClientAlive said:**
> I didn't know computers were around in 59 though. I thought computers didn't come out until like 1980 (with the Apple computer and the Comidore). Maybe I'm just thinking of the PC though.

Remember the old green screen and turtle? That's what they had when I was in grade school.:)Computers came into being during WW2, with Eniac (1945), Germany's Z3 (1943), and Britain's Colossus (1944). The first commercial computer in the USA was Univac, which was later absorbed into Sperry-Rand. IBM was not far behind, however, and by the mid-50s dominated the industry.

My 1959 exposure came with my move from being a newspaper reporter to being a tech writer in the Atlas missile program. That project got shut down before I had been with it for a year, and I moved over to the Thompson Ramo Wooldridge company in southern California, where I got the job of writing the programming reference manual for a gadget called the AN/UYK-1. It was a computer built small enough to go through the hatch of a nuclear sub, and powerful enough to do all the calculations needed to implement GPS for the sub. It had a 15-bit word, and 4K of RAM implemented in semiconductors! That got me interested; at the time I was an active ham operator (K5JKX) and doing lots of writing for ham magazines as my moonlighting efforts.

I left TRW and came back to Oklahoma in early 1962, but when I joined G-E in 1965 it was my earlier experience with things digital that got me the job. I was amazed to discover how little progress had been made in the time I had been away from the field, and a chance wisecrack during a brainstorming session got me the assignment to try to "teach the machines how to write the manuals." That developed into nearly a full-time effort, implemented mostly in Basic and assembly language, but by 1970 I had a working publications system going, all over time-shared mainframes and 1700 miles of telephone lines. My backups were on punched paper tape!

When the Altair microcomputer appeared, in January 1975, it was too weak and too high in price for me to have one. However by the time the first IBM PC came out in 1981, my mainframe publishing programs had made an impression on a local entrepreneur and he had suggested a joint venture in which he would provide the hardware and I would do the programs, to create a word processor for the then-popular Radio Shack TRS-80. That marked my entrance into the PC world!

It took several years for me to abandon the TRS-80 and switch to the IBM-compatible world; it was a step backward, since the "Trash-80" had a much more advanced operating system despite its less capable hardware. We still don't have all the features I was using in 1980, but we do have things now that we couldn't even dream of then.

The demise of the green screen is one of those good things! I still see a few systems in use that emulate the old green-on-black look, but I greatly prefer today's LCD monitors!

This is getting way off the original topic; if you want more detail you can visit my web site at [http://www.jimkyle.com/](http://www.jimkyle.com/) for the whole story.

---

### Post by ClientAlive on 2011-06-08
> **JKyleOKC said:**
> Computers came into being during WW2, with Eniac (1945), Germany's Z3 (1943), and Britain's Colossus (1944). The first commercial computer in the USA was Univac, which was later absorbed into Sperry-Rand. IBM was not far behind, however, and by the mid-50s dominated the industry.

My 1959 exposure came with my move from being a newspaper reporter to being a tech writer in the Atlas missile program. That project got shut down before I had been with it for a year, and I moved over to the Thompson Ramo Wooldridge company in southern California, where I got the job of writing the programming reference manual for a gadget called the AN/UYK-1. It was a computer built small enough to go through the hatch of a nuclear sub, and powerful enough to do all the calculations needed to implement GPS for the sub. It had a 15-bit word, and 4K of RAM implemented in semiconductors! That got me interested; at the time I was an active ham operator (K5JKX) and doing lots of writing for ham magazines as my moonlighting efforts.

I left TRW and came back to Oklahoma in early 1962, but when I joined G-E in 1965 it was my earlier experience with things digital that got me the job. I was amazed to discover how little progress had been made in the time I had been away from the field, and a chance wisecrack during a brainstorming session got me the assignment to try to "teach the machines how to write the manuals." That developed into nearly a full-time effort, implemented mostly in Basic and assembly language, but by 1970 I had a working publications system going, all over time-shared mainframes and 1700 miles of telephone lines. My backups were on punched paper tape!

When the Altair microcomputer appeared, in January 1975, it was too weak and too high in price for me to have one. However by the time the first IBM PC came out in 1981, my mainframe publishing programs had made an impression on a local entrepreneur and he had suggested a joint venture in which he would provide the hardware and I would do the programs, to create a word processor for the then-popular Radio Shack TRS-80. That marked my entrance into the PC world!

It took several years for me to abandon the TRS-80 and switch to the IBM-compatible world; it was a step backward, since the "Trash-80" had a much more advanced operating system despite its less capable hardware. We still don't have all the features I was using in 1980, but we do have things now that we couldn't even dream of then.

The demise of the green screen is one of those good things! I still see a few systems in use that emulate the old green-on-black look, but I greatly prefer today's LCD monitors!

This is getting way off the original topic; if you want more detail you can visit my web site at [http://www.jimkyle.com/](http://www.jimkyle.com/) for the whole story.


Sounds cool Jim. I'll have to check that out.

As far as the topic. I'm pretty comfortable I know what to do and be successful with it. I've just been so busy with work lately I'll probably have to wait till Sunday to make a go of it. Can't wait to see what your site looks like. That sure is some amazing history you gave us.

Jake
------------------------------

Edit: Do you do art too? You know there's a jimkyle.net also. And, did you know that at least one link on your books page is broken? The one for DOS 6 Developer's Guide. Maybe others too though.

---

### Post by JKyleOKC on 2011-06-08
I think the only one of the books that's still in print is "Btrieve Complete." I've not done any significant amount of writing for publication since 1997; that's mostly because most of the technical magazines have folded up.

I haven't checked all of the links in several years; guess I ought to do that and disable any that are broken! Thanks for letting me know.

---

### Post by JKyleOKC on 2011-06-08
Nope, no relation to the artist! However when I did a "white pages" search on my name several years ago, it returned more than 500 hits and only three of them were me (including one showing my address as a house in California that I left in 1962).

I'm into genealogy, and have found at least three different lines of Kyle families, all of them from Northern Ireland or Scotland, and possibly related but I've not been able to prove any connections. My own line apparently landed first in South Carolina, then migrated to east Texas before 1850. Another group landed in Delaware, thence to Pennsylvania, and on to Ohio. The third appeared in Virginia and moved west to Tennessee and also to central Texas. There are also some in Canada.

---

### Post by ClientAlive on 2011-06-08
> **JKyleOKC said:**
> Nope, no relation to the artist! However when I did a "white pages" search on my name several years ago, it returned more than 500 hits and only three of them were me (including one showing my address as a house in California that I left in 1962).

I'm into genealogy, and have found at least three different lines of Kyle families, all of them from Northern Ireland or Scotland, and possibly related but I've not been able to prove any connections. My own line apparently landed first in South Carolina, then migrated to east Texas before 1850. Another group landed in Delaware, thence to Pennsylvania, and on to Ohio. The third appeared in Virginia and moved west to Tennessee and also to central Texas. There are also some in Canada.


I've just recently become interested in tracing my family history. It's actually much more involved that I had hoped. Doh!

> 
Howto mark thread: [https://wiki.ubuntu.com/UnansweredPo.../SolvedThreads](https://wiki.ubuntu.com/UnansweredPo.../SolvedThreads)



Yeah, I probably should do that I guess. Just that I saw people are still saying stuff on here and I thought I would be, being rude if I did. You know, sending the wrong message or something. I also want to come back here once I accomplish this task and post something about it that someone might find helpful in the future.

---

### Post by JKyleOKC on 2011-06-09
I'd leave it open at least until you've put together your script to do the renaming...

---

### Post by ClientAlive on 2011-06-09
> **JKyleOKC said:**
> I'd leave it open at least until you've put together your script to do the renaming...


Ok brother. I guess I can be a little impulsive sometimes. Patience was never my strong suit.  

:)
--------------------

Edit: Oh, I knew something seemed funny about what you said. This is the thread about migrating a clone of my os into virtual box. I can do this. I feel very confident about it - but we'll see what happens when it gets down to the brass tax.

As far as the one about renaming files/ finding bad names - what that one guy gave me as an example is like EXTREME!! Holy cow where did he learn that stuff! It's good for me though. This is the kind of thing I do: take something so far above my head and use it as a challenge to pick it apart and learn everything I can about what's going on. Just that, that approach can take a while sometimes. With this new job I started recently I find my free time is at a premium these days too.

Well, anyway. It's all good. Makin' money. Payin' the bills. Gotta love it.

:)

---

### Post by JKyleOKC on 2011-06-09
> **ClientAlive said:**
> This is the kind of thing I do: take something so far above my head and use it as a challenge to pick it apart and learn everything I can about what's going on. Just that, that approach can take a while sometimes.Sounds like my own trick for learning something new: I look for the most authoritative book on the subject that I can find, and of course it contains all sorts of assumptions that I know nothing about -- but that steers me in the right direction to get the background for the subject, and keeps me from wasting a lot of time on things that won't help at all.

Sometimes, though, I simply browse around to find something that sounds interesting. On the forums here, one that I hit fairly often is "Tips and tutorials" which frequently gives me ideas of things I ought to try...

And then things like your renaming thread really help a lot. I had almost no knowledge of "sed" except its existence, when I suggested that it might help. That example you mention really helped me a lot to see how it's used! And that, my friend, is how we learn all that stuff -- like eating an elephant: one byte at a time.

---

### Post by ClientAlive on 2011-06-10
> **JKyleOKC said:**
> Sounds like my own trick for learning something new: I look for the most authoritative book on the subject that I can find, and of course it contains all sorts of assumptions that I know nothing about -- but that steers me in the right direction to get the background for the subject, and keeps me from wasting a lot of time on things that won't help at all.


A man after my own heart. That's one of the most graceful and elegant descriptions I think I've ever seen.


> **JKyleOKC said:**
> 
Sometimes, though, I simply browse around to find something that sounds interesting. On the forums here, one that I hit fairly often is "Tips and tutorials" which frequently gives me ideas of things I ought to try...


That's how it starts for me. I'm bored or there is some inkling of an idea floating around in my head - then, when I start "browsing around," it begins to take shape until POOF the light bulb goes off and I have something very specific I just need to know.


> **JKyleOKC said:**
> 
And then things like your renaming thread really help a lot. I had almost no knowledge of "sed" except its existence, when I suggested that it might help. That example you mention really helped me a lot to see how it's used! And that, my friend, is how we learn all that stuff -- like eating an elephant: one byte at a time.



That's such an encouraging thing to hear you say and it means a lot to me. I spend a lot of time writing things in these posts (like finishing a thread with a summary post and describing my process and results) only in the hope someone will benefit from it. Even if that benefit is something small or something I don't see the connection in. Sometimes I feel pretty dumb while I'm writing it and I'm not sure what others think of me when they read that stuff. I do it anyway though because I believe it is important.


Sunday's coming my friend. Clone my os time is near. I might be able to do it today though - and that would be awesome! I have a couple things to attend to but I'm going to try and squeeze it in.

By the way, there is this business plan I've been working on (a web site idea). Is this something you would be interested in reviewing? Maybe, if it interests you, there is some role you could play in it. Might be a real money maker . . .

Let me know. PM me if you'd like to talk about it.

---

### Post by ClientAlive on 2011-06-12
Ok, so I have an image of my current os, made with clonezilla, saved on my usb drive - except that it seems this may not play out the way I had initially thought.

I gather there are two ways that doing something like this could play out:

(1) The image you create is created in such a way that it can be installed in Virtual Box the same way any other standard install is. I think that in order to do it like that, one would have to obtain an image of their system that includes the installer and such - however they accomplished it.

(2) Use a regular backup image and restore the backup, not to the regular system, but to the right place so it is in Virtual Box.

Now, from what I observed while using clonezilla this morining, I think it is #2 that I will be stuck with - if I use clonezilla. Now I don't want to abandon the clonezilla route too hastily as I have an investment into it already and I am at least a little familiar with using it. what I need to figure out is where to restore this backup to and a better idea of the rest of the process in order/ sequence.

So, with regard to the process order/ sequence, I'm thinking it would go:

(1) Use Virtual Box's gui to create a virtual machine but do not install anything into it.

(2) Reboot the system with the clonezilla live cd in the drive. Use clonezilla to restore the image I created this morning but direct the restoration to the appropriate place - so it goes into the virtual machine not the regular system.

?? And what/ which place would that be ??  And how would I "direct" such a thing in clonezilla anyway ??

(3) I wonder if there would be another obstacle that could arise. Namely symbolic links within the virtual machine. Perhaps there would be broken links after step 2 and they would need to be fixed? This is a complete guess though - as I have no idea how that stuff works inside the virtual machine.

(4) Reboot the computer, say short prayer that all has worked as it should; and, with any luck, enjoy my new vm version of my cloned os.



By the way, the reason I marked this post with the exclamation mark symbol is that I've been planning this project for a week now. Biding my time until today, Sunday, when I actually have time to do this. I'm afraid if I don't get it done today it could be another week before I'll have time to come back to it. Now that's a gut wrenching thought.  :)

---

### Post by JKyleOKC on 2011-06-12
> **ClientAlive said:**
> 
(1) Use Virtual Box's gui to create a virtual machine but do not install anything into it.

(2) Reboot the system with the clonezilla live cd in the drive. Use clonezilla to restore the image I created this morning but direct the restoration to the appropriate place - so it goes into the virtual machine not the regular system.

?? And what/ which place would that be ??  And how would I "direct" such a thing in clonezilla anyway ??

(3) I wonder if there would be another obstacle that could arise. Namely symbolic links within the virtual machine. Perhaps there would be broken links after step 2 and they would need to be fixed? This is a complete guess though - as I have no idea how that stuff works inside the virtual machine.

(4) Reboot the computer, say short prayer that all has worked as it should; and, with any luck, enjoy my new vm version of my cloned os.Almost, but not quite. Step 1 is good. However you don't need to reboot your system at step 2. Instead, when creating the VM, set it up to boot from CD, and attach your actual drive as its CD. Put the clonezilla cd into the drive and then start the VM.

It should boot into clonezilla.

Sorry but I can't help with how to tell clonezilla where to do the restore, since I've never actually used the program. The "where" will be the virtual drive of the VM, but I don't know the clonezilla menus, nor do I know how that drive will be identified. I'd guess, however, that it will be called /dev/sda1 or /dev/hda1. But it may, since at this point it's totally blank with not even an MBR sector, just be identified as something else. Nevertheless it should be the only HD shown for the VM, and since clonezilla is running in the VM rather than in the host, it should only show that single HD as a potential target.

For point 3, symbolic links ought not be a problem. If they exist, they ought to still be valid, especially if your clonezilla image includes your home directory. They **are** symbolic after all, which means there's nothing absolute such as inode numbers in them.

For point 4, after the restore completes, eject the cd from the drive and restart the VM, not the host computer. It should come up with a copy of your host -- but as I mentioned much earlier the differences in hardware might give you trouble, and we can't know about that until you try it.

---

### Post by ClientAlive on 2011-06-12
> **JKyleOKC said:**
> Almost, but not quite. Step 1 is good. However you don't need to reboot your system at step 2. Instead, when creating the VM, set it up to boot from CD, and attach your actual drive as its CD. Put the clonezilla cd into the drive and then start the VM.

It should boot into clonezilla.

Sorry but I can't help with how to tell clonezilla where to do the restore, since I've never actually used the program. The "where" will be the virtual drive of the VM, but I don't know the clonezilla menus, nor do I know how that drive will be identified. I'd guess, however, that it will be called /dev/sda1 or /dev/hda1. But it may, since at this point it's totally blank with not even an MBR sector, just be identified as something else. Nevertheless it should be the only HD shown for the VM, and since clonezilla is running in the VM rather than in the host, it should only show that single HD as a potential target.

For point 3, symbolic links ought not be a problem. If they exist, they ought to still be valid, especially if your clonezilla image includes your home directory. They **are** symbolic after all, which means there's nothing absolute such as inode numbers in them.

For point 4, after the restore completes, eject the cd from the drive and restart the VM, not the host computer. It should come up with a copy of your host -- but as I mentioned much earlier the differences in hardware might give you trouble, and we can't know about that until you try it.


Oh wow this is going to be a real trip! Until just this moment I was thinking that if I made a mistake and it restored to the regular system it could cause me all kind of grief - break the thing basically. Actually though, all that would happen is it would replace my current system with my current system - I hope - and there would be no more harm than 20 min or so of wasted time and effort. Well, sort of wasted. I wouldn't have reached my goal but I would have learned something. Hmmm . . .  think I'll giver er' a try and see what happens. Wish me luck!

:D

---

### Post by ClientAlive on 2011-06-12
> **JKyleOKC said:**
> Almost, but not quite. Step 1 is good. However you don't need to reboot your system at step 2. Instead, when creating the VM, set it up to boot from CD, and attach your actual drive as its CD. Put the clonezilla cd into the drive and then start the VM.

It should boot into clonezilla.

Sorry but I can't help with how to tell clonezilla where to do the restore, since I've never actually used the program. The "where" will be the virtual drive of the VM, but I don't know the clonezilla menus, nor do I know how that drive will be identified. I'd guess, however, that it will be called /dev/sda1 or /dev/hda1. But it may, since at this point it's totally blank with not even an MBR sector, just be identified as something else. Nevertheless it should be the only HD shown for the VM, and since clonezilla is running in the VM rather than in the host, it should only show that single HD as a potential target.

For point 3, symbolic links ought not be a problem. If they exist, they ought to still be valid, especially if your clonezilla image includes your home directory. They **are** symbolic after all, which means there's nothing absolute such as inode numbers in them.

For point 4, after the restore completes, eject the cd from the drive and restart the VM, not the host computer. It should come up with a copy of your host -- but as I mentioned much earlier the differences in hardware might give you trouble, and we can't know about that until you try it.


Ok. So I did just like you mentioned and all seemed to go well. I also found some details here: [http://jlorenzen.blogspot.com/2010/07/restoring-clonezilla-image-using.html](http://jlorenzen.blogspot.com/2010/07/restoring-clonezilla-image-using.html)  which I was careful to pay attention to. Such as enabling the usb drive my image is on. I didn't need to use a second usb like the guy in that article because my clone is small and I do have enough space on my local disk for it. When I got to that point in clonezilla it was as you had supposed - the only option for where to restore to is the virtual disk (and, it turns out, it is named in such a way that it's clear that's what it is). When I moved past that step and the restoration process began I got an error message from clonezilla. Apparently it doesn't like the partitions structure on that virtual disk (or lack thereof). I've attached a picture of that error screen. There was more to it than what shows up in the picture but I couldn't get the screen to scroll up to show the rest.

Based on what I see I think that one of two things needs to happen.

(1) The virtual disk needs to have a partition structure created in it that is the same as my local disk. The same as the image that came from it. I don't see any way that could happen though. And for a couple different reasons too.

(2) Something in the clonezilla image, some file or something, needs to be edited to match the way the virtual disk is. Something renamed, possibly more.

There is a reference to this editing of files in clonezilla here: [http://forums.linuxmint.com/viewtopic.php?f=42&t=67140](http://forums.linuxmint.com/viewtopic.php?f=42&t=67140)  but they seem to be doing it for a different reason/ different outcome.

What I don't get is that the guy in the first link in this post - didn't seem to have any trouble with doing this.

So, I guess I'll keep looking around and see what I can find or what to do to get past this point.
--------------------

Edit: I just thought of this, but, part of what I think happens in a standard install is that a partition structure is created. I would have thought that clonezilla deals with this when restoring. If it does, that leaves only one other option that I can think of. That because it is a virtual disk and not a regular hard drive it's somehow different and won't let clonzilla create the partition table. This doesn't make sense though because if that were the case it wouldn't let a standard install do it either.

There is a third possibility:

The size of the virtual disk is smaller than the total size of my local hard drive (obviously). Here's what I find odd about this possibility though:

(1) I thought we covered this issue further back in this thread. We determined that clonezilla only uses the used space on the disk and so the virtual disk didn't need to be the same size as my whole hard drive.

(2) I looked at the size of my used space before creating the image with clonezilla this morning. It said it was 5.5 gig. The virtual drive I created is 8 gig.

If, for some odd reason, this is the problem - I can only think of one possible solution. Something in the clonezilla image needs to be edited to match, not the size of my local disk (what it probably recorded when it created the image), but the size of the virtual disk. So, if part of what clonezilla does when it restores is create a partition table, doing this would be similar to using an application to create partitions on my drive. Only, in this case, it would be telling whatever utility clonzilla uses the information you want it to have for the partition table when it makes it. Kind of like a back door or something.

If the size of the used space is only 5.5 gig and the size of the virtual disk it is to go onto is 8 gig - then there shouldn't be any problem with doing something like that.

Any ideas people??
--------------------------------

Edit 2: I just looked at the picture I attached more closely. It says: Error: /dev/sda: unrecognized disk label."  I think what it's saying is something in the virtual disk is labeled /dev/sda and that doesn't line up with what is in the image I want it to restore.

I'm stumped.

---

### Post by CharlesA on 2011-06-12
The virtual drive has to be the same "physical" size as the physical drive.

500GB drives needs to be restored to a 500GB virtual drive.

You can use a dynamic sized disk so that it only uses 5GB of space, but the VM sees that whole 500GB.

---

### Post by ClientAlive on 2011-06-12
> **CharlesA said:**
> The virtual drive has to be the same "physical" size as the physical drive.

500GB drives needs to be restored to a 500GB virtual drive.

You can use a dynamic sized disk so that it only uses 5GB of space, but the VM sees that whole 500GB.


I see. Well, even if I never actually use all the space (I couldn't) it still seems pretty hoakey. There isn't a way to change some configurations in the image to make it think it's smaller? I mean, the used space is smaller. Just that I don't know how that data is spread out across the disk. Just because the used space is only 5.5 gig doesn't mean it's all together in one place I suppose. Is that thinking on the right track?

And what about the error in the picture? what it's complaining about there is the disk label. Unless I'm not understanding what is meant by "disk label."
---------------------

Edit: Ok, but what about this . . .

I just looked at the properties of the image I created this morining. It says the size is 2.6 gig. I think clonezilla compresses the file when it saves it. Now . . .

The size of my entire local hard disk is very roughly 40 gig. Is a standard/ default installation with nothing special about the partitions and Ubuntu is the only system on this machine (so that whole 40 gig is being used by my one and only Ubuntu system - that's how things are set up).

Here's the readout from Applications > Disk Usage Analyzer:

Total File System Capacity: 35.1 GB (used: 5.5 GB available: 29.6 GB)

So here's the thing - I can see an image size of 2.6 gig from a used space of 5.5 gig, but I can't picture an image size of 2.6 gig from a total size of 35.1 gig. You can compress 5.5 gig down to 2.6 gig (especially if a lot of it is text), there's no way you can compress 35.1 gig down to 2.6 gig though. I'm not sure how this works?

---

### Post by CharlesA on 2011-06-12
Yeah, it only copies the used data and compresses it.

---

### Post by JKyleOKC on 2011-06-13
As CharlesA said, define your virtual disk to be 40 GB and "dynamic" so that it will actually use only enough space to hold your 5.6 GB. I agree that it's a bit hokey to do it this way, but then Clonezilla is a free package and doing it this way eliminates lots of potential problems in dealing with mismatched disk sizes. As it is, the program only needs to look at the disk to be assured that there's enough room -- even if, as in this case, none of that "enough" space actually exists before it's really needed!

When you restore from Clonezilla, it will effectively defrag your files so that they are all up at the front. This is implicit in the way that it compresses and decompresses without storing any unused disk space.

As for not having a label, you may need to dig into the VBox manual chapter on VBoxManage to see if there's a way to create the virtual disk with a label -- and through the Clonezilla docs to see if they tell you anything about what kind of label it's looking for! My experience is that the MBR for a partition contains its label, so no label would be present until the drive was partitioned.

However, it's also quite possible that this error message is a red herring caused by the size mismatch. Quite often, a subtle error will confuse a program into taking a wrong path and then displaying a totally unrelated message a bit later. I've had it happen many times!

---

### Post by ClientAlive on 2011-06-13
> **JKyleOKC said:**
> As CharlesA said, define your virtual disk to be 40 GB and "dynamic" so that it will actually use only enough space to hold your 5.6 GB. I agree that it's a bit hokey to do it this way, but then Clonezilla is a free package and doing it this way eliminates lots of potential problems in dealing with mismatched disk sizes. As it is, the program only needs to look at the disk to be assured that there's enough room -- even if, as in this case, none of that "enough" space actually exists before it's really needed!

When you restore from Clonezilla, it will effectively defrag your files so that they are all up at the front. This is implicit in the way that it compresses and decompresses without storing any unused disk space.

As for not having a label, you may need to dig into the VBox manual chapter on VBoxManage to see if there's a way to create the virtual disk with a label -- and through the Clonezilla docs to see if they tell you anything about what kind of label it's looking for! My experience is that the MBR for a partition contains its label, so no label would be present until the drive was partitioned.

However, it's also quite possible that this error message is a red herring caused by the size mismatch. Quite often, a subtle error will confuse a program into taking a wrong path and then displaying a totally unrelated message a bit later. I've had it happen many times!


I just tried doing it with a larger disk size and got another, different, error message this time.

I deleted the other vm. Looked in gparted to see the size of the entire disk to more sig digits than disk usage analyzer will tell you and it said 35.69 GiB. I created a virtual machine with a disk size of 35.69 GB (now I have heard there is a difference between GiB and GB but I don't know the detail or what the conversion is). So then I go through the process with clonezilla again. I get to the point where I've made all my selections and tell it to go ahead with the restore. Right away it gives me an error saying two things that stand out. (1) It says "cannot create partition outside the local disk. And then (2) It poses the question, is the disk the right size (or something of that nature).

I had found a thing about resizing/ shrinking the size of the virtual disk here: [http://forums.virtualbox.org/viewtopic.php?t=2507&start=0&postdays=0&postorder=asc&highlight=](http://forums.virtualbox.org/viewtopic.php?t=2507&start=0&postdays=0&postorder=asc&highlight=)  and had intended to do that at the very end if I could get this installed and working. Now I wonder if I can't do that to the clonzilla image first, then try again to install it.

---

### Post by ClientAlive on 2011-06-13
The more I read about clonzilla I find myself confused about how and why it would need the space you restore to, to be the same size as the orig it was taken from. I read that it does not do a bit for bit copy. This link [http://ubuntuforums.org/showthread.php?t=704219](http://ubuntuforums.org/showthread.php?t=704219)  talks about it and says other things that make me question why this would be the case. It says it does not copy unused sectors in that link and I've read that elsewhere as well. How then does it record the original size and what is really going on here? I keep keep thinking that it has a config file in the image somewhere that records the orig size and compares it with the size of where you're trying to restore. If that were the case then one should be able to just edit that file to a smaller figure for the size - something more in line with the used space size or just slightly over that. I'm going to have to dig around in that image and see what is in there.
-------------------------

Edit: The following is the list of files inside that image:

```

SystemClone_2011-06-12-img$ ls
disk               parts                      sda-mbr
Info-dmi.txt       sda1.ext4-ptcl-img.gz.aa   sda-pt.parted
Info-lshw.txt      sda1.ext4-ptcl-img.gz.ab   sda-pt.sf
Info-lspci.txt     sda-chs.sf                 swappt-sda5.info
Info-packages.txt  sda-hidden-data-after-mbr

```

Even just looking at the names seems to be very telling. Hmm . . .


Edit 2: This is the partition table. It's in the file called, "sda-pt.sf"

```

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size= 74838016, Id=83, bootable
/dev/sda2 : start= 74842110, size=  3297282, Id= 5
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start= 74842112, size=  3297280, Id=82
sda-pt.sf (END) 

```

And this is the swap file. It has a place for "Label" and it is blank:

```

UUID="1bcb2760-6aff-4b63-a33f-3f34c9685642"
LABEL=""
swappt-sda5.info (END) 

```

---

### Post by JKyleOKC on 2011-06-13
I'd make the disk size 40 GB or maybe even 50; it's my impression that the two sizes don't have to match precisely but the target just has to have **enough** room to handle all of the source disk (disk itself, not the files on it). Once the restore completes, you can shrink the virtual disk back down to 5.6 or a bit more. I'd make it 10 to give room for some playing around, since it won't be used until needed (in 2-GB chunks if I remember correctly from when I used dynamic sizing).

I've seen similar error messages from partitioning before and they usually come about because of a GB vs GiB mismatch. Drive manufacturers all use GB, powers of 10; programs **mostly** use GiB, powers of 2, but **not** always. That's why I always allow at least a gigabyte of leeway when setting sizes.

EDIT: Okay, didn't see your last post until after posting this one. The partition table tells the tale. Its sda1 is your system, and it's taking up the whole 40 GB except for the swap space at sda5. The sda2 entry is the extended partition that contains the swap; sda3 and sda4 don't exist (size=0) but are there to keep the table general. The swap partition is two sectors (total 1024 bytes) smaller than its container;; these hold its metadata.

It might be possible to edit the partition table, but that might also FUBAR it beyond redemption so I would not try it. Instead, define the virtual disk to be plenty big enough, more than 40 GB as I suggest above. The restore may still fail; it all depends on whether Clonezilla is smart enough to recognize that sda1 is only partially used, and adjust the partition size accordingly. If it's not, then you'll have to modify your actual partitioning to use no more than half the drive, and include the extended partition in that half -- which runs the risk of destroying your real system, which is what we're trying to avoid!

Since external drives are so low in cost these days, I would simply get one and put the guest drives on it. About a year ago, I bought a 500-GB drive locally for a little more than $50, new over the counter...

---

### Post by ClientAlive on 2011-06-13
> **JKyleOKC said:**
> I'd make the disk size 40 GB or maybe even 50; it's my impression that the two sizes don't have to match precisely but the target just has to have **enough** room to handle all of the source disk (disk itself, not the files on it). Once the restore completes, you can shrink the virtual disk back down to 5.6 or a bit more. I'd make it 10 to give room for some playing around, since it won't be used until needed (in 2-GB chunks if I remember correctly from when I used dynamic sizing).

I've seen similar error messages from partitioning before and they usually come about because of a GB vs GiB mismatch. Drive manufacturers all use GB, powers of 10; programs **mostly** use GiB, powers of 2, but **not** always. That's why I always allow at least a gigabyte of leeway when setting sizes.

EDIT: Okay, didn't see your last post until after posting this one. The partition table tells the tale. Its sda1 is your system, and it's taking up the whole 40 GB except for the swap space at sda5. The sda2 entry is the extended partition that contains the swap; sda3 and sda4 don't exist (size=0) but are there to keep the table general. The swap partition is two sectors (total 1024 bytes) smaller than its container;; these hold its metadata.

It might be possible to edit the partition table, but that might also FUBAR it beyond redemption so I would not try it. Instead, define the virtual disk to be plenty big enough, more than 40 GB as I suggest above. The restore may still fail; it all depends on whether Clonezilla is smart enough to recognize that sda1 is only partially used, and adjust the partition size accordingly. If it's not, then you'll have to modify your actual partitioning to use no more than half the drive, and include the extended partition in that half -- which runs the risk of destroying your real system, which is what we're trying to avoid!

Since external drives are so low in cost these days, I would simply get one and put the guest drives on it. About a year ago, I bought a 500-GB drive locally for a little more than $50, new over the counter...


I'm willing to try making the virtual disk larger than my actual hard drive but there's something ominous about that, that makes me really nervous. I suppose my operating system is smart enough not to let anything get overwritten but that seems to involve a pretty healthy dose of trust unless one knows exactly how it works and know for absolute certain nothing is going to break by doing that. I imagine you do know Jim and I trust you to steer me straight.

One thing I keep thinking about and would like to consider is this thing about resizing/ shrinking. Now this software they talked about at the link I posted earlier supposedly works by deleting the zeros in virtual disk file. Apparently a zero means empty. So if what they are talking about is doing it with a virtual disk file, and the image I have from clonezilla contains my hard disk in a file somewhere, then I should be able to do the same thing to the image that they're talking about doing to the virtual disk.

If it is a compressed file, I think the way the compression works with empty space is it somehow records that there are x number of zeros rather than actually writing them all out. If that is the case then one could simply edit that compressed file of my hard disk to say there are less zeros right? Same effect.

In either of those two cases I think other files would then have to be edited to match what had been done there. (I don't want to call it an "image" because I get the impression "image" refers to the whole thing - with all the files in it. I don't know for sure - but I think the logic holds).

I think the question I need to answer is:

If clonezilla only records the used sectors, how; or, in what way, does it know what the entire disk size is? If I can find that out I think I would really be on to something.

Yes, I could make the virtual disk file on my external drive. I have a 230 gig drive sitting right here on the table next to me. That would be easy but would I then be cutting myself short? Would that be the sissy way out? I know I stand to gain more if I don't. On the other hand though, by not taking that easy way out I put off just using it. It's a difficult balancing act sometimes. Truthfully? I'm more interested in what I can learn and the skills I can gain. There's learning to be had all over the place though and sometimes its tough to know how far to chase a rabbit.

:D
------------------

Edit: Ok, so this idea just took shape for me. What a guy could do is:

(1) Shrink the file that contains data from your hard disk by eliminating zeros. If it's a compressed file, and I'm pretty sure it is with clonezilla, you would change the number or zeros that are recorded as being in that file buy reducing that number.

(2) Edit the partition table to reflect the new size.

Right?

So if a guy did it manually, and it works, he could go on to write a script that does it for you. If the script were done right it's something that could actually be added to clonezilla itself. It could read and use the used space size in the partition table right off the local disk; and, possibly also, compare that with the zero count in the data file - then use that information to make the appropriate changes in both places before creating the image. The end result would be a shrunk image that is only the size of the used space with nothing extra.

---

### Post by JKyleOKC on 2011-06-14
I haven't examined a Clonezilla image file in detail as you have, but I suspect that it doesn't actually contain full disk images at all. Instead, I think that it contains enough information to re-create the disk's partition structure from scratch, on a totally blank drive that has enough space to do so, and then restores each file from compressed copies in much the same fashion that ordinary Zip files are handled. This would automatically drop all the zeroed sectors of the drive, and as an added bonus would defragment the drive in the process.

If my guess is correct, then editing the partition table in the image file ought to accomplish your goal -- but I can't recommend it as a solution because there's no way of telling whether any of the compressed system files inside the image depend on the existing values in the partition table.

To interpret the partition table in terms of actual sizes, you have to know that one sector contains 512 bytes. All the values in the partition table you posted earlier are in terms of sectors, so they must be multiplied by 512 to convert them to byte counts. You have to add the size of each partition to its starting point to find the starting point for the next partition, and must also round the starting points up to cylinder boundaries. A "cylinder" is the space contained by all tracks that are the same distance from the disk center. 

Think of a drive with multiple disks, all on the same shaft, with heads on each side of each disk. Assume a total of 5 platters, giving 10 heads, and 200 tracks on each surface (these figures are from an actual mainframe disk drive that I worked with in the 70s; modern drives have quite different architecture, but still use the terminology developed in the old days). The cylinder addressed as "100" would consist of the areas at track 100, addressed through heads 1 to 10 in sequence. Driver software would not address individual tracks or individual heads, just the cylinder. That's why partitions should end on cylinder boundaries. And knowing just where these boundaries are requires detailed knowledge of how the drive is laid out physically; a two-platter drive would have smaller cylinders than the example with five platters. This knowledge is built into our driver programs, but I don't know where to find it to verify that any manual editing of partition values is correct!

If my guess is correct, there really aren't any zeroes in the image file (I keep calling it this because that's how Clonezilla refers to it) to edit out.

As for the possibility of overwriting part of your working system, I've found over the years that Murphy's Law applies to just about everything so if anything can go wrong, it will. And with computers, it's just about impossible to rule out even the most improbable catastrophe. That's why it's always a good idea to have a total backup of the system before attempting anything major, such as installing a shadow copy in a VM. Since you have an external drive large enough to hold another image of your system, and a bootable CD of Clonezilla, make a current backup to the external and then feel safe in trying the restore with an impossibly large virtual drive. If it does overwrite any part of your system, restore from the backup image and tally up the experience. You could take the same approach to resizing the partitions of your real system; with a good backup from which to recover if anything goes awry, you could shrink sda1 to a bit less than half of the disk, then move sda2 (and with it sda5) down to occupy the rest of the first half, and leave the second half of the disk unassigned. A Clonezilla image made after doing this would only contain the half-sized drive data, and should be internally consistent. If you store that image on the external drive also, you could then restore your original partitions from the backup image of them to be sure of having plenty of room, define a virtual drive for the guest system that's only 20 GB or so, and restore to it from the smaller backup image. This sounds like a lot of work, but probably would actually be less than trying to modify the image you are now working with!

---

### Post by ClientAlive on 2011-06-14
> **JKyleOKC said:**
> I haven't examined a Clonezilla image file in detail as you have, but I suspect that it doesn't actually contain full disk images at all. Instead, I think that it contains enough information to re-create the disk's partition structure from scratch, on a totally blank drive that has enough space to do so, and then restores each file from compressed copies in much the same fashion that ordinary Zip files are handled. This would automatically drop all the zeroed sectors of the drive, and as an added bonus would defragment the drive in the process.

If my guess is correct, then editing the partition table in the image file ought to accomplish your goal -- but I can't recommend it as a solution because there's no way of telling whether any of the compressed system files inside the image depend on the existing values in the partition table.

To interpret the partition table in terms of actual sizes, you have to know that one sector contains 512 bytes. All the values in the partition table you posted earlier are in terms of sectors, so they must be multiplied by 512 to convert them to byte counts. You have to add the size of each partition to its starting point to find the starting point for the next partition, and must also round the starting points up to cylinder boundaries. A "cylinder" is the space contained by all tracks that are the same distance from the disk center. 

Think of a drive with multiple disks, all on the same shaft, with heads on each side of each disk. Assume a total of 5 platters, giving 10 heads, and 200 tracks on each surface (these figures are from an actual mainframe disk drive that I worked with in the 70s; modern drives have quite different architecture, but still use the terminology developed in the old days). The cylinder addressed as "100" would consist of the areas at track 100, addressed through heads 1 to 10 in sequence. Driver software would not address individual tracks or individual heads, just the cylinder. That's why partitions should end on cylinder boundaries. And knowing just where these boundaries are requires detailed knowledge of how the drive is laid out physically; a two-platter drive would have smaller cylinders than the example with five platters. This knowledge is built into our driver programs, but I don't know where to find it to verify that any manual editing of partition values is correct!

If my guess is correct, there really aren't any zeroes in the image file (I keep calling it this because that's how Clonezilla refers to it) to edit out.

As for the possibility of overwriting part of your working system, I've found over the years that Murphy's Law applies to just about everything so if anything can go wrong, it will. And with computers, it's just about impossible to rule out even the most improbable catastrophe. That's why it's always a good idea to have a total backup of the system before attempting anything major, such as installing a shadow copy in a VM. Since you have an external drive large enough to hold another image of your system, and a bootable CD of Clonezilla, make a current backup to the external and then feel safe in trying the restore with an impossibly large virtual drive. If it does overwrite any part of your system, restore from the backup image and tally up the experience. You could take the same approach to resizing the partitions of your real system; with a good backup from which to recover if anything goes awry, you could shrink sda1 to a bit less than half of the disk, then move sda2 (and with it sda5) down to occupy the rest of the first half, and leave the second half of the disk unassigned. A Clonezilla image made after doing this would only contain the half-sized drive data, and should be internally consistent. If you store that image on the external drive also, you could then restore your original partitions from the backup image of them to be sure of having plenty of room, define a virtual drive for the guest system that's only 20 GB or so, and restore to it from the smaller backup image. This sounds like a lot of work, but probably would actually be less than trying to modify the image you are now working with!


I think the best plan of action is maybe to do both. I can use the external drive and my thumb drive to, hopefully, get a working vm going. Then, on the side, maybe I can work on the whole resizing/ shrinking thing. If you look on the internet about it you'll see that people have been petitioning clonezilla to include something like this in their program anyway. I don't know why they haven't done it yet. Maybe it's real complicated to implement. I don't know. But I know I can probably learn a lot about hard drives and how data is stored and partitioning, etc. So maybe I can have my cake and eat it too!  :D

I let you know what happens. Thanks for the great info.

---

### Post by ClientAlive on 2011-06-14
[COLOR="Red"][size="4"]Please ignore everything you see in 'this' post. Whatever I described doing here did not end up working correctly. For a description of a successful way see post #55.[/size][/COLOR]
====================================================================================


**[size="2"]its doing iiittt!!!!!! Ahhh haaa haaa haaa ha!!!!![/size]**

          :d
------------------

Edit:

Ok, sorry for that little outburst.:D  That was pretty exhilarating though.

So I got my host os cloned and installed in Virtual Box. Here's how it worked for me:

1) I made a clone of my host o/s with clonezilla and stored it on my 230 gig external usb drive.

2) I made a copy of that onto my 8 gig usb thumb drive (you can't have the destination drive mounted when you install in the virtual machine later).

3) I created a virtual machine with a 50 gig disk and located it's disk on my 230 gig external.

4) Go into the settings of the virtual machine and and uncheck both "floppy" and "Hard Disk" in the "Boot Order" area (this is under "System" in the list in the left hand pane of the window).

5) Shut that settings window, insert a cd or dvd disc with clonezilla live on it into the disc drive, and start your virtual machine. The virtual machine will run clonzezilla inside itself from that disc.

6) Follow the steps through clonezilla to, ultimately, restore the clone you made of your host - but into the virtual machine.

Notes:

* When you get to the step in clonezilla where you choose the destination for the resore - it will be apparent by the name that it is the correct selection and not on your real machine. If more than one item appears in the list just make sure you read the names carefully. The right one will be obvious.

* The way to set the destination for you virtual machine disk (involved in step 3) is click the browse button next to the "location" field. When you get through about 4 or 5 clicks - going through the wizard to create the vm - you will eventually arrive at a screen that says: "Virtual Disk Location and Size" at the top of it. The first field in that window had the title above it "Location" and to the right of that field there is a small brown or yellow square icon that looks like a folder. Clicking it will allow you to select a location where you want the disk to be stored.

* When you modify the settings of the virtual machine (step 4) you may want to enable a couple other things as well. Perhaps you would like to enable "Enable IO APIC" and/ or, "Enable PAE/NX" under the 'Processor" tab in "System".

* In step 6, when going through the steps in clonezilla to restore the image, you will come to a point where you select to work with usb drive (that's not how it reads but you should recognize it when you see it). At that point you will need to, first, make sure the usb drive is enabled withing virtual box. This can be done by clicking "Devices > USB Devices" and then selecting the name of your usb drive. This first "Devices" item is found in the menu bar across the top of the virtual machine window after starting the machine. You may also have to do this every time you start the virtual machine after that (at least until or if you move it's disk from the usb drive to your local disk).

* After a successful install of the clone image into Virtual Box, but before running the machine, you will need to go back into the machine's settings and re-select both "Floppy" and "Hard Disk" so that it will boot from the virtual machine's disk now.

* The version of Virtual Box I did this on is: Version 4.0.8 r71778

Happy vm'ing!



PS: Because of the size limitations of my local disk, I was forced to make the virtual machine's disk grossly large compared to the size of the data on it. Now, my next step is to resize/ shrink that disk to a more reasonable size (perhaps 10 gig). Finally, I will want to synchronize many of the folders and possibly processes between my host o/s and it's cousin "the vm clone." The original goal was to have a matching host and guest but to keep them matching I will need to find a way to synchronize key folders and processes. If; after searching the net, I can't find the information I need, I'll start a new thread about it.


I was given soooo much awesome information in this thread! I appreciate everything you guys shared with me more than I have words to say.

Have a great evening everyone.

Jake

---

### Post by ClientAlive on 2011-06-16
> 
"FATAL: Unable to read from the boot medium. System halted."



Well, I thought I had it all sorted out but the above quote is what I get whenever I try to start the machine - after having completely closed Virtual Box the other night and re-opening it again today. I know what is going on. When I click "Start" to start the machine the window for the machine opens up and in "Devices > USB Devices" I see that it is not enabled. It is impossible to get to it and enable it quickly enough for the machine to start successfully. Perhaps the way to address it was back when I had just finished the install and had run the machine for the first time. Perhaps if I would have taken a snapshot of the machine with the usb drive enabled it would have saved that way? I'm not for certain as I don't know exactly what taking a snapshot covers or not. Nevertheless, it seem this is a new challenge I need to overcome in order to get this thing working. I will start a new thread for this though as this one is getting a bit unruly.

:D

---

### Post by JKyleOKC on 2011-06-16
With the USB drive plugged in and powered up, but not opened in Ubuntu itself, open up VBox, select the VM, and in its "Settings" dialog select USB. You'll see a (probably empty) list of "filters" in the resulting dialog. There will also be a checkbox for USB 2.0. If the box is not checked, check it; 2.0 gives nearly double the transfer speed of 1.1 and is almost 100% compatible.

Alongside the filter list on the right is a stack of buttons. The one just below the top, with a "+" sign on it, will create a device-specific filter. Click it and another button will appear to list the known devices, one of which will be your USB drive. Select it and hit OK. Then "OK" your way out of VBox to the point where you can start the VM.

It should come up properly this time. The filter will keep Ubuntu itself from grabbing the USB port, and also will add the checkmark to the "devices" menu for you. I've had to do this with the printer attached to my Email VM in order to use its Windows drivers instead of the Linux ones that would otherwise take over and prevent me from using its bells and whistles.

If it does come up properly, shut it down by clicking the "close" button at top right of the VM window, and select "save the state" instead of "power down" from its options. This will create a snapshot automatically and make it start much faster next time. The only time I actually power down is when I need to change something in the settings!

I'll look for your other thread but replying to this one was the quickest way I know to get the info to you...

---

### Post by ClientAlive on 2011-06-16
> **JKyleOKC said:**
> With the USB drive plugged in and powered up, but not opened in Ubuntu itself, open up VBox, select the VM, and in its "Settings" dialog select USB. You'll see a (probably empty) list of "filters" in the resulting dialog. There will also be a checkbox for USB 2.0. If the box is not checked, check it; 2.0 gives nearly double the transfer speed of 1.1 and is almost 100% compatible.

Alongside the filter list on the right is a stack of buttons. The one just below the top, with a "+" sign on it, will create a device-specific filter. Click it and another button will appear to list the known devices, one of which will be your USB drive. Select it and hit OK. Then "OK" your way out of VBox to the point where you can start the VM.

It should come up properly this time. The filter will keep Ubuntu itself from grabbing the USB port, and also will add the checkmark to the "devices" menu for you. I've had to do this with the printer attached to my Email VM in order to use its Windows drivers instead of the Linux ones that would otherwise take over and prevent me from using its bells and whistles.

If it does come up properly, shut it down by clicking the "close" button at top right of the VM window, and select "save the state" instead of "power down" from its options. This will create a snapshot automatically and make it start much faster next time. The only time I actually power down is when I need to change something in the settings!

I'll look for your other thread but replying to this one was the quickest way I know to get the info to you...


Thanks man. I'm wondering whether I'll find I need to have guest additions installed (it isn't now). I guess I'll find out in a min here.

One consideration for me is that I have not yet dealt with shrinking that disk. I'm confident that changing settings and adding a usb filter will not have a negative affect on doing that later but I'm a little cautious about the snapshot and what effect that may have.

Here we go . . .
------------------------

Edit:

Well, it's odd. I'm familiar with what you describe I just hadn't known that it was the answer (or should be). I get the same error; and, when I close the virtual machine, nautilus opens the widow for that drive. Actually, to begin with, there were two nautilus windows open and I closed one but didn't realize there was a second. Then I tried to start the vm, got the error, realized the other window, shut down the vm, closed the window, tried to start the vm again (with no nautilus windows open) - and got the same result/ same error and a failed launch.

So, the thing has to run in order to install the guest additions right? So if that is the problem then I'm screwed? The vBox Manual: [http://www.virtualbox.org/manual/ch04.html#idp11234128](http://www.virtualbox.org/manual/ch04.html#idp11234128)  chapter 4 says that some distros come with guest additions installed. If that were true of Ubuntu 10.04 (the disro/ release in question) then I could eliminate that. I checked in synaptic, however, on my host o/s. It's not installed. If it isn't installed here then it isn't installed there (being a clone).

---

### Post by Rasa1111 on 2011-06-16
> **Derxst said:**
> You can create an iso of your current system using Remastersys. Then you can boot to the iso and recover your system to the virtual machine.

[http://geekconnection.org/remastersys/](http://geekconnection.org/remastersys/)

Exactly what I would do. (and have done)
Remastersys works great!

---

### Post by ClientAlive on 2011-06-16
> **Rasa1111 said:**
> Exactly what I would do. (and have done)
Remastersys works great!


Ok Rasa1111. But it would have to have the benefit of not requiring the virtual disk to be the same size as the hard disk on my computer - otherwise it might not be much different. Does it do that? Install only the used space and not require the entire disk size for install?

---

### Post by Rasa1111 on 2011-06-16
> **ClientAlive said:**
> Ok Rasa1111. But it would have to have the benefit of not requiring the virtual disk to be the same size as the hard disk on my computer - otherwise it might not be much different. Does it do that? Install only the used space and not require the entire disk size for install?

 Im pretty sure that benefit is there. 
Pretty sure I am not required to have my virtual disk the same size as my computers hdd. 

Sorry if I am misunderstanding you though. 

But here is a clone of my 10.10 install, running in VB on my 11.04 install. 
[ATTACH]195319[/ATTACH]

If I have misunderstood, please elaborate for me. 
and I will further elaborate, if you need.

---

### Post by Rasa1111 on 2011-06-16
Just checked..
I only allocated 7.7 GB to install it in VB. (OS size is about 3.8 GB)
My hdd is 140GB

---

### Post by ClientAlive on 2011-06-17
> **Rasa1111 said:**
> Im pretty sure that benefit is there. 
Pretty sure I am not required to have my virtual disk the same size as my computers hdd. 

Sorry if I am misunderstanding you though. 

But here is a clone of my 10.10 install, running in VB on my 11.04 install. 
[ATTACH]195319[/ATTACH]

If I have misunderstood, please elaborate for me. 
and I will further elaborate, if you need.


Wowwww . . . That look is sik!! I wish my computer looked like that.  :D


The thing about hard drive size is in this thread and can be seen being talked about in post #'s 8 (bottom half), 11 (last half), 37 (middle of "Edit", and others . . .

Note post #12 - I tried that. (compare posts #35 - 40 and 46). The install was successful only after making the virtual disk larger than the original size of the disk the image came from. Even though clonzilla only copies the used space, it seems the partition table it uses is the same as from your original disk that the image came from - thus requiring a destination disk size of, not just the size of the used space, but the size defined by the partition table (the whole enchilada!).

That fact is causing me all kinds of grief! The real goal here is not to have a virtual machine who's disk is on an external drive, but to have one who's disk is on my local drive right along with my host o/s. I haven't found a way to do that without jumping through all kinds of sick hoops. It's a horror show! The host o/s I wanted to clone to begin with takes up the entire local disk see "Edit" at bottom) - therefore, when I clone the thing, the clone needs a space to install to that is the size of the entire local disk. That fact makes it impossible to store the target disk (vm disk) on my local drive (it would have to be bigger than it is and I don't have a magic wand I can wave over the laptop and make that happen).

So, I can't believer there isn't software out there to do the job I'm trying to do and do it in the way I need - so that the restore size is only the size of the used space, not the size of the whole drive. When I heard mention of remastersys again and inkling of hope sprung up within me - but then I remembered this . . .

Check out post #11 where a concern about remastersys even working for me is stated . . .

> 
1) Remastersys says it has a 4 gig size limit but my used space is greater than that. Unless I'm misunderstanding some detail of what they are talking about I would need to find way to get my total data size down below that and I don't know if that's feasable for what I'm trying to do.



Perhaps I have some faulty assumptions, incorrect facts, and or unrealistic goals - please correct me on these points because I really want to learn.

:)
------------------

Edit:

It isn't that the host o/s takes up the entire local drive, the used space is actually only about 11 GiB right this minute. So with a 35.1 GiB drive most of that is used space.

---

### Post by ClientAlive on 2011-06-25
Well I guess I finally got it right this time. What a learning curve!

So I got my o/s p2v'd into Virtual Box. Even managed to shrink the thing down to 9.8 gb grand total with about 3.6 gb unused space left. That seems just about right for me since I don't think I'll be putting anything on it that eats up a whole ton of space.

So the route I went was:

1> Used the dd command to make a raw image file and saved it to my external usb drive/
2> Used CloneVDI (with "Compact drive while copying" ticked/ selected) to clone and compact that raw image to my local, physical disk.
3> Made a vm and used that vdi as it's disk.
4> Set that vm so that it only boot from cd/dvd and booted gparted live in it.
5> Resized the disk with gparted live so that it was set to 10240 MiB.
6> Used CloneVDI again (as above) to compact that resized vdi; and, this time, sent that clone to my external usb drive.
7> Deleted the vm I had made using the option to delete all files (that deleted the old vdi also when it happened).
8> Copied that final, resized and compacted vdi back to my local disk into the folder I had made for it inside "VirtualBox VMs."
9> Made another vm, the final one, the one I've been after - using that final, resized and compacted vdi for it's disk.
10> Booted my new vm host replica, "HostClone," and have been enjoying it ever since.

As far as I can tell it's fine and nothing wrong with it. If there are any problems I'm sure they will come out in the following days. I'm also sure that the way I arrived at my goal may not have been the most efficient or even best way - but I did it the best way I knew how, after the instruction/ input you guys and a couple fellas at Virtual Box forums gave me.

Thanks a whole, whole bunch guys. I'm glad you showed up for me.

Peace out!

Jake

---

