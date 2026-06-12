---
title: "Possibly hacked?"
date: 2015-05-12
forum: Security
---

### Post by Jellby on 2015-05-12
I noticed some background network activity (with gkrellm) in my laptop when I thought there should be none (1-3 Kbps). I run iftop and it should several (many) connections to "random" addresses, many of them of .jp domain, like these:

```
ns3.bredband.com
61-24-70-50.rev.home.ne.jp
p02f898.kngwnt01.ap.so-net.ne.jp
13.122.102.121.dy.bbexcite.jp
ns6.bredband.com
ab160235.dynamic.ppp.asahi-net.or.jp
i60-36-38-104.s41.a032.ap.plala.or.jp
ntaich362055.aich.nt.ftth4.ppp.infoweb.ne.jp
softbank126004044168.bbtec.net
113.5.232.5
ns4.bredband.com
58-3-13-160.ppp.bbiq.jp
ns8.bredband.com
ns7.bredband.com
114.164.173.221
```                                                   

This is weird, then I run nethogs and got something like:

```
?     root     85.230.109.179:52669-135.0.249.200:51915                                                                                   0.032       0.038 KB/sec
?     root     85.230.109.179:42732-184.85.223.35:80                                                                                      0.011       0.013 KB/sec
3081  jellby   /usr/lib/firefox/firefox                                                                                        wlan0      0.000       0.000 KB/sec
?     root     unknown TCP                                                                                                                0.000       0.000 KB/sec
```

but sometimes I can also see activity in gkrellm and nothing happens in nethogs. Note that the weird connections above happen with firefox closed too, and no other networking program active (that I know of).

Should I be worried? How can I further track it down? How can I fix it?

---

### Post by veddox on 2015-05-13
I'm not a security expert, but since no-one else is responding, I might as well:

My first reflex would be to check the system logs - do you see anything suspicious? (Attempt to use sudo, log in as root...) Are there any firewall log entries?

Next: did you install any programs recently? Potentially one of them is trying to send information to the outside.

Also: try pinging each of the addresses you noticed unwanted connections to. They might end up resolving to one and the same IP address, or at least boil down to relatively few hosts. If they do, that is definitely suspicious.

---

### Post by cogset on 2015-05-13
Something must be connecting to those addresses, as  you've ruled out firefox, you could maybe use ```
watch -n2 ss -aptn state established
```  and/or    ```
watch -n2 ss -aptr state established
```  in a terminal to see what is connecting to those addresses and which ports are involved.

       If nothing useful comes up, maybe it's time to use more sophisticated tools such as Wireshark.

BTW, I'm no security expert either, by any stretch of the imagination.

---

### Post by CitadelUniversal on 2015-05-13
Do you go on any japanese sites because .jp indicates that they are connecting to the japanese domains see here [http://en.wikipedia.org/wiki/.jp](http://en.wikipedia.org/wiki/.jp)  - also don't forgot that if you are concerned about security then try to minimize the risks and try adblock plus and then it'll block adverts on any websites those links could be links from adverts on websites. There's also this [http://blog.mattbrock.co.uk/hardening-the-security-on-ubuntu-server-14-04/](http://blog.mattbrock.co.uk/hardening-the-security-on-ubuntu-server-14-04/)   - & - this [http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421) which you can use to increase security on whatever version of Ubuntu you are using.....

---

### Post by Jellby on 2015-05-13
After a night spent in hibernation, when I woke the computer up I don't see this background traffic anymore. I checked the syslog file and don't see anything suspicious there. I have adblockplus and don't visit Japanese sites regularly. I may have installed some program recently, but always through apt-get and the official repositories...

Then I thought that maybe this traffic is not originating on my side. Could it be that other computers saw mine before through bittorrent or some other P2P network, and they were still trying to access it even after I had shut down the programs, and this is just the traffic I saw?

---

### Post by CitadelUniversal on 2015-05-13
I think its bittorrent related see this website [http://siderite.blogspot.com/2013/09/solved-bittorrent-stuck-on-connecting.html](http://siderite.blogspot.com/2013/09/solved-bittorrent-stuck-on-connecting.html)    - it maybe related to your problem....

---

