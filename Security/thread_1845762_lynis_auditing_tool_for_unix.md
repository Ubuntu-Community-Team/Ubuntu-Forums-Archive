---
title: "lynis auditing tool for unix"
date: 2011-09-17
forum: Security
---

### Post by boregard on 2011-09-17
Hello, I installed Lynis Auditing tool and now I need help viewing the results. To start with how do I see a log of the results? I was in the terminal and pressing enter instead ctr+cl and the terminal unexpectedly closed before I could save the results. Appreciate any help or advice.

---

### Post by haqking on 2011-09-17
> **boregard said:**
> Hello, I installed Lynis Auditing tool and now I need help viewing the results. To start with how do I see a log of the results? I was in the terminal and pressing enter instead ctr+cl and the terminal unexpectedly closed before I could save the results. Appreciate any help or advice.

/var/log/lynis-report.dat (this will show you recommendations on how to secure things)
/var/log/lynis.log

---

### Post by boregard on 2011-09-17
Sorry I still need clarification, I entered ( /var/log/lynis-report.dat ) in the terminal and tried logfile viewer and keep getting permission denied. Thanks

---

### Post by haqking on 2011-09-17
> **boregard said:**
> Sorry I still need clarification, I entered ( /var/log/lynis-report.dat ) in the terminal and tried logfile viewer and keep getting permission denied. Thanks


well you wouldnt just enter /var/log/lynis-report.dat into a terminal you need to pipe it to a reader or redirect to another output.

cat or nano or vi or gedit etc (if you use gedit then gksudo it and not sudo)

as for permission denied it will need root so use sudo as you shoud have to run lynis in the first place

---

### Post by boregard on 2011-09-17
How do I pipe it to a reader?

---

### Post by haqking on 2011-09-17
> **boregard said:**
> How do I pipe it to a reader?


ok well i assume they are there and the audit ran ok, you should of seen a text based gui come up whilst it was auditing ?

anyways so to view the logs then use sudo and any reader of your choice as i mentioned, using tail, more, less etc as they will be long or...

you might want to view it in gedit so:

```
gksudo gedit /var/log/logname

```or in nano:

```
sudo nano /var/log/xxxx
```or concatenate it with cat:

```
cat /var/log/xxxx
```or vi/vim

```
sudo vim /var/log/xxx
```etc etc

If you run a graphical one then use gksudo and not sudo though.  from what i remember they are lengthy logs, im not sure which one you will find most suitable to view it, or of course run the log file viewer with gksudo as:
```

gksudo  gnome-system-log &
```

---

### Post by Dangertux on 2011-09-17
That project hasnt really been updated in awhile and like most generic "nix" auditing tools spits out false positives when dealing with ubuntu. 

But yeah it logs to  /var/log and /tmp

Also this might be helpful. [http://www.rootkit.nl/files/lynis-documentation.html](http://www.rootkit.nl/files/lynis-documentation.html)

---

### Post by boregard on 2011-09-17
Thanks to both of you for your help! I finally figured out how to view the log using the gk sudo cmd. If the project hasn't been updated in a while and spits out false positives I prolly wont use it much. Least I know how to find logfiles and view them now. Just trying to learn how to secure system. Much Thanks.

---

### Post by haqking on 2011-09-17
> **boregard said:**
> Thanks to both of you for your help! I finally figured out how to view the log using the gk sudo cmd. If the project hasn't been updated in a while and spits out false positives I prolly wont use it much. Least I know how to find logfiles and view them now. Just trying to learn how to secure system. Much Thanks.


no worries, you are welcome.

please use thread tools menu to mark as solved.

cheers

---

