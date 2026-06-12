---
title: "Ubuntu Server 17.10 - Package Sources Older Than Release Packages"
date: 2017-12-21
forum: Repositories &amp; Backports
---

### Post by guitardood2 on 2017-12-21
Hello All,
I'm having an issue where the source packages have not been updated to the same release version as the binaries through
apt. This is on 17.10 server.


I've had to download and compile the source package for samba, in order to apply a patch that resolves issue with 32-bit
 printer driver uploads. The problem is that the binaries available through apt have now appended a ".1" to the release
packages and now the server is prompting me to upgrade these packages, so I figured I'd let it install and then download
ed a supposedly fresh copy of the source so I can patch and compile. After compiling, when I install the .deb's created
by the package build, dpkg reports that it is downgrading the release from the installed 3.1 to 3.


I guess my question is, how long does it take for source packages to be updated to match the binary .deb versions?


Best,
guitardood

---

### Post by QIII on 2017-12-21
Hello!

I have removed the original post from public view.  Please don't create duplicate posts.  If you feel you have made a post in the wrong place, use the "Report post" button to ask the staff to move it.

Thanks.

---

### Post by ian-weisser on 2017-12-21
> **guitardood2 said:**
> how long does it take for source packages to be updated to match the binary .deb versions?

The question makes no sense.
Sources are updated first. That's how the updated binary gets made.

If you can point to a specific package, bug, and/or version, perhaps we can help you better.

---

### Post by guitardood2 on 2017-12-21
> **ian-weisser said:**
> The question makes no sense.
Sources are updated first. That's how the updated binary gets made.

If you can point to a specific package, bug, and/or version, perhaps we can help you better.

Samba.  Source is: samba_4.6.7+dfsg-1ubuntu3.  After installing the version I built from the source package, apt wants to upgrade it to samba_4.6.7+dfsg-1ubuntu3.1.


Best,
Guitardood

---

### Post by ian-weisser on 2017-12-21
First thing you need to know is that after release (like 17.10), Ubuntu DOES NOT update the code. No new releases of LibreOffice or Openshot or Samba during 17.10's life.
The security team (and the SRU developers) will do exactly what you did - patch the 4.6.7 code. Then they increment the `ubuntuX.Y` string at the end of the version string from 3 to 3.1.
Apt reads the changed version string, and treat it (properly) as an upgrade.

It's generally considered a bad idea to fix or game the version number system. It leads to all kinds of trouble.
You can simply tell apt to not upgrade samba anymore:
```
sudo apt-mark hold samba          //today
sudo apt-mark unhold samba        //someday, to remove the hold
```

See 'man apt-mark'

---

### Post by guitardood2 on 2017-12-21
> **ian-weisser said:**
> First thing you need to know is that after release (like 17.10), Ubuntu DOES NOT update the code. No new releases of LibreOffice or Openshot or Samba during 17.10's life.
The security team (and the SRU developers) will do exactly what you did - patch the 4.6.7 code. Then they increment the `ubuntuX.Y` string at the end of the version string from 3 to 3.1.
Apt reads the changed version string, and treat it (properly) as an upgrade.

It's generally considered a bad idea to fix or game the version number system. It leads to all kinds of trouble.
You can simply tell apt to not upgrade samba anymore:
```
sudo apt-mark hold samba          //today
sudo apt-mark unhold samba        //someday, to remove the hold
```

See 'man apt-mark'

Thanks for the info.

I didn't change anything version-wise, just downloaded source with 'apt-get source samba', applied the patch to the source to resolve 32-bit printer driver issues, ran dpkg-buildpackage and then installed the created .debs with dpkg.  After I install my patched .debs, apt-get dist-upgrade wants to "upgrade" all of the samba packages.  The 3.1 is coming from apt binary release, despite the source package only being 3. Perhaps I'm not understanding where the .1 comes from.  I was hoping to not have to use the 'hold' feature so that I'd be notified when any patches have been made and I figured I'd download the source and recompile whenever apt notified me that there was a new release, just to keep my patched release current.

Best,
Guitardood

---

### Post by ian-weisser on 2017-12-21
The .1 comes from the Ubuntu Security Team.
Apt does not have a 'notification-only' function.

---

### Post by guitardood2 on 2017-12-21
> **ian-weisser said:**
> Apt does not have a 'notification-only' function.

Sure it does.  Not an explicit 'notification-only' function, per se, but I do an 'apt-get dist-upgrade', see what packages it wants to upgrade and then answer 'N'o.


> **ian-weisser said:**
> The .1 comes from the Ubuntu Security Team.

So does this mean that the downloaded source package is NOT the same release as the binaries provided by the Security Team?  I don't mean to be obtuse, but there is a version discrepancy.  If I download source through apt, make NO changes and rebuild, I should, theoretically, have the same binaries as those being distributed by the package manager, No?  If the security team is modifying versions, I'm assuming they are modifying the code as well.  That being the case, where do we obtain the source being used to compile the distributed binaries?

Best,
Guitardood

---

### Post by ian-weisser on 2017-12-21
Good question:

version ubuntu3 source is in the artful repos.
version ubuntu3.1 source is in the artful-security repos.

---

### Post by guitardood2 on 2017-12-21
SOLUTION:
> **ian-weisser said:**
> Good question:

version ubuntu3 source is in the artful repos.
version ubuntu3.1 source is in the artful-security repos.

Ahhhhh.  Repos uncommented, source compiling as we speak.

Thank You!!

Best,
Guitardood

---

