---
title: "ClamAV is outdated"
date: 2011-02-18
forum: Security
---

### Post by francwalter on 2011-02-18
Hello,

i have Ubuntu 8.04 LTS and i am running ClamAV 0.96.5 on it.
In my logfile i get a warning:

>  WARNING: Your ClamAV installation is OUTDATED! 
  WARNING: Local version: 0.96.5 Recommended version: 0.97 but i don't find any sources for the newest 0.97 for aptitude, i guess there aren't even backports for it, is it?

So what to do?

Waiting or compiling? 
Is there hope for a actual package for ubuntu?

Thank you,
kindly regardings,

franc

---

### Post by cariboo on 2011-02-18
8.04 Desktop will eol in April of this year, you may want to considered updating to 10.04.

---

### Post by francwalter on 2011-02-18
Unfortunately this is not possible as it is a virtual server.
Update to 10.04 won't run, they told us.
We still have a very old 2.6.9 kernel and it is not possible to change this.

---

### Post by cariboo on 2011-02-18
You may want to talk to your it guys then, with a kernel that old, you may have all sorts of security problems that clamav won't help.

---

### Post by francwalter on 2011-02-18
Hm. 
I am the IT guy ;-)
But the provider doesn't provide much newer kernels on his vps-host.
What to do?
Move?

---

### Post by SeijiSensei on 2011-02-19
> **francwalter said:**
> Move?

I would.  My provider, Linode, currently offers [all these up-to-date distributions](http://www.linode.com/faq.cfm#which-distributions-do-you-offer).  I use the older CentOS 5.5 myself on servers because I came from RedHat, and because some of the software I use is better supported on that platform.

That said, you could just compile your own copy of ClamAV.  I've built it from source a number of times in the past, typically when I've been in the same situation as you.  If you haven't built it before, run "sudo apt-get build-dep clamav" to install the dependencies, then get the source from clamav.net.  It will probably install into /usr/local.  You should also run "sudo apt-get purge clamav" after you've built your own copy to avoid conflicts.

---

### Post by Trapper on 2011-02-19
> **francwalter said:**
> Hello,

i have Ubuntu 8.04 LTS and i am running ClamAV 0.96.5 on it.
In my logfile i get a warning:
but i don't find any sources for the newest 0.97 for aptitude, i guess there aren't even backports for it, is it?
So what to do?
Waiting or compiling? 
Is there hope for a actual package for ubuntu?
franc

Yeah, there's a PPA to get ubuntu untested packages from. Unfortunately, there isn't even a 0.97 package available there yet.

Here's some Ubuntu documentation concerning clamav and how to utilize the ppa repository:

[https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)


UPDATE!!!! See here for 0,97:

[http://ubuntuforums.org/showthread.php?t=1684007](http://ubuntuforums.org/showthread.php?t=1684007)

---

### Post by heli2reg on 2012-01-02
> **Trapper said:**
> Yeah, there's a PPA to get ubuntu untested packages from. Unfortunately, there isn't even a 0.97 package available there yet.
 
Here's some Ubuntu documentation concerning clamav and how to utilize the ppa repository:
 
[https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)
 
 
UPDATE!!!! See here for 0,97:
 
[http://ubuntuforums.org/showthread.php?t=1684007](http://ubuntuforums.org/showthread.php?t=1684007)
 
So... in this thread folks are talking mainly about Ubuntu 8.04 (LTS) and ClamAV 0.97. The link you posted refers to maverick, which is Ubunutu 10.10.
 
Are you saying that by adding the link to the maverick repo you can update ClamAV to 0.97 on Ubunutu 8.04 LTS as well? Will it even update / be compatible?
 
Thanks!

---

### Post by francwalter on 2013-01-29
By the way now I am on Ubuntu 12.04 LTS and had the same ClamAV problems again.
I found this source:

**[https://launchpad.net/~ubuntu-clamav/+archive/ppa](https://launchpad.net/~ubuntu-clamav/+archive/ppa)**

I added it to **sources.list** and did:

[B]aptitude install python-software-properties
add-apt-repository ppa:ubuntu-clamav/ppa
aptitude update[/B]

Now I have the newest ClamAV packages and no worries about these outdated-alarms in logwatch :)

frank

---

