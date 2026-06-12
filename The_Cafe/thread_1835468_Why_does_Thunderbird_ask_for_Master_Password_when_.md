---
title: "Why does Thunderbird ask for Master Password when program starts?"
date: 2011-08-29
forum: The Cafe
---

### Post by nrundy on 2011-08-29
I'd like Thunderbird to be able to start and run without having to input a password. Yet I'd like a password to be prompted for if Show Passwords is selected.

How come in order to have a password prompt appear when I select Show Passwords, I have to put up with a password prompt everytime I start the program? Is this the only way protecting the passwords from being seen in plain text can work, or it could be coded differently and Mozilla just hasn't done it?

Anybody else wish they could start Thunderbird without a password prompt but still get a password prompt when trying to view the account passwords in plain text?

---

### Post by MadCow108 on 2011-08-29
thunderbird always needs the password to be able to decrypt your saved passwords and use it to login to your mail provider.

the only way to not have to enter a secret at login is to only store the passwords in encoded form (= no master password => **not** encrypted).

---

### Post by Lucradia on 2011-08-29
> **MadCow108 said:**
> thunderbird always needs the password to be able to decrypt your saved passwords and use it to login to your mail provider.

the only way to not have to enter a secret at login is to only store the passwords in encoded form (= no master password => **not** encrypted).


This is why Pidgin doesn't ask for it, though, if that were true with empathy, then it should ask for the password too to decrypt the passwords.

---

### Post by zekopeko on 2011-08-29
What should actually happen is for Thunderbird to integrate into the system's keychain so that you are asked only once for your password instead of every application implementing their own keychain software.

---

### Post by nrundy on 2011-08-29
It would sure be preferable if the user only had to enter the Master Password when trying to view the Passwords.

---

### Post by Lucradia on 2011-08-29
> **zekopeko said:**
> What should actually happen is for Thunderbird to integrate into the system's keychain so that you are asked only once for your password instead of every application implementing their own keychain software.

Unfortunately, Thunderbird is independent of DEs :V

---

### Post by alphacrucis2 on 2011-08-29
> **Lucradia said:**
> Unfortunately, Thunderbird is independent of DEs :V


True for the vanilla Moz T'bird but the version that will be shipped with 11.10 has been modified to integrate with the Unity DE as T'bird has been adopted as the default email client in that release. I don't know if keychain integration is part of that as I haven't tried 11.10 yet.

---

### Post by Lucradia on 2011-08-29
> **alphacrucis2 said:**
> True for the vanilla Moz T'bird but the version that will be shipped with 11.10 has been modified to integrate with the Unity DE as T'bird has been adopted as the default email client in that release. I don't know if keychain integration is part of that as I haven't tried 11.10 yet.

Unity is not a DE.

Even the about page is not found: [http://unity.ubuntu.com/about](http://unity.ubuntu.com/about)

It still is GNOME-heavy. If it were truly a DE, it'd strive to be lighter than GNOME, to be honest.

---

### Post by alphacrucis2 on 2011-08-29
> **Lucradia said:**
> Unity is not a DE.

Even the about page is not found: [http://unity.ubuntu.com/about](http://unity.ubuntu.com/about)

It still is GNOME-heavy. If it were truly a DE, it'd strive to be lighter than GNOME, to be honest.

Well yes. I guess calling it a shell for gnome is the best description. Funny that the "about" link doesn't work. Maybe it should be bugged on launchpad as a unity documentation fault.

---

### Post by Lucradia on 2011-09-01
> **alphacrucis2 said:**
> Maybe it should be bugged on launchpad as a unity documentation fault.

It's working now.

---

