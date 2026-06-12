---
title: "apt-get dist-upgrade problems"
date: 2014-05-12
forum: Server Platforms
---

### Post by kosmokramer314 on 2014-05-12
I wasn't thinking and did a dist-upgrade without making a restore point and now I'm having issues with Apache..of course.  I'd prefer to roll back the changes instead of troubleshooting the existing environment to make it work again.  I have the list of packages that were modified and I need some guidance on how I should go about rolling back the changes if possible.

```
The following packages will be REMOVED:
  apache2.2-common libapache2-mod-perl2 libapache2-mod-python libapache2-mod-ruby libapache2-reload-perl

The following NEW packages will be installed:
  apache2-bin apache2-data dh-php5 libgd3 libicu52 libjson-c2 libonig2 libqdbm14 libvpx1 php5-json php5-readline pkg-php-tools

The following packages will be upgraded:
  apache2 apache2-mpm-prefork apache2.2-bin libapache2-mod-php5 libjson0 php-pear php5 php5-cli php5-common php5-curl php5-dev php5-gd
  php5-intl php5-mysql php5-sqlite
```

What I was thinking was to 
[LIST=3]
[*]reinstall the packages that were removed.[*]
[*]uninstall the packages that were added.[*]
[*]downgrade the packages that were upgraded one by one.[*]
[/LIST]

Will that accomplish what I'm trying to do, or am I screwed?  I'm needing to do this because Apache won't serve any pages to a browser now...

I get this error on the SSL site
[INDENT][FONT=Arial Narrow][SIZE=2]SSL connection error
Unable to make a secure connection to the server. This may be a problem with the server, or it may be requiring a client authentication certificate that you don't have.[/SIZE][/FONT][/INDENT]

And this error on the non SSL site:
[INDENT][FONT=Arial Narrow][SIZE=2]Your PHP installation appears to be missing the MySQL extension which is required by WordPress.[/SIZE][/FONT][/INDENT]

---

### Post by kosmokramer314 on 2014-05-12
Here are the actual packages from **/var/log/apt/history.log**, but how do I format these to specify the correct package to apt-get?

[INDENT]Start-Date: 2014-05-12  11:11:03
Commandline: apt-get dist-upgrade

Install: php5-readline:i386 (5.5.12+dfsg-2+deb.sury.org~precise+1, automatic), libicu52:i386 (52.1-1+debphp.org~precise+1, automatic), dh-php5:i386 (0.1+deb.sury.org~pr ecise+1, automatic), apache2-data:i386 (2.4.9-1+deb.sury.org~precise+1, automatic), libqdbm14:i386 (1.8.78-1build2, automatic), libjson-c2:i386 (0.11-4+deb.sury.org~pre cise+1, automatic), libonig2:i386 (5.9.1-1, automatic), libvpx1:i386 (1.0.0-1, automatic), libgd3:i386 (2.1.0-2~precise+1, automatic), pkg-php-tools:i386 (1.9+debphp.or g~precise+1, automatic), apache2-bin:i386 (2.4.9-1+deb.sury.org~precise+1, automatic), php5-json:i386 (1.3.4-3+deb.sury.org~precise+2, automatic)

Upgrade: php5:i386 (5.3.10-1ubuntu3.11, 5.5.12+dfsg-2+deb.sury.org~precise+1), apache2.2-bin:i386 (2.2.22-1ubuntu1.5, 2.4.9-1+deb.sury.org~precise+1), php5-sqlite:i386  (5.3.10-1ubuntu3.11, 5.5.12+dfsg-2+deb.sury.org~precise+1), apache2-mpm-prefork:i386 (2.2.22-1ubuntu1.5, 2.4.9-1+deb.sury.org~precise+1), php5-gd:i386 (5.3.10-1ubuntu3. 11, 5.5.12+dfsg-2+deb.sury.org~precise+1), apache2:i386 (2.2.22-1ubuntu1.5, 2.4.9-1+deb.sury.org~precise+1), libjson0:i386 (0.9-1ubuntu1, 0.11-4+deb.sury.org~precise+1) , php-pear:i386 (5.3.10-1ubuntu3.11, 5.5.12+dfsg-2+deb.sury.org~precise+1), php5-curl:i386 (5.3.10-1ubuntu3.11, 5.5.12+dfsg-2+deb.sury.org~precise+1), php5-intl:i386 (5 .3.10-1ubuntu3.11, 5.5.12+dfsg-2+deb.sury.org~precise+1), php5-mysql:i386 (5.3.10-1ubuntu3.11, 5.5.12+dfsg-2+deb.sury.org~precise+1), php5-cli:i386 (5.3.10-1ubuntu3.11,  5.5.12+dfsg-2+deb.sury.org~precise+1), php5-dev:i386 (5.3.10-1ubuntu3.11, 5.5.12+dfsg-2+deb.sury.org~precise+1), libapache2-mod-php5:i386 (5.3.10-1ubuntu3.11, 5.5.12+d fsg-2+deb.sury.org~precise+1), php5-common:i386 (5.3.10-1ubuntu3.11, 5.5.12+dfsg-2+deb.sury.org~precise+1)

Remove: libapache2-mod-python:i386 (3.3.1-9ubuntu1), libapache2-mod-ruby:i386 (1.2.6-2), libapache2-reload-perl:i386 (0.11-2), apache2.2-common:i386 (2.2.22-1ubuntu1.5) , libapache2-mod-perl2:i386 (2.0.5-5ubuntu1)
End-Date: 2014-05-12  11:12:32[/INDENT]

---

### Post by bapoumba on 2014-05-12
Looks like you have a ppa with some packages that are not even in the ubuntu precise repos.

If I look for the first one php5-readline5.5.12 , the trusty repo shows 5.5.9+dfsg-1ubuntu4: amd64 i386 : [http://packages.ubuntu.com/search?suite=trusty&section=all&arch=any&keywords=php5-readline&searchon=names](http://packages.ubuntu.com/search?suite=trusty&section=all&arch=any&keywords=php5-readline&searchon=names)
So your ppa brought in a version higher than the trusty repo, probably with the dependencies or as a dependency.

So what Ubuntu version are you using ? Any other ppa than deb.sury.org~precise (not sure which one this is) ?

```
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d

```

First idea : remove the packages and ppa you are using with ppa-purge : [https://launchpad.net/ubuntu/+source/ppa-purge](https://launchpad.net/ubuntu/+source/ppa-purge)
ppa-purge will revert the packages back to your distribution ones. Then straiten your dependency tree, and reconsider the ppa and packages versions you need.

---

### Post by kosmokramer314 on 2014-05-12
```
$ cat /etc/apt/sources.list
#

# deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820.2)]/ precise main restricted

# deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820.2)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu precise main
# deb-src http://extras.ubuntu.com/ubuntu precise main

```

```
$ ls /etc/apt/sources.list.d
arnaud-hartmann-glances-stable-precise.list       google.list.save                      ondrej-php5-precise.list
arnaud-hartmann-glances-stable-precise.list.save  jcfp-ppa-precise.list                 ondrej-php5-precise.list.save
chris-lea-node_js-precise.list                    jcfp-ppa-precise.list.save            plexmediaserver.list
chris-lea-node_js-precise.list.save               malte_swart-dovecot-2_2-precise.list  plexmediaserver.list.save

```

---

### Post by bapoumba on 2014-05-12
You need to have a look at the ppas in /etc/apt/sources.list.d and find which ones are for deb.sury.org and debphp.org. In the ppa repos, the syntax is the same as for the sources.list file.
Once you found the faulty repos, you can install ppa-purge and purge them along with the file they installed.

Do you know why you are using each ppa and the packages you were looking for by using them ? Would the distribution packages fit your needs ?

---

### Post by kosmokramer314 on 2014-05-12
I'm not sure which repo's to turn off since I need to keep some packages at their current level for my other applications to work properly.  I think if I can get the Apache installation fixed, I'd be good to go

---

### Post by bapoumba on 2014-05-12
> **kosmokramer314 said:**
> I'm not sure which repo's to turn off since I need to keep some packages at their current level for my other applications to work properly.  I think if I can get the Apache installation fixed, I'd be good to go

As you dist-upgraded, all higher versions available from all repos were installed.

```
cat /etc/apt/sources.list.d/<ppa_name>.list
```
will show you the ppa repos. Which one have the two I mentioned earlier ?

If you need particular versions of packages, would a later ubuntu release fit your needs ?
But you need first to fix you current status.

---

### Post by kosmokramer314 on 2014-05-12
> **bapoumba said:**
> 
Do you know why you are using each ppa and the packages you were looking for by using them ? Would the distribution packages fit your needs ?

**for the system monitoring utility called Glances**
arnaud-hartmann-glances-stable-precise.list
arnaud-hartmann-glances-stable-precise.list.save

**nodeRed dev platform**
chris-lea-node_js-precise.list
chris-lea-node_js-precise.list.save                 

**no idea why this is here**
ondrej-php5-precise.list
ondrej-php5-precise.list.save

**removed list when uninstalled chrome**
google.list.save

**don't know**
jcfp-ppa-precise.list 
jcfp-ppa-precise.list.save

**media server**
plexmediaserver.list
plexmediaserver.list.save

**dovecot email server**
malte_swart-dovecot-2_2-precise.list


I ran across this just now when searching for ondrejphp5 [http://www.jamestitcumb.com/posts/downgrading-ondrejphp5-to-ondrejphp5-oldstable](http://www.jamestitcumb.com/posts/downgrading-ondrejphp5-to-ondrejphp5-oldstable)  I think I found the culprit

---

### Post by bapoumba on 2014-05-12
So could you ppa-purge the ondrej-php5-precise ? Listed as "no idea why this is here" :)

---

### Post by kosmokramer314 on 2014-05-12
I was able to get most of my configuration back and functioning, but for some reason my vhosts is messed up and only serving the HTTPS site.  the default HTTP site is loading instead of the site I have stood up to be served on port 80...probably need to mess around more with the a2enmod settings and the vhosts file..nothing terrible.  Thank you for getting me on the right track!

---

### Post by bapoumba on 2014-05-13
Very glad you fixed it :)
For the other server issue, it may be better you start a new thread with details, and maybe link here for refs.

---

