---
title: "&quot;Hole in the Linux kernel allows root access&quot; - Do we have to worry?"
date: 2009-11-04
forum: Security
---

### Post by MasterNetra on 2009-11-04
There is mention of some hole in the linux kernel that could allow someone to access the system with root privilages, sense root account is disabled by default is it something us Ubuntu users have to be concerned about?

See Article for details.
Article: [http://www.h-online.com/open/news/item/Hole-in-the-Linux-kernel-allows-root-access-850016.html](http://www.h-online.com/open/news/item/Hole-in-the-Linux-kernel-allows-root-access-850016.html)

---

### Post by RiceMonster on 2009-11-04
This vulnerability was fixed a few months ago.

---

### Post by Foster Grant on 2009-11-04
According to the (somewhat inaccurate, IMHO) summary on Slashdot, the bug is "mitigated" in most major distros at this point. Apparently it's not fixed yet in Red Hat Enterprise Linux. How that translates into "virtually all production versions in use at the moment (are) vulnerable" (as the /. summary quoting the article says) I don't understand, unless you count the fact that it's fixed via workaround rather than via code in the kernel.

I think I should file a bug report on the writer himself for that one. :)

---

### Post by MasterNetra on 2009-11-04
Oh ok, so thats a no we don't have to worry about it. ^.^

---

### Post by Xbehave on 2009-11-04
if you have a kernel before 2.6.32 yes, ubuntu does have root, you just can't login as root. The vulnerability is minimised unless you have wine or dosbox installed in which case it is still there. If you run 
```
cat /proc/sys/vm/mmap_min_addr

```
if you get 0  you are bulnerable
if you get >0 you are safe 

edit erm when i said >0 i think i was wrong it has to be a big number

---

### Post by Xoanan on 2009-11-04
Hi All

I read this article;  Is this affecting all distros? The article did not specify as far as I can tell

[http://www.linuxtoday.com/news_story.php3?ltsn=2009-11-04-017-35-SC-KN]("http://www.linuxtoday.com/news_story.php3?ltsn=2009-11-04-017-35-SC-KN")

---

### Post by cariboo on 2009-11-04
According to the article, you will only be affected if you use wine or dosemu. It wouldn't surprise me to see a kernel update in the next couple of days.

---

### Post by solitaire on 2009-11-04
Think it's all Linux versions on kernels BELOW 2.6.32- which are prone to this issue.

So that's probably affecting everyone, except the people compiling their own latest 2.6.32 kernels.

What kernel is Lucid Lynx (or what ever 10.04 is called) going to be using?

---

### Post by rookcifer on 2009-11-04
While this bug has not been fixed in the kernel yet, almost all distros have "worked around" it by adjusting the mmap_min_addr value.  Karmic has fixed this issue by default already.  The only major distro to not fix it is Fedora.

Here's how you can check if you are vulnerable:

```
cat /proc/sys/vm/mmap_min_addr
```

If that command returns a value other than 0, you are safe.  (My Karmic install returns 65536).  If you do see 0, then you can fix it by typing:

```
sysctl -w vm.mmap_min_addr="65536"
```

This exploit is actually over a month old and it fails me why this is even news at all.  [This article]("http://www.theregister.co.uk/2009/11/03/linux_kernel_vulnerability/") goes into more detail.  And [this article]("http://www.linux-magazine.com/Online/News/Security-Hole-in-Kernel-Allows-Privilege-Extensions") provides the fix I just posted.

Again, no Ubuntu users have anything to worry about here.

---

### Post by TheForumTroll on 2009-11-04
I get a 0 from that command. I'm using Karmic..

---

### Post by ad_267 on 2009-11-04
> **TheForumTroll said:**
> I get a 0 from that command. I'm using Karmic..

Same here, I have Wine installed. I'm not particularly worried though.

---

### Post by rookcifer on 2009-11-04
> **TheForumTroll said:**
> I get a 0 from that command. I'm using Karmic..

As the second article I posted suggests, Wine is causing this.  I don't run Wine, so I am still using the default 65535 value that Karmic provides.

---

### Post by Sir Jasper on 2009-11-04
Hi rookcipher,

Thank you for posting both the test and the fix (where I had a 0 value and needed to start the fix with ¨sudo¨).

I did not read the articles and I use 9.04 and Wine; which seems to still be working, I assume as expected, after applying the fix.

My regards

---

### Post by 3rdalbum on 2009-11-04
Ubuntu ships with that magic number at a high value; the exploit only works when the number is set to 0 (which happens if Wine or DOSbox is installed).

Funnily enough, Wine still seems to work if you set the number to 1.

---

### Post by cariboo on 2009-11-04
Lucid is already running 2.6.32:

```
Linux alexis-lucid 2.6.32-2-generic #2-Ubuntu SMP Sat Oct 31 17:06:33 UTC 2009 x86_64 GNU/Linux
```

---

### Post by FuturePilot on 2009-11-05
I thought this was already [fixed?]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/413656")

---

### Post by TheForumTroll on 2009-11-05
> **rookcifer said:**
> As the second article I posted suggests, Wine is causing this.  I don't run Wine, so I am still using the default 65535 value that Karmic provides.

I missed that bit. Thank you for the info :KS

---

### Post by MasterNetra on 2009-11-06
Doesn't Karmic Come with it fixed?

---

### Post by coldReactive on 2009-11-06
> **FuturePilot said:**
> I thought this was already [fixed?]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/413656")

Fix Released NEVER EVER in a million years will EVER equal fix committed.

---

### Post by FuturePilot on 2009-11-06
> **coldReactive said:**
> Fix Released NEVER EVER in a million years will EVER equal fix committed.

What?

---

### Post by coldReactive on 2009-11-06
> **FuturePilot said:**
> What?

One time there was a fix released, but that only meant that the fix was shown to all who would want to commit it.

Fix Released =/= Fix Commited

---

### Post by MasterNetra on 2009-11-06
> **coldReactive said:**
> One time there was a fix released, but that only meant that the fix was shown to all who would want to commit it.

Fix Released =/= Fix Commited

Don't you mean Fix Released != Fix Committed ? != (Not Equal)

---

### Post by FuturePilot on 2009-11-06
> **coldReactive said:**
> One time there was a fix released, but that only meant that the fix was shown to all who would want to commit it.

Fix Released =/= Fix Commited

Are you referring to bugs that are linked from upstream bug trackers in launchpad? If so, then yes sometimes those can be marked as fixed before it makes it into Ubuntu, but I see no such link in that bug report.

I think you're confusing some of the bug status. [https://wiki.ubuntu.com/Bugs/Status]("https://wiki.ubuntu.com/Bugs/Status")

---

### Post by MrNatewood on 2009-11-06
> **Xbehave said:**
> if you have a kernel before 2.6.32 yes, ubuntu does have root, you just can't login as root. The vulnerability is minimised unless you have wine or dosbox installed in which case it is still there. If you run 
```
cat /proc/sys/vm/mmap_min_addr

```
if you get 0  you are bulnerable
if you get >0 you are safe 

edit erm when i said >0 i think i was wrong it has to be a big number

So... How do I keep wine working and not be vulnerable?

---

### Post by coldReactive on 2009-11-06
> **MrNatewood said:**
> So... How do I keep wine working and not be vulnerable?

Remove Z: which is set to the whole file system /

If you do this however, you'll have to run all your wine apps in drive_c folder from now on.

---

### Post by samjh on 2009-11-06
> **MasterNetra said:**
> Doesn't Karmic Come with it fixed?

Not sure, but when I tried **sysctl vm.mmap_min_addr** on my Karmic system (with wine installed), it returned 0 which means it would be vulnerable.  Whether or not it really *is* vulnerable is another question, because a default Ubuntu installation has no root account.

BTW, it looks like a diligent member of our community has reported it:
[https://bugs.launchpad.net/ubuntu/+source/dosemu/+bug/401950](https://bugs.launchpad.net/ubuntu/+source/dosemu/+bug/401950)

So with dosemu or wine installed, it *could be* (not necessarily *is*) vulnerable, but I'll leave that to be answered by a member of the security team or other appropriately educated persons.

---

### Post by FuturePilot on 2009-11-06
> **samjh said:**
> Not sure, but when I tried **sysctl vm.mmap_min_addr** on my Karmic system (with wine installed), it returned 0 which means it would be vulnerable.  Whether or not it really *is* vulnerable is another question, because a default Ubuntu installation has no root account.

BTW, it looks like a diligent member of our community has reported it:
[https://bugs.launchpad.net/ubuntu/+source/dosemu/+bug/401950](https://bugs.launchpad.net/ubuntu/+source/dosemu/+bug/401950)

So with dosemu or wine installed, it *could be* (not necessarily *is*) vulnerable, but I'll leave that to be answered by a member of the security team or other appropriately educated persons.

Ubuntu *does* have a root account, it's disabled though. So yes it is possible to get a root shell through an exploit.

---

### Post by dixie460 on 2009-11-08
I uninstalled Wine, rebooted, and ran this code
cat /proc/sys/vm/mmap_min_addr
and still got a 0. Do I need to be concerned? I can't find how to take care of this problem anywhere, does anyone on here know how?

Thanks

Andy

---

### Post by MasterNetra on 2009-11-09
> **dixie460 said:**
> I uninstalled Wine, rebooted, and ran this code
cat /proc/sys/vm/mmap_min_addr
and still got a 0. Do I need to be concerned? I can't find how to take care of this problem anywhere, does anyone on here know how?

Thanks

Andy

Apparently yes for as long as it is zero. However there is a fix and you can still theoretically run Wine.

According to: [http://www.itworld.com/security/83917/an-important-linux-fix](http://www.itworld.com/security/83917/an-important-linux-fix)

All you have to do is sudo the command (sense just entering yields our favorite insufficient access reply):
```
 sysctl -w vm.mmap_min_addr="1024" 
```

however the 1024 can be any number up to 65535. This fix however is only good until you reboot. Though I suppose you could setup a script or something. How you would do a script for a limited account I have no clue.

---

### Post by Mornedhel on 2009-11-09
> **Xbehave said:**
> if you have a kernel before 2.6.32 yes, ubuntu does have root, you just can't login as root. The vulnerability is minimised unless you have wine or dosbox installed in which case it is still there.

FYI, I have dosbox installed and:

```
sysctl vm.mmap_min_addr
```

returns "vm.mmap_min_addr = 65536", on Karmic.

---

### Post by MasterNetra on 2009-11-09
> **Mornedhel said:**
> FYI, I have dosbox installed and:

```
sysctl vm.mmap_min_addr
```

returns "vm.mmap_min_addr = 65536", on Karmic.

Ya sure its proper? I mean apparently the highest number is suppose to be 65535?

---

### Post by Mornedhel on 2009-11-09
The documentation says : "This file indicates the amount of address space which a user process will be restricted from mmaping."

It's a quantity of memory, so a power of 2 makes sense, although I imagine any amount is legal. No upper bound is mentioned, either.

Quoted from : [http://www.linuxinsight.com/proc_sys_vm_mmap_min_addr.html](http://www.linuxinsight.com/proc_sys_vm_mmap_min_addr.html)

---

### Post by FuturePilot on 2009-11-09
> **MasterNetra said:**
> Ya sure its proper? I mean apparently the highest number is suppose to be 65535?

65536 is correct.

---

### Post by phrostbyte on 2009-11-09
This is a local kernel exploit, meaning the hax0r has to already be in your machine in order to root it. That is not a particularly easy thing to do. Secondly, you are only vulnerable to this in Ubuntu if you have Wine installed. This is one of **many** kernel exploits (most of which have been plugged already) that take advantage of the same issue, null pointer derefs on Intel processors, and unfortunately this is probably not an issue that will ever go away for good on current hardware.

---

### Post by Mornedhel on 2009-11-09
> **phrostbyte said:**
> This is a local kernel exploit, meaning the hax0r has to already be in your machine in order to root it. That is not a particularly easy thing to do. Secondly, you are only vulnerable to this in Ubuntu if you have Wine installed. This is one of **many** kernel exploits that take advantage of the same issue, null pointer derefs on Intel processors, and unfortunately this is probably not an issue that will ever go away for good on current hardware.

What he said.

However, user access is relatively easy to obtain. All you need is good old social engineering: "save this to your Desktop and execute it to install a dancing bunny screensaver". Then privilege escalation occurs.

Or ssh'ing with a password dictionary, or with the user's mother's maiden name, etc.

Well, the usual basic security advice applies: get a decent password, don't blindly execute anything.

---

### Post by phrostbyte on 2009-11-09
> **Mornedhel said:**
> 
However, user access is relatively easy to obtain. All you need is good old social engineering: "save this to your Desktop and execute it to install a dancing bunny screensaver". Then privilege escalation occurs.

Or ssh'ing with a password dictionary, or with the user's mother's maiden name, etc.

I don't agree with this, first of all, even if there is no privildge escalation vuln on a machine, if you run a random binary from the Internet, regardless if it gets root or not, it is capable of causing havok. Up to and including send over your entire home directory to the hacker, personal files and all. You do not need ROOT to do this, ever! On Windows, there is a a lot of user mode viruses now. 

Also by default there is no way to SSH into an Ubuntu computer, even the server edition. This has to be explicitly enabled by installing [this]("apt:openssh-server").

> **Mornedhel said:**
> 
Well, the usual basic security advice applies: get a decent password, don't blindly execute anything.

++

You should NEVER execute random shell scripts or binaries off the Internet, regardless if you "sudo" it or not.

Personally I think sudo is a stupid idea, I think it gives people a false sense of security. That they can run anything they want as long as they don't sudo it, they will be safe. Well that is wrong.

---

### Post by Mornedhel on 2009-11-09
> **phrostbyte said:**
> I don't agree with this, first of all, even if there is no privildge escalation vuln on a machine, if you run a random binary from the Internet, regardless if it gets root or not, it is capable of causing havok. Up to and including send over your entire home directory to the hacker, personal files and all. You do not need ROOT to do this, ever! On Windows, there is a a lot of user mode viruses now.

Well, sure. But root access gets *really* interesting if you get it on an large corporation's network, where retrieving data from any user is more interesting than thrashing a single home directory or a single machine, or installing a bot.

> **phrostbyte said:**
> Also by default there is no way to SSH into an Ubuntu computer, even the server edition. This has to be explicitly enabled by installing [this]("apt:openssh-server").

Yes, this is true. But any machine that does have an SSH server installed and is exposed to the Internet *will* get attempts to brute-force one's way for ssh access, and then in the default configuration (accept connection from any address) your last defense is your username/password.

> **phrostbyte said:**
> Personally I think sudo is a stupid idea, I think it gives people a false sense of security. That they can run anything they want as long as they don't sudo it, they will be safe. Well that is wrong.

I don't know... The alternative was enabling a root account (which reduces security for brute-forcing password, for starters, since you don't have to guess a username). Then users would think they can run anything as long as they aren't logged as root. With sudo you have a finer control on who can do what and the users make exactly the same (false) assumptions.

---

### Post by MasterNetra on 2009-11-09
I successfully created a startup script to take care of this each time I reboot.
For those interested: [http://ubuntuforums.org/showthread.php?t=1320622](http://ubuntuforums.org/showthread.php?t=1320622)
^.^ Simple script but does what it is suppose to. :)

---

### Post by xpto09 on 2009-11-09
[http://www.h-online.com/open/news/item/Hole-in-the-Linux-kernel-allows-root-access-850016.html](http://www.h-online.com/open/news/item/Hole-in-the-Linux-kernel-allows-root-access-850016.html)

[http://www.sidux.com/](http://www.sidux.com/)
The current [Kernel exploit]("http://www.h-online.com/open/news/item/Hole-in-the-Linux-kernel-allows-root-access-850016.html") will be published very soon and so become exploitable.
Current sidux kernels are not affected.
Every user can test easily by running:  [COLOR=#ff0000]*sysctl vm.mmap_min_addr*[/COLOR]
 This should return a non-zero value
If it returns zero (possible with quite old sidux kernels) please update your kernel immediately


ubuntu@ubuntu-desktop:~$ sysctl vm.mmap_min_addr
vm.mmap_min_addr = 0



Is this correct?


I am using 9.10
ubuntu@ubuntu-desktop:~$ uname -a
Linux ubuntu-desktop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

---

### Post by Tony Ricena on 2009-11-09
If you are receiving a response of 0 then no..

Have you updated your kernel libs?  Use Synaptic Package Manager and see if any of your kernel libs and other programs are updated, if not sometimes its just easier to click on the Mark All Upgrades button.  Hope that helps

---

