---
title: "Samba sharing with no defined shares"
date: 2011-04-09
forum: Server Platforms
---

### Post by ckfoxtrot on 2011-04-09
Hi all,

I set samba up on my ubuntu server and it is sharing a directory, the one I want in fact, without any shares set up in smb.conf.

If I put a share in smb.conf, it shows up fine and allows me too access it.  I am just wondering how/why it is sharing without any set shares?

My best thought as of now is due to creating that directory as follows:

```

sudo mkdir -p /srv/olympia
sudo chown nobody.nogroup /srv/olympia/

```

It is working, which is great, but I just want to make sure that it is working right :)

ck

---

### Post by Morbius1 on 2011-04-09
>  I set samba up on my ubuntu server and it is sharing a directory, the one I want in fact, without any shares set up in smb.conf.Two possibilities come to mind:
You do have a share defined - [homes] - but it's definition is usually scattered throughout smb.conf so it's hard to see. You can get a better look by issuing the following command:
```
testparm -s
```Another possibility is that you used Nautilus to create the share - but then you would have to have Nautilus installed on your server. You can see if there are any Nautilus-shares with this command since their share defintiions are in another location and not in smb.conf:
```
net usershare info --long
```

---

### Post by ckfoxtrot on 2011-04-09
> **Morbius1 said:**
> Two possibilities come to mind:
You do have a share defined - [homes] - but it's definition is usually scattered throughout smb.conf so it's hard to see. You can get a better look by issuing the following command:
```
testparm -s
```Another possibility is that you used Nautilus to create the share - but then you would have to have Nautilus installed on your server. You can see if there are any Nautilus-shares with this command since their share defintiions are in another location and not in smb.conf:
```
net usershare info --long
```

Hi Morbius1,

There is no home share in my smb.conf but the folder is indeed being shared through nautilus.  I think I created the folder as outlined above but then also changed the permissions within nautilus while trying to set it up.

Previously, the one share I set up in smb.conf did show up when trying to connect to my server but I removed it since it seemed redundant, so at least I still know that samba was working.  Now it is just a matter of fixing the system v samba permissions.

Thanks!

ck

---

