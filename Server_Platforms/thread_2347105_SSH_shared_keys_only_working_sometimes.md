---
title: "SSH shared keys only working sometimes"
date: 2016-12-21
forum: Server Platforms
---

### Post by courtney2 on 2016-12-21
I have been having problems with SSH and preshared keys on Ubuntu Server 16.04. I created a preshared key via the Ubuntu Help Wiki. It works, however sometimes it requires I type in a password and won't use the preshared key method until I do. I have kept password login enabled because I have wasted a lot of time before having to visit the server site locally to edit configs to allow password login, login, disable password login and then get back to business. The point of preshared keys is to disable password login and only allow the key holder to login, however, the system seems broken on Ubuntu. Is there a configuration I am missing? It seems to be happening randomly and also guaranteed not to work after a reboot

---

### Post by The Cog on 2016-12-21
I think you will have to explain in more detail what you are doing. I don't think there is anything wrong with pre-shared keys, so there must be some kind of problem with the configuration or with how you are using it.

The basic idea is that you have a public key that identifies you stored in ~/.ssh/id_rsa.pub, and this is stored (appended to) .ssh/suthorized_keys in the appropriate home directory on the server. If you recreate your local keys at any time, you will then have to correct the key stored in the server of course.

You should always be able to log in without a password once the keys are set up properly, and only when passwordless login is reliable should you disable password logins.

---

### Post by courtney2 on 2016-12-21
Hi The Cog,

I'm doing exactly what you described, so I apologize for not being clear about that. I have things set up the way you mentioned (which to my understanding is the same as this setup process here: [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)) and like I said, at random times and after reboots I will have to do password login via SSH for any pre-shared key to work. I hope I am saying this in a way that makes sense. I didn't recreate any keys so that shouldn't have anything to do with this issue. My only change right now is that I am not accessing SSH via the default port 22

---

### Post by kevdog on 2016-12-21
How are you trying to ssh into the box?  Can you list the command?

---

### Post by Graham_Willis on 2016-12-22
Check the logs. Primarily /var/log/auth.log, but syslog, kern.log, dmesg also can contain information worth looking. Post the relevant lines here if you're confused, but remember to stripe them off possible sensitive data.

---

### Post by courtney2 on 2016-12-23
ssh -p (port # over 9k) courtney@ip_address

I'm trying to follow the pattern of when it will require a password and when it won't, and so far my guess is it needs to have a password login first when I try to ssh in from new networks

---

### Post by darkod on 2016-12-23
How did you move the key to the destination server? Using ssh-copy-id?

If you did manual copy-paste and maybe even created the authorized_keys file yourself, check the permissions on the .ssh folder and the authorized_keys file. The folder has to have 700 and the file 600. That's requirement for ssh keys to work correctly. Also the owner has to be the user you are trying to login as, for example courtney:courtney.

Also if you were pasting the key manually make sure there are no extra characters like spaces, etc...

---

### Post by courtney2 on 2016-12-23
darkod,

I did ssh-copy-id to the server, my .ssh directory (where it is stored) has permissions 700 and authorized_keys is 600 on the server. The user on my local machine and the server are both courtney:courtney and my user and group id are both the same. Is there are particular permission that needs to be set in place for my id_rsa, id_rsa.pub and known_hosts on my client machine?

---

### Post by darkod on 2016-12-24
No, the permissions of the id_rsa would be correctly set by ssh-keygen. I was asking for .ssh and authorized_keys because sometimes I needed to create them manually and in such case the permissions by default are not 700 and 600.

Did you access this server by ip_address from the start, from installation? Have you maybe reinstalled it or changed IP? Because in such cases in your client known_hosts there will be records of the "old" server too and it can complain. In such case you have to clean all old unnecessary entries.

And another important thing is: when creating the key on the client, did you use a passphrase or set it to blank? Because if the passphrase is not blank it is normal ssh to ask you for it when using the key. For a key authentication to really be without user intervention, the key needs to be created without passphrase.

---

### Post by courtney2 on 2017-01-07
I did yes, both with an external IP and internal IP. When I created the keys it was via the internal IP address. My addresses have not changed (though my external is dynamic), also I left it blank because I wanted to remove password entry altogether when using SSH (even though the password is for a different purpose). I haven't had to type in my password lately, so it seems the problem stopped? Used to be a simple shutdown would require I type in the password for it to "remember" the key but that hasn't been the case with these last 2 shutdowns. Perhaps this is more of just an anomaly than a real issue huh?

---

