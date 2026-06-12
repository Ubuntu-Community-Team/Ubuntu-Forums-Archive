---
title: "SSH privacy concern"
date: 2010-09-21
forum: Security
---

### Post by Sianegad on 2010-09-21
Hi, I am looking for a way to insure privacy to users while still being able to administer their computer through SSH.  Because `hey trust me!` is not often enough, when you tell people you can get in their computer

I would like to make it impossible to access some folders remotely.  I need it to be transparent to users so Encryption is not my first choice.

I will log-in through SSH with an admin account.  I tried 'chmod 700' which prevent access to it, but i still can change it back anytime.  and 'sudo su' will get me everywhere.  

maybe a local script could toggle SSH server on and off and encrypt/decrypt a few folders but i think i have seen something about preventing root access to folders before (i didnt need that then) but i cannot find it now, i might have misunderstood.

surely there is a way to prevent IT geeks from getting to the president's lamp shade hat pictures...  :-\"

A nudge in the right direction would be nice

---

### Post by Bachstelze on 2010-09-21
If your users use the "encrypted home directory" feature of Ubuntu, you can just ask them to log out while you do your stuff: it will automagically encrypt their home directories.

---

### Post by bodhi.zazen on 2010-09-21
> **Sianegad said:**
> Hi, I am looking for a way to insure privacy to users while still being able to administer their computer through SSH.  Because `hey trust me!` is not often enough, when you tell people you can get in their computer

I would like to make it impossible to access some folders remotely.  I need it to be transparent to users so Encryption is not my first choice.

I will log-in through SSH with an admin account.  I tried 'chmod 700' which prevent access to it, but i still can change it back anytime.  and 'sudo su' will get me everywhere.  

maybe a local script could toggle SSH server on and off and encrypt/decrypt a few folders but i think i have seen something about preventing root access to folders before (i didnt need that then) but i cannot find it now, i might have misunderstood.

surely there is a way to prevent IT geeks from getting to the president's lamp shade hat pictures...  :-\"

A nudge in the right direction would be nice

The only possible ways to confine root are with tools such as apparmor (or selinux) or encryption.

You could likely adapt this post

[Jailbash]("http://ubuntuforums.org/showpost.php?p=9799756&postcount=5") 

Either that or use encrypted home directories, or some variation.

---

### Post by CharlesA on 2010-09-21
+1 to jailbash. Sounds like a nice way to go about it.

---

### Post by BkkBonanza on 2010-09-23
You could copy bash to a new shell and attach it to sshd as only permitted shell. Then use apparmor to lock down the new shell to restricted areas. I haven't tried this but it seems doable.

Other than that an encrypted home is the best bet. It's transparent to users but makes sure that others can't get into the files. It's probably possible to config an encrypted private directory that opens on login (using pam as does encrypted home) if you need home to be "open to admin" but still have a private area.

(edit: sounds like I'm just repeating past ideas)

---

