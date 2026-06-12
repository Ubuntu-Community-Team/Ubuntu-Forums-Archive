---
title: "Ubuntu getting faster and faster?"
date: 2006-05-23
forum: The Cafe
---

### Post by Engnome on 2006-05-23
First when I installed ubuntu (breezy) it wasnt very fast.  (Its crashed all the time too) so I removed it very fast.

Tried out some other dists wich felt faster but there was something they missed, even tried some BSD variants wich were extremely fast. They put both XP and all Linux dists I've tried far behind them in terms of speed.

But then some time later I decided to try dapper out. In the beginning it wasnt very fast either but atleast it didnt get any slower (like windows) But after some major updates (like a 190+ updates 1 week ago and 120 or so today) it has felt like opening that particular app took 2 seconds less than before, booting maybe 4 seconds faster. Im now working in an extremely fast dapper installation and Im no longer annoyed beacause I have to wait for some app to start. 

I am wondering: Do you feel the same? Or is it just me getting used to the slowness? After years with windows it feels strange that an OS actually gets faster as time goes by, especially when you use it as much as I do and like experimenting and installing new stuff alot.

If alot of people think I'm right than this might be one of the biggest advantages over windows I have found yet. (Im a speed freak, windows classic in XP is the only acceptable theme for me)

---

### Post by G Morgan on 2006-05-23
Yeah I've found that Dapper is more efficient than Breezy. True progress of the kind that is a utilisation of resources rather than a wastage like Vista.

Also I use Geoshell rather than use any of the normal themes with XP. It loads much nicer without explorer.

---

### Post by nalmeth on 2006-05-23
I think the speed improvements come from the new kernel series.
I have personally noticed as well, though other's have not.

If you're a speed freak (and occaisionally have time to let the computer sit, possibly for hours) you should install prelink. It will speed up the start-times of all your applications, but the actual process of prelinking can take time.

There is also some risk involved, but I've only heard vague notion's of risk, and never personally experienced them.

---

### Post by LKRaider on 2006-05-23
Dapper boots in 34 seconds to the login screen here. And Gnome fully loads in about ~10-15 seconds after that.

This beats by far the WinXP boot, which is fast to get to the main screen (~40 secs), but takes ages to give a fully working desktop (+2min), given the antivirus, firewall + other services it got to run to work (you can't do anything in the meanwhile, since it takes all cpu and thrashes the harddrive while loading them).

Only place Win still beats my Dapper is on shutdown, while WinXP takes ~5secs, Dapper takes from 20 to 30secs.

No other distro I tried is as fast as Dapper.

---

### Post by towsonu2003 on 2006-05-23
[QUOTE=G Morgan]Yeah I've found that Dapper is more efficient than Breezy. [/QUOTE]
opposite for me... boots fast and all, but all that firefox slowness, desktop rendering slowness thc are driving me nuts... and I can't file a bug report bc I've no idea why it's doing that, where it's doing that, and what's doing that, especially bc it has the same X setup/configuration that I had with breezy. 

we'll see ;)

---

### Post by Engnome on 2006-05-23
Ok thanks for the input.

[QUOTE=nalmeth]I think the speed improvements come from the new kernel series.
I have personally noticed as well, though other's have not.[/QUOTE]

The new kernels seem to do some improvements, everytime I boot after the "Restart Requiered" It feels faster.

Installing the 686 instead of the 386 made a huge difference aswell

I'll look into prelink, speed is more important than stability. (within reasonably limits of course)

[QUOTE=G Morgan]Also I use Geoshell rather than use any of the normal themes with XP. It loads much nicer without explorer.[/QUOTE]

Thanks, didnt know something like that existed. Gonna check it out.

---

### Post by BoyOfDestiny on 2006-05-23
[QUOTE=Engnome]First when I installed ubuntu (breezy) it wasnt very fast.  (Its crashed all the time too) so I removed it very fast.

Tried out some other dists wich felt faster but there was something they missed, even tried some BSD variants wich were extremely fast. They put both XP and all Linux dists I've tried far behind them in terms of speed.

But then some time later I decided to try dapper out. In the beginning it wasnt very fast either but atleast it didnt get any slower (like windows) But after some major updates (like a 190+ updates 1 week ago and 120 or so today) it has felt like opening that particular app took 2 seconds less than before, booting maybe 4 seconds faster. Im now working in an extremely fast dapper installation and Im no longer annoyed beacause I have to wait for some app to start. 

I am wondering: Do you feel the same? Or is it just me getting used to the slowness? After years with windows it feels strange that an OS actually gets faster as time goes by, especially when you use it as much as I do and like experimenting and installing new stuff alot.

If alot of people think I'm right than this might be one of the biggest advantages over windows I have found yet. (Im a speed freak, windows classic in XP is the only acceptable theme for me)[/QUOTE]

I think a lot of the improvements stem from gnome getting snappier. 

I can only wonder how fast Ubuntu is on one of those fancy new rigs... Fast greasy speed...

---

### Post by nalmeth on 2006-05-23
Yeah, I installed the i686 kernel for my hyper-threading PC, and it's just blazing. 
Firefox opens in less than 2 seconds if its the first time since boot, less than 1 if I've opened it already.
I'm afraid to prelink as well, fearing my eyes will pop!

---

### Post by Lovechild on 2006-05-23
One thing is that GNU+Linux is really at this point rather feature complete for your general Desktop. This means developers now have an chance to develop tools to detect performance bottlenecks (see Frysk, systemtap, strace, valgrind, etc.) There is simply no urgent need to spend cycle after cycle adding funtionality anymore, we can polish the system.

I think the thing that really changed overall speed has been the efforts of Red Hat, Sun and Novell to give us tools and more importantly collect real data to pin point problems and teach programmers how to use these tools.

---

### Post by Engnome on 2006-05-23
[QUOTE=nalmeth]Yeah, I installed the i686 kernel for my hyper-threading PC, and it's just blazing. 
Firefox opens in less than 2 seconds if its the first time since boot, less than 1 if I've opened it already.
I'm afraid to prelink as well, fearing my eyes will pop![/QUOTE]

If you have hyper threading arent you supposed to use the smp kernel?

---

### Post by BoyOfDestiny on 2006-05-23
[QUOTE=Engnome]If you have hyper threading arent you supposed to use the smp kernel?[/QUOTE]

I believe the kernels have built in support for SMP now...

---

### Post by nalmeth on 2006-05-23
To the avail of my research I thought I had to install i686. I don't know about the SMP kernel, but will look into it, thanks. I did notice a big difference, so I think I still may have the right kernel already.

---

### Post by Lovechild on 2006-05-23
[QUOTE=Engnome]If you have hyper threading arent you supposed to use the smp kernel?[/QUOTE]

There is really very little reason to not run a SMP kernel, even on UP setups - it reduces the amount of kernels that need to be supported and the overhead on modern CPUs is very close to zero - e.g. the athlon series CPUs factor out the locks in a very efficent manner.

It would also solve support issues when it comes to detecting dual-core and SMT setups as those would just work on the stock kernel (Breezy e.g. didn't detect my AMD64 X2 so I had to manually install the SMP kernel).

I can say that FC5 has only SMP kernels for the x86_64 distribution and FC6 just switched to SMP only for i386. Not one person has complained about performance issues and it really does make the maintainers life a bit easier.

---

### Post by G Morgan on 2006-05-23
Just to clarify. I saw huge increases in FPS in glxgears though that maybe because of a later Nvidia driver. I do find the OS runs a little quicker in general though. It's just a pain that Emacs has stopped working. Luckily I use Kdevelop a bit so Kate is a simple transition for now.

---

### Post by graabein on 2006-05-23
Wasn't one of GNOME 2.14's goals also to be faster?

[A Look at GNOME 2.14]("http://www.gnome.org/~davyd/gnome-2-14/")

---

### Post by 23meg on 2006-05-23
Dapper is much snappier and boots much faster (+-30 secs) over here. Especially with the stock XGL + Compiz, both of which have been stable so far, I have much improved 2D graphics performance, and thus it *feels* faster as well as actually *being* faster due to new internals such as the newer kernel, initng, etc. GNOME startup speed has also seen a huge increase, almost twofold.

---

### Post by teet on 2006-05-23
> Only place Win still beats my Dapper is on shutdown, while WinXP takes ~5secs, Dapper takes from 20 to 30secs.

No other distro I tried is as fast as Dapper.

Windows hibernation on my machine is also MUCH MUCH faster...like it takes 3-4 seconds tops to hibernate in windows (and yes, I know the difference between "hibernate" and "standby") and about as long to come out of hibernation.

But in general, I must agree that Dapper does indeed feel much snappier than breezy (most likely due to the improvements in Gnome 2.14).  I've never been able to tell much of a difference between the 386/686 kernels though...and warty, hoary, and breezy all felt around the same speed in my opinion.    

-teet

---

### Post by dyssident on 2006-05-23
[QUOTE=LKRaider]This beats by far the WinXP boot, which is fast to get to the main screen (~40 secs), but takes ages to give a fully working desktop (+2min)[/QUOTE]

this really shows that special sort of diabolical microsoft genius. cant make it boot faster? pop up the log in screen super fast and most will be fooled.

---

### Post by Lucho on 2006-05-23
I never had speed problems with Breezy, but then again I use
the 64-bit version. No real performance advantage ( :( ) but the system
is in general snappier than XP. So far, I'm only testing Dapper in 32-bit
mode, but so far, so good.
       Here's a question for those who love speed: Have you checked the 
swappiness of the system (i.e. how much the system accesses the HD
and uses swap memory over RAM. Even with 1 GB, the system will tend 
to swap from time to time)? It's normally set at 60 for most distros, inc.
Ubuntu. Lower it to 10, and you'll be *amazed* at the difference it makes.
      8) 8)

---

### Post by adamkane on 2006-05-23
Prelinking is a lot of work for small benefit. Not necessary. Not worth the effort.

Installing the correct kernel is all you need.

---

### Post by Lucho on 2006-05-23
I said swappiness, not prelinking. It's no work at all, and only sets the
system to favor RAM over swap and HD (thus accessing the HD less).

---

### Post by adamkane on 2006-05-23
Sorry. I was responding to an earlier post.

I agree. Swappiness is good.

---

### Post by Lovechild on 2006-05-23
[QUOTE=adamkane]Prelinking is a lot of work for small benefit. Not necessary. Not worth the effort.

Installing the correct kernel is all you need.[/QUOTE]

A lot of work. you have got to be kidding me.

sudo apt-get install prelink
vi /etc/defaults/prelink (change unknown to yes)
/etc/cron.daily/prelink

That is about 3 steps more than on Fedora though since they deploy it by default without any issues and plenty of loadtime improvements.

---

### Post by nalmeth on 2006-05-23
When you need it, any increase is good.

Prelinking was well worth it for me, even though I had to let it sit overnight to prelink after a huge update.

If anything, it's worth waiting till you're not getting daily updates.

How much effort is it really? Once integrated with apt, it prelinks automatically every time you install anything. Waiting is different than effort. 

Hmm... Waiting, for speed increase... Sound's funny

---

### Post by adamkane on 2006-05-23
How do you adjust swappiness again?

---

### Post by Clay85 on 2006-05-23
I think I messed something up. Nothing is happening:

[QUOTE=Enzo's Terminal]enzo@reboot:~$ cd /etc/default/prelink
bash: /etc/default/prelink: Permission denied
enzo@reboot:~$ su
Password:
root@reboot:/home/enzo# cd /etc/default
root@reboot:/etc/default# gedit prelink

(gedit:32726): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
root@reboot:/etc/default#
root@reboot:/etc/default# cd
root@reboot:~#  sudo /etc/cron.daily/prelink

[/quote]
And the cursor is blinking underneath the last line.

What's happening? :(

Edit: After gedit prelink the terminal gave me that warning, opened up the file, and I changed Unknown to Yes, just as in the directions.

Edit2: After a very very very long wait (I got dinner), I received "root@reboot:~#" :D Does that mean it worked?

Edit3: This is so fast I may need some Aloe Vera; I think I have wind burn. x.x

---

### Post by Lucho on 2006-05-24
I tried to find the original article, but it's apparently gone. However,
here's how to adjust the swappiness- add this to the  /etc/sysctl.conf
file (you need root access, so you'll probably have to sudo it):
```
vm.swappiness=10
```
This will set the swappiness to 10 at the next bootup- I'm still looking
for the command to lower it on the spot.
  The number is normally set to 60; the lower the number the more
the system favors RAM and accesses less the HD in general (but it
also says that going below 10 can harm the system's stability).

---

### Post by mcduck on 2006-05-24
[QUOTE=Lucho]I tried to find the original article, but it's apparently gone. However,
here's how to adjust the swappiness- add this to the  /etc/sysctl.conf
file (you need root access, so you'll probably have to sudo it):
```
vm.swappiness=10
```
This will set the swappiness to 10 at the next bootup- I'm still looking
for the command to lower it on the spot.
  The number is normally set to 60; the lower the number the more
the system favors RAM and accesses less the HD in general (but it
also says that going below 10 can harm the system's stability).[/QUOTE]
try this:
```
sudo sysctl -w vm.swappiness=10
```

---

### Post by jdong on 2006-05-24
Breezy was a relatively slow release. The transition to GCC 4.0 and cairo lead to slower compiled code and slower graphical rendering, especially visible in Firefox which was 3-4x slower than stock mozilla.org's firefox.

By the time Dapper rolled around, most of these initial troublemakers have been 'fixed' by upstream. Bootup speed was thanks to the Ubuntu team investigating bootup bottlenecks.


I do feel that Dapper is improving with respect to speed.



P.S. In Dapper, all non-386 kernels are SMP by default... In Breezy and below there used to be a separate -smp kernel.

---

### Post by jdong on 2006-05-24
[QUOTE=Lucho]I tried to find the original article, but it's apparently gone. However,
here's how to adjust the swappiness- add this to the  /etc/sysctl.conf
file (you need root access, so you'll probably have to sudo it):
```
vm.swappiness=10
```
This will set the swappiness to 10 at the next bootup- I'm still looking
for the command to lower it on the spot.
  The number is normally set to 60; the lower the number the more
the system favors RAM and accesses less the HD in general (but it
also says that going below 10 can harm the system's stability).[/QUOTE]

I'd like to take a stab at trying to explain this more accurately:

One job of the OS's memory manager is to balance memory usage between applications and cache. For example, a busy fileserver really benefits from having a larger cache so that it doesn't always have to go to disk to look for files, even if that means some other services have to be swapped out to make room for cache. Meanwhile, an actively multitasking desktop benefits a lot more from trying to keep every program in RAM, because at any given time the user can request to bring up an 'idle' program, and if it was cached then it would take seconds to bring it out of swap, nullifying any benefits the cache would've had.


The vm.swappiness number tunes how the memory manager balances cache vs applications. A setting near zero means that applications are more favored, while a setting near 100 means that caching is more favored. The default setting is 60, which is more or less ideal for a server or average system.

However, on a super heavily multitasking system, or on a system with low amounts of RAM (256 or under), for desktop responsiveness most of the RAM should be used to keep applications out of swap. As a result, you can set vm.swappiness to a low number, like 10. Setting it too low may allocate too little cache, in which case you may get excessive disk trashing (and thus slowdowns) from rereading the same data over and over again.

---

### Post by Lovechild on 2006-05-24
This might also be of interest for a performance boost..

Yours truly presents ext3 with dir_index b-trees.
[http://ubuntuforums.org/showthread.php?t=37806](http://ubuntuforums.org/showthread.php?t=37806)

---

### Post by ihavenoname on 2006-05-25
[QUOTE=Lovechild]
I can say that FC5 has only SMP kernels for the x86_64 distribution and FC6 just switched to SMP only for i386. Not one person has complained about performance issues and it really does make the maintainers life a bit easier.[/QUOTE]
FC6? its out yet? or are u using rawhide? What are gonna be some of the main features...I  have a soft spot for fedora,,,but maybe this is the wrong thread:-D  PM me or something I wanna hear about where fedora is going.

---

### Post by jdong on 2006-05-25
Well, Fedora has never been a performance king since around Core 2... SELinux and their other protection measures killed performance compared to other distros.

Now, I'm not ripping on Fedora or anything... if any other distro wanted SELinux security, they'd have to pay the same price.


I've never seen benchmarks of SMP vs UP kernels on a UP system... that'd be interesting to take a look at.

---

### Post by jdong on 2006-05-25
Video performance seems improved in the new fglrx... I'm getting a few more FPS'es out of UT2004 than before.

Also, aticonfig --lsp shows the currently active state with a star. A lot of other little things were fixed here and there... more aticonfig options, the GUI control panel, actually working, and so on.

I'm pretty impressed with ATI's Linux support...

---

### Post by Robgould on 2006-05-25
The SMP and 686 kernel are the same now. They used to be different. If you select 686-smp it installs the 686 kernel.
 
I tired prelinking in Breezy.  I could not "feel" any real differnce at all.  I have not tried it with Dapper though.

---

### Post by Lovechild on 2006-05-25
[QUOTE=jdong]Well, Fedora has never been a performance king since around Core 2... SELinux and their other protection measures killed performance compared to other distros.

Now, I'm not ripping on Fedora or anything... if any other distro wanted SELinux security, they'd have to pay the same price.


I've never seen benchmarks of SMP vs UP kernels on a UP system... that'd be interesting to take a look at.[/QUOTE]

Jdong, you should know better than to make performance claims without evidence. You make it sound like someone tied a 10 ton lead weight to the system which definately isn't true.

The average overhead in runtime for the proactive security deployed in FC is very small - yes it's there but Fedora is also highly tuned for performance (more so than Ubuntu), be that using compiler tricks, prelinking, optimized filesystem functionality.

If it "killed" performance I would definately like to see out of the box comparisons between FC5 and Dapper (this should be more than fair - FC5 has been out for a while now, Dapper is set for release in about 2 weeks time if I'm not mistaken) - if the difference is more than statistically insignificant, I will buy you beer. 

Since you made the claim the burdon of proof is on you.

For my money the slight overhead we will see is definately worth it considering we defeat about HALF of all security flaws without need for patching (this is deeply significant for longterm support).

[quote=ihavenoname]
FC6? its out yet? or are u using rawhide? What are gonna be some of the main features...I have a soft spot for fedora,,,but maybe this is the wrong thread PM me or something I wanna hear about where fedora is going.
[/quote]

I run Development, as development isn't very far along the featureset for FC6 isn't set in stone.

The major points will be development on the Stateless Linux project, the One Laptop Per Child project and the Fedora Rendering project (AIGLX and related bling). The FC6 test1 freeze is coming up and that should show you a bit of what has been worked on - overall, Xen works nicer, security is better and of course the application set has been upgraded to the latest versions (GNOME 2.15.x entered the tree yesterday e.g.)

You can get videos from the FUDCon 2006 meeting in Boston here:
[http://torrent.fedoraproject.org/torrents/FUDConBoston2006.torrent](http://torrent.fedoraproject.org/torrents/FUDConBoston2006.torrent)

During the FC6 talk you will notice some desires for this cycle. You can also look here:
[http://fedoraproject.org/wiki/FC6Future](http://fedoraproject.org/wiki/FC6Future)

Longterm I can say that Red Hat hired Ralph Giles (of Xiph.org and Ogg Vorbis fame) to fix audio on Linux for good, but this is probably not going to make it into FC6 as it's a rather longterm project, FC7 would probably be the target if I understand him correctly. There is also a lot of development time being poured into tools like Frysk and SystemTap, not that you will see that as an enduser but these tools will help with optimization and bug detection.

SELinux keeps improving leaps and bounds.

The final thing we might want to highlight is davidz' (of HAL fame) work on PolicyKit which overall looks to solve a lot of security concerns regarding priviliaged programs (say when you gksu a program - this technically requires you to trust a bunch of code like gtk+ with root access.. which isn't desirable).

Overall Fedora is racing along, how much of this we'll see in FC6 is uncertain but it will get here when it's ready. The final thing to note, the past month or so since FC5 came out Development has been rather stable and thus boring, that ended yesterday with a few massive updates - this means the fun has started and we might start to see some code evolution take place.

---

### Post by jdong on 2006-05-25
[http://www.linuxquestions.org/questions/showthread.php?p=2248023#post2248023](http://www.linuxquestions.org/questions/showthread.php?p=2248023#post2248023)

Stopwatch timed common operations for Fedora vs Ubuntu


[http://www.phoronix.com/scan.php?page=article&item=404&num=2](http://www.phoronix.com/scan.php?page=article&item=404&num=2)

Concrete Fedora 5 vs Fedora 4  benchmarks.


And also, just feel... I have FC5 and Ubuntu dual-booting on an older PIII, and you can _clearly_ feel that Fedora Core runs a lot slower than Ubuntu. The difference is much less significant on a new shiny computer, like my Core Duo laptop, but log operations and 3D games do show noticeable losses (UT2004 is 45FPS vs 50FPS)

---

### Post by Lovechild on 2006-05-25
[QUOTE=jdong][http://www.linuxquestions.org/questions/showthread.php?p=2248023#post2248023](http://www.linuxquestions.org/questions/showthread.php?p=2248023#post2248023)

Stopwatch timed common operations for Fedora vs Ubuntu

[http://www.phoronix.com/scan.php?page=article&item=404&num=2](http://www.phoronix.com/scan.php?page=article&item=404&num=2)

Concrete Fedora 5 vs Fedora 4  benchmarks.

And also, just feel... I have FC5 and Ubuntu dual-booting on an older PIII, and you can _clearly_ feel that Fedora Core runs a lot slower than Ubuntu. The difference is much less significant on a new shiny computer, like my Core Duo laptop, but log operations and 3D games do show noticeable losses (UT2004 is 45FPS vs 50FPS)[/QUOTE]

I did a Dapper install yesterday to see how far along your guys were and performance has increased however I don't feel much of a difference from my FC Development install. We both know that "feelings" lie, they are naturally tainted and easy to fool - we have to have hard data.

The Phoronix data needs to be updated to not use a test release - which is slower because Dave Jones had stuff like slab debugging enabled in the kernel most of the way through the cycle. This has a serious and meassurable effect on performance naturally you'd expect to see this. That is the reason why development releases is a bad idea unless you make damn sure that kind of thing is turned off. I think his conclusion is based on false premises and guess work.

Stopwatch tests are noturiously bad and not much information is given on the test (it sounds a little like he has both OSes installed on the same machine and dual boot - which isn't a fair test). We might also both agree that something hanging for 12 secs is very unnatural even on old setups and I suspect this might be a bug or configuration flaw he is encountering, which we should definately looking into (this also require WAY more data than he provides).

I would really like to agree upon a set of tests and do this under a controlled environment. I'm pretty confident that every distro will perform about the same since I haven't seen anything to unsettle me from that belief. 
However since you did provide at least some data I guess I owe you a cold one.

---

### Post by jdong on 2006-05-25
Lovechild:

A lot of this "speed" thing between distros do go by feeling. After all, if you think about it, at the end of a desktop user's day it's indeed the feeling that matters.

I go by experience in saying that Ubuntu is more "responsive" than FC when I used it extensively (Core 3 and 4)... The types of complaints I have usually are related to heavy IO in background and trying to work with desktop apps in the foreground... I've had cases where FC3 would even have trouble responding to mouse movements smoothly.

It might've been something about my configuration... hardware or software, that caused the problem, but it definitely made the OS slower.


I'm definitely not a Fedora hater by any means... you've been in my Fedora threads before... I'm just sharing an experience.


And I agree with you on detailed benchmarking. If only there was a good way of setting this thing up to reflect average use cases

---

### Post by ComplexNumber on 2006-05-25
**jdong**
try FC5. i find it *very* responsive...even more so than FC4. the fact that i have SElinux disabled may play a part. my linux box isn't connected to the internet, so there is no point in me running SElinux. its true that it slows things down.

---

### Post by Lovechild on 2006-05-25
[QUOTE=ComplexNumber]**jdong**
try FC5. i find it *very* responsive...even more so than FC4. the fact that i have SElinux disabled may play a part. my linux box isn't connected to the internet, so there is no point in me running SElinux. its true that it slows things down.[/QUOTE]

for reference:

Disabling SELinux is easy (either use the tool or simply boot with selinux=0) for testing purposes, but I honestly don't feel a difference these days, they really did a lot of work reducing the overhead. I strongly recommend keeping it enabled unless you have a really good reason, it doesn't get in your way nor does it slow you down and the extra security is nice to have.

FC5 is really a great distribution, I highly recommend trying it out.

---

### Post by ComplexNumber on 2006-05-25
[quote=Lovechild]for reference:

Disabling SELinux is easy (either use the tool or simply boot with selinux=0) for testing purposes, but I honestly don't feel a difference these days, they really did a lot of work reducing the overhead. I strongly recommend keeping it enabled unless you have a really good reason, it doesn't get in your way nor does it slow you down and the extra security is nice to have.

FC5 is really a great distribution, I highly recommend trying it out.[/quote] i suppose the word "disabling" is the wrong word for me to use. it was never enabled in the first place on FC5 (ie i set it to "disabled" during the installation of FC5). i ran it briefly in FC4 to see what the performance difference was. that was all.
i do have a good reason ot to run SElinux - i don't have an internet connection for my linux box :). i'm not really concerned about the finer details.

---

### Post by Lovechild on 2006-05-25
[QUOTE=ComplexNumber]i suppose the word "disabling" is the wrong word for me to use. it was never enabled in the first place on FC5 (ie i set it to "disabled" during the installation of FC5). i ran it briefly in FC4 to see what the performance difference was. that was all.
i do have a good reason ot to run SElinux - i don't have an internet connection for my linux box :). i'm not really concerned about the finer details.[/QUOTE]

Hence the "For reference"

---

### Post by jdong on 2006-05-25
I'm glad to hear Fedora's improvements since the last time I used it extensively. That's awesome for everyone :)

I echo Lovechild's recommendation to play with Fedora Core. It _is_ really cool

---

### Post by 23meg on 2006-05-25
I'd have to say that *all distros* are getting faster and faster, whatever your definition of speed is, which is a Good Thing for all, and hardly a surprise. Just install Warty or FC3 which were the latest and greatest about a year ago side by side with Dapper or FC5 and see the difference. Development is not only getting faster; it's accelerating at a greater rate as well.

---

### Post by ihavenoname on 2006-05-25
[QUOTE=23meg]I'd have to say that *all distros* are getting faster and faster, whatever your definition of speed is, which is a Good Thing for all, and hardly a surprise. Just install Warty or FC3 which were the latest and greatest about a year ago side by side with Dapper or FC5 and see the difference. Development is not only getting faster; it's accelerating at a greater rate as well.[/QUOTE]

Id have to agree Ive been distro hopping for a while now, it used to be the Arch Linux  could run circles aroung the bigger distros like Fedora and Ubuntu but now the speed diffrence is not as big.( although I would love it if Ubuntu went i686, do alot of ppl have i386s anymore?)

and on the FC issue, yes FC5 is very fast and i usually disable SElinux cause I like to use reiserfs, but even when I had selinux on it was still about the same speed. However I did like the overall theme that FC4 had, (maybe it was just that it was my first distro) it was darker and seemed cooler, maybe a bit more proffesional as well. Even thou the new theme is kind of nice I still favor the old one. In anycase despite the fact that I will always have "a special place in my heart" for Fedora, since using the Dapper development (starting a few weeks back) I have notice that in general Ubuntu is much better ironed out not as many little quirks. For example on Fedora when I log out X always restarts (..crashes) that doesnt happen on Ubuntu, and its still in development. 

In anycase, the future of linux is looking really good. Let's hope it continues

---

### Post by ComplexNumber on 2006-05-25
> For example on Fedora when I log out X always restarts
that doesn't happen for me.  i don't why its happening for you.


come to think of it, FC5 is by far the best distro i've ever used.

---

### Post by ihavenoname on 2006-05-26
[QUOTE=ComplexNumber]that doesn't happen for me.  i don't why its happening for you.


come to think of it, FC5 is by far the best distro i've ever used.[/QUOTE]
Hm, well I'm glad it worked out for you! Do you have an Nvidia card? ( I do)

---

### Post by Lovechild on 2006-05-26
[QUOTE=ihavenoname]Hm, well I'm glad it worked out for you! Do you have an Nvidia card? ( I do)[/QUOTE]

nVidia cards will work out of the box, however given strict freedom guidelines you will get no 3d acceleration - that is an issue I would recommend you take up with nVidia.

[quote=http://msn.com.com/2100-3513_22-6061491.html]
For Nvidia, intellectual property is a secondary issue. "It's so hard to write a graphics driver that open-sourcing it would not help," said Andrew Fear, Nvidia's software product manager. In addition, customers aren't asking for open-source drivers, he said.
[/quote]

So as you can see they also seem to think that FOSS people are to stupid to actually make use of their code as well as there not being any demand..

Want to help change their mind?

---

### Post by ComplexNumber on 2006-05-26
[quote=ihavenoname]Hm, well I'm glad it worked out for you! Do you have an Nvidia card? ( I do)[/quote]
yup, i've got an nvidia goforce 200

---

### Post by Engnome on 2006-05-26
[QUOTE=23meg]I'd have to say that *all distros* are getting faster and faster, whatever your definition of speed is, which is a Good Thing for all, and hardly a surprise. Just install Warty or FC3 which were the latest and greatest about a year ago side by side with Dapper or FC5 and see the difference. Development is not only getting faster; it's accelerating at a greater rate as well.[/QUOTE]

Yeah of course software gets faster and faster. But it feels like MY dapper installation is getting faster all the time. The software patches are not only keeping up with me installing/changing working  with my system (wich have to slow down some right?), It actually beats it and speeds up. That is impressive.

---

### Post by ihavenoname on 2006-05-27
[QUOTE=ComplexNumber]yup, i've got an nvidia goforce 200[/QUOTE]

did you install the livna driver or did you compile your own? (Im using the lvina one, the problem also happens in arch linux, for somereason Ubuntu is the only distro where gdm does not restart when I logout..hmm)

---

### Post by jakepoz on 2006-05-31
I disagree with the speed improvements.

Also, there is a HUGE problem with GUI starvation during heavy disk usage:

[https://launchpad.net/distros/ubuntu/+source/linux-meta/+bug/31766](https://launchpad.net/distros/ubuntu/+source/linux-meta/+bug/31766)

---

