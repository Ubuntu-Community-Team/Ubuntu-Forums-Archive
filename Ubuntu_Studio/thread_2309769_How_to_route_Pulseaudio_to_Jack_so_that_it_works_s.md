---
title: "How to route Pulseaudio to Jack so that it works stable?"
date: 2016-01-13
forum: Ubuntu Studio
---

### Post by gertim-alberda on 2016-01-13
Hello,

I use a Firewire Express card (a Startech IEEE1394A FireWire) in my laptop, which is a Thinkpad X220 and is running on Ubuntu Studio (14.04). My external soundcard is a M-audio firewire 610 (this setup only works if the the soundcard gets powered by the adapter!). To get it work with Ubuntu Studio, I first started FFADOO (you seem to have to do that just once, so that the soundcard is recognized) and then QjackCtl, the Jack Audio Connection Kit. I chose 'firewire' and 'hw:0' ('default' will work too). This is the only way to make Firewire work, through Jack on top of FFadoo That was not enough however, I believe I also had to install some extra jack related mixer stuff or extras from the Ubuntu repository and also had to active ACPI.. I don't exactly know anymore what I did, but I got it running in the end. However, there still remained a problem, that I also encountered in Tango Studio, but then for other reasons, because their they don't have Pulseaudio installed at all (and I can understand why, because it gives a lot of issues and seems to make the system unstable). I figured out the easiest way to make it work in Ubuntu Studio was to route Pulseaudio to Jack and that's why I put some after startup scripts in Qjackctl. At first, this is what I entered in the after startup script:

pactl load-module module-jack-sink channels=2; pactl load-module module-jack-source channels=2; pacmd set-default-sink jack_out

After stopping and restarting Jack, it worked right away. When I opened Youtube and played a movie I had great sound through my external soundcard, connected to my firewire express card. So, I was happy with that.

But not for long, because then it got unstable.. sometimes it worked and sometimes it didn't. After rebooting it did not work and sometimes in Youtube it did not work (always whit Jack running of course). So it seemed that the scripts were not sufficient.

So, I changed the scripts in QjackCtl to this, based on [this website]("http://www.rncbc.org/drupal/node/348"). (I don't want permanent links, because when I undock the laptop everything should run through the internal speakers with Alsa; standard setup. I only run QjackCtl and use firewire when docked)
[B]
on startup script:[/B]
pacmd suspend true

**after startup script**
port pulseaudio to jack:
pactl load-module module-jack-sink channels=2; pactl load-module module-jack-source channels=2; pacmd set-default-sink jack_out

**on shut down script:**
module-jack-sourcepactl unload-module module-jack-sink channels=2; pactl unload-module module-jack-source channels=2 
[B]
I first used this and after that I encountered the problem, described below: [/B]
 SINKID=$(pactl list | grep -B 1 "Name: module-jack-sink" | grep Module | sed 's/[^0-9]//g')
SOURCEID=$(pactl list | grep -B 1 "Name: module-jack-source" | grep Module | sed 's/[^0-9]//g')
pactl unload-module $SINKID
pactl unload-module $SOURCEID
sleep 5

**after shut down script: **
pacmd suspend false; killall -9 jackdbus

That worked at first, but after closing QjackCtl, with automatically closing the Jackserver, and starting it up again, there was a problem. Whatever I tried and changed, there was no way to get Pulseaudio connections with Jack. The connection screen only shows the firewire_pcm connections. Nothing else. Rebooting does not help, nothing seems to help anymore. So I am having problems getting the right scripts to work and Pulseaudio to Jack seems to be blocked right now. What to do? Any suggestions?

---

### Post by gertim-alberda on 2016-01-13
probably pulseaudio was hanging (which is not solved bij rebooting, which I thought). After I did "killall pulseaudio" it suddenly worked.

---

### Post by gertim-alberda on 2016-01-13
these are the right settings that work well, also for Ubuntu 14.04 [http://rivendell.tryphon.org/wiki/Debian_6_Setup_JACK2_with_Pulse_Audio](http://rivendell.tryphon.org/wiki/Debian_6_Setup_JACK2_with_Pulse_Audio)
I placed the scripts in /usr/local/bin
then I did: 
chown root:adm /usr/local/bin # to make sure the admin user can execute those scripts. 
chmod -R 755 /usr/local/bin

---

### Post by gertim-alberda on 2016-01-13
Playing videos from Youtube just isn't stable this way...  a lot of xruns.. 

Wed Jan 13 20:45:18 2016: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Triggered
[I]
 Wed Jan 13 20:45:18 2016: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error

 [COLOR=#cc66cc](qjackctl:8668): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed[/COLOR]
 [COLOR=#cc66cc](qjackctl:8668): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed[/COLOR]
 [COLOR=#cc66cc]20:47:12.353 XRUN callback (2).[/COLOR]
 [COLOR=#cc66cc]20:47:23.420 XRUN callback (4).[/COLOR]
 [COLOR=#cc99cc]20:47:24.702 XRUN callback (1 overgeslagen).[/COLOR]
 [COLOR=#cc66cc]20:47:33.426 XRUN callback (6).[/COLOR]
 [COLOR=#cc66cc]20:47:59.349 XRUN callback (7).[/COLOR]
 [COLOR=#cc66cc](qjackctl:8668): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed[/COLOR]
 [COLOR=#cc66cc](qjackctl:8668): Gtk-CRITICAL **: IA__gtk_widget_get_direc[/COLOR][/I]

Pulseaudio to Jack with Ubuntu Studio seems very unstable, certainly if playing videos from Youtube. Keeps giving Xruns and you hear them as little interruptions. I had this problem before with Ubuntu Studio. That's why I tried Tango Studio and that worked out of the box just fine, with low latency and no errors or Xruns (so it is not a hardware thing). However it is not supported anymore. So I thought lets go back to Ubuntu Studio, which has a greater community and maybe more support. So anyone? Who knows how to tackle this? I think it has to do with the Pulseaudio te Jack routing and not with CPU scaling, because when I don't play a Youtube video (that is when the routing from Pulseaudio to Jack kicks in) then I have the x-runs. When playing a music file from Audition, then there are no Xruns. The CPU frequency scaling is on power-save, but I need that, becaus I am also running a webserver from my laptop and I don't want the power consumption and the heat to go up. Maybe that is an impossible combination?

---

