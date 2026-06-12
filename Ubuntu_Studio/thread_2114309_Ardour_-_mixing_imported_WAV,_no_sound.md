---
title: "Ardour - mixing imported WAV, no sound"
date: 2013-02-09
forum: Ubuntu Studio
---

### Post by callmebruce on 2013-02-09
I'm running Ubuntu Studio 12.10. I can play mp3's and wav files under Audacity. I opened a new project in Ardour, imported two wav files, mixed them together (well, simply put one track over the other to play a trumpet and guitar together). I went to play the tracks inside Ardour, but got no sound. I exported the project, and can play that under Audacity.

I let Ardour kick off JACK, rather than manually starting JACK. I am not trying to record anything from the mic, simply trying to work with MP3's and wav files. 

JACK looks like this:
[https://lh3.googleusercontent.com/-7sGRpNIHQd4/URa__UsnJ3I/AAAAAAAACxw/kVTnHgR0TmE/s640/Screenshot%2520-%252002092013%2520-%252004%253A26%253A00%2520PM.png](https://lh3.googleusercontent.com/-7sGRpNIHQd4/URa__UsnJ3I/AAAAAAAACxw/kVTnHgR0TmE/s640/Screenshot%2520-%252002092013%2520-%252004%253A26%253A00%2520PM.png)

For input, my options are: hw:0 HDA Intel, hw:0,0 AD198x Analog, and (default). I left it default. For output my options are: hw:0 HDA Intel, hw:0,0 AD198x Analog and hw:0,1 AD198x Digital and (default). I left output as (default).

My JACK connections look like this under Audio:
[https://lh3.googleusercontent.com/-3XfwpVnTiNw/URbBt-GNXhI/AAAAAAAACyA/2QtYrJtLhOg/s605/Screenshot%2520-%252002092013%2520-%252004%253A37%253A21%2520PM.png](https://lh3.googleusercontent.com/-3XfwpVnTiNw/URbBt-GNXhI/AAAAAAAACyA/2QtYrJtLhOg/s605/Screenshot%2520-%252002092013%2520-%252004%253A37%253A21%2520PM.png)  

I don't see anything connected under midi or Alsa. I think I need to make some Alsa connections, but not sure what needs to connect where:
[https://lh3.googleusercontent.com/-cuEirhgafiA/URbDS0WRkLI/AAAAAAAACyI/jASExYZmjRY/s601/Screenshot%2520-%252002092013%2520-%252004%253A40%253A52%2520PM.png](https://lh3.googleusercontent.com/-cuEirhgafiA/URbDS0WRkLI/AAAAAAAACyI/jASExYZmjRY/s601/Screenshot%2520-%252002092013%2520-%252004%253A40%253A52%2520PM.png)


What needs to connect to what so I can import a sound file into Ardour then play the sound file when I hit the play button?

---

### Post by jejeman on 2013-02-09
Everything looks connected right to me.
If you are using the card which has speakers pluged in, I don't see the reason for no sound ouput jack wise.

I've noticed that few people has this problem regarding hearing sound from Ardour2. I really don't seee why.

---

### Post by callmebruce on 2013-02-10
Booted off the USB and Ardour worked perfectly. Was able to grab sounds from freesound, mix and play. Decided to just reinstall. Not sure why it works, but it does.

---

