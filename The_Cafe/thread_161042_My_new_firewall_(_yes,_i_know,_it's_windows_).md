---
title: "My new firewall ( yes, i know, it's windows )"
date: 2006-04-16
forum: The Cafe
---

### Post by jason.b.c on 2006-04-16
Has anybody every had any experience with **Comodo Personal Firewall** in windows.??

I had the *Sygate Firewall* for like the longest time but it crapped out on me and won't reinstall ( *you know how windows behaves *), so i downloaded a new one ( All Totally Free )..    But now i have this problem with it not letting me get **ANYWHERE**:mad:  on the internet including this forum,  See thats why i'm asking this here ( ha ha ha )  If anyone knows how i can correct this i sure would be willing to listen..!!!:eek: 


I've been up half the night **Fighting** with windows and i'm getting preaty sick of it.!!:mad: ](*,) 

Yea i know, this isn't a linux question, is it.;)

---

### Post by bjweeks on 2006-04-16
Get a router.

---

### Post by zenwhen on 2006-04-16
[QUOTE=bjweeks]Get a router.[/QUOTE]
Gonna have to second this.

---

### Post by prizrak on 2006-04-16
Try Kerio (i think that's how it's spelled). Sygate used to be awesome but now it's owned by Symantec so it sux. 
Otherwise get a router new ones come with SPI firewalls and are quite nice.

---

### Post by ice60 on 2006-04-16
i use the free old version of Kerio 2.1.5 with BlitzenZeus's replacement rules. only use if you really understand the protocols! because it's hard getting help if you don't - BlitzenZeus is quite vicious lol (the rules are down the page, near the buttom - BZKerio2xDefaultRepl

select "Kerio Personal Firewall" from the dropdown, then 2.1.5
[http://download.kerio.com/archive/](http://download.kerio.com/archive/)
[http://www.dslreports.com/forum/remark,8023708](http://www.dslreports.com/forum/remark,8023708)

forum
[http://www.dslreports.com/forum/kerio](http://www.dslreports.com/forum/kerio)

maybe read this first??
[http://www.dslreports.com/forum/remark,2670783~root=kerio~mode=flat](http://www.dslreports.com/forum/remark,2670783~root=kerio~mode=flat)

actually, you can find out about that firewall below
[http://www.wilderssecurity.com/showthread.php?t=127726](http://www.wilderssecurity.com/showthread.php?t=127726)

---

### Post by Lovechild on 2006-04-16
> 
Windows 2k pro and Ubuntu breezy super user..


I think we have a contradition here..

please if you must use a software firewall, IPtables isn't hard to setup, we even have nice guis.. otherwise get a router

---

### Post by jason.b.c on 2006-04-16
[QUOTE=Lovechild]I think we have a contradition here..

please if you must use a software firewall, IPtables isn't hard to setup, we even have nice guis.. otherwise get a router[/QUOTE]


OH  Hardy Har Har, Nah i know you were joking.:) 

> IPtables isn't hard to setup

  Iptables in windows????  Is that what you meant??

> otherwise get a router   Well i wish i had *high speed*, unfortunetly i'm stuck with internal dialup wich means i don't have internet in ubuntu.](*,) 

Thank you **Ice60** i'll keep that stuff in mind.:D

---

### Post by ice60 on 2006-04-16
[QUOTE=jason.b.c]Thank you**Ice60** i'll keep that stuff in mind.:D[/QUOTE]
no problem, i just want to say Kerio 2.1.5 is just about lightest FW there is resource wise.

i'll help you set up Kerio if you like, once you've setup one or two rules they pretty much follow the same pattern. then we can ask if the rules look OK somewhere :)  

also, for more ideas you can look [here](http://wilderssecurity.com/forumdisplay.php?f=31), they seem to spend most of their online time trying out new FWs lol

---

### Post by jason.b.c on 2006-04-16
[QUOTE=ice60]no problem, i just want to say Kerio 2.1.5 is just about lightest FW there is resource wise.

i'll help you set up Kerio if you like, once you've setup one or two rules they pretty much follow the same pattern. then we can ask if the rules look OK somewhere :)  

also, for more ideas you can look [here](http://wilderssecurity.com/forumdisplay.php?f=31), they seem to spend most of their online time trying out new FWs lol[/QUOTE]


:D Ok Cool, I have ( what i think ) is an older version of *Kerio* on a disk that i got in the mail, Now i did install it first before comodo, but i noticed something afterwards- in the startup splash screen thingy ;)  it sayed that   *" this is a thirty**(30)** day trial period* , it also sayed something like that after  the trial the firewall would no longer protect from **incoming** ( i think ) traffic.  I don't know.:(    But now i think i've got this **Comodo** thing figured out ( i hope ) i'm in this forum now with it "on" full strength so...?

I'll still keep ya in mind though, in case i have any trouble.   Thanks:)

---

### Post by towsonu2003 on 2006-04-16
[QUOTE=jason.b.c]Has anybody every had any experience with **Comodo Personal Firewall** in windows.??

I had the *Sygate Firewall* for like the longest time but it crapped out on me and won't reinstall ( *you know how windows behaves *), so i downloaded a new one ( All Totally Free )..    But now i have this problem with it not letting me get **ANYWHERE**:mad:  on the internet including this forum,  See thats why i'm asking this here ( ha ha ha )  If anyone knows how i can correct this i sure would be willing to listen..!!!:eek: 


I've been up half the night **Fighting** with windows and i'm getting preaty sick of it.!!:mad: ](*,) 

Yea i know, this isn't a linux question, is it.;)[/QUOTE]
I donno how comodo works. you probably have to navigate preferences inside the program and open ports (80 for http, 443 for https) or tell it to allow specific programs to access internet.

I never had problems with zonelabs personal firewall (free). it learns (by asking you questions) as you go along.

---

### Post by ice60 on 2006-04-16
[QUOTE=jason.b.c]I'll still keep ya in mind though, in case i have any trouble.   Thanks:)[/QUOTE]
you can do a port scan to check and see it's working.
click through the first page then click on something like 'all service ports' or 'all common ports' i can't check because i'm using a proxy and it won't let me into the site
[https://grc.com/x/ne.dll?bh0bkyd2](https://grc.com/x/ne.dll?bh0bkyd2)

Note - if you are using a router it will likely just scan your router and not the software firewall, also check you have disabled the windows firewall.

what happens when you launch a new program which wants internet access?

you can try TCPView, it's a standalone network monitor
[http://www.sysinternals.com/Utilities/TcpView.html](http://www.sysinternals.com/Utilities/TcpView.html)

you could also try Process Explorer to see if it's running and how it's working
[http://www.sysinternals.com/Utilities/ProcessExplorer.html](http://www.sysinternals.com/Utilities/ProcessExplorer.html)

---

### Post by jason.b.c on 2006-04-16
> **ice60]you can do a port scan to check and see it's working.
click through the first page then click on something like 'all service ports' or 'all common ports' i can't check because i'm using a proxy and it won't let me into the site
[https://grc.com/x/ne.dll?bh0bkyd2](https://grc.com/x/ne.dll?bh0bkyd2)

Note - if you are using a router it will likely just scan your router and not the software firewall, also check you have disabled the windows firewall.

what happens when you launch a new program which wants internet access?

you can try TCPView, it's a standalone network monitor
[http://www.sysinternals.com/Utilities/TcpView.html](http://www.sysinternals.com/Utilities/TcpView.html)

you could also try Process Explorer to see if it's running and how it's working
[http://www.sysinternals.com/Utilities/ProcessExplorer.html](http://www.sysinternals.com/Utilities/ProcessExplorer.html)[/QUOTE]




> what happens when you launch a new program which wants internet access?


A little pop up thingy comes up asking for permission to let that program have  access the internet.:) 


> you could also try Process Explorer to see if it's running 

Allready have it, It's a cool little program, isn't it?? said:**
> if you are using a router =  Dial up. internal.  it sucks.!:(

---

### Post by jason.b.c on 2006-04-16
Ok i did that firewall scan thing in the link you provided, here's what i got.:>

--------------------------------------------------------------------

GRC Port Authority Report created on UTC: 2006-04-17 at 01:35:48

Results from scan of ports: 0-1055

    0 Ports Open
   32 Ports Closed
 1024 Ports Stealth
---------------------
 1056 Ports Tested

NO PORTS were found to be OPEN.

Ports found to be CLOSED were: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 
                               10, 11, 12, 13, 14, 15, 16, 17, 
                               18, 19, 20, 21, 22, 23, 24, 25, 
                               26, 27, 28, 29, 30, 31

Other than what is listed above, all ports are STEALTH.

TruStealth: FAILED - NOT all tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - A PING REPLY (ICMP Echo) WAS RECEIVED.

------------

So did i pass or fail??:confused:    The one thing said " **True Stealth Fail** ":confused:

Is that a bad thing when it knows your **11** digit IP address??

---

### Post by ice60 on 2006-04-16
[QUOTE=jason.b.c]Ok i did that firewall scan thing in the link you provided, here's what i got.:>

--------------------------------------------------------------------

GRC Port Authority Report created on UTC: 2006-04-17 at 01:35:48

Results from scan of ports: 0-1055

    0 Ports Open
   32 Ports Closed
 1024 Ports Stealth
---------------------
 1056 Ports Tested

NO PORTS were found to be OPEN.

Ports found to be CLOSED were: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 
                               10, 11, 12, 13, 14, 15, 16, 17, 
                               18, 19, 20, 21, 22, 23, 24, 25, 
                               26, 27, 28, 29, 30, 31

Other than what is listed above, all ports are STEALTH.

TruStealth: FAILED - NOT all tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - A PING REPLY (ICMP Echo) WAS RECEIVED.

------------

So did i pass or fail??:confused:    The one thing said " **True Stealth Fail** ":confused:

Is that a bad thing when it knows your **11** digit IP address??[/QUOTE]
that's a result he talks about on the results page. it should be under the result, your firewall is reacting to the scan in some way. it's the bit where it starts off all blue then turns green, i think.

i'll disable my proxy and have alook at the page i'm talking about, it won't let me on to the site with it on ](*,)

---

### Post by ice60 on 2006-04-16
i've saved the relevant text to a text file and attached it to the post. anyway, your FW is perfectly safe - all the ports were closed. the difference between closed and stelthed is a stealthed FW will drop all the packets and not return a reply. closed will say 'yes i'm here, but the port is closed'

any network expert (i'm not an expert lol) will tell you there's no difference **AT ALL** between the two.

when a hacker does a scan and there's no reply they know there's someone at the IP because packets are supposed to let you know if they don't get to where they're going to with 'unreachable' replies.

plus there are tools like nmap which will send 'funny' packets which act in such a way a hacker knows if someone is there.

so you are fine, there's only a problem if you start finding ports open, keep checking over the next day or so. :cool:

---

### Post by ice60 on 2006-04-16
this is the bit from the text file, i can't see the attachment from the last post. it's on the results page from the scan, you should see it when you next do a scan 

> Strange Results?
Personal firewalls are beginning to exhibit "adaptive behavior". The grid shown to the left starts off showing ports mostly closed with a few open (mostly blue with a few red cells). Then at some point it suddenly switches into "stealth mode". This can occur when a firewall "adapts" to the scanning IP and raises its defenses against just the attacker. This complicates the job of accurately checking a system's security.

Two things you can do: If you are not certain whether your firewall is adaptive, you can re-run any test here to compare the results. Differing behavior often indicates that your firewall has "learned" that it is being probed from our IP and is treating it differently. For the most accurate scan results, disable any adaptive behavior during the testing.

You can use these tests to learn exactly how your firewall deals with probes to specific ports, and to port ranges.


---

### Post by jason.b.c on 2006-04-17
> so you are fine, there's only a problem if you start finding ports open, keep checking over the next day or so.

Ok cool, That result page on that site was just a bit confusing:confused:  and i wasn't sure.

I know when i had **Sygate** in here it was no problem to get it set up and tested on there website.;) And it always past with *Flying colors*.;) 

This one seems to be working ok now ( I think/hope ):p

---

### Post by ice60 on 2006-04-17
[QUOTE=jason.b.c]Ok cool, That result page on that site was just a bit confusing:confused:  and i wasn't sure.

I know when i had **Sygate** in here it was no problem to get it set up and tested on there website.;) And it always past with *Flying colors*.;) 

This one seems to be working ok now ( I think/hope ):p[/QUOTE]
OK, let us know if it starts showing open ports, if it doesn't you should be fine. :)

---

### Post by Sonique on 2006-04-17
[QUOTE=bjweeks]Get a router.[/QUOTE]

I have a router and am using ubuntu. If i don't forward any ports, am I safe, or should i use firestarter? Also, does firestarter actually do anything?

---

### Post by jason.b.c on 2006-04-17
----------------------------------------------------------------------

GRC Port Authority Report created on UTC: 2006-04-18 at 02:06:35

Results from scan of ports: 0-1055

    0 Ports Open
   32 Ports Closed
 1024 Ports Stealth
---------------------
 1056 Ports Tested

NO PORTS were found to be OPEN.

Ports found to be CLOSED were: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 
                               10, 11, 12, 13, 14, 15, 16, 17, 
                               18, 19, 20, 21, 22, 23, 24, 25, 
                               26, 27, 28, 29, 30, 31

Other than what is listed above, all ports are STEALTH.

TruStealth: FAILED - NOT all tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - A PING REPLY (ICMP Echo) WAS RECEIVED.

----------------------------------------------------------------------;) 


Now i wonder how i could *close up* just a **few** of these ports??](*,) To make the "Trustealth" a little better.?!

---

### Post by cnbiz850 on 2006-04-18
[QUOTE=jason.b.c]Has anybody every had any experience with **Comodo Personal Firewall** in windows.??

I had the *Sygate Firewall* for like the longest time but it crapped out on me and won't reinstall ( *you know how windows behaves *), so i downloaded a new one ( All Totally Free )..    But now i have this problem with it not letting me get **ANYWHERE**:mad:  on the internet including this forum,  See thats why i'm asking this here ( ha ha ha )  If anyone knows how i can correct this i sure would be willing to listen..!!!:eek: 


I've been up half the night **Fighting** with windows and i'm getting preaty sick of it.!!:mad: ](*,) 

Yea i know, this isn't a linux question, is it.;)[/QUOTE]

Your best solution is to dump Windows completely. You can't save trash.

---

### Post by jason.b.c on 2006-04-18
[QUOTE=cnbiz850]Your best solution is to dump Windows completely. You can't save trash.[/QUOTE]


Hey hey now, Well ok i'll ask you this then:>     **ARE YOU** going to send _me_ an external modem so that i can have internet access in ***Ubuntu***?????:rolleyes: :rolleyes: 

Thats all i've got right now,  some people don't have an abundance of money to throw around....

---

### Post by benplaut on 2006-04-18
I'm suprised nobody said it before...

t3h best f*ing firewall out there is ZoneAlarm. Make sure you get the personal edition (which is completely free, no trial)

---

### Post by jason.b.c on 2006-04-18
[QUOTE=benplaut]I'm suprised nobody said it before...

t3h best f*ing firewall out there is ZoneAlarm. Make sure you get the personal edition (which is completely free, no trial)[/QUOTE]


:eek: ;)   I thought **ZoneAlarm** was only for *High speed internet* ???:o

---

### Post by ice60 on 2006-04-18
[QUOTE=Sonique]I have a router and am using ubuntu. If i don't forward any ports, am I safe, or should i use firestarter? Also, does firestarter actually do anything?[/QUOTE]
yes, you should be fine. Ubuntu does have a firewall running called iptables, so you should have your router and iptables running. firestarter is only a frontend for iptables.
[QUOTE=jason.b.c]:eek: ;)   I thought **ZoneAlarm** was only for *High speed internet* ???:o[/QUOTE]
Zone Alarm is a software firewall, you can use any software firewall.


like i already said - i'm not an expert , but i'll just tell you how i think it works :rolleyes: 

this is how routers (hardware firewalls) and software firewalls (zone alarm, Kerio etc) work and what they do.

a router sits at the gateway to the internet on your home network. it does two things - blocks unwanted packets from the internet (like a firewall) and forwards packets to computers behind it using its routing table. 

NOTE - there's no safe authentication method behind a router, so they are safe to use at home when you trust all the computers connected, but at the local cafe shop, or hot spot, you have to assume someone is watching everything you do. that's unless you use ssh, vnc etc to connect to your home computer first, then route out to the internet that way

routers block packets in one direction only - from the interent. software firewalls block in both directions. that's because a router might have 100 computers behind it so it just lets everything through. a software firewall is only used by one computer so it will let you know when something wants internet access then lets you decide what to do.

so if you have a worm on your computer a router will let it out to the internet, a software firewall will stop it.

most windows firewalls do alot more then just block or accept packets, they might block popups, watch cookies, tell you your Anti Virus patterns are out of date :rolleyes: that's what Zone Alarm does, and because of that it uses alot of resources and its more likely to conflict with other software. some firewalls even have sandboxes to control what's allowed to run on the computer, i think the new Kerio firewall does that, and Tiny too.

---

