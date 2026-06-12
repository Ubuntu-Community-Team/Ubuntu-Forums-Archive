---
title: "VPS Sizing for Low Traffic CiviCRM and Drupal install? InnoDB tuning?"
date: 2012-04-19
forum: Server Platforms
---

### Post by britebyte on 2012-04-19
I have run internal Linux hardware servers using Debian and Ubuntu before but with 1GB of RAM or more. I am setting up a Drupal site with the CiviCRM add-on that requires InnoDB. All the docs recommend a VPS over shared hosting as the memory requirements are likely to be exceeded on shared hosting. I am new to VPS hosting and I would love to hear some opinions on VPS sizing for something like this and/or performance tips. 

Site: Only 1000 page views/mth, in campaign time about double of that.
Administration: 2 Drupal content editors making about 1 edit per day if that.
CiviCRM: Once weekly report pulling, once monthly mailing list, webform integration with low # of submits.

Right now I  have a 384MB OpenVZ based VPS as I have read many anecdotal posts about  running Drupal on 256MB VPS but I am constantly running out of memory.
I  am using Apache2 at the moment. I have tried using both mod_php with  mpm_prefork and mod_fcgid with mpm_worker. My Apache settings for each  are down below.

Part 2:
"top" reports that my MySQL process RSS is 27MB to 31MB.
Is there any info on getting the memory usage of InnoDB down? I can't find any posts on it. All the low memory tuning articles say is turn on "skip-innodb".  

```

<IfModule mpm_prefork_module>
StartServers       1
MinSpareServers    2
MaxSpareServers    4
MaxClients        10
    MaxRequestsPerChild   2000
</IfModule>


<IfModule mpm_worker_module>
StartServers       1
MinSpareThreads    2
MaxSpareThreads    6
    ThreadLimit          16
    ThreadsPerChild      8
MaxClients        8
    MaxRequestsPerChild   0
</IfModule>

```

---

