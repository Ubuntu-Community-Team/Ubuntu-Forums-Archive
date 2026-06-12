---
title: "Does Ubuntu Software Center implement application approval for security purpose?"
date: 2012-04-19
forum: Security
---

### Post by kcs11 on 2012-04-19
I was searching for a program for Ubuntu that does exactly as Deep Freeze from Faronics would do for windows. Luckily, the software called Ofris had been written especially for Ubuntu users. So, I opened up Ubuntu Software Center and typed in Ofris, but no search was found. What I realize was this was written by third party programer, and I had to manually download and install it via Sudo commands.
 
My questions and concerns are:
 
How can I be sure that Ofris is not an exploit and is absolutely safe to use?
 
Moreover, how can I be sure of any third party applications as such I download and install manually would be free from vunerable exploit or malware?
 
Where as Apple App Store uses a security method for implimenting all applications must be deemed safe before it is approved, does Ubuntu Software Center carry out a similar security technique implement for Linux applications?
 
...If not, it would be such a great idea if they do.
 
 
Please repond to my concerns (questions), thank you!

---

### Post by ammofreak on 2012-04-19
Hi ):P 
For 3rd party downloads, I installed BitDefender. 
_[http://www.bitdefender.com/business/antivirus-for-unices.html](http://www.bitdefender.com/business/antivirus-for-unices.html)_ (request a free license for personal use)

Then, after I download anything not from Ubuntu repositories, I simply scan it before installing it. There is ClamAV with a GUI but I could never figure out how to update the virus engine. Albeit, the virus signatures always updated without any problem. Hope this helps.

If you do not want to use BitDefender, go here for other suggestions: _[http://www.makeuseof.com/tag/free-linux-antivirus-programs/](http://www.makeuseof.com/tag/free-linux-antivirus-programs/)_

For more info: [https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by for.i.am.root on 2012-04-19
A bit of a geeky answer, however, I don't like downloading a binary executable. I always download source where available. And yes, I actually do skim through all source before I compile it.

If the source is unavailable I turn to Google to see what the rest of my peers think of it and if it is considered safe.

Remember to check md5sums as well. It's fairly easy east to rename a malicious binary to something known safe to trick people into running it.

In this case Ofris is safe. Just download from a trusted source and verify the md5sum / signature before running anything.

---

### Post by rookcifer on 2012-04-20
> **kcs11 said:**
>  
My questions and concerns are:
 
How can I be sure that Ofris is not an exploit and is absolutely safe to use?

You have to trust two things:

1) That the author of the software itself is not evil (most of us don't bother with this step, since it would take a full review of the source code)

2) That the file you downloaded is *really* the file you think you're getting (this is the easiest step to complete).

Ubuntu normally takes care of step #2 for us since all packages that get put there are verified cryptographically to be from the actual author or from some other trusted party who compiled it.

Since you didn't get this from Ubuntu's repos, you have to verify it yourself.  Some developers are lazy and do not sign their software with GPG keys.  If that is the case, the best you can do is to compare the hash of the package you have with the hash of the package on the site you got it from.  Keep in mind that even if the hashes match it is not a 100% guarantee that the package is clean.  Why?  Because someone could have hacked his website and uploaded a fake package.  But if you *assume* his site hasn't been hacked, then hashes should verify the package is legit.  

The best way is for every developer to simply sign their packages with GPG keys.  That way, even if their site (or development repository) is hacked, you can be sure the package you get is legit.  However, you still have the issue of verifying that the GPG key belongs to the real author.  But even if you don't bother, you will know if something changes in the packages over time or if they are signed suddenly by a new key (which would indicate someone has uploaded a fake).
 
> Moreover, how can I be sure of any third party applications as such I download and install manually would be free from vunerable exploit or malware?

You can't without at least completing step #2 above.  If you can also complete step #1, excellent, but most people aren't going to take them time to review code unless it is something like the kernel code, etc. that tons of people collaborate on.
 
> Where as Apple App Store uses a security method for implimenting all applications must be deemed safe before it is approved, does Ubuntu Software Center carry out a similar security technique implement for Linux applications?

Sort of.  They take care not to allow "fake" packages in, but there is no guarantee that the original author isn't evil and doing something malicious.  The same can be true of Apple too.  I doubt Apple checks every line of code before they approve a package.  I would assume they do what Ubuntu does and just go by the package's general reputation (e.g., lots of people use this and have not reported funny behavior, so let's go ahead and accept it and be sure we get it from the original source).

Also, please ignore the advice others have given about using AV scanners.  They are worthless, even on Windows for the most part.  This is especially true on Linux since most AV scanners will only scan for Windows malware anyway (since there simply isn't much Linux malware out there).  Most likely if a Linux package is malicious, it will not be something an AV scanner picks up anyway.  One of the reasons Windows security is in its sorry state is because people have fallen for the AV con (a multi-billion dollar industry).  AV vendors *want* you to be behind the curve.  They know that their method of blacklisting always means that some new virus will pop up, thus making customers have to renew their subscriptions.  They want it that way because it makes them lots of money.

The best way to verify packages in Linux is to do what I said above.

---

