---
title: "I would like to know how to apply security to Ubuntu."
date: 2023-12-27
forum: Security
---

### Post by rnakama on 2023-12-27
I would like to know how to apply security to Ubuntu. Is the command below correct to apply the security patch?


apt update && apt install '~U ~Asecurity'

---

### Post by ian-weisser on 2023-12-27
That command will update your local database of available deb packages, then produce an error message.
Producing an error message seems unlikely to be your intended goal.

A stock install of Ubuntu will, if connected to the internet, install most security patches completely automatically at least twice daily. You don't need to trigger the action. You don't need to do anything. "automatically" means just that.

Some security patches are not automatic for various reasons.

You can review all automatic upgrades, including security patch upgrades, in your apt log: /var/log/apt/history.log

---

### Post by MAFoElffen on 2023-12-27
> **rnakama said:**
> I would like to know how to apply security to Ubuntu. Is the command below correct to apply the security patch?
```

apt update && apt install '~U ~Asecurity'

```

As Holger explained, no.

What I'm curious about, is what do you mean by "apply security"? 

Do you mean apply a CVE Security Vulnerabilty Patch? For those, most are automatic, though some need certain things done. I usually look at the CVE notices.

Do you mean doing a security audit to harden a system for commercial or Govt CIS/STIG compliance? That would be the CIS?STIG audit or installing 'Lynis' to do a lower level security compliance audit.

I'm thinking maybe not... But thought to ask, for the just-in-cases.

---

### Post by deadflowr on 2023-12-27
moved to security

---

### Post by TheFu on 2023-12-28
If all you want is security patches, you get those automatically by doing normal patching via any APT interface provided the system and repos involved are currently supported.  On install, there are usually a few specific packages that aren't *supported*.  

If you install using PPAs or Snaps or flatpaks or AppImages or manually with .deb, or install files, then all bets are off. You've accepted this responsibility.  Stay with the core repos only, don't use any *funny* extra installations, stay on LTS releases for 3 yrs (or 5yrs if Servers), and you'll get all the security patches.

As for security configuration, that's up to you. There's no magic to make that happen, since many of those more secure, restrictive, settings, break things normal users expect to "*just work*".

As other have said, stay patched and if you want more security, then find the guide(s) appropriate to the level of security you seek.  I think the 22.04 versions of those security guides aren't published yet.  The 20.04 version are, but probably only for 2 yr old releases, so you'll need to use your judgement and skill to decide which specific items impact the system you have.

[https://github.com/lfit/itpol](https://github.com/lfit/itpol) is the Linux Foundation's Workstation Security Guide, for example.
STIGs for Ubuntu 22.04 aren't ready, but here are where they will be placed and other guides: [https://ubuntu.com/security/certifications/docs/2204](https://ubuntu.com/security/certifications/docs/2204)

---

### Post by rnakama on 2024-01-04
Thank you everyone for your replies. I am very grateful.
And I'm sorry for the insufficient explanation.

For example, I don't know the command to implement a security patch on Ubuntu that is equivalent to the Red Hat Enterprise Linux command below, so I would like to know.


yum -y update --security

---

### Post by TheFu on 2024-01-04
According to the manpage, apt-get doesn't have an equivalent command.  You would need to get a list of updates, determine if they are security related, then choose to install each, hoping the dependencies don't change if you don't include other package updates.

Google found this answer: [https://askubuntu.com/questions/194/how-can-i-install-just-security-updates-from-the-command-line](https://askubuntu.com/questions/194/how-can-i-install-just-security-updates-from-the-command-line)
```
apt-get -s dist-upgrade | grep "^Inst" | \
    grep -i securi | awk -F " " {'print $2'} | \
    xargs apt-get install
```

I've never used it, so YMMV.  I'd probably use a 1-line perl command rather than 2 greps and an awk myself, but have at it.

Why are they different than that other distro's command?  APT and RPM are different with different audiences/users.

---

### Post by SeijiSensei on 2024-01-04
Why not just upgrade everything? Why limit yourself to security upgrades?

---

### Post by Dennis N on 2024-01-04
If you want to see exactly which updates are security updates, use Software Updater which segregates the updates as "Security Updates" or "Other Updates". See Screenshot. It handles them all.

---

