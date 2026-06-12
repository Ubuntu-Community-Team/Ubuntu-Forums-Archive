---
title: "Please test: Thunderbird and Firefox install scripts v. 3.1.0"
date: 2007-04-27
forum: Ubuntuzilla
---

### Post by nanotube on 2007-04-27
***EDIT: the 'testing' phase for this version has completed. these are now live. if you have any problems/comments on the scripts, just post a thread in the main ubuntuzilla forum.

Please note that if you simply want to use the "stable" version of the script, get it from our website:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla)
This version is for testers only.

Here is a new version of the firefox and thunderbird install scripts. the new features of this version are:

[LIST]
[*]tries several keyservers, each a couple of times, when retrieving gpg key
[*]catches verification failure, offers option to delete downloaded files and try again.
[*]set download timeout to 60 secs (from default 15 min)
[*]print script version in startup message (to facilitate troubleshooting)
[/LIST]

these "robustness" add-ons have been prompted by [this post (thanks)]("http://ubuntuforums.org/showpost.php?p=2548462&postcount=20")

if these mods work, they will of course be ported over to the thunderbird script as well.

scripts attached.

edit: threw the mods over to the thunderbird script as well, after i did some testing myself. but i'd like to get some more feedback before sending this version live to the main site.

---

### Post by aysiu on 2007-05-01
nanotube, before I start testing these, how exactly am I testing this?

For example, how would I know if it tries several key servers or not? How do I make the verification fail so that I can see if it offers an option to delete downloaded files and try again? How do I make the download take longer than 60 seconds?

By the way, is it conceivable that users on dial-up might be using this script, in which case 60 seconds might be too low a timeout time?

---

### Post by aysiu on 2007-05-01
In the meantime, I've tested both scripts (*install* and *remove* for reach) just to see if they're functional in normal situations--they are.

---

### Post by nanotube on 2007-05-01
> **aysiu said:**
> nanotube, before I start testing these, how exactly am I testing this?

For example, how would I know if it tries several key servers or not? How do I make the verification fail so that I can see if it offers an option to delete downloaded files and try again? How do I make the download take longer than 60 seconds?

By the way, is it conceivable that users on dial-up might be using this script, in which case 60 seconds might be too low a timeout time?

hey aysiu. this is where you get creative. :)
at the very least, i'd like to get confirmation that it runs through without any problems. (edit: ah, i see you've already done that. cool :) ).

for extra test scenarios, this is what i did:
# i edited the keyserver list to include some nonexistent servers, to give it a chance to fail and move on to another keyserver.
# i made the verification run without a tar.gz present, which of course resulted in verification failure, and gave it a chance to do its thing
# i did not test the timeout thing, but conceivably what you could do is pull the network plug out for 60 secs in the middle of the download, and see if it attempts to restart. but it really does not require extra testing, since it's just a built-in feature of wget - it's not something i rigged up with the script.

about the 60sec timetout: it is not the total download time, but the time during which you receive no data. so, if your download is "stalled" and you receive no data for 60 seconds, it kills that connection, and starts another, continuing from where it left off. so even if you are on dialup, if you receive no data for 60 seconds, that's a pretty good indication that the download has stalled out. 
(from the wget manpage:
```
--read-timeout=seconds
           Set the read (and write) timeout to seconds seconds.  The &#8216;&#8216;time&#8217;&#8217; of this timeout
           refers idle time: if, at any point in the download, no data is received for more
           than the specified number of seconds, reading fails and the download is restarted.
           This option does not directly affect the duration of the entire download.
```
)

---

### Post by aysiu on 2007-05-01
Okay, to clarify a bit... > **nanotube said:**
> 
for extra test scenarios, this is what i did:
# i edited the keyserver list to include some nonexistent servers, to give it a chance to fail and move on to another keyserver. I don't really know much about key server lists. Where do I find them? What would be a good non-existent one to try?
> # i made the verification run without a tar.gz present, which of course resulted in verification failure, and gave it a chance to do its thing So while the script is running, delete the .tar.gz before the script does? > # i did not test the timeout thing, but conceivably what you could do is pull the network plug out for 60 secs in the middle of the download, and see if it attempts to restart. but it really does not require extra testing, since it's just a built-in feature of wget - it's not something i rigged up with the script. Thanks for explaining that. In that case, 60 seconds is a bit too generous, but that's probably good to be on the safe side.

---

### Post by nanotube on 2007-05-01
> **aysiu said:**
> Okay, to clarify a bit...  I don't really know much about key server lists. Where do I find them? What would be a good non-existent one to try?

the keyserver list is in the script itself, stored in PGP_KEYSERVERS variable. so just scroll down til you see it (or ctl-f).
a good nonexistent one to try? something like "blablabla.nthoeurcd.com" comes to mind. :) in other words, just make something up.
when you edit the list, make note of the format of the list, and keep all the spaces, etc. 

> 
 So while the script is running, delete the .tar.gz before the script does?  

yea, it will download the tar.gz, and then it will ask you, do you wanna verify the gpg sig? so, while it's waiting for your answer, you have plenty of time to delete the .tar.gz - or even more sneaky, to hexedit it and just change one bit of it - that would really test how good this gpg signature verification is against corrupt downloads and stuff.

> Thanks for explaining that. In that case, 60 seconds is a bit too generous, but that's probably good to be on the safe side.

heh yea, i figure most people can sit through 60 seconds of idle time without too much trouble - in the unlikely case that it materializes at all. :)

---

### Post by aysiu on 2007-05-01
Okay. I'll try it out.

---

### Post by aysiu on 2007-05-01
Some success: ```
Note that if you have never used gpg before on this system, and this is your first time running this script, there may be a delay of about a minute during the generation of a gpg keypair. This is normal and expected behavior.

gpg: requesting key 0E3606D9 from hkp server lalalal.pgp.net
?: lalalal.pgp.net: Host not found
gpgkeys: HTTP fetch error 7: couldn't connect: Success
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
Unable to retrieve Mozilla Software Releases Public key from lalalal.pgp.net. Trying again...
gpg: requesting key 0E3606D9 from hkp server lalalal.pgp.net
?: lalalal.pgp.net: Host not found
gpgkeys: HTTP fetch error 7: couldn't connect: Success
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
Unable to retrieve Mozilla Software Releases Public key from lalalal.pgp.net. Trying again...
gpg: requesting key 0E3606D9 from hkp server blahblahblah.mit.edu
?: blahblahblah.mit.edu: Host not found
gpgkeys: HTTP fetch error 7: couldn't connect: Success
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
Unable to retrieve Mozilla Software Releases Public key from blahblahblah.mit.edu. Trying again...
gpg: requesting key 0E3606D9 from hkp server blahblahblah.mit.edu
?: blahblahblah.mit.edu: Host not found
gpgkeys: HTTP fetch error 7: couldn't connect: Success
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
Unable to retrieve Mozilla Software Releases Public key from blahblahblah.mit.edu. Trying again...
gpg: requesting key 0E3606D9 from hkp server pgp.mit.edu
gpg: key 0E3606D9: "Mozilla Software Releases <releases@mozilla.org>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
Successfully retrieved Mozilla Software Releases Public key from pgp.mit.edu.


Verifying signature...
Note: do not worry about "untrusted key" warnings. That is normal behavior for newly imported keys.

gpg: Signature made Thu 05 Apr 2007 10:07:49 PM PDT using DSA key ID 0E3606D9
gpg: Good signature from "Mozilla Software Releases <releases@mozilla.org>"
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: F57F 372A 8C6D 4F55 72DE  C9B9 696E 3431 0E36 06D9

Extracting the downloaded Thunderbird archive


Removing installation file(s) to free up disk space


Linking launcher to new thunderbird

Adding `local diversion of /usr/bin/mozilla-thunderbird to /usr/bin/mozilla-thunderbird.ubuntu'

The new thunderbird version 2.0.0.0 has been installed successfully.
``` I'll post more as I test.

---

### Post by aysiu on 2007-05-01
More success: ```
Verifying signature...
Note: do not worry about "untrusted key" warnings. That is normal behavior for newly imported keys.

gpg: Signature made Thu 05 Apr 2007 10:07:49 PM PDT using DSA key ID 0E3606D9
gpg: BAD signature from "Mozilla Software Releases <releases@mozilla.org>"
Key verification failed. This is most likely due to a corrupt download. You should delete files 'thunderbird-2.0.0.0.tar.gz.asc' and 'thunderbird-2.0.0.0.tar.gz' and run the script again.

Would you like to delete those two files now? [y/n]? y
OK, deleting files and exiting.
``` I had unzipped the .tar.gz, deleted one file, and then rezipped it up.

---

### Post by aysiu on 2007-05-01
The Firefox one tested perfectly, too.

With Firefox, I made two of the keyservers gibberish (instead of just one), and I deleted the .tar.gz instead of altering it.

---

### Post by nanotube on 2007-05-01
cool, thanks a lot for the testing.
i will take these live, then. :)

---

### Post by aysiu on 2007-05-01
Great!

I really wish we had more testers.

I can test, and you can test, but it's impossible for two people to foresee every possible situation...

---

### Post by nanotube on 2007-05-01
> **aysiu said:**
> Great!

I really wish we had more testers.

I can test, and you can test, but it's impossible for two people to foresee every possible situation...

yea, i hear you. 
well, now that it's live, we will have a bunch of users testing it. :)

---

