---
title: "Active Directory"
date: 2007-08-02
forum: Server Platforms
---

### Post by sasanf on 2007-08-02
I've been following the tutorial located at [https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto).  I've gotten to the join the domain step but am getting errors.   Yeah the tutorial is for an older version of Ubuntu but it is by far the best I've tried.  I tried a bunch of others and couldn't get nearly as far as I have with this one.  BTW, I am running Feisty 32 bit.  The output is below:

superman@importer-linux:~$ sudo net ads join -U superman
superman's password: 
Using short domain name -- BEI
[2007/08/02 14:22:36, 0] utils/net_rpc_join.c:net_rpc_join_ok(70)
  net_rpc_join_ok: failed to get schannel session key from server dc1.bei.image for domain BEI. Error was NT_STATUS_ACCESS_DENIED
Failed to verify membership in domain!
superman@importer-linux:~$ wbinfo -u
Error looking up domain users
superman@importer-linux:~$ wbinfo -g
Error looking up domain groups
superman@importer-linux:~$ 

Please be quick in response.  I have to have this working by 4 O' Clock today- Eastern time.  Thanks in advance for the help.

---

