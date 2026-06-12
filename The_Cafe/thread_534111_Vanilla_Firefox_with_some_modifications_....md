---
title: "Vanilla Firefox with some modifications ..."
date: 2007-08-24
forum: The Cafe
---

### Post by capink on 2007-08-24
After having several problems with firefox sometime ago, I decided to create my own debian package for firefox using the mozilla binaries.

I wondered why I am keeping this [package]("http://rapidshare.com/files/51108015/xubuntu-firefox_2.0.0.5-zaki1_i386.deb.html") for myself alone? maybe someone would be interested in the package.

The package is the basically the mozilla binaries (firefox 2.0.0.5) with some modifications:

1. The path to the files in the packages reside in /opt/firefox except for some folders that I will highlight later.

2. Symlinked /opt/firefox/firefox to /usr/bin/firefox

3. Created a menu entry for firefox (/usr/share/applications/firefox).

4. Removed the extensions that came with the mozilla binary.

5. Moved the plugins directory form /opt/firefox/plugins to /usr/lib/firefox/plugins so that the package is compatible with firefox plugins in ubuntu repositories.

6. Flash is preinstalled within the package. Modifications to the package control file so that flashplugin-nonfree is added to (Replaces: ), ( Provides: ) and ( Conflicts: ) fields.

7. Installed the following extensions globally, meaning that they will be available for every user on the system without the need to install them on each user's home directory. They will also be removed on uninstalling the package. Here is a list for the installed extensions:

> A. Downthemall: download manager/accelerator built inside Firefox. It works side by side with firefox own download manager. But it have some extra features.
	
B. Flashblock: Blocks Flash so it won't get in your way, but if you want to see it, just click on a play button.
	
C. Unplug: UnPlug is an extension which lets you save video and audio which is embedded on a webpage - it's a video download tool. This extension has been particularly helpful in downloading youtube videos to my hard disk.
	
D. MediaPlayerConnectivity: Allow you to launch embed video of website in an external application (vlc, mplayer .....) with a simple click.
	
E. Blue Ice: Blue theme for firefox. For more details look here:
	[https://addons.mozilla.org/en-US/firefox/addon/3085](https://addons.mozilla.org/en-US/firefox/addon/3085)
	
F. iFox Graphite: Dark theme for firefox. For more details look here:
	[https://addons.mozilla.org/en-US/firefox/addon/1315](https://addons.mozilla.org/en-US/firefox/addon/1315)
	
8. everything configured to run java once you install the necessary packages *:

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```
	
9. IPv6 disabled by default. **

10. Slight Modifications to the interface making the icons look bigger and with underlining text. ***

11. In he control file of the package firefox is listed as an entry in ( Replaces: ), ( Conflicts: ) and ( Provides: ) fields, so as to remove the original firefox - without breaking depencies - upon installation of this custom package. This worked in my system, but mine was heavily customized ( a lot of default packages uninstalled) by the time I installed this package.

12. The package name is xubuntu-firefox. Again to avoid conflict with ubuntu firefox ( In case ubuntu firefox has a higher version number).



Note: Some settings in this package will not take effect if you have an old firefox account on your home directory. The workaround to this is to remove - and backup - you old firefox accounts:

```
cp ~/.mozilla/firefox/ ~/.mozilla/firefox_bak
```

Don't forget to copy your bookmarks file from the old to the new account.

The details for which settings will not take effect with old accounts, and which files exactly you need to delete in order to activate the new settings is explained below (you can bypass all this by simply removing your old account after backing up your bookmarks as explained above):

* Java is enabled by default within the preferences file that come with the package. But if you have a previous account on you home directory, you will have to either enable java manualy ( Edit > Preferences > Content > Enable java ) or simply delete the prefrences file (prefs.js) in you /home/user/.mozilla/firefox/account.../prefs.js
(This can be ignored if you simply delete your old account after backing up your bookmarks ~/.mozilla/firefox/account../bookmarks.html)

** Again you will have to delete you old preferences file for this to take effect. Or if you want your old file you can disable ipv6 manually (type about:config in the address bar > Type ipv6 in the filter bar > right click on network.dns.disable.Ipv6 and select toggle so that the value field change to true )
(This can be ignored if you simply delete your old account after backing up your bookmarks ~/.mozilla/firefox/account../bookmarks.html)

*** These interface will not work if you have an old account on you home directory. If you want to try this out, delete the file "localstore.rdf" in your account directory after backing it up.
(This can be ignored if you simply delete your old account after backing up your bookmarks ~/.mozilla/firefox/account../bookmarks.html)

Note: Installing this package worked alright for me. But as I mentioned above, by the time I installed this package my system was heavily customized. By that time a lot of the packages that depended on firefox were already removed. So please backup you system before proceeding. I AM NOT RESPONSIBLE FOR ANY DAMAGE THAT MIGHT HAPPEN TO YOUR SYSTEM. Here is a  [guide]("http://www.psychocats.net/ubuntu/partimage") for backing up your system, and [here]("http://ubuntuforums.org/showthread.php?t=35087") is another one.


Note: If after trying out the package you want to restore ubuntu firefox - without the package manager complaining about any broken dependencies - the command will be:

```
sudo aptitude install firefox+ xubuntu-firefox_
```

the above command will install original firefox and remove xubuntu-firefox at the same time.

Here is the control file of the package if anyone is interested to look at before downloading:
```
Package: xubuntu-firefox
Priority: optional
Section: web
Installed-Size: 35964
Maintainer: user <user@company.com>
Architecture: i386
Version: 2.0.0.5-zaki1
Replaces: mozilla-firefox, firefox
Provides: www-browser, firefox, flashplugin-nonfree
Depends: fontconfig, psmisc, debianutils (>= 1.16), libatk1.0-0 (>= 1.12.1), libc6 (>= 2.4-1), libcairo2 (>= 1.2.4), libfontconfig1 (>= 2.3.0), libfreetype6 (>= 2.2), libgcc1 (>= 1:4.1.1-12), libglib2.0-0 (>= 2.12.0), libgtk2.0-0 (>= 2.10.3), libjpeg62, libmyspell3c2, libpango1.0-0 (>= 1.14.5), libpng12-0 (>= 1.2.8rel), libstdc++6 (>= 4.1.1-12), libx11-6, libxft2 (>> 2.1.1), libxrender1, libxt6, zlib1g (>= 1:1.2.1)
Conflicts: mozilla-firefox (<< 1.5.dfsg-1), firefox, flashplugin-nonfree
Description: lightweight web browser based on Mozilla
 Firefox is a redesign of the Mozilla browser component, similar to
 Galeon, K-Meleon and Camino, but written using the XUL user interface
 language and designed to be lightweight and cross-platform.
 .
 This browser was previously known as Firebird and Phoenix. . .
```



link: [http://rapidshare.com/files/51108015/xubuntu-firefox_2.0.0.5-zaki1_i386.deb.html]("http://rapidshare.com/files/51108015/xubuntu-firefox_2.0.0.5-zaki1_i386.deb.html")

---

