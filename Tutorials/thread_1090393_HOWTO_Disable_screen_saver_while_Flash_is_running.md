---
title: "HOWTO: Disable screen saver while Flash is running"
date: 2009-03-08
forum: Tutorials
---

### Post by sdennie on 2009-03-08
**Summary**
When playing Flash video in Firefox, the screen saver is not disabled and so you are required to move your mouse every few minutes to prevent the screen saver from turning on.  This is highly annoying.  This guide provides a method to automatically disable the screen saver whenever Flash is being used in Firefox.

Note: This method disables the screen saver regardless of what type of Flash program is running.  It doesn't discriminate between a Youtube video and a Punch the Monkey ad.

**Implementation**
We are going to create a daemon that detects if the Flash shared library currently has any memory mapped.  If it does, we disable the screen saver.  If it doesn't, and we know that we previously disabled the screen saver, we turn it back on.  First, we need to make sure we have a local bin directory:

```

mkdir -p ~/bin

```

Next, save the following script as ~/bin/flash_saver.sh:

```

#!/bin/bash

# Cleanup any bad state we left behind if the user exited while flash was
# running
gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type bool true

we_turned_it_off=0

while true; do
    sleep 60
    flash_on=0

    for pid in `pgrep firefox` ; do
        if grep libflashplayer /proc/$pid/maps > /dev/null ; then
            flash_on=1
        fi
        
        ss_on=`gconftool-2 -g /apps/gnome-screensaver/idle_activation_enabled`

        if [ "$flash_on" = "1" ] && [ "$ss_on" = "true" ]; then
            gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled \
                --type bool false
            we_turned_it_off=1
        elif [ "$flash_on" = "0" ] && [ "$ss_on" = "false" ] \
                && [ "$we_turned_it_off" = "1" ]; then
            gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled \
                --type bool true
            we_turned_it_off=0
        fi

    done
done

```

Next, we make the script executable:

```

chmod +x ~/bin/flash_saver.sh

```

Now, we can turn it on by pressing F2 and running, "~/bin/flash_saver.sh".  You can now either test it watching some Flash videos or just proceed to System->Preferences->Session and adding "flash_saver.sh" as one of your startup programs.

**Testing**
Watch some long Flash videos and verify that screen saver doesn't come on.  Afterwards, close all tabs that have any Flash content on them and see if the screen saver now comes on as normal.

---

### Post by binbash on 2009-03-09
thanks, it is very handy when watching movies

---

### Post by jackmcslay on 2009-03-09
which part of this script I need if I just need a terminal command to disable the screen saver?

---

### Post by jkernsjr on 2009-03-09
sdennie, fantastic job with the script..thanks! One problem though. All parts of script seem to work except when I no longer have flash playing, or even close the browser all together, screensaver will not enable itself back to on?

jackmcslay, see my post #7 here: [http://ubuntuforums.org/showthread.php?p=6858013#post6858013](http://ubuntuforums.org/showthread.php?p=6858013#post6858013)

---

### Post by sdennie on 2009-03-14
> **jkernsjr said:**
> sdennie, fantastic job with the script..thanks! One problem though. All parts of script seem to work except when I no longer have flash playing, or even close the browser all together, screensaver will not enable itself back to on?

jackmcslay, see my post #7 here: [http://ubuntuforums.org/showthread.php?p=6858013#post6858013](http://ubuntuforums.org/showthread.php?p=6858013#post6858013)

I'm not sure what would cause this unless some other application has turned off the screen saver.  The script goes out of its way to not touch things if something else has changed the settings.  The other possibility is that you have some hung firefox process somewhere that is using flash but you can't see it.

---

### Post by h2o4444 on 2009-03-18
Thank you very much for this How-To but I don't know how to write codes and using the command line is no natural to me. I'm going to wait for Ubuntu 9.04 to come out and hope that this problem is solved in that version. Also this problem doesn't only occur in Flash, it occurs whenever I'm watching a video (full screen or not) such as on youtube, or just a regular mpg or avi file.

---

### Post by aktiwers on 2009-03-18
Will do this when I get home..  this really should be default setting IMO

---

### Post by Thelasko on 2009-03-18
Any way to only do this only while flash is in full screen, or only on certain websites?

Good work by the way!

---

### Post by sdennie on 2009-04-07
Didn't notice these questions.  Sorry for the late replies:

> **jackmcslay said:**
> which part of this script I need if I just need a terminal command to disable the screen saver?

To disable:

```

gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type bool false

```

To enable:

```

gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type bool false

```

> **Thelasko said:**
> Any way to only do this only while flash is in full screen, or only on certain websites?

Good work by the way!

You should be able to.  It's a bit more work than I'm willing to put into it but, here is a snippet I've pulled out of another script I wrote that only does stuff when a window named "foo" is active:

```

    active_win_line=$(xprop -root | grep "_NET_ACTIVE_WINDOW(WINDOW)")
    active_win_id="${active_win_line:40}"
    
    if xwininfo -id $active_win_id | grep "foo" > /dev/null ; then
        # Do stuff
    fi

```

---

### Post by Boppy3125 on 2009-05-11
I don't know if you are still watching this thread but I am having some difficulty with this.  It looks like the script is working and setting the gconftool-2 setting correctly but the screen saver is still starting.  I am running MythBuntu 8.10, pretty much vanila.  I have the screen saver set to start after like 2 minutes.  MythTV correctly stops it from activating.  Here is the output from some commands while firefox has a hulu program playing and the screensaver is running.  (I got these out of a putty session connected.)
```
curt@media1:~$ ps -A | grep flash_saver.sh
 5908 ?        00:00:00 flash_saver.sh
curt@media1:~$ pgrep firefox
17662
curt@media1:~$ grep libflashplayer /proc/17662/maps
b0990000-b12e2000 r-xp 00000000 08:01 724861     /usr/lib/adobe-flashplugin/libflashplayer.so
b12e2000-b1316000 rw-p 00951000 08:01 724861     /usr/lib/adobe-flashplugin/libflashplayer.so
curt@media1:~$ gconftool-2 -g /apps/gnome-screensaver/idle_activation_enabled
false

```

Now, that last setting never seems to go back to true, is that a problem?  Anyone see anything obviously wrong?

--
[edit - research at work]
Looks like it is possible Mythbuntu based on Xbuntu uses xscreensaver instead of gnome-screensaver.  It looks like simply executing "xscreensaver-command -deactivate" periodically may provide a simulated mouse/keyboard movement.  Issuing this every 60 seconds while flash is active could be an easy modification to that script.  I will try changing it and report back when I have the chance to try this.

---

### Post by Boppy3125 on 2009-05-15
Well, it is weird.  I do have the gnome-screensaver.  I have the original script in place.  It doesn't seem like it worked right in testing, it definitely seemed as though any interaction using putty was making it less predictable.  Even taking that out of the equation, after shutting down firefox, the script properly changes idle_activation_enabled setting back to true, but then the screensaver doesn't seem to come back on.

Then I gave up with it in that state, next day I noticed the screensaver seems to be working.  So I guess it is working.

---

### Post by rfourie on 2009-07-10
Hi, after much searching of the net/forums/mailinglists/etc, I managed to find a way to determine if the current window is full screen. I haven't tested it extensively, so your results may vary, but I think it's relatively robust. I've also changed some of the variables to make it a bit more generic (and added a test for xine, my default dvd/movie player), and also turned off sleep/hibernate.

```

#!/bin/bash

# cleanup any bad state we left behind if the user exited while flash was running
gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type bool true

turn_it_off=0
sleepcomputer0=`gconftool-2 -g /apps/gnome-power-manager/timeout/sleep_computer_ac`
sleepdisplay0=`gconftool-2 -g /apps/gnome-power-manager/timeout/sleep_display_ac`

while true; do
	sleep 60
	SS_off=0
	
	# check to see if flashplayer is being used by firefox
	for pid in `pgrep firefox` ; do
		if grep libflashplayer /proc/$pid/maps > /dev/null ; then
			SS_off=1
		fi
	done
	
	# check to see if xine is being used
	if pgrep xine > /dev/null; then
		SS_off=1
	fi

	# check to see if current application is fullscreen	
	current_window_id=`xprop -root | grep "_NET_ACTIVE_WINDOW(WINDOW)" | cut -d" " -f5`
	if xprop -id $current_window_id | grep "_NET_WM_STATE_FULLSCREEN" > /dev/null; then
		SS_off=1
	fi

	# read current state of screensaver
	ss_on=`gconftool-2 -g /apps/gnome-screensaver/idle_activation_enabled`
	
	# change state of screensaver as necessary
	if [ "$SS_off" = "1" ] && [ "$ss_on" = "true" ]; then
		gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type bool false
		gconftool-2 -s /apps/gnome-power-manager/timeout/sleep_computer_ac --type int 0
		gconftool-2 -s /apps/gnome-power-manager/timeout/sleep_display_ac --type int 0
		turn_it_off=1
	elif [ "$SS_off" = "0" ] && [ "$ss_on" = "false" ] && [ "$turn_it_off" = "1" ]; then
		gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type bool true
		gconftool-2 -s /apps/gnome-power-manager/timeout/sleep_computer_ac --type int $sleepcomputer0
		gconftool-2 -s /apps/gnome-power-manager/timeout/sleep_display_ac --type int $sleepdisplay0
		turn_it_off=0
	fi

done

```

---

### Post by Thelasko on 2009-07-10
Thanks, I'll have to give that a try.

---

### Post by Thelasko on 2009-07-11
I gave the new script a try.  Unfortunately, it still works whenever flash is running, and not just while in full screen.  I'll try to take a look at it and figure out what's wrong.

---

### Post by rfourie on 2009-07-12
> **Thelasko said:**
> I gave the new script a try.  Unfortunately, it still works whenever flash is running, and not just while in full screen.  I'll try to take a look at it and figure out what's wrong.

Thelasko, do you mean that it doesn't disable the screensaver when flash is running, or that it doesn't disable the screensaver when the current application is full screen, or both?

---

### Post by Thelasko on 2009-07-12
> **rfourie said:**
> Thelasko, do you mean that it doesn't disable the screensaver when flash is running, or that it doesn't disable the screensaver when the current application is full screen, or both?

No, it works.  It's just that I was thinking it would disable the screensaver while flash was running **and** full screen.  However, the script is written so the screensaver is disabled while flash is running **or** an application is full screen.

I've made my own modification to the script.  It seems to work pretty well, but I'm aware of one bug.  It will disable the screensaver if flash is running and **any** application is full screen.

```
#!/bin/bash

# cleanup any bad state we left behind if the user exited while flash was running
gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type bool true

turn_it_off=0
sleepcomputer0=`gconftool-2 -g /apps/gnome-power-manager/timeout/sleep_computer_ac`
sleepdisplay0=`gconftool-2 -g /apps/gnome-power-manager/timeout/sleep_display_ac`

while true; do
	sleep 60
	SS_off=0
	
	# check to see if flashplayer is being used by firefox
	for pid in `pgrep firefox` ; do
		if grep libflashplayer /proc/$pid/maps > /dev/null ; then
	# check to see if current application is fullscreen	
	current_window_id=`xprop -root | grep "_NET_ACTIVE_WINDOW(WINDOW)" | cut -d" " -f5`
	if xprop -id $current_window_id | grep "_NET_WM_STATE_FULLSCREEN" > /dev/null; then
		SS_off=1
	fi
		fi
	done
	
	# check to see if xine is being used
#	if pgrep xine > /dev/null; then
#		SS_off=1
#	fi
#
#	# check to see if current application is fullscreen	
#	current_window_id=`xprop -root | grep "_NET_ACTIVE_WINDOW(WINDOW)" | cut -d" " -f5`
#	if xprop -id $current_window_id | grep "_NET_WM_STATE_FULLSCREEN" > /dev/null; then
#		SS_off=1
#	fi

	# read current state of screensaver
	ss_on=`gconftool-2 -g /apps/gnome-screensaver/idle_activation_enabled`
	
	# change state of screensaver as necessary
	if [ "$SS_off" = "1" ] && [ "$ss_on" = "true" ]; then
		gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type bool false
		gconftool-2 -s /apps/gnome-power-manager/timeout/sleep_computer_ac --type int 0
		gconftool-2 -s /apps/gnome-power-manager/timeout/sleep_display_ac --type int 0
		turn_it_off=1
	elif [ "$SS_off" = "0" ] && [ "$ss_on" = "false" ] && [ "$turn_it_off" = "1" ]; then
		gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type bool true
		gconftool-2 -s /apps/gnome-power-manager/timeout/sleep_computer_ac --type int $sleepcomputer0
		gconftool-2 -s /apps/gnome-power-manager/timeout/sleep_display_ac --type int $sleepdisplay0
		turn_it_off=0
	fi

done
```

Also note that I commented out the part about Xine.  I don't use Xine so I disabled it.  I might change that to work with Miro instead.

---

### Post by rfourie on 2009-07-12
Oh, cool. This is my first real fix and I'm a bit proud of it...
I did make it pretty generic for full-screen applications so that no matter what is playing full screen, it disables the screensaver. I might post to other threads about that part of the solution.

---

### Post by Lockheed on 2009-08-22
I was trying to adopt it to mplayer so my screen doesn't dim while playing movies but it didn't work. I modified two lines:
```
    for pid in `pgrep mplayer` ; do
        if grep smplayer /proc/$pid/maps > /dev/null ; then
            flash_on=1
```
but the screen still dims :/

---

### Post by Boppy3125 on 2009-08-23
Two thoughts without looking up anything.  Isn't MPlayer case sensitive?  Maybe that grep isn't.  Can't MPlayer do that with some command line switch?

Hope that at least gets you googling in the right direction.

---

### Post by Lockheed on 2009-08-24
Well, smplayer has such optionin the menus and I was already using it but with no effect. However, yesterday, this option starded to work spontaneously (after a month!) so I don't need the script anymore.

---

### Post by Gen2ly on 2009-08-24
This script doesn't detect flash but will suspend the screen saver for KDE 4, disable xorg server blanking, and disable dpms.

```
#!/bin/bash
# screenblank - Toggle screen blanking/powersaving/screensaver on/off in KDE 4.
# Useful for when watching movies...

# Tests for X server blanking / Monitor blanking
xblanktest=$(xset -q | grep timeout | awk '{printf $2}')
dpmstest=$(xset -q | grep "  DPMS is Enabled")

if [[ "$xblanktest" -gt 0 ]] || [[ -n "$dpmstest" ]]; then
  # Turn off X blanking, Monitor blanking
  xset s off; xset -dpms
  # Supend screensaver
  echo '#!/bin/bash'  >  /tmp/suspend-dbus-screensaver
  echo 'while :'      >> /tmp/suspend-dbus-screensaver
  echo 'do'           >> /tmp/suspend-dbus-screensaver
  echo 'qdbus org.freedesktop.ScreenSaver /ScreenSaver SimulateUserActivity' \
                      >> /tmp/suspend-dbus-screensaver
  echo 'sleep 119'    >> /tmp/suspend-dbus-screensaver
  echo 'done'         >> /tmp/suspend-dbus-screensaver
  chmod u+x /tmp/suspend-dbus-screensaver
  nohup "/tmp/suspend-dbus-screensaver" &> /dev/null &
  echo " - Disabled screen blanking, powersaving, and screensaver"; else
  # Resume X blanking, Monitor blanking
  xset s on; xset +dpms
  # Resume screensaver
  pkill suspend-dbus
  echo " + Enabled screen blanking and powersaving, and screensaver"
fi

# Limitations:
#  Unable to tell if screensaver is active
#   qdbus org.freedesktop.ScreenSaver /ScreenSaver GetActive  always returns
#   false
#  Enables both X server blanking and DPMS even if one is orginally turned off
```

---

### Post by rvm4000 on 2009-08-25
> **Lockheed said:**
> Well, smplayer has such optionin the menus and I was already using it but with no effect. However, yesterday, this option starded to work spontaneously (after a month!) so I don't need the script anymore.

From the smplayer FAQ:
> 
21. The screensaver doesn't turn off, why? 

 If you use a recent version of MPlayer you may need to add a line like this in your ~/.mplayer/config: 
 (gnome) 
heartbeat-cmd="gnome-screensaver-command -p &>/dev/null"
 (kde) 
heartbeat-cmd="dcop kdesktop KScreensaverIface enable false &>/dev/null && dcop kdesktop KScreensaverIface enable true &>/dev/null"
Please take a look at the MPlayer manpage for more info.


---

### Post by Lockheed on 2009-08-25
> **rvm4000 said:**
> From the smplayer FAQ:

I will try that cause the dimming is back again for no apparent reason.

---

### Post by Whoopie on 2009-09-17
Hi,

there's also a new project called [Caffeine]("https://code.launchpad.net/caffeine").

Best regards,
Whoopie

---

### Post by Thelasko on 2009-09-29
I've been having some trouble with the script not exiting cleanly.  Basically, when I close a Flash movie the screen saver remains disabled.

Does anybody have any suggestions to fix this?

---

### Post by Thelasko on 2009-09-30
What is the while loop for?  Why does it say "while true"  while what is true?

Edit: Nevermind
> Note the use of the true statement. This means: continue execution until we are forcibly interrupted (with kill or Ctrl+C).

---

### Post by Thelasko on 2009-09-30
I think I fixed it!

```
#!/bin/bash

# cleanup any bad state we left behind if the user exited while flash was running
gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type bool true

turn_it_off=0
sleepcomputer0=`gconftool-2 -g /apps/gnome-power-manager/timeout/sleep_computer_ac`
sleepdisplay0=`gconftool-2 -g /apps/gnome-power-manager/timeout/sleep_display_ac`

while true; do
	sleep 60
	SS_off=0
	
	# check to see if flashplayer is being used by firefox
	for pid in `pgrep firefox` ; do
		if grep libflashplayer /proc/$pid/maps > /dev/null ; then
		# check to see if current application is fullscreen	
		current_window_id=`xprop -root | grep "_NET_ACTIVE_WINDOW(WINDOW)" | cut -d" " -f5`
			if xprop -id $current_window_id | grep "_NET_WM_STATE_FULLSCREEN" > /dev/null; then
			SS_off=1			
		fi
	fi
	done
	
	# check to see if xine is being used
	if pgrep miro > /dev/null; then
		current_window_id=`xprop -root | grep "_NET_ACTIVE_WINDOW(WINDOW)" | cut -d" " -f5`
		if xprop -id $current_window_id | grep "_NET_WM_STATE_FULLSCREEN" > /dev/null; then
			SS_off=1
		fi
	fi
#
#	# check to see if current application is fullscreen	
#	current_window_id=`xprop -root | grep "_NET_ACTIVE_WINDOW(WINDOW)" | cut -d" " -f5`
#	if xprop -id $current_window_id | grep "_NET_WM_STATE_FULLSCREEN" > /dev/null; then
#		SS_off=1
#	fi

	# read current state of screensaver
	ss_on=`gconftool-2 -g /apps/gnome-screensaver/idle_activation_enabled`
	
	# change state of screensaver as necessary
	if [ "$SS_off" = "1" ] && [ "$ss_on" = "true" ]; then
		gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type bool false
		gconftool-2 -s /apps/gnome-power-manager/timeout/sleep_computer_ac --type int 0
		gconftool-2 -s /apps/gnome-power-manager/timeout/sleep_display_ac --type int 0
		turn_it_off=1
#	I think this is the problem.  Some states are not accounted for, so we use else instead
#	elif [ "$SS_off" = "0" ] && [ "$ss_on" = "false" ] && [ "$turn_it_off" = "1" ]; then
	else
		gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type bool true
		gconftool-2 -s /apps/gnome-power-manager/timeout/sleep_computer_ac --type int $sleepcomputer0
		gconftool-2 -s /apps/gnome-power-manager/timeout/sleep_display_ac --type int $sleepdisplay0
		turn_it_off=0
	fi

done
```

edit: Never mind, this doesn't work at all.

---

### Post by javajesse on 2009-11-19
Its a manual click, but I use the Inhibit Applet on the Panel.  Quick and easy to disable / enable screensaver & sleep.

---

### Post by Thelasko on 2009-11-19
If you can get it to work, Hulu Desktop automatically disables the screen saver.

---

### Post by bassliu on 2009-12-20
doesn't work with google chrome. but it still great script

---

### Post by brott8 on 2009-12-26
Just wanted to say that post #16 from TheLasko worked like a charm.  Huge thanks as this was a big gripe of mine.

---

### Post by Thelasko on 2009-12-28
> **brott8 said:**
> Just wanted to say that post #16 from TheLasko worked like a charm.  Huge thanks as this was a big gripe of mine.

Thanks, I'm still using that version of the script as well.  I do have some occasional problems with it though.  Sometimes the screensaver doesn't seem to resume after I close flash from full screen.  I haven't been able to resolve that issue.

---

### Post by produnis on 2010-01-30
> **Thelasko said:**
> Thanks, I'm still using that version of the script as well.  I do have some occasional problems with it though.  Sometimes the screensaver doesn't seem to resume after I close flash from full screen.  I haven't been able to resolve that issue.
same here, after the script has run for one time, suspend does not work at all...
everything seems to be set right, but nevertheless, my PC doesnt go to suspend at all..

If i click "suspend" with my mouse, then it does...
but no longer automatically...
:(

---

### Post by fa2k on 2010-05-25
> **javajesse said:**
> Its a manual click, but I use the Inhibit Applet on the Panel.  Quick and easy to disable / enable screensaver & sleep.

This is a nice solution.. :) I would think that this would be done "properly" in the flash plugin sooner or later, but this works well for the moment.

---

### Post by abuster on 2011-05-18
I've edited the script from post #16, so that it works for Chrome, Opera or whatever browser which use libflashplayer. It checks to see if the window in focus is the flashplayer(flashplayer is in focus when flashplayer are running in full screen). This way, commercials or other flash content, will not disable the screen saver(when the program in focus are running full screen, which might be another program). A video which is not in full screen, will not disable the screen saver either. Not sure how to test this(seen some scripts which looks for a file in /tmp, but it doesn't always work.) But hey, if I'm watching a video over several minutes, I'm probably having it blown up full screen.

I've also changed the "sleep 60" to "sleep 30", for those who have set the screen saver time limit to 60 seconds. The rest should be the same.

```

#!/bin/bash

# cleanup any bad state we left behind if the user exited while flash was running
gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type bool true

turn_it_off=0
sleepcomputer0=`gconftool-2 -g /apps/gnome-power-manager/timeout/sleep_computer_ac`
sleepdisplay0=`gconftool-2 -g /apps/gnome-power-manager/timeout/sleep_display_ac`

# run loop forever
while true; do
  # interval between checks
  sleep 30
  SS_off=0
  # make id variable of window in focus
  current_window_id=`xprop -root | grep "_NET_ACTIVE_WINDOW(WINDOW)" | cut -d" " -f5`
  # make pid array of every command with libflashplayer in full(-f) command
  for pid in `pgrep -f libflashplayer` ; do
    # check if window in focus is our libflashplayer
    if [ $pid == `xprop -id $current_window_id | grep PID | cut -d" " -f3` ]
      then SS_off=1
    fi
  done

# check to see if xine is being used
#  if pgrep xine > /dev/null; then
#    SS_off=1
#  fi
#
# check to see if current application is fullscreen
#  current_window_id=`xprop -root | grep "_NET_ACTIVE_WINDOW(WINDOW)" | cut -d" " -f5`
#  if xprop -id $current_window_id | grep "_NET_WM_STATE_FULLSCREEN" > /dev/null; then
#    SS_off=1
#  fi

  # read current state of screensaver
  ss_on=`gconftool-2 -g /apps/gnome-screensaver/idle_activation_enabled`

  # change state of screensaver as necessary
  if [ "$SS_off" = "1" ] && [ "$ss_on" = "true" ]; then
    gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type bool false
    gconftool-2 -s /apps/gnome-power-manager/timeout/sleep_computer_ac --type int 0
    gconftool-2 -s /apps/gnome-power-manager/timeout/sleep_display_ac --type int 0
    turn_it_off=1
  elif [ "$SS_off" = "0" ] && [ "$ss_on" = "false" ] && [ "$turn_it_off" = "1" ]; then
    gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type bool true
    gconftool-2 -s /apps/gnome-power-manager/timeout/sleep_computer_ac --type int $sleepcomputer0
    gconftool-2 -s /apps/gnome-power-manager/timeout/sleep_display_ac --type int $sleepdisplay0
    turn_it_off=0
  fi
done

```Happy watching youtube, vimeo and whatever flash movie :popcorn:

---

### Post by Super R on 2011-06-02
First of all, this script is great!!! This is a fairly old thread so I am not sure if anyone is still interested. BUT I had the problem where gnome-screensaver does not come back on after returning from full screen.

I believe that I have found a sloppy fix for this. Keep in mind that I am using this script for ALL fullscreen windows rather than for fullscreen flash windows. I don't think it matters, just thought I would mention it.

Adding the following line after the screensaver value returns to true seems to work every time.

```
gnome-screensaver-command -a
```

The only downside to this would be that the screensaver comes on as soon as the value is set to true rather than waiting for your screensaver to activate on its own.

Anyway, here is the code I use. A couple things didn't apply to my setup so I commented them out. Thank you so much for posting this as it is a huge annoyance that is now solved for me :)

```
#!/bin/bash

# cleanup any bad state we left behind if the user exited while flash was running
gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type bool true

turn_it_off=0
#sleepcomputer0=`gconftool-2 -g /apps/gnome-power-manager/timeout/sleep_computer_ac`
#sleepdisplay0=`gconftool-2 -g /apps/gnome-power-manager/timeout/sleep_display_ac`

# run loop forever
while true; do
  # interval between checks
  sleep 30
  SS_off=0
  # make id variable of window in focus
  #current_window_id=`xprop -root | grep "_NET_ACTIVE_WINDOW(WINDOW)" | cut -d" " -f5`
  # make pid array of every command with libflashplayer in full(-f) command
  #for pid in `pgrep -f libflashplayer` ; do
    # check if window in focus is our libflashplayer
    #if [ $pid == `xprop -id $current_window_id | grep PID | cut -d" " -f3` ]; then 
    	#SS_off=1
    #fi
  #done

# check to see if vlc is being used
#  if pgrep vlc > /dev/null; then
#    SS_off=1
#  fi
#
# check to see if current application is fullscreen
  current_window_id=`xprop -root | grep "_NET_ACTIVE_WINDOW(WINDOW)" | cut -d" " -f5`
  if xprop -id $current_window_id | grep "_NET_WM_STATE_FULLSCREEN" > /dev/null; then
    SS_off=1
  fi

  # read current state of screensaver
  ss_on=`gconftool-2 -g /apps/gnome-screensaver/idle_activation_enabled`

  # change state of screensaver as necessary
  if [ "$SS_off" = "1" ] && [ "$ss_on" = "true" ]; then
    gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type bool false
    #gconftool-2 -s /apps/gnome-power-manager/timeout/sleep_computer_ac --type int 0
    #gconftool-2 -s /apps/gnome-power-manager/timeout/sleep_display_ac --type int 0
    turn_it_off=1
  elif [ "$SS_off" = "0" ] && [ "$ss_on" = "false" ] && [ "$turn_it_off" = "1" ]; then
    gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type bool true
    gnome-screensaver-command -a
    #gconftool-2 -s /apps/gnome-power-manager/timeout/sleep_computer_ac --type int $sleepcomputer0
    #gconftool-2 -s /apps/gnome-power-manager/timeout/sleep_display_ac --type int $sleepdisplay0
    turn_it_off=0
  fi
done
```

---

### Post by abuster on 2011-06-03
> **Super R said:**
> First of all, this script is great!!! This is a fairly old thread so I am not sure if anyone is still interested. 

I am aware of the oldness of this thread, but as many others, this is still a immense annoyance in Ubuntu/Linux Mint(at least in LM 10, as I am using).

I think this is because there isn't a "right" way of doing it. libflashplayer should not have rights to change screensavers settings on it's own(security), libflashplayer is closed source, and so on. And the problem falls into the bike-shed category(a must read: [http://www.bikeshed.com/](http://www.bikeshed.com/)).

Still, this is the thread that you will find, if you search for "disable screen saver flash ubuntu". I think the first post should be edited to reflect that, reading through all the pages is time taking(I know, anything worth knowing, is time taking). Anyhow, this is such a thing that I expect to "just work". I'm not sure if there is some administrative restrictions to editing the first post?

And, yes, thanks for your input, Super R.

---

### Post by Super R on 2011-06-07
Hello again. After playing with the script in my last post for a while, I was experiencing strange behaviour when I would wake up the screensaver after a cycle...it would go right back to sleep again. Waking it up the second time did the trick, but it was a slight annoyance. So I decided to try a different approach and use gnome-screensaver-command to inhibit the screensaver. I thought that it may be a "better way" to do this whole thing.

Below you will find a revised script (again) that uses gnome-screensaver-command to inhibit the screensaver when any window is fullscreen and kills gnome-screensaver-command when the window becomes regular again. It is the most perfect solution I have found so far (and I have been looking for a solution to this problem for 5 years) as it is automatic and care-free. Enjoy!!

```
#!/bin/bash

turn_it_off=0

while true; do
  sleep 30
  SS_off=0
 
  current_window_id=`xprop -root | grep "_NET_ACTIVE_WINDOW(WINDOW)" | cut -d" " -f5`
  if xprop -id $current_window_id | grep "_NET_WM_STATE_FULLSCREEN" > /dev/null; then
    SS_off=1
  fi

  pidof gnome-screensaver-command
  if [ "$SS_off" = "1" ] && [ $? -le 0 ] && [ "$turn_it_off" = "0" ]; then
  	gnome-screensaver-command -i &
  	turn_it_off=1  	
  elif [ "$SS_off" = "0" ] && [ "$turn_it_off" = "1" ]; then
  	killall gnome-screensaver-command
  	turn_it_off=0
  fi
done
```

---

### Post by Green_Star on 2011-08-20
Thanks Super R, your script works great.

---

### Post by Stray Wolf on 2011-09-10
I was wondering if this solution works fine in 10.04 and if it works like Totem does when it suppresses the screen saver.  Specifically, does the screen saver come back on if the video is paused?

---

### Post by Super R on 2011-09-10
Hi Stray Wolf, No is the answer to your question. The screensaver will turn off when a fullscreen window is in focus and turn back on when there is not a fullscreen window in focus.

---

### Post by trash on 2011-10-11
I think this might be a problem for the developers to figure out because using kde in lucid i have disabled the screensaver and disabled dimming in the power management performance scheme and still my screen blanks.. is anybody out there able to completely stop the screen from blanking? and if so how?

---

### Post by The Sorrow on 2011-10-12
Very useful! This will keep my screen from turning off when Im watching videos. Thanks!

---

### Post by Bu84Lhswr on 2011-10-16
Here is the solution.

This tiny script checks every ... seconds if the screen has changed enough to be a movie or something similar...
Have fun it works great.
Please excuse my bad speaking english, but i'm very tired ;-) (6:31 am in germany ...)

```

#!/bin/bash
# 
#
#Installation on Ubuntu (testet with 11.04)
#    sudo apt-get install imagemagick
#    chmod 755 <name and location of this script>
#    sh <name and location of this script> #or insert this line to "System -> Einstellungen -> Startprogramme" (autostart)



#time between checks in seconds
SLEEPTIME=10
#percentage of screen that have to be changed to poke the screensaver
#note that the clock and instant messengers notes could change often, so at least 5% should be used
PERCENTAGETOPOKE=25



#take first screenshot
import -window root stopscreensaver1.jpg
# infinite loop
while [ 1 -eq 1 ]
do
    #count of pixels
    WIDTH=$(identify -format "%w" stopscreensaver1.jpg)
    HEIGHT=$(identify -format "%h" stopscreensaver1.jpg)
    let PIXEL=$WIDTH*$HEIGHT

    #check every ... seconds
    sleep $SLEEPTIME

    #take compare-image
    import -window root stopscreensaver2.jpg

    #count of different pixels and the percentage
    DIFFERENCE=$(compare -dissimilarity-threshold 1 -metric AE stopscreensaver1.jpg stopscreensaver2.jpg stopscreensaverdifference.jpg 2>&1)
    let PERCENTAGE=$DIFFERENCE*100/$PIXEL

    #check if enough screen-area has changed
    if [ $PERCENTAGE -ge $PERCENTAGETOPOKE ]; then
            gnome-screensaver-command --poke
            echo "Scrennsaver poked at $PERCENTAGE of $PERCENTAGETOPOKE"
        else
            echo "Screensaver not poked at $PERCENTAGE of $PERCENTAGETOPOKE"
    fi

    #new compare image 
    rm -f stopscreensaver1.jpg
    mv -f stopscreensaver2.jpg stopscreensaver1.jpg
done

```

---

### Post by fightling on 2012-01-21
I inserted a parameter to your nice little script so that one can change the application it is looking for. That's useful for me, because I'm using prism instead of firefox for watching TV.

```
#!/bin/bash

# Cleanup any bad state we left behind if the user exited while flash was
# running
gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type bool true

we_turned_it_off=0

while true; do
    sleep 60
    flash_on=0

    # CHANGED THIS LINE:
    for pid in `pgrep $1` ; do
        if grep libflashplayer /proc/$pid/maps > /dev/null ; then
            flash_on=1
        fi
        
        ss_on=`gconftool-2 -g /apps/gnome-screensaver/idle_activation_enabled`

        if [ "$flash_on" = "1" ] && [ "$ss_on" = "true" ]; then
            gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled \
                --type bool false
            we_turned_it_off=1
        elif [ "$flash_on" = "0" ] && [ "$ss_on" = "false" ] \
                && [ "$we_turned_it_off" = "1" ]; then
            gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled \
                --type bool true
            we_turned_it_off=0
        fi

    done
done
```

---

### Post by amikrop on 2012-05-28
This wasn't even an issue in Ubuntu 10.10 and previous. Now it needs caffeine (which is not optimal as it is not an automated solution) or scripts like this. Maybe there should be a bug filed about this?

---

