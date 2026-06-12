---
title: "Adding Repositories"
date: 2006-11-07
forum: Repositories &amp; Backports
---

### Post by Darrenlaid on 2006-11-07
Yesterday i attempted to add some software, it might have been chess software or perhaps it was anagram software, needless to say i was not very succesfully.
Today i was working my way through "adding repositories" [https://help.ubuntu.com/community/Repositories/Ubuntu#head-a86dddc6826cec4a3847d8441b24051d07b8dc64](https://help.ubuntu.com/community/Repositories/Ubuntu#head-a86dddc6826cec4a3847d8441b24051d07b8dc64)
When i tried to reload in synaptic package manager i got an error.
E: Type &#8216;[ftp://ftp.cis.uab.edu/pub/hyatt/&#8217;](ftp://ftp.cis.uab.edu/pub/hyatt/&#8217;) is not known on line 34 in source list /etc/apt/sources.list
E: Unable to lock the list directory

After seeing this i remember i did a custom add channel yesterday, big mistake i guess.
Could somebody be so kind as to help me correct my error and clean up this mess i have created. Thank you

---

### Post by GeirG on 2006-11-07
The entry you added is missing a type indicator (**deb** or **src**) telling whether it is a source for binary or source packages.

The easiest way to fix this (imho) is to issue the following command (after  shutting down Synaptic):
**sudo gedit /etc/apt/sources.list**
This wil prompt you for you password, and then let you edit the source list for apt repositories.

Find the line with the problematic address, and add **deb** or **src** at the beginning (with a space after the type).
My guess is that it should be **deb** in this case.

Save the file, exit gedit (the text editor that was started by the command you entered), and restart Synaptic.

Good luck

---

