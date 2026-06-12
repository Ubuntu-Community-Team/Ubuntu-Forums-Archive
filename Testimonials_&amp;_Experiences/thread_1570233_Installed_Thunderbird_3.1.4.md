---
title: "Installed Thunderbird 3.1.4"
date: 2010-09-07
forum: Testimonials &amp; Experiences
---

### Post by uRock on 2010-09-07
I upgraded to it and it even has a click to install for Lightning on the first page where it shows what is new in the version.

If anyone out there is like me and was unhappy with Lightning dying with an update a month back, then this may be good news.

uRock

---

### Post by sixthwheel on 2010-09-08
I'm going to have to check it out. Thanks
I went back to Evalution a few weeks ago.

---

### Post by uRock on 2010-09-08
If you need help getting it installed and running, then feel free to let me know.

I can't live without being able to update calenders with the wife with both of us being full time students and having other projects going on.

uRock

---

### Post by oh henry on 2010-09-09
> **uRock said:**
> If you need help getting it installed and running, then feel free to let me know.

I can't live without being able to update calenders with the wife with both of us being full time students and having other projects going on.

uRock

Please tell me more, how did you do it?

---

### Post by uRock on 2010-09-09
Uninstall Thunderbird via terminal, Synaptic, or USC.

Download the Thunderbird Package from the Mozilla website.

Move it to the /home folder.

Right-click and select to "Extract Here"

In the menu, go to Applications> Accessories> gedit Text Editor

In the text editor, copy and paste the following text;

```
# This file is for launching Thunderbird.
cd ~/thunderbird
./thunderbird
```

Save the file in the /home folder as .tbird

Open a terminal and enter the following command tto make the launcher executable;
```
chmod +x .tbird
```

Now for the easy part, adding the launcher to your main menu. Go to System> Preferences> Main Menu. In the left pane, either click Internet or Office, whichever place you prefer, then on the right, click New Item.

Name it Thunderbird and in the command box enter ./.tbird

To get the thunderbird icon, click the current icon and navigate to the thunderbird floder in your /home folder, then go to thunderbird> chrome> icons> default then select default256.png

Then after selecting the icon, you can close the Launcher Propoerties window and go through the menus and launch Thunderbird.

Congrats! You now have Thunderbird installed and running.

uRock

---

### Post by jonathonblake on 2010-09-09
> **uRock said:**
> 
I can't live without being able to update calenders 

Where do you get a 64 bit version of Lightning that works that version of Thunderbird?

jonathon

---

### Post by uRock on 2010-09-09
> **jonathonblake said:**
> Where do you get a 64 bit version of Lightning that works that version of Thunderbird?

jonathon
For 64bit, you may have to install Sunbird. Or install the 32bit version of thunderbird.

Edit: I dropped 64bit Ubuntu from my system a few weeks ago, because of compatibility issues with Cisco PacketTracer and, at the time, Thunderbird.

---

### Post by jonathonblake on 2010-09-11
> **uRock said:**
> For 64bit, you may have to install Sunbird. Or install the 32bit version of Thunderbird.

So the options are either to use a program that is no longer being developers (Sunbird), or downgrade the OS.

The more I use Thunderbird the more disgusted with it I become. Unfortunately, it is the only thing for *Nix that almost resembles an email client. (If anybody wants to complain about my attitude towards *Nix email clients, respond at [http://ubuntuforums.org/showthread.php?t=1564478](http://ubuntuforums.org/showthread.php?t=1564478) , not here.)

jonathon

---

### Post by uRock on 2010-09-12
To make that even more fun, Sunbird isn't in the repos for 10.04.

---

### Post by wilee-nilee on 2010-09-12
So 3.1.3 is already in Maverick for Lucid there is this ppa.
[https://launchpad.net/~lucid-bleed/+archive/ppa](https://launchpad.net/~lucid-bleed/+archive/ppa)

---

### Post by malibusurfer2 on 2010-09-14
It took me a while to get the new version of Thunderbird installed and my old mail and settings moved over from version 2, so here is some help for other users.:KSThis is on Ubuntu 9.04 Jaunty:

First, make a backup of your .mozilla-thunderbird folder!

Just add the following line to your sources.list.

System, Administration, Software Sources:

deb [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main

Open a Terminal window (Applications, Accessories, Terminal):

sudo apt-get update
sudo apt-get install thunderbird-mozilla-build 

If you get error regarding public key not available, then:
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29

To import old settings and email boxes and emails from Thunderbird v2:

Old files are in .mozilla-thunderbird in a folder something like n2fcrfl2.default.
Copy and paste this folder into .thunderbird.
In .thunderbird, open profiles.ini (double click on it and it will open in the editor).
Change the default user Path= to the old default folder (something like n2fcrfl2.default).
(The old profiles.ini will be saved as profiles.ini~).

My old Thunderbird start icon in the Panel now opens Thunderbird v3 without my having to change it, but if you need to create a new start icon or add to Applications list, the Thunderbird program is located in /opt/thunderbird/thunderbird.

---

### Post by uRock on 2010-09-16
Just installed the 3.1.4 release. Works great. This is with 32bit though, not 64bit.

---

