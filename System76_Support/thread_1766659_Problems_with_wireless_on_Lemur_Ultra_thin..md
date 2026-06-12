---
title: "Problems with wireless on Lemur Ultra thin."
date: 2011-05-24
forum: System76 Support
---

### Post by Memento Mori on 2011-05-24
Hello I received my lemur ultra thin running on ubuntu 11.04 a few days ago. I am having problems with holding a connection to wifi. I have several friends with ubuntu 11.04 who can connect flawlessly to the same router.

I can connect on a reboot of the system, but it then disconnects within a couple of minutes. I've tried turning off and on wireless with fn+F11. iwlist has this to say about the network I am connected to:

          Cell 02 - Address: 00:26:5A:FD:1E:66
                    ESSID:"Launchpad"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=95/100  Signal level=-56 dBm  Noise level=-117 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    Extra: Last beacon: 3ms ago

I had no problems with my wifi connection a couple of days ago on my home router. But with this one, no luck.

Thank you.

---

### Post by Wood Prof on 2011-05-24
Not that this helps, but I have the same problem at work with the university wireless.  At home there is no problem, but at work it drops every few minutes.

---

### Post by Memento Mori on 2011-05-25
I found instead of restarting that I can do:

$ sudo rmmod r8192se_pci 
$ sudo modprobe r8192se_pci

, but it doesn't solve my problem, only save me time

---

### Post by isantop on 2011-05-25
Can you guys make sure the routers are up to date firmware-wise? Also, go ahead and unplug the suspect routers for a minute or two, then plug them back in. Does that help?

---

### Post by Memento Mori on 2011-05-25
Router isn't mine. I can potentially ask if it's possible to mess around with, but I can't guarantee they'll be receptive. If I get the chance later, I'll let you know.

What I do know is that the router is a DIR-655 D-link.

Thanks.

---

### Post by torosc on 2011-05-26
This sounds a lot like the issue I am having with my Starling that I mentioned in another thread. I have noticed that the problem occurs when the computer is downloading and working hard, causing it to warm up and run the fan. Each time this happened, the computer was warm and the fan was on. Is this what happens in your case?

t

---

### Post by Wood Prof on 2011-05-26
The routers (multiple all over campus), reset periodically, and as far as I know (which isn't much) are updated when the firmware is needed.  We use WPA2 using PEAP with MSCHAPV2 for security if that helps.

---

### Post by Memento Mori on 2011-05-26
> **torosc said:**
> This sounds a lot like the issue I am having with my Starling that I mentioned in another thread. I have noticed that the problem occurs when the computer is downloading and working hard, causing it to warm up and run the fan. Each time this happened, the computer was warm and the fan was on. Is this what happens in your case?

t

That may be the case, but I don't think I've pushed my CPU loads to above 50%, and it's usually lower than 25%. I haven't been paying attention to the fan though, so I'll keep my eyes open.

---

### Post by torosc on 2011-05-26
> **Memento Mori said:**
> That may be the case, but I don't think I've pushed my CPU loads to above 50%, and it's usually lower than 25%. I haven't been paying attention to the fan though, so I'll keep my eyes open.

I take that back.. Of course, after I posted that, I lost my connection while filling out an online form (as in nothing strenuous).

t

---

### Post by Memento Mori on 2011-05-28
I'm still having troubles, but yesterday there was a period where it was connected for a couple of hours straight. Unfortunately, not so today.

---

### Post by lordadi on 2011-05-28
> **Wood Prof said:**
> The routers (multiple all over campus), reset periodically, and as far as I know (which isn't much) are updated when the firmware is needed.  We use WPA2 using PEAP with MSCHAPV2 for security if that helps.

This sounds like a bad wpa_supplicant - are you running 10.10 or prior by any chance? If so, this worked for me: [http://twitter.com/#!/da/statuses/27916469257904128](http://twitter.com/#!/da/statuses/27916469257904128)

---

### Post by Memento Mori on 2011-05-29
Since I've been restarting the wireless card module with,

sudo rmmod r8192se_pci && sudo modprobe r8192se_pci

,I've had my system crash occasionally. I've attached my logs.tar file.

---

### Post by Memento Mori on 2011-06-01
Sorry for bumping, but any help would be greatly appreciated!

---

### Post by kingofspades8 on 2011-06-02
I have the same problem at school but not at home.  

I suspect there's something wrong with the drivers - when I tried out Fedora and Debian they didn't include drivers for the Realtek 8192 due to stability issues.  In those distributions you have to add them manually using the terminal...

---

### Post by Tart on 2011-06-02
I have the same problem at home. Doesn't happen everyday.

---

### Post by ImperfectlyInformed on 2011-06-02
I have this problem as well - started with 10.10 (or 10.04?) and still happens with 11 which I just upgraded to. There's a related thread at [http://ubuntuforums.org/showthread.php?t=1612903&page=3](http://ubuntuforums.org/showthread.php?t=1612903&page=3)

---

### Post by Memento Mori on 2011-06-19
Sorry for the necromancy. But I have had no improvement in my connection. Searching around, it seems many others have had problems with realtek's  RTL8191SEvB in ubuntu. Has there been any progress on this front?

---

### Post by thomasaaron on 2011-06-20
Hi, Memento Mori. This thread is starting to get a little hectic. People chiming in with variations of the problem. Let's move you to email support where we can expedite this more effectively. support...at...system76...dot...com.

That invitation is open to all System76 customers on this thread as well.

Let me know in the email if the problem is on just one router or multiple routers.

---

### Post by Memento Mori on 2011-06-21
> **thomasaaron said:**
> Hi, Memento Mori. This thread is starting to get a little hectic. People chiming in with variations of the problem. Let's move you to email support where we can expedite this more effectively. support...at...system76...dot...com.

That invitation is open to all System76 customers on this thread as well.

Let me know in the email if the problem is on just one router or multiple routers.

sent!

---

