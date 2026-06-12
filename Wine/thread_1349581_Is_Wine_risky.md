---
title: "Is Wine risky??"
date: 2009-12-08
forum: Wine
---

### Post by rahilm on 2009-12-08
if i install wine, does that make me exposed to all the viruses they make for windows. I know they can't mess with the system. But they can sure annoy me.

---

### Post by gordintoronto on 2009-12-08
No, it's not Windows.

---

### Post by nini9012 on 2009-12-08
Nope, Wine isn't risky. It may be annoying to actually get a program to run, but you won't get viruses.

---

### Post by alex.rayu on 2009-12-08
Yes, wine is risky in some cases. It can successfully run some types of trojans that there are in the internet. Wine recognized that some viruses could be run on it since 2005 ([http://www.winehq.org/pipermail/wine-users/2005-January/016730.html](http://www.winehq.org/pipermail/wine-users/2005-January/016730.html)) Since then, Wine developed, and can now run more programs and more viruses.

Here is a post on Linux Today [http://www.linuxtoday.com/security/2009102600839SCHL](http://www.linuxtoday.com/security/2009102600839SCHL)

Just Google: wine + viruses - and you will find lots of reading on how it works and how to protect yourself from actually harming Linux with it.

---

### Post by steviefordi on 2009-12-08
I'm no expert but thinking logically, wine only runs programs you tell it to run by giving it:
```
wine program
```

from the command line. Windows viruses usually set themselves to start as a Windows service when booting up, they do this by editing the registry when they are installed. Wine doesn't start services on bootup so, although one may manage to install itself, it wouldn't start a malicious program that way.

Secondly, your important linux files should be protected by the permissions that are set on them (ie only root can write to certain directories). As long as you don't run wine a root, you should be ok. However, if you kicked off a virus with one of:

```
wine virus_program
wine programs_that_calls_virus_program
```

it could potentially cause a little havoc in your home directory.

---

### Post by joes7 on 2009-12-08
> **alex.rayu said:**
> Yes, wine is risky in some cases. It can successfully run some types of trojans that there are in the internet. Wine recognized that some viruses could be run on it since 2005 ([http://www.winehq.org/pipermail/wine-users/2005-January/016730.html](http://www.winehq.org/pipermail/wine-users/2005-January/016730.html)) Since then, Wine developed, and can now run more programs and more viruses.

Here is a post on Linux Today [http://www.linuxtoday.com/security/2009102600839SCHL](http://www.linuxtoday.com/security/2009102600839SCHL)

Just Google: wine + viruses - and you will find lots of reading on how it works and how to protect yourself from actually harming Linux with it.

Ermm wrong. Wine only runs programs one tells it to. Hence, there is no risk unless you run something plaged by viruses, for example 3rd party MSN addons.

---

### Post by Psumi on 2009-12-08
> **joes7 said:**
> Ermm wrong. Wine only runs programs one tells it to. Hence, there is no risk unless you run something plaged by viruses, for example 3rd party MSN addons.

So basically, the average uninformed windows user should be bashed for running something they normally use on windows without fear/problem on wine because it is as such?

Not everyone cares, if it works, it works.

So start bashing yourself, not others.

---

Before anyone runs ANYthing... remove Z: drive from winecfg. It's your filesystem, and is only there so you can run wine programs/windows programs everywhere. Removing this restricts programs to .wine/drive_c.

This should be put on the winehq homepage in big bold text so everyone does it.

---

### Post by alex.rayu on 2009-12-09
> **joes7 said:**
> Ermm wrong. Wine only runs programs one tells it to. Hence, there is no risk unless you run something plaged by viruses, for example 3rd party MSN addons.

You dont have to believe me. I gave you links. If you search you will fins links, threats descriptions, which viruses run and which don't. No point arguing with me when there is an abundance of official information on that.

---

### Post by jwbrase on 2009-12-09
> **alex.rayu said:**
> You dont have to believe me. I gave you links. If you search you will fins links, threats descriptions, which viruses run and which don't. No point arguing with me when there is an abundance of official information on that.

I think what he's arguing with is that said viruses are a threat. Sure, there are viruses out there that will run on Wine, but not all of them will, and even the ones that do are likely to be crippled. And even if they run perfectly, they can't do as much damage to a Linux+Wine System as they could on a Windows System, simply because Windows in in charge when it's running, but Wine is running on top of Linux.

Furthermore, the biggest security hole in Windows is IE, with its drive-by-download functionality. Considering that a Linux user is not likely to be browsing with IE through Wine, the threat is very much mitigated.

---

### Post by Psumi on 2009-12-09
> **jwbrase said:**
> I think what he's arguing with is that said viruses are a threat. Sure, there are viruses out there that will run on Wine, but not all of them will, and even the ones that do are likely to be crippled. And even if they run perfectly, they can't do as much damage to a Linux+Wine System as they could on a Windows System, simply because Windows in in charge when it's running, but Wine is running on top of Linux.

Furthermore, the biggest security hole in Windows is IE, with its drive-by-download functionality. Considering that a Linux user is not likely to be browsing with IE through Wine, the threat is very much mitigated.

Similarly with ReactOS, as there will be no browser support through explorer.exe in the upcoming explorer-new. Even if there was, it would use gecko.

---

### Post by jwbrase on 2009-12-09
In fact, I've never been able to get the Wine version of IE to run, and even if it did, I doubt they'd duplicate it down to the smallest vulnerability.

---

### Post by rahilm on 2009-12-09
I always keep some some viral .exe which i collected over past experiences handy. I may try them (one of them contains Win32:Virut , one of the reasons I am using Ubuntu today)

I think paying a visit to keygen, serials, crack sites (that's how i collected them) is a good experiment to begin with. I am going to try one in virtualbox.

---

### Post by Ferrat on 2009-12-09
Wine can run stuff if other wine stuff says - start that (it's its own environment, there for for ex launchers work with games, it can never go outside that environment because outside doesn't exist for WINE), but that means like surfing in a webbrowser via wine which seems pointless but it's possible for a virus or trojan to attack your WINE install, also most viruses uses exploites and flaws in windows code, since WINE is virgin code doing the same thing, the chances of the exact same flaw is extremely remote so viruses are more or less worthless under WINE, you can perhaps get them to run but the more advanced they are the less chance of them actually doing anything. 

Trojans could run under WINE but worst case just remove the .wine folder and restart WINE, mostly they will have the same problems as viruses and you should never run WINE as ROOT, so even if you are so unlucky that you get a working virus for ex it can't touch your system files cause Linux wont allow it, WINE itself has no real stops but Linux does, also WINE only sees what you tell it is there (in winecfg) so as long as you don't share any other disk there it can't do anything but to the .wine folder which as stated you can remove and just restart wine to get a new one

---

