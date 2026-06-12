---
title: "Streaming movies remotely"
date: 2013-05-12
forum: Server Platforms
---

### Post by dd1linux on 2013-05-12
I know what you're thinking - "Use google retard", but I have - and I have tried following countless how-to's, yet every one i follow hits a snag somewhere and I can't find the answers I need.  I am, admittedly, atleast somewhat of a newb.  What I want is to be able to stream the movies I have saved on my external drive attached to my server at home anywhere I happen to be.  I started with making a LAMP ubuntu 12 server.  Then I made an index.html in /var/www which gave links to the various things I'd like to access (Music, Movies, Pictures, etc .. )  First, I ht a snag in even getting linked to anything outside my /var/www folder.  Then I found a how to which showed me how to add what I believe to be called SymLinks to my httpd.conf such as:

Alias /woogabooga "/media/storage/Movies"

<Directory "/media/storage/Movies">
Options +FollowSymLinks
AllowOverride None
Order allow,deny
Allow from all
AuthType Basic
AuthName "Restricted Files"
AuthUserFile /home/John/passwords
Require user John
</Directory>

So, after editing my /var/www/index.html to include a link to movies, I go to my website and see a basic page with a link to Movies.  When I click Movies I see the very basic file list of all the movies I have.  From anywhere in the world I can click on those titles and DOWNLOAD them (sometimes stream - depending upon the plugins installed on the remote PC i presume) - pretty cool I thought.  However, my ultimate goal is to STREAM them on anything as opposed to downloading the entire thing.  

So, I found another how-to which instructed me to download a program called filenice.  Well, I got that all setup and now I can go to [http://mywebaddress/filenice](http://mywebaddress/filenice) and get a nicer looking page where I can see a much more visually appealing list of whatever files it's linked to.  The problem is, I can only see the files I copy to /var/www/filenice (as opposed to all files in 'media/storage/Movies), I can see it pop up remotely and atleast on a computer (as opposed to an iPhone), click on "Open in MPlayer", and have it stream!  

The next step was to download Darwin Streaming Server.  I got the .tar, unzipped it, and was then instruced to run ./Buildit, but then received all sorts of error messages as follows:

onfiguring for the Linux i686 platform
Building for Linux.i686 with gcc
Building CommonUtilitiesLib for Linux.i686 with gcc
./Buildit: 327: ./Buildit: make: not found
Building QTFileLib internal for Linux.i686 with gcc
./Buildit: 335: ./Buildit: make: not found
Building StreamingServer for Linux.i686 with gcc
./Buildit: 341: ./Buildit: make: not found
Building RefMovieModule for Linux.i686 with gcc
./Buildit: 345: ./Buildit: make: not found
Building DemoAuthorizationModule for Linux.i686 with gcc
./Buildit: 349: ./Buildit: make: not found
Building RawFileModule for Linux.i686 with gcc
./Buildit: 353: ./Buildit: make: not found
Building SpamDefenseModule for Linux.i686 with gcc
./Buildit: 357: ./Buildit: make: not found
Building HomeDirectoryModule for Linux.i686 with gcc
./Buildit: 361: ./Buildit: make: not found
Building StreamingProxy for Linux.i686 with gcc
./Buildit: 367: ./Buildit: make: not found
Building qtpasswd for Linux.i686 with gcc
./Buildit: 371: ./Buildit: make: not found
Building PlaylistBroadcaster for Linux.i686 with gcc
./Buildit: 375: ./Buildit: make: not found
Building MP3Broadcaster for Linux.i686 with gcc
./Buildit: 379: ./Buildit: make: not found
Building QTFileTools for Linux.i686 with gcc
Building QTBroadcaster for Linux.i686 with gcc
./Buildit: 386: ./Buildit: make: not found
Building QTFileInfo for Linux.i686 with gcc
./Buildit: 390: ./Buildit: make: not found
Building QTFileTest for Linux.i686 with gcc
./Buildit: 394: ./Buildit: make: not found
Building QTRTPFileTest for Linux.i686 with gcc
./Buildit: 398: ./Buildit: make: not found
Building QTRTPGen for Linux.i686 with gcc
./Buildit: 402: ./Buildit: make: not found
Building QTSDPGen for Linux.i686 with gcc
./Buildit: 406: ./Buildit: make: not found
Building QTSampleLister for Linux.i686 with gcc
./Buildit: 410: ./Buildit: make: not found
Building QTTrackInfo for Linux.i686 with gcc
./Buildit: 414: ./Buildit: make: not found
Building StreamingLoadTool for Linux.i686 with gcc
./Buildit: 421: ./Buildit: make: not found

So .. I either need Darwin to compile properly, figure out how to link to all movies in /storage/Movies to it and go that route, or figure out why some devices will stream some of the conent from Movies and not others - and then remedy that situation.  I realize I may have explained my problem poorly, and if that's the case please tell me what more information you need, or (and preferrably) get filenice to link to my movies folder.  Pease help.

---

### Post by DaveyG on 2013-05-12
Looks like you don't have make installed, try installing build-essential and try again:

```
sudo apt-get install build-essential
```

---

### Post by rubylaser on 2013-05-12
Just one more option for streaming.  [Plexmediaserver]("http://www.plexapp.com/getplex/") makes this dead simple, has a nice interface, is free, and will automatically transcode movies for devices over the WAN. High bitrate files will struggle to playback remotely, until they are transcoded first. It doesn't provide Downloading movies though.

---

### Post by SeijiSensei on 2013-05-12
Cheesemill listed a variety of options for streaming video in [this recent post]("http://ubuntuforums.org/showthread.php?t=2142911&p=12639263&viewfull=1#post12639263").

---

### Post by dd1linux on 2013-05-12
DaveyG, you were spot on!  Thanks for your help with that.  

rubylaser, I went ahead and went with Plex - and WOW is it perfect!!  It's really made for dummies like me, lol.  I pretty much have it all set up already, but I have a few more questions.  If you wouldn't mind assisting me through PM, I would really appreciate it (just message me - I don't want to bother you.)  No big deal if not - I can go ask for help on their board.

---

### Post by rubylaser on 2013-05-13
Just ask your question here, that way other users searching in the future may benefit from the conversation :)  I'll be happy to try to answer your questions.

---

### Post by DaveyG on 2013-05-13
You're welcome dd1linux. Feel free to ask your question here

---

### Post by dd1linux on 2013-05-14
Wow, you guys sure are helpful!  OK, here goes .. is there any way I can get two instances of plex running on the same server?  I've done some researching today, and it seems to be impossible at this point in time.  I would like for my niece and nephew to be able to watch movies off my server, but the way things are now, I have no way of cutting them off from watching Natural Born Killers, Goodfellas, etc..  Ideally, I would like two instances running - one with family friendly content, and the other with the adult stuff (I thought I'd be able to by using different ports - i.e., if it usually uses 32400 I thought I could setup another one to use 32401), but from what I've been reading that is not possible.  So I guess I will be looking to setup an entirely different program - but MAN is PLEX nice with the thumbnails, streaming to ANY device (even flash retarded iPhones, etc.)  Perhaps there are other programs in the same tier as far as ease of installation and vast features goes?

---

### Post by rubylaser on 2013-05-14
Good question.  No, this is not built into Plex, but you can get around this limitation, if you are willing to follow some pretty [easy directions]("http://forums.plexapp.com/index.php/topic/44409-parental-controls-a-working-solution/").

---

