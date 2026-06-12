---
title: "Media Programs Cannot Read From Blu-Ray/DVD Source &amp; AC Power Issue"
date: 2012-02-25
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by WilliamGuglielmo on 2012-02-25
I am a long-time user of Ubuntu. I ran Xubuntu on my old laptop. Earlier, I bought a brand new laptop and put Ubuntu 12.04 LTS Precise on it. It was the only Linux distro that came even close to working well. So far so good except for a few issues:

1) Though I have the right DVD codecs installed, none of the media players (Parole, Movie Player, or SMPlayer) can play a DVD. Each has given me the "cannot read from source" message. I don't know if there may be something with newer codecs needed or if it's a driver for the blu-ray/dvd-rw.

2) When I tell Ubuntu to shut down, it restarts when running on AC Power. When it runs on battery, it will shut down just fine.

I know that 12.04 is still in development and that there are bugs that need to be worked out. 

Specifics of my system:
OS: Ubuntu 12.04 LTS 64-bit (32-bit didn't work so well on my system).
Computer: Toshiba Satellite L775D-S7340
Processor: AMD A6-3400M APU w/Radeon HD Graphics (64-bit)
Blu-Ray/DVD-RW: MASHITABD-CMB UJ141EF (straight from the BIOS)

Thanks for all suggestions!

---

### Post by mc4man on 2012-02-25
Running this in a terminal should resolve your dvd issue (dvd, not Blu-Ray
```
sudo apt-get install libdvdread4 && \
sudo /usr/share/doc/libdvdread4/install-css.sh
```

If any continuing then this wouldn't hurt
```
sudo apt-get install gstreamer0.10-plugins-bad \
gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly
```

If still an issue then you may need to set a region on the drive **once**

Don't know about your shut down issue - I have a different shutdown/restart issue here that is most likely hardware/video driver related, yours sounds like something else

---

### Post by WilliamGuglielmo on 2012-02-26
Ran the command to install libdvdread4 and it told me it was already there. But I ran the second command and got this:

```
--2012-02-26 09:33:05--  http://packages.medibuntu.org/dists/precise/free/binary-amd64/Packages 
Resolving packages.medibuntu.org (packages.medibuntu.org)... 88.191.127.22 
Connecting to packages.medibuntu.org (packages.medibuntu.org)|88.191.127.22|:80... connected. 
HTTP request sent, awaiting response... 404 Not Found 
2012-02-26 09:33:07 ERROR 404: Not Found. 

Dynamic fetch failed; Falling back to static fetch 
--2012-02-26 09:33:07--  http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_amd64.deb 
Resolving packages.medibuntu.org (packages.medibuntu.org)... 88.191.127.22 
Connecting to packages.medibuntu.org (packages.medibuntu.org)|88.191.127.22|:80... connected. 
HTTP request sent, awaiting response... 200 OK 
Length: 37252 (36K) [application/octet-stream] 
Saving to: `/tmp/dvdcss-7v0EqD/libdvdcss.deb' 

100%[======================================>] 37,252      92.8K/s   in 0.4s    

2012-02-26 09:33:14 (92.8 KB/s) - `/tmp/dvdcss-7v0EqD/libdvdcss.deb' saved [37252/37252] 

(Reading database ... 134852 files and directories currently installed.) 
Preparing to replace libdvdcss2 1.2.10-0.2medibuntu1 (using .../dvdcss-7v0EqD/libdvdcss.deb) ... 
Unpacking replacement libdvdcss2 ... 
Setting up libdvdcss2 (1.2.10-0.2medibuntu1) ... 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place
```

Ran the command line for the "bad" plugins and they are already there. 

Ran the command line for "ugly" and got this:
```
william@william-Satellite-L775D:~$ gstreamer0.10-ffmpeg gstreamer0.10-plugins-ugly 
gstreamer0.10-ffmpeg: command not found
```

I then tried a DVD again. Parole gave me the "Could not read from source" message. Movie Player, VLC, and SMPlayer tried to play it, but then it somehow told Ubuntu to log me out, and I had to log back in. 

I know how to reset a DVD drive to another region in Windows, not very sure how to do it in Ubuntu.

---

