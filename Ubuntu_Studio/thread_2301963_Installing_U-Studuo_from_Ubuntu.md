---
title: "Installing U-Studuo from Ubuntu"
date: 2015-11-06
forum: Ubuntu Studio
---

### Post by O)9(yo&amp;# on 2015-11-06
If you already have Ubuntu 14.04, how do you install Studio? within Ubuntu, on another partition, etc? Do you need to download it, or is it already in your system? Thanks, michael

---

### Post by ajgreeny on 2015-11-06
You can just install the ubuntustudio-desktop package and you will have the option to login to US instead of normal ubuntu.

However, bear in mind that it will pull in a lot of packages that are not really needed simply to do all the multimedia tasks that US can do; it will also add the xfce4 desktop along with all the dependencies of that.

What you could do is make use of synaptic, the best package manager there is, which you will have to install first, refresh the repos and mark US-desktop for installation with all the dependencies that it asks for.

Now, instead of using the Apply toolbar button, go to File->"Save markings as..." and save it as a txt file in your home.  If you now open that file you can check all the packages marked and note those that appear useful to you, delete those that are not really needed, including the ubuntustudio-desktop package itself, and then manually install the ones that look to be useful to you, along with their dependencies.

It's a fairly complicated way to get all the multimedia parts of ubuntu-studio without the various DE parts that it asks for but may not be as long winded as it sounds as I've never even thought about it before, and certainly never carried it out.

---

### Post by O)9(yo&amp;# on 2015-11-06
Thank you AJ for that great reply. At this point, I'm in the survey stage re: Linux Audio. I don't need the visual stuff, but it still might be good to have it, as my wife might find it interesting (and I would love to get her into Linux). If I decide on US, I'll come back to your instructions before installing it as they make a lot of sense.

---

