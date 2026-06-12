---
title: "Lost User privileges to mount volumes from naultilus"
date: 2010-09-13
forum: Security
---

### Post by cludwig on 2010-09-13
I'm running 10.04 running daily updates.  A couple days back, I saw an update related to mounting volumes.  Not sure if this is what broke my system, but might be.

When attempting to mount a partition from nautilus, I get a message saying I do not have authorization.  It does not even ask for my password, just fails.  I tried running updates and this asks for my password and accepts it fine.  I opened disk utility from the menus and tried to mount the volume from there but also got the same permission denied, not authorized without even being asked for my password.  

I then ran gksu palimpsest.  I was asked for my password and was able to mount and unmount partitions from there.  However, when mounted, my applications and nautilus cannot access the data in the partitions mounted using gksu palimpsest.  In nautilus, I can navigate to /media/Data (the partition in question) but I get "THE FOLDER CONTENTS CANNOT BE DISPLAYED You do not have the permissions necessary to view the contents of "Data"."  When I open nautilus via gksu in the terminal, I do have full access to the partitions.

How do I get my privileges back for my user account.  I am the only user on the computer, and I have never set up a root account since my upgrade to 10.04 months ago.  I tried of course the Administration->Users and Groups menu, but I am not permitted to change the account type or open advanced settings.  I click the button, but nothing happens, not even a password request.  Running gksu admin-settings on the terminal allows me access.  My current settings are attached.

Any help getting my old access rights back would be appreciated (mount and unmount as a user with just a quick typing of my password).

-Chris

---

### Post by cludwig on 2010-09-13
Update:

...so I did the only obvious thing.  Using gksu users-admin, I changed my user account to administrator and saved.  I logged out and back in.  I still cannot mount volumes from nautilus (still not prompting for a password, and not giving me privileges by default).  I also cannot change user settings either.  I have to use gksu to be able to change settings in users-admin and palimpsest.

My latest user settings attached.  Full admin rights, but user privileges still busted...

When launching users-admin from the terminal, I get no error messages.  However, when launching it using gksu, it launches, but with the following warning in the terminal:

"cludwig@cludwig-laptop:~$ gksu users-admin

(users-admin:6720): Liboobs-WARNING **: There was an unknown error communicating asynchronously with the backends: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

Let me know if there are any logs I can collect for more info.

---

### Post by cludwig on 2010-09-13
SOLVED:

I noticed one of my two CPU's was running all out, but there were no processes which appeared to be responsible.  I tried to reboot, but when rebooting, it didn't actually reboot.  It just logged me off.  I tried to shutdown from the login screen but that too failed.  I logged back into the system and the ran "sudo shutdown -h now" in the terminal.  I was asked for my password and the computer rebooted normally.

When the computer came back up, I had all my normal user privileges.  Whatever started this, I have no idea, but forcing a shutdown with the above command was enough to fix it.  logging out did noting for me.  It had to be a real shutdown and boot back up.  I had already tried that but since I was temporarily lacking privileges, I couldn't actually restart unless I used the "sudo shutdown -h now" command in the terminal.

hope this info helps someone else if they find themselves in this predicament.

-Chris.

---

### Post by Zeblue on 2010-09-26
*Is the issue really solved...?*

This is pointing to two issues I'm experiencing as well, though they are isolated to two different machines, both running Ubuntu 10.04 with all current updates.

**[Machine #1]**: Shutdown via GUI menu sometimes logs out instead of shuts down and must be done manually as cludwig wrote.

**[Machine #2]**: I am getting the same error message when trying to access any storage device other than the partition Ubuntu 10.04 is installed on.
> Error:
Unable to mount [XX] GB Filesystem
Not authorizedWhen I try to check my account permissions via user settings using the terminal and "sudo users-admin", the terminal gives back the following message before opening the Users Settings window:

> (users-admin:3061): Liboobs-WARNING **: There was an unknown error communicating asynchronously with the backends: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.I have gone to my user -> advanced settings -> user privileges and put a check next to "Mount user-space filesystems (FUSE)", which was not previously checked, but worked fine, up until now. Anyway, then I logout and back on and see that I still get the same errors as above (for Machine #2), my User Settings are intact, and I do not have any problem with "Shut Down" causing a log off, instead, on this machine.

**Possibly unrelated...**

On Machine #2 when I run Update Manager, I receive the following error message:

> Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.However, when I select "close" on the message, I am able to download all the same updates as listed on Machine #1, which does not get an error when updating.

**Status:** As of now, I still have to manually shutdown Machine #1 on occasion (happens randomly), and have not found any work around for this very new error mounting drives.

---

### Post by Zeblue on 2010-09-26
Okay...

I used the "Restart" GUI option and the computer rebooted with no issues back into Ubuntu 10.04, but I still had the weird mounting error.

When I tried to "shut down" from the GUI, just now, it logged me out, instead. So, I used the "sudo shutdown -h now" command. When I started my computer back up, I could mount the partitions.

I'm weary of calling this "solved", though. I'll keep watching the bug report, [here]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/518533").[]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/518533")

---

### Post by Zeblue on 2010-09-27
This morning Machine #2 yielded the same problem from last night, with one new feature:

log on -> unable to mount drives -> "shut down..." & "restart..." simply cause a log out -> use "sudo shutdown -h now" -> start machine, again -> now, able to mount drives

This is decidedly a workaround procedure and not a fix.

---

### Post by cludwig on 2010-09-29
I would suggest copying your problem into a new thread in one of the busier forums on this site. Perhaps "general help". I noticed this thread wasn't getting many views when posted under security. I have not had a reoccurrence of this problem since I posted the work around I used above. (using sudo to set permissions and force a shutdown to reset everything). 

Good luck,
-chris

---

### Post by Jim_in_Omaha on 2010-09-29
This exact same thing has happened to me with the latest alpha 10.10 and it is happening on a new install of 10.04LTS with the latest updates. I noticed my CPU fan ran up to max then realized a 100%.

I'm watching this one.

---

### Post by Khalaris on 2011-01-30
Your problems seem to be caused by [this bug]("https://bugs.launchpad.net/ubuntu/lucid/+source/consolekit/+bug/544139"). I used C. Watson's Lucid fix and it has solved the problems for me.

---

