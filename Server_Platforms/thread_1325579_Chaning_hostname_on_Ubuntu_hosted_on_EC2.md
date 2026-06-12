---
title: "Chaning hostname on Ubuntu hosted on EC2"
date: 2009-11-13
forum: Server Platforms
---

### Post by acroporas on 2009-11-13
I recently set up a Amazon EC2 hosting account.  And when I ssh in, the default hostname is long and ugly.  I dont have any real reason why it needs to be changed, but it would make the whole ssh experience more enjoyable if I did not have to look at that long and ugly hostname all day long.

So I tried to change it using the instructions found at [http://ubuntuforums.org/showpost.php?p=2694796&postcount=2](http://ubuntuforums.org/showpost.php?p=2694796&postcount=2)

And it does not work.  Short-term it does work.  I log out and log back in and it shows the new hostname.  But once I reboot the server the hostname is back to the default.

Any ideas what else to try?  Or is there some good reason why it will not let me change the hostname?

Thanks

---

### Post by MartinSmith on 2010-10-18
Ran into the same problem.  Looks like amazon is pushing hostnames from their DHCP server.

You can modify the file /etc/dhcp3/dhclient.conf (or similarly located).

You'll want to remove the options under request for "domain-name" and I think also "host-name".

At this point, the server should keep the hostname that was specified in /etc/hostname.

---

### Post by Irregular Joe on 2010-10-21
Changing the hostname within the EC2 guest does not change the DNS name you would use to access it over the internet.  It will, however, change the prompts you see while connected to guest.

I created a dynamic DNS entry (DynDNS or freedns.afraid.org) and put the script to send the IP address changes inside a cron file (or the /etc/rc.local).  That way, I only have to use one designated DNS name of my choosing to get to the guest.

One small issue is that my router has DNS caching, and it sometimes takes a few minutes to see the new IP address once I boot the guest.

Hope this helps!

---

