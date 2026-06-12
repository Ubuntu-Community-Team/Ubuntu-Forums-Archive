---
title: "Choosing a distro for a Small Business Server"
date: 2006-04-08
forum: Server Platforms
---

### Post by NewbieUser on 2006-04-08
I am in the process of building a linux-based server to replace a present MS 2003-based system.  I have worked with a number of different distros and would like some input on the process of choosing a base distribution for the server.  I have worked with fedora, SuSE, CentOS and ubuntu/debian.  I feel that fedora is a too bleeding-edge for a server and have focused on the other three.  Are basically desktop distros such as Ubuntu and SuSE really viable as servers and what factors would affect your choice.  SuSE also has Yast which, after I learned to let it do the writting for the configuration files, does make some set-up steps easier.  

Many thanks for the input.

---

### Post by joshuapurcell on 2006-04-08
At this point, I would almost just go with what you are most comfortable with, but I'm assuming that you will be the one also providing the support. What will you be using this server for? DNS, DHCP, Storage, other? What type of hardware will you be using, and have you been able to install any distro on this hardware before? Are there any particular packages that you require in your setup?

I should add that my personal choice would without a doubt be Ubuntu (but you are asking this question on the Ubuntu forum :D). You've started out in the right place, so it looks like you are leaning in the right direction.

---

### Post by NewbieUser on 2006-04-08
Joshua:

Thank you for the input.  The server will be a spare Dell Poweredge that we have and will be used initially as a mail serve with file, print, DNS and DHCP being added later (or eventually transfered to a second Dell server that will be setup on Linux as well).  I have installed all of the Distros on the server and built a mail system using Postfix, Dovecot, Squirellamail and Amavis or Mail Scanner on each of the systems.  The most problematic was the install of Amavis on CentOS as I descended into RPM dependency problems for a while.  

I wondered if CentOS being based on RHEL provides any greater stability or long-term security support than desktop distros.  Also SuSEs Yas does make set-up easy and wondered if Ubuntu has any similar server tools?

I have used Ubuntu as a desktop distro as well as Fedora and, presently, SuSE.

Many thanks for the input.

---

### Post by petterah on 2006-04-08
Hi, im currently in the same situation myself... installing linux on my companys dell poweredge, running file sharing, internal web server, with php system info, and some intranet sites. I have used linux for some time, but not quite found the one (distro) i liked. I used redhat for some time (6.0-9) but discovered the unstable nature of fedora and jumped over to debian. I have also tried centos, but debian is the one i have used the most besides redhat, and some quick sessions with slack, gentoo and now ubuntu. 

My impressions is, ubuntu is a very nice distro. I have just installed it (breezy) on my home fileserver, running samba and cups. The install was very smooth, and all of my old hardware was detected, and the system is running stable and smooth. All my previous debian knowlegde is nice to have.. the basic commands for the shell is debian. My desktop is running dapper, and i have to say... its cool stuff.. running Xgl, compiz and all is smooth. 

All this have convinced me to install ubuntu 5.10 (stable) on my companys dell server. After all, its debian, with newer packages, and a nice community, and forum ;)

-Petter-

---

### Post by najames on 2006-04-09
I have been beating on a Tyan S2882-D dual Opteron server for a couple days.  It has a 40GB IDE drive (master) NEC DVDRW (slave), four Samsung 250GB SataII connected to the onboard controller.

Fedora Core 5 final worked, made the 4-drive "soft RAID5" array easily, BUT it seemed to be running slow at times.  I found when I resized windows (including the system monitor) one of the two 246 Opterons would peg at 100% with the Xorg process.  It was REALLY flaky.

I tried Ubuntu AMD64 both Breezy and Dapper, neither wanted to build the array correctly, the seemed to only want to do 500GB max.  I'd use Ubuntu in a minute if it would build the arrays.  After trying this my disks seemed borked, I downloaded the Samsung drive tools and wiped the master boot record and I was back in business. I really like the usability and maintainability of it with Synaptic.  ALL my regular AMD64 PCs will likely have Ubuntu.  We just need a 64bit Automatix.

I tried CentOS 4.3 and it also easily created the RAID5 arrays, used a SMP kernel, seems very stable.  I added YumEx. It's "somewhat" like Synaptic, a little slow.  Samba is not working yet, nor as easy to set up as Ubuntu.  This is being typed from CentOS.

I have some Suse 10 PCs too.  I like Suse 10 in every way but one, I** HATED** the Yast update system, tried Synaptic, worked ok for a while but then I started getting app errors.  Oops, not good.

Lastly, I also have Win2003 Server 64.  I tried it for a while today and it just reminded me of all the things I hated about WinXP.  Nagware.

Jim

---

### Post by LordHunter317 on 2006-04-09
[QUOTE=NewbieUser] I feel that fedora is a too bleeding-edge for a server and have focused on the other three. [/quote]Fedora isn't a server-oriented distro, receives little focused server package testing, and is senseless to run on a server when you can get RHEL rebuilds for free.

>  Are basically desktop distros such as Ubuntu and SuSE really viable as servers and what factors would affect your choice.Seeing as both have server builds, I don't know what you're talking about.

They all run the same software for everything you've noted it'll run, so run whatever you're most comfortable with, unless you need paid support.  Then SUEL or RHEL are your only options.

---

### Post by puddpunk on 2006-04-10
[QUOTE=LordHunter317]unless you need paid support.  Then SUEL or RHEL are your only options.[/QUOTE]

Don't spread such FUD - did you even read the firefox starting page?

[http://www.ubuntu.com/support/supportoptions/paidsupport](http://www.ubuntu.com/support/supportoptions/paidsupport)

---

### Post by alamba on 2006-04-10
Depending on how much time you would like to put into implementing and maintaining a particular solution is one measure that I like to keep in mind while deciding on a server distro. I currently have mail servers, infrastructure servers (DNS, DHCP, etc.) and even security servers (nessus, nmap, nagios, etc.) running on ubuntu and have so far not faced any issues that would lead me to believe that ubuntu is any lesser a server distro as compared to any other.

A

---

### Post by LordHunter317 on 2006-04-10
[QUOTE=puddpunk]Don't spread such FUD - did you even read the firefox starting page?

[http://www.ubuntu.com/support/supportoptions/paidsupport](http://www.ubuntu.com/support/supportoptions/paidsupport)[/QUOTE]Yes, I did, and I think you need to read that page.  As it stands, the offered support is useless for a server, today.

Even under Dapper, it will be still be somewhat questionable.  Main will be greately improved in what it carries for server packages (comparable to RHEL for some types of serving.  The real question is, and not answered on that page, is how willing is Canonical to handle your custom configurations, external packages, source-builds, etc.

---

### Post by najames on 2006-04-12
I'd like to update my previous statements with additional testing experience.  

I have built another system consisting of an AMD64, a 40GB IDE system drive, and 4 160GB drives for the RAID.   I tried installing Ubuntu Dapper 32bit Server.  I found that I had created the RAID partitions on each drive but not properly linked them together afterwards.  This time they showed up in the correct configuation/size.  

When it rebooted after installation it is having some sort of Mac error.  Both Suse10 and Ubuntu have been installed on this system on the past so I know it should work.  

Ubuntu's disk partioner works slightly different than setting up with CentOS/RedhatEL Disk Druid.  In Ubuntu I assigned full drives to be logical/RAID devices, then went back afterwards and set the RAID to be mounted on /home.  I estimate the soft RAID performace of transferring data across the Gigabit LAN was about the same as with a single drive as expected.  I have not benchmarked any soft raid5 yet.

I intend to use this box for developing VMware machines on.

Edit: 

I found that the BIOS had reordered the drives.  The RAID was listed first, the actual IDE system drive last.  Once I reordered them, I was back in business. 

It did install correctly.  I thought it was hung on a blue screen for a LONG time.  The first time I got impatient and rebooted and started over, the second time I was pissed and ignored it.  After an hour or so and it eventually came back and continued installing, must have taken that long to build the array.

No desktop, poop.  Time to dredge around and see if I can apt-get it or reinstall.

4x160GB Hitachis = 453GB, with 430GB available on software RAID5 using Ext3.

---

