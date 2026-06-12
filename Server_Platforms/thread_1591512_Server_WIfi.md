---
title: "Server WIfi"
date: 2010-10-09
forum: Server Platforms
---

### Post by hantechbl on 2010-10-09
I have my Very old server runnin 10.04 I think.  I want to hook up to the web, and I was wondering, how can I hook up my 3800HGV-B up to the server with wifi or preferably USB (I ordered a ethernet card :) but it's not here yet, any solutions to hook this up with usb or wifi?  I only got terminal and yes the wifi does have encryption.

---

### Post by scrooge_74 on 2010-10-09
You need to read about command line iwconfig, which is what will let you configure the wifi and the encryption

---

### Post by hantechbl on 2010-10-09
ok thank you.

---

### Post by hantechbl on 2010-10-09
i read the man and --help and I still can make sense of it so lets say that I have a router with the name 2wire000 and an wpa personal key of 0000000000, how would I enter this?

---

### Post by scrooge_74 on 2010-10-09
something like

sudo iwconfig [wificard] essid 2wire000 key 0000000000 

You will need to research more being a few years since I had to manually hook to a wireless network, network-manager has improve a lot during these few years

---

### Post by iponeverything on 2010-10-09
> **hantechbl said:**
> i read the man and --help and I still can make sense of it so lets say that I have a router with the name 2wire000 and an wpa personal key of 0000000000, how would I enter this?


install wpa_supplicant with apt-get

```
sudo apt-get install wpasupplicant
```

create the file /etc/wpa_supplicant.conf and add the following stanza:



```

network={
        ssid="2wire000"
        proto=WPA2
        key_mgmt=WPA-PSK        
        psk=0000000000
}

```

edit the file /etc/network/interfaces and the following stanza where
wlan0 is your wireless device:

```

auto wlan0
iface wlan0 inet dhcp
wpa-conf /etc/wpa_supplicant.conf

```

reboot and you should be good.

---

### Post by hantechbl on 2010-10-10
> **scrooge_74 said:**
> something like

sudo iwconfig [wificard] essid 2wire000 key 0000000000 

You will need to research more being a few years since I had to manually hook to a wireless network, network-manager has improve a lot during these few years

I tried this and i used: sudo iwconfig wlan0 essid 2wire000 key 0000000000 but when I run apt-get it can't fetch any packages.... I don't know what I am doing wrong.....
It shows up with an x after every 4 characters so it shows up as 0000x0000x00.:confused:

---

### Post by hantechbl on 2010-10-13
Ok I edited the files and went for reboot, but now it keeps going to fsck before login, and I can't get into recovery mode because it says "unknown command "terminal"" It worked before..... I had to chown /etc/ was that bad?

---

### Post by scrooge_74 on 2010-10-13
why you chown /etc ?

---

### Post by arrrghhh on 2010-10-13
Yea I'm wondering why you chown'd /etc... You may be in for a reinstall.  You could boot with a livecd and try to repair... but it may be difficult/cumbersome.

---

