---
title: "Weirdness Loggin in"
date: 2010-03-16
forum: Security
---

### Post by Sticky_Bit on 2010-03-16
So logged into my pc yesterday morning to find find a new icon on my panel that said I was logged in with elevated privileges. The icon was a set of keys and clicking it disabled the elevated privileges. This only happened once but I am concerned that my pc may have been compromised.

Should I be worried? Is there something that I can check? I'm somewhat new to Linux so I don't really know all the places to check for signs of being hacked like I would in windows.

---

### Post by cdenley on 2010-03-16
That does sound concerning.
-Go to System>Administration>Authorizations
-Select "Read authorizations of other users" on the left
-Check "Show authorizations from all users" at the bottom

This should show recent privilege elevations.

---

### Post by Sticky_Bit on 2010-03-16
Hi thanks. Authorization is not an option under System>Administration. Im running 9.10 if that helps.

---

### Post by cdenley on 2010-03-16
> **feedusafetus said:**
> Hi thanks. Authorization is not an option under System>Administration. Im running 9.10 if that helps.

I'm pretty sure it should be there unless you removed it.
```

sudo apt-get install policykit-gnome
polkit-gnome-authorization

```

---

### Post by Sticky_Bit on 2010-03-16
Ok got it. It only shows elevation for my account "a moment ago", I'm guessing because I used sudo to load the selection. At least I have somewhere to look in the future.

---

### Post by OpSecShellshock on 2010-03-16
I think that icon is for when you elevate privileges by way of a graphic application and want to set them back to normal earlier than what would happen if you were to just wait for sudo to time out (I think 15 minutes by default).

---

### Post by cdenley on 2010-03-16
> **OpSecShellshock said:**
> I think that icon is for when you elevate privileges by way of a graphic application and want to set them back to normal earlier than what would happen if you were to just wait for sudo to time out (I think 15 minutes by default).

Actually, policykit and sudo are completely seperate privilege elevation systems. I don't think there is a timeout like sudo, but the process has elevated privileges until it ends or you re-lock it. The original poster said the icon appeared at login, which sounds suspicious, but maybe the network configuration applet or something elevates privileges at login without requiring the user to enter a password. I'm not sure why it wouldn't be listed with polkit-gnome-authorization, though.

---

### Post by OpSecShellshock on 2010-03-16
> **cdenley said:**
> Actually, policykit and sudo are completely seperate privilege elevation systems. I don't think there is a timeout like sudo, but the process has elevated privileges until it ends or you re-lock it. The original poster said the icon appeared at login, which sounds suspicious, but maybe the network configuration applet or something elevates privileges at login without requiring the user to enter a password. I'm not sure why it wouldn't be listed with polkit-gnome-authorization, though.

Ah, makes sense, thanks. In light of that, it does seem a bit odd.

---

### Post by Sticky_Bit on 2010-03-17
Op, cdenley, You guys are both right. I have noticed this happeing when I am mounting another partition from within Rhythmbox. The partition has all of my music on it and requires me to enter a password to mount it. When I mount it I get the elevated privileges icon on my panel.

I think I may just simply have been mistaken about this happening when I first logged in. I'm thinking I logged in and opened something that needed sudo. Thank you all for your help. I'm resting a little easier today.

---

### Post by sublimation on 2010-03-17
For a future reference, it seems to me polkit-gnome-authorization isn't default in 9.10. I didn't have it on my (relatively) fresh install. About the only thing I've removed is Evolution.

---

