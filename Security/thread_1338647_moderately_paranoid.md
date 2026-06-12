---
title: "moderately paranoid"
date: 2009-11-26
forum: Security
---

### Post by Ron_ on 2009-11-26
I have just installed my first Ubuntu system.  I wanted to take some security precautions based on recommendations from Uwe Hermann, Ubuntu's "Stricter Defaults" page and elsewhere.  I am finding it difficult to implement some of them in 9.10.

1) In "/etc/ssh/sshd_config" change PermitRootLogin yes to PermitRootLogin no.  [File not found.]

2) sudo chown root:admin /bin/su.  [Or /bin/sudo, as someone advised?  su file exists but sudo does not.  Original SU properties: Owner:Root (RW) Group:Root (ReadOnly) Others:ReadOnly)]

Once these matters are resolved, I intend also to do the following.

3) chmod 4750 /bin/su.

4) gksudo gedit /etc/fstab.  Add the following line of code:  tmpfs /dev/shm tmpfs defaults,ro 0 0.

5) chmod 0700 /home/username. [Done.]

Do these all look okay?

---

### Post by rookcifer on 2009-11-26
> **Ron_ said:**
> I have just installed my first Ubuntu system.  I wanted to take some security precautions based on recommendations from Uwe Hermann, Ubuntu's "Stricter Defaults" page and elsewhere.  I am finding it difficult to implement some of them in 9.10.

1) In "/etc/ssh/sshd_config" change PermitRootLogin yes to PermitRootLogin no.  [File not found.]

That's because ssh is not installed by default and I recommend you *not* install it unless you know how to properly secure it.

> 2) sudo chown root:admin /bin/su.  [Or /bin/sudo, as someone advised?  su file exists but sudo does not.  Original SU properties: Owner:Root (RW) Group:Root (ReadOnly) Others:ReadOnly)]

Once these matters are resolved, I intend also to do the following.

3) chmod 4750 /bin/su.

4) gksudo gedit /etc/fstab.  Add the following line of code:  tmpfs /dev/shm tmpfs defaults,ro 0 0.

5) chmod 0700 /home/username. [Done.]

Do these all look okay?

I personally do not worry with any of these "hardening" tips except for #5.  I think #4 is already implemented anyway.  #1 is good *if* you use ssh.  So, basically I would ignore #2 and #3.

The only thing you need to do in regard to security with Ubuntu (and most Linux distros) is:

1) Make sure ssh is not listening if you don't use it.
2) Ditto for VNC
3) Install packages only from the repos
4) Always update your system when prompted by Ubuntu

Ubuntu comes with no open ports by default, so even a firewall is not necessary (though I recommend buying a good router like a Linsys WRT54GL and flash it with Tomato, especially if you have Windoze boxes on your network).

If you want to delve into advanced security, look into AppArmor.  There is a sticky at the top of this forum that covers these topics.

---

### Post by sisco311 on 2009-11-26
> **Ron_ said:**
> 
2) sudo chown root:admin /bin/su.  [Or /bin/sudo, as someone advised?  su file exists but sudo does not.  Original SU properties: Owner:Root (RW) Group:Root (ReadOnly) Others:ReadOnly)]

Once these matters are resolved, I intend also to do the following.

3) chmod 4750 /bin/su.
[Done.]

Do these all look okay?

By default, the root account password is locked, so you can not su to root, however any user is allowed to su. If you want to restrict this and allow only users in the admin group to use su, then edit the etc/pam.d/su file, uncomment the 
```

#auth       required   pam_wheel.so
```line and edit it to look like this:
```
auth       required   pam_wheel.so    **group=admin**
```

By default only members of the admin group are allowed to use sudo, so changing the file's permission is futile. 

If you want to restrict the sudo right of some users, then edit the sudoers file: [thread=1132821]HowTO: Sudoers Configuration[/thread]

---

### Post by rookcifer on 2009-11-26
> **sisco311 said:**
> By default, the root account password is locked, so you can not su to root, however any user is allowed to su. If you want to restrict this and allow only users in the admin group to use su, then edit the etc/pam.d/su file, uncomment the 
```

#auth       required   pam_wheel.so
```line and edit it to look like this:
```
auth       required   pam_wheel.so    **group=admin**
```

By default only members of the admin group are allowed to use sudo, so changing the file's permission is futile. 

If you want to restrict the sudo right of some users, then edit the sudoers file: [thread=1132821]HowTO: Sudoers Configuration[/thread]

Exactly.  Which is why I told him to ignore #2 and #3.  I don't know who wrote that tutorial but they obviously don't use Ubuntu (or else they would know there is no su to root by default).

---

### Post by EJeanmaire on 2009-11-27
> **rookcifer said:**
> 
I personally do not worry with any of these "hardening" tips except for #5.  

This.

> **rookcifer said:**
> 
Ubuntu comes with no open ports by default, so even a firewall is not necessary (though I recommend buying a good router like a Linsys WRT54GL and flash it with Tomato, especially if you have Windoze boxes on your network).

Not quite true, if you are running Gnome, mDNS/Ahavi service runs, and will definitely scream out to the world as much as it can that you are using Ubuntu.

---

### Post by Ron_ on 2009-11-27
Very helpful.  Thank you all.  Because I am a newbie, I will try to repeat back your advice to see if I've got it straight.

1) By default, SSH is not installed (thus, not listening.)  I don't need it, so my best course is to do nothing.  May I assume that the same holds for VNC?

2) and 3) I still have some confusion over the difference between su and sudo, but by default no one can su to root and only admins are allowed to sudo.  Because of this, changing (su?/sudo?) ownership and permissions adds no protection.  I understand that I can edit the line in etc/pam.d/su if I like.

4) I was unable to confirm that this was implemented anyway.  In any case it will do no harm to add the line.

5) Done and worthwhile.

I did install AppArmor, CheckRootKit, ClamAV, Firestarter, Snort and Wireshark.  Some day I'll have to figure out how/when to use them.

While we're on the topic, let me ask one more question.  I went to some trouble to create encrypted partitions on a dual-boot machine.  If I were dumb enough to open a port after mounting the encrypted volumes, could an intruder read them by masquerading as me, or would the intruder be seen as a new user and confronted with the passphrase prompt?

---

### Post by wilee-nilee on 2009-11-28
Your computer is never safe as long as court orders for search and seizure are still implemented.

---

