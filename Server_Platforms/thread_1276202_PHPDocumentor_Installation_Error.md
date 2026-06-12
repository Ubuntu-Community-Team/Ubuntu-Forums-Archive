---
title: "PHPDocumentor Installation Error?"
date: 2009-09-26
forum: Server Platforms
---

### Post by CCKrause on 2009-09-26
[FONT=Verdana][SIZE=3]I'm currently trying to create a PHP dev environment under Ubuntu 9.04 [/SIZE][/FONT][FONT=Verdana][SIZE=3]- admittedly with less than expert experience with Ubuntu/Linux (just over a month).[/SIZE][/FONT]
[FONT=Verdana][SIZE=3]
I've installed NetBeans 6.7.1, Subversion, Selenium, and PHPUnit - all which seem to work well together.
What I'm trying to do now is install CruiseControl and [/SIZE][/FONT][FONT=Verdana][SIZE=3]phpUnderControl as a continuous integration server and I've run into a problem.

When I try and install [/SIZE][/FONT][FONT=Verdana][SIZE=3]phpUnderControl I get the following error:[/SIZE][/FONT]
[FONT=Verdana][SIZE=3]
[/SIZE][/FONT][FONT=Courier New][SIZE=3]cckrause@Vedexent:~$ sudo pear install --alldeps phpunit/phpUnderControl
[sudo] password for cckrause: 
phpunit/phpUnderControl requires package "pear/PhpDocumentor" (version >= 1.4.0), installed version is 
No valid packages found
install failed

[/SIZE][/FONT][FONT=Verdana][SIZE=3]So, I tried to install PhpDocumentor with the the following results:[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]
cckrause@Vedexent:~$ sudo pear install PhpDocumentor
downloading PhpDocumentor-1.4.3.tgz ...
Starting to download PhpDocumentor-1.4.3.tgz (2,423,486 bytes)
....................................done: 2,423,486 bytes
ERROR: pear.php.net/PhpDocumentor not installed
cckrause@Vedexent:~$ [/SIZE][/FONT]

[FONT=Verdana][SIZE=3]I find the failure perplexing. There isn't an error listed, it's just ERORR.

Does anyone have any idea what might be happening here, how it might be fixed, or even where I might look to find **what **error is occuring?


[/SIZE][/FONT] [FONT=Courier New][SIZE=3]
[/SIZE][/FONT]

---

### Post by CCKrause on 2009-09-27
Tried another route using a plain PEAR install: 

[FONT=Courier New]cckrause@Vedexent:~$ sudo pear upgrade PhpDocumentor
[sudo] password for cckrause: 

Warning: in_array(): Wrong datatype for second argument in PEAR/REST/10.php on line 703

Warning: in_array(): Wrong datatype for second argument in /usr/share/php/PEAR/REST/10.php on line 703

Call Stack:
    0.0064     358456   1. {main}() /usr/share/php/pearcmd.php:0
    0.3165    4755048   2. PEAR_Command_Common->run() /usr/share/php/pearcmd.php:305
    0.3165    4755048   3. PEAR_Command_Install->doInstall() /usr/share/php/PEAR/Command/Common.php:271
    0.4578    8383336   4. PEAR_Command_Install->_filterUptodatePackages() /usr/share/php/PEAR/Command/Install.php:619
    0.4920    9033704   5. PEAR_REST_10->listLatestUpgrades() /usr/share/php/PEAR/Command/Install.php:1231
    9.3355    9331664   6. in_array() /usr/share/php/PEAR/REST/10.php:703

downloading PhpDocumentor-1.4.3.tgz ...
Starting to download PhpDocumentor-1.4.3.tgz (2,423,486 bytes)
........................................done: 2,423,486 bytes
ERROR: pear.php.net/PhpDocumentor not installed[/FONT]

The errors in PEAR seemed alarming, so I tried to upgrade PEAR with the following results:


[FONT=Courier New]cckrause@Vedexent:~$ pear upgrade

Warning: in_array(): Wrong datatype for second argument in PEAR/REST/10.php on line 703

Warning: in_array(): Wrong datatype for second argument in /usr/share/php/PEAR/REST/10.php on line 703

Call Stack:
    0.0063     370448   1. {main}() /usr/share/php/pearcmd.php:0
    0.2295    4764120   2. PEAR_Command_Common->run() /usr/share/php/pearcmd.php:305
    0.2295    4764120   3. PEAR_Command_Install->doInstall() /usr/share/php/PEAR/Command/Common.php:271
    0.2834    7442592   4. PEAR_Command_Install->doUpgradeAll() /usr/share/php/PEAR/Command/Install.php:547
    0.2924    7456288   5. PEAR_Command_Install->doInstall() /usr/share/php/PEAR/Command/Install.php:900
    0.3708    8524856   6. PEAR_Command_Install->_filterUptodatePackages() /usr/share/php/PEAR/Command/Install.php:619
    0.9262    9258192   7. PEAR_REST_10->listLatestUpgrades() /usr/share/php/PEAR/Command/Install.php:1231
    1.0720    9491240   8. in_array() /usr/share/php/PEAR/REST/10.php:703


Release Warnings
================
C

C
[/FONT]
So, somehow, in the process of trying to install CruiseControl I've damaged PEAR?

If you look at the CruiseControl install instructions for Ubuntu here: [http://no-names.biz/2008/06/09/cruisecontrol-and-phpundercontrol-in-debian-etch/](http://no-names.biz/2008/06/09/cruisecontrol-and-phpundercontrol-in-debian-etch/) this is the process I followed - although I haven't gotten as far as getting PHPUnderControl installed, obviously.

Any idea how to proceed? Can I/Should I rip out and re-install PEAR completely?

Have I managed to corrupt some essential path someone (such as Java Home)?

---

### Post by CCKrause on 2009-09-27
OK - uninstalling and reinstalling PEAR via the Synaptic Package Manager has **no** effect on the system's responses when trying to upgrade/install PHPDocumentor, but the error for trying to upgrade PEAR itself has gone away.

[FONT=Courier New]cckrause@Vedexent:~$ pear upgrade
Nothing to upgrade[/FONT]

Still looking for **someone** who might have an idea what's going on - or can suggest an avenue of investigation.

Anyone?

---

### Post by ashnazg on 2009-09-27
There are some issues with the PEAR code that was included in PHP's 5.2.10 and 5.2.11 releases.  Some of the symptoms as seen from Karmic are this Ubuntu bug [1], since it's 5.2.10 that Karmic has packaged in its repository.

In your case, if the only visible issue you see is the "ERROR: {package} not installed", then perhaps it is the issue with the tarball not being unzipped properly [2].  Try adding the "-Z" argument to your install command, so that it will download the .tar file rather than the .tgz file.

* pear install -Z --alldeps phpunit/phpUnderControl


[1] -- [https://bugs.launchpad.net/ubuntu/+source/php5/+bug/420639](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/420639)
[2] -- [http://pear.php.net/bugs/bug.php?id=16606](http://pear.php.net/bugs/bug.php?id=16606)

---

### Post by CCKrause on 2009-09-27
OK - the saga continues.

I tried installing without the compression as you suggested, again with no success.

Digging around in the bug reports, and based on some odd messages about the default channel being a German domain channel - which I recall setting according to the CruiseControl instructions - I erased and reloaded the PEAR Channels with:

[FONT=Courier New]sudo rm -R /usr/share/php/.channels
[/FONT][FONT=Courier New] sudo pear update-channels[/FONT]

While I'm not getting any channel related messages, I **am** still getting errors with regards to PEAR itself:

[FONT=Courier New]Warning: in_array(): Wrong datatype for second argument in PEAR/REST/10.php on line 703

Warning: in_array(): Wrong datatype for second argument in /usr/share/php/PEAR/REST/10.php on line 703

Call Stack:
    0.0064     358456   1. {main}() /usr/share/php/pearcmd.php:0
    0.3165    4755048   2. PEAR_Command_Common->run() /usr/share/php/pearcmd.php:305
    0.3165    4755048   3. PEAR_Command_Install->doInstall() /usr/share/php/PEAR/Command/Common.php:271
    0.4578    8383336   4. PEAR_Command_Install->_filterUptodatePackages() /usr/share/php/PEAR/Command/Install.php:619
    0.4920    9033704   5. PEAR_REST_10->listLatestUpgrades() /usr/share/php/PEAR/Command/Install.php:1231
    9.3355    9331664   6. in_array() /usr/share/php/PEAR/REST/10.php:703[/FONT]

I'm having to do most operation under sudo to get anything to work anyway.

I find it perplexing/annoying that

a) PHPUnderControl won't load except with PHPDocumentor
b) PHPDocumentor won't **load**

At this point I'd be tempted to chuck it all and go with Xinc or some other CI server - but **they** will need PHPDocumentor as well :(

I'm getting close to ripping down Ubuntu and trying a fresh installation

---

