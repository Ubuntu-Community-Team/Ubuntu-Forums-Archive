---
title: "Install BankID?"
date: 2013-11-11
forum: Security
---

### Post by Niemil on 2013-11-11
I need to install BankID in order to send in some blankets to a website.

I finding the download page in here: [https://install.bankid.com]("https://install.bankid.com/")
But for me it says: "[COLOR=#363636][FONT=Arial]Your platform Linux 64-bit is not supported. [/FONT][/COLOR][You find information about supported platforms here.]("http://support.bankid.com/")"

But then I go here: [https://install.bankid.com/Download/All](https://install.bankid.com/Download/All)
And it says there is a download for Ubuntu/Linux, I downloaded the files, but it is massive of files. Looks like this: [http://screencloud.net/v/kYwK](http://screencloud.net/v/kYwK)

Does it work to install this? how should I place the files?

This software is simply some software that needs to be open on my computer, and then I go visit a website that have this Bank ID available, and a popup will appear in the browser and I will be able to login.

Or do I have to go another way around? Do I need use some virtualbox or wine?

---

### Post by th.sigit on 2013-11-11
You could extract the downloaded archive anywhere you want, from the command line typically 

> tar -zxvf BISP-.4.1.19.1.11663.tar.gz

still from the command line, go to BISP-.4.1.19.1.11663 folder the archive will have just created, and from there run the .sh file 
(from your screenshot, I think it is called install.4.1.19.1.11663.sh) by typing 

> ./install.4.1.19.1.11663.sh

(Don't forget to put ./ in front of the filename)

---

### Post by Niemil on 2013-11-11
Well, for first command I tested do it, I wrote **tar -zxvf **and then i copied the name of the archive and pasted. But it said that the file/archive doesn't exist.
Tried do same with the [B]./
[/B]I manually extracted the archive and then tried run the code, but that didn't work either, it just say that it doesn't exist (and yeah, the name is correct, I copied from 'rename' on the file).

Then I also been trying open the file manually, and chosed to open with terminal, but it just opened and closed instantly.

---

### Post by ajgreeny on 2013-11-11
You need to run that first tar command in the folder where the archive is sitting, so if you downloaded to your Desktop folder run command **cd Desktop** first then the **tar -zxvf filename**.

---

### Post by th.sigit on 2013-11-11
Looking at your screenshot, the archive you've downloaded is called BISP-.4.1.19.1.11663(1).tar.gz -->double download maybe?

So first you need to go the folder where you've downloaded that archive, and run this in the command line:

> tar -zxvf BISP-.4.1.19.1.11663(1).tar.gz 			 		

And tried to run the *install.4.1.19.1.11663.sh* as described above.

Hope it helps!

---

### Post by Niemil on 2013-11-11
Well, it didn't work.
And I actually have one without the "(1)". I had downloaded the same file two times, and kept both. 
Here is another screenshot of it:
[http://screencloud.net/v/7BE9](http://screencloud.net/v/7BE9)

Gotta sleep now.

---

### Post by th.sigit on 2013-11-12
Ok, I've downloaded the archive from that site and try to replicate your problem, and here's how I did it in my computer. 

Make sure your doing it from the command line because extracting the archive using GUI may result a minor error (the *install.4.1.19.1.11663.sh* located at *~/Downloads_/BISP-4.19.1.11663/BISP-4.19.1.11663_/install.4.1.19.1.11663.sh* instead of *~/Downloads_/BISP-4.19.1.11663/_install.4.1.19.1.11663.sh*).

Simply cut and paste these lines instead of typing it (I've double checked it, last night I didn't sleep at all and make a few mistakes ....)

From your home directory, on the command line:

> cd Downloads
> tar -zxvf BISP-4.19.1.11663.tar.gz
> cd BISP-4.19.1.11663
> sudo ./install.4.19.1.11663.sh i

When it's finished it'll say:

[FONT=arial]Installing BankID Security Application
Installation complete.[/FONT]

Here's my screenshot

[[img]http://s24.postimg.org/kjxwely35/bank_ID.jpg[/img]](http://postimg.org/image/kjxwely35/)

[http://postimg.org/image/kjxwely35/](http://postimg.org/image/kjxwely35/)

---

### Post by Niemil on 2013-11-12
Ah thank you! 

I found the BankID security in the applications, under the dash.
However, it seems like it wont open?

I tried click it, multiple times to make sure it is open.
I been entering my bank and other pages where I need this one, but at my bank when I were going to create an ID for the app, it says that I doesn't have the BankID security application installed (or atleast not runned).

---

### Post by apollothethird on 2013-11-12
> **Niemil said:**
> Ah thank you! 

I found the BankID security in the applications, under the dash.
However, it seems like it wont open?

I tried click it, multiple times to make sure it is open.
I been entering my bank and other pages where I need this one, but at my bank when I were going to create an ID for the app, it says that I doesn't have the BankID security application installed (or atleast not runned).

Will you give us the output of:

```

$ personal

```

Type in that command from your home directory.

Running an application from the commandline will provide the benefit of clear error messages.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by Niemil on 2013-11-12
> **apollothethird said:**
> Will you give us the output of:

```

$ personal

```

Type in that command from your home directory.

Running an application from the commandline will provide the benefit of clear error messages.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")
Hm, how do you mean? I type it in terminal at home directory?
Here is screenshot of what I tried (some failure in beginning, but at end still same error anyway)[IMG]http://screencloud.net//img/screenshots/2dca85533a782a69ff351d3f5545688f.png[/IMG]

---

### Post by apollothethird on 2013-11-12
> **Niemil said:**
> Hm, how do you mean? I type it in terminal at home directory?
Here is screenshot of what I tried (some failure in beginning, but at end still same error anyway)[IMG]http://screencloud.net//img/screenshots/2dca85533a782a69ff351d3f5545688f.png[/IMG]

First I'll mention that I can read text much easier than I can read pictures.

The error message you're getting is because the application is looking for a 32bit version of libraries on your system.  You can add the 32bit support in a number of ways.

Try installing this modules to begin with:

```

$ sudo apt-get install lib32z1 lib32ncurses5 lib32bz2-1.0
$ sudo apt-get install libgtk2.0-0:i386
$ personal

```

Notice how I put my text between code tags.  This will make it easy for you to read the information.  If I had used a picture for the text, reading it (at least for me) wouldn't have been as easy.

Let me know if the program progresses further after installing those modules.  Also give us the text output of the error message using code tags.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")

---

### Post by Niemil on 2013-11-12
> **apollothethird said:**
> First I'll mention that I can read text much easier than I can read pictures.

The error message you're getting is because the application is looking for a 32bit version of libraries on your system.  You can add the 32bit support in a number of ways.

Try installing this modules to begin with:

```

$ sudo apt-get install lib32z1 lib32ncurses5 lib32bz2-1.0
$ sudo apt-get install libgtk2.0-0:i386
$ personal

```

Notice how I put my text between code tags.  This will make it easy for you to read the information.  If I had used a picture for the text, reading it (at least for me) wouldn't have been as easy.

Let me know if the program progresses further after installing those modules.  Also give us the text output of the error message using code tags.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")

Oh okey. Here is output :)

```
sozu@HP625:~$ sudo apt-get install lib32z1 lib32ncurses5 lib32bz2-1.0[sudo] password for sozu: 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libunistring0:i386 gir1.2-ubuntuoneui-3.0 guile-1.8-libs libgomp1:i386
  librhythmbox-core5 libfam0 libgdu-gtk0 libavahi-ui-gtk3-0 libcroco3:i386
  language-pack-kde-en kde-l10n-engb libgettextpo0:i386 libubuntuoneui-3.0-1
  thunderbird-globalmenu libmusicbrainz3-6 language-pack-kde-en-base
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  lib32tinfo5 libc6-i386
The following NEW packages will be installed:
  lib32bz2-1.0 lib32ncurses5 lib32tinfo5 lib32z1 libc6-i386
0 upgraded, 5 newly installed, 0 to remove and 3 not upgraded.
Need to get 4,280 kB of archives.
After this operation, 10.8 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libc6-i386 amd64 2.15-0ubuntu10.5 [3,992 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise/main lib32bz2-1.0 amd64 1.0.6-1 [33.3 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise/main lib32tinfo5 amd64 5.9-4 [90.1 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ precise/main lib32ncurses5 amd64 5.9-4 [114 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ precise/main lib32z1 amd64 1:1.2.3.4.dfsg-3ubuntu4 [51.1 kB]
Fetched 4,280 kB in 4s (939 kB/s)
Selecting previously unselected package libc6-i386.
(Reading database ... 212599 files and directories currently installed.)
Unpacking libc6-i386 (from .../libc6-i386_2.15-0ubuntu10.5_amd64.deb) ...
Replaced by files in installed package libc6:i386 ...
Setting up libc6-i386 (2.15-0ubuntu10.5) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously unselected package lib32bz2-1.0.
(Reading database ... 212905 files and directories currently installed.)
Unpacking lib32bz2-1.0 (from .../lib32bz2-1.0_1.0.6-1_amd64.deb) ...
Selecting previously unselected package lib32tinfo5.
Unpacking lib32tinfo5 (from .../lib32tinfo5_5.9-4_amd64.deb) ...
Selecting previously unselected package lib32ncurses5.
Unpacking lib32ncurses5 (from .../lib32ncurses5_5.9-4_amd64.deb) ...
Selecting previously unselected package lib32z1.
Unpacking lib32z1 (from .../lib32z1_1%3a1.2.3.4.dfsg-3ubuntu4_amd64.deb) ...
Setting up lib32bz2-1.0 (1.0.6-1) ...
Setting up lib32tinfo5 (5.9-4) ...
Setting up lib32ncurses5 (5.9-4) ...
Setting up lib32z1 (1:1.2.3.4.dfsg-3ubuntu4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
sozu@HP625:~$ sudo apt-get install libgtk2.0-0:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libunistring0:i386 gir1.2-ubuntuoneui-3.0 guile-1.8-libs libgomp1:i386
  librhythmbox-core5 libfam0 libgdu-gtk0 libavahi-ui-gtk3-0 libcroco3:i386
  language-pack-kde-en kde-l10n-engb libgettextpo0:i386 libubuntuoneui-3.0-1
  thunderbird-globalmenu libmusicbrainz3-6 language-pack-kde-en-base
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libatk1.0-0:i386 libcairo2:i386 libdatrie1:i386 libgdk-pixbuf2.0-0:i386
  libjasper1:i386 libpango1.0-0:i386 libpixman-1-0:i386 libthai0:i386
  libxcb-render0:i386 libxcb-shm0:i386 libxft2:i386
Suggested packages:
  librsvg2-common:i386 gvfs:i386 libjasper-runtime:i386 ttf-baekmuk:i386
  ttf-arphic-gbsn00lp:i386 ttf-arphic-bsmi00lp:i386 ttf-arphic-gkai00mp:i386
  ttf-arphic-bkai00mp:i386
The following NEW packages will be installed:
  libatk1.0-0:i386 libcairo2:i386 libdatrie1:i386 libgdk-pixbuf2.0-0:i386
  libgtk2.0-0:i386 libjasper1:i386 libpango1.0-0:i386 libpixman-1-0:i386
  libthai0:i386 libxcb-render0:i386 libxcb-shm0:i386 libxft2:i386
0 upgraded, 12 newly installed, 0 to remove and 3 not upgraded.
Need to get 4,280 kB of archives.
After this operation, 11.1 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise/main libatk1.0-0 i386 2.4.0-0ubuntu1 [58.7 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise/main libpixman-1-0 i386 0.24.4-1 [243 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libxcb-render0 i386 1.8.1-1ubuntu0.2 [14.2 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libxcb-shm0 i386 1.8.1-1ubuntu0.2 [5,696 B]
Get:5 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libcairo2 i386 1.10.2-6.1ubuntu3 [490 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ precise/main libdatrie1 i386 0.2.5-3 [16.9 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ precise/main libjasper1 i386 1.900.1-13 [153 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ precise/main libgdk-pixbuf2.0-0 i386 2.26.1-1 [194 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ precise/main libthai0 i386 0.1.16-3 [20.2 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ precise/main libxft2 i386 2.2.0-3ubuntu2 [42.4 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libpango1.0-0 i386 1.30.0-0ubuntu3.1 [361 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ precise/main libgtk2.0-0 i386 2.24.10-0ubuntu6 [2,681 kB]
Fetched 4,280 kB in 5s (733 kB/s)         
Selecting previously unselected package libatk1.0-0:i386.
(Reading database ... 212935 files and directories currently installed.)
Unpacking libatk1.0-0:i386 (from .../libatk1.0-0_2.4.0-0ubuntu1_i386.deb) ...
Selecting previously unselected package libpixman-1-0:i386.
Unpacking libpixman-1-0:i386 (from .../libpixman-1-0_0.24.4-1_i386.deb) ...
Selecting previously unselected package libxcb-render0:i386.
Unpacking libxcb-render0:i386 (from .../libxcb-render0_1.8.1-1ubuntu0.2_i386.deb) ...
Selecting previously unselected package libxcb-shm0:i386.
Unpacking libxcb-shm0:i386 (from .../libxcb-shm0_1.8.1-1ubuntu0.2_i386.deb) ...
Selecting previously unselected package libcairo2:i386.
Unpacking libcairo2:i386 (from .../libcairo2_1.10.2-6.1ubuntu3_i386.deb) ...
Selecting previously unselected package libdatrie1:i386.
Unpacking libdatrie1:i386 (from .../libdatrie1_0.2.5-3_i386.deb) ...
Selecting previously unselected package libjasper1:i386.
Unpacking libjasper1:i386 (from .../libjasper1_1.900.1-13_i386.deb) ...
Selecting previously unselected package libgdk-pixbuf2.0-0:i386.
Unpacking libgdk-pixbuf2.0-0:i386 (from .../libgdk-pixbuf2.0-0_2.26.1-1_i386.deb) ...
Selecting previously unselected package libthai0:i386.
Unpacking libthai0:i386 (from .../libthai0_0.1.16-3_i386.deb) ...
Selecting previously unselected package libxft2:i386.
Unpacking libxft2:i386 (from .../libxft2_2.2.0-3ubuntu2_i386.deb) ...
Selecting previously unselected package libpango1.0-0:i386.
Unpacking libpango1.0-0:i386 (from .../libpango1.0-0_1.30.0-0ubuntu3.1_i386.deb) ...
Selecting previously unselected package libgtk2.0-0:i386.
Unpacking libgtk2.0-0:i386 (from .../libgtk2.0-0_2.24.10-0ubuntu6_i386.deb) ...
Setting up libatk1.0-0:i386 (2.4.0-0ubuntu1) ...
Setting up libpixman-1-0:i386 (0.24.4-1) ...
Setting up libxcb-render0:i386 (1.8.1-1ubuntu0.2) ...
Setting up libxcb-shm0:i386 (1.8.1-1ubuntu0.2) ...
Setting up libcairo2:i386 (1.10.2-6.1ubuntu3) ...
Setting up libdatrie1:i386 (0.2.5-3) ...
Setting up libjasper1:i386 (1.900.1-13) ...
Setting up libgdk-pixbuf2.0-0:i386 (2.26.1-1) ...
Setting up libthai0:i386 (0.1.16-3) ...
Setting up libxft2:i386 (2.2.0-3ubuntu2) ...
Setting up libpango1.0-0:i386 (1.30.0-0ubuntu3.1) ...
Setting up libgtk2.0-0:i386 (2.24.10-0ubuntu6) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
sozu@HP625:~$ personal
/usr/local/lib/personal/personal.bin: error while loading shared libraries: libidn.so.11: cannot open shared object file: No such file or directory
sozu@HP625:~$ 



```

---

### Post by apollothethird on 2013-11-12
> **Niemil said:**
> Oh okey. Here is output :)

```
sozu@HP625:~$ sudo apt-get install lib32z1 lib32ncurses5 lib32bz2-1.0[sudo] password for sozu: 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libunistring0:i386 gir1.2-ubuntuoneui-3.0 guile-1.8-libs libgomp1:i386
  librhythmbox-core5 libfam0 libgdu-gtk0 libavahi-ui-gtk3-0 libcroco3:i386
  language-pack-kde-en kde-l10n-engb libgettextpo0:i386 libubuntuoneui-3.0-1
  thunderbird-globalmenu libmusicbrainz3-6 language-pack-kde-en-base
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  lib32tinfo5 libc6-i386
The following NEW packages will be installed:
  lib32bz2-1.0 lib32ncurses5 lib32tinfo5 lib32z1 libc6-i386
0 upgraded, 5 newly installed, 0 to remove and 3 not upgraded.
Need to get 4,280 kB of archives.
After this operation, 10.8 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libc6-i386 amd64 2.15-0ubuntu10.5 [3,992 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise/main lib32bz2-1.0 amd64 1.0.6-1 [33.3 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise/main lib32tinfo5 amd64 5.9-4 [90.1 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ precise/main lib32ncurses5 amd64 5.9-4 [114 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ precise/main lib32z1 amd64 1:1.2.3.4.dfsg-3ubuntu4 [51.1 kB]
Fetched 4,280 kB in 4s (939 kB/s)
Selecting previously unselected package libc6-i386.
(Reading database ... 212599 files and directories currently installed.)
Unpacking libc6-i386 (from .../libc6-i386_2.15-0ubuntu10.5_amd64.deb) ...
Replaced by files in installed package libc6:i386 ...
Setting up libc6-i386 (2.15-0ubuntu10.5) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously unselected package lib32bz2-1.0.
(Reading database ... 212905 files and directories currently installed.)
Unpacking lib32bz2-1.0 (from .../lib32bz2-1.0_1.0.6-1_amd64.deb) ...
Selecting previously unselected package lib32tinfo5.
Unpacking lib32tinfo5 (from .../lib32tinfo5_5.9-4_amd64.deb) ...
Selecting previously unselected package lib32ncurses5.
Unpacking lib32ncurses5 (from .../lib32ncurses5_5.9-4_amd64.deb) ...
Selecting previously unselected package lib32z1.
Unpacking lib32z1 (from .../lib32z1_1%3a1.2.3.4.dfsg-3ubuntu4_amd64.deb) ...
Setting up lib32bz2-1.0 (1.0.6-1) ...
Setting up lib32tinfo5 (5.9-4) ...
Setting up lib32ncurses5 (5.9-4) ...
Setting up lib32z1 (1:1.2.3.4.dfsg-3ubuntu4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
sozu@HP625:~$ sudo apt-get install libgtk2.0-0:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libunistring0:i386 gir1.2-ubuntuoneui-3.0 guile-1.8-libs libgomp1:i386
  librhythmbox-core5 libfam0 libgdu-gtk0 libavahi-ui-gtk3-0 libcroco3:i386
  language-pack-kde-en kde-l10n-engb libgettextpo0:i386 libubuntuoneui-3.0-1
  thunderbird-globalmenu libmusicbrainz3-6 language-pack-kde-en-base
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libatk1.0-0:i386 libcairo2:i386 libdatrie1:i386 libgdk-pixbuf2.0-0:i386
  libjasper1:i386 libpango1.0-0:i386 libpixman-1-0:i386 libthai0:i386
  libxcb-render0:i386 libxcb-shm0:i386 libxft2:i386
Suggested packages:
  librsvg2-common:i386 gvfs:i386 libjasper-runtime:i386 ttf-baekmuk:i386
  ttf-arphic-gbsn00lp:i386 ttf-arphic-bsmi00lp:i386 ttf-arphic-gkai00mp:i386
  ttf-arphic-bkai00mp:i386
The following NEW packages will be installed:
  libatk1.0-0:i386 libcairo2:i386 libdatrie1:i386 libgdk-pixbuf2.0-0:i386
  libgtk2.0-0:i386 libjasper1:i386 libpango1.0-0:i386 libpixman-1-0:i386
  libthai0:i386 libxcb-render0:i386 libxcb-shm0:i386 libxft2:i386
0 upgraded, 12 newly installed, 0 to remove and 3 not upgraded.
Need to get 4,280 kB of archives.
After this operation, 11.1 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise/main libatk1.0-0 i386 2.4.0-0ubuntu1 [58.7 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise/main libpixman-1-0 i386 0.24.4-1 [243 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libxcb-render0 i386 1.8.1-1ubuntu0.2 [14.2 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libxcb-shm0 i386 1.8.1-1ubuntu0.2 [5,696 B]
Get:5 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libcairo2 i386 1.10.2-6.1ubuntu3 [490 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ precise/main libdatrie1 i386 0.2.5-3 [16.9 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ precise/main libjasper1 i386 1.900.1-13 [153 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ precise/main libgdk-pixbuf2.0-0 i386 2.26.1-1 [194 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ precise/main libthai0 i386 0.1.16-3 [20.2 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ precise/main libxft2 i386 2.2.0-3ubuntu2 [42.4 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libpango1.0-0 i386 1.30.0-0ubuntu3.1 [361 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ precise/main libgtk2.0-0 i386 2.24.10-0ubuntu6 [2,681 kB]
Fetched 4,280 kB in 5s (733 kB/s)         
Selecting previously unselected package libatk1.0-0:i386.
(Reading database ... 212935 files and directories currently installed.)
Unpacking libatk1.0-0:i386 (from .../libatk1.0-0_2.4.0-0ubuntu1_i386.deb) ...
Selecting previously unselected package libpixman-1-0:i386.
Unpacking libpixman-1-0:i386 (from .../libpixman-1-0_0.24.4-1_i386.deb) ...
Selecting previously unselected package libxcb-render0:i386.
Unpacking libxcb-render0:i386 (from .../libxcb-render0_1.8.1-1ubuntu0.2_i386.deb) ...
Selecting previously unselected package libxcb-shm0:i386.
Unpacking libxcb-shm0:i386 (from .../libxcb-shm0_1.8.1-1ubuntu0.2_i386.deb) ...
Selecting previously unselected package libcairo2:i386.
Unpacking libcairo2:i386 (from .../libcairo2_1.10.2-6.1ubuntu3_i386.deb) ...
Selecting previously unselected package libdatrie1:i386.
Unpacking libdatrie1:i386 (from .../libdatrie1_0.2.5-3_i386.deb) ...
Selecting previously unselected package libjasper1:i386.
Unpacking libjasper1:i386 (from .../libjasper1_1.900.1-13_i386.deb) ...
Selecting previously unselected package libgdk-pixbuf2.0-0:i386.
Unpacking libgdk-pixbuf2.0-0:i386 (from .../libgdk-pixbuf2.0-0_2.26.1-1_i386.deb) ...
Selecting previously unselected package libthai0:i386.
Unpacking libthai0:i386 (from .../libthai0_0.1.16-3_i386.deb) ...
Selecting previously unselected package libxft2:i386.
Unpacking libxft2:i386 (from .../libxft2_2.2.0-3ubuntu2_i386.deb) ...
Selecting previously unselected package libpango1.0-0:i386.
Unpacking libpango1.0-0:i386 (from .../libpango1.0-0_1.30.0-0ubuntu3.1_i386.deb) ...
Selecting previously unselected package libgtk2.0-0:i386.
Unpacking libgtk2.0-0:i386 (from .../libgtk2.0-0_2.24.10-0ubuntu6_i386.deb) ...
Setting up libatk1.0-0:i386 (2.4.0-0ubuntu1) ...
Setting up libpixman-1-0:i386 (0.24.4-1) ...
Setting up libxcb-render0:i386 (1.8.1-1ubuntu0.2) ...
Setting up libxcb-shm0:i386 (1.8.1-1ubuntu0.2) ...
Setting up libcairo2:i386 (1.10.2-6.1ubuntu3) ...
Setting up libdatrie1:i386 (0.2.5-3) ...
Setting up libjasper1:i386 (1.900.1-13) ...
Setting up libgdk-pixbuf2.0-0:i386 (2.26.1-1) ...
Setting up libthai0:i386 (0.1.16-3) ...
Setting up libxft2:i386 (2.2.0-3ubuntu2) ...
Setting up libpango1.0-0:i386 (1.30.0-0ubuntu3.1) ...
Setting up libgtk2.0-0:i386 (2.24.10-0ubuntu6) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
sozu@HP625:~$ personal
/usr/local/lib/personal/personal.bin: error while loading shared libraries: libidn.so.11: cannot open shared object file: No such file or directory
sozu@HP625:~$ 



```

Thanks for the output.  I don't need the output of the module installation (unless you have errors and can't install the modules).  I'll just need the error message you get when running the application.

Install these modules.  Some of them will already be installed:

```

$ sudo apt-get install libidn11
$ sudo apt-get install libidn11:i386
$ sudo apt-get install libcanberra-gtk-module
$ personal

```

Thanks again for the brevity consideration or only providing the ouput of the "personal" command unless you get errors when installing the modules.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by Niemil on 2013-11-12
Okey thanks :)

Hey, something happened now when I runned "personal" code ! The Bank ID window popped up! :) awesome
But there was some error after the personal too:
```
sozu@HP625:~$ personal

(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
Gtk-Message: Failed to load module "canberra-gtk-module"
`menu_proxy_module_load': /usr/local/lib/personal/personal.bin: undefined symbol: menu_proxy_module_load


(personal.bin:15811): Gtk-WARNING **: Failed to load type module: (null)


`menu_proxy_module_load': /usr/local/lib/personal/personal.bin: undefined symbol: menu_proxy_module_load


(personal.bin:15811): Gtk-WARNING **: Failed to load type module: (null)


`menu_proxy_module_load': /usr/local/lib/personal/personal.bin: undefined symbol: menu_proxy_module_load


(personal.bin:15811): Gtk-WARNING **: Failed to load type module: (null)


`menu_proxy_module_load': /usr/local/lib/personal/personal.bin: undefined symbol: menu_proxy_module_load


(personal.bin:15811): Gtk-WARNING **: Failed to load type module: (null)


`menu_proxy_module_load': /usr/local/lib/personal/personal.bin: undefined symbol: menu_proxy_module_load


(personal.bin:15811): Gtk-WARNING **: Failed to load type module: (null)

```


However, I just logged into the bank again and went into order new bank ID, and there I didn't pass it again, it still said I got no Bank ID installed :S :/
And it's same for another site where it looks for bankID ( [https://auth1.arbetsformedlingen.se/BankID/VerifyBankIDServlet](https://auth1.arbetsformedlingen.se/BankID/VerifyBankIDServlet) ), there I getting error too saying I don't have it.

[edit]
I was away earlier, and well now I gotta head to bed, back in like 8 hours.

---

### Post by apollothethird on 2013-11-13
> **Niemil said:**
> Okey thanks :)

Hey, something happened now when I runned "personal" code ! The Bank ID window popped up! :) awesome
But there was some error after the personal too:
```
sozu@HP625:~$ personal

(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",


(personal.bin:15811): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
Gtk-Message: Failed to load module "canberra-gtk-module"
`menu_proxy_module_load': /usr/local/lib/personal/personal.bin: undefined symbol: menu_proxy_module_load


(personal.bin:15811): Gtk-WARNING **: Failed to load type module: (null)


`menu_proxy_module_load': /usr/local/lib/personal/personal.bin: undefined symbol: menu_proxy_module_load


(personal.bin:15811): Gtk-WARNING **: Failed to load type module: (null)


`menu_proxy_module_load': /usr/local/lib/personal/personal.bin: undefined symbol: menu_proxy_module_load


(personal.bin:15811): Gtk-WARNING **: Failed to load type module: (null)


`menu_proxy_module_load': /usr/local/lib/personal/personal.bin: undefined symbol: menu_proxy_module_load


(personal.bin:15811): Gtk-WARNING **: Failed to load type module: (null)


`menu_proxy_module_load': /usr/local/lib/personal/personal.bin: undefined symbol: menu_proxy_module_load


(personal.bin:15811): Gtk-WARNING **: Failed to load type module: (null)

```


However, I just logged into the bank again and went into order new bank ID, and there I didn't pass it again, it still said I got no Bank ID installed :S :/
And it's same for another site where it looks for bankID ( [https://auth1.arbetsformedlingen.se/BankID/VerifyBankIDServlet](https://auth1.arbetsformedlingen.se/BankID/VerifyBankIDServlet) ), there I getting error too saying I don't have it.

[edit]
I was away earlier, and well now I gotta head to bed, back in like 8 hours.

First be advised that most of the messages you see in the terminal when running a GUI from the terminal are not errors, they are status, information, and debugging messages.  GUI applications are normally run from a launcher where the user won't see those messages.

So, if you run BankID Security Application from Ubuntu's dash you won't see the distracting messages.

However at this point, a questionable problem I see is the missing "canberra-gtk-module" module.  You can fix that with:

```

$ sudo apt-get install libcanberra-gtk-module:i386

```

I don't think the theme warning message is very serious.  Some of them might have some significance.  I suggest contacting the BankID support team about the "no Bank ID installed" error.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")

---

