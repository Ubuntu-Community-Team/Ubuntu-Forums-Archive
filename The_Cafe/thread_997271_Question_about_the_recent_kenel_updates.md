---
title: "Question about the recent kenel updates"
date: 2008-11-29
forum: The Cafe
---

### Post by diablo75 on 2008-11-29
I caught wind of recent security patches to the Kernel while browsing digg earlier today.  The article it linked to can be found here:

[http://news.softpedia.com/news/Newly-Discovered-Kernel-Vulnerabilities-Affect-All-Ubuntu-Users-98864.shtml](http://news.softpedia.com/news/Newly-Discovered-Kernel-Vulnerabilities-Affect-All-Ubuntu-Users-98864.shtml)

I've already update, and am not concerned with it much.  But I have a question about the very last paragraph in the article:

> Due to an unavoidable ABI change, the kernel packages have a new version number, which will force you to reinstall or recompile all third-party kernel modules you might have installed. 

I've seen first hand that I've had to recompile my Virtualbox kernel headers.  But I was wondering what it means by "unavoidable ABI change".  What does that mean?  Will I have to worry about recompiling kernel headers again in the future.  Or will the DKMS package take care of that for me (as I had originally expected it to in this instance before reading that in the article).

Edit:  Sorry... Meant to spell the word KERNEL updates in the title.  If you're a mod can you change that please?

---

### Post by sefs on 2008-11-29
Interesting....

As a general rule i usually reinstall all the programs on my system anytime i see a kernel update coming down. Which would be vmware, truecrypt and serial monkey drivers...

I thought dell had some tech in ubuntu that made this unnecessary.

---

### Post by diablo75 on 2008-11-29
> **sefs said:**
> I thought dell had some tech in ubuntu that made this unnecessary.

[http://en.wikipedia.org/wiki/Dynamic_Kernel_Module_Support](http://en.wikipedia.org/wiki/Dynamic_Kernel_Module_Support)

And I have it installed.  But this time around it did not serve it's intended purpose.

---

### Post by bruce89 on 2008-11-29
> **diablo75 said:**
> [http://en.wikipedia.org/wiki/Dynamic_Kernel_Module_Support](http://en.wikipedia.org/wiki/Dynamic_Kernel_Module_Support)

And I have it installed.  But this time around it did not serve it's intended purpose.

Some things use it, and others don't. Look at the rdepends of dkms:

> bruce@Scooby-Dum:~$ apt-cache rdepends dkms
dkms
Reverse Depends:
  nvidia-177-kernel-source
  nvidia-173-kernel-source
  fglrx-kernel-source
  nvidia-96-kernel-source
  lirc-modules-source
  virtualbox-ose-source
  virtualbox-ose-guest-source
  lirc-modules-source
  kvm-source
  kqemu-source
  nvidia-96-kernel-source
  nvidia-71-kernel-source
  nvidia-177-kernel-source
  nvidia-173-kernel-source
  fglrx-kernel-source


---

### Post by diablo75 on 2008-11-29
> **bruce89 said:**
> Some things use it, and others don't. Look at the rdepends of dkms:

Ahhh, so the OSE version of Virtualbox makes use of it, but not the proprietary version... is that right?

---

### Post by FuturePilot on 2008-11-30
> **diablo75 said:**
> Ahhh, so the OSE version of Virtualbox makes use of it, but not the proprietary version... is that right?

If I remember correctly the PUEL version also makes use of DKMS.

---

