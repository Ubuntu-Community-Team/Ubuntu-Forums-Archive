---
title: "Preference for sending error reports in Privacy is lost"
date: 2012-08-25
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by jokerdino on 2012-08-25
Every time I tick the checkbox to be able to send apport bug reports, it is lost when I close gnome-control-center and reopen it. I am not particularly sure if this is a bug or a localized issue. Can someone verify or help me with this?

You have to be running Unity BTW.


[IMG]http://i.imgur.com/xjZMss.jpg[/IMG]

---

### Post by xeizo on 2012-08-25
I'm not running Unity, I run Xubuntu, but yesterdays crashfest continues and apport is one of the main culprits.

software-update-gtk etc crashes constantly, and there's lots of repositories not to be found when updating, I tried several different servers.

Also, I'm not allowed to send error reports because I locked X to 1.12, so now it seems we MUST run X 1.13 even though Nvidia doesn't work with it. That's nice, since so many run Nvidia ...

Another error is first was all extra harddrives/filesystems removed from /run/user and moved to /media/user, and now they are autorenamed with every reboot - a "1" is added to the name - so I have to create new symlinks every new upstart. It seems messy and unreliable at the moment.

---

### Post by cariboo on 2012-08-25
> **jokerdino said:**
> Every time I tick the checkbox to be able to send apport bug reports, it is lost when I close gnome-control-center and reopen it. I am not particularly sure if this is a bug or a localized issue. Can someone verify or help me with this?

You have to be running Unity BTW.


[IMG]http://i.imgur.com/xjZMss.jpg[/IMG]

This shouldn't stop you from reporting bugs, as on my system the setting is unchecked, but bug reports still go through. I may be missing something here though, if that is not your problem.

---

### Post by mc4man on 2012-08-25
It will uncheck after closing, (never have enabled here)
If recently broke then likely related to g-c-c, switch to gsettings, ect.

Always took it be sending reports to ubuntu's whoopsie/daisy  'whatever', nothing much to do with apport-gtk, ect.

Some info in 1st. answer
[http://askubuntu.com/questions/135540/what-is-the-whoopsie-process-and-how-can-i-remove-it](http://askubuntu.com/questions/135540/what-is-the-whoopsie-process-and-how-can-i-remove-it)

---

### Post by cariboo on 2012-08-25
> **mc4man said:**
> It will uncheck after closing, (never have enabled here)
If recently broke then likely related to g-c-c, switch to gsettings, ect.

Always took it be sending reports to ubuntu's whoopsie/daisy  'whatever', nothing much to do with apport-gtk, ect.

Some info in 1st. answer
[http://askubuntu.com/questions/135540/what-is-the-whoopsie-process-and-how-can-i-remove-it](http://askubuntu.com/questions/135540/what-is-the-whoopsie-process-and-how-can-i-remove-it)

Thanks for that mc4man, so basically this is a good thing for those that don't want their distribution phoning home on an occasional basis. :)

---

### Post by mc4man on 2012-08-25
> **cariboo907 said:**
> Thanks for that mc4man, so basically this is a good thing for those that don't want their distribution phoning home on an occasional basis. :)
That's how I see it - don't think there is an security issue & I gather those reports are put to good use - see occasional ref's on LP bugs
(still I don't feel inclined to enable myself & don't even know if there is value while in dev??

---

### Post by cariboo on 2012-08-25
I personally think this is one of those tools that are more useful to commercial customers, than it is for us consumer users.

---

### Post by jokerdino on 2012-08-26
> **cariboo907 said:**
> This shouldn't stop you from reporting bugs,  as on my system the setting is unchecked, but bug reports still go  through. I may be missing something here though, if that is not your  problem.

I experienced that apport crashes never pop up and I assumed it is because the setting is not checked. 


> **mc4man said:**
> It will uncheck after closing, (never have enabled here)
If recently broke then likely related to g-c-c, switch to gsettings, ect.

Always took it be sending reports to ubuntu's whoopsie/daisy  'whatever', nothing much to do with apport-gtk, ect.

Some info in 1st. answer
[http://askubuntu.com/questions/135540/what-is-the-whoopsie-process-and-how-can-i-remove-it](http://askubuntu.com/questions/135540/what-is-the-whoopsie-process-and-how-can-i-remove-it)

It was broken for quite some time. This didn't happen because of any of the recent changes. OK, I am calling it broken but is this behavior intended?

I  was of the assumption that if it isn't selected, apport wouldn't  appear. And it was happening pretty much like that. The apport crash  dialog appears if I login to KDE but not when I am in Unity.

---

