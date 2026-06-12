---
title: "chkrootkit output"
date: 2004-12-15
forum: Server Platforms
---

### Post by cacofonix on 2004-12-15
Im worried about a chkrootkit scan I just ran it is saying that eth0 has a packet sniffer on dhclient. Is this normal or is it something to be worried about?

```

eth0: PACKET SNIFFER(/sbin/dhclient3[4303])

```

thanks in advance

cacofonix

---

### Post by TamirEr on 2004-12-15
I get the same output...
However, I tried googling "chkrootkit packet sniffer dhclient" and i've found that it's probably a false alarm.
I guess that if you're still worried about using dhclient (which is handling traffic before almost everything and that's why chkrootkit detected it) you can set permanent IP adresses on your network...

---

### Post by cacofonix on 2004-12-15
Cheers I was hoping to hear that thanks for the help TamirEr :D

cacofonix

---

### Post by felixdzerzhinsky on 2004-12-21
I have also experienced false positives with chkrootkit.  I recommend getting rootkithunter from:

[http://www.rootkit.nl/projects/rootkit_hunter.html](http://www.rootkit.nl/projects/rootkit_hunter.html)

Follow the instructions to build from source then run rkhunter. 

If chkrootkit and rkhunter both give you the same result  then you've got something to worry about. Otherwise it is likely a false positive. There is still a possibility it is a new rootkit that has not beet put in the signature base. T

You also might want to install a file integrity checker such as AIDE or Tripwire which is available as a debian package through apt or as source from:

 [www.tripwire.org](www.tripwire.org)

Ideally tripwire should be installed BEFORE you connect to the net. Tripwire is a debian testing and unstable package.

AIDE (Advanced Intrusion Detection Environment) is an alternative to Tripwire. Ideally AIDE should also be installed BEFORE you connect to the net. It is available as a debian stable package.  

If rkhunter or chkrootkit come up with something you can run checks to see if your files have been manipulated. If they have been tampered with  you may well have a rootkit. Reinstall.

As an aside I don't think AIDE or Tripwire are on the installation CD. (I could be wrong about this. Typing this at work.)

I suspect it will be possible to securely install the packages using a knoppix live cd or maybe the ubuntu live cd also. Boot into the live CD and:

Knoppix hacks number 68 from O'Reilly (In a shell) *( I havn't tried this but will when I get home.)*

 **sudo mount o rw /dev/hda# /mnt/hda#** (replace # with the number of your root partition)

**sudo dpkg  --root /mnt/hda# -i *<package name>*** Package name insert aide or tripwire.

When you boot back into ubuntu  as root in a shell:

**dpkg-reconfigure *<package name>***


You could also install bastille this way. Great program for locking down your system. [www.bastille-linux.org](www.bastille-linux.org)

After all this all you need to do is keep your system patched with apt or synaptic and run whichever rootkit search program you choose and check your file integrity.
This may seem like a lot but compared to REALLY  locking down Win XP it is easy. 
You may want to dig up Maximum Linux Security or The Linux Security Cookbook from you library or bookstore.

Security is a process not a finished product or I am not paranoid everyone is against me.

---

### Post by ubuntu_demon on 2004-12-21
[QUOTE=felixdzerzhinsky]I have also experienced false positives with chkrootkit.  I recommend getting rootkithunter from:

[http://www.rootkit.nl/projects/rootkit_hunter.html](http://www.rootkit.nl/projects/rootkit_hunter.html)

Follow the instructions to build from source then run rkhunter. 

If chkrootkit and rkhunter both give you the same result  then you've got something to worry about. Otherwise it is likely a false positive. There is still a possibility it is a new rootkit that has not beet put in the signature base. T

You also might want to install a file integrity checker such as AIDE or Tripwire which is available as a debian package through apt or as source from:

 [www.tripwire.org](www.tripwire.org)

Ideally tripwire should be installed BEFORE you connect to the net. Tripwire is a debian testing and unstable package.

AIDE (Advanced Intrusion Detection Environment) is an alternative to Tripwire. Ideally AIDE should also be installed BEFORE you connect to the net. It is available as a debian stable package.  

If rkhunter or chkrootkit come up with something you can run checks to see if your files have been manipulated. If they have been tampered with  you may well have a rootkit. Reinstall.

As an aside I don't think AIDE or Tripwire are on the installation CD. (I could be wrong about this. Typing this at work.)

I suspect it will be possible to securely install the packages using a knoppix live cd or maybe the ubuntu live cd also. Boot into the live CD and:

Knoppix hacks number 68 from O'Reilly (In a shell) *( I havn't tried this but will when I get home.)*

 **sudo mount o rw /dev/hda# /mnt/hda#** (replace # with the number of your root partition)

**sudo dpkg  --root /mnt/hda# -i *<package name>*** Package name insert aide or tripwire.

When you boot back into ubuntu  as root in a shell:

**dpkg-reconfigure *<package name>***


You could also install bastille this way. Great program for locking down your system. [www.bastille-linux.org](www.bastille-linux.org)

After all this all you need to do is keep your system patched with apt or synaptic and run whichever rootkit search program you choose and check your file integrity.
This may seem like a lot but compared to REALLY  locking down Win XP it is easy. 
You may want to dig up Maximum Linux Security or The Linux Security Cookbook from you library or bookstore.

Security is a process not a finished product or I am not paranoid everyone is against me.[/QUOTE]

No rant intended.

I don't recommend any of this for average-desktop-users. The default installation is reasonably safe. 

It's nice for nerds,paranoid people and people who run servers or critical systems. 

see :
[http://www.ubuntuforums.org/showthread.php?t=7511](http://www.ubuntuforums.org/showthread.php?t=7511)

---

