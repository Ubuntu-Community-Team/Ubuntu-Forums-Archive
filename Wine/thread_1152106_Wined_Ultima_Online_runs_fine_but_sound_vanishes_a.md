---
title: "Wined Ultima Online runs fine but sound vanishes after a bit"
date: 2009-05-07
forum: Wine
---

### Post by Burneddi on 2009-05-07
Yeah well. I've been wanting to play this classy game for some time on my linux box, got it running "fine" (Hella choppy, sound lagged, mouse 'blinked' weirdly) and after trying some settings in UO settings and Wine I got it running mostly perfect.


So, my problem is that, although the sound runs 100% perfect, isn't choppy at all, music plays etc. it just vanishes after I play a bit. Just goes away with no warning. After that the game still runs 100% perfect, except there's no sound. It's not a real problem and I can deal with it but still it'd be nice to fix it.

In the Wine DirectSound thing I've tried every possible setting (Full, standard, basic, emulation), none of which solved it. Also tried ticking the "Emulate sound" (or something like that, my menu is in Finnish) box, which completely put away the sound. Mixer is set to ALSA mixer, if it matters. Tried OSS mixer too, which didn't work at all.


Ok, that's my current problem. If someone else is stumping with the problems I used to have, here's how I solved them:

1) (Sound) Lag: Turn off your desktop effects (Basically turn off Compiz as it was causing this) in System > Settings > Appearance

2) Mouse blinking: In Ultima Online, in your paperdoll, click Options -> In the upper right corner of the screen there's a picture of a mouse, change to that tab -> Uncheck "Run mouse in a separate thread"

E: Oho, seems like I posted this to a wrong forum. Pardon me, I'm quite new with this :P.. Can't move it anymore so there's nothing I could do with it anymore. Apparently it should be in the Wine forum, instead of deletan or something this could the moderator move this there?

---

### Post by ifyc576 on 2009-05-07
I just wanted to let you know that I have the same problem as you do with UO.  I never did find a solution.  Logging out and logging back into the shard would restore the sound until of course it would go out again.

Sorry I cannot offer a solution, but I thought you would like to know "you're not the only one".:)

---

### Post by Hans Olo on 2009-11-02
I have the same problem on my desktop PC, after upgrading from 9.04 to 9.10 -- Hopefully someone will help us out, as I've tried everything I can think of...

Interestingly, on my laptop, I've had this problem for months -- it's been running Ubuntu 9.04 for some time, and I have not yet upgraded it. Sound works in UO for a little while, then stops until application is restarted. I was living with it, since I do UO most often on my desktop. So, now since the desktop is doing the same thing, I'm more motivated to finding a solution! 

I'll post here if I figure it out.

---

### Post by Hans Olo on 2009-11-05
I though I had this problem fixed -- there was a VIA sound module loading for a 'modem' device. I had already black-listed the module for my onboard sound card, as I use a Sound Blaster Live PCI. It seemed that once I did: rmmod snd_via82xx_modem
Then restarted alsa, my sound under Ultima Online worked fine for over 2 hours.

IF you have the same situation - an onboard sound card and an add-on card, and in case you don't know where to black-list modules, edit the file:

/etc/modprobe.d/blacklist.conf

The lines I added to disable my on-board sound:
[I]blacklist snd_via82xx
blacklist snd_via82xx_modem[/I]

..of course, you would either need to reboot after making these changes, or manually rmmod the modules.

After some more digging, it seems I've tracked the problem down to PulseAudio. 
From [http://https://wiki.ubuntu.com/PulseAudio]("http://https//wiki.ubuntu.com/PulseAudio")
> There may be problems with getting sound from Adobe Flash v. 9 and earlier, **Wine** and Skype when these applications use the ALSA protocol. The sound is supposed to go through the "pulse" plugin in ALSA, that passes it to PulseAudio, where it get mixed with all other sound, and passed on to a audio interface. These problems should not occur in Flash v. 10 and later.

I don't think I need PulseAudio, since SoundBlaster Live! cards mix multiple sources on-board. So I will see if I can eliminate it all together.. I'll post my results here if it fixed my problem with sound on UO.

---

### Post by Hans Olo on 2009-11-07
***I posted this to another thread already, but my original problem was with Ultima Online under Wine, so I am posting here as well. The problem was indeed PulseAudio, so this is how to remove PulseAudio from Ubuntu 9.10***

Thanks to a commenter, Demagog on this page: [http://idyllictux.wordpress.com/2009...eaudio-at-bay/]("http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/")

I am now running on ALSA without that Pulse CRAP :grin:

His instructions were missing a step or two, so I will attempt to fill in the blanks:

# Remove PulseAudio and reboot!
sudo killall pulseaudio
sudo apt-get purge pulseaudio 
sudo reboot     # or reboot through the Gnome dialogs

# Install asoundconf-gtk and aumix-gtk
sudo apt-get install aumix-gtk 
sudo apt-get install asoundconf-gtk

# Download the missing 'asoundconf' binary, as it is no longer in the alsa-utils package!!!
Get alsa-utils_1.0.18-1ubuntu11_i386.deb from here (64-bit version also on the page):
[http://packages.ubuntu.com/jaunty/alsa-utils](http://packages.ubuntu.com/jaunty/alsa-utils)

 Extract  asoundconf  from alsa-utils*.deb with Archive Manager
 Then install it to the proper place:
 sudo cp asoundconf /usr/bin/
 
# Type on Terminal, or from your run dialog:
asoundconf-gtk

# Select your sound card from the list. Mine showed "LIVE", as I have a Sound Blaster Live! card.

# Run aumix-gtk, from the menu->Sound & Video->aumix
Make the window larger so you can see the sliders better. I had turn "PCM2" way up before I could hear anything. (I believe this is due to PulseAudio volumes being higer than alsa volumes?)

I now have working sound, and my system seems to be more responsive. The only problem still, is the stupid Gnome volume control only works with Pulse!! But I would rather have working sound and no volume control applet, than an applet and crappy sound. I'll just run aumix until the volume control is fixed.


Now I must note that before I did all of this, I tried using the 'pasuspender' binary before the command to run my wine games, which resulted in no sound. It's possible that would have worked if I had run the aumix app to adjust volumes... BUT, I'm not about to re-install PulseAudio to find out.

---

