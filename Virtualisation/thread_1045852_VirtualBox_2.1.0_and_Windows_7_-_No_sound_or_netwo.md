---
title: "VirtualBox 2.1.0 and Windows 7 - No sound or network?"
date: 2009-01-20
forum: Virtualisation
---

### Post by chazdraves on 2009-01-20
Okay, I'm moving this thread here because this is off the original topic of my previous thread...

I've got Win 7 64-bit and Xubuntu 8.10 64-bit installed with Ubuntu 8.10 host and the Guest Additions, but I still don't have sound or network... I have sound set to ALSA and ACH97 and Network set to NAT... Can anyone help?

Thanks!
- Chaz

---

### Post by chazdraves on 2009-01-21
Anybody?

- Chaz

---

### Post by chazdraves on 2009-01-21
Okay... new discovery... I AM connected to my router (I'm using wireless, if that matters), I'm just not connected to the internet...

Anybody?

- Chaz

---

### Post by chazdraves on 2009-01-21
Okay.. I'm learning more here.. The problem seems to be with my DNS address... but what should it be set to? Anyone?

- Chaz

---

### Post by chazdraves on 2009-01-21
Finally figured it out myself.

- Chaz

---

### Post by Dedoimedo on 2009-01-22
1) Post your solution so others can learn from it.

2) sound issue, Win 7 might not like the basic sound drivers ...

3) network issue, you may need forwarding enabled in the host OS and dns servers defined under /etc/resolv.conf in guests.

Dedoimedo

---

### Post by HotShotDJ on 2009-01-22
VirtualBox 2.1.2 just released today.  It now officially supports Windows 7.  Try upgrading and see if your problems are solved.

---

### Post by chazdraves on 2009-01-22
Yes, I noticed the upgrade this morning. I also noticed that shared folders now work exactly as they should under Windows 7.

Firstly, the networking problem... I didn't know - and I didn't find any documentation anywhere that told me otherwise - but it seems I needed to configure the DNS address under the virtual OS's. I assumed (foolishly) that this would just work "out the box". Once I found my DNS addresses (listed under the resolv.conf file sudo gedit /etc/resolv.con), I input them in both Windows (right-click on the connection name, highlight TCP/IP settings, click configure) and Xubuntu (right-click on the connection in the systray and click "edit connections") and it worked just as I expected. I found a quick test is to see if you can access your router or not. If you can, then the connection is working and you simply need to configure your DNS address; if you can't, then you've got bigger problems and should consult someone more knowledgable than myself.

Once the internet was working, I fixed my second problem by downloading the latest Realtek AC97 drivers. Unfortunately, the audio is a bit rough under Windows, but works perfectly in Xubuntu and the like. It could be that there was a better driver to use, but Windows refused to find it automatically, so I took the easy route out.

Beyond that, I'm sure it doesn't hurt to have 2.1.2 installed either...

Anywho, thanks to you both for your involvement and for reminding me to post what made it work for me (don't I feel stupid now knowing how little a problem it was).

Regards,
- Chaz

---

