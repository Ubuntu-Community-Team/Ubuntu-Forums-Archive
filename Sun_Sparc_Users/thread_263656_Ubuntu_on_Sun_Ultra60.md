---
title: "Ubuntu on Sun Ultra60"
date: 2006-09-23
forum: Sun Sparc Users
---

### Post by tideline on 2006-09-23
I know this has been covered in other posts, but I think it _may_ help others.  I finally got Ubuntu to install on my Ultra60.  Basically, when I tried to install from the first CD I burned, I got the Illegal Instruction error.  So it was off to net boot, However, I was getting Timeout for ARP/RARP request every time I tried.  So i read somewhere that perhaps the speed I wrote the CD with may be part of the problem.  Sure enough I wrote the CD at 8x and bammmm it worked.  Hope this might help others.

Mike

---

### Post by tideline on 2006-09-24
Anyone know where I can get the latest afb.ucode?  the one I have doesn't work, at least I think it's the problem.

I am getting 

```
FB0: Loading Elite3D microcode...
mmap user regs: Invalid argument
done.
```

Thanks for any help
Mike

---

### Post by scottie4442 on 2007-02-22
Did you ever git this fixed, I am having the same problem.  I do have the Solaris 10 DVD, I will see if the afb.ucode is on it, if so I can send it to you.

Added: I have the Solaris 10 version of the afb.ucode, I got it off of one of my Ultra 10's.  I do not know if it is the newest but it is the one that Solaris 10 installs.  If you private message me your e-mail I will send it to you

---

### Post by scottie4442 on 2007-02-22
I copied the Solaris 10 afb.ucode file to /usr/lib/ and it still gives me this error, so it is not the afb.ucode file.

---

