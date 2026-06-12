---
title: "gnome-shell &amp; wicd"
date: 2012-04-01
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by SWoRD-Jr on 2012-04-01
Let me begin by saying I'm fairly new to linux in general but have been testing distros for quite some time and came across a problem I have never encountered before so bear with me and please tell me exact steps to follow if you are suggesting a solution.

network-manager has always been buggy on my laptop (random reconnects every few mins) therefore I've stuck with wicd since karmic came out. During beta 1 on precise I had no problems simply removing network-manager on gnome-shell (3.3.92) and installing wicd as a replacement. However ever since shell 3.4 was released it seems either disabling network-manager or removing it wont let me log into gnome-shell anymore. It simply loads a screen with no panel/dash. Unity is not affected and wicd runs there perfectly.

To reproduce simple try 

sudo service network-manager stop
or sudo apt-get remove network-manager gives me the same result.
then log out and in again to gnome-shell, it will crash (atleast here it does!)

I'm running a fresh install of beta2 here with all my previous configs cleared.

Advice needed.

Thanks

---

### Post by dino99 on 2012-04-01
im not a GS user but confirm that wicd works fine on gnome-classic (gnome-session-fallback)

---

### Post by mc4man on 2012-04-01
Can see that here - if you remove Network Manager then GS will crash when logging in - you should be getting a crash report, maybe file a bug  (look in /var/crash), though possibly not a bug

(you could also see in the continuing nonsense that ~/.xsession-errors can produce if you don't delete it before trying a new login

Edit: - it appeas GS needs Network Manager, but not network-manager-gnome, so maybe just leave NM installed

---

### Post by SWoRD-Jr on 2012-04-01
> **dino99 said:**
> im not a GS user but confirm that wicd works fine on gnome-classic (gnome-session-fallback)

Yes the problem is gnome-shell specific, gnome fallback and unity 2D/3D are not affected.

> **mc4man said:**
> Can see that here - if you remove Network Manager  then GS will crash when logging in - you should be getting a crash  report, maybe file a bug  (look in /var/crash), though possibly not a  bug

(you could also see in the continuing nonsense that ~/.xsession-errors  can produce if you don't delete it before trying a new login

Edit: - it appeas GS needs Network Manager, but not network-manager-gnome, so maybe just leave NM installed

Yes but my problem is I need to disable network-manager service to be able to use Wicd instead. Having both running at the same time makes Wicd quite useless. Anyway I found that stopping the service makes me able to use wicd temporarily until I log out without suffering those random disconnects. There must be a clean way to get rid of network-manager without breaking gnome-shell  on every login. I'm sure when wicd users upgrade to precise they'll find this problem irritating.

Still waiting on suggestions/help.

---

### Post by jbicha on 2012-04-01
I believe gnome-shell has a hard dependency on network-manager.

EDITED: Debian has a patch to make that dependency optional, but it needs updating for 3.4.

---

### Post by mc4man on 2012-04-01
> **jbicha said:**
> I believe gnome-shell has a hard dependency on network-manager.

EDITED: Debian has a patch to make that dependency optional, but it needs updating for 3.4.
currently here it deps on some libnm*, gir1.2-network.., but not on network-manager itself

Edit: they should also remove the dep on gnome-bluetooth, even when disabled in bios the indicator shows unless adjusted in gsettings

---

### Post by SWoRD-Jr on 2012-04-01
> **jbicha said:**
> I believe gnome-shell has a hard dependency on network-manager.

EDITED: Debian has a patch to make that dependency optional, but it needs updating for 3.4.


I guess I'll be waiting for that patch until someone figures out another workaround. Its a shame network-manager doesn't like my wireless hardware so much. I dont see why that dependency is necessary they're making it tougher to customize default utilities with every release. RC1 didn't have that problem (GS 3.3.92). Wicd has given me better results always but that's just my experience! Anyway hope this is solved soon.

---

### Post by sammiev on 2012-04-01
Network-manager has not been the best in 12.04 since the start. Hope it will be fixed before the final release. I moved over to wired from wireless until it's fixed.

---

