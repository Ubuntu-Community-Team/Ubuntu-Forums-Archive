---
title: "apt-get errors during 10.04.3 install, should I worry?"
date: 2011-11-30
forum: Server Platforms
---

### Post by darkod on 2011-11-30
Hi all.

I am installing a 10.04.3 server for a simply home network storage. Something strange happened during the install.

When it got to the "Configuring apt-get" step, saying Retrieving file 1 of 10, it doesn't proceed, just sits there. It doesn't state the name of the file of course, and just the option Cancel is highlighted.
After waiting long, I finally hit Enter to accept the Cancel and it continued. Right away it does it again at Retrieving file 1 of 5 message (still the apt-get step). I hit Cancel again and it continues.
The install runs fine from then on.

After the first reboot I did apt-get update and apt-get upgrade right away. No errors, it updated the sources and upgraded the packages. Without a single error.
Then I did apt-get install transmission and it finished fine, downloading lots of other packages too. Not a single error.

Is it safe to say hitting Cancel didn't have any consequences before I proceed further with the setup?

---

### Post by newbie-user on 2011-11-30
Do you have two network cards in your server?  What might be happening is that the installation is trying to download through the network card that isn't connected to your Internet connection.

---

