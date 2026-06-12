---
title: "Updating 18.04 generates &quot;redirection loop encountered&quot;"
date: 2018-04-05
forum: Ubuntu Development Version
---

### Post by SeijiSensei on 2018-04-05
The last few times I've updated Kubuntu 18.04 from the command prompt, I have ended up with two or three packages tagged with the "redirection loop encountered" error.  Using "--fix-missing" ignores these errors and installs the rest of the packages.  If I open the links to the problematic debs directly from the terminal (in Konsole by right-clicking and choosing "open link"), sometimes these packages will install manually.  That was not the case today, though.

What generates these errors?  A search online returns very little information.  Will the errors eventually disappear when the final version of 18.04 is released?

Today's errors came from libgoa, linux-headers-4.15.0, and gdb.  Other times different packages generate these errors.

---

### Post by dino99 on 2018-04-05
'journalctl -b' might be your best friend

is that install a fresh one or a rolling one ? Maybe clean the system to remove old setting files/orphans.
Also check /etc/apt/sources.list about possible typo.
In case of installed ppa, try deactivating them, then downgrade the packages; or use ppa-purge to rollback to a genuine install.
Be sure you does not have broken links inside the many /etc/rc?.d dirs

Then run: sudo dpkg --configure -a  /  sudo dpkg-reconfigure apt

---

### Post by SeijiSensei on 2018-04-05
None of the issues you mention are likely to cause this.  I don't have any problems after an installation with "--fix-missing", but the packages that generate the errors are not updated.  I just don't understand what the error means or why it happens.  There's little documentation about this out there.

I'm routinely upgrading from a snapshot that I installed a couple of weeks ago.  I have no PPAs.  Nor have I edited or added any files to /etc/apt/sources.list.d/.

"journalctl -b" generates a huge output that I'm not about to pore over.  If I filter the output through grep and search for "error" there are a couple of issues regarding SNAP which I don't use, and an "exec format error" for /etc/rc.local which I do use.  I have no idea about that one; I suspect it has to do with systemd issues.  (The file /etc/rc.local has the correct format and is executable.) In any event none of these problems would generate the redirection error.

---

### Post by zika on 2018-04-05
> **SeijiSensei said:**
> "journalctl -b" generates a huge output that I'm not about to pore over.You could always use [https://pastebin.com/](https://pastebin.com/) to share it with us...
Take a look at: [https://askubuntu.com/questions/986362/apt-get-install-fails-cant-find-this-error-message-anywhere](https://askubuntu.com/questions/986362/apt-get-install-fails-cant-find-this-error-message-anywhere) ...

---

### Post by dino99 on 2018-04-05
About 'journalctl -b' : only focus on 'highlighted' lines for warnings, and 'red' lines about errors
You can also test your profile: login with an other user to know if the problem persist.

---

### Post by SeijiSensei on 2018-04-05
I think this problem has more to do with discrepancies in the availability of packages in development. I don't think it has much, if anything, to do with my essentailly vanilla configuration.  That's why I'm looking for documentation of the redirection error.

---

### Post by SeijiSensei on 2018-04-06
In support of my last post, I installed Kubuntu 18.04 from scratch today.  When I ran a "dist-upgrade", I ended up with a motley collection of nine packages that generated the "redirection loop" error, including such mainstays as fdisk, iproute and bind9-host. Since these errors occurred on a brand-new vanilla installation, I have to assume it's a problem upstream.

These errors always include URLs with IP addresses rather than the usual us.archive.ubuntu.com hostname.

---

### Post by zika on 2018-04-07
> **SeijiSensei said:**
> When I ran a "dist-upgrade"What packages where removed while You vere doing dist-upgrade? What were the reasons apt gave You to do dist-upgrade instead of regular one?

---

### Post by SeijiSensei on 2018-04-07
I always use dist-upgrade when starting from scratch to update the kernel and associated files. The list of updated packages numbered over 900. 

You seem convinced I'm doing something wrong. I've been installing and updating Ubuntu for at least a decade now and never saw this error before.

---

### Post by zika on 2018-04-07
> **SeijiSensei said:**
> You seem convinced I'm doing something wrong. I've been installing and updating Ubuntu for at least a decade now and never saw this error before.I can only try to convince You that I am not even in a slight sense but I do doubt that I could, You seem so convinced I do...
To quote You, with a twist: I've been counceling on installing and updating Ubuntu for at least a decade now, mostly distantly so I do have a tendency to make things the way I did in those prevoius cases that ended in a success, amplified by the fact that I do not have/had access to a machine in case...
Please accept my appology for trying to help. I'll courteously exit this thread not to make You feel bad... I've reported on a similar case of redirection (it was caused by packages removed) and that was the only reason I asked You what I've asked You. Sorry... Bye.

---

