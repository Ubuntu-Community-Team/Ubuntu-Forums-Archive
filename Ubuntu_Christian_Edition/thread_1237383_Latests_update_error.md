---
title: "Latests update error"
date: 2009-08-11
forum: Ubuntu Christian Edition
---

### Post by shane2peru on 2009-08-11
I updated today, and there were U-CE updates.  I updated everything and got these errors:

```

Errors were encountered while processing:
 ubuntu-ce-sounds
 ubuntu-ce
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up ubuntu-ce-sounds (0.2) ...
Failed to access configuration source(s): Couldn't resolve address for configuration source: Couldn't resolve address for configuration source: Bad address `xml::/home/lost+found/.gconf': `+' is an invalid character in a configuration storage address
dpkg: error processing ubuntu-ce-sounds (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-ce:
 ubuntu-ce depends on ubuntu-ce-sounds; however:
  Package ubuntu-ce-sounds is not configured yet.
dpkg: error processing ubuntu-ce (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ubuntu-ce-sounds
 ubuntu-ce

```

I assume it is probably the sounds config thing not setting up correctly or something.  I don't think it is a major problem, but did want to let you know about it.

Shane

---

### Post by arky on 2009-08-11
Fill a bug report with 'ubuntu-bug ubuntu-ce'

---

### Post by shane2peru on 2009-08-11
> **arky said:**
> Fill a bug report with 'ubuntu-bug ubuntu-ce'

Yeah, I thought of that afterwards.  Where do I find that?  Is that local on my system, or on the web?  

Shane

---

### Post by arky on 2009-08-11
ubuntu-bug tool is provided by 'apport' package.

---

### Post by stlsaint on 2009-08-11
do you have the ce repo's in your sources list?

---

### Post by shane2peru on 2009-08-11
> **arky said:**
> ubuntu-bug tool is provided by 'apport' package.

Hmm, ok, I tried that, but it didn't work, says the package is not an official Ubuntu package.  Also can you reference a how to for this?  I updated my laptop and it had the same problem and I just clicked on the report the problem thing and it said apport, of which of course I recognized from this thread.  

> **stlsaint said:**
> do you have the ce repo's in your sources list?


Hmm, yes, I have the Ubuntu CE repos in my list, that is how I got the update.  Maybe mine aren't right?  Oh, probably if you didn't see this error, it is because you aren't using Ubuntu-CE-64  the 64bit version.  That could be.

Shane

---

### Post by david_kt on 2009-08-11
> **arky said:**
> Fill a bug report with 'ubuntu-bug ubuntu-ce'

No, do not report to ubuntu-bug, just report it to me.

Could you try to use command line and post the error here?

DK

---

### Post by shane2peru on 2009-08-11
Here is the error I get when I try to upgrade:
```

sudo apt-get upgrade
[sudo] password for shane: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up ubuntu-ce-sounds (0.2) ...
Failed to access configuration source(s): Couldn't resolve address for configuration source: Couldn't resolve address for configuration source: Bad address `xml::/home/lost+found/.gconf': `+' is an invalid character in a configuration storage address
dpkg: error processing ubuntu-ce-sounds (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-ce:
 ubuntu-ce depends on ubuntu-ce-sounds; however:
  Package ubuntu-ce-sounds is not configured yet.
dpkg: error processing ubuntu-ce (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 ubuntu-ce-sounds
 ubuntu-ce
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Like I said, it doesn't seem to be a major problem, I have a working system with no real problems.  

Shane

PS.  I guess I probably could have just pm'ed you.  That may have been better.  Next time.

---

### Post by david_kt on 2009-08-11
> **shane2peru said:**
> Here is the error I get when I try to upgrade:
```

sudo apt-get upgrade
[sudo] password for shane: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up ubuntu-ce-sounds (0.2) ...
Failed to access configuration source(s): Couldn't resolve address for configuration source: Couldn't resolve address for configuration source: Bad address `xml::/home/lost+found/.gconf': `+' is an invalid character in a configuration storage address
dpkg: error processing ubuntu-ce-sounds (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-ce:
 ubuntu-ce depends on ubuntu-ce-sounds; however:
  Package ubuntu-ce-sounds is not configured yet.
dpkg: error processing ubuntu-ce (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 ubuntu-ce-sounds
 ubuntu-ce
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Like I said, it doesn't seem to be a major problem, I have a working system with no real problems.  

Shane

PS.  I guess I probably could have just pm'ed you.  That may have been better.  Next time.

No, it is real problem actually. I tried to force user to use ubuntu ce sound when first time installing it. But looks like I make some error in the script. Actually user need to select the sound manually after installing it. If I could not repair the script, I will just abort it.

I will take a look at the error and see whether it is possible to rectify it.

DK

---

### Post by david_kt on 2009-08-12
Shane,
Could you download manually below file:

[http://ubuntuce.com/repos/Ubuntu_CE/jaunty_i386/ubuntu-ce-sounds_0.3_all.deb](http://ubuntuce.com/repos/Ubuntu_CE/jaunty_i386/ubuntu-ce-sounds_0.3_all.deb)

and then install it. Please let me know if there is still an error there.

If it is ok, run sudo apt-get upgrade again it should be ok now.

If everything ok, I will update the repository.
Thank you for your feedback.

This bug will appear only to those have home directory in separate partition. I have included a work around in the 0.3 release.

DK

---

### Post by shane2peru on 2009-08-12
> **david_kt said:**
> Shane,
Could you download manually below file:

[http://ubuntuce.com/repos/Ubuntu_CE/jaunty_i386/ubuntu-ce-sounds_0.3_all.deb](http://ubuntuce.com/repos/Ubuntu_CE/jaunty_i386/ubuntu-ce-sounds_0.3_all.deb)

and then install it. Please let me know if there is still an error there.

If it is ok, run sudo apt-get upgrade again it should be ok now.

If everything ok, I will update the repository.
Thank you for your feedback.

This bug will appear only to those have home directory in separate partition. I have included a work around in the 0.3 release.

DK


Yes, that worked like a charm.  And you hit the nail on the head, I do have my home on a separate partition.  Makes for very easy upgrades. :)   Thanks for the fix.

Shane

---

### Post by oneinch on 2009-08-12
I have been experiencing the same error on the ubuntuce-sounds. I downloaded the *.deb David and the install of that went fine. It complained about there being an older version in the repo and that you should use the one in the repo because it would be more supported or something similar to that. But it still installed. And sudo apt-get upgrade went smoothly too.

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up ubuntu-ce (1.6) ...
oneinch@CHRiSTBoX:~$

```

---

### Post by david_kt on 2009-08-12
> **oneinch said:**
> I have been experiencing the same error on the ubuntuce-sounds. I downloaded the *.deb David and the install of that went fine. It complained about there being an older version in the repo and that you should use the one in the repo because it would be more supported or something similar to that. But it still installed. And sudo apt-get upgrade went smoothly too.

I have upgraded the repository to ubuntu-ce-sound 0.3.

DK

---

