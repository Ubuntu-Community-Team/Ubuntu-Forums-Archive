---
title: "Configuring Root Password Login on Ubuntu with CIS Hardening for Console Access"
date: 2024-04-09
forum: Server Platforms
---

### Post by abteilung-technik on 2024-04-09
Hello, Ubuntu Community,


I'm reaching out for some guidance on configuring a secure fallback login method for our systems running Ubuntu Pro with CIS Level 1 hardening applied. We've encountered a unique challenge where our standard login method (exclusively using public keys) isn't viable under certain conditions, specifically network issues.


For background, our infrastructure heavily relies on VCSA (VMware vCenter Server Appliance) remote console access for administration. Normally, all logins are conducted exclusively via SSH with public key authentication. However, we've found that in scenarios where network problems arise, we're unable to use SSH and, by extension, public key authentication to access our systems. This leads to a critical need for a reliable fallback method.


The ideal solution we're aiming for is to enable password login for the root user but only through the software console – akin to having physical access to the server. This is meant strictly as an emergency measure, ensuring we can still manage the system even when network-based access methods fail.


After applying CIS 1 hardening standards, we've run into trouble configuring this setup. Specifically, we're facing an issue with the `passwd` command for the root user, receiving a "passwd: Module is unknown" error despite having reset faillock and ensured all related PAM modules are correctly in place.


Here's our dilemma: how can we maintain the stringent security standards set by CIS hardening while also ensuring that we have a robust, secure method for root access under emergency conditions through the console?


Additionally, if anyone has alternative suggestions or best practices for achieving this type of emergency access setup on systems with similar security requirements, I would greatly appreciate your insights. We're open to exploring different approaches that align with our security and operational needs.


Thank you in advance for your time and assistance. Looking forward to your suggestions and advice.


Best regards

---

### Post by TheFu on 2024-04-09
Ubuntu does not enable root logins. It isn't needed and enabling the root account would be a security failure, IMHO.  I consider other distributions that do allow root logins to have huge security problems that should be solved.

Create a different local account and provide it with sudo access to elevate privileges and record all commands run with sudo (the default).

BTW, nobody here works for Canonical. You are only getting opinions.  The secured networks where I've worked were all air-gapped.  I wasn't an admin on those networks - well - not for most of the users.  My team had servers that I was admin on, but we didn't have root enabled. 

As for network problems, perhaps the better answer is to mandate redundant network cards and switch infrastructure AND remote terminals like the major players do.  Our servers always had 6 network connections and at least 1 serial console connection that was available at the head of each rack row.  If 1 switch failed or 1 NIC failed, we'd see the error in system logs and an alarm would go out to the hardware support guys who would schedule replacement during the next weekend maintenance window.  As the systems architect, I didn't even get notified for hardware issues like that.  OTOH, it was my job to ensure sufficient NIC ports were available in the servers and the switches for the front network, management network and backup networks.  If you have only 1 NIC working in your server and that's the only way to access it, I consider that a network and system design failure.

---

### Post by abteilung-technik on 2024-04-10
So, if I understand correctly, you're suggesting creating a separate user account and granting it the ability to log in via password. This seems like a feasible approach to avoid enabling root login while still maintaining emergency access under specific conditions.


I'm considering using the sshd_config's Match block for this purpose. Essentially, I could configure it to allow password authentication for this new user, but strictly limit this capability to connections from a certain internal network, enhancing security.


Would something like the following configuration be the right way to implement this idea?



```

Match User emergencyUser Address 192.168.1.0/24
    PasswordAuthentication yes

```



This setup would mean `emergencyUser` can log in with a password only when connecting from the 192.168.1.0/24 subnet. Do you think this is a secure and effective method to achieve the emergency access we need, while keeping in line with best practices for a hardened Ubuntu setup?



I'm currently facing a challenge on systems running Ubuntu Pro that have been hardened following the CIS (Center for Internet Security) benchmarks at USG Server Level 1. After applying these hardening measures, I've run into an issue when attempting to assign or change passwords for users. Whenever I try to use the `passwd` command, I encounter the following errors:


```

passwd: Module is unknown
passwd: password unchanged

```


This seems to be a direct consequence of the CIS hardening process, possibly due to stricter PAM (Pluggable Authentication Modules) configurations or other security policies that have been put into place to strengthen the system's defenses.


Given the stringent security requirements we're adhering to, I'm looking for guidance on how to successfully assign or change user passwords under these conditions. Is there a recommended workaround or specific steps I should follow to manage user passwords without compromising the hardened security stance of the system?


I found this one:
[https://ubuntuforums.org/showthread.php?t=1973164](https://ubuntuforums.org/showthread.php?t=1973164)

But i cant figure out where is my issue located.
 /etc/pam.d/common-password  
```

# here are the per-package modules (the "Primary" block)
password        [success=1 default=ignore]      pam_unix.so obscure yescrypt remember=5
# here's the fallback if no module succeeds
password        requisite                       pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
password        required                        pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config
password requisite pam_pwquality.so retry=3



```

I appreciate any insights or advice you can share. Thank you in advance for your time and help.


Best regards

---

### Post by abteilung-technik on 2024-04-10
Okay, I have identified the problem. I misunderstood something.


I don't have to do anything in the sshd configuration if a user is to be able to log in locally. That was my mistake.
The problem is that I could not assign a password to the user that I had already created during the installation.


To solve the problem I had to use 'usermod':
```

openssl passwd -6 -salt RANDOMSALT 'yournewpassword'

```

```

sudo usermod -p 'yournewpasswordhash' username

```

Now the user has a password again with which he can log in. However, as no password login via SSH is permitted in the SSHD configuration, the user can only log in locally.

If I have done something wrong, please tell me where my mistake is so that I can fix it

---

### Post by TheFu on 2024-04-10
I'm busy this morning, so didn't read everything carefully.

ssh doesn't honor PAM.  That's probably the missing thing. I didn't understand that decades ago.  I'd lock an account, but people could still ssh into the system.
ssh is network logins.
PAM is local logins and for passwords, if any. 

I don't understand using usermod.  Why not just use the **passwd** command to set the password for the user?  I suppose either method can work, but **passwd** is the normal way.

There are usually 50 different ways to achieve an outcome. Which is best is often a matter of opinion and experience.  Networking really just never fails anywhere I've worked because we have redundant NIC connections to all servers from redundant switches.

---

### Post by MAFoElffen on 2024-04-10
I missed something... Why not another user with it's own shh key?

Ths might help as it releates to security and the CIS: [https://security.stackexchange.com/questions/174558/is-allowing-root-login-in-ssh-with-permitrootlogin-without-password-a-secure-m](https://security.stackexchange.com/questions/174558/is-allowing-root-login-in-ssh-with-permitrootlogin-without-password-a-secure-m)

---

### Post by abteilung-technik on 2024-04-12
Thank you for your answers.
The problem is that IF the network fails or has problems, then access to the system is no longer possible IF logins are only allowed via PublicKey.


Since we do not allow logins via SSH without PublicKey. We also do not use passwords. 


As these are virtual systems, this means that the system is no longer accessible in the event of a failure.
My question was therefore how I can assign a password to a "local admin" user. The user was already there during installation. However, old Ansible routines removed the password. After that there was an Ubuntu Pro CIS Level 1 hardening.
From this point on, passwd was no longer possible.
```

passwd: Module is unknown
passwd: password unchanged

```
That's why I looked for other options. I know that passwd is the normal way, but it no longer works after a hardinung.

---

### Post by TheFu on 2024-04-12
> **abteilung-technik said:**
>  
That's why I looked for other options. I know that passwd is the normal way, but it no longer works after a hardinung.

Ah.  


If the passwd command still exists, you could change the permissions to only allow your backup userid to run it as root.  I haven't tried it, so I don't know if there are any extra protections inside the program - there definitely have to be.  I've written a few setuid-root programs in my decades doing these things.  That was before we had sudo, however.  There are other, similar to sudo, tools.  Besides my own, extremely specialized programs, I've never used anything but sudo.

```
$ ll /usr/bin/passwd
-rw[COLOR="#FF0000"]s[/COLOR]r-xr-x 1 root root 59976 Feb  6 07:54 /usr/bin/passwd*

```
We can see that the program is setuid-root.  Just change the group to one for the new userid and remove any access for "other".

---

