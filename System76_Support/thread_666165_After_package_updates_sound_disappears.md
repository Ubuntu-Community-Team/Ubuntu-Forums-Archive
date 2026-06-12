---
title: "After package updates sound disappears"
date: 2008-01-13
forum: System76 Support
---

### Post by Mung the Wicked on 2008-01-13
Hi.

I'm using a Serval running Gutsy Gibbon 7.10

About an hour or two ago, I said, "What the hell.  I'll just go ahead and install all these updates I keep getting notified about."  That was a mistake.  One reboot later and my sound disappeared completely -  I'm talking not even the little drum rattle during the login screen.

After reboot, the first time you left-click on the sound icon in the panel, you get this error message:
"The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu."

Then if you Right Click -> Open Volume Control, you'll get:
"No volume control GStreamer plugins and/or devices found."

The only sound-related entries in Device Manager seems to be:
ALSA Sequencer Device
ALSA Timer Device
OSS Sequencer Device
OSS Sequencer Device

These are the packages that I installed:
apturl (0.1ubuntu1) to 0.1ubuntu2
avahi-autoipd (0.6.20-2ubuntu3) to 0.6.20-2ubuntu3.1
avahi-daemon (0.6.20-2ubuntu3) to 0.6.20-2ubuntu3.1
bind9-host (1:9.4.1-P1-3) to 1:9.4.1-P1-3ubuntu1
clamav (0.91.2-3ubuntu2.1) to 0.91.2-3ubuntu2.2
clamav-base (0.91.2-3ubuntu2.1) to 0.91.2-3ubuntu2.2
clamav-freshclam (0.91.2-3ubuntu2.1) to 0.91.2-3ubuntu2.2
cupsys (1.3.2-1ubuntu7.1) to 1.3.2-1ubuntu7.5
cupsys-bsd (1.3.2-1ubuntu7.1) to 1.3.2-1ubuntu7.5
cupsys-client (1.3.2-1ubuntu7.1) to 1.3.2-1ubuntu7.5
cupsys-common (1.3.2-1ubuntu7.1) to 1.3.2-1ubuntu7.5
deskbar-applet (2.20.0-0ubuntu2) to 2.20.1-0ubuntu1
dnsutils (1:9.4.1-P1-3) to 1:9.4.1-P1-3ubuntu1
e2fslibs (1.40.2-1ubuntu1) to 1.40.2-1ubuntu1.1
e2fsprogs (1.40.2-1ubuntu1) to 1.40.2-1ubuntu1.1
evolution-data-server (1.12.1-0ubuntu1) to 1.12.1-0ubuntu2
evolution-data-server-common (1.12.1-0ubuntu1) to 1.12.1-0ubuntu2
findutils (4.2.31-1ubuntu2) to 4.2.31-1ubuntu2.1
firefox (2.0.0.8+2nobinonly-0ubuntu1) to 2.0.0.11+2nobinonly-0ubuntu0.7.10
firefox-gnome-support (2.0.0.8+2nobinonly-0ubuntu1) to 2.0.0.11+2nobinonly-0ubuntu0.7.10
foo2zjs (20070625-0ubuntu1) to 20070625-0ubuntu1.1
gdm (2.20.1-0ubuntu1) to 2.20.1-0ubuntu2
ghostscript (8.61.dfsg.1~svn8187-0ubuntu3.2) to 8.61.dfsg.1~svn8187-0ubuntu3.3
ghostscript-x (8.61.dfsg.1~svn8187-0ubuntu3.2) to 8.61.dfsg.1~svn8187-0ubuntu3.3
gimp (2.4.0~rc3-1ubuntu7) to 2.4.2-0ubuntu0.7.10.1
gimp-data (2.4.0~rc3-1ubuntu7) to 2.4.2-0ubuntu0.7.10.1
gimp-python (2.4.0~rc3-1ubuntu7) to 2.4.2-0ubuntu0.7.10.1
gnome-system-tools (2.20.0-0ubuntu1) to 2.20.0-0ubuntu2
gs-gpl (8.61.dfsg.1~svn8187-0ubuntu3.2) to 8.61.dfsg.1~svn8187-0ubuntu3.3
language-pack-en (1:7.10+20071012) to 1:7.10+20071120
language-pack-gnome-en (1:7.10+20071012) to 1:7.10+20071120
libapache2-mod-php5 (5.2.3-1ubuntu6.2) to 5.2.3-1ubuntu6.3
libavahi-client3 (0.6.20-2ubuntu3) to 0.6.20-2ubuntu3.1
libavahi-common-data (0.6.20-2ubuntu3) to 0.6.20-2ubuntu3.1
libavahi-common3 (0.6.20-2ubuntu3) to 0.6.20-2ubuntu3.1
libavahi-compat-libdnssd1 (0.6.20-2ubuntu3) to 0.6.20-2ubuntu3.1
libavahi-core5 (0.6.20-2ubuntu3) to 0.6.20-2ubuntu3.1
libavahi-glib1 (0.6.20-2ubuntu3) to 0.6.20-2ubuntu3.1
libbind9-30 (1:9.4.1-P1-3) to 1:9.4.1-P1-3ubuntu1
libblkid1 (1.40.2-1ubuntu1) to 1.40.2-1ubuntu1.1
libcairo2 (1.4.10-1ubuntu4) to 1.4.10-1ubuntu4.4
libcamel1.2-10 (1.12.1-0ubuntu1) to 1.12.1-0ubuntu2
libclamav2 (0.91.2-3ubuntu2.1) to 0.91.2-3ubuntu2.2
libcupsimage2 (1.3.2-1ubuntu7.1) to 1.3.2-1ubuntu7.5
libcupsys2 (1.3.2-1ubuntu7.1) to 1.3.2-1ubuntu7.5
libdb4.4 (4.4.20-8.1ubuntu3) to 4.4.20-8.1ubuntu3.1
libdns32 (1:9.4.1-P1-3) to 1:9.4.1-P1-3ubuntu1
libdvdcss2 (1.2.5-1) to 1.2.9-2medibuntu4
libebook1.2-9 (1.12.1-0ubuntu1) to 1.12.1-0ubuntu2
libecal1.2-7 (1.12.1-0ubuntu1) to 1.12.1-0ubuntu2
libedata-book1.2-2 (1.12.1-0ubuntu1) to 1.12.1-0ubuntu2
libedata-cal1.2-6 (1.12.1-0ubuntu1) to 1.12.1-0ubuntu2
libedataserver1.2-9 (1.12.1-0ubuntu1) to 1.12.1-0ubuntu2
libedataserverui1.2-8 (1.12.1-0ubuntu1) to 1.12.1-0ubuntu2
libegroupwise1.2-13 (1.12.1-0ubuntu1) to 1.12.1-0ubuntu2
libexchange-storage1.2-3 (1.12.1-0ubuntu1) to 1.12.1-0ubuntu2
libflac8 (1.1.4-3ubuntu1) to 1.1.4-3ubuntu1.1
libgimp2.0 (2.4.0~rc3-1ubuntu7) to 2.4.2-0ubuntu0.7.10.1
libgs8 (8.61.dfsg.1~svn8187-0ubuntu3.2) to 8.61.dfsg.1~svn8187-0ubuntu3.3
libisc32 (1:9.4.1-P1-3) to 1:9.4.1-P1-3ubuntu1
libisccc30 (1:9.4.1-P1-3) to 1:9.4.1-P1-3ubuntu1
libisccfg30 (1:9.4.1-P1-3) to 1:9.4.1-P1-3ubuntu1
libkpathsea4 (2007-12ubuntu3) to 2007-12ubuntu3.1
liblwres30 (1:9.4.1-P1-3) to 1:9.4.1-P1-3ubuntu1
libmono-cairo1.0-cil (1.2.4-6ubuntu6) to 1.2.4-6ubuntu6.1
libmono-corlib1.0-cil (1.2.4-6ubuntu6) to 1.2.4-6ubuntu6.1
libmono-corlib2.0-cil (1.2.4-6ubuntu6) to 1.2.4-6ubuntu6.1
libmono-data-tds2.0-cil (1.2.4-6ubuntu6) to 1.2.4-6ubuntu6.1
libmono-security2.0-cil (1.2.4-6ubuntu6) to 1.2.4-6ubuntu6.1
libmono-sharpzip2.84-cil (1.2.4-6ubuntu6) to 1.2.4-6ubuntu6.1
libmono-sqlite2.0-cil (1.2.4-6ubuntu6) to 1.2.4-6ubuntu6.1
libmono-system-data2.0-cil (1.2.4-6ubuntu6) to 1.2.4-6ubuntu6.1
libmono-system-web2.0-cil (1.2.4-6ubuntu6) to 1.2.4-6ubuntu6.1
libmono-system1.0-cil (1.2.4-6ubuntu6) to 1.2.4-6ubuntu6.1
libmono-system2.0-cil (1.2.4-6ubuntu6) to 1.2.4-6ubuntu6.1
libmono0 (1.2.4-6ubuntu6) to 1.2.4-6ubuntu6.1
libmono2.0-cil (1.2.4-6ubuntu6) to 1.2.4-6ubuntu6.1
libpcre3 (7.2-1ubuntu2) to 7.4-0ubuntu0.7.10.1
libpcrecpp0 (7.2-1ubuntu2) to 7.4-0ubuntu0.7.10.1
libperl5.8 (5.8.8-7ubuntu3) to 5.8.8-7ubuntu3.1
libpoppler-glib2 (0.6-0ubuntu2) to 0.6-0ubuntu2.1
libpoppler2 (0.6-0ubuntu2) to 0.6-0ubuntu2.1
libpq-dev (8.2.5-1.1) to 8.2.6-0ubuntu0.7.10
libpq5 (8.2.5-1.1) to 8.2.6-0ubuntu0.7.10
libpt-1.10.0 (1.10.10-0ubuntu2) to 1.10.10-0ubuntu2.1
libpt-plugins-alsa (1.10.10-0ubuntu2) to 1.10.10-0ubuntu2.1
libpt-plugins-v4l (1.10.10-0ubuntu2) to 1.10.10-0ubuntu2.1
libpt-plugins-v4l2 (1.10.10-0ubuntu2) to 1.10.10-0ubuntu2.1
libpurple0 (1:2.2.1-1ubuntu4) to 1:2.2.1-1ubuntu4.1
libsmbclient (3.0.26a-1ubuntu2) to 3.0.26a-1ubuntu2.3
libsnmp-base (5.3.1-6ubuntu2) to 5.3.1-6ubuntu2.1
libsnmp10 (5.3.1-6ubuntu2) to 5.3.1-6ubuntu2.1
libss2 (1.40.2-1ubuntu1) to 1.40.2-1ubuntu1.1
libuuid1 (1.40.2-1ubuntu1) to 1.40.2-1ubuntu1.1
linux-headers-2.6.22-14 (2.6.22-14.46) to 2.6.22-14.47
linux-headers-2.6.22-14-generic (2.6.22-14.46) to 2.6.22-14.47
linux-image-2.6.22-14-generic (2.6.22-14.46) to 2.6.22-14.47
linux-libc-dev (2.6.22-14.46) to 2.6.22-14.47
linux-ubuntu-modules-2.6.22-14-generic (2.6.22-14.37) to 2.6.22-14.38
mono-common (1.2.4-6ubuntu6) to 1.2.4-6ubuntu6.1
mono-gac (1.2.4-6ubuntu6) to 1.2.4-6ubuntu6.1
mono-jit (1.2.4-6ubuntu6) to 1.2.4-6ubuntu6.1
mono-runtime (1.2.4-6ubuntu6) to 1.2.4-6ubuntu6.1
openoffice.org (1:2.3.0-1ubuntu5.1) to 1:2.3.0-1ubuntu5.3
openoffice.org-base (1:2.3.0-1ubuntu5.1) to 1:2.3.0-1ubuntu5.3
openoffice.org-calc (1:2.3.0-1ubuntu5.1) to 1:2.3.0-1ubuntu5.3
openoffice.org-common (1:2.3.0-1ubuntu5.1) to 1:2.3.0-1ubuntu5.3
openoffice.org-core (1:2.3.0-1ubuntu5.1) to 1:2.3.0-1ubuntu5.3
openoffice.org-draw (1:2.3.0-1ubuntu5.1) to 1:2.3.0-1ubuntu5.3
openoffice.org-evolution (1:2.3.0-1ubuntu5.1) to 1:2.3.0-1ubuntu5.3
openoffice.org-gnome (1:2.3.0-1ubuntu5.1) to 1:2.3.0-1ubuntu5.3
openoffice.org-gtk (1:2.3.0-1ubuntu5.1) to 1:2.3.0-1ubuntu5.3
openoffice.org-impress (1:2.3.0-1ubuntu5.1) to 1:2.3.0-1ubuntu5.3
openoffice.org-java-common (1:2.3.0-1ubuntu5.1) to 1:2.3.0-1ubuntu5.3
openoffice.org-math (1:2.3.0-1ubuntu5.1) to 1:2.3.0-1ubuntu5.3
openoffice.org-style-human (1:2.3.0-1ubuntu5.1) to 1:2.3.0-1ubuntu5.3
openoffice.org-writer (1:2.3.0-1ubuntu5.1) to 1:2.3.0-1ubuntu5.3
openssh-client (1:4.6p1-5build1) to 1:4.6p1-5ubuntu0.1
perl (5.8.8-7ubuntu3) to 5.8.8-7ubuntu3.1
perl-base (5.8.8-7ubuntu3) to 5.8.8-7ubuntu3.1
perl-modules (5.8.8-7ubuntu3) to 5.8.8-7ubuntu3.1
php5 (5.2.3-1ubuntu6.2) to 5.2.3-1ubuntu6.3
php5-cgi (5.2.3-1ubuntu6.2) to 5.2.3-1ubuntu6.3
php5-common (5.2.3-1ubuntu6.2) to 5.2.3-1ubuntu6.3
php5-curl (5.2.3-1ubuntu6.2) to 5.2.3-1ubuntu6.3
php5-dev (5.2.3-1ubuntu6.2) to 5.2.3-1ubuntu6.3
php5-mysql (5.2.3-1ubuntu6.2) to 5.2.3-1ubuntu6.3
php5-pgsql (5.2.3-1ubuntu6.2) to 5.2.3-1ubuntu6.3
pidgin (1:2.2.1-1ubuntu4) to 1:2.2.1-1ubuntu4.1
pidgin-data (1:2.2.1-1ubuntu4) to 1:2.2.1-1ubuntu4.1
poppler-utils (0.6-0ubuntu2) to 0.6-0ubuntu2.1
python-uno (1:2.3.0-1ubuntu5.1) to 1:2.3.0-1ubuntu5.3
skype (1.4.0.118dynamic+static-0medibuntu3) to 2.0.0.27-0medibuntu1
skype-common (1.4.0.118dynamic+static-0medibuntu3) to 2.0.0.27-0medibuntu1
ssh-askpass-gnome (1:4.6p1-5build1) to 1:4.6p1-5ubuntu0.1
system76-driver (2.1.2) to 2.1.3
ttf-opensymbol (1:2.3.0-1ubuntu5.1) to 1:2.3.0-1ubuntu5.3
tzdata (2007h-0ubuntu0.7.10) to 2007k-0ubuntu0.7.10
ubufox (0.4~beta1-0ubuntu4) to 0.4~beta1-0ubuntu6
update-manager (1:0.81) to 1:0.81.1
update-manager-core (1:0.81) to 1:0.81.1
xserver-xorg-video-intel (2:2.1.1-0ubuntu9) to 2:2.1.1-0ubuntu9.1

Any help would be much appreciated.  Thanks in advance.

---

### Post by asmiller-ke6seh on 2008-01-13
You might want to try reinstalling the System76 Driver.

It can't hurt - and it might help.

---

### Post by thomasaaron on 2008-01-14
I'm not trying to mince words, here. But just to clarify.
You should not need to REINSTALL the system 76 driver (as in re-download it onto your computer from our repos). You just need to re-run it.

Go to System > Admin > System76 Driver.
Click the Install Tab and the Install Button.
Then re-boot your computer.

---

### Post by Mung the Wicked on 2008-01-14
Ok.  That worked.  Earlier this morning, I remembered seeing at the bottom of the list of updates, System 76 package updates.  I would that a sound driver update was amongst them.

If that is the case, then is it generally a good idea to not update hardware's drivers with updated drivers from System 76?  I know it was like that with Windows XP.  If the Automatic Updater said it had an update for your video card/etc., you didn't want to install it.  I'm definitely not comparing XP to Ubuntu.  Ubuntu kicks XP's behind, but I'm just wondering if it's a similar scenario.

Thanks, guys!  I was tempted to do what you told me initially, but I just wanted to make sure.  I'm a noob at this still.  Been using Ubuntu for 7 months at work and finally got my own machine for private/work use in December so I could really start digging into and spending extra time with this great OS (and laptop!).

---

### Post by thomasaaron on 2008-01-14
Hi, Mung.

There will not always be a System76 driver update when an Ubuntu kernel update comes down. In fact, it was just sheer coincidence that both came downstream to you at the same time.

Your sound is controlled by ALSA, which is compiled against your kernel. So when a *new* kernel update comes down, it will often hose ALSA. By running the System 76 driver, you are re-compiling ALSA against the new kernel and, thus, restoring your sound.

In general, whenever something seems to be wrong with your computer, you might want to go ahead and run the driver first and then reboot. If the problem hasn't disappeared, you should seek help (forums, email, phone, etc...).

---

### Post by Mung the Wicked on 2008-01-14
> **thomasaaron said:**
> Hi, Mung.

There will not always be a System76 driver update when an Ubuntu kernel update comes down. In fact, it was just sheer coincidence that both came downstream to you at the same time.

Your sound is controlled by ALSA, which is compiled against your kernel. So when a *new* kernel update comes down, it will often hose ALSA. By running the System 76 driver, you are re-compiling ALSA against the new kernel and, thus, restoring your sound.

In general, whenever something seems to be wrong with your computer, you might want to go ahead and run the driver first and then reboot. If the problem hasn't disappeared, you should seek help (forums, email, phone, etc...).
Ah ha!  That makes perfect sense.  That's a great piece of knowledge to have, because I can actually possibly apply that theory to other future problems with hardware/software not working after an update.  Thanks again!

---

### Post by asmiller-ke6seh on 2008-01-15
> **thomasaaron said:**
> I'm not trying to mince words, here. But just to clarify.
You should not need to REINSTALL the system 76 driver (as in re-download it onto your computer from our repos). You just need to re-run it.

Go to System > Admin > System76 Driver.
Click the Install Tab and the Install Button.
Then re-boot your computer.

Mince words - please mince words. What you said is what I meant, and I'm not sure that Mung the Wicked understood that what I meant is what I said - you did, and you said what I meant.

:guitar:

---

### Post by preoche on 2008-02-09
i have the same problem, but i'm system 76 replies it's unsupported. i'm runnong on 64 bit 7.10.

any help?

---

### Post by thomasaaron on 2008-02-11
preoche,

What problem are you having? No sound after updating?
If so, run your System76 driver and re-boot the computer.

64-bit is now supported.

---

