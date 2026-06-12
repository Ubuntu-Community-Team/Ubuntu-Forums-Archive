---
title: "Version mixup and no internet after ubuntuzilla install"
date: 2008-07-22
forum: Ubuntuzilla
---

### Post by Gerippter on 2008-07-22
Hi.
I've just installed ubuntuzilla to keep my firefox and thunderbird up to date. I'm using the 64bit version of Ubuntu Hardy Whatever...(8.x), pretty fresh install, with the default thunderbird and firefox install, resp. using the package manager.
I installed some add-ons to both ff and tb and then realised it was tedious to keep them up to date manually... but voila! ubuntuzilla to the rescue.
Theoretically. 

I am trying to reconstruct what I did...
Upon my first try, I got some problems with some libraries and installed the 32bit compatibility libraries as described here:
[http://ubuntuzilla.wiki.sourceforge.net/#usersof64bitubuntu](http://ubuntuzilla.wiki.sourceforge.net/#usersof64bitubuntu)
```

sudo apt-get install ia32-libs*
sudo apt-get install lib32asound2 lib32ncurses5 lib32stdc++6
```

I then downloaded ubuntuzilla (amd64 version) and installed it by double clicking.
Did some hasty reading and did 
```

ubuntuzilla.py -a installupdater
 
ubuntuzilla.py -a installupdater -p thunderbird
```

as I thought I did have both ff and tb installed already. I eventually got a notification that a newer version (3.0.1) of FF is available, but the links in the notification were dead: no clicking, no copying, no action. 

so I went back and read again, and this time found that I need to update the mozilla version using the install option, so that is what I did:
```

ubuntuzilla.py -a install -p firefox
 
ubuntuzilla.py -a install -p thunderbird
```

All went well, installed both firefox and thunderbird, copied the addons etc, gave one error for updating ifox (theme), but then started. 

However, neither TB nor FF get a connection.
After a bit of try and error I decided to deinstall both the mozilla versions again, as I have to do some other more urgent stuff atm and need the internet.

so, to uninstall i did

```
ubuntuzilla.py -a remove -p firefox
 
ubuntuzilla.py -a remove -p thunderbird
```

All went well, but annoyingly the links firefox and thunderbird were not reverted, but deleted. However, starting firefox-3.0 works fine, Internet is back.
Thunderbird however is lost, even though the package manager says its still installed, I dont have a clue how to find it.

Curious and ready to procrastinate, I did another install using 
```

ubuntuzilla.py -a install -p firefox
 
ubuntuzilla.py -a install -p thunderbird
```

to find out what the differences are.

Unfortunately, I did not close FF when installing, but only realised when the ubuntuzilla script wanted to copy the preferences. I then tried to close FF, but the installation via the script failed. I tried again with FF closed, and it worked.

Now if I start the repository 3.0 version, it tells me firefox was updated to 3.0.1, but shows 3.0 as the version in the 'about' section, but all in all works fine.
If I start 'firefox' from the console, while firefox-3.0 is open, this both versions work, and the new mozilla version shows version '3.0.1'.

However if the firefox-3.0 is closed, 3.0.1 (mozilla version) does not get any connection, nor does TB.

Arg. 
No Email, big mess, please help!

---

### Post by Gerippter on 2008-07-22
ok, obviously thunderbird isnt gone. (rolleyes)
just had to look a bit harder...

---

### Post by nanotube on 2008-07-22
Hi,
well, at least you got your old ff and tb back. :)

anyway, one thing you can try is pull down the tar.bz2 from mozilla yourself, extract it to some directory (say, a folder on your desktop).

then, quit all firefoxes, open that directory where you extracted, and double-click on "firefox" from there.

does that work? can it access the internet?

---

### Post by Gerippter on 2008-07-23
good point.
tried it, and no, it can not access the internet.

hm.
might have to check with the sysadmins, as my acc is local, but integrated into the insitute FS and yesterday I was kicked out of the sudos list again by some unidentified process. Might be something todo with rights, no?

---

### Post by nanotube on 2008-07-23
> **Gerippter said:**
> good point.
tried it, and no, it can not access the internet.

hm.
might have to check with the sysadmins, as my acc is local, but integrated into the insitute FS and yesterday I was kicked out of the sudos list again by some unidentified process. Might be something todo with rights, no?

hm, well, i am not sure /why/ it is that mozilla build of ff doesn't access the net for you, but at least we have confirmed that the problem is not with ubuntuzilla, but with something in your system not liking the mozilla build...

i don't think you need admin rights in order to access the net, though, so it's probably something else...

---

