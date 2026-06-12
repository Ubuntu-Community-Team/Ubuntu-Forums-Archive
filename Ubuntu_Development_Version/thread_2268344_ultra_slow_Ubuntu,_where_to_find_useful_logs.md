---
title: "ultra slow Ubuntu, where to find useful logs?"
date: 2015-03-08
forum: Ubuntu Development Version
---

### Post by enricobe on 2015-03-08
Hello,
today i'm gone biking leaving my Notebook (Ubuntu 15.04) on. 
There was one folder opened in nautilus, 2 inkscape windows in background and Firefox with 3 tabs. I've set Ubuntu to put the screen in standby after 10 mins.

When i came back (1:30 h) the screen was still on and the system was ultra-slow. I moved the mouse and the cursor has moved after 5-10 second doing the movement in 1-2 minutes! I was unable to close or open any windows, so i pressed CTRL+ALT+F1 which has opened a terminal in about 2 minutes.

From the terminal i've tried to login but when i have entered the username i was unable to enter the password and the terminal has returned a login timeout after 60 seconds.

I was going to do the shutdown holding down the power button for some seconds, but I&#8217;ve tried to blindly enter some commands in the terminal. I've tried to login, launch a ```
sudo reboot
``` and type my password. After 1-2 minutes the system rebooted. Now it works fine.

Where I can find useful logs? Could someone help me? Is it useful to investigate the problem or should I just forget it?

---

### Post by dino99 on 2015-03-08
if you boot with upstart (old default config), then ~/home/youruser/xorg.0.log and /var/log/* are the places to glance at.
if you already boot with systemd (systemd-sysv installed) then run: sudo journalctl

---

### Post by enricobe on 2015-03-08
Thank you. I wasn't using systemd.

I've found this on syslog. 
```
Mar  8 09:17:01 enrico-ubuntu CRON[10279]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar  8 09:17:28 enrico-ubuntu kernel: [ 6035.682423] perf interrupt took too long (2508 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
Mar  8 10:17:37 enrico-ubuntu CRON[10735]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
```
It seems strange, but i can't understand what it means and if it's a issue.

---

### Post by Doug S on 2015-03-08
That is not an abnormal log entry, I get similar:```
doug@s15:~/temp-k-git-3.10rc4/linux/Documentation/cpu-freq$ [COLOR=#ff0000]grep -A 1 -B 1 "perf interrupt" /var/log/syslog.1[/COLOR]
Mar  7 08:39:01 s15 CRON[21072]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Mar  7 09:00:11 s15 kernel: [223733.335881] perf interrupt took too long (2503 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
Mar  7 09:09:01 s15 CRON[12168]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
```It just means the particular interrupt took slightly longer than its default allotment:```
doug@s15:~/ubuntu-help$ [COLOR=#ff0000]cat /proc/sys/kernel/perf_event_max_sample_rate[/COLOR] 50000 
doug@s15:~/ubuntu-help$ [COLOR=#ff0000]cat /proc/sys/kernel/perf_cpu_time_max_percent[/COLOR] 25
```

---

### Post by grahammechanical on 2015-03-08
Is there a setting in BIOS that puts the machine in suspension or hibernation? Do you have enough swap space for suspend to disk? I am just trying wild guesses here. It sounds to me as if the UI has released memory and then is being slow at claiming it back.

On my desktop machine with 1 GB of RAM if I close Chromium then memory is quickly released but if I then switch workspaces the movement is slow and if I try to work with opened Libreoffice documents there is a delay before the cursor is moving at the normal speed.

I have System Load Indicator installed. So, I get a visual representation in an app-indicator of what is happening to memory. Earlier releases of Ubuntu held more tightly to memory and so made more use of swap. I have noticed this quick freeing up of memory from 14.04 onwards. I cannot blame the OS for my having only 1 GB of RAM.

Oh, I have just thought of another thing. Those Inkscape documents - do they automatically save the file at regular periods? Overlapping save file actions can put a strain on the CPU forcing it to task switch back and forth which in turn delays the completion of some actions, especially screen redraws. Now add in a background wallpaper that cycles through different wallpapers.

Regards.

---

### Post by VinDSL on 2015-03-08
> **enricobe said:**
> I've set Ubuntu to put the screen in standby after 10 mins[...]

Just a shot in the dark...  ;)

Are you 'suspending' or 'hibernating'?

Personally, I've never had any luck with 'hibernate' in Ubu et al.  It does what you're describing on every device I own.

'Suspend' always works like a charm.


**EDIT**


You might find this useful (or not):  [https://wiki.ubuntu.com/Power](https://wiki.ubuntu.com/Power)

Ubu 'hibernates' by default...

Extra credit reading:  [https://bugs.launchpad.net/ubuntu/+source/policykit-desktop-privileges/+bug/812394](https://bugs.launchpad.net/ubuntu/+source/policykit-desktop-privileges/+bug/812394)

---

### Post by sammiev on 2015-03-08
> **VinDSL said:**
> Just a shot in the dark...  ;)

Are you 'suspending' or 'hibernating'?

Personally, I've never had any luck with 'hibernate' in Ubu et al.  It does what you're describing on every device I own.

'Suspend' always works like a charm.

+1 to Suspend and the above post.

---

### Post by VinDSL on 2015-03-08
> **sammiev said:**
> +1 to Suspend and the above post.

Maybe we should explain how to do it...  ;)


First, edit this file.  Specify 'Yes' for everything and save:

```
sudo gedit /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla
```


And, if it's a laptop, edit the following:

```
sudo gedit /etc/systemd/logind.conf
```


Uncomment this line:

```
#HandleLidSwitch=hibernate
```


Change 'hibernate' to 'suspend':

```
HandleLidSwitch=suspend
```


Save and reboot.  ;)

---

### Post by enricobe on 2015-03-08
Thank you all for your answers! :)

It's quite difficult to write the exact command because my Ubuntu is in italian and I need to do a quick translation to post there.

I'm not talking about suspending or hibenating, but just about the screen standby.
Look at this image
[http://www.techotopia.com/images/7/7b/Ubuntu_11_unity_battery_power_management_settings.jpg](http://www.techotopia.com/images/7/7b/Ubuntu_11_unity_battery_power_management_settings.jpg)
the "Put display to sleep when inactive for" was set to 10 mins and the "put computer to sleep when inactive for" was not set (never suspend?). The Notebook never goes in standby, just the screen does.

[**[COLOR=#000000]@grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323") I have an Intel i5 with 4GB of RAM and 512MB or 1GB of swap. I actually don't know if its enough but i guess it is. Inkscape doesn't have an auto-save function or I did not found it. It has default settings on my PC.

Ubuntu was really slow and when I was moving the mouse it worked but with a huge delay. The cursor was moving slowly and with lags. e.g. It moves for 100 pixels, then stops for 2-3 seconds and so on. I think that do a move from one diplay edge to another could take 30-40 seconds.

---

### Post by sammiev on 2015-03-08
Your swap should match your memory in most cases but you do have enough memory. If your memory is full and your computer is going into suspend or so on it would need the full 4 GB.

---

### Post by mc4man on 2015-03-08
> **enricobe said:**
> 

I'm not talking about suspending or hibenating, but just about the screen standby.
Look at this image
[http://www.techotopia.com/images/7/7b/Ubuntu_11_unity_battery_power_management_settings.jpg](http://www.techotopia.com/images/7/7b/Ubuntu_11_unity_battery_power_management_settings.jpg)
the "Put display to sleep when inactive for" was set to 10 mins and the "put computer to sleep when inactive for" was not set (never suspend?). The Notebook never goes in standby, just the screen does.

Have to ask as that image is named unity..
Where are you getting that pm screen from? (as it's not seen here in any recent Ubuntu in a ubuntu (unity) session

---

### Post by ventrical on 2015-03-08
He installed caffine from ppa repo.

[http://askubuntu.com/questions/56128/how-can-i-actually-change-my-power-management-settings](http://askubuntu.com/questions/56128/how-can-i-actually-change-my-power-management-settings)

---

### Post by mc4man on 2015-03-08
> **ventrical said:**
> He installed caffine from ppa repo.

[http://askubuntu.com/questions/56128/how-can-i-actually-change-my-power-management-settings](http://askubuntu.com/questions/56128/how-can-i-actually-change-my-power-management-settings)
Don't have nor will that type of caffeine but I *think* that au post was showing a screen from older versions of Ubuntu, not caffeine induced
> Power mangament

But you could also try to set the Power management settings as system default by pressing "make default", that worked for me in 11.04 and 10.04.1.  



---

### Post by enricobe on 2015-03-09
It's not a screenshot of my PC, just an image to help you to understand what my settings are. I have not installed caffeine.


> **sammiev said:**
> Your swap should match your memory in most cases  but you do have enough memory. If your memory is full and your computer  is going into suspend or so on it would need the full 4 GB.
Ok, thank you. It could be the problem, i'll try opening the same programs and look if it works.

---

### Post by crcarson on 2015-03-09
Seen a problem of slow/no response on my 15.04 desktop running systemd.  System was idle and the screen blanked.  Coming back and moving the mouse I get the lock screen which normally goes away with enter but several times the lock screen stays for 1-2 minutes.  The mouse moves without hesitation and the lock screen shows the "V"'s flash at some regular interval.  Will check the logs next time this occurrs.

---

