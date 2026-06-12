---
title: "Regarding bug i noticed on beta2 iso"
date: 2012-09-28
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by craig10x on 2012-09-28
I downloaded the ubuntu 12.10 beta 2 (64 bit) iso and ran it live session...I have not actually installed it as of yet...
I have a new toshiba laptop with i3 intel core processor and graphics...

Two bugs i noticed were:

1) when installing Google Chrome deb file with ubuntu software center, it installed it properly but some warning window came up about it being a bad file...

2) i also noticed that no matter what time i set the display to turn off (ex: 30 minutes, 60 minutes, Never)...it would still turn off after the default 10 minutes...

I was wondering if anyone who has installed the beta 2 have encountered those two bugs after actual installation....
I'm especially concerned about #2 because if i installed now i sure wouldn't want the display to turn off after 10 minutes all the time...

As far as i could tell, everything else seemed to run pretty smoothly...

Thanks for all input ;)

---

### Post by SheamusPatt on 2012-09-28
The 12.10 Beta 2 was just released - why are you testing 12.04?

---

### Post by craig10x on 2012-09-28
> **SheamusPatt said:**
> The 12.10 Beta 2 was just released - why are you testing 12.04?

oops..thanks for calling that to my attention...i meant 12.10 beta2...:)
just edited my post...

i know sometimes one will encounter certain bugs on an iso that won't be present when actually installed...so i was hoping for some input from those that have actually installed it, to find out if those 2 bugs are present (especially the display one i mentioned)...

---

### Post by cariboo on 2012-09-29
I just installed chrome on my Gnome Remix install, and ran into the same problem. I found that I wasn't paying attention, and installed the 32-bit package on my 64-bit installation, and synaptic kept saying I had a broken package. Removing the 32-bit, and installing the 64-bit solved the majority of the problems. Synaptic still says under google-chrome properties, that google-chrome breaks google-chrome, but it works without a problem for me.

As to your second concern, this problem has been discussed both during the previous development cycle, as well as this one. You should find an answer to your question in [this]("http://ubuntuforums.org/showthread.php?t=2059551") thread.

---

### Post by mc4man on 2012-09-29
> **craig10x said:**
> 
Two bugs i noticed were:

1) when installing Google Chrome deb file with ubuntu software center, it installed it properly but some warning window came up about it being a bad file...

Not really a Ubuntu bug, the google-chrome package is not quite properly done so it fails a lintian test which produces the 'bad package' message

Don't think it's of much concern, if curious the lintian error usually is - 
"E: google-chrome-stable: file-in-etc-not-marked-as-conffile etc/cron.daily/google-chrome"
which means there should have been a conffile in the package's  Debian folder & there wasn't

---

### Post by funicorn on 2012-09-29
For now the genuine bug I met is window expo runs choppy when window preview are tiled and displayed. It's a huge regression of unity.

---

### Post by craig10x on 2012-09-29
So, then i take it that everyone running 12.10 (installed) is having this bug where the screen display always goes off at the 10 minutes interval no matter what you set it to in system settings?

---

### Post by cariboo on 2012-09-29
> **craig10x said:**
> So, then i take it that everyone running 12.10 (installed) is having this bug where the screen display always goes off at the 10 minutes interval no matter what you set it to in system settings?

Yes, that's why there are work-arounds posted in the thread I linked to.

---

