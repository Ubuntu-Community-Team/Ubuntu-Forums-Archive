---
title: "Thunderbird 2 core dump after presenting UI"
date: 2007-06-19
forum: Ubuntuzilla
---

### Post by DoctorLard on 2007-06-19
I have apt-get installed Thunderbird 2 from:
   deb [http://gnomefreak.youmortals.com/mozilla-testing](http://gnomefreak.youmortals.com/mozilla-testing) feisty main

and it works fine on two desktops, but seg faults (core dumps) on my laptop, but after presenting the main UI window briefly, and long enough to try connecting to a mail server.

1. All three are at the same version, all three have 4 packages installed: thunderbird, mozilla-thunderbird-enigmail, thunderbird-gnome-support and thunderbird-locale-en-gb packages.

2. I tried backing up and nuking the ~/.mozilla-thunderbird folder, which presented the account set up wizard as normal. After filling the account details, TB core dumped when attempting to connect.

3. I tried with a fresh folder again, this time cancelling the account setup (so TB has no accounts). UI window stays up fine. Quit, copied old prefs.js in, core dumps.

4. I tried apt-get remove scim. No cigar.

5. All three machines are running 386 Feisty, all up to date, all with universe, multiverse and above mozilla-testing repos enabled.

Is there some debug info being written somewhere I can investigate, or undocumented switches to turn on logging, etc?

Highly annoying.
J

---

### Post by nanotube on 2007-06-20
hi,
well, this forum is for ubuntuzilla, which installs the official mozilla build directly from the mozilla release servers.
you appear to have installed from a custom repository, packaged by gnomefreak.
so... i would advise you to contact gnomefreak and ask him about this problem, as it may be something specific due to the way he packaged the .deb.

you might also find help in this thread, which gnomefreak seems to be monitoring:
[http://ubuntuforums.org/showthread.php?t=413908&page=3](http://ubuntuforums.org/showthread.php?t=413908&page=3)

otherwise, you are free to try to use the [ubuntuzilla script]("http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla"), and install thunderbird from the official mozilla build, and see if it continues to present the seg fault problem.

---

