---
title: "Video corruption in GNOME Shell 3.6 top panel"
date: 2012-09-27
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by pressureman on 2012-09-27
See attached screenshot. This only started happening this morning after updating to GS 3.6. Already rebooted once, after the first boot was showing blue squares where the icons normally are on the right hand side.

Also noticed this in dmesg, which I haven't seen before:

```

[   51.396335] [TTM] Failed to find memory space for buffer 0xffff8801fe0c6048 eviction
[   51.396339] [TTM] No space for ffff8801fe0c6048 (4050 pages, 16200K, 15M)
[   51.396341] [TTM]   placement[0]=0x00070002 (1)
[   51.396342] [TTM]     has_type: 1
[   51.396342] [TTM]     use_type: 1
[   51.396343] [TTM]     flags: 0x0000000A
[   51.396344] [TTM]     gpu_offset: 0xA0000000
[   51.396345] [TTM]     size: 131072
[   51.396345] [TTM]     available_caching: 0x00070000
[   51.396346] [TTM]     default_caching: 0x00010000
[   51.396348] [TTM]  0x00000000-0x00000001:        1: used
[   51.396349] [TTM]  0x00000001-0x00000011:       16: used
[   51.396350] [TTM]  0x00000011-0x00000111:      256: used
[   51.396351] [TTM]  0x00000111-0x00000211:      256: used
[   51.396352] [TTM]  0x00000211-0x00000215:        4: free
[   51.396353] [TTM]  0x00000215-0x00000216:        1: used
[   51.396354] [TTM]  0x00000216-0x0000021b:        5: free
[   51.396355] [TTM]  0x0000021b-0x0000021c:        1: used
[   51.396356] [TTM]  0x0000021c-0x0000021d:        1: used
[   51.396357] [TTM]  0x0000021d-0x0000021e:        1: used
[   51.396357] [TTM]  0x0000021e-0x0000021f:        1: used
[   51.396358] [TTM]  0x0000021f-0x00000220:        1: used
[   51.396359] [TTM]  0x00000220-0x00000221:        1: used
[   51.396360] [TTM]  0x00000221-0x00000222:        1: used
[   51.396361] [TTM]  0x00000222-0x00000223:        1: used
[   51.396362] [TTM]  0x00000223-0x00000224:        1: used
[   51.396363] [TTM]  0x00000224-0x00000225:        1: used
[   51.396363] [TTM]  0x00000225-0x00000226:        1: used
[   51.396364] [TTM]  0x00000226-0x00000227:        1: used
[   51.396365] [TTM]  0x00000227-0x00000228:        1: used
[   51.396366] [TTM]  0x00000228-0x00000229:        1: used
[   51.396367] [TTM]  0x00000229-0x0000022a:        1: used
[   51.396368] [TTM]  0x0000022a-0x0000022b:        1: used
[   51.396368] [TTM]  0x0000022b-0x0000022c:        1: used
[   51.396369] [TTM]  0x0000022c-0x0000023c:       16: used
[   51.396370] [TTM]  0x0000023c-0x00000367:      299: free
[   51.396371] [TTM]  0x00000367-0x00001339:     4050: used
[   51.396372] [TTM]  0x00001339-0x00001421:      232: free
[   51.396373] [TTM]  0x00001421-0x000023f3:     4050: used
[   51.396374] [TTM]  0x000023f3-0x000033c5:     4050: used
[   51.396375] [TTM]  0x000033c5-0x00004397:     4050: used
[   51.396376] [TTM]  0x00004397-0x00005369:     4050: used
[   51.396377] [TTM]  0x00005369-0x0000633b:     4050: used
[   51.396377] [TTM]  0x0000633b-0x0000730d:     4050: used
[   51.396378] [TTM]  0x0000730d-0x000082df:     4050: used
[   51.396379] [TTM]  0x000082df-0x000092b1:     4050: used
[   51.396380] [TTM]  0x000092b1-0x0000a283:     4050: used
[   51.396381] [TTM]  0x0000a283-0x0000b255:     4050: used
[   51.396382] [TTM]  0x0000b255-0x0000ba3e:     2025: free
[   51.396383] [TTM]  0x0000ba3e-0x0000ca10:     4050: used
[   51.396384] [TTM]  0x0000ca10-0x0000d9e2:     4050: used
[   51.396384] [TTM]  0x0000d9e2-0x0000e1cb:     2025: free
[   51.396385] [TTM]  0x0000e1cb-0x0000f19d:     4050: used
[   51.396386] [TTM]  0x0000f19d-0x0001016f:     4050: used
[   51.396387] [TTM]  0x0001016f-0x00011141:     4050: used
[   51.396388] [TTM]  0x00011141-0x00012113:     4050: used
[   51.396389] [TTM]  0x00012113-0x000130e5:     4050: used
[   51.396390] [TTM]  0x000130e5-0x000140b7:     4050: used
[   51.396391] [TTM]  0x000140b7-0x00015089:     4050: used
[   51.396391] [TTM]  0x00015089-0x0001605b:     4050: used
[   51.396392] [TTM]  0x0001605b-0x0001702d:     4050: used
[   51.396393] [TTM]  0x0001702d-0x00017fff:     4050: used
[   51.396394] [TTM]  0x00017fff-0x00018fd1:     4050: used
[   51.396395] [TTM]  0x00018fd1-0x00019fa3:     4050: used
[   51.396396] [TTM]  0x00019fa3-0x0001af75:     4050: used
[   51.396397] [TTM]  0x0001af75-0x0001bf47:     4050: used
[   51.396398] [TTM]  0x0001bf47-0x0001cf19:     4050: used
[   51.396399] [TTM]  0x0001cf19-0x0001deeb:     4050: used
[   51.396400] [TTM]  0x0001deeb-0x0001eebd:     4050: used
[   51.396401] [TTM]  0x0001eebd-0x0001fe8f:     4050: used
[   51.396401] [TTM]  0x0001fe8f-0x00020000:      369: free
[   51.396402] [TTM]  total: 131072, used 126113 free 4959
[   51.396405] [drm:radeon_cs_ioctl] *ERROR* Failed to parse relocation -12!

```

I'm not using flgrx - simply using the default open source radeon driver.

Anybody else seeing this?

---

### Post by pressureman on 2012-09-28
Blue squares are back today.

---

### Post by Stinger on 2012-09-28
I have seen something similar when I was messing around with a new Plymouth theme.
It was only present in gdm, once I logged in the square icons disappeared ( mine where white ).
I use the open source ati driver myself, Radeon HD 4670.

I haven't had trouble since I borked my install twice ([the gdm bug]("http://ubuntuforums.org/showthread.php?t=2063067&page=3")), re-installed the ubuntu-gnome-20120913 alpha again and did a complete upgrade.

---

### Post by pressureman on 2012-09-28
Mine is a daily-updated install from beta1 CD, and I'm using GDM since Gnome Shell no longer supports screen locking without it. I was actually growing quite fond of the lightdm aesthetics.

---

### Post by Mr. Picklesworth on 2012-09-28
> **pressureman said:**
> Mine is a daily-updated install from beta1 CD, and I'm using GDM since Gnome Shell no longer supports screen locking without it. I was actually growing quite fond of the lightdm aesthetics.

Actually, that has been patched: if you use lightdm, it will fall back to locking the screen with gnome-screensaver.

---

### Post by mips on 2012-09-28
Ignore useless post ;)

---

### Post by pressureman on 2012-09-28
> **mips said:**
> That might be a LightDM issue. Reboot, log in, log out and log in again. If the problem is gone on the second login it indicates a lightdm/propriety gpu driver issue.

Why would it be a proprietary GPU driver issue? I wrote in the first post that I'm **not** using fglrx, but instead using the open source radeon driver.

Also, I've rebooted the machine a few times - problem is always there after booting... but surprisingly corrects itself within about 5-10 minutes of normal use. Go figure.

---

### Post by mc4man on 2012-09-28
I've seen this from time to time for some time now.
Used to think it was from switching a user back & forth from Unity, Gs sessions but still see once & awhile on a user account that never uses unity.
*though still think it was more common on an account that used both.
I wonder if it's light-theme related, didn't see on an install that used the Gs only iso (UbuntuGnome or whatever they're calling it) though haven't used long enough for a good test.

(nvidia, nouveau here, don't think that matters at all

---

### Post by mips on 2012-09-28
> **pressureman said:**
> I wrote in the first post that I'm **not** using fglrx, but instead using the open source radeon driver.


Sorry missed that, ignore my post.

---

### Post by nebajoth on 2012-09-29
This also affects me. Quantal, ATI Radeon 4850, open source radeon driver. Gnome-shell 3.5.9, kernel 3.5.0.

---

### Post by Rukiri on 2012-09-29
Had to test this on one of my Radeon 7X machines, and from my experience.. ati drivers are just awful even the open-source versions.  However on my 7990 works perfectly with the manufacture's drivers.

---

### Post by Stinger on 2012-09-30
> **Rukiri said:**
> Had to test this on one of my Radeon 7X machines, and from my experience.. ati drivers are just awful even the open-source versions.  However on my 7990 works perfectly with the manufacture's drivers.
I'm not sure that you are right about awful drivers, I never had these tearing's or strange icons when using Fedora. I think these oddities is related to Ubuntu's implementation of those drivers, but I might be wrong ?

---

### Post by pressureman on 2012-10-01
My video card is a Radeon HD 4290. This definitely wasn't happening a couple of weeks back, when I first installed from beta1 DVD. It also doesn't affect my Thinkpad T500 notebook (Intel graphics).

For the record, I have beige squares this morning, instead of blue. Variety is the spice of life.

---

### Post by Stinger on 2012-10-01
I can reproduce this phenomena every time I log out of a session, first I get a black screen with white tearing's at top and bottom, then gdm appears with three square icons in the right corner, if I hoover over the icons they return to their normal look. when I log in again the problem disappears. :confused:

If I haven't said it, my card is a radeon HD 4670

---

### Post by pressureman on 2012-10-04
No video corruption or strangely coloured blocks on the top panel this morning.

Hopefully whatever it was has been fixed.

---

### Post by pressureman on 2012-10-05
Hmm. I don't like to continually reply to my own threads, but the problem is back this morning.

I suspect this bug *may* be related: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/717870](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/717870)

It's not a a showstopper, and certainly doesn't prevent me from working... it's just a minor curiosity.

---

