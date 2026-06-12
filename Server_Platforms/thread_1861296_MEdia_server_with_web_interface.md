---
title: "MEdia server with web interface"
date: 2011-10-15
forum: Server Platforms
---

### Post by monkeypigs on 2011-10-15
Hi, 

My Ubuntu server (Oneric) box is sat sitting vastly under utilised. It's currently running as an FTP server and also has DNSMasq installed, so I thought I'd go about setting up a media server, but have hit so many brick walls it's unreal!

[LIST]
[*]I've used firefly in the past, but mt-daapd is no longer maintained
[*]I tried Ampache but could not for love nor money to get it to stream a playlist (It would create a playlist and add to it, but you can't add to a currently playing list on the fly, or I'm doing something very wrong!)
[*]Thought I'd have a crack at forked-mtdaapd but that lacks a web interface.
[*]Jinzora looked good but their site never seems to load from here. 
[*]VLC is a no go as it's Ubuntu server so no GUI
[/LIST]

So, the question is, what else is there out there?

I need something that will ideally stream music and movies (music is more important though) and will let me add to a playlist whilst it's currently playing. 

A web interface for my family is a must. 

For the time being, it will be streaming to other PCs but other devices may come along at some point. 

Any suggestions are more than welcome!
Iain

---

### Post by bcboybuzz on 2011-10-15
Jinzora is my current recommendation, although I haven't used it too much. It seems that it can stream video as well, but I'm only using it for audio at the moment. Not only will it stream to your default media player, it can also use an embedded player, but that's farther than I had to go in the tutorial. My main computer has automatic 5.1 upmixing that wouldn't be available with embedding. Anyway, I just put Jinzora on my 11.04 server last night. Here's the sourceforge link:
 
[http://sourceforge.net/projects/jinzora/](http://sourceforge.net/projects/jinzora/)
 
and heres the steps i used to install it:
 
[http://maketecheasier.com/how-to-install-and-setup-jinzora-media-server-in-ubuntu/2008/08/25](http://maketecheasier.com/how-to-install-and-setup-jinzora-media-server-in-ubuntu/2008/08/25)
 
Don't know whether you'll have the same problem, but I noticed that the install pages seem to take a long frickin time to load. They do eventually load though, and the main interface loaded just fine. Also, with jinzora3, for some reason, the file jinzora.cfg.php got renamed to jinzora_cfg.php in step 8 so i had to save it and manually add it to the server. 
 
Hope that helps your Jinzora install :)
 
BC
[http://bcboy.dyndns.org/](http://bcboy.dyndns.org/)

---

### Post by monkeypigs on 2011-10-15
Didn't think about searching sourceforge for it! Doh!

I've currently just found [http://www.subsonic.org/pages/index.jsp](http://www.subsonic.org/pages/index.jsp) and am very impressed with it especially the way it handles movies

Do you feel Jinzora is better, or just different? If it offers a lot over Subsonic I'll give it a whirl tomorrows¬!

Thanks
Iain

---

### Post by monkeypigs on 2011-10-15
Hmmmm..... trying to install Jinzora, and it just refuses to read the index.php after I've run the config.sh

Placed in the root of my www directory just get a 404 each time I try to load it.....

---

### Post by bcboybuzz on 2011-10-15
> **monkeypigs said:**
> Didn't think about searching sourceforge for it! Doh!
 
I've currently just found [http://www.subsonic.org/pages/index.jsp](http://www.subsonic.org/pages/index.jsp) and am very impressed with it especially the way it handles movies
 
Do you feel Jinzora is better, or just different? If it offers a lot over Subsonic I'll give it a whirl tomorrows¬!
 
Thanks
Iain
 
Unknown. I've only just built my server, and have only tried Jinzora and Ampache (ampache is too limited for my happiness). I have had some difficulties with Jinzora, so I'll be checking out subsonic tonight. Thanks for the tip.
 
EDIT: First impressions, I like subsonic a lot more than Jinzora...might be making a change to my server :)
 
 
 
> **monkeypigs said:**
> Hmmmm..... trying to install Jinzora, and it just refuses to read the index.php after I've run the config.sh
 
Placed in the root of my www directory just get a 404 each time I try to load it.....
 
I have a website in place already ([http://bcboy.dyndns.org/](http://bcboy.dyndns.org/) shameless plug ftw) so I installed to /var/www/jinzora. As I mentioned, it took an exceptionally long time to load index.php the first time, several minutes in fact. Perhaps your browser is timing it out?
 
BC

---

### Post by monkeypigs on 2011-10-16
I've had a look at some screenshots and Jinzora is out of the question now!

One thing I did find with Subsonic is that it struggles with some video files, audio is out of sync. 
This is down to the default config only having 100Mb RAM usage. 
I've got 1.7Gb on my server and it's never used more than 400 Mb RAM before I installed Subsonic so I've upped it's memory to 768Mb RAM and it plays video real smooth now.

```
pico /etc/default/subsonic
```

Change

```
SUBSONIC_ARGS="--max-memory=100"
```

to
```
SUBSONIC_ARGS="--max-memory=768"
```

and restart subsonic

```
/etc/init.d/subsonic restart
```

---

### Post by bcboybuzz on 2011-10-16
> **monkeypigs said:**
> I've had a look at some screenshots and Jinzora is out of the question now!
 
One thing I did find with Subsonic is that it struggles with some video files, audio is out of sync. 
This is down to the default config only having 100Mb RAM usage. 
I've got 1.7Gb on my server and it's never used more than 400 Mb RAM before I installed Subsonic so I've upped it's memory to 768Mb RAM and it plays video real smooth now.
 
```
pico /etc/default/subsonic
```
 
Change
 
```
SUBSONIC_ARGS="--max-memory=100"
```
 
to
```
SUBSONIC_ARGS="--max-memory=768"
```
 
and restart subsonic
 
```
/etc/init.d/subsonic restart
```
 
Yep, after taking a look at subsonic, I switched too. Jinzora is off my server. I'm not using it for video streaming, but I changed my config to 128MB (my server is really limited in RAM, only 512MB, with 2GB swap). I've not yet noticed any trouble with the stream.

---

### Post by mashedbear on 2011-10-23
Hi - has mt-daapd been removed by 11.10 upgrade process? 

I've had mt-daapd running quite happily since Ubuntu 8.04 streaming music to two roku network music players. After upgrading to 11.10 last night mt-daapd has stopped working..last message in the log below 

> 2011-10-22 15:29:26 (83b73a30): Updating playlists
2011-10-22 15:29:26 (83b73a30): Scanned 2564 songs (was 2564) in 1 seconds
2011-10-23 00:40:39 (83b73a30): Got shutdown signal.
2011-10-23 00:40:39 (83b73a30): Stopping gracefully
2011-10-23 00:40:39 (83b73a30): Closing database
2011-10-23 00:40:39 (83b73a30): Done!

Can this be true - has mt-daapd been removed? 

Looking at the shell script below - should there be a daemon in /usr/sbin/mt-daapd? (I've looked and there isn't now!) It would be great to get this old friend working again.  

```
#!/bin/sh

### BEGIN INIT INFO
# Provides:          mt-daapd
# Required-Start:    $local_fs $remote_fs $network $time avahi
# Required-Stop:     $local_fs $remote_fs $network $time
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Multithreaded DAAP music server 
# Description:       mt-daapd, a.k.a. Firefly Media Server, is what
#                    most people will understand to be an iTunes share
#                    server. It uses the DAAP protocol, as iTunes does,
#                    and supports streaming MP3 and AAC natively. It can
#                    make use of a number of conversion methods to expose
#                    Ogg and FLAC files too.
### END INIT INFO

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/sbin/mt-daapd
DAEMON_OPTS=-m
NAME=mt-daapd
DESC=mt-daapd

test -x $DAEMON || exit 0

# Include mt-daapd defaults if available
if [ -f /etc/default/mt-daapd ] ; then
	. /etc/default/mt-daapd
fi

set -e

stopd() {
	echo -n "Stopping $DESC: "
	start-stop-daemon --stop --quiet --pidfile /var/run/$NAME.pid \
	    --signal 2 --exec $DAEMON --oknodo
	echo "$NAME."
	counter=0
	seen=0
	while pidof mt-daapd >/dev/null && [ $counter -lt 15 ]; do
		if [ $seen -eq 0 ]; then
			echo -n "Waiting for mt-daapd to terminate..."
			seen=1
		fi
		
		counter=$(($counter + 1))
		echo -n "."
		sleep 1
	done
	echo "OK, all clear."
}

startd() {
	echo -n "Starting $DESC: "
	start-stop-daemon --start --quiet -m --pidfile /var/run/$NAME.pid \
		--oknodo --exec $DAEMON -- $DAEMON_OPTS 2>/dev/null
	echo "$NAME."
}

case "$1" in
  start)
	startd
	;;
  stop)
	stopd
	;;
  restart|force-reload)
	stopd
	startd
	;;
  *)
	N=/etc/init.d/$NAME
	echo "Usage: $N {start|stop|restart|force-reload}" >&2
	exit 1
	;;
esac

exit 0
```


I can still see the project on sourcefourge [http://sourceforge.net/projects/mt-daapd/files/mt-daapd/0.2.4.2/](http://sourceforge.net/projects/mt-daapd/files/mt-daapd/0.2.4.2/) 

Can I reinstall it from this? If so - how? Are there other dependencies I need to check - like avahi - would 11.10 have removed this aswell?

---

### Post by monkeypigs on 2011-10-24
I've no idea about it being removed by the upgrade process. 
I was running the 11.10 beta for quite a while and mt-daap was never availible. 
mt-daapd was replaced by forked-daapd which is basically the same minus the web interface. You can find further info specific to forked-daapd on [http://ubuntuforums.org/showthread.php?t=1354196](http://ubuntuforums.org/showthread.php?t=1354196)

Without the user web interface it was of no use to me, hence my use of Subsonic and I'd urge you to have a look at that as well. It's free but you have to donate 10 euro to continue using advanced features (eg Video streaming) after the first month - well worth the price!

Hope that helps!

---

### Post by mashedbear on 2011-10-29
Thanks monkeypigs. Am trying to get forked-daapd running. Not there yet - see [http://ubuntuforums.org/showthread.php?p=11405387#post11405387](http://ubuntuforums.org/showthread.php?p=11405387#post11405387)

I think I need a daap server with RSP support for Roku's SoundBridge devices. Can see that forked-daapd has this [http://www.jblache.org/projects/daapd/](http://www.jblache.org/projects/daapd/)

I don't think Subsonic does. Do you know?

cheers

---

### Post by kleverbear on 2011-10-30
Does sub sonic show up in itunes like firefly by chance? Im trying to get a daap server on 10.04 headless server.

NVM 

"Works with any network-enabled media player, such as Winamp, iTunes, XMMS, VLC, MusicMatch and Windows Media Player. Also includes an embedded Flash player."

---

### Post by cj13579 on 2011-10-31
> **monkeypigs said:**
> Hi, 
but mt-daapd is no longer maintained


It is still amazing though and available through the Ubuntu repos.

I have tried Subsonic and Jinzora and I like them both. I am currently using Jinzora but that is only because I had been using it for ages and I know how use to it (I also don't like change :)). Subsonic is very pretty and very nice though. I think it's embedded player is much better than Jinzora's.

---

### Post by kleverbear on 2011-11-01
Subsonic is way better than mt-daap or firefly, i love the ability to sync to a phone and have your own personal cloud of music. damn glad i found this thread

---

### Post by zim2dive on 2011-11-13
Have also been using mt-daapd for years and am very sad to see it not supported in 11.10.

I've been playing with forked-daapd, but 

a) it doesn't seem to read my iTunes playlists (mt-daapd did)
b) it cuts off maybe every 1.5 songs, log file says "connection failed"

if anyone gets mt-dappd to compile, PLEASE post instructions.

---

### Post by zim2dive on 2011-11-13
> **kleverbear said:**
> Subsonic is way better than mt-daap or firefly, i love the ability to sync to a phone and have your own personal cloud of music. damn glad i found this thread

looking at the subsonic page.. does it

a) serve as a DAAP server?
b) how about DLNA?

thanks,
Mike

---

### Post by monkeypigs on 2011-11-13
Jinzora sorts out DLNA, but I removed that after a day as it's next to useless. 
DAAP is apparently handled already by mediatomb, but I've not had any experience with that aspect of MediaTomb. 

The latest beta version does add lots of new features to Subsonic (For instance it comes ready set up to handle dual core processors) and I've decided that after trying Jinzora and MediaTomb, Subsonic is the clear winner for me!

---

### Post by zim2dive on 2011-11-13
> **monkeypigs said:**
> Jinzora sorts out DLNA, but I removed that after a day as it's next to useless. 
DAAP is apparently handled already by mediatomb, but I've not had any experience with that aspect of MediaTomb. 

The latest beta version does add lots of new features to Subsonic (For instance it comes ready set up to handle dual core processors) and I've decided that after trying Jinzora and MediaTomb, Subsonic is the clear winner for me!

short version is I need a linux equivalent iTunes server.. subsonic definitely looks nice, but doesn't have DAAP server features yet (its apparently on the TODO list, but has been since 2007 :( ).

Not clear to me that mediatomb is a mt-daapd replacement either...

---

### Post by monkeypigs on 2011-11-13
Google is your friend: 
[http://manpages.ubuntu.com/manpages/natty/man1/tangerine.1.html](http://manpages.ubuntu.com/manpages/natty/man1/tangerine.1.html)
[http://embraceubuntu.com/2006/09/22/share-music-in-a-network-using-avahi-daap/](http://embraceubuntu.com/2006/09/22/share-music-in-a-network-using-avahi-daap/)

---

### Post by zim2dive on 2011-11-13
> **monkeypigs said:**
> Google is your friend: 
[http://manpages.ubuntu.com/manpages/natty/man1/tangerine.1.html](http://manpages.ubuntu.com/manpages/natty/man1/tangerine.1.html)
[http://embraceubuntu.com/2006/09/22/share-music-in-a-network-using-avahi-daap/](http://embraceubuntu.com/2006/09/22/share-music-in-a-network-using-avahi-daap/)

I've been thru both of those (and more) years ago.. mt-daapd was by far the most capable.  None of the others will "see" pre-existing ratings (from iTunes), nor the already created playlists.

---

### Post by monkeypigs on 2011-11-13
Well as mt-daapd is now dead in the water it may be time to shift on from iTunes streaming, and switch to something more usable and supported (Sorry if that sounds a little blunt!)

---

### Post by kleverbear on 2011-11-13
> **zim2dive said:**
> looking at the subsonic page.. does it

a) serve as a DAAP server?
b) how about DLNA?

thanks,
Mike

It accutally does show up in itunes similar to Firefly buts not a daap server, as for DLNA im Using [MiniDLNA]("http://blog.homelinux.org/?p=198") IF you decide to use mini let me know i can help u set it up its very simple. FYI get the start up scrip from the [SVN]("http://minidlna.cvs.sourceforge.net/viewvc/minidlna/minidlna/linux/minidlna.init.d.script?view=log") from source forge dotn create your own as it states in the blog. Hopes this helps!

---

### Post by kleverbear on 2011-11-13
> **monkeypigs said:**
> Well as mt-daapd is now dead in the water it may be time to shift on from iTunes streaming, and switch to something more usable and supported (Sorry if that sounds a little blunt!)

I actually let go of iTunes due to Subsonic.

---

### Post by zim2dive on 2011-11-16
> **kleverbear said:**
> I actually let go of iTunes due to Subsonic.

I think I can export the playlists (to m3u)... but only _some_ of the DAAP servers handle ratings.. and I'm not sure why I'm seeing so many disconnects when using forked-daapd (almost every 1.5 songs)

I am playing with twonky right now b/c I just got a Sony network media player ($40 refurb) which is DLNA... once the 30-day trial is up, I may try minidlna.

I'm trying to move away from iTunes.. I'm just trying to KEEP/MIGRATE as much of the DATA as I can (ie. ratings and playlists).

---

### Post by monkeypigs on 2011-11-16
> **kleverbear said:**
> I actually let go of iTunes due to Subsonic.
Yeah, you really don't need both when you've got Subsonic, and there is even an iTunes theme available if you miss the interface of iTunes!

---

### Post by kleverbear on 2011-11-16
> **zim2dive said:**
> I am playing with twonky right now b/c I just got a Sony network media player ($40 refurb) which is DLNA... once the 30-day trial is up, I may try minidlna.

Let me know how it goes with twonky, im looking for something to stream MKV and encode on the fly. i tried twonky a few yrs back im hoping its matured. :popcorn:

---

### Post by zim2dive on 2011-11-17
> **kleverbear said:**
> Let me know how it goes with twonky, im looking for something to stream MKV and encode on the fly. i tried twonky a few yrs back im hoping its matured. :popcorn:

I played with it for 20 minutes.. I was impressed at being able to stream video wirelessly to the box.. I did NOT yet try a full 20G BR rip (with mkv).. will give that a try this weekend.

I've got to figure out the playlist thing too.. looking a list of 3000 songs, isn't the ergonomics I'm looking for :)

Hoping to have time this weekend... life has been busy and not leaving a lot of time for this kind of stuff.

EDIT: I'm not sure I saw Twonky show up in iTunes.. should it? Even tho I'm migrating from Mac being the server to Ubuntu, will still have Mac "clients" wanting to access the "served from linux" material.

---

### Post by Steve54 on 2011-11-17
> **kleverbear said:**
> Let me know how it goes with twonky, im looking for something to stream MKV and encode on the fly. i tried twonky a few yrs back im hoping its matured. :popcorn:
 
Twonky still doesn't transcode on the fly.
 
PS3mediaserver does, that is what I'm currently using on my media server to stream directly to the TV. I've wound back to version 1.3 (current V is 1.5?) as it seems to work better with my Panny TV.

---

### Post by zim2dive on 2011-11-18
> **monkeypigs said:**
> Hi, 

My Ubuntu server (Oneric) box is sat sitting vastly under utilised. It's currently running as an FTP server and also has DNSMasq installed, so I thought I'd go about setting up a media server, but have hit so many brick walls it's unreal!

[LIST]
[*]I've used firefly in the past, but mt-daapd is no longer maintained


I may have gotten it to compile... using the clue I found in: [http://ubuntuforums.org/showthread.php?p=11400708](http://ubuntuforums.org/showthread.php?p=11400708)

I installed all the dependencies (see the Natty package dependency list on launchpad).. and was able to get thru to the last compile which was failing ```
rend-unix.c:116:10: warning: ignoring return value of â, declared with attribute warn_unused_result [-Wunused-result]
gcc  -g -O2  -o mt-daapd -lpthread -lgdbm -lid3tag -lz   main.o uici.o webserver.o configfile.o err.o restart.o daap-proto.o daap.o db-gdbm.o mp3-scanner.o playlist.o lexer.o parser.o strcasestr.o strsep.o redblack.o dynamic-art.o query.o mDNS.o mDNSPosix.o mDNSUNP.o rend-posix.o rend-unix.o      
main.o: In function `start_signal_handler':
/home/zimmy/tmp/mt-daapd-0.2.4.2/src/main.c:679: undefined reference to `pthread_create'
main.o: In function `main':
/home/zimmy/tmp/mt-daapd-0.2.4.2/src/main.c:943: undefined reference to `pthread_kill'
/home/zimmy/tmp/mt-daapd-0.2.4.2/src/main.c:944: undefined reference to `pthread_join'
webserver.o: In function `ws_start':
``` etc...etc.. but I ran the last gcc by hand (with lib listing at EOL)```
gcc  -g -O2  -o mt-daapd -lpthread -lgdbm -lid3tag -lz   main.o uici.o webserver.o configfile.o err.o restart.o daap-proto.o daap.o db-gdbm.o mp3-scanner.o playlist.o lexer.o parser.o strcasestr.o strsep.o redblack.o dynamic-art.o query.o mDNS.o mDNSPosix.o mDNSUNP.o rend-posix.o rend-unix.o  -lpthread -lgdbm -lid3tag -lz 
``` and I have a binary now... haven't tested it yet (at work) other than to verify version```
./mt-daapd --help (y|n|e|a)? yes
./mt-daapd: invalid option -- '-'
Usage: ./mt-daapd [options]

Options:
  -d <number>    Debuglevel (0-9)
  -D <mod,mod..> Debug modules
  -m             Disable mDNS
  -c <file>      Use configfile specified
  -p             Parse playlist file
  -f             Run in foreground
  -y             Yes, go ahead and run as non-root user


Valid debug modules:
 config,webserver,database,scan,query,index,browse
 playlist,art,daap,main,rend,misc
```

---

### Post by kleverbear on 2011-11-20
> **Steve54 said:**
> Twonky still doesn't transcode on the fly.
 
PS3mediaserver does, that is what I'm currently using on my media server to stream directly to the TV. I've wound back to version 1.3 (current V is 1.5?) as it seems to work better with my Panny TV.

Well no Twonky for me it it cant transcode on the fly. I thought PS3MS was a dead project, i love how it worked but the ram max was 600mb and after awhile the java updates would kill it. I use to use t on a freeNas box loved it for the 3 month it worked. Has it been updated???:confused:

---

### Post by zim2dive on 2011-11-23
> **kleverbear said:**
> Well no Twonky for me it it cant transcode on the fly. I thought PS3MS was a dead project, i love how it worked but the ram max was 600mb and after awhile the java updates would kill it. I use to use t on a freeNas box loved it for the 3 month it worked. Has it been updated???:confused:

Was finally able to test as well.. agreed Twonky does not seem to transcode.. I had an mkv on my machine, but it did not show up in the list on my DLNA box.  Its does show up in the web-based list (via the browser on the server).

To answer a different question, I don't think iTunes will behave as a DLNA/UPnP client.. only as a DAAP client, and I don't see a way for Twonky to do that... so far, I'm not seeing any universally compatible server?

I guess I will try miniDLNA next.

---

### Post by PCFreak2 on 2011-11-23
I've poked around a bit with Jinzora
It's pretty stable
And the best web interface I've found yet

---

### Post by zim2dive on 2011-11-23
Just to clarify.. do any of the media servers function as both DLNA/UPnP and as DAAP servers at the same time?

Just seeing if there was one which would serve all the "clients" we have running around the house...

thanks,
Mike

---

### Post by kleverbear on 2011-11-24
I haven't found a DLNA/UPnP on the fly transcode server package yet. I would love to find something like that. Im looking to serve all my DLNA (tv/PS3) and transcode my MKV's for those and of course handle my music. SubSonic has video streaming but its web based. 

I'm currently running MiniDLNA, Subsonic, Samba and looking to install PS3MS to serve all my needs and last but not least webmin to manage settings on other services. Looked up PS3MS after reading steve54 post looks like a lot of improvements have been made. Looking forward to trying it out.

Damn this variety of devices.

---

### Post by AMSlider on 2012-02-03
kleverbear, you should also check out Serviio  [http://www.serviio.org/]("http://www.serviio.org/").  It handles all of the transcoding to my LG tv and works great.  It's also written in Java and runs headless so the OP could use it on his Ubuntu server.  I think the music/pics support is pretty good as well, at least for DLNA.

Also to the OP,
You should check out MPD [http://mpd.wikia.com]("http://mpd.wikia.com").  Lot's of different CLI, GUI, and web interfaces.  It has the playlist capability you are looking for.  It takes a while to get your head around all of the possibilities, but I'm using it to stream to other pulse enabled machines on my lan, plus stream it over the web, and can stream it to my iphone as well when i'm on the go with MPoD.

HTH.

---

### Post by jkiddo on 2012-10-10
I'm currently maintaining a DAAP server for Java and I recently offered Subsonic to use it - I have however not yet received an answer

---

