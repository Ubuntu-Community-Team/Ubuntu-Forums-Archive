---
title: "Blank Icon space on Starling"
date: 2010-11-07
forum: System76 Support
---

### Post by nealaustin on 2010-11-07
On my Starling with 10.04 my desktop has these huge icons for each program in the favorites part of the menu. I have added some and taken away some. They are not rearrangeable. At one point a blank space appeared at the end and as I took away Icons and added more it started to move towards the front of the line. I tried deleting them all and then replacing them with the result that I have this blank space on the upper left corner of my menu. Any Idea how to get rid of it?

---

### Post by Dave_L on 2010-11-07
The Favorites configuration seems to be in the gconf-editor key "/apps/netbook-launcher/favorites".  The corresponding location in the file system is "~/.gconf/apps/netbook-launcher/favorites/".

You might see if anything looks unusual there.

Make changes at your own risk.  If you break something, I don't know if it's easy to fix. :wink:

---

### Post by nealaustin on 2010-11-07
I have a long history of breaking things. Thanks though, anyone with an easy fix?

---

### Post by nealaustin on 2010-11-12
Finally figured out how to fix the missing Icon/Button. I removed all of the icons in the favorites menu. Powered down and then restarted. It priorly didn't work that way with a simple restart. One Icon appeared upon the restart and It was a earth (network or whatever) I then added my favorite programs in the order that I wanted and during that process I removed the earth icon and now all is good with no empty spaces.

---

### Post by flukeairwalker on 2010-11-16
I just removed UNE last night for 10.10 so I can't say with 100% certainty, but I believe in System>Preferences>Main Menu you can edit the order of the favorited programs.

---

