---
title: "Why Is Gnome Now Prompting for Creation of a &quot;Default Keyring&quot;??"
date: 2019-01-17
forum: Ubuntu Development Version
---

### Post by lostmoonofsaturn on 2019-01-17
Gnome in Disco is now prompting me with a dialogue to create a password for a "Default Keyring" whenever I attempt the initial setup of an account that requires authentication.  E.g., one of the account offered in Online Accounts, Evolution, etc.

This is very annoying behavior I have not seen in Gnome for a very long time. Is this an intentional change?

---

### Post by VMC on 2019-01-17
This "problem" has been around for ages. I've tried various fixes. Some work better than others. I personally don't buy into its reasoning. Here's the best yet topic on how to get round the dreaded keyring nonsense:
[https://ubuntuforums.org/showthread.php?t=1655397&p=10301640#post10301640](https://ubuntuforums.org/showthread.php?t=1655397&p=10301640#post10301640)

Ironically Lubuntu doesn't have any issues with keyring and chrome. I don't use any other authentication keyring required programs

---

### Post by lostmoonofsaturn on 2019-01-18
> **VMC said:**
> This "problem" has been around for ages.

Yes. It's been a very long time since I've come across it, though.  Perhaps distributions have been doing something to get it out of the way but some recent change has resurfaced the thing.  I see it in Disco, update Fedora 29, and Debian Testing.

What's doubly annoying is that sometimes I see a prompt to *create* a keyring password and sometimes I see a prompt to *provide* the keyring password, which, of course, does not exist.

Most users will not know a password keyring exists, why it exists, or what to do with it.  Unless a user intervenes, the password keyring's own password should default to the login password and its operation kept invisible from users.

It's reminiscent of the annoying things that used to happen with KDE and its KWalletManager.

---

### Post by mc4man on 2019-01-19
I don't see this at all. Just setup an online account (Google), only had to one time provide the google password. Nothing about a keyring at all. 
Are you auto logging in?

edit: as screen shows my login pass is being used for goa

---

### Post by VMC on 2019-01-22
I realized that I only use Chrome and not any other Gnome Keyring related program. Therefore all I needed to do is change "/usr/share/applications/google-chrome.desktop: Exec=/usr/bin/google-chrome-stable %U --password-store=basic"

---

