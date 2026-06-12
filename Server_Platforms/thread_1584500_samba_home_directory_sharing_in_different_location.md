---
title: "samba home directory sharing in different location"
date: 2010-09-29
forum: Server Platforms
---

### Post by wall_e on 2010-09-29
HI Guys,

I have 10.04 and have samba running.

Samba is remotely administered with webmin and aim to setup home directory sharing. I am however having some trouble getting this to work.

I was of the understanding that home directory sharing allows me to create a user in ubuntu, which samba will then pickup and offer it up as a share.

My smb.conf looks like this..

```

#======================= Global Settings =======================

[global]
    unix extensions = no
    share modes = no
    security = user

#======================= Share Definitions =======================

[homes]
    comment = Home Direcotries
    valid users = %S
    browseable = no
    writeable = yes

```

Essentially I've found this works providing I give the samba user a password after it is automatically created using the 'Configure automatic Unix and Samba user synchronisation' option in webmin.

However if I move the location of this home folder off the main drive i.e. /home/username I get turned away at attempted login.

Any ideas?

I've tried specifying the path in [homes] using the path = /media/discarray, but this seems to break authentication somehow.

---

### Post by the_original_billq on 2010-09-29
> **wall_e said:**
> 

Essentially I've found this works providing I give the samba user a password after it is automatically created using the 'Configure automatic Unix and Samba user synchronisation' option in webmin.

However if I move the location of this home folder off the main drive i.e. /home/username I get turned away at attempted login.

Any ideas?

I've tried specifying the path in [homes] using the path = /media/discarray, but this seems to break authentication somehow.

How are you moving them "off the main drive"?  Their passwd home directory entry has to reflect their actual home directory, wherever it is.

-Bill

---

### Post by wall_e on 2010-09-29
When I create the user in webmin I've set it up to create the home folder at the location /media/discarray.

I've checked the permissions on these folders for the user, everything seems to be in order.

---

