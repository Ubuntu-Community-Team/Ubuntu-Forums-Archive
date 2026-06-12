---
title: "PCI-DSS Compliance and PHP"
date: 2012-10-22
forum: Security
---

### Post by coldlamper on 2012-10-22
I'm trying to make my server PCI-DSS compliant.  I run a third party scanner and it tells me this:

> PHP < 5.3.15 or PHP < 5.4.5 Multiple Vulnerabilities

- An unspecified overflow vulnerability exists in the function '_php_stream_scandir' in the file 'main/streams/streams.c'. (CVE-2012-2688)
- An unspecified error exists that can allow the 'open_basedir' constraint to be bypassed.(CVE-2012-3365) 

I'm running Ubunutu Server 12.04 LTS, I installed php5 with apt-get. php -v reports PHP 5.3.10-1ubuntu3.4.
At the time of this post, when I look at the change logs at [http://changelogs.ubuntu.com/changelogs/pool/main/p/php5/php5_5.3.10-1ubuntu3.4/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/p/php5/php5_5.3.10-1ubuntu3.4/changelog) I can see CVE-2012-2688 is resolved but CVE-2012-3365 is not.

PHP 5.3.10-1ubuntu3.4 is the latest package.  What's the best resolve this.  Do I need to compile from source or should I wait for a package update?  Compiling seems like it could cause a lot of issues and also i would have to recompile for each update.

I was using Ubuntu 10.04 and installed 12.04 to fix pci-dss compliance issues. I was surprised(i just assumed it would be,my own fault) when I found out the latest packaged version of php isn't compliant.  Any ideas on whats the best way to deal with this.?   
   
Thanks,Brian

---

### Post by CharlesA on 2012-10-23
This one has been fixed:

[http://people.canonical.com/~ubuntu-security/cve/2012/CVE-2012-2688.html](http://people.canonical.com/~ubuntu-security/cve/2012/CVE-2012-2688.html)

This one has been ignored due to it not being a security issue:

[http://people.canonical.com/~ubuntu-security/cve/2012/CVE-2012-3365.html](http://people.canonical.com/~ubuntu-security/cve/2012/CVE-2012-3365.html)

[https://bugzilla.redhat.com/show_bug.cgi?id=169857](https://bugzilla.redhat.com/show_bug.cgi?id=169857)

---

### Post by coldlamper on 2012-10-23
Thanks for the info.  I'm required to pass the 3rd party scanner to get PCI-DSS compliant.  Ubunutu may say it's not a security risk but PCI-DSS says it is.  So what can I do?

---

### Post by CharlesA on 2012-10-23
RedHat says it isn't a security risk either because those features aren't supposed to be used as security features.

Your best bet would be to compile PHP from source, but then you are going to be tasked with keeping it up to date (and the possible breakage that goes along with it).

Also see here:
[http://www.php.net/security-note.php](http://www.php.net/security-note.php)

---

### Post by coldlamper on 2012-10-23
That's what I was thinking. But like you said compiling yourself creates more work on updates and may possibly cause more problems than you would fix. This really puts you in a bind if you want to use Ubunutu and PHP and be PCI-DSS compliant.  Guess compiling is the only option.
Thanks for the help.

---

### Post by samiux on 2012-10-23
> **coldlamper said:**
> That's what I was thinking. But like you said compiling yourself creates more work on updates and may possibly cause more problems than you would fix. This really puts you in a bind if you want to use Ubunutu and PHP and be PCI-DSS compliant.  Guess compiling is the only option.
Thanks for the help.

I wonder why you not pentest your PHP application yourself to confirm that if it is vulnerabilty to the CVE-2012-3365 or not?

Samiux

---

### Post by coldlamper on 2012-10-23
Because I don't think that it is questionable if the vulnerability is there or not.  

Am I wrong in thinking that?

---

### Post by samiux on 2012-10-23
> **coldlamper said:**
> Because I don't think that it is questionable if the vulnerability is there or not.  

Am I wrong in thinking that?

In my opinion, if there is a known vulnerability, it is a high risk for your network/application.

So that, you should make sure if the vulnerability is existed in your application/network or not.

If the vulnerability is existed, you need to fix it by applying the security patches or setting up some snort rules (or IDS/IPS rules).

However, it is very hard to proof your network/application is 100% free from vulnerability as some of the vulnerabilities are not disclosed or discovered.

Samiux

---

### Post by gcornelisse on 2013-02-27
Hey guys...  I'm having this same problem too. I REALLY, REALLY don't want to compile PHP from source even though I know how to.  Is there any way to force PHP up to 5.3.15?

I've tried disputing these issues with the compliance service but they're about as useful as talking to a rock.

---

