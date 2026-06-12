---
title: "Possible DoS attack - Help logging"
date: 2010-09-19
forum: Security
---

### Post by POQbum on 2010-09-19
I believe someone is flooding the UDP ports in a very short burst (under  10 seconds) - enough for the game servers to lose connection with all of  it's players causing all 6 of the game servers I run go to 0.

I run game servers on a ubuntu server. Renting from a datacenter and they have no issues with their connection.

The help I'm looking for is for anything that could log this activity or anything related, so I can look back on it and pick out the real problem.

Most likely a script kiddie I'm dealing with so I think it should be fairly easy to stop once I find out, but as of now I have no way of defending and no way of catching.

I tried reading up on another thread about ip tables logging incoming UDP connections, but could not get it to work- or maybe it was working and I couldn't find where it was spitting out the logs.

I'm a newbie at linux and especially ubuntu.

Any help at all would be great.

Many thanks
 - Paul

---

### Post by Rubi1200 on 2010-09-19
You might want to look at using Snort:
[http://ubuntuforums.org/showthread.php?t=1477696](http://ubuntuforums.org/showthread.php?t=1477696)

From the same security stickies by bodhi.zazen:
[http://ubuntuforums.org/showthread.php?t=1477662](http://ubuntuforums.org/showthread.php?t=1477662)

A more general overview of security:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

