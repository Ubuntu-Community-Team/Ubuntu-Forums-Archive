---
title: "Downgrade curl"
date: 2010-02-13
forum: Server Platforms
---

### Post by tegryan on 2010-02-13
Hi,

I need to downgrade curl (newest version has a bug I can't get around) and I'm not exactly sure how.  I have removed curl (sudo apt-get remove php-curl), and downloaded and installed (./configure, make, make install) the version I need and everything looks fine for that.  However, my phpinfo page doesn't show curl support anymore, so I assume I need to recompile php with curl support.  My question is, how do I recompile php with all the current settings it has now?  I used apt-get to install it with a bunch of other packages, so I'm not really sure what arguments to use when I recompile it.  Is there a way to print the current settings?

Thanks!

---

### Post by falconindy on 2010-02-13
Do you need to downgrade curl? Or the curl module for php?

---

### Post by tegryan on 2010-02-13
> **falconindy said:**
> Do you need to downgrade curl? Or the curl module for php?

cURL, I believe.  It's a PHP script calling the curl function, but I don't think the PHP module is the issue.

---

### Post by falconindy on 2010-02-13
If you're calling it from a php script and not using the system() function, it's the php-curl module that's causing your issue. Downgrading may not be possible without downgrading your entire php install.

---

### Post by tegryan on 2010-02-13
> **falconindy said:**
> If you're calling it from a php script and not using the system() function, it's the php-curl module that's causing your issue. Downgrading may not be possible without downgrading your entire php install.

hmmm, ok, here is the error:

Warning: curl_setopt() [function.curl-setopt]: CURLPROTO_FILE cannot be activated when in safe_mode or an open_basedir

Looks like it might be the module then.

Are older versions of PHP in the repositories?

---

### Post by falconindy on 2010-02-13
Is this on a VPS or some other commercially hosted server? Safe mode is a feature of PHP that's typically used by hosters to prevent bad things on happening on shared servers. Downgrading isn't going to help. You need to disable safe mode.

[http://php.net/manual/en/features.safe-mode.php](http://php.net/manual/en/features.safe-mode.php)

---

### Post by tegryan on 2010-02-14
> **falconindy said:**
> Is this on a VPS or some other commercially hosted server? Safe mode is a feature of PHP that's typically used by hosters to prevent bad things on happening on shared servers. Downgrading isn't going to help. You need to disable safe mode.

[http://php.net/manual/en/features.safe-mode.php](http://php.net/manual/en/features.safe-mode.php)

It's a dedicated server.

Safemode is actually not on, it's just a bug in cURL that's throwing that error.  I've talked to the developer of the module that's causing the error and we're quite certain that it's a bug with the version of cURL i'm using.

It's sounds like I'm going to have to downgrade to an older version of PHP then.  I guess I'll get working on that.

Thanks for your help.

---

### Post by falconindy on 2010-02-14
> **tegryan said:**
> It's a dedicated server.

Safemode is actually not on, it's just a bug in cURL that's throwing that error.  I've talked to the developer of the module that's causing the error and we're quite certain that it's a bug with the version of cURL i'm using.

It's sounds like I'm going to have to downgrade to an older version of PHP then.  I guess I'll get working on that.

Thanks for your help.
Right on. Good luck in your downgrade.

---

