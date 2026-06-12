---
title: "VirtualBox 4.1"
date: 2011-09-09
forum: Virtualisation
---

### Post by dmubu on 2011-09-09
Hello,

I am trying to install VirtualBox 4.1 on my machine. I currently have version 4.0.

I ran:

```
 sudo apt-get update sudo apt-get install virtualbox-4.1  
```and received:

```

Package virtualbox-4.1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'virtualbox-4.1' has no installation candidate

```Any ideas?

Thank you

---

### Post by haqking on 2011-09-09
> **dmubu said:**
> Hello,

I am trying to install VirtualBox 4.1 on my machine. I currently have version 4.0.

I ran:

```
 sudo apt-get update sudo apt-get install virtualbox-4.1  
```and received:

```

Package virtualbox-4.1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'virtualbox-4.1' has no installation candidate

```Any ideas?

Thank you

it is 4.1.2 i think

and easier to download the .deb from here [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

then just double click the .deb if you are having issues.

Also add the extensions pack also

cheers

---

### Post by dmubu on 2011-09-09
Thanks for the reply!

That worked!

---

### Post by haqking on 2011-09-10
> **dmubu said:**
> Thanks for the reply!

That worked!

no problem, you are very welcome

---

### Post by CharlesA on 2011-09-10
You can also add the repo to sources.list and install with apt-get, I do it that way so I don't have to worry about manual upgrades. :)

The instructions for that are listed on the [Linux Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads") page.

---

### Post by haqking on 2011-09-10
> **CharlesA said:**
> You can also add the repo to sources.list and install with apt-get, I do it that way so I don't have to worry about manual upgrades. :)

The instructions for that are listed on the [Linux Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads") page.


For some reason i had issues with their repo, i commented it out in the end, it would never install over an existing version i would always have to remove the previous.

I know this happens anyways with a major version change, but with .debs i download it doesnt happen on the incremental changes.

any thoughts ?

---

### Post by CharlesA on 2011-09-10
> **haqking said:**
> For some reason i had issues with their repo, i commented it out in the end, it would never install over an existing version i would always have to remove the previous.

I know this happens anyways with a major version change, but with .debs i download it doesnt happen on the incremental changes.

any thoughts ?

I don't know what could be causing that unless you were bumping from 4.0 to 4.1 or 3.2 to 4.0 (or the like). I don't recall running into anything like that (yet at least). I think it happens on the major version changes since they are incompatible with each other.

---

### Post by haqking on 2011-09-10
> **CharlesA said:**
> I don't know what could be causing that unless you were bumping from 4.0 to 4.1 or 3.2 to 4.0 (or the like). I don't recall running into anything like that (yet at least). I think it happens on the major version changes since they are incompatible with each other.


mmm well no biggie.

I use VB everyday and it tells me if there is an update anyways so all good.

cheers

---

### Post by CharlesA on 2011-09-10
> **haqking said:**
> mmm well no biggie.

I use VB everyday and it tells me if there is an update anyways so all good.

cheers

I run it headless so the only way I know if there is an update is when I run apt-get or check the website. :p

---

### Post by Matt26 on 2012-02-15
> **haqking said:**
> it is 4.1.2 i think

and easier to download the .deb from here [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

then just double click the .deb if you are having issues.

Also add the extensions pack also

cheers

i ran into this same error trying to install the latest version of virtualbox on ubuntu 11.10.. this is the error i get:

> Package operation failed

The installation or removal of a software package failed.

Selecting previously deselected package virtualbox-4.1.
dpkg: considering removing virtualbox in favour of virtualbox-4.1 ...
dpkg: yes, will remove virtualbox in favour of virtualbox-4.1.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 153851 files and directories currently installed.)
Unpacking virtualbox-4.1 (from .../virtualbox-4.1_4.1.8-75467~Ubuntu~oneiric_i386.deb) ...
 * Stopping VirtualBox kernel modules
   ...done.
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: data error'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /home/matthew/Downloads/virtualbox-4.1_4.1.8-75467~Ubuntu~oneiric_i386.deb (--install):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for shared-mime-info ...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-central ...
Errors were encountered while processing:

any ideas?

---

### Post by haqking on 2012-02-16
> **Matt26 said:**
> i ran into this same error trying to install the latest version of virtualbox on ubuntu 11.10.. this is the error i get:



any ideas?

remove previous version first

---

### Post by Matt26 on 2012-02-16
> **haqking said:**
> remove previous version first

virtualbox didn't install, so there shouldn't be a previous version installed- this is a fresh install of Ubuntu and virtualbox is the first program that i've tried to install.

i have made a few attempts at installing virtualbox with no success before trying the .deb package from the virtualbox website- is it possible that there are traces of those failed installation attempts remaining?  if so, how do i remove them?

---

### Post by haqking on 2012-02-16
> **Matt26 said:**
> virtualbox didn't install, so there shouldn't be a previous version installed- this is a fresh install of Ubuntu and virtualbox is the first program that i've tried to install.

i have made a few attempts at installing virtualbox with no success before trying the .deb package from the virtualbox website- is it possible that there are traces of those failed installation attempts remaining?  if so, how do i remove them?

oh ok.

go to synaptic and make sure all vbox elements are gone.

Then retry from the deb.

also i take it you are running x86 and not x64

---

### Post by Matt26 on 2012-02-19
> **haqking said:**
> oh ok.

go to synaptic and make sure all vbos elements are gone.

Then retry from the deb.

also i take it you are running x86 and not x64

yes, running x86.

i've installed synaptic and searched for 'vbos' which returns a couple of results- glmark2 and glmark-es2- neither are installed.. are these the vbos elements you're referring to?

i also noticed via the ubuntu software center that 'x86 virtualization solution- base binaries' was installed, so i removed that as well, but still the .deb package fails to install.

any ideas?

thanks!

---

### Post by haqking on 2012-02-19
> **Matt26 said:**
> yes, running x86.

i've installed synaptic and searched for 'vbos' which returns a couple of results- glmark2 and glmark-es2- neither are installed.. are these the vbos elements you're referring to?

i also noticed via the ubuntu software center that 'x86 virtualization solution- base binaries' was installed, so i removed that as well, but still the .deb package fails to install.

any ideas?

thanks!

sorry it was a typo i meant vbox meaning reinstall virtual box

---

### Post by Matt26 on 2012-02-20
> **haqking said:**
> sorry it was a typo i meant vbox meaning reinstall virtual box

ok, i tried searching for 'virtualbox' in synaptic and none of the items listed were installed.

what else can i do?  should i try installing the version listed in synaptic (4.1.2) and then upgrade to the current version?

i got this error when i tried to reload the package information in synaptic..

> Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/oneiric/Release](http://download.virtualbox.org/virtualbox/debian/dists/oneiric/Release)  Unable to find expected entry 'contrib/source/Sources' in Release file (Wrong sources.list entry or malformed file)
Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by Matt26 on 2012-02-22
i tried installing again from the terminal window using the commands outlines at [https://www.virtualbox.org/wiki/Linux_Downloads]("https://www.virtualbox.org/wiki/Linux_Downloads") under the Debian-based Linux distributions section.

i've also tried installing from synaptic, which only shows version 4.1.2 and no success- an error occurs when i try to reload the package information (see previous post for error).

can anyone help me, please?

---

### Post by CharlesA on 2012-02-22
What is the entry in /etc/apt/sources.list?

---

### Post by AnrDaemon on 2012-02-24
You MUST NOT at any point edit sources.list by yourself.
If you want to add new repositories - there's a /etc/apt/sources.list.d directory, where you can put files mentioning them.

---

### Post by CharlesA on 2012-02-24
> **AnrDaemon said:**
> You MUST NOT at any point edit sources.list by yourself.
If you want to add new repositories - there's a /etc/apt/sources.list.d directory, where you can put files mentioning them.
You can edit it manually, but it's easier to just use software sources to add entries.

---

### Post by AnrDaemon on 2012-02-24
> **CharlesA said:**
> You can edit it manually,

Do NOT do it. Don't think about it. Leave it alone. And your system will be safer from your meddling.

---

### Post by CharlesA on 2012-02-24
> **AnrDaemon said:**
> Do NOT do it. Don't think about it. Leave it alone. And your system will be safer from your meddling.
I guess we can just agree to disagree then.

You *can* edit it manually, but it is safer/easier to do it from the GUI.

---

### Post by AnrDaemon on 2012-02-24
I said it earlier, you must not EDIT sources.list.
You have to create additional lists in the /etc/apt/sources.list.d/ directory, which is considered an extension to the /etc/apt/sources.list with such a benefit, that you don't have a chance to royally screw up your whole update system.
I've had a couple of such cases with people toying with main sources.list and then screaming around the forum for clean copy of it.
It's much safer and easier to teach people proper methods straight out, than to tell them "you can do it", and then helping them to recover from doing it afterward...

---

### Post by haqking on 2012-02-25
> **AnrDaemon said:**
> I said it earlier, you must not EDIT sources.list.
You have to create additional lists in the /etc/apt/sources.list.d/ directory, which is considered an extension to the /etc/apt/sources.list with such a benefit, that you don't have a chance to royally screw up your whole update system.
I've had a couple of such cases with people toying with main sources.list and then screaming around the forum for clean copy of it.
It's much safer and easier to teach people proper methods straight out, than to tell them "you can do it", and then helping them to recover from doing it afterward...


personal preference i guess. The "NOT and SHOULDNT" are a bit strong though, sources.list has always been the way to add or edit repos in a debian based distro, the .d is relatively new, so telling someone you shoudlnt is  bad advice, telling them they can also drop a file into the sources.list.d directory is better.

either way there should be a backup of your system files before editing.

And if you dont know what you are doing shouldnt be editing system files anyways ;-)

---

