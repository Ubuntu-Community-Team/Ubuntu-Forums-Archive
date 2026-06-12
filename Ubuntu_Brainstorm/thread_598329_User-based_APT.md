---
title: "User-based APT"
date: 2007-10-31
forum: Ubuntu Brainstorm
---

### Post by coolen on 2007-10-31
I know this is a Debian thing, not Ubuntu, and it'd represent a massive overhaul, but here's my idea.

APT is great. I love it. It's the reason I chose Debian back when I first started playing with Linux (I was given Fedora CDs, but they were defective).


However, on a user-oriented system, APT tends to encourage users to become root, which we don't want to do. You don't want the head of a household giving root privileges to his entire family so that they don't need to wait for him to get home from work before they can play this new game involving bubbles. You also don't want them having to mess with source code and tarballs.

We want to keep things within APT, but retain the user focus upon which Linux is built.

Many programs in Linux can be installed by the user from a tarball, without root's assistance, to their home directory. For simple programs, whose dependencies are already met, it's no problem.

APT could have two different modes: a user-based mode, and a root mode. When in root mode, it'll install the program to system-wide directories, and when in user-based mode, it'll install to the user's home directory, unless it has a dependency which can only be resolved in root mode (or not at all). The data for each mode would be contained within the one package.

Additionally, when the root user opens Synaptic, a filter should appear listing the user-installed applications, along with how many users have installed it. The root user can choose to install it system-wide, in which case the program data (not configuration or saved data) will be removed from the user's home directory, to save space.

To save on some of the effort of repackaging, it may be possible for APT to determine where the files should go, if the user-based information is lacking. I don't know enough about the packaging process to say, unfortunately.

As I mentioned, this would be a major overhaul, but the long-term advantages would be great. Package management should enhance the Linux experience, not negate it. We're pushing to make Linux more suitable for the desktop. Linux users these days aren't working, or logging in remotely: they're using it to play music and games, watch movies. They need the flexibility we love in Linux, not just in how it looks, but in what's available to them. More importantly, they need to have this without the supreme power of root at their fingertips.

---

### Post by smartboyathome on 2007-10-31
This can be done using the user's ~/.share/ and ~/.local/share/ folders to keep the programs in the user directories. I like this idea. Not only does it increase security (a program installed for a single user will, at worst, ruin their home folder), but flexibility as well (you don't have to have  root permissions to install an app).

---

### Post by coolen on 2007-10-31
That was my thinking. The user's home directory contains (or can be made to contain) a scaled-down version of the Linux filesystem. All you need to do is teach APT to map the directory structure into that.
Of course, it may not always be that simple. Packages containing files in /etc, for example, don't really have an equivalent in the home directory. So, obviously, many programs would need to be repackaged (although not all packages should be accessible to the user).
I don't expect this for Hardy, but it'd be great to have at some point.

---

### Post by smartboyathome on 2007-10-31
> **coolen said:**
> That was my thinking. The user's home directory contains (or can be made to contain) a scaled-down version of the Linux filesystem. All you need to do is teach APT to map the directory structure into that.
Of course, it may not always be that simple. Packages containing files in /etc, for example, don't really have an equivalent in the home directory. So, obviously, many programs would need to be repackaged (although not all packages should be accessible to the user).
I don't expect this for Hardy, but it'd be great to have at some point.

Maybe it is time to start patching APT? :KS

---

### Post by coolen on 2007-10-31
I could always give it a try. I have very limited programming experience (for our last assignment, we had to do things with stock data. Oooooh), but I might be able to yield some results.

---

### Post by smartboyathome on 2007-10-31
> **coolen said:**
> I could always give it a try. I have very limited programming experience (for our last assignment, we had to do things with stock data. Oooooh), but I might be able to yield some results.

I don't know much programming (i have learned some python/bash/java here and there), but I do know that you could probably use apt-get set it to detect if it is run as root, and if not, then it would substitute the ~/.share folder for the /usr/share folder, the ~/.local/share folder for /usr/local/share. I don't know about the /usr/bin, though. I don't think there is an alternative for program binaries.

---

### Post by mysticmatrix on 2007-11-01
Perhaps 0install suits our needs

[http://0install.net/](http://0install.net/)

---

### Post by coolen on 2007-11-01
> **smartboyathome said:**
> I don't know much programming (i have learned some python/bash/java here and there), but I do know that you could probably use apt-get set it to detect if it is run as root, and if not, then it would substitute the ~/.share folder for the /usr/share folder, the ~/.local/share folder for /usr/local/share. I don't know about the /usr/bin, though. I don't think there is an alternative for program binaries.

You'd need to create a bin folder in the user's home directory (a common setup amongst scripters).
In bash, you can simply test the UID. Root has 0, I believe, home folder's kept as a global variable. You'd need to add the user's bin to their path, too.

I might get started on this in a week or two. I've got exams coming up (one of them is a computer science subject...). After that, it'd be fun to mess with it.

---

### Post by coolen on 2007-11-01
These aren't to suit my needs. I am the administrator of all my machines, and the only active user. My sister and her fiance occasionally check their bank balance on here, but that's it.

However, I think this is a necessary step for Ubuntu to become a central system in the average household, with more than one active user. It's certainly one of the long-term goals. I'm not looking for a fix: I'm suggesting a feature.


EDIT: Sorry, I misread your post. It was "our needs", not "your needs".
I don't think it would be wise for Ubuntu to abandon its Debian roots. Debian is renowned for its stability, and even though Ubuntu takes its packages from the testing branch, it's still one of the best sources.
I also don't trust the decentralised distribution model Zero Install encourages. It's not as though APT is a closed system: anyone can create a repository. I use quite a few to get those extra bits of software, and you can always download a single .deb if need be.
Not to mention the work involved in adopting a new package manager, and essentially a new base system.
Additionally, if these changes were applied to APT, it could potentially affect every Debian-based distro out there.

---

### Post by kragen on 2007-11-02
Being able to run apt / synaptic as non root might get confusing. Would it instead make more sense to have an "install only for user" tag / switch instead - that way it wouldnt all go wrong if you intended to install as root, and just forgot to use sudo.

---

### Post by smartboyathome on 2007-11-02
> **kragen said:**
> Being able to run apt / synaptic as non root might get confusing. Would it instead make more sense to have an "install only for user" tag / switch instead - that way it wouldnt all go wrong if you intended to install as root, and just forgot to use sudo.

That would work if apt could figure out which user was running it as sudo, and install it. I was just saying not as root because then it would be easy for it to know which user is running it.

---

### Post by coolen on 2007-11-02
I think the link to Synaptic in the Administration menu should continue to use gksudo. There should be no reason for a user to have that level of control: it's unlikely they'd be able to install a lot of libraries and services.

Other frontends could be a problem...this would need to be addressed. Perhaps the GUIs for admin users could default to a root environment, with an option to install as a user. I see little reason why someone who can install system-wide would want to install as a user, anyway.

As for apt-get/dpkg, perhaps it could warn you if you tried to run it as a user.

---

