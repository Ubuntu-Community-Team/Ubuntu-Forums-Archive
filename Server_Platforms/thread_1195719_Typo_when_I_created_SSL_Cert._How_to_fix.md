---
title: "Typo when I created SSL Cert. How to fix?"
date: 2009-06-24
forum: Server Platforms
---

### Post by mewbie on 2009-06-24
I'm using: Linux Debian / apache2-mpm-prefork 2.2.9-10+lenny2
Apache/2.2.9 (Debian) PHP/5.2.6-1+lenny3 with Suhosin-Patch mod_python/3.3.1 Python/2.5.2 mod_ssl/2.2.9 OpenSSL/0.9.8g mod_perl/2.0.4 Perl/v5.10.0

(I followed the instructions here [http://ubuntuforums.org/archive/index.php/t-405786.html](http://ubuntuforums.org/archive/index.php/t-405786.html))

**My https does work**, but I must have made a typo when creating my ssl-cert as I have this error in logs:
[Sun Jun 07 18:16:44 2009] [warn] RSA server certificate CommonName (CN) `**lo**mysite.com' does NOT match server name!?

And on my saved cert in firefox it says **lo**mysite.com

the '**lo**' shouldn't be there, maybe it said localhost and I didn't clear it when making cert. This is how 

_This is how I made the cert:_
[B]mkdir /etc/apache2/ssl
/usr/sbin/make-ssl-cert /usr/share/ssl-cert/ssleay.cnf /etc/apache2/ssl/apache.pem [/B]

When I try to repeat those steps to fix it I get permission denied. 
Is there a way to edit it or should I just delete 'apache.pem' then the same steps will work again? I'm scared to delete it and then https not work at all..

*Also I'd rather just make one with site name: 'none'* as I read this is what one should do to use the same cert for virtual host names to allow same ports to be used for different apps (like apache2 ssl port 443 and ajaxterm port 443) ([http://www.davekb.com/browse_computer_tips:you_should_not_use_name_based_virtual_hosts_in_conjunction_with_ssl:txt](http://www.davekb.com/browse_computer_tips:you_should_not_use_name_based_virtual_hosts_in_conjunction_with_ssl:txt))

Thank you for your time :D

---

### Post by mewbie on 2009-06-27
Solved it, was easy.. just being a scaredy cat. 
Will post how I fixed it just in case anyone with same problem:
I renamed the file apache.pem to anything to be safe instead of deleting it. It's here: /etc/apache2/ssl/apache.pem 
Then I run the same cmd again:
/usr/sbin/make-ssl-cert /usr/share/ssl-cert/ssleay.cnf /etc/apache2/ssl/apache.pem 

It prompts me, as before, only for commonName' field of which I fixed the typo.
/etc/init.d/apache2 restart

Done, no more errors

:popcorn:

---

