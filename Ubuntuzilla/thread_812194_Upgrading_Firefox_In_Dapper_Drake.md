---
title: "Upgrading Firefox In Dapper Drake"
date: 2008-05-29
forum: Ubuntuzilla
---

### Post by theravenproject on 2008-05-29
I am using Dapper Drake becuase I had some serious install problems between Hardy and my MSI (Nvidea 8400GS) Graphics Card-So here I am with the FF that shipped with Dapper and I am interested in upgrading to a later (if not the latest) FF release...is this possible?  If so what are the advantages to upgrading?  I was using The latest FF release on my Win XP before I built this new (High end Gamer) and it was way slower than this version I am using now: Version 1.5.0.12eol(X11;U;Linuxi686)-are there advantages to sticking with the distro I have?  Please advise!

---

### Post by nanotube on 2008-05-30
yes, it is possible to upgrade to the latest ff, if you want.

reasons to upgrade? well, if everything is running fine and you have no complaints, there's no reason. however, there are increasing numbers of extensions that no longer support ff 1.5. ff2 a bit nicer in some ways. ff3 is /much/ nicer than ff2, very fast, the new url bar is quite useful, bookmarks have tags, etc.

(until ff3 gets released, though, ubuntuzilla will only install the latest ff2 for you...)

so anyway.. that's that, in a nutshell. :)

---

### Post by wkitty42 on 2008-07-01
> **nanotube said:**
> yes, it is possible to upgrade to the latest ff, if you want.

reasons to upgrade? well, if everything is running fine and you have no complaints, there's no reason. however, there are increasing numbers of extensions that no longer support ff 1.5. ff2 a bit nicer in some ways. ff3 is /much/ nicer than ff2, very fast, the new url bar is quite useful, bookmarks have tags, etc.

(until ff3 gets released, though, ubuntuzilla will only install the latest ff2 for you...)

so anyway.. that's that, in a nutshell. :)

i agree with everything you have written nanotube... however, there's one ugly gotcha waiting in the wings to jump up and beat on the unsuspecting users now that FF3 is out...

i'm on a fully patched and updated *Kubuntu* Dapper Drake box with ubuntuzilla-4.5.0 installed (according to the counters on sourceforge, i'm the only one who has downloaded it :shock:)...

i attempted to update to FF3 because i couldn't remember what the latest FF2 is/was and i just wanted to make sure that i was up to date on the latest... since i couldn't remember the newest version of FF2 i went ahead and let ubuntuzilla update me to FF3... however, i was met with this rather ugly message when attempting to execute FF3 after it was installed by ubuntuzilla...

```
We're sorry, this application requires a version of the GTK+
library that is not installed on your computer.

You have GTK+ 2.8.
This application requires GTK+ 2.10 or newer.

Please upgrade your GTK+ library if you wish to use this application.
```

now, if that won't make someone freak out a bit :?

in any case, i was able to re-run ubuntuzilla and get back to the working FF2 that i had before... here's the steps i went thru...

[LIST=1]
[*]```
ubuntuzilla.py -a remove -p firefox
```
that takes you all the way back to the original FF1.5 version that comes on Drapper Drake...
[*]then i used the working FF1.5 and go digging about on the mozilla.org site... let me say that it took quite a bit of digging, too :( but i was finally able to find out that the latest FF2 is v2.0.0.14...
[*]close mozilla and re-run ubuntuzilla...
[*]```
ubuntuzilla.py -a install -p firefox
```
[*]> Retrieving the version of the latest release of Firefox from the Mozilla website...
The most recent release of Firefox is detected to be 3.0. Please make sure this is correct before proceeding. (You can confirm by going to [http://www.mozilla.org/](http://www.mozilla.org/))
If no version number shows, if the version shown is not the latest, or if you would like to install an older release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]?
Please enter 'y' or 'n':
**answer 'N'o here!!**
[*]> If no version shows, or it does not agree with the latest version as listed on [http://www.mozilla.org](http://www.mozilla.org), please visit our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) and let us know.
In the meantime, if you want to proceed with installation, you have the option of looking up the latest version yourself on the [http://www.mozilla.org/](http://www.mozilla.org/) website, and entering it here by hand.

Please enter the latest version of Firefox:
enter **_2.0.0.14_** here!
[*]let ubuntuzilla continue normally...
[/LIST]
when ubuntuzilla finishes, you should now have a working FF2.0.0.14 install... i do and i'm using it to write this message with :)

needless to say, i was in a bit of a panic for a li'l bit... all i could do was cross my fingers and hope that the "remove" option would back me out to a working version of FF so that i could get back to what i had before i stumbled into that dark alley where GTK+ snuck up and hit me in the back of the head ;)

---

### Post by nanotube on 2008-07-02
hey!
thanks for posting your experiences on this. :)
i'm aware of the gtk problem with ff3 on dapper, but don't have a dapper box to test on.
would you be willing to help me out with some testing on dapper, to try to get ff3 working?

here's the thread where we were playing with it, until my "tester" gave up for lack of time. :)
[http://ubuntuforums.org/showthread.php?t=832407&page=2](http://ubuntuforums.org/showthread.php?t=832407&page=2)

let's get the discussion going on this thread:
[http://ubuntuforums.org/showthread.php?t=847484](http://ubuntuforums.org/showthread.php?t=847484)

---

### Post by wkitty42 on 2008-07-02
update to my post above:

while i was writing that post, i mistyped 2.0.0.15 a couple of times and had to go back and correct it to 2.0.0.14... now, here it is within 24 hours later and 2.0.0.15 is out :lol:

just follow my instructions above and use **2.0.0.15** instead of 2.0.0.14 and you should be ok to go ;)

now i'm off to see about actually getting it onto my kubuntu side of the fence ;)

---

### Post by wkitty42 on 2008-07-02
> **nanotube said:**
> hey!
thanks for posting your experiences on this. :)
i'm aware of the gtk problem with ff3 on dapper, but don't have a dapper box to test on.
would you be willing to help me out with some testing on dapper, to try to get ff3 working?

here's the thread where we were playing with it, until my "tester" gave up for lack of time. :)
[http://ubuntuforums.org/showthread.php?t=832407&page=2](http://ubuntuforums.org/showthread.php?t=832407&page=2)

let's get the discussion going on this thread:
[http://ubuntuforums.org/showthread.php?t=847484](http://ubuntuforums.org/showthread.php?t=847484)

i'll take a look at those, nanotube, and see what i might be able to do... unfortunately, i really can afford to muck up that install as it is very important to keep it operational for my daily activities when i'm not booted into my win98se side of the fence ;)

---

