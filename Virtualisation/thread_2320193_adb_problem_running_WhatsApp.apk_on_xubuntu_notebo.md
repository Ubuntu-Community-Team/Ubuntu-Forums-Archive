---
title: "adb problem running WhatsApp.apk on xubuntu notebook"
date: 2016-04-11
forum: Virtualisation
---

### Post by makem2 on 2016-04-11
I used the following pages to install all necessary components:

[http://www.2daygeek.com/install-whatsapp-on-ubuntu-centos-debian-fedora-mint-rhel-opensuse/#](http://www.2daygeek.com/install-whatsapp-on-ubuntu-centos-debian-fedora-mint-rhel-opensuse/#)

I believe my Android device locations is:

```

/opt/android-sdk-linux/tools             

```

I have placed the Android,apk file in that folder.

[http://www.2daygeek.com/install-sdk-android-emulator-on-ubuntu-centos-debian-fedora-mint-rhel-opensuse/](http://www.2daygeek.com/install-sdk-android-emulator-on-ubuntu-centos-debian-fedora-mint-rhel-opensuse/)

[http://www.2daygeek.com/install-java-openjdk-6-7-8-on-ubuntu-centos-debian-fedora-mint-rhel-opensuse/](http://www.2daygeek.com/install-java-openjdk-6-7-8-on-ubuntu-centos-debian-fedora-mint-rhel-opensuse/)

[http://www.whatsappfor.org/whatsapp-for-linux/whatsapp-linux/](http://www.whatsappfor.org/whatsapp-for-linux/whatsapp-linux/)

In the Android Virtual Device (AVD) Manager, I have a device running.

```
makem@newTOSH:~$ sudo su[sudo] password for makem: 
root@newTOSH:/home/makem# cd /opt/android-sdk-linux/tools
root@newTOSH:/opt/android-sdk-linux/tools# ./android

```

At this point after few seconds I get a window which is blank black and which has controls at the right plus an attached pane in white with further controls but nothing else. One of two of the controls work but the close/shutdown does not. This means a reboot to kill the process. Assuming the window is waiting for a WhatsApp.apk................

I must then use another Terminal.

```

makem@newTOSH:~$ sudo adb install WhatsApp.apk[sudo] password for makem: 
15308 KB/s (29137136 bytes in 1.858s)
makem@newTOSH:~/Desktop$ sudo adb install /opt/android-sdk-linux/tools/WhatsApp.apk
16445 KB/s (29137136 bytes in 1.730s)
Error: Could not access the Package Manager.  Is the system running?

```

Package Manager is?

Is it Synaptic?

---

