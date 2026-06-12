---
title: "Hits, Hacks, and port hole cracks"
date: 2007-06-03
forum: Server Platforms
---

### Post by TheFlamingBush on 2007-06-03
Ok i have a problem.

i have a duel boot laptop, with XP and Dapper. 

Up until recently i have had to use my XP, as ive been using a speedtouch 330 usb modem, and the connectivity was a bridge too far for me, being a bit of a linux novice. 

However, a week ago, i ran into an article on here, where a new member of the Ubuntu clan had taken it on board to write a connection program for adsl speedtouch 330 modems, and viola it worked like a treat!.....

boy was i happy!!!!.......no longer have i had to boot into XP, being able to use this incredible distro, and features that is Ubuntu Dapper.

I have clam and firestarter installed. And i have also installed a number of other programs over the year ive had Ubuntu.....mostly to do with my film making, such as Cinelerra, and graphics tools, along with a sound recording studio ( licks lips waiting for Ubuntu Studio to unfold).

Since my connectivity however, ive been taking an unbelievable number of hits on Firestarter.....every minute or two, for the entire week, sometimes every few seconds my ports are being hammered, from all over the place......fujitsu, abuse demon, and too many others to mention have been attacking my box non stop.
I'll post the first few minutes log for todays online session for you to see the kind of traffic im getting.

I have to say its beginning to scare the heck out of me, and im about the can Ubuntu as an online alternative to Windows, which i have running, zone alarm pro, SSM, avira, and various rootkit scanners and spy and bot scanners. I know they suck my resourses, but at least im fairly certain im catching the hacks, cracks, and whacks.

How can i be sure all my ports are now closed, since ive been installing software on my Ubuntu for about a year?.........how can i be sure that im not b eing used as a bounce by some clever ******* to break into the CIA?.........where is the security in this system once you have installed software beyond the origional specs?.... 

I know the ports are all closed on a new install, but hey mine isnt, and im worried im leaking info, or worse being used as a bounce.

My business is such i need my laptop as a graphic sound and video studio, and cannot afford to lose data.....am i then forced to go back to XP..........i sure dont want to, but im taking so much flack and being probed almost incesintly its hard not to.

any and all suggestions gratefully accepted.

I had various hits on a multiple array of ports in the first 20 mins today and still its ongoing, about 50 hits in 18 minutes so far.

---

### Post by cantormath on 2007-06-03
Alright, first of all............
those programs you talk about do not protect you as well as linux, they just dont tell you about the security issues.  They are made to make you feel safe.

Going back to windows would be like putting a wooden door on a bank vault instead of the vault door.

Unless you are running a mail server, you dont really need clam.....but you can use it.  If you have firestarter, again, probably a bit over protected, especially for a home unit, but go to town with it.  Also, how do you know of these "hits"?  Is the firewall telling you?  That is a good thing.

You can check the ports via nmap to localhost I believe:
in terminal
```
:/$ sudo nmap localhost
``` Use your password if prompted.

The hits arent alot to worry about if you are locked up with linux, you can engage a firewall on your router or switch and block connections from the outside, meaning your router will block people trying to connect to anything behind your router from the outside, however, if there is a nice locked up linux box, there isnt alot to worry about.   If you are realllllly scared.  You can also block an entire subnet of IPs.   If, for example, the hits are coming from IPs in China, you can block the entire subnet of chinese IPs in question......Start here for that:
[http://okean.com/thegoods.html](http://okean.com/thegoods.html)
you would have to right a cron or something to do the subnet block, at least as far as I know.  To figure out where the IPs hitting you are ..........use whois <IP> in terminal.

> im taking so much flack and being probed almost incesintly its hard not to.You think it gonna stop when you go back to the wooden door? :-)

Bottom line.  You are 10x safer on linux then windows.........there is no spyware or virii in linux, windows virii do not work on linux............and contrary to this fact......you are running virus protection, have a firewall, and you even have the option to use AVG antispyware to protect you against a none threat,...unless you are running a email server for a business or something.....spyware then only an issue because email servers can send spyware to windows boxes, but your box would still  be fine.

My opinion, your gonna be just fine.


Hope that helps and dont be stupid(aka windows).

---

### Post by TheFlamingBush on 2007-06-03
Thanks Cantormath, ive installed Nmap, and probed my local host and found i have 3 open ports. running 
1/ netbios-ssn
2/microsoft-ds
3/ ipp

the microsoft-ds activity on one of the open ports is a bit weird, i dont really know whatt that is?

im about to download nessus, and have a good look at all vulnerabilities. Im still taking a load of hits, but at least it appears that most of my ports are stil closed.

Ive still got the xp installed as a couple of commercial progs are native windows for business, and im still gaming a little which sadly is still a little better in windows........ hopefully not for long! :)

but Ubuntu is definately my prefered option for os, and ive also tried red hat, mandrake, suse.....but Ubuntu rocks! :)

JUST NEED TO MAKE SURE THE SECURITY ISSUES ARE SORTED OUT!:KS

thanks again man for the advise.

---

### Post by davef1m on 2007-06-03
If you aren't sharing files with any Windows boxes, disable the first two, and if you aren't sharing your printer, disable the last one as well.

---

### Post by TheFlamingBush on 2007-06-03
what about my connectivity to the net dave?....isnt one of these to connection?......and im wondering if one of the ports isnt being used as access to the windows patition?

sorry for being such a novice. (blush)

---

### Post by cantormath on 2007-06-03
> **TheFlamingBush said:**
> what about my connectivity to the net dave?....isnt one of these to connection?......and im wondering if one of the ports isnt being used as access to the windows patition?

sorry for being such a novice. (blush)


no....those are showing what ports you have open coming in...again, just because they are open does not mean they are vulnerable.  When you share with windows boxes, you should enable them to require a password to access shares, if they are not that way by default..... You can use the windows firewall on them and enable file sharing as an exception.  If you have windows boxes accessing your linux box, that usually requires a password as well......

> **TheFlamingBush said:**
> 
im about to download nessus, and have a good look at all vulnerabilities. Im still taking a load of hits, but at least it appears that most of my ports are stil closed.

Again, Nessus is over kill for home, but you are welcome to it.  Nmap should be enough.

> **TheFlamingBush said:**
> 
Ive still got the xp installed as a couple of commercial progs are native windows for business, and im still gaming a little which sadly is still a little better in windows........ hopefully not for long! :)

Sadly, gaming is not awesome yet on Linux, however, cedega works really well from what I have seen for installing M$ based games on a linux box,.  I am not a gamer, so I have little advice there.
> **TheFlamingBush said:**
> 
but Ubuntu is definately my prefered option for os, and ive also tried red hat, mandrake, suse.....but Ubuntu rocks! :)
JUST NEED TO MAKE SURE THE SECURITY ISSUES ARE SORTED OUT!:KS

I understand the security concerns after using windows.........It is almost a crime that MS does not fix these issue.  Linux has gotcha covered.  I do not run any kind of virus or antispyware software at all, nor a firewall program.  My switch (Linksys WRT54G router with DD-WRT firmware) is all the security I need.

---

### Post by TheFlamingBush on 2007-06-03
can i ask how i go about closing those ports then, please then cantor? :)

---

### Post by cantormath on 2007-06-03
> **TheFlamingBush said:**
> can i ask how i go about closing those ports then, please then cantor? :)

Well, if you are connected to a router, the best thing to do is to turn the firewall options on and block incoming requests.  That way, even if  "they"  try to connect, the router rejects the connection just because its coming from the outside.

To get those ports to close, the easiest way to go about it, assuming you dont need to file share or use a printer from that box is to turn the services for samba and cupsys off, System>Administration>Services.  However, both of those services require a password, and outside connections are gonna be blocked, assuming you enable the blockage from the router.

By the way, that care on your blog is crazy, is that yours? Pretty cool.

---

### Post by obimeister on 2007-06-03
[https://www.grc.com/x/ne.dll?bh0bkyd2]("https://www.grc.com/x/ne.dll?bh0bkyd2")

Check that link out. Click proceed and choose "All Service Ports" scan the page will tell you which ports are open. I personally use iptables straight from command line and have only few basic rules created. Got only ssh and https opened for outside world. My ssh gets hammered daily probably by some bot, but i have disabled root access and don't have any stupid usernames or passwords like test/test so they havent got in. Also atleast here is quite normal receive windows share hammering, probably because my isp gives ips with big mask and people have xp machines running without decent protection.

---

### Post by TheFlamingBush on 2007-06-03
thanks Cantor....... :)

the car isnt mine, but its more than feasible. I know of a few diferent ways to get your car up and running on Hydrogen..... ;)...have to be aware of rusting though, as the byproduct of combusting hydrogen is of course water vapour. just adjusting your timing to tdc, and with slightly higher ping plugs with a cng cylinder injection system is also an alternative!.... :)....beats paying for petrol!

thanks fo the info obi :)....it appears i am operating in a totally stealthy environment!.....great news, and the hits on firestarter have completely stopped! :)....happy days!

---

### Post by cantormath on 2007-06-03
figuring out iptables is a more sophisticated way of doing it, and a bit more proper.....

LOL, that site says:
[FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=-0][COLOR=#000080]**Your Internet port 139 does not appear to exist!** 
[SIZE=-1][COLOR=#404040]**One or more ports on this system are operating in FULL STEALTH MODE!** Standard Internet behavior requires port connection attempts to be answered with a success or refusal response. Therefore, only an attempt to connect to a nonexistent computer results in no response of either kind. **But YOUR computer has DELIBERATELY CHOSEN NOT TO RESPOND** (that's very cool!) which represents advanced computer and port stealthing capabilities. A machine configured in this fashion is well hardened to Internet NetBIOS attack and intrusion.[/COLOR][/SIZE][/COLOR][/SIZE][/FONT]
[FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=-0][COLOR=#000080]**Unable to connect with NetBIOS to your computer.**
[SIZE=-1][COLOR=#404040]All attempts to get **any** information from your computer have **FAILED**. (This is **very** uncommon for a Windows networking-based PC.) Relative to vulnerabilities from Windows networking, this computer appears to be **VERY SECURE** since it is **NOT exposing ANY** of its internal NetBIOS networking protocol over the Internet.

How did you test?
[/COLOR][/SIZE][/COLOR][/SIZE][/FONT]
Glad I could help.

---

### Post by TheFlamingBush on 2007-06-03
ive done as you suggested cantor, and closed the samba and printsys.......when i scan with nmap now i see that all ports are now closed! 

feeling a little more secure! :)

---

### Post by TheFlamingBush on 2007-06-06
this situation is totaly out of control!...........im being hit incessently.......my system was compromised about 10 minutes ago. Im not exactly a dangerous surfer, it just appears that from the moment i come online with linux im being probed constantly.

Ive closed all the ports, and dont send any packets back when hit, but still it goes on......every bloody day its like this, and im getting a bit sick of it. i find myself being hit with kill commands, is linux just a breeding ground for hackers who practice on linux users? or what?

Ide post the firestarter log but the forum doesnt accept images of that length...

---

### Post by MJN on 2007-06-06
I think you will have to post some sort of 'evidence' of these compromises as from what you've described it sounds to me like you're maybe grabbing the wrong end of the stick and misunderstanding what's going on.
 
Of course I could be wrong, in which case we may be able to help you, but there are so many *'I've been hacked!'* posts appearing these days and by far the most turn out to be false alarms due to misunderstandings and jumping the gun. To justify spending time looking into the reported cases really needs something concrete to go on.
 
Mathew

---

### Post by MJN on 2007-06-06
(Thanks for the PM - you should post the details here really then we all benefit, hence I'll put the reply here also)
 
The ports you're receiving hits on are as a result of various bots (possibly collaborative nets) looking for (vulnerable) Windows machines to exploit. All quite 'normal'.
 
Port 1026, via UDP, is so-called 'Messenger Spam' - MS Messenger listens on this port to display certain types of pop-up messeges. Given the connection is via UDP, i.e. 'connectionless', it is trivially easy to spoof the source address and get away with it (as no response is required) so don't assume the source address is genuine... indeed assume it's fake given how much of this goes on (on behalf of my employer I receive a couple of e-mails a day complaining that we're attacking their systems - and this is from supposed security 'experts'!).
 
If you haven't got MS Messenger running then you've got nothing to worry about.
 
Port 2967 probes over TCP are indicitive of attempted Symantec exploitation - again if you don't use it you have no worries unless the rate was so high as to cause a DoS. Further info available at [http://isc.sans.org/port.html?port=2967](http://isc.sans.org/port.html?port=2967)
 
As you've closed down all your non-required ports you should view these 'attacks' as little more than a pain in your logs, and a reminder that it's an unfriendly world out there.
 
So far these do not indicate compromises. However, you also mention 'being hit with kill commands' - what did you mean?
 
Mathew

---

### Post by TheFlamingBush on 2007-06-06
Thanks for the info Mathew........its very informative for a linux newbie like myself to get some info on some of the security stuff. Especially as coming from windows i am used to being super paranoid about hacks and various infiltrations. 

The kill command happened whilest i was searching a forum, i noticed that my desktop froze up, and then began to stutter, something familiar to windows users who have been infiltrated and had there systems hacked by some remote user. I tried to close my internet connection down, but no dice, and neither was any other process accesable or usable...it appeared as though the only thing i had any control over was the movement of the mouse, which was stuttering across the desktop..........i pulled the cable out of the laptop, and the system crashed after a small ikon box came up with a warning error: something like killall command syntax error.......or something like this, the comp then crashed proper and i had to reboot (offline, and run rootkit scans, and a virus scan).

i run a duel boot xp/ubuntu dapper machine, and although i dont use the doze that much, i still have a lot of valuable information on that partition which i wouldnt be too happy to lose, especially as its my work and income. I have plays, and screenplays, and books i have written on there, and if i cannot protect that info whilest using Ubuntu, ide rather not use it.......even though i would be very very sad to lose the use of such a great operating system. I far prefer Ubuntu to doze, but i game and work sometimes on doze and only have the one laptop.

is there no way to ensure this doesnt happen again..........im being probed almost constantly, and my worry is that if im hacked again then i could lose information that simply couldnt be replaced....bar a major ammount of work and the use of a huge library of backups.  Some of the info would be lost for ever i fear, like contacts and other colleagues work, some of whom are no longer with us......

---

### Post by MJN on 2007-06-06
> **TheFlamingBush said:**
> is there no way to ensure this doesnt happen again..........im being probed almost constantly, and my worry is that if im hacked again then i could lose information that simply couldnt be replaced....bar a major ammount of work and the use of a huge library of backups. Some of the info would be lost for ever i fear, like contacts and other colleagues work, some of whom are no longer with us......
 
Well that's just it, ensure *what* doesn't happen again? You're saying *hacked*, I'd prefer to call it *crashed* until I see any evidence to prove otherwise! If it is the former then we'd need info to support the theory so as to be able to manage it, if the latter then well the same thing really!
 
As for losing data forever, that's never going to happen given you've got a complete backup solution in place. ...Haven't you?
 
Mathew

---

### Post by TheFlamingBush on 2007-06-06
mat ive been running dapper for about a year i guess, all i was doing was visiting a site i go to almost every day for that same ammount of time, absolutely nothing else...........nothing. sure it might have crashed........but why after a year, completely out of the blue, whilest im taking hit after hit after hit on my firewall????....thats not making sence to me, dapper is one of the most stable platforms i have ever run. i'll send you my logs and you can take a peak at my current hit rate....

this particular situation mirrored in no small way other occasions ive had on windows over the years, and always its been intruders..........always..... why would i think otherwise here. OK maybe it crashed for no reason what so ever, never has before, hasnt since my reboot, in fact everythings running sweet, except for the purpetual firewall hits that is,two of which firestarter classed as serious.  my firestarter seems to be constantly showing a red button with a black lightening strike, makes one wonder why they designed that blue button for the front end at all!

---

### Post by MJN on 2007-06-06
Having checked your logs you really need to put things into perspective - over that 2 hour period you got, what, 100 dropped packets? That really is nothing... sure you could do without but I wouldn't (and indeed am not with my connection) be overly concerned about that.

Your firewall is doing its job - dropping packets that are not explicitly allowed. Everything is working as it should be.

As for why your machine crashed it's impossible to say, but I would recommend against necessarily assuming it is in any way related.

How are you connected to the Internet? Is there a router between you and the cable/ADSL modem (if that's what you've got)? If so, is there a firewall on it that you could use to restrict forwarded ports with? This might make you sit more comfortably with the current situation...

Mathew

---

### Post by TheFlamingBush on 2007-06-06
Mat i dont have a router, but i think thats a very good suggestion. thankyou.

as for the dropped packets, if you think thats normal fair enough, but i dont ever recall having that kind of traffic before........mind you i take your point that everything is working as it should be and all the ports are closed. 

i think the router sounds like a very good idea to me.... thanks for your time and help mathew. :)

---

### Post by MJN on 2007-06-06
You're welcome. Hope my apparent distrust of your concerns wasn't too negative! ;)

Note that the router will simply shift the packet/port dropping point to before your machine hence same/similar effectiveness but less 'in your face'! Kind of like having people locked out by your garden gate as opposed to them banging at your door.... (note to self: that analogy needs a bit more work...)

Mathew

---

### Post by meman63 on 2007-06-07
One thing I would like to point out.

If Firestarter is running in your systems panel,then you are potentially exposing a root escalation.

Firestarter runs as root.Running a root app in user mode kinda negates the purpose of user mode,doesn't it?SUID should be sparsely used.

Just remember that with Windows the firewall usually drops packets without telling you,once you have it set where you want it.Firestarter is just a front-end for the behind-the-scenes firewall we all know as IP-Tables.Once you set the level in Firestarter,it should load your preferences every time you reboot,without having to load the icon in your panel.

By the way.I hope you have it set to only allow what you need,HTTP,HTTPS,FTP maybe ssh if you need it.Most home users will not.I would also suggest blocking some ICMP's.Especially echo-request as it's rather useless anyway for a home user.

Just My Two-Cents Worth,
                                      Meman63

P.S.   A router is a good idea,but is not perfect.It most likely will just be a stateful packet filter(meaning if an attempted connection did not originate from your box,it will be dropped).

---

### Post by Cheese Sandwich on 2007-06-07
> **cantormath said:**
> By the way, that care on your blog is crazy, is that yours? Pretty cool.

Ditto.

My dad did some work related to hydrogren advocacy in the rotary club:

[http://www.clean-air.org/](http://www.clean-air.org/)

---

