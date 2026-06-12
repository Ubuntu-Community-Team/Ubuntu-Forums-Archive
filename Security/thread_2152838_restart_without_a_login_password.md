---
title: "restart without a login password"
date: 2013-06-09
forum: Security
---

### Post by Neill_R on 2013-06-09
Hello

I am able to restart my ubuntu 12.04 server (+ Ubuntu-Desktop installed) without reentering my password. Has anyone else experience similar? There is one import fact I should add that I am running Centrify's CentrifyDC package this enable the joining of an Active directory domain. I am connected and logged in when I do a restart. The desktop is unity.
On the last two restarts this has happen so it is repeatable and has happen before several times. But now i feel that this should be highlighted to the community.

I will now log out and log in as a local machine use and see if the same is true.

[Edit]

I find that the choice of a local user requires the entry of a password after a restart. I therefore expect the same of an Active Directory Domain user. But find that it is not. I will raise this with Centrify.

Notes

After login out of the AD Domain user and logging in tot the local user I found that on restart the old pasword for the Active Direcory Domain user nolonger worked until that is i logged in as the local user again and did a

ssh [email]AciveDirectory.DomainUser@Domain.co.uk[/email] 
password : Existing password


After that the login worked at the login prompt screen.

---

### Post by Cheesemill on 2013-06-09
I'm not sure what you're getting at. When you are using a DE then anyone can restart the machine without entering their password as long as no-one else is logged in.

---

### Post by Neill_R on 2013-06-09
Yes the machine starts and the desktop environment starts. The first thing that should happen is that the login screen should appear. If what you are saying is true I should be able to logout as the AD user and login as a local user and restart and the login screen will NOT appear. I will Try it once again to see if this is so.

---

### Post by Cheesemill on 2013-06-09
So you mean you can restart and it will automatically log you in again without a password?

Your original post just made it seem like you could restart without a password, which is the normal behaviour.

---

### Post by Neill_R on 2013-06-09
When I did the above I was asked for a password to log in to the DE. This is what I would consider normal behaviour. if I logging as the active directory user it appears to go to the desktop logged in as I was before the restart. If ones was to accidentally restart instead of shutdown and walk away from the PC then there is a security problem.

I just repeated the restart for an active directory user and I WAS asked for my password . So this problem is not always repeatable.

[URL="http://community.centrify.com/t5/DirectControl-Express-for-UNIX/Straight-to-Desktop-without-login-screen/td-p/11920"]
[http://community.centrify.com/t5/DirectControl-Express-for-UNIX/Straight-to-Desktop-without-login-screen/td-p/11920](http://community.centrify.com/t5/DirectControl-Express-for-UNIX/Straight-to-Desktop-without-login-screen/td-p/11920) [/URL]

---

### Post by Neill_R on 2013-06-09
I tried a restart again and this time it DID NOT ask for user-name or password but took the system straight to the desktop login.

---

### Post by cariboo on 2013-06-09
> **Neill_R said:**
> I tried a restart again and this time it DID NOT ask for user-name or password but took the system straight to the desktop login.

That is normal behaviour for the desktop version. I'd suggest removing lightdm, and starting the desktop only when you need it, by typing:

```
startx
```

at the prompt, then when you don't need the gui, log out. When running from the command line, you need to enter a password when you want to shutdown or reboot the system.

---

### Post by Neill_R on 2013-06-10
Hi thank you for you input on this, however I believe your answer is misguided. It is normal for the  restart of the computer to recycle via the CMOS screen the Grub screen and then the login screen where a user name must be chosen and the password entered. It is only when I use an active directory user name that the login in screen is bypassed. 


Point to not e the local user I am using is the one created to install the Ubuntu OS and in the /ect/centifydc/user.ignore its name is included so that the AD is not searched.

---

