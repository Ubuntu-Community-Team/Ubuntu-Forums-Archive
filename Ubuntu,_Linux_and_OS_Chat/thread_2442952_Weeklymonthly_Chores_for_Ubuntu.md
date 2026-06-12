---
title: "Weekly/monthly Chores for Ubuntu?"
date: 2020-05-09
forum: Ubuntu, Linux and OS Chat
---

### Post by ferfykins on 2020-05-09
Just wondering what are some regular chores you gotta do with Ubuntu? (specifically XUBuntu).... For example with windows, i gotta delete temp files regularly, defrag computer, run CCLenaer, etc.   Thanks guys!

---

### Post by CelticWarrior on 2020-05-09
Nothing of that sort.
Install updates when notified to do so, that's all.

---

### Post by Autodave on 2020-05-09
Took me about a year to quit thinking about all that stuff you mentioned,  Was kinda weird, but it is really nice not having to worry about that stuff anymore.

---

### Post by jdeca57 on 2020-05-09
You might be interested in the state of your drive and then there is this [https://www.fosslicious.com/2019/08/check-ssd-health-in-xubuntu.html]("https://www.fosslicious.com/2019/08/check-ssd-health-in-xubuntu.html") It's about ssd and xubuntu but actually the info is general.

---

### Post by Irihapeti on 2020-05-09
Maybe not quite what you have in mind, but... Backup, regularly.

---

### Post by Perfect Storm on 2020-05-09
You could cache clean your browser once in awhile and empty the trash can.

---

### Post by oldfred on 2020-05-09
I do some regular housecleaning.
I installed 20.04 mostly as daily driver to a new drive several months ago. Still considered my 18.04 as main install.
But updates were so frequent that I run a script that updates, housecleans, deletes older logs, vacuums sqlite files (mostly Firefox & Thunderbird) and house cleans some cache & thumbnail files.

Updates, backups, delete old kernels - TheFu in Forums
[http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)
[https://help.ubuntu.com/community/RemoveOldKernels](https://help.ubuntu.com/community/RemoveOldKernels)

RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:
Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.
[http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc](http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc)

---

### Post by MartyBuntu on 2020-05-09
Backups
Updates (as they show up in notifications)
Dump old kernels every 3-4 months


This ain't Windows

---

### Post by ActionParsnip on 2020-05-10
If you are using an SSD I don't suggest you defrag. It makes near zero difference and wears the storage down.

If you run:
```
 
sudo apt-get clean 
sudo apt-get --purge autoremove 

``` 

It will keep debs that you have installed from wasting space. You can also uninstall old kernels to free space. Deborphan is a bit more hardcore but can save space. 

Other than that the OS will manage itself. Temp files go to temp storage (unlike in Windows) so a reboot clears them off

---

### Post by ActionParsnip on 2020-05-10
Ohh yes backups!!

---

### Post by Quarkrad on 2020-05-11
There is a nice graphical cleaner called *ubuntu cleaner* you can install.  If you have not done so already install an 'app installer' called *synaptic* - open the terminal and type **sudo apt-get install synaptic -y** Once synaptic is installed open/launch it and search for ubuntu cleaner and follow the prompts* to install it.  Once installed you will find ubuntu-cleaner most useful.  * See the attached - once visible put your mouse over the text *ubuntu cleaner* and right click, choose the option *Mark for installation*.  Then click on the Apply icon (under File, Edit, Package, Settings, Help).  Synaptic will install ubuntu cleaner for you.

---

### Post by ajgreeny on 2020-05-11
Personally I would keep away from applications like ubuntu cleaner; it might save a few seconds but will also possibly clean away some things you want to keep.

Your mantra should really be
Backup
Update and upgrade
Don't install packages that you are not sure you need and trust

Other than that the OS looks after itself a lot better than Windows.

---

### Post by slickymaster on 2020-05-11
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by SeijiSensei on 2020-05-11
A more general answer to your question. 

Routine tasks are handled by the "cron" system.  Every day your computer runs a bunch of maintenance scripts that reside in /etc/cron.daily/.  For instance, the program logrotate in that directory manages the system logs so they don't expand infinitely and eat up your drive. 

These programs are all managed by the master /etc/[crontab]("https://linux.die.net/man/5/crontab") file which invokes the daily, weekly, and monthly scripts as appropriate.  

So if, in the future, you wrote yourself a backup script and wanted to run it every day, you could do that by putting it in the directory /etc/cron.daily.

---

