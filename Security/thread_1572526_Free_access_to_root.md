---
title: "Free access to root?"
date: 2010-09-11
forum: Security
---

### Post by dwel on 2010-09-11
I was in the process of moving /home to a seperate partition. I somehow got the uuid wrong in fstab, thats not the problem, I know what went wrong. The problem is: when the new /home couldnt be mounted, ubuntu offered me a choice. Auto blah blah to try and fix it or to do it manually. I opted for manual.

The next screen displayed me was a terminal, with a prompt. I typed in startx and to my amazement x started, as root, without ever having typed a password. Why? Root has a password, I know this. Is it a bug? a fluke? Should I (we) be concerned?



Dwel

---

### Post by OpSecShellshock on 2010-09-11
Don't think so. It probably took you into recovery mode, which would get you a root user in order to fix whatever was causing the trouble. The root user isn't really enabled for normal user sessions, so under regular working conditions you can't just log in as root. In recovery mode you can. This is only really a security problem if the person doing it isn't you, but it requires the person doing it to be physically present at the computer (i.e. it can't be done remotely). This is why people on these forums say physical access is the same as root access.

However, starting a graphical desktop session while in that mode is quite risky. Mostly because of the potential for accidental damage.

---

### Post by CharlesA on 2010-09-11
Unless you enabled the root account, root is locked, so booting to a root shell from recovery mode doesn't prompt for a password.

This is by design. You can set it to prompt for the root password, but you need to enable the root account which isn't worth the risk imo.

---

### Post by dwel on 2010-09-11
I have not intentionally enabled root, if it is locked by default. And , it was root, I actually went in and fixed fstab with it, not having to sudo before gedit.

Im not upset or anything, it took me by suprise.

---

### Post by OpSecShellshock on 2010-09-11
> **dwel said:**
> I have not intentionally enabled root, if it is locked by default. And , it was root, I actually went in and fixed fstab with it, not having to sudo before gedit.

Im not upset or anything, it took me by suprise.

Yeah, it seems a bit alarming when coming to it cold, but in context it makes sense. If it actually asked for a password, users wouldn't be able to use the recovery console.

---

### Post by CharlesA on 2010-09-11
> **OpSecShellshock said:**
> Yeah, it seems a bit alarming when coming to it cold, but in context it makes sense. If it actually asked for a password, users wouldn't be able to use the recovery console.

Indeed. I only really know about it because I was doing research on something else and stumbling across the info.

But yah, physical access = root access for the most part, since if someone has physical access, they can just boot off a livecd, to get access.

---

### Post by movieman on 2010-09-11
> **CharlesA said:**
> But yah, physical access = root access for the most part, since if someone has physical access, they can just boot off a livecd, to get access.

Bingo: encryption is the only way to protect your files from an attacker who has physical access to the machine.

---

### Post by bodhi.zazen on 2010-09-12
> **dwel said:**
> I was in the process of moving /home to a seperate partition. I somehow got the uuid wrong in fstab, thats not the problem, I know what went wrong. The problem is: when the new /home couldnt be mounted, ubuntu offered me a choice. Auto blah blah to try and fix it or to do it manually. I opted for manual.

The next screen displayed me was a terminal, with a prompt. I typed in startx and to my amazement x started, as root, without ever having typed a password. Why? Root has a password, I know this. Is it a bug? a fluke? Should I (we) be concerned?

Dwel

[https://wiki.ubuntu.com/SecurityTeam/FAQ#Rescue%20Mode](https://wiki.ubuntu.com/SecurityTeam/FAQ#Rescue%20Mode)

As has been pointed out, Physical access == root access. The only possible protection would be encryption, although physical access can circumvent encryption as well.

---

