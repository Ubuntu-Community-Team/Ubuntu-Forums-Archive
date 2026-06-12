---
title: "Question about SSH Key Agent."
date: 2010-08-04
forum: Security
---

### Post by Stormsy on 2010-08-04
Hi there,

I've had Ubuntu for about two weeks and I really like it!  I have to admit - it was a bit strange getting use to the concept of having no Anti-virus or any firewall software installed.  But now I've gotten over it, I am quite content with Ubuntu.  It's my only OS installed on my Dell Laptop.

I've been having a poke about Ubuntu (as you do with a new OS) and under System > Preferences > Start-up applications, I noticed that "SSH Key Agent" was ticked to start up when the Ubuntu was booted.

From what I understand, SSH is **not** installed when Ubuntu is first installed, and also SSH is used if you use a server (you have to manually install from Synaptic Package Manager if you want to use it).  I understand that, but I do not understand as to why I have this entry ticked in Start-up applications?

Under the entry, the description mentions; "GNOME Keyring: SSH agent" - I think Keyring is like a password safe where you save all your passwords and have just a master password? If so, is it safe to untick this entry to stop it from starting up when I boot my laptop?

Many thanks,
Stormsy. :)

---

### Post by rookcifer on 2010-08-04
That's just the SSH *client*.  It's not a server.  It's essentially the same thing as the gpg-agent.  It helps with handling your SSH keys.  If you don't use SSH at all then you can disable it.

---

### Post by FuturePilot on 2010-08-04
SSH key agent is basically like a keyring. You can have it unlock SSH keys when you login or have it remember the password for the session so you don't have to constantly type it when you connect to an SSH server.

You're pretty much spot on about Gnome Keyring. Only it's no so much for *you* to store passwords as it is for applications to store passwords. A lot of applications store account passwords in gnome-keying. This is nice because it is well integrated with the Gnome desktop and it offers a secure way for applications to store account passwords. Disabling this will cause things to break or annoyingly prompt you to unlock your keyring. Best to leave it alone IMO.

---

