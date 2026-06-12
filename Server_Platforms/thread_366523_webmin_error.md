---
title: "webmin error"
date: 2007-02-21
forum: Server Platforms
---

### Post by Strangerdave on 2007-02-21
Hey there,

I have been trying to install webmin for a while now but keep getting this error

```
tar: webmin-1.320/logrotate/config-open-linux: Not found in archive
tar: webmin-1.320/ldap-useradmin/config-united-linux: Not found in archive
tar: webmin-1.320/ldap-useradmin/config-debian-linux: Not found in archive
tar: webmin-1.320/ldap-useradmin/config-mandrake-linux: Not found in archive
tar: webmin-1.320/ldap-useradmin/config-suse-linux: Not found in archive
tar: webmin-1.320/ldap-useradmin/config-redhat-linux: Not found in archive
tar: webmin-1.320/ldap-useradmin/config-debian-squirrelmail-linux: Not found in archive
tar: Error exit delayed from previous errors
```

Does anyone know what this means?

I am kind of new at this server thing so thanks for any and all help.

-SD-

---

### Post by caryb on 2007-02-21
Did you install the .deb or the rpm? I installed the deb today on 2 Edgy servers they failed deps but all I did was sudo apt-get -f install & all deps were installed & then completed the install. It works a treat x2 :-)


Cary

---

### Post by Strangerdave on 2007-02-21
Thanks for the reply.  I realize now that my post could have been a little clearer.  I have downloaded the .tar file, and am trying to unpack it to my desktop.  I also tried to install the  deb files but also got a error.  I can't remember the exact error message as I am at work, but the problem seems to be unpacking the files.

-SD-

---

### Post by Brazen on 2007-02-21
personally, I would strongly suggest using the deb package.

But, to answer your question, how are you unpacking it?  Sorry I'm not familiar with the gui way of doing this, but the command line would be "tar -xzf webmin-XXX.tar.gz".

---

### Post by Strangerdave on 2007-02-21
I am unpacking it using the archive program (can't think of the actual name).

Maybe I will try the deb method once more and see if I have success, or even using the command line method.

Thanks

-SD-

---

### Post by caryb on 2007-02-21
The deb install will fail with dep problems but after you apt-get -f install it will fix dep problems & finish the webmin install. Have just finished my 3rd server webmin install & all have done this but all is good!!!



Cary

---

### Post by Strangerdave on 2007-02-21
Thanks for the help.  I used the deb package and it installed like a charm.

-SD-

---

