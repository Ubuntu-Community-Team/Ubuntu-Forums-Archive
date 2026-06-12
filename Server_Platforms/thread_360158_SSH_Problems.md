---
title: "SSH Problems"
date: 2007-02-12
forum: Server Platforms
---

### Post by DustinW on 2007-02-12
Im getting the following error when trying to login..Im typing "$ssh name@ipaddress" in terminal (OSX) to access my ubuntu server. 

Any ideas how fix fix this?
  @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
  @    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
  @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
  IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
  Someone could be eavesdropping on you right now (man-in-the-middle attack)!
  It is also possible that the RSA host key has just been changed.
  The fingerprint for the RSA key sent by the remote host is
  23:00:20:83:de:02:95:f1:e3:34:be:57:3f:cf:2c:e7.
  Please contact your system administrator.
  Add correct host key in /home/xahria/.ssh/known_hosts to get rid of this message.
  Offending key in /home/xahria/.ssh/known_hosts:8
  RSA host key for localhost has changed and you have requested strict checking.
  Host key verification failed.

---

### Post by kidders on 2007-02-12
Hi there,

Part of the reason SSH is so trusted is that it does some checks to make sure you're talking to who you *think* you're talking to, when you try to open a connection. In your case, the remote host's identification key has changed, so your SSH client makes the assumption that it's not the same computer it was yesterday.

The solution is in your o/p though...

> Add correct host key in /home/xahria/.ssh/known_hosts to get rid of this message.
Offending key in /home/xahria/.ssh/known_hosts:8If I were you, I would just delete line 8. The correct key will be added the next time you connect.

Among other reasons, this kind of thing will happen if you reinstall your SSH server, or if someone is impersonating your computer. OSX's SSH client is basically leaving it up to you to determine whether there's a reasonable explanation for the identification change.

I hope that helps.

---

### Post by DustinW on 2007-02-12
I see how it happened now...but for the life of me Im not sure were to find the file to edit! i type in "$gedit /home/xahria/.ssh/Known_hosts"  and nothing...You know how I can find the file?

---

### Post by kidders on 2007-02-12
You're looking in the right place. Was the capital 'K' a typo?

**Edit:** Just out of curiosity, the command "$gedit..." makes it look like you have gedit running on OSX. :confused: What's in the $gedit variable?

---

### Post by DustinW on 2007-02-12
I was trying to find the file on the linux server.. SHould I be looking for the file on my my mac?
I may ahve been trying the wrong thing..ohh..and the "K" was a typo.


thanks for the help thus far!

Dustin

---

### Post by kidders on 2007-02-12
Ahhh I see. Sorry...

> **DustinW said:**
> I was trying to find the file on the linux server.If you've used SSH on your Linux box (you may not have), a similar file would be there too, but it would be the wrong one. The computer that has the objection is your Mac, so the known_hosts you should be modifying is there.

---

