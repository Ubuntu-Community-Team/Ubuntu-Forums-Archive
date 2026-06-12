---
title: "Why can't you decided where programs go?"
date: 2016-12-15
forum: Ubuntu, Linux and OS Chat
---

### Post by mintmag on 2016-12-15
When installing programs either from a the repository or from a local .deb file it doesn't let you chose which directory you want it installed. I'm curious is there a reason for this. What if the main drive gets full and you want to install programs to another drive.

---

### Post by CharlesA on 2016-12-15
Because there is a specific structure to the file system? See [here]("http://www.thegeekstuff.com/2010/09/linux-file-system-structure/").

If you want to pick where you install your applications, you might look into compiling things from source.

---

### Post by mintmag on 2016-12-15
Right, but why force it. Windows has directories like that too.

---

### Post by lisati on 2016-12-16
The short answer is that Linux does some things a bit differently to Windows, or, if you prefer, "Linux is not Windows."

A generalization you might encounter from time to time is "On a LINIX system, everything is a file; if something is not a file, it is a process." For an elaboration, you might want to read [this]("http://www.tldp.org/LDP/intro-linux/html/sect_03_01.html") article.

---

### Post by QIII on 2016-12-16
Since it is all open source, you are free to download any source you choose, alter it as you wish, change it to allow you to install wherever you want, compile it and go on your happy way.

If you want to install things willy nilly, nothing is holding you back.

---

### Post by mintmag on 2016-12-16
> **lisati said:**
> The short answer is that Linux does some things a bit differently to Windows, or, if you prefer, "Linux is not Windows."

A generalization you might encounter from time to time is "On a LINIX system, everything is a file; if something is not a file, it is a process." For an elaboration, you might want to read [this]("http://www.tldp.org/LDP/intro-linux/html/sect_03_01.html") article.

Thanks I will give that a read. What I would like though is a more layman's answer. Is it to do with the way it indexes or whatever it has in-place of a registry?

---

### Post by lisati on 2016-12-16
There is no direct equivalent to the Windows registry that I'm aware of. The Windows registry serves a number of purposes, including the saving of configuration information and system information. In Linux, /etc is commonly used to store configuration information, and /var is used for information about the state of the system. Extreme care is needed when editing the contents of both, as it is very easy to make changes that break your system.

---

### Post by TheFu on 2016-12-16
Some more ideas on this topic: [https://serverfault.com/questions/23734/is-there-any-way-to-get-apt-to-install-packages-to-my-home-directory](https://serverfault.com/questions/23734/is-there-any-way-to-get-apt-to-install-packages-to-my-home-directory)

The "main drive is full" really isn't an issue.  Unix has symbolic links which can redirect from /usr --> /some/other/hdd/directory/ if it becomes necessary. I've used this back when HDDs were 1G in total size.  With larger disks these days, it really is hard to use more than 30G with applications and settings, which is a tiny disk (when compared to OTHER, popular, OSes) for today.  It is the data that goes elsewhere and is usually trivial to control that other location.  My daily use desktop is 
```
Filesystem       Size  Used Avail Use% Mounted on
/dev/vda1         17G   13G  2.6G  84% /

``` which included /home/ too. Hardly a bloated install.  This install has been moved forward from 8.04 days - so 8 yrs old.  I'm careful to keep "data" on network drives (NFS).  

Actually, much of the OS can be on NFS drives too. Don't see this very often anymore, but in the old days, when storage was expensive and smaller, we routinely shared /usr across all the systems on a network running the same architecture.  Looking up the "Linux [File System Hierarchy]("http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/")" will give the full details of which directories can be remote, which can be read-only and which must be local.

Regardless, symlinks are a powerful tool, when necessary.

---

### Post by mintmag on 2016-12-16
> **TheFu said:**
> Some more ideas on this topic: [https://serverfault.com/questions/23734/is-there-any-way-to-get-apt-to-install-packages-to-my-home-directory](https://serverfault.com/questions/23734/is-there-any-way-to-get-apt-to-install-packages-to-my-home-directory)

The "main drive is full" really isn't an issue.  Unix has symbolic links which can redirect from /usr --> /some/other/hdd/directory/ if it becomes necessary. I've used this back when HDDs were 1G in total size.  With larger disks these days, it really is hard to use more than 30G with applications and settings, which is a tiny disk (when compared to OTHER, popular, OSes) for today.  It is the data that goes elsewhere and is usually trivial to control that other location.  My daily use desktop is 
```
Filesystem       Size  Used Avail Use% Mounted on
/dev/vda1         17G   13G  2.6G  84% /

``` which included /home/ too. Hardly a bloated install.  This install has been moved forward from 8.04 days - so 8 yrs old.  I'm careful to keep "data" on network drives (NFS).  

Actually, much of the OS can be on NFS drives too. Don't see this very often anymore, but in the old days, when storage was expensive and smaller, we routinely shared /usr across all the systems on a network running the same architecture.  Looking up the "Linux [File System Hierarchy]("http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/")" will give the full details of which directories can be remote, which can be read-only and which must be local.

Regardless, symlinks are a powerful tool, when necessary.

Oh so you can use symlinks. I'm still not entirely sure what they are. I know that's what gets created when I try to make a shortcut. Can you tell me why Ubuntu uses symlinks instead of shortcuts. A typical shortcut would look something like ```
xdg-open /location/to/program
```

---

### Post by ian-weisser on 2016-12-16
> **mintmag said:**
> Right, but why force it. Windows has directories like that too.
It's only forced if you insist on using Package Management.
Packages tell the installer (dpkg) where they should be installed.

You are, of course, free to edit the package to install wherever you like.
Warning: That's quite advanced, and can easily break your whole system if you edit the wrong package.

It's generally easier to not use the packages if you want that level of customization.
Instead, install using the (edited) makefile. A much older and more brittle, but much more configurable installation method.
Warning: Using the makefile method of installation adds some (human) admin responsibilities, since you are giving up the advantages of packages.
Warning: Using makefiles is an intermediate-level skill. It must be practiced and learned.


One of the ancient features of the Debian/Ubuntu is space savings through the use of shared files, sometimes including whole subsidiary applications, (not just dll-type binaries.
Shared files are assumed to be in a standard location, and consuming applications --including system applications-- may not verify that.
So if you move one of those shared files by editing it's package, be sure you place a symlink (shortcut) to the new location so using applications can find it.

---

### Post by TheFu on 2016-12-16
> **mintmag said:**
> Oh so you can use symlinks. I'm still not entirely sure what they are. I know that's what gets created when I try to make a shortcut. Can you tell me why Ubuntu uses symlinks instead of shortcuts. A typical shortcut would look something like ```
xdg-open /location/to/program
```

I have no idea what a *shortcut* is. Never heard of them outside Windows.  Symbolic Links are part of Unix-like file systems and have been there 30+ years.  I'm not much of a GUI user, so don't know about xdg-open either. Never needed it.

While you are looking up (via google) **symlinks**, check out **hardlinks** too. Wikipedia is a good place to start.

---

### Post by mintmag on 2016-12-17
> **TheFu said:**
> I have no idea what a *shortcut* is. Never heard of them outside Windows.  Symbolic Links are part of Unix-like file systems and have been there 30+ years.  I'm not much of a GUI user, so don't know about xdg-open either. Never needed it.

While you are looking up (via google) **symlinks**, check out **hardlinks** too. Wikipedia is a good place to start.

Right well Linux can have shortcuts too that work exactly the same. symlinks aren't the same as shortcuts because they don't' retain the root address but a shortcut does. Example of a shortcut to my documents for Linux. 

```

[Desktop Entry]
Comment=
Terminal=false
Name=Shortcut to documents
Exec=xdg-open /home/mintmag/Documents
Type=Application

```

Save that to a .desktop file

---

### Post by mintmag on 2016-12-17
So are these shard files used to save space and make things more efficient.

---

### Post by The Cog on 2016-12-17
The "shortcut" that you posted is what I would call an application launcher. It specifically launches an application to deal with a file. In your example, the file is actually a directory, so I guess that it would normally open a file manager application like nautilus to show the contents of the Documents folder. As far as I know, these launchers, desktop files, are restricted in use to launching GUI applications. Their prime reason for existence is to put a pretty icon on the desktop to allow launching an application with a mouse click.

A symlink is much less specific. It is a kind of redirect from one file location to another. It works for any kind of file for any kind of reason, not just for the purpose of launching applications. It can redirect access to application executables, library files, data files, configuration files, directories, even devices. 

My desktop has a CD/DVD reader/writer drive, so it has several device names, the actual driver being sr0:
```
$ ls -ld /dev/*  | grep sr0
lrwxrwxrwx  1 root root           3 Dec 17 09:53 /dev/cdrom -> sr0
lrwxrwxrwx  1 root root           3 Dec 17 09:53 /dev/cdrw -> sr0
lrwxrwxrwx  1 root root           3 Dec 17 09:53 /dev/dvd -> sr0
lrwxrwxrwx  1 root root           3 Dec 17 09:53 /dev/dvdrw -> sr0
brw-rw----+ 1 root cdrom    11,   0 Dec 17 09:53 /dev/sr0
```

One common use is to divert a well known filename to a particular version, e.g. the operating system itself, has symlinks in the root directory that redirects the bootloader to specific versions in a subdirectory:
```
$ ls -l / | grep ^l
lrwxrwxrwx   1 root root    32 Dec 12 10:18 initrd.img -> boot/initrd.img-4.8.0-30-generic
lrwxrwxrwx   1 root root    32 Nov 30 19:31 initrd.img.old -> boot/initrd.img-4.8.0-28-generic
lrwxrwxrwx   1 root root    29 Dec 12 10:18 vmlinuz -> boot/vmlinuz-4.8.0-30-generic
lrwxrwxrwx   1 root root    29 Nov 30 19:31 vmlinuz.old -> boot/vmlinuz-4.8.0-28-generic
```

I notice that /bin/ping4 and /bin/ping6 both symlink to /bin/ping for instance - the one ping executable knows how to handle both protocols, and I think it changes its behaviour depending on which command it was started with.

Another use might be (as suggested) to divert to directories that are not where you might normally expect to find them, e.g:
```
$ ls -ld /var/*  | grep ^l
lrwxrwxrwx  1 root root        9 Nov 26 16:59 /var/lock -> /run/lock
lrwxrwxrwx  1 root root        4 Nov 26 16:59 /var/run -> /run

```

Symlinks can indeed "retain the root address", if you choose to start them with a "/" character. If you don't, they are relative to the location they are redirecting from. Since symlinks are just text, they can also refer to non-existent locations (known as broken symlinks).

So the use case for symlinks is much wider than just launching applications from an icon. It is quite fundamental to that way things are structured. 

I read that Windows has recently acquired the ability to have symlinks, though I don't think I have seen them actually being used.

---

### Post by ian-weisser on 2016-12-17
Sometimes shared files in standard locations (libs, like dlls) are used to save space and make the system more efficient.

As a byproduct, they also encourage (but do not require) uniform behavior and version control, since only one lib can be in the expected location.

Another example of standard locations is hook directories or include directories that can be used by scripts of programs to change behavior or settings of another (/etc/cron.d,  /etc/apt/sources.list.d, /etc/kernel/postrm.d, /etc/ifup.d, /var/lock, and many more).

Another example of standard location are 'group applications'. These are groups of small independent or semi-dependent applications that users mistake for a single application, sometimes with widely different upstreams. The Package Manager itself is one of these (dpkg, apt, aptdaemon, packagekit, unattended-upgrade, update-notifier, update-manager). Imagemagick is another.

---

### Post by TheFu on 2016-12-17
.desktop files are for a specific use. Not what you need here. You need a "symbolic link."  Also called symlink, softlink. These are file system objects.  Wikipedia describes them.  They always work; desktops, servers, raspberry pis, anything using a Unix-like file system. Support is built-into the file system, not some GUI tool (like in Windows).  I suspect my thermostatic supports symlinks, since it is running Linux.

NTFS added both hard and soft linking about 6 years ago. It hasn't caught on because people from that type of computing didn't need it.  When "Libraries" came out on Windows Vista, I was really excited. Finally, they'd included symlinks.  Turns out they didn't.  Libraries only work with GUI tools, which was worthless to me.  I wanted the file system symbolic linking, to merge locations without risking data like LVM does or RAID0 does.  

Symlinks rock.  Think of it like a cheque.  I don't have any money, but if you talk to these guys at this bank, they will pay you.  The wikipedia article has simple diagrams which explain it better.  Just know that any program using the file system will see the symlink and follow it where ever it goes.  A tiny few programs pay attention to symlinks, but most just follow them and do "the expected thing." Which is good. Over the last 30+ years, I can think of 2 programs that didn't work due to symlinks. Every other program worked fine.

I don't think symlinks are just text files. They are file system objects that point to another file system object.  Basically an inode-to-inode redirection with a name.  The inodes still have parents. In the old days, if we used a shell program to follow a symlink to another directory, when we went back up through the parent of the parent of the parent, it wouldn't follow the reverse path correctly and we'd be in the original directory path.  Bash does what we expect these days. Hiding the symlink traversal. 

Did I mention that symlinks rock? They do.

He just wants a way to free up some storage on /usr/.  I suggested he move all of /usr/ to another disk and create a symlink from /usr/ ---> /some/new/disk/usr/ as a way to do it.  

Versioning. That's another use for symlinks.  When I manually install certain complex server programs, it is nice to have newer versions appear to be in the same place as the prior version. Makes scripts and config files easier. For example, my blog software:
```
$ tree
.
&#9500;&#9472;&#9472; blog@ -> blog-v3
&#9500;&#9472;&#9472; blog-v1/
&#9500;&#9472;&#9472; blog-v2/
&#9500;&#9472;&#9472; blog-v3/
```

v2 had some bugs, so v3 was pushed out quickly. I don't trust it yet, which is why blog-v1/ is still around.  blog@ denotes a symlink to blog-v3/.  Convenience.  If something is really wrong with v3, I can stop the blog daemon, change the link back to blog-v1/ and restart the daemon.  No need to copy 10G worth of files.  This is a common pattern.

---

### Post by mintmag on 2016-12-18
That's an odd description. Symlinks are defiantly interesting but I think desktop shortcuts are a bit of a waist of their function.

> **The Cog said:**
> 
Symlinks can indeed "retain the root address", if you choose to start  them with a "/" character. If you don't, they are relative to the  location they are redirecting from. Since symlinks are just text, they  can also refer to non-existent locations (known as broken symlinks).

So the use case for symlinks is much wider than just launching  applications from an icon. It is quite fundamental to that way things  are structured. 

I read that Windows has recently acquired the ability to have symlinks,  though I don't think I have seen them actually being used.

Most  of what you wrote in this post has gone way over my head. Symlinks are  like voodoo to me I'm still trying to wrap my head around how they work  and how to use them. You said that they can retain the root address. How  do you do that with a desktop symlink?

---

### Post by TheFu on 2016-12-18
Everything that can be done in a .desktop file, can be done with a script ... except showing an icon.  As a server guy, icons aren't really very important unless they are shown on a webpage or inside a thick application.

symbolic links are really dumb and simple.  It is a pointer from 1 location (directory or file) to another on a Unix-like file system. In programming, we call it a "pointer", which is an extremely powerful idea.  Redirection is very powerful and the more generic that is, the more uses it can support.

I'm confused by the "root" mention too.  "root" has multiple meanings in Linux/Unix.  It is a userid. It is a username.  It denotes the "root directory", / which is where every file and file system mounted can trace their parentage. Usually / doesn't allow normal users to create anything in that directory.  Talking about root vs relative paths is something users may not understand, but every OS has the idea of a root directory.  C:\ is a root directory on Windows.  D:\ is another root directory and every drive letter can have a root on Windows.  On Unix systems, there is only 1 /. 1, not 2, not 26.  One.

Don't know what any of this has to do with deciding where to place programs.  I was thinking from a purely disk storage perspective, but if someone else is looking at this from a menu perspective or placement on a desktop point of view, then symbolic links aren't likely to help.

---

### Post by The Cog on 2016-12-18
> **mintmag said:**
> Most  of what you wrote in this post has gone way over my head. Symlinks are  like voodoo to me I'm still trying to wrap my head around how they work  and how to use them. You said that they can retain the root address. How  do you do that with a desktop symlink?
I had assumed that by "retains the root address" you meant they could give a full path like /users/foo/hello1.txt. If they omit the leading "/" then they describe a location relative to the location of the symlilnk itself. 
It seems that's not what you meant. What did you actually mean?

Try this little demo:
```
mkdir demo1
mkdir demo2
echo This is demo1/aaa > demo1/aaa
echo This is demo1/bbb > demo1/bbb
echo This is demo2/ccc > demo2/ccc
ln -s ../demo1/aaa demo2/ddd
ln -s ../demo1/xxx demo2/eee

```
First just list the files so you can see what's there:
```
ls -l demo*/*
```
For me, I get this output:
```

-rw-rw-r-- 1 steve steve 18 Dec 18 18:49 demo1/aaa
-rw-rw-r-- 1 steve steve 18 Dec 18 18:49 demo1/bbb
-rw-rw-r-- 1 steve steve 18 Dec 18 18:49 demo2/ccc
lrwxrwxrwx 1 steve steve 12 Dec 18 18:49 demo2/ddd -> ../demo1/aaa
lrwxrwxrwx 1 steve steve 12 Dec 18 18:49 demo2/eee -> ../demo1/xxx


```
You can see that demo2/ccc is a normal file. print the file contents with the command "cat demo2/ccc" and see what it says.

You can see that demo2/ddd is a link to ../demo1/aaa, which is actually a redirection another file location. Type the contents with "cat demo2/ddd" and see what it says. 
This is a working symlink. In basically says, "No not here, read/write over there instead".

demo2/eee is a broken symlink. It points to a non-existent location. "cat demo2/eee" will get you an error message. However, if you run the command "echo This is demo2/eee > demo2/eee", it will of course end up writing to demo1/xxx because that's where it is being redirected to.

So symlinks are like landing on a snake or a ladder in a game of snakes and ladders. They take you someplace else instead. That's all. Because a symlink is part of the operation of the filesystem, programs are not aware that their file access has been redirected. There are many reasons why you might want to do that:
* redirect a general filename to specific named versions, e.g. config.txt -> config-version-5.txt,
* redirect specific program names towards a more general purpose program, e.g. /bin/ping6 -> ping
* redirect a commonly used directory to a different but preferred location (on a disk with more space perhaps)
* Give a file multiple names, as with my CD/DVD drive having multiple names.

---

### Post by mintmag on 2016-12-19
I'm a GUI user and try to avoid CLI because I am a desktop user. root is a word that can have many different meanings. By root address I mean the root address of the file.

example A: xdg-open /home/mintmag/Documents opens that address. Exsample B simlink documents opens  /home/mintmag/Desktop/simlinked-docuemtns

---

### Post by mintmag on 2016-12-19
> **TheFu said:**
> Everything that can be done in a .desktop file, can be done with a script ... except showing an icon.  As a server guy, icons aren't really very important unless they are shown on a webpage or inside a thick application.

symbolic links are really dumb and simple.  It is a pointer from 1 location (directory or file) to another on a Unix-like file system. In programming, we call it a "pointer", which is an extremely powerful idea.  Redirection is very powerful and the more generic that is, the more uses it can support.

I'm confused by the "root" mention too.  "root" has multiple meanings in Linux/Unix.  It is a userid. It is a username.  It denotes the "root directory", / which is where every file and file system mounted can trace their parentage. Usually / doesn't allow normal users to create anything in that directory.  Talking about root vs relative paths is something users may not understand, but every OS has the idea of a root directory.  C:\ is a root directory on Windows.  D:\ is another root directory and every drive letter can have a root on Windows.  On Unix systems, there is only 1 /. 1, not 2, not 26.  One.

Don't know what any of this has to do with deciding where to place programs.  I was thinking from a purely disk storage perspective, but if someone else is looking at this from a menu perspective or placement on a desktop point of view, then symbolic links aren't likely to help.

Well I'm a desktop user and prefer the GUI. I think someone mentioned that you can use simlinks redirect where programs get installed. Can you do that? I mostly started this thread in the OS chat instead of the tech support section because it's a question of curiosity. Why does Linux have stricter access to where programs go. I'm sure there's a reason for it, has it got something to do with it's design?

---

### Post by The Cog on 2016-12-19
> **mintmag said:**
> Why does Linux have stricter access to where programs go. I'm sure there's a reason for it, has it got something to do with it's design?
It doesn't. 
Both Linux and Windows allow you to install programs wherever you like (access restrictions permitting). 
For both operating systems, you can find installers that ask where you want to install programs. 
For both operating systems, it seems to me that the majority of installers simply use a default location, often in "Program Files" for windows and in /opt for Linux.

---

### Post by TheFu on 2016-12-19
> **mintmag said:**
> Well I'm a desktop user and prefer the GUI. I think someone mentioned that you can use simlinks redirect where programs get installed. Can you do that? I mostly started this thread in the OS chat instead of the tech support section because it's a question of curiosity. Why does Linux have stricter access to where programs go. I'm sure there's a reason for it, has it got something to do with it's design?

It isn't Linux. Linux is extremely flexible - beyond pretty much any other OS. In a basic Linux install with just a minimal set of programs, there isn't a package manager and we place programs where ever we like. The management overhead is something we understand.  Your home router is like this. It doesn't have a package manager and still runs Linux.  Same for whatever device you use as a media player - a chromecast, WD Player, ... no package manager.  They simply don't want to waste the storage for those extra tools.

Ubuntu, Debian, Redhat, SuSE, and pretty much every other "distro" have specific locations for things to ease package management and interoperability between tens of thousands of programs.  It wasn't always that way. In the mid-1990s nobody did package management. We did everything for every program manually. Imagine having to deal with program-to-program-to-library dependencies manually. It sucked.  APT is amazing. It has gotten smarter over the years.  APT is amazing. The trade-off is that we accept the default installation locations. That is well worth the trade-off, IMHO.

If you plan to remain a "desktop only user", many of these things will be impossible to explain.  The GUI isn't where 90% of the power for Linux lies. The GUI is a 10% windows in to the operating system. If that meets your needs, great!  OTOH, with a little lower level understanding, you'll be able to accomplish things GUI users never knew were even possible.  That can be both limiting and freeing.  Sometimes I don't know how to get "there" from here, because of a deeper understanding.  OTOH, when I look at any Apple or Android product, since these are all based on Unix, I have a different level of understanding.

For example, your definition of "address" as "root address" isn't correct, IMHO.  It is a directory, which is sorta like an address - address is extremely generic. Directory would be more specific and accurate. Inside a browser program, that area of the screen is called an "address bar." Don't know what other programs call it and since many do accept URL-like constructs (sftp://, ssh://, etc), perhaps address bar fits?  I dunno.

On Unix-like systems the root directory is /. PERIOD.

BTW, I figure that I understand about 10% of Linux. I've only been studying it for 26 years. ;)

---

### Post by Geoffrey_Arndt on 2016-12-19
+1 * 100 for post 23 by Mr. Manchu . . . . 

Perhaps MintMag is just now getting an inkling of what OS's,  Linux & Unix are about.   I love the saying "never make something simpler than it absolutely needs to be" . . .

---

### Post by nothingspecial on 2016-12-19
The whole point of Ubuntu is to be easy.

The package manager puts programs in certain directories to make things easier.

Complex programs require other programs to run (dependencies). If those "dependencies" are not where the complex program expects them to be, they won't run. So the package manager puts them where they are expected to be. This is easier.

There is also your $PATH [https://en.wikipedia.org/wiki/PATH_(variable)](https://en.wikipedia.org/wiki/PATH_(variable))

Your path is a list of folders (directories) in which Ubuntu expects or searches for a program.

I have some custom programs (scripts) I've made myself in /home/me/bin because /home/me/bin is in my $PATH. I could make a folder to put them in called /var/snowman/banana if I wanted to. But I would have to change my $PATH to inlcude /var/snowman/banana (or run them from their parent directory (but I'm trying to keep this realy simple)). So placing them in /home/me/bin is easier.

They depend on other programs. Because these other programs are where they are supposed to be, the script just calls them by their name. If these other programs were scattered all over the place it would be more difficult.

In short, this is linux, you can do whatever you want, you can put programs wherever you want. But why would you?  Ubuntu has set it all up so you don't have to.

---

### Post by TheFu on 2016-12-19
The Unix Philosophy from different, "old guys" [https://en.wikipedia.org/wiki/Unix_philosophy](https://en.wikipedia.org/wiki/Unix_philosophy) - skimming this will open some eyes.

It is VERY different from the ways that Windows, DOS, OSX are designed.  It seems to be different from the philosophies of the current generation of Linux GUI designers too, but that is absolutely fine.  **Choice is good.**

Good chat.

---

### Post by SeijiSensei on 2016-12-19
Did you read the link that Charles posted at the top of this thread: [http://www.thegeekstuff.com/2010/09/linux-file-system-structure/](http://www.thegeekstuff.com/2010/09/linux-file-system-structure/)

The mainstream Linux distributions adhere to something called the [Filesystem Hierarchy Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard).  It defines the locations of files according to type.

In principle you can put a binary executable anywhere you want in the filesystem and run it with a command like
```
/path/to/my/really/obscure/directory/program
```
but that would create chaos.  So executable programs are usually stored in just a few places like /bin and /usr/bin.  To understand the difference between those two locations requires understanding the difference between "single-user" and "multi-user" mode.

When Linux boots up, it runs in single-user mode.  Everything is being run by the root user.  At some point during the boot process, Linux goes into multi-user mode.  Programs run during the first phase are stored in /bin (and /sbin; see below).  That's because Unix systems need not store the /usr filesystem on the same device as / itself.  On traditional networks, administrators could maintain a central archive of executables on a common server which was mounted over the network to /usr on client machines during the switch to multi-user mode.  Any programs that ordinary users other than root might run in multi-user mode thus need to be in /usr/bin, though users can run programs in /bin as well.  (Most of those are utilities like ping, grep and sed which might be needed in both modes.)

There are corresponding "supervisor" directories which contain programs primarily intended for the root user.  The /sbin directory is available during single-user mode.  It contains programs like fsck, the "chkdsk" equivalent in Linux, which may be needed during boot, but which may also be run when the system is fully functioning.  The corresponding /usr/sbin directory contains programs that may be started by root but change their ownership to another, less-privileged user when they are running for security reasons.  The Apache web server is a good example; it starts as root but quickly becomes owned by the "www-data" user on Debian and Ubuntu systems.

Because Unix was designed to rely on plain-text configuration files, the closest Linux equivalent to the Windows registry is /etc.  Well-behaved programs place their configuration files in either /etc itself or a custom subdirectory like /etc/X11 for the X11 graphics subsystem.

There is also a directory structure under /usr/local which is generally reserved for programs and associated content not installed by the standard methods like the .deb files in Ubuntu.  If, for instance, you download and compile the source code for a standards-compliant program, it will install itself under /usr/local so as not to interfere with other versions of the program that came with the standard distribution. If you run the command "echo $PATH" at the prompt, you'll see that directories like /usr/local/bin are consulted before ones like /usr/bin, so the operating system will choose a local version of a program over the standard version installed from .debs.

---

### Post by mintmag on 2016-12-19
Yes I have read [http://www.thegeekstuff.com/2010/09/linux-file-system-structure/](http://www.thegeekstuff.com/2010/09/linux-file-system-structure/) and many articles like it. This is just curiosity about the Linux infrastructure. When installing programs you are not prompted to where you want it to go and trying to change it is not recommended. This is because it's not designed that way**.** I would like to know why is works the way it does. A lot of these posts have been filled with lost of useful information, but I was hopping for something a little simpler. What are the advantages of having a package manager store all your files in one place like this?

---

### Post by oldos2er on 2016-12-19
Closed for staff review.

EDIT

Conditionally re-opened.

---

### Post by DuckHook on 2016-12-19
> **SeijiSensei said:**
> &#8230;In principle you can put a binary executable anywhere you want in the filesystem and run it with a command like
```
/path/to/my/really/obscure/directory/program
```
but that would create chaos.> **mintmag said:**
> &#8230;What are the advantages of having a package manager store all your files in one place like this?:confused:

Question answered ten ways to Sunday, yet posed again anyway. One would begin to suspect a reading comprehension issue here, or an attempt at wasting everyone's time.

This thread is now eating its own tail.

@OP

If you have a *real* question, please ask it. Else this thread will be closed permanently.

---

### Post by mintmag on 2016-12-19
You know I'm not a Linux expert right? Almost all my threads have been closed by the mods. Alright I have one for you. Do you really think that bullying someone who's just trying to learn how things work and why things are like the way they are is really going to bring more people over. I have accounts on both Manjaro and Fedura and haven't had to deal with any of this nonsense before. I won't be posting anymore threads for a while, go ahead and close it. I'll PM someone for more information.

---

### Post by wildmanne39 on 2016-12-19
You keep asking why, if you want to know for sure please pose the question to the one person who can answer and that would be the creator of linux. We are just simple users with no hand in why or how it was designed.

It is not the fact that you asked the question but it is the fact that none of the answers ever seem to satisfy you that is the real  issue here.

---

### Post by QIII on 2016-12-19
PMing for help is discouraged as highly unfair to all the other members of the forum who are robbed of solutions given.  Please do not do that.  Unsolicited PMs typically get reported by the receiver, in which case you will hear from us.

What might be better is to stop for a moment, read what you have been given and stop going back over the same tracks as you have done in this and other threads.

---

### Post by DuckHook on 2016-12-19
I will only say this once.

We routinely welcome new users on these forums with patience and goodwill. The vast majority have their problems happily solved. Some even go on to become experts in their own right and contribute back to these forums with their expertise. ***None*** of us have forgotten what it feels like to be a new user, lost at sea, wrestling with an OS that we do not understand. It is churlish of you to suggest so.

However, this is *not* what is occurring with your posts. Contrary to your statement, your posts have nothing to do with seeking more knowledge or with clarification. You habitually repeat the same query with no respect for the fact that it has already been answered. This is unfair not only to the one answering, but to the entire community, because our limited pool of expertise is expended in repeating explanations that you just don't feel like accepting.

Far from "bullying" you, I took pains to quote two passages in my last post: the one from one of our forum gurus who answered you with precision and skill, and the other from you yet again repeating the same question ad nauseum.

This thread has now exhausted its course and is closed.

---

