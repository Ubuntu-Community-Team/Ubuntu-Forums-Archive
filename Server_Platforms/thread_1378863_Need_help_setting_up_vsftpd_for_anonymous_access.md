---
title: "Need help setting up vsftpd for anonymous access"
date: 2010-01-11
forum: Server Platforms
---

### Post by EienTatsu on 2010-01-11
So I have users accessing their home folders which is fine. The problem I have is with anonymous users. I store my media in a different partition than the ftp root directory and I have a symlink connecting it to the diff. partition. I can't figure out how to make it to where the anonymous users can use the sym link even though the target folder is read allowed by everyone.

---

### Post by EienTatsu on 2010-01-12
anyone?

---

### Post by HermanAB on 2010-01-12
FTP servers will not follow symlinks - security problem.

---

### Post by EienTatsu on 2010-01-12
> **HermanAB said:**
> FTP servers will not follow symlinks - security problem.Is there any reason my local accounts can via ftp. But anyways Is there any way to give anonymous access to the other partition while leaving the anonymous root where it is now?

---

### Post by EienTatsu on 2010-01-12
I really do need help with a solution since i will be needing to link my HDs to my anon ftp account

---

### Post by Lars Noodén on 2010-01-13
> **EienTatsu said:**
> I really do need help with a solution since i will be needing to link my HDs to my anon ftp account

Well, you could treat the FTP directory as a mirror site. 
 
For that you can make a script to use rsync to update the FTP mirror from the other directories you have scattered around the system.  Then you can have cron do this update automatically and/or allow your users to run it "manually"  


Or, a bit riskier, you could put the data directories in the FTP directories and symlink **to** those from the user directories.

---

