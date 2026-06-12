---
title: "I wrote an upgrade script for the hell of it..."
date: 2006-10-12
forum: The Cafe
---

### Post by aysiu on 2006-10-12
**Disclaimer**: I am not a programmer. I know very little about shell scripts except that they're collections of terminal commands. Most of this code is stuff I stole/adapted from a script written by forum member [Nanotube.](http://ubuntuforums.org/member.php?u=66474)

If you see anything you want to improve, please post the improvement.

Since most people who would know enough to do ```
chmod +x scriptname.sh
./scriptname.sh
``` would know enough to upgrade themselves, I'm not sure how useful this script might be, but I just put it together to see if it was possible to do easily.

Let me know what you think: ```
#/bin/bash

## Script written on 11 October, 2006 by aysiu
## Most of the syntax is adapted or just plain copied from code originally written by Nanotube for a Firefox installation script

## Make sure that we exit if any commands do not complete successfully.
set -o errexit
trap 'echo "Previous command did not complete successfully. Exiting."' ERR

## Introduction to script
echo "This script will upgrade you to the next version of Ubuntu.

If you're using Warty, it will upgrade you to Hoary.
If you're using Hoary, it will upgrade you to Breezy.
If you're using Breezy, it will upgrade you to Dapper.
If you're using Dapper, it will upgrade you to Edgy.

You should not upgrade more than one version at a time. If you want to upgrade from Breezy to Edgy, you're better off--in terms of time and stability--just installing Edgy from scratch.

This script also assumes you have a broadband internet connection. If you have no internet connection or are on dial-up, please do not use this script."

## Confirmation of desire to proceed
echo -e -n "

Do you still wish to proceed [y/n]? "
while true
do
  read ans
  case $ans in
       Y|y) break ;;
  [Yy][Ee][Ss]) break ;;
       N|n) exit ;;
  [Nn][Oo]) exit ;;
         *) echo -n "Invalid command. Please answer yes or no [y/n] " ;;
  esac
done

## Stop from running the script people who are already at the latest version.
if grep -q "development" /etc/issue ; then
  echo "You're already using the development version. You cannot upgrade to a newer version."
  exit 1
elif grep -q "6.10" /etc/issue ; then
  echo "At the time of this script's creation, Edgy was already the latest release of Ubuntu."
  exit 1
fi

## Prompt for metapackage installation
echo -e -n "

In order to have a more likely success in upgrading, we're going to have to install the appropriate metapackages for your desktop environments. This may involve the installation of additional software." 
echo -e -n "

Do you still wish to proceed? [y/n]? "
while true
do
  read ans
  case $ans in
       Y|y) break ;;
  [Yy][Ee][Ss]) break ;;
       N|n) exit ;;
  [Nn][Oo]) exit ;;
         *) echo -n "Invalid command. Please answer yes or no [y/n] " ;;
  esac
done

## Install metapackages
if [ -f /usr/share/xsessions/gnome.desktop ]; then
  echo -e "

Since you have Gnome installed, we're going to make sure ubuntu-desktop is also installed"
  sudo aptitude update && sudo aptitude install ubuntu-desktop
fi
if [ -f /usr/share/xsessions/kde.desktop ]; then
  echo -e "

Since you have KDE installed, we're going to make sure kubuntu-desktop is also installed"
  sudo aptitude update && sudo aptitude install kubuntu-desktop
fi
if [ -f /usr/share/xsessions/xfce.desktop ]; then
  echo -e "

Since you have XFCE installed, we're going to make sure xubuntu-desktop is also installed"
  sudo aptitude update && sudo aptitude install xubuntu-desktop
fi

## Back up sources.list
echo '

Backing up old sources.list file'
sudo cp /etc/apt/sources.list /etc/apt/sources.list.old

## Revise sources.list
echo '

Replacing with new sources.list for upgrade'
if grep -q "4.10" /etc/issue ; then
  sed 's/warty/hoary/g' /etc/apt/sources.list > ~/temp.list && sudo mv ~/temp.list /etc/apt/sources.list
elif grep -q "5.04" /etc/issue ; then
  sed 's/hoary/breezy/g' /etc/apt/sources.list > ~/temp.list && sudo mv ~/temp.list /etc/apt/sources.list
elif grep -q "5.10" /etc/issue ; then
  sed 's/breezy/dapper/g' /etc/apt/sources.list > ~/temp.list && sudo mv ~/temp.list /etc/apt/sources.list
elif grep -q "6.06" /etc/issue ; then
  sed 's/dapper/edgy/g' /etc/apt/sources.list > ~/temp.list && sudo mv ~/temp.list /etc/apt/sources.list
else
  echo "

Error: unable to determine what version of Ubuntu you currently have installed."
  exit 1
fi

## Do the upgrade
echo "

We're going to start doing the actual upgrade. This could take hours, even on a broadband internet connection. Please be patient."
sudo aptitude update && sudo aptitude dist-upgrade
``` Even if you have nothing to contribute, please let me know if you think this sort of script is worth doing... or if people already know how to upgrade properly...

---

### Post by maniacmusician on 2006-10-12
I think it is definitely worth doing, especially if you get it to evolve into a little tiny program, that could eventually be used by anyone. this goes even beyond holding new user's hands. this is like putting them in a crib surrounded by food and love. 

on the other hand, it wouldn't kill people to know how to just type "sudo aptitude update && sudo aptitude dist-upgrade", it's really not that hard. So i guess i have mixed feelings about it

edit: actually, i guess they would have to replace their sources.list file too. So it's probably good to automate that for them...

---

### Post by mips on 2006-10-12
> **aysiu said:**
> Even if you have nothing to contribute, please let me know if you think this sort of script is worth doing... or if people already know how to upgrade properly...

Maybe just warn people with bandwidth caps that it might be a better option to download the latest ISO than upgrading all the way from warty to edgy as it will eat considerable bandwidth and take time.

---

### Post by keithweddell on 2006-10-12
Given the various problems reported from past upgrades of all sorts, you'll want to put some major caveats on this if you're going to recommend it (or something like it) to newbies.

I find myself in something of a dilemma over this type of script. I started using Ubuntu (and linux) about 6 months ago and mostly tried to avoid using scripts. Instead, I read the wiki and forum information and learned much more.  However, I realise that not everyone wants to do it this way.

It is good to lend a hand to new users but hiding everything in scripts and GUIs removes the opportunity to learn. I've found that the most valuable part of writing this sort of script was what I learned during the writing.


Keith

---

### Post by aysiu on 2006-10-12
> **maniacmusician said:**
> 
on the other hand, it wouldn't kill people to know how to just type "sudo aptitude update && sudo aptitude dist-upgrade", it's really not that hard. So i guess i have mixed feelings about it

edit: actually, i guess they would have to replace their sources.list file too. So it's probably good to automate that for them... It's a three-parter to do a proper upgrade:

1. Make sure you have the proper metapackage installed (xubuntu-desktop, for example)

2. Change your sources.list

3. Do the upgrade

So, it is simple... but it's also not.

> **mips said:**
> Maybe just warn people with bandwidth caps that it might be a better option to download the latest ISO than upgrading all the way from warty to edgy as it will eat considerable bandwidth and take time. I did actually warn people... not about the bandwidth, but I did tell them not to try skip versions in upgrades (Breezy to Edgy, for example).

> **keithweddell said:**
> Given the various problems reported from past upgrades of all sorts, you'll want to put some major caveats on this if you're going to recommend it (or something like it) to newbies. Good point.

> I find myself in something of a dilemma over this type of script. I started using Ubuntu (and linux) about 6 months ago and mostly tried to avoid using scripts. Instead, I read the wiki and forum information and learned much more.  However, I realise that not everyone wants to do it this way.

It is good to lend a hand to new users but hiding everything in scripts and GUIs removes the opportunity to learn. I've found that the most valuable part of writing this sort of script was what I learned during the writing. Well, to me, it's all about choice.

If people want to learn stuff, I'm all for that. But if they want a simpler way... they should get that if it's available.

By the way, is anyone willing to test this script? It doesn't have to be now... whenever you move to Edgy from Dapper.

I did a sort of test on my test machine, and it seemed to work (I canceled out before the actual *dist-upgrade*).

---

### Post by John.Michael.Kane on 2006-10-12
aysiu I will test it,and post back findings errors should there be any.

---

### Post by iovar on 2006-10-12
Well, I wouldn't recommend this kind of script to anyone. I upgraded
by changing my sources and it certainly required some manual attention.
I think that people that do not know to do this operation on their
own,are very likely to not know how to deal with potential problems.

And I think it should be better completely replacing sources.list with a
new one since it is likely that many people would have added custom
repositories, many of which might not yet have an edgy pool.

---

### Post by aysiu on 2006-10-12
That's what I figured.

An upgrade is a major change.

Anyone who needs a script will likely run into problems, blame the script, and then not know how to fix it.

Still, it may be useful to a handful of people (a very, very small handful).

---

### Post by jdong on 2006-10-12
Ayisu, I don't really mean to be critical or anything, but have you seen dist-upgrader? (aka the update-manager -c -d thing)

It's already a very reliable upgrader for Ubuntu, implemented as a GNOME GUI. A console frontend is in the discussion, for server usage, etc.

I think this kind of upgrader work needs to be consolidated into one, and so far the best solution I've used is dist-upgrader / update-manger.

---

### Post by aysiu on 2006-10-12
> **jdong said:**
> Ayisu, I don't really mean to be critical or anything, but have you seen dist-upgrader? (aka the update-manager -c -d thing)

It's already a very reliable upgrader for Ubuntu, implemented as a GNOME GUI. A console frontend is in the discussion, for server usage, etc.

I think this kind of upgrader work needs to be consolidated into one, and so far the best solution I've used is dist-upgrader / update-manger.
At the time when Dapper came out, I saw numerous complaints about the updater application to go from Breezy to Dapper.

If that's been refined for the Dapper to Edgy transition, then that would make my script totally useless, of course, except for those wanting to upgrade from Warty to Hoary, Hoary to Breezy, or Breezy to Dapper.

---

### Post by jdong on 2006-10-12
ah, ok. The dist-upgrader tool is like apt-get dist-upgrade plus numerous workarounds and fallbacks. I don't think the script would work any better on cases where dist-upgrader would fail (which primarily are when users have installed lots of 3rd party stuff)

---

### Post by aysiu on 2006-10-12
You're probably right. Well, it was a fun exercise, anyway.

---

### Post by John.Michael.Kane on 2006-10-12
aysiu The script does work for me,however. For other endusers ymmv.

---

### Post by aysiu on 2006-10-12
You actually used it?

Thanks for testing it, SD-Plissken.

Well, it's there. If people want to use it, use it. Otherwise, there are other ways...

---

### Post by John.Michael.Kane on 2006-10-12
Yes i tested. not only does it make sure the user has all the dapper dependencies required for upgrading  it downloads those,and then proceeds to upgrade dapper to edgy.

I must say aysiu for not being a scripter you did good on this one.

Note: dist-upgrading is not for the faint of heart.Any method one uses short of clean installing can be risky.

---

### Post by aysiu on 2006-10-12
Thanks for the compliment. All the complicated code I just stole from Nanotube's Firefox installation script anyway.

---

### Post by John.Michael.Kane on 2006-10-12
jdong touched on the use 3rd party deb source lines/files. The one 3rd party line i had was ignored by the script. now i'm not sure if this effect would carry over for more users as it may depend on the source line or installed files.

Hope this helps some.

---

### Post by aysiu on 2006-10-12
Well, it basically does a find/replace on one word (Dapper) for another word (Edgy). So if you have repositories without those words in them, they will be unaffected.

But if you have a repository that's valid for Dapper and has the word Dapper in it but isn't valid for Edgy, that repository won't work any more. I don't think it should affect the upgrade, but it'll probably give you a 404 not found.

---

### Post by dddouglas on 2006-10-12
aysiu 
> **aysiu said:**
> At the time when Dapper came out, I saw numerous complaints about the updater application to go from Breezy to Dapper.


That was how I upgraded to Dapper but iovar makes a good point. I am guilty of running something or point click without regard as to what is being done (I have cut and pasted many times from your web site only half know what I was doing)and really searching to find a fix.:rolleyes:  However for my purpose that is just fine. I do not need a highly custom machine. Knowing what I know now I would be afraid to run such a script. Maybe with some more scripting under my belt but not for a newbie.

---

### Post by John.Michael.Kane on 2006-10-12
Well then your script is golden should enduser's need or want to use it.

Thanks for allowing me to test it.


dddouglas it's possable for script makers to include a doc on what each step the script is doing,however.most post that you will find here has the enduser asking how do i make xyz work not how does this script or xyz work.

---

### Post by dddouglas on 2006-10-12
> **SD-Plissken said:**
> W
most post that you will find here has the enduser asking how do i make xyz work not how does this script or xyz work.

But as a novice running a script that you might pick up here or there knowing what is happening just seems prudent. In other words I might make xyz work but one needs to take into account unexpected consiqunce and knowledge how xyz worked will help in that eval when things go wrong. At any rate I only want to learn and I appreciate all of you who continue to share the wealth.:KS

---

### Post by aysiu on 2006-10-26
Bumping this thread for the hell of it... just in case someone wants to upgrade tonight and is feeling adventurous.

It has a 100% success rate so far... with one test subject...

---

### Post by jdong on 2006-10-26
Ayisu... from my testing the official upgrader still works better.... It does basically what your script does, plus some workarounds, including some forced downgrades for known broken 3rd party  repositories (compiz/beryl, for one), and it has failsafes that execute dpkg --configure -a and apt-get -f install for failed upgrades, so worst case another run of the upgrader will clear it up.


I still have to recommend using the official upgrader. Plus, another bonus, it's a GUI with a progress bar so you have a much better sense of how long it's gonna take and how much is left.

---

### Post by H.E. Pennypacker on 2006-10-26
I was thinking of testing the script, but if the GUI does everything it does and more, I may as well go wtih update-manager -c -d.

---

