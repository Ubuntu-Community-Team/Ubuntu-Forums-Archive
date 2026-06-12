---
title: "Wily Proposed"
date: 2015-05-14
forum: Ubuntu Development Version
---

### Post by QDR06VV9 on 2015-05-14
So feeling a little adventurous this morning, I enabled proposed.
```
The following packages have been kept back:
  ffmpeg gstreamer0.10-plugins-ugly gstreamer1.0-plugins-ugly
  gstreamer1.0-plugins-ugly-amr libavcodec-extra-56 libavcodec-ffmpeg56
  libavformat-ffmpeg56 libvlc5 libvlccore8 python-openssl vlc vlc-data vlc-nox
  vlc-plugin-pulse
The following packages will be upgraded:
  chromium-codecs-ffmpeg-extra firefox firefox-locale-en gcc-5-base
  gir1.2-atk-1.0 gir1.2-gtk-2.0 gir1.2-wnck-3.0 glib-networking
  glib-networking-common glib-networking-services gtk2-engines-pixbuf
  krb5-locales libasn1-8-heimdal libatk1.0-0 libatk1.0-data libatk1.0-dev
  libatomic1 libavcodec-extra libavdevice-ffmpeg56 libavfilter-ffmpeg5
  libavformat56 libavresample-ffmpeg2 libavresample2 libavutil-ffmpeg54
  libavutil54 libcairo-perl libcgi-pm-perl libcilkrts5 libestr0 libgail-common
  libgail18 libgcc1 libgfortran3 libglib-perl libglib2.0-0 libglib2.0-bin
  libglib2.0-data libglib2.0-dev libgomp1 libgssapi-krb5-2 libgssapi3-heimdal
  libgssdp-1.0-3 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common
  libhcrypto4-heimdal libheimbase1-heimdal libheimntlm0-heimdal
  libhx509-5-heimdal libipc-run-perl libitm1 libk5crypto3 libkrb5-26-heimdal
  libkrb5-3 libkrb5support0 liblsan0 libnet-dbus-perl libnet-ssleay-perl
  libperl5.20 libpostproc-ffmpeg53 libpulse-mainloop-glib0 libpulse0
  libpulsedsp libpython2.7 libpython2.7-minimal libpython2.7-stdlib
  libquadmath0 libroken18-heimdal libsqlite3-0 libssl1.0.0 libstdc++6
  libswresample-ffmpeg1 libswscale-ffmpeg3 libswscale3
  libtext-levenshtein-perl libtsan0 libubsan0 libwind0-heimdal libwnck-3-0
  libwnck-3-common openssl oxideqt-codecs-extra patchutils perl perl-base
  perl-modules pulseaudio pulseaudio-module-bluetooth pulseaudio-module-x11
  pulseaudio-utils python-six python2.7 python2.7-minimal python3-six
  qt-faststart ubuntu-drivers-common
96 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
Need to get 66.9 MB of archives.
After this operation, 546 kB of additional disk space will be used.
Do you want to continue? [Y/n] 

```
Upgrade and dist-upgrade and a reboot, All went well for now!
I have not found any breakage yet.
Regards

---

### Post by dino99 on 2015-05-14
by now there is not much packages in main, simply 'vivid' reaffected to 'wily'; upgrade are from 'proposed'

---

### Post by QDR06VV9 on 2015-05-14
> **dino99 said:**
> by now there is not much packages in main, simply 'vivid' reaffected to 'wily';_ upgrade are from 'proposed'_

Yes!;) As stated in the Title Thread **Proposed**.:)
Regards

---

### Post by ventrical on 2015-05-15
You are a true pioneer ! :)

Regards..

---

### Post by rrnbtter on 2015-05-15
Greetings,
I ran the entire Vivid cycle with Proposed enabled with no problem. I have continued this with Wily since changing the repos over to devel. I think that back in the Trusty cycle Canonical decided to keep the dependencies together with the "proposed" to stop the continual breakage. It has been smooth sailing since then. That being said I keep my Home on a separate partition which makes a reinstall easier. But then you already know that. The results is that these upgrade cycles are becoming somewhat mundane. Last cycle we had systemd and pkexe to play with, this go round should have some surprises also. The difference from the long past is that it will be ready for prime time before it shows. Hopefully nothing more than some annoyances.    
PS: keep an updated ISO handy just in case :)

---

### Post by QDR06VV9 on 2015-05-15
> **ventrical said:**
> You are a true pioneer ! :)

Regards..

Heh Heh Yes to be sure a true Daniel Boone!):P 

> The difference from the long past is that it will be ready for prime  time before it shows. Hopefully nothing more than some annoyances.    
PS: keep an updated ISO handy just in case :smile:
Words to live by.;)
Regards

---

### Post by rrnbtter on 2015-05-15
Greetings,
Small correction on my previous post. I did do a reinstall early in the Vivid cycle but can't remember the exact reason. I do know that it had to do with a no reboot for reasons I was unable to correct. This in spite of the fact that I am getting pretty good with safe mode and root access.  I keep a copy of Puppy Linux on my Home partition just to make things easier.

---

### Post by MikeMecanic on 2015-05-15
Feel good to see that I'm not the only one doing so.  When Software Updater is ain't showing any significant activity (It's was the case for a long period between B2 and Final Release), I open or enable in Software & Updates / Updates/ Pre-released Updates/ Vivid-proposed.  **Testing for me is related to playing and by doing so it's a good way to play in the developers backyard.**  But (knowing now that it's a dangerous approach) many of you will be happy, I stop doing it in Final release.  
If it's the meaning of <<* enabled proposed* >>?

Take care,

---

### Post by QDR06VV9 on 2015-05-25
Bear in mind that this is with Proposed enabled. (And on Mate)
Just a heads up, When I did my upgrade and dist-upgrade I encountered a partial upgrade(ubuntu-mate-core)!
Went ahead with the upgrade and dist-upgrade still did not pullin <ubuntu-mate-core>
But a manual install of <ubuntu-mate-core> did the job.
And after a reboot things are good!
Did not notice anything strange with Lubuntu just mate DE
Regards

---

