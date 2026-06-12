---
title: "Problems with Dansguardian"
date: 2010-04-07
forum: Ubuntu Christian Edition
---

### Post by calebyong on 2010-04-07
I have been switching to ubuntu since october, i very new to ubuntu and unix systems, i have been using windows until last year, i liked ubuntu alot. But i have an addiction to pornography, which can be solved by installing a filter, by the grace of God, i've found UCE, and have been using it. But Dansguardian is not really working all the time, it seems to not load any websites sometimes. Is a there a bug or a workaround?

---

### Post by stlsaint on 2010-04-07
Can you give us a more indepth description as to what/when exactly your errors are occuring.

---

### Post by david_kt on 2010-04-07
> **calebyong said:**
> I have been switching to ubuntu since october, i very new to ubuntu and unix systems, i have been using windows until last year, i liked ubuntu alot. But i have an addiction to pornography, which can be solved by installing a filter, by the grace of God, i've found UCE, and have been using it. But Dansguardian is not really working all the time, it seems to not load any websites sometimes. Is a there a bug or a workaround?

Did you use UCE or just dansguardian? If you use CE, that bugs should not exist.

DK

---

### Post by LifeBringer on 2010-04-08
Porn used to be really distracting for me too (ages 14-15). Now-a-days I use UbuntuCE's filter for facebook and other distractions.
What problems do you find, when, and how? 
For example, if you uninstall the GUI (too avoid turning it off yourself). I find that the redirector stops working. :-(


On a side note, wish it had an extra password feature too. :-P

---

### Post by david_kt on 2010-04-08
> **LifeBringer said:**
> 
For example, if you uninstall the GUI (too avoid turning it off yourself). I find that the redirector stops working. :-(


On a side note, wish it had an extra password feature too. :-P

Ask your parents or somebody else to hold the administrator password, and you should log in as normal user. You will not have the ability to switch it off.

DK

---

### Post by calebyong on 2010-04-12
i use google chrome 5.0 beta, UCE 9.10 with all the updates. Sometimes, the browsing is just slow, i can use chat, but browsing on http is slow.

---

### Post by david_kt on 2010-04-12
> **calebyong said:**
> i use google chrome 5.0 beta, UCE 9.10 with all the updates. Sometimes, the browsing is just slow, i can use chat, but browsing on http is slow.

How about firefox? Is there any problem if you use firefox?

DK

---

### Post by calebyong on 2010-04-12
same too. its slow if i turn it on too.

---

### Post by CPUNeck on 2010-05-06
Yep, I can not surf the web at all using Firefox 3.5.  I was running standard 8.04... upgraded to 9.0? then to 9.10 and finally did the in place upgrade using instructions from the web site.  All went well, and the install works.  If I disable Dansguardian, I can surf, otherwise there is no worries of getting to a site my kids shouldn't be... it goes no where.

---

### Post by morepractice on 2010-08-06
Try my tutorial on: [http://ubundance.blogspot.com/2010/07/how-to-install-and-setup-dans-guardian.html](http://ubundance.blogspot.com/2010/07/how-to-install-and-setup-dans-guardian.html)

---

### Post by blueorthlog224@hush.ai on 2010-08-20
Dansguardian is not working. The following is a quick description  
 
Ubuntu CE 9.04 Jaunty is supposed to work "out of the box".


First I setup several user accounts. Updated the distribution using... 



```
sudo apt-get install ubuntu-desktop 
```
```
sudo apt-get update && sudo apt-get safe-upgrade
```

 At onset the Dansguardian Gui filters keywords like " proxy ... " ect 
once restarting the box the redirect option it disable for all users and filtering is useless. 

Is this is bug? 

-blueortholog

---

### Post by david_kt on 2010-08-20
> **blueorthlog224@hush.ai said:**
> Dansguardian is not working. The following is a quick description  
 
Ubuntu CE 9.04 Jaunty is supposed to work "out of the box".


First I setup several user accounts. Updated the distribution using... 



```
sudo apt-get install ubuntu-desktop 
```
```
sudo apt-get update && sudo apt-get safe-upgrade
```

 At onset the Dansguardian Gui filters keywords like " proxy ... " ect 
once restarting the box the redirect option it disable for all users and filtering is useless. 

Is this is bug? 

-blueortholog

Open terminal, and post the output of:


```
cat /etc/lsb-release 
```

DK

---

### Post by Jordy_224 on 2010-09-07
Having a similar problem, After restart tinyproxy is disabled. When it is disabled the content filtering doesn't fuction.

More details are shown in my previous post. 

[HTML]http://ubuntuforums.org/showthread.php?t=1492885&page=5
[/HTML]

How do you set default parameters and force it to keep default parameters upon start. 

Thanks

---

### Post by david_kt on 2010-09-07
> **Jordy_224 said:**
> Having a similar problem, After restart tinyproxy is disabled. When it is disabled the content filtering doesn't fuction.

More details are shown in my previous post. 

[HTML]http://ubuntuforums.org/showthread.php?t=1492885&page=5
[/HTML]

How do you set default parameters and force it to keep default parameters upon start. 

Thanks

It is supposed to stay even after restart. May be you have other firewall running so that it interfere with ubuntu ce firewall.

DK

---

### Post by Jordy_224 on 2010-09-10
Yes, I have firehol running in addition to tinyproxy. 

 What is auto/configure? How does it fix conflicts.

 Auto/configure options should be a permanent change after restart.

How is this done?


-J

---

### Post by david_kt on 2010-09-10
> **Jordy_224 said:**
> Yes, I have firehol running in addition to tinyproxy. 

 What is auto/configure? How does it fix conflicts.

 Auto/configure options should be a permanent change after restart.

How is this done?


-J

Firehol overrides ubuntu ce firewal setting when restart, probably it is loaded after ubuntu ce firewall. What you could do is to remove firehol.

DK

---

### Post by Jordy_224 on 2010-09-12
Honesty, I am trying to avoid deleting my firewall. This is because, in general firehol works and is the best alternative to squid. (since I had difficultly with dansguarding using squid)

SO, I want to run autoconfigure at startup after firehol is loaded. But, there isn't much documentation autoconfigure. 

-J

---

### Post by david_kt on 2010-09-12
> **Jordy_224 said:**
> Honesty, I am trying to avoid deleting my firewall. This is because, in general firehol works and is the best alternative to squid. (since I had difficultly with dansguarding using squid)

SO, I want to run autoconfigure at startup after firehol is loaded. But, there isn't much documentation autoconfigure. 

-J

One way to do that is:

```
sudo update-rc.d -f ubuntu_ce_firewall remove
sudo update-rc.d ubuntu_ce_firewall defaults 99
```

But it is the same as removing firehol. Only one firewall could work at a time, either firehol or ubuntu_ce_firewall.

DK

---

### Post by Jordy_224 on 2010-09-13
Problem fixed. 

The problem was that the dansguardian proxy settings would drop after restart. This would cause an error in tinyproxy and resulted in the users ability to bypass content filtering. A temporary solution was to use the autoconfigure option but again after restart there was a conflict. 

As mentioned before in my previous post. Option firefox lock proxy doesn't work using the gui for my system.  

The solution was to manually lock firefox proxy. 

To do so I used the following post, by gohsthb here: 

[HTML]http://ubuntuforums.org/showthread.php?t=812832[/HTML]

but for xubuntu edit the apturl.js 

```
sudo gedit /etc/firefox-3.0/pref/apturl.js

```

Next, 
After restart the firefox proxy setting were still reserved.  Tinyproxy remained connected, even after restart dansguardian blocked access. 

In conclusion dansguardian works, (for my system at least) if you follow the guide describe here: 

[HTML]
http://ohioloco.ubuntuforums.org/showthread.php?t=1492885&page=5[/HTML]



"...good work dansguardian, I believe in what the program does. Thanks"

---

### Post by Jordy_224 on 2011-02-10
I'm running the following cron job, to restart the firewall and change the transparent proxy ** off ** status to transparent proxy** on  **

To do so I restart the firewall after boot. 

```

#
# m h  dom mon dow   command
SHELL=/bin/bash
PATH=/sbin:/bin:/usr/sbin:/usr/bin
MAILTO=root
HOME=/

@reboot root    /etc/init.d/ubuntu_ce_firewall restart >/tmp/myubufire2.log
```

yet, its not changing the transparent proxy status.

**Update::: **

So my goal is to restart the firewall after boot and re-gain transparent status on firewall.

**Problem solved!**

I was able to restart the firewall by linking to a script within a cronjob and using the sleep function to delay restarting the firewall. For example:

Code:

```
Sleep 15 
/etc/init.d/ubuntu_ce_firewall restart >/tmp/mylog.log
```


I didn't think that the **sleep **function could be so handy...

---

### Post by xman1616 on 2011-02-13
I can't seem to uninstall dansguardian-gui. The error message is below. Now I can't install anything with synaptic because it can't uninstall this package. Any help would be great. Thanks.

Joe

joe-linuxmint10 joe # sudo apt-get remove dansguardian-gui
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  dansguardian-gui
0 upgraded, 0 newly installed, 1 to remove and 15 not upgraded.
1 not fully installed or removed.
After this operation, 102kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 139661 files and directories currently installed.)
Removing dansguardian-gui ...
update-rc.d: /etc/init.d/ubuntu_ce_firewall exists during rc.d purge (use -f to force)
dpkg: error processing dansguardian-gui (--remove):
 subprocess installed post-removal script returned error exit status 1
Processing triggers for ureadahead ...
Errors were encountered while processing:
 dansguardian-gui
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by david_kt on 2011-02-13
> **xman1616 said:**
> I can't seem to uninstall dansguardian-gui. The error message is below. Now I can't install anything with synaptic because it can't uninstall this package. Any help would be great. Thanks.

Joe

joe-linuxmint10 joe # sudo apt-get remove dansguardian-gui
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  dansguardian-gui
0 upgraded, 0 newly installed, 1 to remove and 15 not upgraded.
1 not fully installed or removed.
After this operation, 102kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 139661 files and directories currently installed.)
Removing dansguardian-gui ...
update-rc.d: /etc/init.d/ubuntu_ce_firewall exists during rc.d purge (use -f to force)
dpkg: error processing dansguardian-gui (--remove):
 subprocess installed post-removal script returned error exit status 1
Processing triggers for ureadahead ...
Errors were encountered while processing:
 dansguardian-gui
E: Sub-process /usr/bin/dpkg returned an error code (1)

Try below:
```
sudo rm /etc/init.d/ubuntu_ce_firewall
sudo apt-get remove dansguardian-gui
```

DK

---

### Post by Jordy_224 on 2011-03-07
How to use Dansguardian to block all online web proxies that use 
glype?

--- 

I'm settled with a series of keywords to block all online proxies within the phraselist.txt file

---

