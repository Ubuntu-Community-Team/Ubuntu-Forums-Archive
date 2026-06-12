---
title: "HowTo configure 8.04 for Jack part 2"
date: 2009-10-15
forum: Ubuntu Studio
---

### Post by llwdtp on 2009-10-15
[SIZE=2]

**[SIZE=5]Disable pulse audio[/SIZE]**
[/SIZE]First install sudo apt-get install sysv-rc-conf
[LEFT][IMG]http://docs.google.com/File?id=dhjrjpnc_13dtkhbm46_b[/IMG][/LEFT]

Then use it
*sudo sysv-rc-conf* 
will open the tool.  Scroll down to pulseaudio using control n.

[LEFT][IMG]http://docs.google.com/File?id=dhjrjpnc_14fsz2s6d8_b[/IMG]

[/LEFT]
Use the arrow keys and the space bar to get rid of all the checks in the pulseaudio row.

[LEFT][IMG]http://docs.google.com/File?id=dhjrjpnc_15hkkb68gb_b[/IMG][/LEFT]

Use *q* to quit
[B][SIZE=5]
Alsa assignment[/SIZE][/B]
Now assign the main audio card to Alsa. First use *asoundconf list* to see your sound card choices. Then use 
*unset-pulseaudio* and *asoundconf set-default-card 'your card'  *to assign the card to Alsa ( I think). Notice that card in the example below is *Live* for the sound blaster live.

[LEFT][IMG]http://docs.google.com/File?id=dhjrjpnc_168cgk6vf7_b[/IMG]

[SIZE=5]**Default driver**[/SIZE]
Next we edit the file by opening it up as shwon below.


[IMG]http://docs.google.com/File?id=dhjrjpnc_17d4tvdmf8_b[/IMG]

It is supposed to say what is shown below. Mine did not need a change but I was toald to check that the default_drive = alsa.

[LEFT][IMG]http://docs.google.com/File?id=dhjrjpnc_18gnq6xchq_b[/IMG]

[SIZE=5]**Sound panel**[/SIZE]
Next we open the panel ***System>preferences>sound*** as shown below. You should make it look as shown below except your Default mixer tracks may be a bit different.
[/LEFT]


[IMG]http://docs.google.com/File?id=dhjrjpnc_19c2sjzqdh_b[/IMG][/LEFT]

Now go to 
***HowTo configure 8.04 for Jack part 3***

---

