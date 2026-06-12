---
title: "lightdm 1.1.4-0ubuntu1 a bit of an issue (here"
date: 2012-03-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by mc4man on 2012-03-02
Causes all sessions to fail to load (though do get an excellent plymouth splash..
Maybe my install, maybe not - nvidia hardware

---

### Post by dino99 on 2012-03-02
seen your report but you does not give much details to devs for fixing it; please complete asap

---

### Post by Harry33 on 2012-03-02
The truth is that after upgrading lightdm to the version 1.1.4-0ubuntu1 you cannot start gnome-shell nor gnome-panel-session either.

You have to downgrade to the older version of ligthdm (1.1.3-0ubuntu1).
After that everything works again.

---

### Post by mc4man on 2012-03-02
> **Harry33 said:**
> The truth is that after upgrading lightdm to the version 1.1.4-0ubuntu1 you cannot start gnome-shell nor gnome-panel-session either.

You have to downgrade to the older version of ligthdm (1.1.3-0ubuntu1).
After that everything works again.

It's a bit of a mess here, real ying-yang
Almost all restarts into a ubuntu session now get me to a Desktop,(Didn't till I (re)installed gnome-session), then compiz dies.
All restarts into gnome-session work just fine, then a log out/in to a ubuntu session works

If I go back to the previous lightdm all is good everywhere.

On a A2 install updated that I've screwed around with to no end - all is fine ??
[https://bugs.launchpad.net/bugs/944736](https://bugs.launchpad.net/bugs/944736)

---

### Post by jerrrys on 2012-03-02
Im installing beta this weekend, guess Ill just use gdm until this gets resolved.

---

### Post by Harry33 on 2012-03-02
> **jerrrys said:**
> Im installing beta this weekend, guess Ill just use gdm until this gets resolved.

The newest lightdm version 1.1.4-0ubuuntu1 is not part of the Precise-beta1.
You can install beta, but do not upgrade lightdm. Keep the version 1.1.3-0ubuntu1 or at least downgrade the 1.1.4 before you reboot, if it gets accidentally installed.

---

### Post by zika on 2012-03-02
Or use .Xsession+startx to circumvent trouble...

---

### Post by jerrrys on 2012-03-03
Ok, not a problem for classic users

I went ahead and installed 1.1.4.  Been on it for 30 minutes and it works in gnome-classic

---

### Post by dino99 on 2012-03-03
> **jerrrys said:**
> Ok, not a problem for classic users

I went ahead and installed 1.1.4.  Been on it for 30 minutes and it works in gnome-classic

its due to revert :)


lightdm (1.1.4.is.1.1.3-0ubuntu1) precise; urgency=low

  * Revert to 1.1.3 until we can figure out proper solution to bug 944736

---

### Post by jerrrys on 2012-03-03
> **dino99 said:**
> its due to revert :)

I do get an error message at boot.  but so far, so good.

---

### Post by paul_in_london on 2012-03-03
> **dino99 said:**
> its due to revert :)


lightdm (1.1.4.is.1.1.3-0ubuntu1) precise; urgency=low

  * Revert to 1.1.3 until we can figure out proper solution to bug 944736

It had apparently already been reverted when I updated late last night (64 bit).

From **[COLOR="Red"]/var/log/aptitude[/COLOR]**:

```
[UPGRADE] lightdm 1.1.3-0ubuntu1 -> 1.1.4.is.1.1.3-0ubuntu1
```

Still the same version today so far:

```
paul@precise-64:~$ apt-cache policy lightdm
lightdm:
  Installed: 1.1.4.is.1.1.3-0ubuntu1
  Candidate: 1.1.4.is.1.1.3-0ubuntu1
...

```

---

### Post by prusswan on 2012-03-03
is the error some "fail to start session ubuntu"? I had to do a sudo killall X-org to login properly

---

### Post by paul_in_london on 2012-03-03
> **prusswan said:**
> is the error some "fail to start session ubuntu"? I had to do a sudo killall X-org to login properly

Yes I think that was it. Here's the bug report:

[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/944736](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/944736)

---

### Post by jerrrys on 2012-03-03
Enable your boot log to see whats going on.

[ATTACH]213649[/ATTACH]

---

