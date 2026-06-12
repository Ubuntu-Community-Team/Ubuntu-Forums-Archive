---
title: "Problems with opening ports."
date: 2005-06-19
forum: Server Platforms
---

### Post by Moonzag on 2005-06-19
Hi, like the title of this thread says, I'm having problems with opening ports. Normally, I run a Direct Connect hub, but that's kind of hard if you can't open ports. It doesn't matter if it's below or above the root ports, I get the same result - nothing. It's like I'm behind a firewall or something.  ](*,) 

I do not think it's a hardware problems, since the router works well on all the other computers in the network. And I can't recall changing any settings concerning the network. Oh, one more thing. I manged to get it running once, but I had to re-install Ubuntu, and since that install I've been having this problem.

One last thing, it's not my hub software either, no matter what software I use, I get the same result - nothing. Other than that, Ubuntu works just fine.  ;-) 

Thanks, and sorry for my rusty English.

// William Lagerquist

---

### Post by LordHunter317 on 2005-06-19
Unless you installed or setup a firewall, there isn't one running by default in Ubuntu.  So I doubt it's that.

I suspect you forgot to properly redirect the ports on the router. That's the first thing I would check.

---

### Post by Moonzag on 2005-06-19
[QUOTE=LordHunter317]Unless you installed or setup a firewall, there isn't one running by default in Ubuntu.  So I doubt it's that.

I suspect you forgot to properly redirect the ports on the router. That's the first thing I would check.[/QUOTE]

I've checked the settings in the router, over and over again. I've been trying to open ports for various programs, and I don't think I'd make the same mistake for all of 'em.

Or wait, do I have to do something special when opening ports in Linux? o_O

Before I installed Ubuntu I where running the Direct Connect hub on Windows.

---

### Post by LordHunter317 on 2005-06-19
No,  but like I said, unless you installed a firewall, none is running on your Ubuntu box.

The issue is either with your router or your configuration of your direct connect hub.  If you post it's configuration file, I can attempt to review it for you, but I can't promise that I'll be able to fix it--that software is not my expertise.

---

### Post by Moonzag on 2005-06-19
Problem fixed, I'm an idiot.  ](*,) 

But still, how could I have gotten the wrong IP? I copy-pasted it to make sure I didn't make any mistakes. My guess is that I got a new IP after that.

---

