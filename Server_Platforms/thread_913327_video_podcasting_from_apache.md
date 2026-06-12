---
title: "video podcasting from apache"
date: 2008-09-07
forum: Server Platforms
---

### Post by scotton on 2008-09-07
Hello Everyone!  This is my first post and i hope you think it is a good one :-D

I have been using ubuntu as my desktop for over a year now, and have been working on a certain script for almost as long.  The script deals with my downloaded television shows and is meant for use with my Ipod (and now new laptop :-))  The script works great, recognizing when a download is completed and proceeding to convert the file and place it in an appropriate location.  It also whips up an rss entry for the episode and places that into season specific rss files.  All of these files are accessible by apache and are then viewable around the house (as an rss in a browser, or even in Itunes when the address has been added).  Then the problem begins....

In Itunes, I can view the podcast, see the episodes and read their descriptions.  I can even start downloading.  I then get the lovely "err=-3259" and the download stops.  From researching this It seems that Itunes needs to have specific ports available to it in windows to be able to download, specifically, TCP 3689 and UDP 5353.  I have made those ports available in my firewalls(both on the laptop and the desktop/server).  Still getting the error...booooo!

So enough background, I guess that my question comes down to requirements for podcast serving.  Am I in need of opening different outgoing ports on the server?  perhaps a different module in apache?  Haven't been able to find anyone discussing podcast serving in the *buntu forums, so hopefully I have laid out the problem clearly and someone...anyone...has ideas :-)

Thanks in advance!

---

