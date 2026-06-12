---
title: "AVG Anti-virus Free For Linux Now Available For Download"
date: 2006-01-10
forum: The Cafe
---

### Post by lotusleaf on 2006-01-10
**AVG Anti-virus Free For Linux Now Available For Download**

In Oct '05 I posted [here](http://www.ubuntuforums.org/showthread.php?t=75260) about Grisoft's AVG Anti-Virus coming to Linux with a free version.

As of [Grisoft's official announcement](http://free.grisoft.com/doc/4040/lng/us/tpl/v5) dated Jan 9, '06 it is now available for download/use for free.

On the AVG for Linux [download page](http://free.grisoft.com/doc/20/lng/us/tpl/v5) as of right now you'll find the [User Manual](http://free.grisoft.com/softw/70free/doc/avg_afl_uma_en_71_2.pdf) (.PDF), and three RPM files for download: for [Mandriva](http://free.grisoft.com/softw/70free/setup/avglinux-7.1-22_free_mdk_avi0649.i386.rpm) (Mandrake), [Red Hat](http://free.grisoft.com/softw/70free/setup/avglinux-7.1-22_free_rh_avi0649.i386.rpm), and [SUSE ](http://free.grisoft.com/softw/70free/setup/avglinux-7.1-22_free_suse_avi0649.i386.rpm) at version 7.1.0022.

I haven't had the time to try it yet, but I'm sure some will and perhaps they could report back their experiences with it here. [Alien](http://packages.ubuntu.com/breezy/admin/alien), anyone? :P Time to send a kind e-mail to Grisoft requesting they make a DEB available for download for Ubuntu. :)

I'll spare my thoughts on potential security issues which could arise from using a closed source anti-virus on Linux, but I'm sure someone will chime in for me. 

Comments?

*Notes:* > AVG Free for Linux is NOT authorized or intended for:

    * Business or commercial use (including testing and evaluation)
    * Non-profit Organizations

[License agreement for AVG Free](http://free.grisoft.com/softw/70free/doc/license_us.txt)

*Related articles: *[digg mention & user comments](http://digg.com/linux_unix/AVG_releases_free_anti-virus_for_Linux)

[color=red](01-29-2006) Edit:[/color] There's also a .tar.gz download available [here](http://www.grisoft.com/doc/71/lng/us/tpl/tpl01) under "AVG 7.1 for Linux Workstation".
Direct download for version 7.1-23: [avglinux-7.1-23_avi0672.i386.tar.gz](http://www.grisoft.cz/softw/70/filedir/inst/lnx_lws_stf__7_1-23.dir/avglinux-7.1-23_avi0672.i386.tar.gz)

---

### Post by DigitalDuality on 2006-01-10
I use an Ubuntu box (was Fedora) as my personal computer at work (which has about 70 Wintel boxes, a 2003 exchange/file/web server and a Debian Censornet box) and was curious as to whether i should install AVG or at the very least.. Clam, to protect the network users from windows viruses that i may download or transmit.

I like that AVG has offered the product but i'd really like to see Clam (for Windows, Mac and Linux) really advance itself more and more.  Or at least a full AV suite go open source.

There was news that Clam might actually get some commercial support [http://news.zdnet.com/2100-1009_22-5992194.html](http://news.zdnet.com/2100-1009_22-5992194.html) and that made me happy, but that's yet to be seen.

---

### Post by briancurtin on 2006-01-10
>> AVG Free for Linux is NOT authorized or intended for:
>>  * Non-profit Organizations

i know, RTFA, but can someone let me know why a group doing work not for profit should not use this free software? why are they "NOT authorized" to use this, and why should they be disallowed from using this in any way?

---

### Post by DigitalDuality on 2006-01-10
^
I agree fully, but in the windows world that is definately a trend of non-open freeware.  Ad-aware, spybot, AVG, avast, (the list goes on) all have free versions that are only intended for personal use.  The goal is to impress home users, maybe someone will mention it to a tech guy at work, maybe a tech person themselves d/l's it at home and is impressed and will then pay for the "professional" version at his work place per computer.

Companies don't mind giving stuff away for personal use alot of the times, it acts as a great marketing tool.  And i think alot of people underestimate how many computers are in the non-profits and business world. That's where the money is.

As for non-profits. Non-profits are alot of the time, merely a way for people to get rich.  Take a look at the salary for the leader of the girl scouts for instance.. or the Red Cross.

---

### Post by drizek on 2006-01-10
[QUOTE=briancurtin]>> AVG Free for Linux is NOT authorized or intended for:
>>  * Non-profit Organizations

i know, RTFA, but can someone let me know why a group doing work not for profit should not use this free software? why are they "NOT authorized" to use this, and why should they be disallowed from using this in any way?[/QUOTE]

probably just a legal thing...

the best i can come up with is that it might possibly have something to do with them getting some sort of tax credits for giving their software to non-profits for free.

---

### Post by BLTicklemonster on 2006-01-14
A nice "how to install it for breezy for morons" would be nice. I have all three downloads, and I'm sitting here staring at them wondering what to do with them. I used alien on one of them, but nothing happened that I can tell. I didn't get any errors.

```
bill@ubuntu:~$ sudo alien avglinux-7.1-22_free_rh_avi0649.i386.rpm
avglinux_7.1-23_i386.deb generated
bill@ubuntu:~$ sudo dpkg -i avglinux_7.1-23_i386.deb
(Reading database ... 141384 files and directories currently installed.)
Preparing to replace avglinux 7.1-23 (using avglinux_7.1-23_i386.deb) ...
Unpacking replacement avglinux ...
Setting up avglinux (7.1-23) ...
bill@ubuntu:~$ 
```

Now what?


*Edit:

That figures... Okay, so there it is in applications under accessories. I click on it, and I get an error with no specificity. I click okay, and the error message goes away, and avg is ready to run. But it won't run. And I don't have permission to upgrade it. 

weeeeee!!!

---

### Post by curuxz on 2006-01-14
I take it this thing is designed to scan for windowz viruses on your other partition? 

They cant serioulsy expect us linux users to need avg for native drives

---

### Post by BLTicklemonster on 2006-01-14
My personal view on all things viral is, "you just never know what's going to happen next", so I'd prefer to be on the scoffed safe side. 

BUT, be that as it may, I don't really do anything in ubuntu that I am concerned with losing, so I give up. I can't even get clamav to cooperate. I just tried updating it and it uninstalled itself and won't install from synaptic. 


Support site for it is written for people who know what they are doing, which, imho is what keeps average people (Im not abnormal, but try to be average) from using linux. Which is probably the whole idea, but whatever.

---

### Post by curuxz on 2006-01-14
Personaly I want to keep the anti-virus compaines as far away from linux as possible. If we give them a market then they will have to make viruses to justify it. If linux users dont adopt their clients then they will have no reason to make more. 

If we let them in then we will get viruses.

---

### Post by awakatanka on 2006-01-14
[QUOTE=curuxz]Personaly I want to keep the anti-virus compaines as far away from linux as possible. If we give them a market then they will have to make viruses to justify it. If linux users dont adopt their clients then they will have no reason to make more. 

If we let them in then we will get viruses.[/QUOTE]
Thats just crap you spreading. There are linux virus already and there is already software for it.

---

### Post by tageiru on 2006-01-14
[QUOTE=awakatanka]Thats just crap you spreading. There are linux virus already and there is already software for it.[/QUOTE]
Yeah, about 10 that are ment as jokes.

Anti-virus software is a plague that should be avoided at all cost. It is a sign of operating systems with lacking security models.

Please avoid this non-free crap. It would be a shame if Linux ended up as a poor copy of Windows with every inch of it turned into a market for shady companies.

---

### Post by curuxz on 2006-01-14
there have been less than a hand full of isolated viruses, most were worms aimed at specific servers.

---

### Post by prizrak on 2006-01-14
[QUOTE=curuxz]there have been less than a hand full of isolated viruses, most were worms aimed at specific servers.[/QUOTE]
Apache Slammer was hardly an isolated virust that worked just fine under Linux. "If there is a hole there is a way". There are many vulnerabilities in Linux itself as well as software (such as Apache, BIND, Sendmail, etc...) and if there is a vulnerability there will be malware that uses it no doubt about it. Sure in Linux it can only do as much damage as the user account that gets infected but if you lose all your data it won't be much comfort that the rest of the OS is still working. 
Make no mistake *nix is a better designed and configured system than Windows and is more resilient against malware, but it doesn't make it bulletproof a good security policy is always in order.

---

### Post by curuxz on 2006-01-14
Prizrak I could not agree more, you need good people behind the screen else its just a hunk of metal asking to be hacked. My only point is I dont want to see windows'esc features comming into the linux world like antivirus programs, because its like giving cows the foot and mouth jab, sure they wont get the illness but by making them imune you admit there is a problem.

Linux does not have a virus problem and as long as good sense prevails we wont get one, let the antivirus people rip off the windows world and stay away from nix :)

---

### Post by DigitalDuality on 2006-01-14
^
I'll agree with that as long as Linux remains a minority used OS.  The second 'nix grabs even 15-20% of market share though... is the second i will definately say otherwise.

AV apps though are great for 'nix in multi OS environments though.  I have 3 Linux boxes at my work, which is a 80 computer windows network.  EVERY  computer has an antivirus on it.

---

### Post by BWF89 on 2006-01-14
I use the free version of AGV on my Windows XP box along with ClamWin and I've found that eventhuogh ClamWin takes longer to scan my computer they both do about the same job.

---

### Post by visctrix on 2006-01-19
[QUOTE=DigitalDuality]^
As for non-profits. Non-profits are alot of the time, merely a way for people to get rich.  Take a look at the salary for the leader of the girl scouts for instance.. or the Red Cross.[/QUOTE]

Of course there are hundreds of thousands of charities and non-profits out there, ranging from the ethical equivalent of M$ to your bedroom open source activist.  Actually I think many of these organisations are just too principled for their own good.  I'm currently working for nothing to set up a small charity that advises other charities and I couldn't bring myself to install the free AVG at work.

I think there are many people in the open source community who would take a similarly principled view (although it would obviously cost them less!).  So please less of the slanderous generalisations.

Visctrix

---

### Post by Maggot on 2006-01-19
[QUOTE=BLTicklemonster]A nice "how to install it for breezy for morons" would be nice. I have all three downloads, and I'm sitting here staring at them wondering what to do with them. I used alien on one of them, but nothing happened that I can tell. I didn't get any errors.

```
bill@ubuntu:~$ sudo alien avglinux-7.1-22_free_rh_avi0649.i386.rpm
avglinux_7.1-23_i386.deb generated
bill@ubuntu:~$ sudo dpkg -i avglinux_7.1-23_i386.deb
(Reading database ... 141384 files and directories currently installed.)
Preparing to replace avglinux 7.1-23 (using avglinux_7.1-23_i386.deb) ...
Unpacking replacement avglinux ...
Setting up avglinux (7.1-23) ...
bill@ubuntu:~$ 
```

Now what?


*Edit:

That figures... Okay, so there it is in applications under accessories. I click on it, and I get an error with no specificity. I click okay, and the error message goes away, and avg is ready to run. But it won't run. And I don't have permission to upgrade it. 

weeeeee!!![/QUOTE]

Gotta install these 2 pkg's:

wget [http://ftp.at.debian.org/debian/pool/main/g/gcc/libstdc++2.10_2.95.2-14_i386.deb](http://ftp.at.debian.org/debian/pool/main/g/gcc/libstdc++2.10_2.95.2-14_i386.deb)

wget  [http://ftp.at.debian.org/debian/pool/main/g/gcc-2.95/libstdc++2.10-glibc2.2_2.95.4-11woody1_i386.deb](http://ftp.at.debian.org/debian/pool/main/g/gcc-2.95/libstdc++2.10-glibc2.2_2.95.4-11woody1_i386.deb)

then

dpkg -i libstdc*

Wa-La :)

edit:  Well now. You have to have a license. The one provided in the README is 70LINUX-TTS05-PZ-C01-S1-J18-IHAR BUT expires in 30 days. I hardly see how that's FREE :rolleyes: 

Windows version isn't like that.

---

### Post by Vlammetje on 2006-01-20
depends on how you get one. If you get it by identifying yourself as a user and in exchange for nothing more than some personal info, I'd say that is on par with other (cost)free closed source sw I know of.

I don't really see anything wrong with running AV on a linux box tbh. It's good and great and all that that there aren't many linux viruses around that have impacted many end users... it's even better that the linux market as a whole is so fragmented that perhaps not one single virus could infect all of them and all that.

Still a PC is only as smart as the user behind it.

I'm all for being cautious and I will give it a try... just as I did with F-prot. Better to be prepared for that day when so many people have followed the call of Ubuntu that writing a virus for ubunutu apps may be worthwile.

---

### Post by lotusleaf on 2006-01-29
There's also a .tar.gz download available [here](http://www.grisoft.com/doc/71/lng/us/tpl/tpl01) under "AVG 7.1 for Linux Workstation".
Direct download for version 7.1-23: [avglinux-7.1-23_avi0672.i386.tar.gz](http://www.grisoft.cz/softw/70/filedir/inst/lnx_lws_stf__7_1-23.dir/avglinux-7.1-23_avi0672.i386.tar.gz)

I updated my first post in this thread with this information.

Has anyone installed this yet, tested it and compared the results to other anti-virus programs for Linux?

---

