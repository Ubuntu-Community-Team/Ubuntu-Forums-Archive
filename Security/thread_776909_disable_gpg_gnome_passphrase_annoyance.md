---
title: "disable gpg gnome passphrase annoyance"
date: 2008-05-01
forum: Security
---

### Post by heisters on 2008-05-01
I have .gpg files encrypted with a GPG key that I use a vim plugin to edit handily. Now some smartass Hardy Heron app is getting in my way.

In the terminal when I type "vi foo.gpg" a gnome dialog pops up titled "Passphrase" and asking for the key's passphrase. I can't move the dialog box (it spawns itself neatly between my two monitors), I can't give any other windows focus, and, as if that weren't enough, if I try to cancel out of it vim is unable to edit the file.

Does anyone have any idea how to disable this ********?!?

I'll just take this moment to vent my frustration: I did not install this doohicky, and it's this kind of "helpful" software that royally pisses me off. I've been using Ubuntu since Warty, and Hardy is seriously making me consider switching to another distro or os.

---

### Post by HermanAB on 2008-05-01
ps -e
kill -9 PID

---

### Post by heisters on 2008-05-01
> **HermanAB said:**
> ps -e
kill -9 PID

well of course. And xkill would work too. Are you suggesting I should also do the following in .bash_aliases?

```

alias vi="xkill & vi"

```

Actually, just for kicks, I just tried to get the PID of whatever it is by starting it and then opening a new terminal and doing ps ax. But this little bugger seems to swallow all inputs so I can't even open a second terminal. I can't even do Ctrl-Alt-F1 to go to one of the virtual terminals.

I also tried killing the bugger with xkill per my suggestion. It works, but just like when you cancel out of it, vi can't get into the file. And now I seem to have killed the parent process as well, which makes the dialog not pop up, but vi still can't access the file.

---

### Post by epolin on 2008-07-10
It is worse than that: the dialog box appears even when you use the --passphrase option!!! So that my backup script, which prompts for the password then uses it on several files, cannot run unattended any more. A bug caused "intentionally" by mere stupidity is no laughing matter.

---

### Post by heisters on 2008-07-10
> **epolin said:**
> It is worse than that: the dialog box appears even when you use the --passphrase option!!! So that my backup script, which prompts for the password then uses it on several files, cannot run unattended any more. A bug caused "intentionally" by mere stupidity is no laughing matter.

wow, that's rich! But that's actually a big problem, not just a terrible design decision. I've filed a bug report, please feel free to add your 2 cents, though I've taken the liberty of including the problem you're experiencing.

[https://bugs.launchpad.net/ubuntu/+bug/247345](https://bugs.launchpad.net/ubuntu/+bug/247345)

---

