---
title: "Best way to manage SSH key pair for sftp using Open Office?"
date: 2008-08-03
forum: Security
---

### Post by MountainX on 2008-08-03
What is the right way to work around this Open Office bug?

The problem is described in this bug report:
[https://bugs.launchpad.net/openoffice/+bug/41985](https://bugs.launchpad.net/openoffice/+bug/41985)

A solution is offered in this comment:
[https://bugs.launchpad.net/openoffic...85/comments/18](https://bugs.launchpad.net/openoffic...85/comments/18)

Basically it says to make a passwordless SSH key pair.

What is the most secure way to go about implementing this solution? Can I store the private key inside GPG via Seahorse? If so, how?

Also, does setting up an SSH key pair between a client and server allow login in both directions? In other words, could I put the private key on the server and still solve my Open Office problem?

Thanks.

---

### Post by kevdog on 2008-08-03
What do you really want to do?  How about doing it the long way -- by using sftp/scp to download the file to your computer, make changes, and then reuploading the file to the server (which is similar to rsync if you want to make mirrors).

---

### Post by MountainX on 2008-08-03
> **kevdog said:**
> What do you really want to do?  How about doing it the long way -- by using sftp/scp to download the file to your computer, make changes, and then reuploading the file to the server (which is similar to rsync if you want to make mirrors).

Hi! Unfortunately, the long way won't meet the requirement. My goal is to get Open Office to work over the sftp connection. It sounds like the passwordless SSH key pair will solve that OO bug, but I just don't understand the security ramifications at all.

---

### Post by kevdog on 2008-08-03
The security ramification of a unprotected private key is that if anyone gets ahold of the private key -- they could use it.  If you have a safe place of storage for your private key this may not be much of an issue for you at all. It just depends.

---

### Post by MountainX on 2008-08-03
> **kevdog said:**
>  If you have a safe place of storage for your private key ...

I was thinking I'd store my SSH private key in GPG. Will that work?

(I could also keep it in an encrypted partition, I guess. I know that will work but it doesn't seem quite as secure given that my computer is always on.)

---

### Post by hyper_ch on 2008-08-04
sshfs and mount the remote filesystem in the local one...

---

### Post by kevdog on 2008-08-04
Yes you could store your ssh private key in gpg, but just remember that you would need access to the ggp executable to decrypt the key so you could use it.  If you are working with linux boxes, gpg is probably on the machine by default.  With windows machines, this might not be the case.

---

### Post by MountainX on 2008-08-04
> **hyper_ch said:**
> sshfs and mount the remote filesystem in the local one...
Thanks! I think I'll take this approach.

---

### Post by Biochem on 2008-08-04
+1 for sshfs

However, I found that saving a file that already exist to be sometime problematic with sshfs. 2 easy and safe workaround: delete the original before saving or use save-as and save under another name.

---

### Post by hyper_ch on 2008-08-04
I use sshfs regurarly for web-coding... never had a problem with safing.

---

### Post by Biochem on 2008-08-04
> **hyper_ch said:**
> I use sshfs regurarly for web-coding... never had a problem with safing.

used to always happen to me with openoffice in 7.04. Mayba I miss-configured something. Anyway, now I use nfs over openvpn with no problem.

---

### Post by MountainX on 2008-08-05
> **Biochem said:**
>  now I use nfs over openvpn with no problem.

Is nfs + openvpn easier to set up than nfs4 with kerebos? Which is better? (I don't need my traffic encrypted, but I would like to ensure that unauthorized users cannot log in to the nfs server.)

---

### Post by Biochem on 2008-08-05
> **MountainX said:**
> Is nfs + openvpn easier to set up than nfs4 with kerebos? Which is better? (I don't need my traffic encrypted, but I would like to ensure that unauthorized users cannot log in to the nfs server.)

I find openvpn pretty easy to configure for small virtual network (I never did one with more than 6 users). The authentication is done with signed rsa key which if I remember well can be password protected if you want. And traffic is fully encrypted which is a must if you are accessing your share from the internet. The other advantage of a vpn is that you can have access to your whole lan network if you want not just a single pc.

NFS is then just the same as in a lan but with the VPN addresses. You can set the vpn ip to be static for all clients so setting different share for different user is not a problem.

Beware though that the openvpn documention is extensive and can be overwhelming. But the sample files are pretty complete.

---

