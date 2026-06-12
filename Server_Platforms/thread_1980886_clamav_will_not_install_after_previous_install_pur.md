---
title: "clamav will not install after previous install purged"
date: 2012-05-15
forum: Server Platforms
---

### Post by cornflake000 on 2012-05-15
I'm kind of stumped on a clamav reinstall.  I have been running clamav on this mail server for a couple of years using clamav-daemon.  I decided to upgrade it; I purged it using apt-get.  After doing so, it would not install without dependency errors in freshclam.  I am running Lynx server and the repository version is clamav 0.96.5+dfsg-1ubuntu1.10.04.3. The clamav site said something about making sure there are no old libclamav.so files that conflict and that the init.d files were manually removed... so.... I deleted those and did another purge and reinstall.  Now, the new clamav install is looking for the old libclamav.so.6 and it is not there and it will not reinstall it.

There is this old problem with libclamav.so.6 not being found which is solved by ldconfig but this is not the issue as libclamav.so.6 does not exist on this server.

What I gather is that there are other leftover files or lib's that I don't know about or that do not un-install in the normal way and the new install expects them to already be there and doesn't reinstall libclamav.so.6 or it's new counter part.

The question... How can I get clamav to reinstall?  How can I totally remove all remnants of it as if it was never installed?  It's totally borked now and simply will not finish the install of freshclam.  I am not new to Linux or Ubuntu and have a fair amount of experience but this is weird.

Thanks!

---

### Post by wilee-nilee on 2012-05-16
Run a search of clamav stuff on your system and remove every remnant, a purge does not always remove every thing.

---

### Post by cornflake000 on 2012-05-16
Thanks willee...

You got me thinking, and I decided to go backwards from your suggestion and I looked up all the files listed for the clamav packages on the packages.ubuntu site.  I found that the libclamav.so.6 in question was part of another package libclamav6 that was not installing.  When I looked for the location of files associated with libclamav6 I found it was already installed but now of course missing libclamav.so.6.  I also found libclamav5 and libclamav2 just sitting there.  So I deleted the 5 and 2 version and un-unstalled the 6 version -f due to dependency errors and purged everything again.  Then I installed clamav, clamav-base, clamav-daemon, clamav-freshclam and added libclamav6.  BOOM... everything works!

Sorry to go on but I hate it when there is a question and the guy comes back and says, "oh, I fixed it... bye", and never tells how he did it.  Well, there we have it.

---

### Post by wilee-nilee on 2012-05-16
> **cornflake000 said:**
> Thanks willee...

You got me thinking, and I decided to go backwards from your suggestion and I looked up all the files listed for the clamav packages on the packages.ubuntu site.  I found that the libclamav.so.6 in question was part of another package libclamav6 that was not installing.  When I looked for the location of files associated with libclamav6 I found it was already installed but now of course missing libclamav.so.6.  I also found libclamav5 and libclamav2 just sitting there.  So I deleted the 5 and 2 version and un-unstalled the 6 version -f due to dependency errors and purged everything again.  Then I installed clamav, clamav-base, clamav-daemon, clamav-freshclam and added libclamav6.  BOOM... everything works!

Sorry to go on but I hate it when there is a question and the guy comes back and says, "oh, I fixed it... bye", and never tells how he did it.  Well, there we have it.

Cool, that was a very logical way to find all the files and do what needed to be done. :)

---

