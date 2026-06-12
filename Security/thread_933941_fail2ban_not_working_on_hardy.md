---
title: "fail2ban not working on hardy"
date: 2008-09-30
forum: Security
---

### Post by Excalibre on 2008-09-30
I have fail2ban set up to limit the number of attempted intrusions on my SSH server. I'm not really worried about this, because I use private-key authentication, and my logs show no one's guessed my username anyway, but I'm concerned because fail2ban is clearly not working.

I installed in from the repositories and basically started it as is -- I didn't modify the config file at all, because it looked adequate as far as I could tell. But it's clearly not doing anything -- it should lock out anyone who makes three login attempts in ten minutes, but it clearly doesn't. Looking in auth.log I see dozens of attempts from one IP address in a row. What am I doing wrong here? Why isn't fail2ban banning them?

---

### Post by cariboo on 2008-09-30
I found the same problem using the default config. I started using denyhosts instead, and it works the way it should.

Jim

---

### Post by sot3 on 2008-10-19
I just discovered the same thing, and apparently it's a known bug in fail2ban.  It won't start unless you create its working directory:
```
sudo mkdir /var/run/fail2ban
```
I've been running both denyhosts and fail2ban and they seem to play well together.

---

### Post by wattaman on 2010-04-12
> **sot3 said:**
> I just discovered the same thing, and apparently it's a known bug in fail2ban.  It won't start unless you create its working directory:
```
sudo mkdir /var/run/fail2ban
```
I've been running both denyhosts and fail2ban and they seem to play well together.

Almost opened a new thread asking the same... good luck I've searched before.
Thank for the intel. Now I've got a fail2ban running - funny thing (stupid, actually): I have it installed for 3 month but just now it came to my mind to check its status and logs ](*,)

---

### Post by wattaman on 2010-04-13
ok, one question: why the /var/run/fail2ban I've created in order to start fail2ban has dissapeared after reboot?
I'm affraid it will do the same in the future and, again, f2b will not run after restart.

---

### Post by wattaman on 2010-04-14
OK, I can confirm this: after reboot, the /var/run/fail2ban directory is missing again.
How can this be fixed?  :confused:

---

