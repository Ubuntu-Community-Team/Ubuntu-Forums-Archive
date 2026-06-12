---
title: "Error in boot  /run/dev not writable"
date: 2015-05-04
forum: Server Platforms
---

### Post by rushizaki on 2015-05-04
I´m getting this error during boot process:

[FONT=courier new]udevd[371]: error: runtime directory '/run/dev/' not writable, for now falling back to /dev/.udev'[/FONT]

But I get no prompt and can´t login, it freezes in that error.

I tried booting in recovery mode, but I get the same error.
Any idea or solutions?

Thanks.

---

### Post by rushizaki on 2015-05-04
I managed to enter in recovery mode and after searching for this error, I found this [https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/811441](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/811441)
I tried solution #51 and the error message disappeared.

BUT my server boot hangs after '/scripts/init-bottom Done' message...

Then I tried this [https://bugs.launchpad.net/ubuntu/+bug/398214](https://bugs.launchpad.net/ubuntu/+bug/398214)
Using solution #21 I managed to get a prompt and internet connection.

And now I don´t know what else I can do...

Please anyone has any ideas/suggestions?
I´m about to reinstall this server.

Using ubuntu server 10.04 and 2.6.32.38-server.

Thanks in advance!

---

