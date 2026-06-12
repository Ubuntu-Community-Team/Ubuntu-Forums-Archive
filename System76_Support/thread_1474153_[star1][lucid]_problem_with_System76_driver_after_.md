---
title: "[star1][lucid] problem with System76 driver after `do-release-upgrade`"
date: 2010-05-05
forum: System76 Support
---

### Post by tlroche on 2010-05-05
**summary:** After upgrading a starling 9.10 -> 10.04 using `do-release-upgrade` I can't run the System76 driver. How to fix?

**details:**

Today I upgraded a starling from karmic to lucid via

```
$ sudo aptitude update
$ sudo do-release-upgrade
$ sudo aptitude update
```

I dunno if this is not The Way To Do This, but I have run `do-release-upgrade` successfully a lot on servers (going back several releases). (FWIW most of my linux experience is shelling into servers.) `do-release-upgrade` completed successfully, so I restarted and updated (just to be safe). All seemed well: I reconnected to my router via the wire (on which I upgraded), then removed the wire, and it went to wireless. I was also able to suspend/resume, but have no hibernation UI. I then tried to reinstall the System76 driver:

[LIST=1]
[*]I 2-clicked System>Administration>System76 Driver and got dialog=Unsupported
```
This driver is designed for System76 machines running
Ubuntu versions 6.06 through 9.10. If you have a System76
machine running one of the above Ubuntu versions please file
a bug report at https://launchpad.net/system76

```
[*]I closed that, then ran System>Administration>Software Sources, choosing tab=Other Software. There was no record for
```
http://planet76.com/repositories/ ./

```
so I hit button=Add and added the line
```
deb http://planet76.com/repositories/ ./

```
then hit button=Add Source. The resulting record's box was checked in the resulting (main Software Sources) dialog, so I hit button=Reload (in resulting dialog), but got an untitled warning dialog
```
An error occurred
The following details are provided:

W: GPG error: http://planet76.com/repositories/ ./ Release: The following signatures
couldn't be verified because the public key is not available:
NO_PUBKEY 176A5C84ED67C9ED

```
[/LIST]

For the helluvit I tried rerunning the System 76 driver but got the same error as previous. What do I need to do to make the System76 driver play nice?

TIA, Tom Roche <Tom_Roche@pobox.com>

---

### Post by juelze on 2010-05-05
> **tlroche said:**
> **summary:** After upgrading a starling 9.10 -> 10.04 using `do-release-upgrade` I can't run the System76 driver. How to fix?

**details:**

Today I upgraded a starling from karmic to lucid via

```
$ sudo aptitude update
$ sudo do-release-upgrade
$ sudo aptitude update
```

I dunno if this is not The Way To Do This, but I have run `do-release-upgrade` successfully a lot on servers (going back several releases). (FWIW most of my linux experience is shelling into servers.) `do-release-upgrade` completed successfully, so I restarted and updated (just to be safe). All seemed well: I reconnected to my router via the wire (on which I upgraded), then removed the wire, and it went to wireless. I was also able to suspend/resume, but have no hibernation UI. I then tried to reinstall the System76 driver:

[LIST=1]
[*]I 2-clicked System>Administration>System76 Driver and got dialog=Unsupported
```
This driver is designed for System76 machines running
Ubuntu versions 6.06 through 9.10. If you have a System76
machine running one of the above Ubuntu versions please file
a bug report at https://launchpad.net/system76

```
[*]I closed that, then ran System>Administration>Software Sources, choosing tab=Other Software. There was no record for
```
http://planet76.com/repositories/ ./

```
so I hit button=Add and added the line
```
deb http://planet76.com/repositories/ ./

```
then hit button=Add Source. The resulting record's box was checked in the resulting (main Software Sources) dialog, so I hit button=Reload (in resulting dialog), but got an untitled warning dialog
```
An error occurred
The following details are provided:

W: GPG error: http://planet76.com/repositories/ ./ Release: The following signatures
couldn't be verified because the public key is not available:
NO_PUBKEY 176A5C84ED67C9ED

```
[/LIST]

For the helluvit I tried rerunning the System 76 driver but got the same error as previous. What do I need to do to make the System76 driver play nice?

TIA, Tom Roche <Tom_Roche@pobox.com>

Welcome to the club.

---

### Post by |Porsche on 2010-05-05
[http://knowledge76.com/index.php/LucidUpgrade](http://knowledge76.com/index.php/LucidUpgrade)

Read the "Run System76 Driver" Section. 

Download the latest one manually. You should be good to go after that.

---

### Post by juelze on 2010-05-06
> **|Porsche said:**
> [http://knowledge76.com/index.php/LucidUpgrade](http://knowledge76.com/index.php/LucidUpgrade)

Read the "Run System76 Driver" Section. 

Download the latest one manually. You should be good to go after that.

That's how I did mine and it still doesn't work.

---

### Post by tlroche on 2010-05-06
> **|Porsche said:**
> [http://knowledge76.com/index.php/LucidUpgrade](http://knowledge76.com/index.php/LucidUpgrade)
Read the "Run System76 Driver" Section.

I did, but I thought I was blocked by the repository problem. Per your suggestion I went ahead and {downloaded,installed,ran} the driver, and the starling seems happy.

For future use, I updated the wiki page to

[LIST]
[*]clarify the 3 steps of re-enabling the driver repository, download/installing the driver, and run the driver
[*]note that one can fail to re-enable the driver repository, but still download/install/run the driver
[/LIST]

I'd mark this [SOLVED] but I still believe there's a problem with the System76 driver repository.

thanks, Tom Roche <Tom_Roche@pobox.com>

---

### Post by tlroche on 2010-05-06
> **|Porsche said:**
> [http://knowledge76.com/index.php/LucidUpgrade](http://knowledge76.com/index.php/LucidUpgrade)
Read the "Run System76 Driver" Section.

> **juelze said:**
> That's how I did mine and it still doesn't work.

Here's what worked for me:

[LIST]
[*]in terminal, ran this bash scriptlet
```
S76_URI="http://planet76.com/repositories/system76-driver-2.4.8.deb"
S76_DIR="/tmp"
S76_FP="${S76_DIR}/$(basename ${S76_URI})"
curl -o ${S76_FP} ${S76_URI}
sudo dpkg -i ${S76_FP}

```to download/install the driver.
[*][ran the driver]("http://knowledge76.com/index.php/LucidUpgrade#Run_System76_Driver") as described in the newly-improved (if I do say so myself) wiki page
[*]restarted the starling
[*]after restart, checked that the repository is re-enabled.
[/LIST]

---

