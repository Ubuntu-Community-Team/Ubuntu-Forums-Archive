---
title: "Messed Up Apt-Get"
date: 2005-08-26
forum: Repositories &amp; Backports
---

### Post by Jade Robbins on 2005-08-26
I did a HowTo and now whenever i try to install any packages with apt-get i get ```
jaderobbins@usasuper2:~$ sudo apt-get install linpopup
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  linpopup: Depends: samba but it is not going to be installed
E: Broken packages
``` 

Any help allowing me to use apt again? Thanks!

---

### Post by invalid on 2005-08-26
If you are not using a server install, I would suggest using Synaptic (which comes already installed on desktops) to download and install packages.

Synaptic works the same as apt-get, just in a gui enviornrment. Additionally, it had an option to fix broken packages upon request.

Cheers,
Cb

---

### Post by Jade Robbins on 2005-08-26
[QUOTE=invalid]If you are not using a server install, I would suggest using Synaptic (which comes already installed on desktops) to download and install packages.

Synaptic works the same as apt-get, just in a gui enviornrment. Additionally, it had an option to fix broken packages upon request.

Cheers,
Cb[/QUOTE]
 i've used Synapitic and get an error message stating the same thing. Where is the broken packages option?

Thanks.

---

### Post by Jade Robbins on 2005-08-26
[QUOTE=Jade Robbins]i've used Synapitic and get an error message stating the same thing. Where is the broken packages option?

Thanks.[/QUOTE]
 in synaptic i get the error message that states a dependency and then says it's not going to be installed. Also , i found the broken package fixer but it did not help. :S

---

### Post by az on 2005-08-26
Try:

sudo apt-get -f install

the install samba

sudo apt-get install samba


Post the result if it does not make you happy.

---

