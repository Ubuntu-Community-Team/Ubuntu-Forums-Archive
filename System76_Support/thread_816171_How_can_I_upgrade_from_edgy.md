---
title: "How can I upgrade from edgy?"
date: 2008-06-02
forum: System76 Support
---

### Post by desconocido on 2008-06-02
Hello,

I installed Ubuntu 6.10 (edgy) recently from a DVD that came with a magazine.

That worked OK and then I wanted to install Firestarter.

So I followed the advice in [http://www.fs-security.com/docs/installation.php:](http://www.fs-security.com/docs/installation.php:) "Ubuntu users can install Firestarter by enabling the "universe" repository in the /etc/apt/sources.list file or in synaptic under Settings->Repositories. Having enabled the repository, the procedure is the same as in Debian."

Unfortunately that gives me various error messages of the form:

[http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
etc.

which I imagine is because edgy is no longer supported and is no longer available under [http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/).

No problem I thought. I will upgrade 6.10 to 7.04 using the Update Manager.
So I followed the advice in [https://help.ubuntu.com/community/FeistyUpgrades](https://help.ubuntu.com/community/FeistyUpgrades)
"The latest version of Update Manager (0.45.2) must be installed before you upgrade. Otherwise, you will receive an Authentication failed error." As I only had 0.45.0 I did 

"If you only want to update the update-manager package, open System/Administration/Synaptic Package Manager and click on "Search", then type "update-manager". Verify in the "Latest Version" column that 0.45.2 is available and install it. If it is not available click on "Reload". If it is still not available after a reload, open Settings/Repositories and make sure that the "Internet Updates/Recommended updates" checkbox is checked. After a reload the update package will be available."

But that gives me the same problem that I had above!

Can anyone suggest a way round this? Can I download 0.45.2 from somewhere else?

By the way, due to problems I will describe in another post, the computer will not boot from any CD except the DVD I got edgy from. So I can't do a clean install of Ubuntu 8.04 (hardy) from the CD I have in the normal way. But I can read the CD. Is there anyway of running Ubuntu from my hard disk and then installing hardy from the CD onto the hard disk?

Thanks in advance.

---

### Post by thomasaaron on 2008-06-02
Which computer model are you using?
Did you try installing from an 8.04 CD using Safe Graphics Mode?

---

### Post by prshah on 2008-06-02
> **desconocido said:**
> way. But I can read the CD. Is there anyway of running Ubuntu from my hard disk and then installing hardy from the CD onto the hard disk?

 
Get the _alternate_ cd image of Feisty, Gutsy or Hardy. When running your Ubuntu 6.06, if you pop in your alternate CD, it will ask to whether you want to upgrade. Note that it will ask this only ONCE, so be alert to select that option.

If you miss that option, post back here for instructions to start a manual alternate CD upgrade.

---

### Post by desconocido on 2008-06-16
Thanks for your suggestions. But I shortcircuited all that by buying a new (working!) CD reader and installing hardy.

---

### Post by desconocido on 2008-06-16
> **thomasaaron said:**
> Which computer model are you using?

Packard Bell imedia with 32 bit processor.  

> Did you try installing from an 8.04 CD using Safe Graphics Mode?

No, but I think the hardware problem with the CD reader was the cause. See my comment elsewhere near here.

> 1. What version of Ubuntu are you using? (Ubuntu, Kbuntu, Xubuntu | 32-bit, 64-bit)
32 bit processor. ubuntu desktop.

> 2. What is your System 76 Model Number?


Interesting, never heard of System 76.
> 3. What have you already tried?
Just the stuff in my first post.

---

### Post by walkeraj on 2008-06-16
> **desconocido said:**
> Interesting, never heard of System 76.

It's a company that sells pre-installed linux machines.  This forum is for support for those machines only.  You probably want to be in one of the main forums.

---

### Post by desconocido on 2010-08-07
> **walkeraj said:**
> It's a company that sells pre-installed linux machines.  This forum is for support for those machines only.  You probably want to be in one of the main forums.

You are right. All sorted now, I am using Karmic.

---

