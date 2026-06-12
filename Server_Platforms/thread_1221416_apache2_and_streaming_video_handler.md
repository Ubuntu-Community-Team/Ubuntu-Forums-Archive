---
title: "apache2 and streaming video handler"
date: 2009-07-23
forum: Server Platforms
---

### Post by jasonbrisbane on 2009-07-23
Hello,

I have been running my own apache2 website with two domains and various directories, php with a wiki, etc and all is working fine.

i am trying to find a module to add to apache2 to allow streaming video.

Apparently there are several ways to do this:
1) a php handler, rather slow but works fine (dont knwo where this is or what it is called)
2) apache mod - mod_flvx, written by Paul Querna.
3) run vlc viewer on server and open port on router
4) flowplayer - never heard of this and dont want to use more programs, especially as I want to keep the server LAMP only - its a slow machine....

The mod (for #2) is a c file and requires apxs, which I have not been able to find. I think it may be supposed to be part of apache??

I run apache2 from ubuntu deb sources and dont compile anything  in order to maintain ubuntu deb compatibility (had issues with being unable to upgrade when manually patching in the past).

My questions are:

a) is there a streaming flash video handler in apache?
b) is it available from an apache2 source and where is this?
c) do I have to manually compile this as the only way to get apache to feed a flv file to a website?


PS: I am aware of having to modify the conf files for AddHandler and maxConnections (re streaming connection issues).

PSS: I am using EmbedVideo in my wiki and can see youtube videos and since they are all hosted by [http://www.youtube.com/v/xxxxxxxx](http://www.youtube.com/v/xxxxxxxx) then I am trying to set up, basically, the same scenario (videos of my daughter for family, as well as future family events, etc) on my website (darkeen.homelinux.com/videos/xxxxx.flv).

d) should I just update to 9.04 JJ? I currently run apache 2.2 on 7.04 Desktop Ubuntu. As such the option to upgrade or download 7.04 sources is out as they are no longer hosted and cant be downloaded through the Deb manager. Is there a seperate deb file for the apache2 mod for flv?

e) will the server ubuntu make the server run faster?

f) does the server ubuntu have x windows by default? I remote vnc into the server from my laptop(running 8.04) to do all the work so I can shove the server into a corner of the dining room without a monitor or keyboard.....


Thanks in advance to all my (relativly) newby questions...

---

### Post by jasonbrisbane on 2009-07-28
Hi All,

Just to advise I have got it working now.

I upgraded gutsy Gibbons using:
$ sudo  do-release-update
$ sudo aptitude install lighttpd lighttpd-doc
$ sudo gedit /etc/lighttpd/lighttpd.conf

and:
Changed port from 80 to 3000 to stop a conflict with apache.
Added host rule for my domain.
Removed # from module mod_flv_streaming and added module mod_secdownload.
Changed the documentroot to the correct folder for the videos.

INserted the correct code into Embedvideo.php for the wiki extension.
Ensured the flv file was on the website.
Downlaoded a swf player for the videos (I used jw flv player)
$ sudo /etc/init.d/lighttpd start

and Viola, I can now play videos for my own website inside my wiki page!

JW flv player also shows you how you can add skins to the player so you can change the look of it... Not a bad option really.

So now, effectively, I have my own "Youtube" website!

I hope this assist others who want to do the same thing...

---

