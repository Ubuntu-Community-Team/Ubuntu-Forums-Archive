---
title: "Forcing noip2 to Update"
date: 2015-02-27
forum: Tutorials
---

### Post by burninghut on 2015-02-27
I was troubleshooting my noip2 on boot script and I finally got it to work using the [tutorial here]("https://www.howtoforge.com/how-to-install-no-ip2-on-ubuntu-12.04-lts-in-order-to-host-servers-on-a-dynamic-ip-address"). It appeared to startup okay without any errors, but my ip address didn't seem to be updating when I logged into my account and checked it under "Manage Hosts". If you click "Modify", it shows you that last time the ip was updated. For me it was several hours ago (see pic), longer than the 30min interval I set in the configuration file.

Long story short, after much searching to no avail, I finally discovered the answer and decided to share it here. I believe the "Last Update" time refers to the last time the ip address changed and not the last time noip2 sent an update. This may be because noip2 checks the stored ip and if it matches, it doesn't update, but I'm not sure.

Here is what I did that worked:

After logging into my account and going through Manage Hosts -> Modify you can actually set your ip. So I entered in the wrong one and updated. When I ran noip2, it updated! Pretty simple...

Here's what didn't work for me:

I looked at other forums, and they didn't have satisfactory answers. The most recent being [http://ubuntuforums.org/showthread.php?t=2088669](http://ubuntuforums.org/showthread.php?t=2088669).

To renew my ip, I tried running 
```
dhclient eth0
```
which I read would work, but didn't and not sure why... 

Anyway, hope someone else finds this useful!

---

