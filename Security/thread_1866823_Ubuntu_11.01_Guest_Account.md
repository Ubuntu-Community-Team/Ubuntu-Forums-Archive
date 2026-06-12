---
title: "Ubuntu 11.01 Guest Account?"
date: 2011-10-22
forum: Security
---

### Post by h3trick on 2011-10-22
When you first start Ubuntu 11.01, there is a guest login option.....
How would I go about completely removing this option altogether. I tried using the 
sudo apt-get remove gdm-guest-session

but it didn't work. Any ideas?

---

### Post by lovbuntu on 2011-10-22
> **h3trick said:**
> When you first start Ubuntu 11.01, there is a guest login option.....
How would I go about completely removing this option altogether. I tried using the 
sudo apt-get remove gdm-guest-session

but it didn't work. Any ideas?

Hi! You can remove the guess session from the login screen by doing the following:

[PHP]sudo nano /etc/lightdm/lightdm.conf[/PHP]Then add: [PHP]allow-guest=false[/PHP] at the bottom.

You should now have:

[PHP][SeatDefaults]
greeter-session=unity-greeter
user-session=ubuntu
allow-guest=false[/PHP]In your [PHP]/etc/lightdm/lightdm.conf[/PHP]

---

### Post by h3trick on 2011-10-22
> **lovbuntu said:**
> Hi! You can remove the guess session from the login screen by doing the following:

[PHP]sudo nano /etc/lightdm/lightdm.conf[/PHP]Then add: [PHP]allow-guest=false[/PHP] at the bottom.

You should now have:

[PHP][SeatDefaults]
greeter-session=unity-greeter
user-session=ubuntu
allow-guest=false[/PHP]In your [PHP]/etc/lightdm/lightdm.conf[/PHP]

Did that, unfortunately when you start the computer the guest option is still shown....
Any other ideas?

---

### Post by lovbuntu on 2011-10-22
> **h3trick said:**
> Did that, unfortunately when you start the computer the guest option is still shown....
Any other ideas?

Hmm. That is strange, i'm 99.9% sure that should have worked. Are you sure that you followed those steps correctly?

---

### Post by cariboo on 2011-10-22
I made the same modification to /etc/lightdm/lightdm.conf:

```
cat /etc/lightdm/lightdm.conf

[SeatDefaults]
greeter-session=unity-greeter
user-session=ubuntu
allow-guest=false
```

See the screenshot to see what my lgoin screen looks like.

---

