---
title: "Global Menu: All options &quot;greyed&quot; (as if they were disabled) for all programs"
date: 2012-01-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2012-01-23
About the Global Menu (again): Now I have noticed that, for all programs, all sub-menu options are "greyed", like if they were all disabled, which is impossible. 

Sub-menu items that should be accessible are (they work if you click them). But it's impossible to visually identify which options are available and which are disabled. 

It's seems to be a theme issue, but the same effect happens if I switch themes (Ambience, Adwaita, other). So I'm guessing it started somewhere in the recent updates to GTK libs. 

I'm not sure when this has started: I had the Global Menu disabled until recently and have just restarted testing machines with it enabled.

Have a look at the screenshots.

[ATTACH]211347[/ATTACH]
[ATTACH]211348[/ATTACH]

Regards,
Effenberg

---

### Post by dino99 on 2012-01-23
tweaking ccsm sometimes brings unwanted effects, have you use it ?

---

### Post by zika on 2012-01-23
> **effenberg0x0 said:**
> About the Global Menu (again): Now I have noticed that, for all programs, all sub-menu options are "greyed", like if they were all disabled, which is impossible. 

Sub-menu items that should be accessible are (they work if you click them). But it's impossible to visually identify which options are available and which are disabled. 

It's seems to be a theme issue, but the same effect happens if I switch themes (Ambience, Adwaita, other). So I'm guessing it started somewhere in the recent updates to GTK libs. 

I'm not sure when this has started: I had the Global Menu disabled until recently and have just restarted testing machines with it enabled.

Have a look at the screenshots.

[ATTACH]211347[/ATTACH]
[ATTACH]211348[/ATTACH]

Regards,
EffenbergI've complained on something similar week or so ago. Since I'm not often in Unity or GS I am not sure how it is working (right) now here... I'll check (if I do not forget) once I do log-out from this session... I remember that it kind of cleared but it stayed in LightDM log-in window. Since then I've changed greeter so...

---

### Post by effenberg0x0 on 2012-01-23
> **dino99 said:**
> tweaking ccsm sometimes brings unwanted effects, have you use it ?
Hey Dino, 
Good tip. I have tried resetting compiz effects, but it didn't fix it. I think it's not in ccsm glitches this time. 

> **zika said:**
> I've complained on something similar week or so ago. Since I'm not often in Unity or GS I am not sure how it is working (right) now here... I'll check (if I do not forget) once I do log-out from this session... I remember that it kind of cleared but it stayed in LightDM log-in window. Since then I've changed greeter so...
It's weird cause it doesn't show in a fresh install I just did. I can't remember of a change I might have done to cause this. 

Regards,
Effenberg

---

### Post by mc4man on 2012-01-23
There was this bug about a week ago that caused the same Except it extended to all menus, was light-theme specific & was fixed. (though the fix did bork breadcrumbs which is now fix committed
[https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/917734](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/917734)

BC
[https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/917830](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/917830)

So maybe your issue is somehow gtk related? (assume you've tried a new user

---

### Post by effenberg0x0 on 2012-01-23
> **mc4man said:**
> There was this bug about a week ago that caused the same Except it extended to all menus, was light-theme specific & was fixed. (though the fix did bork breadcrumbs which is now fix committed
[https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/917734](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/917734)

BC
[https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/917830](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/917830)

So maybe your issue is somehow gtk related? (assume you've tried a new user

Hi mc4man, just been through these too. Yes, I have tried a new user, same results. But I can't reproduce it in a fresh install. It's not a bug unless it affects others in a fresh install IMO, so I'll keep investigating it.

---

### Post by mc4man on 2012-01-23
> It's not a bug unless it affects others in a fresh install IMO, so I'll keep investigating it.

Probably some local glitch or whatever, there were gtk;gail & glib upgrades today that went ok, all fine  here

---

### Post by kyleabaker on 2012-01-23
Try applying different themes then go back to Ambiance. I saw this about a week ago. I think that fixed it for me.

---

### Post by mdhollis on 2012-01-23
> **kyleabaker said:**
> Try applying different themes then go back to Ambiance. I saw this about a week ago. I think that fixed it for me.

+1

This happens to me using ambiance and radiance colors.  When I switched back to the default ambiance theme I'm ok.

---

### Post by effenberg0x0 on 2012-01-23
Thank you all, it was fixed by switching between themes a couple times. I have no idea what caused it though.

Regards,
Effenberg

---

### Post by kyleabaker on 2012-01-23
> **mdhollis said:**
> +1

This happens to me using ambiance and radiance colors.  When I switched back to the default ambiance theme I'm ok.

Glad I could help! :guitar:

---

### Post by zika on 2012-01-24
> **kyleabaker said:**
> Try applying different themes then go back to Ambiance. I saw this about a week ago. I think that fixed it for me.
Yes, that is the &#8222;cure&#8220; I used ([written somewhere here](http://ubuntuforums.org/showpost.php?p=11610542&postcount=12))...

---

