---
title: "Using ClamAV..."
date: 2010-08-20
forum: Security
---

### Post by Stormsy on 2010-08-20
Hi,

It's been about 2/3 months since I installed Ubuntu over my Win Vista HDD (and I'll never regret doing it!)  And so far it's been great!

Obviously, having a new OS, I started looking in the Ubuntu Repo's seeing what free software I could download (a lot of packages were donwloaded that day).  I thought I would try using the ClamAV package and just have a bit-of-a "poke" about with it - curiosity got the better of me.

After I downloaded it from the Repo, I couldn't update it though.  I was wondering if there is a solution to update the virus definitions etc?

Is the package updated through Ubuntu Update manager?

Thanks,
Stormsy. :)

---

### Post by cdenley on 2010-08-20
Why are you using ClamAV if you no longer have Windows Vista installed? What are you trying to accomplish? How are you trying to update the definitions, and how is it failing?

The package is updated with the update-manager, not the virus definitions. On my 8.04 file server, there is a process (freshclam) which runs in the background and updates virus definitions periodically. I imagine there is similar functionality in more recent releases.

---

### Post by bodhi.zazen on 2010-08-20
Try the security sticky

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Specifically :

[http://ubuntuforums.org/showpost.php?p=9265657&postcount=9](http://ubuntuforums.org/showpost.php?p=9265657&postcount=9)

---

### Post by Stormsy on 2010-08-24
Thanks for your replies.

Like I said before, I am just curious about using AV in Ubuntu and wanted to know how to update the virus definitions for the Clam scanner - of course, it makes sense now to use the terminal and sudo to update.

Thanks for your help! :)
Stormsy.

EDIT::  Just installed clamAV using the following command line;

"sudo apt-get install clamav"

And using the command line is a lot better actually!  A quick question, using;

"sudo freshclam" - will that completely update the whole AV; databases, AV engines etc?

Also - using "sudo", does that give me complete root access, or is it used to verify the installation of the package?  Is there anyway to "logout" from using "sudo" in the terminal?

(Sorry for the large amount of questions! :D)

---

### Post by bodhi.zazen on 2010-08-24
> **Stormsy said:**
> Thanks for your replies.

Like I said before, I am just curious about using AV in Ubuntu and wanted to know how to update the virus definitions for the Clam scanner - of course, it makes sense now to use the terminal and sudo to update.

Thanks for your help! :)
Stormsy.

EDIT::  Just installed clamAV using the following command line;

"sudo apt-get install clamav"

And using the command line is a lot better actually!  A quick question, using;

"sudo freshclam" - will that completely update the whole AV; databases, AV engines etc?

Also - using "sudo", does that give me complete root access, or is it used to verify the installation of the package?  Is there anyway to "logout" from using "sudo" in the terminal?

(Sorry for the large amount of questions! :D)

freshclam updates the virus database.

For your sudo questions , see

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

I can not tell from your post if you are logging out of a root shell ( you used sudo -I) , in that case use "exit" without quotes.

Of if you are asking about the grace period (timeout) when you can use sudo without a password (15 min by default) , in which case use sudo -k

---

