---
title: "Mozilla Firefox 3.5.3 -- No Java.."
date: 2009-09-09
forum: Ubuntuzilla
---

### Post by ubuntu_n00b on 2009-09-09
Yes I'm new to Linux.. love Ubuntu though and this seems to be my only snag.. I can't get Firefox 3.5.3 to use Java.. I followed ALL instructions to a "T" from the Ubuntuzilla Instructions/FAQ page and can't for the life of me get this to work.. I have flash, and under about:plugins I only show Flash, no java.. What have I missed?? I'm using a fresh install of Ubuntu 9.04 x64.. Thanks!!!

---

### Post by Leunamal on 2009-09-10
> **ubuntu_n00b said:**
> Yes I'm new to Linux.. love Ubuntu though and this seems to be my only snag.. I can't get Firefox 3.5.3 to use Java.. I followed ALL instructions to a "T" from the Ubuntuzilla Instructions/FAQ page and can't for the life of me get this to work.. I have flash, and under about:plugins I only show Flash, no java.. What have I missed?? I'm using a fresh install of Ubuntu 9.04 x64.. Thanks!!!

Hi, I have the same problem. How can we solve this problem?

Thanks.

---

### Post by nanotube on 2009-09-10
did you guys install the ia32-sun-java6-plugin package, as suggested by the ubuntuzilla faq?

if so, and it still doesn't work, then try getting the 32bit sun-java6-plugin package.

go to [http://packages.ubuntu.com/jaunty/sun-java6-plugin](http://packages.ubuntu.com/jaunty/sun-java6-plugin)

then down there in the download section choose 'i386', download the .deb from one of the mirrors, install it - then restart firefox.

---

### Post by ubuntu_n00b on 2009-09-11
> **nanotube said:**
> did you guys install the ia32-sun-java6-plugin package, as suggested by the ubuntuzilla faq?

if so, and it still doesn't work, then try getting the 32bit sun-java6-plugin package.

go to [http://packages.ubuntu.com/jaunty/sun-java6-plugin](http://packages.ubuntu.com/jaunty/sun-java6-plugin)

then down there in the download section choose 'i386', download the .deb from one of the mirrors, install it - then restart firefox.

Doesn't work.. still no sign of Java in about : plugins.. I downloaded and tried to install the i386 but I got an error message about wrong architecture ...

---

### Post by nanotube on 2009-09-11
well then... i guess your best bet is to either use the 3.0 from the repos, or install from a firefox PPA:
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

---

### Post by ubuntu_n00b on 2009-09-11
Would it have anything to do with where firefox is directed? I mean for the plugin? Or should it just automatically install correctly?

---

### Post by nanotube on 2009-09-12
> **ubuntu_n00b said:**
> Would it have anything to do with where firefox is directed? I mean for the plugin? Or should it just automatically install correctly?

well, ubuntuzilla sets up the install to look for plugins in the same place that the default firefox does...

i don't have a 64bit machine, so i can't just go and play around with it and figure it out. i'm just stabbing in the dark here. :)

here's something else for you to try, to get java working:

```
sudo ln -s /usr/lib/jvm/ia32-java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so ~/.mozilla/plugins/
```

(but first make sure that the file /usr/lib/jvm/ia32-java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so exists (if it doesn't, look for it elsewhere, possibly in /usr/lib/jvm/ia32-java-6-sun-1.6.0.13/jre/plugin/i386/ns7/libjavaplugin_oji.so ), and that directory ~/.mozilla/plugins exists (create it if it doesn't)

give that a try, see what happens :) (this won't mess anything up, at worst it just won't work)

---

### Post by witeshark17 on 2009-10-15
Is there anything more on this issue? How about for 32 bit users? Maybe these instructions will help:

                                 Note: after installation, do **not** remove the repositories version of Firefox, as doing so will break a lot of Gnome packages that depend on the Gecko rendering engine.  
 Here are the steps to use this script to install the Mozilla build of Firefox, Thunderbird, or SeaMonkey:  
 
[LIST]
[*]Download .deb installer of the     latest release [(follow     this link to the file release servers)]("http://sourceforge.net/projects/ubuntuzilla/files/"), and save it to your     disk.
[LIST]
[*]Users of 64 bit Ubuntu, get the amd64 package (and see this         [note         for 64 bit users]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ#.5BThunderbird.2C_Firefox.5D_For_64-bit_Ubuntu_users")); users of 32 bit Ubuntu get the i386 package.         To determine which one you have, run command
[/LIST]
 
[/LIST]
 uname -m      64 bit users would see *x86_64*, 32 bit users would see *i686*.          
[LIST]
[*]     Completely exit Firefox or Thunderbird prior to installation (just     in case).
[*]Double-click on the .deb to start     the graphical package installer to install Ubuntuzilla. Once that is     complete, you are ready to use the script to install the Mozilla     software of your choice.
[LIST]
[*]If double-clicking doesn't start a package installer for you         (as might happen if you are using Kubuntu, e.g.), or if you just         like using the terminal, use the following commandline procedure to         install ubuntuzilla:
[/LIST]
 
[/LIST]
 sudo dpkg -i /path/to/ubuntuzilla*.deb sudo apt-get install -f 
[LIST]
[*]If you happen to have already     downloaded the appropriate Thunderbird, Firefox, or SeaMonkey tar.gz     archive to your drive, and want to avoid another download, place     your downloaded tar.gz into /tmp (without changing the original     filename). The script will still ask you questions about the     version, localizations, etc., but will not actually make another     download.
[*]Open a terminal
[/LIST]
 
[LIST]
[*]         Note: do **not** run ubuntuzilla with *sudo*.         That will mess up the ownership of some of the files in your home         directory (e.g., the stuff in *~/.gnupg*).          
     Enter one of the following
[*]commands to run the script (choose     one depending on which software you want to install; copy and paste     to avoid typos):
[/LIST]
 ubuntuzilla.py -a install -p firefox  ubuntuzilla.py -a install -p thunderbird  ubuntuzilla.py -a install -p seamonkey 
[LIST]
[*]Read the instructions and follow the prompts.
[/LIST]
 As an alternative to using the script, instructions for manually installing the official builds of Mozilla software are available on the Ubuntu wiki:  
 
[LIST]
[*][Manual     Install of Mozilla Firefox]("https://help.ubuntu.com/community/FirefoxNewVersion")
[*][Manual     Install of Mozilla Thunderbird]("https://help.ubuntu.com/community/ThunderbirdNewVersion")
[*][Manual     Install of Mozilla SeaMonkey]("https://help.ubuntu.com/community/SeaMonkey")
[/LIST]
 **Removal**

 Here are the steps to use this script to uninstall the Mozilla build of Firefox, Thunderbird, or SeaMonkey:  
 
[LIST]
[*]Completely exit Firefox or     Thunderbird prior to installation (just in case).
[*]Open a terminal
[*]Enter this command to run the script (choose one depending on     which software you want to remove; copy and paste to avoid typos):
[/LIST]
 ubuntuzilla.py -a remove -p firefox  ubuntuzilla.py -a remove -p thunderbird  ubuntuzilla.py -a remove -p seamonkey 
[LIST]
[*]Read the instructions and follow the prompts.
[/LIST]
 **Uninstall Ubuntuzilla**

 If you decide to uninstall Ubuntuzilla itself, you can use the usual procedure using your package manager of choice. For example, with apt-get, you can run command  
 sudo apt-get remove --purge ubuntuzilla To remove the automatic update checking job for Mozilla software, edit your user's crontab file and comment out or delete the relevant "ubuntuzilla" lines. To edit your crontab, enter command  
 crontab -e** Updates**

 Ubuntuzilla will let you install an automatic update checker job, which will periodically check for updates to your Mozilla software, and alert you with an unobtrusive notification. (See image at right for a sample. It shows up for a few seconds at the bottom right corner of your screen, when a new release becomes available.)  
 [[IMG]http://sourceforge.net/apps/mediawiki/ubuntuzilla/nfs/project/u/ub/ubuntuzilla/7/7b/Firefoxupdatenotification.png[/IMG]]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=File:Firefoxupdatenotification.png")
 [[COLOR=#000080][IMG]http://sourceforge.net/apps/mediawiki/ubuntuzilla/skins/common/images/magnify-clip.png[/IMG][/COLOR]]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=File:Firefoxupdatenotification.png")
 Ubuntuzilla update notification
 To install the automatic update checker, just run the installation, follow the prompts at the end of installation and choose 'yes' to enable automatic update checking. If you have already installed the Mozilla software at an earlier time, and just want to enable the automatic update checking, you can run Ubuntuzilla with action "installupdater" to install the updater job separately. Use the following command (choose one depending on which software you want to check for updates; copy and paste to avoid typos):  
 ubuntuzilla.py -a installupdater -p firefox  ubuntuzilla.py -a installupdater -p thunderbird  ubuntuzilla.py -a installupdater -p seamonkey If you have installed the update checking job, and now want to remove it, you can use the following commands (choose one depending on which software you want remove the update checking job for; copy and paste to avoid typos): ubuntuzilla.py -a removeupdater -p firefox  
 ubuntuzilla.py -a removeupdater -p thunderbird  ubuntuzilla.py -a removeupdater -p seamonkey You can also use Ubuntuzilla to do a one-time check for availability of new releases of Firefox, Thunderbird, and SeaMonkey. For text-mode update notification (message in the terminal or console), use the following command (choose one depending on which software you want to check for updates; copy and paste to avoid typos):  
 ubuntuzilla.py -a checkforupdatetext -p firefox  ubuntuzilla.py -a checkforupdatetext -p thunderbird  ubuntuzilla.py -a checkforupdatetext -p seamonkey For GUI update notification (message pop-up in the bottom right corner of your desktop), use the following command (choose one depending on which software you want to check for updates; copy and paste to avoid typos):  
 ubuntuzilla.py -a checkforupdategui -p firefox  ubuntuzilla.py -a checkforupdategui -p thunderbird  ubuntuzilla.py -a checkforupdategui -p seamonkey Read on in the next subsections for how to carry out the upgrade if a newer version is available.  
 **Update Official Mozilla Build of Firefox**

 If you already have the official build installed (e.g., by using the Ubuntuzilla script to install at some point before), you don't have to go through a reinstall in order to update (though you could if you wanted to). You can use the built-in "Updates" functionality of Firefox.  
 **Note: the "Update" functionality in Firefox won't upgrade you from FF2 to FF3, so if you want to do that, you'll have to do a fresh firefox install with Ubuntuzilla.**
      Note: do **not** use the plain *sudo* here.     That will mess up permissions inyour profile.      
 In order for Firefox to update itself, it 



will have to be run as root. So quit all Firefox windows, and in a terminal, type, if on GNOME:  
 gksudo firefox & If on KDE:  
 kdesu firefox & This will start Firefox as root. Select **Help** > **Check for Updates** from the menu, and it will find an update and download it. You will then get a message that says Firefox needs to be restarted to apply the update, and you can choose **Later** or **Restart Firefox Now**. Choose **Restart Firefox Now**. Firefox will restart again as root and tell you it's been updated. Now, you can close Firefox again, and then start it as normal from the menu, not as root. And you should be all good to go!  
 **Update Official Mozilla Build of Thunderbird**

 If you already have the official build installed (e.g., by using the Ubuntuzilla script to install at some point before), you don't have to go through a reinstall in order to update (though you could if you wanted to). You can use the built-in "Updates" functionality of Thunderbird.  
      Note: do **not** use the plain *sudo* here.     That will mess up permissions in your profile.      
 In order for Thunderbird to update itself, it will have to be run as root. So 



quit Thunderbird, and in a terminal, type, if on GNOME:  
 gksudo thunderbird & If on KDE:  
 kdesu thunderbird & This will start Thunderbird as root. Select **Help** > **Check for Updates** from the menu, and it will find an update and download it. You will then get a message that says Thunderbird needs to be restarted to apply the update, and you can choose **Later** or **Restart Thunderbird Now**. Choose **Restart Thunderbird Now**. Thunderbird will restart again as root and tell you it's been updated. Now, you can close Thunderbird again, and then start it as normal from the menu, not as root. And you should be all good to go!  
 **Update Official Mozilla Build of Seamonkey**

 Unlike Firefox and Thunderbird, SeaMonkey does not currently have a built-in updater. So to update to the latest version, just use the instructions from the [Installation]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation") section and install the newest version over the old one.  
 **Other options**

 You can get help on the aforementioned options, and more, by running the script with option '-h', as follows:  
 ubuntuzilla.py -h

---

### Post by kansasnoob on 2009-10-16
I just wanted to remind everyone that you must restart Firefox after each and every change to plug-ins:)

---

### Post by shane2peru on 2009-10-21
> **nanotube said:**
> well, ubuntuzilla sets up the install to look for plugins in the same place that the default firefox does...

i don't have a 64bit machine, so i can't just go and play around with it and figure it out. i'm just stabbing in the dark here. :)

here's something else for you to try, to get java working:

```
sudo ln -s /usr/lib/jvm/ia32-java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so ~/.mozilla/plugins/
```

(but first make sure that the file /usr/lib/jvm/ia32-java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so exists (if it doesn't, look for it elsewhere, possibly in /usr/lib/jvm/ia32-java-6-sun-1.6.0.13/jre/plugin/i386/ns7/libjavaplugin_oji.so ), and that directory ~/.mozilla/plugins exists (create it if it doesn't)

give that a try, see what happens :) (this won't mess anything up, at worst it just won't work)

This hit the nail on the head!  If you cannot find this file do the following.

1.  Find the File
```

sudo updatedb && locate libjavaplugin_oji.so

```

2.  That may spit out a few locations, you want to use the /usr or /opt or something not in your homedirectory.  Now lets cp that file to your plugins folder*

```

cp /[COLOR="Red"]location/found/above[/COLOR]/libjavaplugin_oji.so ~/.mozilla/plugins/

```

*note we copied the file because per chance that they find it in the home directory and delete it, will cause them problems later.  You can link it with "ln -s"  instead of the "cp" part above, if you are sure it is a permanent file.

This works on 64bit machines.

Shane


**PS**  Thanks nanotube and the others involved in the ubuntuzilla project.

---

### Post by heartbeat348 on 2009-10-26
I have 32 bit machine running 9.04 server manually installed firefox 3.5.3 and apt installed Sun JDK and JRE. Had the same problems as above.

**[FONT=Courier New]sudo ln -s /usr/lib/jvm/java-6-sun-1.6.016/jre/lib/i386/libnpjp2.so /usr/lib/firefox/plugins/libnpjp2.so[/FONT]**

worked for me

---

### Post by zleilndka on 2010-01-29
> **heartbeat348 said:**
> I have 32 bit machine running 9.04 server manually installed firefox 3.5.3 and apt installed Sun JDK and JRE. Had the same problems as above.

**[FONT=Courier New]sudo ln -s /usr/lib/jvm/java-6-sun-1.6.016/jre/lib/i386/libnpjp2.so /usr/lib/firefox/plugins/libnpjp2.so[/FONT]**

worked for me

Though this topic is fairly old, I have to say this is what worked for me.  Java was working with everything else with the exception of Firefox.

Putting the link to the "libjavaplugin_oji.so" file in the plugins folder--no go, but once I put a link to the "libnpjp2.so" file in the plugins folder, voila java showed up.

Thanks!

Ubuntu 9.10
Firefox 3.6 (newest version)
Java(TM) Plug-in 1.6.0_18 (newest version)

---

### Post by nanotube on 2010-01-29
indeed, libjavaplugin_oji.so uses an old plugin interface that no longer works with firefox3.6, so now we should use libnpjp2.so instead.

the updated instructions, using update-alternatives, are on the ubuntuzilla website, here:
[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Java_plugin_not_showing_up_.28on_Ubuntu_Karmic.29](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Java_plugin_not_showing_up_.28on_Ubuntu_Karmic.29)

---

