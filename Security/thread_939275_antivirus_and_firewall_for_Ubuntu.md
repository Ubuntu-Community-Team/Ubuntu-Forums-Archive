---
title: "antivirus and firewall for Ubuntu"
date: 2008-10-05
forum: Security
---

### Post by formol on 2008-10-05
Hello everyone, 

In the Add/Remove menu in Ubuntu, there is available firewall and antivirus.
Are they really useful in Ubuntu?  

thank you.

---

### Post by Drezard on 2008-10-05
The AV in the linux Add/Remove only detects windows viruses on your linux system unfournately. So thats pretty useless. A firewall is only useful if you are running any servers.

Daniel

---

### Post by DrMega on 2008-10-05
> **Drezard said:**
> The AV in the linux Add/Remove only detects windows viruses on your linux system unfournately. So thats pretty useless.

That's all it needs to do. Linux isn't Windows, it doesn't leave the front door wide open and post signs all over town telling people that your not in like Windows does.

---

### Post by hyper_ch on 2008-10-06
(1) you generally don't need antivirus

(2) you generally don't need to alter the firewall that's installed

---

### Post by remy06 on 2008-10-06
Hi,

I've read that ubuntu has iptables installed.Im a new user here so am wondering if do we need to enable the firewall or just leave it as it is (assuming it is preconfigured and running already by default)?

I've read on ufw that comes with ubuntu also and that we have to enable it
via "ufw enable".Does it mean that the firewall is not activated by default?

I actually thought that iptables is already configured and active by default,and that ufw only provides an easier way to configure the firewall rules and thus we have to enable it to use.

Please advice and correct me if im wrong.Thanks!

---

### Post by hyper_ch on 2008-10-06
> **remy06 said:**
> if do we need to enable the firewall or just leave it as it is (assuming it is preconfigured and running already by default)?
iptables runs by default - however it does not filter anything but lets everything pass - and that's good. There's not really a reason why you should run a firewall as long as you don't install servers...[/QUOTE]

---

### Post by jerome1232 on 2008-10-06
iptables is always enabled, and configured to allow all traffic by default.

UFW is just a frontend to iptables, if you enable ufw it just configures iptables with any rules you have configured using ufw, when you disable ufw it removes all of it's rules from iptables.

Fortunately by default Ubuntu has no services listening for connections so it drops all incoming traffic any ways. (Where as on Windows a default install does have programs listening for connections, they can't be configured to not listen for connections making a firewall essential)

Firewalls are usually used on servers to restrict connections to certain hosts, or begin dropping connections if multiple repeated attempts are made to connect to a service that is running on the computer.

---

### Post by Crayboff on 2008-10-06
I recently downloaded Firestarter and for some reason, since then, my internet access seems to have slowed down a little and become a little tempermental. Such that internet access from a usually reliable source just sort of doesn't work for my computer. I wait a little and try again and it then seems like my computer only connects grudgingly.

Is Firestarter good/ should I have a 3rd party firewall? I have ubuntu 8.04 and I dunno if that has a built in one that is good enough.

---

### Post by hyper_ch on 2008-10-06
firestarter is no firewall...

---

### Post by Forbees on 2008-10-06
AVG for Linux

go get it if your worried

---

### Post by formol on 2008-10-06
remy06 resume my interrogation about the necessity of a firewall, if iptable close everything by default, did a firewall is very useful?
or maybe intrusion are possible in the port 21 or 80? which are normallement open for email and internet?

---

### Post by hyper_ch on 2008-10-06
formol:

by default, iptables does nothing and lets all traffic pass
iptables is the backend for firestarter, ufw, .... those programs do nothing but modify iptables.
by default, no services are running hence all ports are closed...

only when you start installing services you might want to consider altering the default iptables rules. Even then in most cases it's not needed.

---

### Post by haydnc on 2008-10-06
You can get a number of antivirus applications free that work quite well under Linux though not many of them seem to do full-time on access scanning like they do under Windows.

Bearing that limitation in mind I quite like using Avast antivirus ([www.avast.com](www.avast.com)) though if anyone out there knows a better one that on-access scanning does work on, I'm listening.

---

### Post by formol on 2008-10-06
hyper_ch:

if I understood you correctly, if I do nothing special with my computer, I don't have to worry about firewall?

---

### Post by hyper_ch on 2008-10-07
formol:

that's correct. If no services are running, nothing from the outside can connect to you. And if you are running services, let's say a webserver, you normally want everybody to connect.

However if you run a ssh server, you may want to limit people that can connect to to a certain ip/country or you may not want that people from certain countries can connect...

On windows, in most software that you install, you also have home phoning stuff (usage feedback) and such stuff. There, you want to have a firewall that blocks also outgoing stuff rigirously. That's not the case here on linux.

---

### Post by cariboo on 2008-10-07
I keep seeing people recommend anti virus programs. Because there are no Linux viruses in the wild, all these antivirus programs only scan fo windows viruses, and becuase windows viruses have no affect on Linux, they are totally useless. They are just a waste of cpu cycles and bsndwidth. If you feel you need to play big brother  to your friends and family and protect them from what they  should be doing themselves more power to you.

Jim

---

### Post by hyper_ch on 2008-10-07
what is the chance that it's YOU who forwards virus to third party people? What is the chance those third party people will get the same virus from another source? I think the chance is pretty small that it's you who forwards it.

However if you run a mail- or fileserver you might want to use av... but generally I think people that don't protect themselves will get infected anyway regardless whether I av-check the stuff I send to them.

---

### Post by lisati on 2008-10-07
> **Forbees said:**
> AVG for Linux

go get it if your worried

And if you do decide to "go for it" there's an "AVG tips" thread ad [http://ubuntuforums.org/showthread.php?t=889552](http://ubuntuforums.org/showthread.php?t=889552) (with a short discussion on the merits or otherwise of anti-virus with Linux)

Whatever tools you decide to use, it's up to you to decide for yourself.

---

### Post by catatonicprime on 2008-10-07
> **cariboo907 said:**
> I keep seeing people recommend anti virus programs. Because there are no Linux viruses in the wild, all these antivirus programs only scan fo windows viruses, and becuase windows viruses have no affect on Linux, they are totally useless. They are just a waste of cpu cycles and bsndwidth. If you feel you need to play big brother  to your friends and family and protect them from what they  should be doing themselves more power to you.

Jim

According to [VX Heavens Virus Stats]("http://vx.netlux.org/vl.php?dir=stat") at the time of writing, there are 86 "viruses" designed for linux in their collection. The specifics of which can be left to those who want to meander through how a virus writer circumvents file permissions etc.

However, I wanted to know if these virus scanners we use scan for -only windows viruses-? So I downloaded one under the linux category and scanned it using ClamAV, it was detected which leads me to believe that ClamAV (and surely others) do scan for linux based viruses. Interesting note: In their categorizations they have in their collection 1,617 Win32 viruses, and 16,644 DOS viruses. Making the 86 linux viruses a mere drop in the hat.

These 86 are not in the wild (or are they? Anyone?)

---

### Post by remy06 on 2008-10-07
> **hyper_ch said:**
> formol:

by default, iptables does nothing and lets all traffic pass
iptables is the backend for firestarter, ufw, .... those programs do nothing but modify iptables.
by default, no services are running hence all ports are closed...

only when you start installing services you might want to consider altering the default iptables rules. Even then in most cases it's not needed.

ic..thanks guys
clarified my doubt on this

---

### Post by cariboo on 2008-10-07
@catatonicprime

You said you ran clamav and it found a Linux virus? Or did it find a windows virus in your download directory?

As an aside, I found and article that explains how hard it is for a linux virus to do anything to a system:

[http://www.downloadsquad.com/2008/02/14/flipping-the-linux-switch-the-anti-virus-question/](http://www.downloadsquad.com/2008/02/14/flipping-the-linux-switch-the-anti-virus-question/)

Jim

---

### Post by catatonicprime on 2008-10-07
@cariboo907

Yep, I scanned the file I downloaded (after unzipping) in my tmp download directory. I'm sorry I'm not at home and can't provide the output at this moment. Alternatively... heres this: [ClamAV Database Search for Linux.Alaeda.A]("http://clamav-du.securesites.net/cgi-bin/clamgrok?virus=Linux.Alaeda.A&search-type=exact&case-sensitivity=Yes&database=main&display=database&display=file&display=virus&display=signature&.submit=Submit+Query&.cgifields=database&.cgifields=search-type&.cgifields=case-sensitivity&.cgifields=display")

As I said, the 86 I do not believe are in the wild - but some people on the internet are not so kind and could package it with... well something else. Or in other words another technique could be employed to allow infections to occur (tar/untar maintain file perms suid maybe?)

I would like to mention a little history lesson: The 1988-Morris Worm ran on and infected Unix machines running SendMail. This was not a virus(file infector) and is fundamentally different in operation. The take home lesson though is, poor configuration and the virus technology still opens the door for infection. But yeah, still not in the wild. :)

---

### Post by Crayboff on 2008-10-07
Ok, I seem to be getting mixed signals. Should I get an antivirus software and/or a firewall for my Hardy Heron? I use this computer as a personal computer and I do not run a server of any kind. 

I'd like this answered once and for all, and if you can, please suggest some I should look into. I have read the forementioned article ([http://www.downloadsquad.com/2008/02/14/flipping-the-linux-switch-the-anti-virus-question/](http://www.downloadsquad.com/2008/02/14/flipping-the-linux-switch-the-anti-virus-question/)), but still do not know whether or not I should. I have used windows all of my life and only recently switched (like 3 weeks ago or something).

---

### Post by jerome1232 on 2008-10-07
> **Crayboff said:**
> Ok, I seem to be getting mixed signals. Should I get an antivirus software and/or a firewall for my Hardy Heron? I use this computer as a personal computer and I do not run a server of any kind. 

I'd like this answered once and for all, and if you can, please suggest some I should look into. I have read the forementioned article ([http://www.downloadsquad.com/2008/02/14/flipping-the-linux-switch-the-anti-virus-question/](http://www.downloadsquad.com/2008/02/14/flipping-the-linux-switch-the-anti-virus-question/)), but still do not know whether or not I should. I have used windows all of my life and only recently switched (like 3 weeks ago or something).

This is sometimes an opinionated topic so you will get mixed answers from both camps. Viruses created for Linux tend to die out very quickly because it is very difficult for them to spread (they have to infect the root users account to gain system wide access) Also Linux get's it's critical security issues fixed and patched much faster than Windows does.

It boils down to this, if you install software from the repo's and don't go around running un-trusted scripts as root (say you find this 'really cool' script on somedude12's blog) you will not get a virus, you will not get maleware. 

In the server world Linux is used more than Windows and has shown time and time again to be much more resistant to attacks/worms/viruses. 

Website's that have the highest uptimes are constantly BSD and Linux (linux reset's it uptime every 486 days so BSD has an advantage there)

---

### Post by catatonicprime on 2008-10-08
> **Crayboff said:**
> Ok, I seem to be getting mixed signals. Should I get an antivirus software and/or a firewall for my Hardy Heron? I use this computer as a personal computer and I do not run a server of any kind. 

I'd like this answered once and for all, and if you can, please suggest some I should look into. I have read the forementioned article ([http://www.downloadsquad.com/2008/02/14/flipping-the-linux-switch-the-anti-virus-question/](http://www.downloadsquad.com/2008/02/14/flipping-the-linux-switch-the-anti-virus-question/)), but still do not know whether or not I should. I have used windows all of my life and only recently switched (like 3 weeks ago or something).

I didn't mean to confuse you. If your not running servers, you will probably be fine without an anti-virus. If you were running servers, it'd more or less be a courtesy to users using a windows machine (but still not necessary).

---

### Post by hyper_ch on 2008-10-08
> **Crayboff said:**
> Should I get an antivirus software and/or a firewall for my Hardy Heron?

(1) You have already a firewall installed - however the firewall currently has no rules in it so it lets everything pass.

This is generally good because
(a) there are no services running to which an external user can connect to - so all ports are "closed"
(b) a firewall on windows also prevents you that installed software phones home and submits data on the installation and usage - in linux you normally install all the software from repositories or compile it from source and they don't have (generally) such spyware integrated. This means you don't need to check all outgoing connections
(c) however if you run servers (apache webserver, ssh server, ftp server) you may want to restric connection access. E.g. let only certain ips connect ot the ssh server.. in that case a modification of iptables is what you need

(2) regarding viruses, there are none in the wild. If you download stuff only from the repos or trusted sources (e.g. sourceforge) you won't catch anything. Most, if not all, antivirus programs have as main task to filter out windows malware in order to protect windwos users. So if you run a fileserver or mailserver you may want to consider to run antivirus. However all windows users must protect themselves also, otherwise they will get infected over time. Your effort prevents not much on that front...

---

