---
title: "Cant get internet to work on ubuntu 17.10 and more"
date: 2017-11-10
forum: Ubuntu/Debian BASED
---

### Post by frequencyg on 2017-11-10
I just installed 17.10. It says "wired connecting" since i ticked it in VBOX. I listed my LSUSB list and i could see my RT2800USB detected. But could not make wireless work either. I will edit the post with a script afterwards.
#edit cant use the script since i got no internet..

---

### Post by wildmanne39 on 2017-11-10
*Thread moved to **Virtualisation for a more appropriate fit**.*

---

### Post by wildmanne39 on 2017-11-10
Please run these commands in the terminal one line at time, copy and paste for accuracy:
```
echo "options rt2800usb nohwcrypt=y" | sudo tee /etc/modprobe.d/rt2800usb.conf 
sudo modprobe -rfv rt2800usb 
sudo modprobe -v rt2800usb
```
if that does not work go back to the page where the wireless script is and see if you can run it by following the directions for running it without an internet connection.

Thanks

---

### Post by ajgreeny on 2017-11-10
Can you use the **NAT** connection instead of **bridged** which is what I presume you are using at the moment?

---

### Post by frequencyg on 2017-11-12
Yes exactly. I am gonna run the commands now and repost!

OUTPUT
```

[COLOR=#ff0000]**root@kali:**[/COLOR]~# echo "options rt2800usb nohwcrypt=y" | sudo tee /etc/modprobe.d/rt2800usb.conf 
options rt2800usb nohwcrypt=y
[COLOR=#ff0000]root@kali:[/COLOR]~# sudo modprobe -rfv rt2800usb 
rmmod rt2800usb
rmmod rt2800lib
rmmod crc_ccitt
rmmod rt2x00usb
rmmod rt2x00lib
rmmod mac80211
rmmod cfg80211
root@kali:~# sudo modprobe -v rt2800usb
insmod /lib/modules/4.13.0-kali1-amd64/kernel/lib/crc-ccitt.ko 
insmod /lib/modules/4.13.0-kali1-amd64/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/4.13.0-kali1-amd64/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/4.13.0-kali1-amd64/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00lib.ko 
insmod /lib/modules/4.13.0-kali1-amd64/kernel/drivers/net/wireless/ralink/rt2x00/rt2800lib.ko 
insmod /lib/modules/4.13.0-kali1-amd64/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00usb.ko 
insmod /lib/modules/4.13.0-kali1-amd64/kernel/drivers/net/wireless/ralink/rt2x00/rt2800usb.ko nohwcrypt=y 








```

i also changed to kali for compatibility cause i had given up on ubuntu,might switch if i get this one working

---

### Post by oldos2er on 2017-11-12
[Kali is not a desktop distro.]("https://docs.kali.org/introduction/should-i-use-kali-linux")

---

### Post by wildmanne39 on 2017-11-12
I am sorry I do not know anything about kali.

---

### Post by frequencyg on 2017-11-12
Its the same commands that made me work the card on ubuntu and kali before i reset all the VMs

---

### Post by wildmanne39 on 2017-11-12
Yes same commands but a lot of differences in other ways. 
> Its the same commands that made me work the card on ubuntu
So these commands got it working on Ubuntu? Either way I know nothing about Kali there are to many differences for me to help, I know because I have tried before and if I remember correctly the output from the wireless script looks different too.

---

### Post by jeremy31 on 2017-11-12
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
```
systemctl restart network-manager.service
```
Might do it as power management causes quite a few issues

---

### Post by frequencyg on 2017-11-12
> **jeremy31 said:**
> ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
```
systemctl restart network-manager.service
```
Might do it as power management causes quite a few issues

Yea correct,those wont run on kali.I did some research on airmon-ng and saw that i could tweak it. But i could not install the newest version since it crashes. Take a look.

Code that went good

```

sudo apt-get update
sudo make clean
sudo apt-get install libnl-genl-3-200 libnl-genl-3-dev libnl-idiag-3-dev



```

THEN
i had to type "make install"
output
```


root@kali:~/aircrack-ng-1.2-rc4# make install
make -C src all
make[1]: Entering directory '/root/aircrack-ng-1.2-rc4/src'
gcc -g -W -Wall -O3  -msse2 -pthread -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -DCONFIG_LIBNL30 -DCONFIG_LIBNL -I/usr/include/libnl3 -fstack-protector-strong -Wno-unused-but-set-variable -Wno-array-bounds -Iinclude   -c -o crypto.o crypto.c
crypto.c: In function ‘calc_mic’:
crypto.c:291:11: error: storage size of ‘ctx’ isn’t known
  HMAC_CTX ctx;
           ^~~
crypto.c:317:2: warning: implicit declaration of function ‘HMAC_CTX_init’; did you mean ‘HMAC_CTX_new’? [-Wimplicit-function-declaration]
  HMAC_CTX_init(&ctx);
  ^~~~~~~~~~~~~
  HMAC_CTX_new
crypto.c:327:2: warning: implicit declaration of function ‘HMAC_CTX_cleanup’; did you mean ‘HMAC_CTX_get_md’? [-Wimplicit-function-declaration]
  HMAC_CTX_cleanup(&ctx);
  ^~~~~~~~~~~~~~~~
  HMAC_CTX_get_md
crypto.c:291:11: warning: unused variable ‘ctx’ [-Wunused-variable]
  HMAC_CTX ctx;
           ^~~
crypto.c: In function ‘calc_tkip_mic_key’:
crypto.c:932:5: warning: this ‘if’ clause does not guard... [-Wmisleading-indentation]
     if((ptr-message) % 4 > 0)
     ^~
crypto.c:933:49: note: ...this statement, but the latter is misleadingly indented as if it were guarded by the ‘if’
         memcpy(ptr, ZERO, 4-((ptr-message)%4)); ptr+=4-((ptr-message)%4);
                                                 ^~~
<builtin>: recipe for target 'crypto.o' failed
make[1]: *** [crypto.o] Error 1
make[1]: Leaving directory '/root/aircrack-ng-1.2-rc4/src'
Makefile:25: recipe for target 'all' failed
make: *** [all] Error 2

```


i will investigate more!

---

### Post by wildmanne39 on 2017-11-12
We do not support that topic here, so thread closed! Best to try Kali or aircrack forum.
> Cracking: Requests for help about any form of password or encryption "cracking" are not supported. Even though there are packages such as aircrack in the repositories, discussions about cracking or software related to cracking often lead to discussions about illegal activities. Such threads will be closed.

---

