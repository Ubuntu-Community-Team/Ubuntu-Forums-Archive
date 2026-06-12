---
title: "what will hapen if i remove the hdd while the computer is turned on?"
date: 2009-07-20
forum: The Cafe
---

### Post by heyyy on 2009-07-20
its probably a stupid thing to do but im curious...
please answer if you really know what your talking about

---

### Post by Malta paul on 2009-07-20
Always turn the power off before working on your computer.
To answer your question, if you unplugged the power plug from the HD _first_ nothing will happen, but don't push your luck! 
:)

---

### Post by toupeiro on 2009-07-20
Logically or physically?



Assuming you don't have a server with hot-swappable hard drives (noticeable by the very large lock releases and handles on the front of a slideable chassis) let me reaffirm your hypothesis.  Yes, it is a stupid thing to do.  I'm going to stretch further than my obligatory "strong recommendation against" and go for a very straightforward "**don't ever do this!**"

If you're very, very lucky, nothing will happen.  If you're somewhat average lucky, you'll just corrupt your file system.  Know, however, that you are well within the realm of frying hardware.  Not just your hard drive, but your motherboards disk controller and possibly more.

---

### Post by Grenage on 2009-07-20
If you happen to be writing at the time, there is a chance it will get a little corrupt.  If it's not writing at the time, the chance of any damage occurring is quite low.

As for the OS; it _may_ continue to function if what it needs is stored in memory.  Once it tried to access someone on the drive, it would all go to hell.

---

### Post by toupeiro on 2009-07-20
> **Grenage said:**
> If you happen to be writing at the time, there is a chance it will get a little corrupt.  If it's not writing at the time, the chance of any damage occurring is quite low.

As for the OS; it _may_ continue to function if what it needs is stored in memory.  Once it tried to access someone on the drive, it would all go to hell.

Your prognosis ultimately depends on what he means by "unplug"  If you want to assume he means power, fine.  I won't make that assumption.

---

### Post by Grenage on 2009-07-20
It would be pretty much the same story whether he pulled the data, power, or both at the same time.

---

### Post by toupeiro on 2009-07-20
> **Grenage said:**
> It would be pretty much the same story whether he pulled the data, power, or both at the same time.

I sure wish I had photo's of that scorched ribbon cable I pulled out of an old AMD Thunderbird.  I am "pretty much" sure that wouldn't have happened if power wasn't hooked up when they accidentally missed a pin plugging it back in. ;)

Don't play with fire in the first place and you'll be much better off.

---

### Post by Grenage on 2009-07-20
Well with plugging it back in, that does add an extra dimension ;)

Bottom line, Mr Opening Poster; don't do it!

---

### Post by heyyy on 2009-07-20
lets say that i only have rythmbox(without playing music) on and its on screensaver for about 15 minutes and then completely remove the hdd(lets say.. for 5 minutes) and then you put it back on,while the computer is still on and in screensaver.
According to these circumstances.. what will happen?

---

### Post by russo.mic on 2009-07-20
This like asking "what would happen If I were to cut my thumb off while holding a gun pointed at my head?"

My vote is to try it and find out.  Might as well put a new pair of shoes on before you shoot yourself in the foot.  

Are you thinking of doing this?  Or have you already done it?

---

### Post by varun1786 on 2009-07-20
I tried that a yr back when i had windows. My system just froze. I switched the power off connected the hdd back on an it started. Din notice any problems but scandisk insisted that i scan my harddisk, i skipped it, and it still works to this day.

---

### Post by heyyy on 2009-07-20
> **russo.mic said:**
> This like asking "what would happen If I were to cut my thumb off while holding a gun pointed at my head?"

My vote is to try it and find out.  Might as well put a new pair of shoes on before you shoot yourself in the foot.  

Are you thinking of doing this?  Or have you already done it?

no,but i think someone in my home already done it while i was away and im trying to find out if this is possible

---

### Post by scrapmetal on 2009-07-20
Do not do it.
Have done it by mistake.
Hey we are all human.
Over the years results have been dead hard drives, a motherboard and possibility a number of power supply early retirements.

---

### Post by heyyy on 2009-07-20
> **scrapmetal said:**
> Do not do it.
Have done it by mistake.
Hey we are all human.
Over the years results have been dead hard drives, a motherboard and possibility a number of power supply early retirements.

im not saying that ill do it.
im just checking my options...

---

### Post by heyyy on 2009-07-20
lets add one more condition:
what if when i remove it,install it on another computer(normally this time),do some reading and then install on the first computer(while its turned on)?

---

### Post by varun5049 on 2009-07-20
I have done that with my external Hdd a couple of times...
Turning the power off usually doesn't do any harm...
But if u are writing into your system while you do that you'll end up frying up your Harddisk...
thats it... Nothing more than that..

well we could do with one more observation..
Just let me know what happened when you actually do that..

---

### Post by Elfy on 2009-07-20
moved to cafe as it's not a support thread.

---

### Post by calrogman on 2009-07-20
If you do attempt this for whatever reason, please be sure to umount the hard drive.  If you are running Linux from the hard drive at the time, please ensure that you have booted the kernel with the "toram" parameter.

---

### Post by heyyy on 2009-07-20
the truth is that i think my younger brother did it while i was away and now im trying to figure it out <--is there a way to know?

---

### Post by Grenage on 2009-07-20
Not really; bit of a random thing to suspect.

---

### Post by CaptainMark on 2009-07-20
Im wondering more why the heck do you want to find out?

---

### Post by heyyy on 2009-07-20
> **CaptainMark said:**
> Im wondering more why the heck do you want to find out?

because i have a lot of important data in there,things that my brother dont want to see

---

### Post by Grenage on 2009-07-20
If you're bothered about privacy, use encryption.

---

### Post by heyyy on 2009-07-20
> **Grenage said:**
> If you're bothered about privacy, use encryption.

as a newbe here id appreciate some links related to this
but the question remains if someone has an idea like what to look for.
could i check for some clues in the "log file viewer" ?

---

### Post by gn2 on 2009-07-20
> **heyyy said:**
> lets add one more condition:
what if when i remove it,install it on another computer(normally this time),do some reading and then install on the first computer(while its turned on)?

If it's an IDE hard drive and you connect it to a live molex plug, you will release the magic smoke and kill the drive stone dead.
Same if it's a SATA drive with a molex power socket.

---

### Post by Grenage on 2009-07-20
I would recommend you try something like TrueCrypt, it's a decent encryption program. If you have trouble with that, there is an easy interface called "Easy Crypt" which should be available in the main repository.

There is no way to know if your brother did unplug it.  It can't write to a log file if the drive has been unplugged.

---

### Post by heyyy on 2009-07-20
> **Grenage said:**
> I would recommend you try something like TrueCrypt, it's a decent encryption program. If you have trouble with that, there is an easy interface called "Easy Crypt" which should be available in the main repository.

There is no way to know if your brother did unplug it.  It can't write to a log file if the drive has been unplugged.

why truecrypt its not on the repos?

---

### Post by Grenage on 2009-07-20
TrueCrypt is available as a DEB file from the main site.  Easy Crypt is another interface for truecrypt.

---

### Post by t0p on 2009-07-20
> **heyyy said:**
> why truecrypt its not on the repos?

Truecrypt is the best encryption app I know of.  Read its documentation and you'll see what it can do.  I don't know why it isn't in any repos, but this is one of the very few times I'd recommend a user go download a package from a site somewhere.   There's a .deb available at [www.truecrypt.org]("http://www.truecrypt.org").

Encryption is the way you need to go to protect your files from prying eyes.  Taking out the hard disk and hiding it is obviously an option.  But I'd say a pretty crap option.  Your brother may find the hidden disk; he won't find your truecrypt passphrase (unless you write it down somewhere - which is, of course, a very stupid thing to do).

> **Grenage said:**
> Easy Crypt is another interface for truecrypt.

Don't bother with easycrypt.  It has been rendered obsolete by truecrypt's excellent gui.

---

### Post by hessiess on 2009-07-20
Truecrypt was covered in detail on Sccurity Now 41.
[http://twit.tv/sn41](http://twit.tv/sn41)

---

### Post by Grenage on 2009-07-20
Oh Christ, not Steve Gibson!

---

### Post by willmsbrt1 on 2009-07-20
when you boot up go to bios , 

when in bios go to security and place a boot password on it it , if it was removed and placed into another pc the bios ( boot ) password will not allow a user to open unless it is password opened , no matter what pc the hd is insatlled in , use a password that you will remember though as it will lock the drive to all unless the proper boot password is used , 

as for the first question it would depend on the hard drive itself , make and model would help with this , if it is a newer unit , post 04 or so it most likely could be hot swapped as it was starting to become more of a norm during this time , check the mfg infor on the drive and google and you can find out , 

the bios log will also tell you if and when it was a clean shutdown or not , as in time date and , power loss , user requested , so on, question though , are we talking windows or ubuntu ?? ubuntu > system > administration > system log and you will know when the drive was ran , watches everythin

---

### Post by heyyy on 2009-07-21
> **willmsbrt1 said:**
> when you boot up go to bios , 

when in bios go to security and place a boot password on it it , if it was removed and placed into another pc the bios ( boot ) password will not allow a user to open unless it is password opened , no matter what pc the hd is insatlled in , use a password that you will remember though as it will lock the drive to all unless the proper boot password is used , 

as for the first question it would depend on the hard drive itself , make and model would help with this , if it is a newer unit , post 04 or so it most likely could be hot swapped as it was starting to become more of a norm during this time , check the mfg infor on the drive and google and you can find out , 

the bios log will also tell you if and when it was a clean shutdown or not , as in time date and , power loss , user requested , so on, question though , are we talking windows or ubuntu ?? ubuntu > system > administration > system log and you will know when the drive was ran , watches everythin

i think the bios password implies only for the computers main unit boot up not for the drive specific..

---

### Post by heyyy on 2009-07-21
and i repeat my qusetion :why truecrypt is not on the repos?

---

### Post by Grenage on 2009-07-21
Then let us repeat our answer: "We don't know".

Maybe the authors didn't want it on the repositories.

---

### Post by dmizer on 2009-07-21
> **heyyy said:**
> the truth is that i think my younger brother did it while i was away and now im trying to figure it out <--is there a way to know?

If your drive is SATA II and your mainboard SATA controller supports hotswap, not much would happen other than a system freeze.

If your drive is IDE, you would most likely have a non-functional computer. Disconnecting/connecting IDE cables while powered destroys drives and destroys main boards.

IF your drive is SATA II and your brother disconnected it, read it from another system, and plugged it back in, then there would be no logs and no way to prove that this was done.

As to why truecrypt is not in the repos: [s]I'm not positive, but that level of encryption is illegal in many countries outside of the U.S.[/s] Truecrypt is released under their own custom license. The truecrypt license is not approved by the FSF or OSI.

Source: [http://brainstorm.ubuntu.com/idea/10062/](http://brainstorm.ubuntu.com/idea/10062/)

---

### Post by heyyy on 2009-07-21
> **dmizer said:**
> If your drive is SATA II and your mainboard SATA controller supports hotswap, not much would happen other than a system freeze.

If your drive is IDE, you would most likely have a non-functional computer. Disconnecting/connecting IDE cables while powered destroys drives and destroys main boards.

IF your drive is SATA II and your brother disconnected it, read it from another system, and plugged it back in, then there would be no logs and no way to prove that this was done.

As to why truecrypt is not in the repos: [s]I'm not positive, but that level of encryption is illegal in many countries outside of the U.S.[/s] Truecrypt is released under their own custom license. The truecrypt license is not approved by the FSF or OSI.

Source: [http://brainstorm.ubuntu.com/idea/10062/](http://brainstorm.ubuntu.com/idea/10062/)

thanks
after some thought i couldn't resist any more and tried it
i put out the hard drive and then back in... nothing happened
everything worked fine and no sign on the log viewer that it happened...
as for truecrypt if it is only a licence thing ill give it a try

---

### Post by bodhi.zazen on 2009-07-21
You are playing with fire if you do that.

A computer is an electrical device and if you are working on the internals trun it off and disconnect it from the power supply.

Otherwise you risk shorting your circuits / motherboard (speaking from personal experience), or worse serious electrical injury or death.

After your fry your first component, and see the sparks and smoke , you probably will not do that again, at least now without proper precautions and personal insulation and a fire extinguisher.

Thread closed.

---

