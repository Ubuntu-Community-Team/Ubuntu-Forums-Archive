---
title: "What steps to take to mitigate newly discovered CVE-2016-5195 privilege-escalation?"
date: 2016-10-21
forum: Security
---

### Post by skyemoor on 2016-10-21
What steps can be taken to avert attack by CVE-2016-5195? Or is this already patched?

[http://arstechnica.com/security/2016/10/most-serious-linux-privilege-escalation-bug-ever-is-under-active-exploit/](http://arstechnica.com/security/2016/10/most-serious-linux-privilege-escalation-bug-ever-is-under-active-exploit/)

[INDENT]
"A serious vulnerability that has been present for nine years in virtually all versions of the Linux operating system is under active exploit, according to researchers who are advising users to install a patch as soon as possible.

While CVE-2016-5195, as the bug is cataloged, amounts to a mere privilege-escalation vulnerability rather than a more serious code-execution vulnerability, there are several reasons many researchers are taking it extremely seriously. For one thing, it's not hard to develop exploits that work reliably. For another, the flaw is located in a section of the Linux kernel that's a part of virtually every distribution of the open-source OS released for almost a decade. What's more, researchers have discovered attack code that indicates the vulnerability is being actively and maliciously exploited in the wild.

"It's probably the most serious Linux local privilege escalation ever," Dan Rosenberg, a senior researcher at Azimuth Security, told Ars. "The nature of the vulnerability lends itself to extremely reliable exploitation. This vulnerability has been present for nine years, which is an extremely long period of time."

The underlying bug was patched this week b[/INDENT]y the maintainers of the official Linux kernel. Downstream distributors are in the process of releasing updates that incorporate the fix. Red Hat has classified the vulnerability as "important."

---

### Post by howefield on 2016-10-21
> **skyemoor said:**
> What steps can be taken to avert attack by CVE-2016-5195? Or is this already patched?

Update your system..

[https://www.ubuntu.com/usn/](https://www.ubuntu.com/usn/)

---

### Post by anoda on 2016-10-21
Hello. Yes, **howefield** is right. Yesterday an unpdate for this CVE was available. Just use update-manager or run [COLOR=#008000]sudo apt-get update[/COLOR] and [COLOR=#008000]sudo apt-get dist-upgrade[/COLOR]. By the way, this bug is from 2005.

---

### Post by ewren on 2016-10-26
> **anoda said:**
> Hello. Yes, howefield is right. Yesterday an unpdate for this CVE was available. Just use update-manager or run sudo apt-get update and sudo apt-get dist-upgrade. By the way, this bug is from 2005.


Hi,

Just found this thread now. I am trying to update my 12.04 box to protect against this vulnerability.

I have run:

sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade

and updated my system and then rebooted.

However using the POC exploit code here:
[http://www.cyberciti.biz/faq/dirtycow-linux-cve-2016-5195-kernel-local-privilege-escalation-vulnerability-fix/](http://www.cyberciti.biz/faq/dirtycow-linux-cve-2016-5195-kernel-local-privilege-escalation-vulnerability-fix/)

My system is still vulnerable to this attack. How can I be sure that the upgrade successfully installed the correct patches.

Thanks

---

### Post by howefield on 2016-10-26
Perhaps you are you running an unsupported HWE kernel, what's the output of 

```
uname -r
```
```
cat /etc/*-release
```

---

### Post by ewren on 2016-10-26
Thanks for the quick reply.

After upgrading the box the output is as follows:

```

$ uname -r
3.5.0-54-generic
```


```

$ cat /etc/*-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.5 LTS"
NAME="Ubuntu"
VERSION="12.04.5 LTS, Precise Pangolin"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu precise (12.04.5 LTS)"
VERSION_ID="12.04"

```

---

### Post by howefield on 2016-10-26
I haven't checked in detail but that looks like the Quantal HWE kernel which was supported for 18 months ending when Ubuntu 14.04 was released in April 2014, so as a now unsupported kernel it is pretty unlikely it would be patched.

---

### Post by Habitual on 2016-10-26
> **ewren said:**
> Hi,

Just found this thread now. I am trying to update my 12.04 box to protect against this vulnerability.

I have run:

sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade

and updated my system and then rebooted.

However using the POC exploit code here:
[http://www.cyberciti.biz/faq/dirtycow-linux-cve-2016-5195-kernel-local-privilege-escalation-vulnerability-fix/](http://www.cyberciti.biz/faq/dirtycow-linux-cve-2016-5195-kernel-local-privilege-escalation-vulnerability-fix/)

My system is still vulnerable to this attack. How can I be sure that the upgrade successfully installed the correct patches.

Thanks
I ran
do-release-upgrade
yesterday on a 12.04 in Amazon after 
```
 sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```
failed to install a newer kernel.

We got ```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.5 LTS"
NAME="Ubuntu"
VERSION="14.04.5 LTS, Trusty Tahr"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 14.04.5 LTS"
VERSION_ID="14.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
```and **3.13.0-100-generic**
YMMV.

---

### Post by ewren on 2016-10-26
Okay, I tried this instead:

```

sudo apt-get install linux-generic-lts-trusty

```

And now I have:

```



3.13.0-100-generic



```

and

```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.5 LTS"
NAME="Ubuntu"
VERSION="12.04.5 LTS, Precise Pangolin"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu precise (12.04.5 LTS)"
VERSION_ID="12.04"

```

and it seems to have fixed the issue.

Thanks!

---

### Post by Habitual on 2016-10-26
Well, I guess the difference is "do we want to upgrade the system, or just the kernel"?
Since mine are in Amazon, I chose an upgrade to take advantage of both.
Glad it worked out!

I did see [https://ubuntuforums.org/showthread.php?t=2341177&p=13561688#post13561688](https://ubuntuforums.org/showthread.php?t=2341177&p=13561688#post13561688) prior to my decision, and in ignorance,
I thought 'apt-get dist-upgrade' covered it.

---

### Post by howefield on 2016-10-26
> **ewren said:**
> ...and it seems to have fixed the issue.

Cool, well done on sussing it out.

Bear in mind that you'll likely have more upgrading to do next April as 12.04 hits the end of the road :)

---

### Post by RichardET on 2016-10-29
uname -r
4.4.0-45-generic

Presumably this kernel does not have the bug?

---

### Post by howefield on 2016-10-29
> **RichardET said:**
> Presumably this kernel does not have the bug?

Sort of.. I believe you need to have 4.4.0-45.66 to be patched. What's the output of..

```
apt-cache policy linux-image-4.4.0-45-generic
```

```
apt-cache policy linux-image-4.4.0-45-generic 
linux-image-4.4.0-45-generic:
  Installed: 4.4.0-45.66
  Candidate: 4.4.0-45.66
  Version table:
 *** 4.4.0-45.66 500
        500 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
        100 /var/lib/dpkg/status
```

[https://people.canonical.com/~ubuntu-security/cve/2016/CVE-2016-5195.html](https://people.canonical.com/~ubuntu-security/cve/2016/CVE-2016-5195.html)

---

### Post by RichardET on 2016-10-29
Installed: 4.4.0-45.66
  Candidate: 4.4.0-45.66
  Version table:
 *** 4.4.0-45.66 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 Packages
        100 /var/lib/dpkg/status


Thus I guess I have the correct updates installed.

---

### Post by howefield on 2016-10-29
> **RichardET said:**
> ...Thus I guess I have the correct updates installed.

Yep, jobs a good 'un.

---

