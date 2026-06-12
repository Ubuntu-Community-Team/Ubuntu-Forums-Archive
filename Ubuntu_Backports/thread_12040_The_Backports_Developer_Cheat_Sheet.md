---
title: "The Backports Developer Cheat Sheet"
date: 2005-01-21
forum: Ubuntu Backports
---

### Post by jdong on 2005-01-21
*Not finished yet, but it's coming together*

Purpose:
To provide a quick how-to for making backports, along with a common set of policies and rules governing Ubuntu backports.


[CENTER]**Part 1: The Request**[/CENTER]
A user has requested backports on the forum. Should it be accepted?
**Good Backport Candidate:**
Anything in Universe
Desktop Applications
Compelling reason for backporting

**Bad Candidate**
Servers / daemons in Main -- they would benefit from security updates
Anything introducing new library versions -- other packages have to be recompiled against it, or breakage may occur.
Big, major things, like X11 or GNOME
Kernels/drivers, hardware stuff that may cause additional bugs for some users.

**The Acceptance Process**
If it's determined that the package is fit for backporting, a Developer should "call" the backports, or assign it to another developer. This way, we don't have two developers doing the same work, and valuable time is wasted! A developer from **Each architecture** must respond.


[CENTER]**Part 2: Building the Package**[/center]
Let's walk through GAIM.

You should have a copy of the Subversion repository checked out. If not, secretly do so now! LOL.

```

$ cd ~/backports-arena
$ svn co http://backports.ubuntuforums.org/backports .

```

You should have a development branch's sources in your sources.list:
```

deb-src http://archive.ubuntu.com/ubuntu hoary main universe multiverse restricted

```


Make a temporary directory:
```

$mkdir ~/tmp/gaim-backport
$cd ~/tmp/gaim-backport

```

If the source is in your sources.list (i.e. backporting from Hoary with the deb-src line)
```

$apt-get source gaim
$cd gaim-1.1.1-blah/

```

Else, you need to get the sources yourself:
```

$wget http://archive.ubuntu.com/ubuntu/pool/main/g/gaim/gaim_1.1.1.orig.tar.gz
$tar xzvf gaim_1.1.1.orig.tar.gz
$wget http://archive.ubuntu.com/ubuntu/pool/main/g/gaim/gaim_1.1.1-2ubuntu6.diff.gz
$cd gaim_1.1.1/
$zcat gaim_1.1.1-2ubuntu6.diff.gz | patch -p1

```

Update the version. Open up **debian/changelog** with your favorite editor. In the version field, add the UBP trailer, such as **~4.10ubp1**. Put the target Ubuntu release, then ubp, then the build #. The first revision would be 1, the next bugfix would be 2, etc etc.

In this case, we're gonna use "~4.10ubp1". Why the ~ instead of a dash like with Warty backports? I've been told that "~" is a future less than operator for versions. Unsure whether or not this is in Hoary, but I certainly hope that by the next release, it's gonna be implemented.

Try to satisfy build dependencies. To get a list of what you're missing, run from the source folder:
```

$fakeroot dpkg-buildpackage -rfakeroot
TODO: Sample output

```
If you don't have the proper dependencies, the command will bomb out and list what you need. Use apt-get to install as many as possible.

It's perfectly possible that you might not be able to satisfy some of the versions it's looking for. In this case, install the stable version in Ubuntu.

Once you've gotten as many dependencies as you could, or all of them, run:
```

$fakeroot dpkg-buildpackage -rfakeroot -d

```

This skips the dependency check. If you skipped any dependencies, **remember them** -- you need that info for the backports announcement! Also, make extra sure to test the package in that case!

After this command finishes, go to your temp directory:
```

$cd ..
$ls *.deb

```

You should see one or more .deb's. Congratulations, your packages are built! Now, we'll commit them to the backports tree.

[center]**Part 3: Committing to the backports tree**[/center]
I'm assuming you're in the temp directory containing the .debs. If not, GET THERE! :D

First, copy the debs to the appropriate section in the tree copy you checked out of Subversion:
```

$cp -v *.deb ~/backports-tree/dists/warty-backports-staging/main/binary-i386/

```
Make sure you get the proper distribution (warty-backports-STAGING), the proper section (GAIM is in main), and the proper architecture (I'm building for i386).

Now, you need to tell Subversion that there's new packages, or it'll ignore them.
```

$cd ~/backports-tree/dists/warty-backports-staging/main/binary-i386/
$svn status
?      gaim-data_1.1.1-2ubuntu6-4.10ubp1_all.deb
?      gaim-dev_1.1.1-2ubuntu6-4.10ubp1_i386.deb
?      gaim_1.1.1-2ubuntu6-4.10ubp1_i386.deb

```
Subversion tells you what packages need to be added. Items with a ? mark means that they aren't in the tree, but are in the folder. We need to put these in the repository.
```

$svn add (name of all files to be added)
A   File1
A   File2
...

```

Now, subversion's marked that on the next commit, these packages need to be uploaded.

Next step, we need to update the Packages file. This is an index of all the packages -- apt-get update downloads these files. I have written an automatic script to handle this:

```

$cd ~/backports-tree/
$./update-lists.sh

```

**WARNING: ** Don't be lazy. You must be in the same directory as update-lists.sh for the script to work!!! 
This command may take a while, as it indexes all the packages in the tree. On my system, it takes a whopping 10 seconds to finish  indexing the final Warty backports tree (which has 270 packages) :rolleyes: 

Now, you're ready to commit:
```

$cd ~/backports/tree
$svn commit

```

Subversion will pop up your CLI text editor, where you're prompted to fill in a changelog. First, make sure the changes it lists are correct -- if not, exit and correct them! **ALWAYS Write a changelog entry** -- others need to know what modifications you made to the tree. I may DELETE commits that don't have a changelog entry for security reasons. **ONE package per commit, please**. That way, it's simple to roll back the tree if somehow it gets corrupted!! If multiple debs came from a single source package, that's fine. For this commit, I added the text "GAIM 1.1.1 testing backport".

Save & quit the editor. Subversion will upload your changes. Now, it's time to announce your testing backport to the public. Don't close your commandline yet -- you'll need that last revision info!

FYI, the Subversion versioning system is fully atomic. That means either the whole commit finishes or nothing shows up -- this way, the downloads aren't interrupted while you're uploading -- perfect for what we need!

[CENTER]
**Part 4: Beta tester party**
[/CENTER]
Now, the package is in the staging section of the APT repository. It's time to test. First off, let's write an announcement in this forum. Always follow the following format:

Title: Backport: Gaim 1.1.1-2ubuntu6
```

**Synopsis**
As a tutorial for the Hoary backports system, I created a GAIM backport.

**Backporting Process**
The source archive directly came from Hoary. I was not able to meet the following dependencies, although the package compiled cleanly:

libgnutls11-dev (>= 1.0.16-5) libebook1.2-dev libedata-book1.2-dev libxss-dev libcamel1.2-dev

**Packaging Status:**
i386 -- Staging at revision 2, Stable at revision 4.
amd64 -- Not packaged
ppc -- Not packaged



**Beta tester notes:**
Make sure everything works.


```

There. Now, you have some beta testers on your side.

[CENTER]
**Part 5: Promotion**
[/CENTER]

Promotion refers to the process of packages being marked stable. Remember that packages promoted should be of no less than the superceded package's quality! General rules:

**NO** package may directly enter the stable tree, without being in the staging tree for some time.

Packages should remain in staging for at least **7 days** before being promoted. Exceptions include **security updates**, which may move out of staging as soon as it's verified to work.

**Maintainers** should be the **ONLY** people making promotions. Developers may promote packages only if it's a pressing security fix, or if a maintainer is on vacation...

**The Process**
Promoting is simply moving a package from the -staging area to the corresponding non-staging area. Make sure you use **svn mv**, not just mv. The standard UNIX mv will not instruct the repository to remove the old instance and add the new one.

In keeping to the GAIM example:
```

$cd backports-tree/
$svn mv dists/warty-backports-staging/main/binary-i386/gaim_1.1.1-2ubuntu6-4.10ubp1_i386.deb dists/warty-backports/main/binary-i386/
$svn mv dists/warty-backports-staging/main/binary-i386/gaim-data_1.1.1-2ubuntu6-4.10ubp1_all.deb dists/warty-backports/main/binary-i386/
$svn mv dists/warty-backports-staging/main/binary-i386/gaim-dev_1.1.1-2ubuntu6-4.10ubp1_i386.deb dists/warty-backports/main/binary-i386/
$./update_list.sh
$svn commit

```
**IMPORTANT**: Make sure you run ./update_list.sh -- otherwise, the backport won't show up.

A commit will follow at the end -- fill in the changelog! Promote **one set of packages at a time**. Set is defined the same way as above, in the backporting packages section -- With GAIM, the gaim source package creates the "gaim", "gaim-data", and "gaim-dev" binary packages. Notice how you don't need to re-upload all the data -- Subversion can do REAL moves, as opposed to my old rsync system, which can't!

Then, go back and **edit the backports announcement**, updating the "Packaging Status" field appropriately.
===================================
**Congratulations**, you've completed the tutorial! You should be all trained to handle backports.


[center]**Appendix: Tips and such**[/center]

[list]
[*]Run the **svn update** command on your checked-out copy of the repository regularly. It make sure you have others' changes to the repository, and the latest changelog.
[*]Want to see the changelog? Run **svn log | less**
[*]Install "fakeroot" to get the Fakeroot command, "subversion" to get the svn command.
[*]Conflicts may occur with Packages.gz. I haven't made sure of that yet, but I anticipate it. Please report such issues to me. In the meantime, refer to a Subversion tutorial/handbook for information on resolving conflicts. In our case, if you run "svn update", then ./update_list.sh, you may safely replace the current packages.gz with your copy. Take a look specifically at the "svn resolved" command.
[*]Messed up real badly? Run **svn revert** to undo all changes since last commit. You may even roll back farther than that, but do an **svn update** before continuing, and examine the changelog before blatantly reverting others' changes!
[*]If Subversion gives you timeout errors when committing huge packages, you need to set the global http-timeout value to 0 in ~/.subversion/servers.
[/list]

---

### Post by macewan on 2005-01-22
thanks for taking the time to provide/share this information

---

### Post by jdong on 2005-01-22
Sure thing.

I think I'm almost finished with the guide.

---

### Post by Daniel G. Taylor on 2005-01-22
Very nice!

---

### Post by Quest-Master on 2005-01-22
As soon as I pull up the courage to go unstable, I want to start backporting. :)

---

### Post by Danilo Piazzalunga on 2005-02-11
I've read your guide, it's pretty exaustive! :-) 
If you don't mind, I would like to suggest few tricks to the **Building the package** section.

> **jdong]Update the version. Open up **debian/changelog** with your favorite editor. In the version field, add the UBP trailer, such as **~4.10ubp1**. Put the target Ubuntu release, then ubp, then the build #. The first revision would be 1, the next bugfix would be 2, etc etc.
[/QUOTE]

Alternatively, install the **devscripts** package and use **dch -D *target-release* -i** and change the version manually, or use **-v *target-version***. For example:

```

EDITOR=gedit dch -D warty-ubp -v 1:1.1.1-2ubuntu6~4.10ubp1

```

[QUOTE=jdong]Try to satisfy build dependencies. To get a list of what you're missing, run from the source folder:
```

$fakeroot dpkg-buildpackage -rfakeroot
TODO: Sample output

```
[/QUOTE]

Sample output:

```

dpkg-buildpackage: source package is gaim
dpkg-buildpackage: source version is 1:1.1.1-2ubuntu6~4.10ubp1
dpkg-buildpackage: source maintainer is Tollef Fog Heen <tfheen@canonical.com>
dpkg-buildpackage: host architecture is i386
dpkg-checkbuilddeps: Unmet build dependencies: libgtk2.0-dev libgnutls11-dev (>= 1.0.16-5) tcl8.4-dev tk8.4-dev libao-dev libaudiofile-dev libgtkspell-dev libltdl3-dev libstartup-notification0-dev libzephyr-dev libxml2-dev libebook1.2-dev libedata-book1.2-dev libxss-dev libxext-dev libcamel1.2-dev heimdal-dev
dpkg-buildpackage: Build dependencies/conflicts unsatisfied said:**
> This skips the dependency check. If you skipped any dependencies, **remember them** -- you need that info for the backports announcement! Also, make extra sure to test the package in that case!


It may be a good idea updating the **Build-Depends:** field in **debian/control** to reflect the changes. Anyway, a package should build fine if and only if the build-dependencies are satisfied.

Cheers

---

### Post by jdong on 2005-02-11
Thanks. I'll integrate your input into the cheat sheet.

About the build-depends, IMO lots of the dependencies are unnecessary. Heck a newer package over at Gentoo has less demanding build dependencies than some of the ones Hoary has. Something tells me these are generated automatically, given the packages installed.

---

### Post by Danilo Piazzalunga on 2005-02-12
I'm sorry, but I don't think so. Most build dependencies are simply the development files for the libraries, and IIRC in Gentoo these are installed together with the library package (so you don't see them as separate dependencies).

Besides, only the binary packages' *Depends:* on shared libraries are auto generated, while the build dependencies are written by the package maintainers. If there are any unnecessary build-deps, it is likely due to an error in the source package.

One last thing: there is one tool named **pbuilder** whose purpose is helping to verify the correctness of the build-deps by rebuilding packages in a clean chroot'ed environment. It could also be used for backports, with some effort.

---

### Post by cmsj on 2005-03-01
Hi

[QUOTE=jdong]*Not finished yet, but it's coming together*
```

$cd ~/backports-tree/
$./update-lists.sh

```
[/QUOTE]

Is it safe to be doing this on an amd64 box? I am prepared to build and submit some backport packages to the amd64 tree.

---

### Post by jdong on 2005-03-01
Yes, it's a simple shellscript that calls the dpkg-scanpackages program to regenerate all the Packages.gz files.

If you want to submit some backports, you really don't need to worry about it -- We can do that in-place.

---

### Post by keyshawn on 2005-05-01
> [http://archive.ubuntu.com/ubuntu/pool/main/g/gaim/gaim_1.1.1-2ubuntu6.diff.gz](http://archive.ubuntu.com/ubuntu/pool/main/g/gaim/gaim_1.1.1-2ubuntu6.diff.gz)

Where would I get the 'diff' src at; and how could someone 'create/compile' the 'diff' .tar.gz if it has not been made yet....

I'm trying to run through your steps, but got a bit confused there...

thanks,
skora.

---

### Post by jdong on 2005-05-01
The .diff's can be found at packages.ubuntu.com and packages.debian.org.

Refer to the Debian Maintainer's guide for information on manually debianizing sources for the first time.

---

### Post by crvendramini on 2005-06-04
How to get a copy of subversion repository? I tried, but it asks for username and password..

 ](*,)  ](*,)  ](*,)

---

### Post by jdong on 2005-06-08
NOTE:

This guide is now largely out-of-date and inapplicable, thanks to the new ubp-build.py scripts.

---

