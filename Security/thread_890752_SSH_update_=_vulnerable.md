---
title: "SSH update? = vulnerable"
date: 2008-08-15
forum: Security
---

### Post by ukjimbow on 2008-08-15
Alright all,

Why is it that I upgrade my system, get the latest packages etc. and still be vulnerable? As of right now SSH is not updated to the latest version and is still running ssh version 4.7? I did apt-get upgrade / dist-upgrade etc. and still will not upgrade?

Is this Ubuntu's problem on not up to date repositories or what?
Any way to upgrade ssh w/out downloading the tar and doing it manually etc.? 

Also, should I be worried about other things not up to date and vulnerable?  

I mean c'mon now, I do not want to be forced to switch to another flavour of Linux :(

---

### Post by jerome1232 on 2008-08-15
Ubuntu is not a rolling distro, versions get frozen every distro release (6 months).
What is particularly vulnerable about that version of ssh? or are you referring to the openssl vulnerability? If you are talking about the openssl vulnerability there's a sticky above this thread that tells you how to deal with that.

---

### Post by ukjimbow on 2008-08-15
> **jerome1232 said:**
> Ubuntu is not a rolling distro, versions get frozen every distro release (6 months).
What is particularly vulnerable about that version of ssh? or are you referring to the openssl vulnerability? If you are talking about the openssl vulnerability there's a sticky above this thread that tells you how to deal with that.
I'm using the latest version of Ubuntu 8.04 LTS. The vuln for the SSH is:

OpenSSH X Connections Session Hijacking Vulnerability --> [http://www.securityfocus.com/bid/28444](http://www.securityfocus.com/bid/28444)

OpenSSH ForceCommand Command Execution Weakness --> [http://www.securityfocus.com/bid/28531](http://www.securityfocus.com/bid/28531)

---

### Post by jerome1232 on 2008-08-15
If that's what you are concerned about you'd have to install it manually from their site, I have backports enabled and it's still the old version of ssh.

---

### Post by ukjimbow on 2008-08-15
> **jerome1232 said:**
> If that's what you are concerned about you'd have to install it manually from their site, I have backports enabled and it's still the old version of ssh.
It just amazes me it's Ubuntu's latest version and they dont update one of the most important services. ya know? Thats the scary thing about it. You want to be secure and you think you are but your not.

Know what I mean?

---

### Post by Dr Small on 2008-08-15
Better to switch to a rolling release distro (like Arch) if you want to have the lastest updates.

---

### Post by jerome1232 on 2008-08-15
Debian is also a rolling distro

---

### Post by cdenley on 2008-08-15
> **ukjimbow said:**
> I'm using the latest version of Ubuntu 8.04 LTS. The vuln for the SSH is:

OpenSSH X Connections Session Hijacking Vulnerability --> [http://www.securityfocus.com/bid/28444](http://www.securityfocus.com/bid/28444)

OpenSSH ForceCommand Command Execution Weakness --> [http://www.securityfocus.com/bid/28531](http://www.securityfocus.com/bid/28531)

What makes you think you're vulnerable?
[http://changelogs.ubuntu.com/changelogs/pool/main/o/openssh/openssh_4.7p1-8ubuntu1.2/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/o/openssh/openssh_4.7p1-8ubuntu1.2/changelog)
> 
* Patch from Red Hat / Fedora:
    - CVE-2008-1483: Don't use X11 forwarding port which can't be bound on
      all address families, preventing hijacking of X11 forwarding by
      unprivileged users when both IPv4 and IPv6 are configured (closes:
      #463011).

> 
* Backport from 4.9p1:
    - Ignore ~/.ssh/rc if a sshd_config ForceCommand is specified (see
      [http://www.securityfocus.com/bid/28531/info](http://www.securityfocus.com/bid/28531/info)).


---

### Post by jerome1232 on 2008-08-15
Nice information I was just thinking maybe it was worthwhile to purpose the new version for backports but it looks like the issue has been addressed

---

### Post by ukjimbow on 2008-08-17
Thanks guys....I guess i just need to keep on looking to see if new version are out there which Ubuntu does not update. Manual way it is! :(

Thanks for your time guys.

---

### Post by cdenley on 2008-08-18
> **ukjimbow said:**
> Thanks guys....I guess i just need to keep on looking to see if new version are out there which Ubuntu does not update. Manual way it is! :(

Thanks for your time guys.

Why would you compile the latest version from source? If you don't care about stability and want the latest version, install an alpha release of ubuntu intrepid with openssh 5.1. If you want a reliable version tested to work with your system and security patches backported (including the two you mentioned), use the repository.

Just because that version wasn't originally released with a security fix doesn't mean the ubuntu security team hasn't patched it.

---

