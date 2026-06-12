---
title: "sftp missing (9.04 server edition)"
date: 2009-06-04
forum: Server Platforms
---

### Post by mleisher on 2009-06-04
sftp seems to be missing and reinstalling openssh-* did not work. Any hints?

---

### Post by cdenley on 2009-06-04
> **mleisher said:**
> sftp seems to be missing and reinstalling openssh-* did not work. Any hints?

The sftp command is missing, or you cannot connect to your server using the sftp command?

---

### Post by mleisher on 2009-06-04
It was missing. I reinstalled the openssh-* packages a third time and it finally showed up. I now notice that sftp-server is missing.

---

### Post by cdenley on 2009-06-04
> **mleisher said:**
> It was missing. I reinstalled the openssh-* packages a third time and it finally showed up. I now notice that sftp-server is missing.

What did you mean by "it". Is "it" separate from "sftp-server". Is "sftp-server" a package you are expecting to see, or are you missing sftp functionality in your ssh server? Is there something currently missing?

---

### Post by mleisher on 2009-06-04
First, /usr/bin/sftp was not installed. It simply wasn't on the system. Uninstalling and reinstalling the openssh packages three times worked.

Second, /usr/lib/sftp-server, which was working before I started the above reinstalls, is now gone.

I have since downloaded and installed the latest openssh. Everything worked right away.

This installation has been plagued with so many bizarre configuration problems that it can only be a problem with the platform.

Installing everything I need from source has worked up to this point. Hopefully that will run long enough to get replacement hardware.

---

