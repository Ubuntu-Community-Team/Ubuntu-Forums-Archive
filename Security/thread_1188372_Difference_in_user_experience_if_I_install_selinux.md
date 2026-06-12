---
title: "Difference in user experience if I install selinux?"
date: 2009-06-15
forum: Security
---

### Post by pythonscript on 2009-06-15
I'm a beginning ubuntu jaunty user, and I'm thinking about installing selinux. How much would this change the basic user experience of my ubuntu installation? Right now, I only use basic terminal commands (chmod +x on my scripts, mostly) and for office document processing, internet browsing, listening to music, and basic python programming. How, if at all, would installing selinux affect these activities? Sorry about the vague question; I wasn't really sure how to phrase this. Thanks in advance!

---

### Post by bodhi.zazen on 2009-06-15
Selinux does (should) not affect normal activities.

i suggest you take Fedora 11 for a spin if you want to try selinux. If you like, try to install it on Ubuntu (can be problematic).

---

### Post by HermanAB on 2009-06-15
Hmm, on Ubuntu, if you enable SELinux, then almost everything will be broken.

Note that the purpose of Mandatory Access Control is really to allow a single system to process information with differing levels of classification. For example, if you load Confidential data onto a Secret system then the data will immediately become Secret, unless your system uses SELinux to keep the data apart. Unless you are working for a government or defence department, then it is not of much use.

---

### Post by pythonscript on 2009-06-15
> Selinux does (should) not affect normal activities.

and 

> 
 on Ubuntu, if you enable SELinux, then almost everything will be broken.



These seem like widely conflicting opinions here. Is there something I'm missing? Thanks for the quick replies.

---

### Post by bodhi.zazen on 2009-06-15
ubuntu uses Apparmor by default.

selinux is not easy to install and configure, more so if you are unfamiliar with it and how it works.

I have never broken ubuntu with selinux so I do not share HermanAB's experience with it.

Yes if selinux is misconfigured it will lock out even root so I can see where a system could be broken, although that has not been my experience with it.

I was unable to configure selinux on Ubuntu 8.10 or Ubutnu 9.04 (it works with 8.04).

selinux is a fairly sophisticated tool and there are very few on these forums with much experience with it. Even on the Fedora forums many people simply turn it off.

Again, if you want to try selinux I advise you try Fedora or Centos. If you like it you can try to install it on Ubuntu.

---

### Post by rookcifer on 2009-06-15
Good luck with installing SELinux on Ubuntu.  Even though it appears to be unofficially supported, it is a PITA.  Like bodhi said, if you want SELinux then use Fedora.

That said, AppArmor will do what you need, imo.

---

### Post by HermanAB on 2009-06-15
If you really want to play with SELinux, then you have to buy the book.  Otherwise you won't get far.

SELinux has three modes.  If you activate it and the system still works, then you haven't enabled 'Enforcing Mode' correctly...
;)

---

### Post by Chemical Imbalance on 2009-06-15
If you are new to Linux, I definitely recommend you wait a while before trying that.  Either do like OP recommended and try Fedora 11 (includes a nice implementation of SElinux by default) or do some serious reading up on it first.  I'd wait until you are comfortable with Linux and Bash first.  Distros have problems implementing it themselves.  SElinux can cause some serious headaches.

---

### Post by movieman on 2009-06-15
> **HermanAB said:**
> Unless you are working for a government or defence department, then it is not of much use.

Sorry, but that's nonsense; SELinux, will, for example, prevent a hack that breaks into your Apache server from being used to access any files on the system other than those which are available to said web server. Just because you're not working for the CIA, that doesn't mean it won't be beneficial.

However, while it works well on Fedora-based OSes, I've never got it to work on a Debian-based OS: building a policy from scratch is hard.

---

### Post by kitplummer on 2009-06-25
Is anyone maintaining the SELinux on Ubuntu effort?  Makes sense that 8.04 works (as an LTS release) though.  But, would be nice to see it continue to support future versions - or Ubuntu continue to support SELinux.

---

### Post by rookcifer on 2009-06-25
> **HermanAB said:**
> Hmm, on Ubuntu, if you enable SELinux, then almost everything will be broken.

Note that the purpose of Mandatory Access Control is really to allow a single system to process information with differing levels of classification. For example, if you load Confidential data onto a Secret system then the data will immediately become Secret, unless your system uses SELinux to keep the data apart. Unless you are working for a government or defence department, then it is not of much use.

SELinux is more than a MAC and is used for more than data separation.

OP, just use AppArmor.

---

### Post by the8thstar on 2009-07-02
I installed it and it didn't break Ubuntu 9.04. However I don't know where the GUI for configuring SELinux administrator is located now!

---

### Post by bodhi.zazen on 2009-07-02
It is a bit off topic, but here are some nice slide sets on SELinux ;

[SELinux for Everyday Users]("http://www.slideshare.net/PaulWay/selinux-for-everyday-users") 

[Slug 2009 06 SELinux For Sysadmins]("http://www.slideshare.net/PaulWay/slug-2009-06-selinux-for-sysadmins") 

I am afraid I am a bit old school with SELinux and use it primarily on servers, so manage selinux from the command line.

---

### Post by the8thstar on 2009-07-03
Well... the system update resulted in a system breakage. I was not able to remove SELinux through Synaptic but at least I solved the kernel panic problem by removing "selinux=1" in /boot/grub/menu.lst.

Oh well. So much for security.

---

### Post by bodhi.zazen on 2009-07-03
> **the8thstar said:**
> Well... the system update resulted in a system breakage. I was not able to remove SELinux through Synaptic but at least I solved the kernel panic problem by removing "selinux=1" in /boot/grub/menu.lst.

Oh well. So much for security.

If you want to try selinux, try Fedora.

SELinux is better supported in fedora and just because you had a problem installing it in Ubuntu does not mean selinux is difficult (selinux in Ubuntu is problematic).

---

### Post by the8thstar on 2009-07-05
> **bodhi.zazen said:**
> ...just because you had a problem installing it in Ubuntu does not mean selinux is difficult (selinux in Ubuntu is problematic).

I didn't imply that. But it DID break my system.

---

