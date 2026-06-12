---
title: "Run windows apps and games already installed on the windows installation"
date: 2010-04-06
forum: Wine
---

### Post by fasoulas on 2010-04-06
Can i run an application that is already installed on the windows installation from wine by just clicking on the .exe executable in it's installation folder.

I have tried it and some apps work this way,but especially games don't work.

So is there a way to make them work without reinstalling them on the linux partition??

---

### Post by hikaricore on 2010-04-06
No

---

### Post by doas777 on 2010-04-06
probably not, but it's not a simple yes/no.

for instance, I use notepad++, putty, and winscp on windows. all of these apps come with installers, but the installer jsut copies the file somwhere. they doesn;t alter the registery, or install subcomponents, or register shared libraries.
these apps will run fine (assuming wine will run them) just by launching the exe via wine.

however an app like visual studio, makes extensive alterations to the registry, installs and configures host services, register libraries, and who knows what else. this kind of app will not run unless you install it into wine itself. 

wine has a "virtual registry" and as such it needs to be modified by the installer, as it is not the same one used by teh windows install. 

hth

---

### Post by fasoulas on 2010-04-06
> **doas777 said:**
> probably not, but it's not a simple yes/no.

for instance, I use notepad++, putty, and winscp on windows. all of these apps come with installers, but the installer jsut copies the file somwhere. they doesn;t alter the registery, or install subcomponents, or register shared libraries.
these apps will run fine (assuming wine will run them) just by launching the exe via wine.

however an app like visual studio, makes extensive alterations to the registry, installs and configures host services, register libraries, and who knows what else. this kind of app will not run unless you install it into wine itself. 

wine has a "virtual registry" and as such it needs to be modified by the installer, as it is not the same one used by teh windows install. 

hth

thanks for repling.
this could have helped a lot in saving hd space if it was true.

---

