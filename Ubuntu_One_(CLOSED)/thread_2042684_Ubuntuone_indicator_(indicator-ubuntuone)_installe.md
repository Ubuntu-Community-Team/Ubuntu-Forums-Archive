---
title: "Ubuntuone indicator (indicator-ubuntuone) installed but won't show in dash"
date: 2012-08-15
forum: Ubuntu One (CLOSED)
---

### Post by MorrisseyJ on 2012-08-15
Hi, 

I am trying to install the ubuntuone indicator from the ppa:rye/ubuntuone-extras.

> sudo add-apt-repository ppa:rye/ubuntuone-extras
sudo apt-get update
sudo apt-get install indicator-ubuntuone

Everything seems to go fine and programme looks like its installed but i am unable to launch the programme from the dash. Nothing comes up when i search and there is no ubuntuone indicator under: applications-->Internet.

When i try and run: "indicator-ubuntuone" from the command line i get: > indicator-ubuntuone: command not found I Have tried purging and reinstalling. Also tried installing through both the ppa and the .deb. Nothing works. 

If i try apt-get install indicator-ubuntuone, i get```
:indicator-ubuntuone is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
``` Which means that it is installed. Its just not registering in the dash. 

Anyone have any ideas what's going on?

Thanks, 

j

---

### Post by cheri703 on 2012-08-17
I came across this post while looking for an answer to the same question!

I found this: [http://rtg.in.ua/blog/2012/04/a-brand-new-ubuntu-one-indicator-for-precise/](http://rtg.in.ua/blog/2012/04/a-brand-new-ubuntu-one-indicator-for-precise/)

Basically, it isn't in /usr/bin, it is in /usr/lib/indicator-ubuntuone/ so that's why it doesn't show up in the dash.

If you go into /usr/lib/indicator-ubuntuone/ and double click indicator-ubuntuone then it'll open. I added it to my startup applications so I don't have to worry about it in the future.

Hope that helps!

---

### Post by MorrisseyJ on 2012-08-19
Yup, 

That's the answer. 

Thanks very much.

j

---

