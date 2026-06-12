---
title: "Ubuntu Server using Winbind authentication instead of SSSD"
date: 2021-10-25
forum: Server Platforms
---

### Post by dacrane91 on 2021-10-25
Hi everyone,

I am new to Linux administration and have run into an issue that I hope someone can help with.

Last week I setup an Ubuntu server and joined it to our domain using SSSD authentication. This worked well and I was able to SSH into the server using my domain credentials, but after installing updates it is no longer accepting domain logins.

I have set it up to use SSSD to authenticate and when I run

```
realm discover {domain}
```

I get the following output:

```
<domain>  type: kerberos
  realm-name: <Domain>
  domain-name: <Domain>
  configured: kerberos-member
  server-software: active-directory
  client-software: sssd
  required-package: sssd-tools
  required-package: sssd
  required-package: libnss-sss
  required-package: libpam-sss
  required-package: adcli
  required-package: samba-common-bin
  login-formats: %U
  login-policy: allow-permitted-logins
  permitted-logins:
  permitted-groups: <domain Groups>

```

However, when I check /var/log/auth.log I am getting this error, indicating it is attempting to use winbind to authenticate, rather than SSSD:

```
Connection from <IPAddress> port 63369 on <IPAddress> port 22pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=<IPAddress>  user=<username>
pam_winbind(sshd:auth): getting password (0x000003c8)
pam_winbind(sshd:auth): pam_get_item returned a password
pam_winbind(sshd:auth): could not lookup name: <DOMAIN>\<domainGroup>
pam_winbind(sshd:auth): cannot convert group <DOMAIN>\<domainGroup> to sid, check if group <DOMAIN>\<domainGroup> is valid group.
Failed password for <username> from <IPAddress> port 63369 ssh2
```

The same thing also happens if I try to log in to the server directly from the VMWare console.

I know the group names are correct(I copied and pasted straight out of AD after creating the groups) and this was working before updates were installed.

I have also tried replacing the <DOMAIN>\<domainGroup> in /etc/pam.d/common-auth with the group SID and <DOMAIN\<SID>. This changed the error output, but still failed(it treated the SID as a group name).

I suspect that somewhere it is set to use winbind, rather than SSSD. Does this sound like a possibility? Any other suggestions?

I have been searching on various forums and Google, but no luck so far. Similar issues all seem to be winbind errors where they want to use winbind, not SSSD.

Thanks in advance!

Edit: I was able to resolve this by editing /etc/pam.d/common-auth and changing pam_winbind.so to pam_sss.so. I am not sure how this file got changed, but once I set it back to SSS and rebooted it started working again.

---

### Post by LHammonds on 2021-10-25
Seems like having a method to monitor changes to key files in /etc would be a good thing to have running...maybe not only detect write changes but also to email a report of what changed.

I can envision a way to do this with a backup /etc folder and a script that compares each of the files but maybe there is a tool already created to do that.  I'll have to research that.

LHammonds

---

### Post by MAFoElffen on 2021-10-27
Maybe as simple as a scheduled script (as a job) using dif or comparison between the two... if a certain change occurs, then notify... I email an admin email account with reports and notifications. Urgent is texted to me directly. You can do the same in Domain audits in WIN, which I wrote PowerShell scripts for...

I helped my son (who is a Systems Engineer) to learn C#, Linux Bash, SED, and using SSH to create a Citrix Management app replacement to manage over 1000 of his managed, multi-platformed servers (Mostly WIN). There's a lot you can do, in so many ways, between systems. It just depends on how you want to approach that, and with what toolsets. 

My family is very IT intensive. Very entertaining family dinners between 3 generations involved in IT.

---

