---
title: "Gnome-keyring - Anyone know a lot about it?"
date: 2012-11-15
forum: Security
---

### Post by fixitdude on 2012-11-15
Can anyone who has used and understands Gnome-keyring please tell me how it works before I install it?

I've got one program that always says it wont save any passwords because Gnome-keyring is not installed or is not accessible.

But I am a little weary because the LIMITED info on the net says that it might also store SSH passwords and I really don't want to do that.

So one question is, does Gnome-keyring have some sort of GUI where you can configure it?

Another is, can I configure it to not accept password requests from certain programs?

Will it interfere with KDE Wallet?

---

### Post by trimmer on 2012-11-16
I have the "Passwords & Keys" software installed and it has 3 tabs:

1) Passwords
2) Personal Keys
3) Public Keys

This software is powered by Seahorse and integrates the gnome-keyring, Gnu Privacy Guard and the SSH/SSL keystore into one location. I recommend it.

Gnome-keyring is a repository of your session passwords, UUID's and SSO's and it can also be configured to hold those logins across reboot. According to Launchpad and it's very own maintainers, this is their definition, "gnome-keyring is a program that keeps password and other secrets for users. It is run as a damon in the session, similar to ssh-agent, and other applications can locate it by an environment variable.

The program can manage several keyrings, each with its own master password, and there is also a session keyring which is never stored to disk, but forgotten when the session ends."

It is encrypted by the very least your login password and it offers even more security. If you are using EFS for your $HOME dir then you also have that to fall back on as well. Security is layered and individuals are best served by adding as many layers as their infrastructure allows without sacrificing "much" performance. It really isn't as cumbersome as it sounds and requires little to know interaction.

I hope you find this helpful.

If not here is the complete description of what gnome-keyring is and how it works. It is a binary command in the Seahorse package.

[Seahorse 2.30.1]("http://library.gnome.org/users/seahorse/stable/")

---

