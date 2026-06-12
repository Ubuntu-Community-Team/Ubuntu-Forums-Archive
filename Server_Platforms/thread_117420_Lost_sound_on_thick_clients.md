---
title: "Lost sound on thick clients"
date: 2006-01-14
forum: Server Platforms
---

### Post by ttaulman on 2006-01-14
I have figured out how to set up a new network at school for a new computer lab (with the help of some of you great people :KS ). The server is running Ubuntu 5.10 and each of the clients is running Edubuntu 5.10 (workstation install option). At the present time, we aren't too worried about thin clients because the lab has new computers that are very cable of running alone. When this all works, I’ll look at it, but maybe setup just an LTSP server. Each client should act like a stand alone computer except for pulling their home directory from the server. This was accomplished by using samba, nfs and ldap. I wanted the authentication to be central and there will still be a few windows clients that I haven't even addressed yet. I am exporting the /home directory from the server so the client can pick it up for an automount. Users have been added to the audio group on the server since that was the first thing I tried when the below took place.

I have two problems currently that halt everything.
1) Takes over a minute to log into GUI from a client PC.
2) Once it gets logged in, I have no sound.

Does anyone have any thoughts or suggestions on how to fix this? My suspicion is they are related, but I don't know why sound would not work. When I log into a local account on the client, sound is there.

---

### Post by JackandJohn on 2006-01-17
is it possible that one of the ~/.folders is configuring the sound card on the client machines somehow? as in, something is reading a config file from the home dir, and is configuring like the server pc?

What were to happen if you created a completely blank random folder and mount *it* as home?


As for the amount of time; you may want to take a look at how much data is on the home drive, and what mounting protocol you are using.
I mention, because I just saw the other day a writup on all the different filesystems, and some of them did alot of work during init, while others rounded out and did only a little at the beginning.
Past that; check your logs, or disable the splash screen and see where it's hanging. (or if those dont work; go to text login, log in as user, and start your xwindows session)

---

