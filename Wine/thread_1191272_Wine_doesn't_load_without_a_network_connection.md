---
title: "Wine doesn't load without a network connection"
date: 2009-06-18
forum: Wine
---

### Post by bryceowen on 2009-06-18
I was trying to load Steam on my laptop through Wine and the process shows up in ps aux, but nothing happens on the screen. Believing Steam to have become corrupt, I connected to the hard-wire network to redownload it and almost immediately after connecting, Steam came up.

I shut steam down and re-opened it while connected and it came up normally. Then I disconnected from the network again and tried to launch it: same problem as before. It appears to launch and shows as a running process, but doesn't DO anything until I plug into the network (can't test with wireless right now, but will when I get home).

Out of curiosity, I tried a different app under Wine to see if the same problem happened (PSPad) and sure enough, it behaves the exact same way. Unless I'm connected to a network (doesn't have to be internet, just an active network connection), Wine doesn't start the program.

Can anyone tell me what is going on?

Disregard:
The problem seems to stem from the fact I have a Windows share mounted. When I umounted the share, all Wine apps started without a hitch. (Though I have no idea why an inability to connect to a share would influence Wine...)

---

