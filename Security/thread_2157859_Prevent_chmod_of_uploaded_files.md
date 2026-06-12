---
title: "Prevent chmod of uploaded files"
date: 2013-06-27
forum: Security
---

### Post by typhen on 2013-06-27
Hi,

I'm running a PHP CMS on Apache, which includes functionality to upload files.

I'd like to configure permissions appropriately so that the Apache/PHP user can't chmod those files.

As I understand (please correct me if I'm wrong), if the PHP site is compromised, then it'll have permission to not only write files to the upload folder, but also to chmod +x them.

Is there any way to lock down my server to prevent chmod +x by a PHP script gone rogue?


Edit: There's no need at all for normal users to chmod. Would this be a good solution?
 chmod 700 /bin/chmod

---

### Post by cool110 on 2013-06-27
A simple way of doing this would be to put /var on a separate partition and mount it with the noexec option. changing the permissions of chmod will cause various programs and scripts to break.

---

### Post by compiledkernel on 2013-06-27
Mod your php which calls the file to do something like this. 

bool chmod ( string $filename , int $mode )

---

### Post by unspawn on 2013-06-28
> **typhen said:**
> As I understand (please correct me if I'm wrong), if the PHP site is compromised, then it'll have permission to not only write files to the upload folder, but also to chmod +x them.What you need is a server that's properly setup, user processes that are isolated (PHP-FPM, PHPsuExec or any other means to confine processes to their own unprivileged user Id), server hardening, auditing being scheduled automagically and regularly and applying any software updates when they are released. I'm not saying it's not an utter and complete b*tch to implement and manage but this should be the basis and not *combating (post-compromise) symptoms instead of addressing the root cause*, which is what it looks like you're trying to do... > **typhen said:**
> Edit: There's no need at all for normal users to chmod. Would this be a good solution? chmod 700 /bin/chmodNo because it's not the default, meaning an upgrade could undo that w/o you realizing it. And like cool110 already said: changing permissions may cause application b0rkage.

---

### Post by typhen on 2013-07-01
> A simple way of doing this would be to put /var on a separate partition and mount it with the noexec option. changing the permissions of chmod will cause various programs and scripts to break.

The noexec flag sounds amazing and should solve my needs perfectly. Thanks cool110! 

> **unspawn said:**
> What you need is a server that's properly setup, user processes that are isolated (PHP-FPM, PHPsuExec or any other means to confine processes to their own unprivileged user Id), server hardening, auditing being scheduled automagically and regularly and applying any software updates when they are released. I'm not saying it's not an utter and complete b*tch to implement and manage but this should be the basis and not *combating (post-compromise) symptoms instead of addressing the root cause*, which is what it looks like you're trying to do... No because it's not the default, meaning an upgrade could undo that w/o you realizing it. And like cool110 already said: changing permissions may cause application b0rkage.

Yes, such is my thinking. But I don't know of a way to prevent users from being able to chmod +x a file they've just created. (cool110's solution looks like it should work.)

Basically, the site was written by someone before me and deployed by someone else before me. I don't have contact with either of them.

My plan is to lock down some basic security issues including this one (as it seems someone has already uploaded files and executed them). It'll be faster to get that deployed than tracking down the vulnerabilities in the php code.

After that I'll start to actually find and fix the bugs in the php code, but I'd feel better after locking down the +x permissions as a safety net, because I don't think it's going to be easy to find and fix these issues in someone else's code without a few attempts at it.

---

