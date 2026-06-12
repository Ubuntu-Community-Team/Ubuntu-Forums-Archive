---
title: "Samba4 Secondary DC provision not working"
date: 2014-07-02
forum: Server Platforms
---

### Post by suriya2 on 2014-07-02
Hi
iam trying in ubuntu 14.0 server with samba4 with windows 2008 R2 DC. I need this Samba4 to act as additional DC for user authentications. When i try this command 
samba-tool join domain as dc, it starts the replication of schemas and last i get this error,

Failed to apply records: failed to find GUID for (null) invalid DN syntax
Failed to commit objects: WERR_GENERAL_Failure
Join Failed - Cleaning up
Errr type exceptions : uncaught exception - Failed to process chunk: NT_Status_Unsuccessful.

what could be the reason??

I explored in certain forums that Samba4 as SDC is not compatible with windows that has Exchange. Is it true?
If not what is the best way to have an ubuntu server with LDAP that can just enumerate my windows users and groups for allowing local Firewall authentication instead of contacting my local DC from remote location every time utilizing the WAN link.

regards
Suriya

---

### Post by lingpanda on 2014-07-21
Did you ever resolve this issue? If not what is the full syntax you are using to attempt join?

---

