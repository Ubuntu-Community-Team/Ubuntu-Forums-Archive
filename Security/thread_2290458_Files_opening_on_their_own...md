---
title: "Files opening on their own..?"
date: 2015-08-12
forum: Security
---

### Post by zero212 on 2015-08-12
I left my computer and locked my screen, when I came back and unlocked it there were some text files opened and I know for certain they weren't before. This has happened a few times, but its rare. I ran rkhunter and everything is clean except the ruby script warning on unhide.rb(which isnt bad I think?). I tried nethogs and no weird processes showed up. What is going on?

Additional information, this isn't a server and has never had any SSH setups or remote stuff. It's just a simple computer.

---

### Post by v3.xx on 2015-08-12
What files are showing up?

---

### Post by zero212 on 2015-08-12
It's usually just notes I make and other documents like school work.

---

### Post by Habitual on 2015-08-12
Were they opened recently (before this event)?

---

### Post by mc4man on 2015-08-12
I've seen somewhat the same here on a fairly old, 1yr+ 14.04 install. My newer 14.04.3 install is fine, both are using the lts-vivid kernel.

The  difference here is it's a laptop where I've set closing the laptop lid to 'do nothing' which basically should just blank the screen.
While the lid is closed apps start opening, longer closed the more. I've even had a video player open up & start playing a video.

It seems to open apps as they have been recently but can occur after a reboot. For example just closed the lid, waited a minute or so & evince was open on a .pdf from this morning. This install has been shut down a couple of times since then.

I'll likely just dump the install rather than pursue, I don't need it doing something  over again like sending some email or whatever..., don't  trust this install at all anymore.

---

### Post by zero212 on 2015-08-13
Never been opened in months actually, a lot of what opens is stuff I don't even need. 

@Mc4Man
That's exactly what happens! This is so strange, it's really quite spooky.

---

### Post by mc4man on 2015-08-13
It is really weird - 
So this morning booted up, closed lid, went to make a coffee. all of a sudden heard music coming from laptop. Opening lid on ws1 there were 4 nautilus windows open on same location (hadn't opened that location in some time), on ws2 a nautilus window & command line player playing a video.
So closed out all, log out/in, closed lid, got coffee. Now what you see in screen 1. Notice the file had been edited & highlighted, I hadn't touched the keyboard when opening. (A space was added between lines 7 & 8..

---

### Post by zero212 on 2015-08-13
Wow, this is seeming more and more like a sophisticated deep rooted backdoor. One thing that I am positive of is that mine started up after the flash exploit news, since then the laptop has been acting like this. What is particularly strange is that it only happens when I close the lid. I watched nethogs all night long, and still saw nothing. I'm not too familiar with network monitoring but perhaps there is a better way to monitor a computer to see if there is any kind of remote logins happening.

Edit: Oh yeah, I also completely looked over **auth.log** and found *nothing, *even when I looked at the events all I saw was Lid Closed, then Lid Opened.

---

### Post by mc4man on 2015-08-13
Happens here with  Internet connection turned off. 
Also removed the zeitgeist folder, recently-used.xbel, unhooked wireless mouse - no difference
When I disabled the Desktop (no show icons) it slowed a bit  but windows did show.
Also nothing in any of the /var logs or ~/.cache/upstart logs. 
Complete mystery here... especially the editing/highlighting of text or source files.

Maybe I'll set up a new user & see what happens there, will have this install until mid next week.

---

### Post by fugu2 on 2015-08-14
if your computer is infected, the simply telling it to turn the Internet is not sufficient. The wifi card in your laptop is probably about 1 inch by 1/2 inch, and you'll need to pull it out (if you feel comfortable doing so) usually just 1 maybe 2 screws.

---

### Post by CharlesA on 2015-08-14
> **fugu2 said:**
> if your computer is infected, the simply telling it to turn the Internet is not sufficient. The wifi card in your laptop is probably about 1 inch by 1/2 inch, and you'll need to pull it out (if you feel comfortable doing so) usually just 1 maybe 2 screws.

That's a bit extreme isn't it?

mc4man: Try wiping the machine and see if the same behavior shows up on the clean install. If so report it as a bug.

---

### Post by deadflowr on 2015-08-14
Is this all happening within a Unity session?
Or does it persists on other(or all) DEs?

---

### Post by zero212 on 2015-08-14
Well I use XFCE, and Unity has never been installed on this laptop before.

---

### Post by untrustytahr on 2015-08-14
I have actually seen this behavior before.  It was caused by a defective trackpad and/or keyboard.  Closing the lid would cause enough flex to enter clicks.  Sometimes it was the trackpad mounting screws coming loose... Other times the trackpad itself was going bad.  Similar problems with keyboards.

I would try disabling the trackpad & keyboard and use an external replacement and see if the problem persists.

---

### Post by mc4man on 2015-08-14
Seemed to have resolved here with a bit of a sledgehammer.
From another install moved all . files & folders & all non Xdg dir folders & loose files  in home to holding folders on Desktop, then booted/logged in. 
no sign of issues, so have moved slowly back some . files (.bash*, .profile), ~/.config/dconf/user, ~./config/autostart, ~/.local/share/applications/various .desktops, still no sign.

I don't believe it was any of the auto recreated files - ~/.Xauthority, ~/ICEauthority, ect. so something else in ~/. 
Maybe over the weekend will put back some of those orig.  folders/files & see if it starts up again & if so what causes.

---

### Post by fugu2 on 2015-08-14
> **CharlesA said:**
> That's a bit extreme isn't it?
Yes, probably. But its going to guarantee that someone won't be able to react to his actions if he does have an infection.

---

### Post by mc4man on 2015-08-15
Completely gone here - unfortunately my attempt then to 're-enable' the behaviour  has been thwarted by not paying attention to what window I was in when doing some copying so lost some of the orig. . folders.  Too bad really..

 Maybe try from either another install or a tty (ctrl+alt+F3 will do) moving some suspect . folders to a new name, then reboot & log in. Start with .cache, .config, .local
(as in .cache > .cache1, ect. From tty just simple command, ex. 
mv .config .config1
If doing from a tty don't return to the tty7 session, do a sudo reboot from tty.

---

### Post by The Cog on 2015-08-15
> **mc4man said:**
> Completely gone here - unfortunately my attempt then to 're-enable' the behaviour  has been thwarted 

That's a shame. I ws going to suggest closing the lid with a sheet of baking foil between the screen and trackpad to see if it was display->trackpad crosstalk.

---

### Post by mc4man on 2015-08-15
> **The Cog said:**
> That's a shame. I ws going to suggest closing the lid with a sheet of baking foil between the screen and trackpad to see if it was display->trackpad crosstalk.
Don't have any tin foil, but started me thinking, particularly in reference to what changed over the last 2-3 weeks or so & what could be in one of those . folders.

So *here*  it does **seem** to be from closing the lid in 'blank' mode & having the touchpad enabled. When doing so then random windows are opened in various state & workspaces while the lid is closed over a period of time.

A bit of history - 
I use a wireless mouse & always have the touchpad disabled. In Ubuntu there was [an ongoing bug]("https://bugs.launchpad.net/ubuntu/+source/unity-settings-daemon/+bug/1283863") that when one disabled the touchpad the setting would be reverted on log out/in or restart/fresh boot. As it was not fixed for a long time started using a start up script that was very effective, this way all new sessions would have it disabled. 
A couple of weeks ago there was an update to unity-settings-daemon that while was on a [slightly different related bug]("https://bugs.launchpad.net/ubuntu/+source/unity-settings-daemon/+bug/1454950") also happened to fix the former bug. So I removed the startup script & just went with the new u-s-d to keep touchpad disabled.

The problem with that is that if the wireless mouse is disconnected or during one's log in or session ?whatever? loses contact with the mouse then the touchpad (plugin) is immediately re-enabled & stays that way.

So I say seem above because when I replaces all the .folders orig. I would have gotten a gsetting of touchpad enabled. I don't remember turning it off... yet all was well. Also this didn't occur in a new user which would have had the plugin enabled also. So that's still a mystery of sorts but I can recreate the issue by re-enabling the touchpad plugin. (maybe I had a window open, maybe another factor.

Anyway, if affected, try disabling the touchpad or foil

Can also dupe this behaviour on same machine 14.04.3 & 15.10 installs. Only diff is the number/time of windows/apps opened. Much slower & less on these installs.

(- if someone's got a method to log input events would be interested.

---

### Post by mc4man on 2015-08-15
```
sudo lsinput
/dev/input/event5
   bustype : BUS_I8042
   vendor  : 0x2
   product : 0xe
   version : 0
   name    : "ETPS/2 Elantech Touchpad"
   phys    : "isa0060/serio1/input0"
   bits ev : EV_SYN EV_KEY EV_ABS

```
attached is a log of sudo input-events 5 -t 360  >> 11.log, created over a couple of min. with lid closed on the mildly affected 14.04.3 install
(a couple of windows where open when returning & a couple of new untitled folders created, whether the command or log is  correct manner or relevant don't know, seems like a couple of events were logged. 
Without the -t first attempt just timed out with no events

---

