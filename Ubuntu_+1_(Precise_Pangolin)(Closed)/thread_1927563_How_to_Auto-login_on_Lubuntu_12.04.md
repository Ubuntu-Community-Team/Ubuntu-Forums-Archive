---
title: "How to Auto-login on Lubuntu 12.04?"
date: 2012-02-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by SteveDee on 2012-02-18
What do I have to edit to auto-login on Lubuntu 12.04 Alpha?

I tried the usual way: edit /etc/xdg/lubuntu/lxdm/lxdm.conf and set:-
autologin=steve

Then I tried editing: /etc/lightdm/lightdm.conf and added:-
default-user=steve

...but no joy either way, so how is it done?

---

### Post by linuxnas on 2012-02-19
edit this 

/etc/lxdm/default.conf

---

### Post by SteveDee on 2012-02-19
> **linuxnas said:**
> edit this 

/etc/lxdm/default.conf

Thanks for your suggestion. Unfortunately this does not work.

Closer examination of the file system shows that these files are linked:-

/etc/lxdm/default.conf >link to> /etc/alternatives/lxdm.conf >link to> /etc/xdg/lubuntu/lxdm/lxdm.conf

I also tried running:-
```

sudo update-alternatives --config  lxdm.conf

```
...but as there is only one option (i.e. no alternatives) there is nothing to configure.

---

### Post by hkarn on 2012-03-30
Tried this too it doesn't work.

Is there another way?

---

### Post by ventrical on 2012-03-30
systemtools>users&groups>changepassword

You have to actually put in a new password and the login screen still comes up after you tic off 'don't ask for password at logon. All you have to do is click <logon>. Thats about as close as I can get to auto-logon.

---

### Post by chriswyatt on 2012-04-04
Are you using LightDM? You can create/edit /etc/lightdm/lightdm.conf with these contents:

```
[SeatDefaults]
autologin-user=<your_username>
autologin-user-timeout=0
user-session=Lubuntu
greeter-session=lightdm-gtk-greeter
```

I'm not sure if this is the correct way to do it, but it appears to work nonetheless.

---

### Post by SteveDee on 2012-04-20
> **chriswyatt said:**
> ...I'm not sure if this is the correct way...

Thanks Chris, this works!

---

