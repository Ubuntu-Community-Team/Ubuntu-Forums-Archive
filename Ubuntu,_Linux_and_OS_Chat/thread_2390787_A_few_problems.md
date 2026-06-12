---
title: "A few problems"
date: 2018-05-02
forum: Ubuntu, Linux and OS Chat
---

### Post by paralis on 2018-05-02
Just made a clean install of Bionic Beaver on an ASUS N550JV. Overall, I'm okay with it but...

Several apps are VERY slow to start (when they start). Namely the snap ones. For some obscure reason, some gnome components are snaps such as : gnome-calculator, gnome-characters, gnome-logs, gnome-system-monitor, etc. In addition they still (it's an old problem AFAIK) lack theming (most of the time) so they usually look awful. So once you know what is the problem, you get rid of them fast and replace them with 'regular' deb straight from the Ubuntu repo.

Now the Ubuntu app store. It's still a mess. Lot of apps don't have any screenshot to show off (I think it's been that way since the very beginning of the store). I don't think it's hard to understand people need to SEE the app but well, we're only in 2018 after all...

Could also add that having one entry by packaging method is a poor decision since it multiplies the entries for a single app and it's quite confusing for a beginner to see three entries for vlc or whatever app, one for the deb, one for the snap, one for the flatpak. Tons of people will get a mix of official repo, snap and flatpack without even knowing it. A complete mess...

I've got to chat frequently with beginners on linux or Ubuntu and it's quite sad to see an overall good distro crippled with such details.

Anyway, have fun with the beaver.

Eric

---

### Post by monkeybrain20122 on 2018-05-03
I don't use the app store, I still prefer synaptic, aside from finer control the catalog is complete, the app store shows very few apps and nothing like libraries and so on, also snap. The app store pushes for snap whenever possible and it is nasty since a lot of snap apps are not ready, they take up a lot of space, are slow to start and many are crippled in functionality :skype, vlc etc. Since new users think the app store is the most obvious and the only way to install apps chances are they may get tripped over and form a really bad first impression of ubuntu. They should only offer snap packages in the app store if no .deb is available. Enthusiasts can easily experiment with the terminal.

Seems that snap is pushed by some over zealous dev who once again wants to do experiments with the LTS release (Canonical had the good sense to walk back from wayland, snap is a bit of a PITA but this would seem minor comparing to defaulting to wayland ) [https://www.omgubuntu.co.uk/2018/02/ubuntu-18-04-include-snap-apps-default](https://www.omgubuntu.co.uk/2018/02/ubuntu-18-04-include-snap-apps-default)

P.S since I don't use those gnome apps I didn't know they are snap until reading your post. I have not experienced slow boot time, still same as 16.04, which is extremely fast on this machine.

---

### Post by Claus7 on 2018-05-03
Hello,

> **paralis said:**
> Just made a clean install of Bionic Beaver on an ASUS N550JV. Overall, I'm okay with it but...

Nice that overall is ok, sometimes (at least in the past) is/was not. I remember polls about how the installation/upgrade went and for some it was not ok.

> **paralis said:**
> 
Several apps are VERY slow to start (when they start). Namely the snap ones. For some obscure reason, some gnome components are snaps such as : gnome-calculator, gnome-characters, gnome-logs, gnome-system-monitor, etc. 
In addition they still (it's an old problem AFAIK) lack theming (most of the time) so they usually look awful. So once you know what is the problem, you get rid of them fast and replace them with 'regular' deb straight from the Ubuntu repo.

Since you installed them via deb, then you have found solution to your problem. It's a general issue as far as I can see in the forums. In that case indeed such applications you can install them via deb. Some others that are not maintained this way, you can install them via snaps.

> **paralis said:**
> 
Now the Ubuntu app store. It's still a mess. Lot of apps don't have any screenshot to show off (I think it's been that way since the very beginning of the store). I don't think it's hard to understand people need to SEE the app but well, we're only in 2018 after all...

More pictures would be more helpful, indeed...

> **paralis said:**
> 
Could also add that having one entry by packaging method is a poor decision since it multiplies the entries for a single app and it's quite confusing for a beginner to see three entries for vlc or whatever app, one for the deb, one for the snap, one for the flatpak. Tons of people will get a mix of official repo, snap and flatpack without even knowing it. A complete mess...

I've got to chat frequently with beginners on linux or Ubuntu and it's quite sad to see an overall good distro crippled with such details.

Anyway, have fun with the beaver.

Eric

Everything needs its maintenance including this new way of packaging.

Enjoy,

[Edit
> **monkeybrain20122 said:**
> 
P.S since I don't use those gnome apps I didn't know they are snap until reading your post.


In order to check your snap packages you can issue the command:
```
snap list
```
Edit]

Regards!

---

### Post by monkeybrain20122 on 2018-05-03
> **Claus7 said:**
> 
In order to check your snap packages you can issue the command:
```
snap list
```


Regards!

I know that. What I meant was I wouldn't have checked if I had not read his post.

---

