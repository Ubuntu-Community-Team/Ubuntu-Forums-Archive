---
title: "Firefox optimization and troubleshooting thread"
date: 2009-06-21
forum: Tutorials
---

### Post by lovinglinux on 2009-06-21
The objective of this tutorial is to provide a simple, but comprehensive, list of optimizations for Firefox and help with troubleshooting common issues. 

The tutorial is currently hosted on my web site. For questions and support is preferable that you post on this thread.

**[COLOR="Grey"][Table of Contents](http://webgapps.org/groups/firefox/forum/topic/firefox-optiomization-and-troubleshooting/)**[/COLOR]

---

### Post by xzero1 on 2009-06-22
Great thread!:D When I first started testing firefox 3.5 using an alpha version of Jaunty (3 maybe 2) it seemed *much faster*. It seems something happened to Jaunty that slowed it down. I did not add or change firefox. Did anyone else get the same impression?

---

### Post by v1nsai on 2009-06-25
I've been having an issue with firefox reverting to backed up bookmarks on close, I wasn't able to find a profiles folder (I assume all this is in .mozilla right?), but I did find many files labled as such: places.sqlite-#.corrupt, and there were 83 of them numbered 1-83 in the folder .mozilla/firefox/kmhbvuwv.default .  I also saw a filed called profiles.ini sitting in .mozilla/firefox but other than that no profiles folder.

I deleted all the .corrupt places.sqlite files that I found, but all that happened was the icons next to all my bookmarks were lost, and still reverted back to the backup

---

### Post by lovinglinux on 2009-06-25
> **v1nsai said:**
> I've been having an issue with firefox reverting to backed up bookmarks on close, I wasn't able to find a profiles folder (I assume all this is in .mozilla right?), but I did find many files labled as such: places.sqlite-#.corrupt, and there were 83 of them numbered 1-83 in the folder .mozilla/firefox/kmhbvuwv.default .  I also saw a filed called profiles.ini sitting in .mozilla/firefox but other than that no profiles folder.

I deleted all the .corrupt places.sqlite files that I found, but all that happened was the icons next to all my bookmarks were lost, and still reverted back to the backup

The profile folder is .mozilla/firefox/kmhbvuwv.default 

Delete all *places.sqlite-#.corrupt* just in case, but the one that is important is the *places.sqlite* without *#.corrupt* in the name. Just delete it and start Firefox again. It should fix the problem.

The file *profiles.ini* has nothing to do with your problem. It is the file that lists all profiles you have, but I think you have just one. Anyway, don't delete it.

---

### Post by v1nsai on 2009-06-25
Ah, I see.  Anyway, I deleted places.sqlite about 3 times now, created a new bookmark, then closed and reopened and my bookmark has yet to make it through the restart.  I've noticed that my history disappears every time I delete it, but my bookmarks still revert.  Would deleting the cached .json file that I restored from do anything?

---

### Post by v1nsai on 2009-06-25
I think I solved it, I mv'ed my .mozilla folder to .mozillabak and then restored my bookmarks from the recent backup and then added a few new ones.  Everything has persisted, even through a full system startup.

Weird...but solved.  What does places.sqlite do?

---

### Post by lovinglinux on 2009-06-26
> **v1nsai said:**
> I think I solved it, I mv'ed my .mozilla folder to .mozillabak and then restored my bookmarks from the recent backup and then added a few new ones.  Everything has persisted, even through a full system startup.

Weird...but solved.  What does places.sqlite do?

Just for the record, you could have moved/renamed/deleted only the firefox folder inside .mozilla and the effect would be the same. All Mozilla applications, like Thunderbird or Sunbird, stores their profiles inside .mozilla, so deleting/moving the entire .mozilla folder is not recommended/needed, because it would reset all Mozilla program settings, not only Firefox.

The places.sqlite file is a database where bookmarks and browsing history are stored.

---

### Post by mattsimis on 2009-06-26
For the "Font too small.." problem (issue on big Plasmas and projectors typically), I recommend the "NoSquint" addon, with it set to apply a 20% increase on all pages (NoSquint's default mode is to remember specific pages).
[http://urandom.ca/nosquint/](http://urandom.ca/nosquint/)

This is better than changing the font size as it scales the whole page (images too), making it less likely to have overlapping or truncated text.



Now, if anyone could advise how to get Backspace working as a "Back" button like on* other platform* FF builds, I would be happy.

---

### Post by kevdog on 2009-07-01
I haven't tried really anything in this thread yet, however just wanted to thank your for the time that went into preparing the advice in the guide.  Very informative and a job well done!

---

### Post by kromagg on 2009-07-01
The "general system optimization" tips section in there is completely superfluous. It also happens to be full of misinformation, I'd just remove it or splice it out to another thread if I were you.

---

### Post by areteichi on 2009-07-01
I didn't know about this new service called 'Weave'! It will be very useful to synchronize my Firefox profile across ubuntu and windows. Thank you so much!!

---

### Post by lovinglinux on 2009-07-01
> **kevdog said:**
> I haven't tried really anything in this thread yet, however just wanted to thank your for the time that went into preparing the advice in the guide.  Very informative and a job well done!

Thank you.

> **kromagg said:**
> The "general system optimization" tips section in there is completely superfluous. It also happens to be full of misinformation, I'd just remove it or splice it out to another thread if I were you.

I agree that it should be spliced. It was originally, so I just included the link. Anyway, would you mind explaining why you think there is misinformation?

> **areteichi said:**
> I didn't know about this new service called 'Weave'! It will be very useful to synchronize my Firefox profile across ubuntu and windows. Thank you so much!!

You are welcome.

---

### Post by adam_kimber on 2009-07-01
> **kromagg said:**
> The "general system optimization" tips section in there is completely superfluous. It also happens to be full of misinformation, I'd just remove it or splice it out to another thread if I were you.

There are some people stating that Flash performance has benefited from some of the tweaks in the other thread. Maybe those could be ported over to this thread under flash or the link just left with a note that it might not work for all etc... ????

Cheers for the info about Weave. Did not know about that.

---

### Post by johnraff on 2009-07-01
> **lovinglinux said:**
> All Mozilla applications, like Thunderbird or Sunbird, stores their profiles inside .mozillaI don't know about Sunbird, but my Thunderbird files are in a different folder called .mozilla-thunderbird. My .mozilla folder only contains Firefox material. They've always had separate folders on my systems - Ubuntu and Windows both.
**edit: **Please ignore the bit about Windows - of course the folder structures are quite different.

---

### Post by lovinglinux on 2009-07-01
> **johnraff said:**
> I don't know about Sunbird, but my Thunderbird files are in a different folder called .mozilla-thunderbird. My .mozilla folder only contains Firefox material. They've always had separate folders on my systems - Ubuntu and Windows both.

I have firefox, sunbird and eclipse in the ~/.mozilla folder. As far as I remember from Windows, when I used Thunderbird, it was also saved in the mozilla directory. I could be wrong tho.

---

### Post by CrazyG on 2009-07-01
Thanks for this, I run Hardy and Firefox has really been slow lately.  I have been looking at other browsers but they don't have the extensions I need (Adblock Plus and NoScript).

---

### Post by lovinglinux on 2009-07-01
> **CrazyG said:**
> Thanks for this, I run Hardy and Firefox has really been slow lately.  I have been looking at other browsers but they don't have the extensions I need (Adblock Plus and NoScript).

You are welcome. I also stick with Firefox because of the extensions. I use several of them and they make my web experience much better.

I'm updating the tutorial right now, to include a section on how to compile Firefox 3.5. I had 30% improvement in performance with an optimized 3.5 version on Jaunty ;)

---

### Post by lovinglinux on 2009-07-02
I have updated the "Firefox Alternatives & Newer Versions" section to include a warning about the *ubuntu-mozilla-daily* PPA repository, because the current Firefox package available there is already 3.5.1 Alpha.

---

### Post by oxf on 2009-07-05
OK thanks for refering me to this. It explains a lot!

One question: in my default profile folder there is a file called "lock" When I look at properties (or try to open it) it describes it as a "broken link". What is this and should I delete it?

Thanks

---

### Post by lovinglinux on 2009-07-05
> **oxf said:**
> OK thanks for refering me to this. It explains a lot!

One question: in my default profile folder there is a file called "lock" When I look at properties (or try to open it) it describes it as a "broken link". What is this and should I delete it?

Thanks

No, don't delete it. I'm not sure, but I think the lock file is created when you use the profile with Firefox, to prevent another Firefox instance using -no-remote to use the same profile, which could cause conflict of data being saved to it.

---

### Post by forestwalkerjoe on 2009-07-05
ok.. so far none of what the thread has told me to do works. 
I am in Ubuntu 904 wubi install. Which from what i understand should have NO trouble. I have added the PPA thing.. and i get an update on the system in a day or so.. then.. after the install.. the ABOUT area still has version 3. in it. and there are no new features. If you go to the Mizilla site.. it says wow.. you can down load this and install! i down load and its a TAR.Bz2 . If you extract.. then there is no file to install it. Its all (SO) files. I am assuming this means SOURCE. 
I have no experience with Compiling.. but found the HOW to complile from source.. and its last comments are move the file firefox etc TAR.Bz2 to the HOME directory.. which i have done.. then it says use this code to extract.the page i am reading from is here.. and scroll down to the compiling source area till you see the code in the next part.. which is where my install fails```
 http://ubuntuforums.org/showthread.php?t=1193567
``` ```
tar -xjf firefox-z.y.x-source.tar.bz2
```where i get this error.  ```
rj@ubuntu:~$ sudo tar -xjf firefox-z.y.x-source.tar.bz2
tar: firefox-z.y.x-source.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
rj@ubuntu:~$ 

``` I am getting frustrated. I am far from mastering LINUX Ubuntu.. but i do installs of it for my friends consistantly.. and with little or no complaints. IT doesnt help for me to NOT be able to update the dang Firefox install.. when its the "BEST BROWSER " on the market. You cant get any one to agree with that.. if its such a beast to install the upgrade. If this is the primary install of browser.. why in heck would you make it so hard to upgrade? 
some one want to trouble shoot my system to find out why each of the FIXES for upgrade i have tried.. FAILS? 

RJ

---

### Post by oxf on 2009-07-05
> **lovinglinux said:**
> No, don't delete it. I'm not sure, but I think the lock file is created when you use the profile with Firefox, to prevent another Firefox instance using -no-remote to use the same profile, which could cause conflict of data being saved to it.

OK fair enough. What concerns me is the "broken link" part  (which I also get as an errorif I try to open it). So would this have any impact on my performance?

---

### Post by lovinglinux on 2009-07-05
EDIT: I writing new reply with a step-by-step to solve your problem.

---

### Post by lovinglinux on 2009-07-05
> **oxf said:**
> OK fair enough. What concerns me is the "broken link" part  (which I also get as an errorif I try to open it). So would this have any impact on my performance?

Don't worry about it. It doesn't affect your performance. Besides, when you close Firefox it goes away.

---

### Post by forestwalkerjoe on 2009-07-05
I will look into the instructions you have added here.. but. as i said above.. the ABOUT area of my browser still says version 3.1. IF you go to the main site looking for download of the Newest released install.. you get this LINUX download of the Bz2. which does not install directly.. you are not reading my Fail comments. I was being told by another to download the full source file and try install from there.. which I DID also Download. and Yes i DO  know there are two different files there. ON is etc SOURCE tar.. and the other is just Tar.bz2. 
I dont want to sound disrespectful.. but there is much i did write abov that you are not answering.. or reading. I know this is because you have some much going on and probably didnt read it all. 
I DID read your whole list of things to do.. and as i said.. it fails for me. NO my install is not now 3.5.. NO i am not trying to get an early release candidate.. and as i have said.. i have already gone to the main Mozilla site and read their requirement to add th&#8364; PPA and IT DOes say.. one can update the old that way. BY installing the new and importing the settings from the old. My questions were that i have no instructions that seem to work for this BZ2 file. or the one that is fully the SOURCE code. NOR did the DB file i found install either. .. or the UPdate the web site says you can get. 
The update is supposed to allow an install of the 3.5 and when i do get an update statment in the update manager.. it says for installing version 3.5 but nothing changes. 
So to keep you from getting lost.. yes.. i have tried all the types i know of of getting this install.. including APT getting and nothing has actaully done the deed. 

FWJ

---

### Post by lovinglinux on 2009-07-05
> **forestwalkerjoe said:**
> I will look into the instructions you have added here.....

FWJ

I don't want to sound disrespectful either, but your posts are hard to understand. 

You are correct..there is a lot of threads I'm trying to help right now and sometimes I read them all over again to check the situation. For instance, take a look on [this thread](http://ubuntuforums.org/showthread.php?t=1197505) and see how much confusion was made until I decided to help the the OP step-by-step. I'm not saying I know better than others, but the fuzz around Firefox 3.5 makes people install all everything suggested on every post of every thread they can find and then the problems appear. Troubleshooting that is a nightmare, because I don't know what have already been done. Anyway, the problem was easily fixed with patience and following the correct procedures.

So, let's do it the same way. Take a breath. I will guide you through the steps and I'm sure you will have Firefox 3.5 in no time. Just to make you more comfortable, I just removed my Firefox 3.5 and did exactly the steps I'm posting here to make sure I'm not missing anything and it works perfectly.

First, we need to make sure you don't have other versions installed floating around.

Run the following command to remove Shiretoko. I know it's probably not installed, but it won't hurt to do this:

```
sudo apt-get remove firefox-3.5
```

Now let's remove any remaining manual Firefox installation:

```
sudo rm /usr/bin/firefox && sudo dpkg-divert --rename --remove /usr/bin/firefox && sudo rm -r /opt/firefox
```

Now go to "System >> Software Sources" and remove any PPA repository for Firefox that you have included there. 

Then delete any firefox-3.5****.tar.bz2 you have downloaded from Mozilla and saved in your home, not matter if it's source code or not. This is very important!

Now let's install Firefox 3.5.

Download the appropriate version to your system from [http://www.getfirefox.com](http://www.getfirefox.com). The site should detect your system specs appropriately and provide the right file. Save it in your home directory. Do not extract it, do not rename it, do not put it inside any sub-folder of home. Just save it in your home directory.

Tehn run this commands, one by one:

```
sudo tar -jxvf firefox-*.tar.bz2 -C /opt
```

```
rm firefox-*.tar.bz2
```

```
sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup
```

```
sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins
```

```
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
```

```
sudo ln -s /opt/firefox/firefox /usr/bin/firefox

```

Start Firefox and you will see the version is 3.5, not Shiretoko or anything else.

If you decide to revert to Firefox 3.0.11 for some reason, just run this code:

```
sudo rm /usr/bin/firefox && sudo dpkg-divert --rename --remove /usr/bin/firefox && sudo rm -r /opt/firefox
```

---

### Post by johnh10000 on 2009-07-06
Hi there you say flash isn't good in jaunty :(

I tried what you suggested, putting the non-free one on, using your code snipit.

I dialog box shows up Title"Network Problem",Body"Connection Problem. You could try to start chat"Ok button.

The ok button won't click :(

The site in question is: [http://www.aceradio.co.uk/chatroom.html](http://www.aceradio.co.uk/chatroom.html)

Any ideas?  BTW it works fine under windoz (xp)

---

### Post by lovinglinux on 2009-07-06
> **johnh10000 said:**
> Hi there you say flash isn't good in jaunty :(

I tried what you suggested, putting the non-free one on, using your code snipit.

I dialog box shows up Title"Network Problem",Body"Connection Problem. You could try to start chat"Ok button.

The ok button won't click :(

The site in question is: [http://www.aceradio.co.uk/chatroom.html](http://www.aceradio.co.uk/chatroom.html)

Any ideas?  BTW it works fine under windoz (xp)

The chat is working for me here, so I can't test the problem of the button. But this already suggest a problem on your connection. Since it works on XP, maybe the problem is some extension that is blocking the connection. Do you have AdBlock installed?

Additionally, you could try to disable ipv6. Type **about:config** in the address bar, then search for **network.dns.disableIPv6** and double click on it if the option is set to **false**, so it toggles to **true**.

---

### Post by johnh10000 on 2009-07-06
thanks gang, got it working!

see :[http://ubuntuforums.org/showthread.php?p=7568680#post7568680](http://ubuntuforums.org/showthread.php?p=7568680#post7568680)

---

### Post by forestwalkerjoe on 2009-07-06
ok.. now i am in a different boat i guess. 
The FF 3.5 installed.. but before the codes would not work. i did the removal of all the stuff you suggested.. and then it was able to do the install, i guess. 
I do have to say i was worried because you wanted me to remove so much and i was concerned it would not save my links and book marks and such. Its not compatible with a few of my  plugs and the FONT is wayyyy to big now.. every thing looks bigger. I tried to change the default font and that didn't do much.. and i pulled back on the zooom.. and it changed the text IN the page but not ON the browser itself. 
the Flash like thing.. took some time to want to work.. but it seems to be working. i have not tried any audio yet. you say there is optimization? these OPS will they smooth out some of what i mentioned here? 

I hope so.. 
i guess the troubles i had before were conflicting codes. i had all these DUMMY helper things.. from the update manager.. and when you had me code to remove 3.5 it removed about 5  of them.. then suddenly the install was able again. 
thanks for the help with that.. i do hope you have good ideas on the size and speed and such .. so i dont regret having this newer version. 


FWJ

---

### Post by lovinglinux on 2009-07-06
> **forestwalkerjoe said:**
> ok.. now i am in a different boat i guess.

Yes, you are :)

> **forestwalkerjoe said:**
> Its not compatible with a few of my  plugs and the FONT is wayyyy to big now.. every thing looks bigger. I tried to change the default font and that didn't do much.. and i pulled back on the zooom.. and it changed the text IN the page but not ON the browser itself. 


When you install a new version directly from Mozilla or through the other methods above, some of your extensions won't work, because they are dependent on the Firefox version. But the extension compatibility check can be disabled by setting the preference *extensions.checkCompatibility* to **false**. Some extensions might work this way, because they don't have anything in their code that could break on the new Firefox version, they just haven't been tested yet and the authors didn't change the version compatibility in the installation file. So when you disable extension check, they work as usual. Nevertheless, some extensions might have incompatible code, so use it at you own risk. 

To fix the FONT issue visit [http://ubuntuforums.org/showpost.php?p=7544051&postcount=3](http://ubuntuforums.org/showpost.php?p=7544051&postcount=3)

[QUOTE=forestwalkerjoe;7568806]the Flash like thing.. took some time to want to work.. but it seems to be working. i have not tried any audio yet. you say there is optimization? these OPS will they smooth out some of what i mentioned here? /QUOTE]

No they won't. You can try the Flash optimization section in the first post and [these tweaks](http://ubuntuforums.org/showthread.php?t=1152095), which helped a lot.[

---

### Post by lovinglinux on 2009-07-06
I have updated the installation instructions for Firefox 3.5, particularly the method 3, because Shiretoko 3.5 final release is already in Jaunty repositories. Nevertheless, I still recommend methods 1 and 2, specially if you don't like the Shiretoko name/logo and want the Firefox branding.

---

### Post by JLucien on 2009-07-07
I have a Firefox question that I hope is ok to ask in this thread.

I want to do a clean reinstall of my system to upgrade from Gutsy, but I am keeping my existing home partition.

Will the new Firefox installed on my Jaunty system use my existing data or will I have to explicitly backup and reimport my bookmarks?

Great guide so far!

---

### Post by lovinglinux on 2009-07-07
> **JLucien said:**
> I have a Firefox question that I hope is ok to ask in this thread.

I want to do a clean reinstall of my system to upgrade from Gutsy, but I am keeping my existing home partition.

Will the new Firefox installed on my Jaunty system use my existing data or will I have to explicitly backup and reimport my bookmarks?

Great guide so far!

No problem at all. Questions are always welcome. That's the purpose of this thread. Besides, this also helps to improve it.

It will use your existing data. Nevertheless, is always a good idea to backup first. Firefox profiles can become corrupted pretty easy and depending on the version you are upgrading, some things might not work. I recommend using the [FEBE](https://addons.mozilla.org/en-US/firefox/addon/2109) extension to backup your entire profile, including bookmarks, extensions, settings, passwords and so on.

---

### Post by JLucien on 2009-07-07
> **lovinglinux said:**
> No problem at all. Questions are always welcome. That's the purpose of this thread. Besides, this also helps to improve it.

It will use your existing data. Nevertheless, is always a good idea to backup first. Firefox profiles can become corrupted pretty easy and depending on the version you are upgrading, some things might not work. I recommend using the [FEBE](https://addons.mozilla.org/en-US/firefox/addon/2109) extension to backup your entire profile, including bookmarks, extensions, settings, passwords and so on.

Thanks for answering! I hope this includes Greasemonkey too.

---

### Post by lovinglinux on 2009-07-07
I have updated the "Installing Other Versions" sections with a detailed explanation of each method, comparing the most important differences.

---

### Post by Andy06 on 2009-07-08
Hi lovinglinux, 

Your guide is awesome but I will still be asking some redundant questions mainly because various threads around the forums give wildly different info. I think I know the correct answers to these questions but I just want to confirm because in addition to my own system, I will also be making changes to about 50 other computers in my college for friends, fellow students, college comps etc.
I have already read the following:

[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

[http://www.asoftsite.org/s9y/archives/160-FAQ-Where-can-I-get-firefox-3.5-for-Ubuntu.html](http://www.asoftsite.org/s9y/archives/160-FAQ-Where-can-I-get-firefox-3.5-for-Ubuntu.html)

and almost all of the threads about firefox 3.5 as listed in your other counter thread. (and these are the threads with the various opinions that caused the confusion)

I am in no hurry to install it asap and want as official a solution as possible but would like to get it sooner rather than later since all the windows folks got it a week ago and we are taking a lot of flak for it :D

So here goes
1. Will the latest Firefox 3.0.11 be automatically updated to 3.5 ever? [I'm guessing not but could the meta package be updated itself?]
So should I ask Jaunty users to wait or to install the 3.5b4 Shiretoko package and force an upgrade through that route?

2. When will backports kick in? Will they ever kick in? This is relevant to the Hardy comps (college "official" comps such as admin comps) and to Intrepid comps (lazy friends who haven't upgraded). 

3. How to backports work exactly and what do they do? I read all of the help documentation but do backports enable every single new feature version for older users directly or merely the latest feature version packaged as the default base for the latest Ubuntu?

4. The official Jaunty installations of FFv3.5 from the repos installed it side by side with FFv3.0, the profile is in a separate firefox 3.5 folder in .mozilla. How to completely get rid of FFv3.0 and ensure the profile stays under the "firefox" folder? Should I uninstall and purge the standard firefox meta package? Will uninstalling the old FF break some dependencies for the new FFv3.5?

5. What's the solution to the non standard name (Shiretoko) and blue logo despite this being the "official" full version?

Thanks a lot for your help
Just want to be extra cautious.

---

### Post by lovinglinux on 2009-07-08
> **Andy06 said:**
> 
1. Will the latest Firefox 3.0.11 be automatically updated to 3.5 ever? [I'm guessing not but could the meta package be updated itself?]

I think several threads posted this week creates a lot of confusion around these questions. I'm not experienced enough with Ubuntu to reply with confidence, but as far as I understand, the answer is no for both. Firefox 3.0 won't be updated to 3.5 in Jaunty repositories, since it introduces new features/code, instead of just security/stability updates. Besides, firefox-3.5 is in the universe repositories and thus are not maintained by Canonical. They are offered as an easy solution for early adoption and testing. That's why it uses a different profile folder, a different launcher and is not branded as Firefox. If you check the description of both firefox meta package and the firefox-3.0 package, you will see that "Canonical provides critical updates for firefox (firefox-3.0) until October 2010", while in all other packages you see "Canonical does not provide updates for firefox-x.y. Some updates may be provided by the Ubuntu community".

I also think most discussions surrounding the question of Firefox 3.5 will be or won't be in the repositories, fails to address the distinction between main and universe repositories. Not to mention backports. When they say it will be in the repositories, I think they mean that it will be available as separate package maintained by the community, not as a firefox-3.0 or meta package update.

> **Andy06 said:**
> So should I ask Jaunty users to wait or to install the 3.5b4 Shiretoko package and force an upgrade through that route?

This package already has been updated to the final version. But this is still a hard question to answer, specially considering that you will be updating about 50 computers. In my opinion, the fact that firefox-3.5 uses a different profile folder is enough to reject this method for a large scale update, unless you take measures to minimize possible issues. I don't know how much responsible you will be for those computers, but, imagine this scenario:

When you first install Shiretoko, all personal profiles will be copied to ~/.mozilla/firefox-3.5. This probably won't be a problem initially, since all profiles are automatically copied, but if an user decides to go back to 3.0 or if eventually uses firefox-3.0 and firefox3.5 at the same time, he will have 2 different profiles, since they are not synchronized. Additionally, when Karmic comes out and they upgrade, Firefox will be 3.5 and will be using the regular profile folder. So, some users might be surprised with missing settings and extensions once they upgrade. If they are not aware that Shiretoko uses a different profile, they might loose important data. This can be mitigated by informing them about the difference or solved by the answer to question 4, but does it worth the trouble?

> **Andy06 said:**
> 2. When will backports kick in? Will they ever kick in? This is relevant to the Hardy comps (college "official" comps such as admin comps) and to Intrepid comps (lazy friends who haven't upgraded). 

3. How to backports work exactly and what do they do? I read all of the help documentation but do backports enable every single new feature version for older users directly or merely the latest feature version packaged as the default base for the latest Ubuntu?

I never used backports, so I will refrain myself from replying this one. :)

What I know is what is available through the official documentation at [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports), but I believe Firefox 3.5 would be a candidate for upgrades using backports.


> **Andy06 said:**
> 4. The official Jaunty installations of FFv3.5 from the repos installed it side by side with FFv3.0, the profile is in a separate firefox 3.5 folder in .mozilla. How to completely get rid of FFv3.0 and ensure the profile stays under the "firefox" folder? Should I uninstall and purge the standard firefox meta package? Will uninstalling the old FF break some dependencies for the new FFv3.5?

What you can do about the profile is to create, before installing firefox-3.5, a symbolic link to ~/.mozilla/firefox and rename it to firefox-3.5. This will work and will guarantee that the same profile will be used for firefox-3.0 and firefox-3.5. This also guarantees that on future updates, the users won't be surprised with totally different settings. Nevertheless, this might introduce additional problems, if the users keep using both versions. Every time you launch the profile with a different version, Firefox will check for extension compatibility. Right now, this won't be a big problem, because most extensions updated to work with Firefox 3.5 still work with 3.0. But soon there will be lots of extensions that will work only with 3.5. Additionally, I think this might increase the chances of profile corruption.

To create the symlink, run the following command (before installing 3.5 or make sure firefox-3.5 doesn't exist):

```
ln -s ~/.mozilla/firefox ~/.mozilla/firefox-3.5
```

I wouldn't recommend removing or purging firefox-3.0 or firefox meta package. I did a test on a virtual machine and Shiretoko works without it, but at least the searchplugins were broken.  Additionally, if you first remove firefox then install firefox-3.5, it install the other packages all over again. 

> **Andy06 said:**
> 
5. What's the solution to the non standard name (Shiretoko) and blue logo despite this being the "official" full version?

I think there isn't a solution, at least not a legal one.

Considering your scenario, if I were on your situation, I would use the method #2 ( Ubuntuzila), since it offers official Mozilla packages, with branding, possibility of automatic updates, automatic modification of default launchers, does not create a new profile folder and it's easy to revert to default packages, without braking anything.

---

### Post by Andy06 on 2009-07-08
Well thanks a lot for those detailed replies. :D

Unfortunately, it confirmed my fears about the update behaviour hehe.

Since the Firefox 3.5 package is part of the universe, will it get the same sort of updates along with the vanilla and official mozilla builds (such as 3.5.1, 3.5.2) and like we got for FFv3.0.0 till FFv3.0.11 or is that upto us to manage manually?

---

### Post by lovinglinux on 2009-07-08
> **Andy06 said:**
> Well thanks a lot for those detailed replies. :D

Unfortunately, it confirmed my fears about the update behaviour hehe.

Since the Firefox 3.5 package is part of the universe, will it get the same sort of updates along with the vanilla and official mozilla builds (such as 3.5.1, 3.5.2) and like we got for FFv3.0.0 till FFv3.0.11 or is that upto us to manage manually?

Oh, yes. I believe they will continue to feed the Tamagochies :)

Nevertheless, the Ubuntuzilla method is the most guaranteed and synchronized with Windows releases, because it relies on Mozilla releases site. For instance, Ubuntuzilla users were able to update to Firefox 3.5 final the same day Mozilla officially released the final version, while the universe repository users where able to update only yesterday. Additionally, it provides everything you need (brand, logo, updates, integration, same profile, easy removal...).

---

### Post by lovinglinux on 2009-07-08
> **JLucien said:**
> Thanks for answering! I hope this includes Greasemonkey too.

Yes, all your extensions. Some will require updates tho.

---

### Post by martinbaselier on 2009-07-08
a shorter version of your firefox-optimize script:
```

killall firefox
find $HOME/.mozilla/ \( -name "*.sqlite" \) -exec sqlite3 {} \;

```

---

### Post by lovinglinux on 2009-07-08
> **martinbaselier said:**
> a shorter version of your firefox-optimize script:
```

killall firefox
find $HOME/.mozilla/ \( -name "*.sqlite" \) -exec sqlite3 {} \;

```

Unfortunately, it doesn't seem to work or I'm doing something wrong. After running the command i get an sqlite prompt asking for commands and when I enter *vacuum;* nothing happens.

---

### Post by martinbaselier on 2009-07-08
my mistake, I forgot vacuum
```

find $HOME/.mozilla/ \( -name "*.sqlite" \) -exec sqlite3  {} "vacuum" \;

```

---

### Post by lovinglinux on 2009-07-08
> **martinbaselier said:**
> my mistake, I forgot vacuum
```

find $HOME/.mozilla/ \( -name "*.sqlite" \) -exec sqlite3  {} "vacuum" \;

```

Thank you very much. I have updated the tutorial.

BTW, I also changed the Flash Optimization section.

---

### Post by Andy06 on 2009-07-08
Lovinglinux,

With the Ubuntuzilla version, do all your plugins work without hiccups? I understand that people have been having trouble getting their flash and java to work with the ubuntuzilla route.

What about the font rendering problem? I don't have it throughout the 3.5 app, just in text entry boxes, like the one I am typing in now. Menus, interface font, other display fonts (such as reading the forums) is all fine. Wierd yeah? I don't want to be editing fonts.conf for fear of messing it up for some other GNOME app.

Does Ubuntuzilla's version have the font issue? Any "official" resolution to the font problem. I'm a bit non inclined to use ubuntuzilla since its a non official script even if it uses the official version. But if it doesn't have the font issues and you recommend it, I'll give it a go.

To be honest, this whole Firefox 3.5 installation on Ubuntu thing is becoming a fiasco here in college. Lots of people have tried all sorts of routes with varying degrees of success (no 100% success yet), I've seen people unpack n use the tar.gz, install from the tar.gz, use scripts, use the 3.5b4 from repos, gksudo firefox to enable check for updates (dint work), try enabling backports and proposed (one person got it through proposed couple of days ago, just one), all types of PPAs etc. :( 

I installed it on windows today and I dare say that it felt....seamless.

---

### Post by lovinglinux on 2009-07-08
> **Andy06 said:**
> Lovinglinux,

With the Ubuntuzilla version, do all your plugins work without hiccups? I understand that people have been having trouble getting their flash and java to work with the ubuntuzilla route.

What about the font rendering problem? I don't have it throughout the 3.5 app, just in text entry boxes, like the one I am typing in now. Menus, interface font, other display fonts (such as reading the forums) is all fine. Wierd yeah? I don't want to be editing fonts.conf for fear of messing it up for some other GNOME app.

Does Ubuntuzilla's version have the font issue? Any "official" resolution to the font problem. I'm a bit non inclined to use ubuntuzilla since its a non official script even if it uses the official version. But if it doesn't have the font issues and you recommend it, I'll give it a go.

To be honest, this whole Firefox 3.5 installation on Ubuntu thing is becoming a fiasco here in college. Lots of people have tried all sorts of routes with varying degrees of success (no 100% success yet), I've seen people unpack n use the tar.gz, install from the tar.gz, use scripts, use the 3.5b4 from repos, gksudo firefox to enable check for updates (dint work), try enabling backports and proposed (one person got it through proposed couple of days ago, just one), all types of PPAs etc. :( 

I installed it on windows today and I dare say that it felt....seamless.

Give me some time to check it out. I have to install Ubuntuzilla again, since I'm using a compiled Mozilla version.

---

### Post by Andy06 on 2009-07-08
Umm...Can you also confirm this,

FFv3.5 renders improperly on some pages. Interestingly, even the most obscure of pages are perfect but Live mail (hotmail) and Facebook have problems. So basically 2 of the most popular websites both of which are probably in the top 10 overall in the world.

In hotmail, there are misalignments etc of the log out button and near the user options drop down and in facebook, the chat pop in chat window isn't there, you have to use pop out chat. 
I think maybe its mucking up AJAX or Javascript somewhere because both those pages are heavy on that and the widgets with the errors certainly rely on them.

More interestingly, the Windows FFv3.5 exhibits no such behaviour and works perfectly.

Even more interestingly, the vanilla Mozilla build of FFv3.5 which can be run from a self contained folder also does not exhibit this behaviour!! It works fine too, hell even the font rendering is perfect! 

So this manifests itself in the Shiretoko 3.5 final from the repos, saw it also on some Ubuntu security and daily PPA installs on another computer in the dorm. No one on Ubuntuzilla so far so don't know about that.

---

### Post by forestwalkerjoe on 2009-07-08
I am not even sure how this happened.. but in the process of getting the FF 3.5 to install.. we discovered a few conflicts in my system.. once those were removed as suggested by you.. the install went well. I have some small issues with how the videos play and once in a while the synch is off.. but the other reason i am writing is there were tweaks you showed me that i could improve my system. Getting more from the CPU and so on. some would not work.. the CPU one did. 
i had to set the graphics back to default to get back in my system , so the graphics Tweak was a bad idea for me. 
I had discussed with you a constant need for fixing my sound.. since the day i updated from 810 to 904.. some of the system sounds would not work. I over the months have fixed nearly all of the issue.. with the exception of start up sound.. LOG ON and such.. just would not play. 
i could FIND the file and it would play.. but it would not play on start up of machine. 
after doing the Graphics default fix.. i had not had a chance to reboot again.. till this morning. when i was surprised to find.. i NOW have full system sounds too. 
NOT sure what the FIX did.. or which fix did what.. but i am grateful in any case. 

FWJ

---

### Post by lovinglinux on 2009-07-08
> **Andy06 said:**
> Lovinglinux,

With the Ubuntuzilla version, do all your plugins work without hiccups? I understand that people have been having trouble getting their flash and java to work with the ubuntuzilla route.

What about the font rendering problem? I don't have it throughout the 3.5 app, just in text entry boxes, like the one I am typing in now. Menus, interface font, other display fonts (such as reading the forums) is all fine. Wierd yeah? I don't want to be editing fonts.conf for fear of messing it up for some other GNOME app.

Does Ubuntuzilla's version have the font issue? Any "official" resolution to the font problem. I'm a bit non inclined to use ubuntuzilla since its a non official script even if it uses the official version. But if it doesn't have the font issues and you recommend it, I'll give it a go.

To be honest, this whole Firefox 3.5 installation on Ubuntu thing is becoming a fiasco here in college. Lots of people have tried all sorts of routes with varying degrees of success (no 100% success yet), I've seen people unpack n use the tar.gz, install from the tar.gz, use scripts, use the 3.5b4 from repos, gksudo firefox to enable check for updates (dint work), try enabling backports and proposed (one person got it through proposed couple of days ago, just one), all types of PPAs etc. :( 

I installed it on windows today and I dare say that it felt....seamless.

I have installed all over again 3 times using each method. Installation went flawlessly every time with all methods. The only issue I had was launching Shiretoko updated using the *ubuntu-mozilla-daily* PPA. Apparently it was using a corrupted or incompatible profile copied from ~/.mozilla/firefox which rendered an error. It didn't start. So I moved ~/.mozilla/firefox and let Shiretoko create it's own profile, which solved the problem.

I don't know about the font rendering problem. All methods resulted in the same font rendering. They look slightly thinner than Firefox 3.0, but I don't have any weird artifacts.

I tested flash rendering with the same video from YouTube and they all performed the same. The only difference noticed was using Swiftfox and a compiled version with PGO and processor optimizations, when the video buffered faster. Some pause due to video buffering was noticed on all versions except for those two optimized versions. But it the third test it went well (yes, I deleted the cache before each test :)).

I also tested them with Peacekeeper benchmark and couldn't find any significant difference, except for Swiftfox and the compiled version, for obvious reasons.

Here are the results and screenshots:

**#1 [Psychocats](http://ubuntuforums.org/attachment.php?attachmentid=120424&stc=1&d=1247098220)**
Benchmark - 860 points
Flash CPU usage - ~45%

**#2 [Ubuntuzilla](http://ubuntuforums.org/attachment.php?attachmentid=120425&stc=1&d=1247098308)**
Benchmark - 875 points
Flash CPU usage - ~45%
[B]
#3 [PPA](http://ubuntuforums.org/attachment.php?attachmentid=120426&stc=1&d=1247098356)[/B]
Benchmark - 863 points
Flash CPU usage - ~45%

**#4.1 [Shiretoko](http://ubuntuforums.org/attachment.php?attachmentid=120427&stc=1&d=1247098400)**
Benchmark - 858 points
Flash CPU usage - ~45%

**#4.2 [Swiftfox-Prescott-PGO](http://ubuntuforums.org/attachment.php?attachmentid=120428&stc=1&d=1247098447)**
Benchmark - 1005 points
Flash CPU usage - ~45%

**Firefox-Prescott-PGO**
Benchmark - 1082 points
Flash CPU usage - ~45%


> **Andy06 said:**
> Umm...Can you also confirm this,

In hotmail, there are misalignments etc of the log out button and near the user options drop down and in facebook, the chat pop in chat window isn't there, you have to use pop out chat.

Are you serious? :)

The hotmail issue is barely noticeable. There is a misalignment in the logout button, but if you didn't mentioned I would even noticed. Anyway, for anything coming from Redmond I would except intrusive adds popping up all over the place and the page not rendering at all :)  I don't have a Facebook account.


> **forestwalkerjoe said:**
> I am not even sure how this happened.. but in the process of getting the FF 3.5 to install.. we discovered a few conflicts in my system.. once those were removed as suggested by you.. the install went well. I have some small issues with how the videos play and once in a while the synch is off.. but the other reason i am writing is there were tweaks you showed me that i could improve my system. Getting more from the CPU and so on. some would not work.. the CPU one did. 
i had to set the graphics back to default to get back in my system , so the graphics Tweak was a bad idea for me. 
I had discussed with you a constant need for fixing my sound.. since the day i updated from 810 to 904.. some of the system sounds would not work. I over the months have fixed nearly all of the issue.. with the exception of start up sound.. LOG ON and such.. just would not play. 
i could FIND the file and it would play.. but it would not play on start up of machine. 
after doing the Graphics default fix.. i had not had a chance to reboot again.. till this morning. when i was surprised to find.. i NOW have full system sounds too. 
NOT sure what the FIX did.. or which fix did what.. but i am grateful in any case. 

FWJ

That's the way I like it. Fixing problems even when messing things up :lol: 
I have included a warning about the graphics tweak. Thanks.

---

### Post by Andy06 on 2009-07-09
You mentioned your fonts looking thinner. Is this throughout for ALL text? Because that is the problem everyone is facing.

I, however am facing a different one, for me, ALL text is normal EXCEPT the one I manually type in text entry boxes like the one we use to type in replies in this forum. That font is more wiry, everything else is like it should be. Is it possible then that just the default fonts have changed and there might in fact be no problem?

> Are you serious?

The hotmail issue is barely noticeable. There is a misalignment in the logout button, but if you didn't mentioned I would even noticed. Anyway, for anything coming from Redmond I would except intrusive adds popping up all over the place and the page not rendering at all I don't have a Facebook account.

Hehe. Yeah, but to be honest, I think it is quite serious since it is a regression. Most importantly, I don't think pointing the finger at Mozilla (or Microsoft) will do here especially since the windows version of FFv3.5 renders it perfectly. Did you see this problem in all installs of Firefox or just some? And if just some, which ones?

I don't know if you have Windows Vista but if you do, try and install FFv3.5 on it and see the performance. It will really come to life. Will be smoother, faster, snappier, no flickering, and faster rendering (last one is very subjective, so I can't say with conviction). This was the case with v3.0 as well and its just annoying since Linux should be Firefox's native soil.

Running it in Linux still feels like I am running it with half the RAM compared to windows. I guess you would already know what the difference is like since you are running your own compiled optimised version. Its similar to the difference between a vanilla build and your faster custom compiled build.

Do let me know if you see those rendering issues on only some or all of the builds (PPA, Ubuntuzilla, Psychocats, Repo Shiretoko and your own build).

Thanks a ton :D

---

### Post by Andy06 on 2009-07-09
I am trying to compile a list of PPAs and repos to have up-to-date software on a Ubuntu system.

Which method do you think I should opt for?

In method #1, you mention:

> It does not provide new version checking and download. You have to download new versions manually, remove the old version before updating with a new one and perform the installation commands for each new install.

Why is that? If it is not integrated with Apt/Synaptic in any way, is the "Check for Updates" still greyed out? Can I not check for updates manually even if I "gksu Firefox 3.5"? I think gksudo should work shouldn't it?

Ubuntuzilla is probably the perfect method but unfortunately its very unofficial :) so method #2 is not a candidate currently.

With method #3, the updates are only being "tested" for Ubuntu right, but will be official for Mozlla? I am assuming Ubuntu begins testing only after Mozilla releases a new update officially? So if 3.5.1 was released by Mozilla on the 20th, it would be in this PPA and under "testing" from 20-25th before being an official Ubuntu release?

And with method #4.1, you mention:

> but updates are performed only after being proposed by the universe repository maintainers and approved to enter this repository. You won't get regular updates like using the PPA repositories

So will the shiretoko from repos updates keep in step with Mozilla, give or take a few days like the ones in method#3 and the way it was for FFv3.0? Or will each update have to be proposed? Because if each is proposed, then this is hardly "official" at all despite being in the repos.

What are the testers in #3 testing for anyway, as in where are they pushing their updates into after they become official? Into method #4.1 or for Karmic testers who are getting it through the Karmic updates and karmic security channels?

---

### Post by lovinglinux on 2009-07-09
> **Andy06 said:**
> You mentioned your fonts looking thinner. Is this throughout for ALL text? Because that is the problem everyone is facing.

Yep, it seems that all text is affected, but the bold ones aren't bad. Take a look at the screenshots on the previous post.

> **Andy06 said:**
> Is it possible then that just the default fonts have changed and there might in fact be no problem?

I tried to change the fonts with no luck. Nevertheless, Firefox 3.0 also wasn't very good with fonts. I had to tweak a lot to find a combination of settings that pleased me.

> **Andy06 said:**
> Hehe. Yeah, but to be honest, I think it is quite serious since it is a regression. Most importantly, I don't think pointing the finger at Mozilla (or Microsoft) will do here especially since the windows version of FFv3.5 renders it perfectly. Did you see this problem in all installs of Firefox or just some? And if just some, which ones?

I just tested this problem on my own compiled Firefox, because when I saw your post I was already posting the results of my tests and I'm not going to install all of them again :)

> **Andy06 said:**
> I don't know if you have Windows Vista but if you do, try and install FFv3.5 on it and see the performance. It will really come to life. Will be smoother, faster, snappier, no flickering, and faster rendering (last one is very subjective, so I can't say with conviction). This was the case with v3.0 as well and its just annoying since Linux should be Firefox's native soil.

Running it in Linux still feels like I am running it with half the RAM compared to windows. I guess you would already know what the difference is like since you are running your own compiled optimised version. Its similar to the difference between a vanilla build and your faster custom compiled build.

I have Windows 7 on a virtual machine, but I don't think it would be the perfect environment for comparison. Nevertheless, I might try it just for the sake of curiosity.

> **Andy06 said:**
> Do let me know if you see those rendering issues on only some or all of the builds (PPA, Ubuntuzilla, Psychocats, Repo Shiretoko and your own build).

The font rendering issue is on all of them. Check the screenshots.

---

### Post by halovivek on 2009-07-10
One of the wonderful Thread :) Thanks for posting

---

### Post by lovinglinux on 2009-07-10
> **halovivek said:**
> One of the wonderful Thread :) Thanks for posting

You are welcome.

> **Andy06 said:**
> Why is that? If it is not integrated with Apt/Synaptic in any way, is the "Check for Updates" still greyed out? Can I not check for updates manually even if I "gksu Firefox 3.5"? I think gksudo should work shouldn't it?

Sorry, I missed this post yesterday.

Ubuntuzilla check for new releases on Mozilla releases site and then download and extract the *.tar.bz2* file. It's not a package manager. It is similar to the auto-update feature of Firefox, in the sense that it gets the Mozilla official distributions, but it has it's own script for checking new versions, downloading and extracting them to the Firefox folders. 

I never tried to enable the update feature of Firefox using "gksudo". It should work like Ubuntuzilla updates, as long as you don't enable it for the official Ubuntu firefox meta package (i.e. Firefox 3.0), which I do not recommend. If you enable it for the manually installed *.tar.bz2* file from method #1, then it will work pretty much the same way as an Ubuntuzilla install. I also wouldn't recommend this method for those who installed Firefox via other repositories. Additionally, be careful and do not use "sudo", otherwise your profile can become inaccessible and corrupted.

> **Andy06 said:**
> Ubuntuzilla is probably the perfect method but unfortunately its very unofficial :) so method #2 is not a candidate currently.

Well, if you want Ubuntu official and tested, then wait for Karmic Koala. If you want stable new versions as soon as they are released, without hassle, then use Ubuntuzilla or manually update with method #1.

> **Andy06 said:**
> And with method #4.1, you mention:
...

So will the shiretoko from repos updates keep in step with Mozilla, give or take a few days like the ones in method#3 and the way it was for FFv3.0? Or will each update have to be proposed? Because if each is proposed, then this is hardly "official" at all despite being in the repos.

Each update has to be proposed and is not official, it's maintained by the community for those who can't wait.

> **Andy06 said:**
> With method #3, the updates are only being "tested" for Ubuntu right, but will be official for Mozlla? I am assuming Ubuntu begins testing only after Mozilla releases a new update officially? So if 3.5.1 was released by Mozilla on the 20th, it would be in this PPA and under "testing" from 20-25th before being an official Ubuntu release?

It is tested for Ubuntu, but it's not Ubuntu official, it's semi-official :) until they become part of the firefox meta package, which will probably not happen until Karmic. But in my opinion it is as good as the official one. Keep in mind that depending on the PPA you choose, you will also get unstable releases, which means those that are really being tested, not those that are already released by Mozilla to the public.

> **Andy06 said:**
> What are the testers in #3 testing for anyway, as in where are they pushing their updates into after they become official?  Into method #4.1 or for Karmic testers who are getting it through the Karmic updates and karmic security channels?

They get into Jaunty (method #4.1) for testing and as a preview, but their main focus is Karmic.

> **ubuntu-mozilla-security** - Users of the most recent Ubuntu release can get new versions of Firefox a few days early from the semi-official ubuntu-mozilla-security archive. This archive holds updates to the Mozilla suite (including Firefox) while they're tested for security and stability. 

**ubuntu-mozilla-daily** - Users of recent Ubuntu releases can get the latest development version of Firefox from the semi-official ubuntu-mozilla-daily archive. This archive holds updates to the Mozilla suite (including Firefox) that are under active development - for example, a preview version of Firefox 3.5.1 was available at the time of writing. Although these packages will work well most of the time, you should expect crashes and other problems.

---

### Post by WongFuChu on 2009-07-11
I'm currently using firefox 3.0.11 that came with eeebuntu. I was wondering about compiling firefox 3.5 just for kicks...

If I do so and install it, then there's two instances of firefox: 3.0.11 and 3.5. I was wondering... how would I get rid of the older one? How would you uninstall 3.5 (I'm a newb; noticed it's not in gnome app install)?

Also, *just how much faster* is 3.5 if compiled with profiledbuild? I mean, is it noticeably faster than the one that comes with the Jaunty?

---

### Post by Andy06 on 2009-07-11
Ok I think I wasn't clear enough. :D

I meant the testing that the ubuntu people are doing for the Security PPA, those are the updates that get pushed to the people using the meta package right? Updates such as the 3.0.0 to 3.0.1 and 3.0.10 to 3.0.11.

So when I enable this PPA and get these updates that are being "tested" at ubuntu-mozilla-security, these updates are merely being tested for Ubuntu right? But they are based on the already released version for the rest of the world and just being tested for ubuntu integration.

As a real case: Say Mozilla pushes out FFv3.5.1 on the 20th of July, then ubuntu-mozilla-security will test 3.5.1 from 20th-25th and push it out as "official" on 25th right? So basically by enabling this PPA and getting it on the 20th itself means we are getting a finalised Mozilla version but a testing Ubuntu version....correct? Or have I got it wrong somewhere?

And if I use a PPA, will the PPA updates conflict with the regular update manager in that both will want to update my firefox to different things?

---

### Post by lovinglinux on 2009-07-11
> **WongFuChu said:**
> I'm currently using firefox 3.0.11 that came with eeebuntu. I was wondering about compiling firefox 3.5 just for kicks...

If I do so and install it, then there's two instances of firefox: 3.0.11 and 3.5. I was wondering... how would I get rid of the older one? How would you uninstall 3.5 (I'm a newb; noticed it's not in gnome app install)?

It's not recommended to uninstall the official Firefox 3.0.11. Leave it there. It won't hurt, since the compiled version is installed on another directory.

When you run the command *checkinstall*, described in the "Compiling Firefox" section of the tutorial, it creates a deb package and add it to Synaptic. So you can uninstall Firefox 3.5 from there, like any other application in the repositories.

Nevertheless, the name of the package depends on which name you choose during the *checkinstall* process. If you do not change the default values, it will be installed as ***mozilla-1.9.1***. For example I have changed the name to **firefox-prescott-pgo** (see attached screenshot)

The Removal instructions are also included in the compiling section.

If you try to compile, please let me know how it went, so I can improve the tutorial of you find any errors or difficulties.

> **WongFuChu said:**
> Also, *just how much faster* is 3.5 if compiled with profiledbuild? I mean, is it noticeably faster than the one that comes with the Jaunty?

In my system, the PGO didn't increased the performance that much, just about 10%. What really made the difference was the optimizations flags for my processor (**-O3 -march=prescott**) included in the mozconfig file. The performance increased by 30%.


> **Andy06 said:**
> Ok I think I wasn't clear enough. :D

I meant the testing that the ubuntu people are doing for the Security PPA, those are the updates that get pushed to the people using the meta package right? Updates such as the 3.0.0 to 3.0.1 and 3.0.10 to 3.0.11.

No. When approved, they are pushed into firefox-3.5 package in Jaunty, not the official firefox-3.0 (related to the meta package). But they are pushed to Karmic Koala repositories, where the official Firefox package will be firefox-3.5 and where firefox-3.0 probably won't exist.

> **Andy06 said:**
> So when I enable this PPA and get these updates that are being "tested" at ubuntu-mozilla-security, these updates are merely being tested for Ubuntu right? But they are based on the already released version for the rest of the world and just being tested for ubuntu integration.

Yes.

> **Andy06 said:**
> As a real case: Say Mozilla pushes out FFv3.5.1 on the 20th of July, then ubuntu-mozilla-security will test 3.5.1 from 20th-25th and push it out as "official" on 25th right? So basically by enabling this PPA and getting it on the 20th itself means we are getting a finalised Mozilla version but a testing Ubuntu version....correct? Or have I got it wrong somewhere?

Yes.

> **Andy06 said:**
> And if I use a PPA, will the PPA updates conflict with the regular update manager in that both will want to update my firefox to different things?

No. Because they won't update firefox-3.0 package in Jaunty, they will update firefox-3.5 package. The firefox-3.0 package will be always there in Jaunty and will be only updated to 3.0.12, 3.0.13 and so on.

When Karmic Koala gets out, it will already come with firefox-3.5 as the default.

---

### Post by WongFuChu on 2009-07-11
Alright, thanks.

Compiling still as I type. I'd say its been over 4 or 5 hours... could even be 6.

The flags I'm using is -02 -march=prescott (not sure if that's correct; I googled for intel atom and it said that).

Man... I hope it's worth it. I mean, with a tmpfs mounted profile, I'm hoping to experience this "lightning fast" firefox.

---

### Post by Andy06 on 2009-07-11
Gee thanks a lot for all the clarifications. I have one more question unfortunately. :D (I am a curious type)

By conflict I meant:

1.If I have say the official FFv3.5 of Mozilla installed (like from method 1), then I enable a repository [ubuntu security one], will it update it? Even though the initial install was not from that repo and so in effect, doesn't "point" to it?

2.Now if I also have the FFv3.5 Shiretoko from universe repo installed, I will have two FFv3.5s, and two update sources (ubuntu security PPA and regular community updates for Shiretoko), won't that cause massive confusion, like the wrong update going to the wrong firefox? Or will the newer version from the combined sources always over rule the older ones and update ALL Firefoxes to that latest version.

Sorry, I know it sounds very hypothetical but a lot of people I am trying to help have multiple Firefoxes (some have upto 4-5 of them: Mozilla tar.gz, Mozilla official installed like from method #1, Shiretoko 3.5 from universe repos, ubuntuzilla FF, some have daily builds plus everybody has the FFv3.0 and then the truly adventurous mess it all up by throwing swiftfox in it too hehe)

---

### Post by Andy06 on 2009-07-11
I think I should add this question as well since it will make things a lot clearer for our context.

If I manually install program A and THEN add the repositories for A, does A still get updated despite not being initially installed from the repos? [In this case A being a particular Firefox].

I'm guessing probably yes since for lots of programs like Cairo, Wine, Gnome Do, Opera etc, once you add the third party repos, they start querying them as well and downloading the latest updates from there. In case of Firefox, the whole situation is a mess, so I am not so sure about Firefox.

---

### Post by lovinglinux on 2009-07-11
> **WongFuChu said:**
> Alright, thanks.

Compiling still as I type. I'd say its been over 4 or 5 hours... could even be 6.

The flags I'm using is -02 -march=prescott (not sure if that's correct; I googled for intel atom and it said that).

Man... I hope it's worth it. I mean, with a tmpfs mounted profile, I'm hoping to experience this "lightning fast" firefox.

I don't know if it will run. 

> 
On x86 and x86-64 CPUs, -march will generate code specifically for that CPU using all its available instruction sets and the correct ABI; it will have no backwards compatibility for older/different CPUs.

So, if you use the wrong march option, the application will not run.

You should read this before creating your mozconfig:

[http://www.gentoo.org/doc/en/gcc-optimization.xml](http://www.gentoo.org/doc/en/gcc-optimization.xml)

Links that might help:

[http://en.wikipedia.org/wiki/Intel_Atom](http://en.wikipedia.org/wiki/Intel_Atom)
[http://gcc.gnu.org/onlinedocs/gcc-4.3.3/gcc/i386-and-x86_002d64-Options.html#i386-and-x86_002d64-Options](http://gcc.gnu.org/onlinedocs/gcc-4.3.3/gcc/i386-and-x86_002d64-Options.html#i386-and-x86_002d64-Options)
[http://stackoverflow.com/questions/110674/gcc-optimization-flags-for-intel-atom](http://stackoverflow.com/questions/110674/gcc-optimization-flags-for-intel-atom)

> **Andy06 said:**
> 1.If I have say the official FFv3.5 of Mozilla installed (like from method 1), then I enable a repository [ubuntu security one], will it update it? Even though the initial install was not from that repo and so in effect, doesn't "point" to it?

No. The method one does no create deb packages and does not add Firefox 3.5 to Synapitc, so it doesn't get updates through the package manager.


> **Andy06 said:**
> 
2.Now if I also have the FFv3.5 Shiretoko from universe repo installed, I will have two FFv3.5s, and two update sources (ubuntu security PPA and regular community updates for Shiretoko), won't that cause massive confusion, like the wrong update going to the wrong firefox? Or will the newer version from the combined sources always over rule the older ones and update ALL Firefoxes to that latest version.

The only Firefox 3.5 version (Shiretoko) that is updated by the *universe* repository, by the *proposed* repository, by the *ubuntu-mozilla-security* and the *ubuntu-mozilla-daily* is firefox-3.5 package. They all update the same Firefox. Versions installed through methods #1 and #2 are not updated. So, the repo with newer version should have priority.

> **Andy06 said:**
> Sorry, I know it sounds very hypothetical but a lot of people I am trying to help have multiple Firefoxes (some have upto 4-5 of them: Mozilla tar.gz, Mozilla official installed like from method #1, Shiretoko 3.5 from universe repos, ubuntuzilla FF, some have daily builds plus everybody has the FFv3.0 and then the truly adventurous mess it all up by throwing swiftfox in it too hehe)

That can be a mess ([see this thread](http://ubuntuforums.org/showthread.php?t=1197505)). Better to remove all of them and reinstall only one.

> **Andy06 said:**
> I think I should add this question as well since it will make things a lot clearer for our context.

If I manually install program A and THEN add the repositories for A, does A still get updated despite not being initially installed from the repos? [In this case A being a particular Firefox]. I'm guessing probably yes since for lots of programs like Cairo, Wine, Gnome Do, Opera etc, once you add the third party repos, they start querying them as well and downloading the latest updates from there. In case of Firefox, the whole situation is a mess, so I am not so sure about Firefox.

If you manually install it with a method like #1 and #2, then no. If you install it using a deb file, then yes.

---

### Post by -=hazard=- on 2009-07-11
Great thread. The flash thing helped me a lot.

---

### Post by lovinglinux on 2009-07-11
> **-=hazard=- said:**
> Great thread. The flash thing helped me a lot.

> **-=hazard=- said:**
> Allready reported --> [http://bugs.adobe.com/jira/browse/FP-1692](http://bugs.adobe.com/jira/browse/FP-1692)

I hope they fix this.

Thanks. I have included the link to the bug report on the tutorial.

---

### Post by WongFuChu on 2009-07-11
Hey, the make -f client.mk profiledbuild part took +6 hours....

However, when I try to continue and type make... it said:
```
make: *** No targets specified and no makefile found.  Stop.
```
Does that mean it didn't work?

My mozconfig:```

    . $topsrcdir/browser/config/mozconfig
export MOZILLA_OFFICIAL=1
export BUILD_OFFICIAL=1
mk_add_options MOZILLA_OFFICIAL=1
mk_add_options BUILD_OFFICIAL=1
mk_add_options PROFILE_GEN_SCRIPT='$(PYTHON) $(MOZ_OBJDIR)/_profile/pgo/profileserver.py'
mk_add_options MOZ_OBJDIR=@TOPSRCDIR@/obj-@CONFIG_GUESS@
ac_add_options --enable-official-branding
    export CHOST="i686-pc-linux-gnu"
    export CFLAGS="-O2 -march=prescott -pipe -fomit-frame-pointer"
    export CXXFLAGS="-O2 -march=prescott -pipe -fomit-frame-pointer"
    export CPPFLAGS="-O2 -march=prescott -pipe -fomit-frame-pointer"

ac_add_options --enable-application=browser
mk_add_options MOZ_CO_PROJECT=browser
ac_add_options --enable-optimize 
ac_add_options --enable-profile-guided-optimization
ac_add_options --enable-default-toolkit=cairo-gtk2
ac_add_options --enable-xft
ac_add_options --enable-extensions=default
ac_add_options --enable-strip
ac_add_options --enable-install-strip
ac_add_options --enable-pango
ac_add_options --enable-svg
ac_add_options --enable-canvas
ac_add_options --disable-tests
ac_add_options --disable-accessibility
ac_add_options --disable-mochitest
ac_add_options --disable-debug
ac_add_options --disable-installer
ac_add_options --disable-crashreporter
ac_add_options --disable-parental-controls
ac_add_options --with-pthreads
```

I was following this for the Cflags since I didn't know what to put for my intel atom N280 (I know it doesn't point out N270, but some thread I found through google said it was okay to use):
[http://en.gentoo-wiki.com/wiki/Safe_Cflags/Intel](http://en.gentoo-wiki.com/wiki/Safe_Cflags/Intel)

Do I have to start ALL OVER *AGAIN? *Not trying to be rude because it's caps, but this took FOREVER!

---

### Post by lovinglinux on 2009-07-11
> **WongFuChu said:**
> Hey, the make -f client.mk profiledbuild part took +6 hours....

However, when I try to continue and type make... it said:
```
make: *** No targets specified and no makefile found.  Stop.
```
Does that mean it didn't work?

Sorry. My fault. I have updated the mozconfig and forgot to update the make command section accordingly:

To install it, you need to *cd* into the obj directory, which is something like this:

```
cd ~/mozilla-[color=#FF0000]**x.y.z**[/color]/obj-**[COLOR="Red"]i686-pc-linux-gnu[/COLOR]**
```

*The path in red varies.*

Then simply run the following commands:

```

make
sudo checkinstall
```


> **WongFuChu said:**
> 
I was following this for the Cflags since I didn't know what to put for my intel atom N280 (I know it doesn't point out N270, but some thread I found through google said it was okay to use):
[http://en.gentoo-wiki.com/wiki/Safe_Cflags/Intel](http://en.gentoo-wiki.com/wiki/Safe_Cflags/Intel)!

It seems it will work. I will add that page to the tutorial, since it might help others.

> **WongFuChu said:**
> Do I have to start ALL OVER *AGAIN? *Not trying to be rude because it's caps, but this took FOREVER!

Yep, 6 hours is a lot of time :)

Just cd into the obj directory like explained above and repeat the make and checinstall commands. It won't take much time to complete (less than a minute).

---

### Post by lovinglinux on 2009-07-11
A moderator has moved this thread to the tutorial section. Thank you.

---

### Post by WongFuChu on 2009-07-11
Well, after installing some extensions and restarting, I noticed a remarkable speed up! I'm not good with numbers, but it's noticeable nonetheless.

---

### Post by lovinglinux on 2009-07-11
> **WongFuChu said:**
> Well, after installing some extensions and restarting, I noticed a remarkable speed up! I'm not good with numbers, but it's noticeable nonetheless.

Great news. Test it with [Peacekeeper](http://service.futuremark.com/peacekeeper/index.action) then compare with the one from the repositories ;)

---

### Post by mag1 on 2009-07-12
Is the Shiretoko version easiest and best for the average user?  If the updates are likely to appear within a week or so of their release that seems fine to me, i can't say im bothered about the name and icon being different. :p

---

### Post by lovinglinux on 2009-07-12
> **mag1 said:**
> Is the Shiretoko version easiest and best for the average user?  If the updates are likely to appear within a week or so of their release that seems fine to me, i can't say im bothered about the name and icon being different. :p

Yes it is. Just run the command to install and launch it through "Applications >> Internet >> Shiretoko Web Browser"

---

### Post by Andy06 on 2009-07-12
To everyone, try and avoid the Shiretoko version available from the repos.

See here:
[http://ubuntuforums.org/showthread.php?t=1211495](http://ubuntuforums.org/showthread.php?t=1211495)

Lovinglinux, 
Pls see the thread link I posted above, would love to hear your thoughts on it, you seem real knowledgeable with FF on Ubuntu.:D

I started that separate thread because it deals with a slightly different problem and will be more visible that way.

Thanks a lot

---

### Post by Andy06 on 2009-07-13
Another similar thread but with different methods and approach:
[http://ubuntuforums.org/showthread.php?t=1120475](http://ubuntuforums.org/showthread.php?t=1120475)

---

### Post by lovinglinux on 2009-07-13
> **Andy06 said:**
> Another similar thread but with different methods and approach:
[http://ubuntuforums.org/showthread.php?t=1120475](http://ubuntuforums.org/showthread.php?t=1120475)

I knew that tutorial. It is interesting. I'm glad that you posted the link, because I have forgotten about it. As soon as I have time, I will read the entire thread and eventually include the link to it on my tutorial.

---

### Post by Andy06 on 2009-07-13
Lovinglinux,

I tested the FFv3.5 installable from the repos (Shiretoko) against the tar.gz available from Mozilla and made a thread about it here:
[http://ubuntuforums.org/showthread.php?t=1211495](http://ubuntuforums.org/showthread.php?t=1211495)

Your input would be extremely helpful. I'm finding the Ubuntu builds to be sub par, and this was the case with v3.0 as well.

---

### Post by lovinglinux on 2009-07-13
> **Andy06 said:**
> Lovinglinux,

I tested the FFv3.5 installable from the repos (Shiretoko) against the tar.gz available from Mozilla and made a thread about it here:
[http://ubuntuforums.org/showthread.php?t=1211495](http://ubuntuforums.org/showthread.php?t=1211495)

Your input would be extremely helpful. I'm finding the Ubuntu builds to be sub par, and this was the case with v3.0 as well.

I will reply there as soon as I can.

I'm working on a script inspired by the tutorial that puts the profile in RAM. It will be totally automatic, will allow working with multiple profiles and to put the profile in RAM on-demand, which means will not be permanently like the tutorial you mentioned. You will be able to use the profiles as you usually do or to put them in the RAM before starting Firefox.

So far so good. The performance is really better. I can even watch Flash videos on crappy sites without stuttering.

---

### Post by lovinglinux on 2009-07-13
I have created a script to easily load Firefox profiles into RAM. Please test it and tell me what you think. It was inspired by the tutorial [Howto; Firefox profile in RAM for increased speed and stability](http://ubuntuforums.org/showthread.php?t=1120475) (see discussion above).

The script is in the new section "Running Profiles from RAM".

---

### Post by twright on 2009-07-13
The first method for installing stock versions using dpkg-diverge can be done more simply by just creating a symlink to the new version of firefox's binary in /usr/local/bin. This is the best way to do it as it does not mess up the existing version and it is "the right way to do it" in terms of the unixy system hierarchy. Any binary in /usr/local/bin will be run instead of ones in /usr/bin and if it is removed then it will fall back to the Ubuntu version automatically.
```

ln -s /opt/firefox/firefox /usr/local/bin/firefox

```

---

### Post by lovinglinux on 2009-07-13
> **twright said:**
> The first method for installing stock versions using dpkg-diverge can be done more simply by just creating a symlink to the new version of firefox's binary in /usr/local/bin. This is the best way to do it as it does not mess up the existing version and it is "the right way to do it" in terms of the unixy system hierarchy. Any binary in /usr/local/bin will be run instead of ones in /usr/bin and if it is removed then it will fall back to the Ubuntu version automatically.
```

ln -s /opt/firefox/firefox /usr/local/bin/firefox

```

It makes sense, since is the place where a compiled version puts the symlink. Thanks for the tip. I'm updating the tutorial.

---

### Post by lovinglinux on 2009-07-14
I have updated the scripts from section "Running Profiles from RAM". The process of mounting and unmounting the profile are now separated to avoid errors and the unmounting script deals with common issues caused by system crashes or by rebooting without unmounting the profile.

---

### Post by beamo on 2009-07-14
I am trying to compile firefox for my machine. I have a AMD Phenom II X4 920 2.8GHz Socket AM2+ 125W Quad-Core Processor Model HDX920XCGIBOX.

I am getting this error:

checking whether the C compiler (gcc -O3 -march=deneb -pipe -fomit-frame-pointer ) works... no
configure: error: installation or configuration problem: C compiler cannot create executables.


Anyone have any idea what I am doing wrong? I am using an AM2+ chip on an AM2 board and when I check the processor I get this:

tim@tim-desktop:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 4
model name	: AMD Processor model unknown
stepping	: 2
cpu MHz		: 2812.735
cache size	: 512 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 4
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
bogomips	: 5625.46
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate


Any hints are much appreciated.

---

### Post by lovinglinux on 2009-07-14
> **beamo said:**
> I am trying to compile firefox for my machine. I have a AMD Phenom II X4 920 2.8GHz Socket AM2+ 125W Quad-Core Processor Model HDX920XCGIBOX.

I am getting this error:

checking whether the C compiler (gcc -O3 -march=deneb -pipe -fomit-frame-pointer ) works... no
configure: error: installation or configuration problem: C compiler cannot create executables.

Did you install the dependencies?

```
sudo apt-get install build-essential checkinstall
sudo apt-get build-dep firefox
sudo apt-get install mercurial libasound2-dev libcurl4-openssl-dev libnotify-dev
```

---

### Post by beamo on 2009-07-14
Yes, I did. I'm thinking there is some problem with the fact that my cpu doesn't seem to be recognized. I have my old Athlon X2 and I may pop it back in and see if that changes anything. 

Thanks for the suggestion. 

In case it matters, here is the full output:

tim@tim-desktop:~/mozilla-1.9.1$ make -f client.mk build
Adding client.mk options from /home/tim/mozilla-1.9.1/.mozconfig:
    MOZILLA_OFFICIAL=1
    BUILD_OFFICIAL=1
    PROFILE_GEN_SCRIPT=$(PYTHON) $(MOZ_OBJDIR)/_profile/pgo/profileserver.py
    MOZ_OBJDIR=$(TOPSRCDIR)/obj-$(CONFIG_GUESS)
    MOZ_CO_PROJECT=browser
make[1]: Entering directory `/home/tim/mozilla-1.9.1'
cd /home/tim/mozilla-1.9.1/obj-x86_64-unknown-linux-gnu
/home/tim/mozilla-1.9.1/configure
Adding configure options from /home/tim/mozilla-1.9.1/.mozconfig:
  --enable-application=browser
  --enable-official-branding
  --enable-application=browser
  --enable-optimize
  --enable-profile-guided-optimization
  --enable-default-toolkit=cairo-gtk2
  --enable-xft
  --enable-extensions=default
  --enable-strip
  --enable-install-strip
  --enable-pango
  --enable-svg
  --enable-canvas
  --disable-tests
  --disable-accessibility
  --disable-mochitest
  --disable-debug
  --disable-installer
  --disable-crashreporter
  --disable-parental-controls
  --with-pthreads
loading cache ./config.cache
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking build system type... x86_64-unknown-linux-gnu
checking for gawk... gawk
checking for gcc... gcc
checking whether the C compiler (gcc -O3 -march=deneb -pipe -fomit-frame-pointer ) works... no
configure: error: installation or configuration problem: C compiler cannot create executables.
*** Fix above errors and then restart with               "make -f client.mk build"
make[1]: *** [configure] Error 1
make[1]: Leaving directory `/home/tim/mozilla-1.9.1'
make: *** [/home/tim/mozilla-1.9.1/obj-x86_64-unknown-linux-gnu/Makefile] Error 2
tim@tim-desktop:~/mozilla-1.9.1$

---

### Post by markbuntu on 2009-07-14
Great tutorial but there is oen thing that is really bugging me. I have 2 monitors and flash always plays full screen on the wrong one. Is there any way to change this?
I could not find anything about fixing this anywhere.

---

### Post by lovinglinux on 2009-07-14
> **markbuntu said:**
> Great tutorial but there is oen thing that is really bugging me. I have 2 monitors and flash always plays full screen on the wrong one. Is there any way to change this?
I could not find anything about fixing this anywhere.

I know nothing about dual monitors, but I will do some research.

---

### Post by beamo on 2009-07-14
Well, I got it to compile. I had a wrong value:

-march=deneb had to read -march=athlon64

I just hope that is correct.

---

### Post by lovinglinux on 2009-07-14
> **beamo said:**
> Well, I got it to compile. I had a wrong value:

-march=deneb had to read -march=athlon64

I just hope that is correct.

How does it perform? Have you tested it?

---

### Post by beamo on 2009-07-15
I spoke to soon. There was a compiling error after about twenty minutes. I got past it though and am trying to compile it again. I really want to get it to work.

---

### Post by beamo on 2009-07-15
It just crashed again. Here is the latest error:

make[4]: *** [mozilla-xremote-client] Error 1
make[4]: Leaving directory `/home/tim/mozilla-1.9.1/obj-x86_64-unknown-linux-gnu/widget/src/xremoteclient'
make[3]: *** [libs_tier_toolkit] Error 2
make[3]: Leaving directory `/home/tim/mozilla-1.9.1/obj-x86_64-unknown-linux-gnu'
make[2]: *** [tier_toolkit] Error 2
make[2]: Leaving directory `/home/tim/mozilla-1.9.1/obj-x86_64-unknown-linux-gnu'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/tim/mozilla-1.9.1/obj-x86_64-unknown-linux-gnu'
make: *** [build] Error 2


Any ideas?

---

### Post by lovinglinux on 2009-07-15
> **beamo said:**
> It just crashed again. Here is the latest error:

make[4]: *** [mozilla-xremote-client] Error 1
make[4]: Leaving directory `/home/tim/mozilla-1.9.1/obj-x86_64-unknown-linux-gnu/widget/src/xremoteclient'
make[3]: *** [libs_tier_toolkit] Error 2
make[3]: Leaving directory `/home/tim/mozilla-1.9.1/obj-x86_64-unknown-linux-gnu'
make[2]: *** [tier_toolkit] Error 2
make[2]: Leaving directory `/home/tim/mozilla-1.9.1/obj-x86_64-unknown-linux-gnu'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/tim/mozilla-1.9.1/obj-x86_64-unknown-linux-gnu'
make: *** [build] Error 2


Any ideas?

Backup your mozconfig file, then delete mozilla-1.9.1 and start over. I had some errors too when trying to compile for the second time. I don't recall which errors I had, but when I deleted everything and started over it worked. Also try using -O2 instead of -O3.

---

### Post by beamo on 2009-07-15
I already switched to -O2 and removed all files and started from scratch. It did get me past some errors.

I'm running Intrepid and may upgrade to Jaunty though I'm worried I'll have problems. When I installed Jaunty the first time I used ext4 filesystem and it wound up flaking out on me. I think I'll stick with ext3 if I do however I'd prefer to do a clean install but don't want to go through the hassle of setting everything up again. 

The one thing that bothers me is I can't use firefox 3.5. Everytime I do my internet connection dies. So, probably I will do a fresh install of Jaunty and start over. Unless somebody has another idea.

---

### Post by lovinglinux on 2009-07-15
> **beamo said:**
> The one thing that bothers me is I can't use firefox 3.5. Everytime I do my internet connection dies. So, probably I will do a fresh install of Jaunty and start over. Unless somebody has another idea.

What do you mean by "my internet connection dies"? You loose all connectivity or just Firefox can't open pages? If it is just Firefox, then disable ipv6 in Firefox preferences. See **Solution** [*[COLOR="Red"]**FOT005**[/COLOR]*] from the Troubleshooting section for instructions.

---

### Post by beamo on 2009-07-15
Thanks, I will try that now. 

It is firefox that stops connecting but the problem affects Opera Chrome and firefox 3.0 for a few minutes afterwards.

---

### Post by beamo on 2009-07-15
I did a fresh install of Jaunty and it compiled on the first try no problems. However, when I ran checkinstall I got this error:

dpkg-deb - error: (upstream) version (`gnu') doesn't contain any digits
dpkg-deb: 1 errors in control file
/var/tmp/tmp.FbBLTAQIvR/dpkgbuild.log (END)

What now?

---

### Post by beamo on 2009-07-15
I used make install instead and it was fine. Scored 1682 on peacekeeper. There was a problem, though.I didn't include the profile build options in the .mozconfig and that is the method I used. I'm uninstalling and redoing it.

My old firefox 3.0 on Intrepid scored 1080.

---

### Post by lovinglinux on 2009-07-15
> **beamo said:**
> I used make install instead and it was fine. Scored 1682 on peacekeeper. There was a problem, though.I didn't include the profile build options in the .mozconfig and that is the method I used. I'm uninstalling and redoing it.

My old firefox 3.0 on Intrepid scored 1080.

Have you tested the official Firefox 3.5?

---

### Post by hanbin973 on 2009-07-16
I wanna upload a PGO firefox to ppa. 
But the problem was, debian/rules read .mozconfig?

Do you know how to do this?

---

### Post by lovinglinux on 2009-07-16
> **hanbin973 said:**
> I wanna upload a PGO firefox to ppa. 
But the problem was, debian/rules read .mozconfig?

Do you know how to do this?

I have no idea how to do that. Besides, it might be illegal, unless you don't use the --enable-official-branding. I couldn't find any Firefox deb anywhere. So you might want to check the license conditions first. Maybe other users are not uploading debs because of this.

---

### Post by hanbin973 on 2009-07-16
Then anyone can enable the official branding thing.

Right now, I tested by running fakeroot debian/rules binary ,

But the result was just ' firefox '.

hmmm....

Checkinstall might work?? hmm. ]

But the firefox in the ppa and the official repository depend on xulrunner. Thats the main problem!

Xulrunner is a engine, so no change in the Xulrunner, then nothing gets better.

But I think I will have problems with plugins and stuff. ( I need to do everything by my hand so it takes to much to enable and install the plugins to it. The firefox's in the ppa or etc automaticlly syncronize the original profile and every thing. ) 

whatever.. I will try more times and write the result here.
If firefox is build in the way you thought, then it is xulrunner independent?

---

### Post by beamo on 2009-07-16
> Have you tested the official Firefox 3.5?

I did and it scored slightly higher than the version I compiled. I just tried to compile with profile build and am getting this error:

OBJDIR=/home/tim/mozilla-1.9.1/obj-x86_64-unknown-linux-gnu python /home/tim/mozilla-1.9.1/obj-x86_64-unknown-linux-gnu/_profile/pgo/profileserver.py
INFO | (automation.py) | Application pid: 9726
TEST-UNEXPECTED-FAIL | (automation.py) | Exited with code -11 during test run
INFO | (automation.py) | Application ran for: 0:00:00.014902
make: *** [profiledbuild] Error 245

I'm going to keep trying later today. I think your tutorial is OUTSTANDING, by the way.
Thanks.

---

### Post by lovinglinux on 2009-07-16
> **hanbin973 said:**
> But the firefox in the ppa and the official repository depend on xulrunner. Thats the main problem!

Xulrunner is a engine, so no change in the Xulrunner, then nothing gets better.

But I think I will have problems with plugins and stuff. ( I need to do everything by my hand so it takes to much to enable and install the plugins to it. The firefox's in the ppa or etc automaticlly syncronize the original profile and every thing. ) 

whatever.. I will try more times and write the result here.
If firefox is build in the way you thought, then it is xulrunner independent?

I believe it compiles xulrunner together with Firefox 3.5, because xulrunner-1.9.1 is not installed on my system, although Firefox 3.5 shows it in the about page.



> **beamo said:**
> I'm going to keep trying later today.

Good luck.

> **beamo said:**
> I think your tutorial is OUTSTANDING, by the way.
Thanks.

Thank you very much.

---

### Post by running_rabbit07 on 2009-07-17
I just tried to install FF3.5 the way you have shown above on my 8.04 machine and now I have no firefox at all, I tried using Synaptic Package Manager to reinstall  3.0 and it didn't work. I tried the command below it and it said the file wasn't there to remove.

I am using the LiveCD right now. I also restarted the PC to see if that would help. Now I have no tool bars. All I have is the desktop photo and the one file that was on the desktop.

These are the commands I ran,
cp -R ~/.mozilla ~/.mozilla.backup
sudo tar -jxvf firefox-*.tar.bz2 -C /opt
rm firefox-*.tar.bz2
sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup
sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins
sudo ln -s /opt/firefox/firefox /usr/local/bin/firefoxand this is the one I just tried to use to fix,

sudo rm /usr/local/bin/firefox && sudo rm -r /opt/firefox



Can anyone help me get back up and running without having to reformat?

Thanx.

---

### Post by lovinglinux on 2009-07-17
> **running_rabbit07 said:**
> I just tried to install FF3.5 the way you have shown above on my 8.04 machine and now I have no firefox at all, I tried using Synaptic Package Manager to reinstall  3.0 and it didn't work. I tried the command below it and it said the file wasn't there to remove.

I am using the LiveCD right now. I also restarted the PC to see if that would help. Now I have no tool bars. All I have is the desktop photo and the one file that was on the desktop.

These are the commands I ran,
cp -R ~/.mozilla ~/.mozilla.backup
sudo tar -jxvf firefox-*.tar.bz2 -C /opt
rm firefox-*.tar.bz2
sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup
sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins
sudo ln -s /opt/firefox/firefox /usr/local/bin/firefoxand this is the one I just tried to use to fix,

sudo rm /usr/local/bin/firefox && sudo rm -r /opt/firefox



Can anyone help me get back up and running without having to reformat?

Thanx.

Did you download and save the file **firefox-3.5.tar.bz2** in your home directory before running those commands?

Did you get any errors while running those commands?

Did you remove Firefox 3.0 before installing Firefox 3.5? You shouldn't remove it. What happened when you tried to reinstall Firefox 3.0?

Please post the output of these commands:

```
ls /opt/
```

```
ls /usr/local/bin/
```

```
whereis firefox-3.5
```

```
whereis firefox
```

To fix the toolbar issue, try this:

```
killall gnome-panel
```

---

### Post by running_rabbit07 on 2009-07-17
> **lovinglinux said:**
> Did you download and save the file **firefox-3.5.tar.bz2** in your home directory before running those commands?

Yes, It was in my home folder.

> **lovinglinux said:**
> Did you get any errors while running those commands

No, didn't see any.

> **lovinglinux said:**
> Did you remove Firefox 3.0 before installing Firefox 3.5?

No. I only did the commands you had for installing.

 > **lovinglinux said:**
> You shouldn't remove it. What happened when you tried to reinstall Firefox 3.0?

It said the instal was okay, but when I clicked on the FF shortcut I got the timer/pointer then nothing happened. Then when I started to reboot the colors of the Ubuntu shutdown splash were all distorted, then at restart, there were no toolbars. 

I am going to restart now with the LiveCD and run those codes. 

Thank you for helping me.

---

### Post by running_rabbit07 on 2009-07-17
ubuntu@ubuntu:~$ ls /opt/
ubuntu@ubuntu:~$ sudo ls /opt/
ubuntu@ubuntu:~$ killall gnome-panel
ubuntu@ubuntu:~$ ls /usr/local/bin/
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ whereis firefox-3.5
firefox-3: /usr/bin/firefox-3.0 /etc/firefox-3.0
ubuntu@ubuntu:~$ whereis firefox
firefox: /usr/bin/firefox /usr/lib/firefox /usr/lib64/firefox /usr/share/firefox
ubuntu@ubuntu:~$ 


This isn't showing much, do these commands work while in LiveCD? 

Or, Do I need to try to get a terminal via a keyboard command?

---

### Post by lovinglinux on 2009-07-17
> **running_rabbit07 said:**
> Or, Do I need to try to get a terminal via a keyboard command?

I'm afraid so.

Login without the LiveCD, the hit ALT+F2 the run *gnome-terminal* to launch the terminal

---

### Post by running_rabbit07 on 2009-07-17
Here is what I got while inputting via restore mode CLI

```
ls /opt/
```

firefox

```
ls /usr/local/bin/
```

firefox

```
whereis firefox-3.5
```

firefox-3: /usr/bin/firefox-3.0 /etc/firefox-3.0

```
whereis firefox
```

firefox: /usr/bin/firefox /usr/lib/firefox /usr/lib64/firefox /usr/local/bin/firefox /usr/share/firefox


To fix the toolbar issue, try this:

```
killall gnome-panel
```
gnome-panel: no process killed

Thanx again for the help.

---

### Post by running_rabbit07 on 2009-07-17
> **lovinglinux said:**
> I'm afraid so.

Login without the LiveCD, the hit ALT+F2 the run *gnome-terminal* to launch the terminal

I'll give it a try.

Tried it, ALT F2 didn't do anything.

---

### Post by lovinglinux on 2009-07-17
> **running_rabbit07 said:**
> Here is what I got while inputting via restore mode CLI

```
ls /opt/
```

firefox

```
ls /usr/local/bin/
```

firefox

```
whereis firefox-3.5
```

firefox-3: /usr/bin/firefox-3.0 /etc/firefox-3.0

```
whereis firefox
```

firefox: /usr/bin/firefox /usr/lib/firefox /usr/lib64/firefox /usr/local/bin/firefox /usr/share/firefox


To fix the toolbar issue, try this:

```
killall gnome-panel
```
gnome-panel: no process killed

Thanx again for the help.

Login again, but not in recovery mode. Then click ALT+F2 to bring the bring the "Run Application" dialog and run the command gnome-terminal to launch the terminal. If it doesn't show, try ALT+F1 to see if the menu appears and then go to "Applications >> Acessories >> Terminal".

Once in the terminal, run these:

```
gnome-session-remove gnome-panel
```

```
gconftool-2 --recursive-unset /apps/panel
```

```
pkill gnome-panel
```

This should reset your panels (toolbar).

Then run this to remove Firefox 3.5

```
sudo rm /usr/local/bin/firefox && sudo rm -r /opt/firefox
```

Then launch Firefox.

---

### Post by running_rabbit07 on 2009-07-17
> **running_rabbit07 said:**
> I'll give it a try.

Tried it, ALT F2 didn't do anything.

I got a terminal open but have the same results, no toolbars.

I managed to find the command to open the home folder and from there found the applications folder and found a shortcut for terminal.

If have to reinstall Ubuntu I will. Being I have a /home, will the reinstall over right all the apps I have installed? I prefer not to but, if it is what I have to do then I will.

---

### Post by lovinglinux on 2009-07-17
> **running_rabbit07 said:**
> I got a terminal open but have the same results, no toolbars.

I managed to find the command to open the home folder and from there found the applications folder and found a shortcut for terminal.

If have to reinstall Ubuntu I will. Being I have a /home, will the reinstall over right all the apps I have installed? I prefer not to but, if it is what I have to do then I will.

Have you seen the post above?

---

### Post by running_rabbit07 on 2009-07-17
> **lovinglinux said:**
> Login again, but not in recovery mode. Then click ALT+F2 to bring the bring the "Run Application" dialog and run the command gnome-terminal to launch the terminal. If it doesn't show, try ALT+F1 to see if the menu appears and then go to "Applications >> Acessories >> Terminal".

Once in the terminal, run these:

```
gnome-session-remove gnome-panel
``````
gconftool-2 --recursive-unset /apps/panel
``````
pkill gnome-panel
```This should reset your panels (toolbar).

Then run this to remove Firefox 3.5

```
sudo rm /usr/local/bin/firefox && sudo rm -r /opt/firefox
```Then launch Firefox.

Will do.

---

### Post by running_rabbit07 on 2009-07-17
> **running_rabbit07 said:**
> Will do.

Can't get any key commands to work to open any windows or terminals. I gotta take a break from this thing.

Thank you for the help. Hopefully I'll get it back on track later tonight or in the morning. Again, Thank you!

---

### Post by running_rabbit07 on 2009-07-18
> **running_rabbit07 said:**
> Can't get any key commands to work to open any windows or terminals. I gotta take a break from this thing.

Thank you for the help. Hopefully I'll get it back on track later tonight or in the morning. Again, Thank you!

Giggidy, I reinstalled Ubuntu. I set it to do it's thing while I went and cooled off. All my settings were OK, being I had the /home partition. When I booted earlier, I couldn't get anything to work. I did find that the firefox3.5 was in the trash some how. I plan to reread your directions to make sure I don't miss anything this time.

Thanks again for your help.

---

### Post by forestwalkerjoe on 2009-07-18
Hey, since you were so helpful with my install and stream lining of my FF install.. i am in hopes that you can help solve what MAYBE another FF issue.
It was suggested that this MIGHT be related to the upgrade to 3.5 but i have no way to know that other than.. this issue started right after i did the new FF install. 
here is my post..
```
http://ubuntuforums.org/showthread.php?t=1216647
```
 and i hope you can help me figure out.. what they heck is going on here? 


FWJ

---

### Post by ssulaco on 2009-07-18
> **lovinglinux said:**
> 
[color=#CC0000][SIZE="4"]Removing Conflicting Plugins[/SIZE][/color]

Ubuntu comes with swfdec plug-in, but it doesn't work on several sites. Installing the version from Adobe might solve this problem and improve performance. 

To remove other flash plug-ins and install only the one from Adobe open "Applications >> Accessories >> Terminal", then paste (CTRL+SHIFT+V) the code below in the terminal window and hit enter:

```
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
```


[color=#CC0000][SIZE="4"]Flash Tweaks[/SIZE][/color]

Some people [reported](http://ubuntuforums.org/showpost.php?p=7279173&postcount=14) improvements doing this ([original source](http://blogs.adobe.com/penguin.swf/2008/08/secrets_of_the_mmscfg_file_1.html)):

```
sudo mkdir /etc/adobe
*echo* "*OverrideGPUValidation*=true" >~/mms.cfg
sudo mv ~/mms.cfg /etc/adobe/
```



followed your procedure here,utube & hulu work great so far....Great guide(tutorial).......Thankyou.

---

### Post by lovinglinux on 2009-07-18
> **ssulaco said:**
> followed your procedure here,utube & hulu work great so far....Great guide(tutorial).......Thankyou.

You are welcome. Thanks for the feedback.

---

### Post by zika on 2009-07-19
> ```
sudo mkdir /etc/adobe
echo "OverrideGPUValidation=true" >~/mms.cfg
sudo mv ~/mms.cfg /etc/adobe/ 
```should be, for security reasons, replaced with:
```
echo "OverrideGPUValidation=true" >~/.adobe/mms.cfg
```It works this way and system integrity is preserved ...

---

### Post by lovinglinux on 2009-07-19
**[COLOR="Red"]Warning:[/COLOR]** If you are using the method of running Firefox profile from RAM, I suggest you revisit the corresponding section because I have changed the *ramprofile.sh* script. The previous code would make a backup of fstab and current profile as a tar archive inside ~/.mozilla/firefox , every time you run it and also would delete old backups. Nevertheless, due to some error I couldn't reproduce, I have lost the entire content of ~/.mozilla/firefox when unloading the profile from RAM. So now, the script will create a backup of your entire  ~/.mozilla/firefox folder in your HOME directory and will not delete the old ones. You need to delete them manually if you want to preserve space. This way you can easily restore any profiles if such an error occur to you.

---

### Post by dcstar on 2009-07-19
> **lovinglinux said:**
> 
........
**Symptoms:**

[list][*] **Some images are displayed with weird colors**[/list]
**Solution** [*FOT007*]**:**

This is due to color management feature, which allows to correct image colors based on embedded color profiles. You could disable color management, but the best way is to enable color management for tagged graphics only, which means all images will display correctly, even if they don't have color profiles.

   1. Type *about:config* in the address bar, press Enter.
   2. Find ***gfx.color_management.mode*** in the list.
   3. Right-click -> Modify.
   4. Set the value to 2. 

.......


After seeing too many pics displayed in weird colours in 3.5, setting this to 0 (off) seems to fix it - it was already set to 2.

---

### Post by lovinglinux on 2009-07-19
> **dcstar said:**
> After seeing too many pics displayed in weird colours in 3.5, setting this to 0 (off) seems to fix it - it was already set to 2.

I have it set to 2 and I don't have issues, but you are not the first one to report similar behavior. I guess this could be due to differences in firefox preferences between 3.0 and 3.5. Nevertheless, setting it to 0 will definitely solve any problems. I will update the tutorial accordingly. Thanks.

---

### Post by Andy06 on 2009-07-25
Wow you've really tuned up the first post a bit within 2 weeks :)

I was also playing around with ng.layout paint setting and I have about a dozen friends convinced there Fx3.5 is now much snappier just coz I changed the setting.:mrgreen:
Whats really funny is if you change the nglayout value EITHER way (ie decrease or increase it from the default of 250ms), people will think its faster especially if they are on broadband connections. 
If you shift it down to something like 10, Fx will display something immediately on screen n people will be like oh its faster!
If you shift it up to something like 1000, Fx will display everything almost all at once, creating a woah! all-done-at-once-Apple-Safari type effect. Again people perceive it as faster.

I tried throwing Swiftfox their way though (to avoid perception biases that I might be inducing) and none of them felt any difference whatsoever. [using stopwatches mainly, hardly scientific but way more useful and a better meter than utterly irrelevant pure javascript benchmarks]

I've been experimenting with browsers (like 7-8 of em) on Windows and Linux and I can't for the life of me see a noticeable difference between the stock vanilla Mozilla build and optimised builds (for my processor). You compiled your own right? In theory you should have performance even better than Swiftfox which is still sort of generic to one type of processor and not a specific machine. You mentioned that it was around 30% faster on peacekeeper. What sort of perceivable difference do you see? 

Is this a 30% decrease in page loading/rendering times? 30% better UI responsiveness? Computation? Calculation? Or is merely 30% better javascript benchmark performance?

---

### Post by lovinglinux on 2009-07-25
> **Andy06 said:**
> What sort of perceivable difference do you see? 

Is this a 30% decrease in page loading/rendering times? 30% better UI responsiveness? Computation? Calculation? Or is merely 30% better javascript benchmark performance?

The 30% improvement is a benchmark value, since I could not quantify it by simply observing the browser behaviour. Nevertheless, I have been comparing my benchmarks results with my daily experience and I'm pretty sure the gain is not artificial. The browser is more responsive, using less CPU and rendering faster. I'm not saying pages load faster, because that depends on network factors, but pages with heavy content does perform much better. Just observing the benchmark test for example you can see that animations are rendered much more smoothly and calculations are much faster.

---

### Post by KanineN on 2009-07-26
Hello! I have problem with firefox, and that is that when I surf firefox freezes and I have to shutdown the computer. It is when I press the keys quickly it freezes. 

It doesn't shutdown when I press slowly, but who want to do that? I am now typing on opera but I want all the good plugins firefox have!

I don't find anything that helps me in the throubleshooting section.

I have a 64-bits system.

---

### Post by lovinglinux on 2009-07-26
> **KanineN said:**
> Hello! I have problem with firefox, and that is that when I surf firefox freezes and I have to shutdown the computer. It is when I press the keys quickly it freezes. 

It doesn't shutdown when I press slowly, but who want to do that? I am now typing on opera but I want all the good plugins firefox have!

I don't find anything that helps me in the throubleshooting section.

I have a 64-bits system.


It freezes when you type where? In the address bar, search bar or when writing a post?

Start Firefox and wait for it to display this issue, then use the command top to determine CPU and memory usage. Post the results here.

Have you tried to use a clean profile, without extensions or bookmarks? It would help to pinpoint the culprit if we determine if it's a profile related issue or not. 

Also try **Solution** [*[COLOR="Red"]**FOT010**[/COLOR]*] from the Troubleshooting section.

---

### Post by KanineN on 2009-07-26
> **lovinglinux said:**
> It freezes when you type where? In the address bar, search bar or when writing a post?

Start Firefox and wait for it to display this issue, then use the command top to determine CPU and memory usage. Post the results here.

Have you tried to use a clean profile, without extensions or bookmarks? It would help to pinpoint the culprit if we determine if it's a profile related issue or not. 

Also try **Solution** [*[COLOR="Red"]**FOT010**[/COLOR]*] from the Troubleshooting section.

It freezes when I type in the address bar. I have tried the FOT010 but it didn't help. 

How do I do to use a clear profile without extensions and bookmarks?

EDIT: when it freezed (?) and I had to restart my computer the processor 1 was 39,4% and processor2: 36,8%

---

### Post by lovinglinux on 2009-07-26
> **KanineN said:**
> It freezes when I type in the address bar. I have tried the FOT010 but it didn't help.

Whenever you type something in the address bar, Firefox searches for possible matches in your bookmark and history database. The speed of the process can be affected by the amount of entries in the database and amount of left overs in the database entries. 

To improve this you can optimize the database, delete your browsing history or disable the awesomebar feature.

First of all, make sure you have a backup of your profiles, just in case you want to revert changes. Run this in the terminal:

```
tar cvf $HOME/firefoxprofiles-backup.tar $HOME/.mozilla/firefox
```

Then close Firefox and execute this command to optimize the database:

```
find $HOME/.mozilla/ \( -name "*.sqlite" \) -exec sqlite3  {} "vacuum" \;
```

Start Firefox and check if that helps. If not, then try deleting the browsing history and repeat the process above.

If the problem persists, then try deleting the database file. Close Firefox and run this command:

```
rm $HOME/.mozilla/firefox/**/places.sqlite
```

Restart Firefox and see if it helps.

> **KanineN said:**
> How do I do to use a clear profile without extensions and bookmarks?

Run the command below to launch the profile manager.

```
firefox -P
```

You can create, delete and start profiles from there.

---

### Post by xzero1 on 2009-07-28
The Compiz option "Unredirect Fullscreen Windows" when unchecked kills fullscreen xv video acceleration provided by my display driver when using mplayer. In my case this is the default as well as the most efficient display option. Though this might only apply to my particular computer, you may wish to provide some warnings since some of these more general optimizations can have unintended effects and would be difficult to troubleshoot. I applaud you for an excellent, needed and well thought out thread.

---

### Post by lovinglinux on 2009-07-28
> **xzero1 said:**
> The Compiz option "Unredirect Fullscreen Windows" when unchecked kills fullscreen xv video acceleration provided by my display driver when using mplayer. In my case this is the default as well as the most efficient display option. Though this might only apply to my particular computer, you may wish to provide some warnings since some of these more general optimizations can have unintended effects and would be difficult to troubleshoot. I applaud you for an excellent, needed and well thought out thread.

Thanks for the suggestion and compliments.

---

### Post by thered on 2009-07-29
I've been umming and aahing about doing this since 3.5 came out.

Took the plunge and used procedure #2 to upgrade.

all went well -thanks lovinglinux :)

---

### Post by lovinglinux on 2009-07-29
> **thered said:**
> I've been umming and aahing about doing this since 3.5 came out.

Took the plunge and used procedure #2 to upgrade.

all went well -thanks lovinglinux :)

You are welcome.

BTW, thanks to the forum staff for selecting this thread as tutorial of the week. :popcorn:

---

### Post by KanineN on 2009-07-29
Cheers mate! I havn't had a crash for a long time now! I think it was one of my plugins that f*ed it up. But now firefox won't play any flash videos except those on youtube. When I tried to watch a movie on myspace I just got a black screen.

---

### Post by lovinglinux on 2009-07-29
> **KanineN said:**
> Cheers mate! I havn't had a crash for a long time now! I think it was one of my plugins that f*ed it up. But now firefox won't play any flash videos except those on youtube. When I tried to watch a movie on myspace I just got a black screen.

Do you have AdBlock extension? If you have, try replacing it with AdBlock Plus. If you already have AdBlock Plus, then try disabling it to see if it works. If you don't have any of these, then check the flash plugin version on Firefox addons.

---

### Post by KanineN on 2009-07-29
I have Shockwave flash, VLC multimedia plugin, windows media player plugin, quicktime plugin installed.

---

### Post by lovinglinux on 2009-07-29
> **KanineN said:**
> I have Shockwave flash, VLC multimedia plugin, windows media player plugin, quicktime plugin installed.

Which Flash version? Can you post a link to a video that doesn't work?

---

### Post by KanineN on 2009-07-29
> **lovinglinux said:**
> Which Flash version? Can you post a link to a video that doesn't work?

[http://vids.myspace.com/index.cfm?fuseaction=vids.individual&VideoID=6358418](http://vids.myspace.com/index.cfm?fuseaction=vids.individual&VideoID=6358418)

Shockwave flash: 9.0 r999
VLC Multimedia Plugin: 2.26.1
Windows Media Player Plugin: 2.26.1
Quicktime Plugin: 7.20 (2.26.1)

2.26.1 is the totem.

---

### Post by lovinglinux on 2009-07-29
> **KanineN said:**
> [http://vids.myspace.com/index.cfm?fuseaction=vids.individual&VideoID=6358418](http://vids.myspace.com/index.cfm?fuseaction=vids.individual&VideoID=6358418)

Shockwave flash: 9.0 r999
VLC Multimedia Plugin: 2.26.1
Windows Media Player Plugin: 2.26.1
Quicktime Plugin: 7.20 (2.26.1)

2.26.1 is the totem.

See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section.

---

### Post by KanineN on 2009-07-30
> **lovinglinux said:**
> See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section.

thanks! It works like a charm now!

---

### Post by lovinglinux on 2009-07-30
> **KanineN said:**
> thanks! It works like a charm now!

You are welcome.

---

### Post by ssulaco on 2009-07-30
Here is a Tool I used to compare FF to Opera to IE,(when i was mainly using Windows)....Opera would usually whip FF,...IE was always last.;-)
Website is called Numion.

[http://www.numion.com/StopWatch/](http://www.numion.com/StopWatch/)

Speaking of Opera...what would be the preferred method of installation,I dont see it in Add/Remove Apps,or Synaptic Package Manager....Thanks.

---

### Post by lovinglinux on 2009-07-31
> **ssulaco said:**
> Here is a Tool I used to compare FF to Opera to IE,(when i was mainly using Windows)....Opera would usually whip FF,...IE was always last.;-)
Website is called Numion.

[http://www.numion.com/StopWatch/](http://www.numion.com/StopWatch/)

Speaking of Opera...what would be the preferred method of installation,I dont see it in Add/Remove Apps,or Synaptic Package Manager....Thanks.

Thanks for the tip.

You can get Opera deb file from [http://www.opera.com/browser/download/](http://www.opera.com/browser/download/)

You can also add the repository: 

```
deb http://deb.opera.com/opera/ stable non-free
```

---

### Post by ssulaco on 2009-07-31
I added the repository,but am getting this error,when i reload deb.opera

---

### Post by zika on 2009-07-31
> **ssulaco said:**
> I added the repository,but am getting this error,when i reload deb.opera```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 033...
```

---

### Post by lovinglinux on 2009-07-31
> **ssulaco said:**
> I added the repository,but am getting this error,when i reload deb.opera

Sorry I forgot the key. See post above. Don't forget to replace **033...** with the key number.

---

### Post by n8bounds on 2009-07-31
Nice post, thanks!

---

### Post by ssulaco on 2009-07-31
> **zika said:**
> ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 033...
```

Thank you zika....worked good.

lovinglinux....have you had much experience tweaking Opera,this thing is mighty slow....I havent optimized my FF yet,and its alot faster than Opera

---

### Post by lovinglinux on 2009-08-01
> **ssulaco said:**
> Thank you zika....worked good.

lovinglinux....have you had much experience tweaking Opera,this thing is mighty slow....I havent optimized my FF yet,and its alot faster than Opera

I've never touched Opera for more than 10 minutes :)

I can't live without Firefox extensions and customizations ;)

---

### Post by matyasfalvi on 2009-08-02
Hey!

A buddy of mine has some problems with firefox on his mac I think I can fix it however I need to get into his permissions.sqlite file which I told him to send me over. Unfortunately I am unable to open the file. gedit says: ```
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.
``` I have tried ```
chmod a+x
``` that didn't work. Then I told my buddy to copy the contents of his permissions.sqlite file to a .txt file and send it over that way. This didn't work either. I get the same error message from gedit when I try to open the file.

Any help is much appreciated!

Thanx

---

### Post by lovinglinux on 2009-08-02
> **matyasfalvi said:**
> Hey!

A buddy of mine has some problems with firefox on his mac I think I can fix it however I need to get into his permissions.sqlite file which I told him to send me over. Unfortunately I am unable to open the file. gedit says: ```
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.
``` I have tried ```
chmod a+x
``` that didn't work. Then I told my buddy to copy the contents of his permissions.sqlite file to a .txt file and send it over that way. This didn't work either. I get the same error message from gedit when I try to open the file.

Any help is much appreciated!

Thanx

You can't open it with gedit. You need a sqlite database manager to do it. You could install [SQLite Manager](https://addons.mozilla.org/en-US/firefox/addon/5817) extension for Firefox, which is great and easy to use, or use a standalone application like [sqlitebrowser](apt:sqlitebrowser) [apt-get] 

> [color=#CC0000]**Note:**[/color] when you see [apt-get] after a link on my posts it means that you just need to click it to install the software. This is basically an easy way to perform an installation from the [repositories](http://en.wikipedia.org/wiki/Software_repository)  without running the command on a terminal. This is the same as running the command *sudo apt-get install* followed by the name of the program.

---

### Post by matyasfalvi on 2009-08-02
Wow Man! You are amazing! Answer in 5 min. and it works just perfectly I can edit the .sqlite file so easily with the sqlite browser. 

Thank you very much for your time help and concern!

Take care!

---

### Post by lovinglinux on 2009-08-02
> **matyasfalvi said:**
> Wow Man! You are amazing! Answer in 5 min...

That was a coincidence. I have spent the entire day programming and came here just to do something different for a few minutes, exactly when you posted. Good timing I guess :)

> **matyasfalvi said:**
> ...and it works just perfectly I can edit the .sqlite file so easily with the sqlite browser. 

Thank you very much for your time help and concern!

Take care!

You are welcome.

---

### Post by n8bounds on 2009-08-03
The swiftfox + RAM profile thing paid off big for me. I liked it so much, I made a script for installing it on my computers!

[http://n8.thruhere.net/blog/?p=151](http://n8.thruhere.net/blog/?p=151)

Thanks, man!

---

### Post by Haruki-kun on 2009-08-03
Hi, there. I'm having trouble with Firefox and I was wondering if anyone could help me out.

About a week ago, my places.sqlite file got corrupted, and I had to resort to deleting it as Solution [FOT003] told me to. It worked fine.

However, just now, I've noticed that my bookmarks disappear every time I shut down the computer. Strangely enough, the one bookmark that hasn't disappeared at all is this thread, which I bookmarked right after I deleted the places.sqlite file. All bookmarks saved by StumbleUpon also seem to stay saved.

Where's the problem coming from? And how can I fix it?

---

### Post by jaudelo on 2009-08-03
Thank you very much for the information about conflicting flash plugins!  I finally got youtube working and google maps street view is also now working!:P

---

### Post by ArmenianLeader4 on 2009-08-03
great tutorial. Helped me alot!

---

### Post by lovinglinux on 2009-08-03
> **n8bounds said:**
> The swiftfox + RAM profile thing paid off big for me. I liked it so much, I made a script for installing it on my computers!

[http://n8.thruhere.net/blog/?p=151](http://n8.thruhere.net/blog/?p=151)

Thanks, man!

> **jaudelo said:**
> Thank you very much for the information about conflicting flash plugins!  I finally got youtube working and google maps street view is also now working!:P

> **ArmenianLeader4 said:**
> great tutorial. Helped me alot!


You are welcome. I'm glad to see it is helping out. 

> **Haruki-kun said:**
> Hi, there. I'm having trouble with Firefox and I was wondering if anyone could help me out.

About a week ago, my places.sqlite file got corrupted, and I had to resort to deleting it as Solution [FOT003] told me to. It worked fine.

However, just now, I've noticed that my bookmarks disappear every time I shut down the computer. Strangely enough, the one bookmark that hasn't disappeared at all is this thread, which I bookmarked right after I deleted the places.sqlite file. All bookmarks saved by StumbleUpon also seem to stay saved.

Where's the problem coming from? And how can I fix it?

Check Solution [FOT001] and try delting places.sqlite again. Also check if you have a bunch of corrupted places.sqlite in your profile folder and delete them.

---

### Post by jackson.polyps on 2009-08-03
hi , i am having trouble getting streaming video files to play on my new install of ubuntu 9.04 it doesnt ask for any plug ins to install and i cant quite figure out how to install flash plugin it keeps giving me errors. can anyone help me or send me a link to a tutorial? 

                                                                                        thanks jackson.polyps

---

### Post by lovinglinux on 2009-08-04
> **jackson.polyps said:**
> hi , i am having trouble getting streaming video files to play on my new install of ubuntu 9.04 it doesnt ask for any plug ins to install and i cant quite figure out how to install flash plugin it keeps giving me errors. can anyone help me or send me a link to a tutorial? 

                                                                                        thanks jackson.polyps

[Comprehensive Multimedia & Video Howto](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by Haruki-kun on 2009-08-05
> **lovinglinux said:**
> Check Solution [FOT001] and try delting places.sqlite again. Also check if you have a bunch of corrupted places.sqlite in your profile folder and delete them.

None of these solutions worked. I ran the solution's command in the terminal and nothing happened, I deleted places.sqlite again, and strangely enough my bookmarks didn't disappear, and I couldn't find any corrupted files.

---

### Post by lovinglinux on 2009-08-06
> **Haruki-kun said:**
> None of these solutions worked. I ran the solution's command in the terminal and nothing happened, I deleted places.sqlite again, and strangely enough my bookmarks didn't disappear, and I couldn't find any corrupted files.

Start a new profile a see if it works.

---

### Post by Haruki-kun on 2009-08-07
> **lovinglinux said:**
> Start a new profile a see if it works.

OK, this one worked. Thanks a lot! :)

---

### Post by Chuchaqui on 2009-08-08
I just had the FOT008 problem again after updating. I had to change the /usr/lib/firefox-3.5.2/firefox.sh script like the post said. Thought that little bit should be added :)

Cheers

---

### Post by FakeOutdoorsman on 2009-08-13
Nice tutorial!  Very well written and organized.

---

### Post by lovinglinux on 2009-08-14
> **FakeOutdoorsman said:**
> Nice tutorial!  Very well written and organized.

Thank you.

---

### Post by hanbin973 on 2009-08-16
I tried to make a PGO build and the error is ( What ever, I started building with Arch's PKGBUILD ) 

```
make[1]: Leaving directory `/home/hanbin973/firefox-pgo-beta/mozilla-central'
OBJDIR=/home/hanbin973/firefox-pgo-beta/mozilla-central/ff-pgo python /home/hanbin973/firefox-pgo-beta/mozilla-central/ff-pgo/_profile/pgo/profileserver.py
INFO | automation.py | Application pid: 4856
TEST-UNEXPECTED-FAIL | automation.py | Exited with code -11 during test run
INFO | automation.py | Application ran for: 0:00:00.092347
make: *** [profiledbuild] &#50724;&#47448; 245
bash: return: can only `return' from a function or sourced script

```

The korean ( &#50724;&#47448; ) vocab's meaning is "error". :)

Many people are having problem.

---

### Post by hanbin973 on 2009-08-16
> **beamo said:**
> I did and it scored slightly higher than the version I compiled. I just tried to compile with profile build and am getting this error:

OBJDIR=/home/tim/mozilla-1.9.1/obj-x86_64-unknown-linux-gnu python /home/tim/mozilla-1.9.1/obj-x86_64-unknown-linux-gnu/_profile/pgo/profileserver.py
INFO | (automation.py) | Application pid: 9726
TEST-UNEXPECTED-FAIL | (automation.py) | Exited with code -11 during test run
INFO | (automation.py) | Application ran for: 0:00:00.014902
make: *** [profiledbuild] Error 245

I'm going to keep trying later today. I think your tutorial is OUTSTANDING, by the way.
Thanks.

You have a same error with me?

---

### Post by lovinglinux on 2009-08-16
> **hanbin973 said:**
> I tried to make a PGO build and the error is ( What ever, I started building with Arch's PKGBUILD ) 

```
make[1]: Leaving directory `/home/hanbin973/firefox-pgo-beta/mozilla-central'
OBJDIR=/home/hanbin973/firefox-pgo-beta/mozilla-central/ff-pgo python /home/hanbin973/firefox-pgo-beta/mozilla-central/ff-pgo/_profile/pgo/profileserver.py
INFO | automation.py | Application pid: 4856
TEST-UNEXPECTED-FAIL | automation.py | Exited with code -11 during test run
INFO | automation.py | Application ran for: 0:00:00.092347
make: *** [profiledbuild] &#50724;&#47448; 245
bash: return: can only `return' from a function or sourced script

```

The korean ( &#50724;&#47448; ) vocab's meaning is "error". :)

Many people are having problem.

I suppose you are trying to compile version 3.6a1 right? I was unable to compile it with PGO enabled. But I did without it, after adding the following option:

```
ac_add_options --disable-necko-wifi
```

I'm currently unable to compile version 3.5.2, with or without pgo.

---

### Post by lovinglinux on 2009-08-17
> **chang_m33 said:**
> Whooooooo. This one of the best thread on our favorite Firefox.

Thank you. I'm glad you like it. I have plans to expand it, but I'm currently very busy with the the development of Firefox extensions. Developing extensions gave me a very good insight on how Firefox works and why some extensions make it slow. I will write about that when I have some time ;)

---

### Post by harry2006 on 2009-08-17
Very helpful article on optimizing FF@Ubuntu.
Thank you very much.

---

### Post by lovinglinux on 2009-08-17
> **harry2006 said:**
> Very helpful article on optimizing FF@Ubuntu.
Thank you very much.

You are welcome and thanks for your comments.

---

### Post by hanbin973 on 2009-08-23
I successfully complied a 3.5.3pre .

I made the mozconfig based on the ~ubuntu-mozilla-daily ppa and just added the options for the PGO.

Its really~~~~~ FAST!!!!

The mozconfig

```
ac_add_options --disable-debug 
ac_add_options --with-user-appdir=.mozilla 
ac_add_options --with-system-jpeg=/usr 
ac_add_options --with-system-zlib=/usr 
ac_add_options --with-system-nspr 
ac_add_options --with-system-nss
ac_add_options --disable-crashreporter 
ac_add_options --disable-composer 
ac_add_options --disable-elf-dynstr-gc 
ac_add_options --disable-gtktest 
ac_add_options --disable-install-strip 
ac_add_options --disable-installer 
ac_add_options --disable-ldap 
ac_add_options --disable-mailnews 
ac_add_options --disable-profilesharing 
ac_add_options --disable-strip 
ac_add_options --disable-strip-libs 
ac_add_options --disable-tests 
ac_add_options --disable-mochitest 
ac_add_options --disable-updater 
ac_add_options --disable-xprint
ac_add_options --enable-application=browser 
ac_add_options --enable-canvas 
ac_add_options --enable-default-toolkit=cairo-gtk2 
ac_add_options --enable-gnomevfs 
ac_add_options --enable-optimize 
ac_add_options --enable-pango 
ac_add_options --enable-postscript 
ac_add_options --enable-svg 
ac_add_options --enable-mathml 
ac_add_options --enable-xft 
ac_add_options --enable-xinerama 
ac_add_options --enable-extensions=default,-reporter 
ac_add_options --enable-safe-browsing 
ac_add_options --enable-single-profile 
ac_add_options --enable-system-myspell 
ac_add_options --with-distribution-id=com.ubuntu 

mk_add_options MOZ_CO_PROJECT=browser
mk_add_options MOZ_OBJDIR=@TOPSRCDIR@/ff-pgo
mk_add_options PROFILE_GEN_SCRIPT='$(PYTHON) $(MOZ_OBJDIR)/_profile/pgo/profileserver.py'
ac_add_options --enable-optimize
ac_add_options --enable-profile-guided-optimization
```

---

### Post by juliomeza on 2009-08-24
Thanks
Help me a lot.

---

### Post by xchecker on 2009-08-25
I installed 3.5 and changed the properties of my panel icon to run it.  Now how do I import my bookmarks, tabs, etc to the new version?  I tried FILE/IMPORT but it found nothing to import.

---

### Post by lovinglinux on 2009-08-25
> **xchecker said:**
> I installed 3.5 and changed the properties of my panel icon to run it.  Now how do I import my bookmarks, tabs, etc to the new version?  I tried FILE/IMPORT but it found nothing to import.

That depends on how you installed Firefox 3.5. Nevertheless, most methods will use the same profiles from version 3.0 or make an exact copy of them to another folder, when you first launch it. So you should have the same bookmarks, passwords, extensions and so on.

As far as I know, only Swiftweasel profiles needs to be copied manually from Firefox profiles folder.

How did you install FF 3.5?

---

### Post by xchecker on 2009-08-25
I installed from Synaptic Package Manager.

---

### Post by lovinglinux on 2009-08-25
> **xchecker said:**
> I installed from Synaptic Package Manager.

So, when you start FF 3.5 it will copy your profiles from ~/.mozilla/firefox to ~/.mozilla/firefox-3.5. Check if you have a copy of your ff 3.0 profiles there. If not, then close Firefox, delete ~/.mozilla/firefox-3.5 and start Firefox again. It will clone your profiles again.

---

### Post by KanineN on 2009-09-03
Why do I have a unbranded firefox version? I installed firefox through ubuntuzilla because I couldn't get it to work. Now it just says "A web browser 3.5". Is it possible to remove it?

EDIT: And when I try to install flash player 10 on my 64 bits system I can't get it to work, please help!

---

### Post by lovinglinux on 2009-09-03
> **KanineN said:**
> Why do I have a unbranded firefox version? I installed firefox through ubuntuzilla because I couldn't get it to work. Now it just says "A web browser 3.5". Is it possible to remove it?

I'm not sure why you have it, since Ubuntuzilla installs Firefox 3.5 branded. Check in Synaptic if the abrowser metapackages are installed and remove them.

If you want to remove Firefox 3.5 installed by Ubuntuzilla, then run this command:

```
ubuntuzilla.py -a remove -p firefox
```


> **KanineN said:**
> EDIT: And when I try to install flash player 10 on my 64 bits system I can't get it to work, please help!

Try this [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

---

### Post by KanineN on 2009-09-03
> **lovinglinux said:**
> 


Try this [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

it didn't work when I tried the guide in the post but it worked when I did as adobe said on the website that the guy was linking to. Thank you!

---

### Post by lovinglinux on 2009-09-03
> **KanineN said:**
> it didn't work when I tried the guide in the post but it worked when I did as adobe said on the website that the guy was linking to. Thank you!

You are welcome.

---

### Post by angellika on 2009-09-05
this helped me to fix my video playing in firefox. i had problems with sound. it stopped playing in some parts of streaming. it was really annoying. but now is ok. i used this 
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

so thanks guys.o0

jaro

---

### Post by ssulaco on 2009-09-05
Here is My peacekeeper scores.......Swiftfox vs Chromium (ppa)
Although it seemed Swiftfox would render pages a little faster using Numion stopwatch.

---

### Post by lovinglinux on 2009-09-05
> **ssulaco said:**
> Here is My peacekeeper scores.......Swiftfox vs Chromium (ppa)
Although it seemed Swiftfox would render pages a little faster using Numion stopwatch.

I believe you still have room for improvements on the Swiftfox side.

---

### Post by Dangger on 2009-09-11
Well I've tried almost everything. Firefox improved, not greatly though. Replacing youtube with totem or mplayer improves usability but youtube is not the only site with flash and when the video is embedded this solution doesn't work. I know also that this is not a Ubuntu problem, but a problem with flash. 

I think that my problem has to do with Intel and its video drivers, which is understandable, but I have the specially crafted DVD for Dell so I don't really know what else to do.  (updating drivers improved overall performance of Ubuntu as suggested in the other thread for Intel graphics) 

Also, language support for FF is way too much. I have uninstalled every language except for the three that I use the most and I still have more than 50 languages in the spell checker list which means I'm always wasting time looking for the correct language. 

My suggestion is to download chromium and enable plugins. It is twice as fast, flash is ok and it tends to break every once in a while. It's a shame really, that I have to use an unstable browser that is not even part of the distro. But at least it's open source.

---

### Post by lovinglinux on 2009-09-11
> **Dangger said:**
> Well I've tried almost everything. Firefox improved, not greatly though. Replacing youtube with totem or mplayer improves usability but youtube is not the only site with flash and when the video is embedded this solution doesn't work. I know also that this is not a Ubuntu problem, but a problem with flash. 

I think that my problem has to do with Intel and its video drivers, which is understandable, but I have the specially crafted DVD for Dell so I don't really know what else to do.  (updating drivers improved overall performance of Ubuntu as suggested in the other thread for Intel graphics) 

Also, language support for FF is way too much. I have uninstalled every language except for the three that I use the most and I still have more than 50 languages in the spell checker list which means I'm always wasting time looking for the correct language. 

My suggestion is to download chromium and enable plugins. It is twice as fast, flash is ok and it tends to break every once in a while. It's a shame really, that I have to use an unstable browser that is not even part of the distro. But at least it's open source.

Yep, flash is a problem for me too. Most sites play well, but there are some that are almost impossible to watch.

Nevertheless, I believe that using a browser in development stage is not a safe solution. You could try Firefox 3.6. It's in alpha stage, but it should be better than using Chromium right now. FF 3.6 is incredible fast, almost as good as Chromium. Flash plays well too.

---

### Post by Dangger on 2009-09-11
> **lovinglinux said:**
> Yep, flash is a problem for me too. Most sites play well, but there are some that are almost impossible to watch.

Nevertheless, I believe that using a browser in development stage is not a safe solution. You could try Firefox 3.6. It's in alpha stage, but it should be better than using Chromium right now. FF 3.6 is incredible fast, almost as good as Chromium. Flash plays well too.

Thanks, will try :D

---

### Post by KanineN on 2009-09-11
I tried ```
gksudo firefox &
``` when I tried to update my firefox thorugh ubuntuzilla but it don't work. I have the same version as before except that my bookmarks was gone...

---

### Post by lovinglinux on 2009-09-11
> **KanineN said:**
> I tried ```
gksudo firefox &
``` when I tried to update my firefox thorugh ubuntuzilla but it don't work. I have the same version as before...

I don't recommend updating FF 3.0 to 3.5 using the gksudo method. I never tried it, tho. I believe is simpler to just keep another Firefox version with regular Ubuntuzilla installation. To do that run this:

```
ubuntuzilla.py -a install -p firefox
```

> **KanineN said:**
> ...except that my bookmarks was gone...

Have you closed Firefox after using gksudo command? Are you able to restore a backup?

---

### Post by David-IT on 2009-09-12
:KS you do not understand how much i love the > sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree commands they fixed all of my flash problems and the flash optimization's went GREAT! ty soo much!

---

### Post by lovinglinux on 2009-09-12
> **David-IT said:**
> :KS you do not understand how much i love the  commands they fixed all of my flash problems and the flash optimization's went GREAT! ty soo much!

:D You are welcome.

---

### Post by sports fan Matt on 2009-09-12
This guide for whatever reason...when I run Running Profiles from RAM..it comopletely restores everything to defaults when i start FF eavh and every time.  Is there a way to fix this so that EVERY firefox session doesnt start as a default?  It does get annoying to lose all your FF custimizations everytime FF Starts

---

### Post by lovinglinux on 2009-09-12
> **sox fan Matt said:**
> This guide for whatever reason...when I run Running Profiles from RAM..it comopletely restores everything to defaults when i start FF eavh and every time.  Is there a way to fix this so that EVERY firefox session doesnt start as a default?  It does get annoying to lose all your FF custimizations everytime FF Starts

It shouldn't be doing that, as long as you don't boot. You need to restore the profile back to the disk before booting, but you can close and start Firefox as many times you want.

---

### Post by pcjunkie on 2009-09-12
Tweaks still work.

Amazing performance boost.

Cheers:P

---

### Post by lazylew on 2009-09-16
Firefox acted weird some months ago: messages wouldn't open, but keep on "loading" forever.
The only solution was to go back to "older version". 
Disabling labs and some add-ons I could live without didn't do the trick.
The problem was solved after a few weeks, but I have no clue how; was it after a "bettergmail2" or "bettergmail1" update or a general Ubuntu update... no idea.

Now since a few days the problem is back again.
To open an email I have to use "older version".

Any ideas? [COLOR=Red]EDIT: I[/COLOR] don't know where I left my brain when I typed all this... [COLOR=Red]I meant "Gmail[/COLOR] is acting weird" (using Firefox)

---

### Post by lovinglinux on 2009-09-16
> **lazylew said:**
> Firefox acted weird some months ago: messages wouldn't open, but keep on "loading" forever.
The only solution was to go back to "older version". 
Disabling labs and some add-ons I could live without didn't do the trick.
The problem was solved after a few weeks, but I have no clue how; was it after a "bettergmail2" or "bettergmail1" update or a general Ubuntu update... no idea.

Now since a few days the problem is back again.
To open an email I have to use "older version".

Any ideas?

Have you tried disabling ipv6?

---

### Post by lazylew on 2009-09-16
> **lovinglinux said:**
> Have you tried disabling ipv6?I don't know what that is, so I did a quick search for ipv6 and see that it has to do with slow internet? but that's not the case here. 
Connection is good and fast.

---

### Post by lovinglinux on 2009-09-16
> **lazylew said:**
> I don't know what that is, so I did a quick search for ipv6 and see that it has to do with slow internet? but that's not the case here. 
Connection is good and fast.

See See **Solution** [*[COLOR="Red"]**FOT005**[/COLOR]*] from the Troubleshooting section.

Perhaps you are experiencing issues with cookies. Some of these online services requires cookies for more than one domain.

---

### Post by lazylew on 2009-09-17
please note the [COLOR=Red]EDIT [/COLOR]of my initial post (194) :redface:
my brain connections failed a bit...

---

### Post by KanineN on 2009-09-23
Hello! Sorry for my newbie questions but I'm getting completly mad when I try to install plugins to mozilla. I just tried to install java. 

Here's the codes that I have been using

```
chmod +x Desktop/jre-6u12-linux-x64.bin (I downloaded a newer version so I changed that)
```
```
cd /opt
```
```
sudo sh ~/Desktop/jre-6u12-linux-x64.bin
```
```
cd /usr/lib/mozilla/plugins/
```
```
sudo ln -s /opt/jre1.6.0_12/lib/amd64/libnpjp2.so
```

When I tried the last code in the terminal it said I already had that, but I couldn't use java.

Then I remembered that I had a mozilla folder in home hidden. So I changed the last one so it would redirect to my mozilla in home. When I did that a square pop'd up and said from where I wanted to download me setting. It was "opera" and "nothing at all" so i choose nothing at all option. When I started firefox it was like I had formated firefox. All of my plugins where gone and all of my bookmarks.. 

Do you know what the problem is?

---

### Post by lovinglinux on 2009-09-23
> [COLOR="Red"]**Warning:**[/COLOR] if you are following this discussion because you want to install java, then keep in mind the previous post and the code below are for 64bit manual installation method. 32bit users should install java from the repositories.

> **KanineN said:**
> When I tried the last code in the terminal it said I already had that, but I couldn't use java.


Try these:

```
cd /usr/lib/mozilla/plugins/
```
```
sudo mv libnpjp2.so libnpjp2.so.bak
```
```
sudo ln -s /opt/jre1.6.0_12/lib/amd64/libnpjp2.so
```

> **KanineN said:**
> Then I remembered that I had a mozilla folder in home hidden. So I changed the last one so it would redirect to my mozilla in home. When I did that a square pop'd up and said from where I wanted to download me setting. It was "opera" and "nothing at all" so i choose nothing at all option. When I started firefox it was like I had formated firefox. All of my plugins where gone and all of my bookmarks.. 

Do you know what the problem is?

I guess you have replaced your **~/.mozilla** folder with a symlink to somewhere else. Check if it has an arrow emblem over the folder icon. If yes, then open its properties to see the real path. Then delete the Firefox profile related stuff from the real path and delete the **.mozilla** symlink from home. When you start Firefox again it will recreate the **~/.mozilla** folder.

---

### Post by lazylew on 2009-09-23
> **lazylew said:**
> ... [COLOR=Red]EDIT: I[/COLOR] don't know where I left my brain when I typed all this... [COLOR=Red]I meant "Gmail[/COLOR] is acting weird" (using Firefox)
Sorry to have invaded this thread with an off topic post inadvertently; meanwhile the problem is solved by using Opera for my Gmail (still love Firefox as well though ;-))

---

### Post by KanineN on 2009-09-24
> **lovinglinux said:**
> 

I guess you have replaced your **~/.mozilla** folder with a symlink to somewhere else. Check if it has an arrow emblem over the folder icon. If yes, then open its properties to see the real path. Then delete the Firefox profile related stuff from the real path and delete the **.mozilla** symlink from home. When you start Firefox again it will recreate the **~/.mozilla** folder.


I looked at my usr/bin/mozilla folder and it didn't have any arrow on it. But when I looked around I found firefox 3.0.14 and firefox 3.5.2, can I delete this? I also looked at the mozilla folder in home and it didn't have an arrow on it.

---

### Post by lovinglinux on 2009-09-24
> **KanineN said:**
> I looked at my usr/bin/mozilla folder and it didn't have any arrow on it. But when I looked around I found firefox 3.0.14 and firefox 3.5.2, can I delete this? I also looked at the mozilla folder in home and it didn't have an arrow on it.

DON'T DELETE installation folders manually.

If I were you I would start from scratch.

Uninstall firefox-3.5 with the proper ubuntuzilla command:

```
ubuntuzilla.py -a remove -p firefox
```

Then rename the **.mozilla** folder in your [COLOR="DarkRed"]**home**[/COLOR] directory as a backup:

```
mv ~/.mozilla ~/.mozilla_backup
```

Then install firefox-3.5 again:

```
ubuntuzilla.py -a install -p firefox
```

Start Firefox, so it will recreate your ~/.mozilla folder and a new profile. 

Then close firefox and try to install the java plugin using the same method you've tried before.

---

### Post by KanineN on 2009-09-24
> **lovinglinux said:**
> 
Then close firefox and try to install the java plugin using the same method you've tried before.

It says that I already have java in the mozilla folder so I looked it up and I had it in the plugin folder. 


libj2pcsc.so and libj2pcsc.so.bak. 

But then again I have libflashplayer  in the same folder but flash is not working neither..

---

### Post by lovinglinux on 2009-09-24
> **KanineN said:**
> It says that I already have java in the mozilla folder so I looked it up and I had it in the plugin folder. 


libj2pcsc.so and libj2pcsc.so.bak. 

But then again I have libflashplayer  in the same folder but flash is not working neither..

Uninstall java and flash from synaptic before installing them manually.

---

### Post by KanineN on 2009-09-24
> **lovinglinux said:**
> Uninstall java and flash from synaptic before installing them manually.

Synaptic says that I don't have any java or flash installed. I had some files installed when I searched for java but non of them was for firefox. In flash I had libswfdec-0.8.4-1 installed.

---

### Post by lovinglinux on 2009-09-24
> **KanineN said:**
> Synaptic says that I don't have any java or flash installed. I had some files installed when I searched for java but non of them was for firefox. In flash I had libswfdec-0.8.4-1 installed.

I don't know about the java issue, but to remove that flash plugin run this:

```
sudo apt-get remove swfdec-mozilla
```

See the Flash Optimization section for further instructions.

---

### Post by ajaustin on 2009-09-24
I'm running Firefox 3.0.14 on Hardy Heron LTS. If Firefox is open when I Log Out or Shut Down the currently open web pages are automatically saved and next time I launch Firefox I get these tabs and not the Home page.

Can I get Firefox to give me the Home page?

If I close Firefox before Shutting Down I get the Save or Quit dialog but this does not come up when Shutting Down with Firefox still left open.

Regards.

---

### Post by lovinglinux on 2009-09-24
> **ajaustin said:**
> I'm running Firefox 3.0.14 on Hardy Heron LTS. If Firefox is open when I Log Out or Shut Down the currently open web pages are automatically saved and next time I launch Firefox I get these tabs and not the Home page.

Can I get Firefox to give me the Home page?

If I close Firefox before Shutting Down I get the Save or Quit dialog but this does not come up when Shutting Down with Firefox still left open.

Regards.

Type **about:config** in the address bar, then search for **browser.sessionstore.resume_from_crash** and set it to **false**. This should prevent Firefox from opening saved pages when you logoff or shut down without closing Firefox.

More info:

[http://kb.mozillazine.org/Browser.sessionstore.resume_from_crash](http://kb.mozillazine.org/Browser.sessionstore.resume_from_crash)
[http://kb.mozillazine.org/Browser.sessionstore.enabled](http://kb.mozillazine.org/Browser.sessionstore.enabled)

---

### Post by ajaustin on 2009-09-25
> **lovinglinux said:**
> Type **about:config** in the address bar, then search for **browser.sessionstore.resume_from_crash** and set it to **false**. This should prevent Firefox from opening saved pages when you logoff or shut down without closing Firefox.

More info:

[http://kb.mozillazine.org/Browser.sessionstore.resume_from_crash](http://kb.mozillazine.org/Browser.sessionstore.resume_from_crash)
[http://kb.mozillazine.org/Browser.sessionstore.enabled](http://kb.mozillazine.org/Browser.sessionstore.enabled)

Thanks for your help "lovinglinux".

Setting Browser.sessionstore.resume_from_crash to false almost gave me what I wanted; no restored tabs but still no home page.

Setting Browser.sessionstore.enabled to false gets me what I want on Shut Down but now it doesn't warn me about closing multiple tabs.  Any ideas?

Tony

---

### Post by lovinglinux on 2009-09-25
> **ajaustin said:**
> Setting Browser.sessionstore.resume_from_crash to false almost gave me what I wanted; no restored tabs but still no home page.

Open Firefox preferences and set "Show my home page" in the Startup options.

---

### Post by ajaustin on 2009-09-25
> **lovinglinux said:**
> Open Firefox preferences and set "Show my home page" in the Startup options.

I _do_ have "show my home page" and "warn me when closing multiple tabs" set.

Just for the record, this all worked fine before I updated from Dapper Drake LTS to Hardy Heron LTS about 6 weeks ago.

Thanks for your help, any more ideas?

Tony

---

### Post by lovinglinux on 2009-09-25
> **ajaustin said:**
> I _do_ have "show my home page" and "warn me when closing multiple tabs" set.

Just for the record, this all worked fine before I updated from Dapper Drake LTS to Hardy Heron LTS about 6 weeks ago.

Thanks for your help, any more ideas?

Tony

There is a workaround. Create a new launcher or edit the current Firefox launcher, using the command below:

```
firefox http://www.yourhomepage.com
```

---

### Post by ajaustin on 2009-09-25
> **lovinglinux said:**
> There is a workaround. Create a new launcher or edit the current Firefox launcher, using the command below:

```
firefox http://www.yourhomepage.com
```

I haven't tried that yet as I seem to have solved the Home Page issue by doing the file renaming bit in this 
```
http://support.mozilla.com/en-US/kb/Firefox+does+not+ask+to+save+tabs+and+windows+on+exit?s=warn%20me%20when%20closing%20multiple%20tabs
```

link.

So the only problem remaining is that I am not getting the warning when closing multiple tabs. Which, strangely, _does_ work if I have 2 Firefox sessions open.

Tony

---

### Post by calaverazon on 2009-09-30
Hello I ve just checked out your section of flash optimization it just helped me a lot I was having so much headache with the Youtube lag that i was about to give up!!! :'( ,now it s working just fine!!! ^^, when I have a little time off I ll continue checking the other solutions to see what I can get, but for now my system with ubuntu its working just awesome (L)!!

Saludos desde Argentina

---

### Post by lovinglinux on 2009-09-30
> **calaverazon said:**
> Hello I ve just checked out your section of flash optimization it just helped me a lot I was having so much headache with the Youtube lag that i was about to give up!!! :'( ,now it s working just fine!!! ^^, when I have a little time off I ll continue checking the other solutions to see what I can get, but for now my system with ubuntu its working just awesome (L)!!

Saludos desde Argentina

I'm glad it helped. What version of Firefox are you using?

---

### Post by calaverazon on 2009-10-03
I m using 3.0.1.4, right now Im checking on how to update it, Im a newbie so Im going step by step :P

---

### Post by MohanaRao on 2009-10-11
Hi Friends 

I am using Firefox 3.5.5pre (shiretoko). My CPU reaching its peak level when i am browsing flash enabled website. In detail when i am playing a video on youtube . com CPU usage is 100% but when i downloaded video on my system and playing with vlc player CPU usage is 20%. I applied some tweaks to firefox nothing is helped me. Just throw me some light on this issue. Thanks in advance.

---

### Post by lovinglinux on 2009-10-12
> **MohanaRao said:**
> Hi Friends 

I am using Firefox 3.5.5pre (shiretoko). My CPU reaching its peak level when i am browsing flash enabled website. In detail when i am playing a video on youtube . com CPU usage is 100% but when i downloaded video on my system and playing with vlc player CPU usage is 20%. I applied some tweaks to firefox nothing is helped me. Just throw me some light on this issue. Thanks in advance.

Unfortunately, I have thrown all the light I have on the Flash Optimization section of the tutorial. Indeed playing the same videos with mplayer uses much less CPU. For YouTube you can use a Greasemonkey script to replace the flash player with mplayer.

---

### Post by lovinglinux on 2009-10-25
EDITED: nevermind

---

### Post by HousieMousie2 on 2009-10-27
Thank you for the fabulous walk-throughs!  Many things for me to try.

Unfortunately my Flash issues have nothing to do with downloadable media and everything to do with flash-using websites like Facebook's games... I am having frequent full system crashes.  113% CPU (How is that even possible?) and 13.7% Memory?!  Wow.

EDITED:  I take back that "Wow"... 276% CPU?!?

---

### Post by Butterknife on 2009-10-30
I've been instructed to come here with my Firefox issues.

Here is a brief summary of what's been going on - 

I just did a fresh install of Koala after being incredibly satisfied by 9.04. However, this proved to be a great disappointment for this one reason - Firefox 3.5 will NOT start no matter what! I've been using this browser on a daily basis for 9 years now and cannot imagine using anything else unless, like in this case, I can't help it.
 I removed it through Synaptic, downloaded a fresh package from Firefox web, tried to install that instead, but for some reason, the terminal isn't reporting anything at all, whenever I try to do anything in it, like untar/install. Usually there used to be lines of detail after untar process but this time - nothing. So I don't know if any of it is even successful. Running it through gksudo worked but it's not an option I want to use daily. Tried following #1 suggestion in this thread in Troubleshooting section, but nothing happened. This is what I get:

```
chown: changing ownership of `/home/ana/.mozilla/firefox/profiles.ini': Input/output error
chown: changing ownership of `/home/ana/.mozilla/firefox/9d1aipeq.default/bookmarks.html': Input/output error
chown: changing ownership of `/home/ana/.mozilla/firefox/9d1aipeq.default/compatibility.ini': Input/output error
chown: changing ownership of `/home/ana/.mozilla/firefox/9d1aipeq.default/.parentlock': Input/output error
chown: changing ownership of `/home/ana/.mozilla/firefox/9d1aipeq.default/XPC.mfasl': Input/output error
chown: changing ownership of `/home/ana/.mozilla/firefox/9d1aipeq.default/localstore.rdf': Input/output error
chown: changing ownership of `/home/ana/.mozilla/firefox/9d1aipeq.default/XUL.mfasl': Input/output error
chown: changing ownership of `/home/ana/.mozilla/firefox/9d1aipeq.default/xpti.dat': Input/output error
chown: changing ownership of `/home/ana/.mozilla/firefox/9d1aipeq.default/mimeTypes.rdf': Input/output error
chown: changing ownership of `/home/ana/.mozilla/firefox/9d1aipeq.default/search.json': Input/output error
chown: changing ownership of `/home/ana/.mozilla/firefox/9d1aipeq.default/compreg.dat': Input/output error
chown: changing ownership of `/home/ana/.mozilla/firefox/9d1aipeq.default/chrome/userChrome-example.css': Input/output error
chown: changing ownership of `/home/ana/.mozilla/firefox/9d1aipeq.default/chrome/userContent-example.css': Input/output error
```

In addition to this, terminal seems incapable of make install of anything, which is making the whole situation even more infuriating.

---

### Post by lovinglinux on 2009-10-30
> **Butterknife said:**
> I've been instructed to come here with my Firefox issues.

Here is a brief summary of what's been going on - 

I just did a fresh install of Koala after being incredibly satisfied by 9.04. However, this proved to be a great disappointment for this one reason - Firefox 3.5 will NOT start no matter what! I've been using this browser on a daily basis for 9 years now and cannot imagine using anything else unless, like in this case, I can't help it.
 I removed it through Synaptic, downloaded a fresh package from Firefox web, tried to install that instead, but for some reason, the terminal isn't reporting anything at all, whenever I try to do anything in it, like untar/install. Usually there used to be lines of detail after untar process but this time - nothing. So I don't know if any of it is even successful. Running it through gksudo worked but it's not an option I want to use daily. Tried following #1 suggestion in this thread in Troubleshooting section, but nothing happened. This is what I get:

```
chown: changing ownership of `/home/ana/.mozilla/firefox/profiles.ini': Input/output error
chown: changing ownership of `/home/ana/.mozilla/firefox/9d1aipeq.default/bookmarks.html': Input/output error
chown: changing ownership of `/home/ana/.mozilla/firefox/9d1aipeq.default/compatibility.ini': Input/output error
chown: changing ownership of `/home/ana/.mozilla/firefox/9d1aipeq.default/.parentlock': Input/output error
chown: changing ownership of `/home/ana/.mozilla/firefox/9d1aipeq.default/XPC.mfasl': Input/output error
chown: changing ownership of `/home/ana/.mozilla/firefox/9d1aipeq.default/localstore.rdf': Input/output error
chown: changing ownership of `/home/ana/.mozilla/firefox/9d1aipeq.default/XUL.mfasl': Input/output error
chown: changing ownership of `/home/ana/.mozilla/firefox/9d1aipeq.default/xpti.dat': Input/output error
chown: changing ownership of `/home/ana/.mozilla/firefox/9d1aipeq.default/mimeTypes.rdf': Input/output error
chown: changing ownership of `/home/ana/.mozilla/firefox/9d1aipeq.default/search.json': Input/output error
chown: changing ownership of `/home/ana/.mozilla/firefox/9d1aipeq.default/compreg.dat': Input/output error
chown: changing ownership of `/home/ana/.mozilla/firefox/9d1aipeq.default/chrome/userChrome-example.css': Input/output error
chown: changing ownership of `/home/ana/.mozilla/firefox/9d1aipeq.default/chrome/userContent-example.css': Input/output error
```

In addition to this, terminal seems incapable of make install of anything, which is making the whole situation even more infuriating.

Since your problem seems to be a little bit complex and probably not just related to Firefox, I will send you a PM soon. We will try to figure out what's going on and fix your installation. Please wait for my PM.

---

### Post by lovinglinux on 2009-10-30
> **lovinglinux said:**
> Since your problem seems to be a little bit complex and probably not just related to Firefox, I will send you a PM soon. We will try to figure out what's going on and fix your installation. Please wait for my PM.

Problem fixed by PM. It was a corrupted Firefox profile.

---

### Post by mousestalker on 2009-10-30
I've upgraded to 9.10. I now have one issue, which I'm trying to solve. This is not that issue. :)

Back when I was running Jaunty, I installed firefox 3.5.x as 'shiretoko'. Now, with the upgrade, I have a nonfunctional 'firefox' button under applications and a functional 'minefield'. I also seem to have various bits and bobs of firefox/mozilla scattered all over my poor computer. 

Assuming that I'm an idiot (which is pretty safe), how can I eliminate all the various loose bits, reduce down to just firefox 3.5 and keep all my bookmarks/passwords/plugins and other custom features?

In short, what can I safely remove, what should I not touch, and what must I rename or move?

---

### Post by lovinglinux on 2009-10-30
> **mousestalker said:**
> I've upgraded to 9.10. I now have one issue, which I'm trying to solve. This is not that issue. :)

Back when I was running Jaunty, I installed firefox 3.5.x as 'shiretoko'. Now, with the upgrade, I have a nonfunctional 'firefox' button under applications and a functional 'minefield'. I also seem to have various bits and bobs of firefox/mozilla scattered all over my poor computer. 

Assuming that I'm an idiot (which is pretty safe), how can I eliminate all the various loose bits, reduce down to just firefox 3.5 and keep all my bookmarks/passwords/plugins and other custom features?

In short, what can I safely remove, what should I not touch, and what must I rename or move?


First open the minefield version, go to "Help >> About Mozilla Firefox" and check the version of minefield. Close it. If the version is 3.6 for example, then run the following command:

```
sudo apt-get remove firefox-3.6
```

Then re-install Firefox 3.5. Open Synaptic Package Manager, search for firefox, then select the packages **firefox** and **firefox-3.5** and mark them for re-installation. Click apply. This should restore your launchers. If not, then make sure the launcher command is **firefox %u**.

Then run these commands:

```
mv ~/.mozilla/firefox ~/.mozila/firefox_old
mv ~/.mozilla/firefox-3.5 ~/.mozilla/firefox
```

This will restore Shiretoko profiles into the folder used by the default installation of Firefox 3.5.

That's it.

---

### Post by mousestalker on 2009-10-30
Thanks for the fast reply!

My version is showing up as version 3.5.5pre

I tried removing with apt-get 3.5.5 and 3.5.5pre, but got a 'not found' error. weirdly, the version of ubuntu showing in the same box is jaunty, not karmic.

---

### Post by lovinglinux on 2009-10-30
> **mousestalker said:**
> Thanks for the fast reply!

My version is showing up as version 3.5.5pre

I tried removing with apt-get 3.5.5 and 3.5.5pre, but got a 'not found' error. weirdly, the version of ubuntu showing in the same box is jaunty, not karmic.

You can remove it via Synaptic, since it will show which version is installed. Since you have a development version, you probably need to remove the PPA repository associated with it. Check if you have a *ubuntu-mozilla-daily* or *ubuntu-mozilla-security* through the Software Sources manager and disable or remove it before re-installing firefox-3.5.

---

### Post by SilverWave on 2009-10-31
Thanks for the prompt on flash - in Karmic 9.10, flash was working but "just" e.g. it played but I couldn't get it to pause or jump or do full screen.
Embedded Flash video didn't work at all :(

Fix:
1. Uninstall "flashplugin-installer" via synaptic.
2. Follow the instructions in the Quote.
> Danny Piccirillo: 
The 32-bit flash player runs terribly on 64-bit systems, and if you don't want to use Gnash, Adobe has released the only 64-bit version of Flash Player 10 for Linux! It currently isn't in the repositories because it's still in alpha, but it's so much more stable than even the final 32-bit version. To install it, download the .tar.gz file at the bottom of this page:

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Next, extract the file to your home folder; then just enter this into a terminal window:

sudo cp libflashplayer.so /usr/lib/mozilla/plugins/

From: Top things to do after installing Ubuntu Linux 9.10 Karmic Koala
[http://swik.net/Ubuntu/Planet+Ubuntu/Danny+Piccirillo:+Top+things+to+do+after+installing+Ubuntu+Linux+9.10+Karmic+Koala/c66hb](http://swik.net/Ubuntu/Planet+Ubuntu/Danny+Piccirillo:+Top+things+to+do+after+installing+Ubuntu+Linux+9.10+Karmic+Koala/c66hb)

[EDIT]
Spoke to soon - the 64-bit version of Flash Player 10 for Linux isn't in the repositories for a reason, it is an Alpha (crashes gmail when chat loads).

---

### Post by mousestalker on 2009-10-31
Well, I now have one version of Firefox (3.5.4), but it stubbornly refuses to believe in Java. Since I have to use Java for my job, I've installed Opera. Opera works quite nicely with the website I must use for work, so that reduces my Firefox Java problem from a head ache to an annoyance.

:)

---

### Post by lovinglinux on 2009-10-31
> **SilverWave said:**
> Thanks for the prompt on flash - in Karmic 9.10, flash was working but "just" e.g. it played but I couldn't get it to pause or jump or do full screen.
Embedded Flash video didn't work at all :(

Fix:
1. Uninstall "flashplugin-installer" via synaptic.
2. Follow the instructions in the Quote.


And it Just Works! :D

Thanks for the tip. 

There is a quote in the Flash Optimization section for 64bit users to a tutorial that provides essentially the same method:

> Note: For flash 64bit visit [http://news.softpedia.com/news/How-t...10-98076.shtml](http://news.softpedia.com/news/How-t...10-98076.shtml)

---

### Post by SilverWave on 2009-10-31
Spoke to soon - the 64-bit version of Flash Player 10 for Linux isn't in the repositories for a reason, it is an Alpha (crashes gmail when chat loads).

So best to wait for a fix to the 32bit flash included in Karmic. Its high profile and they have identified the root cause here: [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407/comments/143](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407/comments/143)

I have also tested the fix and it works fine... up to now ;)

> 
I've renamed my /usr/lib/nspluginwrapper/i386/linux/npviewer.bin to npviewer.bin.real, and created an executable script in place of npviewer.bin with the following contents:

#!/bin/sh
GDK_NATIVE_WINDOWS=true /usr/lib/nspluginwrapper/i386/linux/npviewer.bin.real $*


If you try this don't forget to make the script executable.

---

### Post by H.Filbert on 2009-11-01
Hello,

I am a new user to Ubuntu, just installed 9.10 (fr) when it came out and everything was working like a charm until this evening. Just suddenly, Firefox stopped working. I cannot launch it anymore if I click on the icon.
From the command terminal, I can start firefox, it informs me that I can get back my last session and, whatever my choice, it just ends there with this error message on the command terminal :
[I]firefox: ../../src/xcb_io.c*:542*:*_XRead:  L'assertion «*dpy->xcb->reply_data != ((void *)0)*» a échoué.
Abandon[/I]

I have uninstall/reinstall it but it didn't work out. I found this command and it  did launch firefox
*gksudo firefox*

Hope you can help me out.

---

### Post by lovinglinux on 2009-11-01
> **H.Filbert said:**
> I found this command and it  did launch firefox
*gksudo firefox*

It launches with gksudo because then it uses the root profile, which is clean. So the problem must be a corrupted profile.

Run this commands on a terminal.

```
mv ~/.mozilla/firefox ~/.mozilla/firefox_backup
```

When you start Firefox it should create a new profile and it should work. You will have to copy some files from the backup above if you want to restore bookmarks, extensions, passwords and so on. But I advice to not copy all at once, otherwise you will end up with the same problem. You should copy just the files you need, one by one and test firefox after each copy.

---

### Post by lovinglinux on 2009-11-01
On a second thought, perhaps you could fix your current profile by deleting the file **sessionstore.js** from your current profile folder.

---

### Post by H.Filbert on 2009-11-01
Thank you very much for the quick replies.

Can you give me the location for the current profile folder?

---

### Post by lovinglinux on 2009-11-01
> **H.Filbert said:**
> Thank you very much for the quick replies.

Can you give me the location for the current profile folder?

It's a hidden folder under your home directory, so you need to hit CTRL+H to see it on Nautilus. The path is /home/**[COLOR="DarkRed"]you[/COLOR]**/.mozilla/firefox/[COLOR="DarkRed"]**xxxxxxxx.default**[/COLOR], where [COLOR="DarkRed"]**you**[/COLOR] is your user name, **[COLOR="DarkRed"]default[/COLOR]** is your profile name and [COLOR="DarkRed"]**xxxxxxxx**[/COLOR] is a series of random letters and numbers.

---

### Post by H.Filbert on 2009-11-01
It's strange, I don't have this file *sessionstore.js*, I have *session.rdf* but no js file.

---

### Post by lovinglinux on 2009-11-01
> **H.Filbert said:**
> It's strange, I don't have this file *sessionstore.js*, I have *session.rdf* but no js file.

Move *session.rdf* to another place and start Firefox to see if solves the problem.

---

### Post by H.Filbert on 2009-11-01
It didn't :(
It gave me the same error on the terminal.

---

### Post by lovinglinux on 2009-11-01
> **H.Filbert said:**
> It didn't :(
It gave me the same error on the terminal.

Do [this](http://ubuntuforums.org/showpost.php?p=8217418&postcount=234) then.

---

### Post by H.Filbert on 2009-11-01
> 
mv ~/.mozilla/firefox ~/.mozilla/firefox_backup


I tried the move command and carefully copy/pasted everything from the backup folder. Error was coming from the Extension folder in which I had 12 addons. I had to take out the cooliris addon which was the culprit. So everything's working now. Thank you for your help!

I have noticed that even when I launch firefox with *gksudo firefox*, I do get warning messages. Is it normal?
[I](firefox:7553): Gdk-WARNING **: XID collision, trouble ahead
(firefox:7553): Gdk-WARNING **: XID collision, trouble ahead (...)[/I]

---

### Post by lovinglinux on 2009-11-01
> **H.Filbert said:**
> I tried the move command and carefully copy/pasted everything from the backup folder. Error was coming from the Extension folder in which I had 12 addons. I had to take out the cooliris addon which was the culprit. So everything's working now. Thank you for your help!

I have noticed that even when I launch firefox with *gksudo firefox*, I do get warning messages. Is it normal?
[I](firefox:7553): Gdk-WARNING **: XID collision, trouble ahead
(firefox:7553): Gdk-WARNING **: XID collision, trouble ahead (...)[/I]

Oh yes, cooliris causes a lot of trouble.

---

### Post by H.Filbert on 2009-11-02
> **lovinglinux said:**
> Oh yes, cooliris causes a lot of trouble.

I found it so cool but it almost made me crazy causing firefox to crash like that. 
I just solved my first Ubuntu puzzle. Thanks for all your help \\:D/

---

### Post by Rambar on 2009-11-02
This is a great topic. Thanks for the help. :p

---

### Post by phillw on 2009-11-09
Hi lovinglinux, please don't hate me :lolflag:

when you get some time, could you pop over and have a look at this thread -->> [http://ubuntuforums.org/showthread.php?t=1261872](http://ubuntuforums.org/showthread.php?t=1261872)

I'd rather not get into forced re-installing for FF, I'm hoping you have a less scary solution.

Thanks,

Phill.

---

### Post by lovinglinux on 2009-11-09
> **phillw said:**
> Hi lovinglinux, please don't hate me :lolflag:

when you get some time, could you pop over and have a look at this thread -->> [http://ubuntuforums.org/showthread.php?t=1261872](http://ubuntuforums.org/showthread.php?t=1261872)

I'd rather not get into forced re-installing for FF, I'm hoping you have a less scary solution.

Thanks,

Phill.

Hi,

Copy **about:config** and paste it in the address bar and click enter. Then type **browser.urlbar** in the filter field and hit enter. Take a screenshot of the results and post here.

Does the problem persists if you start Firefox in safe mode?

To start Firefox in safe mode, close it and run this on terminal:

```
firefox -safe-mode
```

Does the problem persists if you use a clean profile?

To create a new and clean profile close Firefox then run this:

```
firefox -P
```

It will launch the profile manager, from where you create and start a new profile.

---

### Post by zebrapositions on 2009-11-16
"filename" could not be saved, because you cannot change the contents of that folder.
error happens when i try to open something like a torrent or other file associated with anything. i also cannot "open containing folder" either. before the update i had no problems what so ever. if this is a firefox bug, sorry for the hassle but i need a fix. i have read and tried the "fix" in this post
[http://ubuntuforums.org/showthread.php?t=1287258&highlight=torrent+saved%2C+change+contents+folder.](http://ubuntuforums.org/showthread.php?t=1287258&highlight=torrent+saved%2C+change+contents+folder.)

and i see the same problem here
[http://ubuntuforums.org/showthread.php?t=1121810&highlight=torrent+saved%2C+change+contents+folder.](http://ubuntuforums.org/showthread.php?t=1121810&highlight=torrent+saved%2C+change+contents+folder.)

my /tmp dir is fine and even if i save it somewhere else i cannot "open containing folder", nothing happens

ive tried renaming my .mozilla dir and apt-get remove firefox* and reinstalling, nothing seems to work

---

### Post by lovinglinux on 2009-11-16
> **zebrapositions said:**
> "filename" could not be saved, because you cannot change the contents of that folder.
error happens when i try to open something like a torrent or other file associated with anything. i also cannot "open containing folder" either. before the update i had no problems what so ever. if this is a firefox bug, sorry for the hassle but i need a fix. i have read and tried the "fix" in this post
[http://ubuntuforums.org/showthread.php?t=1287258&highlight=torrent+saved%2C+change+contents+folder.](http://ubuntuforums.org/showthread.php?t=1287258&highlight=torrent+saved%2C+change+contents+folder.)

and i see the same problem here
[http://ubuntuforums.org/showthread.php?t=1121810&highlight=torrent+saved%2C+change+contents+folder.](http://ubuntuforums.org/showthread.php?t=1121810&highlight=torrent+saved%2C+change+contents+folder.)

my /tmp dir is fine and even if i save it somewhere else i cannot "open containing folder", nothing happens

ive tried renaming my .mozilla dir and apt-get remove firefox* and reinstalling, nothing seems to work

What version of Firefox and Ubuntu you are using?

It seems to be a bug in recent Firefox versions - [http://ubuntuforums.org/showthread.php?t=1296958](http://ubuntuforums.org/showthread.php?t=1296958)

I remember discussing this, but I can't find the thread right now.

Perhaps you could disable the "Ubuntu Firefox Modifications" extension and check if it works then. I'm just guessing here, but it could work :)

---

### Post by zebrapositions on 2009-11-19
> **lovinglinux said:**
> What version of Firefox and Ubuntu you are using?

It seems to be a bug in recent Firefox versions - [http://ubuntuforums.org/showthread.php?t=1296958](http://ubuntuforums.org/showthread.php?t=1296958)

I remember discussing this, but I can't find the thread right now.

Perhaps you could disable the "Ubuntu Firefox Modifications" extension and check if it works then. I'm just guessing here, but it could work :)

i just updated to ubuntu 9.10. thats when this happened, so firefox 3.5.5

---

### Post by lovinglinux on 2009-11-19
> **zebrapositions said:**
> i just updated to ubuntu 9.10. thats when this happened, so firefox 3.5.5

Sorry, I don't know how to solve your problem. I would consider re-installing Ubuntu from fresh, since your problem could be the result of a faulty upgrade.

---

### Post by zebrapositions on 2009-11-20
tried some more random things, apt-get remove firefox* and gnome extension. running firefox in safe mode and resetting everything. now when i right click and try to open containing folder it asks me what application to run and if i try to open the file it does the same error "... could not be saved, because you cannot change the contents of that folder." this is really starting to bother me, anyone got a fix?

---

### Post by J03y on 2009-11-24
Do these tweaks work in Xubuntu?

---

### Post by lovinglinux on 2009-11-24
> **J03y said:**
> Do these tweaks work in Xubuntu?

I don't see why not.

---

### Post by DavidMP on 2009-11-26
Hello, 

I wonder if I could get some help in here. I'm using FF3.5.5 in Hardy and when I close a session with multiple tabs open, choose to save the tabs and restart they are gone. 
I have tried the chown process again (I had made the common sudo instead of gksudo mistake some time ago and this fixed it). I have also resintalled FF from synaptic and re-run ubuntuzilla script and it is still the same. 
A puzzling fact is that sessionstore.js is made in the profile when I start FF but deleted as it ends. If I open sessionstore.js with gedit and save it the tabs appear upon re-start. Any idea what is telling FF to delete this file?

Just to check I tried running FF using gksudo and it gives no trouble

---

### Post by lovinglinux on 2009-11-26
> **DavidMP said:**
> Hello, 

I wonder if I could get some help in here. I'm using FF3.5.5 in Hardy and when I close a session with multiple tabs open, choose to save the tabs and restart they are gone. 
I have tried the chown process again (I had made the common sudo instead of gksudo mistake some time ago and this fixed it). I have also resintalled FF from synaptic and re-run ubuntuzilla script and it is still the same. 
A puzzling fact is that sessionstore.js is made in the profile when I start FF but deleted as it ends. If I open sessionstore.js with gedit and save it the tabs appear upon re-start. Any idea what is telling FF to delete this file?

Just to check I tried running FF using gksudo and it gives no trouble

Open the address **about:config** then type **session**, hit enter, make  a screenshot of Firefox settings and post it here.

If you want a quick fix, backup your settings with [FEBE](https://addons.mozilla.org/en-US/firefox/addon/2109), then close Firefox, then rename ~/.mozilla folder (check if there isn't any other application settings there), restart Firefox. Firefox will create a new profile from scratch. Then use FEBE to restore only the settings you need. Don't restore the entire profile, otherwise you might end up with the same problem.

---

### Post by DavidMP on 2009-11-27
Here is the output.

I might try FEBE but I would rather understand what is going on.
Thank you very much for your help. I really appreciate it

Cheers

David

---

### Post by lovinglinux on 2009-11-27
> **DavidMP said:**
> Here is the output.

I might try FEBE but I would rather understand what is going on.
Thank you very much for your help. I really appreciate it

Cheers

David

I figure it out. It's because you have configured Firefox to clear the browsing history when closing. You can disable that in the Privacy tab of FF preferences or type **about:config** in the address bar, then set **privacy.clearOnShutdown.history** or **privacy.sanitize.sanitizeOnShutdown** to **false**. The first one will disable only the browsing history deletion, while the second will turn off the feature completely.

---

### Post by DavidMP on 2009-11-28
> **lovinglinux said:**
> I figure it out. It's because you have configured Firefox to clear the browsing history when closing. You can disable that in the Privacy tab of FF preferences or type **about:config** in the address bar, then set **privacy.clearOnShutdown.history** or **privacy.sanitize.sanitizeOnShutdown** to **false**. The first one will disable only the browsing history deletion, while the second will turn off the feature completely.

Thanks for your help. 
**privacy.sanitize.sanitizeOnShutdown** to **false** did it 
Funnily enough, after an automated restart (updating extensions) it recovered correctly so this setting must only apply to a shutdown forced by the user

Thanks a lot lovinglinux

David

---

### Post by Bobhuber on 2009-12-08
I successfully compiled Firefox (3.6b4) for my processor following your great instructions and it has made a huge difference in performance . I have not however been able to use the instructions for compiling the program using the profile build. When it gets to the second run it gives the following error.

OBJDIR=/home/bob/mozilla-1.9.2/obj-x86_64-unknown-linux-gnu python /home/bob/mozilla-1.9.2/obj-x86_64-unknown-linux-gnu/_profile/pgo/profileserver.py
INFO | automation.py | Application pid: 7968
TEST-UNEXPECTED-FAIL | automation.py | Exited with code -11 during test run
INFO | automation.py | Application ran for: 0:00:00.024705
make: *** [profiledbuild] Error 245

I'm running 64bit Karmic 9.10 on an AMD Athlon X2 processor with 3/gig of ram.

---

### Post by lovinglinux on 2009-12-09
> **Bobhuber said:**
> I successfully compiled Firefox (3.6b4) for my processor following your great instructions and it has made a huge difference in performance . I have not however been able to use the instructions for compiling the program using the profile build. When it gets to the second run it gives the following error.

OBJDIR=/home/bob/mozilla-1.9.2/obj-x86_64-unknown-linux-gnu python /home/bob/mozilla-1.9.2/obj-x86_64-unknown-linux-gnu/_profile/pgo/profileserver.py
INFO | automation.py | Application pid: 7968
TEST-UNEXPECTED-FAIL | automation.py | Exited with code -11 during test run
INFO | automation.py | Application ran for: 0:00:00.024705
make: *** [profiledbuild] Error 245

I'm running 64bit Karmic 9.10 on an AMD Athlon X2 processor with 3/gig of ram.

That didn't work for me either since version 3.6a1. Unfortunately I'm not an expert on debugging compilation errors. Nevertheless, I wouldn't bother with it, since the performance improvement is not so big as when you compile with optimization flags for your processor.

---

### Post by Bobhuber on 2009-12-09
> **lovinglinux said:**
> That didn't work for me either since version 3.6a1. Unfortunately I'm not an expert on debugging compilation errors. Nevertheless, I wouldn't bother with it, since the performance improvement is not so big as when you compile with optimization flags for your processor.

Thanks for the reply.I've also tried it with 3.5.5 with the same results.I'll keep playing with it and change a couple of flags to see if that makes a difference and post the results.

---

### Post by DaveRowell on 2009-12-12
THANK YOU!

Disabling IPv6 in Firefox helped my lookup time - a lot.

---

### Post by cmcanulty on 2009-12-12
Wow, you surely are a firefox expert. I love firefox but am about to dump it as I extensively use bookmarks sorted into many folders for my work. Lately I can't save bookmarks to a folder just unsorted, and if I try to organize bookmarks none of them show. Also there are about 3 of every folder in the lists. I have tried uninstalling firefox, deleting profiles etc. Also I used the firefox backup before a clean install of Karmic and when I went to restore it the thing was empty.Very frustrating

---

### Post by lovinglinux on 2009-12-12
> **DaveRowell said:**
> THANK YOU!

Disabling IPv6 in Firefox helped my lookup time - a lot.

You are welcome.

> **cmcanulty said:**
> Wow, you surely are a firefox expert. I love firefox but am about to dump it as I extensively use bookmarks sorted into many folders for my work.

Have you tried [TagSifter](https://addons.mozilla.org/en-US/firefox/addon/998)? It is awesome to organize your bookmarks with tags. You can also use different folder organization. I use a mix of both.

TagSifter is not compatible with FF 3.5.x but you can force the compatibility. It works.

> **cmcanulty said:**
> Lately I can't save bookmarks to a folder just unsorted, and if I try to organize bookmarks none of them show. Also there are about 3 of every folder in the lists. I have tried uninstalling firefox, deleting profiles etc. Also I used the firefox backup before a clean install of Karmic and when I went to restore it the thing was empty.Very frustrating


I think there is some way to fix it. Do you have the original profile backup?

---

### Post by cmcanulty on 2009-12-13
No but I do have bookmarks saved that don't have the last few months. Now when I save a bookmark it is under the history in saved bookmarks but not in the list of unsorted and I can't save to a folder.I can do a new profile to solve this, anything that works. I tried the firefox -P command and it just opened another firefox.

---

### Post by gmgj on 2009-12-13
I have been saving my bookmarks since 1996 so I have quite a large collection as well.  But after 5,000 or so I decided that maybe I needed to look at a way of organizing and segmenting them.  I saved my bookmarks as html and broke them up into 3 different files.  The ones I frequently use were loaded back in and I can just push a button to search my "archived" ones.  I've used a couple of bookmark managers that all worked very well; however, the easiest thing for me has turned out to be segmenting the bookmarks and keeping a word processing project notebooks where I just paste hyperlinks used in research under various topics.  When I move from machine to machine I use Google Bookmarks or a wiki page to store items of interest.

---

### Post by lovinglinux on 2009-12-13
> **cmcanulty said:**
> No but I do have bookmarks saved that don't have the last few months. Now when I save a bookmark it is under the history in saved bookmarks but not in the list of unsorted and I can't save to a folder.I can do a new profile to solve this, anything that works. I tried the firefox -P command and it just opened another firefox.

If you have Firefox opened then use this:

```
firefox -P -no-remote
```

Export your current bookmarks to HTML, then create a new profile and import them to it,  then import the backup you already have to the same clean profile. Then close firefox, delete (move to a safe place) the file **places.sqlite** from your regular profile, then copy the same file from the new profile into it. This should solve the bookmark issues.

---

### Post by skaramanger on 2009-12-14
Hello,

I currently have no sound in flash. Video from youtube plays fine.  Video from[ http://alientrap.org/nexuiz/index.php]("http://alientrap.org/nexuiz/index.php")

I get the following error messages when I startup Firefox 3.5.5:

```
<prompt>cat  firefox-newprofile-alsa-errs.txt 
<prompt>firefox -ProfileManager --no-remote
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4633:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib pcm_hw.c:1433:(_snd_pcm_hw_open) Invalid value for card
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4633:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib pcm_hw.c:1433:(_snd_pcm_hw_open) Invalid value for card
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4633:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib pcm_hw.c:1433:(_snd_pcm_hw_open) Invalid value for card
Killed
```

My kernel is: 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:02:15 UTC 2009 x86_64 GNU/Linux

Below is a run of the shell script alsa-info.sh:

```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.58
!!################################

!!Script ran on: Tue Dec 15 04:33:35 UTC 2009


!!Linux Distribution
!!------------------

Ubuntu 9.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 9.10"


!!DMI Information
!!---------------

Manufacturer:      System manufacturer
Product Name:      System Product Name


!!Kernel Information
!!------------------

Kernel release:    2.6.31-16-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.21
Library version:    1.0.21a
Utilities version:  1.0.20


!!Loaded ALSA modules
!!-------------------

snd_usb_audio


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 1 [default        ]: USB-Audio - PnP Audio Device        
                      PnP Audio Device         at usb-0000:00:02.0-7, full speed


!!PCI Soundcards installed in the system
!!--------------------------------------



!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

05:00.0 0300: 10de:0402 (rev a1)
	Subsystem: 1682:4016


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-hda-intel: power_save=10 power_save_controller=N


!!Loaded sound module options
!!--------------------------

!!Module: snd_usb_audio
	async_unlink : Y
	device_setup : 0,0,0,0,0,0,0,0
	enable : Y,Y,Y,Y,Y,Y,Y,Y
	id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
	ignore_ctl_error : N
	index : -2,-1,-1,-1,-1,-1,-1,-1
	nrpacks : 8
	pid : -1,-1,-1,-1,-1,-1,-1,-1
	vid : -1,-1,-1,-1,-1,-1,-1,-1


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116, 32 Dec 13 18:06 /dev/snd/controlC1
crw-rw----+ 1 root audio 116, 56 Dec 13 18:12 /dev/snd/pcmC1D0c
crw-rw----+ 1 root audio 116, 48 Dec 13 22:24 /dev/snd/pcmC1D0p
crw-rw----+ 1 root audio 116,  1 Dec 13 18:06 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Dec 13 18:06 /dev/snd/timer

/dev/snd/by-id:
total 0
drwxr-xr-x 2 root root  60 Dec 13 18:06 .
drwxr-xr-x 4 root root 180 Dec 13 18:06 ..
lrwxrwxrwx 1 root root  12 Dec 13 18:06 usb-0d8c_PnP_Audio_Device-00 -> ../controlC1

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  60 Dec 13 18:06 .
drwxr-xr-x 4 root root 180 Dec 13 18:06 ..
lrwxrwxrwx 1 root root  12 Dec 13 18:06 pci-0000:00:02.0-usb-0:7:1.0 -> ../controlC1


!!ALSA configuration files
!!------------------------

!!User specific config file (~/.asoundrc)

pcm.usb-audio {
          type hw
          card 1 
       }
       
       ctl.usb-audio {
          type hw
          card 1
       }



!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 1: default [PnP Audio Device        ], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 1: default [PnP Audio Device        ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 1 [default]

Card hw:1 'default'/'PnP Audio Device         at usb-0000:00:02.0-7, full speed'
  Mixer name	: 'USB Mixer'
  Components	: 'USB0d8c:0201'
  Controls      : 17
  Simple ctrls  : 7
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 8065
  Mono:
  Front Left: Playback 6984 [87%] [6.49dB] [on]
  Front Right: Playback 6984 [87%] [6.49dB] [on]
Simple mixer control 'Speaker',1
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right - Rear Left - Rear Right - Front Center - Woofer - Side Left - Side Right
  Limits: Playback 0 - 197
  Mono:
  Front Left: Playback 176 [89%] [0.00dB] [on]
  Front Right: Playback 176 [89%] [0.00dB] [on]
  Rear Left: Playback 176 [89%] [0.00dB] [on]
  Rear Right: Playback 176 [89%] [0.00dB] [on]
  Front Center: Playback 176 [89%] [0.00dB] [on]
  Woofer: Playback 176 [89%] [0.00dB] [on]
  Side Left: Playback 176 [89%] [0.00dB] [on]
  Side Right: Playback 176 [89%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 6928
  Front Left: Capture 5543 [80%] [8.84dB] [on]
  Front Right: Capture 5543 [80%] [8.84dB] [on]
Simple mixer control 'PCM Capture Source',0
  Capabilities: enum
  Items: 'Mic' 'Mixer' 'CD  ' 'Input 3'
  Item0: 'Mixer'
Simple mixer control 'PCM',1
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 6928
  Front Left: Capture 5543 [80%] [8.84dB] [on]
  Front Right: Capture 5543 [80%] [8.84dB] [on]
Simple mixer control 'CD  ',0
  Capabilities: pvolume cvolume pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 8065 Capture 0 - 6928
  Front Left: Playback 6144 [76%] [5.71dB] [on] Capture 4096 [59%] [6.53dB] [on]
  Front Right: Playback 6144 [76%] [5.71dB] [on] Capture 4096 [59%] [6.53dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume cvolume pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 8065 Capture 0 - 6928
  Front Left: Playback 5152 [64%] [4.79dB] [on] Capture 4142 [60%] [6.61dB] [on]
  Front Right: Playback 5152 [64%] [4.79dB] [on] Capture 4142 [60%] [6.61dB] [on]


!!Alsactl output
!!-------------

--startcollapse--
state.default {
	control.1 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Playback Switch'
		value true
	}
	control.2 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 8065'
		comment.dbmin 0
		comment.dbmax 750
		iface MIXER
		name 'Mic Playback Volume'
		value.0 5152
		value.1 5152
	}
	control.3 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'CD   Playback Switch'
		value true
	}
	control.4 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 8065'
		comment.dbmin 0
		comment.dbmax 750
		iface MIXER
		name 'CD   Playback Volume'
		value.0 6144
		value.1 6144
	}
	control.5 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Speaker Playback Switch'
		value true
	}
	control.6 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 8065'
		comment.dbmin 0
		comment.dbmax 750
		iface MIXER
		name 'Speaker Playback Volume'
		value.0 6984
		value.1 6984
	}
	control.7 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Speaker Playback Switch'
		index 1
		value true
	}
	control.8 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 8
		comment.range '0 - 197'
		comment.dbmin 0
		comment.dbmax 0
		iface MIXER
		name 'Speaker Playback Volume'
		index 1
		value.0 176
		value.1 176
		value.2 176
		value.3 176
		value.4 176
		value.5 176
		value.6 176
		value.7 176
	}
	control.9 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Mic Capture Switch'
		value true
	}
	control.10 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 6928'
		comment.dbmin 0
		comment.dbmax 1106
		iface MIXER
		name 'Mic Capture Volume'
		value.0 4142
		value.1 4142
	}
	control.11 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'PCM Capture Switch'
		value true
	}
	control.12 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 6928'
		comment.dbmin 0
		comment.dbmax 1106
		iface MIXER
		name 'PCM Capture Volume'
		value.0 5543
		value.1 5543
	}
	control.13 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'CD   Capture Switch'
		value true
	}
	control.14 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 6928'
		comment.dbmin 0
		comment.dbmax 1106
		iface MIXER
		name 'CD   Capture Volume'
		value.0 4096
		value.1 4096
	}
	control.15 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'PCM Capture Switch'
		index 1
		value true
	}
	control.16 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 6928'
		comment.dbmin 0
		comment.dbmax 1106
		iface MIXER
		name 'PCM Capture Volume'
		index 1
		value.0 5543
		value.1 5543
	}
	control.17 {
		comment.access 'read write'
		comment.type ENUMERATED
		comment.count 1
		comment.item.0 Mic
		comment.item.1 Mixer
		comment.item.2 'CD  '
		comment.item.3 'Input 3'
		iface MIXER
		name 'PCM Capture Source'
		value Mixer
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
isofs
udf
crc_itu_t
binfmt_misc
vboxnetadp
vboxnetflt
vboxdrv
xt_time
xt_connlimit
xt_realm
iptable_raw
xt_comment
xt_policy
ipt_ULOG
ipt_REJECT
ipt_REDIRECT
ipt_NETMAP
ipt_MASQUERADE
ipt_LOG
ipt_ECN
ipt_ecn
ipt_CLUSTERIP
ipt_ah
ipt_addrtype
nf_nat_tftp
nf_nat_snmp_basic
nf_nat_sip
nf_nat_pptp
nf_nat_proto_gre
nf_nat_irc
nf_nat_h323
nf_nat_ftp
nf_nat_amanda
ts_kmp
nf_conntrack_amanda
nf_conntrack_sane
nf_conntrack_tftp
nf_conntrack_sip
nf_conntrack_proto_sctp
nf_conntrack_pptp
nf_conntrack_proto_gre
nf_conntrack_netlink
nf_conntrack_netbios_ns
nf_conntrack_irc
nf_conntrack_h323
nf_conntrack_ftp
xt_tcpmss
xt_recent
xt_pkttype
xt_physdev
xt_owner
xt_NFQUEUE
xt_NFLOG
nfnetlink_log
xt_multiport
xt_MARK
xt_mark
xt_mac
xt_limit
xt_length
xt_iprange
xt_helper
xt_hashlimit
xt_DSCP
xt_dscp
xt_dccp
xt_conntrack
xt_CONNMARK
xt_connmark
xt_CLASSIFY
xt_tcpudp
xt_state
iptable_nat
nf_nat
nf_conntrack_ipv4
nf_defrag_ipv4
nf_conntrack
iptable_mangle
nfnetlink
snd_usb_audio
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_page_alloc
snd_usb_lib
snd_hwdep
snd_seq_dummy
snd_seq_oss
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
iptable_filter
snd_seq
snd_timer
snd_seq_device
snd
ip_tables
amd64_edac_mod
nvidia
soundcore
hwmon_vid
i2c_nforce2
edac_core
k8temp
x_tables
ppdev
parport_pc
psmouse
serio_raw
asus_atk0110
joydev
lp
parport
ses
enclosure
hid_microsoft
dm_raid45
xor
sbp2
usbhid
usb_storage
ohci1394
ieee1394
floppy
forcedeth


!!ALSA/HDA dmesg
!!------------------

```

This has been frustrating.  If you have read this far, my thanks. I hope there is at least some suggestions out there that I might try.  I have read many posts and tried some of the suggestions. 

thanks in advance

---

### Post by lovinglinux on 2009-12-15
> **skaramanger said:**
> Hello,

I currently have no sound in flash. Video from youtube plays fine.  Video from[ http://alientrap.org/nexuiz/index.php]("http://alientrap.org/nexuiz/index.php")

I get the following error messages when I startup Firefox 3.5.5:
...
This has been frustrating.  If you have read this far, my thanks. I hope there is at least some suggestions out there that I might try.  I have read many posts and tried some of the suggestions. 

thanks in advance

Are you using 32bit or 64 bit? Are you using pulseaudio or alsa?

Check this out: [http://ubuntuforums.org/showthread.php?t=1309931](http://ubuntuforums.org/showthread.php?t=1309931)

---

### Post by skaramanger on 2009-12-15
Thanks for your reply lovinglinux,


> **lovinglinux said:**
> Are you using 32bit or 64 bit? Are you using pulseaudio or alsa?

I'm using 64bit flashplugin.



Check this out: [http://ubuntuforums.org/showthread.php?t=1309931](http://ubuntuforums.org/showthread.php?t=1309931)

I have seen this thread before, and tried removing pulseaudio.  If you look at my error messages you'll see that they appear to be related to alsa.  If Flash were using pulseaudio, then won't the errors be different.

I hope someone can clear this up. Even if there isn't a ready solution.  I'd just like to know why Flash is getting alsa errors.

Thanks again,

---

### Post by lovinglinux on 2009-12-15
> **skaramanger said:**
> Thanks for your reply lovinglinux,




I have seen this thread before, and tried removing pulseaudio.  If you look at my error messages you'll see that they appear to be related to alsa.  If Flash were using pulseaudio, then won't the errors be different.

I hope someone can clear this up. Even if there isn't a ready solution.  I'd just like to know why Flash is getting alsa errors.

Thanks again,

I have seen lots of threads about Flash audio issues recently, but unfortunately I don't have a solution for you. I'm using KDE on Karmic 32bit, which works fine with pulseaudio. When I was using Ubuntu Jaunty, this problem could be fixed by tweaking ALSA settings or by removing pulseaudio and installing ESD. I'm not sure you can do that on Karmic. Anyways, 64 bit is different story and I don't know much about it. Perhaps you could install the latest version of flash. It seems the new 64 bit version is pretty good. There are a few threads about it in the forums.

---

### Post by Bobhuber on 2009-12-15
> **skaramanger said:**
> Thanks for your reply lovinglinux,




I have seen this thread before, and tried removing pulseaudio.  If you look at my error messages you'll see that they appear to be related to alsa.  If Flash were using pulseaudio, then won't the errors be different.

I hope someone can clear this up. Even if there isn't a ready solution.  I'd just like to know why Flash is getting alsa errors.

Thanks again,


I have the same processor and a nvidia vidio card running Karmic 64bit.I had all kinds of problems untill I installed the 64bit Flash plugin (10.0 r32) and I also recommend that you install the 64bit Java plugin.I also had no luck at all when trying to upgrade to Karmic and wound up with a fresh install.Compiling firefox makes a HUGE difference.My benchmark (Peacekeeper) went from 1089 to 1377. Good luck.

---

### Post by skaramanger on 2009-12-15
Thanks bobhuber

> **Bobhuber said:**
> I have the same processor and a nvidia vidio card running Karmic 64bit.I had all kinds of problems untill I installed the 64bit Flash plugin (10.0 r32) and I also recommend that you install the 64bit Java plugin.I also had no luck at all when trying to upgrade to Karmic and wound up with a fresh install.Compiling firefox makes a HUGE difference.My benchmark (Peacekeeper) went from 1089 to 1377. Good luck.

Yeah I've been contemplating a fresh install. Soon.. I have the 64bit 10.0.r42 installed right now.  I'll consider compiling Firefox.  See how it goes.

---

### Post by skaramanger on 2009-12-16
> **skaramanger said:**
> Thanks bobhuber



Yeah I've been contemplating a fresh install. Soon.. I have the 64bit 10.0.r42 installed right now.  I'll consider compiling Firefox.  See how it goes.

:) Well I did a fresh install last night and all works now. But I hate the fight get it right.  Maybe only fresh installs from now on! Problem with sound is no longer.

---

### Post by AgenT on 2009-12-17
I had a problem where Flash would cause 95-100% CPU usage in Firefox and other browsers. The movie would first stop having sound then would freeze altogether. Closing the tab where the flash movie was playing would not help. Only restarting the browser helped.

The solution?

I had timidity installed, from before my upgrade to 9.10. Timidity steals the soundcard which produces problems. After removing timidity, the problem went away. Now I get 30-40% CPU and after the movie finishes playing, it drops to CPU usage before playing the movie!

For those having any PulseAudio problems, **READ OVER THE [SIZE=3]_[KARMIC CAVEATS]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")_[/SIZE] WIKI**!

---

### Post by Simulation Brain on 2009-12-24
Just wanted to share how I fixed my new install of Karmic:

"PCM" volume on KMix had been automagically turned all the way off at some point- with it on, everything works!

---

### Post by cmcanulty on 2009-12-25
One thing tht is driving me crazy. My address bar searches with Yahoo even after I go to about:config and set it to google I even tried changing it to yahoo and back to google and it still searches with yahoo which I hat, can someone help me with this?

---

### Post by AridWarrior on 2010-01-03
Recently, I installed Karmic on my Dell Inspiron E1505 laptop via Wubi. Firefox worked fine until I restarted my machine following some updates (prompted by Update Manager). After the restart I have not been able to start Firefox via the panel Firefox icon or via **Applications>Internet>Firefox Web Browser**. All I get is a message saying **Starting Firefox Web Browser** in the bottom panel which disappears after a few seconds.

When I try to launch firefox from the terminal using the command

```
firefox
```I get a message saying **exec: 148: /usr/lib/firefox-3.5.6/: Permission denied**

However, firefox does launch with the command:

```
gksudo firefox
```(Please note that I kept getting a "**GLib-Warning :** **g_set_prgname() called multiple times" **message initially with the gksudo firefox command but this went away when I downgraded the libglib2.0-0 and libglib2.0-data packages to the previous version , 2.22.2-0ubuntu1)
[B][U]
Steps Taken So Far:[/U][/B]
1. I renamed the .mozilla folder to .mozilla_OLD based on a thread I read but that did not help.

2. I reinstalled all the firefox packages but that did not help either.

Any idea as to what might be causing this behaviour. 

Regards

AridWarrior

---

### Post by lovinglinux on 2010-01-03
> **cmcanulty said:**
> One thing tht is driving me crazy. My address bar searches with Yahoo even after I go to about:config and set it to google I even tried changing it to yahoo and back to google and it still searches with yahoo which I hat, can someone help me with this?

Sorry for the delay. I don't know how I missed this post.

Have you tried to create a clean profile or start Firefox in safe mode? Perhaps there is an extension messing with the search functionality. For example, I'm currently using FF 3.6b5 and when I use the "Add To Search Bar" extension I can no longer organize the search engines with the search bar manager.


> **AridWarrior said:**
> Recently, I installed Karmic on my Dell Inspiron E1505 laptop via Wubi. Firefox worked fine until I restarted my machine following some updates (prompted by Update Manager). After the restart I have not been able to start Firefox via the panel Firefox icon or via **Applications>Internet>Firefox Web Browser**. All I get is a message saying **Starting Firefox Web Browser** in the bottom panel which disappears after a few seconds.

When I try to launch firefox from the terminal using the command

```
firefox
```I get a message saying **exec: 148: /usr/lib/firefox-3.5.6/: Permission denied**

However, firefox does launch with the command:

```
gksudo firefox
```(Please note that I kept getting a "**GLib-Warning :** **g_set_prgname() called multiple times" **message initially with the gksudo firefox command but this went away when I downgraded the libglib2.0-0 and libglib2.0-data packages to the previous version , 2.22.2-0ubuntu1)
[B][U]
Steps Taken So Far:[/U][/B]
1. I renamed the .mozilla folder to .mozilla_OLD based on a thread I read but that did not help.

2. I reinstalled all the firefox packages but that did not help either.

Any idea as to what might be causing this behaviour. 

Regards

AridWarrior

The only thing I can think of is that it could be Apparmor messing with Firefox, since a Firefox profile was included in karmic.

Try this:

```
sudo mv /etc/apparmor.d/usr.bin.firefox-3.5 /etc/apparmor.d/usr.bin.firefox-3.5.old
```

Then this:

```
sudo /etc/init.d/apparmor restart
```

If that doesn't help, then run the following code to revert the changes:

```
sudo mv /etc/apparmor.d/usr.bin.firefox-3.5.old /etc/apparmor.d/usr.bin.firefox-3.5
```

```
sudo /etc/init.d/apparmor restart
```

Also check if the file /usr/lib/firefox-3.5.6/firefox is set as an executable.

---

### Post by AridWarrior on 2010-01-03
@lovinglinux: Thanks for the reply. The Apparmor steps you recommended did not help. As suggested I reverted the changes. 

The **/usr/lib/firefox-3.5.6/firefox** is set as an executable. Actually if it helps, here are the files(directories) in the directory /usr/lib/firefox-3.5.6/ along with the [file|Dir] permissions:

**total 152**
lrwxrwxrwx 1 root root     7 2010-01-03 11:49 abrowser -> firefox
lrwxrwxrwx 1 root root     7 2010-01-03 11:49 abrowser-3.5 -> firefox
-rw-r--r-- 1 root root  2027 2009-12-15 17:20 application.ini
-rw-r--r-- 1 root root  2552 2009-12-15 17:17 blocklist.xml
-rw-r--r-- 1 root root    49 2009-12-15 17:17 browserconfig.properties
drwxr-xr-x 3 root root  4096 2010-01-03 11:49 chrome
drwxr-xr-x 2 root root  4096 2010-01-03 11:49 components
drwxr-xr-x 3 root root  4096 2010-01-03 10:09 defaults
lrwxrwxrwx 1 root root    25 2010-01-03 10:09 dictionaries -> ../../share/myspell/dicts
drwxr-xr-x 2 root root  4096 2010-01-03 11:49 distribution
lrwxrwxrwx 1 root root    28 2010-01-03 10:09 extensions -> ../firefox-addons/extensions
-rwxr-xr-x 1 root root  9700 2009-12-15 17:20 ffox-35-beta-profile-migration-dialog
**-rwxr-xr-x 1 root root 75584 2009-12-15 17:20 firefox**
lrwxrwxrwx 1 root root     7 2010-01-03 11:49 firefox-3.5 -> firefox
-rw-r--r-- 1 root root   460 2009-12-15 17:15 firefox-3.5-restart-required.update-notifier
-rwxr-xr-x 1 root root  4277 2009-12-15 17:16 firefox.sh
drwxr-xr-x 2 root root  4096 2010-01-03 11:49 icons
drwxr-xr-x 2 root root  4096 2010-01-03 11:49 modules
lrwxrwxrwx 1 root root    25 2010-01-03 10:09 plugins -> ../firefox-addons/plugins
-rwxr-xr-x 1 root root 10450 2009-12-15 17:17 run-mozilla.sh
-rw-r--r-- 1 root root     0 2009-12-15 17:20 update.locale
drwxr-xr-x 3 root root  4096 2010-01-03 10:46 updates

Is there anything else I can try?

Regards

AridWarrior

---

### Post by lovinglinux on 2010-01-04
> **AridWarrior said:**
> 

Is there anything else I can try?

Regards

AridWarrior

Try this just to make sure you have the ownership of your mozilla folder:

```
sudo chown -R $USER:$USER ~/.mozilla
```

Don't replace $USER with your username. Just run the code as is.

Perhaps is a profile permission issue, since you can start it with gksudo, but the weird thing is that deleting ~/.mozilla didn't help. Anyway, it won't hurt to try.

---

### Post by Mahiwaga on 2010-01-04
Nice.. thanks for this post..:)

---

### Post by AridWarrior on 2010-01-04
> **lovinglinux said:**
> Try this just to make sure you have the ownership of your mozilla folder:

```
sudo chown -R $USER:$USER ~/.mozilla
```Don't replace $USER with your username. Just run the code as is.

Perhaps is a profile permission issue, since you can start it with gksudo, but the weird thing is that deleting ~/.mozilla didn't help. Anyway, it won't hurt to try.

```
sudo chown -R $USER:$USER ~/.mozilla
```

did not work. 

The folder ~/.mozilla is not getting created when I run firefox from the panel or when I just run 

```
**firefox**
```

in the terminal.

I can see the folder that I renamed i.e. ~/.mozilla_OLD but that's it.

The folder ~/.mozilla gets created when I run

```
**sudo firefox**
```

but then only root has access to the folder.

---

### Post by AridWarrior on 2010-01-07
Since I could not solve the problem I had to reinstall Karmic and now the issue is fixed. However, the order of the steps made a difference.

[U]Machine:
[/U]Dell E1505[U]

Steps Taken:[/U]

1. I re-installed Karmic via Wubi.
2. Launched Firefox successfully once the setup was complete.
2. Connected to the internet via Ethernet i.e. did not install any drivers for the wireless card.
3. Launched Update Manager and installed all the latest updates.
4. Restarted the machine.
5. Launched Firefox successfully again.
6. Installed the driver for the wireless card.
7. Connected to the wireless network and disconnected the Ethernet.
8. Launched Firefox and experienced no more issues.


Regards 
AridWarrior

---

### Post by dbruce100 on 2010-01-08
> **Butterknife said:**
> I've been instructed to come here with my Firefox issues.

Here is a brief summary of what's been going on - 

I just did a fresh install of Koala after being incredibly satisfied by 9.04. However, this proved to be a great disappointment for this one reason - Firefox 3.5 will NOT start no matter what! I've been using this browser on a daily basis for 9 years now and cannot imagine using anything else unless, like in this case, I can't help it.
 I removed it through Synaptic, downloaded a fresh package from Firefox web, tried to install that instead, but for some reason, the terminal isn't reporting anything at all, whenever I try to do anything in it, like untar/install. Usually there used to be lines of detail after untar process but this time - nothing. So I don't know if any of it is even successful. Running it through gksudo worked but it's not an option I want to use daily. Tried following #1 suggestion in this thread in Troubleshooting section, but nothing happened. This is what I get:

```
chown: changing ownership of `/home/ana/.mozilla/firefox/profiles.ini': Input/output error
chown: changing ownership of `/home/ana/.mozilla/firefox/9d1aipeq.default/bookmarks.html': Input/output error
chown: changing ownership of `/home/ana/.mozilla/firefox/9d1aipeq.default/compatibility.ini': Input/output error
chown: changing ownership of `/home/ana/.mozilla/firefox/9d1aipeq.default/.parentlock': Input/output error
chown: changing ownership of `/home/ana/.mozilla/firefox/9d1aipeq.default/XPC.mfasl': Input/output error
chown: changing ownership of `/home/ana/.mozilla/firefox/9d1aipeq.default/localstore.rdf': Input/output error
chown: changing ownership of `/home/ana/.mozilla/firefox/9d1aipeq.default/XUL.mfasl': Input/output error
chown: changing ownership of `/home/ana/.mozilla/firefox/9d1aipeq.default/xpti.dat': Input/output error
chown: changing ownership of `/home/ana/.mozilla/firefox/9d1aipeq.default/mimeTypes.rdf': Input/output error
chown: changing ownership of `/home/ana/.mozilla/firefox/9d1aipeq.default/search.json': Input/output error
chown: changing ownership of `/home/ana/.mozilla/firefox/9d1aipeq.default/compreg.dat': Input/output error
chown: changing ownership of `/home/ana/.mozilla/firefox/9d1aipeq.default/chrome/userChrome-example.css': Input/output error
chown: changing ownership of `/home/ana/.mozilla/firefox/9d1aipeq.default/chrome/userContent-example.css': Input/output error
```

In addition to this, terminal seems incapable of make install of anything, which is making the whole situation even more infuriating.

I have the exact issue as Butterknife had and have been.....to say the least, lost as to the cause.  From the thread, it seams lovinglinux is th master of Firefox issues and 2, solved the issue for Butterknife via PM.

Could use the same info for my wonderful FF problem.   

My problem is outlined in the following:

[http://ubuntuforums.org/showthread.php?p=8634026#post8634026](http://ubuntuforums.org/showthread.php?p=8634026#post8634026)

Pre-thanx for any time you all take looking into it.

---

### Post by gonzalez01 on 2010-01-08
[B]Hello friends!
[/B]I want to invite you all to play with me at [**EterniaGames LastChaos - EterniaGames.com**]("http://lastchaos.eterniagames.com/").
**EGLastChaos, powered by EterniaGames is an unique private server of LAST CHAOS.**

If you want to join me in this great game, or you want to join one of the other games that EterniaGames.com has, 
please click on the following links:
**Main Site: [http://eterniagames.com]("http://eterniagames.com/")**
**Forums: [http://forum.eterniagames.com]("http://forum.eterniagames.com/")**
**Game Site: [http://lastchaos.eterniagames.com]("http://lastchaos.eterniagames.com/")**

**Note:**
This message was provided by "EGLastChaos" to be used in our advertising system.
We take no responsibility for the misuse of this system.

---

### Post by dbruce100 on 2010-01-08
> **AridWarrior said:**
> ```
sudo chown -R $USER:$USER ~/.mozilla
```

did not work. 

The folder ~/.mozilla is not getting created when I run firefox from the panel or when I just run 

```
**firefox**
```

in the terminal.

I can see the folder that I renamed i.e. ~/.mozilla_OLD but that's it.

The folder ~/.mozilla gets created when I run

```
**sudo firefox**
```

but then only root has access to the folder.

The above is the identical issue I have.  I did an upgrade, so starting from scratch would be a challenge.

There has to be a permission issue somewhere.  In my case, I did an upgrade from 9.04 to 9.10......so there is a strange bug somewhere causing this.

---

### Post by Arwen17evenstar on 2010-01-09
I have a tiny, but annoying problem. 
I don't know if it's firefox or something I'm doing.

Sometimes when I start to type in Firefox's address bar, it acts like it's in some kind of insert or overtype mode. I can't type anything past 1 letter because it types over the top of the previous letter.

I've only ever had this happen in the address bar and only in ubuntu, no other OS.
Why is it doing this and how do I make it stop?

---

### Post by zika on 2010-01-09
> **Arwen17evenstar said:**
> I have a tiny, but annoying problem. 
I don't know if it's firefox or something I'm doing.

Sometimes when I start to type in Firefox's address bar, it acts like it's in some kind of insert or overtype mode. I can't type anything past 1 letter because it types over the top of the previous letter.

I've only ever had this happen in the address bar and only in ubuntu, no other OS.
Why is it doing this and how do I make it stop?Autocompletion?

---

### Post by lovinglinux on 2010-01-09
> **Arwen17evenstar said:**
> I have a tiny, but annoying problem. 
I don't know if it's firefox or something I'm doing.

Sometimes when I start to type in Firefox's address bar, it acts like it's in some kind of insert or overtype mode. I can't type anything past 1 letter because it types over the top of the previous letter.

I've only ever had this happen in the address bar and only in ubuntu, no other OS.
Why is it doing this and how do I make it stop?

I saw this before, but I don't remember if there was a solution. Try the suggestion from the post above and [this](http://ubuntuforums.org/showpost.php?p=1113542&postcount=2).

---

### Post by cmcanulty on 2010-01-09
Wow that fixed mine, was driving me nuts. Is there any tutorial that tells about all the settings in abou:config? Thanks

---

### Post by lovinglinux on 2010-01-09
> **cmcanulty said:**
> Wow that fixed mine, was driving me nuts. Is there any tutorial that tells about all the settings in abou:config? Thanks

Which one, which problem? 

There are several tutorials out there, covering different parts of the about:config. If you want all of them, then visit:

```
http://kb.mozillazine.org/the_name_of_the_preference
```

Where **the_name_of_the_preference** is the name of the preference you want more info. For example:

```
http://kb.mozillazine.org/Browser.sessionstore.enabled
```

---

### Post by schmolch on 2010-01-10
I get alot of horizontal lines in FF when i scroll webpages.
Does anyone know anything about this issue?

---

### Post by lovinglinux on 2010-01-10
> **schmolch said:**
> I get alot of horizontal lines in FF when i scroll webpages.
Does anyone know anything about this issue?

Got to the Advanced preferences tab and disable smooth scrolling. See if that helps.

---

### Post by schmolch on 2010-01-10
> **lovinglinux said:**
> Got to the Advanced preferences tab and disable smooth scrolling. See if that helps.

No it doesn't.
Smooth scrolling is already disabled, with it being enabled scrolling is practically impossible its that slow.

I openend a bug-report here:
[https://bugzilla.mozilla.org/show_bug.cgi?id=538843](https://bugzilla.mozilla.org/show_bug.cgi?id=538843)

---

### Post by lovinglinux on 2010-01-10
> **schmolch said:**
> No it doesn't.
Smooth scrolling is already disabled, with it being enabled scrolling is practically impossible its that slow.

I openend a bug-report here:
[https://bugzilla.mozilla.org/show_bug.cgi?id=538843](https://bugzilla.mozilla.org/show_bug.cgi?id=538843)

Do you have Compiz enabled and the proper video card driver installed? I think this is more a video driver issue than a Firefox issue.

---

### Post by schmolch on 2010-01-10
> **lovinglinux said:**
> Do you have Compiz enabled and the proper video card driver installed? I think this is more a video driver issue than a Firefox issue.

No Compiz, using the prop. Nvidia-Driver.
Im not having this Issue with any other Browser, so it has to be FFs fault.

---

### Post by linux_paul on 2010-01-10
After the latest firefox update I can't view videos on [www.hulu.com](www.hulu.com). Before yesterdays update everything worked fine. Running 64bit Ubuntu, Flash verison 10.0 r42. Any ideas?

These are the packages that were upgraded:```

firefox 3.5.6+nobinonly-0ubuntu0.9.10.1 => 3.5.7+nobinonly-0ubuntu0.9.10.1
    firefox-3.0 3.5.6+nobinonly-0ubuntu0.9.10.1 => 3.5.7+nobinonly-0ubuntu0.9.10.1
    firefox-3.0-branding 3.5.6+nobinonly-0ubuntu0.9.10.1 => 3.5.7+nobinonly-0ubuntu0.9.10.1
    firefox-3.0-gnome-support 3.5.6+nobinonly-0ubuntu0.9.10.1 => 3.5.7+nobinonly-0ubuntu0.9.10.1
    firefox-3.5 3.5.6+nobinonly-0ubuntu0.9.10.1 => 3.5.7+nobinonly-0ubuntu0.9.10.1
    firefox-3.5-branding 3.5.6+nobinonly-0ubuntu0.9.10.1 => 3.5.7+nobinonly-0ubuntu0.9.10.1
    firefox-3.5-gnome-support 3.5.6+nobinonly-0ubuntu0.9.10.1 => 3.5.7+nobinonly-0ubuntu0.9.10.1
    firefox-gnome-support 3.5.6+nobinonly-0ubuntu0.9.10.1 => 3.5.7+nobinonly-0ubuntu0.9.10.1
    libsmbclient 2:3.4.0-3ubuntu5.1 => 2:3.4.0-3ubuntu5.3
    libwbclient0 2:3.4.0-3ubuntu5.1 => 2:3.4.0-3ubuntu5.3
    samba-common 2:3.4.0-3ubuntu5.1 => 2:3.4.0-3ubuntu5.3
    samba-common-bin 2:3.4.0-3ubuntu5.1 => 2:3.4.0-3ubuntu5.3
    smbclient 2:3.4.0-3ubuntu5.1 => 2:3.4.0-3ubuntu5.3
    xulrunner-1.9.1 1.9.1.6+nobinonly-0ubuntu0.9.10.1 => 1.9.1.7+nobinonly-0ubuntu0.9.10.1
    xulrunner-1.9.1-gnome-support 1.9.1.6+nobinonly-0ubuntu0.9.10.1 =>
+1.9.1.7+nobinonly-0ubuntu0.9.10.1

```

---

### Post by lovinglinux on 2010-01-10
> **linux_paul said:**
> After the latest firefox update I can't view videos on [www.hulu.com](www.hulu.com). Before yesterdays update everything worked fine. Running 64bit Ubuntu, Flash verison 10.0 r42. Any ideas?


Remove the flash plugin and install it again following [these instructions](http://ubuntuforums.org/showthread.php?t=1358591).

---

### Post by linux_paul on 2010-01-10
> **lovinglinux said:**
> Remove the flash plugin and install it again following [these instructions](http://ubuntuforums.org/showthread.php?t=1358591).That installs the same version I currently have just to a different location (mine was in ~/.mozilla/plugins). I tried it anyway but still hulu will still not play :confused: youtube plays fine. 

The error hulu gives is **Sorry we are unable to stream this video. Please check your Internet connection and try again.** Using Internet Explorer in a Windows XP virtualbox environment hulu plays just fine.

Thanks for the quick reply, any other ideas?

---

### Post by altp on 2010-01-10
I have the _exact_ same problem as linux_paul.  I'm running 64-bit Kubuntu 9.10 with 64-bit flash alpha installed from Adobe Labs and Hulu worked perfectly until I upgraded the other day to Firefox 3.5.7 that was released into the repository.  Now I cannot view Hulu (it gives the same error) and I cannot for the life of me figure out a solution.

I would consider downgrading to Firefox 3.5.6 but I can't find the package anywhere.

---

### Post by linux_paul on 2010-01-10
Is there a way to enable rollbacks of updates?

---

### Post by altp on 2010-01-10
I think the problem is somehow related to 64-bit flash.  The Hulu Technical Issues Forum has a thread related to this exact problem and one of the members mentioned that testing with 32-bit flash worked, whereas the 64-bit flash did not.

[edit]
I just tested it myself by removing 64-bit flash and installing flashplugin-installer and it indeed does solve my problems.  Not a favorable solution since I prefer native 64-bit flash, but it'll have to do for now unfortunately..

---

### Post by linux_paul on 2010-01-10
> **altp said:**
> 
I just tested it myself by removing 64-bit flash and installing flashplugin-installer and it indeed does solve my problems.  Not a favorable solution since I prefer native 64-bit flash, but it'll have to do for now unfortunately..
I tried too and the video plays fine it just won't go fullscreen and none of the 'features' work like popout, pause, etc...

---

### Post by SamsLembas on 2010-01-10
I can confirm this analysis. I get the error in both Firefox and Chromium under x64 Arch Linux with native Flash. On a different computer running the same software stack in 32-bit, everything works. Ditto under 64-bit Win7 with native flash on the first computer, so the problem does seem to be Linux-specific.

---

### Post by ds3 on 2010-01-10
I am also getting the "Sorry, we are unable to stream this video. Please check your Internet connection and try again." message from Hulu since updating to Firefox 3.5.7 on 64 bit Ubuntu. I am using the beta version of the 64 bit Flash player 10.0 r32 from Adobe and it works fine everywhere else, and worked on Hulu prior to the update. I am using a dual boot machine with a shared Firefox profile and Hulu plays fine on Windows with the same shared Firefox 3.5.7 profile. They do use different versions of Flash, but this version of Flash used to work in Linux with Hulu. 

I thought this error message was usually related to not being in a country Hulu streamed to. Is this definitely a Flash problem rather than some strange Firefox setup in Ubuntu or proxy that makes Hulu misread the location?

Thanks.

---

### Post by ds3 on 2010-01-10
Incidentally, you should be able to roll back to Firefox 3.5.3 if you really want to. You can do this from Synaptic using the "force version" option in the "Package" menu. Firefox 3.5.3 is listed because it is the base version with Ubuntu Karmic, but I don't know where to find 3.5.6.

---

### Post by linux_paul on 2010-01-11
I tried the Synaptic method of rolling back but Help > About still says 3.5.7.

---

### Post by vood on 2010-01-11
i have been having problem trying to watch hulu videos, whenever i got to hulu and try to watch a video i get a message saying "sorry, we are unable to stream this video. please check you connection and try again" fro what i hear this usaly a message given to people who do not live in the US... the only issue im having with this is that i do live in the US and i have been able to view hulu videos till about 3 or 4 days ago... if any one have any ideas about what could have happened or a way to fix it i would appreciate the help.

---

### Post by kazik on 2010-01-11
vood, this seems to be a widespread issue with 64-bit Flash in Linux:

[http://www.hulu.com/discussions/9/110036/495965](http://www.hulu.com/discussions/9/110036/495965)

Hulu suddently stopped working with 64-bit Flash on January 9th. It still works in my Kubuntu Karmic (which uses 32-bit Flash).

---

### Post by vood on 2010-01-11
> **kazik said:**
> vood, this seems to be a widespread issue with 64-bit Flash in Linux:

[http://www.hulu.com/discussions/9/110036/495965](http://www.hulu.com/discussions/9/110036/495965)

Hulu suddently stopped working with 64-bit Flash on January 9th. It still works in my Kubuntu Karmic (which uses 32-bit Flash).

ah thank you... it still sucks but at leas i know im not alone in this

---

### Post by linux_paul on 2010-01-11
Just for the sake of trying I installed huludesktop 64bit for ubuntu to see if it has issues. I was suprised to see the video start to play, but was disappointed by another error message: **We're sorry, currently our video library is only available within the United States. You can continue to browse our library or choose one of the following options.** I live in the US. I just found it odd that the video would play at all, unlike the website. Still I submitted an error with the service to hulu.

---

### Post by linux_paul on 2010-01-11
I was just trying huludesktop again, this time turning webcontentcontrol protection off and it works just fine. This may we a useful workaround while the website wont play.

---

### Post by lovinglinux on 2010-01-11
> **linux_paul said:**
> I was just trying huludesktop again, this time turning webcontentcontrol protection off and it works just fine. This may we a useful workaround while the website wont play.

Thanks for the heads up. I don't have access to Hulu, because I live outside US, but this is a very popular subject and lots of users will benefit from this info.

---

### Post by SilverWave on 2010-01-12
A new command in Karmic makes it easy to add a PPA repository and its  key, all at once.
 **Firefox 3.6 & 3.7** Available via daily ppa

 **Gain access to the latest [ubuntu-mozilla-daily]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa?field.series_filter=") ppa.**
     ```
sudo add-apt-repository ppa:ubuntu-mozilla-daily 
```**Now install Firefox as below** (or via the Synaptic Package  Manager).
     ```
sudo apt-get update
sudo apt-get install firefox-3.6
sudo apt-get install firefox-3.7 
```These packages install in their own directories so you can use    3.5/3.6/3.7 side by side.
The new FF3.6 will be found under the name "Namoroka" in Applications  > Internet.
The new FF3.7 will be found under the name "Minefield 3.7 Web Browser".

More detail here:
[Install The Newest Firefox ppa with command "add-apt-repository" (9.10 & above)]("http://ubuntuforums.org/showthread.php?p=8482673")
[Taming ubuntu-mozilla-daily with Pin-Priority: 400]("http://ubuntuforums.org/showpost.php?p=8636047&postcount=36")

I'm running 3.6pre and 3.7a1 - both working fine :)

---

### Post by lovinglinux on 2010-01-12
> **SilverWave said:**
> A new command in Karmic makes it easy to add a PPA repository and its  key, all at once.
 **Firefox 3.6 & 3.7** Available via daily ppa

 **Gain access to the latest [ubuntu-mozilla-daily]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa?field.series_filter=") ppa.**
     ```
sudo add-apt-repository ppa:ubuntu-mozilla-daily 
```**Now install Firefox as below** (or via the Synaptic Package  Manager).
     ```
sudo apt-get update
sudo apt-get install firefox-3.6
sudo apt-get install firefox-3.7 
```These packages install in their own directories so you can use    3.5/3.6/3.7 side by side.
The new FF3.6 will be found under the name "Namoroka" in Applications  > Internet.
The new FF3.7 will be found under the name "Minefield 3.7 Web Browser".

More detail here:
[Install The Newest Firefox ppa with command "add-apt-repository" (9.10 & above)]("http://ubuntuforums.org/showthread.php?p=8482673")
[Taming ubuntu-mozilla-daily with Pin-Priority: 400]("http://ubuntuforums.org/showpost.php?p=8636047&postcount=36")

I'm running 3.6pre and 3.7a1 - both working fine :)

I still prefer to download from Mozilla and install manually or use Ubuntuzilla. I'm running 3.6rc1 while ubuntu-mozilla-daily still has 3.6pre, which seems to be a beta.

Additionally, some user are not aware that the PPA keeps updating with unstable versions even after the final release. There were some users experiencing problems after the final release of Shiretoko because they had the PPA. Anyway, it wasn't anything serious, just a little annoyance, fixed by removing firefox, xulrunner, the PPA and then installing it again.

---

### Post by SilverWave on 2010-01-12
> **lovinglinux said:**
> I still prefer to download from Mozilla and install manually or use Ubuntuzilla. I'm running 3.6rc1 while ubuntu-mozilla-daily still has 3.6pre, which seems to be a beta.


I think this is the RC - soon to be 3.6.0:... (Now:firefox-3.6                                                3.6~hg, Previously:firefox-3.6     3.6~b6~hg).


> **lovinglinux said:**
> 
Additionally, some user are not aware that the PPA keeps updating with unstable versions even after the final release. ...


... funny you should say that... here is my solution:


> **Pinning the  ubuntu-mozilla-daily PPA**

 "I regularly use a package from  the Ubuntu Daily Mozilla PPA. Unfortunately the PPA also contains  snapshot builds of Firefox 3.5 and [XulRunner]("https://help.ubuntu.com/community/XulRunner") 1.9.1,  which I want to keep at their standard Ubuntu versions". 
The Pinning Solution 
To make  apt-get upgrading as painless as possible set a lower Pin-Priority on  the PPA, this will stop unwanted package versions from installing. Once  set,** packages from the ubuntu-mozilla-daily PPA will always lose in any  contest with packages from other repositories, even if they have a  higher version. **
Create the  file: 

[LIST=1]
[*]/etc/apt/preferences.d/ubuntu-mozilla-daily-pin-400
[*]Add the following to the file:
[/LIST]
```
Package: *
Pin: release o=LP-PPA-ubuntu-mozilla-daily
Pin-Priority: 400
```Use the  following commands, before and after, to check that the Pin-Priority has  been updated. 

apt-cache policy
apt-cache policy firefox-3.5
apt-cache policy firefox-3.6
More details: 
[Taming ubuntu-mozilla-daily with Pin-Priority: 400]("http://ubuntuforums.org/showpost.php?p=8636047&postcount=36")


Actually the way I have it set up...
The ubuntu-mozilla-security PPA  will give me any security updates straight away on "Standard Packages I  don't want to mess with", e.g. Firefox-3.5.

Then the  ubuntu-mozilla-daily PPA gives me access to any new shiny toys that are  out from Mozilla but not in the Official Karmic repositories. But as it  has been pinned to 400, if say 3.6 ever does show up in Karmic, then I  should automatically switch over to that version... or at least that is  the theory :)

Also these packages install in their own  directories so you can use 3.6/3.7 side by side and they are 64bit! 

Having  Cake and eating it too :)
Also the defaults on Karmic are to only  offer updates each week so I shouldn't be too bugged by the daily  builds...
Anyway with 3.6 just around the corner I have the perfect  opportunity to test it.

Cheers!

---

### Post by lovinglinux on 2010-01-12
Interesting.

---

### Post by Arwen17evenstar on 2010-01-13
> **Arwen17evenstar said:**
> I have a tiny, but annoying problem. 
I don't know if it's firefox or something I'm doing.

Sometimes when I start to type in Firefox's address bar, it acts like it's in some kind of insert or overtype mode. I can't type anything past 1 letter because it types over the top of the previous letter.

I've only ever had this happen in the address bar and only in ubuntu, no other OS.
Why is it doing this and how do I make it stop?

> **zika said:**
> Autocompletion?

> **lovinglinux said:**
> I saw this before, but I don't remember if there was a solution. Try the suggestion from the post above and this.

I have that turned on in firefox, you think that's causing the problem? 
I like it highlighting the whole thing so I can delete it very quickly.

---

### Post by lovinglinux on 2010-01-13
> **Arwen17evenstar said:**
> I have that turned on in firefox, you think that's causing the problem? 
I like it highlighting the whole thing so I can delete it very quickly.

Maybe.

---

### Post by friv_livs on 2010-01-13
How do I tell firefox 3.5 to replace spaces in downloaded files with _ instead of %20?

Thanks in advance,

Friv

---

### Post by misha680 on 2010-01-19
Dear All:

I am having the following error compiling Firefox 3.5 with PGO:
```

ake[1]: Leaving directory `/home/misha/mozilla-1.9.1'
OBJDIR=/home/misha/mozilla-1.9.1/obj-x86_64-unknown-linux-gnu python /home/misha/mozilla-1.9.1/obj-x86_64-unknown-linux-gnu/_profile/pgo/profileserver.py
INFO | (automation.py) | Application pid: 18203
TEST-UNEXPECTED-FAIL | (automation.py) | Exited with code -11 during test run
INFO | (automation.py) | Application ran for: 0:00:00.081871
make: *** [profiledbuild] Error 245

```

It seems per 
[http://forums.mozillazine.org/viewtopic.php?f=42&t=1276355](http://forums.mozillazine.org/viewtopic.php?f=42&t=1276355)
to have the solution of installing gcc 4.5. I am on Ubuntu Hardy Heron 8.04 amd64

Is this version available somewhere by any chance?

I have a significant improvement in performance for PGO firefox 3.0 vs non-PGO (also compiled) firefox 3.0

I used, for the non-PGO firefox 3.0 the following flags:
```

ac_add_options --enable-official-branding
    export CHOST="i686-pc-linux-gnu"
    export CFLAGS="-O3 -march=native -pipe -fomit-frame-pointer"
    export CXXFLAGS="-O3 -march=native -pipe -fomit-frame-pointer"
    export CPPFLAGS="-O3 -march=native -pipe -fomit-frame-pointer"

```

I have a Core 2 Duo processor T7800
```

cat /proc/cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     T7800  @ 2.60GHz
stepping	: 11
cpu MHz		: 800.000
cache size	: 4096 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm ida
bogomips	: 5185.51
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     T7800  @ 2.60GHz
stepping	: 11
cpu MHz		: 800.000
cache size	: 4096 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm ida
bogomips	: 5185.56
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

```

Per
[http://www.thinkwiki.org/wiki/Intel_Core_2_Duo](http://www.thinkwiki.org/wiki/Intel_Core_2_Duo)
"Alternatively, as of gcc 4.2, the "native" argument is supported. This will automatically determine the cpu-type on which compilation is taking place and apply optimisations specific to that cpu. "

and my gcc version:
```
gcc --version
gcc (GCC) 4.2.4 (Ubuntu 4.2.4-1ubuntu4)
Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

Any help much appreciated!

Thank you
Misha

---

### Post by misha680 on 2010-01-19
Compiling without PGO using the following .mozconfig:
```

    . $topsrcdir/browser/config/mozconfig
export MOZILLA_OFFICIAL=1
export BUILD_OFFICIAL=1
mk_add_options MOZILLA_OFFICIAL=1
mk_add_options BUILD_OFFICIAL=1
mk_add_options MOZ_OBJDIR=@TOPSRCDIR@/obj-@CONFIG_GUESS@
ac_add_options --enable-official-branding
    export CHOST="i686-pc-linux-gnu"
    export CFLAGS="-O3 -march=native -pipe -fomit-frame-pointer"
    export CXXFLAGS="-O3 -march=native -pipe -fomit-frame-pointer"
    export CPPFLAGS="-O3 -march=native -pipe -fomit-frame-pointer"

ac_add_options --enable-application=browser
mk_add_options MOZ_CO_PROJECT=browser
ac_add_options --enable-optimize 
ac_add_options --enable-default-toolkit=cairo-gtk2
ac_add_options --enable-xft
ac_add_options --enable-extensions=default
ac_add_options --enable-strip
ac_add_options --enable-install-strip
ac_add_options --enable-pango
ac_add_options --enable-svg
ac_add_options --enable-canvas
ac_add_options --disable-tests
ac_add_options --disable-accessibility
ac_add_options --disable-mochitest
ac_add_options --disable-debug
ac_add_options --disable-installer
ac_add_options --disable-crashreporter
ac_add_options --disable-parental-controls
ac_add_options --with-pthreads

```

I get the following error:
```

rm -f libxremote_client_s.a
ar cr libxremote_client_s.a XRemoteClient.o  
ranlib libxremote_client_s.a
mozilla-xremote-client.cpp
c++ -o mozilla-xremote-client.o -c -I../../../dist/include/system_wrappers -include /home/misha/mozilla-1.9.1/config/gcc_hidden.h -DOSTYPE=\"Linux2.6\" -DOSARCH=Linux  -I/home/misha/mozilla-1.9.1/widget/src/xremoteclient -I. -I../../../dist/include/xpcom -I../../../dist/include   -I../../../dist/include/xremoteclient -I/home/misha/mozilla-1.9.1/obj-x86_64-unknown-linux-gnu/dist/include/nspr    -I/home/misha/mozilla-1.9.1/obj-x86_64-unknown-linux-gnu/dist/sdk/include    -fPIC  -O3 -march=native -pipe -fomit-frame-pointer  -fno-rtti -fno-exceptions -Wall -Wpointer-arith -Woverloaded-virtual -Wsynth -Wno-ctor-dtor-privacy -Wno-non-virtual-dtor -Wcast-align -Wno-invalid-offsetof -Wno-long-long -pedantic -O3 -march=native -pipe -fomit-frame-pointer -fno-strict-aliasing -fshort-wchar -pthread -pipe  -DNDEBUG -DTRIMMED -Os -freorder-blocks -fno-reorder-functions -finline-limit=50  -O3 -march=native -pipe -fomit-frame-pointer  -DMOZILLA_CLIENT -include ../../../mozilla-config.h -Wp,-MD,.deps/mozilla-xremote-client.pp /home/misha/mozilla-1.9.1/widget/src/xremoteclient/mozilla-xremote-client.cpp
c++ -o mozilla-xremote-client -O3 -march=native -pipe -fomit-frame-pointer  -fno-rtti -fno-exceptions -Wall -Wpointer-arith -Woverloaded-virtual -Wsynth -Wno-ctor-dtor-privacy -Wno-non-virtual-dtor -Wcast-align -Wno-invalid-offsetof -Wno-long-long -pedantic -O3 -march=native -pipe -fomit-frame-pointer -fno-strict-aliasing -fshort-wchar -pthread -pipe  -DNDEBUG -DTRIMMED -Os -freorder-blocks -fno-reorder-functions -finline-limit=50  mozilla-xremote-client.o XRemoteClient_standalone.o     -lpthread   -Wl,-rpath-link,/home/misha/mozilla-1.9.1/obj-x86_64-unknown-linux-gnu/dist/bin -Wl,-rpath-link,/usr/local/lib  -L../../../dist/bin -L../../../dist/lib -L/home/misha/mozilla-1.9.1/obj-x86_64-unknown-linux-gnu/dist/lib -lplds4 -lplc4 -lnspr4 -lpthread -ldl  -lX11  -lasound -ldl -lm      
XRemoteClient_standalone.o: In function `global constructors keyed to 0__ZN13XRemoteClientC2Ev':
XRemoteClient.cpp:(.text+0x1e50): undefined reference to `__gcov_init'
XRemoteClient_standalone.o:(.data.rel+0x48): undefined reference to `__gcov_merge_add'
collect2: ld returned 1 exit status
make[4]: *** [mozilla-xremote-client] Error 1
make[4]: Leaving directory `/home/misha/mozilla-1.9.1/obj-x86_64-unknown-linux-gnu/widget/src/xremoteclient'
make[3]: *** [libs_tier_toolkit] Error 2
make[3]: Leaving directory `/home/misha/mozilla-1.9.1/obj-x86_64-unknown-linux-gnu'
make[2]: *** [tier_toolkit] Error 2
make[2]: Leaving directory `/home/misha/mozilla-1.9.1/obj-x86_64-unknown-linux-gnu'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/misha/mozilla-1.9.1/obj-x86_64-unknown-linux-gnu'
make: *** [build] Error 2

```

Thank you!

Misha

---

### Post by misha680 on 2010-01-19
Also per this thread
[http://ubuntuforums.org/showthread.php?t=1344962](http://ubuntuforums.org/showthread.php?t=1344962)

Compiling gcc from svn I get the following error:
```

checking how to compare bootstrapped objects... cmp --ignore-initial=16 $$f1 $$f2
checking for objdir... .libs
checking for correct version of gmp.h... yes
checking for correct version of mpfr.h... buggy but acceptable
checking for the correct version of mpc.h... no
configure: error: Building GCC requires GMP 4.2+, MPFR 2.3.2+ and MPC 0.8.0+.
Try the --with-gmp, --with-mpfr and/or --with-mpc options to specify
their locations.  Source code for these libraries can be found at
their respective hosting sites as well as at
ftp://gcc.gnu.org/pub/gcc/infrastructure/.  See also
http://gcc.gnu.org/install/prerequisites.html for additional info.  If
you obtained GMP, MPFR and/or MPC from a vendor distribution package,
make sure that you have installed both the libraries and the header
files.  They may be located in separate packages.
make: *** No targets specified and no makefile found.  Stop.
make: *** No targets specified and no makefile found.  Stop.

```

Thank you!

---

### Post by turboopugsleylx on 2010-01-19
> [COLOR=#cc0000][SIZE=4]Flash Tweaks[/SIZE][/COLOR]

Some people [reported]("http://ubuntuforums.org/showpost.php?p=7279173&postcount=14") improvements doing this ([original source]("http://blogs.adobe.com/penguin.swf/2008/08/secrets_of_the_mmscfg_file_1.html")):

 	Code:
 	sudo mkdir /etc/adobe
*echo* "*OverrideGPUValidation*=true" >~/mms.cfg
sudo mv ~/mms.cfg /etc/adobe/ 
 	Quote:
 	 	 		 			 				**[COLOR=DarkRed]Note:[/COLOR]** it seems the above tweak only works for YouTube, but it works great. 			 		



Question...this tweak is great....how can I also make this work for my windows system as well? anyone?

---

### Post by lovinglinux on 2010-01-19
@ misha680

I have given up compiling myself since 3.5.x due to those compiling errors. I will be glad to update the tutorial if you find a solution.

@ turboopugsleylx

Don't know how to do that on Windows.

---

### Post by misha680 on 2010-01-19
> **lovinglinux said:**
> @ misha680

I have given up compiling myself since 3.5.x due to those compiling errors. I will be glad to update the tutorial if you find a solution.

@ turboopugsleylx

Don't know how to do that on Windows.

Thank you so much. I am somewhat confused I used this link:
[ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/3.5/source/firefox-3.5-source.tar.bz2](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/3.5/source/firefox-3.5-source.tar.bz2)

That you reference in your tutorial. Is this not the version you yourself compiled? Is the difference Hardy vs later versions of Ubuntu or something else?

Thank you

Sincerely yours
Misha

---

### Post by lovinglinux on 2010-01-19
> **misha680 said:**
> Thank you so much. I am somewhat confused I used this link:
[ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/3.5/source/firefox-3.5-source.tar.bz2](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/3.5/source/firefox-3.5-source.tar.bz2)

That you reference in your tutorial. Is this not the version you yourself compiled? Is the difference Hardy vs later versions of Ubuntu or something else?

Thank you

Sincerely yours
Misha

No, there is no difference between Hardy vs later versions of Ubuntu when you download the source code. Such difference only exists on packages distributed with Ubuntu, which are optimized form each OS version.

The link is correct. That version was the one I have compiled myself, but I wasn't able to do it later on, with version 3.5.6 if I remember correctly.

I never tried to compile for 64bit tho. So I don't know if there was any problems compiling that version for your platform.

---

### Post by misha680 on 2010-01-19
> **lovinglinux said:**
> No, there is no difference between Hardy vs later versions of Ubuntu when you download the source code. Such difference only exists on packages distributed with Ubuntu, which are optimized form each OS version.

The link is correct. That version was the one I have compiled myself, but I wasn't able to do it later on, with version 3.5.6 if I remember correctly.

I never tried to compile for 64bit tho. So I don't know if there was any problems compiling that version for your platform.

Thank you. So I guess I'm stuck since I can't compile the same version that you yourself successfully compiled (3.5) :(

Thank you
Misha

---

### Post by lovinglinux on 2010-01-19
> **misha680 said:**
> Thank you. So I guess I'm stuck since I can't compile the same version that you yourself successfully compiled (3.5) :(

Thank you
Misha

I wish I could help more, but I'm not an expert with compilation. I put that on the tutorial because it worked for me, but troubleshooting compilation errors is a different story.

Have you tried to use Swiftweasel or even Swiftfox? They are both optimized for different processors and use PGO, so the result would be the same. Keep in mind Swiftfox is not open source.

---

### Post by misha680 on 2010-01-19
> **lovinglinux said:**
> I wish I could help more, but I'm not an expert with compilation. I put that on the tutorial because it worked for me, but troubleshooting compilation errors is a different story.

Have you tried to use Swiftweasel or even Swiftfox? They are both optimized for different processors and use PGO, so the result would be the same. Keep in mind Swiftfox is not open source.

Thank you. Swiftweasel has an old Adblock Plus which caused too many ads for me to go through.

On the upside I used your instructions to compile Firefox 3.0 with PGO and it seems to work quite well!!!

Thank you
Misha

---

### Post by lovinglinux on 2010-01-19
> **misha680 said:**
> Thank you. Swiftweasel has an old Adblock Plus which caused too many ads for me to go through.

Swiftweasel is Firefox with a different brand, so there is no difference on the add-ons. You can run the same Firefox extensions on Swiftweasel.  

I don't know what you mean by Swiftweasel having an old Adblock Plus, since the extension doesn't come installed and as long as the Firefox/Swiftweasel version is compatible, Adblock Plus should install from Mozilla Add-ons site without issues. Even if there isn't a compatible version of an extension, which is the case for example for the new FF 3.6, you can override the extension compatibility check. There are a few tools to do that, but I recommend [Add-on Compatibility Reporter](https://addons.mozilla.org/en-US/firefox/addon/15003?src=external-fxfirstrun).

 Perhaps you forgot to update the extensions after installing Swiftweasel.

> **misha680 said:**
> Thank you. Swiftweasel has an old Adblock Plus which caused too many ads for me to go through.

On the upside I used your instructions to compile Firefox 3.0 with PGO and it seems to work quite well!!!

Thank you
Misha

I would recommend sticking with Swiftweasel, since the performance difference between Firefox 3.0 and Firefox 3.5 is huge. Swiftweasel will fly on your machine.

---

### Post by misha680 on 2010-01-19
Thank you. Actually at the moment Swiftweasel _does_ come with Adblock Plus built in.

And perhaps I was not clear - I was _only_ able to get Swiftweasel 3.0 to work, _not_ 3.5.

I am trying again for Firefox 3.5 compilation _without_ PGO with hardy's gcc-snapshot which is gcc 4.3.3. Keep your fingers crossed :)

Thank you!
Misha

p.s. So fyi with gcc-snapshot it compiles.

```
sudo aptitude install gcc-snapshot
```

You need to make edits in the mozconfig file like the following (this is where I pulled from)
[https://developer.mozilla.org/En/Compiling_Mozilla_With_Mingw](https://developer.mozilla.org/En/Compiling_Mozilla_With_Mingw)

```

CC=/usr/lib/gcc-snapshot/gcc
CXX=/usr/lib/gcc-snapshot/g++
CPP=/usr/lib/gcc-snapshot/cpp
AS=/usr/lib/gcc-snapshot/as
LD=/usr/lib/gcc-snapshot/ld

```

Unfortunately Firefox 3.5 has issues for me as it has other times when I actually managed to get it installed
(e.g., after a while the Google search button just stops working - in fact all links do :( )

I think I'll stick with Firefox 3.0 for now until there's a new LTS release. Thanks for all the info though. I did get Firefox 3.0 PGO which is _much_ faster!

---

### Post by dcstar on 2010-01-20
If anyone using FF 3.0.17 has suddenly found that the Ubuntu forums (and some other web sites) now have weird large fonts, chances are they are also using the Noscript add-on (version 1.9.9.36).

The fix is to install the current beta Noscript (1.9.9.39) from the Noscript home page and everything is back to normal...... :)

---

### Post by wojox on 2010-01-20
> **dcstar said:**
> If anyone using FF 3.0.17 has suddenly found that the Ubuntu forums (and some other web sites) now have weird large fonts, chances are they are also using the Noscript add-on (version 1.9.9.36).

The fix is to install the current beta Noscript (1.9.9.39) from the Noscript home page and everything is back to normal...... :)

People still use 3.0 ? geeez louise.

---

### Post by lovinglinux on 2010-01-20
> **misha680 said:**
> Thank you. Actually at the moment Swiftweasel _does_ come with Adblock Plus built in.

And perhaps I was not clear - I was _only_ able to get Swiftweasel 3.0 to work, _not_ 3.5.


You are right, it comes with Adblock Plus, but all you need to do is click "Find updates" to get the latest version.


> **misha680 said:**
> p.s. So fyi with gcc-snapshot it compiles.

```
sudo aptitude install gcc-snapshot
```

You need to make edits in the mozconfig file like the following (this is where I pulled from)
[https://developer.mozilla.org/En/Compiling_Mozilla_With_Mingw](https://developer.mozilla.org/En/Compiling_Mozilla_With_Mingw)

```

CC=/usr/lib/gcc-snapshot/gcc
CXX=/usr/lib/gcc-snapshot/g++
CPP=/usr/lib/gcc-snapshot/cpp
AS=/usr/lib/gcc-snapshot/as
LD=/usr/lib/gcc-snapshot/ld

```

Thanks for the heads up.

> **misha680 said:**
> Unfortunately Firefox 3.5 has issues for me as it has other times when I actually managed to get it installed
(e.g., after a while the Google search button just stops working - in fact all links do :( )

I think I'll stick with Firefox 3.0 for now until there's a new LTS release. Thanks for all the info though. I did get Firefox 3.0 PGO which is _much_ faster!

Have you tried Firefox 3.6rc2? The final version is about to be released and it is working great.

> **wojox said:**
> People still use 3.0 ? geeez louise.

I wouldn't be surprised if there is still people using FF 1.5, specially Windows users. :)

---

### Post by phillw on 2010-01-20
> **lovinglinux said:**
> 
Have you tried Firefox 3.6rc2? The final version is about to be released and it is working great.


I hope it is running better than 3.5.8rc that arrived from the daily build today and borked on my 9.10 installation. Had to back out the daily build repositry do a force remove and re-install of 3.5 :-\

Still, first time it's ever borked. I'm not too sure where they're up to with the 3.6rc - I had a quick look when it was first being used on the 10.04, they (mozilla) were talking about possibly several attempts at a 'final' rc candidate. I thought that such things should be called betas, but I guess it's only words !!!

Not to worry, by the time 10.04 settles down, 3.6 should be good to go :-)  I'll miss Shiretoko tho' it's been an rock solid install ever since it appeared all that time ago ! Yes, I know it FF without the branding - but I still like it - lol

Regards,

Phill.

---

### Post by lovinglinux on 2010-01-20
> **phillw said:**
> I hope it is running better than 3.5.8rc that arrived from the daily build today and borked on my 9.10 installation. Had to back out the daily build repositry do a force remove and re-install of 3.5 :-\

I don't get it from the daily ppa, but from Mozilla ftp site and install it manually, side-by-side with 3.5. It's working great here, aside from some random high CPU usage that occurs when closing it, which I suspect is due to some extension, since I'm overriding compatibility of several extensions.

---

### Post by dbruce100 on 2010-01-20
Didn't get a response last time, so try try again.

Updated to 9.10 from 9.04 and now Firefox only works with gksudo.  Haven't a clue, but assume the permissions are messed up somewhere since it shows up in the lower bar and then dies off.  Problem was originally on this thread.

Any file I can look at to see where is is failing?  I've been using Opera, which isn't much of a substitute.

---

### Post by dcstar on 2010-01-21
> **wojox said:**
> People still use 3.0 ? geeez louise.

Yep, something that actually still uses the Gnome font settings rather than ignore them (like FF 3.5).

I've tried to change over to 3.5 about 3 times now, but I'm sick of not having things that work correctly in 3.0.x

---

### Post by lovinglinux on 2010-01-21
I have updated the [COLOR="Sienna"]**Install Other Versions**[/COLOR] section of the tutorial, due to the release of Firefox 3.6.

---

### Post by SilverWave on 2010-01-22
Seen this an thought it may be of interest:

[Blueprint: desktop-lucid-new-firefox-support-model](https://wiki.ubuntu.com/DesktopTeam/Specs/Lucid/FirefoxNewSupportModel)

> **Use in-source  libraries rather than system libs**

 enabling  system libs is not officially supported upstream and supporting this  caused notable work in the past while sometimes leading to a suboptimal  user experience due to version variants in the ubuntu released compared  to the optimize version shipped in the firefox upstream tarballs. 

---

### Post by lovinglinux on 2010-01-22
> **SilverWave said:**
> Seen this an thought it may be of interest:

[Blueprint: desktop-lucid-new-firefox-support-model](https://wiki.ubuntu.com/DesktopTeam/Specs/Lucid/FirefoxNewSupportModel)

Yes it is. Thanks. But I don't understand all the jargon. Does that mean we might get new major releases on on stable Ubuntu versions?

---

### Post by SilverWave on 2010-01-22
> **lovinglinux said:**
> Yes it is. Thanks. But I don't understand all the jargon. Does that men we might get new major releases on on stable Ubuntu versions?

Yes it looks like a completely new support-model :)

[Prepare Firefox for Major-Minor Version upgrades](https://blueprints.launchpad.net/ubuntu/+spec/desktop-lucid-new-firefox-support-model)

> Mozilla moved to a monthly security update cycle early in 2009; next  step planned is to stop doing stable release branches for any  distro-relevant amount of time. For instance, they consider to release  firefox 3.6 as a minor update to firefox 3.5 and want to a 3-4 month  cycle for such minor-major version upgrades. Also it happens more  frequently now that they bump reqtuirements on system libs like cairo  and sqlite3 in minor version upgrades.
 This is in line with what is planned by chromium and it's unfeasible  to try to do our own stable release branch maintenance as this would  require far more resources than we can get at any point in the future.
 Instead we should prepare for what is coming and ensure that we can  follow major-minor version upgrades in a timely fashion.
 Main topics addressed by this blueprint are:
  1. how to prepare the firefox package so we can follow the  major-minor version upgrade path.
 2. how to deal with xulrunner reverse-dependencies


---

### Post by lovinglinux on 2010-01-22
> **SilverWave said:**
> Yes it looks like a completely new support-model :)

[Prepare Firefox for Major-Minor Version upgrades](https://blueprints.launchpad.net/ubuntu/+spec/desktop-lucid-new-firefox-support-model)

I guess this is why ubuntu-mozilla-daily is updating Firefox 3.5 with Firefox 3.6 instead of creating a side-by-side installation. Great news.

---

### Post by lovinglinux on 2010-01-22
Another interesting news.

> From: [http://www.computerworld.com/s/article/9147102/Mozilla_launches_Firefox_3.6_calls_it_world_s_best_browser_](http://www.computerworld.com/s/article/9147102/Mozilla_launches_Firefox_3.6_calls_it_world_s_best_browser_)

The appearance of Firefox 3.6 also starts the end-of-life clock ticking for Firefox 3.5; Mozilla's policy is to support an older edition for approximately six months after the launch of a successor, meaning the kill date for 3.5 will likely be in late July 2010. At or around that time, Mozilla will stop producing security patches for the older browser.

---

### Post by lovinglinux on 2010-01-22
I thought would be interesting to let other users know about this. 

[http://blog.mozilla.com/addons/2010/01/22/broken-executables-in-extensions-in-firefox-3-6/](http://blog.mozilla.com/addons/2010/01/22/broken-executables-in-extensions-in-firefox-3-6/)

The blog post is targeting developers, but if you find that an extension doesn't work even with compatibility check overridden, they might be because of this.

Basically, they changed the way how extensions are extracted during installation and due to some issues, any extracted executable loses the permission to be executed. This only affects extensions with executables included (binaries, bash scripts...) and should be fixed on Firefox 3.6.1.

If you want to fix this problem for a particular extension, then locate the executable in the extension folder and change the permission accordingly.

---

### Post by DanH 1970 on 2010-01-23
Hello,

I am an Ubuntu newbie, and I am having trouble installing firefox 3.6.  I performed the following steps per the instructions contained on another site:

1. To install from PPA, add the mozilla-daily PPA in the repository list.[INDENT]sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa
[/INDENT]2. Update the software list using the command[INDENT]sudo apt-get update
[/INDENT]3. Install Firefox 3.6 using the command[INDENT]sudo apt-get install firefox-3.6
[/INDENT]It seemed like everything went as planned, but when I restarted firefox and checked the version, it was still showing 3.5.7.

So I went to the Synaptic package manager, thinking maybe I should just uninstall firefox completely and then re-install.  But when I did this, it uninstalled 3.6 and left 3.5.7 intact as that's what I'm using to access this forum.

Any help is greatly appreciated.

UPDATE

I used Synaptic package manager to re-install firefox, and now apparently I'm using version 3.6.1 "Namoroka" which appears to be a pre-release.  I just want the stable version, LOL!

---

### Post by lovinglinux on 2010-01-23
> **DanH 1970 said:**
> Hello,

I am an Ubuntu newbie, and I am having trouble installing firefox 3.6.  I performed the following steps per the instructions contained on another site:

1. To install from PPA, add the mozilla-daily PPA in the repository list.[INDENT]sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa
[/INDENT]2. Update the software list using the command[INDENT]sudo apt-get update
[/INDENT]3. Install Firefox 3.6 using the command[INDENT]sudo apt-get install firefox-3.6
[/INDENT]It seemed like everything went as planned, but when I restarted firefox and checked the version, it was still showing 3.5.7.

So I went to the Synaptic package manager, thinking maybe I should just uninstall firefox completely and then re-install.  But when I did this, it uninstalled 3.6 and left 3.5.7 intact as that's what I'm using to access this forum.

Any help is greatly appreciated.

UPDATE

I used Synaptic package manager to re-install firefox, and now apparently I'm using version 3.6.1 "Namoroka" which appears to be a pre-release.  I just want the stable version, LOL!

You should read the Method Comparisons in the Install Other Versions section, because it explains the differences of each installation method in details.

Anyway, here is the deal. When you use the PPA, you get not only final releases but also alphas, betas, pre-releases and so on. So they already have the next version available, which is 3.6.1. Additionally, the browser is named Namaroka, which is the codename of Firefox 3.6. 

If you simply add the PPA  and just update, then it replaces firefox-3.5 package with the Firefox 3.6.1pre binaries. But you can also install side-by-side with firefox-3.5, as you did initially, by manually installing firefox-3.6 package.

If you are running 64bit, that is the recommended method. If you are running 32bit and don't want to get alphas, betas and pre-releases, then method #2 (Ubuntuzilla) is the recommended. Is the best option to keep Firefox in sync with Mozilla releases.

If you want that, disable the *ubuntu-mozilla-daily* PPA from "System >> Administration >> Software Sources" then remove Firefox completely, then install the firefox package. This will put the default firefox (3.5.7) back in place. Then go to [Ubuntuzilla](http://ubuntuzilla.wiki.sourceforge.net/) and add their PPA and follow their installation instructions. It will install another version of Firefox, side-by-side with the default one. But this version will have Firefox logo, Firefox name and will be version 3.6, not 3.6.1pre. When using Ubuntuzilla you also get updates, but only final stable releases, as you want.

---

### Post by SilverWave on 2010-01-23
**Re: ubuntu-mozilla-daily**
From my testing you now can't run firefox-3.6 side-by-side with 3.5 as you could up to a couple of days ago.

When I saw a transition package being created on the UMD PPA I thought I had best test.
I reverted my system back to the Official Firefox-3.5 package and tried installing firefox-3.6, I found that things had indeed changed, as I only received the dummy package not Firefox-3.6.

From the testing I have done the following works...

> **SilverWave said:**
> **Everything is Changing**
[COLOR=RoyalBlue]OK the old instructions, noted in the last post,  may no longer work as things have changed.[/COLOR][COLOR=Blue]
[/COLOR] This is because Firefox-3.6 is now considered to be a minor  version upgrade to 3.5 and the Ubuntu Mozilla Daily PPA packages have  been rebuilt to reflect this. :)
[B]
New Firefox 3.6 Installation Instructions[/B] (Karmic).
     ```

sudo add-apt-repository ppa:ubuntu-mozilla-daily

```  **Now install Firefox as below** (or via the Synaptic  Package  Manager).
     ```

sudo apt-get update
sudo apt-get install firefox-3.5
```For full details and notes go [here]("http://ubuntuforums.org/showthread.php?p=8708092#post8708092").
________________________________________________


as does "sudo apt-get install firefox"

Checkout post #[43]("http://ubuntuforums.org/showthread.php?p=8708092#post8708092") for the latest news.

The last posters experience tends to bare this out.

---

### Post by lovinglinux on 2010-01-23
> **SilverWave said:**
> **Re: ubuntu-mozilla-daily**
From my testing you now can't run firefox-3.6 side-by-side with 3.5 as you could up to a couple of days ago.

When I saw a transition package being created on the UMD PPA I thought I had best test.
I reverted my system back to the Official Firefox-3.5 package and tried installing firefox-3.6, I found that things had indeed changed, as I only received the dummy package not Firefox-3.6.

From the testing I have done the following works...



as does "sudo apt-get install firefox"

Checkout post #[43]("http://ubuntuforums.org/showthread.php?p=8708092#post8708092") for the latest news.

The last posters experience tends to bare this out.

You are correct. I did the test now too. Before yesterday, you could install firefox-3.6 package separately and during the process there was a prompt asking if you would like to copy Firefox profile. After clicking yes, it copied the profile form ~/.mozilla/firefox to ~/.mozilla/firefox-3.6-something. This behavior no longer exists. Thanks for pointing that out.

---

### Post by darco on 2010-01-23
I just hosed my FF using silverwaves instructions. FF initially ran but now refuses even with gksudo. I did delete the profile but still a no go. I use Mint7x64 which may be the issue since I believe they customize it in some way...

```
$ firefox

(firefox-bin:6246): GLib-WARNING **: g_set_prgname() called multiple times

```

---

### Post by lovinglinux on 2010-01-23
> **darco said:**
> I just hosed my FF using silverwaves instructions. FF initially ran but now refuses even with gksudo. I did delete the profile but still a no go. I use Mint7x64 which may be the issue since I believe they customize it in some way...

```
$ firefox

(firefox-bin:6246): GLib-WARNING **: g_set_prgname() called multiple times

```

Try to reboot or reload apparmor. See discussion [here](http://ubuntuforums.org/showthread.php?p=8706487).

---

### Post by darco on 2010-01-23
I dont seem to have appamor installed....reply is "sudo: /etc/init.d/apparmor: command not found". I reinstalled 3.7 and it came right up w/no issues. Then closed it and tried again and will not open up.

edit *ok, its a "64-bit thang"......

---

### Post by lovinglinux on 2010-01-23
> **darco said:**
> I dont seem to have appamor installed....reply is "sudo: /etc/init.d/apparmor: command not found". I reinstalled 3.7 and it came right up w/no issues. Then closed it and tried again and will not open up.

You have Apparmor installed. It is not **sudo[COLOR="Sienna"]:[/COLOR] /etc/init.d/apparmor** is **sudo /etc/init.d/apparmor**.

Anyway, your problem seems to be a different one. After closing Firefox, go to the System Manager and make sure there isn't a **firefox-bin** running. If it is still there, kill it, than start Firefox again. See if that helps.

---

### Post by darco on 2010-01-23
> **lovinglinux said:**
> You have Apparmor installed. It is not **sudo[COLOR="Sienna"]:[/COLOR] /etc/init.d/apparmor** is **sudo /etc/init.d/apparmor**.

Anyway, your problem seems to be a different one. After closing Firefox, go to the System Manager and make sure there isn't a **firefox-bin** running. If it is still there, kill it, than start Firefox again. See if that helps.

No, I ran the command correctly. That was the response.....
I already checked sys monitor and it only shows a zombie running.....
Also synaptic does not show appamour installed
thxs

---

### Post by lovinglinux on 2010-01-23
> **darco said:**
> No, I ran the command correctly. That was the response.....
I already checked sys monitor and it only shows a zombie running.....
Also synaptic does not show appamour installed
thxs

Try this:

```
firefox -P -no-remote
```

If that works, create a new profile and launch it.

---

### Post by darco on 2010-01-23
Ran the command, Namoroka 3.61pre popped up, created a profile. Closed browser, tried to restart via menu, nothing, tried via command line, profile mngr popped up, chose profile, same error as above.

from the About Namoroka
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.1pre) Gecko/20100123 Ubuntu/9.10 (karmic) Namoroka/3.6.1pre

---

### Post by lovinglinux on 2010-01-23
> **darco said:**
> Ran the command, Namoroka 3.61pre popped up, created a profile. Closed browser, tried to restart via menu, nothing, tried via command line, profile mngr popped up, chose profile, same error as above.

I think the problem is that firefox is not closing properly and the profile is still in use. Nevertheless, you should get a warning about that.. Try this

```
firefox -no-remote -P "default"
```

Where default is the name of the profile you want to use.

---

### Post by darco on 2010-01-23
Any profile related command brings up the profile mngr, but once I choose a profile, same error as before. I think you are right that its not shutting down correctly because I added another profile, it opens the browser fine, but once I close, it wont reopen.
This shouldnt matter but I am on 2.6.33rc4 kernel

**eidt* I ran firefox -safe-mode and disabled all addons, it seems to work. I only had adblocker and noscript so Ill see which is causing the problem. My wife will be happy  since she uses FF but she was happy w/Opera too!

---

### Post by Daniel_le_Rouge on 2010-01-25
Hello!

The fonts in my Firefox are displayed awkward. Especially when there are bold letters, the interior of the letter is empty or white and only the border is displayed.

I attached two screenshot of [Mozilla's add-ons website]("https://addons.mozilla.org/en-US/firefox/"). The first one is from the Ubuntu machine, the other one is taken from a Mac, where everything works properly. You will see the difference immediately, as it is hardly possible to read the categories on the left side in the Ubuntu screenshot. I already checked Firefox's fonts configuration, but they are the same. I also attached a screenshot of my configuration (German version).

Both machines use the same Firefox version 3.6. But the problems occurred also in Firefox 3.5 and 3.0. I am using Ubuntu 9.10 Karmic Koala.

Thank you very much for your help!

Daniel

---

### Post by lovinglinux on 2010-01-25
> **Daniel_le_Rouge said:**
> Hello!

The fonts in my Firefox are displayed awkward. Especially when there are bold letters, the interior of the letter is empty or white and only the border is displayed.

I attached two screenshot of [Mozilla's add-ons website]("https://addons.mozilla.org/en-US/firefox/"). The first one is from the Ubuntu machine, the other one is taken from a Mac, where everything works properly. You will see the difference immediately, as it is hardly possible to read the categories on the left side in the Ubuntu screenshot. I already checked Firefox's fonts configuration, but they are the same. I also attached a screenshot of my configuration (German version).

Both machines use the same Firefox version 3.6. But the problems occurred also in Firefox 3.5 and 3.0. I am using Ubuntu 9.10 Karmic Koala.

Thank you very much for your help!

Daniel

Try to untick the option "Seiten das Verwenden von eigenen..."

---

### Post by Daniel_le_Rouge on 2010-01-25
> **lovinglinux said:**
> Try to untick the option "Seiten das Verwenden von eigenen..."
That worked perfectly! Thanks a lot!

---

### Post by lovinglinux on 2010-01-25
> **Daniel_le_Rouge said:**
> That worked perfectly! Thanks a lot!

You are welcome.

---

### Post by phillw on 2010-01-25
Hi lovinglinux, not sure whether to post here or on 10.04 ....

Is 3.6 stable enough to put onto my 9.10 system safely (I commented on the 3.57rc borking from daily)

It's just that I rsync my bookmarks etc. over between the .mozilla on 10.04 & 9.10 to keep them, well, sync'd !!

It makes sense to me, to have the same version number running on both systems. Should I 'go for it', or wait ?

As a P.S. - the numerals 1 and 4 in display on FFox, is always bigger than all the other text - does anyone else have this, or is it only picking on me !! I'm set up to use the default fonts.  --> It shows here --> [http://mgjuddltd.phillw.net/rep_filters.php](http://mgjuddltd.phillw.net/rep_filters.php)

Thanks, 

Phill.

---

### Post by lovinglinux on 2010-01-25
> **phillw said:**
> Is 3.6 stable enough to put onto my 9.10 system safely (I commented on the 3.57rc borking from daily)

Yes. Go for it. But keep in mind that if you are using the daily PPA you will continue to get unstable releases. Nevertheless, you can open Synaptic, select **firefox**, **firefox-3.5** and **firefox-branding** then go to the **Package** menu and select **Lock version**.

> **phillw said:**
> It's just that I rsync my bookmarks etc. over between the .mozilla on 10.04 & 9.10 to keep them, well, sync'd !!

It makes sense to me, to have the same version number running on both systems. Should I 'go for it', or wait ?

It's better to sync when using the same version, otherwise Firefox will keep checking extension compatibility whenever you start one version after the other. Yes, go for it. But keep in mind some people is experiencing font rendering issues. Nevertheless, is working great for me.

> **phillw said:**
> As a P.S. - the numerals 1 and 4 in display on FFox, is always bigger than all the other text - does anyone else have this, or is it only picking on me !! I'm set up to use the default fonts.  --> It shows here --> [http://mgjuddltd.phillw.net/rep_filters.php](http://mgjuddltd.phillw.net/rep_filters.php)

Never heard of a similar problem. Definitely a weird one.

---

### Post by zika on 2010-01-26
I'm having a small problem. In either 3.6 or 3.7 I can not erase entry in History that messes with autocomplete I want. I highlight entry, use Del, Shift-Del, right-click and _D_elete, it does not make a difference. Entry is gone from the window but it is back as soon I search through History again... So, how to permanently delete entry from History?

---

### Post by lovinglinux on 2010-01-26
> **zika said:**
> I'm having a small problem. In either 3.6 or 3.7 I can not erase entry in History that messes with autocomplete I want. I highlight entry, use Del, Shift-Del, right-click and _D_elete, it does not make a difference. Entry is gone from the window but it is back as soon I search through History again... So, how to permanently delete entry from History?

Your problem suggests a corruption or permission issue related to places.sqlite. Check if you have the right permissions on or .moozilla/firefox folder. Also create a new profile and check if the problems persist. If not, then start your regular profile and make a backup of your bookmarks, then close Firefox, then delete the file places.sqlite from your profile, then start Firefox and import the bookmark backup.

---

### Post by bluelamp999 on 2010-01-26
Hey LovingLinux

Have you (or anybody else) had any luck in compiling FF 3.6 from source as per the instructions in your excellent tutorial?

Cheers

---

### Post by lovinglinux on 2010-01-26
> **bluelamp999 said:**
> Hey LovingLinux

Have you (or anybody else) had any luck in compiling FF 3.6 from source as per the instructions in your excellent tutorial?

Cheers

No. I haven't compiled it since 3.5.6 I guess, due to some errors. I recently upgraded my CPU and switched to 64bit, so I'm thinking about compiling it again, just to see how long it takes with the dual core CPU :)

Anyways, take a look at [this post](http://ubuntuforums.org/showpost.php?p=8692594&postcount=334).

---

### Post by zika on 2010-01-26
> **lovinglinux said:**
> Your problem suggests a corruption or permission issue related to places.sqlite. Check if you have the right permissions on or .moozilla/firefox folder. Also create a new profile and check if the problems persist. If not, then start your regular profile and make a backup of your bookmarks, then close Firefox, then delete the file places.sqlite from your profile, then start Firefox and import the bookmark backup.Solved with option "Forget about this site"... Permissions are OK. Everything is OK, just Delete does not work as I thought it would.

---

### Post by bluelamp999 on 2010-01-26
> **lovinglinux said:**
> No. I haven't compiled it since 3.5.6 I guess, due to some errors. I recently upgraded my CPU and switched to 64bit, so I'm thinking about compiling it again, just to see how long it takes with the dual core CPU :)

Anyways, take a look at [this post](http://ubuntuforums.org/showpost.php?p=8692594&postcount=334).

Well, if anyone's interested it compiled for me fairly easily.

I followed the compilation instructions in the (most excellent) HOW TO at the start of this thread.

There were a few minor issues...

Having set the processor options in **.mozconfig** to reflect my own CPU and issuing... ```
make -f client.mk build
```
I got the following error:

*configure: error: Can't find header iwlib.h for Necko WiFi scanning (might be in package libiw-dev (Ubuntu) or wireless-tools-devel (Fedora)); use --disable-necko-wifi to disable*

So I just added ```
ac_add_options --disable-necko-wifi
``` to my  **.mozconfig** file and everything compiled this time around (took about 50 mins).

I then switched to the **/mozilla-x.y.z/obj-i686-pc-linux-gnu** folder and ran ```
make
``` 
which ran fine,

On running (with the defaults) ```
sudo checkinstall
```
I got 
```
Striping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package... FAILED!

*** Failed to build the package

Do you want to see the log file?  [y]:

Erasing temporary files...OK

Writing backup package...OK

Deleting temp dir...OK
```

Looking at the log file:
```
dpkg-deb - error: (upstream) version ('gnu') doesn't contain any digit
dpkg-deb: 1 errors in the control file
```

To overcome this I simply ran the command again and put a version no. in for option 3 as mine initially contained 'gnu' (I put in '3.6'.)

And that was it!

A deb package was created (**obj-i686-pc-linux** in my case) and now my Firefox is the one compiled by my own sweet self!

Thus far there's just one small issue, the new FF instance seems to have taken its icon from my installed icon theme (gTango) which is less than optimal.

Otherwise, it definitely feels more responsive and all extensions, plugins and themes seem to be fine.

Thanks to LovingLinux again...

Edit: FF is *definitely* more responsive. A very positive upgrade.

Edit: As I'm running an older processor (Pentium M 2GHz) the benefits of CPU-specific compilation might be more noticeable. I can't comment on more modern processors.

---

### Post by lovinglinux on 2010-01-27
> **bluelamp999 said:**
> Well, if anyone's interested it compiled for me fairly easily.

....

Edit: FF is *definitely* more responsive. A very positive upgrade

Edit: As I'm running an older processor (Pentium M 2GHz) the benefits of CPU-specific compilation might be more noticeable. I can't comment on more modern processors.

That's great news. Thanks for sharing. I have already included a link to your post on the tutorial.

I recently upgraded my CPU from a P4 to a Core2 Duo. When using the Pentium, the difference was huge. I haven't tested it with the dual core yet.

---

### Post by bluelamp999 on 2010-01-27
> **lovinglinux said:**
> That's great news. Thanks for sharing. I have already included a link to your post on the tutorial.

I recently upgraded my CPU from a P4 to a Core2 Duo. When using the Pentium, the difference was huge. I haven't tested it with the dual core yet.

You wouldn't happen to know how to change the program icon? Not the launcher/menu icon but the actual FF program icon.

Also, what about upgrades? I'm assuming I'll have to recompile any time there's a new version released? - E.g. 3.6.1

Thanks for all your help...

---

### Post by lovinglinux on 2010-01-27
> **bluelamp999 said:**
> You wouldn't happen to know how to change the program icon? Not the launcher/menu icon but the actual FF program icon.

You need to enable branding on the compiling options.

> **bluelamp999 said:**
> Also, what about upgrades? I'm assuming I'll have to recompile any time there's a new version released? - E.g. 3.6.1

Unfortunately, yes.

---

### Post by bluelamp999 on 2010-01-27
Me again...

I had major headaches trying to get the latest version of the Java plugin [1.6.0_18] recognized by FF.

I followed the instructions here - [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java) - everything seemed OK as regards the symlinks etc. but still no joy with the plugin.

Eventually I found this post
> **modean987 said:**
> The libjavaplugin_oji.so no longer works.

In your firefox plugins directory add a symbolic link to the NEW plugin.

ln -s /usr/local/java/jre1.6.0_18/lib/i386/libnpjp2.so libnpjp2.so 

Change your path accordingly.

Disclaimer: This works with a mozilla 3.6 tarball.

Info: [http://java.sun.com/javase/6/webnotes/install/jre/manual-plugin-install-linux.html](http://java.sun.com/javase/6/webnotes/install/jre/manual-plugin-install-linux.html)

The above link assumes you're using Sun's latest JRE installed in /usr/local. For those of you using Ubuntu's Sun packages, the appropriate symbolic link would be:

ln -s /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so libnpjp2.so

Setting the symlink to point to libnpjp2.so solved the issue!

It seems like this might be specific to compiled FF? Maybe?

---

### Post by zika on 2010-01-29
Am I the only one having problem with currently unusable FF-3.7? It starts loading the page and... it stops, "Force quit" is the only exit... Latest version from mozilla-daily... For three days, now...```
~$ /usr/bin/firefox-3.7

** (firefox-3.7:5287): WARNING **: Serious fd usage error 14

** (firefox-3.7:5287): WARNING **: Serious fd usage error 12
```FF-3.6 works OK, Chromium-browser-daily, works great!
Creating new profile or renaming .mozilla/firefox-3.7 folder did not help in any way. It just stalls during loading a simple page...

---

### Post by SilverWave on 2010-01-29
Anyone having trouble with ff3.6 fonts... may want to have a look at  this setting...

[http://kb.mozillazine.org/Browser.di..._min_font_size]("http://kb.mozillazine.org/Browser.display.auto_quality_min_font_size")

As I wanted text to be **optimized for display quality** I set
     ```
browser.display.auto_quality_min_font_size = 0 
```Worked  for me.

---

### Post by wsonar on 2010-01-29
All I know is Chrome perfomrs better on linux than FF

---

### Post by lovinglinux on 2010-01-29
> **bluelamp999 said:**
> It seems like this might be specific to compiled FF? Maybe?

Thanks for posting the solution. Have you tried with other versions to see if the problem is in the compiled one?


> **zika said:**
> Am I the only one having problem with currently unusable FF-3.7? It starts loading the page and... it stops, "Force quit" is the only exit... Latest version from mozilla-daily... For three days, now...

Unfortunately, I'm not using 3.7 yet. I will at some point, to test my extensions.

Here is [Chromium that isn't working](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8723572). 

> **SilverWave said:**
> Anyone having trouble with ff3.6 fonts... may want to have a look at  this setting...

[http://kb.mozillazine.org/Browser.di..._min_font_size]("http://kb.mozillazine.org/Browser.display.auto_quality_min_font_size")

As I wanted text to be **optimized for display quality** I set
     ```
browser.display.auto_quality_min_font_size = 0 
```Worked  for me.

That's really interesting. Does this solve the weird font issues some users are experiencing after FF 3.6 upgrade from the PPA?

> **wsonar said:**
> All I know is Chrome perfomrs better on linux than FF

I guess everyone knows that. Nevertheless, nothing beats Firefox in terms of customization and extension availability. If Firefox was slow like a turtle than I would probably use Chrome, but Firefox 3.5 and 3.6 performances are excellent. I don't see a good reason to switch.

Anyways, this a thread for Firefox support. So please keep the discussion in line with the objective of the thread. There are plenty of threads on the forums that discuss how faster Chrome is.

---

### Post by SilverWave on 2010-01-29
> **lovinglinux said:**
> 
...
That's really interesting. Does this solve the weird font issues some users are experiencing after FF 3.6 upgrade from the PPA?...

Yes is seems to have for me anyway...

I reset my system back to firefox defaults and then installed Firefox3.6 via Firefox Stable  Channel Packages ppa.

It even calls its self Firefox and has the correct Icon ;)

But the fonts were pants :(

Found some info while reading this:
[http://limulus.wordpress.com/2010/01/28/an-open-letter-to-mozilla-re-ubuntu/](http://limulus.wordpress.com/2010/01/28/an-open-letter-to-mozilla-re-ubuntu/)

> Suggest a clean start (backup your bookmarks and then import them).But in the comments:

[http://kb.mozillazine.org/Gfx.use_text_smoothing_setting](http://kb.mozillazine.org/Gfx.use_text_smoothing_setting)
**Don't think this applies... but confirmation would be good.**

[URL="http://kb.mozillazine.org/Browser.display.auto_quality_min_font_size"]http://kb.mozillazine.org/Browser.display.auto_quality_min_font_size
[/URL] **This is the one that worked for me.**

---

### Post by lovinglinux on 2010-01-29
> **SilverWave said:**
> Yes is seems to have for me anyway...

I reset my system back to firefox defaults and then installed Firefox3.6 via Firefox Stable  Channel Packages ppa.

It even calls its self Firefox and has the correct Icon ;)

But the fonts were pants :(

Found some info while reading this:
[http://limulus.wordpress.com/2010/01/28/an-open-letter-to-mozilla-re-ubuntu/](http://limulus.wordpress.com/2010/01/28/an-open-letter-to-mozilla-re-ubuntu/)

But in the comments:

[http://kb.mozillazine.org/Gfx.use_text_smoothing_setting](http://kb.mozillazine.org/Gfx.use_text_smoothing_setting)
**Don't think this applies... but confirmation would be good.**

[URL="http://kb.mozillazine.org/Browser.display.auto_quality_min_font_size"]http://kb.mozillazine.org/Browser.display.auto_quality_min_font_size
[/URL] **This is the one that worked for me.**

I saw your post on the Firefox 3.6 thread discussing the font issue. I'm curious to see if it will work for the other users. Let's hope so.

---

### Post by mrand on 2010-01-30
Finally upgraded to 9.10... the very first time Firefox launched, it created a "Starting firefox..." menu icon, but that disappeared and nothing else happened.  Launching from a shell produces no output at all (text or graphical)... and does not return to shell prompt - it just hangs.


```
test@media:~/.mozilla$ ps -ef | grep fire
test      4936  4906  0 12:23 ?        00:00:00 /bin/sh -c /usr/lib/firefox/firefox -version
test      4937  4936  0 12:23 ?        00:00:00 /bin/sh /usr/lib/firefox/firefox -version
test      4941  4937  0 12:23 ?        00:00:00 /bin/sh /usr/lib/firefox/run-mozilla.sh /usr/lib/firefox/firefox-bin -version
test      4945  4941  0 12:23 ?        00:00:00 /usr/lib/firefox/firefox-bin -version
test      4947     1  0 12:23 ?        00:00:00 /usr/lib/firefox-3.5.7/firefox
$
$ gdb firefox
Reading symbols from /usr/lib/firefox-3.5.7/firefox...(no debugging symbols found)...done.
(gdb) run
Starting program: /usr/lib/firefox-3.5.7/firefox 
[Thread debugging using libthread_db enabled]
^C
Program received signal SIGINT, Interrupt.
0x003b5422 in __kernel_vsyscall ()

```

Starting with gksudo firefox works.
I tried purging firefox and installing - no change.

I'd welcome any ideas,

[INDENT]Marc[/INDENT]

---

### Post by lovinglinux on 2010-01-30
> **mrand said:**
> Finally upgraded to 9.10... the very first time Firefox launched, it created a "Starting firefox..." menu icon, but that disappeared and nothing else happened.  Launching from a shell produces no output at all (text or graphical)... and does not return to shell prompt - it just hangs.


```
test@media:~/.mozilla$ ps -ef | grep fire
test      4936  4906  0 12:23 ?        00:00:00 /bin/sh -c /usr/lib/firefox/firefox -version
test      4937  4936  0 12:23 ?        00:00:00 /bin/sh /usr/lib/firefox/firefox -version
test      4941  4937  0 12:23 ?        00:00:00 /bin/sh /usr/lib/firefox/run-mozilla.sh /usr/lib/firefox/firefox-bin -version
test      4945  4941  0 12:23 ?        00:00:00 /usr/lib/firefox/firefox-bin -version
test      4947     1  0 12:23 ?        00:00:00 /usr/lib/firefox-3.5.7/firefox
$
$ gdb firefox
Reading symbols from /usr/lib/firefox-3.5.7/firefox...(no debugging symbols found)...done.
(gdb) run
Starting program: /usr/lib/firefox-3.5.7/firefox 
[Thread debugging using libthread_db enabled]
^C
Program received signal SIGINT, Interrupt.
0x003b5422 in __kernel_vsyscall ()

```

Starting with gksudo firefox works.
I tried purging firefox and installing - no change.

I'd welcome any ideas,

[INDENT]Marc[/INDENT]

Try

```
firefox -P -no-remote
```

---

### Post by ironjaw33 on 2010-01-30
Setting Browser.display.auto_quality_min_font_size = 0 does nothing for me -- my fonts still look terrible.  The only solution I have found so far to fix the fonts is to compile Firefox from source.

---

### Post by mrand on 2010-01-30
(launching firefox produces absolutely no output to shell.  No window created.  gksudo firefox works)
> **lovinglinux said:**
> Try```
firefox -P -no-remote
```Unfortunately, same behavior - no output anywhere.

I tried removing my profile of course... no change.  I'm willing to help debug this further with debug packages, or whatever (or go to 3.6 if that would be easier to debug).
[INDENT]Marc[/INDENT]

---

### Post by lovinglinux on 2010-01-30
> **mrand said:**
> (launching firefox produces absolutely no output to shell.  No window created.  gksudo firefox works)
Unfortunately, same behavior - no output anywhere.

I tried removing my profile of course... no change.  I'm willing to help debug this further with debug packages, or whatever (or go to 3.6 if that would be easier to debug).
[INDENT]Marc[/INDENT]

Go to Synaptic, search for *xulrunner-1.9.1* and mark it for reinstallation, then click apply. Do not attempt to remove it, since several gnome dependencies would be removed too. So, just use the reinstall option.

You did an upgrade from 9.04 to 9.10 or a fresh install?

---

### Post by mrand on 2010-01-30
> **lovinglinux said:**
> Go to Synaptic, search for *xulrunner-1.9.1* and mark it for reinstallation, then click apply. Do not attempt to remove it, since several gnome dependencies would be removed too. So, just use the reinstall option.

You did an upgrade from 9.04 to 9.10 or a fresh install?This was an upgrade to 9.10.  Reinstalling xulrunner didn't help.  Followed that with reinstalling xulrunner-1.9.1-gnome-support as well as firefox... same problem.

Thanks for the rapid help,

[INDENT]   Marc[/INDENT]

Mulling this over further, the only possible thing I can think that might be out of the normal on this install: I don't recall manually installing a new version of Firefox last summer, but it is possible that I did.  Even still, I believe I was on 8.10 at that point, so it upgraded to 9.04 without problem.

---

### Post by lovinglinux on 2010-01-30
> **mrand said:**
> This was an upgrade to 9.10.  Reinstalling xulrunner didn't help.  Followed that with reinstalling xulrunner-1.9.1-gnome-support as well as firefox... same problem.

Thanks for the rapid help,

[INDENT]   Marc[/INDENT]

Mulling this over further, the only possible thing I can think that might be out of the normal on this install: I don't recall manually installing a new version of Firefox last summer, but it is possible that I did.  Even still, I believe I was on 8.10 at that point, so it upgraded to 9.04 without problem.

I would reinstall Ubuntu. I never do upgrades, just clean installs.  Did another one on the day Firefox 3.6 was released, to switch to 64bit. 

If you have a separate partition for home and export the list of installed packages from Synaptic, then re-installing is pretty easy.

---

### Post by phillw on 2010-01-30
Hi,

lovinglinux, or one of the others who is 'good' at FireFox - could one of you pop over to --> [http://ubuntuforums.org/showthread.php?t=1394353](http://ubuntuforums.org/showthread.php?t=1394353)

The only way I know of doing it is to enable the stable ppa and get it that way. I'm worried that it might break something if I suggest that as I don't know about 8.04

Thanks,

Phill.

---

### Post by mrand on 2010-01-30
> **lovinglinux said:**
> I would reinstall Ubuntu. I never do upgrades, just clean installs.  Did another one on the day Firefox 3.6 was released, to switch to 64bit. 

If you have a separate partition for home and export the list of installed packages from Synaptic, then re-installing is pretty easy.Wow.  I hope you're kidding.  People joke about reinstalls being required sometimes Windows, but this is the first I've seen someone suggest it for Ubuntu - so I assume you're joking.

But in case you are serious... No, it isn't pretty easy for most users, myself included.  I don't have a separate home partition.  And among other things, this is a file server and a MythTV combined front-end/back-end media server, so I have a number of configuration options that I would lose if I reinstalled.  Not to mention that I don't have the time to reinstall and reconfigure everything.

I'm hoping you or someone else has some other ideas...

[INDENT]Marc[/INDENT]

---

### Post by lovinglinux on 2010-01-30
> **mrand said:**
> Wow.  I hope you're kidding.  People joke about reinstalls being required sometimes Windows, but this is the first I've seen someone suggest it for Ubuntu - so I assume you're joking.

But in case you are serious... No, it isn't pretty easy for most users, myself included.  I don't have a separate home partition.  And among other things, this is a file server and a MythTV combined front-end/back-end media server, so I have a number of configuration options that I would lose if I reinstalled.  Not to mention that I don't have the time to reinstall and reconfigure everything.

I'm hoping you or someone else has some other ideas...

[INDENT]Marc[/INDENT]

Well, I have to agree with you that in your case it's not the best solution. But I wasn't joking. The thing is that I take some steps to allow such easy re-install process (see quote at the end):

We definitely do not need to re-install Linux as we had to re-install Windows and I avoid suggesting that solution. But in your case you have already re-installed Firefox, xulrunner, created a new profile and nothing works and you don't even get errors on the terminal. Nevertheless, I should have tried a different approach first.

Create a new user on your system, not on Firefox , and log into Gnome with that user account, then start Firefox and see what happens. 

The fact that creating a new profile doesn't help, but running Firefox as gksudo does, suggests that the problem lies on your user configuration files. There must be some Gnome configurations that are messing with Firefox or some corrupted system package that is only affecting you particular settings. So running Firefox from a new account should work. After testing this hypothesis, we can try to pinpoint the culprit.

Perhaps you could also check if you have the necessary permissions to write on the .mozilla folder. See [this](http://lovinglinux.megabyet.net/?page_id=220#Firefox-doesn%27t-start-through-regular-command/menu-but-starts-using-%22sudo-firefox%22--2).

> **Why I say re-installing is easy.**

1) I have a separate /home, where I save only configuration files. All my personal files (documents, videos, music, projects) are stored on another partition and symlinked to /home. This way I don't even need to worry about losing home if something goes wrong. But I also make a backup of all config files prior to any re-installation.

2)  I have a journal of every process performed to tweak config files outside /home and backups of every working configuration files tweaked by me. For example, I have annotations of how to configure my remote control and TV card, step-by-step and copies of their config files. So after the reinstall I just copy the backups to /etc/lirc, run a couple of commands and voilà, I have a working remote and TV.

3) I develop [a Firefox extension](https://addons.mozilla.org/en-US/firefox/addon/13153) that generates a list with all installed and removed applications on my machine. So after the re-install, I just start Firefox, click a button in my extension and it takes care of installing all software for me. Since I have a separate /home with all the config files, I'm able to get my machine exactly the way it was before the re-installation in a couple of hours.

---

### Post by mrand on 2010-01-31
> **lovinglinux said:**
> Create a new user on your system, not on Firefox , and log into Gnome with that user account, then start Firefox and see what happens.I did one better.  Today when I woke up, I realized that I had overlooked a very important piece of information: I'm running over NX.  Completely slipped my mind because it has worked seemlessly for two years.  Sorry for the omission!

Anyway, I went to the actual machine and Firefox opens just fine with my test user - the very same user (and profile), not to mention the same Firefox install.  Go back to the remote NX session, and it doesn't work.

Please feel free to correct me, but I believe this indicates both the profile and the Firefox install are fine... it is likely a permission problem with some system resource that Firefox is trying to use or access and permissions are blocking that access when run from remote (with NX).  

Might anyone have some ideas on what Firefox might wait/hang on, expecting access but never getting it?  Sound plays with vlc, so I don't think it's that. 

Thanks for any ideas!

   Marc

P.S.  I also realized that I hadn't run strace on it.  I attached that here, along with a gdb generated stack trace:
[https://answers.launchpad.net/ubuntu/+source/firefox/+question/99319](https://answers.launchpad.net/ubuntu/+source/firefox/+question/99319)

*UPDATE:*
Solution was to disable multi-media support in NX client:
[http://ubuntuforums.org/showthread.php?p=8772736#post8772736](http://ubuntuforums.org/showthread.php?p=8772736#post8772736)

---

### Post by lovinglinux on 2010-01-31
> **mrand said:**
> I did one better.  Today when I woke up, I realized that I had overlooked a very important piece of information: I'm running over NX.  Completely slipped my mind because it has worked seemlessly for two years.  Sorry for the omission!

Anyway, I went to the actual machine and Firefox opens just fine with my test user - the very same user (and profile), not to mention the same Firefox install.  Go back to the remote NX session, and it doesn't work.

Please feel free to correct me, but I believe this indicates both the profile and the Firefox install are fine... it is likely a permission problem with some system resource that Firefox is trying to use or access and permissions are blocking that access when run from remote (with NX).  

Might anyone have some ideas on what Firefox might wait/hang on, expecting access but never getting it?  Sound plays with vlc, so I don't think it's that. 

Thanks for any ideas!

   Marc

P.S.  I also realized that I hadn't run strace on it.  I attached that here, along with a gdb generated stack trace:
[https://answers.launchpad.net/ubuntu/+source/firefox/+question/99319](https://answers.launchpad.net/ubuntu/+source/firefox/+question/99319)


Sounds you have figured it out. Unfortunately, I never used NX so can help you with that. But you could try to forward Firefox over ssh.

---

### Post by zika on 2010-02-01
> **zika said:**
> Am I the only one having problem with currently unusable FF-3.7? It starts loading the page and... it stops, "Force quit" is the only exit... Latest version from mozilla-daily... For three days, now...```
~$ /usr/bin/firefox-3.7

** (firefox-3.7:5287): WARNING **: Serious fd usage error 14

** (firefox-3.7:5287): WARNING **: Serious fd usage error 12
```FF-3.6 works OK, Chromium-browser-daily, works great!
Creating new profile or renaming .mozilla/firefox-3.7 folder did not help in any way. It just stalls during loading a simple page...If I disable flash plugin it works nicely... Flash-plugin is the latest from Adobe (alpha 64-bit). The same plugin works perfectly with 3.6 and Chromium. Any news on what is happening?

---

### Post by lovinglinux on 2010-02-01
> **zika said:**
> If I disable flash plugin it works nicely... Flash-plugin is the latest from Adobe (alpha 64-bit). The samo plugin works perfectly with 3.6 and Chromium. Any news on what is happening?

No, but I'm experiencing the same problem using the latest alpha 64bit flash plugin with Chromium. It starts, but hangs on the first page I try to load, if I enable the plugins. So I guess flash is the culprit.

Take a look at [this discussion](http://ubuntuforums.org/showthread.php?t=1390244).

---

### Post by zika on 2010-02-01
> **lovinglinux said:**
> No, but I'm experiencing the same problem using the latest alpha 64bit flash plugin with Chromium. It starts, but hangs on the first page I try to load, if I enable the plugins. So I guess flash is the culprit.

Take a look at [this discussion]("http://ubuntuforums.org/showthread.php?t=1390244").With Chromium 5.0.312.0 (37680) Ubuntu on my machine Flash works fine... Strange...

---

### Post by lovinglinux on 2010-02-01
> **zika said:**
> With Chromium 5.0.312.0 (37680) Ubuntu on my machine Flash works fine... Strange...

Yep, it seems to be causing problems only for KDE users. Who knows whats going on....

---

### Post by SilverWave on 2010-02-06
Just in case anyone is playing with 3.7, A2 is out :)

[Firefox 3.7 Alpha2 Install and Test Details]("http://ubuntuforums.org/showpost.php?p=8783159&postcount=61")

[Changelog]("http://ubuntuforums.org/showpost.php?p=8783108&postcount=60")

---

### Post by phillw on 2010-02-14
Hiya lovinglinux, 

A quick question, I'm still on FF Namoroka (3.6.1pre) on both my 9.10 and 10.04 - Is it time to update both to a full release ? (and if so, point me to the directions ;) )

Not sure if this is what i need ?
> 
			 				For** ubuntu karmic/Lucid users**
sudo add-apt-repository ppa:mozillateam/firefox-stable
 sudo apt-get update
 sudo apt-get install firefox-3.6


Thanks,

Phill.

---

### Post by lovinglinux on 2010-02-14
> **phillw said:**
> Hiya lovinglinux, 

A quick question, I'm still on FF Namoroka (3.6.1pre) on both my 9.10 and 10.04 - Is it time to update both to a full release ? (and if so, point me to the directions ;) )

Not sure if this is what i need ?


Thanks,

Phill.

Yep, that's is what I use. Nevertheless, you won't need that on Lucid, since it already has Firefox 3.6. Disable any ppa for Firefox that you have and re-install firefox.

---

### Post by phillw on 2010-02-14
> **lovinglinux said:**
> re-install firefox.

Hmm.. Well, I tried the ```
sudo apt-get update
 sudo apt-get install firefox-3.6
``` and it said it went a getting, and firefox then went a getting updates for extensions.. Still says 3.6.1pre and Namoroka ..

I've just rsync'd everything over to my 'other' /home - How do i "re-install" ?

/edit - which reminds me .... I haven't backed up to my other, other home recently 

Thanks,

Phill.

---

### Post by lovinglinux on 2010-02-14
> **phillw said:**
> Hmm.. Well, I tried the ```
sudo apt-get update
 sudo apt-get install firefox-3.6
``` and it said it went a getting, and firefox then went a getting updates for extensions.. Still says 3.6.1pre and Namoroka ..

I've just rsync'd everything over to my 'other' /home - How do i "re-install" ?

/edit - which reminds me .... I haven't backed up to my other, other home recently 

Thanks,

Phill.

First remove or disable the ubuntu-mozilla-daily ppa, then add the mozillateam/firefox-stable ppa then remove firefox and firefox-3.6, then install firefox only. Don't worry, it will say that firefox-3.5 will be installed, but in fact it will be 3.6.

---

### Post by phillw on 2010-02-14
> **lovinglinux said:**
> First remove or disable the ubuntu-mozilla-daily ppa, then add the mozillateam/firefox-stable ppa then remove firefox and firefox-3.6, then install firefox only. Don't worry, it will say that firefox-3.5 will be installed, but in fact it will be 3.6.

yikes !!!  
Synaptics shows ...

firefox   3.6.1~hg20100125r35540+nobinonly-0ubuntu1~umd1
ubufox   0.8-0ubuntu1
firefox-branding     3.6.1~hg20100125r35540+nobinonly-0ubuntu1~umd1

Which am i marking, and for removal or complete removal ?

Phill.

---

### Post by lovinglinux on 2010-02-14
> **phillw said:**
> yikes !!!  Am i removing or removing completely ?

Phill.

It doesn't matter. Just make sure to re-install any dependencies like ubuntu-desktop if the package manager also remove them. I'm on KDE, so I forget about those details.

---

### Post by phillw on 2010-02-14
okies - here goes ;)

Phill.

---

### Post by phillw on 2010-02-14
Thanks.

3.6 - canonical 1.0 and Firefox branding.

:popcorn:

Phill.

---

### Post by lovinglinux on 2010-02-14
> **phillw said:**
> Thanks.

3.6 - canonical 1.0 and Firefox branding.

:popcorn:

Phill.

You are welcome 

:popcorn:

---

### Post by misha680 on 2010-02-19
Anyone tried 3.0.18 (compilation with PGO). I am getting strange errors on checkinstall:

```

./nsIDOMCSSStyleDeclaration.idl
./nsIEditor.idl
/home/misha/src/mozilla/obj-x86_64-unknown-linux-gnu/config/nsinstall -D /usr/local/lib/firefox-devel-3.0.18/sdk/lib
if test -f ../../dist/sdk/include/xpcom-config.h; then \
	  /home/misha/src/mozilla/obj-x86_64-unknown-linux-gnu/config/nsinstall -t -m 644 ../../dist/sdk/include/xpcom-config.h /usr/local/lib/firefox-devel-3.0.18; \
	fi
(cd ../../dist/sdk/lib && tar -cvhf - .) | (cd /usr/local/lib/firefox-devel-3.0.18/sdk/lib && tar -xf -)
./
./libnssutil.a
./libssl.a
./libsoftokn.a
./libmozreg_s.a
./libxul.so
./libnss.a
./libcrmf.a
tar: ./libxul.so: Cannot utime: No such file or directory
tar: ./libnss.a: Cannot utime: No such file or directory
./libunicharutil_external_s.a
./libembed_base_s.a
./libnspr4.so
tar: ./libcrmf.a: Cannot utime: No such file or directory
tar: ./libunicharutil_external_s.a: Cannot utime: No such file or directory
tar: ./libembed_base_s.a: Cannot utime: No such file or directory
./libsmime.a
tar: ./libnspr4.so: Cannot utime: No such file or directory
./libembed_base_standalone.a
./libmozjs.so
tar: ./libsmime.a: Cannot utime: No such file or directory
tar: ./libembed_base_standalone.a: Cannot utime: No such file or directory
./libxpcomglue_s.a
tar: ./libmozjs.so: Cannot utime: No such file or directory
./libplc4.so
./libxpcom.so
./libxpcomglue.a
tar: ./libxpcomglue_s.a: Cannot utime: No such file or directory
tar: ./libplc4.so: Cannot utime: No such file or directory
tar: ./libxpcom.so: Cannot utime: No such file or directory
./libplds4.so
tar: ./libxpcomglue.a: Cannot utime: No such file or directory
tar: ./libplds4.so: Cannot utime: No such file or directory
tar: Error exit delayed from previous errors
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/misha/src/mozilla/obj-x86_64-unknown-linux-gnu/browser/installer'
make: *** [install] Error 2

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.


```

Thank you!
Misha

---

### Post by meka4996 on 2010-02-20
Problem solved as of 6 March 2010
Thank you lovinglinux!
For those having problems with Firefox starting and don't get any errors on the terminal, verify if you have Prism installed and remove it. Prism is causing this problem here, using Firefox 3.6.
------------
Firefox won't start, but will start only once.

2010 Feb 18... after some updates on my Ubuntu Linux 9.04,
Firefox 3.6 starts only once, will not start again, unless I move the directory, or run Firefox 3.0.18, or reboot...

I launched Firefox everyday before that date, all was good. 

After deleting ~/.mozilla, 
After $ sudo apt-get remove --purge firefox
After downloading and running a fresh Firefox 3.6 via $ ~/firefox/firefox,
the problem is still the same!
Strangely, if I move the extracted folder[from a new Firefox download] "Firefox" to another directory like "~/Desktop", then the command "~/Desktop/firefox/firefox" will launch Firefox again, but only once... why??? Somebody help me!

After installing Firefox via Ubuntu Package Manager, Firefox 3.0.18 now works every time...
But why the Firefox 3.6 won't work after the first launch???
Especially, if running Firefox 3.0.18 after running Firefox 3.6, Firefox 3.0.18 seems to launch for the first time with brief flash of importing something... After Firefox 3.0.18 running, then Firefox 3.6 runs fine, only for the first time...
It seems there is a profile conflict within .mozilla/firefox so it needs to be re-written as brand new for Firefox 3.6 to work

$ sudo dpkg-reconfigure firefox  ... nothing shows up...

$ tail ~/.xsession-errors 
** (gnome-panel:3782): DEBUG: Adding applet 17.
** (gnome-panel:3782): DEBUG: Adding applet 18.
** (update-notifier:3800): DEBUG: /usr/lib/update-notifier/apt-check returned 1 (security: 0)
** (update-notifier:3800): DEBUG: crashreport_check

[4261:4270:697768709:ERROR:/usr/local/google/b/slave/chrome-official-linux/build/src/base/file_util_posix.cc(654)] Couldn't stat /usr/lib/firefox/plugins/libjavaplugin_oji.so: No such file or directory
[4261:4261:5234941644:ERROR:/usr/local/google/b/slave/chrome-official-linux/build/src/chrome/common/temp_scaffolding_stubs.h(41)] Not implemented reached in void printing::PrintViewManager::Stop()
** (update-notifier:3800): DEBUG: /usr/lib/update-notifier/apt-check returned 1 (security: 0)
** (update-notifier:3800): DEBUG: /usr/lib/update-notifier/apt-check returned 1 (security: 0)
** (update-notifier:3800): DEBUG: /usr/lib/update-notifier/apt-check returned 1 (security: 0)

Please help, thanks!

---

### Post by lovinglinux on 2010-02-20
> **meka4996 said:**
> Firefox won't start, but will start only once.

2010 Feb 18... after some updates on my Ubuntu Linux 9.04,
Firefox 3.6 starts only once, will not start again, unless I move the directory, or run Firefox 3.0.18, or reboot...

I launched Firefox everyday before that date, all was good. 

After deleting ~/.mozilla, 
After $ sudo apt-get remove --purge firefox
After downloading and running a fresh Firefox 3.6 via $ ~/firefox/firefox,
the problem is still the same!
Strangely, if I move the extracted folder[from a new Firefox download] "Firefox" to another directory like "~/Desktop", then the command "~/Desktop/firefox/firefox" will launch Firefox again, but only once... why??? Somebody help me!

After installing Firefox via Ubuntu Package Manager, Firefox 3.0.18 now works every time...
But why the Firefox 3.6 won't work after the first launch???
Especially, if running Firefox 3.0.18 after running Firefox 3.6, Firefox 3.0.18 seems to launch for the first time with brief flash of importing something... After Firefox 3.0.18 running, then Firefox 3.6 runs fine, only for the first time...
It seems there is a profile conflict within .mozilla/firefox so it needs to be re-written as brand new for Firefox 3.6 to work

$ sudo dpkg-reconfigure firefox  ... nothing shows up...

$ tail ~/.xsession-errors 
** (gnome-panel:3782): DEBUG: Adding applet 17.
** (gnome-panel:3782): DEBUG: Adding applet 18.
** (update-notifier:3800): DEBUG: /usr/lib/update-notifier/apt-check returned 1 (security: 0)
** (update-notifier:3800): DEBUG: crashreport_check

[4261:4270:697768709:ERROR:/usr/local/google/b/slave/chrome-official-linux/build/src/base/file_util_posix.cc(654)] Couldn't stat /usr/lib/firefox/plugins/libjavaplugin_oji.so: No such file or directory
[4261:4261:5234941644:ERROR:/usr/local/google/b/slave/chrome-official-linux/build/src/chrome/common/temp_scaffolding_stubs.h(41)] Not implemented reached in void printing::PrintViewManager::Stop()
** (update-notifier:3800): DEBUG: /usr/lib/update-notifier/apt-check returned 1 (security: 0)
** (update-notifier:3800): DEBUG: /usr/lib/update-notifier/apt-check returned 1 (security: 0)
** (update-notifier:3800): DEBUG: /usr/lib/update-notifier/apt-check returned 1 (security: 0)

Please help, thanks!

Try to start Firefox with the command below:

```
~/Desktop/firefox/firefox -P -no-remote
```

Replace the path accordingly.

---

### Post by meka4996 on 2010-02-20
Hi lovinglinux, yes, I tried...
$ ~/firefox/firefox
... nothing shows up, no error messages in the terminal

$ ~/firefox/firefox -P -no-remote
after selecting the profile, nothing shows up

$ ~/firefox/firefox -P
after selecting the profile, nothing shows up
What do you think? Thanks

---

### Post by lovinglinux on 2010-02-21
> **meka4996 said:**
> Hi lovinglinux, yes, I tried...
$ ~/firefox/firefox
... nothing shows up, no error messages in the terminal

$ ~/firefox/firefox -P -no-remote
after selecting the profile, nothing shows up

$ ~/firefox/firefox -P
after selecting the profile, nothing shows up
What do you think? Thanks


Strange. Have you tried to kill firefox-bin process before restarting Firefox?

---

### Post by meka4996 on 2010-02-21
Yes, I tried 
$ ps ux | less

There is no any firefox process after 
$ ~/firefox/firefox

---

### Post by lovinglinux on 2010-02-21
> **meka4996 said:**
> Yes, I tried 
$ ps ux | less

There is no any firefox process after 
$ ~/firefox/firefox

I don't know what is happening. I think you should report a bug.

---

### Post by phillw on 2010-02-24
Hi lovinglinux, next time you have a minute, could you take a look at [http://ubuntuforums.org/showthread.php?p=8853739](http://ubuntuforums.org/showthread.php?p=8853739)

The OP cannot post onto the forums either, so we're trying to assist via the IRC.

He has tried > 
[SIZE=2][COLOR=#445f1c](23:17:49) [/COLOR][/SIZE][COLOR=#445f1c]steelsteve: [/COLOR]Web sites keeps loading but never show up - [FOT005]
[SIZE=2][COLOR=#445f1c](23:17:49) [/COLOR][/SIZE][COLOR=#445f1c]steelsteve: [/COLOR]Firefox can’t connect to any sites, but other browsers work - [FOT005]Firefox can connect to sites only using the IP number - [FOT005to no avail.

You can catch him on either #Ubuntu-Beginners or ##devil if you need to chat with him directly

Thanks,

Phill.

---

### Post by SilverWave on 2010-02-24
> **meka4996 said:**
> Yes, I tried 
$ ps ux | less

There is no any firefox process after 
$ ~/firefox/firefox

Just a thought...
Are you installing 3.6 from

mozillateam/firefox-stable

or
ubuntu-mozilla-daily?

---

### Post by lovinglinux on 2010-02-24
> **phillw said:**
> Hi lovinglinux, next time you have a minute, could you take a look at [http://ubuntuforums.org/showthread.php?p=8853739](http://ubuntuforums.org/showthread.php?p=8853739)

The OP cannot post onto the forums either, so we're trying to assist via the IRC.

He has tried to no avail.

You can catch him on either #Ubuntu-Beginners or ##devil if you need to chat with him directly

Thanks,

Phill.

Problem solved. It was an extension (which one to be determined). Starting Firefox in safe mode fixed the problem.

---

### Post by phillw on 2010-02-25
> **lovinglinux said:**
> Problem solved. It was an extension (which one to be determined). Starting Firefox in safe mode fixed the problem.


Sadly, there is a problem, it didn't manifest itself straight away, but it has now - If you get chance, steve is on ##steelsteve (He's going to log that, so he can keep track of what has been tried, etc).

Thanks for all your help on this one !!

Regards,

Phill.

---

### Post by phillw on 2010-02-25
> **phillw said:**
> Sadly, there is a problem, it didn't manifest itself straight away, but it has now - If you get chance, steve is on ##steelsteve (He's going to log that, so he can keep track of what has been tried, etc).

Thanks for all your help on this one !!

Regards,

Phill.


/edit

Im' not real sure what is going on with his system, except that it is pretty messed up for FFox.

I propose following :-

 [http://support.mozilla.com/en-US/kb/Uninstalling+Firefox?s=reinstall](http://support.mozilla.com/en-US/kb/Uninstalling+Firefox?s=reinstall)

doing the backup of his ```
~/.mozilla/firefox*
```  directory then > 
then add the mozillateam/firefox-stable ppa then remove firefox and  firefox-3.6, then install firefox only. Don't worry, it will say that  firefox-3.5 will be installed, but in fact it will be 3.6.along with 
> Some video issues are caused by  conflicting plug-ins. It’s not a good  idea to have multiple plug-ins  for the same type of content. To remove conflicting flash plug-ins and  install only the one from Adobe  open “Applications >>  Accessories >> Terminal”, then paste  (CTRL+SHIFT+V) the code  below in the terminal window and hit enter:
  
 ```

 sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get install flashplugin-nonfree

```


Do you think it is worth trying ?

Regards

Phill.
P.S. - I hope you're not paying for the hosting of your tutorial, etc

---

### Post by lovinglinux on 2010-02-25
> **phillw said:**
> Do you think it is worth trying ?

I don't think so. Yesterday we already added the stable ppa and updated Firefox to 3.6. It looks like a profile problem, since other browsers work, including those that use xulrunner, and a new profile works for a while.

> **phillw said:**
> P.S. - I hope you're not paying for the hosting of your tutorial, etc

I'm not. It is a free hosting service :)

---

### Post by zika on 2010-03-01
How do You "translate" this:```
~$ firefox-3.7
Could not find compatible GRE between version 1.9.3a2pre and 1.9.3a2pre.
```...?

---

### Post by kmcbest on 2010-03-01
> **zika said:**
> How do You "translate" this:```
~$ firefox-3.7
Could not find compatible GRE between version **1.9.3a2pre and 1.9.3a2pre**.
```...?

I saw the same thing on 9.10 today, and
"sudo xulrunner-1.9.3 --register-global" doesn't solve the problem.

Don't know why. Two identical versions not compatible, that's beyond me.

---

### Post by idv on 2010-03-01
> **zika said:**
> How do You "translate" this:```
~$ firefox-3.7
Could not find compatible GRE between version 1.9.3a2pre and 1.9.3a2pre.
```...?

Looks like xulrunner was updated to 1.9.3a3pre, but firefox-3.7a3pre was built against xulrunner-1.9.3a2pre.

I assume that'll be fixed the next time the autobuilder runs, but for the moment, you can revert to 1.9.3a2 by grabbing the appropriate packages from http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/pool/main/x/xulrunner-1.9.3/

---

### Post by zika on 2010-03-02
> **idv said:**
> Looks like xulrunner was updated to 1.9.3a3pre, but firefox-3.7a3pre was built against xulrunner-1.9.3a2pre.

I assume that'll be fixed the next time the autobuilder runs, but for the moment, you can revert to 1.9.3a2 by grabbing the appropriate packages from [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/pool/main/x/xulrunner-1.9.3/](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/pool/main/x/xulrunner-1.9.3/)Fixed. Flash, still, doesn't work...

---

### Post by lovinglinux on 2010-03-02
Try to re-install flash using the [automated installer created by carlee](http://ubuntuforums.org/showthread.php?t=1414595). This tool  will install the best flash version according to your CPU architecture and will also attempt to remove any left-overs from previous  installations, thus helping to avoid conflicts with manually installed plugins.

---

### Post by lovinglinux on 2010-03-02
For those having problems with Firefox starting and don't get any errors on the terminal, verify if you have Prism installed and remove it. Prism is causing this problem here, using Firefox 3.6.

---

### Post by zika on 2010-03-02
> **lovinglinux said:**
> Try to re-install flash using the [automated installer created by carlee]("http://ubuntuforums.org/showthread.php?t=1414595"). This tool  will install the best flash version according to your CPU architecture and will also attempt to remove any left-overs from previous  installations, thus helping to avoid conflicts with manually installed plugins.No, I just use libflashplayer.so, without any installer, and it works in 3.6, chromium, opera... No left-overs, just clean install and libflashplayer.so put in the right place, the freshest one (64-bit, alpha)...
No need to use elaborate tools just to change a bulb... in this case just to DL and put a single file in the right place. Eventually, just to tell opera or whoever that a file is there to be used. It works for me...

---

### Post by lovinglinux on 2010-03-02
> **zika said:**
> No need to use elaborate tools just to change a bulb...

I suggest this tool because I have been noticing that there is a trend, specially among new users, of following multiple tutorials to achieve the same objective, without taking notes about how to revert the changes. So they end up with multiple versions of flash that might override the correct one installed from Synaptic. So while installing flash is pretty easy, this tool allows to avoid such problems, without tracking left-overs.

I know you are not a beginner, but I didn't know what else you have tried before. Just a suggestion anyway.

---

### Post by zika on 2010-03-02
> **lovinglinux said:**
> I suggest this tool because I have been noticing that there is a trend, specially among new users, of following multiple tutorials to achieve the same objective, without taking notes about how to revert the changes. So they end up with multiple versions of flash that might override the correct one installed from Synaptic. So while installing flash is pretty easy, this tool allows to avoid such problems, without tracking left-overs.

I know you are not a beginner, but I didn't know what else you have tried before. Just a suggestion anyway.It doesn't matter if I'm beginner or not. Only the final result matters. I think that only simple methods are efficient. I'm sorry if I did not state my point clearly... Just by erasing libflashplugin.so You revert everything to the previous state, if You use method I'm suggesting. I think that is the most appropriate and easiest way, especially for beginners. You can do it either in CLI or in GUI... Any kind of installer is, at least for me, gray box that can leave traces, even most experienced user might miss and that is open door for trouble... I always suggest avoiding usage of scripts and such things on Forums, at least for beginners, because testing of these scripts is, often, sparse... Never mind, that is just my .02$... Probably You're right, but I'm stubborn...

---

### Post by Daniel_le_Rouge on 2010-03-04
Hi!

I like to start my four favourite website on startup. I know that it works by separating the pages with a pide "|". So I did, but when I start the browser only two pages are opened. I have no idea what's going wrong. Maybe somebody here can help me?

I am using Firefox 3.6 on Ubuntu 9.10.

Thanks!

Daniel

---

### Post by fooman on 2010-03-04
> **Daniel_le_Rouge said:**
> Hi!

I like to start my four favourite website on startup. I know that it works by separating the pages with a pide "|". So I did, but when I start the browser only two pages are opened. I have no idea what's going wrong. Maybe somebody here can help me?

I am using Firefox 3.6 on Ubuntu 9.10.

Thanks!

Daniel

not sure of the problem,  but you could try it this way:

open firefox and open the 4 pages you want to have open when firefox starts.  close any other pages that are open...  then go to edit > preferences > general tab

click the "use current pages" button.

hope that helps.

---

### Post by Daniel_le_Rouge on 2010-03-05
> not sure of the problem, but you could try it this way:

open firefox and open the 4 pages you want to have open when firefox starts. close any other pages that are open... then go to edit > preferences > general tab

click the "use current pages" button.

hope that helps. 

Thanks for your answer.

I have already tried this, but it does not solve the problem. I also installed the add-on "MorningCoffee" to open the sites. But nothing changes. Only the first two pages are opened. I have no idea, what to do.

---

### Post by fooman on 2010-03-05
could be an add-on or something else in your firefox-profile causing it.  have you tried creating a new profile with the firefox profile manager to see if the problem persists?  to try that:

first close firefox if it is open,  then run the following in a terminal (applications > accessories > terminal):

```
firefox -P
```when it opens,  click "create profile",  then open the browser using the newly created profile and see if you can add those pages.  

hope that helps.

---

### Post by aloprot on 2010-03-05
Hello I have ubuntu 9.10 -64 bit version with firefox 3.5.8 and would like to upgrade to the latest version. Would you recommend that? and please if you can guide me in this process as i am a new and inexperienced user. Thank you!

---

### Post by Daniel_le_Rouge on 2010-03-06
I started Firefox in safe-mode (firefox -safe-mode) and reactivated one add-on after the other. At the end it was the extension "Tab Mix Plus" which caused the problem. But now everything is working out fine again.

Thanks for your help!

Daniel

---

### Post by lovinglinux on 2010-03-07
> **aloprot said:**
> Hello I have ubuntu 9.10 -64 bit version with firefox 3.5.8 and would like to upgrade to the latest version. Would you recommend that? and please if you can guide me in this process as i am a new and inexperienced user. Thank you!

See the [COLOR="Sienna"]**Installing Other Versions**[/COLOR] section in the first post. I recommend using mozillateam/firefox-stable ppa or the Ubuntuzilla method.

---

### Post by Daniel_le_Rouge on 2010-03-12
Hi again!

I have two little problem:

1. I recently update the add-on "Personal Menu" which hides the menu bar and creates one single to access the menu. Since the add-on update my menu bar is shown. Is there an option in about:config to hide the bar or another possibility?

2. I am using Firefox 3.6, but when I click on Help &#8594; About, the following appears at the end: "Mozilla/5.0 (X11; U; Linux i686; de-DE; rv:1.9.2) Gecko/20100115 Firefox/3.5"
The beginning of the dialogue clearly indicates FF 3.6. When I visit the FF add-ons page I am also identified as a 3.5 user. What can I do to solve this problem?

Thanks for your help!

Daniel

---

### Post by lovinglinux on 2010-03-12
> **Daniel_le_Rouge said:**
> 1. I recently update the add-on "Personal Menu" which hides the menu bar and creates one single to access the menu. Since the add-on update my menu bar is shown. Is there an option in about:config to hide the bar or another possibility?

Is it [this one](https://addons.mozilla.org/en-US/firefox/addon/3895)? It looks like the new version is not available for Linux. Anyway, you could use the extension [Hide Menu Bar](https://addons.mozilla.org/en-US/firefox/addon/4762), [Hide Gui Bars](https://addons.mozilla.org/en-US/firefox/addon/57805) or you could move all items from the Navigation Toolbar to the Menu Toolbar and hide the Navigation toolbar (View >>> Tollbars).

I have used the Personal Menu in the past, but it didn't work well. I prefer [Tiny Menu](https://addons.mozilla.org/en-US/firefox/addon/1455).

> **Daniel_le_Rouge said:**
> 2. I am using Firefox 3.6, but when I click on Help &#8594; About, the following appears at the end: "Mozilla/5.0 (X11; U; Linux i686; de-DE; rv:1.9.2) Gecko/20100115 Firefox/3.5"
The beginning of the dialogue clearly indicates FF 3.6. When I visit the FF add-ons page I am also identified as a 3.5 user. What can I do to solve this problem

How did you install Firefox 3.6? Do you have User Agent Switcher extension installed?

---

### Post by Daniel_le_Rouge on 2010-03-12
1. Worked out fine. I have just download the add-on and the Menu bar is gone.

2. I am updating Firefox with Ubuntuzilla.

---

### Post by lovinglinux on 2010-03-12
EDIT: wrong command

---

### Post by Daniel_le_Rouge on 2010-03-13
> **lovinglinux said:**
> Close Firefox, then open a terminal and run:

```
firefox-mozilla-build
```

Go to the about the About menu and check the version.

I tried, but I received the following error message:

```
daniel@daniel-laptop:~$ firefox-mozilla-build
firefox-mozilla-build: command not found

```

It seems, that there is a bigger problem than I thought. Normally I start Firefox with ```
firefox %u
```.

Any idea what's wrong?

---

### Post by lovinglinux on 2010-03-13
> **Daniel_le_Rouge said:**
> It seems, that there is a bigger problem than I thought. Normally I start Firefox with ```
firefox %u
```.

Any idea what's wrong?

The command above is correct. I was just guessing how to start the Ubuntuzilla package of Firefox, which is installed separately. Forget about it.

Try to re-install Firefox.

---

### Post by prodigy_ on 2010-03-14
Just a little bit of info:

I was totally unable to cure font issues in FF (3.6 from stable PPA) with any method suggested on the forums (created .fonts.conf; changed contents of /etc/fonts/conf.d; experimented with about:config). And no, I didn't forget "sudo dpkg-reconfigure fontconfig" after every step. That's what I see (it's easy to notice that FF menu bar isn't affected):

[Firefox, coloured shadows](http://img139.imageshack.us/img139/2497/ff1f.png)

[Chromium, normal rendering](http://img684.imageshack.us/img684/371/chr1.png)

Well, that's a real showstopper for me, so I'm back to Windows till 10.04.

---

### Post by TRG1 on 2010-03-14
Since I installed Ubuntu a few days ago, I have continued to use Firefox, but I've been missing Chrome.  Today I ran the Peacekeeper benchmark with Firefox and scored 287; I'm using an old Inspiron 2650. I had not been terribly unhappy with Firefox under Ubuntu, but decided to go ahead and install Chrome. I did, which was completely painless, and my benchmark score jumped up to 1035 so goodbye Firefox.

tom

---

### Post by SilverWave on 2010-03-22
**Upgrade Now!**                                                                             Time to upgrade  to 3.6.3 as there is a **Zero Day Exploit in 3.6!** and it wont be  fixed until the 30th.

Exploit Details Here: [Firefox 3.6 contains the zero-day vulnerability]("http://www.computerworld.com/s/article/9173874/German_government_urges_users_to_scrap_Firefox_3.6")

Update Firefox: [http://ubuntuforums.org/showthread.php?t=1352580&page=9](http://ubuntuforums.org/showthread.php?t=1352580&page=9)

__________________

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.3pre) Gecko/20100316 Ubuntu/10.04 (lucid) Namoroka/3.6.3pre - Build ID: 20100316073122

---

### Post by lovinglinux on 2010-03-22
> **SilverWave said:**
> **Upgrade Now!**                                                                             Time to upgrade  to 3.6.3 as there is a **Zero Day Exploit in 3.6!** and it wont be  fixed until the 30th.

Exploit Details Here: [Firefox 3.6 contains the zero-day vulnerability]("http://www.computerworld.com/s/article/9173874/German_government_urges_users_to_scrap_Firefox_3.6")

Update Firefox: [http://ubuntuforums.org/showthread.php?t=1352580&page=9](http://ubuntuforums.org/showthread.php?t=1352580&page=9)

__________________

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.3pre) Gecko/20100316 Ubuntu/10.04 (lucid) Namoroka/3.6.3pre - Build ID: 20100316073122

Thanks for posting here.

I have read all the info on those links and it is not clear if this vulnerability affects Linux. The Computer World article says it affects Windows, but I couldn't find any additional info.

---

### Post by SilverWave on 2010-03-22
> **lovinglinux said:**
> Thanks for posting here.

I have read all the info on those links and it is not clear if this vulnerability affects Linux. The Computer World article says it affects Windows, but I couldn't find any additional info.

I agree probably not but better to be cautious :-)

---

### Post by lovinglinux on 2010-03-22
> **SilverWave said:**
> I agree probably not but better to be cautious :-)

I agree. Nevertheless, I think NoScript would take care of this.

---

### Post by SilverWave on 2010-03-23
> **lovinglinux said:**
> I agree. Nevertheless, I think NoScript would take care of this.

Looks like it is related to a new font rendering tech introduced in 3.6

>  Title:      WOFF heap corruption due to  integer overflow
Impact:     Critical
Announced:  March 22, 2010
Reporter:   Evgeny Legerov
Products:   Firefox 3.6

Fixed in:   Firefox 3.6.2

   **Description**

  Security researcher **Evgeny Legerov** of Intevydis reported that the WOFF decoder contains an integer overflow in a font decompression routine.  This flaw could result in too small a memory buffer being allocated to store a downloadable font.  An attacker could use this vulnerability to crash a victim's browser and execute arbitrary code on his/her system.
On and I cant trust NoScript so dont use it.
I use a combination of AdblockPlus with this:
```
*$script,third-party,domain=~bbc.co.uk|~flickr.com|~youtube.com|~imdb.com|~ubuntuforums.org

```In combination with RequestPolicy.

Oh and just turning JavaScript off, if needed :-)

---

### Post by TheConsaw on 2010-03-23
So i updated firefox 3.6.2 with ubuntuzilla
and it killed my get64Flash I had installed
now i cant see any flash content, or cant install any flash plugin when it asks on a webpage

ive tried to uninsatll then reinstall FF, but its reinstalling as 3.6.2 everytime with all my addons etc,

how can i completely delete FF and flash
are re install, ill happily stay on 3.6 once i have flash working

thanks

---

### Post by lovinglinux on 2010-03-23
> **TheConsaw said:**
> So i updated firefox 3.6.2 with ubuntuzilla
and it killed my get64Flash I had installed
now i cant see any flash content, or cant install any flash plugin when it asks on a webpage

ive tried to uninsatll then reinstall FF, but its reinstalling as 3.6.2 everytime with all my addons etc,

how can i completely delete FF and flash
are re install, ill happily stay on 3.6 once i have flash working

thanks

Your profile don't get deleted when you re-install (see Profile section of the first post). Anyway, the get64Flash script does not install flash on your profile. 

Use the [tool created by carlee](http://ubuntuforums.org/showthread.php?t=1414595) to remove flash completely and install it again.

---

### Post by manoriax on 2010-04-09
This thread is great. Thank you!

---

### Post by lovinglinux on 2010-04-09
> **manoriax said:**
> This thread is great. Thank you!

Thanks. I'm glad you liked it. Firefox rocks :)

---

### Post by SilverWave on 2010-04-10
Interesting stuff:

[Bug 512489 - (support-L64) [tracking bug] officially support Linux x86-64 builds](https://bugzilla.mozilla.org/show_bug.cgi?id=512489)

Looks like 64-bit did not have JIT!

Hopefully this means that we will get a fully optimized 64bit ff rsn.

Cheers.

---

### Post by lovinglinux on 2010-04-10
> **SilverWave said:**
> Interesting stuff:

[Bug 512489 - (support-L64) [tracking bug] officially support Linux x86-64 builds](https://bugzilla.mozilla.org/show_bug.cgi?id=512489)

Looks like 64-bit did not have JIT!

Hopefully this means that we will get a fully optimized 64bit ff rsn.

Cheers.


Thanks for sharing.

Have you tried [Firefox Lorentz](http://ubuntuforums.org/showthread.php?t=1450678). The feature to prevent the browsing from crashing due to flash and other plugins is awesome.

---

### Post by SilverWave on 2010-04-11
> **lovinglinux said:**
> Thanks for sharing.

Have you tried [Firefox Lorentz]("http://ubuntuforums.org/showthread.php?t=1450678"). The feature to prevent the browsing from crashing due to flash and other plugins is awesome.

hmm I am using the dailies so probably...

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.4pre) Gecko/20100410 Ubuntu/10.04 (lucid) Namoroka/3.6.4pre - Build ID: 20100410093139 

I see a firefox, firefox-bin and npviewer.bin ...

tbh I don't get ff crashes so this will not be a great win for me.

Saying which it is a good idea and could be used to help with security at a later date.

The best news is that they are upping their game to compete with chrome and bringing out updates faster :-)

Cheers.

---

### Post by bcschmerker on 2010-04-11
Thank you, everybody who posted here, the foregoing will come in VERY handy when transferring Bookmarks during a major software-upgrade process, as I'm leaping from Mozilla® Firefox® 3.0.19 on Ubuntu® 8.04.4 to Firefox® 3.6.3 or 3.6.4 on the in-beta (as of 11 April 2010) Ubuntu® 10.04.  I am already planning my anticipated Extensions, based on what has worked to date on 3.6.3 on an eMachines®/Acer® EL1210-09 running Microsoft® Windows 6.0.6002; of course, not all Extensions will be identical---LinUX has better development tools, Windows better UI enhancements.

---

### Post by lovinglinux on 2010-04-12
**[SIZE="6"]Attention Firefox 3.6.4 [Namoroka] ubuntu-mozilla-daily users![/SIZE]**

It seems this is a bug affecting only Firefox 3.6.4 [Namoroka] installed using the *ubuntu-mozilla-daily* ppa. The browser crashes when viewing pages with flash content or content for other plugins.

This problem is due to a bad/old implementation of the new Lorentz technology that should prevent flash from crashing the browser. When opening a page with flash content using Namoroka 3.6.4, there is a new *firefox-bin* process loaded and the browser crashes. 

[Firefox 3.6.4 Lorentz from Mozilla](http://www.mozilla.com/en-US/firefox/lorentz/) doesn't behave like this and instead of loading a new *firefox-bin* process, it loads a *mozilla-runtime* process, which takes care of the flash content. It works like a charm and the browser doesn't crash or lock, even if you are viewing a messed up flash video.

So you have 3 options to fix your problem:

[LIST]
[*]disable *ubuntu-mozilla-daily* and reinstall Firefox to downgrade it to the default browser version
[*]temporarily turn off the flash process isolation following [these instructions](http://ubuntuforums.org/showpost.php?p=9104945&postcount=19)
[*]download [Firefox 3.6.4 Lorentz from Mozilla](http://www.mozilla.com/en-US/firefox/lorentz/) and follow [these instructions](http://lovinglinux.megabyet.net/?page_id=220##1---Manual-installation-of-fresh-final-releases-from-Mozilla-3) to install it.
[/LIST]

There are some considerations about using a ppa repository for Firefox that I would like to highlight:
[LIST]
[*]some ppa repositories like *ubuntu-mozilla-daily* update not only Firefox, but also other Mozilla applications, like Thunderbird.
[*]some ppa repositories like ubuntu-mozilla-daily install development versions of Firefox which does not have the official branding (logo and name). Although they use essentially the same source code, the browser could be called Shiretoko, Namoroka or something else.
[*] some repositories like *mozillateam/firefox-stable* doesn’t seem to be updated frequently, thus missing important security patches.
[*]some repositories like *ubuntu-mozilla-daily* upgrade Firefox with unstable releases, sometimes causing issues, like crashing the browser in specific conditions or preventing it from starting.
[/LIST]

Please Before adding a ppa repository for Firefox, please make sure you understand how the repository works, which version it will install and how often it will provide updates.

---

### Post by zika on 2010-04-12
If You try to use Lorentz, do not use "Check for updates" or You will end up with 3.6.4pre...

---

### Post by lovinglinux on 2010-04-12
> **zika said:**
> If You try to use Lorentz, do not use "Check for updates" or You will end up with 3.6.4pre...

My Lorentz is 3.6.4pre and it works fine. As I said, I believe this problem is affecting only the packages from ubuntu-mozilla-daily.

---

### Post by zika on 2010-04-12
> **lovinglinux said:**
> My Lorentz is 3.6.4pre and it works fine. As I said, I believe this problem is affecting only the packages from ubuntu-mozilla-daily.Lorentz works fine. But, If You choose "Check for updates" (in Lorentz: Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.4pre) Gecko/20100412 Lorentz/3.6.4pre) You will be offered to upgrade. Upgrade will not give You Lorentz, it will give You Namaroka 3.6.4pre... At least archive that is now available in ftp...

---

### Post by lovinglinux on 2010-04-12
> **zika said:**
> Lorentz works fine. But, If You choose "Check for updates" (in Lorentz: Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.4pre) Gecko/20100412 Lorentz/3.6.4pre) You will be offered to upgrade. Upgrade will not give You Lorentz, it will give You Namaroka 3.6.4pre... At least archive that is now available in ftp...

Sorry, you are right. I just did an update and I got Namoroka 3.6.4pre. Nevertheless, it doesn't behave badly, at least on my machine. 

I didn't actually tested Namoroka from ubuntu-mozilla-daily. My warning is based on multiple threads from ubuntu-mozilla-daily users.

 BTW, I'm running the 64bit Firefox version with 64bit flash.

---

### Post by lovinglinux on 2010-04-13
I was doing some maintenance on the site today, but the tutorial it is back online.

---

### Post by SilverWave on 2010-04-14
> **lovinglinux said:**
> **[SIZE=6]Attention Firefox 3.6.4 [Namoroka] ubuntu-mozilla-daily users![/SIZE]**

It seems this is a bug affecting only Firefox 3.6.4 [Namoroka] installed using the *ubuntu-mozilla-daily* ppa. The browser crashes when viewing pages with flash content or content for other plugins.

...

hmm odd I have never had a problem :-)

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.4pre) Gecko/20100410 Ubuntu/10.04 (lucid) Namoroka/3.6.4pre - Build ID: 20100410093139

But you do take a small risk as it is a daily build...

With great power...

---

### Post by lovinglinux on 2010-04-14
> **SilverWave said:**
> hmm odd I have never had a problem :-)

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.4pre) Gecko/20100410 Ubuntu/10.04 (lucid) Namoroka/3.6.4pre - Build ID: 20100410093139

But you do take a small risk as it is a daily build...

With great power...

There are lots of complains on the forums from Namoroka users.

---

### Post by zika on 2010-04-14
It seems that [https://launchpad.net/~ubuntu-mozilla-daily](https://launchpad.net/~ubuntu-mozilla-daily) is out of service... [ftp://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/) is, sort of up-to-date, excluding Lorentz, but ppa is sort of "dead"...

---

### Post by lovinglinux on 2010-04-14
> **zika said:**
> It seems that [https://launchpad.net/~ubuntu-mozilla-daily](https://launchpad.net/~ubuntu-mozilla-daily) is out of service... [ftp://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/) is, sort of up-to-date, excluding Lorentz, but ppa is sort of "dead"...

Wow. There is nothing there. I guess it was a good move after all to stop recommending the use of Firefox ppa repositories. I hope they come back, otherwise there will be lots of users complaining why they can't update Firefox anymore.

I guess this deserves a warning thread.

---

### Post by zika on 2010-04-14
> **lovinglinux said:**
> Wow. There is nothing there. I guess it was a good move after all to stop recommending the use of Firefox ppa repositories. I hope they come back, otherwise there will be lots of users complaining why they can't update Firefox anymore.Well, I've updated Lorentz and got Namoroka 3.6.5pre (Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.5pre) Gecko/20100414 Namoroka/3.6.5pre)... It seems it is a transition time... Flash works and everything is OK. So, Lorentz played its role... I hope ppa will restore its content...

---

### Post by lovinglinux on 2010-04-14
> **zika said:**
> Well, I've updated Lorentz and got Namoroka 3.6.5pre (Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.5pre) Gecko/20100414 Namoroka/3.6.5pre)... It seems it is a transition time... Flash works and everything is OK. So, Lorentz played its role... I hope ppa will restore its content...

The same is happening with ubuntu-mozilla-security.

---

### Post by zika on 2010-04-14
> **lovinglinux said:**
> The same is happening with ubuntu-mozilla-security.I think they entangled themselves too much with 1.9.1, 1.9.2, 1.9.3, 3.5, 3.6, 3.6, Lorentz, transition from 3.5 to 3.6 while on the road, it is not easy to follow that tree anymore...

---

### Post by SilverWave on 2010-04-14
> [        firefox -  3.6.4~hg20100410r34032+nobinonly-0ubuntu1~umd1       ]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+sourcepub/1073678/+listing-archive-extra")                                  [(changes  file)]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+files/firefox_3.6.4%7Ehg20100410r34032+nobinonly-0ubuntu1%7Eumd1_source.changes")                                 [fta]("https://launchpad.net/%7Efta")                        2010-04-10     Published     Lucid     Web            [IMG]https://launchpad.net/@@/yes[/IMG]                             **Publishing details**

        
[LIST]
[*]       **Published**       on 2010-04-10
[/LIST]
                   **Changelog**

         firefox (3.6.4~hg20100410r34032+nobinonly-0ubuntu1~umd1) lucid; urgency=low

  [ Micah Gersten ]
  * Rebase patch after upstream landing of Lorentz branch
    - update debian/patches/bz460917_att350845_reload_new_plugins.patch

  [ Fabien Tassin ]
 -- Fabien Tassin <email address hidden>   Sat, 10 Apr 2010 05:28:18 +0200            **Available diffs**

     
[LIST]
[*]                                    [3.6.4~hg20100408r34022+nobinonly-0ubuntu1~umd1  to 3.6.4~hg20100410r34032+nobinonly-0ubuntu1~umd1]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+files/firefox_3.6.4%7Ehg20100408r34022+nobinonly-0ubuntu1%7Eumd1_3.6.4%7Ehg20100410r34032+nobinonly-0ubuntu1%7Eumd1.diff.gz")              (17.0 KiB)
[/LIST]
   

Hmm interesting

> $ apt-cache policy firefox
firefox:
  Installed: 3.6.4~hg20100410r34032+nobinonly-0ubuntu1~umd1
  Candidate: 3.6.4~hg20100410r34032+nobinonly-0ubuntu1~umd1
  Version table:
 *** 3.6.4~hg20100410r34032+nobinonly-0ubuntu1~umd1 0
        500 [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/) lucid/main Packages
        100 /var/lib/dpkg/status
     3.6.3+nobinonly-0ubuntu2 0
>      **Latest updates**

                  
[LIST]
[*]           **firefox-3.7**                        four days             ago           
          Failed to build:                        [amd64]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/1685103")             [i386]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/1685104")             [lpia]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/1685105")
[*]           **xulrunner-1.9.2**                        four days             ago           
          Successfully built
[*]           **firefox**                        four days             ago           
          Failed to build:                        [amd64]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/1685125")             [i386]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/1685126")             [lpia]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/1685127")
[*]           **xulrunner-1.9.1**                        four days             ago           
          Successfully built
[*]           **xulrunner-1.9.3**                        four days             ago           
          Failed to build:                        [amd64]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/1685092")             [i386]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/1685093")             [lpia]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa/+build/1685094")
[/LIST]
          


>Currently                      0           packages building

I think they are in the middle of a change over to reflect changes at Mozilla.

---

### Post by lovinglinux on 2010-04-14
> **zika said:**
> It seems that [https://launchpad.net/~ubuntu-mozilla-daily](https://launchpad.net/~ubuntu-mozilla-daily) is out of service... [ftp://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/) is, sort of up-to-date, excluding Lorentz, but ppa is sort of "dead"...

Is that something normal to happen with a ppa, like a maintenance thing?

---

### Post by zika on 2010-04-15
> **lovinglinux said:**
> Is that something normal to happen with a ppa, like a maintenance thing?Who knows. But, it's alive...

---

### Post by bcschmerker on 2010-04-15
Thanks for the heads up on the situation with Mozilla® Firefox® Lorentz 3.6.3plugin1; I'm already planning on a stable version for my Dist-Upgrade from Hardy to Lucid.  Mozilla® may very well have a stable 3.6.4 by the time Lucid is officially released to market (they're still testing as of 15 April 2010).

---

### Post by SilverWave on 2010-04-16
> **lovinglinux said:**
> Is that something normal to happen with a ppa, like a maintenance thing?

Back in business with a shiny new 3.6.5 Installed.

[More here]("http://ubuntuforums.org/showpost.php?p=9133136&postcount=85").

---

### Post by lovinglinux on 2010-04-17
> **eMJayy said:**
> The developers have resolved the Namoroka flash process isolation issue that was affecting users of the daily PPA version from mozilla. 

I just got a Namoroka update which appropriately isolates the flash plugin without crashing the browser. When the flash process isolation feature is turned on, the browser moves the flash data to a separate process called *plugin-container*, which prevents flash from bringing down the whole browser session. 

Those persons who turned off flash process isolation to fix the freezing issue should now apply this latest update and can now re-enable flash isolation if they choose to.

[color="Sienna"][list]

[*]**Source:** [[color="DarkSlateGray"] Re: Update Totally Hosed My Firefox[/color]]("http://ubuntuforums.org/showpost.php?p=9135777")

[*]**Tags:** [[color="DarkSlateGray"]Update Totally Hosed My Firefox[/color]]("http://www.google.com/search?q=Update+Totally+Hosed+My+Firefox+site:ubuntuforums.org")

[*]**Powered by: **[[color="DarkSlateGray"]QuoteMarks[/color]]("http://lovinglinux.megabyet.net/?page_id=555")[/list][/color]

---

### Post by cmcanulty on 2010-04-18
Lately whenever I do a clean install and import my bookmarks as a .html file they all show up in folders under bookmarks but when I try tp save a new bookmark I can't access the folders to save to and so I end up with a big disorganized mess. Also the backup shows 2 folder lists with identical folders under the bookmarks menu. I use LOTS of bookmarks and really need to keep them organized. I have seen other people post this problem but never a solution, thank you

---

### Post by lovinglinux on 2010-04-18
> **cmcanulty said:**
> Lately whenever I do a clean install and import my bookmarks as a .html file they all show up in folders under bookmarks but when I try tp save a new bookmark I can't access the folders to save to and so I end up with a big disorganized mess. Also the backup shows 2 folder lists with identical folders under the bookmarks menu. I use LOTS of bookmarks and really need to keep them organized. I have seen other people post this problem but never a solution, thank you

What is the source of the bookmarks, your old profile? You could try to export them as json instead of HTML, then simply restore the json backup in the new profile.

Another alternative would be to manually back the file **places.sqlite** from your FF profile or use [FEBE](https://addons.mozilla.org/en-US/firefox/search/?q=FEBE) extension to do that. 

You could also import those HTML into an [Xmarks](https://addons.mozilla.org/en-US/firefox/search/?q=Xmarks) account and sync the new profile with it.

Anyway, I never use HTML exporting feature, I prefer to simply backup the sqlite database. Less conversions, less trouble.

---

### Post by cmcanulty on 2010-04-18
No I exported them to an html and then imported them

---

### Post by cmcanulty on 2010-04-18
They get imported fine that isn't the problem. The issue is when I try to save new bookmarks there is no way to save them to a folder as the folders won't show up in the save options

---

### Post by lovinglinux on 2010-04-18
> **cmcanulty said:**
> They get imported fine that isn't the problem. The issue is when I try to save new bookmarks there is no way to save them to a folder as the folders won't show up in the save options

I know that. What I think is that importing as HTML might be messing with the database structure someway or corrupting the sqlite file. That's why I suggested the other methods.

---

### Post by cmcanulty on 2010-04-18
Oh I see. But for this time I guess it is too late. Last time I tried the firefox backup utility that was supposed to save all your user stuff and that saved nothing so it was totally useless . So next time I will try one of your suggestions, thanks

---

### Post by cmcanulty on 2010-04-18
OK I have an Xmarks account  I synced them but still none of my folders show up when I try to add  a new bookmark. FF really has developed some bugs this past year.

---

### Post by lovinglinux on 2010-04-18
> **cmcanulty said:**
> OK I have an Xmarks account but how do I sync it with my FF profile

Have you installed Xmarks extension?

---

### Post by cmcanulty on 2010-04-18
Yes I already had it and I synced it but still I can only save new bookmarks as is without putting them into a folder

---

### Post by lovinglinux on 2010-04-18
> **cmcanulty said:**
> Yes I already had it and I synced it but still I can only save new bookmarks as is without putting them into a folder

Could you post a screenshot of the Save Bookmark dialog?

---

### Post by lovinglinux on 2010-04-21
Mozilla [has released a beta version](http://blog.mozilla.com/blog/2010/04/20/firefox-3-6-4-beta-available-for-download-and-testing/) of the most anticipated Firefox 3.6.4 [Lorentz], which brings a new feature that prevents the browsing from crashing when viewing problematic flash, quicktime and silverlight content. I have already tested Lorentz before the beta and it works like a charm. This is really a nice feature. Kudos for Mozilla.

Want to make a test? Visit [this video](http://s114.photobucket.com/albums/n274/crankmy5150/?action=view&current=Jeepknocking.flv) with Firefox 3.6.4. **Warning:** I don't know what is the content of that video, I just know it will freeze or crash Firefox 100% of the time, if you are not using Lorentz.

The new Firefox will give you the warning below, where the flash video was supposed to load, instead of crashing the browser.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=153914&stc=1&d=1271824196[/IMG]

To easily test it without closing your default Firefox version or profile, use my extension [FoxTester](http://ubuntuforums.org/showthread.php?p=9109976). Please keep in mind this extension is still experimental and under development. Nevertheless, it works fine for me.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=153915&stc=1&d=1271825493[/IMG]

---

### Post by Bobhuber on 2010-04-23
I've compiled the most recent version of firefox 3.6.3 which now happens to be the release version in Lucid. Do you know how to make a link to the packaged version before I install the new one compiled for my processor.

---

### Post by lovinglinux on 2010-04-23
> **Bobhuber said:**
> I've compiled the most recent version of firefox 3.6.3 which now happens to be the release version in Lucid. Do you know how to make a link to the packaged version before I install the new one compiled for my processor.

What do you mean? You want to make a launcher for the old version? Just use /usr/bin/firefox for the old one and /usr/local/bin/firefox for the new one.

---

### Post by Bobhuber on 2010-04-23
> **lovinglinux said:**
> What do you mean? You want to make a launcher for the old version? Just use /usr/bin/firefox for the old one and /usr/local/bin/firefox for the new one.
Thanks very much. Thats exactly what I wanted. Still learning but not doing to bad for an old man.

---

### Post by lovinglinux on 2010-04-23
> **Bobhuber said:**
> Thanks very much. Thats exactly what I wanted. Still learning but not doing to bad for an old man.

Don't worry, you are doing just fine. When I read your question I was making a pause from several hours straight doing some programming. My brain was overloaded :)

---

### Post by Chame_Wizard on 2010-04-24
Can someone tell me how the fix the tabs:Everything I click on the hyperlinks,it's open in a new window(?) instead to the current tab on the right.:(

---

### Post by lovinglinux on 2010-04-24
> **Chame_Wizard said:**
> Can someone tell me how the fix the tabs:Everything I click on the hyperlinks,it's open in a new window(?) instead to the current tab on the right.:(

Go to Edit >> Preferences >> Tabs...

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=154194&stc=1&d=1272111316[/IMG]

---

### Post by Chame_Wizard on 2010-04-24
> **lovinglinux said:**
> Go to Edit >> Preferences >> Tabs...

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=154194&stc=1&d=1272111316[/IMG]

For some weird reason,it gives me the opposite effect(ubuntuzilla FF 3.6.3.):lolflag:

---

### Post by lovinglinux on 2010-04-24
> **Chame_Wizard said:**
> For some weird reason,it gives me the opposite effect(ubuntuzilla FF 3.6.3.):lolflag:

Create a new profile and test if the problems persist. See the Profile section of the tutorial.

---

### Post by SilverWave on 2010-04-27
> Firefox-3.6  - One Daily A Month
 One daily a month from ubuntu-mozilla-daily.
 The latest firefox without the update hassle
 $ sudo add-apt-repository ppa:silverwave/one-daily-a-month-0
**Hi Guys, I have created a PPA so that I have a reasonably up-to-date Firefox but don't get overwhelmed with updates**.

[https://launchpad.net/~silverwave/+archive/one-daily-a-month-0]("https://launchpad.net/%7Esilverwave/+archive/one-daily-a-month-0")

Firefox 3.6 and xulrunner will be the only Packages in this PPA so you wont update other stuff in error.

>                  
[IMG]https://launchpad.net/@@/package-source[/IMG] firefox                                               3.6.5~hg20100427r34130+nobinonly-0ubuntu1~umd1                                                                  [Fabien Tassin]("https://launchpad.net/%7Efta")                                      (1 hour ago)
[IMG]https://launchpad.net/@@/package-source[/IMG]                 xulrunner-1.9.2                                               1.9.2.5~hg20100427r34130+nobinonly-0ubuntu1~umd1                                                                  [Fabien Tassin]("https://launchpad.net/%7Efta")                                      (1 hour ago)                                  Its for Lucid users - I have tested the 64bit version OK.

Same idea for Firefox-3.7
> 
Firefox-3.7 - One Daily A Month
 One daily a month from ubuntu-mozilla-daily.
 The latest firefox without the update hassle
 $ sudo add-apt-repository ppa:silverwave/one-daily-a-month-1

I will be updating the packages on the 1st of each month.
(unless there is a security issue etc.).

Note:
[I]Low safety, daily packages have not undergone any quality  assurance.
Sometimes very safe but sometimes may not work at all[/I].

---

### Post by lovinglinux on 2010-04-27
> **SilverWave said:**
> **Hi Guys, I have created a PPA so that I have a reasonably up-to-date Firefox but don't get overwhelmed with updates**.

[https://launchpad.net/~silverwave/+archive/one-daily-a-month-0]("https://launchpad.net/~silverwave/+archive/one-daily-a-month-0")

Firefox 3.6 and xulrunner will be the only Packages in this PPA so you wont update other stuff in error.

Its for Lucid users - I have tested the 64bit version OK.

Same idea for Firefox-3.7
I will be updating the packages on the 1st of each month.
(unless there is a security issue etc.).

Note:
[I]Low safety, daily packages have not undergone any quality  assurance.
Sometimes very safe but sometimes may not work at all[/I].

I liked the title of the PPA :)

Thanks for sharing. I'm going to test it later.

---

### Post by SilverWave on 2010-04-28
> **lovinglinux said:**
> I liked the title of the PPA :)

Thanks for sharing. I'm going to test it later.

That would be great... its good to have a sanity check :-D

I have given it some thought and will support both Lucid and Karmic with separate PPA's for Firefox-3.6 and 3.7.

[https://launchpad.net/~silverwave]("https://launchpad.net/%7Esilverwave")

Details follow:

> Firefox-3.6 - One Daily A Month -  Lucid
 One daily a month from ubuntu-mozilla-daily.
 The latest firefox without the update hassle.
 $ sudo add-apt-repository ppa:silverwave/one-daily-a-month-0


Firefox-3.7  - One Daily A Month - Lucid
 One daily a month from ubuntu-mozilla-daily.
 The latest firefox without the update hassle.
 $ sudo add-apt-repository ppa:silverwave/one-daily-a-month-1[I]I have tested the packages in a virtual machine running Lucid  10.04, 32bit and 64bit.
Both Firefox-3.6 and 3.7 install and open with no problem.[/I]

> Firefox-3.6  - One Daily A Month - Karmic
 One daily a month from ubuntu-mozilla-daily.
 The latest firefox without the update hassle.
 $ sudo add-apt-repository ppa:silverwave/one-daily-a-month-2


Firefox-3.7  - One Daily A Month - Karmic
 One daily a month from ubuntu-mozilla-daily.
 The latest firefox without the update hassle.
 $ sudo add-apt-repository ppa:silverwave/one-daily-a-month-3[I]I have tested the packages in a virtual machine running Karmic 9.10,  32bit and 64bit.
Both Firefox-3.6 and 3.7 install and open with no problem.


[/I]Latest info will be posted here: [http://ubuntuforums.org/showthread.php?t=1352580](http://ubuntuforums.org/showthread.php?t=1352580)[URL="http://ubuntuforums.org/showthread.php?t=1352580"]
[/URL]

---

### Post by lovinglinux on 2010-04-28
> **SilverWave said:**
> That would be great... its good to have a sanity check :-D

It will have to be later tho. I'm in the process of releasing a new version of Umarks and since it could help users that will install Lucid from scratch tomorrow, then I want to release it today. I'm currently going nuts with the last tests and tutorial development. But I'm really excited about this new version.

---

### Post by lovinglinux on 2010-05-06
**Ghostery is slowing down tab switching**

If you are experiencing slow tab switching in Firefox recently, disable Ghostery extension. I have noticed this behavior recently and I thought it was a problem with version 2.1.1, released on May 3rd, but version 2.1 also affects tab switching, although no so intensively. I didn't test older versions.

---

### Post by Bobhuber on 2010-05-07
I've downloaded and am trying to manually install a developers release of the Firetray extension in Firefox.By right clicking on the xpi file and telling it to open using Firefox it installs the extension as if I had opened Firefox from a terminal using an empty profile and does not add it to my existing profile and extensions. Help
Just figured out one way. Created a task bar shortcut to open firefox and dragged the file over it with a mouse.

---

### Post by lovinglinux on 2010-05-07
> **Bobhuber said:**
> I've downloaded and am trying to manually install a developers release of the Firetray extension in Firefox.By right clicking on the xpi file and telling it to open using Firefox it installs the extension as if I had opened Firefox from a terminal using an empty profile and does not add it to my existing profile and extensions. Help

What version of Ubuntu and Firefox you are using? Have you installed a non-default Firefox version? Have you tried to do this with Firefox closed?

---

### Post by Bobhuber on 2010-05-07
> **lovinglinux said:**
> What version of Ubuntu and Firefox you are using? Have you installed a non-default Firefox version? Have you tried to do this with Firefox closed?
I'm using Lucid.I am using a compiled version (my own) of Firefox 3.6.3. I specified the exact location for  both the system install and my compiled version (I tried them both) after I realized what was going on to see if it made any difference.I tried it both ways as far as having firefox open.Obviously it opens Firefox automatically when you attempt to install the extention.

---

### Post by lovinglinux on 2010-05-07
> **Bobhuber said:**
> I specified the exact location for  both the system install and my compiled version (I tried them both) after I realized what was going on to see if it made any difference.

Where did you setup the paths? What are the paths?

> **Bobhuber said:**
> Obviously it opens Firefox automatically when you attempt to install the extention.

So it only happens if Firefox is closed?

---

### Post by Bobhuber on 2010-05-07
> **lovinglinux said:**
> Where did you setup the paths? What are the paths?
The paths are the default (in fact you gave them to me)
System Package - /usr/local/lib/firefox-3.6.3/firefox with what I guess is a symlink in /usr/bin/firefox to the aforementioned (not my strong point)
Compiled - /usr/local/bin/firefox
So it only happens if Firefox is closed?
Nope. It will open up a new occurrence of Firefox when you attempt to install the extension.
I also just did some playing around with some HTML files that I have on my system.
If I double click on them it does the same thing (opens the file with what I'll call a barebones  Firefox with no extensions as if I had used the terminal).
Checked (and changed) the Preferred applications under System-Preferences and it doesn't make any difference. No clue as to whats going on.

---

### Post by lovinglinux on 2010-05-07
> **Bobhuber said:**
> Nope. It will open up a new occurrence of Firefox when you attempt to install the extension.
I also just did some playing around with some HTML files that I have on my system.
If I double click on them it does the same thing (opens the file with what I'll call a barebones  Firefox with no extensions as if I had used the terminal).
Checked (and changed) the Preferred applications under System-Preferences and it doesn't make any difference. No clue as to whats going on.

Can you remove the compiled version and the default one, then re-install only the default too see if it works?

---

### Post by Bobhuber on 2010-05-07
> **lovinglinux said:**
> Can you remove the compiled version and the default one, then re-install only the default too see if it works?
I have Karmic loaded on another partition thats doing the same thing when I double click on an HTML file so I'll play with that a bit also.Got to be something with the file manager and not Firefox that is causing the problem.A shortcut on the desktop or in the panel with just the command Firefox will run the compiled version with extentions (as it should). If I specify a path to the system installed Firefox that opens correctly also with the extensions which leads me to believe the symlinks are correct.

---

### Post by lovinglinux on 2010-05-07
> **Bobhuber said:**
> I have Karmic loaded on another partition thats doing the same thing when I double click on an HTML file so I'll play with that a bit also.Got to be something with the file manager and not Firefox that is causing the problem.A shortcut on the desktop or in the panel with just the command Firefox will run the compiled version with extentions (as it should). If I specify a path to the system installed Firefox that opens correctly also with the extensions which leads me to believe the symlinks are correct.

I also believe is a Gnome or Nautilus issue. I can only think that your Gnome settings are messing with this. Nevertheless, is very weird that Karmic on the other partition is doing the same thing.  You could try to create a new Ubuntu user to see if it works.

---

### Post by Bobhuber on 2010-05-07
> **lovinglinux said:**
> I also believe is a Gnome or Nautilus issue. I can only think that your Gnome settings are messing with this. Nevertheless, is very weird that Karmic on the other partition is doing the same thing.  You could try to create a new Ubuntu user to see if it works.
Problem Solved (or at least figured out). I have a panel shortcut to open the Nautilus file manager that I was opening with gksu (root privileges). Everything done thru the file manager is now done as if you had opened up the associated programs as root thru the terminal.Thanks for your help and sorry to be a bother.

---

### Post by lovinglinux on 2010-05-07
> **Bobhuber said:**
> Problem Solved (or at least figured out). I have a panel shortcut to open the Nautilus file manager that I was opening with gksu (root privileges). Everything done thru the file manager is now done as if you had opened up the associated programs as root thru the terminal.Thanks for your help and sorry to be a bother.

I' glad you figured it out. I strongly suggest you check your home directory and files permissions, since you might have changed them while using Nautilus with gksu.

---

### Post by Bobhuber on 2010-05-07
> **lovinglinux said:**
> I' glad you figured it out. I strongly suggest you check your home directory and files permissions, since you might have changed them while using Nautilus with gksu.
Not a problem just me and the dog using the computer.:lolflag:

---

### Post by lovinglinux on 2010-05-07
> **Bobhuber said:**
> Not a problem just me and the dog using the computer.:lolflag:

That's not the issue :)

The problem is that some applications might fail to save data to your directories, due to permissions issues.

---

### Post by lovinglinux on 2010-05-10
I'm currently in the process of moving the tutorial to a new site. Please give me a couple of days to update the links.

---

### Post by lovinglinux on 2010-05-10
Tutorial site is up again. Well, most of it... :oops:

I still need to add the most common trouble shooting issues and the section on how to compile Firefox. 

I hope you like the new site. Is much faster than the other one and now there is a RSS feed and a Twitter account just for the tutorials.

---

### Post by ozzyprv on 2010-05-16
Great tutorial. THANK YOU.
The section that particularly helped me was "installing other versions".

PS: Great avatar as well.

---

### Post by lovinglinux on 2010-05-17
> **ozzyprv said:**
> Great tutorial. THANK YOU.
The section that particularly helped me was "installing other versions".

PS: Great avatar as well.

You are welcome.

---

### Post by Bobhuber on 2010-05-19
Having downloaded and compiled several different versions of Firefox source code I've been looking at the Firefox branch structure and pre releases. I'm not quite sure I understand all I know about it.Can you explain for instance what the difference is in the files you would find at Mozilla-Central as opposed to Mozilla 1-9.2 with the same pre-release name.The Wiki tree structure shows Mozilla-Central as a bed for 3.7/1.9.3 work and Mozilla 1-1.9.2 as a bed for 3.6/1.9.2 work.Confusing but I confuse myself sometimes. 
Never mind I just figured out my own question. Thanks

---

### Post by wojox on 2010-05-19
> **lovinglinux said:**
> 
I hope you like the new site. Is much faster than the other one and now there is a RSS feed and a Twitter account just for the tutorials.

Cool, looks good and is a lot faster than your old site. :)

---

### Post by lovinglinux on 2010-05-19
> **wojox said:**
> Cool, looks good and is a lot faster than your old site. :)

Thanks. I was going crazy with the speed of the old one. :)

---

### Post by Bobhuber on 2010-05-20
I'm not sure that this hasn't been posted in this thread somewhere else but here goes.
I've been having a problem with disappearing tool bar icons in one of the most recent versions of Firefox ( 3.7a4).After searching the posts I found out I'm not alone and it's not just this version of FF. Seems that the Ubufox extension in Ubuntu is causing some  problems. After removing it all is well with the tool bar again. Hope this helps someone else.

---

### Post by lovinglinux on 2010-05-20
> **Bobhuber said:**
> I'm not sure that this hasn't been posted in this thread somewhere else but here goes.
I've been having a problem with disappearing tool bar icons in one of the most recent versions of Firefox ( 3.7a4).After searching the posts I found out I'm not alone and it's not just this version of FF. Seems that the Ubufox extension in Ubuntu is causing some  problems. After removing it all is well with the tool bar again. Hope this helps someone else.

Thanks for the tip.

---

### Post by lovinglinux on 2010-05-26
Just added a new article on how to fix corrupted profiles.

---

### Post by foresthill on 2010-05-29
I have been having an odd problem in Firefox that occurs when I post on message boards. I will start typing and one of two things happen:

1.) Letters do not appear when I type. Sometimes I have to begin a sentence two or three times before the characters finally start to appear. It's not a "lag" problem (where the letters appear after a few seconds) the keyboard just flat out does not respond.

or

2.) I begin typing and my recycle bin opens, one instance for each character I type. So it I type out a ten characters, I have 10 instances of my recycle bin open, which I then have to close one by one and begin my sentence all over again. No text appears.

I have two laptops, one running 9.10 and the other one running 9.10 and 10.4. This same thing happens on both machines, on and off. So I don't think it's a hardware problem.

Seems to be a Firefox problem, since this is the only common denominator. Though I run Ad Block on both machines and use a wireless broadband card.

One further unrelated Firefox problem is one I have with spellcheck. Firefox thinks I am using UK English (I'm in the US). Therefore, words such as "color" are underlined in red as misspelled unless I spell them "colour". It's a very minor annoyance, but is there a Firefox option to set locale?

Thanks in advance!

---

### Post by lovinglinux on 2010-05-29
> **foresthill said:**
> I have been having an odd problem in Firefox that occurs when I post on message boards. I will start typing and one of two things happen:

1.) Letters do not appear when I type. Sometimes I have to begin a sentence two or three times before the characters finally start to appear. It's not a "lag" problem (where the letters appear after a few seconds) the keyboard just flat out does not respond.

or

2.) I begin typing and my recycle bin opens, one instance for each character I type. So it I type out a ten characters, I have 10 instances of my recycle bin open, which I then have to close one by one and begin my sentence all over again. No text appears.

I have two laptops, one running 9.10 and the other one running 9.10 and 10.4. This same thing happens on both machines, on and off. So I don't think it's a hardware problem.

Seems to be a Firefox problem, since this is the only common denominator. Though I run Ad Block on both machines and use a wireless broadband card.

Have you tried the [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html)?

> **foresthill said:**
> One further unrelated Firefox problem is one I have with spellcheck. Firefox thinks I am using UK English (I'm in the US). Therefore, words such as "color" are underlined in red as misspelled unless I spell them "colour". It's a very minor annoyance, but is there a Firefox option to set locale?

Thanks in advance!

Type **about[noparse]:[/noparse]config** in the address bar, then search for **spellchecker.dictionary**. Right-click on that preference and select **Modify**. Set as **en-US**.

---

### Post by foresthill on 2010-05-29
Hey, thanks for the Spellcheck tip. I will peruse the other section you linked to as well and post the answer if i find it. Thanks again!

---

### Post by lovinglinux on 2010-05-30
It seems the current version of Swiftfox has a bug that prevents it from detecting plugins. It doesn't recognize any newly installed plugins. If you start Firefox using the same user profile, then close Firefox and start Swiftfox it does recognize the plugins, but they don't work. I would recommend switching to the default Firefox for now.

---

### Post by ChrisHuntley on 2010-06-01
> **kevdog said:**
> I haven't tried really anything in this thread yet, however just wanted to thank your for the time that went into preparing the advice in the guide.  Very informative and a job well done!

Yeah, Kev, such great info.  I love Firefox, and I'm particularly thankful for the link about where the Firefox profile page is stored.  I'd be lost without my passwords, cookies, and bookmarks, so the first thing I did when I learned the location was backed it up with my carbonite.  Thanks so much LovingLinux.

---

### Post by foresthill on 2010-06-02
> **foresthill said:**
> I have been having an odd problem in Firefox that occurs when I post on message boards. I will start typing and one of two things happen:

1.) Letters do not appear when I type. Sometimes I have to begin a sentence two or three times before the characters finally start to appear. It's not a "lag" problem (where the letters appear after a few seconds) the keyboard just flat out does not respond.

or

2.) I begin typing and my recycle bin opens, one instance for each character I type. So it I type out a ten characters, I have 10 instances of my recycle bin open, which I then have to close one by one and begin my sentence all over again. No text appears.

I have two laptops, one running 9.10 and the other one running 9.10 and 10.4. This same thing happens on both machines, on and off. So I don't think it's a hardware problem.

Seems to be a Firefox problem, since this is the only common denominator. Though I run Ad Block on both machines and use a wireless broadband card.


While I did not find a solution for this issue, I did find a bug report on it:

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/584513](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/584513)

---

### Post by lovinglinux on 2010-06-02
> **foresthill said:**
> While I did not find a solution for this issue, I did find a bug report on it:

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/584513](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/584513)

Try to create a new Ubuntu user and see if the problem persists when using that account. This way you can rule out any Gnome settings issue, since the new user will have a clean set of settings for everything, not only Firefox.

---

### Post by ewg on 2010-06-09
Thanks for doing this.
Ever since my update to  Ubuntu 10.04 with Firefox 3.6.3 I've had flash issues. The only plugins I see are "ice tea" (don't need), something for an iphone(don't need) and a version 9 of the flash plug in. I've tried over and over to update the flash plug in with no luck. Ubuntu synaptic says the new version is installed already.  I suspect your flash-aid extension would help but I loaded it and don't see it. It was put in a 'chrome' folder in my documents directory but it does not run when I start firefox. Did I miss something? Why does it extract to a chrome folder? What do I need to do for it to run? 

Thanks,

---

### Post by lovinglinux on 2010-06-09
> **ewg said:**
> Thanks for doing this.
Ever since my update to  Ubuntu 10.04 with Firefox 3.6.3 I've had flash issues. The only plugins I see are "ice tea" (don't need), something for an iphone(don't need) and a version 9 of the flash plug in. I've tried over and over to update the flash plug in with no luck. Ubuntu synaptic says the new version is installed already.  I suspect your flash-aid extension would help but I loaded it and don't see it. It was put in a 'chrome' folder in my documents directory but it does not run when I start firefox. Did I miss something? Why does it extract to a chrome folder? What do I need to do for it to run? 

Thanks,

Look at Firfefox status bar (the one at the bottom). You should see a flash-aid icon there. Click it and select the "Install" option. It will guide you through the flash installation process.

---

### Post by ewg on 2010-06-09
Thanks for the reply but there is no icon anywhere.

---

### Post by lovinglinux on 2010-06-09
> **ewg said:**
> Thanks for the reply but there is no icon anywhere.

There is also an icon that you can drag to the main toolbar. Click the toolbar then customize and drag the FLASH-AID icon.

---

### Post by lovinglinux on 2010-06-09
> **ewg said:**
> I suspect your flash-aid extension would help but I loaded it and don't see it. It was put in a 'chrome' folder in my documents directory but it does not run when I start firefox. Did I miss something? Why does it extract to a chrome folder? What do I need to do for it to run? 

Thanks,

Sorry, I didn't catch the problem when I first read your post. You should not extract the xpi file, but open it with Firefox. It will install the extension automatically. After restarting Firefox, it will prompt for Flash installation. You can delete the chrome folder in your desktop, you can't run the extension from there.

---

### Post by ewg on 2010-06-09
Thanks. That did the trick, I'm good to go!

---

### Post by emarkay on 2010-06-10
So where are we here - Lucid and Maverick?  As a Lucid LTS devotee, and a FF 3.6.3 from the official repo user, what's still the optimum optimize for FF? Are these still "the best"? 

  	 	 	 	 	 	  [SIZE=2]Browser.bookmarks.max_backups=2  browser.sessionhistory.max_entries=5 Plugin.expose_full_path=T[/SIZE]
[SIZE=2]Sessionstore.max_tabs_undo=3  Sessionstore.max_windows_undo=1 
[/SIZE]
[SIZE=2]dom.popup_maximum=5  
[/SIZE]
[SIZE=2]DNS.disableIPv6=True[/SIZE]
[SIZE=2]layout.spellcheckDefault=2  
[/SIZE]
[SIZE=2]Max-connections=48[/SIZE]
[SIZE=2]Max-connections-per-server=24[/SIZE]
[SIZE=2]Max-persistent-connections-per-proxy=12 
[/SIZE]
[SIZE=2]Max-persistent-connections-per-server=12[/SIZE]
[SIZE=2] Network-prefetch-next=False [/SIZE]
[SIZE=2]**Add Integer:** 
[/SIZE]
[SIZE=2]browser**.**cache.memory.capacity=24576[/SIZE]
[SIZE=2]nglayout.initialpaint.delay=0 
[/SIZE]
[SIZE=2]content.notify.backoffcount=5[/SIZE]

---

### Post by finlayj on 2010-06-10
Quickly solved problem I had trying to install Flash for past 2 days.  Flash-Aid of great assistance and now I have no more problem with viewing videos in Firefox 3.6.3.  Fantastic.  Many thanks.

---

### Post by lovinglinux on 2010-06-12
> **emarkay said:**
> So where are we here - Lucid and Maverick?  As a Lucid LTS devotee, and a FF 3.6.3 from the official repo user, what's still the optimum optimize for FF? Are these still "the best"? 

> browser.bookmarks.max_backups=2

The default is 5 and I don't see a good reason to reduce to 2. I have about 1500 bookmarks and the backups only take 1 Mb each. 

> browser.sessionhistory.max_entries=5 

In my personal opinion, I think 5 is too low. The default is 50. Reducing this value can reduce Firefox memory usage, but I would use at least 10 or 20.

> plugin.expose_full_path=T

This is useful for troubleshooting plugin issues,  but has no effect on performance.

> sessionstore.max_tabs_undo=3

I also think is too low. The default value is fine for me and I actually use it quite often.

> sessionstore.max_windows_undo=1 

Personally, I don't like to use new windows, only tabs. Most new windows I open are created by web sites, so setting this preference to 1 makes sense to me.

> dom.popup_maximum=5  

I never had problems with popup loops. I even don't use the block popus feature of Firefox, but I use NoScript and Adblock Plus. Reducing this value would help only if you have issues with several popus showing without interaction.

> network.dns.disableIPv6=True

Essential. Most users with page loading problems solve the issue by disabling ipv6.

> layout.spellcheckDefault=2  

I'm fine with the default value. 

> max-connections=48
> max-connections-per-server=24
> max-persistent-connections-per-proxy=12 
> max-persistent-connections-per-server=12

See [http://www.tweakguides.com/Firefox_11.html](http://www.tweakguides.com/Firefox_11.html)

> network-prefetch-next=False

I use this, because I don't like my browser to downloading pages I'm not going to visit. Nevertheless, this doesn't work on all sites.

> browser.cache.memory.capacity=24576

I'm currently using 14336 to reduce memory usage, but if you don't have issues with Firefox using too much memory and have at least 2Gb ram, then your value should be fine. Please notice that I have more than 50 extensions installed, so reducing this helps to keep Firefox memory usage at decent levels.

> nglayout.initialpaint.delay=0 

Although this preference is very popular, I consider this a placebo.

> content.notify.backoffcount=5

I know what this preference do, but I don't have any experience with it to have an opinion.

Please keep in mind some of the preferences you changed depend on other preferences. So I recommend reading each preference information at [MozillaZine Knowledge Base](http://kb.mozillazine.org/Knowledge_Base).

I also recommend these tutorials:

[http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)
[http://www.tweakguides.com/Firefox_10.html](http://www.tweakguides.com/Firefox_10.html)

---

### Post by SilverWave on 2010-06-22
[http://ftp.ankara.edu.tr/mozilla/firefox/releases/3.6.4/linux-i686/en-US/firefox-3.6.4.tar.bz2](http://ftp.ankara.edu.tr/mozilla/firefox/releases/3.6.4/linux-i686/en-US/firefox-3.6.4.tar.bz2)

[Firefox 3.6.4 with Crash Protection Now Available]("http://blog.mozilla.com/blog/2010/06/22/firefox-3-6-4-with-crash-protection-now-available/")

---

### Post by BlitzLio on 2010-06-23
Hi LovingLinux,
                         After taking a look at your tutorials and doing the flash optimization, I still have some problems with my flash player. My firefox version is 3.6.3 and I am using Ubuntu 10.04. My problem is when watching youtube videos, there are some video frames lag. The audio and video does not match by few seconds and the some videos frames were skipped. Something like you are watch the video at 0.01 then it suddenly jumps to 0.03 then 0.07 and then 0.08. What could be the cause? Flash optimization has been done.

---

### Post by lovinglinux on 2010-06-23
> **BlitzLio said:**
> Hi LovingLinux,
                         After taking a look at your tutorials and doing the flash optimization, I still have some problems with my flash player. My firefox version is 3.6.3 and I am using Ubuntu 10.04. My problem is when watching youtube videos, there are some video frames lag. The audio and video does not match by few seconds and the some videos frames were skipped. Something like you are watch the video at 0.01 then it suddenly jumps to 0.03 then 0.07 and then 0.08. What could be the cause? Flash optimization has been done.

Before Ubuntu 10.04 you could fix that by going to "System >> Preferences >> Sound" and changing the options to ALSA. I don't know where they have put those options now (I use KDE).

Perhaps you could try the commands below and then reboot:

```
rm -r ~/.pulse ~/.asound*
sudo rm /etc/asound.conf
```

I'm not sure it will work, but those commands usually fix missing sounds in flash.

---

### Post by cmcanulty on 2010-06-23
For the past week firefox suddenly closes and I have to restart it, any hints? I am running 10.04 Ubuntu

---

### Post by lovinglinux on 2010-06-23
> **cmcanulty said:**
> For the past week firefox suddenly closes and I have to restart it, any hints? I am running 10.04 Ubuntu

Need more information, like what type of content being displayed...

---

### Post by cmcanulty on 2010-06-23
It doesn't matter I usually have several tabs open and bang it all closes immediately, just started this week.Sometime with only my igoogle page open.

---

### Post by lovinglinux on 2010-06-23
> **cmcanulty said:**
> It doesn't matter I usually have several tabs open and bang it all closes immediately, just started this week.Sometime with only my igoogle page open.

See [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html)

Post your results.

---

### Post by bluelamp999 on 2010-06-23
Hey lovinglinux,

What's happened to your excellent Firefox compilation howto?

I can't find it on your blog or here in the forums.

I've relied on it several times in the past to give me the fastest possible FF on my system...

Cheers!

PS - Go Brazil!

---

### Post by lovinglinux on 2010-06-23
> **bluelamp999 said:**
> Hey lovinglinux,

What's happened to your excellent Firefox compilation howto?

I can't find it on your blog or here in the forums.

I've relied on it several times in the past to give me the fastest possible FF on my system...

Cheers!

PS - Go Brazil!

The only article not included in the new blog is the one on how to compile Firefox. But I will add it soon. I just need to test it first. Is about time.

---

### Post by bluelamp999 on 2010-06-23
> **lovinglinux said:**
> The only article not included in the new blog is the one on how to compile Firefox. But I will add it soon. I just need to test it first. Is about time.

Any chance you could provide the 'old' one?

I'm dying to compile 3.6.4 :p

Thanks

---

### Post by lovinglinux on 2010-06-23
> **bluelamp999 said:**
> Any chance you could provide the 'old' one?

I'm dying to compile 3.6.4 :p

Thanks

Rename the attached file extension to maff and open it with firefox.

---

### Post by bluelamp999 on 2010-06-23
> **lovinglinux said:**
> Rename the attached file extension to maff and open it with firefox.

You sir, are a scholar and a gentleman!

Thank you so much!

Edit: I'd got as far as the 'make -f client.mk build' but couldn't recall the rest - Again, thanks!

---

### Post by lovinglinux on 2010-06-23
> **bluelamp999 said:**
> You sir, are a scholar and a gentleman!

Thank you so much!

Edit: I'd got as far as the 'make -f client.mk build' but couldn't recall the rest - Again, thanks!

You are welcome.

---

### Post by bluelamp999 on 2010-06-23
> **lovinglinux said:**
> You are welcome.

All is good. A blistering FF 3.6.4 now running perfectly...

---

### Post by lovinglinux on 2010-06-23
> **bluelamp999 said:**
> All is good. A blistering FF 3.6.4 now running perfectly...

Good to know. I will try to compile myself. I haven't done that since I upgraded my CPU to a Core2 Duo :)

---

### Post by Vimmander on 2010-06-23
I've noticed that FF tends to use, when idling, anywhere fron 32 to 40 percent of both cores of my CPU.  I found this annoying, so after looking around, I changed:

browser.cache.memory.enable

to false.  Immediately, the CPU usage dropped to the single digits, but now it's back up to 58% and holding.  ](*,)Two questions:

1.)  Is it safe to leave this setting on false, or should I switch it back?
2.)  How can I kill the sickening CPU usage?  I never had this problem in Windows 7, and I don't want to go back to that OS.

FF version is 3.6.3, I'm using Ubuntu 10.04 LTS

NOTE:  I think I figured it out.  I'm using Gliffy for a database class, and it's flash based.  Upon logging out of the site, my CPU usage dropped to 1%.  My first question, however, still stands:  Can I leave the setting on false, or does doing that open a security hole?

---

### Post by lovinglinux on 2010-06-24
> **GrogTheDreamer said:**
> I've noticed that FF tends to use, when idling, anywhere fron 32 to 40 percent of both cores of my CPU.  I found this annoying, so after looking around, I changed:

browser.cache.memory.enable

to false.  Immediately, the CPU usage dropped to the single digits, but now it's back up to 58% and holding.  ](*,)Two questions:

1.)  Is it safe to leave this setting on false, or should I switch it back?
2.)  How can I kill the sickening CPU usage?  I never had this problem in Windows 7, and I don't want to go back to that OS.

FF version is 3.6.3, I'm using Ubuntu 10.04 LTS

NOTE:  I think I figured it out.  I'm using Gliffy for a database class, and it's flash based.  Upon logging out of the site, my CPU usage dropped to 1%.  My first question, however, still stands:  Can I leave the setting on false, or does doing that open a security hole?

You can leave *browser.cache.memory.enable* disabled, but I don't recommend. It won't help to reduce CPU usage and could slow down page loading. See more info about this preference [here](http://kb.mozillazine.org/Browser.cache.memory.enable).

The CPU usage issue is indeed flash related. See the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html).

---

### Post by lovinglinux on 2010-06-24
> **bluelamp999 said:**
> All is good. A blistering FF 3.6.4 now running perfectly...

Compiled it yesterday. running perfectly here too :)

---

### Post by bluelamp999 on 2010-06-24
> **lovinglinux said:**
> Compiled it yesterday. running perfectly here too :)

Do you notice a speed boost with your Core2 Duo?

---

### Post by lovinglinux on 2010-06-24
> **bluelamp999 said:**
> Do you notice a speed boost with your Core2 Duo?

Not much, but there is some. Chrome pages like Speed Dial definitely loads faster.

---

### Post by SilverWave on 2010-07-13
> Firefox-4.0 - One Daily A Month #1 - Lucid
SilverWaveFirefox-4.0 - One Daily A Month #1 - ...

PPA description
The latest firefox without the update hassle.
One daily a month from ubuntu-mozilla-daily.
______________________________
Firefox-4.0 - One Daily A Month #1 - Lucid
One update a month.
Firefox and xulrunner only.
Tested in a virtual machine.
______________________________
sudo add-apt-repository ppa:silverwave/one-daily-a-month-1
sudo apt-get update
sudo apt-get install firefox-4.0
______________________________
Disclaimer: Use at your own risk, no guarantees.
> 
Firefox-4.0 - One Daily A Month #3 - Karmic
SilverWaveFirefox-4.0 - One Daily A Month #3 - ...

PPA description
The latest firefox without the update hassle.
One daily a month from ubuntu-mozilla-daily.
______________________________
Firefox-4.0 - One Daily A Month #3 - Karmic
One update a month.
Firefox and xulrunner only.
Tested in a virtual machine.
______________________________
sudo add-apt-repository ppa:silverwave/one-daily-a-month-3
sudo apt-get update
sudo apt-get install firefox-4.0
______________________________
Disclaimer: Use at your own risk, no guarantees.
All tested and working

Based on:

4.0~b2~hg20100712r47317+nobinonly-0ubuntu1~umd2
2.0~b2~hg20100712r47317+nobinonly-0ubuntu1~umd1

Enjoy!

---

### Post by lovinglinux on 2010-07-13
[http://blog.mozilla.com/addons/2010/07/13/add-on-security-announcement/](http://blog.mozilla.com/addons/2010/07/13/add-on-security-announcement/)

> **Add-on security vulnerability announcement**

One malicious add-on and another add-on with a serious security vulnerability were discovered recently on the Mozilla Add-ons site. Both issues have been dealt with, and the details are described below.

**Mozilla Sniffer**

Issue

An add-on called &#8220;Mozilla Sniffer&#8221; was uploaded on June 6th to addons.mozilla.org. It was discovered that this add-on contains code that intercepts login data submitted to any website, and sends this data to a remote location. Upon discovery on July 12th, the add-on was disabled and added to the blocklist, which will prompt the add-on to be uninstalled for all current users.

Impact to users

If a user installs this add-on and submits a login form with a password field, all form data will be submitted to a remote location. Uninstalling the add-on stops this behavior. Anybody who has installed this add-on should change their passwords as soon as possible.

Status

Mozilla Sniffer has been downloaded approximately 1,800 times since its submission and currently reports 334 active daily users. All current users should receive an uninstall notification within a day or so. The site this add-on sends data to seems to be down at the moment, so it is unknown if data is still being collected.

Mozilla Sniffer was not developed by Mozilla, and it was not reviewed by Mozilla. The add-on was in an experimental state, and all users that installed it should have seen a warning indicating it is unreviewed. Unreviewed add-ons are scanned for known viruses, trojans, and other malware, but some types of malicious behavior can only be detected in a code review.

Credit

This issue was originally reported by Johann-Peter Hartmann.

Note

Having unreviewed add-ons exposed to the public, even with low visibility, has been previously identified as an attack vector for hackers. For this reason, we&#8217;re already working on implementing a new security model for addons.mozilla.org that will require all add-ons to be code-reviewed before they are discoverable in the site. [Here&#8217;s more information about it](https://forums.addons.mozilla.org/viewtopic.php?f=19&t=1134&p=3158).

**CoolPreviews**

Issue

A security escalation vulnerability was discovered in version 3.0.1 of the CoolPreviews add-on. The vulnerability can be triggered using a specially crafted hyperlink. If the user hovers the cursor over this link, the preview function executes remote JavaScript code with local chrome privileges, giving the attacking script control over the host computer. Version 3.0.1 and all older versions have been disabled on addons.mozilla.org, and a fixed version was uploaded and reviewed within a day of the developer being notified.

Impact to users

Proof of concept code for this vulnerability was posted on [this blog](http://d.hatena.ne.jp/teramako/20100621/p1), but no known malicious exploits have been reported so far. If a user has a vulnerable version installed and clicks on a malicious link that targets the add-on, the code in the malicious link will run with local privileges, potentially gaining access to the file system and allowing code download and execution.

All users of CoolPreviews should update to the latest version as soon as possible in order to avoid exposure.

Status

Currently, 177,000 users have a vulnerable version installed. This is less than 25% of the current install base and it will continue to decrease as more users are prompted to update to a new version. Vulnerable versions will also be blocklisted very soon.

Credit

This issue was originally reported by Alice White.

---

### Post by lovinglinux on 2010-07-14
> **SilverWave said:**
> All tested and working

Based on:

4.0~b2~hg20100712r47317+nobinonly-0ubuntu1~umd2
2.0~b2~hg20100712r47317+nobinonly-0ubuntu1~umd1

Enjoy!

Since there is already users trying Firefox 4 Beta, I thought would by wise to leave a warning for add-ons users.

Firefox 4 introduced some radical changes in the add-ons manager, as you can see from the new manager design. These changes will probably break several add-ons, even if you don't think they are broken. 

Usually when Firefox releases a new major version, we can override the extension compatibility check to force extensions to work. In this particular case, some extensions might appear to be working, but they could have issues with updates.

The problem is that whenever such extensions update, they grab the version number from the extension manager, in order to determine if they need to perform changes in associated databases, extension settings and profiles. Since the add-on manager has changed drastically, they won't be able to update properly. They will appear to be working, but won't be able to update some files and perform some functions dependent on extension version.

So if you are using Firefox 4, I would recommend using a separate profile, until all your extensions are updated to work with it.

---

### Post by lovinglinux on 2010-07-15
You are welcome.

---

### Post by npantuso on 2010-07-21
I've been having issues loading some images in firefox. Sometimes, [like here for instance,]("http://b1nd1.deviantart.com/art/Balloon-Comic-1-77860182?q=&qo=")an image won't load all of the way, and will turn completely black or be scrambled. In the link I provided, I can see the image at first, but when I click to zoom in, the entire thing goes black. I tried going into Safe Mode and following Mozilla's troubleshooting tips with no luck. What's especially odd is that it doesn't happen with every image, though I believe it might just be ones that are large i.e. ones that are scaled down to fit on a page and need to be zoomed in on to see full sized. I do have a laptop with a mediocre graphics card, but I don't see why it would be a problem to display a large image.

I'm running Firefox 3.6.6 and Ubuntu 10.04 LTS.

---

### Post by lovinglinux on 2010-07-21
> **npantuso said:**
> I've been having issues loading some images in firefox. Sometimes, [like here for instance,]("http://b1nd1.deviantart.com/art/Balloon-Comic-1-77860182?q=&qo=")an image won't load all of the way, and will turn completely black or be scrambled. In the link I provided, I can see the image at first, but when I click to zoom in, the entire thing goes black. I tried going into Safe Mode and following Mozilla's troubleshooting tips with no luck. What's especially odd is that it doesn't happen with every image, though I believe it might just be ones that are large i.e. ones that are scaled down to fit on a page and need to be zoomed in on to see full sized. I do have a laptop with a mediocre graphics card, but I don't see why it would be a problem to display a large image.

I'm running Firefox 3.6.6 and Ubuntu 10.04 LTS.

I think it could be a graphics card issue. 

Do you have the latest driver for you card? Do you have effects enabled or disabled?

Have you also tried to create a new profile to see of the problem persists?

Also try this: [http://kb.mozillazine.org/Images_or_animations_don%27t_load](http://kb.mozillazine.org/Images_or_animations_don%27t_load)

---

### Post by npantuso on 2010-07-21
It must be the graphics card because creating a new profile didn't do it. I have effects set to Normal. How do I go about updating the driver for my card?

---

### Post by lovinglinux on 2010-07-21
> **npantuso said:**
> It must be the graphics card because creating a new profile didn't do it. I have effects set to Normal. How do I go about updating the driver for my card?

Go to "System >> Administration > Hardware Drivers", select the recommended if available and click to activate.

---

### Post by npantuso on 2010-07-21
Nothing there. I'm not using a proprietary driver for my graphics card.

---

### Post by lovinglinux on 2010-07-21
> **npantuso said:**
> Nothing there. I'm not using a proprietary driver for my graphics card.

It seems you don't have a supported graphics card. 

About the images, I never saw such problem before, but I did experience some graphical glitches in browser tooltips due to video driver. 

Can you post a screenshot of a corrupted image?

---

### Post by lovinglinux on 2010-07-26
Firefox 3.6.8 is now available through the official repositories. Updates are available for Hardy, Jaunty, Karmic and Lucid.

---

### Post by VideoAddicted on 2010-08-01
I hope that this question is okay (and not already asked).  I have Flash 10 installed and confirmed it in Add/Remove Applications as well as Synaptic.  However when i check my flash version in FF it tells me i still have Flash 9.  Any ideas about what's going on?  All the other threads i've checked about this have been less than helpful

Am running 8.04 and have FF 3.6.8.

Thx in advance for anyone willing to help.

---

### Post by lovinglinux on 2010-08-01
> **VideoAddicted said:**
> I hope that this question is okay (and not already asked).  I have Flash 10 installed and confirmed it in Add/Remove Applications as well as Synaptic.  However when i check my flash version in FF it tells me i still have Flash 9.  Any ideas about what's going on?  All the other threads i've checked about this have been less than helpful

Am running 8.04 and have FF 3.6.8.

Thx in advance for anyone willing to help.

Flash 10 in Ubuntu 8.04 is a fake, that actually installs 9.0 r277. I don't know why they did this way, but I presume because of compatibility issues.

Another possible explanation is that swfdec or gnash could also be installed and thus Firefox is not detecting the version from Adobe.

Do you have any player issues? If yes, then get [FLASH-AID]("https://addons.mozilla.org/en-US/firefox/addon/161939/") to fix it.

If you don't have any issues, but want the real version 10 and have a 32bit system, then you could download [version 10 deb file from Adobe]("http://get.adobe.com/flashplayer/") and install it.

---

### Post by lovinglinux on 2010-08-02
I have created a new thread for Firefox 4 support.

[http://ubuntuforums.org/showthread.php?t=1544124](http://ubuntuforums.org/showthread.php?t=1544124)

---

### Post by johnraff on 2010-08-02
> **VideoAddicted said:**
> I hope that this question is okay (and not already asked).  I have Flash 10 installed and confirmed it in Add/Remove Applications as well as Synaptic.  However when i check my flash version in FF it tells me i still have Flash 9.  Any ideas about what's going on?  All the other threads i've checked about this have been less than helpful

Am running 8.04 and have FF 3.6.8.

Thx in advance for anyone willing to help.I had a similar issue a couple of days ago - even after downloading and installing Flash 10 from Adobe the browser (Fx 3.6.8 ) still thought it was 9.something. To fix it I had to:
1) rename a folder called plugins in my ~/.mozilla folder to plugins-disabled. It contained an old flash plugin that was getting priority.
2) purge (or "completely remove" in Synaptic) the new Adobe plugin and install it again.

---

### Post by lovinglinux on 2010-08-02
> **johnraff said:**
> I had a similar issue a couple of days ago - even after downloading and installing Flash 10 from Adobe the browser (Fx 3.6.8 ) still thought it was 9.something. To fix it I had to:
1) rename a folder called plugins in my ~/.mozilla folder to plugins-disabled. It contained an old flash plugin that was getting priority.
2) purge (or "completely remove" in Synaptic) the new Adobe plugin and install it again.

FLASH-AID would take care of that. Just use the "Remove" option and install the deb from Adobe.

---

### Post by VideoAddicted on 2010-08-03
On that note, this has been bugging me.  I've seen numerous references to the mozzilla firefox folder, but despite my best efforts i have been unable to locate it.

---

### Post by lovinglinux on 2010-08-03
> **VideoAddicted said:**
> On that note, this has been bugging me.  I've seen numerous references to the mozzilla firefox folder, but despite my best efforts i have been unable to locate it.

Go to your home folder, hit CTRL+H to display hidden files and folders (ALT+DOT on KDE), then look for a folder named **.mozilla** (with a dot in front). The firefox folder is inside it.

---

### Post by VideoAddicted on 2010-08-04
Thanks for your help

---

### Post by lovinglinux on 2010-08-04
> **VideoAddicted said:**
> Thanks for your help

You are welcome.

---

### Post by Mahngiel on 2010-08-05
Hey lovinglinux,

I've seen your assistance on my FF related issues, and have come to your HowTo/Tips.  Going through your help blog provided through your links, I've managed to come a step closer to having FF restored.  I thought I could just replace it, but have found FF to be far superior to any other alternatives.  Thanks for what you do.

My only last problem can be understood by viewing the attachment.  The left FF is through my user profile (I suppose), while the FF on the right was prompted through gksudo.

If the image is too small to see, I've opened up the font Advance tab from the Content menu.  I had to uncheck (per your advise) Allow pages to chose...

Any further assistance would be appreciated.

***Problem solved via unchecking the Allow pages to chose... under the colors tab.***

Where can I reset this setting to allow the pages to customize themselves without having this issue?

---

### Post by lovinglinux on 2010-08-05
> **Mahngiel said:**
> Hey lovinglinux,

I've seen your assistance on my FF related issues, and have come to your HowTo/Tips.  Going through your help blog provided through your links, I've managed to come a step closer to having FF restored.  I thought I could just replace it, but have found FF to be far superior to any other alternatives.  Thanks for what you do.

My only last problem can be understood by viewing the attachment.  The left FF is through my user profile (I suppose), while the FF on the right was prompted through gksudo.

If the image is too small to see, I've opened up the font Advance tab from the Content menu.  I had to uncheck (per your advise) Allow pages to chose...

Any further assistance would be appreciated.

***Problem solved via unchecking the Allow pages to chose... under the colors tab.***

Where can I reset this setting to allow the pages to customize themselves without having this issue?

I can't understand the problem. If you want to reset everything, just close Firefox and delete (better move it somewhere else to be safe) the file **prefs.js** in you profile folder. This will reset all Firefox settings to default, including extensions settings.

---

### Post by Mahngiel on 2010-08-05
The problem lies in the option "Allow pages to use their own fonts/colors" If selected, everything is blank.  When deselected, I see text.  And deleting my preference file did nothing.  So my curiosity begs to question:
What is the conflict requiring me to disallow pages to use their own settings in order for proper display?

---

### Post by lovinglinux on 2010-08-05
> **Mahngiel said:**
> The problem lies in the option "Allow pages to use their own fonts/colors" If selected, everything is blank.  When deselected, I see text.  And deleting my preference file did nothing.  So my curiosity begs to question:
What is the conflict requiring me to disallow pages to use their own settings in order for proper display?

I see. Most likely bad web site code.

---

### Post by Mahngiel on 2010-08-05
> **lovinglinux said:**
> I see. Most likely bad web site code.

I doubt that is the problem for ESPN, Ubuntu Forums, etc etc.  But, nonetheless, problem solved.  A credit to you.

---

### Post by lovinglinux on 2010-08-05
> **Mahngiel said:**
> I doubt that is the problem for ESPN, Ubuntu Forums, etc etc.  But, nonetheless, problem solved.  A credit to you.

OK then :)

---

### Post by lindend on 2010-09-10
I've got a very strange problem with firefox 3.6. It runs fine when I access it from vnc.  However, when used inside NoMachines, it hangs the shell prompt when launched just disappears when launched via the desktop.

If I start it from a shell prompt, I see no errors...just a hang.

This problem first cropped up with 9.04 and has persisted after an upgrade to 10.04 lucid.  

One other note: firefox 3.0 and 3.5 both orginally ran without incident on nomachines. At some point, it stopped working but I'm not sure what package upgrade may have caused this.

---

### Post by lovinglinux on 2010-09-10
> **lindend said:**
> I've got a very strange problem with firefox 3.6. It runs fine when I access it from vnc.  However, when used inside NoMachines, it hangs the shell prompt when launched just disappears when launched via the desktop.

If I start it from a shell prompt, I see no errors...just a hang.

This problem first cropped up with 9.04 and has persisted after an upgrade to 10.04 lucid.  

One other note: firefox 3.0 and 3.5 both orginally ran without incident on nomachines. At some point, it stopped working but I'm not sure what package upgrade may have caused this.

I don't use vnc or nomachines, but all my Firefox versions work fine when forwarded via ssh shell.

Have you tried to create a new Firefox profile in the remote machine or to access the remote Firefox from a different client machine?

---

### Post by lindend on 2010-09-10
> **lovinglinux said:**
> Have you tried to create a new Firefox profile in the remote machine or to access the remote Firefox from a different client machine?

firefox -P has the same behavior (no window shown, app hangs) when launched in nomachines.  Works fine in VNC.

Is there a log file somewhere I can look at to see why its hanging?

---

### Post by lovinglinux on 2010-09-10
> **lindend said:**
> firefox -P has the same behavior (no window shown, app hangs) when launched in nomachines.  Works fine in VNC.

Is there a log file somewhere I can look at to see why its hanging?

**/var/log**

You can access the logs from "System >> Administration >> Log Viewer".

---

### Post by zuerston on 2010-09-11
Here is a Firefox optimization I just completed on my computer and it sure does work! its several times faster than before.I was really getting peed off at how slow Fox was ,but its ok now.
see this link for instructions.
[http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)

In fact,this is unbelievable as to why Firefox is setup the way it comes out of the box! I cant believe the speed that it reacts now after this tuneup! I was blaming it on my computer but it was all Firefox problems. Why would they do this with their new products? 

I did the above in two separate windows ,so I could read the instructions as I went ,and it wasn't hard to do at all,no problems and the author claims up to 30 times faster and I believe that! its rockin and rollin now! nothing slows it down now.

---

### Post by lovinglinux on 2010-09-11
> **zuerston said:**
> Here is a Firefox optimization I just completed on my computer and it sure does work! its several times faster than before.I was really getting peed off at how slow Fox was ,but its ok now.
see this link for instructions.
[http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)

In fact,this is unbelievable as to why Firefox is setup the way it comes out of the box! I cant believe the speed that it reacts now after this tuneup! I was blaming it on my computer but it was all Firefox problems. Why would they do this with their new products? 

I did the above in two separate windows ,so I could read the instructions as I went ,and it wasn't hard to do at all,no problems and the author claims up to 30 times faster and I believe that! its rockin and rollin now! nothing slows it down now.

You may also like these:

[http://firefox-tutorials.blogspot.com/2010/05/preferences-tweaks.html](http://firefox-tutorials.blogspot.com/2010/05/preferences-tweaks.html)

---

### Post by lindend on 2010-09-12
> **lovinglinux said:**
> You can access the logs from "System >> Administration >> Log Viewer".

Alas, I see nothing firefox related in any of the logs in /var/log.

---

### Post by kosaidpo on 2010-09-26
hello guys
my  FF launch up offline and i've forgot what option in the about:config i have to set to change this .
can someone please help me ?? thanks

---

### Post by lovinglinux on 2010-09-26
> **kosaidpo said:**
> hello guys
my  FF launch up offline and i've forgot what option in the about:config i have to set to change this .
can someone please help me ?? thanks

[http://ubuntuforums.org/showthread.php?t=1537317](http://ubuntuforums.org/showthread.php?t=1537317)

---

### Post by Sepiraph on 2010-10-07
Is there a way to add a horizontal scroll bar in firefox 3.6.10?

---

### Post by lovinglinux on 2010-10-07
> **Sepiraph said:**
> Is there a way to add a horizontal scroll bar in firefox 3.6.10?

Horizontal bar is added automatically once you shrink the page width. Do you want it to be permanent?

---

### Post by dentaku65 on 2010-10-09
Hi lovinglinux, hi all
I've update my guide
[http://ubuntuforums.org/showthread.php?t=1533664](http://ubuntuforums.org/showthread.php?t=1533664)
the part of sqlite with cron
:P

---

### Post by Sepiraph on 2010-10-10
> **lovinglinux said:**
> Horizontal bar is added automatically once you shrink the page width. Do you want it to be permanent?

Actually it doesn't show up in mine at all (running 3.6.10), perhaps I disabled it at some point.

---

### Post by lovinglinux on 2010-10-10
> **Sepiraph said:**
> Actually it doesn't show up in mine at all (running 3.6.10), perhaps I disabled it at some point.

Create a new profile and check if the problem persists, so we can determine if it is a an issue with your settings or not.

---

### Post by Sepiraph on 2010-10-10
> **lovinglinux said:**
> Create a new profile and check if the problem persists, so we can determine if it is a an issue with your settings or not.

My apology, actually it DOES show up if I made the window small enough.  If I guess the question is if there is a way permanent enable horizontal scrollbar 

(did a quick google & find someone asked but no answer [http://support.mozilla.com/tiki-view_forum_thread.php?forumId=1&comments_parentId=5685](http://support.mozilla.com/tiki-view_forum_thread.php?forumId=1&comments_parentId=5685))

Basically, the reason why I wanted that in the first place is because on certain non-web application that I open on firefox, I found that the scroll bar will not appear even if the content doesn't fit within the window.

---

### Post by lovinglinux on 2010-10-10
> **Sepiraph said:**
> My apology, actually it DOES show up if I made the window small enough.  If I guess the question is if there is a way permanent enable horizontal scrollbar 

(did a quick google & find someone asked but no answer [http://support.mozilla.com/tiki-view_forum_thread.php?forumId=1&comments_parentId=5685](http://support.mozilla.com/tiki-view_forum_thread.php?forumId=1&comments_parentId=5685))

Basically, the reason why I wanted that in the first place is because on certain non-web application that I open on firefox, I found that the scroll bar will not appear even if the content doesn't fit within the window.

Go to the chrome folder in your Firefox profile at ~/.mozilla/firefox/<profilename>/chrome/, then rename the file **userContent-example.css** to **userContent.css**, open it with a text editor and add this:

```
html {overflow-x: scroll !important;}
html {overflow-y: scroll !important;}
```

The first one is for horizontal scroller and the second for vertical.

Restart Firefox to see the result in action.

---

### Post by Sepiraph on 2010-10-10
> **lovinglinux said:**
> Go to the chrome folder in your Firefox profile at ~/.mozilla/firefox/<profilename>/chrome/, then rename the file **userContent-example.css** to **userContent.css**, open it with a text editor and add this:

```
html {overflow-x: scroll !important;}
html {overflow-y: scroll !important;}
```

The first one is for horizontal scroller and the second for vertical.

Restart Firefox to see the result in action.

Thanks it works! :)

---

### Post by lovinglinux on 2010-10-10
> **Sepiraph said:**
> Thanks it works! :)

You are welcome.

---

### Post by bigsmitty64 on 2010-10-10
Hi lovinglinux,
I noticed when I go to your blog,
 **[http://lovinglinuxblog.blogspot.com/](http://lovinglinuxblog.blogspot.com/)**
my scrolling in firefox 3.6.10 becomes almost unusable, and I get the "grayed out/ unresponsive" problem that I thought was gone since installing Meerkat. Any ideas as to what is causing this? Thanks,
Smitty

---

### Post by lovinglinux on 2010-10-10
> **bigsmitty64 said:**
> Hi lovinglinux,
I noticed when I go to your blog,
 **[http://lovinglinuxblog.blogspot.com/](http://lovinglinuxblog.blogspot.com/)**
my scrolling in firefox 3.6.10 becomes almost unusable, and I get the "grayed out/ unresponsive" problem that I thought was gone since installing Meerkat. Any ideas as to what is causing this? Thanks,
Smitty

Could be some script in the page. Does it happen on these addresses too?

[http://firefox-tutorials.blogspot.com](http://firefox-tutorials.blogspot.com)
[http://flvideoreplacer-extension.blogspot.com](http://flvideoreplacer-extension.blogspot.com)
[https://www.blogger.com](https://www.blogger.com)

---

### Post by bigsmitty64 on 2010-10-10
Yes sir it does indeed!

---

### Post by lovinglinux on 2010-10-10
> **bigsmitty64 said:**
> Yes sir it does indeed!

Does it happen in safe mode?

---

### Post by bigsmitty64 on 2010-10-10
Not "quite" as bad in safe mode but still significant.

---

### Post by lovinglinux on 2010-10-10
> **bigsmitty64 said:**
> Not "quite" as bad in safe mode but still significant.

Can you confirm if it happens on other blogs hosted on blogspot.com?

---

### Post by bigsmitty64 on 2010-10-11
the following are fine,
[http://throwgrammarfromthetrain.blogspot.com/](http://throwgrammarfromthetrain.blogspot.com/)
[http://treenich.blogspot.com/?expref=next-blog](http://treenich.blogspot.com/?expref=next-blog)
[http://superpunch.blogspot.com/2010/03/this-cake-is-bomb-link-rounudp.html](http://superpunch.blogspot.com/2010/03/this-cake-is-bomb-link-rounudp.html)

However, the original 3 you posted still do it pretty bad. Hope this helps.
Seems like the ones with backgrounds? does that make any sense to ya?

---

### Post by lovinglinux on 2010-10-11
> **bigsmitty64 said:**
> the following are fine,
[http://throwgrammarfromthetrain.blogspot.com/](http://throwgrammarfromthetrain.blogspot.com/)
[http://treenich.blogspot.com/?expref=next-blog](http://treenich.blogspot.com/?expref=next-blog)
[http://superpunch.blogspot.com/2010/03/this-cake-is-bomb-link-rounudp.html](http://superpunch.blogspot.com/2010/03/this-cake-is-bomb-link-rounudp.html)

However, the original 3 you posted still do it pretty bad. Hope this helps.
Seems like the ones with backgrounds? does that make any sense to ya?

Could be. It makes sense. Do you have the latest video driver installed?

Try this one:

[http://mediabar-extension.blogspot.com](http://mediabar-extension.blogspot.com)

I have changed the template. You might need to shrink the browser window to be able to scroll, since the page content it not big.

---

### Post by bigsmitty64 on 2010-10-11
I do have the latest video driver installed. And the link you just gave me is fine. I just tried something, I hope I can explain it right. 

When on youtube.  I go to a video, then click on "view all comments", then with the mouse off to the side of the page I middle click for auto scroll, if I keep my mouse over to the edge of the page, It scrolls fine, BUT if I move my mouse to "hover" over the comments while auto scrolling it freezes!

---

### Post by lovinglinux on 2010-10-11
> **bigsmitty64 said:**
> I do have the latest video driver installed. And the link you just gave me is fine.

So the culprit  is possibly the transparent layer or something in the template.

> **bigsmitty64 said:**
> I just tried something, I hope I can explain it right. 

When on youtube.  I go to a video, then click on "view all comments", then with the mouse off to the side of the page I middle click for auto scroll, if I keep my mouse over to the edge of the page, It scrolls fine, BUT if I move my mouse to "hover" over the comments while auto scrolling it freezes!

Possibly because of the javascript that highlights the comments.

Try to disable Compiz and check if there is any improvement.

Also Firefox 4 with a clean profile.

See [http://kb.mozillazine.org/Scrolling_is_slow](http://kb.mozillazine.org/Scrolling_is_slow)

---

### Post by _outlawed_ on 2010-10-11
Bookmarked your blog for later reference and use, lovinglinux. Thanks! :popcorn:

---

### Post by lovinglinux on 2010-10-11
> **_outlawed_ said:**
> Bookmarked your blog for later reference and use, lovinglinux. Thanks! :popcorn:

You are welcome.

---

### Post by dentaku65 on 2010-10-17
My guide updated today
[http://ubuntuforums.org/showthread.php?t=1533664](http://ubuntuforums.org/showthread.php?t=1533664)

---

### Post by soldier1st on 2010-10-18
here is a problem i have noticed with all ubuntu+variants and it has to do with firefox only. on websites you will encounter images that look distorted/out of focus/garbled/pixilated yet only firefox does this as opera and chrome do not have that behavior, i do recall that the namaroka browser(firefox beta) did not have these issues but it is beta and i don't exactly trust beta software. any fix will help and clicking the option of zooming text only does not work unless there is a setting that needs to be changed or created that will fix it.

---

### Post by lovinglinux on 2010-10-18
> **soldier1st said:**
> here is a problem i have noticed with all ubuntu+variants and it has to do with firefox only. on websites you will encounter images that look distorted/out of focus/garbled/pixilated yet only firefox does this as opera and chrome do not have that behavior, i do recall that the namaroka browser(firefox beta) did not have these issues but it is beta and i don't exactly trust beta software. any fix will help and clicking the option of zooming text only does not work unless there is a setting that needs to be changed or created that will fix it.

Please post a screeenshot.

---

### Post by soldier1st on 2010-10-20
the screenshot will appear fine as like i said it's firefox only(linux version only), everything else is not affected. this site has images that are distorted but open it in firefox and only inspect the pictures
[http://legacy.filefront.com/](http://legacy.filefront.com/)
i even tested it on a fresh ubuntu install in virtualbox in firefox(no extensions) and it still happens.

---

### Post by lovinglinux on 2010-10-20
> **soldier1st said:**
> the screenshot will appear fine as like i said it's firefox only(linux version only), everything else is not affected. this site has images that are distorted but open it in firefox and only inspect the pictures
[http://legacy.filefront.com/](http://legacy.filefront.com/)
i even tested it on a fresh ubuntu install in virtualbox in firefox(no extensions) and it still happens.

Looks fine to me. Please provide a direct link to a distorted image on that web site.

---

### Post by mobilediesel on 2010-10-30
Is there a location where I can download Firefox 3.0.x, whatever the last one was before 3.6? I'm running Xubuntu 8.04.4 and Firefox 3.6.x is garbage, Swiftfox 3.6.x is garbage. Compiling the latest myself is garbage.

3.0.x worked and 3.6.x does not. 3.6.x crashes so regularly it reminds me of IE6. After the latest update I can't even print from the browser. I can print from any other program capable of printing but I cannot print from the browser. That's just the last straw with 3.6.x as I have been trying to "deal" with it until the mess with trying to print.

---

### Post by lovinglinux on 2010-10-30
> **mobilediesel said:**
> Is there a location where I can download Firefox 3.0.x, whatever the last one was before 3.6? I'm running Xubuntu 8.04.4 and Firefox 3.6.x is garbage, Swiftfox 3.6.x is garbage. Compiling the latest myself is garbage.

3.0.x worked and 3.6.x does not. 3.6.x crashes so regularly it reminds me of IE6. After the latest update I can't even print from the browser. I can print from any other program capable of printing but I cannot print from the browser. That's just the last straw with 3.6.x as I have been trying to "deal" with it until the mess with trying to print.

I wouldn't recommend running Firefox 3, since it is no longer supported and thus do not have the latest security patches. Nevertheless, you can download it from [ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/3.0.19-real-real/](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/3.0.19-real-real/)

It would be better to run [Firefox 4 Beta]("http://firefox-tutorials.blogspot.com/2010/08/firefox-4-download-install-customize.html"), which still has bugs but is a lot better than previous versions.

I also recommend trying [Opera alpha 11]("http://www.opera.com/browser/next/"), which is awesome. If you don't care about customizations and the features provided by Opera and Firefox, then try [Google Chrome]("http://www.google.com/chrome").

---

### Post by tlu on 2010-10-30
> **mobilediesel said:**
> Is there a location where I can download Firefox 3.0.x, whatever the last one was before 3.6? I'm running Xubuntu 8.04.4 and Firefox 3.6.x is garbage, Swiftfox 3.6.x is garbage. Compiling the latest myself is garbage.

3.0.x worked and 3.6.x does not. 3.6.x crashes so regularly it reminds me of IE6. After the latest update I can't even print from the browser. I can print from any other program capable of printing but I cannot print from the browser. That's just the last straw with 3.6.x as I have been trying to "deal" with it until the mess with trying to print.

As lovinglinux already said, FF 3.0.x is no longer safe - you should not use it. 
Something is probably wrong with your profile. Have you tried creating a new profile? (you have to start FF with the -P option). I suggest that you follow the hints on [http://kb.mozillazine.org/Standard_diagnostic_-_Firefox](http://kb.mozillazine.org/Standard_diagnostic_-_Firefox)

---

### Post by _outlawed_ on 2010-11-03
Just have to bump and bring this to the first page since it's such a useful thread.

And these optimization tweaks aren't just for Linux, they work wonders in Windows too.

---

### Post by lovinglinux on 2010-11-03
> **_outlawed_ said:**
> Just have to bump and bring this to the first page since it's such a useful thread.

And these optimization tweaks aren't just for Linux, they work wonders in Windows too.

:guitar:

---

### Post by _outlawed_ on 2010-11-03
> **lovinglinux said:**
> :guitar:
And of which, I just reinstalled Windows 7 again so time to go apply the tweaks. :D

Seriously, a page that would take 1 second to load...after the tweaks...takes like 50% of that time off.

---

### Post by DachaArh on 2010-11-13
Im using Firefox 3.6.12, and Ubuntu 10.10
When I go to this page for example:
[http://www.gimp.org/screenshots/](http://www.gimp.org/screenshots/)
and try to open third screenshot in first row... when I click on it, it is zooming in very slowly, and when I press X to exit it.. Firefox becomes unusable for about 5-10 seconds, and then starts to zoom-out the image, very slowly...

I have this issue on every site that has big images to zoom, when I say big... I do not have issue with lets say 1600*1200 pixels, but I do with 2500*1600 pixels.
My configuration : AMD Athlon 64 bit 3000+; Ati Radeon X600, 2GB DDR2...
I have tested in all other browsers on my Ubuntu and its working fine...
I have tried safe mode, I have tried new profile... I have tried latest Minefield beta... nothing works... zooming is very slow everywhere...
I have tried live CDs Fedora 14, Ubuntu 10.04, Ubuntu 10.10 and all of them have this issue with Firefox...

I have tried disabling Compiz... not helping, I have tried disabling Pango in bashrc file, not helping...

Firefox on Windows is working fine, and everything else except Firefox is working fine on Ubuntu

Any Ideas?
thanks for any help

---

### Post by lovinglinux on 2010-11-14
> **DachaArh said:**
> Im using Firefox 3.6.12, and Ubuntu 10.10
When I go to this page for example:
[http://www.gimp.org/screenshots/](http://www.gimp.org/screenshots/)
and try to open third screenshot in first row... when I click on it, it is zooming in very slowly, and when I press X to exit it.. Firefox becomes unusable for about 5-10 seconds, and then starts to zoom-out the image, very slowly...

I have this issue on every site that has big images to zoom, when I say big... I do not have issue with lets say 1600*1200 pixels, but I do with 2500*1600 pixels.
My configuration : AMD Athlon 64 bit 3000+; Ati Radeon X600, 2GB DDR2...
I have tested in all other browsers on my Ubuntu and its working fine...
I have tried safe mode, I have tried new profile... I have tried latest Minefield beta... nothing works... zooming is very slow everywhere...
I have tried live CDs Fedora 14, Ubuntu 10.04, Ubuntu 10.10 and all of them have this issue with Firefox...

I have tried disabling Compiz... not helping, I have tried disabling Pango in bashrc file, not helping...

Firefox on Windows is working fine, and everything else except Firefox is working fine on Ubuntu

Any Ideas?
thanks for any help

I have tested that screenshot with various browsers and the performance decreases in this order: Chrome, Opera 11, Firefox 4.0b7 and Firefox 3.6.12. This is exactly the order of performance of those browsers when benchmarking with javascript tests.

For me it doesn't freeze the browser and although the zooming gets slower on FF 3.6.12, there is no pausing in the animation. So I suspect your problem is due to a combination of poor javascript engine performance of the browser and video driver.

Don't know how to solve it. You could try Firefox 4 to see if the problem persists. It has a much better javascript engine.

---

### Post by DachaArh on 2010-11-14
Thank you for your reply... I have tried firefox 4 and it is the same... I have lost of pausing in animation... but I did some system tweaking and now my browser does not freeze when I try to close (zoom out)...

I know that it is problem with video driver.. Im using open drivers, and when I go to system~Administration~Aditional drivers there is nothing to install, so I do not know what should I try with drivers... :(

---

### Post by lovinglinux on 2010-11-14
> **DachaArh said:**
> I know that it is problem with video driver.. Im using open drivers, and when I go to system~Administration~Aditional drivers there is nothing to install, so I do not know what should I try with drivers... :(

[Here are some recent Ati Radeon X600 threads]("http://www.google.com/search?q=Ati+Radeon+X600+site:ubuntuforums.org&hl=en&tbo=1&prmdo=1&output=search&source=lnt&tbs=qdr:m&sa=X&ei=u5fgTJzYLYP88Aa77ugC&ved=0CAcQpwU"). Perhaps you can find a solution there. Unfortunately, I know nothing about Ati.

---

### Post by DachaArh on 2010-11-15
thank you for your help ;)

---

### Post by lovinglinux on 2010-11-15
> **DachaArh said:**
> thank you for your help ;)

I wish I could be more helpful. :(

---

### Post by static chaser on 2010-11-22
Lovinglinux I have a small problem with FF4. When I hover my cursor over a button, the website appears in the right hand side of the address bar. This causes me a problem in Ancestry.com with buttons that are a java function, like save or view data. Is there a way to move that info to the bottom tool bar like FF3? I appreciate any help you can give. I use your info to tweak and optimize a lot.

---

### Post by lovinglinux on 2010-11-22
> **static chaser said:**
> Lovinglinux I have a small problem with FF4. When I hover my cursor over a button, the website appears in the right hand side of the address bar. This causes me a problem in Ancestry.com with buttons that are a java function, like save or view data. Is there a way to move that info to the bottom tool bar like FF3? I appreciate any help you can give. I use your info to tweak and optimize a lot.

Yes, you can use [Status-4-Evar]("https://addons.mozilla.org/en-US/firefox/addon/235283/") extension to hide the address bar info and put it in the add-ons bar on the bottom.

---

### Post by static chaser on 2010-11-22
OK I downloaded S4E and moved the info to the bottom is the new add-on bar. That helped a lot with other junk that used to be available, but didn't fix the Java button issue I have. I have filed a bug report but am sure it has a low priority because it is only a button in Ancestry.com. I still have to keep FF3 to use because the button works on there. Thanks for the help. You do a great job and have helped me on other issues with Flash.

---

### Post by Bobhuber on 2010-11-24
Small problem may be you can help with. About every other time I use the  back arrow to revisit a previous page (single click) it ignores me.If I single click again it works as it should.
I THINK I have seen this before but just can't remember weather it fixed itself on an update or what.
Thanks in advance - Bob

Firefox 4.0 Beta 7

---

### Post by lovinglinux on 2010-11-24
> **Bobhuber said:**
> Small problem may be you can help with. About every other time I use the  back arrow to revisit a previous page (single click) it ignores me.If I single click again it works as it should.
I THINK I have seen this before but just can't remember weather it fixed itself on an update or what.
Thanks in advance - Bob

Firefox 4.0 Beta 7

First time I see such problem. Perhaps you have an extension messing with the back button functionality. Start Firefox in safe mode and check if the problem persists.

---

### Post by cmcanulty on 2010-11-24
Mine has done that for years also

---

### Post by bigsmitty64 on 2010-11-24
> **cmcanulty said:**
> Mine has done that for years also
same here, with or without extensions

---

### Post by zika on 2010-11-25
[http://kb.mozillazine.org/Browser.backspace_action](http://kb.mozillazine.org/Browser.backspace_action)
I use **browser.backspace_action=0** ...
(about:config)

---

### Post by Bobhuber on 2010-11-25
> **zika said:**
> [http://kb.mozillazine.org/Browser.backspace_action](http://kb.mozillazine.org/Browser.backspace_action)
I use **browser.backspace_action=0** ...
Thanks a lot. I'll give it a try. Its got to be key mapping somewhere in compiz or elsewhere.
Great post.

---

### Post by Bobhuber on 2010-11-28
OK heres a new one. Firefox 4.0 Beta 7 - When I go to optimize the sqlite databases using firefox-optimize.sh I get the following error when it gets to the cookies.sqlite.
Error: file is encrypted or is not a database
All goes well except for this one file.I can delete the file and reload Firefox (which recreates the file) and the same error occurs.Safe mode etc. makes no difference.I even changed the home page and deleted  stored cookies before shutting down. Optimizing the system version 3.6.12 works fine with the same extensions.

---

### Post by lovinglinux on 2010-11-28
> **Bobhuber said:**
> OK heres a new one. Firefox 4.0 Beta 7 - When I go to optimize the sqlite databases using firefox-optimize.sh I get the following error when it gets to the cookies.sqlite.
Error: file is encrypted or is not a database
All goes well except for this one file.I can delete the file and reload Firefox (which recreates the file) and the same error occurs.Safe mode etc. makes no difference.I even changed the home page and deleted  stored cookies before shutting down. Optimizing the system version 3.6.12 works fine with the same extensions.

I'm also experiencing such issue recently, with Firefox 4. Don't know the reason yet.

---

### Post by Bobhuber on 2010-11-29
[B][B]Here's a really neat trick that should increase FF speed if you have enough Ram.
[/B][/B]

Credit goes to an article posted at **CPTL.ORG **on SSD drives.

This is along the lines of running your profile from ram only were just going to load the firefox disk-cache into memory.
**_ Move Firefox cache to a tmpfs_**

For most of us, using Firefox is probably responsible for the largest  percentage of our disk activity.  To reduce the number of writes to the  disk you can move your cache to a tmpfs filesystem.  Your browser cache  will be stored in your physical memory (RAM), bypassing the need to  store it on the disk altogether.  Of course, it will be wiped out when  you reboot, but most people won’t really mind that. To create a tmpfs filesystem, you’ll need to edit your /etc/fstab  file.  Adding the following line will convert your system’s /tmp  directory to tmpfs:
none /tmp tmpfs defaults 0 0
After a reboot, use the mount command and verify that your change worked by looking for a line like this:
none on /tmp type tmpfs (rw)
If you’ve verified that your tmpfs has been created, open Firefox and enter **about:config** in the location bar.  Right-click and choose the option **New->String**.  Enter “browser.cache.disk.parent_directory” for the preference name, and for the string value enter “/tmp/firefox-cache”.
Restart Firefox, and look inside the /tmp directory to make sure the browser’s cache is being written to the new location.

[B]My 2 cents 
[/B]So far so good for me [B]BUT >
[/B]The system files that are normally stored in the /tmp directory will also be stored in your new RAM directory so I would recommend at least 2-3 gig of memory.
As the name implies these files should be rewritten on every reboot and I can foresee no problems however **> PROCEED AT YOUR OWN RISK <**

---

### Post by Damiox on 2010-11-30
there has to be a better way to do that without involving the entire tmp dir ?  all you need is the FF tmp in ram . shortcut link in ram ? seems overly complicated :)  note: wow man . you have kept this thread going for over a year . - applause- wow !  Lol

---

### Post by zika on 2010-11-30
> **Damiox said:**
> there has to be a better way to do that without involving the entire tmp dir ?  all you need is the FF tmp in ram . shortcut link in ram ? seems overly complicated :)  note: wow man . you have kept this thread going for over a year . - applause- wow !  LolLike /dev/shm ...

---

### Post by Bobhuber on 2010-11-30
> **Damiox said:**
> there has to be a better way to do that without involving the entire tmp dir ?  all you need is the FF tmp in ram . shortcut link in ram ? seems overly complicated :)  note: wow man . you have kept this thread going for over a year . - applause- wow !  Lol
You can create the tmpfs in _any_ directory you want. Create a new dir and modify your fstab accordingly. Not sure why the author created it there other than almost all Linux systems would already have the dir and the system files being there would actually speed things up and cut down on read/write drive access which is what the original article intended. As far as this thread is concerned its one of the best I've found on the forums and one of the most read thanks to Lovinglinux and his time and knowledge. You can always unsubscribe if you don't think so.

---

### Post by lovinglinux on 2010-11-30
> **Damiox said:**
> there has to be a better way to do that without involving the entire tmp dir ?  all you need is the FF tmp in ram . shortcut link in ram ? seems overly complicated :)

> **zika said:**
> Like /dev/shm ...

Yep. See this: [http://firefox-tutorials.blogspot.com/2010/08/use-ramdisk-to-save-firefox-cache.html](http://firefox-tutorials.blogspot.com/2010/08/use-ramdisk-to-save-firefox-cache.html)

> **Damiox said:**
> note: wow man . you have kept this thread going for over a year . - applause- wow !  Lol

Wow. I didn't realize that until now. That's really great, specially considering I'm feeling like a thread killer recently :)

Thanks for the applause :)

> **Bobhuber said:**
> As far as this thread is concerned its one of the best I've found on the forums and one of the most read thanks to Lovinglinux and his time and knowledge. You can always unsubscribe if you don't think so.

Thanks a lot. That is really nice to read.

BTW, I'm building a new web site for my extensions and tutorials. Maintaining all those blogs is starting to be more time consuming that I expected, specially now that I am also building extension for Opera and Chrome. Inf fact, now I realize creating separate blogs on blogspot was a really bad idea :) Anyways, because of that I will probably update some of tutorials. I will update the links as soon as the site is online.

---

### Post by Damiox on 2010-11-30
> **lovinglinux said:**
> Yep. See this: [http://firefox-tutorials.blogspot.com/2010/08/use-ramdisk-to-save-firefox-cache.html](http://firefox-tutorials.blogspot.com/2010/08/use-ramdisk-to-save-firefox-cache.html)



Wow. I didn't realize that until now. That's really great, specially considering I'm feeling like a thread killer recently :)

Thanks for the applause :)



Thanks a lot. That is really nice to read.

BTW, I'm building a new web site for my extensions and tutorials. Maintaining all those blogs is starting to be more time consuming that I expected, specially now that I am also building extension for Opera and Chrome. Inf fact, now I realize creating separate blogs on blogspot was a really bad idea :) Anyways, because of that I will probably update some of tutorials. I will update the links as soon as the site is online.

Neat and easy  lol .. much better ..  and your welcome ... i would have told all these peeps where to stick it along time ago lol

---

### Post by psablo on 2010-12-01
Thanks, Loving Linux!
I needed to "Disable IPv6" on my laptop to get Firefox 3.6 to connect under my new 10.04 upgrade and your "Common Issues and Solutions" explained it perfectly.

---

### Post by COKEDUDE on 2010-12-02
Nice post. A lot of useful stuff here.

---

### Post by DachaArh on 2010-12-11
Ok... new problems with firefox... tried Firefox 3.6.13... Namaroka 3.6.14 MInefield 4. b08 pre... tried new profiles.. problem remains...

First error itself... when I run Firefox via terminal, after some time I get this error :


```
(<unknown>:2657): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2657): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2657): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2657): Gdk-WARNING **: XID collision, trouble ahead
```

it multplies... as you can see.. sometimes alot more times than 4.. like right now...

I do not mind the message it self.. that terminal is moved to another workspace anyway..

But I mind this:
I have Firefox tweaked pretty good... nglayout is 0, content.notify.interval and switch.treshold are 750k tokenizing time 3 times larger... and so on...

Well it works perfectly... but then.. it the middle on my sessing something happens to firefox, I get no warning, but browsing experience changes... like all of the sudden nglayout is changed from 0, to "redraw when loaded" - that whould be the right name... because, before that, all pages I browse would start to draw instantly.. and after that page is drawn after it is fully loaded.... so on most forums I have to wait 2-3 seconds to see the link... If I close firefox... all is back to normal, but it cant last 15 minutes... :(

Edit :

The problem Im having with redraw time has nothing to do with that terminal message.. I have no messages in terminal now... but I do have problem... instant redraw lasted whole 5 minutes.... :(

---

### Post by lovinglinux on 2010-12-11
> **DachaArh said:**
> Ok... new problems with firefox... tried Firefox 3.6.13... Namaroka 3.6.14 MInefield 4. b08 pre... tried new profiles.. problem remains...

First error itself... when I run Firefox via terminal, after some time I get this error :


```
(<unknown>:2657): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2657): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2657): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:2657): Gdk-WARNING **: XID collision, trouble ahead
```

it multplies... as you can see.. sometimes alot more times than 4.. like right now...

I do not mind the message it self.. that terminal is moved to another workspace anyway..

[http://ubuntuforums.org/showthread.php?p=7506398](http://ubuntuforums.org/showthread.php?p=7506398)

> **DachaArh said:**
> But I mind this:
I have Firefox tweaked pretty good... nglayout is 0, content.notify.interval and switch.treshold are 750k tokenizing time 3 times larger... and so on...

Well it works perfectly... but then.. it the middle on my sessing something happens to firefox, I get no warning, but browsing experience changes... like all of the sudden nglayout is changed from 0, to "redraw when loaded" - that whould be the right name... because, before that, all pages I browse would start to draw instantly.. and after that page is drawn after it is fully loaded.... so on most forums I have to wait 2-3 seconds to see the link... If I close firefox... all is back to normal, but it cant last 15 minutes... :(

Edit :

The problem Im having with redraw time has nothing to do with that terminal message.. I have no messages in terminal now... but I do have problem... instant redraw lasted whole 5 minutes.... :(

Does it happen with new web sites or just with web sites that you have already visited in the same session?

---

### Post by lovinglinux on 2010-12-11
> **DachaArh said:**
> 
I have Firefox tweaked pretty good... nglayout is 0, content.notify.interval and switch.treshold are 750k tokenizing time 3 times larger... and so on..

Try to lower content.notify.interval and if it helps.

---

### Post by DachaArh on 2010-12-11
thanks for your reply... ;)

I will try to lower... it seems that is only happens with sites opened before that random point of problem start... ;)

If I lower content.notify.interval.. I think I should lower tokenizing time.. right ? 

I will try now... ;)

---

### Post by DachaArh on 2010-12-11
Lowering down content.notify.interval does not help... 

It seems that is only happens with sites that were opened to that point.. not with new websites.... but closing tabs that have problem and opening them again doe snot help...  :(

---

### Post by SilverWave on 2010-12-12
Just a heads up in case anyone gets a sync error after playing with the dailies e.g FF4b8pre.
> **SilverWave said:**
> 
The latest FF4b8pre updates your back end sync data (held on Mozilla servers).

The problem is that any FF3.6 machines still on 1.5.1 cant read the new format yet.

So you wont be able to sync with your FF3.6 machines until they release an update.

[reposted to correct group]

---

### Post by SilverWave on 2010-12-12
> **SilverWave said:**
> Just a heads up in case anyone gets a sync error after playing with the dailies e.g FF4b8pre.


[reposted to correct group]

I have a fix but its a little involved so go [here]("http://ubuntuforums.org/showthread.php?p=10225769#post10225769") for the gory details:

Quick and Dirty instructions follow:

You need this:
[Latest Update: Firefox Sync 1.6b4 (December 11, 2010)]("https://services.mozilla.com/sync/updated/?version=1.5&channel=dev")

and then you will get *Wrong Sync Key* error.

to fix this see this:

[http://tech.mahesha.com/2010/12/07/your-old-firefox-sync-key-is-no-good/](http://tech.mahesha.com/2010/12/07/your-old-firefox-sync-key-is-no-good/)

(What's happened is that they have **changed your sync key without telling you**!).

---

### Post by DachaArh on 2010-12-12
> **DachaArh said:**
> Lowering down content.notify.interval does not help... 

It seems that is only happens with sites that were opened to that point.. not with new websites.... but closing tabs that have problem and opening them again doe snot help...  :(



Little update... it happens only after visiting sites like : omgubuntu.co.uk
or [http://www.multimediaboom.com](http://www.multimediaboom.com)

what is common with those sites, I do not know... but I know it is not flash... because I installed flashblock... and my initialpaint.delay is still messed up after going to sites like this....

---

### Post by lovinglinux on 2010-12-12
> **DachaArh said:**
> Little update... it happens only after visiting sites like : omgubuntu.co.uk
or [http://www.multimediaboom.com](http://www.multimediaboom.com)

what is common with those sites, I do not know... but I know it is not flash... because I installed flashblock... and my initialpaint.delay is still messed up after going to sites like this....

If the value of initialpaint.delay is changed in the preferences, then you should you should report it, since it would be a serious bug.

I have experienced issues with omgubuntu in Firefox and Opera, but mostly crashes.

---

### Post by DachaArh on 2010-12-12
> **lovinglinux said:**
> If the value of initialpaint.delay is changed in the preferences, then you should you should report it, since it would be a serious bug.

I have experienced issues with omgubuntu in Firefox and Opera, but mostly crashes.

No it is not changed in prefs... but it feels like it is changed...
when I go to about:config, it still says that is it 0
but pages are not "painted" untill they are fully loaded....
and all I can do is restart firefox... than it is back to normal...

---

### Post by lovinglinux on 2010-12-13
> **DachaArh said:**
> No it is not changed in prefs... but it feels like it is changed...
when I go to about:config, it still says that is it 0
but pages are not "painted" untill they are fully loaded....
and all I can do is restart firefox... than it is back to normal...

Weird. Does it get better if you leave the computer alone for a while?

---

### Post by DachaArh on 2010-12-13
I even tried using live CDs of  Fedora 14 and Ubuntu 10.10...
Fedora has Firefox 3.6.12, Ubuntu has 3.6.10...  When I tweak them like that... they both act like my Firefox... they redraw instantly.. untill something happens, after visiting some pages... after that they redraw when loaded...

I havent tried to leave it for a while, because I really do not want to browse the web for 10 minutes, and then to wait 5 minutes, to browser again, no offence ;)

---

### Post by DachaArh on 2010-12-13
Ok, since I have dual boot, I just copied my prefs.js from ubuntu to Windows 7, since all other in profiles is already same, same addons, same bookmars ...etc...

And there is not problem in Windows 7... 

As far as Im concerned, it would be more decent from Mozilla not to make Browser for Linux, that making something that is worse than it is on windows...

Opera is even worse... one only needs 5 minutes on Opera on Windows, and then it is bettter to torture him then to make him browse with Opera for Linux... scrolling is terible in web pages... flash terrible to...

And I have 150+ frames in games (Torcs, Urban Terror)... so I do not think it is my hardware...


Im forced to use one of those two... but there are constantly some problems with those, and I have came to the point where I have to choose between two "evils" : 1. Firefox which after most 30 minutes, starts to redraw pages when they are fully loaded, so If Im on heavy forums, I have to wait 4-5 seconds to see some change on screen and 2. Opera, trust me, you dont wanna see that scrolling, it is all choppy ( I have turned of smooth scrolling offcourse ) facebook chat button jumps when you scroll the page, twitter top-black-panel jumps when you scroll up.. etc...

Sometimes I ask myself this **"Does Microsoft pay Mozilla and Opera to make linux builds worse, or they do it on purpose"**... but I alwas forget to ask them..

---

### Post by zika on 2010-12-13
> **DachaArh said:**
> Ok, since I have dual boot, I just copied my prefs.js from ubuntu to Windows 7, since all other in profiles is already same, same addons, same bookmars ...etc...

And there is not problem in Windows 7... 

As far as Im concerned, it would be more decent from Mozilla not to make Browser for Linux, that making something that is worse that on windows...

Opera is even worse... one only needs 5 minutes on Opera on Windows, and then it is bettter to torture him then to make him browse with Opera for Linux... scrolling is terible in web pages... flash terrible to...

And I have 150+ frames in games (Torcs, Urban Terror)... so I do not think it is my hardware...


Im forced to use one of those two... but there are constantly some problems with those, and I have came to the point where I have to choose between two "evils" : 1. Firefox which after most 30 minutes, starts to redraw pages when they are fully loaded, so If Im on heavy forums, I have to wait 4-5 seconds to see some change on screen and 2. Opera, trust me, you dont wanna see that scrolling, it is all choppy ( I have turned of smooth scrolling offcourse ) facebook chat button jumps when you scroll the page, twitter top-black-panel jumps when you scroll up.. etc...

Sometimes I ask myself this **"Does Microsoft pay Mozilla and Opera to make linux builds worse, or they do it on purpose"**... but I alwas forget to ask them..Try ```
Version
11.00 beta

Build
1140

Platform
Linux

System
x86_64, 2.6.37-999-generic

Browser identification

Opera/9.80 (X11; Linux x86_64; U; en) Presto/2.7.62 Version/11.00
```
or ```
Chromium 10.0.610.0 (68978) Ubuntu 11.04
```...
I do not have any scroll problems...
No problems in FF 4.0b8pre, either.

The only problem I have is in Chrome(ium) with YouTube inserted in Forum messages, but that will pass, soon, I hope...

Oh, yes, there is problem with current version of Opera ans some Forums in answering to messages... Temporary, I'm sure...

---

### Post by DachaArh on 2010-12-13
Thanks Zika, we know each other :D

FIrefox problem I have is on my Ubuntu, Ubuntu live, Fedora live, and OpenSuse live... so Im outa clue there... 

Scrolling problem in Opera is in all versions, I actualy use the 1040 build... someone maybe does not see that as a problem but it is much worse than in Firefox, not just slower ( less lines, because my firefox is tweaked to scroll more lines), but it is not fluid.. it is kinda choppy, not much, but big difference between it and Firefox...
Chrome/Chromium I do not use for a reason I stated on other forum, just under your comment about Chrome ;), I am talking about Serbian Ubuntu community ;) 

Since we are in same city, you are free to come to my place, to test everything, just that we all see that Im not imagining it, and we can move towards solving it :D

I love Linux/Ubuntu, but at this moment I do not have a Web Browser Im satisfied with... :(

I have tried all profile deleting, unistaling and installing again....

Since Im on  Dusanovac, we are realy probably not more than 3 kilometers away :D

edit : FIrefox would be perfect if page draw delay would stay the same the whole session, and Opera even better with only better scrolling and flash preformance on some sites... but there is a saying in my country, about grandma having something.. she would not need grandpa.. but its dirty... :D

---

### Post by lovinglinux on 2010-12-13
> **DachaArh said:**
> Thanks Zika, we know each other :D

FIrefox problem I have is on my Ubuntu, Ubuntu live, Fedora live, and OpenSuse live... so Im outa clue there... 

Scrolling problem in Opera is in all versions, I actualy use the 1040 build... someone maybe does not see that as a problem but it is much worse than in Firefox, not just slower ( less lines, because my firefox is tweaked to scroll more lines), but it is not fluid.. it is kinda choppy, not much, but big difference between it and Firefox...
Chrome/Chromium I do not use for a reason I stated on other forum, just under your comment about Chrome ;), I am talking about Serbian Ubuntu community ;) 

Since we are in same city, you are free to come to my place, to test everything, just that we all see that Im not imagining it, and we can move towards solving it :D

I love Linux/Ubuntu, but at this moment I do not have a Web Browser Im satisfied with... :(

I have tried all profile deleting, unistaling and installing again....

Since Im on  Dusanovac, we are realy probably not more than 3 kilometers away :D

edit : FIrefox would be perfect if page draw delay would stay the same the whole session, and Opera even better with only better scrolling and flash preformance on some sites... but there is a saying in my country, about grandma having something.. she would not need grandpa.. but its dirty... :D

I had problems with Opera scrolling in the early alphas, but now that you mentioned, I turned smooth scrolling on and looks good to me. 

```
11.00 beta

Build
1136

Platform
Linux

System
i686, 2.6.32-24-generic
```

About Firefox, remove everything personal from your *prefs.js* and send it to me. I would like to test it.

---

### Post by DachaArh on 2010-12-13
about the Opera part... well smooth scrolling is terrible, on the long page I have to spinn mu scroll like 100 times, it takes me 3 times more scrolling to get to the end...

Version
11.00 beta

Build
1140

Platform
Linux

System
i686, 2.6.35-23-generic


____________________

About Firefox:
I think that prefs.js does not store password, right ?
If it does not, than all else in not personal, I guess...

---

### Post by DachaArh on 2010-12-13
ok, prefs.js uploaded.. hoping for best....

If you can, Visit some heavy forums, wait to load index page, and load some subforum, then some topic.. after that see that page start to redraw almost instantly, you can see the beggining right away, and and then you get the rest of page...  it all happens pretty fast...

Then open omgubuntu.co.uk
 browser atlest 4-5 articles from their main page, scroll to the bottom of every page - including articles... 
and then after all that return to that forums, now load back that subforum, you will have to wait, and then you will get in all at once, same is for topic, so its like nglayout is somehow messed up...

I can only notice on heavy forums, since lite forums load very fast any way...

It does not happen only after that site, it happens after some time on facebook... etc...

Ubuntu 10.10 32bit 2.6.35-23 generic

thanks so much for this ;)

---

### Post by lovinglinux on 2010-12-13
> **DachaArh said:**
> ok, prefs.js uploaded.. hoping for best....

If you can, Visit some heavy forums, wait to load index page, and load some subforum, then some topic.. after that see that page start to redraw almost instantly, you can see the beggining right away, and and then you get the rest of page...  it all happens pretty fast...

Then open omgubuntu.co.uk
 browser atlest 4-5 articles from their main page, scroll to the bottom of every page - including articles... 
and then after all that return to that forums, now load back that subforum, you will have to wait, and then you will get in all at once, same is for topic, so its like nglayout is somehow messed up...

I can only notice on heavy forums, since lite forums load very fast any way...

It does not happen only after that site, it happens after some time on facebook... etc...

Ubuntu 10.10 32bit 2.6.35-23 generic

thanks so much for this ;)

Sorry, but I couldn't reproduce your problem. Perhaps you should look into your router or maybe (just guessing) reducing the number of network.http.max-connections and see if that helps.

---

### Post by zika on 2010-12-14
> **DachaArh said:**
> Thanks Zika, we know each other :D
Since Im on  Dusanovac, we are realy probably not more than 3 kilometers away :DIf we would take a straight line, I think it is much less..
One is sure, I do not doubt any character in Your statement of the problem... I'm just stating that it is not common, at least not for the two of us...
See You on ubuntu-rs...
P.S.:I do notice one thing. I NEVER use smooth scrolling...

---

### Post by Bobhuber on 2010-12-15
I don't quite know where to post this or to who so here goes. Lovinglinux ??
My best guess is that the latest beta firefox-4.0b9pre.en-US.linux-x86_64.tar.bz2 has a virus or I've gone over the edge or both.
Ive done the same thing three times with the same results. I downloaded and unzipped the file in my home directory as I've done a thousand times with nightly releases that I run daily. This creates a new firefox directory in my home directory and I delete the zip file . THIS DOES NOT HAPPEN UNTIL I RUN THE FILE. After running firefox and closing it the directory (firefox) disappears along with the mozilla-central directory(another copy of firefox) in the GUI (nautilus).
I can see the files in a terminal using LS normally or as root. I can still open and run firefox.
I can see the directory from PLACES as a locked file (its owned by root) rwe  with read and execute privileges for all others. After restoring the system  I can download any of the other files from the FTP site and do the same thing without any problems.

---

### Post by lovinglinux on 2010-12-15
> **Bobhuber said:**
> I don't quite know where to post this or to who so here goes. Lovinglinux ??
My best guess is that the latest beta firefox-4.0b9pre.en-US.linux-x86_64.tar.bz2 has a virus or I've gone over the edge or both.
Ive done the same thing three times with the same results. I downloaded and unzipped the file in my home directory as I've done a thousand times with nightly releases that I run daily. This creates a new firefox directory in my home directory and I delete the zip file . THIS DOES NOT HAPPEN UNTIL I RUN THE FILE. After running firefox and closing it the directory (firefox) disappears along with the mozilla-central directory(another copy of firefox) in the GUI (nautilus).
I can see the files in a terminal using LS normally or as root. I can still open and run firefox.
I can see the directory from PLACES as a locked file (its owned by root) rwe  with read and execute privileges for all others. After restoring the system  I can download any of the other files from the FTP site and do the same thing without any problems.

Weird. Perhaps a Nautilus problem. Install another file browser and check if the problem persists.

---

### Post by Bobhuber on 2010-12-18
FYI - The latest flash player (10.1) included with the ubuntu 10.10 upgrade gave me all kinds of problems. I went back to flash 10.0.r45 and all is back to normal (or at least usable) for the flash plugins.

---

### Post by aeronutt on 2010-12-24
Anyone know how to get ride of the title bar in firefox-4.0? (Similar to Chrome.) I've tried a few of the userChrome.css files found on the web, and they don't seem to work. (Like found here: [http://www.techexplorer.in/2010/07/remove-title-bar-trim-firefox-4-even-more.html](http://www.techexplorer.in/2010/07/remove-title-bar-trim-firefox-4-even-more.html)) I'm guessing there's a setting in gnome that needs to change also?

---

### Post by Bobhuber on 2010-12-24
> **aeronutt said:**
> Anyone know how to get ride of the title bar in firefox-4.0? (Similar to Chrome.) I've tried a few of the userChrome.css files found on the web, and they don't seem to work. (Like found here: [http://www.techexplorer.in/2010/07/remove-title-bar-trim-firefox-4-even-more.html](http://www.techexplorer.in/2010/07/remove-title-bar-trim-firefox-4-even-more.html)) I'm guessing there's a setting in gnome that needs to change also?
Theres an addon called hide menubar that will do part of what you want.

---

### Post by aeronutt on 2010-12-24
> **Bobhuber said:**
> Theres an addon called hide menubar that will do part of what you want.

There's already an option to hide the menu bar in firefox-4.0.  I'd like to hide the window title bar, as shown in the link I provided, and like you can in Chrome.

---

### Post by lovinglinux on 2010-12-24
> **Bobhuber said:**
> FYI - The latest flash player (10.1) included with the ubuntu 10.10 upgrade gave me all kinds of problems. I went back to flash 10.0.r45 and all is back to normal (or at least usable) for the flash plugins.

That version has serious vulnerabilities. try the latest beta:

32bit [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

64bit [http://labs.adobe.com/downloads/flashplayer10_square.html](http://labs.adobe.com/downloads/flashplayer10_square.html)

> **aeronutt said:**
> Anyone know how to get ride of the title bar in firefox-4.0? (Similar to Chrome.) I've tried a few of the userChrome.css files found on the web, and they don't seem to work. (Like found here: [http://www.techexplorer.in/2010/07/remove-title-bar-trim-firefox-4-even-more.html](http://www.techexplorer.in/2010/07/remove-title-bar-trim-firefox-4-even-more.html)) I'm guessing there's a setting in gnome that needs to change also?

> **aeronutt said:**
> There's already an option to hide the menu bar in firefox-4.0.  I'd like to hide the window title bar, as shown in the link I provided, and like you can in Chrome.

I don't think you can. The tutorial from that link is for the Windows version of Firefox 4. The Linux version UI has some limitations.

---

### Post by aeronutt on 2010-12-24
> **lovinglinux said:**
> That version has serious vulnerabilities. try the latest beta:

32bit [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

64bit [http://labs.adobe.com/downloads/flashplayer10_square.html](http://labs.adobe.com/downloads/flashplayer10_square.html)





I don't think you can. The tutorial from that link is for the Windows version of Firefox 4. The Linux version UI has some limitations.

Ahhh...thanks. Let's hope the Linux UI gets its due share once it's at full release.

---

### Post by lovinglinux on 2010-12-24
> **aeronutt said:**
> Ahhh...thanks. Let's hope the Linux UI gets its due share once it's at full release.

I don't think it will change.

---

### Post by lovinglinux on 2010-12-25
Tutorials are now hosted on a new site. Some of them were also reviewed and updated.

[http://www.webgapps.org/blogs/firefox-tutorials](http://www.webgapps.org/blogs/firefox-tutorials)

---

### Post by Rubi1200 on 2010-12-25
> **lovinglinux said:**
> Tutorials are now hosted on a new site. Some of them were also reviewed and updated.

[http://www.webgapps.org/blogs/firefox-tutorials](http://www.webgapps.org/blogs/firefox-tutorials)
Very nice lovinglinux :)

Thanks.

---

### Post by lovinglinux on 2010-12-25
> **Rubi1200 said:**
> Very nice lovinglinux :)

Thank you.

---

### Post by Sky Aisling on 2010-12-30
Thank you all for all the work that has gone into this thread.
I think the answer I am looking for is in: [http://www.webgapps.org/firefox/profiles-and-backups#](http://www.webgapps.org/firefox/profiles-and-backups#)
But, I'm not sure.

I am **installing** *not* upgrading **Lucid Lynx 10.04**,
The current distro is **Karmic Koala**.
The machine is a **ZaReason 3660 **with** 4GB of RAM.** 

My intent is to delete Karmic Koala then make a clean install of Lucid Lynx.  

How do I save Firefox bookmarks created in Karmic Koala and install them in Firefox of Lucid Lynx?

Thank you in advance for your consideration of my question.

---

### Post by Arwen17evenstar on 2010-12-30
> **Sky Aisling said:**
> Thank you all for all the work that has gone into this thread.
I think the answer I am looking for is in: [http://www.webgapps.org/firefox/profiles-and-backups#](http://www.webgapps.org/firefox/profiles-and-backups#)
But, I'm not sure.

I am **installing** *not* upgrading **Lucid Lynx 10.04**,
The current distro is **Karmic Koala**.
The machine is a **ZaReason 3660 **with** 4GB of RAM.** 

My intent is to delete Karmic Koala then make a clean install of Lucid Lynx.  

How do I save Firefox bookmarks created in Karmic Koala and install them in Firefox of Lucid Lynx?

Thank you in advance for your consideration of my question.

if you're just trying to transfer bookmarks, why not try the xmarks add-on for firefox.
upload your bookmarks using xmarks and then download them onto your new install.

---

### Post by Sky Aisling on 2010-12-30
Thank you, Arwen17evenstar.

That sounds exactly what I am looking for!  I'll give it a try.

Sky

---

### Post by lovinglinux on 2010-12-30
> **Sky Aisling said:**
> Thank you all for all the work that has gone into this thread.
I think the answer I am looking for is in: [http://www.webgapps.org/firefox/profiles-and-backups#](http://www.webgapps.org/firefox/profiles-and-backups#)
But, I'm not sure.

I am **installing** *not* upgrading **Lucid Lynx 10.04**,
The current distro is **Karmic Koala**.
The machine is a **ZaReason 3660 **with** 4GB of RAM.** 

My intent is to delete Karmic Koala then make a clean install of Lucid Lynx.  

How do I save Firefox bookmarks created in Karmic Koala and install them in Firefox of Lucid Lynx?

Thank you in advance for your consideration of my question.

If you do not have a separate partition for /home, then I recommend you create one. When you need to reinstall the OS you can leave the /home partition unformatted and just mount it, so you don't lose any personal files or configurations for any application.

See [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I don't know how I could live without a separate /home partition. I can install a new version of Ubuntu and get everything just the way it was before, in less than two hours.

If you don't want to create a separate partition for /home, then simply backup the folder ~/.mozilla and transfer it to the new machine. All your Firefox settings will be preserved.

---

### Post by audiomick on 2010-12-30
[COLOR=Red][SIZE=5]Typo!!![/SIZE][/COLOR]


> **lovinglinux said:**
> ...When you need to reinstall the OS you [COLOR=Red]can't[/COLOR] leave the /home partition unformatted and just mount it,

You don't mean "can't". you mean "CAN". ;)

---

### Post by lovinglinux on 2010-12-30
> **audiomick said:**
> [COLOR=Red][SIZE=5]Typo!!![/SIZE][/COLOR]

You don't mean "can't". you mean "CAN". ;)

Indeed. That is what happens when you spend too many hours coding stuff then go to the forums. Brain freeze. :)

Thanks.

---

### Post by zika on 2010-12-31
> **lovinglinux said:**
> If you do not have a separate partition for /home, then I recommend you create one. When you need to reinstall the OS you can leave the /home partition unformatted and just mount it, so you don't lose any personal files or configurations for any application.

See [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I don't know how I could live without a separate /home partition. I can install a new version of Ubuntu and get everything just the way it was before, in less than two hours.

If you don't want to create a separate partition for /home, then simply backup the folder ~/.mozilla and transfer it to the new machine. All your Firefox settings will be preserved.The very good thing is that (nowadays and several versions ago) if You do not mark / for formatting then You get your /home preserved even though You did a (re)install...

---

### Post by audiomick on 2011-01-03
> **lovinglinux said:**
> 
Thanks.More than welcome. Nice to be able to help you for a change... ;)

---

### Post by foutes on 2011-01-12
I have not had time to read the entire thread yet and not sure how to describe the problem to search thread for the answer.

The screen shot shows what happens when I try to view images in FF.

I do not have compiz enabled but I do use metacity compositor.

I have deleted profile and still no luck.

Video playback if fine,in fact everything works in FF except for this error.

Any help will be appreciated.

---

### Post by lovinglinux on 2011-01-13
> **foutes said:**
> I have not had time to read the entire thread yet and not sure how to describe the problem to search thread for the answer.

The screen shot shows what happens when I try to view images in FF.

I do not have compiz enabled but I do use metacity compositor.

I have deleted profile and still no luck.

Video playback if fine,in fact everything works in FF except for this error.

Any help will be appreciated.

This is video driver issue. Make sure you have the latest driver for your graphics card.

---

### Post by foutes on 2011-01-16
> **lovinglinux said:**
> This is video driver issue. Make sure you have the latest driver for your graphics card.

 Thanks for the help,new driver fixed this problem.

---

### Post by _outlawed_ on 2011-02-01
This tutorial is in need of some bumpage, for glory sake.

---

### Post by -Sparx- on 2011-02-08
I'm not sure if this is the right thread but I hope it is.
I have been using foxtester for a little while and i think it's great!
However, I have a small problem. I made firefox 4.0b9 my default browser and except for a few bugs it runs good. But firefox reminds me of installing an update to b10 and i though that would be a good idea and do it via the foxtester menu. Now when i try to go to the foxtester menu there is no "make default" option anymore and the plugin is sometimes, when i switch profile, disabled for incompatibility, and i have to reinstall it to get the menu back, but it still lacks the option of "make default". 

Is there any help i can get to make it work? It would be really nice.
Thanks!

---

### Post by tlu on 2011-02-08
> **-Sparx- said:**
> I'm not sure if this is the right thread but I hope it is.
I have been using foxtester for a little while and i think it's great!
However, I have a small problem. I made firefox 4.0b9 my default browser and except for a few bugs it runs good. But firefox reminds me of installing an update to b10 and i though that would be a good idea and do it via the foxtester menu. Now when i try to go to the foxtester menu there is no "make default" option anymore and the plugin is sometimes, when i switch profile, disabled for incompatibility, and i have to reinstall it to get the menu back, but it still lacks the option of "make default". 

Is there any help i can get to make it work? It would be really nice.
Thanks!

Why don't you use the betas from [https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa) ? Add that ppa to your repos and you'll get updates nearly every other day.

---

### Post by -Sparx- on 2011-02-08
> **tlu said:**
> Why don't you use the betas from [https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa) ? Add that ppa to your repos and you'll get updates nearly every other day.

Thanks for the tip!
However, I did that the first time around and it messed up every mozilla product i used at the time(thunderbird and firefox 3.6 my default installation) and was a bit of a hassle to revert. So when i tried to resolve that i found foxtester here and thought I would try it out.
Maybe I'll give the repos another go, if all else fails.

---

### Post by tlu on 2011-02-08
> **-Sparx- said:**
> Thanks for the tip!
However, I did that the first time around and it messed up every mozilla product i used at the time(thunderbird and firefox 3.6 my default installation) and was a bit of a hassle to revert. 

This shouldn't be the case any more. 
If you install FF 4.0 from the ppa it creates a new subfolder Firefox-4.0 in ~/.mozilla and **copies** your FF 3.6 profile to that new folder. So your original profile remains unchanged. Nothing to worry about.:)
Nevertheless it surely makes sense to backup your profile once in a while ...

---

### Post by undisclosedname on 2011-02-10
Has anyone managed to compile Firefox 4 beta 11 with --enable-system-cairo on Maverick? I can't compile Firefox 4 with --enable-system-cairo. Without this option the fonts look odd.

I've tried applying this patch to no avail: [https://bugzilla.mozilla.org/show_bug.cgi?id=363861](https://bugzilla.mozilla.org/show_bug.cgi?id=363861)

---

### Post by arzali on 2011-02-11
> **aeronutt said:**
> Anyone know how to get ride of the title bar in firefox-4.0? (Similar to Chrome.) I've tried a few of the userChrome.css files found on the web, and they don't seem to work. (Like found here: [http://www.techexplorer.in/2010/07/remove-title-bar-trim-firefox-4-even-more.html](http://www.techexplorer.in/2010/07/remove-title-bar-trim-firefox-4-even-more.html)) I'm guessing there's a setting in gnome that needs to change also?

Im using compiz and [Hide Caption Titlebar Plus addon]("https://addons.mozilla.org/de/firefox/addon/hide-caption-titlebar-plus-sma/")  to get "tabs in title bar" like Chrome.

For more infos and screenshots see [http://ubuntuforums.org/showthread.php?t=1684542](http://ubuntuforums.org/showthread.php?t=1684542)

---

### Post by -Sparx- on 2011-02-14
> **tlu said:**
> This shouldn't be the case any more. 
If you install FF 4.0 from the ppa it creates a new subfolder Firefox-4.0 in ~/.mozilla and **copies** your FF 3.6 profile to that new folder. So your original profile remains unchanged. Nothing to worry about.:)
Nevertheless it surely makes sense to backup your profile once in a while ...

Sorry for the late reply.
I will try this out later and see how it turns out. 
Thanks! 
And of course remember to make a backup :D

PS: I assume that i still manually have to uncheck updates relating to firefox 3.6 when using the update manager?

---

### Post by lovinglinux on 2011-02-14
> **-Sparx- said:**
> I'm not sure if this is the right thread but I hope it is.
I have been using foxtester for a little while and i think it's great!
However, I have a small problem. I made firefox 4.0b9 my default browser and except for a few bugs it runs good. But firefox reminds me of installing an update to b10 and i though that would be a good idea and do it via the foxtester menu. Now when i try to go to the foxtester menu there is no "make default" option anymore and the plugin is sometimes, when i switch profile, disabled for incompatibility, and i have to reinstall it to get the menu back, but it still lacks the option of "make default". 

Is there any help i can get to make it work? It would be really nice.
Thanks!

I have experienced issues with some versions of Firefox 4. Most of the time is another extension interfering with FoxTester and installing it on a clean profile make it work again. I wasn't able to determine the culprit yet.

Try this:

-create a new profile in Firefox
-install FoxTester using the new profile
-install the Firefox 4 you want using FoxTester menu
-make it default
-restart Firefox using the default profile

---

### Post by yakinikku on 2011-02-28
I am having a very strange problem with firefox.  I think this video best describes it.

[http://tinypic.com/r/25fq5bd/7](http://tinypic.com/r/25fq5bd/7)

the shuffling is happening automatically whenever firefox is opened.  the bookmarks in the bookmarks toolbar are also being overwritten when that happens.  any ideas how to solve the problem?

solved

[http://aeric.poon.my/index.php/tag/desktop-couch-scratch/](http://aeric.poon.my/index.php/tag/desktop-couch-scratch/)

---

### Post by lovinglinux on 2011-03-01
> **yakinikku said:**
> I am having a very strange problem with firefox.  I think this video best describes it.

[http://tinypic.com/r/25fq5bd/7](http://tinypic.com/r/25fq5bd/7)

the shuffling is happening automatically whenever firefox is opened.  the bookmarks in the bookmarks toolbar are also being overwritten when that happens.  any ideas how to solve the problem?

Try a new profile.

---

### Post by Kanehekili on 2011-04-29
hi,
I'm running Firefox 4 on Lucid 10.04 with compiz activated. My problem are the popup panels, such as the bookmark panel or the "Remember password" panel. I could make the bookmark panel visible by adding some code into the userchrome.css file:

#editBookmarkPanel {
margin-top: 100px !important;
margin-left: 50px !important;
margin-right: -400px !important;
background-color: -moz-dialog !important;
}

#mainPopupSet #editBMPanel_folderTree,
#mainPopupSet #editBMPanel_newFolderBox {
visibility: visible !important;
} 

So far so good, but that does not work with the "Remember Passswrod" panel, which pops up whenever I login  into a new page. 
If compiz is turned off, all panels are visible.

Did anybody encounter a similiar problem with firefox 4? Help would be appreciated

---

### Post by lovinglinux on 2011-04-29
> **Kanehekili said:**
> hi,
I'm running Firefox 4 on Lucid 10.04 with compiz activated. My problem are the popup panels, such as the bookmark panel or the "Remember password" panel. I could make the bookmark panel visible by adding some code into the userchrome.css file:

#editBookmarkPanel {
margin-top: 100px !important;
margin-left: 50px !important;
margin-right: -400px !important;
background-color: -moz-dialog !important;
}

#mainPopupSet #editBMPanel_folderTree,
#mainPopupSet #editBMPanel_newFolderBox {
visibility: visible !important;
} 

So far so good, but that does not work with the "Remember Passswrod" panel, which pops up whenever I login  into a new page. 
If compiz is turned off, all panels are visible.

Did anybody encounter a similiar problem with firefox 4? Help would be appreciated

It is a common problem. Usually the dialogs are displayed again if you minimize and maximize Firefox.

---

### Post by Kanehekili on 2011-04-29
@lovinglinux- thanks for the fast reply. I've read about this problem, but as far as I understood, it concerned menus and the hoovering above them.
Problem is that a popup panel (is that the correct term?) closes itself as soon as it looses its focus - e.g. when trying to minimize the main window - so the popup will not exist anymore when the main window is maximized again. (I checked that out while compiz was turned off)
What I'm really looking for is a fix in the userchrome.css  as described for the bookmark panel for the "remember password" panel. :icon_frown:

---

### Post by lovinglinux on 2011-04-29
> **Kanehekili said:**
> @lovinglinux- thanks for the fast reply. I've read about this problem, but as far as I understood, it concerned menus and the hoovering above them.
Problem is that a popup panel (is that the correct term?) closes itself as soon as it looses its focus - e.g. when trying to minimize the main window - so the popup will not exist anymore when the main window is maximized again. (I checked that out while compiz was turned off)
What I'm really looking for is a fix in the userchrome.css  as described for the bookmark panel for the "remember password" panel. :icon_frown:

I will have too look into this. Probably is just a matter of figuring out the ID of the password overlay element. The problem is that when I try to do that with DOM Inspector, it loses focus and close.

---

### Post by Kanehekili on 2011-05-11
It seems I found a solution to the missing popup panels and would like to share it with you:
In all my tests, I had the Firefox 4 Menubar visible! As soon as you deactivate the menubar (View->Toolbars->Menubar) all popup dialogs will display correctly. 
It seems to be a composition window manager problem, since this happens on compiz as well as Metacity, when "compositing" was turned on. (gconf editor)
Hope that helps anybody

---

### Post by lovinglinux on 2011-05-11
> **Kanehekili said:**
> It seems I found a solution to the missing popup panels and would like to share it with you:
In all my tests, I had the Firefox 4 Menubar visible! As soon as you deactivate the menubar (View->Toolbars->Menubar) all popup dialogs will display correctly. 
It seems to be a composition window manager problem, since this happens on compiz as well as Metacity, when "compositing" was turned on. (gconf editor)
Hope that helps anybody

Thanks for sharing. That will be certainly useful to other users.

---

### Post by lovinglinux on 2011-05-25
Just updated the site and the tutorials!

---

### Post by tlu on 2011-05-26
> **lovinglinux said:**
> Just updated the site and the tutorials!

Thank you very much, lovinglinux! Great site!

---

### Post by lovinglinux on 2011-05-26
> **tlu said:**
> Thank you very much, lovinglinux! Great site!

You are welcome and thank you.

---

### Post by SilverWave on 2011-06-22
> **SilverWave said:**
> 
> 
Christian Legnitto, the Firefox release manager, put it most succinctly   in a May 25 message.
He said. "Firefox 5 will be the security update for Firefox 4".

Wow.

---

### Post by hopefulkayaker on 2011-06-22
Hello, I'm running version 4, and I've noticed a really obnoxious bug. Once in a while, when I hover over an area which brings up a menu, that menu will disppear when I move my mouse to browse the menu options. This happens on many sties, including Youtube.

On some sites, this makes it very difficult to access certain pages that are only accessible through a menu.

Has anyone else encountered this?

---

### Post by lovinglinux on 2011-06-22
> **hopefulkayaker said:**
> Hello, I'm running version 4, and I've noticed a really obnoxious bug. Once in a while, when I hover over an area which brings up a menu, that menu will disppear when I move my mouse to browse the menu options. This happens on many sties, including Youtube.

On some sites, this makes it very difficult to access certain pages that are only accessible through a menu.

Has anyone else encountered this?

Yes. I have encountered this, but only on rare occasions and is not permanent. Have you tried to reload the page? Also try to minimize and maximize the browser to see if the problem goes away.

---

### Post by hopefulkayaker on 2011-06-23
> **lovinglinux said:**
> Yes. I have encountered this, but only on rare occasions and is not permanent. Have you tried to reload the page? Also try to minimize and maximize the browser to see if the problem goes away.

Thank you for the tips. I will give them a shot next time this problem comes up.

---

### Post by mikeleonard on 2011-06-23
Nice Information about fireFox optimization .Please Share More information.

---

### Post by lovinglinux on 2011-06-23
> **mikeleonard said:**
> Nice Information about fireFox optimization .Please Share More information.

I am currently very active in the [Firefox 4, 5 & Beyond Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247"). Not directly related to optimization, but there are lots of Firefox info there too.

---

### Post by geazzy on 2011-06-24
great threads :D

---

### Post by lovinglinux on 2011-06-24
> **geazzy said:**
> great threads :D

Thanks.

---

### Post by Mjateznik on 2011-06-24
Hi! I have a problem with running flash 10 on Ubuntu 10.04 (64 bit) and heard you might have the answears ;)

I have checked your troubleshoot and looked for gnash and swfdec - neither are installed.

I have uninstalled the flashplugin- installer and nonfree and then installed flashplugin64-installer. I also tried to use a script which downloaded the tar.gz from adobes website and installed it but with no effect. When I go to about:plugins I never see flash (or any other plugins) and flash wont work.

What should I do?

---

### Post by lovinglinux on 2011-06-24
> **Mjateznik said:**
> Hi! I have a problem with running flash 10 on Ubuntu 10.04 (64 bit) and heard you might have the answears ;)

I have checked your troubleshoot and looked for gnash and swfdec - neither are installed.

I have uninstalled the flashplugin- installer and nonfree and then installed flashplugin64-installer. I also tried to use a script which downloaded the tar.gz from adobes website and installed it but with no effect. When I go to about:plugins I never see flash (or any other plugins) and flash wont work.

What should I do?

Install [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/), run the extension wizard and restart Firefox.

If that doesn't work, click the Flash-Aid "Help" menu and then "Generate Report". Paste the contents of the *firefox-report.txt* file created in your desktop, so I can take a look.

---

### Post by Mjateznik on 2011-06-25
Thanks for the tip, Flash Aid did the trick!

---

### Post by lovinglinux on 2011-06-25
> **Mjateznik said:**
> Thanks for the tip, Flash Aid did the trick!

You are welcome.

---

### Post by habana on 2011-07-29
I have searched the forums without success so maybe here's the place to ask:) Firefox has the incredibly annoying (to me) property of changing to full screen whenever I move its window towards the top of my screen. No doubt this is deliberate but I can't find a way to disable it. Hopefully this is a simple setting in about:config but I can't find it!

Thanks in advance for any advice

Natty
Unity
Firefox 5.0

---

### Post by Bobhuber on 2011-07-29
> **habana said:**
> I have searched the forums without success so maybe here's the place to ask:) Firefox has the incredibly annoying (to me) property of changing to full screen whenever I move its window towards the top of my screen. No doubt this is deliberate but I can't find a way to disable it. Hopefully this is a simple setting in about:config but I can't find it!

Thanks in advance for any advice

Natty
Unity
Firefox 5.0
I't seems to be a function of Natty (Unity) and not Firefox.Any of the windows do the same thing and disabling the integrated Unity Menu Bar makes no difference.

---

### Post by lovinglinux on 2011-07-29
> **Bobhuber said:**
> I't seems to be a function of Natty (Unity) and not Firefox.Any of the windows do the same thing and disabling the integrated Unity Menu Bar makes no difference.

Yes, it is a Natty feature.

To disable it, see [http://ubuntuforums.org/showpost.php?p=10832264&postcount=14](http://ubuntuforums.org/showpost.php?p=10832264&postcount=14)

---

### Post by habana on 2011-07-29
Thanks guys! All fixed now - funny I only noticed it in Firefox

---

### Post by lovinglinux on 2011-07-31
I just added a new section to the Preferences Tweaks tutorial, about preferences cleanup:

> **Preferences Cleanup**

When you remove Firefox extensions, they leave behind some preferences in the *prefs.js* file. For some time I thought this wouldn't affect Firefox performance, but actually I believe they do. After removing old extensions preferences , I was able to see a significant reduction in page loading time.

To clean up your Firefox preferences, you can use the [Preferences Cleaner]("https://addons.mozilla.org/en-US/firefox/addon/preferences-cleaner/") extension. After you install the extension, you can launch it through the Add-on Manager (about:addons) or by dragging the extension launcher to a toolbar. To do that, right-click on a toolbar and select *Customize*.

Be careful to not delete preferences that are not related to extensions or from extensions that are actually in use. To find preferences from extensions that have been removed, click the *Loose Preferences* button then the extensions folder (branch). Some extensions save data outside the extensions branch, so you might need to look in the root folder too.

If you experience any problems after deleting some preferences, you can restore a backup, which is created automatically whenever you use the extension. It doesn't seem to offer a restore feature, but you can simply open the backup folder, copy the backup and replace the *prefs.js* file in your profile.

---

### Post by karen729 on 2011-09-26
So far I have customized about:config and installed flash-aid. i have noticed a considerable improvement using Firefox 3.6. Pages load much faster and the flash is behaving much better. I will get to the rest of the table of contents (at the beginning of this thread) shortly. 

Thanks much for sharing all of your hard work. Another Thanks for maintaining this thread and answering all the posters. :D

---

### Post by lovinglinux on 2011-09-26
> **karen729 said:**
> So far I have customized about:config and installed flash-aid. i have noticed a considerable improvement using Firefox 3.6. Pages load much faster and the flash is behaving much better. I will get to the rest of the table of contents (at the beginning of this thread) shortly. 

Thanks much for sharing all of your hard work. Another Thanks for maintaining this thread and answering all the posters. :D

You are welcome.

I also recommend getting the latest Firefox 7, which will be released tomorrow. It is a lot faster than 3.6. See [Firefox 6 & Beyond Mega Thread](http://ubuntuforums.org/showthread.php?t=1712247)

---

### Post by tlu on 2011-10-06
@lovinglinux:

I'm using your Flash-Aid extension - it's really good, congratulations! However, I found one problem: I created a new profile for my FF and installed Flash-Aid (and added /usr/bin/konsole as the terminal path). It informed me that a new version of 64bit Flash was available. I tried to install it with the Wizard mode - and nothing happened! I found the culprit very soon: I have the AppArmor Firefox profile set to enforce, and this prevented read access to some executables in /bin and execute access to /usr/bin/konsole. After fixing that, I had no problems anymore.

Thus, I suggest that might think about two alternatives: 
1. Either you inform the user during installation that she might run into problems if AppArmor is set to enforce and suggest to manually add the necessary rules available on your extension homepage to /etc/apparmor.d/local/usr.bin.firefox, or,
2. you check if AppArmor is set to enforce and offer to export the update script to the konsole (although AppArmor might prevent even this check - I'm not sure about this).

Just my 2 cents ;)

---

### Post by KingYaba on 2011-10-07
Most of the stuff I've seen or done myself but not the pipelining thing. How noticeable is it on a broadband connection?

---

### Post by sillyboy on 2011-10-19
Firefox 3.6.23 is not shutting down properly.  FF v7, from what I read, SUX so far.  I would like to go to the version of FF right before 3.6.23.

Thank You

---

### Post by lovinglinux on 2011-10-19
> **tlu said:**
> @lovinglinux:

I'm using your Flash-Aid extension - it's really good, congratulations! However, I found one problem: I created a new profile for my FF and installed Flash-Aid (and added /usr/bin/konsole as the terminal path). It informed me that a new version of 64bit Flash was available. I tried to install it with the Wizard mode - and nothing happened! I found the culprit very soon: I have the AppArmor Firefox profile set to enforce, and this prevented read access to some executables in /bin and execute access to /usr/bin/konsole. After fixing that, I had no problems anymore.

Thus, I suggest that might think about two alternatives: 
1. Either you inform the user during installation that she might run into problems if AppArmor is set to enforce and suggest to manually add the necessary rules available on your extension homepage to /etc/apparmor.d/local/usr.bin.firefox, or,
2. you check if AppArmor is set to enforce and offer to export the update script to the konsole (although AppArmor might prevent even this check - I'm not sure about this).

Just my 2 cents ;)

Thanks for the suggestion. So far, I haven't received similar reports, but I will consider adding such information.

---

### Post by lovinglinux on 2011-10-19
> **KingYaba said:**
> Most of the stuff I've seen or done myself but not the pipelining thing. How noticeable is it on a broadband connection?

For me is very noticeable.

---

### Post by lovinglinux on 2011-10-19
> **sillyboy said:**
> Firefox 3.6.23 is not shutting down properly.  FF v7, from what I read, SUX so far.  I would like to go to the version of FF right before 3.6.23.

Thank You

FF 7 is great. I would recommend installing instead of going back to an insecure version.

---

### Post by sillyboy on 2011-10-19
> **lovinglinux said:**
> FF 7 is great. I would recommend installing instead of going back to an insecure version.

Why then all the negative posting about FF7?  I seem to see more - than +.

Thanks

---

### Post by lovinglinux on 2011-10-19
> **sillyboy said:**
> Why then all the negative posting about FF7?  I seem to see more - than +.

Thanks

Well, most negative posts I have seen are regarding the new fast development cycle and add-on compatibility.

You can decide yourself by downloading it, extracting to your home and launching it. If you you don't like it, close it and delete it. If you like it, add the ppa to upgrade.  See the first post for a tutorial.

---

### Post by Dannny213 on 2011-10-29
I need help, please. I have just installed Flash-aid and it did improve my flash performance, however, I now have a 30 second delay on every flash video and my computer seems to freeze during this period.

I disabled and uninstalled the flash-aid extention, and still the problem persists. I have removed the flash plugin for Mozilla and reinstalled that also, and I still have the same problem.

Is the flash-aid installation process irreversible? I would like to remove everything that has been installed with it. Please help!

---

### Post by lovinglinux on 2011-10-30
> **Dannny213 said:**
> I need help, please. I have just installed Flash-aid and it did improve my flash performance, however, I now have a 30 second delay on every flash video and my computer seems to freeze during this period.

I disabled and uninstalled the flash-aid extention, and still the problem persists. I have removed the flash plugin for Mozilla and reinstalled that also, and I still have the same problem.

Is the flash-aid installation process irreversible? I would like to remove everything that has been installed with it. Please help!

I would try Flash-Aid again, since I have updated it to install the latest Flash Beta 11.2.

If you want to revert, launch the the Advanced Mode. In the *Installation Options* select "Do not install". In the *Removal Options* select everything and in the *Tweaking Options* de-select everything. Click the *Script* tab, then *Execute*. It will remove all changes. Then you can re-install flash from the repositories.

BTW, you don't need to uninstall the extension, since it does nothing by itself, only when you execute the Wizard or other installation modes. Thus removing the extension also doesn't do anything.

---

### Post by vasa1 on 2011-10-30
> **sillyboy said:**
> Why then all the negative posting about FF7?  I seem to see more - than +.

Thanks

You'll see negative comments more than positive ones for many things. I guess it's just human nature!

As LovingLinux says, Fx 7 is just fine and you'll be better off using it rather than Fx 3.6 or 3.5 or whatever.

---

### Post by zika on 2011-11-03
I'm seeing some artifact in lower right corner (can not decioher what it is) on some of the pop-up animations and such in Firefox 10 a1... Am I the only one... ? ;)

---

### Post by lovinglinux on 2011-11-04
> **zika said:**
> I'm seeing some artifact in lower right corner (can not decioher what it is) on some of the pop-up animations and such in Firefox 10 a1... Am I the only one... ? ;)

Is it a triangle?

---

### Post by zika on 2011-11-04
> **lovinglinux said:**
> Is it a triangle?No. It's like an elongated writing, looking like Arabic or something like that...
It exists both in firefox-trunk and in firefox-nightly...

---

### Post by lovinglinux on 2011-11-04
> **zika said:**
> No. It's like an elongated writing, looking like Arabic or something like that...
It exists both in firefox-trunk and in firefox-nightly...

Screenshot please.

---

### Post by zika on 2011-11-04
> **lovinglinux said:**
> Screenshot please.Once/If I catch it. It is on those fast pop-out screnlets... Whatever there name is...

Update: It seems that artifact is present on lower right corner in Flash sub-screens... (11,2,202,19 installed)
So, that is not Firefox issue. Mea culpa...

---

### Post by SPR_3141 on 2011-11-13
> **zika said:**
> No. It's like an elongated writing, looking like Arabic or something like that...
It exists both in firefox-trunk and in firefox-nightly...

I have exactly the same problem (Ubuntu 11.10, Firefox 7.0.1, ) after having updated Flash (11.2.202.19) with the Firefox add-on Flash-Aid. Does someone know where this is coming from?

---

### Post by zika on 2011-11-13
> **SPR_3141 said:**
> I have exactly the same problem (Ubuntu 11.10, Firefox 7.0.1, ) after having updated Flash (11.2.202.19) with the Firefox add-on Flash-Aid. Does someone know where this is coming from?
Just like that. Thank You for taking time to capture and document it. If I downgrade to Flash 10 it disappears...

---

### Post by lovinglinux on 2011-11-13
> **SPR_3141 said:**
> I have exactly the same problem (Ubuntu 11.10, Firefox 7.0.1, ) after having updated Flash (11.2.202.19) with the Firefox add-on Flash-Aid. Does someone know where this is coming from?

I was able to reproduce and investigated the problem. This only happens with the beta version of Flash. Looks like some message embedded by Adobe. In my system, I couldn't read it, but it doesn't look like Arabic. I suppose the message on my system is in Portuguese. I have tested with Flash-Aid and also by downloading the latest beta from Adobe and installing manually.

I wouldn't worry about it, unless it distracts your viewing.

---

### Post by zika on 2011-11-13
No, it does not distract me. At first I thought it was a glitch. Now I'm kind of used to it... ;)

---

### Post by ubupirate on 2011-11-16
Thanks!

Preference tweaks work wonders on Firefox 8. :)

---

### Post by zika on 2011-11-16
> **ubupirate said:**
> Thanks!

Preference tweaks work wonders on Firefox 8. :)They work wonders even in 11.0a1 (2011-11-16) ... ;) Thank You for reminding me to check again. This „install“ of FF (just un-tar-ed in folder) did not get its share of care and attention... Now it did...

---

### Post by iitywygms on 2011-12-02
I get this annoying popup when typing in the google search bar,
How can I stop this from happening?
Im on Natty with firefox 8.0
[IMG]http://i193.photobucket.com/albums/z161/dabears_rule/Screenshot.png[/IMG]

---

### Post by vasa1 on 2011-12-02
> **iitywygms said:**
> I get this annoying popup when typing in the google search bar,
How can I stop this from happening?
Im on Natty with firefox 8.0
...
Do you see it in safe mode?

---

### Post by errrn on 2011-12-02
I had it, but now it's gone. I updated again with flash aid (I don't even think it was to a newer release, just re updated), and it went away. just like "that"!

---

### Post by iitywygms on 2011-12-02
> **vasa1 said:**
> Do you see it in safe mode?

yes.  Can I post any log files or anything?
And, it only appears at the google main page. No where else.
It does not happen with Windows.

---

### Post by vasa1 on 2011-12-02
> **iitywygms said:**
> yes.  Can I post any log files or anything?
And, it only appears at the google main page. No where else.
It does not happen with windblows.

Can you try this?
With Firefox not running...
Temporarily rename your default profile by appending **.backup** to the existing name. In case you don't know, your profile is something like this: alphanumericstring.default and is in a hidden folder, **.mozilla**, in your home folder.
Then start Firefox. It will create a totally new profile. If the problem doesn't occur, it means something in your (original) profile has been corrupted.
If the problem still occurs we'll just have to wait for LovingLinux to help :D
 My *guess* is it could be mimeTypes.rdf that's gone wonky.

---

### Post by belstaffleather on 2011-12-03
> **lovinglinux said:**
> The objective of this tutorial is to provide a simple, but comprehensive, list of optimizations for Firefox and help with troubleshooting common issues. 

The tutorial is currently hosted on my web site, but you can find the table of content below, which links to each corresponding section. For questions and support is preferable that you post on this thread.


Great thread!

---

### Post by lovinglinux on 2011-12-03
> **vasa1 said:**
> Can you try this?
With Firefox not running...
Temporarily rename your default profile by appending **.backup** to the existing name. In case you don't know, your profile is something like this: alphanumericstring.default and is in a hidden folder, **.mozilla**, in your home folder.
Then start Firefox. It will create a totally new profile. If the problem doesn't occur, it means something in your (original) profile has been corrupted.
If the problem still occurs we'll just have to wait for LovingLinux to help :D
 My *guess* is it could be mimeTypes.rdf that's gone wonky.

Does it happen only when you search using the search toolbar in Firefox or it also happens when you use the search form on Google page?

> **belstaffleather said:**
> Great thread!

Thanks. :popcorn:

---

### Post by iitywygms on 2011-12-03
> **vasa1 said:**
> Can you try this?
With Firefox not running...
Temporarily rename your default profile by appending **.backup** to the existing name. In case you don't know, your profile is something like this: alphanumericstring.default and is in a hidden folder, **.mozilla**, in your home folder.
Then start Firefox. It will create a totally new profile. If the problem doesn't occur, it means something in your (original) profile has been corrupted.
If the problem still occurs we'll just have to wait for LovingLinux to help :D
 My *guess* is it could be mimeTypes.rdf that's gone wonky.

Tried as you suggested.  Renaming my profile did not work. Firefox would hang when starting.  But I created a new profile by typing firefox -p in a terminal.  Using a new profile, the error did not occur.
I guess I need to use the new profile?  I disabled all my addons but the error still appeared in my original profile.

> **lovinglinux said:**
> Does it happen only when you search using the search toolbar in Firefox or it also happens when you use the search form on Google page?



Thanks. :popcorn:

Actually you have it backwards.  It ONLY occurs when using the search bar on the google main page.  It does not happen using the search bar in the upper right corner of firefox.

So is the solution creating a new profile?  If so, how can I make it so my bookmarks and passwords are moved over to the new profile?
thanks to all for the help.

---

### Post by lovinglinux on 2011-12-04
> **iitywygms said:**
> Tried as you suggested.  Renaming my profile did not work. Firefox would hang when starting.  But I created a new profile by typing firefox -p in a terminal.  Using a new profile, the error did not occur.
I guess I need to use the new profile?  I disabled all my addons but the error still appeared in my original profile.



Actually you have it backwards.  It ONLY occurs when using the search bar on the google main page.  It does not happen using the search bar in the upper right corner of firefox.

So is the solution creating a new profile?  If so, how can I make it so my bookmarks and passwords are moved over to the new profile?
thanks to all for the help.

Before moving to a new profile, make a backup of ~/.mozilla/firefox/<profilename>, then delete the folder ~/.mozilla/firefox/<profilename>/extensions/ and the file ~/.mozilla/firefox/<profilename>/prefs.js. Test Firefox to see if the problem persists. If the problem persists, then copy the files *places.sqlite*, *key3.db* and *signons.sqlite* to the new profile. They are responsible for the bookmarks and passwords. Don't forget to close Firefox before doing any operation with those files.

---

### Post by iitywygms on 2011-12-05
> **lovinglinux said:**
> Before moving to a new profile, make a backup of ~/.mozilla/firefox/<profilename>, then delete the folder ~/.mozilla/firefox/<profilename>/extensions/ and the file ~/.mozilla/firefox/<profilename>/prefs.js. Test Firefox to see if the problem persists. If the problem persists, then copy the files *places.sqlite*, *key3.db* and *signons.sqlite* to the new profile. They are responsible for the bookmarks and passwords. Don't forget to close Firefox before doing any operation with those files.

I deleted the suggested files but still had the same problem.
So I created the new profile, copied all the files over, and all is well now.
Thanks to all for the help.

---

### Post by tjeremiah on 2012-01-19
does anybody know why Firefox sucks when it comes to displaying large images? I love FF and have been using it for years but whenever I open up a thread that displays large, multiple images, FF completely crashes. This has been a problem for awhile now but is worst since moving to a netbook (less than a GB of RAM).

What also bothers me is that when using Chrome (aka the enemy ;)) it doesnt crash and displays the images smoothly. Same can be said for the browser Empathy. But neither browser has the addons or customization that FF has so I can't consider them my primary browser. 

Lovinglinux, I've tried the options in the optimization pages on your site but neither seem to solve this issue. Any other suggestions?

---

### Post by lovinglinux on 2012-01-20
> **tjeremiah said:**
> does anybody know why Firefox sucks when it comes to displaying large images? I love FF and have been using it for years but whenever I open up a thread that displays large, multiple images, FF completely crashes. This has been a problem for awhile now but is worst since moving to a netbook (less than a GB of RAM).

What also bothers me is that when using Chrome (aka the enemy ;)) it doesnt crash and displays the images smoothly. Same can be said for the browser Empathy. But neither browser has the addons or customization that FF has so I can't consider them my primary browser. 

Lovinglinux, I've tried the options in the optimization pages on your site but neither seem to solve this issue. Any other suggestions?

I am not sure, but I would dare to say it is because multi-process architecture of Chrome.

---

### Post by vasa1 on 2012-01-20
> **tjeremiah said:**
> does anybody know why Firefox sucks when it comes to displaying large images? I love FF and have been using it for years but whenever I open up a thread that displays large, multiple images, FF completely crashes. This has been a problem for awhile now but is worst since moving to a netbook (less than a GB of RAM).

What also bothers me is that when using Chrome (aka the enemy ;)) it doesnt crash and displays the images smoothly. Same can be said for the browser Empathy. But neither browser has the addons or customization that FF has so I can't consider them my primary browser. 

Lovinglinux, I've tried the options in the optimization pages on your site but neither seem to solve this issue. **Any other suggestions**?
Yes, you could still give examples of what you consider "a thread that displays large, multiple images".

---

### Post by tjeremiah on 2012-01-21
> **vasa1 said:**
> Yes, you could still give examples of what you consider "a thread that displays large, multiple images".

any forum that has large multiple images on a page. These are random on sites that I visit. From Engadget to say this : [http://www.gtaforums.com/index.php?showtopic=491242&st=940](http://www.gtaforums.com/index.php?showtopic=491242&st=940)

As more are displayed, Firefox just crashes.

---

### Post by tlu on 2012-01-22
> **tjeremiah said:**
> any forum that has large multiple images on a page. These are random on sites that I visit. From Engadget to say this : [http://www.gtaforums.com/index.php?showtopic=491242&st=940](http://www.gtaforums.com/index.php?showtopic=491242&st=940)

As more are displayed, Firefox just crashes.

Not on my system. It might depend on your hardware (e.g., how much RAM, what graphics card including related driver - open or closed source ... etc.) and on your specific Firefox configuration (like cache management etc.). Again, I don't see these crashes here.

---

### Post by EchoTech on 2012-01-22
Loads just fine here in 1.6 seconds (6Mb DSL), no crash.

---

### Post by SilverWave on 2012-04-06
**Firefox Beta 12.0~b4**

If you install the beta 4 from [https://launchpad.net/~mozillateam/+archive/firefox-next](https://launchpad.net/~mozillateam/+archive/firefox-next) it seems to break flash.

				 					Firefox 12.0 Beta 4 reports that plug-ins are missing (yellow bar at top of page), but if you allow install it does not work afaict.
 
I think that all you need to do is to reinstall flash at least that has worked for me :-)


> flashplugin-nonfree (11.2.202.228ubuntu0.11.10.2~mfn1) oneiric; urgency=low    * Only create symlinks in /usr/lib/mozilla/plugins     - update debian/flashplugin-installer.postinst.in     - update debian/flashplugin-installer.prerm.in   * Don't create a symlink in /usr/share/ubufox/plugins     - update debian/flashplugin-installer.postinst.in  -- Chris Coulson <email address hidden>   Sun, 01 Apr 2012 00:21:17 +0100

---

### Post by koftis on 2012-04-14
[B][FONT=&quot] I am running Ubuntu 11.10 x64 (ssd based  system..)

[/FONT][/B][FONT=&quot]And i want to enable firefox to [/FONT][FONT=&quot] to write cached files  to RAM instead of the ssd
is that possible without creating a Ram disk?
I found this tip but i do not now if it requires ram disk..
[/FONT][B][FONT=&quot]

[/FONT][/B]> [B][FONT=&quot;]Firefox - Use memory cache
[/FONT][/B][FONT=&quot;]reduce disk writes[/FONT]
  [FONT=&quot;]Firefox has the ability to write cached files  to RAM instead of the hard disk. This is not only faster, but will  significantly reduce writes to the SSD while using the browser.[/FONT]
  [FONT=&quot;]To change the cache location to RAM:
Open Firefox -> Type about:config into the address bar ->  Enter -> double-click browser.cache.disk.enable to set the value to  False -> Right-Click anywhere -> New -> Integer ->  Preference Name "disk.cache.memory.capacity" -> value memory size in  KB. Enter 32768 for 32MB, 65536 for 64MB, etc. -> restart Firefox[/FONT]thx!!;)

I also found [this]("http://forums.mozillazine.org/viewtopic.php?f=8&t=2115257")  ...

---

### Post by lovinglinux on 2012-04-14
> **koftis said:**
> [B][FONT=&quot] I am running Ubuntu 11.10 x64 (ssd based  system..)

[/FONT][/B][FONT=&quot]And i want to enable firefox to [/FONT][FONT=&quot] to write cached files  to RAM instead of the ssd
is that possible without creating a Ram disk?
I found this tip but i do not now if it requires ram disk..
[/FONT][B][FONT=&quot]

[/FONT][/B]

thx!!;)
[FONT=&quot][/FONT]

Well, I guess it should work. What the tutorial suggest is disabling disk cache and increasing memory cache capacity. However, I am not sure if will store all data it would store in the disk cache. Try it and check if the browser often reloads the content .

---

### Post by koftis on 2012-04-14
> **lovinglinux said:**
> Well, I guess it should work. What the tutorial suggest is disabling disk cache and increasing memory cache capacity. However, I am not sure if will store all data it would store in the disk cache. Try it and check if the browser often reloads the content .


I also found[ this ]("http://ubuntuforums.org/showthread.php?t=1915105&highlight=ram+disk")
but i am afraid of implementing it:confused:

---

### Post by lovinglinux on 2012-04-14
> **koftis said:**
> I also found[ this ]("http://ubuntuforums.org/showthread.php?t=1915105&highlight=ram+disk")
but i am afraid of implementing it:confused:

Why not just use the simplified method from my tutorial?

[http://www.webgapps.org/tutorials/firefox/optimization/ramdisk-cache](http://www.webgapps.org/tutorials/firefox/optimization/ramdisk-cache)

I have used it for a long time and never got any problem.

---

### Post by koftis on 2012-04-14
> **lovinglinux said:**
> Why not just use the simplified method from my tutorial?

[http://www.webgapps.org/tutorials/firefox/optimization/ramdisk-cache](http://www.webgapps.org/tutorials/firefox/optimization/ramdisk-cache)

I have used it for a long time and never got any problem.


I could not find [B]browser.cache.memory.capacity

is this the "browser.cache.memory.max_entry_size"


[/B]**i've created it **

> **Firefox Memory Leak Fix** Open a new tab. Type &#8220;about:config&#8221; without quotes into the address bar and hit enter/click Go.
 Right-click anywhere, select New, then Integer. In the dialog prompt that appears, type:
 browser.cache.memory.capacity
 Click OK. Another dialog prompt will appear. This is where you decide  how much memory to allocate to Firefox. This depends on how much RAM  your computer has, but generally you don&#8217;t want to allocate too little  (under 8MB), but if you allocate too much, you might as well not do  this. A good recommended setting is 16MB. If you want 16MB, enter this  value into the dialog prompt:
 16384


---

### Post by lovinglinux on 2012-04-14
> **koftis said:**
> I could not find browser.cache.memory.capacity

is this the "browser.cache.memory.max_entry_size"

No. The first determines the size of the entire memory cache, while the second determines the maximum size of a single file. If a file has 90% of the size of the entire cache, it is not saved, even if the second preference allows it.

> **koftis said:**
> **i've created it **

Just create *browser.cache.memory.capacity* preference.

---

### Post by koftis on 2012-04-15
> **lovinglinux said:**
> No. The first determines the size of the entire memory cache, while the second determines the maximum size of a single file. If a file has 90% of the size of the entire cache, it is not saved, even if the second preference allows it.



Just create *browser.cache.memory.capacity* preference.


Did it..

Thx a lot "lovinglinux" 
(i've just bookmarked your site..)

> I am now trying to find a similar solution for the opera browser

:lolflag:

---

### Post by lovinglinux on 2012-04-15
Type *opera:config#UserPrefs|Cache Directory4* in Opera's address bar.

---

### Post by koftis on 2012-04-15
> **lovinglinux said:**
> Type *opera:config#UserPrefs|Cache Directory4* in Opera's address bar.

just did it..
:p

---

### Post by lovinglinux on 2012-04-15
> **koftis said:**
> just did it..
:p

Replace the path with /dev/shm

There is also **opera:config#Cache|Application Cache Quota**

---

### Post by koftis on 2012-04-15
> **lovinglinux said:**
> Replace the path with /dev/shm

There is also **opera:config#Cache|Application Cache Quota**

how much should i give it says 51200?


You are my hero m8..):P

&#921; have 8 gb ram..

---

### Post by lovinglinux on 2012-04-15
> **koftis said:**
> how much should i give it says 51200?


You are my hero m8..):P

If you are changing the disk cache directory to use RAM, then depends on how much RAM you have. The table at [http://www.webgapps.org/tutorials/firefox/optimization/preferences-tweaks](http://www.webgapps.org/tutorials/firefox/optimization/preferences-tweaks) might help.

---

### Post by Cincinnatux on 2012-04-15
> **lovinglinux said:**
> The objective of this tutorial is to provide a simple, but comprehensive, list of optimizations for Firefox and help with troubleshooting common issues. 

The tutorial is currently hosted on my web site, but you can find the table of content below, which links to each corresponding section. For questions and support is preferable that you post on this thread.

**[SIZE="4"][COLOR="Grey"]Table of Content[/COLOR][/SIZE]**

[LIST]
[*][[COLOR="Sienna"]**Benchmarks**[/COLOR]](http://www.webgapps.org/tutorials/firefox/optimization/benchmarks)
[*][[COLOR="Sienna"]**Profiles & Backups**[/COLOR]](http://www.webgapps.org/tutorials/firefox/general/profiles-and-backups)
[*][[COLOR="Sienna"]**Database Optimization**[/COLOR]](http://www.webgapps.org/tutorials/firefox/optimization/database-optimization)
[*][[COLOR="Sienna"]**Extensions Optimization**[/COLOR]](http://www.webgapps.org/tutorials/firefox/optimization/extension-optimization)
[*][[COLOR="Sienna"]**Preferences Tweaks**[/COLOR]](http://www.webgapps.org/tutorials/firefox/optimization/preferences-tweaks)
[*][[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://www.webgapps.org/tutorials/firefox/optimization/flash-optimization)
[*][[COLOR="Sienna"]**Flash Issues & Solutions**[/COLOR]](http://www.webgapps.org/tutorials/firefox/troubleshooting/flash-issues-and-solutions)
[*][[COLOR="Sienna"]**Installing Other Versions**[/COLOR]]("http://www.webgapps.org/tutorials/firefox/general/installing-other-versions")
[*][[COLOR="Sienna"]**Troubleshooting**[/COLOR]](http://www.webgapps.org/tutorials/firefox/troubleshooting)
[*][[COLOR="Sienna"]**Fixing a problematic or corrupted profile**[/COLOR]](http://www.webgapps.org/tutorials/firefox/troubleshooting/fixing-corrupted-profiles)
[*][[COLOR="Sienna"]**Compiling Firefox**[/COLOR]](http://www.webgapps.org/tutorials/firefox/advanced/compiling-from-source)
[/LIST]

Wow.  Just...wow.  Thanks!

---

### Post by lovinglinux on 2012-04-16
> **Cincinnatux said:**
> Wow.  Just...wow.  Thanks!

You are welcome.

---

### Post by didistortion on 2012-04-24
> **lovinglinux said:**
> The objective of this tutorial is to provide a simple, but comprehensive, list of optimizations for Firefox and help with troubleshooting common issues. 

The tutorial is currently hosted on my web site, but you can find the table of content below, which links to each corresponding section. For questions and support is preferable that you post on this thread.

**[SIZE="4"][COLOR="Grey"]Table of Content[/COLOR][/SIZE]**

[LIST]
[*][[COLOR="Sienna"]**Benchmarks**[/COLOR]](http://www.webgapps.org/tutorials/firefox/optimization/benchmarks)
[*][[COLOR="Sienna"]**Profiles & Backups**[/COLOR]](http://www.webgapps.org/tutorials/firefox/general/profiles-and-backups)
[*][[COLOR="Sienna"]**Database Optimization**[/COLOR]](http://www.webgapps.org/tutorials/firefox/optimization/database-optimization)
[*][[COLOR="Sienna"]**Extensions Optimization**[/COLOR]](http://www.webgapps.org/tutorials/firefox/optimization/extension-optimization)
[*][[COLOR="Sienna"]**Preferences Tweaks**[/COLOR]](http://www.webgapps.org/tutorials/firefox/optimization/preferences-tweaks)
[*][[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://www.webgapps.org/tutorials/firefox/optimization/flash-optimization)
[*][[COLOR="Sienna"]**Flash Issues & Solutions**[/COLOR]](http://www.webgapps.org/tutorials/firefox/troubleshooting/flash-issues-and-solutions)
[*][[COLOR="Sienna"]**Installing Other Versions**[/COLOR]]("http://www.webgapps.org/tutorials/firefox/general/installing-other-versions")
[*][[COLOR="Sienna"]**Troubleshooting**[/COLOR]](http://www.webgapps.org/tutorials/firefox/troubleshooting)
[*][[COLOR="Sienna"]**Fixing a problematic or corrupted profile**[/COLOR]](http://www.webgapps.org/tutorials/firefox/troubleshooting/fixing-corrupted-profiles)
[*][[COLOR="Sienna"]**Compiling Firefox**[/COLOR]](http://www.webgapps.org/tutorials/firefox/advanced/compiling-from-source)
[/LIST]

Did you change the url's? I'm getting 404's.

[IMG]http://webgapps.org/wp-content/uploads/2012/04/404.jpg[/IMG]

---

### Post by lovinglinux on 2012-04-24
> **didistortion said:**
> Did you change the url's? I'm getting 404's.

[IMG]http://webgapps.org/wp-content/uploads/2012/04/404.jpg[/IMG]


Yes. I have changed the server, the CMS platform and urls. However, there are some redirects that should have be working. I don't know why they aren't. I will investigate.

Meanwhile, here are the new ones:

[http://webgapps.org/groups/firefox/forum/topic/firefox-optiomization-and-troubleshooting/](http://webgapps.org/groups/firefox/forum/topic/firefox-optiomization-and-troubleshooting/)

Let me know if you can't reach those.

---

### Post by lovinglinux on 2012-04-24
> **lovinglinux said:**
> Yes. I have changed the server, the CMS platform and urls. However, there are some redirects that should have be working. I don't know why they aren't. I will investigate.

Meanwhile, here are the new ones:

[http://webgapps.org/groups/firefox/forum/topic/firefox-optiomization-and-troubleshooting/](http://webgapps.org/groups/firefox/forum/topic/firefox-optiomization-and-troubleshooting/)

Let me know if you can't reach those.

Fixed.

---

### Post by lovinglinux on 2012-04-24
> **lovinglinux said:**
> Fixed.

Unfixed. The fix created a problem, so I had to revert. I am trying to solve with the hosting support. Please stand by.

---

### Post by lovinglinux on 2012-04-24
> **lovinglinux said:**
> Unfixed. The fix created a problem, so I had to revert. I am trying to solve with the hosting support. Please stand by.

Fixed. The old links should be working by now.

---

### Post by didistortion on 2012-04-24
Thanks for the quick reply!

Still not working correctly though. When going to [http://webgapps.org/groups/firefox/docs/page/2/](http://webgapps.org/groups/firefox/docs/page/2/) it shows nothing instead of docs 11-17 (both firefox + Chromium).

Btw, I was looking for "Compiling Firefox", can't find it anywhere.

---

### Post by lovinglinux on 2012-04-24
> **didistortion said:**
> Thanks for the quick reply!

Still not working correctly though. When going to [http://webgapps.org/groups/firefox/docs/page/2/](http://webgapps.org/groups/firefox/docs/page/2/) it shows nothing instead of docs 11-17 (both firefox + Chromium).

That is another issue I am trying to solve since yesterday. Please use this page instead: [http://webgapps.org/groups/firefox/forum/topic/firefox-optiomization-and-troubleshooting/](http://webgapps.org/groups/firefox/forum/topic/firefox-optiomization-and-troubleshooting/)


> **didistortion said:**
> Btw, I was looking for "Compiling Firefox", can't find it anywhere.

I saw several clicks on that link in my 404 report. Well, that was the only tutorial I removed from the server, because it was outdated.

Any particular reason why you want to compile Firefox?

---

### Post by lovinglinux on 2012-04-24
> **didistortion said:**
> Btw, I was looking for "Compiling Firefox", can't find it anywhere.

I wasn't going to publish it, but here it is:

[http://webgapps.org/groups/firefox/docs/compiling-from-source/](http://webgapps.org/groups/firefox/docs/compiling-from-source/)

Keep in mind I haven't used this in a long time and it will probably fail.

---

### Post by didistortion on 2012-04-28
Thanks!

I was building Firefox with patches from the [Tor Project](https://www.torproject.org/projects/torbrowser-details.html.en). I just needed the Tor Browser, not the Tor Browser Bundle.

Btw, I found some usable info in your doc.

---

### Post by firekage on 2012-06-24
Guys, i have strange problem with firefox but on all Linux machines. 

I have bookmarks, i had bookmarked many websites that i need to have  acces. In fact, it was did over past six years and synchronize with  xmarks plugin for firefox.

 On all Windows machine when i click on bookmarks tab (i created folders  in bookmarks in order to have good view of what i have, so for an  example there are folders like: ubuntu, ubuntu_repos, linux, slackware,  law, cars, forums and so on) the tabs react swiftly, right away and i  can use them.

On all Linux machine like Slackware, Ubuntu 11.10 and so on, when i  click bookmarks tab (i have more than 6000 tabs added for firefox, on  Windows it works great) i see a list of bookmarks folders, i enter/click  for an example: linux folder tabs, and then firefox freezez for few  seconds also with unity (control bar for the system). Then i can enter  the folders and i should have right away listed bookmarks in linux  folder bookmarks in Firefox but i don't have. Again it stops/freezes for  couple of seconds (sometimes it takes loong) and after it i see that my  bookmarks are showing up one after another. 

I use many bookmarks, many bookmared folders and sites and it sometimes  drive me mad because on Windows it just works ok, i don't know why on  Ubuntu wit Unity and even Slackware with KDE the same strange things  occurs all the time. I tried it on linux Firefox 4,7,12 or 13.

Can you help me to fix it?

---

### Post by lovinglinux on 2012-06-25
> **firekage said:**
> Guys, i have strange problem with firefox but on all Linux machines. 

I have bookmarks, i had bookmarked many websites that i need to have  acces. In fact, it was did over past six years and synchronize with  xmarks plugin for firefox.

 On all Windows machine when i click on bookmarks tab (i created folders  in bookmarks in order to have good view of what i have, so for an  example there are folders like: ubuntu, ubuntu_repos, linux, slackware,  law, cars, forums and so on) the tabs react swiftly, right away and i  can use them.

On all Linux machine like Slackware, Ubuntu 11.10 and so on, when i  click bookmarks tab (i have more than 6000 tabs added for firefox, on  Windows it works great) i see a list of bookmarks folders, i enter/click  for an example: linux folder tabs, and then firefox freezez for few  seconds also with unity (control bar for the system). Then i can enter  the folders and i should have right away listed bookmarks in linux  folder bookmarks in Firefox but i don't have. Again it stops/freezes for  couple of seconds (sometimes it takes loong) and after it i see that my  bookmarks are showing up one after another. 

I use many bookmarks, many bookmared folders and sites and it sometimes  drive me mad because on Windows it just works ok, i don't know why on  Ubuntu wit Unity and even Slackware with KDE the same strange things  occurs all the time. I tried it on linux Firefox 4,7,12 or 13.

Can you help me to fix it?

Try to optimize the places.sqlite database. It should fix the problem.

[http://webgapps.org/groups/firefox/docs/database-optimization/](http://webgapps.org/groups/firefox/docs/database-optimization/)

---

### Post by firekage on 2012-06-25
> **lovinglinux said:**
> Try to optimize the places.sqlite database. It should fix the problem.

[http://webgapps.org/groups/firefox/docs/database-optimization/](http://webgapps.org/groups/firefox/docs/database-optimization/)

Didn't help.

---

### Post by vasa1 on 2012-06-25
> **firekage said:**
> Guys, i have strange problem with firefox but on all Linux machines. 
... (i have more than **6000 tabs** added for firefox, on  Windows it works great)...
Great to know that works with Windows. Personally, I don't trust the bookmarks or history of **any** browser on **any** OS. Actually, I don't trust the entire profile folder.

---

### Post by firekage on 2012-06-25
> **vasa1 said:**
> Great to know that works with Windows. Personally, I don't trust the bookmarks or history of **any** browser on **any** OS. Actually, I don't trust the entire profile folder.

It is synchronized with xmarks and on different windows machines, even with one core cpu, works great, on Linux with quad core cpu works bad, slow, as i mentioned above.

---

### Post by lovinglinux on 2012-06-26
> **firekage said:**
> It is synchronized with xmarks and on different windows machines, even with one core cpu, works great, on Linux with quad core cpu works bad, slow, as i mentioned above.

Try a clean profile with a clean bookmark database, just to see if the problem is independent of database size and data. Add some bookmarks and test. If the problem persists, then the issue might be something like disk access speed or even video driver.

If the problem does not persist then is the database. You could export the bookmarks to HTML, delete the database and import them back. This can solve some issues that occur with old profiles and new Firefox versions.

---

### Post by firekage on 2012-06-26
> **lovinglinux said:**
> Try a clean profile with a clean bookmark database, just to see if the problem is independent of database size and data. Add some bookmarks and test. If the problem persists, then the issue might be something like disk access speed or even video driver.

This problem doesen't occurs when there are few bookmarks. Also, on some folders where there aren't loot of bookamrked links/websites it runs faster than with folder that have many bookmarks.

You want me to bookmarks few thing and check or do a new profile and import from xmarks? If the first one than it works, if the second one than i could try but i did it a couple of times and the result was the same on linux machines - slow like i mentioned till to a completly freezing for some amount of time.

How to start clean profile?

---

### Post by firekage on 2012-06-26
I bookmarked as html in 11.10 and in Firefox 7, i imported from html to 12.04 and FF 11 and there is still the same bug. When i open folder in bookmarks that has a lot bookmarks than Unity stops, firefox stops and it takes some time to work back or show content of this folder in bookmarks.

---

### Post by Keeper of the Keys on 2012-08-31
I am working on a light remote access system and FF lack of support for HTTP_PROXY when set to "Use System Settings" is killing me.

The system is Ubuntu-server, with X2Go and LXDE (also XFCE4 but that seems to perform less good so I'm probably removing it).

I tried adding mandatory/default gconf keys that set the proxy but to no avail.

How do I set up a systemwide proxy that FF also accepts, Chromium is working like a charm with the environment vars...

---

### Post by firekage on 2012-09-02
I found this at the mozilla forum:

[http://forums.mozillazine.org/viewtopic.php?f=38&t=2036069](http://forums.mozillazine.org/viewtopic.php?f=38&t=2036069)

It's the same problem that i have, but, in  fact, he had it on Windows while i have it on all Linux distros. I have more than 10.000 bookmarks, he have about 5000 and the problem is the same - it tooks very long to respond when using bookmarks - when i try to enter bookmarked site when using bookmarks, just like him. 

I see that there is no fix for it. Don't know why i don't have this on different windows machines and different windows version.

---

### Post by lovinglinux on 2012-09-02
> **firekage said:**
> I found this at the mozilla forum:

[http://forums.mozillazine.org/viewtopic.php?f=38&t=2036069](http://forums.mozillazine.org/viewtopic.php?f=38&t=2036069)

It's the same problem that i have, but, in  fact, he had it on Windows while i have it on all Linux distros. I have more than 10.000 bookmarks, he have about 5000 and the problem is the same - it tooks very long to respond when using bookmarks - when i try to enter bookmarked site when using bookmarks, just like him. 

I see that there is no fix for it. Don't know why i don't have this on different windows machines and different windows version.

That thread is old. The author is refering to Fireofx 3.6, which was a lot slower than current versions.

I am not sure where the problem is. Try to disable Xmarks. It can be really slow sometimes and this could be affecting bookmarks performance.


You could also experiment running the Firefox profile from RAM, if it solves the problem, then most likely the issue is sqlite/HD related. If not, then most likely to be a video driver issue.

[http://ubuntuforums.org/showthread.php?t=1120475](http://ubuntuforums.org/showthread.php?t=1120475)

I haven't used this for a while, so I am not sure if it still works. Backups are highly recommended before trying this.

---

### Post by Karandras on 2012-09-02
not sure if this is the tread for my question but ill try anyways.

i  know in the latest versions of firefox, there was a way to change the  order of the right click menu to have open link in new window 1st and  below that have open link in new tab. im getting very frustrated trying  to find how to do this (was able to do it before i did a fresh install  of Xubuntu 12.04). can anyone point me in the right direction or know  what i need to modify (where it be a file or in the about:config)? 

when googleing my question all i see are solutions for windows.

---

### Post by studiogrynn on 2012-09-05
Try the menu editor extension.
[https://addons.mozilla.org/firefox/addon/menu-editor]("https://addons.mozilla.org/firefox/addon/menu-editor")

---

### Post by NonStop on 2012-09-08
Hey, I have a problem with my titlebar. Am using Lubuntu 12.04. Unlike in Ubuntu when the everything is fully maximised the titlear dissapears, in Lubuntu there is a massive titlebar above it saying the webpage in big letters and the firefox icons on the left hand side, no matter whether it is maximised or not.

Any ideas? Thank you!

---

### Post by mikewhatever on 2012-09-08
> **NonStop said:**
> Hey, I have a problem with my titlebar. Am using Lubuntu 12.04. Unlike in Ubuntu when the everything is fully maximised the titlear dissapears, in Lubuntu there is a massive titlebar above it saying the webpage in big letters and the firefox icons on the left hand side, no matter whether it is maximised or not.

Any ideas? Thank you!

Installing Firefox in Lubuntu will also pull in the firefox-globalmenu package. Try ininstalling it, then logout/in.

---

### Post by NonStop on 2012-09-10
> **mikewhatever said:**
> Installing Firefox in Lubuntu will also pull in the firefox-globalmenu package. Try ininstalling it, then logout/in.

I'm a bit of a newbie to the whole thing I'm afraid, where should I go to do this without screwing up firefox?

---

### Post by mikewhatever on 2012-09-10
> **NonStop said:**
> I'm a bit of a newbie to the whole thing I'm afraid, where should I go to do this without screwing up firefox?

Synaptic Package Manager, alternatively, run this in a terminal window:

sudo apt-get remove firefox-globalmenu

Either way should not screw up anything.

---

### Post by lovinglinux on 2012-09-11
> **mikewhatever said:**
> Synaptic Package Manager, alternatively, run this in a terminal window:

sudo apt-get remove firefox-globalmenu

Either way should not screw up anything.

You can also uninstall it using the Software Center. Just launch it, search for *firefox-globalmenu*, select the result and click the remove button.

---

