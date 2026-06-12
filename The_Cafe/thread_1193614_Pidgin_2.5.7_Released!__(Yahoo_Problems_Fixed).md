---
title: "Pidgin 2.5.7 Released!  (Yahoo Problems Fixed)"
date: 2009-06-21
forum: The Cafe
---

### Post by Kosimo on 2009-06-21
Folks, Pidgin 2.5.7 has been released!

Here the changelog:

>    * Yahoo Protocol 16 support, including new HTTPS login method; this should
     fix a number of login problems that have recently cropped up.  (Sulabh
     Mahajan, Mike &quot;Maiku&quot; Ruprecht)
   * Only display the AIM &quot;Unable to Retrieve Buddy List&quot; message once per
     connection.  (Rob Taft)
   * Blocking MSN users not on your buddy list no longer disconnects you.
   * When performing operations on MSN, assume users are on the MSN/Passport
     network if we don't get network ID's for them.



Get it from Getdeb.net:

[http://www.getdeb.net/app/Pidgin](http://www.getdeb.net/app/Pidgin)


Of if you want to copile it yourself:  [www.pidgin.im](www.pidgin.im)

---

### Post by RATM_Owns on 2009-06-21
Already got it from mah `pacman -Syu` :D

---

### Post by Wiebelhaus on 2009-06-21
Nice! , thanks for the heads up!

---

### Post by JordyD on 2009-06-21
> **RATM_Owns said:**
> Already got it from mah `pacman -Syu` :D

Likewise

---

### Post by racerraul on 2009-06-21
How much longer till you can add multiple people to a single chat?

---

### Post by DirtDawg on 2009-06-21
No Intrepid build? Boo!

Thanks for the heads up anyways.

---

### Post by AgentZ86 on 2009-06-21
Nice, thanks

---

### Post by Tibuda on 2009-06-21
> **DirtDawg said:**
> No Intrepid build? Boo!

Thanks for the heads up anyways.

Try the PPA.
[https://launchpad.net/~pidgin-developers/+archive/ppa](https://launchpad.net/~pidgin-developers/+archive/ppa)

---

### Post by AgentZ86 on 2009-06-21
> **danielrmt said:**
> Try the PPA.
[https://launchpad.net/~pidgin-developers/+archive/ppa](https://launchpad.net/~pidgin-developers/+archive/ppa)

Intrepid Boo Boo big time, I got one computer running hardy and the other running intrepid

Now What ?

---

### Post by AgentZ86 on 2009-06-21
Fix for Intrepid and perhaps other versions or all version of Pidgin Yahoo client

See other post on this and it worked great for me also.

I updated pidgin on my Ubuntu 8.04 which worked well, however the pidgin update for intrepid 8.10 did not work since there is only a 2.5 version for intrepid,
 so I then used the info found at this link:

[http://ubuntuforums.org/showthread.php?t=1192135&highlight=pidgin+yahoo](http://ubuntuforums.org/showthread.php?t=1192135&highlight=pidgin+yahoo)

Also a few others links on Ubuntu suggest to put Yahoo IP address in for Pager server, but I've not tried that since this suggestions worked good.

Thanks go all.

---

### Post by earthpigg on 2009-06-21
sooo i removed pidgin via synaptic... then downloaded pidgin for amd64 jaunty... it told me i needed pidgin-data, so i downloaded that from getdeb.

when i open up pidgin-data, the 'install' button is ghosted, with no indication as to why.

ideas, anyone?

edit: got it. had to remove libpurple and the other one, too...

---

### Post by zeroseven0183 on 2009-06-21
Great! No more changing of hosts.

---

### Post by Grant A. on 2009-06-21
TBH, I'm very confused about Pidgin using Yahoo. Yahoo sued Xfire over similarities to Yahoo's protocol, yet Pidgin gets to use it?

---

### Post by earthpigg on 2009-06-21
> **Grant A. said:**
> TBH, I'm very confused about Pidgin using Yahoo. Yahoo sued Xfire over similarities to Yahoo's protocol, yet Pidgin gets to use it?

[http://news.cnet.com/Yahoo-sues-Xfire-for-patent-infringement/2100-1047_3-5564179.html](http://news.cnet.com/Yahoo-sues-Xfire-for-patent-infringement/2100-1047_3-5564179.html)

> 
In the case of the '125 patent, Gottlieb and Kirmse were employed by Yahoo when they developed technologies for a game-specific variation on Yahoo's popular Yahoo Messenger. Yahoo has been the sole owner of the '125 patent since it was granted.

The complaint describes the Yahoo Messenger instant-message service--in this case, the GameProwler instant messenger application--as one that "allows users to use a game server in connection with a messenger server to permit 'buddies' to know when other 'buddies' are playing games online, and easily join such games."

pidgin does not do that.... not that it changes anything about how software patents in their current state are utter crap.

---

### Post by Twexcom on 2009-06-22
I wish there was a 2.5.7 build for 8.10 (Intrepid). Would someone be nice enough to do that?

---

### Post by AgentZ86 on 2009-06-22
> **Twexcom said:**
> I wish there was a 2.5.7 build for 8.10 (Intrepid). Would someone be nice enough to do that?

Hi

Intrepid and just about all others fixes for Yahoo can be done

Although I still upgraded my Intrepid Pidgin to version 2.5 it still needed the Pager Server field fixed.

See Message 1) from this link:
[http://ubuntuforums.org/showthread.php?t=1192135&highlight=pidgin+yahoo](http://ubuntuforums.org/showthread.php?t=1192135&highlight=pidgin+yahoo)

Also others suggested using the IP address of yahoo to place this in the Pager Server field but I've not tried this since my Yahoo on Intrepid is working.

I hope this helps

---

### Post by g33k on 2009-06-22
Works like a charm, thanks!

---

### Post by duckytn on 2009-06-23
I have followed these steps and have Pidgin working fine. The only issue is it appears to have broken the association between Pidgin and the new Notification Area. I can no longer get Pidgin to minimize to the Notification Area. Anyone else experience this or have any suggestions?

Thanks!

Eric

---

### Post by Kosimo on 2009-06-23
> **duckytn said:**
> I have followed these steps and have Pidgin working fine. The only issue is it appears to have broken the association between Pidgin and the new Notification Area. I can no longer get Pidgin to minimize to the Notification Area. Anyone else experience this or have any suggestions?

Thanks!

Eric

Open the main window, go to preferences, and set the notification icon to show up ALWAYS.

---

### Post by duckytn on 2009-06-23
> **Kosimo said:**
> Open the main window, go to preferences, and set the notification icon to show up ALWAYS.

Is this within Pidgin ?

---

### Post by peggyarmstrong on 2009-06-24
I did this, then a few days later update manager fed updates and they worked without any problems

Ubuntu ships Pidgin but does not update it after a release (except for security issues). For those users who desire new releases of Pidgin, we have packaged Pidgin in a PPA. If you encounter problems with these packages, try building from source and report the bug.

To setup the PPA, copy-and-paste these commands into a terminal:

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \     67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8

echo deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) \     `lsb_release --short --codename` main | \
    sudo tee /etc/apt/sources.list.d/pidgin-ppa.list

Once this PPA is setup, Pidgin updates will show up in Update Manager along with the usual Ubuntu updates. The PPA will need to be re-setup only after upgrading Ubuntu.

This PPA is maintained by one developer, so please be patient. It often lags behind the source releases a couple of days.

---

### Post by thale on 2009-06-24
> **peggyarmstrong said:**
> 
To setup the PPA, copy-and-paste these commands into a terminal:

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \     67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8

echo deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) \     `lsb_release --short --codename` main | \
    sudo tee /etc/apt/sources.list.d/pidgin-ppa.list



It appears the keyserver is timing out :(

---

### Post by g33k on 2009-06-24
You can manually add this key to your sources:

[ATTACH]118794[/ATTACH]

The .txt suffix is just to get it to attach to the forums.

---

### Post by thale on 2009-06-24
Perfect, works great!

In the event you're like me, running jaunty and completely removed pidgin. You'll need to reinstall pidgin-libnotify to get your jaunty integration back.

---

### Post by g33k on 2009-06-24
And pidgin-otr and pidgin-encryption if you use such things.

---

### Post by shark on 2009-06-24
Hi. Recently updated to 2.5.7, it worked fine for a couple of days, but suddenly all avatars disappeared. I'm using it for Yahoo protocol. I'll tried to reinstall and to remove ~/.purple, but nothing ...

---

### Post by mister_k81 on 2009-06-24
> **shark said:**
> Hi. Recently updated to 2.5.7, it worked fine for a couple of days, but suddenly all avatars disappeared. I'm using it for Yahoo protocol. I'll tried to reinstall and to remove ~/.purple, but nothing ...

I'm having the same problem as well. Also the file transfer in Yahoo protocol doesn't work for me either.

---

### Post by g33k on 2009-06-25
> **shark said:**
> Hi. Recently updated to 2.5.7, it worked fine for a couple of days, but suddenly all avatars disappeared. I'm using it for Yahoo protocol. I'll tried to reinstall and to remove ~/.purple, but nothing ...


How did you upgrade?  From PPA, from getdeb, or from source?

---

### Post by PuddingKnife on 2009-06-25
does it have web cam chat yet?

---

### Post by g33k on 2009-06-25
> **PuddingKnife said:**
> does it have web cam chat yet?

Negative.

---

### Post by PuddingKnife on 2009-06-25
> **g33k said:**
> Negative.

Well that sucks.  Are there any linux chat clients that have web cam integration and work w/ yahoo chat?

---

### Post by g33k on 2009-06-25
> **PuddingKnife said:**
> Well that sucks.  Are there any linux chat clients that have web cam integration and work w/ yahoo chat?

None that I'm aware of.  But I don't use webcam chat, so I honestly haven't looked into it very extensively.

---

### Post by longtom on 2009-06-25
Thanks for that.  Had to jump through hoops before that - now all is as it should be.

---

### Post by shark on 2009-06-25
> **g33k said:**
> How did you upgrade?  From PPA, from getdeb, or from source?
I'll tried all methods.

---

### Post by g33k on 2009-06-25
> **shark said:**
> I'll tried all methods.

Not sure.  By avatars, you mean yours?  Or your friends?  I assume you have checked the Buddies > Show > Buddy Details option.

---

### Post by shark on 2009-06-25
> **g33k said:**
> Not sure.  By avatars, you mean yours?  Or your friends?  I assume you have checked the Buddies > Show > Buddy Details option.
Neither. And "Buddy Details" is checked. :)

---

### Post by g33k on 2009-06-25
> **shark said:**
> Neither. And "Buddy Details" is checked. :)


Odd indeed.  So, when you uninstalled Pidgin, did you blow out ~/.purple and let it rebuild?

---

### Post by shark on 2009-06-25
> **g33k said:**
> Odd indeed.  So, when you uninstalled Pidgin, did you blow out ~/.purple and let it rebuild?
I removed the application, then removed that folder, after that reinstalled the applicatin, but no change.

---

### Post by g33k on 2009-06-25
> **shark said:**
> I removed the application, then removed that folder, after that reinstalled the applicatin, but no change.

Did you also kill /etc/purple and /usr/share/purple?  I'm just grasping at straws with you to be honest.

---

### Post by shark on 2009-06-25
> **g33k said:**
> Did you also kill /etc/purple and /usr/share/purple?  I'm just grasping at straws with you to be honest.
Only /etc/purple, because /usr/share/purple does not exist.

---

### Post by g33k on 2009-06-25
Ok, so let me make sure I inderstand.  Pidgin works fine, but doesn't display avatars?

---

### Post by billgoldberg on 2009-06-25
> **RATM_Owns said:**
> Already got it from mah `pacman -Syu` :D

Only 1 post until someone mentions Arch.

It's getting bad.

---

### Post by shark on 2009-06-25
> **g33k said:**
> Ok, so let me make sure I inderstand.  Pidgin works fine, but doesn't display avatars?
Exactly! :D

---

### Post by g33k on 2009-06-25
> **shark said:**
> Exactly! :D


Hmm... That's effed up.

---

### Post by shark on 2009-06-25
Maybe this will help: 
(18:23:26) prefs: /pidgin/blist/show_buddy_icons changed, scheduling save.
(18:23:27) dbus: Need to register an object with the dbus subsystem. (If you are not a developer, please ignore this message.)
(18:23:27) dbus: The signal "drawing-tooltip" caused some dbus error. (If you are not a developer, please ignore this message.)

---

### Post by peggyarmstrong on 2009-06-26
> **thale said:**
> It appears the keyserver is timing out :(
I cut and pasted it as it was all three sets of commands at the same time, didn't think it would work but the updates came 2 days later

---

