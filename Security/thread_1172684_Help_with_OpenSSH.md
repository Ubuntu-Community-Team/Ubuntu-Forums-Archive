---
title: "Help with OpenSSH"
date: 2009-05-28
forum: Security
---

### Post by Dollar Bill on 2009-05-28
I give up.  I need help setting up OpenSSH. 
I have a Ubuntu desktop trying to connect to a Ubuntu server.  Both 9.04. 
After working on this for many days it suddenly started working.  I don't know why.  It worked for two days.  Then it quit working.  I still don't know why.  (I've worked on other people's problems enough to not say "I didn't change anything") 
Oh, the same keys were working on to different clients, then they quit working on both clients.
In verbose mode on the client there are no error messages.  It sees and accepts the keys from the host.  On the server the only error messages are:
Failed publickey for xxx from 192.168.1.100 port 52494 ssh2
debug3: mm_answer_keyallowed: key 0xb8a8f4f8 is not allowed

I've checked the permissions on the path to ~/.ssh/authorized_keys on the host and to ~/.ssh on the client.

Anyone have suggestions?

Thanks.

---

### Post by statistic on 2009-05-29
Since it looks like you're using authorized keys to do the login, are you able to login by typing the password? 

Also if you're trying to login as root, your sshd.conf may not allow that.

---

### Post by bodhi.zazen on 2009-05-29
Please post the contents of /etc/ssh/sshd_config plus the output of 

"ssh --vv" using your key.

Also are you using either apparor or selinux ?

My initial thought is that the key is blacklisted, you may want to try generating a new key ;)

---

### Post by Dollar Bill on 2009-05-30
I am not using root to connect.
I am not using AppArmor or SELinux that I know of.  The server is the standard 9.04 install with patches applied.
I did modify the sshd_config per the various HowTo's.
I did try regenerating new keys but it didn't make a difference.
I don't find a blacklist file to check.
I have attached the debug files and sshd_config.
Thanks.

---

### Post by roman_platonov on 2009-05-30
just flush all known keys on client

---

### Post by albinootje on 2009-05-30
> **Dollar Bill said:**
> 
I did try regenerating new keys but it didn't make a difference.


I'm not sure whether this is normal behavior :
```

debug2: key_type_from_name: unknown key type '-----BEGIN'
debug2: key_type_from_name: unknown key type 'Proc-Type:'
debug2: key_type_from_name: unknown key type 'DEK-Info:'
debug2: key_type_from_name: unknown key type '-----END'
debug1: identity file /home/xxx/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-4096
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-4096
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug2: key_type_from_name: unknown key type 'Proc-Type:'
debug2: key_type_from_name: unknown key type 'DEK-Info:'
debug2: key_type_from_name: unknown key type '-----END'

```
Is it possible that your file system needs to be checked ?
You said that there were no changes, but what about reboots ?

---

### Post by Rubicon_82 on 2009-05-30
Hi,

The problem may be caused by the authorized_keys file (as this is the last thing mentioned in the server debug trace before the key is rejected).

@OP:

Can you please verify that the file '~/.ssh/authorized_keys' exists on the **server**, and that it contains your client-side public key '[client]:~/.ssh/id_rsa.pub' or similar.

If the file does not exist, you can create it by running 'ssh-copy-id' from the client side:
```

ssh-copy-id [user]@server
```

Alternatively, you can copy your public key to the server by other means and manually add it to your authorized_keys file.

---

### Post by Dollar Bill on 2009-05-30
Previous attempts to solve this problem included deleting the records out of the authorised_keys file and regenerating the keys.  I also rebooted the server a couple of times. I set up this server to learn.  Getting ssh working is the first thing I tried.  I could just delete the partition and reinstall the server and not cause too much work but I would like to solve the problem. I have read and definitely learned about ssh, because I've been trying to solve this for two weeks before asking for help.  I am ready to either reinstall the os or take a hammer to it.  I haven't decided which yet.

If there is something to try like "flushing the keys" you will have to show me the commands.

Thanks.

---

### Post by Rubicon_82 on 2009-05-30
Hi Dollar Bill,

Does your server use ecryptfs-utils to create an encrypted home directory? If so, please make sure that your authorized_keys file is not encrypted.  If it is, the ssh-server will be attempting to access it before you log in (while the file is still encrypted).

See Bug 362427 for more details [https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/362427](https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/362427)

---

### Post by Dollar Bill on 2009-05-31
Rubicon_82,

You solved the problem.  I followed the instructions in the link you cited and ssh is working.  Thank you.

---

