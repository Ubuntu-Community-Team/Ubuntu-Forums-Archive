---
title: "Reinstall help with Seamonkey"
date: 2010-01-13
forum: Ubuntuzilla
---

### Post by FrancisT on 2010-01-13
So I used the older deb ubuntuzilla method to get seamonkey 2.0. I then successfully updated this, though I did have a sudo-caused permissions/ownership problem which I fixed. Seamonkey 2.02 is now available but there is also a new ubuntuzilla method to get it.

In a series of removals to tidy things up to get it (removing seamonkey 1.1.x which was still there for some reason, of the old unubtuzilla, of the ubuntuzilla installed seamonkey 2.0...) something broke.

I now cannot finish an install of seamonkey 2.0.2. It claims to install but there is no link put in /usr/bin/ for the binary file (it is in /opt/seamonkey though and can be run from there) and attempting to remove the package ends up failng because of the lack of /usr/bn/seamonkey

I've fixed it by doing a 
```
sudo ln -s /opt/seamonkey/seamonkey /usr/bin/seamonkey
```

but I'm concerned that I may have not really fixed the underlying problem so is there something else I should do too? there was, I saw, some error about /usr/bin/seamonkey.ubuntu which doesn't exist either

---

### Post by nanotube on 2010-01-13
> **FrancisT said:**
> So I used the older deb ubuntuzilla method to get seamonkey 2.0. I then successfully updated this, though I did have a sudo-caused permissions/ownership problem which I fixed. Seamonkey 2.02 is now available but there is also a new ubuntuzilla method to get it.

In a series of removals to tidy things up to get it (removing seamonkey 1.1.x which was still there for some reason, of the old unubtuzilla, of the ubuntuzilla installed seamonkey 2.0...) something broke.

I now cannot finish an install of seamonkey 2.0.2. It claims to install but there is no link put in /usr/bin/ for the binary file (it is in /opt/seamonkey though and can be run from there) and attempting to remove the package ends up failng because of the lack of /usr/bn/seamonkey


please specify what method you are using to try to install seamonkey that 'cannot finish', and what exactly it does when it 'claims to install'. maybe post a copy of the terminal log of whatever installation method you're trying to use.

> 
I've fixed it by doing a 
```
sudo ln -s /opt/seamonkey/seamonkey /usr/bin/seamonkey
```

but I'm concerned that I may have not really fixed the underlying problem so is there something else I should do too? there was, I saw, some error about /usr/bin/seamonkey.ubuntu which doesn't exist either

it's hard to say what the 'underlying problem' is without knowing what exactly you have done and what you are attempting to do now. please post some more detail. 

what version of ubuntu?
what method of seamonkey installation are you trying now?
what seamonkey package[s] do you currently have installed?
what precisely is 'not working' as you expect it to?

---

