---
title: "Font problem in About Ubuntu Document"
date: 2010-08-29
forum: The Cafe
---

### Post by ranjank on 2010-08-29
How to solve this ? I am getting some numbers in small boxes instead of letters .

---

### Post by devondashla on 2010-08-29
I'm having this same problem with Maverick. It's just when I open "About Ubuntu". though, so it doesn't bother me much.

---

### Post by ranjank on 2010-08-31
It is not a problem for me , but it must be solved before the release of Maverick . Someone please solve  it .

---

### Post by hhh on 2010-08-31
Try installing unifont and it's dependencies...

```
sudo apt-get install unifont
```

---

### Post by Ruesca on 2010-11-01
I had similar problems, in a lot of my system windows the text was not readable. Instead of prober letters only empty boxes/squares were displayed. I solved the problem according to Ray Woodcock's blog [http://raywoodcockslatest.blogspot.com/2010/09/ubuntu-1004-adding-fonts-from-windows.html](http://raywoodcockslatest.blogspot.com/2010/09/ubuntu-1004-adding-fonts-from-windows.html) with the following three commands

```
sudo dpkg-reconfigure libcairo2 libpango1.0-common
sudo fc-cache -fs
sudo update-pangox-aliases

```

hope that helps, cheers

---

