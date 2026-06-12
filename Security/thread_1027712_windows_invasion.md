---
title: "windows invasion"
date: 2009-01-01
forum: Security
---

### Post by bu2971x on 2009-01-01
I was surfing and some windows based scam virus checker got in my system..??????????????
How the hell can this get in my Ubuntu. ??????
its called   scan4new.com      something or other....
It jumped up on the screen when I get into Fox 3.
Anybody know about this????? Where can I revoke any permissions for any file that has this in the file name....  specifically
thanks
Ubu 8.04     no dual boot

---

### Post by cariboo on 2009-01-01
Relax, the file will have no effect on your system, your browser has probably been hijacked. Check in Firefox Edit-->Preferences-->Main-->Home Page to see if it has been changed, and make sure you have the Noscript addon installed and turned on. You may want to check /etc/resolv.conf to see if that has changed, it shoiuld look something like this:

```
 cat /etc/resolv.conf
domain aplus
search aplus
nameserver 64.59.168.13
nameserver 64.59.168.15
```

If you don't recognize the domain and search entries, remove them.

Jim

---

### Post by The Cog on 2009-01-01
Its [http://scan4new.com/](http://scan4new.com/) - It scanned my Ubuntu drive C and found several .exe viruses (allegedley). Nasty behaviour - I had to kill firefox to get rid of it. It's all javascript.

The .exe it wants you to download would almost certainly hijack your windiws PC though.

---

### Post by slowth5 on 2009-01-01
The Cog, wipe your Ubuntu C: immediately, because your system drive is compromised.

Seriously folks, this is most likely the antivirus 2009 that Microsoft wiped from at least one million machines.  This bug is insidious.

[http://en.wikipedia.org/wiki/MS_Antivirus](http://en.wikipedia.org/wiki/MS_Antivirus)

---

### Post by Rhubarb on 2009-01-01
> **slowth5 said:**
> The Cog, wipe your Ubuntu C: immediately, because your system drive is compromised.

Seriously folks, this is most likely the antivirus 2009 that Microsoft wiped from at least one million machines.  This bug is insidious.

[http://en.wikipedia.org/wiki/MS_Antivirus](http://en.wikipedia.org/wiki/MS_Antivirus)
Linux is not windows, Linux (and hence Ubuntu) can't run windows executables.
There is no such thing as C: in Ubuntu, and there is nothing wrong with your Ubuntu partition.

As advised further above, check to see if your DNS has been hijacked, clear out your firefox cookies and cache.
Also check to see your default firefox homepage is ok and normal.

Also check to see if there's any updates waiting to be downloaded and installed in Ubuntu:
System --> Administration --> Check for updates.

---

### Post by albinootje on 2009-01-01
> **bu2971x said:**
> I was surfing and some windows based scam virus checker got in my system..??????????????
How the hell can this get in my Ubuntu. ??????
its called   scan4new.com      something or other....
It jumped up on the screen when I get into Fox 3.

I just tested it on my Linux only system, I'm using noscript, I temporarily allowed java-script from that page, and from then on it was an unstoppable <cancel> or <OK> mess :(
Nasty website :(

And of course the whole scanning of C: drive which it shows is fake.

---

### Post by melojo on 2009-01-01
> **cariboo907 said:**
> Relax, the file will have no effect on your system, your browser has probably been hijacked. Check in Firefox Edit-->Preferences-->Main-->Home Page to see if it has been changed, and make sure you have the Noscript addon installed and turned on. You may want to check /etc/resolv.conf to see if that has changed, it shoiuld look something like this:

```
 cat /etc/resolv.conf
domain aplus
search aplus
nameserver 64.59.168.13
nameserver 64.59.168.15
```

If you don't recognize the domain and search entries, remove them.

Jim

+1 
not to worry linux is not windows so relax.
I ended up deleting my .mozilla hidden directory.

LOL

---

### Post by bu2971x on 2009-01-01
No Scrp got rid of it but..  what a dog ****... Fox shouldnt have allowed it.

---

### Post by slowth5 on 2009-01-02
Hey Rhubarb, your joke meter must be malfunctioning or maybe it was just a bad joke.  If so, my sincerest apologies.  But seriously folks, check your C: drive.

---

### Post by cariboo on 2009-01-02
I really don't understand why people blame software, when the biggest problem with Linux is what is between the back of the chair and the keyboard. :)

Jim

---

