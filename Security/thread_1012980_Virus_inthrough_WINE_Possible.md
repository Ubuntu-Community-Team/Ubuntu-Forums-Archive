---
title: "Virus in/through WINE? Possible?"
date: 2008-12-16
forum: Security
---

### Post by TJCIB on 2008-12-16
Okay, so there is this "Facebook" virus going around.  I know Linux is not immune to viruses, but very difficult to infect...that is not my question here.

Hypothetical situation:
If one of my kids downloads an executable (.exe) intended to a be Windows virus, and manages to execute the file using WINE, would the imaginary WINE drives and files be infected and affected by the virus?  If so, could they potentially reach user files outside of the WINE drive?

System files wouldn't be an issue since you need to have root privileges to delete/modify, but could other files be at risk?

Just wondering.  One of my kids asked me this during our "don't accept rides, candy, or files from strangers" talks.

---

### Post by hovzio on 2008-12-16
I have read several articles on the subject. (sorry no links avail.) According to the articles most viri wont start but some very few are able to install themselves in the ~/.wine directory. All in all they were not able to do much, one example caused cpu usage to significantly rise, and as soon you to a kill wine this takes an end.. so in a whole its not really an issue, check out the wine directory periodically. Thats what I've read anyway, I am by no means an expert on subject viruses.

---

### Post by TJCIB on 2008-12-16
Yeah, my response was that WINE is a program, so as long as that program is not running, it can't do anything.

I wasn't sure if I was correct, but of course I had to save face in front of the kids =)

Normally I they wouldn't need wine, except they love playing DoTA with me =)

---

### Post by doobiest on 2008-12-16
No you don't have to worry about it damaging your Linux filesystem but it's true that it could spawn an emulated process that eats up CPU/MEM.

I'd say it's unlikely to happen since most exe's crash out of the box with wine anyway ;-)

Maybe if you had Internet Explorer running through wine you'd see an increased chance of malware.

---

### Post by Skripka on 2008-12-16
It is very unlikely.  Very unlikely.


I've run highly infected EXEs via Wine before-and barely noticed a bit more than some strange behaviour in the EXE....I found out later the EXE was a trojan carrier as I ran said EXE in my WinXP  setup on my 2nd drive---XP was dead and bluescreening in less than 5 minutes.

---

### Post by Hospadar on 2008-12-16
The short answer is no.

As their name suggests, Wine Is Not an Emulator, meaning it doesn't actually run a copy of windows.  Most viruses leech onto some other program in windows, or give themselves windows administrator privileges, and or add themselves to some autostart list somewhere.  Pretty much all of these things have no meaning in wine.

What wine does is modify executables at runtime to make their windows system calls go to wine-written libraries which immitate the function of those system calls.

For a virus to really infect you (let's say steal some important data) it would have to know that it was running in wine on top of a linux system and go way out of its way to set itself up very cleverly to make unix run it.  By this time, I expect a virus author would have just given up and written a virus native to linux.

I suppose maybe certain very simple viruses might run once when you first try to open them (shoot of some spam emails or something), so if you want some extra protection, you could get clamAV and scan yourself regularly.  You might want to read some guides on how to get that nicely integrated into ubuntu.

---

### Post by Tatty on 2008-12-16
[http://www.linux.com/articles/42031](http://www.linux.com/articles/42031)

Theoretically I could imagine how a virus may be able to affect your documents in your home folder if you link the wine Documents folders to your home folder.  
To get around this possibility simply go to winecfg and under the Desktop Integration tab, make sure all the folders point to a place which isnt under your /home.  You could always create a new folder /wineHome for example, and give that read/write permissions to the nessesary users.

Just thinking off the top of my head, I havent tried any of this.

---

### Post by TJCIB on 2008-12-16
As long as Warcraft 3 doesn't get messed up we'll be fine over here =)

Thanks for your quick responses.  You will make me look much smarter than I am when I go back with an updated answer.

---

### Post by gandaran on 2008-12-16
yes if you run the .exe file it'll install in wine but it won't do any arm to your computer, it just sits there doing nothing.
I have tried and played with some virus, they did install but you can easily spot them in wine, they didn't actually infect wine system files, they just installed in separate folders and won't be running, I tried running them without luck, wine just won't run those type of programs

---

### Post by cariboo on 2008-12-16
Have a look at this [thread]("http://ubuntuforums.org/showthread.php?t=72598"), where the OP actually installed viruses in Wine.

Jim

---

### Post by propagation_of_sound on 2008-12-16
I once had a virus in Windows that nearly killed the system. Fortunately it was deletable but the system has never been the same again. However, I (foolishly) opened that .exe in WINE to see if anything untoward happened. 

Nothing. 

WINE still ran perfectly after that and the whole system had no extra emulated processes (I checked)

---

### Post by bodhi.zazen on 2008-12-16
There have been rare reports of windows viruses running in wine.

Most do not : [http://www.linux.com/articles/42031](http://www.linux.com/articles/42031)

What you should do, IMO, is remove any links from ~/.wine to any location outside of ~/.wine and do not run wine as root.

This will restrict the damage to ~/.wine

In addition, report any such viruses to winehq and they will likely issue a patch.

---

### Post by donkyhotay on 2008-12-16
Possible? Well, anythings possible... Realistically though your pretty safe. Wine can be configured as to whether or not windows programs can see the entire file structure (It does by default) but remember unless your running as root you shouldn't have write access to your system files which means the worst a virus can do is mess up your personal documents. This is one reason native linux viruses don't do much damage and why script kiddies don't write viruses for linux.

---

### Post by Slim Odds on 2008-12-16
> **Hospadar said:**
> What wine does is modify executables at runtime to make their windows system calls go to wine-written libraries which immitate the function of those system calls.

WINE does **NOT** modify executables. WINE is an API that provides much of the same functionality as Windows.

---

### Post by ToasterThief on 2008-12-16
> **TJCIB said:**
> 
Hypothetical situation:
If one of my kids downloads an executable (.exe) intended to a be Windows virus, and manages to execute the file using WINE, would the imaginary WINE drives and files be infected and affected by the virus?


It's very unlikely but possibly. Keyloggers would be your greatest problem.

> **TJCIB said:**
> 
If so, could they potentially reach user files outside of the WINE drive?


No way.

Generally you won't take any damage from malware, if you're running Ubuntu - however, you could participate in spreading it from your pc, since you don't actively scan for Windows specific malicious software in the files you distribute. This is of course none of your problem though - It's a bug generated by Launchpad bug #1.

> **Hospadar said:**
> 
What wine does is modify executables at runtime to make their windows system calls go to wine-written libraries which immitate the function of those system calls.


What the fuc... are you talking about?

---

