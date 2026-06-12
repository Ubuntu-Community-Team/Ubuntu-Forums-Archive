---
title: "FTP GUI anyone ?"
date: 2005-11-08
forum: The Cafe
---

### Post by flower on 2005-11-08
Is anybody using a nice FTP gui program?
I mean ... yeah .. I can do with gFTP but it sucks ... 
I tried also kasablanka and kbear (but KDE ... bleah .. )

On windows I'm using FileZilla wich is nearly perfect in 96% of interface and functionality ... It has a nice Site Manager (drag&drop stuff included), nice GUI (again drag&drop super useful), it's multithreaded, it supports ftp, sftp, ftp over ssh2, it has a CLEAR way to show the processed files, and it has a log of the ftp commands, also import & export of the stored sites. The author works on the Linux version ... but I don't see much progress ... 

In general every Ftp client has these, but either it's ugly or it is not user friendly (at least I didn't found one that I like) ... 

I'm playing with the source of one (CubeFtp) but it doesn't seem as I have enough time to make it as good as I want ... 

So ... anyone to recommend a good FTP gui ?

---

### Post by cyrax on 2005-11-08
why GUI`??

---

### Post by A-star on 2005-11-08
Just a suggestion, you can run FileZilla if you use wine.

---

### Post by frodon on 2005-11-08
You could try : [IglooFTP]("http://www.iglooftp.com/unix/download.html"), [AxYFTP]("http://www.wxftp.seul.org/"), [NFTP]("http://www.ayukov.com/nftp/index.html"), [yafc]("http://yafc.sourceforge.net/"), [DPS-FTP]("http://dpsftp.sourceforge.net/"), ...

---

### Post by Jonne on 2005-11-08
Filezilla is coming to Linux in version 3.0. Just wait a bit :). I find the lack of a nice GUI ftp app annoying too.

---

### Post by frodon on 2005-11-08
Yes there isn't many good FTP clients for the moment but i like gFTP personally :)

---

### Post by Jonne on 2005-11-08
I *use* gFTP, but I don't *like* it ;).

---

### Post by asimon on 2005-11-08
If I don't use lftp I just use Konqueror, it's GUI is good enough for my ftp needs.

---

### Post by flower on 2005-11-08
**why GUI :** I'm a web developer - I need a powerful program to handle my ftp stuff - it remembers the login data, and the default folders. It's drag&drop so I can see what I'm doing, and lot of other stuff 

**filezilla + wine : ** I tried that some time ago, but it's buggy (specially the ftp commands log which is important to me) and the interface is sluggish, the folders are organized wine way with drives etc. I'm not excited about it

**filezilla3 ** : yes the site says it's under development but I downloaded cuple of time snapshots and I don't see any progress ... :((((( 

thanks for the other propositions guys, I'm gonna give them a try :)

---

### Post by flower on 2005-11-08
yeah, and just an addition to my post : 

I'm not just asking for a good program, bcz see I'm mad GUI guy or something like this ... 
I do websites and I just need a lot of features to save time ...

---

### Post by Jonne on 2005-11-08
hey, i'm in the same boat as you. gFTP kinda works for me, but i'd prefer filezilla.

---

### Post by flower on 2005-11-08
well yes that's the exact problem ! gFTP **kinda** works ... with a site manager and drag&drop this program will do but ...

---

### Post by crypto178 on 2005-11-08
It is possible to bookmark locations (with password) in gFTP, while it's not a full featured site manager it is enough for me... 
The lack of drag&drop support is annoying though.

---

### Post by flower on 2005-11-08
here's some outcome from my tries to beautify the GUI of ftpcube ...

I've made a new Site Manager (in the screenshot) and I'm trying to make buttons and texts to be smaller ... but I guess I don't know python enough to make the program complete ... drag & drop for example is a mistery at this point :)

---

### Post by frodon on 2005-11-08
wow, it looks good !!

is it in the repositories and does the drag & drop work with ftpcube ?

---

### Post by endersshadow on 2005-11-08
Yeah, dude, that definitely looks awesome.  Make sure to make that available...perhaps somebody else with Python experience can help you with the drag and drop.

---

### Post by Stormy Eyes on 2005-11-08
Firefox has a fireFTP extension that allows Firefox to act as an ftp client. Also, you can configure Nautilus to open ftp connections and store passwords in a keyring. What exactly is wrong with gFTP? I've used it for years without any trouble.

---

### Post by Jonne on 2005-11-08
If you've used Filezilla on Windows, you'll probably want to use it on Linux too. It's just the best FTP app I've ever used.

---

### Post by Mr. Electric Wizard on 2005-11-08
I curious about the FileZilla multi thread issue.
Does this make the transfers faster?
I noticed that the new NewsReader programs are multithreading too (newsBinPro).

---

### Post by flower on 2005-11-09
to Mr. Electric Wizard : yes multithreading means the client opens few ftp connection to the same server and uploads/downloads few files at the same time - it's a bit faster when you upl/download big count of small files

to Jonne : yes, I totally agree FileZilla is the best one ... no much progress on ver.3 tough :( are you a belgian ?

to frodon & endersshadow : yeah I put a lot of work, bcz ftpcube was written in older ver. of Python and older ver. of wxWindows, so ... I fixed the code to work with the current versions, and I have put some work on the GUI ... but still there are some serious issues / bugs there ... it goes slow tough and I doubt I can make it alone

-------------------
wow .. one of you tol me about fireftp and I must say it's really nice ... it just lacks a site manager, but it's really nice : [http://fireftp.mozdev.org/](http://fireftp.mozdev.org/)

---

### Post by jasidog on 2006-05-05
You can get recent nightlies of Filezilla3 that seem to work ok on Breezy here - [http://filezilla-project.org/nightly.php](http://filezilla-project.org/nightly.php)

Just extract and run the binary. 

I've not had a chance to really play about with it. I'm sure there are bugs but is seems to work ok.

---

### Post by Stormy Eyes on 2006-05-05
Try the FireFTP extension for Firefox.

---

### Post by aysiu on 2006-05-05
*kftpgrabber* is the closest native Linux application I've seen to FileZilla, and it's available in the Dapper Universe repositories.

---

### Post by Jonne on 2006-05-05
[QUOTE=jasidog]You can get recent nightlies of Filezilla3 that seem to work ok on Breezy here - [http://filezilla-project.org/nightly.php](http://filezilla-project.org/nightly.php)

Just extract and run the binary. 

I've not had a chance to really play about with it. I'm sure there are bugs but is seems to work ok.[/QUOTE]
thanks for telling us.

It seems to work ok (in Dapper).

I just extracted it in my home directory and it worked from there. Where should it be placed ideally? I'm a Linux n00b, and I'm still not sure where exactly apps should be stored on the Linux file system ;).

Also, it looks like a QT app, so I think you'll need some of the KDE libs to be able to run it. I'm not certain though.

---

### Post by SeanTater on 2006-05-05
100% kio/konqueror here -- with it I see no need for an ftp program

---

### Post by prizrak on 2006-05-05
I prefer cuteFTP on Windows personally. I want FileZilla server to be ported to Linux, it was the easiest FTP server I have EVER had to setup (then again my FTP serving experience went from ServU to first ever FileZilla to ProFTPd to latest FileZilla)
It will be nice when FZ 3.0 comes out for Linux though, the devs did a great job with it and it is very powerful for those who have to deal with alot of FTP sites. I believe it also supports encrypted downloading and pausing.

---

### Post by INMCM on 2006-05-05
Recently I've been using VirgoFTP [http://virgoftp.auserver.net/](http://virgoftp.auserver.net/)

It written in Java, but's it's REALLY nice even.

---

### Post by mustang on 2006-05-05
FlashFXP 2.1 w/wine

can't beat good old flashfxp

---

### Post by htinn on 2006-05-05
For FTP: <insert name of favorite file manager here>

---

### Post by pianoboy3333 on 2006-05-05
[QUOTE=htinn]For FTP: <insert name of favorite file manager here>[/QUOTE]

So we can use nautilus as an FTP? I've got an idea, instead of wining about not finding one you like, *make* one to suit your needs!

---

### Post by prizrak on 2006-05-05
[QUOTE=pianoboy3333]So we can use nautilus as an FTP? I've got an idea, instead of wining about not finding one you like, *make* one to suit your needs![/QUOTE]
If you missed it he did mention trying. Also not everyone posseses the knowledge to create an FTP application. I for one do not, despite being able to program in multiple languages.

---

### Post by htinn on 2006-05-05
Actually, I have used Nautilus for FTP and it works great. Now, I generally prefer to use something like Worker or Krusader, but you see where I'm going with this.

---

### Post by prizrak on 2006-05-05
[QUOTE=htinn]Actually, I have used Nautilus for FTP and it works great. Now, I generally prefer to use something like Worker or Krusader, but you see where I'm going with this.[/QUOTE]
Nautilus works just fine as well as Firefox or even IE, the problem however is certain features that come in specialized FTP cients. Nautilus doesn't multithread or pause/resume dls, it doesn't support encryption, the list goes on and on.
This is basically the thing, for any regular user Nautilus will work just fine or anything else that is fairly basic. Just like MS Paint worked fine for me when I needed to do some basic picture editing but for anything more than that you need a specialized program.

---

### Post by Dark Tranquility on 2006-05-06
[QUOTE=htinn]Actually, I have used Nautilus for FTP and it works great. Now, I generally prefer to use something like Worker or Krusader, but you see where I'm going with this.[/QUOTE]
Yes Nautilus works great for me too!
I also like Igloo

---

### Post by aysiu on 2006-05-08
I wouldn't have said this a year ago, but I just tried FireFTP, and it blew me away.

It has improved **a lot** in the past year. It is definitely the best FTP client I have seen--simple but powerful. My previous favorite was FileZilla, which is powerful but not that simple. For Linux, KFTPGrabber came close to FileZilla, but it also lacked FireFTP's simplicity.

The best thing about FireFTP is its integration with the browser (just another tab), which makes it cross-platform. I can use it in OS X, XP, and Dapper.

New things I'm impressed by:

1. Remembering directories--both local and remote--and tailored specifically for each site.

2. Security protocols

---

### Post by SolidAndShade on 2006-05-08
Flower, have you tried using Nautilus's FTP functionality? Just select "Connect to Server" from Nautilus's File menu to connect to a remote server. Dragging and dropping is very easy, since Nautilus handles all the graphical file browsing on a typical Gnome Ubuntu installation. Whenever you create a "Connect to Server" link in Nautilus you are asked what folder you want to link to, so you can create mount points for many different places within an FTP server's directory tree.

---

### Post by arachn1d on 2006-05-12
I actually like FireFTP alot. It's fun :)

---

### Post by TheApe on 2006-05-12
**lftp can handle the job**

On windows, I used to use leachftp, or other Visual ftp client.
Since I'm web developer and have to upload and download lots of files, this was the best choice.

I think gftp is very weak. And haven't found any other GUI ftp client. Then I decided to go to the command line, and found lftp. The best feature for me is the function *mirror*. I can use it to sync any directory tree(even the whole ftp site). So if I make some change on local i just hit mirror -R and it puts just the changed and newer files. It's such a nice tool for working with websites.

Lftp can even handles bookmarks and have others great features.
Geave it a try ;) 

```
sudo apt-get install lftp
```

---

### Post by hizaguchi on 2006-05-12
Fuse's sshfs is the way to go.  You can just mount your webspace like a local directory and then edit and save your files without needing to move them around or anything.

---

