---
title: "Auto login selection not working with gdm"
date: 2012-09-30
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by kansasnoob on 2012-09-30
I know Ubuntu and most of the herd are now using lightdm, but Jeremy Bicha's Ubuntu GNOME Remix uses gdm.

During the most recent install I did not select auto-login. Now when I open the System Settings > User Accounts UI, unlock and select auto-login = On, the setting change is not respected.

I'd guess that it's a compatibility issue between the User Accounts UI and gdm, but thought I'd see what others know about the issue ;)

The closest related bug I've found is this:

[https://bugzilla.gnome.org/show_bug.cgi?id=684926](https://bugzilla.gnome.org/show_bug.cgi?id=684926)

But I don't quite think this is the same exact thing :confused:

---

### Post by tista on 2012-09-30
> **kansasnoob said:**
> I know Ubuntu and most of the herd are now using lightdm, but Jeremy Bicha's Ubuntu GNOME Remix uses gdm.

During the most recent install I did not select auto-login. Now when I open the System Settings > User Accounts UI, unlock and select auto-login = On, the setting change is not respected.

I'd guess that it's a compatibility issue between the User Accounts UI and gdm, but thought I'd see what others know about the issue ;)

The closest related bug I've found is this:

[https://bugzilla.gnome.org/show_bug.cgi?id=684926](https://bugzilla.gnome.org/show_bug.cgi?id=684926)

But I don't quite think this is the same exact thing :confused:

Hi kansasnoob :)

If you didn't check this file out, please follow it first:

**1. Open the file with editors whichever you'd like to use:**
```
gksu gedit /etc/gdm/custom.conf
```

**2. Add these options to that file like this:**
```
# GDM configuration storage
#
# See /usr/share/gdm/gdm.schemas for a list of available options.

[daemon]
# Enabling automatic login
[color=red][b]AutomaticLoginEnable = true
AutomaticLogin = YOUR_ACCOUNT_NAME[/b][/color]
.
.
.

```

**3. Then save and reboot and check if your machine could accept "auto-login" as normally...**

Best regards,
Tista

---

### Post by kansasnoob on 2012-09-30
OK, looking at the default "/etc/gdm/custom.conf" I'm inclined to think I could just uncomment these two lines:

```
# GDM configuration storage
#
# See /usr/share/gdm/gdm.schemas for a list of available options.

[daemon]
# Enabling automatic login
**[COLOR="Red"]#[/COLOR]**  AutomaticLoginEnable = true
**[COLOR="Red"]#[/COLOR]**  AutomaticLogin = user1

# Enabling timed login
#  TimedLoginEnable = true
#  TimedLogin = user1
#  TimedLoginDelay = 10

# Reserving more VTs for test consoles (default is 7)
#  FirstVT = 9

[security]

[xdmcp]

[greeter]
# Only include selected logins in the greeter
# IncludeAll = false
# Include = user1,user2

[chooser]

[debug]
# More verbose logs
# Additionally lets the X server dump core if it crashes
#  Enable = true
```

Does that make sense?

---

### Post by tista on 2012-09-30
> **kansasnoob said:**
> OK, looking at the default "/etc/gdm/custom.conf" I'm inclined to think I could just uncomment these two lines:

```
# GDM configuration storage
#
# See /usr/share/gdm/gdm.schemas for a list of available options.

[daemon]
# Enabling automatic login
**[COLOR="Red"]#[/COLOR]**  AutomaticLoginEnable = true
**[COLOR="Red"]#[/COLOR]**  AutomaticLogin = user1

# Enabling timed login
#  TimedLoginEnable = true
#  TimedLogin = user1
#  TimedLoginDelay = 10

# Reserving more VTs for test consoles (default is 7)
#  FirstVT = 9

[security]

[xdmcp]

[greeter]
# Only include selected logins in the greeter
# IncludeAll = false
# Include = user1,user2

[chooser]

[debug]
# More verbose logs
# Additionally lets the X server dump core if it crashes
#  Enable = true
```

Does that make sense?

Yeah it makes sense... ;P

This is the problem that gdm configurations didn't sync with gnome-control-center I suppose. But if we could handle such configs via dconf-services (or account-services), then it meant to be "There would be no need to store any configs into local plain-text files"...

When?

Oh I don't know, sorry. Anyway I've confirmed your issue as "bug" on gdm 3.6.0 since 3.5.3 could sync with gnome-control-center properly. :P

So we'd better to file this bug to Gnome bugzilla if it haven't been reported before, then you could do that? or me?

Best Regards,
Tista

---

### Post by kansasnoob on 2012-09-30
I'm just headed out to try and take care of some non-puter issues but let me check this out closer this evening. Jeremy Bicha did mention in the Beta 2 release notes:

> Some GNOME apps will not be upgraded to 3.6 for the 12.10 release. If you want these, try the GNOME3 PPA. Affected apps include Aisleriot, Nautilus, **System Settings**, and Totem. 

So I wonder if we even need a bug report?

Maybe we could try 'gnome-control-center' from a PPA first?

I seem to recall Jeremy saying something about not having had time to get the 3.6 version into the PPA, but I can't find that comment ATM :(

---

### Post by kuvanito on 2012-09-30
this took care for me:
for ubuntu:

sudo gedit /etc/gdm/custom.conf

then copy and paste the text below exactly as it shows but enter your user name

[daemon]
AutomaticLoginEnable=true
AutomaticLogin=YOUR USER NAME HERE

save and reboot.

pretty much the same as you guys explained before me,just no # signs no spaces,then again i am not using Gnomebuntu but Ubuntu My Way (gdm)

---

### Post by kansasnoob on 2012-10-01
I was curious what a default "/etc/gdm/custom.conf" would look like if auto-login were selected during installation so here it is:

```
# GDM configuration storage
#
# See /usr/share/gdm/gdm.schemas for a list of available options.

[daemon]
AutomaticLoginEnable=true
AutomaticLogin=lance
TimedLoginEnable=true
TimedLogin=lance
TimedLoginDelay=10
# Enabling automatic login

# Enabling timed login

# Reserving more VTs for test consoles (default is 7)
#  FirstVT = 9

[security]

[xdmcp]

[greeter]
# Only include selected logins in the greeter
# IncludeAll = false
# Include = user1,user2

[chooser]

[debug]
# More verbose logs
# Additionally lets the X server dump core if it crashes
#  Enable = true
```

I'll get back to this tomorrow :)

---

### Post by Harry33 on 2012-10-01
Maybe some issues with GDM and Ubuntu's Gnome-control-center are due to the fact that Ubuntu is still using the old version of gnome-control-center (3.4.2).
The newest is 3.6.0 and that can be downloaded from the Ricotz Staging PPA.

There are some issues with the G-C-C 3.6.0 version and Unity however.

---

### Post by kansasnoob on 2012-10-01
> **Harry33 said:**
> Maybe some issues with GDM and Ubuntu's Gnome-control-center are due to the fact that Ubuntu is still using the old version of gnome-control-center (3.4.2).
The newest is 3.6.0 and that can be downloaded from the Ricotz Staging PPA.

There are some issues with the G-C-C 3.6.0 version and Unity however.

Thanks, I hadn't thought to check Ricotz Staging :)

I'll give that a whirl soon. I was just looking through a couple of older threads for something possibly, sort of, related.

I think I recall Jeremy Bicha discussing a log-out issue with someone, but can't find the conversation now :(

What I've noticed is that if I select "auto-login" during install then log-out appears not to work, but if I do NOT select "auto-login" then log-out works perfectly fine.

I'd assume that it has to do with the "timed login" section of "/etc/gdm/custom.conf", but I need to experiment a little bit.

---

### Post by kansasnoob on 2012-10-01
BTW I've installed all three of these PPA's:

[https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3)

[https://launchpad.net/~ricotz/+archive/testing](https://launchpad.net/~ricotz/+archive/testing)

[https://launchpad.net/~ricotz/+archive/staging](https://launchpad.net/~ricotz/+archive/staging)

Then after updating the repos:

```
lance@lance-desktop:~$ sudo apt-get install gnome-control-center
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  grub-pc-bin libgtkmm-2.4-1c2a libreadline5 linux-headers-3.5.0-15
  linux-headers-3.5.0-15-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gkbd-capplet gnome-control-center-data gnome-settings-daemon
  libgnome-control-center1
The following NEW packages will be installed:
  gkbd-capplet
The following packages will be upgraded:
  gnome-control-center gnome-control-center-data gnome-settings-daemon
  libgnome-control-center1
4 upgraded, 1 newly installed, 0 to remove and 65 not upgraded.
Need to get 12.2 MB of archives.
After this operation, 16.8 MB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

Now I'll see what dragons I can unleash :lolflag:

---

### Post by kansasnoob on 2012-10-01
No apparent change :(

---

### Post by kansasnoob on 2012-10-01
Okey dokey, here's what I've learned.

Just removing the comments here are not enough:

```
[daemon]
# Enabling automatic login
**[COLOR="Red"]#[/COLOR]**  AutomaticLoginEnable = true
[COLOR="Red"]#[/COLOR]  AutomaticLogin = user1

```

The user name must actually be set to the true username, eg: lance - no real surprise there ;)

Regarding the log-out issue I'm also wrong. Once auto-login is set, whether manually by editing "/etc/gdm/custom.conf" or during installation, then log-out does NOT work.

But if you install Ubuntu GNOME Remix w/o choosing auto-login the the log-out option works just fine.

Does this make sense :confused:

About reporting a bug. I have a Launchpad account, but no Bugzilla account, so I'd appreciate some help :D

I'm just a tired, old tester that ain't quite ready to hang up his cyber-spurs yet :lolflag:

---

### Post by kansasnoob on 2012-10-02
Purely as a usability work-around I installed lightdm by installing the package 'lightdm-gtk-greeter'. Then I purged the ppa packages so I'm back to using only native packages with the proposed repo activated.

Now that I'm using lightdm auto-login selection using gnome-control-center works fine, and log out works fine whether auto-login is set to yes or no.

So tista is clearly correct about gdm being buggy ;)

Edit: I just thought to add, the reason I mentioned specifically installing 'lightdm-gtk-greeter' is because if you try to just install 'lightdm' it wants to install the unity greeter and a lot of other unneeded pkgs like compiz.

---

### Post by kansasnoob on 2012-10-07
I'm testing the latest gdm from Ricotz staging (along with all other packages in Ricotz testing & staging and the Gnome 3 PPA) and the issue about gdm not following the settings applied in System Settings appears to be fixed :)

But the log out issue still exists if auto-login is selected. And I got an automated crash report this time:

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1063267](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1063267)

I'll follow up more later.

---

