---
title: "no more updating possible due to error in synaptic"
date: 2006-11-16
forum: Repositories &amp; Backports
---

### Post by rjz35 on 2006-11-16
When messing around with the installation of a conexant modem driver the following occured.
Synaptic error: The package conexant needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

After this i started looking in the forums for people with the same problem, found this instruction;

"sudo dpkg --force-remove-reinstreq --purge conexant"

The following error occurred;

"dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 117993 files and directories currently installed.)
Removing conexant ...
ERROR: Module hsfserial does not exist in /proc/modules
ERROR: Module hsfengine does not exist in /proc/modules
ERROR: Module hsfbasic2 does not exist in /proc/modules
ERROR: Module hsfosspec does not exist in /proc/modules
dpkg: error processing conexant (--purge):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 conexant"

Pls help me, i'm not able to update anymore or install anything and i do not want to install edgy again.

---

### Post by Joe_CoT on 2006-11-16
:-/ that's not good....
You could try touching those missing files so it can remove them

or running it with --force-all

or waiting to see if someone has a better solution (i'd recommend touching over forcing myself) :???:

---

### Post by rjz35 on 2006-11-17
> **Joe_CoT said:**
> :-/ that's not good....
You could try touching those missing files so it can remove them

or running it with --force-all

or waiting to see if someone has a better solution (i'd recommend touching over forcing myself) :???:

Joe,

thanks for your reply, one question though, what do you mean with "touching" do i need to create the files?

---

### Post by Joe_CoT on 2006-11-17
touch is a commmand. It means to create an empty file. So yes, just create them.

---

