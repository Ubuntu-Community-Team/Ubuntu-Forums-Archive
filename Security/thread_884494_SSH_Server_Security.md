---
title: "SSH Server Security"
date: 2008-08-09
forum: Security
---

### Post by Dave_Connor on 2008-08-09
I have already edited ssh_config and sshd_config to have more secure settings. But instead of using key authorization would using a strong password work instead ?

---

### Post by HermanAB on 2008-08-09
If you make ALL your passwords longer than 9 characters then it should be OK.  (There are dictionaries out there that goes up to 8 characters.)  My passwords are 16 characters semi-pronounceable and my servers don't get compromised.

If you are bothered by dictionary attacks, change the SSH port number to something different.  That will throw the stupid script kiddies off.

Cheers,

Herman

---

### Post by Biochem on 2008-08-09
> **HermanAB said:**
> 
If you are bothered by dictionary attacks, change the SSH port number to something different.  That will throw the stupid script kiddies off.


Herman

It also help to keep your auth log lean and clean

---

### Post by ptn107 on 2008-08-10
For maximum security you should be using public key authorization rather than password authentication.

In sshd_config, set:
```
PubkeyAuthentication yes
PasswordAuthentication no
```

You will have to make sure each clients public key is appended to the servers ~/.ssh/authorized_keys file.

---

### Post by binbash on 2008-08-11
It will be ok but port knocking will cut brute force or similar attacks

---

### Post by Oldsoldier2003 on 2008-08-11
> **binbash said:**
> It will be ok but port knocking will cut brute force or similar attacks

IMO portknocking is an unnecessarily complicated way to thwart brute force. You can throttle connection attempts, use fail2ban (or denyhosts) and implement publickey authentication. I don't like using a nonstandard port but as said before- it will stop most of the "scriptkiddies". Another thing to consider is only allowing certain accounts ssh ability. 

Like Herman stated earlier, strong passwords on ALL accounts is normally good enough, especially if you implement one or more of the other methods to block bruteforcers.

---

### Post by Dave_Connor on 2008-08-11
I change my password to a stronger password, and tweaked with denyhosts to be more strict with authorization.

---

