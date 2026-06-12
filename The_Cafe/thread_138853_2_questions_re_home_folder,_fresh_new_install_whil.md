---
title: "2 questions re: home folder, fresh new install while keeping old settings"
date: 2006-03-02
forum: The Cafe
---

### Post by Koobi on 2006-03-02
i'm a PHP/MySQL web developer and i've been using Ubuntu for over a year and it's been my first real linux experience but i still don't know too much about how it works but i have a fair knowledge of system commands.

i have two questions to ask you:



(1)
i've read in numerous places that it's best to have your /home folder in a seperate partition...why is this?
i can only think of one reason...is it so that you can install as many distro's as you want on another partition and boot them knowing that your settings will be consistent no matter what distro you're on? that would probably make uninstalling a distro easy as well since it's on a seperate partition, right?

any other advantages i'm missing out on?


also, assuming i do have multiple ext3 partitions, what would i have to do via the installation setup to to install my home folder on one partition and the system on the other?




(2)
i currently have ubuntu on my PC. the thing is, it's so cluttered because i've been experimenting with all sorts of programs over the last year. now that i know what programs i want, i'd like to make a fresh install while keeping my old settings such as the ones in my home folder. is it safe for me to simply backup my home folder and replace it back there once i've completed a fresh install?
i know i could just remove the files i don't want but there are so many and there probably might be some residue files so i'd prefer to just do a clean install and be careful from here on.




thanks for your time :) feel free to throw in any tips.

---

### Post by Bragador on 2006-03-02
You will definitely get more help if you post your questions and problems at [http://ubuntuforums.org/forumdisplay.php?f=91](http://ubuntuforums.org/forumdisplay.php?f=91)

This is more a place to chat so less people come in here :/

I hope this helps...

---

### Post by gord on 2006-03-02
i keep my home folder on a seperate partition, it meens that whenever i re-install or install a new version of ubuntu, my settings are kept the same and i don't have to re-configure everything to how i like it. allthough there are potential problems with upgrading the newer versions because newer versions of programs might not be compatible with old config files.


if you want  to set it up from the get go, just use the advanced partition editor in the setup and when you set up a partition, instead of it pointing to /media/hda1 or whatever, have it point to /home

if you want to do it with an existing setup, just change the partiion info in your fstab to point to /home


i wouldn't recomend just copying your home folder around though, because of problems with the owner of the files changing when you copy them around. allthough it might be fine.

---

### Post by Koobi on 2006-03-02
sorry, thanks for pointing that out. i wasn't quite sure where to post this. i don't see how it's a desktop issue anyway but can a mod please move this thread to that section? or to a more appropriate section if there is one, for this subject.

thanks.

---

