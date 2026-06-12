---
title: "Need help for specific SSH JumpBox Config"
date: 2018-12-26
forum: Server Platforms
---

### Post by vick7512 on 2018-12-26
Hey everyone,

I would like some assistance in finishing my Open SSH jumpbox setup. 

Use case is this:

Multiple outside vendors from different companies will need to connect to inside servers they own. Would like them to auth through jumpbox using Putty key pair. Once authenticated, would like the jumpbox to port forward RDP to specific host for each vendor. 

Ideally, here is what I would like the vendor to see on their end when connecting. 

1. Open putty, load private key and connect
2. Authenticate to jumpbox 
3. Putty minimizes with no shell access once connected
4. Vendor opens Windows Remote Desktop and types localhost:3389 
5. Once finished, close RDP connection and then close Putty connection
 
I already have the jump box setup and working to use key pair authentication and I have tested this successfully. The only thing I need assistance with is locking down access for the outside vendors to only allow them to RDP localhost and not have ANY CLI/shell access. Curveball would be to have this configuration be specific to the key pair that is authenticating so that each vendor only has access to what we permit. Ie: If vendor 1 connects, their key pair will only allow access to server 1. Vendor 2 to server 2 and so forth. 

I was told this can be done on the authorized_keys and/or sshd_config file however, aside from the port forwarding commands I found in the manual for it, I am at a loss for getting it to work. 

I would like to know the following: 

1. What would be the configuration to restrict the users from getting shell access once the authentication to the jump box is complete?
2. What would the configuration syntax be for forwarding port 3389 to a specific host and having the vendor use Windows RDP localhost since they will not have access to the shell to run commands?  (I know this can be done in Putty but I would not like the vendor to know any of our local IPs)
3. Can step 2 be configured per user?
4. Is it possible to have a script or configuration on the jump box to have the vendor's Putty instance minimize once auth has completed without having them configure anything in putty? 

Let me know if you need additional info or have any questions. 

Thanks!

---

### Post by howefield on 2018-12-26
Moved to the "*Server Platforms*" forum.

---

