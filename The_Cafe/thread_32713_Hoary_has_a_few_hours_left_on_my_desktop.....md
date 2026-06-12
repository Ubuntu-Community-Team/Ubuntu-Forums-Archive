---
title: "Hoary has a few hours left on my desktop...."
date: 2005-05-09
forum: The Cafe
---

### Post by jdong on 2005-05-09
Before my SuSE 9.3 torrent finishes :(


It's sad to announce that Hoary and I are not getting along well on my desktop. The last straw was RAID support -- I cannot get a RAID5 root to boot with the default kernels. I've tried for quite a while now. Sure, I could go off and compile/patch my own kernels, by why do that when there's distributions out there with elegant RAID support built-in?

For now, SuSE 9.3 will get installed on my 200GB RAID5, while Ubuntu will step aside to my 40GB spare partition, serving as a Backports chroot environment.


Like every other of my little distro-changing moments, Backports and UbuntuForums involvement both won't be affected -- I still have systems running Ubuntu, and I still recommend Ubuntu.



PS, yes, this means I'll be giving a SuSE 9.3 review within the next few days ;)

PPS: Yes, it is perfectly legal & governed by SuSE's EULA to redistribute SuSE in any fashion, including reselling it. Gotta love Free software!

---

### Post by TravisNewman on 2005-05-09
Good luck keeping something installed this time J! Hopefully you'll find something to fit your needs :)

---

### Post by KiwiNZ on 2005-05-09
I'll be looking forward to your Suse 9.3 reports . I have been given the Professional version but havent had time to try it yet .

---

### Post by dodger on 2005-05-09
I just came back to ubuntu from suse 9.3.
It might havi its advantages as a server os, but imho there is no better desktop distri than (k)ubuntu at the moment.
suse is just way too bloated by default, itS taking ages to boot, and worst of all, it does not have apt-get.
yes, I know, there is apt-get-for-rpms and I have used it, but it's just not the same.

dodger

---

### Post by BAshworth on 2005-05-09
Great thing about Suse though, is that there are Red Carpet repositories for it.  That, and Yast is a great tool.

---

### Post by maspro on 2005-05-09
Very curious about your review, Suse 9.3 sounds very cool and I haven't checked there latest version yet. But there is one thing I don't like about Suse Professional and that is that you have to pay for updates.  [-X  

Take a look at there Comparative Features and Benefits chart:

[http://www.novell.com/products/linuxprofessional/comparative.html](http://www.novell.com/products/linuxprofessional/comparative.html)

Then Mandriva would be a better choice IMHO.  :)

---

### Post by jdong on 2005-05-09
Hmm, I don't think paying for updates is true -- I see updates on SuSE FTP mirrors already!


I'm just gonna give it a whirl, before resorting to a complete reinstall of Ubuntu. SuSE may be just as good as Ubuntu, but as I've already stated, Ubuntu refuses to boot on my IDE RAID5, but SuSE 9.2 certainly did boot md raid root. That's my problem right now...

---

### Post by Seth on 2005-05-09
[QUOTE=jdong]Hmm, I don't think paying for updates is true -- I see updates on SuSE FTP mirrors already!


I'm just gonna give it a whirl, before resorting to a complete reinstall of Ubuntu. SuSE may be just as good as Ubuntu, but as I've already stated, Ubuntu refuses to boot on my IDE RAID5, but SuSE 9.2 certainly did boot md raid root. That's my problem right now...[/QUOTE]
 I still use SuSE 9.2 on my desktop. I love SuSE and Ubuntu; they each have their strengths. SuSE has better hardware support in my experience, which is why I use it on my desktop. Things tend to work more out-of-the-box.

Don't forget [http://suseforums.net](http://suseforums.net) ;)

---

### Post by poofyhairguy on 2005-05-09
[QUOTE=jdong]
PS, yes, this means I'll be giving a SuSE 9.3 review within the next few days ;)[/QUOTE]

That makes it all worthwhile.

Jdong's reviews are the best. 

( I might push you into Madriva sometime just to get the writeup).

---

### Post by nocturn on 2005-05-10
[QUOTE=BAshworth]Great thing about Suse though, is that there are Red Carpet repositories for it.  That, and Yast is a great tool.[/QUOTE]

It's strange how opinions can differ.
I like SuSE overall (although I do prefer Debian derivates), I actually really dislike yast.  I only ever use sw_single and online_update from it.

What I miss the most is a simple command to upgrade (apt-get update && apt-get upgrade) instead of the menu driven stuff...

---

### Post by maspro on 2005-05-10
[QUOTE=jdong]Hmm, I don't think paying for updates is true -- I see updates on SuSE FTP mirrors already!
[/QUOTE]
Well according to this link: [http://www.novell.com/products/linuxprofessional/comparative.html](http://www.novell.com/products/linuxprofessional/comparative.html)
you don't have to pay for all of the updates, but many updates aren't free. Although there is a difference in the amount of free updates between the professional version and the enterprise server version.

---

### Post by BAshworth on 2005-05-10
[QUOTE=nocturn]It's strange how opinions can differ.
I like SuSE overall (although I do prefer Debian derivates), I actually really dislike yast.  I only ever use sw_single and online_update from it.

What I miss the most is a simple command to upgrade (apt-get update && apt-get upgrade) instead of the menu driven stuff...[/QUOTE]

'online-update'  No need for a menu.  I just like Yast for installing new software.

---

### Post by jdong on 2005-05-11
Alright, I'm posting from SuSE right now. Firstly, I've confirmed that the RAID issue was Ubuntu-specific. I created the new RAID5 from SuSE's installer (YAST), and made sure SuSE booted OK with it.

Then, I swapped over to Ubuntu, and the initrd complained that members don't have superblocks or have the wrong uuid's, blah blah. Switched back to SuSE, and it worked fine :)


So, I'll do this bullet-style:

[list]
[*] First of all, I'd like to complement SuSE on the bootsplash. Like in 9.2, there's a progress bar running at the bottom of the screen, which is quite nice information to know.   
[*]SuSE's installation procedure is very straightforward. From partitioning to selecting packages to that initial reboot, I had no problems with the installer.   
[*]I will have to complain that SuSE took much longer (1 hour) to install compared to a base Ubuntu system (25 minutes)   
[*]**Configuration: **YaST guided me through flawlessly to a login screen, though not Nvidia accelerated. **NVidia support was buggy** -- I had to manually edit /etc/X11/xorg.conf to switch 'nv' to 'nvidia', and also removed all the ModeLines, because they brought my LCD display to 640x480...   
[*]**Bootup times are slower** than Ubuntu, but I have to add that SuSE has a MUCH more elaborate bootup system. The initrd waits for root filesystems to initialize before trying to mount them -- very useful for USB root devices that take a couple of seconds to initialize. Also, the SuSE networking scripts are commendable. The scripts wait 3-4 seconds for DHCP, then backgrounds and continues non-network related bootups. If DHCP still times out, SuSE will skip trying to start any network-related services. In addition, SuSE comes with  a caching nameserver. My ISP's DNS is crap, and I appreciate SuSE's insight.   
[*]Ok, now, we're past installing and initial configuration. I'd like to talk about updates. SuSE employs a Fedora-like update system: For major system packages like X.org or Apache/MySQL, security and bugfixes are backported to the shipped version [Ubuntu/Debian style updates]. However, for desktop apps, like Firefox or GAIM, SuSE takes the latest revision. Even though, for example, SuSE 9.1 shipped with Firefox 0.10PR1, it currently has been updated to 1.0.3+ for security reasons! Ubuntu needs to start doing this.   
[*]SuSE ships with OpenOffice 2.0 beta (build 79 + bugfixes), and Novell promises an update to 2.0 final when it's released. I played with OOo a bit today, and found it to be VERY stable -- better than the latest build on Ubuntu or Windows. It's apparent that Novell worked very hard to stabilize this beta. KDE integration works beautifully.   
[*]I'd also like to add that SuSE uses deltarpm patches. For an Openoffice.org2.0 security update, only ~500kb was downloaded, as opposed to the entire updated 100MB package! Very nice job!   
[*]SuSE has switched to udev, but still uses its hwdetect/hwplug architecture heavily. For automounting, SuSE still uses Submount. Submount has the advantage that CD's can be ejected at will.   
[*]SuSE has toned down its window decorations to be more 'conservative', giving the entire environment a more professional feel. 
[/list] 
Overall, I'm having a great time with SuSE right now. I'm currently testing out my chroot environment for backports, and am planning to package some backports tonight!

---

### Post by TravisNewman on 2005-05-11
so questions for you jdong-- 
 
How is Gnome, or have you tried it? Or WILL you try it?
 
Have you messed with Xen? I know it was included in this release of SuSE, and that would be better for your backports than a chroot or UML. Thought about doing that myself.
 
Ignore RAID support-- how does it stack up against Ubuntu, talking everything into account?
 
what's a deltarpm again?

---

### Post by jdong on 2005-05-11
[QUOTE=panickedthumb]so questions for you jdong-- 
 
How is Gnome, or have you tried it? Or WILL you try it?
 
Have you messed with Xen? I know it was included in this release of SuSE, and that would be better for your backports than a chroot or UML. Thought about doing that myself.
 
Ignore RAID support-- how does it stack up against Ubuntu, talking everything into account?
 
what's a deltarpm again?[/QUOTE]

GNOME: I haven't tried it yet, and don't plan on doing so. It does appear, from screenshots, to be quite well polished. Knowing Novell & Ximian, i'd expect GNOME to look pretty nice.

I've yet to play with Xen -- am planning to do so soon. When all you need is a command line, chroots run faster than any sort of virtualization (including Xen) because they're NATIVE, not virtualized at all. I definitely want to play with Xen soon. I did install it during the initial package selection.


Ignoring RAID support, I do find SuSE to be a bit more user friendly, primarily because it has a CENTRALIZED setup place (YaST), as opposed to Ubuntu, which has tools here and there. In my experience of converting Windows users to Ubuntu, "Where's Control Panels" has been the most common question. SuSE solves that issue, and so does Mandrake (err Mandriva)


Delta RPM's are patches to currently installed packages. (i.e. an incremental patch to an RPM file)

---

### Post by poofyhairguy on 2005-05-11
My question:

One of the bullet points for this new release was Beagle was added. How does it work in suse? Does it have all the needed pluggins to search most files?

---

### Post by ow50 on 2005-05-11
How's the package selection? I remember when I tried suse (9.0 I think) the package selection was not good at all and there was no good community repository like for example PLF for Mandrake.

---

### Post by TravisNewman on 2005-05-11
chroots are much better for small things, but when you need to test backported kernels or something, a chroot won't do much good.

---

### Post by KiwiNZ on 2005-05-12
"SuSE has toned down its window decorations to be more 'conservative', giving the entire environment a more professional feel"

That has been one feature that has turned off Suse in the past,The over use of Crayolas. Have they reduced the size of their Icons ? especially in the launch menu?

Install times have been a pain the past .Maybe I am impatient, anything over 30 minutes gets me grumpy.

I may have to dig out the disk for 9.3 and give it a try though.

---

### Post by im_ka on 2005-05-12
i've tried suse 9.3 on my thinkpad t23 but i could only stand it for a few days.

gnome:
i wanted to do a plain gnome install. not possible. it is, but it installs a bunch of k stuff too. it even installs konqueror if you do a gnome installation. and you can't get rid of the kde stuff because they are deps for gnome. strange. okay, i installed gnome, but it was terribly slow. haven't tried beagle since gnome was not usable for my standards, so i went on...

kde:
kde was pretty good, but sometimes sluggish

the xen version that comes with suse is broken. i played with it, but you can't really restore domains. actually you can, but the restore command gives an error, and simply starting a domain from the old config file gives you a restored domain, while it should give you a new domain with the same config. i've talked to a developer, and he said that the version included in suse 9.3 is buggy (it's a release candidate of some version)

yast is nice, but sloooooooow

overall, suse 9.3 is pretty slow on my thinkpad with 866 mhz P3 and 256 mb ram. yea, it's not the latest hardware, but other distros perform much better.

the only positive thing was that my ralink based wlan card was supported "out-of-the-box", but it takes about 5 minutes to set it up on ubuntu or debian.

suse was the one that got me into linux (i've used/tried every version since 9), and i really expected 9.3 to be much better.

i'm running debian sarge with xfce now. i have not had any problems with ubuntu, but i had this itching to try something new and to give debian an honest try. ubuntu is nice and still like it, but debian gives me more options. it took a few hours to set up everything, but it was worth the time. i will keep using sarge and run the always up-to-date xfce from the extra repo (os cillation). i love xfce, it's really refreshing.
i don't think i'm going anywhere from here, at least not on this machine. if i had a more powerful machine (maybe an amd64), i would go for gentoo. i tried it and liked it, but wouldn't use it as my main system.

this is where i'm now :)

---

### Post by BAshworth on 2005-05-12
[QUOTE=ow50]How's the package selection? I remember when I tried suse (9.0 I think) the package selection was not good at all and there was no good community repository like for example PLF for Mandrake.[/QUOTE]

When I used Suse 9.2, I had Red-Carpet installed on it, which gives you many extra choices for software to install through open carpet.  I didn't get into Yast enough to look up how to add additional repositories to it.

---

### Post by jdong on 2005-05-17
I have left SuSE, and made my own reiser4-patched 2.6.11 kernel to work with Ubuntu, and I'm glad to be back home.

SuSE simply didn't fit:

[list]
[*]**Speed Issues** -- I found similar speed issues I found in Redhat/Fedora: heavy disk I/O stalls the system. For example, if I'm copying a 2GB file across two partitions, the system barely responds to my mouse movement. I don't know what kernel/userland modifications cause this behavior, but it's absolutely unacceptable.   
[*]**Community** -- I don't get the "we're all just like each other", community feeling from SuSE's forums/lists. It simply doesn't feel the same. 
[/list] 
However, I did learn quite a bit from SuSE. Most importantly, it made me value packaging restricted software (flashplayer, w32codecs, Java) and Openoffice.org2.

As a result, though I can't really make an OOo 2.0 Debian-quality package, I'm trying to at least compile a set of binaries that are safe to use with Hoary.

I'm also starting to package more Java stuff.

---

### Post by BAshworth on 2005-05-18
[QUOTE=jdong]I have left SuSE, and made my own reiser4-patched 2.6.11 kernel to work with Ubuntu, and I'm glad to be back home.

SuSE simply didn't fit:

[list]
[*]**Speed Issues** -- I found similar speed issues I found in Redhat/Fedora: heavy disk I/O stalls the system. For example, if I'm copying a 2GB file across two partitions, the system barely responds to my mouse movement. I don't know what kernel/userland modifications cause this behavior, but it's absolutely unacceptable.   
[/QUOTE]

If it's the same issue as Fedora had, it's that DMA isn't enabled on the drive.  I had to create a hardiskhda file in my etc/sysconfig folder to turn it on.  Solved the lagging problem.

I still have Suse, and they do add some features (Gnome Control Center, etc..) that give it just a bit more polish.

However, Ubuntu still runs better. :D

---

### Post by jdong on 2005-05-18
No, DMA is certainly enabled -- I checked all the drives.

Furthermore, I can easily get 50MB/s+ bandwidth from my drives in RAID5 -- faster than Ubuntu [45MB/s]

However, if you run a **dd if=/dev/md0 of=/dev/null** in the background, then try to launch Openoffice, watch SuSE and Fedora grind to a halt.

---

### Post by jerome bettis on 2005-05-18
you think reiser4 has anything to do with it?  but if it works in ubuntu then that makes no sense at all.  i wonder if the compiled binaries between suse and ubuntu are done with different optimizations which could cause problems like that.   what distro you use should have no effect on how the kernel behaves.  strange ...

i just switched my /usr /var and /home partitions over to reiser4 last night ... it seems really quick with small files but big files like a 700mb mpeg seem to take longer to load.

i'm wondering how to switch my root partition over ... i could use a live cd but i'm not sure if any of their kernels have reiser4 support built in.  i know mepis doesn't.  i guess i could move my windows data to my usb disk and use that partition to act as root while i switch over ... but i'm wondering if there's an easier way?

---

### Post by jdong on 2005-05-18
reiser4 does speed up parallel disk access, but is still slow under SuSE -- I converted to a R4 root just for fun, and it was no help.

I'm currently using a pure reiser4+raid5 setup on my Ubuntu system. The Kanotix LiveCD is very helpful. It has reiser4 built-in.

---

### Post by jdong on 2005-05-18
[QUOTE=jerome bettis]i just switched my /usr /var and /home partitions over to reiser4 last night ... it seems really quick with small files but big files like a 700mb mpeg seem to take longer to load.[/QUOTE]

Hmm, reiser4 seems all-around faster than ext3 and reiserfs for me. Especially when dealing with the backports tree (svn update, which has to do mdsums and deltas for 13GB worth of packages), reiser4 offers AMAZING speed.

I do find that some uses, like APT rebuilding its dependency trees, are slightly slower, though, but it's gotten better in recent kernel revisions.

---

### Post by poofyhairguy on 2005-05-19
[QUOTE=jdong]
[*]**Community** -- I don't get the "we're all just like each other", community feeling from SuSE's forums/lists. It simply doesn't feel the same. 

[/QUOTE]

How sweet.

---

### Post by neighborlee on 2005-05-22
[QUOTE=maspro]Very curious about your review, Suse 9.3 sounds very cool and I haven't checked there latest version yet. But there is one thing I don't like about Suse Professional and that is that you have to pay for updates.  [-X  

Take a look at there Comparative Features and Benefits chart:

[http://www.novell.com/products/linuxprofessional/comparative.html](http://www.novell.com/products/linuxprofessional/comparative.html)

Then Mandriva would be a better choice IMHO.  :)[/QUOTE]
------------
not to mention 'limited availability' of security uipdates ???

l8r
me

---

### Post by neighborlee on 2005-05-22
[QUOTE=poofyhairguy]How sweet.[/QUOTE]
-------------
yeah I agree..how sweet...ubuntu's community seems more focused on being 'nice' huh ;-)

;-)
nl

---

### Post by davidgypsy on 2005-05-22
I have Ubuntu running very nicely on my laptop and Suse 9.2 pro on my desktop. Suse does some things very well straight out of the box, but you do have to pay to do an update to the new version, only security updates are free. I am considering changing my desktop to Ubuntu, maybe...

---

### Post by jdong on 2005-05-22
I got my copy of SuSE through Bittorrent. I seeded it back up to a ratio of 2 before leaving. :)

---

### Post by neighborlee on 2005-05-22
[QUOTE=jdong]I got my copy of SuSE through Bittorrent. I seeded it back up to a ratio of 2 before leaving. :)[/QUOTE]
-------
there is no suse bittorrent for suse 9.3 anything faik..only ftp download and that is a net install ( barf)..

where is this ?

bye for now
nl

---

### Post by jdong on 2005-05-22
[http://www.interknet.net/bt/?torrent=suse93](http://www.interknet.net/bt/?torrent=suse93)

Third result from Google search suse 9.3 torrent

---

### Post by TravisNewman on 2005-05-22
[QUOTE=jdong][http://www.interknet.net/bt/?torrent=suse93](http://www.interknet.net/bt/?torrent=suse93)

Third result from Google search suse 9.3 torrent[/QUOTE]
 And SuSE does agree that getting it over BT is fine, right?

---

### Post by jdong on 2005-05-22
Yep, Novell has said that the EULA grants users that right.

It was the first thing discussed on that site.

---

