---
title: "Avi file which was encoded by Mencoder is not recognized by portable dvd player"
date: 2009-06-24
forum: Ubuntu Studio
---

### Post by haneulso on 2009-06-24
I want to convert video files to play it by portable dvd player.

I will use this command.

"mencoder foo.avi -ovc lavc -oac mp3lame -o foo2.avi -ffourcc XVID"

The problem is video image size.

My player cannot play a file which has image size over 720x480.

But, some video image size of my video files are over 720x480.

I want to downsize its image size without change of resolution ratio.

How can I get this?

In summary, how can I downsize video resolution without change of resolution ratio.

---

### Post by andrew.46 on 2009-06-25
Hi haneulso,

> **haneulso said:**
> 

```
mencoder foo.avi -ovc lavc -oac mp3lame -o foo2.avi -ffourcc XVID
```

The problem is video image size. My player cannot play a file which has image size over 720x480. But, some video image size of my video files are over 720x480.

I want to downsize its image size without change of resolution ratio.

There is the easy way that I always used when I was more of a MEncoder fan. The following sets the horizontal size to 720 while allowing MEncoder to set the vertical size based on the aspect ratio:

```

mencoder foo.avi **[COLOR="Purple"]-vf scale -zoom -xy 720[/COLOR]** -ovc lavc \
        -oac mp3lame -o foo2.avi -ffourcc XVID

```

Hope this helps?

Andrew

---

### Post by haneulso on 2009-06-25
Thanks.
It work great.

---

### Post by andrew.46 on 2009-06-25
Hi haneulso,

> **haneulso said:**
> Thanks. It work great.

Good news! There are many other little extras you could add to that command line but if you are happy with the result I reckon stick to that :-).

Andrew

---

