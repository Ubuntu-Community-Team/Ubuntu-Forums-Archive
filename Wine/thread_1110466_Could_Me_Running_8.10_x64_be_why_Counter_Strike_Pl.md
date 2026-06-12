---
title: "Could Me Running 8.10 x64 be why Counter Strike Plays Awfully?"
date: 2009-03-29
forum: Wine
---

### Post by punkiishmob on 2009-03-29
I tried everything to get Steam working in Cedega, Wine, and I finally got it working in PlayOnLinux. I guess that's some app with some extra wine features. Steam installed fine, so did CS:S. However, everytime I play

- The text is mushy and very hard to read
- The video is SO CHOPPY. I am running a GeForce 8800 GTX using the 177 recommended driver. 

I tried everything, even disabling Compiz, and CS:S still will not run smooth..

Am I missing something? Is it because I am running Ubuntu x64?

Any help would be appreciated, thanks!

---

### Post by Psyphre on 2009-03-29
go to the properties of the game in steam and try putting in: "-dxlevel 80" under the start up options.

---

### Post by asdfoo on 2009-03-30
> **punkiishmob said:**
> I tried everything to get Steam working in Cedega, Wine, and I finally got it working in PlayOnLinux. I guess that's some app with some extra wine features. Steam installed fine, so did CS:S. However, everytime I play

- The text is mushy and very hard to read
- The video is SO CHOPPY. I am running a GeForce 8800 GTX using the 177 recommended driver. 

I tried everything, even disabling Compiz, and CS:S still will not run smooth..

Am I missing something? Is it because I am running Ubuntu x64?

Any help would be appreciated, thanks!

If you make sure you're using atleast Wine 1.1.17 (get latest from [http://winehq.org](http://winehq.org)) you will find that CS:S works very well on the default dx9 mode.

I also recommend you upgrade your drivers 180.37 works very nicely for me, newer releases have stability and performance fixes.

---

### Post by punkiishmob on 2009-03-31
> **asdfoo said:**
> If you make sure you're using atleast Wine 1.1.17 (get latest from [http://winehq.org](http://winehq.org)) you will find that CS:S works very well on the default dx9 mode.

I also recommend you upgrade your drivers 180.37 works very nicely for me, newer releases have stability and performance fixes.

This is most likely the solution! I will try it out. THANK YOU! :)

---

