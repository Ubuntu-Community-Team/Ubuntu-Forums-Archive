---
title: "sshd_config &quot;usepam&quot;, keyboard problems"
date: 2008-08-17
forum: Server Platforms
---

### Post by Poka64 on 2008-08-17
What exactly does "usepam" do?

I'm having som strange problems with ssh keys because when I set "usepam no", the keyboard layout doesn't work anymore in OS X, especially "å ä ö". If I use gnome-terminal, on ubuntu, everything just works as it should do with ssh keys.

This is what I get when I set "usepam yes" in sshd_config running "locale" with the terminal i OS X (Leopard)

```
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=en_US.UTF-8

```

If I use "usepam no" this happens:

```
LANG=
LC_CTYPE="POSIX"
LC_NUMERIC="POSIX"
LC_TIME="POSIX"
LC_COLLATE="POSIX"
LC_MONETARY="POSIX"
LC_MESSAGES="POSIX"
LC_PAPER="POSIX"
LC_NAME="POSIX"
LC_ADDRESS="POSIX"
LC_TELEPHONE="POSIX"
LC_MEASUREMENT="POSIX"
LC_IDENTIFICATION="POSIX"
LC_ALL=

```

---

### Post by HalPomeranz on 2008-08-18
"UsePAM" tells the SSH server to obey the system's default PAM (Pluggable Authentication Modules) configuration.  PAM is a mechanism in Unix that makes it easier for developers and system administrators to insert security code into the login process.  For example, if you wanted to use LDAP for authentication, you can enable that by changing the system's PAM configuration to use the pam_ldap module instead of the normal password authentication mechanisms.  PAM is also used to do things like forcing good passwords (pam_cracklib), expiring passwords and forcing users to pick new ones (pam_unix), and locking out accounts after a certain number of failures (pam_tally).

In this case, it appears that there's a PAM module that responsible for setting your language locale settings.  When you have PAM disabled in sshd ("UsePAM no") then you're getting the POSIX locale by default, but when you have it turned on it appears that your terminal app in Leopard is asserting that you're in the "en_US" (US English) language locale.  It's not surprising that the special Swedish characters are not being rendered properly here.

I think there are two possible fixes here.  The first would be to somehow make your Mac terminal application believe that it's supposed to be using the Swedish language locale.  I'm not sure how to do this (don't own a Mac), but my theory is that once you get this right, it should be propagated to the Ubunutu box when you log in with "UsePAM yes".  The other alternative would be to just explicitly set the various LC_* variables whenever you log into the Ubuntu box.  You could do this via your ~/.profile or ~/.bashrc file.

---

### Post by Poka64 on 2008-08-19
Thank you so much for that information, now I understand what this PAM stands for at least :)

---

