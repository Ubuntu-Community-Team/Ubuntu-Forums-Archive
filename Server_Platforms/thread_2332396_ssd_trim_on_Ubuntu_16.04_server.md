---
title: "ssd trim on Ubuntu 16.04 server"
date: 2016-07-31
forum: Server Platforms
---

### Post by bobwdn on 2016-07-31
I have a sftp server that I am running that is installed on a Transcend model TS32GSSD340. It supports TRIM.```
ad*****x@d***03:~$ sudo hdparm -I /dev/sda }| grep "TRIM supported"
}: No such file or directory
	   *	Data Set Management TRIM supported (limit 8 blocks)
```
I setup (I noticed this file content is different from previous v14.04 version I had notes from)```
ad*****x@d***03:~$ sudo cat /etc/cron.weekly/fstrim
#!/bin/sh
# trim all mounted file systems which support it
/sbin/fstrim --all --no-model-check || true
```

And received this forwarded complaint root email:  ```
/etc/cron.weekly/fstrim:
/sbin/fstrim: [COLOR="#FF0000"]unrecognized option '--no-model-check'
[/COLOR]
Usage:
 fstrim [options] <mount point>

Discard unused blocks on a mounted filesystem.

Options:
 -a, --all           trim all mounted filesystems that are supported
 -o, --offset <num>  the offset in bytes to start discarding from
 -l, --length <num>  the number of bytes to discard
 -m, --minimum <num> the minimum extent length to discard
 -v, --verbose       print number of discarded bytes

 -h, --help     display this help and exit
 -V, --version  output version information and exit

For more details see fstrim(8).
```

The man fstrim references nothing about --no-model-check option.

Has trim support for Transcend ssd changed with version 16.04LTS?

---

### Post by MAFoElffen on 2016-08-01
Moved to server section for better exposure.

---

### Post by bobwdn on 2016-08-14
MafoElffen thanks for moving my thread to the proper forum. 

This morning I received an email from the machine that this is still going on. So, I ask again, > Has trim support for Transcend ssd changed with version 16.04LTS? 

This is a problem because if I run 'fstrim' manually it "trims" properly therefore it is not functioning properly as a crontab job. This inability to run automatically could become a problem.

Any help, please?

---

### Post by MAFoElffen on 2016-08-14
> **bobwdn said:**
> MafoElffen thanks for moving my thread to the proper forum. 

This morning I received an email from the machine that this is still going on. So, I ask again, 

This is a problem because if I run 'fstrim' manually it "trims" properly therefore it is not functioning properly as a crontab job. This inability to run automatically could become a problem.

Any help, please?
Thought that someone would surely jump in and help, but.. no matters:

Re:
[http://manpages.ubuntu.com/manpages/trusty/en/man8/fstrim-all.8.html](http://manpages.ubuntu.com/manpages/trusty/en/man8/fstrim-all.8.html)
[http://manpages.ubuntu.com/manpages/xenial/man8/fstrim.8.html](http://manpages.ubuntu.com/manpages/xenial/man8/fstrim.8.html)
[ftp://ftp.kernel.org/pub/linux/utils/util-linux/](ftp://ftp.kernel.org/pub/linux/utils/util-linux/)

I went through the man pages on fstrim and fstrim-all. I went through the change logs and release notes for linux-utils, which is the package where the utility fstrim is from. The release notes had the changes... so had to go through each...
```

I compiled changes on fstrim since linux-util version 2.24, from the doc's at kernel.org

2.24.1: fstrim(1): 
[COLOR=#000000]  - add --all to discard all filesystem  [Karel Zak]; [/COLOR][COLOR=#000000]- cleanup usage()  [Karel Zak]
[/COLOR][COLOR=#000000]2.24.2: fstrim(1):
[/COLOR][COLOR=#000000]  - add hint to man page  [Karel Zak][/COLOR][COLOR=#000000]
[/COLOR]2.25: [COLOR=#000000]fstrim(1):
  [/COLOR][COLOR=#000000]- supports new option --all to discard all filesystem on devices that supports [/COLOR][COLOR=#000000]TRIM operation.
2.27: fstrim(1):
[/COLOR][COLOR=#000000]- close dir before exit [coverity scan]  [Karel Zak]
  [/COLOR][COLOR=#000000]- de-duplicate by mount source too  [Karel Zak]
2.28: fstrim(1):[/COLOR][COLOR=#000000] 
  - use mountpoint, not device  [Andreas Henriksson]
 [/COLOR][COLOR=#000000] - a few tiny tweaks of the man page  [Benno Schulenberg]
[/COLOR][COLOR=#000000]  - add reference to blkdiscard  [Karel Zak]
[/COLOR]
```[COLOR=#000000]
But one thing I noticed in all that research and in the manpages... 

Your thrown errors: 
"[/COLOR]--no-model-check[COLOR=#000000]" is not a valid option for fstrim. [/COLOR]

[COLOR=#000000]Curious why you are passing the output piped as Boolean true? It has valid return codes to indicate it's run-time disposition.[/COLOR]

---

