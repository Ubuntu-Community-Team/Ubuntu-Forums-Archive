---
title: "How To - Compile and Install Unison File Sychronizer from SVN"
date: 2008-06-01
forum: Security
---

### Post by kevdog on 2008-06-01
**[SIZE="5"]Unison File Synchronizer[/SIZE]**

Unison is a file synchronizer (MAC, Windows, Linux compatible), that allows two replicas of files stored on two separate computers to be synchronized by simply propagating the changes between each replica.  Unison is akin to rsync (in fact it uses rsync), however it is truly a two-way synchronization tool, rather than a simple one-way mirroring utility.  More information about the Unison File Synchronizer can be found here: [http://www.cis.upenn.edu/~bcpierce/unison/index.html](http://www.cis.upenn.edu/~bcpierce/unison/index.html)

Unison is contained with the Ubuntu repositories.  There are graphical and console-based versions of the program.  It is possible to simplify the process of installation with:
```

sudo aptitude install unison-gtk unison

``` 

Unison is a state of constant development.  Many new features and bugs are rapidly fixed and new functionality added.  To take advantage of these newer and fixed features, it is often necessary to run client and server versions of Unison that are much newer than those contained within the Ubuntu/Debian repository.

Instructions to compile and build Unison from svn sources (the most recent-bleeding edge version of unison) are described below

**[SIZE="5"]Installation of the Unison File Synchronizer from SVN sources[/SIZE]**

**Install Dependencies**
```
sudo aptitude install build-essential linux-headers-$(uname -r) subversion ocaml liblablgtk2-ocaml-dev
```

**Download and Install Unison SVN sources**
```

cd ~
mkdir Source
cd Source
svn co https://webdav.seas.upenn.edu/svn/unison/trunk unison
cd unison/src
make (Ignore error about etags)
mv unison unison-gtk
make clean
make UISTYLE=text (Ignore error about etags)

sudo cp unison unison-gtk /usr/bin

```

The unison svn binaries should now be installed in /usr/bin.  To test and see the currently installed unison version
```

$ unison-gtk -version
$ unison -version
unison version 2.28.34

```

The unison console based version should always be used on the server.  The unison-gtk GUI or unison text version may be used as the client.

**[SIZE="5"]Client available for Other Platforms[/SIZE]**

Although not truly svn client versions, cutting edge pre-compiled binaries may be found for both MAC and Windows versions here:
[http://alan.petitepomme.net/projets/unison/index.html](http://alan.petitepomme.net/projets/unison/index.html).  Please note that in order to use the Windows GTK version, the GTK+ 2.12 runtime environment must be installed.  This may be installed from [http://downloads.sourceforge.net/pidgin/gtk-runtime-2.12.1-rev-b.exe](http://downloads.sourceforge.net/pidgin/gtk-runtime-2.12.1-rev-b.exe)

---

### Post by bjornsam on 2009-04-15
Thanks for the install instruktions :KS

---

### Post by Tex-Twil on 2009-10-23
Hello,
how can I compile a 64bit version ? I tried just "make" it on a 64bits Ubuntu but the produced binary is still a 32 bit. 

Thanks,
Tex

---

### Post by kevdog on 2009-10-24
How do you know its still 32 bits?

---

### Post by Tex-Twil on 2009-10-24
```

file unison

```

tells me that it's a 32bits executable.

---

### Post by kevdog on 2009-10-24
I'm not sure if I can answer your question.  My bet is b/c your using gtk 32 bit libraries to link against -- or possibly its a 32 bit ocaml compiler.

---

### Post by Tex-Twil on 2009-10-24
> **kevdog said:**
> I'm not sure if I can answer your question.  My bet is b/c your using gtk 32 bit libraries to link against -- or possibly its a 32 bit ocaml compiler.
I'm not linking it against the gtk stuff since I need no GUI.

How can I get a 64bit ocaml ?

---

