---
title: "quicky question"
date: 2006-08-26
forum: Repositories &amp; Backports
---

### Post by Mazehero55 on 2006-08-26
How come when I try to install the build-essential packages it says I don't have make, gcc, or g++. But I know I have those. And when I try zsnes it says I don't have glx, But I'm pretty sure I do. How can I fix this.

---

### Post by Pragmatist on 2006-08-26
> **Mazehero55 said:**
> How come when I try to install the build-essential packages it says I don't have make, gcc, or g++. But I know I have those. And when I try zsnes it says I don't have glx, But I'm pretty sure I do. How can I fix this.

We need more information.

1. What is **zsnes** ?

2. What *versions* of gcc, g++, etc.... do you have?

3. What program are you using to install software?

4. What is the exact error message your getting?

---

### Post by tzulberti on 2006-08-27
> **Pragmatist said:**
> We need more information.

1. What is **zsnes** ?

zsnes is a Nintendo emulator. It play the nintendo 64 games on you pc.

---

### Post by skymt on 2006-08-28
> **tzulberti said:**
> zsnes is a Nintendo emulator. It play the nintendo 64 games on you pc.

Super Nintendo, actually. </nitpick>

Mazehero55: You're using Synaptic? apt-get? Aptitude?

---

### Post by Mazehero55 on 2006-08-28
sudo -i dpkg

---

### Post by skymt on 2006-08-29
> **Mazehero55 said:**
> sudo -i dpkg

The proper command would be 'sudo aptitude install zsnes', or 'sudo aptitude install build-essential'. Either way, it fetches everything for you.

---

### Post by Mazehero55 on 2006-08-30
oh I'm not really sure what aptitude is.

---

### Post by Senshi on 2006-08-30
[What apt-get is.]("https://help.ubuntu.com/ubuntu/desktopguide/C/apt-get.html")
[apt-get vs. aptitude]("http://www.psychocats.net/ubuntu/aptitude")

---

