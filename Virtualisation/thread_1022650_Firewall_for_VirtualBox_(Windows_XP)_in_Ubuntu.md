---
title: "Firewall for VirtualBox (Windows XP) in Ubuntu"
date: 2008-12-27
forum: Virtualisation
---

### Post by Dave_G on 2008-12-27
Hi

I have successfully installed Windows XP in VirtualBox on my Ubuntu PC; will i need to install an anti-virus and firewall for Windows XP in VirtualBox, or does Ubuntu's own built in firwall 'IPTables' cover the Windows XP that is running in the VirtualBox?

Many Thanks

---

### Post by Dedoimedo on 2008-12-27
You don't need a firewall, unless you're bridging the host network interface and running an external IP ... But if you're using NAT, you're ok.

But then, Windows XP built in firewall is fine.

Lastly, you don't need an anti-virus any more or less than you normally need it. Windows XP will be prone to anything you do. So if you tend to get infected a lot, it will get infected. If you know what you're doing, then you don't need an anti-virus.

Keep in mind that XP will suffer whatever fate you drop on it, be it installations, tweaks, browser addons etc ...

Dedoimedo

---

### Post by bodhi.zazen on 2008-12-27
NAT will act as your firewall and unless you are running a server on Windows you should use that over a bridged network connection.

Otherwise, treat you virtual windows install exactly as you would a physical installation.

My advice is to run antivirus and something for spyware.

---

### Post by Dave_G on 2008-12-28
Thanks for the response guys; i forgot that XP SP2 has a built in firewall, i'm really pleased with it as i could not get my TomTom Home to run in Wine and VirtualBox has helped me out.

---

### Post by thefish123 on 2008-12-29
> **bodhi.zazen said:**
> NAT will act as your firewall and unless you are running a server on Windows you should use that over a bridged network connection.

Otherwise, treat you virtual windows install exactly as you would a physical installation.

My advice is to run antivirus and something for spyware.
Yes, NAT will act as a firewall.  If you’re running in bridged mode your XP box will have an IP address that is visible to on the local network your Linux box is connected to.  This is likely undesirable in which case I would suggest turning on the XP firewall.
	
I do NOT recommend running anti-virus software.  It will slow your XP box down and is probably not necessary.  If you made it this far (downloaded and installed Ubuntu, installed VirtualBox and installed XP) you likely are not a computer idiot.  Just don’t download junk inside your XP box.  Make a backup of your virtual hard disk if you’re going to try something “risky”.

I have been running a real physical XP box since XP came out without antivirus software and have never once been infected.  The leading cause of computer virus infection is user behavior.

The Fish

---

### Post by Dedoimedo on 2008-12-29
thefish, we don't call windows users 'idiots' - they are merely computeristically challenged. And it is the average that defines the norm, so if you draw the normal distribution of average compute population/literacy, you'll definitely get a gaussian and we'll be at the far end - we're the freaks :)
Dedoimedo

---

### Post by Dave_G on 2008-12-30
TheFish, Windows XP is working fine in my XP VirtualBox, and have updated it to SP3 with no problems too.  Ubuntu is my only OS, but will use the XP Box for TomTom updates and to play the odd Football Manager game ;o)

---

### Post by solwic on 2008-12-30
> **Dave_G said:**
> TheFish, Windows XP is working fine in my XP VirtualBox, and have updated it to SP3 with no problems too.  Ubuntu is my only OS, but will use the XP Box for TomTom updates and to play the odd Football Manager game ;o)

I guess I'm one of the lucky ones.  I don't dual boot, I don't run Windows XP in VirtualBox, and I don't even use Wine.  I'm totally off the Micro-teat.  

It's wonderful.  :P  

(Of course, I understand for some that's not an option...I guess I'm just bragging.  :P)

---

### Post by solwic on 2008-12-30
> **bodhi.zazen said:**
> 
Otherwise, treat you virtual windows install exactly as you would a physical installation.

My advice is to run antivirus and something for spyware.

+1 to all that.  A virtual XP install can still get infected.  While I don't imagine it would harm your Ubuntu install, it could cause you to have to reinstall Windows in the VM.  

BTW, I love the name, Bodhi.   :)

---

### Post by howefield on 2008-12-30
> **jrock612 said:**
> A virtual XP install can still get infected.  While I don't imagine it would harm your Ubuntu install, it could cause you to have to reinstall Windows in the VM.

Creating a backup of your VM means a "reinstall" doesn't mean starting from scratch.
```
VBoxManage clonevdi source destination
```

eg, 
VBoxManage clonevdi ~/.VirtualBox/WindowsXP.vdi ~/WindowsXP_Backup.vdi

---

### Post by solwic on 2008-12-30
> **howefield said:**
> Creating a backup of your VM means a "reinstall" doesn't mean starting from scratch.
```
VBoxManage clonevdi source destination
```

eg, 
VBoxManage clonevdi ~/.VirtualBox/WindowsXP.vdi ~/WindowsXP_Backup.vdi

Or that.  :)  I'm a little out of practice here...I don't use Windows (with or without Virtualbox) anymore.  

But yeah, a backup of the .vdi would be good, too.  :)

---

### Post by thefish123 on 2008-12-30
> **Dedoimedo said:**
> thefish, we don't call windows users 'idiots' - they are merely computeristically challenged. And it is the average that defines the norm, so if you draw the normal distribution of average compute population/literacy, you'll definitely get a gaussian and we'll be at the far end - we're the freaks :)
DedoimedoHi Dedoimedo,

I think you misunderstood me.  I was not suggesting that Windows users are idiots.  In fact I appreciate your comment that they are not.  Many of them can do things I cannot (like fix a car, re-shingle a house, fix a broken toilet, bake a cake).  Being "computer literate" does not mean I do not need anyone else.  I was merely saying that this user (who is clearly more advanced then the average “got a virus” Windows user) is probably not that likely to get a virus infection under any OS.

Most viruses pray on inexperienced users and try to “trick” you into downloading them.  The idea that Windows is inherently riddled with holes simply isn't true.  I patch my SUSE 10.x boxes as often as I patch my Windows servers.  Patching is a fact of life.  Reality is most malware is invited in by the user.

One of the things I hate is religious style flame-wars over OS'es.  Really?!?!  I am an IT consultant and software developer for over 10 years.  I write and deploy high-level business applications using ASP.NET/MS-SQL.  Does that make me an "enemy" to my friends in the Linux world?  There is a time to use Linux and a time to use Windows and a good IT consultant knows about both (and other) options.  Ironically one of the things holding Linux back from being taken seriously by many "management types" is the irrational juvenile hatred toward anything Microsoft.  We really need to grow up and stop calling in "Micro$oft Windoze".

That being said I an wildly impressed with the professional polished appearance of Ubuntu.

Regards,
The Fish

---

