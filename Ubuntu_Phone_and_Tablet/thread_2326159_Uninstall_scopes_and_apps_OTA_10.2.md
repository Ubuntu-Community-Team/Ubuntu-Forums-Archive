---
title: "Uninstall scopes and apps OTA 10.2"
date: 2016-05-28
forum: Ubuntu Phone and Tablet
---

### Post by mily2 on 2016-05-28
Hi Community,

I would like remove all scopes that I don't use: Amazon, Ebay, Yahoo! Finance, Shopping, Yelp... How I can uninstall these, please?

They are more scopes and apps, that after uninstall by "Ubuntu Store",  continue to appear in Permy app, like: BBC, BBC-Sport,EuroNews, FitBit,  Food, Google Plus, Instagram, Telegram, Soundcloud, Twitter, webapp-Amazon, webapp-Ebay, webapp-Facebook, webapp-Gmail, webapp- Twitter... 
It's very confused and worrying; especially by the affected permissions (accounts, connectivity, content_exchange, content_exchange_source networking...) How I can delete these permanently?

I tried uninstall from terminal, but these don't appear using "click list" command-line.

---

### Post by mily2 on 2016-06-10
Anybody know delete these scopes and apps?

---

### Post by krusty8 on 2016-06-11
Let me see whether I understood you correctly. Correct me if I got it wrong.
- Originally you saw these apps in the dash.
- And you saw these scopes in that scope management list when you swipe up from the bottom of the dash. 
- Also both, apps and scopes showed up as installed in the store
- You uninstalled them from the store
- Now the apps and scopes do not show up in the normal places anymore, points 1 and 2 above
- however, they do show up in Permy

Is that the situation? Maybe there are just some configuration left overs? Have you tried searching on the disk? Can you verify where these items have files when installed? /opt ? /usr .... ~/.local ~/.config ~/.cache .... Just try something like

find / -iname '*amazon*'

Or maybe click would tell you.

Then verify that the files go away when you uninstall them, or whether any files are left.

Hth!

---

### Post by mily2 on 2016-06-13
Thanks krusty8 for help me.

Points 1, 2, 3 and 4 are correct.

Point 5: I don't saw these apps in the dash, but I saw these scopes in the scope management list: Amazon, Ebay, 7digital, Yahoo!finance... I attached screenshots of my scope management list.

Point 6: Permy apparent works OK. I attached Permy app sreenshots: with OSMScaut app, after uninstalling OSMScaut (app disappears from Permy) and all apps and scopes.

I tried searching disk. I attached /opt screenshot with Telegram and SoundCloud (these apps ware uninstalled from the Ubuntu Store previously); and iname Amazon, Google and Facebook screenshots (I can't see the first lines because the limited scrolling lines displayed on the Terminal app;[ http://ubuntuforums.org/showthread.php?t=2326806]("http://ubuntuforums.org/showthread.php?t=2326806") ).

This is the link with all screenshots: [URL="https://upload.disroot.org/r/EFZJTC_xzR#XszqU6c0QMNw2J6SraPzwt8xYZNm5/YIS9VPZHk3vhA="]https://upload.disroot.org/r/5okuMRZX7q#4pDL68nKOJc36RDHgz4rpvHc2sD+vdWQGfu/5w1zNNE=
[/URL]
Regards

---

### Post by krusty8 on 2016-06-14
Strange indeed!

My UT Nexus 7 seems to not want to download the screenshots. I've commented on the terminal scroll thread - maybe that helps. Also I suggest you establish commandline access from your destkop via abd or ssh. That would be a lot more convenient for you for bigger terminal tasks and should allow you to copy paste the terminal output rather than needing screenshots.

However, even without having seen the screenshots, if point 5 is that clear, I'd raise a bug on launchpad, if none exists yet.

---

### Post by mily2 on 2016-06-14
Thanks krusty8.

Confirmed: unfortunately Ubuntu Touch can't open the link (and neither links in a PDF document via Document Viewer app).  I tried with Liri Browser, Browserhtm and Browser (Firefox on Android  6.01 and Ubuntu 12.04 Desktop 32-bit and 64-bit download it OK). Can you download the  screenshots with desktop or Android, please? [https://upload.disroot.org/r/5okuMRZX7q#4pDL68nKOJc36RDHgz4rpvHc2sD+vdWQGfu/5w1zNNE=](https://upload.disroot.org/r/5okuMRZX7q#4pDL68nKOJc36RDHgz4rpvHc2sD+vdWQGfu/5w1zNNE=)
I  did new screenshots for BBC, FitBit, Google, Instagram, Telegram,  Soundcloud, Twitter, Amazon, Ebay, Facebook and Gmail using less  command: [https://upload.disroot.org/r/HyYKpwOCxm#Gxdtjc37+v4QRgVAfsp8QMYMV0s4ikU5Y06WIgsTTa8=](https://upload.disroot.org/r/HyYKpwOCxm#Gxdtjc37+v4QRgVAfsp8QMYMV0s4ikU5Y06WIgsTTa8=)
I will try via adb or ssh.

I discovered that scopes and apps are in /custom/click .

The  most serious problem is all apps and scopes, by default installed, that  not appear in Ubuntu Store; although delete default apps and scopes via  Ubuntu Store, and still appear in Permy and in too much directories also  is worrisome.
The bug is reported: [https://bugs.launchpad.net/ubuntu/+source/unity8/+bug/1404824](https://bugs.launchpad.net/ubuntu/+source/unity8/+bug/1404824)

Do you know runlevel configuration tool like rcconf? or How I can install rcconf without lost OTAs?

---

### Post by krusty8 on 2016-06-15
> **mily2 said:**
> Can you download the  screenshots with desktop or Android, please?


I've looked through a few of them now. Can't claim that it is giving me a lot of additional ideas to advise. I guess some things like webapps, are not gonna do much by themselves unless you start them. However, I think I do understand that this kind of argumentation is not what you are looking for. Also there are some .so files which might or might not get called to - I don't know. Also with the scopes, I don't know whether they get triggered in any way other than explicit user interaction.

> 
I discovered that scopes and apps are in /custom/click .
The bug is reported: [https://bugs.launchpad.net/ubuntu/+source/unity8/+bug/1404824](https://bugs.launchpad.net/ubuntu/+source/unity8/+bug/1404824)


I'm afraid unless you want to break out the big RW and rm -rf /custom hammer (on your own risk of course, you didn't hear me advise that! I don't know what you end up with), I guess waiting for a response on the bug report might be your only remaining option - and it's probably not a fast one. 


> 

Do you know runlevel configuration tool like rcconf? 

Nope. Sorry.

> 
How I can install rcconf without lost OTAs?

I don't know. I don't even really know whether things like runlevels still apply to modern day ubuntu (or any linux really). Is that still a thing in todays upstart (systemd) reality?

However, installing with apt-get after mount -o rw,remount / does probably mean losing OTAs and it does probably call for reflashing sooner or later.

Installing into a chroot might not actually allow you to do what you want to do with that tool (whatever that is that you're trying to achieve).

Installing into a libertine container probably has a) the same limitations as chroot and b) has likely not yet been released for your device.

---

### Post by mily2 on 2016-06-15
Thank you very much.

I use rcconf in Ubuntu 12.04 and 16.04 Desktop without any problem.

I will try configure the services at startup UT with upstart. Any advice or command "miracle", please? I find this app that creates script for upstart, TouchRules: [https://uappexplorer.com/app/com.ubuntu.developer.psasse.touchrules](https://uappexplorer.com/app/com.ubuntu.developer.psasse.touchrules)

Can I install vim without are the drawbacks stated in the last two posts (about install rcconf)? and gedit?

---

### Post by krusty8 on 2016-06-16
Upstart - sorry dont have any experience with the configuration. The app that you found sounds like a great lead!

Vim - have you checked? Its installed on my device and I dont recall having apt-get installed it myself.

Gedit - well, here we are talking about an installation that requires an xserver. 

My best advise: Wait for libertine. 

2nd best: Take the RW plunge. 

3rd best: Maaaaaayyyybe one can actually install all of xmir inside a chroot [http://askubuntu.com/a/623311](http://askubuntu.com/a/623311) but I am not aware that anybody ever attemted. Roll up your sleeves you would be blazing a new trail in UT world :) Not sure whether this is really doable. Chroot should be ok for command line programs. **X applications** should work as well. **X server** .... well ... if you're looking for a challenge :)

---

### Post by mily2 on 2016-06-16
Thanks, I will follow your advices.

I have not checked right. I used vim command instead of vi.

I find this text editor: [URL="https://uappexplorer.com/app/com.ubuntu.developer.pawstr.edit"]https://uappexplorer.com/app/com.ubuntu.developer.pawstr.edit
[/URL]
I will also try configure services, apps and scopes with those apps and UFW: [URL="https://open.uappexplorer.com/app/tweakgeek.mzanetti"]
[/URL][https://open.uappexplorer.com/app/tweakgeek.mzanetti](https://open.uappexplorer.com/app/tweakgeek.mzanetti)  
[URL="https://open.uappexplorer.com/app/ut-tweak-tool.sverzegnassi"]https://open.uappexplorer.com/app/ut-tweak-tool.sverzegnassi 
[/URL][https://open.uappexplorer.com/app/upstartusersession.chahn](https://open.uappexplorer.com/app/upstartusersession.chahn)

---

### Post by mily2 on 2016-06-16
UT Tweak Tool does not detect those scopes: Amazon, Ebay, 7digital, Reedit, Yahoo!finances, Open Library and The Weather Channel (listed in the UT scope management list); but discovered new scopes installed! like Inrix and Hints!
 At least in the section apps they are not surprises (not are listed Telegram neither SoundCloud; even if they are in /opt).

---

### Post by andrew-q2 on 2016-06-17
"The  most serious problem is all apps and scopes, by default installed, that  not appear in Ubuntu Store"

If I understand ok, this is similar to my comment (3) here: [http://ubuntuforums.org/showthread.php?t=2325458](http://ubuntuforums.org/showthread.php?t=2325458)
How about a future OTA included an app for tidying up things like hangover files after uninstalling apps.  A "phone cleanup" utility.

---

### Post by krusty8 on 2016-06-19
> **mily2 said:**
> UT Tweak Tool does not detect those scopes

You could try to reinstall some of these temporarily, maybe we get a better understanding. What do the Store, Permy, UTTT and find think when it is *actually* installed?

---

### Post by mily2 on 2016-06-19
Thanks.

**Andrew-q2**, about your problem: "2. In Security and privacy \ Location, I see various apps listed, but  there is one entry with no app shown.  Surely there should not be such  an entry.  What does this blank entry refer to please?  (MX4, OTA 10.1)" [http://ubuntuforums.org/showthread.php?t=2325458](http://ubuntuforums.org/showthread.php?t=2325458)
I have the same problem. It has origin in OSMScaut app; after uninstalling OSMScaut I have entry with no app shown in privacy \ Location.

I hope "anxious" a "phone cleanup" utility (I deleted a file of 5GB via File Manage app, but the space was not liberated according config \ about this device \ storage. I searched trash vainly; after two days the space was liberated mysteriously automatically),  "uninstall app" effective utility, and "configurator services" utility; it's very frustrating.
It is a problem like your "3", more default installed scopes that are not uninstallable (and some apps like Telegram and SoundCloud, but maybe this is the problem of temporary files).


> **krusty8 said:**
> You could try to reinstall some[FONT=arial] of these  [/FONT]temporarily, maybe we get a better understanding. What do the Store,  Permy, UTTT and find think when it is *actually* installed?
Reinstall Amazon, Ebay, 7digital, Reedit, Yahoo!finances, Open Library and The Weather Channel scopes? It is impossible, they are not listed in "Ubuntu Store", [https://uappexplorer.com/apps?type=scope](https://uappexplorer.com/apps?type=scope) 

About **Permy app**, continues as before:  Apps and scopes UT default installed, like  BBC, BBC-Sport,EuroNews, FitBit,  Food, Google Plus, Instagram,  Telegram, Soundcloud, Twitter, webapp-Amazon, webapp-Ebay,  webapp-Facebook, webapp-Gmail, webapp- Twitter..., continue to appear in Permy after uninstall via "Ubuntu Store" (and via "[FONT=arial]click unregister <name of app or scope as generated by click list> --user=phablet"[/FONT] ) (webapp-Amazon, webapp-Ebay and scopes of the previous point are uninstallable)._ Apps installed for me_ via "Ubuntu Store", like OSMScaut, _disappear after uninstall_ (as I show in the previous screenshots).

About **Ubuntu Store** and **UTTT**. The apps and scopes that I uninstalled via Ubuntu Store not appear in UTTT.

---

