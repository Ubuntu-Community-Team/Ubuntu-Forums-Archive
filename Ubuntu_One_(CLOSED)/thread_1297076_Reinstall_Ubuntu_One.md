---
title: "Reinstall Ubuntu One"
date: 2009-10-21
forum: Ubuntu One (CLOSED)
---

### Post by Marran77 on 2009-10-21
Hello

I have some trouble with U1. It does not sync! I think it has to do with the fact that I installed Karmic beta over a jaunty installation but kept the U1 account. But reinstalling U1 does not solve the issue. So, how do I reinstall U1 from scratch, including removing all configurationfiles?

edit: Maybe I should add that the ubuntu one-folder, after connecting comes with a U1.conflict

---

### Post by joshuahoover on 2009-10-22
> **Marran77 said:**
> Hello

I have some trouble with U1. It does not sync! I think it has to do with the fact that I installed Karmic beta over a jaunty installation but kept the U1 account. But reinstalling U1 does not solve the issue. So, how do I reinstall U1 from scratch, including removing all configurationfiles?

edit: Maybe I should add that the ubuntu one-folder, after connecting comes with a U1.conflict

Hi,

I'll try to answer this question here, but if you continue to have problems, the best way to get a problem tracked and fixed is to submit a bug by right-clicking on the client and selecting "Report a Problem".

[LIST=1]
[*]Quit the Ubuntu One client
[*]$ sudo rm -rf ~/.share/local/ubuntuone
[*]$ rm -rf ~/.cache/ubuntuone
[*]$ rm -rf ~/.config/ubuntuone
[*]$ mv ~/Ubuntu\ One/ ~/Ubuntu\ One_old/
[*]Open Applications->Accessories->Passwords and Encryption Keys, go to the Passwords tab, delete the Ubuntu One token
[*]$ sudo apt-get purge ubuntuone*
[*]$ sudo apt-get install ubuntuone*
[*]Open Applications->Internet->Ubuntu One and you should have to add your computer via the web page that comes up once you login to Ubuntu One
[*]Put a small text file in the newly created ~/Ubuntu One/ directory and make sure that syncs correctly, if not, please report a bug
[*]If all goes well this far, move the files and folders from ~/Ubuntu One_old/ to ~/Ubuntu One/ and the sync should happen
[/LIST]
Those steps are for those wanting to completely start over from scratch with Ubuntu One. You shouldn't normally have to do this, but it's possible there were some things that got messed up along the way. Again, if you have problems, please right-click on the Ubuntu One client and select "Report a Problem".

Thank you,

Joshua

---

### Post by james_mcl on 2009-10-23
Will this procedure be sufficient to start from scratch in the release candidate and final release too?

---

### Post by Soul-Sing on 2009-10-25
> **james_mcl said:**
> Will this procedure be sufficient to start from scratch in the release candidate and final release too?

Don't know, but it works perfect on Jaunty.

---

### Post by joshuahoover on 2009-10-26
> **james_mcl said:**
> Will this procedure be sufficient to start from scratch in the release candidate and final release too?

Yes, this will work in the RC and final release of Karmic. I added an FAQ with these steps for future reference: [https://answers.edge.launchpad.net/ubuntuone-client/+faq/778](https://answers.edge.launchpad.net/ubuntuone-client/+faq/778)

---

### Post by mnoyes on 2009-10-29
Tried this but did not work -- when I opened the application at the end of the process you describe I just got the same thing: the icon appears in the panel with a red box with an x in it. No prompt to add my computer. I tried cancelling my sub at ubuntuone and creating a new one, but still no luck. 

It seems it would help if users could manage their connections -- remove and add a computer...

---

### Post by jTips on 2009-11-02
Thanks Josh! This worked a treat for my issue :)

---

### Post by =NickJ= on 2009-11-06
I'm giving this a bump as it's doing exactly the same for me too, clicking on "Connect" just does nothing and I haven't had an Add My Computer prompt...

---

### Post by avdzm on 2009-11-07
Ubuntu one doesn't work for me,
it fails to authenticate and sync.

---

### Post by joshuahoover on 2009-11-09
> **avdzm said:**
> Ubuntu one doesn't work for me,
it fails to authenticate and sync.

For those having problems even after reinstalling...First, my apologies for the inconvenience. Can you please do the following?

1) Are you using NetworkManager? If not, Ubuntu One won't currently work for you.
2) Check the following log files for errors, if there are any, please file a bug by right-clicking on the Ubuntu One client and selecting "Report a Problem"

Thank you,

Joshua

---

### Post by avdzm on 2009-11-12
> **joshuahoover said:**
> For those having problems even after reinstalling...First, my apologies for the inconvenience. Can you please do the following?

1) Are you using NetworkManager? If not, Ubuntu One won't currently work for you.
2) Check the following log files for errors, if there are any, please file a bug by right-clicking on the Ubuntu One client and selecting "Report a Problem"

Thank you,

Joshua

Hey Joshua,

I am using NetworkManager.
And I have report the problem to launchpad.

thanks

---

### Post by rpras on 2009-11-15
Hi Joshua:

> **joshuahoover said:**
> Hi,

I'll try to answer this question here, but if you continue to have problems, the best way to get a problem tracked and fixed is to submit a bug by right-clicking on the client and selecting "Report a Problem".

[LIST=1]
[*]Quit the Ubuntu One client
[*]$ sudo rm -rf ~/.share/local/ubuntuone
[*]$ rm -rf ~/.cache/ubuntuone
[*]$ rm -rf ~/.config/ubuntuone
[*]$ mv ~/Ubuntu\ One/ ~/Ubuntu\ One_old/
[*]Open Applications->Accessories->Passwords and Encryption Keys, go to the Passwords tab, delete the Ubuntu One token
[*]$ sudo apt-get purge ubuntuone*
[*]$ sudo apt-get install ubuntuone*
[*]Open Applications->Internet->Ubuntu One and you should have to add your computer via the web page that comes up once you login to Ubuntu One
[*]Put a small text file in the newly created ~/Ubuntu One/ directory and make sure that syncs correctly, if not, please report a bug
[*]If all goes well this far, move the files and folders from ~/Ubuntu One_old/ to ~/Ubuntu One/ and the sync should happen
[/LIST]
Those steps are for those wanting to completely start over from scratch with Ubuntu One. You shouldn't normally have to do this, but it's possible there were some things that got messed up along the way. Again, if you have problems, please right-click on the Ubuntu One client and select "Report a Problem".

Thank you,

Joshua

Just did the above.  Restarting UbuntuOne gives me an icon in the upper panel -- but it has a red "x" on it.  Same as it was before reinstalling UbuntuOne.

> **joshuahoover said:**
> For those having problems even after reinstalling...First, my apologies for the inconvenience. Can you please do the following?

1) Are you using NetworkManager? If not, Ubuntu One won't currently work for you.
2) Check the following log files for errors, if there are any, please file a bug by right-clicking on the Ubuntu One client and selecting "Report a Problem"

Thank you,

Joshua

Not using NM.  Have had a lot of problems with it on my iBook G3 running Karmic PPC.  Currently I have plain vanilla ifconfig/iwconfig/dhclient setup to connect to my wireless APs.  No NM, no wicd.

I'll try reporting a problem.

---

### Post by avdzm on 2009-11-16
ITS WORKING!!!!!!!!!!!
Hey guys, Ubuntu ONE is finally working!!!

And the solution is simple. 
The problem isn't on the client side (at least mine wasn't).

Did you guys subscribe to ubuntu one before the release of karmic?
Well I did. 

What I did, was I canceled my subscription and resubscribed.
and now U1 is working (the problem seems to be on the server). As suggested by Lucas [https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/480602](https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/480602).

Good luck guys.

---

### Post by lordskid on 2010-01-18
I still get the red icon with the x but if I hover my mouse over it it says updating files... am planning to wait and see if the files will be sync'ed. Well I have to manually connect it, now it is sync'ing to the cloud server thanks joshua. this was very helpful.

---

### Post by hallu on 2010-01-27
> **joshuahoover said:**
> 
1) Are you using NetworkManager? If not, Ubuntu One won't currently work for you.


Thx, now I know why I couldn't connect. I have an old adsl modem. I'm not using NetworkManager to configure it.

---

### Post by joshuahoover on 2010-02-01
> **hallu said:**
> Thx, now I know why I couldn't connect. I have an old adsl modem. I'm not using NetworkManager to configure it.

We have a fix for this. If you're using Jaunty, then please update your software and restart the Ubuntu One client. If you're using Karmic, then please follow this FAQ to install the proposed update: [https://answers.edge.launchpad.net/ubuntuone-client/+faq/930](https://answers.edge.launchpad.net/ubuntuone-client/+faq/930)

Thanks!

Joshua

---

### Post by hallu on 2010-02-23
i'm using the ppa:ubuntuone/beta, it works now, i think i had to purge network-manager to make it work

---

### Post by DedMoroz on 2010-02-26
THANK YOU! This solved my problem!


> **joshuahoover said:**
> Hi,

I'll try to answer this question here, but if you continue to have problems, the best way to get a problem tracked and fixed is to submit a bug by right-clicking on the client and selecting "Report a Problem".

[LIST=1]
[*]Quit the Ubuntu One client
[*]$ sudo rm -rf ~/.share/local/ubuntuone
[*]$ rm -rf ~/.cache/ubuntuone
[*]$ rm -rf ~/.config/ubuntuone
[*]$ mv ~/Ubuntu\ One/ ~/Ubuntu\ One_old/
[*]Open Applications->Accessories->Passwords and Encryption Keys, go to the Passwords tab, delete the Ubuntu One token
[*]$ sudo apt-get purge ubuntuone*
[*]$ sudo apt-get install ubuntuone*
[*]Open Applications->Internet->Ubuntu One and you should have to add your computer via the web page that comes up once you login to Ubuntu One
[*]Put a small text file in the newly created ~/Ubuntu One/ directory and make sure that syncs correctly, if not, please report a bug
[*]If all goes well this far, move the files and folders from ~/Ubuntu One_old/ to ~/Ubuntu One/ and the sync should happen
[/LIST]
Those steps are for those wanting to completely start over from scratch with Ubuntu One. You shouldn't normally have to do this, but it's possible there were some things that got messed up along the way. Again, if you have problems, please right-click on the Ubuntu One client and select "Report a Problem".

Thank you,

Joshua

---

### Post by Nickedynick on 2010-03-02
Excellent, fixed my issues too - thanks!

I have however noticed that my username in preferences seems to be showing as "None Nickedynick" rather than just "Nickedynick". Looks like a simple formatting error at the moment, but it's annoying :P

---

### Post by joshuahoover on 2010-03-03
> **Nickedynick said:**
> Excellent, fixed my issues too - thanks!

I have however noticed that my username in preferences seems to be showing as "None Nickedynick" rather than just "Nickedynick". Looks like a simple formatting error at the moment, but it's annoying :P

I'm looking for that formatting error, but I'm unable to find it. Could you post a screenshot and/or point me to the URL where you're seeing this?

Thanks!

Joshua

---

### Post by noisufnoc on 2010-04-15
I actually spoke too soon.  I followed your direction, and cannot use the directory.  When I go to Applications>Internet>Ubuntu One the icon appears but with the "!" in the middle.  If I click on the icon, it crashes.

---

### Post by joshuahoover on 2010-04-15
> **noisufnoc said:**
> I actually spoke too soon.  I followed your direction, and cannot use the directory.  When I go to Applications>Internet>Ubuntu One the icon appears but with the "!" in the middle.  If I click on the icon, it crashes.

It sounds like you're on Karmic. If so, can you file a bug report by right-clicking on the Ubuntu One client applet and select "Report a Problem"? Please describe the steps you took that got you to this error. My guess is it's a known issue (with a possible workaround) but without seeing the log files I can't say for sure.

Thank you,

Joshua

---

### Post by gh1234 on 2010-06-03
> **joshuahoover said:**
> I'm looking for that formatting error, but I'm unable to find it. Could you post a screenshot and/or point me to the URL where you're seeing this?

Thanks!

Joshua

I think I have actually the same problem... I will attach a screen shot!
BTW: there is no way to authenticate for me, too!
I just tried to unsubscribe but it seems to take longer until every data is deleted.
When I re subscribe all data are unchanged :confused:

---

### Post by bprins on 2010-10-23
Awesome, it works for me too :=)

Thanks Joshua!

---

### Post by rabideau on 2011-01-11
UbuntuOne on 10.10 is failing for me.  I have tried all the suggestions in this stream including complete reinstalls of all UbuntuOne packages in Synaptic.  I am running 10.10 64bit and U1 was working fine until I added a second machine to my account, a new email address and 20GB of space.  Now nothing works. But I did manage to send some money to Canonical!

My U1 sync updates are hung at 472MB (never to progress although it appears that Tomboy syncs still work). U1 options have disappeared from all Nautilus context menus, and whenever I attempt a U1 Restart or Connect  thru the U1 control panel things sit and spin until they finally stop (probably due to boredom).

I have reported this error 3 or 4 times thru support on U1 and never received a response.  

I am now looking for a reliable backup & sync option.  Any suggestions?

---

### Post by bprins on 2011-01-11
dropbox seems pretty mainstream
[http://www.dropbox.com/](http://www.dropbox.com/)

---

### Post by cabbrick1243 on 2011-02-26
Thanks!
Seems to have worked on 10.10
I had changed my hostname, so it was not syncing at all.

---

### Post by suganux on 2011-03-07
it works for me, thanks guys.

---

### Post by mordak13 on 2011-04-14
> **joshuahoover said:**
> Hi,

I'll try to answer this question here, but if you continue to have problems, the best way to get a problem tracked and fixed is to submit a bug by right-clicking on the client and selecting "Report a Problem".

[LIST=1]
[*]Quit the Ubuntu One client
[*]$ sudo rm -rf ~/.share/local/ubuntuone
[*]$ rm -rf ~/.cache/ubuntuone
[*]$ rm -rf ~/.config/ubuntuone
[*]$ mv ~/Ubuntu\ One/ ~/Ubuntu\ One_old/
[*]Open Applications->Accessories->Passwords and Encryption Keys, go to the Passwords tab, delete the Ubuntu One token
[*]$ sudo apt-get purge ubuntuone*
[*]$ sudo apt-get install ubuntuone*
[*]Open Applications->Internet->Ubuntu One and you should have to add your computer via the web page that comes up once you login to Ubuntu One
[*]Put a small text file in the newly created ~/Ubuntu One/ directory and make sure that syncs correctly, if not, please report a bug
[*]If all goes well this far, move the files and folders from ~/Ubuntu One_old/ to ~/Ubuntu One/ and the sync should happen
[/LIST]
Those steps are for those wanting to completely start over from scratch with Ubuntu One. You shouldn't normally have to do this, but it's possible there were some things that got messed up along the way. Again, if you have problems, please right-click on the Ubuntu One client and select "Report a Problem".

Thank you,

Joshua

Thanks this process worked for me to get UbuntuOne working on my Natty Beta update from Maverick.

---

### Post by imblack on 2011-05-07
Can you assist for the same procedure in Windows?

I am running win7 64b and I have lost the syncing ability of my U1.

It doesnt sync at all, you right click from tray, click sync and after a sec it shows synced with nothing done. Works great on ubuntu though.

---

### Post by glendavee on 2011-05-13
I've followed mordak13's instructions to reinstall. I'm using Natty. Seemed to go ok, but now ubuntuone control panel won't open. Any ideas?

---

