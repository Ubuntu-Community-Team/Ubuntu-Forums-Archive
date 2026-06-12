---
title: "Cannot ssh to NFS-connected machine: permission denied"
date: 2011-04-18
forum: Security
---

### Post by neoAnderson on 2011-04-18
Hi all,

I am having a strange problem. I have, say, 10 machines, connected via NFS and NIS. There's a server which exports the /home using NFS, and exports the user names using NIS. All machines are working fine. I am able to ssh to the machines remotely and get my work done.

Recently though, one of the machines (say M, for easy reference) would not allow any other machine on the NFS network [or outside the NFS network] to ssh into it. Every time an ssh attempt is made, 3 IP addresses [including the machine from which an ssh attempt was being made] are added to the /etc/hosts.deny file on M, and the error message on the other machine shows 'permission denied' after the password is entered. I tried using various options that ssh provides, but I cannot figure it out. I also tried uninstalling and reinstalling openssh-client and openssh-server on M, but it didn't change anything.

Another point to note is this: another user made use of M before, for a while, by disabling ssh passwords - so he could access M without having to enter his ssh password. That individual can still log in to M. All others who require to enter a password cannot ssh into M.

So that's my problem. Any help or pointers will be really appreciated. Thanks!

Neo.

---

### Post by Jive Turkey on 2011-04-18
Check the settings in /etc/denyhosts.conf and /etc/ssh/sshd_config.
The former appears to only give one login attempt before banning an IP, that's too low IMO.  The latter may be set to only allow certain users/machines and the service needs to be restarted after changing the line "PasswordAuthentication no" to "PasswordAuthentication yes".  Also check that sshd is running on the server and there are no firewall rules blocking your client(s).


Consider an entry in /etc/hosts.allow for the services/machines that need access.

---

### Post by bodhi.zazen on 2011-04-18
Sounds as if M is running some service or active response to ssh connections.

Probably denyhosts, but could be psad or other service.

Check the logs on M

---

### Post by Tmcarr on 2011-04-18
Sounds like there might be multiple possible issues here.

The user who previously used M probably used SSH keys, which is why it still works. 

It sounds like you are trying to make thin clients on the hosts connected to the NFS. IF this is the case, you might try adding SSH keys to the NFS for every machine attached to it. This might fix your issue.

---

### Post by neoAnderson on 2011-04-19
> **Jive Turkey said:**
> Check the settings in /etc/denyhosts.conf and /etc/ssh/sshd_config.
The former appears to only give one login attempt before banning an IP, that's too low IMO.  The latter may be set to only allow certain users/machines and the service needs to be restarted after changing the line "PasswordAuthentication no" to "PasswordAuthentication yes".  Also check that sshd is running on the server and there are no firewall rules blocking your client(s).


Consider an entry in /etc/hosts.allow for the services/machines that need access.

Hi there [and all others], 
thanks for your response. Let's resume saying that the machine with the problem is M and my other machine is, say, P.

I checked the /etc/denyhosts.conf on M and it says allowed attempts 5 for invalid users and 10 for valid users, and 1 for restricted users. I checked the files on M in /var/lib/denyhosts and my NIS username was added to users-invalid as well as my IP address (of P) was added to hosts-restricted. P's IP however is also in the hosts-valid file. 

/etc/ssh/sshd_config already has PasswordAuthentication set to Yes.

I cleared P's IP from these files on M, I cleared my username from these files on M, I cleared P's IP from hosts.deny on M, and then I restarted ssh and denyhosts on M. But the problem hasn't gone away. I try to make one login attempt from P to M, and it adds my username to /var/lib/denyhosts/users-invalid, adds P's IP address to /var/lib/denyhosts/hosts-restricted, and adds the IP also to /etc/hosts.deny.

/var/log/auth.log says [message from ssh] failed login for my username because tcsh does not exist: which is strange because both machines are running tcsh. 

I also added P's IP to /etc/hosts.allow but it does not do anything. What's funny is that P's IP address is in both /var/lib/denyhosts/hosts-restricted and /var/lib/denyhosts/hosts-valid. The suspicious-logins file in that folder is empty.

The other person who did the ssh-keys thing and could log in to M without password, and all the other stuff, points to the conclusion that password authentication for ssh is failing. Is there a possibility that M has been cracked?

Do you guys have any further suggestions?

---

### Post by bodhi.zazen on 2011-04-19
> **neoAnderson said:**
> Do you guys have any further suggestions?

It is probably denyhosts.

Shut denyhosts off and try again =)

---

