---
title: "How-To: Disable IPV6 to speed up Internet."
date: 2005-11-08
forum: Tutorials
---

### Post by SlowJet on 2005-11-08
Hello all, :)

  During today's  Dapper development updates one of the packaes wanted to replace the /etc/modporbe.d/aliases file. Yes or No? 
Normally I would say No to keep my confuguration but it mentioned "to keep the developers additions". So I say, Yes replace it.

I knew this was the file that would trun IPV6 back on and so I had to change it again after re-boot.
Well, I guess I forgot how to do that (format wise) but after entering several forms I thot the net had sped up some but it was still stalling and slugish at the end of a web page load, as if it had to wait for a done signal.

I thoht I would re-boot and see if there was a difference. Sure enough the network is responding a top speed now.

So here are the changes I put in with the orginal comment out.
But the re-boot is required.

alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off
#alias net-pf-10 ipv6

IPV6 slows down the IPV4 environment if the router out the door does not understand IPV6 and for most people IPV6 is not needed.

So,  add the 3 lines, comment the orginal, save and re-boot.

Firefox and Thunderbird will respond 3 to 4 times faster.


SJ

---

### Post by i3dmaster on 2005-11-08
wow... that sounds terrific. I will give it a try. Thanks!!

---

### Post by GoA on 2005-11-09
Do I put those three lines at the end of the file or at the network protocols space? Please be more specific with these. You have to make sure all the noobs understand these instructions. :)

---

### Post by kashms on 2005-11-09
[QUOTE=SlowJet]
  During today's  Dapper development updates one of the packaes wanted to replace the /etc/modporbe.d/aliases file. Yes or No? 
[/QUOTE]

I think that's the /etc/**modprobe.d**/aliases file.

---

### Post by SlowJet on 2005-11-09
Sorry about the sloppy post.

cd /etc/modprobe.d
darwinhwebb@Celcila-24:/etc/modprobe.d$ dir
aliases           alsa-base     blacklist          isapnp
aliases~          arch          bluez              nvidia-kernel-nkc
aliases.dpkg-old  arch-aliases  ibm_acpi.modprobe  toshiba_acpi.modprobe
darwinhwebb@Celcila-24:/etc/modprobe.d$ cat aliases
# These are the standard aliases for devices and kernel drivers.
# This file does not need to be modified.
#
# Please file a bug against module-init-tools if a package needs a entry
# in this file.

# network protocols ##########################################################
alias net-pf-1  unix
alias net-pf-2  ipv4
alias net-pf-3  ax25
alias net-pf-4  ipx
alias net-pf-5  appletalk
alias net-pf-6  netrom
alias net-pf-7  bridge
alias net-pf-8  atm
alias net-pf-9  x25
#                               1, 2, 3 new lines
alias net-pf-10 ipv6 off       
alias net-pf-10 off
alias ivp6 off
#alias net-pf-10 ivp6           =========the original line
alias net-pf-11 rose
alias net-pf-12 decnet
# 13 NETBEUI
alias net-pf-15 af_key
alias net-pf-16 af_netlink
alias net-pf-17 af_packet

---

### Post by mhael on 2005-11-09
There's an easy way: instead of changing **aliases** file, create fie named **bad_list** in **/etc/modprobe.d** containing this line:
```
alias net-pf-10 off
```Now reboot and voila, no IPv6 on your system!

This method will work even if /etc/modprobe.d/aliases get replaced at some update.

---

### Post by sailor420 on 2005-11-09
[QUOTE=mhael]There's an easy way: instead of changing **aliases** file, create fie named **bad_list** in **/etc/modprobe.d** containing this line:
```
alias net-pf-10 off
```Now reboot and voila, no IPv6 on your system!

This method will work even if /etc/modprobe.d/aliases get replaced at some update.[/QUOTE]

If we do this, do we have to do any of the steps above? I'm a bit confused...

Also, how would we check to see if IPv6 is enabled or disabled?

---

### Post by Yagisan on 2005-11-09
From the ubuntu-devel mailing list (culled from a variety of posts)
[quote=ubuntu-devel list]
Having IPv6 be the cause of 'slow' connection is actually a common
misconception, reinforced in that disabling some IPv6 features may help
mitigate the problem, in most cases it is the result of bad network
configuration.

IPv6 itself does not in any way slow down your connection, problems will
arise however if you have a route out to the IPv6 internet but it is not
operational, as the browser will try to connect and it will take a while
to time-out, note this would also happen with a bad IPv4 internet
connection.

Another cause in the past has been bugs in programs (e.g. mozilla) that
do the wrong thing internally, most of the major problems here have been
fixed.

As above, these issues would *only* happen if the website you are trying
to connect to has an IPv6 address associated.  Another cause can be
having an IPv6 name-server configured in resolv.conf or similar, in
which case the problem would arise if you were trying to connect to
*any* address.


Most people do not have a problem with having IPv6 enabled, it
simply is un-used when not in use.

If you are having problems, it is likely due to some kind of
misconfiguration, you would need to diagnose that.

In particular, the commands 'ip -6 route' may help, it will indicate if
you have any routes to the broader IPv6 world (look for '2000::/3' and
'default' routes).  THis may be caused by an incorrect router on your
network, or by using tunneling software (such as tspc from
freenet6.net), or a number of other reasons.

In simpler terms: with a default Ubuntu install, if you're not using
IPv6, you shouldn't even know it's there. If you're experiencing
negative side effects, they're likely the result of a broken application
or incorrect configuration. Firefox, for instance, is a known culprit.

One thing you can try is, with IPv6 enabled, to launch a terminal, and
type 'host www.google.com'. If the command succeeds quickly, listing
Google's IPs, then you're not having general network connectivity
trouble, and you can start filing bug reports against whichever specific
applications are being slow.
[/quote]

My suggestion to all those with "slow" internet. Try the last paragraph especially, then start filling bug reports.

---

### Post by mhael on 2005-11-09
[QUOTE=sailor420]If we do this, do we have to do any of the steps above? I'm a bit confused...

Also, how would we check to see if IPv6 is enabled or disabled?[/QUOTE]

No, all you need is to create /etc/modprobe.d/bad_list with specified line and reboot.

To check IPv6 state open terminal and execute:
```
ip a | grep inet6
```
If this command shows some lines - IPv6 is enabled. If output is empty - IPv6 disabled.

---

### Post by Josef K. on 2005-11-10
sorry for the silly question :rolleyes:  (but man page isn't so clear to me)
why there's ipv6 if you should disable?

---

### Post by SlowJet on 2005-11-10
[QUOTE=Josef K.]sorry for the silly question :rolleyes:  (but man page isn't so clear to me)
why there's ipv6 if you should disable?[/QUOTE]


Why do cars go 120 M. P. H. if you shouldn't speed?

IPV6 is part of Inernet II.
It allows so many ip addresses that every man and woamn that ever lived on the planet to have an ip along with their ipod, toaster oven, car, and wallet. :)

But .... it's not ready for the avgerge joe's home rig and will take many years to get rid of IVP4.

IPV6 is mainly used for private networks, cluster communication, and is concitered expermental.


The main reason it needs to be disabled in the home is that a router (almost required now by ISP's) doesn't understand it and it tunnels trough IPV4, but also goes into a long time out and slows down the internet.

SJ
SJ

---

### Post by Saiboogu on 2005-11-10
> **Josef K.]sorry for the silly question :rolleyes:  (but man page isn't so clear to me)
why there's ipv6 if you should disable?[/QUOTE]

For future support. IPv4 is running out of address space, so we must transition to IPv6 at some point soon. IPv6 also offers other benefits that I'm not immediately aware of ... Just the latest and greatest networking gimick, yada yada :) But support isn't widespread yet, so mostly its just sitting idle on your system. Disabling it removes some bloat and streamlines your networking for the time being, especially (in my experience) within Firefox. 

Try typing about:config in your Firefox address bar. Type ipv6 in the "Filter:" box, find the option that says "network.dns.disableIPv6". If it reads "False" right click and toggle it to True. Should give you a slight speedup in your browsing.

EDIT: As usual, I sat on my reply too long. I even refreshed the initial page before I posted to make sure I didn't do this .. Pagebreak fooled me.  said:**
> Why do cars go 120 M. P. H. if you shouldn't speed?

:)

---

### Post by Yagisan on 2005-11-10
[QUOTE=SlowJet]But .... it's not ready for the avgerge joe's home rig and will take many years to get rid of IVP4.

IPV6 is mainly used for private networks, cluster communication, and is concitered expermental.[/QUOTE] And small out of the way places, such as Japan. I think you'll find it is not considered experimental, and deployed more widely then you think.

[QUOTE=SlowJet]The main reason it needs to be disabled in the home is that a router (almost required now by ISP's) doesn't understand it and it tunnels trough IPV4, but also goes into a long time out and slows down the internet.
[/QUOTE] Not at all. I could use the same excuse with IPX and it would be just as untrue. Your IPv4 only router (when not used as a bridge) can't understand IPv6 packets, and so it silently drops them.

Now firefox seems to prefer trying with the IPv6 address first, so it gets your system to try that. After a long timeout, because your router/isp doesn't support IPv6, firefox then trys IPv4, and suddenly everything works fine.


[quote=Saiboogu]For future support. IPv4 is running out of address space, so we must transition to IPv6 at some point soon. IPv6 also offers other benefits that I'm not immediately aware of ... Just the latest and greatest networking gimick, yada yada But support isn't widespread yet, so mostly its just sitting idle on your system. Disabling it removes some bloat and streamlines your networking for the time being, especially (in my experience) within Firefox.[/quote] And yet having it enabled causes no issues for any other application - see the pattern anyone ?

[quote=Saiboogu]Try typing about:config in your Firefox address bar. Type ipv6 in the "Filter:" box, find the option that says "network.dns.disableIPv6". If it reads "False" right click and toggle it to True. Should give you a slight speedup in your browsing.[/quote]
And that is the best workaround for "disabling" IPv6 in the broken application, not systemwide. Those of you affected by this, file bugs on firefox, otherwise you'll be doing this evrytime you upgrade you system.

---

### Post by chien on 2005-11-11
ok, i did it, but I don't want to reboot my system. Is there any way to activate it without rebooting? come on guys, we are on linux.

I did ifdown and ifup but "ip a | grep inet6" still shows some lines.

---

### Post by SlowJet on 2005-11-11
Yagisan, :)

 You may be perfectly correct but on the number of posts on site taking your view vs. the router being stupid is running about 3 to 1 against you.

And it doesnt matter ..
Globally off takes care of all and any futrue programs trying to use IPV6.

I am not in Japan.
I don't have any IPV6 addresses nor do I connect to any.
And there are other slow downs occuring, not just the browswer and mail.

So go round up the unusal suspects in the development world and tell them to get there act together about IPV6 coz it's not going to fly on a home rig until it stops mis-behaving.

SJ

---

### Post by yesplease on 2005-11-11
Originally Posted by SlowJet: IPV6 is mainly used for private networks, cluster communication, and is concitered expermental.

Originally Posted by Yagisan: And small out of the way places, such as Japan. I think you'll find it is not considered experimental, and deployed more widely then you think.

Yagisan has a valid point there. Users should know the consequences of disabling IPV6.

---

### Post by LaSSarD on 2005-11-11
thanks it really works :)
i'm using fasterfox to chronomete it and all the pages are 1/4 faster (at least) :D

---

### Post by canadianwriterman on 2005-11-11
[QUOTE=yesplease]Originally Posted by Yagisan: And small out of the way places, such as Japan. I think you'll find it is not considered experimental, and deployed more widely then you think.

Yagisan has a valid point there. **Users should know the consequences of disabling IPV6**.[/QUOTE]

I've heard this comment before and have been searching the Web for some authoritative information on the "consequences of diasbling ipv6." I can't find any. However, when you Google "disable ipv6" it appears that almost everyone is doing it.

I had to disable it both in Firefox and within the system because everything was taking so long to look up ip adddresses.

---

### Post by Yagisan on 2005-11-12
[QUOTE=SlowJet]Yagisan, :)

 You may be perfectly correct but on the number of posts on site taking your view vs. the router being stupid is running about 3 to 1 against you.
[/quote]True most people disagree with me, but I honestly doubt most of those people are network engineers and actually understand how the IP protocols work. It's a bit like this, I'm not a doctor, but I've seen House, and All Saints, and a few other doctor shows. Now if you have something wrong with you, I could after watching those shows offer an opinion on your problem - I'd probally be wrong though, as I have had no medical training.
[QUOTE=SlowJet]
And it doesnt matter ..
Globally off takes care of all and any futrue programs trying to use IPV6.
[/quote]Yes quite right, unless you are one of the users that connects via IPv6 (then you have a problem don't you)
[QUOTE=SlowJet]I am not in Japan.
I don't have any IPV6 addresses nor do I connect to any.
[/quote]Japan is just one of many places that use IPv6. Consider the fact that other users may require that functionality.
[QUOTE=SlowJet]So go round up the unusal suspects in the development world and tell them to get there act together about IPV6 coz it's not going to fly on a home rig until it stops mis-behaving.[/QUOTE] Well, IPv6 flys on my home rig, and my business rigs, but I obviously don't use the same applications as you. You will need to be specific about the applications that you use.
[QUOTE=SlowJet]And there are other slow downs occuring, not just the browswer and mail.[/quote]
[QUOTE=canadianwriterman]I had to disable it both in Firefox and within the system because everything was taking so long to look up ip adddresses.[/quote]
Now I can't force you to not disable IPv6, but going with my doctor anolgy, the slowness you percive with some applications is the symptoms, but is not the underlying cause. The underlying cause is that the applications you are useing are buggy, and need a bug report filed on them to prompt the developers to fix them.

You may treat the symptons, or you can treat the underlying cause. It's like breaking an arm (the underlying cause) - it hurts like hell (the symptoms) and you take some painkillers to stop the pain, while leaving your arm in a twisted wreck - or you can set up arm in a cast so it can heal.

[QUOTE=canadianwriterman]I've heard this comment before and have been searching the Web for some authoritative information on the "consequences of diasbling ipv6." I can't find any. However, when you Google "disable ipv6" it appears that almost everyone is doing it.[/quote] A bit of common sense will tell you that if you disable it it won't work. Not a good thing if you are are user that relies on IPv6.

So in conclusion, before you blindly disable IPv6, make sure you are aware of the facts, and choose whether to treat the symptoms, or the underlying cause appropriatly.

---

### Post by canadianwriterman on 2005-11-12
[QUOTE=Yagisan]
 Well, IPv6 flys on my home rig, and my business rigs, but I obviously don't use the same applications as you. You will need to be specific about the applications that you use.[/QUOTE]

When ipv6 is enabled, the following applications are extremely slow on their initial connection (and fast with ipv6 disabled):

Firefox
Opera
Epiphany
Synaptic
The "Add Applications" frontend of Synaptic
The gdesklet for weather
The "Weather Report" application addon for the panel

I cannot believe that all these applications (although some are using the same core code) are at fault.

[QUOTE=Yagisan]A bit of common sense will tell you that if you disable it it won't work. Not a good thing if you are are user that relies on IPv6.

So in conclusion, before you blindly disable IPv6, make sure you are aware of the facts, and choose whether to treat the symptoms, or the underlying cause appropriatly.[/QUOTE]

My post was in response to comments like "use caution when disabling ipv6" and "understand the consequences." Please don't dismiss me as not having any "common sense." I've spent a great deal of time searching (including [www.ipv6.org](www.ipv6.org) for the slightest scrap of information that would enlighten me on what these consequences might be... to no avail. 

I understand that ipv6 is a replacement standard that is intended to replace ipv4 and that it is taking time to phase in. Nowhere I have I seen any definitive information on the so-called consquences.

Let me assure you that with my machine, connected to my ISP and accessing the IP addresses that I access, ipv6 has had a negative impact. Also, I've experienced no problems by diasbling ipv6.

As for you rather dismissive comment: "...if you disable it it won't work. Not a good thing if you are are user that relies on IPv6," How am I to KNOW that I rely on ipv6. If you have that knowledge, please share it with us ignorant folks who are "blindly disabling ipv6" so that all the programs we rely on to connect to IP addresses function effectively. It would be greatly appreciated.

---

### Post by beemer on 2005-11-30
Just wanted to let you know:

I have a Linksys WUSB54G Wireless adapter that has refused to get an IP on boot from my router (it's running using V1 Windows XP Drivers via ndiswrapper).

I just put in the "bad_list" fix and rebooted and it got it's address!

Thanks!!!

---

### Post by andrius on 2005-11-30
[http://www.ubuntuforums.org/showpost.php?p=533983&postcount=27](http://www.ubuntuforums.org/showpost.php?p=533983&postcount=27)

---

### Post by viscount on 2005-12-14
[QUOTE=SlowJet]Sorry about the sloppy post.

#                               1, 2, 3 new lines
alias net-pf-10 ipv6 off       
alias net-pf-10 off
alias ivp6 off
#alias net-pf-10 ivp6           =========the original line
[/QUOTE]

I notice you have "ivp6" and "ipv6" ...is that a typo?
Which should it be, or is it both just as it appears.

---

### Post by akurashy on 2005-12-14
does this work in breezy? if it does damn im going to try it :D

---

### Post by Josef K. on 2005-12-15
[QUOTE=akurashy]does this work in breezy? if it does damn im going to try it :D[/QUOTE]

I've tried the bad_list trick and seems to work  :)

---

### Post by xtacocorex on 2005-12-15
bad_list file worked.

Thanks for the how-to.

---

### Post by viscount on 2005-12-26
I could be wrong, but I think perhaps if you have no apps that require
or use ipv6 then it gets shut off automatically.

The reason I say that is because this box is a relatively fresh install, and I haven't
messed around with the modules.d yet. However I have switched off ipv6 in Firefoxs
about:config and when I did `ip a | grep inet6` it shows nothing.

Also, my network is very responsive.

```

$ COUNTER=0
$ time while [ $COUNTER -lt 10 ]; do host www.google.com; let COUNTER=COUNTER+1; done
www.google.com is an alias for www.l.google.com.
www.l.google.com has address 66.102.7.104
www.l.google.com has address 66.102.7.147
www.l.google.com has address 66.102.7.99
www.google.com is an alias for www.l.google.com.
www.google.com is an alias for www.l.google.com.
www.google.com is an alias for www.l.google.com.
www.l.google.com has address 66.102.7.104
www.l.google.com has address 66.102.7.147
www.l.google.com has address 66.102.7.99
www.google.com is an alias for www.l.google.com.
www.google.com is an alias for www.l.google.com.
www.google.com is an alias for www.l.google.com.
www.l.google.com has address 66.102.7.147
www.l.google.com has address 66.102.7.99
www.l.google.com has address 66.102.7.104
www.google.com is an alias for www.l.google.com.
www.google.com is an alias for www.l.google.com.
www.google.com is an alias for www.l.google.com.
www.l.google.com has address 66.102.7.99
www.l.google.com has address 66.102.7.104
www.l.google.com has address 66.102.7.147
www.google.com is an alias for www.l.google.com.
www.google.com is an alias for www.l.google.com.
www.google.com is an alias for www.l.google.com.
www.l.google.com has address 66.102.7.99
www.l.google.com has address 66.102.7.104
www.l.google.com has address 66.102.7.147
www.google.com is an alias for www.l.google.com.
www.google.com is an alias for www.l.google.com.
www.google.com is an alias for www.l.google.com.
www.l.google.com has address 66.102.7.99
www.l.google.com has address 66.102.7.104
www.l.google.com has address 66.102.7.147
www.google.com is an alias for www.l.google.com.
www.google.com is an alias for www.l.google.com.
www.google.com is an alias for www.l.google.com.
www.l.google.com has address 66.102.7.104
www.l.google.com has address 66.102.7.147
www.l.google.com has address 66.102.7.99
www.google.com is an alias for www.l.google.com.
www.google.com is an alias for www.l.google.com.
www.google.com is an alias for www.l.google.com.
www.l.google.com has address 66.102.7.104
www.l.google.com has address 66.102.7.147
www.l.google.com has address 66.102.7.99
www.google.com is an alias for www.l.google.com.
www.google.com is an alias for www.l.google.com.
www.google.com is an alias for www.l.google.com.
www.l.google.com has address 66.102.7.147
www.l.google.com has address 66.102.7.99
www.l.google.com has address 66.102.7.104
www.google.com is an alias for www.l.google.com.
www.google.com is an alias for www.l.google.com.
www.google.com is an alias for www.l.google.com.
www.l.google.com has address 66.102.7.147
www.l.google.com has address 66.102.7.99
www.l.google.com has address 66.102.7.104
www.google.com is an alias for www.l.google.com.
www.google.com is an alias for www.l.google.com.

real    0m1.220s
user    0m0.027s
sys     0m0.028s

```

30 looksups and 30 resolves in 1.2seconds? Not bad. :)

---

### Post by Danny Boy on 2006-03-18
Can someone help me? I just did a fresh install of Breezy. I cannot create a bad_list file. 

Also when i try to open the aliases file it opens as read only, I tried doing the old windows trick to change permissions but it's says I'm not the owner. I'm the only account on the computer how can I not be the owner?

What do I do?

---

### Post by nalmeth on 2006-03-18
So from what I think I picked out of this, if ipv6 is affecting your connection, it would cause a 'significant' delay or time out, rather than a cummulative lagging of every connection? Or does it cause a low percentage of lag for every online operation you make? Sounds like I should just keep it on rather than disable.

---

### Post by dcstar on 2006-03-18
[QUOTE=Danny Boy]Can someone help me? I just did a fresh install of Breezy. I cannot create a bad_list file. 

Also when i try to open the aliases file it opens as read only, I tried doing the old windows trick to change permissions but it's says I'm not the owner. I'm the only account on the computer how can I not be the owner?

What do I do?[/QUOTE]
Use sudo

---

### Post by xshady87 on 2006-03-19
I'm a bit confused. Where exactly do I go about typing this? In the terminal? Because I tried it there, and after the second line it said "directory not found".

---

### Post by guysmiley on 2006-03-21
If you're having problems in Synaptic or Firefox, if you're a newbie like me, here's the process at it's most basic:

ipv6 is a protocol not handled by many routers.  It's new and will be needed someday (which means a long time from now (like years) you're gonna have to buy a new one.  In the meantime, config linux not to use it by:

1.  Open a Terminal Window
2.  Type sudo gedit /etc/modprobe.d/bad_list/
3.  In the gedit window, type: alias net-pf-10 off
4.  Save the file and reboot.

To make sure you no longer have ipv6 running, open a terminal window and type:
ip a | grep inet6

Many thanks to mhael for this process!

gs  :)

---

### Post by neoflight on 2006-03-26
[QUOTE=guysmiley]If you're having problems in Synaptic or Firefox, if you're a newbie like me, here's the process at it's most basic:

ipv6 is a protocol not handled by many routers.  It's new and will be needed someday (which means a long time from now (like years) you're gonna have to buy a new one.  In the meantime, config linux not to use it by:

1.  Open a Terminal Window
2.  Type sudo gedit /etc/modprobe.d/bad_list/
3.  In the gedit window, type: alias net-pf-10 off
4.  Save the file and reboot.

To make sure you no longer have ipv6 running, open a terminal window and type:
ip a | grep inet6

Many thanks to mhael for this process!

gs  :)[/QUOTE]


this is what i am getting before and after creating the file....

```
ip a | grep inet6
inet6 ::1/128 scope host
inet6 fe80::212:f0ff:fe24:202d/64 scope link

```
any clues..... ???

---

### Post by xyz on 2006-04-13
Hi 
neoflight,
I had to go into Firefox as well.Open a new tab and type "about:config". Then scroll down to "network.dns.disableIPv6"...if it reads "true", leave it. I f it reads "false", double-click on it to make it read "true".
Then try the test again: ip a | grep inet6

---

### Post by Ariam on 2006-04-13
1.  Open a Terminal Window
2.  Type sudo gedit /etc/modprobe.d/bad_list/
3.  In the gedit window, type: alias net-pf-10 off
4.  Save the file and reboot.


Thanks to mhael again, you made it very clear for a newbee like me to follow. 
Ariam.

---

### Post by gpeck157 on 2006-04-14
Yagisan, well said. I would add that ipv6 was considered necessary until the widespread use of NAT routing made it less so. Now, due to NAT routing, everyone in a household can have their own private ip behind the NAT router, which only requires one ip address from your ISP. Even some ISPs are now using NAT routing for their customers. This has taken a lot of the pressure off in needing immediate implimentation of ipv6. 

Glen

---

### Post by gymsmoke on 2006-04-14
So, maybe a solution would be during the install of Ubuntu, ask whether you want/need ipv6 enabled, and take the appropriate action...

Then there would only need to be a HOW TO on "enabling ipv6" when it is needed...








"I've gone out to find myself... If I'm not back in 10 minutes, come and get me"

---

### Post by Gulo gulo on 2006-04-16
[QUOTE=mhael]There's an easy way: instead of changing **aliases** file, create fie named **bad_list** in **/etc/modprobe.d** containing this line:
```
alias net-pf-10 off
```Now reboot and voila, no IPv6 on your system!

This method will work even if /etc/modprobe.d/aliases get replaced at some update.[/QUOTE]

Thanks a lot for your solution. just what a newbe like me needed. after a upgrade to the latest dapper my internet dident work at all,even not after trying to disable ipv6 in firefox. 
But now i am writing from my ubuntu box.

:-D

---

### Post by gpeck157 on 2006-04-17
[QUOTE=mhael]There's an easy way: instead of changing **aliases** file, create fie named **bad_list** in **/etc/modprobe.d** containing this line:
```
alias net-pf-10 off
```Now reboot and voila, no IPv6 on your system!

This method will work even if /etc/modprobe.d/aliases get replaced at some update.[/QUOTE]

Outstanding suggestion! I did this on both my Ubuntu boxes and it worked like a charm. I had actually done this in Windows a long time ago, but never thougt about it in Linux until this thread. Thank you all. Web pages are poppin'.

Glen

---

### Post by Danny Boy on 2006-04-17
It works well and definetly speeds up the 'net all around, but their still seems to be a delay. In windows when I go to a URL it loads instantly in Ubuntu it takes a second or two until looks for the server.

My sisters laptop uses a wireless connection and webpages load instantly with windows.

---

### Post by Cysman on 2006-04-19
[QUOTE=guysmiley]If you're having problems in Synaptic or Firefox, if you're a newbie like me, here's the process at it's most basic:

ipv6 is a protocol not handled by many routers.  It's new and will be needed someday (which means a long time from now (like years) you're gonna have to buy a new one.  In the meantime, config linux not to use it by:

1.  Open a Terminal Window
2.  Type sudo gedit /etc/modprobe.d/bad_list/
3.  In the gedit window, type: alias net-pf-10 off
4.  Save the file and reboot.

To make sure you no longer have ipv6 running, open a terminal window and type:
ip a | grep inet6

Many thanks to mhael for this process!

gs  :)[/QUOTE]

After searching through this post someone finally drew this thing out in crayon for those of us who really needed it.  Thanks a bunch!:)

---

### Post by horsey1901 on 2006-04-20
[QUOTE=akurashy]does this work in breezy? if it does damn im going to try it :D[/QUOTE]

I removed IPV6 and its now flies in breezy..

---

### Post by ramonhollands on 2006-05-07
I'm running dapper, it doesn't work for me. I tried both methods. ip a shows the system is still using ipv6. How is this possible? Maybe because it is using other the new NetworkManager?

---

### Post by Googler on 2006-05-08
wooow
thank you SlowJet it's realy amazing !!
firefox became 10 times faster :razz:

---

### Post by electroconvulsive on 2006-05-09
[QUOTE=mhael]No, all you need is to create /etc/modprobe.d/bad_list with specified line and reboot.

To check IPv6 state open terminal and execute:
```
ip a | grep inet6
```
If this command shows some lines - IPv6 is enabled. If output is empty - IPv6 disabled.[/QUOTE]

I have disabled ipv6 using the instructions in your post and I have also disabled via about:config in firefox. Still no joy with the internet. 

As a matter of intertest in my connection properties under support the subnet mask is still coming up as 255.255.255.255 not a valid subnet mask for a,b or c class networks in ipv4 does anyone know how to cure this?

---

### Post by electroconvulsive on 2006-05-09
[QUOTE=mhael]No, all you need is to create /etc/modprobe.d/bad_list with specified line and reboot.

To check IPv6 state open terminal and execute:
```
ip a | grep inet6
```
If this command shows some lines - IPv6 is enabled. If output is empty - IPv6 disabled.[/QUOTE]

I have disabled ipv6 using the instructions in your post and I have also disabled via about:config in firefox. Still no joy with the internet. 

As a matter of intrest in my connection properties under support the subnet mask is still coming up as 255.255.255.255 not a valid subnet mask for a,b or c class networks in ipv4 does anyone know how to cure this?

---

### Post by SilvioTO on 2006-06-05
in dapper these metods don't work, wen I type ip a | grep inet6 the terminal show the following lines:

    inet6 ::1/128 scope host
    inet6 fe80::2c0:26ff:fef4:83b7/64 scope link

---

### Post by phoenix_1983 on 2006-06-06
I've tried the above and i'm still getting IPV6 as enabled..

So far i have:

Disabled IPV6 in firefox
edited IPV6 out in aliases
done the bad_list trick
also commented out the IPV6 stuff in /etc/hosts

What is causing IPV6 to still be enabled!....  this is really getting frustrating because i can't access updates with IPV6 enabled... the connection times out.

---

### Post by edwing on 2006-06-06
If you're using Dapper Drake edit /etc/modprobe.d/aliases, comment out the existing alias net-pf-10 ipv6 and add alias net-pf-10 off, like so:

alias net-pf-10 off
# alias net-pf-10 ipv6

Reboot.

That worked for me.

---

### Post by reztho on 2006-06-08
In Dapper I got to disable ipv6 in this way: Make a file called 'blacklist-ipv6' in /etc/modprobe.d/ and inside the file put this text: blacklist ipv6

So the next time you boot, the ipv6 module won't be loaded (lsmod | grep ipv6 ; it's a better way to check ipv6 presence than 'ip a | grep inet6', I think, since the module manages the thing).

---

### Post by trash on 2006-06-08
[QUOTE=reztho]In Dapper I got to disable ipv6 in this way: Make a file called 'blacklist-ipv6' in /etc/modprobe.d/ and inside the file put this text: blacklist ipv6

So the next time you boot, the ipv6 module won't be loaded (lsmod | grep ipv6 ; it's a better way to check ipv6 presence than 'ip a | grep inet6', I think, since the module manages the thing).[/QUOTE]


Thanks reztho, of all the methods above yours is the only one that worked in Dapper

---

### Post by pstracha on 2006-06-09
Wow, I have 'high-speed' Internet again :D ... and I just thought my PC was getting old. This is a great tip, thank you SlowJet!

I got it working in Dapper in the same way reztho did but I just appended the following line to the blacklist file that already existed in /etc/modprobe.d/

```
# disable ipv6
blacklist ipv6
```

---

### Post by HeXonX on 2006-06-13
Reztho, YOU ROCK! After wasting about an hour...your tip did the trick.

[QUOTE=reztho]In Dapper I got to disable ipv6 in this way: Make a file called 'blacklist-ipv6' in /etc/modprobe.d/ and inside the file put this text: blacklist ipv6

So the next time you boot, the ipv6 module won't be loaded (lsmod | grep ipv6 ; it's a better way to check ipv6 presence than 'ip a | grep inet6', I think, since the module manages the thing).[/QUOTE]

---

### Post by msixp_k7 on 2006-06-18
Hay I Just turned off that junk!!!!!!! I have DSL now And it felt like dailup with a bad conection BUT NOW ITs goo to go.  THANKS FOR YOUR HELP!!!!!!!!!!!!!!!!!!!!!!

---

### Post by cookfromfrozen on 2006-06-19
Been having problems with slow Internet / DNS problems for a while and it made me go back to Win for a while.

Downloading 6.06 now and gonna give this a try. :D

---

### Post by gneeot on 2006-07-03
Is it going to help if I'm not using Internet on Linux server, but using it on other windows machines on my LAN?

---

### Post by dac0nv1ct on 2006-07-18
Being a total linux n00b and trying out ubuntu i was about to give up and go bk to windows but amazingly it works on my ubuntu desktop I finally got dsl and  managed to get my updates all 117 of them plus firefox works.:D 
Now i just have to work out how to disable it on my other box that I installed the lamp server cd on as that is still not getting any internet.](*,) 
Which? editor would I use in the server set up as it does not have gedit and vim asks for a £10 donation thanks.:-k

---

### Post by reztho on 2006-07-19
> **dac0nv1ct said:**
> Being a total linux n00b and trying out ubuntu i was about to give up and go bk to windows but amazingly it works on my ubuntu desktop I finally got dsl and  managed to get my updates all 117 of them plus firefox works.:D 
Now i just have to work out how to disable it on my other box that I installed the lamp server cd on as that is still not getting any internet.](*,) 
Which? editor would I use in the server set up as it does not have gedit and vim asks for a £10 donation thanks.:-k


Use nano. For vi or vim you need a manual to understand how they work.

Actually because it is only a line, you can do it easier without a text editor using a bash redirection: 
sudo echo "blacklist ipv6" > /etc/modprobe.d/blacklist-ipv6

---

### Post by Bossieman on 2006-07-19
Thanks! this worked like a charm! Thanks very muck. :p

---

### Post by paulmerchant on 2006-07-25
Thanks! This saved me.

To those who say we should not turn off ipv6, please note that it is a complete show stopper for many of us. My DSL router, an ActionTec GT704, hosed my network connection every time with ipv6 on. Strange stuff, too. I could often ping URLs great while Firefox and Synaptic connections would completely die. Basically, it is impossible for me to use Ubuntu right now without having the current ipv6 turned off. This also happened at a second location (my office) with  a completely different router setup. With all the other wireless and networking issues that someone like me has to deal with (a brand noob to Ubuntu), it's quite difficult to start out with this ipv6 issue on top of everything else. And it's kind off silly for people to tell us we can't turn it off.

That said, thanks again to those who helped me turn it off. I did all the methods above (the alias thing and bad_list and blacklist just to be sure I killed this horrible ipv6 thing).

Edit: I thought I'd mention that this is also my first post. Yeah!

---

### Post by Jhongy on 2006-07-26
I wonder if this is why I've been getting DNS timeouts whenever DNS is handled by DHCP. For the past couple of years - in WinXP and Linux, I've had to manually specify DNS servers - otherwise 90% of DNS requests would not resolve until I hit "refresh" several times over.

Can't wait to try it out!

---

### Post by rupesh on 2006-07-31
i have same problem, with dapper and after readind all stuff i tried following steps:-
 1) disabled ipv6 in mozilla
 2) changed /etc/modprobe.d/aliases
 3) creating badlist file.
 4) creating blacklist-ipv6 file.
 
 now i dont get any modules loaded by 
 ip a | grep inet6
     or 
 lsmod | grep ipv6

after all this i am able to use mozilla. but still unable to connect using synaptic or gaim etc..
 can anyone plzz help me for fixing this problem? 
 also plzz answer on following post:-
 [http://www.ubuntuforums.org/showthread.php?t=225734](http://www.ubuntuforums.org/showthread.php?t=225734)
 
 thanks and regards

---

### Post by TwistesdTexan on 2006-08-02
Just to let you know This thread is still hel-ping people. I just use it because my dsl had become as slow as dial-up also and is back to normal now. Thanks!!=D>
I also tried the other way sugested by typing in about:config in the address bar and typing in ipv6 in the filter and toggling it to false and received the same results. Both fixes worked for me. The last was the easiest.:-\"

---

### Post by H.E. Pennypacker on 2006-08-03
> **mhael said:**
> There's an easy way: instead of changing **aliases** file, create fie named **bad_list** in **/etc/modprobe.d** containing this line:
```
alias net-pf-10 off
```Now reboot and voila, no IPv6 on your system!

This method will work even if /etc/modprobe.d/aliases get replaced at some update.

After doing that, IPv6 will still show up if I do ip a | grep inet6.  This command should show whether IPv6 is enabled or not, and if something comes back, it means its still turned on.  That's what someone said in this thread.  Something's still being shown in the output.

---

### Post by Markus Valkeapaa on 2006-08-10
Thank you very much reztho! Another ubuntu/linux newbie here who was just about to go back to Windows. Especially 'lsmod' vs 'ip' was great info. Based on 'ip' I thought ipv6 was not  present, whereas using 'lsmod' it was listed. 

In reference to the previous ipv6 discussion on this thread, I also tested with couple of browsers. Firefox, Galeon, and Epiphany all used very long times for the "looking up..." part. Seems to me also that if there is a browser bug, Firefox is not the only one with it.

-Markus

---

### Post by ciscosurfer on 2006-08-10
@Yagisan
From one engineer to another, I completely agree 100% with every point you make.  Each one of your posts ([post 8]("http://ubuntuforums.org/showpost.php?p=478267&postcount=8"), [post 13]("http://ubuntuforums.org/showpost.php?p=483032&postcount=13"), [post 19]("http://ubuntuforums.org/showpost.php?p=485462&postcount=19")) are well thought out and describe the problem head-on.  Well done!

@gpeck157
Your points too [re: NAT]("http://ubuntuforums.org/showpost.php?p=920634&postcount=36") and the slow movement towards IPv6 are also key to understanding these issues.  Good job!

I don't have any need for IPv6 and so after going through this thread, and b/c I'm a Dapper user (Breezy users should use the methods mentioned towards the beginning of this thread...Dapper users should try the methods mentioned towards the end of this thread) I decided to use the following to speed things up (and yes, I do notice a change):

I go to Firefox (b/c this is the browser I use) and I type about:config and then enter **network.dns.disableIPv6 **or any variation of that string to bring up this specific preference.  I then make sure that the value says **true**.  Double click the line to enable/disable.  Enabled=true / Disabled=false ...  we want it to say **true**.  This will disable IPv6 dns lookups from within Firefox only--not your entire Ubuntu system.

To do it for the entire system, I create a file under **/etc/modprobe.d/** I name it anything I want (disable_ipv6, bad_ipv6, ipv6_noload, or anything else you want to name it...the key here is the line you put within the file *not* the file name.  This is b/c everything within **/etc/modprobe.d/** gets "sourced" at boot time or any other time you probe modprobe.d)  Another option is to simply add our special line to the already existing file under **/etc/modprobe.d/** called **blacklist**.  I choose the latter option because I don't see any reason to create a new file, but if you want to have a separate file for our 'special line,' that's totally fine, too.  

So, here we go:```
sudo gedit /etc/modprobe.d/blacklist
```Add the following **2** lines to your file (the comment line isn't necessary, but helps in describing the line below it and will aid you when you want to get rid of it, etc):```
# (this is a comment line; comment here however you want; i.e., disables ipv6
blacklist ipv6
```Save the file, and reboot.  After you reboot and are up again, go to a terminal and type in```
lsmod | grep ipv6
```If the terminal doesn't respond with anything after you hit enter, then everything above worked!  Some people like to use```
ip a | grep inet6
```Try them both to make sure ipv6 isn't loading.  The prior method works best because we're grep'ing our modules with lsmod, which makes sense b/c we are adding our 'special line' and/or file to **/etc/modprobe.d/** which is a folder that probes for module rules, etc.

Good Luck, and Happy Speed Surfing!

---

### Post by stanz on 2006-08-12
Hi All...
I don't know if this is repeating, but Thunderbird mail - has this in its 'about:config' also.

---

### Post by awelux on 2006-08-22
Hi, I believe a big part of the problem might be that sometimes the ipv6 loopback device is unreachable. Programs that access it will timeout causing the slow behavior.

Has anyone an idea how to add the default route to ipv6 again?

root@myhost:~# ip -6 route
fe80::/64 dev eth0  metric 256  expires 7948568sec mtu 1500 advmss 1440 hoplimit 4294967295
fe80::/64 dev eth1  metric 256  expires 7974725sec mtu 1500 advmss 1440 hoplimit 4294967295
ff00::/8 dev eth0  metric 256  expires 7948568sec mtu 1500 advmss 1440 hoplimit 4294967295
ff00::/8 dev eth1  metric 256  expires 7974725sec mtu 1500 advmss 1440 hoplimit 4294967295
unreachable default dev lo  proto none  metric -1  error -101 hoplimit 255

---

### Post by SeQual on 2006-09-02
Thanks, used this guide and solved a problem I had.

:KS

---

### Post by peter b on 2006-09-08
Hi to all!
Did anyone tryed ununtu 606 amd64 live? In my case it gives me a nice desktop but no autodetection of the NAT and no internet. Cannot log in the router or ping it. Any idea if ipv6 can be disabled in live install? Can this ipv6 implementation on ubuntu be the cause of my internet problems?

The other day a friend gave me a Knoppix linux on CD. Guess what world, after live boot it detected everything and I accessed the internet full blast dsl broadband -no mas no fuss! and ipv6 was enabled by default. I can log in the router and/or ping it.

Any leads and/or help appreciated.

Peter b

---

### Post by Tom Mann on 2006-09-08
Thanks, ipv6 doesn't like certain D-Link hardware, including my router :(
This little nugget solved the lot!

---

### Post by cookfromfrozen on 2006-09-08
Is there any way when disabling IPv6 through this guide to apply the changes without rebooting?

I've tried

```
sudo /etc/init.d/networking restart
```

and I've ifdown and ifup'd the interface but it seems the only way is to reboot.  Come on, this is Linux :)

---

### Post by Psquared on 2006-09-08
After fiddling with this for sometime, I finally did the Dapper thing and no more ipv6. Pages refresh faster in Firefox without any timeouts or having to hit stop and click again and again. This is a great help, but don't forget to reboot and use the Dapper instructions if you have 6.06.

---

### Post by hype on 2006-09-09
> **mhael said:**
> There's an easy way: instead of changing **aliases** file, create fie named **bad_list** in **/etc/modprobe.d** containing this line:
```
alias net-pf-10 off
```Now reboot and voila, no IPv6 on your system!

This method will work even if /etc/modprobe.d/aliases get replaced at some update.

Hi mhael,
i've just added ```
alias net-pf-10 off
``` in /etc/modprobe.d/bad_list .

 After reboot, i made a ip a | grep inet6 , but it still outputs:
```
~$ ip a | grep inet6
    inet6 ::1/128 scope host
    inet6 fe80::201:6cff:fe3d:6208/64 scope link
    inet6 fe80::250:56ff:fec0:8/64 scope link
    inet6 fe80::250:56ff:fec0:1/64 scope link

```

This means ipv6 Hasn't been disabled, right?

Did any one tested both methods? Is it a problem of "bad_list" not being loaded by modprobe or something?

EDIT: Modifying my "blacklist" in modprobe.d just did the trick !

---

### Post by peter b on 2006-09-10
hello to all

today I downloaded just for the fun of it Kubuntu for amd 64 -that's right, the one with K! and to make a long story short, on the same PC it booted live flawlessly, autodetected and configured RIGHT OFF THE BAT the router, the NIC and in no time I was surfing the net, sending and receiving e-mail AT FULL BROADBAND SPEED WITH ipv6 enabled.  So I'll leave it up to the readers to draw their own conclusions re ipv6 problems expressed on this thread.
peter b

---

### Post by zachofalltrades on 2006-09-13
with all due respect to the network engineers,

Telling people that they should deal with their problem by filing bug reports with various specific application developers is not a really useful solution for most end-users. It may be true that IP6 should not be a problem for most users, but clearly it is. End users don't really care whether this is the 'fault' of their ISP, their own network equipment, their oeprating system, or their specific internet application. How something 'should' work isn't really important to most users -- people really only care about the result (the symptom, not the underlying cause).

guysmiley 'wrote in crayons' the solution suggested by mhael: 
1. Open a Terminal Window
2. Type sudo gedit /etc/modprobe.d/bad_list/
3. In the gedit window, type: alias net-pf-10 off
4. Save the file and reboot.

For folks who just want to use their system rather than mess around with the internals. This is a silver bullet. It bypasses the need for the end user to tweak specific applications. It 'fixes' the problem at the system level. By creating a new file instead of editing one that already exists, they avoid messing something up, or losing their tweak by some other upgrade or automated installer. By the time most people actually need IP6, the misbehaving applications will probably be fixed, and then people can just delete this little file -- if they are even still using their current system.

BTW -- this solution 'fixed' FireFox and Evolution for me -- I was desperate until I found this thread.

---

### Post by cookfromfrozen on 2006-09-17
In my experience you need to do all three methods (the aliases file, the bad_list file AND the blacklist file) to fully disable IPv6.  I've tried just the bad_list trick or the blacklist trick on its own and I still get output from ip a | grep inet6.

If you get any output from that command then IPv6 is still enabled so you'll probably need to do all three "hacks" to finally turn it off.

Or...just buy a router that doesn't freak out with IPv6.

---

### Post by missmoondog on 2006-09-17
> **Yagisan said:**
> From the ubuntu-devel mailing list (culled from a variety of posts)
 Originally Posted by ubuntu-devel list
Having IPv6 be the cause of 'slow' connection is actually a common
misconception, reinforced in that disabling some IPv6 features may help
mitigate the problem, in most cases it is the result of bad network
configuration.

IPv6 itself does not in any way slow down your connection, problems will
arise however if you have a route out to the IPv6 internet but it is not
operational, as the browser will try to connect and it will take a while
to time-out, note this would also happen with a bad IPv4 internet
connection.

Another cause in the past has been bugs in programs (e.g. mozilla) that
do the wrong thing internally, most of the major problems here have been
fixed.

As above, these issues would *only* happen if the website you are trying
to connect to has an IPv6 address associated. Another cause can be
having an IPv6 name-server configured in resolv.conf or similar, in
which case the problem would arise if you were trying to connect to
*any* address.


Most people do not have a problem with having IPv6 enabled, it
simply is un-used when not in use.

If you are having problems, it is likely due to some kind of
misconfiguration, you would need to diagnose that.

In particular, the commands 'ip -6 route' may help, it will indicate if
you have any routes to the broader IPv6 world (look for '2000::/3' and
'default' routes). THis may be caused by an incorrect router on your
network, or by using tunneling software (such as tspc from
freenet6.net), or a number of other reasons.

In simpler terms: with a default Ubuntu install, if you're not using
IPv6, you shouldn't even know it's there. If you're experiencing
negative side effects, they're likely the result of a broken application
or incorrect configuration. Firefox, for instance, is a known culprit.

One thing you can try is, with IPv6 enabled, to launch a terminal, and
type 'host www.google.com'. If the command succeeds quickly, listing
Google's IPs, then you're not having general network connectivity
trouble, and you can start filing bug reports against whichever specific
applications are being slow.


My suggestion to all those with "slow" internet. Try the last paragraph especially, then start filling bug reports.

yep, couldn't agree more. ipv6 has nothing to do with your normal connection. just disabling it in your browser is sufficient.

---

### Post by Buelldozer on 2006-09-18
With all due respect to yagisan and missmoondog. In my opinion you ask too much.

Which do you suspect *most* users would rather do when faced with an IP based problem? 

1) Issue a single command to the operating system to disable a feature that they do not use or need but is causing major system slowdowns.

2) Spend hours troubleshooting networking hardware that may or may not be having problems with this 'newfangled' IP addressing scheme and then replacing said hardware (that costs money) IF they can track that as the source of their ills. If, or probably then, when they continue to have issues spend time documenting which applications are having problems and filing bug reports using 20 different tracking systems, each with it's own logon and password set and different operating scheme. Then they get told "It's a problem with your hardware or distro" by some cranky developer.

What you see in this thread is "most" users. The harcore techs are filing bug reports and chasing hardware. For the non-technical user it is perfectly acceptable to JUST TURN OFF IPV6!

Remeber, most users couldn't figure out IPV*4* if they had a CCIE right there helping them, you can forget IPV6. (K)Ubuntu puts itself out there as a distribution for new Linux users and you can't, and shouldn't, expect them to spend hours and dollars sorting out crazy routing issues.

Perhaps those issues are the fault of their hardware, perhaps they are the fault of their software, but either way they do not have the technical knowledge or skill to solve the problem on their own.

These users post to these forums for help from other, and hopefully more knowledgeable, users. They don't post here to be told that they need to spend hours and dollars chasing ghosts in the hardware and glitches in the applications.

Again, in my opinion, unless you're willing to handhold them through testing hardware and filing bug reports with all of their software vendors you should simply tell them to turn off the source of their problems.

With all due respect, please remember that you are working, mostly, with people that have little experience in network and application troubleshooting.;)

---

### Post by Ted_Smith on 2006-09-20
> 
In Dapper I got to disable ipv6 in this way: Make a file called 'blacklist-ipv6' in /etc/modprobe.d/ and inside the file put this text: blacklist ipv6

So the next time you boot, the ipv6 module won't be loaded (lsmod | grep ipv6 ; it's a better way to check ipv6 presence than 'ip a | grep inet6', I think, since the module manages the thing).


Was the only one out of the three methods that worked for me. Thanks! The other two made no difference in my case. 

And yes, FF does seem much faster! 

Ted

---

### Post by bokibre on 2006-10-04
> **rupesh said:**
> i have same problem, with dapper and after readind all stuff i tried following steps:-
 1) disabled ipv6 in mozilla
 2) changed /etc/modprobe.d/aliases
 3) creating badlist file.
 4) creating blacklist-ipv6 file.
 
 now i dont get any modules loaded by 
 ip a | grep inet6
     or 
 lsmod | grep ipv6

after all this i am able to use mozilla. but still unable to connect using synaptic or gaim etc..
 can anyone plzz help me for fixing this problem? 
 also plzz answer on following post:-
 [http://www.ubuntuforums.org/showthread.php?t=225734](http://www.ubuntuforums.org/showthread.php?t=225734)
 
 thanks and regards

I have the same problem firefox is working just fine but synaptic won't reload nor update is working, I can't download anything of things are listed!!! What's with that?!?!?! IPV6 again or samething completely different?!?!?!?

HEEELLLLPPP!!!

oh and thanks for this that is working!

---

### Post by wilberfan on 2006-10-20
Holy crap...

*HUGE* difference!   The only thing that worked for me (Dapper), was editing the aliases file. 

:mrgreen:

---

### Post by ign on 2006-10-26
> **zachofalltrades said:**
>  
1. Open a Terminal Window
2. Type sudo gedit /etc/modprobe.d/bad_list/
3. In the gedit window, type: alias net-pf-10 off
4. Save the file and reboot.

This saved my life, thank you!!!
i run Dapper, Firefox was painfully slow, but this has made an amazing change  in the speed and response.

---

### Post by redjediuk on 2006-10-28
> **Tom Mann said:**
> Thanks, ipv6 doesn't like certain D-Link hardware, including my router :(
This little nugget solved the lot!

Hi,

I made this change to Dapper...

"1. Open a Terminal Window
2. Type sudo gedit /etc/modprobe.d/bad_list/
3. In the gedit window, type: alias net-pf-10 off
4. Save the file and reboot."

...and all was fine and I could resolve DNS with Firefox etc.

**However..**

I've just installed Edgy Eft and completed the same fix and it doesn't work. I checked the Networking and the Link is fixed to the IPV6 settings and not the IPV4. 

**How can I turn off / remove IPV6 from Edgy Eft?**

Many thanks

Jedi

---

### Post by handy on 2006-10-28
> **redjediuk said:**
> Hi,

I made this change to Dapper...

"1. Open a Terminal Window
2. Type sudo gedit /etc/modprobe.d/bad_list/
3. In the gedit window, type: alias net-pf-10 off
4. Save the file and reboot."

...and all was fine and I could resolve DNS with Firefox etc.

**However..**

I've just installed Edgy Eft and completed the same fix and it doesn't work. I checked the Networking and the Link is fixed to the IPV6 settings and not the IPV4. 

**How can I turn off / remove IPV6 from Edgy Eft?**

Many thanks

Jedi

I have to do it in Firefox or I can't even browse the web! 

It's in the middle of [***_this short How-To_***]("http://ubuntuforums.org/showthread.php?t=282034").

I hope it works for you too? :)

***[Edit:]*** I just had a quick look at the last 3 or 4 pages, the **about:config** thing for **Firefox** is in there already.

---

### Post by phormion on 2006-10-28
For those who want to look a bit deeper into the problem, here's document that's 'a bit' more informative: 

[http://v6fix.net/docs/wide-draft-v6fix.en](http://v6fix.net/docs/wide-draft-v6fix.en)

What this document implies is that most problems are caused by two things: 

a) apps which perform AAAA queries (for IPv6 addresses) even if IPv6 connectivity is not available
b) inappropriate handling of dual-stack setups in operating systems (like the 'on link assumption'); 

So, some DNS AAAA lookups that used to fail now succeed, as people get IPv6 connectivity, but sometimes it's not a good idea to use those addresses. The second thing is - the problem is related both to bugs in applications and operating systems (the document implies that at least the 'on link assumption' was fixed in kernel 2.6.9, but that's one of the problems). 

What's in a way disturbing is that after reading that document it's obvious the guy who posted that message on the ubuntu-devel mailing list didn't know too well what he was talking about. Suggesting 'host www.google.com' as a way to diagnose connectivity is hilarious - this only checks your DNS resolution, nothing more.

---

### Post by compwiz18 on 2006-10-29
adding ipv6 to the modprobe blacklist did it for me

so simply add ipv6 to the end of /etc/modprobe.d/blacklist, and that takes care of it.

---

### Post by redjediuk on 2006-10-29
> **compwiz18 said:**
> adding ipv6 to the modprobe blacklist did it for me

so simply add ipv6 to the end of /etc/modprobe.d/blacklist, and that takes care of it.

Apologies but I'm a complete newbie to Linux so please could you show me the syntax of the file so I can replicate it.

Many thanks

Jedi

---

### Post by compwiz18 on 2006-10-30
> **redjediuk said:**
> Apologies but I'm a complete newbie to Linux so please could you show me the syntax of the file so I can replicate it.

Many thanks

Jedi
The easy way is to just run this command:

```
sudo echo "ipv6" >> /etc/modprobe.d/blacklist
```

that should fix it up.

---

### Post by ddtrust on 2006-11-03
> **reztho said:**
> In Dapper I got to disable ipv6 in this way: Make a file called 'blacklist-ipv6' in /etc/modprobe.d/ and inside the file put this text: blacklist ipv6

So the next time you boot, the ipv6 module won't be loaded (lsmod | grep ipv6 ; it's a better way to check ipv6 presence than 'ip a | grep inet6', I think, since the module manages the thing).

Thanks for this. I think that's the way to go with 6.06 Dapper. At least it worked for me. And if you ever want to enable ipv6 again, all you have to do is to delete the file (sudo rm /etc/modprobe.d/blacklist-ipv6) and reboot to make it work again. Am I right? :D

---

### Post by reztho on 2006-11-03
yes, you are right :)

---

### Post by ruibernardo on 2006-11-08
> **compwiz18 said:**
> The easy way is to just run this command:

```
sudo echo "ipv6" >> /etc/modprobe.d/blacklist
```that should fix it up.

When I tried it, it didn't worked. After looking to the file, I saw why not: It must be **blacklist ipv6**. What a simple and effective way do it!!

sudo echo "**blacklist** ipv6" >> /etc/modprobe.d/blacklist

Worked just fine on 6.10 Edgy! Thanks :)

---

### Post by superba on 2006-11-16
Hi,

Okay guys, I seem to be having the same problem.  However, modding modprobe.d to turn off ipv6 didn't do it.  Adding "bad_list" with alias net-pf-10 off didn't do it.  I was suspicious of adding "bad_list" with all those blacklist files in there anyway.  

I know that my small network does not depend on ipv6 for anything.  However, my old Netgear RP614v1 chokes on it.  I didn't know that Firefox couldn't handle ipv6, though. 

My system, the one I load 'nix stuff on worked fine with Xandros, various and sundry versions of Windows installed, Mandrake, etc. I even had a working installation of Ubuntu until the latest automatic, with consent, update of Ubuntu.  I'm running v6.06, I think, daffy duck.  

How can I roll back the latest update?  My system works fine other than not being able to get to the network.  Pinging loopback works;  however, pinging the host ip and the router ip fail with network connection not found.  Yes, it's plugged in.

This may need to be moved to another forum or thread.  Just let me know where to find it if you do.

Thanks,

Cheers!

---

### Post by Ralesk on 2006-11-22
Excellent posts, and the techy guys are correct about IPv6 itself

But it&#8217;s a very good point that Ubuntu is a users&#8217; distro, not a &#8220;techy&#8221; one, and it shouldn&#8217;t expect people to know just what on Earth IPv6 is.

Obviously the apps are at fault.  Why do they look up via IPv6 first if it&#8217;s rare?  Geographically it's pretty much restricted to the Far-East and some LANs at this time; the vast majority of people (even taking into account the amount of people living in the Far-East) does have no use for IPv6 yet.  And it&#8217;s a good question too, why there are IPv6 DNS lookups and stuff even if there&#8217;s no IPv6 connection available &#8212; and why there isn&#8217;t a proper way to setup IPv6 anyway (other than hacking around somewhere in /etc&#8230;)

So yeah, it&#8217;s an issue that should be fixed for the sake of the users, even though IPv6 is Good Stuff&#8482;.

One thing that hasn&#8217;t been answered yet: how to apply modprobe.d settings without rebooting? :)

---

### Post by nabilmalik on 2006-12-16
As an answer to the question of why we need ipv6:
we need ipv6 becasue the world is running low on ipv4 addresses. The devices with ip addresses are increasing and the ipv4 will soon be all taken. Ipv6 was designed for future needs and has a large enough address space that cannot ever be completely reserved (practically) by the world.. 

search google for more information on ipv6.. Good luck

-Nabil,

---

### Post by CowzRule on 2006-12-28
Methods that worked for me
> Open a Terminal Window and paste```
sudo gedit /etc/modprobe.d/bad_list
```In that file paste```
alias net-pf-10 off
```Save the file, then reboot.
> Open a Terminal Window and paste```
sudo gedit /etc/modprobe.d/blacklist-ipv6
```In that file paste```
blacklist ipv6
```Save the file, then reboot.
> To check IPv6 state open terminal and paste```
ip a | grep inet6
```If this command shows some lines - IPv6 is enabled. If output is empty - IPv6 disabled.

---

### Post by Yink on 2006-12-29
I'd just like to say thanks. My firefox was taking its time to look up web address's. I did the firefox method typed in about:config and looked for 'network.dns.disableIPv6' doubled clicked it to change the value to true and firefox loads pages up 10x faster. I'm on dapper btw.

---

### Post by Somenoob on 2006-12-29
Opera is now much faster, thanks for the info.

---

### Post by bscook on 2007-01-03
i tried all of the methods listed above (change /etc/modprobe.d/aliases, add /etc/modprobe.d/bad_list, and change firefox directly).  changes to the aliases file would render my network unusable.  same if i did the bad_list change.  so obviously my system needs ipv6 for something, but my old dlink di-524 doesn't support it, so it must be something internal to dapper itself (wild-assed guess).

changing the about:config in both firefox and thunderbird improved performance of both 10-fold.  not only are they faster, but i now have access to some sites that previously only gave me intermittent access at best (e.g. dev.mysql.com)

sure some of the techies may think ipv6 is the bees' knees, but if it negatively affects real-world performance then what's it worth?  for an average joe user like me, it's more trouble than it's worth...  in fact i'd have to say that much of my ubuntu experience over the past 6 months is like that.  there are a lot of really nice features that are far superior to windows which i really like (especially not crashing every day), but the learning curve, the useability, and the frustration involved in getting even the simplest things to work has left a sour taste in my mouth.  if i had to do it all over again, i would have stayed with xp.  on the other hand, after 6 months i've at least got a system working reliably the way i want it to work (mostly).

---

### Post by xyz on 2007-01-04
> **bscook said:**
> i tried all of the methods listed above (change /etc/modprobe.d/aliases, add /etc/modprobe.d/bad_list, and change firefox directly).  changes to the aliases file would render my network unusable.  same if i did the bad_list change.  so obviously my system needs ipv6 for something, but my old dlink di-524 doesn't support it, so it must be something internal to dapper itself (wild-assed guess).

changing the about:config in both firefox and thunderbird improved performance of both 10-fold.  not only are they faster, but i now have access to some sites that previously only gave me intermittent access at best (e.g. dev.mysql.com)

sure some of the techies may think ipv6 is the bees' knees, but if it negatively affects real-world performance then what's it worth?  for an average joe user like me, it's more trouble than it's worth...  in fact i'd have to say that much of my ubuntu experience over the past 6 months is like that.  there are a lot of really nice features that are far superior to windows which i really like (especially not crashing every day), but the learning curve, the useability, and the frustration involved in getting even the simplest things to work has left a sour taste in my mouth.  if i had to do it all over again, i would have stayed with xp.  on the other hand, after 6 months i've at least got a system working reliably the way i want it to work (mostly).
Off thread topic but I'd suggest you spend time getting your OS the way you want it, back it up and restore it when something goes wrong with your system.

---

### Post by bscook on 2007-01-04
i do make backups regularly.  i have yet to figure out how to get my OS "the way I want it," despite pouring hundreds of hours trying to figure it out.  Instead I have settled for getting it mostly functional with regular backups and a harried frenzy whenever something seemingly straightforward gets in the way.  For example, it took me (brand new to linux) a little under a week to figure out how to even make and restore a backup.  still not even sure i've got the whole "dereference vs no-dereference" thing sorted out ... and you think it's even documented?  yes there are exhaustive, cryptic, and circular references to lots of stuff in the man entries pages... mostly useless unless you already understand the jargon.  
anyway, you're right it's off-topic and i guess i'm just venting.
cheers

---

### Post by daverave999 on 2007-01-05
Disabling IPv6 has just done wonders to Azureus for me. I struggled to connect to any peers, each connection seemed to time out and I'd only manage a trickle from them with EVERY torrent I tried (easily 50 or so, all well seeded). I added 'blacklist ipv6' into /etc/modprobe.d/blacklist and rebooted. [Running Edgy]

Instantly I could see the difference. I am now saturating my available bandwidth. 8) 

Firefox seems to have become much snappier too. I'm hoping this may also have sorted my MSN troubles as messages were being dropped all the time in any client I used. Here's hoping. I assume this all more than pure coincidence!

Thanks!

---

### Post by Delta Dude on 2007-01-09
I just wanted to say thanks for all the good info. regarding the IPv6 slow down issue. I got version 6.06 LTS running fast by changing the IPv6 line in the "aliases" file. Previous methods didn't seem to work.

There is also an interesting article about IPv6 on the MS site at - 

[http://www.microsoft.com/whdc/device/network/IPv6_IGD.mspx](http://www.microsoft.com/whdc/device/network/IPv6_IGD.mspx)

Does anyone know of an equivilant Linux article in this same area? In my view, the U.S. needs to get to IPv6 ASAP. The Telco crap where they want you to use DHCP and then lease you an IP address for 15 minutes to a day and then it's gone is stupid. I already have several internal devices where I'm at that I would like to have static IP addresses for so they can be reached easily and directly from the Internet. The Telcos where I'm at either don't offer them or want big bucks for them. 2 to the 128th power, the last time I calculated, equates to approx. 6.2 times 10 to the 25 power for every sq. ft. on the planet.
I guess if you make everyone think the supply is limited, you can charge more. 

Thanks Again :-)

---

### Post by porco.rosso on 2007-01-20
Ok guys, i've followed all your instruction an modified IPv6 lines in modprobe, but still the command

ip a | grep inet6

returns me some output, sign that IPv6 is still enabled.

Then, what can i do now?

---

### Post by runcivalle on 2007-01-20
I just started using Linux  (Ubuntu 6.10)and I couldn't get any app to connect to the Internet. Disabling ipv6 using  "blacklist ipv6" as described on this thread worked for Firefox but not for Synaptic. But then I followed the instructions on [http://ubuntuforums.org/showthread.php?t=282034]("http://ubuntuforums.org/showthread.php?t=282034") using that OpenDNS service, and everything seemed to work fine. Now I just re-enabled ipv6 everywhere and everything still works! So maybe, as some posters have said, the problem is not in ipv6 per se. For me at least, it seemed to reside on the DNS service I was using.

---

### Post by pikachu01 on 2007-01-21
> **compwiz18 said:**
> The easy way is to just run this command:

```
sudo echo "ipv6" >> /etc/modprobe.d/blacklist
```

that should fix it up.

If you get errors doing this, you should

sudo gedit /etc/modprobe.d/blacklist
then insert this line:

blacklist ipv6

This works for me in 6.10 Edgy

---

### Post by bear54 on 2007-01-30
I seem to be having a problem trying to speed-up Firefox. the following is what I have tried so far with the result. Have I done this correctly? Any help is greatly appreciated.
Eric
[B]root@mycompaq:/home/eric# /etc/modprobe.d/bad_list alias net-pf-10 off
bash: /etc/modprobe.d/bad_list: is a directory
root@mycompaq:/home/eric#
root@mycompaq:/home/eric# cd /etc/modprobe.d/bad_list
root@mycompaq:/etc/modprobe.d/bad_list# alias net-pf-10 off
bash: alias: net-pf-10: not found
bash: alias: off: not found
root@mycompaq:/etc/modprobe.d/bad_list# ip a | grep inet6
    inet6 ::1/128 scope host
    inet6 fe80::250:fcff:feb8:6bc5/64 scope link
root@mycompaq:/etc/modprobe.d/bad_list#[/B]

---

### Post by dbott67 on 2007-01-31
**_To disable IPv6 in Firefox_**

1. Type **about:config** in the address bar
2. Enter **network.dns.disableIPv6 **
3. Change the value to **true**.  Double click the line to enable/disable.  Enabled=true / Disabled=false.  This will disable IPv6 dns lookups from within Firefox only--not your entire Ubuntu system.

**_To do it for the entire system:_**

***Keep in mind that there are a number of ways to accomplish this.***

1. Verify that the IPv6 module is loaded.  From a terminal type:
```
dbott@thedrake:~$ lsmod | grep ipv6
ipv6                  265856  10
```

2. From a terminal type:
```
sudo echo "blacklist ipv6" > /etc/modprobe.d/blacklist-ipv6
```

3. Restart

4. Verify that the IPv6 module is not loaded.  From a terminal type:
```
dbott@thedrake:~$ lsmod | grep ipv6
dbott@thedrake:~$
```

This is just a compilation of posts from this thread.

-Dave

---

### Post by bear54 on 2007-01-31
Wow success!! This old Compaq Laptop is much faster surfing the internet now! Thank you all for your help. It's got to be tough dealing with nubes! hehe Keep-up the fantastic work.
  Eric

---

### Post by andyni on 2007-03-28
One more noob-type question, if we're diabling IPv6 to improve performance and avoid loading stuff we don't use, why don't be disable atm, appletalk and the rest of the protocols we'll never use while we're doing this?

---

### Post by bve on 2007-03-29
> **bscook said:**
> i do make backups regularly.  i have yet to figure out how to get my OS "the way I want it," despite pouring hundreds of hours trying to figure it out.  Instead I have settled for getting it mostly functional with regular backups and a harried frenzy whenever something seemingly straightforward gets in the way.  For example, it took me (brand new to linux) a little under a week to figure out how to even make and restore a backup.  still not even sure i've got the whole "dereference vs no-dereference" thing sorted out ... and you think it's even documented?  yes there are exhaustive, cryptic, and circular references to lots of stuff in the man entries pages... mostly useless unless you already understand the jargon.  
anyway, you're right it's off-topic and i guess i'm just venting.
cheers

With all due respect I rather doubt you were a Windows expert after using it for a week....

Yes you are off-topic, and venting which is fine, however please do try to remember your early experiences with Windows before you are critical of Linux.

Did you know how to backup anything on Windows in your first week on it? I suspect not, you will find extensive help and support in the forums here with the right questions and approach.

Jargon is not unique to Linux, nor computers. Patience and time will pay off, as they do when attempting to learn anything new.

---

### Post by imaginate on 2007-04-20
Simply a thanks to those who posted this fix.  Nice to see my response times back to where they should be.:popcorn: :popcorn:

---

### Post by Xylaquin on 2007-05-08
I seem to have disabled IPV6, the two test in terminal show no line below them. Firefox no longer needs to have it's IPV6 option set to true, and it runs in both modes.

But other programs *still* seem to not do anything. Gaim (or Pidgin as it's now called) doesn't log me in :(

---

### Post by wpshooter on 2007-05-10
> **mhael said:**
> There's an easy way: instead of changing **aliases** file, create fie named **bad_list** in **/etc/modprobe.d** containing this line:
```
alias net-pf-10 off
```Now reboot and voila, no IPv6 on your system!

This method will work even if /etc/modprobe.d/aliases get replaced at some update.

This did **NOT** work.

Should I try the method described in the earlier post on page 1 ?

Thanks.

---

### Post by wilberfan on 2007-05-10
(This won't be helpful--but I just wanted to chime-in and say that the 'bad-list' method has NEVER worked for me--going back to Dapper...!)

---

### Post by DoktorSeven on 2007-05-10
All these methods!  Sheesh.  I've always found one method to be the most reliable:

**gksudo gedit /etc/modprobe.d/aliases**

Change

**alias net-pf-10 ipv6**
to
**alias net-pf-10 off**

Reboot.

Validate with
** lsmod | grep v6**
Should return nothing.

Why reboot?  Because it's the easiest way to do it.  It's possible to simply rmmod ipv6 but to do so you need to remove everything that has to do with networking, which means shutting down X, all services, removing your network card modules, etc, etc.  It's *much* easier to just reboot.

Why remove ipv6?  Really, almost no one that runs a desktop system is even going to come in contact with ipv6 anytime soon, and until we get to the point where every device is ready for ipv6 (hint: we're not even close), it's best to just disable the thing.  It'd really probably be better for Ubuntu to disable ipv6 **by default** and have people who really need it (the *vast* minority) enable it.

---

### Post by wfwoo on 2007-05-10
> **DoktorSeven said:**
> 
**gksudo gedit /etc/modprobe.d/aliases**

Change

**alias net-pf-10 ipv6**
to
**alias net-pf-10 off**

Reboot.

Validate with
** lsmod | grep v6**
Should return nothing.

Thanks, Doktor. It is really easy.

---

### Post by wpshooter on 2007-05-11
Thanks, that works much better.

---

### Post by pietsnot on 2007-06-12
> **mhael said:**
> No, all you need is to create /etc/modprobe.d/bad_list with specified line and reboot.

To check IPv6 state open terminal and execute:
```
ip a | grep inet6
```
If this command shows some lines - IPv6 is enabled. If output is empty - IPv6 disabled.
or just do:   lsmod | grep ipv6

---

### Post by NaSiO6 on 2007-10-19
hi!

well disabling ipv6 did solve my problem to an extent.
but when i do type in 'host [www.google.com](www.google.com)' i get this message at times(2 out of 5 attempts were succesful)
host [www.google.com](www.google.com)
;; Warning: Message parser reports malformed message packet.
;; connection timed out; no servers could be reached

is this normal?

---

### Post by dyoung on 2007-11-25
ok i am a total newbe to ubuntu how do you create this file ? can you give me clear step by step instructions. Please , thank you

---

### Post by aubreyisland on 2007-12-03
> **DoktorSeven said:**
> All these methods!  Sheesh.  I've always found one method to be the most reliable:

**gksudo gedit /etc/modprobe.d/aliases**

Change

**alias net-pf-10 ipv6**
to
**alias net-pf-10 off**

...

**I did this on Gusty 7.10 on an Acer 5050 and internet seems faster, and yes Ubuntu should disable this by default!**

---

### Post by jeffspen on 2008-01-01
Hi

I am unable to connect to any secure sites - ebay etc that use the "https://" thing.
Like others in this forum my problem is not browser specific - have tried loads!
i have tried everything in this thread and am sure I have ipv6 turned off.
But it still does not help me. My problem here isn't the slow connection speed.

I connect to the internet using a LAN router modem (usual ip address 192.168.0.0 my ubuntu machine is 192.168.0.1 etc) and have set everything to direct connection rather than any manual proxy situation.

I am going a bit mad here. Can anyone help??

---

### Post by ~LoKe on 2008-01-02
You should start a thread in general help.  That has nothing to do with ipv6.

---

### Post by jeffspen on 2008-01-02
Well i nearly did that but a thread on exactly my problem refers to this thread as a solution.

---

### Post by jeffspen on 2008-01-02
although now i have discovered the factory settings on my new router were wrong and the cause of my problem. Ubuntu is as blameless as I wanted it to be! Thanks anyway,

---

### Post by Zaopunk on 2008-01-18
Wow!!!! I Followed The First Page Of Instructions And She Scoots Now!
Thank You!

---

### Post by zer000 on 2008-01-28
hi, i'm running Kubuntu 7.10. 

since a few days i installed a (cheap) new router on my network and suddenly my internet has gone very slow/intermittent. 

a few sites work normally, but a lot of them (google and yahoo, among others) get stuck in the "looking up hostname.." phase. when i wait for those to time out and press reload, they usually do load immediately. so, i guess the problem has something to do with the DNS?

so i thought maybe it's the IPv6 thing, because this is a cheap sweex router that might not support it (?), while before my flatmate's computer running winXP performed the role of routing the internet between us.

when i try the solutions mentioned in this thread either they do not disable IPv6 (according to the [COLOR="DarkGreen"]ip a | grep inet6[/COLOR] command, this happens with making changes to the aliases file) or they do disable IPv6 (when i made a bad_list file, or update the blacklist file) but my browsers (both Opera and Firefox) will not connect to any server at all anymore.
the strange thing in the last case is that Pidgin still connects just fine to MSN, ICQ and IRC.

also, i disabled IPv6 for Firefox in the [COLOR="#006400"]about:config[/COLOR] screen, but this didn't change any behaviour at all (for better or for worse). does that mean i might be looking completely in the wrong direction (disabling IPv6) for solving my problem here?

i am kind of in the dark as to what is going on right now, does anybody have any ideas?

---

### Post by zer000 on 2008-01-29
just wanted to say, i think i fixed it for now by disabling DHCP and entering the DNS servers (that were listed in my router's config page) manually into the KNetworkManager config screen.

it doesn't really feel like the most optimal solution, but it seems to to do the trick for now.

---

### Post by juky on 2008-03-11
Hi all,

of all things written in this post, all I did was modifying /etc/modprobe.d/blacklist file by adding the following:

```

#blacklist ipv6
blacklist ipv6

```

Nothing outputs when entering ```
ip a | grep inet6
``` command, means ipv6 disabled!

Note that I am Gutsy Gibbon user, so I do not know how it will work in other versions.

Cheers,
juky

---

### Post by Kerry_W on 2008-03-12
> **DoktorSeven said:**
> All these methods!  Sheesh.  I've always found one method to be the most reliable:

**gksudo gedit /etc/modprobe.d/aliases**

Change

**alias net-pf-10 ipv6**
to
**alias net-pf-10 off**

Reboot


This was quick and easy and worked perfectly. thanks DoktorSeven.

Kerry

---

### Post by johny42 on 2008-03-15
> **canadianwriterman said:**
> However, when you Google "disable ipv6" it appears that almost everyone is doing it.

Try Googling "enable ipv6".

---

### Post by wpshooter on 2008-03-30
> **juky said:**
> Hi all,

of all things written in this post, all I did was modifying /etc/modprobe.d/blacklist file by adding the following:

```

#blacklist ipv6
blacklist ipv6

```

Nothing outputs when entering ```
ip a | grep inet6
``` command, means ipv6 disabled!

Note that I am Gutsy Gibbon user, so I do not know how it will work in other versions.

Cheers,
juky

I wish someone could condense all of the information in this thread down to just the info given in this particular post and place it somewhere in an obvious point on this forum so you did not have to read thru 15 pages of messages to get to a correct answer.

Thanks.

---

### Post by gfk on 2008-06-28
I just did this and it has vastly improve my Internet performance and now my system feels faster.

I first wanted to keep it for compatibly reasons but preferred to improve my Internet performance.

Having read some articles about ipv6 I found out that Windows XP doesn't support ipv6.  However can do through some DNS resolve, not sure as I'm not to competent about networks.

I also found that my ISP doesn't even support ipv6 also.  To confirm I tried to visit [http://ipv6.google.com/]("http://ipv6.google.com/") before I disabled ipv6, which I could not access.

---

### Post by awahid2020 on 2008-07-09
> **reztho said:**
> In Dapper I got to disable ipv6 in this way: Make a file called 'blacklist-ipv6' in /etc/modprobe.d/ and inside the file put this text: blacklist ipv6

So the next time you boot, the ipv6 module won't be loaded (lsmod | grep ipv6 ; it's a better way to check ipv6 presence than 'ip a | grep inet6', I think, since the module manages the thing).


Yeah, thats the best way, managed to disable ip6, I used all tricks, but ony this one worked

---

### Post by gfk on 2008-07-20
I am mistaken about xp not being ipv6 supported.  I just read this [Wired article]("http://blog.wired.com/27bstroke6/2008/07/the-ghost-in-yo.html") about ipv6, which contradicts what I previously thought.

The articles describes a possible secruity hole with some firewalls not being ipv6 compatible and are unable to block access.

---

### Post by 4lc0h0l1c on 2008-07-26
Hi all,
confirming the above fixes worked for me.  Firefox & Opera were extremely slow under Ubuntu Hardy 8.04.  I've been a steady Opera user for a few years, and after I switched from Windows to Ubuntu the browser speeds were Konqueror -> Firefox -> Opera.  +1 to these solutions.  I don't know which one in particular did it, but I followed these steps: 

I disabled ipv6 in Firefox: type "about:config" (without the quotes) into the location bar, search for "ipv6" in the filter, and you should come up with "network.dns.disableIPv6" under "Preference Name".  Set this value to "true" (double-click or something).

I did not find a way to disable IPv6 in Opera (although I know it does have an about:config page) but it seems to be running fine anyway after the steps below.

> 
Methods that worked for me
Quote:Open a Terminal Window and paste
Code:
sudo gedit /etc/modprobe.d/bad_list
In that file paste
Code:
alias net-pf-10 off
Save the file, then reboot. 

Quote:Open a Terminal Window and paste
Code:
sudo gedit /etc/modprobe.d/blacklist-ipv6
In that file paste
Code:
blacklist ipv6
Save the file, then reboot. 

Quote:To check IPv6 state open terminal and paste
Code:
ip a | grep inet6
If this command shows some lines - IPv6 is enabled. If output is empty - IPv6 disabled.


actually I did not make a specific blacklist-ipv6 file.  I did

sudo nano /etc/modprobe.d/blacklist

and added "blacklist ipv6" (without the quotes) to the end

---

### Post by 2hot6ft2 on 2008-10-24
> **guysmiley said:**
> If you're having problems in Synaptic or Firefox, if you're a newbie like me, here's the process at it's most basic:

ipv6 is a protocol not handled by many routers.  It's new and will be needed someday (which means a long time from now (like years) you're gonna have to buy a new one.  In the meantime, config linux not to use it by:

1.  Open a Terminal Window
2.  Type sudo gedit /etc/modprobe.d/bad_list/
3.  In the gedit window, type: alias net-pf-10 off
4.  Save the file and reboot.

To make sure you no longer have ipv6 running, open a terminal window and type:
ip a | grep inet6

Many thanks to mhael for this process!

gs  :)

I believe this is the post that is getting quoted a lot and right off the bat I see something that doesn't look right to me. Line 2

2.  Type sudo gedit /etc/modprobe.d/bad_list/
this line ends with a [COLOR="Magenta"]"/"[/COLOR]

Doesn't that make it a folder/directory instead of a editable text file?

I know I didn't have it in my command in terminal when I did it. This may be why ppl are having trouble getting it to work.

I did all 3 ways and now IPV6 is disabled on mine.

Here's what I did.

First was the Firefox fix: Opened a new tab and copy and pasted in the address bar:

about:config

hit "enter"

then in the "Filter Box" put:

ipv6

which brought up the option that says "network.dns.disableIPv6"

selected it then right clicked on it and toggled it to be "true"

Restarted Firefox.

Then in a terminal window copy and pasted:

sudo gedit /etc/modprobe.d/bad_list

and added this line

alias net-pf-10 off

saved and closed it then again in the terminal window copy and pasted:

sudo gedit /etc/modprobe.d/blacklist-ipv6

and added this line

blacklist ipv6

saved and closed it and everything else then rebooted.

Once up and running again in a new terminal window copy and pasted:

lsmod | grep ipv6

and hit enter. Then copy and pasted:

ip a | grep inet6

and hit enter.

Now they both return nothing.

Thanks to everyone for their posts on how to get it done.

Sorry for all the empty lines but it should be easier to follow that way.
By the way I'm using Ubuntu Ultimate Edition 1.8 x64
:guitar:

Too funny someone had the same idea at the same time;)

---

### Post by oaxacamatt1 on 2008-11-18
Hi SlowJet,
I noticed that the IP6 disable is for Daper.  Do you know if this fix works for Itepid ibex or not?
Oaxacamatt

---

### Post by anonymous_user on 2008-11-28
Just follow these instructions for Intrepid Ibex:

[http://ubuntuforums.org/showpost.php?p=2631546&postcount=116](http://ubuntuforums.org/showpost.php?p=2631546&postcount=116)

---

### Post by sanemanmad on 2009-02-04
How I have IPv6 blocked in Ubuntu Intrepid Ibex 64-bit Server:

Just insert following line I used from ([mhael's]("http://ubuntuforums.org/member.php?u=786")) post into bad_list file

> alias net-pf-10 off
```
sudo su
vi /etc/modprobe.d/bad_list
reboot now
```

```
netstat -tl
```
show only tcp and no tcp6 connections, that's how i know :)

IF THIS IS A PRODUCTION SERVER, THEN THERE ARE OTHER PREFERRED METHODS.... PLEASE DO NOT PERFORM THE LAST COMMAND *reboot now* This could lead to unwanted issues. Please seek advice on another method.

---

### Post by muhannadfa on 2009-03-02
Last night i booted from live CD ubuntu 8.10
it works like charm over the net
checked ipv6, it's working >> net speed is normal with no problems
------------------------------------------
make install ubuntu >> tried Internet >>> low Internet speed

Why while from live CD (ipv6 activated) > normal internet speed > install ubuntu > low speed 
------------------------------------------
do ipv6 disable >>> it works like charm
thanks in advance

---

### Post by -jay- on 2009-04-15
how do you disable this for 9.04 ?

---

### Post by BazookaAce on 2009-04-20
> **-jay- said:**
> how do you disable this for 9.04 ?

It's the same method as described. I just did it, and it works :)

---

### Post by nazrysamaratin on 2009-05-01
in my jaunty i didnt see bad_list or aliases and blacklist-ipv6 in modprobe.d folder

---

### Post by DJB1609 on 2009-05-24
Me too! (No bad_list or aliases in Jaunty).

---

### Post by Arup on 2009-05-24
Jaunty has ipv6 enabled at kernel level so nothing works.

---

### Post by vaikz on 2009-06-29
They are right, IPV6 is integrated in the kernel so all you need to do is disable it on the kernel parameters but before that you need to update your kernel. tried this and it work.

here&#347; the link. [http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html](http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html)

---

### Post by deankovell on 2009-07-07
I've got ubuntu studio 64 bit jaunty , which I don't know how different it is from other ubuntu jauntys, but I have read that it's got a real time kernel. For me grub says 2.6.28-3-rt. From what I've read the RT part is very important to the way the audio programs are going to work. I'm looking to upgrade my kernel so I can deal with my wireless issues, but I didn't see the RT on any of the Kernel updates. Sorry, but I completely new to Linux, and I need some help.  could someone point me in the direction to find an updated RT kernel so I can move on to getting my wireless up and actually test driving my shiny new ubuntu. Thanks.

---

### Post by randumnumber on 2009-12-08
I am having the same issue, after fresh installing 9.10 w firefox 3.5.5 websites seem to stick at certain points, i can reload or re request pages a few times and they will load eventually, if i let the page sit for a few minutes it will load eventually. i think its because of a timeout issue or something. ive been trying to fix it for a week to no avail. the first thing i did was disable ipv6 systemwide, and reboot it didnt work. same issues, i have tried to use firefox, seamonkey and chrome no use.

---

### Post by coach george on 2009-12-11
In order to dis-able IPV 6 DNS lookups in FireFox, this really slows down firefox:

[LIST=1]
[*]Open a new tab
[*]type in the address bar (with out the quotes) "about:config" Enter
[*]When it gives you the warning click "I'll be careful, I promise"
[*]In the filter bar type "ipv6"
[*]right click on "network.dns.disableIPv6;true" and choose "Toggle"
[/LIST]
Close the tab. You are done.  This also works in Windows.

---

### Post by batubolu on 2009-12-12
how about disabling it on karmic? is it the same way?

---

### Post by Ramcorfu on 2010-01-04
Greetings

I was facing a slow internet (web browsing) issue myself with Ubuntu and reached this discussion trying to find a solution.

I have not read all posts so I'm sorry if I will repeat something already told.

In my case the solution was simply to deactivate the "Block reported attack sites" and "Block reported web forgeries" options at the Preferences>Security tab of Firefox.

Hope this helps some users

Happy New Year to all :)

---

### Post by marcovanl on 2010-01-08
I agree with the post above; the firefox setting to disable IPv6 works for me, also on Karmic.

However, host lookups from the command-line are slow (e.g. host [www.google.com):](www.google.com):) I get a IPv4 reply quickly:

```
mvl@purple:~$ host www.google.com
www.google.com is an alias for www.l.google.com.
www.l.google.com has address 74.125.77.99
www.l.google.com has address 74.125.77.147
www.l.google.com has address 74.125.77.104
```

and then there is a pause, which I am pretty sure is caused by an IPv6 lookup attempt, which then results in:
```
;; connection timed out; no servers could be reached
;; connection timed out; no servers could be reached
```

I suspect that the built-in router/DNS server of my wireless DSL modem does not support IPv6. 

Switching off IPv6 with the kernel boot option, as described here: [http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html) 
does not help.

Even 'host -4' seems to try the IPv6 lookup. That's strange, or?

Any insights/ideas on this are welcome...

---

### Post by sharke on 2010-01-09
Disable ipv6 in karmic [http://www.webupd8.org/2009/11/how-to-disable-ipv6-in-ubuntu-910.html](http://www.webupd8.org/2009/11/how-to-disable-ipv6-in-ubuntu-910.html)
Cheers
Sharke

---

### Post by L a r r y on 2010-08-02
> **Josef K. said:**
> sorry for the silly question :rolleyes:  (but man page isn't so clear to me)
why there's ipv6 if you should disable?

IPV4 is the current IP addressing scheme, whereby you have IP addresses in 4 groups of 1-to-3 digits separated by a dot:  192.168.0.1

There are only so many IP addresses to go around, and in sometime in 2011 we will run out of available IP addresses to assign to new users of the Internet.

The IPV6 system increases the size of the pool of available IP addresses manyfold.  I am not sure about how this system works, but I am sure there must be an article on Wikipedia about IPV6 and IPV4.

IPV4 handles the Latin alphabet that the English-speaking world uses, and IPV4 is sufficient for our use as long as the supply holds up.  IPV6 handles domain names written in Chinese and other similar language scripts, and is therefore already in use in those parts of the world where those languages are used.

It is possible to disable IPV6 and speed up IPV4 processing, but you will eventually not have access to new resources as the supply of IP addresses runs out and new resources must be assigned IP's under the IPV6 system.

---

### Post by L a r r y on 2010-08-02
> **mhael said:**
> There's an easy way: instead of changing **aliases** file, create fie named **bad_list** in **/etc/modprobe.d** containing this line:
```
alias net-pf-10 off
```Now reboot and voila, no IPv6 on your system!

This method will work even if /etc/modprobe.d/aliases get replaced at some update.

I see I posted a reply earlier to this thread, responding to something on page 1 of a 16-page thread.

Oh woe.

I tried this bad_list approach in 10.04 and I still have IPV6 on my system after a reboot, but I disabled it in Firefox -- Boy did the pages fly onto my screen!

Just enter about:config into the address bar and enter ipv6 into the filter and toggle the value to true on the one item that comes up.

---

### Post by fabricio.lemos on 2010-10-17
I'm having problems with my internet connection. Firefox was really slow. I fix the problem setting network.dns.disableIPv6;true in about:config.

But I still having problems with other software, like curl. Any curl request takes 20 seconds to return in Ubuntu. With Windows they return instantly. I also have some Java code that does some http requests, which also takes 20 seconds and in Windows returns instantly.

I already tried 
```

echo 'blacklist ipv6' | sudo tee -a '/etc/modprobe.d/blacklist.local' >/dev/null
echo "#disable ipv6" | sudo tee -a /etc/sysctl.conf
echo "net.ipv6.conf.all.disable_ipv6 = 1" | sudo tee -a /etc/sysctl.conf
echo "net.ipv6.conf.default.disable_ipv6 = 1" | sudo tee -a /etc/sysctl.conf
echo "net.ipv6.conf.lo.disable_ipv6 = 1" | sudo tee -a /etc/sysctl.conf
```

but with no results.

command
```
cat /proc/sys/net/ipv6/conf/all/disable_ipv6
```
returns 1

and
```
lsmod | grep ipv6
```
returns nothing

Does anyone have some clue on what could be wrong?

---

### Post by Jepeppi on 2011-05-24
> **Saiboogu said:**
> For future support. IPv4 is running out of address space, so we must transition to IPv6 at some point soon. IPv6 also offers other benefits that I'm not immediately aware of ... Just the latest and greatest networking gimick, yada yada :) But support isn't widespread yet, so mostly its just sitting idle on your system. Disabling it removes some bloat and streamlines your networking for the time being, especially (in my experience) within Firefox. 

Try typing about:config in your Firefox address bar. Type ipv6 in the "Filter:" box, find the option that says "network.dns.disableIPv6". If it reads "False" right click and toggle it to True. Should give you a slight speedup in your browsing.

EDIT: As usual, I sat on my reply too long. I even refreshed the initial page before I posted to make sure I didn't do this .. Pagebreak fooled me. ;) But, I like SJ's answer better anyway .... 

:)

Oh dude! Thank you so much for that! I was struggling to get 1kb/s until I did what you said and then my dl finished in a split second!

Since this is my first post here, just a little background on me: I live in Melbourne Australia, 25y.o married, bub on the way, and am not what you would call good with computers. I get by, but I'm not great, so your input has helped me immensely! Ubuntu 11.04 is my first real Linux experience, which I am using because I use an eeePC for uni, and it was PAINFULLY slow on XP. Please don't can my account for this statement, but I personally am quite fond of Windows 7 as it is a delightful change from the rubbish you got with Vista and XP. I am struggling to get around ubuntu, and (no offence to the creators of it, compliments are below) I am finding it very difficult without any computer knowledge to get around. As for the compliments I have for it: First off, I was impressed by how easy it is to do the basic stuff. Just accessing files, updating etc... was a breeze! It was pretty easy to install, and I liked how it had my sound, mouse, speaker etc... drivers ready to go. Good job on it there guys! You guys have done a great job for a software that earns you no money, and for that: hats off! I know i complained about some aspects above, but don't think I don't know why these problems are there, and that I am not impressed regardless at the quality of the OS considering it is free and made on peoples free time. I know its evolution will continue and do hope that it catches windows soon (as good as 7 is, $300 is a bit steep!!!).

Thanks again guys! I know that I will be on here again with more drama's as I can't stand it. I personally work on cars, and am quite good with them, so if you have any car drama's just PM me. If it is a car that we do not have in Australia, then forgive the amount of conversation needed to diagnose problems, but that would be expected when dealing with a foreign to me car (if anyone ever tells you all cars are the same, they are lying or stupid).

---

### Post by Jepeppi on 2011-05-24
Hi guys, sorry to bug you again, but I have another internet speed related issue that isn't ivp6 related. When I plug my eeepc into power, the internet is great. It runs at the same speed it used to on XP, and that my wifes netbook with XP does. However, once i run onto batteries, it becomes REALLY slow. I've scoured the power settings, and wireless settings that I could find and there was nothing about capping the speed to save power or anything. How can I fix this?

---

### Post by Mineria on 2013-04-15
> **L a r r y said:**
> 
It is possible to disable IPV6 and speed up IPV4 processing, but you will eventually not have access to new resources as the supply of IP addresses runs out and new resources must be assigned IP's under the IPV6 system.
And? Most ISP's here still provide connections as ipv4 without any form of ipv6 support, heck, a lot of Companies still use firewalls and routers with no ipv6 support either. and it works, cause of ipv4 to ipv6 conversion.  PS. sorry for necroing this up, but ipv6 still gets disabled on many servers to avoid conflicts and bugs.

---

