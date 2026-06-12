---
title: "Samba smb bug and fix related to WannaCry"
date: 2017-06-01
forum: Security
---

### Post by sp40140 on 2017-06-01
WannaCry was windows thing. But it was related to SMB bug in windows.
Turns out that SAMBA has similar bug.

Link: [https://www.samba.org/samba/security/CVE-2017-7494.html](https://www.samba.org/samba/security/CVE-2017-7494.html)

Now, I do have samba set-up at home. I already have disabled the samba ports so it's not visible from internet.
Still, I would like to update samba to patched version. I currently have 4.5.8 installed. And it's not patched. 4.5.10 is patched. 
However, 4.5.10 has not been pushed in ubuntu updates yet!
I wonder when that will happen?
If not, I will have to manually download and install it. I would like to avoid doing this though.

---

### Post by howefield on 2017-06-01
Would that be 17.04 that you are running, as long as you have updated to current package versions you should be covered.

[http://changelogs.ubuntu.com/changelogs/pool/main/s/samba/samba_4.5.8+dfsg-0ubuntu0.17.04.2/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/s/samba/samba_4.5.8+dfsg-0ubuntu0.17.04.2/changelog)

---

### Post by sp40140 on 2017-06-01
Yes, I am running 17.04 64bit. All the updates / patches are applied.
Good, I am covered.

BTW, how do (did) you find out that it's been patched and pushed in ubuntu? (so that I can check it myself in future).

Thank you.

---

### Post by deadflowr on 2017-06-01
> BTW, how do (did) you find out that it's been patched and pushed in ubuntu? (so that I can check it myself in future).
[https://www.ubuntu.com/usn/]("https://www.ubuntu.com/usn/")
Sign up for the announcements mailing list to get the notices when they come out.

---

### Post by sp40140 on 2017-06-01
Merci

---

### Post by howefield on 2017-06-02
> **sp40140 said:**
> BTW, how do (did) you find out that it's been patched and pushed in ubuntu? (so that I can check it myself in future).

Apart from the link above, I sign up to the "change" mailing lists for the versions I have installed on my machines which at the moment are xenial, zesty and artful.

But in this specific instance, I specifically looked at the package change log the first time this issue question was posted. Oftentimes you won't get a major change in package version number when a security update has been applied, in other words it might still look like version 4.5.8 but if you look at the full package name you'll see the change.

2:4.5.8+dfsg-0ubuntu0.17.04.2
2:4.5.8+dfsg-0ubuntu0.17.04.1

---

