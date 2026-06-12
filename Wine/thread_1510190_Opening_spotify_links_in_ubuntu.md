---
title: "Opening spotify links in ubuntu"
date: 2010-06-15
forum: Wine
---

### Post by MacHaddock on 2010-06-15
Is there a way to get wine to open the spotify links you get on say facebook? And is there a way to get wine to tell firefox in ubuntu to open the links in spotify?

---

### Post by .nedberg on 2010-06-15
> **MacHaddock said:**
> Is there a way to get wine to open the spotify links you get on say facebook? And is there a way to get wine to tell firefox in ubuntu to open the links in spotify?

From the "[Running-Spotify-under-Wine]("http://www.spotify.com/no/help/faq/wine/#opening-spotify-links-in-web-browsers")" documentation on spotify.com:

> **Opening spotify links in web browsers**

The installer adds keys to the registry in Wine so that web browsers can handle spotify links, but this is not picked up by web browsers in Linux.

Create an openspotify script by pasting the following commands in a terminal: (\ means line wrap)
echo '#!/bin/sh' > $HOME/bin/openspotify
echo 'exec wine "C:\Program Files\Spotify\spotify.exe" /uri "$@"' \
>> $HOME/bin/openspotify
chmod 755 $HOME/bin/openspotify

**Configure Firefox/Chrome**

Firefox and Chrome use xdg-open to open external protocols, which you can configure by pasting the following commands in a terminal: (\\ means line wrap)
gconftool-2 -t string -s /desktop/gnome/url-handlers/spotify/command \
 "$HOME/bin/openspotify %s"
gconftool-2 -t bool -s /desktop/gnome/url-handlers/spotify/needs_terminal false
gconftool-2 -t bool -s /desktop/gnome/url-handlers/spotify/enabled true

[B]Configure Opera
[/B]
Open Preferences. Select the Advanced tab and then the Programs tab. Click “add” and enter spotify in the protocol field and select the openspotify program as the handler program.

---

### Post by bjornolai on 2010-08-05
If you are using the native (sort-off) client these commands, run in terminal, will do it:

```
gconftool-2 -s /desktop/gnome/url-handlers/spotify/command '/usr/bin/spotify /uri %s' --type String
```

```
gconftool-2 -s /desktop/gnome/url-handlers/spotify/enabled --type Boolean true
```

---

### Post by MacHaddock on 2010-08-06
Thank you so much. This worked!

I love this place :D

---

### Post by lunalui on 2010-09-27
Sorry to post again in a closed thread, but I'm having the same problem mentioned here and I seem unable to fix it.
I've just installed the open version of Spotify that runs under wine. At the beginning I had an error message when I tried to open spotify links in firefox, telling me firefox did not know how to handle the links. 
After following bjornolai suggestion (thanx), I managed to have firefox ask me which application should be used to open the link.
I chose the Desktop spotify launcher to no effect.
I then tried what's suggested here
[http://atheistblogger.com/2008/12/17/using-spotify-links-in-linux/](http://atheistblogger.com/2008/12/17/using-spotify-links-in-linux/)
with the same result...
I tried other suggestions I found by googling but nothing seems to work...
any help will be really appreciated. Thanks in advance

---

### Post by Begin_learn on 2010-09-28
hi .nedberg.can we chat on some place??

---

### Post by .nedberg on 2010-09-28
> **Begin_learn said:**
> hi .nedberg.can we chat on some place??

I'm not solving this at all. I just copy the spotify links and paste them into Spotify. The solution I posted is from the Spotify under Wine page on spotify.com.

---

### Post by lunalui on 2010-09-28
> **lunalui said:**
> Sorry to post again in a closed thread, but I'm having the same problem mentioned here and I seem unable to fix it.
I've just installed the open version of Spotify that runs under wine. At the beginning I had an error message when I tried to open spotify links in firefox, telling me firefox did not know how to handle the links. 
After following bjornolai suggestion (thanx), I managed to have firefox ask me which application should be used to open the link.
I chose the Desktop spotify launcher to no effect.
I then tried what's suggested here
[http://atheistblogger.com/2008/12/17/using-spotify-links-in-linux/](http://atheistblogger.com/2008/12/17/using-spotify-links-in-linux/)
with the same result...
I tried other suggestions I found by googling but nothing seems to work...
any help will be really appreciated. Thanks in advance


I'll try adding some more details, so maybe someone will find the situation intriguing enough to check where the problem is...

I've got a pc and  a vaio laptop, both with the same version of lucid.

On both machines I've tested the script suggested in the tutorial linked above, and got differents results:

on the pc, the application opens spotify at the right page.
on the laptop, the application doesn't do anything

Note, though, that the script is ok, for if I enter '/home/username/spotify.sh spotifyaddress' in a terminal, the command results in opening spotify at the correct page.

So, on my laptop I decided to follow this other tutorial
[http://www.spotify.com/uk/help/faq/wine/#opening-spotify-links-in-web-browsers](http://www.spotify.com/uk/help/faq/wine/#opening-spotify-links-in-web-browsers)
the result was the same, BUT I was surprised to discovered that this second strategy worked fine with seamonkey which is also installed on my laptop. In this case the application not only opens spotify, it also opens the correct link in spotify, even if you still need to click to play the song, just like in the pc case. 


any ideas why this is so? thanks a lot for your replies.

---

### Post by lunalui on 2010-10-05
OK, just in case other people are interested, I've solved my problem by completely removing firefox (3.6.10), and then installing it... Note that reinsallation alone is not sufficient to fix the problem. It looks like this was due to some incompatibility with older versions of firefox which wasn't fixed by upgrading.
:)

---

