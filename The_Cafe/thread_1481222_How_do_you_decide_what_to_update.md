---
title: "How do you decide what to update?"
date: 2010-05-12
forum: The Cafe
---

### Post by gabriella on 2010-05-12
Just curious... How do you decided what updates to install? I don't so much mean what one should or should not update but do you have a strategy for deciding. I look at all the possible updates think OMG and leave it till later!!

---

### Post by mikewhatever on 2010-05-12
I usually install the security and the recommended updates, which should be the default settings. New releases usually get loads of updates for the first few months, anyway, when is 'till later'? :P

---

### Post by gabriella on 2010-05-12
> **mikewhatever said:**
> I usually install the security and the recommended updates, which should be the default settings. New releases usually get loads of updates for the first few months, anyway, when is 'till later'? :P

But the list of recommended updates is huge, most of which for things I never use. "till later" is until I can sit down and scroll down the list and decide which might possibly affect me. I admit I don't do it nearly as often as I should!

---

### Post by 98cwitr on 2010-05-12
i install everything

---

### Post by Excedio on 2010-05-12
> **98cwitr said:**
> i install everything
 
 
[COLOR=white]|||||||||||||||||||||[/COLOR]^

---

### Post by RiceMonster on 2010-05-12
The updates in Ubuntu are almost always bug and security fixes, so it's a good idea to update everything.

---

### Post by chickengirl on 2010-05-12
I take a look at the list to see what kind of updates I'm getting today, then install them all.

Really, IMO, it's best practice to install all updates unless you have a specific reason *not* to.

---

### Post by Phrea on 2010-05-12
> **98cwitr said:**
> i install everything

+1

---

### Post by MarcusW on 2010-05-12
> **gabriella said:**
> But the list of recommended updates is huge, most of which for things I never use. "till later" is until I can sit down and scroll down the list and decide which might possibly affect me. I admit I don't do it nearly as often as I should!

Since it only updates programs you have installed, I'm guessing all updats kinda affect you.

---

### Post by descendent87 on 2010-05-12
I'm nearly always on development versions of ubuntu so I check a few times a day and install everything. Even when on stable releases I install all updates. Usually they've released an update for a reason (eg bug fixing/security) so it's a good idea just to install them

---

### Post by gabriella on 2010-05-12
> **MarcusW said:**
> Since it only updates programs you have installed, I'm guessing all updats kinda affect you.

Hmmm maybe you're all right and I should install everything? It's just there's lots of things installed that I've never used or likely too. Checking right now if I installed everything it would take up 300MB of disk space. Thats what I wonder about.

---

### Post by Penguin Guy on 2010-05-12
I update whatever the computer tells me to - the computer knows best.

---

### Post by mikewhatever on 2010-05-12
> **gabriella said:**
> Hmmm maybe you're all right and I should install everything? It's just there's lots of things installed that I've never used or likely too. Checking right now if I installed everything it would take up 300MB of disk space. Thats what I wonder about.

Interesting. 300MB is a lot for something that's only been out two weeks ago. Can you post the output of the following to see what's getting updated: **sudo apt-get -s upgrade**
The commands should not install anything, since -s is there fro simulation.

---

### Post by Viva on 2010-05-12
I always install all the updates other than those from third party repositories like playdeb.

---

### Post by swoll1980 on 2010-05-12
> **mikewhatever said:**
> Interesting. 300MB is a lot for something that's only been out two weeks ago. Can you post the output of the following to see what's getting updated: **sudo apt-get -s upgrade**
The commands should not install anything, since -s is there fro simulation.

The entire binary for all the programs that are being patched have to be downloaded. In Ubuntu, at least as far as I know there is no way to patch the existing versions of those files without replacing them completely with the new file. I think that's how it works. I could be wrong.

---

### Post by mikewhatever on 2010-05-12
> **swoll1980 said:**
> The entire binary for all the programs that are being patched have to be downloaded. In Ubuntu, at least as far as I know there is no way to patch the existing versions of those files without replacing them completely with the new file. I think that's how it works. I could be wrong.

I think you are right. It's just that I can see how 300MB in two weeks can be a little shocking to a new user.

---

### Post by chessnerd on 2010-05-12
I just update everything as soon as I get it. I should probably be more selective about some things, but I've rarely encountered issues with new updates.

Especially with Lucid, I've found the updates make it better and better. Something during the boot processes wasn't working well on my laptop. It was slow, Plymouth didn't seem to load properly, and sometimes GDM wouldn't start. A few days later, after some updates, everything works great now. I don't know what, of the 20 or so updates in the list, fixed it, but I'm glad it works now.

---

### Post by gabriella on 2010-05-12
> **mikewhatever said:**
> Interesting. 300MB is a lot for something that's only been out two weeks ago. Can you post the output of the following to see what's getting updated: **sudo apt-get -s upgrade**
The commands should not install anything, since -s is there fro simulation.


Well I admit I do need ..some.. updates! but maybe not all of them? 
Here goes.......

libglib2.0-0 libglib2.0-data libgnome-desktop-2-11 libgomp1 libgssapi-krb5-2 libgstreamer-plugins-base0.10-0 libgtk2.0-0
  libgtk2.0-bin libgtk2.0-common libgudev-1.0-0 libhtml-parser-perl libibus1 libindicate-gtk1 libindicate3 libk5crypto3
  libkpathsea4 libkrb5-3 libkrb5support0 libmetacity0 libmysqlclient16 libnautilus-extension1 libnss3-1d libpng12-0
  libpoppler-glib4 libpoppler5 libpostproc51 libpq5 libpulse-browse0 libpulse-mainloop-glib0 libpulse0 libpurple-bin
  libpurple0 libpython2.6 libsmbclient libssl0.9.8 libstdc++6 libswscale0 libthai-data libthai0 libudev0 libvorbis0a
  libxml2 libxml2-utils linux-firmware linux-libc-dev metacity metacity-common mysql-common nautilus nautilus-data ntpdate
  nvidia-common obexd-client openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core
  openoffice.org-draw openoffice.org-emailmerge openoffice.org-gnome openoffice.org-gtk openoffice.org-impress
  openoffice.org-math openoffice.org-style-human openoffice.org-writer openssl poppler-utils pulseaudio
  pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-udev pulseaudio-module-x11
  pulseaudio-utils python python-apport python-avahi python-ibus python-libxml2 python-minimal python-problem-report
  python-uno python2.6 python2.6-minimal rsyslog samba-common samba-common-bin same-gnome smbclient sudo
  system-tools-backends sysv-rc sysvinit-utils telepathy-gabble totem totem-common totem-mozilla totem-plugins
  transmission-common transmission-gtk ttf-opensymbol tzdata ubuntu-xsplash-artwork udev uno-libs3 update-manager
  update-manager-core upstart ure x11-common xsane xsane-common xulrunner-1.9.1 xulrunner-1.9.1-gnome-support
247 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
Inst dpkg [1.15.4ubuntu2] (1.15.4ubuntu2.1 Ubuntu:9.10/karmic-updates)
Conf dpkg (1.15.4ubuntu2.1 Ubuntu:9.10/karmic-updates)
Inst gzip [1.3.12-8ubuntu1] (1.3.12-8ubuntu1.1 Ubuntu:9.10/karmic-updates)
Conf gzip (1.3.12-8ubuntu1.1 Ubuntu:9.10/karmic-updates)
Inst libc-bin [2.10.1-0ubuntu15] (2.10.1-0ubuntu16 Ubuntu:9.10/karmic-updates) [libc6 ]
Conf libc-bin (2.10.1-0ubuntu16 Ubuntu:9.10/karmic-updates) [libc6 ]
Inst libc6 [2.10.1-0ubuntu15] (2.10.1-0ubuntu16 Ubuntu:9.10/karmic-updates) [libc6-i686 on libc6] [libc6-i686 libc6-dev ]
Conf libc6 (2.10.1-0ubuntu16 Ubuntu:9.10/karmic-updates) [libc6-i686 libc6-dev ]
Inst libc6-i686 [2.10.1-0ubuntu15] (2.10.1-0ubuntu16 Ubuntu:9.10/karmic-updates) [libc6-dev ]
Inst libc-dev-bin [2.10.1-0ubuntu15] (2.10.1-0ubuntu16 Ubuntu:9.10/karmic-updates) [libc6-dev ]
Inst libc6-dev [2.10.1-0ubuntu15] (2.10.1-0ubuntu16 Ubuntu:9.10/karmic-updates)
Inst linux-libc-dev [2.6.31-14.48] (2.6.31-21.59 Ubuntu:9.10/karmic-updates)
Inst libgomp1 [4.4.1-4ubuntu8] (4.4.1-4ubuntu9 Ubuntu:9.10/karmic-updates) []
Inst gcc-4.4-base [4.4.1-4ubuntu8] (4.4.1-4ubuntu9 Ubuntu:9.10/karmic-updates) [libstdc++6 gcc-4.4 libgcc1 cpp-4.4 ]
Conf gcc-4.4-base (4.4.1-4ubuntu9 Ubuntu:9.10/karmic-updates) [libstdc++6 gcc-4.4 libgcc1 cpp-4.4 ]
Inst libgcc1 [1:4.4.1-4ubuntu8] (1:4.4.1-4ubuntu9 Ubuntu:9.10/karmic-updates) [libstdc++6 gcc-4.4 cpp-4.4 ]
Conf libgcc1 (1:4.4.1-4ubuntu9 Ubuntu:9.10/karmic-updates) [libstdc++6 gcc-4.4 cpp-4.4 ]
Inst cpp-4.4 [4.4.1-4ubuntu8] (4.4.1-4ubuntu9 Ubuntu:9.10/karmic-updates) [libstdc++6 gcc-4.4 ]
Inst gcc-4.4 [4.4.1-4ubuntu8] (4.4.1-4ubuntu9 Ubuntu:9.10/karmic-updates) [libstdc++6 ]
Inst libstdc++6 [4.4.1-4ubuntu8] (4.4.1-4ubuntu9 Ubuntu:9.10/karmic-updates)
Conf libstdc++6 (4.4.1-4ubuntu9 Ubuntu:9.10/karmic-updates)
Inst binutils [2.20-0ubuntu1] (2.20-0ubuntu2 Ubuntu:9.10/karmic-updates)
Inst tzdata [2009o-1ubuntu2] (2010i-0ubuntu0.9.10 Ubuntu:9.10/karmic-updates)
Conf tzdata (2010i-0ubuntu0.9.10 Ubuntu:9.10/karmic-updates)
Inst libpython2.6 [2.6.4~rc2-0ubuntu1] (2.6.4-0ubuntu3 Ubuntu:9.10/karmic-updates) []
Inst python2.6 [2.6.4~rc2-0ubuntu1] (2.6.4-0ubuntu3 Ubuntu:9.10/karmic-updates) []
Inst libssl0.9.8 [0.9.8g-16ubuntu3] (0.9.8g-16ubuntu3.1 Ubuntu:9.10/karmic-updates) []
Conf libssl0.9.8 (0.9.8g-16ubuntu3.1 Ubuntu:9.10/karmic-updates) []
Inst python2.6-minimal [2.6.4~rc2-0ubuntu1] (2.6.4-0ubuntu3 Ubuntu:9.10/karmic-updates)
Conf python2.6-minimal (2.6.4-0ubuntu3 Ubuntu:9.10/karmic-updates)
Inst python [2.6.4~rc1-0ubuntu1] (2.6.4-0ubuntu1 Ubuntu:9.10/karmic-updates) []
Inst python-minimal [2.6.4~rc1-0ubuntu1] (2.6.4-0ubuntu1 Ubuntu:9.10/karmic-updates)
Conf python-minimal (2.6.4-0ubuntu1 Ubuntu:9.10/karmic-updates)
Inst sysvinit-utils [2.87dsf-4ubuntu11] (2.87dsf-4ubuntu12 Ubuntu:9.10/karmic-updates)
Conf sysvinit-utils (2.87dsf-4ubuntu12 Ubuntu:9.10/karmic-updates)
Inst sysv-rc [2.87dsf-4ubuntu11] (2.87dsf-4ubuntu12 Ubuntu:9.10/karmic-updates)
Conf sysv-rc (2.87dsf-4ubuntu12 Ubuntu:9.10/karmic-updates)
Inst initscripts [2.87dsf-4ubuntu11] (2.87dsf-4ubuntu12 Ubuntu:9.10/karmic-updates)
Conf initscripts (2.87dsf-4ubuntu12 Ubuntu:9.10/karmic-updates)
Inst upstart [0.6.3-10] (0.6.3-11 Ubuntu:9.10/karmic-updates)
Conf upstart (0.6.3-11 Ubuntu:9.10/karmic-updates)
Inst x11-common [1:7.4+3ubuntu7] (1:7.4+3ubuntu10 Ubuntu:9.10/karmic-updates)
Inst libavahi-common-data [0.6.25-1ubuntu5] (0.6.25-1ubuntu5.1 Ubuntu:9.10/karmic-updates)
Inst libavahi-common3 [0.6.25-1ubuntu5] (0.6.25-1ubuntu5.1 Ubuntu:9.10/karmic-updates)
Inst libavahi-client3 [0.6.25-1ubuntu5] (0.6.25-1ubuntu5.1 Ubuntu:9.10/karmic-updates)
Inst libgssapi-krb5-2 [1.7dfsg~beta3-1] (1.7dfsg~beta3-1ubuntu0.5 Ubuntu:9.10/karmic-updates) []
Inst libkrb5-3 [1.7dfsg~beta3-1] (1.7dfsg~beta3-1ubuntu0.5 Ubuntu:9.10/karmic-updates) []
Inst libkrb5support0 [1.7dfsg~beta3-1] (1.7dfsg~beta3-1ubuntu0.5 Ubuntu:9.10/karmic-updates)
Inst libk5crypto3 [1.7dfsg~beta3-1] (1.7dfsg~beta3-1ubuntu0.5 Ubuntu:9.10/karmic-updates)
Inst libcups2 [1.4.1-5ubuntu2] (1.4.1-5ubuntu2.4 Ubuntu:9.10/karmic-updates)
Inst libcupscgi1 [1.4.1-5ubuntu2] (1.4.1-5ubuntu2.4 Ubuntu:9.10/karmic-updates)
Inst libcupsdriver1 [1.4.1-5ubuntu2] (1.4.1-5ubuntu2.4 Ubuntu:9.10/karmic-updates)
Inst libpng12-0 [1.2.37-1] (1.2.37-1ubuntu0.1 Ubuntu:9.10/karmic-updates)
Inst libcupsimage2 [1.4.1-5ubuntu2] (1.4.1-5ubuntu2.4 Ubuntu:9.10/karmic-updates)
Inst libcupsmime1 [1.4.1-5ubuntu2] (1.4.1-5ubuntu2.4 Ubuntu:9.10/karmic-updates)
Inst libcupsppdc1 [1.4.1-5ubuntu2] (1.4.1-5ubuntu2.4 Ubuntu:9.10/karmic-updates)
Inst libxml2 [2.7.5.dfsg-1ubuntu1] (2.7.5.dfsg-1ubuntu1.1 Ubuntu:9.10/karmic-updates)
Inst libpoppler5 [0.12.0-0ubuntu2] (0.12.0-0ubuntu2.1 Ubuntu:9.10/karmic-updates)
Inst poppler-utils [0.12.0-0ubuntu2] (0.12.0-0ubuntu2.1 Ubuntu:9.10/karmic-updates)
Inst cups-common [1.4.1-5ubuntu2] (1.4.1-5ubuntu2.4 Ubuntu:9.10/karmic-updates)
Inst cups-bsd [1.4.1-5ubuntu2] (1.4.1-5ubuntu2.4 Ubuntu:9.10/karmic-updates) []
Inst adduser [3.110ubuntu6] (3.110ubuntu7 Ubuntu:9.10/karmic-updates) []
Inst cups-client [1.4.1-5ubuntu2] (1.4.1-5ubuntu2.4 Ubuntu:9.10/karmic-updates)
Inst cups [1.4.1-5ubuntu2] (1.4.1-5ubuntu2.4 Ubuntu:9.10/karmic-updates)
Inst foomatic-filters [4.0.3-0ubuntu2] (4.0.3-0ubuntu2.2 Ubuntu:9.10/karmic-updates)
Inst openoffice.org-emailmerge [1:3.1.1-5ubuntu1] (1:3.1.1-5ubuntu1.1 Ubuntu:9.10/karmic-updates)
Inst libudev0 [147~-6] (147~-6.1 Ubuntu:9.10/karmic-updates)
Conf libudev0 (147~-6.1 Ubuntu:9.10/karmic-updates)
Inst dhcp3-client [3.1.2-1ubuntu7] (3.1.2-1ubuntu7.1 Ubuntu:9.10/karmic-updates) []
Inst dhcp3-common [3.1.2-1ubuntu7] (3.1.2-1ubuntu7.1 Ubuntu:9.10/karmic-updates)
Inst ifupdown [0.6.8ubuntu21] (0.6.8ubuntu21.2 Ubuntu:9.10/karmic-updates)
Inst libglib2.0-0 [2.22.2-0ubuntu1] (2.22.3-0ubuntu1 Ubuntu:9.10/karmic-updates)
Inst libglib2.0-data [2.22.2-0ubuntu1] (2.22.3-0ubuntu1 Ubuntu:9.10/karmic-updates)
Inst rsyslog [4.2.0-2ubuntu5] (4.2.0-2ubuntu5.1 Ubuntu:9.10/karmic-updates)
Inst fuse-utils [2.7.4-1.1ubuntu4] (2.7.4-1.1ubuntu4.3 Ubuntu:9.10/karmic-updates) []
Inst libfuse2 [2.7.4-1.1ubuntu4] (2.7.4-1.1ubuntu4.3 Ubuntu:9.10/karmic-updates)
Inst udev [147~-6] (147~-6.1 Ubuntu:9.10/karmic-updates)
Inst apparmor [2.3.1+1403-0ubuntu27] (2.3.1+1403-0ubuntu27.3 Ubuntu:9.10/karmic-updates)
Inst libapparmor1 [2.3.1+1403-0ubuntu27] (2.3.1+1403-0ubuntu27.3 Ubuntu:9.10/karmic-updates)
Inst libapparmor-perl [2.3.1+1403-0ubuntu27] (2.3.1+1403-0ubuntu27.3 Ubuntu:9.10/karmic-updates)
Inst apparmor-utils [2.3.1+1403-0ubuntu27] (2.3.1+1403-0ubuntu27.3 Ubuntu:9.10/karmic-updates)
Inst update-manager [1:0.126.6] (1:0.126.9 Ubuntu:9.10/karmic-updates) []
Inst update-manager-core [1:0.126.6] (1:0.126.9 Ubuntu:9.10/karmic-updates)
Inst libcairo2 [1.8.8-2ubuntu1] (1.8.8-2ubuntu1.1 Ubuntu:9.10/karmic-updates)
Inst libgail-common [2.18.3-1] (2.18.3-1ubuntu2.2 Ubuntu:9.10/karmic-updates) []
Inst libgail18 [2.18.3-1] (2.18.3-1ubuntu2.2 Ubuntu:9.10/karmic-updates) []
Inst libgtk2.0-common [2.18.3-1] (2.18.3-1ubuntu2.2 Ubuntu:9.10/karmic-updates) []
Inst gtk2-engines-pixbuf [2.18.3-1] (2.18.3-1ubuntu2.2 Ubuntu:9.10/karmic-updates) []
Inst libgtk2.0-0 [2.18.3-1] (2.18.3-1ubuntu2.2 Ubuntu:9.10/karmic-updates)
Inst gnome-games-common [1:2.28.0-0ubuntu1] (1:2.28.0-0ubuntu3 Ubuntu:9.10/karmic-updates)
Inst aisleriot [1:2.28.0-0ubuntu1] (1:2.28.0-0ubuntu3 Ubuntu:9.10/karmic-updates)
Inst app-install-data-partner [12.9.10] (12.9.10.3 Ubuntu:9.10/karmic-updates)
Inst python-problem-report [1.9.3-0ubuntu4] (1.9.3-0ubuntu4.2 Ubuntu:9.10/karmic-updates)
Inst python-apport [1.9.3-0ubuntu4] (1.9.3-0ubuntu4.2 Ubuntu:9.10/karmic-updates)
Inst apport [1.9.3-0ubuntu4] (1.9.3-0ubuntu4.2 Ubuntu:9.10/karmic-updates)
Inst apport-gtk [1.9.3-0ubuntu4] (1.9.3-0ubuntu4.2 Ubuntu:9.10/karmic-updates)
Inst avahi-autoipd [0.6.25-1ubuntu5] (0.6.25-1ubuntu5.1 Ubuntu:9.10/karmic-updates)
Inst libavahi-core6 [0.6.25-1ubuntu5] (0.6.25-1ubuntu5.1 Ubuntu:9.10/karmic-updates)
Inst libexpat1 [2.0.1-4ubuntu1] (2.0.1-4ubuntu1.1 Ubuntu:9.10/karmic-updates)
Inst avahi-daemon [0.6.25-1ubuntu5] (0.6.25-1ubuntu5.1 Ubuntu:9.10/karmic-updates)
Inst libgstreamer-plugins-base0.10-0 [0.10.25-2ubuntu1] (0.10.25-2ubuntu1.2 Ubuntu:9.10/karmic-updates)
Inst libnautilus-extension1 [1:2.28.1-0ubuntu1] (1:2.28.1-0ubuntu3 Ubuntu:9.10/karmic-updates)
Inst libbrasero-media0 [2.28.1-0ubuntu1] (2.28.2-0ubuntu1 Ubuntu:9.10/karmic-updates)
Inst libgudev-1.0-0 [1:147~-6] (1:147~-6.1 Ubuntu:9.10/karmic-updates)
Inst libvorbis0a [1.2.0.dfsg-6] (1.2.0.dfsg-6ubuntu0.1 Ubuntu:9.10/karmic-updates)
Inst gstreamer0.10-plugins-base [0.10.25-2ubuntu1] (0.10.25-2ubuntu1.2 Ubuntu:9.10/karmic-updates)
Inst brasero [2.28.1-0ubuntu1] (2.28.2-0ubuntu1 Ubuntu:9.10/karmic-updates)
Inst checkbox-gtk [0.8.5] (0.8.6 Ubuntu:9.10/karmic-updates) []
Inst checkbox [0.8.5] (0.8.6 Ubuntu:9.10/karmic-updates)
Inst libdecoration0 [1:0.8.4-0ubuntu2] (1:0.8.4-0ubuntu2.1 Ubuntu:9.10/karmic-updates)
Inst libgnome-desktop-2-11 [1:2.28.1-0ubuntu2] (1:2.28.1-0ubuntu3 Ubuntu:9.10/karmic-updates)
Inst metacity-common [1:2.28.0-0ubuntu1] (1:2.28.0-0ubuntu2 Ubuntu:9.10/karmic-updates)
Inst libmetacity0 [1:2.28.0-0ubuntu1] (1:2.28.0-0ubuntu2 Ubuntu:9.10/karmic-updates)
Inst compiz-gnome [1:0.8.4-0ubuntu2] (1:0.8.4-0ubuntu2.1 Ubuntu:9.10/karmic-updates) []
Inst compiz-plugins [1:0.8.4-0ubuntu2] (1:0.8.4-0ubuntu2.1 Ubuntu:9.10/karmic-updates) []
Inst compiz-core [1:0.8.4-0ubuntu2] (1:0.8.4-0ubuntu2.1 Ubuntu:9.10/karmic-updates) []
Inst compiz-wrapper [1:0.8.4-0ubuntu2] (1:0.8.4-0ubuntu2.1 Ubuntu:9.10/karmic-updates)
Inst compiz [1:0.8.4-0ubuntu2] (1:0.8.4-0ubuntu2.1 Ubuntu:9.10/karmic-updates)
Inst devicekit-disks [007-2ubuntu3] (007-2ubuntu6 Ubuntu:9.10/karmic-updates)
Inst devicekit-power [011-1ubuntu1] (011-1ubuntu2 Ubuntu:9.10/karmic-updates)
Inst libdevkit-power-gobject1 [011-1ubuntu1] (011-1ubuntu2 Ubuntu:9.10/karmic-updates)
Inst libempathy30 [2.28.1-1ubuntu1] (2.28.1.1-0ubuntu1 Ubuntu:9.10/karmic-updates) []
Inst libempathy-common [2.28.1-1ubuntu1] (2.28.1.1-0ubuntu1 Ubuntu:9.10/karmic-updates)
Inst libenchant1c2a [1.5.0-0ubuntu2] (1.5.0-0ubuntu3 Ubuntu:9.10/karmic-updates)
Inst libempathy-gtk28 [2.28.1-1ubuntu1] (2.28.1.1-0ubuntu1 Ubuntu:9.10/karmic-updates) []
Inst libempathy-gtk-common [2.28.1-1ubuntu1] (2.28.1.1-0ubuntu1 Ubuntu:9.10/karmic-updates)
Inst libindicate3 [0.2.3-0ubuntu1] (0.2.3-0ubuntu2 Ubuntu:9.10/karmic-updates)
Inst libindicate-gtk1 [0.2.3-0ubuntu1] (0.2.3-0ubuntu2 Ubuntu:9.10/karmic-updates)
Inst empathy [2.28.1-1ubuntu1] (2.28.1.1-0ubuntu1 Ubuntu:9.10/karmic-updates) []
Inst empathy-doc [2.28.1-1ubuntu1] (2.28.1.1-0ubuntu1 Ubuntu:9.10/karmic-updates)
Inst erlang-xmerl [1:13.b.1-dfsg-2ubuntu1] (1:13.b.1-dfsg-2ubuntu1.1 Ubuntu:9.10/karmic-updates) []
Inst erlang-syntax-tools [1:13.b.1-dfsg-2ubuntu1] (1:13.b.1-dfsg-2ubuntu1.1 Ubuntu:9.10/karmic-updates) []
Inst erlang-inets [1:13.b.1-dfsg-2ubuntu1] (1:13.b.1-dfsg-2ubuntu1.1 Ubuntu:9.10/karmic-updates) []
Inst erlang-mnesia [1:13.b.1-dfsg-2ubuntu1] (1:13.b.1-dfsg-2ubuntu1.1 Ubuntu:9.10/karmic-updates) []
Inst erlang-ssl [1:13.b.1-dfsg-2ubuntu1] (1:13.b.1-dfsg-2ubuntu1.1 Ubuntu:9.10/karmic-updates) []
Inst erlang-public-key [1:13.b.1-dfsg-2ubuntu1] (1:13.b.1-dfsg-2ubuntu1.1 Ubuntu:9.10/karmic-updates) []
Inst erlang-crypto [1:13.b.1-dfsg-2ubuntu1] (1:13.b.1-dfsg-2ubuntu1.1 Ubuntu:9.10/karmic-updates) []
Inst erlang-runtime-tools [1:13.b.1-dfsg-2ubuntu1] (1:13.b.1-dfsg-2ubuntu1.1 Ubuntu:9.10/karmic-updates) []
Inst erlang-base [1:13.b.1-dfsg-2ubuntu1] (1:13.b.1-dfsg-2ubuntu1.1 Ubuntu:9.10/karmic-updates)
Inst libevdocument1 [2.28.1-0ubuntu1] (2.28.1-0ubuntu1.2 Ubuntu:9.10/karmic-updates)
Inst libevview1 [2.28.1-0ubuntu1] (2.28.1-0ubuntu1.2 Ubuntu:9.10/karmic-updates)
Inst libkpathsea4 [2007.dfsg.2-7ubuntu1] (2007.dfsg.2-7ubuntu1.1 Ubuntu:9.10/karmic-updates)
Inst libpoppler-glib4 [0.12.0-0ubuntu2] (0.12.0-0ubuntu2.1 Ubuntu:9.10/karmic-updates)
Inst evince [2.28.1-0ubuntu1] (2.28.1-0ubuntu1.2 Ubuntu:9.10/karmic-updates)
Inst libnss3-1d [3.12.3.1-0ubuntu2] (3.12.6-0ubuntu0.9.10.2 Ubuntu:9.10/karmic-updates)
Inst evolution [2.28.1-0ubuntu1] (2.28.1-0ubuntu2 Ubuntu:9.10/karmic-updates) []
Inst evolution-common [2.28.1-0ubuntu1] (2.28.1-0ubuntu2 Ubuntu:9.10/karmic-updates)
Inst evolution-plugins [2.28.1-0ubuntu1] (2.28.1-0ubuntu2 Ubuntu:9.10/karmic-updates)
Inst gcalctool [5.28.1-0ubuntu1] (5.28.2-0ubuntu2 Ubuntu:9.10/karmic-updates)
Inst gdm [2.28.1-0ubuntu1] (2.28.1-0ubuntu2.1 Ubuntu:9.10/karmic-updates)
Inst libgimp2.0 [2.6.7-1ubuntu1] (2.6.7-1ubuntu1.1 Ubuntu:9.10/karmic-updates)
Inst gimp-data [2.6.7-1ubuntu1] (2.6.7-1ubuntu1.1 Ubuntu:9.10/karmic-updates)
Inst gimp [2.6.7-1ubuntu1] (2.6.7-1ubuntu1.1 Ubuntu:9.10/karmic-updates)
Inst glchess [1:2.28.0-0ubuntu1] (1:2.28.0-0ubuntu3 Ubuntu:9.10/karmic-updates)
Inst glines [1:2.28.0-0ubuntu1] (1:2.28.0-0ubuntu3 Ubuntu:9.10/karmic-updates)
Inst gnect [1:2.28.0-0ubuntu1] (1:2.28.0-0ubuntu3 Ubuntu:9.10/karmic-updates)
Inst gnibbles [1:2.28.0-0ubuntu1] (1:2.28.0-0ubuntu3 Ubuntu:9.10/karmic-updates)
Inst gnobots2 [1:2.28.0-0ubuntu1] (1:2.28.0-0ubuntu3 Ubuntu:9.10/karmic-updates)
Inst gnome-about [1:2.28.1-0ubuntu2] (1:2.28.1-0ubuntu3 Ubuntu:9.10/karmic-updates) []
Inst gnome-desktop-data [1:2.28.1-0ubuntu2] (1:2.28.1-0ubuntu3 Ubuntu:9.10/karmic-updates)
Inst gnome-blackjack [1:2.28.0-0ubuntu1] (1:2.28.0-0ubuntu3 Ubuntu:9.10/karmic-updates)
Inst gnome-sudoku [1:2.28.0-0ubuntu1] (1:2.28.0-0ubuntu3 Ubuntu:9.10/karmic-updates)
Inst libclutter-gtk-0.10-0 [0.10.2-0ubuntu1] (0.10.2-0ubuntu2 Ubuntu:9.10/karmic-updates)
Inst gnometris [1:2.28.0-0ubuntu1] (1:2.28.0-0ubuntu3 Ubuntu:9.10/karmic-updates)
Inst gnomine [1:2.28.0-0ubuntu1] (1:2.28.0-0ubuntu3 Ubuntu:9.10/karmic-updates)
Inst gnotravex [1:2.28.0-0ubuntu1] (1:2.28.0-0ubuntu3 Ubuntu:9.10/karmic-updates)
Inst gnotski [1:2.28.0-0ubuntu1] (1:2.28.0-0ubuntu3 Ubuntu:9.10/karmic-updates)
Inst gtali [1:2.28.0-0ubuntu1] (1:2.28.0-0ubuntu3 Ubuntu:9.10/karmic-updates)
Inst iagno [1:2.28.0-0ubuntu1] (1:2.28.0-0ubuntu3 Ubuntu:9.10/karmic-updates)
Inst gnome-mahjongg [1:2.28.0-0ubuntu1] (1:2.28.0-0ubuntu3 Ubuntu:9.10/karmic-updates)
Inst same-gnome [1:2.28.0-0ubuntu1] (1:2.28.0-0ubuntu3 Ubuntu:9.10/karmic-updates)
Inst gnome-games [1:2.28.0-0ubuntu1] (1:2.28.0-0ubuntu3 Ubuntu:9.10/karmic-updates)
Inst gnome-screensaver [2.28.0-0ubuntu3] (2.28.0-0ubuntu3.5 Ubuntu:9.10/karmic-updates)
Inst libasound2 [1.0.20-3ubuntu6] (1.0.20-3ubuntu6.1 Ubuntu:9.10/karmic-updates)
Inst gstreamer0.10-alsa [0.10.25-2ubuntu1] (0.10.25-2ubuntu1.2 Ubuntu:9.10/karmic-updates)
Inst gstreamer0.10-plugins-base-apps [0.10.25-2ubuntu1] (0.10.25-2ubuntu1.2 Ubuntu:9.10/karmic-updates)
Inst gstreamer0.10-x [0.10.25-2ubuntu1] (0.10.25-2ubuntu1.2 Ubuntu:9.10/karmic-updates)
Inst gtk2-engines [1:2.18.4-1ubuntu1] (1:2.18.4-1ubuntu2 Ubuntu:9.10/karmic-updates)
Inst gtk2-engines-murrine [0.90.3-1ubuntu1] (0.90.3-1ubuntu2 Ubuntu:9.10/karmic-updates)
Inst libibus1 [1.2.0.20090927-2ubuntu1] (1.2.0.20090927-2ubuntu2 Ubuntu:9.10/karmic-updates)
Inst ibus [1.2.0.20090927-2ubuntu1] (1.2.0.20090927-2ubuntu2 Ubuntu:9.10/karmic-updates) []
Inst python-ibus [1.2.0.20090927-2ubuntu1] (1.2.0.20090927-2ubuntu2 Ubuntu:9.10/karmic-updates)
Inst ibus-gtk [1.2.0.20090927-2ubuntu1] (1.2.0.20090927-2ubuntu2 Ubuntu:9.10/karmic-updates)
Inst jockey-gtk [0.5.5-0ubuntu2] (0.5.5-0ubuntu3 Ubuntu:9.10/karmic-updates) []
Inst jockey-common [0.5.5-0ubuntu2] (0.5.5-0ubuntu3 Ubuntu:9.10/karmic-updates)
Inst kerneloops-daemon [0.12+git20090217-1ubuntu4] (0.12+git20090217-1ubuntu4.1 Ubuntu:9.10/karmic-updates)
Inst libaudiofile0 [0.2.6-7ubuntu2] (0.2.6-7ubuntu2.1 Ubuntu:9.10/karmic-updates)
Inst libavahi-glib1 [0.6.25-1ubuntu5] (0.6.25-1ubuntu5.1 Ubuntu:9.10/karmic-updates)
Inst libavahi-gobject0 [0.6.25-1ubuntu5] (0.6.25-1ubuntu5.1 Ubuntu:9.10/karmic-updates)
Inst libavahi-ui0 [0.6.25-1ubuntu5] (0.6.25-1ubuntu5.1 Ubuntu:9.10/karmic-updates)
Inst libavutil49 [4:0.5+svn20090706-2ubuntu2] (4:0.5+svn20090706-2ubuntu2.2 Ubuntu:9.10/karmic-updates)
Inst libavcodec52 [4:0.5+svn20090706-2ubuntu2] (4:0.5+svn20090706-2ubuntu2.2 Ubuntu:9.10/karmic-updates)
Inst libavformat52 [4:0.5+svn20090706-2ubuntu2] (4:0.5+svn20090706-2ubuntu2.2 Ubuntu:9.10/karmic-updates)
Inst libdvdnav4 [4.1.3-3] (4.1.3-3ubuntu1 Ubuntu:9.10/karmic-updates)
Inst libgd2-xpm [2.0.36~rc1~dfsg-3ubuntu1] (2.0.36~rc1~dfsg-3ubuntu1.9.10.1 Ubuntu:9.10/karmic-updates)
Inst libgtk2.0-bin [2.18.3-1] (2.18.3-1ubuntu2.2 Ubuntu:9.10/karmic-updates)
Inst libhtml-parser-perl [3.61-1] (3.61-1ubuntu0.1 Ubuntu:9.10/karmic-updates)
Inst mysql-common [5.1.37-1ubuntu5] (5.1.37-1ubuntu5.1 Ubuntu:9.10/karmic-updates)
Inst libmysqlclient16 [5.1.37-1ubuntu5] (5.1.37-1ubuntu5.1 Ubuntu:9.10/karmic-updates)
Inst libpostproc51 [4:0.5+svn20090706-2ubuntu2] (4:0.5+svn20090706-2ubuntu2.2 Ubuntu:9.10/karmic-updates)
Inst libpq5 [8.4.1-1] (8.4.3-0ubuntu9.10.1 Ubuntu:9.10/karmic-updates)
Inst pulseaudio-utils [1:0.9.19-0ubuntu4] (1:0.9.19-0ubuntu4.1 Ubuntu:9.10/karmic-updates) []
Inst pulseaudio-module-udev [1:0.9.19-0ubuntu4] (1:0.9.19-0ubuntu4.1 Ubuntu:9.10/karmic-updates) []
Inst pulseaudio-module-gconf [1:0.9.19-0ubuntu4] (1:0.9.19-0ubuntu4.1 Ubuntu:9.10/karmic-updates) []
Inst pulseaudio-module-bluetooth [1:0.9.19-0ubuntu4] (1:0.9.19-0ubuntu4.1 Ubuntu:9.10/karmic-updates) []
Inst pulseaudio-esound-compat [1:0.9.19-0ubuntu4] (1:0.9.19-0ubuntu4.1 Ubuntu:9.10/karmic-updates) []
Inst pulseaudio-module-x11 [1:0.9.19-0ubuntu4] (1:0.9.19-0ubuntu4.1 Ubuntu:9.10/karmic-updates) []
Inst pulseaudio [1:0.9.19-0ubuntu4] (1:0.9.19-0ubuntu4.1 Ubuntu:9.10/karmic-updates) []
Inst libpulse-mainloop-glib0 [1:0.9.19-0ubuntu4] (1:0.9.19-0ubuntu4.1 Ubuntu:9.10/karmic-updates) []
Inst libpulse-browse0 [1:0.9.19-0ubuntu4] (1:0.9.19-0ubuntu4.1 Ubuntu:9.10/karmic-updates) []
Inst libpulse0 [1:0.9.19-0ubuntu4] (1:0.9.19-0ubuntu4.1 Ubuntu:9.10/karmic-updates)
Inst libpurple-bin [1:2.6.2-1ubuntu7] (1:2.6.2-1ubuntu7.2 Ubuntu:9.10/karmic-updates)
Inst libpurple0 [1:2.6.2-1ubuntu7] (1:2.6.2-1ubuntu7.2 Ubuntu:9.10/karmic-updates)
Inst libsmbclient [2:3.4.0-3ubuntu5] (2:3.4.0-3ubuntu5.6 Ubuntu:9.10/karmic-updates)
Inst libswscale0 [4:0.5+svn20090706-2ubuntu2] (4:0.5+svn20090706-2ubuntu2.2 Ubuntu:9.10/karmic-updates)
Inst libthai-data [0.1.12-1] (0.1.12-1ubuntu0.2 Ubuntu:9.10/karmic-updates)
Inst libthai0 [0.1.12-1] (0.1.12-1ubuntu0.2 Ubuntu:9.10/karmic-updates)
Inst libxml2-utils [2.7.5.dfsg-1ubuntu1] (2.7.5.dfsg-1ubuntu1.1 Ubuntu:9.10/karmic-updates)
Inst linux-firmware [1.24] (1.26 Ubuntu:9.10/karmic-updates)
Inst metacity [1:2.28.0-0ubuntu1] (1:2.28.0-0ubuntu2 Ubuntu:9.10/karmic-updates)
Inst nautilus-data [1:2.28.1-0ubuntu1] (1:2.28.1-0ubuntu3 Ubuntu:9.10/karmic-updates)
Inst nautilus [1:2.28.1-0ubuntu1] (1:2.28.1-0ubuntu3 Ubuntu:9.10/karmic-updates)
Inst ntpdate [1:4.2.4p6+dfsg-1ubuntu5] (1:4.2.4p6+dfsg-1ubuntu5.1 Ubuntu:9.10/karmic-updates)
Inst nvidia-common [0.2.15] (0.2.15.1 Ubuntu:9.10/karmic-updates)
Inst obexd-client [0.14-0ubuntu1] (0.14-0ubuntu1.1 Ubuntu:9.10/karmic-updates)
Inst ure [1.5.1+OOo3.1.1-5ubuntu1] (1.5.1+OOo3.1.1-5ubuntu1.1 Ubuntu:9.10/karmic-updates) []
Inst uno-libs3 [1.5.1+OOo3.1.1-5ubuntu1] (1.5.1+OOo3.1.1-5ubuntu1.1 Ubuntu:9.10/karmic-updates)
Inst openoffice.org-calc [1:3.1.1-5ubuntu1] (1:3.1.1-5ubuntu1.1 Ubuntu:9.10/karmic-updates) []
Inst openoffice.org-impress [1:3.1.1-5ubuntu1] (1:3.1.1-5ubuntu1.1 Ubuntu:9.10/karmic-updates) []
Inst openoffice.org-draw [1:3.1.1-5ubuntu1] (1:3.1.1-5ubuntu1.1 Ubuntu:9.10/karmic-updates) []
Inst openoffice.org-gtk [1:3.1.1-5ubuntu1] (1:3.1.1-5ubuntu1.1 Ubuntu:9.10/karmic-updates) []
Inst openoffice.org-gnome [1:3.1.1-5ubuntu1] (1:3.1.1-5ubuntu1.1 Ubuntu:9.10/karmic-updates) []
Inst python-uno [1:3.1.1-5ubuntu1] (1:3.1.1-5ubuntu1.1 Ubuntu:9.10/karmic-updates) []
Inst openoffice.org-math [1:3.1.1-5ubuntu1] (1:3.1.1-5ubuntu1.1 Ubuntu:9.10/karmic-updates) []
Inst openoffice.org-style-human [1:3.1.1-5ubuntu1] (1:3.1.1-5ubuntu1.1 Ubuntu:9.10/karmic-updates) []
Inst openoffice.org-common [1:3.1.1-5ubuntu1] (1:3.1.1-5ubuntu1.1 Ubuntu:9.10/karmic-updates) []
Inst ttf-opensymbol [1:3.1.1-5ubuntu1] (1:3.1.1-5ubuntu1.1 Ubuntu:9.10/karmic-updates) []
Inst openoffice.org-writer [1:3.1.1-5ubuntu1] (1:3.1.1-5ubuntu1.1 Ubuntu:9.10/karmic-updates) []
Inst openoffice.org-base-core [1:3.1.1-5ubuntu1] (1:3.1.1-5ubuntu1.1 Ubuntu:9.10/karmic-updates) []
Inst openoffice.org-core [1:3.1.1-5ubuntu1] (1:3.1.1-5ubuntu1.1 Ubuntu:9.10/karmic-updates)
Inst openssl [0.9.8g-16ubuntu3] (0.9.8g-16ubuntu3.1 Ubuntu:9.10/karmic-updates)
Inst python-avahi [0.6.25-1ubuntu5] (0.6.25-1ubuntu5.1 Ubuntu:9.10/karmic-updates)
Inst python-libxml2 [2.7.5.dfsg-1ubuntu1] (2.7.5.dfsg-1ubuntu1.1 Ubuntu:9.10/karmic-updates)
Inst smbclient [2:3.4.0-3ubuntu5] (2:3.4.0-3ubuntu5.6 Ubuntu:9.10/karmic-updates) []
Inst samba-common [2:3.4.0-3ubuntu5] (2:3.4.0-3ubuntu5.6 Ubuntu:9.10/karmic-updates)
Inst samba-common-bin [2:3.4.0-3ubuntu5] (2:3.4.0-3ubuntu5.6 Ubuntu:9.10/karmic-updates)
Inst sudo [1.7.0-1ubuntu2] (1.7.0-1ubuntu2.2 Ubuntu:9.10/karmic-updates)
Inst system-tools-backends [2.8.2-1] (2.8.2-1ubuntu1 Ubuntu:9.10/karmic-updates)
Inst telepathy-gabble [0.8.7-1] (0.8.7-1ubuntu1 Ubuntu:9.10/karmic-updates)
Inst totem-plugins [2.28.1-0ubuntu4] (2.28.2-0ubuntu3 Ubuntu:9.10/karmic-updates) []
Inst totem-common [2.28.1-0ubuntu4] (2.28.2-0ubuntu3 Ubuntu:9.10/karmic-updates) []
Inst totem [2.28.1-0ubuntu4] (2.28.2-0ubuntu3 Ubuntu:9.10/karmic-updates)
Inst totem-mozilla [2.28.1-0ubuntu4] (2.28.2-0ubuntu3 Ubuntu:9.10/karmic-updates)
Inst transmission-gtk [1.75-0ubuntu2] (1.75-0ubuntu2.2 Ubuntu:9.10/karmic-updates) []
Inst transmission-common [1.75-0ubuntu2] (1.75-0ubuntu2.2 Ubuntu:9.10/karmic-updates)
Inst ubuntu-xsplash-artwork [0.8.4-0ubuntu1] (0.8.5-0ubuntu1 Ubuntu:9.10/karmic-updates)
Inst xsane [0.996-2ubuntu1] (0.996-2ubuntu1.1 Ubuntu:9.10/karmic-updates) []
Inst xsane-common [0.996-2ubuntu1] (0.996-2ubuntu1.1 Ubuntu:9.10/karmic-updates)
Inst xulrunner-1.9.1-gnome-support [1.9.1.3+build1+nobinonly-0ubuntu6] (1.9.1.9+nobinonly-0ubuntu0.9.10.1 Ubuntu:9.10/karmic-updates) []
Inst xulrunner-1.9.1 [1.9.1.3+build1+nobinonly-0ubuntu6] (1.9.1.9+nobinonly-0ubuntu0.9.10.1 Ubuntu:9.10/karmic-updates)
Inst acroread [9.3.1-1karmic1] (9.3.2-karmic1 Ubuntu:9.10/karmic)
Inst evolution-documentation-en [2.28.1-0ubuntu1] (2.28.1-0ubuntu2 Ubuntu:9.10/karmic-updates)
Inst evolution-indicator [0.2.4-0ubuntu2] (0.2.4-0ubuntu3.1 Ubuntu:9.10/karmic-updates)
Conf libc6-i686 (2.10.1-0ubuntu16 Ubuntu:9.10/karmic-updates)
Conf libc-dev-bin (2.10.1-0ubuntu16 Ubuntu:9.10/karmic-updates)
Conf linux-libc-dev (2.6.31-21.59 Ubuntu:9.10/karmic-updates)
Conf libc6-dev (2.10.1-0ubuntu16 Ubuntu:9.10/karmic-updates)
Conf libgomp1 (4.4.1-4ubuntu9 Ubuntu:9.10/karmic-updates)
Conf cpp-4.4 (4.4.1-4ubuntu9 Ubuntu:9.10/karmic-updates)
Conf binutils (2.20-0ubuntu2 Ubuntu:9.10/karmic-updates)
Conf gcc-4.4 (4.4.1-4ubuntu9 Ubuntu:9.10/karmic-updates)
Conf python2.6 (2.6.4-0ubuntu3 Ubuntu:9.10/karmic-updates)
Conf libpython2.6 (2.6.4-0ubuntu3 Ubuntu:9.10/karmic-updates)
Conf python (2.6.4-0ubuntu1 Ubuntu:9.10/karmic-updates)
Conf x11-common (1:7.4+3ubuntu10 Ubuntu:9.10/karmic-updates)
Conf libavahi-common-data (0.6.25-1ubuntu5.1 Ubuntu:9.10/karmic-updates)
Conf libavahi-common3 (0.6.25-1ubuntu5.1 Ubuntu:9.10/karmic-updates)
Conf libavahi-client3 (0.6.25-1ubuntu5.1 Ubuntu:9.10/karmic-updates)
Conf libkrb5support0 (1.7dfsg~beta3-1ubuntu0.5 Ubuntu:9.10/karmic-updates)
Conf libk5crypto3 (1.7dfsg~beta3-1ubuntu0.5 Ubuntu:9.10/karmic-updates)
Conf libkrb5-3 (1.7dfsg~beta3-1ubuntu0.5 Ubuntu:9.10/karmic-updates)
Conf libgssapi-krb5-2 (1.7dfsg~beta3-1ubuntu0.5 Ubuntu:9.10/karmic-updates)
Conf libcups2 (1.4.1-5ubuntu2.4 Ubuntu:9.10/karmic-updates)
Conf libcupscgi1 (1.4.1-5ubuntu2.4 Ubuntu:9.10/karmic-updates)
Conf libcupsdriver1 (1.4.1-5ubuntu2.4 Ubuntu:9.10/karmic-updates)
Conf libpng12-0 (1.2.37-1ubuntu0.1 Ubuntu:9.10/karmic-updates)
Conf libcupsimage2 (1.4.1-5ubuntu2.4 Ubuntu:9.10/karmic-updates)
Conf libcupsmime1 (1.4.1-5ubuntu2.4 Ubuntu:9.10/karmic-updates)
Conf libcupsppdc1 (1.4.1-5ubuntu2.4 Ubuntu:9.10/karmic-updates)
Conf libxml2 (2.7.5.dfsg-1ubuntu1.1 Ubuntu:9.10/karmic-updates)
Conf libpoppler5 (0.12.0-0ubuntu2.1 Ubuntu:9.10/karmic-updates)
Conf poppler-utils (0.12.0-0ubuntu2.1 Ubuntu:9.10/karmic-updates)
Conf cups-common (1.4.1-5ubuntu2.4 Ubuntu:9.10/karmic-updates)
Conf adduser (3.110ubuntu7 Ubuntu:9.10/karmic-updates)
Conf cups-client (1.4.1-5ubuntu2.4 Ubuntu:9.10/karmic-updates)
Conf cups-bsd (1.4.1-5ubuntu2.4 Ubuntu:9.10/karmic-updates)
Conf cups (1.4.1-5ubuntu2.4 Ubuntu:9.10/karmic-updates)
Conf foomatic-filters (4.0.3-0ubuntu2.2 Ubuntu:9.10/karmic-updates)
Conf openoffice.org-emailmerge (1:3.1.1-5ubuntu1.1 Ubuntu:9.10/karmic-updates)
Conf dhcp3-common (3.1.2-1ubuntu7.1 Ubuntu:9.10/karmic-updates)
Conf dhcp3-client (3.1.2-1ubuntu7.1 Ubuntu:9.10/karmic-updates)
Conf ifupdown (0.6.8ubuntu21.2 Ubuntu:9.10/karmic-updates)
Conf libglib2.0-0 (2.22.3-0ubuntu1 Ubuntu:9.10/karmic-updates)
Conf libglib2.0-data (2.22.3-0ubuntu1 Ubuntu:9.10/karmic-updates)
Conf rsyslog (4.2.0-2ubuntu5.1 Ubuntu:9.10/karmic-updates)
Conf libfuse2 (2.7.4-1.1ubuntu4.3 Ubuntu:9.10/karmic-updates)
Conf udev (147~-6.1 Ubuntu:9.10/karmic-updates)
Conf fuse-utils (2.7.4-1.1ubuntu4.3 Ubuntu:9.10/karmic-updates)
Conf apparmor (2.3.1+1403-0ubuntu27.3 Ubuntu:9.10/karmic-updates)
Conf libapparmor1 (2.3.1+1403-0ubuntu27.3 Ubuntu:9.10/karmic-updates)
Conf libapparmor-perl (2.3.1+1403-0ubuntu27.3 Ubuntu:9.10/karmic-updates)
Conf apparmor-utils (2.3.1+1403-0ubuntu27.3 Ubuntu:9.10/karmic-updates)
Conf update-manager-core (1:0.126.9 Ubuntu:9.10/karmic-updates)
Conf update-manager (1:0.126.9 Ubuntu:9.10/karmic-updates)
Conf libcairo2 (1.8.8-2ubuntu1.1 Ubuntu:9.10/karmic-updates)
Conf libgtk2.0-common (2.18.3-1ubuntu2.2 Ubuntu:9.10/karmic-updates)
Conf libgtk2.0-0 (2.18.3-1ubuntu2.2 Ubuntu:9.10/karmic-updates)
Conf libgail18 (2.18.3-1ubuntu2.2 Ubuntu:9.10/karmic-updates)
Conf libgail-common (2.18.3-1ubuntu2.2 Ubuntu:9.10/karmic-updates)
Conf gtk2-engines-pixbuf (2.18.3-1ubuntu2.2 Ubuntu:9.10/karmic-updates)
Conf gnome-games-common (1:2.28.0-0ubuntu3 Ubuntu:9.10/karmic-updates)
Conf aisleriot (1:2.28.0-0ubuntu3 Ubuntu:9.10/karmic-updates)
Conf app-install-data-partner (12.9.10.3 Ubuntu:9.10/karmic-updates)
Conf python-problem-report (1.9.3-0ubuntu4.2 Ubuntu:9.10/karmic-updates)
Conf python-apport (1.9.3-0ubuntu4.2 Ubuntu:9.10/karmic-updates)
Conf apport (1.9.3-0ubuntu4.2 Ubuntu:9.10/karmic-updates)
Conf apport-gtk (1.9.3-0ubuntu4.2 Ubuntu:9.10/karmic-updates)
Conf avahi-autoipd (0.6.25-1ubuntu5.1 Ubuntu:9.10/karmic-updates)
Conf libavahi-core6 (0.6.25-1ubuntu5.1 Ubuntu:9.10/karmic-updates)
Conf libexpat1 (2.0.1-4ubuntu1.1 Ubuntu:9.10/karmic-updates)
Conf avahi-daemon (0.6.25-1ubuntu5.1 Ubuntu:9.10/karmic-updates)
Conf libgstreamer-plugins-base0.10-0 (0.10.25-2ubuntu1.2 Ubuntu:9.10/karmic-updates)
Conf libnautilus-extension1 (1:2.28.1-0ubuntu3 Ubuntu:9.10/karmic-updates)
Conf libbrasero-media0 (2.28.2-0ubuntu1 Ubuntu:9.10/karmic-updates)
Conf libgudev-1.0-0 (1:147~-6.1 Ubuntu:9.10/karmic-updates)
Conf libvorbis0a (1.2.0.dfsg-6ubuntu0.1 Ubuntu:9.10/karmic-updates)
Conf gstreamer0.10-plugins-base (0.10.25-2ubuntu1.2 Ubuntu:9.10/karmic-updates)
Conf brasero (2.28.2-0ubuntu1 Ubuntu:9.10/karmic-updates)
Conf checkbox (0.8.6 Ubuntu:9.10/karmic-updates)
Conf checkbox-gtk (0.8.6 Ubuntu:9.10/karmic-updates)
Conf libdecoration0 (1:0.8.4-0ubuntu2.1 Ubuntu:9.10/karmic-updates)
Conf libgnome-desktop-2-11 (1:2.28.1-0ubuntu3 Ubuntu:9.10/karmic-updates)
Conf metacity-common (1:2.28.0-0ubuntu2 Ubuntu:9.10/karmic-updates)
Conf libmetacity0 (1:2.28.0-0ubuntu2 Ubuntu:9.10/karmic-updates)
Conf compiz-wrapper (1:0.8.4-0ubuntu2.1 Ubuntu:9.10/karmic-updates)
Conf compiz-core (1:0.8.4-0ubuntu2.1 Ubuntu:9.10/karmic-updates)
Conf compiz-plugins (1:0.8.4-0ubuntu2.1 Ubuntu:9.10/karmic-updates)
Conf compiz-gnome (1:0.8.4-0ubuntu2.1 Ubuntu:9.10/karmic-updates)
Conf compiz (1:0.8.4-0ubuntu2.1 Ubuntu:9.10/karmic-updates)
Conf devicekit-disks (007-2ubuntu6 Ubuntu:9.10/karmic-updates)
Conf libdevkit-power-gobject1 (011-1ubuntu2 Ubuntu:9.10/karmic-updates)
Conf devicekit-power (011-1ubuntu2 Ubuntu:9.10/karmic-updates)
Conf libempathy-common (2.28.1.1-0ubuntu1 Ubuntu:9.10/karmic-updates)
Conf libempathy30 (2.28.1.1-0ubuntu1 Ubuntu:9.10/karmic-updates)
Conf libenchant1c2a (1.5.0-0ubuntu3 Ubuntu:9.10/karmic-updates)
Conf libempathy-gtk-common (2.28.1.1-0ubuntu1 Ubuntu:9.10/karmic-updates)
Conf libempathy-gtk28 (2.28.1.1-0ubuntu1 Ubuntu:9.10/karmic-updates)
Conf libindicate3 (0.2.3-0ubuntu2 Ubuntu:9.10/karmic-updates)
Conf libindicate-gtk1 (0.2.3-0ubuntu2 Ubuntu:9.10/karmic-updates)
Conf empathy-doc (2.28.1.1-0ubuntu1 Ubuntu:9.10/karmic-updates)
Conf empathy (2.28.1.1-0ubuntu1 Ubuntu:9.10/karmic-updates)
Conf erlang-base (1:13.b.1-dfsg-2ubuntu1.1 Ubuntu:9.10/karmic-updates)
Conf erlang-xmerl (1:13.b.1-dfsg-2ubuntu1.1 Ubuntu:9.10/karmic-updates)
Conf erlang-syntax-tools (1:13.b.1-dfsg-2ubuntu1.1 Ubuntu:9.10/karmic-updates)
Conf erlang-mnesia (1:13.b.1-dfsg-2ubuntu1.1 Ubuntu:9.10/karmic-updates)
Conf erlang-crypto (1:13.b.1-dfsg-2ubuntu1.1 Ubuntu:9.10/karmic-updates)
Conf erlang-public-key (1:13.b.1-dfsg-2ubuntu1.1 Ubuntu:9.10/karmic-updates)
Conf erlang-runtime-tools (1:13.b.1-dfsg-2ubuntu1.1 Ubuntu:9.10/karmic-updates)
Conf erlang-ssl (1:13.b.1-dfsg-2ubuntu1.1 Ubuntu:9.10/karmic-updates)
Conf erlang-inets (1:13.b.1-dfsg-2ubuntu1.1 Ubuntu:9.10/karmic-updates)
Conf libevdocument1 (2.28.1-0ubuntu1.2 Ubuntu:9.10/karmic-updates)
Conf libevview1 (2.28.1-0ubuntu1.2 Ubuntu:9.10/karmic-updates)
Conf libkpathsea4 (2007.dfsg.2-7ubuntu1.1 Ubuntu:9.10/karmic-updates)
Conf libpoppler-glib4 (0.12.0-0ubuntu2.1 Ubuntu:9.10/karmic-updates)
Conf evince (2.28.1-0ubuntu1.2 Ubuntu:9.10/karmic-updates)
Conf libnss3-1d (3.12.6-0ubuntu0.9.10.2 Ubuntu:9.10/karmic-updates)
Conf evolution-common (2.28.1-0ubuntu2 Ubuntu:9.10/karmic-updates)
Conf evolution (2.28.1-0ubuntu2 Ubuntu:9.10/karmic-updates)
Conf evolution-plugins (2.28.1-0ubuntu2 Ubuntu:9.10/karmic-updates)
Conf gcalctool (5.28.2-0ubuntu2 Ubuntu:9.10/karmic-updates)
Conf gdm (2.28.1-0ubuntu2.1 Ubuntu:9.10/karmic-updates)
Conf libgimp2.0 (2.6.7-1ubuntu1.1 Ubuntu:9.10/karmic-updates)
Conf gimp-data (2.6.7-1ubuntu1.1 Ubuntu:9.10/karmic-updates)
Conf gimp (2.6.7-1ubuntu1.1 Ubuntu:9.10/karmic-updates)
Conf glchess (1:2.28.0-0ubuntu3 Ubuntu:9.10/karmic-updates)
Conf glines (1:2.28.0-0ubuntu3 Ubuntu:9.10/karmic-updates)
Conf gnect (1:2.28.0-0ubuntu3 Ubuntu:9.10/karmic-updates)
Conf gnibbles (1:2.28.0-0ubuntu3 Ubuntu:9.10/karmic-updates)
Conf gnobots2 (1:2.28.0-0ubuntu3 Ubuntu:9.10/karmic-updates)
Conf gnome-desktop-data (1:2.28.1-0ubuntu3 Ubuntu:9.10/karmic-updates)
Conf gnome-about (1:2.28.1-0ubuntu3 Ubuntu:9.10/karmic-updates)
Conf gnome-blackjack (1:2.28.0-0ubuntu3 Ubuntu:9.10/karmic-updates)
Conf gnome-sudoku (1:2.28.0-0ubuntu3 Ubuntu:9.10/karmic-updates)
Conf libclutter-gtk-0.10-0 (0.10.2-0ubuntu2 Ubuntu:9.10/karmic-updates)
Conf gnometris (1:2.28.0-0ubuntu3 Ubuntu:9.10/karmic-updates)
Conf gnomine (1:2.28.0-0ubuntu3 Ubuntu:9.10/karmic-updates)
Conf gnotravex (1:2.28.0-0ubuntu3 Ubuntu:9.10/karmic-updates)
Conf gnotski (1:2.28.0-0ubuntu3 Ubuntu:9.10/karmic-updates)
Conf gtali (1:2.28.0-0ubuntu3 Ubuntu:9.10/karmic-updates)
Conf iagno (1:2.28.0-0ubuntu3 Ubuntu:9.10/karmic-updates)
Conf gnome-mahjongg (1:2.28.0-0ubuntu3 Ubuntu:9.10/karmic-updates)
Conf same-gnome (1:2.28.0-0ubuntu3 Ubuntu:9.10/karmic-updates)
Conf gnome-games (1:2.28.0-0ubuntu3 Ubuntu:9.10/karmic-updates)
Conf gnome-screensaver (2.28.0-0ubuntu3.5 Ubuntu:9.10/karmic-updates)
Conf libasound2 (1.0.20-3ubuntu6.1 Ubuntu:9.10/karmic-updates)
Conf gstreamer0.10-alsa (0.10.25-2ubuntu1.2 Ubuntu:9.10/karmic-updates)
Conf gstreamer0.10-plugins-base-apps (0.10.25-2ubuntu1.2 Ubuntu:9.10/karmic-updates)
Conf gstreamer0.10-x (0.10.25-2ubuntu1.2 Ubuntu:9.10/karmic-updates)
Conf gtk2-engines (1:2.18.4-1ubuntu2 Ubuntu:9.10/karmic-updates)
Conf gtk2-engines-murrine (0.90.3-1ubuntu2 Ubuntu:9.10/karmic-updates)
Conf libibus1 (1.2.0.20090927-2ubuntu2 Ubuntu:9.10/karmic-updates)
Conf python-ibus (1.2.0.20090927-2ubuntu2 Ubuntu:9.10/karmic-updates)
Conf ibus (1.2.0.20090927-2ubuntu2 Ubuntu:9.10/karmic-updates)
Conf ibus-gtk (1.2.0.20090927-2ubuntu2 Ubuntu:9.10/karmic-updates)
Conf jockey-common (0.5.5-0ubuntu3 Ubuntu:9.10/karmic-updates)
Conf jockey-gtk (0.5.5-0ubuntu3 Ubuntu:9.10/karmic-updates)
Conf kerneloops-daemon (0.12+git20090217-1ubuntu4.1 Ubuntu:9.10/karmic-updates)
Conf libaudiofile0 (0.2.6-7ubuntu2.1 Ubuntu:9.10/karmic-updates)
Conf libavahi-glib1 (0.6.25-1ubuntu5.1 Ubuntu:9.10/karmic-updates)
Conf libavahi-gobject0 (0.6.25-1ubuntu5.1 Ubuntu:9.10/karmic-updates)
Conf libavahi-ui0 (0.6.25-1ubuntu5.1 Ubuntu:9.10/karmic-updates)
Conf libavutil49 (4:0.5+svn20090706-2ubuntu2.2 Ubuntu:9.10/karmic-updates)
Conf libavcodec52 (4:0.5+svn20090706-2ubuntu2.2 Ubuntu:9.10/karmic-updates)
Conf libavformat52 (4:0.5+svn20090706-2ubuntu2.2 Ubuntu:9.10/karmic-updates)
Conf libdvdnav4 (4.1.3-3ubuntu1 Ubuntu:9.10/karmic-updates)
Conf libgd2-xpm (2.0.36~rc1~dfsg-3ubuntu1.9.10.1 Ubuntu:9.10/karmic-updates)
Conf libgtk2.0-bin (2.18.3-1ubuntu2.2 Ubuntu:9.10/karmic-updates)
Conf libhtml-parser-perl (3.61-1ubuntu0.1 Ubuntu:9.10/karmic-updates)
Conf mysql-common (5.1.37-1ubuntu5.1 Ubuntu:9.10/karmic-updates)
Conf libmysqlclient16 (5.1.37-1ubuntu5.1 Ubuntu:9.10/karmic-updates)
Conf libpostproc51 (4:0.5+svn20090706-2ubuntu2.2 Ubuntu:9.10/karmic-updates)
Conf libpq5 (8.4.3-0ubuntu9.10.1 Ubuntu:9.10/karmic-updates)
Conf libpulse0 (1:0.9.19-0ubuntu4.1 Ubuntu:9.10/karmic-updates)
Conf libpulse-browse0 (1:0.9.19-0ubuntu4.1 Ubuntu:9.10/karmic-updates)
Conf pulseaudio-utils (1:0.9.19-0ubuntu4.1 Ubuntu:9.10/karmic-updates)
Conf pulseaudio (1:0.9.19-0ubuntu4.1 Ubuntu:9.10/karmic-updates)
Conf pulseaudio-module-udev (1:0.9.19-0ubuntu4.1 Ubuntu:9.10/karmic-updates)
Conf pulseaudio-module-gconf (1:0.9.19-0ubuntu4.1 Ubuntu:9.10/karmic-updates)
Conf pulseaudio-module-bluetooth (1:0.9.19-0ubuntu4.1 Ubuntu:9.10/karmic-updates)
Conf pulseaudio-esound-compat (1:0.9.19-0ubuntu4.1 Ubuntu:9.10/karmic-updates)
Conf pulseaudio-module-x11 (1:0.9.19-0ubuntu4.1 Ubuntu:9.10/karmic-updates)
Conf libpulse-mainloop-glib0 (1:0.9.19-0ubuntu4.1 Ubuntu:9.10/karmic-updates)
Conf libpurple-bin (1:2.6.2-1ubuntu7.2 Ubuntu:9.10/karmic-updates)
Conf libpurple0 (1:2.6.2-1ubuntu7.2 Ubuntu:9.10/karmic-updates)
Conf libsmbclient (2:3.4.0-3ubuntu5.6 Ubuntu:9.10/karmic-updates)
Conf libswscale0 (4:0.5+svn20090706-2ubuntu2.2 Ubuntu:9.10/karmic-updates)
Conf libthai-data (0.1.12-1ubuntu0.2 Ubuntu:9.10/karmic-updates)
Conf libthai0 (0.1.12-1ubuntu0.2 Ubuntu:9.10/karmic-updates)
Conf libxml2-utils (2.7.5.dfsg-1ubuntu1.1 Ubuntu:9.10/karmic-updates)
Conf linux-firmware (1.26 Ubuntu:9.10/karmic-updates)
Conf metacity (1:2.28.0-0ubuntu2 Ubuntu:9.10/karmic-updates)
Conf nautilus-data (1:2.28.1-0ubuntu3 Ubuntu:9.10/karmic-updates)
Conf nautilus (1:2.28.1-0ubuntu3 Ubuntu:9.10/karmic-updates)
Conf ntpdate (1:4.2.4p6+dfsg-1ubuntu5.1 Ubuntu:9.10/karmic-updates)
Conf nvidia-common (0.2.15.1 Ubuntu:9.10/karmic-updates)
Conf obexd-client (0.14-0ubuntu1.1 Ubuntu:9.10/karmic-updates)
Conf uno-libs3 (1.5.1+OOo3.1.1-5ubuntu1.1 Ubuntu:9.10/karmic-updates)
Conf ure (1.5.1+OOo3.1.1-5ubuntu1.1 Ubuntu:9.10/karmic-updates)
Conf openoffice.org-style-human (1:3.1.1-5ubuntu1.1 Ubuntu:9.10/karmic-updates)
Conf openoffice.org-common (1:3.1.1-5ubuntu1.1 Ubuntu:9.10/karmic-updates)
Conf ttf-opensymbol (1:3.1.1-5ubuntu1.1 Ubuntu:9.10/karmic-updates)
Conf openoffice.org-core (1:3.1.1-5ubuntu1.1 Ubuntu:9.10/karmic-updates)
Conf openoffice.org-base-core (1:3.1.1-5ubuntu1.1 Ubuntu:9.10/karmic-updates)
Conf openoffice.org-calc (1:3.1.1-5ubuntu1.1 Ubuntu:9.10/karmic-updates)
Conf openoffice.org-draw (1:3.1.1-5ubuntu1.1 Ubuntu:9.10/karmic-updates)
Conf openoffice.org-impress (1:3.1.1-5ubuntu1.1 Ubuntu:9.10/karmic-updates)
Conf openoffice.org-gtk (1:3.1.1-5ubuntu1.1 Ubuntu:9.10/karmic-updates)
Conf openoffice.org-gnome (1:3.1.1-5ubuntu1.1 Ubuntu:9.10/karmic-updates)
Conf python-uno (1:3.1.1-5ubuntu1.1 Ubuntu:9.10/karmic-updates)
Conf openoffice.org-math (1:3.1.1-5ubuntu1.1 Ubuntu:9.10/karmic-updates)
Conf openoffice.org-writer (1:3.1.1-5ubuntu1.1 Ubuntu:9.10/karmic-updates)
Conf openssl (0.9.8g-16ubuntu3.1 Ubuntu:9.10/karmic-updates)
Conf python-avahi (0.6.25-1ubuntu5.1 Ubuntu:9.10/karmic-updates)
Conf python-libxml2 (2.7.5.dfsg-1ubuntu1.1 Ubuntu:9.10/karmic-updates)
Conf samba-common (2:3.4.0-3ubuntu5.6 Ubuntu:9.10/karmic-updates)
Conf smbclient (2:3.4.0-3ubuntu5.6 Ubuntu:9.10/karmic-updates)
Conf samba-common-bin (2:3.4.0-3ubuntu5.6 Ubuntu:9.10/karmic-updates)
Conf sudo (1.7.0-1ubuntu2.2 Ubuntu:9.10/karmic-updates)
Conf system-tools-backends (2.8.2-1ubuntu1 Ubuntu:9.10/karmic-updates)
Conf telepathy-gabble (0.8.7-1ubuntu1 Ubuntu:9.10/karmic-updates)
Conf totem-common (2.28.2-0ubuntu3 Ubuntu:9.10/karmic-updates)
Conf totem (2.28.2-0ubuntu3 Ubuntu:9.10/karmic-updates)
Conf totem-plugins (2.28.2-0ubuntu3 Ubuntu:9.10/karmic-updates)
Conf totem-mozilla (2.28.2-0ubuntu3 Ubuntu:9.10/karmic-updates)
Conf transmission-common (1.75-0ubuntu2.2 Ubuntu:9.10/karmic-updates)
Conf transmission-gtk (1.75-0ubuntu2.2 Ubuntu:9.10/karmic-updates)
Conf ubuntu-xsplash-artwork (0.8.5-0ubuntu1 Ubuntu:9.10/karmic-updates)
Conf xsane-common (0.996-2ubuntu1.1 Ubuntu:9.10/karmic-updates)
Conf xsane (0.996-2ubuntu1.1 Ubuntu:9.10/karmic-updates)
Conf xulrunner-1.9.1 (1.9.1.9+nobinonly-0ubuntu0.9.10.1 Ubuntu:9.10/karmic-updates)
Conf xulrunner-1.9.1-gnome-support (1.9.1.9+nobinonly-0ubuntu0.9.10.1 Ubuntu:9.10/karmic-updates)
Conf acroread (9.3.2-karmic1 Ubuntu:9.10/karmic)
Conf evolution-documentation-en (2.28.1-0ubuntu2 Ubuntu:9.10/karmic-updates)
Conf evolution-indicator (0.2.4-0ubuntu3.1 Ubuntu:9.10/karmic-updates)
Gabi1@pchome..

---

### Post by mikewhatever on 2010-05-12
OK, thanks for the output. As you are running Karmic, these are all the updates that accumulated since Oct 2009, including system files, programs and dependencies, interface tweaks, and so on. It should be safe to install all of them, and if you are on broadband, it probably won't take too long.
I usually install all of those right after the installing the OS to get it over with.

---

### Post by gabriella on 2010-05-12
> **mikewhatever said:**
> OK, thanks for the output. As you are running Karmic, these are all the updates that accumulated since Oct 2009, including system files, programs and dependencies, interface tweaks, and so on. It should be safe to install all of them, and if you are on broadband, it probably won't take too long.
I usually install all of those right after the installing the OS to get it over with.

OK so this looks normal then! I'm not worried about the time, my wifi's pretty fast, just I get stingy about disk space  ;)
Thanks

---

### Post by sanderella on 2010-05-12
> **98cwitr said:**
> i install everything

Me too. That way if you get problems a lot of other people do too, and so they are quickly sorted out.:)

---

### Post by Frogs Hair on 2010-05-12
All regular updates, but I look at them first . My machine is a but fussy about kernel updates , it works best if remove the Nvidia drivers first and reinstall after the kernel update.

---

### Post by mikewhatever on 2010-05-12
> **gabriella said:**
> OK so this looks normal then! I'm not worried about the time, my wifi's pretty fast, just I get stingy about disk space  ;)
Thanks

Well, disk space must be available to download and install updates. When done, you can reclaim most of the disk space by removing the downloaded packages.
```
sudo apt-get clean
```

---

### Post by gabriella on 2010-05-12
> **mikewhatever said:**
> Well, disk space must be available to download and install updates. When done, you can reclaim most of the disk space by removing the downloaded packages.
```
sudo apt-get clean
```

OK excuse me for being dense but what exactly does this do? The updates remain installed right? So What is being removed?

---

### Post by mikewhatever on 2010-05-12
> **gabriella said:**
> OK excuse me for being dense but what exactly does this do? The updates remain installed right? So What is being removed?

The command will delete the downloaded packages, the installation files, so to speak. The updates will remain installed.

---

### Post by 3rdalbum on 2010-05-12
> **mikewhatever said:**
> The command will delete the downloaded packages, the installation files, so to speak. The updates will remain installed.

The updates replace the old versions of the packages, too; so it's not like "OMG I'm going to lose 200 megabytes by installing these updates!"; each update might be the same as what you had earlier, plus twenty lines of code. So after installing the updates your system might take up a megabyte or two more space.

---

### Post by gabriella on 2010-05-13
> **3rdalbum said:**
> The updates replace the old versions of the packages, too; so it's not like "OMG I'm going to lose 200 megabytes by installing these updates!"; each update might be the same as what you had earlier, plus twenty lines of code. So after installing the updates your system might take up a megabyte or two more space.

OK thanks guys. I understand. I thought it seemed a little odd that each time there were updates XXX MB would be added and next time again and so on...

---

### Post by deanjm1963 on 2010-05-13
I update "when" updates are available. I try to look on the bright side and think that the updates aren't going to cause any breakage. The only time I've ever seen updates that broke something was back in Dapper Drake - 6.06 (about 2 days after it was released) ... a nasty nVidia bug that broke quite a few peoples puters ... a few hours later it was fixed ... that's what's so great about linux in general, if something is broken, there is a fix just around the corner ... 

If you're worried about updates in general just check the forums to see if there is any breakage regarding "updates", otherwise, most updates are beneficial. My 2 cents worth.

---

### Post by gabriella on 2010-05-16
Further question on this subject: Do I need Kerberos if I'm not on a network?

---

### Post by screaminj3sus on 2010-05-16
I update everything and I always have ppa's to get newer stuff (either that or I am testing alpha/beta ubuntu).

---

### Post by chriswyatt on 2010-05-16
It's a shame you can't just download the difference between the previous version and the new version, it would dramatically reduce load on the servers, only downside is that Ubuntu would have to host both the full download and just the patch by itself so it would take up a little more server space.

---

