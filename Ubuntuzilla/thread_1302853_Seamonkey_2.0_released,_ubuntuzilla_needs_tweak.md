---
title: "Seamonkey 2.0 released, ubuntuzilla needs tweak"
date: 2009-10-27
forum: Ubuntuzilla
---

### Post by kitchin on 2009-10-27
Seamonkey 2.0  is out, but Ubuntuzilla.py needs some tweaks to install it. I found this works:

1. Upgrading: if you are using Seamonkey 1.1.x and have unused profiles, delete them. Seamonkey has a bug migrating multiple profiles, see [known issues]("http://www.seamonkey-project.org/releases/seamonkey2.0/#issues"). Even trying a manual migration (from the GUI, not command line) did not work for me. But everything works automatically if you have just one profile.

2. Upgrading: Uninstall Seamonkey 1.1.x first.  Seamonkey 2.0 crashed for me when I skipped that step:
% ubuntuzilla.py -a remove -p seamonkey

3. Mod ubuntuzilla.py 4.7.4. The FTP paths have changed and ubuntuzilla does not understand them. Also, the download file is now .bz2 compressed, instead of .gz.  Here is my diff, use as you see fit!

```

--- ubuntuzilla.py    Tue Oct 27 14:55:56 2009
+++ mod-ubuntuzilla.py    Tue Oct 27 15:06:58 2009
@@ -586,8 +586,23 @@
         self.sigFilename = self.packageFilename + ".md5"
         print "\nDownloading Seamonkey MD5 sums from the Mozilla site\n"
         
-        self.util.robustDownload(argsdict={'executionstring':"wget -c --tries=5 --read-timeout=20 --waitretry=10 -q -nv -O - ftp://" + "%mirror%" + self.options.package + "/releases/" + self.releaseVersion + "/MD5SUMS | grep 'linux-i686.tar.gz' > " + self.sigFilename, 'includewithtest':True}, errormsg="Failed to retrieve md5 sum. This may be due to transient network problems, so try again later. Exiting.")
-        
+        self.util.robustDownload(argsdict={'executionstring':"wget -c --tries=5 --read-timeout=20 --waitretry=10 -q -nv -O - ftp://" + "%mirror%" + self.options.package + "/releases/" + self.releaseVersion + "/MD5SUMS | grep -F './linux-i686/en-US/" + self.packageFilename + "' > " + self.sigFilename, 'includewithtest':True}, errormsg="Failed to retrieve md5 sum. This may be due to transient network problems, so try again later. Exiting.")
+
+        # example: 91360c07aea125dbc3e03e33de4db01a  ./linux-i686/en-US/seamonkey-2.0.tar.bz2
+        # sed to:  91360c07aea125dbc3e03e33de4db01a  ./seamonkey-2.0.tar.bz2
+        print "demunging: sed -i 's#/linux-i686/en-US/#/#' " + self.sigFilename + "...\n" 
+        returncode = os.system("sed -i 's#/linux-i686/en-US/#/#' " + self.sigFilename)
+        if returncode:
+            print "MD5 sum demunging failed. You should delete file '", self.sigFilename, "' and run the script again.\n"
+            print "Would you like to delete this file now? [y/n]? "
+            self.askyesno()
+            if self.ans == 'y':
+                print "\nOK, deleting file and exiting.\n"
+                os.remove(self.sigFilename)
+            else:
+                print "OK, exiting without deleting file.\n"
+            sys.exit(1)
+       
     def verifyGPGSignature(self):
         print "\nVerifying signature...\nNote: do not worry about \"untrusted key\" warnings. That is normal behavior for newly imported keys.\n"
         returncode = os.system("gpg --verify " + self.sigFilename + " " + self.packageFilename)
@@ -1097,11 +1112,13 @@
 
     def downloadPackage(self):
         #MozillaInstaller.downloadPackage(self)
-        self.packageFilename = self.options.package + "-" + self.releaseVersion + ".en-US.linux-i686.tar.gz"
+        # example: seamonkey-2.0.tar.bz2
+        self.packageFilename = self.options.package + "-" + self.releaseVersion + ".tar.bz2"
         
         print "\nDownloading", self.options.package.capitalize(), "archive from the Mozilla site\n"
         
-        self.util.robustDownload({'executionstring':"wget -c --tries=5 --read-timeout=20 --waitretry=10 ftp://" + "%mirror%" + self.options.package + "/releases/" + self.releaseVersion + "/" + self.packageFilename, 'includewithtest':True})
+        # example: seamonkey/releases/2.0/linux-i686/en-US/seamonkey-2.0.tar.bz2
+        self.util.robustDownload({'executionstring':"wget -c --tries=5 --read-timeout=20 --waitretry=10 ftp://" + "%mirror%" + self.options.package + "/releases/" + self.releaseVersion + "/linux-i686/en-US/" + self.packageFilename, 'includewithtest':True})
 
     def downloadGPGSignature(self): #don't need this for seamonkey, blank it out
         pass

```So it's minor, a few string changes and a call to sed.

---

### Post by kitchin on 2009-10-27
An improvement would be to detect 1.1.x, because those versions still use the old paths and compression. Users may want to install and uninstall as I did. But I had two versions of the py script to use.

---

### Post by Uncle Spellbinder on 2009-10-28
Hopefully the deb files at [sourceforge](http://sourceforge.net/projects/ubuntuzilla/files/) will be updated. The last update was August, '09.

---

### Post by nanotube on 2009-10-28
Hi

I have made the update for seamonkey install function to work with v2.0

please test it out - grab the latest ubuntuzilla.py out of the project git repository.

repository info:
[http://sourceforge.net/scm/?type=git&group_id=202789](http://sourceforge.net/scm/?type=git&group_id=202789)

git web view:
[http://ubuntuzilla.git.sourceforge.net/](http://ubuntuzilla.git.sourceforge.net/)

I have tested it myself and it works, but some independent verification before i release it would be nice.

Note also that the new code will not work with old versions of seamonkey (v1.x)

---

### Post by nanotube on 2009-10-28
Attaching some .debs for testing

---

### Post by kansasnoob on 2009-10-28
Thanks for the .deb's.

Wanted to post this (looks good):

> lance@lance-desktop:~$ ubuntuzilla.py -a install -p seamonkey

Welcome to the Ubuntuzilla Seamonkey script version 4.7.5

Ubuntuzilla is built only for Ubuntu Linux and other distributions derived from Ubuntu (such as Linux Mint, e.g.)

This script will now install the latest release of the official Mozilla build of Seamonkey on your Linux system. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) 

Retrieving the version of the latest release of Seamonkey from the Mozilla website...
The most recent release of Seamonkey is detected to be 2.0. Please make sure this is correct before proceeding. (You can confirm by going to [http://www.mozilla.org/](http://www.mozilla.org/))
If no version number shows, if the version shown is not the latest, or if you would like to install an older release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]? 
Please enter 'y' or 'n': y
Retrieving list of available localizations for Seamonkey ...
Please choose the localization (language) for Seamonkey. Enter the number of your choice from the list below. [If you do not see a list of localizations, please check the help section of our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) for steps you can take to resolve this problem.]
  0. be         Belarusian [&#1041;&#1077;&#1083;&#1072;&#1088;&#1091;&#1089;&#1082;&#1072;&#1103;]
  1. ca         Catalan [català]             
  2. cs         Czech [&#268;eština]             
  3. de         German [Deutsch]              
  4. en-US      English (US) [English (US)]   
  5. es-AR      Spanish (Argentina) [Español (de Argentina)]
  6. es-ES      Spanish (Spain) [Español (de España)]
  7. fr         French [Français]            
  8. gl         Galician [Galego]             
  9. hu         Hungarian [Magyar]            
 10. ka         Georgian [&#4325;&#4304;&#4320;&#4311;&#4323;&#4314;&#4312;]
 11. lt         Lithuanian [lietuvi&#371; kalba]  
 12. nb-NO      Norwegian (Bokmål) [Norsk bokmål]
 13. nl         Dutch [Nederlands]            
 14. pl         Polish [Polski]               
 15. pt-PT      Portuguese (Portugal) [Português (Europeu)]
 16. ru         Russian [&#1056;&#1091;&#1089;&#1089;&#1082;&#1080;&#1081;]      
 17. sk         Slovak [sloven&#269;ina]          
 18. sv-SE      Swedish [Svenska]             
 19. tr         Turkish [Türkçe]            

Enter your choice of localization (integer, from 0 to 19): 4
You have chosen localization en-US, English (US) [English (US)]. Is that correct [y/n]? 
Please enter 'y' or 'n': y

Backing up old Seamonkey preferences

Retrieving package name for Seamonkey ...
Success!: seamonkey-2.0.tar.bz2

Downloading Seamonkey archive from the Mozilla site

--2009-10-28 17:06:10--  [ftp://mozilla.isc.org/pub/mozilla.org/seamonkey/releases/2.0/linux-i686/en-US/seamonkey-2.0.tar.bz2](ftp://mozilla.isc.org/pub/mozilla.org/seamonkey/releases/2.0/linux-i686/en-US/seamonkey-2.0.tar.bz2)
           => `seamonkey-2.0.tar.bz2'
Resolving mozilla.isc.org... 204.152.184.113
Connecting to mozilla.isc.org|204.152.184.113|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/seamonkey/releases/2.0/linux-i686/en-US ... done.
==> SIZE seamonkey-2.0.tar.bz2 ... 13166327
==> PASV ... done.    ==> RETR seamonkey-2.0.tar.bz2 ... done.
Length: 13166327 (13M)

100%[======================================>] 13,166,327   589K/s   in 24s     

2009-10-28 17:06:37 (543 KB/s) - `seamonkey-2.0.tar.bz2' saved [13166327]


Downloading Seamonkey MD5 sums from the Mozilla site

demunging: sed -i 's#/linux-i686/en-US/#/#' seamonkey-2.0.tar.bz2.md5...


Verifying Seamonkey MD5 sum

./seamonkey-2.0.tar.bz2: OK

Extracting archive

[sudo] password for lance: 
If you have the repositories version of Firefox installed, you can choose to link all the Firefox plugins to your Seamonkey install. Would you like to do that? [y/n]? 
Please enter 'y' or 'n': y
Trying to determine firefox plugin path...
Plugin path is:  /usr/lib/xulrunner-addons/plugins

Linking plugins


Linking dictionaries


Creating link to Seamonkey in /usr/bin/seamonkey

Would you like to create an Applications menu item for Seamonkey? [y/n]? 
Please enter 'y' or 'n': y
Creating Applications menu item for Seamonkey.


The new Seamonkey version 2.0 has been installed successfully.

If you are looking to use Seamonkey in other languages, head over to [http://www.mozilla.org/projects/seamonkey/releases/#l10n](http://www.mozilla.org/projects/seamonkey/releases/#l10n) and download the installable language pack of your choice.

Would you like to set up automatic update checking for the official Mozilla build of Seamonkey (recommended)? This feature will regularly check for updates to Seamonkey, and put up a small unobtrusive notification message with update information, when a new release is available. [y/n] 
Please enter 'y' or 'n': y
Updater successfully installed to your crontab. Try 'crontab -l' to see your new crontab, 'crontab -e' if you decide to edit it.

Thank you for using Ubuntuzilla.

Please support this project! If you found Ubuntuzilla helpful, please consider showing your appreciation with a small donation. :)

Just visit the project website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) , and click the donate button.
lance@lance-desktop:~$ 


I'll now launch Seamonkey and report back.

---

### Post by kansasnoob on 2009-10-28
Looks good:

[ATTACH]133460[/ATTACH]

Anymore needed?

BTW this was tested in Jaunty with no existing Seamonkey, only Firefox and Ubuntuzilla 4.7.4. It appears that all "imports" worked.

I was notified of an update to FF 3.5.4 while doing this.

Must look Seamonkey over a bit more closely since I don't normally use it, but all seemed to go well.

Right now it's back to Karmic iso testing ............ ARRRGH! This has been a tough one.

---

### Post by vinutux on 2009-10-28
> **Uncle Spellbinder said:**
> Hopefully the deb files at [sourceforge](http://sourceforge.net/projects/ubuntuzilla/files/) will be updated. The last update was August, '09.

+1 good to see updated debs on there

---

### Post by nanotube on 2009-10-28
> **kansasnoob said:**
> Looks good:

[ATTACH]133460[/ATTACH]

Anymore needed?

BTW this was tested in Jaunty with no existing Seamonkey, only Firefox and Ubuntuzilla 4.7.4. It appears that all "imports" worked.


great, thanks!

would be good to give it a testing on karmic, when you get a chance...
but for now i'll push out the new release.

---

### Post by Uncle Spellbinder on 2009-10-28
```
$ sudo dpkg -i /home/wombat/Desktop/ubuntuzilla*.deb
Selecting previously deselected package ubuntuzilla.
(Reading database ... 158000 files and directories currently installed.)
Unpacking ubuntuzilla (from .../ubuntuzilla-4.7.5-0ubuntu1-amd64.deb) ...
dpkg: dependency problems prevent configuration of ubuntuzilla:
 ubuntuzilla depends on libstdc++5; however:
  Package libstdc++5 is not installed.
dpkg: error processing ubuntuzilla (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 ubuntuzilla

```

Can't find **libstdc++5** anywhere. No synaptic, apt-get install. Nothing.

:-k

---

### Post by nanotube on 2009-10-28
hm, ok, so libstdc++5 used to be necessary to run the mozilla builds, but it appears that it is no longer included in karmic (only libstdc++6 is).

i just checked, and it appears that current builds do not require v5, and are fine with just v6, so i removed the libstdc++5 dependency.

please try one of these attached debs.

---

### Post by Uncle Spellbinder on 2009-10-28
Yes! that works. Though I cannot link to Firefox plugins. Says to manually link by inputting location. Tried several different locations with no luck.

---

### Post by nanotube on 2009-10-28
> **Uncle Spellbinder said:**
> Yes! that works. Though I cannot link to Firefox plugins. Says to manually link by inputting location. Tried several different locations with no luck.

ok, so some good news :)

about plugins: gah, they must have changed something again...
what's your output for
```
find /usr/lib -name 'libunixprintplugin.so'
```
and for
```
find /usr/lib -name 'libnullplugin.so'
```

---

### Post by Uncle Spellbinder on 2009-10-29
find /usr/lib -name 'libunixprintplugin.so'
```
/usr/lib/songbird/xulrunner/plugins/libunixprintplugin.so
```


find /usr/lib -name 'libnullplugin.so'
```
/usr/lib/songbird/xulrunner/plugins/libnullplugin.so
```


Weird. I don't recall ever installing Songbird????



EDIT:
UNINSTALLED Songbird. The output is now blank for both

---

### Post by nanotube on 2009-10-29
hrm...

in that case, say you install the flash plugin - where does it go? does a symlink show up maybe in /usr/lib/xulrunner/plugins, or maybe in /usr/lib/xulrunner-1.9.1.3/plugins

---

### Post by Uncle Spellbinder on 2009-10-29
Well, Its everywhere (along with the other plugins).

/usr/lib/xulrunner/plugins
/usr/lib/xulrunner-1.9.1.3/plugins 
/usr/lib/xulrunner-addons/plugins 
/usr/lib/firefox/plugins
/usr/lib/mozilla/plugins

/usr/lib64/xulrunner/plugins
/usr/lib64/xulrunner-1.9.1.3/plugins 
/usr/lib64/xulrunner-addons/plugins 
/usr/lib64/firefox/plugins
/usr/lib64/mozilla/plugins

---

### Post by kansasnoob on 2009-10-29
I'd forgotten about the plugin-path error. I'd just been hitting enter:

> Extracting archive

Trying to determine firefox plugin path...
Unable to determine firefox plugin path. Please determine the directory where firefox looks for plugins, and enter that directory manually here: 
Plugin path is:  

Linking plugins


Linking dictionaries


Linking launcher to new Firefox

Adding `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
Adding `local diversion of /usr/bin/mozilla-firefox to /usr/bin/mozilla-firefox.ubuntu'

The new Firefox version 3.5.4 has been installed successfully.

Would you like to set up automatic update checking for the official Mozilla build of Firefox (recommended)? This feature will regularly check for updates to Firefox, and put up a small unobtrusive notification message with update information, when a new release is available. [y/n] 
Please enter 'y' or 'n': y
no crontab for lance
Updater successfully installed to your crontab. Try 'crontab -l' to see your new crontab, 'crontab -e' if you decide to edit it.

Thank you for using Ubuntuzilla.

Please support this project! If you found Ubuntuzilla helpful, please consider showing your appreciation with a small donation. :)

Just visit the project website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) , and click the donate button.
lance@lance-desktop:~$ 


Probably not very helpful, but everything seems to work regardless:)

---

### Post by kansasnoob on 2009-10-29
Karmic install of Seamonkey (same problem with plugin-path):

> lance@lance-desktop:~$ ubuntuzilla.py -a install -p seamonkey

Welcome to the Ubuntuzilla Seamonkey script version 4.7.6

Ubuntuzilla is built only for Ubuntu Linux and other distributions derived from Ubuntu (such as Linux Mint, e.g.)

This script will now install the latest release of the official Mozilla build of Seamonkey on your Linux system. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) 

Retrieving the version of the latest release of Seamonkey from the Mozilla website...
The most recent release of Seamonkey is detected to be 2.0. Please make sure this is correct before proceeding. (You can confirm by going to [http://www.mozilla.org/](http://www.mozilla.org/))
If no version number shows, if the version shown is not the latest, or if you would like to install an older release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]? 
Please enter 'y' or 'n': y
Retrieving list of available localizations for Seamonkey ...
Please choose the localization (language) for Seamonkey. Enter the number of your choice from the list below. [If you do not see a list of localizations, please check the help section of our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) for steps you can take to resolve this problem.]
  0. be         Belarusian [&#1041;&#1077;&#1083;&#1072;&#1088;&#1091;&#1089;&#1082;&#1072;&#1103;]
  1. ca         Catalan [català]             
  2. cs         Czech [&#268;eština]             
  3. de         German [Deutsch]              
  4. en-US      English (US) [English (US)]   
  5. es-AR      Spanish (Argentina) [Español (de Argentina)]
  6. es-ES      Spanish (Spain) [Español (de España)]
  7. fr         French [Français]            
  8. gl         Galician [Galego]             
  9. hu         Hungarian [Magyar]            
 10. ka         Georgian [&#4325;&#4304;&#4320;&#4311;&#4323;&#4314;&#4312;]
 11. lt         Lithuanian [lietuvi&#371; kalba]  
 12. nb-NO      Norwegian (Bokmål) [Norsk bokmål]
 13. nl         Dutch [Nederlands]            
 14. pl         Polish [Polski]               
 15. pt-PT      Portuguese (Portugal) [Português (Europeu)]
 16. ru         Russian [&#1056;&#1091;&#1089;&#1089;&#1082;&#1080;&#1081;]      
 17. sk         Slovak [sloven&#269;ina]          
 18. sv-SE      Swedish [Svenska]             
 19. tr         Turkish [Türkçe]            

Enter your choice of localization (integer, from 0 to 19): 4
You have chosen localization en-US, English (US) [English (US)]. Is that correct [y/n]? 
Please enter 'y' or 'n': y

Backing up old Seamonkey preferences

Retrieving package name for Seamonkey ...
Success!: seamonkey-2.0.tar.bz2

Downloading Seamonkey archive from the Mozilla site

--2009-10-29 04:00:55--  [ftp://mozilla.isc.org/pub/mozilla.org/seamonkey/releases/2.0/linux-i686/en-US/seamonkey-2.0.tar.bz2](ftp://mozilla.isc.org/pub/mozilla.org/seamonkey/releases/2.0/linux-i686/en-US/seamonkey-2.0.tar.bz2)
           => `seamonkey-2.0.tar.bz2'
Resolving mozilla.isc.org... 204.152.184.113, 2001:4f8:0:2::1f
Connecting to mozilla.isc.org|204.152.184.113|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/seamonkey/releases/2.0/linux-i686/en-US ... done.
==> SIZE seamonkey-2.0.tar.bz2 ... 13166327
==> PASV ... done.    ==> RETR seamonkey-2.0.tar.bz2 ... done.
Length: 13166327 (13M)

100%[======================================>] 13,166,327   608K/s   in 22s     

2009-10-29 04:01:18 (589 KB/s) - `seamonkey-2.0.tar.bz2' saved [13166327]


Downloading Seamonkey MD5 sums from the Mozilla site

demunging: sed -i 's#/linux-i686/en-US/#/#' seamonkey-2.0.tar.bz2.md5...


Verifying Seamonkey MD5 sum

./seamonkey-2.0.tar.bz2: OK

Extracting archive

If you have the repositories version of Firefox installed, you can choose to link all the Firefox plugins to your Seamonkey install. Would you like to do that? [y/n]? 
Please enter 'y' or 'n': y
[B][COLOR="Red"]Trying to determine firefox plugin path...
Unable to determine firefox plugin path. Please determine the directory where firefox looks for plugins, and enter that directory manually here: 
Plugin path is:  

Linking plugins
[/COLOR][/B]

Linking dictionaries


Creating link to Seamonkey in /usr/bin/seamonkey

Would you like to create an Applications menu item for Seamonkey? [y/n]? 
Please enter 'y' or 'n': y
Creating Applications menu item for Seamonkey.


The new Seamonkey version 2.0 has been installed successfully.

If you are looking to use Seamonkey in other languages, head over to [http://www.mozilla.org/projects/seamonkey/releases/#l10n](http://www.mozilla.org/projects/seamonkey/releases/#l10n) and download the installable language pack of your choice.

Would you like to set up automatic update checking for the official Mozilla build of Seamonkey (recommended)? This feature will regularly check for updates to Seamonkey, and put up a small unobtrusive notification message with update information, when a new release is available. [y/n] 
Please enter 'y' or 'n': y
Updater successfully installed to your crontab. Try 'crontab -l' to see your new crontab, 'crontab -e' if you decide to edit it.

Thank you for using Ubuntuzilla.

Please support this project! If you found Ubuntuzilla helpful, please consider showing your appreciation with a small donation. :)

Just visit the project website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) , and click the donate button.
lance@lance-desktop:~$ 


I'll be in and out from time to time today but I'll try to pop back in if I can be of help.

---

### Post by mouratos1a on 2009-10-29
Dear all,
I am not very experienced with Ubuntu installations (manually) but I did download Seamonkey 2.0 and installed it following the ReadMe Instructions in the downloaded folder.
I managed to install it but failed to make it start from the GNome panel  something is wrong in the instructions (or in my mind!) so after all my efforts I still receive something like: "Cannot run child process..." or something similar...
Could somebody give a hint or a tip?
Thanks,
Mouratos

---

### Post by nanotube on 2009-10-29
ok thanks guys!
i'll talk some with the ubuntu mozilla team see what i can find out, then try to update my plugin path detection method to work everywhere, and post some test debs here.

---

### Post by nanotube on 2009-10-29
> **mouratos1a said:**
> Dear all,
I am not very experienced with Ubuntu installations (manually) but I did download Seamonkey 2.0 and installed it following the ReadMe Instructions in the downloaded folder.
I managed to install it but failed to make it start from the GNome panel  something is wrong in the instructions (or in my mind!) so after all my efforts I still receive something like: "Cannot run child process..." or something similar...
Could somebody give a hint or a tip?
Thanks,
Mouratos

did you use ubuntuzilla to install, or manually download seamonkey and extract etc? if not ubuntuzilla, then you're in the wrong section of the forum. :)

---

### Post by nanotube on 2009-10-29
ok, new .debs to test

now i'm just using /usr/lib/mozilla/plugins which should work fine on currently supported ubuntu versions.

please give these a try. would like to see how this pans out on hardy-karmic, as far as actual availability of plugins after install.

---

### Post by kansasnoob on 2009-10-29
Works great:

> Extracting archive

Using plugin path: /usr/lib/mozilla/plugins

Linking plugins


Linking dictionaries


Linking launcher to new Firefox

Adding `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
Adding `local diversion of /usr/bin/mozilla-firefox to /usr/bin/mozilla-firefox.ubuntu'

The new Firefox version 3.5.4 has been installed successfully.

Would you like to set up automatic update checking for the official Mozilla build of Firefox (recommended)? This feature will regularly check for updates to Firefox, and put up a small unobtrusive notification message with update information, when a new release is available. [y/n] 
Please enter 'y' or 'n': y
Updater successfully installed to your crontab. Try 'crontab -l' to see your new crontab, 'crontab -e' if you decide to edit it.

Thank you for using Ubuntuzilla.

Please support this project! If you found Ubuntuzilla helpful, please consider showing your appreciation with a small donation. :)

Just visit the project website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) , and click the donate button.
lance@lance-desktop:~$ 


BTW I began by removing the Mozilla builds of FF and Seamonkey:

ubuntuzilla.py -a remove -p firefox
ubuntuzilla.py -a remove -p seamonkey

And purging the prior Ubuntuzilla.

I'll check out Seamonkey again now.

---

### Post by nanotube on 2009-10-29
kansasnoob: good news - thanks for testing! :)

was that on jaunty or karmic? and did the plugins show up for firefox after install (i.e, start firefox, see that you see in about:plugins what you expect)

---

### Post by kansasnoob on 2009-10-29
Seamonkey worked fine also:

> If you have the repositories version of Firefox installed, you can choose to link all the Firefox plugins to your Seamonkey install. Would you like to do that? [y/n]? 
Please enter 'y' or 'n': y
Using plugin path: /usr/lib/mozilla/plugins

Linking plugins


Linking dictionaries


Creating link to Seamonkey in /usr/bin/seamonkey

Would you like to create an Applications menu item for Seamonkey? [y/n]? 
Please enter 'y' or 'n': y
Creating Applications menu item for Seamonkey.


The new Seamonkey version 2.0 has been installed successfully.


I did both of these in Karmic, I was just wondering if I shouldn't do at least Firefox in Jaunty just to check for possible regression?????

Oh, yes, I did check to be sure the plugins actually work.

---

### Post by nanotube on 2009-10-29
> **kansasnoob said:**
> 
Oh, yes, I did check to be sure the plugins actually work.

excellent!

and yes, it would be nice if you could run a quick test in jaunty as well. please :)

---

### Post by kansasnoob on 2009-10-29
Here's Jaunty:

> Extracting archive

Using plugin path: /usr/lib/mozilla/plugins

Linking plugins


Linking dictionaries


Linking launcher to new Firefox

Adding `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
Adding `local diversion of /usr/bin/mozilla-firefox to /usr/bin/mozilla-firefox.ubuntu'

The new Firefox version 3.5.4 has been installed successfully.



---

### Post by nanotube on 2009-10-29
double check: the plugins show up?

---

### Post by kansasnoob on 2009-10-29
Seamonkey + Jaunty:

> If you have the repositories version of Firefox installed, you can choose to link all the Firefox plugins to your Seamonkey install. Would you like to do that? [y/n]? 
Please enter 'y' or 'n': y
Using plugin path: /usr/lib/mozilla/plugins

Linking plugins


Linking dictionaries


Creating link to Seamonkey in /usr/bin/seamonkey

Would you like to create an Applications menu item for Seamonkey? [y/n]? 
Please enter 'y' or 'n': y
Creating Applications menu item for Seamonkey.


The new Seamonkey version 2.0 has been installed successfully.


Would you like me to check with a Hardy Live CD also?

---

### Post by kansasnoob on 2009-10-29
> **nanotube said:**
> double check: the plugins show up?

Yep.

I even actually always try flash.

---

### Post by nanotube on 2009-10-29
all excellent news! :)

if you have hardy handy, then yes, please try, and if that one works, then i'll push out the release.

thanks for all the testing! :)

---

### Post by kansasnoob on 2009-10-29
I'll boot her up and get back to you.

---

### Post by nanotube on 2009-10-29
cool thanks - looking forward to the results :)

---

### Post by kansasnoob on 2009-10-29
I'm probably just asleep at the wheel here but when I try to open that latest .deb gdebi spits this at me:

> /tmp/ubuntuzilla-4.7.6-0ubuntu1-i386.deb could not be saved, because you cannot change the contents of that folder.

Change the folder properties and try again, or try saving in a different location

Don't laugh, we all have our moments:p

Actually I guess it's the download manager that does that. Gdebi does try to open.

---

### Post by nanotube on 2009-10-29
could you just save to desktop? then doubleclick?

---

### Post by kansasnoob on 2009-10-29
> **nanotube said:**
> could you just save to desktop? then doubleclick?

I was just going to say I figured that out. After saving to desktop I had to enable some additional repos so libnotify-bin could be installed.

I'll go ahead and run the script now and get back to you.

---

### Post by nanotube on 2009-10-29
ok sounds good :)

---

### Post by kansasnoob on 2009-10-29
Hmmmm, not so good. The script runs fine but afterwards I showed no plugins.

I've even repeated that twice, making sure that Firefox was closed. That is I removed and reinstalled checking what plugins were listed before installing if I typed "about:plugins" and after.

The pre-installed plugins fail to link but those I manually install - flash and java - do show up :(

Here's the script if that provides any clues:

> ubuntu@ubuntu:~$ ubuntuzilla.py -a install -p firefox

Welcome to the Ubuntuzilla Firefox script version 4.7.6

Ubuntuzilla is built only for Ubuntu Linux and other distributions derived from Ubuntu (such as Linux Mint, e.g.)

This script will now install the latest release of the official Mozilla build of Firefox on your Linux system. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) 

Retrieving the version of the latest release of Firefox from the Mozilla website...
The most recent release of Firefox is detected to be 3.5.4. Please make sure this is correct before proceeding. (You can confirm by going to [http://www.mozilla.org/](http://www.mozilla.org/))
If no version number shows, if the version shown is not the latest, or if you would like to install an older release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]? 
Please enter 'y' or 'n': y
Please enter 'y' or 'n': y
Retrieving list of available localizations for Firefox ...
Please choose the localization (language) for Firefox. Enter the number of your choice from the list below. [If you do not see a list of localizations, please check the help section of our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) for steps you can take to resolve this problem.]
  0. af         Afrikaans [Afrikaans]         
  1. ar         Arabic [&#1593;&#1585;&#1576;&#1610;]             
  2. as         Assamese [&#2437;&#2488;&#2478;&#2496;&#2479;&#2492;&#2494;]
  3. be         Belarusian [&#1041;&#1077;&#1083;&#1072;&#1088;&#1091;&#1089;&#1082;&#1072;&#1103;]
  4. bg         Bulgarian [&#1041;&#1098;&#1083;&#1075;&#1072;&#1088;&#1089;&#1082;&#1080;]
  5. bn-BD      Bengali (Bangladesh) [&#2476;&#2494;&#2434;&#2482;&#2494; (&#2476;&#2494;&#2434;&#2482;&#2494;&#2470;&#2503;&#2486;)]
  6. bn-IN      Bengali (India) [&#2476;&#2494;&#2434;&#2482;&#2494; (&#2477;&#2494;&#2480;&#2468;)]
  7. ca         Catalan [català]             
  8. cs         Czech [&#268;eština]             
  9. cy                                       
 10. da         Danish [Dansk]                
 11. de         German [Deutsch]              
 12. el         Greek [&#917;&#955;&#955;&#951;&#957;&#953;&#954;&#940;]      
 13. en-GB      English (British) [English (British)]
 14. en-US      English (US) [English (US)]   
 15. eo         Esperanto [Esperanto]         
 16. es-AR      Spanish (Argentina) [Español (de Argentina)]
 17. es-CL      Spanish (Chile) [Español (de Chile)]
 18. es-ES      Spanish (Spain) [Español (de España)]
 19. es-MX      Spanish (Mexico) [Español (de México)]
 20. et         Estonian [Eesti keel]         
 21. eu         Basque [Euskara]              
 22. fa         Persian [&#1601;&#1575;&#1585;&#1587;&#1740;]          
 23. fi         Finnish [suomi]               
 24. fr         French [Français]            
 25. fy-NL      Frisian [Frysk]               
 26. ga-IE      Irish [Gaeilge]               
 27. gl         Galician [Galego]             
 28. gu-IN      Gujarati [&#2711;&#2753;&#2716;&#2736;&#2750;&#2724;&#2752;]
 29. he         Hebrew [&#1506;&#1489;&#1512;&#1497;&#1514;]           
 30. hi-IN      Hindi (India) [&#2361;&#2367;&#2344;&#2381;&#2342;&#2368; (&#2349;&#2366;&#2352;&#2340;)]
 31. hr         Croatian [Hrvatski]           
 32. hu         Hungarian [Magyar]            
 33. id         Indonesian [Bahasa Indonesia] 
 34. is         Icelandic [íslenska]         
 35. it         Italian [Italiano]            
 36. ja         Japanese [&#26085;&#26412;&#35486;]          
 37. ka         Georgian [&#4325;&#4304;&#4320;&#4311;&#4323;&#4314;&#4312;]
 38. kk         Kazakh [&#1178;&#1072;&#1079;&#1072;&#1179;]           
 39. kn         Kannada [&#3221;&#3240;&#3277;&#3240;&#3233;]     
 40. ko         Korean [&#54620;&#44397;&#50612;]            
 41. ku         Kurdish [Kurdî]              
 42. lt         Lithuanian [lietuvi&#371; kalba]  
 43. lv         Latvian [Latviešu]           
 44. mk         Macedonian [&#1052;&#1072;&#1082;&#1077;&#1076;&#1086;&#1085;&#1089;&#1082;&#1080;]
 45. ml         Malayalam [&#3374;&#3378;&#3375;&#3390;&#3379;&#3330;]
 46. mn         Mongolian [&#1052;&#1086;&#1085;&#1075;&#1086;&#1083;]      
 47. mr         Marathi [&#2350;&#2352;&#2366;&#2336;&#2368;]     
 48. nb-NO      Norwegian (Bokmål) [Norsk bokmål]
 49. nl         Dutch [Nederlands]            
 50. nn-NO      Norwegian (Nynorsk) [Norsk nynorsk]
 51. oc         Occitan (Lengadocian) [occitan (lengadocian)]
 52. or         Oriya [&#2835;&#2849;&#2876;&#2879;&#2822;]       
 53. pa-IN      Punjabi [&#2602;&#2672;&#2588;&#2622;&#2604;&#2624;]  
 54. pl         Polish [Polski]               
 55. pt-BR      Portuguese (Brazilian) [Português (do Brasil)]
 56. pt-PT      Portuguese (Portugal) [Português (Europeu)]
 57. rm         Romansh [rumantsch]           
 58. ro         Romanian [român&#259;]           
 59. ru         Russian [&#1056;&#1091;&#1089;&#1089;&#1082;&#1080;&#1081;]      
 60. si         Sinhala [&#3523;&#3538;&#3458;&#3524;&#3517;]     
 61. sk         Slovak [sloven&#269;ina]          
 62. sl         Slovenian [slovensko]         
 63. sq         Albanian [Shqip]              
 64. sr         Serbian [&#1057;&#1088;&#1087;&#1089;&#1082;&#1080;]        
 65. sv-SE      Swedish [Svenska]             
 66. ta-LK      Tamil (Sri Lanka) [&#2980;&#2990;&#3007;&#2996;&#3021; (&#2951;&#2994;&#2969;&#3021;&#2965;&#3016;)]
 67. ta         Tamil [&#2980;&#2990;&#3007;&#2996;&#3021;]       
 68. te         Telugu [&#3108;&#3142;&#3122;&#3137;&#3095;&#3137;]   
 69. th         Thai [&#3652;&#3607;&#3618;]              
 70. tr         Turkish [Türkçe]            
 71. uk         Ukrainian [&#1059;&#1082;&#1088;&#1072;&#1111;&#1085;&#1089;&#1100;&#1082;&#1072;]
 72. vi         Vietnamese [Ti&#7871;ng Vi&#7879;t]   
 73. zh-CN      Chinese (Simplified) [&#20013;&#25991; (&#31616;&#20307;)]
 74. zh-TW      Chinese (Traditional) [&#27491;&#39636;&#20013;&#25991; (&#32321;&#39636;)]

Enter your choice of localization (integer, from 0 to 74): 14
You have chosen localization en-US, English (US) [English (US)]. Is that correct [y/n]? 
Please enter 'y' or 'n': y

Updating repositories information with apt-get update. You may be prompted for your password.

Ign cdrom://Ubuntu 8.04.3 _Hardy Heron_ - Release i386 (20090713.1) hardy/main Translation-en_US
Ign cdrom://Ubuntu 8.04.3 _Hardy Heron_ - Release i386 (20090713.1) hardy/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Sources
Reading package lists... Done

Making sure that the repositories version of Firefox is installed...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 117 not upgraded.

Backing up old Firefox preferences

Retrieving package name for Firefox ...
Success!: firefox-3.5.4.tar.bz2

Downloading Firefox archive from the Mozilla site

--20:52:04--  [ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.4/linux-i686/en-US/firefox-3.5.4.tar.bz2](ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.4/linux-i686/en-US/firefox-3.5.4.tar.bz2)
           => `firefox-3.5.4.tar.bz2'
Resolving mozilla.isc.org... 204.152.184.113
Connecting to mozilla.isc.org|204.152.184.113|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.5.4/linux-i686/en-US ... done.
==> PASV ... done.    ==> RETR firefox-3.5.4.tar.bz2 ... done.
Length: 9,923,819 (9.5M) (unauthoritative)

100%[====================================>] 9,923,819    314.25K/s    ETA 00:00

20:52:24 (497.79 KB/s) - `firefox-3.5.4.tar.bz2' saved [9923819]


Downloading Firefox signature from the Mozilla site

--20:52:24--  [ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.4/linux-i686/en-US/firefox-3.5.4.tar.bz2.asc](ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.4/linux-i686/en-US/firefox-3.5.4.tar.bz2.asc)
           => `firefox-3.5.4.tar.bz2.asc'
Resolving mozilla.isc.org... 204.152.184.113
Connecting to mozilla.isc.org|204.152.184.113|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.5.4/linux-i686/en-US ... done.
==> PASV ... done.    ==> RETR firefox-3.5.4.tar.bz2.asc ... done.
Length: 194 (unauthoritative)

100%[====================================>] 194           --.--K/s             

20:52:25 (17.16 KB/s) - `firefox-3.5.4.tar.bz2.asc' saved [194]

tru::1:1256847822:0:3:1:5
pub:-:1024:17:696E34310E3606D9:2005-09-29:::-:Mozilla Software Releases <releases@mozilla.org>::scESC:
sub:e:1024:17:C660CCE21AF32821:2005-09-29:2006-09-29:::::s:
sub:-:2048:16:70474DABAFE99880:2005-09-29::::::e:
tru::1:1256847822:0:3:1:5
pub:-:1024:17:74474499812347DD:2007-07-17:2011-07-20::-:Mozilla Software Releases <releases@mozilla.org>::scESC:
sub:-:1024:17:B57B548417785FE8:2007-07-17:2011-07-20:::::s:
sub:-:2048:16:CB3A74DF1B0EC2E7:2007-07-17:2011-07-20:::::e:

Verifying signature...
Note: do not worry about "untrusted key" warnings. That is normal behavior for newly imported keys.

gpg: Signature made Fri 16 Oct 2009 08:37:55 PM UTC using DSA key ID 17785FE8
gpg: Good signature from "Mozilla Software Releases <releases@mozilla.org>"
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: 8D6F 1BA4 A340 4DDB 3F2F  D080 7447 4499 8123 47DD
     Subkey fingerprint: 3338 E6BA FF10 3B3D A6A9  E424 B57B 5484 1778 5FE8

Extracting archive

Using plugin path: /usr/lib/mozilla/plugins

Linking plugins


Linking dictionaries


Linking launcher to new Firefox

Adding `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
Adding `local diversion of /usr/bin/mozilla-firefox to /usr/bin/mozilla-firefox.ubuntu'

The new Firefox version 3.5.4 has been installed successfully.

Would you like to set up automatic update checking for the official Mozilla build of Firefox (recommended)? This feature will regularly check for updates to Firefox, and put up a small unobtrusive notification message with update information, when a new release is available. [y/n] 
Please enter 'y' or 'n': y
Updater successfully installed to your crontab. Try 'crontab -l' to see your new crontab, 'crontab -e' if you decide to edit it.

Thank you for using Ubuntuzilla.

Please support this project! If you found Ubuntuzilla helpful, please consider showing your appreciation with a small donation. :)

Just visit the project website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) , and click the donate button.
ubuntu@ubuntu:~$ 



---

### Post by kansasnoob on 2009-10-29
Just thinking out loud here:

I did several reinstalls of Karmic during the development cycle and I swear just hitting enter when it asked for a plugin path still resulted in successful linkage of the plugins.

I need to lay down for a while right now, but I'll check back either later tonight or in the AM.

---

### Post by nanotube on 2009-10-29
hmm what are the preinstalled plugins? you mean like totem and friends?

what do you see in /usr/lib/mozilla/plugins/ ?

what about /usr/lib/xulrunner-addons/plugins/

---

### Post by nanotube on 2009-10-29
> **kansasnoob said:**
> Just thinking out loud here:

I did several reinstalls of Karmic during the development cycle and I swear just hitting enter when it asked for a plugin path still resulted in successful linkage of the plugins.

I need to lay down for a while right now, but I'll check back either later tonight or in the AM.

hey good thinking...
indeed, it seems that firefox picks up plugins from /usr/lib/mozilla/plugins by default, without having to be linked directly to them.

on hardy, though, it seems that the totem plugin (and possibly others) stick their stuff into /usr/lib/xulrunner-addons/plugins, from where firefox does /not/ pick stuff up by default. So, it seems that we can get rid of plugin linking completely on everything after hardy...

well, that makes it simple - i'll just go back to the old code (which seems to have worked just fine), and leave the default (if plugin path not found, as on karmic) to do nothing.

thanks again for all your hard work! :)

---

### Post by nanotube on 2009-10-29
ok, so here are the freshest debs for testing
now we find plugins for hardy, and do nothing for later ubuntu releases.

would appreciate a little testing before i push it out.

---

### Post by akwala on 2009-10-29
RE: ubuntuzilla-4.7.6-0ubuntu1-amd64.deb on Jaunty

> ubuntuzilla.py -a install -p seamonkey

...results in:

```
Backing up old Seamonkey preferences

cp: cannot open `/home/aslam/.mozilla/firefox/v7yozn03.akMedia/chrome/ubx-style.css' for reading: Permission denied
cp: cannot open `/home/aslam/.mozilla/firefox/oqxon5io.optDefault/chrome/ubx-style.css' for reading: Permission denied
cp: cannot open `/home/aslam/.mozilla/firefox/8x1q828d.akPrimary/chrome/ubx-style.css' for reading: Permission denied
cp: cannot open `/home/aslam/.mozilla/firefox.3.0-replaced/8x9k5cp7.optDefault/chrome/ubx-style.css' for reading: Permission denied
cp -R ~/.mozilla ~/.mozilla_backup_$(date -Iseconds)
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1314, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 306, in start
    si.start()
  File "/usr/local/bin/ubuntuzilla.py", line 343, in start
    self.install()
  File "/usr/local/bin/ubuntuzilla.py", line 756, in install
    self.backupProfile()
  File "/usr/local/bin/ubuntuzilla.py", line 1125, in backupProfile
    self.util.execSystemCommand(executionstring="cp -R ~/.mozilla ~/.mozilla_backup_$(date -Iseconds)")
  File "/usr/local/bin/ubuntuzilla.py", line 143, in execSystemCommand
    raise SystemCommandExecutionError, "Command has not completed successfully. If this problem persists, please seek help at our website, " + self.version.url
__main__.SystemCommandExecutionError: Command has not completed successfully. If this problem persists, please seek help at our website, http://ubuntuzilla.sourceforge.net/

```

Sorry if I've missed an earlier discussion re this... Is the backing up of Firefox profiles intentional for a Seamonkey update?

---

### Post by nanotube on 2009-10-29
> **akwala said:**
> 

Sorry if I've missed an earlier discussion re this... Is the backing up of Firefox profiles intentional for a Seamonkey update?

Hi
yes, it backs up the entire .mozilla directory for "just in case"

the errors you are getting is because the ownership of some of your files in the firefox profile is messed up.
you should run command:
```
sudo chown -R youruser:youruser ~/.mozilla
```
to fix that and try again
or if you would like to skip the backup step, add the '-b' option.

---

### Post by Uncle Spellbinder on 2009-10-29
Oh, well. Must be something on my end. Tried the last 2 test debs and nothing. I got he following on the latest test deb...

```
If you have the repositories version of Firefox installed, you can choose to link all the Firefox plugins to your Seamonkey install. Would you like to do that? [y/n]? 
Please enter 'y' or 'n': y
Ubuntu version 9.10
Not linking plugin path, your plugins should still show up.

Linking dictionaries


Creating link to Seamonkey in /usr/bin/seamonkey
```


Still nothing. Though I do see the "default plugin" in SeaMonkey's add-on manager>plugins.

Very odd. I'll be doing a fresh install of Karmic over the weekend. I'll try again then. 

Appreciate your help!

---

### Post by nanotube on 2009-10-29
> **Uncle Spellbinder said:**
> Oh, well. Must be something on my end. Tried the last 2 test debs and nothing. I got he following on the latest test deb...

Still nothing. Though I do see the "default plugin" in SeaMonkey's add-on manager>plugins.

Very odd. I'll be doing a fresh install of Karmic over the weekend. I'll try again then. 

Appreciate your help!

hrm, strange - i tried here on intrepid without linking plugin dir, and my seamonkey automagically picked up all the plugins, totem, java, flash, etc... i'll look around some more...

---

### Post by nanotube on 2009-10-29
ok, another set of debs for testing :)

i just left the old plugin path detection, and put the failover as /usr/lib/mozilla/plugins. 

hope it will work now. please test. :)

---

### Post by akwala on 2009-10-30
> **nanotube said:**
> ok, another set of debs for testing :)

i just left the old plugin path detection, and put the failover as /usr/lib/mozilla/plugins. 

hope it will work now. please test. :)

Did the following after (re)installing this 4.7.6 amd64 deb (on Jaunty):
> ubuntuzilla.py -a install -p seamonkey

Seamonkey crashes upon launching...
```
$ seamonkey -ProfileManager
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgiofam.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiofam.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
```
...no crash log seems to be generated.

---

### Post by Uncle Spellbinder on 2009-10-30
Yep. I get a notice that "SeaMonkey is already running".

---

### Post by nanotube on 2009-10-30
> **akwala said:**
> Did the following after (re)installing this 4.7.6 amd64 deb (on Jaunty):
> ubuntuzilla.py -a install -p seamonkey

Seamonkey crashes upon launching...
```
$ seamonkey -ProfileManager
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgiofam.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiofam.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
```
...no crash log seems to be generated.

well the builds on mozilla releases are all 32bit, so it's expected that 64bit plugins are not going to be able to load.

as to the crash, here's a possible fix:
 if you've had seamonkey v1 installed earlier, you have to manually remove the old /opt/seamonkey (or run ubuntuzilla's remove action), and reinstall.  otherwise, some v1 files get left over and cause seamonkey to crash.

---

### Post by nanotube on 2009-10-30
> **Uncle Spellbinder said:**
> Yep. I get a notice that "SeaMonkey is already running".

try looking for it in the process list and killing it

if that doesn't help (or it's not showing up in 'ps ax | grep seamonkey' output) try deleting the .lock file from the profile, or try starting with a fresh profile.

---

### Post by kansasnoob on 2009-10-30
Newest from post #47, Hardy + Firefox:

> Extracting archive

Trying to determine firefox plugin path...
Plugin path is:  /usr/lib/xulrunner-addons/plugins

Linking plugins


Linking dictionaries


Linking launcher to new Firefox

Adding `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
Adding `local diversion of /usr/bin/mozilla-firefox to /usr/bin/mozilla-firefox.ubuntu'

The new Firefox version 3.5.4 has been installed successfully.


Looks great, now I'll try Seamonkey.

Plugins are properly linked and working.

---

### Post by kansasnoob on 2009-10-30
Here's the Seamonkey script from Hardy:

> If you have the repositories version of Firefox installed, you can choose to link all the Firefox plugins to your Seamonkey install. Would you like to do that? [y/n]? 
Please enter 'y' or 'n': y
Trying to determine firefox plugin path...
Plugin path is:  /usr/lib/xulrunner-addons/plugins

Linking plugins


Linking dictionaries


Creating link to Seamonkey in /usr/bin/seamonkey

Would you like to create an Applications menu item for Seamonkey? [y/n]? 
Please enter 'y' or 'n': y
Creating Applications menu item for Seamonkey.


The new Seamonkey version 2.0 has been installed successfully.


I think it's OK but want to look more closely. (I'm not used to using Seamonkey so I want to do some double checking.)

That does appear to work alright. I verifed that Flash, Totem and print actually worked, but I'm going to check the behavior of the repo version of Seamonkey against that of the Mozilla build in Karmic and Jaunty.

It's always harder and slower to work from the Live desktop.

---

### Post by kansasnoob on 2009-10-30
Karmic + Firefox works great (BTW I did remove and purge first):

> Extracting archive

Trying to determine firefox plugin path...
Plugin path is:  /usr/lib/mozilla/plugins

Linking plugins


Linking dictionaries


Linking launcher to new Firefox

Adding `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
Adding `local diversion of /usr/bin/mozilla-firefox to /usr/bin/mozilla-firefox.ubuntu'

The new Firefox version 3.5.4 has been installed successfully.


I'm going to give Seamonkey a much closer look in Karmic and then I'll check things out in Jaunty.

---

### Post by kansasnoob on 2009-10-30
Seamonkey + Karmic:

> If you have the repositories version of Firefox installed, you can choose to link all the Firefox plugins to your Seamonkey install. Would you like to do that? [y/n]? 
Please enter 'y' or 'n': y
Trying to determine firefox plugin path...
Plugin path is:  /usr/lib/mozilla/plugins

Linking plugins


Linking dictionaries


Creating link to Seamonkey in /usr/bin/seamonkey

Adding `local diversion of /usr/bin/seamonkey to /usr/bin/seamonkey.ubuntu'
Would you like to create an Applications menu item for Seamonkey? [y/n]? 
Please enter 'y' or 'n': y
Creating Applications menu item for Seamonkey.


The new Seamonkey version 2.0 has been installed successfully.


I actually checked the behavior of Seamonkey prior to using your script by installing the repo version.

All plugins linked properly, the only anomaly is that I ended up with two Seamonkey launchers in the Internet menu. Both launch version 2.0 so I removed one in the Main Menu app.

**I do need to revisit the plugin behavior in Hardy!**

I'm going to check out Jaunty first though.

---

### Post by kansasnoob on 2009-10-30
Seamonkey in Jaunty:

> ./seamonkey-2.0.tar.bz2: OK

Extracting archive

If you have the repositories version of Firefox installed, you can choose to link all the Firefox plugins to your Seamonkey install. Would you like to do that? [y/n]? 
Please enter 'y' or 'n': y
Trying to determine firefox plugin path...
Plugin path is:  /usr/lib/xulrunner-addons/plugins

Linking plugins


Linking dictionaries


Creating link to Seamonkey in /usr/bin/seamonkey

Adding `local diversion of /usr/bin/seamonkey to /usr/bin/seamonkey.ubuntu'
Would you like to create an Applications menu item for Seamonkey? [y/n]? 
Please enter 'y' or 'n': y
Creating Applications menu item for Seamonkey.


The new Seamonkey version 2.0 has been installed successfully.


Plugins are fine, same behavior with the two launchers which I wouldn't consider an issue at all.

I really do need to have another look at Hardy and I'll do that as soon as I'm done checking out  Firefox in Jaunty.

---

### Post by kansasnoob on 2009-10-30
Two thumbs up on Jaunty + Firefox:

> Trying to determine firefox plugin path...
Plugin path is:  /usr/lib/xulrunner-addons/plugins

Linking plugins


Linking dictionaries


Linking launcher to new Firefox

Adding `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
Adding `local diversion of /usr/bin/mozilla-firefox to /usr/bin/mozilla-firefox.ubuntu'

The new Firefox version 3.5.4 has been installed successfully.


I'm going to revisit Hardy now that I've made myself a bit more familiar with Seahorse.

---

### Post by kansasnoob on 2009-10-30
OK, I'm in Hardy now, using only the repo versions of Firefox and Seamonkey. Firefox lists the common plugins:

> Installed plugins
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.
Default Plugin

    File name: libnullplugin.so
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

MIME Type 	Description 	Suffixes 	Enabled
* 	All types 	.* 	No
Demo Print Plugin for unix/linux

    File name: libunixprintplugin.so
    The demo print plugin for unix.

MIME Type 	Description 	Suffixes 	Enabled
application/x-print-unix-nsplugin 	Demo Print Plugin for Unix/Linux 	.pnt 	Yes
Totem Web Browser Plugin 2.22.1

    File name: libtotem-basic-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-ogg 	- 	ogg 	Yes
application/ogg 	Ogg multimedia 	ogg 	Yes
audio/ogg 	Ogg Audio 	oga 	Yes
audio/x-ogg 	Ogg Audio 	ogg 	Yes
video/ogg 	Ogg Video 	ogv 	Yes
video/x-ogg 	Ogg Video 	ogg 	Yes
application/annodex 	- 	anx 	Yes
audio/annodex 	- 	axa 	Yes
video/annodex 	- 	axv 	Yes
video/mpeg 	MPEG video 	mpg, mpeg, mpe 	Yes
audio/wav 	WAV audio 	wav 	Yes
audio/x-wav 	WAV audio 	wav 	Yes
audio/mpeg 	MP3 audio 	mp3 	Yes
application/x-nsv-vp3-mp3 	NullSoft video 	nsv 	Yes
video/flv 	Flash video 	flv 	Yes
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible (compatible; Totem)

    File name: libtotem-complex-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio-plugin 	RealAudio document 	rpm 	Yes
VLC Multimedia Plugin (compatible Totem 2.22.1)

    File name: libtotem-cone-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-vlc-plugin 	unknown 		Yes
application/vlc 	unknown 		Yes
video/x-google-vlc-plugin 	unknown 		Yes
Windows Media Player Plug-in 10 (compatible; Totem)

    File name: libtotem-gmp-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-mplayer2 	AVI video 	avi, wma, wmv 	Yes
video/x-ms-asf-plugin 	ASF video 	asf, wmv 	Yes
video/x-msvideo 	AVI video 	asf, wmv 	Yes
video/x-ms-asf 	ASF video 	asf 	Yes
video/x-ms-wmv 	Windows Media video 	wmv 	Yes
video/x-wmv 	Windows Media video 	wmv 	Yes
video/x-ms-wvx 	Microsoft ASX playlist 	wmv 	Yes
video/x-ms-wm 	ASF video 	wmv 	Yes
application/x-ms-wms 	Windows Media video 	wms 	Yes
application/asx 	Microsoft ASX playlist 	asx 	Yes
audio/x-ms-wma 	Windows Media audio 	wma 	Yes
DivX® Web Player

    File name: libtotem-mully-plugin.so
    DivX Web Player version 1.4.0.233

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	AVI video 	divx 	Yes
QuickTime Plug-in 7.2.0

    File name: libtotem-narrowspace-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QuickTime video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	QuickTime image 	pict, pict1, pict2 	Yes
video/x-m4v 	MPEG-4 video 	m4v 	Yes
iTunes Application Detector

    File name: librhythmbox-itms-detection-plugin.so
    This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.

MIME Type 	Description 	Suffixes 	Enabled
application/itunes-plugin 			Yes


But Seamonkey only shows:

> No plug-ins are installed
Find more information about browser plug-ins at mozilla.org.
Help for installing plug-ins is available from plugindoc.mozdev.org.


Anyway that's not on you. What I saw after installing the newest Ubuntuzilla and running the script for Firefox and then for Seamonkey was the same list for Firefox plugins but only "itunes" in Seamonkey.

Then after installing the flash plugin it did show up and work in Seamonkey. Anyway that's an anomaly that exists in Hardy regardless of which version of Seamonkey is installed.

I may investigate this a bit further, but I think your script is good to go!

---

### Post by kansasnoob on 2009-10-30
Hmmmmm, I tried first installing seamonkey-gnome-support and then running the script but the behavior was the same.

Oddly the repo version shows no plugins but after running your script it shows itunes.

Anyway I don't see how this is on you.

Feel free to PM me if you need any further testing done, and keep up the good work, it's much appreciated :)

---

### Post by nanotube on 2009-10-30
Hi

Thanks for all the testing! Looks good, I will push out a release.

As far as hardy, plugins, and seamonkey - indeed seems strange, but if the repos version doesn't pick them up either, then i am not going to worry about it too much.

---

### Post by nanotube on 2009-10-30
made release 4.7.6, it's out and live. thanks to everyone who helped test this release! :)

---

### Post by akwala on 2009-10-31
> **nanotube said:**
> as to the crash, here's a possible fix:
 if you've had seamonkey v1 installed earlier, you have to manually remove the old /opt/seamonkey (or run ubuntuzilla's remove action), and reinstall.  otherwise, some v1 files get left over and cause seamonkey to crash.
Thanks, this worked, and Seamonkey has been behaving as expected.

However, the [COLOR=Red]***following***[/COLOR] causes the "checkforupdategui" cron to trigger the update alert despite having already updated (it's an error I got in one of my attempts the other night):[INDENT][FONT=Courier New]$ ubuntuzilla.py -a checkforupdatetext -p seamonkey
Retrieving the version of the latest release of Seamonkey from the Mozilla website...
[COLOR=Red]***The version of Seamonkey currently installed is awk: warning: escape sequence `\.' treated as plain `.'***[/COLOR]
The latest version available from Mozilla is 2.0
Please refer to the detailed instructions for updating Seamonkey on our site, [http://ubuntuzilla.sourceforge.net/#Update_Official_Mozilla_Build_of_Seamonkey](http://ubuntuzilla.sourceforge.net/#Update_Official_Mozilla_Build_of_Seamonkey) .

If you have not yet installed the official Mozilla build with the help of the Ubuntuzilla script, and are still running the repositories version, run this script with '-install' to install the latest Mozilla build of Seamonkey .[/FONT]
[/INDENT]How can I fix it?

---

### Post by nanotube on 2009-10-31
hi
you're probably configured to use gawk instead of mawk. see the solve on this thread:
[http://ubuntuforums.org/showthread.php?t=474549](http://ubuntuforums.org/showthread.php?t=474549)

---

### Post by nanotube on 2009-11-01
fyi: i've just pushed out the next version which fixes this - now works equally well with both mawk and gawk.

---

### Post by akwala on 2009-11-01
> **nanotube said:**
> fyi: i've just pushed out the next version which fixes this - now works equally well with both mawk and gawk.
Thanks! It works as advertised :)

---

### Post by nanotube on 2009-11-02
> **akwala said:**
> Thanks! It works as advertised :)

excellent! :)

---

### Post by Uncle Spellbinder on 2009-11-04
Well. I did it! I actually installed Ubuntu 9.10 32-bit. Then, for a very easy install of SeaMonkey 2, I used UbuntuZilla.

All plugins are present an functioning.

Thanks for a great way to get my favorite browser on my favorite flavor of Linux!

---

### Post by nanotube on 2009-11-04
> **Uncle Spellbinder said:**
> Well. I did it! I actually installed Ubuntu 9.10 32-bit. Then, for a very easy install of SeaMonkey 2, I used UbuntuZilla.

All plugins are present an functioning.

Thanks for a great way to get my favorite browser on my favorite flavor of Linux!

you're welcome, and thanks for the feedback! :)

---

### Post by daniele80 on 2009-12-16
```
daniele@daniele-laptop:~$ ubuntuzilla.py -a install -p seamonkey

Welcome to the Ubuntuzilla Seamonkey script version 4.8.2

Ubuntuzilla is built only for Ubuntu Linux and other distributions derived from Ubuntu (such as Linux Mint, e.g.)

This script will now install the latest release of the official Mozilla build of Seamonkey on your Linux system. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at http://ubuntuzilla.sourceforge.net/ 

Retrieving the version of the latest release of Seamonkey from the Mozilla website...
The most recent release of Seamonkey is detected to be 2.0.1.

Please make sure this is correct before proceeding. (You can confirm by going to http://www.mozilla.org/)
If no version number shows, if the version shown is not the latest, or if you would like to install a different release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]? 
Please enter 'y' or 'n': y
Retrieving list of available localizations for Seamonkey ...
Please choose the localization (language) for Seamonkey. Enter the number of your choice from the list below. [If you do not see a list of localizations, please check the help section of our website at http://ubuntuzilla.sourceforge.net/ for steps you can take to resolve this problem.]
  0. be         Belarusian [&#1041;&#1077;&#1083;&#1072;&#1088;&#1091;&#1089;&#1082;&#1072;&#1103;]
  1. ca         Catalan [català]             
  2. cs         Czech [&#268;eština]             
  3. de         German [Deutsch]              
  4. en-US      English (US) [English (US)]   
  5. es-AR      Spanish (Argentina) [Español (de Argentina)]
  6. es-ES      Spanish (Spain) [Español (de España)]
  7. fr         French [Français]            
  8. gl         Galician [Galego]             
  9. hu         Hungarian [Magyar]            
 10. it         Italian [Italiano]            
 11. ka         Georgian [&#4325;&#4304;&#4320;&#4311;&#4323;&#4314;&#4312;]
 12. lt         Lithuanian [lietuvi&#371; kalba]  
 13. nb-NO      Norwegian (Bokmål) [Norsk bokmål]
 14. nl         Dutch [Nederlands]            
 15. pl         Polish [Polski]               
 16. pt-PT      Portuguese (Portugal) [Português (Europeu)]
 17. ru         Russian [&#1056;&#1091;&#1089;&#1089;&#1082;&#1080;&#1081;]      
 18. sk         Slovak [sloven&#269;ina]          
 19. sv-SE      Swedish [Svenska]             
 20. tr         Turkish [Türkçe]            

Enter your choice of localization (integer, from 0 to 20): 10
You have chosen localization it, Italian [Italiano]. Is that correct [y/n]? 
Please enter 'y' or 'n': y

Backing up old Seamonkey preferences

Retrieving package name for Seamonkey ...
Success!: seamonkey-2.0.1.tar.bz2

Downloading Seamonkey archive from the Mozilla site

--2009-12-16 10:55:04--  ftp://mozilla.isc.org/pub/mozilla.org/seamonkey/releases/2.0.1/linux-i686/it/seamonkey-2.0.1.tar.bz2
           => `seamonkey-2.0.1.tar.bz2'
Risoluzione di mozilla.isc.org... 204.152.184.113, 2001:4f8:0:2::1f
Connessione a mozilla.isc.org|204.152.184.113|:21... connesso.
Accesso come utente anonymous ... Login eseguito!
==> SYST ... fatto.    ==> PWD ... fatto.
==> TYPE I ... fatto.  ==> CWD /pub/mozilla.org/seamonkey/releases/2.0.1/linux-i686/it ... fatto.
==> SIZE seamonkey-2.0.1.tar.bz2 ... 13012668
==> PASV ... fatto.    ==> REST 13012668 ... fatto.    
==> RETR seamonkey-2.0.1.tar.bz2 ... fatto.
Lunghezza: 13012668 (12M), 0 (0) rimanenti

100%[+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++] 13.012.668  --.-K/s   in 0s      

2009-12-16 10:55:07 (0,00 B/s) - "seamonkey-2.0.1.tar.bz2" salvato [13012668]


Downloading Seamonkey MD5 sums from the Mozilla site

wget -c --tries=5 --read-timeout=20 --waitretry=10 -q -nv -O - ftp://mozilla.isc.org/pub/mozilla.org/seamonkey/releases/2.0.1/MD5SUMS | grep -F './linux-i686/it/seamonkey-2.0.1.tar.bz2' > seamonkey-2.0.1.tar.bz2.md5
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Error downloading. Trying again, hoping for a different mirror.
wget -c --tries=5 --read-timeout=20 --waitretry=10 -q -nv -O - ftp://mozilla.ussg.indiana.edu/pub/mozilla.org/seamonkey/releases/2.0.1/MD5SUMS | grep -F './linux-i686/it/seamonkey-2.0.1.tar.bz2' > seamonkey-2.0.1.tar.bz2.md5
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Error downloading. Trying again, hoping for a different mirror.
wget -c --tries=5 --read-timeout=20 --waitretry=10 -q -nv -O - ftp://ftp.osuosl.org/pub/mozilla.org/seamonkey/releases/2.0.1/MD5SUMS | grep -F './linux-i686/it/seamonkey-2.0.1.tar.bz2' > seamonkey-2.0.1.tar.bz2.md5
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Error downloading. Trying again, hoping for a different mirror.
wget -c --tries=5 --read-timeout=20 --waitretry=10 -q -nv -O - ftp://mozilla.cs.utah.edu/pub/mozilla.org/seamonkey/releases/2.0.1/MD5SUMS | grep -F './linux-i686/it/seamonkey-2.0.1.tar.bz2' > seamonkey-2.0.1.tar.bz2.md5
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Error downloading. Trying again, hoping for a different mirror.
wget -c --tries=5 --read-timeout=20 --waitretry=10 -q -nv -O - ftp://mozilla.mirrors.tds.net/pub/mozilla.org/seamonkey/releases/2.0.1/MD5SUMS | grep -F './linux-i686/it/seamonkey-2.0.1.tar.bz2' > seamonkey-2.0.1.tar.bz2.md5
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Error downloading. Trying again, hoping for a different mirror.

```

and then ubuntuzilla freezes :(

---

### Post by daniele80 on 2009-12-16
ok, i replaced

```
self.util.robustDownload(argsdict={'executionstring':"wget -c --tries=5 --read-timeout=20 --waitretry=10 -q -nv -O - ftp://" + "%mirror%" + self.options.package + "/releases/" + self.releaseVersion + "/MD5SUMS | grep -F './linux-i686/" + self.locList[self.locChoice] + "/" + self.packageFilename + "' > " + self.sigFilename, 'includewithtest':True}, errormsg="Failed to retrieve md5 sum. This may be due to transient network problems, so try again later. Exiting.")
```

with

```
self.util.robustDownload(argsdict={'executionstring':"wget -c --tries=5 --read-timeout=20 --waitretry=10 -q -nv -O - ftp://" + "%mirror%" + self.options.package + "/releases/" + self.releaseVersion + "/MD5SUMS | grep -F 'linux-i686/" + self.locList[self.locChoice] + "/" + self.packageFilename + "' | sed -r 's/linux-i686/.\/linux-i686/g' > " + self.sigFilename, 'includewithtest':True}, errormsg="Failed to retrieve md5 sum. This may be due to transient network problems, so try again later. Exiting.")
```

and now it works :D

---

### Post by nanotube on 2009-12-16
> **daniele80 said:**
> ok, i replaced

```
self.util.robustDownload(argsdict={'executionstring':"wget -c --tries=5 --read-timeout=20 --waitretry=10 -q -nv -O - ftp://" + "%mirror%" + self.options.package + "/releases/" + self.releaseVersion + "/MD5SUMS | grep -F './linux-i686/" + self.locList[self.locChoice] + "/" + self.packageFilename + "' > " + self.sigFilename, 'includewithtest':True}, errormsg="Failed to retrieve md5 sum. This may be due to transient network problems, so try again later. Exiting.")
```

with

```
self.util.robustDownload(argsdict={'executionstring':"wget -c --tries=5 --read-timeout=20 --waitretry=10 -q -nv -O - ftp://" + "%mirror%" + self.options.package + "/releases/" + self.releaseVersion + "/MD5SUMS | grep -F 'linux-i686/" + self.locList[self.locChoice] + "/" + self.packageFilename + "' | sed -r 's/linux-i686/.\/linux-i686/g' > " + self.sigFilename, 'includewithtest':True}, errormsg="Failed to retrieve md5 sum. This may be due to transient network problems, so try again later. Exiting.")
```

and now it works :D

Hi
Looks like they changed the format of the items in the MD5SUMS file with release 2.0.1

I'll adjust the code and make a fresh release.

Thanks a lot for pointing this out! :)

---

### Post by nanotube on 2009-12-16
pushed out ubuntuzilla 4.8.3 with the fix. give it a try :)

---

