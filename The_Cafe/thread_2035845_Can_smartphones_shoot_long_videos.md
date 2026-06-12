---
title: "Can smartphones shoot long videos?"
date: 2012-07-31
forum: The Cafe
---

### Post by azangru on 2012-07-31
Digital camerals are usually capable of recording videos, sometemis even in full HD, but are seriously limited in the allowed length of the recorded videos since 1) they use FAT32 file systems with the 4GB size limit per file, and 2) the ability to record videos 30 minutes long or longer officialy turns a digital camera into a digital camcorder, which attracts higher taxes and requires the manufacturer to pay for certain codec licences.

So does anybody know how it is with the smartphones? From what I've googled, Android smartphones use ext4, so the file size limitation is irrelevant. Can these phones record videos longer that 30 minutes or does this restriction apply to them as well?

---

### Post by ssam on 2012-07-31
my nokia n900 (running maemo) claims to be able to record for 99 minutes.

---

### Post by azangru on 2012-07-31
> **ssam said:**
> my nokia n900 (running maemo) claims to be able to record for 99 minutes.

Wow, I have Nokia n900 too. Never checked its tech specs on video though.

But n900's internal storage is formatted in Fat32. Will Android phones with ext4 do better?

---

### Post by ssam on 2012-07-31
i left it recording for 50 minutes, which made a 1.3 GB file. it got quite warm and used a lot of battery.

if you are up for a bit of tinkering i am sure you can reformat the file system on an n900 to ext4 ( [http://talk.maemo.org/showthread.php?t=71653](http://talk.maemo.org/showthread.php?t=71653) ). You could also stream from the webcam directly to a file using gstreamer ( [http://talk.maemo.org/showthread.php?t=46046](http://talk.maemo.org/showthread.php?t=46046) ), which would let you control the format and compression, and probably get you past the 99 minute limit.

---

### Post by oldsoundguy on 2012-07-31
fat 32 is dos or Windows based .. ext4 is Linux based (Android is Linux based) .. they are non compatible.

---

### Post by azangru on 2012-08-01
> **ssam said:**
> if you are up for a bit of tinkering i am sure you can reformat the file system on an n900 to ext4 ( [http://talk.maemo.org/showthread.php?t=71653](http://talk.maemo.org/showthread.php?t=71653) ). You could also stream from the webcam directly to a file using gstreamer ( [http://talk.maemo.org/showthread.php?t=46046](http://talk.maemo.org/showthread.php?t=46046) ), which would let you control the format and compression, and probably get you past the 99 minute limit.

I turned on the camera on my n900 and switched to the video mode. Then I cycled through different video quality options. There are three: high, medium and low. I am not sure what each other means, but I would expect that the low quality video will take less space. However, with all three quality settings the maximum length of the video recording remained the same - 99 minutes and 59 seconds.

So I believe in Nokia case it's the software that sets the time limit, not the file size.

---

### Post by Lymphocyte on 2012-08-01
beware not all android devices use ext4, my kindle fire has its storage formatted fat32 (blame amazon)

---

### Post by alexfish on 2012-08-01
[IMG]http://news.bbc.co.uk/media/images/40005000/jpg/_40005936_pedroso.jpg[/IMG]

---

### Post by ssam on 2012-08-02
> **azangru said:**
> I turned on the camera on my n900 and switched to the video mode. Then I cycled through different video quality options. There are three: high, medium and low. I am not sure what each other means, but I would expect that the low quality video will take less space. However, with all three quality settings the maximum length of the video recording remained the same - 99 minutes and 59 seconds.

So I believe in Nokia case it's the software that sets the time limit, not the file size.

i suspect that its just the camera app limiting it. did you try with the gstreamer command?

something like
```
gst-launch v4l2camsrc device=/dev/video0 ! avimux ! filesink location=/media/mmc1/test.avi
```

(you may need to apt-get install gstreamer-tools). you can put a huge number of interesting things in gstreamer pipeline. try searching for gst-launch at [http://talk.maemo.org/](http://talk.maemo.org/)

---

