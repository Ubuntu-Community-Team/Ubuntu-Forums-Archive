---
title: "How To Setup Fingerprint Authentication (Lenovo Laptop)"
date: 2020-11-21
forum: Security
---

### Post by zamfp on 2020-11-21
Hi there :)

I have a Lenovo laptop (E15) and am trying to set up fingerprint authentication. I need someone to hold my hand setting this up. How do I do this?? When I go into Settings > Users, there is nothing there? Cheers!

---

### Post by EuclideanCoffee on 2020-11-21
You are going to want to install fprint. You may need to do it with the following command in the terminal.

[https://askubuntu.com/questions/511876/how-do-i-install-a-fingerprint-reader-on-lenovo-thinkpad](https://askubuntu.com/questions/511876/how-do-i-install-a-fingerprint-reader-on-lenovo-thinkpad)

Then follow these instructions on where to locate fprint and configure it.

[https://help.gnome.org/users/gnome-help/stable/session-fingerprint.html.en](https://help.gnome.org/users/gnome-help/stable/session-fingerprint.html.en)

---

### Post by zamfp on 2020-11-21
> **EuclideanCoffee said:**
> You are going to want to install fprint. You may need to do it with the following command in the terminal.

[https://askubuntu.com/questions/511876/how-do-i-install-a-fingerprint-reader-on-lenovo-thinkpad](https://askubuntu.com/questions/511876/how-do-i-install-a-fingerprint-reader-on-lenovo-thinkpad)

Then follow these instructions on where to locate fprint and configure it.

[https://help.gnome.org/users/gnome-help/stable/session-fingerprint.html.en](https://help.gnome.org/users/gnome-help/stable/session-fingerprint.html.en)

Hi. Thanks for replying. I already had fprint installed. When I go to users, there is nothing there for fingerprint logon at all. Do you have any ideas? Cheers.

---

### Post by EuclideanCoffee on 2020-11-21
You may need to enable it with this command: sudo pam-auth-update

[https://askubuntu.com/questions/1231185/fingerprint-login-in-20-04](https://askubuntu.com/questions/1231185/fingerprint-login-in-20-04)

---

### Post by zamfp on 2020-11-21
> **EuclideanCoffee said:**
> You may need to enable it with this command: sudo pam-auth-update

[https://askubuntu.com/questions/1231185/fingerprint-login-in-20-04](https://askubuntu.com/questions/1231185/fingerprint-login-in-20-04)

This is frustrating! It still doesn't work I'm afraid :(

---

### Post by EuclideanCoffee on 2020-11-21
Unfortunately I have some more bad news. This does not appear to be an Ubuntu certified machine: [https://certification.ubuntu.com/make/Lenovo?&page=15](https://certification.ubuntu.com/make/Lenovo?&page=15)

If you want to use Linux only and this is a recent purchase, I recommend returning this model and buying one that is certified. You should also be able to buy Lenovo with Ubuntu pre-installed. E15 does not appear as an option: [https://news.lenovo.com/pressroom/press-releases/lenovo-launches-linux-ready-thinkpad-and-thinkstation-pcs-preinstalled-with-ubuntu/](https://news.lenovo.com/pressroom/press-releases/lenovo-launches-linux-ready-thinkpad-and-thinkstation-pcs-preinstalled-with-ubuntu/)

Because this is not certified, it is likely you are using only generic drivers instead of drivers configured for the machine. :(

---

