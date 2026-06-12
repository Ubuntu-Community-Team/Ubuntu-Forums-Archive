---
title: "SSH  to root give permission denied"
date: 2007-06-20
forum: Server Platforms
---

### Post by techteacher on 2007-06-20
Hi!
        
I am using ubuntu 6.06 LTS on slave node of linux cluster. On master node FC6 is  loaded.  I want to make ssh from FC6 to ubuntu password free. For this i check the following command 

  My Ubuntu is logged in as user name " slave " and its hosts name is also slave.

ssh slave
    it ask me for password of 
root@slave password ://igive password and enter it give following message
permission denied
 root@slave password:
    
              How can i able to ssh a root user.
  pls, help me.

---

### Post by eentonig on 2007-06-20
You can, but I wouldn't do it.

root is one of those usernames *everybody* knows about. So every would be hacker will try this account as well. And so you gave him already half te solution on how to get in.

If you don't allow root to ssh, he has to guess your usernamen and your password.

Just do a sudo once you logged in.

---

### Post by galeron on 2007-06-20
1) Is your root account even enabled? Ubuntu disables the root account by default. To enable it, do a "sudo passwd root" and type in the new password

2) In your sshd_config, what is the value of PermitRootLogin? Change it to "yes" if it is any other value.

Hope this helps.

Cheers!

---

