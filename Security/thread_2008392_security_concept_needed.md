---
title: "security concept needed"
date: 2012-06-22
forum: Security
---

### Post by Blackbelt2011 on 2012-06-22
Hi,

I want to install Ubuntu 10.10 on a completely encrypted filesystem.
After my router was hacked, I want to secure my installation against hacker attacks.
I have some questions:
- Is there a tool what shows me if there is another network access to my system?
- Is it useful to install ClamAV?
- Is it helpful to have internet access via VPN connection and a proxy?
- what else can I do to have an installation that is not accessible?

Regards,
Blackbelt2011

---

### Post by Ms. Daisy on 2012-06-22
Start with the [basic security wiki]("https://wiki.ubuntu.com/BasicSecurity").  In particular look at the "home network" section for links specifically about securing your router.

---

### Post by CharlesA on 2012-06-22
How do you know your router was "hacked" ??

---

### Post by Blackbelt2011 on 2012-06-23
The WLAN pw was changed (WPA2) and the login data for internet access was changed. I had to have the router flashed new.

---

### Post by OpSecShellshock on 2012-06-23
Well the first thing is to start with the router's administration page. A lot of home routers unfortunately won't allow the user name to be changed to anything other than "admin" so to compensate, have a long password in place. Then make sure UPnP is disabled and that the option to access the administration page from external networks is disabled. For whatever reason a lot of home routers have both of those things enabled by default which is terrible.

As we often say here, the WPA2 password itself (which allows access to the wireless network, not the router's admin page) only has to be entered once, so use all 63 characters and go nuts with it. It's OK to write it down as long as you control access to that piece of paper.

There's an excellent (G)UFW tutorial linked from the Basic Security wiki, which should help you properly restrict incoming and outgoing traffic. A good firewall configuration sits comfortably somewhere between panacea and reckless. Once it's enabled you can just look at /var/log/ufw.log to see if external networks are attempting to establish connections, but odds are if you set it up according to the instructions there won't be anything.

ClamAV or any other AV software really won't do you much good.

Whether or not a VPN or proxy would help really depends on what you want it for. They can be good when you are connecting to other networks that are outside of your control and/or that you don't trust, but I assume your home network is within your control and that you're inclined to trust it. A number of people like to use such things for the sake of anonymity, but since most of the main things people do on the web are tied to an authenticated identity in some way, you'd be undermining that as soon as you logged into something as yourself.

---

### Post by Cheesemill on 2012-06-23
Installing an End Of Life operating system that no longer receives any support or updates probably isn't the best way to go from a security point of view. I'd install 12.04 if I were you.

---

### Post by CharlesA on 2012-06-23
> **Cheesemill said:**
> Installing an End Of Life operating system that no longer receives any support or updates probably isn't the best way to go from a security point of view. I'd install 12.04 if I were you.
Good catch. 10.04 around another year of support, but I'd go with 12.04.

---

### Post by rookcifer on 2012-06-24
> **Blackbelt2011 said:**
> Hi,

I want to install Ubuntu 10.10 on a completely encrypted filesystem.
After my router was hacked, I want to secure my installation against hacker attacks.


An encrypted filesystem does nothing to stop remote hackers.  All it does is stop people with physical access to your machine from accessing your files when the filesystem is not mounted.

---

### Post by Blackbelt2011 on 2012-06-24
> **Cheesemill said:**
> Installing an End Of Life operating system that no longer receives any support or updates probably isn't the best way to go from a security point of view. I'd install 12.04 if I were you.

I want to use VMWare 8, and this is not supported by 11.10 today.
But I will have a look at the Oracle Virtualbox too. I want to connect external devices to a guest, and as far as I know that works better with VMWare than with Virtualbox.

I think VMWare will suppport Ubuntu 12.10 in a while, but not now.

---

### Post by Cheesemill on 2012-06-24
VMware Workstation 8 is supported on 10.04 and 11.04, both of which are still being supported by Canonical. Running either of these would be better than installing the end-of-life 10.10 as mentioned in your first post.

Although not officially supported it's also easy enough to get Workstation running on 12.04.

As to using VirtualBox I've never had any problems with passing devices through to my VM's.

---

