---
title: "Security in recovery mode issue"
date: 2007-06-20
forum: Server Platforms
---

### Post by Beamvr6 on 2007-06-20
I'm using 6.0.6 LTS (AMD 64-bit) and fully up to date and discovered the following.

I started Ubuntu in recovery mode of the latest installed kernel. Started Midnight Commander from the prompt and    was able not only to view files I can't view without sudo in Gnome and password but also was able to edit those files. In the recovery mode start process I never had to enter a password and wasn't asked for using MC. I also had access to all devices normally mounted through fstab.

I'm not sure this issue is related to MC assuming it basically launches linux commands. It means imho that this implies one can start in recovery mode and have full access to all files and edit them or am I missing something here?

---

### Post by 5-HT on 2007-06-20
By default, Ubuntu locks the root account. It's not MC specific, you are automatically granted root privs when using recovery mode. You can always set a root password to prevent such behaviour when booting into recovery mode: that way you'll need to enter the root password in order to be granted root privs. Setting a root password will not interfere with sudo at all.
cheers,

---

### Post by Beamvr6 on 2007-06-20
This feels like the rock and the hard place. In order to secure recovery mode a password for root needs to be set which requires creation of root as a user afaik, yet from what I've read it is much safer to run Ubuntu without the root user and  everything you'll ever need to do in Ubuntu can be done using sudo?

---

### Post by debone on 2007-06-20
> **Beamvr6 said:**
> This feels like the rock and the hard place. In order to secure recovery mode a password for root needs to be set which requires creation of root as a user afaik, yet from what I've read it is much safer to run Ubuntu without the root user and  everything you'll ever need to do in Ubuntu can be done using sudo?

Yep, wouldn't advice a newbee to make a root account. Too much hassle, finallly had to reinstall..

---

### Post by 5-HT on 2007-06-20
> **Beamvr6 said:**
> This feels like the rock and the hard place. In order to secure recovery mode a password for root needs to be set which requires creation of root as a user afaik, yet from what I've read it is much safer to run Ubuntu without the root user and  everything you'll ever need to do in Ubuntu can be done using sudo?

The root account is there in Ubuntu, it's just locked. You can still use sudo for everything if you unlock it, but you will not be able to boot into recovery mode with full root privileges unless you supply the password.

---

### Post by Beamvr6 on 2007-06-21
This is a bit confusing:
- Having read a lot of threads about the root password the main recommendation is DO NOT set a root password.
- Booting in recovery mode gives root rights so files can be added, changed and deleted. Users can also be added and rights granted.
- This can be prevented by setting the root password.

Don't know how to describe the contradiction any clearer. It feels like a house with a front door secured very well but in case you lose the key leave the backdoor unlocked.

To start with the first bullet. What are the main reasons for not setting the root password? I'm fully aware that the superuser account can do virtually everything needed with sudo btw.

---

### Post by 5-HT on 2007-06-21
> **Beamvr6 said:**
> Having read a lot of threads about the root password the main recommendation is DO NOT set a root password. 
It is important to be cognizant of *why* that is the recommendation. Moreover, that recommendation is to not use the root account. Enabling it != using it for recovery mode as recovery mode has root privs anyways. The only difference is whether or not you'll be prompted for a password.
> **Beamvr6 said:**
> 
To start with the first bullet. What are the main reasons for not setting the root password?
I can  only think of one:
In order to compromise an account only two pieces of information are required: 1)username, 2)password (well...there are of course other ways to compromise an account, but they are not relevant for a sudo/root debate).
If you have an active root account, half of the needed info is already there. However, most people use easily attackable usernames and if you have a strong password enabled the point is basically moot.

In terms of why someone would not want to use the root account under X, that is blatantly obvious. I am not advocating that you use X under root privs though and highly recommend that you don't.

There is a lot of FUD surrounding the root account on these forums. Enabling the root account does not necessarily add to security risks. Root accounts are ubiquitous in *nix, and are there *for* security. The reason most commonly stated on these forums is that if you use sudo, it is for a single command and you won't be in a position to forget that you are root and accidentally bork your system. That has *no* bearing on the security of the root account at all. That is simply a matter of user responsibility.

Also, you can get a root shell using sudo. So again, what matters is how you use the granted privileges.
> **Beamvr6 said:**
> I'm fully aware that the superuser account can do virtually everything needed with sudo btw. It's actually the converse: sudo can escalate privs up to and including those of root. 

Overall, it really depends on how you feel. If other people have physical access to you system they can be granted full root privs using recovery mode. It is often mentioned that one cannot protect a system if an attacker has physical access. Indeed, there are many, many ways to compromise a system if you have physical access. However, setting the root account to prevent others from booting in recovery mode can add at least some defense. Additional measures could include setting a grub password, bios password, preventing booting from removable media, encrypting all your disks, etc... They are by no means fool proof, but they can deter someone who either 1) isn't that interested, 2) isn't that knowledgeable.

---

