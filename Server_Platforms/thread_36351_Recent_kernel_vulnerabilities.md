---
title: "Recent kernel vulnerabilities"
date: 2005-05-23
forum: Server Platforms
---

### Post by gnutered on 2005-05-23
There are some current Linux kernel exploits that don't appear patched in Ubuntu.

[http://secunia.com/advisories/15392/](http://secunia.com/advisories/15392/) - 17 May
[http://secunia.com/advisories/15341/](http://secunia.com/advisories/15341/) - 12 May
[http://secunia.com/advisories/15204/](http://secunia.com/advisories/15204/) - 2 May

Without being too soapboxy, shouldn't these be fixed quicksmart?  I've been waiting for new kernels to appear.

AIUI, the "official" Hoary kernel is 2.6.10-5, from 5 April, which is much older than these vulnerabilities.  I see that a 2.6.11-1 and a 2.6.12-1 are in the universe archives, but the 2.6.11 is something like 12 Feb, and the 2.6.12 is 11 May.

Tony

---

### Post by mendicant on 2005-05-23
[http://ubuntuforums.org/showthread.php?t=36375](http://ubuntuforums.org/showthread.php?t=36375)

and a few others, too.

---

### Post by mendicant on 2005-05-23
By the way, the way these things work is that security fixes get backported to whatever version of the package was actually released.  I suppose for updates, it also gets applied to them.  So you can't take version numbers as indicators of the existence of security vulnerabilities.

---

### Post by gnutered on 2005-05-23
Looks like I spoke a day too soon.  New kernels are out.  Thanks.

Next question: Are we looking at this kind of turn-around generally?  The current round of exploits were IIRC local ones.  If there was a remote exploit that came to light, could we expect a faster turnaround?

Or, in another way, is there some kind of benchmark the Ubuntu developers are aiming for when it comes to time-to-patch, especially for kernel vulnerabilities?  Is it too much to expect this within hours, or a day at the most?

Tony

---

### Post by mendicant on 2005-05-24
I suspect they would try to fix remote exploits as soon as possible.  There may be delays due to getting the patch backported, working with the upstream authors and perhaps even other distributions.  For a better answer, you could ask on the mailing lists.

---

### Post by Mgcross on 2005-05-25
[QUOTE=gnutered]Looks like I spoke a day too soon.  New kernels are out.  Thanks.

Next question: Are we looking at this kind of turn-around generally?  The current round of exploits were IIRC local ones.  If there was a remote exploit that came to light, could we expect a faster turnaround?

Or, in another way, is there some kind of benchmark the Ubuntu developers are aiming for when it comes to time-to-patch, especially for kernel vulnerabilities?  Is it too much to expect this within hours, or a day at the most?

Tony[/QUOTE]
K, new kernels are out, do I have to worry 'bout the fact that linux restricted is no updated either? Will this kill my nvidia drivers when I update?

---

### Post by mendicant on 2005-05-25
No, both the ATI and nvidia drivers work fine, still.

---

### Post by Mgcross on 2005-05-25
[QUOTE=mendicant]No, both the ATI and nvidia drivers work fine, still.[/QUOTE]
Thanks a lot....good to know...and here I go....

---

### Post by jdong on 2005-05-25
[QUOTE=Mgcross]K, new kernels are out, do I have to worry 'bout the fact that linux restricted is no updated either? Will this kill my nvidia drivers when I update?[/QUOTE]
Binary modules won't die, unless the kernel's ABI was forced to be broken/changed due to the update.

If this happens, it's made quite clear in the USN.

---

### Post by Masato on 2005-05-25
Given the circumstances concerning the Ubuntu/Linux kernel, and the recent [hype](http://www.eweek.com/article2/0,1759,1787112,00.asp) surrounding the Linux kernel drawing concerns, I was drawn to this topic. Also, being that security is my profession, it has a tendency to stick out alot more than other things. 

I was concerned when I heard about the kernel not being patched, but really it shouldn't be an issue for too long. Even if it brings out certain vulnerabilities, that just means there was a flaw that is now pointed out and therefore, gets patched, making it better in the long run.

---

### Post by jdong on 2005-05-25
I like it when ANY kind of vulnerability is found and patched within good time. It just simply means Linux's security is increasing. For those truly paranoid, they'd be running a distribution patched with SELinux, PAX, Exec-shield, GCC's Mudflap / FORTIFY_SOURCE, Grsec, or some other proactive security solution (like Fedora, RHEL). These add a secondary layer of protection that often stops these exploits dead in their tracks.
 
As someone who compiles and patches his own kernel, I love the new 2.6.11.x system, which allows these security patches to be added to the latest stable release, rather than some patch attached to an e-mail that takes hours to find and keep track of :)

---

