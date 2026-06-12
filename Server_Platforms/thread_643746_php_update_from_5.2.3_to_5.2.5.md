---
title: "php update from 5.2.3 to 5.2.5 ?"
date: 2007-12-18
forum: Server Platforms
---

### Post by Jean__ on 2007-12-18
Hello,

I'm new to ubuntu since 2 weeks.

My question, has anyone experience updating php, the latest and greatest seems to be 5.2.5 while my phpinof() says PHP Version 5.2.3-1ubuntu6.2.

Can I just apt-get install php?

If nobody confirms succes on this I'll just let it be, I don't want to screw up all my work so far.

Greets from Groningen netherlands
Jean.

---

### Post by cdenley on 2007-12-18
The latest version of php in ubuntu gutsy is 5.2.3-1ubuntu6.2. Security patches are applied, if that is what concerned you.

[http://changelogs.ubuntu.com/changelogs/pool/main/p/php5/php5_5.2.3-1ubuntu6.2/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/p/php5/php5_5.2.3-1ubuntu6.2/changelog)

---

### Post by Jean__ on 2007-12-18
No, as I have to port my stuff anyway to register globals off I thought why not go with the latest available php but I'll stick with the ubuntu default me thinks.
Thanks.

> **cdenley said:**
> The latest version of php in ubuntu gutsy is 5.2.3-1ubuntu6.2. Security patches are applied, if that is what concerned you.

[http://changelogs.ubuntu.com/changelogs/pool/main/p/php5/php5_5.2.3-1ubuntu6.2/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/p/php5/php5_5.2.3-1ubuntu6.2/changelog)

---

### Post by canopus4320 on 2007-12-24
> **cdenley said:**
> The latest version of php in ubuntu gutsy is 5.2.3-1ubuntu6.2. Security patches are applied, if that is what concerned you.

[http://changelogs.ubuntu.com/changelogs/pool/main/p/php5/php5_5.2.3-1ubuntu6.2/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/p/php5/php5_5.2.3-1ubuntu6.2/changelog)

Just to bump this thread again, is there some way to compile php 5.2.5 from source without breaking anything? (i'm using the default apache2 install with mod_php5 on gutsy)

i would appreciate any solution

---

### Post by mustang357 on 2007-12-25
Is there any need for 5.2.5?  Typically an ubuntu release is a specific release of an upstream version.  With each ubuntu release, the packages are updated to a newer version.  The 5.2.3 was compiled into packages and tested to ensure compatibility.

To compile from source (which I don't recommend unless there is a specific feature you need), you would probably have to compile against apache (in my somewhat limited experience).

Hope this helps!

---

### Post by Guiness on 2007-12-25
PHP 5.2.5 users have noticed a considerable performance increase.

[http://www.php.net/](http://www.php.net/)
The PHP development team would like to announce the immediate availability of PHP 5.2.5. This release focuses on improving the stability of the PHP 5.2.x branch with **[COLOR="Black"]over 60 bug fixes[/COLOR]**, several of which are security related. All users of PHP are encouraged to upgrade to this release.

I'd like to upgrade but still can't find a way. :-(

---

### Post by Guiness on 2007-12-27
Please check out [http://www.securityfocus.com/bid/26403/info](http://www.securityfocus.com/bid/26403/info)

**PHP 5.2.4 and Prior Versions Multiple Vulnerabilities**
PHP 5.2.4 and prior versions are prone to multiple security vulnerabilities. Successful exploits could allow an attacker to bypass security restrictions, cause a denial-of-service condition, and potentially execute code.

---

### Post by cammj on 2007-12-27
> **mustang357 said:**
> 
To compile from source (which I don't recommend unless there is a specific feature you need), you would probably have to compile against apache (in my somewhat limited experience).


depends if apache was built with apxs or not :)

---

### Post by Guiness on 2007-12-27
**Ubuntu 8.04 LTS (Hardy Heron) Alpha 2 comes with PHP 5.2.5**
[http://cdimage.ubuntu.com/releases/hardy/alpha-2/](http://cdimage.ubuntu.com/releases/hardy/alpha-2/)

To compare the different distributions check out:
[http://distrowatch.com/table.php?distribution=ubuntu](http://distrowatch.com/table.php?distribution=ubuntu)

Looks like Hardy is better than Gutsy

---

### Post by mustang357 on 2007-12-27
If that's the case, why not use the hardy packages and the following tutorial?:

[http://ubuntuforums.org/showthread.php?t=268687](http://ubuntuforums.org/showthread.php?t=268687)

Edit:  I suggest this because hardy isn't yet stable

---

### Post by jtc on 2007-12-27
> **Guiness said:**
> Please check out [http://www.securityfocus.com/bid/26403/info](http://www.securityfocus.com/bid/26403/info)

**PHP 5.2.4 and Prior Versions Multiple Vulnerabilities**
PHP 5.2.4 and prior versions are prone to multiple security vulnerabilities. Successful exploits could allow an attacker to bypass security restrictions, cause a denial-of-service condition, and potentially execute code.

Well, as cdenley mentioned earlier, you do get the security patches.

PHP Version 5.2.3-1ubuntu6.2 is basically PHP version 5.2.3, but with all the current security patches. The reason Ubuntu won't call it 5.2.5 is because they haven't added any of the new functionality.

---

