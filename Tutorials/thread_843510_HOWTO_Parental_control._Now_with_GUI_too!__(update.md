---
title: "HOWTO: Parental control. Now with GUI too!  (updated version)"
date: 2008-06-28
forum: Tutorials
---

### Post by KIAaze on 2008-06-28
_**Description:**_
WebContentControl is a parental control GUI (more specifically a GUI for DansGuardian+TinyProxy+FireHol).

_**Official website:**_ [https://launchpad.net/webcontentcontrol](https://launchpad.net/webcontentcontrol)

Feedback is very welcome. And help too!

Please report bugs at [https://bugs.launchpad.net/webcontentcontrol](https://bugs.launchpad.net/webcontentcontrol)

**IMPORTANT:** If you get blank pages for non-banned sites, see here: [https://launchpad.net/webcontentcontrol/+announcement/4830](https://launchpad.net/webcontentcontrol/+announcement/4830)

_**Pre-Installation:**_
Please make sure you have the "universe" repository enabled.

Go to System->Administration->Software sources and check the "universe" repository.
More info: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

_**Installation:**_
There are three ways to install WebContentControl:
1)Through the PPA repositories
2)From the Debian package
3)From source

_**1)Through the PPA repositories**_
```

deb http://ppa.launchpad.net/webcontentcontrol/webcontentcontrol/ubuntu lucid main 
deb-src http://ppa.launchpad.net/webcontentcontrol/webcontentcontrol/ubuntu lucid main 

```
See here for how to add repositories:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Add the repos by command-line:
```
sudo add-apt-repository ppa:webcontentcontrol/webcontentcontrol
sudo apt-get update
```

Once you've added those repositories, just:
```
sudo apt-get install webcontentcontrol
```
(Or use Synaptic package manager if you prefer a GUI.)

_**2)From the Debian package**_
Download the latest .deb from the site and double-click on it or by command-line:
```
sudo gdebi <package>.deb
```

_**3)From source**_
```

sudo apt-get install gambas2-runtime gambas2-gb-qt gambas2-gb-form gambas2-gb-form-dialog gambas2-gb-qt-kde gambas2-gb-qt-kde-html
sudo apt-get install dansguardian tinyproxy firehol

```
Then download the latest version on [https://launchpad.net/webcontentcontrol/+download](https://launchpad.net/webcontentcontrol/+download) and:
```
tar -xzvf webcontentcontrol-1.0.tar.gz
cd webcontentcontrol-1.0
./configure && make && sudo make install

```

The shortcut should be created in Applications->System tools.
If it isn't, the command-line to launch it is:
```
/usr/bin/webcontentcontrol
```

_**How to uninstall it:**_
```
sudo make uninstall
```
____________________________________

_**List of filtering solutions/projects:**_
[LIST]
[*]WebContentControl: [https://launchpad.net/webcontentcontrol](https://launchpad.net/webcontentcontrol)
[*]Webstrict: [http://www.ubuntume.com/webstrict](http://www.ubuntume.com/webstrict) + [https://launchpad.net/webstrict](https://launchpad.net/webstrict)
[*]GChildCare (not yet available): [https://launchpad.net/gchildcare](https://launchpad.net/gchildcare)
[*]UbuntuCE's Parental control GUI: [http://linux.softpedia.com/get/Security/Parental-control-24501.shtml](http://linux.softpedia.com/get/Security/Parental-control-24501.shtml)
[*]Squid+Squidgard:
[https://help.ubuntu.com/community/SquidGuard](https://help.ubuntu.com/community/SquidGuard) + [http://www.squidguard.org/](http://www.squidguard.org/)
[*]SmoothGuardian (by the creator of DansGuardian, commercial version with web-based easy to use interface): [http://smoothwall.net/products/smoothguardian2008/](http://smoothwall.net/products/smoothguardian2008/) + [http://dansguardian.org/?page=smoothwall](http://dansguardian.org/?page=smoothwall)
[*]MintNanny: [http://www.linuxmint.com/blog/?p=350](http://www.linuxmint.com/blog/?p=350)
[*]MoBlock, an IP blocker: [http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/) or [https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock) (deprecated site: [http://moblock.berlios.de/](http://moblock.berlios.de/))
[*]TimeKpr, track and control account usage: [https://launchpad.net/timekpr](https://launchpad.net/timekpr)
[*]Discussion about K9 web protection GNU/Linux port: [http://forums.bluecoat.com/viewtopic.php?f=13&t=3179&st=0&sk=t&sd=a&hilit=linux](http://forums.bluecoat.com/viewtopic.php?f=13&t=3179&st=0&sk=t&sd=a&hilit=linux) (suggested by eric.duveau)
[*]Mandriva Linux Parental Control: DrakGuard: [http://www.mandriva.com/enterprise/en/company/press/mandriva-presents-its-latest-distribution-mandriva-linux-2008-spring](http://www.mandriva.com/enterprise/en/company/press/mandriva-presents-its-latest-distribution-mandriva-linux-2008-spring) and [http://rpm.pbone.net/index.php3/stat/4/idpl/9208569/com/drakguard-0.6-1mdv2009.0.noarch.rpm.html](http://rpm.pbone.net/index.php3/stat/4/idpl/9208569/com/drakguard-0.6-1mdv2009.0.noarch.rpm.html)
[*]A content filtering solution for Linux-based netbooks (proprietary): [http://www.mobicip.com/online_safety/netbooks](http://www.mobicip.com/online_safety/netbooks)
[*]Gnome Nanny (under development): [http://projects.gnome.org/nanny/](http://projects.gnome.org/nanny/) or [https://launchpad.net/nanny](https://launchpad.net/nanny)
[*]Timedoctor, a closed-source cross-platform time-tracking solution, does not block: [http://www.timedoctor.com/index.php](http://www.timedoctor.com/index.php)
Related links: [http://www.rescuetime.com/](http://www.rescuetime.com/) (no GNU/Linux support) and [http://www.timedoctor.com/blog/2010/07/25/how-is-time-doctor-different-than-rescue-time](http://www.timedoctor.com/blog/2010/07/25/how-is-time-doctor-different-than-rescue-time)
[/LIST]

_**DNS filtering:**_
[LIST]
[*]OpenDNS (suggested by forger): [http://www.opendns.com/](http://www.opendns.com/)
[*]GNU/Linux Desktop parental control based on Opendns.com by Eric Duveau: [http://forums.opendns.com/comments.php?DiscussionID=2942&page=1#Comment_18690](http://forums.opendns.com/comments.php?DiscussionID=2942&page=1#Comment_18690)
[*]ScrubIT: [http://www.scrubit.com/](http://www.scrubit.com/)
[/LIST]

_**Kiosk specific (for internet cafes, etc):**_
[LIST]
[*]Kiosk: [http://kiosk.mozdev.org/](http://kiosk.mozdev.org/)
[*]Lock down KDE settings: [http://jriddell.org/programs/kiosk-article.html](http://jriddell.org/programs/kiosk-article.html)
[*]Lock down Gnome settings + disable virtual terminals: [http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/desktop-guide/s1-ddg-lockdown-disable-command-line.html](http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/desktop-guide/s1-ddg-lockdown-disable-command-line.html)
[*]Disable ctrl+alt+backspace: [http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/en-US/Reference_Guide/s3-x-server-config-xorg.conf-serverf.html](http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/en-US/Reference_Guide/s3-x-server-config-xorg.conf-serverf.html)
[*]KDE Kiosk Admin Tool: [http://extragear.kde.org/apps/kiosktool/](http://extragear.kde.org/apps/kiosktool/)
[*]Ubuntu server and DansGuardian for filtering public wireless access: [http://www.branchdistrictlibrary.org/professional/ubuntu_and_dansguardian.php](http://www.branchdistrictlibrary.org/professional/ubuntu_and_dansguardian.php)
[/LIST]

_**Firefox specific:**_
[LIST]
[*][http://kb.mozillazine.org/Parental_controls](http://kb.mozillazine.org/Parental_controls)
[/LIST]

_**Firewalls and blocking MSN:**_
[LIST]
[*]NuFW: An authenticating firewall: [http://www.nufw.org/](http://www.nufw.org/)
[*]How to block MSN: [http://blog.eglis.com/index.php/post/2005/11/16/Bloquer-le-protocol-MSN](http://blog.eglis.com/index.php/post/2005/11/16/Bloquer-le-protocol-MSN) (French)
[/LIST]

_**For Windows:**_
[LIST]
[*]LogProtect (Windows only, but Free/Libre Software): [http://www.logprotect.fr/](http://www.logprotect.fr/)
[*]K9 Web Protection (proprietary): [http://www1.k9webprotection.com/](http://www1.k9webprotection.com/)
[*]Time control on Windows: [http://www.dougknox.com/xp/tips/xp_restrict_users.htm](http://www.dougknox.com/xp/tips/xp_restrict_users.htm) and [http://www.builderau.com.au/program/windows/soa/Force-users-to-log-off-when-their-time-is-up/0,339024644,339282967,00.htm](http://www.builderau.com.au/program/windows/soa/Force-users-to-log-off-when-their-time-is-up/0,339024644,339282967,00.htm)
[/LIST]

**_Useful links:_**
[LIST]
[*]Setup without iptables: [http://www.vollmar.ch/dansguardian-e.html](http://www.vollmar.ch/dansguardian-e.html)
[*]Sarg - Squid Analysis Report Generator: [http://sarg.sourceforge.net/sarg.php](http://sarg.sourceforge.net/sarg.php)
[*]DansGuardian Documentation Wiki: [http://contentfilter.futuragts.com/wiki/doku.php?id=main_index](http://contentfilter.futuragts.com/wiki/doku.php?id=main_index)
[/LIST]

_**How it works:**_
Note: Tinyproxy is equivalent to Squid and Firehol is equivalent to iptables (FireHol manages iptables).
[LIST]
[*][http://dansguardian.org/?page=dgflow](http://dansguardian.org/?page=dgflow) (except that WebContentControl forces the use of the proxy through FireHol)
[*][http://www.zephyrsoft.net/files/linux-filtering-monitoring-howto.pdf](http://www.zephyrsoft.net/files/linux-filtering-monitoring-howto.pdf) (Picture inside, as well as script for mailing banned sites access attempts to someone)
[/LIST]

If you know other projects, useful links, etc, please tell me so I can add them to the list.

_**FAQ, troubleshooting and tips:**_
[LIST=1]
[*]Is user-specific configuration possible?
Not yet. But you can do it manually.
It requires setting up some authentication method (so that dansguardian can identify the user).
I managed to do it using squid (webcontentcontrol uses tinyproxy instead):
[http://tech.groups.yahoo.com/group/dansguardian/message/22651](http://tech.groups.yahoo.com/group/dansguardian/message/22651)
See here for more info:
[http://contentfilter.futuragts.com/wiki/doku.php?id=user_identification_methods](http://contentfilter.futuragts.com/wiki/doku.php?id=user_identification_methods)
[http://contentfilter.futuragts.com/wiki/doku.php?id=group_configuration](http://contentfilter.futuragts.com/wiki/doku.php?id=group_configuration)

[*]If the internet doesn't work anymore or isn't filtered: Please post the contents of the following files:
```
/etc/dansguardian/dansguardian.conf
/etc/tinyproxy/tinyproxy.conf
/etc/firehol/firehol.conf

```
and also the output of this command:
```
sudo lsof -i :8080
```

[*]If almost everything you google gets blocked: Just turn on Google safe mode again. ;)

[*]Filtering not working over wireless?
Three solutions:
1)Lock WPA interfaces by clicking on the "WPA interfaces unlocked" button.
2)Lock the firefox proxy settings from the GUI and disable/uninstall all other browsers (or lock their proxy settings to port 8080 if you know how to do it).
3)Restart FireHol after wireless has started.

[*]SSL not blocked?
You have to lock down the browser settings for this to work. cf explanation above.

[*]Dansguardian tweaking tips:
Use [http://urlblacklist.com/](http://urlblacklist.com/) or [http://www.shallalist.de/](http://www.shallalist.de/) (suggested by eric.duveau) ;)

[*]Also, it's useful to comment out "japanese pornography" in the weightedphraselist, as well as whitelist all webmail sites in the "exceptionsitelist".

/etc/dansguardian/lists/exceptionsitelist:
```

...
.Include</etc/dansguardian/lists/blacklists/mail/domains>
...

```
/etc/dansguardian/lists/exceptionurllist:
```

...
.Include</etc/dansguardian/lists/blacklists/mail/urls>
...

```
/etc/dansguardian/lists/weightedphraselist:
```

...
##.Include</etc/dansguardian/lists/phraselists/pornography/weighted_japanese> #ALPHA#
...

```
...because some valid sites tend to get blocked by it due to some strange encoding problems. :(

[*]Don't forget to prevent getting any filesharing program (or configure your firewall to block ports):
/etc/dansguardian/lists/bannedsitelist:
```
...
.Include</etc/dansguardian/lists/blacklists/filesharing/domains>
...

```
/etc/dansguardian/lists/bannedurllist:
```
...
.Include</etc/dansguardian/lists/blacklists/filesharing/urls>
...

```

An interface to select categories from the blacklists directory is planned. ;)

[*]How to disable X11 forwarding in openssh:
I created a patch for this, which you can get here: [http://bazaar.launchpad.net/%7Ezohn-joidberg/webcontentcontrol/main/annotate/head%3A/openssh-5.2p1_disableX11.patch](http://bazaar.launchpad.net/%7Ezohn-joidberg/webcontentcontrol/main/annotate/head%3A/openssh-5.2p1_disableX11.patch)
Download openssh-5.2p1.tar.gz from [http://www.openssh.com/](http://www.openssh.com/)
Then just:
```
tar -xzvf openssh-5.2p1.tar.gz
cd openssh-5.2p1
patch -p2 < ../openssh-5.2p1_disableX11.patch
./configure
make
sudo make install

```
[*] Using a custom proxy (like squid):
I added the possibility to disable filtering configuration during install, as well as choose a custom proxy!

Just do the following to use squid instead of tinyproxy:
```
bzr branch lp:webcontentcontrol
cd webcontentcontrol
./configure --with-proxy=squid --disable-config  && make && sudo make install

```

For now you'll have to configure the .conf files yourself of course.
But at least, you'll be able to use the GUI to start/stop the filtering and open the .conf files.
Setting ports will probably not work correctly since it was made for tinyproxy.conf.

Please let me know how it works and also post your squid.conf, so I can adapt the install process for it (if you want to have a go at it yourself, look at WCCDIR/scripts/install.sh). ;)
If it works, I'll make a quick release of it.

[/LIST]

____________________________________

The rest of this post should now hopefully be unnecessary. :)

If you want to set up such a system manually without the GUI, here's a very helpful guide which also explains how it works:
[http://www.pilpi.net/journal/item-985.php](http://www.pilpi.net/journal/item-985.php)

=======================================
06/09/2008: UPDATE
I started uploading my code to launchpad for version control (&bug reports+ distribution):
[https://launchpad.net/webcontentcontrol](https://launchpad.net/webcontentcontrol)

I also joined the [GChildCare]("https://launchpad.net/gchildcare") project and plan to help it. So this is only a project to get a working GUI quickly up and running.

Until this is the case, please follow the instructions below.
=======================================

This "Howto" is an updated version of this one:
[http://ubuntuforums.org/showthread.php?t=226298](http://ubuntuforums.org/showthread.php?t=226298)

[B]Downloads are at the bottom of this post.
Note: WebContentControl.tar.gz is meant for developers and contains the source code of a new GUI I'm working on.[/B]

The original GUI was made by nanomad. I just made a few changes so that it should work "out of the box".
I created a new thread because nanomad stopped updating the other one.
If you still encounter problems, please tell me.

> Here is a simple (but powerful) install script for a parental control feature
It is based on tinyproxy + firehol + dansguardian.

Download the attached archive, extract it and run the script (2x click or from a terminal) (There are a couple of hidden files and folder too in the archive)

It will d/l, install and configure all you need + install a GUI created by me to configure everything (it is located under System --> Administration)

Note:
Another parental control GUI is available from Ubuntu ME here:
[http://www.ubuntume.com/webstrict](http://www.ubuntume.com/webstrict)

However, it is browser dependent, meaning that it will only work with properly configured browsers. In other words, it can easily be bypassed by using another browser or changing the browser config if it isn't locked.
An easy way to fix this is installing firehol. However, it is then also necessary to configure it correctly...

If I have time, I might try using their nice GUI with the browser-independent system from the one given here. ;)

_**For Hardy and later versions:**_
gambas-runtime has been replaced by gambas2-runtime, so until the GUI is made compatible with the new version, you may download&install the old gambas-runtime here:
[http://packages.ubuntu.com/gutsy/gambas-runtime](http://packages.ubuntu.com/gutsy/gambas-runtime)

_**Troubleshooting: If you are having problems:**_
1)Please post the console output of the installation process (just rerun the installation and copy/paste the output before closing the terminal window)
An easier way to do this (until I add automatic log creation ;) ):
For installation problems:
```
./.setup 1>install.log 2>&1
```
For uninstallation problems:
```
./.remove 1>uninstall.log 2>&1
```

2)If the GUI won't launch: post the output of the following command:
```
/usr/local/apps/parental-control/ubuntu_parental_control_gui
```

---

### Post by WhiteJedi on 2008-07-23
Thanks for the information very useful, now I have a ?  do I need to install the script on every User Profile?

thanks

WJ:confused:

---

### Post by KIAaze on 2008-07-23
No, you shouldn't have to. I have not yet tested it, but it should work for all users.

The programs (tinyproxy, dansguardian, firehol, gambas) get installed the standard way from the repositories, so they are certainly available for all users.
The GUI gets installed for all users too (/usr/local/bin/ + /usr/local/apps/parental-control).

The only potential problem might be the configuration files, but it seems they are user independant.

__________
Speaking of configuration files, I just noticed my package doesn't contain the custom dansguardian.conf made by nanomad...
Will correct that immediately.
edit: Seems there is no custom dansguardian.conf. It just uses the default one and comments out the "unconfigured" line. ^^'
__________

P.S:
Thanks to the admins for accepting this updated thread version. :)

---

### Post by zedstrange on 2008-08-15
Thanks but not working for me - am using 8.04 Edubuntu.
Installed the script,  and when run the main Application Parental Control Filter a terminal screen flashes up for a split second and closes. 

And Browsing is completly blocked.  

I also noticed during the installation process at the language select page, there was not an option to choose English.

Sorry cant give much more info, but if ya give me a clue i might?  :-)

p.s.  I set it up on another computer running plain old Ubuntu 8.04 and problem repeats exactly the same.

---

### Post by KIAaze on 2008-08-18
Sorry for the delay.
Yes, I know about the language selection problem.
It seems to be due to a limitation of the number of options in zenity (GUI system used in the installation script).

I'll try finishing a pyGTK version of that dialog for tomorrow. Don't have time right now.

For the moment, an easy solution is to change the language manually in the dansguardian.conf file.
Open the configuration file:
```
gksudo gedit /etc/dansguardian/dansguardian.conf
```
Look for a line like this:
```
# language to use from languagedir.
language = 'french'

```
and replace "french" or whatever there is to "ukenglish", then save and it should work.

As for the GUI problem, try running it from command-line and post the output here:
```
/usr/local/bin/parental-control-config
```

> And Browsing is completly blocked. 
This is most likely due to dansguardian not having started correctly. Since everything goes through dansguardian, if it hasn't started, the internet won't work at all unless firehol and tinyproxy are stopped.

Temporary solution: stop all 3 services:
```
sudo /etc/init.d/dansguardian stop
sudo /etc/init.d/tinyproxy stop
sudo /etc/init.d/firehol stop

```

Definitive solution:
My guess is that there is a configuration problem or that another program is using port 8080 (default port used by the parental control system).
I had the problem myself and here's the solution:
[http://ubuntuforums.org/showthread.php?t=884664](http://ubuntuforums.org/showthread.php?t=884664)

You can try solving the problem yourself by changing the port number.
If you can start tinyproxy and then dansguardian without any error messages, it will most likely work.
commands to start the different services manually:
```
sudo /etc/init.d/dansguardian start
sudo /etc/init.d/tinyproxy start
sudo /etc/init.d/firehol start

```

If this seems to complex to you, just post the contents of the following files and I'll see what I can do:
> /etc/dansguardian/dansguardian.conf
/etc/tinyproxy/tinyproxy.conf
/etc/firehol/firehol.conf


---

### Post by iGama on 2008-08-19
Thanks for the Update! 

Going to test it now :)

---

### Post by iGama on 2008-08-19
the gui wont work :( Using 8.04. 

When i run it, a terminal opens and closes right away, but browsing is working.

Any ideia?

---

### Post by KIAaze on 2008-08-19
Ok, I made some updates.
Please try version 3.1 from above.

Also note the added troubleshooting section. ;)

_Changes:_
-pyGTK language selection dialogue -> All available languages get displayed
-If dansguardian+tinyproxy+firehol don't start successfully after the installation, they will be automatically deactivated so that the internet isn't blocked. (oops forgot about what happens after reboot. Todo...)
-terminals remain open now until you close them (for installation, uninstallation and the GUI).
This should make debugging easier. Originally I wanted to have both terminal output + this output saved in a file, but it got a bit complicated so I settled for this solution.
Eventually, I'll just create install/uninstall logs, remove the terminal output and replace it with a progress bar.
-Some code simplification

---

### Post by iGama on 2008-08-20
Ok just tested v3.1 and already found the problem.

The problem is with Gambas.

$ /usr/local/apps/parental-control/ubuntu_parental_control_gui 
bash: /usr/local/apps/parental-control/ubuntu_parental_control_gui: /usr/bin/gbx: bad interpreter: No such file or directory

So i installed gambas2-runtime, but this installes gbx2. gambas-runtime is not available in Hardy.

If I do a ln -s gbx2 gbx , and run the gui again, i get:

$ /usr/local/apps/parental-control/ubuntu_parental_control_gui 
gbx2: too many project files.

Does this help?

---

### Post by KIAaze on 2008-08-20
Yes, that helps. :)
I never noticed that because I still have the old gambas-runtime installed (despite already running Intrepid ^^).

For the moment, you could try installing the old Gutsy version:
[http://packages.ubuntu.com/gutsy/gambas-runtime](http://packages.ubuntu.com/gutsy/gambas-runtime)

I'll have to update the GUI to make it compatible with gambas2, but the main problem is that I don't have the source code!

I already contacted nanomad and mhancoc7 (the one who made a GUI for UbuntuCE's parental control) and hope one of them will answer me.
Another solution might be to use the Java webstrict GUI (of which I already have the source code :) ).

---

### Post by KIAaze on 2008-08-20
I managed to locate the source code of the UbuntuCE Parental Control GUI. :)
It also contains an interesting perl script which parses the DansGuardian log files and outputs them to HTML.

If you want you can try out the GUI here without having to install Ubuntu CE:
[http://linux.softpedia.com/get/Security/Parental-control-24501.shtml](http://linux.softpedia.com/get/Security/Parental-control-24501.shtml)
(the source code is in the .deb contained in the tar.gz ironically)

Unfortunately, it also uses the old gambas-runtime, so it won't work for Hardy and later versions! (unless you install the old Gutsy package)

I also discovered this: [https://launchpad.net/gchildcare](https://launchpad.net/gchildcare)
However, it doesn't have any code or downloads yet.

---

### Post by forger on 2008-08-20
I use [opendns]("http://www.opendns.com") :)
You just switch the DNS nameservers of your router/modem to theirs, and that's it!
If you head to [http://welcome.opendns.com](http://welcome.opendns.com) it checks if you are connected properly to their nameservers.

You can then register (free) and head to [https://www.opendns.com/dashboard/](https://www.opendns.com/dashboard/) to manage your preferences.

I've attached a small screenshot of blocking content categories, it's pretty straight-forward and pain-free if you ask me.

---

### Post by KIAaze on 2008-08-20
Interesting. Adding it to initial post.

But I suppose it doesn't do weighted phrase filtering (based on words found on the page, not its DNS). Or does it analyze pages before letting them through?

And it could probably be bypassed by entering an IP address instead of a URL. Of course, getting an IP without having access to another DNS is hard... ^^

But most importantly, DansGuardian allows me to set up different configurations for different times (and users). ;)
This isn't implemented in the GUI yet, but it's possible. I already do it manually with /etc/rc.local and crontab.
And it keeps logs too, altough I don't need them. Others might like that feature.

---

### Post by forger on 2008-08-20
I think it's IP/domain based blacklisting
It does block IP addresses too, it redirected me to [http://phish.opendns.com/?url=208.69.34.133](http://phish.opendns.com/?url=208.69.34.133) when I tried [http://208.69.34.133](http://208.69.34.133) or [http://internetbadguys.com](http://internetbadguys.com) (opendns test site, it's safe to visit)

To set up a local dns server:
[http://www.howtoforge.com/installing-an-ubuntu8.04-dns-server-with-bind](http://www.howtoforge.com/installing-an-ubuntu8.04-dns-server-with-bind)
(never tried though)

---

### Post by lime4x4 on 2008-08-21
here is the error i'm getting when trying to start the gui. running hardy 64 bit here

syntax error in project file
cann't preload libraries: success
sixeof(class) =256 !
gbx: swapping archive
error: #1 out of memory
bash line 3: 16688 segmentation fault     ./ubuntu_parental_control_gui

---

### Post by KIAaze on 2008-08-26
I already adapted the code of the GUI for Gambas2, but haven't made a working package yet, since the UbuntuCE GUI works a bit differently actually.
I already reworked the GUI a lot, but it isn't functional yet.

However, if you wish to work on it or just check it out, you can download WebContentControl.tar.gz in the initial post.
Improvement ideas and/or help are welcome.

@lime4x4:
Except a working solution in the next few days. ;)
Does the filtering work at least?
If it does, you can easily modify the settings by opening the files in /etc/dansguardian/dansguardian.conf and /etc/dansguardian/lists.
They are heavily commented and the GUI currently only opens them in gedit anyway, so it doesn't make a big difference.
You can start and stop the parental control by using the provided start.sh and stop.sh scripts in the tarball. (don't forget to display hidden files)

---

### Post by KIAaze on 2008-09-11
Good news everyone:

1) A few days ago, I created a project on Launchpad called "WebContentControl" in order to have version control and make distribution easier.
And today, I made the first functional release!
You can get it here: [https://launchpad.net/webcontentcontrol](https://launchpad.net/webcontentcontrol)

Feedback is very welcome. (and help too of course)
Translation service should be available soon. If you want you can already start translating through Gambas.

_How to install it:_
```
sudo apt-get install gambas2-runtime gambas2-runtime gambas2-gb-qt gambas2-gb-qt gambas2-gb-form gambas2-gb-form gambas2-gb-form-dialog gambas2-gb-form-dialog gambas2-gb-qt-kde gambas2-gb-qt-kde gambas2-gb-qt-kde-html gambas2-gb-qt-kde-html
sudo apt-get install dansguardian tinyproxy firehol

```
Then download the latest version on [https://launchpad.net/webcontentcontrol/+download](https://launchpad.net/webcontentcontrol/+download) and:
```
tar -xzvf webcontentcontrol-1.0.tar.gz
cd webcontentcontrol-1.0
./configure && make && sudo make install

```

The shortcut should be created in Applications->System tools.
If it isn't, the command-line to launch it is:
```
/usr/bin/webcontentcontrol
```

_How to uninstall it:_
```
sudo make uninstall
```

2)I also joined the [GChildCare project]("https://launchpad.net/gchildcare"). Actually I created this other project because the project leader didn't think it would be a good idea to upload the code there, even if it's just to get a working GUI temporarily.
So I'll be working on that too eventually, once the WebContentControl GUI is done.

---

### Post by KIAaze on 2008-11-04
I fixed the install process. :)
You can get the latest version (v1.0.5) here:
[https://launchpad.net/webcontentcontrol/+download](https://launchpad.net/webcontentcontrol/+download)

Or did it work for others previously? Because I never got any feedback! :(
So, if anybody uses it, please send me feedback!

---

### Post by iwm on 2008-11-04
I tried to install the version 1.0.5 in my hardy... i've had to do a couple of additional step in order to install it.
1.
apt-get install gambas2-dev
2.
sudo cp webcontentcontrol-1.0.5.gambas /usr/share/webcontentcontrol/webcontentcontro.gambas

After those commands i've launched the script /usr/bin/webcontentcontrol but i get an error:
FMain.?.0: #6: Type mismatch: wanted Integer, got String instead

What can i do now?
Thank you.

---

### Post by High Roller on 2008-11-05
> **iwm said:**
> I tried to install the version 1.0.5 in my hardy... i've had to do a couple of additional step in order to install it.
1.
apt-get install gambas2-dev
2.
sudo cp webcontentcontrol-1.0.5.gambas /usr/share/webcontentcontrol/webcontentcontro.gambas

After those commands i've launched the script /usr/bin/webcontentcontrol but i get an error:
FMain.?.0: #6: Type mismatch: wanted Integer, got String instead

What can i do now?
Thank you.

Same problem here.

---

### Post by KIAaze on 2008-11-06
Thanks for the feedback.

I think I fixed the problem. (didn't notice it because I didn't remove everything from an older install)

I still have a few tests to do and then I'll make a new release.
In the meanwhile, you can try the latest branch like this:
```
bzr branch lp:webcontentcontrol
```

---

### Post by KIAaze on 2008-11-07
v1.06 released: [https://launchpad.net/webcontentcontrol/trunk/1.0.6](https://launchpad.net/webcontentcontrol/trunk/1.0.6)
Debian package should come soon.

---

### Post by DrumBoyG on 2008-11-08
I'm going to intall Kubuntu for the first time and am glad to see some type of web content filtering done.  I'm a user of Gentoo and the setup for this was insane.  Gentoo for a home family computer is too much work to maintain.  Anyway, will webcontentcontrol work w/ the new Ubuntu 8.10?  Will it work with Kubuntu 8.10?  I'm not a gnome fan and want to install the Kubuntu package!  Does webcontentcontrol have the ability to select what users you want to filter?  I wouldn't want me or my wife to be filtered.  
Thank you.  I look forward to your reply :-)

---

### Post by KIAaze on 2008-11-08
> Anyway, will webcontentcontrol work w/ the new Ubuntu 8.10?

It already does. At least for me. :)
> Will it work with Kubuntu 8.10?
It uses Gambas for the GUI, so I see no reason for it not to work.
> Does webcontentcontrol have the ability to select what users you want to filter?

Not yet.

---

### Post by DrumBoyG on 2008-11-08
Kewl.  Thanks so much for replying.  I look forward to doing a nice fresh install of Kubuntu 8.10 for the family and applying the webcontentcontrol.

Are all the packages listed in the package manager (add/remove programs) or do you install everything directly from the command line?

Ok, nothing yet to control what users can be filtered....is there a bypass password you can set/use when surfing or grabbing .iso packages etc..

How does this all efect Kubuntu or Ubuntu for that matter on getting updates etc??

Thanks again...

---

### Post by KIAaze on 2008-11-09
> **DrumBoyG said:**
> 
Are all the packages listed in the package manager (add/remove programs) or do you install everything directly from the command line?

I just released the first .deb package: [https://launchpad.net/webcontentcontrol/trunk/1.0.7](https://launchpad.net/webcontentcontrol/trunk/1.0.7)
So you should be able to install it by just downloading and double-clicking on it. :)

> **DrumBoyG said:**
> 
Ok, nothing yet to control what users can be filtered....is there a bypass password you can set/use when surfing or grabbing .iso packages etc..

I answered a bit quickly last time.
The current GUI doesn't allow "easy" user-specific configuration yet, but you should be able to set up user-specific filtering by editing the dansguardian configuration files (which can be done through the GUI).

As for a password: it currently requires the user's password just like "sudo" and changes can only be made if that user also has root permissions.
So an easy solution is to either not give "protected persons" the password or create an account for them without root permissions.

Blocking downloads (like .iso files) can also be done in dansguardian by editing the following files:
/etc/dansguardian/lists/bannedextensionlist
/etc/dansguardian/lists/bannedmimetypelist

Please refer to the DansGuardian website for more details: [http://dansguardian.org/](http://dansguardian.org/)

Another site I can recommend for blacklists is: [http://urlblacklist.com/](http://urlblacklist.com/)

> **DrumBoyG said:**
> 
How does this all efect Kubuntu or Ubuntu for that matter on getting updates etc??

It shouldn't be a problem as long as there aren't any big updates for firehol, tinyproxy and dansguardian.
I always keep my system up-to-date, so if an update of those packages breaks webcontentcontrol, I'll try to fix it as soon as possible.
Current versions I'm using:
```
ii  firehol                   1.256-3  
ii  tinyproxy                 1.6.3-3
ii  dansguardian              2.9.9.7-2 

```

Note: I initially intended for webcontentcontrol to be a "temporary package" for those wanting a parental control GUI until the [GChildCare]("https://launchpad.net/gchildcare") project offers a working alternative. (Using gambas+bash allows fast development)

This means that advanced features like user-specific filtering are currently not my highest priority.
I want something that's easy to install and has a basic GUI to turn on/off.
I would like to know if my current package fills these conditions and would be happy to have some feedback about this.

---

### Post by KIAaze on 2008-11-09
v1.0.8 is out: [https://launchpad.net/webcontentcontrol/trunk/1.0.8](https://launchpad.net/webcontentcontrol/trunk/1.0.8)
There were some missing dependencies in the previous package.

edit:
@DrumBoyG
I made a mistake: The program might currently not work correctly if you don't have gksudo, gedit and bash installed.

While bash may not be a problem, gksudo and gedit will be since they aren't available on Kubuntu by default as far as I know.

Solution: Install gksu + gedit.

I'll quickly fix the .deb and will try adding use of kdesudo + kate if on KDE later.

---

### Post by Kaaiman on 2008-11-09
Is the Debian package also compatible with Ubuntu 8.10?
Would it also run flawlessly on Ubuntu 64-bit theoretically?

---

### Post by DrumBoyG on 2008-11-10
My goodness, what a rapid process I have started....LOL.  Thanks so much KIAaze for your hard work :-)
Ok, so that I'm not lost and to be sure I'm doing this right the first time....LOL..... I disregard the install instructions on the beginning of this thread w/ doing an apt-get all the gambas2 packages, dansguardian, tinyproxy and firehol.  And then make install of webcontentcontrol, right?  I can skip doing all that and just install gksu and gedit and then download webcontentcontrol_1.0.8-_i386.deb and not webcontentcontrol_1.08.tar.gz?  Double click the deb package and all the necessardy installs will install and be ready to go?
Will the deb package work w/ Kubuntu8.10 or do I need to use the tarball?

So, editing the dansguardian config file thru gui I can add what users to filter?  If not, at least be able to use sudu if that person has admin rights, to bypass it when a page is blocked?  (Which I wouldn't give my kids admin rights anyway so access to sudo would be an NO.  I don't think I'd give my wife sudo, either....LOL).  I read the group_config setup dansguardian and the only thing I don't understand or how to setup is identifing the username as it mentions since your install doesn't use squid.  What do I setup to pass the info to dansguardian and setup dansguardian to see it?

Also, as you keep coming out w/ updates, how do you apply those once you've already installed one of your previous packages?

Thanks again for everything.

---

### Post by KIAaze on 2008-11-10
**IMPORTANT:** I noticed a big problem with my last debian package: Some paths in the scripts were relative to my own filesystem.
Just fixed that with this new release:
[https://launchpad.net/webcontentcontrol/trunk/1.0.9](https://launchpad.net/webcontentcontrol/trunk/1.0.9)

> **Kaaiman said:**
> Is the Debian package also compatible with Ubuntu 8.10?

Yes.
> 
Would it also run flawlessly on Ubuntu 64-bit theoretically?
The debian package was built for 32-bit, but it may work on 64-bit. (I can't test it since I don't have access to a 64-bit machine)
But you should be able to build it for 64-bit using the .tar.gz package.
I would be glad if you could help me create 64-bit debian packages.
All you have to do is the following:
```

tar -xzvf webcontentcontrol-1.0.9.tar.gz
cd webcontentcontrol-1.0.9/
./testing/release.sh

```

It will ask for a password at the end to sign the packages, but you can just hit ctrl+C.
If you have a GPG signature, you can enter your password and sign them of course. :)
I'll be glad to upload your packages on launchpad. Or if you have a launchpad account, I can add you to the dev group and you'll be able to upload them yourself.

> **DrumBoyG said:**
> Ok, so that I'm not lost and to be sure I'm doing this right the first time....LOL..... I disregard the install instructions on the beginning of this thread w/ doing an apt-get all the gambas2 packages, dansguardian, tinyproxy and firehol.  And then make install of webcontentcontrol, right?  I can skip doing all that and just install gksu and gedit and then download webcontentcontrol_1.0.8-_i386.deb and not webcontentcontrol_1.08.tar.gz?  Double click the deb package and all the necessardy installs will install and be ready to go?
Yes, exactly. At least I hope. That's why I need testers. :)

> Will the deb package work w/ Kubuntu8.10 or do I need to use the tarball?
It will work, however, as I said, it currently uses gksudo and gedit (firefox and nautilus too in some rare cases).
They are not necessary to launch the GUI itself, but will be necessary as soon as you start pressing certain buttons.

I already added a Gnome/KDE switcher in the "advanced settings" tab of the GUI.
It will work for the buttons in the first tab and some others, but not all.

> 
So, editing the dansguardian config file thru gui I can add what users to filter? 
Yes, but I don't know how to do it yet myself. ^^
By default, it will filter everybody.

> 
If not, at least be able to use sudo if that person has admin rights, to bypass it when a page is blocked?
"Blocked-page-bypassing" doesn't work yet (and I hadn't even thought about implementing it).
Just turn off the webfilter if you want to access porn or whatever it is that's blocked.


> 
I read the group_config setup dansguardian and the only thing I don't understand or how to setup is identifing the username as it mentions since your install doesn't use squid.  What do I setup to pass the info to dansguardian and setup dansguardian to see it?

I don't know, I haven't tried it yet myself. Once I finished other important stuff like KDE compatibility, I'll have a look at it.

> 
Also, as you keep coming out w/ updates, how do you apply those once you've already installed one of your previous packages?

Theoretically, you could just install one over the other.
However, since it's still under heavy development, I recommend removing the previous package before installing a new one.
This is also better for testing purposes (install in a clean environment).
How to remove a .deb package:
```
sudo apt-get remove webcontentcontrol
```

---

### Post by DrumBoyG on 2008-11-11
Kewl....very kewl.  I will have to look into the whole group/user thing for Dansguardian.  It doesn't look that hard but getting it to see the username from the proxy will be the issue.  I've been looking at what I could w/ tinyproxy and haven't seen anything yet.
Once you get the KDE compatibility done than I won't have to install gksu or gedit at all then, right?
Hopefully, by weeks end, I'll finds some more answers and download and install your latest and let you know :-)
Thanks again.....

---

### Post by DrumBoyG on 2008-11-17
Hey KIAaze... I ended up doing an Ubuntu install afterall.  Kubuntu w/ KDE 4.1 sucked!  It's lacking so much personal configuration and 3.5 is so much better.  So, I installed your latest .deb package and want to report and ask question on what I found for you...
1. Suggestion, even though when making changes in the WebContentControl Program Window, sudo users get access via their password but a normal user can still open it and can see everything.  Maybe you could add gksu to the begginning of the command line on the Launch properties so that only sudo users can get into it.  Maybe even set it up so that you have to use sudo on the command line their too so it can't be executed there either.  All this would be extremely helpful and useful.
2. Once you open the WebContentControl Program Window it's constantly "flickering".  Almost like it's refreshing or something.
3. None of the File menu options across the top work except for view console.
4. Filter Settings Tab- Preset Configuration does what exactly?  Nothing is selected and does not appear to do anything.
5. Logs Tab- Error comes up stating "an error occured while loading file://localhost/var/log/dansguardian/html/index.htm"  Says file/folder doesn't exist.  Also, the buttons on the page do nothing when you click them.
6. Language Tab- Drop down list for Language is blank and you can't select one, there's nothing there.  If you click "Test Access Denied Page" an errors states file://localhost/etc/dansguardian/languages//template.htm can't find file/folder.  I'm assuming because of the double slashes after languages it's looking for what was selected in the language selection box, which doesn't work.  Also, is there a way to edit the html Access Denied Page since stuff like "you org name" and "-user" is not correct?
7. Advanced Settings Tab- does the "Open Main Config Files" suppose to open Firehol & Tinyproxy as well as the Dansguardian config file?  Only the Dansguardian one opens.
8. Websites Tab- is totally blank.  Nothing is listed and pressing any of the buttons does nothing.
9. Does standard iptables commands work in the firehol config?
10. Other than that, the filtering appears to be working well.  There was a few times entering the Web Content Control program window that it crashed but clicked on it again and opened.

Sorry so long but wanted to report to you my findings in hopes that it will help you w/ further developement.  Looking forward to your reply.

Thanks....

---

### Post by KIAaze on 2008-11-20
Ok, I don't have time right now to make a detailed answer to each point, but here's a short version:

Most of the things you mentioned aren't functional.
The only one that surprised me is the language setting. It was supposed to work.
The flickering is due to regular updates. The GUI checks the status of each service regularly and updates the GUI accordingly.
I'll try to fix all those things soon.

The HTML template pages can be changed manually.
They are in /etc/dansguardian/languages/<your_language>/template.html

> 9. Does standard iptables commands work in the firehol config?
Yes

> 10. Other than that, the filtering appears to be working well. There was a few times entering the Web Content Control program window that it crashed but clicked on it again and opened.
This is good news. :)

(mmh, I think it became a long version after all. ^^)

---

### Post by DrumBoyG on 2008-11-20
Wow, I noticed your time stamp on this reply..you tired...LOL.

I figured out how to add gksu to the command line on the application launcher for gnome.  I edited your entry for /usr/share/applications/webcontentcontrol.desktop and added gksu as a prefix to the command line entry (gksu /usr/bin/webcontentcontrol) so at least regualar users can't even open it.  However, I'm still trying to figure a way for it to tell you only admins can open it when it's executed on the command line.  Changing permissions causes some errors :-(

I'm not sure why the language isn't showing but am almost certain that's why the error comes up when trying to view the page.  There's probably something in your code that isn't quite right :-(

Logs tab is the other one....not sure if that's one of your finished items or not but that is an error too :-(  Seeing the log files would be a good thing to see in the gui if you get that going ;-)

Now, as far as iptables goes, I've messed w/ this a little in gentoo with a version of iptables, squid and dansgaurdian running there.  However, it's difficult to maintain especially the iptables part.  My point is, I'll have to check my notes and get back to you on this, but I might be able to offer a simple way of which users may or may not be filtered using iptables commands in firehol as long as the command structure is the same.  I'll test this as well.  It maybe helpful to be able to write something in your gui that will append this line in firehol a lot easier than using dansguardian's way of doing it using groups (which will only work if you have something in the background running that will grab the username in the headers of the html page/like identd or something).

8-)

---

### Post by KIAaze on 2008-11-20
I forgot to ask:
Why do you want to prevent regular users from accessing the GUI? :confused:
They can't deactivate the filtering without a password after all.
As for seeing the filter settings, it can be done without the GUI by looking into /etc/dansguardian.

I think it makes more sense to allow seeing settings without needing a password, just as it is done in most admin GUIs.
If you want to make changes, you hit the "Unlock" button.

It's also safer than running the whole GUI as root. (basic security rule: Use sudo/gksudo/kdesudo as little as possible.)

What I could do:
-Add an option to change the file permissions of the dansguardian config files of course, but I would have to make sure it doesn't prevent dansguardian from working correctly.
-Same thing for the log files (in /var/log/dansguardian) which show exactly for what reason a page was blocked/logged (you can log "banned sites" instead of blocking them).

---

### Post by DrumBoyG on 2008-11-21
Thanks for your reply.  I have an almost 15yo that is very curious about things computer.  He runs through all the menus and basically tries everything there that he can get into.  He's not smart enough to know where things are thru the command line...YET!  However, I think for me, having him look at logs thru the gui or any lists that prevent him from going anywhere won't give him any "site" ideas to try on someone else's computer somewhere else.  As far as making changes, I must be missing something because I don't have an "Unlock" button showing on my gui!  If I go to make a change, gksu prompts me for a password, like it should.
Hmmmm, I think in order for you to make an option to change permissions on the dansgaurdian stuff you'd have to make it owned by dansguardian.  I'm not sure by making that option would be something I would want you to waste your time on.  I think getting your other features going and fixing the log page error and language error would be more important :-)

As far as iptables in firhol goes, you could make a feature to add an iptables line in firehol to DENY access to the Internet completely to a specific user by adding: iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner --uid-owner <USERNAME> -j DENY.  Also, if you didn't want someone filtered than you could add a line similar to this:
iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner --uid-owner <USERNAME> -j ACCEPT.  I haven't tested this yet but this works using nat on my gentoo box!  By doing this, it will give you three options: 1) everyone is filtered. 2) everyone is filtered except a certain user or users.  3) everyone is filtered except a certain user or users AND deny a certain user access to the Internet completely.
I'll test these and get back to you with that but it could be a helpful feature for ya :-)

---

### Post by KIAaze on 2008-11-25
Sorry for the long delay.
Here's a new release finally:
[https://launchpad.net/webcontentcontrol/trunk/1.1.0](https://launchpad.net/webcontentcontrol/trunk/1.1.0)

Import/export and consequently predefined configs should be coming soon hopefully.

IMPORTANT: Remove previous version before installing this one.

---

### Post by DrumBoyG on 2008-11-26
Kewl, I'll check it out.  Did you determine the problem w/ selecting a language as well?
Also, I tested my settings regarding disabling access and bypassing access in firehol using iptables commands and my original thought did not work!  However, I do have settings I used on my gentoo box that I implemented into my Ubuntu box and they work great!  Instead of using -t filter it uses -t nat and uses some redirection.  I'm able to now control who gets filtered and who doesn't and who has access to the Interent and who doesn't!  If you are interested in the config for firehol, I'll share that w/ you.  Maybe that will help in your development :-)  Also, I had to change the username/group to dansguardian in all configs to make sure they all work and play nice w/ each other.  root root OR root proxy along w/ dansguardian don't play well w/ each other.
I'll try your new install and get back to you.  Happy Turkey Day!

---

### Post by KIAaze on 2008-11-26
I'm focusing on the GUI now.
The current iptables setting I set up through FireHol work well enough (except it doesn't work sometimes through wifi, but this can be fixed by locking the firefox proxy settings or restarting FireHol).

New release again: [https://launchpad.net/webcontentcontrol/trunk/1.1.1](https://launchpad.net/webcontentcontrol/trunk/1.1.1)

> I'm able to now control who gets filtered and who doesn't and who has access to the Interent and who doesn't! If you are interested in the config for firehol, I'll share that w/ you
Yes I am. :)
Just post it here.

---

### Post by DrumBoyG on 2008-11-26
Ok, that's fine.  I just wanted to help w/ some insight, tis all.  I will gladly share the iptables in firehol w/ you.  I'm not sure how you'd it but it could be used in your gui as access controls.  I'm at work right now but will post it here when I get a chance.  

Also, I forgot to mention, I can't remember which config it is but it might be the dansguardian one, if not, the tinyproxy one, there is a left over IP left over in the config file.  It lists the loopback address then on the next line after it lists 192.168.0.1, I believe.  I ended up commenting that out.

I'll check out your latest.  I am still curious as to if they language selection was fixed.  Did you figure that one out?

Thanks again.  Great Job!  Take care.

---

### Post by KIAaze on 2008-11-26
Yes, I think I fixed the language bug. Forgot to mention that.
At least it works for me.

I just noticed another problem: If you get an "There was an error" message while trying to remove the package, just do the following:
```
sudo rm /var/lock/firehol
```

It seems the FireHol service doesn't get stopped correctly sometimes.
I haven't been able to figure out when exactly this happens.

edit:
Huh, v1.1.2 released. Just make sure to look for the latest here: [https://launchpad.net/webcontentcontrol](https://launchpad.net/webcontentcontrol)
In case I forgot something else... "Release early, release often" is what they say. ^^'

---

### Post by DrumBoyG on 2008-11-26
Ok, glad you found that.  Thanks.  I'll try your latest install tonight and will get you my firehol config.  Hmmmmm, how do you attach a file to this thread?  I might have to copy/paste.....LOL....

---

### Post by DrumBoyG on 2008-11-26
Well, it would appear there is an issue w/ uninstalling the .deb package.  I've listed the error below.  What needs to be done in order to do a manual remove of everything?

ERROR when doing sudo apt-get remove webcontentcontrol

Removing webcontentcontrol ...
Unconfiguring dansguardian+firehol+tinyproxy
FireHol is stopped
TinyProxy is stopped
DansGuardian is stopped
 * Stopping Firewall firehol                                                             [ OK ] 
Stopping tinyproxy: tinyproxy.
 * Stopping DansGuardian dansguardian                                                    [ OK ] 
No log file exists.  Is Dan's Guardian even running?
 No such file or directory 
dpkg: error processing webcontentcontrol (--remove):
 subprocess pre-removal script returned error exit status 2
Errors were encountered while processing:
 webcontentcontrol
E: Sub-process /usr/bin/dpkg returned an error code (1)

Ok, I managed to remove all the packages one by one and then webcontentcontrol last and they all removed.  Then I deleted all the remaining directories.  BUT, when I went to to install your latest .deb package it crashed with this error:
It complained there was no dansguardian.conf file AND
/etc/init.d/tinyproxy missing LSB style header AND
tinyproxy wouldn't start up and said config was missing AND
Processing triggers for libc6, ldconfig deferred processing now taking place AND
Errors were encountered while processing tinyproxy AND
gdebi-gtk:  Fatal IO error 9 (Bad file descriptor) on X server:0.0.  THEN SHE DIED!
Now I've got a mess :-(

Any ideas???

---

### Post by KIAaze on 2008-11-27
Mmh, what the hell did you do? O.o

> Then I deleted all the remaining directories. 
Can you tell me exactly which directories you deleted?

If you still have the complete output from the console, please post it.
(you can run "gdebi" instead of "gdebi-gtk" to install from a terminal: sudo gdebi ./webcontentcontrol.deb)

Please post the output of:
```
dpkg -l firehol tinyproxy dansguardian webcontentcontrol
```
Post the output of (or attach the files):
```
cat /etc/firehol/firehol.conf
```
```
cat /etc/tinyproxy/tinyproxy.conf
```
```
cat /etc/dansguardian/dansguardian.conf
```
```
sudo cat /var/log/dpkg.log
```

edit:
Actually, the most important one: post the output of:
```
sudo gdebi webcontentcontrol_1.1.2-1_i386.deb
```

---

### Post by notbitmonk on 2008-11-27
KIAaze, I would like to help in translating the GUI to Spanish.  How do we go about it?  Do you use .po files?  I have a 9 year old that is starting to use computers and was looking for an an application like this for a while.

---

### Post by DrumBoyG on 2008-11-27
What I did was when I noticed all the files that webcontentcontrol was going to remove when removing it, I used that list of files for each package name and removed each one, one by one by using apt-get remove <package.name>.  It was successful in doing that for each package.  Then when they were all removed, I did apt-get remove webcontentcontrol and that finally successfuly removed.  For some reason, just doing apt-get remove webcontentcontrol from the get go, did not work and resulted in those errors I posted.  Then when I said I deleted the remaining directories and fiels, I manually removed /etc/dansguardian, /etc/firehol, /etc/tinyproxy because they were left over.  I even removed the init scripts from /etc/init.d because they were still left over.  I then did and apt-get remove <package.name> again for each package to be sure they removed and they did.  I never did have to sudo rm /var/lock/firehol.  The file didn't exist.

After I did all that, I double-clicked your newest .deb package then got the install failure like I posted.  It's almost like your latest package didn't come w/ any configs or something.  Weird!  Then I went through AGAIN to remove each package that just installed from that failed attempt one by one again until everything was gone AGAIN.  It still doesn't install.

I then was going to install each package, dansguardian, tinyproxy and firehol individually but none of them list in the Add/Remove package manager when doing a search!  Even after opening up software sources to allow more packages into the synaptic mangager.  Looks like Ubuntu don't have an actuall listing for those packages there.  I didn't go any further after that.  

This is a result of doing dpkg -l firehol tinyproxy dansguardian webcontentcontrol:
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
rc  dansguardian   2.9.9.7-2      Web content filtering
rc  firehol        1.256-3        An easy to use but powerful iptables statefu
rc  tinyproxy      1.6.3-3        A lightweight, non-caching, optionally anony
rc  webcontentcont 1.0.9-1        Parental Control GUI

As far as catting the configs, there are none because I deleted those originally manually after doing the uninstalls in order to make thing clean.  I don't have the output in the console anymore.  I pretty much typed out what I showed you that looked bad originally.

Doing sudo cat /var/log/dpkg.log is so ungodly long I couldn't post it here.  If I could output to a file and attach it, I would but I don't see that option on these forums to do that.

sudo gdebi webcontentcontrol_1.1.2-1_i386.deb output died(crashed) here:
Setting up gambas2-gb-qt-kde (2.7-1) ...
Setting up gambas2-gb-qt-kde-html (2.7-1) ...
Setting up tinyproxy (1.6.3-3) ...
cp: cannot stat `/usr/share/doc/tinyproxy/tinyproxy.conf.dist': No such file or directory

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 clamav-freshclam
 clamav
 dansguardian
 firehol
Traceback (most recent call last):
  File "/usr/bin/gdebi", line 111, in <module>
    debi.install()
  File "/usr/lib/python2.5/site-packages/GDebi/GDebiCli.py", line 117, in install
    res = self._cache.commit(fprogress,iprogress)
  File "/usr/lib/python2.5/site-packages/apt/cache.py", line 226, in commit
    res = self.installArchives(pm, installProgress)
  File "/usr/lib/python2.5/site-packages/apt/cache.py", line 201, in installArchives
    res = installProgress.run(pm)
  File "/usr/lib/python2.5/site-packages/apt/progress.py", line 216, in run
    res = pm.DoInstall(self.writefd)
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)
Traceback (most recent call last):
  File "/usr/bin/gdebi", line 111, in <module>
    debi.install()
  File "/usr/lib/python2.5/site-packages/GDebi/GDebiCli.py", line 117, in install
    res = self._cache.commit(fprogress,iprogress)
  File "/usr/lib/python2.5/site-packages/apt/cache.py", line 230, in commit
    raise SystemError, "installArchives() failed"
SystemError: installArchives() failed

Now how do I remove everything up to that point before it failed?  Manually one by one again?

---

### Post by KIAaze on 2008-11-27
> **notbitmonk said:**
> KIAaze, I would like to help in translating the GUI to Spanish.  How do we go about it?  Do you use .po files?  I have a 9 year old that is starting to use computers and was looking for an an application like this for a while.
I already have some .pot files which have been generated by gambas in "webcontentcontrol_GUI/.lang".
You can either get them from the tarball or from here:
[http://bazaar.launchpad.net/~zohn-joidberg/webcontentcontrol/main/files/203?file_id=lang-20081105221636-swgr73w71sdnxvrp-2](http://bazaar.launchpad.net/~zohn-joidberg/webcontentcontrol/main/files/203?file_id=lang-20081105221636-swgr73w71sdnxvrp-2)

If you want to start translating right away, the most important one is FMain.pot (or .pot which seems to include FMain.pot???). The others don't even appear in the GUI yet.
As for the text from the scripts, I don't know how to make the strings in there translatable yet (Is it necessary?).

However:
1)Not all strings from the GUI appear in the .pot files yet, because some are inside the code and I have to modify it a bit for them to get into the .pot
2)The GUI isn't completely finished
3).po files currently don't get installed.
4)I haven't put the .pot into the launchpad translation system yet.

So, please wait a bit. I'll contact you once all is ready for translation. ;)

> **DrumBoyG said:**
> 
Now how do I remove everything up to that point before it failed?  Manually one by one again?

It looks like you still have some config files remaining from webcontentcontrol v1.0.9, as well as from the other programs.

Please use "**sudo apt-get install --purge**" to remove programs completely next time instead of manually deleting files. ;)

```
sudo apt-get install --purge firehol tinyproxy dansguardian webcontentcontrol

```

Additionally, you should do the following (or remove it if you want):
```
sudo mv /usr/share/webcontentcontrol ~
```

Otherwise, the only thing I can say is that the problem seems to be that **tinyproxy can't get installed**.
Try to install tinyproxy only first to see if it works.

And to attach files, just click on the "manage attachments" button.
It's just under the reply box in "Additional Options ".

**Thank you for taking the time to test my program and going through all that trouble.**
I really appreciate that. I'll make sure to add you in the "about" box once it's implemented. :KS

---

### Post by notbitmonk on 2008-11-28
I'll wait till you tell me everything is ready.  FYI, in the Gnome-es translation team we send the translated package to the coordinator.  If it will be different here, let me know in your message.

---

### Post by DrumBoyG on 2008-11-28
Ha ha ha, you crack me up.  I'm not sure how much of help I've been but thanks.

I've attached the dpkg.log filed greped from the time I installed webcontentcontrol to late when trying to uninstall and uninstall and reinstall and uninstall etc...LOL.  It's in .gz format.

sudo apt-get install --purge firehol tinyproxy dansguardian webcontentcontrol
revealed the following (it looks like it wants to add progs and not remove them):
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package webcontentcontrol is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package webcontentcontrol has no installation candidate

Then I removed webcontentcontrol from the list and this resulted:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  wine-gecko ttf-liberation winbind
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  aggregate clamav clamav-base clamav-freshclam libclamav5
Suggested packages:
  unrar lha clamav-docs squid
The following NEW packages will be installed:
  aggregate clamav clamav-base clamav-freshclam dansguardian firehol
  libclamav5 tinyproxy
0 upgraded, 8 newly installed, 0 to remove and 32 not upgraded.
Need to get 0B/20.9MB of archives.
After this operation, 25.1MB of additional disk space will be used.

It looks like wine-gecko ttf-liberation winbind are still there.  However, notice the packages it wants to install plus what the suggest list reads.  I substituted install w/ remove and got this:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package firehol is not installed, so not removed
Package tinyproxy is not installed, so not removed
Package dansguardian is not installed, so not removed
The following packages were automatically installed and are no longer required:
  wine-gecko ttf-liberation winbind
Use 'apt-get autoremove' to remove them.

So, question is, since all this has messed up my wine stuff I had installed, does your package include wine and wine dependencies because something has drug that in and pulled it out during the uninstall process?  I noticed a font problem in the wine config window (making it unreadable) and wasn't sure if all this installing and uninstalling messed that up.

I did an sudo apt-get autoremove wine-gecko ttf-liberation winbind (which weren't any of the original packages installed w/ webcontentcontrol that I could see and it removed those packages.

There was no /usr/share/webcontentcontrol folder to mv or rm.  I used the find command to search any traces of webcontentcontrol and it found none.

How tinyproxy firehol and dansguardian aren't listed in the repositories of thee add/remove program in ubuntu?  Aren't those supported packages?

Also, I attached the firehol.conf that I was using (as promised) to control who has access to the Internet and who doesn't etc..  Hope this helps.  I'm sure it could be tweaked.....

And finally, sudo apt-get install tinyproxy resulted in this:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  tinyproxy
0 upgraded, 1 newly installed, 0 to remove and 37 not upgraded.
Need to get 0B/65.8kB of archives.
After this operation, 238kB of additional disk space will be used.
Selecting previously deselected package tinyproxy.
(Reading database ... 107362 files and directories currently installed.)
Unpacking tinyproxy (from .../tinyproxy_1.6.3-3_i386.deb) ...
Processing triggers for man-db ...
Setting up tinyproxy (1.6.3-3) ...
cp: cannot stat `/usr/share/doc/tinyproxy/tinyproxy.conf.dist': No such file or directory

I then did a sudo apt-get remove --purge tinyproxy and removed it again then did a sudo apt-get install tinyproxy and got a different error:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  tinyproxy
0 upgraded, 1 newly installed, 0 to remove and 37 not upgraded.
Need to get 0B/65.8kB of archives.
After this operation, 238kB of additional disk space will be used.
Selecting previously deselected package tinyproxy.
(Reading database ... 107358 files and directories currently installed.)
Unpacking tinyproxy (from .../tinyproxy_1.6.3-3_i386.deb) ...
Processing triggers for man-db ...
Setting up tinyproxy (1.6.3-3) ...
update-rc.d: warning: /etc/init.d/tinyproxy missing LSB style header
Starting tinyproxy: tinyproxy.

Looks like a mess, doesn't it....LOL?

So, what happened anyhow?  How come apt-get remove webcontentcontrol didn't work?  And what's going on w/ your current install?
I'm hoping I don't have to dump my whole system and start over.  Not that it's a big deal because I've been testing wine and a few other things before setting it up for the family.

Thanks.

---

### Post by KIAaze on 2008-11-29
> How tinyproxy firehol and dansguardian aren't listed in the repositories of thee add/remove program in ubuntu? Aren't those supported packages?
They should be there, so I think you really messed up your system, but I doubt it's because of my package.

Have you made sure to update your package list?:
```
sudo apt-get update
```
And that the official repositories are in /etc/apt/sources.list?

My program does not depend on Wine. Unless there's some very deep going dependency I'm unaware of (Can't check now. On Windows).

Thanks for the firehol.conf. I'll see what I can make of it.

---

### Post by DrumBoyG on 2008-11-30
Huh, not sure what the issue is.  This is a fresh install of Ubuntu and everything was fine til now.  Not sure why tinyproxy, dansguardian or firehol shows up in add/remove programs.  The package list is up-to-date.  It finds them when doing using apt-get but doesn't show up in add/remove programs.  Since I'm beta'ing this Ubuntu install, I'll probably dump it and reload it.  I'm also looking into maybe trying Xubuntu.  This computer isn't a fast machine; 933MHz w/ 384MB of RAM.  I'm wondering if the Ubuntu install is overloading the system.  Maybe Xubuntu will be less straining as an OS and actually give more resources for other apps to be used.  Will your app work w/ Xubuntu?

---

### Post by eric.duveau on 2008-11-30
> **KIAaze said:**
> **Sept 11, 2008: First functional release of "WebContentControl" on the Launchpad project page**
**Nov 9, 2008: First debian package released**

Get it here: [https://launchpad.net/webcontentcontrol](https://launchpad.net/webcontentcontrol)

Feedback is very welcome.
____________________________________

_How to install from source:_
```
sudo apt-get install gambas2-runtime gambas2-runtime gambas2-gb-qt gambas2-gb-qt gambas2-gb-form gambas2-gb-form gambas2-gb-form-dialog gambas2-gb-form-dialog gambas2-gb-qt-kde gambas2-gb-qt-kde gambas2-gb-qt-kde-html gambas2-gb-qt-kde-html
sudo apt-get install dansguardian tinyproxy firehol

```
Then download the latest version on [https://launchpad.net/webcontentcontrol/+download](https://launchpad.net/webcontentcontrol/+download) and:
```
tar -xzvf webcontentcontrol-1.0.tar.gz
cd webcontentcontrol-1.0
./configure && make && sudo make install

```

The shortcut should be created in Applications->System tools.
If it isn't, the command-line to launch it is:
```
/usr/bin/webcontentcontrol
```

_How to uninstall it:_
```
sudo make uninstall
```
____________________________________

_**List of filtering solutions/projects:**_
[LIST]
[*]WebContentControl: [https://launchpad.net/webcontentcontrol](https://launchpad.net/webcontentcontrol)
[*]Webstrict: [http://www.ubuntume.com/webstrict](http://www.ubuntume.com/webstrict) + [https://launchpad.net/webstrict](https://launchpad.net/webstrict)
[*]GChildCare (not yet available): [https://launchpad.net/gchildcare](https://launchpad.net/gchildcare)
[*]UbuntuCE's Parental control GUI: [http://linux.softpedia.com/get/Security/Parental-control-24501.shtml](http://linux.softpedia.com/get/Security/Parental-control-24501.shtml)
[*]Squid+Squidgard: 
[https://help.ubuntu.com/community/SquidGuard](https://help.ubuntu.com/community/SquidGuard) + [http://www.squidguard.org/](http://www.squidguard.org/)
[*]SmoothGuardian (by the creator of DansGuardian, commercial version with web-based easy to use interface): [http://smoothwall.net/products/smoothguardian2008/](http://smoothwall.net/products/smoothguardian2008/) + [http://dansguardian.org/?page=smoothwall](http://dansguardian.org/?page=smoothwall)
[*]OpenDNS (suggested by forger): [http://www.opendns.com/](http://www.opendns.com/)
[*]MintNanny: [http://www.linuxmint.com/blog/?p=350](http://www.linuxmint.com/blog/?p=350)
[*]MoBlock, an IP blocker: [http://moblock.berlios.de/](http://moblock.berlios.de/)
[*]TimeKpr, track and control account usage: [https://launchpad.net/timekpr](https://launchpad.net/timekpr)
[*]LogProtect (Windows only, but Free/Libre Software): [http://www.logprotect.fr/](http://www.logprotect.fr/)
[/LIST]
Kiosk specific (for internet cafes, etc):
[LIST]
[*]Kiosk: [http://kiosk.mozdev.org/](http://kiosk.mozdev.org/)
[*]Lock down KDE settings: [http://jriddell.org/programs/kiosk-article.html](http://jriddell.org/programs/kiosk-article.html)
[/LIST]

If you know others, please tell me so I can add them to the list.
____________________________________

The rest of this post should now hopefully be unnecessary. :)

If you want to set up such a system manually without the GUI, here's a very helpful guide which also explains how it works:
[http://www.pilpi.net/journal/item-985.php](http://www.pilpi.net/journal/item-985.php)

=======================================
06/09/2008: UPDATE
I started uploading my code to launchpad for version control (&bug reports+ distribution):
[https://launchpad.net/webcontentcontrol](https://launchpad.net/webcontentcontrol)

I also joined the [GChildCare]("https://launchpad.net/gchildcare") project and plan to help it. So this is only a project to get a working GUI quickly up and running.

Until this is the case, please follow the instructions below.
=======================================

This "Howto" is an updated version of this one:
[http://ubuntuforums.org/showthread.php?t=226298](http://ubuntuforums.org/showthread.php?t=226298)

[B]Downloads are at the bottom of this post.
Note: WebContentControl.tar.gz is meant for developers and contains the source code of a new GUI I'm working on.[/B]

The original GUI was made by nanomad. I just made a few changes so that it should work "out of the box".
I created a new thread because nanomad stopped updating the other one.
If you still encounter problems, please tell me.



Note:
Another parental control GUI is available from Ubuntu ME here:
[http://www.ubuntume.com/webstrict](http://www.ubuntume.com/webstrict)

However, it is browser dependent, meaning that it will only work with properly configured browsers. In other words, it can easily be bypassed by using another browser or changing the browser config if it isn't locked.
An easy way to fix this is installing firehol. However, it is then also necessary to configure it correctly...

If I have time, I might try using their nice GUI with the browser-independent system from the one given here. ;)

_**For Hardy and later versions:**_
gambas-runtime has been replaced by gambas2-runtime, so until the GUI is made compatible with the new version, you may download&install the old gambas-runtime here:
[http://packages.ubuntu.com/gutsy/gambas-runtime](http://packages.ubuntu.com/gutsy/gambas-runtime)

_**Troubleshooting: If you are having problems:**_
1)Please post the console output of the installation process (just rerun the installation and copy/paste the output before closing the terminal window)
An easier way to do this (until I add automatic log creation ;) ):
For installation problems:
```
./.setup 1>install.log 2>&1
```
For uninstallation problems:
```
./.remove 1>uninstall.log 2>&1
```

2)If the GUI won't launch: post the output of the following command:
```
/usr/local/apps/parental-control/ubuntu_parental_control_gui
```
3)If the internet doesn't work anymore or isn't filtered: Please post the contents of the following files:
```
/etc/dansguardian/dansguardian.conf
/etc/tinyproxy/tinyproxy.conf
/etc/firehol/firehol.conf

```
and also the output of this command:
```
sudo lsof -i :8080
```
4)If almost everything you google gets blocked: Just turn on Google safe mode again. ;)

God bless you.

There is also a plan to port K9 webprotection
[http://www.k9webprotection.com](http://www.k9webprotection.com)

Look at

[http://forums.bluecoat.com/viewtopic.php?f=13&t=3179&p=21080&hilit=linux#p21080](http://forums.bluecoat.com/viewtopic.php?f=13&t=3179&p=21080&hilit=linux#p21080)

---

### Post by jsmac8218 on 2008-12-04
> **KIAaze said:**
> Yes, I think I fixed the language bug. Forgot to mention that.
At least it works for me.

I just noticed another problem: If you get an "There was an error" message while trying to remove the package, just do the following:
```
sudo rm /var/lock/firehol
```

It seems the FireHol service doesn't get stopped correctly sometimes.
I haven't been able to figure out when exactly this happens.

edit:
Huh, v1.1.2 released. Just make sure to look for the latest here: [https://launchpad.net/webcontentcontrol](https://launchpad.net/webcontentcontrol)
In case I forgot something else... "Release early, release often" is what they say. ^^'

Hi, I am fresh out of the Windows world and trying to understand Linux. I am running Ubunutu 8.04 and want to install webcontentcontrol on my 14yr olds new dell Mini. when I went to launchpad there are two versions: xxx.tar.gz 1.1.2 (tarball) and xxxi386.deb 1.1.2 (Debian package). I'm not sure which one I need to run.

PS: This is truly amazing, you guys are awesome and I'm flabbergasted that you do all this work for free! I am looking forward to installing this before Christmas when I give this notepad to my daughter.

Thanks.

---

### Post by KIAaze on 2008-12-05
Use the .deb.
Please read this too:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

And it's not completely for free. I want feedback. :)

---

### Post by jsmac8218 on 2008-12-05
Excellent, thanks. The installingsoftware post was helpful too for future uses. I tried add/remove and it could not find the webcontentcontrol package. 

I searched in Synoptic and I think it found it and listed it in the left top most window, but it did not list it in the right window so i could not select it. 

So, I clicked on the package in launchpad.net and it saved it to my desktop, I then double clicked it and package installer unpacked it and gave me this status message:  Error: wrong architecture 'i386'.

I am running it on a Dell Mini 9 which uses the Intel Atom N270 processor. I am running it on Ubuntu 8.04.

---

### Post by KIAaze on 2008-12-08
double post

---

### Post by KIAaze on 2008-12-08
> **DrumBoyG said:**
> It finds them when doing using apt-get but doesn't show up in add/remove programs.

Use "Synaptic" instead of "add/remove programs".
"Add/remove programs" only shows the most popular programs apparently.
cf [https://answers.launchpad.net/ubuntu/+question/2550](https://answers.launchpad.net/ubuntu/+question/2550)


> **DrumBoyG said:**
> Will your app work w/ Xubuntu?
Yes it should.
You can now configure custom apps to use in the "advanced settings" tab if you don't want to install things like gedit, etc.

> **jsmac8218 said:**
> Excellent, thanks. The installingsoftware post was helpful too for future uses. I tried add/remove and it could not find the webcontentcontrol package.

That's because it isn't available through the [repositories]("http://en.wikipedia.org/wiki/Software_repository") yet.
Think of a repository as being some kind of big store.
Currently, my product "webcontentcontrol" hasn't made it into the big store yet. :)
(I haven't even submitted it to the repository managers.)

So for now, you'll have to get it from here: [https://launchpad.net/webcontentcontrol](https://launchpad.net/webcontentcontrol)
which is also better since it will be more up to date.

> So, I clicked on the package in launchpad.net and it saved it to my desktop, I then double clicked it and package installer unpacked it and gave me this status message:  Error: wrong architecture 'i386'.

I am running it on a Dell Mini 9 which uses the Intel Atom N270 processor. I am running it on Ubuntu 8.04.

Do you know whether you have the 32-bit or 64-bit version of Ubuntu installed?

To find out, run the following command:
```
uname -m
```
i386 or i686 means 32-bit
x86_64 or ia64 means 64-bit

If you have no idea what the command-line is: [http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)

I'll try to find a way to build 64-bit packages.
In the meanwhile, you may try installing from source using the .tar.gz.
cf the initial post for installation instructions.

---

### Post by jsmac8218 on 2008-12-08
Kiaze,

results from "uname -m" is
"i686 unknown"

I will try the tar.gz install and will feedback when done. Of course my daughter is off school today and this is a Christmas present, so I haveto do it stealthily for her not to see the PC.

---

### Post by KIAaze on 2008-12-09
v1.1.4 released: [https://launchpad.net/webcontentcontrol/trunk/1.1.4](https://launchpad.net/webcontentcontrol/trunk/1.1.4)

@jsmac8218:
That's strange. i386 packages should work on i686. (I even have i686)
And the fact that it outputs "i686 unknown" is also strange. It should be only "i686". Are you sure you used "uname -m" and not "uname -m -i"/"uname -m -p"?

Please let me know how the tar.gz worked for you.

---

### Post by jsmac8218 on 2008-12-09
Bad news. I tried running the first line of your .tar script and got an error: "E: Couldn't find package gambas2-runtime" so I started add/remove and selected Gambas2 package, and got an error: "Gambas2 cannot be installed on your computer type (lpia). Either the application requires special hardware features or the vendor decided to not support your computer type."

I am running a Dell Mini 9 with Atom processor. Dell installed Ubuntu 8.04, perhaps they have blocked it somehow or for some reason.

Keep in mind I have no idea what any gambas2 is for or why it would be blocked. I'm just following suggestions.

Thanks

---

### Post by jsmac8218 on 2008-12-09
> **KIAaze said:**
> v1.1.4 released: [https://launchpad.net/webcontentcontrol/trunk/1.1.4](https://launchpad.net/webcontentcontrol/trunk/1.1.4)

@jsmac8218:
That's strange. i386 packages should work on i686. (I even have i686)
And the fact that it outputs "i686 unknown" is also strange. It should be only "i686". Are you sure you used "uname -m" and not "uname -m -i"/"uname -m -p"?

Please let me know how the tar.gz worked for you.

Sorry! Fat fingers small keypad. I used uname -pm. uname -m came back as "i686" only.

:lolflag: my bad!

---

### Post by KIAaze on 2008-12-10
> **jsmac8218 said:**
> Bad news. I tried running the first line of your .tar script and got an error: "E: Couldn't find package gambas2-runtime" so I started add/remove and selected Gambas2 package, and got an error: "Gambas2 cannot be installed on your computer type (lpia). Either the application requires special hardware features or the vendor decided to not support your computer type."

I am running a Dell Mini 9 with Atom processor. Dell installed Ubuntu 8.04, perhaps they have blocked it somehow or for some reason.

Keep in mind I have no idea what any gambas2 is for or why it would be blocked. I'm just following suggestions.

Thanks

_**Problem:**_
Ok, after some reasearch I found this:
LPIA = Low Power on Intel Architecture
[http://lwn.net/Articles/247003/](http://lwn.net/Articles/247003/)
[http://forums.cnet.com/5208-7587-0.html;jsessionid=abc2dskKEioU24OlvPY1r?forumID=69&threadID=315292&messageID=2901413](http://forums.cnet.com/5208-7587-0.html;jsessionid=abc2dskKEioU24OlvPY1r?forumID=69&threadID=315292&messageID=2901413)

So it's not really an i386/686 architecture.

_**Here's how to install i386 packages anyway:**_
[http://ubuntuforums.org/archive/index.php/t-982260.html](http://ubuntuforums.org/archive/index.php/t-982260.html)

_**Related threads:**_
[http://ubuntuforums.org/showthread.php?t=979458](http://ubuntuforums.org/showthread.php?t=979458)

_**Other solutions:**_
1)Install ubuntu 8.10 (not sure, but it may allow you to use the official ubuntu repositories)
[http://www.ubuntumini.com/2008/10/installing-ubuntu-on-dell-inspiron-mini.html](http://www.ubuntumini.com/2008/10/installing-ubuntu-on-dell-inspiron-mini.html)

2)Add the official ubuntu repositories to sources.lst

3)Installing using the command-line gdebi appears to work:
> I think I ran into this same issue when trying to install skype and also managed to mess up gdebi.

Here is the whole thread [http://www.mydellmini.com/forum/*-de...ling-t433.html](http://www.mydellmini.com/forum/*-de...ling-t433.html) , but basically I just had to go to a terminal and install from there: gdebi skypeblahblah.deb and it worked! Skype is running just fine. I don't know if I deleted the "ability to graphically run gdebi from the gui" or just broke an association, but that's for another day.

Joe
[http://ubuntuforums.org/showthread.php?t=979458](http://ubuntuforums.org/showthread.php?t=979458)

4)Ignore the architecture:
```
sudo dpkg -i --force-architecture <package>.deb
```

5)Compile & install all necessary packages from source :/

_**Getting the packages:**_
You can get download the necessary .deb packages from the official repository here:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Use the search box at the bottom and then click on "all" or "i386" (also at the bottom) depending on what's available.
ex: gambas2: [http://packages.ubuntu.com/intrepid/gambas2](http://packages.ubuntu.com/intrepid/gambas2)

_**Required packages:**_
```
firehol
tinyproxy
dansguardian
gambas2-runtime
gambas2-gb-qt
gambas2-gb-form
gambas2-gb-form-dialog
gambas2-gb-qt-kde
gambas2-gb-qt-kde-html

```

---

### Post by jsmac8218 on 2008-12-11
OK, so I'm learning a whole lot about Linux but not quite enough. I think Dell must have doen something to restrict some functions and packages from loading.

I ran through the post about getting i386 packages and that did allow more progress, but I got the gambas2 missing error, so I tried adding a line to source.list include the source for gambas2 becuase Dell did not let that install from Synpotic or add/remove, but, when I inserted this line into source.list: 

deb [http://azores.linex.org/gambas-other/](http://azores.linex.org/gambas-other/) hardy main

and then run sudo apt-get update I get this line error at the end of the long script:

W: failed to fetch [http://azores.linex.org/gambas-other/dists/hardy/main/binary-lpia/Packages.gz](http://azores.linex.org/gambas-other/dists/hardy/main/binary-lpia/Packages.gz)  404 Not Found

I suspect becuase it is looking for lpia packages and Gambas2 only has an i386 package but I don't know how to force it to retrieve that one and need to modify something else.

I suppose I could copy the i386 packages and run them manually but I need that help line by line, I'm still unsure of how to run tar files.

PS: I am open to IMing if you would prefer. I certainly appreictae your help.

---

### Post by KIAaze on 2008-12-11
v1.1.5 released: [https://launchpad.net/webcontentcontrol/trunk/1.1.5](https://launchpad.net/webcontentcontrol/trunk/1.1.5)

@jsmac8218:
> 
I ran through the post about getting i386 packages and that did allow more progress, but I got the gambas2 missing error, so I tried adding a line to source.list include the source for gambas2 becuase Dell did not let that install from Synpotic or add/remove, but, when I inserted this line into source.list:

deb [http://azores.linex.org/gambas-other/](http://azores.linex.org/gambas-other/) hardy main

Where did you find this source?
Try this instead:
```
deb http://de.archive.ubuntu.com/ubuntu/ intrepid universe
```
Depending on where you are, you can (but don't have to) replace "ge" with "us","fr",etc.

The gambas2 package is for all architectures if you download it from here:
[http://packages.ubuntu.com/intrepid/gambas2](http://packages.ubuntu.com/intrepid/gambas2)
Try to download and install it.

You can contact me through jabber or IRC for IMing:
[email]KIAaze@jabber.org[/email]
[email]KIAaze@irc.freenode.net[/email]

If you never used jabber or IRC:
[http://tips.webdesign10.com/free-software/how-use-jabber](http://tips.webdesign10.com/free-software/how-use-jabber)
[https://help.ubuntu.com/community/InternetRelayChat](https://help.ubuntu.com/community/InternetRelayChat)

Note: If you choose IRC, you may also join the #ubuntu channel.
There will be a lot of people who can help you there since this your problem is not directly related to my program for the moment. (you could also post here: [http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326) )

---

### Post by jsmac8218 on 2008-12-12
Done! I took your advice and installed ubuntu 8.10 on my mini 9 using USB, it went without a hitch and installing webcontent was a breeze, no issues.

Thanks a million!

---

### Post by KIAaze on 2008-12-13
I started using PPA (Personal Package Archive) on Launchpad.
What this means is that you can now add:
```
deb http://ppa.launchpad.net/zohn-joidberg/ubuntu intrepid main
deb-src http://ppa.launchpad.net/zohn-joidberg/ubuntu intrepid main

```
to your software sources and install+upgrade through Synaptic. :)

It also means that I can now offer Debian packages for i386, amd64 and even LPIA! ;)

For direct download: [https://launchpad.net/~zohn-joidberg/+archive](https://launchpad.net/~zohn-joidberg/+archive)

---

### Post by ridgeland on 2008-12-14
Wow!  Thanks KIAaze!
I've been fussing with Dansguardian for a couple of days trying to get it set up.  I'm using Ubuntu 8.10
I went to Synaptic added your two lines of repos. Reload.  Quick Search for webcontent showed nothing.  Regular Search button found it.  Simple install and its set.
Thanks again.

---

### Post by Oihandi on 2008-12-18
KIAaze, thank you VERY much!

I have been looking for an application like WebContentControl for a long time. I have downoad the deb (Ubuntu, 8.10, Gnome), and all is running OK, without problems. Thaks again for tour efforts.

(Sorry for my limited english - from Spain)

---

### Post by jsmac8218 on 2008-12-22
I just realized that WebContentControl was blocking my access to my home network shared drives. When it is disabled I have access and when enabled I don't. I thought I had screwed something else up and totally reinstalled Ubuntu 8.10.

How do I allow access to any shared drive within my home LAN?

Thanks

---

### Post by KIAaze on 2008-12-26
Thanks for the feedback. Gracias para el feedback. :)

@jsmac8218: I think I answered your question here: [https://answers.launchpad.net/webcontentcontrol/+question/55187](https://answers.launchpad.net/webcontentcontrol/+question/55187) ;)

I'm planning a new release soon, but I first have to make some changes to the install process so that people can upgrade without the default settings being restored every time in case they already made changes.

I'll try to fix the shared drive issue too by adding more GUI configuration for FireHol.

P.S: As for the user specific configuration, it seems rather simple altough I haven't tried it yet myself:
[http://www.ubuntume.com/webstrict#i_want_different_configurations_for_different_user_accounts](http://www.ubuntume.com/webstrict#i_want_different_configurations_for_different_user_accounts)

---

### Post by KIAaze on 2009-01-03
==================================
New release: v1.2.0:
[https://launchpad.net/webcontentcontrol/+announcement/1731](https://launchpad.net/webcontentcontrol/+announcement/1731)
==================================

---

### Post by ellipsis21 on 2009-01-03
OK I posted earlier on a different (older?) thread and you redirected me here and now I'm completely lost hahaha... I tried the methods and I'm pretty sure I'm doing them wrong. I tried running the "source" method code, but it said it couldn't find gambas2-runtime... I really have no idea what I'm doing here so anything would help (: Thanks!


Ellipsis

EDIT: I read your posts on the previous page and tried adding the repos and installing in Synaptic but that was a no go either :/

---

### Post by KIAaze on 2009-01-03
What about the debian package?

To install from source, you need to install the dependencies first as indicated.

---

### Post by KIAaze on 2009-01-18
New release: [https://launchpad.net/webcontentcontrol/+announcement/1820](https://launchpad.net/webcontentcontrol/+announcement/1820)

> **ellipsis21 said:**
> OK I posted earlier on a different (older?) thread and you redirected me here and now I'm completely lost hahaha... I tried the methods and I'm pretty sure I'm doing them wrong. I tried running the "source" method code, but it said it couldn't find gambas2-runtime... I really have no idea what I'm doing here so anything would help (: Thanks!


Ellipsis

EDIT: I read your posts on the previous page and tried adding the repos and installing in Synaptic but that was a no go either :/

Is this still a problem?
Please make sure you have the "universe" repository enabled since gambas2-runtime is in there.

Go to System->Administration->Software sources and check the "universe" repository.
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by Toyota on 2009-01-22
Thanks a million, the Web Content Control gui is working! 

At last a working gui to take all the drudgery out of using Dansguardian.

---

### Post by fparri on 2009-02-07
Compliments for this very cool GUI. Is there a way to differentiate permits according to users?

I would like to have an open access to the web when connecting wuith my account whereas I'd like to block other accounts.

Thanks a lot in advance,
Fabio

---

### Post by KIAaze on 2009-02-07
Yes and no.
You can configure dansguardian manually to filter differently according to the user acoount by following those instructions for example:
[http://www.ubuntume.com/webstrict#i_want_different_configurations_for_different_user_accounts](http://www.ubuntume.com/webstrict#i_want_different_configurations_for_different_user_accounts)

But I haven't tried it out yet myself and haven't implemented it in the GUI yet.
It's on the TODO list. ;)

---

### Post by eric.duveau on 2009-02-07
Very nice gui indeed!

Do you think to include in near future release:

1) Remote accountability
2) Choice of adding a free DB like [http://www.shallalist.de/](http://www.shallalist.de/)
3) The creation of power users that can make some admin stuff like installing know softwares

---

### Post by fparri on 2009-02-09
That's very good news to hear ;)

Thanks a lot again for the good work ;)

> **KIAaze said:**
> Yes and no.
You can configure dansguardian manually to filter differently according to the user acoount by following those instructions for example:
[http://www.ubuntume.com/webstrict#i_want_different_configurations_for_different_user_accounts](http://www.ubuntume.com/webstrict#i_want_different_configurations_for_different_user_accounts)

But I haven't tried it out yet myself and haven't implemented it in the GUI yet.
It's on the TODO list. ;)

---

### Post by KIAaze on 2009-02-11
> **eric.duveau said:**
> Very nice gui indeed!

Do you think to include in near future release:

1) Remote accountability
2) Choice of adding a free DB like [http://www.shallalist.de/](http://www.shallalist.de/)
3) The creation of power users that can make some admin stuff like installing know softwares

1) Mmh, maybe... Could you give more details about how you would like it to be? An easy solution would probably automatic e-mailing of the dansguardian logs.
2) Thanks for the link. I didn't know about it. It's similar to [http://urlblacklist.com/](http://urlblacklist.com/) . Yes, I'll probably add that.
3) This is supposed to be controlled through "Users and Groups" in Ubuntu and similar GUIs in other distros. So, no.
However, I already started implementing special program group permissions which should allow forbidding access to a group of programs to certain users.

---

### Post by eric.duveau on 2009-02-11
> **KIAaze said:**
> 1) Mmh, maybe... Could you give more details about how you would like it to be? An easy solution would probably automatic e-mailing of the dansguardian logs.
yes, I think that this feature is coded in dansguardian itself. But a GUI is missing.


> **KIAaze said:**
> 
3) This is supposed to be controlled through "Users and Groups" in Ubuntu and similar GUIs in other distros. So, no.
However, I already started implementing special program group permissions which should allow forbidding access to a group of programs to certain users.

Maybe I was not clear enough. I am myself an adult and I do not want to loose my time on "bad" sites. So I would like to be "protected" and at the same time be able to use ubuntu as a regular user including be able to install/remove software without getting the root priviledge. 

What is difficult to implement is when you are able to remove software, you can remove protecting software!

---

### Post by KIAaze on 2009-02-11
> **eric.duveau said:**
> 
Maybe I was not clear enough. I am myself an adult and I do not want to loose my time on "bad" sites. So I would like to be "protected" and at the same time be able to use ubuntu as a regular user including be able to install/remove software without getting the root priviledge. 

What is difficult to implement is when you are able to remove software, you can remove protecting software!

cf: [http://bazaar.launchpad.net/~zohn-joidberg/webcontentcontrol/main/annotate/head%3A/README_selfcontrol.txt](http://bazaar.launchpad.net/~zohn-joidberg/webcontentcontrol/main/annotate/head%3A/README_selfcontrol.txt)

Stay tuned for new revisions. ;)

---

### Post by mnavasuk on 2009-02-12
Thanks KIAaze. I really look forward to news on this.
By the way, on the question posted on [https://blueprints.launchpad.net/webcontentcontrol/+spec/install-upgrade-removal-processes](https://blueprints.launchpad.net/webcontentcontrol/+spec/install-upgrade-removal-processes) (I looked into giving a response there, but couldn't find the answer to how on launchpad's faqs), I think option 1 is the best for the great majority.
With the half term starting tomorrow, I would have loved to have the parental control enabled. Oh well, keep the good work.

---

### Post by KIAaze on 2009-02-13
Just create a Launchpad account and then when you view the blueprint, just click on "Edit whiteboard" to add comments.
(It seems anyone can edit whiteboards, but I don't see any other way of commenting blueprints.)

I'll try to implement Solution 1 then as soon as I can.
Thanks for the feedback on this. You're the first one so far. :)

---

### Post by gruslo on 2009-02-15
Hi. I am new to ubuntu and tried your software. It's easy to install, but there are some problems: When Firehol is on, the content control works and blocks what is intended to block. But when Firehol is off, all sites are accepted. I wouldn't have a problem if there was not a LAN network: Firehol blocks my LAN and I can't access other computers. But without Firehol, the content control does not work. Is there anything I can do? I read [https://answers.launchpad.net/webcontentcontrol/+question/55187](https://answers.launchpad.net/webcontentcontrol/+question/55187) but was not helpful. So, there is no way to allow LAN access when Firehol is on??

BTW, [Gchildcare]("https://launchpad.net/gchildcare") is a very promising project! I wish a nice GUI like the [k9 web protection]("http://www1.k9webprotection.com/") one for Window$. This is really a missing software from Linux...

---

### Post by KIAaze on 2009-02-16
I'm pretty sure it's possible. I just don't know how yet.
And I don't have a LAN on which I can test it since I only have one laptop.

Still, it might be helpful if you could give me details on how your LAN is set up and what services you need access too.

I attached a picture explaining how things work.
The only difference is that WebContentControl uses Squid instead of Tinyproxy and that iptables is managed by FireHol.

The picture is taken from this howto:
[http://www.zephyrsoft.net/files/linux-filtering-monitoring-howto.pdf](http://www.zephyrsoft.net/files/linux-filtering-monitoring-howto.pdf)

---

### Post by arapozo on 2009-02-20
Can someone help me?
Dansguardian is not showing the username in the logfile.

---

### Post by KIAaze on 2009-02-20
> **arapozo said:**
> Can someone help me?
Dansguardian is not showing the username in the logfile.

You mean in /var/log/dansguardian/access.log ?
The GUI uses a perl script to create an HTML page from access.log.
I don't know if it supports username logging.

So first, check /var/log/dansguardian/access.log (open the logs with a text editor).

To log usernames, you'll probably also need to edit /etc/dansguardian/dansguardian.conf

Modify the following parts as follows:
```

...
# Logging Settings
#
# 0 = none  1 = just denied  2 = all text based  3 = all requests
loglevel = 2

# Log Exception Hits
# Log if an exception (user, ip, URL, phrase) is matched and so
# the page gets let through.  Can be useful for diagnosing
# why a site gets through the filter.
# 0 = never log exceptions
# 1 = log exceptions, but do not explicitly mark them as such
# 2 = always log & mark exceptions (default)
logexceptionhits = 2

...

# anonymize logs (blank out usernames & IPs)
anonymizelogs = off
...

```

Note: I am unable to test this at the moment, so I can't guarantee it'll work, but hopefully it will.

cf here for more info:
[http://contentfilter.futuragts.com/wiki/doku.php?id=general_troubleshooting_strategies&DokuWiki=965ce24132ab65d63c4ec10f8b869480](http://contentfilter.futuragts.com/wiki/doku.php?id=general_troubleshooting_strategies&DokuWiki=965ce24132ab65d63c4ec10f8b869480)

---

### Post by mrhealthpatriot on 2009-02-27
I use Foxfilter because it has a separate password. I can give the password to someone else for accountability purposes. I would want the same from any Internet Content Filter.

BTW, I currently use a Zyxel Zywall 2 Plus at home b/c it can send a report via email to an accountability person and it has its own password. Nothing is "perfect" but Dansguardian and the hardware box are close.

---

### Post by eric.duveau on 2009-02-27
> **mrhealthpatriot said:**
> I use Foxfilter because it has a separate password. I can give the password to someone else for accountability purposes. I would want the same from any Internet Content Filter.

BTW, I currently use a Zyxel Zywall 2 Plus at home b/c it can send a report via email to an accountability person and it has its own password. Nothing is "perfect" but Dansguardian and the hardware box are close.

I am trying do something similar to foxfilter with opendns.com:

[http://forums.opendns.com/comments.php?DiscussionID=2942&]("http://forums.opendns.com/comments.php?DiscussionID=2942&")

Beware It is still alpha :-)

---

### Post by KIAaze on 2009-02-27
That's interesting. I also thought of using openDNS. One of the biggest advantages is that it's lighter on the system and allows filtering multiple PCs with one system.
Does it work already? Are you unable to bypass it?

However, the advantage of having dansguardian locally installed is that you can easily increase the restrictions as necessary without being able to deactivate it. ;)
Time windows with different settings can also be configured using crontab.

As for Foxfilter, since it's Firefox specific, it can be easily bypassed by using another browser (and Konqueror is kind of mandatory for KDE users) or starting in safe mode.
If you know how to disable safe mode for firefox, please tell me.

---

### Post by eric.duveau on 2009-02-28
> **KIAaze said:**
> That's interesting. I also thought of using openDNS. One of the biggest advantages is that it's lighter on the system and allows filtering multiple PCs with one system.
Does it work already? Are you unable to bypass it?


So far it seems to work, but I did not try to challenge it.
I am still in the tuning phase.

---

### Post by shatterblast on 2009-03-03
First, thank you for the efforts into Web Content Control.  I am liking it very much so far.  I have a novice question in regards to setting up site / URL blocking.  Is there a functionality for covering a keyword in the URL?  

I have tried using asterisks (*), but that doesn't seem to cover it in the "banned site list" and the "banned url list".  I used inequality symbols ( < > ) just fine in the "banned phrase list", but that tends to block more sites than I personally care for.

Thanks for any insight.

---

### Post by KIAaze on 2009-03-04
Yes, it's possible to ban regular expressions and keywords in a URL.
Have a look at the file **/etc/dansguardian/lists/bannedregexpurllist**, as well as the Dansguardian wiki: [http://contentfilter.futuragts.com/wiki/doku.php?id=main_index](http://contentfilter.futuragts.com/wiki/doku.php?id=main_index)

The GUI currently only offers 12 buttons to access Dansguardian configuration files. That's because it's based on the GUI made for Ubuntu CE.
But there are a lot more files you can use:
```
[12][/etc/dansguardian/lists]$  ls
authplugins          bannedphraselist        bannedurllist      downloadmanagers        exceptioniplist         exceptionsitelist  greyurllist       logurllist     weightedphraselist
bannedextensionlist  bannedregexpheaderlist  blacklists         exceptionextensionlist  exceptionmimetypelist   exceptionurllist   headerregexplist  phraselists
bannediplist         bannedregexpurllist     contentregexplist  exceptionfilesitelist   exceptionphraselist     filtergroupslist   logregexpurllist  pics
bannedmimetypelist   bannedsitelist          contentscanners    exceptionfileurllist    exceptionregexpurllist  greysitelist       logsitelist       urlregexplist

```

Fixing that is on my TODO list as well. ;)
But maybe Didier Roche will have uploaded his new GChildCare GUI by then. :)

---

### Post by shatterblast on 2009-03-04
That worked successfully.  Thanks for the information.

---

### Post by roc1479 on 2009-03-13
Hi,

Anyway to edit the GUI to change TinyProxy to Squid?  I'd like to use squid with my setup instead of TinyProxy.  I've gotten it to work, but need to change the button to reflect the changes.  Also, does your gui work with xfce or kde?  I'm currently using gnome.  Please let me know.

Thanks,

---

### Post by KIAaze on 2009-03-13
Yes, it works with xfce, KDE, openbox, etc... It even works without a GUI. :)
I added a special tab to configure apps like the text editor, etc so people can use the apps of their desktop environment.

Now, as for using squid: yes and no.
If you have some experience with bash scripting, it should be relatively easy.
Here's a listing of the places where you'll have to replace "tinyproxy" with "squid":
```
[15][~]$  grep tinyproxy /usr/share/webcontentcontrol/scripts/*.sh
/usr/share/webcontentcontrol/scripts/activate_htmllogs.sh:TP=/etc/tinyproxy/tinyproxy.conf
/usr/share/webcontentcontrol/scripts/autosetports.sh:    gksudo /etc/init.d/tinyproxy start;
/usr/share/webcontentcontrol/scripts/autosetports.sh:    gksudo /etc/init.d/tinyproxy stop;
/usr/share/webcontentcontrol/scripts/autosetports_nogui.sh:    /etc/init.d/tinyproxy start;
/usr/share/webcontentcontrol/scripts/autosetports_nogui.sh:    /etc/init.d/tinyproxy stop;
/usr/share/webcontentcontrol/scripts/common_functions.sh:    pid_tp="`pidof tinyproxy | tr -d [:space:]`"
/usr/share/webcontentcontrol/scripts/common_functions.sh:    then gksudo /etc/init.d/tinyproxy start;
/usr/share/webcontentcontrol/scripts/common_functions.sh:    /etc/init.d/tinyproxy restart;
/usr/share/webcontentcontrol/scripts/common_functions.sh:    gksudo /etc/init.d/tinyproxy stop;
/usr/share/webcontentcontrol/scripts/common_functions.sh:    then /etc/init.d/tinyproxy start;
/usr/share/webcontentcontrol/scripts/common_functions.sh:    /etc/init.d/tinyproxy stop;
/usr/share/webcontentcontrol/scripts/file_paths.sh:TP=/usr/local/etc/tinyproxy/tinyproxy.conf
/usr/share/webcontentcontrol/scripts/file_paths.sh:TP_FILTER=/usr/local/etc/tinyproxy/filter
/usr/share/webcontentcontrol/scripts/get_filterport.sh:TP=/etc/tinyproxy/tinyproxy.conf
/usr/share/webcontentcontrol/scripts/get_language.sh:TP=/etc/tinyproxy/tinyproxy.conf
/usr/share/webcontentcontrol/scripts/get_proxyport.sh:TP=/etc/tinyproxy/tinyproxy.conf
/usr/share/webcontentcontrol/scripts/install.sh:/usr/share/webcontentcontrol/scripts/tinyproxy_setup.sh proxy proxy 3128
/usr/share/webcontentcontrol/scripts/reset.sh:cp -v /etc/tinyproxy/tinyproxy.conf .
/usr/share/webcontentcontrol/scripts/service_setup.sh:    if [ $SERVICE = 'tinyproxy' ]; then update-rc.d tinyproxy defaults ; fi
/usr/share/webcontentcontrol/scripts/set_ports.sh:TP=/etc/tinyproxy/tinyproxy.conf
/usr/share/webcontentcontrol/scripts/set_ports_nogui.sh:TP=/etc/tinyproxy/tinyproxy.conf
/usr/share/webcontentcontrol/scripts/stop2.sh:/etc/init.d/tinyproxy stop
/usr/share/webcontentcontrol/scripts/stop2.sh:killall tinyproxy
/usr/share/webcontentcontrol/scripts/totalcontrol_lock.sh:/usr/share/webcontentcontrol/scripts/service_setup.sh tinyproxy on
/usr/share/webcontentcontrol/scripts/totalcontrol_unlock.sh:/usr/share/webcontentcontrol/scripts/service_setup.sh tinyproxy off

```

I can't guarantee everything will work if you do that, but the proxy start/stop button should then work for squid at least.

I might add support for squid too eventually. But if you could help me implement it, I'll gladly accept your help. 
I'm aware that there's still a lot left to fix/improve, but I'm a bit busy with lots of other projects right now unfortunately and am already quite satisfied with how webcontentcontrol works.

---

### Post by roc1479 on 2009-03-17
KIAaze,

Thank you for your response.  I had gone through all the files, replacing tinyproxy with squid, so I was able to get the main button to work. However, the Tinyproxy button doesn't seem to work.  When I click it, it says that tinyproxy is either starting or stopping, depending on if the service was already running, but nothing happens.  The main shutoff button works perfectly.  I'll double check the files to see if I missed something though.

Anyway, your setup of tinyproxy is basically how you would have to setup squid.  All I had to do was append transparent to the port line.  I have mine setup in gateway mode because I wanted a way of editing the configs without the terminal, for ease of use.  It works, as I can change stuff in real time and apply it all from the gui.  I would like to add more options to the gui though, for editing more files.  There are a ton of files in dansguardian now, and I would like to be able to edit most of them through the gui.

The reason I asked about the desktop gui is because I want a setup that uses very little space, to optimize performance.  I noticed that gnome makes filtering a bit slower that a normal setup without the gui.  Speaking of which, you said that this setup can work without the gui?  But would you have to edit the conf files through the terminal?  

Rocky.

---

### Post by KIAaze on 2009-03-17
[v1.2.2 released!]("https://launchpad.net/webcontentcontrol/+announcement/2227")

> **roc1479 said:**
> 
The reason I asked about the desktop gui is because I want a setup that uses very little space, to optimize performance.  I noticed that gnome makes filtering a bit slower that a normal setup without the gui.  Speaking of which, you said that this setup can work without the gui?  But would you have to edit the conf files through the terminal?  

Yes, without the GUI, you'll have to edit the conf files in a terminal. However, there isn't any terminal/ncurses GUI (midnight commander style GUI).

About performance:
WCC is just a GUI frontend to configure firewall+proxy+dansguardian.
So when it isn't running it doesn't use up any processing power or RAM space.
Only the firewall+proxy+dansguardian daemons will be affecting the performances.

Note that tinyproxy is lighter than squid. ;)

> I have mine setup in gateway mode because I wanted a way of editing the configs without the terminal, for ease of use. It works, as I can change stuff in real time and apply it all from the gui.

Mmh, could you explain a bit more what the gateway mode is and how you can edit the squid config without the terminal?

> However, the Tinyproxy button doesn't seem to work. When I click it, it says that tinyproxy is either starting or stopping, depending on if the service was already running, but nothing happens.
You probably have to modify the gambas source files too:
```
webcontentcontrol_GUI/ExportOptions.form
webcontentcontrol_GUI/FMain.class

```
Download the .tar.gz (or check out the bzr repository), replace tinyproxy with squid in the above files and install from source.

**_edit: mmh, actually, I think you should be careful with the following, since this will likely also modify your squid.conf instead of tinyproxy.conf!!!_**

For your convenience:
```

tar -xzvf webcontentcontrol_1.2.2.orig.tar.gz
cd webcontentcontrol-1.2.2
find . -type f | xargs -n1 sed -i 's/tinyproxy/squid/g'
./configure && make && sudo make install

```
This should replace tinyproxy with squid everywhere! Haven't tested if the GUI still works after that. ^^

---

### Post by eric.duveau on 2009-03-19
> **KIAaze said:**
> That's interesting. I also thought of using openDNS. One of the biggest advantages is that it's lighter on the system and allows filtering multiple PCs with one system.
Does it work already? Are you unable to bypass it?

However, the advantage of having dansguardian locally installed is that you can easily increase the restrictions as necessary without being able to deactivate it. ;)
Time windows with different settings can also be configured using crontab.

As for Foxfilter, since it's Firefox specific, it can be easily bypassed by using another browser (and Konqueror is kind of mandatory for KDE users) or starting in safe mode.
If you know how to disable safe mode for firefox, please tell me.

[http://forums.opendns.com/comments.php?DiscussionID=2942&page=1#Comment_18690](http://forums.opendns.com/comments.php?DiscussionID=2942&page=1#Comment_18690)

Version 0.4 is available.

I must say that it works at home but not in the office where firewalls seem to block dns request to opendns.com 

duveau@duveau-laptop:~$ sudo -l
User duveau may run the following commands on this host:
    (root) NOPASSWD: /usr/sbin/synaptic

You have the freedom install some software

---

### Post by roc1479 on 2009-03-20
Hi KIAaze,

Thank you for sharing your knowledge about using squid with your frontend.  I was wondering if there was a way to install the gui without having it setup or modigy firehol, squid and dansguardian.  

Please let me know if your install script can be modified to just install the gui.

Thanks,

Rocky

---

### Post by eric.duveau on 2009-03-20
Look at:
[http://www.mobicip.com/online_safety/netbooks](http://www.mobicip.com/online_safety/netbooks)

---

### Post by KIAaze on 2009-03-25
> **roc1479 said:**
> Hi KIAaze,

Thank you for sharing your knowledge about using squid with your frontend.  I was wondering if there was a way to install the gui without having it setup or modigy firehol, squid and dansguardian.  

Please let me know if your install script can be modified to just install the gui.

Thanks,

Rocky

Ok, I finally added the possibility to disable filtering configuration during install, as well as choose a custom proxy! :)

Just do the following to use squid instead of tinyproxy:
```
bzr branch lp:webcontentcontrol
cd webcontentcontrol
./configure --with-proxy=squid --disable-config  && make && sudo make install

```

For now you'll have to configure the .conf files yourself of course.
But at least, you'll be able to use the GUI to start/stop the filtering and open the .conf files.
Setting ports will probably not work correctly since it was made for tinyproxy.conf.

Please let me know how it works and also post your squid.conf, so I can adapt the install process for it (if you want to have a go at it yourself, look at WCCDIR/scripts/install.sh). ;)
If it works, I'll make a quick release of it.

@eric.duveau:
I added links to your software and to mobicip.com in the initial post. Thanks for the info.

---

### Post by eric.duveau on 2009-03-26
> **KIAaze said:**
> _**Description:**_
WebContentControl is a parental control GUI (more specifically a GUI for DansGuardian+TinyProxy+FireHol).

_**Official website:**_ [https://launchpad.net/webcontentcontrol](https://launchpad.net/webcontentcontrol)

Feedback is very welcome. And help too!

Please report bugs at [https://bugs.launchpad.net/webcontentcontrol](https://bugs.launchpad.net/webcontentcontrol)

_**Pre-Installation:**_
Please make sure you have the "universe" repository enabled.

Go to System->Administration->Software sources and check the "universe" repository.
More info: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

_**Installation:**_
There are three ways to install WebContentControl:
1)Through the PPA repositories
2)From the Debian package
3)From source

_**1)Through the PPA repositories**_
Note: Please avoid using this method for the moment, since the upgrade process isn't fixed yet. (you may loose your settings when upgrading)
```
deb http://ppa.launchpad.net/zohn-joidberg/ubuntu intrepid main
deb-src http://ppa.launchpad.net/zohn-joidberg/ubuntu intrepid main
```
See here for how to add repositories:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

_**2)From the Debian package**_
Download the latest .deb from the site and double-click on it or by command-line:
```
sudo gdebi <package>.deb
```

_**3)From source**_
```

sudo apt-get install gambas2-runtime gambas2-gb-qt gambas2-gb-form gambas2-gb-form-dialog gambas2-gb-qt-kde gambas2-gb-qt-kde-html
sudo apt-get install dansguardian tinyproxy firehol

```
Then download the latest version on [https://launchpad.net/webcontentcontrol/+download](https://launchpad.net/webcontentcontrol/+download) and:
```
tar -xzvf webcontentcontrol-1.0.tar.gz
cd webcontentcontrol-1.0
./configure && make && sudo make install

```

The shortcut should be created in Applications->System tools.
If it isn't, the command-line to launch it is:
```
/usr/bin/webcontentcontrol
```

_**How to uninstall it:**_
```
sudo make uninstall
```
____________________________________

_**List of filtering solutions/projects:**_
[LIST]
[*]WebContentControl: [https://launchpad.net/webcontentcontrol](https://launchpad.net/webcontentcontrol)
[*]Webstrict: [http://www.ubuntume.com/webstrict](http://www.ubuntume.com/webstrict) + [https://launchpad.net/webstrict](https://launchpad.net/webstrict)
[*]GChildCare (not yet available): [https://launchpad.net/gchildcare](https://launchpad.net/gchildcare)
[*]UbuntuCE's Parental control GUI: [http://linux.softpedia.com/get/Security/Parental-control-24501.shtml](http://linux.softpedia.com/get/Security/Parental-control-24501.shtml)
[*]Squid+Squidgard: 
[https://help.ubuntu.com/community/SquidGuard](https://help.ubuntu.com/community/SquidGuard) + [http://www.squidguard.org/](http://www.squidguard.org/)
[*]SmoothGuardian (by the creator of DansGuardian, commercial version with web-based easy to use interface): [http://smoothwall.net/products/smoothguardian2008/](http://smoothwall.net/products/smoothguardian2008/) + [http://dansguardian.org/?page=smoothwall](http://dansguardian.org/?page=smoothwall)
[*]MintNanny: [http://www.linuxmint.com/blog/?p=350](http://www.linuxmint.com/blog/?p=350)
[*]MoBlock, an IP blocker: [http://moblock.berlios.de/](http://moblock.berlios.de/)
[*]TimeKpr, track and control account usage: [https://launchpad.net/timekpr](https://launchpad.net/timekpr)
[*]Discussion about K9 web protection GNU/Linux port: [http://forums.bluecoat.com/viewtopic.php?f=13&t=3179&st=0&sk=t&sd=a&hilit=linux](http://forums.bluecoat.com/viewtopic.php?f=13&t=3179&st=0&sk=t&sd=a&hilit=linux) (suggested by eric.duveau)
[*]Mandriva Linux Parental Control: DrakGuard: [http://www.mandriva.com/enterprise/en/company/press/mandriva-presents-its-latest-distribution-mandriva-linux-2008-spring](http://www.mandriva.com/enterprise/en/company/press/mandriva-presents-its-latest-distribution-mandriva-linux-2008-spring) and [http://rpm.pbone.net/index.php3/stat/4/idpl/9208569/com/drakguard-0.6-1mdv2009.0.noarch.rpm.html](http://rpm.pbone.net/index.php3/stat/4/idpl/9208569/com/drakguard-0.6-1mdv2009.0.noarch.rpm.html)
[*]A content filtering solution for Linux-based netbooks (proprietary): [http://www.mobicip.com/online_safety/netbooks](http://www.mobicip.com/online_safety/netbooks)
[/LIST]

_**DNS filtering:**_
[LIST]
[*]OpenDNS (suggested by forger): [http://www.opendns.com/](http://www.opendns.com/)
[*]GNU/Linux Desktop parental control based on Opendns.com by Eric Duveau: [http://forums.opendns.com/comments.php?DiscussionID=2942&page=1#Comment_18690](http://forums.opendns.com/comments.php?DiscussionID=2942&page=1#Comment_18690)
[*]ScrubIT: [http://www.scrubit.com/](http://www.scrubit.com/)
[/LIST]

_**Kiosk specific (for internet cafes, etc):**_
[LIST]
[*]Kiosk: [http://kiosk.mozdev.org/](http://kiosk.mozdev.org/)
[*]Lock down KDE settings: [http://jriddell.org/programs/kiosk-article.html](http://jriddell.org/programs/kiosk-article.html)
[*]Lock down Gnome settings + disable virtual terminals: [http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/desktop-guide/s1-ddg-lockdown-disable-command-line.html](http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/desktop-guide/s1-ddg-lockdown-disable-command-line.html)
[*]Disable ctrl+alt+backspace: [http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/en-US/Reference_Guide/s3-x-server-config-xorg.conf-serverf.html](http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/en-US/Reference_Guide/s3-x-server-config-xorg.conf-serverf.html)
[*]KDE Kiosk Admin Tool: [http://extragear.kde.org/apps/kiosktool/](http://extragear.kde.org/apps/kiosktool/)
[/LIST]

_**Firefox specific:**_
[LIST]
[*][http://kb.mozillazine.org/Parental_controls](http://kb.mozillazine.org/Parental_controls)
[/LIST]

_**Firewalls and blocking MSN:**_
[LIST]
[*]NuFW: An authenticating firewall: [http://www.nufw.org/](http://www.nufw.org/)
[*]How to block MSN: [http://blog.eglis.com/index.php/post/2005/11/16/Bloquer-le-protocol-MSN](http://blog.eglis.com/index.php/post/2005/11/16/Bloquer-le-protocol-MSN) (French)
[/LIST]

_**For Windows:**_
[LIST]
[*]LogProtect (Windows only, but Free/Libre Software): [http://www.logprotect.fr/](http://www.logprotect.fr/)
[*]K9 Web Protection (proprietary): [http://www1.k9webprotection.com/](http://www1.k9webprotection.com/)
[*]Time control on Windows: [http://www.dougknox.com/xp/tips/xp_restrict_users.htm](http://www.dougknox.com/xp/tips/xp_restrict_users.htm) and [http://www.builderau.com.au/program/windows/soa/Force-users-to-log-off-when-their-time-is-up/0,339024644,339282967,00.htm](http://www.builderau.com.au/program/windows/soa/Force-users-to-log-off-when-their-time-is-up/0,339024644,339282967,00.htm)
[/LIST]

**_Useful links:_**
[LIST]
[*]Setup without iptables: [http://www.vollmar.ch/dansguardian-e.html](http://www.vollmar.ch/dansguardian-e.html)
[*]Sarg - Squid Analysis Report Generator: [http://sarg.sourceforge.net/sarg.php](http://sarg.sourceforge.net/sarg.php)
[*]DansGuardian Documentation Wiki: [http://contentfilter.futuragts.com/wiki/doku.php?id=main_index](http://contentfilter.futuragts.com/wiki/doku.php?id=main_index)
[/LIST]

_**How it works:**_
Note: Tinyproxy is equivalent to Squid and Firehol is equivalent to iptables (FireHol manages iptables).
[LIST]
[*][http://dansguardian.org/?page=dgflow](http://dansguardian.org/?page=dgflow) (except that WebContentControl forces the use of the proxy through FireHol)
[*][http://www.zephyrsoft.net/files/linux-filtering-monitoring-howto.pdf](http://www.zephyrsoft.net/files/linux-filtering-monitoring-howto.pdf) (Picture inside, as well as script for mailing banned sites access attempts to someone)
[/LIST]

If you know other projects, useful links, etc, please tell me so I can add them to the list.

_**FAQ, troubleshooting and tips:**_
[LIST=1]
[*]Is user-specific configuration possible?
Yes, but not through the GUI yet.
cf:
[http://www.ubuntume.com/webstrict#i_want_different_configurations_for_different_user_accounts](http://www.ubuntume.com/webstrict#i_want_different_configurations_for_different_user_accounts)
[http://contentfilter.futuragts.com/wiki/doku.php?id=group_configuration](http://contentfilter.futuragts.com/wiki/doku.php?id=group_configuration)

[*]If the internet doesn't work anymore or isn't filtered: Please post the contents of the following files:
```
/etc/dansguardian/dansguardian.conf
/etc/tinyproxy/tinyproxy.conf
/etc/firehol/firehol.conf

```
and also the output of this command:
```
sudo lsof -i :8080
```

[*]If almost everything you google gets blocked: Just turn on Google safe mode again. ;)

[*]Filtering not working over wireless?
Three solutions:
1)Lock WPA interfaces by clicking on the "WPA interfaces unlocked" button.
2)Lock the firefox proxy settings from the GUI and disable/uninstall all other browsers (or lock their proxy settings to port 8080 if you know how to do it).
3)Restart FireHol after wireless has started.

[*]SSL not blocked?
You have to lock down the browser settings for this to work. cf explanation above.

[*]Dansguardian tweaking tips:
Use [http://urlblacklist.com/](http://urlblacklist.com/) or [http://www.shallalist.de/](http://www.shallalist.de/) (suggested by eric.duveau) ;)

[*]Also, it's useful to comment out "japanese pornography" in the weightedphraselist, as well as whitelist all webmail sites in the "exceptionsitelist".

/etc/dansguardian/lists/exceptionsitelist:
```

...
.Include</etc/dansguardian/lists/blacklists/mail/domains>
...

```
/etc/dansguardian/lists/exceptionurllist:
```

...
.Include</etc/dansguardian/lists/blacklists/mail/urls>
...

```
/etc/dansguardian/lists/weightedphraselist:
```

...
##.Include</etc/dansguardian/lists/phraselists/pornography/weighted_japanese> #ALPHA#
...

```
...because some valid sites tend to get blocked by it due to some strange encoding problems. :(

[*]Don't forget to prevent getting any filesharing program (or configure your firewall to block ports):
/etc/dansguardian/lists/bannedsitelist:
```
...
.Include</etc/dansguardian/lists/blacklists/filesharing/domains>
...

```
/etc/dansguardian/lists/bannedurllist:
```
...
.Include</etc/dansguardian/lists/blacklists/filesharing/urls>
...

```

An interface to select categories from the blacklists directory is planned. ;)

[*]How to disable X11 forwarding in openssh:
I created a patch for this, which you can get here: [http://bazaar.launchpad.net/%7Ezohn-joidberg/webcontentcontrol/main/annotate/head%3A/openssh-5.2p1_disableX11.patch](http://bazaar.launchpad.net/%7Ezohn-joidberg/webcontentcontrol/main/annotate/head%3A/openssh-5.2p1_disableX11.patch)
Download openssh-5.2p1.tar.gz from [http://www.openssh.com/](http://www.openssh.com/)
Then just:
```
tar -xzvf openssh-5.2p1.tar.gz
cd openssh-5.2p1
patch -p2 < ../openssh-5.2p1_disableX11.patch
./configure
make
sudo make install

```
[/LIST]

____________________________________

The rest of this post should now hopefully be unnecessary. :)

If you want to set up such a system manually without the GUI, here's a very helpful guide which also explains how it works:
[http://www.pilpi.net/journal/item-985.php](http://www.pilpi.net/journal/item-985.php)

=======================================
06/09/2008: UPDATE
I started uploading my code to launchpad for version control (&bug reports+ distribution):
[https://launchpad.net/webcontentcontrol](https://launchpad.net/webcontentcontrol)

I also joined the [GChildCare]("https://launchpad.net/gchildcare") project and plan to help it. So this is only a project to get a working GUI quickly up and running.

Until this is the case, please follow the instructions below.
=======================================

This "Howto" is an updated version of this one:
[http://ubuntuforums.org/showthread.php?t=226298](http://ubuntuforums.org/showthread.php?t=226298)

[B]Downloads are at the bottom of this post.
Note: WebContentControl.tar.gz is meant for developers and contains the source code of a new GUI I'm working on.[/B]

The original GUI was made by nanomad. I just made a few changes so that it should work "out of the box".
I created a new thread because nanomad stopped updating the other one.
If you still encounter problems, please tell me.



Note:
Another parental control GUI is available from Ubuntu ME here:
[http://www.ubuntume.com/webstrict](http://www.ubuntume.com/webstrict)

However, it is browser dependent, meaning that it will only work with properly configured browsers. In other words, it can easily be bypassed by using another browser or changing the browser config if it isn't locked.
An easy way to fix this is installing firehol. However, it is then also necessary to configure it correctly...

If I have time, I might try using their nice GUI with the browser-independent system from the one given here. ;)

_**For Hardy and later versions:**_
gambas-runtime has been replaced by gambas2-runtime, so until the GUI is made compatible with the new version, you may download&install the old gambas-runtime here:
[http://packages.ubuntu.com/gutsy/gambas-runtime](http://packages.ubuntu.com/gutsy/gambas-runtime)

_**Troubleshooting: If you are having problems:**_
1)Please post the console output of the installation process (just rerun the installation and copy/paste the output before closing the terminal window)
An easier way to do this (until I add automatic log creation ;) ):
For installation problems:
```
./.setup 1>install.log 2>&1
```
For uninstallation problems:
```
./.remove 1>uninstall.log 2>&1
```

2)If the GUI won't launch: post the output of the following command:
```
/usr/local/apps/parental-control/ubuntu_parental_control_gui
```

[COLOR="Blue"]It may be useful for someone who wants to keep some freedom to install packages:[/COLOR]

_to install a package:_

**sudo aptgetintall < a_package >**

**cat  aptgetintall**
#/bin/bash
apt-get install $1

_to upgrade_

**sudo aptgetupgrade**

**cat aptgetupgrade**
#/bin/bash
apt-get upgrade
[COLOR="Blue"]
User will be able to install and upgrade[/COLOR]

**sudo -l**
aptgetintall, aptgetupgrade

---

### Post by KIAaze on 2009-03-26
You didn't have to quote my whole post. ^^'
Anyway, I don't think "sudo aptgetintall" is much shorter than "sudo apt-get install ".

As for the "sudo -l" (list out the allowed (and forbidden) commands for the invoking user on the current host), it would make more sense if you also explained what to put in the /etc/sudoers file for it to work. ;)

/etc/sudoers definitely is very useful. Here are some tutorials:
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)
[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

I have a template sudoers file in the webcontentcontrol source package. ;)

---

### Post by eric.duveau on 2009-03-26
> **KIAaze said:**
> You didn't have to quote my whole post. ^^'
Anyway, I don't think "sudo aptgetintall" is much shorter than "sudo apt-get install ".

aptgetinstall allows to install (but not to remove)

> **KIAaze said:**
> 
As for the "sudo -l" (list out the allowed (and forbidden) commands for the invoking user on the current host), it would make more sense if you also explained what to put in the /etc/sudoers file for it to work. ;)


```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

User_Alias MES_USERS = duveau
Host_Alias MES_ORDIS = localhost, duveau-laptop
Cmnd_Alias MES_COMMANDES = /usr/local/pkgm/bin/aptgetinstall, /usr/local/pkgm/bin/aptgetupdate,/usr/local/pkgm/bin/aptgetupgrade




# User privilege specification
root	ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
# %admin ALL=(ALL) ALL
#

MES_USERS MES_ORDIS=(root)NOPASSWD:MES_COMMANDES
```

---

### Post by eric.duveau on 2009-03-26
I like very much your parental control but I am looking for a solution to give some admin rights to the controlled user. Like the possibility to add new software. (of course the user should not have the possibility to remove the filtering software).

This is the goal of my post.

---

### Post by nanomad on 2009-03-28
(I already posted this, but it was in the wrong thread, sorry)

Thanks for continuing developing my project. Unfortunately I've lost the sources long ago in an harddrive crash (and I've got connectivity issues for a long period).
I'm quite busy right now, but tell me if I can help you in any way.

ps. I do want to continue developing, since I've got a kind of "moral contract" with the guy who posted above me (he started it all).

---

### Post by KIAaze on 2009-03-28
Wow, so you're still alive! :shock: :)
I never expected to hear from you after all this time!
Check your PM inbox. I think I sent you quite a few messages. ;)

> ps. I do want to continue developing, since I've got a kind of "moral contract" with the guy who posted above me (he started it all).

You mean me or eric.duveau?
You can join the launchpad project anytime you want. :)
Just join the GChildCare group. I think this should give you commit permissions.
It's managed by Didier Roche, but I'm sure he'll accept you.

Also, it would help if you updated your initial post in your thread:
[http://ubuntuforums.org/showthread.php?t=226298](http://ubuntuforums.org/showthread.php?t=226298)

A lot of people find it via google and install what's in the first post and then have problems.

P.S.: And thanks of course for your software. It helped me get started. :)

---

### Post by eric.duveau on 2009-03-28
> **KIAaze said:**
> Wow, so you're still alive! :shock: :)


Yes I am also happy you're back. KIAaze has made a great job thanks to you've done at the beginning. If you could collaborate together I would be nice

As for me I see two missing features: 

* remote accounting 
* users privileges management (different user profiles)

But it it up to you (just a suggestion)

---

### Post by nanomad on 2009-03-29
Ok, i've updated the first page of my thread. There is a big red message on top now. I'm going to send a PM to one of the mods to close that thread.
I've also sent a membership request to the GChildCare team. I'm downloading the bzr sources right now.
I was thinking about porting my old GUI to native GTK+ (either Python or C++, I prefer the first choice), what do you think? (It should wipe away the need for gambas, which is an overkill IMHO)

---

### Post by KIAaze on 2009-03-29
In case you haven't figured out how to download the source code yet:
```
bzr branch lp:webcontentcontrol
```
should do it.

And, yes, I'm also for switching to python+GTK (pygtk). :)
We might even commit this to the GChildCare project then since they plan to use python.
(Altough I really enjoyed Gambas for developing the GUI. It's really easy to use.)

Didier Roche already has some python prototype code for the GUI. Hopefully this will motivate him to finally release it. ;)

---

### Post by nanomad on 2009-03-29
Ok, i've downloaded the code (i was trying to branch lp:gchildcare before). I'm reinstalling gambas right now, then I'll try to create a similar GUI in python.

---

### Post by trinidadflores on 2009-04-05
Does this program work for the 64 bit version of ubuntu?  If not is there a version that will work for this version?

---

### Post by KIAaze on 2009-04-06
> **trinidadflores said:**
> Does this program work for the 64 bit version of ubuntu?  If not is there a version that will work for this version?

Yes. Yes. :)

v1.2.6 released:
[https://launchpad.net/webcontentcontrol/+announcement/2433](https://launchpad.net/webcontentcontrol/+announcement/2433)

You can get the 64-bit packages from the PPA again now.
Otherwise, the source .tar.gz should work too.

cf the [initial post]("http://ubuntuforums.org/showthread.php?t=843510") for installation info.

---

### Post by vaski on 2009-04-07
After updating to the new release of web content control all of my edited lists where deleted, is there any way to get them back ?
i installed it through the ppa repository

---

### Post by KIAaze on 2009-04-07
What version did you previously have installed?

I fixed the upgrade process for package upgrades **after** 1.2.6, **not for previous versions**. Sorry for forgetting to mention that. :oops:

However, it should still have made a backup of the configuration files during installation, so you should have them in "**/usr/share/webcontentcontrol/backup.dgs.full**" (it's just a .tar.gz by the way).

1)First of all, make a backup of the backup somewhere, just in case. ;)
```
cp /usr/share/webcontentcontrol/backup.dgs.full ~
```

2)Now, have a look at the current configuration files. Because normally, the installation shouldn't have changed any of the files in /etc/dansguardian/lists/ (it only changes dansguardian.conf, tinyproxy.conf and firehol.conf ).

If they haven't changed, make a backup of them too. You can use the GUI export function to do this for example.
Or by command-line:
```
sudo /usr/share/webcontentcontrol/scripts/super_export.sh ~/anotherbackup 1 1 1
```


3)Then, to restore the previous configuration files, just run:
```
sudo /usr/share/webcontentcontrol/scripts/import_all.sh /usr/share/webcontentcontrol/backup.dgs.full

```

4)To make sure later upgrades don't reconfigure the system, run the following command:
```
sudo touch /usr/share/webcontentcontrol/configured
```
(The file should already be there if you installed the latest version, but just in case...)

Note1: Normally, you should be able to use the import function from the GUI to import the backup file.
Unfortunately it doesn't work right now because the GUI save dialog adds ".tcs" automatically and then doesn't find the file. I will have to fix that.

Note2: Doing "sudo apt-get remove webcontentcontrol" would have restored the previous config files too.

---

### Post by notbitmonk on 2009-04-09
I updated the html files for the English and Spanish languages to XHTML 1.0 Strict with the latest compatibility guides from W3C.  It mostly follows the original html files but I added all the components that make webcontentcontrol.  I tried to separate the css to its own file but wasn't able to make the html find the link to the file.  So now, like in the old page, the CSS is repeated with each page.  The two files are attached.  What I did was to open gedit through the Terminal with sudo and copy the html to the html file.

---

### Post by Kalma on 2009-04-29
Great Job!!!

Since I am an absolute newbie, I find very hard to configure WebContentControl by using the conf files... The presets look fine for me, but it fails when trying to load them: /usr/share/webcontentcontrol/preset_configs directory doesn't exist... How can I fix this?

Thanx!!!

---

### Post by KIAaze on 2009-04-30
It's because I haven't created the preset configs yet. I'll try doing it as soon as possible.

---

### Post by Kalma on 2009-04-30
Oh! I'm sorry... I will wait in such a case. You're doing an excellent job. Thanx a lot.

Is it possible to create different behaviours (profiles) for each users yet? I have a home PC, which is used by me and my three children, who have  a wide range of ages, so I would like to configure WebContentControl to behave in a different way for each one of them. I have seen that the GUI lets you select the user, but I have also read that it must be done in a different way. If so, which is this other way?

---

### Post by mnrbig on 2009-05-02
Is it possible to use this in a networked (proxy server) environment. I have 4 children each with there own PC and I don't want to have to make changes 4 times.

---

### Post by KIAaze on 2009-05-03
> **Kalma said:**
> Oh! I'm sorry... I will wait in such a case. You're doing an excellent job. Thanx a lot.

Is it possible to create different behaviours (profiles) for each users yet? I have a home PC, which is used by me and my three children, who have  a wide range of ages, so I would like to configure WebContentControl to behave in a different way for each one of them. I have seen that the GUI lets you select the user, but I have also read that it must be done in a different way. If so, which is this other way?
The other way requires setting up some authentication method (so that dansguardian can identify the user).
I managed to do it using squid (webcontentcontrol uses tinyproxy instead):
[http://tech.groups.yahoo.com/group/dansguardian/message/22651](http://tech.groups.yahoo.com/group/dansguardian/message/22651)
See here for more info:
[http://contentfilter.futuragts.com/wiki/doku.php?id=user_identification_methods](http://contentfilter.futuragts.com/wiki/doku.php?id=user_identification_methods)
[http://contentfilter.futuragts.com/wiki/doku.php?id=group_configuration](http://contentfilter.futuragts.com/wiki/doku.php?id=group_configuration)

> **mnrbig said:**
> Is it possible to use this in a networked (proxy server) environment. I have 4 children each with there own PC and I don't want to have to make changes 4 times.

Yes, it is possible with dansguardian. It's probably possible to do it with the GUI too somehow, but I recommend trying it with dansguardian only first so you understand how it works.
Normally, if you already have firewall and proxy set up on the server, all you need to do is install dansguardian on the server too and specify the proxy port number in dansguardian.conf.

If you need help for setting up dansguardian, you can use its mailing-list:
[http://dansguardian.org/?page=mailinglist](http://dansguardian.org/?page=mailinglist)

Here's also a tutorial on setting up dansguardian in a networked environment:
[http://www.branchdistrictlibrary.org/professional/ubuntu_and_dansguardian.php](http://www.branchdistrictlibrary.org/professional/ubuntu_and_dansguardian.php)

Other tutorials:
[http://dansguardian.org/?page=documentation](http://dansguardian.org/?page=documentation)

I will try to make webcontentcontrol support squid too (so that multiple filtering groups are possible) and eventually even independent of the proxy and firewall used (dansguardian already is that way, but it's not "user-friendly").

The biggest problem is that to prevent filter bypassing it's necessary to configure the firewall. On GNU/Linux, there's only iptables as far as I know, all others (like firehol) are just interfaces to iptables. But I can't just add iptable rules since they might be removed by those other interfaces on startup. :/
So supporting just tinyproxy and squid for multiple filter groups will probably come first...

---

### Post by Kalma on 2009-05-11
Again, thanx a lot.

I will try and will come back to tell how it was.

Keep on pushing!!!

---

### Post by High Roller on 2009-05-11
> **KIAaze said:**
> It's because I haven't created the preset configs yet. I'll try doing it as soon as possible.

Are these presets specific to "Webcontentcontrol" or dansguardian?

I can't wait until there are some available.  The way it's setup by default causes a lot of false positives.

---

### Post by KIAaze on 2009-05-12
> **High Roller said:**
> Are these presets specific to "Webcontentcontrol" or dansguardian?

I can't wait until there are some available.  The way it's setup by default causes a lot of false positives.

Specific to WebContentControl.

---

### Post by mdbarton on 2009-05-16
Will adding these sources:
```
deb http://ppa.launchpad.net/zohn-joidberg/ubuntu **intrepid** main
deb-src http://ppa.launchpad.net/zohn-joidberg/ubuntu **intrepid** main 
```
work on Jaunty?  or is this Intrepid only?

---

### Post by mdbarton on 2009-05-16
> **mdbarton said:**
> Will adding these sources:
```
deb http://ppa.launchpad.net/zohn-joidberg/ubuntu **intrepid** main
deb-src http://ppa.launchpad.net/zohn-joidberg/ubuntu **intrepid** main 
```
work on Jaunty?  or is this Intrepid only?

Ok, now I've woken up a bit more and read the instructions, I just got the latest deb file and it seems to be installing fine on Jaunty.

---

### Post by popaye85 on 2009-06-03
I have a semi-working Web Content Control installation working.

Installed the deb pkg on my ubuntu Jaunty 9.04.  Everything went VERY smoothly.  Everything started and configured correctly.

Filtering works great on the Jaunty machine.  However transparent proxy/filter doesn't work on the dhcp clients (internal network).

Summary of problem:
-If I leave a client with no proxy set and WCC set to defaults, the clients cannot see the internet at all.
-If I set the client proxy to point to the proxy/filter/gateway machine and leave the proxy at defaults (firehol running) I get nothing.
-If I turn off firehol via WCC leaving the client pointing the proxy to the WCC machine, filtering works fine.  However, I cannot get other services to pass thorough, (may be another issue) such as ftp, ssh, etc.

My question is twofold, a) what have I done wrong to keep transparent proxy from working?  and b) how can I open up services from clients through the proxy/filter/gateway (such as ftp, etc)?

The config files I think are required are listed below.  Thanks in advance!

**my firehol.conf**
```

version 5
iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP
transparent_squid 8080 "proxy root"


# Accept all client traffic on any interface
interface any world
policy drop
protection strong
	client all accept
server cups accept
```

**My tinyproxy.conf **
```
User proxy
Group proxy

#
# Port to listen on.
#
Port 3128

#
# If you have multiple interfaces this allows you to bind to only one. If
# this is commented out, tinyproxy will bind to all interfaces present.
#
#Listen 192.168.0.1

#
# The Bind directive allows you to bind the outgoing connections to a
# particular IP address.
#
#Bind 192.168.0.1

#
# Timeout: The number of seconds of inactivity a connection is allowed to
# have before it closed by tinyproxy.
#
Timeout 600

#
# ErrorFile: Defines the HTML file to send when a given HTTP error
# occurs.  You will probably need to customize the location to your
# particular install.  The usual locations to check are:
#   /usr/local/share/tinyproxy
#   /usr/share/tinyproxy
#   /etc/tinyproxy
#
# ErrorFile 404 "/usr/share/tinyproxy/404.html"
# ErrorFile 400 "/usr/share/tinyproxy/400.html"
# ErrorFile 503 "/usr/share/tinyproxy/503.html"
# ErrorFile 403 "/usr/share/tinyproxy/403.html"
# ErrorFile 408 "/usr/share/tinyproxy/408.html"

# 
# DefaultErrorFile: The HTML file that gets sent if there is no
# HTML file defined with an ErrorFile keyword for the HTTP error
# that has occured.
#
DefaultErrorFile "/usr/share/tinyproxy/default.html"

#
# StatFile: The HTML file that gets sent when a request is made
# for the stathost.  If this file doesn't exist a basic page is
# hardcoded in tinyproxy.
#
StatFile "/usr/share/tinyproxy/stats.html"

#
# Where to log the information. Either LogFile or Syslog should be set,
# but not both.
#
Logfile "/var/log/tinyproxy.log"
# Syslog On

#
# Set the logging level. Allowed settings are:
#	Critical	(least verbose)
#	Error
#	Warning
#	Notice
#	Connect		(to log connections without Info's noise)
#	Info		(most verbose)
# The LogLevel logs from the set level and above. For example, if the LogLevel
# was set to Warning, than all log messages from Warning to Critical would be
# output, but Notice and below would be suppressed.
#
LogLevel Info

#
# PidFile: Write the PID of the main tinyproxy thread to this file so it
# can be used for signalling purposes.
#
PidFile "/var/run/tinyproxy/tinyproxy.pid"

#
# Include the X-Tinyproxy header, which has the client's IP address when
# connecting to the sites listed.
#
#XTinyproxy mydomain.com

#
# Turns on upstream proxy support.
#
# The upstream rules allow you to selectively route upstream connections
# based on the host/domain of the site being accessed.
#
# For example:
#  # connection to test domain goes through testproxy
#  upstream testproxy:8008 ".test.domain.invalid"
#  upstream testproxy:8008 ".our_testbed.example.com"
#  upstream testproxy:8008 "192.168.128.0/255.255.254.0"
#
#  # no upstream proxy for internal websites and unqualified hosts
#  no upstream ".internal.example.com"
#  no upstream "www.example.com"
#  no upstream "10.0.0.0/8"
#  no upstream "192.168.0.0/255.255.254.0"
#  no upstream "."
#
#  # connection to these boxes go through their DMZ firewalls
#  upstream cust1_firewall:8008 "testbed_for_cust1"
#  upstream cust2_firewall:8008 "testbed_for_cust2"
#
#  # default upstream is internet firewall
#  upstream firewall.internal.example.com:80
#
# The LAST matching rule wins the route decision.  As you can see, you
# can use a host, or a domain:
#  name     matches host exactly
#  .name    matches any host in domain "name"
#  .        matches any host with no domain (in 'empty' domain)
#  IP/bits  matches network/mask
#  IP/mask  matches network/mask
#
#Upstream some.remote.proxy:port

#
# This is the absolute highest number of threads which will be created. In
# other words, only MaxClients number of clients can be connected at the
# same time.
#
MaxClients 100

#
# These settings set the upper and lower limit for the number of
# spare servers which should be available. If the number of spare servers
# falls below MinSpareServers then new ones will be created. If the number
# of servers exceeds MaxSpareServers then the extras will be killed off.
#
MinSpareServers 5
MaxSpareServers 20

#
# Number of servers to start initially.
#
StartServers 10

#
# MaxRequestsPerChild is the number of connections a thread will handle
# before it is killed. In practise this should be set to 0, which disables
# thread reaping. If you do notice problems with memory leakage, then set
# this to something like 10000
#
MaxRequestsPerChild 0

#
# The following is the authorization controls. If there are any access
# control keywords then the default action is to DENY. Otherwise, the
# default action is ALLOW.
#
# Also the order of the controls are important. The incoming connections
# are tested against the controls based on order.
#
Allow 127.0.0.1
#Allow 192.168.0.0/16
#Allow 172.16.0.0/12
#Allow 10.0.0.0/8

#
# The "Via" header is required by the HTTP RFC, but using the real host name
# is a security concern.  If the following directive is enabled, the string
# supplied will be used as the host name in the Via header; otherwise, the
# server's host name will be used.
#
ViaProxyName "tinyproxy"

#
# The location of the filter file.
#
#Filter "/etc/tinyproxy/filter"

#
# Filter based on URLs rather than domains.
#
#FilterURLs On

#
# Use POSIX Extended regular expressions rather than basic.
#
#FilterExtended On

#
# Use case sensitive regular expressions.
#                                                                         
#FilterCaseSensitive On     

#
# Change the default policy of the filtering system.  If this directive is
# commented out, or is set to "No" then the default policy is to allow
# everything which is not specifically denied by the filter file.
#
# However, by setting this directive to "Yes" the default policy becomes to
# deny everything which is _not_ specifically allowed by the filter file.
#
#FilterDefaultDeny Yes

#
# If an Anonymous keyword is present, then anonymous proxying is enabled.
# The headers listed are allowed through, while all others are denied. If
# no Anonymous keyword is present, then all header are allowed through.
# You must include quotes around the headers.
#
#Anonymous "Host"
#Anonymous "Authorization"

#
# This is a list of ports allowed by tinyproxy when the CONNECT method
# is used.  To disable the CONNECT method altogether, set the value to 0.
# If no ConnectPort line is found, all ports are allowed (which is not
# very secure.)
#
# The following two ports are used by SSL.
#
ConnectPort 443
ConnectPort 563
```

**My dansguardian.conf**
```
# DansGuardian config file for version 2.9.9.7

# **NOTE** as of version 2.7.5 most of the list files are now in dansguardianf1.conf

#UNCONFIGURED - Please remove this line after configuration

# Web Access Denied Reporting (does not affect logging)
#
# -1 = log, but do not block - Stealth mode
#  0 = just say 'Access Denied'
#  1 = report why but not what denied phrase
#  2 = report fully
#  3 = use HTML template file (accessdeniedaddress ignored) - recommended
#
reportinglevel = 3

# Language dir where languages are stored for internationalisation.
# The HTML template within this dir is only used when reportinglevel
# is set to 3. When used, DansGuardian will display the HTML file instead of
# using the perl cgi script.  This option is faster, cleaner
# and easier to customise the access denied page.
# The language file is used no matter what setting however.
#
languagedir = '/etc/dansguardian/languages'

# language to use from languagedir.
language = 'ukenglish'

# Logging Settings
#
# 0 = none  1 = just denied  2 = all text based  3 = all requests
loglevel = 2

# Log Exception Hits
# Log if an exception (user, ip, URL, phrase) is matched and so
# the page gets let through.  Can be useful for diagnosing
# why a site gets through the filter.
# 0 = never log exceptions
# 1 = log exceptions, but do not explicitly mark them as such
# 2 = always log & mark exceptions (default)
logexceptionhits = 2

# Log File Format
# 1 = DansGuardian format (space delimited)
# 2 = CSV-style format
# 3 = Squid Log File Format
# 4 = Tab delimited
logfileformat = 1

# truncate large items in log lines
#maxlogitemlength = 400

# anonymize logs (blank out usernames & IPs)
#anonymizelogs = on


# Syslog logging
#
# Use syslog for access logging instead of logging to the file
# at the defined or built-in "loglocation"
#syslog = on

# Log file location
# 
# Defines the log directory and filename.
#loglocation = '/var/log/dansguardian/access.log'


# Statistics log file location
#
# Defines the stat file directory and filename.
# Only used in conjunction with maxips > 0
# Once every 3 minutes, the current number of IPs in the cache, and the most
# that have been in the cache since the daemon was started, are written to this
# file. IPs persist in the cache for 7 days.
#statlocation = '/var/log/dansguardian/stats'


# Network Settings
# 
# the IP that DansGuardian listens on.  If left blank DansGuardian will
# listen on all IPs.  That would include all NICs, loopback, modem, etc.
# Normally you would have your firewall protecting this, but if you want
# you can limit it to a certain IP. To bind to multiple interfaces,
# specify each IP on an individual filterip line.
filterip =

# the port that DansGuardian listens to.
filterport = 8080

# the ip of the proxy (default is the loopback - i.e. this server)
proxyip = 127.0.0.1

# the port DansGuardian connects to proxy on
proxyport = 3128

# accessdeniedaddress is the address of your web server to which the cgi
# dansguardian reporting script was copied. Only used in reporting levels 1 and 2.
#
# This webserver must be either:
#  1. Non-proxied. Either a machine on the local network, or listed as an exception
#     in your browser's proxy configuration.
#  2. Added to the exceptionsitelist. Option 1 is preferable; this option is
#     only for users using both transparent proxying and a non-local server
#     to host this script.
#
# Individual filter groups can override this setting in their own configuration.
#
accessdeniedaddress = 'http://YOURSERVER.YOURDOMAIN/cgi-bin/dansguardian.pl'

# Non standard delimiter (only used with accessdeniedaddress)
# To help preserve the full banned URL, including parameters, the variables
# passed into the access denied CGI are separated using non-standard
# delimiters. This can be useful to ensure correct operation of the filter
# bypass modes. Parameters are split using "::" in place of "&", and "==" in
# place of "=".
# Default is enabled, but to go back to the standard mode, disable it.
nonstandarddelimiter = on



# Banned image replacement
# Images that are banned due to domain/url/etc reasons including those
# in the adverts blacklists can be replaced by an image.  This will,
# for example, hide images from advert sites and remove broken image
# icons from banned domains.
# on (default) | off
usecustombannedimage = on
custombannedimagefile = '/usr/share/dansguardian/transparent1x1.gif'



# Filter groups options
# filtergroups sets the number of filter groups. A filter group is a set of content
# filtering options you can apply to a group of users.  The value must be 1 or more.
# DansGuardian will automatically look for dansguardianfN.conf where N is the filter
# group.  To assign users to groups use the filtergroupslist option.  All users default
# to filter group 1.  You must have some sort of authentication to be able to map users
# to a group.  The more filter groups the more copies of the lists will be in RAM so
# use as few as possible.
filtergroups = 1
filtergroupslist = '/etc/dansguardian/lists/filtergroupslist'



# Authentication files location
bannediplist = '/etc/dansguardian/lists/bannediplist'
exceptioniplist = '/etc/dansguardian/lists/exceptioniplist'



# Show weighted phrases found
# If enabled then the phrases found that made up the total which excedes
# the naughtyness limit will be logged and, if the reporting level is
# high enough, reported. on | off
showweightedfound = on

# Weighted phrase mode
# There are 3 possible modes of operation:
# 0 = off = do not use the weighted phrase feature.
# 1 = on, normal = normal weighted phrase operation.
# 2 = on, singular = each weighted phrase found only counts once on a page.
#
weightedphrasemode = 1
# gg switched from 2



# Positive (clean) result caching for URLs
# Caches good pages so they don't need to be scanned again.
# It also works with AV plugins.
# 0 = off (recommended for ISPs with users with disimilar browsing)
# 1000 = recommended for most users
# 5000 = suggested max upper limit
# If you're using an AV plugin then use at least 5000.
urlcachenumber = 1000
#
# Age before they are stale and should be ignored in seconds
# 0 = never
# 900 = recommended = 15 mins
urlcacheage = 900



# Clean cache for content (AV) scan results
# By default, to save CPU, files scanned and found to be
# clean are inserted into the clean cache and NOT scanned
# again for a while.  If you don't like this then choose
# to disable it.
# (on|off) default = on.
scancleancache = on



# Smart, Raw and Meta/Title phrase content filtering options
# Smart is where the multiple spaces and HTML are removed before phrase filtering
# Raw is where the raw HTML including meta tags are phrase filtered
# Meta/Title is where only meta and title tags are phrase filtered (v. quick)
# CPU usage can be effectively halved by using setting 0 or 1 compared to 2
# 0 = raw only
# 1 = smart only
# 2 = both of the above (default)
# 3 = meta/title
phrasefiltermode = 2

# Lower casing options
# When a document is scanned the uppercase letters are converted to lower case
# in order to compare them with the phrases.  However this can break Big5 and
# other 16-bit texts.  If needed preserve the case.  As of version 2.7.0 accented
# characters are supported.
# 0 = force lower case (default)
# 1 = do not change case
# 2 = scan first in lower case, then in original case
preservecase = 0

# Note:
# If phrasefiltermode and preserve case are both 2, this equates to 4 phrase
# filtering passes. If you have a large enough userbase for this to be a
# worry, and need to filter pages in exotic character encodings, it may be
# better to run two instances on separate servers: one with preservecase 1
# (and possibly forcequicksearch 1) and non ASCII/UTF-8 phrase lists, and one
# with preservecase 0 and ASCII/UTF-8 lists.



# Hex decoding options
# When a document is scanned it can optionally convert %XX to chars.
# If you find documents are getting past the phrase filtering due to encoding
# then enable.  However this can break Big5 and other 16-bit texts.
# off = disabled (default)
# on = enabled
hexdecodecontent = off



# Force Quick Search rather than DFA search algorithm
# The current DFA implementation is not totally 16-bit character compatible
# but is used by default as it handles large phrase lists much faster.
# If you wish to use a large number of 16-bit character phrases then
# enable this option.
# off (default) | on (Big5 compatible)
forcequicksearch = off



# Reverse lookups for banned site and URLs.
# If set to on, DansGuardian will look up the forward DNS for an IP URL
# address and search for both in the banned site and URL lists.  This would
# prevent a user from simply entering the IP for a banned address.
# It will reduce searching speed somewhat so unless you have a local caching
# DNS server, leave it off and use the Blanket IP Block option in the
# bannedsitelist file instead.
reverseaddresslookups = off



# Reverse lookups for banned and exception IP lists.
# If set to on, DansGuardian will look up the forward DNS for the IP
# of the connecting computer.  This means you can put in hostnames in
# the exceptioniplist and bannediplist.
# If a client computer is matched against an IP given in the lists, then the
# IP will be recorded in any log entries; if forward DNS is successful and a
# match occurs against a hostname, the hostname will be logged instead.
# It will reduce searching speed somewhat so unless you have a local DNS server, 
# leave it off.
reverseclientiplookups = off


# Perform reverse lookups on client IPs for successful requests.
# If set to on, DansGuardian will look up the forward DNS for the IP
# of the connecting computer, and log host names (where available) rather than
# IPs against requests.
# This is not dependent on reverseclientiplookups being enabled; however, if it
# is, enabling this option does not incur any additional forward DNS requests.
logclienthostnames = off


# Build bannedsitelist and bannedurllist cache files.
# This will compare the date stamp of the list file with the date stamp of
# the cache file and will recreate as needed.
# If a bsl or bul .processed file exists, then that will be used instead.
# It will increase process start speed by 300%.  On slow computers this will
# be significant.  Fast computers do not need this option. on | off
createlistcachefiles = on



# POST protection (web upload and forms)
# does not block forms without any file upload, i.e. this is just for
# blocking or limiting uploads
# measured in kibibytes after MIME encoding and header bumph
# use 0 for a complete block
# use higher (e.g. 512 = 512Kbytes) for limiting
# use -1 for no blocking
#maxuploadsize = 512
#maxuploadsize = 0
maxuploadsize = -1



# Max content filter size
# Sometimes web servers label binary files as text which can be very
# large which causes a huge drain on memory and cpu resources.
# To counter this, you can limit the size of the document to be
# filtered and get it to just pass it straight through.
# This setting also applies to content regular expression modification.
# The value must not be higher than maxcontentramcachescansize
# The size is in Kibibytes - eg 2048 = 2Mb
# use 0 to set it to maxcontentramcachescansize
maxcontentfiltersize = 256



# Max content ram cache scan size
# This is only used if you use a content scanner plugin such as AV
# This is the max size of file that DG will download and cache
# in RAM.  After this limit is reached it will cache to disk
# This value must be less than or equal to maxcontentfilecachescansize.
# The size is in Kibibytes - eg 10240 = 10Mb
# use 0 to set it to maxcontentfilecachescansize
# This option may be ignored by the configured download manager.
maxcontentramcachescansize = 2000



# Max content file cache scan size
# This is only used if you use a content scanner plugin such as AV
# This is the max size file that DG will download
# so that it can be scanned or virus checked.
# This value must be greater or equal to maxcontentramcachescansize.
# The size is in Kibibytes - eg 10240 = 10Mb
maxcontentfilecachescansize = 20000



# File cache dir
# Where DG will download files to be scanned if too large for the
# RAM cache.
filecachedir = '/tmp'



# Delete file cache after user completes download
# When a file gets save to temp it stays there until it is deleted.
# You can choose to have the file deleted when the user makes a sucessful
# download.  This will mean if they click on the link to download from
# the temp store a second time it will give a 404 error.
# You should configure something to delete old files in temp to stop it filling up.
# on|off (defaults to on)
deletedownloadedtempfiles = on



# Initial Trickle delay
# This is the number of seconds a browser connection is left waiting
# before first being sent *something* to keep it alive.  The
# *something* depends on the download manager chosen.
# Do not choose a value too low or normal web pages will be affected.
# A value between 20 and 110 would be sensible
# This may be ignored by the configured download manager.
initialtrickledelay = 20



# Trickle delay
# This is the number of seconds a browser connection is left waiting
# before being sent more *something* to keep it alive.  The
# *something* depends on the download manager chosen.
# This may be ignored by the configured download manager.
trickledelay = 10



# Download Managers
# These handle downloads of files to be filtered and scanned.
# They differ in the method they deal with large downloads.
# Files usually need to be downloaded 100% before they can be
# filtered and scanned before being sent on to the browser.
# Normally the browser can just wait, but with content scanning,
# for example to AV, the browser may timeout or the user may get
# confused so the download manager has to do some sort of
# 'keep alive'.
#
# There are various methods possible but not all are included.
# The author does not have the time to write them all so I have
# included a plugin systam.  Also, not all methods work with all
# browsers and clients.  Specifically some fancy methods don't
# work with software that downloads updates.  To solve this,
# each plugin can support a regular expression for matching
# the client's user-agent string, and lists of the mime types
# and extensions it should manage.
#
# Note that these are the matching methods provided by the base plugin
# code, and individual plugins may override or add to them.
# See the individual plugin conf files for supported options.
#
# The plugins are matched in the order you specify and the last
# one is forced to match as the default, regardless of user agent
# and other matching mechanisms.
#
downloadmanager = '/etc/dansguardian/downloadmanagers/fancy.conf'
#downloadmanager = '/etc/dansguardian/downloadmanagers/trickle.conf'
downloadmanager = '/etc/dansguardian/downloadmanagers/default.conf'



# Content Scanners (Also known as AV scanners)
# These are plugins that scan the content of all files your browser fetches
# for example to AV scan.  The options are limitless.  Eventually all of
# DansGuardian will be plugin based.  You can have more than one content
# scanner. The plugins are run in the order you specify.
# This is one of the few places you can have multiple options of the same name.
#
# Some of the scanner(s) require 3rd party software and libraries eg clamav.
# See the individual plugin conf file for more options (if any).
#
#contentscanner = '/etc/dansguardian/contentscanners/clamav.conf'
#!! Not compiled !! contentscanner = '/etc/dansguardian/contentscanners/clamdscan.conf'
#!! Unimplemented !! contentscanner = '/etc/dansguardian/contentscanners/kavav.conf'
#!! Not compiled !! contentscanner = '/etc/dansguardian/contentscanners/kavdscan.conf'
#contentscanner = '/etc/dansguardian/contentscanners/icapscan.conf'
#contentscanner = '/etc/dansguardian/contentscanners/commandlinescan.conf'



# Content scanner timeout
# Some of the content scanners support using a timeout value to stop
# processing (eg AV scanning) the file if it takes too long.
# If supported this will be used.
# The default of 60 seconds is probably reasonable.
contentscannertimeout = 60



# Content scan exceptions
# If 'on' exception sites, urls, users etc will be scanned
# This is probably not desirable behavour as exceptions are
# supposed to be trusted and will increase load.
# Correct use of grey lists are a better idea.
# (on|off) default = off
contentscanexceptions = off



# Auth plugins
# These replace the usernameidmethod* options in previous versions. They
# handle the extraction of client usernames from various sources, such as
# Proxy-Authorisation headers and ident servers, enabling requests to be
# handled according to the settings of the user's filter group.
# Multiple plugins can be specified, and will be queried in order until one
# of them either finds a username or throws an error. For example, if Squid
# is configured with both NTLM and Basic auth enabled, and both the 'proxy-basic'
# and 'proxy-ntlm' auth plugins are enabled here, then clients which do not support
# NTLM can fall back to Basic without sacrificing access rights.
#
# If you do not use multiple filter groups, you need not specify this option.
#
#authplugin = '/etc/dansguardian/authplugins/proxy-basic.conf'
#authplugin = '/etc/dansguardian/authplugins/proxy-digest.conf'
#authplugin = '/etc/dansguardian/authplugins/proxy-ntlm.conf'
#authplugin = '/etc/dansguardian/authplugins/ident.conf'
#authplugin = '/etc/dansguardian/authplugins/ip.conf'



# Re-check replaced URLs
# As a matter of course, URLs undergo regular expression search/replace (urlregexplist)
# *after* checking the exception site/URL/regexpURL lists, but *before* checking against
# the banned site/URL lists, allowing certain requests that would be matched against the
# latter in their original state to effectively be converted into grey requests.
# With this option enabled, the exception site/URL/regexpURL lists are also re-checked
# after replacement, making it possible for URL replacement to trigger exceptions based
# on them.
# Defaults to off.
recheckreplacedurls = off



# Misc settings

# if on it adds an X-Forwarded-For: <clientip> to the HTTP request
# header.  This may help solve some problem sites that need to know the
# source ip. on | off
forwardedfor = off


# if on it uses the X-Forwarded-For: <clientip> to determine the client
# IP. This is for when you have squid between the clients and DansGuardian.
# Warning - headers are easily spoofed. on | off
usexforwardedfor = off


# if on it logs some debug info regarding fork()ing and accept()ing which
# can usually be ignored.  These are logged by syslog.  It is safe to leave
# it on or off
logconnectionhandlingerrors = on



# Fork pool options

# If on, this causes DG to write to the log file whenever child processes are
# created or destroyed (other than by crashes). This information can help in
# understanding and tuning the following parameters, but is not generally
# useful in production.
logchildprocesshandling = off

# sets the maximum number of processes to spawn to handle the incoming
# connections.  Max value usually 250 depending on OS.
# On large sites you might want to try 180.
maxchildren = 120


# sets the minimum number of processes to spawn to handle the incoming connections.
# On large sites you might want to try 32.
minchildren = 8


# sets the minimum number of processes to be kept ready to handle connections.
# On large sites you might want to try 8.
minsparechildren = 4


# sets the minimum number of processes to spawn when it runs out
# On large sites you might want to try 10.
preforkchildren = 6


# sets the maximum number of processes to have doing nothing.
# When this many are spare it will cull some of them.
# On large sites you might want to try 64.
maxsparechildren = 32


# sets the maximum age of a child process before it croaks it.
# This is the number of connections they handle before exiting.
# On large sites you might want to try 10000.
maxagechildren = 500


# Sets the maximum number client IP addresses allowed to connect at once.
# Use this to set a hard limit on the number of users allowed to concurrently
# browse the web. Set to 0 for no limit, and to disable the IP cache process.
maxips = 0



# Process options
# (Change these only if you really know what you are doing).
# These options allow you to run multiple instances of DansGuardian on a single machine.
# Remember to edit the log file path above also if that is your intention.

# IPC filename
# 
# Defines IPC server directory and filename used to communicate with the log process.
ipcfilename = '/tmp/.dguardianipc'

# URL list IPC filename
# 
# Defines URL list IPC server directory and filename used to communicate with the URL
# cache process.
urlipcfilename = '/tmp/.dguardianurlipc'

# IP list IPC filename
#
# Defines IP list IPC server directory and filename, for communicating with the client
# IP cache process.
ipipcfilename = '/tmp/.dguardianipipc'

# PID filename
# 
# Defines process id directory and filename.
#pidfilename = '/var/run/dansguardian.pid'

# Disable daemoning
# If enabled the process will not fork into the background.
# It is not usually advantageous to do this.
# on|off (defaults to off)
nodaemon = off

# Disable logging process
# on|off (defaults to off)
nologger = off

# Enable logging of "ADs" category blocks
# on|off (defaults to off)
logadblocks = off

# Enable logging of client User-Agent
# Some browsers will cause a *lot* of extra information on each line!
# on|off (defaults to off)
loguseragent = off

# Daemon runas user and group
# This is the user that DansGuardian runs as.  Normally the user/group nobody.
# Uncomment to use.  Defaults to the user set at compile time.
# Temp files created during virus scanning are given owner and group read
# permissions; to use content scanners based on external processes, such as
# clamdscan, the two processes must run with either the same group or user ID.
#daemonuser = 'dansguardian'
#daemongroup = 'dansguardian'

# Soft restart
# When on this disables the forced killing off all processes in the process group.
# This is not to be confused with the -g run time option - they are not related.
# on|off (defaults to off)
softrestart = off

# Mail program
# Path (sendmail-compatible) email program, with options.
# Not used if usesmtp is disabled (filtergroup specific).
mailer = '/usr/sbin/sendmail -t'

```

**My dhcpd.conf**
```
#
# Sample configuration file for ISC dhcpd for Debian
#
# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as
# configuration file instead of this file.
#
# $Id: dhcpd.conf,v 1.1.1.1 2002/05/21 00:07:44 peloy Exp $
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style none;

#gg between #gg is added for bcls-proxy
authoritive;
option domain-name "bcls-proxy.org";
option domain-name-servers 10.1.10.1, 68.87.74.162, 192.168.5.1;
default-lease-time 1440;
max-lease-time 4200;
log-facility local7;
subnet 192.168.5.0 netmask 255.255.255.0 {
option domain-name-servers 10.1.10.1, 68.87.74.162, 192.168.5.1;
option broadcast-address 192.168.5.255;
option subnet-mask 255.255.255.0;
option routers 192.168.5.1;
range 192.168.5.100 192.168.5.200;
}
#gg end
 

# option definitions common to all supported networks...
#gg option domain-name "example.org";
#gg option domain-name-servers ns1.example.org, ns2.example.org;

#gg default-lease-time 600;
#gg max-lease-time 7200;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
#authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
#log-facility local7;

# No service will be given on this subnet, but declaring it helps the 
# DHCP server to understand the network topology.

#subnet 10.152.187.0 netmask 255.255.255.0 {
#}

# This is a very basic subnet declaration.

#subnet 10.254.239.0 netmask 255.255.255.224 {
#  range 10.254.239.10 10.254.239.20;
#  option routers rtr-239-0-1.example.org, rtr-239-0-2.example.org;
#}

# This declaration allows BOOTP clients to get dynamic addresses,
# which we don't really recommend.

#subnet 10.254.239.32 netmask 255.255.255.224 {
#  range dynamic-bootp 10.254.239.40 10.254.239.60;
#  option broadcast-address 10.254.239.31;
#  option routers rtr-239-32-1.example.org;
#}

# A slightly different configuration for an internal subnet.
#subnet 10.5.5.0 netmask 255.255.255.224 {
#  range 10.5.5.26 10.5.5.30;
#  option domain-name-servers ns1.internal.example.org;
#  option domain-name "internal.example.org";
#  option routers 10.5.5.1;
#  option broadcast-address 10.5.5.31;
#  default-lease-time 600;
#  max-lease-time 7200;
#}

# Hosts which require special configuration options can be listed in
# host statements.   If no address is specified, the address will be
# allocated dynamically (if possible), but the host-specific information
# will still come from the host declaration.

#host passacaglia {
#  hardware ethernet 0:0:c0:5d:bd:95;
#  filename "vmunix.passacaglia";
#  server-name "toccata.fugue.com";
#}

# Fixed IP addresses can also be specified for hosts.   These addresses
# should not also be listed as being available for dynamic assignment.
# Hosts for which fixed IP addresses have been specified can boot using
# BOOTP or DHCP.   Hosts for which no fixed address is specified can only
# be booted with DHCP, unless there is an address range on the subnet
# to which a BOOTP client is connected which has the dynamic-bootp flag
# set.
#host fantasia {
#  hardware ethernet 08:00:07:26:c0:a5;
#  fixed-address fantasia.fugue.com;
#}

# You can declare a class of clients and then do address allocation
# based on that.   The example below shows a case where all clients
# in a certain class get addresses on the 10.17.224/24 subnet, and all
# other clients get addresses on the 10.0.29/24 subnet.

#class "foo" {
#  match if substring (option vendor-class-identifier, 0, 4) = "SUNW";
#}

#shared-network 224-29 {
#  subnet 10.17.224.0 netmask 255.255.255.0 {
#    option routers rtr-224.example.org;
#  }
#  subnet 10.0.29.0 netmask 255.255.255.0 {
#    option routers rtr-29.example.org;
#  }
#  pool {
#    allow members of "foo";
#    range 10.17.224.10 10.17.224.250;
#  }
#  pool {
#    deny members of "foo";
#    range 10.0.29.10 10.0.29.230;
#  }
#}
```

and finally
**My /etc/network/interfaces**

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#gg iface eth0 inet dhcp
iface eth0 inet static
address 10.1.10.205
netmask 255.255.255.0
network 10.1.10.0
broadcast 10.1.10.255
gateway 10.1.10.1

auto eth1
iface eth1 inet static
address 192.168.5.1
netmask 255.255.255.0
network 192.168.5.0
broadcast 192.168.5.255
gateway 10.1.10.1
```

Thanks in advance for your help!!!

---

### Post by KIAaze on 2009-06-04
> **mdbarton said:**
> Will adding these sources:
```
deb http://ppa.launchpad.net/zohn-joidberg/ubuntu **intrepid** main
deb-src http://ppa.launchpad.net/zohn-joidberg/ubuntu **intrepid** main 
```
work on Jaunty?  or is this Intrepid only?

Sorry for the delay. I wanted to make new packages for Jaunty before replying, but now I just copied the packages to the Jaunty PPA: [https://launchpad.net/~zohn-joidberg/+archive/ppa](https://launchpad.net/~zohn-joidberg/+archive/ppa)
Haven't tested installation yet, but the packages are exactly the same so it should work.

@popaye85:
I don't know if I'll be able to help you with this. I don't even understand what your network is like and I'm not good with networking related issues at all. :/

Did you install WCC on your server? Or on a PC you use, but which provides internet to other machines via a second network card?

I'm really busy at work at the moment, so I don't think I'll be able to work on WCC for a while now. :(

---

### Post by popaye85 on 2009-06-05
> **KIAaze said:**
> @popaye85:
I don't know if I'll be able to help you with this. I don't even understand what your network is like and I'm not good with networking related issues at all. :/

**Did you install WCC on your server? Or on a PC you use, but which provides internet to other machines via a second network card?**


I installed on a small second machine (with two network cards) that I want to use as a transparent network proxy/filter for the rest of the internal network (for a small school).

Thanks again for any help you may have time to offer.

---

### Post by Scarletgecko on 2009-06-06
Which file or config screen do I need to modify to turn off the "Japanese Porn" filter?

Thank you.

-p:)

---

### Post by KIAaze on 2009-06-06
/etc/dansguardian/lists/weightedphraselist
```

...
##.Include</etc/dansguardian/lists/phraselists/pornography/weighted_japanese> #ALPHA#
...

```

It was already written in the FAQ in the initial post. ;)

---

### Post by team.hn@gmail.com on 2009-08-19
Is it possible to access Webcontencontrol remotely?

I've just installed it as well as DG and Squid on a Ubuntu x64 server (version 9), and would really love to be to access WCC from my PC. Since this is the server edition, I'd like to skip the GUI install if I can.

Thank you kindly!

---

### Post by KIAaze on 2009-08-20
Well you can access the server over ssh and then use it from there (ssh -X for graphical interface)...
There is currently no other way.

---

### Post by KIAaze on 2009-09-26
v1.3.0 released:
[https://launchpad.net/webcontentcontrol/+announcement/3878](https://launchpad.net/webcontentcontrol/+announcement/3878)

---

### Post by KIAaze on 2009-09-28
v1.3.2 released:
[https://launchpad.net/webcontentcontrol/+announcement/3890](https://launchpad.net/webcontentcontrol/+announcement/3890)

---

### Post by shinkaide on 2009-09-30
Hello, I've a question regarding the use of the filter groups list.

I'm currently using web content control on a single machine (9.04) with multiple users. I'm trying to give different users different ways of accessing the internet (some can't access specific sites, some can access everything else) through the machine.

This is [the tutorial I'm currently following]("http://www.opensourcehowto.org/how-to/dansguardian/dansguardian-with-different-filter-groups.html") (it's a bit dated, so there may be something it and I am missing).

I've followed the tutorial to the letter, with the exception of copying the list files: the tutorial doesn't take into account the new version's folder hierarchy of putting the list files in the "list" folder, so I compensated for that (copying files to fg2/lists/*.* as per the howto).

I've set the filter groups list option in dansguardian.conf to "2".

I've set my filtergroupslist file (the one in the /etc/dansguardian/lists/... and the one in /etc/dansguardian/fg2/lists/... ) to read as so:


```
andre=filter2
bianca=filter2
jesh=filter1
test=filter1
```

However, regardless of which account I use, all users default to using the primary bannedsitelist, which blocks a number of sites. 

The filter groups list method doesn't seem to work with how I've done it... help, please? What am I doing wrong?

---

### Post by KIAaze on 2009-10-01
**You must set up an authentication method** for this.
Therefore, you need an explicit proxy, which means **you cannot use tinyproxy** (transparent proxying). Use squid instead.

WCC doesn't directly support squid yet unfortunately, so you'll have to set it up manually.

cf here for an example configuration of squid + DG + multiple filter groups:
[http://tech.groups.yahoo.com/group/dansguardian/message/22651](http://tech.groups.yahoo.com/group/dansguardian/message/22651)

I also just uploaded the corresponding reference files to the bazaar repository in [reference/superconfig]("http://bazaar.launchpad.net/~zohn-joidberg/webcontentcontrol/main/files/head%3A/reference/superconfig/").

For more (up to date) info about setting up authentication and multiple filter groups, please refer to the dansguardian wiki:
[http://contentfilter.futuragts.com/wiki/doku.php?id=Main%20Index](http://contentfilter.futuragts.com/wiki/doku.php?id=Main%20Index)

(They recommend webmin + the webmin dansguardian module for easy configuration. I don't know if it also sets up squid however.)

P.S.: Never forget to restart services after configuring them. ;)
```
sudo /etc/init.d/SERVICE restart
sudo service SERVICE restart

```

edit: A while back I added custom proxy support. I just updated the original post to mention this:
> **KIAaze said:**
> Using a custom proxy (like squid):
I added the possibility to disable filtering configuration during install, as well as choose a custom proxy!

Just do the following to use squid instead of tinyproxy:
```
bzr branch lp:webcontentcontrol
cd webcontentcontrol
./configure --with-proxy=squid --disable-config  && make && sudo make install

```

For now you'll have to configure the .conf files yourself of course.
But at least, you'll be able to use the GUI to start/stop the filtering and open the .conf files.
Setting ports will probably not work correctly since it was made for tinyproxy.conf.

Please let me know how it works and also post your squid.conf, so I can adapt the install process for it (if you want to have a go at it yourself, look at WCCDIR/scripts/install.sh). ;)
If it works, I'll make a quick release of it.


---

### Post by Clayton South on 2009-10-13
Hello,

Thanks for this great program. A couple of questions:

I am running 9.04 and with the recent updates, dansguardian no longer seems to be working. I decided to reformat and re-install and give dansguardian install another shot.

I downloaded the newest release from the website to my desktop, extracted them to their own directory on the desktop. Then, I went in, copied the files, and pasted them into the /etc/dansguardian directory.  When I followed the instructions in the readme file ./configure etc etc I got several errors. One was a 127 error and the other was error 2. 

Advice? I really like this program and need to continue to use it, so if you could please enlighten me that would be awesome.

-Clayton South

---

### Post by marius_brkt on 2009-10-16
Thks for all

I've installed webcontentcontrol ( Ubuntu 9.04, amd64) all is OK, block all I need, until the next restart when the program doesn't wants to start automatically..I have to click on the icon to start it..:(( ..I tried to read the manual, but theres no manual..:((..when I click on Help -> manual, nothing's happening...

anyone who encountered the same problem?

---

### Post by KIAaze on 2009-10-19
> **Clayton South said:**
> 
I downloaded the newest release from the website to my desktop, extracted them to their own directory on the desktop. Then, I went in, copied the files, and pasted them into the /etc/dansguardian directory.  When I followed the instructions in the readme file ./configure etc etc I got several errors. One was a 127 error and the other was error 2. 

The error text (or the complete text from the installation process) would be more helpful to me than the error numbers. ;)

Also, how did you install the program the first time?
You should follow the instructions I gave in the initial post: [http://ubuntuforums.org/showthread.php?t=843510](http://ubuntuforums.org/showthread.php?t=843510)
(I recommend using the PPA.)

Extracting the source code in /etc/dansguardian is not a good idea!
Just extract it on your desktop or in your home directory and install from there.

> Thks for all

I've installed webcontentcontrol ( Ubuntu 9.04, amd64) all is OK, block all I need, until the next restart when the program doesn't wants to start automatically..I have to click on the icon to start it..( ..I tried to read the manual, but theres no manual..(..when I click on Help -> manual, nothing's happening...

anyone who encountered the same problem? 
I haven't created any manual yet, so it's normal that it doesn't work when you click on it.

And what do you mean by it doesn't start automatically?
Webcontentcontrol is just a user interface. It does not need to be run at startup (there is (currently) no icon in the system tray showing that it is running like with most programs in Windows).

What should run on startup however are the following services:
-dansguardian (the real content filter)
-tinyproxy (proxy)
-firehol (firewall (not necessary if browser set to use the filter port directly))

Check the buttons in "advanced settings"->"services" to make sure that those services run on startup.

Also, what language are you running webcontentcontrol in? Or what is your system language?
I only recently implemented translations, so it's possible that using languages other than English introduce some new bugs.

edit: Thanks for the bug report. I copied my answer there. ;)
[https://bugs.launchpad.net/webcontentcontrol/+bug/451077](https://bugs.launchpad.net/webcontentcontrol/+bug/451077)

---

### Post by kd5jnx on 2009-10-20
Maybe I'm missing something simple, but after installing WCC my LTSP clients can no longer boot from the LTSP server. They are receiving IP addresses but stop after that. I am running Jaunty/LTSP/Edubuntu. Everything works great on the server but my kids clients wont boot now unless i turn off WCC.

Thanks in advance.

---

### Post by newbie2 on 2009-10-29
Maybe canonical could have a 'sponsorship' with this [CEOP]("http://www.ceop.gov.uk/") ... good advertising me thinks... ;)

---

### Post by The_Weaver on 2009-11-03
Hi, installed this, but there does not appear to any password protection to turn this off. (ie when I open up the GUI I have full control to change fvilter options & to turn off the proptection. I'm using the 1.3.2 in Jaunty. Thanks

---

### Post by KIAaze on 2009-11-03
> **The_Weaver said:**
> Hi, installed this, but there does not appear to any password protection to turn this off. (ie when I open up the GUI I have full control to change fvilter options & to turn off the proptection. I'm using the 1.3.2 in Jaunty. Thanks

This is probably because you used sudo/gksu/kdesudo before running the GUI, so you still have superuser privileges.
sudo has a timeout of about 5 minutes by default I think.
Use "sudo -k" to make sure the password is requested again.

---

### Post by dawynn on 2009-11-04
Seeing a number of instances of blank pages -- no error text, but the requested page does not come up.

Also, when I load the wcc control screen, most of it does not appear.  I'm wondering if this is just a matter of trying to use Jaunty version of wcc in Karmic.  (Perhaps an older Jaunty version too, since I updated all of my repositories to Karmic, and am just accepting the "not found" error messages for now)

Is there an ETA on a Karmic version?

---

### Post by KIAaze on 2009-11-04
Yes, I have the same problem with the blank pages since upgrading to Karmic. I hope it's just a matter of reinstalling dansguardian, but haven't tested it yet.
This also means I'll probably bring out a Karmic package soon. ;)

> Also, when I load the wcc control screen, most of it does not appear. I'm wondering if this is just a matter of trying to use Jaunty version of wcc in Karmic.

Could you please post a screenshot of it?

---

### Post by dawynn on 2009-11-06
I'm attaching the screen shot.  Notice the left column of configuration settings.  I get just a hint that there are settings there, and the rest is blank.

System:
1.4 ghx Athlon Classic
GeForce FX 5700LE
1 Gb memory installed.  (System max)

Key packages installed:
ubuntu-minimal
ubuntu-standard
ubuntu-restricted-extras
non-free-codecs
nvidia-glx-96 (the motherboard cannot handle later drivers)
lsb
lsb-languages
lsb-multimedia
lsb-qt4
lsb-security
lxde
linux
linux-generic
language-pack-en
language-support-en
gdm
webcontentcontrol

---

### Post by Kaaiman on 2009-11-10
When will WCC be added to the Karmic (ppa) repos?

---

### Post by Kalma on 2009-12-22
Hi again, guys,

as promissed, I wanted to come back to explain how it was using dansguardian + Squid + iptables... And after lots of hours, it finally works!!!!

I've been able to configure Squid to request a password, then I have configured several filtergroups, assigning different profiles to them (with different severity levels), and finally, configured iptables to re-direct th traffic, thus allowing both Squid and Dansguardian to work together.

I know this configuration is not WCC, but it is the only one I got to have different profiles at the moment. Maybe a WCC2.0?

Again, thank you very much for your effort.

---

### Post by KIAaze on 2009-12-22
Thanks.
Could you post the corresponding config files too to make things easier? :)

> **dawynn said:**
> I'm attaching the screen shot.  Notice the left column of configuration settings.  I get just a hint that there are settings there, and the rest is blank.

I had the same bug once.
Resizing/maximizing the window allowed me to see everything again.
I'll try to look into it.

> **Kaaiman said:**
> When will WCC be added to the Karmic (ppa) repos?
I don't know. ^^'
I haven't been using it for a while now, which reduced development unfortunately.
I had the problem about some allowed pages being blank. I think it's a dansguardian problem, but it disqualifies WCC for permanent use. :(

---

### Post by Kalma on 2009-12-24
Of course.

I am not sure how to do that. I have attached the 5 modified files, compressed into a tar.gz file... If it doesn't work, please let me know.

Some short notes:

- squid.conf
I have used ncsa_auth as authentication method. Other methods are also suitable, but I got it working with this one. This requires to create a password file, using webmin or chpasswd (webmin is easier).
Note I have added the option "password" to all http_address entries, since I was not sure exactly where it was required (maybe somebody else could help to optimize it).

- dansguardian.conf
Here is where you may indicate there are various filtergroups. I am using 2:
filtergroups = 2
filtergroupslist = '/etc/dansguardian/lists/filtergroupslist'

and also, indicate the appropriate ports:
# the port that DansGuardian listens to.
filterport = 8080
# the ip of the proxy (default is the loopback - i.e. this server)
proxyip = 127.0.0.1
# the port DansGuardian connects to proxy on
proxyport = 3128

Finally, I uncommented the line referred to the authentication (otherwise it will not work). In my case "basic":
authplugin = '/etc/dansguardian/authplugins/proxy-basic.conf'

The port 80 should be redirected to 8080 by using iptables:
iptables -A PREROUTING -t nat -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 8080

- dansguardianf1.conf
Here you indicate which filtering and exception files to use for filtergroup 1 (the most restrictive)
-dansguardianf2.conf
Here you indicate which filtering and exception files to  use for filtergroup 2. In my case, this is for adults, so no filtering is selected, then no files are needed,

-filtergroupslist
Here you define which user belongs to which filter group. If the user is not listed, then the first filter group is assigned by default. This is why the group 1 should be the most restrictive.

- Proxy Settings:
In order to have everything working without other complex configurations, the general system settings are set to "NO Proxy" (this applies to apt, and other applications like screenlets and so on), then in the firefox and the aMSN configuration for every user, the Squid proxy is selected (thus filtering only firefox and aMSN). After doing this, I locked the firefox configuration by applying this post:


This configuration is working fine for me, because of two reasons:
- It is enough for families with two groups: kids and adults
- The other users are not experts, so I am quite sure they will not override these confs

Hope this helps!!! Let me know if you need further information or anything I can help.

---

### Post by Kalma on 2009-12-24
I'm affraid the attachement didn't work. I will try again. If it doesn't, I have no more ideas, any help will be welcome.

---

### Post by alby241992 on 2009-12-29
Hello!
I don't speack english very well.
I have tried to follow this guide for install an software parental control.

If i type this comand:
```
sudo apt-get install webcontentcontrol
```

this is the result:
```
I seguenti pacchetti NUOVI (NEW) saranno installati:
  webcontentcontrol
0 aggiornati, 1 installati, 0 da rimuovere e 323 non aggiornati.
È necessario prendere 0B/981kB di archivi.
Dopo quest'operazione, verranno occupati 1929kB di spazio su disco.
Selezionato il pacchetto webcontentcontrol, che non lo era.
(Lettura del database ... 194497 file e directory attualmente installati.)
Spacchetto webcontentcontrol (da .../webcontentcontrol_1.3.2-0ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Configuro webcontentcontrol (1.3.2-0ubuntu1) ...
===>postinst:configure
-->install-data-hook target called
Adapting scripts (path)...
Configuring dansguardian+firehol+tinyproxy
Running from /
===>exporting /usr/share/webcontentcontrol/backup.dgs.full
/etc/dansguardian/dansguardian.conf
/etc/firehol/firehol.conf
/etc/tinyproxy/tinyproxy.conf
/etc/init.d/dansguardian
/etc/default/firehol
/etc/squid/squid.conf
tar: /etc/squid3/squid.conf: funzione "stat" non riuscita: Nessun file o directory
tar: /etc/squid/squidGuard.conf: funzione "stat" non riuscita: Nessun file o directory
tar: /var/lib/squidguard/db/weapons/domains: funzione "stat" non riuscita: Nessun file o directory
/etc/dansguardian/lists/
/etc/dansguardian/lists/bannedsitelist
/etc/dansguardian/lists/bannedregexpheaderlist
/etc/dansguardian/lists/contentregexplist
/etc/dansguardian/lists/bannedurllist
/etc/dansguardian/lists/exceptionextensionlist
/etc/dansguardian/lists/bannediplist
/etc/dansguardian/lists/phraselists/
/etc/dansguardian/lists/phraselists/weapons/
/etc/dansguardian/lists/phraselists/weapons/weighted_portuguese
/etc/dansguardian/lists/phraselists/weapons/weighted
/etc/dansguardian/lists/phraselists/games/
/etc/dansguardian/lists/phraselists/games/weighted
/etc/dansguardian/lists/phraselists/gambling/
/etc/dansguardian/lists/phraselists/gambling/banned_portuguese
/etc/dansguardian/lists/phraselists/gambling/weighted_portuguese
/etc/dansguardian/lists/phraselists/gambling/banned
/etc/dansguardian/lists/phraselists/gambling/weighted
/etc/dansguardian/lists/phraselists/upstreamfilter/
/etc/dansguardian/lists/phraselists/upstreamfilter/weighted
/etc/dansguardian/lists/phraselists/chat/
/etc/dansguardian/lists/phraselists/chat/weighted_italian
/etc/dansguardian/lists/phraselists/chat/weighted
/etc/dansguardian/lists/phraselists/idtheft/
/etc/dansguardian/lists/phraselists/idtheft/weighted
/etc/dansguardian/lists/phraselists/conspiracy/
/etc/dansguardian/lists/phraselists/conspiracy/weighted
/etc/dansguardian/lists/phraselists/music/
/etc/dansguardian/lists/phraselists/music/weighted
/etc/dansguardian/lists/phraselists/violence/
/etc/dansguardian/lists/phraselists/violence/weighted_portuguese
/etc/dansguardian/lists/phraselists/violence/weighted
/etc/dansguardian/lists/phraselists/rta/
/etc/dansguardian/lists/phraselists/rta/banned
/etc/dansguardian/lists/phraselists/travel/
/etc/dansguardian/lists/phraselists/travel/weighted
/etc/dansguardian/lists/phraselists/pornography/
/etc/dansguardian/lists/phraselists/pornography/banned_portuguese
/etc/dansguardian/lists/phraselists/pornography/weighted_danish
/etc/dansguardian/lists/phraselists/pornography/weighted_italian
/etc/dansguardian/lists/phraselists/pornography/weighted_chinese
/etc/dansguardian/lists/phraselists/pornography/weighted_polish
/etc/dansguardian/lists/phraselists/pornography/weighted_spanish
/etc/dansguardian/lists/phraselists/pornography/weighted_german
/etc/dansguardian/lists/phraselists/pornography/weighted_dutch
/etc/dansguardian/lists/phraselists/pornography/weighted_portuguese
/etc/dansguardian/lists/phraselists/pornography/banned
/etc/dansguardian/lists/phraselists/pornography/weighted_russian
/etc/dansguardian/lists/phraselists/pornography/weighted
/etc/dansguardian/lists/phraselists/pornography/weighted_malay
/etc/dansguardian/lists/phraselists/pornography/weighted_norwegian
/etc/dansguardian/lists/phraselists/pornography/weighted_japanese
/etc/dansguardian/lists/phraselists/pornography/weighted_french
/etc/dansguardian/lists/phraselists/translation/
/etc/dansguardian/lists/phraselists/translation/weighted
/etc/dansguardian/lists/phraselists/badwords/
/etc/dansguardian/lists/phraselists/badwords/weighted_spanish
/etc/dansguardian/lists/phraselists/badwords/weighted_german
/etc/dansguardian/lists/phraselists/badwords/weighted_dutch
/etc/dansguardian/lists/phraselists/badwords/weighted_portuguese
/etc/dansguardian/lists/phraselists/badwords/weighted_french
/etc/dansguardian/lists/phraselists/illegaldrugs/
/etc/dansguardian/lists/phraselists/illegaldrugs/weighted_portuguese
/etc/dansguardian/lists/phraselists/illegaldrugs/banned
/etc/dansguardian/lists/phraselists/illegaldrugs/weighted
/etc/dansguardian/lists/phraselists/domainsforsale/
/etc/dansguardian/lists/phraselists/domainsforsale/weighted
/etc/dansguardian/lists/phraselists/googlesearches/
/etc/dansguardian/lists/phraselists/googlesearches/banned
/etc/dansguardian/lists/phraselists/goodphrases/
/etc/dansguardian/lists/phraselists/goodphrases/exception
/etc/dansguardian/lists/phraselists/goodphrases/weighted_general_dutch
/etc/dansguardian/lists/phraselists/goodphrases/weighted_general
/etc/dansguardian/lists/phraselists/goodphrases/weighted_general_polish
/etc/dansguardian/lists/phraselists/goodphrases/weighted_general_danish
/etc/dansguardian/lists/phraselists/goodphrases/weighted_news
/etc/dansguardian/lists/phraselists/goodphrases/weighted_general_malay
/etc/dansguardian/lists/phraselists/goodphrases/exception_email
/etc/dansguardian/lists/phraselists/goodphrases/weighted_general_portuguese
/etc/dansguardian/lists/phraselists/forums/
/etc/dansguardian/lists/phraselists/forums/weighted
/etc/dansguardian/lists/phraselists/webmail/
/etc/dansguardian/lists/phraselists/webmail/weighted
/etc/dansguardian/lists/phraselists/peer2peer/
/etc/dansguardian/lists/phraselists/peer2peer/weighted
/etc/dansguardian/lists/phraselists/news/
/etc/dansguardian/lists/phraselists/news/weighted
/etc/dansguardian/lists/phraselists/safelabel/
/etc/dansguardian/lists/phraselists/safelabel/banned
/etc/dansguardian/lists/phraselists/proxies/
/etc/dansguardian/lists/phraselists/proxies/weighted
/etc/dansguardian/lists/phraselists/secretsocieties/
/etc/dansguardian/lists/phraselists/secretsocieties/weighted
/etc/dansguardian/lists/phraselists/legaldrugs/
/etc/dansguardian/lists/phraselists/legaldrugs/weighted
/etc/dansguardian/lists/phraselists/warezhacking/
/etc/dansguardian/lists/phraselists/warezhacking/weighted
/etc/dansguardian/lists/phraselists/sport/
/etc/dansguardian/lists/phraselists/sport/weighted
/etc/dansguardian/lists/phraselists/intolerance/
/etc/dansguardian/lists/phraselists/intolerance/banned_portuguese
/etc/dansguardian/lists/phraselists/intolerance/weighted_portuguese
/etc/dansguardian/lists/phraselists/intolerance/weighted
/etc/dansguardian/lists/phraselists/gore/
/etc/dansguardian/lists/phraselists/gore/weighted_portuguese
/etc/dansguardian/lists/phraselists/gore/weighted
/etc/dansguardian/lists/phraselists/drugadvocacy/
/etc/dansguardian/lists/phraselists/drugadvocacy/weighted
/etc/dansguardian/lists/phraselists/malware/
/etc/dansguardian/lists/phraselists/malware/weighted
/etc/dansguardian/lists/phraselists/personals/
/etc/dansguardian/lists/phraselists/personals/weighted_portuguese
/etc/dansguardian/lists/phraselists/personals/weighted
/etc/dansguardian/lists/phraselists/nudism/
/etc/dansguardian/lists/phraselists/nudism/weighted
/etc/dansguardian/lists/bannedphraselist
/etc/dansguardian/lists/exceptionsitelist
/etc/dansguardian/lists/exceptionfilesitelist
/etc/dansguardian/lists/exceptionurllist
/etc/dansguardian/lists/pics
/etc/dansguardian/lists/exceptionfileurllist
/etc/dansguardian/lists/blacklists/
/etc/dansguardian/lists/blacklists/ads/
/etc/dansguardian/lists/blacklists/ads/urls
/etc/dansguardian/lists/blacklists/ads/domains.processed
/etc/dansguardian/lists/blacklists/ads/domains
/etc/dansguardian/lists/logsitelist
/etc/dansguardian/lists/exceptioniplist
/etc/dansguardian/lists/logurllist
/etc/dansguardian/lists/exceptionregexpurllist
/etc/dansguardian/lists/exceptionmimetypelist
/etc/dansguardian/lists/logregexpurllist
/etc/dansguardian/lists/bannedmimetypelist
/etc/dansguardian/lists/exceptionphraselist
/etc/dansguardian/lists/greysitelist
/etc/dansguardian/lists/bannedextensionlist
/etc/dansguardian/lists/authplugins/
/etc/dansguardian/lists/authplugins/ipgroups
/etc/dansguardian/lists/greyurllist
/etc/dansguardian/lists/filtergroupslist
/etc/dansguardian/lists/urlregexplist
/etc/dansguardian/lists/downloadmanagers/
/etc/dansguardian/lists/downloadmanagers/managedmimetypelist
/etc/dansguardian/lists/downloadmanagers/managedextensionlist
/etc/dansguardian/lists/weightedphraselist
/etc/dansguardian/lists/contentscanners/
/etc/dansguardian/lists/contentscanners/exceptionvirusurllist
/etc/dansguardian/lists/contentscanners/exceptionvirussitelist
/etc/dansguardian/lists/contentscanners/exceptionvirusmimetypelist
/etc/dansguardian/lists/contentscanners/exceptionvirusextensionlist
/etc/dansguardian/lists/bannedregexpurllist
/etc/dansguardian/lists/headerregexplist
tar: /etc/tinyproxy/filter: funzione "stat" non riuscita: Nessun file o directory
/usr/share/doc/firefox-3.0/firefox.cfg
/etc/firefox-3.0/pref/firefox.js
tar: /etc/firefox/pref/firefox.js: funzione "stat" non riuscita: Nessun file o directory
/etc/firefox-3.0/pref/firefox.js
tar: /opt/swiftfox/defaults/pref/firefox.js: funzione "stat" non riuscita: Nessun file o directory
tar: /usr/lib/firefox-3.0.3/defaults/preferences/firefox.js: funzione "stat" non riuscita: Nessun file o directory
tar: /usr/lib/firefox/firefox.cfg: funzione "stat" non riuscita: Nessun file o directory
/usr/share/doc/firefox-3.0/firefox.cfg
tar: Uscita per errore ritardata dall'errore precedente
Running from /
===>exported /usr/share/webcontentcontrol/backup.dgs.full
ON
START_FIREHOL=YES
START_FIREHOL=YES
version 5
PRESENT
iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP
PRESENT
MISSING
interface any world
PRESENT
policy drop
PRESENT
protection strong
PRESENT
   client all accept
PRESENT
server cups accept
PRESENT

Fetching IANA IPv4 Address Space, from:
http://www.iana.org/assignments/ipv4-address-space

aggregate: maximum prefix length permitted will be 32
--2009-12-28 18:39:27--  http://www.iana.org/assignments/ipv4-address-space
Risoluzione di www.iana.org... 208.77.188.193
Connessione a www.iana.org|208.77.188.193|:80... connesso.
HTTP richiesta inviata, in attesa di risposta... 301 Moved Permanently
Posizione: http://www.iana.org/assignments/ipv4-address-space/ [segue]
--2009-12-28 18:39:28--  http://www.iana.org/assignments/ipv4-address-space/
Connessione a www.iana.org|208.77.188.193|:80... connesso.
HTTP richiesta inviata, in attesa di risposta... 200 OK
Lunghezza: 31670 (31K) [text/plain]
Salvataggio in: "STDOUT"

100%[======================================>] 31.670      16,7K/s   in 1,8s   

2009-12-28 18:39:31 (16,7 KB/s) - "-" salvato [31670/31670]



FOUND THE FOLLOWING RESERVED IP RANGES:
RESERVED_IPS="0.0.0.0/7 5.0.0.0/8 10.0.0.0/8 14.0.0.0/8 23.0.0.0/8 27.0.0.0/8 31.0.0.0/8 36.0.0.0/7 39.0.0.0/8 42.0.0.0/8 49.0.0.0/8 50.0.0.0/8 100.0.0.0/6 104.0.0.0/6 127.0.0.0/8 176.0.0.0/7 179.0.0.0/8 181.0.0.0/8 185.0.0.0/8 223.0.0.0/8 240.0.0.0/4 "


Differences between the fetched list and the list installed in
/etc/firehol/RESERVED_IPS:
# diff /etc/firehol/RESERVED_IPS /tmp/iana.13023.180

No differences found.

User proxy
User proxy
Group proxy
Group proxy
Port 3128
Port 3128
STATUS: Dansguardian is unconfigured
STATUS: Dansguardian is configured
Configuration successful
proxyport=3128 filterport=8080
===========================================
setting ports
proxyport=3128
filterport=8080
========================
proxyport=3128
filterport=8080
===========================================
stopping all
* Stopping Firewall firehol                                             [ OK ]
Stopping tinyproxy: tinyproxy.
* Stopping DansGuardian dansguardian                                    [ OK ]
===========================================
starting all
* Starting Firewall firehol                                                   
--------------------------------------------------------------------------------
ERROR #: 1
WHAT   : Initializing transparent_proxy
WHY    : Previous work was not applied.
COMMAND: transparent_proxy 80 8080 proxy\ root
SOURCE : line INIT of /etc/firehol/firehol.conf


--------------------------------------------------------------------------------
ERROR #: 2
WHAT   : Initializing transparent_proxy
WHY    : transparent_proxy cannot be used in 'interface'. Put it before any 'interface' definition.
COMMAND: transparent_proxy 80 8080 proxy\ root
SOURCE : line INIT of /etc/firehol/firehol.conf


--------------------------------------------------------------------------------
ERROR #: 2
WHAT   : Initializing transparent_proxy
WHY    : Previous work was not applied.
COMMAND: transparent_proxy 80 8080 root\ root
SOURCE : line INIT of /etc/firehol/firehol.conf


--------------------------------------------------------------------------------
ERROR #: 3
WHAT   : Initializing transparent_proxy
WHY    : transparent_proxy cannot be used in 'interface'. Put it before any 'interface' definition.
COMMAND: transparent_proxy 80 8080 root\ root
SOURCE : line INIT of /etc/firehol/firehol.conf


NOTICE: No changes made to your firewall.
                                                                         [fail]
chown: utente non valido: "proxy\nproxy"
* Starting DansGuardian dansguardian                                    [ OK ]
===========================================
checking ports
FireHol is stopped
TinyProxy is stopped
DansGuardian is running
There was an error
===========================================
proxyport=3128 filterport=8081
===========================================
setting ports
proxyport=3128
filterport=8080
========================
proxyport=3128
filterport=8081
===========================================
stopping all
* Stopping Firewall firehol                                             [ OK ]
Stopping tinyproxy: tinyproxy.
* Stopping DansGuardian dansguardian                                    [ OK ]
===========================================
starting all
* Starting Firewall firehol                                                   
--------------------------------------------------------------------------------
ERROR #: 1
WHAT   : Initializing transparent_proxy
WHY    : Previous work was not applied.
COMMAND: transparent_proxy 80 8081 proxy\ root
SOURCE : line INIT of /etc/firehol/firehol.conf


--------------------------------------------------------------------------------
ERROR #: 2
WHAT   : Initializing transparent_proxy
WHY    : transparent_proxy cannot be used in 'interface'. Put it before any 'interface' definition.
COMMAND: transparent_proxy 80 8081 proxy\ root
SOURCE : line INIT of /etc/firehol/firehol.conf


--------------------------------------------------------------------------------
ERROR #: 2
WHAT   : Initializing transparent_proxy
WHY    : Previous work was not applied.
COMMAND: transparent_proxy 80 8081 root\ root
SOURCE : line INIT of /etc/firehol/firehol.conf


--------------------------------------------------------------------------------
ERROR #: 3
WHAT   : Initializing transparent_proxy
WHY    : transparent_proxy cannot be used in 'interface'. Put it before any 'interface' definition.
COMMAND: transparent_proxy 80 8081 root\ root
SOURCE : line INIT of /etc/firehol/firehol.conf


NOTICE: No changes made to your firewall.
                                                                         [fail]
chown: utente non valido: "proxy\nproxy"
* Starting DansGuardian dansguardian                                    [ OK ]
===========================================
checking ports
FireHol is stopped
TinyProxy is stopped
DansGuardian is running
There was an error
===========================================
proxyport=3129 filterport=8080
===========================================
setting ports
proxyport=3128
filterport=8081
========================
proxyport=3129
filterport=8080
===========================================
stopping all
* Stopping Firewall firehol                                             [ OK ]
Stopping tinyproxy: tinyproxy.
* Stopping DansGuardian dansguardian                                    [ OK ]
===========================================
starting all
* Starting Firewall firehol                                                   
--------------------------------------------------------------------------------
ERROR #: 1
WHAT   : Initializing transparent_proxy
WHY    : Previous work was not applied.
COMMAND: transparent_proxy 80 8080 proxy\ root
SOURCE : line INIT of /etc/firehol/firehol.conf


--------------------------------------------------------------------------------
ERROR #: 2
WHAT   : Initializing transparent_proxy
WHY    : transparent_proxy cannot be used in 'interface'. Put it before any 'interface' definition.
COMMAND: transparent_proxy 80 8080 proxy\ root
SOURCE : line INIT of /etc/firehol/firehol.conf


--------------------------------------------------------------------------------
ERROR #: 2
WHAT   : Initializing transparent_proxy
WHY    : Previous work was not applied.
COMMAND: transparent_proxy 80 8080 root\ root
SOURCE : line INIT of /etc/firehol/firehol.conf


--------------------------------------------------------------------------------
ERROR #: 3
WHAT   : Initializing transparent_proxy
WHY    : transparent_proxy cannot be used in 'interface'. Put it before any 'interface' definition.
COMMAND: transparent_proxy 80 8080 root\ root
SOURCE : line INIT of /etc/firehol/firehol.conf


NOTICE: No changes made to your firewall.
                                                                         [fail]
chown: utente non valido: "proxy\nproxy"
* Starting DansGuardian dansguardian                                           Error connecting to parent proxy
                                                                         [fail]
===========================================
checking ports
FireHol is stopped
TinyProxy is stopped
DansGuardian is stopped
There was an error
===========================================
proxyport=3129 filterport=8081
===========================================
setting ports
proxyport=3129
filterport=8080
========================
proxyport=3129
filterport=8081
===========================================
stopping all
* Stopping Firewall firehol                                             [ OK ]
Stopping tinyproxy: tinyproxy.
* Stopping DansGuardian dansguardian                                    [ OK ]
===========================================
starting all
* Starting Firewall firehol                                                   
--------------------------------------------------------------------------------
ERROR #: 1
WHAT   : Initializing transparent_proxy
WHY    : Previous work was not applied.
COMMAND: transparent_proxy 80 8081 proxy\ root
SOURCE : line INIT of /etc/firehol/firehol.conf


--------------------------------------------------------------------------------
ERROR #: 2
WHAT   : Initializing transparent_proxy
WHY    : transparent_proxy cannot be used in 'interface'. Put it before any 'interface' definition.
COMMAND: transparent_proxy 80 8081 proxy\ root
SOURCE : line INIT of /etc/firehol/firehol.conf


--------------------------------------------------------------------------------
ERROR #: 2
WHAT   : Initializing transparent_proxy
WHY    : Previous work was not applied.
COMMAND: transparent_proxy 80 8081 root\ root
SOURCE : line INIT of /etc/firehol/firehol.conf


--------------------------------------------------------------------------------
ERROR #: 3
WHAT   : Initializing transparent_proxy
WHY    : transparent_proxy cannot be used in 'interface'. Put it before any 'interface' definition.
COMMAND: transparent_proxy 80 8081 root\ root
SOURCE : line INIT of /etc/firehol/firehol.conf


NOTICE: No changes made to your firewall.
                                                                         [fail]
chown: utente non valido: "proxy\nproxy"
* Starting DansGuardian dansguardian                                           Error connecting to parent proxy
                                                                         [fail]
===========================================
checking ports
FireHol is stopped
TinyProxy is stopped
DansGuardian is stopped
There was an error
===========================================
Updating menus

```

This is the error that is repeated several times:
```
NOTICE: No changes made to your firewall.
                                                                   [fail]
chown: invalid user: "proxy\nproxy"
```

If i start webcontentcontrol by user interface this is result:
[[img]http://img257.imageshack.us/img257/3469/schermatawebcontentcont.th.png[/img]](http://img257.imageshack.us/i/schermatawebcontentcont.png/)
[[img]http://img697.imageshack.us/img697/3469/schermatawebcontentcont.th.png[/img]](http://img697.imageshack.us/i/schermatawebcontentcont.png/)

Why?

Thanks

---

### Post by KIAaze on 2010-01-12
@alby241992:
Sorry, I'm a little bit short on time lately.
I'll try to look into your problem as soon as I can.

_**Concerning the dansguardian + tinyproxy empty page bug on Ubuntu Karmic 9.10:**_
The solution is to downgrade to the Jaunty (9.04) version of dansguardian.

Perhaps installing the latest dansguardian from source might fix it too, but I haven't tried that.

To downgrade the dansguardian version:
1) Remove dansguardian```
sudo apt-get remove dansguardian
```
2) Download and install the jaunty version from here:
[http://packages.ubuntu.com/jaunty/dansguardian](http://packages.ubuntu.com/jaunty/dansguardian)
3) Reinstall webcontentcontrol

Bug reports:
[http://sourceforge.net/tracker/?func=detail&aid=2881442&group_id=131757&atid=722098](http://sourceforge.net/tracker/?func=detail&aid=2881442&group_id=131757&atid=722098)
[https://bugs.launchpad.net/ubuntu/+source/dansguardian/+bug/474475](https://bugs.launchpad.net/ubuntu/+source/dansguardian/+bug/474475)
Solution threads:
[http://swiss.ubuntuforums.org/showthread.php?p=8114293#post8114293](http://swiss.ubuntuforums.org/showthread.php?p=8114293#post8114293)
[http://newyork.ubuntuforums.org/showthread.php?t=1310351](http://newyork.ubuntuforums.org/showthread.php?t=1310351)

---

### Post by HarshReality on 2010-01-23
I have a mini 9 running Hardy.. anybody tell me how to work this out? I added the jaunty ppa to sources and I get the gambas2 etc. etc. Broken Packages

---

### Post by KIAaze on 2010-01-24
@alby241992:
Could you please post the output of the following commands:
```
dpkg -l *proxy*
cat /etc/tinyproxy/tinyproxy.conf
lsb_release -a
/etc/init.d/tinyproxy start

```

Also, do you know if you have any other proxy running? Do you have a special network setup?

> **HarshReality said:**
> I have a mini 9 running Hardy.. anybody tell me how to work this out? I added the jaunty ppa to sources and I get the gambas2 etc. etc. Broken Packages

Can you install the gambas2 package?
Which packages can't be installed or are broken?
Do those commands run without errors?:
```
sudo apt-get install gambas2-runtime gambas2-gb-qt gambas2-gb-form gambas2-gb-form-dialog gambas2-gb-qt-kde gambas2-gb-qt-kde-html
sudo apt-get install dansguardian tinyproxy firehol
```

---

### Post by mdbarton on 2010-02-08
I'm about to acquire a new laptop which I'll install 9.10 NBR on.  I've read around on the forums that the Karmic dansguardian packages are not working.  Is this still the case?  Should I install the Jaunty ones?

---

### Post by KIAaze on 2010-02-10
Last time I checked, it was still the case. So yes, use the Jaunty version of dansguardian.
If you want, you can try compiling the latest dansguardian version from source. I haven't tried that yet.

---

### Post by Script Warlock on 2010-06-26
@KIAaze, thanks for your effort on this project i tried to install it on lucid from [here]("https://launchpad.net/~zohn-joidberg/+archive/ppa/+packages") yes it worked but cant surf anymore. and then when remove the package this is what i got:

scripwarlock@scripwarlock-laptop:~$ sudo apt-get remove webcontentcontrolReading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gambas2-gb-form kdelibs4c2a kdelibs-data liblualib50 gambas2-gb-form-dialog
  gambas2-runtime kdelibs5-data gambas2-gb-qt libavahi-qt3-1
  gambas2-gb-qt-kde-html gambas2-gb-qt-kde libqt3-mt liblua50 gambas2-gb-gtk
  gambas2-gb-gui gambas2-gb-settings
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  webcontentcontrol
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 1,929kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 161029 files and directories currently installed.)
Removing webcontentcontrol ...
===>prerm:remove
prerm remove|deconfigure called
Unconfiguring dansguardian+firehol+tinyproxy
FireHol is running
TinyProxy is stopped
DansGuardian is stopped
 * Stopping Firewall firehol                                                    

WARNING
File '/etc/firehol/RESERVED_IPS' is more than 90 days old.
You should update it to ensure proper operation of your firewall.

Run the supplied get-iana.sh script to generate this file.

                                                                         [ OK ]
Stopping tinyproxy: tinyproxy.
 * Stopping DansGuardian dansguardian                                    [ OK ] 
FireHol is running
TinyProxy is stopped
DansGuardian is stopped
There was an error
dpkg: error processing webcontentcontrol (--remove):
 subprocess installed pre-removal script returned error exit status 1
===>postinst:abort-remove
Errors were encountered while processing:
 webcontentcontrol
E: Sub-process /usr/bin/dpkg returned an error code (1)

any remedies?

---

### Post by KIAaze on 2010-06-28
An untested solution:
[https://answers.launchpad.net/webcontentcontrol/+question/99576](https://answers.launchpad.net/webcontentcontrol/+question/99576)

The uninstall issue is theoretically fixed in the current repository version, but I had some problems creating the new debian package, so I haven't been able to test it yet.

---

### Post by KIAaze on 2010-07-04
Here is a tested way for removing webcontentcontrol for those that still have problems removing it:

```
sudo rm /var/lib/dpkg/info/webcontentcontrol.prerm
sudo rm /var/lib/dpkg/info/webcontentcontrol.postrm
sudo apt-get remove --purge webcontentcontrol
sudo apt-get remove --purge firehol tinyproxy dansguardian

```

A new version fixing the uninstall problems and other issues is under way.

Announcement: [https://launchpad.net/webcontentcontrol/+announcement/6256](https://launchpad.net/webcontentcontrol/+announcement/6256)

---

### Post by KIAaze on 2010-07-04
New release: [https://launchpad.net/webcontentcontrol/+announcement/6263](https://launchpad.net/webcontentcontrol/+announcement/6263)

---

### Post by daboochmeister on 2010-07-22
@KIAaze - thank you for your work on this.  After upgrade to Lucid, and installing 1.3.6 from the PPA, I'm having a problem in that, once I turn off WebContentControl from the GUI, I can no longer turn it on.  When I try, I get the following error, in the messages area:

```
There was an error
/usr/share/webcontentcontrol/scripts/common_functions.sh: line 84: test: -eq: unary operator expected
/usr/share/webcontentcontrol/scripts/common_functions.sh: line 90: test: -eq: unary operator expected
/usr/share/webcontentcontrol/scripts/common_functions.sh: line 96: test: -eq: unary operator expected
```

Checking the script, I notice those lines are all in a function named "no_gui" -- but I am using the GUI.

Note that I've installed the Jaunty version of DansGuardian, because of the blank page issue.  Also, I adjusted get-iana.sh to address the location and format change of the text version of the reserved ranges -- but can't see how that would affect this.

Also note, I can stop and start firehol, tinyproxy, and dansguardian manually.  I get an error starting tinyproxy, that they've apparently dealt with in v1.8.2 (about being unable to open the logfile), but it starts successfully.

Any help appreciated!

---

### Post by daboochmeister on 2010-07-22
Btw, tinyproxy actually did NOT start correctly -- a temp fix for that is to edit /etc/tinyproxy.conf, comment out the logfile line, and uncomment the line that says to log to syslog instead of a logfile.

But that still didn't fix the problem mentioned above.

---

### Post by daboochmeister on 2010-07-22
I hate to say it, but I started having the blank page error again -- this was with the jaunty DansGuardian, and any version of tinyproxy (I tried 1.8.2 and 1.8.0, in addition to the 1.8.1 in the Lucid repo).

I finally switched to polipo -- as lighterweight than squid (though it does cache like squid, by default), and more importantly, not exhibiting the white page/compression error.  Polipo uses port 8123, not 3128, so a DansGuardian conf was needed.

Next I'll see if the newer DansGuardian packages work with polipo ... project for tomorrow.

---

### Post by KIAaze on 2010-07-22
> **daboochmeister said:**
> When I try, I get the following error, in the messages area:

```
There was an error
/usr/share/webcontentcontrol/scripts/common_functions.sh: line 84: test: -eq: unary operator expected
/usr/share/webcontentcontrol/scripts/common_functions.sh: line 90: test: -eq: unary operator expected
/usr/share/webcontentcontrol/scripts/common_functions.sh: line 96: test: -eq: unary operator expected
```

Checking the script, I notice those lines are all in a function named "no_gui" -- but I am using the GUI.


This should be fixed now. Can you try the latest version from the bzr repository?
It's in a function called no_gui because it doesn't make use of gksudo. I did this to support non-Gnome systems.
I removed the unused start_all function, as well as all the checks. It should just try to start all daemons no matter if they are running or not. Those checks are some remnants of the initial code from the Ubuntu CE GUI.

> 
Also, I adjusted get-iana.sh to address the location and format change of the text version of the reserved ranges -- but can't see how that would affect this.

Could you give me the modified get-iana.sh?
Alternatively, you can join the development team and commit it if you want. :)

> **daboochmeister said:**
> Btw, tinyproxy actually did NOT start correctly -- a temp fix for that is to edit /etc/tinyproxy.conf, comment out the logfile line, and uncomment the line that says to log to syslog instead of a logfile.

But that still didn't fix the problem mentioned above.
I'll try to check that out as soon as possible. Thanks for reporting it.
P.S.: You can use the launchpad bug reporting system. ;)

---

### Post by primetime34 on 2010-07-26
Just installed the software and I'm pretty lost about how to do the following:

I would like to block all websites except those I whitelist.  How do I do this?  Running lucid.  Thanks.

---

### Post by KIAaze on 2010-07-26
See here:
[http://contentfilter.futuragts.com/wiki/doku.php?id=configuration_examples](http://contentfilter.futuragts.com/wiki/doku.php?id=configuration_examples)

Basically, you just add this line to the bannedsitelist:
```
**
```

And put the sites you want on the exceptionsitelist.

P.S.: As reported by daboochmeister, you might have problems restarting tinyproxy.

---

### Post by KIAaze on 2010-07-26
v1.3.7 released:
[https://launchpad.net/webcontentcontrol/+announcement/6396](https://launchpad.net/webcontentcontrol/+announcement/6396)

---

### Post by sunwatt on 2010-11-24
How do I install and config DansGuardian on Linux Mint Debian Edition?

Thanks

Jim

---

### Post by KIAaze on 2010-11-24
If it's Debian based and has at least firehol, dansguardian and tinyproxy in its repositories, you should be able to install the webcontentcontrol package like in Ubuntu.

If you don't want to install webcontentcontrol, but want to configure dansguardian "manually", it's more complicated.

But in principle, all you have to do is install the dansguardian package and a proxy of your choice. (The firewall is only necessary if you don't want to configure every browser to connect to the dansguardian filterport.)
Then you have to configure the different components.

Here's an example of the main things that need to be configured with the dansguardian+tinyproxy+firehol combo:

_Usual values:_
FILTERPORT=8080
PROXYPORT=3128
DGUSER=dansguardian
PROXYUSER=proxy
PROXYGROUP=proxy

_/etc/dansguardian/dansguardian.conf_
```

# the port that DansGuardian listens to.
filterport = $FILTERPORT
# the port DansGuardian connects to proxy on
proxyport = $PROXYPORT
# the user dansguardian runs as
daemonuser = '$DGUSER'

```

_/etc/tinyproxy/tinyproxy.conf_
```

# Port to listen on.
Port $PROXYPORT
# Name of the user the tinyproxy daemon should switch to after the port
User $PROXYUSER
# Name of the group the tinyproxy daemon should switch to after the port
Group $PROXYGROUP

```

_/etc/firehol/firehol.conf_
```

# drop all packets arriving at $PROXYPORT which do not come from $DGUSER
# (prevents bypassing dansguardian by connecting directly to the proxy)
iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport $PROXYPORT -m owner ! --uid-owner $DGUSER -j DROP
# redirect all http traffic through port $FILTERPORT and affect it to user $PROXYUSER and group $PROXYGROUP
# (automatically redirects all http traffic to dansguardian, so it's not necessary to configure each browser to connect to it)
transparent_squid $FILTERPORT "$PROXYUSER $PROXYGROUP"

```

Some examples (including with squid as proxy) can be found [here](http://bazaar.launchpad.net/~webcontentcontrol/webcontentcontrol/main/files/head%3A/reference/) (no guarantee that they work as is).

---

### Post by c.monty on 2010-12-01
Hello!

I've successfully installed the tools on Lucid 10.04.

All services start automaticall. Everything looks fine.

However, if all services are started, I cannot access the system from outside, means from any other system within the same network.
Neither Ping nor SSH are allowed.

What needs to be modified in order to allow 
SSH
VNC
on the system secured with "Parental control"?

THX

---

### Post by KIAaze on 2010-12-01
You need to configure firehol.
To do this, just edit "/etc/firehol/firehol.conf" and restart firehol.

I think all you need to do is add the following line:
```
server "vnc ping ssh" accept
```

You should be able to find everything you need here:
[http://firehol.sourceforge.net/](http://firehol.sourceforge.net/)
[http://firehol.sourceforge.net/tutorial.html](http://firehol.sourceforge.net/tutorial.html)
[http://ubuntuforums.org/showthread.php?t=1242050](http://ubuntuforums.org/showthread.php?t=1242050)
[http://firehol.sourceforge.net/services.html](http://firehol.sourceforge.net/services.html)

---

### Post by c.monty on 2010-12-02
Hi KIAaze,

thanks for your support!
Rating: +++

This works perfectly for me.

---

### Post by c.monty on 2010-12-07
Hello!

I have to address two issues with the tool hoping to get support from you.

1. I cannot display (popular german) websites [www.heute.de](www.heute.de) (news) or [www.zdf.de](www.zdf.de)
In the attached screenshot "Mozilla Firefox_010.png" you can see nothing but a comment "Fertig" that implies that the website has been loaded.

What would you suggest in order to have the content of these websites available?

2. When booting the PC, Firehol is not starting automatically although all settings should initiate the automatic start.
In the screenshot "Web Content Control_009.png" you can see that the service Firehol is not started with the setting "Firehol running at startup".
When I disable all services at startup and reboot the PC, I could then manually start the services with exception of Firehol and Dansguardian.
When starting manually Firehol I get error message "[...] warning firehol start runlevel do not match LSB Default [...]". Please check screenshot "Auswahl_004.png".
The same error message "[...] warning firehol start runlevel do not match LSB Default [...]" is shown when starting service Dansguardian manually. Please check screenshot "Auswahl_005.png".
Only service Tinyproxy starts without error.

What would you recommend to fix these issues?

Here's the conf-files:
```

firehol.conf
#
# $Id: client-all.conf,v 1.2 2002/12/31 15:44:34 ktsaou Exp $
#
# This configuration file will allow all requests originating from the
# local machine to be send through all network interfaces.
#
# No requests are allowed to come from the network. The host will be
# completely stealthed! It will not respond to anything, and it will
# not be pingable, although it will be able to originate anything
# (even pings to other hosts).
#

version 5
iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP
transparent_squid 8080 "proxy root"

# Accept all client traffic on any interface
interface any world
policy drop
protection strong
client all accept
#server cups accept
server "samba ssh vnc ping icmp" accept

```

```

dansguardian.conf
# DansGuardian config file for version 2.9.9.7

# **NOTE** as of version 2.7.5 most of the list files are now in dansguardianf1.conf

#UNCONFIGURED - Please remove this line after configuration

# Web Access Denied Reporting (does not affect logging)
#
# -1 = log, but do not block - Stealth mode
#  0 = just say 'Access Denied'
#  1 = report why but not what denied phrase
#  2 = report fully
#  3 = use HTML template file (accessdeniedaddress ignored) - recommended
#
reportinglevel = 3

# Language dir where languages are stored for internationalisation.
# The HTML template within this dir is only used when reportinglevel
# is set to 3. When used, DansGuardian will display the HTML file instead of
# using the perl cgi script.  This option is faster, cleaner
# and easier to customise the access denied page.
# The language file is used no matter what setting however.
#
languagedir = '/etc/dansguardian/languages'

# language to use from languagedir.
language = 'german'

# Logging Settings
#
# 0 = none  1 = just denied  2 = all text based  3 = all requests
loglevel = 2

# Log Exception Hits
# Log if an exception (user, ip, URL, phrase) is matched and so
# the page gets let through.  Can be useful for diagnosing
# why a site gets through the filter.
# 0 = never log exceptions
# 1 = log exceptions, but do not explicitly mark them as such
# 2 = always log & mark exceptions (default)
logexceptionhits = 2

# Log File Format
# 1 = DansGuardian format (space delimited)
# 2 = CSV-style format
# 3 = Squid Log File Format
# 4 = Tab delimited
logfileformat = 1

# truncate large items in log lines
#maxlogitemlength = 400

# anonymize logs (blank out usernames & IPs)
#anonymizelogs = on


# Syslog logging
#
# Use syslog for access logging instead of logging to the file
# at the defined or built-in "loglocation"
#syslog = on

# Log file location
# 
# Defines the log directory and filename.
#loglocation = '/var/log/dansguardian/access.log'


# Statistics log file location
#
# Defines the stat file directory and filename.
# Only used in conjunction with maxips > 0
# Once every 3 minutes, the current number of IPs in the cache, and the most
# that have been in the cache since the daemon was started, are written to this
# file. IPs persist in the cache for 7 days.
#statlocation = '/var/log/dansguardian/stats'


# Network Settings
# 
# the IP that DansGuardian listens on.  If left blank DansGuardian will
# listen on all IPs.  That would include all NICs, loopback, modem, etc.
# Normally you would have your firewall protecting this, but if you want
# you can limit it to a certain IP. To bind to multiple interfaces,
# specify each IP on an individual filterip line.
filterip =

# the port that DansGuardian listens to.
filterport = 8080

# the ip of the proxy (default is the loopback - i.e. this server)
proxyip = 127.0.0.1

# the port DansGuardian connects to proxy on
proxyport = 3128

# accessdeniedaddress is the address of your web server to which the cgi
# dansguardian reporting script was copied. Only used in reporting levels 1 and 2.
#
# This webserver must be either:
#  1. Non-proxied. Either a machine on the local network, or listed as an exception
#     in your browser's proxy configuration.
#  2. Added to the exceptionsitelist. Option 1 is preferable; this option is
#     only for users using both transparent proxying and a non-local server
#     to host this script.
#
# Individual filter groups can override this setting in their own configuration.
#
accessdeniedaddress = 'http://YOURSERVER.YOURDOMAIN/cgi-bin/dansguardian.pl'

# Non standard delimiter (only used with accessdeniedaddress)
# To help preserve the full banned URL, including parameters, the variables
# passed into the access denied CGI are separated using non-standard
# delimiters. This can be useful to ensure correct operation of the filter
# bypass modes. Parameters are split using "::" in place of "&", and "==" in
# place of "=".
# Default is enabled, but to go back to the standard mode, disable it.
nonstandarddelimiter = on



# Banned image replacement
# Images that are banned due to domain/url/etc reasons including those
# in the adverts blacklists can be replaced by an image.  This will,
# for example, hide images from advert sites and remove broken image
# icons from banned domains.
# on (default) | off
usecustombannedimage = on
custombannedimagefile = '/usr/share/dansguardian/transparent1x1.gif'



# Filter groups options
# filtergroups sets the number of filter groups. A filter group is a set of content
# filtering options you can apply to a group of users.  The value must be 1 or more.
# DansGuardian will automatically look for dansguardianfN.conf where N is the filter
# group.  To assign users to groups use the filtergroupslist option.  All users default
# to filter group 1.  You must have some sort of authentication to be able to map users
# to a group.  The more filter groups the more copies of the lists will be in RAM so
# use as few as possible.
filtergroups = 1
filtergroupslist = '/etc/dansguardian/lists/filtergroupslist'



# Authentication files location
bannediplist = '/etc/dansguardian/lists/bannediplist'
exceptioniplist = '/etc/dansguardian/lists/exceptioniplist'



# Show weighted phrases found
# If enabled then the phrases found that made up the total which excedes
# the naughtyness limit will be logged and, if the reporting level is
# high enough, reported. on | off
showweightedfound = on

# Weighted phrase mode
# There are 3 possible modes of operation:
# 0 = off = do not use the weighted phrase feature.
# 1 = on, normal = normal weighted phrase operation.
# 2 = on, singular = each weighted phrase found only counts once on a page.
#
weightedphrasemode = 2



# Positive (clean) result caching for URLs
# Caches good pages so they don't need to be scanned again.
# It also works with AV plugins.
# 0 = off (recommended for ISPs with users with disimilar browsing)
# 1000 = recommended for most users
# 5000 = suggested max upper limit
# If you're using an AV plugin then use at least 5000.
urlcachenumber = 1000
#
# Age before they are stale and should be ignored in seconds
# 0 = never
# 900 = recommended = 15 mins
urlcacheage = 900



# Clean cache for content (AV) scan results
# By default, to save CPU, files scanned and found to be
# clean are inserted into the clean cache and NOT scanned
# again for a while.  If you don't like this then choose
# to disable it.
# (on|off) default = on.
scancleancache = on



# Smart, Raw and Meta/Title phrase content filtering options
# Smart is where the multiple spaces and HTML are removed before phrase filtering
# Raw is where the raw HTML including meta tags are phrase filtered
# Meta/Title is where only meta and title tags are phrase filtered (v. quick)
# CPU usage can be effectively halved by using setting 0 or 1 compared to 2
# 0 = raw only
# 1 = smart only
# 2 = both of the above (default)
# 3 = meta/title
phrasefiltermode = 2

# Lower casing options
# When a document is scanned the uppercase letters are converted to lower case
# in order to compare them with the phrases.  However this can break Big5 and
# other 16-bit texts.  If needed preserve the case.  As of version 2.7.0 accented
# characters are supported.
# 0 = force lower case (default)
# 1 = do not change case
# 2 = scan first in lower case, then in original case
preservecase = 0

# Note:
# If phrasefiltermode and preserve case are both 2, this equates to 4 phrase
# filtering passes. If you have a large enough userbase for this to be a
# worry, and need to filter pages in exotic character encodings, it may be
# better to run two instances on separate servers: one with preservecase 1
# (and possibly forcequicksearch 1) and non ASCII/UTF-8 phrase lists, and one
# with preservecase 0 and ASCII/UTF-8 lists.



# Hex decoding options
# When a document is scanned it can optionally convert %XX to chars.
# If you find documents are getting past the phrase filtering due to encoding
# then enable.  However this can break Big5 and other 16-bit texts.
# off = disabled (default)
# on = enabled
hexdecodecontent = off



# Force Quick Search rather than DFA search algorithm
# The current DFA implementation is not totally 16-bit character compatible
# but is used by default as it handles large phrase lists much faster.
# If you wish to use a large number of 16-bit character phrases then
# enable this option.
# off (default) | on (Big5 compatible)
forcequicksearch = off



# Reverse lookups for banned site and URLs.
# If set to on, DansGuardian will look up the forward DNS for an IP URL
# address and search for both in the banned site and URL lists.  This would
# prevent a user from simply entering the IP for a banned address.
# It will reduce searching speed somewhat so unless you have a local caching
# DNS server, leave it off and use the Blanket IP Block option in the
# bannedsitelist file instead.
reverseaddresslookups = off



# Reverse lookups for banned and exception IP lists.
# If set to on, DansGuardian will look up the forward DNS for the IP
# of the connecting computer.  This means you can put in hostnames in
# the exceptioniplist and bannediplist.
# If a client computer is matched against an IP given in the lists, then the
# IP will be recorded in any log entries; if forward DNS is successful and a
# match occurs against a hostname, the hostname will be logged instead.
# It will reduce searching speed somewhat so unless you have a local DNS server, 
# leave it off.
reverseclientiplookups = off


# Perform reverse lookups on client IPs for successful requests.
# If set to on, DansGuardian will look up the forward DNS for the IP
# of the connecting computer, and log host names (where available) rather than
# IPs against requests.
# This is not dependent on reverseclientiplookups being enabled; however, if it
# is, enabling this option does not incur any additional forward DNS requests.
logclienthostnames = off


# Build bannedsitelist and bannedurllist cache files.
# This will compare the date stamp of the list file with the date stamp of
# the cache file and will recreate as needed.
# If a bsl or bul .processed file exists, then that will be used instead.
# It will increase process start speed by 300%.  On slow computers this will
# be significant.  Fast computers do not need this option. on | off
createlistcachefiles = on



# POST protection (web upload and forms)
# does not block forms without any file upload, i.e. this is just for
# blocking or limiting uploads
# measured in kibibytes after MIME encoding and header bumph
# use 0 for a complete block
# use higher (e.g. 512 = 512Kbytes) for limiting
# use -1 for no blocking
#maxuploadsize = 512
#maxuploadsize = 0
maxuploadsize = -1



# Max content filter size
# Sometimes web servers label binary files as text which can be very
# large which causes a huge drain on memory and cpu resources.
# To counter this, you can limit the size of the document to be
# filtered and get it to just pass it straight through.
# This setting also applies to content regular expression modification.
# The value must not be higher than maxcontentramcachescansize
# The size is in Kibibytes - eg 2048 = 2Mb
# use 0 to set it to maxcontentramcachescansize
maxcontentfiltersize = 256



# Max content ram cache scan size
# This is only used if you use a content scanner plugin such as AV
# This is the max size of file that DG will download and cache
# in RAM.  After this limit is reached it will cache to disk
# This value must be less than or equal to maxcontentfilecachescansize.
# The size is in Kibibytes - eg 10240 = 10Mb
# use 0 to set it to maxcontentfilecachescansize
# This option may be ignored by the configured download manager.
maxcontentramcachescansize = 2000



# Max content file cache scan size
# This is only used if you use a content scanner plugin such as AV
# This is the max size file that DG will download
# so that it can be scanned or virus checked.
# This value must be greater or equal to maxcontentramcachescansize.
# The size is in Kibibytes - eg 10240 = 10Mb
maxcontentfilecachescansize = 20000



# File cache dir
# Where DG will download files to be scanned if too large for the
# RAM cache.
filecachedir = '/tmp'



# Delete file cache after user completes download
# When a file gets save to temp it stays there until it is deleted.
# You can choose to have the file deleted when the user makes a sucessful
# download.  This will mean if they click on the link to download from
# the temp store a second time it will give a 404 error.
# You should configure something to delete old files in temp to stop it filling up.
# on|off (defaults to on)
deletedownloadedtempfiles = on



# Initial Trickle delay
# This is the number of seconds a browser connection is left waiting
# before first being sent *something* to keep it alive.  The
# *something* depends on the download manager chosen.
# Do not choose a value too low or normal web pages will be affected.
# A value between 20 and 110 would be sensible
# This may be ignored by the configured download manager.
initialtrickledelay = 20



# Trickle delay
# This is the number of seconds a browser connection is left waiting
# before being sent more *something* to keep it alive.  The
# *something* depends on the download manager chosen.
# This may be ignored by the configured download manager.
trickledelay = 10



# Download Managers
# These handle downloads of files to be filtered and scanned.
# They differ in the method they deal with large downloads.
# Files usually need to be downloaded 100% before they can be
# filtered and scanned before being sent on to the browser.
# Normally the browser can just wait, but with content scanning,
# for example to AV, the browser may timeout or the user may get
# confused so the download manager has to do some sort of
# 'keep alive'.
#
# There are various methods possible but not all are included.
# The author does not have the time to write them all so I have
# included a plugin systam.  Also, not all methods work with all
# browsers and clients.  Specifically some fancy methods don't
# work with software that downloads updates.  To solve this,
# each plugin can support a regular expression for matching
# the client's user-agent string, and lists of the mime types
# and extensions it should manage.
#
# Note that these are the matching methods provided by the base plugin
# code, and individual plugins may override or add to them.
# See the individual plugin conf files for supported options.
#
# The plugins are matched in the order you specify and the last
# one is forced to match as the default, regardless of user agent
# and other matching mechanisms.
#
downloadmanager = '/etc/dansguardian/downloadmanagers/fancy.conf'
#downloadmanager = '/etc/dansguardian/downloadmanagers/trickle.conf'
downloadmanager = '/etc/dansguardian/downloadmanagers/default.conf'



# Content Scanners (Also known as AV scanners)
# These are plugins that scan the content of all files your browser fetches
# for example to AV scan.  The options are limitless.  Eventually all of
# DansGuardian will be plugin based.  You can have more than one content
# scanner. The plugins are run in the order you specify.
# This is one of the few places you can have multiple options of the same name.
#
# Some of the scanner(s) require 3rd party software and libraries eg clamav.
# See the individual plugin conf file for more options (if any).
#
#contentscanner = '/etc/dansguardian/contentscanners/clamav.conf'
#!! Not compiled !! contentscanner = '/etc/dansguardian/contentscanners/clamdscan.conf'
#!! Unimplemented !! contentscanner = '/etc/dansguardian/contentscanners/kavav.conf'
#!! Not compiled !! contentscanner = '/etc/dansguardian/contentscanners/kavdscan.conf'
#contentscanner = '/etc/dansguardian/contentscanners/icapscan.conf'
#contentscanner = '/etc/dansguardian/contentscanners/commandlinescan.conf'



# Content scanner timeout
# Some of the content scanners support using a timeout value to stop
# processing (eg AV scanning) the file if it takes too long.
# If supported this will be used.
# The default of 60 seconds is probably reasonable.
contentscannertimeout = 60



# Content scan exceptions
# If 'on' exception sites, urls, users etc will be scanned
# This is probably not desirable behavour as exceptions are
# supposed to be trusted and will increase load.
# Correct use of grey lists are a better idea.
# (on|off) default = off
contentscanexceptions = off



# Auth plugins
# These replace the usernameidmethod* options in previous versions. They
# handle the extraction of client usernames from various sources, such as
# Proxy-Authorisation headers and ident servers, enabling requests to be
# handled according to the settings of the user's filter group.
# Multiple plugins can be specified, and will be queried in order until one
# of them either finds a username or throws an error. For example, if Squid
# is configured with both NTLM and Basic auth enabled, and both the 'proxy-basic'
# and 'proxy-ntlm' auth plugins are enabled here, then clients which do not support
# NTLM can fall back to Basic without sacrificing access rights.
#
# If you do not use multiple filter groups, you need not specify this option.
#
#authplugin = '/etc/dansguardian/authplugins/proxy-basic.conf'
#authplugin = '/etc/dansguardian/authplugins/proxy-digest.conf'
#authplugin = '/etc/dansguardian/authplugins/proxy-ntlm.conf'
#authplugin = '/etc/dansguardian/authplugins/ident.conf'
#authplugin = '/etc/dansguardian/authplugins/ip.conf'



# Re-check replaced URLs
# As a matter of course, URLs undergo regular expression search/replace (urlregexplist)
# *after* checking the exception site/URL/regexpURL lists, but *before* checking against
# the banned site/URL lists, allowing certain requests that would be matched against the
# latter in their original state to effectively be converted into grey requests.
# With this option enabled, the exception site/URL/regexpURL lists are also re-checked
# after replacement, making it possible for URL replacement to trigger exceptions based
# on them.
# Defaults to off.
recheckreplacedurls = off



# Misc settings

# if on it adds an X-Forwarded-For: <clientip> to the HTTP request
# header.  This may help solve some problem sites that need to know the
# source ip. on | off
forwardedfor = off


# if on it uses the X-Forwarded-For: <clientip> to determine the client
# IP. This is for when you have squid between the clients and DansGuardian.
# Warning - headers are easily spoofed. on | off
usexforwardedfor = off


# if on it logs some debug info regarding fork()ing and accept()ing which
# can usually be ignored.  These are logged by syslog.  It is safe to leave
# it on or off
logconnectionhandlingerrors = on



# Fork pool options

# If on, this causes DG to write to the log file whenever child processes are
# created or destroyed (other than by crashes). This information can help in
# understanding and tuning the following parameters, but is not generally
# useful in production.
logchildprocesshandling = off

# sets the maximum number of processes to spawn to handle the incoming
# connections.  Max value usually 250 depending on OS.
# On large sites you might want to try 180.
maxchildren = 120


# sets the minimum number of processes to spawn to handle the incoming connections.
# On large sites you might want to try 32.
minchildren = 8


# sets the minimum number of processes to be kept ready to handle connections.
# On large sites you might want to try 8.
minsparechildren = 4


# sets the minimum number of processes to spawn when it runs out
# On large sites you might want to try 10.
preforkchildren = 6


# sets the maximum number of processes to have doing nothing.
# When this many are spare it will cull some of them.
# On large sites you might want to try 64.
maxsparechildren = 32


# sets the maximum age of a child process before it croaks it.
# This is the number of connections they handle before exiting.
# On large sites you might want to try 10000.
maxagechildren = 500


# Sets the maximum number client IP addresses allowed to connect at once.
# Use this to set a hard limit on the number of users allowed to concurrently
# browse the web. Set to 0 for no limit, and to disable the IP cache process.
maxips = 0



# Process options
# (Change these only if you really know what you are doing).
# These options allow you to run multiple instances of DansGuardian on a single machine.
# Remember to edit the log file path above also if that is your intention.

# IPC filename
# 
# Defines IPC server directory and filename used to communicate with the log process.
ipcfilename = '/tmp/.dguardianipc'

# URL list IPC filename
# 
# Defines URL list IPC server directory and filename used to communicate with the URL
# cache process.
urlipcfilename = '/tmp/.dguardianurlipc'

# IP list IPC filename
#
# Defines IP list IPC server directory and filename, for communicating with the client
# IP cache process.
ipipcfilename = '/tmp/.dguardianipipc'

# PID filename
# 
# Defines process id directory and filename.
#pidfilename = '/var/run/dansguardian.pid'

# Disable daemoning
# If enabled the process will not fork into the background.
# It is not usually advantageous to do this.
# on|off (defaults to off)
nodaemon = off

# Disable logging process
# on|off (defaults to off)
nologger = off

# Enable logging of "ADs" category blocks
# on|off (defaults to off)
logadblocks = off

# Enable logging of client User-Agent
# Some browsers will cause a *lot* of extra information on each line!
# on|off (defaults to off)
loguseragent = off

# Daemon runas user and group
# This is the user that DansGuardian runs as.  Normally the user/group nobody.
# Uncomment to use.  Defaults to the user set at compile time.
# Temp files created during virus scanning are given owner and group read
# permissions; to use content scanners based on external processes, such as
# clamdscan, the two processes must run with either the same group or user ID.
daemonuser = 'dansguardian'
daemongroup = 'dansguardian'

# Soft restart
# When on this disables the forced killing off all processes in the process group.
# This is not to be confused with the -g run time option - they are not related.
# on|off (defaults to off)
softrestart = off

# Mail program
# Path (sendmail-compatible) email program, with options.
# Not used if usesmtp is disabled (filtergroup specific).
mailer = '/usr/sbin/sendmail -t'

```

---

### Post by c.monty on 2010-12-07
Update:

I've investigated some time to figure out why the service Firehol is not running after startup.
I found this [webpage]("http://1000umbrellas.com/2010/05/14/how-to-configure-the-firewall-with-firehol-on-ubuntu-10-04-lucid-lynx") that says:
"Simply change the second line (in /etc/default/firehol) to
START_FIREHOL=YES
and save the file. That will enable the firewall upon reboot. What that means is that Firehol will run its bash scripts, generate iptables rules, and then the iptables will be activated. Firehol does not run continuously as a service."

If I understood correctly, during startup some Firehol bash scripts will be executed to define ip table settings.
There's no service started in background.

If that is true, the traffic light in "Parental control GUI" will always be red until the service is started.

And as a consequence the Parental control appears to be off.

Any comment from you?

THX

---

### Post by roc1479 on 2010-12-09
If firehol is not started, it won't work. Make sure to change the line to yes and restart the services.

---

### Post by KIAaze on 2010-12-09
> **c.monty said:**
> What that means is that Firehol will run its bash scripts, generate iptables rules, and then the iptables will be activated. Firehol does not run continuously as a service."

If I understood correctly, during startup some Firehol bash scripts will be executed to define ip table settings.
There's no service started in background.


That's correct. iptables is some kind of linux kernel service and all "firewall programs" are just interfaces to it as far as I know.
Ubuntu comes with "ufw" by default now, but I haven't checked if that causes any conflicts yet.

Sorry, I'm a bit busy at the moment, but concerning your pages which don't load, but are not banned, I think it's due to a known dansguardian bug:
[https://launchpad.net/webcontentcontrol/+announcement/4830](https://launchpad.net/webcontentcontrol/+announcement/4830)

I haven't tried WCC recently on Ubuntu 10.10, but I assume the problem and solution are still the same unfortunately.

---

### Post by roc1479 on 2010-12-09
KIAaze,

Great frontend to dansguardian!  I'm sorry about not following up with you regarding squid integration. The reason I'm interested in squid is because of all the different authentication schemes that it's capable of.  

My current setup works via ipgroups plugin for dansguardian.  I'm quite sure it can work with Tinyproxy without any problems.  However, I'd like the ability to do some authentication against AD and caching, therefore using squid is my option.

I plan to join my proxy box to AD to enable ntlm authentication, setup webcontentcontrol and have nginx serve clients the wpad configuration for a true transparent setup.  

Currently, this is how my setup looks:

NICA -->Incoming
NICB -->Outgoing
Firehol entry to allow traffic to pass
Webcontentcontrol to edit dansguardian/group files and start/stop services

So essentially, I'm using it as a gateway.  I love the frontend feature, which allows quick edits to config files. The only issue is the squid button.  I've changed the Tinyproxy button, gotten the scripts to start/stop the service, but the button does not update the status.  I think that's all I have to do now to get it to work flawlessly.  I'll keep digging at your scripts, I'm sure there's one that controls the status updates.  If you have a min and can point me in the right direction, I'd really appreciate it.

Thanks,

Rocky

---

### Post by c.monty on 2010-12-10
Hi!

I want to focus on the issue with Firehol startup. (The other issues have lower priority for me.)

This issue is not related to ufw or any other firewall, because ufw is inactive:
```

user@pc2-xubuntu1004:~$ sudo ufw status 
Status: inactive

```

I've verified if Firehol is **starting up as a process** on another Ubuntu 10.04 installation, means I've installed Firehol
```

sudo apt-get install firehol

```
and then set the startup by means modifying line START_FIREHOL=YES in /etc/default/firehol.

However when displaying the process list Firehol is not listed:
```

ps -ea | grep firehol

```

But I do believe that Firehol has started by means of modifying the iptable settings. It's just not launched as a service.

What do you think?

---

### Post by KIAaze on 2010-12-10
A good way to make sure that FireHol is running (or has set up iptables) is to run:
```
sudo iptables -L
```

It will be short if no iptable rules have been set, otherwise quite long.

To clear the iptables settings, you can use:
```
sudo iptables -F
```

For c.monty and roc1479: The status updates are handled in "[common_functions.sh]("http://bazaar.launchpad.net/~webcontentcontrol/webcontentcontrol/main/annotate/head:/scripts/common_functions.sh")":

Here's how WCC checks if FireHol is running:
```
function check_fh {
    FIREHOL_LOCK_DIR="/var/lock/subsys"
    test ! -d "${FIREHOL_LOCK_DIR}" && FIREHOL_LOCK_DIR="/var/lock"

    ## FireHol
    if ( test -n "`which firehol`" ) && ( test -f $FIREHOL_LOCK_DIR/firehol || test -f /var/lock/subsys/firehol );
    then fh_running=1 && echo "FireHol is running" && return 1;
    else fh_running=0 && echo "FireHol is stopped" && return 0;
    fi
}

```

Basically, this means that it considers firehol as running if one of the following files exist:
-/var/lock/firehol
-/var/lock/subsys/firehol

Additionally, it checks that firehol is installed with "which firehol".
If that command fails, firehol is considered as not running.
I added that because of errors during uninstallation.

Using "iptables -L" might be difficult to interpret safely and requires root permissions.
And I think I based the running check on the firehol init script itself recently.

And for the proxies:
```

function check_tp {
    ## TinyProxy
    pid_tp="`pidof tinyproxy | tr -d [:space:]`"
    if (test -z $pid_tp);
    then tp_running=0 && echo "TinyProxy is stopped" && return 0;
    else tp_running=1 && echo "TinyProxy is running" && return 1;
    fi
}

function check_sq {
    ## squid
    pid="`pidof squid | tr -d [:space:]`"
    if (test -z $pid);
    then sq_running=0 && echo "squid is stopped" && return 0;
    else sq_running=1 && echo "squid is running" && return 1;
    fi
}

```

I added a configure option to use squid as proxy instead of tinyproxy a while ago. You have to install from source to use it.
Not sure if it still works.

---

### Post by roc1479 on 2010-12-10
Firehol is basically just the frontend to iptables.  

What's in your firehol.conf?

---

### Post by roc1479 on 2010-12-10
KIAaze,

Thanks for the information.  I figured it out early today..lol  I have it running squid and it looks like everything is good so far.  I am able to stop/start squid and even renamed the buttons to reflect it.  Since I'm using this as a gateway device, I'll remove the firefox button.  Should I also remove the WPA button?

Thanks,

Rocky

---

### Post by AlexanderDGreat on 2010-12-10
Looks interesting, but I'm using Squid Proxy to control the Internet Usage & Squid Guard to filter Key Words, I use Iptables to forward workstation subnet to my server subnet (they are different subnets).

What are the advantages of this setup?

---

### Post by roc1479 on 2010-12-14
The most noted difference is that dansguardian does everything squidguard does plus the heuristics analysis of the queries/web content.

---

### Post by c.monty on 2010-12-18
> **KIAaze said:**
> A good way to make sure that FireHol is running (or has set up iptables) is to run:
```
sudo iptables -L
```
It will be short if no iptable rules have been set, otherwise quite long.


FireHol must start (not running) and configure iptables accordingly:
```

user@pc2-xubuntu1004:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination   

```

> **KIAaze said:**
> 
To clear the iptables settings, you can use:
```
sudo iptables -F
```

For c.monty and roc1479: The status updates are handled in "[common_functions.sh]("http://bazaar.launchpad.net/~webcontentcontrol/webcontentcontrol/main/annotate/head:/scripts/common_functions.sh")":

Here's how WCC checks if FireHol is running:
```
function check_fh {
    FIREHOL_LOCK_DIR="/var/lock/subsys"
    test ! -d "${FIREHOL_LOCK_DIR}" && FIREHOL_LOCK_DIR="/var/lock"

    ## FireHol
    if ( test -n "`which firehol`" ) && ( test -f $FIREHOL_LOCK_DIR/firehol || test -f /var/lock/subsys/firehol );
    then fh_running=1 && echo "FireHol is running" && return 1;
    else fh_running=0 && echo "FireHol is stopped" && return 0;
    fi
}

```

Basically, this means that it considers firehol as running if one of the following files exist:
-/var/lock/firehol
-/var/lock/subsys/firehol


Only file /var/lock/firehol exists:
```

user@pc2-xubuntu1004:~$ ls -l /var/lock/
insgesamt 0
drwxr-xr-x 2 root root 40 2010-12-18 06:19 aumix
-rw------- 1 root root  0 2010-12-18 06:19 firehol
-rw------- 1 root root  0 2010-12-18 06:19 iptables
drwxr-xr-x 2 root root 40 2010-12-18 06:19 subsys
user@pc2-xubuntu1004:~$ ls -l /var/lock/subsys/
insgesamt 0

```

> **KIAaze said:**
> 
Additionally, it checks that firehol is installed with "which firehol".
If that command fails, firehol is considered as not running.
I added that because of errors during uninstallation.


Command "which firehol" returns: /sbin/firehol
```

user@pc2-xubuntu1004:~$ which firehol
/sbin/firehol

```

> **KIAaze said:**
> 
Using "iptables -L" might be difficult to interpret safely and requires root permissions.
And I think I based the running check on the firehol init script itself recently.

And for the proxies:
```

function check_tp {
    ## TinyProxy
    pid_tp="`pidof tinyproxy | tr -d [:space:]`"
    if (test -z $pid_tp);
    then tp_running=0 && echo "TinyProxy is stopped" && return 0;
    else tp_running=1 && echo "TinyProxy is running" && return 1;
    fi
}

function check_sq {
    ## squid
    pid="`pidof squid | tr -d [:space:]`"
    if (test -z $pid);
    then sq_running=0 && echo "squid is stopped" && return 0;
    else sq_running=1 && echo "squid is running" && return 1;
    fi
}

```

I added a configure option to use squid as proxy instead of tinyproxy a while ago. You have to install from source to use it.
Not sure if it still works.

So, it looks to me that at least 2 out of 3 check conditions are positive. Nevertheless the light in the GUI indicates that FireHol is not running.

Any suggestions?

THX

---

### Post by dfarin on 2010-12-30
I've been searching this and earlier threads, and it seems that the tools are designed for use as web filters looking for text associated with certain types of content. If enough text is there with key word counts, the site will be blocked from appearing in search results. Part of what I'm trying to understand is the big picture, strengths and weaknesses of these various tools. I appreciate the importance of the work developers have invested. I plan to install these tools and to test them using [http://filter-test.echoz.com](http://filter-test.echoz.com) as described in the following blog [http://oinateb.wordpress.com/](http://oinateb.wordpress.com/).

I'm searching for something I could use on my media server with Mythbuntu to block inappropriate video content as well. I find the content offered on Hulu Desktop and other internet streaming sources to include much that I feel is inappropriate for my younger children, and want to limit their access on this particular computer which is in our family room, not our common living area. I had been using TiVo Kidzone for this purpose but decided to give Mythbuntu on a Zotac Ion media pc with front and backend installation. I'm wondering if there are Ubuntu users with internet filters limiting content available through Hulu, youtube, etc.

---

### Post by KIAaze on 2011-01-02
Sorry for the late reply.
=============
@roc1479:
> **roc1479 said:**
> KIAaze,

Thanks for the information.  I figured it out early today..lol  I have it running squid and it looks like everything is good so far.  I am able to stop/start squid and even renamed the buttons to reflect it.  Since I'm using this as a gateway device, I'll remove the firefox button.  Should I also remove the WPA button?

Thanks,

Rocky

Remove it if you want.
If you make modifications to WCC that you think might be useful to others (or not ^^), you're welcome to join the project anytime. :)

Oh, and the configure option to use squid instead of tinyproxy is mentioned in the FAQ in the original post. (In case you hadn't found it. I didn't remember how to use it actually, so I was happy to see I put it there back then.)

And thanks for answering AlexanderDGreat's question!

=============
@c.monty:
```

user@pc2-xubuntu1004:~$ ls -l /var/lock/
insgesamt 0
drwxr-xr-x 2 root root 40 2010-12-18 06:19 aumix
-rw------- 1 root root  0 2010-12-18 06:19 firehol
-rw------- 1 root root  0 2010-12-18 06:19 iptables
drwxr-xr-x 2 root root 40 2010-12-18 06:19 subsys
user@pc2-xubuntu1004:~$ ls -l /var/lock/subsys/
insgesamt 0
```
This is why the test fails: "/var/lock/subsys/" exists and does not contain "firehol". The script sets the FH dir to "/var/lock/subsys" and then tests for "/var/lock/subsys/firehol" two times.
So, yes, this is clearly a bug in the test algorithm.

However, looking at the output of " sudo iptables -L", it seems that firehol is really not running in your case. So there appears to be a bigger problem...

=============
@dfarin: Yes, dansguardian filters by keywords/content, not only with a URL blacklist. I don't know of any video content filtering tool. But in principle, filtering by words should be enough since for usabilty reasons, the text around the video (title, description, related video titles, comments) should give a good idea of what is in it.

=============
P.S.: Happy new year! Felicxan novjaron! :)

---

### Post by c.monty on 2011-01-24
> **KIAaze said:**
> 
@c.monty:
```

user@pc2-xubuntu1004:~$ ls -l /var/lock/
insgesamt 0
drwxr-xr-x 2 root root 40 2010-12-18 06:19 aumix
-rw------- 1 root root  0 2010-12-18 06:19 firehol
-rw------- 1 root root  0 2010-12-18 06:19 iptables
drwxr-xr-x 2 root root 40 2010-12-18 06:19 subsys
user@pc2-xubuntu1004:~$ ls -l /var/lock/subsys/
insgesamt 0
```
This is why the test fails: "/var/lock/subsys/" exists and does not contain "firehol". The script sets the FH dir to "/var/lock/subsys" and then tests for "/var/lock/subsys/firehol" two times.
So, yes, this is clearly a bug in the test algorithm.

However, looking at the output of " sudo iptables -L", it seems that firehol is really not running in your case. So there appears to be a bigger problem...



OK, not good.
How can I continue analysing this issue.
Which directories should be checked, which logs should be reviewed?

THX

---

### Post by KIAaze on 2011-01-24
Make sure that /etc/default/firehol contains the following:
```
#To enable firehol at startup set START_FIREHOL=YES
START_FIREHOL=YES
#If you want to have firehol wait for an iface to be up add it here
WAIT_FOR_IFACE=""

```

I tried a clean install of firehol and noticed that after stopping it, I couldn't restart it because of "START_FIREHOL=NO" in /etc/default/firehol by default. So I think that might be the problem.

However, a clean install of webcontentcontrol on Ubuntu 10.10 seemed to work correctly. (It sets START_FIREHOL=YES during installation.)

To start/stop firehol manually use:
```
sudo /etc/init.d/firehol start
sudo /etc/init.d/firehol stop

```

---

### Post by shane2peru on 2011-04-19
I'm looking at using this, but I wondered if it can be configured to allow ssh inside my network.  I have a two computers setup, and I want to be able to ssh into the other computer and update etc, and sftp to the other computer to copy files to it, or scp, can these things be set up to work with the webcontentcontrol?  Thanks!

Shane

---

### Post by KIAaze on 2011-04-20
Yes, should be possible by modifying the firehol configuration file /etc/firehol/firehol.conf

Check [http://firehol.sourceforge.net/](http://firehol.sourceforge.net/) for more help.

In principle, to make my program completely user-friendly, I would need a full GUI for dansguardian, the user-defined proxy and the user-defined firewall. I might do it eventually, but not now. :)

At the moment, you should be able to open the configuration files from the GUI though, if I remember correctly.

---

### Post by shane2peru on 2011-04-20
> **KIAaze said:**
> Yes, should be possible by modifying the firehol configuration file /etc/firehol/firehol.conf

Check [http://firehol.sourceforge.net/](http://firehol.sourceforge.net/) for more help.

In principle, to make my program completely user-friendly, I would need a full GUI for dansguardian, the user-defined proxy and the user-defined firewall. I might do it eventually, but not now. :)

At the moment, you should be able to open the configuration files from the GUI though, if I remember correctly.

I will test it out and get back to you.  Being someone that runs ssh and scp means I don't mind using a little cli and configuring that so long as I know how and can find it.  I will let you know how it goes!  Thanks!

Shane

[b]EDIT-1:Also, I upgrade one box to test out Natty, I would be willing to give this a try for Natty too.
EDIT-2:Ok, got ssh working with firehol, had to add this line to the firehol.conf:  ```
server "dns ftp ssh ping" accept
```[/b]

---

### Post by shane2peru on 2011-04-20
I have found using google chrome, set the proxy to 8080 that many web pages simply don't load.  That is kind of annoying.  I refresh, and it still doesn't load?  Any ideas?  I'm on 10.10.

Shane

---

### Post by KIAaze on 2011-04-20
Yes, I also had that problem. Even happens in Firefox. It seems to be a dansguardian bug, so there's not much I can do about it at the moment, without starting to debug dansguardian.
The easy solution is to downgrade to an older version of dansguardian.
cf: [https://launchpad.net/webcontentcontrol/+announcement/4830](https://launchpad.net/webcontentcontrol/+announcement/4830)

---

### Post by shane2peru on 2011-04-20
What version of DansGuardian was that?  Seems the Jaunty is now gone!  No longer supported I think.  At any rate the DG package isn't there any longer. :(  However I can download older versions of DG from their web site, 2.8 and older, and build from source?

Shane

---

### Post by KIAaze on 2011-04-20
2.9.9.7 according to this: [https://bugs.launchpad.net/ubuntu/+source/dansguardian/+bug/474475](https://bugs.launchpad.net/ubuntu/+source/dansguardian/+bug/474475)

The source package is here: [http://dansguardian.org/downloads/2/Beta/](http://dansguardian.org/downloads/2/Beta/)

The hardy version might work as well: [http://packages.ubuntu.com/hardy/dansguardian](http://packages.ubuntu.com/hardy/dansguardian)

---

### Post by shane2peru on 2011-04-20
> **KIAaze said:**
> 2.9.9.7 according to this: [https://bugs.launchpad.net/ubuntu/+source/dansguardian/+bug/474475](https://bugs.launchpad.net/ubuntu/+source/dansguardian/+bug/474475)

The source package is here: [http://dansguardian.org/downloads/2/Beta/](http://dansguardian.org/downloads/2/Beta/)

The hardy version might work as well: [http://packages.ubuntu.com/hardy/dansguardian](http://packages.ubuntu.com/hardy/dansguardian)
Ok, got the hardy version, and now running that, seems to work much better.  I will test it and if I run into any problems will report back here, otherwise you can assume it is running fine. :)  Thanks for the help with this!

Shane

---

### Post by shane2peru on 2011-04-21
Ok, I discovered that you have to pin or lock that package so it doesn't get upgraded.  That is nicely outlined on this page:  [https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

Shane

---

### Post by foxy123 on 2011-10-16
Looks like webcontentcontrol and timekpr are not available for Oneiric.

---

### Post by asottomayor on 2011-12-22
Hi,
Just trying to get this to work, is there a script for install or just set repos and get in going on 10.4 ?
Thanks
 
Asottomayor

---

### Post by asottomayor on 2011-12-22
> **asottomayor said:**
> Hi,
Just trying to get this to work, is there a script for install or just set repos and get in going on 10.4 ?
Thanks
 
Asottomayor

Yes, it's working fine with Lucind, just needed to adjust firehol :
Created a new firehol.conf, test it and works great as a network proxy.
Thanks on your software !!
Asottomayor:popcorn:

---

### Post by roc1479 on 2012-01-18
Foxy,

I've gotten webcontentcontrol to work with Oneiric.  I'll post what I did for anyone who wants to try it.

Rocky

---

### Post by foxy123 on 2012-01-19
> **roc1479 said:**
> Foxy,

I've gotten webcontentcontrol to work with Oneiric.  I'll post what I did for anyone who wants to try it.

Rocky

Thanks a lot. Please do.

---

### Post by KIAaze on 2012-01-21
Ah, great. :)
Sorry I have not been working/updating WCC recently. I am quite busy at the moment with various other things, and most importantly, I have stopped using it myself, which reduces my motivation to work on it. :/

I hope to be able to work on it again soon, at least to keep it in a functioning state and working with each new Ubuntu release.

---

