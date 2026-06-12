---
title: "My Computer has been Hacked/Monitored; Help!"
date: 2011-03-22
forum: Security
---

### Post by tunknown31 on 2011-03-22
Hi, my computer has been surely hacked for at least more than two months; my private information are being hacked and spread around! I initally used Windows Vista and I had the firewall off and no antivirus software. When I realized that my OS had been hacked, I began turning my firewall on and installing security softwares, but nothing stopped the hack.
 
Yesterday, I erased all my partitions and installed Ubuntu 10.10. I installed rkhunter and a firewall. I changed my static IP adress, at least for the sake of knowledge, to another one, then I got disconnected since my router only allows my old IP.
 
When I'm about to write my admin password, I disconnect from the network. I've scanned my system using rkhunter, and the result is a list of 30 suspicious files!
 
Can I adjust my router in a way that it can allow any IP adress? If yes, can I have a non-static IP adress? How to prevent the hacking in the first place? However, I believe, I don't know yet, that my Ubuntu has also been hacked...
 
Dude, I need a professional help! If I can't get rid of the hacker(s), then I should permanently disconnect from internet and find another way to receive information anonymously through the internet.

---

### Post by falko on 2011-03-22
Your public IP is allocated by your provider, so you have no influence on it (unless you have more than one IP).

Please make sure that your router's firewall is on.

What makes you think that your Ubuntu got hacked as well?

In addition to rkhunter, you might also want to run chkroootkit.

---

### Post by rookcifer on 2011-03-22
Calm down.  What has most likely happened in rkhunter is throwing false positives as it always does.  You most probably have not had Ubuntu cracked.  Do you have any other reason to believe so other than rkhunter?

---

### Post by bodhi.zazen on 2011-03-22
rkhunter (and other tools) are notorious for false positives.

Read the stickies, drink some tea, and relax.

---

### Post by Dire_Devourer on 2011-03-22
Execute the command: sudo rkhunter --propupd

When you do a sudo apt-get update followed with a sudo apt-get upgrade rkhunter normally has a mini spas attack because loads of files have had there properties & signatures change.

Unless you can see a Rootkit coming up then its highly unlikely that you've been hacked and even then that can sometimes be a false positive. It sounds to me like you just forgot to do a property update!

Try that first then re-run rkhunter with sudo rkhunter -c and you'll see all the bad stuff has gone away, because it was never there in the first place.

It's very easy to panic un-necessarily in such scenarios god knows I've seen it happen often enough... When I used Windows 98SE back in the day when it was all the rage getting hacked was almost a daily occurrence, other family members have all had the same negative experiance and guess what, I'm the only smart cookie in the family that actually uses Ubuntu because I know it's virtually un-hackable. If all the hard-core hackers out there are using Linux then it stands to reason Linux is the daddy!

Notice that hacker can have negative connotations the word you want is cracker, ie: someone cracked your security. Hackers as a rule tend to make stuff, it's the bad element they (we) refer to as crackers that come along and break it afterwards.

Although if I was going to be totally honest I would say: Unix is the Daddy, Linux is the Offspring & Windows is something thats just unsavory and doomed to failure!

---

### Post by SeijiSensei on 2011-03-22
> **tunknown31 said:**
> Hi, my computer has been surely hacked for at least more than two months; my private information are being hacked and spread around! I initally used Windows Vista and I had the firewall off and no antivirus software. When I realized that my OS had been hacked, I began turning my firewall on and installing security softwares, but nothing stopped the hack.

I'm guessing that whatever happened occurred then.  It seems more likely that your passwords were sniffed or even exported off your machine by some form of Windows malwere.  Did you use this computer in open wifi settings like coffee shops or an airport?  Did you log into a site in one of those places that doesn't use HTTPS?

If you just installed a fresh version of Ubuntu, there's really no reason to believe that installation has already been hacked, regardless of what rkhunter might tell you.  Hacking into Linux isn't for novices, and it's very very unlikely it would have happened in just a day or two.

I presume you've changed all your passwords already, yes?

---

### Post by msandoy on 2011-03-22
I hope you have a new username and a secure password on your new and shiny Ubuntu install. If your windows was compromized, the offender has all the old user info.
Regarding setting up your router for automatic IP distribution, you have to give us some more info, like make and model of router. I have not seen yet a router without this capability.
A clean install of Ubuntu does not have any servers listening for incomming traffic, so your computer should be safe for now.

---

### Post by JRIDE on 2011-03-23
I have wiped and re-written my entire HD after being hacked and have re-installed several times and still getting malicious code. So I would be cautious. See my thread. Help if possible.

---

### Post by Dire_Devourer on 2011-03-23
JRIDE I looked at your thread in question and yes, you are correct:

The following mean nothing:

Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]

Those two warnings are standard even on my copy of Ubuntu 10:10 - I get them and I know more about hacking per-say than most people because when I was younger and nieve it was the profession I aspired to learn.

The files in /dev are in fact caused by Pulse Audio which you need as without it you would have no system sounds and even microsoft windows has hidden files & directories so is it so surprising to see that warning churn up?! Nope!

If you had done the following command: sudo cat /var/log/rkhunter.log you would have been able to see this by reading the log file for yourself. Needlessly formatting your hard-disk is no way to combat someone cracking your security. What you do is perform a complete system HALT and then remove your system from the on-line world & Internet then you would mirror your entire hard-disk and send it away to the forensic labs and try to figure out what went wrong and where. But in your case forgive my being blunt but it would seem your imagination is seeing ghouls and ghosts where none exist, all because some idiot on IRC told you "yeah dude, we're gonna HaXoR Jo0!!"

The fact that your Windows Box went down is a given, in another thread of my own I extrapolate on why windows security is a pile of sh** with an example of someones windows getting screwed over. I have to agree whole heartedly with the advice you've already heard.

> **rookcifer said:**
> The fact that you have formatted and reinstalled Ubuntu numerous times  and still think you are hacked is what is telling me that you were not  compromised but are simply being paranoid.  If the **entire** drive  has been formatted there is no way a hacker can maintain access between  installs.  And since Ubuntu comes with no listening ports, the hacker  would have to be superman to "instantly" hack you again.  Something like  this would require physical access. The chances of suddenly getting a rootkit after just installing Ubuntu  is really about 0.  Again, rootkit scanners are not reliable.  Do a  search on the forum -- there are tons of threads where people think they  were "hacked" because rkhunter gives false positives.  This is why I  detest rkhunter.  Too many Windows converts come to Linux thinking that  security = a virus scanner.  That's not the way it works here.   Virus/rootkit scanners are worthless.

On a plus note if you keep up that drive re-formatting business your hard-disk will eventually fail and then it will really be a mute point of being hacked or not, because with each re-format your doing more damage by taxing that HDD than an attacker could ever hope to do. /me *head-desk* ](*,)

@JRIDE: Can you tell me how many times you have reformatted your HDD && which IRC server it was you met these "Hackers" on???

I only ask because I would like to meet the people that pulled off such an epic feat of Social Engineering on you (they really worked a number on you lad!) to the point where you now see them crawling out of every nook, cranny and crevice with such abject uncontrollable fear... "The hackers are all out to get me - gibber, gasp!"

It would be extremely helpful if you could remember which channel (chat room) you where in and which nick (nick-name) or handle, said they where going to "hack" you prior to having it actually happen. I only ask as I know a few of them...

:lolflag: (Probably not helping to cure your paranoia by re-enforcing your opinion that the hackers are everywhere!)

---

### Post by tunknown31 on 2011-03-23
> **falko said:**
> Your public IP is allocated by your provider, so you have no influence on it (unless you have more than one IP).
Please make sure that your router's firewall is on.
 Is the public IP the WAN IP? My router According to [http://whatismyipaddress.com/](http://whatismyipaddress.com/), my IP is dynamic. Accessing my router's firewall settings, Address Restricted is checked for UDP Endpoint Filtering; although there is another option that is Port And Address Restricted; anti-spoof checking is also disabled. I don't clearly understand all the settings concerning firewall.
 > **rookcifer said:**
> Do you have any other reason to believe so other than rkhunter? I actually don't know whether it's been hacked or not. My Windows had been hacked to the point where anti-virus software and firewall seemed useless. How to be sure whether the router has been hacked or not? 
> **bodhi.zazen said:**
> Read the stickies, drink some tea, and relax. :)

> **Dire_Devourer said:**
> It sounds to me like you just forgot to do a property update! How to do a proper update? I've done by typing: sudo apt-get install update, and afterwards I upgrade.

> **Dire_Devourer said:**
> Try that first then re-run rkhunter with sudo rkhunter -c and you'll see all the bad stuff has gone away, because it was never there in the first place.
The warnings are gone after executing: sudo rkhunter --propupd.

> **SeijiSensei said:**
> I'm guessing that whatever happened occurred then.  It seems more likely that your passwords were sniffed or even exported off your machine by some form of Windows malwere.  Did you use this computer in open wifi settings like coffee shops or an airport?  Did you log into a site in one of those places that doesn't use HTTPS? It's my home computer. In the beginning, I had my firewall off and no security software; I'm often confident in surfing websites, but the hacker knows me; the hacker has not chosen my IP randomly.

> **SeijiSensei said:**
> I presume you've changed all your passwords already, yes?
My system's root password is different. I did reset my router today and changed its password too.

> **msandoy said:**
> Regarding setting up your router for automatic  IP distribution, you have to give us some more info, like make and model  of router.
Dude, it's around 2 am right now; I look at that tomorrow! There are three computers connected to that router.

> **msandoy said:**
> A clean install of Ubuntu does not have any  servers listening for incomming traffic, so your computer should be safe  for now.
How to make sure that there are no open ports?

---

### Post by msandoy on 2011-03-23
Since you have three computers connected to the same router, and at least one of them had no firewall and no security software at all, and running a compromized windows in your local network, I may assume that you need to check also the other two computers in your home for malware and other nasty software. But beginning with your Ubuntu, just type "sudo ufw enable" to enable the firewall at startup. Then all ports are closed.
You are talking about settings in the router regarding public IP and firewall settings. Do you have a combined router/DSL modem or do you have a traditional setup with a modem by itself connected to the wan port of a home router? Details of your setup makes diagnosing problems easier.
With ufw enabled you can relax and do some reading. Just don't get too paranoid while reading the security threads. :-)

---

### Post by Dire_Devourer on 2011-03-24
sudo apt-get install gufw and then you can be extra lazy and use the GUI.. ;) System --> Administration --> Firewall Configuration :)

---

### Post by tunknown31 on 2011-03-24
Some information about my router:
Connection Type :   DHCP Client
   Wireless Radio :   Enabled
   Wi-Fi Protected Setup :   Enabled/Configured
Security Mode: WPA/WPA2         - Personal
Copyright © 2004-2008 D-Link Systems, Inc.
   
   A cable is connected from my PC to the router.
> **msandoy said:**
> Do you have a combined router/DSL modem or do  you have a traditional setup with a modem by itself connected to the wan  port of a home router?
Where can I find the model and the info in question?

---

### Post by msandoy on 2011-03-24
Well, you have a D-Link router, Normally on the outside of the router itself it is written D-Link "then some info consisting of letters and numbers". On a sticker on the underside of the router, it will be specified maker and model.
Your computer is connected to the router with a cable, so not wireless. From the router, do you have any cable going into the wall or into another box?

---

### Post by bodhi.zazen on 2011-03-24
> **Dire_Devourer said:**
> sudo apt-get install gufw and then you can be extra lazy and use the GUI.. ;) System --> Administration --> Firewall Configuration :)

Off topic: If you want to be extra lazy

```
sudo ufw enable
```

Probably sufficient for the vast majority of desktop users and does not involve installing anything.

If you simply want to allow a port the ufw syntax is rather simple.

---

### Post by tunknown31 on 2011-03-31
> **msandoy said:**
> Well, you have a D-Link router, Normally on the outside of the router itself it is written D-Link "then some info consisting of letters and numbers". On a sticker on the underside of the router, it will be specified maker and model.
Your computer is connected to the router with a cable, so not wireless. From the router, do you have any cable going into the wall or into another box?
The model is DIR-655. My router is connected by a cable to another box given by the company.

---

### Post by tunknown31 on 2011-03-31
Yesterday, I scanned for TCP ports using nmap: sudo nmap -PN -p0-65535 [WanIP]
The detected ports' numbers were: 80 (http), 4444, 20005 and a few others (unknown). 

[http://www.auditmypc.com/port/tcp-port-4444.asp](http://www.auditmypc.com/port/tcp-port-4444.asp)
[http://www.auditmypc.com/port/tcp-port-20005.asp](http://www.auditmypc.com/port/tcp-port-20005.asp)

I then accessed to my router's settings, and blocked all those detected ports (except 80) and rebooted. First, how did 4444 and 20005 become listened?

Right now, I've blocked all the 65535 ports but except the port number 80.

---

### Post by spynappels on 2011-03-31
If you have UPnP set up on the router and use Skype/MSN/ICQ/.... these ports will be opened automatically by **U**niversal **P**lug **n** **P**lay functionality. Google the router name and model number to see if this "feature" is available on the router and how to check if it is enabled, often it is by default.

---

### Post by Zintha on 2011-04-01
I don't mean to... disturb the topic.
However, how do you actually know you were hacked at all?
I mean, theres a lot of panic and all but no sustenance to support you've been compromised.

How do you know your Windows install was hacked?

---

### Post by d3v1150m471c on 2011-04-01
First off, one of the most effective, and arguably most common attack vectors is to install a trojan or maleware on the intended victim. Installing and using a firewall afterwards is prettymuch useless at that point. The best thing you can do is completely wipe your harddrive and reinstall. Then, when you have a system you know is secure, before getting online and playing around you'll want to install your firewall and prevention measures. Also, if you have a router, use it, it'll help mitigate some connections, otherwise your system is a sitting duck just waiting to be hacked. You'll probably want to look into Firestarter, possibly PSAD. If you aren't using a service that listens on an open port Disable it.

```

sudo netstat -tlnp

```The above should show you what programs are on what port.

BTW, start keeping backups, dated backups in the event this occurs again you aren't losing all your data. 
here's an excellent HowTo: [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

Edit:
or you can use sockstat:
```

sudo apt-get install sockstat
man sockstat

```

---

