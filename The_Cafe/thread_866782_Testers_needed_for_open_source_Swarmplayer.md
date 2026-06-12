---
title: "Testers needed for open source Swarmplayer"
date: 2008-07-22
forum: The Cafe
---

### Post by philinux on 2008-07-22
Not sure where to put this so feel free to move it.

Testers needed

[http://trial.p2p-next.org/](http://trial.p2p-next.org/)

It's from the EU funded p2p-next consortium.

[http://www.tribler.org/P2P-Next/19Million-for-P2P](http://www.tribler.org/P2P-Next/19Million-for-P2P)

Open source and Linux version at start. Must be worthwhile.

---

### Post by Vadi on 2008-07-22
Thanks for the link

---

### Post by oldgreyfox on 2008-07-22
I downloaded Swarmplayer 1.0.1 from the repository.
When I ran it nothing happened at all.

There is no help screen on the website, so I can't go any further.

Any ideas?

---

### Post by philinux on 2008-07-22
> **oldgreyfox said:**
> I downloaded Swarmplayer 1.0.1 from the repository.
When I ran it nothing happened at all.

There is no help screen on the website, so I can't go any further.

Any ideas?

Thats odd. It creates a menu item in Internet.

Running that takes you to gui to select the torrent to play. You need to download either of the two test torrents, or both as I did.

---

### Post by philinux on 2008-07-22
Come on guys this is open source!

---

### Post by seuzy13 on 2008-07-22
I've got time on my hands. Think I'll give it a shot.

---

### Post by philinux on 2008-07-22
Well Done. :)

---

### Post by Joeb454 on 2008-07-22
Moved to the Cafe :) It wasn't a support request :)

I'm quite interested to see how this turns out actually, it's got EU backing too

---

### Post by philinux on 2008-07-22
Thanks for moving to appropriate forum.

---

### Post by wrtpeeps on 2008-07-22
Was using it earlier.

It doesn't do anything interesting at the moment. I tried the live stream and it was really choppy.

---

### Post by Joeb454 on 2008-07-22
Well it's not long entered beta, give it a chance - it isn't a Google beta app after all (is Gmail still beta?).

And no problem philinux :)

---

### Post by uberlube on 2008-07-22
Im using linux mint so I decided to install using the .deb so I didn't have to mess around adding it to the repos. It installed quickly with no problems and launched just the same. Both test streams worked well and were not choppy at all. Also tried a highly seeded torrent and after it buffered and found an acceptable download speed it launched the media in VLC. Great app and i look forward to seeing it grow. :)

---

### Post by philinux on 2008-07-23
Excellent. Hope this thing takes off.

---

### Post by oldgreyfox on 2008-07-24
Thanks for that.  I was expecting the files to be in the Tribler directory.

---

### Post by philinux on 2008-07-24
Come on guys have a go. It's a scientific test of the system.

---

### Post by nbayiha on 2008-07-28
I just heard about it today , so i am going to give it a try.
And will reply .

---

### Post by Kingsley on 2008-08-09
This is the error I get when I follow the directions to run from source.

```

[king@localhost swarmplayer-1.0.1]$ python Tribler/Player/swarmplayer.py live.tstream
Traceback (most recent call last):
  File "Tribler/Player/swarmplayer.py", line 25, in <module>
    from Tribler.Core.API import *
ImportError: No module named Tribler.Core.API

```

I get this error on Fedora 9.

---

### Post by synctext on 2008-08-10
> **Kingsley said:**
> This is the error I get when I follow the directions to run from source.
```

[king@localhost swarmplayer-1.0.1]$ python Tribler/Player/swarmplayer.py live.tstream
Traceback (most recent call last):
  File "Tribler/Player/swarmplayer.py", line 25, in <module>
    from Tribler.Core.API import *
ImportError: No module named Tribler.Core.API

```
I get this error on Fedora 9.

Message from the SwarmPlayer developers...
This error indicates the PYTHONPATH needs to be set:
```

env PYTHONPATH=. python Tribler/Player/swarmplayer.py ParadisoCam.mpegts.tstream

```

Thanx for all the support people, we got close to 7000 testers. Really helpful feedback and solid contribution for moving this code forward.

---

### Post by Kingsley on 2008-08-12
I get another error when I attempt the solution.

```

[king@localhost swarmplayer-1.0.1]$ env PYTHONPATH=. python Tribler/Player/swarmplayer.py ParadisoCam.mpegts.tstream
Traceback (most recent call last):
  File "Tribler/Player/swarmplayer.py", line 25, in <module>
    from Tribler.Core.API import *
  File "/home/king/Desktop/swarmplayer-1.0.1/Tribler/Core/API.py", line 19, in <module>
    from Tribler.Core.Session import *
  File "/home/king/Desktop/swarmplayer-1.0.1/Tribler/Core/Session.py", line 14, in <module>
    from Tribler.Core.SessionConfig import *
  File "/home/king/Desktop/swarmplayer-1.0.1/Tribler/Core/SessionConfig.py", line 13, in <module>
    from Tribler.Core.BitTornado.RawServer import autodetect_socket_style
  File "/home/king/Desktop/swarmplayer-1.0.1/Tribler/Core/BitTornado/RawServer.py", line 5, in <module>
    from SocketHandler import SocketHandler
  File "/home/king/Desktop/swarmplayer-1.0.1/Tribler/Core/BitTornado/SocketHandler.py", line 19, in <module>
    from Tribler.Core.NATFirewall.DialbackMsgHandler import DialbackMsgHandler
  File "/home/king/Desktop/swarmplayer-1.0.1/Tribler/Core/NATFirewall/DialbackMsgHandler.py", line 33, in <module>
    from Tribler.Core.Overlay.SecureOverlay import OLPROTO_VER_THIRD
  File "/home/king/Desktop/swarmplayer-1.0.1/Tribler/Core/Overlay/SecureOverlay.py", line 19, in <module>
    from Tribler.Core.Overlay.permid import ChallengeResponse
  File "/home/king/Desktop/swarmplayer-1.0.1/Tribler/Core/Overlay/permid.py", line 10, in <module>
    from M2Crypto import Rand,EC,EVP
  File "/home/king/Desktop/swarmplayer-1.0.1/Tribler/Player/__init__.py", line 14, in <module>
    
  File "build/bdist.linux-i686/egg/M2Crypto/__m2crypto.py", line 7, in <module>
  File "build/bdist.linux-i686/egg/M2Crypto/__m2crypto.py", line 6, in __bootstrap__
ImportError: /home/king/.python-eggs/M2Crypto-0.19-py2.5-linux-i686.egg-tmp/M2Crypto/__m2crypto.so: undefined symbol: PEM_read_bio_ECPrivateKey

```

---

### Post by masch on 2008-08-31
I have the same error Kingsley, do you know how to resolved?

Salu2...

---

### Post by saru411 on 2008-09-17
hi i installed swarmplayer and now none of my bittorrents work. i use bittornado for BT D/L. I'm unsure of how to open a torrent file in a terminal to see what error messages i might be getting. Any help is appreciated.

---

### Post by tanha on 2008-10-23
> **saru411 said:**
> hi i installed swarmplayer and now none of my bittorrents work. i use bittornado for BT D/L. I'm unsure of how to open a torrent file in a terminal to see what error messages i might be getting. Any help is appreciated.

Don't know if this is too late or not ... you can open any application in the terminal by typing in the application name. If you want to open a specific file you can just specify the file name. For example:

```
vlc /home/username/movie.avi
```

Hope that helps.

---

### Post by saru411 on 2008-10-24
Yes it's too late but if you type bittornado into terminal it doesn't open the program. I understand how terminal works and have been using it for years but bittorrent(bittornado) yields "bash command not found"

I have already reinstalled my o/s since no one had an answer for me.

Thanks anyway

---

### Post by tanha on 2008-10-24
> **saru411 said:**
> Yes it's too late but if you type bittornado into terminal it doesn't open the program. I understand how terminal works and have been using it for years but bittorrent(bittornado) yields "bash command not found"

I have already reinstalled my o/s since no one had an answer for me.

Thanks anyway

OK.

Well, in case you want to know... you need to input the absolute path to bittornado, as it is not in $PATH. (you could add the path if you wanted, though.) In any case, type this into the terminal to achieve what you wanted:

```
/usr/bin/btdownloadgui.bittornado
```

cheers

---

### Post by atomkarinca on 2008-10-30
> **Kingsley said:**
> This is the error I get when I follow the directions to run from source.

```

[king@localhost swarmplayer-1.0.1]$ python Tribler/Player/swarmplayer.py live.tstream
Traceback (most recent call last):
  File "Tribler/Player/swarmplayer.py", line 25, in <module>
    from Tribler.Core.API import *
ImportError: No module named Tribler.Core.API

```

I get this error on Fedora 9.

I've got the same error on Arch Linux and adding "env PYTHONPATH=." to the beginning doesn't help, either.

---

### Post by smizzi428 on 2011-03-25
I have it downloaded and installed and working. Trying to test the uninstall functionally - and I can not uninstall. What am I missing?

---

### Post by cariboo on 2011-03-25
This thread is over three years old, is this still relevant? Closed.

---

