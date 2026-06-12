---
title: "Stream webradio"
date: 2008-12-31
forum: Server Platforms
---

### Post by Flance on 2008-12-31
I have an Ubuntu Server installed and i am looking for a specific application. 
The application i am looking for is able to play streaming audio like webradio.
Is there such an aplication?

[SIZE="1"](I'm sorry for my bad english)[/SIZE]

---

### Post by TestDummy! on 2008-12-31
Well, a program like **mpg123** (for MP3) or **ogg123** (for Ogg Vorbis) should be able to take a URL as an argument. Ubuntu Server doesn't have **ALSA** set up by default, so if you haven't installed that already, you'll have to do so to get audio playback.

To install these (I'm guessing they're all in the regular repos), you do: **sudo apt-get install alsa mpg123 vorbis-tools**

**ogg123** is included in **vorbis-tools**.

I'm assuming that's what you were asking for: A terminal application for listening to pre-existing streaming audio on the Internet, although it works fine for playback of local files too.

---

