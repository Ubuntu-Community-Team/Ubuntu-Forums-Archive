---
title: "MPD: cannot connect client until a ssh connection is established"
date: 2013-05-15
forum: Server Platforms
---

### Post by moody_mark on 2013-05-15
Hi Folks,

I have a odd problem: I have a old Toshiba sattelite laptop which runs ubuntu server. Its a great way to make use of an old PC that would otherwise have been thrown out. It runs squid proxy for web access, sarg reports for web useage reports, apache http server for viewing the sarg reports, and mpd for playing music, via a external amp and speakers. The machine works a treat and I know it has connectivity because the web proxy is constantly in use by my kids PCs, the wifes iPad and other devices like phones and other PCs. Its really useful to be able to connect to MPD with a client on a mobile device like a phone or tablet to play music and radio. Often I've showed it to friends who are taken aback when they realise its all done for free and not some expensive solution bought for £££, a good argument in the "pros" for linux :-)

There is one strange problem thought and I think its something to do with MPD; when you connect with a client if MPD hasnt been used for a while, say a few hours, it doesn't matter which client, you can view the currently playing song but the controls like stop/start will not work and you cannot view playlists etc. Only when you open a terminal ssh session to the device does mpd respond. Now I know its not a connectivity thing because as I said above other services like the web proxy and http server all work 24/7.

Also sometimes I see TCP SYN_SENT connections built up on the server to the mobile device, and i have to restart the service (sudo service mpd restart) to get it working. I have turned on debugging in the mpd logs but nothing of use was seen there. Of course I have to ssh in to check connections which repairs the problem. If im seeing SYN_SENT then the mpd service will need a restart, if I see lots of ESTABLISHED connections then a ssh connection will generally resolve it.

I'm using for clients: "mpd droid" - andriod, "mpad" - iOS, "Sonata" - Ubuntu 10.04 desktop.

Has anyone seen anything similar and have any suggestions?

---

