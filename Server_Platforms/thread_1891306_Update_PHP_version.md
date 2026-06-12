---
title: "Update PHP version"
date: 2011-12-05
forum: Server Platforms
---

### Post by lstanderfer on 2011-12-05
Hello all,

This is my first post to the Ubuntu Forums and I'm newer to Ubuntu, so please forgive if I misuse terms or accidentally omit any details.

I'm currently in process of deploying a front end web server that's running on Ubuntu 11.10 (no UI) with LAMP installed. We ran an AppSec assessment against the server and discovered that the current PHP version is 5.3.6 which has a few medium level CVE vulnerabilities. My question is is there a way to update our PHP to the latest version without having to download the source and compiling? If no, could someone please provide some guidance in how to accomplish the version update and have Apache2 reflect the updated version?

Thank you for your time in advance. 

Les

---

### Post by maverickaddicted on 2011-12-06
Check this -

[http://sudarmuthu.com/blog/installing-php-5-3-x-in-ubuntu-through-apt-get-or-aptitude](http://sudarmuthu.com/blog/installing-php-5-3-x-in-ubuntu-through-apt-get-or-aptitude)

---

### Post by lstanderfer on 2011-12-06
maverickaddicted-- Thank you for the link. I'll run through the blog steps today and report back the outcome.

Have a good day.

Les

---

### Post by lstanderfer on 2011-12-06
So I just stepped through the process identified in the link. The php version specified when installing the php libapache2-mod is still 5.3.6. I've also verified that the current version still 5.3.6 by using a phpinfo page.
 
Any ideas?
 
 
Les

---

### Post by maverickaddicted on 2011-12-06
Sorry for that link, but after doing some research. I was only able to get these two links - 

[http://php53.dotdeb.org/dists/oldstable/php5/binary-i386/](http://php53.dotdeb.org/dists/oldstable/php5/binary-i386/)
[http://www.dotdeb.org/2011/08/30/php-5-3-8-is-available/](http://www.dotdeb.org/2011/08/30/php-5-3-8-is-available/)

---

### Post by SeijiSensei on 2011-12-06
I did a bit of browsing and could not find any .deb repositories offering PHP 5.3.8.  It looks like you'd need to build it from scratch.

I looked up the vulnerabilities you mentioned.  The first, [CVE-2011-2202](http://web.nvd.nist.gov/view/vuln/detail?vulnId=CVE-2011-2202), concerns specially-crafted file name entries that exploit a problem in the file uploading functions.  If you don't allow uploading, this won't apply to you at all.  If you do, you can just add some code to the PHP scripts that checks to make sure you've been sent a valid name.  You should probably have been doing that already anyhow.

The other vulnerability, [CVE-2011-1938](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2011-1938) concerns a problem with the sockets_connect() function that can be exploited by long file names.  Do you use this function?

However a quick check shows that **patches to fix both these vulnerabilities were incorporated** into the [release version of PHP 5.3.2]("http://www.ubuntuupdates.org/packages/show/202115") for Ubuntu 10.10.  I would assume that haven't been removed in 5.3.6.

---

### Post by snowpine on 2011-12-06
You may find this article helpful (written for Red Hat but applies to Ubuntu as well): [https://access.redhat.com/security/updates/backporting/?sc_cid=3093](https://access.redhat.com/security/updates/backporting/?sc_cid=3093)

You can check the Ubuntu Changelog to verify whether PHP has been patched to your satisfaction: [http://changelogs.ubuntu.com/changelogs/pool/main/p/php5/php5_5.3.6-13ubuntu3.2/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/p/php5/php5_5.3.6-13ubuntu3.2/changelog)

---

### Post by lstanderfer on 2011-12-06
SeijiSensei-- Thank You for your post. This is a 3rd party Learning Management system that we are going to grant internal employees and external clients access to. Unfortunately, part of the site functionality is to allow various file types used by the different companies/groups to get uploaded. Concerning the long pathname, i'm not sure about this one,  I know there are no restrictions on the file names uploaded into the application.

Regards,

Les

---

### Post by lstanderfer on 2011-12-06
maverickaddicted and Snowpine-- Thank you for the links. I'll take a look at them this evening and provide feedback.


Les

---

### Post by SeijiSensei on 2011-12-07
I think you missed the part of my post pointing out that *these vulnerabilities have already been fixed* in the current version of PHP from Ubuntu.  It's not uncommon to "backport" security fixes into a package rather than upgrading to a new version.  Long-term releases like Ubuntu LTS or RedHat have followed this practice for years.

---

### Post by lstanderfer on 2011-12-07
SeijiSensei-- You are correct, I misinterpreted your response. I wasn't aware of the "back porting" practice and need to further investigate whether the PHP version vulnerability is a false-positive or still valid with our deployment.

Thanks again for your help.


Les

---

