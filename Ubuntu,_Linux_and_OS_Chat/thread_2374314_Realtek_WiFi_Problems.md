---
title: "Realtek WiFi Problems"
date: 2017-10-14
forum: Ubuntu, Linux and OS Chat
---

### Post by Geoff_Lane on 2017-10-14
Folks,

Toshiba Satellite laptop with Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter

I'm not actually posting a request for help because I have effectively 'given up'.

Searching on the internet I can see other users have been having problems for over a couple of years now, I thought I may have resolved the problem by following the advice as follows;

[https://askubuntu.com/questions/452315/problems-with-realtek-rtl8188ee-on-14-04](https://askubuntu.com/questions/452315/problems-with-realtek-rtl8188ee-on-14-04)

But again no, wifi started then ground to a halt.

What puzzles me is Realtek are obviously a major chip manufacturer and the wifi in many devices so loads of Linux users MUST be having the same problems.

Works superbly under Windows 10 but Ubuntu is my main system so obviously a wee bit disappointed.

Ah well, lucky ethernet convenient most of the time.

Geffers

---

### Post by jeremy31 on 2017-10-14
*Thread moved to **Ubuntu, Linux and OS Chat**.* Since you are not looking for support
Relevant support posts [https://ubuntuforums.org/showthread.php?t=2371998](https://ubuntuforums.org/showthread.php?t=2371998)
[https://ubuntuforums.org/showthread.php?t=2373344](https://ubuntuforums.org/showthread.php?t=2373344)

I was surprised that Larry Fingers github didn't fix the disconnects for the rtl8821ae chipset.  There are bug reports filed already so all we can do is wait [https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=rtl8821ae&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=&orderby=-id&start=0](https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=rtl8821ae&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=&orderby=-id&start=0)

---

### Post by verymadpip on 2017-10-15
Hi there.
Many years ago I had an issue with a Realtek chip on a second hand laptop.  (Unfortunately I don't recall which chip it was now & laptop has long since been disposed of).
My cure was a cheap USB wireless stick, initially, & then I tried ndiswrapper just to free up the USB port.
Ndiswrapper worked for me, although IIRC I had to reinstall ndiswrapper with every new kernel.  Once I'd done it a couple of times it wasn't so daunting.
I'm aware that ndiswrapper is sometimes regarded as the ginger stepchild to be avoided at all costs & this is only a suggestion for a possible alternative workaround.

---

### Post by tea for one on 2017-10-15
> **Geoff_Lane said:**
> Folks,

Toshiba Satellite laptop with Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter

I'm not actually posting a request for help because I have effectively 'given up'.

Searching on the internet I can see other users have been having problems for over a couple of years now, I thought I may have resolved the problem by following the advice as follows;

[HTML]https://askubuntu.com/questions/452315/problems-with-realtek-rtl8188ee-on-14-04[/HTML]

But again no, wifi started then ground to a halt.

What puzzles me is Realtek are obviously a major chip manufacturer and the wifi in many devices so loads of Linux users MUST be having the same problems.

Works superbly under Windows 10 but Ubuntu is my main system so obviously a wee bit disappointed.

Ah well, lucky ethernet convenient most of the time.

Geffers

Hello Geoff

I can't really help you with your Realtek wireless device but here is a cheap and cheerful wireless adaptor that works with Linux.

[https://www.ebuyer.com/220220-edimax-wireless-n150-nano-usb-adapter-compatible-with-raspberry-pi-ew-7811un](https://www.ebuyer.com/220220-edimax-wireless-n150-nano-usb-adapter-compatible-with-raspberry-pi-ew-7811un)

Kind regards

---

### Post by Geoffrey_Arndt on 2017-10-15
Simple solution.   Support a known and proven vendor that supplies Linux friendly adapters.   Panda at the top of my list (have tested over a dozen devices . . Panda based on Ralink works without needing to install or compile drivers).

[http://www.pandawireless.com/](http://www.pandawireless.com/)

Upon plugin, you'll see two networks - the panda device and the built in (realtek) device.    Choose to connect to Panda and the realtek will be disabled for the session.  So, with the nano sized dongle - your laptop will be a real laptop again.

---

### Post by Geoff_Lane on 2017-10-18
> **Geoffrey_Arndt said:**
> Simple solution.   Support a known and proven vendor that supplies Linux friendly adapters.   Panda at the top of my list (have tested over a dozen devices . . Panda based on Ralink works without needing to install or compile drivers).

[http://www.pandawireless.com/](http://www.pandawireless.com/)

Upon plugin, you'll see two networks - the panda device and the built in (realtek) device.    Choose to connect to Panda and the realtek will be disabled for the session.  So, with the nano sized dongle - your laptop will be a real laptop again.

Must admit just bought a new laptop - didn't think for one minute I'd have a problem as previous laptop and wifi system working fine.

I may get a Ralink device but currently my ethernet is convenient, MORE SO since the WPA2 problem has surfaced.

Geffers

---

### Post by Geoff_Lane on 2017-10-18
> **tea for one said:**
> Hello Geoff

I can't really help you with your Realtek wireless device but here is a cheap and cheerful wireless adaptor that works with Linux.

[https://www.ebuyer.com/220220-edimax-wireless-n150-nano-usb-adapter-compatible-with-raspberry-pi-ew-7811un](https://www.ebuyer.com/220220-edimax-wireless-n150-nano-usb-adapter-compatible-with-raspberry-pi-ew-7811un)

Kind regards

Thank you, may go down that line.

Geffers

---

### Post by Geoffrey_Arndt on 2017-10-19
Linux users often don't help ourselves.   When someone buys a Windows PC . . . it has to be compatible . . . else they won't sell.

If one looks at the "Specs" of PC's with Linux pre-installed, then there is a MUCH improved chance everything will work.    Generally, it's smart to go with ALL Intel machines (intel cpu's, intel wireless and intel integrated graphics.    Not a solution for high-end gaming, but for all else, Intel PC's just work out of the box (ps - not including dual-gpu systems).

---

### Post by cariboo on 2017-10-19
Not all Intel systems are equal. I found a Toshiba laptop at a local retailer for less than $200.00CA which was less money than the Compaq netbook it replaced. It is all Intel except for networking:

```
inxi -n
Network:   Card-1: Realtek RTL8101/2/6E PCIE Fast/Gigabit Ethernet controller
           driver: r8169
           IF: enp1s0 state: down mac: f8:a9:63:7a:e4:e3
           Card-2: Qualcomm Atheros AR9485 Wireless Network Adapter
           driver: ath9k
           IF: wlp2s0 state: up mac: b8:ee:65:8a:1b:f7
```

Fortunately the networking hardware is well supported, but the laptop was a deal I couldn't turn down, and it wouldn't have lasted long, so there wasn't time to check the specs, and asking the guy in the blue vest about technical specifications wasn't going to get me anywhere. :)

---

### Post by Geoff_Lane on 2017-12-24
May have found a remedy folks.

Fixed the IP addess and has been running now perfectly for 2 days.

Fingers crossed :mad: :lolflag:

Geffers

---

### Post by coffeefiend on 2017-12-24
I had the same issue. Bought a cheap HP laptop and installed Ubuntu 16.04 in dual boot with the pre-installed Windows 10. I noticed right out of the box that the wireless card wasn't being recognized. So I hit the Internet to do some research to try to fix it. I tried every suggestion I could find, but nothing worked. I connected directly to my router with an ethernet cable and ran updates. Still nothing. I did a fresh load with 17.10. But during the install I was searching more on the Internet on my other laptop and realized that 17.10 had the same issue with Realtek adapters. The next morning while in the shower I was racking my brain about it trying to think of a solution (because that's the level of nerdiness, as my wife so affectionately refers to it as, that I was at) when it occurred to me that the most simple fix was a wireless dongle. I took the dongle out of my Raspberry Pi2, plugged it in, and bickety bam! Problem solved. No, it isn't ideal, but it works. Hopefully one day Realtek will join the rest of us in the 21st century and start supporting Linux with some much needed drivers. If only I had come across this thread earlier I would have went the dongle route much sooner.

---

### Post by jeremy31 on 2017-12-24
coffefiend, start a new thread in Networking & Wireless, see the wireless script link in my signature and post results in the thread, we may have a fix for your internal device

---

### Post by coffeefiend on 2017-12-24
> **jeremy31 said:**
> coffefiend, start a new thread in Networking & Wireless, see the wireless script link in my signature and post results in the thread, we may have a fix for your internal device

That's awesome! I'm on duty today and not able to use my laptop here, but I will take advantage of your recommendation as soon as I can. The wifi dongle works great, but if there is a possible fix, I will definitely give it a try.

---

### Post by Geoff_Lane on 2017-12-24
> **coffeefiend said:**
> when it occurred to me that the most simple fix was a wireless dongle. I took the dongle out of my Raspberry Pi2, plugged it in, and bickety bam! Problem solved. 

Try fixing the IP on the Realtek device.

Mine now working fine.

Geffers

---

### Post by jeremy31 on 2017-12-24
> **Geoff_Lane said:**
> Try fixing the IP on the Realtek device.

Mine now working fine.

Geffers
There are a few Realtek wifi devices not supported by the kernel like the c821 and d723 devices, hopefully coffeefiend has the d723 device as we do have a fix thanks to smlinux on github

---

### Post by coffeefiend on 2017-12-24
> **jeremy31 said:**
> There are a few Realtek wifi devices not supported by the kernel like the c821 and d723 devices, hopefully coffeefiend has the d723 device as we do have a fix thanks to smlinux on github

It is d723

---

### Post by jeremy31 on 2017-12-24
Check your kernel version with ```
uname -a
```
See [https://ubuntuforums.org/showthread.php?t=2367405&p=13723723#post13723723](https://ubuntuforums.org/showthread.php?t=2367405&p=13723723#post13723723)

---

### Post by coffeefiend on 2017-12-24
It is 4.13

---

### Post by rrnbtter on 2017-12-24
Greetings, 
I don't know what OS version you are using but the RTL wifi cleared up with the 4.14 kernel. Prior to that I have been using the git hub drivers since 17.04 which work fine but you have to rerun the script with each kernel update. Not much of an issue. 

sudo apt-get install linux-headers-generic build-essential git 
git clone [http://github.com/lwfinger/rtlwifi_new.git](http://github.com/lwfinger/rtlwifi_new.git)
cd rtlwifi_new
make
sudo make install


Just in case the system doesn&#8217;t load the appropriate kernel module, you can execute the following command from within your rtlwifi_new directory
sudo modprobe **rtl8821ae** (put your card version here).
and reboot your system.

---

### Post by jeremy31 on 2017-12-24
> **rrnbtter said:**
> Greetings, 
I don't know what OS version you are using but the RTL wifi cleared up with the 4.14 kernel. Prior to that I have been using the git hub drivers since 17.04 which work fine but you have to rerun the script with each kernel update. Not much of an issue. 

sudo apt-get install linux-headers-generic build-essential git 
git clone [http://github.com/lwfinger/rtlwifi_new.git](http://github.com/lwfinger/rtlwifi_new.git)
cd rtlwifi_new
make
sudo make install


Just in case the system doesn&#8217;t load the appropriate kernel module, you can execute the following command from within your rtlwifi_new directory
sudo modprobe **rtl8821ae** (put your card version here).
and reboot your system.

Larry Finger's rtlwifi-new doesn't support the rtl8723de chipset

---

### Post by rrnbtter on 2017-12-24
Greetings,
Thanks for the info Jeremy. I still don't know what series OS he is using but he may be able to get the 4.14 kernel by enabling "Proposed".

---

### Post by jeremy31 on 2017-12-24
The 4.13 kernel is in Ubuntu 17.10

---

### Post by rrnbtter on 2017-12-24
Greetings,
I had RTL wifi problems through out the 17.04, 17.10 cycle in which I used the git drivers as a solution. However my cellular hotspot has been continually freezing after a extended idle time. I was using 18.04 and my RTL problems were resolved with the 4.14 Kernel release. However my hotspot continued to freeze. Two weeks ago I upgraded my wife's 17.10 install to 18.04 and the hotspot quit freezing. Hence I believe that 17.10 has persistent dhcp stack problems. Everything has been fine here since the upgrade.  Gnome/Wayland/GDM 18.04 running on both machines.
FYI.

---

