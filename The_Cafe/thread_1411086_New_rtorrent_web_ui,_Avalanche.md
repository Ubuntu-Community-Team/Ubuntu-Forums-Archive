---
title: "New rtorrent web ui, Avalanche"
date: 2010-02-19
forum: The Cafe
---

### Post by Keithamus on 2010-02-19
Hey guys!

I've just released my brand new rtorrent client, called Avalanche. It is loosely based off of Clutch and offers powerful, easy to use features.

So, all you rtorrent users out there, why not give it a whirl? I will be actively developing it for a long time coming. I've developed it because I've been dissatisfied with other torrent clients I've used (rutorrent, rtgui, wtorrent, torrentflux - sorry guys! Don't take offence), and I want you guys to help me make it the best rtorrent client out there!

If you want to download it, go to [http://bit.ly/AvalancheRT](http://bit.ly/AvalancheRT) and download the beta. It should be easy enough to see how to set it up, but just edit the settings.php and give it a try.

Thanks!

---

### Post by markp1989 on 2010-02-19
sounds decent :) will give it a go on my rtorrent machine later on :)

edit: looked at the screnies, looks goood :D  i havnt got a web ui installed on my rtorrent, never had any luck getting the other webuis working, hoping i have better luck with this one :D

---

### Post by zekopeko on 2010-02-19
No screenshots. Unacceptable. Show us the shiny!!! :P

---

### Post by Keithamus on 2010-02-19
Sorry, how dare I!

It is very beta at the mo, (while functional, has a few niggling bugs), but by the time it gets to 0.9 final I will have screenshots, screencasts, instructions and everything on the google code website, but lazyness is getting the better of me right now.

*EDIT* Don't know if the screenshot does it much justice, but the feel is very fluid. Alot of things are instant (because I carefully balanced queries to rtorrent with just working stuff out in js client side) and shortcuts and "operating system behaviours" make it feel natural. I havent used a desktop torrent client in a long while but it feels very similar to what I remember. I want to make sure it keeps that desktop app feel, an area which I feel alot of the rtorrent clients lack right now. Also, being a designer, to me, looks are as important as code *END EDIT*

Alas, here you go, hopefully it quenches your thirst:

---

### Post by Keithamus on 2010-02-20
Either of you tried it out yet? I'd like to get some more opinions/ideas on it.

If either of you did try it, what did you like? What bugged you? What do you wish you could do, but couldn't?

---

### Post by Dj Melik on 2010-02-20
I installed it, although I can't connect to my rtorrent.

I have all the required packages installed and configured it.

---

### Post by Keithamus on 2010-02-20
Sorry for that. Proper debugging is one of the most lacking features of this. For the time being the best way to debug is adding "remote.php?action=retrieve" to the url, so for example if the url is:

[http://192.168.1.1/avalanche](http://192.168.1.1/avalanche)

Then the new URL to look at would be:

[http://192.168.1.1/avalanche/remote.php?action=retrieve](http://192.168.1.1/avalanche/remote.php?action=retrieve)

If you paste the results here (or PM me if you'd prefer) I can talk you through the issues and how to fix them. Also if you include whether you use a user name/password and what type (digest or basic) you use, that would help loads.

---

### Post by markp1989 on 2010-02-20
> **Keithamus said:**
> 
[http://192.168.1.1/avalanche/remote.php?action=retrieve](http://192.168.1.1/avalanche/remote.php?action=retrieve)

If you paste the results here (or PM me if you'd prefer) I can talk you through the issues and how to fix them. Also if you include whether you use a user name/password and what type (digest or basic) you use, that would help loads.

right now i get "403 - Forbidden" with action=retrieve , when i go to ip/avalanche i see the interface (lookin good btw), but am also having problems connecting to my rtorrent.  i think this might be more a problem with me and lighttpd then it is with avalanche,

---

### Post by stmiller on 2010-02-20
Somewhat related - for a web torrent downloader, check out [http://www.torrentflux.com/](http://www.torrentflux.com/)

Though I think it is based on Bitornado.

---

### Post by Noah0504 on 2010-02-21
> **Keithamus said:**
> Hey guys!

I've just released my brand new rtorrent client, called Avalanche. It is loosely based off of Clutch and offers powerful, easy to use features.

So, all you rtorrent users out there, why not give it a whirl? I will be actively developing it for a long time coming. I've developed it because I've been dissatisfied with other torrent clients I've used (rutorrent, rtgui, wtorrent, torrentflux - sorry guys! Don't take offence), and I want you guys to help me make it the best rtorrent client out there!

If you want to download it, go to [http://bit.ly/AvalancheRT](http://bit.ly/AvalancheRT) and download the beta. It should be easy enough to see how to set it up, but just edit the settings.php and give it a try.

Thanks!

Want to give a quick little how-to for folks like me?

---

### Post by Dj Melik on 2010-02-23
```
[Tue Feb 23 17:13:33 2010] [error] [client 127.0.0.1] PHP Notice:  Undefined index: set_auth_digest in /srv/http/torrent/lib/rtorrent.php on line 39, referer: http://127.0.0.1/torrent/
[Tue Feb 23 17:13:33 2010] [error] [client 127.0.0.1] PHP Notice:  Undefined index: set_auth_digest in /srv/http/torrent/lib/rtorrent.php on line 39, referer: http://127.0.0.1/torrent/
[Tue Feb 23 17:13:33 2010] [error] [client 127.0.0.1] PHP Fatal error:  Call to undefined function json_encode() in /srv/http/torrent/remote.php on line 159, referer: http://127.0.0.1/torrent/
[Tue Feb 23 17:13:34 2010] [error] [client 127.0.0.1] PHP Notice:  Undefined index: set_auth_digest in /srv/http/torrent/lib/rtorrent.php on line 39, referer: http://127.0.0.1/torrent/
[Tue Feb 23 17:13:34 2010] [error] [client 127.0.0.1] PHP Fatal error:  Call to undefined function json_encode() in /srv/http/torrent/remote.php on line 159, referer: http://127.0.0.1/torrent/
[Tue Feb 23 17:13:34 2010] [error] [client 127.0.0.1] PHP Fatal error:  Call to undefined function json_encode() in /srv/http/torrent/remote.php on line 159, referer: http://127.0.0.1/torrent/
[Tue Feb 23 17:13:34 2010] [error] [client 127.0.0.1] File does not exist: /srv/http/torrent/media/favicon.ico

```

---

### Post by devinw on 2010-02-23
Looks really slick. I look forward to checking it out.

---

### Post by Keithamus on 2010-02-27
Hey guys, just wanted to say I've updated Avalanche to Beta 2. It fixes a few bugs and more importantly sets up error dialogues so you can see why its breaking.

On Monday (GMT) I'm gonna put some video tutorials up on how to set it up (from scratch using Ubuntu server edition) and also a quick guide on how to use it, some of its killer features etc.

So Noah0504 & others, if you could please hold out until Monday I'll hopefully have some good stuff to show you so you can get it running.

And to others, please update, if you want to, you can use SVN as the trunk is as stable as the releases.

Finally, DJ Melik, you need to have PHP version 5.2.0 or above. Do you know which version you have? Try doing:

```

php --version

```

If its not 5.2.0 then it wont work I'm afraid.

---

### Post by Aurelius on 2010-02-27
I'm looking forward to the tutorials - it looks like a nice front-end.

---

### Post by Noah0504 on 2010-02-27
I too am ready for a little how to.  I'd love to get this up and running!

---

### Post by Dj Melik on 2010-02-28
> **Keithamus said:**
> Hey guys, just wanted to say I've updated Avalanche to Beta 2. It fixes a few bugs and more importantly sets up error dialogues so you can see why its breaking.

On Monday (GMT) I'm gonna put some video tutorials up on how to set it up (from scratch using Ubuntu server edition) and also a quick guide on how to use it, some of its killer features etc.

So Noah0504 & others, if you could please hold out until Monday I'll hopefully have some good stuff to show you so you can get it running.

And to others, please update, if you want to, you can use SVN as the trunk is as stable as the releases.

Finally, DJ Melik, you need to have PHP version 5.2.0 or above. Do you know which version you have? Try doing:

```

php --version

```

If its not 5.2.0 then it wont work I'm afraid.
```
[melik@augustina ~]$ php --version
PHP 5.3.1 with Suhosin-Patch (cli) (built: Feb 20 2010 04:00:08) 
Copyright (c) 1997-2009 The PHP Group
Zend Engine v2.3.0, Copyright (c) 1998-2009 Zend Technologies
```

I definitely have the latest PHP, the thing is I use Arch Linux.. so it comes un-configured. Do you know what PHP modules Avalanche uses; so that I may enable them.

Edit: Figured out the problem, took a look at the code and learned that it uses json.. so I went to edit my php.ini file and saw that json.so wasn't enabled:

```
extension=json.so
``` 

So i enabled it, and it works :D

Thanks for the great code.

---

### Post by cedeel on 2010-03-01
Any pointers on how to make this work with SSL?

---

### Post by Noah0504 on 2010-03-01
> **Keithamus said:**
> On Monday (GMT) I'm gonna put some video tutorials up on how to set it up (from scratch using Ubuntu server edition) and also a quick guide on how to use it, some of its killer features etc.

So Noah0504 & others, if you could please hold out until Monday I'll hopefully have some good stuff to show you so you can get it running.


I'm still waiting.  :P

---

### Post by Keithamus on 2010-03-02
Sorry, I am just uploading the videos now, turns out I'm not very good at screencasting...

I cut two minutes of me saying "uhhhmmm" out of the preview video (the video was only 7 minutes long) so hopefully you can start to understand why they're a day late.

Anyway, the preview of Avalanche is uploading to youtube, and Im editing together the tutorial on how to install now, so you only have to wait a very short time longer!

Sorry for not putting them up when I promised :'(

*EDIT 1: Video preview is up: [http://www.youtube.com/watch?v=ZeeCWv3ajDk](http://www.youtube.com/watch?v=ZeeCWv3ajDk) don't forget to switch to HD :D

---

### Post by Noah0504 on 2010-03-02
> **Keithamus said:**
> Sorry, I am just uploading the videos now, turns out I'm not very good at screencasting...

I cut two minutes of me saying "uhhhmmm" out of the preview video (the video was only 7 minutes long) so hopefully you can start to understand why they're a day late.

Anyway, the preview of Avalanche is uploading to youtube, and Im editing together the tutorial on how to install now, so you only have to wait a very short time longer!

Sorry for not putting them up when I promised :'(

No worries!  Better late than never, right?  :P  I'll check them out as soon as they are uploaded.

---

### Post by Keithamus on 2010-03-02
Right! Hot of the... tubes!

Preview Video for Avalanche RT, showing its features & how it works:

[http://www.youtube.com/watch?v=bmK8sHZV5lg](http://www.youtube.com/watch?v=bmK8sHZV5lg)

Instructional video on how to install Avalanche and rTorrent, including instructions for Apache/PHP:

[http://www.youtube.com/watch?v=qSUwEe__pik](http://www.youtube.com/watch?v=qSUwEe__pik) Part 1
[http://www.youtube.com/watch?v=H7Br9mc7rF4](http://www.youtube.com/watch?v=H7Br9mc7rF4) Part 2


Adding captions to all videos, as I realise my voice lacks in both audibility and pleasantry.

---

### Post by Aurelius on 2010-03-02
> **Keithamus said:**
> Right! Hot of the... tubes!

Preview Video for Avalanche RT, showing its features & how it works:



Very nice guide! Thanks.

---

### Post by Noah0504 on 2010-03-03
Great videos, however, I still can't get it to work.  I'm trying to customize it to get it to run out of /avalanche on my web server... It's not going so well.  I have a feeling I'm just doing something stupid.  I'm still piddling around with it.

EDIT:

It helps to have php5-curl installed.  :)

---

### Post by Keithamus on 2010-03-03
Hey Noah0504 did you manage to get it to work? If not PM me and we can discuss it privately if you'd like.

---

### Post by Noah0504 on 2010-03-03
> **Keithamus said:**
> Hey Noah0504 did you manage to get it to work? If not PM me and we can discuss it privately if you'd like.

Yeah, I finally did!  I'm liking it very much, so don't run away on developing.  :P

---

### Post by Keithamus on 2010-03-03
Hah! I definitely wont run away. I use it myself daily. Glad to see you like it. Found any bugs yet? I'd love you to become an active user of the issue tracker:

[http://code.google.com/p/avalanche-rt/issues/list](http://code.google.com/p/avalanche-rt/issues/list)

---

### Post by Noah0504 on 2010-03-03
> **Keithamus said:**
> Hah! I definitely wont run away. I use it myself daily. Glad to see you like it. Found any bugs yet? I'd love you to become an active user of the issue tracker:

[http://code.google.com/p/avalanche-rt/issues/list](http://code.google.com/p/avalanche-rt/issues/list)

Yeah, I love rTorrent, but always would find myself using Transmission on my server for the web interface.  The way Transmission runs though has a few of its own issues.

The only bug I have noticed so far is the "Effect on Disk" section in the details.  It doesn't seem to calculate correctly.  I have 3TB in my server and it tries to tell me I have 1.68GB free.  :P  That's obviously not the case.

Also, do you have Google Talk or Jabber account?  Hit me up sometime: [email]noah.duffy@thenomar.com[/email]

---

### Post by cedeel on 2010-03-03
Please, how do I get this to work using ssl? I've been through the source, but can't find where exactly the change must be made. Additionally, is it possible to make it use a local socket?

---

### Post by Keithamus on 2010-03-04
> **cedeel said:**
> Please, how do I get this to work using ssl? I've been through the source, but can't find where exactly the change must be made.

I don't have enough knowledge of SSL to give you a quick and easy answer. If you want to, I would be more than happy to discuss this with you and get it working, check your PM's for more.


> **cedeel said:**
> Additionally, is it possible to make it use a local socket?

Short Answer: Not with Apache

Long Answer: rtorrent can easily set up a local socket. Just use "scgi_local /path/to/socket" (I think). Unfortunately, Apache's Mod_SCGI (to the best of my knowledge) cannot bind itself to a local socket. I also am quite sure that Lighttp **can** do this, but I am certainly not experienced enough with Lighttp to help you with this. However, in saying all of that, binding rtorrent to a local, blocked port, and securing your apache scgi binding *should* be sufficient security. If you find out how do it in Apache, please tell me as it is something I definitely have been looking for.

---

### Post by cedeel on 2010-03-04
Short Answer: Not with Apache

Long Answer: rtorrent can easily set up a local socket. Just use "scgi_local /path/to/socket" (I think). Unfortunately, Apache's Mod_SCGI (to the best of my knowledge) cannot bind itself to a local socket. I also am quite sure that Lighttp **can** do this, but I am certainly not experienced enough with Lighttp to help you with this. However, in saying all of that, binding rtorrent to a local, blocked port, and securing your apache scgi binding *should* be sufficient security. If you find out how do it in Apache, please tell me as it is something I definitely have been looking for.[/QUOTE]

I'm using Lighttpd for this, so Apache quirks don't really interest me. However, it strikes me as odd that any server shouldn't be able to do this, as the socket basically is a local file which the server should have no problem whatsoever reading.

---

### Post by Keithamus on 2010-03-06
With the help of cedeel, Avalanche has support for SSL, check out the new beta 3, which also includes a few tweaks to the details pane.

SVN users should update - the SVN currently matches beta 3. If you're interested in testing the new features before they go into the released version, I encourage you to use SVN. It is quite stable, and any breakages don't stay broken for long - I make sure to test my changes before I commit - so you can be quite sure that its not going to delete all your torrents or something.

---

### Post by Noah0504 on 2010-03-06
I just upgrade by just deleting all of the files in the Avalanche directory and extracting the new download there.  Is there an easier way?  I'm sure I did that the hard way!

---

### Post by EarthMind on 2010-03-06
This looks great. I was wanting to create an alternative for torrenflux myself but it seems htat I don't have to anymore.

Much appreciated :)

---

### Post by Keithamus on 2010-03-09
@EarthMind, Avalanche can always use more developers. I'm the only one right now, but I want to really push this forward so if you want to join in development, and you see any areas you want to improve, I am more than willing to except patches at [http://code.google.com/p/avalanche-rt/](http://code.google.com/p/avalanche-rt/). Of course full attribution will go to you if you submit any work. Code is (now) under GPLv3.

@Everyone I've updated Avalanche to 0.9 beta 4. This one is pretty close to release, if no bugs are reported it'll probably become 0.9 stable. 

Also, to stay updated with Avalanche releases, you can follow [@avalanchert on twitter](http://www.twitter.com/avalanchert)

---

### Post by EarthMind on 2010-03-11
I'll have to give it a try first ;).

Have you tested compaibility with torrentflux? I hope it'll continue downloading/seeding the torrents correctly.

---

### Post by Keithamus on 2010-03-11
This is a replacement for torrentflux, that is, runs completely with or without torrentflux. It should be compatible with every client and vice versa, in the sense that they don't acknowledge one another.

Hope this answers your question.

---

### Post by PurposeOfReason on 2010-03-11
It takes up far too much space to show one torrent thus rutorrent will remain the king IMO.

---

### Post by Keithamus on 2010-03-11
I am actually working on a few different views for the torrent list, including a tabulated view, much like rutorrent. This will be included in 1.0 release which by the look of the current development speed will be finished within a month or two!

---

### Post by Keithamus on 2010-03-21
Just to let everyone know the latest SVN version checked in today has support for many of the things people have been asking for. Here is a small list of changes between the latest beta release (0.9b4) and the latest svn:

[LIST]
[*]Translations available in English & Japanese (Norwegian coming soon)
[*]Resiable/toggleable details pane.
[*]About dialogue, with update checking
[*]Ability to zoom in/out of the torrent list for large, small and tabulated (single row) versions of the list - on the smallest version I can see over 30 torrents (1680x1050 res), the largest: 11.
[*]Can open torrent files as well as torrents by URL
[*]Details pane works much better, especially files/trackers tabs.
[/LIST]

I want to test this version a bit, get it polished enough & add a few more translations and then it'll be released as 0.9RC1 or Final on **Tuesday Morning (GMT)** depending on how finished it is.

Also this is a good time to say - anyone who wants to translate for Avalanche please help out! Anyone who supplies a translation will get **full credit in the about dialogue, and can optionally link their names to their homepage if they'd like.**

---

### Post by PurposeOfReason on 2010-03-22
Trying it out now. Works very good. 

EDIT - Found how to sort.

---

### Post by markp1989 on 2010-03-22
i tried setting up as described on your site.

im getting this error when connection to the webui.
```

Error parsing remote.php

Bad Json

{"error":"Didn't receive 200 OK from remote server. (HTTP\/1.1 404 Not Found)"}
```

thanks for any help, mark

---

### Post by Keithamus on 2010-03-22
Likely Apache can't read the remote.php file - perhaps you need to chmod it?

```

sudo chmod 755 *.php -R & chown www-data:www-data *.php -R

```

If that doesn't work then take a look at your Apache error log:

```

tail -f -n100 /var/log/apache2/error.log

```

---

### Post by Keithamus on 2010-03-28
Hi all.

I missed the update I promised on Tuesday - I had a lot of job interviews this week and so it has been difficult to get Avalanche to the quality I wanted it to be for RC1. 

However, I've released RC1 just now, so you can get it here:

[http://code.google.com/p/avalanche-rt/downloads/detail?name=avalanche_rt_0_9_RC1.tar.gz](http://code.google.com/p/avalanche-rt/downloads/detail?name=avalanche_rt_0_9_RC1.tar.gz)

SVN users can just "svn up", as this is r46!

If you already have Avalanche (and don't use SVN) then it is recommended to delete your old avalanche install as a lot of files have changed.

I won't promise a release date for the next release, but I can promise a preferences window is in the works. If you want something to be added in Avalanche **please** put it in the issue tracker at [http://code.google.com/p/avalanche-rt/issues/list](http://code.google.com/p/avalanche-rt/issues/list) and I'll do my best to add it. 

Hope you enjoy RC1. If you have any bugs, please report them!

---

### Post by EarthMind on 2010-05-10
Hey Keithamus. I noticed that you use the same webUI as Transmission. Does yours have any added features?

I could see a few more features (e.g. configuration options) and currently don't have the time to do it myself.

---

### Post by Keithamus on 2010-05-11
EarthMind, while my webui **looks** like the Transmission webui, it is meant for rTorrent - which means it behaves very differently to Transmission, and is mostly as strong as your rtorrent config is. This is designed for servers - where X isn't available to run clients like Transmission.

In terms of extra features - well, I'm not sure. I strive to make Avalanche as strong as a desktop client, so you can do the majority of things you'd want from clients such as Transmission or Deluge, anything that is missing, tell me and I'll add it.

Hope that answers your question.

---

### Post by EarthMind on 2010-05-11
The webui of Transmission lacks extensive configuration support which is quite disappointing because then I have to log into SSH every time. I'm curious to try out your rTorrent port :).

I was also interested in adding a feature to Avalanche but haven't had the chance yet, not even the chance to try it out. So that'll be for later and I'm not going to give away anything.

Just a note: Transmission also runs perfectly on servers without X using a high performing daemon and with a CLI or web interface.

---

### Post by IndigoHaze on 2010-05-12
Got it installed and running, must say it looks smooth.

What's the point of the Labels? I'm not seeing that they're searchable or selectable at all, and if I fail to give one when I start the torrent there appears to be no way to set one after the torrent is loaded.

One slight issue I'm seeing with the RC1 as well - When I load a torrent from URL, it dumps it into rtorrent, starts it if I selected the check box, but the web interface just sits there grinding away until it times out. I then have to request a full refresh of the screen for the torrent to show up. I'm watching rtorrent via a shell and I see the torrent download, process in and start up, it's just that the web interface doesn't seem to acknowledge that everything is working.  10.04LTS, KUbuntu on a Phenom 9850 (Quad Core AMD 2.5ghz) 8gb RAM...

---

### Post by IndigoHaze on 2010-05-12
And now that I'm using it local instead of across a SSH tunnel, it doesn't want to load torrents at all. If I load via URL it just times out and never loads. If I download the torrent and attempt to load via File it claims to load it in the UI, but rtorrent claims it's not a vaild file. However if I go to rtorrent directly and load the exact same file, it loads without issue.

---

### Post by doombar on 2010-06-05
I too had the bad json error about remote.php, until I did chmod/chown on /var/www.

Now I've got that fixed, it's reading the rTorrent stuff fine, but it doesn't pick up any changes until I manually refresh the page. So if I load it up, then change the speed cap through SSH, the new cap will only be shown in avalanche when I reload it.
Also, it seems to be somewhat a one-way street. Data can clearly be read, but torrents aren't loading. I get a confirmation saying it's loaded, but looking at rtorrent in SSH shows that it doesn't actually get loaded at all.

Has anyone else had similar problems, or maybe know of a possible solution (or just anything worth trying that could help)? Like another person in this thread, I've been tempted to code my own web ui, but could never be bothered in the end. This is the best looking interface I've seen so far, now all I gotta do is work out what's going wrong behind the scenes :P

---

