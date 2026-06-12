---
title: "Linux for my grandpa"
date: 2012-06-04
forum: The Cafe
---

### Post by layers on 2012-06-04
I think I need a little bit of help when it comes to decisions like these - I feel like what I like is not relevant.

I have this old IBM laptop (we all know what they look like) and I want to send it overseas to my grandpa, so he can use it for communication in his village. I suppose the only uses would be Skype-ing and reading online about bees and rabbits and what not.

I also would like to have remote access to it, in case something happens, and don't want to fuss about the antivirus - naturally, I thought about Lubuntu. It's adequate for the 1GB RAM and 1.7GHz CPU. My grandpa is familiar with XP, so a menu and a task bar with open windows would not be a learning curve for him.

Does anyone have anything else I should look into as a good idea?

---

### Post by Face-Ache on 2012-06-04
From my own recent, albeit limited experience, i'd agree that Lubuntu is the way to go. I've recently installed it in a 512mb RAM and 1.8Ghz CPU laptop, and it's running pretty good.

I agree that it would be the easiest distro for a Windows user to transition to.

---

### Post by drawkcab on 2012-06-04
Linux Mint Debian Edition.  Rolling release is good for grandpa!

I would agree that lxde is probably the most straight forward DE tho.

---

### Post by Perfect Storm on 2012-06-05
> **drawkcab said:**
> Linux Mint Debian Edition.  Rolling release is good for grandpa!


Bad advise. It can break time to time. And if he's no linux/computer wiz it will give more headache than pleasure.


Something stable in this case would be a better option.

---

### Post by layers on 2012-06-05
> **Artificial Intelligence said:**
> 

Something stable in this case would be a better option.

I just don't know which version of Lubuntu to put on.


and a rolling release would not be an option here. I need something that works, I don't care about the latest greatest stuff.

---

### Post by Paqman on 2012-06-05
> **layers said:**
> I just don't know which version of Lubuntu to put on.


12.04, the current release. Since it's an LTS he can keep using it for five years without needing to upgrade. Set it to install security updates automatically then disable proposed, backports and maybe updates too. Should be super-stable.

What browser does he want?

---

### Post by Linux_junkie on 2012-06-05
> **Paqman said:**
> 12.04, the current release. Since it's an LTS he can keep using it for five years without needing to upgrade. Set it to install security updates automatically then disable proposed, backports and maybe updates too. Should be super-stable.

What browser does he want?

Lubuntu 12.04 is _not_ an LTS.  I would still use the latest (current) version of Lubuntu though or version 11.10 as should be very stable once updated.

---

### Post by craig10x on 2012-06-05
I would suggest Zorin 6....it's in 32 bit RC right now but will soon be final released with 32 and 64 bit versions...take a look at the RC in live session and if he likes it, install the final when it arrives...

It uses gnome 3 fallback modification with an awn panel (not dock) on the bottom and gno menu defaulted to a "windows 7" style slab menu (that can be changed to other looks also in the gno menu...i use one of the others myself)...

He will be getting ubuntu 12.04 underneath, with this neat desktop environment and some nice compiz effects and other refinements....very smooth, fast and snappy performance too... :)

In case the computer isn't able to run with the compiz i believe it reverts to an alternate mode to handle that...(using metacity i believe)...

It's a great ubuntu based distro for newbies and "old timer linux users" alike...it should be able to run on there....give it a try....but if you decide to install i would do it with the final release version...the link to the zorin 6 RC is in the "blog section" of their website...

---

### Post by xedi on 2012-06-05
> **Linux_junkie said:**
> Lubuntu 12.04 is _not_ an LTS.  I would still use the latest (current) version of Lubuntu though or version 11.10 as should be very stable once updated.

If LTS is important, then Xubuntu 12.04 would be worth considering, because it is supported for three years and it should run well on the machine, too.

EDIT: Is the CPU a single core processor?

---

### Post by IWantFroyo on 2012-06-05
I would recommend using Lubuntu 12.04. Supported for 5 years or not, I still think it's the best option.
 
As for remote access, would ssh work?

---

### Post by QIII on 2012-06-05
Once you get it the way you like it, install openSSH and either FreeNX or NoMachine NX 3.5.

OpenSSH uses SSH2 and you should use a 4096 bit key.  The combination of openSSH and one of the last two will do well in a low bandwidth scenario.  VNC can be a bit heavy on bandwidth, although some products are well-optimized and can be used over SSH.  There are several tutorials on SSH security.  It's not a magic bullet, especially if you get iptables wrong.

If you don't care about a graphical interface, skip NX and VNC.  But that might not be helpful if grandpa says "When I click this it does that" and you have to troubleshoot.

Also, invest the $20 annual fee for one of the services, like dyndns, that gives you a permanent IP address that updates its connection to an IP address that may change on grampa's end.

You'll have to talk grandpa through setting up that sort of service on his end.

---

### Post by layers on 2012-06-05
Thanks for all the suggestions.

I'm just considering installing the OS, I don't think any updating will have a point, now or in future. Maybe I will go over there once a year to check it up, but nothing else. Plus, I'm one of those people who still run 11.04 and have updating disabled...

And I think I will need GUI for the remote access.

Zorin OS probably feels like a XP, but the computer will probably run better with XFCE or LXDE - it's a thinkpad t42 - 1RAM, Pentium D 1.7GHz. Plus, I am installing everything and sending the machine, I don't have the chance to ask his preference.

And I think Chrome would suffice for bees and rabbit's readings, would you say?


As far as remote access, I'm looking for something free, and basic - the internet is not that good where I am sending it, so a low bandwith option is a good point - it is like a small village in the mountains (very remote). I think FreeNX is best here. Do people use it?
Also, I've never use the remote access application in Ubuntu, is it any good?

---

### Post by QIII on 2012-06-05
I've used FreeNX and it is good.  I don't think it is as feature rich as NoMachine NX (the basis for FreeNX).

NoMachine NX 3.5 server is free for up to 2 connections and the client is also free, so don't worry there.  Although it is easy to install once you have done it a couple of times, it can be a royal pain the first time.

DON'T try the preview of 4.0.  It is pre-Alpha and only gives you a 60 day evaluation.

The one thing I wonder about with regard to Lubuntu is whether you will need to use gdm instead of the stock desktop manager.  You'll need to experiment with both FreeNX and NoMachine NX.  The client may have trouble starting an X session with something other than kdm or gdm on the server.

---

### Post by HermanAB on 2012-06-06
Howdy,

My mother in law runs Fedora on a netbook. She lives in a village and uses a wireless ISP. The only program she uses is Skype.  She doesn't even do web browsing or email.  If she gets a problem, I ask her to do desktop sharing with Skype, so I can see what is going on, then I fix it over SSH.

---

### Post by Paqman on 2012-06-06
> **Linux_junkie said:**
> Lubuntu 12.04 is _not_ an LTS.  I would still use the latest (current) version of Lubuntu though or version 11.10 as should be very stable once updated.

In that case I wouldn't use it. For a machine like this long-term stability and low-maintenance are key.

---

### Post by stalkingwolf on 2012-06-06
Zorin has the look changer available.  with gnome and windows.  it works well
on minimal systems. i have it running on 3 with 1 gb ram and 2.6 gz processors.

Skype works well as does gyache.  It also gives you the choice to install the browser you want.

It has been a very stable and functional install for me.

BTW I just installed it on a laptop for a Gentleman that is 75 yrs old and hasnt touched a computer since he was using gwbasic in 98.  his last
computer had a 6 gb drive and 512 ram with a crt monitor.  He still has his first computer a trs80 that a friend is using to teach his kids to program on.

---

### Post by hakermania on 2012-06-06
I would that say Lubuntu & ssh will do the job :)

But test first if skype is working correctly!

---

### Post by SeijiSensei on 2012-06-06
One good solution for remote access is to use OpenVPN with a [shared static key]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html").  On grandpa's computer, you'd include the "remote" directive pointing at your router.  On the router you'd forward a UDP port back to your computer to the OpenVPN instance running there.  If OpenVPN is set to start at boot on grandpa's machine, it will keep trying to set up a tunnel to you.  Once it's done so, you can access his machine by its tunnel IP.  In this mode his computer stays connected to you no matter where he is at a predictable (private) address.

I use this technique to manage servers behind company firewalls.

---

### Post by TeamRocket1233c on 2012-06-06
Xubuntu or Fedora.

---

### Post by Viper1987 on 2012-06-06
Don't do any work on a computer for your grandpa unless you plan on taking at least a phone call a day, lol...

All kidding aside, whatever the OS, put a lot of icons/widgets on the desktop and make them LARGE

---

### Post by layers on 2012-06-06
> **SeijiSensei said:**
> One good solution for remote access is to use OpenVPN with a [shared static key]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html").  On grandpa's computer, you'd include the "remote" directive pointing at your router.  On the router you'd forward a UDP port back to your computer to the OpenVPN instance running there.  If OpenVPN is set to start at boot on grandpa's machine, it will keep trying to set up a tunnel to you.  Once it's done so, you can access his machine by its tunnel IP.  In this mode his computer stays connected to you no matter where he is at a predictable (private) address.

I use this technique to manage servers behind company firewalls.

But you have to be at home to access this, is that correct?

---

### Post by Deuce1912 on 2012-06-06
> **Linux_junkie said:**
> Lubuntu 12.04 is _not_ an LTS.  I would still use the latest (current) version of Lubuntu though or version 11.10 as should be very stable once updated.

In this case I would install Ubuntu 12.04 and install the LXDE over the top of it. Then you would have a LTS version of Lubuntu. --- More or less.

Deuce1912

---

### Post by layers on 2012-06-06
and the 12.04 version of (l)ubuntu is the most lightwieght? Other than the updating, is there any particular reason I should pick Ubuntu 12.04 versus Ubuntu 10.11?

---

### Post by SeijiSensei on 2012-06-07
> **layers said:**
> But you have to be at home to access this, is that correct?

No, you could set up another tunnel between your laptop and your home then connect to grandpa's computer over his tunnel.  You'd need to enable IP forwarding on the VPN server and a couple of ACCEPT rules to iptables if you run a firewall on the server.

---

### Post by layers on 2012-06-07
> **SeijiSensei said:**
> No, you could set up another tunnel between your laptop and your home then connect to grandpa's computer over his tunnel.  You'd need to enable IP forwarding on the VPN server and a couple of ACCEPT rules to iptables if you run a firewall on the server.

I think I should do something less convoluted.

---

### Post by SeijiSensei on 2012-06-08
> **layers said:**
> I think I should do something less convoluted.

It sounds more complicated than it is in practice.  Basically you just need two configuration files on the server to support the tunnels, and a configuration file on each remote to set up the connection.

---

### Post by Meelis on 2012-06-17
I do not recommend any linux for elderly people.
They are too complex to use.

My mother and grandpa had really a lot of troble with linux.
Most often with printer access permission lost from time to time (like 2-3 times a month). Also problems with sharing files and having rights to do everything with them.
I made backup of another persons data under my user, this was hard for me. Then this other person wasnt able to access to his own data that i had backed up and copied back under his home folder (that was also complex for me).

So you see, there are tons of bugs with Linux.
My 90 yr grandpa saved money 3 months for Windows Vista and no problem yet. I have Windows Vista install from year 2008 on my computer.

---

### Post by Old_Grey_Wolf on 2012-06-17
> **Meelis said:**
> I do not recommend any linux for elderly people.
They are too complex to use.

Linux may be too complex **for you to use**; however, I am 64 years old. I have absolutely no problems installing, configuring, or using Linux. I have no problems sharing files or making backups of my data.

> **Meelis said:**
> 
So you see, there are tons of bugs with Linux.


:lolflag:

---

### Post by layers on 2012-06-17
oh, no, I disagree. For a person who uses only an internet browser and Skype, Linux is by far the best choice. (maybe iOS and Android come close)
I'm talking about two things - antivirus support and that apparent "slowing down" thing that happens on XP machines after a year of use without reinstalling.
(I know, I've had problems with printing, too, but my pops won't be doing that, he has no printer :P)

---

### Post by Meelis on 2012-06-18
> **Old_Gray_Wolf said:**
> Linux may be too complex **for you to use**; however, I am 64 years old. I have absolutely no problems installing, configuring, or using Linux. I have no problems sharing files or making backups of my data.



:lolflag:

My grandpa remembers a lot of facts from past and his specialty, but he can't remember how to print or attach files to email.

Sure i'm no pro but i get printer shared in 0,5 - 4 hours. Still frustrating when it happens a lot because dhcp changes ip's in home network.

---

### Post by mastablasta on 2012-06-18
i've set up XFCE to look like XP. it's easy to do so (a couple of mouse click and you are done). then you just lock in the config. and if XFCE works well on 256MB with 1.2 ghz CPU it will run like crazy on your setup.
 
Lubuntu still has some limits (besides not being LTS).
 
> **layers said:**
> I'm talking about two things - antivirus support and that apparent "slowing down" thing that happens on XP machines after a year of use without reinstalling.

 
We have about 6000+ maschines in company mostly runnign windows XP but newer ones run windows 7. there are no major slowdowns and no reinstall were made. the only slowdown issue i noticed was at my colleague. turn out it was a faulty disk drve. after it was replaced and image cloned to new drive it works normal again. most maschines also have only 1 GB ram.
 
what i am saying is that if you know how to handle the OS there shouldn't be much slow down.
 
oh and there was a slowdown in i think when SP2 came out. SP1 needed 256MB ram to run and SP2 needs 512MB to run. however if you have 2GB you won't really see the slow down. i did see it on a mashcine with 256 MB ram.

---

### Post by kurt18947 on 2012-06-18
> **Meelis said:**
> My grandpa remembers a lot of facts from past and his specialty, but he can't remember how to print or attach files to email.

Sure i'm no pro but i get printer shared in 0,5 - 4 hours. Still frustrating when it happens a lot because **dhcp changes ip's in home network**.

I don't know what kind of printer you have, but I'm able to assign static I.P. addresses to printers. Then there is no problem.  I had the same problem with I.P. assigned by dhcp.

---

### Post by stalkingwolf on 2012-06-18
I have a t42p . It is dual booted with xp and zorin 5.2.   it runs great.  a friend has it right now, it runs better and is more stable than her "gaming system" with win 7.

---

### Post by HansKisaragi on 2012-06-18
Ubuntu 12.04 with cinnamon 1.4

---

### Post by cbanakis on 2012-06-18
I think its a great idea.

I have been doing the same thing with all of my older/less computer literate relatives.

Alot of people think you have to be some guru to use linux.

Not true at all.

If you install the OS, and something does not work correctly, you may need a guru to get it working right, but once its done, its done.

I got so sick and tired of removing virus's and repairing windows for all these people, so eventually, I started saying, "Sure, I'll fix it" (ie, I am erasing that windows nonsense, and installing linux) :)

"There is your internet, there is your email, etc, etc"

No complaints whatsoever.

Just make sure you take the time to test everything out before you dump it on them, specifically all the things you know they are going to do.

Most of the people I have done this for love it.

Newer computers run faster than ever.

Older computers seem to be a bit sluggish compared to a clean windows install, in my experience.

But that clean install feel of windows only lasts a few months.

In the long haul, linux is always faster.

Like I said, most people think if they don't know linux, they will screw up the computer.

The reality, is that you MUST know linux, in order to screw it up.

I know way more about linux than my father, and I screw my system up once a week.

But he has been using Ubuntu 10.04 since it came out, and he has not had a single issue.

You really need to know what your doing to break this system.

---

### Post by layers on 2012-06-18
> **cbanakis said:**
> 

But that clean install feel of windows only lasts a few months.



Exactly! And my Ubuntu is as snappy as it was when I installed it a year ago. I don't know what is the cause for this, but it's true.

---

### Post by Old_Grey_Wolf on 2012-06-18
> **Meelis said:**
> 
Sure i'm no pro but i get printer shared in 0,5 - 4 hours. Still frustrating when it happens a lot because dhcp changes ip's in home network.

> **kurt18947 said:**
> I don't know what kind of printer you have, but I'm able to assign static I.P. addresses to printers. Then there is no problem.  I had the same problem with I.P. assigned by dhcp.

My last 2 routers provided DNS for the LAN (one was a Linksys 3000n and the current one a Verison FIOS provided Westell UltraLite 9100EM). Any device connected to the router could have a Host Name assigned to it. The Host Name followed the device even when DHCP changed the IP address. Then I could use the Host Name rather than IP address for ssh, rdp, ping, printing, etc.

---

### Post by layers on 2012-07-04
In all my efforts to keep it simple and robust, I installed x11vnc and connected to the laptop from the client - but they are in the same network, so in the java-browser, I typed in 192.168.0.101:5800

It doesn't work if I try my external IP address, although I forwarded 5800-5900. There is an ADSL2+ modem in front of the router, do I have to open its ports as well?

---

### Post by Roasted on 2012-07-04
I use Ubuntu + LXDE on my netbook... works great... would that not be supported for 5 years since it's the official Ubuntu build with LXDE installed after?

---

### Post by sudodus on 2012-07-04
> **Roasted said:**
> I use Ubuntu + LXDE on my netbook... works great... would that not be supported for 5 years since it's the official Ubuntu build with LXDE installed after?
That issue is discussed in this link
[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1954702_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1954702")

---

### Post by screaminj3sus on 2012-07-04
> **Old_Gray_Wolf said:**
> My last 2 routers provided DNS for the LAN (one was a Linksys 3000n and the current one a Verison FIOS provided Westell UltraLite 9100EM). Any device connected to the router could have a Host Name assigned to it. The Host Name followed the device even when DHCP changed the IP address. Then I could use the Host Name rather than IP address for ssh, rdp, ping, printing, etc.

Linksys routers also have a handy feature called "dhcp reservation". Just click the dhcp reservation button, it brings up a list of devices, and click on the device you want. This makes dhcp give the selected device the same ip address every time. Essentially a static ip without the fuss :) Useful for wireless printers, and portforwarding and such.

---

### Post by rewyllys on 2012-07-05
> **Meelis said:**
> I do not recommend any linux for elderly people.
They are too complex to use.

My mother and grandpa had really a lot of troble with linux.
Most often with printer access permission lost from time to time (like 2-3 times a month). Also problems with sharing files and having rights to do everything with them.
I made backup of another persons data under my user, this was hard for me. Then this other person wasnt able to access to his own data that i had backed up and copied back under his home folder (that was also complex for me).

So you see, there are tons of bugs with Linux.
My 90 yr grandpa saved money 3 months for Windows Vista and no problem yet. I have Windows Vista install from year 2008 on my computer.
Too complex for you, perhaps.  

Thank goodness I've been around long enough--being in my ninth decade--to be able to handle Linux, not to mention OS/2 back in the 1990s, and MS-DOS back in the 1980s, and other OSs back to 1952, when I wrote my first computer program--in octal.

But I wish you luck in maturing.:)

---

### Post by |{urse on 2012-07-05
Google shows this as top answer for yahoo answers. I've never tried it, kinda curious also.

[http://www.eldy.eu/](http://www.eldy.eu/)

I personally, would recommend Ubuntu.

---

### Post by Old_Grey_Wolf on 2012-07-05
> **rewyllys said:**
> Too complex for you, obviously.  

Thank goodness I've been around long enough--being in my ninth decade--to be able to handle Linux, not to mention OS/2 back in the 1990s, and MS-DOS back in the 1980s, and other OSs back to 1952, when I wrote my first computer program--in octal.

But I wish you luck in maturing.:)

You are older that I am; however, I remember using OS/2, MS-DOS, and UNIVAC. I was a also pretty good octal "finger mumbler". 

For those that are young, a "finger mumbler" wrote programs by entering machine language code in octal using the front panel of a computer. We didn't have keyboards and monitors then. They were 8-bit computers with 64KB of magnetic core memory, and were 5 ft tall.

:lolflag:

I have to admit that most of the people I know, and it doesn't matter what age they are (13 to 70), don't know very much about computers.

Most of us on the forum are exceptions to the norm and do not fall within the stereotypes.

:lolflag:

---

### Post by dwhite on 2012-07-06
> **craig10x said:**
> i would suggest zorin 6....it's in 32 bit rc right now but will soon be final released with 32 and 64 bit versions...take a look at the rc in live session and if he likes it, install the final when it arrives...




+1

---

### Post by 1roxtar on 2012-07-06
> **IWantFroyo said:**
> I would recommend using Lubuntu 12.04. Supported for 5 years or not, I still think it's the best option.
 
As for remote access, would ssh work?

For remote access, you could install Chrome and install the extension CHROME REMOTE DESKTOP.  It's still in Beta, but it works really well.  Another program you could install is Teamviewer.

---

