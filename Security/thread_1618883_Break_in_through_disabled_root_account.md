---
title: "Break in through disabled root account"
date: 2010-11-11
forum: Security
---

### Post by bluenova on 2010-11-11
Hi there,

If root is disabled by default, how is it possible that someone managed to SSH into my computer using root? I never enable/set password for root, it's always left as the default as per a fresh install and I always use sudo for any admin tasks.

**Auth.log**

First there are a whole load of failed attempts then...
```

Nov  8 11:07:32 Morris-Desktop sshd[3601]: Failed password for root from 94.243.50.53 port 4360 ssh2
Nov  8 11:07:38 Morris-Desktop sshd[3603]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=94.243.50.53  user=root
Nov  8 11:07:40 Morris-Desktop sshd[3603]: Failed password for root from 94.243.50.53 port 1546 ssh2
Nov  8 11:07:47 Morris-Desktop sshd[3605]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=94.243.50.53  user=root
Nov  8 11:07:49 Morris-Desktop sshd[3605]: Failed password for root from 94.243.50.53 port 2097 ssh2
Nov  8 11:07:56 Morris-Desktop sshd[3607]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=94.243.50.53  user=root
Nov  8 11:07:58 Morris-Desktop sshd[3607]: Failed password for root from 94.243.50.53 port 2679 ssh2
Nov  8 11:08:04 Morris-Desktop sshd[3609]: pam_sm_authenticate: Called
Nov  8 11:08:04 Morris-Desktop sshd[3609]: pam_sm_authenticate: username = [root]
Nov  8 11:08:04 Morris-Desktop sshd[3609]: Accepted password for root from 94.243.50.53 port 3243 ssh2
Nov  8 11:08:04 Morris-Desktop sshd[3609]: pam_unix(sshd:session): session opened for user root by (uid=0)
Nov  8 11:08:06 Morris-Desktop sshd[3609]: Received disconnect from 94.243.50.53: 11: Goodbye
Nov  8 11:08:06 Morris-Desktop sshd[3609]: pam_unix(sshd:session): session closed for user root
```

Then nothing for a couple of days until...

```
Nov 10 15:57:49 Morris-Desktop sshd[6244]: Failed password for invalid user oracle from 78.111.99.76 port 55081 ssh2
Nov 10 15:57:50 Morris-Desktop sshd[6246]: Address 78.111.99.76 maps to host-78-111-99-76.teklan.com.tr, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Nov 10 15:57:50 Morris-Desktop sshd[6246]: Invalid user test from 78.111.99.76
Nov 10 15:57:50 Morris-Desktop sshd[6246]: pam_unix(sshd:auth): check pass; user unknown
Nov 10 15:57:50 Morris-Desktop sshd[6246]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=78.111.99.76 
Nov 10 15:57:52 Morris-Desktop sshd[6246]: Failed password for invalid user test from 78.111.99.76 port 55723 ssh2
Nov 10 15:57:52 Morris-Desktop sshd[6126]: pam_unix(sshd:session): session closed for user root
Nov 10 16:01:17 Morris-Desktop sshd[6250]: Address 83.43.17.244 maps to 244.red-83-43-17.dynamicip.rima-tde.net, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Nov 10 16:01:18 Morris-Desktop sshd[6250]: pam_sm_authenticate: Called
Nov 10 16:01:18 Morris-Desktop sshd[6250]: pam_sm_authenticate: username = [root]
Nov 10 16:01:18 Morris-Desktop sshd[6250]: Accepted password for root from 83.43.17.244 port 3208 ssh2
Nov 10 16:01:18 Morris-Desktop sshd[6250]: pam_unix(sshd:session): session opened for user root by (uid=0)
Nov 10 16:03:51 Morris-Desktop groupadd[6352]: group added to /etc/group: name=httpd, GID=1000
Nov 10 16:03:51 Morris-Desktop groupadd[6352]: group added to /etc/gshadow: name=httpd
Nov 10 16:03:51 Morris-Desktop groupadd[6352]: new group: name=httpd, GID=1000
Nov 10 16:03:51 Morris-Desktop useradd[6357]: new user: name=httpd, UID=1000, GID=1000, home=/home/httpd, shell=/bin/bash
Nov 10 16:03:52 Morris-Desktop passwd[6364]: eCryptfs PAM passphrase change module retrieved a NULL passphrase; nothing to do
Nov 10 16:04:01 Morris-Desktop passwd[6364]: pam_unix(passwd:chauthtok): password changed for httpd
Nov 10 16:04:01 Morris-Desktop passwd[6364]: gkr-pam: couldn't update the login keyring password: no old password was entered
Nov 10 16:04:01 Morris-Desktop passwd[6364]: Error attempting to parse .ecryptfsrc file; rc = [-13]
Nov 10 16:04:01 Morris-Desktop passwd[6364]: Passphrase file wrapped
Nov 10 16:04:01 Morris-Desktop passwd[6364]: eCryptfs PAM passphrase change module retrieved at least one NULL passphrase; nothing to do
Nov 10 16:04:03 Morris-Desktop chfn[6365]: changed user 'httpd' information
Nov 10 16:04:10 Morris-Desktop sshd[6369]: Address 83.43.17.244 maps to 244.red-83-43-17.dynamicip.rima-tde.net, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Nov 10 16:04:13 Morris-Desktop sshd[6369]: pam_sm_authenticate: Called
Nov 10 16:04:13 Morris-Desktop sshd[6369]: pam_sm_authenticate: username = [httpd]
Nov 10 16:04:13 Morris-Desktop sshd[6369]: Accepted password for httpd from 83.43.17.244 port 3215 ssh2
Nov 10 16:04:13 Morris-Desktop sshd[6369]: pam_unix(sshd:session): session opened for user httpd by (uid=0)
Nov 10 16:06:01 Morris-Desktop CRON[6488]: pam_unix(cron:session): session opened for user httpd by (uid=0)
```

So what they did is create a new user (httpd) with admin privileges and created a cron job under that user which runs a script to bounce things using muh to an irc server in Hungary.

If they hadn't of been silly enough to use a UID in the range that appears on the GDM login screen I wouldn't of caught them.

But what's really bugging me is how they dictionary hacked into a supposedly disabled root account?

---

### Post by CharlesA on 2010-11-11
I don't know how they could have gotten in if the root account was locked, as all they would get would be authentication failures.

Note: By default sshd_config allows root logins, but that should have failed with authentication failure.

What sort of install is that? I know VPS will enable the root account.

You can verify that root has a password or not by running this:

```
charles@atlantis:~$ **sudo cat /etc/shadow | grep root**
root:*:14876:0:99999:7:::
```

The "*" means that account is locked. See [here]("http://www.cyberciti.biz/faq/understanding-etcshadow-file/").

---

### Post by bluenova on 2010-11-11
> **CharlesA said:**
> What sort of install is that? I know VPS will enable the root account.
Just a recent install of Linux Mint. The only thing I enabled was sshd which I thought shouldn't enable the root account.


> **CharlesA said:**
> You can verify that root has a password or not by running this:

```
charles@atlantis:~$ **sudo cat /etc/shadow | grep root**
root:*:14876:0:99999:7:::
```

The "*" means that account is locked. See [here]("http://www.cyberciti.biz/faq/understanding-etcshadow-file/").

Well there is a Hash there now, but I did change the password straight away as soon as I realised root was compromised.

Any idea how to lock it again? It is just a case of disabling the account, that won't mess up sudo or anything?

Also it's strange the ports they were using as I only opened (on the routers firewall) inbound for 22, 80 and 8080 all of which are closed again now. I know it was silly to use port 22 for SSH, I will change it to something else.

---

### Post by OpSecShellshock on 2010-11-11
Found [this]("http://forums.linuxmint.com/viewtopic.php?f=6&t=59210"), which might partially explain it. Mint is based on Ubuntu, but it's a different distro. I didn't read the whole thread, but it appears that the way they use root isn't the same--i.e. in Mint the root account is enabled, and has the same password as the first user account created (the one with sudo privileges). In combination with a default SSH server configuration, that would leave it wide open to brute force attempts.

---

### Post by CharlesA on 2010-11-11
> **bluenova said:**
> 
Well there is a Hash there now, but I did change the password straight away as soon as I realised root was compromised.

Any idea how to lock it again? It is just a case of disabling the account, that won't mess up sudo or anything?

You can lock the root account by running this:

```
sudo passwd -l root
```

> Also it's strange the ports they were using as I only opened (on the routers firewall) inbound for 22, 80 and 8080 all of which are closed again now. I know it was silly to use port 22 for SSH, I will change it to something else.

The source port doesn't matter, the client will pick a random number between 1024 and 65535(or something close to it) to send from. The destination port doesn't change.

> **OpSecShellshock said:**
> Found [this]("http://forums.linuxmint.com/viewtopic.php?f=6&t=59210"), which might partially explain it. Mint is based on Ubuntu, but it's a different distro. I didn't read the whole thread, but it appears that the way they use root isn't the same--i.e. in Mint the root account is enabled, and has the same password as the first user account created (the one with sudo privileges). In combination with a default SSH server configuration, that would leave it wide open to brute force attempts.

Wow. That's a hell of an interesting way to do it, different from both Ubuntu and Debian.

Bad idea (imho) especially when the default sshd config is set to allow root logins.

You should set **PermitRootLogin** to "no" in sshd_config if you install an ssh server, since you can always use sudo to drop to a root prompt.

---

### Post by bluenova on 2010-11-11
Thanks both for the information, very helpful.

> **CharlesA said:**
> You can lock the root account by running this:

```
sudo passwd -l root
```
I did this and it reported:
```
passwd: password expiry information changed.
```
but when I do ```
sudo cat /etc/shadow | grep root

``` I still see the hash instead of a *?

> **CharlesA said:**
> You should set **PermitRootLogin** to "no" in sshd_config if you install an ssh server, since you can always use sudo to drop to a root prompt.
Now done.

---

### Post by CharlesA on 2010-11-11
Try logging in as root from the console. It should be "locked" since the password is set to "expired"

---

### Post by bluenova on 2010-11-11
> **CharlesA said:**
> Try logging in as root from the console. It should be "locked" since the password is set to "expired"

It comes back with
```
su: Authentication failure
```
I'm pretty sure I used the password I set it too so I guess that means it's locked?

---

### Post by CharlesA on 2010-11-11
Yeah. If you want to test it again, set a password for root and then see if you can login - you'll be able to.

Then lock it again and try it again. :)

---

### Post by FuturePilot on 2010-11-11
> **CharlesA said:**
> You can lock the root account by running this:

```
sudo passwd -l root
```


This is not the correct way to re-disable the root account. See here [https://help.ubuntu.com/community/RootSudo#Re-disabling%20your%20root%20account]("https://help.ubuntu.com/community/RootSudo#Re-disabling%20your%20root%20account")

---

### Post by CharlesA on 2010-11-11
> **FuturePilot said:**
> This is not the correct way to re-disable the root account. See here [https://help.ubuntu.com/community/RootSudo#Re-disabling%20your%20root%20account]("https://help.ubuntu.com/community/RootSudo#Re-disabling%20your%20root%20account")

Thanks! Figures that I wouldn't notice that part, since I have that page bookmarked. =/

EDIT: That would work for disabling any user account, wouldn't it?

---

### Post by arapaho on 2010-11-11
@bluenova
I'm also using Mint. Can you check how gksu works for you, because blocking root in Mint for me wasn't effective. 

Regardless of which command I use:
```
sudo passwd -l root
sudo usermod -p ! root
sudo usermod -p '!' root
```
I get:
```
root:!:14924:0:99999:7:::
```
According to one of the comments from the article mentioned * or ! indicates that root account is locked.
But I'm not sure if is actually truth because I can open nautilus as root giving the primary user password with this command:
```
gksu nautilus
```
It looks like in Mint it doesn't work properly.

---

### Post by CharlesA on 2010-11-11
You can still use sudo and gksu with root locked.

You just cannot login directly as root using su or logging in from a console/ssh/whatever.

---

### Post by arapaho on 2010-11-11
@CharlesA
Thank you for explanation. That's a big relief for me. I feel now a little bit more secure.

---

### Post by sisco311 on 2010-11-11
> **FuturePilot said:**
> This is not the correct way to re-disable the root account. See here [https://help.ubuntu.com/community/RootSudo#Re-disabling%20your%20root%20account]("https://help.ubuntu.com/community/RootSudo#Re-disabling%20your%20root%20account")

Both ways are correct.

**passwd -l root** adds a ! at the beginning of the hash, while **usermod -p '!' root** replaces the hash with a !.

---

### Post by CharlesA on 2010-11-11
> **sisco311 said:**
> Both ways are correct.

**passwd -l root** adds a ! at the beginning of the hash, while **usermod -p '!' root** replaces the hash with a !.

Thanks for the clarification. :)

I learned something new today. :guitar:

---

### Post by FuturePilot on 2010-11-11
> **sisco311 said:**
> Both ways are correct.

**passwd -l root** adds a ! at the beginning of the hash, while **usermod -p '!' root** replaces the hash with a !.

However passwd -l will break root cronjobs since it marks the account as expired. It also breaks the root shell in recovery mode.

---

### Post by CharlesA on 2010-11-11
> **FuturePilot said:**
> However passwd -l will break root cronjobs since it marks the account as expired. It also breaks the root shell in recovery mode.

How do you mean? The hash is set the same.

---

### Post by sisco311 on 2010-11-11
> **FuturePilot said:**
> However passwd -l will break root cronjobs since it marks the account as expired. It also breaks the root shell in recovery mode.

Nope.

```
       -l, --lock
           Lock the password of the named account. This option disables a
           password by changing it to a value which matches no possible
           encrypted value (it adds a '!' at the beginning of the password).

           Note that this does not disable the account. The user may still be
           able to login using another authentication token (e.g. an SSH key).
           To disable the account, administrators should use usermod
           --expiredate 1 (this set the accounts expire date to Jan 2, 1970).

           Users with a locked password are not allowed to change their
           password.

```

---

### Post by sisco311 on 2010-11-11
> **CharlesA said:**
> How do you mean? The hash is set the same.

Oh, I remember it now...

In earlier versions the --lock option also marked the account as expired.  
They changed this behavior in passwd 1:4.1.1-3. You can check out the changelog:
```
less +/"shadow \(1:4.1.1-3\)" /usr/share/doc/passwd/changelog.Debian.gz
```

So, in Ubuntu 8.10 (I think) and in earlier releases the --lock option disables an account by changing the password to a value which matches no possible encrypted value, and by setting the account expiry field to 1.

---

### Post by CharlesA on 2010-11-11
> **sisco311 said:**
> Oh, I remember it now...

In earlier versions the --lock option also marked the account as expired.  
They changed this behavior in passwd 1:4.1.1-3. You can check out the changelog:
```
less +/"shadow \(1:4.1.1-3\)" /usr/share/doc/passwd/changelog.Debian.gz
```

So, in Ubuntu 8.10 (I think) and in earlier releases the --lock option disables an account by changing the password to a value which matches no possible encrypted value, and by setting the account expiry field to 1.

I see.

Thanks for the info. :)

---

