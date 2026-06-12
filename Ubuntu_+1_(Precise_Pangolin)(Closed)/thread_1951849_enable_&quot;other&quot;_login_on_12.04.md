---
title: "enable &quot;other&quot; login on 12.04"
date: 2012-04-03
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by linux.girl on 2012-04-03
Hi,

I need to enable the "other" login option on 12.04 Beta 2 - I use centrify express and without the "other" option I cant login (it gives me the option of only local user or guest).

I am trying the 64 bit version.

Does anyone have any idea how to do it?

Thanks in advance,

linux.girl

---

### Post by Thylex on 2012-04-04
Similar problem for us. As part of the post-install one of the techs will log in and setup a few things. After that the login screen only allows either that user or a "guest session" to log in. How do we allow login for other remote (NIS/AD) accounts?

---

### Post by NHclimber on 2012-04-04
You'll want to follow this bug report [https://bugs.launchpad.net/lightdm/+bug/944041](https://bugs.launchpad.net/lightdm/+bug/944041)

You may be able to get the "Other..." login by following the configuration in comment #3.

---

### Post by linux.girl on 2012-04-05
Thanks for the tip :p I will try it.

linux.girl

---

### Post by Thylex on 2012-04-10
After reading up on the VERY limited documentation for Unity greeter and the AccountsService it relies on it seems that the default login screen is only aware of accounts that are usable with usermod/useradd/userdel ie fully local accounts. This is totally useless for us so we have decided to go back to GDM and also to install the GNOME session fallback packages.

So our 400 workstations will be un-broken by doing:
```

apt-get install gnome-session-fallback
apt-get install gdm

shutdown -r now

```

---

### Post by grahammechanical on 2012-04-10
@Thylex

If your employer has a service contract with Canonical then they might be able to fix this issue for your employer.

---

### Post by linux.girl on 2012-04-10
I agree this is a big problem. And I dont understand the logic behind it, after all, this worked really nice on Oneiric, why change it now?

It must be a bug they are overlooking, I cant believe that the system is really designed to be like this - why change it from how it was on 11.10?

I hope they fix this for everyone....

---

### Post by cariboo on 2012-04-10
Has anyone actually found, or created a bug report about this problem, if not it should be done A.S.A.P.

---

### Post by xebian on 2012-04-10
> **cariboo907 said:**
> Has anyone actually found, or created a bug report about this problem, if not it should be done A.S.A.P.

If you read the whole thread, it's there on the 3rd post.

---

### Post by NHclimber on 2012-04-10
This kind of stuff will continue to happen for a while as LightDM matures. Just read this bug report [https://bugs.launchpad.net/lightdm/+bug/674774](https://bugs.launchpad.net/lightdm/+bug/674774) to realize that AD/NIS wasn't exactly 'planned in' from the beginning.

By the time LightDM does everything that gdm does, it won't be "lightweight" anymore.

---

### Post by jbicha on 2012-04-10
I believe lightdm does more than gdm does. LightDM is definitely more themable.

---

### Post by xebian on 2012-04-10
> **jbicha said:**
> I believe lightdm does more than gdm does. LightDM is definitely more themable.

Who cares about 'themability' when 'functionality' is not there?):P

---

### Post by Thylex on 2012-04-12
> **xebian said:**
> Who cares about 'themability' when 'functionality' is not there?):P
+1
Who cares how it looks if you can't log in?

Edit:
To be fair though, its not light DM thats the issue, its the UnityGreeter and the AccountsService thats the problem

---

### Post by NHclimber on 2012-04-12
@Thylex,

Just to clarify your situation.

On a test workstation, you edited /etc/lightdm/lightdm.conf to read:
```
[SeatDefaults]
user-session=ubuntu
greeter-session=unity-greeter
allow-guest=false
greeter-hide-users=true
```

So that now the workstation login looks the attached login screen (sorry about the dual-monitor -- please ignore).

You enter an NIS user and password and what happens?  Authentication failure?
Or are you just referring to the hassle of the non-default lightdm.conf on *n* workstations?

---

### Post by Thylex on 2012-04-17
We didn't bother editing to hide guest session, but what happens is:
1. Enter username and password in "Other user" box. Screen flashes and resets but doesnt log in.
2. Press up-arrow to go back to what used to be the "Other user" box, now it has ny name in it, enter password and it logs in.
3. I do some post-install tasks to prep the host for end-user and log out.
4. The greeter screen now has 2 choices. My username or guest. No choice for the end-user to enter his username and log in.

The workaround we found was to switch to a text-console, log in there as the end-user, log out, switch back to Unity and reset the greeter. It would now have the end-user in one box and guest in the other. So apparently it remembers the last user logged in.

---

