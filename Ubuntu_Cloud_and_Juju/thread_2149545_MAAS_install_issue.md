---
title: "MAAS install issue"
date: 2013-05-29
forum: Ubuntu Cloud and Juju
---

### Post by mark65ak on 2013-05-29
OK first this is my first attempt at installing MAAS.  My end goal; here is to build a private cloud.  I'm using ubuntu server 12.10 64-bit from usb stick.  I am getting stuck with this message as follows:

> The region controller does not know whether any boot images have been imported yet.  If this message does not disappear in 5 minutes, there may be a communication problem between the region worker process and the region controller.  Check the region worker's logs for signs that it was unable to report to the MAAS API. 

I've done some searching without finding favorable results to get me over this hump.

The celeryd bug involving the missing "=" seems to be repaired in my install.  my region controller logs don't appear to show any errors reguarding the disk images.  


> $ tail /var/log/maas/celery-region.log
[2013-05-28 22:49:51,778: INFO/MainProcess] Got task from broker: provisioningserver.tasks.report_boot_images[3c741c81-f996-417a-883a-a817b4f550b2]
[2013-05-28 22:49:51,793: INFO/MainProcess] Task provisioningserver.tasks.report_boot_images[3c741c81-f996-417a-883a-a817b4f550b2] succeeded in 0.000674962997437s: None
[2013-05-28 22:50:11,205: INFO/MainProcess] Got task from broker: provisioningserver.tasks.write_full_dns_config[d728def8-053b-4737-b5e3-da4f3e3f370d]
[2013-05-28 22:50:11,222: INFO/MainProcess] Task provisioningserver.tasks.write_full_dns_config[d728def8-053b-4737-b5e3-da4f3e3f370d] succeeded in 0.00845193862915s: None
[2013-05-28 22:50:11,223: INFO/MainProcess] Got task from broker: provisioningserver.tasks.rndc_command[9d04d326-0596-4c46-a38d-dbb4ced46c2e]
[2013-05-28 22:50:11,241: INFO/MainProcess] Task provisioningserver.tasks.rndc_command[9d04d326-0596-4c46-a38d-dbb4ced46c2e] succeeded in 0.0113160610199s: None
[2013-05-28 22:50:44,371: INFO/MainProcess] Got task from broker: provisioningserver.tasks.write_full_dns_config[8bf7cc13-817c-4e9e-aac3-ad68e2626969]
[2013-05-28 22:50:44,432: INFO/MainProcess] Task provisioningserver.tasks.write_full_dns_config[8bf7cc13-817c-4e9e-aac3-ad68e2626969] succeeded in 0.0270619392395s: None
[2013-05-28 22:50:44,516: INFO/MainProcess] Got task from broker: provisioningserver.tasks.rndc_command[41b31fab-e82b-4cc3-9d65-7022ee9b52c5]
[2013-05-28 22:50:44,532: INFO/MainProcess] Task provisioningserver.tasks.rndc_command[41b31fab-e82b-4cc3-9d65-7022ee9b52c5] succeeded in 0.0125720500946s: None

I'm assuming also I must hurdle this snag before i can get any pxe boot options?

---

### Post by mark65ak on 2013-05-29
I have no relies thus far so I am going to cry and clarify some.
> I'm using ubuntu server 12.10 64-bit from usb stick.
This could be read wrong.  I should have said I installed it to hdd from usb stick with 12.10 amd64 as the install version.
Also I am trying to install it via the "preferred method"  MAAS + Openstack + Juju [http://maas.ubuntu.com/docs/install.html#installing-maas-from-ubuntu-server-boot-media](http://maas.ubuntu.com/docs/install.html#installing-maas-from-ubuntu-server-boot-media)

Could it be a dhcp issue?   I have tried managing the cluster controllers 2nd interface in different networks without luck.  I have also tried it in the same network as the rest of physical machines.
 
I would hate to start this process from the beginning to fail again as I have limited data usage and the maas-import-pxe-files command alone uses 20% of my monthly alotment.  I don;t need anyone to hold my hand throughout the whole process but a little nudge over this hump (with a pointer to the info I am failing to find) would be a tremendous help.

---

### Post by mark65ak on 2013-06-14
Thank for all your help.  It's obvious I am on my own here.    Or does anyone know a better forum where someone might actually respond?

---

### Post by docbrowne on 2013-11-05
Same issue, brother. No one seems to want to help. Let me know if you figured it out! I can't get maas-dhcp-server to start and stay running. It just dies silently.

---

