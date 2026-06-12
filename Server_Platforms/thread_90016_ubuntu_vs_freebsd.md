---
title: "ubuntu vs freebsd ?"
date: 2005-11-14
forum: Server Platforms
---

### Post by dbee on 2005-11-14
I'm wondering which server to go for. I like ubuntu and I think that it'd make a great production server but there's a few things I'm not too sure about.

I think that I'd probably gravitate towords bsd in the end anyway because of it's stability, security and great TCP/IP stack which makes it the perfect server machine. The last time I tried to install FreeBSD 5.3 ? however it wouldn't accept my harddrive ??? It wanted a WesternDigital clone HD only. 

So anyway my question is this - is there a big difference between running a BSD machine and running a Linux one ?
What are the main differences ?
What aret the advantages / disadvantages in your opinion ?
Can I still run tripwire/nessus/webmin and all the old favorite server apps, on a BSD machine? 

cheers,

---

### Post by Joe_lurker on 2005-11-14
I am a BSD fan for servers.  I run FreeBSD 5.10 on my home server and the big geeks I know at an ISP run FreeBSD for everything.  I have not tried using Ubuntu in server install.

The documentation for FreeBSD is really good plus it installs "standard" applications, ie. it downloads and compiles from source.  This means that the documentation for the apps are available on their respective web sites.

Just my opinion.

-Joe

---

### Post by LordHunter317 on 2005-11-14
[QUOTE=dbee]I think that I'd probably gravitate towords bsd in the end anyway because of it's stability, security and great TCP/IP stack which makes it the perfect server machine.[/quote]It's not any more secure than Linux, and the vaunted BSD TCP/IP stack is absoultely crushed by Linux for general serving tasks, and for high-performance servers, these days.

There are plently of sites that cover the differences, but unless you have a specific reason for running any BSD, you probably have no real need to beyond personal preference.  There's nothing done on BSD that really isn't done better on Linux these days, from a pure technical POV.

---

### Post by closet geek on 2005-11-14
[QUOTE=LordHunter317]
There are plently of sites that cover the differences, but unless you have a specific reason for running any BSD, you probably have no real need to beyond personal preference.  There's nothing done on BSD that really isn't done better on Linux these days, from a pure technical POV.[/QUOTE]

Please can I see some of these sites?

cg

---

### Post by kvidell on 2005-11-14
Now... I'm no expert, but I do have personal experience with this...

We have several small servers in the apartment, and the OpenBSD3.3 runs _much_ more steadfast than the Linux based ones (Fedora, Ubuntu)...

Keep in mind Open3.3 is essentially an ancient kernel with quite a few problems..

Oh, not to mention no major security flaws have been found in the BSD client in around 7 years..
I think BSD excells as a server where Linux can only pretend and hope.

We use our BSD box for serving data to an XBox and as a webserver. It had a 735 day uptime or so, and the ARP cache overflowed, but that's because the XBox doesn't speak TCP very well from what we can determine.
- Kev

---

### Post by Chayak on 2005-11-14
I've used mainly Redhat in the past but I also have experience with FreeBSD and OpenBSD.  OpenBSD is a good system but it uses an older kernel, though it's pretty much secure.  FreeBSD is good as well, stable, not as secure as OpenBSD but more up-to-date.  Linux is well established now and I've not personally had any problems with it.  I was running Redhat on a sonar mainframe and aside from some hardware issues with some processor cards flaking out it handled a constant flood of data 24/7 (ie multiple gigabit fiber connections) without going down.  The best choice I would say is what are you more comfortable administrating.

---

### Post by jdong on 2005-11-14
Performance wise, the difference between a modern 2.6 Linux distribution and FreeBSD are pretty minimal, if any. The security advantages of a BSD system are questionable when compared to Linux (again, it could be a function of exposure and user base size)...

As far as ease of use and maintenance, Linux takes the cake. BSD upgrade management can be extremely time-consuming at times.


For example, our current forums server is running FreeBSD, though we have plans to migrate to CentOS soon, because FreeBSD is becoming more and more of a pain to keep updated. Our server is extremely heavily loaded 24/7, and building updated system components takes hours upon hours on the dual Xeon 2.8, not to mention the great uncertainty of the installation process for updates...

In addition, BSD usually has poorer hardware support than Linux. Out of the 10 or so *nix servers I administer for robotics, less than half of them run FreeBSD perfectly (though FreeBSD is supposed to have the best hardware support out of the BSD's), mostly networking problems.

Don't get me wrong, I'm a BSD lover to a certain degree - I have 2 FreeBSD servers myself. From my experience though, I've yet to see them perform better than Linux in any circumstance, but do require at least double the amount of time to stay up-to-date compared to Ubuntu, while also requiring many many more reboots in the process. If it wasn't for the geek appeal of having some BSD around, those build servers would've been switched over to Linux pronto.

---

### Post by hostile on 2005-11-14
> For example, our current forums server is running FreeBSD, though we have plans to migrate to CentOS soon, because FreeBSD is becoming more and more of a pain to keep updated. Our server is extremely heavily loaded 24/7, and building updated system components takes hours upon hours on the dual Xeon 2.8, not to mention the great uncertainty of the installation process for updates...

Now **that** I find interesting. 

Why would you not want to use your own product, or even straight Debian?

I recently rebuilt my server here and finally chose Ubuntu over CentOS, simply b/c I wasn't that impressed with the community support when compared to Ubuntu.

---

### Post by closet geek on 2005-11-14
[QUOTE=hostile]Now **that** I find interesting. 

Why would you not want to use your own product, or even straight Debian?

I recently rebuilt my server here and finally chose Ubuntu over CentOS, simply b/c I wasn't that impressed with the community support when compared to Ubuntu.[/QUOTE]

I wouldn't opt for CentOS either unless they're thinking of running something like cPanel (surely not!)

cg

---

### Post by s0c0 on 2005-11-14
FreeBSD is good, but its kind of a pain.  I ran FreeBSD on one of my boxes for a while and I think that Debian runs faster than it.   Ubuntu and FreeBSD ran about the same using Gnome.

Why would you choose to use Ubuntu over FreeBSD as server (for a desktop its obvious)?  Why would you choose to use Ubuntu as a server?  No offense, just wondering.

I feel Ubuntu updates there OS to frequently.  How long is a Ubuntu version even supported by them?  I know lots of people still running FreeBSD 4.9.  I used to work at a WISP and they ran all FreeBSD 4.9 and the guy says he want upgrade to the 5.x branch for another few years.

---

### Post by closet geek on 2005-11-14
[QUOTE=s0c0]
Why would you choose to use Ubuntu over FreeBSD as server (for a desktop its obvious)?  Why would you choose to use Ubuntu as a server?  No offense, just wondering.

I feel Ubuntu updates there OS to frequently.  How long is a Ubuntu version even supported by them?  I know lots of people still running FreeBSD 4.9.  I used to work at a WISP and they ran all FreeBSD 4.9 and the guy says he want upgrade to the 5.x branch for another few years.[/QUOTE]

No server should ever run a graphical desktop.

You seem to answer your own question here!! You say Ubuntu update their OS too much yet you mention a friend still using FreeBSD 4.9 even though the FreeBSD project is up to 5.xx ;) 

Dapper will be supported by Ubuntu for 3 years.

cg

---

### Post by jdong on 2005-11-14
Our hosting provider does not offer Debian or Ubuntu... Only CentOS 3 or FreeBSD 4.x (which we both managed to bring up to latest versions before deploying into production)...

To do a custom OS install would be $500 or so, which nobody wanted to give us and we did not find the price justified.

---

### Post by closet geek on 2005-11-14
[QUOTE=jdong]Our hosting provider does not offer Debian or Ubuntu... Only CentOS 3 or FreeBSD 4.x (which we both managed to bring up to latest versions before deploying into production)...

To do a custom OS install would be $500 or so, which nobody wanted to give us and we did not find the price justified.[/QUOTE]

By all accounts this dedicated IP is hosted by rcthost.net - I can't even see dedicated packages on their site?!

cg

---

### Post by LordHunter317 on 2005-11-14
[QUOTE=jdong]Performance wise, the difference between a modern 2.6 Linux distribution and FreeBSD are pretty minimal, if any.[/quote]Not really, for heavy I/O tasking, FreeBSD 5.x is terribly poor, as the SMP rewrite they did hurt things, not helped them.  

The verdict's still out on FreeBSD 6.x, being new and all.

> The security advantages of a BSD system are questionable when compared to Linux (again, it could be a function of exposure and user base size)...There are no advantages, I suppose one can make an argument for a few disadvantages (source built patches are icky), and they're comparable in all other aspects.

[quote=kvidell]Now... I'm no expert, but I do have personal experience with this...

We have several small servers in the apartment, and the OpenBSD3.3 runs _much_ more steadfast than the Linux based ones (Fedora, Ubuntu)...

Keep in mind Open3.3 is essentially an ancient kernel with quite a few problems..[/quote]And place any load on it, and it will fall all over itself.  OpenBSD's kernel isn't stable under disk I/O load at all, or any mixed I/O types.  Older kernels aren't stable under high network I/O load, and it's too easy to push into the realm of KP.

> Oh, not to mention no major security flaws have been found in the BSD client in around 7 years..No, there have been major flaws found.  Just generally not ones trivally exploitable remotely.

[quote=closet_geek]No server should ever run a graphical desktop.[/quote]Anyone who says this hasn't ever had to deal with Oracle.  Frankly, I'm getting kind of sick of this "OMG Hardcore headless UNIX" mentality, as it's really never been true.  

Even "headless" servers frequently have heads in the form of remote X sessions.  

> Please can I see some of these sites?Google "freebsd linux comparison"  Be careful of bias, obviously.

---

### Post by kvidell on 2005-11-14
[QUOTE=LordHunter317]And place any load on it, and it will fall all over itself.  OpenBSD's kernel isn't stable under disk I/O load at all, or any mixed I/O types.  Older kernels aren't stable under high network I/O load, and it's too easy to push into the realm of KP.

There have been major flaws found.  Just generally not ones trivally exploitable remotely.[/QUOTE]Ooh, okay.

Well, like I said, we use it for serving ROMs, music, videos, web stuff, etc.
It hasn't had any major issues. Does it matter that we're running on a 1+0 raid using a 3ware controller? (I'm not being sassy, I'm honestly curious).

And I can see that, as far as the security flaws. :)
Good deal.
- K

---

### Post by s0c0 on 2005-11-14
> **closet geek]No server should ever run a graphical desktop.[/QUOTE]

Tell that to Microsoft.  I disagree if you use something like black box or another very light weight window manager for things like webmin.  I agree that no server should ever be running a full desktop environment or even a rich window manager.

[QUOTE=closet geek]You seem to answer your own question here!! You say Ubuntu update their OS too much yet you mention a friend still using FreeBSD 4.9 even though the FreeBSD project is up to 5.xx  said:**
> 

Did I?  It is my understanding that it is best to update a server as little as possible.  Thats why he hasn't updated from 4.9, because its still solid and very few flaws exist..


[QUOTE=closet geek]Dapper will be supported by Ubuntu for 3 years.[/QUOTE]

This is good.

---

### Post by jdong on 2005-11-14
Again, I don't want to sound too critical of the BSD's. They are excellent OS'es, each with something special of its own.

If my sole job was to maintain one server, without a doubt I'd pick BSD for its ultimate tweakability (thanks to Ports), and their Ports team has been extremely reliable for not releasing broken sources (ahem, Gentoo!). However, because I have so many servers here, I gotta say, Linux wins.

Also, as far as BSD's instability under extremely high loads, I've experienced that a bit, espcially under high net loads with the if_xl driver  (like torrenting at 2MB/5MB) I've gotten FreeBSD 6.0 to kernel panic on me. Sometimes these boxes would have unusual slowdowns, like 1/5 the ordinary build performance. After a reboot, all is restored, though no examiniation of top/ps -aux/ vmstat could reveal the problem.

---

### Post by nocturn on 2005-11-15
FreeBSD is nice, I ran it on my server for almost two years.  
In essence, Linux 2.6 can do everything BSD can, it offers comparable speed, stability and security.

For a single server, FreeBSD's lack of binary updates is a killer.

---

### Post by dbee on 2005-11-15
Thanks guys, this thread is really intersting and it's making me reconsider my position. I'd thought of BSD as the more stable option - and I was under the impression that a quick look at server uptime's on netcraft would lend weight to that position.

I am interested though, since linux is the more dynamic of the two choices - what are the big leaps forward that the linux world has taken ahead of the BSD world ?

I've heard great things about ReiserFS, which I know isn't available for BSD. 
There was also the new threading library that came out of redhat, that I'd heard alot about when I was on gentoo.
And something else about a new compiler that gentoo wasn't supposed to use (for some reason) but that gave a 30-40% faster binary ?

So what are the technical things that in your opinion makes all the difference with linux ??

---

### Post by closet geek on 2005-11-15
dbee: netcraft's uptimes are not to be taken too seriously: [http://uptime.netcraft.com/up/accuracy.html#linux26](http://uptime.netcraft.com/up/accuracy.html#linux26)

cg

---

### Post by LordHunter317 on 2005-11-15
[QUOTE=dbee]I'd thought of BSD as the more stable option - and I was under the impression that a quick look at server uptime's on netcraft would lend weight to that position.[/quote]The few large sites that run FreeBSD use server pools and load balancing anyway, so getting the actually desired uptime statistics is rather impossible.

> what are the big leaps forward that the linux world has taken ahead of the BSD world ?2.6 is more scalable than 5.x, in terms of CPUs it'll effectively task on.  Linux with NPTL has far better threading performance, both synthetic and real-world, than BSD does.  More hardware support.  More filesystem support.  FFS with softupdates isn't bad, but it still has some traditional tasks it's a poor performer for. 

> I've heard great things about ReiserFS, which I know isn't available for BSD. It's great until it crashes.  Then your data is gone.

---

### Post by closet geek on 2005-11-15
[QUOTE=LordHunter317]
It's great until it crashes.  Then your data is gone.[/QUOTE]

Woah! We're already having a FreeBSD vs Linux debate don't think we can all cope with a Reiser vs Everyone else debate.

*mentions he uses vim and runs*

cg ;)

---

### Post by LordHunter317 on 2005-11-15
[QUOTE=closet geek]Woah! We're already having a FreeBSD vs Linux debate don't think we can all cope with a Reiser vs Everyone else debate.[/quote]Well, it's true.  Recovery tools are nonexistent.

---

### Post by jdong on 2005-11-15
> **dbee]
I've heard great things about ReiserFS, which I know isn't available for BSD. 
[/quote]
Correct. Don't listen to the reiserfs fud about crashes and reiserfs... Most of it is not true. There were the days back in the 2.4 kernel days when reiserfs would magically eat hard drives on reboot, and other fun ordeals like that. Recently, reiserfs has emerged as one of the more stable filesystems, right up there with ext3. Its performance is excellent all-around, and latency doesn't look significantly behind ext3 for most tasks (unlike what the highly ext3-biased Redhat says about reiserfs kernel latency).

In addition, as far as recovery tools, recovery is easy on ext3 because of an unhashed directory tree. Ext3 performance advocates will tell you to turn on dir_index, which enables binary hashes for directory indexes. This will bring ext3's recovery level back down to reiserfs, without as great an improvement on actual performance (see namesys.com's benchmarks)

In the end, you're always screwed if certain pieces of the filesystem get magically zeroed out overnight by the supernatural forces. Surely ext3's original layout was simple enough that the rest of the filesystem can be pieced together despite the lack of a piece, but that was at the expense of efficiency. It's a very bad idea to rely on filesystems to protect you from physical hard disk damage  said:**
> 
There was also the new threading library that came out of redhat, that I'd heard alot about when I was on gentoo.

NPTL. Most Linux distros use it nowadays, and it provides a marked improvement in performance of threaded applications.

> And something else about a new compiler that gentoo wasn't supposed to use (for some reason) but that gave a 30-40% faster binary ?
I think you're referring to GCC 3.4 and 4.0? The 30-40% is a very inflated optimistic view, usually only happening on amd64, where GCC 3.3 support was terrible. Ubuntu uses GCC 4.0. FreeBSD is going to switch to it (soon, I guess). Debian Sid and Fedora (core 4, RHEL 5) are there. Gentoo is kinda/sorta there, but they are having just phenomenal difficulty adapting to it!

---

### Post by dbee on 2005-11-15
There is one other thing though, I really like to install everything from source if possible. Especially my LAMP config, call me obsessive - but I really want to know exactly what is in there and exactly what isn't ... and to rewrite the config files from the bottom up as well.

This seems like a task which BSD is more suited for ? 
Not that there is anything wrong with the ubuntu way of doing things but some bits are kinda strange ... why is it highly recommended to not install apache from source on ubuntu for instance ?

---

### Post by jdong on 2005-11-15
[QUOTE=dbee]
This seems like a task which BSD is more suited for ? 
[/quote]
Not necessarily... and BSD doesn't really do everything from source the way you're thinking... Ports automates the whole process, default configs and everything.

> 
Not that there is anything wrong with the ubuntu way of doing things but some bits are kinda strange ... why is it highly recommended to not install apache from source on ubuntu for instance ?
Because **YOU** probably are not as intimately familiar with Apache's source code as the Ubuntu and Debian Apache maintainers to know what extra patches you want onto the Apache install. A lot of times, these guys know better and can fine-tune an Apache distribution, not to mention apply bugfixes and security updates before a new version of Apache is even released. There are all kinds of advantages of installing using your distribution's supported mechanism, whether that be Portage, Ports, RPM, or APT. What you're looking from a distribution is its support....


Sure, you can *examine* the source code however much you want, but know that the Ubuntu build archive merely takes out the x-hour wait from the compile process. What you see is what you get compiled. The idea that you "learn more" when you build something from ground up is kinda nonsensical in this situation. You can "learn more" by dissecting the config files down, examining them.

---

### Post by LordHunter317 on 2005-11-15
To be fair, the Apache configuration setup shipped by any distribution or BSD is hardly fine-tuned for anything.  Most ship as close to the default configuration as possible in terms of values, anyway.

The rest is true: Apache shipped by any distribution (or even BSD) is better than compiling from vanilla source, as vanilla source is rarely a desirable thing for Apache.

Some distributions patch more heavily than others.  Apache in OpenBSD is quite heavily modified, for example.

---

### Post by jdong on 2005-11-15
Not to mention that each distribution's Apache has specific modification that makes it blend better with the rest of the distribution. Fortunately, recently LSB compliant init has really been catching on, because I used to experience initscript conflicts on some older distros.

---

