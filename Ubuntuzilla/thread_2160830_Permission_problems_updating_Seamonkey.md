---
title: "Permission problems updating Seamonkey?"
date: 2013-07-08
forum: Ubuntuzilla
---

### Post by Manoel on 2013-07-08
Hi. I hope somebody can help me.  I'm using Seamonkey with Ubuntu since the beginning but from some version on, I wasn't able to update versions as a normal user because I got the message about "...you don't have the system permissions required...", so I began to update using "sudo seamonkey" and then, when updating was over, I closed seamonkey and started it again as a normal user. In this way I was able to do a lot of updatings with no problem at all, but now, when trying to update to 2.19, this method was no longer valid, and when I went back to the normal user Seamonkey, it opened profile start-up window and then when I click on the profile I wanted, and click on "Use Profile", nothing happens and seamonkey exists with a "1" value.  I guess it has to do with permissions. When I installed the ubuntuzilla packages it asked for the SUDO password, so I think it has to do with what they say at [http://kb.mozillazine.org/Browser_will_not_start_up#Ownership](http://kb.mozillazine.org/Browser_will_not_start_up#Ownership) (Seamonkey installed as root) But I haven't been able to fix it. If I update with "sudo..." then I can't go into my profile as a normal user. If I reinstall through Ubuntuzilla, then it all is OK but I'm stuck with 2.17.1 version :-(  I guess it could be OK if Ubuntuzilla offers the last version (2.19). Must I wait till then? How will I know that it's already available? Would be any security risk if I use 2.17.1?  Thanks in advance to anybody who can help.

---

### Post by nanotube on 2013-07-08
Hi,
I've just pushed seamonkey 2.19 to the ubuntuzilla repository, so you should be able to update via the package manager.

---

### Post by Manoel on 2013-07-10
Thanks for the quick answer and update! :-)  But sadly it didn't work either! Now I have the Ubuntuzilla-updated 2.19 version of Seamonkey but when I start at command line or through Gnome desktop, it always exits with "1" value :-(  I think it would be dangerous to run Seamonkey as SUDO, so I need to fix the Seamonkey access as normal user. I'm at a lost! :-( Any idea?

---

### Post by Manoel on 2013-07-10
In my tries I've found something curious which can give some clue about what is happening: when profile startup window opens, if I choose an already existing profile, Seamonkey exits with error (nothing happens, exit value=1). But, if through profile manager window I create a new profile, Seamonkey starts correctly! If I just close Seamonkey and try to start it again with that newly created profile, same thing happens as with older ones: after clicking on "Use profile", it exists in error :-(

---

### Post by Manoel on 2013-07-11
I'm wondering... should I uninstall and install again as normal user? How is it done through Ubuntuzilla? Should I try this installation procedure [http://www.seamonkey-project.org/doc/install-and-uninstall#install_linux](http://www.seamonkey-project.org/doc/install-and-uninstall#install_linux) instead?

---

### Post by nanotube on 2013-07-11
Hi,

Hard to say, with all that sudo-ing you did earlier you could have messed up some permissions somewhere. 

I would suggest that as a first try to fix things, you try to chown all files in your seamonkey profile dir to yourself. Use this command:
```
sudo chown -R yourusername:yourusername ~/.mozilla/seamonkey

```
(obviously change 'yourusername' to your actual username)

See if that helps. If it doesn't, then I would suggest uninstalling seamonkey, wiping the directory where all the stuff goes (if you used ubuntuzilla, should be /opt/seamonkey), and reinstalling again.

---

### Post by Manoel on 2013-07-11
Thanks again, Nanotube. But I already tried that as I saw at [http://kb.mozillazine.org/Browser_will_not_start_up#Ownership](http://kb.mozillazine.org/Browser_will_not_start_up#Ownership) that it could be a fix in some cases. I tried again just a moment ago and the problem is still there.

So I'll uninstall and install it back. You didn't say if I should better install again with ubuntuzilla or independently... I think I'll try those instructions at [http://www.seamonkey-project.org/doc/install-and-uninstall#install_linux](http://www.seamonkey-project.org/doc/install-and-uninstall#install_linux) It's a pity because ubuntuzilla made things a lot easier for me... til now, I must say :(

---

### Post by Manoel on 2013-07-11
I've just removed the ubuntuzilla installation and have the tar.bz2 manually installed instead. To my sad surprise, behaviour is absolutely the same! Profile manager starts but any profile I chose, it closes with an error value, and no feedback! Only newly created profile would open the suite, but then even this profile, once closed, is unaccessible later :-(

./seamonkey -safe-mode is of no use, either. It also exits with no error message.

---

### Post by nanotube on 2013-07-11
hmm, could be something borked in your profile. try moving your old profile dir out of the way and starting fresh:

```
mv ~/.mozilla/seamonkey ~/.mozilla/seamonkey.backup
```

then start again and see.

(and if you're happy with ubuntuzilla, you can always go back to it once we figure this out. :) )

---

### Post by Manoel on 2013-07-12
This is the troubleshooting info when started in safe mode and a new profile is created:
> 
{
  "application": {
    "name": "SeaMonkey",
    "version": "2.19",
    "userAgent": "Mozilla/5.0 (X11; Linux i686; rv:22.0) Gecko/20100101 Firefox/22.0 SeaMonkey/2.19",
    "supportURL": "http://www.seamonkey-project.org/doc/"
  },
  "modifiedPreferences": {
    "browser.cache.disk.capacity": 358400,
    "browser.cache.disk.smart_size.first_run": false,
    "browser.cache.disk.smart_size.use_old_max": false,
    "browser.cache.disk.smart_size_cached_value": 358400,
    "browser.places.smartBookmarksVersion": 4,
    "browser.startup.homepage_override.mstone": "rv:22.0",
    "extensions.lastAppVersion": "2.19",
    "network.cookie.prefsMigrated": true,
    "places.history.expiration.transient_current_max_pages": 49455
  },
  "graphics": {
    "numTotalWindows": 1,
    "numAcceleratedWindows": 0,
    "windowLayerManagerType": "Basic",
    "numAcceleratedWindowsMessage": [
      ""
    ],
    "adapterDescription": "NVIDIA Corporation -- GeForce 7050 PV / nForce 630a/integrated/SSE2/3DNOW!",
    "adapterVendorID": "NVIDIA Corporation",
    "adapterDeviceID": "GeForce 7050 PV / nForce 630a/integrated/SSE2/3DNOW!",
    "adapterRAM": "",
    "adapterDrivers": "",
    "driverVersion": "2.1.2 NVIDIA 304.88",
    "driverDate": "",
    "webglRenderer": "NVIDIA Corporation -- GeForce 7050 PV / nForce 630a/integrated/SSE2/3DNOW!",
    "info": {
      "AzureCanvasBackend": "cairo",
      "AzureFallbackCanvasBackend": "none",
      "AzureContentBackend": "none"
    }
  },
  "javaScript": {
    "incrementalGCEnabled": true
  },
  "accessibility": {
    "isActive": false,
    "forceDisabled": 0
  },
  "libraryVersions": {
    "NSPR": {
      "minVersion": "4.9.6",
      "version": "4.9.6"
    },
    "NSS": {
      "minVersion": "3.14.3.0 Basic ECC",
      "version": "3.14.3.0 Basic ECC"
    },
    "NSSUTIL": {
      "minVersion": "3.14.3.0",
      "version": "3.14.3.0"
    },
    "NSSSSL": {
      "minVersion": "3.14.3.0 Basic ECC",
      "version": "3.14.3.0 Basic ECC"
    },
    "NSSSMIME": {
      "minVersion": "3.14.3.0 Basic ECC",
      "version": "3.14.3.0 Basic ECC"
    }
  },
  "userJS": {
    "exists": false
  },
  "extensions": [
    {
      "name": "ChatZilla",
      "version": "0.9.90",
      "isActive": false,
      "id": "{59c81df5-4b7a-477b-912d-4e0fdf64e5f2}"
    },
    {
      "name": "DOM Inspector",
      "version": "2.0.15pre",
      "isActive": false,
      "id": "inspector@mozilla.org"
    },
    {
      "name": "JavaScript Debugger",
      "version": "0.9.89",
      "isActive": false,
      "id": "{f13b157f-b174-47e7-a34d-4815ddfdfeb8}"
    }
  ]
}[TABLE]
[TR]
[TH][/TH]
[TH][/TH]
[TH][/TH]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
       [/TABLE]


---

### Post by Manoel on 2013-07-12
> **nanotube said:**
> hmm, could be something borked in your profile. try moving your old profile dir out of the way and starting fresh:

Borked in ***ALL*** my profiles? Even in the newly created ones? That seems absurd :-(

I will try to install previous version 2.17.1 and see what happens.

---

### Post by Manoel on 2013-07-12
Before installing an older version, I'll see if there is a general profile problem.

I can see, when Seamonkey closed, a .parentlock file in all the profiles. I think that should not be there, so I've tried and delete it for one of the profiles, the last I created with the last installation, which I'll use for testing purposes. After deleting the .parentlock, I've tried to start Seamonkey in safe mode and -as always- it has exited after chosing the profile, with no message error. But I've discovered that the .parentlock has just beeing created when exiting!! It might be a clue or something?

---

### Post by Manoel on 2013-07-12
BTW. I've got my profiles at a normal location: /home/USERNAME/.mozilla/seamonkey

---

### Post by Manoel on 2013-07-12
A great advance!! I've just found that bypassing the Profile Manager allows me to normally open any profile I want! 

./seamonkey -profile "/home/USERNAME/.mozilla/seamonkey/PROFILEFOLDER"

As it's said at [http://kb.mozillazine.org/Profile_in_use#Check_the_profile_folder_name_and_location](http://kb.mozillazine.org/Profile_in_use#Check_the_profile_folder_name_and_location)

> If you can't spot an error in that file try running the Mozilla application [ with a specific profile using command line arguments]("http://kb.mozillazine.org/Starting_your_Mozilla_application_with_a_specified_profile"). This bypasses the profile manager and profiles.ini. If you succeed then you know that the problem is with profiles.ini

So I guess the problem was with that file. Now that I recover the access to my profiles, I'll investigate with more calm this profiles.ini issue.

After reinstalling with Ubuntuzilla, same behaviour happens: through Profile Manager, existing profiles are unaccessible, but when opening with command line and -profile option it starts correctly.

I hope my documentation of these problems and steps I followed will help anyone with similar problems :-)

---

### Post by Manoel on 2013-07-12
The only strange thing I can see at profile.ini is this bunch of lines:

```
[Profile1]
Name=Default User
IsRelative=1
Path=t54ld5ot.Default User
```

I mean those blank spaces could be creating some issue? This profile was not created by me. There is another "default" profile, with no empty spaces in it:

```
[Profile0]
Name=default
IsRelative=1
Path=doelvaln.default
```

Could it be the thing causing this start-up problems with the profiles? :-m

---

### Post by nanotube on 2013-07-15
> **Manoel said:**
> Borked in ***ALL*** my profiles? Even in the newly created ones? That seems absurd :-(


yes, all your profiles. there's a .ini file that's shared by all.

> I will try to install previous version 2.17.1 and see what happens.

sure, why not give it a whirl. though it seems that trying to nuke your .mozilla/seamonkey dir is an easier thing to try first.

i see you've delved into the .ini file some - i can't really help you there since i never dug into that myself. i don't suppose you've tried nuking the .mozilla/seamonkey dir as i suggested and seeing if that makes the problem go away?

---

