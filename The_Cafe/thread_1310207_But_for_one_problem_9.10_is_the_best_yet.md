---
title: "But for one problem 9.10 is the best yet"
date: 2009-11-01
forum: The Cafe
---

### Post by Malkosha on 2009-11-01
Sorry in advance for the long post …..

While I have installed and run many Linux distros and 9.10 so far seems to be the best yet. I usually don't make posts like this. Instead I whine, moan and groan about this or that, ask questions and look for help but this Ubuntu version is so well done I felt compelled to post about it. If you're not running this distro, you are losing out.

Instead if just updating 9.04, I went with a fresh install and everything went Ubuntu smooth and quick. I had no problems at all and and doubt that even a completely new user would have problems either …  unless of course they wanted to do some fancy partitioning. At that point, no OS could have done any better. Everything worked out of the box. I installed my restricted drivers for my Nvidia card and I must say, the prompt that gives me this option which has been in Ubuntu for a while now would be a major help for a new user. Even in Windows, some users still don't understand the need for 3D drivers until their 3D games don't work. The sound system seems different and works so much better for me with my SB Live. Nice job here!

The entire look and feel is very polished and unlike a Windows installation, I had Office, Internet apps as well as my drivers installed automatically when I was done. The fresh install is usable right from the start and there is no OS I've ever used that does this better. Of course, I need Flash and Java well as some other things so  I went to the Ubuntu forums and under “Multimedia and Video” there is a sticky by “Ubuntu-Freak” that makes this tweaking simple and easy. I always come here to do this and have since 8.04. While I understand that you can now almost point and click to do some of these things as needed. its so nice for me to get this out of the way early. To each their own.

I then went and got the things I always play with. Wine so I can install WoW, Emerald and related apps for my desktop look as well as some games for the wife. I was pleased to see that the Wine beta 1.2 was in the repos. This was needed because at this time the Wine beta wasn't updated in the Wine HQ site and the beta is needed to get WoTLK installed. Everything went great and WoW runs excellent under Ubuntu 9.10. The “Ubuntu Software Center” is a nice addition and makes getting and removing software a breeze.

All in all, I'm more than pleased at the job the dev's, as well as the community … whose feedback, fixes and direction are vital to making this a great Distro ... have done There is one potential problem however and one that for some may be show stopping. While IPv6 is the future of the Internet it does cause problems; not only with ISP's who aren't ready for it, but for users whose hardware just won't work with it. IPv6 may be the future, but the future just isn't here yet.

I researched and found out how to disable it system wide which resulted in fantastically better Internet connectivity, but for the average user … this could be a disaster. All they would understand is that the Internet wouldn't work or was very slow. Not a great way to get rid of Ubuntu “Bug #1”  ;) 

I would recommend that the Ubuntu team either rethink compiling Ipv6 into the kernel or provide a way that a regular user can enable/disable this on the fly. For the time being it should come out of the box disabled giving the user an option to enable it and when the future gets here, you can then switch this around.

I want to thank the Ubuntu team as well as the community for the great work here. This, IMO, is the best Ubuntu yet. I don't have the skills to give anything back to the community but I can talk people into giving it a try and even support them when they have problems. Expect some new and happy users.

---

### Post by pwnst*r on 2009-11-01
since you researched it, how about posting the how-to for others?

---

### Post by 3rdalbum on 2009-11-01
Regarding IPv6, it is neccessary to have built-in support to satisfy one of the conditions for US government contracts. Also, it has been forecast that we will run out of IPv4 addresses some time next year... It's urgent that v6 be adopted ASAP.

Many people these days don't have IPv6 problems anyhow, and my understanding is that it cannot be disabled in 9.04 and later, so are you sure your fix wasn't a placebo?

---

### Post by Malkosha on 2009-11-01
> **pwnst*r said:**
> since you researched it, how about posting the how-to for others?

No problem .... Keep in mind this IS NOT my fix. I found this somewhere else and kept it in my notes for future installs. I wish I could credit the person who figured this out.

From the terminal:

cat /proc/net/if_inet6

then:

ip a | grep inet6

If anything shows up in either one, you have IPv6 enabled. 

To get rid of it, from the terminal:

sudo gedit /etc/sysctl.conf

Add in these lines:

#Disable IPv6
net.ipv6.conf.all.disable_ipv6=1

Save and reboot. Run:

cat /proc/net/if_inet6

then:

ip a | grep inet6

You should get nothing. This not only sped up certain Internet apps, it stopped my router from locking up.

Luck!!

---

### Post by Malkosha on 2009-11-01
> **3rdalbum said:**
> Regarding IPv6, it is neccessary to have built-in support to satisfy one of the conditions for US government contracts. Also, it has been forecast that we will run out of IPv4 addresses some time next year... It's urgent that v6 be adopted ASAP.

Many people these days don't have IPv6 problems anyhow, and my understanding is that it cannot be disabled in 9.04 and later, so are you sure your fix wasn't a placebo?


I'm sure. I tested it out on multiple PC's and had problems like my router locking up as well as very poor Internet performance across various applications. Some home routers simply can't handle IPv6. This has been documented from both Windows, MAC and Linus sources. Win7 as well as Vista has a way of disabling this. 

I tried the fix I found, turning it both off and on, and the performance hit was solid. If your ISP is IPv6 ready AND you have the router hardware that can handle it, this is a non-issue.

While many ISP's are catching up, the main problems are the routers that people get from their ISP's. To me its like putting wings on your car in anticipation that someday cars will fly. It may be "the future" but for now your going to crash and get a ticket.

If Ubuntu MUST put this in, then make its use optional until the day comes when it has to be done. When that day comes Ubuntu will be ready and until then people who don't know why they are having slow Internet problems as well as router crashes can load Ubuntu and have it just work.

---

