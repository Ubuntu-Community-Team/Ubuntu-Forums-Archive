---
title: "Security Encryption for usernames, hashes and Samba transfers"
date: 2008-06-16
forum: Security
---

### Post by tuproxy on 2008-06-16
I just recently became fully aware of how easy it is to get the password hashes from a Samba server or a domain controller.  Breaking them is basically effortless with rainbow tables.  I guess this can only be done with administrative privileges, but these can be gained easily through a 1.7m iso file that resets all NT admin passwords.  So it is easy to elevate privileges and get passwords. 

Now, I want to know if there is a way around this or a way to secure this.  Can the username and password has be sniffed from the network when a user requests a file or logs onto a samba server?  When does the network transfer the username and hash?  Can this be secured by encrypting all network traffic somehow? I would think this may be possible through something like SSH from machine to machine.  So does that make the samba method overtly insecure?

Would encrypting the files that store the hashes make the system more secure?  Is this even possible?  Would encrypting the entire samba server OS be the key?  

Help me out here.  I'm a little fuzzy on the details but I have spotted the security risks and want to learn how to implement better security measures with samba. 

Also, how can someone grab windows passwords off hashes from a windows machine, via the network.  I think this is how my friend got ALL the usernames and passwords for his whole company and got his SYS admin in trouble for a lack of security.

If you can answer any questions here, I'd love it, or can you point me to a good guide for this?

---

### Post by hyper_ch on 2008-06-17
how do you get them from a samba server or domain controller?

---

### Post by cdenley on 2008-06-17
I'm not sure how easy it would be to retrieve password hashes from sniffed traffic. If you have an NT or NTLM hash, you can crack it easily. This means on a Windows machine, you can crack passwords for local accounts (not domain users).

I think there is a way to crack passwords for domain users who have their profiles cached on the client if you have admin privileges on the client.
[http://www.irongeek.com/i.php?page=security/cachecrack](http://www.irongeek.com/i.php?page=security/cachecrack)
[http://support.microsoft.com/kb/172931/](http://support.microsoft.com/kb/172931/)

If you have root privileges on the samba server, you can easily retrieve the hashes.
```

sudo pdbedit -L -w

```
If samba can see the hashes, so can root. You can encrypt /var/lib/samba, but this would only protect you from someone with physical access, and would require you to enter a password after a reboot.

Maybe your friend retrieved passwords by sniffing unencrypted web or e-mail authentication? If anyone knows about sniffing passwords from samba's authentication, I would like to hear it.

---

### Post by gaten on 2008-06-17
Samba over ssh is possible, but I honestly haven't tried it just yet. Here's some articles I found very quickly:

[http://www.security-hacks.com/2007/05/18/tunneling-smb-over-ssh-secure-file-sharing](http://www.security-hacks.com/2007/05/18/tunneling-smb-over-ssh-secure-file-sharing)
[http://www.ibiblio.org/gferg/ldp/Samba-with-SSH/](http://www.ibiblio.org/gferg/ldp/Samba-with-SSH/)

Hope that helps!

---

