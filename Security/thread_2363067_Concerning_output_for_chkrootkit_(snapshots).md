---
title: "Concerning output for chkrootkit (snapshots)"
date: 2017-06-05
forum: Security
---

### Post by marcojv on 2017-06-05
Hi.

I have been very worried about my security lately, so I have been installing and running some antivirus and such... I don't really know about these topics that much but I have been reading a lot.

One of the things that concerns me the most is the output for 

[B]```
sudo chkrootkit
```
[/B]
At the **chkutmp **check it gives me several lines such as:
 
 ```
 Checking `chkutmp'...                                        The tty of the following user process(es) were not found in /var/run/utmp !
! RUID          PID TTY    CMD
! 11,3553;4,12,3553;4,13,3553;4,14,3553;4,15,3553 --disable-accelerated-video-decode --service-request-channel-token=453F220C1234873FDCD8BC960D4260F8 --renderer-client-id=102 --shared-files=v8_natives_data:100,v8_snapshot_data:101       3 4,6,3553;4,7,3553;4,8,3553;4,9,35511,3553;4,12,3553;4,13,3553;4,14,3553;4,15,3553 --disable-accelerated-video-decode --service-request-channel-token=453F220C1234873FDCD8BC960D4260F8 --renderer-client-id=102 --shared- 
```

And I get a LOT of this weird things (like the ones on the last line). Also, in the end I also get

```
 ! root         1483 tty7   /usr/lib/xorg/Xorg -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch 
```

I also get 

```
  Searching for Suckit rootkit...                             Warning: /sbin/init INFECTED 
```

But I checked this last one in rkhunter and it said that Suckit rootkit was not present.

I am using ubuntu 14.04, I don't recall downloading anything strange lately (I have never run these tests before, thou).

I would really appreciate if someone could give me an insight on what is happening and how to solve it.

Thank you in advance.

---

### Post by thehighhat-q on 2017-07-22
I also see the same things on trusty when running chkrootkit.

The strange chkutmp lines appear either when I run chrome/chromium, or when I run firefox w/ a more restrictive apparmor profile.  (all appamor profiles in enforce mode btw)

---

