---
title: "Does Windows need virus protection"
date: 2007-12-10
forum: Virtualisation
---

### Post by oneadvent on 2007-12-10
Does my virtualized windows need virus protection, or will my linux protect me?

(I am leaning toward it needs it)

---

### Post by lian1238 on 2007-12-10
I bet it does. My logic is that your virtualised windows is like another, separate computer connected through your Linux box. A virus, or of that sort, could find its way through to your windows.

---

### Post by lswest on 2007-12-10
yeah, you might want to install AVG Free AV, or Avast! anti-virus or some free virus scanner on it, if you plan on surfing the web with it, however if it does get a virus you can easily just remove it and make the vm again, and it won't affect any other files (in case you're worried about that)

---

### Post by oneadvent on 2007-12-10
So does the virtual windoze have a direct connection to the net? Anotherwords will my firewall help with malware/virus's?

---

### Post by oneadvent on 2007-12-10
> **lswest said:**
> yeah, you might want to install AVG Free AV, or Avast! anti-virus or some free virus scanner on it, if you plan on surfing the web with it, however if it does get a virus you can easily just remove it and make the vm again, and it won't affect any other files (in case you're worried about that)

I actually have a legal copy of windoze xp, and in the user agreement it says that it can be installed on another pc if it is completely removed from the first one, which I did. So I do not want to keep reinstalling it or I will have to call them for the activation code.

I guess its better to be safe than sorry with the virus protect.

---

### Post by Delvien on 2007-12-10
you can turn on Windows firewall and I suggest "ClamAV" its an open source virus scanner, very light weight and has the option to Right click "scan with ClamAV" in windows.

If you only connect to the host and have no internet access its really not needed, but i still recomend it. If you are connected to the internet with that Virtual Machine, a virus scanner is needed.

---

### Post by kackler on 2007-12-12
It's Windows, run AV.

---

### Post by oneadvent on 2007-12-13
I am running FreeAVG, because I am used to it and stubborn.

I decided it was better to be safe than sorry.

---

### Post by Shazaam on 2007-12-14
Yes a virtual Windows has the same vulnerabilities as a native install. So you need an av and some kind of firewall for your virtual Windows. There have been reports about guest o/s's infecting the host o/s so read up on security for whatever virtualization program that you have.

---

### Post by oneadvent on 2007-12-14
Thanks I did not know that.

That has to be one hell of a virus to infect the host, but something I will find out about.

Thanks for the tip and explanation.

Josh

---

### Post by dpj23 on 2007-12-14
Yes, your windows virtual machine needs anti-virus protection... However, if an infection does occur it will not spread to your host Linux machine... At that point you could clean or correct the problem with the Windows machine or delete it and build a new one...

One thought would be to build a virtual machine then take a snapshot of it for a restore image the go to town... If anything were to happen to it you could restore in less then 15 minutes...

---

### Post by jflaker on 2007-12-14
it is still windows regardless of how or where it runs.......AVGFree or Clam are ok and will do the job.  YOUR host system is safe, but windows will most likely get infected or turned into a drone........

---

### Post by perlluver on 2007-12-14
Off topic I think, but can you get a virus from an AVI file that you have saved?  And will that virus run in Linux?

edit: nevermind I am an Idiot....

---

