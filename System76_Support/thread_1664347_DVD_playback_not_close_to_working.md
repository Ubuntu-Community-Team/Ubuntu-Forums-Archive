---
title: "DVD playback not close to working"
date: 2011-01-10
forum: System76 Support
---

### Post by azion1995 on 2011-01-10
OK, big problems w/DVD playback. I know that the DVD-RW drive *should* work, since I have used it to read and write data files to CDs + DVDs. But no dice with DVD playback. VLC gives me the following errors:

p, li { white-space: pre-wr [COLOR=#FF0000]Playback failure:[/COLOR]
 [COLOR=#000000]DVDRead could not open the disc "/dev/dvd".[/COLOR]
 [COLOR=#FF0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'dvd:///dev/dvd'. Check the log for details.[/COLOR]

Unfortunately, a Google search on the above only yielded suggestions to do what I'd already done, which was reinstall ubuntu-restricted-extras and ubuntu-restricted-addons.

One variable: this DVD-RW is not a factory install in my Ratel Ultra. I had planned to transfer my EIDE drives over, and hadn't considered that the new box might not include any EIDE connectors whatsoever. So, I had to purchase a third-party DVD-RW drive. There is a possibility that there is a jumper I had to move, or that I needed to use a different SATA port than I did.

Any assistance would be much appreciated, since I have precious little hair remaining to pull out of my head.

Thx,
-Z

---

### Post by isantop on 2011-01-13
I think you'll want to run this command in the terminal:
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```
That will actually install DVD support from the ubuntu-restricted-extras package. They ought to include that in the post-installation scripts; I'm sure there's some legal issue keeping them from being able to.

---

### Post by motoperpetuo on 2011-03-01
i'm having the same problem with DVD playback on my brand-new lemur. i tried running the code you suggested and got following ouput:

```

--2011-02-28 22:55:09--  http://packages.medibuntu.org/dists/maverick/free/binary-amd64/Packages
Resolving packages.medibuntu.org... 88.191.127.22
Connecting to packages.medibuntu.org|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8010 (7.8K) [text/plain]
Saving to: `/tmp/dvdcss-lS4UeN/Packages'

100%[======================================>] 8,010       49.1K/s   in 0.2s    

2011-02-28 22:55:10 (49.1 KB/s) - `/tmp/dvdcss-lS4UeN/Packages' saved [8010/8010]

--2011-02-28 22:55:10--  http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb
Resolving packages.medibuntu.org... 88.191.127.22
Connecting to packages.medibuntu.org|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 38080 (37K) [application/x-debian-package]
Saving to: `/tmp/dvdcss-lS4UeN/libdvdcss.deb'

100%[======================================>] 38,080      78.6K/s   in 0.5s    

2011-02-28 22:55:10 (78.6 KB/s) - `/tmp/dvdcss-lS4UeN/libdvdcss.deb' saved [38080/38080]

(Reading database ... 132687 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.10-0.3medibuntu1 (using .../dvdcss-lS4UeN/libdvdcss.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.10-0.3medibuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

i'm still getting the same errors as the original poster when i try to play a DVD in VLC. does anyone else out there have any ideas? maybe there's even a step-by-step guide somewhere that i wasn't able to find? i'm surprised this is so difficult.

---

