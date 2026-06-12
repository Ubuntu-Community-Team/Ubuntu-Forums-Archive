---
title: "PulseAudio Equalizer Script"
date: 2009-10-31
forum: Tutorials
---

### Post by psyke83 on 2009-10-31
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=136843&d=1258652669[/IMG]

[COLOR="Blue"]**Note 1:** This package provides an equalizer interface for the LADSPA sound processing functionality of PulseAudio. If you wish to test or discuss an alternate PulseAudio equalizer implementation which does not rely on LADSPA processing, please see [phish3]("http://ubuntuforums.org/member.php?u=970623")'s thread [here]("http://ubuntuforums.org/showthread.php?t=1378087").[/COLOR]

[COLOR="Blue"]**Note 2:** This script requires PulseAudio 0.9.19 or later to function properly, which has the following implications:
[LIST]
[*]**Jaunty users:** your version of PulseAudio is outdated - you must upgrade. I recommend [Luke Yelavich's PPA]("https://launchpad.net/~themuso/+archive/ppa").
[*]**Karmic users:** you do not need to upgrade PulseAudio. If you are already using the 0.9.20 packages from the semi-official [Ubuntu Audio Dev PPA]("https://launchpad.net/~ubuntu-audio-dev/+archive/ppa"), the equalizer will continue working.
[*]**Lucid (testing) users:** you have the latest version of PulseAudio - no further action is necessary.
[/LIST]
**Note 3:** This script assumes that your PulseAudio setup is functioning properly. In other words: if your audio is not working, neither will this script.[/COLOR]

Hey folks,

I'm releasing GUI and script for PulseAudio users that will set up system-wide equalized audio, without needing to restart PulseAudio or any running applications.

Enjoy!

**Advantages:**
[LIST]
[*]Configurable 15 band equalizer for PulseAudio; 
[*]You can enable or disable equalized audio on-the-fly, without having to restart any running applications;
[*]Offers the choice of using equalized audio for the current session or permanently;
[*]No need to edit any configuration files by hand;
[*]User-customizable: you can use any [LADSPA audio processing plugin]("http://www.ladspa.org/") (which can apply various audio effects beyond equalization);
[*]Packaged as a .deb file for easy installation;
[*]Graphical User Interface.
[/LIST]

**Installation:**
Since v2.6, the pulseaudio-equalizer package is available from [my PPA]("https://launchpad.net/~psyke83/+archive/ppa"), which you can access like so:
```
$ sudo software-properties-gtk --enable-ppa=psyke83/ppa; sudo apt-get update; sudo apt-get install pulseaudio-equalizer
```

**Source code:**
The source is [available]("https://code.launchpad.net/~psyke83/+junk/pulseaudio-equalizer") on Launchpad.

**Usage:**
Open the PulseAudio Equalizer (Applications -> Sound & Video). The interface should be fairly self-explanatory:

[LIST]
[*]**15 frequency bands** you can adjust to your liking;
[*]**Preamp** will boost your equalized volume (as a multiplier value from 1x to 4x);
[*]**Presets** are included (based on VLC's built-in equalizer), or you can choose to save own favourite configuration as a new preset;
[*]**EQ Enabled** will enable the equalizer in the current session (which applies to all running applications);
[*]**Keep Settings** will configure your PulseAudio configuration to remain permanently equalized (and therefore, you won't need to run the PulseAudio Equalizer interface each time you login);
[*]**Advanced** menu options so that you can reset all settings (useful for troubleshooting) or delete user presets;
[*]**Apply Settings** will apply all changes.
[/LIST]

**TECHNICAL: How does the equalizer work?**
The script uses a [LADSPA audio processing plugin]("http://www.ladspa.org/"), specifically the [Multiband EQ/mbeq_1197]("http://plugin.org.uk/") plugin from the swh-plugins package.

If you examine the pulseaudio-equalizer.sh script, you will see the following lines near the beginning:

```

# Default LADSPA plugin & control settings; control settings will be overridden if $HOME/.equalizerrc file exists.
PA_LADSPA_PLUGIN="mbeq_1197"
PA_LADSPA_LABEL="mbeq"
PA_LADSPA_CONTROL="-1,-1,-1,-1,-5,-10,-18,-15,-10,-5,-5,-5,-5,0,0"
```

What do these variables mean?
[LIST]
[*]"mbeq_1197" refers to the LADSPA plugin file (located in /usr/lib/ladspa/);
[*]"mbeq" refers to the internal label used by the LADSPA plugin (some plugin files can have multiple labels embedded inside);
[*]the comma separated numbers refers to the actual equalization settings (detailed below).
[/LIST]

You can use the "analyseplugin" utility from the "ladspa-sdk" package in order to see the detailed information on a particular LADSPA plugin. Here's the information for the plugin used by the script:

```
conn@inspiron:~$ analyseplugin mbeq_1197

Plugin Name: "Multiband EQ"
Plugin Label: "mbeq"
Plugin Unique ID: 1197
Maker: "Steve Harris <steve@plugin.org.uk>"
Copyright: "GPL"
Must Run Real-Time: No
Has activate() Function: Yes
Has deativate() Function: No
Has run_adding() Function: Yes
Environment: Normal or Hard Real-Time
Ports:	[COLOR="Blue"]"50Hz gain (low shelving)" input, control, -70 to 30, default 0
	"100Hz gain" input, control, -70 to 30, default 0
	"156Hz gain" input, control, -70 to 30, default 0
	"220Hz gain" input, control, -70 to 30, default 0
	"311Hz gain" input, control, -70 to 30, default 0
	"440Hz gain" input, control, -70 to 30, default 0
	"622Hz gain" input, control, -70 to 30, default 0
	"880Hz gain" input, control, -70 to 30, default 0
	"1250Hz gain" input, control, -70 to 30, default 0
	"1750Hz gain" input, control, -70 to 30, default 0
	"2500Hz gain" input, control, -70 to 30, default 0
	"3500Hz gain" input, control, -70 to 30, default 0
	"5000Hz gain" input, control, -70 to 30, default 0
	"10000Hz gain" input, control, -70 to 30, default 0
	"20000Hz gain" input, control, -70 to 30, default 0[/COLOR]
	"Input" input, audio
	"Output" output, audio
	"latency" output, control
```

As you can see from the text in blue, the mbeq_1197 plugin allows you to equalize 15 different bands. If you wish to customize the plugin or control settings, you can manually edit a preset and enter the appropriate LADSPA information (future versions will support different plugins easily via the interface). If you want to see the plugins available (for all audio processing effects, not merely equalization),  use the "listplugins" and "analyseplugin <plugin_name>" utilities for guidance.

I have provided a "Laptop" preset which I have customized to improve the "tinny" audio from the internal speaker of my laptop (a Dell Inspiron 510m). While the settings may not be optimal for your setup, you may also find it useful for your own hardware.

If you have any problems, questions or suggestions to improve the script, please let me know.

[SIZE="1"]**Changelog:**
v1.0 - 24/10/2009 - Initial version.
v1.1 - 25/10/2009 - Improved status checking; transition entire script to pacmd.
v1.2 - 25/10/2009 - Improved script indenting; added toggle option.
v1.3 - 25/10/2009 - Improved volume handling (existing levels are always maintained when toggling equalizer).
v1.4 - 25/10/2009 - Improved mute handling (existing mute setting is always maintained when toggling equalizer); renamed sink to match LADSPA plugin.
v1.5 - 02/11/2009 - Improved sink handling (user-defined sink will always be used/restored when equalizer is enabled/disabled); better status equalizer detection; better detection of running clients to transfer to equalized audio.
v1.6 - 04/11/2009 - Added options "always-on" and "always-off" to permanently store equalizer settings; added support for custom control settings (if $HOME/.equalizerrc file is present).
v1.7 - 04/11/2009 - Renamed options; options "enable-config" and "disable-config" will edit, backup & restore user configuration ($HOME/.pulse/default.pa) when possible; better status checking.
v1.8 - 04/11-2009 - Avoid duplicate module-ladspa-sink modules getting loaded; added undocumented options "write-equalizerrc" and "delete-equalizerrc" for interfaces.
v1.9 - 08/11/2009 - Now includes PyGtk interface; packaged as a .deb file; interface supports presets (but few meaningful presets are yet included). Requires testing.
v2.0 - 08/11/2009 - Added VLC's equalizers; better support for loading user presets.
v2.1 - 10/11/2009 - Added "debug" option to script; added swh-plugins, ladspa-sdk to depends; "Keep Settings" or selecting a preset will take effect immediately.
v2.2 - 14/11/2009 - Major re-write of PyGTK interface; now supports pre-amp, saving/deleting presets; fixed rare bug which caused "Keep Settings" to mute audio on restart.
v2.3 - 17/11/2009 - Better formatting of scale values on interface; ensure that preset list always remains sorted; script will automatically create user preset folder; confirmed Lucid Lynx compatibility.
v2.4 - 19/11/2009 - Preamp range now 1x to 2x, default is 1.5x and increments are now allowed; added Flat preset; selecting a preset will now apply settings immediately; improved script to make enabling EQ slightly faster; preamp setting is no longer controlled by presets; added application icon.
v2.5 - 04/02/2010 - Preamp range now between 0x and 2x, defaulting to 1x; improved script compatibility with new PulseAudio/Lucid Lynx version; misc bugfixes to prevent hangs on moving streams; optimized script to improve initialization speed and prevent loud pops when applying new settings; Fedora guideline compliance.
v2.6 - 05/02/2010 - Small configuration detection fix - first version in PPA.
v2.7 - 05/02/2010 - Small packaging fix.[/SIZE]

---

### Post by sbersier on 2009-11-05
[COLOR=Red]This post has been removed since [psyke83]("http://ubuntuforums.org/showpost.php?p=8210866&postcount=1") provided us for a nice python GUI. There no need anymore for the java GUI that was provided in this post and which made use of the now outdated v1.8 version of the pulseaudio-equalizer.sh

[/COLOR]

---

### Post by psyke83 on 2009-11-05
(Quoted from the PulseAudio Fixes thread):

> **sbersier said:**
> OK. So...
- There is no more reference to an existing or non-existing default.pa file. It performs a "pulseaudio-equalizer status" operation.
- I didn't make use of the write-equalizerrc feature since I prefer to start in a neutral position (zeros everywhere)
- I separated in the GUI the two functions: (1)(enable, disable) and (2)(enable-config, disable-config)
  It means that you can select the "Keep config" option without necessarily starting the equalizer
  and as well you can deselect the "Keep config" option without stopping the equalizer
  I did this because it was easier for me (I'm not a programmer. In fact, this is my first java program...)
- I've build a equalizer.jar and modified the install instructions.

The result is posted on the new thread and I will no more interfere in this one. My first post will be obsolete and will point to the new thread.
Thanks and best regards.
Steph

I see, thanks for the explanation, and thanks again for writing the interface.

Perhaps the next time you update the interface, you can also attach the equalizer.java file to your post, so that the source code is available?

---

### Post by alijaou on 2009-11-05
Merci, ça fonctionne.

---

### Post by deankovell on 2009-11-05
thanks psyke83 and sbersier. If I could I would give you some of my beans for this.

---

### Post by sbersier on 2009-11-05
[removed]

---

### Post by vade on 2009-11-06
Thanks a lot for working on this.

---

### Post by kjwein on 2009-11-06
This fixed my sound problem, Thank you very much for doing this!

---

### Post by mojo2012 on 2009-11-07
Hi guys,

thank you so much for this little script an the config app. It solved my problem described here: [http://ubuntuforums.org/showthread.php?p=8205002#post8205002](http://ubuntuforums.org/showthread.php?p=8205002#post8205002).

Finally, sound is smootly and equally distributed over all speakers.

What I noticed is, that now the overall sound volume is much lower. Is there a way to make the whole sound louder as well?
I played around with the equalizer but couldn't make the volume louder.

---

### Post by sbersier on 2009-11-07
Even if you push all the sliders to their maximum value?
If so, maybe you could have a look at [http://ubuntuforums.org/showthread.php?t=795525 ]("http://ubuntuforums.org/showthread.php?t=795525")
You should look at "THE HARD WAY" section (if not already tried)...
... "*So if you have a subwoofer and four speakers you're really in a bit of trouble here, because if you tell pulseaudio to use 6 channels, you get low frequency subwoofer sound, but surround sound movies send sound to a centre speaker that doesn't exist, and you don't get any voice on the front speakers. But if you tell pulseaudio that you have four channels, the subwoofer gets no sound. In this case you must define what channels to use manually*."

It looks a bit like the problem you seem to have. I do not have a surround installation myself so I can't help you very much...

Good luck,
Steph

---

### Post by psyke83 on 2009-11-07
> **mojo2012 said:**
> Hi guys,

thank you so much for this little script an the config app. It solved my problem described here: [http://ubuntuforums.org/showthread.php?p=8205002#post8205002](http://ubuntuforums.org/showthread.php?p=8205002#post8205002).

Finally, sound is smootly and equally distributed over all speakers.

What I noticed is, that now the overall sound volume is much lower. Is there a way to make the whole sound louder as well?
I played around with the equalizer but couldn't make the volume louder.

I don't have a surround configuration, so I'm not certain if there's a better way to solve this problem. The point of equalizer used by this script is not to redistribute volume across speakers.

Anyway, the best way to boost sound is to enable "flat-volumes" in PulseAudio, which will ensure that equalized volume is just as loud as regular audio (at least on my system). Here's the easiest way:

```
$ sed 's/flat-volumes = no/flat-volumes = yes/g' /etc/pulse/daemon.conf >~/.pulse/daemon.conf; pkill pulseaudio

```

Note that the above command will (necessarily) force PulseAudio to restart, so any running sound applications will also need to be restarted.

---

### Post by psyke83 on 2009-11-08
Folks,

I've packaged v1.9 of the script which now includes a GUI interface.

GUI Features:
[LIST]
[*]15 equalizer bands available
[*]ability to change settings without restarting applications;
[*]ability to permanently save equalizer settings;
[*]Convenient toggle checkmark to enable/disable the equalizer.
[/LIST]
TODO:
[LIST]
[*]Add more presets (the Flat and Laptop presets work correctly, the Pop preset is not accurate;
[*]Add ability to save settings as a user-defined preset.
[/LIST]
**Problems (v1.9)**
Unfortunately, although I included a .desktop file in the .deb package, the menu item for the PulseAudio Equalizer will not display. If anybody knows how to help, **please get in touch with me **(the [PackagingFromScratch]("https://wiki.ubuntu.com/PackagingGuide/Complete#Packaging%20from%20Scratch") instructions were of no use).

Until this problem is sorted, you can manually create a desktop link, like so:
[LIST=1]
[*]Copy the .desktop file to your own desktop:```
$ cp /usr/share/applications/pulseaudio-equalizer.desktop ~/Desktop/
```
[*]Go to your desktop, double-click on the .desktop file, mark as trusted, and then the shortcut will appear properly.
[/LIST]

You can grab the .deb from the [first post]("http://ubuntuforums.org/showthread.php?t=1308838").

---

### Post by fenian on 2009-11-08
This rocks thanks a lot.

---

### Post by sbersier on 2009-11-08
Psyke83: Indeed you GUI is a LOT better. In order not to introduce confusion I propose to remove mine. What do you think?
Best regards,
Steph

---

### Post by sbersier on 2009-11-08
Hi Psyke83,
I've seen that in VLC media player the graphic equalizer already has presets (Classical, Reggae, Pop, ....) Maybe you could reproduce the values there.
Best regards,
Steph

---

### Post by psyke83 on 2009-11-08
> **sbersier said:**
> Hi Psyke83,
I've seen that in VLC media player the graphic equalizer already has presets (Classical, Reggae, Pop, ....) Maybe you could reproduce the values there.
Best regards,
Steph

The next update will incorporate the VLC presets (though the frequency bands differ, I'll try to compensate) ;).

I plan to make this automatic in a future update, but if you have a setting that you like and want to save as a preset, you can do this:

[LIST]
[*]Click "Apply Changes" to ensure the setting is saved.
[*]Run: ```
$ cp ~/.equalizerrc ~/.pulse/presets/MyPreset.preset
```
[*]The next time you run the GUI, you'll see "MyPreset" in the list.
[/LIST]

Edit: fixed since v2.0

---

### Post by sbersier on 2009-11-08
[removed since psyke83 incorporated the VLC settings]

---

### Post by psyke83 on 2009-11-08
> **sbersier said:**
> I've interpolated (cubic spline) the values from VLC to your GUI. And since VLC uses a preamp value I've subtracted it in order to have 0 values for "Flat" setting.
I've attached a gzipped 'presets' directory.
Best regards,
Steph

I already added the VLC presets (manually) to v2.0.

I'm going to evaluate your files in depth a little later, but I immediately see a problem with the first (Classical) - it seems that the values are inverted... or am I wrong?

---

### Post by sbersier on 2009-11-08
Note: I've intentionally rounded the values to integer values is it absolutely necessary? If not I can modify the previous attachement.

---

### Post by sbersier on 2009-11-08
Ooops, yes indeed the signs are wrong for Classical settings. But if you've already done it. There no point for me to correct it.
Regards,
Steph

---

### Post by psyke83 on 2009-11-08
> **sbersier said:**
> Ooops, yes indeed the signs are wrong for Classical settings. But if you've already done it. There no point for me to correct it.
Regards,
Steph

The problem is that I didn't compensate for the preamp, and used generally un-scientific methods ;). Feel free to fix up your presets, and if they're accurate, I'll include in the next update.

---

### Post by psyke83 on 2009-11-08
> **sbersier said:**
> Note: I've intentionally rounded the values to integer values is it absolutely necessary? If not I can modify the previous attachement.

No, I don't believe that integers are required. However, I've limited the scales (sliders) to one decimal point in order to keep the interface compact.

---

### Post by psyke83 on 2009-11-08
> **sbersier said:**
> Psyke83: Indeed you GUI is a LOT better. In order not to introduce confusion I propose to remove mine. What do you think?
Best regards,
Steph

That's not necessary unless you really want to.

If you wish to keep your interface, I recommend that you download the v1.8 script (still attached to the first post), attach to your post and change the instructions to reflect the fact that you need to use v1.8 and no later.

I've changed a few parts of the script to accommodate the Python interface (because it's my first attempt at programming in Python, I had to rely more on the bash script for passing status between scripts).

---

### Post by sbersier on 2009-11-08
Okay. I will change my first post according to your recommendation. 

Attached is the new 'presets' directory with decimal values (integer values are indeed not necessary) and with the 'Classical' setting corrected. I've made a quick check, it looks like the others a correct...

---

### Post by psyke83 on 2009-11-08
> **sbersier said:**
> Okay. I will change my first post according to your recommendation. 

Attached is the new 'presets' directory with decimal values (integer values are indeed not necessary) and with the 'Classical' setting corrected. I've made a quick check, it looks like the others a correct...

Unfortunately, some of your presets appear to cause distortion artifacts in music (I tried 'The Prodigy - Narayan' with your 'Full bass and treble' preset).

I assume this is because you adjusted for the preamp - it seems that the mbeq_1197 LADSPA plugin simply doesn't compensate for clipping artifacts.

Perhaps there's a better plugin we can use (I've tested tap_eq and it seems promising, but it's limited to 8 bands), but in the meantime we shouldn't correct the preamp on the VLC presets.

---

### Post by sbersier on 2009-11-08
Attached: 'presets' without preamp correction. Changed interpolation method (gives better result on the sides) and corrected an error on the "reggae" setting. I hope that this time it's good...

Attachment modified.

---

### Post by sbersier on 2009-11-08
I'm not so sure our hear can really make the difference between a 15-bands and an 8-bands equalizer. It just takes more time to adjust 15-bands...:razz: So, if the tap plugin is more convenient... why not?

Also, there is a quiet interesting idea for hear-disabled people. It would consist in being able to equalize separately left and right channels. Because, in some cases you can hear correctly from one hear and need some help to hear the trebles or basses from the other one.

---

### Post by psyke83 on 2009-11-09
> **sbersier said:**
> I'm not so sure our hear can really make the difference between a 15-bands and an 8-bands equalizer. It just takes more time to adjust 15-bands...:razz: So, if the tap plugin is more convenient... why not?

Also, there is a quiet interesting idea for hear-disabled people. It would consist in being able to equalize separately left and right channels. Because, in some cases you can hear correctly from one hear and need some help to hear the trebles or basses from the other one.

It appears that the bw_eq ladspa plugin also causes distortion/clipping.

I checked your latest presets (without preamp correction), and they still cause clipping; when I manually reduced all the bands by 3.0, clipping vastly reduced (and in some presets, disappeared).

When using VLC's equalizer (with the PulseAudio equalizer disabled), no clipping occurs even when you move the bands to the maximum/minimum positions, so the accuracy of the values themselves are not the problem.

I propose that we take your latest presets, reduce all values by 3.0 or more, test the results, and adjust any remaining presets that cause distortion.

---

### Post by Vadi on 2009-11-09
Presets, huh. Been looking to tinker with my voice for some VOIP-enabled games.

Going to give this a try.

edit: how can I select what stream do I want to apply this to?

---

### Post by psyke83 on 2009-11-09
> **Vadi said:**
> Presets, huh. Been looking to tinker with my voice for some VOIP-enabled games.

Going to give this a try.

edit: how can I select what stream do I want to apply this to?

You can't. This applies the equalizer to the default sink (output device). You want to apply it to a source (input device), which I don't think is possible.

[http://www.pulseaudio.org/wiki/Modules#module-ladspa-sink](http://www.pulseaudio.org/wiki/Modules#module-ladspa-sink)

---

### Post by Vadi on 2009-11-09
Meh. And here I was all thinking I could put all those hours wasted into PA to good use :(

Hope it can work for sources soon.

---

### Post by nboddie on 2009-11-09
Running Karmic, fully up to date.

I rebooted after installing this equalizer from the deb package, and all of a sudden pulseaudio wouldn't initialize when I logged in.  Got the following errors in syslog:

Nov  9 17:32:45 nboddie-laptop pulseaudio[7399]: main.c: Module load failed.
Nov  9 17:32:45 nboddie-laptop pulseaudio[7399]: main.c: Failed to initialize daemon.
Nov  9 17:32:45 nboddie-laptop pulseaudio[7397]: main.c: Daemon startup failed.
Nov  9 17:32:46 nboddie-laptop pulseaudio[7405]: module-ladspa-sink.c: Master sink not found
Nov  9 17:32:46 nboddie-laptop pulseaudio[7405]: module.c: Failed to load  module "module-ladspa-sink" (argument: "sink_name=ladspa_output.mbeq_1197.mbeq master= plugin=mbeq_1197 label=mbeq control=-0.1,-0.14,-0.12,-0.03,0.1,0.08,-0.12,-0.15,0.03,0.25,0.28,-0.9,-4.77,-8.63,-9.6"): initialization failed.

had to disable the equalizer with:

/ur/bin/pulseaudio-equalizer.sh disable-config

and then logging out and back in results in pulseaudio working correctly.

any fix for this problem?

---

### Post by psyke83 on 2009-11-09
> **Vadi said:**
> Meh. And here I was all thinking I could put all those hours wasted into PA to good use :(

Hope it can work for sources soon.

No, because the ladspa module only works on sinks (outputs).

---

### Post by psyke83 on 2009-11-09
> **nboddie said:**
> Running Karmic, fully up to date.

I rebooted after installing this equalizer from the deb package, and all of a sudden pulseaudio wouldn't initialize when I logged in.  Got the following errors in syslog:

Nov  9 17:32:45 nboddie-laptop pulseaudio[7399]: main.c: Module load failed.
Nov  9 17:32:45 nboddie-laptop pulseaudio[7399]: main.c: Failed to initialize daemon.
Nov  9 17:32:45 nboddie-laptop pulseaudio[7397]: main.c: Daemon startup failed.
Nov  9 17:32:46 nboddie-laptop pulseaudio[7405]: module-ladspa-sink.c: Master sink not found
Nov  9 17:32:46 nboddie-laptop pulseaudio[7405]: module.c: Failed to load  module "module-ladspa-sink" (argument: "sink_name=ladspa_output.mbeq_1197.mbeq master= plugin=mbeq_1197 label=mbeq control=-0.1,-0.14,-0.12,-0.03,0.1,0.08,-0.12,-0.15,0.03,0.25,0.28,-0.9,-4.77,-8.63,-9.6"): initialization failed.

had to disable the equalizer with:

/ur/bin/pulseaudio-equalizer.sh disable-config

and then logging out and back in results in pulseaudio working correctly.

any fix for this problem?

The script doesn't seem to write the master sink name to your configuration file.

Do this:
```
$ pulseaudio-equalizer.sh disable-config; pkill pulseaudio; sleep 10; pacmd info >~/Desktop/pacmd-info.log; pacmd stat >~/Desktop/pacmd-stat.log
```

Send me the two log file that are saved to your desktop.

---

### Post by nboddie on 2009-11-09
files are attached.

---

### Post by psyke83 on 2009-11-09
> **nboddie said:**
> files are attached.

Thanks, I just need a few more:

```
$ pkill pulseaudio; sleep 10; pulseaudio-equalizer.sh enable; sleep 5; pacmd info >~/Desktop/pacmd-info.log; pacmd stat >~/Desktop/pacmd-stat.log
```

Please send the logs again (same filenames on desktop).

---

### Post by nboddie on 2009-11-09
here you go :)

---

### Post by sanskaras on 2009-11-09
I got the same error in my syslog as above on restart. Otherwise this equalizer is awesome!

```
Nov  9 18:38:44 nick-laptop pulseaudio[2487]: module-ladspa-sink.c: Failed to load LADSPA plugin: file not found
Nov  9 18:38:44 nick-laptop pulseaudio[2487]: module.c: Failed to load  module "module-ladspa-sink" (argument: "sink_name=ladspa_output.mbeq_1197.mbeq master=alsa_output.pci-0000_00_1b.0.analog-stereo plugin=mbeq_1197 label=mbeq control=0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0"): initialization failed.
Nov  9 18:38:44 nick-laptop pulseaudio[2487]: main.c: Module load failed.
Nov  9 18:38:44 nick-laptop pulseaudio[2487]: main.c: Failed to initialize daemon.
Nov  9 18:38:44 nick-laptop pulseaudio[2482]: main.c: Daemon startup failed.
```

Attached are the from the commands in the previous post also.

---

### Post by sanskaras on 2009-11-09
Well, I just figured out when I hit enable EQ or apply settings, the eq doesn't change.  Probably because of these errors that simitaneously show up in the log - maybe related to the first errors?

```
Nov  9 18:52:25 nick-laptop pulseaudio[3331]: ratelimit.c: 178 events suppressed
Nov  9 18:52:29 nick-laptop pulseaudio[3331]: module-ladspa-sink.c: Failed to load LADSPA plugin: file not found
Nov  9 18:52:29 nick-laptop pulseaudio[3331]: module.c: Failed to load  module "module-ladspa-sink" (argument: "sink_name=ladspa_output.mbeq_1197.mbeq master=alsa_output.pci-0000_00_1b.0.analog-stereo plugin=mbeq_1197 label=mbeq control=-16.0,-16.0,6.5,6.5,6.0,5.5,4.5,1.0,1.0,1.0,-8.0,-10.0,-16.0,-16.0,-20.4"): initialization failed.
Nov  9 18:52:32 nick-laptop pulseaudio[3331]: ratelimit.c: 198 events suppressed
```

And when the eq is enables or applied the volume jumps to maximum, which is well annoying lol.

---

### Post by psyke83 on 2009-11-09
> **sanskaras said:**
> I got the same error in my syslog as above on restart. Otherwise this equalizer is awesome!

```
Nov  9 18:38:44 nick-laptop pulseaudio[2487]: module-ladspa-sink.c: Failed to load LADSPA plugin: file not found
Nov  9 18:38:44 nick-laptop pulseaudio[2487]: module.c: Failed to load  module "module-ladspa-sink" (argument: "sink_name=ladspa_output.mbeq_1197.mbeq master=alsa_output.pci-0000_00_1b.0.analog-stereo plugin=mbeq_1197 label=mbeq control=0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0"): initialization failed.
Nov  9 18:38:44 nick-laptop pulseaudio[2487]: main.c: Module load failed.
Nov  9 18:38:44 nick-laptop pulseaudio[2487]: main.c: Failed to initialize daemon.
Nov  9 18:38:44 nick-laptop pulseaudio[2482]: main.c: Daemon startup failed.
```

Attached are the from the commands in the previous post also.

Your problem is different - install the packages "swh-plugins" and "ladspa-sdk". In the next update I'll add those as dependencies against the .deb file.

---

### Post by psyke83 on 2009-11-09
> **nboddie said:**
> here you go :)

I didn't find a problem with your logs that explains the problem...

Can you install the latest update (2.1), open a terminal and run the following:
```
$ pulseaudio-equalizer.sh debug
```

When the process finishes, attach the newly-created ~/Desktop/pulseaudio-equalizer.log file.

---

### Post by nboddie on 2009-11-09
installed 2.1, ran the debug script - log attached.

---

### Post by psyke83 on 2009-11-09
> **nboddie said:**
> installed 2.1, ran the debug script - log attached.

I don't see any problems with those logs... everything should work fine.

You only have a problem if you choose "Keep Settings" (save the configuration), and then log out and back in?

Also can you confirm if the equalizer works in the current session (i.e. "EQ Enabled", or the "enable" script option)?

Perhaps give it another try, because I don't see why it shouldn't work.

Edit: you should re-download and install the 2.1 deb, as I re-uploaded with a fix. There was a slight error in the script causing the interface not to apply settings correctly (but it didn't affect the accuracy of the debug logs you sent).

---

### Post by nboddie on 2009-11-09
OK,

Here's what I see now.

Leave 2.1 enabled.
restart system
when it comes up - no sound at all
fiddle with volume, sound preferences, equilizer (applying different presets, etc.) still no sound - leave sound up all the way (still no sound)
Run pulseaudio-equilizer.sh debug
volume applet has restarted, and now the sound is all the way down - move it up
play a song and now there is sound
The debug log is attached -

---

### Post by psyke83 on 2009-11-09
> **nboddie said:**
> OK,

Here's what I see now.

Leave 2.1 enabled.
restart system
when it comes up - no sound at all
fiddle with volume, sound preferences, equilizer (applying different presets, etc.) still no sound - leave sound up all the way (still no sound)
Run pulseaudio-equilizer.sh debug
volume applet has restarted, and now the sound is all the way down - move it up
play a song and now there is sound
The debug log is attached -

It seems that your ALSA sink input is not initialized properly when PulseAudio is first run on your system, which causes a failure when setting up the equalized (LADSPA) sink. I'm not sure what's causing this issue, but here is a possible workaround:

[LIST]
[*]Apply the preset/custom bands that you want. Ensure that "Enable EQ" is checked, but "Keep Settings" in unchecked.
[*]Add a new GNOME startup entry which executes the following:```
sleep 10; pulseaudio-equalizer.sh interface.applysettings
```
[/LIST]

You may also notice that your login sound is not equalized along with some interruption in audio within the first 10 seconds of login - that's to be expected.

I'd appreciate to know if that helps.

---

### Post by nboddie on 2009-11-10
OK,

So now you'll think I was crazy :(

I put together the startup script as you suggested, and in prep for putting it in I did:

pulseaudio-equalizer.sh enable
pulseaudio-equalizer.sh enable-config
rebooted

AND EVERYTHING WORKED!!! Without the startup script!!!
How disturbing....

SO at this point all seems well - maybe it was the 2.1 version? maybe I rolled the dice and came up sevens?

I'm flummoxed.

But at least for now I have equalized sound back....

Thanks for your efforts, if it hoses up again I'll post back here.

Cheers,

Ned

---

### Post by psyke83 on 2009-11-10
> **nboddie said:**
> OK,

So now you'll think I was crazy :(

I put together the startup script as you suggested, and in prep for putting it in I did:

pulseaudio-equalizer.sh enable
pulseaudio-equalizer.sh enable-config
rebooted

AND EVERYTHING WORKED!!! Without the startup script!!!
How disturbing....

SO at this point all seems well - maybe it was the 2.1 version? maybe I rolled the dice and came up sevens?

I'm flummoxed.

But at least for now I have equalized sound back....

Thanks for your efforts, if it hoses up again I'll post back here.

Cheers,

Ned

I managed to replicate the issue, but I don't know what are the exact conditions that cause the problem.

Every time you click "Apply Settings", the configuration file will be re-written to ~/.pulse/default.pa (to update the control values). However, sometimes the bash script will not identify the master (ALSA) sink properly and write a blank entry instead of the master sink name.

I suspect there's some kind of timing issue/glitch when changing PulseAudio's running state. I'll have a look through the script and try to change it so that it works more reliably.

---

### Post by Screwbottle on 2009-11-10
[QUOTE=psyke83;8210866]

(pulseaudio-equalizer.sh) from this post.


Hi psyke83

Need your help from this post. I have Karmic with all of the latest current patches and updates. Pulse Audio working fine, followed your guide, except for two issues.

Firstly could not find your script (edited out from the rest of your post above), so could not follow the instructions further, in connection with your script.
Secondly Pulse Audio does not hold my bass / low frequency emitter, between songs, all other surround channels fine (checking with Pulse Audio Volume Meter and can hear the audible difference) using Rhythmbox, XMMS, Totem or any other multimedia player. I have to invoke the bass channel by clicking on the desktop shortcut, and selecting a preset (most common one I like for my listening is "Soft"). Then the bass kicks in.

Any idea how I cna fix this to permanently activate and keep the low frequency channel active.

Regards
Andrew Brown aka Screwbottle

---

### Post by psyke83 on 2009-11-10
> **Screwbottle said:**
> 
Firstly could not find your script (edited out from the rest of your post above), so could not follow the instructions further, in connection with your script.


The bash script is packaged in the .deb file, gets installed to "/usr/bin/pulseaudio-equalizer.sh", and is no longer intended for direct use (as a GUI now exists). Please ignore the "v1.8" instructions, they're redundant.

> Secondly Pulse Audio does not hold my bass / low frequency emitter, between songs, all other surround channels fine (checking with Pulse Audio Volume Meter and can hear the audible difference) using Rhythmbox, XMMS, Totem or any other multimedia player. I have to invoke the bass channel by clicking on the desktop shortcut, and selecting a preset (most common one I like for my listening is "Soft"). Then the bass kicks in.

The "Keep Settings" option will ensure that PulseAudio always uses the equalizer settings (so it will survive a logout/restart/crash).

Keep in mind that this script's function is to provide software equalization alone - it does not take advantage of hardware bass/treble/equalizer functions. Also, I don't have a surround setup here, so I can't test if the LADSPA sink works correctly for all channels (perhaps not).

---

### Post by Screwbottle on 2009-11-10
> **psyke83 said:**
> The bash script is packaged in the .deb file, gets installed to "/usr/bin/pulseaudio-equalizer.sh", and is no longer intended for direct use (as a GUI now exists). Please ignore the "v1.8" instructions, they're redundant.



The "Keep Settings" option will ensure that PulseAudio always uses the equalizer settings (so it will survive a logout/restart/crash).

Keep in mind that this script's function is to provide software equalization alone - it does not take advantage of hardware bass/treble/equalizer functions. Also, I don't have a surround setup here, so I can't test if the LADSPA sink works correctly for all channels (perhaps not).

Hi psyke83

Thanks for the prompt reply. Ummm I think there could be a problem with LADSPA sink for a multichannel setup. I followed your instructions "Keep Settings", rebooted and still the low frequency channel drops out, until I use the PulseAudio EQ. At least now after the reboot, it is holding my chosen EQ, and the low frequency, once selected via the PA EQ, over multiple songs. A small bug to live with until a fix is found. I'll keep tinkering.

As a matter of interest, in case this helps you, the sound chip is an onboard Realtek HD 82801I (LPCI string Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)), with 7.1 surround sound capability, although I use it with a Yamaha 5.1 surround analogue speaker setup. I know the chip set in LSPCI indicates Intel, as I think Realtek supply the silicon setup, and Intel dope it into their chipset, the X38 chipset, the mobo a MSI X-38 Diamond.

But other than that your instruction and technique from yourself and sbersier have definitely helped in "improving" my Linux sound. So to both of you your posts are very much appreciated, even for us long time Linux users.

Regards
Screwbottle

---

### Post by Lalika3 on 2009-11-10
H[FONT=Arial]i
pulseaudio-equalizer 2.1 all.deb install  => [/FONT] Everything works.

Thanks. 

(Excuse me my bad English)

---

### Post by starfleetcaptainrob on 2009-11-10
Thank you!  This worked great for me out of the box!

---

### Post by sbersier on 2009-11-10
Hi Psyke83,
   I've noticed that in v2.1 the Combo_box doesn't show up correctly at first (at least on my PC) because the list is too long and the window is positioned centered. If you add : 
```
presets.set_wrap_width(4)
``` to the declaration of your Combo_box (e.g. after *presets = gtk.combo_box_new_text() *   ) then it solves this (very) minor problem.
Best regards,
Steph

---

### Post by sanskaras on 2009-11-11
I installed the packages and everything works thanks! this is so much easier then the old equalizer.

I got a suggestion for the gui though, maybe a next version couldincorporate a zoom feature for the sliders that adjusts their range?  Smaller adjustments might be easier that way, I don't see myself ever using more then +-10db.  Right now with large range of the sliders, its hard to see visually (without reading the numbers) the difference in the frequencies.

---

### Post by keta on 2009-11-11
Version 1.9 did not work for me, but with 2.1 everything works fine! Thanks sooo much!!! :D

---

### Post by sbersier on 2009-11-11
Hi Psyke83,
   
 Added two features: 
1) the possibility to define the dB range (in the Options menu on the menu bar) as suggested by [Sanskaras]("http://ubuntuforums.org/showpost.php?p=8291476&postcount=54").
2) the ability to define user presets (not yet to remove them)

More details in the attachement.

Best regards,
Steph

2009/11/11  added Range options
2009/11/11  added user preset

---

### Post by Wipster on 2009-11-11
Wow thankyou! I now have much better sound on my laptop it was driving me insane. Super Kudos ++

---

### Post by L8erG8er on 2009-11-12
Psyke83:

Thanks for all of your hard work on this - I can't believe after several years of Ubuntu use we finally have a system wide equalizer!!

One question - when I move Karmic's new master volume slider up and down, I noticed the sound pops a little as the volume changes - anyone have any ideas on what causes that?

While the volume remains unchanged, no troubles, everything is great!  Thanks again.

---

### Post by Zoot7 on 2009-11-12
@Psyke83

From one country man to another. Sincere Thanks!
I now have much better sound in Ubuntu than Windows.

---

### Post by psyke83 on 2009-11-13
> **sbersier said:**
> Hi Psyke83,
   
 Added two features: 
1) the possibility to define the dB range (in the Options menu on the menu bar) as suggested by [Sanskaras]("http://ubuntuforums.org/showpost.php?p=8291476&postcount=54").
2) the ability to define user presets (not yet to remove them)

More details in the attachement.

Best regards,
Steph

2009/11/11  added Range options
2009/11/11  added user preset

Thanks for the modifications. I'm currently re-writing the interface (to add some new features, improve the appearance and clean up the code), will post it soon.

---

### Post by ratdude747 on 2009-11-14
:guitar::guitar::guitar::guitar::guitar:

you ROCK! thanks!. now my sound system is sounding like it should...

---

### Post by blacksm1th on 2009-11-14
I can't run the last version 2.2. This is the output:
```
~:$ /usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py
Getting settings...
PulseAudio Equalizer/LADSPA Processor
-------------------------------------
Equalizer status: [disabled]
Equalizer configuration status: [disabled]
-------------------------------------
Traceback (most recent call last):
  File "/usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py", line 451, in <module>
    Equalizer()
  File "/usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py", line 297, in __init__
    GetSettings()
  File "/usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py", line 45, in GetSettings
    f = open(eqconfig, "r")
IOError: [Errno 2] No such file or directory: '/home/azot/.pulse/equalizerrc'
~:$ /usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py
Getting settings...
PulseAudio Equalizer/LADSPA Processor
-------------------------------------
Equalizer status: [disabled]
Equalizer configuration status: [disabled]
-------------------------------------
Traceback (most recent call last):
  File "/usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py", line 451, in <module>
    Equalizer()
  File "/usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py", line 297, in __init__
    GetSettings()
  File "/usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py", line 50, in GetSettings
    f = open(eqpresets, "r")
IOError: [Errno 2] No such file or directory: '/home/azot/.pulse/equalizerrc.availablepresets'
~:$ /usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py
Getting settings...
PulseAudio Equalizer/LADSPA Processor
-------------------------------------
Equalizer status: [disabled]
Equalizer configuration status: [disabled]
-------------------------------------
Traceback (most recent call last):
  File "/usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py", line 451, in <module>
    Equalizer()
  File "/usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py", line 297, in __init__
    GetSettings()
  File "/usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py", line 56, in GetSettings
    ladspa_name = str(rawdata[1])
IndexError: list index out of range

```
After first an second error i created two empty files: "equalizerrc" and "equalizerrc.availablepresets" in ".pulse" dir. But then this "IndexError:"....

---

### Post by psyke83 on 2009-11-14
> **blacksm1th said:**
> I can't run the last version 2.2. This is the output:

Try this:
```
$ pulseaudio-equalizer.sh interface.resetsettings
```

Then try to open the GUI again.

---

### Post by mestizo on 2009-11-14
I can not download the deb file. It's a problem with the page, or what?. If there is another way to download it, be grateful. Thanks.

Edit: At the end, i can download the file with Internet Explorer on VirtualBox.

---

### Post by blacksm1th on 2009-11-14
> **psyke83 said:**
> Try this:
```
$ pulseaudio-equalizer.sh interface.resetsettings
```

Then try to open the GUI again.

It's not working. I get the same output as before.

---

### Post by psyke83 on 2009-11-14
> **blacksm1th said:**
> It's not working. I get the same output as before.

That's very odd. I deleted all files in ~/.pulse, restarted PulseAudio and tried the equalizer again - it works perfectly here. You may want to re-download the .deb file - I rebuilt the 2.2 package a few times due to small problems, but the latest version should work fine.

Judging from the output, your problem is probably due to an older version of the pulseaudio-equalizer.sh script present on your system. You should delete /usr/local/bin/pulseaudio-equalizer.sh, or any copies you may have installed elsewhere, and make sure that only one version exists in /usr/bin (provided by the .deb file).

Finaly, run:

```
$ pulseaudio-equalizer.sh debug
```

Attach the log file created on your desktop, and the contents of ~/.pulse/equalizerrc (if it exists).

---

### Post by blacksm1th on 2009-11-14
Thank you psyke83. "/usr/local/bin/pulseaudio-equalizer.sh" was the problem.

---

### Post by sol12 on 2009-11-15
**[SIZE=4]Thank you psyke83[/SIZE]** [SIZE=4][COLOR=black]**!!!!!!!!!!!!!!!!!!!!**[/COLOR][/SIZE]

You did it....
I dont need my amplifier for my headphones anymore.
thxthxthxthxthxthx 
(only thing: personal presets are not saved when i push the "save-button")

enabled + 3 % pulseaudio cpu usage. Thats not woth mentioning.

great job.

---

### Post by sbersier on 2009-11-15
Thanks, installation is now much more simple it installs nicely where it should (psyke83, I think you can now remove the installation points in your post) Nothing to say. It just works (as far I can see). Good work!

---

### Post by psyke83 on 2009-11-15
> **sol12 said:**
> **[SIZE=4]Thank you psyke83[/SIZE]** [SIZE=4][COLOR=black]**!!!!!!!!!!!!!!!!!!!!**[/COLOR][/SIZE]

You did it....
I dont need my amplifier for my headphones anymore.
thxthxthxthxthxthx 
(only thing: personal presets are not saved when i push the "save-button")

enabled + 3 % pulseaudio cpu usage. Thats not woth mentioning.

great job.

I'll fix that in the next update. In the meantime, you just need to do this:
```
mkdir ~/.pulse/presets
```

---

### Post by F!o on 2009-11-16
Hi psyke83,

your script is totaly what I was searching for since PulseAudio integration.
Equalizer works fine, but it kinda behaves odd, when changing the master volume.

When I'm listening to a song in Rhythmbox and I turn on the equalizer, changing the volume behaves just normal, but as soon as I stop playback and start it again, there is a crackling noise (sounds like dropouts or lag or something), whenever I change the master volume.

Any idea?

Thanks,
Flo

---

### Post by psyke83 on 2009-11-16
> **F!o said:**
> Hi psyke83,

your script is totaly what I was searching for since PulseAudio integration.
Equalizer works fine, but it kinda behaves odd, when changing the master volume.

When I'm listening to a song in Rhythmbox and I turn on the equalizer, changing the volume behaves just normal, but as soon as I stop playback and start it again, there is a crackling noise (sounds like dropouts or lag or something), whenever I change the master volume.

Any idea?

Thanks,
Flo

Unfortunately that seems to be an issue with the module-ladspa-sink in PulseAudio, and can't be fixed by me.

Just to confirm: the issue only happens at the moment that you change volume, and stops just after you stop changing the volume?

---

### Post by F!o on 2009-11-16
> **psyke83 said:**
> Unfortunately that seems to be an issue with the module-ladspa-sink in PulseAudio, and can't be fixed by me.

Just to confirm: the issue only happens at the moment that you change volume, and stops just after you stop changing the volume?

Yup, it only occurs in the act of changing volume. It really sounds like lag.

Well, then I'm unfortunate. It doesn't really bother me, but it's just not the way it's supposed to be, is it?

Thanks,
Flo

---

### Post by psyke83 on 2009-11-16
> **F!o said:**
> Yup, it only occurs in the act of changing volume. It really sounds like lag.

Well, then I'm unfortunate. It doesn't really bother me, but it's just not the way it's supposed to be, is it?

Thanks,
Flo

It's a bug in Karmic's version of PulseAudio (0.9.19), and unlikely to be fixed in Karmic.

Coincidentally, I tested 0.9.20 (semi-official packages available from the [Ubuntu Audio Dev PPA]("https://launchpad.net/~ubuntu-audio-dev/+archive/ppa")), and I no longer notice any unusual sounds when changing volume levels.

---

### Post by ibuclaw on 2009-11-17
> **psyke83 said:**
> It's a bug in Karmic's version of PulseAudio (0.9.19), and unlikely to be fixed in Karmic.

Coincidentally, I tested 0.9.20 (semi-official packages available from the [Ubuntu Audio Dev PPA]("https://launchpad.net/~ubuntu-audio-dev/+archive/ppa")), and I no longer notice any unusual sounds when changing volume levels.

So the odd pop, click or glitch in audio is limited to Karmic?
Actually, scratch that, it seems to occur every time an I/O operation occurs (ie: reading data from disk.)

update:
Just upgraded to the Ubuntu PPA Dev repository version and it has indeed gone!

update2:
The preamp is LOUD. And there is a noticeable distortion in Music. A limiter or compressor to keep the output audio tame would be nice. But having a quick look, seems to be outside the jurisdiction of your scripts.

One itch though, it would be nice to have it in realtime, rather than clicking "Apply". ;)

Regards
Iain

---

### Post by F!o on 2009-11-17
> **psyke83 said:**
> It's a bug in Karmic's version of PulseAudio (0.9.19), and unlikely to be fixed in Karmic.

Coincidentally, I tested 0.9.20 (semi-official packages available from the [Ubuntu Audio Dev PPA]("https://launchpad.net/~ubuntu-audio-dev/+archive/ppa")), and I no longer notice any unusual sounds when changing volume levels.

I just updated to 0.9.20, but I still have the same situation as before.
Actually nothing changed, I think... Are you sure it's gone for you?

Thanks,
Flo

---

### Post by psyke83 on 2009-11-17
> **tinivole said:**
> So the odd pop, click or glitch in audio is limited to Karmic?
Actually, scratch that, it seems to occur every time an I/O operation occurs (ie: reading data from disk.)

I didn't notice pops happening due to I/O load, even with 0.9.19 - that's odd.

> update:
Just upgraded to the Ubuntu PPA Dev repository version and it has indeed gone!

Phew! Less work for me ;)
> 
update2:
The preamp is LOUD. And there is a noticeable distortion in Music. A limiter or compressor to keep the output audio tame would be nice. But having a quick look, seems to be outside the jurisdiction of your scripts.

A limiter/compresser would mean chaining two LADSPA sinks together, which would increase CPU usage. A more reasonable alternative is to use more conservative values for the presets.

If you take a look at previous posts, sbersier and I discussed the issue of distortion in the presets. Reducing the values will resolve the issue - as an example, try the Laptop preset. It has less/no distortion because it uses smaller values compared to the other presets.

The Laptop preset is my own personal preset (which I had spent quite some time tuning), but the rest of the presets are a very quick port from the VLC's built-in list of equalizers, with little testing. I assume VLC has a built-in limiter, but the LADSPA plugin that the script uses does not.

I'll refine the presets in the next update, which should hopefully eliminate distortion in all cases.
> 
One itch though, it would be nice to have it in realtime, rather than clicking "Apply". ;)


Me too :). Unfortunately, it's not possible. See [this]("http://ubuntuforums.org/showpost.php?p=8335138&postcount=10") post from the Lucid forum.

---

### Post by psyke83 on 2009-11-17
> **F!o said:**
> I just updated to 0.9.20, but I still have the same situation as before.
Actually nothing changed, I think... Are you sure it's gone for you?

Thanks,
Flo

Maybe it's volume distortion? Reduce the pre-amp to 1x, and try with the EQ enabled but all bands set to 0.0. See if the distortion is gone.

---

### Post by ibuclaw on 2009-11-17
> **psyke83 said:**
> I didn't notice pops happening due to I/O load, even with 0.9.19 - that's odd.

I am on a Netbook, so my testimonial should be treated as a gauge for how well this runs on low-end machines. ;)

> **psyke83 said:**
> 
A limiter/compresser would mean chaining two LADSPA sinks together, which would increase CPU usage. A more reasonable alternative is to use more conservative values for the presets.

Oh, you use a ladspa plugin to control it?
Fixing it should be easy then.

Rather than toolchaining plugins, write your own that has both in one.
I've never done LADSPA programming myself, but I am familiar with how sound processing works.

For everything else you've mentioned. Thanks!

Regards
Iain

---

### Post by musarraf172 on 2009-11-23
This is good guide. Thanks for that. But one thing I dont like  i.e whenever I am changing the equalizer setting it makes my master and PCM volume 100 % > The sound suddenly becomes very loud...

---

### Post by psyke83 on 2009-11-23
> **musarraf172 said:**
> This is good guide. Thanks for that. But one thing I dont like  i.e whenever I am changing the equalizer setting it makes my master and PCM volume 100 % > The sound suddenly becomes very loud...

Yes, that's normal - the ALSA sink volume will be set to the preamp multiplier. For example: if the multiplier is 1.5, your volume will be set to 150%.

When the equalizer is active, the LADSPA sink becomes default, so that becomes the main volume control, not the ALSA sink.

Turn the preamp down to 1.0x if you don't need a volume boost.

---

### Post by musarraf172 on 2009-11-23
> **psyke83 said:**
> Yes, that's normal - the ALSA sink volume will be set to the preamp multiplier. For example: if the multiplier is 1.5, your volume will be set to 150%.

When the equalizer is active, the LADSPA sink becomes default, so that becomes the main volume control, not the ALSA sink.

Turn the preamp down to 1.0x if you don't need a volume boost.

Thanks dear. That solved my problem.....:D:D:D:D:popcorn:

---

### Post by diegodiaz on 2009-11-23
You need to update phyton to make it work right? because whe i try to install it, it says something like Pyhton-support =<0.90.0

---

### Post by psyke83 on 2009-11-23
> **diegodiaz said:**
> You need to update phyton to make it work right? because whe i try to install it, it says something like Pyhton-support =<0.90.0

You're on Jaunty?

---

### Post by NoVista on 2009-11-23
Ubuntu has needed a system wide EQ forever.
This is wonderful.

Since the gain needs to remain constant with/without equalization, it would help if the preamp slider would go lower than x1.0 to attain this, especially needed if one is an audiophile, as the x1.0 threshold may not be low enough.
The original intent of an EQ, was to achieve a level sound across the spectrum, dependent upon the listening environment. Most people end up adding gain when achieving this.
So the only way to do a true listening comparison, between an equalized/non-equalized playback, is to have no change in total volume db. Hence the need for a lower threshold.

---

### Post by ENigma885 on 2009-11-24
Adding [[COLOR="Blue"]Bauer stereophonic-to-binaural DSP[/COLOR]]("http://bs2b.sourceforge.net/") to the equalizer's GUI will be a great improvement. I'm using this specific plugin with Audacious and it's just perfect.

**The developer releases a LADSPA version as well. (can be downloaded from [[COLOR="Blue"]HERE[/COLOR]]("http://downloads.sourceforge.net/project/bs2b/LADSPA%20plugin/0.9.1/ladspa-bs2b-0.9.1.tar.bz2?use_mirror=garr"))

---

### Post by psyke83 on 2009-11-24
> **ENigma885 said:**
> Adding [[COLOR="Blue"]Bauer stereophonic-to-binaural DSP[/COLOR]]("http://bs2b.sourceforge.net/") to the equalizer's GUI will be a great improvement. I'm using this specific plugin with Audacious and it's just perfect.

**The developer releases a LADSPA version as well. (can be downloaded from [[COLOR="Blue"]HERE[/COLOR]]("http://downloads.sourceforge.net/project/bs2b/LADSPA%20plugin/0.9.1/ladspa-bs2b-0.9.1.tar.bz2?use_mirror=garr"))

The [module-ladspa-sink]("http://pulseaudio.org/wiki/Modules#module-ladspa-sink") only supports LADSPA plugins with a single "Input" and single "Output" port:

> Currently this module only works with plugins that have one audio input port named "Input" and one output with name "Output". Patches welcome!

Here's the LADSPA plugin information:

```
conn@inspiron:~/Downloads/ladspa-bs2b-0.9.1$ analyseplugin bs2b

Plugin Name: "Bauer stereophonic-to-binaural 0.9.1 (3.1.0)"
Plugin Label: "bs2b"
Plugin Unique ID: 4221
Maker: "Boris Mikhaylov, Sebastian Pipping"
Copyright: "GPL 2 or later"
Must Run Real-Time: No
Has activate() Function: Yes
Has deativate() Function: No
Has run_adding() Function: No
Environment: Normal
Ports:	"Lowpass filter cut frequency (Hz)" input, control, 300 to 2000, default 725
	"Feeding level (dB)" input, control, 1 to 15, default 4.5
	"Input left" input, audio
	"Input right" input, audio
	"Output left" output, audio
	"Output right" output, audio

```

There are two input/output ports, so it won't work with PulseAudio unless this limitation is removed.

---

### Post by cloudscream on 2009-11-24
FINALLY. An equalizer with a GUI for PulseAudio. Thank you very much! :KS  Can't live without equalizers... 
Now I'm using this with MPD. This is a very very useful addition! 

I' running Karmic 64bit here with the latest updates. I've been using this for a week now with no problems.

---

### Post by sbersier on 2009-11-26
Hi, Psyke83
  In a next version (if there is) I  suggest you to change lines 402-403 by the following:

```

    preampscale.set_range(0,2)
#    preampscale.set_increments(1, 1)

```It will allow users to apply any preamp gain (not only integer values) between 0x and 2x

Also a  good thing would be to save preamp settings for each preset since the needed preamp value is closely related to the chosen preset.

Best regards,
                               Steph

---

### Post by treesurf on 2009-11-26
Thanks so much, this has improved the sound from my laptop.  I'm still trying to figure out how to get PulseAudio to recognize the "subwoofer" on my laptop (Lenovo Y550 with Realtek ALC272), which would really make things sound much better.  This is a definite step in the right direction, though.

One thing I have noticed, though: When I apply the laptop preset the volume has a definite jump up (which is a good thing!).  However, when I use the hardware keys to lower the volume down towards zero, the volume gets trapped back in it's previous low range.  Basically, I can't use the hardware volume keys to go back up to the higher volume of the laptop preset once I've used them to go down below the stock max volume.  I have to open the gui back up and click the "EQ Enabled" box again.

---

### Post by SilverFrost on 2009-11-26
Finally a good system-wide equalizer. Now the sound sounds very much better than before.

Thanks!

---

### Post by funnylife_ma on 2009-11-26
hi psyche83,

can u host ur project on sthg like googlecode or sourceforge so that other people can profit from it ?

---

### Post by ramizz on 2009-11-27
Yahoooooooooooo Thanks a million dude !!! I've been hoping for such a things for years !!!!! (in fact since I switched my laptop to ubuntu)

---

### Post by wolfshark on 2009-11-28
This script is great! I need to leave Preamp to min though because it really screws the sound. Otherwise get this to the official packages ASAP :)

---

### Post by sigurnjak on 2009-11-29
Bravo ! Amazing work !
How ever i have one minor problem . After reboot my volume is muted. How do i set to unmute at boot time . I noticed  it when i lost cool login sound i found and set it up .

EQ set up rocks , keep up good work !:guitar:

---

### Post by psyke83 on 2009-11-29
> **sigurnjak said:**
> Bravo ! Amazing work !
How ever i have one minor problem . After reboot my volume is muted. How do i set to unmute at boot time . I noticed  it when i lost cool login sound i found and set it up .

EQ set up rocks , keep up good work !:guitar:

The next time you reboot and find your sound muted, *don't change anything* (i.e. leave the sound muted/unmodified), and run the following command:

```
$ pulseaudio-equalizer.sh debug
```

Then attach the log file that's saved to your desktop so I can see the problem.

---

### Post by sigurnjak on 2009-11-29
Here it is .

---

### Post by lumanda on 2009-11-29
Thanks a lot for this. What a boost. The sound is significantly increased.

---

### Post by drvista on 2009-11-29
thank you for the great script but i think i have found a bug 
whenver you change  the preset the sound disappear for one sec and return 
using karmic with the official packages only no package other than ubuntu official

---

### Post by topgun on 2009-11-30
Thanks again for this fabulous package, my trance sound rocks more and more woot :D

---

### Post by meindian523 on 2009-11-30
/me has observed that reducing the volume in steps (eg by rolling the mouse wheel while pointing at the speaker icon in the notification area), the sound seems to jitter and then adjust to the new volume. If I'm not mistaken, this was the same issue reported by ibuclaw (aka tinivole). Could using Compiz be a part of the problem?

---

### Post by wd5gnr on 2009-11-30
This is great work. Two observations/questions.

1) I run kubuntu. The python interface has a default icon hardwired into the script on line 362 and that entire folder doesn't exist on my machine. I just pointed it somewhere else, but might consider some simpler way of dealing with that.

2) The equalizer itself assumes that I want to attach it to one of my sound cards. But its the wrong sound card. Setting the PA default sink from padevchooser doesn't help that. It appears that padevchooser is broken. Using pacmd to do it manually work. I don't know if that is persistent or if I need to go munge some pulseaudio rc file somewhere.

But very nice! Thanks.

---

### Post by evoka0 on 2009-11-30
Hi, 

Great work, thank you  very much, you made my music rock again !!. However i have a problem since i use the laptop speakers or a usb headset to listen music, and it only works on the laptop speakers, when i change the sound output to the headset using pulseaudio applet voulume control,  the equalization is gone. Hope there is a workarround to this problem. 

Regards

---

### Post by psyke83 on 2009-11-30
> **wd5gnr said:**
> This is great work. Two observations/questions.

1) I run kubuntu. The python interface has a default icon hardwired into the script on line 362 and that entire folder doesn't exist on my machine. I just pointed it somewhere else, but might consider some simpler way of dealing with that.

I'm not sure how to define a "stock" icon that would also work with KDE. Perhaps it's easier to install humanity-icon-theme and/or hicolor-icon-theme instead? Maybe there's a way to fallback to the default application icon; I'll investigate that.

> 2) The equalizer itself assumes that I want to attach it to one of my sound cards. But its the wrong sound card. Setting the PA default sink from padevchooser doesn't help that. It appears that padevchooser is broken. Using pacmd to do it manually work. I don't know if that is persistent or if I need to go munge some pulseaudio rc file somewhere.

For the sake of simplicity, the equalizer will configure itself to use the default PulseAudio sink at the moment that you enable the "EQ Enabled" checkmark.

The solution is to set the desired sound card as the default before you enable the equalizer. Your suspicions are correct about padevchooser - it's broken. Instead, set the default sink via the PulseAudio Volume Control (pavucontrol) application  - the green checkmark corresponding to the desired sound card on the Output Devices tab.

You can do the following:
1. Completely reset/disable the equalizer (via the Advanced menu of the interface). Close the equalizer interface.
2. Run PulseAudio Volume Control (pavucontrol), and set the desired sound you wish to use as the default (via the green checkmark button on the Output Devices tab).
3. Re-open the equalizer and enable it via the "EQ Enabled" checkmark.

Providing that equalized audio now works with the desired card, you can enable the "Keep Settings" checkmark - this will save the current settings to the $HOME/.pulse/default.pa file.

---

### Post by psyke83 on 2009-11-30
> **evoka0 said:**
> Hi, 

Great work, thank you  very much, you made my music rock again !!. However i have a problem since i use the laptop speakers or a usb headset to listen music, and it only works on the laptop speakers, when i change the sound output to the headset using pulseaudio applet voulume control,  the equalization is gone. Hope there is a workarround to this problem. 

Regards

The equalizer does not support hotplugging of devices, unfortunately. When you click the "EQ Enabled" checkmark, it configures the equalized audio using the sound card that was set as the default at the moment you enabled it.

If you hotplug a new device, the equalized sink will not reconfigure itself.

---

### Post by psyke83 on 2009-11-30
> **meindian523 said:**
> /me has observed that reducing the volume in steps (eg by rolling the mouse wheel while pointing at the speaker icon in the notification area), the sound seems to jitter and then adjust to the new volume. If I'm not mistaken, this was the same issue reported by ibuclaw (aka tinivole). Could using Compiz be a part of the problem?

Compiz isn't related.

The distortion during volume changes is unavoidable, and appears to be a quirk of the PulseAudio LADSPA module.

When the equalizer is enabled, there are two sinks (output devices) active:
[LIST]
[*]the master sink (your real sound card), which is always set to the preamp volume multiplier (preamp of 1.0x is 100% volume, preamp of 1.5x is 150%, etc.).
[*]the ladspa sink, which filters audio through the master sink and becomes the new source for system volume control.
[/LIST]
You can observe this behaviour using the PulseAudio Volume Control application on the Output devices tab.

---

### Post by psyke83 on 2009-11-30
> **sigurnjak said:**
> Here it is .

Your log is unusual.

I don't see any problem with the output, but I can tell that you didn't use the "Keep Settings" checkmark of the interface. You do realize it's necessary to allow the equalizer to survive reboots, don't you?

If your sound is getting muted at startup when the equalizer isn't active, then it's not the fault of the equalizer.

---

### Post by wd5gnr on 2009-11-30
> **psyke83 said:**
> The solution is to set the desired sound card as the default before you enable the equalizer. Your suspicions are correct about padevchooser - it's broken. Instead, set the default sink via the PulseAudio Volume Control (pavucontrol) application  - the green checkmark corresponding to the desired sound card on the Output Devices tab.


Good tip. I just used pacmd, but agree that's better. Probably explains why I never got ear candy to work. I assumed padevchooser's default seetings were working ;)

---

### Post by kimme on 2009-11-30
Thanks for this script. This latest Ubuntu 9.10 (Karmic Koala) has finally made pulse audio work without hitches and now an equalizer also.... :)

---

### Post by afrodeity on 2009-12-01
Congratulations, you've gone and done it!!! System wide equaliser for Ubuntu. Can't thank you enough, it was on my wishlist. Now all we need are mods, effects, some visualisation. Keeps getting better and better.This should definitely be part of the standard install. :)

I see there are cool presets!

Not sure how it relates to my onboard VT1708/A VIA Azalia HDAC onboard sound, but it easily throws up distortion. Will play some more with the pulsaudio levels to see what's up.Maybe there's a way to maximise integration with VIA?;)

---

### Post by afrodeity on 2009-12-01
Crikey, Pulseaudio is now eating my CPU, sitting at 53% when I check top! How do I lower this, I only have a 1.6 ghz Celeron?

UPDATE:It could be the Pulseaudio Volume Control, I see the CPU use for Pulsaudio went down all of a sudden, but this because card configuration got dumped.Its not showing up under configuration (no cards available for configuration). No sound, dummy output!

---

### Post by tonyriva on 2009-12-01
It seem that if the config file doesn't exist the gui doesn't create it and simply fail.

```
Traceback (most recent call last):
  File "/usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py", line 519, in <module>
    Equalizer()
  File "/usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py", line 354, in __init__
    GetSettings()
  File "/usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py", line 46, in GetSettings
    f = open(eqconfig, "r")
IOError: [Errno 2] Nessun file o directory: '/home/antonio/.pulse/equalizerrc'

```

I miss something?

---

### Post by afrodeity on 2009-12-02
Okay I have my pulseaudio volume control configuration which controls Azalia HDAC set to Analog Stereo Ouput + Digital Stereo (IEC958) Input.

There definitely some interactions going on between the Azalia and the LASDPA for example, both are listed in the Output Devices tab. Wonder if this just means I need a soundcard?

---

### Post by psyke83 on 2009-12-03
> **tonyriva said:**
> It seem that if the config file doesn't exist the gui doesn't create it and simply fail.

```
Traceback (most recent call last):
  File "/usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py", line 519, in <module>
    Equalizer()
  File "/usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py", line 354, in __init__
    GetSettings()
  File "/usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py", line 46, in GetSettings
    f = open(eqconfig, "r")
IOError: [Errno 2] Nessun file o directory: '/home/antonio/.pulse/equalizerrc'

```

I miss something?

The configuration file should be written automatically by the bash script at /usr/bin/pulseaudio-equalizer.sh.

If you had an older version of the script in /usr/local/bin/ (before it was packaged in .deb form), it will conflict with the newer version provided by the .deb package in /usr/bin/ - you should delete it.

```
$ sudo rm /usr/local/bin/pulseaudio-equalizer.sh
```

If your problem isn't solved, please send me the log from this command:
```
$ pulseaudio-equalizer.sh debug
```

---

### Post by phish3 on 2009-12-03
Hi - I'm one of the smaller time pulseaudio devs and it took me a long time to get around to replying to this thread but I thought I should mention that upstream pulseaudio has a native equalizer (with an unofficial ppa).  It should be officially released soon and available in the main audio PPAs for 9.10 
This equalizer has pretty much an infinite number of bands and is realtime and of higher quality... additionally mbeq lies about frequency meanings.
Looky at the front-end here:
[http://yasdb.blogspot.com/2009/08/qpaeq-dynamic-band-subdivision.html](http://yasdb.blogspot.com/2009/08/qpaeq-dynamic-band-subdivision.html)
How to setup here:
[http://www.pulseaudio.org/wiki/SystemEqualizer](http://www.pulseaudio.org/wiki/SystemEqualizer)

---

### Post by psyke83 on 2009-12-03
> **phish3 said:**
> Hi - I'm one of the smaller time pulseaudio devs and it took me a long time to get around to replying to this thread but I thought I should mention that upstream pulseaudio has a native equalizer (with an unofficial ppa).  It should be officially released soon and available in the main audio PPAs for 9.10 
This equalizer has pretty much an infinite number of bands and is realtime and of higher quality... additionally mbeq lies about frequency meanings.
Looky at the front-end here:
[http://yasdb.blogspot.com/2009/08/qpaeq-dynamic-band-subdivision.html](http://yasdb.blogspot.com/2009/08/qpaeq-dynamic-band-subdivision.html)
How to setup here:
[http://www.pulseaudio.org/wiki/SystemEqualizer](http://www.pulseaudio.org/wiki/SystemEqualizer)

Thanks for the info.

I tried using your qpaeq interface on a GNOME system (with the necessary eq-enabled pulseaudio packages from a PPA, and the proper python qt packages installed for the interface) and it didn't work. Also, are there any plans to release a GTK interface?

---

### Post by phish3 on 2009-12-04
> **psyke83 said:**
> Thanks for the info.

I tried using your qpaeq interface on a GNOME system (with the necessary eq-enabled pulseaudio packages from a PPA, and the proper python qt packages installed for the interface) and it didn't work. Also, are there any plans to release a GTK interface?

Recent build after instructions on the wiki above followed?  If so, can you post the errors or hop by freenode #pulseaudio to investigate the problem more?   I have no official plans for a gtk client but the backend uses dbus to communicate so you're free to create one and drop it in if you're adamant about not using qt.

---

### Post by NoVista on 2009-12-04
WoW!

What is that, 75 bands? I lost count.
That would make a killer notch filter for shortwave radio use.

---

### Post by sergio.ub on 2009-12-05
well, thank you all for your efforts.
Effectively, i have some questions and some suggestions about "official" and "psyche's" equalizer.
Since i embraced linux some years ago, i missed environmental effects applied to sound (who has audigy/x-fi or recent asus high-end cards and use win can realize what i mean). Still i have a win partition i use only to play songs (using AMAROK, although 2.1!) with the creative sound server. some presets of environmental effects (like theater, or new age) are really stunning.
Now, alsa doesn't manage in any way environmental audio. since no audio driver provides an interface for EAX/EFX builtin functions of high end audio cards it's a perfect task for Pulse Audio. 
PA has two ways od doing it:

1)Using OpenAL as a sink (also OpenAl-soft doesn't use computation power of audio processing units..that slows down cpu)
2)Using a LADSPA plugin for environmental audio (does it really exists???)

the first way seems to me more viable: openal-soft implements some enviromental effects, and is a multiplatform industry standard.
I had some cross posts with chris robinson (openal-soft father), suggesting him to move computation towars OpenCL to gain speed and decrease latency. it's a hard task and chris is alone. I'm not so much skilled to help him.

so my idea is:
1)use openal as a sink pilot it via equalizer.
2)help chris in moving cpu-critical routines to OpenCL.

---

### Post by phish3 on 2009-12-05
I've had whims on some digital audio effects before but couldn't really think of anything I'd really want to use for more than a few minutes.  If you can propose and fleshout a useful effect, I may consider it in the future (so far the only thing more I have planned is some new approaches to normalizing).  Also, the cpu usage for audio effects is pretty low on todays computers and I can improve the equalizer's backend a bit to do most of the work there for nearly the same cpu cost with most any combination of filters/effects.  Audio is one of those things were we can do alot of processing without hardware acceleration (way different story for images/graphics).

---

### Post by MattiViljanen on 2009-12-07
Thanks, the equalizer script works just fine! After some fine-tuning I actually find my old headphones barely acceptable again! Points for that!

And the new Pulseaudio equalizer... I downloaded the newer pulseaudio from here:
[https://launchpad.net/~ubuntu-audio-dev/+archive/ppa](https://launchpad.net/~ubuntu-audio-dev/+archive/ppa)
However, there is no module-dbus-protocol.so file in the pulseaudio package. Therefore, I can't test qpaeq.py script, nor the "newer and better" equalizer. So ATM I'm using 0.9.21 and pulseaudio-equalizer deb from the first post.

Has anyone managed to get the Python script working on 9.10 64-bit?

EDIT: There doesn't seem to be the missing DBUS module in nevions PPA neither... Back to square one. I also tried to compile Pulseaudio from git, but still nothing...

---

### Post by phish3 on 2009-12-08
> **MattiViljanen said:**
> Thanks, the equalizer script works just fine! After some fine-tuning I actually find my old headphones barely acceptable again! Points for that!

And the new Pulseaudio equalizer... I downloaded the newer pulseaudio from here:
[https://launchpad.net/~ubuntu-audio-dev/+archive/ppa]("https://launchpad.net/%7Eubuntu-audio-dev/+archive/ppa")
However, there is no module-dbus-protocol.so file in the pulseaudio package. Therefore, I can't test qpaeq.py script, nor the "newer and better" equalizer. So ATM I'm using 0.9.21 and pulseaudio-equalizer deb from the first post.

Has anyone managed to get the Python script working on 9.10 64-bit?

EDIT: There doesn't seem to be the missing DBUS module in nevions PPA neither... Back to square one. I also tried to compile Pulseaudio from git, but still nothing...

Sorry about that, I don't personally run ubuntu so I don't test it's packages as much.  The packages should be fixed now and at least include the modules themselves (I inspected the results myself :-).  Everything should work on 9.10 amd64 and i386.

On the compiling note you must have libfftw3-dev and libdbus1-dev installed for the modules to be enabled.

---

### Post by afrodeity on 2009-12-09
If I add the pulseaudio dev ppa will the equaliser get updated too?

---

### Post by Djzn.BR on 2009-12-09
Hi folks.

Currently, I am using Aqualung with this same Multiband EQ with the following values:

[B]4,14,14,6,2,2,2,2,2,2,2,2, 7.5 ,20,30
LATENCY 768,0[/B]

However, Aqualung only deals with RVA values instead of ReplayGain and also, the Music Store from Aqualung is a concept really hard to catch, so I am planning in abandoning this application. (Was using ultimately because of the FX EQ plugin feature).

Now I am using Songbird 1.2.0, and the built-in equalizer in it is crap. However, that is my replacement for now and it can benefit from this system wide equalizer. 

I want to find a way to turn off this PREAMP option in the python script, because it is only helping to distort the sound. So this preamp is a no-go for me, and my goal is to use the same setting I was using in Aqualung, so wich file do I need to edit and why the preset files have further values among the ones needed.

Thanks for any help.

---

### Post by urthmover on 2009-12-09
So what do I need to do to install this system wide equalizer after I've added the PPA from above?

sudo apt-get ?

---

### Post by citaworvk on 2009-12-10
Thank you. This works great.

---

### Post by betterthanjordan79 on 2009-12-10
This is brill!!!thaks a million!!!worked 100%!!!

---

### Post by afrodeity on 2009-12-11
Comparison between the two equalisors please!

---

### Post by phish3 on 2009-12-11
pros for the one included in pulseaudio mainstream:
realtime adjustments
unlimited bands* (qpaeq dynamically scales the bands to the width of the window)
higher accuracy than mbeq (the ladspa plugin the alternative relies on)
frequencies are natural (mbeq's frequencies are proportional to real frequencies)

*the limit is half the sample-rate of your master sink/sound card.  One cannot specify more any more useful information beyond that number of bands (theoretical limit).

inherent cons with the mbeq backed equalizer:
frequencies (coefficients you specify in control) above it's 1024 hz are ignored
aliasing occurs because the filter doesn't sample sufficiently
fixed number of bands (again, the bands above 1024hz are ignored)

Not really for this purpose but [here's a blog]("http://yasdb.blogspot.com/2009/08/equalization-abound.html") post I had written way back when detailing theoreticals of equalization and listing the problems with mbeq.

Also the thread original creator - sorry to be a bit of a thread jack but would you mind putting a link to this post and [http://pulseaudio.org/wiki/SystemEqualizer](http://pulseaudio.org/wiki/SystemEqualizer) listing it as an upstream alternative?

---

### Post by ozguitarplayer on 2009-12-13
Hi,
New install of Karmic Koala.
PulseAudio Multiband installed from a .deb file link supplied in this topic.

You mentioned PulseAudio mainstream has realtime adjustments, where can I find the mainstream version?

---

### Post by rdingram on 2009-12-13
Thank you. Thank you. Thank you. I have been looking for something like this for some time. Makes the laptop speakers useable!

---

### Post by ~Las~ on 2009-12-14
Thanx a lot..waited for this for a long time :-)

---

### Post by mocha on 2009-12-14
WOW!  Why isn't this a default addon to the distro pulseaudio packages??  I'm only seeing about 2% sporadic CPU increase with pulseaudio as well.  Excellent work.

---

### Post by ivotron on 2009-12-15
Dude, you're my hero, thanks much for this. This should be definitively included for 10.4 (Lucid)

---

### Post by afrodeity on 2009-12-16
If anybody is getting kludgy sound, just turn down the pre-amp.Usually the source of bother with the presets overloading the system. If sound borks (doesn't get louder, it just fails in certain frequencies), then turn the preamp setting down.So default should be generally lower. Just my two cents.:)

---

### Post by johoe on 2009-12-16
Hi there!

This here is really what I've been looking for my whole "linux-life"! Sound is so much better now
BUT I warmly recommend using the pulseaudio-equalizer from **phish3** ([COLOR="Red"][http://ubuntuforums.org/showpost.php?p=8436269&postcount=115]("http://ubuntuforums.org/showpost.php?p=8436269&postcount=115")[/COLOR]) - it's so much better! You get realtime adjustments, no distortion whatever pre-amp is set etc. and most important: simply brilliant sound!
All what you need and what you have to do is explained here: [COLOR="Red"][http://pulseaudio.org/wiki/SystemEqualizer]("http://pulseaudio.org/wiki/SystemEqualizer")
[/COLOR]
This should got to the official ubuntu-audio-dev ppa!

We just need a gtk interface - see, what I can do about this ;)

Great work!!

regards, johoe

---

### Post by sbersier on 2009-12-16
> **johoe said:**
> Hi there!

This here is really what I've been looking for my whole "linux-life"! Sound is so much better now
BUT I warmly recommend using the pulseaudio-equalizer from **phish3** ([COLOR="Red"][http://ubuntuforums.org/showpost.php?p=8436269&postcount=115]("http://ubuntuforums.org/showpost.php?p=8436269&postcount=115")[/COLOR]) - it's so much better! You get realtime adjustments, no distortion whatever pre-amp is set etc. and most important: simply brilliant sound!
All what you need and what you have to do is explained here: [COLOR="Red"][http://pulseaudio.org/wiki/SystemEqualizer]("http://pulseaudio.org/wiki/SystemEqualizer")
[/COLOR]
This should got to the official ubuntu-audio-dev ppa!

We just need a gtk interface - see, what I can do about this ;)

Great work!!

regards, johoe
Well, I'm glad qpaeq works for you... I have Ubuntu Karmic 32 bits. I've tried to make it work. I've followed strictly the procedure indicated. But there is a problem with the dbus protocol module (I have it installed as well as fftw3 ).
Can you tell me what version of Ubuntu you're using? And is your computer 32 or 64bits?
Thanks,
Stéph

---

### Post by johoe on 2009-12-16
> **sbersier said:**
> Well, I'm glad qpaeq works for you... I have Ubuntu Karmic 32 bits. I've tried to make it work. I've followed strictly the procedure indicated. But there is a problem with the dbus protocol module (I have it installed as well as fftw3 ).
Can you tell me what version of Ubuntu you're using? And is your computer 32 or 64bits?
Thanks,
Stéph

hmm, I'am running exactly the same version (karmic/32bit) as you do. I've installed it on two different machines.
I installed these packackes
python, python-dbus, python-qt4 and python-qt4-dbus
of course you need some of the libqt4-* libraries too.

maybe you can post the the error you get...

johoe

---

### Post by sbersier on 2009-12-16
> **johoe said:**
> hmm, I'am running exactly the same version (karmic/32bit) as you do. I've installed it on two different machines.
I installed these packackes
python, python-dbus, python-qt4 and python-qt4-dbus
of course you need some of the libqt4-* libraries too.

maybe you can post the the error you get...

johoe
libdbus-1, libfftw3, python, python-dbus, ..., python-qt4* are all installed. The problem shows up at the install stage and solely for module-equalizer-sink which has undefined references to pa_dbus_*** stuff.... 
Well, I'll stick to the pulseaudio-equalizer.py script for the moment. It works...

---

### Post by phish3 on 2009-12-16
I think I figured it out - you probably need libdbus-1-dev installed (and to rerun configure), I updated the wiki to mention this.  This should only be needed if you're compiling from source... the packages seem to work fine although it looks like I forgot to include qpaeq. There are download links on the wiki.  In source compiling case you might also want to place "0.9.21" inside .tarball-version in the sourcetree to force the git-version-gen script to detect the build as 0.9.21... else you'll get 0.9.19 and issues might ensue... all due to upstream muckery with git, sorry.

---

### Post by buddyd16 on 2009-12-16
Thank you very much for this. I can now watch tv using my capture card without the god awful audio it had before I used this utility.

---

### Post by dhruv_1884 on 2009-12-16
This is absolutely awesome. Have been waiting for this for a realllllly long time.

finally we have the  Power of Pulse :guitar:

---

### Post by sbersier on 2009-12-17
> **phish3 said:**
> I think I figured it out - you probably need libdbus-1-dev installed (and to rerun configure), I updated the wiki to mention this.  This should only be needed if you're compiling from source... the packages seem to work fine although it looks like I forgot to include qpaeq. There are download links on the wiki.  In source compiling case you might also want to place "0.9.21" inside .tarball-version in the sourcetree to force the git-version-gen script to detect the build as 0.9.21... else you'll get 0.9.19 and issues might ensue... all due to upstream muckery with git, sorry.
In fact, it looks like what was missing was libdbus-qt-1-dev (you should check that and possibly add it to your wiki instructions). After I installed it I could install everything.
But... As soon as I load the "module-equalizer-sink" module the sound is chopped (about 5 times/second) making the sound just unhearable and makes the qpaeq.py script useless.... I tried with and without tsched=0.
Furthermore, now the pulseaudio-equalizer.sh shell script doesn't work anymore...

```

steph@steph-desktop:/usr/share/pulseaudio-equalizer$ pulseaudio-equalizer.sh enable
PulseAudio Equalizer/LADSPA Processor 2.4 (19/11/2009)
-------------------------------------
Current operation: enabling equalizer
-------------------------------------
Suspending clients...
Unloading module-ladspa-sink...
Unloading & reloading stream-restore module...
Loading module-ladspa-sink...
Moving active PulseAudio clients to LADSPA sink (ladspa_output.mbeq_1197.mbeq)...

```And it get stuck there...
 So, I don't have any equalizer anymore.
Not good, not good...

---

### Post by phish3 on 2009-12-17
Regarding the choppyness... did you have pavucontrol opened or any instances of flash while it was getting choppy? I've heard of some problems like this when there are 1 or more instances of flash and other sound programs opened - no clear reason why, but flash is always a problem child for sound.  Also what kind of cpu do you have and do you have powersaving mode enabled (cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor)

As for getting back to the old equalizer, make uninstall since it looks like you're trying to compile from sources (I generally wouldn't recommend that) and remove the relevant entries from your /etc/pulse/default.pa.

HTH

---

### Post by brookie on 2009-12-18
Thanks man! 
I added the ubuntu audio ppa listed in the first post for karmic, ran update manager and it did a partial upgrade. Downloaded the .deb and installed it and "voila!". This old laptop on these old speakers sounds awesome on the 'Rock' setting. 
What a great Christmas present! 
Cheers, 
brook

---

### Post by afrodeity on 2009-12-19
I changed the settings in the pavucontrol, looking for a better setting. Now my volume control has disappeared in the panel, and pavucontrol won't connect. If I try to open pavucontrol, it tells me "Connection failed, Connection refused"

```

pulseaudio
E: module-udev-detect.c: Failed to get card object.
E: module-ladspa-sink.c: Master sink not found
E: module.c: Failed to load  module "module-ladspa-sink" (argument: "sink_name=ladspa_output.mbeq_1197.mbeq master= plugin=mbeq_1197 label=mbeq control=0.0,0.0,0.0,0.0,0.0,-4.5,-10.0,-6.0,0.5,1.0,2.0,4.0,4.0,0.0,0.0"): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.

```

and 

```

 killall pulseasudio
pulseasudio: no process found

```

I I try sound settings
System > Sound

I get "Waiting for sound system to respond"

How do I manually change the pacucontrol settings?

---

### Post by brookie on 2009-12-19
By the way, 
Any idea as to why Ubuntu Karmic does a Partial Distribution Upgrade when the [Ubuntu Audio Dev PPA]("https://launchpad.net/%7Eubuntu-audio-dev/+archive/ppa") is added to Software Sources, and Update Manager is run? 

Just askin? :O

---

### Post by xl_cheese on 2009-12-20
I just installed this and I am not getting any EQing on my system when I apply the changes.  I hear a brief audio pause and then it's the same as before.  

Is there anything else I need to do?  Do I need to restart my computer after installing?

---

### Post by psyke83 on 2009-12-20
phish3,

Can you please start a new thread regarding your equalizer implementation? This is only causing confusion for new users who are trying your patched packages with my script, and I may decide to continue improving the script beyond equalization (e.g., to support multiple LADSPA plugins on the interface). As soon as you make the new thread, I'll edit the first post with the link.

---

### Post by sanket_s on 2009-12-21
One small bug (or may be a glitch) on Karmic, I installed and when i try presets and as soon as i press apply, my sound tray icon is kinda restarted, wanted to know if its like that in the settings to restart the sound or its crashing and restored on its own... following is from the logs, most likely showing each time I applied a new preset...

messages:
Dec 21 18:50:00 ... pulseaudio[1875]: ratelimit.c: 71 events suppressed
Dec 21 18:50:05 ... pulseaudio[1875]: ratelimit.c: 24 events suppressed
Dec 21 18:50:12 ... pulseaudio[1875]: ratelimit.c: 17 events suppressed
Dec 21 18:50:18 ... pulseaudio[1875]: ratelimit.c: 17 events suppressed
Dec 21 18:50:24 ... pulseaudio[1875]: ratelimit.c: 24 events suppressed
Dec 21 18:50:29 ... pulseaudio[1875]: ratelimit.c: 58 events suppressed

---

### Post by adlin5000 on 2009-12-21
Thanks. I have been looking for an equalizer for Ubuntu for a while now. This does everything I need and quite well.

The only gripe, and a minor one, is that every change regardless of if the equalizer is enabled, causes the audio to cut out for a sec. Maybe you could find a way to only make changes when the apply button is hit?

Thanks again.

---

### Post by Indigo340 on 2009-12-22
Thanks for a great equaliser !  :P:):P

I was having some problems to begin with so I read through this entire thread to see if anyone else had them and what could be done about them.
The funny thing is that I happened to experience almost all of the problems in this thread !
The only one that I dealt with was the volume level that was out of sync with my global controller, when using the volume control the volume level would drop dramatically, this was easy to put right by following the good advice.
All the others including, scratchy sounds when adjusting volume control, clipping, not saving volume level between tracks, volume level not being remembered on re-boot etc they all 'fixed themselves' after lowering the slider levels and fine tuning for my system.

I first thought that having such a huge scale for each slider would be way too much for the simple soundcard in my old laptop and I was partly correct but as I played with it more and more I realised that the Pre-Amp control has way more than enough 'gain'. Once I turned it down to 1.2, I found it more than sufficient and I could then get a better balance when also reducing the the EQ sliders into the negative range, reducing Pre-Amp level to 1 meant that I could actually increase some of the EQ sliders a fraction into the positive range without problems.

So I have a some suggestions for improvements;

[LIST=1]
[*]Give the Pre-Amp control a minus or negative range maybe down to -1.0 that would allow the equaliser sliders to actually add db in the required ranges and reduce the maximum Pre-Amp gain to +1.5
[*]The EQ ranges could also be reduced, plus or minus 30db is way too much range, half of that would be adequate.
[*]Please Please Please try to remove the need to click 'Apply Settings' it is very annoying and makes fine tuning very difficult.
[*]Or better still, tell me how to re-set these ranges myself, I am a noob so try to use words and phrases I can understand. :)
[/LIST]

---

### Post by brookie on 2009-12-22
FYI, I found a post explaining a bit about the Partial Dist. Upgrade I experienced after adding the Ubuntu Audio Dev ppa to my sources and running Update Manager. 

Here is the [link]("http://ubuntuforums.org/showthread.php?t=1343434") to that post in case someone else experienced this. 

The EQ and Pulseaudio are working fine though. 

Cheers, 
brook

---

### Post by jabezkaiser on 2009-12-22
This is really great, now I get better sound quality on my laptop. A question, I am having a bit problem with adobe-flashplugin in browsers, it doesn't use PulseAudio Equalizer. how can I configure it to use  PulseAudio Equalizer and not the Internes Audio Anlog Stereo?? Here my Audio Setting window.

[ATTACH]140872[/ATTACH]

---

### Post by dreadyman on 2009-12-23
Just thanks, you did it!

Hope it will be included by default in lucid lynx !

---

### Post by brookie on 2009-12-23
Hey psyke83,

I just upgraded to[ rhythmbox - 0.12.6-0ubuntu1]("https://launchpad.net/%7Ejmatthew/+archive/ppa") on Karmic and I don't hear that popping/skipping sound anymore when adjusting the volume with the mouse wheel. 

Just thought I'd let you know.  The changelog for Rhythmbox is [here]("http://ftp.gnome.org/pub/GNOME/sources/rhythmbox/0.12/rhythmbox-0.12.6.changes") but I was working on a podcast glitch and found [this changlog]("https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/451176") at launchpad which says something about fixing: 
499051 - xfade backend doesn't play nice with LADSPA filters 

Maybe that was the trick? Anyhow, thanks again for this awesome EQ. 

Merry Christmas,
brook

ps - just played Rhythmbox for an hour, popping sound came back (after listening to a podcast) when adjusting volume with mouse wheel, restarted rhythmbox, and no popping when adjusting volume. seems like the poppins starts after rhythmbox has been playing a while??? ...after a couple of more hours just listening to music, no popping still!

---

### Post by promet on 2009-12-24
You sir, are an officer, a gentleman, a saint and a scholar.

I am going to begin taking up a collection to erect some classical statuary in your honor...

This really puts the cherry on the sundae of Karmic Koala for me; just outstanding, also...Merry Christmas to me! ;)

Cheers

---

### Post by jorrieboy on 2009-12-25
I have a problem with this.

When I listen music I hear all the time a weird "popping" noise...
I use the rock preset, and my preamp is 1.0x
I have tried this with al lot of songs, but i still hear the "popping" noise all the time.
p.s. the music i listen is rock/metal

Does somone have a solution for this problem?

(sorry if my English is not so good...)

---

### Post by jonathanfrancisco on 2009-12-26
:guitar:   this solutions really rocks! thanks so much!

---

### Post by kernel_script on 2009-12-28
Hello psyke83, thank you very much for sharing this man, really really great work!

Please, which is the license of it?

---

### Post by claytronic on 2009-12-28
Add my thanks as well. This script just supercharged my whole Ubuntu audio experience!

:guitar:

---

### Post by promet on 2009-12-29
Another interesting note. In addition to making my regular desktop box a righteous rock machine; I've also installed this on an eeepc where I am running the Karmic Netbook Remix.

This little guy was really producing some, truly, weak sound, but now with the PulseAudio Equalizer script, I can pump up and adjust the audio on that sucker (4G 701) and really push those tiny speakers, and so now can listen to good streaming net audio in the kitchen while I'm cooking, or streaming internet news radio stations when I shower...

Gasp! I fear I have shared too much! :p Hahahaha!

Cheers!

---

### Post by helliewm on 2009-12-29
The sound on whatever setting-classical.pop,softrock is really tinny and awful. I have an Audiologu sound card and medium priced £70 Logitech speakers with subwoofer/ Also its really tinny on my N130 Netbook too.

The AlSA Gamix mixer seems much better? Or am I doing something wrong??.

---

### Post by jorrieboy on 2009-12-30
> **jorrieboy said:**
> I have a problem with this.

When I listen music I hear all the time a weird "popping" noise...
I use the rock preset, and my preamp is 1.0x
I have tried this with al lot of songs, but i still hear the "popping" noise all the time.
p.s. the music i listen is rock/metal

Does somone have a solution for this problem?

(sorry if my English is not so good...)

Can I PLEASE have an awnser for this problem?!

---

### Post by promet on 2009-12-30
jorrieboy

do you have "**gnome-alsamixer**" installed? You may have your PCM setting too high, which will produce some distortion at high app volumes. There are, honestly, a lot of things that could be causing that.

Sometimes there are several sound system sliders controlling the volumes of system sound. I like to go into **gnome-alsamixer**, **PulseAudio Volume Control **(pavucontrol), and the other volume/mixer controls on my system. I set all of the **output, PCM** and other relevant sliders down to about 50% to make sure nothing is "spiking" **and then** go into the **"new" Pulseaudio Equalizer** and do my "**fine tuning**" in there...

Also, if you use a** microphone or other input device**, I would try **muting those** also, **when they are not in use**. This sometimes messes with Ubuntu sound, this can be done in the same mixer/volume control apps.

Without a more detailed explanation of your sound system, it is hard to offer more specific help than that. I hope this is helpful on some level though.

Cheers...

---

### Post by jorrieboy on 2010-01-01
Thanks, the sound quality is a lot better now.

---

### Post by promet on 2010-01-01
Why you're very welcome, glad I could be of some help...

Happy New Year (in which Ubuntu will kick further tail!)

---

### Post by vauge on 2010-01-02
++1

Thank you.

---

### Post by joel.bacal on 2010-01-03
hey! I want to know.. how to uninstalla the script from the computer... I installed it, but got problem changing the volume when I was listening to music..

Now I uninstalled the deb package, but still have the ladspa plugin marked as my default output in the pulseaudio manager.

Thanks in advance!

---

### Post by funnylife_ma on 2010-01-03
thanks to psyche83, this great piece of software is now in main Fedora 12 repositories

---

### Post by 741Baus on 2010-01-08
Thanks psyche83 this is a awesome bit of kit :guitar:

---

### Post by gilson585 on 2010-01-09
I must say this is a sweet little tool. Thanks so much for posting this. May I request that the preamp be able to go below 1x and the eq bands be adjustable. Even as it is it is great thx so much. This should be added to the Ubuntu repo's.

For example if it could follow the 2/3 octave standard like this dual dbx pro unit [http://www.dbxpro.com/215/215.php](http://www.dbxpro.com/215/215.php)

---

### Post by diddy1234 on 2010-01-09
Could I also request this be added either as standard or as a repo add on ?

How do we go about getting Ubuntu to include this ?

Sound has always been a bit lagging in linux as in windows i had a general graphic equalizer once the sound card drivers were installed.

This add on would compliment users from windows.
After all a windows user would expect the same functionality in Ubuntu (linux users tend to over see this major factor).

regarding the frequency banding, I know that this can be edited by the user (as I have done) but it would be nice if 30hz existed as well as 15khz (between 10khz and 20khz).

There seems to be too many mid range bands, are these needed ?

The 10khz and 20khz cover too much frequency range.

---

### Post by towheedm on 2010-01-10
Has anyone verified the centre frequencies of mbeq that the PulseAudio Eq Script depends on?  I installed the PulseAudio Eq Script and basically it works.  However, I find it next to impossible to set the eq to my liking.  I'm comparing this to using WinAmp under WinXP and trying to get comparable quality.

Reading the post by phish3 he says > additionally mbeq lies about frequency meanings..  So I decided to test this statement to see if this was why I find it so difficult to adjust the eq to my liking.

I modified the following line in the pulseaudio-equalizer.sh as follows:

```
PA_LADSPA_INPUTS="30,60,120,180,240,360,420,480,540,600,660,720,780,1000,2000"
```I then created a new preset using the Flat preset as a template but modified the frequency values to reflect the changes made above.

I reset the equalizer using the "Reset to default" option under the Advanced menu and then selected my new preset from the presets list.  As you can see from the above, my highest frequency is 2K.  However, when I tested the preset, the 2K slider was still adjusting the high frequencies (20K) and not the mid-band as I expected.

Again my question is has anyone tested the frequencies from mbeq or is this a bug either in mbeq or the pulseaudio-equalizer.sh script?  Am I going about this the wrong way and is there someway to change these frequency values?

Does anyone know the Q of the frequency bands or the technical specs of the DSP routines used by mbeq?  I think this would greatly help in determining the optimum centre frequency for the various bands.

Thanks.

---

### Post by phish3 on 2010-01-10
> **towheedm said:**
> 
Reading the post by phish3 he says...

This is in reference to mbeq's processing which is not sampled sufficiently (sampled at IIRC 1024hz, I believe the control points specified above 1024 were also ignored) and who's hz (control points) are *proportional* to real x/second hz that we hear in.  So frequencies are not as advertised and a crapload of aliasing occurs.  See bottom 2 graphics [here]("http://www.danbullard.com/dan/aliasing.html")

> **towheedm said:**
> 

Again my question is has anyone tested the frequencies from mbeq or is this a bug either in mbeq or the pulseaudio-equalizer.sh script?  Am I going about this the wrong way and is there someway to change these frequency values?


I don't think this is mbeq's fault.

> **towheedm said:**
> 
Does anyone know the Q of the frequency bands or the technical specs of the DSP routines used by mbeq?  I think this would greatly help in determining the optimum centre frequency for the various bands.

mbeq uses an FFT/FIR filter, thus there is no Q parameter.

---

### Post by towheedm on 2010-01-10
OK thanks.

So I decided to try your qpaeq equalizer.  Since the binary was not listed in the PPA you provided at [html]http://pulseaudio.org/wiki/SystemEqualizer[/html] I downloaded the qpaeq.py script from sourceforge.

I uninstalled psyke83 script completely including all configuation files and then I installed all required dependencies for qpaeq and modifed the /etc/pulse/default.pa as stated.  Two problems:

1.  I launch the equalizer using ```
python qpaeq.py 
```.  After the window opens, pulseaudio CPU usage goes to 100%.  Also when I try to play music using Rythmbox there is no sound.  I have included the master=alsa...... to reflect my soundcard.  The FFT based equalizer shows up on PA volume control and is selected.  I have tried everything I could think off but still no sound.  The FFT equalizer is definitely selected as the sink.  Also, the progress bar in Rythymbox jumps in 5sec intervals.  I do not think I have freq scaling or whatever you call that.

2.  If I try to resize the window, then the weirdest thing happens:  python qpaeq.py process memory usage starts climbing from 53MiB to over 800Mib and its CPU usage goes to 100%.

What have I done wrong?

How can I get a binary without having to compile.  I am not to familiar with compiling.

Thanks phish3.

---

### Post by phish3 on 2010-01-11
I don't think it is necessary to uninstall psyke83's script.  Anywho, first make sure you have working sound and just to be sure try a non rythmbox sound test, preferably something with native pulse output (not alsa). Also make sure to test with pavucontrol closed and see if that results in a change.  Please pulseaudio -k && pulseaudio -D after you've closed pavucontrol.

Re 2: cpu usage should jump for a second and go back down  to normal as part of the resizing process, but the qpaeq python process shouldn't take more than like 40 MiB tops, try the git versions to see if they help...

---

### Post by duffydack on 2010-01-11
I found this from the PulseAudio Fixes & System-Wide Equalizer Support thread.  Never did any modifications, just installed the EQ application and it works a treat. Well there are 2 minor quirks, when I move the volume slider I get crackling, and playing SID files (using Audacious2) causes audacious to use a lot of cpu and speed through the track likes on fast-forward...apart from those, it sounds a whole lot better.
Using Karmic btw

*edit* I fixed the sid problem by setting the output from 44100 to 22050 in the sid plugin preferences.  Seems anything higher than 22050 speeds it up

---

### Post by towheedm on 2010-01-11
> **phish3 said:**
> I don't think it is necessary to uninstall psyke83's script.  Anywho, first make sure you have working sound and just to be sure try a non rythmbox sound test, preferably something with native pulse output (not alsa). Also make sure to test with pavucontrol closed and see if that results in a change.  Please pulseaudio -k && pulseaudio -D after you've closed pavucontrol.

Re 2: cpu usage should jump for a second and go back down  to normal as part of the resizing process, but the qpaeq python process shouldn't take more than like 40 MiB tops, try the git versions to see if they help...
Well it took me a bit to figure that GIT was similar to souceforge.  Please excuse my ignorance.  So I D/L'ed the file from GIT.  But before that, pulseaudio works properly on my system even with Rythymbox.  Did the whole HOWTO Pulseaudio Fixes thing from the first post in this thread.

I used pavucontrol to verify that the FFT equalizer was selected as the default sink and that my SoundBlaster was not muted, then daemonized pulseaudio.  Opened Rythymbox and got the qpaeq to work.  BTW, much much much better quality.  However, problem #2 still exists.  If I try to resize the qpaeq window, it becomes non-responsive and starts eating memory.  I looked at the memory map using the system monitor and saw that the heap was eating all of the memory, looks like a bug in Python to me.  qpaeq.py memory usage was quite low.  After leaving it for about 15mins, it chewed up all of my physical memory and about 1GiB of swap.

The other thing now is that once I restart and log in, the SoundBlaster is always muted so I have to pavucontrol and unmute it.  But once I do this, close pavucontrol, daemonize PA launch qpaeq and open up Rythymbox, there's nice sound.  Unfortunately, once I daemonize PA I loose the ability to control the volume with the volume control on my kybd.  Any suggestions on these two issues, especially the resizing will be greatly appreciated.

I will try and compile although I have never ever had to before.  My only programming experience is with VisualBasic and VBA under Windows.  BTW, went into GNOME Alsa Mixer and turned on the 3D Control.  PA + qpaeq + 3D = WOW WOW WOW!

Thanks.

Using Karmic with latest updates, P4 2.8GHz 1MiB RAM 2GiB swap.

---

### Post by phish3 on 2010-01-12
I made a thread for the upstream/qpaeq based equalizer, please direct relevant posts here [http://ubuntuforums.org/showthread.php?t=1378087]("http://ubuntuforums.org/showthread.php?t=1378087")

---

### Post by repsakkgn on 2010-01-14
im running ubuntu 9.10 with latest updates. I've installed the attached .deb, while installing it downloaded 2 files. now i've got P-A-equalizer in gnome menu, but it will not start. the output in console says "Traceback (most recent call last):
  File "/usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py", line 519, in <module>
    Equalizer()
  File "/usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py", line 354, in __init__
    GetSettings()
  File "/usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py", line 62, in GetSettings
    persistence = int(rawdata[6])
ValueError: invalid literal for int() with base 10: ''
"
what should i do? the idea is awesome, and i'd like to try....

---

### Post by psyke83 on 2010-01-15
> **repsakkgn said:**
> im running ubuntu 9.10 with latest updates. I've installed the attached .deb, while installing it downloaded 2 files. now i've got P-A-equalizer in gnome menu, but it will not start. the output in console says "Traceback (most recent call last):
  File "/usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py", line 519, in <module>
    Equalizer()
  File "/usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py", line 354, in __init__
    GetSettings()
  File "/usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py", line 62, in GetSettings
    persistence = int(rawdata[6])
ValueError: invalid literal for int() with base 10: ''
"
what should i do? the idea is awesome, and i'd like to try....

Did you previously test the equalizer before it was packaged in .deb form? If so, delete the old script and the saved settings:
```
$ sudo rm /usr/local/bin/pulseaudio-equalizer.sh
$ rm ~/.pulse/equalizerrc*
```

Then try again.

---

### Post by psyke83 on 2010-01-15
> **phish3 said:**
> I made a thread for the upstream/qpaeq based equalizer, please direct relevant posts here [http://ubuntuforums.org/showthread.php?t=1378087]("http://ubuntuforums.org/showthread.php?t=1378087")

Thanks, I've provided a link to your thread in the first post.

---

### Post by psyke83 on 2010-01-15
> **diddy1234 said:**
> Could I also request this be added either as standard or as a repo add on ?

How do we go about getting Ubuntu to include this ?

I'm not sure if that's worthwhile, considering the alternative EQ implementations for PulseAudio which are currently superior. I wrote the script and Python interface for some fun and for some practice in programming in Python, but the code is a mess. I haven't even moved the source to a suitable repository yet (though I will soon).

> regarding the frequency banding, I know that this can be edited by the user (as I have done) but it would be nice if 30hz existed as well as 15khz (between 10khz and 20khz).

The script cannot offer bands which are not already supported by the LADSPA plugin currently in use. Version 2.4 uses the mbeq_1197" plugin. Take a look at the plugin information:

```
conn@inspiron:~$ analyseplugin mbeq_1197

Plugin Name: "Multiband EQ"
Plugin Label: "mbeq"
Plugin Unique ID: 1197
Maker: "Steve Harris <steve@plugin.org.uk>"
Copyright: "GPL"
Must Run Real-Time: No
Has activate() Function: Yes
Has deativate() Function: No
Has run_adding() Function: Yes
Environment: Normal or Hard Real-Time
Ports:	"50Hz gain (low shelving)" input, control, -70 to 30, default 0
	"100Hz gain" input, control, -70 to 30, default 0
	"156Hz gain" input, control, -70 to 30, default 0
	"220Hz gain" input, control, -70 to 30, default 0
	"311Hz gain" input, control, -70 to 30, default 0
	"440Hz gain" input, control, -70 to 30, default 0
	"622Hz gain" input, control, -70 to 30, default 0
	"880Hz gain" input, control, -70 to 30, default 0
	"1250Hz gain" input, control, -70 to 30, default 0
	"1750Hz gain" input, control, -70 to 30, default 0
	"2500Hz gain" input, control, -70 to 30, default 0
	"3500Hz gain" input, control, -70 to 30, default 0
	"5000Hz gain" input, control, -70 to 30, default 0
	"10000Hz gain" input, control, -70 to 30, default 0
	"20000Hz gain" input, control, -70 to 30, default 0
	"Input" input, audio
	"Output" output, audio
	"latency" output, control

```

> There seems to be too many mid range bands, are these needed ?

The 10khz and 20khz cover too much frequency range.

There's no need to hide them, either.

What I have done is constrain the negative and positive ranges for the control ranges, because the mbeq_1197 filter tends to introduce aliasing/distortion when you set the gain to any positive value, and also to make user adjustments of the sliders more convenient.

With exception to "Laptop", all the included presets suffer from this problem (as they're ported from VLC's equalizer, which does not have distortion problems). Recently, I haven't had time to investigate ways to mitigate this problem (and not many ladspa EQ plugins currently exist).

---

### Post by incontinentiabuttocks on 2010-01-18
Can I just say, as a relative newbie to Ubuntu (and linux in general) that I am extremely grateful for the creator/s of this package. I had been searching for one of these for over 2 years and now that I've found one, I will most likely stick to Ubuntu for a very long time (it was the main reason for me going back to Windows for a while - I like my sound)

Thanks once again.

---

### Post by diddy1234 on 2010-01-26
Thanks for your reply.

I still think its an excellent add on.

I will look at your other post regarding a better control

If I were to implement a better control, how do i remove this current installation ?

Id rather not compile from source just yet, hence your current files are easy to install and get working.

---

### Post by Sparckus on 2010-01-28
Works a treat thanks very much :)

---

### Post by frogotronic on 2010-01-28
OH YEAH BABY!!!!!


"HELL's BELL's" never sounded so damm good....


:popcorn:

---

### Post by matej_jack on 2010-01-30
Is it possible to change frequencies? I would like to change 20Hz, 30Hz, 50Hz and 60Hz.
The lowest possible now is 50Hz, then 100Hz. :frown:

---

### Post by duffydack on 2010-01-30
> **cement_head said:**
> OH YEAH BABY!!!!!


"HELL's BELL's" never sounded so damm good....


:popcorn:

LOL, nice.. I admit, the quality, with a laptop, even a studio17 with JBL speakers, is awesome.

---

### Post by ktp on 2010-02-02
First this is great...makes me want to get really good speaks now!!

One question...how can I keep the set alsamixer's "Master" volume.  Every time system restart or I hit apply in EQ, the master volume goes 100% and I get humming noise.  If I set it at like 92% or disable the EQ, I don't hear the humming noise.  Anything I can do to make sure the master volume is at 92%?  I sure don't want to disable EQ. =)

---

### Post by psyke83 on 2010-02-03
> **ktp said:**
> First this is great...makes me want to get really good speaks now!!

One question...how can I keep the set alsamixer's "Master" volume.  Every time system restart or I hit apply in EQ, the master volume goes 100% and I get humming noise.  If I set it at like 92% or disable the EQ, I don't hear the humming noise.  Anything I can do to make sure the master volume is at 92%?  I sure don't want to disable EQ. =)

You would need to set the pre-amp to (roughly) 0.9x, which isn't yet possible in v2.4. I'll add this capability in the next version (as soon as I set up a new installation - my laptop died).

Edit: OK, I've updated to v2.5 which allows preamp levels below 1x. You can find the new version within the pulseaudio-equalizer_2.5debsrc.tar.bz2 archive (as it seems the forum no longer allows .deb attachments). When I get time, I intend to publish the source on Launchpad and will make future versions available from my PPA.

---

### Post by ktp on 2010-02-04
Thanks so much!!  PPA would be great also.

---

### Post by ktp on 2010-02-04
I just tried the latest and set preamp to .8 but sound server seems to not start on restart the system with following error:
```
pulseaudio[2034]: module.c: Failed to load  module "module-stream-restore" (argument: "restore_device=false restore_device=false restore_device=false restore_device=false restore_device=false restore_device=false restore_device=false restore_device=false restore_device=false restore_device=false restore_device=false restore_device=false restore_device=false restore_device=false restore_device=false restore_device=false"): initialization failed.
main.c: Module load failed.
main.c: Failed to initialize daemon.
```

I have to clean out the ~/.pulse/ directory to fix it.  I tried it twice and then went back to previous version.

---

### Post by psyke83 on 2010-02-04
> **ktp said:**
> I just tried the latest and set preamp to .8 but sound server seems to not start on restart the system with following error:
```
pulseaudio[2034]: module.c: Failed to load  module "module-stream-restore" (argument: "restore_device=false restore_device=false restore_device=false restore_device=false restore_device=false restore_device=false restore_device=false restore_device=false restore_device=false restore_device=false restore_device=false restore_device=false restore_device=false restore_device=false restore_device=false restore_device=false"): initialization failed.
main.c: Module load failed.
main.c: Failed to initialize daemon.
```

I have to clean out the ~/.pulse/ directory to fix it.  I tried it twice and then went back to previous version.

The problem is that v2.4 of the script searched for the phrase "Generated from: pulseaudio-equalizer.sh" in the ~/.pulse/default.pa file, and if it found the phrase then it will know that the equalizer configuration is active.

However, with version 2.5, I dropped the **.sh** suffix (now it looks for "Generated from: pulseaudio-equalizer"), so the script wasn't detecting the old configuration files correctly. Deleting ~/.pulse/default.pa* once should solve the problem permanently.

Can you confirm that v2.5 is now working correctly after having deleted the stale configuration?

---

### Post by psyke83 on 2010-02-05
> **ktp said:**
> I just tried the latest and set preamp to .8 but sound server seems to not start on restart the system with following error:
```
pulseaudio[2034]: module.c: Failed to load  module "module-stream-restore" (argument: "restore_device=false restore_device=false restore_device=false restore_device=false restore_device=false restore_device=false restore_device=false restore_device=false restore_device=false restore_device=false restore_device=false restore_device=false restore_device=false restore_device=false restore_device=false restore_device=false"): initialization failed.
main.c: Module load failed.
main.c: Failed to initialize daemon.
```

I have to clean out the ~/.pulse/ directory to fix it.  I tried it twice and then went back to previous version.

Update: the equalizer is now available from my PPA (and the bug has been fixed).

I recommend that you first install the latest version (through my PPA), and then delete your ~/.pulse/default.pa* files to get rid of the invalid configuration that's still potentially on your system. Thanks.

---

### Post by ktp on 2010-02-05
> **psyke83 said:**
> Update: the equalizer is now available from my PPA (and the bug has been fixed).

I recommend that you first install the latest version (through my PPA), and then delete your ~/.pulse/default.pa* files to get rid of the invalid configuration that's still potentially on your system. Thanks.

It's working great now (using PPA).  Thanks!!

---

### Post by duffydack on 2010-02-06
My volume control applet keeps disappearing after installing the newer version..  also, any other sounds like my email notify sound and system sounds while i`m playing music with any application, is just a clicking static sort of sound...

---

### Post by psyke83 on 2010-02-06
> **duffydack said:**
> My volume control applet keeps disappearing after installing the newer version..  also, any other sounds like my email notify sound and system sounds while i`m playing music with any application, is just a clicking static sort of sound...

If you were using v2.5 of the script, it may have written an invalid configuration file. Newer versions won't create this problem, but if the bad configuration is still present, it will cause problems.

Try:
```
$ rm ~/.pulse/default.pa*; pkill pulseaudio
```

---

### Post by MetalMusicAddict on 2010-02-06
I'm wondering the future of this since pulseaudio git master has an eq?

---

### Post by psyke83 on 2010-02-06
> **MetalMusicAddict said:**
> I'm wondering the future of this since pulseaudio git master has an eq?

It's hard to tell. The built-in EQ still doesn't have a GTK interface, which may preclude it from being used in Ubuntu Lucid by default.

Aside from that, my version can be expanded to use different LADSPA plugins (which, as you know, range beyond simple EQ). The interface is already somewhat capable of using other LADSPA plugins, but needs more work.

The disadvantage of PulseAudio's LADSPA module (used by my interface) is that it's not possible to truly change settings in real-time (which is why you need to click "Apply settings" after each change).

---

### Post by duffydack on 2010-02-07
> **psyke83 said:**
> If you were using v2.5 of the script, it may have written an invalid configuration file. Newer versions won't create this problem, but if the bad configuration is still present, it will cause problems.

Try:
```
$ rm ~/.pulse/default.pa*; pkill pulseaudio
```

there isnt a file called default.pa in my ~ but there is one in /etc/pulse/ 
should I remove it?
For now i`ve just uninstalled the equalizer, removed anything in .pulse called equalizer* and reinstalled it..see what happens

---

### Post by tjk on 2010-02-09
I skimmed through this thread (and the web) but could not find a fix for my problem...

I installed the PA eq today on Kubuntu 9.10 - 64-bit (KDE 4.3.5).  It  appeared that there were no errors and that everything installed  correctly.  However, the main problem that I have is that the eq has no  effect on the tone. 

As well, if I use a preset the eq automatically disables itself.  If I  don't use the presets everything else appears like it should work (but  doesn't).

EDIT: Further to this, when starting the eq in the terminal I'm given the error message: "cannot access /home/tim/.pulse/presets/*.preset: No such file or directory"  When I look in that directory it is empty... no preset file(s).

Any ideas what may be wrong?

---

### Post by brookie on 2010-02-10
Thanks for putting this in your ppa psyke! It's much easier to keep it updated that way. Much appreciated. 
Cheers, 
brook

---

### Post by diddy1234 on 2010-02-10
I had fun and games trying to figure out what PPA was at first then to find psyke83's own PPA.

So for anyone wanting to add psyke83 ppa its here :-

[https://launchpad.net/~psyke83/+archive/ppa](https://launchpad.net/~psyke83/+archive/ppa)

excellent work psyke83

Shame ubuntu doesnt let you post deb files anymore but this way seems to work well, plus everyone gets updates if you update this package.

Just installed it and reading the first post there should be the equalizer available under Applications >- sound and video

However this equalizer does not exist.

This can be ran by -
./pulseaudio-equalizer-gtk

the gui then appears.

It would appear that if the user does not have a .pulse directory the menu option does not exist or it could be that it does not exist until a reboot is performed.

How do i change the default frequency bands ?
is there a way to get this to auto run when logging in (as i have to get this enabled to run).

---

### Post by Adamsmasher23 on 2010-02-10
> **tjk said:**
> EDIT: Further to this, when starting the eq in the terminal I'm given the error message: "cannot access /home/tim/.pulse/presets/*.preset: No such file or directory"  When I look in that directory it is empty... no preset file(s).

Any ideas what may be wrong?


I am having this same problem; I can't start the equalizer at all.  My presets directory is empty.

Any suggestions? Could someone post a .preset file?

---

### Post by psyke83 on 2010-02-11
> **tjk said:**
> I skimmed through this thread (and the web) but could not find a fix for my problem...

I installed the PA eq today on Kubuntu 9.10 - 64-bit (KDE 4.3.5).  It  appeared that there were no errors and that everything installed  correctly.  However, the main problem that I have is that the eq has no  effect on the tone. 

As well, if I use a preset the eq automatically disables itself.  If I  don't use the presets everything else appears like it should work (but  doesn't).

EDIT: Further to this, when starting the eq in the terminal I'm given the error message: "cannot access /home/tim/.pulse/presets/*.preset: No such file or directory"  When I look in that directory it is empty... no preset file(s).

Any ideas what may be wrong?

The "no such file or directory" message is not really an error - it will show for people who have never saved a custom preset, so it's not related to your problem.

Please attach the log generated from this command:
```
$ pulseaudio-equalizer debug
```

---

### Post by necronwarrior on 2010-02-12
Hello,
I am having a problem using the EQ with firefox. Heres what happned:--->
While playing  music from 
[http://www.groveshark.com ]("http://www.groveshark.com/")
The equalizer enables perfectly. But when I try to change the preset firefox stops playing(the song is still playing but no sound). All other applications(eg. vlc ) work fine.
Please help.

---

### Post by psyke83 on 2010-02-22
> **necronwarrior said:**
> Hello,
I am having a problem using the EQ with firefox. Heres what happned:--->
While playing  music from 
[http://www.groveshark.com ]("http://www.groveshark.com/")
The equalizer enables perfectly. But when I try to change the preset firefox stops playing(the song is still playing but no sound). All other applications(eg. vlc ) work fine.
Please help.

Switching presets while playing music on that site doesn't give me any problems...

However, I'm running the Lucid development release, so it may be different for Karmic. Are you using the 32bit or 64bit release?

---

### Post by Nonno Bassotto on 2010-02-28
I tried it and lost my sound. Before enabling it, I had two entries under the tab "output" in the Pulseaudio preferences. One reads

```

RV620 Audio Device [Radeon HD 34xx Series] Digital Stereo HDMI
Stereo

```

and the other one I don't remember, but had "Analog" in it. The one with analog was the one selected.

Now I have the digital one and
```

Lapsda Plugin Multiband EQ on RV620 Audio Device [Radeon HD 34xx Series] Digital Stereo HDMI
Stereo

```
but I lost the analog entry.

Noone of the two available entries allows me to hear any sound whatsoever.

What can I do?

---

### Post by Nonno Bassotto on 2010-02-28
I solved it removing .pulse

---

### Post by psyke83 on 2010-02-28
> **Nonno Bassotto said:**
> I tried it and lost my sound. Before enabling it, I had two entries under the tab "output" in the Pulseaudio preferences. One reads

```

RV620 Audio Device [Radeon HD 34xx Series] Digital Stereo HDMI
Stereo

```

and the other one I don't remember, but had "Analog" in it. The one with analog was the one selected.

Now I have the digital one and
```

Lapsda Plugin Multiband EQ on RV620 Audio Device [Radeon HD 34xx Series] Digital Stereo HDMI
Stereo

```
but I lost the analog entry.

Noone of the two available entries allows me to hear any sound whatsoever.

What can I do?

Run:
```
$ pulseaudio-equalizer debug
```

Attach the log so I can see.

You can then run the equalizer, choose "Reset to defaults" from the Advanced menu to get sound working again.

---

### Post by Adamsmasher23 on 2010-03-01
I attached the log.  When I ran it, a dialog came up, saying:
pa_stream_writable_size() failed: Connection terminated

---

### Post by Ceiber Boy on 2010-03-02
Good job thank you

---

### Post by marinero_arrr on 2010-03-07
Hey, great job.
I'm having some trouble in karmic with 7.1. when I play some mp3 on audacious, totem, any app, the subwoofer channel it's quiet but when I apply some settings on the pulseaudio equalizer the subwoofer starts output the sound of the center channel. I stop & start audacious and the sound works again without the subwoofer. 

I like the subwoofer working with the mp3 but I have to "apply settings" in the equalizer for every app playing sound.

it's a odd behavior of the equalizer,¿sould the subwoofer had worked form the beginning or the subwoofer shouldn't be activated when I apply settings?

---

### Post by psyke83 on 2010-03-10
> **marinero_arrr said:**
> Hey, great job.
I'm having some trouble in karmic with 7.1. when I play some mp3 on audacious, totem, any app, the subwoofer channel it's quiet but when I apply some settings on the pulseaudio equalizer the subwoofer starts output the sound of the center channel. I stop & start audacious and the sound works again without the subwoofer. 

I like the subwoofer working with the mp3 but I have to "apply settings" in the equalizer for every app playing sound.

it's a odd behavior of the equalizer,¿sould the subwoofer had worked form the beginning or the subwoofer shouldn't be activated when I apply settings?

The equalizer employs *software* equalization by filtering audio through a LADSPA plugin. What the implications are for surround sound configurations/subwoofer setups, I don't know (simply as I don't own such hardware, and therefore cannot experiment).

It may be the case that the LADSPA plugin only supports 2-channel stereo output, I've never looked into the issue deeply. You may want to investigate the alternate equalizer (linked in my first post, but remember that this is not a support thread for it).

---

### Post by ThatBum on 2010-03-12
Heya, my audio skips and stutters when the equalizer is active. Pulse takes ~20% CPU when it's active. Is my hardware too old? It's a Pentium D 820 (2.8GHz). Sound card is SB Audigy 4 (not pro). Memory is 2 GB.

Otherwise good work. I have my ghetto 4.1 surround made from two sets of two decade year old computer speakers and the stock HP woofer, but eh. VLC's equalizer works fine by the way, I think equalizing all of Pulse is too much for my rig.

**E:** BOINC is causing a lot of the skipping. Suspending BOINC stops most of it, but it's still there when playing music with VLC or whatever. Setting a lower nice value for pulseaudio removes it completely, but it has to be pretty mean (-10), which I don't like doing, really. I think optimization is in order, or, as I said, my machine is too old. It *is*...uh...5 years old? Yeah, that sounds right.

---

### Post by unratedexter on 2010-03-17
awesome stuff man - works perfectly in Lucid :D

---

### Post by himek on 2010-04-03
The package doesn't pull necessary gnome dependencies on **K**ubuntu.

$ pulseaudio-equalizer-gtk 
Getting settings...
ls: cannot access /home/cician/.pulse/presets/*.preset: No such file or directory
Traceback (most recent call last):
  File "/usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py", line 519, in <module>
    Equalizer()
  File "/usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py", line 362, in __init__
    icon = self.window.set_icon_from_file("/usr/share/icons/hicolor/16x16/apps/gnome-volume-control.svg")
glib.GError: Failed to open file '/usr/share/icons/hicolor/16x16/apps/gnome-volume-control.svg': No such file or directory

---

### Post by tron_5 on 2010-04-12
Great work! Exactly what I was looking for.
Thank you.

---

### Post by ghostcoil on 2010-04-19
Great work - thanks a lot!

---

### Post by BlueSkyNIS on 2010-05-02
Good job, thank you!

---

### Post by thort on 2010-05-02
Thank You! It works very well. :)

---

### Post by Rob3rt0 on 2010-05-07
Hi all, I'm having trouble finding the right 'setup'
for my equalizer when im listening to Hip Hop.
I have 15 GB's of Hip Hop so i need help. :S

Any ideas, downloads or anything?
Or else please link me a tutorial for how to setup your equalizer perfectly.

---

### Post by psyke83 on 2010-05-07
> **Rob3rt0 said:**
> Hi all, I'm having trouble finding the right 'setup'
for my equalizer when im listening to Hip Hop.
I have 15 GB's of Hip Hop so i need help. :S

Any ideas, downloads or anything?
Or else please link me a tutorial for how to setup your equalizer perfectly.

I don't understand... there is no setup required. All you can do is create a new preset... and to do that requires your own ears, not mine.

---

### Post by Rob3rt0 on 2010-05-08
> **psyke83 said:**
> I don't understand... there is no setup required. All you can do is create a new preset... and to do that requires your own ears, not mine.

I need help with that too many controls. : S
I have no idea of audio ...
They should have included the Hip Hop / Rap preset. :S

---

### Post by Frogs Hair on 2010-05-08
Hi,

Bass starts on the left mids are in the middle and highs or treble are one the right . The first 1/3 of the bands being bass and so on. Make very small adjustments until you find a setting you like . It may take some time there is no way around that. Good Luck

---

### Post by n1ght5t4lk3r on 2010-05-08
I thought this was exactly what i was looking for. I added the ppa to my software sources as pointed out at [https://launchpad.net/~psyke83/+archive/ppa]("https://launchpad.net/%7Epsyke83/+archive/ppa") (this machine is running Ubuntu 9.04) and also imported the key successfully

gpg: requesting key 16AE4E77 from hkp server keyserver.ubuntu.com
gpg: key 16AE4E77: public key "Launchpad PPA for Conn" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)

ran the sudo apt-get update but got 404 errors

W: Failed to fetch [http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/jaunty/main/binary-i386/Packages](http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/jaunty/main/binary-i386/Packages)  404 Not Found
W: Failed to fetch [http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/jaunty/main/source/Sources](http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/jaunty/main/source/Sources)  404 Not Found

edit.. I've been trying this since yesterday repeatedly incase server was down or something

---

### Post by n1ght5t4lk3r on 2010-05-08
never mind about the above issue, I clicked on the "View Package Details" link at the top right of the page and found a .deb which i successfully installed

---

### Post by psyke83 on 2010-05-08
> **n1ght5t4lk3r said:**
> never mind about the above issue, I clicked on the "View Package Details" link at the top right of the page and found a .deb which i successfully installed

The equalizer won't work on Jaunty unless you manage to upgrade your version of PulseAudio to 0.9.19 or newer (and no, I'm not aware of anywhere which offers such packages for Jaunty).

---

### Post by n1ght5t4lk3r on 2010-05-08
lol, i was just coming to post about this, after over 24 hours of frustration I find the equalizer isn't working despite being installed correctly, all dependancies satisfied and so on.

So.. basically all of this is useless for 9.04? There is no other equalizer that will work? currently I have to use vlc for my music which is not ideal due to crappy library management since it mainly really a video player but has an awesome equalizer... rythmbox has no useable equalizer and tried Amarok upon suggestion but seems its for KDE which not only did not work for me but totally screwed up my machine's appearance until I had to restart this machine and re-apply my gnome theme.

 I thought this pulse audio equalizer sounded a bit too good to be true...

ah well, nothing wrong with vlc until ubuntu 10.04 is stable and bug free enough to be viable to upgrade to ( i see no reason to upgrade to 9.10 just to upgrade once again to 10.04 after all the bugs i've read about on the forums have been ironed out) then i can use pulse equalizer)

thanks anyway

---

### Post by digitalcircuit36939 on 2010-05-08
The equalizer works very well for me (I'm using it to overcome poor quality speakers), but a warning for 32bit users going to 64bit.

_If you clean install a 64bit version of Ubuntu over a 32bit version (or restore the custom presets from a backup), it **will** make your system unusably slow until you disable the equalizer_ (e.g. remove the .pulse folder).

Took a bit of troubleshooting to find this out, I'll just need to recreate the custom presets from my memory.  It seems the preset files differ between 32bit and 64bit in some crucial way.  Other than that, I've had no problems.  Thanks for this excellent program! :)

---

### Post by squiddy on 2010-05-11
nice one, mate :)

works like a charm on lucid.

---

### Post by bark50 on 2010-05-18
Thanks!  :)

---

### Post by steve_gts on 2010-05-19
my problem was it not changing the audio output, did a google search and ended up half way through this thread with an answer :-)

---

### Post by squiddy on 2010-05-24
if the preset is based on VLC EQ, then why doesn't it produce the same quality?

---

### Post by beke on 2010-05-24
Just wanted to let you know that the gui won't start up using a clean Kubuntu 10.04 install.

The problem seems to be the missing \usr\share\icons\hicolor\16x16\apps\gnome-volume-control.svg . Replacing it manually allows the gui to start.

Works like a charm otherwise. Thanks a lot!

---

### Post by hhh on 2010-05-27
Holy...



wow, running this on sidux, gracias hombre.

---

### Post by junoon53 on 2010-05-30
Awesome! The only issue is that it keeps resetting the master volume to 100% every time I change the equalizer settings. Any idea why? I'm using lucid.

---

### Post by Lancelot59 on 2010-06-15
It's been working great for me so far, but whenever I try to adjust any of the frequency ranges it stops working. I need to restart Firefox for example if I'm watching a video when I adjust it. The audio just dies.

---

### Post by psyke83 on 2010-06-16
[QUOTE=Wipster]Hi,
First let me say great work with the equalisation script, its helped me  almost get the sound response I wanted from my computer.
How tricky would it be to write a script like this (or adapt this) to  work with another LADSPA plugin (fil-plugin's filters) which provides a 4  band parametric equaliser which I think would be highly desired for  sound engineers/enthusiasts. I think this one seems to be pretty good,  if 4 bands where not enough would it be possible to 'chain' single-band  parametric?[/QUOTE]

The interface already has the capability of using other LADSPA plugins  if you feed it a customized preset file, but there are some limitations  due to the way that I designed the GUI, and also due to PulseAudio's  LADSPA support.

Take a look at one of the preset files, perhaps you might understand better.

Here's the "Laptop" preset  (/usr/share/pulseaudio-equalizer/presets/Laptop.preset) with  explanations of each line added:

```
mbeq_1197 -> this is the plugin label + _ + plugin  unique ID  (which is the format that PulseAudio needs when specifying the LADSPA  plugin)
mbeq -> this is the plugin label (also needed by PulseAudio)
Multiband EQ -> this is the "friendly" plugin name to be used by the  interface.
2 -> this is the preamp level (which is currently ignored)
Laptop -> the name of the preset
15 -> the number of bands used by the plugin, which will follow below
-1 -> band 1's value
-1 -> band 2's value
-1  ..
-1 ..
-5 ..
-10 ..
-18 ..
-15 .. 
-10 ..
-5 ..
-5 ..
-5 ..
-5 ..
0 -> band 14's value
0 -> band 15's value
50 -> band 1's frequency (only used to display on the interface)
100 -> band 2's frequency (only used to display on the interface)
156 ..
220 ..
311 ..
440 ..
622 ..
880 ..
1250 ..
1750 ..
2500 ..
3500 ..
5000 .. 
10000 -> band 14's frequency (only used to display on the interface)
20000 -> band 15's frequency (only used to display on the interface)

```I've written the interface to expect a simple layout such as the  above - X amount of bands, X amount of frequencies.

The mbeq_1197 LADSPA plugin is quite simple, conforming to the above,  containing just 15 bands within its parameters:

```
conn@dimension:~$ analyseplugin mbeq_1197

Plugin Name: "Multiband EQ"
Plugin Label: "mbeq"
Plugin Unique ID: 1197
Maker: "Steve Harris <steve@plugin.org.uk>"
Copyright: "GPL"
Must Run Real-Time: No
Has activate() Function: Yes
Has deativate() Function: No
Has run_adding() Function: Yes
Environment: Normal or Hard Real-Time
Ports:    "50Hz gain (low shelving)" input, control, -70 to 30, default 0
    "100Hz gain" input, control, -70 to 30, default 0
    "156Hz gain" input, control, -70 to 30, default 0
    "220Hz gain" input, control, -70 to 30, default 0
    "311Hz gain" input, control, -70 to 30, default 0
    "440Hz gain" input, control, -70 to 30, default 0
    "622Hz gain" input, control, -70 to 30, default 0
    "880Hz gain" input, control, -70 to 30, default 0
    "1250Hz gain" input, control, -70 to 30, default 0
    "1750Hz gain" input, control, -70 to 30, default 0
    "2500Hz gain" input, control, -70 to 30, default 0
    "3500Hz gain" input, control, -70 to 30, default 0
    "5000Hz gain" input, control, -70 to 30, default 0
    "10000Hz gain" input, control, -70 to 30, default 0
    "20000Hz gain" input, control, -70 to 30, default 0
    "Input" input, audio
    "Output" output, audio
    "latency" output, control

```The fil-plugins LADSPA plugin is more complicated:

```
conn@dimension:~$ analyseplugin filters.so

Plugin Name: "4-band parametric filter"
Plugin Label: "Parametric1"
Plugin Unique ID: 1970
Maker: "Fons Adriaensen <fons@kokkinizita.net>"
Copyright: "GPL"
Must Run Real-Time: Yes
Has activate() Function: Yes
Has deativate() Function: Yes
Has run_adding() Function: No
Environment: Normal or Hard Real-Time
Ports:    "Input" input, audio
    "Output" output, audio
    "Filter" input, control, toggled, default 0
    "Gain" input, control, -20 to 20, default 0
    "Section 1" input, control, toggled, default 0
    "Frequency 1" input, control, 20 to 2000, default 200, logarithmic
    "Bandwidth 1" input, control, 0.125 to 8, default 1, logarithmic
    "Gain 1" input, control, -20 to 20, default 0
    "Section 2" input, control, toggled, default 0
    "Frequency 2" input, control, 40 to 4000, default 400, logarithmic
    "Bandwidth 2" input, control, 0.125 to 8, default 1, logarithmic
    "Gain 2" input, control, -20 to 20, default 0
    "Section 3" input, control, toggled, default 0
    "Frequency 3" input, control, 100 to 10000, default 1000,  logarithmic
    "Bandwidth 3" input, control, 0.125 to 8, default 1, logarithmic
    "Gain 3" input, control, -20 to 20, default 0
    "Section 4" input, control, toggled, default 0
    "Frequency 4" input, control, 200 to 20000, default 2000,  logarithmic
    "Bandwidth 4" input, control, 0.125 to 8, default 1, logarithmic
    "Gain 4" input, control, -20 to 20, default 0

```The interface could be modified to support the fil-plugins plugin  properly, but I'm not sure if it's worthwhile (and I don't think that a  regular screen would fit all the details onto the interface without  scrolling).

Finally, I don't think you can chain multiple LADSPA plugins together -   or at least if it were possible, it would greatly increase CPU usage  and  latency to make it impractical. The interface would also become far too complicated.

> Would this be something you would be interested in pursuing for  greater sound customisation or could you offer some tips you might have  on this subject if I where to give it a go.

Thanks and best regards,
WipI'm not sure if it's worthwhile. The next upstream release of  PulseAudio will feature built-in equalization that is not related to my  interface or LADSPA plugins, and will probably offer better  quality/latency etc.

---

### Post by nanoc on 2010-06-16
Is there a way to specify the frequencies which are modified by the equalizer ?

I would really be interested in removing some very specific frequencies at
233, 466, 932 and 1864 hertz. 

Thanks for the script.

---

### Post by Wipster on 2010-06-16
Hi psyke83 thanks for getting back to me so quickly.

> **psyke83 said:**
> I'm not sure if it's worthwhile. The next upstream release of  PulseAudio will feature built-in equalization that is not related to my  interface or LADSPA plugins, and will probably offer better  quality/latency etc.

Ah I didn't realise this was the case, thats good to hear (heh) I shall keep my eyes open for that one.
I think the interface would be big enough to fit the details needed, for instance this is the interface for that plugin for LV2:
[http://nedko.arnaudov.name/soft/lv2fil/trac/attachment/wiki/WikiStart/lv2fil.png](http://nedko.arnaudov.name/soft/lv2fil/trac/attachment/wiki/WikiStart/lv2fil.png)
If the PulseAudio equaliser doesn't do parametric I think I'l have a tinker with that, strip out the dials and replace with text boxes see if I can get something working, be good experience anyway.

Thanks again.

---

### Post by inunu on 2010-06-19
Thanks for this great script, sorted out my audio problems on my Dell Precision M90, Ubuntu Lucid.

---

### Post by CCC999 on 2010-06-19
Thanks for this great script. Compensates for overly bass bias of my otherwise good sound system. Love the way this is out of sight, universal, and easily changed. I just upgraded to Lucid 10.04 on a home built desktop, ran the script with no issues at all. Thanks again!:guitar:

---

### Post by CCC999 on 2010-06-19
> **CCC999 said:**
> Thanks for this great script. Compensates for overly bass bias of my otherwise good sound system. Love the way this is out of sight, universal, and easily changed. I just upgraded to Lucid 10.04 on a home built desktop, ran the script with no issues at all. Thanks again!:guitar:
Note, after using for a few hours I noticed a consistent pause in all applications. Rather than leaving it on, I'll just use it as needed - still just what was needed for Pulse!

---

### Post by adlin5000 on 2010-06-30
I just have a few questions. 

In order to get a decent volume, I have the preamp set to 1.7. Unfortunately this causes distortion whenever it peaks. Listening to Metallica or any other heavy metal is particularly bad. I can drop the volume and its OK, but its very low. Is there a way to just up the base volume level?

Second, I saw this one earlier in the thread but did not see a fix. When I do a full reboot I have no sound whatsoever. When I try and open any of the pulseaudio apps I get a "connection failed" error. I then have to kill anything trying to play audio, open the equalizer, shut it off, open the pulse manager, turn the equalizer back on and re-apply the settings. Not a huge issue as I only do a full reboot about once a month and there are no issues with suspend.

If there has been fixes around, sorry, just call me an idiot and point me in the right direction. Thanks

---

### Post by Absurd on 2010-07-01
> Is there a way to just up the base volume level?
Not without decreasing the midrange and treble a little. That's why it's called an equalizer. If there's distortion, then the sound is not equalized.

---

### Post by retznto on 2010-07-01
I've been having some problems trying to remove the plugin :(

I used apt-get --purge remove to uninstall the software, but it doesn't seem to have removed everything, as I have to manually reselect "Internal Audio Analog Surround 5.1" instead of "LADSPA Plugin Multiband EQ on Internal Audio Analog 5.1". I have tried removing the mbeq_1197.so file, but that broke my sound completely (so I have since restored it).

That was probably completely the wrong way to go about removing it completely, so any help would be gladly accepted :)

Thanks

Edit: Never mind, I found the equaliser stuff at the bottom of the config file in ~/.pulse

---

### Post by psoulocybe on 2010-07-02
You rock!!!! This just made my Sennheisers so happy!

---

### Post by Cason on 2010-07-03
I was thrilled when I found this! I'm a music fanatic, and I've always very carefully tweaked the equalizers in the other OSs I've used. I am, however, having an issue that I can't figure out. But it may very well be a noob-ish thing; I cut teeth on computers, but I'm while learning fast, I'm very new to Ubuntu.

So I followed the instructions in the first post to download and install the most recent version. After installing (and rebooting), when I went to the sound/video folder and opened the PulseAudio Equalizer. It said it was loading, and then nothing happened. After trying repeatedly, I opened the properties and ran the command associated with the GUI button in the terminal, which apparently is "pulseaudio-equalizer-gtk". Doing that gave me the following:

```
Getting settings...
ls: cannot access /home/cason/.pulse/presets/*.preset: No such file or directory
Traceback (most recent call last):
  File "/usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py", line 519, in <module>
    Equalizer()
  File "/usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py", line 362, in __init__
    icon = self.window.set_icon_from_file("/usr/share/icons/hicolor/16x16/apps/gnome-volume-control.svg")
glib.GError: Failed to open file '/usr/share/icons/hicolor/16x16/apps/gnome-volume-control.svg': No such file or directory
```

Being a noob, I didn't really know exactly what that meant (and to be honest I still don't). So I messed around in the terminal a little bit, reading the info on the pulseaudio-equalizer command, tried commands like toggle and reset, but still couldn't seem to get it working. I've looked through this thread but couldn't find anything helpful.

How can I go about fixing this? I'm almost salivating at the thought of having an equalizer for my Ubuntu OS, lol. I've attached my log. And FYI: I'm running Lucid 10.04.

Thanks in advance for any and all help!

---

### Post by psyke83 on 2010-07-03
> **Cason said:**
> I was thrilled when I found this! I'm a music fanatic, and I've always very carefully tweaked the equalizers in the other OSs I've used. I am, however, having an issue that I can't figure out. But it may very well be a noob-ish thing; I cut teeth on computers, but I'm while learning fast, I'm very new to Ubuntu.

So I followed the instructions in the first post to download and install the most recent version. After installing (and rebooting), when I went to the sound/video folder and opened the PulseAudio Equalizer. It said it was loading, and then nothing happened. After trying repeatedly, I opened the properties and ran the command associated with the GUI button in the terminal, which apparently is "pulseaudio-equalizer-gtk". Doing that gave me the following:

```
Getting settings...
ls: cannot access /home/cason/.pulse/presets/*.preset: No such file or directory
Traceback (most recent call last):
  File "/usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py", line 519, in <module>
    Equalizer()
  File "/usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py", line 362, in __init__
    icon = self.window.set_icon_from_file("/usr/share/icons/hicolor/16x16/apps/gnome-volume-control.svg")
glib.GError: Failed to open file '/usr/share/icons/hicolor/16x16/apps/gnome-volume-control.svg': No such file or directory
```Being a noob, I didn't really know exactly what that meant (and to be honest I still don't). So I messed around in the terminal a little bit, reading the info on the pulseaudio-equalizer command, tried commands like toggle and reset, but still couldn't seem to get it working. I've looked through this thread but couldn't find anything helpful.

How can I go about fixing this? I'm almost salivating at the thought of having an equalizer for my Ubuntu OS, lol. I've attached my log. And FYI: I'm running Lucid 10.04.

Thanks in advance for any and all help!

It's a small packaging bug that affects people who don't use GNOME (as the application uses a GNOME icon). You can fix it by doing *one *of the following:

[LIST]
[*] (ideally) install the package "gnome-media-common" (if it doesn't pull loads of unnecessary dependencies for you)
[*] create an empty file for the icon:```
$ sudo touch /usr/share/icons/hicolor/16x16/apps/gnome-volume-control.svg
```
[*]copy any icon you desire to /usr/share/icons/hicolor/16x16/apps/gnome-volume-control.svg
[/LIST]
 
Are you using Kubuntu or another variant? Certain flavours (such as Kubuntu) don't use PulseAudio, so if my equalizer has caused PulseAudio itself to install, your sound may or may not have conflicts.

---

### Post by Cason on 2010-07-03
> **psyke83 said:**
> It's a small packaging bug that affects people who don't use GNOME (as the application uses a GNOME icon). You can fix it by doing *one *of the following:

[LIST]
[*] (ideally) install the package "gnome-media-common" (if it doesn't pull loads of unnecessary dependencies for you)
[*] create an empty file for the icon:```
$ sudo touch /usr/share/icons/hicolor/16x16/apps/gnome-volume-control.svg
```
[*]copy any icon you desire to /usr/share/icons/hicolor/16x16/apps/gnome-volume-control.svg
[/LIST]
 
Are you using Kubuntu or another variant? Certain flavours (such as Kubuntu) don't use PulseAudio, so if my equalizer has caused PulseAudio itself to install, your sound may or may not have conflicts.

Wow, than's for the quick reply! :popcorn:

I'm not using Kubuntu, but Ubuntu Netbook Remix (which apparently is Gnome? I have the option to select Ubuntu or Gnome when I log in...). And I do have pulseaudio installed, as well as the "gnome-media-common", so that wasn't the issue. But when I tried the second fix, it worked just fine. So thanks for that!

Just as an aside, even messing around with trying to adjust the variables through the terminal, I noticed the same thing that CCC999 mentioned a few posts above: while I was listening to music and browsing, there was a slight catch or skip every 30 secs or so. It immediately disappeared when I toggled the EQ off with the terminal command. Any clues as to what causes that, and if so, is there a fix?

If not, I can just do what CCC said and disable it till I need it, which will be much easier now that the GUI is working! :D

---

### Post by hhh on 2010-07-06
> **psyke83 said:**
> It's a small packaging bug that affects people who don't use GNOME (as the application uses a GNOME icon). You can fix it by doing *one *of the following:

[LIST]...
[*] create an empty file for the icon:```
$ sudo touch /usr/share/icons/hicolor/16x16/apps/gnome-volume-control.svg
```
[*]copy any icon you desire to /usr/share/icons/hicolor/16x16/apps/gnome-volume-control.svg
[/LIST]
...
I'm running Xfce4 and was affected by this bug. Just to let you know, creating an empty file does not work as it then reports the error "file contains no data". Copying another image to there works fine.

BTW, and sorry for not reading this entire thread and checking through launchpad, but has anyone reported that enabling the eq or applying an eq setting sets the system volume to 100% every time?

A million thanks for this terrific utility.

---

### Post by psyke83 on 2010-07-07
> **hhh said:**
> I'm running Xfce4 and was affected by this bug. Just to let you know, creating an empty file does not work as it then reports the error "file contains no data". Copying another image to there works fine.

Thanks for the information.

> BTW, and sorry for not reading this entire thread and checking through launchpad, but has anyone reported that enabling the eq or applying an eq setting sets the system volume to 100% every time?

A million thanks for this terrific utility.This is normal and required for the equalizer to work properly. When the equalizer is enabled, a new PulseAudio LADSPA sink (virtual output device) is created, and the hardware sink (the real sound device) is deliberately set proportional to the preamp. The default preamp level 1.0x - equivalent to 100%, as you can see. The LADSPA sink then becomes the default system sink, and this virtual device controls the volume.

When the equalizer is enabled on  GNOME systems, the gnome-volume-control applet switches the PulseAudio LADSPA sink to the default sink (which  takes over control of system volume). Since you're using XFCE, I guess that its volume applet/utility does not recognise when PulseAudio switches to a different sink.

The script is designed to restore the volume level when you enable/disable the equalizer. I'll try to explain, but it's a bit late here, so sorry if it makes no sense ;).

First, some explanation of some of the terms:
sink = PulseAudio output device
hardware sink = your real sound card, as seen by PulseAudio.
LADSPA = the plugin system used to equalize audio; see the first post, it's explained.
LADSPA sink = the virtual, equalized device which plays back equalized  audio. The LADSPA sink relies on the hardware sink to work properly.

So, this is a rough outline of how the EQ works:

1. EQ is not yet enabled -> your hardware sink is set as the default PulseAudio sink, and the hardware sink volume is at 75% (for example).
2. You turn on EQ -> hardware sink volume is set to the preamp level (e.g., 100% for 1.0x, 150% for 1.5x, etc. - volume can be driven over 100%), a LADSPA sink is created with your equalizer settings, this LADSPA sink is made default, and its volume is  set to the previous hardware sink level (75%).
3. While the EQ is active, your default system volume is now the LADSPA sink and not the hardware sink; the hardware sink volume should not be touched. Unfortunately, judging by your reports, XFCE's applet doesn't seem to recognise when PulseAudio changes the default sink.
4. You turn off EQ -> hardware sink is made default, hardware sink volume is set to the previous LADSPA sink level, and the LADSPA sink is removed.

From the user's perspective, there should be no discernible difference between volume levels when enabling/disabling the equalizer, but it relies on a volume applet that can recognise when the default sink changes.

If you're interested in **seeing** how it works rather than **reading** about it, open PulseAudio Volume Control (pavucontrol) on the Output Devices tab, and toggle the EQ on/off. Watch how the sinks change in the applet.

---

### Post by Cason on 2010-07-07
I must preface this with profound thanks: Ubuntu definitely needs a system EQ, and I greatly appreciate the time and effort you've put in to building one and helping the rest of us get it working.

However, ever since I've installed the EQ, my video and audio playback has been rather buggy. It even happens when I disable the EQ now. I haven't made any other changes to my system since, so I'm  assuming that the EQ has something to do with it. Anything that requires audio, be it music, videos, or games, have horrible glitching problems. My particular system hardware has already had significant issues with some programs, so it's not really a surprise that the EQ might cause my system problems. :cry:

That being the case, how can I completely uninstall the EQ? I haven't be able to find instructions in the thread, but maybe I just missed it. I need to see if an uninstall will fix this horribly irritating audio-hiccup I've been having. If that doesn't fix it, then I'll know the problem is elsewhere and, once I have it fixed, I'll reinstall the EQ.

Hopefully the EQ isn't the issue, but I need to be able to find out...

---

### Post by psyke83 on 2010-07-07
> **Cason said:**
> I must preface this with profound thanks: Ubuntu definitely needs a system EQ, and I greatly appreciate the time and effort you've put in to building one and helping the rest of us get it working.

However, ever since I've installed the EQ, my video and audio playback has been rather buggy. It even happens when I disable the EQ now. I haven't made any other changes to my system since, so I'm  assuming that the EQ has something to do with it. Anything that requires audio, be it music, videos, or games, have horrible glitching problems. My particular system hardware has already had significant issues with some programs, so it's not really a surprise that the EQ might cause my system problems. :cry:

That being the case, how can I completely uninstall the EQ? I haven't be able to find instructions in the thread, but maybe I just missed it. I need to see if an uninstall will fix this horribly irritating audio-hiccup I've been having. If that doesn't fix it, then I'll know the problem is elsewhere and, once I have it fixed, I'll reinstall the EQ.

Hopefully the EQ isn't the issue, but I need to be able to find out...
Installing the equalizer will not modify PulseAudio's default configuration files until you click the "Keep Settings" checkmark in the interface. Unchecking that box will restore PulseAudio to its default configuration.

To be completely sure, you can delete the entire ~/.pulse folder and restart PulseAudio, like so: 
```
$ rm ~/.pulse -r; pulseaudio -k
```Be careful of typos, especially when using the "rm" command.

---

### Post by Cason on 2010-07-07
> **psyke83 said:**
> Installing the equalizer will not modify PulseAudio's default configuration files until you click the "Keep Settings" checkmark in the interface. Unchecking that box will restore PulseAudio to its default configuration.

To be completely sure, you can delete the entire ~/.pulse folder and restart PulseAudio, like so: 
```
$ rm ~/.pulse -r; pulseaudio -k
```Be careful of typos, especially when using the "rm" command.
Well, after tinkering for about seven hours, I was able to finally resolve the problem. It was actually an issue with my unit's processor. While the issue was not caused by the EQ, it was exacerbated by the it and made the problem more noticeable. I was able to correct it by adding a command in GRUB on boot-up. After fixing, I reinstalled the EQ and everything's working picture-perfectly.

So now I have another thing to be thankful for in relation to the EQ: it made me aware of a problem I probably wouldn't have really noticed otherwise. Thanks for the help! :D

---

### Post by exponent on 2010-07-14
I saw that someone earlier in the thread also had this problem, but for some reason when creating a blank equalizerrc file, pulseaudio-equalizer was failing to write a valid 'persistence' attribute

```

:~$ pulseaudio-equalizer-gtk
Getting settings...
ls: cannot access /home/paul/.pulse/presets/*.preset: No such file or directory
Traceback (most recent call last):
  File "/usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py", line 519, in <module>
    Equalizer()
  File "/usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py", line 354, in __init__
    GetSettings()
  File "/usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py", line 62, in GetSettings
    persistence = int(rawdata[6])
ValueError: invalid literal for int() with base 10: ''

```

This was easily fixed by changing the 7th line of .pulse/equalizerrc to 0, and everything seems to be working.

---

### Post by mark465 on 2010-07-28
As a person who runs his Ubuntu 9.10 as root I find I get the message "This script must not be run as root!"

Is there a way for a root user to use pulseaudio-equalizer-gtk?  Thank you!

---

### Post by ivanovnegro on 2010-07-28
Thank you psyke83. This is a great program. Something like this I tried to find desperatley.
I found it because I had issues with the equalizer of my favorite music player Guayadeque and now it works so great and the sound is better.
But one thing, when I move the volume controls in the panel the sound scratches a little. Within the player I havent got problems.
Im using Mint 9 main edition on an HP Compaq 6730s.

Thanks very much for this program.

---

### Post by psyke83 on 2010-07-28
> **mark465 said:**
> As a person who runs his Ubuntu 9.10 as root I find I get the message "This script must not be run as root!"

Is there a way for a root user to use pulseaudio-equalizer-gtk?  Thank you!

No offense, but running as root is pure insanity. If you're new to Ubuntu, I recommend you stop using root and do some research into how user permisisons work on Unix-based systems. If you're aware of the risks, etc. and it's a conscious choice, that's fine.

Edit "/usr/bin/pulseaudio-equalizer" and remove the section that does a check for root (searching for the term "root" should do). If you need further assistance as a result of the script not working from root, you'll need to look elsewhere, sorry.

---

### Post by psyke83 on 2010-07-28
> **ivanovnegro said:**
> Thank you psyke83. This is a great program. Something like this I tried to find desperatley.
I found it because I had issues with the equalizer of my favorite music player Guayadeque and now it works so great and the sound is better.
But one thing, when I move the volume controls in the panel the sound scratches a little. Within the player I havent got problems.
Im using Mint 9 main edition on an HP Compaq 6730s.

Thanks very much for this program.

The scratchy sound when changing volume is a byproduct of PulseAudio's LADSPA plugin, and my script can't really fix that, sorry.

---

### Post by ivanovnegro on 2010-07-28
> **psyke83 said:**
> The scratchy sound when changing volume is a byproduct of PulseAudio's LADSPA plugin, and my script can't really fix that, sorry.

Ok, it doesnt matter because it works fine and I needed something like your plugin.

---

### Post by DanielFerreira on 2010-07-28
Thanks a lot!!! ... really! :D

---

### Post by nutellajunkie on 2010-08-13
This is flabtastic!

---

### Post by ubername on 2010-08-16
In Maverick, I had to change line 362 of  /usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py to 

```
	icon = self.window.set_icon_from_file("/usr/share/icons/Humanity/apps/16/gnome-volume-control.svg")
```
(or other icon of your choice, I guess - I don't know where it appears!)
to avoid 

 ```
File "/usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py", line 362, in __init__
    icon = self.window.set_icon_from_file("/usr/share/icons/hicolor/16x16/apps/gnome-volume-control.svg")
glib.GError: Failed to open file '/usr/share/icons/hicolor/16x16/apps/gnome-volume-control.svg': No such file or directory
```

---

### Post by funnylife_ma on 2010-08-23
Well, It crashes here too on Fedora 14, since gnome-volume-control changed to multimedia-volume-control.

I may try to include a temporary fix for that, using a try/catch block, but the problem is in the desktop file which doesn't allow multiple icons.

---

### Post by wd5gnr on 2010-09-01
I've used this before and upgraded to the latest. This is on 64 bit Kubuntu. Had to copy the icon, of course, and populate the presets directory. 

Works fine when you start it up. But if you change and hit apply settings the pulseaudio server dies. Of course, it restarts, too, but with no equalizer. From the output it looks like it is when it is moving the active PA clients to the sink (maybe because they are already there? I dunno).

Anyway, makes it less usable. If there is any data I can collect to help narrow that down, ask.

>>>Update: Ok my fault. I guess reading your guide earlier I had used src-sinc-best-quality for resample. It used to work ok (I have a 4 core machine running just under 4GHz with 8G of RAM). So I don't know if it is a regression or I just had not noticed before but this caused some jitter and the preamp set <1 would go crazy. src-sinc-fastest and speex-float-5 both seem to work fine and clear up problems with Google voice, etc.

Thanks for all the great posts on Pulseaudio!

---

### Post by VastOne on 2010-09-07
For information purposes to help resolve 

I am running 10.10 Beta

I get the following trying to install

```
sudo software-properties-gtk --enable-ppa=psyke83/ppa; sudo apt-get update; sudo apt-get install pulseaudio-equalizer

Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 102, in <module>
    app = SoftwarePropertiesGtk(datadir=data_dir, options=options, file=file)
NameError: name 'data_dir' is not defined

```

Thanks

Edit - FYI, bug report generated to Launchpad  [_[COLOR="Teal"]here[/COLOR]_]("https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/632402")

---

### Post by funnylife_ma on 2010-09-08
I have created a bug report for that :

[https://bugs.launchpad.net/fedora/+source/pulseaudio-equalizer/+bug/632904](https://bugs.launchpad.net/fedora/+source/pulseaudio-equalizer/+bug/632904)

---

### Post by shantiq on 2010-09-10
hi there got it installed and great sound quality but the gui does not show up    could i have anything missing/   using it on maverick

---

### Post by duffydack on 2010-09-10
> **shantiq said:**
> hi there got it installed and great sound quality but the gui does not show up    could i have anything missing/   using it on maverick

[http://ubuntuforums.org/showpost.php?p=9726438&postcount=267](http://ubuntuforums.org/showpost.php?p=9726438&postcount=267)
^there.

---

### Post by shantiq on 2010-09-11
```

```> **duffydack said:**
> [http://ubuntuforums.org/showpost.php?p=9726438&postcount=267](http://ubuntuforums.org/showpost.php?p=9726438&postcount=267)
^there.


thanx for that duffydack but still no gui  this does not appear

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=136843&d=1258652669[/IMG]


i can hear it working it is a nice sound but of course i cannot change the settings i guess it is is on full bass and treble by default

```
Equalizer status: [enabled]
Equalizer configuration status: [enabled]
Equalizer plugin: [mbeq_1197/mbeq]
Equalizer control: [0,0,0,0,0,0,0,0,0,0,0,0,0,0,0]
NOTE: Using user-customized settings from '/home/shantiq/.pulse/equalizerrc'...

```


could the fourth line here show the problem all those 0s

---

### Post by VastOne on 2010-09-11
> **ubername said:**
> In Maverick, I had to change line 362 of  /usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py to 

```
	icon = self.window.set_icon_from_file("/usr/share/icons/Humanity/apps/16/gnome-volume-control.svg")
```
(or other icon of your choice, I guess - I don't know where it appears!)
to avoid 

 ```
File "/usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py", line 362, in __init__
    icon = self.window.set_icon_from_file("/usr/share/icons/hicolor/16x16/apps/gnome-volume-control.svg")
glib.GError: Failed to open file '/usr/share/icons/hicolor/16x16/apps/gnome-volume-control.svg': No such file or directory
```

Thank you so much, this worked beautifully for me.  :KS:KS:KS

---

### Post by UaHummer on 2010-09-12
how install this in ubuntu 10.10 ?

---

### Post by shantiq on 2010-09-12
> **UaHummer said:**
> how install this in ubuntu 10.10 ?


this is the way i did it [http://exploreubuntu.wordpress.com/2010/04/18/equalizer-for-pulse-audio/](http://exploreubuntu.wordpress.com/2010/04/18/equalizer-for-pulse-audio/)

but i have removed it now as the gui would not appear   good luck if you try it


shan

---

### Post by UaHummer on 2010-09-12
> **shantiq said:**
> this is the way i did it [http://exploreubuntu.wordpress.com/2010/04/18/equalizer-for-pulse-audio/](http://exploreubuntu.wordpress.com/2010/04/18/equalizer-for-pulse-audio/)

but i have removed it now as the gui would not appear   good luck if you try it
shan

thanks... how to configure manually

---

### Post by shantiq on 2010-09-12
--

---

### Post by UaHummer on 2010-09-12
> **shantiq said:**
> sorry what do you mean?  the link i gave you is to install it
what do you mean by manually?
all good I understood everything...)))

---

### Post by dangmc on 2010-09-12
> **psyke83 said:**
> No offense, but running as root is pure insanity. If you're new to Ubuntu, I recommend you stop using root and do some research into how user permisisons work on Unix-based systems. If you're aware of the risks, etc. and it's a conscious choice, that's fine.

Edit "/usr/bin/pulseaudio-equalizer" and remove the section that does a check for root (searching for the term "root" should do). If you need further assistance as a result of the script not working from root, you'll need to look elsewhere, sorry.
Just to let you know pulseaudio-eq not found in maverick repos at this time. I installed from lucid repo---no gui. I assume you must be working on this-program works great in lucid.Thank you for your efforts with this.
I triple boot-ubuntu 10.04, 10.10 beta, winxp pro

---

### Post by VastOne on 2010-09-13
> **dangmc said:**
> Just to let you know pulseaudio-eq not found in maverick repos at this time. I installed from lucid repo---no gui. I assume you must be working on this-program works great in lucid.Thank you for your efforts with this.
I triple boot-ubuntu 10.04, 10.10 beta, winxp pro

It is working great for me in Maverick after following the directions from [_[COLOR="RoyalBlue"]this post[/COLOR]_]("http://ubuntuforums.org/showpost.php?p=9726438&postcount=267")

GUI is there and it works just as well as it did  in Lucid

---

### Post by dangmc on 2010-09-13
> **VastOne said:**
> It is working great for me in Maverick after following the directions from [_[COLOR="RoyalBlue"]this post[/COLOR]_]("http://ubuntuforums.org/showpost.php?p=9726438&postcount=267")

GUI is there and it works just as well as it did  in Lucid
VastOne-thank you for your response. I'm afraid the editing you suggested is beyond my level of expertise without more detailed instructions.

---

### Post by VastOne on 2010-09-13
> **dangmc said:**
> VastOne-thank you for your response. I'm afraid the editing you suggested is beyond my level of expertise without more detailed instructions.

Step by Step process to change it

Step One - In terminal enter this in and then enter your password

```
gksudo gedit /usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py 
```

Step 2 

In Gedit in the Menu's Go to Search and from there select Replace

A Replace Dialogue box will come up.  (see attachment)

In the Search For:

```
icon = self.window.set_icon_from_file("/usr/share/icons/hicolor/16x16/apps/gnome-volume-control.svg")
```

In the Replace With:

```
icon = self.window.set_icon_from_file("/usr/share/icons/Humanity/apps/16/gnome-volume-control.svg")
```

Then click replace  and then close

Step 3 

Click Save to save your document

Now you should be able to start the equalizer and have your GUI

---

### Post by dangmc on 2010-09-14
> **VastOne said:**
> Step by Step process to change it

Step One - In terminal enter this in and then enter your password

```
gksudo gedit /usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py 
```

Step 2 

In Gedit in the Menu's Go to Search and from there select Replace

A Replace Dialogue box will come up.  (see attachment)

In the Search For:

```
icon = self.window.set_icon_from_file("/usr/share/icons/hicolor/16x16/apps/gnome-volume-control.svg")
```

In the Replace With:

```
icon = self.window.set_icon_from_file("/usr/share/icons/Humanity/apps/16/gnome-volume-control.svg")
```

Then click replace  and then close

Step 3 

Click Save to save your document

Now you should be able to start the equalizer and have your GUI

VastOne-That did it and Thanks-now to see if it works!

---

### Post by horsemanoffaith on 2010-09-15
Hi, I'm a Linux noob. I'm running 10.04 Lucid. I have sound working just fine... I'm currently listening to Rhythmbox. As soon as I enable the PulseAudio eq, I only get static when there's sound output. What could be causing this? Any solutions?

---

### Post by [STD]Ein on 2010-09-15
This is a bit off topic, and now I'm [cross-posting]("http://ubuntuforums.org/showthread.php?p=9840231") (such a bad boy).

I'm trying to get a different ladspa filter inserted in my audiochain, and was encouraged when I saw how this (awesome) PulseAudio Eq script did it... however..

I'm obviously no linux genius.

trying to mimic this script by appending 

```
### BEGIN: Compressor configuration
load-module module-ladspa-sink sink_name=ladspa_output.dyson_compress_1403.dysonCompress master=alsa_output.default plugin=dyson_compress_1403 label=dysonCompress control=0,1,0.5,0.99
set-default-sink ladspa_output.dyson_compress_1403.dysonCompress
set-sink-volume alsa_output.default 65536
set-sink-mute alsa_output.default 0
### END: Compressor configuration
```

to the end of either /etc/pulse/default.pa or ~/.pulse/default.pa
in sound preferences, I now see a new output (LADSPA Plugin Dyson compressor on Internal Audio) but it doesn't seem to have any effect on the audio.

Any thoughts, is there a better way to accomplish this?  I tried investigating how to make the eq script load this filter, but the script made my head spin (sans the green puke).

Thanks for any, I mean ANY, help.

EDIT: It works.  I'm a dumb ***.  Don't know why, but at some point this began to work correctly.
Now to get a limiter in line, (swh's fast_limiter won't work in pulse, maybe cmt's limit_rms)

---

### Post by tim71 on 2010-09-20
Lucid 64bit - it worked "out of the box", but then came out one very big **BUT**. I mean there was some static and stuff on the background, but then totally unexpected things happened.

I have *resample-method = src-sinc-best-quality* setting in pulseaudio configuration and everything has worked without a glitch this far, but when I enabled the pulseaudio-equalizer and started to watch some more "demanding" video stuff, then in a few minutes my system was grinded to total halt with unstopping harddisk activity. I succeeded to zap my X-session, but still only way out was a reset button.

I tried this again with a little preparation and saw VLC going totally mad and eating up all 12 gigabytes of RAM in an instant - it then occured to me, that this previously observed harddisk activity was VLC eating up all swap space. This time I was able to save the system by zapping (Alt+SysRq+K) just in time.

It is kind of totally reproduceable, but system will be grinded to halt without quick intervention. When pulseaudio equalizer is not enabled, everything works without a problem.

I tried to put VLC to log to syslog, but did not found anything that could help.


I would never thought, that video or audio could eat up all resources on i7 machine like that in seconds...

---

### Post by tgeer43 on 2010-09-28
Running v2.7 under Ubuntu 10.04 64-Bit.

Clicking on the checkbox for "Eq Enabled" and then clicking "Apply" causes the master system volume to be increased to maximum. This happens *every time* on my system.

The first time this happened to me I was playing a bass test mp3 in Audacious and one of my Altec Lansing subwoofers was physically damaged as a result.
I *really* liked that subwoofer. :(

This bug does not occur on a friend's laptop running Ubuntu 10.04 32-Bit.

If this has already been covered please point me to it. I tried reading through this entire thread but gave up far short of the 288th and final post.

tgeer

---

### Post by duffydack on 2010-09-28
I have noticed sound volume max out when changing eq settings and setting them on/off.  Luckily I have a laptop which might not be as powerful as external speakers, but it has a subwoofer and it cost a bit of money :) So I`d hate for it to be blasted to death.. 
I dont change my eq settings much so I`ll live.

---

### Post by Lancelot59 on 2010-09-28
Is there a command that I can have linux run when it boots to that sets the master volume?

---

### Post by bark50 on 2010-09-28
Similar to tgeer and duffydack's problem, I've noticed when the equalizer is enabled and I switch radio stations in Rhythmbox the volume on Rhythmbox will max out with each station change.  This doesn't happen with Guayadeque and doesn't happen when I play something from my library.  I keep my system volume always at 100%, so I don't know if it would max out with enabling the equalizer.

---

### Post by monikgtr on 2010-10-02
You could also install it from the webupd8 ppa, they have a fixed package for maverick

```
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update && sudo apt-get install pulseaudio-equalizer
```



source: [http://www.webupd8.org/2010/09/download-pulseaudio-system-wide.html](http://www.webupd8.org/2010/09/download-pulseaudio-system-wide.html)

---

### Post by tgeer43 on 2010-10-02
Yeah, what I have to do as a precautionary measure is make certain that all currently running apps that emit sound are either turned way down or beter yet, muted. Then I can enable the equalizer and reset my volume levels.

I wouldn't mind it all at but this method doesn't allow you to hear the difference in frequency response back to back in order to make a decent comparison. Since the individual sliders to not respond in real time the problem is even more acute.

Ah well, it'll probably get corrected eventually but in the meantime I'm just glad to have a system wide equalizer/preamp.

Regards,

tgeer

---

### Post by Lancelot59 on 2010-10-11
I just moved over to Maverick, and the equalizer window isn't coming up when I click on the icon in the menu. It just says it's starting it, and then after a bit it dies. The UI is gone apparently. How can I get it back?

---

### Post by VastOne on 2010-10-11
> **monikgtr said:**
> You could also install it from the webupd8 ppa, they have a fixed package for maverick

```
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update && sudo apt-get install pulseaudio-equalizer
```



source: [http://www.webupd8.org/2010/09/download-pulseaudio-system-wide.html](http://www.webupd8.org/2010/09/download-pulseaudio-system-wide.html)

> **Lancelot59 said:**
> I just moved over to Maverick, and the equalizer window isn't coming up when I click on the icon in the menu. It just says it's starting it, and then after a bit it dies. The UI is gone apparently. How can I get it back?

Did you get the updated one from webupd8?

---

### Post by Lancelot59 on 2010-10-11
Sorry, not just that. All my audio is dead now. Thanks for the link though.

---

### Post by VastOne on 2010-10-11
> **Lancelot59 said:**
> Sorry, not just that. All my audio is dead now. Thanks for the link though.

you might want to try to remove ./pulse from your /Home and restart.  When I first started with the initial loads of Maverick Beta I had to remove that and reinstall.  I keep my /Home on a separate partition and that is why it was there.

Just a thought.

---

### Post by Lancelot59 on 2010-10-11
Ah, I can't get to alsaconfig either...something is fishy here. In fact I can't find any entries in the man pages about alsa. However the equalizer is working now. However sound processed by it is somewhat quiet.

EDIT: nevermind. Seems to be working. Just need to turn up the preamp a bit.

---

### Post by Djzn.BR on 2010-10-12
Please psyke83!!!!!!!!!!!! Package this for Maverick Meerkat!!!!! Please !!!!!!!!!!

---

### Post by VastOne on 2010-10-12
> **Djzn.BR said:**
> Please psyke83!!!!!!!!!!!! Package this for Maverick Meerkat!!!!! Please !!!!!!!!!!

It already is 

[http://www.webupd8.org/2010/09/download-pulseaudio-system-wide.html](http://www.webupd8.org/2010/09/download-pulseaudio-system-wide.html)

---

### Post by Lancelot59 on 2010-10-12
Maverick get the thumbs down from me. So many annoyances that compound ruin it for me.

---

### Post by Genesius on 2010-10-13
> **VastOne said:**
> It already is 

[http://www.webupd8.org/2010/09/download-pulseaudio-system-wide.html](http://www.webupd8.org/2010/09/download-pulseaudio-system-wide.html)

Installed it, totally wrecked my sound.

Before, the sound on my laptop was tinny but listenable. Installed the equalizer and sound became so quiet I could barely hear it even with all the settings turned up to full. Completely removed the equalizer, but still can barely hear sound. Any ideas how to fix?

---

### Post by Lancelot59 on 2010-10-13
> **Genesius said:**
> Installed it, totally wrecked my sound.

Before, the sound on my laptop was tinny but listenable. Installed the equalizer and sound became so quiet I could barely hear it even with all the settings turned up to full. Completely removed the equalizer, but still can barely hear sound. Any ideas how to fix?

It's not the EQ. Open Terminal:

```
alsamixer
```

Try adjusting the master and speaker levels there.

Speaking of strange things. I installed
```
linux-backports-modules-alsa-2.6.31-22-generic
```
before installing the equaliser package. Now the volume control for Ubuntu is at 74, while the master in alsamixer is at 84. Adjusting the speaker level in alsamixer causes the difference to increase. This didn't happen before.

The only settings I've modified in alsa-config was adding:
```
options snd_hda_intel model=hp-dv5
```
at the end.

Why are they different values?

---

### Post by Genesius on 2010-10-13
> **Lancelot59 said:**
> It's not the EQ. Open Terminal:

```
alsamixer
```

Try adjusting the master and speaker levels there.



Yep. . . speaker was set to zero.

*sigh* I hate it when it's something simple like that. Been using Ubuntu since Warty, you'd think I'd learn a thing or two. . .

Thanks!

---

### Post by Djzn.BR on 2010-10-14
Thanks VastOne... it worked just fine.

---

### Post by FrancoNero on 2010-10-14
pretty sweet, also found a PPA for maverick.

here are my problems with the equalizer:
- no integration into audio preferences
- no integration into maverick sound applet
- bad audio (noise, etc)
- crackling on changing volume
- select-apply/activate EQ is really loud!
- no integration into rythmbox etc
- not very neat interface

Bottom line: nice start, would be great to see this developed further!

---

### Post by Lancelot59 on 2010-10-15
> **FrancoNero said:**
> pretty sweet, also found a PPA for maverick.

here are my problems with the equalizer:
- no integration into audio preferences
- no integration into maverick sound applet
- bad audio (noise, etc)
- crackling on changing volume
- select-apply/activate EQ is really loud!
- no integration into rythmbox etc
- not very neat interface

Bottom line: nice start, would be great to see this developed further!
1. Please clarify
2. That wouldn't make any sense
3. I agree
4. What do you mean by that?
5. Again that makes no sense.
6. It's an EQ. You don't need anything else.

This EQ is a LADSPA plugin. It gets used by the Linux ALSA. Letting applications control it would be incredibly difficult, mostly because ALSA is slightly silly. This is called a global eq, meaning it affects the sound output directly. Not the sound from various applications going to the output.

---

### Post by nilarimogard on 2010-10-26
> **Genesius said:**
> Installed it, totally wrecked my sound.

Before, the sound on my laptop was tinny but listenable. Installed the equalizer and sound became so quiet I could barely hear it even with all the settings turned up to full. Completely removed the equalizer, but still can barely hear sound. Any ideas how to fix?

That is the original PulseAudio Equalizer in my PPA mentioned above. I've just fixed the icon which caused it not to install on Maverick...

---

### Post by mocha on 2010-11-03
I just wanted to share something that took me a few days to finally figure out after upgrading from 10.04 to 10.10.  Maverick 10.10 users be aware, if you are making recordings from your soundcard's analog line-in or mic inputs and hear intermittent popping, static, or crackling sounds in the recordings the problem is coming from this playback equalizer.

It's not the script creator's fault, it's just that the 10.10 version of pulseaudio with LADSPA have some defect(s) that is the real problem.  Anyway, it was basically the last thing I troubleshot because I didn't think playback effects could affect recordings, but I guess in the world of pulseaudio normal logic doesn't apply.  This was never a problem with prior releases of ubuntu.

---

### Post by FrancoNero on 2010-11-03
banshee already has an equalizer doesn't it

---

### Post by FlameReaper on 2010-11-04
> **FrancoNero said:**
> banshee already has an equalizer doesn't it

So does Amarok, Audacious, Exaile plus some other players I might forget to mention.

However while I use Amarok, I depend on its GStreamer Phonon backend just so that I can see the Moodbar working, which disables the equalizer because it works only with the Xine backend.

So things like these will be a useful thing for me to use :)

To the creator of this equalizer, a lot of thanks from me to you. Now my Windows audio experience is back in Ubuntu, and I can keep forgetting to pick Windows everytime I come to the GRUB screen upon booting up my laptop! :lol:

There were slight quirks (especially a bit of cracking and noise while changing volumes, and it took quite some time for the equalizer to sense changes on the volume control), but otherwise it works without much of a hitch. I believe this is something that'll get improved every release! :D

---

### Post by Valis667 on 2010-11-06
**[SIZE="6"]******WARNING******[/SIZE]**

**[SIZE="4"]Do NOT install this software, it will mess up your system completely![/SIZE]**

---

### Post by VastOne on 2010-11-06
> **Valis667 said:**
> **[SIZE="6"]******WARNING******[/SIZE]**

**[SIZE="4"]Do NOT install this software, it will mess up your system completely![/SIZE]**

Not a fair assessment.  It may have been a problem for you, although I am sure it was probably more than this script, but we may never know if you do not say what went wrong.

I have this running on 5 of my own machines and I know of it installed on at least 20 more, all without incident.

I use it every day and and swear by it. it has always been a great enhancement to my sound system(s)

---

### Post by ivanovnegro on 2010-11-06
> **Valis667 said:**
> **[SIZE=6]******WARNING******[/SIZE]**

**[SIZE=4]Do NOT install this software, it will mess up your system completely![/SIZE]**

It would be better to say what does not work instead to panic.
Im using this script and it works great. The minor issues are known.

---

### Post by Lancelot59 on 2010-11-06
> **ivanovnegro said:**
> It would be better to say what does not work instead to panic.
Im using this script and it works great. The minor issues are known.
Yeah, and I was able to sort out the issues it did cause, namely making a loud buzz when I turn off the computer. You just need to work with it.

---

### Post by duffydack on 2010-11-06
this software worked for me in 9.10, 10.04 and (with different ppa) 10.10.  Thank god for this program.  My audio sounds as hollow as....something very very hollow, otherwise

---

### Post by Lancelot59 on 2010-11-06
> **duffydack said:**
> this software worked for me in 9.10, 10.04 and (with different ppa) 10.10.  Thank god for this program.  My audio sounds as hollow as....something very very hollow, otherwise
A dead tree perhaps?

---

### Post by ivanovnegro on 2010-11-07
> **Lancelot59 said:**
> Yeah, and I was able to sort out the issues it did cause, namely making a loud buzz when I turn off the computer. You just need to work with it.

Yes, that is it and it is the only issue I have.
Its not bothering me as I need this script and Im not tweaking all the days the volume controls within the panel.

---

### Post by marseille on 2010-11-08
I'm trying to figure out why the volume gets jacked up to max output (100) when the EQ is reset. The EQ itself is not changing -- only the volume level that's terrified my neighbors this Vegas morning :P

Someone else noted this issue as well <http://ubuntuforums.org/showpost.php?p=9108426&postcount=8>.

Are my pulseaudio settings off or is it my hardware? What info do I need to give y'all to figure this out? 

Right now I'm running the EQ on UbuntuStudio Lucid (AMD 64-bit).
```
$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe024000 irq 16
 1 [M1x1           ]: USB-Audio - MidiSport 1x1
                      M-Audio MidiSport 1x1 at usb-0000:00:12.0-1, full speed

```

Thank-you, I really want an EQ along these lines.

---

### Post by VastOne on 2010-11-08
> **marseille said:**
> I'm trying to figure out why the volume gets jacked up to max output (100) when the EQ is reset. The EQ itself is not changing -- only the volume level that's terrified my neighbors this Vegas morning :P

Someone else noted this issue as well <http://ubuntuforums.org/showpost.php?p=9108426&postcount=8>.

Are my pulseaudio settings off or is it my hardware? What info do I need to give y'all to figure this out? 

Right now I'm running the EQ on UbuntuStudio Lucid (AMD 64-bit).
```
$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe024000 irq 16
 1 [M1x1           ]: USB-Audio - MidiSport 1x1
                      M-Audio MidiSport 1x1 at usb-0000:00:12.0-1, full speed

```

Thank-you, I really want an EQ along these lines.

I have this same issue every time I reboot. I am going to test something and will let you know the results

Check your preamp settings in EQ.  I had mine at 1.4 and my volume was always at 140% on every restart.  I changed preamp to 1.0 and the problem went away

---

### Post by marseille on 2010-11-08
Excellent! 

I rebooted, turned down amp a couple notches and the differences between the EQ settings can be heard:D w00t w00t!

I will wait on you to elaborate on the rebooting issue but in the meantime... T H A N K - Y O U! :KS

---

### Post by VastOne on 2010-11-08
> **marseille said:**
> Excellent! 

I rebooted, turned down amp a couple notches and the differences between the EQ settings can be heard:D w00t w00t!

I will wait on you to elaborate on the rebooting issue but in the meantime... T H A N K - Y O U! :KS

What I was saying was that I had to adjust my sound on every reboot...

I then adjusted the amp down to 1.0 and rebooted and the issue was corrected.

Glad it worked for you!

---

### Post by duffydack on 2010-11-09
IIRC, the earlier versions used 1.0 amp.  Glad you got it sorted.

---

### Post by ivanovnegro on 2010-11-09
> **VastOne said:**
> What I was saying was that I had to adjust my sound on every reboot...

I then adjusted the amp down to 1.0 and rebooted and the issue was corrected.

Glad it worked for you!

Thats right but when I change the settings in the equalizer, the volume control jumps again to maximum in the panel, everytime by change not the amp but the presets.

---

### Post by toccata015 on 2010-11-10
For those of you running 10.10 (or just have the same weird issue as I did) I noticed that the script was failing to run when opened because it couldn't find the "gnome-volume-control.svg" icon in /usr/share/icons/hicolor/16x16/apps. 

Not sure why it wasn't there, but changing the icon used in the script to something else fixed the problem. I now has EQ :popcorn:

Cheers!

---

### Post by Cadeyrn on 2010-11-13
I've been searching and I can't find my questions, so I'll ask them:

When the EQ is enabled, no matter what it's set to, there's a weird buzz noise on all my sound that gets extremely annoying. How would I fix this?

When I click Apply Settings, my system volume is automatically set to 100%. How do I change that setting?

The EQ runs in the background, but there's no tray icon for easy and quick use. Did somebody make one that I could have a link to?

---

### Post by Cadeyrn on 2010-11-14
Weird. One day later, all those problems are gone. Though I'd still like a tray icon!

---

### Post by ivanovnegro on 2010-11-14
> **Cadeyrn said:**
> Weird. One day later, all those problems are gone. Though I'd still like a tray icon!

It would be cool to have a tray icon, so, what I do is simply put the EQ on the top panel and can access faster to it.

---

### Post by Lancelot59 on 2010-11-14
> **ivanovnegro said:**
> It would be cool to have a tray icon, so, what I do is simply put the EQ on the top panel and can access faster to it.
I just made a launcher for it, and the alsamixer utility. Faster and easier.

---

### Post by ivanovnegro on 2010-11-14
> **Lancelot59 said:**
> I just made a launcher for it, and the alsamixer utility. Faster and easier.

Yes, I meant this, I made a launcher also.

---

### Post by LorDVipeR on 2010-11-19
Hi, don't work for me....



```
sudo software-properties-gtk --enable-ppa=psyke83/ppa; sudo apt-get update; sudo apt-get install pulseaudio-equalizer
```


```
W: Imposible obtener http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Imposible obtener http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

E: Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
E: No se ha podido localizar el paquete pulseaudio-equalizer
lordviper@viper:~$ 

```

any idea...?


Ubuntu 10.10 Maverick 32bit

---

### Post by ivanovnegro on 2010-11-20
> **LorDVipeR said:**
> Hi, don't work for me....



```
sudo software-properties-gtk --enable-ppa=psyke83/ppa; sudo apt-get update; sudo apt-get install pulseaudio-equalizer
``````
W: Imposible obtener http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Imposible obtener http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

E: Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
E: No se ha podido localizar el paquete pulseaudio-equalizer
lordviper@viper:~$ 

```any idea...?


Ubuntu 10.10 Maverick 32bit

Is this the fixed PPA for Maverick? I had a message that the package is no longer active, I installed it via a deb file.
Edit: Yes I have the same message now, but like I said I installed the deb file and the EQ is working. Im not sure if its possible to install at the moment. Seems that this package is outdated. Try it to install from [here]("http://www.webupd8.org/2010/09/download-pulseaudio-system-wide.html").

---

### Post by markoer on 2010-11-22
pulse-eq 15band script is awsome it boost my sound quality to high level

this isn't realy issue with your script i think it has to do something with ladspa, maybe in earler post's someone mentioned this, when scrolling volume up or down, there is crackling sound, which is realy annoying me. Is there any fix related to this issue, or any feedback about this?

Lucid Lynx 10.04 with 
ladspa-sdk1.1-6 
swh-plugins0.4.15+1-4 

keep  up good work..

---

### Post by ivanovnegro on 2010-11-22
> **markoer said:**
> pulse-eq 15band script is awsome it boost my sound quality to high level

this isn't realy issue with your script i think it has to do something with ladspa, maybe in earler post's someone mentioned this, when scrolling volume up or down, there is crackling sound, which is realy annoying me. Is there any fix related to this issue, or any feedback about this?

Lucid Lynx 10.04 with 
ladspa-sdk1.1-6 
swh-plugins0.4.15+1-4 

keep  up good work..

For what I know at the moment there is no fix for the crackling.

---

### Post by unc0nn3ct3d on 2010-12-02
Got the same 404 errors.. glad the .deb is somewhere, thanks for that link, and thanks for developing the equalizer.  

AArgg, after downloading the new version, getting all excited I'm still SOL:


Getting settings...
Traceback (most recent call last):
  File "pulseaudio-equalizer.py", line 519, in <module>
    Equalizer()
  File "pulseaudio-equalizer.py", line 354, in __init__
    GetSettings()
  File "pulseaudio-equalizer.py", line 62, in GetSettings
    persistence = int(rawdata[6])
ValueError: invalid literal for int() with base 10: ''

---

### Post by ivanovnegro on 2010-12-02
For some reason the deb file is no longer working but the PPA from Webupd8 is working.
So you have to add this PPA to install the EQ.

---

### Post by Djzn.BR on 2010-12-09
There seems to be an **issue** with the Pulse Audio Equalizer. When you log within the system with a second user *(like fast user switching)*, and then you come back to your account, the **master volume is dropped very low**, to the point that adjusting the volume slider won't help because it gets stuck under normal volume level.

Anyone using this script can **confirm** this?

---

### Post by jjpcexpert on 2010-12-20
> **evoka0 said:**
> Hi, 

Great work, thank you  very much, you made my music rock again !!. However i have a problem since i use the laptop speakers or a usb headset to listen music, and it only works on the laptop speakers, when i change the sound output to the headset using pulseaudio applet voulume control,  the equalization is gone. Hope there is a workarround to this problem. 

Regards

I think there is a ```
LADSPA-something (usb headset)
``` output option. Tried that yet? Got round to it?

---

### Post by Dempf on 2010-12-25
> **Djzn.BR said:**
> There seems to be an **issue** with the Pulse Audio Equalizer. When you log within the system with a second user *(like fast user switching)*, and then you come back to your account, the **master volume is dropped very low**, to the point that adjusting the volume slider won't help because it gets stuck under normal volume level.

Anyone using this script can **confirm** this?

I have this issue without logging in with a second user. What happens with me is that on first boot the equalizer works perfectly, but, after disabling it and enabling it once, something weird happens:

When the equalizer is **disabled**, sound at half volume sounds normal.

When the 'flat' equalizer is **enabled**, KDE volume jumps to max. However, sound from the speakers is exactly the same as w/ the equalizer disabled.

This means that the equalizer is not functional for my laptop speakers. I wish to reduce the highs and mids; however, this issue causes my custom preset to sound far too quiet on my speakers with no means to increase the volume.

This is a great project, and I hope that issues like this will be fixed so that users like me can enjoy a systemwide equalizer. :D In the future is there a bug tracker or something where I can submit issues?

---

### Post by tzily on 2011-01-29
i was quite exited when someone directed me to this
but to tell you the truth, it stinks
first of all if the eq is enabled and the music plays in audacious, i get some weird popping noise in my headphones while changing the volume
second, the output is not well designed or something. i get bad results for every preset/configuration. the default sounds way better and clear
if anyone ever used dfx for windows winamp knows what i'm talking about. the true powerful bass output and the perfect sound no matter what configuration
i hope you work on this in the future, but thanks... :)

---

### Post by ivanovnegro on 2011-01-29
> **tzily said:**
> i was quite exited when someone directed me to this
but to tell you the truth, it stinks
first of all if the eq is enabled and the music plays in audacious, i get some weird popping noise in my headphones while changing the volume
second, the output is not well designed or something. i get bad results for every preset/configuration. the default sounds way better and clear
if anyone ever used dfx for windows winamp knows what i'm talking about. the true powerful bass output and the perfect sound no matter what configuration
i hope you work on this in the future, but thanks... :)

Its true, this tool is also buggier now as it was on Lucid, it interferes with the volume of the Ubuntu system, also with other applications that use also soundoutput like Skype, there is always a clicking and I noticed that I cannot use crossfading with it enabled because I will have a scratchy sound while the songs are changing.
But I cannot live without it because it makes a good sound on my system, for example when Im listening to streams in the internet or watching Youtube videos, there is no EQ for this.
Im also hoping that this tool could be improved more.

---

### Post by funnylife_ma on 2011-02-21
> **unc0nn3ct3d said:**
> Got the same 404 errors.. glad the .deb is somewhere, thanks for that link, and thanks for developing the equalizer.  

AArgg, after downloading the new version, getting all excited I'm still SOL:


Getting settings...
Traceback (most recent call last):
  File "pulseaudio-equalizer.py", line 519, in <module>
    Equalizer()
  File "pulseaudio-equalizer.py", line 354, in __init__
    GetSettings()
  File "pulseaudio-equalizer.py", line 62, in GetSettings
    persistence = int(rawdata[6])
ValueError: invalid literal for int() with base 10: ''

This is fixed with :

[http://pkgs.fedoraproject.org/gitweb/?p=pulseaudio-equalizer.git;a=blob;f=pulseaudio-equalizer-2.7-force-default-persistence-value.patch;h=7cc2f0c4fad1dedc42dd221ea04497398c148986;hb=HEAD](http://pkgs.fedoraproject.org/gitweb/?p=pulseaudio-equalizer.git;a=blob;f=pulseaudio-equalizer-2.7-force-default-persistence-value.patch;h=7cc2f0c4fad1dedc42dd221ea04497398c148986;hb=HEAD)

The "Max Volume" bug is fixed with :

[http://pkgs.fedoraproject.org/gitweb/?p=pulseaudio-equalizer.git;a=blob;f=pulseaudio-equalizer-2.7-remove-preamp.patch;h=5a1dcc32aedeed8a36a271b1b49bbbc153a3f90e;hb=HEAD](http://pkgs.fedoraproject.org/gitweb/?p=pulseaudio-equalizer.git;a=blob;f=pulseaudio-equalizer-2.7-remove-preamp.patch;h=5a1dcc32aedeed8a36a271b1b49bbbc153a3f90e;hb=HEAD)

---

### Post by Mozenrath on 2011-03-03
Where the heck is the script?:confused:

---

### Post by Lancelot59 on 2011-03-03
> **Mozenrath said:**
> Where the heck is the script?:confused:

It's in the original post:

> **Installation:**
Since v2.6, the pulseaudio-equalizer package is available from[COLOR=Black] [my PPA]("https://launchpad.net/%7Epsyke83/+archive/ppa"),[/COLOR] which you can access like so:
     Code:
     ```
$ sudo software-properties-gtk --enable-ppa=psyke83/ppa; sudo apt-get update; sudo apt-get install pulseaudio-equalizer 
```

---

### Post by Angelontu22 on 2011-03-09
Hello,

I have a Lenovo Ideapad Y560 with Realtek HD audio card and with built-in JBL speakers. I'm having trouble with the EQ crackling on high volume. Some videos work perfectly but there are those were I can barely hear voices and does not sound very clear. I use the "Laptop" preset with the preamp at 1.5x. 


Any tips for at least reducing or completely eliminating the crackling? Thanks in advance.

---

### Post by Nonno Bassotto on 2011-03-15
Hi, I had a look at the source, and i see most of the work is done via a bash script.

I'm trying to do something similar in Python (not a competitor, don't worry :-) ), and it would be useful if you could clarify some points.

1) If I understand correctly there are currently no PulseAudio bindings for Python. But even if there were, they would not be of much use, as there is no equalizer for PulseAudio. Instead, the work is done by an external LAPSDA plugin. Right?
2) What is the relation between LAPSDA and PulseAudio? Does PulseAudio support something like GStreamer pipelines, where you can insert new elements dinamically? Or did you have to hack in some way to make audio pass through a LAPSDA filter?

I realize I can get this information by looking at the source, but I would be glad if you could save me some headache. :-P I think you have some experience with this!

Thank you very much

---

### Post by VastOne on 2011-03-15
> **Nonno Bassotto said:**
> Hi, I had a look at the source, and i see most of the work is done via a bash script.

I'm trying to do something similar in Python (not a competitor, don't worry :-) ), and it would be useful if you could clarify some points.

1) If I understand correctly there are currently no PulseAudio bindings for Python. But even if there were, they would not be of much use, as there is no equalizer for PulseAudio. Instead, the work is done by an external LAPSDA plugin. Right?
2) What is the relation between LAPSDA and PulseAudio? Does PulseAudio support something like GStreamer pipelines, where you can insert new elements dinamically? Or did you have to hack in some way to make audio pass through a LAPSDA filter?

I realize I can get this information by looking at the source, but I would be glad if you could save me some headache. :-P I think you have some experience with this!

Thank you very much

I am not sure exactly what you are looking at but pulseaudio-equalizer.py is a pure python script.

[_[COLOR="RoyalBlue"]Look here for more information on PulseAudio[/COLOR]_]("https://help.ubuntu.com/community/PulseAudio")

---

### Post by Nonno Bassotto on 2011-03-16
Actually pulseaudio-equalizer.py is just a graphical frontend for a [bash script]("http://bazaar.launchpad.net/~psyke83/+junk/pulseaudio-equalizer/view/head:/usr/bin/pulseaudio-equalizer"). Indeed inside the [python source]("http://bazaar.launchpad.net/~psyke83/+junk/pulseaudio-equalizer/view/head:/usr/share/pulseaudio-equalizer/pulseaudio-equalizer.py") there is the function

```

def ApplySettings():
    print "Applying settings..."
    f = open(eqconfig, "w")
    del rawdata[:]
    rawdata.append(str(ladspa_filename))
    rawdata.append(str(ladspa_name))
    ...
    for i in rawdata:
        f.write(str(i)+'\n')
    f.close()
    os.system('pulseaudio-equalizer interface.applysettings')

```

which basically writes the desired settings into a file, so that it can be read by the bash script, and finally uses a system call to invoke the script.

---

### Post by derEremit on 2011-03-26
Could you provide instructions on how to configure this for running on a headless server.
I'm running mpd which already uses pulseaudio as output.

---

### Post by Jayme Harris2007 on 2011-03-29
I'm a newbie, so I hope I'm posting this in the right place. I've had my ubuntu desktop up and running for less than a week and I braved using the terminal to install the PulseAudio Equalizer. I used the scripts from this web site: [http://www.webupd8.org/2010/02/pulseaudio-system-wide-equalizer-now.html](http://www.webupd8.org/2010/02/pulseaudio-system-wide-equalizer-now.html). The Equalizer installed without a flaw, but when I click on EQ enable I can no longer hear audio, even with everything turned all the way up, including the preamp. I assume that my audio is working since I'm listening to Pandora while I'm typing this.  I would appreciate any help I can get.

Thanks Jayme

---

### Post by nilarimogard on 2011-04-25
> **funnylife_ma said:**
> This is fixed with :

[http://pkgs.fedoraproject.org/gitweb/?p=pulseaudio-equalizer.git;a=blob;f=pulseaudio-equalizer-2.7-force-default-persistence-value.patch;h=7cc2f0c4fad1dedc42dd221ea04497398c148986;hb=HEAD](http://pkgs.fedoraproject.org/gitweb/?p=pulseaudio-equalizer.git;a=blob;f=pulseaudio-equalizer-2.7-force-default-persistence-value.patch;h=7cc2f0c4fad1dedc42dd221ea04497398c148986;hb=HEAD)

The "Max Volume" bug is fixed with :

[http://pkgs.fedoraproject.org/gitweb/?p=pulseaudio-equalizer.git;a=blob;f=pulseaudio-equalizer-2.7-remove-preamp.patch;h=5a1dcc32aedeed8a36a271b1b49bbbc153a3f90e;hb=HEAD](http://pkgs.fedoraproject.org/gitweb/?p=pulseaudio-equalizer.git;a=blob;f=pulseaudio-equalizer-2.7-remove-preamp.patch;h=5a1dcc32aedeed8a36a271b1b49bbbc153a3f90e;hb=HEAD)

Thanks for the patches. I've updated PulseAudio Equalizer in the WebUpd8 PPA with both of these patches (now also available for Ubuntu 11.04): [http://www.webupd8.org/2011/04/system-wide-pulseaudio-equalizer.html](http://www.webupd8.org/2011/04/system-wide-pulseaudio-equalizer.html)

---

### Post by ivanovnegro on 2011-04-25
> **nilarimogard said:**
> Thanks for the patches. I've updated PulseAudio Equalizer in the WebUpd8 PPA with both of these patches (now also available for Ubuntu 11.04): [http://www.webupd8.org/2011/04/system-wide-pulseaudio-equalizer.html](http://www.webupd8.org/2011/04/system-wide-pulseaudio-equalizer.html)

I was on your page and you said its no longer maintained, a pity.
I suspected it yet that it wasnt anymore active this project, so I wont install it this time on Natty and now almost all media players have an EQ.

---

### Post by JBauerIV on 2011-04-25
The equalizer is awesome, but I do have one annoying issue. Every time I want to play audio in Chrome I have to open up PulseAudio Volume Control and tell ALSA plug-in [chrome] to use the equalizer for output. Is there some way to set the equalizer to default or something? 

I suppose this isn't really an issue with the eq, but I'm guessing one of you guys will be able to help me out.

---

### Post by ivanovnegro on 2011-04-25
> **JBauerIV said:**
> The equalizer is awesome, but I do have one annoying issue. Every time I want to play audio in Chrome I have to open up PulseAudio Volume Control and tell ALSA plug-in [chrome] to use the equalizer for output. Is there some way to set the equalizer to default or something? 

I suppose this isn't really an issue with the eq, but I'm guessing one of you guys will be able to help me out.

Did you applied the changes? I cannot remember of such a behavior you are describing.

---

### Post by Lancelot59 on 2011-04-26
> **nilarimogard said:**
> Thanks for the patches. I've updated PulseAudio Equalizer in the WebUpd8 PPA with both of these patches (now also available for Ubuntu 11.04): [http://www.webupd8.org/2011/04/system-wide-pulseaudio-equalizer.html](http://www.webupd8.org/2011/04/system-wide-pulseaudio-equalizer.html)
I think I missed something, did the OP drop this project?

---

### Post by ivanovnegro on 2011-04-26
> **Lancelot59 said:**
> I think I missed something, did the OP drop this project?

Yes, I would like to know it also from first hand?

---

### Post by jsevi83 on 2011-04-27
Does anyone know how to integrate pulseaudio equalizer with the sound menu? I think that would be the right place to have it.

---

### Post by Lancelot59 on 2011-04-27
> **jsevi83 said:**
> Does anyone know how to integrate pulseaudio equalizer with the sound menu? I think that would be the right place to have it.
I don't think you can. The sound menu is part of Gnome, and the eq is just a LASPDA plugin. It would be nice to have a system wide eq, but for some reason people have been against it.

---

### Post by jsevi83 on 2011-04-29
Well, with integration I meant to have a launcher to start the equalizer. The same way there is a Banshee shortcut (or any other music player) when you click on the volume icon.

---

### Post by Lancelot59 on 2011-04-29
> **jsevi83 said:**
> Well, with integration I meant to have a launcher to start the equalizer. The same way there is a Banshee shortcut (or any other music player) when you click on the volume icon.

Oh, that's easy.

You create a launcher, then select application for the type. In the command box put this:
```
pulseaudio-equalizer-gtk
```Here's something to stick in the comment field if you want:
```
PulseAudio LADSPA Interface Using MBEQ Multiband EQ Plugin
```

---

### Post by Lancelot59 on 2011-05-06
I haven't had a chance to try the new script yet. How is it with static noise? The version I'm running gets noisy when you adjust any settings, or the volume.

---

### Post by ivanovnegro on 2011-05-06
> **Lancelot59 said:**
> I haven't had a chance to try the new script yet. How is it with static noise? The version I'm running gets noisy when you adjust any settings, or the volume.

Thats normal, its a known issue that cannot be changed. Be aware also you are using something that has no more maintainance, at least not really from the author of the script.

---

### Post by Lancelot59 on 2011-05-06
> **ivanovnegro said:**
> Thats normal, its a known issue that cannot be changed. Be aware also you are using something that has no more maintainance, at least not really from the author of the script.
I thought someone else had taken it over. I know it was a known issue, but I wanted to know if the newer version addressed the problem. Do you know what the cause of it is?

---

### Post by ivanovnegro on 2011-05-06
> **Lancelot59 said:**
> I thought someone else had taken it over. I know it was a known issue, but I wanted to know if the newer version addressed the problem. Do you know what the cause of it is?

Sorry, I did not try the newer patched version, the problem is that I dont understand who made new patches for it and if it was because of this issue or something else. If you use the newer patched version from WebUpd8 and you still suffer from the same bug then it is obviously at the same stage.
Its a pity, but I dont see anymore advantages to use a left project.

---

### Post by Lancelot59 on 2011-05-06
> **ivanovnegro said:**
> Sorry, I did not try the newer patched version, the problem is that I dont understand who made new patches for it and if it was because of this issue or something else. If you use the newer patched version from WebUpd8 and you still suffer from the same bug then it is obviously at the same stage.
Its a pity, but I dont see anymore advantages to use a left project.
I'm curious as to why this feature isn't implemented into ALSA or Pulseaudio by default. Also, I noticed that the eq breaks sound coming from firefox.

---

### Post by ivanovnegro on 2011-05-06
> **Lancelot59 said:**
> I'm curious as to why this feature isn't implemented into ALSA or Pulseaudio by default. Also, I noticed that the eq breaks sound coming from firefox.

And it breaks also the sound from Skype. Dont understand me wrong, its usable, for me has a great sound, I used it one year but its buggy.

---

### Post by Lancelot59 on 2011-05-06
> **ivanovnegro said:**
> And it breaks also the sound from Skype. Dont understand me wrong, its usable, for me has a great sound, I used it one year but its buggy.
Equalization is actually needed for my speakers to function properly. Otherwise the metal grille above the speakers on my laptop resonate horribly. It just sucks that it breaks so many other things.

---

### Post by jsevi83 on 2011-05-12
It would be nice to have this equalizer in the sound indicator. I mean when you click on the volume icon, having a launcher there like there is a banshee launcher.

---

### Post by nightfever on 2011-06-13
I get an error when installing

```
Fetched 4,767 B in 3s (1,222 B/s)
W: Failed to fetch http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package pulseaudio-equalizer

```

---

### Post by Lancelot59 on 2011-06-13
> **nightfever said:**
> I get an error when installing

```
Fetched 4,767 B in 3s (1,222 B/s)
W: Failed to fetch http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package pulseaudio-equalizer

```
I think that's the old PPA.

---

### Post by ivanovnegro on 2011-06-13
> **Lancelot59 said:**
> I think that's the old PPA.

Right. Webupd8 is the way to go, it was mentioned some posts before.

---

### Post by nightfever on 2011-06-13
> **ivanovnegro said:**
> Right. Webupd8 is the way to go, it was mentioned some posts before.
Another thing: can you edit the frequencies or add a custom frequency by editing the configuration file?

---

### Post by ivanovnegro on 2011-06-13
> **nightfever said:**
> Another thing: can you edit the frequencies or add a custom frequency by editing the configuration file?

Eh, not sure, also I dont use the script anymore.

---

### Post by Lancelot59 on 2011-06-13
> **ivanovnegro said:**
> Eh, not sure, also I dont use the script anymore.
Have you found a better substitute? I think you should be able to, but I think you'd have to modify the script directly.

---

### Post by ivanovnegro on 2011-06-13
> **Lancelot59 said:**
> Have you found a better substitute? I think you should be able to, but I think you'd have to modify the script directly.

No, did not find any substitute but the players I use now have a decent equalizer.

---

### Post by Lancelot59 on 2011-06-13
> **ivanovnegro said:**
> No, did not find any substitute but the players I use now have a decent equalizer.
Bummer. I was hoping this would've been implemented.

---

### Post by nightfever on 2011-06-14
Ok I got it.
All you have to do is edit a preset file and add custom frequencies.
Just search for a folder called "presets" and you'll have all the .preset files there.

---

### Post by alexei.colin on 2011-08-13
Thank you for the script! Works nicely.

I'm experiencing the following issue: upon enabling the equalizer the system volume goes to maximum value regardless of what it was before (incl. even muted). The volume value is not affected upon disabling the equalizer. Is this a known issue? (sorry if this was mentioned here -- I couldn't quickly figure out how to search through one thread on Ubuntu Forms). EDIT: Yes, search is right there, sorry. So, I found references to this, but no conclusive resolution (problem just "went away" in one case). It's happening in Natty for me. What's the verdict on this volume-to-maximum-on-eq-enable issue? Thanks.

---

### Post by jaybeecz on 2012-02-29
> **psyke83 said:**
> 
......
The fil-plugins LADSPA plugin is more complicated:

```
conn@dimension:~$ analyseplugin filters.so

Plugin Name: "4-band parametric filter"
Plugin Label: "Parametric1"
Plugin Unique ID: 1970
Maker: "Fons Adriaensen <fons@kokkinizita.net>"
Copyright: "GPL"
Must Run Real-Time: Yes
Has activate() Function: Yes
Has deativate() Function: Yes
Has run_adding() Function: No
Environment: Normal or Hard Real-Time
Ports:    "Input" input, audio
    "Output" output, audio
    "Filter" input, control, toggled, default 0
    "Gain" input, control, -20 to 20, default 0
    "Section 1" input, control, toggled, default 0
    "Frequency 1" input, control, 20 to 2000, default 200, logarithmic
    "Bandwidth 1" input, control, 0.125 to 8, default 1, logarithmic
    "Gain 1" input, control, -20 to 20, default 0
    "Section 2" input, control, toggled, default 0
    "Frequency 2" input, control, 40 to 4000, default 400, logarithmic
    "Bandwidth 2" input, control, 0.125 to 8, default 1, logarithmic
    "Gain 2" input, control, -20 to 20, default 0
    "Section 3" input, control, toggled, default 0
    "Frequency 3" input, control, 100 to 10000, default 1000,  logarithmic
    "Bandwidth 3" input, control, 0.125 to 8, default 1, logarithmic
    "Gain 3" input, control, -20 to 20, default 0
    "Section 4" input, control, toggled, default 0
    "Frequency 4" input, control, 200 to 20000, default 2000,  logarithmic
    "Bandwidth 4" input, control, 0.125 to 8, default 1, logarithmic
    "Gain 4" input, control, -20 to 20, default 0

```The interface could be modified to support the fil-plugins plugin  properly, but I'm not sure if it's worthwhile (and I don't think that a  regular screen would fit all the details onto the interface without  scrolling).
.....


For those who are not awared from command line and find that 4-band parametric filter (LADSPA plugin filters.so -package fil-plugins) can do better job for them as classical 15-band mbeq (e.g. do not have ideal acoustic room treatment and exactly know what frequencies by which amount to equalize) here is simple command using pulseaudio module-ladspa-sink module:

```

pacmd load-module module-ladspa-sink sink_name=ladspa_out master=alsa_output.pci-0000_00_1b.0.analog-stereo plugin=filters label=Parametric1 control=1,0,1,98,0.125,8,1,113,0.125,-13,0,600,0.125,-20,0,3300,0.125,0

```

You can read more about the loading the module here:
[http://www.pulseaudio.org/wiki/Modules#module-ladspa-sink]("http://www.pulseaudio.org/wiki/Modules#module-ladspa-sink")
The master name you can find by running the command :
```
pacmd list-sinks|grep 'name:'
```

The control section takes 18 parameters for the filters plugin (because the first two listed in plugin overview are not of type "input control" and are not involved in the control section), so we start from filter parameter which enables the plugin (IMHO), than we have gain set to zero.  Then follow 4 sections of four numbers - on/off toggle for the section, frequency, bandwidth and wanted gain for the section. 

What I wanted to do was make very narrow 8dB bump on 98Hz (bandwidth 0.125), than really supress (again very narrowly - bandwidth 0.125) frequencies around 113Hz by -13dB (here my room resonates). I am not using the last two sections (leading zeros in their toggle control) at the moment. Just to notice - bandwith control is not in "Q units" (the higher the Q the narrower the band) but the highest value 8 means the widest frequency band affected and vice versa.

So we have crated a pulseaudio sink called ladspa_out (you can check it in the Manager Devices tab) but now we want to play through it. It seems to me there is not optimal synchronization between the  set-default-sink command and GUI tool "padevchooser". I advise you to use the padevchooser and set there default sink to "Other.." and write "ladspa_out" string. Although the pulseaudio manager still shows the old default sink in the "server information tab" you can try to start any new stream and in the "Devices" tab of the Manager you should see that new stream is played through our created LADSPA sink. 

For experimenting you can create another instance of the equalizer with different controls - it only gets different ID and you route streams between the sinks without stopping them with the command 
```
pacmd move-sink-input streamIndex wantedSinkIndex
```
You can obtain all the IDs from the devices tab of the manager.

Unwanted sink can be deleted by the commmand:
```
pacmd unload-module moduleID
```
The moduleID is different to wantedSinkIndex from previous command and can be found in "Owner Module" line in the properties of the sink. 

Hope I helped some of you and you can now enjoy your music better with Pulseaudio!

---

### Post by jimstar79 on 2012-04-07
Originally Posted by **ivanovnegro** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=10115320#post10115320") 				
 				*It would be cool to have a tray icon, so, what I do is simply put the EQ on the top panel and can access faster to it.*


> **Lancelot59 said:**
> I just made a launcher for it, and the alsamixer utility. Faster and easier.

Be great if you guys could explain this; I think it might be exactly what I am looking for to complete my set up! Really hope you come back and help out on this one :)

I wish I could explain what it was I did to finally get my sound working perfectly on my system so that I might be able to help others out!

Ubuntu community is awesome!!

---

### Post by mlaughlin on 2012-09-29
the preamp is missing in my eq... does anyone know why this would occur I am running 11.10

---

### Post by blankopus on 2012-11-08
Thank you for the pulseaudio script!!

-one love

---

### Post by Xplorer4x4 on 2013-01-25
Is there any where to get presets for the eq?

---

### Post by LGA45 on 2013-03-05
Can someone give me the package download link? for some reason when I try using the code provided, it says not found.

---

