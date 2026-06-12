---
title: "Two factor authentication enough or also keys?"
date: 2015-09-04
forum: Server Platforms
---

### Post by lenn-art on 2015-09-04
Besides the standard restrictions (no root login, only groupmembers ssh can login, etc) i've activated Google Two Way-authentication. See [this post]("https://www.digitalocean.com/community/tutorials/how-to-protect-ssh-with-two-factor-authentication") if you're interested. The method is working good.

Is it also necessary to install keys? 

I mean, what is this layer adding?

---

### Post by TheFu on 2015-09-04
More layers provide more hurdles to secure access. Only you can decide how many and which layers are needed.
Only you can decide if software from any provider is more or less secure too.

TL;DR - no, it is not mandatory, but I would.  ssh keys are one of those few things that make things both more secure AND easier to use.

---

### Post by lenn-art on 2015-09-04
> **TheFu said:**
> More layers provide more hurdles to secure access. Only you can decide how many and which layers are needed.
Only you can decide if software from any provider is more or less secure too.

TL;DR - no, it is not mandatory, but I would.  ssh keys are one of those few things that make things both more secure AND easier to use.

TL;DR for 2 lines :'-)

It's on a VPS, so the provider is me = very unreliable .. 

I was thinking, does the layer of keys add an extra encryption to the traffic or is the key only for validating?

---

### Post by TheFu on 2015-09-04
Keys are only for authentication. 

If you already use a strong passphrase to unlock the ssh-keys and prevent brute-force attacks with something like **fail2ban**, the risks to your VPS are pretty tiny.  Sure, if you travel internationally then 2FA can make sense.  I have a yubikey and prepend a pin to the resulting "passphrase" when I'm out of the country.  I'm used to smartphones NOT being connected and don't really trust google enough for this sort of solution. That is a personal hangup of mine.  I have a backup ssh account with a random 88 character login.

It was 1 line, before adding the TL;DR and spacing. ;)

[http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures) might be helpful.

---

### Post by lenn-art on 2015-09-04
Tnx! Fail2ban is on, but is interfering with my own IP-tables file. Next thing to find out ..

---

