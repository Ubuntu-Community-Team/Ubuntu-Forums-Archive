---
title: "X-Forwarding-like capability in Wayland?"
date: 2011-04-17
forum: The Cafe
---

### Post by pi.boy.travis on 2011-04-17
I know it's something probably only the geekiest of us use, but will Wayland work over the network? I do quite a bit of 'remote tech support' with:
```
ssh -X user@host
any & X & app & what & have & you
```
And I would very much miss this functionality. I find VNC virtually unusable from anywhere outside the local network, ESPECIALLY over SSH, which is really the only truly safe way to do it. I know rootless X sessions can be run as Wayland clients, but that seems like a half-baked solution to me. . .

Does anyone versed in Wayland know anything about using it over the network?

---

### Post by pi.boy.travis on 2011-04-17
I just realized that the thread title says 'Forwarning' instead of 'Forwarding'. . .

---

### Post by nerdopolis on 2011-04-17
Its not going to be directly supported by the protocol

Its going to require either another app, or a separate version of a Wayland compositor that forwards the windows over the network.

As far as I can tell, it will be possible, but not as native as X

[http://lists.freedesktop.org/archives/wayland-devel/2010-November/000038.html](http://lists.freedesktop.org/archives/wayland-devel/2010-November/000038.html)

---

### Post by pi.boy.travis on 2011-04-17
Something at the toolkit level would be nice. Like sending a steam of toolkit triggers instead of all the redraw crap X uses. . . Or maybe that's the whole point of Wayland to begin with. . . ? Excuse my ignorance, I'm just a simple Chemical Engineer XD

---

### Post by JDShu on 2011-04-17
[http://wayland.freedesktop.org/faq.html#heading_toc_j_8](http://wayland.freedesktop.org/faq.html#heading_toc_j_8)

I believe the important thing to understand is that Wayland is just a protocol. Anything more than that will hopefully be developed in other open source projects later.

---

### Post by Perfect Storm on 2011-04-17
> **pi.boy.travis said:**
> I just realized that the thread title says 'Forwarning' instead of 'Forwarding'. . .

fixed.

---

### Post by pi.boy.travis on 2011-04-17
> **Artificial Intelligence said:**
> fixed.

Thank you kind sir!

---

### Post by 3rdalbum on 2011-04-18
I thought you'd be able to run a nested X on the local and remote machines for the purposes of doing the forwarding?

---

### Post by Lucradia on 2011-04-18
> **3rdalbum said:**
> I thought you'd be able to run a nested X on the local and remote machines for the purposes of doing the forwarding?

What if you're using Windows and need to connect to your X? :V

---

### Post by 3Miro on 2011-04-18
From what I understand Xorg will be able to run on top of Wayland, which will give you all the current features plus more.

---

### Post by Lucradia on 2011-04-18
> **3Miro said:**
> From what I understand Xorg will be able to run on top of Wayland, which will give you all the current features plus more.

Don't you mean side by side? |3

---

### Post by pi.boy.travis on 2011-04-18
> **Lucradia said:**
> Don't you mean side by side? |3

No, actually, I think X would run as a Wayland client. . .

---

### Post by aguafina on 2011-04-18
> **pi.boy.travis said:**
> No, actually, I think X would run as a Wayland client. . .


But what would the point be of running two windowing systems?

---

### Post by 3Miro on 2011-04-18
> **aguafina said:**
> But what would the point be of running two windowing systems?

Backward compatibility. In this scheme, Wayland will be able to run everything from the old Xorg and we can make a gradual shift.

Plus Wayland + Xorg will have better composition support.

---

