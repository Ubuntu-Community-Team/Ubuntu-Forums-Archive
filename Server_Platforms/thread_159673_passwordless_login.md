---
title: "passwordless login"
date: 2006-04-13
forum: Server Platforms
---

### Post by ashrack on 2006-04-13
I would require that a user ex.: "Petelin" would be passwordless. So that I wouldnt have to type its password in the login screen.And yes I know about the AUTOMATIC LOGIN option. But thats only a temporary workarround. Because when U log out from a another user and then U want to log back in with the user "Petelin" U still have to type the password.
Dont worry this user will not have any administrative priviliges whatsoever.

Can this be done??

---

### Post by fng on 2006-04-15
In the passwd manpages i found this :
```
You can also use the -d option to delete a user&#8217;s password (make it empty).  
Use caution with this option since it can make an account not require a password at 
all to login, leaving your system open to intruders.
```

so login with Petelin
fire up a terminal
passwd -d

i hope it works

---

### Post by ashrack on 2006-04-15
[QUOTE=fng]In the passwd manpages i found this :
```
You can also use the -d option to delete a user’s password (make it empty).  
Use caution with this option since it can make an account not require a password at 
all to login, leaving your system open to intruders.
```

so login with Petelin
fire up a terminal
passwd -d

i hope it works[/QUOTE]
thank U. will try as soon as I can! 
No wonder I couldnt find such an option I was looking in "man usermod"

---

### Post by Thunderbird750 on 2006-04-16
This will leave you vulnerable to someone logining; changing the password; running crud.  Granted, if you find this happening -probably- the worst that will happen is that user environment will get clobbered.

Do keep in mind that many security exploits require a local login; this gives them one. 

Another approach is to use ssh and private/public keys.  This will allow your application to login w/out a password yet prevent random folks from playing with your id.

---

### Post by Hiroshima on 2006-04-19
I want to login automatically everytime I start my computer, rather than typing my name and password.
My computer is at home, so there shouldn't be any security questions... unless you are refering to security threats from the internet.
(If this should be a new topic, please let me know, and I will re-submit it)

---

### Post by ashrack on 2006-04-19
[QUOTE=Hiroshima]I want to login automatically everytime I start my computer, rather than typing my name and password.
My computer is at home, so there shouldn't be any security questions... unless you are refering to security threats from the internet.
(If this should be a new topic, please let me know, and I will re-submit it)[/QUOTE]
the question to this topics already exist. Do a search...

Anyway I already got U the sollution, here U go:

[http://ubuntuguide.org/#automaticlogingnome](http://ubuntuguide.org/#automaticlogingnome)

---

### Post by Hiroshima on 2006-04-19
Sorry, I'm still learning where to search... this thread was the closest that could see when I searched the forum.

Anyhow, I&#12288;will look up your answer.  Thank you.

---

