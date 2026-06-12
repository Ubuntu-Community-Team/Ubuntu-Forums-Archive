---
title: "Error with Synaptic Package Manager"
date: 2006-11-17
forum: Repositories &amp; Backports
---

### Post by kcyster on 2006-11-17
When trying to update my repositories using Synaptic Package Manager I get the following errors:

W: GPG error: [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) edgy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive c <ftpmaster@ubuntu.com>
W: GPG error: [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) edgy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

This is a new installation of Ubuntu 6.10 (Edgy Eft) on a brand new Lenovo 3000 C100 laptop

Can anyone please help me

Thanks

---

### Post by lixy on 2006-11-17
Did you manually edit your /etc/apt/sources.list?

You may also wanna check this [guide]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories")

---

### Post by webjames on 2006-11-28
i have the same problem and so does my friend. i used to get updates no problem, then i check today (28th Nov) and i get an error.

keep an eye on this thread:

> [http://www.ubuntuforums.org/showthread.php?t=308638](http://www.ubuntuforums.org/showthread.php?t=308638)

regards,

James

---

