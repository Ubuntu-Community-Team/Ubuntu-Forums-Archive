---
title: "What do you use to Stream Audio from your server?"
date: 2009-04-04
forum: Server Platforms
---

### Post by redonwhite on 2009-04-04
Here are just 4 I've found while doing my research for setting up a streaming audio server.  If you select "other" please let me know what you like to use and why.  Thanks.  ):P

---

### Post by arsnova on 2009-04-05
I route audio over CAT5 to different rooms in the home, and MP3Blaster is a command line utility that works nicely for exactly that. Open a shell to the server and run the screen command (screen -S 'name'). Start MP3Blaster, choose or create playlists, then just exit the screen and (optionally, but beautifully) log off your machine.

Serving the same purpose, SSHing in with X session running allows you to run Amarok or other graphical clients. Still, I like the flexibility of MP3Blaster, and the menus are outlined well--it's keyboard driven, obviously, so it means a bit more in terms of learning the interface. Here's the Sourceforge page: [http://mp3blaster.sourceforge.net/]("http://mp3blaster.sourceforge.net/")

---

### Post by TwiceOver on 2009-04-05
Subsonic for network/internet streaming.

For house music, my server has an audio out going to an FM transmitter.  Frontended with PHPmpd.  Can change the songs/playlist from any browser.  Any radio in the house can pick up the transmitter.

---

### Post by redonwhite on 2009-04-05
> **TwiceOver said:**
> Subsonic for network/internet streaming.

For house music, my server has an audio out going to an FM transmitter.  Frontended with PHPmpd.  Can change the songs/playlist from any browser.  Any radio in the house can pick up the transmitter.

Ouu! I like that idea with the FM transmitter. :p

---

