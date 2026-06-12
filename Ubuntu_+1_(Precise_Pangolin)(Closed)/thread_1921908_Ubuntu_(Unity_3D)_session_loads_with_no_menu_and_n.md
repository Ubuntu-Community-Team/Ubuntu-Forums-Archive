---
title: "Ubuntu (Unity 3D) session loads with no menu and no launcher."
date: 2012-02-07
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by prusswan on 2012-02-07
At first I thought this could be caused by the partial upgrade which I attempted yesterday on a physical machine, so I have tried to reproduce the issue on a VM but failed (meaning partial upgrade is unlikely to be the cause). 

What is common on both machines is that:
Fresh install of 10.04.3 -> distribution upgrade to 12.04
ccsm and gnome-session-fallback are installed
unity --reset produces a whole bunch of errors leading to "unity-panel-service closed unexpectedly"
Ubuntu 2D / GNOME Classic (with or without effects) seem to be okay


Where can I find the startup logs for unity (if any) or other logs that may indicate the cause?

Edit: solved by purging suspect config files in home folder and replacing with files from a new user profile

---

### Post by effenberg0x0 on 2012-02-07
> **prusswan said:**
> At first I thought this could be caused by the partial upgrade which I attempted yesterday on a physical machine, so I have tried to reproduce the issue on a VM but failed (meaning partial upgrade is unlikely to be the cause). 
What is common on both machines is that:
Fresh install of 10.04.3 -> distribution upgrade to 12.04
So, you installed Lucid Lynx, and jumped over 10.10 (Maverick), 11.04 (Natty) and 11.10 (Oneiric). That's really discouraged.
[https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Alpha2#Upgrading%20from%20Ubuntu%2010.04](https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Alpha2#Upgrading%20from%20Ubuntu%2010.04)

> **prusswan said:**
> 
ccsm and gnome-session-fallback are installed
unity --reset produces a whole bunch of errors leading to "unity-panel-service closed unexpectedly"

Errors can vary from insignificant to really catastrophic ones. It would be really important to know which are those errors.

> **prusswan said:**
> 
Ubuntu 2D / GNOME Classic (with or without effects) seem to be okay
Where can I find the startup logs for unity (if any) or other logs that may indicate the cause?

/var/log/*.log hold all of your machine logs. If you paste the following line in a gnome-terminal window, it will open a Gedit instance with a summary of errors/warnings from all of your log files that you can study. 
```
MYLOG=$HOME/MyLog$(date +%d.%m.%y).log; echo '['"code"']' >> ${MYLOG} && uname -a >> ${MYLOG} && lsb_release -a >> ${MYLOG} && for LOGFILE in $(ls /var/log/*.log); do sudo grep -iHw 'segfault\|warning\|error\|critical\|lightdm\|\(WW\)\|\(EE\)' $LOGFILE | tee -a ${MYLOG}; done && echo '['"code"']' >> ${MYLOG} && DISPLAY=:0.0 gedit ${MYLOG} && rm ${MYLOG}
```However, I think it would be wasted time. The best way to test Precise Pangolin and eventually produce bug reports that can be useful to the community is to download PP ISO and install it, or upgrade a fully updated Oneiric Oncelot (11.10) perfectly working install to Precise Pangolin A1. At this point, any exotic test would be hard to debug, and would consume time that should be dedicated to serious bugs that still affect a normal install/upgrade procedure.

Regards,
Effenberg

---

### Post by mc4man on 2012-02-07
You could log in to unity-3d & then take a look at ~/.xsession-errors

personally I'd log in to unity-3d, run ccsm in a terminal & look at the output. (if or when it opens also see if the unity plugin is enabled.

Quite possible you have some local config files that aren't kosher - one way to tell is create a new user & see it it can get a good login to unity-3d

No harm in deleting ~/.config/compiz-1 & ~/.cache/compizconfig

---

### Post by prusswan on 2012-02-07
> **effenberg0x0 said:**
> So, you installed Lucid Lynx, and jumped over 10.10 (Maverick), 11.04 (Natty) and 11.10 (Oneiric). That's really discouraged.
[https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Alpha2#Upgrading%20from%20Ubuntu%2010.04](https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Alpha2#Upgrading%20from%20Ubuntu%2010.04)

However, I think it would be wasted time. The best way to test Precise Pangolin and eventually produce bug reports that can be useful to the community is to download PP ISO and install it, or upgrade a fully updated Oneiric Oncelot (11.10) perfectly working install to Precise Pangolin A1. At this point, any exotic test would be hard to debug, and would consume time that should be dedicated to serious bugs that still affect a normal install/upgrade procedure.

Regards,
Effenberg

I appreciate your response, the reason why I'm doing that is to anticipate a real migration from 10.04, I have no interest in whatever that's in between. So far mostly it is working as intended. In fact most of the problems I have resolved so far are already present pre-12.04, except for the UI which is currently in a flux. 

Edit: I will post back once I have more results with the suggestions

---

### Post by grahammechanical on 2012-02-07
Well done in becoming at tester for the upgrade path from 10.04 LTS to 12.04 LTS. In a few weeks time many 10.04 users will be getting the upgrade to 12.04 option, perhaps without asking for it. So, it should be tested.

I started testing 12.04 by upgrading an 11.10 install. I find that as the 11.10 libraries are slowly being replaced by 12.10 libraries different daemons close due to obsolete libraries that need upgrading to 12.04 libraries. This happened this morning and I expect the situation to be fixed by an update that I am about to do.

May I suggest that you go into Synaptic Package Manager and look for any Unity Libraries that need upgrading. They will be marked by a grey coloured icon. A right click will let you mark them for upgrade. Unity 5.2 has just been put into 12.04. You may have mix of libraries relating to Unity.

Regards.

---

### Post by effenberg0x0 on 2012-02-08
> **prusswan said:**
> I appreciate your response, the reason why I'm doing that is to anticipate a real migration from 10.04, I have no interest in whatever that's in between. So far mostly it is working as intended. In fact most of the problems I have resolved so far are already present pre-12.04, except for the UI which is currently in a flux. 
Edit: I will post back once I have more results with the suggestions

> **grahammechanical said:**
> Well done in becoming at tester for the upgrade path from 10.04 LTS to 12.04 LTS. In a few weeks time many 10.04 users will be getting the upgrade to 12.04 option, perhaps without asking for it. So, it should be tested.


Actually you're both right: Despite being a [COLOR=Red]_[recognizedly broken and discouraged procedure]("https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Alpha2#Upgrading%20from%20Ubuntu%2010.04")_[/COLOR], the update from 10.04 to 12.04 will be done by users. So thanks for reminding me of that. 

<Mea Culpa>We see all kinds of things here, like this _[COLOR=Red][failed upgrade from Mint to Ubuntu]("http://ubuntuforums.org/showthread.php?t=1921178")[/COLOR]_. So it's hard for me to always recognize a user willing to perform serious testing.</Mea Culpa>

Back to the business at hand: If previous advice do not work, I'd consider:
Run Unity support test:
```
sudo apt-get install nux-tools
/usr/lib/nux/unity_support_test -p

```Make sure of ownership and permissions inside $HOME, include .dotfiles/.dotdirs recursively.
```
cd && sudo chown you:you /home/you -R 

```Obs: Maybe check your chmod (also recursively) in your home to.

dpkg-reconfigure some packages and if it fails, reinstall them:```

sudo dpkg-reconfigure unity unity-2d-spread unity-lens-files unity-2d unity-asset-pool unity-lens-music unity-2d-launcher unity-common unity-scope-musicstores unity-2d-panel unity-greeter unity-services unity-2d-places unity-lens-applications compiz compiz-gnome compizconfig-backend-gconf compiz-plugins compizconfig-settings-manager compiz-plugins-default compiz-core compiz-plugins-main compiz-plugins-main-default
   
sudo apt-get install --reinstall <List of failed packages>
```But these are the workarounds to get a user a working desktop. You are not interested in just that. As a tester, you wanna know the cause(s) of the problem. So, talking about causes of failure I'd check:

- If (and which of) those packages mentioned before was(were) broken / uninstalled / partially installed and then why. You can try (and obviously improve) something like this to automate a comparison between a working and a non-working setup:
```
for PKG in $(dpkg-query -l "*" | awk 'BEGIN {FS=" "} {print $2}'); do dpkg -s $PKG | grep -e 'Package:' -e 'Version:' -e 'Status:'; done
```- Look at environment variables known to play a part in this: .Xauthority, XDG*, GDM_SESSION, COMPIZ_CONFIG_PROFILE, DESKTOP_SESSION.
- Config files to be checked: .config/compiz-1, .compiz-1, .cache/compizconfig-1, .cache/unity, 
- Dconf: Dump and grep it for related keynames.

Ideally, you can just pipe all of that to files and them diff them from those from a working setup. Differences will emerge, giving you a clearer lead on where the problems may reside.

OBS: Most of the comparisons between a working and a non-working install can be automated via simple scripting: Packages (their versions and status), key config files ($HOME/.SomeConfigFile, $HOME/.SomeConfigDir/*, /etc/Something/*, etc), environment variables, etc. It's very fast to work in that way - and it usually works, depending only on the quality of your script. In your case, for example: Create two new users, one in a fresh 12.04 install and one in the broken updated install and run something to compare the two installs. 

Regards,
Effenberg

---

### Post by prusswan on 2012-02-08
After some extensive research, my conclusion now is that this is a pre-12.04 issue like this: 
[http://askubuntu.com/questions/66737/unityjust-disappears-after-changing-launcher-icon-size-and-wont-come-back](http://askubuntu.com/questions/66737/unityjust-disappears-after-changing-launcher-icon-size-and-wont-come-back)
[http://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears](http://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears)

I have cleared out the compiz config files and packages a couple of times, to no effect.
/usr/lib/nux/unity_support_test -p (nothing wrong here)
What really bothers me is that unity --reset is unable to complete gracefully; it seems to hang after:

```


Initializing zoom options...done
WARN  2012-02-08 13:57:32 unity.glib.dbusproxy GLibDBusProxy.cpp:265 Cannot call method InfoRequest proxy /com/canonical/unity/lens/commands does not exist
WARN  2012-02-08 13:57:32 unity.glib.dbusproxy GLibDBusProxy.cpp:265 Cannot call method SetViewType proxy /com/canonical/unity/lens/commands does not exist
WARN  2012-02-08 13:57:32 unity.glib.dbusproxy GLibDBusProxy.cpp:265 Cannot call method InfoRequest proxy /com/canonical/unity/lens/applications does not exist
WARN  2012-02-08 13:57:32 unity.glib.dbusproxy GLibDBusProxy.cpp:265 Cannot call method SetViewType proxy /com/canonical/unity/lens/applications does not exist
Setting Update "main_menu_key"
Setting Update "run_key"
WARN  2012-02-08 13:58:30 unity.glib.dbusproxy GLibDBusProxy.cpp:265 Cannot call method InfoRequest proxy /com/canonical/unity/lens/commands does not exist
WARN  2012-02-08 13:58:30 unity.glib.dbusproxy GLibDBusProxy.cpp:265 Cannot call method SetViewType proxy /com/canonical/unity/lens/commands does not exist
WARN  2012-02-08 13:58:30 unity.glib.dbusproxy GLibDBusProxy.cpp:265 Cannot call method InfoRequest proxy /com/canonical/unity/lens/applications does not exist
WARN  2012-02-08 13:58:30 unity.glib.dbusproxy GLibDBusProxy.cpp:265 Cannot call method SetViewType proxy /com/canonical/unity/lens/applications does not exist
WARN  2012-02-08 13:58:30 unity.glib.dbusproxy GLibDBusProxy.cpp:265 Cannot call method InfoRequest proxy /com/canonical/unity/lens/music does not exist
WARN  2012-02-08 13:58:30 unity.glib.dbusproxy GLibDBusProxy.cpp:265 Cannot call method SetViewType proxy /com/canonical/unity/lens/music does not exist
WARN  2012-02-08 13:58:30 unity.glib.dbusproxy GLibDBusProxy.cpp:265 Cannot call method InfoRequest proxy /com/canonical/unity/lens/files does not exist
WARN  2012-02-08 13:58:30 unity.glib.dbusproxy GLibDBusProxy.cpp:265 Cannot call method SetViewType proxy /com/canonical/unity/lens/files does not exist
WARN  2012-02-08 13:58:31 nux.core.object Object.cpp:289 There are ObjectPtr hosting this object. Release all of them to destroy this object. 
Object allocated at: /build/buildd/unity-5.2.0/plugins/unityshell/src/FilterGenreWidget.cpp:46

WARN  2012-02-08 13:58:31 nux.core.object Object.cpp:289 There are ObjectPtr hosting this object. Release all of them to destroy this object. 
Object allocated at: /build/buildd/unity-5.2.0/plugins/unityshell/src/FilterRatingsWidget.cpp:45

WARN  2012-02-08 13:58:31 nux.core.object Object.cpp:289 There are ObjectPtr hosting this object. Release all of them to destroy this object. 
Object allocated at: /build/buildd/unity-5.2.0/plugins/unityshell/src/FilterGenreWidget.cpp:46

WARN  2012-02-08 13:58:31 nux.core.object Object.cpp:289 There are ObjectPtr hosting this object. Release all of them to destroy this object. 
Object allocated at: /build/buildd/unity-5.2.0/plugins/unityshell/src/FilterMultiRangeWidget.cpp:46

WARN  2012-02-08 13:58:31 nux.core.object Object.cpp:289 There are ObjectPtr hosting this object. Release all of them to destroy this object. 
Object allocated at: /build/buildd/unity-5.2.0/plugins/unityshell/src/FilterGenreWidget.cpp:46

WARN  2012-02-08 13:58:31 nux.core.object Object.cpp:289 There are ObjectPtr hosting this object. Release all of them to destroy this object. 
Object allocated at: /build/buildd/unity-5.2.0/plugins/unityshell/src/FilterGenreWidget.cpp:46

WARN  2012-02-08 13:58:31 nux.core.object Object.cpp:289 There are ObjectPtr hosting this object. Release all of them to destroy this object. 
Object allocated at: /build/buildd/unity-5.2.0/plugins/unityshell/src/FilterGenreWidget.cpp:46

WARN  2012-02-08 13:58:31 nux.core.object Object.cpp:289 There are ObjectPtr hosting this object. Release all of them to destroy this object. 
Object allocated at: /build/buildd/unity-5.2.0/plugins/unityshell/src/FilterMultiRangeWidget.cpp:46

WARN  2012-02-08 13:58:31 unity.iconloader IconLoader.cpp:492 Unable to load icon file:///usr/share/icons/unity-icon-theme/places/svg/category-installed.svg at size 24: Error opening file: No such file or directory
WARN  2012-02-08 13:58:31 unity.iconloader IconLoader.cpp:492 Unable to load icon file:///usr/share/icons/unity-icon-theme/places/svg/category-installed.svg at size 24: Error opening file: No such file or directory
WARN  2012-02-08 13:58:31 unity.iconloader IconLoader.cpp:492 Unable to load icon file:///usr/share/icons/unity-icon-theme/places/svg/category-available.svg at size 24: Error opening file: No such file or directory
WARN  2012-02-08 13:58:31 unity.iconloader IconLoader.cpp:492 Unable to load icon file:///usr/share/icons/unity-icon-theme/places/svg/category-available.svg at size 24: Error opening file: No such file or directory


``` 

although at this point the launcher and menu are actually loaded and remain if I close the terminal by force. Does NOT persist in a new Unity 3D session (that is, the problem will remain after a logout and relogin). I really can't tell if this should be attributed more to CCSM or Unity

---

### Post by effenberg0x0 on 2012-02-08
> **prusswan said:**
> After some extensive research, my conclusion now is that this is a pre-12.04 issue like this: 
[http://askubuntu.com/questions/66737/unityjust-disappears-after-changing-launcher-icon-size-and-wont-come-back](http://askubuntu.com/questions/66737/unityjust-disappears-after-changing-launcher-icon-size-and-wont-come-back)
[http://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears](http://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears)

I have cleared out the compiz config files and packages a couple of times, to no effect.
/usr/lib/nux/unity_support_test -p (nothing wrong here)
What really bothers me is that unity --reset is unable to complete gracefully; it seems to hang after:

```


Initializing zoom options...done
WARN  2012-02-08 13:57:32 unity.glib.dbusproxy GLibDBusProxy.cpp:265 Cannot call method InfoRequest proxy /com/canonical/unity/lens/commands does not exist
WARN  2012-02-08 13:57:32 unity.glib.dbusproxy GLibDBusProxy.cpp:265 Cannot call method SetViewType proxy /com/canonical/unity/lens/commands does not exist
WARN  2012-02-08 13:57:32 unity.glib.dbusproxy GLibDBusProxy.cpp:265 Cannot call method InfoRequest proxy /com/canonical/unity/lens/applications does not exist
WARN  2012-02-08 13:57:32 unity.glib.dbusproxy GLibDBusProxy.cpp:265 Cannot call method SetViewType proxy /com/canonical/unity/lens/applications does not exist
Setting Update "main_menu_key"
Setting Update "run_key"
WARN  2012-02-08 13:58:30 unity.glib.dbusproxy GLibDBusProxy.cpp:265 Cannot call method InfoRequest proxy /com/canonical/unity/lens/commands does not exist
WARN  2012-02-08 13:58:30 unity.glib.dbusproxy GLibDBusProxy.cpp:265 Cannot call method SetViewType proxy /com/canonical/unity/lens/commands does not exist
WARN  2012-02-08 13:58:30 unity.glib.dbusproxy GLibDBusProxy.cpp:265 Cannot call method InfoRequest proxy /com/canonical/unity/lens/applications does not exist
WARN  2012-02-08 13:58:30 unity.glib.dbusproxy GLibDBusProxy.cpp:265 Cannot call method SetViewType proxy /com/canonical/unity/lens/applications does not exist
WARN  2012-02-08 13:58:30 unity.glib.dbusproxy GLibDBusProxy.cpp:265 Cannot call method InfoRequest proxy /com/canonical/unity/lens/music does not exist
WARN  2012-02-08 13:58:30 unity.glib.dbusproxy GLibDBusProxy.cpp:265 Cannot call method SetViewType proxy /com/canonical/unity/lens/music does not exist
WARN  2012-02-08 13:58:30 unity.glib.dbusproxy GLibDBusProxy.cpp:265 Cannot call method InfoRequest proxy /com/canonical/unity/lens/files does not exist
WARN  2012-02-08 13:58:30 unity.glib.dbusproxy GLibDBusProxy.cpp:265 Cannot call method SetViewType proxy /com/canonical/unity/lens/files does not exist
WARN  2012-02-08 13:58:31 nux.core.object Object.cpp:289 There are ObjectPtr hosting this object. Release all of them to destroy this object. 
Object allocated at: /build/buildd/unity-5.2.0/plugins/unityshell/src/FilterGenreWidget.cpp:46

WARN  2012-02-08 13:58:31 nux.core.object Object.cpp:289 There are ObjectPtr hosting this object. Release all of them to destroy this object. 
Object allocated at: /build/buildd/unity-5.2.0/plugins/unityshell/src/FilterRatingsWidget.cpp:45

WARN  2012-02-08 13:58:31 nux.core.object Object.cpp:289 There are ObjectPtr hosting this object. Release all of them to destroy this object. 
Object allocated at: /build/buildd/unity-5.2.0/plugins/unityshell/src/FilterGenreWidget.cpp:46

WARN  2012-02-08 13:58:31 nux.core.object Object.cpp:289 There are ObjectPtr hosting this object. Release all of them to destroy this object. 
Object allocated at: /build/buildd/unity-5.2.0/plugins/unityshell/src/FilterMultiRangeWidget.cpp:46

WARN  2012-02-08 13:58:31 nux.core.object Object.cpp:289 There are ObjectPtr hosting this object. Release all of them to destroy this object. 
Object allocated at: /build/buildd/unity-5.2.0/plugins/unityshell/src/FilterGenreWidget.cpp:46

WARN  2012-02-08 13:58:31 nux.core.object Object.cpp:289 There are ObjectPtr hosting this object. Release all of them to destroy this object. 
Object allocated at: /build/buildd/unity-5.2.0/plugins/unityshell/src/FilterGenreWidget.cpp:46

WARN  2012-02-08 13:58:31 nux.core.object Object.cpp:289 There are ObjectPtr hosting this object. Release all of them to destroy this object. 
Object allocated at: /build/buildd/unity-5.2.0/plugins/unityshell/src/FilterGenreWidget.cpp:46

WARN  2012-02-08 13:58:31 nux.core.object Object.cpp:289 There are ObjectPtr hosting this object. Release all of them to destroy this object. 
Object allocated at: /build/buildd/unity-5.2.0/plugins/unityshell/src/FilterMultiRangeWidget.cpp:46

WARN  2012-02-08 13:58:31 unity.iconloader IconLoader.cpp:492 Unable to load icon file:///usr/share/icons/unity-icon-theme/places/svg/category-installed.svg at size 24: Error opening file: No such file or directory
WARN  2012-02-08 13:58:31 unity.iconloader IconLoader.cpp:492 Unable to load icon file:///usr/share/icons/unity-icon-theme/places/svg/category-installed.svg at size 24: Error opening file: No such file or directory
WARN  2012-02-08 13:58:31 unity.iconloader IconLoader.cpp:492 Unable to load icon file:///usr/share/icons/unity-icon-theme/places/svg/category-available.svg at size 24: Error opening file: No such file or directory
WARN  2012-02-08 13:58:31 unity.iconloader IconLoader.cpp:492 Unable to load icon file:///usr/share/icons/unity-icon-theme/places/svg/category-available.svg at size 24: Error opening file: No such file or directory


```although at this point the launcher and menu are actually loaded and remain if I close the terminal by force. Does NOT persist in a new Unity 3D session (that is, the problem will remain after a logout and relogin). I really can't tell if this should be attributed more to CCSM or Unity

Out of curiosity: WHat are your ccsm profiles and if they have Unityshell enabled:
```
for CCSMPROFILE in $(gconftool-2 --all-dirs /apps/compizconfig-1/profiles); do echo -e "\nProfile: ${CCSMPROFILE} Active Plugins:\n" && gconftool-2 --get ${CCSMPROFILE}/general/screen0/options/active_plugins; done
```

But I think I would reinstall unity-lens*, given your log. 

Regards,
Effenberg

---

### Post by prusswan on 2012-02-08
> **effenberg0x0 said:**
> Out of curiosity: WHat are your ccsm profiles and if they have Unityshell enabled:
```
for CCSMPROFILE in $(gconftool-2 --all-dirs /apps/compizconfig-1/profiles); do echo -e "\nProfile: ${CCSMPROFILE} Active Plugins:\n" && gconftool-2 --get ${CCSMPROFILE}/general/screen0/options/active_plugins; done
```

But I think I would reinstall unity-lens*, given your log. 

Regards,
Effenberg


my ccsm profiles:

```

Profile: /apps/compizconfig-1/profiles/Default Active Plugins:

No value set for `/apps/compizconfig-1/profiles/Default/general/screen0/options/active_plugins'

Profile: /apps/compizconfig-1/profiles/unity Active Plugins:

[core,bailer,detection,composite,opengl,decor,mousepoll,vpswitch,regex,animation,snap,expo,move,compiztoolbox,place,grid,imgpng,gnomecompat,wall,ezoom,workarounds,resize,fade,unitymtgrabhandles,scale,session,unityshell]

Profile: /apps/compizconfig-1/profiles/fooo Active Plugins:

No value set for `/apps/compizconfig-1/profiles/fooo/general/screen0/options/active_plugins'

```

---

### Post by effenberg0x0 on 2012-02-08
> **prusswan said:**
> my ccsm profiles:

```

Profile: /apps/compizconfig-1/profiles/Default Active Plugins:

No value set for `/apps/compizconfig-1/profiles/Default/general/screen0/options/active_plugins'

Profile: /apps/compizconfig-1/profiles/unity Active Plugins:

[core,bailer,detection,composite,opengl,decor,mousepoll,vpswitch,regex,animation,snap,expo,move,compiztoolbox,place,grid,imgpng,gnomecompat,wall,ezoom,workarounds,resize,fade,unitymtgrabhandles,scale,session,unityshell]

Profile: /apps/compizconfig-1/profiles/fooo Active Plugins:

No value set for `/apps/compizconfig-1/profiles/fooo/general/screen0/options/active_plugins'

```
Yea, unityshell is active in the Unity profile, so nothing there.
Maybe dpkg-query -s the unity* packages? You might get some status == partially installed, etc. Also, if you're unsure about Compiz, you might want to test them too.

Just checking: Do you see the same behavior with a newly created user?

Regards,
Effenberg

---

### Post by prusswan on 2012-02-08
Indeed, a new user is working, so this is probably not a package problem (I failed to find any so far).

---

### Post by mc4man on 2012-02-08
Then you should be able to work out, either methodically or with a hatchet.
You may want to try the 2 user files for dconf in ~/.cache/dconf & ~/.config/dconf (move, rename or delete
~/.gconf is another area, & while not likely an issue what does ~/.dmrc say

---

### Post by prusswan on 2012-02-08
Solved. It is one of the files present in one of the .prefixed folders in the current user profile but not in the new user profile (I did not have to modify any file on the home path itself such as .bashrc) , doubtful I will hunt down what file this is exactly until it occurs again however. Thanks for all the help!

---

