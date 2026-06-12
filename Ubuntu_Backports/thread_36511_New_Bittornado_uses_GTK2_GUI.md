---
title: "New Bittornado uses GTK2 GUI"
date: 2005-05-23
forum: Ubuntu Backports
---

### Post by jdong on 2005-05-23
I just uploaded a new Bittornado backport. I forced it to select wxpython 2.5.3 on your system, so it'll have a pretty GTK2 GUI.


My preliminary testing shows nothing wrong, but I sense breakage from making such a no-brainer change ;)


Can you guys help me test?

---

### Post by ow50 on 2005-05-23
I have done the same myself earlier and never had any problems. I haven't used it often though, but I have downloaded about 4 or 5 large torrents without problems.

---

### Post by McQuaid on 2005-05-23
Hey that sounds great! Good work.

Before I give it a try, could you tell me if bittorando supports only using 1 port?  Normally bt need 6881-6899 or something like that.  I just have 1 port open as azureus can map the requests to all one port.

Also can you grab selected files within a torrent with this?  

I'll try it myself later but I'm not home yet and curious.

---

### Post by ow50 on 2005-05-23
[QUOTE=McQuaid]Before I give it a try, could you tell me if bittorando supports only using 1 port?[/QUOTE]
You can freely select a port range. I have never tried using only one port so I can't tell whether it'll work well or not.

[QUOTE=McQuaid]Also can you grab selected files within a torrent with this?[/QUOTE]
Yes.

---

### Post by McQuaid on 2005-05-23
Hey thx good to hear.  I should investigate myself but azureus has an option that is needed for writing to fat32 partitions (I think called incremental file writing or something).  I've never known if that was just a quirk of azureus or is it a feature that would be needed for any client trying to write to a fat32 part from inux using a bt client.

If anyone knows that would be great but I'm going to try and find any and I'll post back.

---

### Post by bored2k on 2005-05-23
[QUOTE=McQuaid]Hey thx good to hear.  I should investigate myself but azureus has an option that is needed for writing to fat32 partitions (I think called incremental file writing or something).  I've never known if that was just a quirk of azureus or is it a feature that would be needed for any client trying to write to a fat32 part from inux using a bt client.

If anyone knows that would be great but I'm going to try and find any and I'll post back.[/QUOTE]
 Have you tried using official bittorrent.com's ?

---

### Post by bored2k on 2005-05-23
This package is still in staging right ?

---

### Post by McQuaid on 2005-05-24
Ya the official client is no good for me. It needs all open ports afaik.

I just noticed g3torrent in staging as well. looks good.  Doesn't seem to have a cap for download though only upload.  I'll guess i'll install em both and compare.

---

### Post by sapo on 2005-05-24
I ll try it out and post a feedback later...

 ;-)

---

### Post by jdong on 2005-05-24
**g3torrent is pretty unstable!!!** I spent about two hours hacking it last night, but the result wasn't too positive.

If you'd like to help out, feel free to do so. See the discussion at [http://ubuntuforums.org/showthread.php?t=18369](http://ubuntuforums.org/showthread.php?t=18369)

---

### Post by McQuaid on 2005-05-25
On a side note about bittorent client performance,  most people want an alternative to azureus because of java, myself included.  But tonight I tried grabbing something in bittornado for the first time.  It was a popular torrent with 100 seeds and 1500 peers.  I configured tornado to use the port i have open for bt, made my upload capped at 35K and download at 200K.  Getting this torrent and after over an hour it was getting it at roughly 35/35 up/down.  Normally with azureus when the torrent is that healthy, it maxes my download.  Most torrents like this would easily hit my cap of 200K or at least be in the 100s.  So I gave up and stopped the torrent and resumed it in azureus, and sure enough in about 10 minutes I was getting 160K.  

I read an article with the author of bt and he said basically all bt clients try as aggressively as posible to get as much data as fast as they can.  Maybe this is somewhere where azureus is the most 'aggressive'.  

I share torrents til there are 1:1 ratio anyways but it's nice to have the torrent quicker.  I'm going to do some more tests but has anyone else found that azureus has the best performance regarding the actual bandwidth and not the resources it consumes?

---

### Post by jdong on 2005-05-25
That's a pretty OT side note, but yes, some BT clients (ahem, g3torrent) do try to be REALLY aggressive in playing the connect-to-everyone game. I'm sure you can hack the Python (easy-to-edit) source code to play the Azureus game, too.


The problem with Azureus is that it's a memory LEAK, not just high memory consumption. If Azurureus used 500MB VM and stopped at there, I'd be fine with it! Unfortunately, it seems like unbounded growth, reaching 2.3GB within 2 days.

---

### Post by rwabel on 2005-07-26
[QUOTE=jdong]That's a pretty OT side note, but yes, some BT clients (ahem, g3torrent) do try to be REALLY aggressive in playing the connect-to-everyone game. I'm sure you can hack the Python (easy-to-edit) source code to play the Azureus game, too.


The problem with Azureus is that it's a memory LEAK, not just high memory consumption. If Azurureus used 500MB VM and stopped at there, I'd be fine with it! Unfortunately, it seems like unbounded growth, reaching 2.3GB within 2 days.[/QUOTE]
 thanks for backporting that one. I got the following error message:
 ```
Traceback (most recent call last):
  File "./g3torrent.py", line 16, in ?
    import wxversion
ImportError: No module named wxversion
```

I had to change the line first line from: #!/usr/bin/env python
to: #!/usr/bin/env python2.4
in /usr/lib/g3torrent/g3torrent.py

Is it normal, that the open dialog looks like very old gtk?

---

### Post by strikeforce on 2005-07-26
[QUOTE=jdong]**g3torrent is pretty unstable!!!** I spent about two hours hacking it last night, but the result wasn't too positive.

If you'd like to help out, feel free to do so. See the discussion at [http://ubuntuforums.org/showthread.php?t=18369](http://ubuntuforums.org/showthread.php?t=18369)[/QUOTE]


I just added a package there that is g3torrent improved.  One of the original coders of g3 created his own bittorrent client based on the g3 code and is currently maintaining it. The links are in that thread that you posted.

There is a linux client as well as a bash script to install.  He uses gentoo atm so the bashscript sorts all the others out.

---

