---
title: "Amazon MP3 Downloader stopped working in Hardy"
date: 2008-04-23
forum: System76 Support
---

### Post by Gorlith on 2008-04-23
Upgraded to Hardy w/ System 76 Driver, all my old programs/packages seem to be running fine except Amazon MP3 Downloader. It keeps trying to download the tracks but then says it cant connect and asks me to check my internet connection, which is of course working.

I'm sure amazon will resolve this once they put out the hardy version (this was a gutsy version), but I figured I'd give the heads up.

---

### Post by doorknob60 on 2008-04-25
Yeah, they'll fix it soon :) Also, I didn't know they had a Linux downloader, so I'm happy :d (I knew it was in development but that's it)

---

### Post by wnmnkh on 2008-04-27
Oh my god. I never imagined Amazon ever succeed in making Linux downloader. I gave up and got over with it after months of waiting.

---

### Post by isaacj87 on 2008-04-27
Yup, I tried it out once...it actually is really sweet...Works just like any other MP3 store, yet it's all DRM-Free woot!

:guitar:

---

### Post by Gorlith on 2008-04-28
Yeah I really liked the downloader, worked great for me. Now I have to wait for an update : / whenever that happens.

---

### Post by hebetude on 2008-05-04
Awesome what happens to this CD I just purchased but cant download?

---

### Post by thomasaaron on 2008-05-05
If you still have the gutsy kernel on your computer, you could boot into it via your grub menu...

(When you boot up and see the "grub...3....2...1..." countdown, press the "Esc" key and choose the Gutsy kernel)

...and download the song from there.

---

### Post by Gorlith on 2008-05-05
> **hebetude said:**
> Awesome what happens to this CD I just purchased but cant download?

I managed to convince them to refund me two albums I had sitting in  Queue and could not download.

---

### Post by hebetude on 2008-05-10
> **Gorlith said:**
> I managed to convince them to refund me two albums I had sitting in  Queue and could not download.

They unlocked the mp3s for me, so I could go to the site and download them one at a time.
IMO, it should be that way anyways...  it's much simpler than supporting the 100 platforms out there.

---

### Post by kihaji on 2008-05-10
I had the same error, using a 64 bit 8.04, it seemed a lot like this error

[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/220377](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/220377)

so I installed lib32nss-mdns and it now works.

---

### Post by hebetude on 2008-05-10
> **kihaji said:**
> I had the same error, using a 64 bit 8.04, it seemed a lot like this error

[https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/220377](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/220377)

so I installed lib32nss-mdns and it now works.

Confirmed, works great after you install lib32nss-mdns

---

### Post by Gorlith on 2008-05-12
Great find guys! Nice to have this running again.

---

### Post by eric2701 on 2008-05-29
Thanks, that was a good find.  How did you figure out that was the problem?

---

### Post by Niscrome on 2008-08-31
For those who don't have _**64 bit Hardy**_ try downloading gtreamer Fluendo in synaptic (search: **Fluendo**) then installing or reinstall Amazon downloader!

It worked for me.

reference:Here
[http://allaboutubuntu.wordpress.com/2008/03/04/amazoncom-meets-ubuntu/:popcorn:](http://allaboutubuntu.wordpress.com/2008/03/04/amazoncom-meets-ubuntu/:popcorn:)

---

