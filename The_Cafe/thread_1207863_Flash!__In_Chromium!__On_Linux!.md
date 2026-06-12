---
title: "Flash!  In Chromium!  On Linux!"
date: 2009-07-08
forum: The Cafe
---

### Post by Giant Speck on 2009-07-08
Zomg it works!

---

### Post by linuxguymarshall on 2009-07-08
How did you pull this one off? And can I see a game on somthing like AddictingGames being played because with YouTube being owned by Google they may ahve made a bit of compatibility there.

---

### Post by Giant Speck on 2009-07-08
> **linuxguymarshall said:**
> How did you pull this one off? And can I see a game on somthing like AddictingGames being played because with YouTube being owned by Google they may ahve made a bit of compatibility there.

I entered the following commands in a terminal a few days ago:

```
cd /usr/lib/chromium-browser/plugins
sudo ln -s /usr/lib/firefox/plugins/flashplugin-alternative.so
```

Until today's update, only sound was working, but now sound and video are working.

The only thing that saddens me, though, is that Pandora doesn't seem to want to load all the way.  :(

---

### Post by BlackRoijaX on 2009-07-08
Am I the only person who doesn't care about Google Chrome? I like Google but Chrome just feels too lightweight compared with Firefox.

---

### Post by cph05a on 2009-07-08
> Am I the only person who doesn't care about Google Chrome? I like Google but Chrome just feels too lightweight compared with Firefox.

I think this browser has a lot of potential. Just give it some time.

---

### Post by Giant Speck on 2009-07-08
> **BlackRoijaX said:**
> Am I the only person who doesn't care about Google Chrome? I like Google but Chrome just feels too lightweight compared with Firefox.

I just like having variety.

---

### Post by Closed_Port on 2009-07-08
Great! I've been waiting for this.

---

### Post by BlackRoijaX on 2009-07-08
> **Giant Speck said:**
> I just like having variety.

Can't argue with that.

---

### Post by Giant Speck on 2009-07-08
Please note that using the command:

```
sudo ln -s /usr/lib/firefox/plugins/flashplugin.so
```

should also work instead of 

```
sudo ln -s /usr/lib/firefox/plugins/flashplugin-alternative.so
```

For some reason, on my computer, the only thing in the Firefox plugins folder was flashplugin-alternative.so.

---

### Post by swoll1980 on 2009-07-08
Is their a way to change the fonts?

Add: I get audio, but no video.

---

### Post by Giant Speck on 2009-07-08
> **swoll1980 said:**
> Is their a way to change the fonts?

Not yet.  That seems to be an issue with Google's port of WebKit.  It doesn't use gtk-webkit like Midori or Epiphany-Webkit, for example, and therefore does not pull the font rendering settings from the desktop.

---

### Post by swoll1980 on 2009-07-08
> **Giant Speck said:**
> Not yet.  That seems to be an issue with Google's port of WebKit.  It doesn't use gtk-webkit like Midori or Epiphany-Webkit, for example, and therefore does not pull the font rendering settings from the desktop.

Oh well. It's coming along nice though. I'm amazed at how fast they're moving it along.

---

### Post by bostonaholic on 2009-07-08
Wait, when did chrome start working for Linux?  I signed up for the email list from Google... I must be out of the loop.

---

### Post by swoll1980 on 2009-07-08
> **bostonaholic said:**
> Wait, when did chrome start working for Linux?  I signed up for the email list from Google... I must be out of the loop.

A pre-alpha Chrome was available like a month ago. We're talking about Chromium, they are not the same thing.

---

### Post by Closed_Port on 2009-07-08
> **swoll1980 said:**
> Is their a way to change the fonts?

Add: I get audio, but no video.
Try to update. I did when I saw this here and with the latest build it's working.

---

### Post by sdlynx on 2009-07-08
> **Giant Speck said:**
> Zomg it works!

bit off topic but can I ask how you got the cpu & ram meters on the right side of your screen?

---

### Post by swoll1980 on 2009-07-08
> **Closed_Port said:**
> Try to update. I did when I saw this here and with the latest build it's working.

OK the youtube videos are working, but the ones at [espn.com]("espn.go.com/video/clip?id=4313176") are audio only.

---

### Post by Giant Speck on 2009-07-08
> **sdlynx said:**
> bit off topic but can I ask how you got the cpu & ram meters on the right side of your screen?

That would be conky.  Give me a little while and I'll try to post it in the conky thread.

---

### Post by Closed_Port on 2009-07-08
> **swoll1980 said:**
> OK the youtube videos are working, but the ones at [espn.com]("espn.go.com/video/clip?id=4313176") are audio only.
Same here.

---

### Post by sdlynx on 2009-07-08
> **Giant Speck said:**
> That would be conky.  Give me a little while and I'll try to post it in the conky thread.

ok thanks, when I tried to use conky it made it's own window and didn't look very good unlike yours

---

### Post by Vadi on 2009-07-08
Good progress. I know a person who was needing that as the last resort (even with ff 3.5 fixing their crap linux js performance, chrome, in my benchmarks, is so far ahead still).

---

### Post by swoll1980 on 2009-07-08
> **sdlynx said:**
> ok thanks, when I tried to use conky it made it's own window and didn't look very good unlike yours

You you have to replace your .conkrc file in your home folder with one of the ones in the conky thread.

---

### Post by hanzomon4 on 2009-07-08
> **Giant Speck said:**
> Zomg it works!

Theme details?

---

### Post by moster on 2009-07-08
> **swoll1980 said:**
> OK the youtube videos are working, but the ones at [espn.com]("espn.go.com/video/clip?id=4313176") are audio only.

Go and click update now manually. I have video too, and with version I downloaded 12 hours before no.

---

### Post by sdowney717 on 2009-07-08
interesting, I tried the link command and now I get audio but no video. The video field is empty.

---

### Post by swoll1980 on 2009-07-08
> **moster said:**
> Go and click update now manually. I have video too, and with version I downloaded 12 hours before no.

I just installed the daily build like 3 hours ago.

---

### Post by swoll1980 on 2009-07-08
> **hanzomon4 said:**
> Theme details?

I want his wallpaper

---

### Post by sdowney717 on 2009-07-08
well I just did a new manual install of the latest chromium and still only get audio and no video on youtube.

---

### Post by sdlynx on 2009-07-08
> **swoll1980 said:**
> You you have to replace your .conkrc file in your home folder with one of the ones in the conky thread.

yeah I figured it out thanks

---

### Post by Vrekk on 2009-07-08
Dang it works pretty well :D Go Chromium team

---

### Post by sertse on 2009-07-08
Works, nice work Speck :P (why would you be randomly copy plugins to the plugin folder on this random day ;) )

---

### Post by Dougie187 on 2009-07-08
That's cool that it works. I just have to figure what to link to with 64 bit flash installed.

---

### Post by flattop1 on 2009-07-08
Thanks ,
that works great

---

### Post by Tristam Green on 2009-07-08
Strange, I've installed the most recent release in the PPA, and used Speck's steps outlined in his post on the first page, and only sound works properly right now.

---

### Post by sdowney717 on 2009-07-08
It does not work for me. Sound only.
Anyone know why?

Maybe I should uninstall chromium and reinstall.

---

### Post by sertse on 2009-07-08
Speck's steps assume you have the flashplayer.so in that folder, the command is to symlink it to the chromium plugins' folder. 

Make sure your flashplayer.so is actually in the folder, otherwise adjust the command to symlink from your folder.

Mine for example was in /usr/lib/flashplugin-nonfree/libflashplayer.so - BUT this is on debian, not ubuntu so I don't know if it applies to you.

---

### Post by Zorael on 2009-07-08
I can't decide which browser to stick with. I wish Firefox just wasn't so sluggish, and I need something fairly fast to compensate for this netbook being underpowered. And now I don't mean time-to-render-page, but in responsiveness, refresh rate, etc. Firefox *noticeably* lags behind when scrolling down on these forums, not to mention more javascript-heavy sites like gmail. And managing the window in genreal is just slower than any Qt browser I have available. Konqueror, sadly, is still using KHTML (so not an option), and Arora is still very early in development.

So far this Chromium alpha is great, especially now if Flash support starts trickling in, but I still need a flash blocker to go with that and some general adblock features. Ooh, and a chromium-qt flavor would be darling. And some akonadi and nepomuk awareness.

---

### Post by sdowney717 on 2009-07-08
uploaded an image of my file search for flashplugin.
how about a link to the one in /etc/alternatives?

---

### Post by DeadSuperHero on 2009-07-08
> **BlackRoijaX said:**
> I like Google but Chrome just feels too lightweight compared with Firefox.

Because you're more comfortable with slow and heavy, amirite?

---

### Post by JillSwift on 2009-07-08
I still only get sound. :(

---

### Post by Dougie187 on 2009-07-09
> **sdowney717 said:**
> uploaded an image of my file search for flashplugin.
how about a link to the one in /etc/alternatives?

I don't think that's going to work. What version of flash do you have installed?

---

### Post by sertse on 2009-07-09
> **sdowney717 said:**
> uploaded an image of my file search for flashplugin.
how about a link to the one in /etc/alternatives?

Try one of the flashplugin-alternative.so in your screenshot, using Speck's steps.

---

### Post by lovinglinux on 2009-07-09
It works for me, but what I think is interesting is that flash delivers the same crappy experience on Chromium, Firefox, Opera or whatever browser you can find.

I was wondering maybe Chromium would make some difference, but no. CPU usage raises to 45% when viewing a YouTube video embedded on Firefox or Chromium, while it drops to 9% when playing locally with gnome-mplayer or vlc. It's a huge difference.

Just for comparison, Chromium scores 1620 on Peacekeeper benchmarks on my machine, while Firefox 3.5 compiled with PGO and processor optimization flags scores 1110 and Opera 10 only 870.

---

### Post by Zorael on 2009-07-09
> **sdowney717 said:**
> uploaded an image of my file search for flashplugin.
how about a link to the one in /etc/alternatives?
Technically the correct one to link to is the one in /etc/alternatives. In case you install several plugins that provide Flash support (like Gnash), the only thing you need to change is where that /etc/alternatives symlink points towards. If you look at the plugin in /usr/lib/firefox/plugins, you'll see that it is actually a link to that very same /etc/alternatives link.

The *real* plugin binary is at **/usr/lib/flashplugin-installer/libflashplayer.so** (on a 32-bit installation via the flashplugin-nonfree package), but by making symlinks in the plugin directories to symlinks in /etc/alternatives, you only need to reroute those /etc/alternatives symlinks to control which Flash a browser uses. There are user-specific alternatives too, so you wouldn't even need root access to change it on a user basis.

```
/usr/lib/**mozilla**/plugins/flashplugin-alternative.so        \
/usr/lib/**firefox**/plugins/flashplugin-alternative.so         \
/usr/lib/**iceweasel**/plugins/flashplugin-alternative.so        } >> /etc/alternatives/*flashplugin >> /usr/lib/flashplugin-installer/libflashplayer.so
/usr/lib/**iceape**/plugins/flashplugin-alternative.so          /
/usr/lib/***randombrowser***/plugins/flashplugin-alternative.so  /
```

```
$ sudo update-alternatives --config **mozilla**-flashplugin
$ sudo update-alternatives --config **firefox**-flashplugin
$ sudo update-alternatives --config **iceweasel**-flashplugin
$ sudo update-alternatives --config **iceape**-flashplugin
$ sudo update-alternatives --config ***randombrowser***-flashplugin
```
Omit sudo to make it a user-specific setting.

Just to defeat the purpose, it gets a bit more confusing as any given browser will import plugins from other plugin directories than "its own"; Firefox won't just import from /usr/lib/firefox/plugins, but also from /usr/lib/**mozilla**/plugins, /usr/lib/**firefox-addons**/plugins, /usr/lib/**firefox-*version***/plugins, etc.

Obviously so far there isn't a **chromium-browser**-flashplugin alternative set up.

---

### Post by pixideps on 2009-07-09
> **Giant Speck said:**
> I entered the following commands in a terminal a few days ago:

```
cd /usr/lib/chromium-browser/plugins
sudo ln -s /usr/lib/firefox/plugins/flashplugin-alternative.so
```

Until today's update, only sound was working, but now sound and video are working.

The only thing that saddens me, though, is that Pandora doesn't seem to want to load all the way.  :(
Great thanx a lot

---

### Post by pt123 on 2009-07-09
with Google's new Chrome OS they are sure to work with Adobe to improve the performance of Flash on Linux

---

### Post by sdowney717 on 2009-07-09
created a link but now pages with flash stop responding and wont even load. It waits for a while and then asks me do I want to kill the page.
I am using the lates adobe flash in the repos.

scott@scott-desktop:/usr/lib/chromium-browser/plugins$ sudo ln -s /etc/alternatives/flashplugin-alternative.so
[sudo] password for scott: 
ln: creating symbolic link `./flashplugin-alternative.so': File exists
scott@scott-desktop:/usr/lib/chromium-browser/plugins$

---

### Post by sdowney717 on 2009-07-09
I rebooted and now the page loads again only with audio, still no video flash. 

just tried the configure option and it says nothing to do.
scott@scott-desktop:~$ sudo update-alternatives --config mozilla-flashplugin
[sudo] password for scott: 

There is only 1 program which provides mozilla-flashplugin
(/usr/lib/flashplugin-installer/libflashplayer.so). Nothing to configure.
scott@scott-desktop:~$ 



My machine is a 2.4ghz dell EVO with 1gb ram and 200gb drive and for the most part runs linux just fine.

---

### Post by sdowney717 on 2009-07-09
ok it is working!
I just did another manual update. I had done one yesterday after people posted how it was working with flash. the about page still shows the same version number.

---

### Post by sdowney717 on 2009-07-09
ok, it is working on youtube but not on CNN video, sound only.

[http://www.cnn.com/video/](http://www.cnn.com/video/)

can any of you check to see?

---

### Post by sdowney717 on 2009-07-09
that was short, chromium has completely died. I was watching a youtube and right clicked the p[layer, got the flash about screen and then HARD LOCK, whole computer locked up. So I pulled plug and restarted. Now chromium wont start up anymore.

scott@scott-desktop:~$ chromium-browser

[6909:6909:1697561880:FATAL:/build/buildd/chromium-browser-3.0.193.0~svn20090708r20142/build-tree/src/chrome/browser/zygote_host_linux.cc(63)] The SUID sandbox helper binary was found, but is not configured correctly. Rather than run without sandboxing I'm aborting now. You need to make sure that /usr/lib/chromium-browser/chromium-browser-sandbox is mode 4755 and that /var/run/chrome-sandbox exists
Trace/breakpoint trap
scott@scott-desktop:~$

---

### Post by sdowney717 on 2009-07-09
did a synaptic reinstall and it is worrking again, but I better not right click the adobe plugin window.

---

### Post by Xoanan on 2009-07-09
It works for me so far!
:popcorn:

---

### Post by sertse on 2009-07-09
You really have to post *6* times in a row?

Chromium is alpha, there are quirks, that it's working at all is impressive. That it's not is not worth posting about. It's not meant to work yet afterall.

I almost wish it didn't get told out, if user are going to react this way....

---

### Post by sdowney717 on 2009-07-09
so far so good the last few minutes it has not crashed.  Will keep you posted on if it does anything wrong.

---

### Post by sdowney717 on 2009-07-09
guess what mostly works except going to full screen video, the player stopped responding and I had to kill it. but my system is ATI x1300 using the free drivers and it likely just cant handle it

---

### Post by sdowney717 on 2009-07-09
Google is an ADVERTISING company. they make money on WEB ADDS.
Do you really think they want to create an ADD BLOCKER for chromium or the new chrome OS?
I think as it will be open source, that someone else will have to program the feature. Seeing they might even consider the add viewing as a fundamental part of the process of marketing and subsidizing  the OS into netbooks, etc... for free, they might even somehow sabotage add blocking or make it just very difficult to implement.

---

### Post by sdowney717 on 2009-07-09
chromium with flash plugin linked is definitely buggy. I just went to ebay and the page cant finish loading. before the link it was fine. I think i will just unlink it for now.

update another fatal crash, this flash on chrome is definitely not ready. 
I simply did a reboot and then tried to restart chromium

scott@scott-desktop:/usr/lib/chromium-browser/plugins$ chromium-browser
[6215:6215:197025969:FATAL:/build/buildd/chromium-browser-3.0.193.0~svn20090708r20142/build-tree/src/chrome/browser/zygote_host_linux.cc(63)] The SUID sandbox helper binary was found, but is not configured correctly. Rather than run without sandboxing I'm aborting now. You need to make sure that /usr/lib/chromium-browser/chromium-browser-sandbox is mode 4755 and that /var/run/chrome-sandbox exists
Trace/breakpoint trap
scott@scott-desktop:/usr/lib/chromium-browser/plugins$

---

### Post by swoll1980 on 2009-07-09
How does a browser crash bring down a whole system? There's something really wrong with that.

---

### Post by Johnsie on 2009-07-09
I got it working. Good start anyway but still very buggy with the flash plugin. How do I deactivate the flash plugin? 

BTW Google are going to be working with adobe on thier OS so hopeully things will improve.

---

### Post by ubudog on 2009-07-09
> **BlackRoijaX said:**
> Am I the only person who doesn't care about Google Chrome? I like Google but Chrome just feels too lightweight compared with Firefox.

Yes I agree but in a year or so it should get better.

---

### Post by sdowney717 on 2009-07-09
To deactivate the plugin all I did was navigate to the chrome plugin folder and delete the link. And then I did a reinstall of chromium. You dont loose anything. Or perhaps you can do the unlink command.

---

### Post by sdowney717 on 2009-07-09
"How does a browser crash bring down a whole system? There's something really wrong with that."

I agree truly! Not a single crash or problem, everything perfect without the flash enabled in chromium. Flash is so buggy, but whatever it does to me, my whole sytem becomes unresponsive. Sometimes it slowly locks up, browser windows stop responding, one time the entire desktop turned BLACK! other times total hard lock.

---

### Post by Sublime Porte on 2009-07-10
> I like Google but Chrome just feels too lightweight compared with Firefox.

It is lightweight, and that's one of it's major advantages. I use it as a quick browser to open if I just wanna quickly check something. Since I usually have about 50 tabs saved per session in Firefox, I often don't wanna wait for them to all load just to check a quick page. I used to keep a second lightweight browser like Kazehakase or Netsurf or an Xulrunner 'simple-browser' around for this, but Chromium is much better.

---

### Post by Danbo19 on 2009-07-10
When I was still using windows I loved chrome for its speed. Although now that I am forced to use firefox I have fallen in love with all the add-ons that I inexplicably didn't know about before. I'll be torn between the two when chrome is officially released for Linux.

---

### Post by gradinaruvasile on 2009-07-10
I experimented with the flash thing using the auto build version from here:

[]("http://build.chromium.org/buildbot/snapshots/chromium-rel-linux/")

 I linked the whole /usr/lib/mozilla/plugins/ folder to /chrome-linux/plugins 
(note that this is a version that comes without plugins folder and different directory names, u just unpack wherewer u want and execute the chrome executable from the folder - it has a fast development cycle too, dozen or so updates/day). 

I could use the quick time plugin to view an axis 210a camera which has mpeg4(quicktime) output. Funny i could hardly use this plugin in firefox...

If some1 interested, i attached a little script that downloads and installs/upgrades (and creates the plugin folder links) the chromium dev version from that site.

Update:

The totem plugin works best as i saw - can play embedded quicktime videos too from the apple site.

---

### Post by mister_k81 on 2009-07-10
> **sdowney717 said:**
> chromium with flash plugin linked is definitely buggy. I just went to ebay and the page cant finish loading. before the link it was fine. I think i will just unlink it for now.

update another fatal crash, this flash on chrome is definitely not ready. 
I simply did a reboot and then tried to restart chromium

scott@scott-desktop:/usr/lib/chromium-browser/plugins$ chromium-browser
[6215:6215:197025969:FATAL:/build/buildd/chromium-browser-3.0.193.0~svn20090708r20142/build-tree/src/chrome/browser/zygote_host_linux.cc(63)] The SUID sandbox helper binary was found, but is not configured correctly. Rather than run without sandboxing I'm aborting now. You need to make sure that /usr/lib/chromium-browser/chromium-browser-sandbox is mode 4755 and that /var/run/chrome-sandbox exists
Trace/breakpoint trap
scott@scott-desktop:/usr/lib/chromium-browser/plugins$

I had the same problem with the latest build as well. But it can be solved it with this simple command: 
 
```
sudo mkdir /var/run/chrome-sandbox
``` 

More info about this issue here: [http://code.google.com/p/chromium/issues/detail?id=16363](http://code.google.com/p/chromium/issues/detail?id=16363)

---

### Post by macabro22 on 2009-07-11
thanks Mr_k 81 

That worked for me.

---

### Post by sdowney717 on 2009-07-11
Thanks, gradinaruvasile the shell script works fine.
for movie trailer I have to actually click the control to show the video, otherwise it plays with a black screen.
why do cnn videos work only with sound? youtube is ok.

Also, i will likely not use chrome without an addblocker. the firefox addblocker will block cnn video adds.

---

### Post by RTrev on 2009-07-11
With or without the link, when I go to Youtube via Chromium Youtube always tells me that I need to enable Javascript.  It makes no mention of Flash.  Does this suggest anything?  I haven't seen anyone else report this.  I'm on Jaunty 64-bit if it matters.

---

### Post by siimo on 2009-07-12
How to hide Window Manager buttons in Chromium? or is that a Chrome only feature? (like in windows where windows standard minimize, maximize, close bar is hidden and Chrome shows its own). 

I have seen some screenshots of the Linux GTK version doing the same (not wine version) but have not been able to find the option in Chromium.

---

### Post by Closed_Port on 2009-07-12
> **siimo said:**
> How to hide Window Manager buttons in Chromium? or is that a Chrome only feature? (like in windows where windows standard minimize, maximize, close bar is hidden and Chrome shows its own). 

I have seen some screenshots of the Linux GTK version doing the same (not wine version) but have not been able to find the option in Chromium.
Just right click on the blue bar next to the tabs and deselect "use system titlebar and borders".

---

### Post by siimo on 2009-07-12
Nice, thanks for the heads up.

---

### Post by Giant Speck on 2009-07-12
> **Closed_Port said:**
> Just right click on the blue bar next to the tabs and deselect "use system titlebar and borders".

Oh, that is so cool!

---

### Post by parthbakshi on 2009-07-12
hey..

thanks for the tip....;)

---

### Post by Vadi on 2009-07-12
Hm... personally, I find my native window handles to look much better than windows xp-like.

---

### Post by Giant Speck on 2009-07-12
> **Vadi said:**
> Hm... personally, I find my native window handles to look much better than windows xp-like.

My native window border doesn't really look good with it, considering my overall desktop theme is brown and Chromium is blue.

And Chromium is still really bad at emulating my dark Gnome theme.  :mad:

---

### Post by joske on 2009-07-15
worked yesterday, with today's update no more ??

---

### Post by Closed_Port on 2009-07-15
> **joske said:**
> worked yesterday, with today's update no more ??
Same problem here. Flash doesn't work after the latest update.

---

### Post by rileinc on 2009-07-15
does it work if you drop libflashplayer.so in /usr/lib/chromium-browser/plugins?

---

### Post by JillSwift on 2009-07-15
Flash died altogether on today's update, for me. :cry: Waaaahhhh!

---

### Post by darco on 2009-07-15
> **JillSwift said:**
> Flash died altogether on today's update, for me. :cry: Waaaahhhh!

heh,,,,thought it was just me!

darco

---

### Post by swoll1980 on 2009-07-15
> **rileinc said:**
> does it work if you drop libflashplayer.so in /usr/lib/chromium-browser/plugins?

No it doesn't work. When I go to a site with flash video, it just shows the install flash logo.

---

### Post by colorprint on 2009-07-15
> **RTrev said:**
> With or without the link, when I go to Youtube via Chromium Youtube always tells me that I need to enable Javascript.  It makes no mention of Flash.  Does this suggest anything?  I haven't seen anyone else report this.  I'm on Jaunty 64-bit if it matters.

The Chromium is 32bit app, so it needs 32bit plugins :(

---

### Post by Giant Speck on 2009-07-15
[noparse]about:plugins[/noparse]

It shows that no plugins are installed, even though the plugins are obviously in the plugins folder.  Damn it.

---

### Post by sefs on 2009-07-15
Hi does Chromium have the V8 Javascript engine as well?

Since I can install this right now on my system, do I need to be waiting around for google chrome ... or will the two be on parity.

Thanks.

---

### Post by mister_k81 on 2009-07-15
> **darco said:**
> heh,,,,thought it was just me!

darco


Same here too, flash doesn't work for me in the latest daily build. I wonder why it was disabled/ removed?

---

### Post by Vadi on 2009-07-16
They had another regression of the text randomly dissapearing from a page too. So this probably wasn't removed.

---

### Post by darco on 2009-07-16
At least we get daily updates to the browser....that is nice.
Todays update , no fix tho :(

darco

---

### Post by birnam on 2009-07-16
Flash died for me today too -- or so I thought. I played around a bit and found that using the " --enable-plugins " flag enabled it!

I'm currently using:

```
chromium-browser --enable-greasemonkey --enable-user-scripts --enable-extensions --enable-plugins
```

---

### Post by JillSwift on 2009-07-16
> **birnam said:**
> Flash died for me today too -- or so I thought. I played around a bit and found that using the " --enable-plugins " flag enabled it!

I'm currently using:

```
chromium-browser --enable-greasemonkey --enable-user-scripts --enable-extensions --enable-plugins
```
[SIZE=4]***D E W D !***[/SIZE]

Thanks a ton! I hand't thought to try this. I get flash now, and *it has video**! Rah!







[SIZE=1]*On YouTube and Google video. Nothing on Veoh, cbs.com[/SIZE], audio only on metacafe...

---

### Post by Closed_Port on 2009-07-16
> **birnam said:**
> Flash died for me today too -- or so I thought. I played around a bit and found that using the " --enable-plugins " flag enabled it!

I'm currently using:

```
chromium-browser --enable-greasemonkey --enable-user-scripts --enable-extensions --enable-plugins
```
Hey, thanks a lot, --enable-plugins solved it.

---

### Post by Vrekk on 2009-07-16
> **birnam said:**
> Flash died for me today too -- or so I thought. I played around a bit and found that using the " --enable-plugins " flag enabled it!

I'm currently using:

```
chromium-browser --enable-greasemonkey --enable-user-scripts --enable-extensions --enable-plugins
```

good to have flash back, but has anyone else noticed that todays update made Chromium REALLY unstable?

---

### Post by darco on 2009-07-16
> **Closed_Port said:**
> Hey, thanks a lot, --enable-plugins solved it.

That line must be new, wasnt there before!...flash works now again..thxs

darco

---

### Post by ubudog on 2009-07-16
> **Giant Speck said:**
> I entered the following commands in a terminal a few days ago:

```
cd /usr/lib/chromium-browser/plugins
sudo ln -s /usr/lib/firefox/plugins/flashplugin-alternative.so
```

Until today's update, only sound was working, but now sound and video are working.

The only thing that saddens me, though, is that Pandora doesn't seem to want to load all the way.  :(

That didn't work for me.  How do I get it working?

---

### Post by ubudog on 2009-07-16
> **birnam said:**
> Flash died for me today too -- or so I thought. I played around a bit and found that using the " --enable-plugins " flag enabled it!

I'm currently using:

```
chromium-browser --enable-greasemonkey --enable-user-scripts --enable-extensions --enable-plugins
```

Nevermind about my other post.  This worked for me too.

---

### Post by crjackson on 2009-07-16
> **lovinglinux said:**
> It works for me, but what I think is interesting is that flash delivers the same crappy experience on Chromium, Firefox, Opera or whatever browser you can find.

I was wondering maybe Chromium would make some difference, but no. CPU usage raises to 45% when viewing a YouTube video embedded on Firefox or Chromium, while it drops to 9% when playing locally with gnome-mplayer or vlc. It's a huge difference.

Just for comparison, Chromium scores 1620 on Peacekeeper benchmarks on my machine, while Firefox 3.5 compiled with PGO and processor optimization flags scores 1110 and Opera 10 only 870.

Same experience here.  Adobe Flash for Linux SUX!

---

### Post by ubudog on 2009-07-16
> **crjackson said:**
> Same experience here.  Adobe Flash for Linux SUX!

Yes you are right.

---

### Post by lindenbranch on 2009-07-17
I just wanted to say thanks to everyone for helping me get flash to work on chromium, especially birnam.  I was wondering why it wasn't working until he posted  --enable-plugins.  Thanks.

---

### Post by hyperdude111 on 2009-07-17
I still cant get this to work. Can someone please help. It might make a difference that I'm using the 64bit version under ia32 libs.

Thanks

---

### Post by dawnlove on 2009-07-17
when I used the enable plug-in script in terminal in my 64b xubuntu 9.04 I got back this

(chromium-browser:4495): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64


anyone know how to fix this or just wait for updates?

---

### Post by darco on 2009-07-18
> **dawnlove said:**
> when I used the enable plug-in script in terminal in my 64b xubuntu 9.04 I got back this

(chromium-browser:4495): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64


anyone know how to fix this or just wait for updates?

I get this too because we are using x64 libraries and Chromium is x32...so we are using the wrong "class" (64)
but so what, Chromium works almost perfect for me, AdSweep,Flash,Java is all I need..I love the constant updates!

darco

---

### Post by pikaia on 2009-07-19
Ok.  Installed Chromium no problem, but I can't get flash working to save my life.  I've tried copy and pasting the .so into the plugin folder, I've ```
sudo ln -s /usr/lib/firefox/plugins/flashplugin-alternative.so.
```  And nothing.  I've tried the --enable-plugins and still nothing.  I'm using Hardy 64.  Flash works on both Firefox and Opera.  

Any thoughts?  Thanks.

---

### Post by birnam on 2009-07-20
> **pikaia said:**
> Ok.  Installed Chromium no problem, but I can't get flash working to save my life.  I've tried copy and pasting the .so into the plugin folder, I've ```
sudo ln -s /usr/lib/firefox/plugins/flashplugin-alternative.so.
```  And nothing.  I've tried the --enable-plugins and still nothing.  I'm using Hardy 64.  Flash works on both Firefox and Opera.  

Any thoughts?  Thanks.


I'm not sure what the flashplugin-alternative.so is. When I installed flash, I downloaded the .tar.gz version of the Linux installer from the Adobe website -- this is important because it is the 32bit version. The file in that is libflashplayer.so. That might be the issue.

---

### Post by martini1179 on 2009-07-20
[SIZE=2]I'm running Jaunty 64 with the 64-bit flash plugin, installed and working in Firefox and Opera with the workaround found in this thread: [http://ubuntuforums.org/showthread.php?t=1081964](http://ubuntuforums.org/showthread.php?t=1081964)

I've entered the terminal commands on the first page of this thread, I've created an icon with the --enable-plugins option, and yet Flash doesn't work. I don't want to go back to the 32-bit plugin because it doesn't work very well for me and a lot of others.

 How do I get the 64-bit plugin to work with Chromium?[/SIZE]

---

### Post by raronson on 2009-07-20
> **BlackRoijaX said:**
> Am I the only person who doesn't care about Google Chrome? I like Google but Chrome just feels too lightweight compared with Firefox.

There's not much to be impressed with now.  It's not really about what it is, but where it's all going...

---

### Post by birnam on 2009-07-21
> **martini1179 said:**
> [SIZE=2]
 How do I get the 64-bit plugin to work with Chromium?[/SIZE]

As far as I can tell, you don't. Chromium is only 32 bit, so it can only load 32 bit libraries.

I am still running the 64 bit flash player on all of my other browsers, and it's the one that's officially "installed" on my system.

When you extract the 32 bit libflashplayer.so from the .tar.gz archive you don't need to place it where the system/other browsers can use it, only in the chromium plugins directory within the chromium installation. This was /usr/lib/chromium-browser/plugins/ for me.

---

### Post by pikaia on 2009-07-21
> **birnam said:**
> I'm not sure what the flashplugin-alternative.so is. When I installed flash, I downloaded the .tar.gz version of the Linux installer from the Adobe website -- this is important because it is the 32bit version. The file in that is libflashplayer.so. That might be the issue.

I actually tried both.  I started with the flash 10 (libflashplayer.so) and that didn't work, following all instructions on the first page.  Then I tried it as described after first removing this and installing the alternative one from synaptic.  Neither works.

I just get the message that I need to install the plugin.

I'll keep trying, but I'm not holding out much hope.  Has this been tested in Hardy?  Which is what I'm using... everyone seems to be using Jaunty.

My problem could also be the 64-bit version of Flash... I'll dig a bit deeper.

---

### Post by darco on 2009-07-21
birnam is right....I have an x64 bit system w/Flash 10 installed and all is well. I did not want to whack a perfectly good system so I d/l the Flash x32 libflashplayer.so and extracted to the chromium/plugin folder and all is good. 

darco

---

### Post by pikaia on 2009-07-22
Well, after trying again I extracted to the plugins folder and now I get the black box but no flash video playing.  So I guess its progress.  Any ideas where to go from here?

Thanks.

---

### Post by darco on 2009-07-22
> **pikaia said:**
> Well, after trying again I extracted to the plugins folder and now I get the black box but no flash video playing.  So I guess its progress.  Any ideas where to go from here?

Thanks.

You are running this command right? 
chromium-browser --enable-greasemonkey --enable-user-scripts --enable-extensions --enable-plugins



good luck
darco

---

### Post by martini1179 on 2009-07-23
> **birnam said:**
> As far as I can tell, you don't. Chromium is only 32 bit, so it can only load 32 bit libraries.

I am still running the 64 bit flash player on all of my other browsers, and it's the one that's officially "installed" on my system.

When you extract the 32 bit libflashplayer.so from the .tar.gz archive you don't need to place it where the system/other browsers can use it, only in the chromium plugins directory within the chromium installation. This was /usr/lib/chromium-browser/plugins/ for me.

Thanks for the tip. I wasn't sure if I could have two Flash plugins running on once system, but it works. 

I was able to get Flash to work on Chromium by downloading the 32-bit Flash .tar.gz file and then moving the 32-bit libflashplayer.so from the desktop (where I originally saved it) by typing 

```
sudo mv Desktop/libflashplayer.so /usr/lib/chromium-browser/plugins/
```Just start/restart Chromium and viola!

Oh, and make sure that you start Chromium with --enable-plugins.

---

### Post by akshunj on 2009-07-24
The newest build doesn't require any moving or copying of plugins.  It will detect and load them from Firefox's plugin directories.  My Chromium plugin directory is empty, but all plugins are loaded including Flash, Java, Gecko Media Player, etc.

---

### Post by Vrekk on 2009-07-24
Mine wont start at all with todays update.  this is what i get from the terminal 
```

brett@brett-desktop:~$ chromium-browser 
exec: 87: -a: not found
```

---

### Post by themusicalduck on 2009-07-24
> **Vrekk said:**
> Mine wont start at all with todays update.  this is what i get from the terminal 
```

brett@brett-desktop:~$ chromium-browser 
exec: 87: -a: not found
```

I got this too. Was excited to try out flash as well.

---

### Post by darco on 2009-07-24
> **Vrekk said:**
> Mine wont start at all with todays update.  this is what i get from the terminal 
```

brett@brett-desktop:~$ chromium-browser 
exec: 87: -a: not found
```

same here...just navigate to usr/lib and start chromium from there

darco

---

### Post by darco on 2009-07-24
> **akshunj said:**
> The newest build doesn't require any moving or copying of plugins.  It will detect and load them from Firefox's plugin directories.  My Chromium plugin directory is empty, but all plugins are loaded including Flash, Java, Gecko Media Player, etc.

thats not good if you have a x64 bit system...arrgh

darco

---

### Post by martini1179 on 2009-07-24
> **themusicalduck said:**
> I got this too. Was excited to try out flash as well.

The latest Chromium daily alpha works, after the previous one failed to load.

---

### Post by sertse on 2009-07-24
Off topic, but is it the case that removing a item from speed dial (clicking the "x") means it'll never ever appear on it again. Is it a feature?

I know you can Undo it at the time, but if you didn't undo it then, it appears there is no way of making the item appear on speed dial again..

---

### Post by Ric_NYC on 2009-07-25
A little off-topic.:

Install the latest Chromium version!!!
The fonts have been fixed... Now they look perfect.

Running flash+good looking fonts... :D

I didn't find any bugs yet... Maybe it is ready to be the default browser after those improvements.

---

### Post by castrojo on 2009-07-25
Here's a tip from fta:

In /etc/chromium-browser/default you can add flags so that you don't have to go change your launchers and stuff:

CHROMIUM_FLAGS="--enable-plugins"

is what I put in mine.

---

### Post by Ric_NYC on 2009-07-25
> **whiprush said:**
> Here's a tip from fta:

In /etc/chromium-browser/default you can add flags so that you don't have to go change your launchers and stuff:

CHROMIUM_FLAGS="--enable-plugins"

is what I put in mine.

Thanks!

---

### Post by bluebyt on 2009-07-25
I like it but it doesn't work well at Deviantart
[http://www.deviantart.com/]("http://www.deviantart.com/")

---

### Post by Vrekk on 2009-07-25
> **bluebyt said:**
> I like it but it doesn't work well at Deviantart
[http://www.deviantart.com/]("http://www.deviantart.com/")

works fine for me.  What dosen't work are ftps

---

### Post by martini1179 on 2009-07-25
> **Ric_NYC said:**
> I didn't find any bugs yet... Maybe it is ready to be the default browser after those improvements.

Sounds like someone hasn't tried tearing tabs away into a separate window and dragging them back. Or logging into Gmail ;)

---

### Post by Giant Speck on 2009-07-26
The fonts do look nice.  They're not perfect, but they look a lot better than they used to.

Also, Pandora still won't load.  And I wish Java would work.

---

### Post by Jay_Bee on 2009-07-28
It's lightning fast! And it's almost ready :)

---

### Post by gnomeuser on 2009-07-28
> **Jay_Bee said:**
> It's lightning fast! And it's almost ready :)

I don't know about everyone else, but I have switched fulltime to Chrome (using the official debs not the ppa, just because) and on my EeePC 1002HA it is so much more pleasant both in it's interface which is more elegant, slim and to me enjoyable. Additionally it is much faster than what is currently presented by Firefox in pretty much every respect. 

I'm not looking back, this is the future.

---

### Post by darco on 2009-07-28
I am a big fan too!....cpu usage a little high tho..flash still works with an x64 OS...
Have you tried Opera 10 beta? Really really nice...I havent used FF in a while now...

darco

---

### Post by itreius on 2009-07-31
Not exactly flash related, but this is the last updated Chrome thread, so here goes

3.0.196.0 changelog contains the following line

[LIST]
[*]Google Chrome now respects the system font hinting/antialiasing setting.
[/LIST]

/cheer

Edit: Hm, I see some people were already commenting on fonts a couple of days ago... Guess I'm late.

---

### Post by Giant Speck on 2009-08-02
HELL YEAH!

Pandora finally works on Chromium!

Now if only Java worked...

---

### Post by sertse on 2009-08-02
I've since filed a report for my issue. (Yea, I know it's offtopic, but this is only currently active Chromium topic right now)

[http://code.google.com/p/chromium/issues/detail?id=18214](http://code.google.com/p/chromium/issues/detail?id=18214)

Surely I'm not the only one who's OCD about these things? ;)

---

### Post by Giant Speck on 2009-08-02
> **sertse said:**
> I've since filed a report for my issue. (Yea, I know it's offtopic, but this is only currently active Chromium topic right now)

[http://code.google.com/p/chromium/issues/detail?id=18214](http://code.google.com/p/chromium/issues/detail?id=18214)

Surely I'm not the only one who's OCD about these things? ;)

It's understandable.  It would be like me accidentally deleting the wrong person from my Facebook friends list and then not being given an option to re-add them as a friend.

---

### Post by xArv3nx on 2009-08-02
> **gnomeuser said:**
> I don't know about everyone else, but I have switched fulltime to Chrome (using the official debs not the ppa, just because) and on my EeePC 1002HA it is so much more pleasant both in it's interface which is more elegant, slim and to me enjoyable. Additionally it is much faster than what is currently presented by Firefox in pretty much every respect. 

I'm not looking back, this is the future.
I'm with you, buddy. I just switched full time to Chromium since all I need is flash.

we'll see how long it lasts :)

---

### Post by wersdaluv on 2009-08-04
Mine's weird. I made a correct flashplugin-alternative.so link. It worked without that, btw. I just had to "--enable-plugins".

Now, I have the right firefox flashplugin-alternative.so link and the "--enable-plugins" flag. Flash videos play without sound. Any idea?

---

### Post by Tulsapoke on 2009-08-09
I have a similar issue, zero sound at all on Chromium.  Flash seems to work but like everything else on Chromium it is also silent.  If the get everything working the thing is so fast that I could easily see using it as my daily browser.

---

### Post by darco on 2009-08-09
Are you on x64 OS?....If so, you need to d/l the x32 flashplayer and install it into the chromium/plugin folder and nowhere else. Delete any links found in that folder. If you are x32 OS, update to the latest Flashplayer 10 after removing the previous flash.

darco

---

