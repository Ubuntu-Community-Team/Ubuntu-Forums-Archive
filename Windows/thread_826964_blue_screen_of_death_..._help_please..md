---
title: "blue screen of death ... help please."
date: 2008-06-12
forum: Windows
---

### Post by will farbrother on 2008-06-12
Hi, 

I've always been curious about linux, and only today got round to doing some exploring.  So I am totally new to this.

I decided to test Ubunto on an old laptop, so burned the iso on to a CD - using my good laptop.  All that was going well, until I rebooted my good laptop - accidently leaving the Ubunto disk in the drive.

Now when I try to boot the good laptop (An Acer Aspire 4315) it allows me to get as far as the desktop, before flashing the blue screen of death and quickly rebooting.  

I have lots of work on this computer that I cant afford to loose.  All help greatly appreciated.  

My questions are:
1)How can I get windows working properly on my good laptop.
2)Is the ubunto disk I have made ok to use on the old laptop.  

Thanks!

Will

---

### Post by vexingmodstwo on 2008-06-12
Wow.  I'm not even close to being an expert on this stuff but I know how it feels so I at least want to give you some hope.

You say you can get to the desktop, that means you should be able to boot into safe mode.  Have you tried that?

---

### Post by melrom on 2008-06-12
Check the md5 sum of the CD you burned. 

I have no idea why you're getting a BSOD just from leaving a disk in the drive. This might be unrelated to leaving it in. Please provide more details about what happens when you get to the desktop and/or if you're booting into safe mode.

Here is Ubuntu documentation that explains what checking the MD5 sum is:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)


also, here are the hashes for the different isos:
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

also, provide more details as to what the bsod message says. furthmore, doesn't acer, by default, make a backup partition with only data on it?

---

### Post by karellen on 2008-06-12
did you change the boot order from your bios? otherwise it shouldn't be a problem (with the iso you've burned at least), maybe your drive (or its drivers) has issues with Windows

---

### Post by will farbrother on 2008-06-12
vexingmodstwo:  thanks.  I'm in safemode at the moment, I'm just hesitating at the moment (dont want to f*%k this up even more).

Should I just do a system restore?  Or is this more complicated?


melrom: I did the MD5SUM thing after I burnt the ISO.  It was fine.  Is it possible that I did some damage when I aborted the set-up early?

---

### Post by vexingmodstwo on 2008-06-12
> **will farbrother said:**
> vexingmodstwo:  thanks.  I'm in safemode at the moment, I'm just hesitating at the moment (dont want to f*%k this up even more).

Should I just do a system restore?  Or is this more complicated?


melrom: I did the MD5SUM thing after I burnt the ISO.  It was fine.  Is it possible that I did some damage when I aborted the set-up early?

Good!  You're in safe mode.

Now, because I don't want to assist you in messing things up further, I will defer to someone else about the system restore.

My initial thought is that if you have a backup you should be able to restore from within safe mode (which would make sense, but this is windows).

---

### Post by melrom on 2008-06-12
interesting. try a sys restore. 

but first, can you tell me what the BSOD said??

if you don't remember:

```

Start -> Control Panel -> Administrative Tools -> Event Viewer

```

And don't do the sys restore yet.

---

### Post by will farbrother on 2008-06-12
Melrom:
when I get to the desktop when booting into safe mode, it seems to be ok .. I'm just not certain what I should do!  

You asked what the bsod message says. It flashes up for less than a second before switching off; very frustrating. 

"furthmore, doesn't acer, by default, make a backup partition with only data on it?" Yes thats true, do have a partition.  Does that help my situation?

---

### Post by vexingmodstwo on 2008-06-12
> **will farbrother said:**
> Melrom:
when I get to the desktop when booting into safe mode, it seems to be ok .. I'm just not certain what I should do!  

You asked what the bsod message says. It flashes up for less than a second before switching off; very frustrating. 

"furthmore, doesn't acer, by default, make a backup partition with only data on it?" Yes thats true, do have a partition.  Does that help my situation?

Check this out:

[http://www.microsoft.com/windowsxp/using/helpandsupport/getstarted/ballew_03may19.mspx](http://www.microsoft.com/windowsxp/using/helpandsupport/getstarted/ballew_03may19.mspx)

Are you using Vista or XP?

Either way, I think the overall concept is the same.  If you have a "recovery" partition, then you should be able to use the "Last Known Good Configuration" option during boot up.

Read the section in that link that says "Before You Try System Restore"

---

### Post by will farbrother on 2008-06-12
Its XP pro.  

I had a look at event viewer but couldnt see anything there that looked like the message I was getting.  Perhaps I'm not looking in the right place.

---

### Post by will farbrother on 2008-06-12
Tried the "last known good configuration" option - it didnt work.  Same problem.  The desktop is open for about 20 seconds.  The blue error message flashes up (too quickly to read) then it reboots itself.

What should I try next?

---

### Post by vexingmodstwo on 2008-06-12
> **will farbrother said:**
> Tried the "last known configuration that worked option" - it didnt work.

Then you might have to go nuclear.

I'd follow the suggestions on that link I gave you since it is from  MS and then do a system restore if all else fails.

(I'm guessing you are going to backup your important files first, right?)

---

### Post by argail1980 on 2008-06-12
did the ubuntu CD actually DO anything, start to install or so? otherwise i think it could be coincidence that your windows failed. I cannot see what the CD should have done when not changing the system... can anyone else?

when you need your data, try a live CD to get them on an external HD or a stick. (I know, in your place I would not let anything linux-like come near my PC. Maybe you can also apply an external disk in Safe Mode).

---

### Post by vexingmodstwo on 2008-06-12
> **argail1980 said:**
> did the ubuntu CD actually DO anything, start to install or so? otherwise i think it could be coincidence that your windows failed. I cannot see what the CD should have done when not changing the system... can anyone else?


I was actually going to say this.  It seems it was just pure luck that something went screwy while the CD was in since the liveCD shouldn't do anything to the hard drive by simply booting up.

There must have been some pre-existing corruption in the hard drive that just decided to show up at the wrong time.

---

### Post by will farbrother on 2008-06-12
Ok, I am in the process of backing up files ... I have compressed the files I need but dont seem to be able to save them to CDs or attach them to emails in safe mode. 

Is there a better way of backing up files in safe mode? Or do I need to come back later when I've got a flash disk?

---

### Post by will farbrother on 2008-06-12
A couple of people have mentioned that this problem might not be related to my messing up with Ubunto.  

The laptop is 6 months old and has never done anything like this before.  I first got the BSOD as soon as I had left the live CD in the drive. My understanding is that as soon as you reboot with a Ubunto live iso. CD the OS installation process starts.  Because I did this accidently, I turned power of to abort.  As soon as I did that the problems started.  

I google a few phrases and came up with stories like [this... ]("http://www.lockergnome.com/it/2008/03/28/an-experiment-with-ubuntu-gone-wrong/")

Obviously, Ive messed up.  I'd like to get windows working on my Acer and then test Ubunto on my older laptop to see if I like it.  Thanks for all your help so far, a community like this is clearly a major plus point to Ubunto.

---

### Post by vexingmodstwo on 2008-06-12
> **will farbrother said:**
> A couple of people have mentioned that this problem might not be related to my messing up with Ubunto.  

The laptop is 6 months old and has never done anything like this before.  I first got the BSOD as soon as I had left the live CD in the drive. My understanding is that as soon as you reboot with a Ubunto live iso. CD the OS installation process starts.  Because I did this accidently, I turned power of to abort.  As soon as I did that the problems started.  

I google a few phrases and came up with stories like [this... ]("http://www.lockergnome.com/it/2008/03/28/an-experiment-with-ubuntu-gone-wrong/")

Obviously, Ive messed up.  I'd like to get windows working on my Acer and then test Ubunto on my older laptop to see if I like it.  Thanks for all your help so far, a community like this is clearly a major plus point to Ubunto.

Booting from the CD does not start an installation process unless you actually hit the "Install Ubuntu" option when it has finished the initial boot from the CD.

---

### Post by wootah on 2008-06-12
> **will farbrother said:**
> A couple of people have mentioned that this problem might not be related to my messing up with Ubunto.  

The laptop is 6 months old and has never done anything like this before.  I first got the BSOD as soon as I had left the live CD in the drive. My understanding is that as soon as you reboot with a Ubunto live iso. CD the OS installation process starts.  Because I did this accidently, I turned power of to abort.  As soon as I did that the problems started.  

I google a few phrases and came up with stories like [this... ]("http://www.lockergnome.com/it/2008/03/28/an-experiment-with-ubuntu-gone-wrong/")

Obviously, Ive messed up.  I'd like to get windows working on my Acer and then test Ubunto on my older laptop to see if I like it.  Thanks for all your help so far, a community like this is clearly a major plus point to Ubunto.

That's what we are here for! Ubuntu isn't quite perfect (we still have bugs to work out :)) but we really want new users to try it out and not have problems :(

I would try and back up your files on to a flash drive, as I don't think you have burning services while in safe mode. Perhaps the installer was in the middle of partitioning? Probably not--I think that starts later and needs user input at the least.

Maybe try running a scan of the hard drive? My Computer | Right Click C: | Properties | then the Tools tab (if I remember correctly... it's in the somewhere). Maybe on the hard reset, the hard drive wrote some bad data somewhere? I'd try that and a defrag.

I personally don't think you messed up. I don't think the live cd should commence an install if left it--it should just boot into the live environment.

Please let us know if things work out :)

PS: Is that the current behavior? I haven't tried 8.04's live cd. The last one I used was 7.04 and it's default behavior was boot into the live environment. Has this changed?

---

### Post by vexingmodstwo on 2008-06-12
> **wootah said:**
> 

PS: Is that the current behavior? I haven't tried 8.04's live cd. The last one I used was 7.04 and it's default behavior was boot into the live environment. Has this changed?

When I ran the liveCD it went to this options screen where you could choose to "Try Ubuntu without Installing" first and then "Install Ubuntu" second.  You had to pick which one you wanted.

---

### Post by melrom on 2008-06-12
Did you choose anything?

---

### Post by wootah on 2008-06-12
> **vexingmodstwo said:**
> When I ran the liveCD it went to this options screen where you could choose to "Try Ubuntu without Installing" first and then "Install Ubuntu" second.  You had to pick which one you wanted.

Yes and before that was the 'press any key to boot from the cdrom' which I think would probably be a BIOS related thing? If you didn't press any key, it would attempt to boot from the 2nd priority listed device.

If you let the menu count down (30 seconds), it would execute the first option, which was boot into the live environment (on 7.04).

So this behavior has not changed?

---

### Post by mac143_01 on 2008-06-12
If you see the blue screen of death, it means that you have uncompatible devices installed in your PC,.. or your memory cannot function very well...

YOu better remove the memory then clean it up with an eraser... do not use metal or liquid solutions to clean the memory coz it may damage the pins, or the copper part of the memory...

then put back into place your memory...

---

### Post by vexingmodstwo on 2008-06-12
> **melrom said:**
> Did you choose anything?

Are you asking me?  I chose "install ubuntu" but I'm not the one who started the thread.  :)

---

### Post by will farbrother on 2008-06-12
When I accidently ran the ubunto CD it didnt get that far.  So I didnt choose either.  

At the moment, I am trying to run a scan.  I was in safe mode, but it wouldnt let me do a scan without rebooting.  I selected safe mode again on reboot, but now I have been waiting for it to start up properly for 30mins at least.  I have a screen full of:

multi(0)disk(0)rdisk(0)partition(1)/WINDOWS/System32/Drivers/etc 

Was'nt able to make back ups with the flash stick I've just gone out and bought.  Does anyone know how I can back things up in safemode?

Thanks.

---

### Post by vexingmodstwo on 2008-06-12
> **wootah said:**
> Yes and before that was the 'press any key to boot from the cdrom' which I think would probably be a BIOS related thing? If you didn't press any key, it would attempt to boot from the 2nd priority listed device.

If you let the menu count down (30 seconds), it would execute the first option, which was boot into the live environment (on 7.04).

So this behavior has not changed?

I'm not sure what you're asking.

The BIOS part was the same, depending on your boot order.

But once you booted from the CD, you'd get this welcome screen type thing and it would wait until you chose an option.  I am pretty sure there was no timer on that part.

---

### Post by will farbrother on 2008-06-12
It appears to be getting worse.  I am no longer able to get into safe mode.

What would happen if I ran the Ubuntu disk properly now?

---

### Post by vexingmodstwo on 2008-06-12
> **will farbrother said:**
> It appears to be getting worse.  I am no longer able to get into safe mode.

What would happen if I ran the Ubuntu disk properly now?

dude, you might actually have a virus.

SOMEONE with more experience please pipe in here.

---

### Post by karellen on 2008-06-12
> **will farbrother said:**
> It appears to be getting worse.  I am no longer able to get into safe mode.

What would happen if I ran the Ubuntu disk properly now?

don't you have a windows install disk? just in case...:D

---

### Post by wootah on 2008-06-12
> **will farbrother said:**
> It appears to be getting worse.  I am no longer able to get into safe mode.

What would happen if I ran the Ubuntu disk properly now?

Wow. What happens now?

By all means, you *could *run the Ubuntu installer but I'm not sure about saving the Windows partition. Hopefully this hasn't left a bad taste for Ubuntu/linux :(

---

### Post by will farbrother on 2008-06-12
"Hopefully this hasn't left a bad taste for Ubuntu/linux"

Certainly not.   

"By all means, you could run the Ubuntu installer but I'm not sure about saving the Windows partition"

Well its an Acer Aspire im using which seems to have a partition by default.  

I'm getting increasingly worried.  I cant get in to safe mode at all now.

---

### Post by vexingmodstwo on 2008-06-12
> **will farbrother said:**
> "Hopefully this hasn't left a bad taste for Ubuntu/linux"

Certainly not.   

"By all means, you could run the Ubuntu installer but I'm not sure about saving the Windows partition"

Well its an Acer Aspire im using which seems to have a partition by default.  

I'm getting increasingly worried.  I cant get in to safe mode at all now.

In theory, you should be able to boot up using the CD and run Ubuntu off of it without the need to access the hard drive.

But what you'd be able to do after that is not something I would be able to advise you on.

Does anyone know if you can access / mount the windows partition while running the liveCD?

---

### Post by Twitch6000 on 2008-06-12
> **will farbrother said:**
> "Hopefully this hasn't left a bad taste for Ubuntu/linux"

Certainly not.   

"By all means, you could run the Ubuntu installer but I'm not sure about saving the Windows partition"

Well its an Acer Aspire im using which seems to have a partition by default.  

I'm getting increasingly worried.  I cant get in to safe mode at all now.

ok I think i know your problem.It seems you tried to install ubuntu and restarted or did something incorrectly before it finished.Causing issues in the partitions.A way to fix this is to download gparted and delete the ubuntu partition.Then see if the windows partition has a boot flag if not put it there.It should then be fixed.if not use boot and nuke and start all over after backing up your data.

---

### Post by vexingmodstwo on 2008-06-12
> **Twitch6000 said:**
> ok I think i know your problem.It seems you tried to install ubuntu and restarted or did something incorrectly before it finished.Causing issues in the partitions.A way to fix this is to download gparted and delete the ubuntu partition.Then see if the windows partition has a boot flag if not put it there.It should then be fixed.if not use boot and nuke and start all over after backing up your data.

How would he download and install gparted if he can't boot up?

---

### Post by wootah on 2008-06-12
> **vexingmodstwo said:**
> How would he download and install gparted if he can't boot up?
A paradox!

To the op: More details on what happens when you try and start up in safe mode, please :)

---

### Post by will farbrother on 2008-06-12
When I try to open in safe mode I can get to the menu point.  Whenever I select safe mode (and safe mode with commands)from the list, I get to the next stage only.  It freezes at the point where my screen fills with 

multi(0)disk(0)ridisk(0)partition(1)/WINDOWS/system32/DRIVERS/etc

...so can go no further.

---

### Post by will farbrother on 2008-06-12
Whenever I try to boot normally, it tries to do another disk scan.  If I 'press any key' and resume the bootup I get the BSOD about 20seconds after the desktop appears.

Incidently, the disk scan is clear.  But it is only scanning my (C)drive.  I also have a (D) drive.  Perhaps there's a clue there for someone.

---

### Post by wootah on 2008-06-12
> **will farbrother said:**
> When I try to open in safe mode I can get to the menu point.  Whenever I select safe mode (and safe mode with commands)from the list, I get to the next stage only.  It freezes at the point where my screen fills with 

multi(0)disk(0)ridisk(0)partition(1)/WINDOWS/system32/DRIVERS/etc

...so can go no further.

what driver does it freeze on? That might give us a clue?

Is there anything crucial that you need from the Windows partition? If not, I would consider wiping everything and reinstalling XP then Ubuntu. If there is important data, try booting back into the LiveCD and copying the data on to your flash drive.

---

### Post by will farbrother on 2008-06-12
It seems to freeze on Drivers/Mup.sys.

---

### Post by wootah on 2008-06-12
> **will farbrother said:**
> It seems to freeze on Drivers/Mup.sys.

I have seen this one before too. Do you have the Windows cd handy? You can boot off of that and go into the recovery console and try to fix it that way.

Honestly though (as always with Windows OSs), it is probably easier to just format and install again.

Try my above suggestion of booting into the live cd and pulling your data from the Windows partition.

---

### Post by will farbrother on 2008-06-12
"Try my above suggestion of booting into the live cd and pulling your data from the Windows partition."

Im willing to try anything at this point, but what does this actually mean?  

Is the live CD the Ubuntu Iso. i made this afternoon?  If I run that will I be able to access all my files?  I have about 4gig of important work which I MUST save.  I also have about 40gig of music which I dont think I could replace very easily.  Are my files doomed?

---

### Post by twright on 2008-06-12
your live CD should be fine

try this tutorial:
[http://antimalwaresupport.freeforums.org/how-to-rescue-data-from-a-broken-windows-install-t86.html](http://antimalwaresupport.freeforums.org/how-to-rescue-data-from-a-broken-windows-install-t86.html)(note at as it uses the previous version of ubuntu the menu names have changed for the boot menu, just select the top one)

the problem wasn't ubuntu's fault, i can think for 2 causes possible

[LIST]
[*]random chance
[*]if you downloaded a program to burn the CD it might be a virus
[/LIST]

---

### Post by vexingmodstwo on 2008-06-12
> **twright said:**
> your live CD should be fine

try this tutorial:
[http://antimalwaresupport.freeforums.org/how-to-rescue-data-from-a-broken-windows-install-t86.html](http://antimalwaresupport.freeforums.org/how-to-rescue-data-from-a-broken-windows-install-t86.html)(note at as it uses the previous version of ubuntu the menu names have changed for the boot menu, just select the top one)

the problem wasn't ubuntu's fault, i can think for 2 causes possible

[LIST]
[*]random chance
[*]if you downloaded a program to burn the CD it might be a virus
[/LIST]

Yeah, that behavior he's describing sounds a lot like he's been infected with a virus.

---

### Post by will farbrother on 2008-06-12
Thanks for your help tonight.  The library are kicking me out now.  I'll keep trying tomorrow and let you know how I get on.

---

### Post by argail1980 on 2008-06-13
I have no experience with that syntax, but... do you have a RAID? 

> multi(0)disk(0)ridisk(0)partition(1)/WINDOWS/system32/DRIVERS/etc

can this have caused problems?

BTW, there is a nice free cd called "ULTIMATE BOOT CD" it has a bunch of anti-viruses, hard disk cheks, small linux distros and so on. Maybe with that you can check your drive for damage. And maybe there's a linux distro that can mount flash drives.

---

