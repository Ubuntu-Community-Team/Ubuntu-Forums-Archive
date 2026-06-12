---
title: "Limit user CPU usage"
date: 2005-12-12
forum: The Cafe
---

### Post by kb00heda on 2005-12-12
Hi,

Maybe this is not the appropriate area for this post... however, I could not find a better one. So, here goes:

I would like to limit the CPU usage for a user, say that he/she should be allowed to use no more than 50 percent of the CPU resources. I recognized this to be possible on a CPU time basis via /etc/security/limits.conf, but this is somewhat different. Alternatively, is it possible to limit the CPU usage for a single process, e.g., to have it fixed at 50 percent?

Regards,
David

---

### Post by towsonu2003 on 2006-01-14
anything new on this? I'm interested how to that as well (sick of clamscan eating 101% cpu and driving heat up 10-15 degrees celsius (from an average of 45 to 62) over 2-3 minutes)

also, this need to be moved to a technical forum...

---

### Post by curtis on 2006-01-14
ulimit may help, I am not sure though.

---

### Post by BSDFreak on 2006-01-14
[quote=curtis]ulimit may help, I am not sure though.[/quote]

No, the only thing you can set with ulimit is the cpu time before the process is aborted.

Only thing that comes to mind is nice and renice, to set priority, which will work just fine if it's slowdown on other processes you are worried about.

---

### Post by Mr_Grieves on 2006-01-14
I don't know.. so I'll just use my huge imagniation.
> 
Fread not! It's **IMAGNIARY BOY!**

-Create a virual root for the user, in this virtual root, replace all commands with scripts that 'nice' each and every command!


---

### Post by BSDFreak on 2006-01-14
[quote=Mr_Grieves]I don't know.. so I'll just use my huge imagniation.[/quote]

man renice. It's not neccessary to do it per process, it can be done per user if you don't want it per process. ;)

---

### Post by Mr_Grieves on 2006-01-14
> **BSDFreak]man renice. It's not neccessary to do it per process, it can be done per user if you don't want it per process.  said:**
> 
AHA!

[quote]
In this episode! **IMAGINARY BOY!** encounters his ARCH enemy - **BSDFreak BOY!**

<WHAM!>
<POW!>
<CRASH!>

What about this **BSDFreak BOY**?

-You create a VMWare enviorment in where this new user must reside! and.. YOU NICE THE VWWare PROCESS!!


I'm sorry kb00heda for the offtopic. I'm soon off to bed. I promise.

---

### Post by BSDFreak on 2006-01-15
[quote=Mr_Grieves]AHA!



I'm sorry kb00heda for the offtopic. I'm soon off to bed. I promise.[/quote]

Um, why not just use renice -u? Or if you are going to use a VM, use Qemu, it's FOSS. ;)

Watch out for the superbaseballbatboy though (old game reference, bonus points if you know where it's from).

---

### Post by sportfreak2020 on 2009-12-08
i know this is an old thread, but i use cpulimit across all our dev servers to limit every thing running on them..
there is a certain script that can be utilized, ie., like a white list and black list...

there is a very nice howto about this one!!

[http://ubuntuforums.org/showthread.php?t=992706](http://ubuntuforums.org/showthread.php?t=992706)

hope it helps someone!!!! :D

---

