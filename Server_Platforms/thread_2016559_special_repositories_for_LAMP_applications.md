---
title: "special repositories for LAMP applications?"
date: 2012-07-04
forum: Server Platforms
---

### Post by sohmc on 2012-07-04
I rent a VPS (Virtual Private Server), which means that my linux installation runs off of OpenVZ.  For those unfamiliar with OpenVZ, it allows you to run a bunch of Linux-based VMs with very few resources.

OpenVZ is in it of itself a Linux distribution that runs it's own kernel.  So if I want to run the latest and greatest Ubuntu installation (12.04 LTS), I have to wait for my provider to support it.  In the mean time, my system remains vulnerable since I don't run the latest software packages, mainly Apache, MySQL, and PHP.

I imagine that I'm not the only person in this boat.  I've noticed that the repositories for 11.10 (what I'm running now) don't have the latest of any of these applications.  Is there a custom repository that provides the latest versions of LAMP software?  If so, can so one provide a link?  I've search google to no avail.

---

### Post by SeijiSensei on 2012-07-04
If you don't mind having things go wrong and need to reinstall the VM, I'd try running "sudo do-release-upgrade" from the command prompt.  That should take you to 12.04.  Now if the VM provider has done some squirrelly things with the Ubuntu image they provide, an upgrade might not be possible.

I've generally found the easiest solution is simply to rent another VM for a while and test things out on it.  Then if everything is working correctly, I'll just switch to the new VM and release the old one.  I use [Linode]("http://www.linode.com/") as my provider, and they refund back any unused portion of the rental fee, so there's no financial penalty involved with starting a new VM.  Other than the minor DNS issues associated with the change in IP address, this is a pretty easy solution to use in a VM environment.

---

### Post by sohmc on 2012-07-04
As stated in my original post, doing the update is not an option.  I tried upgrading to 12.04 but get an error saying that the kernel is not compatible.  

What I'm really looking for is the repository that holds the latest LAMP software.  I've tried building from source but a couple of existing packages didn't really like it.  (Specifically, it was postfix that was complaining that MySQL was not installed.)

I was able to find [this site](https://launchpad.net/ubuntu/+source/mysql-5.5/) but it looks like it's only for the latest Ubuntu.

---

### Post by SeijiSensei on 2012-07-05
Have you tried installing the 12.04 packages on your 11.10 system?  That can work in situations where the new packages don't have strict dependency requirements that cannot be fulfilled by the libraries you already have.

---

