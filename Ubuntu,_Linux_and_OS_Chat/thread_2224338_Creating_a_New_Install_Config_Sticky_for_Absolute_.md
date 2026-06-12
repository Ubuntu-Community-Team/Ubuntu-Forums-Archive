---
title: "Creating a New Install Config Sticky for Absolute Beginners?"
date: 2014-05-15
forum: Ubuntu, Linux and OS Chat
---

### Post by Kurt_Alan on 2014-05-15
**[SIZE=5][COLOR="#000000"][/COLOR][/SIZE]**

One of my backup strategies is to maintain a .doc in the Cloud which describes my personal choices for a new Ubuntu install.  Plan A is a clonezilla image re-install.  However, this is a useful Plan B for every other (new) install.  Config time is much greater than install time.  Why not a "pilot's checklist"?

Think of this list as a template.  One may add or subtract according to choice.  But the sub-categories could be agreed upon (E.g. Initial; Launcher Apps; Tweaks; Troubleshoot)

I am initiating this thread in Ubuntu Chat and using it as an informal "water-cooler" location for assembling a project (this one) if and until it goes prime time in Absolute Beginners' Section as a Sticky.

My list follows.  What can you add or subtract? 

Unity OS Config



INITIAL

First Install:

a. Cat5 + power; install
b. Wi-fi: Go to settings, Software and Updates, find tab for drivers, search.
c. Install Synaptic Package Manager: STORE or CLI:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install synaptic

d. Install Software Updater to Launcher: run and reboot.
e. From Synaptic install Dropbox/Nautilus

After install: CLI: (for flags)

dropbox -h   


APPS TO LAUNCHER: (Personal Choice Varies)

Go to Store "Installed":
a. Remove unused apps that are not system critical
b. Add the following:   **=not from store


Drag to Launcher location according to use (e.g. Terminal at the top)
**terminal (from Dash)
**Files (default; use for Home)
Synaptic Package Manager
**YPPA (ppa manager)
Chromium
**Chrome
Firefox (default)
Notes—from the store
**Skype
Writer (default)
Calc (default)
**Dictionary (ppa)
gPodder
VLC
**Software Center
**Ubuntu Tweak (from Synaptic install gdebi; app in Dropbox).
System Profiler and Benchmark
**Software Updater (Dash)
**Help (Dash)
**workspace
trash

Note: If broken CLI/Synaptic due to broken packages, run:

sudo dpkg --configure -a
sudo apt-get install -f


To wit:

a. Install Chrome:

wget -q -O - [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) | sudo apt-key add -

sudo sh -c 'echo "deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main" >> /etc/apt/sources.list.d/google-chrome.list'

sudo apt-get update-alternatives
sudo apt-get install google-chrome-beta

b. Chrome browser apps: shortcuts to Desktop

c. Configure three browsers: Chromium, Chrome, Firefox

d. Install Skype:

wget -O skype.deb [http://download.skype.com/linux/skype-ubuntu-precise_4.2.0.13-1_i386.deb](http://download.skype.com/linux/skype-ubuntu-precise_4.2.0.13-1_i386.deb)

sudo dpkg -i skype.deb

sudo apt-get -f install;rm skype.deb

e. Add a system load indicator:

sudo apt-get install indicator-multiload

f. Add: dconf-editor: 

sudo dconf-editor

g. Dictionary:

sudo apt-get install gnome-dictionary dict-moby-thesaurus dictd dict-gcide

sudo apt-get install dict-wn dict dict-foldoc dict-jargon 


PPA's

I. Y PPA Manager 0.9.9.2:  

sudo add-apt-repository ppa:webupd8team/y-ppa-manager

sudo apt-get update

sudo apt-get install y-ppa-manager  

II. Install this (Tuxboot), which is based on unetbootin to create a bootable clonezilla flash drive:

If you are using Ubuntu Linux, you can use Ubuntu PPA to install tuxboot:

sudo apt-add-repository ppa:thomas.tsai/ubuntu-tuxboot
sudo apt-get update
sudo apt-get install tuxboot

III. Install ClassicMenu Indicator from store, if available.  If not:

sudo add-apt-repository ppa:diesch/testing
sudo apt-get update
sudo apt-get install classicmenu-indicator

IV. PPA CLI commands:

Add PPA:

sudo add-apt-repository ppa:someppa/ppa

sudo apt-get update

Remove PPA:

sudo add-apt-repository --remove ppa:someppa/ppa

TWEAKS

1. Remove keyboard indicator:

The keyboard langauge is indicated on your panel. Why? If this annoys you you can remove it.

System Settings-> Text Entry and uncheck the Show current input source in the menu bar.

2. Change cursor: 

sudo update-alternatives --config x-cursor-theme

3. Add workspaces:

Type “appearances” at the dash (or get there from system settings), click behavior, show workspaces.

To change horizontal and vertical numbers:

To change the number of rows, type the following command, changing the final number to the number you wish. Press Enter. 
gsettings set org.compiz.core:/org/compiz/profiles/unity/plugins/core/ vsize 2 

To change the number of columns, type the following command, changing the final number to the number you wish. Press Enter. 
gsettings set org.compiz.core:/org/compiz/profiles/unity/plugins/core/ hsize 3 

4. Auto Start Up an Application   

Click the Dash Home icon (or tap Super), type 'Startup Applications' to search for the application and run it.
Click the "Add" button.
Name a program.
Click the "Browse" button and navigate to "Computer" > usr > bin, where programs are usually installed.
Select a program, click the "Open" button followed by the "Add" button.

The above program will then be listed in additional startup programs. Check if the program runs automatically by logging out.

TROUBLESHOOT

1. Reset compiz/unity to default:

sudo dconf -f /org/compiz/

2. Re-install indicator appmenu:

sudo apt-get install –reinstall indicator-appmenu

Other: 

1. wiki.compiz.org

Add ccsm:

2. Google search: Things to do after install Ubuntu X.
3. CLI:

Install multimedia codecs--
sudo apt-get install ubuntu-restricted-extras
NOTE: When you come to Agreement, scroll down, TAB to highlight OK, then Enter.

---

### Post by cariboo on 2014-05-18
If you are going to create one of these list, for absolutely new users, I'd suggest you stay away from the command line and ppa's. Making a newby jump right into using the terminal, is a sure fire way of losing them.

---

### Post by monkeybrain20122 on 2014-05-18
> **cariboo907 said:**
> If you are going to create one of these list, for absolutely new users, I'd suggest you stay away from the command line and ppa's. Making a newby jump right into using the terminal, is a sure fire way of losing them.

Not sure what the problem is. When newbies show up in the forum they are given more or less the same kind of instructions. While Ubuntu wants to be user friendly even for the lowest common denominator users there is no way it can babysit users like Mac. Ubuntu can be easy to use for basic users but only if it is set up and supported by someone who is a bit advanced. If you set up Ubuntu yourself than there is no way to stay away from commands and config files if just for trouble shootings and changing defaults etc. Let's face it, Ubuntu is not so polished that it is trouble free once installed. 

Just because a user is 'basic' in technical know how and Linux doesn't mean his/her needs are also basic,--like just facebook and email.My roommate is a basic user, I set up lubuntu for him the first thing he wanted to do was to close the lid and expected it to wake up (why not? he does it all the time with Windows without second thought). This already might require some non trivial work to set up, suspension and hibernation can be very problematic with Ubuntu. 

So no, Ubuntu is not newbie friendly to the extent that everything just works and doesn't require tinkering, let's not pretend that it is (and on that note: It is annoyinhg that most config tools are not even installed, this assumes the defaults work reliably and are sensible, which often is not the case)

---

### Post by cariboo on 2014-05-18
I have nothing against using the terminal, I use it fairly often myself, but I feel that a new user needs to have some time to get used to the difference between running a Linux distribution and Windows. On my old system, created with well supported hardware, during day-to-day usage there is never a need to do anything on the command line, everything can be done  with gui tools.

---

### Post by LastDino on 2014-05-18
Actually, I find it very pleasing to find terminal way of doing basic things to be introduced in these ''things to do after install'' guides. I shifted not to long ago and believe me, I can't remember more than a dozen  basic commands, and the ones I do were discovered through these guides. They are proving to be quite helpful in neat-keeping my own system. Lets face it, most will simply copy paste without even reading the whole thing, but doing this at least keeps newbies in slightly more ''know how to'' category rather than not having any clue about it at all. Latter is likely to happen by keeping the terminal aspect hidden rather than using this easy way to introduce it.

---

### Post by Kurt_Alan on 2014-05-18
**[SIZE=5][COLOR="#000000"][/COLOR][/SIZE]**


Hmmm.  Interesting.  There appears to be a lot of slipperiness in the term "beginner." It's relative.  Even though the Ubuntu Forum's Beginner's section is modified by 
"absolute" beginner, I see a lot of posts there that reveal advanced knowledge.  I know that because I am not an absolute beginner and I don't have the ability to solve most of the problems there.

Do you think that even ```
 df -h 
``` would be too advanced for a beginner? I'm sure a lot of people, including me, copy/paste code because we have not yet learned syntax.

However, your point is well-taken.  Do you think it would be more appropriate to create such a sticky for the General Help section?  Then, if this works out, we could do a truly simple one for absolute beginners--no terminal; only GUI.  

What do you think?

---

### Post by Kurt_Alan on 2014-05-19
**[SIZE=5][COLOR="#000000"][/COLOR][/SIZE]**

I am marking this thread as SOLVED.  I received the input I was looking for.  The consensus seems to be that my Unity Config rough draft is too complicated for the AB section because it makes more use of the terminal and PPA's as opposed to config via GUI.  This is not to say that the Terminal should not be introduced to the AB section.  For example, it would probably be a good idea to search for Terminal in Dash and drag it to Launcher.
Being aware of its existence is a first enabling step.

Meanwhile, as a project, I am re-writing a Unity Config draft for a General Help sticky.  I will present that in the General Help section later.  If that works, maybe I can do one for the AB section. . .

---

