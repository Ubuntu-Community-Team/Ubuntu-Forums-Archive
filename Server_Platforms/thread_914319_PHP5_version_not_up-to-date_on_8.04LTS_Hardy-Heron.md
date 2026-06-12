---
title: "PHP5 version not up-to-date on 8.04LTS Hardy-Heron"
date: 2008-09-08
forum: Server Platforms
---

### Post by vtknightmare on 2008-09-08
Hello All:

I'm in the process of setting up a LAMP server for my org. and chose 8.04 LTS to be the Base OS, as I was very happy with 6.06 LTS :)

Due to new requirements from my developers however, I'm being forced to upgrade to PHP5.

After installing 8.04 LTS and checking the "LAMP Server" option during setup, then following up with the aptitude update/safe-upgrade/full-upgrade routine, I scanned the system via Nessus.

Nessus, pretty much sh17 itself, saying that the PHP version that is currently installed is older and vulnerable to several "bugs".

Now XSS attacks I'm not that worried about because we have a pretty good dev. crew and I have some QA routines in check to protect us against that sort of thing.

The other vuln.'s however I am concerned about. A list of what Nessus has found is below:

************************************************************************
<snip>

Synopsis :

The remote web server uses a version of PHP that is affected by
multiple flaws.

Description :

According to its banner, the version of PHP installed on the remote
host is older than 5.2.5. Such versions may be affected by various
issues, including but not limited to several buffer overflows.

See also :

[http://www.php.net/releases/5_2_5.php](http://www.php.net/releases/5_2_5.php)

Solution :

Upgrade to PHP version 5.2.5 or later.

Risk factor :

High / CVSS Base Score : 7.5
(CVSS2#AV:N/AC:L/Au:N/C:P/I:P/A:P)
CVE : CVE-2007-4887, CVE-2007-5898, CVE-2007-5900
BID : 26403
Other references : OSVDB:38680, OSVDB:38681, OSVDB:38682, OSVDB:38683, OSVDB:38684, OSVDB:38685

Nessus ID : 28181

************************************************************************

PHP < 5.2.6 Multiple Vulnerabilities

Synopsis :

The remote web server uses a version of PHP that is affected by
multiple flaws.

Description :

According to its banner, the version of PHP installed on the remote
host is older than 5.2.6. Such versions may be affected by the
following issues :

- A stack buffer overflow in FastCGI SAPI.

- An integer overflow in printf().

- An security issue arising from improper calculation
of the length of PATH_TRANSLATED in cgi_main.c.

- A safe_mode bypass in cURL.

- Incomplete handling of multibyte chars inside
escapeshellcmd().

- Issues in the bundled PCRE fixed by version 7.6.

See also :

[http://archives.neohapsis.com/archives/bugtraq/2008-03/0321.html](http://archives.neohapsis.com/archives/bugtraq/2008-03/0321.html)
[http://archives.neohapsis.com/archives/fulldisclosure/2008-05/0103.html](http://archives.neohapsis.com/archives/fulldisclosure/2008-05/0103.html)
[http://archives.neohapsis.com/archives/fulldisclosure/2008-05/0107.html](http://archives.neohapsis.com/archives/fulldisclosure/2008-05/0107.html)
[http://www.php.net/releases/5_2_6.php](http://www.php.net/releases/5_2_6.php)

Solution :

Upgrade to PHP version 5.2.6 or later.

Risk factor :

High / CVSS Base Score : 7.5
(CVSS2#AV:N/AC:L/Au:N/C:P/I:P/A:P)

Plugin output :

PHP version 5.2.4 appears to be running on the remote host based on
the following Server response header :

Server: Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch

CVE : CVE-2007-4850, CVE-2008-0599, CVE-2008-1384, CVE-2008-2050, CVE-2008-2051
BID : 27413, 28392, 29009
Other references : OSVDB:43219, OSVDB:44057, Secunia:30048

Nessus ID : 32123

</snip>
************************************************************************

So... now my question is... what is Ubuntu's policy when it comes to maintaining the PHP framework? In the RHEL world, they will backport "patches" so although you might have a "buggy" version installed it won't suffer from the issues known.

Does Ubuntu adhere to this? If not, how many of you have chosen to step outside of aptitude to manage your own PHP frameworks?

TIA for all answers/replies!

--VTK

---

### Post by RealPSL on 2008-09-08
This might not be the best documentation of that fact but the first paragraph seems to indicate that this is the case [https://help.ubuntu.com/community/UbuntuBackports]("https://help.ubuntu.com/community/UbuntuBackports")

---

### Post by vtknightmare on 2008-09-09
As a matter of fact I looked there... but everyone is whining that it's been taking forever for the ubuntu-backport team to get the 5.2.6 patches backported to 5.2.4

Some "guy" released an un-official 5.2.6 .deb and is saying this is at least better until ubuntu gets it's act together.

I'm still debating whether or not to wait on them or to go with the un-official deb, or just compile it myself...

Any heads up would be appreciated all :)

--VTK

---

