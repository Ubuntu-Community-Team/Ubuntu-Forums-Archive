---
title: "How hard is to manage a dedicated server?"
date: 2010-05-09
forum: Server Platforms
---

### Post by igorb on 2010-05-09
Hi all,

I am thinking of getting this unmanaged dedicated server hosting:
[http://www.hetzner.de/en/hosting/produkte_rootserver/eq4/](http://www.hetzner.de/en/hosting/produkte_rootserver/eq4/)

I think of installing ubuntu server on it and use it as:
- Apache, PHP, MySql server
- IMAP mail server
- backup server

Now the big question - how hard is it to manage ubuntu server?

I have a lot of experience as windows network administrator, PHP and MySQL developer, I have some experience with apache on windows.

I was able to succesfully install php and mysql on ubuntu server through ssh. But I have no experience managing mail server. How hard is it to manage such server, so it will be secure enough. 

What book would you recommend for this topic?

Thank you in advance for all your answers!

---

### Post by EarthMind on 2010-05-09
It's quite exhausting trying to get used to the compiling. If you're just relying on apt-get then it shouldn't be that troublesome.

Configuring software and security are another matter... Keeping the firewall up to date, making sure that your mail server works correctly and that no one can abuse it, checking the logs on the a frequent basis., etc.

---

### Post by igorb on 2010-05-09
Thanks for your reply EarthMind.

Should I be compiling all the sotware? Are there any disadvantages to apt-get.

I don't have much experience with updating software on linux, how hard or complicated can it be?

---

### Post by EarthMind on 2010-05-09
Technically, you don't have to compile anything because apt-get comes with a bunch of ready to use software. But in many cases apt-get isn't sufficient (which is also its disadvantage), such cases can be:

- the officially supported version or outdated or there is none;
- it's missing customizations you need;
- you want to compile stuff just for the sake of security/reliability;
- etc.

If you just need a basic server that hosts your website then apt-get is what you need. However, for maximum control and the best stability and security you'll need to do the dirty work. But if that were the case then you should be using CentOS/Debian (or any commercial Enterprise Linux) instead.

---

### Post by igorb on 2010-05-09
Thank you so much for your help!

This server would not be used for any high traffic enterprise website, just small websites  that I develop.

I did read though that Ubuntu server is not supposed to be any worse than other enterprise servers, it just depends on preferences of a user, but I'm not the one to judge :)

So Ubuntu server doesn't have any "semi-automatic" utility to provide security updates for operating system?

---

### Post by Xipher on 2010-05-09
Actually in the recent releases you can configure it to do automatic updates. I've not used that myself since I prefer to handle updates on my own time so I don't know more about it but I suspect you can find more information in the Ubuntu Server documentation.

---

### Post by EarthMind on 2010-05-09
What differentiates Debian and Enterprise Linux distro's - such as CentOS - from Ubuntu is that they thoroughly test their software for stability issues before they make it available. Unfortunately this stability also comes with drawbacks, i.e. that the software repositories have (sometimes very) outdated software, which makes it harder for you to upgrade certain software. Ubuntu also comes with more frequent updates, which I noticed that most people find annoying, especially _when they need to reboot_ or _when it breaks stuff_. Rebooting can be circumvent with third party software such as ksplice, but updates breaking other software can be a real pain in the ***.

My conclusion: Ubuntu is good enough for small servers and great for development servers but I personally would never use it mission critical servers. My personal choice has always been CentOS and when I need a more up-to-date system I choose Debian.

---

### Post by igorb on 2010-05-09
Xipher and EarthMind, your information is very valuable to me, thanks.

I am now thinking more in direction of moving to Debian. Since Ubuntu is based on Debian, what really are the biggest differences? 
Is it just about included software packages and basic configuration?

Thanks!

---

### Post by EarthMind on 2010-05-09
Yes, that and the difference in stability & reliability.

---

### Post by igorb on 2010-05-09
So I guess there really isn't any reason to stick with ubuntu for such use.
I am now only deciding what would be easier for me - Debian or CentOS. I do think there is more documentation for Debian.

---

### Post by Vegan on 2010-05-09
I use Webmin to manage my Linux machines and I have them set for manual updates, so its not a big deal.

One is my web server, the other is down while I fix it. Need a CPU, some RAM to bring it up.

---

### Post by windependence on 2010-05-09
> **igorb said:**
> So I guess there really isn't any reason to stick with ubuntu for such use.
I am now only deciding what would be easier for me - Debian or CentOS. I do think there is more documentation for Debian.
Personally, I would go with CentOS if you are set on deploying Linux. CentOS IS Red Hat. There is no difference. It is stable and you will find probably more up to date than Debian because Debian uses absolutely stable software in their distro - nothing wrong with that but some packages are quite old because of that.

That all being said, if I want a really stable system with reasonably updated software, I deploy on FreeBSD or if I want absolute security, OpenBSD. Note that these are not Linux, but real Unix. Free also. IMHO way more simple and far more stable than any Linux distro out there.

-Tim

---

### Post by igorb on 2010-05-10
Thanks for all great tips!

I think I will try out CentOS and Debian and I'll see what will give me least trouble.

Thanks

---

### Post by EarthMind on 2010-05-10
I also just noticed that the Ubuntu server uses WAY more RAM by default. Or maybe it's because I'm running Ubuntu server in virtualbox.

I dunno, just be cautious :)

I've always been using CentOS as server OS but I'm growing quite tired of it because of all the missing and outdated software. Yes, I really care about stability, I mean, who wouldn't? But up-to-date software is almost as important to me, because finding and compiling all the dependencies is a real pain. Therefore I'm going to try Debian next time.

---

### Post by igorb on 2010-05-10
I will just try all three and see which will be the easiest to setup. Ubuntu server 10.04 LTS still seems like a good option.

What is the easiest way to monitor resources? So I could compare results of all three...

---

### Post by EarthMind on 2010-05-10
Use webmin to get a graphical interface of your stats.

---

### Post by igorb on 2010-05-10
That seems to be good idea :) Thanks a lot EarthMind

---

### Post by Kljuka on 2010-05-10
It really depends on what you want from your server. I have to say I'm perfectly happy with my dedicated Ubuntu Server. And regarding the fact that Ubuntu is becoming a mainstream Linux distribution, this might be a good investment for the future.

But again, this is my opinion.

---

### Post by lavinog on 2010-05-10
> **EarthMind said:**
> I also just noticed that the Ubuntu server uses WAY more RAM by default. Or maybe it's because I'm running Ubuntu server in virtualbox.

I dunno, just be cautious :)



The ram issue could be ureadahead:
[http://ubuntuforums.org/showthread.php?t=1363165](http://ubuntuforums.org/showthread.php?t=1363165)

---

### Post by windependence on 2010-05-10
> **lavinog said:**
> The ram issue could be ureadahead:
[http://ubuntuforums.org/showthread.php?t=1363165](http://ubuntuforums.org/showthread.php?t=1363165)
FYI, Linux/Unix != Windows

RAM is used if it is available in Linux so you will see high utilization and it's perfectly normal. This makes the system much faster as apps are cached in RAM until needed and swapped out if not needed so Linux will use what you give it. This is a GOOD thing™ :)

-Tim

---

### Post by tgalati4 on 2010-05-11
If you want the new stuff, cloud-based services, and can afford some down time to fix things, then start with ubuntu server (hardy or lucid).

If you want rock-solid stability, use centos or bsd, but make sure you can find all the packages for the services that you want to run.  If you can't find them, then you will have to compile them and that can be painful.

Debian is in-between.  Excellent stability, older packages, but easy to keep up-to-date with the apt system.

Until you have built a few servers it's hard to describe the differences, but they become apparent quickly.

I personally would build a xen server based on ubuntu hardy then run one instance of centos, debian, hardy, lucid, bsd.  Then you can flip between them and have your services running across all of them and just turn off the ones that are too old or don't work properly.

Some secondary considerations:

I have a couple of older dell poweredge servers (1750's).  Through some searching, I found Dell's online management system administrator (OMSA) built for debian.  It was written for Red Hat (and packaged using rpm), but someone went through the pain to convert it to debian and provided debian packages (*.deb) for hardy.  This software allows deep hardware queries (temperatures, memory errors, RAID problems, power supply voltages, etc) over a decent web interface.  The poweredge has 200 MB of BIOS RAM that stores log files that OMSA can format and spit out.  OMSA is helpful, and if it wasn't built for Debian, I would consider Red Hat or Centos so I could run that software.

So your hardware and available system software by the vendor can influence your OS choice.  If you have hardware by vendor XYZ and system utilities are only built for Red Hat and you don't want to go through the pain to convert, then stick with CentOS.

You will have to research your hardware to determine what utilities are available and for what OS.  These utilities are helpful for older machines when things do start to break down.

For remotely-hosted services, ask tech support what they run for the host OS and what they recommend for the guest OS.  If you run something that they are familiar with, you can get things fixed quicker.

---

### Post by lavinog on 2010-05-11
> **windependence said:**
> FYI, Linux/Unix != Windows

RAM is used if it is available in Linux so you will see high utilization and it's perfectly normal. This makes the system much faster as apps are cached in RAM until needed and swapped out if not needed so Linux will use what you give it. This is a GOOD thing™ :)

-Tim

Please take a moment to read the link.
ureadahead tells the kernel to reserve 128Mb for tracing, and doesn't release it when it is done.  The memory is not used for caching or any performance enhancement...it is wasted memory, and a bug.

---

### Post by igorb on 2010-05-11
This decision is harder than I thought. Thanks for all the great tips!

---

### Post by dragos2 on 2010-05-11
> **lavinog said:**
> Please take a moment to read the link.
ureadahead tells the kernel to reserve 128Mb for tracing, and doesn't release it when it is done.  The memory is not used for caching or any performance enhancement...it is wasted memory, and a bug.

I think you both mean swapiness ? That would release a lot of memory for high values like 80, and cache everything for low values like 10 and decent amount of memory.

---

### Post by windependence on 2010-05-11
> **lavinog said:**
> Please take a moment to read the link.
ureadahead tells the kernel to reserve 128Mb for tracing, and doesn't release it when it is done.  The memory is not used for caching or any performance enhancement...it is wasted memory, and a bug.
Did I mention ureadahead at all in my post? I didn't think so. I was talking about the references to Linux consuming too much memory (Linux bloat would be a topic for another thread).

-Tim

---

### Post by lavinog on 2010-05-11
> **windependence said:**
> Did I mention ureadahead at all in my post? I didn't think so. I was talking about the references to Linux consuming too much memory (Linux bloat would be a topic for another thread).

-Tim

You quoted my comment about ureadahead.

---

