---
title: "SSH Server Woes"
date: 2011-04-16
forum: Security
---

### Post by chak2005 on 2011-04-16
I've been using public key authentication with SSH for some time on my remote server. Today I had to give another user access and since I only allow keys no passwords, I had to generate another key pair for this individual. 

After all that was set up I tried logging into my server via SSH with the new key pair on the users account via putty in windows. Got the dreaded &quot;server refused our key&quot; so I did the normal check up, I:

-checked key and .ssh directory permissions
-verified the additional public key was formatted correctly in authorized_keys
-made sure putty was formatting the exported private key correctly
-I tried also amending the user name at the end of the public key and still no dice. 

After scratching my head for some time, I tried simply logging in under my account with the new key pair and it worked flawlessly. So here is my question how do I get this new key pair to work for another user besides myself? Do I need to create another .ssh directory on my remote server for their home directory? My gut is telling me this is simply a user/group issue with created this new account. Has anyone done this before?  **[edit] I figured out the problem. Upon creating new accounts all directories were created except .ssh. I created the .ssh directory and created an authorized_keys file. Upon setting up the correct user permissions, everything is working flawlessly. **

---

### Post by HermanAB on 2011-04-17
Howdy,

First make an account on the server for the user.  Don't use your own account for multiple users.

Upload the public key to the server:
```
$ scp keyfile.pub user@server~/.ssh/.

then you append it to the authorized keys file:
$ ssh user@server
$ cd .ssh
$ cat keyfile.pub >> authorized_keys
```

Note the double greater-than, which means append.

---

### Post by bodhi.zazen on 2011-04-18
I know this is marked as solved, but you can also use

ssh-copy-id

That command automates the process ;)

---

### Post by usatonycuba on 2011-04-19
> **bodhi.zazen said:**
> I know this is marked as solved, but you can also use

ssh-copy-id

That command automates the process ;)
+1

I also know this is marked as solved, but cant keep my mouse shoot .. but... :arrow:.. I did that in the past as @bodhi.zaze said ... it works perfect.

---

