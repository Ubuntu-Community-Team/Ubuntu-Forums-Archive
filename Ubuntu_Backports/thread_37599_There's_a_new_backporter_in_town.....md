---
title: "There's a new backporter in town...."
date: 2005-05-27
forum: Ubuntu Backports
---

### Post by jdong on 2005-05-27
ubp-build.py!

[http://backports.ubuntuforums.org/ubp/projects/ubp-tools/ubp-build/ubp-build.py](http://backports.ubuntuforums.org/ubp/projects/ubp-tools/ubp-build/ubp-build.py)

This handy little Python script I hacked together reduces backporting to a single command!



For example, I just packaged Nautilus 2.10.1 with the command "ubp-build.py nautilus" :) :)


This should really ease our workload :)

---

### Post by 23meg on 2005-05-27
wow, sounds practical. does it backport from debian unstable?

---

### Post by jdong on 2005-05-27
It backports from whatever it can get through the apt-get source command, which depends on your deb-src lines in sources.list.

---

### Post by McQuaid on 2005-05-27
Great work!

---

### Post by jdong on 2005-05-28
Ok, I fixed two bugs in it this morning.... stupid octal... :D

---

### Post by dlpfmVfH on 2005-05-30
mmm...403..forbidden...

that's a pity I would love to help out...in anyway possible

---

### Post by ShaneAu on 2005-05-30
[QUOTE=aboe]mmm...403..forbidden...

that's a pity I would love to help out...in anyway possible[/QUOTE]
 It's on one of the mirrors:

[ftp://ftp2.caliu.info/backports/projects/ubp-tools/ubp-build/ubp-build.py](ftp://ftp2.caliu.info/backports/projects/ubp-tools/ubp-build/ubp-build.py)

---

### Post by dlpfmVfH on 2005-05-30
found it in the ftp....so how can I help building with this?? :smile:

---

### Post by Mez on 2005-05-30
yeah, looks nea, theres a couple of things I'd like to be able to backport

I assume it's just now finding an apt-get deb-src repos for whatever we want ot backport?

---

### Post by jdong on 2005-05-30
Issue "ubp-build.py" to see the syntax. You can provide it a package name, if it's APT-gettable via deb-src, or give it a URL to a pre-debianized tar.gz, or give it URLs to an orig.tar.gz and a .diff.gz.

---

### Post by Technoviking on 2005-06-03
I just realized I can replaced with a small script :).

Mike

---

### Post by jdong on 2005-06-03
Naw, developers can now shift their focus onto the more important issues: stability and quality.

---

### Post by McQuaid on 2005-07-04
I tried this script for the first time and everything seemed to go ok but had this at the end:

```
dpkg-genchanges: binary-only upload - not including any source code
dpkg-buildpackage: binary only upload (no source included)
Build succeeded!
***Copying to local repository
Backport or Extra [B/e] ?B
Section [m/r/U/v] ?U
Architecture [i/p/a] (I)?i
`kaffeine_0.6-0ubuntu6_i386.deb' -> `/home/mcquaid/ubp/dists/hoary-backports-staging/universe/binary-i386'
/bin/cp: cannot create regular file `/home/mcquaid/ubp/dists/hoary-backports-staging/universe/binary-i386': No such file or directory
Traceback (most recent call last):
  File "/home/mcquaid/ubuntu source script/ubp-build.py", line 267, in ?
    add_to_workingcopy()
  File "/home/mcquaid/ubuntu source script/ubp-build.py", line 240, in add_to_workingcopy
    raise Exception("Error copying to repository...")
Exception: Error copying to repository...
```

The deb was still created and I then manually installed it but I curious as to what went wrong.
Also, when it asked me backport/extra,sect,arch I thought that was already answered by the files in the debian directory.

---

### Post by jdong on 2005-07-04
That step is for committing it to a Backports mirror... So it assumes a certain folder structure.

You can CTRL+C at that point, and just look in ~/ubp-compile-temp for the debs.

---

### Post by Quest-Master on 2005-07-04
Hmm.. keeps on asking for a password and username.. :\

---

### Post by Majlo on 2005-07-04
[QUOTE=Quest-Master]Hmm.. keeps on asking for a password and username.. :\[/QUOTE]

Try this link

[http://backports.ubuntuforums.org/ubp/projects/ubp-tools/ubp-build/ubp-build.py](http://backports.ubuntuforums.org/ubp/projects/ubp-tools/ubp-build/ubp-build.py)
;-)

---

### Post by jdong on 2005-07-05
Thanks. Original link fixed.

---

### Post by monway on 2005-11-05
Hi JDONG, 

I'm Dylan the guy that all the buzz is about for the ppc backport support. I've just recently posted to the list a lil intro about me. I'm happy to say i've tested your script on my ppc machine and doing the ubp-build.py nautilus and see how that goes. So far so good. I'm happy to contribute. Looking forward to more as I go. cheers to all.
-Dylan

---

### Post by monway on 2005-11-05
jdong, 

the script worked fine up to this point
```
***Copying to local repository
Backport or Extra [B/e] ?B
Section [m/r/U/v] ?m
Architecture [i/p/a] (I)?p
/bin/cp: `/home/loki/ubp/dists/hoary-backports-staging/main/binary-powerpc': specified destination directory does not exist
Try `/bin/cp --help' for more information.
Traceback (most recent call last):
  File "/home/loki/Desktop/ubp-build.py", line 272, in ?
    add_to_workingcopy()
  File "/home/loki/Desktop/ubp-build.py", line 245, in add_to_workingcopy
    raise Exception("Error copying to repository...")
Exception: Error copying to repository...

```
Looks like we need a powerpc section for me to contribute. Thanks.
:D

---

### Post by manicka on 2005-11-11
Can't download the script with wget

Connection refused

---

### Post by jdong on 2005-11-11
google for ubp-build -- master mirror down for server migration.

---

### Post by floydwaferfield on 2005-11-23
After the edit changelog part, I get the message that says "I couldn't resolve build dependencies by myself. I'll drop you to a shell". I was just wondering how you go about doing this.

---

### Post by jdong on 2005-11-23
First off, that means the package doesn't qualify for official Backports.

IF you want to work past it, try:

```

dpkg-buildpackage -b -rfakeroot

```

This should spit out a list of dependencies that are not currently met. Use **apt-get install** to install as many of these as you can, and keep on doing the above command to check what's left. When you've gotten as close as you possibly can, press CTRL+D, then ubp-build.py will prompt you to rebuild with no dep check, say YES.

If this step fails, the package cannot be compiled under Breezy.

---

### Post by floydwaferfield on 2005-11-23
I was trying to backport ZSNES using the source tar.gz from one of the ZSNES mirrors. How do I copy the dependencies of v.1.40 in multiverse to this version?

---

### Post by jdong on 2005-11-23
Use **ubp-build.py SOURCE_TAR_GZ_URL NEWEST_UBUNTU_OR_DEBIAN_DIFF.diff.gz** and follow the above procedure when prompted to manually do deps.

---

### Post by strikeforce on 2005-11-24
[QUOTE=jdong]Use **ubp-build.py SOURCE_TAR_GZ_URL NEWEST_UBUNTU_OR_DEBIAN_DIFF.diff.gz** and follow the above procedure when prompted to manually do deps.[/QUOTE]


Can we use the source from the repositories?  E.g. packages.ubuntu.com have links to the orig.tar.gz?  Or will that not work?

Edit

Also when backporting the only change is in the number e.g. ~breezy1
Do you change the name in the changelog or just the number?

---

### Post by jdong on 2005-11-24
(1) If you're gonna use both the orig.tar.gz and diff.gz from an APT repository, you might as well put the appropriate deb-src lines in /etc/apt/sources.list, and just do **ubp-build packagename**.

(2) Only append ~breezy0.1 to the version field; Don't bother changing anything else. Use 0.1 rather than 1 so that future "official backports" would override your work.

---

### Post by akurashy on 2005-11-24
i just noticed this post, i should try using this *goes to read more about it*

---

### Post by akurashy on 2005-11-27
well, i'm really a bit confused, is there gonig to be a wiki on using this? would be great for developer reference :)

---

### Post by jdong on 2005-11-27
You want to write one?

---

### Post by akurashy on 2005-11-27
i think I pass, like i said i'm still a bit confused of the usage.

---

### Post by n6mod on 2005-11-30
[QUOTE=jdong]First off, that means the package doesn't qualify for official Backports.
[/QUOTE]

Can you clarify that? For instance, I just built the Evolution packages using ubp-build.py, but I had to build and install evolution-data-server before evolution itself would build. It seems like any modular package would have this problem.

In any event, the new Evolution packages seem to have fixed the horrible problems with Evolution-Exchange in Breezy.

-Zandr

---

### Post by jdong on 2005-11-30
[QUOTE=n6mod]Can you clarify that? For instance, I just built the Evolution packages using ubp-build.py, but I had to build and install evolution-data-server before evolution itself would build. It seems like any modular package would have this problem.
[/quote]
Ok, that's fine, provided that e-d-s is in accordance of the Backports guidelines (i.e. no libraries, builds fine with ubp-build without the built in hacks)

---

### Post by n6mod on 2005-12-01
[QUOTE=jdong]Ok, that's fine, provided that e-d-s is in accordance of the Backports guidelines (i.e. no libraries, builds fine with ubp-build without the built in hacks)[/QUOTE]

I wasn't watching the output of ubp-build carefully enough, nor with enough wisdom, to percieve any built-in hacks.

That said, there are a couple of outside dependencies on libs built as part of e-d-s. deskbar-applet and nautilus-sendto, in particular. (Not very far outside, but outside)

It's also not quite bombproof (It's 2.5, and upstream doesn't think 2.5 is released)

So I'd say it's not ready for Backports, but I can track Dapper with ubp-build. (which is a marvelous tool, thank you!)

The ubp-built packages work fine for me, which is more than can be said about the version in Breezy.

---

### Post by rko618 on 2006-08-18
I feel like a n00b.  I am trying to run
```
ubp-build.py
``` 
in the directory that I KNOW ubp-build.py is in and I am getting
```
ubp-build.py: command not found

```

what am I doing wrong?

---

### Post by mlind on 2006-08-19
If you're on the same directory as this file is, then try
./ubp-build.py

---

### Post by jamadagni on 2006-09-12
I tried modifying the script to work with pre-downloaded source packages and diffs, but probably owing to my total absence of previous experience with Python, I was not able to get it to work. Please check and tell me what I did wrong.

I changed basically the do_tarball and do_patch functions.

Also, I was not able to understand the purpose of the "-O-" between the wget command and the pipe.

---

### Post by jdong on 2006-09-12
The script should already work with predownloaded source and diffs -- if you provide the two filenames it should understand it.

The -O- and pipe just downloads the tarball and directly extracts it as it streams in, instead of saving the tarball to the hard disk first. Saves some disk space :)

---

### Post by jamadagni on 2006-09-12
> **jdong said:**
> The script should already work with predownloaded source and diffs -- if you provide the two filenames it should understand it.

Nope. Voici -

```
$ ls
kboincspy_0.9.1-3.diff.gz kboincspy_0.9.1.orig.tar.gz ubuntu-backport-builder.py

$ ./ubuntu-backport-builder.py kboincspy_0.9.1.orig.tar.gz kboincspy_0.9.1-3.diff.gz
***Parsing packagename....
Treating arguments as source archive and debianization patch
***Cleaning up working directory...
Cleaning up existing working directory...
***Fetching sourcecode...
--20:10:37--  http://kboincspy_0.9.1.orig.tar.gz/
           => `-'
Resolving kboincspy_0.9.1.orig.tar.gz... failed: Name or service not known.

gzip: stdin: unexpected end of file
tar: Child returned status 1
tar: Error exit delayed from previous errors
Something went wrong unpacking sources. I'll let you do it instead...
Unpack sources into a subdirectory of /home/samjnaa/ubp-compile-temp for me.
```

> The -O- and pipe just downloads the tarball and directly extracts it as it streams in, instead of saving the tarball to the hard disk first. Saves some disk space :)

The -O- is a part of what? Bash syntax? If I do want to save the tarball to the disk first, then how should it be changed?

Thanks.

---

### Post by jdong on 2006-09-12
-O- is an option to wget. Namely, -O means specify output file name, and '-' is standard output. Remove the -O- and wget will revert to its original behavior of saving the file.

---

### Post by jamadagni on 2006-09-13
Fine, but what is the solution to use pre-downloaded files?

---

