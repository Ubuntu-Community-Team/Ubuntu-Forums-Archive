---
title: "My experiences with Ubuntu in the workplace"
date: 2010-11-05
forum: Testimonials &amp; Experiences
---

### Post by Ryan Dwyer on 2010-11-05
Hey all,

I'm a web developer and work in a team of about 10 other web developers. Our workplace uses a mix of Windows and Mac for desktops and Linux for our servers. I think most of the devs have at least heard of Ubuntu. I reluctantly use Windows XP but have been wanting to try Ubuntu at work for a while. I might start some sort of motion. :)

**Why I want to use Ubuntu**
- Keyboard shortcuts means I can work faster.
- It's a similar environment to our production servers (ie. Linux), so I won't have issues with case sensitivity in filenames or line breaks.
- I can run PHP interactively instead of having to create a script just to do something simple like check a timestamp.
- I can do stuff much faster from the Terminal like editing config files and controlling services/daemons.
- Computer will start faster.
- Programs won't "stop responding" when I try to shut down my computer.

I want to do this in my own time so if it turns out I can't use Ubuntu I won't have wasted any work time. So after I've done a day's work I stay late and work on installing/configuring Ubuntu the way I need it. My plan is to dual boot it using Wubi and symlink most of my important stuff so once I switch to Ubuntu, if anything goes wrong I can reboot into Windows and continue working with minimal downtime.

**My Windows setup**
- Windows XP
- Dual monitors with NVidia card
- WAMP (Apache, MySQL phpMyAdmin)
- PHP 5.1 (it's what our production servers use)
- FileZilla
- IE8, Chrome and Firefox
- Virtual machines for IE7 and IE6 using VirtualBox
- TortoiseSVN
- Photoshop and GIMP (need to open PSDs to create cutups)
- RescueTime (time tracking tool required by company policy)
- Thunderbird
- Geany (yes, the Windows version)
- Pidgin (we talk via MSN)
- Office (to open docs and read specs, not for creating docs)

**My Ubuntu plan**
- Ubuntu 10.10
- Latest versions of Apache and MySQL
- Pinned PHP 5.1 or 5.2
- Firefox and Chromium
- Virtual machines for IE8/7/6 using VirtualBox
- GIMP
- Thunderbird
- Geany
- Pidgin
- FileZilla
- RabbitVCS for SVN
- RescueTime (a Linux data collector is available but it's not in a repo)
- Symlink www directory, MySQL data directory, emails, FileZilla sites and Pidgin chatlogs.
- Docky and Compiz for maximum impressiveness :)

I'm hoping my work colleagues will be impressed and might switch as well, so I'm keeping an eye out for usability issues which may deter them.

**Day 1** (yesterday)
I took an Ubuntu 10.10 ISO with me to work and installed it using Daemon Tools and Wubi. I gave it a 20GB disk. During the install it said "copying files" with an expand icon. I expanded it and the info was way too technical (a debug console or something). I was expecting it to show me the filenames being copied. I think this should be removed or changed because it offers nothing to a standard user except scaring them into thinking the OS is for tech-heads.

After installing, I went to enable Compiz and it prompted me to install NVidia's driver, so I did. The version it installed wasn't the recommended version though. I went into Additional Drivers and had to update to the recommended one. Making the dual monitors act how I wanted them to was a bit difficult with NVidia's config tool. It has something called Xinerama which needs to be enabled, but doesn't tell you what it is or what it does. I had to Google it to find out how to extend the desktop onto the second screen. I think that could be improved. Also, when saving the NVidia config it complained that /etc/X11/xorg.conf didn't exist, but I know it's not required in the latest versions of Ubuntu. By the way, the first time I did this I was using the non-recommended driver and it broke Xorg. I had to use the CLI environment to remove xorg.conf. Usability FAIL.

Also, after installing the NVidia driver (or configuring xorg.conf) the startup screen now shows the text "Ubuntu 10.10" or whatever it is in the CLI font. It also displays some bootup messages on the same screen which looks messy.

After logging in, I get a notification from Avahi about our .local domain. The message is technical in nature and would probably confuse a lot of people (especially newbies who don't understand DNS or hostname resolution). I think it would be better if this message just wasn't shown. It said network service discovery would be disabled but I still get a list of computers in Places > Network.

In Docky, for some reason when I right click an application the pin option is missing. I Googled this but didn't find anything related to it. I tried again on day 2 and it was there for Geany but not Thunderbird. Weird.

On this day I also did the following which went without problems:
- Symlinked www directory and tested permissions OK.
- Installed Chromium, Geany, Compiz settings manager.
- Started setting up keyboard shortcuts and Bash aliases.
- Installed and configured Pidgin but still need to symlink the chatlog directory.

**Day 2** (today)
Trying to install a previous version of PHP is tricky. I settled for PHP 5.2. Again using Google, I found I had to add karmic repos and pin packages, but then phpMyAdmin complained of dependency problems with php5-mcrypt. I Googled this later and found a solution but haven't implemented it yet. I think the whole process of installing a previous version should be made easier. I think the OS should be aware of the previous distros' repos which are still supported. Maybe in software center have an option to install a previous version and automatically pin it if they do. In this case dependencies should be resolved automatically if possible. A user friendly dependency message would be nice too (instead of saying "phpmyadmin depends on php5-mcrypt but it is not going to be installed").

When setting up Thunderbird, I couldn't find a way to change an account from IMAP to POP once the account is created. I had to delete the account and change it during the account creation process. However, when I try to create the account it tells me the "incoming server already exists." WTF? I'm still working on this one.

I installed RabbitVCS and it picked up the state of all my repos. Remember, my Windows www directory is symlinked to Ubuntu. It knows which repos are up to date and which have uncommitted changes. That's awesome. I also symlinked my MySQL data directory and had a few issues with AppArmor blocking access, but after Googling I got that resolved.

I'm particularly pleased about a script I wrote which watches Apache's error log for changes and notifies me via notify-send. I'm sure my colleagues will be jealous.

I ported one of my Windows scripts to Ubuntu. It reads my repo list and generates the vhost files for Apache. I had to edit /etc/sudoers to give it permission to reload Apache but it didn't take effect. I found out later I need to restart X after changing /etc/sudoers. It would be nice if there was a comment in the file explaining this. By the way, I set up a keyboard shortcut for this script so I can reconfigure Apache for a new repo pretty much instantly. Combined with the log watching script, I get a notification telling me Apache has reloaded when I do. :)

Other things I did today include installing FileZilla, VirtualBox, GIMP and Ghex. I symlinked FileZilla's sites file and tested it successfully. Oh, and I configured Compiz to make windows burn in fire when I close them. :)

I'm really hoping some of the other developers at work will try Ubuntu after seeing that it's a decent OS and offers some things that Windows doesn't. The best way is to lead by example.

Unfortunately I won't be at work again until Wednesday, so my next update will be then.

---

