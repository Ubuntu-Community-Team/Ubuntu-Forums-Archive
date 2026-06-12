---
title: "OpenSSH and FXP setting"
date: 2008-06-27
forum: Security
---

### Post by dwoods99 on 2008-06-27
I already have an OpenSSH server configured and running well.
I have also implemented a chroot jail.  No problems there.

My problem is that someone is asking me to allow server-to-server
transfers with the FXP 'protocol' used by FTP clients such as FlashFXP on Windows.
Their reasoning is that SFTP is not transferring as fast as using the FXP option.

I will only allow changes to be made as long as SSL/TLS is still used.
Is there something in the OpenSSH settings that will allow FXP to be enabled?
I can't find anything so it seems that I may need to install Pure-FTPD and restrict user IP addresses.

Any suggestions appreciated.

---

### Post by HalPomeranz on 2008-06-28
> **dwoods99 said:**
> 
Is there something in the OpenSSH settings that will allow FXP to be enabled?


Sorry, no.  There's no way to do this with OpenSSH.  We're talking totally different and incompatible protocols.

How much data are they trying to move that the speed difference is really an issue?  It sounds to me like the people who are requesting this are just looking for excuses in order to avoid changing things at their end.

---

### Post by dwoods99 on 2008-06-28
I agree that it may be a problem with user perception.
As for file size, we're talking 4-12 GB files/directories.

One thing I still don't "get" is that FXP is supposed to make server-2-server transfers faster, that's fine but I can't see how
local_PC-2-server will go any faster because of FXP compared to sftp with multi-threading.

---

### Post by HalPomeranz on 2008-06-28
> **dwoods99 said:**
> 
As for file size, we're talking 4-12 GB files/directories.


OK, that's a fair amount of data, so the overhead for encryption probably is noticeable.

> **dwoods99 said:**
> 
One thing I still don't "get" is that FXP is supposed to make server-2-server transfers faster, that's fine but I can't see how
local_PC-2-server will go any faster because of FXP compared to sftp with multi-threading.

Well if they're using the default unencrypted form of FXP then it's going to be hugely faster than an encrypted protocol like SSH.

---

### Post by dwoods99 on 2008-06-28
Thanks for the responses.

Looks like I'll just have to allow access with restricted IP validation.

---

### Post by HalPomeranz on 2008-06-28
I just had one more thought.  When they're sending you 4-12GB of data, is that 4-12GB of brand new data or just incremental updates to the same collection of data?  If it's just incremental updates then use rsync (which runs on top of SSH by default) to just update the parts of the data that have been modified, rather than recopying everything.  That will be very fast, and much more secure because it's running over SSH.

---

### Post by dwoods99 on 2008-06-28
Unfortunately, it's new data backups.

---

