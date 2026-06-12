---
title: "Who killed my process?"
date: 2007-05-03
forum: Server Platforms
---

### Post by rainefan on 2007-05-03
Hi people! I really don't know if this forum can help me, but i'm having some problems in receiving kill signal from an UNKNOWN process. I wish i could now the pid or name of the killer process....is anyway? Bash or C?

Thanks!

Regards

---

### Post by dannyboy79 on 2007-05-04
> **rainefan said:**
> Hi people! I really don't know if this forum can help me, but i'm having some problems in receiving kill signal from an UNKNOWN process. I wish i could now the pid or name of the killer process....is anyway? Bash or C?

Thanks!

Regards

could you be more specific? what process is getting killed on ya? when? what are you doing? what process is getting killed? you can't expect some1 to help with the info you've provided. I am not trying to be rude, I am merely informing you that it's most likely that no one has helped because no one want's to bother asking you for more info just so they can then help ya. Next time, post all the info you can so other's can help ya.

---

### Post by rainefan on 2007-05-06
Sorry, i will be more specific...

My program (process) is receiving SIGTERM signals from a unknown process (don't know if it's from kernel or any other userspace process other than mine program).

I searched some info on the net and found something interesting: the OOM kernel process. It kills any process that's requesting more memory that system can give. But I'm sure is not my case since system resources are ok (disabled SIGTERM signal catch on my process and everything is working just fine).

I'm really interested in knowing from my program or any bash script or any kernel log, who's process is sending SIGTERM signals to my process/program.

Thank's again for the help, and sorry again for that as my English really sucks :( 

Regards,

Raine

---

### Post by dannyboy79 on 2007-05-07
> **rainefan said:**
> Sorry, i will be more specific...

My program (process) is receiving SIGTERM signals from a unknown process (don't know if it's from kernel or any other userspace process other than mine program).

I searched some info on the net and found something interesting: the OOM kernel process. It kills any process that's requesting more memory that system can give. But I'm sure is not my case since system resources are ok (disabled SIGTERM signal catch on my process and everything is working just fine).

I'm really interested in knowing from my program or any bash script or any kernel log, who's process is sending SIGTERM signals to my process/program.

Thank's again for the help, and sorry again for that as my English really sucks :( 

Regards,

Raine


havbe you reviewed all the log files? they are in /var/log/. syslog might just show what's sending hte SIGTERM.

---

### Post by sickdude on 2007-05-07
Is your system swapping? If your system is high in load or mem usage the kernel might kill some stuff to keep your system going

---

### Post by rainefan on 2007-05-08
> **dannyboy79 said:**
> havbe you reviewed all the log files? they are in /var/log/. syslog might just show what's sending hte SIGTERM.

Hi danny! I didn't find anything on syslog or any other log that could be indentified as a sigterm...

> **sickdude said:**
> Is your system swapping? If your system is high in load or mem usage the kernel might kill some stuff to keep your system going

Actually, no...all resources are OK

Is any way in C or bash to indicate the sender of that signal?

Thanks anyway!

Regards,
Raine

---

### Post by dannyboy79 on 2007-05-08
did you look in /var/log/messages for anything like this:

kernel: pid 19070 (perl), uid 1022: exited on signal 11 

kernel: pid 9578 (perl), uid 1022: exited on signal 10
(NOTE: Perl is just the example I found)

I read that Signal 11 is a segmentation fault, indicating either (a) bugs in the 
app or (b) hardware problems.  Have you tried on 
a different machine?

---

