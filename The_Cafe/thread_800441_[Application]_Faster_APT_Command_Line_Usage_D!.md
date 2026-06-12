---
title: "[Application] Faster APT Command Line Usage :D!"
date: 2008-05-19
forum: The Cafe
---

### Post by Glaxed on 2008-05-19
Have you ever been using APT in the terminal and you get sick and tired of typing out 'sudo apt-get install ' or 'apt-cache search' or 'sudo apt-get remove'?
How about 'sudo apt-get autoclean' and then upgrade, update, and re-installation? I have found this very annoying especially when I update distros.

For a frequent APT user, this is *just wasted time.*

So I wrote a program to make this very quick, and I attached the source code to the thread.
The comments/documentation explains my program well.

[B]Sample Usage:
$ up up

versus
$ sudo apt-get update && sudo apt-get upgrade && sudo apt-get autoclean[/B] 

Code suggestions (I'm new to C++) or feature requests can be emailed to me at [EMAIL="vminch@gmail.com"]vminch@gmail.com[/EMAIL] or you could just post it here.

I hope someone finds this useful - [COLOR=Red]_I know this saves me a ton of time._[/COLOR]

[http://i238.photobucket.com/albums/ff6/vminch/inaction.png](http://i238.photobucket.com/albums/ff6/vminch/inaction.png)
--- Great screen shot demonstrating the usage.

```

/* up.cpp Version 2 - Copyright Vedant Kumar 2008 GPLv3
 * 
 *      This program is free software; you can redistribute it and/or modify
 *      it under the terms of the GNU General Public License as published by
 *      the Free Software Foundation; either version 2 of the License, or
 *      (at your option) any later version.
 *      
 *      This program is distributed in the hope that it will be useful,
 *      but WITHOUT ANY WARRANTY; without even the implied warranty of
 *      MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 *      GNU General Public License for more details.
 *      
 *      You should have received a copy of the GNU General Public License
 *      along with this program; if not, write to the Free Software
 *      Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston,
 *      MA 02110-1301, USA.
 * 
 *         >>> Description:
 * This program is designed to increase the speed at which
 * users of APT, or the Advanced Package Tool, can work with software 
 * packages in a terminal.
 * 
 *         >>> Usage:
 * Update & Autoclean (-args/-regex):        $ up up
 * Install (+args/+regex):                     $ up in packages                    
 * Uninstall (+args/+regex):                $ up rm packages
 * Autoclean (-args/-regex):                $ up cl
 * Search (1 arg/+regex):                    $ up se package
 * 
 * up can take multiple arguments and simple regex for certain options;
 * $ up [option] package1 package2 packageN
 * $ up [option] package*
 * 
 *         >>> Building:
 * 1. The Normal Way
 * $ g++ -fconserve-space up.cpp -o up
 * 
 * 2. The Recommended Way
 * >>> Pre-req: Place this file on your desktop and install g++/build-essential.
 * $ cd ~/Desktop && g++ -fconserve-space up.cpp -o up && sudo mv up /usr/bin/
 * 
 * To explain, this command will find the up.cpp file on your Desktop
 * and compile it. Then, it will move it into the /usr/bin directory.
 * It will need your password for this.
*/

```

---

### Post by Glaxed on 2008-05-19
I've added a screenshot, but I'm debating whether or not I should use IMG code and stick it in this thread...
Right now, I just have a link to it (on photobucket), but many people may ignore this effort on grounds that they cant see what it does.
On the other hand, putting a large image onto a thread is a b**** move to people with less bandwith...

---

### Post by malfist on 2008-05-19
very interesting, I may try it.

edit: could you do one for aptitude, I would rather use it instead of apt it does a better dependency management.

---

### Post by kerry_s on 2008-05-20
thats what alias's are for.

---

### Post by Glaxed on 2008-05-20
huh, I guess using alias would make more sense, never heard of it before though..

---

### Post by vishzilla on 2008-05-20
I prefer alias anytime, does the job

---

### Post by original_jamingrit on 2008-05-20
It would be interesting as a full blown front-end to APT, with extra features and whatnot.

---

### Post by madjr on 2008-05-20
> **original_jamingrit said:**
> It would be interesting as a full blown front-end to APT, with extra features and whatnot.

+1 for a simple and fast front-end with some nice features.

for aptitude it would be perfect

usually synaptic and add/remove are super slow

i think you can do this with **zenity**

---

### Post by kerry_s on 2008-05-20
some buddy could revive this->
[http://linux.softpedia.com/get/System/Software-Distribution/Buddy-6063.shtml](http://linux.softpedia.com/get/System/Software-Distribution/Buddy-6063.shtml)

[IMG]http://linux.softpedia.com/screenshots/Buddy_1.jpg[/IMG]

i used it back in the day it was nice.

---

### Post by Ebuntor on 2008-05-20
Please forgive my ignorance but why would a  front-end to APT be needed? I mean, isn't that what we have Synaptic for?

---

### Post by kerry_s on 2008-05-20
> **Ebuntor said:**
> Please forgive my ignorance but why would a  front-end to APT be needed? I mean, isn't that what we have Synaptic for?

for speed, yes, there is synaptic, but synaptic is well slow.
example:
find synaptic in your menu> click> type password> wait it's loading> highlight the right side so it will find as you type> mark for install> click apply> yada yada..

open terminal> type> sudo apt-get install name
or
open terminal> type> install name (if you have alias's)
or
if there was a program like buddy:
sudo buddy
press 1 > type> name

speed damit! we want speed! :lolflag:

---

### Post by Ebuntor on 2008-05-20
> **kerry_s said:**
> for speed, yes, there is synaptic, but synaptic is well slow.
example:
find synaptic in your menu> click> type password> wait it's loading> highlight the right side so it will find as you type> mark for install> click apply> yada yada..

open terminal> type> sudo apt-get install name
or
open terminal> type> install name (if you have alias's)
or
if there was a program like buddy:
sudo buddy
press 1 > type> name

speed damit! we want speed! :lolflag:

Lol, ok ok, I get it, more of speed, way more. :p

---

### Post by qazwsx on 2008-05-20
kpackage seems to be little faster to use than synaptic IMO. Keyboard shortcuts...

CLI is unbeatable in package management speed category.

How about little shell script frontend for apt then...

---

### Post by Glaxed on 2008-05-21
tentative feature list:
> list installed packages
> search installed packages & all packages
> get package description
> lock & unlock packages
> add repos and manage gpgs with short commands
> compress cached .deb files
> install .deb files (dpkg frontend)
> get source dependencies

> 'debug' sources.list file (great when experimenting with new repos that cause errors)
[by debug, i mean provide information about what causes the error, not just flash the error message apt does].

((> seed .deb files with upload/download choking - been suggested and shot down before, and requires a tracker and the ability to contact large swarms of people to switch downloads i.e unfeasable)

more suggestions?
This doesnt look too hard to code, seeing as all of it will be done using std::system. Or not, depending on if there is a better approach.

---

### Post by toupeiro on 2008-05-21
> **kerry_s said:**
> thats what alias's are for.

+1

Also, you do know you can tab-to-complete with apt-get right?  you can also tab-tab to get a list of every possible hit in your repository list with what you have typed so far.   I don't see how anything menu-driven can be faster than that which is available between synaptic and apt-get

---

### Post by popuptarget on 2008-05-21
But just out of devils advocate how does one go about CLIing it when one does not know the name of the application needed?  For me I got a Verizon wireless card.  As the instructions were so very useful for Linux users (lots of sarcasm here) I found Synaptic very useful (gnomeppp).  Understanding that CLI=speed and everyone wants speed of course but now that I am in synaptic to find an app, why would I click to close that out to click to open a terminal to type in commands to get an app?

---

### Post by Glaxed on 2008-05-21
So how do you pass arguments to aliases guys?

e.g, if you have

alias sda='sudo mount -o rw /dev/sda3 /home/$USER/$FOLDER'

and you need an argument for the folder location?
can you just $ sda /Desktop
or something like that?

---

### Post by kerry_s on 2008-05-21
> **popuptarget said:**
> But just out of devils advocate how does one go about CLIing it when one does not know the name of the application needed?  For me I got a Verizon wireless card.  As the instructions were so very useful for Linux users (lots of sarcasm here) I found Synaptic very useful (gnomeppp).  Understanding that CLI=speed and everyone wants speed of course but now that I am in synaptic to find an app, why would I click to close that out to click to open a terminal to type in commands to get an app?

these are my alias's

```
alias su='sudo -i'
alias update='sudo apt-get update;sudo apt-get -u dist-upgrade'
alias install='sudo apt-get install'
alias remove='sudo apt-get remove --purge'
alias search='apt-cache search'
alias show='apt-cache show'
alias clean='sudo apt-get clean'
alias fix='sudo apt-get -f install'
```

so for me i use " search editor " and it will list editors. if i want a closer look at it " show nvi " anything you can do in synaptic can be done at command.

---

### Post by popuptarget on 2008-05-21
Well shoot fire.  Now I am going to play with this being a noob and all and see how well I do.  That and see how comfortable (friendliness and intuative) I am using this as opposed to synaptic.  Thanks.  

V/R Jason

---

### Post by kerry_s on 2008-05-21
> **Glaxed said:**
> So how do you pass arguments to aliases guys?

e.g, if you have

alias sda='sudo mount -o rw /dev/sda3 /home/$USER/$FOLDER'

and you need an argument for the folder location?
can you just $ sda /Desktop
or something like that?

this:
alias sda='sudo mount -o rw /dev/sda3 /home/$USER/$FOLDER'
would be more like:
alias sda='sudo mount -t auto /dev/sda3 /$HOME/Desktop'

personally, i would use pmount instead, and put an entry in fstab:

/dev/sda1        /media/usb   auto user,noauto     0       0

i created a usb folder in /media, so i just:

pmount usb
pumount usb

---

### Post by Trail on 2008-05-22
Mine is
```

alias agu='sudo aptitude update'
alias agg='sudo aptitude safe-upgrade'
alias agi='sudo aptitude install'
alias ags='aptitude search'
alias agr='sudo aptitude remove'

```
(in ~/.bashrc of course)

I rarely use other options (like purge) so I type those manually. ags | grep is awesome by the way.

---

