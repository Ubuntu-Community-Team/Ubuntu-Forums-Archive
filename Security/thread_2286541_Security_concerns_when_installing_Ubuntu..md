---
title: "Security concerns when installing Ubuntu."
date: 2015-07-13
forum: Security
---

### Post by leftoverspagetti on 2015-07-13
hello internet,

i was hoping to get in contact with a moderator, or at least a geek who knows a little more about the technicals of ubuntu, specifically boot time opperations. I suspect maliciousness has been installed on my computer and when I run an install what my computer is reading from isnt the DVD but somewhere else in the network. My suspicions arose when I began finding encrypted folders deep in my hard drive, or folders that have been locked and root/admin passwords are unable to open. Is there anyone out there who would care to take a look at my system and spread some light? Unless, of course, you happen to be the person responsible for said folders and behavior, you can go to hell, but anyone else out there would be greatly appreciated. I can supply you with a link to my paste bin and nothing further, no IM, nothing other than over this forum. thanks in advance

Spagetti

---

### Post by Bucky Ball on 2015-07-13
*Thread moved to **Security**.*

Welcome. You don't need a moderator. We do not deal one-on-one with support requests and neither do 99% of the users here. It is discouraged. Just post a thread about your suspicions and we'll all help if we can.

You talk about encrypted and locked folders you've found but give no indication of what they are called or where they are. If you are worried about things coming from elsewhere on the network when installing, simple solution, don't go online when installing. Unplug the ethernet cable and don't configure wireless during install. Done.

Linux is not Windows. Good luck.

(PS: Assuming that a forum user here would want to/care about hacking into your computer and telling them to go to hell and 'calling all geeks' is not going to win many favours. Linux is very secure and it is very doubtful anything untoward is happening, but hard to know as you give so little detail. If something odd is happening on your network that would very doubtfully have anything to do with Ubuntu. It is more likely the folders you are finding are owned by root of the Ubuntu system (which you can access very easily once installed) and there is nothing suspicious going on at all.)

---

### Post by leftoverspagetti on 2015-07-13
ahh, I am sorry if I offended you, when i said go to hell it was a suggestion, and a sugestion toward only one person, and i use the term "geek" endearingly I assure you.

Suspicious files generally have long random names formatted xxxxxxxxxx-xxxxxxxxxxx things like that.
cron jobs to install zeitguiest onto ubuntu 14.04 which i did not make and i doubt that ubuntu did because it breaks 14.04 so that makes no sense. 
offline install works fine until i plug in and these automatic things start.

I agree that it has nothing to do with ubuntu, the security was one of the main reasons i chose ubuntu as my operating systems, the other reason was the friendly helpful support from its community that i read so much about. I am simply asking someone who is more knowledgeable to take a look at my paste bin and see if there is anything fishy going on, or should i say (Phishy)... ahhh I do enjoy a good pun. 

again if you can help please say so and i will link to pastebin 

thanks again

Spagetti

---

### Post by Bucky Ball on 2015-07-13
All good. I have also changed the title of your thread to reflect your concerns more accurately and improve your chances of help.

When you install offline, reboot, get to a desktop, how are these downloads happening? Are they happening randomly or are you told to update the machine? The latter is normal. You will need to input your password for the updates to begin. If you are not inputting a password and these updates are happening, then that might be of concern, but we'll dig deeper. 

This is a regular 14.04 LTS desktop install I take it? Is this your home network we are talking about, where you are the administrator, or another?

---

### Post by leftoverspagetti on 2015-07-13
thank you for the title swap. Brevity is a concept alien to me.

-it is a basic regular 14.04 from your website
-when it comes time to plug into the network i am prompted for my password 3 times. 1st when i log in. 2nd to store my password in some folder incase i ever forget it, 3rd when its update time. I always read the list of updates and take note of it. at times i have noticed rsync being carried out at the same time as 
```

sudo apt-get update
sudo apt-get upgrade

```

is this normal? i didnt set up rsync and deffently not in --daemon mode.

i have had updates installed with out inputting a password. comming back home and an update is in progress things like that.

it is the network of the house i live at and i am not the administrator. the owner of the house lets me use it as part of what i pay for each month. 

Spagetti

---

### Post by Bucky Ball on 2015-07-13
Ok. First up, open Software & Updates> Updates and makes sure you haven't got that set to update automatically. It should look like the screenshot attached.

PS: We are all volunteers here and not employed by or associated with Canonical on a professional basis, just like your good self. It is extremely rare you will find anyone here who is. The download site belongs to Canonical, not us. We are an independent forum which is officially acknowledged by Canonical. :)

---

### Post by buzzingrobot on 2015-07-13
The installer will pull files from the Ubuntu repositories, especially if you have selected the additional codecs and update-while-installing options. Nothing unusual about seeing network activity during the install.

During the install, temporary files and archives are copied  to the target drive.  These are deleted after a successful install.  Perhaps something went wrong with your installation and the files-with-strange-names you see are those files that were not deleted.

How did you determine a "cronjob" is attempting to install zeitgeist?  "crontab -l" in a terminal will list all existing cronjobs for that user.  It's empty unless you've created something yourself.

An explanation of how you did the install might be useful.  "offline install works fine until i plug in and these automatic things start." suggests you did not follow the standard approach. (Very soon after the first reboot after a successful install, assuming the net is available, Ubuntu will contact the repositories to determine if updates are available.  For 14.04, a considerable number of updates will likely be available. The Software Updater icon typically appears in the Launcher and attempts to get the user's attention.)

---

