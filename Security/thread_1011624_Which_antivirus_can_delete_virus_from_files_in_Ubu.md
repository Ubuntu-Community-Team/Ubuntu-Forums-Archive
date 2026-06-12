---
title: "Which antivirus can delete virus from files in Ubuntu?"
date: 2008-12-15
forum: Security
---

### Post by asaren on 2008-12-15
Hi,

Which antivirus can delete virus from files in Ubuntu?

Can avast do this?

My Ubuntu computer is connected to many Window computers in the network. Should i need to install antivirus on Ubuntu?

Thank you

---

### Post by HermanAB on 2008-12-15
You only need anti-virus on Ubuntu if you run an email or file server for the other machines.  In that case, use ClamAV.  Otherwise, don't worry about it.

---

### Post by Poyntz on 2008-12-15
[http://en.wikipedia.org/wiki/Computer_virus](http://en.wikipedia.org/wiki/Computer_virus) - You should do a bit of research on viruses
A virus that affects windows will probably not work for linux unless it is designed to infect specific locations that are installed on windows that may be installed on linux through programs like wine. 
Also, the necessity to bypass access to modification activities in linux makes viruses for linux very rare. ie, one would probably have to know the password you use for **sudo** to cause any real damage

---

### Post by Vantrax on 2008-12-15
> **Poyntz said:**
> [http://en.wikipedia.org/wiki/Computer_virus](http://en.wikipedia.org/wiki/Computer_virus) - You should do a bit of research on viruses
A virus that affects windows will probably not work for linux unless it is designed to infect specific locations that are installed on windows that may be installed on linux through programs like wine. 
Also, the necessity to bypass access to modification activities in linux makes viruses for linux very rare. ie, one would probably have to know the password you use for **sudo** to cause any real damage

Antivirus can be good if you want to scan attached storage, have something running under wine (its rare but can happen), or you have a dual boot system. 

ClamAV or Avast are the best two options ive seen.

---

### Post by wizard10000 on 2008-12-15
> **HermanAB said:**
> You only need anti-virus on Ubuntu if you run an email or file server for the other machines.

Or if you forward email to Windows machines, upload files to the internet or share stuff on removable media.

IM frequently less than HO it's each computer user's responsibility to insure their machine isn't a vector for hostile code - so I run an AV client on all my Linux boxes.

---

### Post by hyper_ch on 2008-12-15
> **wizard10000 said:**
> IM frequently less than HO it's each computer user's responsibility to insure their machine isn't a vector for hostile code - so I run an AV client on all my Linux boxes.

IMHO it's each computer user's responsability to insure that their machine doesn't get infected.

How likely is it that some users machine gets infected because YOU send him an email? How likely is it, that such a user's computers gets infected by a billion other peoples sending him emails?

---

### Post by Kevbert on 2008-12-15
Most 'linux' antivirus packages actually scan for Windows viruses. So unless you're emulating Windows in a Linux session you're wasting your time installing AV software. Most linux viruses are only theoretical at present.

---

### Post by Chayak on 2008-12-15
Malware isn't some mythical beast that waits to infect computers like the plauge or something.  It's simply software.  Malware takes a lot of different forms but just by virtue of running linux and with ubuntu's seperation of the root user from normal use gives you more protection than any anti-virus software out there.

To give you a blunt example my workstation has thousands of malware samples sitting on it.  My laptop that I'm on now has about fifty or so.  Why do I have them?  I'm a security researcher who specializes in malware analysis.  I do most of the work inside of virutal machines running windows then after I'm done I revert the virutal machine back to a clean snapshot.

I make a habit of telling people to surf the net through virutal machine.  When you're done revert it back to a clean state and you'll likely never have an issue with malware.

My workplace, outside of the lab where I work, does just that.  The base machines are Redhat linux and then you can open a Windows VM to work in.  If something happens, then no big deal as that image is nuked and a new one loaded.  IT loves it as it's saved them countless manhours and saved a lot of money that's gone to infrastructre upgrades rather than cleaning windows machines.

---

### Post by Kinstonian on 2008-12-15
> **Chayak said:**
> 

To give you a blunt example my workstation has thousands of malware samples sitting on it.  My laptop that I'm on now has about fifty or so.  Why do I have them?  I'm a security researcher who specializes in malware analysis.  I do most of the work inside of virutal machines running windows then after I'm done I revert the virutal machine back to a clean snapshot.


What do you do when malware is able to detect when it is running in a VM and modifies its behavior?  As I understand it, that's becoming more common and even an option in some binary packers.  I'm not a programmer so true code analysis isn't really an option...  I've thought about using a sandnet like [Truman](http://nsmwiki.org/Truman), but its only at v0.1 so I'll probably wait until the bugs are worked out.  It looks like it has potential though.

---

### Post by Chayak on 2008-12-15
> **Kinstonian said:**
> What do you do when malware is able to detect when it is running in a VM and modifies its behavior?  As I understand it, that's becoming more common and even an option in some binary packers.  I'm not a programmer so true code analysis isn't really an option...  I've thought about using a sandnet like [Truman](http://nsmwiki.org/Truman), but its only at v0.1 so I'll probably wait until the bugs are worked out.  It looks like it has potential though.

The majority of the stuff I see doesn't but normally if it detects a VM we'll try a couple of other virtualization methods, we'll open it in ollydbg and patch out the vm detection, or as a last resort we'll run it on a native machine.  There has been a time or two that we've had to do static only analysis with IDA which is time consuming.

---

