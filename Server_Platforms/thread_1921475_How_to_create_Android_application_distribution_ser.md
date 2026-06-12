---
title: "How to create Android application distribution server?"
date: 2012-02-06
forum: Server Platforms
---

### Post by deepakdeshp on 2012-02-06
I am using Ubuntu 10.04 server and want to add the functionality of Android application distribution server. That is just like the Android devices connect to the market and download the applications from market, my server should lay the same role. 

I shall keep the Android applications on my Ubuntu 10.04 server and other Android devices like Phones and tablets should be able to download and install the applications for themselves from the Ubuntu server.

---

### Post by deepakdeshp on 2012-03-08
One solution is to keep .apk files on the server . The Android clients can connect to the server, download and install the .apk files. But sometimes the .apk files for installation are available only to the Android client as there is no separate downloads but it can be just installed.

 Is there anything eles that can be done?

---

### Post by kevdog on 2012-03-08
What you are asking for is a fairly large project.  You can use ssh to grab the apk's but this isn't exactly like going through a market interface.  Koush Doutta (the creater of SetCPU, Cyanogenmod) is working on a program similar to this -- at least he mentioned it a while ago on g+.

---

### Post by deepakdeshp on 2012-03-12
Loading the .apk applications on the ubuntu server from where they will be served to the Android devices  is all I could do. I didnt get any other information on this subject.

Thanks for the update though.

---

