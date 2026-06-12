---
title: "Thunderbird 3.0  Available - Ubuntuzilla Reports Corrupt Package"
date: 2009-12-08
forum: The Cafe
---

### Post by NormanFLinux on 2009-12-08
Ubuntuzilla has notified about availability of Thunderbird 3.0 but it reports a corrupt package and aborts installation.

I guess its not really "available" yet! :lolflag:

---

### Post by sudoer541 on 2009-12-08
it might be a virus

---

### Post by andrewabc on 2009-12-08
3.0 officially released
[Mozilla Launches Thunderbird 3 ](http://www.mozillamessaging.com/en-US/about/press/archive/2009-12-08-01)

---

### Post by NormanFLinux on 2009-12-08
Installing from the Thunderbird 3.0 Bzip file takes a couple of steps and is more comfortable than using the command line interface:

1. Download the Thunderbird 3.0 file to the desktop
2. Use the zip utility to extract the contents to a folder on the desktop - name it thunderbird.
3. Look in the thunderbird folder and select all the files in it. Then copy them.
4. Launch terminal and go root in your file manager
5, Go to the thunderbird folder in usr/share. Paste in the files you copied and replace or overwrite the old files. When finished, close the thunderbird folder and the usr/share folder.
6. Choose the menu editor for in thunderbird 3.0 - the previous launch command will no longer work. Navigate to the thunderbird folder in usr/share thunderbird and chose usr/share/thunderbird/thunderbird as the new launch command. Save and close the menu editor.

Now the new Thunderbird 3.0 should launch when clicked.

Enjoy!

You can then delete the bzip package and the thunderbird folder that you copied the files from on the desktop.

---

### Post by AllRadioisDead on 2009-12-08
> **sudoer541 said:**
> it might be a virus
Yes, thunderbird 3.0 is a virus.:roll:

---

### Post by NormanFLinux on 2009-12-08
Really? I installed it the cumbersome way. It would be better if they made it available as a deb. or rpm package so people don't have to do all that copying and pasting to the original folder in usr/share! ](*,)

---

### Post by sudoer541 on 2009-12-08
any deb to download? I am not a scientist! I am just a regular person to do all that copying pasting commands etc!

---

### Post by DougieFresh4U on 2009-12-08
Why not add the 'mozilla ppa' and just update and open Synaptic and install Thunderbird 3?
You can also grab Firefox 3.6 and 3.7 there as well.

---

### Post by wilee-nilee on 2009-12-08
> **DougieFresh4U said:**
> Why not add the 'mozilla ppa' and just update and open Synaptic and install Thunderbird 3?
You can also grab Firefox 3.6 and 3.7 there as well.

This
[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

---

### Post by sudoer541 on 2009-12-08
> **DougieFresh4U said:**
> Why not add the 'mozilla ppa' and just update and open Synaptic and install Thunderbird 3?
You can also grab Firefox 3.6 and 3.7 there as well.

where is the mozilla PPA and how to install?

---

### Post by autonomy on 2009-12-08
thanks, NormanFLinux, that worked for me. I think an easier way would be to ```
sudo mv -f Desktop/thunderbird /usr/share/
```
and then paste my old profile into the new thunderbird home directory.

---

### Post by DougieFresh4U on 2009-12-08
> **sudoer541 said:**
> where is the mozilla PPA and how to install?
Here ya go, thanks **wilee-nilee**
[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

---

### Post by wilee-nilee on 2009-12-08
When I installed thunderbird 3 from that ppa it automatically loaded the IMAP set up and needed no transfer of email files. I did not remove the stock thunderbird 1st or yet though.

---

### Post by autonomy on 2009-12-08
BTW, if you're going to paste your old profile into the new .thunderbird folder, don't forget to paste the old profile.ini file, too and move the two new items (profile dir and .ini file) to the old directory. It's working good and looking good.

---

### Post by NormanFLinux on 2009-12-09
I've added the Mozilla Security repository. The Daily site just issues too many changes I don't like.

---

### Post by Dobbie03 on 2009-12-09
Thunderbird 3.0 is called Shredder for me, anyone else have this?

---

### Post by sillyxone on 2009-12-09
Yeah, the daily version is called Shredder. 

I have nothing to complain using the package from daily version, except for the font smoothing. TB2 and Firefox display sub-pixel smooth fonts like the rest of the system but TB3 from the daily package displays grayscale smoothing.

I installed the thunderbird-gnome-support package from the same source too, restarted, no difference in font rendering. Any suggestion? TB3 is more responsive and faster, the index/search is just awesome, and tabbed email is great. Just need the subpixel font smoothing, just that :-(

thanks,

---

### Post by motorcity909 on 2009-12-09
I've tried to update Thunderbird by running it as gksudo (as instructed on the [Ubuntuzilla wiki]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Update_Official_Mozilla_Build_of_Thunderbird")) but instead of opening my existing Thunderbird and allowing me to select Help>Check for Updates, it starts to reinstall TB and go through the import wizard.

I don't want to risk messing my profile up, so without messing about with copying files or installing other repositories, will TB 3.0 eventually come through the normal update manager?

If so, I'll stay with 2.0 for now.

Thanks.

---

### Post by longtom on 2009-12-09
What does 3 do better than 2?

---

### Post by sillyxone on 2009-12-09
> **longtom said:**
> What does 3 do better than 2?

[http://www.mozillamessaging.com/en-US/thunderbird/features/](http://www.mozillamessaging.com/en-US/thunderbird/features/)

basically I found it faster and more responsive. It also indexes the mailboxes, and thus the search feature is awesome. Tabbed email is also a plus.

When I install it from the Mozilla Daily PPA, it just recognized my  existing encrypted .thunderbird folder and created a link .thunderbird-3.0 to it, nothing else changed, all the account settings, mailboxes, message filters are still there, no extra works required.

But I'm still searching for the font smoothing, perhaps recompiling with certain flags on will do.

---

### Post by Fast_Wyvern on 2009-12-09
sillyxone, not sure if this is what you are looking for

in Thunderbird select Help, about:config. Type smooth in the search bar

you should see gfx.use_text_smoothing_setting set as disabled by default, double click to enable, is this what you are after?

---

### Post by longtom on 2009-12-09
> **sillyxone said:**
> [http://www.mozillamessaging.com/en-US/thunderbird/features/](http://www.mozillamessaging.com/en-US/thunderbird/features/)

basically I found it faster and more responsive. It also indexes the mailboxes, and thus the search feature is awesome. Tabbed email is also a plus.

When I install it from the Mozilla Daily PPA, it just recognized my  existing encrypted .thunderbird folder and created a link .thunderbird-3.0 to it, nothing else changed, all the account settings, mailboxes, message filters are still there, no extra works required.

But I'm still searching for the font smoothing, perhaps recompiling with certain flags on will do.

Thanks for the link - appreciated.

---

### Post by motorcity909 on 2009-12-09
Just tried the method as set out in post #4, but no luck.  Thunderbird 3 did open so I then copied my existing profile from the original .mozilla thunderbird folder into the new .thunderbird folder, deleting the newly created profile from within it.  I also deleted the .mozilla thunderbird folder.

I created a new desktop launcher to TB3 but when clicked it told me TB was already running.  Even after a restart it was the same so I've restored my original usr/share folder and my profile in .mozilla thunderbird and am still using TB2.

If I add the additional repository and install TB3 will my existing profile be safe or will I have to copy it's files anywhere?

Thanks as always.

---

### Post by sillyxone on 2009-12-09
> **Fast_Wyvern said:**
> sillyxone, not sure if this is what you are looking for

in Thunderbird select Help, about:config. Type smooth in the search bar

you should see gfx.use_text_smoothing_setting set as disabled by default, double click to enable, is this what you are after?

nah, that settings is only applied to OSX. OSX has a option where font smaller certain size won't be smoothed, and that setting tells Thunderbird whether to follow the same rule defined in OSX.


I always get no font smoothing using direct tarballs from Mozilla, whether it's Firefox or Thunderbird, it's just not integrated into Gnome. The package from Daily Mozilla at least has grayscale smoothing, but my eyes are used to subpixel smoothing already.

thanks

---

### Post by sillyxone on 2009-12-09
> **motorcity909 said:**
> Just tried the method as set out in post #4, but no luck.  Thunderbird 3 did open so I then copied my existing profile from the original .mozilla thunderbird folder into the new .thunderbird folder, deleting the newly created profile from within it.  I also deleted the .mozilla thunderbird folder.

I created a new desktop launcher to TB3 but when clicked it told me TB was already running.  Even after a restart it was the same so I've restored my original usr/share folder and my profile in .mozilla thunderbird and am still using TB2.

If I add the additional repository and install TB3 will my existing profile be safe or will I have to copy it's files anywhere?

Thanks as always.


Actually I didn't add the repo to Synaptic. I was afraid that it will upgrade my Firefox and will nag me for update every day. Instead, I downloaded the deb packages to the Desktop and double-click on them.

You can go directly here:

[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa/+packages]("https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa/+packages")

select thunderbird-3.0 - 3.0.1~hg20091208r4496+nobinonly-0ubuntu1~umd1~<hardy|intrepid|jaunty|karmic> depending on your Ubuntu version. Then under the selected section, select the right package for you hardware architecture (amd64, i386), pick the one without dev or dbg.

I'm not sure exactly what the thunderbird-gnome-support does, I installed but it doesn't solve the font smoothing problem so I've remove it (my TB2 doesn't have that package installed)

Once installed, you can run "thunderbird-3.0" from the terminal. I also edit the shortcut on my panel from "thunderbird" to "thunderbird-3.0"

---

### Post by nanotube on 2009-12-09
> **NormanFLinux said:**
> Ubuntuzilla has notified about availability of Thunderbird 3.0 but it reports a corrupt package and aborts installation.

I guess its not really "available" yet! :lolflag:

Hi
They're using a new gpg key to sign the packages, which Ubuntuzilla wasn't aware of. Try the latest release ubuntuzilla (4.8.2) which solves this problem.

---

### Post by nanotube on 2009-12-09
> **motorcity909 said:**
> I've tried to update Thunderbird by running it as gksudo (as instructed on the [Ubuntuzilla wiki]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Update_Official_Mozilla_Build_of_Thunderbird")) but instead of opening my existing Thunderbird and allowing me to select Help>Check for Updates, it starts to reinstall TB and go through the import wizard.

I don't want to risk messing my profile up, so without messing about with copying files or installing other repositories, will TB 3.0 eventually come through the normal update manager?

If so, I'll stay with 2.0 for now.

Thanks.

Hi

Just cancel out of that import wizard stuff, then do check for updates.

when you run it with gksudo, it opens it in root's environment - don't worry, your profile won't get messed up.

alternatively, you could just run the ubuntuzilla install process again, to install tb3 fresh.

---

### Post by Excedio on 2009-12-09
I love the new look of it, much smoother than 2.0. I am still working on editing the left sidebar to my liking, but having trouble trying to reorganize the folders. LOVED how simply it connected to my gmail.
 
However, I'm a little it dissappointed at how many of my add-ons are not compatible with 3.0. This is obviously not Mozilla's fault, just need to be patient and wait for the add-on devs to upgrade their scripting. The one's I miss the most are:
 
Lightning (Definate MUST have)
Birthday Reminder
Contacts Sidebar
 
EDIT:
Just found this: [http://ftp.mozilla.org/pub/mozilla.org/calendar/lightning/nightly/latest-comm-1.9.1/linux-xpi/](http://ftp.mozilla.org/pub/mozilla.org/calendar/lightning/nightly/latest-comm-1.9.1/linux-xpi/)
 
Learned about it [here]("https://addons.mozilla.org/en-US/thunderbird/addon/2313"). I'll be testing it when I get home :-)

---

### Post by sudoer541 on 2009-12-09
> **sillyxone said:**
> Actually I didn't add the repo to Synaptic. I was afraid that it will upgrade my Firefox and will nag me for update every day. Instead, I downloaded the deb packages to the Desktop and double-click on them.

You can go directly here:

[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa/+packages]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+packages")

select thunderbird-3.0 - 3.0.1~hg20091208r4496+nobinonly-0ubuntu1~umd1~<hardy|intrepid|jaunty|karmic> depending on your Ubuntu version. Then under the selected section, select the right package for you hardware architecture (amd64, i386), pick the one without dev or dbg.

I'm not sure exactly what the thunderbird-gnome-support does, I installed but it doesn't solve the font smoothing problem so I've remove it (my TB2 doesn't have that package installed)

Once installed, you can run "thunderbird-3.0" from the terminal. I also edit the shortcut on my panel from "thunderbird" to "thunderbird-3.0"

Hey thanks! it worked perfectly. That was easy! :p:P:D

---

### Post by sojusnik on 2009-12-09
Thanks for Ubuntuzilla!

Gnome's font rendering is not applied to Thunderbird, when installed through Ubuntuzilla.

How can be this problem solved under Ubuntu 9.10?

---

### Post by NormanFLinux on 2009-12-09
I installed the updated Ubuntuzilla. That should take care of the new gpg key signing issue in updating Firefox/Thunderbird.

---

### Post by FuturePilot on 2009-12-09
> **sillyxone said:**
> Yeah, the daily version is called Shredder. 

I have nothing to complain using the package from daily version, except for the font smoothing. TB2 and Firefox display sub-pixel smooth fonts like the rest of the system but TB3 from the daily package displays grayscale smoothing.

I installed the thunderbird-gnome-support package from the same source too, restarted, no difference in font rendering. Any suggestion? TB3 is more responsive and faster, the index/search is just awesome, and tabbed email is great. Just need the subpixel font smoothing, just that :-(

thanks,

Yeah, I've got the same problem on Jaunty. The fonts look horrible. On Karmic though they look sub-pixel rendered. Not sure what's up with Jaunty.

---

### Post by nanotube on 2009-12-09
> **sojusnik said:**
> Thanks for Ubuntuzilla!

Gnome's font rendering is not applied to Thunderbird, when installed through Ubuntuzilla.

How can be this problem solved under Ubuntu 9.10?

ff3.5 has also been reported to have some font rendering problems. try following the suggestion in this thread, and see if that helps:
[http://ubuntuforums.org/showthread.php?t=1200992](http://ubuntuforums.org/showthread.php?t=1200992)

---

### Post by speedwell68 on 2009-12-09
I tried the PPA version of TB 3.0, Shredder, and the vast majority of my extensions aren't yet compatible with TB 3.0, so I think I'll stick with TB 2.0.xx for the time being.

---

### Post by rogerdean on 2009-12-09
Hi folks
For the sake of easy admin of several machines I'd love to get hold of TB3 either in a .deb or a PPA (but not the nightlies PPA - I don't want constant updates and I would like non-shredder branding)
Does anyone know if these are to be found yet?
Cheers!
R

---

### Post by speedwell68 on 2009-12-09
> **rogerdean said:**
> Hi folks
For the sake of easy admin of several machines I'd love to get hold of TB3 either in a .deb or a PPA (but not the nightlies PPA - I don't want constant updates and I would like non-shredder branding)
Does anyone know if these are to be found yet?
Cheers!
R

You could use the Ubuntuzilla repository...

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Repository_method](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Repository_method)

That is what I will be doing once my addon issues have been resolved.

---

### Post by Excedio on 2009-12-09
Two things:

[LIST=1]
[*]How come when I used the PPA, my Thunderbird is called Shredder?
[*]Can someone PLEEEAAAASE provide me the Thunderbird start page? Mine is saying cannot be found. Google searches are not providing me the 3.0 start page. Located at Edit > Preferences > General > Location
[/LIST]

---

### Post by FuturePilot on 2009-12-09
> **Excedio said:**
> 
[LIST=1]
[*]How come when I used the PPA, my Thunderbird is called Shredder?

[/LIST]

Because it's Ubuntu's policy to only use the official branding on the version that ships with Ubuntu. Shredder is the codename for the Thunderbird 3 release.

Don't know on the second question but it's also missing for me.

---

### Post by sillyxone on 2009-12-09
> **nanotube said:**
> ff3.5 has also been reported to have some font rendering problems. try following the suggestion in this thread, and see if that helps:
[http://ubuntuforums.org/showthread.php?t=1200992](http://ubuntuforums.org/showthread.php?t=1200992)

thanks for the link, that .fonts.conf file does affect both Thunderbird and Firefox, but in different ways:

- all options applied to Thunderbird and Firefox, except "hintstyle"
- "hintstyle" doesn't applied to Firefox, FF either has beautiful smoothing or none depending on "hinting" and "antialias" options

It looks like the same problem I have with Netbean vs Eclipse: Eclipse uses Gnome font smoothing while Netbean has its own font rendering engine (which is not as good and very similar to my TB3 now)

I guess I will wait for the official Ubuntu TB3 to arrive then.

---

### Post by teet on 2009-12-09
Has anybody gotten the google calendar provider extension to work with thunderbird 3?

I was able to get lightning installed by using the latest nightly build (of lightning), but it won't let me install the latest nightly build of the provider extension.

-teet

---

### Post by nanotube on 2009-12-09
> **sillyxone said:**
> thanks for the link, that .fonts.conf file does affect both Thunderbird and Firefox, but in different ways:

- all options applied to Thunderbird and Firefox, except "hintstyle"
- "hintstyle" doesn't applied to Firefox, FF either has beautiful smoothing or none depending on "hinting" and "antialias" options

It looks like the same problem I have with Netbean vs Eclipse: Eclipse uses Gnome font smoothing while Netbean has its own font rendering engine (which is not as good and very similar to my TB3 now)

Hmm... you could also try some tips from this launchpad bug thread:
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/379761](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/379761)

> 
I guess I will wait for the official Ubuntu TB3 to arrive then.
Just FYI, that's not going to happen until the next ubuntu release (Lucid) comes out, in about a half a year.

---

### Post by rogerdean on 2009-12-10
Thanks Speedwell - I tried ubuntuzilla last night. It offered me TB3 and then downloaded and installed TB2. Took me a while to straighten that out...

Any other options out there?

---

### Post by sojusnik on 2009-12-10
@nanotube

The font rendering in Firefox 3.5 under 9.10 works like a charm out of the box for me. Strangley, the Thunderbird 3 doesn't, only when it's installed via the mozilla nightly ppa.

Tried the advices in your posted links, but all affect only Firefox not Thunderbird...

---

### Post by nanotube on 2009-12-10
> **rogerdean said:**
> Thanks Speedwell - I tried ubuntuzilla last night. It offered me TB3 and then downloaded and installed TB2. Took me a while to straighten that out...


err... that strikes me as impossible. are you sure you completely quit and restarted thunderbird? maybe your menu shortcuts point specifically to tb2? 

could you post the complete output of the ubuntuzilla install process so i could take a look?

---

### Post by rogerdean on 2009-12-10
Heh, well, that's what happened. I had Shredder installed before, not TB2, and ended up with TB2...
I'm afraid I've long since lost any logs, was trying to clean it all up, sorry

Edit -
ah, except in my bash history file, these are the commands I ran -
```
sudo apt-get update
sudo apt-get install ubuntuzilla
ubuntuzilla.py -a install -p thunderbird
sudo aptitude remove ubuntuzilla
```

but that doesn't tell you much, except that i did it right (or not?)
Cheers

---

### Post by Excedio on 2009-12-10
> **sillyxone said:**
> Actually I didn't add the repo to Synaptic. I was afraid that it will upgrade my Firefox and will nag me for update every day. Instead, I downloaded the deb packages to the Desktop and double-click on them.
 
You can go directly here:
 
[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa/+packages](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa/+packages)
 
select thunderbird-3.0 - 3.0.1~hg20091208r4496+nobinonly-0ubuntu1~umd1~<hardy|intrepid|jaunty|karmic> depending on your Ubuntu version. Then under the selected section, select the right package for you hardware architecture (amd64, i386), pick the one without dev or dbg.
 
I'm not sure exactly what the thunderbird-gnome-support does, I installed but it doesn't solve the font smoothing problem so I've remove it (my TB2 doesn't have that package installed)
 
Once installed, you can run "thunderbird-3.0" from the terminal. I also edit the shortcut on my panel from "thunderbird" to "thunderbird-3.0"
 
I tried this method, but everytime I tried to start Thunderbird it would say that it was already running even though it was not listed in Gnome System Monitor. I even rebooted, still didn't work.
 
Ended up going with using the PPA. Works great now...except that the Start Page cannot be found. If anyone has a functioning start page for their Thunderbird, could you let me know what the URL is?

---

### Post by rogerdean on 2009-12-10
mine is -

[http://live.mozillamessaging.com/thunderbird/start?locale=en-GB&version=3.0&os=Linux&buildid=20091204170421](http://live.mozillamessaging.com/thunderbird/start?locale=en-GB&version=3.0&os=Linux&buildid=20091204170421)

---

### Post by Excedio on 2009-12-10
> **rogerdean said:**
> mine is -
 
[http://live.mozillamessaging.com/thunderbird/start?locale=en-GB&version=3.0&os=Linux&buildid=20091204170421](http://live.mozillamessaging.com/thunderbird/start?locale=en-GB&version=3.0&os=Linux&buildid=20091204170421)
 
 
Woohoo! Thanks a lot dude! Not my Thunderbird is completely perfect. :-D

---

### Post by nanotube on 2009-12-10
> **rogerdean said:**
> Heh, well, that's what happened. I had Shredder installed before, not TB2, and ended up with TB2...
I'm afraid I've long since lost any logs, was trying to clean it all up, sorry

Edit -
ah, except in my bash history file, these are the commands I ran -
```
sudo apt-get update
sudo apt-get install ubuntuzilla
ubuntuzilla.py -a install -p thunderbird
sudo aptitude remove ubuntuzilla
```

but that doesn't tell you much, except that i did it right (or not?)
Cheers

Hi
indeed doesn't tell me much, but you did use the correct install command...

the fact that you had shredder installed might have modified your launcher links, so that they weren't pointed at the usual /usr/bin/thunderbird, and maybe that's why it didn't launch tb3... 

you could just try ubuntuzilla install again, then quit your tb, and from a terminal run 'thunderbird', which should start tb3. 

you can always easily undo the install by running ubuntuzilla -a remove -p thunderbird.

---

### Post by rogerdean on 2009-12-10
hi nanotube

ok, i see in your sig that ubuntuzilla is your thing, so i'm doing it again...

...and it's installed TB2 again. could this be because I'm requesting the UK english build, and perhaps this doesn't exist yet? just an idea

now rebuilding my email again :) happy to help though...

```
roger@roger-laptop:~$ echo "deb http://switch.dl.sourceforge.net/project/ubuntuzilla/apt all main" | sudo tee -a /etc/apt/sources.list > /dev/null
[sudo] password for roger: 
roger@roger-laptop:~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
[sudo] password for roger: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com C1289A29
gpg: requesting key C1289A29 from hkp server keyserver.ubuntu.com
gpg: key C1289A29: "Daniel Folkinshteyn (Ubuntuzilla signing key) <nanotube@users.sourceforge.net>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
roger@roger-laptop:~$ sudo apt-get update
Hit http://security.ubuntu.com karmic-security Release.gpg                     
Ign http://security.ubuntu.com karmic-security/main Translation-en_GB          
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_GB    
Hit http://archive.canonical.com karmic Release.gpg                            
Ign http://archive.canonical.com karmic/partner Translation-en_GB              
Ign http://security.ubuntu.com karmic-security/universe Translation-en_GB      
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_GB    
Hit http://security.ubuntu.com karmic-security Release                         
Hit http://gb.archive.ubuntu.com karmic Release.gpg                            
Get: 1 http://gb.archive.ubuntu.com karmic/main Translation-en_GB [63.7kB]     
Get: 2 http://dl.google.com testing Release.gpg [189B]                         
Ign http://dl.google.com testing/non-free Translation-en_GB                    
Hit http://archive.canonical.com karmic Release                                
Get: 3 http://packages.linuxmint.com helena Release.gpg [198B]                 
Get: 4 http://dl.google.com stable Release.gpg [189B]                          
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_GB                     
Get: 5 http://switch.dl.sourceforge.net all Release.gpg [197B]                 
Hit http://security.ubuntu.com karmic-security/main Packages                   
Hit http://download.virtualbox.org karmic Release.gpg                          
Ign http://download.virtualbox.org karmic/non-free Translation-en_GB           
Ign http://linux.getdropbox.com karmic Release.gpg                             
Ign http://linux.getdropbox.com karmic/main Translation-en_GB                  
Ign http://dl.google.com stable/non-free Translation-en_GB                     
Ign http://dl.google.com stable/main Translation-en_GB                         
Ign http://packages.linuxmint.com helena/main Translation-en_GB                
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_GB                     
Hit http://ppa.launchpad.net karmic Release                                    
Hit http://archive.canonical.com karmic/partner Packages                       
Hit http://security.ubuntu.com karmic-security/restricted Packages             
Hit http://security.ubuntu.com karmic-security/main Sources                    
Hit http://security.ubuntu.com karmic-security/restricted Sources              
Hit http://security.ubuntu.com karmic-security/universe Packages               
Hit http://security.ubuntu.com karmic-security/universe Sources                
Hit http://security.ubuntu.com karmic-security/multiverse Packages             
Hit http://security.ubuntu.com karmic-security/multiverse Sources              
Get: 6 http://gb.archive.ubuntu.com karmic/restricted Translation-en_GB [3,402B]
Get: 7 http://gb.archive.ubuntu.com karmic/universe Translation-en_GB [33.2kB] 
Get: 8 http://gb.archive.ubuntu.com karmic/multiverse Translation-en_GB [43.8kB]
Get: 9 http://dl.google.com testing Release [2,513B]                           
Hit http://download.virtualbox.org karmic Release                              
Ign http://linux.getdropbox.com karmic Release                                 
Get: 10 http://gb.archive.ubuntu.com karmic-updates Release.gpg [189B]         
Ign http://gb.archive.ubuntu.com karmic-updates/main Translation-en_GB         
Ign http://gb.archive.ubuntu.com karmic-updates/restricted Translation-en_GB   
Ign http://gb.archive.ubuntu.com karmic-updates/universe Translation-en_GB     
Ign http://gb.archive.ubuntu.com karmic-updates/multiverse Translation-en_GB   
Get: 11 http://packages.linuxmint.com helena Release [7,251B]                  
Hit http://ppa.launchpad.net karmic Release                                    
Get: 12 http://dl.google.com stable Release [2,540B]                           
Hit http://gb.archive.ubuntu.com karmic Release                                
Ign http://linux.getdropbox.com karmic/main Packages                           
Hit http://download.virtualbox.org karmic/non-free Packages                    
Ign http://packages.linuxmint.com helena Release                               
Get: 13 http://dl.google.com testing/non-free Packages [793B]                  
Hit http://ppa.launchpad.net karmic/main Packages                              
Get: 14 http://gb.archive.ubuntu.com karmic-updates Release [44.1kB]           
Ign http://linux.getdropbox.com karmic/main Packages                           
Ign http://packages.linuxmint.com helena/main Packages                         
Get: 15 http://dl.google.com stable/non-free Packages [1,010B]                 
Get: 16 http://dl.google.com stable/main Packages [850B]                       
Hit http://ppa.launchpad.net karmic/main Packages                              
Hit http://gb.archive.ubuntu.com karmic/main Packages                          
Hit http://gb.archive.ubuntu.com karmic/restricted Packages                    
Hit http://gb.archive.ubuntu.com karmic/main Sources                           
Hit http://gb.archive.ubuntu.com karmic/restricted Sources                     
Hit http://gb.archive.ubuntu.com karmic/universe Packages                      
Hit http://gb.archive.ubuntu.com karmic/universe Sources                       
Hit http://gb.archive.ubuntu.com karmic/multiverse Packages                    
Hit http://gb.archive.ubuntu.com karmic/multiverse Sources                     
Ign http://switch.dl.sourceforge.net all/main Translation-en_GB                
Hit http://linux.getdropbox.com karmic/main Packages                           
Ign http://packages.linuxmint.com helena/main Packages                         
Hit http://packages.medibuntu.org karmic Release.gpg                           
Ign http://packages.medibuntu.org karmic/free Translation-en_GB                
Ign http://packages.medibuntu.org karmic/non-free Translation-en_GB            
Get: 17 http://gb.archive.ubuntu.com karmic-updates/main Packages [109kB]      
Get: 18 http://gb.archive.ubuntu.com karmic-updates/restricted Packages [14B]  
Get: 19 http://gb.archive.ubuntu.com karmic-updates/main Sources [33.2kB]      
Get: 20 http://gb.archive.ubuntu.com karmic-updates/restricted Sources [14B]   
Get: 21 http://gb.archive.ubuntu.com karmic-updates/universe Packages [64.0kB] 
Get: 22 http://gb.archive.ubuntu.com karmic-updates/universe Sources [15.0kB]  
Get: 23 http://packages.linuxmint.com helena/main Packages [4,767B]            
Hit http://packages.medibuntu.org karmic Release                               
Get: 24 http://gb.archive.ubuntu.com karmic-updates/multiverse Packages [3,041B]
Get: 25 http://gb.archive.ubuntu.com karmic-updates/multiverse Sources [1,744B]
Get: 26 http://switch.dl.sourceforge.net all Release [1,632B]                  
Hit http://packages.medibuntu.org karmic/free Packages                         
Hit http://packages.medibuntu.org karmic/non-free Packages                     
Ign http://switch.dl.sourceforge.net all/main Packages                         
Ign http://switch.dl.sourceforge.net all/main Packages                         
Get: 27 http://switch.dl.sourceforge.net all/main Packages [595B]              
Fetched 437kB in 21s (20.5kB/s)                              
Reading package lists... Done
W: GPG error: http://packages.linuxmint.com helena Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3EE67F3D0FF405B2
roger@roger-laptop:~$ sudo apt-get install ubuntuzilla
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntuzilla is already the newest version.
The following packages were automatically installed and are no longer required:
  libnspr4-dev winbind
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
roger@roger-laptop:~$ ubuntuzilla.py -a install -p thunderbird

Welcome to the Ubuntuzilla Thunderbird script version 4.8.2

Ubuntuzilla is built only for Ubuntu Linux and other distributions derived from Ubuntu (such as Linux Mint, e.g.)

This script will now install the latest release of the official Mozilla build of Thunderbird on your Linux system. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at http://ubuntuzilla.sourceforge.net/ 

Retrieving the version of the latest release of Thunderbird from the Mozilla website...
The most recent release of Thunderbird is detected to be 3.0.

Please make sure this is correct before proceeding. (You can confirm by going to http://www.mozilla.org/)
If no version number shows, if the version shown is not the latest, or if you would like to install a different release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]? 
Please enter 'y' or 'n': y
Retrieving list of available localizations for Thunderbird ...
Please choose the localization (language) for Thunderbird. Enter the number of your choice from the list below. [If you do not see a list of localizations, please check the help section of our website at http://ubuntuzilla.sourceforge.net/ for steps you can take to resolve this problem.]
  0. af         Afrikaans [Afrikaans]         
  1. ar         Arabic [&#1593;&#1585;&#1576;&#1610;]             
  2. be         Belarusian [&#1041;&#1077;&#1083;&#1072;&#1088;&#1091;&#1089;&#1082;&#1072;&#1103;]
  3. bg         Bulgarian [&#1041;&#1098;&#1083;&#1075;&#1072;&#1088;&#1089;&#1082;&#1080;]
  4. bn-BD      Bengali (Bangladesh) [&#2476;&#2494;&#2434;&#2482;&#2494; (&#2476;&#2494;&#2434;&#2482;&#2494;&#2470;&#2503;&#2486;)]
  5. ca         Catalan [català]             
  6. cs         Czech [&#268;eština]             
  7. de         German [Deutsch]              
  8. el         Greek [&#917;&#955;&#955;&#951;&#957;&#953;&#954;&#940;]      
  9. en-GB      English (British) [English (British)]
 10. en-US      English (US) [English (US)]   
 11. es-AR      Spanish (Argentina) [Español (de Argentina)]
 12. es-ES      Spanish (Spain) [Español (de España)]
 13. et         Estonian [Eesti keel]         
 14. eu         Basque [Euskara]              
 15. fi         Finnish [suomi]               
 16. fr         French [Français]            
 17. fy-NL      Frisian [Frysk]               
 18. ga-IE      Irish [Gaeilge]               
 19. gl         Galician [Galego]             
 20. he         Hebrew [&#1506;&#1489;&#1512;&#1497;&#1514;]           
 21. hu         Hungarian [Magyar]            
 22. id         Indonesian [Bahasa Indonesia] 
 23. is         Icelandic [íslenska]         
 24. it         Italian [Italiano]            
 25. ja         Japanese [&#26085;&#26412;&#35486;]          
 26. ka         Georgian [&#4325;&#4304;&#4320;&#4311;&#4323;&#4314;&#4312;]
 27. ko         Korean [&#54620;&#44397;&#50612;]            
 28. lt         Lithuanian [lietuvi&#371; kalba]  
 29. nb-NO      Norwegian (Bokmål) [Norsk bokmål]
 30. nl         Dutch [Nederlands]            
 31. nn-NO      Norwegian (Nynorsk) [Norsk nynorsk]
 32. pa-IN      Punjabi [&#2602;&#2672;&#2588;&#2622;&#2604;&#2624;]  
 33. pl         Polish [Polski]               
 34. pt-BR      Portuguese (Brazilian) [Português (do Brasil)]
 35. pt-PT      Portuguese (Portugal) [Português (Europeu)]
 36. ro         Romanian [român&#259;]           
 37. ru         Russian [&#1056;&#1091;&#1089;&#1089;&#1082;&#1080;&#1081;]      
 38. si         Sinhala [&#3523;&#3538;&#3458;&#3524;&#3517;]     
 39. sk         Slovak [sloven&#269;ina]          
 40. sq         Albanian [Shqip]              
 41. sr         Serbian [&#1057;&#1088;&#1087;&#1089;&#1082;&#1080;]        
 42. sv-SE      Swedish [Svenska]             
 43. ta-LK      Tamil (Sri Lanka) [&#2980;&#2990;&#3007;&#2996;&#3021; (&#2951;&#2994;&#2969;&#3021;&#2965;&#3016;)]
 44. tr         Turkish [Türkçe]            
 45. uk         Ukrainian [&#1059;&#1082;&#1088;&#1072;&#1111;&#1085;&#1089;&#1100;&#1082;&#1072;]
 46. vi         Vietnamese [Ti&#7871;ng Vi&#7879;t]   
 47. zh-CN      Chinese (Simplified) [&#20013;&#25991; (&#31616;&#20307;)]
 48. zh-TW      Chinese (Traditional) [&#27491;&#39636;&#20013;&#25991; (&#32321;&#39636;)]

Enter your choice of localization (integer, from 0 to 48): 9
You have chosen localization en-GB, English (British) [English (British)]. Is that correct [y/n]? 
Please enter 'y' or 'n': y

Updating repositories information with apt-get update. You may be prompted for your password.

Hit http://security.ubuntu.com karmic-security Release.gpg                     
Ign http://security.ubuntu.com karmic-security/main Translation-en_GB          
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_GB    
Hit http://gb.archive.ubuntu.com karmic Release.gpg                            
Hit http://gb.archive.ubuntu.com karmic/main Translation-en_GB                 
Hit http://gb.archive.ubuntu.com karmic/restricted Translation-en_GB           
Hit http://archive.canonical.com karmic Release.gpg                            
Ign http://archive.canonical.com karmic/partner Translation-en_GB              
Get: 1 http://packages.linuxmint.com helena Release.gpg [198B]                 
Ign http://security.ubuntu.com karmic-security/universe Translation-en_GB      
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_GB    
Hit http://security.ubuntu.com karmic-security Release                         
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_GB                     
Hit http://ppa.launchpad.net karmic Release.gpg                                
Hit http://gb.archive.ubuntu.com karmic/universe Translation-en_GB             
Hit http://gb.archive.ubuntu.com karmic/multiverse Translation-en_GB           
Hit http://gb.archive.ubuntu.com karmic-updates Release.gpg                    
Ign http://gb.archive.ubuntu.com karmic-updates/main Translation-en_GB         
Ign http://gb.archive.ubuntu.com karmic-updates/restricted Translation-en_GB   
Ign http://gb.archive.ubuntu.com karmic-updates/universe Translation-en_GB     
Ign http://gb.archive.ubuntu.com karmic-updates/multiverse Translation-en_GB   
Hit http://packages.medibuntu.org karmic Release.gpg                           
Ign http://packages.medibuntu.org karmic/free Translation-en_GB                
Ign http://packages.medibuntu.org karmic/non-free Translation-en_GB            
Hit http://switch.dl.sourceforge.net all Release.gpg                           
Hit http://gb.archive.ubuntu.com karmic Release                                
Ign http://linux.getdropbox.com karmic Release.gpg                             
Ign http://linux.getdropbox.com karmic/main Translation-en_GB                  
Ign http://packages.linuxmint.com helena/main Translation-en_GB                
Hit http://archive.canonical.com karmic Release                                
Get: 2 http://dl.google.com testing Release.gpg [189B]                         
Ign http://dl.google.com testing/non-free Translation-en_GB                    
Get: 3 http://dl.google.com stable Release.gpg [189B]                          
Ign http://ppa.launchpad.net karmic/main Translation-en_GB                     
Hit http://security.ubuntu.com karmic-security/main Packages                   
Hit http://ppa.launchpad.net karmic Release                                    
Hit http://gb.archive.ubuntu.com karmic-updates Release                        
Hit http://packages.medibuntu.org karmic Release                               
Ign http://dl.google.com stable/non-free Translation-en_GB                     
Ign http://dl.google.com stable/main Translation-en_GB                         
Hit http://download.virtualbox.org karmic Release.gpg                          
Ign http://download.virtualbox.org karmic/non-free Translation-en_GB           
Ign http://linux.getdropbox.com karmic Release                                 
Get: 4 http://packages.linuxmint.com helena Release [7,251B]                   
Hit http://archive.canonical.com karmic/partner Packages                       
Get: 5 http://dl.google.com testing Release [2,513B]                           
Hit http://ppa.launchpad.net karmic Release                                    
Hit http://security.ubuntu.com karmic-security/restricted Packages             
Hit http://security.ubuntu.com karmic-security/main Sources                    
Hit http://security.ubuntu.com karmic-security/restricted Sources              
Hit http://security.ubuntu.com karmic-security/universe Packages               
Hit http://gb.archive.ubuntu.com karmic/main Packages                          
Hit http://gb.archive.ubuntu.com karmic/restricted Packages                    
Hit http://gb.archive.ubuntu.com karmic/main Sources                           
Hit http://gb.archive.ubuntu.com karmic/restricted Sources                     
Hit http://gb.archive.ubuntu.com karmic/universe Packages                      
Hit http://packages.medibuntu.org karmic/free Packages                         
Ign http://packages.linuxmint.com helena Release                               
Hit http://download.virtualbox.org karmic Release                              
Ign http://linux.getdropbox.com karmic/main Packages                           
Get: 6 http://dl.google.com stable Release [2,540B]                            
Hit http://ppa.launchpad.net karmic/main Packages                              
Hit http://security.ubuntu.com karmic-security/universe Sources                
Hit http://security.ubuntu.com karmic-security/multiverse Packages             
Hit http://security.ubuntu.com karmic-security/multiverse Sources              
Hit http://gb.archive.ubuntu.com karmic/universe Sources                       
Hit http://gb.archive.ubuntu.com karmic/multiverse Packages                    
Hit http://gb.archive.ubuntu.com karmic/multiverse Sources                     
Hit http://gb.archive.ubuntu.com karmic-updates/main Packages                  
Hit http://gb.archive.ubuntu.com karmic-updates/restricted Packages            
Hit http://gb.archive.ubuntu.com karmic-updates/main Sources                   
Hit http://gb.archive.ubuntu.com karmic-updates/restricted Sources             
Ign http://packages.linuxmint.com helena/main Packages                         
Hit http://packages.medibuntu.org karmic/non-free Packages                     
Ign http://switch.dl.sourceforge.net all/main Translation-en_GB                
Hit http://download.virtualbox.org karmic/non-free Packages                    
Ign http://linux.getdropbox.com karmic/main Packages                           
Get: 7 http://dl.google.com testing/non-free Packages [793B]                   
Hit http://ppa.launchpad.net karmic/main Packages                              
Hit http://gb.archive.ubuntu.com karmic-updates/universe Packages              
Hit http://gb.archive.ubuntu.com karmic-updates/universe Sources               
Hit http://gb.archive.ubuntu.com karmic-updates/multiverse Packages            
Ign http://packages.linuxmint.com helena/main Packages                         
Hit http://linux.getdropbox.com karmic/main Packages                           
Hit http://gb.archive.ubuntu.com karmic-updates/multiverse Sources             
Hit http://packages.linuxmint.com helena/main Packages                         
Get: 8 http://dl.google.com stable/non-free Packages [1,010B]                  
Get: 9 http://dl.google.com stable/main Packages [850B]                        
Hit http://switch.dl.sourceforge.net all Release                               
Ign http://switch.dl.sourceforge.net all/main Packages                         
Ign http://switch.dl.sourceforge.net all/main Packages                         
Hit http://switch.dl.sourceforge.net all/main Packages                         
Fetched 15.5kB in 14s (1,051B/s)                                               
Reading package lists... Done
W: GPG error: http://packages.linuxmint.com helena Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3EE67F3D0FF405B2

Making sure that the repositories version of Thunderbird is installed...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnspr4-dev winbind
Use 'apt-get autoremove' to remove them.
Suggested packages:
  thunderbird-gnome-support
The following NEW packages will be installed
  thunderbird
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/12.1MB of archives.
After this operation, 36.2MB of additional disk space will be used.
Selecting previously deselected package thunderbird.
(Reading database ... 188986 files and directories currently installed.)
Unpacking thunderbird (from .../thunderbird_2.0.0.23+build1+nobinonly-0ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for menu ...
Processing triggers for desktop-file-utils ...
Setting up thunderbird (2.0.0.23+build1+nobinonly-0ubuntu1) ...

Processing triggers for menu ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

A Thunderbird profile has been found at ~/.thunderbird. Do you want to make a backup of your Mozilla Thunderbird profile at ~/.thunderbird? Note that if you store your email there, this may take quite a bit of disk space. You may wish to check the size of that directory and the amount of free disk space before you answer this question. Make backup? [y/n]: 
Please enter 'y' or 'n': y

Backing up old thunderbird preferences

Retrieving package name for Thunderbird ...
Success!: thunderbird-3.0.tar.bz2

Downloading Thunderbird archive from the Mozilla site

--2009-12-10 20:48:59--  ftp://mozilla.isc.org/pub/mozilla.org/thunderbird/releases/3.0/linux-i686/en-GB/thunderbird-3.0.tar.bz2
           => `thunderbird-3.0.tar.bz2'
Resolving mozilla.isc.org... 204.152.184.113, 2001:4f8:0:2::1f
Connecting to mozilla.isc.org|204.152.184.113|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/thunderbird/releases/3.0/linux-i686/en-GB ... done.
==> SIZE thunderbird-3.0.tar.bz2 ... 10723990
==> PASV ... done.    ==> RETR thunderbird-3.0.tar.bz2 ... done.
Length: 10723990 (10M)

100%[======================================>] 10,723,990   258K/s   in 35s     

2009-12-10 20:49:36 (297 KB/s) - `thunderbird-3.0.tar.bz2' saved [10723990]


Downloading Thunderbird signature from the Mozilla site

--2009-12-10 20:49:36--  ftp://mozilla.isc.org/pub/mozilla.org/thunderbird/releases/3.0/linux-i686/en-GB/thunderbird-3.0.tar.bz2.asc
           => `thunderbird-3.0.tar.bz2.asc'
Resolving mozilla.isc.org... 204.152.184.113, 2001:4f8:0:2::1f
Connecting to mozilla.isc.org|204.152.184.113|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/thunderbird/releases/3.0/linux-i686/en-GB ... done.
==> SIZE thunderbird-3.0.tar.bz2.asc ... 323
==> PASV ... done.    ==> RETR thunderbird-3.0.tar.bz2.asc ... done.
Length: 323

100%[======================================>] 323         --.-K/s   in 0.02s   

2009-12-10 20:49:39 (20.0 KB/s) - `thunderbird-3.0.tar.bz2.asc' saved [323]

tru::1:1257530047:0:3:1:5
gpg: error reading key: public key not found
gpg --list-keys --with-colons 0E3606D9
Mozilla GPG key not present on the system. Will attempt to retrieve from keyserver.
Process returned code 2

Importing Mozilla Software Releases public key

Note that if you have never used gpg before on this system, and this is your first time running this script, there may be a delay of about a minute during the generation of a gpg keypair. This is normal and expected behavior.

gpg: requesting key 0E3606D9 from hkp server subkeys.pgp.net
gpg: requesting key 812347DD from hkp server subkeys.pgp.net
gpg: requesting key 6CE2996F from hkp server subkeys.pgp.net
gpg: key 0E3606D9: public key "Mozilla Software Releases <releases@mozilla.org>" imported
gpg: key 812347DD: public key "Mozilla Software Releases <releases@mozilla.org>" imported
gpg: key 6CE2996F: public key "Mozilla Messaging Inc. (Code Signing) <build@mozillamessaging.com>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 3
gpg:               imported: 3  (RSA: 1)
Successfully retrieved Mozilla Software Releases Public key from subkeys.pgp.net .


Verifying signature...
Note: do not worry about "untrusted key" warnings. That is normal behavior for newly imported keys.

gpg: Signature made Sat 05 Dec 2009 21:23:34 CET using RSA key ID 6CE2996F
gpg: Good signature from "Mozilla Messaging Inc. (Code Signing) <build@mozillamessaging.com>"
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: 6536 CB42 CC17 66D6 B8C6  92B4 F889 8FEF 6CE2 996F

Extracting archive


Linking dictionaries


Linking launcher to new thunderbird

Adding `local diversion of /usr/bin/mozilla-thunderbird to /usr/bin/mozilla-thunderbird.ubuntu'
Adding `local diversion of /usr/bin/thunderbird to /usr/bin/thunderbird.ubuntu'

The new Thunderbird version 3.0 has been installed successfully.

Make sure to completely quit the old version of Thunderbird for the change to take effect.

Would you like to set up automatic update checking for the official Mozilla build of Thunderbird (recommended)? This feature will regularly check for updates to Thunderbird, and put up a small unobtrusive notification message with update information, when a new release is available. [y/n] 
Please enter 'y' or 'n': y
Updater successfully installed to your crontab. Try 'crontab -l' to see your new crontab, 'crontab -e' if you decide to edit it.

Thank you for using Ubuntuzilla.

Please support this project! If you found Ubuntuzilla helpful, please consider showing your appreciation with a small donation. :)

Just visit the project website, http://ubuntuzilla.sourceforge.net/ , and click the donate button.
roger@roger-laptop:~$ 
```

---

### Post by nanotube on 2009-12-10
> **rogerdean said:**
> hi nanotube

ok, i see in your sig that ubuntuzilla is your thing, so i'm doing it again...

...and it's installed TB2 again. could this be because I'm requesting the UK english build, and perhaps this doesn't exist yet? just an idea

now rebuilding my email again :) happy to help though...


Hi
thanks for trying :)
from the log, i see that thunderbird 3 was downloaded and installed.
after the install process, try running
```
thunderbird --version
```
which should show thunderbird 3.0.

what exactly leads you to believe that thunderbird2 is installed? could you check to see where the launcher that you're using to start thunderbird points?

---

### Post by rogerdean on 2009-12-10
this bit...

```
The following NEW packages will be installed
  thunderbird
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/12.1MB of archives.
After this operation, 36.2MB of additional disk space will be used.
Selecting previously deselected package thunderbird.
(Reading database ... 188986 files and directories currently installed.)
Unpacking thunderbird (from .../thunderbird_2.0.0.23+build1+nobinonly-0ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for menu ...
Processing triggers for desktop-file-utils ...
Setting up thunderbird (2.0.0.23+build1+nobinonly-0ubuntu1) ...

```

I know it finds TB3 as the latest version, but it downloads and installs as above I'm afraid...

EDIT
oh, hang on, i think i see, it downloads TB2 if not installed, then downloads TB3, right?
doing it again to check again ;)

---

### Post by rogerdean on 2009-12-10
Ok, you're absolutely right, it was a shortcuts issue. 

Due to previous manually installed Shredder, my TB3 shortcut (/usr/share/thunderbird/thunderbird) remained. It now pointed to the newly-installed TB2 which crashes, see screenshot). 

The new TB shortcut appeared from your script, and started TB3 just fine

I guess I just didn't expect TB2 to be installed with TB3 - is this normal?

Cheers
Roger

---

### Post by nanotube on 2009-12-10
> **rogerdean said:**
> Ok, you're absolutely right, it was a shortcuts issue. 

Due to previous manually installed Shredder, my TB3 shortcut (/usr/share/thunderbird/thunderbird) remained. It now pointed to the newly-installed TB2 which crashes, see screenshot). 

The new TB shortcut appeared from your script, and started TB3 just fine

excellent :) just point your dekstop/menu shortcuts to /usr/bin/thunderbird, and then things will work as expected.

> 
I guess I just didn't expect TB2 to be installed with TB3 - is this normal?


yes, the script makes sure the repositories version is installed, just to make sure any dependencies are satisfied. I suppose it is kind of optional, but... it's there for just in case. :)

---

### Post by rogerdean on 2009-12-10
I see. Thanks for your help with this, all should be well now. Not to sound ungrateful, but I'll keep looking for a .deb to carry on a stick!
Cheers nanotube
Roger

---

### Post by nanotube on 2009-12-10
> **rogerdean said:**
> I see. Thanks for your help with this, all should be well now. 

cool 
> 
Not to sound ungrateful, but I'll keep looking for a .deb to carry on a stick!
Cheers nanotube
Roger

cheers! :)

---

### Post by Kubro on 2009-12-10
Big thanks to nanotube for ubuntuzilla! Very sweet!

---

### Post by nanotube on 2009-12-10
> **Kubro said:**
> Big thanks to nanotube for ubuntuzilla! Very sweet!
welcome, amigo :)

---

### Post by NJC on 2009-12-11
FWIW I used the following:

```
sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa && sudo apt-get update && sudo apt-get install thunderbird-3.0
```[http://www.detector-pro.com/2009/12/install-thunderbird-3-on-ubuntu.html](http://www.detector-pro.com/2009/12/install-thunderbird-3-on-ubuntu.html)

---

### Post by motorcity909 on 2009-12-11
> **nanotube said:**
> Hi

Just cancel out of that import wizard stuff, then do check for updates.

when you run it with gksudo, it opens it in root's environment - don't worry, your profile won't get messed up.

alternatively, you could just run the ubuntuzilla install process again, to install tb3 fresh.

Thanks nanotube.  I tried this but Thunderbird simply said there were no new updates.  

Will your suggestion of a fresh tb3 install also keep my profile intact?

---

### Post by nanotube on 2009-12-11
> **motorcity909 said:**
> Thanks nanotube.  I tried this but Thunderbird simply said there were no new updates.  

Will your suggestion of a fresh tb3 install also keep my profile intact?

Ah, well, maybe tb2 isn't set to automatically update to tb3, maybe only to look for v2 updates...

at any rate - your profile and mail /should/ be ok, but you should make a complete backup of your profile for 'just in case'.

as part of the install process, ubuntuzilla will prompt you to make a backup - or you can make one yourself ahead of time. but i can't stress it enough: MAKE A BACKUP. there's always a chance for things to go brown and stinky, and if that happens, you'll be very glad of your backup. :)

---

### Post by motorcity909 on 2009-12-11
> **nanotube said:**
> Ah, well, maybe tb2 isn't set to automatically update to tb3, maybe only to look for v2 updates...

at any rate - your profile and mail /should/ be ok, but you should make a complete backup of your profile for 'just in case'.

as part of the install process, ubuntuzilla will prompt you to make a backup - or you can make one yourself ahead of time. but i can't stress it enough: MAKE A BACKUP. there's always a chance for things to go brown and stinky, and if that happens, you'll be very glad of your backup. :)

Thanks again nanotube.

Am I right in saying it's 
ubuntuzilla.py -a install -p thunderbird

[FONT=Verdana]And will this overwrite v2?  Would I be best to remove TB completely first, then reinstall 
via Ubuntuzilla?

My profile is backed up daily to an ext HD and a memory stick that leaves the house with me 
(paranoid?  me? ;))

Cheers
Dave
[/FONT]

---

### Post by nanotube on 2009-12-11
> **motorcity909 said:**
> Thanks again nanotube.

Am I right in saying it's 
ubuntuzilla.py -a install -p thunderbird

yes, that's correct

> And will this overwrite v2?  Would I be best to remove TB completely first, then reinstall 
via Ubuntuzilla?

If you currently have the repositories version of thunderbird installed: don't uninstall it, ubuntuzilla's version will be installed in a different place and won't even touch it.

if you currently have the ubuntuzilla version installed - can't hurt to run the ubuntuzilla -a remove -p thunderbird first, just to make sure no old tb2 files stick around and confuse anything.

> 
My profile is backed up daily to an ext HD and a memory stick that leaves the house with me 
(paranoid?  me? ;))

always glad to see a fellow with a sensible backup strategy :)

---

### Post by motorcity909 on 2009-12-11
> **nanotube said:**
> 


If you currently have the repositories version of thunderbird installed: don't uninstall it, ubuntuzilla's version will be installed in a different place and won't even touch it.

if you currently have the ubuntuzilla version installed - can't hurt to run the ubuntuzilla -a remove -p thunderbird first, just to make sure no old tb2 files stick around and confuse anything.

My version is the repositories version.  If the Ubuntuzilla version gets installed elsewhere will I have to copy my profile into a different folder?  Won't there be a bunch of TB2 files & folders still left around?

I presume I'll need to point my TB launchers to the new version if it's installed elsewhere?

Apologies for all the questions and thank you so much for your patience.

I'm guessing that part of my issue here is that when I first moved over to Ubuntu in the summer, the repository Firefox wasn't the latest version, so I found Ubuntuzilla and it's been cool since.  However, I didn't do the same for TB as the repository version was the latest version.

---

### Post by motorcity909 on 2009-12-12
All sorted!  Got TB3 installed successfully and am loving it.

I have turned off the Smart folders - prefer separate inbox/sent/deleted folders.

That aside, it feels faster, looks great and I really like tabbed emails.

Thanks for everyone's help on this thread.

Dave

---

### Post by nanotube on 2009-12-13
> **motorcity909 said:**
> My version is the repositories version.  If the Ubuntuzilla version gets installed elsewhere will I have to copy my profile into a different folder?  Won't there be a bunch of TB2 files & folders still left around?

I presume I'll need to point my TB launchers to the new version if it's installed elsewhere?

Apologies for all the questions and thank you so much for your patience.

I'm guessing that part of my issue here is that when I first moved over to Ubuntu in the summer, the repository Firefox wasn't the latest version, so I found Ubuntuzilla and it's been cool since.  However, I didn't do the same for TB as the repository version was the latest version.

Just to clarify, even though i see in a later post that you have it all installed and figured out :)

you don't have to touch your profile, it will get picked up by tb3 automatically.

the launchers will get repointed by ubuntuzilla automatically

yes, the tb2 binaries will still be around... but what's a few megabytes between friends? :) and it doesn't hurt to have it available for 'just in case'. 

anyway, glad it all works. :)

---

### Post by thuerrschmidt on 2009-12-13
I don't think that using Ubuntuzilla, or any other software installer that doesn't integrate with Ubuntu's package manager, is a good idea. I'd even say that it's a bad idea, but that's up to you.

Anyway, the easiest way to install Thunderbird 3.0 in Karmic is by using the [Mozilla Beta PPA ]("https://launchpad.net/~micahg/+archive/mozilla-beta"). As of today it has Shredder RC3, which is by all practical means identical to the final Thunderbird 3 release.

The build from this PPA will integrate better into your Ubuntu and look much nicer than Mozilla's own. Plus, unlike the [Mozilla Daily Build PPA]("https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa"), you'll only get milestone releases, not daily updates.

---

### Post by HonzaPokorny on 2009-12-15
UPDATE: [FIXED] I downloaded the updated .deb and it worked fine. Thunderbird 3.0 is up and running. Thanks!


> **nanotube said:**
> Hi
They're using a new gpg key to sign the packages, which Ubuntuzilla wasn't aware of. Try the latest release ubuntuzilla (4.8.2) which solves this problem.

I tried to update ubuntuzilla by issuing: 

```
ubuntuzilla.py -a updateubuntuzilla
```

and received the following error: 

```
md5sum: ubuntuzilla-4.8.2-0ubuntu1-amd64.deb: No such file or directory
ubuntuzilla-4.8.2-0ubuntu1-amd64.deb: FAILED open or read
md5sum: WARNING: 1 of 1 listed file could not be read
md5sum -c /tmp/ubuntuzilla-4.8.2-0ubuntu1-amd64_md5sum.txt
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Package MD5 sum failed verification. Deleting all downloaded files and exiting.

```

As you can tell from the code, I'm using a 64bit version of ubuntu. 

Any ideas how this can be fixed?

Thanks!

---

### Post by autonomy on 2010-01-02
> **thuerrschmidt said:**
> Ubuntuzilla ... doesn't integrate with Ubuntu's package manager....Synaptic? Apt?

Is this like adding "deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) karmic non-free"?

Thunderbird 3's delete button has been buggy for me, so I used ubuntuzilla to make sure I had the latest build.

---

