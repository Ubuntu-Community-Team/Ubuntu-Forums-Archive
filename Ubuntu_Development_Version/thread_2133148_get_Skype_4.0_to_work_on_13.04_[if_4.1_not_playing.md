---
title: "get Skype 4.0 to work on 13.04 [if 4.1 not playing ball]"
date: 2013-04-07
forum: Ubuntu Development Version
---

### Post by shantiq on 2013-04-07
tried to use 4.1 on Raring and got core dumped message each time tried 3 routes and same

someone on skype [site]("http://community.skype.com/t5/Linux/ubuntu-13-04/td-p/1455552") suggested using 4.0 and bingo

This is for the ones who have had no luck with 4.1
but you need to do a few things

so it does not reinstall 4.1 when you try again   [of course this is a trick until 4.1 is compatible** for all** on raring]



1.   ```
 sudo apt-get remove --purge skype
```

2.    ```
cd /var/cache/apt/archives/ 
```  to see if you have any remaining debs       then to list```
 ls 
```

3.   ```
sudo rm *skype*.deb
```

then


[from]("http://www.noobslab.com/2012/06/install-skype-40-in-ubuntulinux-mint.html")


Install Skype on Ubuntu 32bit  [one line at a time]




```
wget -O skype http://download.skype.com/linux/skype-ubuntu_4.0.0.8-1_i386.deb
sudo apt-get install libxss1
sudo dpkg -i skype
sudo apt-get -f install && sudo rm skype

```



Install Skype on Ubuntu 64bit   


```
wget -O skype http://download.skype.com/linux/skype-ubuntu_4.0.0.8-1_amd64.deb
sudo apt-get install libxss1 lib32stdc++6 lib32asound2 ia32-libs libc6-i386 lib32gcc1
sudo dpkg -i skype
sudo apt-get -f install && sudo rm skype



```


[COLOR=#800000]then go to synaptic and lock version so 4.1 will not be installed at your next update 
  [this of course until 4.1 becomes compatible **for all** with Raring][/COLOR]

---

### Post by kuvanito on 2013-04-07
nice to know,just did it last night on debian 7.0 after someone suggested it but 4.0 does not support MSN

---

### Post by shantiq on 2013-04-07
well kuvanito  many will only use skype as a free videophone;    just glad i got a way for time being  ;  msn might have to wait :KS   until 4.1 is good for everyone   [some people i think ok on 4.1 not sure]

---

### Post by stoneguy on 2013-04-07
To give Skype 4.1 its turn at bat, see [http://ubuntuforums.org/showthread.php?t=2133061]("http://ubuntuforums.org/showthread.php?t=2133061")

Skype 4.0 is the one used before RR. I suspect that the Canonical repos aren't consistent with 4.1 yet. Hopefully they'll sort it out by the Apr 25.

---

### Post by xc3RnbFO8P on 2013-04-08
this works:
> LD_PRELOAD=/usr/lib/i386-linux-gnu/mesa/libGL.so.1 skype

[https://bugs.launchpad.net/ubuntu/+source/apport/+bug/1097773]("https://bugs.launchpad.net/ubuntu/+source/apport/+bug/1097773")

---

### Post by shantiq on 2013-04-12
apparently a fix for 4.1 [here]("http://www.webupd8.org/2013/04/fix-skype-not-working-in-ubuntu-1304.html")   [i have not tried it as happy with 4.0 personally until really fixed]

---

### Post by loganloganlogan on 2013-04-14
Appreciate you posting this. New to Linux (just installed 13.04 on my rMBP today!) and ran into trouble with Skype. This worked perfectly. xo

---

### Post by Iwaneez on 2013-05-04
Thanks boss. I am using Lubuntu 13.04 and now, three weeks after the bug still isn't fixed. I spent 3 days getting it to work, but with no luck. Until i get to your post. This really helped me. Thnak you :)

---

### Post by cariboo on 2013-05-04
Raring was released over a week ago, there's no need to comment on what went on during the last development cycle. Thread Closed.

---

