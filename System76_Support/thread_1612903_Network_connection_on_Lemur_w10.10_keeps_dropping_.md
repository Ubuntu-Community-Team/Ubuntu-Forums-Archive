---
title: "Network connection on Lemur w/10.10 keeps dropping out"
date: 2010-11-03
forum: System76 Support
---

### Post by Azilie on 2010-11-03
Hello System76 and the rest of the Ubuntu Forum community,

I have had my Lemur UltraThin for about two weeks now, and I really like it, except for one recurring frustration which I'm hoping you can help me solve.

The network connection will at times just give out. I've tried the fix in [this thread ]("http://ubuntuforums.org/showthread.php?t=1597043")(the one that involved changing the network manager to ifup managed=true ifdown managed=true) and that seemed to do it (as in it lasted the rest of the day or so without the connection failing) but unfortunately it later broke down again.

At first I thought it was just the wireless, so I've plugged it into the ethernet cable.  Once the wireless fails, this lets me connect again, but even that has conked out on me a couple of times.  So it appears it's not just wireless.

I have noticed that sometimes, when I close the laptop and reopen it, the network connection will come back.  But not reliably.

This also may be related just to my router, as I have had the problem more often at home than at school/work, though that might be because I use it much more often at home.  In any case, I'm quite a beginner with Linux and I'm not sure how to find out.  (I have techier friends than me who help me out sometimes, but I was hoping you could help them help me.)

So any assistance you could give me would be greatly appreciated.  Thank you kindly!

---

### Post by isantop on 2010-11-04
You might try rebooting your router. I've often seen this clear up connection and speed issues. Simply unplug it, wait a minute or two, then plug it back in and see if the problem is resolved.

---

### Post by Azilie on 2010-11-04
Thank you for the suggestion.  Unfortunately, I did try that several times but it didn't solve the problem.

---

### Post by isantop on 2010-11-05
I would try running from an Ubuntu LiveUSB for a while. This will let me know if there is a hardware issue or a software problem at fault.

Instructions for downloading and installing Ubuntu on a Flash Drive are here: [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by Itaylor57 on 2010-11-06
I just received my lemur ultra and I also can not get my wireless to work properly.  If I am right next to the router my connection is good, but any distance away it fails.

---

### Post by |Porsche on 2010-11-06
Are you using wireless N?

---

### Post by Itaylor57 on 2010-11-07
no b/g

---

### Post by isantop on 2010-11-08
The first thing to try would be to turn off the wireless in the laptop, then turn it back on. First, press the Fn+F11 keys simulataneously until the wireless disconnects. Then, press them again to turn it back on. Wait for it to connect, then try out the range.

If that doesn't work, unplug your router for a minute or two, then plug it back in. Wait for it to boot up, then see if the range has improved.

---

### Post by pslinge1 on 2010-11-15
I also just received my new Lemur UltraThin last week and have been having the same issue: the wireless works fine sometimes, but other times it just keeps dropping and turning back on over and over again.  This happens at home and at work on different wireless routers.

---

### Post by isantop on 2010-11-15
Have you tried the suggestions above about resetting your wireless card and your router? I think this will clear it up.

---

### Post by pslinge1 on 2010-11-16
Yes, this seems to help. Thanks for the help.

---

### Post by Plecebo on 2010-11-17
Have a Pan7 that was recently upgraded from 10.04 to 10.10 and started experiencing this issue (at least the wireless part). 

Wireless will work fine for a while, then will stop working. It is happening at two separate locations with the same frequency, each location uses a different model router. 

I haven't done much troubleshooting yet, but know for sure that a reboot fixes the problem. 

Because the trouble happens randomly it is difficult to reproduce reliably, but I'd be willing to try some stuff out if there are suggestions. 

I will try rebooting the router, but as its happening at two different locations I'd be surprised if that was the issue. Especially since my Gazelle Ultra is on 10.10 and connects fine with no wireless dropouts. 

Thanks for any info.

---

### Post by isantop on 2010-11-17
I'd go ahead and try resetting the wireless card. You can do this by pressing Fn+F11, waiting for the wireless to disconnect, then pressing it again. That may clear up the problem.

---

### Post by Itaylor57 on 2010-11-17
I have followed yo ur suggestions to no avail.  I have two networks one b/g/n and one n only.  I even moved my n only network within 5 feet.  It worked for a bit but then the re authenticate dialog keept coning up.

So my workaround is to connect via ehternet is working for now, but I would liike a woring wireless setup.

Somtthing is broke,I hope a fix is in the works.


Update: My wifi is working just fine now.

---

### Post by Plecebo on 2010-11-20
I also had no luck resolving this issue by resetting the network card using fn+F11. It does allow the computer to reconnect to the network but still fails to connect it to the internet. Usually shortly after it reconnects it will again disconnect. 

Still the only reliable way to get things back is to reboot the laptop at which point it will begin working again for a while. 

This seems to be happening every 15-20 minutes, but not consistently like every 10 minutes on the dot, rather it is quite variable. 

Again this is on a Panp7. I am sitting right next to the Panp7 with my gazu1 having no troubles at all. Both computers are running Ubuntu 10.10 and have the system 76 driver installed and updated. 

I haven't tested extensively with a wired connection, but the user seems to remember it happening with the wired connection as well. 

Any additional help you can provide?

---

### Post by Azilie on 2010-11-22
I'm back and I have to say that I have continued having problems, but I haven't looked into fixing them because at this time of the grad school semester it's easier to just keep rebooting every 20 minutes.

Still, I thought I would add the information that eventually the ethernet connection tends to die too, though I am connected with that right now.

I only got about 5 minutes with the wireless on this last boot. :(  I could really use a fix on this too!  I love my new Lemur except for this.

---

### Post by isantop on 2010-11-23
The issue may be with network manager. try opening a terminal (Applications > Accessories > Terminal) and running these commands:

```
sudo apt-get remove --purge network-manager*
sudo apt-get install network-manager-gnome
```

Then reboot and see if that has had any effect.

---

### Post by Azilie on 2010-11-24
If I purge the Network Manager, though, will I still be able to download it again from the Internet?  I'm a newbie so I might be missing something....

---

### Post by houstonbofh on 2010-11-25
Just for some additional data...  I have it too.  Multiple networks and AP brands.  No WEP.  The syslog shows this, repeating endlessly.

```
Nov 24 23:57:32 it-ubuntu-lee kernel: [20760.560634] Linking with TRENDnet,channel:6, qos:0, myHT:0, networkHT:0, mode:6 cur_net.flags:0x406
Nov 24 23:57:32 it-ubuntu-lee kernel: [20760.560645] ===>rtllib_associate_procedure_wq(), chan:6
Nov 24 23:57:32 it-ubuntu-lee kernel: [20760.560649] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
Nov 24 23:57:32 it-ubuntu-lee kernel: [20760.570710] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x1e
Nov 24 23:57:35 it-ubuntu-lee kernel: [20763.069182] Linking with TRENDnet,channel:6, qos:0, myHT:0, networkHT:0, mode:6 cur_net.flags:0x406
Nov 24 23:57:35 it-ubuntu-lee kernel: [20763.069192] ===>rtllib_associate_procedure_wq(), chan:6
Nov 24 23:57:35 it-ubuntu-lee kernel: [20763.069196] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
Nov 24 23:57:35 it-ubuntu-lee kernel: [20763.079248] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x1e
Nov 24 23:57:37 it-ubuntu-lee kernel: [20765.567765] Linking with TRENDnet,channel:6, qos:0, myHT:0, networkHT:0, mode:6 cur_net.flags:0x406
Nov 24 23:57:37 it-ubuntu-lee kernel: [20765.567776] ===>rtllib_associate_procedure_wq(), chan:6
Nov 24 23:57:37 it-ubuntu-lee kernel: [20765.567780] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
Nov 24 23:57:37 it-ubuntu-lee kernel: [20765.577836] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x1e
Nov 24 23:57:40 it-ubuntu-lee kernel: [20768.076321] Linking with TRENDnet,channel:6, qos:0, myHT:0, networkHT:0, mode:6 cur_net.flags:0x406
Nov 24 23:57:40 it-ubuntu-lee kernel: [20768.076332] ===>rtllib_associate_procedure_wq(), chan:6
Nov 24 23:57:40 it-ubuntu-lee kernel: [20768.076336] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
Nov 24 23:57:40 it-ubuntu-lee kernel: [20768.086387] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x1e
Nov 24 23:57:42 it-ubuntu-lee kernel: [20770.577409] Linking with TRENDnet,channel:6, qos:0, myHT:0, networkHT:0, mode:6 cur_net.flags:0x406
Nov 24 23:57:42 it-ubuntu-lee kernel: [20770.577419] ===>rtllib_associate_procedure_wq(), chan:6
Nov 24 23:57:42 it-ubuntu-lee kernel: [20770.577423] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
Nov 24 23:57:42 it-ubuntu-lee kernel: [20770.587476] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x1e
Nov 24 23:57:45 it-ubuntu-lee kernel: [20773.083480] Linking with TRENDnet,channel:6, qos:0, myHT:0, networkHT:0, mode:6 cur_net.flags:0x406
Nov 24 23:57:45 it-ubuntu-lee kernel: [20773.083489] ===>rtllib_associate_procedure_wq(), chan:6
Nov 24 23:57:45 it-ubuntu-lee kernel: [20773.083493] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
Nov 24 23:57:45 it-ubuntu-lee kernel: [20773.093544] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x1e
Nov 24 23:57:47 it-ubuntu-lee kernel: [20775.582082] Linking with TRENDnet,channel:6, qos:0, myHT:0, networkHT:0, mode:6 cur_net.flags:0x406
Nov 24 23:57:47 it-ubuntu-lee kernel: [20775.582092] ===>rtllib_associate_procedure_wq(), chan:6
Nov 24 23:57:47 it-ubuntu-lee kernel: [20775.582096] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
Nov 24 23:57:47 it-ubuntu-lee kernel: [20775.592148] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x1e
Nov 24 23:57:50 it-ubuntu-lee kernel: [20778.080657] Linking with TRENDnet,channel:6, qos:0, myHT:0, networkHT:0, mode:6 cur_net.flags:0x406
Nov 24 23:57:50 it-ubuntu-lee kernel: [20778.080667] ===>rtllib_associate_procedure_wq(), chan:6
Nov 24 23:57:50 it-ubuntu-lee kernel: [20778.080671] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
Nov 24 23:57:50 it-ubuntu-lee kernel: [20778.090722] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x1e
Nov 24 23:57:52 it-ubuntu-lee kernel: [20780.582945] Linking with TRENDnet,channel:6, qos:0, myHT:0, networkHT:0, mode:6 cur_net.flags:0x406
Nov 24 23:57:52 it-ubuntu-lee kernel: [20780.582955] ===>rtllib_associate_procedure_wq(), chan:6
Nov 24 23:57:52 it-ubuntu-lee kernel: [20780.582959] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
Nov 24 23:57:52 it-ubuntu-lee kernel: [20780.593012] rtl819xSE:No more TX desc@6, ring->idx = 0,idx = 0, skblen = 0x1e

```

Only fix is a full reboot.

---

### Post by Azilie on 2010-12-17
If anyone has figured out what has causing this, I still need help. The semester is almost over so I'll be able to give it some time to try to dig up other solutions, but it's gotten to be even more of a problem: now (as of earlier today) it says it can't find any wireless networks at all. I've tried pushing Fn+F11 to turn the wireless on, if it accidentally got switched off, but that hasn't helped.

I don't know, I thought maybe I got a flaky wireless card or something, but others have been having this problem as well.

---

### Post by isantop on 2010-12-17
That sounds like a flaky card. Did you try purging and reinstalling Network Manager? If so, or this is still happening, please send us an email at support...at...system76...dot...com

---

### Post by ImperfectlyInformed on 2011-04-16
I've got a new lemur - this happens to me as well (running 10.10). I should say that at this point it's not that severe - happens more like every few hours than every 20 minutes.

---

