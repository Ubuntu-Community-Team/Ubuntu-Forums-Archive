---
title: "ufw or iptables script"
date: 2010-10-04
forum: Server Platforms
---

### Post by abennettclarku on 2010-10-04
Hi,

I'm coming from a RHEL/CentOS background where I'm used to editing /etc/sysconfig/iptables for host-based firewall stuff.  I can't find a direct equivalent on Ubuntu and I'm pretty surprised.  What I've found is the ufw utility which seems to do some of what I want and some things I may not want, but it seems pretty cumbersome to type "ufw allow proto tcp from <address> to any port <number>" etc over and over again, compared to just copying and pasting and editing a largely canned set of iptables rules on RHEL.

Is that how experienced ubuntu server sysadmins do things?  Do you really use the ufw front end, or do you do a preup script in /etc/network/interfaces that calls a iptables --restore, etc?

Is there another way that I'm missing?  I want to do things the most standard, ubuntu-like way that's consistent with repeatability and quality, basically.

thanks,

Aaron

---

### Post by arrrghhh on 2010-10-04
I guess I'm not an experienced sysadmin, I just use UFW.  I don't setup hundreds and hundreds of boxes tho.

You can certainly use iptables directly, I would think it would be similar to RHEL, perhaps just in a different location... not sure TBH.

Check out the [Ubuntu Doc](https://help.ubuntu.com/community/IptablesHowTo) on iptables.  There's a section called 'Tips' - may have some good info for you there.

---

