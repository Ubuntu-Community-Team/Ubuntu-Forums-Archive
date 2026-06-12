---
title: "Missing messaging menu"
date: 2012-09-26
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by effenberg0x0 on 2012-09-26
I'm not sure if it disappeared today, I don't use it much. But for some reason I needed to use it today and it was not there. I completely purged and reinstalled indicator-messages, did an update&upgrade, even a dist-upgrade and nothing. 

I believe there was some conflict with telepathy-indicator a while ago, but having it installed or not makes no difference here.

Anyone else?

Regards,
Effenberg

---

### Post by wojox on 2012-09-26
Good riddance to it. :p 

I just noticed when I saw this post, mine is gone as well. I did a fresh install from last night's beta2. Don't remember ever seeing it.

---

### Post by nkijak on 2012-09-26
I am missing it as well. Occurred when I updated to the beta 1 version.  Tried doing unity --reset and some other things that worked on older versions with no luck.

---

### Post by jbicha on 2012-09-26
Do you guys have Empathy installed?

There's a new feature where the messaging menu won't show up if you don't have messaging apps.

---

### Post by effenberg0x0 on 2012-09-26
> **jbicha said:**
> Do you guys have Empathy installed?

There's a new feature where the messaging menu won't show up if you don't have messaging apps.

Yep, I read this on LP, I don't think its the same bug. I'm using empathy right now, and I still don't have the messaging-menu. See the screenshot:

[ATTACH]224688[/ATTACH]
Maybe I should browse LP a little more, try to re-check everything here before creating a new bug report.

You have any idea what it could be? I can't find anything relevant in logs.

Regards,
Effenberg

---

### Post by mc4man on 2012-09-26
You haven't mentioned if the process is running.
(I'm sure you've checked that it's not there in the panel sans icon?

I've removed all messaging apps here, still get the menu (indicator),  for TB & unity-mail

---

### Post by effenberg0x0 on 2012-09-27
> **mc4man said:**
> You haven't mentioned if the process is running.
(I'm sure you've checked that it's not there in the panel sans icon?

I've removed all messaging apps here, still get the menu (indicator),  for TB & unity-mail

I did try to change the icon theme to see if it was there but with no icon, no luck. And yes, I see indicator-messages-service running. 

Killing it causes no effect that I can see. But here's what I see when I try to relaunch it (maybe I'm doing it wrong? There's no --help, I don't know if I should use args):

```
[00:48:23] ahsl@AL-DESK01:[~]: /usr/lib/indicator-messages/indicator-messages-service

(process:26938): libindicator-WARNING **: No watchers, service timing out.

(process:26938): Indicator-Messages-WARNING **: Shutting down service!

```

Regards,
Effenberg

PS: I see no difference in having or not having telepathy-indicator installed and running. What is the expected/correct way? Is it installed and running for you?

---

### Post by funicorn on 2012-09-27
The new message indicator seems to to work only with .svg. Check and make sure these files exist in your current icon theme folder. 

I use Faenza icons&#65292;and don't have message menus until I copy these files there.[INDENT][SIZE=3][COLOR=Red][COLOR=Blue]alternate-message-icons:[/COLOR] [/COLOR][/SIZE][SIZE=2][ATTACH]224695[/ATTACH][/SIZE]
[/INDENT][CENTER][INDENT][LEFT]                            [ATTACH]224696[/ATTACH]
[/LEFT]
[/INDENT][/CENTER]

> 
indicator-messages-available-new.svg
indicator-messages-available.svg
indicator-messages-away-new.svg
indicator-messages-away.svg
indicator-messages-busy-new.svg
indicator-messages-busy.svg
indicator-messages-invisible-new.svg
indicator-messages-invisible.svg
indicator-messages-mixed-new.svg
indicator-messages-mixed.svg
indicator-messages-new.svg
indicator-messages-offline-new.svg
indicator-messages-offline.svg
indicator-messages.svg


---

### Post by mc4man on 2012-09-27
> **effenberg0x0 said:**
> 

PS: I see no difference in having or not having telepathy-indicator installed and running. What is the expected/correct way? Is it installed and running for you?

Well, i'm getting ready for new install so the other day removed a whole lot of stuff inc. all messaging apps.
(wantd to see if anything was contributing to some of the current issues in Dash 
The reason I get the indicator is because of TB (& unity-mail

So re-installed the whole mess, (ubuntu-desktop) & it all seems fine, everything shows
As far as the telepathy-indicator, doesn't seem to matter if installed or not.

(only mentioned checking if the indicator was there unseen because of the current indicator-sync which is there (unseen), & has to be exposed thru cursor move & click or highlight an indicator & left/right arrows

---

### Post by lucianct on 2012-09-29
The new messaging menu doesn't work at all with SVG icons, so I converted them to PNG and now everything works perfectly. If you're using a dark version of Faenza (Faenza-Ambiance, Faenza-Dark, Faenza-Darker, Faenza-Darkest), just merge the status folder from the [attachment]("http://ubuntuforums.org/attachment.php?attachmentid=224841") with /usr/share/icons/Faenza-Dark/status/


If you don't like the alternate icons, you could also edit your theme to inherit from one of the ubuntu-mono themes, and the missing icons will be the default ubuntu icons. E.g.:
```
/usr/share/icons/Faenza-Ambiance/index.theme
-  Inherits=Faenza-Darkest
+  Inherits=Faenza-Darkest,ubuntu-mono-dark
```

---

### Post by Frogs Hair on 2012-09-29
The menu works with Nitrux-umd icons if you're looking for something other than the default icons. [http://www.omgubuntu.co.uk/2012/08/nitrux-icon-theme-adds-angular-awesome-to-ubuntu](http://www.omgubuntu.co.uk/2012/08/nitrux-icon-theme-adds-angular-awesome-to-ubuntu)

---

### Post by effenberg0x0 on 2012-09-29
t started working again for me after Friday's updates. No need for manual tweaking of any sort. It was just a temporary glitch.

sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade

Thanks,
Effenberg

---

