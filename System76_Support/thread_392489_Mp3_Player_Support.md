---
title: "Mp3 Player Support"
date: 2007-03-24
forum: System76 Support
---

### Post by tux_rox on 2007-03-24
This might be in the wrong section, but oh well...

I have a Creative Zen MicroPhoto, and will continue to have it until it becomes utterly obsolete... it works really well with Windows Media Player (drag and drop playlists, automatic recognition, etc.), but will it (or, for that matter, other mp3 players) work in Ubuntu?

P.S.  I know that mp3's are a no-no in Ubuntu until you get Automatix or other workarounds - I'm more concerned with the player than the file format.

Thanks!

---

### Post by qamelian on 2007-03-24
Depending on the version of the firmware on this player, it may work with no extra fuss by simply installing either gnomad2 or neutrino, both of which are in the Ubuntu repos and can be installed using aptitude/at-get/synaptic.

If it contains newer firmware that "upgrades" it to use MTP (Media Transport Protocol), it should still be usable but you may need to build libmtp and gnomad2 from source to get it working.

Search these forums for gnomad2 and libmtp. I know there have been a couple of howto's describing the process.

---

### Post by tux_rox on 2007-03-24
Thanks - I was scared I would have to do something drastic like dual-booting just because my mp3 player wouldn't work.  Phew!

---

### Post by Lord Illidan on 2007-03-24
It's not that drastic, imho...but anyway,yes, gnomad2 will/should/probably work.

You want to talk about drastic, I formatted my ipod nano to Rockbox to play .ogg files and Doom.

---

### Post by qamelian on 2007-03-24
> **Lord Illidan said:**
> It's not that drastic, imho...but anyway,yes, gnomad2 will/should/probably work.

You want to talk about drastic, I formatted my ipod nano to Rockbox to play .ogg files and Doom.

Desperate times call for desperate measures!

---

### Post by dracomordag on 2007-03-27
> **tux_rox said:**
> Thanks - I was scared I would have to do something drastic like dual-booting just because my mp3 player wouldn't work.  Phew!
in case you haven't found it yet... [http://www.ubuntuforums.org/showthread.php?t=199250](http://www.ubuntuforums.org/showthread.php?t=199250)

---

### Post by macogw on 2007-03-27
Don't use the debs in the repos.  libmtp in the repos doesn't work.  Compile it from source and use the --prefix=/usr but don't use checkinstall like the howto says.  just use make install.  youll have to compile gnomad2 as well though since you compiled the library and apt doesnt know about it.

---

