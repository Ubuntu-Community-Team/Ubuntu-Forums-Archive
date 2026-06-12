---
title: "Odd Experience &quot;Cloning&quot; Filesystem"
date: 2017-01-04
forum: Server Platforms
---

### Post by JSeymour on 2017-01-04
This **may** be a GNU tar question.  TBH: I've never experienced anything like this, before, in some twenty years admin'ing *nix systems.

**Environment:** Ubuntu 14.04.5 LTS on a Dell PowerEdge 2600.  Internal RAID 5 array.  External RAID 5 array on an EonStor box.  Using LVS on both.  Using Samba for the MS-Windows PCs.

Had several filesystems on the internal RAID array filling up.  Decided to move selected filesystems over to the external RAID array, increasing their size, then add the freed-up space on the internal array to others.

Started with this one:

```
$ df -k /account
Filesystem                     1K-blocks     Used Available Use% Mounted on
/dev/mapper/skynet_vg-account   30301132 28820692     11588 100% /account
```

Created a 45GB filesystem on the EonStor array, mounted it on a temporary mount point and and copied everything over:

```
$ cd /account
$ tar Scpf - --acls . |(cd /mnt && tar Sxpf - --acls)
```

Then checked the results:

```
$ df -k /account /mnt
Filesystem                     1K-blocks     Used Available Use% Mounted on
/dev/mapper/skynet_vg-account   30301132 28820692     11588 100% /account
/dev/mapper/eonstor_vg-account  45511712 15415832  27760956  36% /mnt

```
What?!?!  Did tar copy only half the files and directories over?

Using "find," I got a raw count of the number of files and number of directories on each filesystem.  They matched.  "Hmmm..."  Years ago I'd written a quick-and-dirty script to verify the contents of CDs I created.  Put it to work:

```
$ cd /account
$ cd-verify . /mnt

80463 items in .
80463 items in /mnt
80462 items checked
74717 files compared
```

They match.

Next day ran some additional tests.  Long story short: Found reams of stuff like this:

```
$ ls -l '/account/.../somefile.xls' '/mnt/.../somefile.xls'
-rwxrwxr--+ 1 someuser somegrp 24576 May  2  2016 /account/.../somfile.xls
-rwxrwxr--+ 1 someuser somegrp 24576 May  2  2016 /mnt/.../somefile.xls

$ du -k '/account/../somefile.xls' '/mnt/../somefile.xls'
1024    /account/../somefile.xls
24      /mnt/../somefile.xls
```

GNU tar reduced the size of the copied file.  It looks like GNU tar "thought" many of the source files were sparse files and copied them as such?

A binary compare between the two files matches.  A "sum -r" and "md5sum" on each file produces the same results.  I was able to open the copied file, above, with MS Excel, modify it and save it as a new file.  (It saved only slightly larger.)

In addition to .xls files, there are .xlsx', PDFs, zip files, .doc files, etc. that got "weight reductions."  All were originally created/modified by MS-Windows PCs, over Samba connections.

Anybody know what's going on for sure?

---

### Post by TheFu on 2017-01-04
Just a guess ... Lots and lots of fragmentation of the files sucking up many more blocks than really needed?
I would have used **rsync -avzA source target**. ;)

---

### Post by The Cog on 2017-01-04
I agree with TheFu. The only explanation I can think of is excessive fragmentation. 

Note this --apparent-size option in man du:
>        --apparent-size
              print apparent sizes, rather than disk usage; although the apparent size is usually smaller, it may be larger due to holes in ('sparse') files, internal fragmentation, indirect blocks, and the like

Try making a copy of an xls file and then comparing the original wiht its copy on the same disk (free space permitting):
```
cp /account/.../somfile.xls /account/.../somfile-2.xls
du -k /account/.../somfile*.xls
```
I expect the copy will also be much smaller, although existing disk fragmentation may prevent it from being written as one contiguous block.

---

