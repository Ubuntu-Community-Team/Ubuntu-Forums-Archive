---
title: "Dapper Server &amp; AIC-7892A"
date: 2006-11-02
forum: Server Platforms
---

### Post by mking213 on 2006-11-02
Im trying to load this module and im getting nothing. I see there's a issue w/2.6 kernel. Im trying to get a proliant server with a AIC-7892A card and a tape backup system going. The output is as follows: 

root@bacula:~# modprobe aic7xxx
FATAL: Error inserting aic7xxx (/lib/modules/2.6.15-27-server/kernel/drivers/scsi/aic7xxx/aic7xxx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
root@bacula:~# dmesg |tail
[42955792.660000] aic7xxx: Unknown symbol spi2_populate_ppr_msg
[42955792.660000] aic7xxx: Unknown symbol spi2_attach_transport
[42955792.660000] aic7xxx: Unknown symbol spi2_release_transport
[42955805.790000] aic7xxx: Unknown symbol spi2_populate_width_msg
[42955805.790000] aic7xxx: Unknown symbol spi2_populate_sync_msg
[42955805.790000] aic7xxx: Unknown symbol spi2_dv_device
[42955805.790000] aic7xxx: Unknown symbol spi2_display_xfer_agreement
[42955805.790000] aic7xxx: Unknown symbol spi2_populate_ppr_msg
[42955805.790000] aic7xxx: Unknown symbol spi2_attach_transport
[42955805.790000] aic7xxx: Unknown symbol spi2_release_transport
root@bacula:~#

Any help would be appreiciated.

Mike

---

