---
title: "Question regarding migrating the dhcpd.leases file for ISC-DHCP-SERVER"
date: 2013-05-21
forum: Server Platforms
---

### Post by Sniperm4n on 2013-05-21
Backstory: I am in the process of replacing a SINGLE Debian 3.1 (Sarge)  ISC-DHCP-SERVER (v3.0.1) with 2 Ubuntu 12.04 LTS x64 servers running  ISC-DHCP-SERVER (v4.1-ESV-R4) in failover mode. I've been unable to find  the answer to this on Google, and my internal testing on an empty  subnet has yielded interesting results (please note I'm relatively new  to Linux):

Here are my 3 questions:

1) Should I copy the dhcpd.leases and dhcpd.leases~ files from my Debian  server to /var/lib/dhcp/ on both of the new servers and then start the  DHCP services? Will the files then balance themselves?

2) Should I copy the dhcpd.leases and dhcpd.leases~ files to  /var/lib/dhcp/ on only the primary failover server, and let the  secondary server generate one from scratch after the DHCP services have  been started?

3) Should I not bother copying the files at all, and let the 2 new  Ubuntu servers generate the files from scratch in /var/lib/dhcp/?

TIA!
-Snipe

---

### Post by lykwydchykyn on 2013-05-21
Is there any reason you want to have the clients keep the same leases?

---

### Post by Sniperm4n on 2013-05-21
> **lykwydchykyn said:**
> Is there any reason you want to have the clients keep the same leases?

Hey,

We don't care if the clients keep the same leases, as long as they successfully get leases. Please note we're running a mixed Windows and Linux environment.

Thanks,
-Snipe

---

### Post by SeijiSensei on 2013-05-21
Then you don't need the leases file.  It doesn't matter what the clients are running.

---

### Post by lykwydchykyn on 2013-05-21
I agree.  I think you'll be best off letting the server do its own leases file.  Trying to migrate one from a different server and version is asking for trouble.

---

### Post by Sniperm4n on 2013-05-22
Thank you VERY much for the help everyone, I'll be going with brand new, empty files =)

-Snipe

---

