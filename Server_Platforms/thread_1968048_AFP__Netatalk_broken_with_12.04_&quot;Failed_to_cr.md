---
title: "AFP / Netatalk broken with 12.04 &quot;Failed to create entry group: Not permitted&quot;"
date: 2012-04-28
forum: Server Platforms
---

### Post by wesg on 2012-04-28
I upgraded to 12.04 today and have run into what seems to be a widespread problem with Netatalk and AFPd. Inside syslog I see the following message:

> afpd[15306]: AFP/TCP started, advertising 192.168.0.2:548 (2.2.2)
afpd[15306]: Failed to create entry group: Not permitted

This was after doing lots of changes to the authentication (uam) system according to other forum posts. I've read that what I'm experiencing has something to do with the different ways that netatalk deals with Avahi. What other settings do I have to change? There has been some discussion with [**this bug**]("https://bugs.launchpad.net/ubuntu/+source/netatalk/+bug/810732") but it's been tough to figure out exactly what the posters are saying.

---

### Post by wesg on 2012-04-28
After much gnashing of teeth, I was able to find the solution. I had to remove the Avahi service file and change to the proper configuration in both afpd.conf and netatalk.conf.

Here is the final afpd.conf line that seems to work:

> - -tcp -noddp -uamlist uams_guest.so,uams_dhx2_passwd.so -nosavepassword -setuplog "default log_info /var/log/afpd.log" -mimicmodel RackMac

netatalk.conf should have the same UAM list as this, and using uams_dhx2.so only didn't work.

---

### Post by El Chupacabra on 2012-04-30
Adding:

- -tcp -noddp -uamlist uams_guest.so,uams_dhx2_passwd.so -nosavepassword -setuplog "default log_info /var/log/afpd.log" -mimicmodel RackMac

.....works great. Well done. 'Course, instead of using Ubuntu 12, you could just switch to Debian 6 and do a source install of Netatalk where everything works great and nothing breaks. :-P

---

### Post by OliverHaslam on 2012-05-04
> **El Chupacabra said:**
> Adding:

- -tcp -noddp -uamlist uams_guest.so,uams_dhx2_passwd.so -nosavepassword -setuplog "default log_info /var/log/afpd.log" -mimicmodel RackMac

.....works great. Well done. 'Course, instead of using Ubuntu 12, you could just switch to Debian 6 and do a source install of Netatalk where everything works great and nothing breaks. :-P

Can you give some more info on the Debian route? Thinking of switching from Ubuntu for my VM host, and that's what is running my Time Machine backups.

---

### Post by El Chupacabra on 2012-05-07
Check out the blog [here]("http://www.gimlisnipple.com/index.php/the-lion-the-witch-and-the-wardrobe-os-x-10-7-time-machine-and-your-netatalk-backup-server/") which gives step-by-step instructions

Some of the older libdb4.* might not install on Squeeze, but as long as you have 4.8, you should be good. Source install on Ubuntu works too, however I would stick to Debian if you're looking for the most stable solution.

---

### Post by n4gsx on 2012-07-30
> **wesg said:**
> using uams_dhx2.so only didn't work.

Using uams_dhx2.so didn't work for me either. I had to switch to uams_dhx2_passwd.so.

---

### Post by CarlosJHernandez on 2012-07-31
I followed the other instructions on the post (Thanks everybody) and still got the following error on the afpd.log:

```
{afp_avahi.c:161} (E:AFPDaemon): Failed to add service: Local name collision
```

Then I removed the /etc/avahi/services/afpd.service file and that did the trick.

---

### Post by xdracco on 2012-09-03
> **El Chupacabra said:**
> Adding:

- -tcp -noddp -uamlist uams_guest.so,uams_dhx2_passwd.so -nosavepassword -setuplog "default log_info /var/log/afpd.log" -mimicmodel RackMac

.....works great. Well done. 'Course, instead of using Ubuntu 12, you could just switch to Debian 6 and do a source install of Netatalk where everything works great and nothing breaks. :-P

or one could just have configured netatalk to use the uams_dhx2_passwd.so auth module from the very beginning right? =)

---

