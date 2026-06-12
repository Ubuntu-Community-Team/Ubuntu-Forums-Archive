---
title: "Broken Packages"
date: 2010-05-16
forum: Server Platforms
---

### Post by c0mputerking on 2010-05-16
Hello all i am having some errors with APT and mostly Bacula on my 8.04LST server.

```

apt-get install php5-curl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  bacula-director-mysql: Depends: bacula-director-common (= 2.2.8-5ubuntu7.2) but it is not going to be installed
  php5-curl: Depends: libcurl3 (>= 7.16.2-1) but it is not going to be installed
             Depends: php5-common (= 5.2.4-2ubuntu5.10) but 5.2.9-0.dotdeb.2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```of course i have tried 'apt-get -f install' as well as reinstalling and removing the bacula packages.  did a dpkg --configure -a still get these errors.

The bacula package that comes with 8.04 is way to old so awhile back i installed 3.0.2 from source and I think this is what is causing my problems.

I really need to get php5-curl installed and am not sure what the error about php5-common meas looks like somewhere i may have had to install a newer version of that too. Need to get this all fixed as i need it to get paypal working in drupal6

---

### Post by Vegan on 2010-05-16
first make sure the catalog is up to date

```
sudo apt-get update
```

then update everthing

```
sudo apt-get upgrade
```

and clean up the mess

```
sudo apt-get autoremove
```

Then try your installer again

---

### Post by c0mputerking on 2010-05-16
I already did that! it comes back with some error about not being able to uninstall bacula-common and marks it as partially removed or something like that.  Tells me to run the stuff in my first post

---

### Post by c0mputerking on 2010-05-26
Ok I have made some progress cleaned up the bacula-common stuff and did a successful apt-get update, and apt-get upgrade on this however i still get the same error using apt-get install see below.  Also i get some recommendations now if i use aptitude however it wants to uninstall and downgrade some important looking things.  This is a production server and i do not want to break things can some help me further? 

oot@mx1:/var/www/bacula-web# apt-get install php5-curl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  php5-curl: Depends: php5-common (= 5.2.4-2ubuntu5.10) but 5.2.9-0.dotdeb.2 is to be installed
E: Broken packages


root@mx1:/var/www/bacula-web# aptitude install php5-curl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  php5-curl 
The following packages have been automatically kept back:
  libbind9-30 libdns35 libisc35 libisccc30 libisccfg30 liblwres30 
The following NEW packages will be automatically installed:
  libcurl3 
The following packages have been kept back:
  bind9 bind9-host dnsutils linux-headers-server linux-image-server 
  linux-server 
The following NEW packages will be installed:
  libcurl3 
0 packages upgraded, 2 newly installed, 0 to remove and 12 not upgraded.
Need to get 230kB of archives. After unpacking 537kB will be used.
The following packages have unmet dependencies:
  php5-curl: Depends: php5-common (= 5.2.4-2ubuntu5.10) but 5.2.9-0.dotdeb.2 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
libapache2-mod-php5
php5-cgi
php5-gd
php5-mysql
php5-xsl

Downgrade the following packages:
php5-cli [5.2.9-0.dotdeb.2 (now) -> 5.2.4-2ubuntu5.10 (hardy-updates,
hardy-security)]
php5-common [5.2.9-0.dotdeb.2 (now) -> 5.2.4-2ubuntu5.10 (hardy-updates,
hardy-security)]

Score is 395

Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.

---

### Post by c0mputerking on 2010-05-30
bump nobody has run across this problem?

---

### Post by dv3500ea on 2010-05-30
Try running ```
sudo apt-get install -f
```

Sorry, I didn't read carefully enough that you already tried this!!!

---

### Post by Vegan on 2010-05-30
Might be an idea to move to 10.04 as its now LTS and seems to be OK my my old backup machine. Still trying to scrape up some parts to get the new machine up.

---

### Post by c0mputerking on 2010-05-31
This is a production box with lots of bits and pieces do not really what, and shouldnt need to upgrade.   There are a bunch of clients on it and i do not want to break anything right now.  There hast to be a better option than upgrade to 10.04 dont get me wrong i am running 10.04 on this laptop right now and have been since alpha, but not ready to move the server over yet

---

### Post by stanleytberry on 2010-06-10
Bacula ... I have the same problem on 10.04.

Is there a solution, please?

---

### Post by c0mputerking on 2010-06-10
I am glad to see i am not the only one who has the problem, not glad to see that upgrading to 10.04 will likely not fix my problem.

---

### Post by Vegan on 2010-06-10
Looks like bacula has been abandoned then

---

