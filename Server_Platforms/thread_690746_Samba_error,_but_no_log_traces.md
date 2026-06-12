---
title: "Samba error, but no log traces?"
date: 2008-02-07
forum: Server Platforms
---

### Post by usererror on 2008-02-07
Hello!

I have a curious samba issue.

In my /etc/fstab I have the following lines:

```

//mediacenter/Videos /var/lib/mythtv/videos smbfs rw,guest,fmask=0777,dmask=0777  0       0
//mediacenter/Music  /var/lib/mythtv/music  smbfs rw,guest,fmask=0777,dmask=0777 0       0
//mediacenter/Posters /home/mediacenter/.mythtv/MythVideo smbfs ro,guest,fmask=0755,dmask=0755 0 0

```

At boot up I get an error on the first two, but not the one.  When I check /var/log/samba/log.smbd and log.smbmount I have no errors listed.

Even though it says "Fail" at startup when loading Linux, once it logs in I can still access the Samba mappings!  So I am royally confused.  Is it a permissions issue on the other Linux box?

Thanks in advance!

---

### Post by usererror on 2008-02-17
I have found a solution to this problem, and i have posted it in this other thread here:

[http://ubuntuforums.org/showpost.php?p=4349070&postcount=2](http://ubuntuforums.org/showpost.php?p=4349070&postcount=2)

---

