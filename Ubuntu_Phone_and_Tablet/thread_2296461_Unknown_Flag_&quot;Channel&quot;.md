---
title: "Unknown Flag &quot;Channel&quot;"
date: 2015-09-26
forum: Ubuntu Phone and Tablet
---

### Post by greeleyneptune on 2015-09-26
I'm on ubuntu 15.04 and I am trying to install ubuntu touch, I am on the last steps, I have kitkat 4.4 and im in the bootloader. 

I use this command as reccomended

```
$ ubuntu-device-flash --channel="ubuntu-touch/devel" --bootstrap --server="http://system-image.tasemnice.eu"
```

However I keep getting this error 

```
Unknown Flag "Channel"
```

anyone know why or what I can do?

---

### Post by grahammechanical on 2015-09-26
If the guide is anything to go by you are missing "ubuntu" off of the channel description. "ubuntu-touch/devel/ubuntu"

[https://developer.ubuntu.com/en/start/ubuntu-for-devices/image-channels/](https://developer.ubuntu.com/en/start/ubuntu-for-devices/image-channels/)

Regards.

---

### Post by greeleyneptune on 2015-09-26
Thank you very much for that, strangely enough I just figured out moments ago that you can root your nexus 5 in under 60 seconds with Towelroot, and then you can download the multirom app from the appstore and go through the processes on it, you can download ubuntu touch as a secondary boot from my understanding. I literally am in the process of doing the ubuntu touch installation now via this Towelroot/Multirom method. If it doesn't work (appears to be going swimingly) I will try your suggestions thanks :)

---

