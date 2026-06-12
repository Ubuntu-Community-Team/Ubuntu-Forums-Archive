---
title: "ClamAV antivirus Outdated, how to upgrade"
date: 2015-12-02
forum: Security
---

### Post by Bonnie_Hallow on 2015-12-02
Hi, whenever I try to update my ClamAV antivirus in the terminal, it says "ClamAV 0.98.7 is outdated and I need 0.99 ClamAV."  I have tried everything but I cannot upgrade my ClamAV Antivirus and I put every command I thought of in the terminal.  Can anyone offer me help so that I can upgrade to 0.99 ClamAV?  Thanks.

---

### Post by Bucky Ball on 2015-12-02
*Thread moved to **Security**.*
[I][B]
Ubuntu, Linux and OS Chat[/B][/I] is not a support area.

Welcome. Did you try searching the net for how to do it? Did you install ClamAV from the Software Centre (official repositories) or from a third-party? The former will upgrade ClamAV to the newest version that has been tested on your release. Here's how to update the virus definitions:

[https://duckduckgo.com/?q=update+clamav](https://duckduckgo.com/?q=update+clamav)

---

### Post by flocculant on 2015-12-02
0.98.7+dfsg-0ubuntu4 is the latest version in the repos

---

### Post by Bucky Ball on 2015-12-02
> **flocculant said:**
> 0.98.7+dfsg-0ubuntu4 is the latest version in the repos

Which ones? 14.04, 15.10? OP hasn't stated which release they're using. :)

---

### Post by Bonnie_Hallow on 2015-12-03
I have 14.04 Ubuntu Linux.  Here is what my Terminal says when I try to install the latest version of ClamAV "WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.98.7 Recommended version: 0.99
DON'T PANIC! Read http://www.clamav.net/support/faq"

I have tried everything that I know as a recent user to update my ClamAV anti virus to 0.99.  No luck.  Need help?

---

### Post by Bucky Ball on 2015-12-03
You are aware that if you keep the virus definitions up to date it doesn't matter that you are running a slightly older version of clamav? If you installed from the software centre, then the version you currently have is the version for your release. 

Up date the virus definitions and the protection will be no different than if you were using .99. To update definitions:

```
sudo freshclam
```

That's it. Your virus definitions are up-to-date, as new as they can be, regardless of your clam version.

---

### Post by Bonnie_Hallow on 2015-12-03
No I am new to Linux Ubuntu, so your going to have to forgive me if I ask dumb questions.

Was a Windows 8.1 user.  Tired of Windows.

Anyway tired of Microsoft.  Slow internet, never clearing there registry so web pages go faster. I have decided to use Linux and Ubuntu is the operating system I want to learn.  I know how to build computers and stuff, but I have just been using Microsoft and I am sick of it and Microsoft 10... NOT FOR ME.  Anyway thank you for your help and expect more questions along the way.

---

### Post by fugu2 on 2015-12-13
> **Bonnie_Hallow said:**
> "ClamAV 0.98.7 is outdated and I need 0.99 ClamAV."  So ubuntu repo's kinda lie to everyone IMO. you don't have 0.98.7 installed, but a modified version of 0.98.7. It's 0.98.7 with all the security holes plugged up. They just don't do a good job telling you thats whats going on.
In reality, you probably don't even need the updated version.

---

### Post by deadflowr on 2015-12-14
> **fugu2 said:**
> So ubuntu repo's kinda lie to everyone IMO. you don't have 0.98.7 installed, but a modified version of 0.98.7. It's 0.98.7 with all the security holes plugged up. They just don't do a good job telling you thats whats going on.
In reality, you probably don't even need the updated version.

The outdated message comes from clam's database.
So Clam's database sees the version as 0.98.7.
Security patches don't always magically change that.

---

### Post by SeijiSensei on 2015-12-14
Many updates to ClamAV are in response to attacks against the software by virus developers as in [this case](https://web.nvd.nist.gov/view/vuln/detail?vulnId=CVE-2015-1463). Often these are denial-of-service attacks that cannot be fixed without changing the underlying code.

For LTS versions like 14.04 Ubuntu developers typically "backport" security updates into the existing releases without changing the primary version number so ClamAV complains.

Frankly even if the fixes haven't been backported I would not worry too much about these kinds of attacks.  They're probably quite rare out in the real world.

---

### Post by bumbum2 on 2016-01-04
> **SeijiSensei said:**
> Many updates to ClamAV are in response to attacks against the software by virus developers as in [this case]("https://web.nvd.nist.gov/view/vuln/detail?vulnId=CVE-2015-1463"). Often these are denial-of-service attacks that cannot be fixed without changing the underlying code.

For LTS versions like 14.04 Ubuntu developers typically "backport" security updates into the existing releases without changing the primary version number so ClamAV complains.

Frankly even if the fixes haven't been backported I would not worry too much about these kinds of attacks.  They're probably quite rare out in the real world.

Thanks for the detailed reply.  I've been trying to figure out why it keeps telling me it's outdated even though it won't upgrade it.

---

### Post by patrikmellq on 2016-01-19
I think i have a solution for this, but is has nothing to do with updating the GUI (ClamTK) ...
I read that you can add and update ClamaAV the scanner with the latest with ppa.
Add:
ppa:ubuntu-clamav/ppa

> sudo add-apt-repository ppa:ubuntu-clamav/ppa
> sudo apt-get update

Now maybe you can run ClamAV using the terminal - search for a howto.
If this made you running the most present ClamAV - then sign this topic as SOLVED.

Cheers

---

### Post by deadflowr on 2016-01-19
> **patrikmellq said:**
> I think i have a solution for this, but is has nothing to do with updating the GUI (ClamTK) ...
I read that you can add and update ClamaAV the scanner with the latest with ppa.
Add:
ppa:ubuntu-clamav/ppa

> sudo add-apt-repository ppa:ubuntu-clamav/ppa
> sudo apt-get update

Now maybe you can run ClamAV using the terminal - search for a howto.
If this made you running the most present ClamAV - then sign this topic as SOLVED.

Cheers

Ignore the ppa, as it is now really out of date.
[https://launchpad.net/~ubuntu-clamav/+archive/ubuntu/ppa?field.series_filter=trusty](https://launchpad.net/~ubuntu-clamav/+archive/ubuntu/ppa?field.series_filter=trusty)
Currently it sits at: 
**0.98.5+dfsg-1~ubuntu14.04.1~ppa1**
Ubuntu 14.04 is now::
[B]0.98.7+dfsg-0ubuntu0.14.04.1

[/B]

---

### Post by patrikmellq on 2016-01-19
Yes you are correct - it did not work with my solution - still old version ...
Thanks for the help ...

---

### Post by neilsfarm on 2016-03-17
The latest version of the clamtk for debian is currently 5.20. Homepage for clamtk has version 5.19 for ubuntu/debian.

The latest clamav source code stable build is tarball of version  99.1 its  readme files last noted change is for version 97.5 While I have built  from source code this is not something I would do with Clam.

  i have  read clamtk is moving to use gtk3.

I am using 5.20 and freshclam getting the same error message , which I am ignoring  and waiting for the next version of  clamav in the ubuntu repository to hopefully  fix this.

---

