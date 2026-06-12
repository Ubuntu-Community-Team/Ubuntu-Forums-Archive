---
title: "Upgrade to 12.04 from 11.04"
date: 2012-04-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by gjoris on 2012-04-02
Hi all, 

At the company where I work, I managed a Linux distribution to the developers, supported by a local mirror of the Ubuntu repo's. We adopted the 11.04 at that point as software stack, because at the start of the roll out, 11.10 was not yet released. We stayed at the 11.04 version, because of multiple reasons: 
- 11.04 was more stable 
- we did not want to upgrade too much (6 months upgrades are not feasible to support, we are 50+ in the user pool, and growing faster and faster at this point)
- at the first tests of 11.10, we had some tooling issues

The target was to upgrade to the 12.04 LTS version, and then keep using the LTS version in the future. 

However, upon investigation an upgrade strategy, I noticed that there is no upgrade strategy from 11.04 to 12.04. The documentation specifies that we have to pass the 11.10 version, and then upgrade to the 12.04 version. 

Those steps are not feasible. I realize that most of you will react with "no, that is not possible", but I'm still looking to do the impossible :-) Is there any way, complex as it may be, to upgrade from Natty to Precise, without having to do a fresh installation?

---

### Post by kansasnoob on 2012-04-02
The short answer is yes, it should be possible using the live CD - NOT the alternate CD. Beginning with Maverick the live installer (aka: ubiquity) was reworked and now SHOULD include the ability to upgrade most existing Ubuntu systems to the latest version.

But I encountered some problems while testing the Beta 2, so please be patient. I'm working on a few other projects ATM so it may be a couple of weeks before I have time to actually study this more closely.

If, and ONLY IF, you have a test machine to play around with .............. something where you won't be concerned with data loss, etc ............... then you could try some testing yourself.

In most cases I find it's always best to boot to the live DE first, always better to look before you leap, then if you begin the installation you should be offered an upgrade option similar to this:

[ATTACH]215306[/ATTACH]

Of course that shows 11.10 > 12.04 because that's what I had installed ;)

As I said though, **I encountered some problems!** I need a couple of weeks to get caught up with some unrelated issues and then I'll do some retesting before the final release.

Please feel free to PM me if I appear to have forgotten this issue after about April 16th :D

---

### Post by kansasnoob on 2012-04-02
Also just thought to add:

#1: 11.04 is supported until October 2012, so there is no need to upgrade every 6 months. If the upgrade warnings are driving your users crazy that can be changed in Update Manager > Settings > Updates tab > Notify of new version = never.

#2: Unless the release schedule changes the first "point release" of 12.04 (12.04.1) is due July 19th 2012. That's one of the coolest things about LTS releases. So, even if the final 12.04 release on April 26th is flaky, there is a very good chance that we can have those "flaky" issues worked out by 12.04.1 ;)

---

### Post by gjoris on 2012-04-02
> In most cases I find it's always best to boot to the live DE first, always better to look before you leap, then if you begin the installation you should be offered an upgrade option similar to this:

Not quite. It shows the option, but it is not selectable, since a standard upgrade procedure is not available. With your setup, it works, since an upgrade strategy is in place for the 11.10 version (as well as for 10.04 LTS). As I said: we don't want to pass the 11.10 version, as is stated in the (standard) documentation. 

> #1. 11.04 is supported until October 2012, so there is no need to upgrade every 6 months. If the upgrade warnings are driving your users crazy that can be changed in Update Manager > Settings > Updates tab > Notify of new version = never.

#2: Unless the release schedule changes the first "point release" of 12.04 (12.04.1) is due July 19th 2012. That's one of the coolest things about LTS releases. So, even if the final 12.04 release on April 26th is flaky, there is a very good chance that we can have those "flaky" issues worked out by 12.04.1

The support matrix wasn't really a reason nor an issue to **not** upgrade. As I said, the reason we don't want to upgrade constantly is for stability as well as feasibility (if you have to support about 75 users, an upgrade isn't done quite as easily as doing it for yourself, or even a few users).

---

### Post by kansasnoob on 2012-04-02
> **gjoris said:**
> Not quite. It shows the option, but it is not selectable, since a standard upgrade procedure is not available. With your setup, it works, since an upgrade strategy is in place for the 11.10 version (as well as for 10.04 LTS). As I said: we don't want to pass the 11.10 version, as is stated in the (standard) documentation. 



The support matrix wasn't really a reason nor an issue to **not** upgrade. As I said, the reason we don't want to upgrade constantly is for stability as well as feasibility (if you have to support about 75 users, an upgrade isn't done quite as easily as doing it for yourself, or even a few users).

Sadly you're comparing apples and oranges :(

There are now three ways to upgrade:

#1: Using the update manager

#2: Using the alternate CD

#3: Using the live CD

The first two do indeed require upgrading using the "proper" path. Using the live CD is a whole different thing!

It's also imperfect which is why I asked for a couple of weeks to do some additional testing ](*,)

I did however just get done rebuilding some hardware and I decided to install 11.04 just so I can give this a simple try-out ............. we'll know shortly how right or wrong I am ;)

---

### Post by kansasnoob on 2012-04-02
Golly, gosh, gee whiz, look:

[ATTACH]215308[/ATTACH]

Now will you give me a couple of weeks to sort out the freaking bugs :mad:

I've pretty much had it with the overabundance of FUD!!!!!!!!!!!!!!

---

### Post by grahammechanical on 2012-04-02
@kansasnoob

You are doing good work! So, a 12.04 LTS beta 2 live CD will offer an upgrade to 11.04 and not just to 10.04 LTS.

You knew it. You proved it. Well done!

Regards.

---

### Post by kansasnoob on 2012-04-02
> **grahammechanical said:**
> @kansasnoob

You are doing good work! So, a 12.04 LTS beta 2 live CD will offer an upgrade to 11.04 and not just to 10.04 LTS.

You knew it. You proved it. Well done!

Regards.

I hope you mean "from" instead of "to" :lolflag:

If so yes! Is it perfect? NO! I'm trying to troubleshoot this.

As with any installation or upgrade only a fool fails to back up important data! The data you don't back up will inevitably be the data you lose!!!!!!!!!!!!!!

---

### Post by frogotronic on 2012-04-02
What about an upgrade from 10.10 to 12.04?  Will that work as well?

Thanks

---

### Post by kansasnoob on 2012-04-02
I just completed that and all went well, but I had no data on there yet so I can't be sure how it will handle keeping data safe. Based on previous experience it's pretty darn reliable, but only a fool fails to back up important data!

Now, about the DE! It's possible that someone may want to know if classic remains classic after that type of upgrade .......... NO! After the upgrade you will have to reconfigure the DE:

[http://ubuntuforums.org/showpost.php?p=11809483&postcount=375](http://ubuntuforums.org/showpost.php?p=11809483&postcount=375)

You may even need to blow away some of the hidden dot files/folders to restore a default DE before beginning.

Did anyone notice that I said I need a couple of weeks to work out some issues :confused:

---

### Post by kansasnoob on 2012-04-02
> **cement_head said:**
> What about an upgrade from 10.10 to 12.04?  Will that work as well?

Thanks

I think it should but there is no guarantee. Please RE my last post :)

Wouldn't you like to be the first to test it :confused:

---

### Post by keithpeter on 2012-04-02
> **gjoris said:**
> 
- at the first tests of 11.10, we had some tooling issues

What tools/applications were involved? I'm assuming you have tested that 12.04 will support those OK with the versions that your developers need. A list might help Kansasnoob with his testing when he checks how the data files are affected by migration.

I take it home partitions are on the client machines and not a server somewhere?

---

### Post by kansasnoob on 2012-04-02
> **keithpeter said:**
> What tools/applications were involved? I'm assuming you have tested that 12.04 will support those OK with the versions that your developers need. A list might help Kansasnoob with his testing when he checks how the data files are affected by migration.

I take it home partitions are on the client machines and not a server somewhere?

All good points! I symlink my data partitions so that's slightly (only slightly) similar to using a data server.

Regardless no upgrade is as good as a clean install! But if you have a plan of action an upgrade via live CD as explained here can be faster than a clean install unless something fails.

One thing I'd point out, there is no need for a separate /home using this procedure IF IT WORKS RIGHT! I used caps for a reason :p

I've never experienced data loss doing one of these upgrades via live CD but quite often software packages are considerably mangled due to default package selection between versions.

---

### Post by frogotronic on 2012-04-02
> **kansasnoob said:**
> I think it should but there is no guarantee. Please RE my last post :)

Wouldn't you like to be the first to test it :confused:

HA!  Maybe...because my 10.10 install is ultra perfectly dialed in, I'm not sure...I'll probably do it on a testing machine and possibly write a guide to get back to Gnome Classic in 12.04 after the upgrade from 10.10 (the reason I'm still on 10.10).

- CH   :guitar:

---

### Post by keithpeter on 2012-04-02
Hello All and gjoris

I have a modest dual core desktop (certainly not a developer class machine) that I can use for a test.

64 bit or 32 bit?

What kind of tools? Eclipse or Java involved (big changes there)

Python?

Cheers

---

### Post by djsroknrol on 2012-04-02
The update manager worked fine for me....Lucid to Precise Beta with very little pain. :popcorn:

---

### Post by kansasnoob on 2012-04-02
> **djsroknrol said:**
> The update manager worked fine for me....Lucid to Precise Beta with very little pain. :popcorn:

But you can only upgrade using the Update Manager from either 10.04 to 12.04 or from 11.10 to 12.04. No good for upgrading from either 11.04 or 10.10.

---

### Post by kansasnoob on 2012-04-02
> **cement_head said:**
> HA!  Maybe...because my 10.10 install is ultra perfectly dialed in, I'm not sure...I'll probably do it on a testing machine and possibly write a guide to get back to Gnome Classic in 12.04 after the upgrade from 10.10 (the reason I'm still on 10.10).

- CH   :guitar:

Did you see this:

[http://ubuntuforums.org/showpost.php?p=11809483&postcount=375](http://ubuntuforums.org/showpost.php?p=11809483&postcount=375)

It links to my Oneiric w/o effects classic thread, very little change so far.

---

### Post by frogotronic on 2012-04-02
Okay...putting 12.04 beta in my 10.10 machine gives me the option of UPGRADING.  So it looks as if it will work.

Will wait for a couple of months to see how it goes for people.

- CH

---

### Post by keithpeter on 2012-04-03
Hello All

I've tested using the 12.04 live CD to upgrade an 11.04 install to 12.04 (see thumbnail at end of post). The process took around two hours, half an hour for installation until rebooting into user account, the rest of the time updating and restoring applications (scriptable?)

Summary: it works but you have to install Evolution and Banshee and Ubuntu Restricted Extras again. Once those applications were reinstalled manually, they found their profiles ok. 

Strange thing: no apps visible in apps lens in dash. HUD is working. I can find files ok. Just can't start apps!

**Gory Details**

11.04 set up and updated, including nvidia drivers, ubuntu restricted extras. An email account set up in Evolution and music imported into Banshee and photos into Shotwell. Dropbox installed and copied my dropbox folder over.

Booted into the 12.04 beta 2 CD-ROM and selected the Upgrade 11.10 option. Used the same username and password for the user account, and the same machine name. Normal install process started but error message as below...

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=215371&stc=1&d=1333477893[/IMG]

Rebooted to find I had to reinstall the restricted drivers, Evolution, Banshee (no longer default apps) and to repair Shotwell (missing library). Once reinstalled, Evolution, Shotwell, Banshee recovered their profiles fine. Had to reset the default template in LibreOffice, and LO had forgotten its settings. Didn't install any plug-ins so can't say anything about those. .libreoffice profile is still in home drive. Dropbox needed to be reinstalled but picked up existing profile.

Evolution migrates the profile on first start. Also asks if it is to be default e-mail application.

Dash: nothing in applications lens. Can't get a list of applications at all. Any pointers? There is a Zeitgeist-data process running, and zeitgeist claims to be installed. HUD works and finds menu items.

See Dash screen grab below...

---

### Post by philinux on 2012-04-03
I'd try a unity --reset first. Come back if that works or not.

---

### Post by frogotronic on 2012-04-03
> **keithpeter said:**
> Hello All

I've tested using the 12.04 live CD to upgrade an 11.04 install to 12.04 (see thumbnail at end of post). The process took around two hours, half an hour for installation until rebooting into user account, the rest of the time updating and restoring applications (scriptable?)

Summary: it works but you have to install Evolution and Banshee and Ubuntu Restricted Extras again. Once those applications were reinstalled manually, they found their profiles ok. 

Strange thing: no apps visible in apps lens in dash. HUD is working. I can find files ok. Just can't start apps!

**Gory Details**

11.04 set up and updated, including nvidia drivers, ubuntu restricted extras. An email account set up in Evolution and music imported into Banshee and photos into Shotwell. Dropbox installed and copied my dropbox folder over.

Booted into the 12.04 beta 2 CD-ROM and selected the Upgrade 11.10 option. Used the same username and password for the user account, and the same machine name. Normal install process started but error message as below...

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=215371&stc=1&d=1333477893[/IMG]

Rebooted to find I had to reinstall the restricted drivers, Evolution, Banshee (no longer default apps) and to repair Shotwell (missing library). Once reinstalled, Evolution, Shotwell, Banshee recovered their profiles fine. Had to reset the default template in LibreOffice, and LO had forgotten its settings. Didn't install any plug-ins so can't say anything about those. .libreoffice profile is still in home drive. Dropbox needed to be reinstalled but picked up existing profile.

Evolution migrates the profile on first start. Also asks if it is to be default e-mail application.

Dash: nothing in applications lens. Can't get a list of applications at all. Any pointers? There is a Zeitgeist-data process running, and zeitgeist claims to be installed. HUD works and finds menu items.

See Dash screen grab below...

Does gnome-classic work?

```
$sudo apt-get install gnome-panel
```

reboot & login with gnome-classic

- CH

---

### Post by philinux on 2012-04-03
Gnome classic is now available as default from session.

 [http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29)

---

### Post by keithpeter on 2012-04-03
Hello All

@phillilinux

unity --reset first 

Gives some error messages which I will try to catch, but no change once restarts.

No applications in lens on Unity2d either

@cement_head

Had to install gnome-panel, but works 'with effects'.

Only Unity/Unity2d sessions available when I completed the upgrade.

I should say this old Asus Pundit has Geforce 6150 graphics and has issues. This is how I run Unity...

[http://ubuntuforums.org/showthread.php?t=1879763](http://ubuntuforums.org/showthread.php?t=1879763)

But then unity2d worked really well...

Should I dump the dotfiles?

---

### Post by philinux on 2012-04-03
Yes dump all the dot files. But I tried 11.10 upgrade  the other day and had to reinstall clean and format home. I must have missed a config file that was messing it up.

My bad upgrade would not include classic.

---

### Post by keithpeter on 2012-04-03
Hello All

@philinux

All working now, dumping the dotfiles resulted in the application lens being populated, so thanks.

I guess I could have got away with just deleting .config? 

Everyone: the message I think to people who want to run Ubuntu on a lot of machines is to use a separate home drive. This has actually taken *longer* than a clean install and re-install of missing apps.

---

### Post by philinux on 2012-04-03
> **keithpeter said:**
> Hello All

@philinux

All working now, dumping the dotfiles resulted in the application lens being populated, so thanks.

I guess I could have got away with just deleting .config? 

Everyone: the message I think to people who want to run Ubuntu on a lot of machines is to use a separate home drive. This has actually taken *longer* than a clean install and re-install of missing apps. 

I'm not sure even that would help with an upgrade. Unity has conflicting settings from old to new. Some advice needed regarding deleting config files might be better.

My 11.10 has its own partition and I'm thinking back up FF and EVO and other profiles format home and copy them back.

Not sure yet though. And yes upgrades take absolutely ages.

---

### Post by kansasnoob on 2012-04-03
Regarding apps ........... no doubt some of the apps will not be properly updated, some default apps have changed.

Regarding default settings no matter what upgrade path you follow it may be necessary to blow away some of the hidden dot folders in /home.

I usually just rename the old hidden dots with a suffix of _OLD like this:

[ATTACH]215382[/ATTACH]

No doubt that's far from complete, just a generalization :)

---

### Post by keithpeter on 2012-04-04
> **kansasnoob said:**
> Regarding apps ........... no doubt some of the apps will not be properly updated, some default apps have changed.


Yup, and people will have to install the new versions applications they used to use, so the 11.04 -> 12.04 upgrade needed me to install Banshee and Evolution manually after the upgrade. 

I'm thinking of people like the OP who have moderately large numbers of machines to upgrade. The OP mentioned 75 machines, so at three quarters of an hour per machine with just credentials going in, you could run 5 upgrades in a batch. The problem is the fiddling around after the firrst reboot. Again OP mentioed a local repository so download time could be saved. Working on a batch of 5 in three hours, OP is looking at 45 hours of work here...

I was wondering about a script file to install the missing applications and then rename the dotties?

---

### Post by kansasnoob on 2012-04-04
> **keithpeter said:**
> Yup, and people will have to install the new versions applications they used to use, so the 11.04 -> 12.04 upgrade needed me to install Banshee and Evolution manually after the upgrade. 

I'm thinking of people like the OP who have moderately large numbers of machines to upgrade. The OP mentioned 75 machines, so at three quarters of an hour per machine with just credentials going in, you could run 5 upgrades in a batch. The problem is the fiddling around after the firrst reboot. Again OP mentioed a local repository so download time could be saved. Working on a batch of 5 in three hours, OP is looking at 45 hours of work here...

I was wondering about a script file to install the missing applications and then rename the dotties?

I don't do actual scripts but I do try and figure out "combo" commands that speed things up. Like if I know I always need to rename those hidden dots I'd do something like, "mv .config .config_OLD && mv .gconf .gconf_OLD && etc, etc".

If you want to use the same custom settings on a number of machines you can even make a copy of the customized hidden dots and import over and over again.

It takes a little while figuring out the first one but afterwards you can normally reduce things to running just a few commands :)

---

### Post by rigel4 on 2012-04-04
Hello PhilLinux, I think that we have met before. On NVnews
am I right :KS

If so how are you and if not ... sorry

small lord is the clue

---

