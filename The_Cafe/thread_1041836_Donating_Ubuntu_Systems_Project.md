---
title: "Donating Ubuntu Systems Project"
date: 2009-01-17
forum: The Cafe
---

### Post by Thirtysixway on 2009-01-17
Hello all.

I have recently started working on my Eagle scout project.  For those of you who don't know, Eagle is the highest rank in Boy Scouts.  It's a pretty big accomplishment, only about 5% of those who enter scouting actually get it.  One of the requirements is planning out and executing a project to teach project management and things like that.

My idea right now is to first run a local drive to collect working computers, printers, speakers, monitors, mice, etc.  Then train a small team of scouts/volunteers to install Ubuntu onto the systems.  Then we'll donate the systems to local shelters and community places who need some computers.

I'm looking for some opinions from fellow Ubuntu users.

[LIST=1]
[*]Should I install Edubuntu so that kids can have access to some good educational software?
[*]Should computers be networked to a server, or remain independent desktops?
[*]Will users be able to install updates and such without being on the first created account?
[*]Is there a filtering system so that a parent/advisor can manage filters for kids accounts on each separate machine?
[/LIST]

Any opinions or ideas you have on the project are welcomed.  I figured this would be a great way to give back to the local community as well as get the word out about Ubuntu.  I plan on putting an Ubuntu sticker on each machine :P

---

### Post by Sef on 2009-01-17
> 

[LIST=1]
[*]Should I install Edubuntu so that kids can have access to some good educational software?
[*]Should computers be networked to a server, or remain independent desktops?
[*]Will users be able to install updates and such without being on the first created account?
[*]Is there a filtering system so that a parent/advisor can manage filters for kids accounts on each separate machine?
[/LIST]


1.) Edubuntu or Ubuntu?

 a) For individuals - Install Ubuntu and any software that you think would be useful.  You could make a clone of the first installation, so the others will be the same.  

b) For schools - Edubuntu could work if they were being networked.

2) Networked or not

a) Independent, if you are giving them to individuals.  

b) Networked - Possibly (see 1b)

3) Updating

Yes, if they have administrative rights.   Of course they could do anything then.  For a school, a teacher or other official should be the administrator.

4) Filtering System

a) Best way is to create a white list with UFW - a gui front-end for IPTables, the firewall in Ubuntu.

b) There is Dan's Guardian, but I know nothing about it.  Also there would be some others.

---

### Post by gnomeuser on 2009-01-17
You definitely need to put some thought into support and upgrade path. The LTS version of Ubuntu or CentOS would give you the best options for upgradability and you wouldn't have to support what would amount to hundreds of different hardware configurations for upgrades every 6 months with what comes of interesting breakage.

It's not enough to give a person a computer, he need to teach them how to use it and where to get help. Luckily Linux users are a helpful bunch, you can definitely convince a few people to provide help be it in person or via IM/skype. Having a personal guide I always find give a much better entry into Linux than random bumbling around. From personal experience when I have people like that they ask a few questions or call a few times for help then after a week or so they seem to have learned to fly and start helping people on their own.

Buttomline, the software is not what you should focus on, focus on the support network.

---

### Post by ssam on 2009-01-17
I wouldn't bother with edubuntu unless you want to set up a linux terminal server system ( [http://www.ltsp.org/](http://www.ltsp.org/) ). All the ubuntus use the same repositories, so you can install all the same software.

independent computers are much easier to deal with. unless you are familiar with administering a network i would avoid it (though if you are keen to learn then you should have a try).

there are a few web filters, try searching for DansGuardian or willow.

---

### Post by Thirtysixway on 2009-01-17
Alright.  I did an install on virtualbox of edubuntu and didn't realize it changes all the artwork and whatnot.  I'll most likely stick with either Ubuntu or Xubuntu depending on the specs of the hardware we get.

The support part may be a little tricky.  Perhaps I could try and get a few people from the michigan loco ubuntu group to help out with initial training of the users.  Also maybe a .pdf or actual printed document on how to do things there would help as well.  The main goal of the systems is to let people browse the internet, write up resumes/word processing, and maybe a couple games but nothing really fancy.

Keeping systems independent seems like a better idea.  Sef, are there any resources about doing clone installations?  I doubt all the donated hardware will be the same, do you mean like creating a custom .iso installation disk?

---

