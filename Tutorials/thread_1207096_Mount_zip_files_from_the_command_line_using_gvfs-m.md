---
title: "Mount zip files from the command line using gvfs-mount"
date: 2009-07-07
forum: Tutorials
---

### Post by wolfgangmeyers on 2009-07-07
I found myself in an annoying situation recently. I know from right-clicking on a zip file within a Nautilus window that I can open it with Archive Mounter. I also know that once I do that, I have mounted the zip file, and it is available on my desktop much like a usb device or windows share. This is probably all well known and well documented somewhere. However, I found myself needing to do this from the command line... not so well documented. 

After some research I found that Archive Mounter uses gvfs to mount zip files. So I thought maybe there was a command line tool called gvfs. Typing gvfs into the command line and hitting tab a couple of times listed these tools (none of which have man pages):

gvfs-cat           gvfs-ls            gvfs-mount         gvfs-rm
gvfs-copy          gvfs-mkdir         gvfs-move          gvfs-save
gvfs-info          gvfs-monitor-dir   gvfs-open          gvfs-trash
gvfs-less          gvfs-monitor-file  gvfs-rename        gvfs-tree

The most interesting to me here was gvfs-mount, which by naming convention seems to mount things. So I tried using it on zip files -- "Location does not implement mount". I tried appending "zip://" to the beginning -- "Location is unmountable". Then I found somewhere that I could use "archive://" to specify zip file location. So I tried -- archive://path-to-zip file (file not found). Still not giving up, tried mounting again using archive mounter, which had some url encoded characters in the address once I had opened the zip file, %3A (:) and %2F (/). I copy-pasted this as an argument to gvfs-mount, and it worked... gvfs-mount will apparently only mount a zip file when you url encode the path! Given the zip file /foo/bar/foo.zip, the corresponding argument to gvfs-mount:

gvfs-mount archive://file%3A%2F%2F%2Ffoo%2Fbar%2Ffoo.zip

which should be equivalent to:

gvfs-mount archive://file:///foo/bar/foo.zip

but the latter does not work, it will give you a file not found error.

In case anyone else out there has a need to mount zip files from scripts, I hope this helps.

NOTE: once you mount the zip file, the mount point will be <home directory of user>/.gvfs/<name of zip file>/ by default.

---

### Post by jpeddicord on 2009-07-11
Nice tip. For what it's worth, I googled around and found [this article]("http://andy.wordpress.com/2008/09/17/urlencode-in-bash-with-perl/") for URI-encoding filenames, which should work with the gvfs suite.

Approved; thank you for your tutorials & tips contribution!

---

### Post by ub123reg on 2009-07-14
$ cat gvfs-mount-archive: 
```
#!/bin/bash

gvfs-mount "archive://file%3a%2f%2f${1//\//%2f}"

```adding to nautilus openers list for .zip files helps too

---

### Post by airtonix on 2009-12-18
Have you found a way to mount them in read/write mode?

---

### Post by colorzone on 2009-12-30
:guitar: WinMount provide command line for mounting zip. 
[COLOR=black][FONT=Verdana]winmount3 -m [file path] [-drv:disk letter or path] [-NoWriteback:] [-attach:][/FONT][/COLOR]
[COLOR=black][FONT=Verdana] 
Introduction:
-drv: mount files to disk or path (Not necessary)
-NoWriteback: read only (Not necessary)
-attach: mount using filter drive. Filter drive meas mounting to an exist path.
[file path] can be quoted with whole path, relative path or default 
 
Examples:
1) mount compressed file
winmount3 -m "E:\test.mou" -drv:Z:\abc
2) mount folder
winmount3 -m "E:\test" -drv:Z:\abc
3) mount muti files or folders (seperate paths with space)
winmount3 -m "E:\test.mou" "E:\test.rar" "E:\test.zip" -drv:Z:\abc
Appropriate for *.mou,*.rar,*.zip or folder
 
[http://www.winmount.com/download.html](http://www.winmount.com/download.html)
 
It also supports windows mode
[/FONT][/COLOR]

---

### Post by djalmaoliveira on 2010-01-07
If you want, try to use fuse-zip at:

[http://code.google.com/p/fuse-zip]("http://code.google.com/p/fuse-zip")

---

### Post by tobeme2 on 2010-04-13
I suggest the proper command might be [COLOR="Lime"]/usr/libexec/gvfsd-archive[/COLOR] .
When you right-click a achive-file (eg. foo.tar.gz) and select "Open With Archive Mounter", 
then you type:
 ```
ps aux | grep -i "foo.tar.gz"
```
and you would get:
```
USER PID %CPU %MEM VSZ RSS TTY STAT START TIME COMMAND
ly 16085 6.0 0.2 21672 4672 ? Sl 01:18 0:07 /usr/libexec/gvfsd-archive file=file:///home/ly/downloads/scrapbook.tar.bz2
```

type: 
```
/usr/libexec/gvfsd-archive -h
```
will get:
```
Usage: /usr/libexec/gvfsd-archive key=value key=value ...
```
You'll find it's not necessary to convert the regular path into url as wolfgangmeyers described, and non-English charicters(eg. Chinese) are just fine(My locale is zh_CN.UTF-8).

It seems like quite awkward to use gvfsd-archive directly, so I write two shell-scripts(archmount,archumount) and linked them into /usr/local/bin/ by:
```
ln -s ~/.myscripts/archmount /usr/local/bin/
ln -s ~/.myscripts/archumount /usr/local/bin/
```
to make it a little easier for use in command-line.

Following are their breif help:

```
archmount is a user-script which makes gvfsd-archive a little easier to use for local archives in command-line.
archive-files are mounted into $HOME/.gvfs/ by gvfsd-archive's default action.
Usage:archmount <file_1> [file_2] [...] [file_n]
Regular expression is supported for the arguments.
Supported file types: iso images;tar (compressed) files;
Examples:
archmount foo/bar/foo.tar.gz foo1/foo2.tar.bz2
archmount foo/bar/f[0-9].tar.bz2
archmount foo/bar/foo.tar.{gz,bz2}
archmount foo/bar/*
archmount /foo/bar/foo.tar.gz
```

```
archumount is used to umount archives(in fact kill a gvfsd-archive process).
Usage:archumount <operation|parterns>
operations:
-h,--help	show this help page
-l,--list	list gvfsd-archive mounted files and their pids
-ka,--kill	kill all gvfsd-archive processes.
parterns:
mounted-files or mount-pionts which are seprated by blank.
mounted-files can be listed by operations -l/--list.
Examples:
archumount -l
archumount foo.tar.gz
foo.tar.gz -ka
```

You can download the scripts here:
[By the way: My scripts don't support blank in file-name or path. I'm just about to learn shell-scripting, so you'd have to modify the scripts you yourself if you want to make them more flexible. Any advises are welcome here!]

---

### Post by tobeme2 on 2010-04-13
PS.
I found it will cause very high CPU usage when mount-point of archive-files, any ideas?

My OS :2.6.33-gentoo
gvfs version: gnome-base/gvfs-1.4.3 (/usr/libexec/gvfsd-archive)

---

### Post by dan000 on 2012-06-16
> **ub123reg said:**
> $ cat gvfs-mount-archive: 
```
#!/bin/bash

gvfs-mount "archive://file%3a%2f%2f${1//\//%2f}"

```adding to nautilus openers list for .zip files helps too

That wouldn't necessarily fix special characters in a filename, and would only work if you give the absolute path.

So here's my take on it:
```

#!/bin/bash

if [ ! -f "$1" ]
then
    echo "$1 is not a valid file" >&2
    exit 1
fi

gvfs-mount "archive://$( ( echo -n 'file://' ; readlink -f "$1" ; ) | perl -MURI::Escape -lne 'print uri_escape($_)')"

```
I also added in a check to make sure you're not giving an invalid filename. Not that it's really necessary, since you'll get another error if you don't, but I think it's nice to have anyway.

And, of course, unmount is simply:
```
gvfs-mount -u ~/.gvfs/{filename}
```

---

