---
title: "Dyndns"
date: 2007-05-21
forum: Server Platforms
---

### Post by dzaranka on 2007-05-21
Greetings...

Using this [guide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty/Networking#How_to_assign_Hostname_to_local_machine_with_dynamic_IP_using_free_DynDNS_service") I tried to assign myself a hostname, but now I can't bind my ports to anything.  It seemed to work fine - found my ip address, logged in, etc.

I deleted the files, rebooted, nothing... still can't run any servers on my machine.   They were working fine before I followed that guide.

> httpd: apr_sockaddr_info_get() failed for godmachine

> - IPv4 getaddrinfo 'godmachine' error: No address associated with hostname

Any ideas?

Thanks.

---

### Post by turinglabs on 2007-05-23
ipcheck will update dyndns's records to reflect your new IP address - it shouldn't change any of your network configuration locally. The errors from apache look like a DNS lookup is failing for 'godmachine', this will certainly fail if the name isn't qualified with a domain or is not referenced somewhere.

Some guesses:

-Check your /etc/hosts file to make sure 'godmachine' has an IP address associated with it
-Change your httpd.conf so that the ServerName is fully qualified.

Doug

---

