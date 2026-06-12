---
title: "Cant't decrypt /home user directory - LOGIN passphrase not working"
date: 2013-04-30
forum: Security
---

### Post by phantolino on 2013-04-30
Hello,

I'm writing here as my last resort, since after hours of googling and trying different things i ended up not able to recover my files. I will try to explain my problem as simple and detailed i can:

[LIST]
[*]Using Ubunty 12.04 with encryption on my files.
[*]Laptop died - i removed my HDD and installed it on another computer.
[*]Logged back in and changed password removed HDD again (other computer was old and had hardware issues).
[*]Installed HDD again on another computer (same brand laptop as mine).
[*]Tried to log back in, had the login loop error - black screen with loop login error - i created a new admin user using terminal.
[*]Logged in with new user, changed the password of my old account, logged off and logged in back succefully.
[/LIST]

At this point i had my password changed twice, the problem is that when i tried to access my encrypted files via *ecryptfs-recover-private* command my LOGIN passphrase doesn't work, i tried using all passwords. I have the MOUNT passphrase and i can mount my /home directory but i can't view the files since they are still encrypted. 


What i'm missing here? Thanks in advance.

---

### Post by trundlenut on 2013-04-30
Check the permissions on the home folder for your original user.  I managed to mess them up and got a similar loop problem

---

### Post by phantolino on 2013-05-01
> **trundlenut said:**
> Check the permissions on the home folder for your original user.  I managed to mess them up and got a similar loop problem

I'm using the original user. I also tried with the new user wich is in the sudo group (and gave him full permisions to the original user folder), to do it with the same results :(. One think that i don't understand is why it is asking me in ecryptf-recover-private, if i have the LOGIN passphrase (Y/n), whats the point even if i have the mount key, i can't view the files...

---

### Post by phantolino on 2013-05-01
I managed to get my files by changing my password again to the original one i had. After doing that i runned *ecryptfs-recover-private *again and at LOGIN passphrase question i chose No, then i entered my MOUNT passphrase and the files was readable again :guitar:

---

