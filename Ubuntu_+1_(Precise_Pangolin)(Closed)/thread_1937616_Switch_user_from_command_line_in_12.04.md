---
title: "Switch user from command line in 12.04?"
date: 2012-03-08
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by edm1 on 2012-03-08
Im trying to bind a keyboard shortcut to do the equivalent of clicking 'Me Menu>Switch User Account...'

In 11.10 I used ```
gdmflexiserver -xnest
``` to switch users without logging out however I think gdm has now been completely removed.

How can I invoke a user switch in 12.04?

---

### Post by winh8r on 2012-03-08
just enter

```
su newusername
```

then the password for that user.

---

### Post by edm1 on 2012-03-08
Sorry I probably wasnt as clear as I should have been. Im trying to bind a keyboard shortcut to do the equivalent of clicking 'Me Menu>Switch User Account...'

---

### Post by winh8r on 2012-03-08
This is more of a guess than a known solution , but can you not use:

```
gconf-editor
```

or maybe it has no use in 12.04 (not using my 12.04 machine at the moment)

Hope this either helps or gives you some inspiration!!!!

---

### Post by edm1 on 2012-03-10
No, im not trying to change any settings. I need to know how 12.04 is doing the equivalent of of 11.10's command 'gdmflexiserver -xnest'.

---

### Post by tista on 2012-03-10
Hi edm1,

I also didn't know how lightdm could do that...
Even though I've hosted experimental gdmm 3.2.1 on my ppa.

And it seems to be fixed on lightdm?
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/868363]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/868363")
But unfortunately I didn't use lightdm but gdm 3.2.1...

Cheers,
Tista

---

### Post by edm1 on 2012-03-10
Thankfully found out the answer. The replacement is 

```
dm-tool switch-to-greeter
```

---

### Post by fjgaude on 2012-03-10
> **edm1 said:**
> Thankfully found out the answer. The replacement is 

```
dm-tool switch-to-greeter
```

Wow, that's an interesting fine. Thank you.

---

