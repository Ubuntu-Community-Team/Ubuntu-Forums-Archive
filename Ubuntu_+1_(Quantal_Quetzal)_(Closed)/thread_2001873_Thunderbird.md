---
title: "Thunderbird"
date: 2012-06-11
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by kuvanito on 2012-06-11
something wrong with thunderbird
it will not launch from the unity bar
i must go and find it in the hud to launch it
there two differents icons,the bird have definetely different face look
at first i had two icon showing on unity dash then one but sriosly there is something wrong here.....:guitar:

---

### Post by fjgaude on 2012-06-11
Give us some idea what system you are running, please.

---

### Post by kuvanito on 2012-06-11
> **fjgaude said:**
> Give us some idea what system you are running, please.

where was this thread created?
what do you think?
12.10 dude

---

### Post by Peter09 on 2012-06-12
I have seen this happen before with another application. Try unlocking Thunderbird from the launcher. Then start it via the dash and lock it again in the Launcher.
 
See if the new locked thunderbird can be launched.

---

### Post by kuvanito on 2012-06-12
> **Peter09 said:**
> I have seen this happen before with another application. Try unlocking Thunderbird from the launcher. Then start it via the dash and lock it again in the Launcher.
 
See if the new locked thunderbird can be launched.

thanks peter
done that,still persist.
i know we are testing 12.10 but there is no way to report this little bug.

---

### Post by mc4man on 2012-06-12
Typically when you get a launching icon & then 2nd or even a 3rd controlling icon it's because of a missing or incorrect StartupWMClass= line in the .desktop

In this case - 
 **Edit:** the line in thunderbird.desktop is wrong
As a temp workaround edit as shown
So remove TB icon from launcher, log out/in to clear any possible unity nonsense, then 
```
sudo gedit /usr/share/applications/thunderbird.desktop
```
scroll down & add -bin to the line

Or wait for an update that should be forthcoming


Edit: report
[https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/1012158](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/1012158)

---

### Post by kuvanito on 2012-06-12
mc4man THANK YOU!
You nailed it...
Thanks to You I fixed this little annoying bug

I am having a Beer at your name :D :D :D

---

### Post by mc4man on 2012-06-14
The new TB update should no longer have this issue - 
The line has now been removed entirely from the .desktop as it's no longer needed.

That was my 1st. fix here which worked fine unless TB was opened from messaging indicator while also having  a pinned launcher. In that one case a 2nd icon was opened.
With the new TB this won't happen so all should be good, if you do get a 2nd icon make sure there is no StartupWMClass= line in thunderbird.desktop

---

### Post by billstei on 2012-06-16
This bug is also in Ubuntu 12.04 Precise (thunderbired 12.0) and I removed the StartupWMClass line completely to fix it.

Update: Spoke too soon, broke again.  Did thunderbird package re-install.  Working for now...

---

