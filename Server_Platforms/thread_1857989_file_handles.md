---
title: "file handles"
date: 2011-10-11
forum: Server Platforms
---

### Post by erixnow on 2011-10-11
Does anyone have an idea on how to monitor file handles.  Example:

I want to know the pid of every file that writes to just say /etc/motd.

Im caught between solaris and linux...... some one needs a hybrid *NIX !  

Dtrace and some other utils would be awsome in linux.


Thx,
  Eric Peyser

---

### Post by jazzon on 2011-10-11
dtrace is available from ```
sudo apt-get install systemtap-sdt-dev
```

---

### Post by karlson on 2011-10-11
> **erixnow said:**
> Does anyone have an idea on how to monitor file handles.  Example:

I want to know the pid of every file that writes to just say /etc/motd.

Im caught between solaris and linux...... some one needs a hybrid *NIX !  

Dtrace and some other utils would be awsome in linux.


Thx,
  Eric Peyser

I think the program you are looking for is auditd.  It's available on Solaris as well but you should be careful as it is for one chatty and secondly can slow down your system.  Although both are dependent upon configuration.

---

### Post by erixnow on 2011-10-11
I tried Dtrace for linux,  and it didnt behave well :( .....  I will try auditd and see if I can regex the output so at least screen writes wont slow things up.  maybe even bind it to a CPU core as to not bog down the rest of the system (  Since linux claims to have improved its scheduler / cpu cache refresh problem).


I will post solution......


Thankyou !


-Eric peyser

---

### Post by erixnow on 2011-10-11
ok tried auditctl with:

#auditctl -w /etc/motd -p war -k MOTD

for some reason it is not triggering on changes.  here is a list of my rules (auditctl -l)

LIST_RULES: exit,always watch=/etc/motd perm=rwa key=MOTD


ausearch -i shows basically that a rule was added.

any insight ????


Thx in advance,
  Eric Peyser

---

### Post by karlson on 2011-10-11
> **erixnow said:**
> ok tried auditctl with:

#auditctl -w /etc/motd -p war -k MOTD

for some reason it is not triggering on changes.  here is a list of my rules (auditctl -l)

LIST_RULES: exit,always watch=/etc/motd perm=rwa key=MOTD


ausearch -i shows basically that a rule was added.

any insight ????


Thx in advance,
  Eric Peyser

Is audit running?

---

### Post by erixnow on 2011-10-11
ps shows:
$pid  ppid=1 /sbin/auditd
$pid ppid=2 [kauditd]  (which im not sure if this should goes with the norm)


Regards,
  Eric Peyser

---

### Post by karlson on 2011-10-11
> **erixnow said:**
> ps shows:
$pid  ppid=1 /sbin/auditd
$pid ppid=2 [kauditd]  (which im not sure if this should goes with the norm)


Regards,
  Eric Peyser

```

$ sudo aureport -f

```
??

---

### Post by erixnow on 2011-10-11
<no events of interest were found>


Regards,
  Eric Peyser

---

### Post by erixnow on 2011-10-11
it caught it when i VI'd the file.  But on ubuntu I have some mystery proc that auto fills in my motd with system stats.  It doesnt seem to catch that or when I echo content into the file.

---

### Post by karlson on 2011-10-11
> **erixnow said:**
> it caught it when i VI'd the file.  But on ubuntu I have some mystery proc that auto fills in my motd with system stats.  It doesnt seem to catch that or when I echo content into the file.

Check /var/run/motd and /etc/motd.tail

---

### Post by robvas on 2011-10-11
[FONT="Courier New"]lsof /etc/motd[/FONT]

?

---

### Post by karlson on 2011-10-11
> **robvas said:**
> [FONT="Courier New"]lsof /etc/motd[/FONT]

?
lsof is showing currently open files.  /etc/motd is updated out of cron.

---

### Post by erixnow on 2011-10-12
it is linked to var/run.  auditd doesnt seem to follow links which was a bad assumption on my part.  it seems to report that /bin/login is updating /var/run/motd.  


I still feel uncomfortable that chasing down file handles is such a closed task in linux as far as I can see.   lsof would be a great option..... but polling lsof with watch or other would eat up alot of resources.  I guess I may take a stab at Dtrace for linux again (even though it seemed buggy).  I have done this task in Solaris with almost no effort.

I need to go about this in an interrupt driven way (Dtrace event).  that is why auditd seemed to look very promising. auditd just seems to miss certain type of file operations,  but is a great tool I never knew of (Thanks for that one !).

strace /bin/login would be another viable option provided it also keeps track of resources that all threads open,  whether a child of a child or a child of a root.


Any other ideas on chasing down file handles or file operations would still be appreciated.  most utils are real time and dont have trapping abilities,  so I am unable to catch something that happens in a split second and is gone.

---

### Post by karlson on 2011-10-12
> **erixnow said:**
> it is linked to var/run.  auditd doesnt seem to follow links which was a bad assumption on my part.  it seems to report that /bin/login is updating /var/run/motd.  

I still feel uncomfortable that chasing down file handles is such a closed task in linux as far as I can see.   lsof would be a great option..... but polling lsof with watch or other would eat up alot of resources.  I guess I may take a stab at Dtrace for linux again (even though it seemed buggy).  I have done this task in Solaris with almost no effort.

I need to go about this in an interrupt driven way (Dtrace event).  that is why auditd seemed to look very promising. auditd just seems to miss certain type of file operations,  but is a great tool I never knew of (Thanks for that one !).

strace /bin/login would be another viable option provided it also keeps track of resources that all threads open,  whether a child of a child or a child of a root.

Any other ideas on chasing down file handles or file operations would still be appreciated.  most utils are real time and dont have trapping abilities,  so I am unable to catch something that happens in a split second and is gone.

Have you looked at the cron configurations?  If I remember correctly I had to track this down once before and /etc/motd, /etc/motd.tail on Ubuntu are updated out of /etc/cron.daily or /etc/cron.hourly.  Not sure which one.

/bin/login to my recollection doesn't update /etc/motd it might just read it.

---

### Post by erixnow on 2011-10-12
yeh checked cron and nothing.  also file gets updated on login (/var/run/motd).  strange.  Im about to use strace.  just have to wait for some down time.


motd is just an example that is safe to pratice on.  chasing down system based file changes is a need to know. it is much easier in Solaris.  I am stuck between the two worlds. Solaris hasalot of commands I use alot that linux dosnt and vs. versa.



Regards
  Eric Peyser

---

### Post by erixnow on 2011-10-22
After trying to get Dtrace to behave correctly in linux..... I am abandoning it!!!!!!  It lacks alot.  Oracle is claiming to have a decent port..... then by reading further it is still very lacking.   so no Dtrace !  But thanks for the package name that contained it.



Eric

---

