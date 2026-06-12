---
title: "Setting Up a Public ally Accessible Computer"
date: 2011-01-13
forum: Security
---

### Post by igb on 2011-01-13
Our local community wants to provide broadband access for people who don't own a computer. I have been given the task of setting this up and I am going to use Ubuntu. Internet access will be via a usb dongle to a T-Mobile 3.5g network.

Initially we are intending to limit access to just Internet browsing. Most users will probably be older people, rather than teenage hackers.

Does anyone have any tips, or can point me to any tutorials for configuring/securing a default Ubuntu install for this sort of use.

Ian.

---

### Post by bodhi.zazen on 2011-01-13
Google search "kiosk"

Personally I would advise you use Fedora with the xguest package.

With xguest you get basically a kiosk mode + the account has no password, you just auto log-in, and it is locked down by selinux.

Doubt you could easily get more secure then that with so little effort (you need to install xguest) ;)

When the guest account logs off, all settings are removed and the next time you log in the desktop, firefox, etc are nice and fresh / clean.

---

### Post by igb on 2011-01-13
Thanks I'll have a look at that. I haven't used fedora for a long time. Will the guest's network connection be automatically set up on login?

---

### Post by bodhi.zazen on 2011-01-13
> **igb said:**
> Thanks I'll have a look at that. I haven't used fedora for a long time. Will the guest's network connection be automatically set up on login?

Should be, it "works for me" , I use the kiosk for friends and family.

---

