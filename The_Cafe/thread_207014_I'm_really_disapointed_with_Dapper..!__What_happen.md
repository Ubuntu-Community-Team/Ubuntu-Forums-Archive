---
title: "I'm really disapointed with Dapper..!  What happened.?"
date: 2006-07-01
forum: The Cafe
---

### Post by jason.b.c on 2006-07-01
I recieved my Dapper CD's in the mail today and i couldn't have been more excited.

I tore open the packaging, pulled out the CD's and thought "cool" .!

I got some cool stickers too.:o 

So i put one of the disk's in my computer and restarted, I chose the live boot option and after dapper booted up, I noticed that there were a few changes made to the way this version boots up as compared to breezy, So i thought "Yea , this looks preaty good.!"  

And i was also relieved to find that i wasn't going to have the problem with the **Shutdown and restart** buttons being missing, They work without a hitch ,    But....

And this is where the problems start for me..#-o 

**Problem #1**

**I can't** for for the life of me get my HP 1310 printer to work, I know how to do it.!, I went into **printing** to set up my printer, I click on *add printer* and a little dialog box appears telling me it's searching, then a new window opens up showing me that it found my printer attached to the USB port that the printer is currently plugged into.

Next i make sure that **hpc 1310** is highlighted in the list ( wich it was already ) and i click on **install driver**, "But nothing happens"  all i get is a browser window asking me where to get the **PPD file** from..!

If i cancel ( close ) that window and return to the list and click on the button labled **next** ( i think ) i get taken to a window asking me to provide a name and some other info for the printer, so i fill in that info and click **"apply"**   -***But nothing happens..!!***   , The printer never shows up under printing as ready or otherwise..
But it works just fine in breezy so why won't it install in dapper..??

**Problem #2**

Dapper is extremely slow..!! , If i try to close an open window and the system was doing something in the background it takes several minutes for the window to close if it closes at all..!    I don't have enough fingers on my hands in order to count the number of times something failed to close out or an application failed to open correctly and i would get the error message telling me that **"The program is not responding"** in wich i would have to click on the **"Force quit"** button just to be able to try the program over again only to have it happen to me again..!:confused: 

**Problem #3**

Why does dapper naturally assume that i want it to put my computer into hibernation after (i think) like twenty minutes of inactivity..???

Thats another one that i can't figure out, Now in breezy there's option to disable the ubuntu power managment from being able to shutdown, suspend or hibernate the computer after so many minutes by simply un-checking a check box, But i can't figure this one out in dapper.!

I set the screensaver to come on after five minutes and that works fine although the *fade in fade out* feature dosen't quite work right, it fades out to screensaver but not when returning to desktop ( senses activity )..

But i don't get it.!, Where/How do you disable the power management ( permanently) from being able to hibernate/suspend the computer when i'm away from it.?
I looked and looked for an hour and a half or so and couldn't figure it out.. 

**Problem #4**

When using the **Alacarte menu editor** i can't seem to add some things to the *Applications , Places or System* menu's on the taskbar like i want to, I was able to add a couple of things but not the one's i really wanted, like the sound volume meter , recording meter and so on..

I don't know if this is a glitch or just user error , i dunno..

I thought dapper was supposed to be the upgrade from breezy..??   But with all these problems i'm having it seems more like a downgrade ..

Although my floppy drive works perfectly now.:lol: 

I don't know.? , But if i can't figure out how to get around this stuff and make things work right for me i don't think i'll be upgrading from breezy any time soon..

---

### Post by jarland on 2006-07-01
Well I can only comment on problem #3. Assuming gnome, I know there's a power management option under one of the system menus.

---

### Post by jason.b.c on 2006-07-01
[QUOTE=jarland]Well I can only comment on problem #3. Assuming gnome, I know there's a power management option under one of the system menus.[/QUOTE]


Yea i saw that, But couldn't figure out how to **completely disable it** from setting my computer into hibernation/Suspend mode after so many minutes of inactivity..:confused:

---

### Post by woedend on 2006-07-01
as for speed, I agree that dapper is by far the slowest.  sure gnome sped up a bit logging in(supposedly), but it got unbearable....even the kernel hangs at boot...erg...it was looking so good in the early dev days.

---

### Post by woedend on 2006-07-01
x double post

---

### Post by anodizer on 2006-07-01
[QUOTE=jason.b.c]**Problem #2**

Dapper is extremely slow..!! , If i try to close an open window and the system was doing something in the background it takes several minutes for the window to close if it closes at all..!    I don't have enough fingers on my hands in order to count the number of times something failed to close out or an application failed to open correctly and i would get the error message telling me that **"The program is not responding"** in wich i would have to click on the **"Force quit"** button just to be able to try the program over again only to have it happen to me again..!:confused:[/QUOTE]

This doesn't sound like a problem to me. Maybe your cd-rom drive is not a fast one, or you don't have enough RAM. Anyway, live cds are always somewhat slow, you should really install it to see the performance. Dapper is surely faster than breezy. It boots faster, gnome is faster and you won't have all those "not responding" messages.

You can find the options for power management under System -> Prefs -> Power Management and you can disable it completely through System -> Prefs -> Sessions -> Startup programs (just disable gnome-power-manager).

---

### Post by jason.b.c on 2006-07-01
[QUOTE=anodizer]This doesn't sound like a problem to me. Maybe your cd-rom drive is not a fast one, or you don't have enough RAM. Anyway, live cds are always somewhat slow, you should really install it to see the performance. Dapper is surely faster than breezy. It boots faster, gnome is faster and you won't have all those "not responding" messages.[/QUOTE]

Thank you for your reply..:D 

2 CD rom drives , ( 1 ) 46x generic brand and ( 2 ) 52x Sony CD-RW..
I've got 256 mb's of ram ( Is that too little to run from live disk..? )

Why do i get all the **"not responding"** error messages from the live running mode..???

[QUOTE=anodizer]You can find the options for power management under System -> Prefs -> Power Management and you can disable it completely through System -> Prefs -> Sessions -> Startup programs (just disable gnome-power-manager).[/QUOTE]

I don't want this to sound like i'm trying to argue with you or disagree with what you said but, Are you sure about that..??  I mean because i messed with it and messed with it and couldn't figure out how to stop the power manager from taking over and putting my computer into suspend/hibernate or whatever it was..It drove me crazy..!

So if i go to *system-> preferances-> Sessions-> Startup programs* and disable the power manager it won't be able to do that anymore..???

I could almost swear i tried that and it still happened.! , Although i could very well be wrong..;)

---

### Post by givré on 2006-07-01
[QUOTE=jason.b.c]
I don't want this to sound like i'm trying to argue with you or disagree with what you said but, Are you sure about that..??  I mean because i messed with it and messed with it and couldn't figure out how to stop the power manager from taking over and putting my computer into suspend/hibernate or whatever it was..It drove me crazy..!

So if i go to *system-> preferances-> Sessions-> Startup programs* and disable the power manager it won't be able to do that anymore..???

I could almost swear i tried that and it still happened.! , Although i could very well be wrong..;)[/QUOTE]
You have an option in System -> Prefs -> Power Management, if you don't see it you are just blind. If you are blind, gconf-editor apps>gnome-power-manager should make you happy.
And yes remove it rom your startup programs while disable it

---

### Post by Randomskk on 2006-07-01
[QUOTE=jason.b.c]
I've got 256 mb's of ram ( Is that too little to run from live disk..? )
[/QUOTE]
That isn't much; I must say Dapper runs killer from live CD or installed on my laptop with 1GB of ram, no problems.

---

### Post by raptros-v76 on 2006-07-01
im running dapper with KDE 3.5.2 and E16, and its faster than .... (do not use the duck analogy, do not use the duck analogy)

---

### Post by rcarring on 2006-07-01
Dapper is slower than Breezy. The release version is slower than Beta 2. I can say this quite confidently as I have run Dapper since Beta 2 and also Breezy on identical hardware.

---

### Post by woedend on 2006-07-02
[QUOTE=rcarring]Dapper is slower than Breezy. The release version is slower than Beta 2. I can say this quite confidently as I have run Dapper since Beta 2 and also Breezy on identical hardware.[/QUOTE]

This is exactly my sentiments.  Except, for me the beginnings of dapper(beta 2 as you say perhaps) were faster than breezy.  I'm not sure where things went sour.

---

### Post by Qrk on 2006-07-02
I haven't had any problems, in fact I've been surprised by some of the negative press surrounding dapper. Its still quite speedy for me (I started at RC3 when it was really very speedy)

The new installer worked fine. I love LiveCD installers because they let you ensure everything works before installation, no surprises. Dapper's installer isn't what I would call polished yet, but it is less daunting to new users.

I remember how many people hated Breezy when it came out, and Hoary as well. Breezy had that problem with the gcc (3.4 vs 4.0, it was a nightmare to compile something on breezy) Hoary had the sound problem (I ended up just turning mine off for all but media apps) and Warty had some troubles, namely from Gnome 2.8 for me. 

I suppose my disapointment only comes from my hope that the extra time would have sorted out most of the Dapper issues. But Dapper is still hands down the best Ubuntu yet.

---

### Post by ubuntu27 on 2006-07-02
[QUOTE=jason.b.c]

**Problem #1**

**I can't** for for the life of me get my HP 1310 printer to work, I know how to do it.!, I went into **printing** to set up my printer, I click on *add printer* and a little dialog box appears telling me it's searching, then a new window opens up showing me that it found my printer attached to the USB port that the printer is currently plugged into.

Next i make sure that **hpc 1310** is highlighted in the list ( wich it was already ) and i click on **install driver**, "But nothing happens"  all i get is a browser window asking me where to get the **PPD file** from..!

If i cancel ( close ) that window and return to the list and click on the button labled **next** ( i think ) i get taken to a window asking me to provide a name and some other info for the printer, so i fill in that info and click **"apply"**   -***But nothing happens..!!***   , The printer never shows up under printing as ready or otherwise..
But it works just fine in breezy so why won't it install in dapper..?? [/QUOTE]

This also happens to me. When I run Dapper LIVE/DESKTOP CD and try to add my printer (HP OfficeJet 6110 all-in-one), it just ignores me. I think it's a bug in the Live CD. I think that that would work once it is installed. Give it a chance!!


PS: I am still running Breezy B. and my printer works perfectly. 

PS2: Install it using Alternate CD. The traditional way :)

---

### Post by jason.b.c on 2006-07-02
[QUOTE=givré]You have an option in System -> Prefs -> Power Management, if you don't see it you are just blind. If you are blind, gconf-editor apps>gnome-power-manager should make you happy.
And yes remove it from your startup programs while disable it[/QUOTE]

Well uummm , You didn't need to be sarcastic..  And no , I'm not blind..!

Like i said, I messed with it and messed with it and couldn't figure out what to do.. 

[QUOTE=Ubuntu27]This also happens to me. When I run Dapper LIVE/DESKTOP CD and try to add my printer (HP OfficeJet 6110 all-in-one), it just ignores me. I think it's a bug in the Live CD. I think that that would work once it is installed. Give it a chance!!


PS: I am still running Breezy B. and my printer works perfectly.

PS2: Install it using Alternate CD. The traditional way [/QUOTE]

I would really like to be able to figure that one out, Like when it does ask me for the **PPD** file, I just don't know where to look for it, Where's it at..??

To tell the truth , I really do want to install Dapper, But i just don't want to have to fight with it just to make things work out for me..:cry:

---

### Post by givré on 2006-07-02
I don't know how you can compare a live CD session to an install one. Try it (it's not so much time) and you will see that everything will work. Trust me, and blame me if not

---

### Post by angkor on 2006-07-02
[QUOTE=rcarring]Dapper is slower than Breezy.[/QUOTE]

On my system it isn't. Boot is way faster. Gnome reponsiveness is better / faster. Startup times for programs is the same, as in I don't notice any difference.

---

### Post by DJiNN on 2006-07-02
[QUOTE=jason.b.c]
**Problem #2**

Dapper is extremely slow..!! , If i try to close an open window and the system was doing something in the background it takes several minutes for the window to close if it closes at all..!    I don't have enough fingers on my hands in order to count the number of times something failed to close out or an application failed to open correctly and i would get the error message telling me that **"The program is not responding"** in wich i would have to click on the **"Force quit"** button just to be able to try the program over again only to have it happen to me again..!:confused: 

**Problem #3**[/quote]

I'm having similar problems here i must say, and it's starting to become a pain! First, Firefox crashes almost every day (OK, i know this is NOT "Linux" per se, and i am looking into this as an "individual" problem because it's doing similar things in XP, so it's possibly extensions etc).... butthe main beef i have is "Speed" (Or LACK Of!). Dapper seems to be getting slower & slower..... the amount of time that it takes when i select a new drive in Nautilus is just too much. 

I switch over to XP (Running on another box with a much reduced (Older PIII) CPU & it's running fine...... Sure, XP crashes as well, and does strange things sometimes, but this system is a P4 2.4 with a Gig of RAM, it should have a reasonable speed one would think.....

Anyway, i have noticed that when i reboot & start again from fresh, it all seems a little bit better (But still not as snappy as it could or should be) so i shall give it a while longet before i start thinking about changing to something else. 

Sorry about the rant..... just felt a need to vent & thanks for listening! :) 

DJiNN

---

### Post by bionicyeti on 2006-07-02
I'm running Dapper on a P3 - 1.2ish? with 256mb of ram and I'm having no issues with speed at all. :neutral:

---

### Post by kleeman on 2006-07-02
[QUOTE=jason.b.c]I
**Problem #1**

**I can't** for for the life of me get my HP 1310 printer to work, I know how to do it.!, I went into **printing** to set up my printer, I click on *add printer* and a little dialog box appears telling me it's searching, then a new window opens up showing me that it found my printer attached to the USB port that the printer is currently plugged into.

Next i make sure that **hpc 1310** is highlighted in the list ( wich it was already ) and i click on **install driver**, "But nothing happens"  all i get is a browser window asking me where to get the **PPD file** from..!

If i cancel ( close ) that window and return to the list and click on the button labled **next** ( i think ) i get taken to a window asking me to provide a name and some other info for the printer, so i fill in that info and click **"apply"**   -***But nothing happens..!!***   , The printer never shows up under printing as ready or otherwise..
But it works just fine in breezy so why won't it install in dapper..??..[/QUOTE]
Dude, the Install driver option is for when the system does not have a driver and so you need to have a *.ppd file handy. I don't think though that this was your problem if the printer never showed up. There have been a ton of updates to fix bugs since release. Are you running a completely updated system?

---

### Post by bruce89 on 2006-07-02
The kernel has preemptive multitasking enabled, not sure if that speeds things up. - ```
uname -a
Linux Scooby-Doo 2.6.15-25-amd64-k8 #1 SMP PREEMPT Wed Jun 14 11:39:18 UTC 2006 x86_64 GNU/Linux
```

---

### Post by jason.b.c on 2006-07-02
[QUOTE=kleeman]Dude, the Install driver option is for when the system does not have a driver and so you need to have a *.ppd file handy.[/QUOTE] Oh .?  My bad then..    [QUOTE=kleeman]I don't think though that this was your problem if the printer never showed up. There have been a ton of updates to fix bugs since release. Are you running a completely updated system?[/QUOTE]

I wish someone would/could put something like **What to do when it dosen't work..** on one of these pages..

[Here..?]("https://help.ubuntu.com/community/HpPrinterInstallationAndMaintenanceDapper?highlight=%28CategoryDocumentation%29")
and
[Here..?]("https://help.ubuntu.com/community/HpPscHpPhotosmartSeriesAllInOnePrinters?highlight=%28CategoryDocumentation%29")
:rolleyes:

---

### Post by vayu on 2006-07-03
[QUOTE=jason.b.c]
I would really like to be able to figure that one out, Like when it does ask me for the **PPD** file, I just don't know where to look for it, Where's it at..??
[/QUOTE]

You might have to do a bit of reading, but I think you'll be able to find it here.

[http://www.linuxprinting.org/]("http://www.linuxprinting.org/")

---

### Post by Iandefor on 2006-07-03
[quote=jason.b.c]**Problem #4**

When using the **Alacarte menu editor** i can't seem to add some things to the *Applications , Places or System* menu's on the taskbar like i want to, I was able to add a couple of things but not the one's i really wanted, like the sound volume meter , recording meter and so on...[/quote] Er... do you mean panel applets?

---

### Post by rko618 on 2006-07-03
[QUOTE=jason.b.c]
**Problem #1**

**I can't** for for the life of me get my HP 1310 printer to work, I know how to do it.!, I went into **printing** to set up my printer, I click on *add printer* and a little dialog box appears telling me it's searching, then a new window opens up showing me that it found my printer attached to the USB port that the printer is currently plugged into.

Next i make sure that **hpc 1310** is highlighted in the list ( wich it was already ) and i click on **install driver**, "But nothing happens"  all i get is a browser window asking me where to get the **PPD file** from..!

If i cancel ( close ) that window and return to the list and click on the button labled **next** ( i think ) i get taken to a window asking me to provide a name and some other info for the printer, so i fill in that info and click **"apply"**   -***But nothing happens..!!***   , The printer never shows up under printing as ready or otherwise..
But it works just fine in breezy so why won't it install in dapper..??
[/QUOTE]

Weird... I have the same printer and it installs just fine.  I don't know why yours isn't working.

---

### Post by givré on 2006-07-03
Because he try it from the live session.

---

### Post by heldal on 2006-07-03
Regarding #2, performance:

Many people have found performance-issues with HAL and its constant polling of devices which lead to severe performance degredation with some IDE configurations. Try to stop the dbus service (sudo /etc/init.d/dbus stop) and see if that does anything to the performance. There is no fix available, but it has been reported as a bug. [https://launchpad.net/distros/ubuntu/+bug/48499](https://launchpad.net/distros/ubuntu/+bug/48499)

---

### Post by fabertawe on 2006-07-03
[QUOTE=jason.b.c]Well uummm , You didn't need to be sarcastic..  And no , I'm not blind..!

Like i said, I messed with it and messed with it and couldn't figure out what to do..[/QUOTE] 

Have you tried moving the sliders all the way to the right so they say 'never'?

Apologies if you already tried that ;-)

Paul

---

### Post by DJiNN on 2006-07-03
Well, just a few days ago Dapper was running really slow & Firefox was crashing a lot & creen redraws (The GUi etc) were slow.... well, it was not good & it wasn't getting any better! :)

But, then i decided (After reading several threads) to update my Kernel image to a 686 image, and also start using KDE instead of Gnome..... WOW, what a difference. Dapper is now back & firing on all cylinders again, and better than ever! 

Everything that was "wrong" or "Slow" is not "Right" & "Fast"..... :) I don't know if it was the image or changing to KDE (Or maybe a combination of both even) but whatever it is, it's changed this whole machine. 

Just wanted to share this in case others were having similar problems. 

DJiNN

---

### Post by jason.b.c on 2006-07-03
> **fabertawe]Have you tried moving the sliders all the way to the right so they say 'never'?

Apologies if you already tried that  said:**
> 
Yea i tried that as well.  Thank you anyhow though..

[QUOTE=Iandefor]Er... do you mean panel applets?

Yes.?!   I was trying to add the *System Volume Meter* and a few others and they would not add themselves to the menu's..

[QUOTE=Givre]Because he try it from the live session.[/QUOTE]

Then why does my printer work when i do it in **Breezy.**..??   Live..!

[QUOTE=Vayu]You might have to do a bit of reading, but I think you'll be able to find it here.

[http://www.linuxprinting.org/](http://www.linuxprinting.org/)[/QUOTE]

Thanks., I'll check it out..

---

### Post by givré on 2006-07-03
okay guy, i think i was a bit wrong with you because you compare things from a live session, but you were right, testing stuff in a live session is the good way, i mean, it's made for that.
So i decide to run a live session from the CD i just receveid (so we have the same CD), and test things point by point.

1# Alacarte works pretty good with me, i try to add and remove some stuff, and everything works, even the 'volume meter' works. So i don't know what's wrong there.

2# To disable hibernation, system>prefs>power management, in the general tab, you have an option 'sleep type when inactive' that you can set to sleep or Do nothing, it was set to Do nothing for me, but it stongly depends of the hardware.

3# Live session was quite speed, there were some slow down because of the cdrom, but not so much. So the cause could be the graphic cards (what is yours) or the cdrom device

4# And to finish, the printer problem. Yeah i can confirm it, printer don't work in live session, when i try to add my printer, the same things happens to me, i means nothing happens. But if i had it to an install session it works, so don't worry about that, it's a bug in the liveCD. Although, don't be confuse by the 'install driver' buttons, it's just in case you have an other driver that you want to install.

I hope that it will help you, but i strongly think that you should give dapper a try.

---

### Post by Iandefor on 2006-07-03
[quote=jason.b.c]Yes.?!   I was trying to add the *System Volume Meter* and a few others and they would not add themselves to the menu's..[/quote] Perhaps you're not familiar with what a panel applet is. Right-click on one of your panels, click "Add to Panel..." and look around. If what you're looking for is there, well... you were just looking in the wrong spot, then :).

---

### Post by jason.b.c on 2006-07-22
> Problem #3

Why does dapper naturally assume that i want it to put my computer into hibernation after (i think) like twenty minutes of inactivity..???

Thats another one that i can't figure out, Now in breezy there's option to disable the ubuntu power managment from being able to shutdown, suspend or hibernate the computer after so many minutes by simply un-checking a check box, But i can't figure this one out in dapper.!

I set the screensaver to come on after five minutes and that works fine although the fade in fade out feature dosen't quite work right, it fades out to screensaver but not when returning to desktop ( senses activity )..

But i don't get it.!, Where/How do you disable the power management ( permanently) from being able to hibernate/suspend the computer when i'm away from it.?
I looked and looked for an hour and a half or so and couldn't figure it out.. 


> **anodizer said:**
> 
You can find the options for power management under System -> Prefs -> Power Management and you can disable it completely through System -> Prefs -> Sessions -> Startup programs (just disable gnome-power-manager).

I still can't figure this one out...!!!!

Everything is disabled from startup.!

So why is dapper still suspend or hibernating my computer after like 20-30 minutes..???

Oh and by the way , I've got dapper installed now.! , no longer running from a live CD version..

Could somebody please tell me how to correct this..???   Do i have to edit something.?

---

### Post by jason.b.c on 2006-07-22
*Bump* 

Now i can't figure out why wine won't install.....   AAAARRRRGGGGGG

---

### Post by erikpiper on 2006-07-22
> **jason.b.c said:**
> Well uummm , You didn't need to be sarcastic..  And no , I'm not blind..!

Like i said, I messed with it and messed with it and couldn't figure out what to do.. 


EDIT: Srry- Didnt read the whole thread... But mabe it needs an update to work right?

Erm.. Slide it ALL the way? See the screenshot I took of system > prefs > power management. (Mabe this came with an update?)? Dapper (Installed) is FASTER than breezy for me- even on my old laptop. More polished also. Try installing- If you do a good backup, you can always reinstall breezy..


[img]http://img131.imageshack.us/img131/4632/screenshotaj0.png[/img]

(The monitor can also be set to never) Also- in general I just set both menus to do nothing.

---

### Post by jason.b.c on 2006-07-22
> **erikpiper said:**
> Erm.. Slide it ALL the way? See the screenshot I took of system > prefs > power management. (Mabe this came with an update?)? Dapper (Installed) is FASTER than breezy for me- even on my old laptop. More polished also. Try installing- If you do a good backup, you can always reinstall breezy..


[img]http://img131.imageshack.us/img131/4632/screenshotaj0.png[/img]

(The monitor can also be set to never) Also- in general I just set both menus to do nothing.

Everyone of them are slid all the way over to the right , on every tab in that thing..

Also i disabled the power manager from starting up under **sessions** and still shuts down the computer on me...

Then when i bring it back out and try to use it again it's so damn slow that i have just restart the system just to be able to do anything.....This sucks..!

---

### Post by Zeroangel on 2006-07-22
> **DJiNN said:**
> Well, just a few days ago Dapper was running really slow & Firefox was crashing a lot & creen redraws (The GUi etc) were slow.... well, it was not good & it wasn't getting any better! :)

But, then i decided (After reading several threads) to update my Kernel image to a 686 image, and also start using KDE instead of Gnome..... WOW, what a difference. Dapper is now back & firing on all cylinders again, and better than ever! 

Everything that was "wrong" or "Slow" is not "Right" & "Fast"..... :) I don't know if it was the image or changing to KDE (Or maybe a combination of both even) but whatever it is, it's changed this whole machine. 

Just wanted to share this in case others were having similar problems. 

DJiNN
DJiNN,

I think this is a known bug, I believe there was another thread where people were getting mysterious OS slowdowns than finally lockups. Turns out that Firefox causes Xorg to consume memory like a fat kid consuming a burger. I am using Kubuntu 6.06 and I get this error too. If you're using an AMD machine, than you might want to try installing Swiftfox and have it replace Firefox. Personally, I am doing OK with Konqueror, though I miss the FF extensions a lot.

Also, GTK-Gnutella causes intermnittent slowdowns on my machine, not sure if its because its reading files or if its the fact that its a GTK app (Firefox is also a GTK app). Strangely enough, it worked perfectly back when I was testing Ubuntu/Dapper. 

Come to think of it, Dapper was working flawlessly towards the end of testing, but the final release just seems to have broken a few things. Guess the devs hurried too much to get the final things uploaded that they didnt really have time to test them.

Next time, there will have to be a huge dead period in feature addons (ie: internationalization/hardware support) set sometime before release.

BTW: My rig is:
Kubuntu 6.06, AMD Sempron 2800+ (K7 Kernel), Nvidia GeForce4MX (Proprietary Drivers), Non- XGL/Compiz.

---

### Post by erikpiper on 2006-07-22
AMD Anthlon 64 3500- Firefox. XGL/Compiz- no problems.. only 372 mb ram used.. out of 1 gig. WITH firefox. XGL/Compiz, gdesklets, amarok,etc..

Again, has all of the=is been fixed in updates?

---

### Post by Cyraxzz on 2006-07-23
about the speed issue: it's probably realted to the video driver check if it is correctly installed. you could also read the UDSF Dapper Power tweaking section, that should help.

[http://doc.gwos.org/index.php/PowerTweakingDapper]("http://doc.gwos.org/index.php/PowerTweakingDapper")

And if Gnome is being slow this should help

[http://doc.gwos.org/index.php/Faster_gnome_menus]("http://doc.gwos.org/index.php/Faster_gnome_menus")

If your using a laptop for Dapper then follow these tips for increasing speed.

[this]("http://ubuntuforums.org/showpost.php?p=1254289&postcount=13") [and this]("http://ubuntuforums.org/showpost.php?p=1246285&postcount=11")

I hope that helped, good luck.

---

### Post by SuperMike on 2006-07-23
Your slowness may be video-driver related, I'd reason to bet, and the Installation and Upgrade forum area has a pinned item to help you work on Xorg issues like this if this is the case. You should also install the linux-686 package soon and reboot into that kernel to speed things up slightly. Another way to speed it up is to switch to Swiftfox instead of Firefox. It's a compiled fork that runs better on Pentiums. Just search on Swiftfox in the search here and you'll find out how to install it.

---

### Post by jason.b.c on 2006-07-23
What about kubuntu..???

Is there a glitch in it as well..??  With the power management...

If i just whipe my hard drive..! and install kubuntu instead should i expect to have the same problems with the power manager in it as well..????


This is really starting to get on my nerves...!!!  ](*,) ](*,)

---

