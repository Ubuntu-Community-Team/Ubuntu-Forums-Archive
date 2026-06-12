---
title: "Muse can´t connect to Jack (Error Message)"
date: 2011-05-17
forum: Ubuntu Studio
---

### Post by Troubadix-der-Barde on 2011-05-17
Hi,

in Ubuntu Studio 11.04 is MusE1.1 in the repositorie. But I´m not able to start it. Gives me the error message: 
"MusE failed to find a Jack audio server.
MusE will continue without audio support (-a switch)!
If this was not intended check that Jack was started. If Jack was started check that it was started as the same user as MusE."

and in the terminal: 
"Denormal protection enabled.
no message buffer overruns
no message buffer overruns
unknown option character l
cannot connect to jack server
cannot create jack client"

Of course I started Jack and MusE as the same user. Also other programs (Ardour, ZynAdd, Rosegarden, ...) dont make big problems and work very well together with Jack.

I got the lowlatency-kernel by Alessio Igor Bogani (but already had the problem before).

What might that be? Any ideas?

Saludos

---

### Post by Pablo_F on 2011-05-18
Hi, 

See [https://bugs.launchpad.net/ubuntu/+source/muse/+bug/784919](https://bugs.launchpad.net/ubuntu/+source/muse/+bug/784919)

Cheers, Pablo

---

### Post by Troubadix-der-Barde on 2011-05-19
Thank you, seems to work.

Is there in any other field a problem to switch to the older version of jackd?

Saludos

---

### Post by Pablo_F on 2011-05-19
Hi, 

jackd1 is not an older version of jackd.

See [http://trac.jackaudio.org/wiki/Q_differenc_jack1_jack2](http://trac.jackaudio.org/wiki/Q_differenc_jack1_jack2)

Cheers! Pablo

---

### Post by Troubadix-der-Barde on 2011-05-19
Thank you. 

After a few testings I think, that Jackd1 in general works by far much more stable on my system. With Jackd2 sometimes I had X-runs as hell (about 10 per second), especially with the alsa-driver (firewire worked better). With Jackd1 don´t have that with the alsa-driver (I´m not at home, so I cannot test the firewire-driver).

Saludos y gracias otra vez.

---

### Post by Troubadix-der-Barde on 2011-05-19
Ok, spoken to soon. MusE didn´t want to create a Jack-Midi-Output (always crashed). And now (after about three or four times crashing) even doesn´t want to start anymore.

"Config file might be corrupted. Unkown shortcut: toggle_mi"

Even uninstalling and reinstalling MusE didn´t change that.

:(

---

### Post by jejeman on 2011-05-19
Try to purge it. Removing keeps config files.
apt-get purge

---

### Post by Troubadix-der-Barde on 2011-05-19
Thanks for the reply, but no. Doesn´t solve it. Still the same message.

Edith: I purged, then removed completely, then purged again and then reinstalled.

---

### Post by iiuu on 2011-05-21
Most of the time, start speechless. Messy personal thoughts like the wind, with 

only the fallen leaves in spring go to shuttle between prosperous and bleak. 

Gradually dismissed many memories of occasionally remind of, just in casual 

gently reveals the inmost once. ...
[www.prcwholesale.com](www.prcwholesale.com)

---

