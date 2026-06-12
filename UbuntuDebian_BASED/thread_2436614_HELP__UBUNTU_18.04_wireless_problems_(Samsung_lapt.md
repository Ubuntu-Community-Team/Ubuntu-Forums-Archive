---
title: "HELP | UBUNTU 18.04 wireless problems (Samsung laptop)"
date: 2020-02-10
forum: Ubuntu/Debian BASED
---

### Post by gabrielearmento on 2020-02-10
[B]MY SITUATION 
[/B]Recently I decided I wanted to change OS my Samsung NP270E5E, as Windows 10 was getting considerably slow and stuttery and I need it to be smooth enough to let me work without hiccups. 
As I had a bit of former experience with Linux, and as of right now I don't need big programs like Photoshop and similar, I opted for a ligth distro like Kubuntu, then Lubuntu, then Zorin OS and now Elementary OS. Why did I go through so many? Because on every and each one of the, I had the same exact problem and I couldn't manage to find a fix.

TL;DR
Laptop: Samsung NP270E5E
OS: Elementary OS 5.1 Hera
[B]
THE PROBLEM[/B]
My wireless (wlan) card is not connecting to the internet. I have a Qualcomm Atheros AR9485 that runs on the ath9k driver.

```
rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

```
lspci -v
02:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
    Subsystem: Samsung Electronics Co Ltd AR9485 Wireless Network Adapter
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f1500000 (64-bit, non-prefetchable) [size=512K]
    Expansion ROM at f1580000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath9k
    Kernel modules: ath9k

```

The thing is that wireless WORKS when I use the Live Media on my bootable USB stick (which I'm using rn to post this) and it goes flawlessy.
Also, if I REBOOT from the live-media into my installed version of eOS (click restart, wait for the usb to being inactive, plug off the usb, the system boots into the hd) WiFi WORKS!
Same thing if I INSTALL any distro, it reboots and on the first session WIFi works, and if I keep rebooting it keeps working. (I noticed this because I've done it so many times).
The problem occurs when I shut down the machine to boot it back up. In that case, the card is disabled. (rfkill shows hard block for phy0, which is not hard blocked on the live media).
When it is in this state, I have no way to turn it back up as the Fn-key combination for the hardware switch does not respond. (Which it does on the live-media). 
I noticed that a behaviour connected to the WiFi working or not is the fact that congruently with the WiFi I can also turn it ON and OFF with my hardware switch (Fn+F12), which DOES NOT work when WiFi is disabled. (Same thing for brightness up and down)
[B]
WHAT I'VE ALREADY DONE[/B]


[LIST]
[*]Tried different distros
[*]blacklisted *acer_wmi*: it did not work but on ONE boot-up after this WiFi seemed to work. I shut it down again to verify and boot it back up and it wasn't working again.
[*]Updated eOs
[*]As I noticed the problem might be related to the fact that I CANNOT turn the hardware switch on and off, I tried looking for the module on the live media that was handling this task. I found that on the live media a certain *mxm_wmi *was present that wasn't on the hd. Tried to modprobe that but didn't work.
[*]Same thing for *nouveau *because I had installed nVidia drivers, I removed them and I tried to use nouveau instead but it didn't work.
[*]I reset BIOS in every way possible. (Load default settings, CMOS removal)
[/LIST]

**NOTES**

On the live-media, there is a module called *sparse_keymap*, or something similar. Is that related to the Fn-key binding process?
WiFi card doesn't seem to have problems, as it works fine when it does. It looks like it's a software problem.
I've had problems with my BIOS. I can't get into it by pressing F2 (which is the key that Samsung states for this model), nor with other keys. Trust me I tried everything I could find on the internet. The only way I can get into it is by changing boot order through *efibootmgy*. Also, I accidentally deleted the entry for the Hard Drive so when I boot into BIOS I can only see entries for USB, CD ROM and RECOVERY (and BOOT MENU). That's not an issue because it does boot into the operating system (as I set it up correctly on efibootmgr). But still, it's a bit messed up.

I really hope you can help me with this, I'd like to be able to use my pc without having to keep a USB stick in all the time.

P.S. If you need me to, I can post terminal outputs from both the working version (live-media) and the non-working one (hard-drive) to see the differences.

---

### Post by coffeecat on 2020-02-10
Elementary OS

*Thread moved to **Ubuntu/Debian Based** sub-forum*

---

