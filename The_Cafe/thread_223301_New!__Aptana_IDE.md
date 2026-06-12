---
title: "New!  Aptana IDE"
date: 2006-07-26
forum: The Cafe
---

### Post by racoq on 2006-07-26
Great html, javascript, and css IDE, here is a quote from the official website:

```

Aptana is a robust, JavaScript-focused IDE for building dynamic web applications. Highlights include the following features:

    * Code Assist on JavaScript, HTML, and CSS languages, including your own JavaScript functions
    * Outliner that gives a snapshot view of your JavaScript, HTML, and CSS code structure
    * Error and warning notification for your code
    * Support for Aptana UI customization and extensions
    * Cross-platform support
    * Free and open source. (Source available soon)

```

Its open-source (although its code was not released yet), and it's multi platform, Windows, Linux, Mac, and it has a plugin which supports integration with eclipse.

I think it worths trying.

Aptana Website:

[http://www.aptana.com/](http://www.aptana.com/)

---

### Post by sas171 on 2006-07-28
Looks very nice. When can we expect this one in the repos or at least .deb?

---

### Post by mingster on 2006-07-28
I'm downloading it right now...

If it's up to scratch I'll be replacing dreamweaver with it at work.

*fingers crossed*

Damn IT director put the block on me getting the company to switch from windross to Ubuntu :(

---

### Post by Dagur on 2006-07-28
I tried installing from their .bin file but got this:

```

dagur@dagur64:~/downloaded$ ./Aptana_IDE_Setup.bin
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
nawk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
hostname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

Launching installer...

grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/tmp/install.dir.11447/Linux/resource/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory


```

I should point out that I'm using the 64 version of dapper

---

### Post by Virogenesis on 2006-07-28
try installing eclipse from the repos i found it easier that way.
Thats what I did and.... well I've had it open for about 2 days

---

### Post by Dagur on 2006-07-28
weird, I didn't find it in the repos. 

I however had an eclipse installation and could install aptana as a plugin. Worked fine I think.

---

### Post by Virogenesis on 2006-07-28
> **Dagur said:**
> weird, I didn't find it in the repos. 

I however had an eclipse installation and could install aptana as a plugin. Worked fine I think.

Thats because it ain't in the repos but eclipse is and installing aptana as a n eclipse plug in will give you the same functions plus more.

---

### Post by snowpalmer on 2006-07-28
This is what I had to do to get the download of Aptana to work.

First I chmod'd the file to give it execute permissions

```
chmod +x Aptana_IDE_Setup.bin
```

Then I executed it

```
./Aptana_IDE_Setup.bin
```

It ran some stuff and then the GUI installer started. You specify the install location and it does it's stuff. Once it was complete I had to install the SWT library from the repository.

```
sudo aptitude install libswt3.1-gtk-java
```

Then I created a little shell script to start Aptana up since it needs an environment variable set.

```

#/usr/bin
export MOZILLA_FIVE_HOME=/usr/lib/mozilla
~/bin/Aptana/aptana

```

I named that file aptana and put it right in ~/bin/. Ofcourse that's a directory that I had created previously and it's where I installed aptana at.  I might have already had some prerequisite dependancies installed since I didn't get a problem on the initial installer.

Snowpalmer

---

### Post by malcolmb on 2006-07-29
Thanks snowpalmer, I was trying to figure out a way to have the mozilla_five_home variable permanently set to the path instead of just for the terminal session.  Being a noob i didn't even think of just putting it into the shell script.

Aptana so far seems to be a nice IDE and lets see where it goes.

---

### Post by Cyraxzz on 2006-07-29
looks good.

---

### Post by Linuturk on 2006-07-29
When can we expect to find a package in the repo's?

---

### Post by vdemeester on 2006-08-01
Aptana is still at version 0.31 beta.. I don't think we could find it in the official repos since it's stable..
But in a custom user repos.. why not ?

---

### Post by afterxleep on 2006-10-04
Here you go.

Testing .deb package on the way...

[http://www.aptana.com/forums/viewtopic.php?t=520](http://www.aptana.com/forums/viewtopic.php?t=520)

---

### Post by wladston on 2006-11-18
Tried the repo, but it didn't work correctly with me.

Anyone knows any other repo ?? Or another package ??

On the project view, when I click to open a new file, it shows the aptana spash screen again and nothing happens .. weird ...

---

