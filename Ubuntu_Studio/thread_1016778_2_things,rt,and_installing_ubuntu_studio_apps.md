---
title: "2 things,rt,and installing ubuntu studio apps??"
date: 2008-12-20
forum: Ubuntu Studio
---

### Post by rixtr66 on 2008-12-20
I finally updated to intrepid,so far no problems,what i want to ask is does anyone know if the rt kernel is stable yet?and i prefer to install studio apps on ubuntu,for me studio has been unstable,and i find it works much better on straight ubuntu,how do i get the studio pkgs.in intrepid?
any help would be appreciated!!!!
Rick:guitar:

---

### Post by barisurum on 2008-12-21
As far as I know you don't have to do anything big to get them. They should already be in your repos. If you want to install them as two metagackages just install [COLOR="Red"]ubuntustudio-audio[/COLOR] for audio apps and plugins and [COLOR="Red"]ubuntustudio-graphics[/COLOR] for graphics apps.

As for the rt kernel as long as this statement doesn't change I won't upgrade: [http://ubuntustudio.org/8-10_release_note](http://ubuntustudio.org/8-10_release_note)

---

### Post by Ng Oon-Ee on 2008-12-21
> **rixtr66 said:**
> I finally updated to intrepid,so far no problems,what i want to ask is does anyone know if the rt kernel is stable yet?and i prefer to install studio apps on ubuntu,for me studio has been unstable,and i find it works much better on straight ubuntu,how do i get the studio pkgs.in intrepid?
any help would be appreciated!!!!
Rick:guitar:
There is already (and has always been since release) an RT kernel in the repos. However it has the following two issues:-
1. Only uses a single core. Ever.
2. Shutdown/sleep/hibernate problems (you basically can't, it hangs somewhere) due to problems with Network Manager. Disabling Network Manager manually before you shutdown means it will work fine though, in my experience.

And a quick search could have told you this. Specifically a thread I've started contains the information you need. Subscribe to that one, if an RT-kernel comes out either myself or hopefully someone else will update that thread. [You can find it here.]("http://ubuntuforums.org/showthread.php?t=974982")

---

