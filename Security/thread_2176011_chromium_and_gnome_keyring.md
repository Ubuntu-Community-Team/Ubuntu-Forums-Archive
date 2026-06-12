---
title: "chromium and gnome keyring"
date: 2013-09-22
forum: Security
---

### Post by ICanHasNick on 2013-09-22
Hi there,

my Chromium Browser on an Ubuntu 12.4 saves passwords in the Gnome Keyring - this so far is exactly what I want it to do.

Now when I am logged in (as ubuntu user), the keyring server by default doesn't request the master password before it allows chromium to autocomplete 
the login credentials on web pages that require login. This means that every web-page that I visit can be opened instantly if the username-password combination 
is stored in the "login" keyring.

I would rather like the password manager to behave like it does with my ssh logins where it requiers the password every time when (i.e.) xterm 
needs to unlock the necessary key. (I know, this is actually quite the opposite of what most people want)

The documentation to gnome-keyring and seahorse says that you can add new keyrings with new passwords (which I did) to Gnome Keyring. 
Can I somehow persuade Chromium to use this new keyring instead of the "login" keyring and will it help?

Actually all I want to acheive is that no one can access protected web-pages without the a password when I am logged in and for a while not in front of the computer.


thx in advance

---

### Post by ICanHasNick on 2013-10-07
I belive, that I may not clearly described my problem, thus I will try an improved attempt.

The basic question is, how to achieve a secure SSO (single-sign-on) on an Ubuntu (Gnome) system ?

The Gnome Keyring for instance, does cooperate with many applications and processes which is quite usefull.

The only problem is, that the Keyring, once it has been opend doesn't require the master passwort any more as long es the user session lasts.

Now if you walk away from your computer, anyone around (including your wife/husband/children) has access to all your passwords which is a security issue (at best). 

If we take "sudo" as another example for security management, here we either need to enter the master-password every time or it remembers the password for a short time only.

This implementation of the Gnome Keyring makes it particularly difficult for me to use it as the default Password manager. (As well as Firefox's refusal to support it)

At present I use it only for the "non-crucial" password management. Everything important is saved in the Revelation-Password-Manager whose handling is rather cumbersome.

How do you people achieve a secure SSO management on Ubuntu? And please don't tell me you log off each time when you walk away from the computer.

---

### Post by stinkeye on 2013-10-07
What's wrong with using the screenlocker when you step away from the pc. 
Set a low idle time and/or activate manually ...ctrl+alt+l

Any important passwords (bank gmail U1) I keep in keepassx as I use opera as my main web browser.
Keepassx has an autotype feature.

---

### Post by ICanHasNick on 2013-10-09
> **stinkeye said:**
> What's wrong with using the screenlocker when you step away from the pc. 
Set a low idle time and/or activate manually ...ctrl+alt+l


Actually everything is wrong with using the screenlocker

1.)
You're passing the password security check forward to the log-in manager instead to the Keyring. 
If your system has been corrupted, all your passwords are gone as well.

2,)
There might be people with legal access to your user session that should not have access to your other
 passwords (your boss, your admin, your girlfriend). 

I hope that by choosing the last person combined with only little imagination from your side, might perfectly
 demonstrate the possiblity of a devastating impact on your future life if leaving your other passwords entirely 
unprotected. ;)

There should be an option in the Keyring daemon, where you can specify that for each password request 
you have to provide the SSO-password. Unfortunatelly I couldn't find such an option so far. 

Perhaps I just didn't try hard enough?

---

