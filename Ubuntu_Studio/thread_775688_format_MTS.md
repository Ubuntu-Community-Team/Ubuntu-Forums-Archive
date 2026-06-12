---
title: "format MTS"
date: 2008-04-30
forum: Ubuntu Studio
---

### Post by ninicoco on 2008-04-30
I have a sony camcorder that save video in MTS format.

How can i read this format with Ubuntu?

Thanks for any help.

---

### Post by warbread on 2008-05-01
Have you tried VLC?  It's well known for playing just about anything.  Give it a try, it can't hurt. 

What you can do, if that fails, is convert the .mts into a .avi file.  Instructions can be found [here]("http://wesleybailey.com/blog/2008/01/20/m2tstoavi-avchd/").  Let me know if you have specific questions.

---

### Post by Malcy on 2008-05-01
At the moment, you have to use m2tstoavi to convert from AVCHD to H264 avi. This works well in video editors like KDEnlive. It should be possible to change the m2tstoavi code slightly to convert to a lower resolution format as well, such as DVD resolution mpeg2. At present an easy solution to convert the H264 avi file produced by m2tstoavi to something else is by using ConvertIT, a mencoder front end. You can find ConvertIt and m2tstoavi by searching these forums.

---

### Post by bsmith1051 on 2008-05-01
Does m2tstoavi re-encode it (bad) or re-package it (good)?

---

### Post by Stochastic on 2008-05-01
> **bsmith1051 said:**
> Does m2tstoavi re-encode it (bad) or re-package it (good)?

It transcodes it (good, because then you can use the previously locked proprietary format) and only if you set the output to be a lossy compression will you loose information.  (if I'm not mistaken - not a video whiz myself)

---

### Post by bsmith1051 on 2008-05-01
avchd is not a proprietary format, it's just a new as-yet-unsupported one.  And truly uncompressed HD video runs about 10 GB per minute so that's not a reasonable option.

---

### Post by RebateFX on 2008-08-22
> **warbread said:**
> Have you tried VLC?  It's well known for playing just about anything.  Give it a try, it can't hurt. 

What you can do, if that fails, is convert the .mts into a .avi file.  Instructions can be found [here]("http://wesleybailey.com/blog/2008/01/20/m2tstoavi-avchd/").  Let me know if you have specific questions.

I tried that, thanks, but the resulting output is anything but HD quality. Very blocky. Is there a way to fix it? I suppose I could just try and break the script myself hehe.

---

### Post by bsmith1051 on 2008-08-22
> **warbread said:**
> Have you tried VLC?  It's well known for playing just about anything.  Give it a try, it can't hurt.
FYI - the current 'beta' 0.9 version of VLC doesn't play AVCHD files, at all.

---

