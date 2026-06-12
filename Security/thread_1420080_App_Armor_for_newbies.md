---
title: "App Armor for newbies"
date: 2010-03-02
forum: Security
---

### Post by Advait on 2010-03-02
Hi,

I've been using Ubuntu for about a week. I have no experience with Linux or with programming. I read thru some of the App Armor threads. From what I can see, it looks like using App Armor correctly requires some significant knowledge and experience with Ubuntu/Linux. I definitely don't have that.

So my conclusion is that I don't have sufficient experience to generate an App Armor profile for my FIrefox. And it sounds like to use App Armor with Firefox, it definitely requires some tweaking by the user. I looked thru the sample App Armor profiles for Firefox and they made zero sense to me. After reading the threads I had no clue how I would modify a profile.

Is there some way that App Armor can be used by a newbie like me? Doesn't look like it, but please let me know if I'm missing something. Unfortunately I don't have lots of free time where I can teach myself the finer points of Linux, or spend many hours doing trial and error.

Anyone considering making a gui that would allow a newbie like me to use App Armor with Firefox? I'm guessing that Firefox is at the top of the list when it comes to applications users would like to App Armor.

Thanks,

Tom

PS: I am running No-Script.

---

### Post by uRock on 2010-03-02
In a terminal, enter these two commands to get the standard AppArmor profile that is in the repositories. ```
sudo apt-get install apparmor-profiles
``` ```
sudo enforce firefox
```

---

### Post by bodhi.zazen on 2010-03-02
Apparmor takes some time to understand. It is unfortunate but true.

Basically, in a nut shell, the profile is nothing more then a list of files or directories and permissions.

so you will see something like this :

[http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-9.10/usr.bin.firefox-3.5](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-9.10/usr.bin.firefox-3.5)

```

# Bodhi.Zazen's current firefox profile
# Please note this is for :
# Ubuntu 9.10
# Modified from an original profile from Jamie Strandboge <jamie@canonical.com>

#include <tunables/global>

/usr/lib/firefox-3.5.*/firefox {
  #include <abstractions/audio>
  #include <abstractions/base>
  #include <abstractions/cups-client>
  #include <abstractions/dbus>
  #include <abstractions/fonts>
  #include <abstractions/freedesktop.org>
  #include <abstractions/gnome>
  #include <abstractions/nameservice>
  #include <abstractions/user-tmp>
  #include <abstractions/X>

  # for networking
  network inet stream,
  network inet6 stream,
  @{PROC}/[0-9]*/net/if_inet6 r,
  @{PROC}/[0-9]*/net/ipv6_route r,

  # sounds
  /etc/sound/ r,
  /etc/sound/** r,
  /etc/wildmidi/wildmidi.cfg r,

  # should maybe be in abstractions
  /etc/ r,
  /etc/gnome/defaults.list r,
  /etc/mime.types r,
  /etc/mailcap r,
  /usr/bin/dbus-launch ixr,

  # firefox specific
  /etc/firefox-3.*/ r,
  /etc/firefox-3.*/** r,
  /etc/xulrunner-1.9*/ r,
  /etc/xulrunner-1.9*/** r,
  /etc/gre.d/ r,
  /etc/gre.d/* r,

  # noisy
  deny /usr/lib/firefox-3.*/** w,
  deny /usr/lib/firefox-addons/** w,
  deny /usr/lib/xulrunner-addons/** w,

  # These are needed when a new user starts firefox and firefox.sh is used
  /usr/lib/firefox-3.*/** ixr,
  /usr/bin/basename ixr,
  /sbin/killall5 ixr,
  /bin/which ixr,
  @{PROC}/ r,
  @{PROC}/[0-9]*/cmdline r,
  @{PROC}/[0-9]*/stat r,
  @{PROC}/[0-9]*/status r,
  @{PROC}/filesystems r,
  capability sys_ptrace,

  /etc/mtab r,
  @{PROC}/[0-9]*/mounts r,
  @{PROC}/[0-9]*/maps r,

  # allow access to documentation and other files the user may want to look
  # at in /usr
  /usr/ r,
  /usr/** r,

  # so browsing directories works
  / r,
  /**/ r,

  # allow read and write to all user's files, except explicitly denied ones
  owner @{HOME}/ r,
  owner @{HOME}/{Desktop,Documents,Downloads}/ rw,
  owner @{HOME}/{Desktop,Documents,Downloads}/** rw,
  owner @{HOME}/Firefox_wallpaper* rw,

  #include <abstractions/private-files>
  audit deny @{HOME}/.ssh/** mrwkl,
  owner @{HOME}/.gnome2/accels/ rw,
  owner @{HOME}/.gnome2/accels/** rw,
  owner @{HOME}/.gnome2_private/ mrwkl,
  owner @{HOME}/.gnome2_private/** mrwkl,
  @{HOME}/.cache/ rw,
  @{HOME}/.cache/** rwmk,
  @{HOME}/.gnome2/ rw,
  @{HOME}/.gnome2/** rwmk,
  @{HOME}/.local/ r,
  @{HOME}/.local/** r,

  # comment this out if using gpg plugin/addons
  owner @{HOME}/.gnupg/** mrwkl,

  # per-user firefox configuration
  @{HOME}/.mozilla/ rw,
  @{HOME}/.mozilla/** rwmk,

  # per-user common plugin configuration
  @{HOME}/.icedteaplugin/ rw,
  @{HOME}/.icedteaplugin/** rw,
  @{HOME}/.adobe/ rw,
  @{HOME}/.adobe/** rw,
  @{HOME}/.esd_auth rw,
  @{HOME}/.macromedia/ rw,
  @{HOME}/.macromedia/** rw,
  @{HOME}/.java/ rw,
  @{HOME}/.java/** rwk,

  #
  # Plugins/helpers
  #
  @{PROC}/[0-9]*/fd/ r,
  /usr/lib/** rm,
  /bin/bash ixr,
  /bin/dash ixr,
  /bin/grep ixr,
  /bin/ps Uxr,
  /bin/uname Uxr,
  /usr/bin/m4 ixr,
  /usr/bin/gnome-open ixr,
  /usr/lib/nspluginwrapper/i386/linux/npviewer Uxr,
  /var/lib/ r,
  /var/lib/** mr,
  # noisy
  deny /usr/share/mozilla/extensions/**/ w,
  deny /usr/lib/mozilla/extensions/**/ w,
  deny /usr/lib/firefox-3.*/update.test w,

  # for maximum plugin/helper compatibility
  #/usr/bin/* Uxr,
  #/usr/lib/*/** ixr,

  #
  # For stricter access, comment out the 'maximum plugin/helper compatibility'
  # lines above and uncomment these
  #

  # evince has its own profile, so change to it
  /usr/bin/evince PUxr,

  # miscellaneous
  #/usr/bin/eog Uxr,
  /usr/bin/gedit Uxr,
  /usr/bin/gimp* Uxr,
  /usr/bin/file-roller Uxr,
  /usr/bin/ooffice Uxr,
  /usr/bin/oocalc Uxr,
  /usr/bin/oodraw Uxr,
  /usr/bin/ooimpress Uxr,
  /usr/bin/oowriter Uxr,
  /usr/bin/python*/* ixr,

  # totem
  /usr/lib/totem/** ixr,
  /usr/bin/totem-gstreamer Uxr,
  /usr/bin/totem-xine Uxr,
  /usr/bin/totem Uxr,

  # mozplugger
  /etc/mozpluggerrc r,
  /usr/bin/mozplugger-helper Uxr,
  /usr/bin/mplayer Uxr,

  # java
  /usr/lib/jvm/java-6-openjdk/jre/bin/java Uxr,
  /etc/java-*-sun/** r,
  /usr/lib/jvm/java-*-sun-1.*/jre/bin/java Uxr,

 }
```The break down is:[FONT=monospace]

1. Full path to the application to confine, with rules in the brackets {}

[/FONT]/usr/lib/firefox-3.5.*/firefox {

rules ...

}

2. Includes

These are a pre-defined set of rules and are in /etc/apparmor.d , for example
[FONT=monospace]
[/FONT]#include <abstractions/audio>

includes the permissions to access audio and the are located in /etc/apparmor.d/abstractions/audio

This way you do not have to write audio rules over and over ...

3. Path - permissions

 /bin/bash ixr,

/bin/bash is the file to allow access, ixr are the permissions.

These may include variables such as 
[FONT=monospace]
[/FONT]@{HOME} == a users home directory
options such as owner
and * or **

permissions are not difficult to understand
r = read
w = write
x = execute (ix or Px or Ux, see the sticky for details)

etc ...

See the apparmor sticky for further details.

The advantage of apparmor is that you can read and understand the config file.

But, yes, you need to understand the linux file system and have a sense of what is normal.

==========

The "problem" with firefox is that it needs rather extensive access so the profile is long.

I strongly suggest you start with a smaller program.

[http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-9.10/usr.sbin.privoxy](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-9.10/usr.sbin.privoxy)

That profile is for privoxy and half of it restrict access to things in $HOME.

===========

so, start with smaller profiles an work up.

===========

If at all possible, if you wish, start with the default profiles, for example, follow the advice iRock gave you =)

Understand them and work your way up.

Basically, follow the logs for errors and fix them.

```
tail -F /var/log/messages
```

If (when) you get stuck, ask for help.

After writing a few profiles it gets much easier. For example I wrote the Privoxy profile in under 5 minutes from start to finish.

============

Hopefully more and more profiles will be included over time.

There is a GUI tool for apparmor on SUSE, but, it does not help much as you still need to manually write the rules or at least understand how to do so (the gui tool does not generate a profile).

---

### Post by Advait on 2010-03-02
OK, thanks for the info. The profiles still look pretty daunting to a newbie like me. I could probably learn it but unfortunately don't have that kind of time. I'm guessing that many users would like to have a "standard" profile for FireFox with some kind of gui to easily view and resolve errors. I'm guessing that's just one of hundreds of Ubuntu projects that would be nice to have. Just not enough programmers out there...!

If I didn't have to pay the mortgage, I could take the time to learn programming and do it myself! (smile) 

If I use the Firefox profile you provided, would that create a lot of errors and headaches for me? Or do you think it would work OK on my system? Is the file system layout very different from one Ubuntu installation to another? Or pretty much the same?

I'm guessing the AppArmor profile for Firefox needs to be updated each time Firefox is updated?

Thanks,

Tom

---

### Post by bodhi.zazen on 2010-03-02
Unless you have a good reason, use the default firefox profile.

If you want to use my profile(s) all I can tell you is that they are up to date as of the last time I looked, It has been a while for my ubuntu 8.04 profile, lol.

I currently use the Ubuntu 9.10 profiles, but they vary. One is for the default version of firefox , 3.5.x, and it will work as firefox is update. The other is for firefox 3.6.0, which I downloaded from mozilla, and put in /usr/local/firefox.

If you have problems, well that is what the forums are for.

---

