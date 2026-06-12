---
title: "Looking for a fast booting os, with low power consumption but with diverse functional"
date: 2013-11-02
forum: Ubuntu, Linux and OS Chat
---

### Post by ads2996 on 2013-11-02
Hi,

I currently have a 4 year old HP touchsmart tm2 1010-ea laptop. I currently dual boot windows 7 and Ubuntu 12.04. I am currently looking for a really fast os that wont eat up my battery life but still let me do basic things like run Word (in wine). Or is Ubuntu the best pick already?

---

### Post by ajgreeny on 2013-11-02
On that hardware try Xubuntu or Lubuntu, both using much fewer resources than ubuntu.

If you can manage with E17 window manager you could also look at Bodhi.  It starts with very few applications by default, but it uses the ubuntu repos along with its own, so you can install anything that is available to ubuntu.  It also uses all the same methods of installation that you know already; it just looks so different to a standard DE that it takes a while to get used to.

Others that may be of interest that I have used are puppy, crunchbang, and I'm sure other forum users will come up with more to try.

---

### Post by Allavona on 2013-11-02
It all comes down to personal taste. There is a plethora of light-weight distros out there. ajgreeny just touched the surface. Find a few, make live cd/usb's and shop around.

---

### Post by tgalati4 on 2013-11-02
Linux Mint Mate will give you that 4-year-old, Gnome2 desktop that works with more of what you want and less of what you don't want.

---

### Post by dbass81 on 2013-11-02
> **ads2996 said:**
> Hi,

I currently have a 4 year old HP touchsmart tm2 1010-ea laptop. I currently dual boot windows 7 and Ubuntu 12.04. I am currently looking for a really fast os that wont eat up my battery life but still let me do basic things like run Word (in wine). Or is Ubuntu the best pick already?

Ubuntu is based on Debian.  Crunchbang is Debian running Openbox, which is a very lightweight WM.  You can try it, but it can be very "hackish" compared to Ubuntu.  It requires you to know "shortcut" keys to open apps if you don't know your way around a CLI.  I'm also using Debian with Openbox, but it's very custom, nothing like Crunchbang.  Go to the screenshots thread at the top of this forum if you want to see some screenshots.

---

### Post by david98 on 2013-11-04
The fastest way to boot os's is via a ssd but these can be pricey at the moment but very reliable in my opinion

---

### Post by mastablasta on 2013-11-04
chrunchbang or debian are lighter. so is bodhi. not sure how much battery you gain by using them though. there are a couple of battery management applicaitons you can try. tlp is one of them i believe.

ubuntu with Unity for exampler uses 3D rendering of windows (like win7 aero). that can draw power unnecessarily i think.

---

### Post by scythian.trigon on 2013-11-08
I'm running Lubuntu  13.10 really smooth, fast, stable
and you can expect Ubuntu's ease of configuration ,setup, and support for much tools and features

---

### Post by King Dude on 2013-11-08
I suggest Xubuntu, for the sake that it is efficient and still looks cool.

---

### Post by lykwydchykyn on 2013-11-08
Using any of the lighter desktop environments should speed your startup a bit and help battery life.

I also set up cpufreqd on my laptop and it's done wonders for my battery life.  It takes a bit of fiddling to get it set up, but well worth it.  I don't know if regular ubuntu has some kind of cpu frequency scaler built in, but cpufreqd works pretty well.

---

### Post by dbass81 on 2013-11-10
> **lykwydchykyn said:**
> Using any of the lighter desktop environments should speed your startup a bit and help battery life.

I also set up cpufreqd on my laptop and it's done wonders for my battery life.  It takes a bit of fiddling to get it set up, but well worth it.  I don't know if regular ubuntu has some kind of cpu frequency scaler built in, but cpufreqd works pretty well.

I didn't know about cpufreqd, thanks for the heads up.   I was messing around with the cpufreqd.conf and it doesn't do much for me.  I thought Intel SpeedStep works the same way?  Can I see your cpufreq.conf to see how you configured yours?

---

### Post by Hylas de Niall on 2013-11-10
> **dbass81 said:**
> Ubuntu is based on Debian.  Crunchbang is Debian running Openbox, which is a very lightweight WM.  You can try it, but **it can be very "hackish" compared to Ubuntu.  It requires you to know "shortcut" keys to open apps if you don't know your way around a CLI.**  I'm also using Debian with Openbox, but it's very custom, nothing like Crunchbang.  Go to the screenshots thread at the top of this forum if you want to see some screenshots.

Really?

The shortcuts are listed in the default Conky right there on the desktop, and there is little that cannot be accessed through the Openbox menu.

IMO #! is a *great* distro for lighter or older machines (as well as modern rigs), and it really doesn't demand *any* special skills of the user.

---

### Post by philinux on 2013-11-10
Moved to U L and OS chat.

---

### Post by lykwydchykyn on 2013-11-10
> **dbass81 said:**
> I didn't know about cpufreqd, thanks for the heads up.   I was messing around with the cpufreqd.conf and it doesn't do much for me.  I thought Intel SpeedStep works the same way?  Can I see your cpufreq.conf to see how you configured yours?

Sure:

```

# see CPUFREQD.CONF(5) manpage for a complete reference
#
# Note: ondemand/conservative Profiles are disabled because
#       they are not available on many platforms.

[General]
pidfile=/var/run/cpufreqd.pid
poll_interval=2
verbosity=4
[/General]

[acpi]
acpid_socket=/var/run/acpid.socket
[/acpi]

[sensors_plugin]
sensors_conf=/etc/sensors.conf
[/sensors_plugin]

[Profile]
name=Performance High
minfreq=100%
maxfreq=100%
policy=performance
[/Profile]

[Profile]
name=Performance Low
minfreq=60%
maxfreq=100%
policy=performance
[/Profile]

[Profile]
name=Powersave High
minfreq=60%
maxfreq=60%
policy=powersave
[/Profile]

[Profile]
name=Powersave Low
minfreq=30%
maxfreq=40%
policy=powersave
[/Profile]

[Profile]
name=Conservative High
minfreq=30%
maxfreq=100%
policy=conservative
[/Profile]

[Profile]
name=Conservative Low
minfreq=0%
maxfreq=66%
policy=conservative
[/Profile]

##
# Basic states
##
# when AC use performance mode
[Rule]
name=AC Rule
ac=on                    # (on/off)
profile=Performance High
[/Rule]
 
# stay in performance mode for the first minutes
[Rule]
name=AC Off - High Power
ac=off                   # (on/off)
battery_interval=70-100
#exec_post=echo 5 > /proc/acpi/sony/brightness
profile=Conservative High
[/Rule]

# conservative mode when not AC
[Rule]
name=AC Off - Medium Battery
ac=off                   # (on/off)
battery_interval=30-70
#exec_post=echo 3 > /proc/acpi/sony/brightness
profile=Conservative Low
[/Rule]

# conservative mode when not AC
[Rule]
name=AC Off - Low Battery
ac=off                   # (on/off)
battery_interval=0-30
#exec_post=echo 3 > /proc/acpi/sony/brightness
profile=Powersave Low
[/Rule]

##
# Special Rules
##
# CPU Too hot!
[Rule]
name=CPU Too Hot
acpi_temperature=55-100
cpu_interval=50-100
profile=Performance Low
[/Rule]

# use performance mode if I'm watching a movie
# I don't care for batteries! 
# But don't heat too much.
[Rule]
name=Movie Watcher
programs=xine,mplayer,gmplayer
battery_interval=0-100
acpi_temperature=0-60
cpu_interval=0-100
profile=Performance High
[/Rule]

```

---

