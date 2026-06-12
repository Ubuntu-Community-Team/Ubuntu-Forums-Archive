---
title: "HPLIP Plug-in installation failed"
date: 2013-10-02
forum: Ubuntu Development Version
---

### Post by den_ on 2013-10-02
Hi,

for the case someone else encounters this problem, try downloading the plugin from here:

[http://www.openprinting.org/download/printdriver/auxfiles/HP/plugins/hplip-3.13.9-plugin.run](http://www.openprinting.org/download/printdriver/auxfiles/HP/plugins/hplip-3.13.9-plugin.run)

(when version changes one can find the link in output of 'sudo hp-plugin -i -g'.)

and then execute the script 'sudo sh hplip-3.13.9-plugin.run'.

All other methods didn't work for me.

---

### Post by ping-wu on 2013-10-06
For printers, I don't find a need to install the HPLIP driver.  But for scanners (all-in-one laser), I do.

Can't remember exactly what I did, but I believe the only thing I had to do was to go to Synaptic (or Software Center), and reinstall the hplip package.  Perhaps you could try (or could have tried) this first.

---

### Post by geoffkalender on 2013-10-09
nvm

---

### Post by geoffkalender on 2013-10-09
> **den_ said:**
> Hi,

for the case someone else encounters this problem, try downloading the plugin from here:

[http://www.openprinting.org/download/printdriver/auxfiles/HP/plugins/hplip-3.13.9-plugin.run](http://www.openprinting.org/download/printdriver/auxfiles/HP/plugins/hplip-3.13.9-plugin.run)

(when version changes one can find the link in output of 'sudo hp-plugin -i -g'.)

and then execute the script 'sudo sh hplip-3.13.9-plugin.run'.

All other methods didn't work for me.

I'm having this same issue right now, den_, but openprinting is down.  Any chance you can rehost it?

---

### Post by oldfred on 2013-10-09
Just go to the HP site. It has the newest version.

I have HP Deskjet 3520
[http://ubuntuforums.org/showthread.php?t=2109050](http://ubuntuforums.org/showthread.php?t=2109050)
HP's newest On this website you can download the HPLIP software which supports 2,211 HP printers on nearly any Linux distribution available today.
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)
Ubuntu's older version
sudo apt-get install hplip-gui
gksudo hp-setup
# new version
hp-upgrade

No system tray error:
open up the "startup applications" editor from the admin menu.
add a new program, for the command put:
sleep 10;/usr/bin/hp-systray

---

### Post by geoffkalender on 2013-10-09
> **oldfred said:**
> Just go to the HP site. It has the newest version.

I have HP Deskjet 3520
[http://ubuntuforums.org/showthread.php?t=2109050](http://ubuntuforums.org/showthread.php?t=2109050)
HP's newest On this website you can download the HPLIP software which supports 2,211 HP printers on nearly any Linux distribution available today.
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)
Ubuntu's older version
sudo apt-get install hplip-gui
gksudo hp-setup
# new version
hp-upgrade

No system tray error:
open up the "startup applications" editor from the admin menu.
add a new program, for the command put:
sleep 10;/usr/bin/hp-systray

That finally did it, for some reason it was hanging for hours on the plugin installation last night.  They list a plugin fix in their changelog.  Thank you for your help.

---

### Post by den_ on 2013-10-09
> **ping-wu said:**
> For printers, I don't find a need to install the HPLIP driver.  But for scanners (all-in-one laser), I do.

Can't remember exactly what I did, but I believe the only thing I had to do was to go to Synaptic (or Software Center), and reinstall the hplip package.  Perhaps you could try (or could have tried) this first.

Of course I have tried that first. Installation of the hplip package was/is(?) broken at the moment. Actually installation of package works fine, but its configuration and installation of plugin during that time is broken.

In my case both printer and scanner require proprietary plugin which is not part of hplip self, but is installed with its help.

---

