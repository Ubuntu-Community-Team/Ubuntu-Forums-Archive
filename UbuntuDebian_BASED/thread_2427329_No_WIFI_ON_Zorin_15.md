---
title: "No WIFI ON Zorin 15"
date: 2019-09-20
forum: Ubuntu/Debian BASED
---

### Post by O)9(yo&amp;# on 2019-09-20
I'm posting here because the problem may be due to a bug in Ubuntu, or the Linux kernel.  I recently got an HP Pavilion 360 laptop. It uses the following adapter:

Realtek RTL882 1CE 802.11ac PCIe Adapter.

I HAVE NOT YET INSTALLED ZORIN. I won't unless I can feel comfortable it will have WIFI, otherwise it will probably be returned (though the Microsoft guy at Best Buy won't like it). 

So, when running Zorin LIVE (or for that matter Mint or elementary OS), there is no WIFI adapter found. I have seen threads where this is a kernel bug, and workarounds have been suggested, but I don't see my adapter listed in them. I have also joined the HP forum and asked there, but so far no response. 

The laptop cannot at present be connected to the web, but I can buy a USB Ethernet adapter and do it that way. I'm tempted to do that, and install Zorin 15, hoping that having internet during install might solve the problem. but I'm reluctant.

Hoping someone here may be able to help!

Thanks,

Mike





[COLOR=#000000][FONT=HPSimplifiedLight]

[/FONT][/COLOR]

---

### Post by QIII on 2019-09-20
Moved to Ubuntu/Debian BASED.

---

### Post by uRock on 2019-09-20
The fix in comment #4 should work for you, as well. I've never touched Zorin and haven't looked at Mint for several years, but the replies after that solution seem to show several people being happy with it.
[https://ubuntuforums.org/showthread.php?t=2398917](https://ubuntuforums.org/showthread.php?t=2398917)

Code that worked is;
```
sudo apt-get install --reinstall git dkms build-essential linux-headers-$(uname -r)
git clone https://github.com/tomaspinho/rtl8821ce
cd rtl8821ce
chmod +x dkms-install.sh
chmod +x dkms-remove.sh
sudo ./dkms-install.sh
```

---

### Post by O)9(yo&amp;# on 2019-09-20
> **QIII said:**
> Moved to Ubuntu/Debian BASED.

Sorry, haven't been here in a while!

---

### Post by O)9(yo&amp;# on 2019-09-20
> **uRock said:**
> The fix in comment #4 should work for you, as well. I've never touched Zorin and haven't looked at Mint for several years, but the replies after that solution seem to show several people being happy with it.
[https://ubuntuforums.org/showthread.php?t=2398917](https://ubuntuforums.org/showthread.php?t=2398917)

Code that worked is;
```
sudo apt-get install --reinstall git dkms build-essential linux-headers-$(uname -r)
git clone https://github.com/tomaspinho/rtl8821ce
cd rtl8821ce
chmod +x dkms-install.sh
chmod +x dkms-remove.sh
sudo ./dkms-install.sh
```

Thanks! This looks promising, I'll have to get an adapter so I can connect by Ethernet so I can try it.

---

### Post by oldfred on 2019-12-02
Other HP systems that may be similar, but with Ubuntu.

       HP Pavillion X360 13-a220nw
[https://ubuntuforums.org/showthread.php?t=2359510](https://ubuntuforums.org/showthread.php?t=2359510) & 
[Guide] Install Ubuntu 18.04 on HP Spectre x360 13" 
[https://ubuntuforums.org/showthread.php?t=2414086](https://ubuntuforums.org/showthread.php?t=2414086)
[https://ubuntuforums.org/showthread.php?t=2422113](https://ubuntuforums.org/showthread.php?t=2422113)
See last post for many boot parameters, still using UEFI, not Legacy
[https://ubuntuforums.org/showthread.php?t=2407615](https://ubuntuforums.org/showthread.php?t=2407615) &
[https://ubuntuforums.org/showthread.php?t=2406993](https://ubuntuforums.org/showthread.php?t=2406993)
[https://askubuntu.com/questions/1161563/external-hdd-works-on-desktop-but-not-recognized-on-laptop](https://askubuntu.com/questions/1161563/external-hdd-works-on-desktop-but-not-recognized-on-laptop)

---

