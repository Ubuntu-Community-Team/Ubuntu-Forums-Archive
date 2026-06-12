---
title: "Add startup application by command line"
date: 2011-05-26
forum: Server Platforms
---

### Post by Z.K. on 2011-05-26
I would like to know how to use the command line to add a startup application.  I know how to do it graphically as in System->Preferences->Startup Applications->Add or check/uncheck an application.  How would I do this by the command line.  Is there a configuration file that I can edit for this?

The reason I want to do this is when I remote into a machine using ssh, I don't have access to the Gnome GUI.

---

### Post by ruffEdgz on 2011-05-26
I would read more on update-rc.d:
```

man update-rc.d

```

This is a good read and you will also need to understand LSBinitScripts:
---
[http://wiki.debian.org/LSBInitScripts]("http://wiki.debian.org/LSBInitScripts")
---

If you have any additional information on what init level you need an application to start, any requirements for starting up or shutting down and I can give you a better step-by-step entry on what you need to do.

---

### Post by sisco311 on 2011-05-26
> **Z.K. said:**
> I would like to know how to use the command line to add a startup application.  I know how to do it graphically as in System->Preferences->Startup Applications->Add or check/uncheck an application.  How would I do this by the command line.  Is there a configuration file that I can edit for this?

The reason I want to do this is when I remote into a machine using ssh, I don't have access to the Gnome GUI.

Just copy (delete) the application's .desktop file to (from) ~/.config/autostart/

The .desktop files are usually located at /usr/share/applications, but you can create a custom one if you want.

For more info, check out:

[http://standards.freedesktop.org/autostart-spec/autostart-spec-0.5.html](http://standards.freedesktop.org/autostart-spec/autostart-spec-0.5.html)
and
[http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html)

---

### Post by psrdotcom on 2011-09-16
Thanks. It is somewhat useful information.

---

### Post by BkkBonanza on 2011-09-16
You have a couple different issues here. 

The GUI method you know about actually adds an app to start when you login using the .desktop method above

The update-rc.d (or more current Upstart, /etc/init/*.conf) methods both start a program when the system starts (boots), which is before you login and will start even if you don't login.

Neither are going to run a program when you login with ssh remotely. For that the simplest method is to add the command to your ~/.bashrc (but then it will also run when you open a terminal). 

Another way is to create a ~/.ssh/config file and add a LocalCommand option for the host (and PermitLocalCommand) - see **man ssh_config**.

There are other ways with ssh as well - eg. it's simple to add the command to the ssh login command itself, but if you want to have a active shell then you would need to run a script that runs your program and opens a sub-shell. No doubt someone will chime in with a smart way to do that too.

---

### Post by SlugSlug on 2011-09-22
crontab -e
add something like 

@reboot /bin/ls

---

### Post by OzzyFrank on 2012-05-05
Does anyone know the actual command to initiate the "Startup Applications" app? I've upgraded to 12.04, and at least in the Classic desktop which I use, there is now no way to access it via GUI (my user menu looks like in 11.10, and there is no "Startup Applications" there like I see in 12.04 screenshots. I'd rather use that than be dragging .desktop files in and out of ~/config/autostart. Cheers.

---

### Post by BkkBonanza on 2012-05-05
I just checked my menu item properties for "Startup Applications" in 11.04 and it lists, **gnome-session-properties** as the app it runs.

---

### Post by OzzyFrank on 2012-05-06
> **BkkBonanza said:**
> I just checked my menu item properties for "Startup Applications" in 11.04 and it lists, **gnome-session-properties** as the app it runs.

Thanks buddy! And yeah, after the 12.04 upgrade, all those "System" menu items that ended up in Applications > Other when Gnome 3 got rid of that menu (for reasons I've still yet to fathom) have totally disappeared, yet obviously the apps are still around. Cheers.

---

### Post by penguinsudo on 2012-05-21
ubuntu 12 classic fall back using GUI. 

[http://ubuntugenius.wordpress.com/2012/05/11/ubuntu-12-04-upgrade-fix-access-missing-startup-applications-in-gnome-3-classicfallback-desktop/](http://ubuntugenius.wordpress.com/2012/05/11/ubuntu-12-04-upgrade-fix-access-missing-startup-applications-in-gnome-3-classicfallback-desktop/)

Unity sucks

---

### Post by OzzyFrank on 2012-05-21
> **penguinsudo said:**
> ubuntu 12 classic fall back using GUI. 

[http://ubuntugenius.wordpress.com/2012/05/11/ubuntu-12-04-upgrade-fix-access-missing-startup-applications-in-gnome-3-classicfallback-desktop/](http://ubuntugenius.wordpress.com/2012/05/11/ubuntu-12-04-upgrade-fix-access-missing-startup-applications-in-gnome-3-classicfallback-desktop/)

Unity sucks

Unity is getting better. However, the lack of taskbar is what's keeping me using Classic. I'd rather not have to do some weird mix of Classic running in Unity to get back such a standard (on all OSes) feature. And thanks for sharing my blog link, hehe!

---

### Post by OzzyFrank on 2012-05-21
PS: I totally did not see that upon upgrade to 12.04, I've basically got my System menu back. As most of you are aware, when Classic got upgraded to v3, the **System** menu disappeared, but the apps ended up in **Applications > Other**. After upgrading to 12.04, those had disappeared from **Other** as well, and I've only just realised my **Applications > System Tools** menu now has 2 familiar sub-menus, being **Administration** and **Preferences**.

---

