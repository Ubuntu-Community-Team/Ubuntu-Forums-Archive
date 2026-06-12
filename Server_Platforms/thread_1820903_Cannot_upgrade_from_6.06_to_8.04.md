---
title: "Cannot upgrade from 6.06 to 8.04"
date: 2011-08-08
forum: Server Platforms
---

### Post by toshko3 on 2011-08-08
Hi, when I try to upgrade, using this HOWTO:
[https://help.ubuntu.com/community/EOLUpgrades/Dapper](https://help.ubuntu.com/community/EOLUpgrades/Dapper)
I encounter a problem. I cannot update the repositories:

```
root@mail:~# apt-get update
Get:1 http://old-releases.ubuntu.com dapper-backports Release.gpg [198B]
Ign http://archive.ubuntu.com dapper Release.gpg
Ign http://archive.ubuntu.com dapper-updates Release.gpg
Ign http://archive.ubuntu.com dapper-backports Release.gpg
Ign http://security.ubuntu.com dapper-security Release.gpg
Hit http://old-releases.ubuntu.com dapper-backports Release
Ign http://archive.ubuntu.com dapper Release                        
Ign http://archive.ubuntu.com dapper-updates Release                
Ign http://security.ubuntu.com dapper-security Release              
Ign http://archive.ubuntu.com dapper-backports Release
Ign http://archive.ubuntu.com dapper/main Packages
Ign http://archive.ubuntu.com dapper/restricted Packages
Ign http://archive.ubuntu.com dapper/universe Packages
Ign http://archive.ubuntu.com dapper/multiverse Packages
Hit http://old-releases.ubuntu.com dapper-backports/main/debian-installer Packages
Ign http://security.ubuntu.com dapper-security/main Packages
Ign http://archive.ubuntu.com dapper-updates/main Packages
Ign http://archive.ubuntu.com dapper-updates/restricted Packages
Ign http://archive.ubuntu.com dapper-updates/universe Packages
Ign http://archive.ubuntu.com dapper-updates/multiverse Packages
Ign http://archive.ubuntu.com dapper-backports/main/debian-installer Packages
Err http://archive.ubuntu.com dapper/main Packages
  404 Not Found [IP: 91.189.92.170 80]
Err http://archive.ubuntu.com dapper/restricted Packages
  404 Not Found [IP: 91.189.92.170 80]
Hit http://old-releases.ubuntu.com dapper-backports/main/debian-installer Packages
Ign http://security.ubuntu.com dapper-security/restricted Packages
Ign http://security.ubuntu.com dapper-security/universe Packages
Ign http://security.ubuntu.com dapper-security/multiverse Packages
Err http://archive.ubuntu.com dapper/universe Packages
  404 Not Found [IP: 91.189.92.170 80]
Err http://archive.ubuntu.com dapper/multiverse Packages
  404 Not Found [IP: 91.189.92.170 80]
Err http://archive.ubuntu.com dapper-updates/main Packages
  404 Not Found [IP: 91.189.92.170 80]
Err http://archive.ubuntu.com dapper-updates/restricted Packages
  404 Not Found [IP: 91.189.92.170 80]
Err http://archive.ubuntu.com dapper-updates/universe Packages
  404 Not Found [IP: 91.189.92.170 80]
Err http://archive.ubuntu.com dapper-updates/multiverse Packages
  404 Not Found [IP: 91.189.92.170 80]
Err http://archive.ubuntu.com dapper-backports/main/debian-installer Packages
  404 Not Found [IP: 91.189.92.170 80]
Err http://security.ubuntu.com dapper-security/main Packages
  404 Not Found
Err http://security.ubuntu.com dapper-security/restricted Packages
  404 Not Found
Err http://security.ubuntu.com dapper-security/universe Packages
  404 Not Found
Err http://security.ubuntu.com dapper-security/multiverse Packages
  404 Not Found
Fetched 1B in 0s (3B/s)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.170 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
root@mail:~#  
```

The /etc/apt/sources.list is as follows:
```

## EOL upgrade sources.list
# Required
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ dapper-security main restricted universe multiverse

# Optional
#deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

```

I don't get it! This is for 1 week already and not on only 1 server!:confused:

---

### Post by arrrghhh on 2011-08-08
Whew, that's an ancient release...

Have you seen this page as well?

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

You *might* want to consider a reinstall, and go straight to 10.04...

But if you must upgrade, read the page I posted.  You have to change your sources.list to reflect the "old-releases.ubuntu.com" - I don't think dapper is in the archives anymore...

Edit - just read the dapper page you linked, I think I see why you're confused!  June 2011 was when Dapper server edition went EOL, so I don't think they've updated the page yet... Try the above suggestion with old-releases, instead of archive...

---

### Post by dinu90 on 2011-08-08
the version is too old and has been discounted

You can try the upgrade like this. Change the /etc/apt/sources.list as follows:
```
[FONT=monospace]
## EOL upgrade sources.list
# Required
deb http://archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ hardy-security main restricted universe multiverse

# Optional
#deb http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
[/FONT]
```[FONT=monospace]

then run
```

apt-get update
apt-get upgrade

```

[**java tutorials**]("http://www.java-forums.org/java-tutorial/")
[/FONT]

---

### Post by toshko3 on 2011-08-08
I tried with this:
```
## EOL upgrade sources.list
# Required
deb http://old-releases.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ dapper-security main restricted universe multiverse
```

And get this:
```
root@mail:~# apt-get update
Get:1 http://old-releases.ubuntu.com dapper Release.gpg [189B]
Get:2 http://old-releases.ubuntu.com dapper-updates Release.gpg [198B]
Get:3 http://old-releases.ubuntu.com dapper-security Release.gpg [198B]
Ign http://archive.ubuntu.com dapper-backports Release.gpg
Get:4 http://old-releases.ubuntu.com dapper-backports Release.gpg [198B]
Hit http://old-releases.ubuntu.com dapper Release
Ign http://archive.ubuntu.com dapper-backports Release
Hit http://old-releases.ubuntu.com dapper-updates Release           
Hit http://old-releases.ubuntu.com dapper-security Release
Ign http://archive.ubuntu.com dapper-backports/main/debian-installer Packages
Hit http://old-releases.ubuntu.com dapper-backports Release         
Err http://archive.ubuntu.com dapper-backports/main/debian-installer Packages
  404 Not Found [IP: 91.189.92.171 80]
Hit http://old-releases.ubuntu.com dapper/main Packages
Hit http://old-releases.ubuntu.com dapper/restricted Packages
Hit http://old-releases.ubuntu.com dapper/universe Packages
Hit http://old-releases.ubuntu.com dapper/multiverse Packages
Hit http://old-releases.ubuntu.com dapper-updates/main Packages
Hit http://old-releases.ubuntu.com dapper-updates/restricted Packages
Hit http://old-releases.ubuntu.com dapper-updates/universe Packages
Hit http://old-releases.ubuntu.com dapper-updates/multiverse Packages
Hit http://old-releases.ubuntu.com dapper-security/main Packages
Hit http://old-releases.ubuntu.com dapper-security/restricted Packages
Hit http://old-releases.ubuntu.com dapper-security/universe Packages
Hit http://old-releases.ubuntu.com dapper-security/multiverse Packages
Hit http://old-releases.ubuntu.com dapper-backports/main/debian-installer Packages
Hit http://old-releases.ubuntu.com dapper-backports/main/debian-installer Packages
Fetched 4B in 0s (11B/s) 
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/debian-installer/binary-i386/Packages.gz  404 Not Found [IP: 91.189.92.171 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

:(
Also, I don't see why it tries to get any backports packages???

---

### Post by psusi on 2011-08-08
It sounds like you have additional listings in /etc/sources.list.d/.  Make sure you remove those as well.

Also 8.04 is depreciated now, and a double upgrade will take forever, so you are probably better off doing a clean install of 10.04.

---

### Post by arrrghhh on 2011-08-08
> **psusi said:**
> It sounds like you have additional listings in /etc/sources.list.d/.  Make sure you remove those as well.

Also 8.04 is depreciated now, and a double upgrade will take forever, so you are probably better off doing a clean install of 10.04.

8.04 server edition is supported until April 2013... see [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

To the OP, I would make sure you *only* have old-releases in sources.list.  Either you have [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports in your sources.list somewhere, or like the previous poster said you might have additional entries in sources.list.d.

As for upgrading, if it's not too much of a hassle going straight to a new install of 10.04 might be the easiest option.  If you're hell-bent on upgrading, we can try to help you.. just be wary that upgrades don't always go well.  Fresh installs usually have a much better chance of success and functioning well ;).

---

### Post by psusi on 2011-08-08
> **arrrghhh said:**
> 8.04 server edition is supported until April 2013... see [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)


I didn't say it wasn't supported; I said it is depreciated.  While certain designated packages will continue to get critical security fixes until 2013, those are the only updates it's going to get; no other bugs will be fixed.  You also very well may have packages installed that are not part of the 5 year support and so they aren't even getting security fixes.  This is why it is strongly recommended to run the current LTS release: 10.04.

---

### Post by arrrghhh on 2011-08-08
> **psusi said:**
> I didn't say it wasn't supported; I said it is depreciated.  While certain designated packages will continue to get critical security fixes until 2013, those are the only updates it's going to get; no other bugs will be fixed.  You also very well may have packages installed that are not part of the 5 year support and so they aren't even getting security fixes.  This is why it is strongly recommended to run the current LTS release: 10.04.

Agreed on getting up to 10.04 - to the OP, you're going to want to get yourself on this release one way or another... again, fresh install might be the best route since you're on such an old release...

I just didn't want the OP thinking 8.04 was completely unsupported :p.

---

### Post by toshko3 on 2011-08-09
Thanks, I removed the backports lines from this file:
/etc/apt/sources.list.d/prerequists-sources.dapper.list
and now it doesn't look for them.
BUT, now there is another problem - when I run "do-release-upgrade" it tells me that there is hardy ..... do you want to continue? (yN)
I type "y" and it kills itself with no message at all.:confused:

---

### Post by Wim Sturkenboom on 2011-08-09
As this is the server section, 6.06 is NOT old ;) Only reached end-of-life in june.

I agree that it's best to do a fresh install. I went the upgrade-route (on the desktop version) and 6.06 to 8.04 went fine but 8.04 to 10.04 failed (possibly because of something additional that I installed from the repositories while on 8.04).

---

### Post by psusi on 2011-08-09
> **Wim Sturkenboom said:**
> As this is the server section, 6.06 is NOT old ;) Only reached end-of-life in june.


That MAKES it old.  Actually, it has been old since 2008, it just went off life support two months ago.

---

### Post by arrrghhh on 2011-08-09
> **psusi said:**
> That MAKES it old.  Actually, it has been old since 2008, it just went off life support two months ago.

Yes, yes, that's fine.  Can we stop arguing about it and focus on helping the OP?

> **toshko3 said:**
> Thanks, I removed the backports lines from this file:
/etc/apt/sources.list.d/prerequists-sources.dapper.list
and now it doesn't look for them.
BUT, now there is another problem - when I run "do-release-upgrade" it tells me that there is hardy ..... do you want to continue? (yN)
I type "y" and it kills itself with no message at all.:confused:

Ok.  Have you considered a fresh install?  You seem to be ignoring all of those suggestions.  Much less headache... trust me.

However, we'll still *try* to help you upgrade, just know that it's not going to be easy - as you've found already :p.

So before the do-release-upgrade, you ran ```
sudo aptitude update && sudo aptitude upgrade
``` Right?

Then you do ```
**sudo** do-release-upgrade
```

Let us know how that works.

PS - in the future, you should ***always*** upgrade before the product is completely unsupported.  That's one of the reasons you're getting such negative comments - you've had 2 years to get off of 6.06...

---

### Post by toshko3 on 2011-08-10
OK, I did a language change and it is now OK. It didn't get the "y" as it should. Now the problem is that it always puts the "backports" in the "/etc/apt/sources.list.d/prerequists-sources.dapper.list" file and I cannot do the release upgrade. I delete them and after doing "do-release-upgrade" it puts them again and cannot connect to them, therefore giving me this error:
```
Getting upgrade prerequisites failed 

The system was unable to get the prerequisites for the upgrade. The 
upgrade will abort now and restore the original system state. 

Please report this as a bug against the 'update-manager' package and 
include the files in /var/log/dist-upgrade/ in the bugreport. 


Restoring original system state

Aborting
```

By the way, I don't have physical access to the server and it will be very hard to reinstall the server. I know it is old and in the future will not wait for the support to end, for sure :D

---

### Post by toshko3 on 2011-08-10
And YES:
1. I empty the "/etc/apt/sources.list.d/prerequists-sources.dapper.list" file, after this there are only these lines in the /etc/apt/sources.list:
```
## EOL upgrade sources.list
# Required
deb http://old-releases.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ dapper-security main restricted universe multiverse

```
2. I do "aptitude update" and it is perfect, not wanting the "backports"
3. I run "do-release-upgrade" and it shows this:
```
oot@mail:~# do-release-upgrade 
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading            
extracting 'hardy.tar.gz'
authenticate 'hardy.tar.gz' against 'hardy.tar.gz.gpg' 

Reading cache

Checking package manager
Reading package lists: Done
Building dependency tree: Done
Building dependency tree: Done
Building dependency tree: Done
WARNING: Failed to read mirror file
Ignored http://archive.ubuntu.com dapper-backports Release.gpg
Failed http://archive.ubuntu.com dapper-backports Release.gpg
Done http://old-releases.ubuntu.com dapper Release.gpg
Done http://old-releases.ubuntu.com dapper-updates Release.gpg
Done http://old-releases.ubuntu.com dapper-security Release.gpg
Ignored http://archive.ubuntu.com dapper-backports Release
Failed http://archive.ubuntu.com dapper-backports Release
Hit http://old-releases.ubuntu.com dapper Release
Hit http://old-releases.ubuntu.com dapper-updates Release
Done http://old-releases.ubuntu.com dapper Release
Done http://old-releases.ubuntu.com dapper-updates Release
Ignored http://archive.ubuntu.com dapper-backports/main/debian-installer Packages
Failed http://archive.ubuntu.com dapper-backports/main/debian-installer Packages
Hit http://old-releases.ubuntu.com dapper-security Release
Done http://old-releases.ubuntu.com dapper-security Release
Failed http://archive.ubuntu.com dapper-backports/main/debian-installer Packages
Hit http://old-releases.ubuntu.com dapper/main Packages
Hit http://old-releases.ubuntu.com dapper/restricted Packages
Hit http://old-releases.ubuntu.com dapper/universe Packages
Hit http://old-releases.ubuntu.com dapper/multiverse Packages
Hit http://old-releases.ubuntu.com dapper-updates/main Packages
Hit http://old-releases.ubuntu.com dapper-updates/restricted Packages
Hit http://old-releases.ubuntu.com dapper-updates/universe Packages
Hit http://old-releases.ubuntu.com dapper-updates/multiverse Packages
Hit http://old-releases.ubuntu.com dapper-security/main Packages
Hit http://old-releases.ubuntu.com dapper-security/restricted Packages
Hit http://old-releases.ubuntu.com dapper-security/universe Packages
Hit http://old-releases.ubuntu.com dapper-security/multiverse Packages
Done downloading            
Done http://old-releases.ubuntu.com dapper Release.gpg
Done http://old-releases.ubuntu.com dapper-updates Release.gpg
Done http://old-releases.ubuntu.com dapper-security Release.gpg
Ignored http://archive.ubuntu.com dapper-backports Release.gpg
Failed http://archive.ubuntu.com dapper-backports Release.gpg
Hit http://old-releases.ubuntu.com dapper Release
Hit http://old-releases.ubuntu.com dapper-updates Release
Ignored http://archive.ubuntu.com dapper-backports Release
Failed http://archive.ubuntu.com dapper-backports Release
Done http://old-releases.ubuntu.com dapper Release
Done http://old-releases.ubuntu.com dapper-updates Release
Hit http://old-releases.ubuntu.com dapper-security Release
Ignored http://archive.ubuntu.com dapper-backports/main/debian-installer Packages
Failed http://archive.ubuntu.com dapper-backports/main/debian-installer Packages
Done http://old-releases.ubuntu.com dapper-security Release
Hit http://old-releases.ubuntu.com dapper/main Packages
Hit http://old-releases.ubuntu.com dapper/restricted Packages
Hit http://old-releases.ubuntu.com dapper/universe Packages
Hit http://old-releases.ubuntu.com dapper/multiverse Packages
Hit http://old-releases.ubuntu.com dapper-updates/main Packages
Hit http://old-releases.ubuntu.com dapper-updates/restricted Packages
Failed http://archive.ubuntu.com dapper-backports/main/debian-installer Packages
Hit http://old-releases.ubuntu.com dapper-updates/universe Packages
Hit http://old-releases.ubuntu.com dapper-updates/multiverse Packages
Hit http://old-releases.ubuntu.com dapper-security/main Packages
Hit http://old-releases.ubuntu.com dapper-security/restricted Packages
Hit http://old-releases.ubuntu.com dapper-security/universe Packages
Hit http://old-releases.ubuntu.com dapper-security/multiverse Packages
Done downloading            
Ignored http://archive.ubuntu.com dapper-backports Release.gpg
Failed http://archive.ubuntu.com dapper-backports Release.gpg
Done http://old-releases.ubuntu.com dapper Release.gpg
Done http://old-releases.ubuntu.com dapper-updates Release.gpg
Done http://old-releases.ubuntu.com dapper-security Release.gpg
Ignored http://archive.ubuntu.com dapper-backports Release
Failed http://archive.ubuntu.com dapper-backports Release
Hit http://old-releases.ubuntu.com dapper Release
Hit http://old-releases.ubuntu.com dapper-updates Release
Done http://old-releases.ubuntu.com dapper Release
Done http://old-releases.ubuntu.com dapper-updates Release
Ignored http://archive.ubuntu.com dapper-backports/main/debian-installer Packages
Failed http://archive.ubuntu.com dapper-backports/main/debian-installer Packages
Hit http://old-releases.ubuntu.com dapper-security Release
Done http://old-releases.ubuntu.com dapper-security Release
Failed http://archive.ubuntu.com dapper-backports/main/debian-installer Packages
Hit http://old-releases.ubuntu.com dapper/main Packages
Hit http://old-releases.ubuntu.com dapper/restricted Packages
Hit http://old-releases.ubuntu.com dapper/universe Packages
Hit http://old-releases.ubuntu.com dapper/multiverse Packages
Hit http://old-releases.ubuntu.com dapper-updates/main Packages
Hit http://old-releases.ubuntu.com dapper-updates/restricted Packages
Hit http://old-releases.ubuntu.com dapper-updates/universe Packages
Hit http://old-releases.ubuntu.com dapper-updates/multiverse Packages
Hit http://old-releases.ubuntu.com dapper-security/main Packages
Hit http://old-releases.ubuntu.com dapper-security/restricted Packages
Hit http://old-releases.ubuntu.com dapper-security/universe Packages
Hit http://old-releases.ubuntu.com dapper-security/multiverse Packages
Done downloading            
Reading package lists: Done
Building dependency tree: Done
Building dependency tree: Done
Building dependency tree: Done
WARNING: Failed to read mirror file
Ignored http://archive.ubuntu.com dapper-backports Release.gpg
Failed http://archive.ubuntu.com dapper-backports Release.gpg
Done http://old-releases.ubuntu.com dapper Release.gpg
Done http://old-releases.ubuntu.com dapper-updates Release.gpg
Done http://old-releases.ubuntu.com dapper-security Release.gpg
Ignored http://archive.ubuntu.com dapper-backports Release
Failed http://archive.ubuntu.com dapper-backports Release
Done http://old-releases.ubuntu.com dapper-backports Release.gpg
Hit http://old-releases.ubuntu.com dapper Release
Hit http://old-releases.ubuntu.com dapper-updates Release
Ignored http://archive.ubuntu.com dapper-backports/main/debian-installer Packages
Failed http://archive.ubuntu.com dapper-backports/main/debian-installer Packages
Done http://old-releases.ubuntu.com dapper Release
Done http://old-releases.ubuntu.com dapper-updates Release
Hit http://old-releases.ubuntu.com dapper-security Release
Done http://old-releases.ubuntu.com dapper-security Release
Failed http://archive.ubuntu.com dapper-backports/main/debian-installer Packages
Done http://old-releases.ubuntu.com dapper-backports Release
Hit http://old-releases.ubuntu.com dapper/main Packages
Hit http://old-releases.ubuntu.com dapper/restricted Packages
Hit http://old-releases.ubuntu.com dapper/universe Packages
Hit http://old-releases.ubuntu.com dapper/multiverse Packages
Hit http://old-releases.ubuntu.com dapper-updates/main Packages
Hit http://old-releases.ubuntu.com dapper-updates/restricted Packages
Hit http://old-releases.ubuntu.com dapper-updates/universe Packages
Hit http://old-releases.ubuntu.com dapper-updates/multiverse Packages
Done http://old-releases.ubuntu.com dapper-backports Release
Hit http://old-releases.ubuntu.com dapper-security/main Packages
Hit http://old-releases.ubuntu.com dapper-security/restricted Packages
Hit http://old-releases.ubuntu.com dapper-security/universe Packages
Hit http://old-releases.ubuntu.com dapper-security/multiverse Packages
Done http://old-releases.ubuntu.com dapper-backports/main/debian-installer Packages
Done http://old-releases.ubuntu.com dapper-backports/main/debian-installer Packages
Done http://old-releases.ubuntu.com dapper-backports/main/debian-installer Packages
Done http://old-releases.ubuntu.com dapper-backports/main/debian-installer Packages
100% [Working] 
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Resource temporarily unavailable
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Failed http://old-releases.ubuntu.com dapper-backports/main/debian-installer Packages
100% [Working] 
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Resource temporarily unavailable
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Failed http://old-releases.ubuntu.com dapper-backports/main/debian-installer Packages
Done downloading            
Ignored http://archive.ubuntu.com dapper-backports Release.gpg
Failed http://archive.ubuntu.com dapper-backports Release.gpg
Done http://old-releases.ubuntu.com dapper Release.gpg
Done http://old-releases.ubuntu.com dapper-updates Release.gpg
Done http://old-releases.ubuntu.com dapper-security Release.gpg
Done http://old-releases.ubuntu.com dapper-backports Release.gpg
Hit http://old-releases.ubuntu.com dapper Release
Hit http://old-releases.ubuntu.com dapper-updates Release
Ignored http://archive.ubuntu.com dapper-backports Release
Failed http://archive.ubuntu.com dapper-backports Release
Done http://old-releases.ubuntu.com dapper Release
Done http://old-releases.ubuntu.com dapper-updates Release
Hit http://old-releases.ubuntu.com dapper-security Release
Done http://old-releases.ubuntu.com dapper-security Release
Ignored http://archive.ubuntu.com dapper-backports/main/debian-installer Packages
Failed http://archive.ubuntu.com dapper-backports/main/debian-installer Packages
Hit http://old-releases.ubuntu.com dapper-backports Release
Hit http://old-releases.ubuntu.com dapper/main Packages
Hit http://old-releases.ubuntu.com dapper/restricted Packages
Hit http://old-releases.ubuntu.com dapper/universe Packages
Hit http://old-releases.ubuntu.com dapper/multiverse Packages
Hit http://old-releases.ubuntu.com dapper-updates/main Packages
Hit http://old-releases.ubuntu.com dapper-updates/restricted Packages
Done http://old-releases.ubuntu.com dapper-backports Release
Failed http://archive.ubuntu.com dapper-backports/main/debian-installer Packages
Hit http://old-releases.ubuntu.com dapper-updates/universe Packages
Hit http://old-releases.ubuntu.com dapper-updates/multiverse Packages
Hit http://old-releases.ubuntu.com dapper-security/main Packages
Hit http://old-releases.ubuntu.com dapper-security/restricted Packages
Hit http://old-releases.ubuntu.com dapper-security/universe Packages
Hit http://old-releases.ubuntu.com dapper-security/multiverse Packages
Hit http://old-releases.ubuntu.com dapper-backports/main/debian-installer Packages
Hit http://old-releases.ubuntu.com dapper-backports/main/debian-installer Packages
Hit http://old-releases.ubuntu.com dapper-backports/main/debian-installer Packages
Done downloading            
Ignored http://archive.ubuntu.com dapper-backports Release.gpg
Failed http://archive.ubuntu.com dapper-backports Release.gpg
Done http://old-releases.ubuntu.com dapper Release.gpg
Done http://old-releases.ubuntu.com dapper-updates Release.gpg
Done http://old-releases.ubuntu.com dapper-security Release.gpg
Ignored http://archive.ubuntu.com dapper-backports Release
Failed http://archive.ubuntu.com dapper-backports Release
Done http://old-releases.ubuntu.com dapper-backports Release.gpg
Hit http://old-releases.ubuntu.com dapper Release
Ignored http://archive.ubuntu.com dapper-backports/main/debian-installer Packages
Failed http://archive.ubuntu.com dapper-backports/main/debian-installer Packages
Done http://old-releases.ubuntu.com dapper Release
Hit http://old-releases.ubuntu.com dapper-updates Release
Hit http://old-releases.ubuntu.com dapper-security Release
Done http://old-releases.ubuntu.com dapper-updates Release
Done http://old-releases.ubuntu.com dapper-security Release
Failed http://archive.ubuntu.com dapper-backports/main/debian-installer Packages
Hit http://old-releases.ubuntu.com dapper-backports Release
Done http://old-releases.ubuntu.com dapper-backports Release
Hit http://old-releases.ubuntu.com dapper/main Packages
Hit http://old-releases.ubuntu.com dapper/restricted Packages
Hit http://old-releases.ubuntu.com dapper/universe Packages
Hit http://old-releases.ubuntu.com dapper/multiverse Packages
Hit http://old-releases.ubuntu.com dapper-updates/main Packages
Hit http://old-releases.ubuntu.com dapper-updates/restricted Packages
Hit http://old-releases.ubuntu.com dapper-updates/universe Packages
Hit http://old-releases.ubuntu.com dapper-updates/multiverse Packages
Hit http://old-releases.ubuntu.com dapper-security/main Packages
Hit http://old-releases.ubuntu.com dapper-security/restricted Packages
Hit http://old-releases.ubuntu.com dapper-security/universe Packages
Hit http://old-releases.ubuntu.com dapper-security/multiverse Packages
Hit http://old-releases.ubuntu.com dapper-backports/main/debian-installer Packages
Hit http://old-releases.ubuntu.com dapper-backports/main/debian-installer Packages
Hit http://old-releases.ubuntu.com dapper-backports/main/debian-installer Packages
Done downloading            
Reading package lists: Donecom dapper-backports/main/debian-installer Packages: 98  
Building dependency tree: Done
Building dependency tree: Done
Building dependency tree: Done

Getting upgrade prerequisites failed 

The system was unable to get the prerequisites for the upgrade. The 
upgrade will abort now and restore the original system state. 

Please report this as a bug against the 'update-manager' package and 
include the files in /var/log/dist-upgrade/ in the bugreport. 


Restoring original system state

Aborting
Reading package lists: Done
Building dependency tree: Done
Building dependency tree: Done
Building dependency tree: Done
```

I am with root user directly by the way!
Thanks for the help! :)

---

