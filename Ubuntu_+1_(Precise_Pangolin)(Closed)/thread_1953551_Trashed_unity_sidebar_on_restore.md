---
title: "Trashed unity sidebar on restore?"
date: 2012-04-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by NHclimber on 2012-04-06
Is this a known bug?  [https://launchpadlibrarian.net/100458187/Screenshot%20from%202012-04-06%2013%3A21%3A18.png](https://launchpadlibrarian.net/100458187/Screenshot%20from%202012-04-06%2013%3A21%3A18.png)

---

### Post by kurja on 2012-04-06
I get this too, every time the machine wakes from suspend.

---

### Post by xyzzyman on 2012-04-06
Happens on 11.10. Are we all using the nvidia binary driver?

---

### Post by bluenova on 2012-04-06
Always happened to me.
nVidia proprietary

---

### Post by NHclimber on 2012-04-06
Please go me too this bug

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/975332]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/975332")

If you know of duplicates, feel free to mark this bug as a duplicate.

---

### Post by xyzzyman on 2012-04-06
I think this will turn into a won't fix issue as it's all on the nvidia binary. I bet that switching vt's by ctrl-alt-f1 then back to X by ctrl-alt-f7 also stalls for a bit for you, which is a known issue with the nvidia binary and not an ubuntu pp issue.

---

### Post by kurja on 2012-04-06
> **xyzzyman said:**
> Happens on 11.10. Are we all using the nvidia binary driver?

nvidia here.

---

### Post by kurja on 2012-04-06
> **xyzzyman said:**
> I think this will turn into a won't fix issue as it's all on the nvidia binary. I bet that switching vt's by ctrl-alt-f1 then back to X by ctrl-alt-f7 also stalls for a bit for you, which is a known issue with the nvidia binary and not an ubuntu pp issue.

I'm not experiencing any issues with ctrl-alt-f1 -> ctrl-alt-f7 though.

---

### Post by xyzzyman on 2012-04-06
> **kurja said:**
> I'm not experiencing any issues with ctrl-alt-f1 -> ctrl-alt-f7 though.

I just tried it, and it is much quicker than it was. All throughout 11.10 and even until a week ago it was extremely slow to switch back to VT7. There are a few bugs open but they all say it's an nvidia issue... Looks like something has changed. My bad.

Still it seems the corruption is only happening with people using the nvidia binary.

---

