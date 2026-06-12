---
title: "Auto Update - snap vs flatpak"
date: 2023-02-01
forum: Ubuntu, Linux and OS Chat
---

### Post by Quarkrad on 2023-02-01
Running 20.04  I have two specific elderly neighbours I look after (pc wise) that essentially use ubuntu for web access and email.  One is elusively google based, doing everything via Chrome, and the other just firefox/thunderbird.  These ladies are both in their late 80's and do not like pop-ups or messages appearing on the screen.  (They come from Windows and use an ipad so they are use to things like updates being done for them). I'm thinking about them using snaps or flatpak, so updating is done 'in the background', without them knowing.  I appreciate there is a risk, re an update bringing their system down, but I'm willing to take that risk and sort their system out after the event (should it crash).  I've come to the conclusion(?) that at the moment snaps does provide auto upgrading of its apps without any notification or user involvement but flatpak doesn't.  It seems, to me, 99.9% of web searches is about turning off auto updating by various methods but *none/very little* confirming auto updating without *notification/user input* with the default install.  Is it the case that the default install of snaps will provide me with auto updating of its apps with no *notification/user input* where-as flatpak doesn't (there is a notification and the user has to initiate something)?  (As these ladies use minimal apps I am not concerned about the wasted disc space used by duplicating dependences).

---

### Post by Frogs Hair on 2023-02-01
As noted, flatpaks don't update with the system and require an update command. Some but not all  snaps do update with system, it depends on the platform and the provider of the package.


  > (They come from Windows and use an ipad so they are use to things like updates being done for them)  Are they switching to Linux ? 

[https://itsfoss.com/update-flatpak/](https://itsfoss.com/update-flatpak/)

---

### Post by TheFu on 2023-02-01
The one that is 100% browser based, needs a chromebook with her next PC upgrade.

The one using fat clients will be forced to use snap packages under Ubuntu 22.04, so there isn't much choice.  Snaps update without asking. There's no user interaction and they can break things, but end-users typically have only a minor inconvenience.  Servers and server admins find the auto-update of snap packages abominations, since a snap update will take down a critical service and may break it, so it doesn't come up.  With snaps, it is possible to schedule 1 day a week for the updates.  I have mine set to occur on Saturdays and that does seem to be working.  Unfortunately, I cannot specify a time for the updates on Saturday - so they run a little after midnight local time.  That means a service can be down until the following morning when I notice it.  A few days ago, that happened.  All my lxd containers were offline for about 8 hrs after lxd's snap package failed to upgrade cleanly.  Snap packages don't allow the most needed local overrides.  I find that offensive too, since the defaults are not to my liking.

I know nothing about flatpaks, except by default they are only used for end-user programs, not for servers, and they don't auto-update, unless you setup something to make that happen.  There are tools to accomplish flatpak updates.  Flatpaks allow local control and overrides.

BTW, google answers these questions with more authority.

---

### Post by SeijiSensei on 2023-02-01
When my snap of Firefox or Chromium needs to be updated, I get annoying messages in the notifications app all the time. Might not be the best choice if they hate popups.

---

### Post by Quarkrad on 2023-02-01
Yes - they are both running ubuntu 20.04.  Hmm... the snap of FF and Chromium not auto updating is the whole point of this potential change (especially google chrome).  There doesn't appear to be a snap of google chrome so it looks like I'm back to the drawing board.

---

### Post by TheFu on 2023-02-01
> **Quarkrad said:**
> Yes - they are both running ubuntu 20.04.  Hmm... the snap of FF and Chromium not auto updating is the whole point of this potential change (especially google chrome).  There doesn't appear to be a snap of google chrome so it looks like I'm back to the drawing board.

I'm always shocked when people choose to put software from a huge, global, advertising and tracking company on their computers. Shocked, I say!

Chromium, is the F/LOSS project that is very chrome-like. It comes as a snap package, even on 20.04.  It was the first snap that got my attention (made me unhappy), since snap packages aren't compatible with firejail.  I prefer to setup my own limitations for OS access for end users applications.  

I'm not hating on snaps just because they are snaps.  I dislike that control I had was taken away with no reasonable way to get it back within the Ubuntu ecosystem.  New is great. It might be better. I don't even mind that it is the default, provided there is away to opt out and have local control for things as important as which software is running on our systems and when it gets updated.

---

### Post by #&amp;thj^% on 2023-02-01
> **TheFu said:**
> I'm always shocked when people choose to put software from a huge, global, advertising and tracking company on their computers. Shocked, I say!
Right there with ya! ;)
> **TheFu said:**
> 
Chromium, is the F/LOSS project that is very chrome-like. It comes as a snap package, even on 20.04.  It was the first snap that got my attention (made me unhappy), since snap packages aren't compatible with firejail.  I prefer to setup my own limitations for OS access for end users applications.  

I'm not hating on snaps just because they are snaps.  I dislike that control I had was taken away with no reasonable way to get it back within the Ubuntu ecosystem.  New is great. It might be better. I don't even mind that it is the default, provided there is away to opt out and have local control for things as important as which software is running on our systems and when it gets updated.

How come when you write about the above you don't get any crap, when I discuss snaps, and my *personal* dislikes, I get hell for it:o
No answer needed, just a point of interest.....

---

### Post by #&amp;thj^% on 2023-02-01
> **Quarkrad said:**
> Running 20.04  I have two specific elderly neighbours I look after (pc wise) that essentially use ubuntu for web access and email.  One is elusively google based, doing everything via Chrome, and the other just firefox/thunderbird.  These ladies are both in their late 80's and do not like pop-ups or messages appearing on the screen.  (They come from Windows and use an ipad so they are use to things like updates being done for them). I'm thinking about them using snaps or flatpak, so updating is done 'in the background', without them knowing.  I appreciate there is a risk, re an update bringing their system down, but I'm willing to take that risk and sort their system out after the event (should it crash).  I've come to the conclusion(?) that at the moment snaps does provide auto upgrading of its apps without any notification or user involvement but flatpak doesn't.  It seems, to me, 99.9% of web searches is about turning off auto updating by various methods but *none/very little* confirming auto updating without *notification/user input* with the default install.  Is it the case that the default install of snaps will provide me with auto updating of its apps with no *notification/user input* where-as flatpak doesn't (there is a notification and the user has to initiate something)?  (As these ladies use minimal apps I am not concerned about the wasted disc space used by duplicating dependences).

Quarkrad have you thought about Topgrade? [https://itsfoss.com/topgrade/](https://itsfoss.com/topgrade/)
I run it on all my systems flawlessly. (Arch Red Hat, Suse, Debian testing) as an Alias.
Been using it for a spell now: [https://ubuntuforums.org/showthread.php?t=2481893&p=14124914#post14124914](https://ubuntuforums.org/showthread.php?t=2481893&p=14124914#post14124914)
Once installed correctly, your special ladies will love you for it. ;)

---

### Post by monkeybrain20122 on 2023-02-01
For the Firefox user. If you get rid of the snap and download the Firefox binary from Mozilla it upgrades automatically on restarting the browser. For first launch click firefox in the folder, make it the default then it will create a .desktop file in ~/.local/share/applications. From then on you can just click the launcher icon to start FF like you would do with firefox normally.

---

### Post by donald187 on 2023-02-01
> **Quarkrad said:**
>   \Is it the case that the default install of snaps will provide me with auto updating of its apps with no *notification/user input* where-as flatpak doesn't (there is a notification and the user has to initiate something)? 
I'm just a regular user but this has basically been my experience.  "Basically" because from time to time you do get a notification saying something like "Update of Firefox snap pending.  Close the application to avoid interruptions.  13 days remaining."  I got one this morning.  From reading the forums my understanding is that snaps do update automatically but they need the application to be closed.  If it is open you get the notification I just mentioned.  Now the easiest thing to do is to ignore it and just wait for the next automatic update to occur at which point hopefully Firefox will be closed.

[https://ubuntuforums.org/showthread.php?t=2479262&p=14112858#post14112858](https://ubuntuforums.org/showthread.php?t=2479262&p=14112858#post14112858)

I have not used Flatpak on Ubuntu but I did on Debian with the gnome desktop.  If you install the Flatpak plugin then Gnome Software is supposed include the Flatpak updates with the other updates (I did not try this personally but this is my understanding.  I can verify that Flatpak applications do get included in Gnome Software with the plugin installed.).  And yes, you get a notification that if you click on it will open Gnome Software and you can click the "install Updates" button or whatever it says.  (I have done this personally. i.e. without Flatpak.)   Here are the instructions for Ubuntu.

[https://flatpak.org/setup/Ubuntu](https://flatpak.org/setup/Ubuntu)

---

### Post by Quarkrad on 2023-02-02
1fallen:  Thank you - I am looking at Topgrade; in a vm.  I have yet to dive into it - just installed it.  Can it be run 'in the background' and not ask for a password (say it finds Chrome needs an update - can you config things so that Chrome is installed without entering your sudo password?).  I'm thinking of running Topgrade as a bash script at some point (shutdown or startup?).

---

### Post by grahammechanical on 2023-02-02
Regarding the snap version of Firefox, it will update automatically without requiring any user interaction. Once the notified time has expired Firefox will update as soon as the OS connects to the Internet. This is just like Ubuntu automatically checking for updates.

Software Updater is basically a GUI frontend for a script that runs a few commands such as apt update; apt upgrade and snap refresh. So, running Software Updater will automatically update installed snaps except applications like Firefox where the release of the updated snap version is under the control of the Mozilla developers and not the Ubuntu developers.

I will soon be 75 years old. I do not think it is a good thing to assume that elderly persons cannot learn new things and have to be shielded from stuff that makes life complicated.

Regards

---

### Post by BBQdave on 2023-02-02
> **grahammechanical said:**
> Software Updater is basically a GUI frontend for a script that runs a few commands such as apt update; apt upgrade and snap refresh. So, running Software Updater will automatically update installed snaps except applications like Firefox where the release of the updated snap version is under the control of the Mozilla developers and not the Ubuntu developers.

Thank you for this explanation. I've been away from Ubuntu for a few years, and am playing catch up - understanding how Ubuntu 22.04LTS updates system and applications. I'm getting an education in *snap* :)

---

### Post by Quarkrad on 2023-02-03
grahammechanial:  Apologies for the age ref - it was not relevant.  Actually, I'm nearer to 75 myself than the age I wish I was!  The issue is that these two people, like many others, are not, and have no interest, in computers.  They see them as complicated, bewildering, and as things to use rather than learn about, fix, tinker, play with, etc - I on the other hand see it as something to use, and as my Meccano Set, that I can play with and learn how to build new things.  I look after a number of neighbours machines and many of them got fed up with the virus attacks and down times of their Windows machines; so over time I have converted them to ubuntu/linux.  100% they are very happy.  Yesterday one of these ladies mentioned 'something about an update on Chrome' so I will have to pop round again despite repeatedly saying 'it's ok, just hit update/ok'.  Hence - if something like snap/flatpak could auto update Chrom in the background she would not have this worry about a message popping up.  (I have since found out that flatpak would be a disaster for Chrome because it gives a warning about an update and then a timer comes into action which eventually crashes Chrome and updates! [https://ubuntuforums.org/showthread.php?t=2479262](https://ubuntuforums.org/showthread.php?t=2479262)).

---

### Post by #&amp;thj^% on 2023-02-03
> **Quarkrad said:**
> 1fallen:  Thank you - I am looking at Topgrade; in a vm.  I have yet to dive into it - just installed it.  Can it be run 'in the background' and not ask for a password (say it finds Chrome needs an update - can you config things so that Chrome is installed without entering your sudo password?).  I'm thinking of running Topgrade as a bash script at some point (shutdown or startup?).

Well this is something I don't advise, but in this case you could have a look here: [https://linuxhandbook.com/sudo-without-password/](https://linuxhandbook.com/sudo-without-password/)
If you run into any problems installing "cargo-update" just post in the link I showed you:[https://ubuntuforums.org/showthread.php?t=2481893&p=14124914#post14124914](https://ubuntuforums.org/showthread.php?t=2481893&p=14124914#post14124914)
I will try to help if needed.

---

### Post by donald187 on 2023-02-03
> **Quarkrad said:**
> (I have since found out that flatpak would be a disaster for Chrome because it gives a warning about an update and then a timer comes into action which eventually crashes Chrome and updates! [https://ubuntuforums.org/showthread.php?t=2479262](https://ubuntuforums.org/showthread.php?t=2479262)).

Just to be clear, the timer seems to be 13 days according to the following link.  This is also my experience.  Unless your user leaves the browser open all the time I would think it would likely update before then since it tries to update 4 times a day.

[https://askubuntu.com/questions/1412140/how-to-solve-pending-update-of-firefox-snap-close-the-app-to-avoid-disruptio](https://askubuntu.com/questions/1412140/how-to-solve-pending-update-of-firefox-snap-close-the-app-to-avoid-disruptio)

Also there doesn't seem to be a snap of Chrome.  There is one of Chromium which is nearly the same but it's at least lacking the ability to sync history and bookmarks online with a Chrome app for phone.

---

### Post by Quarkrad on 2023-02-03
So ... is my thinking right(?)

[LIST]
[*]I install Chromium snap
[*]A message will pop up at some time saying there is an update
[*]The next time* the user powers down and then up again the app (Chromium will update itself)
[/LIST]


* If the user powers down/up daily then there is no problem because the 13 day rule is not relevant.

The user is running 20.04 - if I turn off all snap notifications then providing there is daily power down/up everything (in this case (mainly Chromium, but very occasionally firefox) everything gets updated.

---

### Post by DuckHook on 2023-02-04
> **donald187 said:**
> …there doesn't seem to be a snap of Chrome…
```
duckhook@Zeus:~$  snap find chrome
Name                   Version                 Publisher                  Notes    Summary
chromeos-themes        2020-01-18-25-g765be0e  gantonayde                 -        ChromeOS GTK Themes for GTK Snaps
chrome-log-beautifier  1.0.0                   arthursonzogni             -        An interactive terminal UI for analysing Chrome logs.
chromium               109.0.5414.119          canonical&#10003;                 -        Chromium web browser, open-source version of Chrome
postman                10.9.0                  postman-inc&#10003;               -        API Development Environment
polar-bookshelf        1.100.13                inputneuron                -        Polar Bookshelf - Manager for web, books, PDFs + notes
tizonia                0.22.0                  tizonia                    -        Cloud music from the Linux terminal
imagenes               2.0.459                 ubunturox104               -        An Electron-based Google Photos client
skrifa                 0.2.6                   hyuchia                    -        A simple word processor built with web technologies
telemetrytv            23.1.1                  telemetrytv3               -        TelemetryTV Player
node                   18.13.0                 iojs&#10003;                      classic  Node.js
vectr                  0.1.15                  vectr&#10003;                     -        Vectr is a free graphics editor used to create vector graphics easily and intuitively.
red-app                8.0                     keshavnrj&#10026;                 -        Complete Youtube Desktop Applications
orange-app             6.0                     keshavnrj&#10026;                 -        SoundCloud Client and Downloader Desktop Applications
vsslagent              1.18                    vssl                       -        VSSL REST api.
joplin-arnatious       1.0.224                 arnatious                  -        Joplin is a free, open source note taking and to-do application.
pocket-browser         1.7.0                   pocketinc                  -        An open-source browser made for privacy and going towards security!
dashkiosk              v2.7.11                 ogra                       -        Drive a set of screens displaying dashboards
puppetry               3.2.6                   dsheiko                    -        Puppetry - codeless end-to-end test automation, integrated with CI/CD pipeline
reamix                 2.0.0                   vcborn                     -        A simple and useful browser based on electron.
strimio-desktop        3.0.10                  strimio                    -        Strimio is a free media player for macOS, Windows, and Linux, that enables you to play and organize your live streams like neve
office365webdesktop    0.7.1                   rafgui012                  -        It is a simple desktop application for Office365 of the web version for linux
home-media-server      5.20.0                  hms                        -        Digital Media Server (UPnP, DLNA, HTTP)
voidstar               v1.38.0                 fenoll                     -        void* casts files onto 2D/3D colored spaces for your mind blowing needs
boxy-svg               3.96.0                  jarek-foksa                -        Scalable Vector Graphics (SVG) editor
enpass                 6.6.3.835               chrismin13                 -        Offline Password Manager and Secure Vault. Saves and fill in all your passwords, cards and other details.
wise-highlights        1.1.5                   informawise                -        Manage your reading highlights.
accountable2you        6.0.23                  a2udeveloper               -        Accountable2You monitors device activity and sends reports to your chosen partner to help you stay accountable.
bitgesell-wallet       0.9.5                   epexa                      -        Bitgesell Wallet - &#1089;ross-platform wallet for BGL cryptocurrency.
atimerecording         1.4.16                  gerold-gp-softwaretechnik  -        Free online time tracking for work, self-employed, sports and leisure.
appspace-app           2.54.5                  appspace-cloud-ops         -        Reach your workforce with digital signs and more.
gpassmanager           1.1.0                   injamulmd                  -        CommandLine Password Manager
champ                  0.0.1~git               si-dz0ny                   -        Plex 2nd screen player
vtest-chrome           1.1.1                   ms-viojh                   -        vtest-chrome
vioj-chrome-test1      1.1.2                   ms-viojh                   -        Snapcraft Forum
```Apparently not. That's odd as I would have thought someone or other would have created one, but you are right.

I believe that it isn't a big deal to configure Chromium to import bookmarks and history, but I'm not sure about any specific app, so you are probably correct.

---

### Post by donald187 on 2023-02-04
Actually never mind.  I probably should have started a different thread.

---

### Post by poorguy on 2023-02-04
Here's how I update Firefox Snap and all Snaps.

In the terminal enter each command separately.

```

sudo killall firefox

```

press enter 
enter your password
press enter

then enter

```

sudo snap refresh

```

press enter


[https://itsfoss.com/pending-update-firefox-ubuntu/](https://itsfoss.com/pending-update-firefox-ubuntu/)

---

### Post by donald187 on 2023-02-04
> **DuckHook said:**
> 
I believe that it isn't a big deal to configure Chromium to import bookmarks and history, but I'm not sure about any specific app, so you are probably correct.
You seem to be referring to my claim that Chromium won't sync with mobile Chrome App?  You probably know this but I'll put it in here in case others who don't come across this thread.  Google removed the ability to sync Chromium maybe a couple of years ago..

[https://askubuntu.com/questions/1322559/sync-chromium-with-a-google-account-does-not-work-any-more-solutions](https://askubuntu.com/questions/1322559/sync-chromium-with-a-google-account-does-not-work-any-more-solutions)

---

### Post by DuckHook on 2023-02-05
> **donald187 said:**
> You seem to be referring to my claim that Chromium won't sync with mobile Chrome App?  You probably know this but I'll put it in here in case others who don't come across this thread.  Google removed the ability to sync Chromium maybe a couple of years ago..

[https://askubuntu.com/questions/1322559/sync-chromium-with-a-google-account-does-not-work-any-more-solutions](https://askubuntu.com/questions/1322559/sync-chromium-with-a-google-account-does-not-work-any-more-solutions)
I did not know that. Thanks for filling me in.

I admittedly haven't used Chrome for years. I won't touch any browser that has Google's fingerprints on it.

---

### Post by DuckHook on 2023-02-05
> **grahammechanical said:**
> …I will soon be 75 years old. I do not think it is a good thing to assume that elderly persons cannot learn new things and have to be shielded from stuff that makes life complicated.

Regards
@grahammechanical

I'm well seasoned myself and am still learning at a brisk pace, so I'm with you in your sentiments. However, to be completely honest, I also must admit that people like us are outliers.

Most of my compatriots are technophobes. They like the results of technology but not the learning curve. To be sure, a few have taken to Linux (or tech in general) with zest and enthusiasm, but most don't like it, fear it and certainly have no interest in the nitty gritty details. They "put up" with tech because of the benefits, but it's a curious love/hate relationship that I frankly find bizarre.

A considerable number are so technophobic that they would rather forego the benefits of tech than learn how to use it. I find that even more bizarre and self&#8209;limiting, but that's just the way they are. What has me shaking my head is that these are not dumb people. During their working lives, they were lawyers, doctors, architects and entrepreneurs. But in retirement, they have taken to dressing in skins and growling in the backwoods.

In 90% of cases, I've found that Quarkrad's approach is not only appropriate, but required. The only way to get them connected to the larger world out there was to shield them from anything complicated. Before, providing them such an outlet was a nice&#8209;to&#8209;have, but the pandemic turned it into a must&#8209;have because unfortunately I've also seen too many of my old friends draw into themselves and become hermits in the last three years.

Wildly off topic, I know, but I'm feeling strangely pensive today.

---

### Post by DuckHook on 2023-02-05
> **Quarkrad said:**
> So ... is my thinking right(?)

[LIST]
[*]I install Chromium snap
[*]A message will pop up at some time saying there is an update
[*]The next time* the user powers down and then up again the app (Chromium will update itself)
[/LIST]


* If the user powers down/up daily then there is no problem because the 13 day rule is not relevant.

The user is running 20.04 - if I turn off all snap notifications then providing there is daily power down/up everything (in this case (mainly Chromium, but very occasionally firefox) everything gets updated.
I'm not sure this is accurate.

I have to use snaps because I rely on LXD which comes only as a snap. I do shut down every day, but it still runs through the 13 day clock before updating LXD. I know this because I'm especially sensitive to such updates. I multiboot with all three OSes sharing the same LXD pool, so a LXD update on one OS will render the other OSes incapable of launching the pool until I manually update them. I know that a simple power cycle is not enough to initiate such an update. The 13 day clock must first run out.

---

### Post by donald187 on 2023-02-05
> **Quarkrad said:**
> So ... is my thinking right(?)

[LIST]
[*]I install Chromium snap 
[*]A message will pop up at some time saying there is an update 
[*]The next time* the user powers down and then up again the app (Chromium will update itself) 
[/LIST]


* If the user powers down/up daily then there is no problem because the 13 day rule is not relevant.

The user is running 20.04 - if I turn off all snap notifications then  providing there is daily power down/up everything (in this case (mainly  Chromium, but very occasionally firefox) everything gets  updated.


On my machine there seems to be 5 minutes between boot up and the first snap refresh.  From today's /var/log/syslog the first entry is at 6:47 am.

```

Feb  4 22:11:20 donald-Inspiron-3910 gnome-shell[2074]: The offending signal was actor-removed on Gjs_ui_appDisplay_FolderGrid 0x55f8aa1d2a30.
Feb  5 06:47:45 donald-Inspiron-3910 systemd-modules-load[391]: Inserted module 'lp'

```

And this shows when snap refreshed today at 6:52 am.

```

$ snap refresh --time
timer: 00:00~24:00/4
last: today at 06:52 PST
next: today at 13:28 PST

```

So that's 4 or 5 minutes.  My computer is new and boots very quickly.  I got similar results when I checked yesterday.  If your user opens Chromium before the snap refresh takes place then it won't update.

Just a reminder I'm just a regular user speculating.  But you and others can see the output I posted and decide for yourselves.

---

### Post by Dennis N on 2023-02-11
> As noted, flatpaks don't update with the system and require an update command.

I think you are correct regarding Ubuntu, but this may depend on the OS in which the Flatpaks are installed. I was just using a Fedora 37 Workstation, and it automatically updated Flatpaks within 3 minutes of startup and a notification popup appeared. Inkscape is installed as a Flatpak on the system. See screenshot. The updating is done by a plugin in Gnome Software. I've got Gnome Software and the plugin also in Ubuntu, but no automatic updates to Flatpaks seem to be be done in Ubuntu, but it is possible to install Flatpaks and update them along with other updates from the Gnome Software GUI.

---

### Post by monkeybrain20122 on 2023-02-11
> **Dennis N said:**
> I think you are correct regarding Ubuntu, but this may depend on the OS in which the Flatpaks are installed. I was just using a Fedora 37 Workstation, and it automatically updated Flatpaks within 3 minutes of startup and a notification popup appeared. Inkscape is installed as a Flatpak on the system. See screenshot. The updating is done by a plugin in Gnome Software. I've got Gnome Software and the plugin also in Ubuntu, but no automatic updates to Flatpaks seem to be be done in Ubuntu, but it is possible to install Flatpaks and update them along with other updates from the Gnome Software GUI.

Actually, in 20.04 flatpak did update automatically if you install the flatpak extension to gnome-software, or it is supposed to because it sometimes fails though it tries (popup says application updates but somehow can't connect to internet, it works sometimes though). Now in 22.04 I don't know since this is a new system and I haven't had any update for flatpak packages yet.

---

### Post by Quarkrad on 2023-02-12
One of my problems is trying to get 'an old' version of snap or flatpak Chromium to test the update.  I have managed to do this with .deb and adding Chromium to the 'app' part of Unattended Upgrades.  This seemed to work OK, Chromium updated itself without any user involvement.  On my personal machine I do not have any snap or flatpaks becuase partly, I like the manual involvement.  But here I'm looking at a complete non user-involvement environment (like Windows compared to Linux re updating).  There is always the option to take her back to Windows and all that involves in terms of virus' etc - but I would like to try and keep her on ubuntu.  (I could keep her on deb packages as it seems to work but with recent experience with VLC, and the way the tide is going, it seems to me deb is going to need more and more user involvement than snap/flatpak).  Is it possible to get old snap/flatpak versions of Chromium?

---

### Post by Dennis N on 2023-02-12
_Update on automatic updating of Flatpaks_:

Flatpaks on Ubuntu 22.10 do automatically update. I had previously thought no, but I just witnessed it. A notification bubble does appear to inform you. On this system, Ubuntu Software has been uninstalled, and Gnome Software (along with the Flatpak and Snap plugins) replaced it. Gnome Software is a .deb package, not a Snap.

---

### Post by Quarkrad on 2023-02-12
That's very interesting DennisN - is it possible to tell me the two Chromium version numbers?

---

### Post by Dennis N on 2023-02-13
> **Quarkrad said:**
> That's very interesting DennisN - is it possible to tell me the two Chromium version numbers?

The update notification referred to in post #29 was for Inkscape. Chromium does have a Flatpak package, but I haven't installed it. I assume it would behave the same as Inkscape.

```
[dmn@kayleigh ~]$ flatpak remote-info flathub org.chromium.Chromium
        ID: org.chromium.Chromium
       Ref: app/org.chromium.Chromium/x86_64/stable
      Arch: x86_64
    Branch: stable
Collection: org.flathub.Stable
  Download: 129.3*MB
 Installed: 335.7*MB
   Runtime: org.freedesktop.Platform/x86_64/22.08
       Sdk: org.freedesktop.Sdk/x86_64/22.08

```

Flatpak search says the current version is 110.0.5481.77

---

