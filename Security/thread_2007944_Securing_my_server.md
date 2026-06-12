---
title: "Securing my server"
date: 2012-06-21
forum: Security
---

### Post by weiinc on 2012-06-21
I need to expose a server to all the hackers on the Internet. It will only have one external function; to act as a rsync server. This server backs up stuff on my local network. Once a day I have another server at a remote location logon, rsync, and log off. Both are Ubuntu servers.

Other than a long complex username and password and using ssh around rsync what additional precautions would be wise?

Is there a howto or guide or cookbook to reference?

Mike

---

### Post by rukiaEnix on 2012-06-21
You can also use iptables to allow only the connection between those 2 computers and blocking all the other IP.

Use a different port for SSH.

Deny root access to SSH.

---

### Post by weiinc on 2012-06-21
Excellent plan.
I will do so.

Are you aware of any service that will test a system to see if it is secure?

---

### Post by rukiaEnix on 2012-06-21
The truth is that I don't know of any tool but logs always work ;)

---

### Post by weiinc on 2012-06-21
I could put up a blog saying this server is the most secure in the world then wait a minute.
[IMG]http://ubuntuforums.org/images/icons/icon10.gif[/IMG]
Thanks for the help.

Mike

---

### Post by lisati on 2012-06-21
You might want to look into something like [fail2ban]("https://help.ubuntu.com/community/Fail2ban")

---

### Post by CharlesA on 2012-06-22
> **lisati said:**
> You might want to look into something like [fail2ban]("https://help.ubuntu.com/community/Fail2ban")
Yep.

If you are only going to be using the box for rsync (over ssh, I presume). Use keys and only allow the IP of the remote machine access.

---

### Post by The Cog on 2012-06-22
Using password-less authentication for ssh is probably more secure than using long passwords. This uses long keys for authentication. 

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

but for automated access, you will need a key file without a passphrase set.

---

