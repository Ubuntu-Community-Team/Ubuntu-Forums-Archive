---
title: "Different way of mounting"
date: 2005-03-31
forum: Repositories &amp; Backports
---

### Post by keffo on 2005-03-31
Ok, hey.

I have this problem. I need to mount a MINI-IMAGE to run a game, and
in Windows.. it works perfectly.. I just mount it with latest daemon-tools
and theres no problem.

Now the problem in Linux, might be I dont really know how todo this.
Im not really sure about this, I mounted it some way and tried some
stuffs.. But it doesnt work.

Im using Cedega, so I might have to tell Cedega to use that mini-image?
I dunno.. im open for all suggestions.

Its an .mds / .mdf-file

Please help out

---

### Post by soul_rebel on 2005-04-03
never heard of this format, look if it is linux supported and open, maybe it's a proprietary one and linux can't do anything about it.

---

### Post by Bo Rosén on 2005-04-03
One option is to find the mdf2iso tool that converts mdf to iso. I have it, but don't remember where I got it sorry, google helped me though so try that.

then you need to enable the loop in the kernel. 

```

sudo modprobe loop

```

and if you want it everytime you boot

```

sudo gedit /etc/modules

```
and add 'loop' at the end of the file (without the quotation marks)

Then, whenever you need to mount an iso image just type something like this:
```

sudo mount -o loop /mnt/iso /home/me/some-iso-or-other.iso

```

anyway, I hope that is correct, I always get mixed up about the paths...

As for Cedega, can't help you there.

---

