---
title: "Restrict AD Logins to Ubuntu Server?"
date: 2007-09-09
forum: Server Platforms
---

### Post by AxelF on 2007-09-09
hi, 

i have Ubuntu Fiesty setup for AD authentication and can successfully log into my server using a domain account locally or via ssh.  i created a domain global group called Linux Admins and put my account in it. in my sshd_config i added:

AllowGroups root LinuxAdmins

which restricts ssh logins to user in the Linux Admins AD group and local users.  what i am wondering is if there is a way to restrict console logins the same way? 

thanks.

---

### Post by HermanAB on 2007-09-09
Hmm, how did you set it up?  Winbind and PAM?  If so, then look at /etc/pam.d/system-auth and /etc/pam.d/login then make winbind required.

Cheers,

H.

---

### Post by AxelF on 2007-09-09
yes, i used winbind and pam.  i should have mentioned that in my first message.  i will take a look at the pam configurations you suggested.   basically i am trying to duplicate the way a windows server works, only allowing members of the domain admins groups the ability to log into the server when it is joined to a domain.

-af

---

### Post by AxelF on 2007-10-04
i still haven't been able to make this work.  after some reading and googling i thought a  good way to approach this would be to use the pam_succeed_if.so module.  to recap, i have a group in my Active Directory called LinuxAdmins.  my linux severs run Ubuntu and I have them configured for ad authentication which works great.  i want to make sure on my severs, only the local users or members of the AD LinuxAdmins group can log in, very much like how with a Windows 2003 Sever the local computer policy prevents a regular user from walking up to it and logging in at the console you must be a member of the Domain Admins  group to log in.

so what i tried doing was this.  first i got the gid by for my AD group by using the getent command:

```

root@somesystem:/etc/pam.d# getent group | grep myadminaccount
linuxadmins:x:10011:someotheradminaccount,myadminaccount
root@somesystem:/etc/pam.d# 

```

so the gid for linuxadmins is 10011.  i then edited the /etc/pam.d/samba as follows:

```

account sufficient      pam_succeed_if.so debug gid = 10011
@include common-auth
@include common-account
@include common-session

```

but it doesn't seem to make any difference.  also, from the documentation the debug flag should produce some messages in /var/log/syslog but it does not.

can anyone steer me in the right direction?

thanks
-axel

---

### Post by AxelF on 2007-10-04
okay, i am a little closer.  i n common-account i put:

```

account required pam_succeed_if.so debug user ingroup linuxadmins

```

i also found the debug messages for pam go to auth.log, duh.  and i see when i log in pam allows it because my account is in the linuxadmins group.  however i can no longer log in with a local account, so this still needs some more fine tuning.

-axelf

---

### Post by AxelF on 2007-10-04
okay this is my final solution.  

my common-account:

```
# /etc/pam.d/common-account - authorization settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authorization modules that define
# the central access policy for use on the system.  The default is to
# only deny service to users whose accounts are expired in /etc/shadow.
#
[B]account [default=1 success=ignore] pam_succeed_if.so quiet uid >= 10000
account required        pam_succeed_if.so debug user ingroup linuxadmins[/B]
account sufficient      pam_winbind.so
account required        pam_unix.so

```

my samba idmap uid and gid are both 10000-20000.  the first line makes it so if the uid is greater than or equal to 10000 then the user is assumed to be a samba account and it will process the following line, otherwise it will ignore it.  the next line will check to see if the user is in the linuxadmins group.

all in all this seems to work just fine.  i posted the full result here in case it helps someone else.  i think this is the right way to do it, but i am by no means a pam.d expert, maybe someone else who is more knowledgeable would be kind enough to let me know if this is a clean and elegant solution.  my testing indicates this gives me the desired effect that local accounts can login and AD domain accounts can only log in if they are in the LinuxAdmins group. :cool:

-axelf

---

### Post by n0cturnal on 2008-01-02
> **AxelF said:**
>  i posted the full result here in case it helps someone else.
-axelf

Thanks very much AxelF, your code has been of huge help to me. Works a treat.

Many thanks,
n0c

---

### Post by AxelF on 2008-01-31
hi n0cturnal!

i am really glad it helped you out, good to know it is useful to someone other than myself. :)

-axelf

---

