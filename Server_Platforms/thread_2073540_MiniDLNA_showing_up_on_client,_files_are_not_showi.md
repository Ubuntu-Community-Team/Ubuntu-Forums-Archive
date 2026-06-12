---
title: "MiniDLNA showing up on client, files are not showing"
date: 2012-10-19
forum: Server Platforms
---

### Post by duodecillian on 2012-10-19
I'm streaming to a Logitech Revue, and I've actually had success with MiniDLNA before. This time around I don't seem to be so lucky.

MiniDLNA is updating, I know this because if I edit the name of the server and restart it, the client shows these changes.

I'm assuming I'm having some sort of permission errors, though I'm having trouble trying to pinpoint exactly where the problem is.

I'm sorry if I don't have enough information here, but I'm more than willing to divulge anything that I am missing.

Thanks. :)
Also, here is my /etc/minidlna.conf in case I've just made a silly error that for the life of me I cannot seem to find.

```
# This is the configuration file for the MiniDLNA daemon, a DLNA/UPnP-AV media
# server.
#
# Unless otherwise noted, the commented out options show their default value.
#
# On Debian, you can also refer to the minidlna.conf(5) man page for
# documentation about this file.


# Path to the directory you want scanned for media files.
#
# This option can be specified more than once if you want multiple directories
# scanned.
#
# If you want to restrict a media_dir to a specific content type, you can
# prepend the directory name with a letter representing the type (A, P or V),
# followed by a comma, as so:
#   * "A" for audio    (eg. media_dir=A,/var/lib/minidlna/music)
#   * "P" for pictures (eg. media_dir=P,/var/lib/minidlna/pictures)
#   * "V" for video    (eg. media_dir=V,/var/lib/minidlna/videos)
#
# WARNING: After changing this option, you need to rebuild the database. Either
#          run minidlna with the '-R' option, or delete the 'files.db' file
#          from the db_dir directory (see below).
#          On Debian, you can run, as root, 'service minidlna force-reload' instead.
media_dir=/var/lib/minidlna
media_dir=V,/home/duodecillian/Videos/Server
# Path to the directory that should hold the database and album art cache.
db_dir=/var/lib/minidlna

# Path to the directory that should hold the log file.
log_dir=/var/log

# Minimum level of importance of messages to be logged.
# Must be one of "off", "fatal", "error", "warn", "info" or "debug".
# "off" turns of logging entirely, "fatal" is the highest level of importance
# and "debug" the lowest.
#log_level=warn

# Use a different container as the root of the directory tree presented to
# clients. The possible values are:
#   * "." - standard container
#   * "B" - "Browse Directory"
#   * "M" - "Music"
#   * "P" - "Pictures"
#   * "V" - "Video"
# if you specify "B" and client device is audio-only then "Music/Folders" will be used as root
#root_container=.

# Network interface(s) to bind to (e.g. eth0), comma delimited.
#network_interface=

# IPv4 address to listen on (e.g. 192.0.2.1).
#listening_ip=

# Port number for HTTP traffic (descriptions, SOAP, media transfer).
port=8200

# URL presented to clients.
# The default is the IP address of the server on port 80.
presentation_url=http://192.168.0.1:8200/

# Name that the DLNA server presents to clients.
friendly_name=MiniDLNA_Ubuntu

# Serial number the server reports to clients.
serial=12345678

# Model name the server reports to clients.
#model_name=Windows Media Connect compatible (MiniDLNA)

# Model number the server reports to clients.
model_number=1

# Automatic discovery of new files in the media_dir directory.
#inotify=yes

# List of file names to look for when searching for album art. Names should be
# delimited with a forward slash ("/").
album_art_names=Cover.jpg/cover.jpg/AlbumArtSmall.jpg/albumartsmall.jpg/AlbumArt.jpg/albumart.jpg/Album.jpg/album.jpg/Folder.jpg/folder.jpg/Thumb.jpg/thumb.jpg

# Strictly adhere to DLNA standards.
# This allows server-side downscaling of very large JPEG images, which may
# decrease JPEG serving performance on (at least) Sony DLNA products.
#strict_dlna=no

# Support for streaming .jpg and .mp3 files to a TiVo supporting HMO.
#enable_tivo=no

# Notify interval, in seconds.
#notify_interval=895

# Path to the MiniSSDPd socket, for MiniSSDPd support.
#minissdpdsocket=/run/minissdpd.sock
```

---

### Post by cariboo on 2012-10-19
Have you checked /var/log/minidlna.log for any glaring errors?

---

### Post by duodecillian on 2012-10-20
[COLOR="Silver"]Yep, the folder is empty. That's why I'm thinking that MiniDLNA is doing its thing and it is I who made an error somewhere.[/COLOR]
**EDIT: I am an idiot, please ignore the above.**
I suppose if all else fails I can just end up trying Mediatomb.


My minidlna.log seems to be showing these errors repeatedly:
```

[2012/10/19 18:35:41] minidlna.c:898: warn: Starting MiniDLNA version 1.0.24 [SQLite 3.7.13].
[2012/10/19 18:35:41] minidlna.c:1006: warn: HTTP listening on port 8200
[2012/10/19 18:35:41] inotify.c:195: warn: WARNING: Inotify max_user_watches [8192] is low or close to the number of used watches [4] and I do not have permission to increase this limit.  Please do so manually by writing a higher value into /proc/sys/fs/inotify/max_user_watches.
[2012/10/20 01:25:57] minidlna.c:155: warn: received signal 15, good-bye


```

---

### Post by littlegreiger on 2012-10-20
I'm not sure why you have /var/lib/minidlna configured for one of your media folders, if you don't have any media in there you could try removing it. I don't think that's the problem though.

Also when you say that the folder is empty which folder do you mean? /var/lib/minidlna? If so, minidlna most likely doesn't have permission to write to it therefore it cannot build up its database. Try running ```
minidlna -R
``` as whichever user is normally running minidlna then check the log file to see what it says.

---

### Post by duodecillian on 2012-10-20
> **littlegreiger said:**
> I'm not sure why you have /var/lib/minidlna configured for one of your media folders, if you don't have any media in there you could try removing it. I don't think that's the problem though.

Also when you say that the folder is empty which folder do you mean? /var/lib/minidlna? If so, minidlna most likely doesn't have permission to write to it therefore it cannot build up its database. Try running ```
minidlna -R
``` as whichever user is normally running minidlna then check the log file to see what it says.



That folder was there by default, so I figured I'd just leave it there.

I can run minidlna -R as su and have edited the above post to show the error messages that I am getting.

Sorry, my mistake.

---

### Post by littlegreiger on 2012-10-20
You can try changing the number of max_user_watches. My value is 524288, I don't remember setting that though. But with some googling I found a site that explains how to change it [http://monodevelop.com/Inotify_Watches_Limit]("http://monodevelop.com/Inotify_Watches_Limit"). Try changing your value to a value greater than 65536 (unofficial number that minidlna is looking for).
Try that and post back if it doesn't work.

---

### Post by duodecillian on 2012-10-20
Alright, I changed the vallue to 65538

```
# echo 65538 > /proc/sys/fs/inotify/max_user_watches

sysctl fs.inotify.max_user_watches=66538
fs.inotify.max_user_watches = 66538

```

Then, I attempted to restart the server and got this

```
service minidlna restart
 * Restarting DLNA/UPnP-AV media server minidlna                                [2012/10/20 14:07:46] minidlna.c:786: error: Usage:
	/usr/bin/minidlna [-d] [-v] [-f config_file]
		[-a listening_ip] [-p port]
		[-s serial] [-m model_number] 
		[-t notify_interval] [-P pid_filename]
		[-w url] [-R] [-V] [-h]

Notes:
	Notify interval is in seconds. Default is 895 seconds.
	Default pid file is /run/minidlna/minidlna.pid.
	With -d minidlna will run in debug mode (not daemonize).
	-w sets the presentation url. Default is http address on port 80
	-h displays this text
	-R forces a full rescan
	-L do note create playlists
	-V print the version number

```

---

### Post by littlegreiger on 2012-10-20
In your config file it looks like you forgot to enable inotify. Uncomment the lines ```
#inotify=yes
and
#notify_interval=895
```
And you can also decrease the notify interval, I have it set at 300 (5 minutes).

Edit: Thinking about it more, this shouldn't matter. Do you still get the same error when you just start minidlna not as a service?

---

### Post by duodecillian on 2012-10-20
Well, that seems to have fixed just about all the error messages I was getting.

I'm not sure if it will just take a bit for it all to load because the files still aren't coming up, but the only message I'm getting in my /var/log/minidlna.log is this:

```
[2012/10/20 14:25:12] scanner.c:727: warn: Scanning /home/duodecillian/Videos/Server
[2012/10/20 14:25:14] scanner.c:798: warn: Scanning /home/duodecillian/Videos/Server finished (37 files)!
[2012/10/20 14:25:14] playlist.c:125: warn: Parsing playlists...

```

---

### Post by littlegreiger on 2012-10-20
It usually takes a little while to build the database. However, on the client you should see it slowly adding files. If you want you can also look at the database file directly using an sqlite browser or look at the web interface on port 8200 to see the number of files it finds.

---

### Post by duodecillian on 2012-10-20
Alright!, one last thing. I was receiving an error message on the HTTP port 8200, so I just changed it to 8201 in /etc/minidlna.conf and restarted the server, all of the videos *instantly* popped up.

Marking this thread as solved, thank you everyone! So very much! :)

---

