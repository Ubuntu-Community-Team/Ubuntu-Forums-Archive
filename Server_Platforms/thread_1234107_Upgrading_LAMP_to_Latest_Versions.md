---
title: "Upgrading LAMP to Latest Versions"
date: 2009-08-07
forum: Server Platforms
---

### Post by OctPhil on 2009-08-07
Hi,

I'm looking for some advice on moving to the most recent versions of Apache, PHP, and MySQL.  I need to have the most up to date versions to pass a mandated security scan.

I just installed Ubuntu server 8.04 on both a test machine and production server environment.  Using the default install gets me up to 5.2.4 for PHP and 2.2.8 for Apache.  That looks to be as far as apt-get is going to get me according to the package lists at [http://packages.ubuntu.com/hardy/web/](http://packages.ubuntu.com/hardy/web/).

To pass the security scan, I need PHP 5.2.10 and Apache 2.2.12.  Looks like even an upgrade to Jaunty won't clear that hurdle.  I've done some reading and realize I could compile and install from source, but it looks like there are likely headaches with that method.  I've also seen people suggest switching repositories (looks like [http://www.dotdeb.org/](http://www.dotdeb.org/) might be an option).

Can anyone speak to pros/cons of these options?  I'm wondering about things like the stability of my production server, how much of a headache I can expect for future upgrades, and whether my inexperience is completely missing an obvious solution.  Any thoughts would be appreciated.

Thanks!

---

### Post by cdenley on 2009-08-07
Anytime you install software that isn't from the ubuntu repos, you take a chance that you might encounter a problem with it not working properly. Ubuntu doesn't release new versions of packages for already-released versions of ubuntu for stability.
[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

They do, however, patch the older releases of software with the most recent security patches. I understand that you may need the newer version to be compliant with some rules or standards, but the apache 2.2.8 version in the repos shouldn't have any security vulnerabilities that don't exist in 2.2.12. It might even have less, since the non-critical changes in newer versions can actually create security vulnerabilities.

You can use the not-yet-released version of ubuntu (karmic, 9.10) which has apache 2.2.12, but it isn't released for a reason. Installing from source would probably be more stable, but more difficult to support. If you go with karmic, at least it will eventually be supported and stable.

You can also use debian with the unstable repo. It would probably be more stable than karmic at the moment, but it is called unstable for a reason. Don't expect too much help from the ubuntu community, though, although the two should be similar.

I would not try using repos which are not intended to be used with the distribution and version you are running.

---

### Post by OctPhil on 2009-08-07
Thanks, cdenley

I also noticed the unstable version of Debian had the latest updates, but had reservations.  Like you said, the name has a reason.

I'm intrigued by your note about the security vulnerabilities.  The security scan I recently underwent claims there are vulnerabilities that exist in my currently installed version of Apache and PHP.  I'm inclined to believe the report as it gave links to the CVE list for each vulnerability as well as I'm able to note security fixes in the 5.2.5 release of PHP.  [http://www.php.net/ChangeLog-5.php#5.2.5]("http://www.php.net/ChangeLog-5.php#5.2.5")

Sounds like I may be forced into installing from source and dealing with the fact that it will be harder to maintain.  I don't think I'm hearing any easy ways out.

---

### Post by cdenley on 2009-08-07
Those "security scanners" usually list vulnerabilities which existed when that version was originally released. They don't actually check for vulnerabilities, they check the version number which does not reflect patches applied by ubuntu's package maintainer. In other words, it lists all php5 vulnerabilities found since 30-August-2007. However, all security patches released should have been applied to 5.2.4 in the ubuntu repos. If not, you should file a bug report. This may be irrelevant, though, if you need the more current version regardless of whether those vulnerabilities listed actually apply to your software.

[http://changelogs.ubuntu.com/changelogs/pool/main/p/php5/php5_5.2.4-2ubuntu5.6/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/p/php5/php5_5.2.4-2ubuntu5.6/changelog)

---

### Post by OctPhil on 2009-08-07
I was unaware of this.  Thanks for the info!  Looks like I may be able to appeal the scan's findings.

---

### Post by TreborTech on 2009-09-18
This was a great find for me as this relates exactly to what boat I'm in.

What I would like to find out and I'm sure others would also find useful, is there a way to run a local check of the of files to confirm that all patches have been applied? Can we generate some kind of report to provide to auditors?

---

### Post by ukripper on 2009-09-18
> **TreborTech said:**
> This was a great find for me as this relates exactly to what boat I'm in.

What I would like to find out and I'm sure others would also find useful, is there a way to run a local check of the of files to confirm that all patches have been applied? Can we generate some kind of report to provide to auditors?

One of many options is to confirm the version number of any given package using below command:
```
dpkg -p package-name | grep Version*

```
And compare with CVEs published.

Second option is to use logwatch package to check what has been installed or updated.
For example it will display in log file as below:
```
--------------------- dpkg status changes Begin ------------------------ 
 Installed:
    libsensors4 1:3.0.0-4ubuntu2
    lm-sensors 1:3.0.0-4ubuntu2

```

---

