---
title: "Ubuntu packaging for Ubuntu Store"
date: 2016-05-06
forum: Ubuntu Phone and Tablet
---

### Post by ricardo-gcclinux on 2016-05-06
Hello,

I have updated one of my Apps (Desktop only) and uploaded to MyApps but seems to me that ubuntu team no longer are reviewing the new packages and uploading them to the store is that correct?

I would like to know if Ubuntu is still repackaging developed software and uploading it to the store using this URL.

[https://myapps.developer.ubuntu.com/dev/click-apps/](https://myapps.developer.ubuntu.com/dev/click-apps/)

Many Thanks

---

### Post by ricardo-gcclinux on 2016-05-08
Any update from the ubuntu team? How can we package software and put it on the store for ubuntu 16.04

---

### Post by howefield on 2016-05-09
Hello ricardo-gcclinux, I have moved your thread to the "*Ubuntu Phone and Tablet*" forum which seems a better fit than the forum you posted to.

I'd suggest joining the IRC channel #ubuntu-touch where many of the developers are and if you ask at the right time, they are very helpful.

---

### Post by grahammechanical on 2016-05-09
Keep in mind that this is a user forum. We do not know the answers that only the developers & maintainers of Ubuntu would know.

As far as I know, Ubuntu for Devices is still based on 15.04 (vivid) code. It has not yet been re-based on to 16.04 (xenial) code. That will have to happen sometime in the future and when it does the apps will need to be packaged in the snap package format.

If you have written an app to be used on Ubuntu 16.04 desktop edition then it should be snap packaged and submitted to the snap store. If it has been designed to scale from phone size screen through tablet size screen to the desktop screen then the app will be useful to many more users.

 I do not think provision has been made to run Click apps on Ubuntu 16.04 desktop. But we can now install & load snap packages on Ubuntu 16.04 desktop edition. Once approved they will be available in Ubuntu Software (the replacement for Ubuntu Software Centre).

App developers use Snapcraft to package their apps. 

[https://developer.ubuntu.com/en/snappy/build-apps/](https://developer.ubuntu.com/en/snappy/build-apps/)

[http://summit.ubuntu.com/uos-1605/meeting/22682/anatomy-of-a-snap/](http://summit.ubuntu.com/uos-1605/meeting/22682/anatomy-of-a-snap/)

[http://summit.ubuntu.com/uos-1605/meeting/22687/demo-snaps-on-the-desktop/](http://summit.ubuntu.com/uos-1605/meeting/22687/demo-snaps-on-the-desktop/)

Regards

---

