---
title: "[SOLVED] Installing FIRESTARTER in Ubuntu Hardy Heron:"
date: 2008-08-11
forum: Security
---

### Post by Bee Wildered on 2008-08-11
Installing FIRESTARTER in Ubuntu Hardy Heron:

PLEASE HELP: I am trying to install and activate Firestarter Firewall in Ubuntu Hardy Heron and have followed the instructions at:
[http://www.fs-security.com/docs/installation.php](http://www.fs-security.com/docs/installation.php)

I have checked the enable “universe” box in Repositories > Settings > Synaptic Package Manager.
I have then typed  - apt-get install firestarter – in the terminal box and pressed enter but it does not work and I just get the following message in response:

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)

E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


...any clues as to what I'm doing wrong?!

---

### Post by issih on 2008-08-11
Use sudo in front of the apt-get line, then type your login in password when prompted for it and hit enter

Hope that helps

P.S. just to explain, the program is complaining because you are not root, by default all users in ubuntu run as normal (non privileged) users. These users are restricted to changing files and directories they own. Consequently they can't change the guts of the system or indeed install much software. Most administrative tasks require root privileges.

In order to get around this, users that should have access to these administrative functions are placed in the sudoers group. These people have the power to act as the super or root user (sudo = super user do). When you run a command prefixed by sudo you are instructing the system to run the following command with root privileges, and in order to check you have the right to do that, and as a sanity check, the computer asks for your login password.

If you are launching a graphical application from the command line (rather than using a console app) then you must use gksudo rather than sudo. Plain old sudo will appear to work, but you can end up with complications at a later date as you are running in the normal users environment as root. Just use gksudo for graphical apps, its worth remembering.

---

### Post by hyper_ch on 2008-08-11
firestarter is not a firewall.

---

### Post by Vishal Agarwal on 2008-08-11
> **hyper_ch said:**
> firestarter is not a firewall.

I think it is a firewall. Otherwise what it is actually. And what is the firewall.

---

### Post by hyper_ch on 2008-08-11
> **Vishal Agarwal said:**
> I think it is a firewall. Otherwise what it is actually. And what is the firewall.

You think wrong.

Firestarter is (an outdated) configuration tool for the actual firewall/package filtering called iptables.

And very likely you don't even need to adjust the default settings.

---

### Post by issih on 2008-08-11
Whilst you are quite correct, to a new user (which this clearly is) that distinction is utterly irrelevant.

To him the gui application that allows him to configure the daemon processes IS the application. As for being outdated...probably, but ufw is command line, and new users get the jitters when thats forced upon them, let alone editing config files.

---

### Post by Oldsoldier2003 on 2008-08-11
A GUI interface for UFW is located here: [http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

A gentle reminder to all involved, let's help the user- not argue amongst ourselves.

---

### Post by Bee Wildered on 2008-08-11
Cheers folks,

Whatever Firestarter is it is now working and that makes me happy! Your patientce is much appreciated and, as you've no-doubt guessed, I'm a very recent refugee from microsoft...

Bee Wildered.

P.S. What's a 'fish'?

[http://ubuntuforums.org/images/icons/icon12.gif](http://ubuntuforums.org/images/icons/icon12.gif)

---

### Post by hyper_ch on 2008-08-11
> **issih said:**
> Whilst you are quite correct, to a new user (which this clearly is) that distinction is utterly irrelevant.

Not if you think longterm ;)

---

### Post by Vishal Agarwal on 2008-08-11
> **hyper_ch said:**
> You think wrong.

Firestarter is (an outdated) configuration tool for the actual firewall/package filtering called iptables.

And very likely you don't even need to adjust the default settings.

Frankly speaking,  I was not aware that firestarter is a configuration tool, not the firewall. 
This I know that the iptables is a firewall.

---

### Post by Vishal Agarwal on 2008-08-12
> **hyper_ch said:**
> You think wrong.

Firestarter is (an outdated) configuration tool for the actual firewall/package filtering called iptables.

And very likely you don't even need to adjust the default settings.

Last night I tried listing iptables with -L switch
W/o firestarter and then 
W/ firestarter,
and I came to know that the firewall rules was applied to iptables from firestarter.

Concept fully clear.

---

### Post by Francewhoa on 2010-03-04
**Type in the following command in TERMINAL to update your Ubuntu.**
```
sudo apt-get update
```[B]
Type in the following command in TERMINAL to install Firestarter.[/B]
```
sudo apt-get install firestarter
```Firestarter can be found under the following menu APPLICATIONS > INTERNET > FIRESTARTER

The following is optional.

**How to minimize Firestarter to a panel icon when closed. **
With Firestarter already opened navigate to 'Preferences'
Check "Enable tray icon"
Click on ACCEPT button

**How to make Firestarter start automatically at startup**
Navigate to menu 'System' -> 'Preferences' -> 'Sessions' -> 'Startup Programs' -> 'Add'
Fill the 3 following fields
Name
```
Firestarter
```Command
```
sudo firestarter --start-hidden
```Comment
```
Firestarter
```Click on OK button.
Click on CLOSE button.

---

### Post by Enigmapond on 2010-03-04
> **Onopoc said:**
> **Type in the following command in TERMINAL to update your Ubuntu.**
```
sudo apt-get update
```[B]
Type in the following command in TERMINAL to install Firestarter.[/B]
```
sudo apt-get install firestarter
```Firestarter can be found under the following menu APPLICATIONS > INTERNET > FIRESTARTER

The following is optional.

**How to minimize Firestarter to a panel icon when closed. **
With Firestarter already opened navigate to 'Preferences'
Check "Enable tray icon"
Click on ACCEPT button

**How to make Firestarter start automatically at startup**
Navigate to menu 'System' -> 'Preferences' -> 'Sessions' -> 'Startup Programs' -> 'Add'
Fill the 3 following fields
Name
```
Firestarter
```Command
```
sudo firestarter --start-hidden
```Comment
```
Firestarter
```Click on OK button.
Click on CLOSE button.

You do know that this thread is going on two years old and that firestarter is a dead programme? It hasn't been updated since 2005 and that GUFW is far better?? Just in case you weren't aware...

Cheers!

---

