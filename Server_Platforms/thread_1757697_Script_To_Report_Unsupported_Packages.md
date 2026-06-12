---
title: "Script To Report Unsupported Packages?"
date: 2011-05-13
forum: Server Platforms
---

### Post by nutznboltz on 2011-05-13
When Dapper desktop support ended this python script was released:
unsupported-check.py

Here:
[http://people.canonical.com/~ubuntu-security/dapper/](http://people.canonical.com/~ubuntu-security/dapper/)

unsupported-check.py takes a list of supported package names supported.txt as input and reports on any packages which are installed yet not on that list.

Is there anything like this for Hardy now that server support continues after desktop support ends?

---

### Post by nutznboltz on 2011-05-18
You can hack on the python and feed it [hardy-supported.txt ]("http://bazaar.launchpad.net/~ubuntu-security/ubuntu-cve-tracker/master/view/head:/hardy-supported.txt")

But when you do you will find out that Ubuntu 8.04 Universe section catalogs are corrupted by at least one package which has a version number starting with "0~".

The effects of this corruption of the APT catalog are numerous.  For instance:

```
$ apt-cache show webkit
W: Unable to locate package webkit
E: No packages found
```

The version number of the webkit package in Ubuntu 8.04 is 0~svn29752-1.

I think there is logic that decides "0~svn29752-1" == 0
and that version == 0 means there is no package.

The fix should be to bump the webkit package version number to not start with 0~ as well as any others causing this issue.

---

### Post by nutznboltz on 2011-05-18
```
$ lsb_release -d
Description:	Ubuntu 8.04.4 LTS
```

```
$ sudo apt-get install webkit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package webkit
```

However
```

$ apt-get source webkit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Need to get 12.2MB of source archives.
Get:1 http://us.archive.ubuntu.com hardy/universe webkit 0~svn29752-1 (dsc) [869B]
Get:2 http://us.archive.ubuntu.com hardy/universe webkit 0~svn29752-1 (tar) [12.2MB]
Get:3 http://us.archive.ubuntu.com hardy/universe webkit 0~svn29752-1 (diff) [13.7kB]
Fetched 12.2MB in 4s (2737kB/s)
gpg: Signature made Fri 25 Jan 2008 05:48:52 PM EST using DSA key ID 54FD2A58
gpg: Can't check signature: public key not found
dpkg-source: extracting webkit in webkit-0~svn29752
dpkg-source: unpacking webkit_0~svn29752.orig.tar.gz
dpkg-source: applying ./webkit_0~svn29752-1.diff.gz
```

---

### Post by nutznboltz on 2011-05-18
With respect to the original topic of this thread: a script to report unsupported packages, make the following changes to unsupported-check.py

[LIST=1]
[*]Replace the package name list so that it contains the list of supported Hardy packages instead of Dapper ones.
[*]Adjust it to not reject running on Hardy. (see below)
[/LIST]

diff fragment:
```

@@ -810,7 +412,7 @@ def _find_sources_from_apt():
     parts.pop() # _Sources
     parts.pop() # _source
     section = parts.pop() # _main
-    release_real = parts.pop() # _dapper
+    release_real = parts.pop() # _hardy
     saw.setdefault(release_real,True)
     tmp = release_real.split('-')
     release = tmp[0]
@@ -859,9 +461,9 @@ parser.add_option("--main", help="Only include main/restrict
 (opt, args) = parser.parse_args()
 
 try:
-    srcs = load()['dapper']
+    srcs = load()['hardy']
 except:
-    print >>sys.stderr, "This script only works on Dapper."
+    print >>sys.stderr, "This script only works on Hardy."
     sys.exit(1)
 
 bins = []

```

Running the result crashes on the webkit package version number defect.

```
(Pdb) cont
Traceback (most recent call last):
  File "/usr/bin/pdb", line 1213, in main
    pdb._runscript(mainpyfile)
  File "/usr/bin/pdb", line 1138, in _runscript
    self.run(statement, globals=globals_, locals=locals_)
  File "/usr/lib/python2.5/bdb.py", line 366, in run
    exec cmd in globals, locals
  File "<string>", line 1, in <module>
  File "unsupported-check.py", line 488, in <module>
    if bin in srcs[test_src]['binaries']:
KeyError: 'binaries'
Uncaught exception. Entering post mortem debugging
Running 'cont' or 'step' will restart the program
> unsupported-check.py(18)<module>()
-> import os, apt_pkg, sys, subprocess, optparse
(Pdb) p test_src
'webkit'
(Pdb) p srcs[test_src]
{'pocket': 'unset', 'section': 'universe', 'version': '0'}
(Pdb) 
```

---

### Post by nutznboltz on 2011-05-18
The package version of infon-devel is 0~r144-1 so it also starts with 0~ but infon-devel doesn't have the magical characteristics of webkit in that you can "apt-cache policy infon-devel" and unlike webkit there is a package there.

So I put in a hard-coded exception for webkit and adjusted the package version logic to not fail if the package name starts with 0~

Diff fragment
```

diff --git a/unsupported-check.py b/unsupported-check.py
index 50b912f..ebcf656 100755
--- a/unsupported-check.py
+++ b/unsupported-check.py
@@ -438,9 +438,11 @@ def load_collection(item, source_map):
         parser = apt_pkg.ParseTagFile(tags)
         while parser.Step():
             pkg = parser.Section['Package']
-            source_map.setdefault(release,dict()).setdefault(pkg, {'section': 'unset', 'version': '0', 'pocket': 'unset' })
+            if pkg == 'webkit':
+                continue
+            source_map.setdefault(release,dict()).setdefault(pkg, {'section': 'unset', 'version': '~', 'pocket': 'unset' })
             source_map[release][pkg]['section'] = section
-            if apt_pkg.VersionCompare(parser.Section['Version'],source_map[release][pkg]['version'])>0:
+            if apt_pkg.VersionCompare(parser.Section['Version'],source_map[release][pkg]['version'])!='~':
                 source_map[release][pkg]['pocket'] = pocket
                 source_map[release][pkg]['version'] = parser.Section['Version']
                 source_map[release][pkg]['binaries'] = parser.Section['Binary'].split(', ')

```

Still doesn't work but takes longer to crash now.
```

$ ./unsupported-check.py
"Source" missing for linux-headers-2.6.24-26

```

---

### Post by nutznboltz on 2011-05-19
webkit is OK.  The source package simply doesn't match any of the binary package names.  If I take out the exception and just leave the adjustments to the version number checking I get the same results as the previous iteration of unsupported-check.py

---

### Post by nutznboltz on 2011-05-19
Probably works now.  I had to make

```
"Source" missing for linux-headers-2.6.24-26
"Source" missing for linux-headers-2.6.24-16
"Source" missing for linux-headers-2.6.24-16-generic
"Source" missing for linux-headers-2.6.24-26-generic
```

non-fatal errors.  The script was exit(1)ing on that condition before I commented out that exit.

See the attachment for the script.

---

