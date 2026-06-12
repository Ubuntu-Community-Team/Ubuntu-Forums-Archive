---
title: "Redshift"
date: 2022-08-09
forum: Ubuntu/Debian BASED
---

### Post by jacksonguitars on 2022-08-09
Dear sirs and ladies! Any bright ideas on how to make Redshift work for non-admin users?

---

### Post by ajgreeny on 2022-08-09
You do not need to be an admin user to get redshift working but it does need the configuration file in ~/.config/redshift,conf to be created, and that file must of course, contain the correct details of location, colour temperature and brightness/gamma values you want in order for the application to work.
Can you please show us the content of your config file with the output of ```
cat .config/redshift.conf
```
Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

I also note that you have put this thread in the ***Ubuntu/Debian BASED*** section of the forum so can you please tell us what distro you're actually using as that could make a big difference to the answers given.

It is also possible if you are using Ubuntu that your graphic system is using **wayland**, not **xorg** and redshift does not work if using wayland.

---

### Post by jacksonguitars on 2022-08-11
Sir, thank you. Sir, this is the output of [COLOR=#000000][FONT=&amp]cat .config/redshift.conf
[/FONT][/COLOR] for my non-admin user.

Sorry. I'm using Ubuntu. I would give Debian a try though if you convince me.

```
[redshift]
location-provider=manual


[manual]
lat=57.70
lon=11.97
[randr]
screen=0
```

[COLOR=#000000][INDENT]It is also possible if you are using Ubuntu that your graphic system is using **wayland**, not **xorg** and redshift does not work if using wayland. SOLVED. I changed to xorg then somehow Ubuntu changed back to Wayland. 

I called it to early. It still does not work.[/INDENT]


[/COLOR]

---

### Post by ajgreeny on 2022-08-13
First stop redshift from autostarting, reboot (or maybe just logout and in again) then see what output you get if starting redshift in terminal.
That may give us some information and tell us why it will not run.

---

### Post by Dennis N on 2022-08-13
Since you say you are using Ubuntu, Ubuntu has a built-in Night Light application, so Redshift is not really necessary. 
Go to Settings > Display > Night Light.
Note: I you want to use the Sunset to Sunrise automatic activation, then you also need to turn on "Location Services" or that feature won't work.

---

### Post by ajgreeny on 2022-08-14
I don't use Ubuntu as I can't stand the gnome DE, but I wonder if there is a manual method to configure your location in night-light, as there is for redshift.
I personally prefer not to use location services unless absolutely necessary so I have latitude and longitude set in my redshift.conf file.

---

### Post by jacksonguitars on 2022-08-21
Night light did the trick. Ubuntu is like OSX. It's just not as pretty (I've used OSX for 6 years). Thank you all very much. Especially the Developers!

---

