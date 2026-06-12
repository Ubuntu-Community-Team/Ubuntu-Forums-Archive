---
title: "using an Ubuntu PC to virus check/disinfect a Windows 7 PC"
date: 2010-03-22
forum: Security
---

### Post by Tom_ZeCat on 2010-03-22
A coworker of mine has a PC whose OS is an illegal copy of Windows 7 Ultimate that his kid probably got in a torrent.  I let him know that having a pirated OS was a bad idea both because it's illegal and because it would be a good way to have a root kit or some other virus that's so deeply embedded that that it's impossible to get rid of without formatting the hard drive and reinstalling the OS from a clean copy.  

He asked if if was a certainty that he has embedded malware, and I answered truthfully that it was not.  He wondered if I can check his machine out to determine what's the case.  That got my brain ticking.  It would be a waste of time running any antivirus product under his OS because there could be a rootkit or other malware at a deep level that hides itself from even the best antivirus product.  

Then I thought of scanning his computer with my Ubuntu PC.  I could remove his hard drive and then either install it as a secondary drive on my Ubuntu PC or put it into a hard drive enclosure as an external hard drive.  Then if I have an excellent antivirus product that runs under Linux and can find Windows-based viruses, I could scan his hard drive with no fear of infection to my PC.  It would also have the essential advantage not having to run his OS while scanning.

My questions: 
1. Is this a good strategy?  
2. Is there a Linux-based antivirus product that I should use for this?  I don't really feel that Clam or AVG Antivirus are the answer.  I'm honestly not very impressed with these products for Linux, but that hasn't mattered so much since Linux PCs hardly ever get viruses anyway.  I use Kapersky Internet Security on my Windows-based PC.  Maybe its Linux-based version is the one, and maybe they'll give me a discount as a Kapersky for Windows user.  However, if anyone thinks I should use something else, please speak up.  
3. Is this approach good enough to find the toughest kind of virus, the rootkit?

If this works well, I would have a kick-butt system for disinfecting Windows-based PCs without having to reformat and reinstall their OSes.

If I do find a rootkit or other malware on his computer, that will at least answer the question and let him know that he has to toss his illegal OS.  Even if I don't find anything, I'll still caution him that his PC is illegal in its current form.  Of course, it's his call and his risk.

---

### Post by jrssystemsnet on 2010-03-23
Kaspersky is a pretty good antivirus; its Linux version would be a reasonably good bet for the job.

I sometimes use Malwarebytes Anti-Malware running under WINE from a live USB drive to do what you're talking about, but it's not perfect - it has an unfortunate tendency to crash partway through the scan sometimes.  (It does not do that when running under Windows.)

---

### Post by dragos2 on 2010-03-23
Avira has a live cd than can boot and scan a computer:

[http://dlpro.antivir.com/package/rescue_system/common/en/rescue_system-common-en.exe](http://dlpro.antivir.com/package/rescue_system/common/en/rescue_system-common-en.exe)

---

### Post by dogdo on 2010-03-23
Even if you were to upload the iso image to [http://www.virustotal.com/](http://www.virustotal.com/) its highly possible that someone has created a virus that can elude all anti malware scanners-reactive technology can never keep up with this. Curious if the OP were to buy a legitimate copy of windows 7-how likely is it that the OEM provider might be already infected?   On a small side note i remember from my windows days about reading about a rootkit call 'Gromozon' that is particularly hard to detect with av tools...

---

### Post by justanothergreysky on 2010-03-24
It's unlikely that it's infected in such a way as to be completely impossible to find in Windows.

But if it is, it's very likely that you wouldn't be able to find out.

Just a matter of how paranoid you want to be...

Try running "Root Kit Revealer" from Microsoft on it.  That seems to be pretty good at at least giving a hint of the existence of many root-kits.

---

### Post by OpSecShellshock on 2010-03-24
I don't know that the chances of scanning from your Linux machine will be any better than scanning from Windows itself. For known threats, running the free MSRT and Rootkit Revealer from Microsoft at boot will identify anything it knows about. Anything it doesn't know about might be caught by running a third-party AV scanner also at boot (using an administrator account in safe mode). A clean scan under those circumstances still won't confirm a clean build, of course. Pretty much all you're going to gain by scanning from a separate drive running Linux is that the Windows drive will get scanned without having first loaded anything--which is what setting Windows up to do that itself first thing will also do. And anyway a lot of modern stealthy malware infects legitimate libraries and services, and will run completely in memory. In those cases there's nothing left to delete.

A bigger risk from running Windows unlicensed is that it won't be patched, at least not directly by Microsoft. That's bad enough in Windows itself, but will also apply to IE, where things get really risky.

---

### Post by jrssystemsnet on 2010-03-24
> **OpSecShellshock said:**
> I don't know that the chances of scanning from your Linux machine will be any better than scanning from Windows itself.

Scanning from another system is a LOT better than scanning from the possibly-infected system; you cannot trust any results an already infected system gives you.  Quis custodiet ipsos custodes?

I have seen quite a lot of machines show up squeaky-clean when asked to scan themselves with a given a/v product installed on that machine, but show up infected (and cleanable) when scanned with the SAME a/v product from a different system.

Note that booting from a live CD or USB key is effectively "a different system" for the purpose of this discussion.

---

### Post by rookcifer on 2010-03-25
> **Tom_ZeCat said:**
> 
He asked if if was a certainty that he has embedded malware, and I answered truthfully that it was not. 

One can tell whether the pirated .iso is legit or not before ever installing it.  All you have to do is compare the md5sum or SHA-1 hashes against the official MS published ones.

And with Windows 7, MS does indeed allow the non-licensed versions to receive security updates.  This didn't used to be the case, but MS has taken such a beating for allowing all the millions of pirated (and zombiefied) Chinese boxes to wreak havoc on the 'net that they changed their policy on this.

---

### Post by jrssystemsnet on 2010-03-25
> **rookcifer said:**
> One can tell whether the pirated .iso is legit or not before ever installing it.  All you have to do is compare the md5sum or SHA-1 hashes against the official MS published ones.

Except that the majority of the pirated Windows ISOs come bundled with other pirated Windows software right in the ISO, so there isn't a snowball's chance in Miami they'll match any hash published by anybody other than the ISO creator whether or not there's malware in it.

At the bare minimum, they've generally got to have a WGA crack built-in.

---

### Post by rookcifer on 2010-03-25
> **jrssystemsnet said:**
> Except that the majority of the pirated Windows ISOs come bundled with other pirated Windows software right in the ISO, so there isn't a snowball's chance in Miami they'll match any hash published by anybody other than the ISO creator whether or not there's malware in it.

At the bare minimum, they've generally got to have a WGA crack built-in.

Well the other apps are not usually included in the .iso itself.  It's more common to see the .iso and the keygens packed in an archive.  Once the archive is decompressed, the hash check against the .iso should work as usual.  I know because I checked a hash of a Pirate Bay Win 7 Ultimate .iso and it matched the hash on M$'s website. :D

---

### Post by nexes128 on 2010-03-30
You may want to consider AVG for linux it will allow you to scan a mounted windows drive and its free.

---

### Post by 98cwitr on 2010-03-30
avast for linux > *

[http://www.avast.com/linux-unix-edition#tab4](http://www.avast.com/linux-unix-edition#tab4)

---

### Post by fang0654 on 2010-03-31
Seconded for using avira.  I use Sysresccd with Avira's linux version installed.  I can usually clean up a Windows PC enough to the point that Malwarebytes can handle the rest.  The only caveat is to make sure you use quarantining as your default action - I've seen infected storage controller DLLs get deleted and rendered the OS unbootable.

---

