---
title: "linux-NEVER again!!"
date: 2007-04-26
forum: Testimonials &amp; Experiences
---

### Post by w4sef on 2007-04-26
Well folks.....this is a sad tale.. first off let me say I have been using and working with computers since the early 80s so i am no novice. I decided to take the plunge and install linux to see how I would like it. So, I installed a third hard drive on my machine.. made it the H drive.. then proceeded to install ubunta on this drive as I did not wish to take a chance on screwing up the C drive..hahahah... after the install, i rebooted-only to find that I got an error 21 and no grub menu....so, I decided i would reintall Linux. Same thing. So, I disconnected the third drive and rebooted to C.   NO GO...this crap screwed up the MBR on my C drive. ARGGG...I tried everything I could to restore. No go...so, like an idiot, I put this third drive with Linux on my wifes machine..when I booted it immediatly grabbed the C drive and screwed it up too!!! Fortunatley, my wife did not get upset as she knew i was already upset enough as it was. This had left a sour taste in my mouth about Linux. i was veryyyyy disappointed as I have heard great things about Linux and I detest Windoze-UGH.
I sure miss the DOS days....Thanks for reading this.

Steve Fritts

---

### Post by Cypher on 2007-04-26
I'm sorry to hear that your experience was Linux wasn't as smooth as others, but let me first get it out of the way that working with computers for 20+ years with no fore-knowledge of Linux doesn't mean anything.

Rather than install Linux and mess up your existing OS installations, you should have used the LiveCD, booted it and played around with Linux. If you were comfortable and wanted to continue, there are are countless guides on the proper installation method.

Also, if you had come to us before you began the installation, someone here could've probably told you the way to get things installed and working properly.

If you're willing to give Ubuntu (Linux) another try, let us know and we'd be happy to get things back in working order..

---

### Post by ashz on 2007-04-26
go into windows recovery cd,

console

type fixmbr

tada all fixed no need to reinstall everything, but u should know that since u have been using pc's since the 80's, oh btw if u have not used something before dont expect to just jump into the driving seat and be competent in the operation of a os/program straight away just because u have some experience in computers, i will have been using pc's for 20 years this year (since i was 8 and wrote my first program in basic) but i didnt start using linux till last november, and im still a newbie!!!!

cheers
ash

---

### Post by seetho on 2007-04-26
Since your system is already screwed, you'll do no more harm in trying the install from fresh.  Everybody has had (and will have) their fair share of frustrations.  All we can do is try again.  Good luck next time.  Come back and tell us how much you love Ubuntu/Linux after you succeed!

---

### Post by deadgobby on 2007-04-26
I am sorry to hear about that. However, you'll need to read up on dual booting and HD partitioning before going into such a task. Or even ask. Just because you been into computers for over 20 years you cannot assume you know what you are doing. Linux is not windows and need to throw out the windows paradigm right in the trash can.  
 Now did you correct your problem or do you need a helping hand? We are here to help and be more than happy to help you get on the linux path.
Gobby

---

### Post by handy on 2007-04-26
One way you can fix your master boot record is to boot with a floppy or CD that has the dos fdisk command on it, & at the command prompt type:

***fdisk /mbr***

***[Edit:] Wow, 3 replies while i was typing...  That kind of support is hard to come by! :-D***

---

### Post by alexjhill on 2007-04-26
Why didn't you just disconnect your other drives before installing ?  < room falls silent>  "Oh YEA"

Shame tho - but i'd go down the fixMbr route as advised. Im a newbie with Ubuntu and i love it!  can't say I had problems with partitioning or dual booting - user error? :lolflag:

---

### Post by tehbeermang on 2007-04-26
I used a mac, then used Win32 starting with 98. I've taken an intro to unix class at the community college, played with a couple liveCDs and the Fedora systems in the computer lab. 

I had no problems partitioning the drive and dual booting.

I followed this tutorial:
[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

Easy.

---

### Post by DarthWHO on 2007-04-26
If anything, I think the responses here should give you an idea on the kind of community you would be getting yourself into. I love that noone jumped on this post and started doing anything other than trying to assist you.

Like you, I've been in computers for nearly 20 years. Have recently switched to Linux as my primary workstation and haven't turned back. The main reason being that whenever I encounter a problem, I always find an answer here. 9.9/10, users have experienced the same errors/issues and have a solution posted.

As stated already, the MBR is an easy fix with fixmbr.

---

### Post by Death_Sargent on 2007-04-26
1 did you make sure to put grub on the correct hard drive?

2 have you checked for root kit viruses recently or at all (avg will do this for you) .

If you want your windows back without reinstalling entirely i recomend grub anyway becuase it can easily be configured to boot any OS.

Also if your such a genious then tell me why you used windows to format the drive you where installing linux on. sounds as if grub is set to install on the hda drive however if all you have is c,d,e,f,g,h then you should have made sure to install on the hdf drive.

My dad has been working with computers since he had to program with punch cards. He started using windows back when 1.0 came out and he was still lost in linux. 

Before you can declare yourself a computer genious you should take the time to learn more than one OS: 
I trianed myself in windwos, linux, and macos; and i can still say when it comes to computers im still pretty green around the gills. 

Windows boot loader does not want to go down without a fight after XP and especially vista (install twice to kill the bugger). Using more than one hard drive for operating systems on a non RAID system is asking for confusion and data loss. 

So before you go blamming linux look through your procedure becuase I will bet there was something you messed up or a peice of malwar that is messing up your opperations.

---

### Post by wieman01 on 2007-04-26
Format MBR using Windows 98 boot CD if you don't happen to have a DOS floppy as suggested. Kind of reminds me of the eighties and the good old DOS days.

---

### Post by JerseyShoreComputer on 2007-04-26
I go back over 20 years too in computers back to Apple ][ and DOS 3.3... No matter what, even Windows you can have problems. Don't let this discourage you. I've tried the dual boot thing before with success (XP and Edgy)... The suggestions presented by the comunity are good ones - give them a shot. Try the Live CD and re-install.... Give it another try before giving up.

---

### Post by naughtywill on 2007-04-26
Yea sorry about your frustration. I am no computer expert by any stretch, but I have been around the block a few times and I like to think I am much better than the average Joe six pack. I found this Ubuntu a god send and have had very,very little trouble making the transition. Like what Cypher said, the LIVE boot is the way to go until your comfortable with it. Hope you come back and see how much better Linux really is over that cut rate garbage that comes out of Redmond. 

Ps. Like was said before the community support here is freaking just awesome. That is one reason I am now a Linux only user. Try getting this out of some d*ckhead technical support from India.

---

### Post by az on 2007-04-26
> **w4sef said:**
> Well folks.....this is a sad tale.. first off let me say I have been using and working with computers since the early 80s so i am no novice. I decided to take the plunge and install linux to see how I would like it. So, I installed a third hard drive on my machine.. made it the H drive.. then proceeded to install ubunta on this drive as I did not wish to take a chance on screwing up the C drive..hahahah... after the install, i rebooted-only to find that I got an error 21 and no grub menu....

Grub Error 21 means that your motherboard has a bug.  Grub needs to know where your files are and it can only get that information from the BIOS.  In this case, your bios is giving it bad information and ther is no way for the OS to work around that, since it has no way of knowing that the motherboard is buggy.

You need to adjust the device map for grub by hand.
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by Cypher on 2007-04-26
> **naughtywill said:**
> That is one reason I am now a Linux only user. Try getting this out of some d*ckhead technical support from India.
I'm with you all the way, until the last remark. Being an Indian-American I don't really think there is a need for this..

Level 1 technical support (the one MOST people get when they dial the 800 number) is usually manned by people who are best at answer the phone, taking a few keywords and searching for the answer in a database. Only the Level 2 and above tech support people are knowledgeable enough to fix issues without relying on canned database answers. 

So I'd appreciate a refrain on random remarks..

---

### Post by chili555 on 2007-04-26
I doubt there is anything you have done that can't be fixed. Very basically, you will fix the master boot record, so Windows boots, and then reinstall grub so you regain the menu that allows you to select between Windows and Ubuntu. The only trick is installing grub so it selects the right drive for the right operating system. All of this is do-able. It may take some trial and error.

Some of us grey beards here have made the same mistake. I made a little mistake and had to reinstall grub on this machine just last week. It boots fine now.

When you got your first bicycle and fell and skinned your knee, did you say, 'Bicycle-NEVER again'? Or did you pick yourself up and try again, gaining knowledge and confidence from both successes and failures? I think the latter.

---

### Post by aos101 on 2007-04-26
> **Death_Sargent said:**
> So before you go blamming linux look through your procedure becuase I will bet there was something you messed up or a peice of malwar that is messing up your opperations.
I really can't see how a piece of Windows malware could cause Grub to give an error when Windows was never run after Grub was installed.  Windows malware can do a lot of things, but I'd be really impressed by any that could mess up Grub without Windows ever being booted (after Grub had been installed).

---

### Post by Jose Catre-Vandis on 2007-04-26
> **Cypher said:**
> I'm with you all the way, until the last remark. Being an Indian-American I don't really think there is a need for this..

Level 1 technical support (the one MOST people get when they dial the 800 number) is usually manned by people who are best at answer the phone, taking a few keywords and searching for the answer in a database. Only the Level 2 and above tech support people are knowledgeable enough to fix issues without relying on canned database answers. 

So I'd appreciate a refrain on random remarks..

I quite agree. Although he/she could have got away with it if the last two words had been left off!
There is no room for even unintentional racial remarks on my favourite forum.

---

### Post by NullHead on 2007-04-26
I did the same thing ... only on my Dad's computer.

---

### Post by w4sef on 2007-04-26
First off......thank you ALL with the exception of Death Sargent for being so nice with your replies. Yes, I played with the Live Cd for about a week before making the plunge in to installing Linux. NO I am NOT an expert on Linux and never said I was. Yes, I did the Fix MBR trick-no luck. And yes, I checked for viruses before i started doing the install. I used AntiVir which I find is better than anything I have used-even better than E trust which I thought was the best ever until I tried AntiVir. They have a Linux version also!

I agree-I should have unhooked the other drives and just installed Linux to a single drive that would not affect the others.

Again, thank you all for the kind replies and advice. I may try this agian someday-with all of this advice in mind. I know Linux is superior to Windows-I HATE Windows and have every since I left DOS. I was probably the last person in the world to install Windows 3.1 :) 

Steve Fritts

---

### Post by naughtywill on 2007-04-26
> **Cypher said:**
> I'm with you all the way, until the last remark. Being an Indian-American I don't really think there is a need for this..

Level 1 technical support (the one MOST people get when they dial the 800 number) is usually manned by people who are best at answer the phone, taking a few keywords and searching for the answer in a database. Only the Level 2 and above tech support people are knowledgeable enough to fix issues without relying on canned database answers. 

So I'd appreciate a refrain on random remarks.. I apologise. I did not mean to insult the East Indians as a whole and I should have phrased that better. I was referring to the tech support,in my case Dell. I'm sorry I did not mean to offend you.

---

### Post by Tomosaur on 2007-04-26
> **az said:**
> Grub Error 21 means that your motherboard has a bug.  Grub needs to know where your files are and it can only get that information from the BIOS.  In this case, your bios is giving it bad information and ther is no way for the OS to work around that, since it has no way of knowing that the motherboard is buggy.

You need to adjust the device map for grub by hand.
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

Uhh...no, Error 21 means 'disk not found', it doesn't mean the motherboard has a bug, It is possible that yes, a problem with the mobo is causing it, but as far as Grub is concerned, it just can't see the disk. It's a fairly common error message when using multiple hard drives (not that the error is common, it's just that when it occurs, Error 21 is what it usually is), from what I've seen.

To the OP - the MBR only kicks in for  hard disk which holds the primary active partition, which is why Grub installed itself to the MBR on C. You should have made your H drive the master with the active partition being on that disk, to ensure that Grub installed correctly. It's not obviously stated anywhere, but it seems like common sense to some. Anyway - you have a variety of options.

1) Try again, set your H drive to be the master (btw, Linux doesn't use this lettering system. Different drives are viewed as branches off the main filesystem tree, which ultimately goes all the way down to 'root'.), and make sure the primary active partition is on that drive. Set C as a slave, and reinstall Linux to the H drive. If all goes well, you should have Linux and Windows both in the boot menu.

2) Restore windows' bootloader. You can do this using the Windows recovery CD or using fdisk on a floppy.

3) Find an alternative bootloader, such as GAG. This should recognise Windows and allow you to boot again. If you can't restore Windows' bootloader, you may need to just forget about it and use a different bootloader.

---

### Post by Calash on 2007-04-26
Hmm...FixMBR did not work....

Are you sure your dive order is right?  Meaning that Drive 0 is the one you ran FixMBR on.

Another option would be to boot into the Windows XP boot disk, get to the repair console (It is different if it is SPI or 2) and type FixBoot, then FixMBR

Using both I was able to get back to the XP boot loader fairly easily.



This is assuming that the Windows partition is still intact and working, but it is worth the 5 minutes to try :)


I know how you feel, I clung to 3.1 for a good year after it was a dead OS.  Even setup 95 to use Program Manager.   After you spend some time in any OS you get the hang of it.  Ubuntu is no exception.  Combing from a Windows tech world I found it difficult, but worth the effort.

---

### Post by w4sef on 2007-04-26
PostScript to Death Sargent:

After reading your comments again I sense you are very young. Also you might want to use a spell checker....

Harsh comments like yours do not help the situation. I will take everyones advice and reinstall Linux again someday after I get everything restored on mine and my wifes computers.

 I know that Linux is very popular now. My nephew loves it but he was unable to help me fix the problem I had. Since I could not get on line at home due to no computer op system, I had to wait until I got back to work to log in here.

Again thanks to all that offered the advice.

Steve Fritts
Philadelphia, TN.

---

### Post by Duck2006 on 2007-04-26
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Download and give this a go

---

### Post by lepz on 2007-04-26
> **w4sef said:**
> First off......thank you ALL with the exception of Death Sargent for being so nice with your replies. Yes, I played with the Live Cd for about a week before making the plunge in to installing Linux. NO I am NOT an expert on Linux and never said I was. Yes, I did the Fix MBR trick-no luck. And yes, I checked for viruses before i started doing the install. I used AntiVir which I find is better than anything I have used-even better than E trust which I thought was the best ever until I tried AntiVir. They have a Linux version also!

I agree-I should have unhooked the other drives and just installed Linux to a single drive that would not affect the others.

Again, thank you all for the kind replies and advice. I may try this agian someday-with all of this advice in mind. I know Linux is superior to Windows-I HATE Windows and have every since I left DOS. I was probably the last person in the world to install Windows 3.1 :) 

Steve Fritts

Good luck with whatever you decide, and remember that this forum is for help and advice, maybe next time you will use it and hopefully have more success.

---

### Post by igknighted on 2007-04-26
I hope that you get this fixed and try linux again, but please be aware of what you are getting into.  I had used computers for 15 years before linux, but when you come here you are a complete n00b.  We all were (or are).  It is just completely different.  The sooner one realizes that they are starting over, the quicker they learn and are proficient linux users.  I don't mean this in any disrespect, but rather as advice.  In the time I have been on the forum, you would be amazed how many "power users" and "it experts" and other seasoned computer vets struggle, while average users pick it right up... its about habits and expectations.  You have to unlearn years of doing things the wrong way :), and expect an easier time than other users.

But there is hope.  Stick to it, learn from your mistakes, and most importantly read carefully.  There is excellent documentation available.  There was a setting at the last step of the install that let you change which drive the bootloader was installed to (depending on the version.  In 7.04 it's called "advanced" and in 6.10 it's a link called (hd0)).  Also, as mentioned above, unplugging other drives is an option as well (one that, while safer,  leads to other issues later).  Good luck, please stick around!

---

### Post by Josey on 2007-04-26
> **w4sef said:**
> Well folks.....this is a sad tale.. first off let me say I have been using and working with computers since the early 80s so i am no novice. I decided to take the plunge and install linux to see how I would like it. So, I installed a third hard drive on my machine.. made it the H drive.. then proceeded to install ubunta on this drive as I did not wish to take a chance on screwing up the C drive..hahahah... after the install, i rebooted-only to find that I got an error 21 and no grub menu....so, I decided i would reintall Linux. Same thing. So, I disconnected the third drive and rebooted to C.   NO GO...this crap screwed up the MBR on my C drive. ARGGG...I tried everything I could to restore. No go...so, like an idiot, I put this third drive with Linux on my wifes machine..when I booted it immediatly grabbed the C drive and screwed it up too!!! Fortunatley, my wife did not get upset as she knew i was already upset enough as it was. This had left a sour taste in my mouth about Linux. i was veryyyyy disappointed as I have heard great things about Linux and I detest Windoze-UGH.
I sure miss the DOS days....Thanks for reading this.

Steve Fritts

Sorry if I'm being rude but you didn't give linux any respect to begin with and we get what we give. 
You put it on the "H drive" huh?
If you want to give linux a fair shake it goes here
/
not the "h drive"

---

### Post by kelvin spratt on 2007-04-26
i'm nearly 60 so i'm not young if your using xp just boot  on my machine last good install work on mine depends on your bios but give it a try that should rewrite boot but it does not work on all computersuse live cd fiesty
i was shock how bad xp was

---

### Post by wieman01 on 2007-04-26
Deleted...

---

### Post by NullHead on 2007-04-26
We're hear to help not put down and turn away others. It's not fair that we put him down for a minor mistake after all this is a help forum.

---

### Post by diskotek on 2007-04-26
may be it would be very off-topic comment but i begin to sick of these threads headers. e.g. linux sucks, damn linux etc..

i have many problems with my machine as well, making it visible withthese kind of titles is really ugly. respect...

---

### Post by az on 2007-04-26
> **Tomosaur said:**
> Uhh...no, Error 21 means 'disk not found', it doesn't mean the motherboard has a bug, It is possible that yes, a problem with the mobo is causing it, but as far as Grub is concerned, it just can't see the disk. It's a fairly common error message when using multiple hard drives (not that the error is common, it's just that when it occurs, Error 21 is what it usually is), from what I've seen.

Yes, error 21 means Grub cannot find the disk.  The reason that it cannot find it is because it was given misinformation by a bios bug.



> **Tomosaur said:**
> 
To the OP - the MBR only kicks in for  hard disk which holds the primary active partition, which is why Grub installed itself to the MBR on C. You should have made your H drive the master with the active partition being on that disk, to ensure that Grub installed correctly. It's not obviously stated anywhere, but it seems like common sense to some. Anyway - you have a variety of options.


Not true.  There is no such mucking about that needs to be done to dual boot.  While that may be a way to work around the bug in the motherboard bios, you don't need to do that in every other case.  It is not obvious since it should work out-of-the-box.

> **Josey said:**
> Only a noob would install an os thinking it wouldn't mess with the mbr.
On your third hd? lol...  good plan there mr. pro

Sorry if I'm being rude but you didn't give linux any respect to begin with and we get what we give. 
You put it on the "H drive" huh?

You are rude.  Be respectful or leave.  


You shouldn't even have to know what an MBR is to install Ubuntu.

People like you piss me off.

---

### Post by wieman01 on 2007-04-26
> **diskotek said:**
> may be it would be very off-topic comment but i begin to sick of these threads headers. e.g. linux sucks, damn linux etc..

i have many problems with my machine as well, making it visible withthese kind of titles is really ugly. respect...
It is true, but there is always the option to ignore these threads... That said with all respect, mate. 

_**EDIT:**_
Guess it is time to close this thread.

---

### Post by expatCM on 2007-04-26
This is not a bad approach if you prefer a movie rather than reading the manual
[http://video.google.com/videoplay?docid=-6104490811311898236&q=ubuntu+install&hl=en](http://video.google.com/videoplay?docid=-6104490811311898236&q=ubuntu+install&hl=en)

---

### Post by Josey on 2007-04-26
> **az said:**
> 
You are rude.  Be respectful or leave.  


You shouldn't even have to know what an MBR is to install Ubuntu.

People like you piss me off.

Can you people please stop quoting me? I edited it like 10 mins ago...

---

### Post by lepz on 2007-04-26
> **expatCM said:**
> This is not a bad approach if you prefer a movie rather than reading the manual
[http://video.google.com/videoplay?docid=-6104490811311898236&q=ubuntu+install&hl=en](http://video.google.com/videoplay?docid=-6104490811311898236&q=ubuntu+install&hl=en)

I always find the movie to be abit of a let down if I've already read the book. :lolflag:

---

### Post by aysiu on 2007-04-26
> **diskotek said:**
> may be it would be very off-topic comment but i begin to sick of these threads headers. e.g. linux sucks, damn linux etc..

i have many problems with my machine as well, making it visible withthese kind of titles is really ugly. respect...
I agree, which is why I've moved this to Testimonials and Experiences.

This is the relation of an experience (a bad one) and not a support request. I'm always impressed that this community is willing to give support to the frustrated, but this wasn't a support request.

If the OP comes back and says, "Help me fix X problem," then that's an appropriate thread for the support areas of our forums, not "linux-NEVER again!!"

---

### Post by SniperSlap on 2007-04-26
There are a lot of computer users of days gone by who still can't grasp the concept of how computers really work.

I regret to say, the way you went about things (if your post is accurate) doesn't strike me as the actions of someone who is very knowledgeable.  It seems very high level.

Perhaps you should try reading a book, some documents and as others stated: The LiveCD.

---

### Post by igknighted on 2007-04-26
> **az said:**
> Not true.  There is no such mucking about that needs to be done to dual boot.  While that may be a way to work around the bug in the motherboard bios, you don't need to do that in every other case.  It is not obvious since it should work out-of-the-box.
Well, yes.  Normally.  But hes multi booting many disks.  The smart way would be to NOT use Ubuntu's default, which is setup for people who don't understand hardware.  I think it is a dangerous default to overwrite windows bootloader, but its not my call.  I think the part of the Ubuntu install that deals with the bootloader is TERRIBLE.  Use any other distro and there is a full page dedicated to it, showing disks you can put it on, OS's that will be bootable from grub (along with the ability to add more there) and other options (like a bootloader password).  In the Ubuntu install, you have to explicitly select to go "advanced" or know to click a link called (hd0) to get to even a very basic GRUB setup.  You should be presented with these options, as many users know what they are and others are so used to years of mindlessly clicking through wizards they wont see it anyways.

> **az said:**
> You shouldn't even have to know what an MBR is to install Ubuntu.
Disagreed.  Anyone setting up a dual boot should understand what they are doing first, including what the MBR is.  They should also know that overwriting the windows MBR will make windows unbootable if they remove linux.  These are not friendly surprises.  Moral of the story, anyone setting up a dual boot should know what an MBR is or do enough research to find out before they start.

---

### Post by igknighted on 2007-04-26
> **Josey said:**
> Sorry if I'm being rude but you didn't give linux any respect to begin with and we get what we give. 
You put it on the "H drive" huh?
If you want to give linux a fair shake it goes here
/
not the "h drive"

It took me a long time to figure out what "h drive" meant, no lie... that made me feel really good ;)

---

### Post by ZeroWing on 2007-04-26
> **az said:**
> 
You shouldn't even have to know what an MBR is to install Ubuntu.


 I agree. I only had to reinstall Windows and Ubuntu(each) three times before I got it to work, without even considering what it would do to the MBR!:)

---

### Post by aysiu on 2007-04-26
While you shouldn't have to know what the MBR is to install Ubuntu, knowing can certainly help, especially in atypical installation situations.

---

### Post by Ateo on 2007-04-26
You've been using computers since the early 80s? I doubt it. You would have read up and expected issues and not given up so easily... But whatever... you should try again...

---

### Post by agurk on 2007-04-26
w4sef, I can easily picture myself in your situation less than a year ago, when I first started mucking about with Ubuntu. Not that there have been many, but each unsuspected setback has taught me things I previously had no clue about, and I've so far managed to escape relatively unharmed in the end and plenty the wiser. There are indeed some feisty (;)) youngsters around but I'm glad to see you're not the easily offended type and also willing to have another go at things, so, good luck.

---

### Post by thavid on 2007-04-26
Well, first of all, my regards (don't know if it's the best word, english is not my first language) for your problem, sorry you had to deal with that...

Secondly, and as much it cost you to read this, this happened a bit by your fault...

If you wanted to test something you've never used before, you should have used a virtual environment (VMWare Server is FREE!!!), 'cas testing is NEVER done on a production/working system! And if you didn't wanted to use Virtual Machines, you should have at least disconected the other hard drives. If you were unfamiliar with Linux, I guess you were too with it's partitionins system, so who can prove it was the system's fault and not yours?

I know wat you're feeling, I've "been there, done that" and learned my lession! First time I've tried linux, I was in my 16's and the only computer was my father's one (his computer for WORK!!). Me, acting all smart-guy like, fire up the RHL7.1 disk, next thing, no Windows... :( 

But seriosly, don't give it up... Install VMWare Server (again, it's free!) and test it withou fear ;)

Cheerz,
A Happy Ubuntu User :)

---

### Post by reckless2k2 on 2007-04-26
Briefly reading the original post and a few after, I can understand your frustration. Knowing about computers and or working with computers are 2 different things. I work with people everyday that think they know a lot about Windows only to know very little. My point being that most Windows boxes come pre-installed and the only time are touched is to do a complete re-install or upgrade. Rarely will Windows users ever be dealing with booting multiple versions of Windows let alone another OS completely. 

You would have to admit that the setup you purposed is somewhat complicated and should have been researched prior to install. That being said, the 1 FIXMBR suggestion would've corrected the problems. It is evident that while you may be a Windows user, troubleshooting and or multi-boot installs is not up your alley. As I stated before, your idea of how you want to setup the boot process is more complicated and requires research prior to install. 

The LiveCD install is designed for more "simple" installs and or multi-boot installs. It's just the nature of the beast. That being said, what you are trying to accomplish can be done after a little poking around if you so desire to learn. I know many people that learn a great deal more about their computers or computers in general exploring Linux.

Good luck.

---

### Post by Duck2006 on 2007-04-26
Did you try booting in recovery mod?

---

### Post by az on 2007-04-26
> **igknighted said:**
>  I think it is a dangerous default to overwrite windows bootloader, but its not my call.  

When you install Ubuntu on a Vista box, it chainloads the vista bootloader.

> **igknighted said:**
> 
I think the part of the Ubuntu install that deals with the bootloader is TERRIBLE.  Use any other distro and there is a full page dedicated to it, showing disks you can put it on, OS's that will be bootable from grub (along with the ability to add more there) and other options (like a bootloader password).  In the Ubuntu install, you have to explicitly select to go "advanced" or know to click a link called (hd0) to get to even a very basic GRUB setup.  You should be presented with these options, as many users know what they are and others are so used to years of mindlessly clicking through wizards they wont see it anyways.

It is an explicit goal to minimize the number of clicks to an installed system.  The alternate disk installer is less streamlined.  That being said, is there a situation, other than a bug, where the Ubuntu installer breaks your system?

> **igknighted said:**
> 
Disagreed.  Anyone setting up a dual boot should understand what they are doing first, including what the MBR is. 

While it blows people's minds to learn the conept of dual-booting, there is no real need to understand the under-the-hood details if the installer does the work for you and works properly.

> **igknighted said:**
> 
 They should also know that overwriting the windows MBR will make windows unbootable if they remove linux.  These are not friendly surprises.  

That depends on who told you how to remove linux.  

> **aysiu said:**
> While you shouldn't have to know what the MBR is to install Ubuntu, knowing can certainly help, especially in atypical installation situations.

Yes, but dual-booting is not an atypical situation.  If someone wanted to unplug one drive before they install Ubuntu, they would have to know what an MBR is, for example.  But the point is that unpluging a drive is not a requirement for a normal install.

> **Duck2006 said:**
> Did you try booting in recovery mod?

You need to be able to get to the grub menu to do that....

---

### Post by thavid on 2007-04-27
Oh, and by the way, to recover Windows Boot Loader...

In NT/2k/XP/Vista:
GoTo recovery console and type fixmbr and then fixboot

In Win98:
command prompt, then type fdisk /mbr

---

### Post by steveneddy on 2007-04-28
> **w4sef said:**
>  first off let me say I have been using and working with computers since the early 80s so i am no novice. 

Steve Fritts

So why don't you know about the fixmbr command? If you are going to start off a post with such credentials, at least show us that you can read the forums and take some advice before telling the forums in a very public way that you are going away forever.

If you want advice, please ask. There are many experienced persons here that can help beginners like you. Users of computers don't make good installers of programs and software. Just because I know how to use an elevator doesn't mean that I can install one.

If you are going to go away, then please go away. Please take your desperate cries for help elsewhere.

If help is what you need, then please ask. Actually, your problems are elementary and could have been repaired long ago if asked correctly. Even lurking in these forums will reveal answers to questions that you haven't even thought of yet.

Many of us who started using Linux had already dual booted other OS's, partitioned hard drives and installed hardware many times, and using fixmbr was a regular part of this process at times. 

Please don't hesitate to ask for help. We all started somewhere, and you have a chance to start here. You never, you may actually learn something about that little box on your desktop. I thought I knew a lot about PC's, until I installed and started using Linux. It makes one feel good to be successful installing the OS, uning th OS and then installing other programs. 

Nut please, PLEASE, ask questions and don't go away mad. You have to be willing to learn. If not then it will be a frustrating experience. Get the old ideas out of your head and learn some new ideas. You will be a better person for it

This is just my two cents:

-SE

---

### Post by steveneddy on 2007-04-28
Every post he ever made under that user name was in this post. There were no other questions asked in any other forum from this person that I can see. 

Steve, before you go off in a huff, please consider asking more questions, especially if you are a little under experienced.

Lots of Ubuntu love - SE

---

### Post by oomingmak on 2007-04-29
> **alexjhill said:**
> Why didn't you just disconnect your other drives before installing ?  < room falls silent> :
Why should you have to? I have no desire to crawl under my desk to unravel all my neatly cable-tied wires, pull the case out so it can be accessed properly, unscrew the side panels and disconnect a drive, just so I can install an OS (and then have to crawl back under the desk to put it all back again). What right does Ubuntu have to trash your MBR when you have given it no permission whatsoever to write to that drive?

I'm a total Linux noob, and I suffered the same fate with Dapper. In later versions of Ubuntu at least they added the facility to change where grub can be installed (there was no option whatsoever for this in Dapper). But even in v7.04  this new grub placement feature is really badly implemented, and it doesn't work for users switching boot drives using the BIOS (the system will fail to load - unless you know how to edit menu.lst).

This weekend I tried out Foresight Linux for the first time. While the install process is generally a lot uglier than Ubuntu (loads of text mode stuff) the grub installation part of Disk Druid works like a dream (and it absolutely blows Ubuntu out of the water).

I had Foresight install to a second drive and not touch my Windows disk at all, yet Foresight was still bootable as if grub had been installed to (Hd0,0) because you can set the drive order so that a second, third or fourth drive etc. is treated like the master boot disk. Naming schemes for drives in Disk Druid are totally consistent throughout the process (unlike Ubuntu), so you know exactly what is going to happen to your disks before any writes are made.

I also had no problems when I installed Suse, as this too respects your data and only writes where you give it explicit *permission* to do so.

Some people seem more intent on blaming the user for Ubuntu's shortcomings, rather than trying to see if the process itself could be improved.

---

### Post by w4sef on 2007-04-30
Thank you again for all who tried to help. Even the rude ones on here. I WILl try Linux again but only with a single HD so I can't screw it up the way I did the first time.
Again thanks to al.

Steve Fritts
Philadelphia TN

---

### Post by julian67 on 2007-04-30
I think what we've all learned here is that if you're about to do something with little practical knowledge, a reasonable chance of failure and no obvious way to recover from any unexpected problem there's only one sensible course of action to take. Test it out on your wife's PC first and if that doesn't work start on the office machines.

---

### Post by craigsharp on 2007-05-01
The first time I installed Dapper with XP as a dual boot, I came across the same problem.  I don't know how you partitioned the drive, but I first partitioned it in a way that the drive had unused space.   Tried to boot, and a no go.  My next time I used the entire disk with 3 partitions.  1 for my XP, 1 for my ubuntu, and a third which was 1 gig for a swap partition.  That did the trick.   You might double check your partitions and make sure to use the full disk.

I learned my lesson the first time. now I recently installed Feisty on a 250 gig HD with vista on 110 and ubuntu on the rest.  I'm about to leave vista for good and use my entire HD for video and music.

Hope this was of some help.

---

### Post by w4sef on 2007-05-01
To Steveneddy........after reading your rude post I think it is best to close this thread. Yes, I HAVE been using computers since the 80s. I never said I was an expert. I am surprised at some of the harsh and rude comments made to me. Maybe I made a mistake in posting my original message to start with. I have since restored everything and all is running well including my home network.

I will try Linux again soon with just a single hard drive. I was told that the Grub menu would give me a choice as to which operating system I wanted to boot to but that did not happen. And yes, I have known about FixMBR for a long  time and used it in that past to correct some problems.

Again, thank to everyone for attempting to help me. It is appreciated.

Steve Fritts

---

### Post by ubuntu-geek on 2007-05-01
Thread closed per OP's request.

---

