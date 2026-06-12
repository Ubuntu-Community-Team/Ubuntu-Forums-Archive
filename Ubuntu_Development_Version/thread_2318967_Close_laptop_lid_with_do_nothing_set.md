---
title: "Close laptop lid with do nothing set"
date: 2016-03-30
forum: Ubuntu Development Version
---

### Post by mc4man on 2016-03-30
There was an [issue around  15.04]("http://ubuntuforums.org/showthread.php?t=2290458") where in certain circumstances windows would be opened while lid was closed. Seems to have gone away in 15.10/early 16.04 but has showed up again here in spades. (different hardware than seen with before

So this morning on an Hp laptop I have with touchpad enabled & a touch screen I went out & simply closed the lid. Upon returning 5 hrs later found when opening screen - 
More than a dozen windows open, various apps, many i never use. Once I got all the windows closed, (some were hard as a modal window was hidden) I noticed it wasn't my desktop that i'd left on, _it was a guest session_. Logged out, into my session, same deal. In addition to tons of open windows all the icons were wrong in unity panel, folders wrong color, desktop icons with black text, ect. A complete mess. A reboot didn't resolve so reset dconf back to defaults to start over.

If desiring to test, needed is obviously a laptop with an enabled touchpad. Even better if it also has a touch screen. Brightness & Lock and  Power options need to be as in screen shots. Basically set to never turn off when inactive , don't  dim, no lockscreen & do nothing when lid is closed. (the screen will turn off when closing lid.
Then just close lid & check several hrs. later

---

### Post by QDR06VV9 on 2016-03-31
@ mc4man I have tried to test this as you described...but one difference I have no touch-screen, been closed for hours now and nothing abnormal for myself.
Worth noting here my screen did not turn off when closing the lid.
16.04 Mate DE
```
inxi -M
Machine:   System: LENOVO (portable) product: 1068AJU v: Lenovo B570
           Mobo: LENOVO model: Emerald Lake v: FAB1
           Bios: LENOVO v: 44CN43WW date: 10/27/2011
```

---

### Post by mc4man on 2016-03-31
Actually I've now noticed it's worse when the power settings is left at the default of suspend. 
So this morning closed the lid from my session, no windows open. Just got back, opened lid & it was at the greeter screen with guest session highlighted. 
Opened my user to find this nonsense, screen 1. Notice how the window deco is borked, icons are wrong in the unity panel. Also the files icon in launcher is wrong, the highlighting of launcher icons is wrong. 2nd screen is my desktop, wrong text color on icons, wrong folder icons,  2 new untitled folders. (not as bad as yesterday but still uncalled for behavior...
screen 3 is how I left the desktop this morning.

Edit: just uncovered the appearances window, seems while  'suspended' it had switched my theme to high contrast.. scr. 4

---

### Post by QDR06VV9 on 2016-03-31
Sheesh! that is kind of creepy...that could wreak havoc for a paranoid mind.
Still testing the different power settings on mine to see if i can also duplicate.
Kind regards

---

### Post by mc4man on 2016-04-01
Overnight virtually nothing. just was  logged out & trash opened.
This morning did some things, closed all windows out, closed lid (suspend
3 hr.'s later quite remarkable how busy it has been. 

logged me out to greeter
40 nautilus windows or modals
firefox
20 archive managers (mainly dupes
gedit
system settings > details
Videos
power settings
terminal on multilple ws's
mpv
Windows that's on an  other partition (plus Documents & Settings in windows...
10 image viewer windows
(and that's just on 1 workspace, 1/2 dozen others on other ws's

---

### Post by QDR06VV9 on 2016-04-01
Are you April Fooling us..;) No just kidding here.
I remember when this was happening to you on trusty also..Don't know if it is the same laptop or not.
I remember The Cog suggesting a piece of tin foil between the Lid and keyboard for the display->trackpad crosstalk. 
And the only thing I can find on the web about it is just not waking from suspend.

[http://h30434.www3.hp.com/t5/Notebook-Hardware-and-Upgrade-Questions/Numerous-issues-with-Elitebook-840-G1-models/td-p/5081106](http://h30434.www3.hp.com/t5/Notebook-Hardware-and-Upgrade-Questions/Numerous-issues-with-Elitebook-840-G1-models/td-p/5081106)

[http://support.hp.com/us-en/document/c04441999](http://support.hp.com/us-en/document/c04441999)
But that is just not right by all accounts,(Obviously)

---

### Post by mc4man on 2016-04-01
No,  the other laptop was a lenovo Y480p (my main laptop.) On that one almost nothing ever goes awry, as far as this not a factor any more  as I have the touchpad disabled.

This is some HP pavilion I got over the fall that came with a touchscreen display. I seems the combo of touchpad enabled & touchscreen causes this massive cross-talk. 
I mainly got this one because I need windows for a few things & wanted to put an ssd in the lenovo & no windows. I put ubuntu on the Hp just to see how skylake performed. Due to some circumstances I wasn't able to check the Hp out for a month, if I had been able to right away likely would have returned it.
(- now I know what u means in a processor name, other than almost 'useless'

I think I'll try another version of *buntu on this machine to see if this nonsense is version related or linux related as it doesn't happen on windows

---

