---
title: "Hardy installation on my main desktop"
date: 2008-05-03
forum: Testimonials &amp; Experiences
---

### Post by chewearn on 2008-05-03
Today, I decided it's time to install Hardy in my main desktop PC.  I'm currently posting this from the Hardy LiveCD.

Over the past one week, there have been numerous complaint threads created about people problems with Hardy.  There were what I considered good threads: posts which outline their problems and specific questions on what they wish to be solved.  Then, there were the less than good threads, of people simply complaining about Hardy being the worst ever Ubuntu release.  Finally, there were the threads about Ubuntu being at the end of road, that it will now fail because Hardy has failed for them.

I'm posting about one person experience doing a fresh install of Hardy.  I will update this thread about the steps I take, before, during and after installation.  There will be post on any problem encountered, and the solution I find.

My main aim with this thread is to provide any information that may be helpful for others.  Also, in a small way, to demonstrate that Hardy could work in one person's desktop (unless I hit a wall :lol:, then I might have to declare defeat).

Some background: I have been using Ubuntu since Edgy release.  Before that, I attempted and failed to get Dapper working.  On hindsight, I realized two problems with my Dapper attempt: first, I was struggling with amd64 platform (which was not as polished then); and second, I was a complete Linux newbie.  I don't even know about this forum to be honest.  However, since Edgy, I started with 32bit Ubuntu until Gutsy, where I finally took the plunge into amd64 install.

My experience with Hardy started on a Dell D620 laptop.  I install Hardy beta around end March, and the experience has been good.  There were a few gotchas with the nvidia restricted driver, but overall no deal breakers.

Now, I'm ready to load Hardy into my main desktop.  Here is the spec:
MSI barebone PC (mPC51PV)
nvidia MCP51 based motherboard
AMD Athlon 64 X2 3800+ (Opteron socket AM2)
nvidia GeForce 6150 onboard graphics
Realtek ALC880 onboard audio
2GB RAM
160GB HDD

And so it begins.

---

### Post by chewearn on 2008-05-03
Pre-preinstallation:
Thing I do before installation to prepare:
1. Update my Ubuntu installation checklist
Every time I install Ubuntu, I keep a running checklist on the things I did, the applications I need and so on.  This helps to speed up the installation, and remind me about the tweaks I have to make.

2. Back-up evolution mailbox.

3. Burn the install disc (of course!)
I will be using the Hardy desktop amd64 iso.

Pre-installation:
1. Shutdown the PC.

2. Vacuum clean the inside of the PC
It's a good time to clear out the dust.

3. Swap out the existing harddisk (Gutsy installed), swap in a new harddisk.

4. Boot-up LiveCD, do a CD defect checking: pass no error.

5. On to the LiveCD desktop.

6. While LiveCD is booting, put old harddisk into a USB enclosure; this will make it easy to copy files from it later.

---

### Post by chewearn on 2008-05-03
Hit the first problem while booting LiveCD: the primary display (on DVI) became blank, while the secondary display (on VGA) showed garbage (attached screenshot).  But I have encountered this problem in Gutsy, the solution is to unplug the second display from the VGA for now.

In the LiveCD desktop, check out the hardware.

Wired network is working; I'm able to instantly browse the internet and post here :smile:
Stereo sound is ok.
Optical spdif is not ok; might need to sort out once installation is complete.
Card reader is ok.  I'm able to copy jpg file from my SD card and post the image.

System is stable.  It has been almost an hour in LiveCD posting here.  I ran gimp to resize the jpg photo to a smaller file.

Ok, time to hit the install icon.

EDIT:
Realized that the spdif might be muted.  double click on the speaker icon in the notification area to bring up the Alsa Mixer, go to: Edit menu > Preferences, enable checkbox for IEC958.
A new "Switches" tab appear in the mixer main window, select the tab, and enable checkbox IEC958.  Voila! Got sound from the spdif.

Install now completed (less than 20 minutes!) :smile: Time to reboot, see you on the other side.

---

### Post by chewearn on 2008-05-03
1. Upon reboot, first thing check relevant software sources are selected.  Enable backport.

2. Enable nvidia restricted driver.

3. Install nvidia-settings.

4. Reboot.

5. Plug in second monitor.  Use nvidia-settings to generate xorg.conf with second monitor, use "Separate X screen" setting.

6. Reboot again.  Second monitor came up ok, but with 800x600.
The second monitor has faulty or missing EDID info.  Struggle for awhile to force the correct resolution of 1280x768.  Basically, the following entry need to be added into xorg.conf:

Under "Monitor" section of the second monitor:
```
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
```Reboot and the second monitor came up to 1024x768.  Use nvidia-settings again, now I can select 1280x768 for the second monitor.  Save the new xorg.conf, and reboot again (geez!).  Success!

7. Add script to launch two instances of compiz, one for each screen.  This fix the "slow window in the first monitor" bug in gnome desktop when running separate X screen.

8. Add various applets into the panel to monitor the hardware.  I run folding@home, so it's necessary to monitor the CPU clock, CPU load, temperature and fan speed.

```
sudo apt-get install lm-sensors hddtemp sensors-applet
sudo sensors-detect
```Sensors-detect add some items into /etc/modules, so reboot is required for them to take effect.

Run gconf-editor:
apps > gnome-power-manager > cpufreq > policy_ac > change "ondemand" to "performance"
This will make sure the CPU is running at highest clock speed for the folding@home.


EDIT:
After reboot, time to run folding@home.  First, install the prerequisite:
```
sudo apt-get install ia32-libs
```I run f@h in user mode, so migrating from Gutsy to Hardy is simple.  Copy over the f@h directory from the old harddisk.  Then, just run it, and it continues from where is was at.

Let's see if Hardy is stable and still survive after a couple of hours.  Meanwhile time to install some apps and tweak the desktop.  This tiny font in Firefox is killing my vision. :lol:

---

### Post by chewearn on 2008-05-04
Almost 12 hours later, Hardy is still up and running.  :smile:

I have been tweaking and installing stuffs.  No major problem yet.  Minor problems:

1. running alltray caused processor to be tied up by Xorg, making the UI sluggish.  I found a thread in the forum about alltray not working well with compiz.  Between alltray and compiz, I would rather keep compiz, so will stop using alltray for the time being.

2. I can't set the clock to UTC.  In Gutsy, there is a checkbox to show UTC, but this is no longer there in Hardy.

3. Webbrowser Java plug-in in amd64 platform is still a problem.  The IceTea plug-in is not working in banking sites.  I haven't decide what to do about this.

---

### Post by chewearn on 2008-05-04
Almost a day now, still going strong! :smile:

Ok, I admit, I rebooted once after installing truecrypt 5.1a.  I hit a major roadblock here.  Truecrypt 5.1a writing speed was slooow, less than 1MBps.  Many hours of head scratching finding a solution.

Finally, have to compile Truecrypt 4.3a from source.  I found a helpful thread:
[http://ubuntuforums.org/showthread.php?t=647339](http://ubuntuforums.org/showthread.php?t=647339)

This is a big problem for the few people who want to use Truecrypt in Hardy, but not technically incline to be able to do this.  I'm not sure if my experience with ver 5.1a is typical, but I did find some posts in the Truecrypt forum about people wanting a 4.3a deb file for Hardy.

---

