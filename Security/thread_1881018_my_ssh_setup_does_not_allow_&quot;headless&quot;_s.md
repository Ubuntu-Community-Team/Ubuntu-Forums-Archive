---
title: "my ssh setup does not allow &quot;headless&quot; server management"
date: 2011-11-14
forum: Security
---

### Post by nosmadar on 2011-11-14
Probable newbie question here:
Running 10.4.3 server on an Intel i5 box.  Also have laptop running Karmic that I'm trying to use for remote administration. I've read the sticky notes and have got the ssh connection defined to use a key rather than a password. But it does not work in a way that makes sense:  Unless I have already logged into the console directly (i.e. a Monitor connected directly to the server) as the same user, I get a message:  "Permission Denied (Public Key)" when I try to log in with ssh from the laptop to remote manage the server.  I'm assuming that I must have done something wrong but not sure what.
Also if I'm connected via ssh from the laptop, but I then log out of the console, when I try to log in from the console again, I'm told the password is invalid not matter how slowly and carefully I type it.  So it's as if the ssh connection changes how authentication works for this user.  Which admittedly does make some sense, but I want to be sure it's normal.

---

### Post by papibe on 2011-11-14
It looks like you made a little mistake in the process. You can reset all keys by removing the proper directory on both ends:
```
rm -rf ~/.ssh
```
Here's a [tutorial]("http://principialabs.com/beginning-ssh-on-ubuntu/") that I found very detailed. It starts covering the very basics, but the section called "Public-Key Authentication" should offer you the information you need.

Hope it helps, and tell us how it goes.
Regards.

---

### Post by dirtrider1 on 2011-11-15
By the way you worded your question it sounds as if you may have not created your client key pair or added your pubkey to the server correctly. Check the authorized key file on the server and see if your client public key was added to the server. If not you will need to add it,(make sure you have created the key pair on the client first). I use [ssh-copy-id username@ip_address] to easily add the key to the server. Then check again to see if your client pubkey was added to the server authorized key file. Then once it works you can disable password authentication.

---

### Post by nosmadar on 2011-11-15
I think I know what the problem is.  When I was setting this up, I ran into a problem where I could not get the key to copy with the remote copy command. (I might have disabled password auth in ssh too soon.) So I figured out how to mount a USB memory stick and copy it that way. But the .ssh directory wound up in /home/<user>, NOT in "/".  Which might very will explain why it's only accessible if the <user> is already logged in.  So perhaps all I need to do is move the .ssh directory from /home/<user> to "/" ?

---

### Post by spynappels on 2011-11-15
No, it should be in /home/user

The public key is user specific. It sounds like dirtrider1 is correct. You need to create the key on the machine you are using for remote management, then copy the public key to the ~/.ssh/authorized_keys file for the user you want to log in as on the server.

---

### Post by nosmadar on 2011-11-15
> **spynappels said:**
> No, it should be in /home/user

The public key is user specific. It sounds like dirtrider1 is correct. You need to create the key on the machine you are using for remote management, then copy the public key to the ~/.ssh/authorized_keys file for the user you want to log in as on the server.

I think I found my problem, here's an excerpt from the Ubuntu SSH doc:
"Encrypted Home Directory

If you have an encrypted home directory, SSH cannot access your authorized_keys file because it is inside your encrypted home directory and won't be available until after you are authenticated. Therefore, SSH will default to password authentication."

<sighs, looking sheepish>  And yes, my home directory IS encrypted.

So let me run off and try the suggested work around.

---

### Post by nosmadar on 2011-11-15
Hi, just wanted to confirm that the fix suggested in the documentation worked.  Link attached.

Thanks Again, this was driving me crazy because, at the same time, I was unable to get the server to boot with a Monitor connection from a KVM switch. Now both issues are fixed.

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys#Troubleshooting]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys#Troubleshooting")

---

### Post by spynappels on 2011-11-16
Cool, glad it worked, sometimes you need to find the right question to ask, and then the rest is easy.

Didn't realise that about the encrypted home directory, but makes perfect sense when I think about it.

---

