---
title: "Bittorent Clients 'Benchmark'"
date: 2009-06-02
forum: The Cafe
---

### Post by Pasdar on 2009-06-02
I was deciding on which bittorrent client I should use, so I was checking the resources they use and what not to decide which one to use. Thought I'd write everything for everyone else to read too.

**The system I did my tests on:**
Ubuntu 9.04 (running KDE 4.2.3 DE)
AMD Athlon 3000+ (2.2 Ghz)
1.5 GB DDR

You'll get the same results in GNOME, only it'll be more resource intensive and it'll generally be slower.

**Bittorrent Clients used:** Deluge, Ktorrent, Transmission

**RESOURCES WHILE UNUSED (MINIMIZED IN TRAY) [Least resources to most]:**
1. Transmission, 0% CPU, 4 MB MEM, 9 MB Shared MEM
2. Ktorrent, 0% CPU, 6 MB MEM, 20 MB Shared MEM
3. Deluge, 1-5% CPU, 19 MB MEM, 23 MB Shared MEM

**RESOURCES WHILE DOWNLOADING 5 MOVIES (MINIMIZED IN TRAY) [Least resources to most]:**
1. Transmission, 0-1% CPU, 9 MB MEM, 12 MB Shared MEM
2. Ktorrent, 6-12% CPU, 16 MB MEM, 26 MB Shared MEM
3. Deluge, 2-9% CPU, 22 MB MEM, 25 MB Shared MEM

**TIME IT TAKES TO START PROGRAM (MEASURED USING MY OWN PERSEPTION) [from fast to slow]:**
1. Transmission
2. Ktorrent
3. Deluge

**TIME IT TAKES TO SHOW WINDOW FROM TRAY (MEASURED USING MY OWN PERSEPTION) [from fast to slow]:**
1. Transmission
2. Deluge & Ktorrent [Equal speed]

**Conclusion:** If looks and maybe features are not important for you and all you want to do is download, then you'll use Transmission. Transmission on KDE responds to anything almost the instant you click, on GNOME it's slightly slower but still the fastest. If you care about extra features and looks you'll have to choose between Ktorrent and Deluge. They both look good, and (imo) if you want good looks, lot's of features and good response time and such, you'll go with Ktorrent.

---

### Post by bruno9779 on 2009-06-02
Ktorrent is just my piece of cake

---

### Post by geoken on 2009-06-02
Why are you placing more importance on RAM usage than CPU usage? IMO, 8mb of ram is of less consequence than the differences in CPU usage.

Also, the drain on network resources (which I have no idea how to measure) is arguably more important than actual system resources. Other than utorrent in WINE, all the major torrent apps will virtually lock up my router significantly reducing the network performance of every computer in my home.

---

### Post by happysmileman on 2009-06-02
'rtorrent' in a 'screen' session on an always on computer that you can SSH to FTW.

---

### Post by binbash on 2009-06-02
Which versions did you use?

I am asking it because there was a bug at deluge (it is fixed at 1.1.8 ) which causes high CPU usage (Show speed at title bar bug),

Also you are comparing system usages but Transmission is a crap torrent client with NO features.Benchmarking with system usage is a wrong method to determine best torrent client.

---

### Post by AtticusG3 on 2009-06-02
I agree with both statements from geoken and happysmileman.

However, to me features are important, and so there is only one choice, and that is sadly utorrent in WINE.



Off Topic - happysmileman, your sig is absolutely correct and I have always corrected people when they say this. The phrase is "I couldn't care less", those who say "I could care less" are simply moronic and have regurgitated what they have heard incorrectly.</endrant>

---

### Post by Dark Aspect on 2009-06-02
I hate the way ktorrent hogs my system now, it was so much better before KDE4 imo. Now the program is slow and buggy, I use rtorrent when I need now. I get a little more than 12% CPU usage though so it could be a bug or the fact that when I run ktorrent I have gnome and KDE running.

---

### Post by Tibuda on 2009-06-02
I only disagree about looks. Transmission is a lot prettier for me.

---

### Post by Pasdar on 2009-06-02
**Versions:**

Deluge 1.1.7
Ktorrent 3.2.1
Transmission 1.61

---

### Post by HappyFeet on 2009-06-02
> **binbash said:**
> Transmission is a crap torrent client with NO features.

Why is that? It has per torrent bandwidth usage control and a blocklist. What other features do you need? Bittorrent is about uploading and downloading, which it does very well.

---

### Post by Polygon on 2009-06-02
transmission seems to connect to a LOT fewer peers then deluge/utorrent/everything else i try, im not sure why that is, but the end result is that it downloads a lot slower and i upload almost nothing, and combined with the lack of a lot of even basic features, is a bit disconcerting.

---

### Post by lovinglinux on 2009-06-02
> **binbash said:**
> which versions did you use?

I am asking it because there was a bug at deluge (it is fixed at 1.1.8 ) which causes high cpu usage (show speed at title bar bug),

also you are comparing system usages but transmission is a crap torrent client with no features.benchmarking with system usage is a wrong method to determine best torrent client.

+1

---

### Post by Pasdar on 2009-06-02
> **Polygon said:**
> transmission seems to connect to a LOT fewer peers then deluge/utorrent/everything else i try, im not sure why that is, but the end result is that it downloads a lot slower and i upload almost nothing, and combined with the lack of a lot of even basic features, is a bit disconcerting.

I didn't add this because I thought I was the only one having trouble with Deluge. However, Deluge doesn't seem to connect to anything for me in the past week. Download is slow and there is barely any upload going on. Once I started to use Transmission, both download and upload went very fast.

I'm not used to downloading speeds below 300 KByte/s. However, I was downloading at 10-100 KB/s the past week on Deluge... uhhg... it could be because I upgraded from 1.1.6 to 1.1.7.

---

### Post by FuturePilot on 2009-06-02
> **Polygon said:**
> transmission seems to connect to a LOT fewer peers then deluge/utorrent/everything else i try, im not sure why that is, but the end result is that it downloads a lot slower and i upload almost nothing, and combined with the lack of a lot of even basic features, is a bit disconcerting.

I've noticed the same thing too.

---

### Post by evermooingcow on 2009-06-02
Last time I tried rotrrent it didn't have the scheduler feature that deluge has to keep N torrents downloading at once at all times while increasing N as appropriate to account for slow torrents. Downloading one or two torrents at a time is no problem but if I put in 30-40 at a time it is just not as efficient.

Once rtorrent is able to do this it will instantly become my favorite client.

I don't remember why I decided not to use transmission. Maybe I'll try it again - I'm sure its improved since I last tried it..

---

### Post by binbash on 2009-06-02
> **futurepilot said:**
> i've noticed the same thing too.

+2323242424

---

### Post by xpod on 2009-06-02
> I didn't add this because I thought I was the only one having trouble with Deluge. However, Deluge doesn't seem to connect to anything for me in the past week. Download is slow and there is barely any upload going on. Once I started to use Transmission, both download and upload went very fast.

I dont have this issue with Deluge i`m glad to say.
I rarely get my full 20Mb`s(2500Kb`s) with single torrents but speeds of 5,6,7-800Kb`s are quite common.I can get full speed on single ones but that depends on the torrent.

---

### Post by iTrickU on 2009-06-02
I prefer QBittorrent over ktorrent although i haven't tried the others. QBittorrent's download in order feature was very useful and it felt faster

---

