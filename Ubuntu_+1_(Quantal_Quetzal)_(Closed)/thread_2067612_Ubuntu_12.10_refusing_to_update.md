---
title: "Ubuntu 12.10 refusing to update"
date: 2012-10-07
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by danbrownlow on 2012-10-07
Hey,

I recently decided to try out Ubuntu 12.10 and it has been working fine so far.

However, yesterday I clicked on "About my Computer" and the button on the bottom right is telling me I can upgrade. When I click the button, I get the message that the software updater is checking for updates, it tries for about 5 minutes before telling asking me whether I have an internet connection or not (I do, I'm browsing the internet right now).

Anyway I can force it to connect and update? I haven't changed any of the Repo settings, and the updater was working until recently when I tried to upgrade today.

Thank you.

This is the error message I receive:

> 
W:Failed to fetch [http://ppa.launchpad.net/yorba/ppa/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/yorba/ppa/ubuntu/dists/quantal/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/yorba/ppa/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/yorba/ppa/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.


---

### Post by PaulW2U on 2012-10-07
Ubuntu 12.10 hasn't been released yet and the owner of that PPA doesn't yet have a quantal version of the repository. 

If you change 'quantal' to 'precise' in your sources list for that PPA you should find that you can run the update without seeing the error you have quoted. Whether the application that you're getting from the PPA will actually run correctly is another matter though.

By the way your post should have been put in the Quantal Forum - [http://ubuntuforums.org/forumdisplay.php?f=416](http://ubuntuforums.org/forumdisplay.php?f=416).

---

### Post by mcduck on 2012-10-07
THat PPA repository doesn't provide packages for 12.10 at the moment. Just remove the PPA and the problem will disappear.

---

### Post by stinkeye on 2012-10-07
> **danbrownlow said:**
> Hey,

I recently decided to try out Ubuntu 12.10 and it has been working fine so far.

However, yesterday I clicked on "About my Computer" and the button on the bottom right is telling me I can upgrade. When I click the button, I get the message that the software updater is checking for updates, it tries for about 5 minutes before telling asking me whether I have an internet connection or not (I do, I'm browsing the internet right now).

Anyway I can force it to connect and update? I haven't changed any of the Repo settings, and the updater was working until recently when I tried to upgrade today.

Thank you.

This is the error message I receive:
[COLOR="Red"]Edit[/COLOR]Answered above. Twice.  
The ppa yorba you added in 12.04 doesn't have 12.10 packages.
Open software sources > other software
and disable both the binary and source ppa for yorba.

---

### Post by Bucky Ball on 2012-10-07
*Thread moved to **Ubuntu +1***

---

