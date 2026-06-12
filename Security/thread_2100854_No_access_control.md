---
title: "No access control?"
date: 2013-01-03
forum: Security
---

### Post by utopiadaniele on 2013-01-03
Hello everybody,
I am using ubuntu 12.04.1 LTS at home and I am the only user and admin of this machine. 
I was very surprised to discover that my 17-y.o. daughter, without using any pwd, logged into the system.

It was enough, while in locked screen mode, to click on "switch user", then to click on "log in" without entering any pwd, and the profile is open to anybody.

Any idea how to fix this?

Thanks a lot, Daniele (from Italy)

---

### Post by Hungry Man on 2013-01-03
I assume you mean she logged into the guest account?

---

### Post by utopiadaniele on 2013-01-03
Of course not: to my account! not to the guest one...

---

### Post by Hungry Man on 2013-01-03
How odd. Can you recreate that? You can just open the system and log in?

---

### Post by akshay.bhardwaj on 2013-01-03
I guess you have enabled automatic login in User Accounts. Try to get to System Settings>User Accounts and see that automatic login is enabled or not.

---

### Post by utopiadaniele on 2013-01-03
You were right, automatic login was in fact on. 
BUT, even switching it to OFF....... I can log in anyway!!!

I will explain it as I do it (and in fact recreate it!).

Lock screen.

If I try to log in with no pwd --> no way, still locked.

But if I "switch user", and then "log in" (without entering any pwd!!) --> I log in!!!!

weird behaviour...

---

### Post by utopiadaniele on 2013-01-03
Let me also add that there is no "guest" account: just mine (administrator profile).

Thanks, Daniele

---

### Post by Ms. Daisy on 2013-01-03
> **utopiadaniele said:**
> Let me also add that there is no "guest" account: just mine (administrator profile).

Thanks, Daniele

Ubuntu comes with a guest account by default. Unless you specifically removed it,when you change user accounts you are changing to the guest account.

---

### Post by utopiadaniele on 2013-01-03
Great, that is new to me, thanks.

I will try to insert a (new) guest account and then verify if I can switch my profile back to admin with pwd. 
If so, that will be ok for my profile access, but still my machine can be used by my 17 yo daughter... :-) how to lock it and that's it?

---

### Post by utopiadaniele on 2013-01-03
Did so. 
News.

I tried to set the "guest account" with a pwd, that was actually considered by the system too weak and would not accept it. 
Then I tried with a stronger pwd, and in fact guest account worked fine: it would not log in without its pwd.

So I thought that maybe the system was considering my admin pwd too weak, and I tried to change it. 
First, I set the admin access as "no pwd" at all. It actually worked, it would access after locking the screen without even prompting for a pwd. 
But when I secondly tried to change it to a stronger one, it is now asking for an "actual pwd" that is not recognised anymore (nor blank nor the previous one). So I am stuck again.

I am coming to the conclusion that my pwd was (considered) too weak, and therefore it was maybe not recognized as a pwd by the system, whoch would log in without it.

I am trying now to switch down and restart, and hope that it accepts the old one, or the blank pwd. 

In any case, it looks like a small bug.

Thanks, Daniele

---

### Post by utopiadaniele on 2013-01-03
:popcorn: I was wrong, and I found it's no bug. Just I needed to check "Users and Groups" and not "User accounts". Under the "password" section one may choose whether to ask for a pwd at login or not.

TOO EASY!!!!

Of course now it works properly. 
I have removed the "guest" account and the admin is correctly logging in ONLY AFTER its proper password is inserted.

---

### Post by cariboo on 2013-01-03
You can disable the guest account in lightdm using the following command:

```
sudo /usr/lib/lightdm/lightdm-set-defaults --allow-guest false
```

or you can disable by editing /etc/light/lightdm.conf. Open lightdm with a text editor:

```
sudo gedit /etc/lightdm/lightdm.conf
```

then setting:

```
allow-guest=false
```

in the [SeatDefaults] section.

For more info on setting up lightdm, have a look at:

[https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

---

### Post by utopiadaniele on 2013-01-04
Thanks a lot, I am reading through the LightDM pages and it's indeed interesting. 

Thanks, Daniele

---

