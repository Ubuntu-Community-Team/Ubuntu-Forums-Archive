---
title: "Apache and mod_auth_form"
date: 2013-06-28
forum: Server Platforms
---

### Post by wolfgentleman on 2013-06-28
I just want a simple login form the password protects a directory and its contents. I would use basic auth but it HAS to have a username. I don't want a username, just a password. So when I found mod_auth_form on httpd.apache.org I went to try it and I kept getting module doesn't exist. When I looked it up I found that it doesn't appear until 2.3, so I tried looking for a ppa with apache 2.3, couldn't find anything, tried building the source and moving the built binaries into the installed folder that mucked it up so bad I had to reinstall apache, php, and all the little libs that go with them. What can I do to get this working?

---

### Post by wolfgentleman on 2013-06-29
bump

---

### Post by wolfgentleman on 2013-07-01
bump

---

### Post by sandyd on 2013-07-01
Give me a few hours or so, and I will generate a package for you (backport from debian unstable)

The below are very general instructions

Prereq Instructions:
1. Sign up for Launchpad Account ([http://launchpad.net](http://launchpad.net))
2. Generate a OpenGPG key and import it into Launchpad.
3. After youve done that, go to Personal package archives, and create a new PPA.
4. Now your ready to start backporting packages from debian

Backporting instructions: [Note: this is done on the computer where your Gpg key is!!]
1. Create and navigate to a empty folder where the backporting will take place
2. Download apache's source package from packages.debian.org. (Found at [http://packages.debian.org/sid/apache2](http://packages.debian.org/sid/apache2))
```
wget http://ftp.de.debian.org/debian/pool/main/a/apache2/apache2_2.4.4.orig.tar.bz2
wget http://ftp.de.debian.org/debian/pool/main/a/apache2/apache2_2.4.4-6.debian.tar.gz
```
Note the above URLs are just the current ones, I am sure new urls will be avaliable in the future, so check the link above

3. 
```

tar xvf apache2_2.4.4.orig.tar.bz2
tar xvf apache2_2.4.4-6.debian.tar.gz -C  httpd-2.4.4
```

4.
```

cd httpd-2.4.4/debian
nano changelog

```

5.
Edit the below (replacing Celene Barjaval with the Name you used in the gpg key, and [email]sandy@nowhere.com[/email] with the email you used in the gpg key, replace raring with your distribution, and the date as the date)
```

apache2 (2.4.4-6ubuntu0~raring) raring; urgency=high
  * Backport to Ubuntu

 -- Celene Barjaval <sandyd@nowhere.com>  Mon, 1 July 2013 17:54:40 -0800
```

6.
Paste it exactly as is at the top of the changelog file so it looks like
```

apache2 (2.4.4-6ubuntu0~raring) raring; urgency=high
  * Backport to Ubuntu

 -- Celene Barjaval <sandyd@nowhere.com>  Mon, 1 July 2013 17:54:40 -0800

apache2 (2.4.4-6) unstable; urgency=low

  * Denote exact versions breaking gnome-user-share now that Gnome maintainers
    have a fixed version in the works. That makes Gnome installable again.
  * Update our gbp.conf for our big merge next -> master. The eagle has
    landed, 2.4 is here.
  * Push Standards version to 3.9.4 - no changes needed.
  * Fix spelling errors in man pages.
  * Update the git VCS pointer to its canonical location for anonymous

```

7. Now press control+x to save file
```

cd ../
debuild -S -sa
``` (install debuild if you havent)

8.
```

cd ../
ls *.sources.changes

```
That should list one file, refered to as <sources.changes>

9. Repeat the above processes for libaprutil1, changing the things so that it matches libaprutil1

10. Go to your ppa, it should have something like
```
You can upload packages to this PPA using:

dput ppa:sandyd/apache2-backports <source.changes>
```
on the front.

take the dput line, and replace <sources.changes> with the info in step 8.
Upload libaprutil1 first, because apache2 depends on it

That said, theirs a PPA here (which isn't finished compiling) [https://launchpad.net/~sandyd/+archive/apache2-backports](https://launchpad.net/~sandyd/+archive/apache2-backports)
However, I don't have enough time to keep it updated, which is what the above is for.

---

### Post by wolfgentleman on 2013-07-02
Thank you, and I finally have a use for my launchpad account! I started that account not realizing it was source packages only...

EDIT: The dependencies don't have source packages and apt is bucking because it doesn't have the right versions of apache2-bin,apache2-data,apache2.2-common
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 apache2 : Depends: apache2-bin (= 2.4.4-6ubuntu1~precise) but it is not going to be installed
           Depends: apache2-data (= 2.4.4-6ubuntu1~precise) but it is not going to be installed
           Conflicts: apache2.2-common but 2.2.22-1ubuntu1.3 is to be installed
E: Unable to correct problems, you have held broken packages.
```

UPDATE:
Just tried downloading the binary deb files and adding them to my repo (not launchpad) then doing an upgrade and that mucked it up so bad I had to *purge* the AMP part of my LAMP server then reinstall.

---

### Post by wolfgentleman on 2013-07-06
bump

---

### Post by sandyd on 2013-07-06
> **wolfgentleman said:**
> Thank you, and I finally have a use for my launchpad account! I started that account not realizing it was source packages only...

EDIT: The dependencies don't have source packages and apt is bucking because it doesn't have the right versions of apache2-bin,apache2-data,apache2.2-common
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 apache2 : Depends: apache2-bin (= 2.4.4-6ubuntu1~precise) but it is not going to be installed
           Depends: apache2-data (= 2.4.4-6ubuntu1~precise) but it is not going to be installed
           Conflicts: apache2.2-common but 2.2.22-1ubuntu1.3 is to be installed
E: Unable to correct problems, you have held broken packages.
```

UPDATE:
Just tried downloading the binary deb files and adding them to my repo (not launchpad) then doing an upgrade and that mucked it up so bad I had to *purge* the AMP part of my LAMP server then reinstall.
Do you have a link to your LP PPA?

---

### Post by wolfgentleman on 2013-07-08
> **sandyd said:**
> Do you have a link to your LP PPA?

I used your PPA to test it but it bucked about the dependencies, so I deleted the PPA I created and downloaded the binary debs from the debian sid repo and added them to my repo. When I went to install it said it was held back so I used apt-get install instead of upgrade... I don't remember what the error was but when that apt error was resolved and I installed it............ I had to purge the AMP in LAMP server from it mucking it up so bad...

---

### Post by sandyd on 2013-07-09
did you just add the ppa (i.e. like 
```

sudo add-apt-repository ppa:sandyd/apache2-backports
```
if it doesn't work, you need to backport the missing packages (that are causing the dependency problems) from Debian as well. Ive only included the bare minimum needed to actually run apache

---

### Post by wolfgentleman on 2013-07-15
> **sandyd said:**
> did you just add the ppa (i.e. like 
```

sudo add-apt-repository ppa:sandyd/apache2-backports
```
if it doesn't work, you need to backport the missing packages (that are causing the dependency problems) from Debian as well. Ive only included the bare minimum needed to actually run apache

The dependencies don't have source packages. I tried downloading the binary packages and uploading them to my repository, not the ppa. When I added my repo and updated the list and ran apt-get upgrade it said it was held back. So I used aptitude to upgrade it manually and after the install it was so screwed up that I had to purge apache, php, and mysql then reinstall.

I found a different solution for what I originally wanted it for, but I would still like to have the feature available to me.

---

### Post by sandyd on 2013-07-15
which dependencies?

---

