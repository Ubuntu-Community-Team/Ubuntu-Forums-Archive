---
title: "wmlive = Window Maker Live (an hommage)"
date: 2012-09-24
forum: The Cafe
---

### Post by ohnonot on 2012-09-24
There's an installable Window Maker Live CD out there.
I've installed it on an old machine and i love it!
Gimp 2.8 and Firefox 13.0 on an old school Desktop Environment and it's faster than my other, newer machine with xubuntu.

check it out here: [http://wmlive.sourceforge.net/](http://wmlive.sourceforge.net/)

This thread could hopefully develop into a support thread since there's no forum or mailing list for wmlive (yet).

I'm still very much in the process of getting to know it's ways but of course already started customizing...

Greetings,

daniel.

edit: including archive with style, conky, hacked libWINGs, background.

---

### Post by wmlive on 2012-11-28
Hi, this is the wmlive project founder writing. I just stumbled over this thread while searching the web for further traces of my wmlive project. Thanks for your nice words!

Regarding a forum or mailing list for wmlive, there is none of its own because i deemed the wmaker user and devel mailing lists as the best choice for discussing these matters. As wmlive mostly tries to serve the purpose of Wndow Maker the window manager, it is best to keep discussion about both together in one place in order to avoid fragmentation. Check out [http://lists.windowmaker.org](http://lists.windowmaker.org) for further details.

Said that, i am currently waiting for the release of a new wmaker version before publishing new ISO's of wmlive. Progress on my little project has been ongoing all the time, although rather slow as i am basically alone working on this. New releases will only be published when the time is ripe for them.

---

### Post by szymon_g on 2012-11-28
WindowMaker was the first "graphical environment" i've seen on Linux. I saw it 11 years ago, but i see icons are as ugly as they've been back then.

---

### Post by ohnonot on 2012-11-29
hello,

i was quite interested in wmaker for a while but i was having a weird problem with the live install - 
i could not add new icons to the dock. otherwise it was working nicely and i was starting to get the hang of it, but i couldn't get any help on that...
:cry:

i had wmaker installed as a window manager on my other machine but there the dock was ok.

---

### Post by wmlive on 2012-11-29
Hi ohnonot,

of course, there is always the option to directly contact me writing a mail to the address mentioned all over the installation instructions. As the amount of downloaders and users is still not in the millions, until further notice, i should be able to handle such personal feedback.

If you still happen to have the latest version 2012-06-11 as available from wmlive.sf.net installed, in order to enable me to reproduce your issues, could you please run the command 'Preferences > PrefsBackup > Backup Preferences' from the WindowMaker root menu, and send me the resulting archive found in ~/.cache/WindowMaker/PrefsBackUp' via e-mail to the mentioned mail address?

Other than that, it should take only about approximately one more week until the next wmaker version will (hopefully!) finally be officially released, and when new wmlive ISO's will be made available from the sourceforge site. You might prefer waiting for and install that one instead, as it supposedly will have lots less issues than the version you tried.

I already have produced some ISO images containing the latest wmaker git builds, and which have lots of bugs fixed both on behalf of WindowMaker and especially for wmlive itself. So, if you prefer, stay tuned waiting for the next wmlive release version before bothering to debug what is possibly already fixed.

Best regards,
Paul

---

### Post by mr john on 2012-11-30
I love the oldskool look of that. Downloading it now, but I wont get to try it until next week.

---

### Post by ohnonot on 2012-11-30
hello paul,

i believe we had the pleasure already and also discussed this particular problem.
we didn't find a solution then - and since then i've been shuffling my hardware around and installing new operating systems...

but yes, maybe i'll try again when the new windowmaker and/or wmlive is out.
:guitar:
rock'n'roll!

---

### Post by wmlive on 2012-12-03
Hi all,

i do need your eyes and expertise to overcome my own blindness for the limitations of my little wmlive project.

Until the new Window Maker version finally becomes available, in order to produce new ISO images, here is something fo the more adventurous minds.

I have been working intensively on the build procedure for the wmlive ISO images, and have fixed quite a lot of bugs found. Since my build tree now appears to be working quite well, i have created and uploaded a tar ball of the whole thing to Sourceforge. So if someone is interested in creating his own variety of the wmlive ISO, please download [http://sourceforge.net/projects/wmlive/files/wmlive_build.d-20121202.tar.gz](http://sourceforge.net/projects/wmlive/files/wmlive_build.d-20121202.tar.gz) and investigate its possibilities.

You need to have the Debian live-build toolset  (preferably from unstable or testing) installed, in order to be able to run the wmlive build procedure: [http://packages.debian.org/search?keywords=live-build](http://packages.debian.org/search?keywords=live-build) 

There is a manual at [http://live.debian.net/manual/html/live-manual.en.html](http://live.debian.net/manual/html/live-manual.en.html) for further information about how this all works.

Any success or failure reports, maybe even patches and enhancement suggestions would be very welcome! 

Best Regards,
Paul <[EMAIL="wmlive@users.sf.net"]wmlive@users.sf.net[/EMAIL]>

---

