---
title: "SSH Authentication rules on a per user basis"
date: 2008-07-22
forum: Server Platforms
---

### Post by viordiasko on 2008-07-22
I have a Hardy server running ssh. I want to allow one particular client (via a script from a fixed IP) access using an empty passphrased key. All others are to be prompted for their key passphrases.

Can I configure ssh to do this ?

---

### Post by eentonig on 2008-07-22
Yes you can. Check your ssh config file for directives.

Let me know if you need additional help.

---

### Post by viordiasko on 2008-07-22
> **eentonig said:**
> Yes you can. Check your ssh config file for directives.

Let me know if you need additional help.

Sorry, I will need help.

When creating a ssh key, leaving the passphrase empty gives you passwordless login unless
&#8216;PermitEmptyPasswords no&#8217; is active in the sshd_config.

But that is for all users. I just want to permit one users key to be passphrase-less

---

### Post by MJN on 2008-07-23
I think there may be some confusion here...
 
The passphrase to the key is an issue at the client end, i.e. the passphrase serves to allow access to the private key in its unencrypted form. The server does not care, or indeed know, whether or not the client/user private key has a passphrase or not - it just needs to see the result of a hashed value using that key.
 
Hence, what I am trying to say is, remove the passphrase from the particular client/user key and you're sorted - there is no need to make any modification to the server SSHD config.
 
Mathew
 
(Note: The PermitEmptyPasswords directive is not applicable as it relates only to password-authenticated logins, not key-based)

---

### Post by sp0nge on 2008-07-24
Please keep posting on your progress. 

I am also running an ssh enabled server and am working to secure it as best I can. I will be working to specify which users can log in via ssh and from which IPs, any input would be much appreciated.

---

### Post by MJN on 2008-07-24
> **sp0nge said:**
> I will be working to specify which users can log in via ssh and from which IPs, any input would be much appreciated.

Check out the following for one way of achieving that specific requirement:

[http://www.cyberciti.biz/tips/openssh-root-user-account-restriction-revisited.html](http://www.cyberciti.biz/tips/openssh-root-user-account-restriction-revisited.html)

Mathew

---

### Post by sp0nge on 2008-07-24
Thanks, MJN, for that link, it was very helpful. I have configured access.conf just the way I need it!

---

