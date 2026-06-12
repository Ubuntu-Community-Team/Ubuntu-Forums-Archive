---
title: "I cant belive it, everything is gone..."
date: 2008-07-18
forum: The Cafe
---

### Post by MONODA on 2008-07-18
recently I had decided to try out freebsd on the fourth partition of my hard drive. When I got to th par about configuring the network it didnt get my configuration right with dhcp so I canceled sysinstall- actually theres no point of me telling the whole story, the point is, I was stupid and didnt make a backup of my fiels anywhere and now I have ruined all my partitions and destroyed all my datawhich I had acumulated over 6 years. I was running arch linux happily but now I would like to take this as a chance to try out something new, what woud you recommend I do at this time? What would you do in my position? thanks.
PS. I am typing on a mac keyboard which I am not used to so sorry for spelling mistakes :P.

---

### Post by myusername on 2008-07-18
wow dude that sucks...i hate it for you

---

### Post by Jon Monreal on 2008-07-18
> **MONODA said:**
> recently I had decided to try out freebsd on the fourth partition of my hard drive. When I got to th par about configuring the network it didnt get my configuration right with dhcp so I canceled sysinstall- actually theres no point of me telling the whole story, the point is, I was stupid and didnt make a backup of my fiels anywhere and now I have ruined all my partitions and destroyed all my datawhich I had acumulated over 6 years. I was running arch linux happily but now I would like to take this as a chance to try out something new, what woud you recommend I do at this time? What would you do in my position? thanks.
PS. I am typing on a mac keyboard which I am not used to so sorry for spelling mistakes :P.

Trying something new? I generally do that it a Virtual Machine. It makes the process faster and easier (and it won't brick your machine as freebsd did).

You could use this to experiment with a number of distros and other OSes (such as Solaris, Haiku, anything you want to experiment with).

Hope things get better for you.

---

### Post by p_quarles on 2008-07-18
Well, if you want to recover your files, try using a recovery boot disk with testdisk. 

As far as what to try next, give Slackware a shot.

---

### Post by MONODA on 2008-07-19
> (and it won't brick your machine as freebsd did).
freebsd didnt break my machine, I did...

> Well, if you want to recover your files, try using a recovery boot disk with testdisk.

As far as what to try next, give Slackware a shot.
that woudldnt work since while trying to install the packages, th freebsd installer didnt know where to install the files (since I did not secify where) so it kinda mergedthem I guess, that is what it looked like in gparted. I have already tried slackware, I guess I wont be needing to try anythin new since I already have tried almost everything.
EDIT: I am going to install freebsd, might as well...

---

### Post by phidia on 2008-07-19
I would still recommend [System Rescue CD]("http://www.sysresccd.org/Main_Page") and you did say you were installing to the 4th partition-freebsd should not have overwritten your other partitions-maybe the data is still there but the partition table isn't readable? It can't hurt to try the system rescue cd right?

---

### Post by PrimoTurbo on 2008-07-19
I would probably try BSD. But first if the partition table is gone, it might be possible to recover some data is it hasn't been overwritten.

Every few months I do a partial important file backup, things like personal pictures, configurations, documents etc. Things that would be impossible to replace or very difficult. Then I do a media backup every couple of times a year, but media is easy to get back.

---

### Post by Jim! on 2008-07-19
Damn man that sucks, but hey at least now you'll get to learn a new OS! I say give freeBSD or Open Solaris a shot, or openSUSE (GNOME version)...

---

### Post by MONODA on 2008-07-19
> I would still recommend System Rescue CD and you did say you were installing to the 4th partition-freebsd should not have overwritten your other partitions-maybe the data is still there but the partition table isn't readable? It can't hurt to try the system rescue cd right?
i tried that at first but it didnt help. I dont need help recovering my information, I know what happened and that it is impossible to recover the data, I am not going to share the story (unless lots of people ask) since it is quite difficult to explain to someone who wasnt there.

---

### Post by aktiwers on 2008-07-19
That really sucks man! I have about 6-8 years of data on my machine as well.. I can imagine the pain..
I would like to hear the story.. maybe some smart boys knows a way to save the files. It is possible often, I have done it a few times myself.

---

### Post by rectec794613 on 2008-07-19
Well I can't tell you how many times my system messed up and I had to reinstall lol:) There is a data recovery tool you can use on Ubuntu to get your files back. But...

I, don't think there's a GUI. DUN DUN DAAA!:evil:
But that shouldn't be a problem for you non-n00bs=D>

---

### Post by rectec794613 on 2008-07-19
[Try This]("https://help.ubuntu.com/community/DataRecovery")
I haven't read it, but it seems legit;)

---

### Post by MONODA on 2008-07-19
I just found out that I have all of my really important docs on a usb flash drive that I just found :D and i can get all my music from a friend who listens to the same music (that isnt illegal right?) The rest of my files arent really important, I mean, you dont need to watch sam mcguffy jum over 10 trucks a million times :P. However it will be somewhat of a pain to get back that collection of 50 OSs (solaris bsds linuxs haiku minix syllable etc) that I had. I will also miss my really organized /home structure, it will never be the same again lol. 

Anyway, now that I have finally passed through the shock period :P I can tell the story of what happened. 

I had arch / on sda1, /home on sda2 and swap on sda3. I had 40 gigs of blank space which I intended on using for Freebsd. Once the base installation had finished, I was confiuring my network to dhcp but it didnt work for some reason so I rebooted my computer to restart sysinstall (i would be easier to understand why I did this for someone who has already installed freebsd before) I continued configuring my netowrk nd got it to work and then went on to install packages from the bin packages. I selected only two packages, vim tiny and pico. I had forgotten to select which drives to install these on so the installer got confused and apparantl merged the partitions into one unreadable patition (that is what it looked like from system rescue cd a least). When I saw what I had done, i really just didnt believe it. I have done things much worse to my computer (as far as software goes) but never had anyting like this happened. I tried super grub, gparted, and a few other live cds to no avail :'(. But it is fine now, i have all my most important files and it is nice to start fresh.

---

### Post by songshu on 2008-07-19
if you still want to recover give testdisk a try, i had some good results.


once i tried formatting a usb, but apparently formatted the wrong mount point :(
actually i did not notice it because my boss (yes, feel the pain?) until two weeks later because i rebooted the machine and everything was gone.

i tried a live-cd with testdisk and recovered it all, just some routine maintenance i told my boss ;)

---

### Post by MONODA on 2008-07-19
thanks, I will check that out

---

### Post by Barrucadu on 2008-07-19
If all the data was truely and completely gone, in that situation I would scream, punch a wall (I have lots of hard-to-replace files on my computer), and try something new like Slackware, Gentoo, or LFS.

---

### Post by PrimoTurbo on 2008-07-19
I'm still under the impression that you can probably recover everything. However it might not be worth it, you would need to examine the source code of the installer and figure out what exactly it did to the partitions to proceed.

---

### Post by songshu on 2008-07-19
> **PrimoTurbo said:**
> I'm still under the impression that you can probably recover everything. However it might not be worth it, you would need to examine the source code of the installer and figure out what exactly it did to the partitions to proceed.


there is no need to look at the source code of the installer, because it simply did what it needed to do, and that is formatting the drive you selected.

as long as there is nothing written OVER the formatted part you still have a chance on recovery

---

### Post by Exsecrabilus on 2008-07-19
> **MONODA said:**
> recently I had decided to try out freebsd on the fourth partition of my hard drive. When I got to th par about configuring the network it didnt get my configuration right with dhcp so I canceled sysinstall- actually theres no point of me telling the whole story, the point is, I was stupid and didnt make a backup of my fiels anywhere and now I have ruined all my partitions and destroyed all my datawhich I had acumulated over 6 years. I was running arch linux happily but now I would like to take this as a chance to try out something new, what woud you recommend I do at this time? What would you do in my position? thanks.
PS. I am typing on a mac keyboard which I am not used to so sorry for spelling mistakes :P.
Has it come to your realization that:
[LIST]
[*]We don't know you.
[*]You don't know us.
[*]We don't know us.
[*]We don't care about your problem.
[*]There's nothing we can do about it.
[*]You need to learn from this mistake, buy the book *Computers & Operating Systems for Dummies* and try not to be so ignorant next time.
[/LIST]

---

### Post by init1 on 2008-07-19
> **MONODA said:**
> I just found out that I have all of my really important docs on a usb flash drive that I just found :D and i can get all my music from a friend who listens to the same music (that isnt illegal right?) The rest of my files arent really important, I mean, you dont need to watch sam mcguffy jum over 10 trucks a million times :P. However it will be somewhat of a pain to get back that collection of 50 OSs (solaris bsds linuxs haiku minix syllable etc) that I had. I will also miss my really organized /home structure, it will never be the same again lol. 

Anyway, now that I have finally passed through the shock period :P I can tell the story of what happened. 

I had arch / on sda1, /home on sda2 and swap on sda3. I had 40 gigs of blank space which I intended on using for Freebsd. Once the base installation had finished, I was confiuring my network to dhcp but it didnt work for some reason so I rebooted my computer to restart sysinstall (i would be easier to understand why I did this for someone who has already installed freebsd before) I continued configuring my netowrk nd got it to work and then went on to install packages from the bin packages. I selected only two packages, vim tiny and pico. I had forgotten to select which drives to install these on so the installer got confused and apparantl merged the partitions into one unreadable patition (that is what it looked like from system rescue cd a least). When I saw what I had done, i really just didnt believe it. I have done things much worse to my computer (as far as software goes) but never had anyting like this happened. I tried super grub, gparted, and a few other live cds to no avail :'(. But it is fine now, i have all my most important files and it is nice to start fresh.
Although you stated that you weren't interested in data recovery, there's an app called Photorec that will recover files, no matter how messed up your disk is. Even if you have already installed another OS on it, you might be able to get some of it back. The RIP live CD has it. 
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://ftp.leg.uct.ac.za/pub/linux/rip/](http://ftp.leg.uct.ac.za/pub/linux/rip/)

Edit:
Yeah I found the FreeBSD installer very confusing too. All that work, and then it didn't recognize my NIC.

---

### Post by days_of_ruin on 2008-07-19
> **Exsecrabilus said:**
> Has it come to your realization that:
[LIST]
[*]We don't know you.
[*]You don't know us.
[*]We don't know us.
[*]We don't care about your problem.
[*]There's nothing we can do about it.
[*]You need to learn from this mistake, buy the book *Computers & Operating Systems for Dummies* and try not to be so ignorant next time.
[/LIST]
Speak for yourself.

---

### Post by sports fan Matt on 2008-07-19
Sorry to hear that mate.  Been there numerous times and I know how much of a pain it is to reinstall things

---

### Post by Ozor Mox on 2008-07-19
> **Exsecrabilus said:**
> Has it come to your realization that:
[LIST]
[*]We don't know you.
[*]You don't know us.
[*]We don't know us.
[*]We don't care about your problem.
[*]There's nothing we can do about it.
[*]You need to learn from this mistake, buy the book *Computers & Operating Systems for Dummies* and try not to be so ignorant next time.
[/LIST]

Has it come to your realisation that:
[LIST]
[*]This person did not ask for sympathy.
[*]The people who replied apparently do care somewhat.
[*]If you don't care, you might consider not posting instead of posting some arrogant, elitist drivel because this person made a genuine mistake.
[/LIST]

I have years and years of data on my computer that if I lost I would feel exactly like the OP does. More than once I have felt that horrible sinking feeling when my computer has failed to boot, or has found corrupted data on the hard drive.

---

### Post by Miguel on 2008-07-19
If you haven't installed anything yet, you may wan to give [Zenwalk](http://zenwalk.org/) a go. Xfce by default, based on slackware plus a dependency-solving package manager. I must admit though I haven't tried it, but I have read some good stuff on the net. In any case, as you've used Arch Linux, you probably don't want to give up rolling releases. Some options include Debian Testing (it's good, although it will be somewhat frozen in the coming months) and Gentoo. Obviously, you may want to keep Arch, as pacman is pretty good and ABS simply rocks.

---

### Post by hockey97 on 2008-07-19
ughh!! I can feel your pain, I had just a month ago got my particians screwed up and had to restart all over all my website work was gone which I spent a year working on that. 

I am currently in the proccess of buying a external hard drive to make a copy my make working partician.

---

### Post by karellen on 2008-07-19
> **Exsecrabilus said:**
> Has it come to your realization that:
[LIST]
[*]We don't know you.
[*]You don't know us.
[*]We don't know us.
[*]We don't care about your problem.
[*]There's nothing we can do about it.
[*]You need to learn from this mistake, buy the book *Computers & Operating Systems for Dummies* and try not to be so ignorant next time.
[/LIST]

I'm very tempted to act according to your sig ;)

---

### Post by matthew on 2008-07-19
> **Exsecrabilus said:**
> Has it come to your realization that:
FYI, to all other thread participants...

I have issued an infraction for this post. I'm leaving it here as it has been quoted and replied to by multiple people, and removing it would require me removing lots of other posts. From this point on, though, we can ignore it.

To the OP: bummer. That stinks. I've done things like that. It happens, and has helped me learn to backup often. Sorry about the pain. Have fun with a new OS toy, whatever you choose to try out.

---

### Post by BwackNinja on 2008-07-19
+1 for all the suggestions for using testdisk

I've been able to recover everything from a broken (not just corrupted) hard drive with it (though it took awhile because the hard drive was broken and didn't want to keep being read after a certain point, so I had to do things folder by folder so I could just reboot and continue when it stopped.) You are also able to rewrite your partition table using testdisk, so that's a plus as well. Not only might you be able to retrieve your data, but you may even be able to use your computer just like it was before it was borked without much work.

---

### Post by richg on 2008-07-19
That is tough. Sorry to hear about it. I lost a hard drive about five or six years ago so I know it is tough to lose data that took a lot of hard work to write.

I decided that would not happen again. I installed a hard drive rack in my desktop. I have six hard drives, no dual boot, no Windows or Gates. No problems. One hard drive, one OS. I have read many horror stories where someone messed up their hard drive so I took steps to keep that from happening.
I have an external hard drive for all my files. I keep a second hard drive configured with Ubuntu 8.04 just like the primary hard drive that has Ubuntu 8.04. If the primary one fails, I can be back on in a few minutes.
The other hard drives are for playing with a different OS though I am not very good at playing with an OS.
I use to think that the "other" guys hard drive will fail and found out someone was thinking the same thing. I hope those of you who have a lot of data and will take note of MONODA and be prepared.

Cheers

Rich

---

