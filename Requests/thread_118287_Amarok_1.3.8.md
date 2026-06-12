---
title: "Amarok 1.3.8"
date: 2006-01-16
forum: Requests
---

### Post by INMCM on 2006-01-16
Bugfix Release. Already in Dapper.

Changes Version 1.3.8:
Bugfixes

    * NMM engine would crash when seeking after the playlist finished, state Empty wasn't emitted
    * Fixed URL of the Nectarine radio stream.
    * Fix crash after changing the alsa device in the helix configuration dialog.
    * When amaroK exits, send SIGTERM to running scripts. (BR 119159)
    * Old error messages could be shown instead of current track lyrics.
    * The equalizer in the helix engine now works properly at low sample frequencies.
    * Fixed some threading issues in loading XML playlists.
    * Lyrics that are available on lyrc.ar would be shown as "not found".
    * The helix engine now includes protection so that misbehaving streams do not cause the visualizations to leak memory.

---

### Post by Velvet Elvis on 2006-01-17
Other than the usual complaining about taglib, it compiles and runs fine for me, FWIW.

---

### Post by noigeaR on 2006-01-20
now you can get official breezy packages of amarok 1.3.8 here [http://kubuntu.org/announcements/amarok-1.3.8.php](http://kubuntu.org/announcements/amarok-1.3.8.php)

---

### Post by INMCM on 2006-01-20
Horray!!!

---

### Post by edwin11 on 2006-01-25
[QUOTE=noigeaR]now you can get official breezy packages of amarok 1.3.8 here [http://kubuntu.org/announcements/amarok-1.3.8.php](http://kubuntu.org/announcements/amarok-1.3.8.php)[/QUOTE]

Hi, sorry, but i'm a newbie here.

i would like to install amorok 1.3.8, but found that from synaptic i can only get 1.3.1. How then, can i install 1.3.8? i went to the link above, but can't find anything that i can use (or maybe i'm missing something?)



TIA and Regards,
Edwin

---

### Post by GeneralZod on 2006-01-25
[QUOTE=edwin11]Hi, sorry, but i'm a newbie here.

i would like to install amorok 1.3.8, but found that from synaptic i can only get 1.3.1. How then, can i install 1.3.8? i went to the link above, but can't find anything that i can use (or maybe i'm missing something?)



TIA and Regards,
Edwin[/QUOTE]

Add the apt source to your sources.list:

```

deb http://kubuntu.org/packages/amarok-1.3.8 breezy main

```

There are numerous guides to adding repositories dotted around the place :)

---

### Post by Havoc on 2006-01-25
Open up Synaptic, go to "Settings" ----> "Repositories" -----> "Add" ------> "Custom" and copy this into the "APT Line"

```
deb http://kubuntu.org/packages/amarok-1.3.8 breezy main
```

Press Ok, then press "Reload"

There you go. ;)

---

### Post by edwin11 on 2006-01-25
Thanks guys! Woah that totally rocks! For a moment i was starting to look up on how to compile from source! (Some more i'll have to compile libtag 1.4)

BTW, slightly digressing, when i entered the new repository and reloaded, i get the following error message:

> W: GPG error: [http://kubuntu.org](http://kubuntu.org) breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

Don't know if that matters or not 'cos i still managed to update amarok, but what do they mean anyway?

Thanks again!



Regards,
Edwin

---

### Post by INMCM on 2006-01-25
It's a verification thing. Just bring up a console and go:

```
wget http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg
```

```
sudo apt-key add kubuntu-packages-jriddell-key.gpg
```

That'll make it so the packages you get from that repo are signed.

---

### Post by edwin11 on 2006-01-25
hmmm ok... now i don't get the error for the amarok source, but still getting the other one:

> W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

Any idea?



Thanks and Regards,
Edwin

---

