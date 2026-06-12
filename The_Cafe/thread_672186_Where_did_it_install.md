---
title: "Where did it install?"
date: 2008-01-19
forum: The Cafe
---

### Post by bag4705 on 2008-01-19
I'm relatively new to both the forums and Ubuntu so feel free to point me to a more appropriate location, but searches didn't seem to turn up anything.  This seems to be a catch all.

I've been doing a lot of experimenting with various applications and that, of course, means a lot of install and removal of packages.  I've recently found out that "purge" doesn't necessarily delete all files and directories so I'm ending up with junk I'll never use, but I don't recognize much of it.

Is there a command or application that will either record the location of new files and directories as they are created or some method of running a differential after the install so I can later verify total removal if I uninstall the package?

Appreciate any guidance you can provide.

GAB

---

### Post by urukrama on 2008-01-19
Try "whereis *application*" in a terminal. It will tell you where the different files of the application are located.

---

### Post by FuturePilot on 2008-01-19
You can open Synaptic and click the buton "Status". That will sort the packages by status. You can then see the different categories such as Autoremovable, Residual, etc. If you see any Residual packages you can mark them for Complete Removal which will remove everything included in that package.
You can also do the same from the command line if you know the name of the package.
```
sudo apt-get remove --purge <package-name>
```
will purge it from the system.

```
sudo apt-get autoremove
```
will remove un-needed dependencies but will not purge them.

---

### Post by bag4705 on 2008-01-19
That got me part way to where I want to go.  I can now find the apps that don't show on a menu.  :-)  Thanks.

As an example of what I'm trying to achieve, I used clamav since I am confident in being able to restore and configure that particular app.  When I removed all clamav packages (using Mark for complete removal in Synaptic Package Manager), it left /etc/clamav directory and the freshclam.d file behind.

What I am looking for is some way to detect and remove all traces of apps that I'm sure I'll never again use.  I think this will help me learn the Ubuntu without getting hung up trying to figure out what the leftover files/directories are for.

GAB

---

### Post by Mateo on 2008-01-19
i find all of the command-line searches (whereis, find, locate) to be wildly inconsistent and unreliable.  unless you have the exact file name it won't find it, and even if you do it won't find it about 50% of the time.  just my experience.  wildcards doesn't seem to help either.

---

### Post by bag4705 on 2008-01-19
@FuturePilot, thanks for the additional data.  Just one question.  It was my understanding that Mark for Complete Removal in Synaptic Package Manager is the same as apt-get -purge.  Do I have that correct?

Even after using the purge, I have a lot of *freshclam* files floating around in /var and /etc  I could manually remove these without a problem.  In this case, I'm confident where they came from; I'm not as confident about some of the other applications.  That's why I was looking for a way to determine at the beginning which files are attached to the various packages.

Thanks.

GAB

---

### Post by gangalee on 2008-05-20
How about this question? -

Where (which directory) do the packages download for synaptic by default?
I guess I should qualify the query with why I want to do it-
which is I'm in a developing country and my internet access is through a GSM phone and I have a network of Ubuntu machines that I'd like to install packages on without a central network gateway. Is there a way I can cache the packages (which I assume they are already) and then copy the packages to the various machines?

---

### Post by gangalee on 2008-05-20
[nevermind...]("http://ubuntuforums.org/showpost.php?p=3153437&postcount=35")

---

### Post by madjr on 2008-05-20
alt + f2

type the app name

or use deskbar applet

---

