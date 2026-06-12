---
title: "Can't Play Encrypted DVDs In 12.10"
date: 2012-10-14
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by jlacroix on 2012-10-14
This is frustrating. I tried several DVDs in Kubuntu 12.10 and I cannot view any of them. This worked fine in Arch Linux (the distro I switched from).

The first thing I did was install libdvdcss2. I also tried enabling the medibuntu repository, and reinstalled libdvdcss2 again. Both times, I executed: ```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

When I run vlc -v, I get this:
```
VLC media player 2.0.3 Twoflower (revision 2.0.2-93-g77aa89e)
[0x231a108] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configurations from ~/.fonts.conf is deprecated.
libdvdnav: Using dvdnav version 4.2.0
libdvdread: Using libdvdcss version 1.2.12 for DVD access
libdvdnav: DVD Title: THE_DARK_NIGHT
libdvdnav: DVD Serial Number: 394E6B6F
libdvdnav: DVD Title (Alternative): THE_DARK_NIGHT
libdvdnav: Unable to find map file '/home/jlacroix/.dvdnav/THE_DARK_NIGHT.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f60000. Regions: 1 4

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0002bf80
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0002c08f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000403b2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x003b0958
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x003b36d8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x003c3664
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x003c8a12
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x003c8a22
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x003c8a72
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003c8a82
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x003c8ad2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x003c8ae2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x003c8b32
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x003c8b42
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x003c8b92
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x003c8ba2
libdvdread: Elapsed time 0
libdvdread: Found 9 VTS's
libdvdread: Elapsed time 0
libdvdnav: Suspected RCE Region Protection!!!

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1994 ***
*** for pgci_ut->nr_of_lus < 100 ***
```

I saw in the output above that it is complaining about the region. I already set my drive to region 1 previously. However, I figured "what the heck" and did that again. Same problem.

Once, by some stroke of luck, I got it to play and 
[This is what it looked like]("http://imageshack.us/a/img18/2277/snapshot2jg.png").

I'm very frustrated and I hope someone can help me. This is messing with my leisure time. I understand 12.10 is beta but I am still hoping to work around this.

---

### Post by cariboo on 2012-10-14
The output says that the DVD is region 1 4, have you tried setting the region to 4?

---

### Post by jlacroix on 2012-10-14
> **cariboo907 said:**
> The output says that the DVD is region 1 4, have you tried setting the region to 4?
Thanks for the response. I took that to mean that it is viewable in regions 1 and 4. I am in the United States (region code 1) and all my DVDs were purchased in this country (so they are all region 1 as well). These DVDs all worked in Arch Linux on the same PC with the same drive.

---

### Post by cariboo on 2012-10-14
I have the same dvd in my library, I'll give it a try once I dig it out.

---

### Post by cwsnyder on 2012-10-14
Did you install the full **kubuntu-restricted-extras** package, or just libdvdcss2?  And did you install the libdvdcss2 prior to installing VLC?

You may want to try installing **kubuntu-restricted-extras** for the other codecs (mp3 audio and required video) as well as the special codecs needed for commercial DVDs, then removing VLC and re-installing.

---

### Post by jlacroix on 2012-10-14
> **cwsnyder said:**
> Did you install the full **kubuntu-restricted-extras** package, or just libdvdcss2?  And did you install the libdvdcss2 prior to installing VLC?

You may want to try installing **kubuntu-restricted-extras** for the other codecs (mp3 audio and required video) as well as the special codecs needed for commercial DVDs, then removing VLC and re-installing.
Good suggestion. I installed kubuntu-restricted-extras and reinstalled vlc (after purging it and removing all dependencies) then reinstalled it, and same problem. DVDs don't work in Dragon Player either.

Edit: On second thought, that DID work. Now, all the DVDs I'm trying (except for The Dark Knight) are working. I suppose I'll give up on Batman and check out something else.

Thank you both so much!!!

---

### Post by cariboo on 2012-10-14
I haven't found my copy of The Dark Knight, I usually rip my dvd's using handbrake, and then put them away. I did try the Avengers, that worked without a problem in Totem. VLC crashed on me, so I'll have to find and try mc4man's solution to the crash and see what happens.

---

### Post by mc4man on 2012-10-14
While TDK may have some structure protection likely old enough not to cause any issue with current dvdnav.

I'd try this - 
Insert the dvd, close out any player that starts, if any.
Then go into home folder & delete .dvdcss folder or if desired browse thru .dvdcss & delete folder associated with TDK if you can discern.
Then try again, you may have gotten corrupted or incorrect keys previously.

(players always ck. .dvdcss first & use those keys if found even when they are incorrect/incomplete, ect.

Alt. - 
if you can locate the DKR folder in .dvdcss then find the same folder from your arch install & replace the one in your kubuntu install with it.

---

### Post by jlacroix on 2012-10-15
> **mc4man said:**
> While TDK may have some structure protection likely old enough not to cause any issue with current dvdnav.

I'd try this - 
Insert the dvd, close out any player that starts, if any.
Then go into home folder & delete .dvdcss folder or if desired browse thru .dvdcss & delete folder associated with TDK if you can discern.
Then try again, you may have gotten corrupted or incorrect keys previously.

(players always ck. .dvdcss first & use those keys if found even when they are incorrect/incomplete, ect.

Alt. - 
if you can locate the DKR folder in .dvdcss then find the same folder from your arch install & replace the one in your kubuntu install with it.
Thanks so much. TDK started working on its own a bit later. I guess something in restricted extras was needed.

---

