---
title: "Windows Viruses in WINE"
date: 2012-02-29
forum: Security
---

### Post by helpme222 on 2012-02-29
Hi, I was wondering, if I install WINE would this somehow allow windows malware to infect my linux system?

And lets say I insert an infected usb stick into my linux laptop, could the virus from the stick somehow infect my linux laptop? Because sometimes I insert potentially infected usb sticks into my laptop (for work).

---

### Post by ld.4lpha on 2012-03-01
Short answer - yes.

Longer answer - I'd go so far to say that there's likely nothing with this functionality in the wild, but always assume your machine can be infected.

---

### Post by helpme222 on 2012-03-01
The only thing I plan on executing in it is an application from a cdrom. 

Let me clarify the question; by having installed WINE does this somehow allow windows viruses to run without my knowledge off of a usb stick?

---

### Post by jerome1232 on 2012-03-01
no, since wine doesn't arbitrarily start running every executable on a flash stick when you insert it.

If you manually ran a trojan than sure, it might do something.

---

### Post by ld.4lpha on 2012-03-01
Chances are you're fine.  But I wouldn't say categorically "not possible."  After all, by virtue of their character, vulnerabilities are unknown until exploited.  

You need to determine if the chance of infection (which is admittedly quite small) is acceptable given your particular risk tolerance.

---

### Post by jerome1232 on 2012-03-01
> **ld.4lpha said:**
> Chances are you're fine.  But I wouldn't say categorically "not possible."  After all, by virtue of their character, vulnerabilities are unknown until exploited.  

You need to determine if the chance of infection (which is admittedly quite small) is acceptable given your particular risk tolerance.

Without the virus specifically targeting a linux platform running wine, I don't think it's possible to get infected from merely plugging in a usb stick. Ubuntu would have to autorun a linux script or an exploit that targeted linux specifically which in turn exploited wine.

---

### Post by helpme222 on 2012-03-01
> **jerome1232 said:**
> Without the virus specifically targeting a linux platform running wine, I don't think it's possible to get infected from merely plugging in a usb stick. Ubuntu would have to autorun a linux script or an exploit that targeted linux specifically which in turn exploited wine.
Does opensuse have an autoscript?

---

### Post by jerome1232 on 2012-03-01
> **helpme222 said:**
> Does opensuse have an autoscript?

Yes, it's a function of your DE, both Gnome and KDE have facilities for autoruning scripts when removable media is inserted. I believe both can be deactivated although the exact method escapes me.

---

### Post by helpme222 on 2012-03-01
> **jerome1232 said:**
> Yes, it's a function of your DE, both Gnome and KDE have facilities for autoruning scripts when removable media is inserted. I believe both can be deactivated although the exact method escapes me.
I will look into deactivating it. But if I insert a usb stick, it wouldn't automatically execute a virus would it?

Also, I had another security question, is it possible to infect a usb stick and the viruses files remain hidden?

---

### Post by jerome1232 on 2012-03-01
I would contend that anything may be possible, not many things are plausible however.

---

### Post by 0011235813 on 2012-03-03
Wine basically creates a false C drive. That program will only be able to run in that C drive, so it probably won't be able to do much. The only feasible way would be if you ran wine as root, but even then, many viruses still wouldn't work. But on a side note, clamscan can scan for the majority of Windows viruses, why not just scan it first? The command is:
```
 clamscan <location>
```
which would scan the files in the location, like /dev/sdba1 for example, or /media/sdba3. Example:
```
<username>@<computername>: ~$ clamscan /dev/sdba1
<snip>
Scan Results
__ ___
Known viruses: 1152090
Engine version: 0.97.3
Scanned directories: 1
Scanned files: 48
Infected files: 0
Total errors: 1
Data scanned: 65.62 MB
Data read: 1406.25 MB (ratio 0.05:1)
Time: 24.739 sec (0 m 24 s)

```
EDIT: There is also a graphical program that does this called Clamtk Virus Scanner, which is available in the repositories.

---

### Post by Dangertux on 2012-03-03
Actually its quite trivial to impact linux if you can gain code execution in wine.

I've demoed this before and it essentially works because wine is not contained the way people seem to think it is, it is merely an interpreter to translate system calls into linux terms.

Demo 1
 [http://dangertux.wordpress.com/2011/09/17/the-truth-about-windows-malware-wine-and-ubuntu/](http://dangertux.wordpress.com/2011/09/17/the-truth-about-windows-malware-wine-and-ubuntu/)

And 2
 [http://dangertux.wordpress.com/2011/10/20/breaking-down-the-barrier-all-you-do-is-hurt-me/](http://dangertux.wordpress.com/2011/10/20/breaking-down-the-barrier-all-you-do-is-hurt-me/)

---

### Post by jerome1232 on 2012-03-03
> **Dangertux said:**
> Actually its quite trivial to impact linux if you can gain code execution in wine.

I've demoed this before and it essentially works because wine is not contained the way people seem to think it is, it is merely an interpreter to translate system calls into linux terms.

Demo 1
 [http://dangertux.wordpress.com/2011/09/17/the-truth-about-windows-malware-wine-and-ubuntu/](http://dangertux.wordpress.com/2011/09/17/the-truth-about-windows-malware-wine-and-ubuntu/)

And 2
 [http://dangertux.wordpress.com/2011/10/20/breaking-down-the-barrier-all-you-do-is-hurt-me/](http://dangertux.wordpress.com/2011/10/20/breaking-down-the-barrier-all-you-do-is-hurt-me/)

All I see is you demonstrating wine could run a trojan, which no one is questioning. I think it's rather obvious that could happen. I also don't understand what your trying to say about the home folder encryption.... when encryption is unlocked it's not protecting anything, it's only when the user is logged out that the encryption will be protecting files...

I did like the bit about app armor (I really need to get around to messing with that)

---

### Post by Dangertux on 2012-03-03
> **jerome1232 said:**
> All I see is you demonstrating wine could run a trojan, which no one is questioning. I think it's rather obvious that could happen. I also don't understand what your trying to say about the home folder encryption.... when encryption is unlocked it's not protecting anything, it's only when the user is logged out that the encryption will be protecting files...

I did like the bit about app armor (I really need to get around to messing with that)

You are correct my point was to demonstrate that the host linux system os accessible frpm within wine using windows code nothing more

---

### Post by inf1nity on 2012-03-03
No it won't. Unless you have some fancy utility installed on your system that resembles windows' autorun feature.

As for the the hidden virus files, if the file starts with a ".", then it will be hidden, and could infect a windows PC. 
For example-
I write a virus for windows. Using windows, i set its attributes to hidden and i include a "." in the beggining of its name.
Now- Neither Windows nor Linux users can see the file(with their default options). I also include a ".ini" file in the drive which instructs Windows to run the program on inserting the pen drive. This way I could infect a windows PC, if not yours..!!

---

### Post by 0011235813 on 2012-03-03
> **Dangertux said:**
> You are correct my point was to demonstrate that the host linux system os accessible frpm within wine using windows code nothing more

some programs in wine work, others don't. Same with malware. In any case, the malware won't do anything to the root owned folders, and it's always good practice to scan something if you are unsure of it's trustworthiness.

---

### Post by jerome1232 on 2012-03-03
> **kaustbh said:**
> No it won't. Unless you have some fancy utility installed on your system that resembles windows' autorun feature.


Actually, both Gnome and KDE do have an autorun facility by default, although it's for linux scripts. Create a autorun.sh (maybe .autorun.sh I can't remember atm which one, make it do something simple like call gedit) in the root of a usb drive then plug it in.

---

### Post by 0011235813 on 2012-03-03
> **jerome1232 said:**
> Actually, both Gnome and KDE do have an autorun facility by default, although it's for linux scripts. Create a autorun.sh (maybe .autorun.sh I can't remember atm which one, make it do something simple like call gedit) in the root of a usb drive then plug it in.

Yeah but they don't run it as root do they?

---

