---
title: "Unknown user running  process"
date: 2009-10-16
forum: Security
---

### Post by Randypan on 2009-10-16
I hope the title of  the thread doesn't sound too urgent or alarming -I'm just a noob looking for some info on something I noticed about my running processes on my system monitor.
I have installed the SysMonitor screenlet. Among other things, it displays the curently running apps in three columns. The first displays the name of the process [-->COMMAND], the second displays the user under which the process is run [-->USER] (normally 'root' or my own username) and the third displays CPU usage by application [-->%CPU].
So today I noticed that two processes: dbus and hald, had three-digit numbers (111 and 106 If I remember correctly) instead of usernames under the USER column.
Does that indicate a system threat or is it it just normal system operation I haven't noticed before.

NOTE that I ran rkhunter and it found everything to be OK except two [COLOR=Red]WARNING[/COLOR] [COLOR=Black]messages next to /usr/sbin/unhide and /usr/sbin/unhide-linux26. Is that supposed to be a bug or something? As far as I know rkhunter itself uses unhide.
Then it posted another [COLOR=Red]WARNING [COLOR=Black]message next to 'Checking /dev for suspicious file types'.
Apart from the above, everything else was green.
I don't know much about usin rkhunter. For example how can I find what exactly was the problem with /dev?

Thanks in advance for the info.
[/COLOR][/COLOR][/COLOR]

---

### Post by phillw on 2009-10-16
This thread should put you mind at ease !!

[http://ubuntuforums.org/showthread.php?t=1006870&highlight=rkhunter+false+positive](http://ubuntuforums.org/showthread.php?t=1006870&highlight=rkhunter+false+positive)

Regards,

Phill.

---

### Post by Randypan on 2009-10-16
So what about hald and dbus? I'm asking more out of curiosity now than out of fear of intrusion. Thanks by the way.

---

### Post by phillw on 2009-10-16
Hi,

both processes are normal processes.

```
man dbus-daemon
```

and

```
man hald
```

It's nice to see you are looking at your logs and getting used to them :)

Phill.

---

### Post by movieman on 2009-10-16
Note that system utilities (I think it at least applies to 'top' and 'ps', maybe others) will typically display numeric user IDs if the user name is too large to fit in the space allocated to it on the display; otherwise if you have, say, a three character field and two users foo and foobar, you can't tell which is running the program.

---

### Post by Randypan on 2009-10-16
Thanks a lot

---

### Post by __p1n__ on 2009-10-16
Linux kernel and userland rootkits are pretty easy to identify as long as you do so via static-linked system calls and not via command line utilities (which may themselves be compromised.)

Understanding whether or not your o/s is truly rooted (i.e. running inside a VM) can be determined on Intel hardware with this code written by Joanna Rutkowska of Invisible Things:

/* VMM detector, based on SIDT trick
 * written by joanna at invisiblethings.org
 *
 * should compile and run on any Intel based OS
 *
 * [http://invisiblethings.org](http://invisiblethings.org)
 */


#include <stdio.h>
int main () {
  unsigned char m[2+4], rpill[] = "\x0f\x01\x0d\x00\x00\x00\x00\xc3";
  *((unsigned*)&rpill[3]) = (unsigned)m;
  ((void(*)())&rpill)();

  printf ("idt base: %#x\n", *((unsigned*)&m[2]));
  if (m[5]>0xd0) printf ("Inside Matrix!\n", m[5]);
  else printf ("Not in Matrix.\n");
  return 0;
}

---

### Post by unspawn on 2009-10-17
> **__p1n__ said:**
> Linux kernel and userland rootkits are pretty easy to identify as long as you do so via static-linked system calls
Even if you may be right (in a very limited way), isn't it still best practice to offline the system and run an autopsy on the corpse?..


> **__p1n__ said:**
> truly rooted (i.e. running inside a VM) 
How is running an OS as a hypervisor or virtualization guest an unambiguous and failsafe indication of a machine being rooted?.. Besides, how many hardware "rootkit" infections have you actually encountered and investigated since the release of JR's work or the DR kit?

---

### Post by __p1n__ on 2009-10-17
> **unspawn said:**
> Even if you may be right (in a very limited way), isn't it still best practice to offline the system and run an autopsy on the corpse?..

How is running an OS as a hypervisor or virtualization guest an unambiguous and failsafe indication of a machine being rooted?.. Besides, how many hardware "rootkit" infections have you actually encountered and investigated since the release of JR's work or the DR kit?

1. Yes.
2. In the wild?  Zero. ;)

---

### Post by Randypan on 2009-10-20
Well, judging from the above and after double-checking my security status it's obvious the whole thing was false alarm. I just got scared and went paranoid.

---

