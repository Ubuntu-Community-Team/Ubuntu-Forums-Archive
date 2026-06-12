---
title: "Ratel likes to Dim (!?!)"
date: 2012-11-26
forum: System76 Support
---

### Post by nealaustin on 2012-11-26
Just got a beautiful Ratel and everything is great.... except for this one little quirk. When watching videos the screen blacks suddenly after 10 minutes. Touch a key and it's back for another 10 minutes. Works fine while typing. Hmmm <System settings>,<Power> It's set "don't suspend" and "Never" show battery status in the menubar. I tried setting it to "1 hour" ect. to no avail. Hmmm <System Settings>, <Brightness and lock>. I set it to never. I guess this is where I turn off the pesky lock after it returns. Yep that works but it still shuts off. I click on the "dim to save power" and it works! That wasn't dimming that was total blackness. The whole deal was confusing. That has been the only thing and with a little searching. I think it could be an OS thing so the Ratel gets 5 stars. Hats off to System 76.

---

### Post by ibjsb4 on 2012-11-26
Caffeine ?

[http://ubuntu-tweak.com/app/caffeine/](http://ubuntu-tweak.com/app/caffeine/)

[https://launchpad.net/~caffeine-developers/+archive/ppa?field.series_filter=quantal](https://launchpad.net/~caffeine-developers/+archive/ppa?field.series_filter=quantal)

---

### Post by isantop on 2012-11-27
> **nealaustin said:**
> Just got a beautiful Ratel and everything is great.... except for this one little quirk. When watching videos the screen blacks suddenly after 10 minutes. Touch a key and it's back for another 10 minutes. Works fine while typing. Hmmm <System settings>,<Power> It's set "don't suspend" and "Never" show battery status in the menubar. I tried setting it to "1 hour" ect. to no avail. Hmmm <System Settings>, <Brightness and lock>. I set it to never. I guess this is where I turn off the pesky lock after it returns. Yep that works but it still shuts off. I click on the "dim to save power" and it works! That wasn't dimming that was total blackness. The whole deal was confusing. That has been the only thing and with a little searching. I think it could be an OS thing so the Ratel gets 5 stars. Hats off to System 76.

It's certainly an Ubuntu bug; we were seeing the same problem at UDS on 12.10 on the Lemur, Gazelle, and Sable.

---

### Post by levlaz on 2012-12-03
Not sure if this will help, but I've always had this problem with gnome 2, and gnome 3. If you are using Unity I am not sure what the procedure would be but perhaps my fix will help. 

I always thought it was a power setting, but it turns out its the screensaver. By default on gnome2 the screen saver is a black screen. Also by default the computer is  considered idle after 5 minutes and it will dim and then go to the blank screen. 

All you had to do is adjust the Screensaver Preferences to change this. I have not used Unity but in gnome 2 its simply System --> Preferences --> Screensaver.

---

### Post by mrSpaceman on 2012-12-16
So, I'm having a similar problem here with Ubu 12.10 and Unity (though I think I have a Gnome desktop installed also, even if I'm not using it).  There's no Settings->Screensaver which means the solution is a little trickier.  

I'm going to try and disable gnome-screensaver from the CLI.  I might just remove the package. I'll let y'all know what works.

---

### Post by mrSpaceman on 2012-12-16
**What I tried:**

[FONT="Courier New"]gconftool-2 --direct \
  --config-source xml:readwrite:/etc/gconf/gconf.xml.mandatory \
  --type bool \
  --set /apps/gnome-screensaver/idle_activation_enabled false[/FONT]

**What I found:**

I'm not sure that it worked (the screen is still periodically blanking, I think).  I'm going to restart the machine and then see.  Since I've already written this, I'll post it now and add more when I can say for definite.

**Info sources:**

[COLOR="Blue"]*[https://live.gnome.org/GnomeScreensaver/FrequentlyAskedQuestions#I.27m_a_systems_administrator.__How_can_I_set_policies_for_all_users_of_my_system.3F](https://live.gnome.org/GnomeScreensaver/FrequentlyAskedQuestions#I.27m_a_systems_administrator.__How_can_I_set_policies_for_all_users_of_my_system.3F)*[/COLOR]

[COLOR="Blue"]*[http://people.gnome.org/~bmsmith/gconf-docs/C/gnome-screensaver.html](http://people.gnome.org/~bmsmith/gconf-docs/C/gnome-screensaver.html)*[/COLOR]

[COLOR="Blue"]*[http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/)*[/COLOR]

---

### Post by mrSpaceman on 2012-12-16
**Result**:

The above approach worked! :KS

**Note**: I didn't restart the desktop.  The reason I thought the procedure hadn't worked was because I was previously playing with the Unity power features and hadn't disabled the screen off option here (I was testing to see if it was this feature that was making the problem).

---

### Post by nealaustin on 2012-12-29
> **mrSpaceman said:**
> **What I tried:**

[FONT="Courier New"]gconftool-2 --direct \
  --config-source xml:readwrite:/etc/gconf/gconf.xml.mandatory \
  --type bool \
  --set /apps/gnome-screensaver/idle_activation_enabled false[/FONT]

**What I found:**

I'm not sure that it worked (the screen is still periodically blanking, I think).  I'm going to restart the machine and then see.  Since I've already written this, I'll post it now and add more when I can say for definite.

**Info sources:**

[COLOR="Blue"]*[https://live.gnome.org/GnomeScreensaver/FrequentlyAskedQuestions#I.27m_a_systems_administrator.__How_can_I_set_policies_for_all_users_of_my_system.3F](https://live.gnome.org/GnomeScreensaver/FrequentlyAskedQuestions#I.27m_a_systems_administrator.__How_can_I_set_policies_for_all_users_of_my_system.3F)*[/COLOR]

[COLOR="Blue"]*[http://people.gnome.org/~bmsmith/gconf-docs/C/gnome-screensaver.html](http://people.gnome.org/~bmsmith/gconf-docs/C/gnome-screensaver.html)*[/COLOR]

[COLOR="Blue"]*[http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/)*[/COLOR]

It didn't work for me and this is driving my wife nuts. It's her new computer. I am almost temted to put Mint on it. I tried that distro for a while and had no problems on my Starling. I really wonder why Conical went away from gnome. When I use the terminal it's like puting a monkey in front of a piano. Anyone with a solution for me?

---

### Post by nealaustin on 2012-12-29
> **ibjsb4 said:**
> Caffeine ?

[http://ubuntu-tweak.com/app/caffeine/](http://ubuntu-tweak.com/app/caffeine/)

[https://launchpad.net/~caffeine-developers/+archive/ppa?field.series_filter=quantal](https://launchpad.net/~caffeine-developers/+archive/ppa?field.series_filter=quantal)

Hey IBJ you put up a word and I go and overlook the whole message. What the hell can coffee do for me? Well... now I got a (steaming) cup of coffee on the task bar and a happy wife in front of her computer!  THANKS

---

### Post by alabamaIII on 2012-12-29
I was having the same problem. And tried this, before trying the earlier post about Caffiene.

I went to Installed Software via the Software Centre. I chose 'System Settings(GNOME control centre)'. When I was on the installation page for System Settings, I deselected 'GNOME Screensaver and lock' from the Add Ons list. Then chose apply changes.

At first it didn't work. Since then I've rebooted 4 times for other reasons. And now for the past few hours, I haven't had an automatic blank screen every 10 minutes.

I am using Ubuntu 12.10

---

