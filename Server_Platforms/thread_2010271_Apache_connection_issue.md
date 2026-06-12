---
title: "Apache connection issue"
date: 2012-06-25
forum: Server Platforms
---

### Post by Neil948 on 2012-06-25
I have been playing with the config files now for 2 days :rolleyes:, 
I am currently trying to insert an SSL Certificate from a CA i have followed all the instructions and have googled error code as i have come accross them and managed to get to this point i have been instructed to enable 2 default-ssl files in 2 locations as soon as i do a system restart i then get the issue that Apache2 will not start.
the 2 ssl files are in sites-available & sites-enabled
when i'm going to be having my site a root.

When i execute this command as root:-

netstat -na | grep -i list | grep 80

I get this called back:-

tcp6       0      0 :::80                   :::*                    LISTEN     
unix  2      [ ACC ]     STREAM     LISTENING     8030     /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     8029     @/tmp/.X11-unix/X0

any help would be appreciated

I have managed to remove one of the ssl scripts and have gone back to square one getting the 
(Error code: ssl_error_rx_record_too_long) message when i re-enable the other ssl the site works saying my cert is untrusted but as soon as i have to restart apache i go back to the first issue

---

