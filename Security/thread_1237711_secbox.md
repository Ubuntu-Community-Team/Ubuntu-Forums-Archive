---
title: "secbox?"
date: 2009-08-11
forum: Security
---

### Post by Ichido on 2009-08-11
From [http://www.tech-faq.com/blog/ubuntu-security-tools.html](http://www.tech-faq.com/blog/ubuntu-security-tools.html)

Has anyone used this?

Bootable Linux distributions are quite popular right now. Just by booting from a DVD or other media, they allow you to possess a dedicated security auditing or forensics workstation.

Usually though, I don’t want to reboot just to use a different set of applications. I want all of my applications available to me all of the time.

I normally use Synaptic Package Manager to add each application to my Ubuntu system manually. This is time consuming, but eventually allows me to create a system with a rich set of security tools.

A better approach is to call apt-get directly. This is much quicker than using the Synaptic GUI. Then, all available Ubuntu security tools can be installed with one shell script.

secbox is that shell script. With a single command, secbox installs every Ubuntu security tool supported by apt-get. secbox isn’t sexy, but it is very convenient for me — and for pretty much anyone who uses their Ubuntu machine for security work.

---

