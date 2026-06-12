---
title: "Large File Support under Ubuntu 10.0.4"
date: 2011-09-12
forum: Server Platforms
---

### Post by libbrechtemmanuel on 2011-09-12
Hi all,

While copying a dvd with vobcopy i used the option -l to create one large .vob file of the dvd. The problem is that the file can't be created because there is no large file support.

Any idea how to enable large file support and fix this problem?

---

### Post by zackwasa on 2011-09-12
can you please tell us what type of partition are you copying to? Normally this should be enabled by default

---

### Post by ajgreeny on 2011-09-12
> **zackwasa said:**
> can you please tell us what type of partition are you copying to? Normally this should be enabled by default
+1
There is a 4GB limit for files in fat32.  Format the destination to ntfs and you should be OK.

---

### Post by libbrechtemmanuel on 2011-09-12
my filesystem is ext2. is there a file limit in size?

---

### Post by dtfinch on 2011-09-12
Seems like you're hitting a vobcopy limit, not a Linux/filesystem limit. Did you try the "-l" option with vobcopy?

---

### Post by mikewhatever on 2011-09-12
You must have meant 10.0.0.0.0.4.;)

---

### Post by libbrechtemmanuel on 2011-09-13
> **dtfinch said:**
> Seems like you're hitting a vobcopy limit, not a Linux/filesystem limit. Did you try the "-l" option with vobcopy?

yes i tried the -l option but it says that there is a limit of file in size

---

### Post by SecretCode on 2011-09-13
Confirm your OS level...
```
uname -a
```

And check the shell limits ...
```
ulimit -a
```

Can you create a large file using another command?
```
dd if=/dev/zero of=/path/to/file bs=1048576 count=5120
```
- this will create a 5GiB file (took over 3 minutes on my system but that's with other things running)
- make sure you choose a /path/to/file on the file system you're trying to use with vobcopy, and a file that does not already exist!

---

### Post by dtfinch on 2011-09-13
What does it say exactly?

---

### Post by libbrechtemmanuel on 2011-09-14
> **dtfinch said:**
> Seems like you're hitting a vobcopy limit, not a  Linux/filesystem limit. Did you try the "-l" option with  vobcopy?

> **SecretCode said:**
> Confirm your OS level...
```
uname -a
```And check the shell limits ...
```
ulimit -a
```Can you create a large file using another command?
```
dd if=/dev/zero of=/path/to/file bs=1048576 count=5120
```- this will create a 5GiB file (took over 3 minutes on my system but that's with other things running)
- make sure you choose a /path/to/file on the file system you're trying to use with vobcopy, and a file that does not already exist!

i tried to create a large file, so it seems that i'm hitting a vobcopy limit and nog a filesystem limit.

I did try the -l option with vobcopy but i won't work.

Is this a bug in vobcopy? Are there any alternatives for vobcopy? (command line backup of a dvd)

---

### Post by libbrechtemmanuel on 2011-09-14
> **dtfinch said:**
> What does it say exactly?

[Info] DVD-name: DAVINCI_CODE

[Info] Outputting to /home/user/dvd/DAVINCI_CODE1-1.vob
  16MB of 6477MB written (0 %)
[Error] Write() error
[Error] It's possible that you try to write files
[Error] greater than 2GB to filesystem which
[Error] doesn't support it? (try without -l)
[Error] Error: Bad address

---

### Post by SecretCode on 2011-09-14
Assuming that you definitely have enough free space at that location :) ...

It looks like it's failing immediately (at 0%). And the 2GB error message is misleading. 

A [google of vobcopy "Error: Bad address"]("http://www.google.com/search?q=vobcopy+%22error%3A+bad+address%22") turns up lots of people having issues like this, with various possible causes (copy protection, multiple camera angles). Looks like you might need to try another tool.

---

### Post by libbrechtemmanuel on 2011-09-16
> **SecretCode said:**
> Assuming that you definitely have enough free space at that location :) ...

It looks like it's failing immediately (at 0%). And the 2GB error message is misleading. 

A [google of vobcopy "Error: Bad address"]("http://www.google.com/search?q=vobcopy+%22error%3A+bad+address%22") turns up lots of people having issues like this, with various possible causes (copy protection, multiple camera angles). Looks like you might need to try another tool.

thanks for the reply. I don't think that it can be an issue with a copy protection though (i installed libcss and libdvdread)

i tried multiple dvd's, some do work, others don't

any suggestion for another tool?

---

### Post by hansdown on 2011-09-16
Hi libbrechtemmanuel.

SecretCode is probably correct.

Try installing

```
dvdrip
```

It "may" do the job.

Also,

```
dvd95
```

---

### Post by libbrechtemmanuel on 2011-09-16
> **hansdown said:**
> Hi libbrechtemmanuel.

SecretCode is probably correct.

Try installing

```
dvdrip
```It "may" do the job.

Also,

```
dvd95
```

Hmmm thanks

Are those command line tools?

Because I want to put everything in a script. :)

---

### Post by hansdown on 2011-09-16
> **libbrechtemmanuel said:**
> Hmmm thanks

Are those command line tools?

Because I want to put everything in a script. :)

Those are the names of the apps.

Use 

```
sudo-apt-get-install"name of app'.
```

I should point out, that these apps have a gui.

---

### Post by libbrechtemmanuel on 2011-09-16
> **hansdown said:**
> Those are the names of the apps.

Use 

```
sudo-apt-get-install"name of app'.
```I should point out, that these apps have a gui.

Are there any tools that i can use in the command line?

---

### Post by hansdown on 2011-09-17
Sorry, libbrechtemmanuel.

I know you asked for a command line tool.

Are you running 10.04 in a virtual machine?

---

### Post by SecretCode on 2011-09-17
No experience of using them, but dvdbackup and mplayer are command line tools which look like they can do the job.

---

### Post by libbrechtemmanuel on 2011-09-20
> **hansdown said:**
> Sorry, libbrechtemmanuel.

I know you asked for a command line tool.

Are you running 10.04 in a virtual machine?

No problem. :)

It is not running in a virtual machine.

> **SecretCode said:**
> No experience of using them, but dvdbackup  and mplayer are command line tools which look like they can do the  job.

Thanks for the reply, though I tried both of those tools but there are not 100% reliable.

---

