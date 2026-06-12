---
title: "keyring password control"
date: 2017-06-29
forum: Security
---

### Post by SimonHGR on 2017-06-29
Hi all, my problem might have many differing solutions, so I'll explain it before I ask for the solution that I think I need.

I installed Ubuntu on a friend's laptop, and he has "his password" (yeah, I know, but he's an old guy and getting him onto Linux was a huge step and I'm not interested in the lecture about how he shouldn't do this with his password--at least he's not on windows any more :) so hopefully we can all just live with that). Anyway, as you've doubtless guessed, "his password" is insufficient for the desires of the regular password changing tool in the config GUI. So, I changed it with "sudo passwd user". But now, every time he logs in and starts Chrome, he gets that nagging "enter keyring password" box.

I would like the keyring to continue to exist (since I assume it does something useful, though I've never seen it work, since my own system has this configured "properly"), and to do its thing, but not to need this extra help.

So far, I've tried two routes, but failed.

First, I went into /etc/pam.d/common-password, and removed the "obscure" entry (his password is long enough, just not "good" enough). This did not appear to have any effect on the GUI tool, so no joy there.

Second, I started searching for ways to manually change the keyring password, but that search rapidly disappeared down collapsed rabbit holes, and I gave up. I can't even work out if we're running PAM, or gnome-keyring, or something else. I *think* it's gnome-keyring, but the man page for that is very brief and unhelpful, and refers to other man pages that aren't even installed.

Any help would be much appreciated.

Cheers!

---

### Post by SimonHGR on 2017-06-29
Indeed, I now find that I cannot even enter the "right" password in the keyring prompt. This might be because I don't recall accurately what I used, though I'm pretty confident, but the bottom line is the same, I need to find a root-privilege function that can force this issue. Hoping someone can help with that!

TIA!

---

### Post by cariboo on 2017-06-30
Start in recovery mode, and create a new password for the user:

```
passwd $USER
```

---

### Post by SimonHGR on 2017-06-30
Thanks, I was probably unclear. That's actually what caused the problem ;)

I used passwd to force a "too weak" password on the user, but the passwd command does not (evidently??) interact with the keyring, hence, the keyring remains locked on login, and pops up this annoying box. Worse, I don't recall (also evidently!) the password I first used, so I cannot unlock the keyring. I need an equivalent of the passwd command that works on (and can force, using root privilege) the keyring.

All that said, I got desperate and just rebuilt the entire machine, and now he's having to learn to use a slightly more complex password. Not happy about it, and I'm afraid it might make him reject linux entirely (yeah, I know, but there you go). Fingers are crossed, however ;)

Thanks for taking the time to help, I much appreciate it.
Cheers.

---

### Post by deadflowr on 2017-06-30
You should be able to reset the login keyring by simply removing it.
First back it up
```
cp ~/.local/share/keyrings/login.keyring ~/local/share/keyrings/login.keyring.backup
```
then delete the keyring
```
rm ~/.local/share/keyrings/login.keyring
```
then a reboot should reset it and sync with the password.
The downside is that this deletes any saved passwords that where in the keyring.

---

