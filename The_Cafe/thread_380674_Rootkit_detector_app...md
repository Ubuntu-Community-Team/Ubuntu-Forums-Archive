---
title: "Rootkit detector app..?"
date: 2007-03-09
forum: The Cafe
---

### Post by billdotson on 2007-03-09
[http://www.microsoft.com/technet/sysinternals/utilities/RootkitRevealer.mspx]("http://www.microsoft.com/technet/sysinternals/utilities/RootkitRevealer.mspx")

So apparently this program was the first one to find the Sony rootkit.. should I use this on my Windows install?  Also.. I would like to use OSS virus and spyware software if there are any good candidates.

---

### Post by SeanTater on 2007-03-09
Linux is not in any need of Virus protection. There are no viruses  "in the wild" which infect Linux. If you are looking to stop Windows viruses, search for ClamAV. ClamAV works on Linux, but searches for Windows viruses, thus, you can scan your windows with it while running Linux. If you prefer running it windows, search for clamwin.  For rootkits, you can use chkrootkit, but it only checks linux, not Windows.

---

### Post by brianh57 on 2007-03-10
No Linux Viruses?  Not exactly true.  Linux is more secure than Windows and even MacOS for several reasons but if someone targets you individually, they will probably be able to find a weakness.

I think the best defense is an active defense.  By that I mean leave your personal computer off when you're not using it.  When it's on, monitor everything going in and out.  Don't worry about software because someone will find a way to get around that.  If you're running a server, monitor everything going in or out.  That's easier said than done.

---

### Post by SeanTater on 2007-03-10
<nitpick>
That is certainly true, but I don't think that qualifies as a virus. A Virus propagates without human intervention.

[http://dictionary.reference.com/browse/virus](http://dictionary.reference.com/browse/virus)
Definition 4 requires "self propagation"
</nitpick>

As opposed to the paranoid approach, this is most likely not a server. Monitoring will probably be best done with firestarter, if the user is particularly worried. Even among the hundreds of thousands of posters here, I have yet to see a post showing that a hacker "broke in". Even if it is possible, the odds against it are enormous..

---

### Post by brianh57 on 2007-03-10
Just becuase you're paranoid...

The whole idea of a rootkit is that the intruder leaves no traces.  Even in the system logs that monitor traffic in and out of the system.

---

### Post by joselin on 2007-03-10
To check the system looking for rootkits you can install both of the following:
chkrootkit - Checks for signs of rootkits on the local system
rkhunter - rootkit, backdoor, sniffer and exploit scanner

by typing:
```
sudo apt-get install chkrootkit rkhunter
```

---

### Post by brianh57 on 2007-03-10
This is a pretty good set of reasons why Linux is more secure than other OS'es [http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)

Basically, it's security through obscurity (or maybe more accurately security through diversity)

Someone almost has to target you individually to be successful and that's what I was getting at.

---

### Post by billdotson on 2007-03-10
yeah what I am saying is that I want to know if ClamWin and the RootKitRevealer v1.71 are good for use w/ Windows.  As I am planning to have a USB flash drive with security applications to use to check people's PCs when I am troubleshooting them.  That is why I also ask if there are any good OSS spyware/adware scanners and firewalls.  Please remember that these should be good enough for use where I use them to scan someones PC and get paid for it.  So I cannot have it not work right.

I use Windows and Ubuntu and I have never gotten a virus on my PC.. granted when I was a little kid I downloaded some software that got dad's infected but as long as I have had my own I have been virus free.  Spyware on the other hand.. I get 3 or 4 tracking cookies everytime I surf the net w/ FireFox and have to run the scanner before I go to sleep.  Generally though I only enable cookies if I need them to sign into a site.

---

