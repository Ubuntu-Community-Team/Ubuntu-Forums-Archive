---
title: "Encoding Speed: Arch64 vs Gutsy64"
date: 2007-10-21
forum: The Cafe
---

### Post by ahaslam on 2007-10-21
Thought I'd share this little surprise: 

The command:
```
mencoder dvd://13 -oac mp3lame -lameopts abr:br=128 -ovc xvid -xvidencopts bitrate=1440 -vop scale -zoom -xy 720 -o trailer.avi

```

Time for Arch64:
```
real    2m22.479s
user    2m18.091s
sys     0m0.417s
```
Time for Gutsy64:
```
real    0m57.347s
user    0m53.791s
sys     0m0.348s
```

This was just a 2 minute trailer, imagine the difference on a 2 hour film. The dev's obviously got something right, Arch is no slouch ;)

---

### Post by insane_alien on 2007-10-21
woot for gutsy!

thats quite a huge difference.

---

### Post by ahaslam on 2007-10-21
> **insane_alien said:**
> woot for gutsy!

thats quite a huge difference.

Yeah, maybe I'll have to change the link in my sig to 'make Arch run like Ubuntu' ;)

---

### Post by argie on 2007-10-21
Hmm, is it any faster than Gutsy32?

---

### Post by ahaslam on 2007-10-21
> **argie said:**
> Hmm, is it any faster than Gutsy32?

It should be. Tests I've done before have shown 20-30% improvement in 64-bit.

---

