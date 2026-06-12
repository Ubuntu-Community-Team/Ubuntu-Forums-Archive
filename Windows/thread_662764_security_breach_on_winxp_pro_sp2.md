---
title: "security breach on winxp pro sp2"
date: 2008-01-09
forum: Windows
---

### Post by xiphosurus on 2008-01-09
I wonder if anyone has experienced this...:confused:

On my laptop, in C:\>, I share 1 folder on windows share.

On another computer, using win xp, I can see only that folder that I shared.

However on ubuntu 7.10, through the "windows network", there is a C$ which turns out to be the root directory C:\> of my laptop!!!

WORST STILL... I can MOVE AND DELETE files on my laptop root directory C:\> through ubuntu!!!!!!! :shock:

FYI, the remote desktop and receive remote assistance on my laptop is disabled.

---

### Post by insane_alien on 2008-01-09
well, it is an XP problem for sure.

sure you configured it right? check your config.

---

### Post by lespaul_rentals on 2008-01-09
This isn't some unknown exploit or hole, it's a well known function.  If you want to disable this you should stop the NetBIOS service in Services (Start > Run> services.msc).  Also, if you have a firewall, set it to block ports 139 and 445, in and out traffic.  Yes, it will disable sharing, but it's the only way to be 100% safe.

---

### Post by xiphosurus on 2008-01-09
lespaul_rentals, you are right.... turns out this is not really a problem. it is a hidden share for 'administrative purposes'. i tried disabling it but it restarts each time i restart windows.

i still wanted to be able to share folders that i specify... so i found [this hack]("http://www.windowsnetworking.com/kbase/WindowsTips/WindowsXP/AdminTips/Network/DisableWindowsNTW2KXPHiddenAdministrativeShares.html") to get the hidden share permanently disable... thanks for your help!

---

### Post by inversekinetix on 2008-01-09
thats handy, I wonder, though, why when people modify windows to do something that it isn't configured to do out of the box it is referred to as a 'hack'  but when you modify a vanilla linux it isn't.

---

### Post by insane_alien on 2008-01-10
because linux has an easy way to do it that doesn't involve tricking the OS into doing it.

with windows it is usually messy, complicated and dificult.

---

### Post by rickyjones on 2008-01-10
The administrative shares should only be accessible to users with a valid password on the system.

I would personally leave them as is and make sure you use a decent password on your Windows user accounts. 

-Richard

---

### Post by lespaul_rentals on 2008-01-10
> **insane_alien said:**
> because linux has an easy way to do it that doesn't involve tricking the OS into doing it.

with windows it is usually messy, complicated and dificult.

I really think people exaggerate the difficulty of it.  Going into the Windows Registy and changing a value, or disabling a service really isn't that horrible.  Yet, it is pointless, and yes, it is inefficient, but come on, stop trying to find any reason possible that Windows sucks.

---

