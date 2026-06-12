---
title: "[SOLVED] Some Pangolin v3 buttons no longer working"
date: 2007-10-08
forum: System76 Support
---

### Post by octathlon on 2007-10-08
When I first got my Pangolin Value (panv3), the hardware buttons for Mute, Wow Video, and Wow Audio worked fine.  

Recently I noticed that they don't work anymore --  there have been a couple of kernel updates since then.  I have run the System76 driver Restore, but it didn't help.  

The buttons for Internet and Email still work.

Selecting Mute from the Volume control's right-click menu still works (though its shortcut, Ctrl+T, doesn't & I don't think it ever did).  The preferences are set with Front as the track to control and Alsa mixer as the device.

---

### Post by thomasaaron on 2007-10-09
Sounds like you're running Gutsy, right?

I just did all the latest updates on my PanV3. The keys and buttons still work fine.
I think the wow buttons are configured with the System 76 driver (I'll have to verify that). But the driver doesn't do anything under Gutsy yet. It looks like it runs, but that's it.

I don't think the Ctrl-T does anything(??).

Also, go to System > Preferences > Sound and make sure:
1. The Default Mixer Tracks Device is set to "HDA Intel (Alsa Mixer)"
2. "Front" or "Master" is highlighted at the bottom. Then try your volume and mute keys.

---

### Post by octathlon on 2007-10-09
> **thomasaaron said:**
> Sounds like you're running Gutsy, right?

I just did all the latest updates on my PanV3. The keys and buttons still work fine.
I think the wow buttons are configured with the System 76 driver (I'll have to verify that). But the driver doesn't do anything under Gutsy yet. It looks like it runs, but that's it.

No, I'm not running gutsy.  I am running Feisty just as it came preinstalled plus I have run all the automatic updates.
> 
I don't think the Ctrl-T does anything(??).

I just mentioned ctrl-T because it is shown as the shortcut key for Mute under the Volume Control context menu.

> 
Also, go to System > Preferences > Sound and make sure:
1. The Default Mixer Tracks Device is set to "HDA Intel (Alsa Mixer)"
2. "Front" or "Master" is highlighted at the bottom. Then try your volume and mute keys.
Right, that is exactly how it is set, as I mentioned in the first post. 

I am not sure after which updates my buttons stopped working, since I don't use them very often.  After trying to use the mute button and finding it didn't work, I tried the others and found that Audio and Video had also stopped working. 

Also, when I press the mute button, the little window pops up showing the speaker icon, but it does not actually mute -- sound stays on every time I press the button even though the pop-up picture toggles between muted and un-muted.  :confused:  I hadn't tested the volume keys until now ( Fn-F7 and Fn-F8 ), but they aren't working either :( The popup window shows the volume changing, but it doesn't actually change.

---

### Post by thomasaaron on 2007-10-10
**_WOW Buttons:_**

OK, I checked, and the System 76 driver definitely configures the wow buttons.

Run the driver again. Make sure you click the "restore" tab and the "restore" button. The install tab and button will not do the magic. Then reboot your computer and try the buttons. Just for the sheer joy of it. :)

If that does not work:

1. What software have you downloaded since you've had the computer. It is possible that something has re-defined the hotkey setup.
2. Post the System 76 Driver version: Open the driver and click "About"
[B][U]
Sound:[/U][/B]

3. Post the output of: cat /proc/asound/version
4. Post the output of: cat etc/modprobe.d/alsa-base | tail -10

---

### Post by octathlon on 2007-10-10
OK ...
I ran the driver again - Restore tab, Restore button, and rebooted.  Tried buttons and they are still not working.  all symptoms same as described before.

1.  Software I have downloaded: Sun Java 6, Flash plugin for Firefox, Audacity, gPodder, Notecase, Chinese language support, and some games: Anagramarama, Billiard-GL, Gweled, PySol, and Xmoto (which I haven't even tried yet, heh).

2. System76 driver version = 2.0.9

3. Output of cat /proc/asound/version
```

gjd@PANG-LT2:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.14.
Compiled on Oct 10 2007 for kernel 2.6.20-16-generic (SMP).

```

4. Output of cat /etc/modprobe.d/alsa-base | tail -10
```

gjd@PANG-LT2:~$ cat /etc/modprobe.d/alsa-base | tail -10
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel model=toshiba
options snd-hda-intel model=toshiba
options snd-hda-intel model=toshiba
options snd-hda-intel model=toshiba
options snd-hda-intel model=toshiba
options snd-hda-intel model=toshiba
gjd@PANG-LT2:~$ 

```

thx ...

---

### Post by thomasaaron on 2007-10-11
Let's take this one to email. (support<at>system76<dot>com).

I'd like for you to manually run the commands that set up those keys one at a time.
The commands may throw an error that will help us to isolate the problem.

Also, it might fix the Mute key problem as well.

---

### Post by octathlon on 2007-10-11
Thanks, I'll email you as soon as I get home -- that'll be around 3:50pm your time (personal email is blocked at my workplace).

---

### Post by octathlon on 2007-10-12
I emailed you yesterday ...
Is there a log file I can look at to see if there were error messages?

Or, maybe just post the commands I should try here on the forum?

---

### Post by thomasaaron on 2007-10-12
I did not see the email.
Could you please re-send?

---

### Post by thomasaaron on 2007-10-12
Jeesh. I see from another thread that you are running 64-bit. Wouldn't surprise me if that's the reason the buttons are not working with the System 76 driver.

I'll post where you can find the commands in the other thread.

---

### Post by octathlon on 2007-10-12
No, I am NOT running 64-bit.  As I said, I am running exactly what was pre-installed plus all updates that have come across.  You must be confusing me with someone else. :confused:

---

### Post by octathlon on 2007-10-14
UPDATE:

I logged on as a different user and the hardware buttons were working properly under that login!

So I assume my normal user login must have a setting in some config file in my /home directory causing the problem.  But, how can I figure out which one it is?

edit: Even though the wow/mute buttons are separate from the keyboard keys, some things  that could affect my keyboard settings: I use  "US English Alternative International" keyboard in addition to normal US/English keyboard.  Also, I have SCIM set up for Chinese input, which I am more doubtful would affect my keyboard settings, since it uses whatever default keyboard as input.

---

### Post by thomasaaron on 2007-10-15
gconf-editor may contain some clues.
You might also try System > Preferences > Keyboard shortcuts and just re-program those keys.

Also, it might be interesting to configure another user account the same way as the problematic one is configured -- one step at a time to find out which/if one of the alternate settings you are using is hosing the WOW buttons.

---

### Post by octathlon on 2007-10-15
I was looking around in gconf-editor last night and didn't see anything suspicious...

The shortcut keys are still set up correctly; in fact, if you press mute, vol up, or vol down, you see the little display in the bottom-center of the screen that indicates it is attempting to do the defined action (shows volume bar going up or down for example) -- but volume does not change in reality.  I tried re-defining the shortcuts in system>preferences>keyboard shortcuts just in case, but it had no effect.

I'll try your suggestion of re-creating my configuration changes on another account and report back on what happens.

Thx,

---

### Post by octathlon on 2007-10-15
UPDATE:

I created a couple of new users (non-admin) for testing.  WOW and Mute/Volumes worked for them.  

SCIM is available for all users and works fine, can switch back and forth between English and Chinese with no problems.

I got the Wow buttons to stop working as follows:

Under the test user I did System>Preferences>Keyboard; on Layouts tab, clicked Add, added U.S. English International (with dead keys); then closed the dialog.  Opened text editor and verified that the new layout worked.  After logging the test user out and back in, Wow buttons for Audio and Video no longer worked.

Mute button and Volume keys (Fn+F7 and Fn+F8 ) still worked.  [I tried all the config changes I could think of that I had made under original login, including enabling and playing with Accessibility>Assistive Technology preferences, but nothing ever caused them to stop working].

In the test login, I went back into system>preferences>keyboard and deleted the keyboard layout I had added.  I logged out and back in, Wow buttons still did not work.  I logged out and back into my normal login, and ran the System76 driver - Restore, then rebooted.  I logged back into the test login, but Wow buttons still did not work.

EDIT: Then I tried redefining the shortcut keys again under system>preferences>keyboard shortcuts.  Volume and mute did not work, but Launch Audio player **did **work, so now I have the Wow Audio working again!!, but I couldn't find a listing for Launch Video player to try and redefine that one.  So at this stage, on my normal user login: Wow Audio works, Wow video does not, Mute does not, Fn+6,7,8 do not.  And on the test login I also got Wow audio working again by manually redefining the shortcut key.

P.S.
During all the logging in and out and rebooting I did, I noticed some other problems with that #$!@ Network Manager, but as Scarlett said, I won't think about that today, I'll think about that tomorrow, heh.

---

### Post by thomasaaron on 2007-10-16
OK. Good testing.

The one thing (as best I can tell, based on the fact that I've not yet had my coffee this morning) that you did NOT test was:

* Deleting the troublesome configuration in your MAIN account
* Run System 76 Driver.
* Reboot

Running the driver in your main account probably won't fix the problem in your test account. I think they use different configuration files.

Ultimately, I think you have two choices:
1. Choose between your custom configuration and your WOW buttons (this is beginning to sound like an Ubuntu bug)
2. Create an account in which you would use your WOW buttons and one in which you would use your custom configurations (ridiculous, I know -- and inconvenient) 

Obviously, the commands in the System 76 driver that configure the buttons will not work alongside your custom configuration. So, running them outside of the System 76 driver will not help either.

And your choice is... :)

---

### Post by kperkins on 2007-10-16
> **octathlon said:**
> I was looking around in gconf-editor last night and didn't see anything suspicious...

The shortcut keys are still set up correctly; in fact, if you press mute, vol up, or vol down, you see the little display in the bottom-center of the screen that indicates it is attempting to do the defined action (shows volume bar going up or down for example) -- but volume does not change in reality.  I tried re-defining the shortcuts in system>preferences>keyboard shortcuts just in case, but it had no effect.

I'll try your suggestion of re-creating my configuration changes on another account and report back on what happens.

Thx,
For the volume controls try going to System > Preferences > sound and make sure that Front is selected down at the bottom for devices to control with the keyboard.

---

### Post by octathlon on 2007-10-16
OK ... The mystery of the WOW buttons is now solved, but still not even close to solving the Mute button/Fn+6,7,8 volume keys mystery.

On the WOW buttons: Simply deleting the new keyboard layout and S76 restore did not work.  If you look at gconf-editor, under Desktop>Gnome>peripherals>keyboard>kbd, on a user who has never modified the layouts, the settings for layouts and grp are blank, but once you've added a layout, the layout lists your layouts and grp lists your groups, and even if you delete the extra one(s), "us" is still listed in layouts and the grp entry remains.  I deleted those so everything was blank again, reran the S76 restore/reboot, and this time the WOW audio/video buttons started working again.  BTW, running the restore from my main login was enough to fix the test login's buttons too, once its gconf settings were reset.

But under my main login, even after doing all that, I **still don't ** have any of the volume control stuff fixed.  :(  And I still have not been able to recreate breaking them in the test login.  But whatever it was, it apparently wasn't any of my keyboard setting changes...

EDIT @kperkins: Yeah, Front is what I had selected as the device to control ;) thx

EDIT2:  Tom, since you are testing Gutsy this week, are you going to test adding a keyboard layout and see what happens?  :) (Not being very gutsy myself, I plan to wait a little while after the release, see what issues come up and until the new Systeme76 driver is out and if you're going to release a custom CD like you did with Feisty for the Santa Rosas)

---

### Post by thomasaaron on 2007-10-17
Yes, I'll try to test that. I'm betting though that the sound function keys are also messed up by something that was done somewhere along the line to your keyboard configurations.  Here's why: We don't do ANYTHING to support those. They work out of the box with Ubuntu.

One thing I wasn't clear on: Do the sound buttons work for a test user account that has not been modified?

---

### Post by octathlon on 2007-10-17
Yes, sound buttons work on an unmodified test account, and even the test account I was modifying left and right, still had working sound buttons.  I will have to keep looking and see if I can figure out what broke them on my main account.  

Adding a new keyboard layout only broke the 2 WOW buttons.  Looks like an easy workaround for that is to just reassign the shortcuts for them manually.  I did that successfully with WOW Audio using the Keyboard Shortcut dialog.  But since "Launch movie player" is not listed there, I couldn't assign the WOW Video button to it that way.  -- Can you tell me another way to do it, maybe using the command line or gconf-editor?

Thanks

---

### Post by thomasaaron on 2007-10-17
> Yes, sound buttons work on an unmodified test account, and even the test account I was modifying left and right, still had working sound buttons. I will have to keep looking and see if I can figure out what broke them on my main account.

OK, good. So that rules out a hardware problem.

> Adding a new keyboard layout only broke the 2 WOW buttons. Looks like an easy workaround for that is to just reassign the shortcuts for them manually. I did that successfully with WOW Audio using the Keyboard Shortcut dialog. But since "Launch movie player" is not listed there, I couldn't assign the WOW Video button to it that way. -- Can you tell me another way to do it, maybe using the command line or gconf-editor?

I'll see what I can figure out.

---

### Post by octathlon on 2007-10-25
Arrrgh ... SOLVED!

Yeah, I had already checked many times that the Volume Control preferences were set to control device "Front".  Well, I just happened to stumble upon ANOTHER place where this is specified: System>Preferences>Sound - Devices tab.  Yep, in this other place, the setting was on Capture instead of Front!  

I changed that one to Front and the keys work again.  Two different settings for the same thing, who'd a thunk it :confused:

 :popcorn:

---

