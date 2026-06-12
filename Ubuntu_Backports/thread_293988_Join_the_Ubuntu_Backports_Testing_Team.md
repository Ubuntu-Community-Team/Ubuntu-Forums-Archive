---
title: "Join the Ubuntu Backports Testing Team"
date: 2006-11-06
forum: Ubuntu Backports
---

### Post by jdong on 2006-11-06
[https://launchpad.net/people/ubuntu-backports-testers](https://launchpad.net/people/ubuntu-backports-testers)

**Sales Pitch:**
Have an interest in testing packages? Want to help out Ubuntu? Then the Backports Testing Team may be for you!

**What does this team do?**
In the words of the team creator (hey, that's me!):
> 
Ubuntu Backports Testers are those who go through the Ubuntu backports requests. Their tasks include triaging requests to make sure they meet Backporting standards, building test packages to provide for wider testing, and also testing packages to make sure they work.



**Ok, I'm interested. How do I join? Is it a hard job?**
The team is open for anyone to join on Launchpad. Feel free to call yourself an official Backports Tester!

The process is extremely easy and done with automated tools. Very few skills are necessary. You will use the **prevu** tool to build testing backport packages, so familiarize yourself with the operation of this tool. I've written up a nice HOWTO at [http://ubuntuforums.org/showthread.php?t=268687](http://ubuntuforums.org/showthread.php?t=268687)

Also familiarize yourself with the general Backports guidelines as to what's an acceptable backport and what's not. You can find those at [https://wiki.ubuntu.com/UbuntuBackports](https://wiki.ubuntu.com/UbuntuBackports) , under "how to file requests"

**Step-by-step, what do I need to do?**
I am assuming you are running the version of Ubuntu you want to test Backports for. (For example, you're running Edgy and testing Edgy backports candidates. Or you're running Dapper and testing Dapper backports candidates. You are **not** running Edgy and testing Dapper backports candidates). If you are trying to cross-test Backports, you are recommended to use either a dual-boot or a virtual machine of that version of Ubuntu, as you need to be able to run the backport to properly test it.

(1) Get prevu ([http://ubuntuforums.org/showthread.php?t=268687)](http://ubuntuforums.org/showthread.php?t=268687)). If you have not used prevu before, you need to initialize it by running:
```

sudo prevu-init

```

Prevu's output packages also get written to a local APT repository. For your convenience, you can add a line like the following to /etc/apt/sources.list to ease the process of installing a testing backport on your system:
```

deb file:///var/cache/prevu/dapper-debs ./

```

Replace dapper with whatever distribution you are running.

This is covered in more detail at the above linked thread.

(2) Look for open Backports requests. Backports requests are filed in Launchpad under products such as dapper-backports, edgy-backports, and so on. Go to [https://launchpad.net/products/dapper-backports](https://launchpad.net/products/dapper-backports) or [https://launchpad.net/products/edgy-backports](https://launchpad.net/products/edgy-backports), for example. Then, hit the "Bugs" link on the left side. It might be helpful, too, to sort by newest first.

(3) The backporting process is done in phases. What you need to do to help depends on the phase:

**Unconfirmed**: These are requests freshly filed and you're the first to evaluate the backport. Check to make sure that it is a valid backport request according to the guidelines, and send it through a test build via prevu. For example, if someone requests a backport of gedit, run
```

prevu gedit

```

If it builds successfully, change the status to **Confirmed** and add a comment like "Builds successfully with prevu, and meets Backports guidelines". If the build fails with an error, paste the relevant portions of the error onto the bug report, then mark the status as **Rejected**. If the request doesn't meet backports guidelines, mark it as **Rejected**. If you're not sure, then just leave it there, and Backporters will come through and check them.

**Confirmed**: These are requests that another tester has made sure meets guidelines and also compiles successfully. Now, your job is to build & install the package on your system, and make sure that the program functions. For example, if we use the gedit example again, you'd run:
```

prevu gedit
sudo apt-get update; sudo apt-get dist-upgrade
(or, if you don't have an older version installed:) sudo apt-get update; sudo apt-get install gedit

```
Next, you would try using the new gedit, testing all aspects of its functionality to make sure it isn't buggy or unstable, or have any glaring problems.

Finally, you would add a comment on the bug stating your opinion, such as "Confirmed; builds successfully. Also runs fine in my tests", or "There is a bug with the indent plugin; it crashes GEdit."

**In Progress**
If 5 or more testers report back positively in the Confirmed status, and there aren't any bugs unresolved, a member of the Ubuntu Backports team will approve the backport, and the status will be changed to In Progress. Backports **testers** should **NOT** set packages to the In Progress state.

**Fix Released**
After approval, a few days per week Ubuntu Archive Administrators will add these backports to the repositories, and they will set the bug to this state. The backport is now done.


================
**Miscellaneous Notes Worth Mentioning**
================

* This guide has you testing backports for the version of Ubuntu you currently run. This is the recommended way of doing it. If you insist, you can use the "DIST=edgy prevu gedit" (or whatever other Ubuntu release) overrides to target debs for a different Ubuntu release.
* Only use this procedure with prevu to test backports. Prevu builds packages in a controlled, clean environment, so that your testing more closely reflects what will be built on the Ubuntu servers for backports. Do not, for example, download sources from the author's site and use ./configure && make
* Periodically run "sudo prevu-update" to keep your build environment up-to-date.
* Periodically purge the contents of /var/cache/prevu/dapper-debs (or whatever distro you run). This avoids contaminating your build environment.

---

