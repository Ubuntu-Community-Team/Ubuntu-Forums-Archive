---
title: "Xubuntu jammy high ram use compared with focal."
date: 2022-04-18
forum: Ubuntu Development Version
---

### Post by ajgreeny on 2022-04-18
I am curious.
I have been running Xubuntu-22.04 in dual boot with Xubuntu-20.04 since November 2021 which I think is when the iso became installable following the ubiquity bug preventing installation from iso.

22.04 has generally been running very well with no major difficulties but I always see that ram usage is considerably higher at about 850 - 900 MB ram at rest, compared with 20.04 which uses only 530 - 550 MB ram at rest.
I have looked using top to see what might be the reason behind this but it has not shown anything obvious so I'm just wondering, now that we are so close to release of the new LTS, if other users have found the same ram usage situation with their 22.04 installs.

I do not use the same /home partition on the two OSs though have the same data files in both by use of symbolic links from the 20.04 data folders to the 22.04 home and I have almost exactly the same packages installed in both versions with no snaps in either of them.

Anybody got any thoughts about this.

---

### Post by #&amp;thj^% on 2022-04-18
I agree that's a bit higher than I've seen. (850 - 900 MB)
I'm around this currently>>530 - 550 MB
anything in dmesg?

---

### Post by ajgreeny on 2022-04-21
A good thought ifallen but nothing in dmesg that I can see so far.

I am just about to download a new iso as my installations of 22.04 other than virtual ones using KVM/QEMU systems were installed a long time ago and I have noticed that all my virtual installs, which I reinstall often after zsync updatibng their iso files, are using lower amounts of memory than the my old hard metal installs; even a Kubuntu 22.04 installed very recently is using only about 500-550 MB ram; good for Kubuntu I think, even though I'm aware it uses less memory than it used to.

I shall be overwriting my older 22.04 installs with new ones very soon which is no real problem as 20.04 is still my default version and will be until 22.04 has been out for a couple of months.

I will update this thread after I have done everything as mentioned above.

---

### Post by ajgreeny on 2022-04-27
I have now reinstalled my laptop with jammy using an iso from the daily repo at [http://cdimage.ubuntu.com/xubuntu/daily-live/current/jammy-desktop-amd64.iso](http://cdimage.ubuntu.com/xubuntu/daily-live/current/jammy-desktop-amd64.iso) to see if ram usage is any lower than in my original jammy install.

Regrettably there is no real change but using command ***free -mw*** on both jammy and focal I see the main difference is in the output of the ***cache*** section of free.
```
free		#jammy
               total        used        free      shared     buffers       cache   available
Mem:            7867         562        5070         102          86        [COLOR="#FF0000"]2147[/COLOR]        6943
Swap:            947           0         947



free		#focal
              total        used        free      shared     buffers       cache   available
Mem:           7873         501        6038         107          62        [COLOR="#FF0000"]1271[/COLOR]        7019
Swap:           947           0         947
```
Anyone have ideas why that cache figure should be so much higher in jammy than focal, both OSs now using the same /home partition.

---

### Post by TenPlus1 on 2022-04-30
I did a strip down of a fresh Xubuntu 22.04 install and removed startup items (screensaver, at-spi) and removed things like snap and managed to get it down to a respectable 300mb usage with a fully working desktop.

---

