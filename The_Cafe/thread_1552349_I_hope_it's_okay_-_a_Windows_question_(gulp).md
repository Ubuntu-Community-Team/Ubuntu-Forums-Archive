---
title: "I *hope* it's okay - a Windows question (gulp)"
date: 2010-08-13
forum: The Cafe
---

### Post by anewguy on 2010-08-13
I hope nobody minds, but since these forums are so great for ubuntu, programming, etc., help, I thought I'd try posting this here.

I run Windows XP SP3 on my desktop.  I used to dual-boot but removed ubuntu due to a problem and haven't gotten time to reinstall it yet.  I do run 10.04 on my netbook though.

I have update my virus defs every night and have active scanning going for email, etc..  I have SpyBot Search and Destroy also.  I ran the updates for both and then ran them both, and they find nothing, but I have something strange happening and I'm not sure when it started.

About every 2 to 3 seconds, "like clockwork", ZoneAlarm shows a extremely quick burst of traffic and my wireless connection icon in the system tray also shows the traffic.  I've disabled "program updater", whatever it was, as well as Java updater, etc., so I didn't think there should be any traffic, especially if I'm not using a browser, email, etc..

I went so far as to also try the PCPitStop free malware scan. It noted 2 objects, but of course you don't know what until you buy it, but I wasn't concerned because my virus scanner shows 2 hidden objects, both from Microsoft.

Anyone have any idea what might be going on?  It almost looks like an old-fashioned keep-alive.

I'm running a Netgear WG311V3 PCI wireless adapter and connect to a Netgear Wireless router which is connected to a DSL line.

Thanks in advance!

Dave ;)

---

### Post by Mahngiel on 2010-08-13
Start menu > Run > msconfig

Under the processes tab to see what's running.
There are worms/viruses that utilize your connection to download and install themselves.
My wife just got 'Antivirus GT' on her work computer today, and I'm about to head over to clear it off.

---

### Post by ASchweitzer on 2010-08-13
No Dave.... it's not OK.

Have you tried something like wireshark to monitor traffic? See where the connections are going. A quick netstat command should tell you any open connections.

---

### Post by mendhak on 2010-08-13
Get yourself [wireshark]("http://www.wireshark.org/") and/or [fiddler]("http://www.fiddler2.com/fiddler2/") to have a look at what these bursts of traffic are. There are usually loads of processes or services running that often call home (for legit reasons) for updates or as part of their program flow. It may very well depend on what you've got installed. 

Note that Fiddler only does HTTP traffic.

---

### Post by Zorgoth on 2010-08-13
You expect us to know what to do about a problem that is either a) malware or b) a proprietary problem calling home?  We don't have to worry about problems like that :P

We found a the solution already :D

---

### Post by jimbop99 on 2010-08-13
Have you tried Malwarebytes. Excellent free program. Saved my systems may times.

---

### Post by wilee-nilee on 2010-08-13
Are you using XP in a limited account or admin?

---

### Post by chessnerd on 2010-08-13
Windows questions are fine. People here generally know more than people on Windows forums anyway.

That may or may not be a virus. 

It could just be that one of your programs running in the background is sending usage statistics. All it takes is leaving one checkbox checked and you have given an applications the permission to send "anonymous usage statistics". Also, a program may be phoning home.

Then again, it may be malware. For that -

+1 for Malwarebytes, it really is good. I've also heard good things about Ad-Aware, but I don't care for it. Spybot used to be good, but it isn't as reliable as it was in the 90s...

If you think that your current anti-virus is inadequate, you could try out a different free anti-virus. Even if you are paying for one now, you might want to switch to a free one. I've found AVG Free to be way better than Norton and McAfee (then again, having a virus is probably better than having Norton or McAfee).

AVG Free Edition (I use it on all my Windows installs, it's been solid and reliable in the 10+ years my family has used it)

avast! Free (I know a lot of people at my college who use it, they seem to like it)

Avira AntiVir Personal (recently it's gotten a lot of good press and it's more lightweight than the other two)

---

### Post by Old_Grey_Wolf on 2010-08-13
I would use wireshark to check it out just to be safe.

It appears you are using a wireless router or switch. Devices connected to the router/switch advertise their presence in the network. Computers, shared printers, and the router/switch itself all do this advertisement. The advertisements are small packets of 300 bytes or less. These advertisements are sent very frequently, measured in seconds.

As you can see in the attachment the router, printer, and computer advertisements come in or go out every few seconds for each device.

---

### Post by fatality_uk on 2010-08-13
Hi dave,

Old_Gray_Wolf is correct. WireShark is the best solution to see what's going in and out. Knoppix to view traff

---

### Post by anewguy on 2010-08-13
I saw the reply that included sharing - that got my attention.  Earlier this week I was trying to set up my Windows PC and my Ubuntu netbook to share an external hard drive (USB), an external DVD/RW (USB) and a printer all connected on the Windows machine.  You see, it's a known bug in the pre .35 kernel (which last I checked wasn't the main stream for Ubuntu yet) that it won't "hot mount" a USB drive (and sometimes things like USB flash drives) that aren't plugged in and turned on at boot time.  This is why I temporarily deleted Ubuntu from my desktop and left it on my netbook.

At any rate, it strikes me that this didn't start until I messed with the sharing.  I've had the sharing all turned back off, but I wonder if the network is searching for the workgroup (I changed it from MSHOME to a unique one for me).  My PC is the only thing that shows in network places.  So, I'm wondering about that.

In the mean time, I'm going to do the recommended malware scanner downloads and scans.  I'm already running Avira anit-virus with todays definitions (haven't paid for anti-virus in years - used to use AVG but can't remember what problem I had that stopped me using it for now.

Thanks for the input everyone!

Dave ;)

---

### Post by anewguy on 2010-08-13
Just tried to download Wireshark from their site using their download button for 32-bit Windows.  The attachment shows what my anti-virus thinks of it.

Any ideas?

Dave ;)

---

### Post by Johnsie on 2010-08-13
+1 for fiddler
+1 for malwarebytes
I also recommend Avast as an antivirus.

I use fiddler to monitor communcation between applications and the internet. It's really good for debugging web services and seeing how programs interact with the web ;-)

Mailwarebytes can get rid of some of the malware that others cant.

I would recommend using Avast! as an antivirus solution. It's free and pretty good. It also doesn't slow your computer down as much as AVG does. Definitely worth checking out.

---

### Post by ASchweitzer on 2010-08-13
> **anewguy said:**
> Just tried to download Wireshark from their site using their download button for 32-bit Windows.  The attachment shows what my anti-virus thinks of it.

Any ideas?

Dave ;)

Just trust it if you got it from their official site. It's a packet sniffer among other things, so I'm guessing it has code similar to some nastier malware.

On a side note, I've never used antivirus or antimalware on my windows installs. Mind you I re-installed every 6 months (running only Ubuntu now) out of habit and to keep performance up, but as long as you're smart about what you're downloading you shouldn't need antivirus. Firewall on the other hand, very much so.

---

### Post by anewguy on 2010-08-13
Installed the free version of malwarebytes, did the update to get newest defs, than ran the recommended quick scan (wasn't so quick!).  It didn't find anything.

I really am suspecting this is something left over from my work on sharing.  Network places still shows my shared documents instead of nothing - that is what makes me think it might be searching for the workgroup.

In the mean time, considering my virus checker says all okay, pcpitstop says all okay, SpyBot says all okay and now malwarebytes says all okay, I can only assume that...."all okay"!

If I find something that let's me know what's going on I'll post it.  

Thanks again!

Dave ;)

---

### Post by anewguy on 2010-08-14
Okay, now this has me a little worried.  I may have found something:

    A couple of months ago when I got my netbook I wanted to add its MAC to the list in the router since I use MAC filtering.  Well, I couldn't get the admin port for the router to ever come up.

    Today, while trying to follow some instructions so I could share some of my Windows desktop stuff with my Ubuntu netbook, I found out that somehow the router had reset the range of IP addresses from 192. to 10.  This let me know that for some reason the admin port was no longer 192.x.x.x, but 10.0.0.1.  When I got into the router, I found that the internet port IP address was at 192.x.x.x.  My IP address is supposed to be assigned by the ISP (Netgear wireless PCI card to Netgear wireless router to DSL modem [Juno - it's my brother inlaw's connection - I supplied the wireless so now I get to use it instead of dialup]).  I would have thought that address would have been something other than 192.xxxxxx.  This makes me wonder - even though I have WPA2-aes/tkip (I *think* that's what I set it up to on the router) with a password and with MAC filtering, is there someway someone has hijacked the incoming DSL connection?

Thanks in advance!

Dave ;)

---

### Post by neu5eeCh on 2010-08-14
Whew. I'm so glad I've switched over to Linux. I'm so glad all that crap is behind me.

I recall days like that. In similar situations the first thing I did was to install a good firewall. Set the firewall to block *all* traffic in and out that doesn't get approval first. Eventually, if malware is trying to access the web, you'll catch it. Try that if wireshark doesn't work for you.

---

### Post by anewguy on 2010-08-14
As mentioned in a previous post, along with the screen image attachment, my anti-virus (Avira) traps this at download and will *not* let me download it.

Sometimes I think people are missing that I am running Ubuntu on my netbook, and as mentioned earlier it was on my desktop until the kernel bug which causes hot-swap devices not to mount.  When kernel .35 becomes the default ubuntu kernel (supposedly that kernel fixed the problem), I will be back to dual-boot.  

So, I already know about the lack of headaches with Ubuntu, but I really want now is to find out if I'm in "trouble" and if so, by how much.

Thanks!

Dave ;)

---

### Post by anewguy on 2010-08-14
Downloaded and tried fiddler.  I have no idea what I should be even looking for in it, but did note that the 3 things that showed were either zonealarm or fiddler itself.  Nothing seemed to indicate the on/off traffic pattern.  I noted that fiddler is for http traffic - what if it's something different?

Dave

---

### Post by anewguy on 2010-08-14
> **Zorgoth said:**
> You expect us to know what to do about a problem that is either a) malware or b) a proprietary problem calling home?  We don't have to worry about problems like that :P

We found a the solution already :D

See my opening post - look for ubuntu.  Any helpful suggestions?

---

