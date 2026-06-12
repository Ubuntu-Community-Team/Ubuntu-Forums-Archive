---
title: "Install Spotify on Ubuntu 22.04."
date: 2022-04-07
forum: Ubuntu Development Version
---

### Post by Hewjr100 on 2022-04-07
Anyone able to install Spotify.  I get the following message:

```
The following packages have unmet dependencies: spotify-client : Depends: libssl1.1 but it is not installable or
                           libssl1.0.2 but it is not installable or
                           libssl1.0.1 but it is not installable or
                           libssl1.0.0 but it is not installable
E: Unable to correct problems, you have held broken packages.
```

---

### Post by jimmy-frydkaer on 2022-04-07
sudo snap install --edge spotify

---

### Post by Hewjr100 on 2022-04-08
Thank you will give it a go.

Henry

---

### Post by DuckHook on 2022-04-08
Please do note the following:

[LIST=1]
[*]If you decide to go with snaps, just make sure that you are fully aware of the ramifications. There's nothing inherently wrong with snaps, but they have their disadvantages as well as their advantages.
[*]Edge versions are not stable. That's why they're edge. Be aware of this too.
[*]The message: "you have held broken packages" could be a false alarm, but could also be accurate. If the latter, it is a good idea to chase it down and figure out cause and solution. Otherwise, you have just delayed your eventual day of reckoning temporarily.
[/LIST]

---

### Post by Hewjr100 on 2022-04-08
No way am I using snaps, remove all snap files when I do a fresh install.  Naturally they come back and I nuke them again.

Henry

---

### Post by oldos2er on 2022-04-09
There's also a few flatpak spotify front-ends, but I don't have experience running any of them.

---

