---
title: "Possible to disable Authentication?"
date: 2009-11-25
forum: Security
---

### Post by donkeyman1 on 2009-11-25
I've done several searches but not found a way - can I disable Authentication in Ubuntu - for when I install programs etc. - login is automatic, but this Authentication is as bad as User Account Control (UAC) in Windows Vista!

Sorry if this is a stupid question and if it's been asked before.

---

### Post by scorp123 on 2009-11-25
> **donkeyman1 said:**
> for when I install programs etc. I strongly recommend against totally disabling it. **[COLOR="Red"]You can easily hose your system.[/COLOR]**

What I'd recommend instead is that you add yourself to the "**/etc/sudoers**" file so that you can install stuff whenever you need to without being bothered?

[http://ubuntuforums.org/showthread.php?p=8330156#post8330156](http://ubuntuforums.org/showthread.php?p=8330156#post8330156)

So in your case you'd execute "**sudo visudo**" and then add a line saying e.g.

```
# donkey-user may pull updates from the repos when he wishes
donkey-user ALL=NOPASSWD: /usr/bin/apt-get update

# donkey-user may install things whenever he wishes
donkey-user ALL=NOPASSWD: /usr/bin/apt-get install *

```

After that when you execute e.g. **"sudo apt-get install nameOfProgramHere"** then it should not bother you with passwords anymore.

But again ... I advise you against ***totally*** disabling this. Work *with* the security mechanisms ... not *against* them, OK?

---

### Post by cariboo on 2009-11-25
See this [document]("https://help.ubuntu.com/community/RootSudo") about the Ubuntu security policy.

---

### Post by pdxmusl on 2010-11-08
I would agree with the original poster. If there isn't a way to disable this screen, i will be moving to another distribution. This thing is a serious pain. As far as security goes, the only difference between having a root user be the administrator and having a non-root user being the administrator is that the "administrators" login name is harder to guess. Otherwise there isn't any difference. Someone has to have permissions to set-up the system. Or be granted permissions somehow. Once a hacker figures out which user you are using for administrative purposes, the security risk is the same. The only thing this authentication window is is an inconvenience for people attempting to do legitimate things to the system. If I cared about protecting my system from the root user I can disable root on my own. And achieve the same "increase" in security ubuntu experiences. I don't need ubuntu to Microsoft linux for me with implementing there UAC concepts. (or vista implementing ubutus.. whichever :P).

---

### Post by tgm4883 on 2010-11-08
> **pdxmusl said:**
> I would agree with the original poster. If there isn't a way to disable this screen, i will be moving to another distribution. This thing is a serious pain. As far as security goes, the only difference between having a root user be the administrator and having a non-root user being the administrator is that the "administrators" login name is harder to guess. Otherwise there isn't any difference. Someone has to have permissions to set-up the system. Or be granted permissions somehow. Once a hacker figures out which user you are using for administrative purposes, the security risk is the same. The only thing this authentication window is is an inconvenience for people attempting to do legitimate things to the system. If I cared about protecting my system from the root user I can disable root on my own. And achieve the same "increase" in security ubuntu experiences. I don't need ubuntu to Microsoft linux for me with implementing there UAC concepts. (or vista implementing ubutus.. whichever :P).

last I checked, 2 things to crack is harder than 1 thing to crack

---

### Post by cariboo on 2010-11-08
> **pdxmusl said:**
> I would agree with the original poster. If there isn't a way to disable this screen, i will be moving to another distribution. This thing is a serious pain. As far as security goes, the only difference between having a root user be the administrator and having a non-root user being the administrator is that the "administrators" login name is harder to guess. Otherwise there isn't any difference. Someone has to have permissions to set-up the system. Or be granted permissions somehow. Once a hacker figures out which user you are using for administrative purposes, the security risk is the same. The only thing this authentication window is is an inconvenience for people attempting to do legitimate things to the system. If I cared about protecting my system from the root user I can disable root on my own. And achieve the same "increase" in security ubuntu experiences. I don't need ubuntu to Microsoft linux for me with implementing there UAC concepts. (or vista implementing ubutus.. whichever :P).

What's the difference between the way Fedora does it, where you set a password for root during installation and the way Ubuntu does it with sudo?

Both distributions ask for authentication when installing packages or making any configuration changes ie: setting up a network connection.

---

