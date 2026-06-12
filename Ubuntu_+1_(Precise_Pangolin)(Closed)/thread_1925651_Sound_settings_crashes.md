---
title: "Sound settings crashes"
date: 2012-02-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Sportsstar99 on 2012-02-14
Hi im running precise x64 with everything updated and whenever i click on sound settings a white box pops up and immediately closes but when i delete the .pulse folder in the home directory it allows sound settings to pop up but does not show any devices it's been doing this for a few days now. Anybody else experiencing this or knows how to fix it? thanks in advance :p

---

### Post by jbicha on 2012-02-14
Are you using any PPAs?

---

### Post by cariboo on 2012-02-15
I get the same thing when clicking on Sound settings, from the speaker icon. I've created a bug report, #[lpbug]932542[/lpbug], it may be classed as a duplicate though, as there is a similar bug reported for Oneiric.

---

### Post by mc4man on 2012-02-15
Again i'd 1st try a new user & see if it works there, either  it's a system or user issue.

To run directly from term, 
```
 gnome-control-center sound-nua
```

or open g-c-c, click on icon
```
gnome-control-center sound
```

---

### Post by clifford junior on 2012-02-15
i recently have the same problem. i tried logging in as a guest and the same thing. the crashing also effects colour networking etc. actually colour and networking do actually open but as soon as you click anything it crashes.

i ran 

```
gnome-control-centre sound-nua
```

and go the following response while it crashed

```
ion Front Microphone 
 device port = analog-input-microphone-front 
 device stream id 3 
 AND 
 stream port = analog-input-microphone-front stream id 3 and stream description Built-in Audio Analogue Stereo 

 active_input_update Front Microphone 

Gtk-CRITICAL **: gtk_list_store_get_value: assertion `iter_is_valid (iter, list_store)' failed

GLib-GObject-WARNING **: /build/buildd/glib2.0-2.31.16/./gobject/gtype.c:4205: type id `0' is invalid

GLib-GObject-WARNING **: can't peek value table for type `<invalid>' which is not currently referenced
Segmentation fault (core dumped)

```

---

### Post by mc4man on 2012-02-15
Try getting fully updated, sound-nua seemed to break here with the g-c-c upgrade but now is working fine again

---

### Post by kevpan815 on 2012-02-15
At least you are getting sound, I am getting no sound at all currently on this Virtual Box installation, so far I have tried 2 oif the 3 Sound Card Options (Intel Integrated Sound, and Sound Blaster 16) no sound from either of them. The only one that I have NOT tried is AC97 Sound Card. Just FYI.

---

### Post by Sportsstar99 on 2012-02-15
> **jbicha said:**
> Are you using any PPAs?
yes xbmc and all the defualt ones
> **mc4man said:**
> Try getting fully updated, sound-nua seemed to  break here with the g-c-c upgrade but now is working fine again
I am fully updated according to terminal ill try uninstalling it then re-installing it

---

### Post by PaulW2U on 2012-02-15
Some of the sound settings applet is working for me except I cannot select an input or an output. If I do the applet crashes. I've added a note to the bug report.

---

### Post by mc4man on 2012-02-15
> **PaulW2U said:**
> Some of the sound settings applet is working for me except I cannot select an input or an output. If I do the applet crashes. I've added a note to the bug report.

Then that will & does produce an apport crash report (only see on input here

To see the error went ahead & filed here, will leave as private till a retrace is done & if it is a dup it will be marked as such & cleaned up

The error was 
gnome-control-center crashed with SIGSEGV in g_cclosure_marshal_VOID__VOID()

If you get segfaults on something it's worth checking in /var/crash to see if a .crash was generated, you don't always get a pop up

Edit: so the retrace is completed & there is a prior bug on this though atm it's still private so really have no idea it's it is actually the same & the status of.
 [https://bugs.launchpad.net/bugs/930699](https://bugs.launchpad.net/bugs/930699)

---

### Post by PaulW2U on 2012-02-15
> **mc4man said:**
> If you get segfaults on something it's worth checking in /var/crash to see if a .crash was generated, you don't always get a pop up

Ok, I made the applet crash three times, nothing was added to /var/crash.

---

### Post by Mr. Picklesworth on 2012-02-15
This was a bug in a recent libgtk3 update which caused gnome-control-center to crash. Please update to the latest (3.3.14-0ubuntu3) and check if it is still happening.

-edited: silly typo. That's what happens when I type the version number by hand-

---

### Post by mc4man on 2012-02-15
that's already been reverted, so if on 0ubuntu2 then look for 0ubuntu3
> gtk+3.0 (3.3.14-0ubuntu3) precise; urgency=low

  * Revert the previous upload, it turned gnome-control-center to a segfault 
    land (and probably others), we will update to the next gtk including that 
    stack of commits once upstream rolls a tested tarball    
    (lp: #932876, #932644)gtk+3.0 (3.3.14-0ubuntu3) precise; urgency=low

---

### Post by mc4man on 2012-02-15
> **PaulW2U said:**
> Ok, I made the applet crash three times, nothing was added to /var/crash.

Easy to create here, curious -  Do you have any .crash's in /var/crash?

---

### Post by Sportsstar99 on 2012-02-15
> **Mr. Picklesworth said:**
> This was a bug in a recent libgtk3 update which caused gnome-control-center to crash. Please update to the latest (3.3.14-0ubuntu2) and check if it is still happening.
clean installed bout an hour ago and just ran sudo apt-get upgrade and got it but sound settings still crashes:(

---

### Post by PaulW2U on 2012-02-15
> **mc4man said:**
> Easy to create here, curious -  Do you have any .crash's in /var/crash?

Yes, about 15. Mainly related to opera, gnome-shell, gwibber and nautilus.

---

### Post by mc4man on 2012-02-15
With the new updates to gtk & g-c-c no longer crashes here,  - 
gnome-control-center 3.2.2-2ubuntu10
*gtk-3-0  3.3.14-0ubuntu3

---

### Post by Stinger on 2012-02-15
Confirming crash

Still crashes here with

*gtk-3-0 3.3.14-0ubuntu3
gnome-control-center 3.2.2-2ubuntu10

---

### Post by PaulW2U on 2012-02-15
> **Mr. Picklesworth said:**
> This was a bug in a recent libgtk3 update which caused gnome-control-center to crash. Please update to the latest (3.3.14-0ubuntu2) and check if it is still happening.

I've updated to 3.3.14-0ubuntu**3** and the sound applet still crashes when I select some of entries in the input and output tabs. Taking a much closer look at that list I've got far too many entries.

On the output tab, most of the duplicates are either Analogue Output/Amplifier or Analogue Output/No Amplifier against my SB Audigy sound card.

On the input tab, most of the duplicates are labelled Microphone/Microphone 1 or Microphone/Microphone 2 against Built-in Audio.

May be I get the crash when I select an entry that shouldn't be there?

---

### Post by matt_symes on 2012-02-15
Not related to the OP's crash, but i have lost output from the headphone jack socket.

Sound from the main speakers but not through the head phone jack when speakers are plugged in. 

Anybody else have this issue ?

---

### Post by Sportsstar99 on 2012-02-16
Still crashing with the new update

---

### Post by clifford junior on 2012-02-16
yep same here

---

### Post by PaulW2U on 2012-02-17
All seems ok now.

The extra entries in that input and output tabs I referred to in post [#19](http://ubuntuforums.org/showpost.php?p=11692051&postcount=19) have gone. :D

---

### Post by Stinger on 2012-02-22
Seems to work fine now with todays updates \\:D/


*gtk-3-0 3.3.16-0ubuntu1
gnome-control-center 1:3.3.90-0ubuntu1

---

