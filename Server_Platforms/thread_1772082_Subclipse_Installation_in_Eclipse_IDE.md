---
title: "Subclipse Installation in Eclipse IDE"
date: 2011-05-31
forum: Server Platforms
---

### Post by thoufiq on 2011-05-31
Hello All,
              I have installed xampp, xdebug and also eclipse ide in my ubuntu server. To run eclipse in my ubuntu server i installed gnome-desktop-environment.
All these are installed successfully but while installing subclipse in eclipse ide svn perspective cant found in [COLOR=Red]window -> open perspective -> other [COLOR=Black]menu[/COLOR][/COLOR].
Also cant found the php perspective in [COLOR=Red]window -> open perspective -> other [COLOR=Black]menu[/COLOR][/COLOR][COLOR=Black].[/COLOR]
I followed the steps given from the link [COLOR=Red]http://docs.joomla.org/Setting_up_your_workstation_for_Joomla!_development[/COLOR]  

Help me guys.....




Thanks

---

### Post by sanderd17 on 2011-05-31
What version of eclipse did you install? the version from the eclipse site or the version from the repositories.

I ask this because the version from eclipse itself contains some parts that Debian doesn't agree with. So Debian takes the nonfree parts out.

I suggest you to try the version from the site.

---

### Post by thoufiq on 2011-06-01
> **sanderd17 said:**
> What version of eclipse did you install? the version from the eclipse site or the version from the repositories.

I ask this because the version from eclipse itself contains some parts that Debian doesn't agree with. So Debian takes the nonfree parts out.

I suggest you to try the version from the site.

Hai Sanderd,
I am the new user of eclipse and i had removed the eclipse-ide fully and downloaded the eclipse helios version from the website[COLOR=Red][http://www.eclipse.org/downloads/download.php?file=/technology/epp/downloads/release/helios/R/eclipse-php-helios-linux-gtk.tar.gz](http://www.eclipse.org/downloads/download.php?file=/technology/epp/downloads/release/helios/R/eclipse-php-helios-linux-gtk.tar.gz)[/COLOR] . I extracted [COLOR=red]eclipse-php-helios-linux-gtk.tar.gz[/COLOR] file and i got the directory named eclipse, then i run the eclipse using the command [COLOR=red]./eclipse[/COLOR] and its working fine but still after i installed the subclipse, i cant found the [COLOR=red]svn perspective[/COLOR] in the window menu.
I used this link to install subclipse [COLOR=Red][http://subclipse.tigris.org/update_1.6.x](http://subclipse.tigris.org/update_1.6.x)[/COLOR] and the plugins i installed using this link are

  [COLOR=red]CollabNet Merge Client                                2.2.3
  JNA Library                                           3.2.7
  Subclipse (Required)                                  1.6.17
  Subclipse Integration for Mylyn 3.x (Optional)    3.0.0
  Subversion Client Adapter (Required)                    1.6.12
  Subversion JavaHL Native Library Adapter (Required)    1.6.15
  Subversion Revision Graph                            1.0.9
  SVNKit Client Adapter (Not required)                    1.6.15
  SVNKit Library                                    1.3.5.7406
[/COLOR]

I also tried to install eclipse in my desktop but the same svn  perspective cant found in windows menu. I dont know what is the cause  for this problem.
I want to install joomla project in eclipse ide for sharing, for that only i am using eclipse helios version.


Pls pls pls....... help me.

---

