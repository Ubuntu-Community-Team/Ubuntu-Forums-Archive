---
title: "virtual box pcbsd runs out of disk space"
date: 2012-03-06
forum: Virtualisation
---

### Post by carusoswi on 2012-03-06
So, I finally was able to successfully create a virtual bsd machine onto which I installed PC-BSD.  I set the disc size to 20 gb, which should be plenty of space.

I let PC-BSD configure the partitions.

Yet, after installing just one application (Cinepaint), the system complains that it is running low on storage space (my machine has 1TB of storage, and I have set the sizing in VB to be dynamic.

So, why do you think I am running out of disc space?

Thanks for any replies.

Caruso

---

### Post by Lyfang on 2012-07-17
Please post the following output, open the Terminal:
```
df -h
```

---

### Post by CharlesA on 2012-07-18
> **carusoswi said:**
> So, I finally was able to successfully create a virtual bsd machine onto which I installed PC-BSD.  I set the disc size to 20 gb, which should be plenty of space.

I let PC-BSD configure the partitions.

Yet, after installing just one application (Cinepaint), the system complains that it is running low on storage space (my machine has 1TB of storage, and I have set the sizing in VB to be dynamic.

So, why do you think I am running out of disc space?

Thanks for any replies.

Caruso
I have a feeling you think dynamic disk means it will grow if needed. The virtual drive is set to 20GB, having it set up as dynamically allocated only means the file on the host will grow in size as needed, instead of taking the entire 20GB up at once.

---

