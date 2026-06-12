---
title: "NIS and groups"
date: 2007-10-08
forum: Server Platforms
---

### Post by skullmunky on 2007-10-08
my NIS users oten have trouble with peripherals (sound, scanner, etc.. ) because they're not in the secondary groups.  obviously the answer is to add them to the map from the NIS server.  this is a pain, because users are added and removed frequently.  is there a way to make ALL users merged over NIS be just automatically added to audio, dialout, etc. ?

My other solution seems to be to hack the udev rules to make the devices world-read-and-writable.  Which I'm comfortable with but that seems like excessive work too.  Any easier solution?

thanks,

SkullMunky, the laziest admin in the West

ps is there a forum for just admin topics in general, not specifically server and security related?

---

