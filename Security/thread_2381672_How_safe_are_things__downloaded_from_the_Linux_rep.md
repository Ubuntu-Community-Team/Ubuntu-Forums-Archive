---
title: "How safe are things  downloaded from the Linux repository ? (no program specifically)"
date: 2018-01-03
forum: Security
---

### Post by jedi123 on 2018-01-03
HI folks, I just wanted to know how safe are things downloaded from the Linux or Ubuntu repository? 

1. Is it the Ubuntu repository of the Linux repository ? 
2.When I type in **sudo apt-get vlc ,** how  well are things checked for malicious software? 
3. When I download from the software updater app, I basically am hoping that I am not downloading anything bad, and that everything is being checksum verified --- is this true or false? 

Thanks. 

PS yes I am a newbie to Linux, I would like to be informed about security and be more secure .Thanks.

---

### Post by DuckHook on 2018-01-03
Welcome to the forums, jedi123.

Let's start by answering your questions:

[list=1]
[*]Each distro maintains its own repository, so it is the Ubuntu repository. Technically speaking, Linux is only the kernel and therefore does not have a repository.
[*]The premise of your question arises from a basic misunderstanding of open source software. Whereas a closed-source app store like Google's or Apple's tries to "check" for malicious software, they are at an immediate and huge disadvantage to that of any Linux distro—***they have no ability to examine the source code.*** Anything malicious that is hiding in those apps must be teased out through trial and error, testing and the usual antivirus scans. But in the free and open source Linux ecosystem, the only way that an app makes it into the repos is to have its source code openly available. I will leave it to you to decide how likely it is "hide" malicious behaviour when the source code is open to review and analysis by anyone.
[*]Actually, it is a bit more secure than even you are hoping. When you first installed Ubuntu, you also installed Ubuntu's public keys. When you download something from the repos, they are signed in such a way that they must successfully verify themselves against those keys. If they have been tampered with, or are not original, or come from anywhere other than Ubuntu's repos or mirrors, they will not pass signature verification and apt will refuse to install them. It is far more than just a simple checksum.
[/list]
> **jedi123 said:**
> …I am a newbie to Linux, I would like to be informed about security and be more secure .Thanks.
As a user new to Ubuntu, it is only natural, I suppose, to have the concerns that plague users of commercial software. Therefore, I would highly recommend that you read some of the links in my sig. In particular: **Linux is Not Windows** and **Security Basics**. This will give you a lot of the background necessary to think through issues the Linux way.

I will also point you to an old but still relevant post of mine (no use reinventing the wheel): [https://ubuntuforums.org/showthread.php?t=2184758&p=12833795#post12833795](https://ubuntuforums.org/showthread.php?t=2184758&p=12833795#post12833795)

---

### Post by jedi123 on 2018-01-05
I do have a habit  of  everyday,  of  opening a  terminal, and writing ```
sudo apt-get update
``` and  ```
sudo apt-get upgrade
```  However , I notice that even though I do this everyday, the software updater app still says that I need to  download more stuff. Why is this?

Why  this  discrepancy ? In theory I am doing everything I need to do with the above commands, security wise.   PS I can take a screen shot, of my software update preferences, and give them to you . 

Thanks.

---

### Post by vasa1 on 2018-01-05
> **jedi123 said:**
> I do have a habit  of  **everyday **,  of  opening a  terminal, and writing ** "sudo apt-get update" and  sudo apt-get upgrade".  **However , I notice that even though I do this everyday, the **software updater app , still says that I need to  download more stuff.** Why is this?

Why  this  discrepancy ? In theory I am doing everything I need to do with the above commands, security wise.   PS I can take a** screen shot, of my software update preferences,** and give them to you . 

Thanks.Kernel upgrades that may not be available with *sudo apt-get upgrade*? To see, try *sudo apt-get dist-upgrade* and press "N" if you are reluctant to proceed. In any case, copy paste the entire output of
```
sudo apt-get update
```
and```
sudo apt-get dist-upgrade
```
here. No need for a screenshot for now. Some information is better presented via copy/paste using code tags.

---

### Post by DuckHook on 2018-01-05
> **jedi123 said:**
> I do have a habit  of  everyday,  of  opening a  terminal, and writing ```
sudo apt-get update
``` and  ```
sudo apt-get upgrade
```
Good habit. Keep doing that. Some people turn on automatic updating, but I don't like it. I want to know what is being updated.
> …I notice that even though I do this everyday, the software updater app still says that I need to  download more stuff. Why is this?
As *vasa1* notes:```
sudo apt-get upgrade
```…does not update everything. To update the kernel, follow his instructions with:```
sudo apt-get dist-upgrade
```
You can make the *dist-upgrade* process pause, report a list of all changes, then ask for your permission before proceeding further, by installing the package *apt-listchanges*. Note that because *apt-listchanges* must ask for permission, this will break automatic updates. But if your goal is to review all updates before allowing them, then you will not be running automatic updates anyway.

---

### Post by deadflowr on 2018-01-05
> However , I notice that even though I do this everyday, the software updater app still says that I need to download more stuff. Why is this?
Are the listed packages different from those you've just apt-getted?

---

### Post by TheFu on 2018-01-09
I have a slightly different view, but along the same lines as the esteemed folks above.

The #1 security technique for anyone, on any computer, is to have versioned backups. NOTHING, NOTHING, replaces what versioned backups provide.  Patching alone is not enough.

I think running updates daily is asking for trouble and not as easy to find the root cause when something breaks.  I run them weekly. This way, I know for the 24-48 hrs after updates are done, that any issue is likely related to a recent update.  That leaves 5 days of relative stability.

sudo apt upgrade - - does get patches to kernels.  It doesn't update to a newer kernel release.  "New" is the enemy of stable.  I prefer stable almost always.  There are reasons to NOT want a newer kernel, just like there are reasons to need a newer kernel.  Regardless, we all want security updates for the kernel and our programs, which apt upgrade does get, provided the kernel is still supported.  That is a little more complicated question, since some kernels only have 6-9 months of support.  If you don't want to worry about all this, running *sudo apt dist-upgrade* **is** safe and will keep you on a supported kernel provided the entire release is supported.  "dist-upgrade" is the old option name.  There is a newer name that does exactly the same thing, but I can't remember it right now (the apt-get manpage has the answer).  At some future point, dist-upgrade will likely be removed.

You can disable the GUI patching reminders.  If you are manually doing them and always will, you don't need the GUI.  As to why different times of day produce different results?  That is because patches are being provided as they become available and finally get pushed-to/pulled-by the repositories around the world. 

apt, apt-get, aptitude, or the GUI tools for package management all work with the same back-end database and libraries. For normal updates, I use **apt**.  When I need a CLI interface or want slightly more complex choices, then I'll use **aptitude**.   These days, I only use **apt-get** out of muscle memory or when copy/pasting from some notes I made previously.  99% of the time, it doesn't matter which interface to APT we choose, so I choose to type fewer characters. ;)

And lastly, just to clarify the checksum question.  Packages are cryptographically signed. This is a fairly strong level of assurance that nothing has been tampered with or broken or accidentally corrupted between the package maintainer and transfer to your installation.  APT does this and has for decades.  This isn't just a download like setup.exe is.

---

### Post by jedi123 on 2018-01-09
All very good, advice, my concern is, that when I press ok, on th**e software updater application, **some weird non-ubuntu,  and possibly malicious stuff gets put into  the mix.

---

### Post by TheFu on 2018-01-09
The same repos are used, regardless of the interface.

Of course, if you are seeing something different, can you please show the differences?

---

### Post by jedi123 on 2018-01-11
> **TheFu said:**
> The same repos are used, regardless of the interface.

Of course, if you are seeing something different, can you please show the differences?

I was not able to screen shot the terminal. But right now I just did sudo apt-get update and sudo at-get upgrade, then I saw all this security stuff. What gives?  Anything from the software updater is verified via pgp key correct? I attached a screen shot from software updater.

---

### Post by QIII on 2018-01-11
You do not need to post screen shots of terminal results.  In fact, we'd rather you didn't.  Just copy and paste the text between code tags.

---

### Post by deadflowr on 2018-01-11
> Anything from the software updater is verified via pgp key correct
Yep

---

### Post by TheFu on 2018-01-11
> **QIII said:**
> You do not need to post screen shots of terminal results.  In fact, we'd rather you didn't.  Just copy and paste the text between code tags.

+100!!!!!!

---

### Post by ian-weisser on 2018-01-11
There's a whole set of stickies at the top of the Secuirty sub-forum to orient users to Security in Ubuntu, and to help you ask the right questions to keep your system safe.
Start with [https://ubuntuforums.org/showthread.php?t=510812](https://ubuntuforums.org/showthread.php?t=510812)

---

