---
title: "Thoughts on POP!_OS"
date: 2024-08-12
forum: Ubuntu, Linux and OS Chat
---

### Post by sports fan Matt on 2024-08-12
What are your thoughts on POP!_OS?  I'm trying it in a live session at the moment.

---

### Post by Shibblet on 2024-08-14
> **sports fan Matt said:**
> What are your thoughts on POP!_OS?  I'm trying it in a live session at the moment.

Pop_OS! is great!  I love their Pop-Shop design.  I also think that they are doing a great thing with the "Cosmic" desktop.  This really puts some style into System 76.

---

### Post by makitso on 2024-08-15
I looked at it this week.  Doesn't seem to support desktop icons.

---

### Post by Rubi1200 on 2024-08-15
Tried the latest alpha in a VM.

Not sure what to make of it yet.

Will wait until the stable version is released and then take another, closer look.

---

### Post by Dennis N on 2024-08-15
I have tried Pop OS 22.04 only in a VM.  Based on Ubuntu 22.04 and gnome 42.9. It modifies the gnome desktop with several "Cosmic" gnome shell extensions to change functionality and create the "Cosmic Desktop". The big problem for me is that their installer has no support for LVM*. I require that. For many people it would be fine. I saw other differences from the standard Gnome desktop - some good, some not so much, but I will leave it at that.

I should also mention that the installer creates a 4G recovery partition, and a 1G ESP, so on my 20G vm, I lose 5G of that off the top.

-------------------------
*I looked into this again, and while the installer by itself cannot install using LVM (it has no mention of LVM anywhere), an LVM install can be done by using the terminal of the live session to set up the LVM structure _before_ starting the actual installation, then choosing the custom install option. You can also avoid the 4G recovery partition.

---

### Post by davetheoldcoder on 2024-08-23
I've been using Pop!_OS for almost six years, and have been happy with it.

But I'm starting to question whether it's adequately supported. The primary business of the company that develops it is making Linux computers (which are very good quality), not developing software.

Pop!_OS 24.04 is only in Alpha, while Ubuntu 24.04 was released four months ago.

That's why I decided to return to Ubuntu.

---

