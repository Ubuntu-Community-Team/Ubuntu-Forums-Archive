---
title: "root user hostbased ssh failure"
date: 2010-06-28
forum: Server Platforms
---

### Post by dmr123 on 2010-06-28
Hi all,

I'm setting up hostbased authentication between several hosts. All but one are centos servers (w/ openssh 4.3p2), and the other one is running 10.04LTS (openssh 5.3p1). Between the centos boxes, everything works properly. I can ssh from any user into any of the other nodes as that same user. From the centos boxes, I can ssh into the 10.04 host as any user *other* than root without being prompted for a password. Once I try as root, the hostbased stuff fails and I'm asked to provide a password. 

> 
userauth_hostbased mismatch: client sends <shorthostname>, but we resolve <IPADDR> to <fqdn>
   debug2: auth_rhosts2: clientuser root hostname <fqdn> ipaddr <IPADDR>
   debug1: temporarily_use_uid: 0/0 (e=0/0)
   debug1: restore_uid: 0/0
   debug1: temporarily_use_uid: 0/0 (e=0/0)
   debug1: restore_uid: 0/0
   Failed hostbased for root from <IPADDR> port 45258 ssh2
I have no idea what could be causing this. I'm using precisely the same ssh configuration on the 10.04 box as I am on the centos boxes. If it didn't work for all users, I might have some clue where to start looking, but it's only root that fails.

My question boils down to this: I'm new to debian/ubuntu distributions, so is there some mechanism not present in RedHat-like systems that I'm not aware of that's preventing this from working on the 10.04 box? I initially thought it might be some weird PAM-ism (securetty or some such), but I've turned off PAM to no effect. Maybe there's some other silly little config option in a file somewhere I need to flip?

Any ideas?

---

### Post by windependence on 2010-06-28
Check the versions of OpenSSH on the boxes. It shouldn't make any difference but who knows? I can't think of much else that would cause the problem.

-Tim

---

### Post by WinstonChurchill on 2010-06-28
This is a bad idea - if you want to log in to SSH without having to type in passwords, use public key authentication, and save the private key as ~/.ssh/id_rsa on the client machine without an encryption passphrase; that nets the same result and is much more secure. Logging in as root isn't a great idea anyway (As has been made abundantly clear in much Ubuntu documentation...)

That said, I think this could be one of a couple things.

Possible thing 1: PermitRootLogin isn't set in sshd_config - you need the following option (I don't know the default setting in 10.04's config):```
PermitRootLogin yes
```Possible thing 2: There is some issue with sshd's reverse DNS resolutions - change this option in sshd_config:```
UseDNS no
```This option exists partially to make host-based authentication (relatively) more secure, but disabling it might fix your issue.

---

### Post by dmr123 on 2010-06-28
> **WinstonChurchill said:**
> This is a bad idea - if you want to log in to SSH without having to type in passwords, use public key authentication, and save the private key as ~/.ssh/id_rsa on the client machine without an encryption passphrase; that nets the same result and is much more secure. Logging in as root isn't a great idea anyway (As has been made abundantly clear in much Ubuntu documentation...)


In this particular  instance there are no security issues (not already present and mitigated by use of a custom pam module) with doing host based auth, and in fact is required for the proper functioning of this cluster. While I might agree in principle that root logins are "bad", I think the documentation is aimed more towards typical use cases and not those outlier cases like the one I'm setting up. 

> **WinstonChurchill said:**
> 
That said, I think this could be one of a couple things.

Possible thing 1: PermitRootLogin isn't set in sshd_config - you need the following option (I don't know the default setting in 10.04's config):```
PermitRootLogin yes
```Possible thing 2: There is some issue with sshd's reverse DNS resolutions - change this option in sshd_config:```
UseDNS no
```This option exists partially to make host-based authentication (relatively) more secure, but disabling it might fix your issue.

The default setting for permitrootlogin in 10.04 is yes.  I can log in properly with the root password, so I don't think that's the problem. I'll play around with usedns tomorrow. I don't know why, even with the mismatch, it would work with non root users, though it's worth a shot. Perhaps there was a change in openssh 5 to change this behavior. Thanks for the help.

---

