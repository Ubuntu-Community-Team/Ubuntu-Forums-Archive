---
title: "is it difficult to harden ubuntu?"
date: 2012-12-13
forum: Security
---

### Post by nomenkultur on 2012-12-13
Hi,

I have been thinking about switching to ubuntu since I really like the 13.04 version... but I do have some questions pertaining to security.

 I was told to run fedora since it passed u.s. gov tests with +6 or whatever they call it, it seems the selinux and firewall they have is pretty good.

 My question is:

 is it difficult to setup apparmor so it will sorta sandbox firefox?? There's a thread here with profiles for ubuntu 10 firefox, can I use those profiles or do I need specific ones for each version of ubuntu?

 
 is it hard to configure the firewall as to only permit outgoing port 80 and 443 and close everything else?

---

### Post by CharlesA on 2012-12-13
Fedora has Selinux, Ubuntu has AppArmor.

iptables is included with both distros and if you know how to use iptables, it is pretty easy to get a basic set of rules established.

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

### Post by haqking on 2012-12-13
> **CharlesA said:**
> Fedora has Selinux, Ubuntu has AppArmor.

iptables is included with both distros and if you know how to use iptables, it is pretty easy to get a basic set of rules established.

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

+1

and to the OP as far as i know fedora hasnt had a EAL done, and if it did it is not likely to be higher than Red Hat Enterprise which is at EAL 4+.  fedora is a community project, typically only corporations or corporate products apply to common criteria for evaluation

Most end user OS will not exceed EAL 4 as the usability will be compromised

[http://www.commoncriteriaportal.org/products/](http://www.commoncriteriaportal.org/products/)

Security is a process, all systems can be hardened but will never be 100% secure.

Start off with the wiki [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity) and the links from it

Peace

---

### Post by nomenkultur on 2012-12-13
thanks for the links I will read them and try to setup iptables with incoming blocked and outgoing blocked and only out ports 80 and 443 open and then I will setup apparmor for firefox.

 of course since I'm new to linux this may prove more challenging than I think but I will try to find a apparmor profile for firefox already made

---

### Post by Hungry Man on 2012-12-13
Ubuntu comes with an AppArmor profile for Firefox, though I would suggest you learn some basic semantics of a profile (it's really simple).

---

### Post by Ms. Daisy on 2012-12-13
> **nomenkultur said:**
>  I.. will.. try to setup iptables with incoming blocked and outgoing blocked and only out ports 80 and 443 open ... You'll need a few more ports open at least. Here's a tutorial for UFW/GUFW/iptables.

[http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124)

(Dangertux's server must have fallen over so the pictures aren't there, but it's still a good guide.)

---

### Post by Hungry Man on 2012-12-13
Unfortunately Dangertux's blog has been down for a while now. We should probably replace the pictures.

Besides 80 and 443 you'll want 53/UDP out as well for DNS. After that it's going to be program/ protocol specific. 5222 for xmpp etc.

Ms. Daisy will disagree, I believe, but I think an outbound Firewall is virtually useless for users. I would not suggest you spend the time configuring outbound rules. Configure some inbound ones and you're all good to go.

Ubuntu, like any Linux distro, can be configured in a lot of ways. the basic security wiki should meet average user needs for security.

---

### Post by DuckHook on 2012-12-13
> **Hungry Man said:**
> Ms. Daisy will disagree, I believe, but I think an outbound Firewall is virtually useless for users.

Just getting to the point of disagreeing about outbound rules means that you are in the fraction of one percent of users who practice solid security.

---

### Post by nomenkultur on 2012-12-14
EDIT: stupid me, I have red the link ms.daisy posted and I got it exactly the way I wanted... turns out you have to allow 57 and 58 and a bunch more stuff


Now I'm going to get into appamor and try to shield firefox.

 do I have to do much or I can just leave it as it is and it should be safe enough??

 I heard chromium doesn't work with apparmor, is it true?


 and finally my last question:


 I once saw this amazing terminal command that would display info like this:


service:        in:    out:              my ip:                                              the ip you are connected to:               program etc:
tcp                              1                 0                       420.420.420                      91.189.94.25:80                                      CLOSE_WAIT4043/ubuntu-geoip-p                  


 I think it was

 netstat -lanp

 netstat -anp

 something

 and it would constantly refresh so you always knew what connections were going on as long as you left the terminal open

 anyone knows the exact command?

> oh I have been burned by windows.

 You see when you get hacked in windows the criminals don't connect to your system directly, they exploit your system and popular apps so they can have them dial 'home' to them.

 I saw with my own eyes a bunch of outgoing connections to ukraine and God knows where else using the most varied ports and services.

 so I found out that for nomal web browsing all you need is 80 and 443, so why take risks?

 anyways I found a simple way to achieve good enough security with just that simple ufw


 put incoming into reject (so it won't even icmp echo) and then outgoing to allow BUT then start rejecting everything that is not  80 or 443

[http://i.imgur.com/1CpMx.jpg](http://i.imgur.com/1CpMx.jpg)

 it works pretty good, but it should allow you to block all outgoing and then open up just 80 and 443 as that would be optimal.


---

### Post by Lfekey on 2012-12-14
> **DuckHook said:**
> Just getting to the point of disagreeing about outbound rules means that you are in the fraction of one percent of users who practice solid security.

But linux doesn't have a well application based firewall.

---

### Post by nomenkultur on 2012-12-14
> **Lfekey said:**
> But linux doesn't have a well application based firewall.

  that's the only thing I really liked about those commercial firewalls was they popping up warnings saying:
 
"
 this  X thing wants to connect to Z ip using this port:    allow it? "


 but I found out that there's a way for you to know exactly what is connected to where in linux:


 one way is the netstat command I described above that keeps refreshing your terminal


 the other is a conky thing that sits on your desktop and I've seen laptops of people that have it and it shows:

 firefox    61.123.34.45:80
 firefox    192.blablabla

 
 so you can monitor and see if there's anything strange happening

---

### Post by nomenkultur on 2012-12-14
ok got apparmor up and running and it's quite easy and functions perfectly:

 for others who might be new to linux/ubuntu like me:

 
  sudo aa-status



 Will tell you that there are 0 profiles loaded and everything is off

 the profiles are in computer/etc/apparmor.d/

 there is one called firefox

 you can't enforce it before doing this:



 sudo apt-get install apparmor-utils



 then 


  sudo aa-enforce /etc/apparmor.d/usr.bin.firefox


 then 

sudo aa-status
apparmor module is loaded.
4 profiles are loaded.
4 profiles are in enforce mode.
   /usr/lib/firefox/firefox{,*[^s][^h]}
   /usr/lib/firefox/firefox{,*[^s][^h]}//browser_java
   /usr/lib/firefox/firefox{,*[^s][^h]}//browser_openjdk
   /usr/lib/firefox/firefox{,*[^s][^h]}//sanitized_helper
0 profiles are in complain mode.
0 processes have profiles defined.
0 processes are in enforce mode.
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.


 everything works well with appamor fox profiles and restricted firewall.


 canonical should ship ubuntu with gufw and appamor on by default.

---

### Post by chadk5utc on 2012-12-14
sounds like zone alarm or another Windows app

---

### Post by Lfekey on 2012-12-14
> **nomenkultur said:**
> that's the only thing I really liked about those commercial firewalls was they popping up warnings saying:
 
&quot;
 this  X thing wants to connect to Z ip using this port:    allow it? &quot;


 but I found out that there's a way for you to know exactly what is connected to where in linux:


 one way is the netstat command I described above that keeps refreshing your terminal


 the other is a conky thing that sits on your desktop and I've seen laptops of people that have it and it shows:

 firefox    61.123.34.45:80
 firefox    192.blablabla

 
 so you can monitor and see if there's anything strange happening

I really miss comodo and sandboxie here. Apparmor is great but not completed yet.

---

### Post by vasa1 on 2012-12-14
> **nomenkultur said:**
> ...
 canonical should ship ubuntu with ... appamor **on by default**.
I thought apparmor is on by default. The Firefox profile needs to be enabled.

---

### Post by CharlesA on 2012-12-14
> **vasa1 said:**
> I thought apparmor is on by default. The Firefox profile needs to be enabled.
Correct.

As far as Windows is concerned, if you aren't careful about what stuff you install, the only thing you really need to worry about are browser exploits and that is an issue with the browser and not the OS.

---

### Post by nomenkultur on 2012-12-14
If apparmor is on by default is of little consequence since aastatus tells me there are 0 profiles loaded 0 x 0 y 0 z.


CharlesA take it from someone who had his mastercard stolen, his bank acct's breached and was even spied by webcam:

 In windows you need to worry about every piece of software you have, from adobe flash (remember that exploit back in march?) to skype. 


 I was operating under the false hope that my windows wouldn't be easily cracked... that turned out well. 

 if you are targeted by eastern european hackers that know what they are doing, you better catch up on network security and do it fast .


 Anyways and back to the topic at hand:

 I really like ubuntu 13.04, from a security standpoint would it be stupid to install it and use it seeing it's alpha software?

  I have been reading but have to admit that writing a apparmor profile is beyond my skills .

 Has anyone made an apparmor profile for chromium or should I just stick to ffox?


chad: I had that complete eset security package.  It would still freak me out seeing windows system processes dialing to swizerland and the like (I would trace the ip's and they seemed legit) but I decided to use windows only offline and for premiere and switch to linux for online especially since I log in from public wi-fi's a lot... I went with fedora but elementary and ubuntu seem so much friendlier.


 edit (permit me me to dump some stuff here so I can easily find it later):

 
sudo apt-get remove unity-lens-shopping
 [https://addons.mozilla.org/en-us/firefox/addon/showip/](https://addons.mozilla.org/en-us/firefox/addon/showip/)

 [https://addons.mozilla.org/en-us/firefox/addon/noscript/?src=ss](https://addons.mozilla.org/en-us/firefox/addon/noscript/?src=ss)

---

### Post by Lfekey on 2012-12-14
You installed 13.04?  Apparmor should have some profiles enabled without 'sudo apt-get install apparmor-profile".  aa-genprof is your friend. Simply 'sudo aa-genprof path/to/your/app',then launch app.

---

### Post by nomenkultur on 2012-12-14
Lfe I'm loading 13.04 to ram and running it as a live session

 in 13.04 apparmor has 0 profiles loaded.

 

I found the best way to monitor your connections:

 With conky you can set it up so it is always showing what you are connected to etc

[http://i.imgur.com/99EFL.jpg](http://i.imgur.com/99EFL.jpg)

 of course I had to **** it up but I need to ask for help and I'll figure out how get conky to act like a firewall monitor.

---

### Post by CharlesA on 2012-12-14
> **nomenkultur said:**
> 
CharlesA take it from someone who had his mastercard stolen, his bank acct's breached and was even spied by webcam:

 In windows you need to worry about every piece of software you have, from adobe flash (remember that exploit back in march?) to skype. 


 I was operating under the false hope that my windows wouldn't be easily cracked... that turned out well. 

 if you are targeted by eastern european hackers that know what they are doing, you better catch up on network security and do it fast .

The thing is, flash vulnerabilities are a known thing and are based on browser attacks, which can occur no matter the OS. It is best to run without flash, but as flash is used quite often on the internet, so you kinda stuck on that one.

The best thing you can do is sandbox or confine the browser with AppArmor or SELinux or Sandboxie, etc and run addons such as NoScript/Adblock/Flashblock, etc.

Now if you really are being targeted by hackers there isn't much you can do because anyone with enough resources and dedication can break into almost any form of security you may use.

---

### Post by nomenkultur on 2012-12-14
Charles, hopefully, a hardened linux will take more effort than other systems meaning it will no longer be a soft target and not worth the time investment.


if anyone wants the best I could come up with:

> TEXT

${color #bac7c7}In: ${color}${downspeed wlan0} kb/s${offset 58}${color #bac7c7}Out: ${color}${upspeed wlan0} kb/s
${color}${downspeedgraph wlan0 20,105 3E3A39 f17f1f}${alignr}${upspeedgraph wlan0 20,105 3E3A39 f17f1f}

${color #bac7c7}${tcp_portmon 1 65535 count} connections

 ${color #bac7c7}Outbound${alignr}Port${color}
 ${tcp_portmon 32768 61000 rhost 0}${alignr}${tcp_portmon 32768 61000 rservice 0}
 ${tcp_portmon 32768 61000 rhost 1}${alignr}${tcp_portmon 32768 61000 rservice 1}
 ${tcp_portmon 32768 61000 rhost 2}${alignr}${tcp_portmon 32768 61000 rservice 2}
 ${tcp_portmon 32768 61000 rhost 3}${alignr}${tcp_portmon 32768 61000 rservice 3}
 ${tcp_portmon 32768 61000 rhost 4}${alignr}${tcp_portmon 32768 61000 rservice 4}
 ${tcp_portmon 32768 61000 rhost 5}${alignr}${tcp_portmon 32768 61000 rservice 5}
 ${tcp_portmon 32768 61000 rhost 6}${alignr}${tcp_portmon 32768 61000 rservice 6}
 ${tcp_portmon 32768 61000 rhost 7}${alignr}${tcp_portmon 32768 61000 rservice 7}

 ${color #bac7c7}INTRUSION DETECTION:${alignr}Port${color}
 ${tcp_portmon 1 32767 rhost 0}${alignr}${tcp_portmon 1 32767 lservice 0}


---

### Post by Ms. Daisy on 2012-12-14
> **nomenkultur said:**
> I once saw this amazing terminal command that would display info like this:
service:        in:    out:              my ip:                                              the ip you are connected to:               program etc:
tcp                              1                 0                       420.420.420                      91.189.94.25:80                                      CLOSE_WAIT4043/ubuntu-geoip-p                  

 ...and it would constantly refresh so you always knew what connections were going on as long as you left the terminal open

 anyone knows the exact command? sudo watch netstat -antp

---

### Post by DuckHook on 2012-12-14
> **Ms. Daisy said:**
> sudo watch netstat -antp

You are scary.:shock:

---

### Post by nomenkultur on 2012-12-15
> **DuckHook said:**
> You are scary.:shock:

 scaringly amazing

 :KS:KS:KS:KS:KS 

 Thanks Ms. Daisy thanks to your posts I think I'm able to get ubuntu as safe as it can possibly get.

 1. Configured the firewall like bodhi wrote: reject out and in and only have a couple of outgoing ports open.

 2. Loaded apparmor profiles and got a bunch of new ones from this site:

rookcifer.blogspot.com/2012/10/more-apparmor-profiles-for-ubuntu-1204.html

 3. Thanks to the command you posted I can monitor what is going on with the network  ( I would like to get conky to do this so I wouldn't have to have a terminal open but, alas, that is far beyond my technical skill and the conky people are more interested in eye candy configs than security)

 
[http://i.imgur.com/zRLQK.jpg](http://i.imgur.com/zRLQK.jpg)

these steps worked for both 13.04 and ubuntu 12.04 based elementary os, so I think everyone should look into them.

 anything else? I mean is there any obvious thing or any further step I should take?

 edit: just remembered an extra thing:  look at the startup processes/services and shut down what isn't needed



last edit: sector11 made a conky config that acts like an excelent firewall monitor you can see and download it here:

[http://ubuntuforums.org/showpost.php?p=12406247&postcount=21218](http://ubuntuforums.org/showpost.php?p=12406247&postcount=21218)

---

