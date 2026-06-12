---
title: "su -&gt; root"
date: 2021-04-30
forum: Server Platforms
---

### Post by lacid2 on 2021-04-30
I'm somewhat new to Ubuntu server (used ~10 years ago). On my current UNIX servers I'm able to create a user and give permission to "su" (as part of wheel group).
It would be really nice to have the same on Ubuntu server (18.04 and above). I found out that by default root is disabled and I have to *passwd root* to enable it.

[LIST]
[*]sudo su, sudo bash etc is not an option
[*]*PermitRootLogin Yes* in sshd_config isn't an option either
[/LIST]

The only option is to have a user (we can call it joe) who can execute su (/bin/su) and become root itself.

---

### Post by The Cog on 2021-04-30
Don't give root a password. Use sudo instead. Anyone in the sudo group can use sudo, and they then have to give their own (not root's) password. That way, there's no root password to share around.
You can run single commands as sudo: "sudo shutdown now", or run bash as root if you want to run multiple commands without prefixing every one with sudo: "sudo -i".

---

### Post by rsteinmetz70112 on 2021-04-30
If you want a root session you can use sudo -i.  It's pretty close to the Unix su command it makes you in root with /root as the home directory.
Of course you could enable root password and use the su command.

I'm a little curious why you need this and some form sudo won't work. You can even set sudo to not require a password and restrict which commands it has access to.

---

### Post by lacid2 on 2021-04-30
Here is the scenario: sudo is configured via LDAP, sometimes LDAP breaks so I need a backup user.

---

### Post by lacid2 on 2021-04-30
*Of course you could enable root password and use the su command.*<- this is what I'd like to do, how can I do it?

---

### Post by rsteinmetz70112 on 2021-04-30
> **lacid2 said:**
> Here is the scenario: sudo is configured via LDAP, sometimes LDAP breaks so I need a backup user.

I don't run LDAP on any of my computers, you can configure sudo locally, all you have to do is add the users you want to the sudo group```
 usermod -aG sudo newuser
``` but depending on the number of servers it could be a pain to maintain.

I also always have one local user on every server just in case.  

You can enable the root account simply by adding a password for it.

---

### Post by ajgreeny on 2021-05-02
In my 16+ years of running Ubuntu or Ubuntu based distros I have not once found any need to enable a root account or password.
In fact I am also running both Debian and Arcolinux without a separate root account and password and I think it is extremely unlikely that you really need to enable a root password or account on your machine.

See [COLOR="#FF0000"]RootSudo[/COLOR] in my signature below for details, taking particular note of the advantages mentioned there of using sudo.

---

### Post by TheFu on 2021-05-03
Sounds like the LDAP needs a backup server to handle failures. Fix that.

There is nothing special to enable the root account on Ubuntu. I think it is against forum policy to explain how, however.  Perhaps the thought is that if you have to ask, then you shouldn't do it? IDK. There is no magic, no incantation, no group, nothing specific to Ubuntu or Debian required.  Links in posts above have more details from *Ubuntu Wiki* and *Community* help pages.

Back when I ran LDAP, I never had failures that impacted sudo capabilities.  LDAP should cache users and groups for any active logins for at least a day. People use LDAP on disconnected laptops.

If you need a local kbackup user, then make a local user for that purpose.  There are all sorts of failures on Ubuntu when running GUI applications as root, so that really isn't an option.  

Just like any other Unix system, it is very possible to create a local user with the same uid/gid and groups as what a user inside LDAP supports.  Just point the HOME to the same location and you'll be able to login using either.  Sssssh. Don't tell anyone this trick.  Doing things that aren't normally taught is what Unix experts can do to solve specific issues.  Only the admin can decide whether this is pure stupidity or genius.  That is often a fine line.

---

### Post by lacid2 on 2021-05-03
Thank you, this worked, I have an automatization editing bunch of files, it also edited /etc/pam.d/su which denies su
*May  3 14:59:02 ubuntu.hostname.com su[14306]: pam_authenticate: Permission denied*
*May  3 14:59:02 ubuntu.hostname.com su[14306]: FAILED su for root by joe*

I need to find a way to allow only user joe to do su

---

### Post by TheFu on 2021-05-03
> **lacid2 said:**
>  
I need to find a way to allow only user joe to do su

```
sudo -i
```
if "joe" is in the sudo group, as stated above.  sudo can do thousands of other things, BTW.

No other method exists to my knowledge.

---

