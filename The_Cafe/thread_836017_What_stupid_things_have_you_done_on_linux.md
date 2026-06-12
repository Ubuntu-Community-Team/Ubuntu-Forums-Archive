---
title: "What stupid things have you done on linux?"
date: 2008-06-21
forum: The Cafe
---

### Post by JayeD on 2008-06-21
My stupidest thing, I always keep my pc muted and only turn on the sound when I need to hear something. Last night I wanted to watch a short video and noticed no sound. I messed with loads of settings and got nothing. I started to get quite annoyed but decided to sleep on it. Came to the pc today and tried again but still nothing. I could swear that on the sound tests I could hear a faint sound but volume adjustments did nothing. I decided to ask for help on the forums. As I was half way through the post I realised that I had my headphones plugged in to the pc. Talk about feeling stupid...

---

### Post by grossaffe on 2008-06-21
After I installed doom3, i was trying to figure out why i couldn't get sound working.  after trying every possible solution it dawned on me... MUTE!#-o

---

### Post by .nedberg on 2008-06-21
Well, I did ```
sudo rm -rf / 
```

I knew what it would do, I just wanted to try it. I was going to reinstall on that machine anyway and had already backed up everything I needed. It got pretty far before it halted and left the machine unusable...

---

### Post by master5o1 on 2008-06-21
I deleted /var


I meant to delete /var/www/* but forgot the 'www/' and just did /var/* XD

---

### Post by ma_nkooo on 2008-06-21
> **.nedberg said:**
> Well, I did ```
sudo rm -rf / 
```

I knew what it would do, I just wanted to try it. I was going to reinstall on that machine anyway and had already backed up everything I needed. It got pretty far before it halted and left the machine unusable...same here.

---

### Post by schauerlich on 2008-06-21
I ran sudo rm -rfv / on an old computer, but it was on purpose. I wanted to see it brick itself. :)

---

### Post by Erik Trybom on 2008-06-21
I decided to turn my USB memory stick into a Debian installer. Got a few steps into the process, then I remembered I had an entire album of photos there that I hadn't backed up anywhere.

By then the process had wiped the partition table. The stick wouldn't mount on any system. Luckily for me there were excellent tools to deal with this kind of situation - testdisk was what finally worked for me. I got all my files back.

Next time I'll hopefully be more careful.

---

### Post by geo909 on 2008-06-21
I was using scp to transfer some project files in my university machines from where I would submit them. The first time I used scp, I didn't type the right command and I started fetching my home folder of the uni machine, overwriting mine here.

 Luckily I am a huge clonezilla fan and I always keep up to date image copys of my internal hard drive, so I restored it.

---

### Post by VChief on 2008-06-21
rm -rf / on a computer I was going to reinstall Linux on anyway and wanted to see what would happened. One problem...forgot to unmount the Windows partition. By the time I remembered, it was too late. I ended up loosing a lot of stuff I really wanted to not lose. Learned my lesson.

---

### Post by geo909 on 2008-06-21
> **leeward said:**
> rm -rf / on a computer I was going to reinstall Linux on anyway and wanted to see what would happened. One problem...forgot to unmount the Windows partition. By the time I remembered, it was too late. I ended up loosing a lot of stuff I really wanted to not lose. Learned my lesson.

That was the first really stupid rm -rf issue mentioned here. The others were on purpose.

---

### Post by Barrucadu on 2008-06-21
Installed PulseAudio when ALSA was working fine. However, Pulse has some really nice features that make it worth the half an hour headache to get ALSA and Flash working with it.

---

### Post by Ultra Magnus on 2008-06-21
Mounted an external hard drive on /home/james/temp and then did rsync /home/james/ /home/james/temp - came back several hours later to find about a dozen recursive backups of my home directory and my external hard drive totally filled up - Didn't lose anything or anything like that but felt incredibly stupid.

---

### Post by %hMa@?b&lt;C on 2008-06-21
i removed /log because I read that logs eventually take up a lot of space.  needless to say i had a bit of difficulty after that :P

---

### Post by MattBD on 2008-06-21
I wiped my diagnostic partition for Windows once when I installed Ubuntu on my Dell Inspiron. As a result I can never again install XP to it. However, in some ways this was a blessing in disguise as it forced me to stop flitting between Windows and Linux and meant I had to use Linux. So in the end it turned out OK. Not that I'd recommend anyone else do so...

---

### Post by Acglaphotis on 2008-06-21
I accidentally erased /home : /

---

### Post by Solicitous on 2008-06-21
Deleted Linux off my system to install Windows....stupid me *bangs head against wall*  It still hurts :(
Actually probably the worst was when I was drunk one night (many years ago) I decided to reconfigure X to support s-video so we could watch music clips on the TV.  Big mistake.

---

### Post by Dark Aspect on 2008-06-22
I once changed permissions on my entire hard drive with sudo nautilus,making the most secure system in the world.So secure I lacked the permission to even boot and log in.I worked with it and got to the GDM screen but I had so many problems I had to finally reinstall,you can read about my fail here:

[http://ubuntuforums.org/showthread.php?t=645769]("http://ubuntuforums.org/showthread.php?t=645769")

I think it hurt my brain when I did that,thats how stupid that was.

---

### Post by erfahren on 2008-06-22
I was practicing using the find command once -- I was trying to find a file I had just named "file1" that I stuck in some directory in my ~/ and move it to ~/temp 
-- I put in "find ~/ file1 -exec mv {} ~/temp" - (forgetting the "-name") 

*everything* in my home got moved into that "temp" folder, and not "neatly" either. (The hidden files got moved out of their correct directories.) It was a serious mess. I ended up just re-installing.

- this was just after I read a post on some forum where the poster said "btw: be careful of using the find command with -exec - it can be very powerful". --- hmmm.... he was right! lol

---

### Post by Rhubarb on 2008-06-22
For me, I forgot to make regular backups of my personal important documents.
Through stupidity, I "sudo srm"ed a directory that I didn't want - took about 8 hours to complete.  When finished I couldn't boot from the hard drive, because it'd managed to overheat and die.
That hard disk is still in a specialist data recovery place.
Thankfully testdisk (and photorec) managed to recover some documents that I had temporarily copied to other computers (and subsequentially deleted).

A friend of mine last week decided to create another user on his Ubuntu 8.04 intsall, he called that new user "admin", and gave that user Desktop user rights (not admin).
Because Ubuntu creates a group of the same name as it's users, and because his login was apart of group admin (that had root privileges).
His own account got downgraded to desktop user.
Meaning no one on his computer had proper admin / root rights.  No sudo, no synaptic, nothing.
I managed to fix most of it up by going into the recovery console.

---

### Post by Lord Xeb on 2008-06-22
Oops >_>

I have done something like that... I went to go and shread an external drive but ended up shredding my own D: and I had no backup or separate patitions for /home....

---

### Post by starcannon on 2008-06-22
Because I was lazy and had a windows nero cd in front of me, and didn't want to dig through email to get my nero linux key out, I tried to burn a cd using virtual box, I have no idea what the he11 went wrong, but when it got to 55% the system froze, when I rebooted my account was all screwed up. I did a lot of obvious stuff to fix it, but in the end it was easier to create a new account, move important data to it, delete the old account, delete the old directory, create new account, and move everything back. /sheesh... lesson learned, don't be lazy, windows can mess up even a linux install lol.

---

### Post by jpkotta on 2008-06-22
I partially deleted /usr.  It still booted up fine, but I couldn't fix it because the package manager was in /usr, and I ended up reinstalling.  Reinstalling sucked hard because I was using Gentoo at the time.

---

### Post by VChief on 2008-06-24
> **geo909 said:**
> That was the first really stupid rm -rf issue mentioned here. The others were on purpose.

Ooooh. Do I win something? :cool:

Technically, the rm was on purpose...I wanted to watch the results since I was reinstalling anyway. Not unmounting Windows first...well, that was just plain stupid.

---

### Post by drjonze on 2008-06-24
I changed a config file, incorrectly I might add, and I did not back it up first. I'd like those 2 hours back.

---

### Post by MattBD on 2008-06-24
I've done the sudo rm -rf / thing too, but that was in a Xubuntu install on VirtualBox (I like to use Linux installs in VirtualBox to mess around with so I can do all the things I wouldn't want to try on my normal desktop for fear of losing data) so it doesn't really count.

---

### Post by GCoffee on 2008-06-24
When I first installed ubuntu/linux i was messing around with every setting I could find.. Of course, being a linux newbie at the time and having a bad luck streak I totally trashed ubuntu and had to reinstall, thankfully my windows partition wasn't deleted..

Other than that it was probably when I removed ubuntu because i had screwed it up again and wondered why my pc wouldn't boot.. I didn't remove grub..

GC.

---

### Post by B61zz13 on 2008-06-24
I messed around /etc/X11/xorg.conf trying to find a way to manually activate my ATI driver (to make a long story short, I was trying to make Compiz work :/).  I had to make a fresh install and lose all my music in my partition.

---

### Post by Greyed on 2008-06-24
> **geo909 said:**
> That was the first really stupid rm -rf issue mentioned here. The others were on purpose.

I can get a tad more convoluted though it isn't Linux.  FreeBSD, same diff,  just don't tell the Linux and FreeBSD zealots I said that.  ;)

I was tasked with writing a script to back up important files from several servers onto a machine dedicated to the task.  This was before I knew about rsync much kess the wonderful tools built on top of it (dirvish).  About, what, a decade ago now?

Anyway while writing this script I would regularly mount the root partition of another machine so as to copy the requisite files into an appropriately named directory.  When the script bombed I'd rm -rf the save directory, tweak my script, run it again.

So imagine a directory with the following entries:

machinea (root of machine A mounted over NFS)
machinea-save (the local directory to which I was saving files)

cd mach<tab><enter>
rm -rf<enter>

Yes, I went into the wrong directory.
No, I wasn't smart enough to mount the root partition of the remote drive as read-only.
No, I didn't prevent root privs from carrying over (I forget the exact name of it)

Aaaand, if that's not enough.

It took me all of 6 seconds to figure out why it was taking so long and CNTL-C.  By that time it had chewed through most of the /dev directory.  Did I mention this was our primary mail machine?  Oh, and I was telecommuting in from home?  At 2am?  :)

I'm sure someone can come up with a more convoluted way of doing an rm -rf / than having an NFS mounted root partition but I have to say it's hard to do so.  ;)

---

### Post by gina88 on 2008-08-07
well not really me, but my friend was looking for blender tutorials then he was magically transported to a fake antivirus thingy...for XP

he dual boots XP and ubuntu, and he made ubuntu look like XP.

at first he felt stupid for forgetting he was on ubuntu, then he laughed so hard he passed it to me...
it even downloaded the installer (in .exe! but he doesn't have wine)

im glad im also on linux or else i'd be freaking out (fake antivirus warnings often are virii themselves)
:lolflag:

---

### Post by Keyper7 on 2008-08-07
In a sleppy, coffeeless, dazed and confused moment I did an fsck... on a mounted partition.

I still have nightmares about that day.

---

### Post by crazyfuturamanoob on 2008-10-26
I bought a 4.7Gb DVD-R last week.

Burned 1.5Gb onto it. Forgot to burn another 300Mb.
DAMN! Couldn't add data because it was **DVD-R**, not **DVD+R**! ](*,)

And so I lost that 3.2Gb. :(

---

### Post by Lord Xeb on 2008-10-26
Oh god, the list is endless. I will just mention a few:

Deleting my desktop.
Locking my self out of the computer
Deleting /etc
deleting /
messing with my fan and turning it off e_e

---

### Post by Luffield on 2008-10-26
The first computer I installed Ubuntu on had a 3gb hard disk. I dist-upgraded and ran out of disk space midway :-\

Another thing: I had gutsy-backports enabled when I was using gutsy beta before the release :D I don't think any damage was done, but it was just so silly!

---

### Post by sixstorm on 2008-10-26
I have a little too much free time online so I find all these cool features/apps for Linux.  When I install them, something else tears up and it makes me have to reinstall the OS.  Not so much now as I know better, and 8.10 is really good and stable.

---

### Post by jimi_hendrix on 2008-10-26
i just installed arch and i couldnt get internet for an hour...then i realised i never installed the chipset driver or any of the core packages...talk about a lightweight install

on a related note when i got internet and i installed X and began to configure it i messed up my config and had to reboot...but now i couldnt get internet even with the driver installed...i reinstalled arch and the same thing happened after i began to configure X...im sure theres a really dumb reason why this is happening but i cant find it

---

### Post by OutOfReach on 2008-10-26
I did:
```

sudo rm -rf /*

```
(Don't do that, kids^)

While I meant to do:
```

sudo rm -rf */

```

Unknowing that I did the first command I watched more than a dozen lines go by before I Ctrl+C'ed. I checked the filesystem and it appeared that nothing (important) was deleted. I restarted and nothing was out of the usual. This was about a month ago.

---

### Post by SakJur on 2008-10-26
Oh, wonderful topics :D
Well, I think the worst thingy I've ever done is probably something in style with DistUpgrade canceling :D

---

### Post by NullHead on 2008-10-26
Compiled a kernel with out sata drivers ... then tried to fix it (not knowing there were literally no drivers) broke the system even more.

---

### Post by Dr Small on 2008-10-26
Ran:
```
sudo rm -R /boot
```

When I meant to run:
```
sudo rm -R boot/
```

I had a copy of /boot in my $HOME directory, and ran the command wrong. Since there is soo little in /boot, it just about instantly wiped it clean. I was able to recover from it without reinstalling, thankfully.

---

### Post by markp1989 on 2008-10-26
when following this guide [http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=6038376](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=6038376)

at the end  i typed "sudo rm -r ${DEST}/*" in to a new terminal, where dest hadnt been set, by the time i relized most of /dev was gone, and i couldnt boot

---

### Post by Flynn555 on 2008-10-26
> **.nedberg said:**
> Well, I did ```
sudo rm -rf / 
```

I knew what it would do, I just wanted to try it. I was going to reinstall on that machine anyway and had already backed up everything I needed. It got pretty far before it halted and left the machine unusable...

lol i think im gonna try that when i get home...

will this do the same thing?
```

sudo rm -rm /*

```

---

### Post by jimi_hendrix on 2008-10-26
check the global sticky...theres a load of things to try :wink:

---

### Post by smartboyathome on 2008-10-26
I forkbombed myself :p

---

### Post by schauerlich on 2008-10-26
> **smartboyathome said:**
> I forkbombed myself :p

Who hasn't? :)

---

### Post by billgoldberg on 2008-10-26
Not really a linux thing, but still.

When I bought this pc it came with Windows Vista.

I knew I was going to remove it the same day so I loaded it up with some viruses and some other nasty things to trash it.

I pulled out my Ubuntu disks and tried to install it.

It wouldn't boot from cd.

I thought I had badly burned it so I tried some other linux distro's I had laying around.

Nothing worked.

I tried another cd rom drive from an old computer, didn't work either.

I spend around two weeks getting help from the PB helpdesk (totally useless btw) and various forums.

It turned out that the drive it came with and the spare drive were bought broken.

--

Stupid linux things I did?

I bricked my share of installs doing various stupid things.

Thank Jebus for back ups.

---

### Post by Dr Small on 2008-10-26
> **EDavidBurg said:**
> Who hasn't? :)
Me.

---

### Post by jimi_hendrix on 2008-10-26
> **Dr Small said:**
> Me.

same here...

---

### Post by schauerlich on 2008-10-26
> **Dr Small said:**
> Me.

Oh, well, you're no fun. :)

Nice hat.

---

### Post by Tux.Ice on 2008-10-26
I had 2 hard drives on a table. The one on the left had my data on it. I was gonna install it in my computer the next day. The other one was scrap.

I went to sleep.

I woke up, installed a drive, and cut the other one in half with a bandsaw. Then i booted to a blank drive. 

Cut the wrong drive in half. Had no backups. LOst all data.

/action facepalms

---

### Post by Lord Xeb on 2008-10-26
I forkbombed myself. I just let the system sit there for about an hour to see how hot it would get. O_________O DO NOT DO! It got to like almost 195F!

---

### Post by jimi_hendrix on 2008-10-26
why saw it in half if its blank?

---

### Post by Old_Grey_Wolf on 2008-10-26
I got a new laptop. Knowing that wireless support for Linux is poor, it didn't surprise me that the wireless didn't work. I spent hours trying different things to get the wireless to work. Then I discovered there is a switch on the front of the laptop that disables the wireless card. Flipped the switch from 0 to 1 and everything was working.
:lolflag:

---

### Post by snova on 2008-10-26
> **jimi_hendrix said:**
> why saw it in half if its blank?

To find out what's inside?

> **EDavidBurg said:**
> Oh, well, you're no fun. :)

Nice hat.

Agreed. What is it?

Anyway, among other things I've done, here's a good story:

At one point I was trying to make a backup. I copied a large folder of pictures... and stopped it midway through because I changed my mind about how I was going to do it. So I deleted the ones it had finished copying... and lost about half of them all because I used cut and paste and not copy and paste (that is, it deleted the source files after it copied them).

A few weeks ago, I went to make a backup again... and somehow managed to delete the rest of them.

I seem destined not to have pictures. :) Fortunately I only rarely use my camera.

---

### Post by chris4585 on 2008-10-26
I did...

```
chmod -R o-rw /*
```

I meant to do

```
chmod -R o-rw Backgrounds/*
```

felt stupid after words

---

### Post by teaker1s on 2008-10-26
diving in and trying various guides,without first reversing the changes of the previous guides-when I first started. Worse still tried changing ubuntu to debian by changing repositories=broken but kept both halfs:)

---

### Post by Eisenwinter on 2008-10-26
I once deleted my home directory, trying to prove to my friend on IRC that doing rm -rf / will do absolutely nothing as a regular user.

Owned myself. :lolflag:

---

### Post by jimi_hendrix on 2008-10-26
> **chris4585 said:**
> I did...

```
chmod -R o-rw /*
```

I meant to do

```
chmod -R o-rw Backgrounds/*
```

felt stupid after words

what does that do?

---

### Post by JohnFH on 2008-10-26
> **Eisenwinter said:**
> I once deleted my home directory, trying to prove to my friend on IRC that doing rm -rf / will do absolutely nothing as a regular user.

Owned myself. :lolflag:

LOL!  Brilliant - that one made me laugh out loud!

This morning (yes, just this morning) I panicked because my PC wouldn't boot.  It would just sit there doing nothing before even getting to the grub prompt.  I took a deep breath and told myself not to panic as it was working fine yesterday.  Opened the case and removed various connectors one by one - hard drives, etc.  No luck.  The hard drives seemed ok as the BIOS recognised them, so I was a bit stunped until I noticed something sticking out of the front of the PC - my USB stick!  I had configured the BIOS to boot from USB before hard drives!  The thing is, I've done that before!

---

### Post by chris4585 on 2008-10-26
> **jimi_hendrix said:**
> what does that do?

Changed permissons (-R) recursively so other users can read and write, it wasn't too hard to fix

oops!

---

### Post by Dr Small on 2008-10-26
> **EDavidBurg said:**
> Nice hat.

> **snova said:**
> Agreed. What is it?


Thanks. I think it is a "Russian Bomber Hat" type thing. Made of fur, and is really warm. It has the flop down ears on it for extra warmth. This is my favorite winter hat.

---

### Post by nixscripter on 2008-10-26
> **jpkotta said:**
> Reinstalling sucked hard because I was using Gentoo at the time.

I suppose it's too late to say "untar portage again and remerge to fix it"...

My stupid thing: I had a bunch of empty directories, and full directories. So I decided to prune the empty ones with **rm -d *** and save a lot of typing. Unfortunately, I also had several dozen files in the top level directory, so they were gone too. Whoops.

It should be clear from this thread: if anyone out there isn't doing regular backups, start.

---

### Post by OutOfReach on 2008-10-26
> **JohnFH said:**
> 
This morning (yes, just this morning) I panicked because my PC wouldn't boot.  It would just sit there doing nothing before even getting to the grub prompt.  I took a deep breath and told myself not to panic as it was working fine yesterday.  Opened the case and removed various connectors one by one - hard drives, etc.  No luck.  The hard drives seemed ok as the BIOS recognised them, so I was a bit stunped until I noticed something sticking out of the front of the PC - my USB stick!  I had configured the BIOS to boot from USB before hard drives!  The thing is, I've done that before!

LOL. This always happens to me when I leave my iPod connected (to recharge). The first I got this (Actually I didn't get this, my mother did) I was like 'wtf?' and it was an hour before I finally realized that it was my iPod causing the problem.

---

### Post by jimi_hendrix on 2008-10-26
> **nixscripter said:**
> 
It should be clear from this thread: if anyone out there isn't doing regular backups, start.

thats me...

---

### Post by snova on 2008-10-27
Rsync and an external hard drive works well.

---

### Post by Zyphrexi on 2008-10-27
deleted /boot from the wrong drive. manually had to create a new /boot, and it's still working as it's my current install.

when I began using ubuntu, I was new to the 'repository' concept, and replaced all of the ubuntu repos with debian ones, and I dist-upgraded. Somehow, again, I managed to fix it without a complete reinstall.

I'm beginning to think I'm a genius.

---

### Post by Sponzenbroekske on 2008-10-27
> **leeward said:**
> rm -rf / on a computer I was going to reinstall Linux on anyway and wanted to see what would happened. One problem...forgot to unmount the Windows partition. By the time I remembered, it was too late. I ended up loosing a lot of stuff I really wanted to not lose. Learned my lesson.

HARD!!

Well you got rid of windows, gotta stay positive :p
I'll think I'll never try that command :p
And then the most stupid thing on linux...
lets think....
euh... still thinking about it....
yeah I removed gnome while I was active in gnome, you see it fade away and you can't do **** :p (I had KDE)

---

### Post by Mason Whitaker on 2008-10-27
Installed Ubuntu on a full Partition and deleting my Windows Ultimate. 
Now this doesn't sound like a bad idea untill you realize that I forgot to save my files from Windows, losing about two years worth of files.

---

