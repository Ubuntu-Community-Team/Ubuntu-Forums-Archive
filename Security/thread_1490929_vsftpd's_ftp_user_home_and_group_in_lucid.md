---
title: "vsftpd's ftp user home and group in lucid"
date: 2010-05-22
forum: Security
---

### Post by szim90 on 2010-05-22
Hello,

When I installed vsftpd, I noticed that a /home/ftp directory had not been created - the ftp user had it's home set to /srv/ftp, and the ftp user was added to an ftp group. This seems contrary to what the server guide says should happen ([https://help.ubuntu.com/10.04/serverguide/C/ftp-server.html](https://help.ubuntu.com/10.04/serverguide/C/ftp-server.html)) and other tutorials I read, most of which stated home should be set to /home/ftp, and group should be nogroup. 

Are there security implications to having the ftp user a member of the ftp group? Also, is there a need to add people to the ftp group, if one is created?

Additionally, is there a way I can change the permissions on the ftp home directory so regular (non-root) users can add files for anonymous users to download without creating a security problem?

Thanks for any help in this matter.

-Sean

---

### Post by Bachstelze on 2010-05-23
> **szim90 said:**
> 
Are there security implications to having the ftp user a member of the ftp group?

No, because the ftp user and group don't have permission to anything by default. This is something you would need to keep in mind if you're giving the ftp user and/or group permission to something, but it's not normally needed.

> **szim90 said:**
> Also, is there a need to add people to the ftp group, if one is created?

Yes, just like you would add users to any other group (by editing /etc/group for example). I can't see why you would want to do that, though...

> **szim90 said:**
> Additionally, is there a way I can change the permissions on the ftp home directory so regular (non-root) users can add files for anonymous users to download without creating a security problem?

What I would do is that I would create another group for that (for example ftupload), chown /srv/ftp to root:ftpupload and chmod it 775. Giving *all* users write permission to it might be asking for trouble (but if you really want to do that, just chmod it 777).

---

### Post by szim90 on 2010-05-23
Thank you Bachstelze.

Just to clairify, if I wanted to enable users to anonymously upload, I would need to make ftp a member of the ftpupload group you mentioned, correct?

Regards,
Sean

---

### Post by cdenley on 2010-05-24
> **szim90 said:**
> Thank you Bachstelze.

Just to clairify, if I wanted to enable users to anonymously upload, I would need to make ftp a member of the ftpupload group you mentioned, correct?

Regards,
Sean

If I recall correctly, vsftpd will not allow anonymous users to have write permission to their root directory. You must create a subdirectory for them to upload to.

---

### Post by szim90 on 2010-05-24
Alright. Thanks cdenley.

---

