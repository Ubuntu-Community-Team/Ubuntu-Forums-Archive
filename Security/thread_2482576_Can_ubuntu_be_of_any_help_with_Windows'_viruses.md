---
title: "Can ubuntu be of any help with Windows' viruses?"
date: 2023-01-04
forum: Security
---

### Post by gipsyshadow on 2023-01-04
I use Ubuntu 18 and Windows 10 in dual boot. I mostly use Ubuntu, I use Windows rarely and only for some software. Sometimes I must analyze some .zip and .rar archives with .exe files and it happens that these archives contains other archives within them.
That said I wonder if it cold be better to install an antivirus on ubuntu and use it to scan these potentially dangerous archives rather than scanning them with windows system antivirus.
Imho the drawback of this solution is to keep on an antivirus running live in ubuntu and I don't want it.
What do you think and can you suggest me?

---

### Post by yetimon_64 on 2023-01-05
> **gipsyshadow said:**
> ..Imho the drawback of this solution is to keep on an antivirus running live in ubuntu and I don't want it...
Antivirus programs for Ubuntu/Linux are generally not used in the same manner as on Windows. Over the years I have used Avast for Linux and the native clamav scanner. Neither of these 2 use a "resident shield" or on access scanning like in Windows, both were "on demand" usage only. IIRC there are some A/V programs that can do on access scanning in Linux but I've never tried them; I suspect you may need to pay for such programs. I have never heard of a free (money wise) A/V application in Linux with such functionality.

When I was dual booting Windows and Linux years ago I found an on demand scanner like clamav was sufficient within Ubuntu. Your situation sounds a bit similar to what I was doing back then. Nowadays I don't install any A/V programs unless I intend to do file sharing with someone on Windows. I've found Linux itself really doesn't need one and would be a huge waste of resources if used with an on access (resident shield) type version. 

I'm not sure if Avast still have the free (needed to register it with an email address IIRC) Linux scanner, if they do that would probably be more reliable or easier to use than Clamav. Avast had a GUI when I last used it about 9 or 10 years ago. I've found Clamav to be a bit of nuisance to set up and use and sometimes throws up false positives; I don't think it has a GUI ie. it is used in the terminal. I had a good laugh on one installation when clamav declared 4 or 5 of its own installation files as viruses, but that was about 7 or 8 years ago; last time I installed it, it had improved (about 2018 or 2019).

Regards, yeti

---

### Post by lacrosby on 2023-01-26
You can and can't used a linux AV to look for window's viruses. If the antivirus as the signatures for inspecting windows based viruses, yes it can, not sure if ClamAV will pick up all infections since the signatures would be tailored for things that affect linux and not windows specific per say.

In my opinion, if you are wanting to to have something that can scan for both kinds of viruses you should look at something like a firewall with an antivirus/antibot built in. Depends on your environment and budget. Fortigate firewalls, embedded Check Point firewalls, Sophos.

---

### Post by kinstonian2 on 2023-01-28
Just send the .exe to [www.virustotal.com](www.virustotal.com) and they will scan it with over 70 different AV software.

---

### Post by monkeybrain20122 on 2023-01-28
No, you don't need antivirus on Linux, they scan for Windows virus and are not particularly good at it (clam is a piece of junk and resource hog) Security for .exe files and the likes should be taken care of at Windows' end as they are Windows' problems.

As a matter of fact I don't think antivirus are even that great on Windows, I set up Windows for my dad and all the free stuffs (Avast, Avira etc) are either bloated adware or nag ware that keeps nagging you to do this or that. Maybe the paid ones are better but dad is too cheap. :) I heard Windows now comes with its own antivirus (MS security or something like that ) and it gets some good reviews. Maybe those antivirus manufacturers are going to go out of business.

---

### Post by lacrosby on 2023-01-31
If you are looking for an antivirus, Sophos, ESET and Comondo virus protection suites. From a security engineer standpoint, you should always have some kind of antivirus in your environment. Setup a backup process, do it regularly... or even just make a cronjob.

---

### Post by TheFu on 2023-01-31
> **lacrosby said:**
> If you are looking for an antivirus, Sophos, ESET and Comondo virus protection suites. From a security engineer standpoint, you should always have some kind of antivirus in your environment. Setup a backup process, do it regularly... or even just make a cronjob.

The only time I run AV on Linux is when a contract requires it.  My E&O professional insurance requirements, which some clients require, was written by MSFT-centric people, for MS-Centric businesses.  

Seems my use patterns never cause viruses onto systems where I'm not actively seeking them, but I have so many security setup choices on my desktops which have been effective at avoiding all viruses.  
That isn't to say that my systems haven't been hacked.  I've been successfully hacked since the mid-1990s three times.  

The first time, I ran a 1 floppy version of Linux and connected it to the internet without changing all default passwords.

The 2nd time, I my BIND server was 3 months behind on patches.  End-users wouldn't run this, so a desktop user would never need to worry about it.

The 3rd time, I was at a security conference and had taken steps to ensure that if my system was hacked, it wouldn't matter.  I did a fresh Ubuntu install the day before the trip and didn't connect to any networks at the conference and didn't let my laptop out of my sight and nobody was close enough to touch it. I was up on a stage when it wasn't in my direct contact or off completely in my backpack.  I was helping to run a "capture the flag" contest when it happened.  Seems that Ubuntu had enabled bluetooth as part of the installation, which I never used and forgot to disable.  My laptop was hacked via bluetooth, I'm 100% positive.  Because it was a security conference, the hacker simply dropped a file into my HOME saying I'd been hacked.  I didn't risk it and reloaded the system completely that evening, this time disabling BT. The next day, it wasn't hacked again.

Don't enable bluetooth.  And don't trust wifi.  I only use wifi with a VPN, even at my own home.  They are still finding bugs in wifi implementations that have been around 20+ yrs ... and are in  the newest wifi standards.  Average people accept (or don't know) about these problems. After all, "everyone" uses BT and wifi, right?

At these security conferences, everyone comes expecting some nefarious hacking.  I don't take a smartphone, for example.  I have a $20 dumb phone for those conferences.  For a few years, there were 2 presentations - how to hack iOS and how to hack Android.  After seeing those, I was positive that I'd never put anything important on either of those systems.  Not email and certainly not any banking or financial apps.  Heck, I feel bad even having an airline app on my phone, since it is probably the least secure computer I have.  The most secure computer I have is a chromebook running stock ChromeOS.

---

### Post by DuckHook on 2023-01-31
You don't really need additional input from me about the actual security aspects of AV. I would only echo what others have said, which is, leave Windows defence to Windows AV apps. Linux and Windows are separate universes and mixing the two does not generally yield good results.

My recommendation is of a different sort:

You mention that you rarely use Windows and even then, only for some non&#8209;resource&#8209;intensive apps? If so, why not get rid of dual boot altogether and install Windows in a VM?

Benefits:

[LIST]
[*]Snapshots and rollbacks give great peace of mind. If you get infected, rolling back to a clean snapshot is essentially instant recovery.
[*]VMs are by their nature an additional layer of security because they are quite effective sandboxes. An app needs to be really cunning and sophisticated to escape from the confines of a VM.
[*]VMs are incredibly portable. It's very easy to move a VM over to another physical machine (along with all its customizations and data). Not so easy with a real install.
[*]
[/LIST]
Drawbacks:

[LIST]
[*]VMs will never run at native speeds and can perform poorly on resource&#8209;limited systems.
[*]You will need to check your Windows licensing terms.
[*]VMs are yet another thing to learn.
[/LIST]

---

### Post by TheFu on 2023-01-31
Completely unrelated, but Ubuntu 18.04 standard support ends in April, so you should be moving to either 20.04 or 22.04 at this point.
I have a few servers still to move myself.

---

