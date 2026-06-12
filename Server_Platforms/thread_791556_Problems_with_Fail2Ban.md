---
title: "Problems with Fail2Ban"
date: 2008-05-12
forum: Server Platforms
---

### Post by dacool25 on 2008-05-12
Hey everyone,

I'm having lots of trouble with [fail2ban]("http://www.fail2ban.org/wiki/index.php/Main_Page").  I originally had it set up and it was working like a charm.  Then I updated to 8.04 and nothing worked after that.  So I did a simple apt-get remove and got rid of it and tried to re-install it.  Still nothing, the logs would fill up but it wouldn't actually block anything.

Now I thought I'd try that again.  I removed it and then did a locate fail2ban and deleted most of the instances of it besides the things in /var/lib/dpkg/info/

Now I tried to install it and it says ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  mailx python-gamin
The following NEW packages will be installed:
  fail2ban
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/82.4kB of archives.
After this operation, 614kB of additional disk space will be used.
Selecting previously deselected package fail2ban.
(Reading database ... 31636 files and directories currently installed.)
Unpacking fail2ban (from .../fail2ban_0.8.2-2_all.deb) ...
Setting up fail2ban (0.8.2-2) ...


```

and it seems like it works fine, but it doesn't create anything.  In /etc/fail2ban there are just the two folders but no config files or scripts or anything.

Where do I go from here?

P.S. there is nothing in the fail2ban log

Thanks!

---

### Post by HermanAB on 2008-05-12
Don't use fail2ban.  It is better to use generic new connection throttling, since that works against any and all DOS attacks.

Do a google for "iptables rate limit"

This kind of problem is best handled by netfilter.

Cheers,

Herman

---

### Post by dacool25 on 2008-05-12
Does the rate limit work for ftp, courier, apache, imap and log them as well?

---

### Post by brigux on 2008-05-15
I'd suggest you to download the source from:
[http://sourceforge.net/project/showfiles.php?group_id=121032](http://sourceforge.net/project/showfiles.php?group_id=121032)
then install it again following the readme (very simple)
I had some issues too with the ubuntu repository while upgrading, a fresh install from the source solved it.

---

### Post by HermanAB on 2008-05-15
Rate limiting works against any and all DOS and exhaustive search attacks.

---

### Post by Fireal on 2008-05-15
> Now I thought I'd try that again.  I removed it and then did a locate fail2ban and deleted most of the instances of it besides the things in /var/lib/dpkg/info/

and it seems like it works fine, but it doesn't create anything.  In /etc/fail2ban there are just the two folders but no config files or scripts or anything.

Try:
```
sudo apt-get purge fail2ban
```
then install again,  
```
sudo apt-get install fail2ban
```

I think when you manually delete config files, package managers sometimes still think they are still there.  This should make apt-get think they are deleted so it will put them back in /etc/fail2ban when you install.

---

### Post by wolfchri on 2008-05-15
Hello,

same here: fail2ban simply does nothing.... Now it so bad that although is was started and even restarted, there are no log entries, let alone banning of any kind. Does not show up in htop.

However, also no error message in the terminal when restarting it, nor any other output. Just nothing. 

I beginning to lose faith in Ubuntu 8.04 server as there are also bad problems with Aide and PAM modules. :confused:

Any ideas other than installing it from source (then, why is it in the repos???)

---

### Post by wolfchri on 2008-05-15
Update: After I purged fail2ban and reinstalled it, it worked. Strange. I installed it from scratch before, did not touch the configs - did not work. Now it does. 

Well, I guess the answer to this is also "42".....

---

