---
title: "How to setup Firefox to prevent from downloading anything"
date: 2009-06-14
forum: Security
---

### Post by SoberWarlock on 2009-06-14
I applied this to any Operating System because I would like to know how to setup Firefox to prevent from downloading any sort of files including a simple picture. I want to block of all downloading ability. I have people who come in use the computer and download programs they should not be downloading and I want to stop that.

I would like to know how to do this for:

*Windows XP 32bit*
*Ubuntu*

---

### Post by Sir Jasper on 2009-06-14
Hi,

in 'buntu you could use Firestater to set up the iptables firewall to block http and https.

My regards

Addendum:

On second thoughts; perhaps then noone could use it at all. Use your warlock power?

Just to clarify - it's OK for visitors to use FF but not to downlod?

---

### Post by lovinglinux on 2009-06-14
> **Sir Jasper said:**
> Hi,

in 'buntu you could use Firestater to set up the iptables firewall to block http and https.

My regards

Addendum:

On second thoughts; perhaps then noone could use it at all. Use your warlock power?

Just to clarify - it's OK for visitors to use FF but not to downlod?

That doesn't solve the OP problem, because unless you block the entire Internet it will be able to download stuff and if you block the Internet, then Firefox becomes unusable. Besides, this is a Linux only approach.

To prevent Firefox from downloading files, use the [PublicFox](https://addons.mozilla.org/en-US/firefox/addon/3911) extension. It allows you to determine which file types can and cannot be downloaded. Whenever the user tries to download a blocked file type, it will prompt for the master password. If the user doesn't have the password, the download will fail.

---

### Post by Sir Jasper on 2009-06-15
lovinglinux,

You've educated me and helped SoberWarlock.

Much thanks

---

### Post by SoberWarlock on 2009-06-15
Sir Jasper that is too much to block I needed something to prevent firefox from downloading any sort of file/exention. lovinglinux suggested PublicFox which is exactly what I needed. Thanks You

---

