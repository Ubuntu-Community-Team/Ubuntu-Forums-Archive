---
title: "Incorrect Username And/Or Password"
date: 2009-01-08
forum: Virtualisation
---

### Post by mathman on 2009-01-08
Hi all,

I have downloaded the Ubuntu 8.10 distro as a VMWare virtual appliance. I downloaded it from [here]("http://www.vmware.com/appliances/directory/54943").

This page claims that username = user, and password = user.

When I run it in the VMWare player (on Win XP Home), I am prompted for the username and password. When I key these in, I get the error message "Incorrect username or password. Letters must be typed in the correct case" (Caps-Lock is not on).

So, the stated values of the username and password are incorrect. 

Can someone please fill me in on what is the correct username and password for Ubuntu 8.10 ? 

Thanks and regards,
Andrew Fortune,
Melbourne,
Australia

---

### Post by bodhi.zazen on 2009-01-08
> **mathman said:**
> Hi all,

I have downloaded the Ubuntu 8.10 distro as a VMWare virtual appliance. I downloaded it from [here]("http://www.vmware.com/appliances/directory/54943").

This page claims that username = user, and password = user.

When I run it in the VMWare player (on Win XP Home), I am prompted for the username and password. When I key these in, I get the error message "Incorrect username or password. Letters must be typed in the correct case" (Caps-Lock is not on).

So, the stated values of the username and password are incorrect. 

Can someone please fill me in on what is the correct username and password for Ubuntu 8.10 ? 

Thanks and regards,
Andrew Fortune,
Melbourne,
Australia

Who knows you would need to ask whoever made the appliance.

What you can do is boot to recovery mode. This will be command line only but you will be root.

List your user(s) with

```
ls /home
```

Set a new password then with

```
passwd user
```

In that second command change "user" to the name of the account you with to set a new password with.

Then reboot.

---

### Post by mathman on 2009-01-09
Thanks a million ! ... worked like a charm :)

---

