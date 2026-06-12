---
title: "Why can't there be a good Download Manager/Accelerator For Ubuntu ?"
date: 2007-11-12
forum: The Cafe
---

### Post by cyneuron on 2007-11-12
Hello Friends.

I am witting this post after a frustrating experience in recently in Ubuntu....

I wanted to download few heavy videos (like 250 MB) from Google video. for this i needed a download manager.

I could not use:

1. Firefox own Download Manager as i needed to pause and resume downloads, sometime even after closing Firefox or restarting Ubuntu.

2. DownThemAll for same reasons as above...

I downloaded  Gwget from Ubuntu repos and installed flashgot extension in Firefox.

Now when i sent download link to Gwget via flashget, Gwget didn't process the link and showed error "Can't write file" while even the firefox download manager and DownThemAll, both were able to download the .mp4 file.

Story doesn't end here....

I started looking for other download manager.

Aria Download Manager : There were no buttons when i opened the program. I don't know why. But the same problem was there with Aria in Ubuntu Feisty as well.

D4X: same problem as with Gwget...

wxDownloadFast : not available in Ubuntu repo.....Gutsy package not available, neither on getdeb.net, nor on its official website....feisty and edgy package are unstable when installed in Gutsy....though it was the only one which could start the download....

Kget: I am on GNOME (most of us are ).... i didn't want to install loads of KDE libs on my Ubuntu GNOME system....

Finally i had to boot into Windows XP and download files using Flashget....

I a really frustrated with this experience....though it hasn't shaken my belief in Ubuntu....

I am surprised as if why isn't there a good download manager/accelerator available in Ubuntu ?

Flashget is such an awesome Download Manager/Accelerator in Windows. It is free. so why can't they or someone else port it to Linux.

I have filed a bug on Gwget website about this odd problem of Gwget being not able to process the download link from Google video.

---

### Post by -grubby on 2007-11-12
have you tried running flashget in wine?

---

### Post by cyneuron on 2007-11-12
using any windows program under wine is even much more resource hugry process than even running KDE program under ubuntu.....

---

### Post by -grubby on 2007-11-12
> **cyneuron said:**
> using any windows program under wine is even much more resource hugry process than even running KDE program under ubuntu.....

that is 100% false unless you have something to back that up with

---

### Post by cyneuron on 2007-11-12
no intention of hurting you.... 

i am no professional in knowing this....said this thinking that running anything under wine will require lots of RAM to run wine itself....and above that the program...

and even important than above reason, is using a windows program under wine to solve really a good solution..... ? isn't it is always good to have native apps of any environment ?

and i mean its just a download manager, nothing big like Adobe Photoshop that you should think wine in first place.....

---

### Post by -grubby on 2007-11-12
> **cyneuron said:**
> no intention of hurting you.... 

i am no professional in knowing this....said this thinking that running anything under wine will require lots of RAM to run wine itself....and above that the program...

and even important than above reason, is using a windows program under wine to solve really a good solution..... ? isn't it is always good to have native apps of any environment ?

and i mean its just a download manager, nothing big like Adobe Photoshop that you should think wine in first place.....

I'm thinking there should be a download manager for Linux natively. It just wouldn't make sense to be missing that. It's a simple program. I'll go looking for one. Wine is useful only sometimes also. Sometimes programs dont' like to work in it

---

### Post by -grubby on 2007-11-12
I found one. It's Kind of old though. get it [here]("http://packages.debian.org/prozgui")

---

### Post by afonic on 2007-11-12
I use Flashget download manager under Wine and it uses the same ammount of RAM than in WindowsXP. Remember Wine is not an emulator.

I just use wget for all my downloading needs just keep Flashget around for when I need to download loads of files fast and -r option in wget gives errors. Aria2 works well too.

The best download manager for Linux is Downloader4X however, if you can describe the error maybe someone can help you.

---

### Post by LaRoza on 2007-11-12
Opera (the web browser) will allow you to stop and resume transfers easily. It is also quite fast (at least in my experience).

---

### Post by Sunflower1970 on 2007-11-12
> **LaRoza said:**
> Opera (the web browser) will allow you to stop and resume transfers easily. It is also quite fast (at least in my experience).

+1 for Opera. Whenever I have trouble with Firefox, I'll switch to Opera do d/l things...

---

### Post by LaRoza on 2007-11-12
I use Opera all the time. It is fast, feature rich, and I use it everywhere. I have the portable version on a flash drive (along with 50 other apps) so I can use it on other computers without installing.

---

### Post by Vivaldi Gloria on 2007-11-12
Try multiget:

multiget.sourceforge.net

Either copy and paste the link to multiget, or use flashgot to pass it to multiget. Unfortunetly, you have to configure flashgot to this. But it is very easy to do. You can make flashgot support MulltiGet by adding a new downloader in flashgot's settings menu with the path /usr/bin/MultiGet and the pass option [url=URL] [refer=REFERER].

By the way, flashgot can pass the links from firefox to gwget without a problem in my gutsy. I don't know why yours cannot.

The reason I prefer multiget is that you can download a file multi-threaded, i.e. download the diffrent parts of a file at the same time to increase speed. AFAIK Gwget does not support this.


I agree with you on

1. No linux downloader is as good as freedownloadmanager.org

2. I don't like using wine for any reason. But this has got nothing to do with the resources. I want to use linux programs with the linux feel and look. Wine sucks. Besides, the repos and program updates are the strong point of linux.

---

### Post by cyneuron on 2007-11-12
have got opera recommended for this purpose for the first time.....does opera support resuming even after restarting Ubuntu....

gonna try multiget....but as it is not available in official repo, its kind aproblem for me...i prefer to install things from official repo only to maintain my system stability and preent any crashes during upgrade....

---

### Post by cyneuron on 2007-11-12
just went to install opera....it has libqt2-mt as dependecy...in its description :

Qt GUI Library (Threaded runtime version), Version 3 
This is the Trolltech Qt library, version 3. It's necessary for
applications that link against the libqt-mt.so.3, e.g. all KDE3
applications.


about prozgui, its not available in Ubuntu repo...

about multiget, its not available for Gutsy....

---

### Post by maybeway36 on 2007-11-12
Then use KGet. I know its KDE, but it works well with FlashGot (and I use KDE so its an obvious choice for me.)

---

### Post by snowjm on 2007-11-12
I may be mistaken, but I was sure there is a firefox option that allowed you to continue downloading files even after you closed the browser, though I think it may require installing the  Download Statusbar plugin (which is probably the best plugin ever :p)

---

### Post by cyneuron on 2007-11-12
> **Vivaldi Gloria said:**
> Try multiget:

multiget.sourceforge.net

By the way, flashgot can pass the links from firefox to gwget without a problem in my gutsy. I don't know why yours cannot.
.

it is passing, but Gwget is unable to process the download link. its not a direct link to .mp4 file it refer to. surprisingly, even the firefox download manager can get the link and start downloading file but Gwget not....

---

### Post by original_jamingrit on 2007-11-12
To the OP:
    If you're willing to spend so much time looking for a download manager, why don't you also at least try the **native** command line wget?  I'm pretty sure it supports download resuming.  Plus it's pretty much as low as it gets when it comes to resource management.
```
man wget
```
simply use ```
 wget http://whatever.com/video.avi
```
and then ```
wget **-c** http://whatever.com/video.avi
```
to resume that file's download in the same directory.
Try it on for size.  Even though it has no GUI, it's simple enough.  You may like it, or at least use it as a temporary stand-in.

---

### Post by revolve on 2007-11-12
I love wget. It seems much faster than the downloader in Firefox.

---

### Post by kelvin spratt on 2007-11-12
wget works perfect with gnome its in the repros I use it all the time never had a problem. As does webdownloader for X nice gui supports resume upto 100 tries and multy downloads in the repro.

---

### Post by K.Mandla on 2007-11-12
[axel]("http://packages.ubuntu.com/axel") is wicked fast, but probably won't download videos from Google.

---

### Post by FG123 on 2007-11-12
[https://addons.mozilla.org/en-US/firefox/addon/4318](https://addons.mozilla.org/en-US/firefox/addon/4318)

Use the extension on a Google Video site to provide you with a link, then stick the link into your favorite download manager.

---

### Post by LaRoza on 2007-11-12
> **cyneuron said:**
> have got opera recommended for this purpose for the first time.....does opera support resuming even after restarting Ubuntu....


Yes. As long as the file (what has been downloaded so far) is still there. I have used Opera Portable to download something on the school's computer a little at a time over the course of several days. Just go to the transfers page (Tools->Transfers) right click the transfer, and stop it. Resume it the same way.

---

### Post by daengbo on 2007-11-12
Gnome (Ubuntu's desktop) has a built-in dowload manager in Epiphany, the default browser for Gnome. It allows you to pause and resume, creates a nice little progress bar in the notification area, and generally handles this all seamlessly.

[Install Epiphany]("apt:epiphany-browser") and [the extensions]("apt:epiphany-extensions"), and you won't need to do anything else. All of the common Firefox extensions are available as Epiphany extensions, too.

---

### Post by cyneuron on 2007-11-13
i have tried all such firefox addons......most of them either don't work or few works like unplug, and Video Download Helper, all of them give download lin similar to as you get by directly clicking Download Video on Google video. This link is not the direct link to video file on google serve rather it redirects the download client, which is where Gwget is failing.....

---

### Post by MRiGnS on 2007-11-13
> **cyneuron said:**
> i have tried all such firefox addons......most of them either don't work or few works like unplug, and Video Download Helper, all of them give download lin similar to as you get by directly clicking Download Video on Google video. This link is not the direct link to video file on google serve rather it redirects the download client, which is where Gwget is failing.....

flashgot + d4x is working fine here, so is gwget and kget.

when I want to download googlevids for example with the  I copy the link to [www.keepvid.com](www.keepvid.com) which does provide you with a regular download link.

keepvid also gives you the option to put it in your toolbar as a bookmark, opening the bookmark results in downloading google, youtube, metacafe videos in your active tab.

---

### Post by igknighted on 2007-11-13
> **cyneuron said:**
> just went to install opera....it has libqt2-mt as dependecy...in its description :

Qt GUI Library (Threaded runtime version), Version 3 
This is the Trolltech Qt library, version 3. It's necessary for
applications that link against the libqt-mt.so.3, e.g. all KDE3
applications.


about prozgui, its not available in Ubuntu repo...

about multiget, its not available for Gutsy....

Install it from the gutsy-commercial repo (uncomment it in sources.list).  It should handle the deps for you.  Just because it is built w/ qt doesn't mean it is a "kde app".  I mean, lots of the apps you list use window toolkits other than gnome's native gtk (like wx, for example).  It should only bring in qt, which is the windowing toolkit, and not any kde libraries.  Those are all separate.

And remember, wine is not an emulator, so you are not really "running" wine, just referencing the wine libraries.  So in most cases it shouldn't really be more resource hungry than the windows version (perhaps a little at times, but not much).

---

### Post by bruce89 on 2007-11-13
Download managers don't speed things up at all, they just kill servers.

---

### Post by cyneuron on 2007-11-13
> **MRiGnS said:**
> flashgot + d4x is working fine here, so is gwget and kget.

when I want to download googlevids for example with the  I copy the link to [www.keepvid.com](www.keepvid.com) which does provide you with a regular download link.

keepvid also gives you the option to put it in your toolbar as a bookmark, opening the bookmark results in downloading google, youtube, metacafe videos in your active tab.


i had already tried this....i am really frustrated....are you guys able to download google video by using the links provided by this site in D4X or Gwget ? 

both ae failing here....

---

### Post by pt123 on 2007-11-13
Multiget can do threaded downloads and hasn't crashed on me.

Works with Flashgot

---

### Post by macogw on 2007-11-13
I'd just use wget, and then if I want to resume, it's "wget -c <url>"

EDIT:
[quote=cyneuron]clicking Download Video on Google video. This link is not the direct link to video file on google serve rather it redirects the download client, which is where Gwget is failing.....[/quote]
You're right.  Google Video does stupid stuff with redirects instead of having the actual URL, so anything of a wget-nature fails with it.  It's pure idiocy, IMO.

---

### Post by zugu on 2007-11-14
Wget is so darn good I use the win32 port as my download manager of choice in WinXP.

And yes, the multithreaded downloaders just kill the servers.

---

### Post by cyneuron on 2007-11-14
> **macogw said:**
> 

EDIT:

You're right.  Google Video does stupid stuff with redirects instead of having the actual URL, so anything of a wget-nature fails with it.  It's pure idiocy, IMO.


does anybody know any workaround for this....?

---

### Post by MRiGnS on 2007-11-16
> **cyneuron said:**
> i had already tried this....i am really frustrated....are you guys able to download google video by using the links provided by this site in D4X or Gwget ? 

both ae failing here....

They do work for me, never had any problems.

EDIT: I made a short vid:

embeded in my blog= [http://ainotenshi.org/?p=36](http://ainotenshi.org/?p=36)

download = [http://files.ainotenshi.org/blam.ogg](http://files.ainotenshi.org/blam.ogg)

---

### Post by ice60 on 2007-11-16
you can use the firefox extension called cache viewer to get the urls for videos that are hard to get. for other videos you can use The All-In-One Video Bookmarklet. just drag it to your toolbar, then click on it to get the download urls
[http://1024k.de/bookmarklets/video-bookmarklets.html](http://1024k.de/bookmarklets/video-bookmarklets.html)

here's what it looks like for a google video, i just clicked that button that says vid save (sorry if there's anything inappropriate in the screenshot.)

[[img]http://xs221.xs.to/xs221/07465/Screenshot.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs221&d=07465&f=Screenshot.png)

EDIT firefox has a greasemonkey script too if you want it, but it puts a yellow bar at the top of the screen so you can click that to get the download links. here's an old picture i found showing the script for the download links -

[[IMG]http://img176.imageshack.us/img176/9999/screenshot2sp0.th.png[/IMG]](http://img176.imageshack.us/my.php?image=screenshot2sp0.png)

but, you can just 'watch' the video then get it out of the browser cache when it's finished downloading, it should be just as quick.

i got lots of cool buttons and userjs in opera. i made a thread with just a few of the things here, there's a nice youtube script.
[http://www.wilderssecurity.com/showthread.php?t=185624](http://www.wilderssecurity.com/showthread.php?t=185624)

i would do a howto for cool opera things, but the last howto for opera i did didn't get posted, so i won't lol

---

### Post by ice60 on 2007-11-16
i didn't say, but i use wget, it's really, really good. check out these -
wget --help
info wget
man wget

i was just looking for a picture of prozgui at google image search and i found 2 pages with loads of download managers, it looks spanish though, but if you click on the links for the home pages, they are in English.
[http://www.tuxresources.org/portal/modules/wfdownloads/viewcat.php?cid=73](http://www.tuxresources.org/portal/modules/wfdownloads/viewcat.php?cid=73)

---

### Post by seshomaru samma on 2007-11-18
can you wget a yousendit.com file?

---

### Post by happysmileman on 2007-11-18
> **bruce89 said:**
> Download managers don't speed things up at all, they just kill servers.

Download accelerators kill servers, but download managers download the same way a browser does, just supports continuing and pausing AFAIK?

Or is there something I'm not thinking about?

---

### Post by shafin on 2007-12-01
> **happysmileman said:**
> Download accelerators kill servers, but download managers download the same way a browser does, just supports continuing and pausing AFAIK?

Or is there something I'm not thinking about?
No,a browser downloads a file continuously,starting from the start,and ending at the end.On the other hand,download accelerators download separate chunks of the same file simultaneously, thus increasing speed,and server load.

---

### Post by CouchMaster on 2007-12-01
*Finally i had to boot into Windows XP and download files using Flashget....*

One of the reasons I keep Windows around - in all of the years I've been downloading things Flashget (ver. 1.3 I think) has never let me down.  It's the most bullet proof program I've ever used!  Rain ,sleet, hail, thunder storms, gloom of night - geeze....

---

### Post by cookies on 2007-12-01
> **cyneuron said:**
> just went to install opera....it has libqt2-mt as dependecy...in its description :

Qt GUI Library (Threaded runtime version), Version 3 
This is the Trolltech Qt library, version 3. It's necessary for
applications that link against the libqt-mt.so.3, e.g. all KDE3
applications.


about prozgui, its not available in Ubuntu repo...

about multiget, its not available for Gutsy....

Qt != KDE. It's one qt dependency. [If you don't like it, get the static build (It will look like **** though)](http://www.opera.com/download/get.pl?distro=other%2Fstatic+deb&id=29921%2C29920&location=40&sub=++++&x=147&y=15)

---

### Post by chrismine on 2008-01-02
Did you try wxDownload Fast?

It's not perfect and sometimes crash but since I limited the download speed it works nicely. Don't know about Youtube video's though.

---

### Post by kpkeerthi on 2008-01-02
> **CouchMaster said:**
> *Finally i had to boot into Windows XP and download files using Flashget....*

One of the reasons I keep Windows around - in all of the years I've been downloading things Flashget (ver. 1.3 I think) has never let me down.  It's the most bullet proof program I've ever used!  Rain ,sleet, hail, thunder storms, gloom of night - geeze....

Can you tell me what is that you are missing in d4x that Flashget has?

---

### Post by capink on 2008-01-02
> **Vivaldi Gloria said:**
> Try multiget:

multiget.sourceforge.net



multiget is good but it has a problem with windows filesystems like fat32. Apparently it keeps trying to set permissions on those filesystems and then it reports that it failed.

---

### Post by capink on 2008-01-02
The combination of wget and screen makes me able to continue downloading when X crash. And according to what I read on the screen manual, the download continues even if the current user logged out.

---

### Post by deebocean on 2008-08-14
> **Vivaldi Gloria said:**
> 
 You can make flashgot support MulltiGet by adding a new downloader in flashgot's settings menu with the path /usr/bin/MultiGet and the pass option [url=URL] [refer=REFERER].

thanks so much for this info, i need it.
> **Vivaldi Gloria said:**
> 
 I want to use linux programs with the linux feel and look. Wine sucks. Besides, the repos and program updates are the strong point of linux.

and i am absolutely with you in this matter. if you gonna you use a linux distro. then feel it and live it and enjoy it. and forget windows :).

---

### Post by artir on 2008-08-14
MultiGet FTW!!

---

### Post by RATM_Owns on 2008-08-14
Oh, about downloading videos, I'm almost positive they all appear in /tmp. So you can just drag them out of there.

---

