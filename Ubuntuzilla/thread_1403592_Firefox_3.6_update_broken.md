---
title: "Firefox 3.6 update broken"
date: 2010-02-10
forum: Ubuntuzilla
---

### Post by 2LSS on 2010-02-10
I'm not sure if this is spicifically a firefox, or ubuntuzilla bug but I will give it a try here.

I updated firefox 3.5.7 to 3.6 (using gksudo firefox, etc) and restarted. As firefox started back up the "installing your updates" window started like normal but quickly stopped and displayed an error message "The update could not be installed. Please make sure there are no other copies of Firefox running on your computer, and then restart Firefox to try again." I checked for another running firefox process, but found none and even restarted my computer but I still get the same error message.

I checked in the /opt/firefox/updates/0/updates.log and found,
```
copy_file: failed to open or stat: -1,old-homepage-default.properties.moz-backup,2
```
so I tried,
```
cp old-homepage-default.properties old-homepage-default.properties.moz-backup
```
and started firefox but got the same error. I checked back in the log and found that ff found my copy but was missing instead,
```
copy_file: failed to open or stat: -1,icons/mozicon16.xpm.moz-backup,2
FINISH REMOVE icons/mozicon50.xpm
copy_file: failed to open or stat: -1,icons/mozicon50.xpm.moz-backup,2
```
So it seems to me that a bunch of files got removed and since firefox cant find them it won't update. Does anyone know what I should do?

---

### Post by nanotube on 2010-02-10
well, something apparently got borked in the upgrade from 3.5.7 to 3.6

i would suggest to remove the mozilla build install (if you install the installer script, run "ubuntuzilla.py -a remove -p firefox"), and then install afresh, using the ubuntuzilla repository rather than the script (the info on which is available at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) )

---

### Post by 2LSS on 2010-02-10
Wow I didn't realize you guys had new repo! 
Prior to removing my old script-installed firefox I want to back up my profile. Is it located in the .mozilla folder in my home directory or in /opt/firefox?

---

### Post by nanotube on 2010-02-10
> **2LSS said:**
> Wow I didn't realize you guys had new repo! 
Prior to removing my old script-installed firefox I want to back up my profile. Is it located in the .mozilla folder in my home directory or in /opt/firefox?

yes, your user profile is in ~/.mozilla

there are no user settings in /opt/firefox, the whole thing can be safely deleted.

---

### Post by 2LSS on 2010-02-10
Ok, used the build from your repo. All is good so far, thanks.

---

### Post by nanotube on 2010-02-10
> **2LSS said:**
> Ok, used the build from your repo. All is good so far, thanks.

excellent. :)

---

### Post by Objekt on 2010-02-11
> **2LSS said:**
> Wow I didn't realize you guys had new repo! 
Prior to removing my old script-installed firefox I want to back up my profile. Is it located in the .mozilla folder in my home directory or in /opt/firefox?

For that kind of thing, I use Firefox Backup Environment Extension (FEBE), written by Chuck Baker.  The current version (6.3.2) supports Firefox 3.6, and it really is a great help.  FEBE lets you back up your entire user profile, if you like.  I do that regularly, just in case my profile somehow gets hosed up.  I use it in Windows as well as Ubuntu.

FEBE install page at mozilla.org: [https://addons.mozilla.org/en-US/firefox/addon/2109]("https://addons.mozilla.org/en-US/firefox/addon/2109")

---

### Post by 2LSS on 2010-02-11
Thanks Objekt, I will have to give this add-on a try. I initially thought that firefox had a similar feature built in but apparently that is not the case.

---

