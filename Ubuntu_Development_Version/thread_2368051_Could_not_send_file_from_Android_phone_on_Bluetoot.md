---
title: "Could not send file from Android phone on Bluetooth"
date: 2017-08-06
forum: Ubuntu Development Version
---

### Post by kagashe on 2017-08-06
Hi,

I have downloaded the Daily iso of Ubuntu 17.10 mainly to try Wayland session on my Laptop Lenovo G5045. It is working fine.

On any new Ubuntu Version I am checking Bluetooth File Transfer from/to my Android Phone. I could not send file from Phone to the Laptop and vice versa. I have paired the device and it is connected.

In previous Ubuntu versions I had to open Personal File Sharing and put the check mark for receive files over Bluetooth. I have done the same in Ubuntu 17.10 as well.

Kamalakar

---

### Post by MyMurry on 2017-08-06
I have the same problem. See this bug report:

[https://bugs.launchpad.net/ubuntu/+source/gnome-user-share/+bug/1681956](https://bugs.launchpad.net/ubuntu/+source/gnome-user-share/+bug/1681956)

My workaround: [https://bugs.launchpad.net/ubuntu/+source/gnome-user-share/+bug/1681956/comments/4](https://bugs.launchpad.net/ubuntu/+source/gnome-user-share/+bug/1681956/comments/4)

Kind Regards,

Norbert

---

### Post by kagashe on 2017-08-06
> **MyMurry said:**
> I have the same problem. See this bug report:

[https://bugs.launchpad.net/ubuntu/+source/gnome-user-share/+bug/1681956](https://bugs.launchpad.net/ubuntu/+source/gnome-user-share/+bug/1681956)

My workaround: [https://bugs.launchpad.net/ubuntu/+source/gnome-user-share/+bug/1681956/comments/4](https://bugs.launchpad.net/ubuntu/+source/gnome-user-share/+bug/1681956/comments/4)

Kind Regards,

Norbert
It works thanks.

Kamalakar

---

### Post by MyMurry on 2017-08-06
Hello Kamalakar,

could you mark the bug as "this affect me too", please.

---

### Post by kagashe on 2017-08-07
> **MyMurry said:**
> Hello Kamalakar,

could you mark the bug as "this affect me too", please.

Done.

---

### Post by kagashe on 2017-08-07
> **MyMurry said:**
> I have the same problem. See this bug report:

[https://bugs.launchpad.net/ubuntu/+source/gnome-user-share/+bug/1681956](https://bugs.launchpad.net/ubuntu/+source/gnome-user-share/+bug/1681956)

My workaround: [https://bugs.launchpad.net/ubuntu/+source/gnome-user-share/+bug/1681956/comments/4](https://bugs.launchpad.net/ubuntu/+source/gnome-user-share/+bug/1681956/comments/4)

Kind Regards,

Norbert
Your wokaround  worked yesterday but not working today.

Kamalakar

---

### Post by MyMurry on 2017-08-07
Hello Kamalakar,

it still works for me. Do have the correct settings at gnome-file-share-properties?

Norbert

---

### Post by kagashe on 2017-08-08
Do I need to execute the following command on every boot?
```
systemctl --user start obex
systemctl --user enable obex
/usr/lib/gnome-user-share/gnome-user-share-obexpush &
```

Kamalakar

---

### Post by MyMurry on 2017-08-08
Hello Kamalakar,

yes after every boot. To prevent this you cloud do this:

sudo systemctl --global enable obex

gnome-session-properties

Add a new entry:
Name: gnome-user-share-obexpush
Command: /usr/lib/gnome-user-share/gnome-user-share-obexpush
save

Enable the new entry

Regards

Norbert

---

### Post by kagashe on 2017-08-08
> **MyMurry said:**
> Hello Kamalakar,

yes after every boot. To prevent this you cloud do this:

sudo systemctl --global enable obex

gnome-session-properties

Add a new entry:
Name: gnome-user-share-obexpush
Command: /usr/lib/gnome-user-share/gnome-user-share-obexpush
save

Enable the new entry

Regards

Norbert
Done, thanks.

Kamalakar

---

### Post by lotfy_it on 2018-01-30
Many thanks.
Worked for me

---

### Post by cariboo on 2018-01-30
Thread Closed.

---

