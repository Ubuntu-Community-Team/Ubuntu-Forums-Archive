---
title: "MythTV removed from Backports"
date: 2005-06-12
forum: Ubuntu Backports
---

### Post by jdong on 2005-06-12
MythTV 0.18 has been REMOVED from the Backports archive, because no suitable source debs for the plugins could be found.

If you've installed this backport, please roll it back by running:
```

apt-get install mythtv/hoary

```

Please confirm that this rollback procedure works...

---

### Post by scoultas on 2005-06-13
I've been continuing to struggle with this since my last post which was
a request for the plugins to be added.

I raised a bug with Ubuntu about the compilation problems when trying
to build a dependency of the mythmusic packages, though this hasn't 
been looked at yet.

JDong, I asked in a previous thread if it would be possible to build the rest of
the plugins into a package by using 

./configure --disable-mythmusic

Then at least the majority of the modules would become available?
In fact, I believe it might be possible within the mythmusic module to disable
the particular encoding type that is causing the compilation error.

I've been trying to find a way around this without success.  I can't stay with 
version 0.17 because there's a LiveTV bug which crashes my frontend after
watching live tv for a while.  I can't run 0.18 because the plugins don't work.
I installed debian versions of the packages, but these caused Synaptic to declare
the packages 'broken' - the installation was suspect but they appeared to 
work.  However, once 'broken', I couldn't install or upgrade any other packages
through Synaptic.

The only remaining possibility for me is to build all of MythTV from source.
This is a shame, since one of the reasons I moved away from my 3-year old
Mandrake distribution to Ubuntu was to prevent myself from having to build
everything from source due to lack of packages being available.

---

### Post by chaumurky on 2005-06-16
No go for me...

> $ sudo apt-get install mythtv/hoary
Reading package lists... Done
Building dependency tree... Done
Selected version 0.17-3 (Ubuntu:5.04/hoary) for mythtv
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mythtv: Depends: mythtv-database (= 0.17-3) but 0.18-1~5.04ubp1 is to be installed
          Depends: mythtv-frontend (= 0.17-3) but 0.18-1~5.04ubp1 is to be installed
          Depends: mythtv-backend (= 0.17-3) but 0.18-1~5.04ubp1 is to be installed
E: Broken packages


---

### Post by jdong on 2005-06-16
Remove all mythtv packages and reinstall.

---

### Post by chaumurky on 2005-06-16
[QUOTE=jdong]Remove all mythtv packages and reinstall.[/QUOTE]
 That works, thanks. Back to mysql hell again...

---

### Post by wengerp on 2005-07-08
[QUOTE=scoultas]
The only remaining possibility for me is to build all of MythTV from source.
This is a shame, since one of the reasons I moved away from my 3-year old
Mandrake distribution to Ubuntu was to prevent myself from having to build
everything from source due to lack of packages being available.[/QUOTE]

Hi,

Another possibility is to add the following repository to sources.list:
deb [http://dijkstra.csh.rit.edu/~mdz/ubuntu](http://dijkstra.csh.rit.edu/~mdz/ubuntu) hoary mythtv
deb-src [http://dijkstra.csh.rit.edu/~mdz/ubuntu](http://dijkstra.csh.rit.edu/~mdz/ubuntu) hoary mythtv

Most plugins are available. However, Mythmusic seems to be broken (mythmusic doesn't appear in mythtv). Do others have the same problem?

Patrick

---

### Post by dc2447 on 2005-07-09
sorry to bump an old thread but am I right in thinking that there is currently no way of installing mythtv via apt?

Excuse my ignorance but what is the issue here?  Lack of packagers?  Licencing?

---

### Post by wengerp on 2005-07-09
Mythtv version 0.17 is part of the multiverse repository in hoary and breezy and can be installed with apt without problems. This thread is only about version 0.18. 0.18 is available via the above mentioned repository, but only for certain plugins.

Patrick

---

### Post by elgordo123 on 2005-07-11
I am trying to install mythtv-frontend 18 the above repositories  and this is what I get
The following packages have unmet dependencies:
  mythtv-frontend: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
                   Depends: libmyth-0.18.1 but it is not going to be installed
                   Depends: libqt3c102-mt (>= 3:3.3.4) but 3:3.3.3-7ubuntu3 is to be installed

I cannot find the newer version of libc6 anywhere same with libqt3.


Following the tutoral from:
[http://www.cs.rit.edu/~css8044/?q=mythinstall](http://www.cs.rit.edu/~css8044/?q=mythinstall)

Thanks in advance.

---

### Post by wengerp on 2005-07-12
Hi

Are you sure that you are using the right repository? The tutorial that you mention refers to the /debian unstable tree. For ubuntu you have to use the /ubuntu hoary tree (if you use hoary, of course).

Patrick

---

### Post by tnvu on 2005-07-16
[QUOTE=wengerp]Hi,

Another possibility is to add the following repository to sources.list:
deb [http://dijkstra.csh.rit.edu/~mdz/ubuntu](http://dijkstra.csh.rit.edu/~mdz/ubuntu) hoary mythtv
deb-src [http://dijkstra.csh.rit.edu/~mdz/ubuntu](http://dijkstra.csh.rit.edu/~mdz/ubuntu) hoary mythtv
Patrick[/QUOTE]

This should work except mdz needs to run the scan.sh file found in that directory to create the Packages.gz file so its recognized as a repository.

---

### Post by pt123 on 2005-07-17
[QUOTE=elgordo123]I am trying to install mythtv-frontend 18 the above repositories  and this is what I get
The following packages have unmet dependencies:

                   Depends: libqt3c102-mt (>= 3:3.3.4) but 3:3.3.3-7ubuntu3 is to be installed.[/QUOTE]
 A lot of other apps request this version too 3:3.3.3-7

---

