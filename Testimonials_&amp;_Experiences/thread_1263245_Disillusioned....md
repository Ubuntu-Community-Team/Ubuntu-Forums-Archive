---
title: "Disillusioned..."
date: 2009-09-10
forum: Testimonials &amp; Experiences
---

### Post by kevinatkins on 2009-09-10
The title says it all..

So here's the story.. bear with me..

Way back in 2003, I was running Windows 9x. Busy with my studies, I grew tired of the constant 'BSODs' and general instability - trying to get my work done, I was often rebooting 3-4 times per day. 

By chance, I happened on Mandrake Linux on a magazine cover disc; figuring I had nothing to lose, I installed it and was rewarded with an operating system that, at last, just dropped into the background and did its job. Sure, back then there were a few hardware issues, notably the old dial-up modem drivers that needed compiling from source, but it was a learning experience, and fun, too. But once that system was set up, it worked beautifully; I was firmly gripped by the possibilities of this new, open-source operating system.

So, eventually I tried a few alternatives to Mandrake / Mandriva, finally settling on Ubuntu, back at 5.04...

During the passage of time, I've stuck with Ubuntu, but my computing needs have grown, too. 

I have a number of customers, and often need remote access to sites; this has been generally successful, using VPN access, but over the last 18 months or so, there have been regressions - stuff that used to work, no longer does... And network browsing in a Windows domain environment - used to work nicely, no longer does (for at least the last year or so, despite bug reports)

So regressions are one thing. But what I cannot tolerate is basic flakiness. Today, after some updates, I've had to reboot at least six times. The machine just freezes.. I've run hardware checks, I've fsck'd the filesystems, there's nothing wrong; being a dual-boot rig, I'm now running MS Vista and it's good as gold.. go figure.

I guess this is the straw that's about to break the camel's back - I've noticed more general instability, regressions and flakiness with Ubuntu over the last 12 months or so. 

I came to Linux as a result of unreliability of MS Windows. But today, in need of getting my work done, I ended up using a machine running a beta of Windows 7. Guess what, it ran perfectly, without hitch. Looks like, for me, things might be coming full circle - and yes, with Windows 7, Ubuntu really is going to have a fight on its hands.

Failing that, I might just go 'back to the source' and stick Debian on my machine - at least that really is solid....

---

### Post by yabbadabbadont on 2009-09-10
Before all the, "I update all the time and it works perfectly", crowd gets here (;)), I think that trying out the stable branch of Debian might just be what you need, given your requirements.

(Dang, how many commas does one sentance need?  :lol:)

---

### Post by aesis05401 on 2009-09-10
I am running deb stable now on my essential machines and also recommend it to the OP.  One question I have, though.  You are running LTS, right?  The incremental releases have been getting flakier because there are a lot of things changing under the hood.  

My understanding is that they are trying to get a lot into the pipeline as they head toward the next LTS release.

Anyhow, I hope you find a solution to your frustration via Ubuntu, deb stable, or MS.

---

### Post by kreggz on 2009-09-10
I noticed it says in your user prefs that your using Jaunty, maybe I am wrong. Perhaps stick with Ubuntu 8.04.3 LTS and turn off pre-released updates.

Also, you can be selective about your updates e.g security updates first and anything else download when your ready. This is the case with Windows as well.

---

### Post by Hallvor on 2009-09-11
> **kevinatkins said:**
> 
Failing that, I might just go 'back to the source' and stick Debian on my machine - at least that really is solid....

If you want stability, you could try Debian Lenny. It is kind of dull and the software isn`t the latest and greatest, but it is incredibly stable and you don`t have to spend time fixing things. It is ideal for a production system.

---

### Post by Marflus on 2009-09-11
> **kevinatkins said:**
> with Windows 7, Ubuntu really is going to have a fight on its hands.

You say that as if Ubuntu is currently the leading OS worldwide :P

More on topic, people on this thread have got it right, really. There are plenty of stable linux distros you could opt for - Debian being a fantastic choice in my opinion, or you could go to Windows 7. From what I've seen it looks like a big improvement on Microsoft's other recent efforts, so I'm sure you'll do fine by it.

---

### Post by moster on 2009-09-12
I must tell something too.
I installed Ubuntu 9.4 on EeePC. Everything worked except Wlan. After few day of fiddling and reinstalling I finally get it to work. After few more days kernel update came and brake wlan again. I again reinstall and again it worked but I am really dissapointed. 

No way I would install Ubuntu 9.4 on production machine after that. Can someone tell is something like this happening on LTS? I do not want to install Debian.

---

### Post by SeePU on 2009-09-12
Did you ask about wlan in the wireless section?

What type/brand is your wireless card?   Unless it's Broadcom, there's probably a good solution.

---

### Post by 3rdalbum on 2009-09-12
Ubuntu does not have a "fight" on its hands.

The people using Linux with no problems are not going to switch to Windows 7 just because "it's said to be somewhat better than Vista".

I've got Windows 7, and I've used Vista a reasonable amount. Vista is alright. Windows 7 is Vista with a different taskbar - that's what it comes down to. Ubuntu is continually getting better in an evolutionary manner - it's not like Jaunty is reputed to be a terrible release.

Most people use Linux because they like Linux, not because they dislike Vista.

---

### Post by 3rdalbum on 2009-09-12
> **moster said:**
> I must tell something too.
I installed Ubuntu 9.4 on EeePC. Everything worked except Wlan. After few day of fiddling and reinstalling I finally get it to work. After few more days kernel update came and brake wlan again. I again reinstall and again it worked but I am really dissapointed. 

No way I would install Ubuntu 9.4 on production machine after that. Can someone tell is something like this happening on LTS? I do not want to install Debian.

On any Linux distribution if you compile a kernel module from source code and then update your kernel, the old module will not work with the new kernel. This is normal behavior unless you register your module with DKMS, which will automatically rebuild the module on every kernel update.

Wireless drivers take, what, thirty seconds to rebuild? Just run make and sudo make install and you're done.

The idea is to install Linux on compatible hardware, which means all needed drivers are already in-kernel and will be supported by every subsequent new kernel that you install.

---

### Post by DJonsson2008 on 2009-09-12
>The idea is to install Linux on compatible hardware, which >means all needed drivers are already in-kernel and will be >supported by every subsequent new kernel that you install.

That's a good point.

On Ubuntu I've found though that KDE Konqueror 
goes a long way to helping with LAN drive mapping 
issues.

KDE mountconfig is also an indespensible LAN mapping
and drive mounting tool.

These 2 items give considerable leverage.

Some other tips.

* dual-booting may not be the best idea

* with the price of 2nd hand HD's starting 
  at about 20$ its easy enough to keep a rollback 
  Ubuntu OS drive backup ready to go, this redundancy
  is vital in any production environment, if you don't
  want to loose valuable worktime time due to a crash 
  or other problem.

I'm still on 8.04 LTS, even though it is trailing with
video card support its a good OS for daily office needs.

Skype and HD video editing is what drives me to Windows,
and I'd like better LAN printer support with Ubuntu,
otherwise though Ubuntu does the job.

---

### Post by kevinatkins on 2009-09-13
Thanks for all the replies folks.. Well, I feel like a silly billy now - it turned out to be a weird hardware issue on my machine - at least, that's what I think.

Thing is, on this particular machine, I dual boot with Vista (well, I don't often boot into Vista in fact) and when Ubuntu (9.04) started freezing, etc, I booted into Vista, no problems at all. Now, Vista is on a physically separated hard drive in the machine. Anyway, thinking nevertheless that it might be hardware related, I left Memtest86 running overnight - no problems found; I ran a disk surface scan on the Ubuntu drive - no problem found..

Anyway, cut a long story short, I tried installing Debian, and that started exhibiting the same behaviour. Vista remained fine. So I'm thinking at this point that it had to be to do with the hard drive (SATA)... Well, in desperation, I just decided to open the machine up, give it a good clean, re-seated memory and all connectors, and re-installed Ubuntu. And it's been running absolutely fine ever since, for the last 24 hours without hitch. The only sensible possibility I can think of is that perhaps it was a memory issue - the machine is fairly low-grade with shared nVidia graphics, and I don't think Memtest checked the shared memory bit? And that perhaps Vista wasn't addressing the memory locations which were causing problems? I dunno...

Anyway, it's sorted, and Ubuntu is back on (in spite of my grumblings.. do I feel like a prat now or what?!)

---

### Post by moster on 2009-09-13
> **3rdalbum said:**
> On any Linux distribution if you compile a kernel module from source code and then update your kernel, the old module will not work with the new kernel. This is normal behavior unless you register your module with DKMS, which will automatically rebuild the module on every kernel update.

Wireless drivers take, what, thirty seconds to rebuild? Just run make and sudo make install and you're done.

The idea is to install Linux on compatible hardware, which means all needed drivers are already in-kernel and will be supported by every subsequent new kernel that you install.

I did not  compile anything. I had to add *blacklist acer_wmi* to */etc/modprobe.d/blacklist* for my wifi to work. That is all. But week after that, update came and wlan stop working. I did reinstall again and update it all and then blacklist again and now it work. But I would not bet my money how long it will work. We can argue, but this is not way for doing business. There is no point in repairing(updating) one thing and damaging another.

Sorry everybody for carry out my own problems in this thread.

---

### Post by K7522 on 2009-09-13
I'm glad the hardware issue got sorted, a lot of the time I've noticed hardware is the issue when Ubuntu decides to act up.

---

### Post by kevinatkins on 2009-09-13
Yes, me too :D Thanks!

I really should have known better - my experience to date has been that, apart from the slightly irritating regressions previously noted, Ubuntu is pretty rock solid.. in fact, the same could be said of most Linux distros I've run over the last six years or so..

Actually, maybe things have turned out for the best anyway - my machine had been previously been upgraded over at least two Ubuntu iterations but now it's running a 'bare metal' install of 9.04 and the difference in performance is really quite noticeable! Much better.. so although I've never had problems with upgrades per se, I'm thinking that in future I'll do full re-installs when I want to move to the next version.

---

### Post by slakkie on 2009-09-13
> **moster said:**
> I did not  compile anything. I had to add blacklist acer_wmi to /etc/modprobe.d/blacklist for my wifi to work. That is all. But week after that, update came and wlan stop working. I did reinstall again and update it all and then blacklist again and now it work. But I would not bet my money how long it will work. We can argue, but this is not way for doing business. There is no point in repairing(updating) one thing and damaging another.

Sorry everybody for carry out my own problems in this thread.

I think you might want to pin your kernel. That way you will not upgrade any kernel version.

```

dpkg2pin () {
        [ -z "$1" ] && return
        local pkg
        pkg=$(dpkg -l | grep "^ii" |awk '{print $2" "$3}' | grep "$1")
        [ $? -ne 0 ] && return
        local msg
        msg="$(date +'%Y%m%d:%H%M%S')"
        echo -e "$pkg" | awk '{print "\nExplanation: Added on '$msg' by dpkg2pin\nPackage: "$1"\nPin: version "$2"\nPin-Priority: 1001\n"}' | sudo tee -a /etc/apt/preferences
}

```

Then run dpkg2pin linux-headers and linux-image and you are in the clear. Be aware that when doing a release upgrade you will not update your kernel..

---

### Post by K7522 on 2009-09-13
> **kevinatkins said:**
> I'm thinking that in future I'll do full re-installs when I want to move to the next version.

Fresh installs are by far the best thing to do and the great thing I love about Linux is that you can keep all your files consolidated in /home/ directories, making backups of pertinent files simple. Anything I have important saved elsewhere in the computer I have a script that backs those folders daily into /home/kurt/Backups :D

---

### Post by GodLikeCreature on 2009-09-14
I think freedom of choice is implicit in the Linux phylosophy.  If someone is not entirely happy using any Linux distro, s/he should move on to something that fits their needs/likes better.

I very much enjoy the challenge of overcoming an issue and learning from it.  In that process, I learn about the system and become more knowledgeable when it comes to computers...

It is a fact that device manufacturer support is still far from being mature under linux, and that distros go one after the other perhaps too fast for a strict production environment.

Having said so, as always in Linux, there are lots of flexibility, and an administrator could choose not to upgrade certain parts, or do so only when security is a concern.

Quite honestly, I have had the same issues in Windows when big upgrades are due.  You are usually safe with security patches, but when you have to apply a big upgrade, such as a service pack or things like that, it is not that unusual that you get issues after it happens.

Anyways, I think Linux is trying hard to close its (very few)gaps to Mac and Windows and its very aggressive approach has a small downside to it.  I am happy with that and could live with slight flakiness at the expense of that quick improvement curve (although I have to say I never have had that kind of issues).  If other people are not and want an environment that behaves the same every day for years, then maybe they should look somewhere else...

---

### Post by ukripper on 2009-09-14
How about starting from the 2nd distro of Distrowatch's list - [http://distrowatch.com/](http://distrowatch.com/) and moving down to the bottom? Try which of them works for you the best.......... GNU/Linux is about choice, goodluck!

---

### Post by GodLikeCreature on 2009-09-14
> **kevinatkins said:**
> Thanks for all the replies folks.. Well, I feel like a silly billy now - it turned out to be a weird hardware issue on my machine - at least, that's what I think.

Thing is, on this particular machine, I dual boot with Vista (well, I don't often boot into Vista in fact) and when Ubuntu (9.04) started freezing, etc, I booted into Vista, no problems at all. Now, Vista is on a physically separated hard drive in the machine. Anyway, thinking nevertheless that it might be hardware related, I left Memtest86 running overnight - no problems found; I ran a disk surface scan on the Ubuntu drive - no problem found..

Anyway, cut a long story short, I tried installing Debian, and that started exhibiting the same behaviour. Vista remained fine. So I'm thinking at this point that it had to be to do with the hard drive (SATA)... Well, in desperation, I just decided to open the machine up, give it a good clean, re-seated memory and all connectors, and re-installed Ubuntu. And it's been running absolutely fine ever since, for the last 24 hours without hitch. The only sensible possibility I can think of is that perhaps it was a memory issue - the machine is fairly low-grade with shared nVidia graphics, and I don't think Memtest checked the shared memory bit? And that perhaps Vista wasn't addressing the memory locations which were causing problems? I dunno...

Anyway, it's sorted, and Ubuntu is back on (in spite of my grumblings.. do I feel like a prat now or what?!)

Well, don't feel like that, man!...  I think the initial frustration then leads to finding a solution, and the inevitable finding of something you didn't know.  I really hope you continue to enjoy a good experience under our favorite distro!

---

### Post by moster on 2009-09-14
> **slakkie said:**
> I think you might want to pin your kernel. That way you will not upgrade any kernel version.

```

dpkg2pin () {
        [ -z "$1" ] && return
        local pkg
        pkg=$(dpkg -l | grep "^ii" |awk '{print $2" "$3}' | grep "$1")
        [ $? -ne 0 ] && return
        local msg
        msg="$(date +'%Y%m%d:%H%M%S')"
        echo -e "$pkg" | awk '{print "\nExplanation: Added on '$msg' by dpkg2pin\nPackage: "$1"\nPin: version "$2"\nPin-Priority: 1001\n"}' | sudo tee -a /etc/apt/preferences
}

```

Then run dpkg2pin linux-headers and linux-image and you are in the clear. Be aware that when doing a release upgrade you will not update your kernel..
This is really nice tip. Thanks :)

---

### Post by steveneddy on 2009-09-15
Try another version of Ubuntu, try a different distro, or go back to Windows.

Maybe try a Mac if you like.

Remember that the newest versions of Ubuntu are not really for a production environment and that you may do well to go to 8.04 Hardy or 8.10 Intrepid. Hardy is supported for a few more years and Intrepid is supported for about another year or so. The later versions are only supported for six months. 

I installed Intrepid to solve a few issues that I had with Hardy. Just because the latest version is available does not mean that it is recommended for a working machine. My advise is that if you have to get work done, stay off of the cutting edge.

I say that **use whatever works** for you so you can get something done.

Do not define yourself personally or professionally by what operating system you use.

---

### Post by fourtyseven on 2009-09-17
> **steveneddy said:**
> 

I say that **use whatever works** for you so you can get something done.



In my opinion, 9.04 has been the worst release to date. Never have I had as many problems as I have had whilst using 9.04.
Eventually out of frustration I went back to 8.10; it runs like a dream. I think its very easy to get caught up in wanting to run the newest version which is not always better. Its all about finding what works for you. After all, isn't that part of the beauty of Linux?

---

