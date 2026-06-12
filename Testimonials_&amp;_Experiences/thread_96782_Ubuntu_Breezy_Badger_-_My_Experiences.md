---
title: "Ubuntu Breezy Badger - My Experiences"
date: 2005-11-29
forum: Testimonials &amp; Experiences
---

### Post by trekkypj on 2005-11-29
Installed Breezy Badger to replace FC4 on a dual boot Dell Latitude D600 with Win 2000 about three weeks ago. Despite a few niggles I have with configs and so on, I really, really like Ubuntu so far. Especially like apt-get and Synaptic, having gotten fed up with the RPM distros because of dependency hell. The final straw was when I couldn't get Scribus to install because of a silly and idiotic dependency issue where the package being called for was actually installed but RPM couldn't find it. :mad: 

So why did I switch from FC4? Well, the college I attend changed the means by which the student residences connect to their network, and hence the Internet. Previously, it was a straightforward DHCP connection with a HTTP Proxy and a firewall. Then it was decided that the hassle of registering MAC addresses of network cards wasn't worth the hassle and decided to use a Microsoft VPN setup with usernames and passwords.

It meant that I was without internet under Linux until the campus IT person, who luckily was a debian/Ubuntu fan, came up with a precompiled custom kernel patched to make VPN work, and a script to log on to the VPN. But they only worked with Debian based distros, and with me getting annoyed over the dependency problems I was experiencing with RPMs, I chucked FC 4 and installed Breezy.

The default install worked a treat. I had a working desktop with full sound and the radeon driver and screen settings were automatically set up. Nice.

I have one niggly issue however... I can't get the ATI fglrx driver to work. This is because the driver won't work with my custom 2.6.13 kernel. I know that it's because of the kernel version I'm running, but I'm slightly disappointed that the kernel-restricted-module package can only be secured for 2.6.12 kernels, thus preventing me from installing the fglrx driver. It's not a major issue for me though.

Apart from the one problem, my Breezy system works a treat! I haven't booted into WIn 2000 for days now!

---

