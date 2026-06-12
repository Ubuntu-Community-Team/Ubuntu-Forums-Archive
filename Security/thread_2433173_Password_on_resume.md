---
title: "Password on resume"
date: 2019-12-15
forum: Security
---

### Post by mangoduck on 2019-12-15
I have searched here and found nothing. Often I will resume and a password is not asked for, I just end up at a functional desktop. Phenomenon seems to come and go with regular updates and I would think people would not let it regress in this way, but after seemingly inconsequential and regular updates it recurs. Usually, it prompts for pass (after first showing the whole world whatever I was doing), but sometimes not. I can't trust that a particular update will or won't let people right in. 18.04 LTS. Anyone else experienced this?

---

### Post by TheFu on 2019-12-15
I have not.  I don't use Gnome3. **xscreensaver-demo** is the program I use to control the screen saver, but each DE seems to have a different program.

For others who might confuse locking,  there are 3 times when a password is needed. Each is configurable.
* Login
* Screen lock
* When using sudo

In home environments, many people choose not to be prompted for a password at login. This is especially popular with media center setups.

Screen lock settings are often tied to power settings.  It is common to force a locked screen after 30 minutes, but it can be setup in many different ways.  This would be configured differently based on the window manager and desktop environment.  Most DE manuals will have a specific section on this topic.   [https://help.ubuntu.com/stable/ubuntu-help/privacy-screen-lock.html.en](https://help.ubuntu.com/stable/ubuntu-help/privacy-screen-lock.html.en) is for 19.10 using gnome3 DE.  If this setting is incomplete or gets reset somehow, all bets are off.
It might have something to do with snap packages. More and more packages in Ubuntu are being distributed as snaps with highly restricted access to directories.  Having the ability to read/write desktop settings would critical for snaps, but we never know.  **snap list** will show a list of installed snaps. See if your DE is in that list and see if the screen-saver or power management are too.  Screen blanking, screen locking, and going into standby are each different controls.  I use **xscreensaver-demo** to control the settings, but I'm not running Gnome2/3/whatever. The "Advanced" settings have the power management options.

The last way is via sudo.  Every time a successful sudo authentication happens, a file is written to the $HOME of the userid. sudo can be configured to allow reoccurring access without any credentials by the timeout option in the sudoers file. 15 minutes is the default value.  Use **sudo visudo** to check this file.

If you've verified each of those places and there is still an issue, please open a bug.

---

