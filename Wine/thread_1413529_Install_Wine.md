---
title: "Install Wine"
date: 2010-02-22
forum: Wine
---

### Post by Tempyr on 2010-02-22
Has anyone seen a message like this before when trying to install Wine?

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: wine1.2 but it is not going to be installed
E: Broken packages


:confused:

---

### Post by hikaricore on 2010-02-22
Do you have the proper repos enabled?

---

### Post by Soulcage on 2010-02-23
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine1.2

Paste these into a terminal.

---

### Post by Tempyr on 2010-02-24
Thanks, I'll try it out when I get home.

---

