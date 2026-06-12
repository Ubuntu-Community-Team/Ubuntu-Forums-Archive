---
title: "Can't get my Awus036NH wireless usb adapter to work"
date: 2017-02-02
forum: Ubuntu/Debian BASED
---

### Post by zizon65 on 2017-02-02
Hi guys,
I know this has been discussed here, but anyway even it may sound dumb to ask for that, I'd rather ask than continuing to struggle against this problem. I have an awus036NH wireless usb adapter from Alfa, and I can't get it working anymore! So my question is what to do to solve this problem please? Any help would be greatly appreciated.
Thanks in advance.

---

### Post by ajgreeny on 2017-02-02
See Wireless-Info in my signature below and follow the instruction there to download, run and post the script results back here.

---

### Post by zizon65 on 2017-02-03
> **ajgreeny said:**
> See Wireless-Info in my signature below and follow the instruction there to download, run and post the script results back here.

Thanks for your quick reply sir! So following your instructions, I have done what you've asked: [ATTACH]273495[/ATTACH]
zizon65

---

### Post by wildmanne39 on 2017-02-03
*Thread moved to **Ubuntu/Debian BASED for better support**.*

---

### Post by wildmanne39 on 2017-02-04
There is several things that need changed but let's do a few at a time, please do:
```
echo "options rt2800usb nohwcrypt=y" | sudo tee /etc/modprobe.d/rt2800usb.conf 
sudo modprobe -rfv rt2800usb 
sudo modprobe -v rt2800usb 

```
Let's reset the interfaces file:
```
echo -e "auto lo\niface lo inet loopback" | sudo tee /etc/network/interfaces
```
Reset the resolv,config file:
```
sudo dpkg-reconfigure resolv.conf
```
You have wicd and network manager installed, you can only have one at a time, so please remove one of them preferably wicd.

Your country code is in correct if you are in Africa please do:
```
sudo iw reg set SN
sudo sed -i 's/^REG.*=$/&SN/' /etc/default/crda
```
Set network manager settings to match the screenshots:
[ATTACH=CONFIG]273514[/ATTACH][ATTACH=CONFIG]273515[/ATTACH]
Change the settings in the router. WPA2-AES is best; do not use WPA and WPA2 mixed mode unless you absolutely have too and do not use TKIP. Second, if your router is capable of N speeds, You may have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. Set a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router, after it has come back up reboot your computer.
Thanks

---

### Post by zizon65 on 2017-02-04
> **wildmanne39 said:**
> There is several things that need changed but let's do a few at a time, please do:
```
echo "options rt2800usb nohwcrypt=y" | sudo tee /etc/modprobe.d/rt2800usb.conf 
sudo modprobe -rfv rt2800usb 
sudo modprobe -v rt2800usb 

```
Let's reset the interfaces file:
```
echo -e "auto lo\niface lo inet loopback" | sudo tee /etc/network/interfaces
```
Reset the resolv,config file:
```
sudo dpkg-reconfigure resolvconf
```
You have wicd and network manager installed, you can only have one at a time, so please remove one of them preferably wicd.

Your country code is in correct if you are in Africa please do:
```
sudo iw reg set SN
sudo sed -i 's/^REG.*=$/&SN/' /etc/default/crda
```
Set network manager settings to match the screenshots:
[ATTACH=CONFIG]273514[/ATTACH][ATTACH=CONFIG]273515[/ATTACH]
Change the settings in the router. WPA2-AES is best; do not use WPA and WPA2 mixed mode unless you absolutely have too and do not use TKIP. Second, if your router is capable of N speeds, You may have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. Set a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router, after it has come back up reboot your computer.
Thanks

After entering "sudo dpkg-reconfigure resolv.conf", i got this "dpkg-query: package 'resolvconf' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: resolvconf is not installed"

What shall I do?
Thanks.

---

### Post by wildmanne39 on 2017-02-04
It should have been:
```
sudo dpkg-reconfigure resolv.conf
```
I missed the period late last night.

---

### Post by zizon65 on 2017-02-05
> **wildmanne39 said:**
> It should have been:
```
sudo dpkg-reconfigure resolv.conf
```
I missed the period late last night.

Nothing has changed sir, as I am always getting this : 
dpkg-query: package 'resolv.conf' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: resolv.conf is not installed

---

### Post by wildmanne39 on 2017-02-05
It must have a little different name, unfortunately I have never used Kali, and the differences is enough to cause difficulties for me trying to help you.

---

### Post by zizon65 on 2017-02-06
> **wildmanne39 said:**
> It must have a little different name, unfortunately I have never used Kali, and the differences is enough to cause difficulties for me trying to help you.

Anyway thanks for trying to help.

---

