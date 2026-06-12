---
title: "Bit of a let down"
date: 2004-11-29
forum: The Cafe
---

### Post by papiermache on 2004-11-29
Hello, well I have just tried the latest Ubuntu release (4.1) after some friends convinced me. Previously I was running Windows XP, unhappy with the security problems plaguing it, curious by Linux - a friend suggested Ubuntu.

On the up side, it's quite attractive and comes with lots of apps.

However, after being told that Linux is lighter, faster and more secure, it's something of a let down. During installation it downloaded nearly 80 megabytes of security fixes - quite shocking for an OS that (as far as I know) has only been out since October!

Plus it takes quite a bit longer than XP to boot up, and the desktop feels slower. Applications are more sluggish to start as well (I used Firefox on XP before and it takes longer to start up on Linux). OpenOffice takes about 10 times longer to start than MS Office. I've made sure DMA is enabled, I've done all the tuning I can see in novice-friendly docs - but still doesn't feel as snappy as Windows (with themes and crap turned off).

I thought this was just me but it seems others are finding this, even with other distros like Mandrake and SUSE. Only help I've been given is to switch to "Fluxbox", which by the screenshots seems to be extremely limited and non-integrated. I'd rather stick with a proper desktop.

Just thought I'd let my feelings be known. I'd really like to use Linux more, and Ubuntu looked quite polished, but the boot speed, sluggish desktop and huge security updates kind of went against what I'd been told about Linux :(

I will try the next release - hopefully it will be better. Open source looks great but there needs to be real incentives to switch, and 80 megs of fixes two months later, and a slow boot (important on my laptop), desktop and apps won't make others happy either. I wish you all well and hope these problems are fixed!

---

### Post by sebast on 2004-11-29
Well,

For myself, Ubuntu boots faster than windows and is faster.

And that's not just to promote Linux, Ubuntu is really faster than windows on my Dell desktop.

Actually, it's also faster than Fedora 2 (and Fedora 2 takes a great while to boot)

---

### Post by kingnubian on 2004-11-29
HHHmmm, not all these "fixes" are 100% security related some are just updated versions to existing applications. I will thake the 80Mb, as you say, of downloads which i get for free rather than having to pay, legally at least, for those on Windows. Also consider that given the amount of software that Ubuntu installs such as OpenOffice, Firefox, ect, that even on a Windows machine attempting to update the equivalent amount and type of software will take longer and mean more Mb transfered.  Remember after a Windows install it's pretty vanilla, add just an office suite and you've notched up the complexity a fair amount. Now add instant messanging, MSN messenger, Yahoo Messenger and ICQ will have to be downloaded and installed, a PDF viewer, ect and now see how long it takes and how many Mb are transfered. 

Another thing to realize is that security fixes tend to come out sooner after an issue is found than in the Windows world. There are still well known soft spots in various versions of Windows that MS has been made aware of months and months ago but has yet to address. It's as if MS has the "leave it alone untill something bad happens" VS the Linux "fix it before the problem can be exploited" direction.

The Linux world is also moving presently much faster than the windows world so expect more activity.

One thing I've noticed right away using Ubuntu is how much smoother and faster networking is than on my XP box. In paticular printing to my printer on the network, directly connected to a server, is much much faster! What I mean is that the print jobs start almost right away vs taking up to 1 min if initiated from my windows box.  Browsing remote machines is also very smooth and fast. Samba rocks!

Another feather in Ubuntu's cap is apt-get or in a GUI mode, Synaptic. Never has installing/uninstalling software or fixes been such  no brainer before. The downside is that some software still have cryptic names but if you know what you are looking for your on your way and if not there is a great search function.

Powerfull symplicity is what I call Ubuntu, never have I installed an OS that allows me to be productive right away. The forums are fantastic and the Howto section alone is worth it's weight in Gold.

---

### Post by amoser on 2004-11-29
What kind of processor are you running, if you are running a p4, try apt-getting the 686 kernel.  If you are running a AMD Duron/Athlon, get the k7 kernel.  That will really help your speed out.

~Alan

---

### Post by wallijonn on 2004-11-29
With Linux when you start an application it "compiles" each time. In the Windows world the application is usually one big .exe file. So yes, Windows will always load faster.

Now, let's say that you have 4.6 gig of .jpegs or .mp3s. Copy them to your home folder under Windows and Linux. You should find that Linux is much faster. Burn a full CD of data on Windows or Linux; Linux should be much faster. 

One thing which may help, somewhat, is pre-linking the apps. (tip elsewhere on this site).

---

### Post by mr_ed on 2004-11-29
I agree that you have valid criticisms.

Thank you for making people aware of your problems.  Without stuff like this (and stuff that gets posted to Bugzilla), the developers may not even be alerted to the problem.

It _is_ slower to boot on my machine as well.  I can turn on my work machine (PIII-650MHz, 256MB RAM, Win2K) and my home laptop (PIII-1000MHz, 256MB RAM, Ubuntu 4.10), and they finish roughly at the same time, IIRC.  If the laptop isn't connected to the network when I boot, add 1 minute to the startup time of the laptop.

One thing though, is that Windows will load the desktop before it's loaded all its services, where I find it's the opposite with Linux, so Windows "appears" faster, even though the hard drive is still churning away.

The devs are working on this for the Hoary release.  I can't wait to see what they come up with.  :)

You shouldn't have to use Fluxbox to get an acceptable speed.  It is faster though.  ;)

When I was running Arch Linux (which is an uber-leet distro that's fast), the startup time was faster, but not by much.  It all depends on how many services are starting up.

With respect to security fixes, kingnubian has pretty much covered it.

---

### Post by az on 2004-11-29
"With Linux when you start an application it "compiles" each time"
You mean linking, don't you?  And that is the same as a windows app using a dll. isn't it?  The reason why some applications load faster in windows is that they are preloaded into memory whether you need them or not.
There is an openoffice quickstart package available that does just that - it loads it into memory for faster startup when clicked.

Windows shows you the desktop faster, but it is not readily useable.  I find it annoying for it to ignore my clicks as it is starting services.  
Windows has a snappy responsive-to-click desktop, but I have found the unpleasant lags and freezes to be more than annoying and they slowed down my productivity.  If you use fluxbox, icewm or older gtk1.2 apps, you can see that snappieness in linux.  The newer gtk2 apps have smoothed fonts - and that takes more time to draw.

My wife had the same reaction whe she first tried linux.  She said it was slower.

It took her five minutes of surfing the web for her to never want to switch back to windows.  It seemed that for pages to load in windows we had to wait for approval or something.  And that was not with any virus programs running.  I can only imagine how horrible an experience that would be...

Insofar as security, the way open-source software works is that everyone is looking at it.  The fact that many fixes are introduced is a good thing.  In the windows world, such up-to-the-minute security fixes are only available if you pay for the service.  The desktop user has to wait weeks, months or years for fixes.  If you are using a non-english version of windows, add another month (on average) to that wait.

This is arguable, but you can say that security is measured in the time-to-fix period.  The longer the time-to-fix, the worse the security.  The windows security-by-obscurity has proven to not work.

People tend not to read long posts, so I'll stop here.

---

### Post by ChrisP on 2004-11-29
Hi papiermache,,

Sorry to see that your disapointed with linux. Any chance the same m8's that persuaded you to try  it built up your expectations a wee bit too much? You must have had some pressing need to look for something else or you would not have gone to the effort of trying ubuntu?

FWIW  I first tried linux a couple of months ago, like you, because windows security was driving me daft.

 Every one of my friends has been hit with adware, malware, viruses etc this year and, even though i know nothing much about computers, i do know slightly more than the rest of them, so guess who ends up spending hours/days trying to sort them out :(  I enjoy helping friends out but rapidly got out of my depth and the time it was taking up was getting beyond what i could do. )

So i looked for alternatives and learnt about how to make a windows system safe. That took me to firefox which started the grey matter thinking "if they can do THAT!, then what else is all this open source about?

Got the Suse 9.1 personal disk. Loading that was a bit of shock; totally non geeky , it shrank my windows partition,  loaded itself up, bunged on  a menu that allowed me to choose between win2k and linux at boot. and it just worked  :shock: 

Like you, i did not enjoy the long boot uptime, and i'd agree that openoffice seems to take forever to load, but there are a lot of plus points too; I don't have to keep on top of the latest adaware/spybot blaster/avast antivirus/ zonealarm/ etc etc updates: what i need all comes through the Suse updates. Im sure the same is true for Ubuntu.

I had to reformat and reinstall 2 mths ago (yet another virus for which i could get no help ) and reinstalled win 2k. I was on dial up at the time and trying to get the windows patches was no  fun. You tried to download the w2k sp4 patch on dialup? that was bad.. what are the Xp service packs like?

Like you, i was shocked  by the amount of patches needed for a month old distro (as suse 9.1 was to me at that time -a lso about 80mb lol) but at least i could download them by hooking up to the internet before heading for bed, selecting a few packages,  and 50% of the time they were downloaded by the time i woke up. 


I tried w2k sp4 3 nights in a row ,and every time the patch was so massive that my connection had dropped before it finished;so i go to bed with a live connection , through IE (omg), and no firewall or AV allowed (according to MS instructions). Maybe im paranoid but i hated every minute of it and never did get 2k fully patched that week.

Then, last week, i got broadband and was able to get the Suse and W2k quickly and easily totally up to date. First time ever i have been running with the latest patches. No problems with Suse but one of the 2k patches (an "improvement" to the via chipset) caused me yet more hours of grief) _ if i 'd listened to my local comp repair shop i would have shelled out for a new motherboard/processor by now , but a bit of digging on the net showed it was a crap bios that worked until the MS improvements screwed it up. Not MS fault, it was my board,also not my shops fault; cause who knows everything?


Sorry if his seems like a rant, but its just been a bad summer and i've ended up knowing a lot more about computers than i want to know

Chris

---

### Post by wallijonn on 2004-11-30
azz,

It just seems as if The GIMP takes a long time loading. I think it's because of the loading bar when the app. starts.

When I start up any of my computers I usually will walk away. My P4 1.5 / 512MB / W2KPP machine seems to take forever to load. My P4 3.0 / 1G / W2KP takes a little shorter but it still seems like a long time to get to the login screen. WXPP boots up faster than W2KP but it  seems to take longer to shutdown than W2KP. WXP SP2 helped a lot - it boots up quicker than before. 

My P4 1.5 has firewall, anti-virus, anti-trojan, anti-spyware, anti-bho, anti-worm apps. running. Talk about a long time to get to start working... I don't like putting anything in my system tray, like FireFox, ATI, Office, OpenOffice, etc. For awhile I even turned off the date & time applet.

I use The GIMP and OpenOffice on my P4 3.0 / W2KP and MSO2K on my P4 3.0. App. start times don't really bother me. 

Now that I have Ubuntu tweaked the way I love it I find it hard for me to look at FF under Windows. To get Windows looking like my GlossyP is too much work as I work with limited accounts in WXPP and W2KP.

---

### Post by jdong on 2004-11-30
The issues you mentioned are not ubuntu specific, but I'll addresss them anyway:

**Security updates**:
Don't let size fool you... Windows Update uses 'differential hotfixes' -- applying binary patches, while Ubuntu's update mechanism downloads a new VERSION of the package in question. In addition, not all the security updates are 'flaws' -- there are PLENTY of IE/WMP exploits that MS refuses to acknowledge as flaws -- I use these almost on a daily basis to gain higher privs at school.
**You have to remember that Ubuntu provides security updates with ALL BUNDLED SOFTWARE**: Not just GNOME, not just the kernel. Everything from the command prompt to GNOME Tetris receives security updates. There have been 33 from its release -- a relatively small number; and not all of those are what Microsoft considers to be security issues.


**Loading time / Sluggishness:**
Hmm, sluggishness shouldn't happen. I think we should address this separately, if you can give us more info about your computer / hardware.

Loading times... sometimes Linux does take longer to boot up or start a program... It's a UNIX-like OS -- designed to be up for long periods of time without shutdown. On my desktop, which usually gets 10-20 days of uptime before I manage to reboot it, GNOME starts in less than 3 seconds, Firefox pops up almost instantly when I click its button, etc. Try to leave your computer running more often (or use Software Suspend 2!!)

I'll be back later with configuring Software Suspend -- I'm preparing and testing a newbie-friendly HOWTO for it.

---

### Post by sard on 2005-02-06
I'm running a Dell Latitude C610 with 800Mhz and 256 ram, ATI Radeon Mobility.  Applications seem to start quickly, Open Office and Firefox load faster than they do in windows on my main Athlon XP3000+ system which has a gig of ram.

My problem is with the rate the screen is updated.  For example when I switch tabs in Firefox, minimise or maximise programs, click OK on menu boxes it takes a noticeable amount of time for the screen to change.  Is this the legendary rubbish ATI Linux drivers?  It makes using Ubuntu feel a lot more sluggish and less responsive than running XP on this same laptop.

---

### Post by nocturn on 2005-02-07
On the desktop slugishness, maybe you do not have acceleration on in your video driver (I had to do this for my nvidia card).

That aside.  I have run WinXP at work on an PIII, 600Mhz, 256 MB RAM.  It would freeze for 20 seconds when a mail came in.  Starting an Office app would freeze the Desktop for about 30-60 seconds.  

My old laptop at home, running Warty, is a PII 333, 128MB ram, it runs Gnome, Evolution and yes, even OpenOffice fine.  Openoffice starts relatively slow, but the desktop and other apps remain responsive.

---

### Post by KiwiNZ on 2005-02-07
I have to say that I agree with  the slowness of Open Office to open . I have applied the "fix" for this and I still find it painfully slow.
 
 As for the slow boot times , yes try to leave your PC on , its a lesson I took awhile to learn and its hard to get into the habit , post windows not to shut down each night .
 Linux can stay up for weeks without  the need to reboot. Also your hardware will like you better . Boot ups shorten the life span of hardware. The cold shot of current is like cold starts in a car , no oil to protect  the parts.

---

### Post by Tichondrius on 2005-02-07
[QUOTE=KiwiNZ]I have to say that I agree with  the slowness of Open Office to open . I have applied the "fix" for this and I still find it painfully slow.
 
 As for the slow boot times , yes try to leave your PC on , its a lesson I took awhile to learn and its hard to get into the habit , post windows not to shut down each night .
 Linux can stay up for weeks without  the need to reboot. Also your hardware will like you better . Boot ups shorten the life span of hardware. The cold shot of current is like cold starts in a car , no oil to protect  the parts.[/QUOTE]
 On my PC, it takes Windows 22 seconds to boot from the BIOS beep at the end of POST to the time the login screen is displayed and ready for me click and type my password. After entering the password, it takes 6 more seconds until the desktop is displayed, but as you konw some things are still loading in the background for 2-4 seconds more. On the same PC booting woody-i386 it takes 45 seconds from bios post to the GDM login screen, and 7 seconds from login to desktop displayed. I also installed hoary-amd64 on the same machine, and the boot time (post-to-login) is 10 seconds shorter than woody, partly because it has less startup services configured (e.g. mysql), but probably because of some other changes in Hoary. Btw, windows boots from a dual sata/150 raid-0 disk array, vs linux which boots from a single uata/100 disk, so obviously this give windows some advantage, but overall defietely linux takes more time. Well, at least until your windows become overloaded with zillion utilities which add themselves to the startup scrips. Any way you look at it, windows becomes an unmanageable system after a while - it deteriorates, mainly because of the lack of distinction between admin and user privileges.

---

### Post by Shadow Skill on 2005-02-08
Wait a minute what is this Hoary ye speak of? Don't tell me I wasted a cd on Warty when there is a better one already available! :mad: Anyway the slowness you are experiencing could be because of what services are being loaded by Linux and of course your hardware and the way the drivers for that hardware were written.  I will say that after using Ubuntu successfully for about five hours the boot up time seems to be about as long as the boot up time for Windows XP.  It's mainly the fact that Windows loads up the desktop quicker than Ubuntu, an FC3 user also mentioned that Ubuntu's X startup is somewhat slower than FC3's and I would have to agree with his assesment.  I suggest you try to turn off some of the more useless services running on your system and then see if you experience better general performance aside from the boot time which does tend to be a tad sluggish.  You can also try different lightweight Window managers like XFCE [very Gnome like in appearance and compatible with most Gnome themes.  It even has some built in transparency support if you happen to use Xorg and have 3d acceleration enabled.] or Fluxbox which is highly configurable and very, very light.

Keep in mind as well that Linux has a way of reserving memory for applications so the initial startup may be slow but subsequent application startup will be very fast.

---

### Post by Randabis on 2005-02-08
[QUOTE=Shadow Skill]Wait a minute what is this Hoary ye speak of? Don't tell me I wasted a cd on Warty when there is a better one already available! :mad: Anyway the slowness you are experiencing could be because of what services are being loaded by Linux and of course your hardware and the way the drivers for that hardware were written.  I will say that after using Ubuntu successfully for about five hours the boot up time seems to be about as long as the boot up time for Windows XP.  It's mainly the fact that Windows loads up the desktop quicker than Ubuntu, an FC3 user also mentioned that Ubuntu's X startup is somewhat slower than FC3's and I would have to agree with his assesment.  I suggest you try to turn off some of the more useless services running on your system and then see if you experience better general performance aside from the boot time which does tend to be a tad sluggish.  You can also try different lightweight Window managers like XFCE [very Gnome like in appearance and compatible with most Gnome themes.  It even has some built in transparency support if you happen to use Xorg and have 3d acceleration enabled.] or Fluxbox which is highly configurable and very, very light.

Keep in mind as well that Linux has a way of reserving memory for applications so the initial startup may be slow but subsequent application startup will be very fast.[/QUOTE]
 the thing is, ubuntu by default barely loads any services you don't need.

---

### Post by sard on 2005-02-08
I have noticed it trying to contact an Ubuntu server to sync the time though.  If no network is available it takes a long time to give up.

---

### Post by Jspired on 2005-02-08
In response to the original post and how you were disappointed with the amount of security updates you had to make--->I tend to believe this is a good thing.  Ubuntu has addressed issues and offered fixes.  Would you prefer there were none?

---

### Post by jerome bettis on 2005-02-08
it sounds like you need to recompile the kernel on your system.  it's really not that difficult, and if you have the patience to do it, i bet you'll see a significant increase in performance.  the default kernel with ubuntu is optimized for a 386, and it's packaged with a lot of stuff that you don't need (it has to work on everybody's system).

[www.kernel.org](www.kernel.org) download which ever version you see fit.

```
sudo -s
apt-get install build-essential libc6-dev binutils bin86 modutils gawk shellutils grep libncurses5-dev 
mv /path/where/you/saved/the/file/linux-(version).tar.bz2 /usr/src
cd /usr/src
tar -jxf linux-(version).tar.bz2
ln -s linux-(version) linux
cd linux

make menuconfig    <--- take your time and look at the help if you are unsure.  it is better to have a working kernel than a streamlined one at first. 

make-kpkg clean  

make-kpkg -rootcmd fakeroot --append-to-version -(your version number ie custom1) kernel_image modules-image > /dev/null  (this might take a while)

dpkg -i /usr/src/kernel-image-(version).deb 

reboot
```
choose the new kernel at the grub screen.  it should be faster.

also if that made no sense do gedit /usr/share/doc/linux-sourc*/debian.README for more info.

---

### Post by anomie on 2005-02-08
papiermache wrote:
> Open source looks great but there needs to be real incentives to switch, and 80 megs of fixes two months later, and a slow boot (important on my laptop), desktop and apps won't make others happy either.

Linux isn't right for everyone. If you don't have the time or patience to learn something new, you aren't going to get around to realizing the real incentives.

---

### Post by sard on 2005-02-09
[QUOTE=jerome bettis]it sounds like you need to recompile the kernel on your system.  it's really not that difficult, and if you have the patience to do it, i bet you'll see a significant increase in performance.  the default kernel with ubuntu is optimized for a 386, and it's packaged with a lot of stuff that you don't need (it has to work on everybody's system).

[www.kernel.org](www.kernel.org) download which ever version you see fit.

```
sudo -s
apt-get install build-essential libc6-dev binutils bin86 modutils gawk shellutils grep libncurses5-dev 
mv /path/where/you/saved/the/file/linux-(version).tar.bz2 /usr/src
cd /usr/src
tar -jxf linux-(version).tar.bz2
ln -s linux-(version) linux
cd linux

make menuconfig    <--- take your time and look at the help if you are unsure.  it is better to have a working kernel than a streamlined one at first. 

make-kpkg clean  

make-kpkg -rootcmd fakeroot --append-to-version -(your version number ie custom1) kernel_image modules-image > /dev/null  (this might take a while)

dpkg -i /usr/src/kernel-image-(version).deb 

reboot
```
choose the new kernel at the grub screen.  it should be faster.

also if that made no sense do gedit /usr/share/doc/linux-sourc*/debian.README for more info.[/QUOTE]

I'll give that a try, but does this mean the Gentoo peeps with their specifically compiled installations aren't using the emperors’ new operating system after all?  :D

---

### Post by jnoreiko on 2005-03-30
[QUOTE=papiermache]Plus it takes quite a bit longer than XP to boot up, and the desktop feels slower. Applications are more sluggish to start as well (I used Firefox on XP before and it takes longer to start up on Linux). OpenOffice takes about 10 times longer to start than MS Office. [/QUOTE]

I have an 800Mhz Duron.

Warty boots faster than Windows 2000, and I find it to be more responsive. Some apps take a while to launch, but once they are there, things such as moving windows around feels snappy, whereas Win2000 can often get laggy.

---

### Post by jdodson on 2005-03-30
this comment is for the originator of the post.

the gnome desktop is too slow.  this i will not disagree with.  do not get me wrong, i love gnome as a desktop!  however, many developers and users know that gnome is a pretty hefty resource hog.  much work is being done to optimize gnomes memory footprint.  to test this run windows xp on a pentium 3 500MHZ with 128 megs or ram.  now run warty with the defaults.  which one is faster?  my experience has been that xp is.  now there are many reasons for this, however they don't make gnome faster.  i know you can tweak until you are 50 years old, however the best solution is to run a lightweight window manager instead of gnome if you want speed that you are afforded in windows.  i have scoured the gnome site many times to find reasons why gnome is so memory heavy.  i forget the link but i remember developers stating that a simple hello world program with gtk widgets takes up 500k of memory!  

nat friedman and a few others are offering bounties to help "clean up" gnome.

[http://codeblogs.ximian.com/blogs/benm/archives/000457.html](http://codeblogs.ximian.com/blogs/benm/archives/000457.html)

it seems that the next gnome version might address some memory problems.  i am not sure how big a dent it will make to speed up the 128 meg memory problem though.

i don't have speed issues on my computer.  thats because i run a AMD 64 3000+ with  1G of ram.  i don't think throwing hardware at a OS makes it better.  optimizations make it smarter.

as far as updates go, jdong did a good job answering the question.  if security patches consisted of fixing the file in question, that would make them smaller.  perhaps a new apt-get version could address that problem.  it would cut down on downloads for all apt users and save bandwidth costs for all parties involved.  

gnu/linux is more secure than windows.  in particular, the default ubuntu desktop is more secure than the xp equivalent because ubuntu opens no ports by default.  you could have a warty machine on the internet and it would NEVER get cracked by anyone, ever.  well it would if they have physical access to the machine or you opened a trojan, however to my knowledge not many gnu/linux trojans exist.

as far as the boot speed goes.  the latest version, hoary attempts to address that issue.  it does load signifigantly faster than warty.  not that it matters to me much though, boot speed to me is pretty irrelavent actually.  i would rather more energy be put into making a stable and faster desktop.

---

