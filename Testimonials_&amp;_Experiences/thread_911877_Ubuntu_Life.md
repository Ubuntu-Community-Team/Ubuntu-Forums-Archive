---
title: "Ubuntu Life"
date: 2008-09-06
forum: Testimonials &amp; Experiences
---

### Post by zombrax on 2008-09-06
Five months ago, I decided to install Ubuntu on my laptop. This was at that time; just a test mahcine to see what the hype was all about Ubuntu. I was a long time fan of Linux having installed flavours like Red Hat, Debian and Mandrake. But with all of the above, I survived a few months before switching back to M$.

So I tried installing the Desktop version of Feisty Fawn 7.04 first but I got lots of errors so I tried to install the Server version on it. To my surprise; Ubuntu installed perfectly with no errors and detecting every single hardware that I had on the laptop. I was impressed and happy and made a decision that I was going to spend more time and learn Linux finally! Thus I decided to take this laptop on my 6 month long stint away from home. I didn't know much about Ubuntu at this stage; I should say much about Linux in general but I thought that if I took this laptop then I had no choice but to learn about it. 

Now to give you an idea about my laptop; it has a Celeron Coppermine processor (anyway to find out the exact speed?), only had an initial 128MB RAM, a CD-ROM and 10GB HDD. The graphics card is CyberBlade XPAi1.

My first issue was the laptop being way too slow to load up anything. So I jumped on EBay and ordered another 128MB of RAM; this arrived within 2 weeks from the US and gave me a total of 256MB; which made things a bit more quicker. It sill made my life easier as I mainly use lappy for the net, GIMP and play video clips. 

Secondly, even though my wireless card was detected; for some reason I still could not connect to the local network via Wireless. The network is running WPA encryption. But I had a work around which was to use a CAT5 connection. I had to walk about 50m to access this as I couldn't get it from my room but still it wasn't a real big hassle. At this stage, I had another issue and that was the fact that I couldn't for some weird reason connect to my proxy server which obviously I needed to connect to the net. This really stumped me for about 2-3 weeks; I researched everywhere and asked a lot of fellow Ubuntuans but after trying everything and looking at my proxy settings a million times I still couldn't figure it out. Then one early morning I looked at my settings again and there it was right in front of me!! 198.168.1.1:3128 is way different to 192.168.1.1:3128!! Such a silly user error and it took me that long to work it out. Anyways, putting this behind me I did all the updates and added and downloaded a few new programs like VLC media player etc which at that time I couldn't because of proxy issue but I had a workaround this; read it [here]("http://ubuntuforums.org/showthread.php?t=761288") if you want. 

Thirdly, to see if I could speed up the lappy a bit more, I tried to increase the page file. At first it took a bit of looking around and asking fellow folks on the forum but eventually I got a solution from the forums itself. And thus that was solved!

As my laptop is close to 5 years old and not having a DVD-ROM in this modern age and being away from home makes it really hard to enjoy your spare time. So I bought a WD My Book 750GB ext HDD and filled it up with lots of movie files. I have no probs accessing this drive from the laptop; but when I access movie files and after a few random flick through various clips I simply this blue screen on my laptop. I have no work around this other than holding the power button down to turn the laptop off and power it back on. I strongly suspect that this is due to the lack of memory I have on this laptop as I have checked a few times when just having Firefox and terminal running I would have about 3-4MB RAM left :( But I sort of live with this issue as I understand that my hardware is 5 years old and I don't expect it to work miracles for me.

In the last five months, apart from working shift work and working around the clock in some extreme conditions, I have dedicated a lot of time to learn Ubuntu. I'm happy with my progress so far. Some of the stuff that I have learned are simple like using terminal to update/upgrade, doing administrative tasks, playing around with GIMP, installing CODECS etc etc. I have also bought a book "Beginning Ubuntu Linux - From Novice to Professional" which I think is a fantastic book although I'm still going through it. This book has also taught me a lot of tips and tricks along with new ways of doing things and learning administrative stuff. 

I still have outstanding issues like Wireless and I cannot restart the system as it simply hangs when trying to reboot after shutdown and issues with video. But I don't see these as critical problems but with time I would be able to solutions and not workarounds. 

Overall I'm a happy Ubuntuer. I love to learn more and plan to become a Linux Administrator one day and above all to help others on this forum. My only advice to ppl who has issues at first is to spend time on it and to look around rather than just giving up. I, for one know that with persistence you can almost achieve anything.

Many thanks for reading my rant. What I intend to do from here will be covered in another thread.......

---

### Post by hyper_ch on 2008-09-06
have you got wpasupplicant installed? I think by default older versions (before hardy) don't support wpa out of the box.

---

### Post by steveneddy on 2008-09-06
Keep plugging away.

Welcome.

---

### Post by Crafty Kisses on 2008-09-06
Welcome aboard, and hopefully it's a good one. :)

---

### Post by zipperback on 2008-09-06
It nice to hear that you are happy with Ubuntu and that you are working through the difficulties as you learn a new operating system.

In regard to wireless, I have Ubuntu Hardy 8.04.1 installed on my laptop and I am running open source madwifi driver that I compiled. It supports WPA without any problems for me.

I've also noticed that things generally work alot better on my laptop with Ubuntu Hardy than they did with the previous release.

Is there anything preventing you from upgrading your system to the currently available release of Ubuntu?

- zipperback
:popcorn:

---

### Post by zombrax on 2008-09-07
> **zipperback said:**
> It nice to hear that you are happy with Ubuntu and that you are working through the difficulties as you learn a new operating system.

In regard to wireless, I have Ubuntu Hardy 8.04.1 installed on my laptop and I am running open source madwifi driver that I compiled. It supports WPA without any problems for me.

I've also noticed that things generally work alot better on my laptop with Ubuntu Hardy than they did with the previous release.

Is there anything preventing you from upgrading your system to the currently available release of Ubuntu?

- zipperback
:popcorn:

Only cause my laptop has 256MB of RAM and it is slow as it is man. Isnt the recommended RAM for Hardy much higher?

---

### Post by zombrax on 2008-09-07
> **hyper_ch said:**
> have you got wpasupplicant installed? I think by default older versions (before hardy) don't support wpa out of the box.

I think i have dude, how can I check it to make sure please? I remember doing some bits and pieces for my Wireless back a few months ago but can't remember for sure.

many thanks.

---

### Post by Sef on 2008-09-07
> I think i have dude, how can I check it to make sure please? I remember doing some bits and pieces for my Wireless back a few months ago but can't remember for sure.

To check what version you have of an application, in the terminal type this code:

```
apt-cache policy package_name
```

---

### Post by zombrax on 2008-09-07
many thanks!

zombrax@ub-lap:~$ apt-cache policy wpasupplicant
wpasupplicant:
  Installed: 0.5.7-0ubuntu2
  Candidate: 0.5.7-0ubuntu2
  Version table:
 *** 0.5.7-0ubuntu2 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
        100 /var/lib/dpkg/status

so I have it installed. Where can I go from here? many thanks once again.

---

### Post by Sef on 2008-09-07
> Only cause my laptop has 256MB of RAM and it is slow as it is man. Isnt the recommended RAM for Hardy much higher?256 is the minimum amount of ram needed.  512 works much better.   


>  so I have it installed. Where can I go from here? many thanks once again.     

Check and see if they support your card.

Here is the [wpa supplicant]("http://hostap.epitest.fi/wpa_supplicant/") home page.

Here is a [tutorial]("http://www.thinkwiki.org/wiki/Wpa_supplicant") on installing it.

---

