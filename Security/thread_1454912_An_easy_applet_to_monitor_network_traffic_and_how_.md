---
title: "An easy applet to monitor network traffic and how to turn firestarter into it"
date: 2010-04-15
forum: Security
---

### Post by tanoloco on 2010-04-15
Hi guys,

sorry for the long post:

[CENTER][U][B]FIRST BLOCK: ANY EASY NETWORK TRAFFIC MONITOR APPLET?

[/B][/U][/CENTER]
I recently switched from firestarter to ufw following nowadays recommendation and I installed gufw as its configuration gui :)

Everything works nice but I miss some firestarter features. As I want to use gufw only to configure ufw, as it would be, I would like to install another applet which:

1. could remain iconized in the notification area.

2. is easy to read and light while running.

3. can show network traffic reporting if the firewall blocks something with ip addresses, in or out, tcp or udp info (as events tab on firestarter) and maybe could change color if the firewall blocks something (as firestarter shows the red flash)

4. can show the active traffic (as the active connections tab on firestarter)

Any suggestions?
I tried some product like wireshark (too complicated) and etherape (not working with me)

Oh .. this applet must work on any active interfaces, as I have to install it on a laptop which has ethernet or wireless connection .. so the applet must keep on working switching interfaces.



[CENTER][B][U]SECOND BLOCK: TURN FIRESTARTER INTO THE REQUIRED APPLET:

[/U][/B][/CENTER]
While testing ufw I firstly hadn't removed firestarter but left it iconized on the notification area and stopped. I noticed that it could keep on working as this required applet: it does all I wrote before included if ufw blocked a request firestarter (while stopped) would show it changing color and listing the event in the event tab. Even the active connections are keeping on working.

So I thought I could turn firestarter into this required applet but I've noticed that while stopped if I enable a network connection (both ethernet or wireless) it starts up automatically and turn off ufw!!

So to turn completely firestarter in a network applet I:
1. ran the wizard again and selected *[I]"Start*/*Restart* firewall on program startup".
[/I]2. edited```
sudo gedit /etc/firestarter/firestarter.sh
```and added 
```
exit 0
```immediately after ```
#!/bin/bash
```3. I configured firestarter to start automatically on boot as explained in a lot of guides online

In this way:
Good.
- firestarter will start on boot iconized on the notification area
- it won't disable ufw while enabling a network connection
- if enabled it will soon auto stop itself
- changing the rules on firestarter won't affect ufw behavior.
- ufw activity will be reported changing the icon (of firestarter) and listed on the events tab
- the active connections list of firestarter will work properly.

Bad:
- firestarter will always have a red icon: at least changin from stopped status with a square to blocking status with a flash

Question:
a: Does this make sense? I mean to turn firestarter into a network applet ..

b: Is this safe? I read that starting up firestarter on boot is not safe but as long as I tested changing rules in firestarter won't affect the active firewall (ufw) and even if enabled it will disable itself very soon .. so I guess that an hacker won't have anything to gain if he can manipulate firestarter started on boot. Is it right?

c: Is there a chance to change the stopped icon on firestarter into another one? for example a green one. Changing the color will catch better the user attention.

[B]
BTW: [/B]where is located the log that firestarter read to list the requests blocked by ufw???

Again sorry fot the long post :)
Cheers

---

### Post by LeeDaugherty on 2010-04-15
First, every firewall in Linux does the same thing.  Built into the kernel is a "program" called iptables.  This is what filters IP traffic.  Most people find iptables very hard and confusing, that's why ufw, firestarter, and the rest of them exist.  The are front-ends for iptables (and sysctl...but that's another story).  Firestarter has a gui, but when you start it, the only thing it does is run a script that turns on iptables.  When you start ufw, it does the same.  Both of them are doing the same thing, and overwriting each other.  There is no program I know of like Firestarter.  It is a neat program, but no serious security program live monitors.  It's computer intensive, and albeit fun to watch, but in the end completely pointless.  And for that matter, Firestarter's GUI was legendary for not reporting usually 20% of traffic is you had more than a 10 connections up.  What you are asking for is Firestarter, but it's a dead package.  And please do not use it, it is very outdated, and reprograms features in the kernel that need to be set differently for good internet performance.  And FYI, firestarter runs on boot, it runs the scripts.  Whether the GUI/icon is there, it has already run it's scripts and secured the system (why are you worried about securing Ubuntu anyway with a firewall?), when you click on it again, it runs the scripts again (pointless), and starts the GUI.  I hate to seem negative, I used firestarter for years, I love it, if I had time I'd bring it back from the dead, but it's dead, and bad to use now.  I'm sorry.

---

### Post by tanoloco on 2010-04-15
Thank you to clarify this for me :)

In the meanwhile I've understood that any firewall log its activities into /var/log/syslog
so that's how firestarter could read ufw blocks and show them.

Ok: you explained very good to me so I can remove firestarter (sigh! :() use ufw and check syslog if something goes wrong by typing 

```
grep UFW /var/log/syslog
```

Could it be?

It would have be nice to have an icon showing that the firewall is blocking something but ok ..

Cheers
T

---

### Post by LeeDaugherty on 2010-04-15
There is some minor reporting functionality in ufw...'ufw show listening' will report listening ports on your system and 'ufw show raw' dumps all its info, 'ufw status' is usually good too.  As far as the ICMP block goes, UFW default replies.  I'm not sure if ufw-gui or whatever does it, but editing /etc/ufw/before.rules and changing the five rules that are in the ICMP section 'ufw-before input icmp icmp type echo request DROP'...they all say ACCEPT by default, I'd make them all DROP.  It'll stop most responses to most types of port-scans.  And make sure you always DROP, not REJECT.  Reject sends a signal back, it's just as good as being open.  THere is tons of docs on ufw, it's really easy to use and kind of fun.  While UFW probably does log to syslog, it technically would be kern.log.  And for that matter, there are utilities to process log files that might help you make reports, if you want to do that.  Just beware of the martians.

---

### Post by lovinglinux on 2010-04-15
For monitoring active connections: [iptraf](apt:iptraf) [iptstate](apt:iptstate)

For monitoring blocked connections:

```
tail -f /var/log/messages
```

---

### Post by LeeDaugherty on 2010-04-15
Forgot about iptraf, that's a good one and low resources...great suggestion

---

### Post by lovinglinux on 2010-04-15
> **LeeDaugherty said:**
> Forgot about iptraf, that's a good one and low resources...great suggestion

Yes it is, but I still prefer the simplicity of iptstate. Anyway, I used to monitor traffic for both active and blocked connections when I switched from Windows. Today I don't even waste my time with that.

---

### Post by bodhi.zazen on 2010-04-15
> **lovinglinux said:**
> Yes it is, but I still prefer the simplicity of iptstate. Anyway, I used to monitor traffic for both active and blocked connections when I switched from Windows. Today I don't even waste my time with that.

This ^^

---

### Post by tanoloco on 2010-04-16
I swiched from win only since a few months .. maybe in a while I'll not wasting my time over that anymore too :) .. but for now I'm still afraid of the martians!! :KS

It's still unbelievable for me to drop any anti-virud app on ubuntu (WOW!) but I read somewhere that a firewall is still a good idea to install on it ... and for now I think it's correct. Maybe in a while I will change my mind :P

Maybe using a firewall is useless at all, as someone might say, but in case someone wants to use it I think that an applet addable to the bar showing if the firewall is blocking something is needed and missing.

Once for example I spent a lot of time and money wth a tec phone center of my isp because  I couldn't downoad anymore my emails with evolution and after days I discovered that I was blocking the pop3 port !!!
I discovered it by chance opening firestarter which has this alerting icon.

I think I'm not the only one on the earth thinking that if you just have a look at this:
[http://brainstorm.ubuntu.com/idea/22/](http://brainstorm.ubuntu.com/idea/22/)

the usage of a firewall seems to be arbitrary and as far as I can understand I personally agree with the user defcon in that thread who says:
> I agree with this feature, some people will need to open certain ports for certain applications, and may want to block certain applications from certain ip ranges. Add a few nice features in an easy/basic gui and a firewall log monitor and we will see allot of happy people. Blah blah blah :guitar:

---------------------------------------------------------------------------
just to give some feedback:

**1.** thank you **lovinglinux** I'll use iptstate if ever want to monitor my net because it's easier
and together with your code for monitoring blocked connections they fit my needs
:popcorn:

Though an alerting icon applet for firewall activity is still missing imo.


**2. lee**: thank you for explaining it to me more detailed, but I don't have show command in ufw ```
sudo ufw show
sudo ufw show listening
```give error: action "show" not supported

my situation:
ufw version: 0.29-4ubuntu1
gufw version: 10.04.3-0ubuntu2
kernel: 2.6.31-20-generic (karmic)

While if I edit ```
sudo gedit /etc/ufw/before.rules
```I've got this icmp section> # ok icmp codes
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPTeven if with the gui gufw I set in and out as deny.

Do you recommend to set them manually to DROP?
What do they affect exactly? I haven't found any info around at the moment


**3. Lee**: just to know and understand better (no wish to use :)) but are you sure that firestarter "reprograms features in the kernel that need to be set differently for good internet performance" or can do other not recommendable things even if I use it having put exit 0 just after #! /bin/bash in its firestarter.sh?

It does nothing in this way, neither loads its configuration ... it's a doing -nothig bash like
```

#! /bin/bash
exit 0
```Maybe it's inoffensive in that way and it's really working only as a monitoring applet.
Any change I do with firestarter in this way has no effect at all.

Maybe this could be interesting because a working applet addable to the bar monitoring the net and showing firewall activity is missing.


Thank you all guys for your help!!!

---

