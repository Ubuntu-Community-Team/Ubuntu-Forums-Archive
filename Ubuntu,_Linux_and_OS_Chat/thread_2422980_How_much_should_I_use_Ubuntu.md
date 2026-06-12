---
title: "How much should I use Ubuntu?"
date: 2019-07-15
forum: Ubuntu, Linux and OS Chat
---

### Post by nickjonson on 2019-07-15
I am a new user of ubuntu. Which version should I use to run the VM more stable and error-free?

---

### Post by wildmanne39 on 2019-07-15
Hello and welcome to the forum!

*Thread moved to **Ubuntu, Linux and OS Chat a more appropriate sub-forum**.*

---

### Post by nickjonson on 2019-07-15
Thanks for the welcome

---

### Post by uRock on 2019-07-15
I'd recommend the LTS release. It's older and the devs aim to keep it as stable as possible.

---

### Post by nickjonson on 2019-07-16
> **uRock said:**
> I'd recommend the LTS release. It's older and the devs aim to keep it as stable as possible.
Can you introduce me? Thank you

---

### Post by uRock on 2019-07-16
What information are you looking for? Have you used any form of Linux desktop operating system before?

You can download the image here. [https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)

---

### Post by nickjonson on 2019-07-16
> **uRock said:**
> What information are you looking for? Have you used any form of Linux desktop operating system before?

You can download the image here. [https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)
Thank you

---

### Post by TheFu on 2019-07-16
The choices are between the different 18.04 variants.  That isn't really up for discussion.  LTS releases are in April of even years.  12.04, 14.04, 16.04, 18.04 and 20.04 ... see how that aligns?  Any other releases are, by definition, NOT LTS. They are used by Canonical to try out new features, usually most things are fine, but sometimes there are really bad issues, usually the first time a new technology is forced before it is ready.  Wayland was pushed before it was ready in 17.10.   For many users, it was a bad situation.  19.10 promises to have similar problems due to snaps being pushed more and more, breaking many common workflows.  The good news is that Wayland is getting better and is ready for more people to use.  So, 18.10, 19.04 are non-LTS and each has been used to trial new tech that hasn't always worked perfectly.

There is also the question as to which hypervisor you plan to use.  Enterprises use KVM+QEMU or much less, Xen.  Desktop people tend to learn on either Oracle VirtualBox or VMWare Workstation before moving to KVM.  KVM is the most stable hypervisor on Linux because it is part of the Linux Kernel and tested with the kernel.

Is this for a desktop or a server as the host?  
If it is a server then using Ubuntu Server 18.04 LTS. In Unix, servers don't have any GUI.  Are you prepared for that?

If it is for a desktop, then I would suggest using one of the lighter DEs, like XFCE or LXQt or Mate on Ubuntu 18.04. There are specific distros. If you have a high-end GPU, you might want the standard Gnome3 Ubuntu Desktop.

Will the VMhost be a desktop  or server?  
If it is a desktop, I suspect you are mainly interested in running desktop-on-desktop virtualization.  Many people new to virtualization have many misconceptions, like thinking their physical hardware will be used by the guest VMs.  It will not.  Guests only see virtual hardware. This is very frustrating for people with high-end GPUs.

Are the VMs absolutely critical infrastructure or play things?
For critical infra, use Ubuntu Server and KVM. Period.

Do you have another Linux workstation to remotely manage and access the VMs or not?
If you don't have another Linux workstation, then using Ubuntu Server on the VM host will probably be a hassle.  Using a desktop for the VM host raises security risks and wastes resources that would better be used by the guest VMs.

On Unix systems, most administration is performed either using ssh or ssh-tunnels. This includes management of VMs and the VM host.  How's your skills with ssh?

If you need a point-n-click type interface, there are other considerations too.  Learning Linux has a very steep curve if you don't already have an intermediate Unix skillset.  Windows knowledge seldom transfers well. The overall philosophies are extremely different between Unix-like systems and Windows.  Unix systems will let users do dumb things. Don't expect any protection against that. If you ask the system to delete itself, it will, usually without any "are you certain" confirmation.

---

### Post by an-ordered-hole on 2019-07-20
Ubuntu is updated like every 6 months and a lot of software is packaged to work together. However, this might mean software may not be up to date. For instance the last ubuntu install I did came with python2 on it and python3 has been available for like 11 years.  I found ubuntu works well with the software prepackaged in it but once you start changing it can be problematic. 

I mainly install ubuntu on computers I find and fix up. It's fun to network old computers and access them via ssh. Org-mode for emacs is rather fun. Just do the latest LTS release and learn on that rather than going distribution shopping and don't change anything unless you have an absolute need to.

I found this video series helpful for orientation:

[https://www.youtube.com/watch?v=Yxikwcqz8D0](https://www.youtube.com/watch?v=Yxikwcqz8D0)

---

### Post by TheFu on 2019-07-20
Python3 has been available on Ubuntu for a very long time, just not as the default so that compatibility is there.  Use
#!/usr/bin/env python3 
on the 1st line of your scripts to access the built-in version.  However, if you are a professional scripter in any scripting language, it is SOP (best practice) to use an environment management tool like pyenv to have your own python versions installed so you pick which you want to use in each project.  If you are writing your own apps in any scripting language, you don't want to be stuck using the default versions or libraries maintained by someone outside your team.  This is especially important for webapps.

Other scripting languages have tools like this too - also best practice:
Ruby has rbenv or rvm.
Perl uses perlbrew.

As for running current versions of any specific program, most teams will have their own PPA, which extends the entire APT packaging system so once you add the PPA, it is no different to install and update to the latest versions than using Canonical's repos.  All the packages are still cryptographically signed and validated after download.  Dependencies are still included and each PPA is for a specific release, so dependencies don't get out of whack.

This is a main reason that maintaining Windows installations suck in comparison to any APT-based Linux.  At least for me.

---

### Post by an-ordered-hole on 2019-07-20
Generally the tech stuff only makes sense if you've been in the game a while. You'll find a lot of stipulate definitions for things that only have meaning indexed from obscure additions. You cannot make sense of it just by observing it in it's current state re: it's not intuitive. Documentation for software is often a rats-nest and techies are often trolls. 

Go slow and steady and branch out gently and only when you have a specific need for something.

---

### Post by DuckHook on 2019-07-20
> **an-ordered-hole said:**
> …Documentation for software is often a rats-nest and techies are often trolls.
You appear to mean well, so I will take it in the spirit (hopefully) intended.

I agree with the first part of your statement, but the second part is problematic: it is a generalization that paints with too broad a brush.

I doubt that techies are more prone to trolling than folks in any other walk of life. However:

[LIST]
[*]techies are techies for a reason; for the same reason that they are not poets or social workers,
[*]techies focus on problem-solving; not emoting or effusiveness,
[*]techies will sometimes apply their analytical outlook to the point of abruptness and not realize it.
[/LIST]
To be sure, there are outright trolls within the tech community and the staff have had lots of experience dealing with them but, by and large, the tech community is as helpful and accommodating as any other.

> Go slow and steady and branch out gently and only when you have a specific need for something.
&#8593;+1

---

