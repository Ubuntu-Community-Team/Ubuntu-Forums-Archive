---
title: "Security consideration when enabling remote loggin over ssh"
date: 2010-02-18
forum: Security
---

### Post by mahela007 on 2010-02-18
I'm going to enable remote loging in on my desktop PC using X over ssh. What must I do to protect my system from would be intruders ? With the default configuration wouldn't they be able to access my PC?  My PC connects to the internet from behind a router.

---

### Post by bodhi.zazen on 2010-02-18
With ssh I advise you use keys, disable passwords, and either install denyhosts / fail2ban, or a set of rules for iptables.

[SSH/OpenSSH/Keys - Community Ubuntu Documentation]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") 

[SSH/OpenSSH/Configuring - Community Ubuntu Documentation]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring")

---

### Post by 2hot6ft2 on 2010-02-18
> **bodhi.zazen said:**
> With ssh I advise you use keys, disable passwords, and either install denyhosts / fail2ban, or a set of rules for iptables.

[SSH/OpenSSH/Keys - Community Ubuntu Documentation]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") 

[SSH/OpenSSH/Configuring - Community Ubuntu Documentation]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring")
+ 1 That's what I did. That way you can disable password login entirely. See the guide in my sig for tips and use RSA instead of DSA keys with the 4096 setting to make it even more secure.

---

### Post by mahela007 on 2010-02-18
Thanks.. I"ll try what you guys said

---

