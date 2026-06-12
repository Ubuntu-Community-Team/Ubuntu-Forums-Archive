---
title: "Make user group only able to run certain programs as root?"
date: 2008-02-20
forum: Security Discussions
---

### Post by smartboyathome on 2008-02-20
I was wondering how I could make it so that a user could only use admin privilages on certain programs? Would I do this by editing the sudoers file? Also, is there a way to get visudo to use nano instead of vim (vim is really confusing for me)? I am wanting to make it so that the group (student) can only run Synaptic, Add/Remove Programs, and Ubiquity (so it can be installed). Is this possible?

---

### Post by HermanAB on 2008-02-22
Yes, it is explained very well in the sudoers man page.  I can't explain it any better, so I'm sorry, but you got to RTFM.  The man page is good.

Cheers,

Herman

---

### Post by p_quarles on 2008-02-22
> **smartboyathome said:**
> I was wondering how I could make it so that a user could only use admin privilages on certain programs? Would I do this by editing the sudoers file? Also, is there a way to get visudo to use nano instead of vim (vim is really confusing for me)? I am wanting to make it so that the group (student) can only run Synaptic, Add/Remove Programs, and Ubiquity (so it can be installed). Is this possible?
Hmm. I had thought that visudo in Ubuntu/Debian used nano by default. Anyway, you can force it to use nano easily:
```
export EDITOR=nano && sudo visudo
```

---

### Post by smartboyathome on 2008-02-23
> **HermanAB said:**
> Yes, it is explained very well in the sudoers man page.  I can't explain it any better, so I'm sorry, but you got to RTFM.  The man page is good.

Cheers,

Herman

Ok, thanks, I looked it up, and it does tell me how to do this. :)

Also, thanks p_quarels for that command, it works.

---

