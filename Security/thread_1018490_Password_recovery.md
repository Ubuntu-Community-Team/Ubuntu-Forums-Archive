---
title: "Password recovery"
date: 2008-12-22
forum: Security
---

### Post by Lloydlec on 2008-12-22
Two of my servers have been hacked and the ROOT passwords changed. Is there anyway I can gain control of the servers again ? I need to set up new passwords but without the original(as it has been changed) I seem to have a problem and as I am really clueless on this Linux stuff I need help! Can I get control remotely or do I have to go to the servers?

---

### Post by Sarmacid on 2008-12-22
If you have sudo rights you can change the root password or disable it(add -l to disable it)```
sudo passwd root
```

But now that the servers have been compromised, you should just grab your data, wipe them and reinstall.

---

### Post by cdenley on 2008-12-22
I'm guessing your server got hacked because you set a root password. When an attacker tries to guess your password, 2 out of 3 times they guess with the root user. If you used your admin user account, they wouldn't have known a valid username. Also, make sure you choose a strong password.

If you don't have "sudo" access for some reason, then you will need physical access.

I agree with Sarmacid that there is no way to know what an attacker did, and you can no longer trust that filesystem. The only safe thing to do is wipe it, then reinstall following safe practices.
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by Lloydlec on 2008-12-22
Thanks SARMACID, I will see what I can do and try and limit damage! I wish I could do this stuff:-(

---

### Post by Lloydlec on 2008-12-22
Thanks cdelley, will give it a try!

---

### Post by rweaver on 2008-12-23
> **Lloydlec said:**
> Two of my servers have been hacked and the ROOT passwords changed. Is there anyway I can gain control of the servers again ? I need to set up new passwords but without the original(as it has been changed) I seem to have a problem and as I am really clueless on this Linux stuff I need help! Can I get control remotely or do I have to go to the servers?

It depends on the exact situation, and it changes dramatically depending on if you were hacked by an expert or a script kiddie, how long they've had access, if they've installed a root kit, etc.  

However, the first thing to attempt is what was described above-- reset the root password via sudo.  If that fails then you almost have to have direct access to the machine or at least someone on site who can work with you.  

The secondary thing you need to figure out is how they obtained access.  The first place to look for that is passwords, if you're using less than a 8 character password that is mixed case with numbers letters and symbols, you need to correct it. D4rkn3$s is a bad password (better than a simple word though) because it spells darkness and is relatively easy to crack based on rules. s*@nK81- is a much stronger password because it's not based off a dictionary and is fairly complex.  Longer passwords are better and be sure not to use the same password on any two systems.  If you're having trouble remembering passwords get a program like keepass that lets you remember a password for it and it stores your remaining passwords in an encrypted format.  Another thing to carefully monitor is who has access to the system via sudo.

If you don't have extensive experience with Linux security your best option is to wipe the machines and start from scratch after you retrieve your data.

---

### Post by Vantrax on 2008-12-23
I would suggest that even if you were a linux security expert you would still do a complete wipe and rebuild.

You can never trust the integrity of a box that has been compromised.

---

