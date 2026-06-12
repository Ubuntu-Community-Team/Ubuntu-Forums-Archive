---
title: "USB Startup Disk Creator - an accident waiting to happen!"
date: 2009-10-20
forum: Testimonials &amp; Experiences
---

### Post by merlinblack on 2009-10-20
I've done some experimenting with this little utility and discovered that is has some seriously sharp pointy bits, ready to poke someone's eye out. 

The problem is with the "Format" button.  It looks innocent enough.  However unless you read the help (which is in-probable since this program is so simple) you are unlikely to know that:

a) Its not going to ask if you are sure you want to obliterate all the data on the USB drive.
and
b) Its going to format the WHOLE drive.  Not just that partition you have selected in the list box above.

Yes that's right.  Say you have a nice USB drive you have used previously for this sort of thing.  Its 250GB, with a little 2GB partition formated as FAT32, and the rest is another ext3 partition that you use for all sorts of stuff.

So you plug it, in.  See the partitions listed.  Select the first one (/dev/sdb1 or whatever), and hit format to zap that Debian install image, or the really old Ubuntu server install image you don't need any more.  TADA you've just toasted anything in the partition you did not select AS WELL.  The whole disk is now FAT32.:mad:  It didn't even ask for my password!

Welcome to the friendly, anyone can use, Ubuntu Linux.

---

### Post by 3rdalbum on 2009-10-20
> **merlinblack said:**
> I've done some experimenting with this little utility and discovered that is has some seriously sharp pointy bits, ready to poke someone's eye out. 

The problem is with the "Format" button.  It looks innocent enough.  However unless you read the help (which is in-probable since this program is so simple) you are unlikely to know that:

a) Its not going to ask if you are sure you want to obliterate all the data on the USB drive.
and
b) Its going to format the WHOLE drive.  Not just that partition you have selected in the list box above.

Yes that's right.  Say you have a nice USB drive you have used previously for this sort of thing.  Its 250GB, with a little 2GB partition formated as FAT32, and the rest is another ext3 partition that you use for all sorts of stuff.

So you plug it, in.  See the partitions listed.  Select the first one (/dev/sdb1 or whatever), and hit format to zap that Debian install image, or the really old Ubuntu server install image you don't need any more.  TADA you've just toasted anything in the partition you did not select AS WELL.  The whole disk is now FAT32.:mad:  It didn't even ask for my password!

Welcome to the friendly, anyone can use, Ubuntu Linux.

I haven't used it lately, but if what you're saying is true, then good point and well spotted. Please send me a link to the bug report you've raised, so I can keep track of it.

---

### Post by K.Mandla on 2009-10-20
> **3rdalbum said:**
> I haven't used it lately, but if what you're saying is true, then good point and well spotted. Please send me a link to the bug report you've raised, so I can keep track of it.
Agreed. File a bug report, and it will be fixed. Complaining here does ... almost nothing.

---

### Post by solwic on 2009-10-20
> **K.Mandla said:**
> Agreed. File a bug report, and it will be fixed. Complaining here does ... almost nothing.

Yeah, 'cause why would you want to make the community aware of a problem that could potentially wipe their whole drive?  Sheesh, man, what're you thinking?!?!

Seriously, file a bug report...but thanks for the heads up here.  Nobody reads those reports anyway; at least, not as much as they check this forum.  

:biggrin:

---

### Post by 3rdalbum on 2009-10-20
I agree, thanks for the heads-up.

---

### Post by merlinblack on 2009-10-21
Looks like I've been beaten to it:
[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/446891](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/446891)

I forgot to say originally that this was with Karmic beta.  However this quite possibly affects Jaunty too.

---

### Post by originalsynthesis on 2009-11-03
Actually, I just used this tool today, on the stable 9.10 release, and it wiped my whole flashdisk, which I was fine with, but apparently did not actually format it! The whole disk became invisible to my system, I happened to have a brand new computer built for a friend, so I stuck it in there, and xp noted the unformatted disk and asked me very nicely, "would you like to format this disk?", and handled it. 
   Don't get me wrong, I really dig my ubuntu, but that could have been a major pain in the ****, or another 12 bucks on a new drive maybe, if I didn't have another computer sitting around.
   Has anyone seen something like that happen? I forgot to mention first that this had a 9.04 startup partition, and a plain fat32 part on it already.

---

### Post by Tamlynmac on 2009-11-03
> K.Mandla
Agreed. File a bug report, and it will be fixed. Complaining here does ... almost nothing. 	

With that said, why do we even have a T&E section. The majority of threads in this section are often complaints? I agree with you that I doubt complaining here resolves much. IMHO, most of the flame wars and arguments in this section are a direct result of complaining. :-k

Just my $0.02

---

### Post by Bios Element on 2009-11-03
> **Tamlynmac said:**
> With that said, why do we even have a T&E section. The majority of threads in this section are often complaints? I agree with you that I doubt complaining here resolves much. IMHO, most of the flame wars and arguments in this section are a direct result of complaining. :-k

Just my $0.02

Probably because 1 outta every 50 posts is someone who actually posts a non-flame testimonial. >.<

---

### Post by Tamlynmac on 2009-11-03
> Bios Element
Probably because 1 outta every 50 posts is someone who actually posts a non-flame testimonial. >.< 	

Good numbers. :p

Unfortunately, your probably right. I don't think it's quite that high, but I'll bet you're close. Depending on the evaluation criteria. ;)

---

### Post by solwic on 2009-11-03
> **tamlynmac said:**
> with that said, why do we even have a t&e section. The majority of threads in this section are often complaints? I agree with you that i doubt complaining here resolves much. Imho, most of the flame wars and arguments in this section are a direct result of complaining. :-k

just my $0.02

+1

---

### Post by Seventh Reign on 2009-11-04
I dont see what the problem here is.  The USB Startup Disc Creator is for USB Flash/Pendrives, NOT USB HDD's.  It is supposed to delete & format the entire flash drive.  There is no bug its doing exactly what it needs to do to work correctly.

---

### Post by DrMilo on 2009-11-11
> **originalsynthesis said:**
> Actually, I just used this tool today, on the stable 9.10 release, and it wiped my whole flashdisk, which I was fine with, but apparently did not actually format it! The whole disk became invisible to my system, I happened to have a brand new computer built for a friend, so I stuck it in there, and xp noted the unformatted disk and asked me very nicely, "would you like to format this disk?", and handled it. 
   Don't get me wrong, I really dig my ubuntu, but that could have been a major pain in the ****, or another 12 bucks on a new drive maybe, if I didn't have another computer sitting around.
   Has anyone seen something like that happen? I forgot to mention first that this had a 9.04 startup partition, and a plain fat32 part on it already.

Just happened to me too on Koala Netbook Remix. It's not that it wiped my stick; it's that it wiped my stick and did nothing else as far as I can tell! I don't have another computer to work with right now but tomorrow I'll be able to plug this into a windows machine and see if that recognizes it. Yes I know that sticks fail but having it fail right after I hit format on an app is more than a little suspicious!

---

### Post by Dullstar on 2009-11-12
A viable alternative might be UNetBootin, although it has a tendancy to only work sometimes.  However, it can install to a usbdrive without formatting it.  I'll try doing it to a real hard drive as soon as I get a spare machine.  My brother should be letting me use one of the computers at any time, although he said if I want to use that one, he'll probably change some stuff.

---

### Post by running_rabbit07 on 2009-11-12
I personally grasped that before trying, but it is good for others to know who have not yet noticed.

---

### Post by running_rabbit07 on 2009-11-12
> **Dullstar said:**
> A viable alternative might be UNetBootin, although it has a tendancy to only work sometimes.  However, it can install to a usbdrive without formatting it.  I'll try doing it to a real hard drive as soon as I get a spare machine.  My brother should be letting me use one of the computers at any time, although he said if I want to use that one, he'll probably change some stuff.

The USB startup creator is used like a LiveCD with memory, so that you can do updates and store data.

---

### Post by DrMilo on 2009-11-12
> **DrMilo said:**
> Just happened to me too on Koala Netbook Remix. It's not that it wiped my stick; it's that it wiped my stick and did nothing else as far as I can tell! I don't have another computer to work with right now but tomorrow I'll be able to plug this into a windows machine and see if that recognizes it. Yes I know that sticks fail but having it fail right after I hit format on an app is more than a little suspicious!

Great it's not formatted for windows now, although windows knows that it's there. And as this computer is at my school I don't have the rights to format it.

So it would appear that Koala formats it so that Koala doesn't recognize it and it doesn't install anything!

How did this get into a stable release?

---

### Post by DrMilo on 2009-11-12
Now I got my stick formatted (in windows) and DID NOT choose the dreaded format option in usb creator. I clicked "make startup" and after it copied the files I have a blank box titled "Installing". No indication that it's doing anything for 10 minutes! System monitor says that it's sleeping!

About a half an hour in total now. I'm going to stop it and hope that it completed.

Well I have 45 minutes till my next class...

---

### Post by DrMilo on 2009-11-12
About a half an hour in total now. I'm going to stop it and hope that it completed.

---

### Post by running_rabbit07 on 2009-11-12
> **DrMilo said:**
> Great it's not formatted for windows now, although windows knows that it's there. And as this computer is at my school I don't have the rights to format it.

So it would appear that Koala formats it so that Koala doesn't recognize it and it doesn't install anything!

How did this get into a stable release?

Maybe your school does set their BIOS to boot from USBs.

---

### Post by Tirek on 2009-11-12
Hi everyone. I regret that my first post has to be about such an issue, but this is a *major* problem, I think.

Like the original poster, I wanted to install Ubuntu Karmic using an external hard drive - two NTFS partitions, one 50 gig, the other just shy of 950 gig, with 500 gb worth of backups which I sincerely hope I'll be able to recover (currently running a utility called "GetDataBack for NTFS". As you can imagine, I didn't bother to research all that much - so if anyone has recommendations, I'll be grateful)

I didn't know whether it will work or not (UNetBootin refuses to install to USB hard drives, at least for me), but when I saw that it correctly detected and identified both partitions IN ADDITION to the whole device entry, and that they were individually selectable, I was rather sure that the simplest explanation (that is, you can choose which partition to format and use for install) was the correct one. I'm pretty certain that most people would find this conclusion reasonable, especially those who are supposed to be the target audience for this fairly popular Linux distro, which is focused on usability, simplicity and intuitiveness.

Anyway, I pressed the "format" button and I don't remember even having ANY warning pop up (there was an error, but frankly, I didn't remember to write it down). Then the USB creator window darkened and the hard drive started chugging away. It wasn't until I found a single 1000 GB partition listed in the "Places" menu that the realization hit me.

> I dont see what the problem here is. The USB Startup Disc Creator is for USB Flash/Pendrives, NOT USB HDD's. It is supposed to delete & format the entire flash drive. There is no bug its doing exactly what it needs to do to work correctly.

Which it utterly fails to communicate to the user. It looks simple enough that you don't bother to read help; it sets up expectations about it's behaviour which turn out to be tragically wrong and it fails to inform the user about what will happen. But yes, it may not, strictly speaking, be a bug. :rolleyes:

Also, I know of no technical reason why a partition on an external hard drive could not function as a live USB (if there is, I'd like to know it).

I may have come across as harsh, but to be honest, I'm holding myself back, as this has really strained my nerves... Still, I want to end this on a more positive note - Karmic has been a delight to use, otherwise.

---

### Post by DrMilo on 2009-11-12
> **DrMilo said:**
> About a half an hour in total now. I'm going to stop it and hope that it completed.

Nope, didn't complete. All of the folders and files appear to be on the stick but it will not boot.

Why should it take 30-40 minutes to do anything on a 1 gig USB stick I have no idea.

I opened make startup disk and had it look at the stick again. It tells me there isn't enough space, so I clicked on "open" and it did nothing. You'd think that I'd get an error message, progress bar etc. but nothing.

---

### Post by running_rabbit07 on 2009-11-12
> **DrMilo said:**
> Nope, didn't complete. All of the folders and files appear to be on the stick but it will not boot.

Why should it take 30-40 minutes to do anything on a 1 gig USB stick I have no idea.

I opened make startup disk and had it look at the stick again. It tells me there isn't enough space, so I clicked on "open" and it did nothing. You'd think that I'd get an error message, progress bar etc. but nothing.

You're the doctor, fix it.

---

### Post by DrMilo on 2009-11-12
> **running_rabbit07 said:**
> You're the doctor, fix it.

That's helpful, not to mention courteous.

---

### Post by PRC09 on 2009-11-12
I dont know what all the excitement is about....The very first line of the app says to TRY or install *FROM* a start up disk not *Install* to a start up disk.....or am I missing something.I have used it just fine for what it was designed for.To make a bootable copy of the live CD on a usb drive....

---

### Post by running_rabbit07 on 2009-11-12
> **DrMilo said:**
> That's helpful, not to mention courteous.

Well, you were talking to yourself in a web forum. If you want help, start a thread in the proper place.

---

### Post by Tirek on 2009-11-13
> **PRC09 said:**
> I dont know what all the excitement is about....The very first line of the app says to TRY or install *FROM* a start up disk not *Install* to a start up disk.....or am I missing something.I have used it just fine for what it was designed for.To make a bootable copy of the live CD on a usb drive....
 
If my post gave the impression that I wanted to *install* Ubuntu on the drive, it was unintentional. What I wanted to do was *make a bootable copy of the live CD on an empty partition on an external usb hard drive.* If this is technically impossible, then I accept the blame for not knowing that; but it doesn't change the fact that the program has a serious usability issue (or several, depending on how you look at it):
 
-it does not communicate clearly and up-front that it requires the use of the whole physical drive and not just a single partition.
-it lists individual partitions *along* with the actual physical drive and lets the user select them individually (I presume the list itself is meant for choosing among different drives if more than one is plugged in?)
-it fails to inform the user about what it's going to do. A simple warning would prevent most if not all accidents of the kind I (and others) have experienced. Maybe something like "*You are about to format the entire physical drive, removing ALL partitions, thus destroying ALL data in ALL the partitions in the device. Are you sure you want to continue?*". It may be annoying and jarring and I know everyone hates popup messages but surely in THIS case it would be worth it?
 
When there is potential for data loss (I've already successfully recovered some data, I hope for the best), I'd think even a usability issue such as this one should be considered serious. Frankly I'm a bit surprised at the "I don't know what the excitement is about" comment. Have I completely lost perspective? Have several of my colleagues also lost perspective? They all agree that this is unacceptable and none of us is new to computers.
I wonder what the response would be if it were about some other program on some other forum. I've seen people go completely berserk over much stupider things.

---

### Post by PRC09 on 2009-11-13
My apologies on the excitement comment,I mis-read the partition part.I was having a hard time reasoning why anyone would want to use a huge usb drive (not partition) to do what I had assumed was designed for a thumb drive..
I now see where the excitement could happen.....

---

### Post by merlinblack on 2009-11-14
Once I had calmed down from having my whole drive erased, I found that using the 'Disk Utility' it was very easy to setup a 1 gig FAT partition, and then the rest as ext3 in another partition.  Then the USB Startup Creator, worked fine, and installed into the partition I had selected.

I think the Format button should be either removed, or changed to start the Disk Utility.  At the very least it should say after clicking: "About to completely wipe device bla", Ok, Cancel.

---

### Post by wilee-nilee on 2009-11-14
> **merlinblack said:**
> I've done some experimenting with this little utility and discovered that is has some seriously sharp pointy bits, ready to poke someone's eye out. 

The problem is with the "Format" button.  It looks innocent enough.  However unless you read the help (which is in-probable since this program is so simple) you are unlikely to know that:

a) Its not going to ask if you are sure you want to obliterate all the data on the USB drive.
and
b) Its going to format the WHOLE drive.  Not just that partition you have selected in the list box above.

Yes that's right.  Say you have a nice USB drive you have used previously for this sort of thing.  Its 250GB, with a little 2GB partition formated as FAT32, and the rest is another ext3 partition that you use for all sorts of stuff.

So you plug it, in.  See the partitions listed.  Select the first one (/dev/sdb1 or whatever), and hit format to zap that Debian install image, or the really old Ubuntu server install image you don't need any more.  TADA you've just toasted anything in the partition you did not select AS WELL.  The whole disk is now FAT32.:mad:  It didn't even ask for my password!

Welcome to the friendly, anyone can use, Ubuntu Linux.

If it saya format you have to ask yourself what does this mean, in windows when you format it warns you, I agree it should in Linux.

---

### Post by wilee-nilee on 2009-11-14
> **merlinblack said:**
> Once I had calmed down from having my whole drive erased, I found that using the 'Disk Utility' it was very easy to setup a 1 gig FAT partition, and then the rest as ext3 in another partition.  Then the USB Startup Creator, worked fine, and installed into the partition I had selected.

I think the Format button should be either removed, or changed to start the Disk Utility.  At the very least it should say after clicking: "About to completely wipe device bla", Ok, Cancel.

Your better off using gparted for formatting or any of the other numerous open source variations of formatting partitions.

---

### Post by longtom on 2009-11-14
> **DrMilo said:**
> That's helpful, not to mention courteous.

You will find that this particular user is full of wisdom like that.  He is an ardent fighter for Ubuntu to the point of being fanatical.  As we all know, that can make you blind at times and rude to anybody who doesn't share this fanaticism.
I wouldn't get to worked up about people like that.

Coming back to the issue you raise:  

It is an important one if we accept the fact that Koala is a de facto test ground for the next LTS.  Have you had the opportunity to file a bug report or add to an existing one yet?  I reckon this would be something the devs want to look at.

---

### Post by John Bean on 2009-11-14
> **wilee-nilee said:**
> If it saya format you have to ask yourself what does this mean
Sure you do. But having asked myself I'd never come to the conclusion that "format" means "remove the partition table" - which is what it does in this case.

Not only is it dangerous and carried out without confirmation or warning, it's not even accurately described in the first place.

---

### Post by merlinblack on 2009-11-14
> **wilee-nilee said:**
> Your better off using gparted for formatting or any of the other numerous open source variations of formatting partitions.

I don't know of any technical advantage, so I guess it depends on personal preference.  I found the 'Disk Utility' adequate for this job, and it's installed by default.  Had I had gparted installed, I probably would have used that, since I'm more familiar with it.

They are all a breeze compared to 'disklabel' on DEC Unix v4!!! :p

---

### Post by Tirek on 2009-11-14
I agree that the easiest way to solve this problem would be to remove the formatting feature from the program altogether, pointing the user towards using GParted instead. Getting rid of the partition/device list and having a clearly labeled link or a button to launch GParted, for instance. This could be a temporary solution at least, until a more elegant solution can be found.

---

### Post by running_rabbit07 on 2009-11-14
> **longtom said:**
> You will find that this particular user is full of wisdom like that.  He is an ardent fighter for Ubuntu to the point of being fanatical.  As we all know, that can make you blind at times and rude to anybody who doesn't share this fanaticism.
I wouldn't get to worked up about people like that.

If I am a fanatic, does that make you a troll? Don't judge me. Just by counting beans it is obvious who actually posts in the help threads.

> **longtom said:**
> Coming back to the issue you raise:  

It is an important one if we accept the fact that Koala is a de facto test ground for the next LTS.  Have you had the opportunity to file a bug report or add to an existing one yet?  I reckon this would be something the devs want to look at.

Thanks, I wonder how my response makes me a fanatic. Last I looked this is a testimonial thread, not a help request.

---

### Post by wilee-nilee on 2009-11-14
> **John Bean said:**
> Sure you do. But having asked myself I'd never come to the conclusion that "format" means "remove the partition table" - which is what it does in this case.

Not only is it dangerous and carried out without confirmation or warning, it's not even accurately described in the first place.

You cherry pick my only two sentences, and leave out my agreement with the OP. 

Look it is Linux you have to watch your step always with any changes, your given the power to bork your computer so you don't do anything unless you know what your doing.

Also a external USB HD used as a OS is not the best of ideas, it will run slow, the transfer speed is not good. Also formatting it to a Ext that can only be read by a Linux program is not a good Idea either, even if that has some advantages as far as file placement. The only time this is a good idea is if the HD is solid state, a flash like a thumb or pen or card is.

Lets say you meet a nice person of the gender of your choice, and you have music and movies...etc that you want to share with them you go to their pad, and all they have is a Windows or Apple set up the HD is now a door stop.

There is plenty of documentation on how this program works, and even when you format on a windows computer it does the same thing it deletes the content.

Complaining about doing something that common sense says gee I better make sure I know what I am doing is nonsensical. We all can probably name a similar circumstance that has happened to us. That is how your learn, about 2 minutes on Google looking up formatting and Linux or even computers would have given the answer to this. 

It is a computer it can't hold your hand, and tell you everything will be better like your mommy.

I also don't believe the OP description if you had the skills to have partitioned this external then you would not have used the USB creator to rewrite a partition already there. There is no mention of the size of the device except in a as if description fat32 can only write as a 32 gig partition to be functional.

The OP doesn't say that they had a partitioned HD and and that choosing a particular partition to format, they give a description of a what if situation. Has anybody taken their partitioned USB and tried this to see if this actually happens.

---

### Post by John Bean on 2009-11-14
> **wilee-nilee said:**
> You cherry pick my only two sentences, and leave out my agreement with the OP. 
Not cherry-picking at all, unless you regard any kind of selective quoting as cherry-picking.

I replied only to challenge your implication that people were getting bitten because they hadn't considered the meaning of "format" in this context, so that's the part I quoted. I had no comment to make about the rest of your post.

Simple as that.

---

### Post by wilee-nilee on 2009-11-14
> **John Bean said:**
> Not cherry-picking at all, unless you regard any kind of selective quoting as cherry-picking.

I replied only to challenge your implication that people were getting bitten because they hadn't considered the meaning of "format" in this context, so that's the part I quoted. I had no comment to make about the rest of your post.

Simple as that.

Kind of hard to admit your mistakes now isn't it, just as the OP should have done. We will all respect you more when you admit this sort of thing it makes you seem more human.

---

### Post by Tirek on 2009-11-14
> **wilee-nilee said:**
> You cherry pick my only two sentences, and leave out my agreement with the OP. 

Look it is Linux you have to watch your step always with any changes, your given the power to bork your computer so you don't do anything unless you know what your doing.

Also a external USB HD used as a OS is not the best of ideas, it will run slow, the transfer speed is not good. Also formatting it to a Ext that can only be read by a Linux program is not a good Idea either, even if that has some advantages as far as file placement. 

Lets say you meet a nice person of the gender of your choice, and you have music and movies...etc that you want to share with them you go to their pad, and all they have is a windows or Apple set up the HD is now a door stop.

There is plenty of documentation on how this program works, and even when you format on a windows computer it does the same thing it deletes the content.

Complaining about doing something that common sense says gee I better make sure I know what I am doing is nonsensical. We all can probably name a similar circumstance that has happened to us. That is how your learn, about 2 minutes on Google looking up formatting and Linux or even computers would have given the answer to this. 

It is a computer it can't hold your hand, and tell you everything will be better like your mommy.

This is about Ubuntu and a Ubuntu-specific tool. One of the goals of Ubuntu is supposed to be friendliness, as I understand. "Linux for human beings". So I don't think you get to dodge the issue this way.

Also - I can't speak for everyone, but at least in my case, you misunderstood the intention. I didn't want to *install* to the external HDD. I just happened to not have any USB sticks lying around for making live USBs and wanted to use my external HDD instead. The smaller empty partition I had put on it was kept empty and was meant for exactly this sort of temporary purposes.

There may well be a lot of documentation for this program, but this shouldn't absolve it from having a misleading, deceptively simple UI. But then again, I've already explained what I think the problem is in one of my previous posts in this topic. I agree that expecting formatting to not delete data would be ridiculous - but what about not expecting it to wipe the whole partition table?

---

### Post by kelvin spratt on 2009-11-14
check the usb drive for files and back them up if needed, all contents will be destroyed. 
This taken from the Ubutu Documentation its self explanatory or it is to me its not referring to a USB H/Drive.

---

### Post by cariboo on 2009-11-14
I just used the tool for what it was created for, to create a thumb drive I can use to boot other computers with.

I just had a look at the documentation after the fact, and it does give you the impression that you can use any usb external drive to create a Startup disk. This is unfortunate, as that is not the purpose of the utility, it is meant for a thumb drive, and not a hard drive. 

It's time to create another bug report.

---

### Post by wilee-nilee on 2009-11-14
> **Tirek said:**
> This is about Ubuntu and a Ubuntu-specific tool. One of the goals of Ubuntu is supposed to be friendliness, as I understand. "Linux for human beings". So I don't think you get to dodge the issue this way.

Also - I can't speak for everyone, but at least in my case, you misunderstood the intention. I didn't want to *install* to the external HDD. I just happened to not have any USB sticks lying around for making live USBs and wanted to use my external HDD instead. The smaller empty partition I had put on it was kept empty and was meant for exactly this sort of temporary purposes.

There may well be a lot of documentation for this program, but this shouldn't absolve it from having a misleading, deceptively simple UI. But then again, I've already explained what I think the problem is in one of my previous posts in this topic. I agree that expecting formatting to not delete data would be ridiculous - but what about not expecting it to wipe the whole partition table?

In my very post I said knowing what formatting does would be helpful then I said it would be nice if there was a warning so I am in agreement with this basic consensus. But in the end it is a user error situation by not understanding what the program does.

None of us want a person to lose data, or have any problems, so that is why you see people post that back up your stuff and understand what your doing when you do it. I personally after using the USB creator and unetbootin probably 50 times never let them format, gparted is a better partitioning tool that does much more. 

If you got a warning on every program every time then your day would be awfully slow. On my W7 OS the 1st thing I did was turn off the are you sure you want to do this popup because I am experienced user and know what I am doing, and I will not blame the program or OS for my ineptitude. 

Now the honorable mod cariboo907 considers this as a bug I would disagree on this the program does what it is supposed to, you just have to know what it does. No operating system is user friendly, it is a computer being friendly is a human or animal attribute and achieved through reasoning, a computer does not reason ;)

---

### Post by Tirek on 2009-11-14
> **wilee-nilee said:**
> In my very post I said knowing what formatting does would be helpful then I said it would be nice if there was a warning so I am in agreement with this basic consensus. But in the end it is a user error situation by not understanding what the program does.

None of us want a person to lose data, or have any problems, so that is why you see people post that back up your stuff and understand what your doing when you do it. I personally after using the USB creator and unetbootin probably 50 times never let them format, gparted is a better partitioning tool that does much more. 

If you got a warning on every program every time then your day would be awfully slow. On my W7 OS the 1st thing I did was turn off the are you sure you want to do this popup because I am experienced user and know what I am doing, and I will not blame the program or OS for my ineptitude. 

Now the honorable mod cariboo907 considers this as a bug I would disagree on this the program does what it is supposed to, you just have to know what it does. No operating system is user friendly, it is a computer being friendly is a human or animal attribute and achieved through reasoning, a computer does not reason ;)

Apparently I've misunderstood you then - I'm sorry.

However, I still don't agree that this is purely user error - my decision was brash, but not entirely unreasonable. What I'm saying is that I can easily imagine many people doing the wrong thing. To me, it looks like the kind of situation where semi-power-users fare the worst, as the program looks simple enough that reading the manual seems pointless, whereas it's actual behavior is very unintuitive. It simply shouldn't list individual partitions, nor allow to select them. I'd call this a "usability bug".

BTW, I also dislike throwing the term "user friendliness" around too much and yes, it's kinda hard to define, but there definitely is such a thing as a more or less "user-friendly" system... Not in the sense of it being able to reason or not being dumb, of course. It's about it being dumb in a very consistent, predictable fashion ;)

---

### Post by merlinblack on 2009-11-14
I originally posted a hypothetical scenario, but its pretty much what happened to me.  It seems my experience got the better of me in this case.  I know the difference between formatting, and partitioning, this program does not make the distinction.  I was as pissed off at myself as much as at the program.

The program should do the least surprising thing.  Re-partitioning the device, when you click a button that says 'Format', which is under a list of partitions (one of which you have selected) is not what you would expect to happen, experienced user or not.

Even changing the button caption to 'Format Device' would be a improvement.  Its not that the program does not do enough 'hand holding'.  The problem is that the UI does not adequately convey the assumptions of its design, that assumption being that you want to use the whole device.

Having the slight annoyance of a "Are you sure?" question in this case is a minor inconvenience compared to possible irretrievable data loss.

I agree that calling this a 'Bug' is a stretch.  It is a design issue.

---

### Post by solwic on 2009-11-14
> **merlinblack said:**
> I agree that calling this a 'Bug' is a stretch.  It is a design issue.

And a very poor one at that.  I agree that the program should be more clear about what it's doing, although I must also admit that I assumed it would format the whole device, rather than use a single partition on that device.

---

### Post by DrMilo on 2009-11-15
> **longtom said:**
> You will find that this particular user is full of wisdom like that.  He is an ardent fighter for Ubuntu to the point of being fanatical.  As we all know, that can make you blind at times and rude to anybody who doesn't share this fanaticism.
I wouldn't get to worked up about people like that.

Coming back to the issue you raise:  

It is an important one if we accept the fact that Koala is a de facto test ground for the next LTS.  Have you had the opportunity to file a bug report or add to an existing one yet?  I reckon this would be something the devs want to look at.

I believe that this is already reported.

---

### Post by cariboo on 2009-11-16
I consider the documentation wrong, it gives the user the impression that they can use any attached usb drive, including hard drives and create a bootable startup device, when in fact it is only meant for thumb drives.

---

### Post by running_rabbit07 on 2009-11-16
I have tried that application a few times. It finished what it was doing in a decent amount of time, but when I plugged it into a system to which the BIOS accepts bootable USBs, it didn't work.

That bites being I wanted to use it for Lucid. I'll just have to get a second HDD for that.

---

### Post by nema.arpit on 2009-11-16
@[running_rabbit07]("http://ubuntuforums.org/member.php?u=840719")
Try the syslinux method : works flawlessly and best of all u can actually save your partitions(I think)

---

### Post by datelus on 2009-11-16
Please tell me there is a way to get all that data back.
Ive done the same thing, by pressing the button, and all it showed was the copy from dvd progress window.
All my life was in that disc, so i hope there is a way to get some data back. Thanks.

---

### Post by Cyr1dian on 2009-11-22
> **Tirek said:**
> Hi everyone. I regret that my first post has to be about such an issue, but this is a *major* problem, I think.

Like the original poster, I wanted to install Ubuntu Karmic using an external hard drive - two NTFS partitions, one 50 gig, the other just shy of 950 gig, with 500 gb worth of backups which I sincerely hope I'll be able to recover (currently running a utility called "GetDataBack for NTFS". As you can imagine, I didn't bother to research all that much - so if anyone has recommendations, I'll be grateful)

I didn't know whether it will work or not (UNetBootin refuses to install to USB hard drives, at least for me), but when I saw that it correctly detected and identified both partitions IN ADDITION to the whole device entry, and that they were individually selectable, I was rather sure that the simplest explanation (that is, you can choose which partition to format and use for install) was the correct one. I'm pretty certain that most people would find this conclusion reasonable, especially those who are supposed to be the target audience for this fairly popular Linux distro, which is focused on usability, simplicity and intuitiveness.

Anyway, I pressed the "format" button and I don't remember even having ANY warning pop up (there was an error, but frankly, I didn't remember to write it down). Then the USB creator window darkened and the hard drive started chugging away. It wasn't until I found a single 1000 GB partition listed in the "Places" menu that the realization hit me.



Which it utterly fails to communicate to the user. It looks simple enough that you don't bother to read help; it sets up expectations about it's behaviour which turn out to be tragically wrong and it fails to inform the user about what will happen. But yes, it may not, strictly speaking, be a bug. :rolleyes:

Also, I know of no technical reason why a partition on an external hard drive could not function as a live USB (if there is, I'd like to know it).

I may have come across as harsh, but to be honest, I'm holding myself back, as this has really strained my nerves... Still, I want to end this on a more positive note - Karmic has been a delight to use, otherwise.

I had almost the exact same problem! I am now desperately trying to recover a tonne of lost data. The thing is called "USB Startup DISK created" ffs, not Thumbdrive startup creator or something. Deleting all partitions of a drive UNPROMPTED is most definitely a HUGE design flaw! I'm a dev myself and this is just not acceptable.

---

