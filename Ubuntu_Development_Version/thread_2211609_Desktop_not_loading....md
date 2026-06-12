---
title: "Desktop not loading..."
date: 2014-03-16
forum: Ubuntu Development Version
---

### Post by x-shaney-x on 2014-03-16
Not been able to get to the desktop for a few days.
After signing in, I just get the background and nothing else happens.  It's the same thing on two different user accounts.
Anyone else have this?

---

### Post by 23dornot23d on 2014-03-17
What are you trying to run is it just for Unity or are you checking with other desktop environments as well

With Unity a few weeks back now I had a similar problem.

But I could go into other desktops ok ( Kde - Lxde - Fallback )

---

### Post by x-shaney-x on 2014-03-17
Yes its just unity. It is basically a default Ubuntu installation with just a few apps added.
I did try installing Ubuntu desktop last night and it did bring a fair few things in so I'm thinking maybe I haven't been paying attention and something was removed during updates but its still not working.

---

### Post by zika on 2014-03-17
On of the easiest ways is to check into /var/log/apt/ to see what might had been removed during upgrades...
Also check /var/log/Xorg*.log files to see what warnings and erros You get while DM/WM is starting...

---

### Post by x-shaney-x on 2014-03-17
The apt logs point to a few items that were removed during an upgrade but they are the same items that were installed alongside ubuntu-desktop last night and I have checked each removed item and it says each on is already installed.

Xorg logs are showing no apparent errors.
Strange thing is I tried loggin into guest mode and the desktop has appeared as normal but just won't show up on the two "proper" user accounts...

---

### Post by steeldriver on 2014-03-17
tried this? --> [http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html](http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html)

---

### Post by x-shaney-x on 2014-03-17
> **steeldriver said:**
> tried this? --> [http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html](http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html)

I'm unable to download the deb, in console mode thing at the moment and wget gives me an unknown host error for the deb download.
The dconf rest just gives me a long error.  

Also, since that guest login, any attempt at logging in as guest since is giving me the same problems as other users.

---

