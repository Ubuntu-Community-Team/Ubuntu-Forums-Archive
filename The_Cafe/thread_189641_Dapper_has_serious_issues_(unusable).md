---
title: "Dapper has serious issues (unusable)"
date: 2006-06-05
forum: The Cafe
---

### Post by pksings on 2006-06-05
The upgrade using the "alternative" CDROM and over the net failed to complete for both my son and I. We were both running Breezy. (which was awesome!). Leaving both of our machines in unusable condition. Mine is a Dell D600 laptop, his is an Athlon64 workstation.

Both of us had to format and re-install from scratch.  The "Live" CD will not let me re-use the existing partitions, it only allows formating my /home and dividing it up into a new system (unacceptable, formatting my homedir is never acceptable)

text-mode install from the "alternative" CD was my only choice, which worked fine, install completed and is partially functional.  USB mouse problems, VMware won't run after completing it's install.   

Server installed perfectly the first time. I install xorg, configured it, installed gdm, as xorg wasn't complete, xorg starts and then explodes, no "default" font.  I don't even have time to troubleshoot that...


This is not ready for prime-time folks...  I cannot recommend this to anybody.

Note to Mark Shuttleworth, if this has to be supported from this install base for three to five years the foundation will be broke in two....

Sorry to say, but to me this is a giant setback, If I cannot solve my laptop issues by tonight I have to put Breezy or Hoary back on.


Please don't get me wrong, I love(d) Ubuntu, Hoary and Breezy were both flawless in every place that I put them (A lot), I'm not putting this in anything else.

PK


Update 1, used it all day... lots of missing stuff, jpilot, ssh server, found a link on VMware.com that solved the VMware issue. Too old of a libpng library being used. Command line switch bypasses it.. Mouse problem is a detection issue between the PS/2 to USB keyboard/mouse adapter and a real USB mouse. I unplugged both and put back the mouse and it was fine, then the PS/2 adapter went in second and my problem was gone. Apparently it got detected first and the drivers somehow conflict.  

It's faster than Breezy and Hoary, I love the new printer drivers, my workplace printer is finally fully supported, (Gestetner).
Firefox is much improved and the Blackdown Java engine works properly with EMC Clariion Navisphere Admin. (Yippie!).
This is cool.. But I still can't recommend it, too many bugs getting things working. My less computer geek friends will never be able to get this to work.

---

### Post by deweese on 2006-06-05
I had the same crash.  You ought to either try the alternate install disc of Dapper or use the Breezy Disc and then upgrade on line by putting in terminal
gksudo "update-manager -d"

---

### Post by noelsanidad on 2006-06-06
Whatever happen to "it just works?" I downloaded the new iso image of dapper from one of the mirrors but when it was finished, booted and installed dapper, networking is not working. At first the system can communicate with the dhcp server then if I want to activate my second adapter, the network settings window's graphics is all messed up and then networking stops functioning. I tried to check for the problem even tried to download new drivers for my video card even though its an ati it was working fine in breezy and networking was superb but with dapper those two are messed up. I had to revert back to winxp, as painful as it is maybe but I'm disappointed with what happen. I thought this was my new OS but it failed me.

---

### Post by encompass on 2006-06-06
I certainly would recommend it to anyone... it works great... and yes there are a few querks, but most people won't see it.  If you set up your partitions properly, you should be just find wiht the install... if anything... you can do the partitions yourself using the tools on the cd.  I did have a small confusion with which partition what what, but nothing that most people come across.  (I had home root var usr opt and swap with a "sandbox partition at the end. so it was hard to figure out what was what without deleting any data."  But otherwise fantastic.  I personally would recommend this to anyone doing a fresh install, but, as with any os out there... I would never recommend upgrading from one distro to another, as it leaves old garbage in every user and setting.
Sorry to here your complaint... but dapper is the cleanest os I have seen in a long time.
Keep up the good work Mark.

---

### Post by HeavyAl on 2006-06-07
I agree with encompass. Dapper abosolutely rocks. And I hosed my install too! 

I was using breezy but when I went to upgrade I did some no-no's during the process and ended up screwing the final product up. My solution was simple though, I just booted into safe mode, copied my home dir out to another server on my network, and then popped in the dapper cd, reinstalled (took a whole fifteen mins to install) then copied my home dir back to the finished product. Joila! I was up and running. Sure, I had to reconfigure a few minor things but its a small price to pay for such a slick distro.

---

### Post by vgeddes on 2006-06-08
Dapper's simply amazing. 200% better than Breezy. I too went through serious installation problems, but the any misgivings I had were blown away by Dapper's features and UI polish.:D

---

### Post by jimbeaux on 2006-06-08
I have to agree with vgeddes. Dapper's fantastic!! I had no problems with the install. Everything worked just as if I knew what I was doing. (I don't, I am a nOOb of the first order, but I'm trying to change my ways) IT JUST WORKS!!!

Now, if I can just get the Windows Media only audio files to play for my son, I can say so long to Windows FOREVER.

---

### Post by kurimaw on 2006-06-14
i used the breezy CD on the install and upgraded it OL...works fine...currently trying edgy to see if something breaks...(hope so...)

heard of *nix for years but only swithced this april 2006...

first used RH..bad choice...only this distro lets me have fun...:D

---

### Post by oskie on 2006-06-14
If one checks the forums of most distros one quickly realizes that there is no distro release that is universally a breeze to install in terms of hardware detection, performance etc. Does it make sense to quickly label a distro as 'not fit for primetime' simply because it didn't turn out as expected on your particular box or for your intended use? Granted, it certainly can be frustrating when a new release of your favourite distro turns out to be disappointing (SuSE 10.1 in my case) but I don't think we should automatically state that a whole release is a disaster and should have been put off.  I myself I am thoroughly impressed with Dapper. It is the first Ubuntu release I have been able to install on my notebook and the only Linux release to run more or less flawlessly on same laptop. But then again I am a simple desktop user and don't expect much from my system other than to browse the net and send emails. For a home user, Dapper is fine to me, even for a newbie, particularly on a PC. Can't comment on corporate use, perhaps there it does indeed have teething pains. Perhaps choosing to support this particular release commercially for 3 years was not the wisest thing to do but only time will tell. So far though, 75% or more of reviews appear to be positive. Hey, can't be worse than Vista!

---

### Post by sporkinum on 2006-06-15
I keep wanting to try dapper, but still no luck. I have been running mandrake/mandriva for years, and the main problems I have with it are drivers. I got a ubuntu disk from a friend a year ago, tried it, but it would never see my existing ext3 partitions. So I waited, and then waited some more. Dapper drake came out and I downloaed the desktop install iso, tried it, still doesn't see my existing linux partitions, only the windows partitions. I did some searching and found that gparted running from the desktop should work. Nope.. still no luck. After more research, I was told the alternate ISO was the answer to all my woes. Downloaded, burnt, ran, and I'll be damned.. it still doesn't work.

All I have to say is that the developers should take a long hard look at mandriva's disk partitioning tool, diskdrake. That is the way a partitioner should work. 

For now, the ubuntu disks go back un the shelf until they realize not everyone has a clean partition to install to, and they supply the tools to use them.

Completely unacceptable IMHO.

---

### Post by therunnyman on 2006-06-15
[QUOTE=vgeddes]Dapper's simply amazing. 200% better than Breezy. I too went through serious installation problems, but the any misgivings I had were blown away by Dapper's features and UI polish.:D[/QUOTE]

Would you mind elaborating on these statements?  I disagree with all of them, profoundly (excepting the crumby installer), but I'm willing to lighten up, and retract my general condemnation of Dapper.

runny

---

### Post by John.Michael.Kane on 2006-06-15
We as enduser's must all understand that what works for someone on their hardware may not work for others on their's. vgeddes hardware works with dapper he/she is happy. while person b or c may have had a not so happy go at installing dapper. 


Sidenote: if dapper be it the live/install or alternate cd is hashing you issues.  try testing another distro to see if you get the same problems or new one's.


Just my thoughts...

---

### Post by poofyhairguy on 2006-06-16
[QUOTE=sporkinum] After more research, I was told the alternate ISO was the answer to all my woes. Downloaded, burnt, ran, and I'll be damned.. it still doesn't work.[/QUOTE]

What do you mean by this?

Did the alternative installer not even see the partition? Did it just show you had no hard drives? If it see the partition it up to you to "manually edit partition table" and tell the installer that you want to mount your old partition as / (root) or /home. It does not automatically do that.

The only thing the Ubuntu paritioner does automatically is erase the entire hard drive and partition it manually. Anything more advanced than that you have to do. Its no big deal- I have a really hard partition table that I set up everytime.

---

### Post by mstlyevil on 2006-06-16
[QUOTE=pksings]The upgrade using the "alternative" CDROM and over the net failed to complete for both my son and I. We were both running Breezy. (which was awesome!). Leaving both of our machines in unusable condition. Mine is a Dell D600 laptop, his is an Athlon64 workstation.

Both of us had to format and re-install from scratch.  The "Live" CD will not let me re-use the existing partitions, it only allows formating my /home and dividing it up into a new system (unacceptable, formatting my homedir is never acceptable)

text-mode install from the "alternative" CD was my only choice, which worked fine, install completed and is partially functional.  USB mouse problems, VMware won't run after completing it's install.   

Server installed perfectly the first time. I install xorg, configured it, installed gdm, as xorg wasn't complete, xorg starts and then explodes, no "default" font.  I don't even have time to troubleshoot that...


This is not ready for prime-time folks...  I cannot recommend this to anybody.

Note to Mark Shuttleworth, if this has to be supported from this install base for three to five years the foundation will be broke in two....

Sorry to say, but to me this is a giant setback, If I cannot solve my laptop issues by tonight I have to put Breezy or Hoary back on.


Please don't get me wrong, I love(d) Ubuntu, Hoary and Breezy were both flawless in every place that I put them (A lot), I'm not putting this in anything else.

PK


Update 1, used it all day... lots of missing stuff, jpilot, ssh server, found a link on VMware.com that solved the VMware issue. Too old of a libpng library being used. Command line switch bypasses it.. Mouse problem is a detection issue between the PS/2 to USB keyboard/mouse adapter and a real USB mouse. I unplugged both and put back the mouse and it was fine, then the PS/2 adapter went in second and my problem was gone. Apparently it got detected first and the drivers somehow conflict.  

It's faster than Breezy and Hoary, I love the new printer drivers, my workplace printer is finally fully supported, (Gestetner).
Firefox is much improved and the Blackdown Java engine works properly with EMC Clariion Navisphere Admin. (Yippie!).
This is cool.. But I still can't recommend it, too many bugs getting things working. My less computer geek friends will never be able to get this to work.[/QUOTE]

VMware is the problem and not Dapper. There is a simple fix. Symlink /lib/libgcc_s.so.1 to /usr/lib/vmware/lib/libgcc_s.so.1 . This will fix VMware which is using the lib compiled by gcc3.4 instead of gcc4.0 like dapper uses. You obviousaly found this fix but I wanted to elaborate for those who did not realize how easy it was to fix.

Both of my USB mice work fine. Both are Logitech and one is a marble mouse scrollwheel mouse. Did you try killing gdm and the doing a sudo dpkg-reconfigure xserver-xorg to correct the mouse problem? It could be as simple as that to fix the problem.

Since the alternate installer is available and very good I don't see the real issue with the live cd installer unless you have no net connection or are on dial-up. I tell everyone to steer clear of it. At least Ubuntu gives us the option.

None of the things you listed convince me that Dapper is not ready for prime time. Every distro I tried including Mepis and Suse have given me minor hardware issues that I had to find a way to fix. This is the hardware manufactuers fault for not releasing hardware specs or drivers. They also have had things missing that I needed or expected. That is why if one does not work for your set up, then try another that will work. Hell even Windows has given me problems with my hardware in the past lol.

I am glad you are finding solutions. But no distro is right for everone. Breezy had some horrid issues that took months to smooth out. Dapper has by far worked much better for me than Hoary or Breezy ever has.

---

### Post by kenweill on 2006-06-16
I have problems with the Desktop CD as well. Can't install.

But i was able to install Dapper Beta with no problem. I just update/upgrade it and it works just fine. I have even installed "kubuntu-desktop" and update kde to 3.5.3 with no problem at all.

I guess the problem is on the Dapper Final installer.

---

### Post by sporkinum on 2006-06-16
[QUOTE=poofyhairguy]What do you mean by this?

Did the alternative installer not even see the partition? Did it just show you had no hard drives? If it see the partition it up to you to "manually edit partition table" and tell the installer that you want to mount your old partition as / (root) or /home. It does not automatically do that.

The only thing the Ubuntu paritioner does automatically is erase the entire hard drive and partition it manually. Anything more advanced than that you have to do. Its no big deal- I have a really hard partition table that I set up everytime.[/QUOTE]

No, it doesn't see the partitions. I don't have a lot of space available for it. 4.8gb is the current / (hdb2) partition. Swap is 627mb, and /home (hdb7) is 4.1gb. All ubuntu sees is just hdb. I want to reformat / and swap and keep /home. Why do they consider that too advanced? It seems pretty basic to me.
[IMG]http://www.sporkinum.org/images/d/164-1/snapshot2.png[/IMG]

---

### Post by tseliot on 2006-06-16
[QUOTE=sporkinum]No, it doesn't see the partitions. I don't have a lot of space available for it. 4.8gb is the current / (hdb2) partition. Swap is 627mb, and /home (hdb7) is 4.1gb. All ubuntu sees is just hdb. I want to reformat / and swap and keep /home. Why do they consider that too advanced? It seems pretty basic to me.[/QUOTE]

Are you sure that it doesn't see your partitions? I have 12 paritions and it can see them. Of course I have to set the mount points. It's not done automatically. Make sure you pay enough attention during the installation (OF COURSE I'm NOT saying that you're a lier).

---

### Post by therunnyman on 2006-06-16
[QUOTE=SD-Plissken]We as enduser's must all understand that what works for someone on their hardware may not work for others on their's. vgeddes hardware works with dapper he/she is happy. while person b or c may have had a not so happy go at installing dapper. 


Sidenote: if dapper be it the live/install or alternate cd is hashing you issues.  try testing another distro to see if you get the same problems or new one's.


Just my thoughts...[/QUOTE]

Snake, man, throw me a bone here..we been friends for how long now?

If a Linux based OS can't deal with more than two hard disks, something is horribly wrong.  We turn to Linux for RAIDs, and servers, and just general rock-stable performance.  Dapper, after many hours of difficult, delicate, dangerous work, will function as a RAID 5/server, I'll grant that.  But are you going to trust critical data on something that can't enumerate *hard disks* properly, and confuses mirrors with stripes *on install*?

Help me out here, Snake, bubby...that's a serious problem, man!

runny

PS I did try other distros, just incidentally - I am, after all, a scientist.  Breezy, of all things, does the best job handling disks and their uses, so far as I've seen.

---

### Post by John.Michael.Kane on 2006-06-16
@therunnyman your right. that the issues some are having under dapper should not be there. Being  that most are just upgrading the OS, and still running the same config's they had working stable under brezzy. Sure the same config sould would with dapper but  this does not seem to be the case, some of the isses have no known work around atleast none i know of. This is the reason i asked for users with problems that have no known work around to try another distro so they could find one that is stable for what they are trying to do, be it raiding 6-sata dives or setting up a server. I would rather see an enduser happy with what ever distro even if it's not ubuntu at least till these issues that are being posted about are worked out. just my take on it.

---

