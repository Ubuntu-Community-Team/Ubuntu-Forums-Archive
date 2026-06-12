---
title: "Ubuntu privacy"
date: 2010-01-17
forum: Security
---

### Post by one-up on 2010-01-17
Hi everyone,
I am going to install ubuntu (64-bit 9.10 karmic) on a public computer, and because I don't want people to go through other people's history, I want to disable every single history/recent documents list, logs etcetera.
I have managed to disable the recent documents list in the places menu and the history in firefox, but there is probably still a lot of private data being stored somewhere.
Does anyone know of a method to disable all of it?
Thanks

---

### Post by adam814 on 2010-01-18
Will these people have separate user accounts?  If so just make sure files in the home directories aren't group-readable

For example:
```
sudo chmod 700 /home/*
```

---

### Post by The Cog on 2010-01-18
> **adam814 said:**
> Will these people have separate user accounts?  If so just make sure files in the home directories aren't group-readable

For example:
```
sudo chmod -R 600 /home
```

I think that would leave the users unable to enter their own directories (directory not executable). I would think that just setting all the home directories to being owner accessible only would do the trick:
```
sudo chmod 700 /home/*
```

If the users don't have their own logins, I think there is something called a "kiosk mode" that may do what you want but I don't know the details.

---

### Post by one-up on 2010-01-18
Thanks your replies, but I don't want people to login(no seperate accounts) and users need full permissions, so no kiosk mode either.

---

### Post by koenn on 2010-01-18
> **one-up said:**
> Thanks your replies, but I don't want people to login(no seperate accounts) and users need full permissions, so no kiosk mode either.

set up a mechanism that wipes the user and replaces it with the content of a known good 'default' home, or rsync the user home against that default.
Be careful that the default can't be modified by users, but that the resulting copy has the appropriate permissions for users. This means you may also have to chmod and chown them. 

There are scripts in /etc/gdm/PostSession/ and /etc/gdm/PreSession/ where you can add the relevant commands. These scripts run as root just before the user logs on and after  logoff (i.e. before the next user can log on)

---

### Post by FuturePilot on 2010-01-18
> **The Cog said:**
> I think that would leave the users unable to enter their own directories (directory not executable). I would think that just setting all the home directories to being owner accessible only would do the trick:
```
sudo chmod 700 /home/*
```


You don't even need to do that. If the top level /home/$USER is 700 it doesn't matter what the permissions are on anything below it.

---

### Post by The Cog on 2010-01-18
> **FuturePilot said:**
> You don't even need to do that. If the top level /home/$USER is 700 it doesn't matter what the permissions are on anything below it.

That's what **sudo chmod 700 /home/*** does - it sets all the /home/$USER to 700.

---

### Post by The Cog on 2010-01-18
> **koenn said:**
> There are scripts in /etc/gdm/PostSession/ and /etc/gdm/PreSession/ where you can add the relevant commands. These scripts run as root just before the user logs on and after  logoff (i.e. before the next user can log on)

That's very interesting.
Maybe have the pre-session script delete all the user's home contents and then restore clean contents from a tar file.

---

### Post by FuturePilot on 2010-01-18
> **The Cog said:**
> That's what **sudo chmod 700 /home/*** does - it sets all the /home/$USER to 700.

Oh whoops, read too fast. :oops:
Must have still been half asleep.

---

### Post by koenn on 2010-01-18
> **The Cog said:**
> That's very interesting.
Maybe have the pre-session script delete all the user's home contents and then restore clean contents from a tar file.
yep, something like that

---

