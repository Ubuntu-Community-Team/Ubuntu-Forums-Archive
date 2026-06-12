---
title: "Testers wanted: seamonkey installation script"
date: 2007-05-09
forum: Ubuntuzilla
---

### Post by nanotube on 2007-05-09
**EDIT:Read further down in the thread for the newest testing version. If you want the "stable" release, get the latest from [our homepage]("http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla"). 

as a celebration of finishing my last final exam (woo!), i have taken the time and created the seamonkey install script. it is based on our previous framework, rather than one posted by sumashod above, though i have borrowed the idea of creating an applications menu icon. :)

as our prior scripts, it has a number of fancy features, including 
* automatically detects the latest version, 
* downloads 
* installs in /opt, 
* verifies md5sum (no gpg signatures for seamonkey, so we do the next best thing), 
* links to firefox plugins (if user requests)
* creates the apps menu icon. 
* has option to uninstall

it is missing one feature, which is localization choice, since seamonkey does not have official localized builds, only a few contributed builds... so at this point i have decided to try for en-US only, which is the official build.

command to run the script is equivalent to our tb and ff scripts,
```
bash /path/to/script/installseamonkey.sh -install
```
and
```
bash /path/to/script/installseamonkey.sh -remove
```
please test, and post any bugs/corrections/suggestions.

script attached.

---

### Post by aysiu on 2007-05-09
It didn't quite work. I asked it to link to the repositories' Firefox plugins, and it appeared to try to link to the /opt Firefox plugins (which doesn't exist right now): ```
If you have the repositories version of Firefox installed, you can choose to link all the Firefox plugins to your Seamonkey install. Would you like to do that? [y/n]? y

Backing up old Seamonkey preferences


Changing to home directory


Downloading Seamonkey archive from the Mozilla site

--18:23:22--  ftp://ftp.mozilla.org/pub/mozilla.org/seamonkey/releases/1.1.1/seamonkey-1.1.1.en-US.linux-i686.tar.gz
           => `seamonkey-1.1.1.en-US.linux-i686.tar.gz'
Resolving ftp.mozilla.org... 63.245.208.138
Connecting to ftp.mozilla.org|63.245.208.138|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/seamonkey/releases/1.1.1 ... done.
==> PASV ... done.    ==> RETR seamonkey-1.1.1.en-US.linux-i686.tar.gz ... done.
Length: 14,762,685 (14M) (unauthoritative)

100%[==============================================================================================================================>] 14,762,685   144.42K/s    ETA 00:00

18:25:00 (148.88 KB/s) - `seamonkey-1.1.1.en-US.linux-i686.tar.gz' saved [14762685]


Downloading Seamonkey MD5 sums from the Mozilla site


Verifying Seamonkey MD5 sum

./seamonkey-1.1.1.en-US.linux-i686.tar.gz: OK

Extracting the downloaded Seamonkey archive


Removing installation file(s) to free up disk space


Linking plugins

mv: cannot stat `/opt/firefox/plugins': No such file or directory
Previous command did not complete successfully. Exiting.
```

---

### Post by nanotube on 2007-05-09
whoops, that was an accidental holdover from the firefox script (which i used as the base).
here's the updated version, attached.
thanks for the testing :)

---

### Post by aysiu on 2007-05-09
It works perfectly now. By the way, it seems to just go for English. Is the locale thing not possible with Seamonkey?

---

### Post by nanotube on 2007-05-10
> **aysiu said:**
> It works perfectly now. By the way, it seems to just go for English. Is the locale thing not possible with Seamonkey?

cool! just to make sure, did the menu item show up? 

as to locales; see this sentence in the first post in this thread:
> it is missing one feature, which is localization choice, since seamonkey does not have official localized builds, only a few contributed builds... so at this point i have decided to try for en-US only, which is the official build.
so, while it's /possible/, i'm not sure if it's worth it? 
they have 6 contributed builds in tar.gz/tar.bz2 format, but all of these plus some others are available as installable language packs (ie, once you have seamonkey, can install a language pack on top) ([http://www.mozilla.org/projects/seamonkey/releases/#l10n](http://www.mozilla.org/projects/seamonkey/releases/#l10n))

so, i figure, it would be better to just install the en-US version, and point people to the language pack list if they want another language, since that gives more choices?

---

### Post by aysiu on 2007-05-10
Thanks for the explanation about locales.

The menu entry didn't show up, but I'm using IceWM, so I'm not sure if that has something to do with it (I do have *menu-xdg* installed, though--maybe I needed to restart IceWM for it to be acknowledged?). I'll test that later.

---

### Post by aysiu on 2007-05-10
Well, even after a restart in IceWM, it isn't in the menus, but the menu entry is definitely present: ```
username@ubuntu:~/Desktop$ cd /usr/share/applications/
username@ubuntu:/usr/share/applications$ ls
avidemux.desktop                    gnome-cups-manager.desktop       hplip-kubuntu.desktop           orca.desktop                          Thunar.desktop
baobab.desktop                      gnome-dictionary.desktop         hp-sendfax.desktop              python2.4.desktop                     Thunar-folder-handler.desktop
cddb-slave.desktop                  gnome-keyring-manager.desktop    hwdb.desktop                    python2.5.desktop                     time.desktop
defaults.list                       gnome-nettool.desktop            java1.4.desktop                 reclevel.desktop                      users.desktop
evince.desktop                      gnome-power-preferences.desktop  javaws1.4.desktop               redhat-manage-print-jobs.desktop      vlc.desktop
exo-preferred-applications.desktop  gnome-screenshot.desktop         kde                             redhat-system-config-printer.desktop  vumeter.desktop
file-roller.desktop                 gnome-search-tool.desktop        language-selector.desktop       rhythmbox.desktop                     wine-notepad.desktop
firefox.desktop                     gnome-sound-recorder.desktop     leafpad.desktop                 scim-setup.desktop                    wine-regedit.desktop
galeon.desktop                      gnome-system-log.desktop         mimeinfo.cache                  screensavers                          wine-uninstaller.desktop
gcalctool.desktop                   gnome-volume-control.desktop     mozilla-thunderbird.desktop     seamonkey.desktop                     wine-winecfg.desktop
gdmflexiserver.desktop              gnome-volume-properties.desktop  mozilla-thunderbird-pm.desktop  services.desktop                      wine-winefile.desktop
gdmflexiserver-xnest.desktop        goobox.desktop                   mplayer.desktop                 shares.desktop                        wine-winehelp.desktop
gdmphotosetup.desktop               gpilotd-control-applet.desktop   network.desktop                 sun-java5-java.desktop                wine-winemine.desktop
gdmsetup.desktop                    gqview.desktop                   ooo-base.desktop                sun-java5-javaws.desktop              xfce-xfprint-settings.desktop
gimp-2.2.desktop                    gstreamer-properties.desktop     ooo-calc.desktop                synaptic.desktop                      xfprint.desktop
gksu.desktop                        gucharmap.desktop                ooo-draw.desktop                synaptic-kde.desktop                  xfprint-manager.desktop
gnome-btdownload.desktop            hal-device-manager.desktop       ooo-impress.desktop             tagtool.desktop                       xsane.desktop
gnome-cd.desktop                    hp-fab.desktop                   ooo-math.desktop                template.desktop
gnome-cups-icon.desktop             hplip.desktop                    ooo-writer.desktop              Thunar-bulk-rename.desktop
username@ubuntu:/usr/share/applications$ cat seamonkey.desktop 
[Desktop Entry]
Encoding=UTF-8
Name=Seamonkey
GenericName=Browser
Comment=Internet-Browser
Exec=seamonkey 
Icon=/opt/seamonkey/chrome/icons/default/seamonkey.png
Terminal=false
X-MultipleArgs=false
Type=Application
Categories=Application;Network;
username@ubuntu:/usr/share/applications$ 
```

---

### Post by nanotube on 2007-05-10
hmm, that must be an icewm thing, because i just tested it here on gnome, and the menu showed up in the internet submenu, along with all the other browsers, automagically.

---

### Post by aysiu on 2007-05-10
Well, it's there in /usr/share/applications, so I think it's good.

---

### Post by nanotube on 2007-05-10
well, i added a section about seamonkey install to the ubuntuzilla website, and uploaded the script. :)

also, i have moved the script downloads off to the main sf.net fileservers. this has the benefit of 
(1) letting sf.net spread the bandwidth between its mirrors (though the effect for the small scripts is minimal)
(2) giving us download statistics for the scripts. (already, in the last half an hour, the firefox script's been downloaded 8 times!)

so, that's the news. :)
thanks again for testing!

---

### Post by igster on 2007-05-10
Works for me on Feisty.  I tried install and remove options and it worked perfectly.  Great job!

---

### Post by nanotube on 2007-05-10
> **igster said:**
> Works for me on Feisty.  I tried install and remove options and it worked perfectly.  Great job!

thanks for your feedback! :)

---

### Post by sumashod on 2007-05-11
Hi.
I found a small bug:

```
wget -c --tries=20 --read-timeout=60 --waitretry=10 -q -O - [ftp://ftp.mozilla.org/pub/mozilla.org/seamonkey/releases/1.1.1/MD5SUMS](ftp://ftp.mozilla.org/pub/mozilla.org/seamonkey/releases/1.1.1/MD5SUMS) |grep 'linux-i686.tar.gz' > seamonkey-$VERSION.en-US.linux-i686.tar.gz.md5
```

correct is```
 /releases/$VERSION/MD5SUMS
```

Andy

---

### Post by nanotube on 2007-05-11
> **sumashod said:**
> Hi.
I found a small bug:

```
wget -c --tries=20 --read-timeout=60 --waitretry=10 -q -O - [ftp://ftp.mozilla.org/pub/mozilla.org/seamonkey/releases/1.1.1/MD5SUMS](ftp://ftp.mozilla.org/pub/mozilla.org/seamonkey/releases/1.1.1/MD5SUMS) |grep 'linux-i686.tar.gz' > seamonkey-$VERSION.en-US.linux-i686.tar.gz.md5
```

correct is```
 /releases/$VERSION/MD5SUMS
```

Andy

hey wow, you're right, thanks for catching that! that would've been a major pain once they released a new version, and md5sums started consistently failing. :) heh heh... 
thanks for taking the time to read the code! i will fix and push out the new version shortly.

if you have any other comments/suggestions, please feel free to post them :)

---

### Post by sumashod on 2007-05-11
I have finished myself with my SeaMonkey instal-script. In my Script I have integrated one more update function. One can begin this with me with seamonkey-update in shell or console. If you also have interest in this function, then you could use certainly a few things from my Script. Unfortunately, I am able to only badly in English and help myself in an on-line translator, but for the code you need no German to speak. 

Greeting Andy

[SeaMonkey Installer](http://sumashod.su.funpic.de/scripts/seamonkey-installer-de.tar.bz2)

---

### Post by nanotube on 2007-05-13
thanks for posting your updated script. 
the update option is a good idea, seeing as how seamonkey does not have a built-in updater like firefox and thunderbird do. 
i have updated my script to include an update option, though i used, again, a different basic method to provide that functionality. ;) (i didn't go for generating a separate script)

see the new versions up for testing at [http://ubuntuforums.org/showthread.php?t=441909](http://ubuntuforums.org/showthread.php?t=441909)

please test, look, read the code, comment :)

---

### Post by garrencornelius on 2007-06-03
I ran the script just now, and everything worked wonderfully.  The icon showed up in K Menu under Internet, as I'm using Kubuntu 7.04.  Thank you very much for the script.  I was having trouble compiling everything a few weeks ago, and just decided to see if anyone had posted an easier solution.

---

### Post by nanotube on 2007-06-03
> **garrencornelius said:**
> I ran the script just now, and everything worked wonderfully.  The icon showed up in K Menu under Internet, as I'm using Kubuntu 7.04.  Thank you very much for the script.  I was having trouble compiling everything a few weeks ago, and just decided to see if anyone had posted an easier solution.

thanks for your feedback! :)

---

