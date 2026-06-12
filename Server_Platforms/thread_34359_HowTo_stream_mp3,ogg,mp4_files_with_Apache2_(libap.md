---
title: "HowTo stream mp3,ogg,mp4 files with Apache2 (libapache2-mod-musicindex)"
date: 2005-05-14
forum: Server Platforms
---

### Post by tornamodo on 2005-05-14
Hope you like this: **How-To make Apache2 Stream Music**.
We use libapache2-mod-musicindex; it works with MP3, FLAC, Ogg Vorbis or MP4/AAC files.

**We start off with installing mod and codecs:**
```
apt-get install libapache2-mod-musicindex libogg-dev 
apt-get install libvorbis-dev libid3tag0-dev libmad0-dev libflac-dev
```

**Add the mod_musicindex.so Module**
Add this line to /etc/apache2/httpd.conf
```
LoadModule musicindex_module /usr/lib/apache2/modules/mod_musicindex.so
```

**Finally, edit the <Directory> you want to **
I use the /etc/apache2/conf.d/alias file

Assuming your music is in /home/foo/music the settings should look like these:
```
Alias /music /home/foo/music/
<Directory /home/foo/music/>
    Options Indexes MultiViews FollowSymlinks
    AllowOverride       Indexes
    MusicLister         On
    MusicSortOrder      album disc track artist title length bitrate freq filet$
    MusicFields         title artist length bitrate
    MusicAllowDownload  Off
    MusicAllowStream    On
    MusicAllowSearch    On
#    MusicRssItems       Off
    MusicPageTitle      home
    MusicCssDefault     musicindex.css
    MusicCachePath      /tmp/musicindex
#    MusicIceServer     [ice.domain.my]:8000
#    MusicCookieLife    300
</Directory>
```
I'd recommend adding password protection: [http://httpd.apache.org/docs-2.0/howto/auth.html](http://httpd.apache.org/docs-2.0/howto/auth.html)

**Restart Apache**
```
/etc/init.d/apache2 restart
```

**Finished!**
Your Server is now ready to stream!
This example you'd access @ [http://localhost/music/](http://localhost/music/)


**Weblinks:**
• [http://www.parisc-linux.org/~varenet/musicindex/](http://www.parisc-linux.org/~varenet/musicindex/)
• [http://httpd.apache.org/docs-2.0/](http://httpd.apache.org/docs-2.0/)


**Simple Cosmetics**
The interface doesn't look so good out of the box I think.
A simple way to change it a bit is the file **/var/www/musicindex/musicindex.css**. 

For example the a.rss tag:
```
table#directories div > a.rss {
  font-size: 10pt;
}
```
If you change it like this:
```
table#directories div > a.rss {
  font-size: 10pt;
  margin-left:200px;
}
```
you'll have much more overview because of space between the directories  \\:D/ 

Enjoy your music streams  :-)

---

### Post by rwabel on 2005-05-15
> **tornamodo]Hope you like this: **How-To make Apache2 Stream Music**.
We use libapache2-mod-musicindex said:**
> :8000
#    MusicCookieLife    300
</Directory>
```
I'd recommend adding password protection: [http://httpd.apache.org/docs-2.0/howto/auth.html](http://httpd.apache.org/docs-2.0/howto/auth.html)

**Restart Apache**
```
/etc/init.d/apache2 restart
```

**Finished!**
Your Server is now ready to stream!
This example you'd access @ [http://localhost/music/](http://localhost/music/)


**Weblinks:**
• [http://www.parisc-linux.org/~varenet/musicindex/](http://www.parisc-linux.org/~varenet/musicindex/)
• [http://httpd.apache.org/docs-2.0/](http://httpd.apache.org/docs-2.0/)


**Simple Cosmetics**
The interface doesn't look so good out of the box I think.
A simple way to change it a bit is the file **/var/www/musicindex/musicindex.css**. 

For example the a.rss tag:
```
table#directories div > a.rss {
  font-size: 10pt;
}
```
If you change it like this:
```
table#directories div > a.rss {
  font-size: 10pt;
  margin-left:200px;
}
```
you'll have much more overview because of space between the directories  \\:D/ 

Enjoy your music streams  :-)
 thanks for the howto. it's really a sweet thing :-)
does shuffle and stream work for you?

---

### Post by tornamodo on 2005-05-16
Yes, shuffle & stream - everything works fine!

Only the RSS is not working. I disabled the option anyway by adding "color: white;" to the a.rss tag in /var/www/musicindex/musicindex.css. 
```
table#directories div > a.rss {
  font-size: 10pt;
  margin-left:200px;
  color: white;
}
```

The only problem i have with "Badly Drawn Boy - About A Boy". The tracks stop at about 3/4 of the length... 
All other files are working perfect - even over the net (200kb/50kb connection)

Shuffle and Stream works really nice  :grin:  \\:D/

---

### Post by Sniffer on 2005-05-16
Thks for this one, will come very in handy.

---

### Post by tomski on 2006-09-16
Thanks for the HowTo

I tried various embedded players and gave up when i spotted this!!
This is what i origanlly wanted

Cheers

---

### Post by Tragos on 2006-12-01
Cheers, mate!

Nice how-to, now I can easily listen to music from my server with my Nokia 770. However, you did the configurations to Apache in a bit old-fashioned way.

> **tornamodo said:**
> **Add the mod_musicindex.so Module**
Add this line to /etc/apache2/httpd.conf

In Apache2 each LoadModule row is written to its own file in */etc/apache2/mods-available/*. In fact a file called *musicindex.load* is already created in Dapper when installing the *libapache2-mod-musicindex* deb package. Modules are enabled by symlinking the .load file to directory */etc/apache2/mods-enabled/*.
```
sudo ln -s /etc/apache2/mods-available/musicindex.load /etc/apache2/mods-enabled/
```

> **tornamodo said:**
> **Finally, edit the <Directory> you want to **
I use the /etc/apache2/conf.d/alias file


Directories can be created in a similar way. Instead of using apache1-style */etc/apache2/conf.d/alias*, we create configuration files for each directory in */etc/apache2/sites-available/*. Then we symlink it to */etc/apache2/sites-enabled/*.

```
sudo ln -s /etc/apache2/sites-available/music /etc/apache2/sites-enabled/.
```

Now we can easily disable modules and directories we don't need just by deleting the symlinks. No need to search for huge configuration files for the right rows to be commented out.

---

### Post by BatteryCell on 2006-12-24
Hey thanks a lot I've been looking for something like this for a while :-)

Oh but when I installed it there wasnt a default musicindex.css or musicindex folder, I can make my own and I did, but I was just wondering if anyone had a default .css file they could post ?

---

### Post by envis on 2006-12-25
is this more like an automatically created index type of page that posts your music library automatically or is it more like a streaming component that would make apache stream audio any better?

i host somekind of "interactive radio station" already.. just wondering if that module could be of any use to me...

im a newbie in server admin :) ....

if it just builds an index from your music library, i've already sweated on a script that builds a whole freaking website from my audio libraby... but if it can somehow make apache transmit mp3 or ogg better... then i might need it!....

---

### Post by ronlybonly on 2007-01-20
Thanks for the HOWTO! I can't wait to try this out!

---

### Post by robert@debian on 2007-04-05
Thanks for this fabulous HowTo! This one helped me alot. 

This is the most comfortable way to listen to my music @ work 

:guitar:

---

### Post by userthebuntu on 2007-04-10
Hi,

thanks for the tutorial.
I did everything you said and my apache2 does run and everything (I can reach the apache2 testsite).

However apache2 doesn't seem to like the alias I'm trying to feed to it:

Alias /music/ /media/hda1/Musik/
<Directory /media/hda1/Musik/>
    Options Indexes MultiViews FollowSymlinks
    AllowOverride       Indexes
    MusicLister         On
    MusicSortOrder      album disc track artist title length bitrate freq filet$
    MusicFields         title artist length bitrate
    MusicAllowDownload  Off
    MusicAllowStream    On
    MusicAllowSearch    On
#    MusicRssItems       Off
    MusicPageTitle      home
#    MusicCssDefault     musicindex.css
    MusicCachePath      /tmp/musicindex
#    MusicIceServer     [localhost]:8000
#    MusicCookieLife    300
</Directory>

When commenting out every line of this file apache2 will run but w/ the alias file like above it won't...w/o giving out an error message or anything.

Anyone have an idea?

Many thanks in advance

---

### Post by userthebuntu on 2007-04-12
Bumpster

---

### Post by mbvlist on 2007-06-27
Pretty easy: you have to quote the directory names. At least: that's the major difference between yours and mine ;)

I forgot that directories should end with a /, unlike other things in linux. And the MusicAllow* and MusicIndex settings are legacy. /etc/apache2/sites-available/music contains:
```
Alias /music/ "/home/shared/MMFiles/"
<Directory "/home/shared/MMFiles">
        AuthType Basic
        AuthName "music"
        AuthUserFile /etc/apache2/passwords
        AuthGroupFile /etc/apache2/groups
        Require group musicindex

    Options Indexes MultiViews FollowSymlinks
    AllowOverride       Indexes
    MusicIndex          On +Stream +Download +Search -Rss -Tarball
    MusicFields         title artist length bitrate
    MusicPageTitle      Martin's homepage
    MusicDefaultCss     musicindex.css
    MusicIndexCache     file://tmp/musicindex
    MusicDirPerLine     4
#    MusicIceServer     [ice.domain.my]:8000
#    MusicCookieLife    300
</Directory>

```
If you create a file in sites-available, you can enable it with a2ensite [filename]

---

### Post by firecat53 on 2007-06-30
I actually use [edna]("http://edna.sourceforge.net/") as a very lightweight music server. Edna can run in parallel with your normal webserver (or by itself if you don't have one). Uses MUCH less resources than apache -- for that old PII you have sitting in the garage :)  It actually serves up .m3u playlist (shuffled or regular) for any music file in the directory hierarchy you have, displays album art, dynamic directory listing... Very slick!  Hmmmm....maybe another howto is in order!  

Scott

---

### Post by troseph on 2007-09-01
How to edit the home page??? I can't find the index file for my music index... It still says "Martin's homepage" as the default. How do I edit the main index file? It's not in my /usr/share/mod_musicindex folder either. Is there something I missed?

---

### Post by troseph on 2007-09-01
Oh. Duh. It's in the alias I set up. Fixed it.

---

### Post by oraknabo on 2007-12-20
This is a really great howto the first post info combined with Tragos's comments had me set up streaming mp3s in less than an hour.

---

### Post by Dr_Deadmeat on 2008-05-13
Hm... It does not work here... Whenever I try to restart my apache server I get this error

```

andreas@drdeadmeat:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                Syntax error on line 5 of /etc/apache2/conf.d/alias:
Invalid command 'MusicLister', perhaps misspelled or defined by a module not included in the server configuration
                                                                         [fail]
andreas@drdeadmeat:~$

```
And apache dont start...

---

### Post by lemerou on 2008-06-22
See: [http://www.parisc-linux.org/~varenet/musicindex/README](http://www.parisc-linux.org/~varenet/musicindex/README)

```

The MusicIndex Option replaces altogether MusicLister, MusicAllowDownload,
MusicAllowStream, MusicAllowSearch, and MusicAllowRss. To enable or disable the
module, give On or Off as an option. To enable or disable the other features,
just give '+' or '-' followed by Download, Stream, Search, Rss or Tarball.


```

if you need an e.g:

```

<Directory /var/www/MP3/>
    Options		Indexes MultiViews FollowSymlinks
    AllowOverride	Indexes
# Can be overriden in .htaccess
    MusicIndex		On +Stream +Download +Search -Rss -Tarball
    MusicSortOrder      album disc track artist title length bitrate freq filetype filename uri
    MusicFields		title artist album length bitrate
    MusicPageTitle	Myname
    MusicDefaultCss	musicindex.css
# Can only be set in apache configuration
    MusicDefaultDisplay	HTML
    MusicIndexCache	file://tmp/musicindex
    MusicIceServer	[ice.domain.my]:8000
    MusicCookieLife	300
    MusicDirPerLine	3
</Directory>


```

---

### Post by NTolerance on 2008-07-15
This is a great program.  I've been running Mythmusic/Mythweb for a while and was getting tired of some of its limitations such as lack of automated folder scanning.  Because musicindex simply lists directories it doesn't need to scan anything and your collection is always up to date.  On top of that it does what a lot of streaming servers lack - it creates playlists with song titles in them.  It's quite odd how many streaming servers give you a playlist with gibberish for all the song titles.  

I also like the folder.jpg display at the top of the page.  By default it's too small so I edited the musicindex.css file to make it 200x200.  I don't know much about web programming but changing the values in the CSS file is easy enough.

I did get some strange "unable to load module" errors from Apache when I had my DocumentRoot pointed to /var/www/mythweb.  I changed it back to /var/www and now musicindex works fine.  

The search feature doesn't work for me for some reason.  The page won't load and my CPU gets pegged when I try it.  I disabled it in the config file.  No big deal, I can just use CTRL+F in Firefox to find what I need.

Another word of caution:  newcomers to this thread please check the project page for the latest documentation as the config posted by the OP is very much out of date.

Here's my edited musicindex.css file if anyone wants to try it out:

```
body {
  font: 9pt "Lucida Grande", Verdana, Helvetica, Arial, sans-serif;
  color: black;
  background-color: white;
}

/* Italic style disabled because it just doesn't work right */
/*  for many scripts or fonts.                              */

h1 {
  font-size: 11pt;
  /* font-style: italic; */
  color: red;
  background-color: transparent;
}

h2 {
  /* font-style: italic; */
}

acronym {
	cursor : help;
}

tr.title {
  color: black;
  background-color: #FFE89B;
  text-align: left;
}

tr.title a {
  color: blue;
}

tr.odd {
  color: black;
  background-color: white;
  padding: 0;
  margin: 0;
}

tr.even {
  color: black;
  background-color: rgb(200,255,255);
  padding: 0;
  margin: 0;
}

td#directory {
  font-weight: bold;
}

div#header {
  width: 100%;
  min-height: 200px;
  font-weight: bold;
  border: 0pt;
  position: relative;
  left: 0;
  top: 0;
}

div#mainicon {
  width: 60px;
  position: absolute;
  left: 0;
  top: 0;
}

div#mainicon >img {
  width: 200px;
  height: 200px;
}

div#maintitle {
  margin-left: 210px;
}

span.rarrow {
  display: inline;
  padding-right: 10px;
  width: 13px;
  height: 10px;
  background-image: url(/musicindex/right_arrow.gif);
  background-repeat: no-repeat;
  background-position: center center;
  text-decoration: none;
}

span.dldok {
  display: inline;
  padding-right: 15px;
  padding-top: 5px;
  padding-bottom: 5px;
  width: 22px;
  height: 22px;
  background-image: url(/musicindex/fetchok.png);
  background-repeat: no-repeat;
  background-position: center center;
  text-decoration: none;
}

span.streamok {
  display: inline;
  padding-right: 15px;
  padding-top: 5px;
  padding-bottom: 5px;
  width: 21px;
  height: 22px;
  background-image: url(/musicindex/soundok.png);
  background-repeat: no-repeat;
  background-position: center center;
  text-decoration: none;
}

a.bigdir {
  position: absolute;
  margin-top: -6px;
  width: 34px;
  height: 34px;
  display: inline;
  background-image: url(/musicindex/directory.png);
  background-repeat: no-repeat;
  text-decoration: none;
}

a.dld {
  display: inline;
  padding-right: 15px;
  padding-top: 8px;
  padding-bottom: 5px;
  width: 22px;
  height: 22px;
  background-image: url(/musicindex/fetch.png);
  background-repeat: no-repeat;
  background-position: center center;
  text-decoration: none;
}

a.stream {
  display: inline;
  padding-right: 15px;
  padding-top: 8px;
  padding-bottom: 5px;
  width: 21px;
  height: 22px;
  background-image: url(/musicindex/sound.png);
  background-repeat: no-repeat;
  background-position: center center;
  text-decoration: none;
}

a.shuffle {
  display: inline;
  padding-right: 15px;
  padding-top: 8px;
  padding-bottom: 5px;
  width: 21px;
  height: 22px;
  background-image: url(/musicindex/shuffle.png);
  background-repeat: no-repeat;
  background-position: center center;
  text-decoration: none;
}

a.rss {
  display: inline;
  padding-right: 15px;
  padding-top: 5px;
  padding-bottom: 5px;
  width: 22px;
  height: 22px;
  background-image: url(/musicindex/rss.png);
  background-repeat: no-repeat;
  background-position: center center;
  text-decoration: none;
}

a.tarball {
  display: inline;
  padding-right: 15px;
  padding-top: 5px;
  padding-bottom: 5px;
  width: 22px;
  height: 22px;
  background-image: url(/musicindex/fetch.png);
  background-repeat: no-repeat;
  background-position: center center;
  text-decoration: none;
}

form#searching {
  position: absolute;
  right: 0;
  top: 0;
  text-align: right;
}

td {
  padding-left: 5px;
  padding-right: 5px;
}

td.Length {
  text-align: right;
}

td.Select {
  text-align: left;
}

td.Disc {
  text-align: center;
}

td.Track {
  text-align: center;
}

td.Bitrate {
  text-align: right;
}

td.Freq {
  text-align: right;
}

td.Size {
  text-align: right;
}

td.Filetype {
  text-align: right;
}

td.Filename {
  font-family: monospace;
}

table#directories {
  font-weight: bold;
  width: 95%;
  text-align: left;
  vertical-align: bottom;
  table-layout: fixed;	/* this may cause issues with twisted directory names... */
}

table#directories td {
/*  width: 33%; */
  padding-bottom: 5px;
}

table#directories div > a {
  font-size: 10pt;
}

table#directories td > a > img {
}

table#directories div {
  margin-left: 38px;
  min-height: 50px;
}

form#tracks table {
  width: 100%;
  border-spacing: 0;
  border: 0;
}

form#custom {
  border: maroon solid 2px;
  width: 99%;
  background-color: #ffe89b;
  margin: 0 auto;
}

form#custom table {
  width: 100%;
  border-spacing: 0;
  border: 0;
}

form#custom tr.odd {
  background-color: #ffe89b;
}

form#custom tr.even {
  background-color: #ffe89b;
}

form#custom div {
  background: transparent;
}

th {
  padding-left: 5px;
  padding-right: 5px;
}

th.Select {
  width: 70px;
  text-align: center;
}

th.Bitrate {
  text-align: right;
}

th.Freq {
  text-align: right;
}

th.Length {
  text-align: right;
}

th.Size {
  text-align: right;
}

th.Genre {
  text-align: center;
}

th.Filetype {
  text-align: right;
}

img {
  border: 0pt;
  vertical-align: middle;
}

a {
  color: blue;
  background-color: transparent;
}

button {
  color: black;
  background-color: white;
}

div {
  color: black;
  background-color: white;
}

.playlist {
  color: black;
  background-color: #FFE89B;
}

div#footer {
  width: 100%;
  position: relative;
  left: 0;
  top: 0;
  height: 41px;
}

div#valid {
  position: absolute;
  left: 0;
}

div#name {
  position: absolute;
  right: 0;
  top: 10px;
  bottom: 10px;
  vertical-align: middle;
}

```

---

