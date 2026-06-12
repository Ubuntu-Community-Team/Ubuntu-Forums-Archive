---
title: "FreeNX vs. x2go"
date: 2011-08-02
forum: Security
---

### Post by crush_157 on 2011-08-02
Hi,

To get at a gnome desktop remotely I'm looking at FreeNX or x2go.

Use case is that while the family are using the box under the TV for fun, I can log into it remotely and do other stuff from my aged laptop.  This saves me from spending money on a new laptop that could be invested in a new snowboard.

I'd be interested if anyone has any comments on FreeNX and/or x2go from a security standpoint?

I'm slightly uncomfortable with the fact that neither FreeNX or x2go can be downloaded from the standard Ubuntu repositories (and yes, I know I'm paranoid, but having decided to use Ubuntu means I have to trust the guys at canonical and so I trust the stuff that they vouch for in the repositories).

I also looked at LTSP, but that seemed to be overkill for what I want to do.

Cheers,

Crush_157

---

### Post by cariboo on 2011-08-02
You didn't mention what OS the box beneath the TV was running, if it's running a Linux variant, why not use X-forwarding with ssh?

---

### Post by crush_157 on 2011-08-02
Box beneath the TV is running Ubuntu.

So ssh -X works for most things, but there are times when it is nice to have the full desktop.

---

### Post by hantms on 2011-09-09
Not everything is in the repositories, I would not let that worry me too much.  Ubuntu is already waaaay ahead of other popular distributions (never mind other operating systems) in terms of what can be obtained from the standard app store (repositories).

Keep in mind that if you go with x2go, you still stay within the basic repository-based installation method: you just add the x2go repository which is explained on their site, any other packages that it depends on will be obtained automatically from the standard Ubuntu repositories, it's all very painless, and actually no different from installing things like Google Chrome or Skype.

So, which one is better.. I struggled and failed to make FreeNX work about 9-10 months ago.  I just tried x2go yesterday and it 'just-worked'. ;)

One tip is that they both use ssh, so before getting started with either of them I would first understand sshd, get it configured to the point where you can log in with a terminal using ssh successfully.

I would assume it would work pretty smoothly on a home LAN.. I'm typing this from 10,000 miles away and it's still pretty ok.

---

### Post by amaramrahul on 2012-04-25
I switched from using FreeNX to X2Go for remote connectivity. This decision has been made for the following reasons:
- For X2Go, SSH access to only the user logging in is sufficient. For FreeNX, a separate user "nx" needs to have SSH access.
- For X2Go, user's SSH key can be used for logging in. For FreeNX, this is not possible i.e. user's password has to be used. (I inferred this from the options in x2go client)
- X2Go supports Debian squeeze. For FreeNX, I was using Ubuntu PPA repos.

---

