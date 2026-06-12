---
title: "Using apparmor to restrict file browser"
date: 2010-09-21
forum: Security
---

### Post by joelwhrs on 2010-09-21
I am trying to use apparmor to restrict my file browser, which is Thunar to only let me view the files that are in the home directory and also removable media. I tried following the apparmor sticky with no success. I created the profile and tried editing it and it either started and let me do pretty much everything or did not start at all. Would it be possible for someone to help me step by step to set up a profile for thunar that would only show the home directory and removable media.

---

### Post by bodhi.zazen on 2010-09-21
> **joelwhrs said:**
> I am trying to use apparmor to restrict my file browser, which is Thunar to only let me view the files that are in the home directory and also removable media. I tried following the apparmor sticky with no success. I created the profile and tried editing it and it either started and let me do pretty much everything or did not start at all. Would it be possible for someone to help me step by step to set up a profile for thunar that would only show the home directory and removable media.

I suggest you start by looking at and understanding how apparmor works and perhaps start with an easier application.

Restricting thunar to /home is not possible as you will need access to binaries, lib, and icons, etc, outside of /home.

Also although you might confine thunar, it does not do much if users can open a shell and go where they wish.

At any rate, you need to watch your logs and debug the error message apparmor is giving you.

As an alternate take a look at jailbash.

[Jailbash]("http://ubuntuforums.org/showpost.php?p=9799756&postcount=5")

---

### Post by joelwhrs on 2010-09-22
Actually all that I would need to do is keep the user from being able to access the parent directory above the home folder. It would not really matter if they could access the icons, etc just as long as they could not easily view the complete root directory, etc. Would this be easier to accomplish?

---

