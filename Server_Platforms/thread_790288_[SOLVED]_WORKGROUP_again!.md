---
title: "[SOLVED] WORKGROUP again!"
date: 2008-05-11
forum: Server Platforms
---

### Post by JanvL on 2008-05-11
Hello,

Can someone refresh my mind.

I have made a clean install of Hardy and started Samba again.
The machine however is put in WORKGROUP and not in my network.
I had the same with Dapper but cannot find where I changed it then,
and wonder that it is the same again.

So can someone tell me how to get rid of WORKGROUP please.

Thanks for any help,

Jan

---

### Post by koenn on 2008-05-11
/etc/samba/smb.conf ?

---

### Post by JanvL on 2008-05-11
NO,

it is not in the smb.conf
I copied that from Dapper.

Thanks

---

### Post by koenn on 2008-05-11
and you restarted samba afterward you copied that file ?

```
nix:~# grep "workgroup" /etc/samba/smb.conf
# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = GOELAG
```

---

### Post by JanvL on 2008-05-12
Thanks for the reply,

Yes I restarted Samba, know how to handle it.
I remember from 5.10 to 6.06 upgrade that there was a kind of "registry" where this "workgroup" still was, after removing it Samba accepted only the name of my network.

The only thing is that I just blew my Hardy, something with the ATI-drivers,
also again (I had this before) so I have to repair that as well.
I am happy to have left my 6.06 so I can still work.

It seems that some problems from 6.06 are still not solved so I will post to Canonical and explain, maybe it will change then.

Jan

---

### Post by JanvL on 2008-05-21
SOLVED

In the networksettings I found the entry, removed it now it is OK.

Jan

---

