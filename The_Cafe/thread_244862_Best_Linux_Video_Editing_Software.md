---
title: "Best Linux Video Editing Software?"
date: 2006-08-27
forum: The Cafe
---

### Post by BOBSONATOR on 2006-08-27
Hey, guys, i use Sony Vegas 6 on XP, just wondering, is there an equivilant or better for linux?

Thanks.

---

### Post by BitTorrentBuddha on 2006-08-27
Most people would say Kino, but it's a KDE native app, of course that works to your advantage if you're running KDE.

---

### Post by drucer on 2006-08-27
[http://en.wikipedia.org/wiki/Cinelerra](http://en.wikipedia.org/wiki/Cinelerra)

---

### Post by pelle.k on 2006-08-27
Video editing, music making, and gaming is three things i dual boot for.
There's no way _any_ video editing app in linux even comes close to the complexity, and ease of use of Sony Vegas.

If you wan't to do some serious video editing using linux, then prepare to get your hands dirty, (it can be done) but in my world it's not even worth it. Sorry. I wish it wasn't so.

---

### Post by drucer on 2006-08-27
Here you can find Cinelerra Ubuntu installation instructions:

[http://www.kiberpipa.org/~gandalf/ubuntu/README](http://www.kiberpipa.org/~gandalf/ubuntu/README)

Some screenshots:

[http://www.heroinewarrior.com/cinelerra_shots.php3](http://www.heroinewarrior.com/cinelerra_shots.php3)

---

### Post by %hMa@?b&lt;C on 2006-08-27
another vote for cinelerra

---

### Post by DoctorMO on 2006-08-27
Cinerella is nice, and does everything I like but it's the devil to install on ubuntu and I wish the main prgrammer wasn't so stuck up, aparently his gui is holy than thou and doesn't even want to improve his shoddy icon set with improved tango icons so it'll never look 'intergrated' or even well produced.

Fork + Gtk2 + Tango + Mencoder = Cinerella2

---

### Post by NoTiG on 2006-08-27
what about Pitivi ? [http://pitivi.sourceforge.net/]("http://pitivi.sourceforge.net/")

---

### Post by FISHERMAN on 2006-08-27
> **DoctorMO said:**
> Cinerella is nice, and does everything I like but it's the devil to install on ubuntu

1. Enable universe, multiverse and restricted

Make sure you have following line uncommented in your /etc/apt/sources.list

for breezy:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse restricted

for dapper:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse restricted

2. Add mjpegtools ubuntu backport

for breezy:

deb [http://www.kiberpipa.org/~gandalf/ubuntu/breezy/mjpegtools](http://www.kiberpipa.org/~gandalf/ubuntu/breezy/mjpegtools) ./

for dapper:

deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools) ./

3. Add cinelerra build for your arch:

for breezy:

- i686:
    deb [http://www.kiberpipa.org/~gandalf/ubuntu/breezy/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/breezy/cinelerra/i686/) ./
- athlonxp:
    deb [http://www.kiberpipa.org/~gandalf/ubuntu/breezy/cinelerra/athlonxp/](http://www.kiberpipa.org/~gandalf/ubuntu/breezy/cinelerra/athlonxp/) ./
- pentium4:
    deb [http://www.kiberpipa.org/~gandalf/ubuntu/breezy/cinelerra/pentium4/](http://www.kiberpipa.org/~gandalf/ubuntu/breezy/cinelerra/pentium4/) ./

for dapper:

- i686:
    deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/) ./
- athlonxp:
    deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/athlonxp/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/athlonxp/) ./
- pentium4:
    deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/) ./

Installation:

apt-get update
apt-get install cinelerra

Certainly not that hard

---

### Post by trotski on 2006-08-27
Kino is a GTK+ 2.0 app, NOT a KDE one.

---

### Post by kievking on 2006-08-27
Thanks Fisherman - that was an easy installation

---

### Post by nalmeth on 2006-08-27
Avidemux has been doing everything I need it to..
It's probably not the 'best' but it works quite well for me

---

### Post by danielph on 2006-09-14
Cinerella - when playing a video I could not stop it - does not respond to any stop buttons and will not shutdown without  being forced. Strange that this app did work for me a few months ago, but seem to have a little bug now. Anyone else get this problem?
EDIT: Problem Solved
This happens when using the ALSA sound driver. Switch to OSS and there is no problem

Lives - does not load
GOPchop - corrupts mpg's (noticable when you use dvdauthor after chopping)
Diva - need to try this, but install was long
Jahshaka - could not work out the interface and how to edit videos. I don't think it works, but I may have missed something. After 1 hour I gave up.
Pitivi - would not edit a file - still early days for this app.
Kino - good for avi or dv
avidemux - i love this app, will not work with raw mpg, needs index and can cause AV sync problem

So the best, well for me avidemux at the moment for simplicity and some good features, but the others hold a lot of promise. I know Cinelerra has a lot of features, but I am not keen on the interface.

Edit: Also there is t@b ZS4 - but this does not import mpg in Linux

---

### Post by Grey on 2006-09-14
Chalk up another vote for Cinelerra.  I have used both Cinelerra and Adobe Premiere.  I very much preferred Cinelerra.

---

### Post by ogden_freen on 2006-09-18
The best I've used on Linux is Flint. But as far as free stuff goes...

Cinelerra seems the best, and that's really depressing.
SUCH A TERRIBLE INTERFACE!!
Nobody will ever do any colour grading on a tropical coloured GUI like that, the whole layout provides for a ridiculously cumbersome workflow and as has been pointed out earlier, the developer lives in his own world and doesn't seem willing to fix anything.

Jahshaka...
Don't even bother. It is not worth the download. They've spent far more effort on the look (including a slick website and splashscreen contest) than actually making it WORK.
DON'T BE FOOLED!
Despite their attempts to make it look like Combustion, it sure as heck aint. 
This REALLY steams me as I feel it gives open source a bad name. :mad:  I understand that these guys have had a fair bit of money and technology thrown at them to get it right.

So that leaves...
Blender. =D> 
The saving grace. Just add documentation. (which they are)
Once the docs are here, this will be the best bet by far.

So basically, keep your dual boot for now, but in a year or so...
Who knows?

---

### Post by cosine7 on 2006-11-05
> **FISHERMAN said:**
> 1. Enable universe, multiverse and restricted

Make sure you have following line uncommented in your /etc/apt/sources.list

for breezy:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse restricted

for dapper:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse restricted

2. Add mjpegtools ubuntu backport

for breezy:

deb [http://www.kiberpipa.org/~gandalf/ubuntu/breezy/mjpegtools](http://www.kiberpipa.org/~gandalf/ubuntu/breezy/mjpegtools) ./

for dapper:

deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools) ./

3. Add cinelerra build for your arch:

for breezy:

- i686:
    deb [http://www.kiberpipa.org/~gandalf/ubuntu/breezy/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/breezy/cinelerra/i686/) ./
- athlonxp:
    deb [http://www.kiberpipa.org/~gandalf/ubuntu/breezy/cinelerra/athlonxp/](http://www.kiberpipa.org/~gandalf/ubuntu/breezy/cinelerra/athlonxp/) ./
- pentium4:
    deb [http://www.kiberpipa.org/~gandalf/ubuntu/breezy/cinelerra/pentium4/](http://www.kiberpipa.org/~gandalf/ubuntu/breezy/cinelerra/pentium4/) ./

for dapper:

- i686:
    deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/) ./
- athlonxp:
    deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/athlonxp/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/athlonxp/) ./
- pentium4:
    deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/) ./

Installation:

apt-get update
apt-get install cinelerra

Certainly not that hard

That worked for me thanks.... Anyonw know where a good howto is, talk about steep learning curve....

---

### Post by amonsul on 2006-11-11
Hey, keep an eye on [http://kdenlive.sourceforge.net/screenshots.php]("http://kdenlive.sourceforge.net/screenshots.php")

---

### Post by uuwatti on 2006-11-13
hey thanks for pointing out kdenlive, will try it soon. (btw. i keep list of all editing apps i can find on art & design section of this forum.) [http://www.ubuntuforums.org/showthread.php?t=293798](http://www.ubuntuforums.org/showthread.php?t=293798)

---

### Post by dbbolton on 2006-11-13
yeah, i definitely don't like cinelerra's interface. it seems like it has many features. now, if i could just figure out how to use them.

---

### Post by dad311 on 2006-11-13
Has anyone tried LiVES?

[http://lives.sourceforge.net/index.php?do=home](http://lives.sourceforge.net/index.php?do=home)

---

### Post by dbbolton on 2006-11-15
[http://www.robfisher.net/video/](http://www.robfisher.net/video/)


word.

---

### Post by blaine00 on 2006-11-17
Cinelerra does have a terrible interface... and for some reason it would not encode videos correctly for me. Of course, this was in Freespire, which I have not used for about 6 months and I have yet to get it for Ubuntu.

Speaking of which, is there a repo for installing Cinelerra for Edgy? If not, would the Dapper repo work?

---

### Post by EdThaSlayer on 2006-11-17
I use Avidemux, but that only handles mpegs and avi files and can't really do all the complex stuff such as video effects(according to my current knowledge).

---

### Post by sw_ on 2006-11-19
> **blaine00 said:**
> Cinelerra does have a terrible interface... and for some reason it would not encode videos correctly for me. Of course, this was in Freespire, which I have not used for about 6 months and I have yet to get it for Ubuntu.

Speaking of which, is there a repo for installing Cinelerra for Edgy? If not, would the Dapper repo work?

I just installed it on Edgy using the Dapper instructions. works perfectly.:D

---

### Post by ububaba on 2006-11-26
> **sw_ said:**
> I just installed it on Edgy using the Dapper instructions. works perfectly.:D

You are really lucky.:-k  I can't install it even on Dapper. See below

> [COLOR="Blue"]
$ sudo aptitude install cinelerra
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  cinelerra libquicktimehv
The following NEW packages will be automatically installed:
  fftw3 libguicast libmpeg3hv
The following NEW packages will be installed:
  fftw3 libguicast libmpeg3hv
0 packages upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 13.9MB of archives. After unpacking 30.8MB will be used.
The following packages have unmet dependencies:
  cinelerra: Depends: libiec61883-0 which is a virtual package.
             Depends: libraw1394-8 which is a virtual package.
  libquicktimehv: Depends: libfaac0 (>= 1.24+cvs20060416) but 1.24clean-0ubuntu4 is installed.
                  Depends: libfaad2-0 (>= 2.0.0+cvs20060416) but 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
cinelerra [Not Installed]
libquicktimehv [Not Installed]

Score is 8[/COLOR] 

---

### Post by bayvista on 2006-12-15
Not that hard?? please comment on the following:
david@linuxpc:~/Desktop$ sudo apt-get update
Err http: //www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools Release.gpg
  Unable to connect to  http:
Ign http: //www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools Release
Ign http: //www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools/./ Packages
Err http: //www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools/./ Packages
  Unable to connect to  http:
Ign [http://www.kiberpipa.org](http://www.kiberpipa.org) ./ Release.gpg
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:2 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ign [http://www.kiberpipa.org](http://www.kiberpipa.org) ./ Release
Get:4 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release
Ign [http://www.kiberpipa.org](http://www.kiberpipa.org) ./ Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Err [http://www.kiberpipa.org](http://www.kiberpipa.org) ./ Packages
  404 Not Found
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/multiverse Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/multiverse Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/multiverse Packages
Get:5 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main Sources [47.9kB]
Get:6 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Get:7 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/universe Sources [3530B]
Get:8 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/multiverse Sources [427B]
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports/multiverse Sources
Fetched 51.9kB in 4s (10.5kB/s)
Failed to fetch http:/dists///www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools/Release.gpg  Unable to connect to  http:
Failed to fetch http:/dists///www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools/.//binary-i386/Packages.gz  Unable to connect to  http:
Failed to fetch [http://www.kiberpipa.org/~gandalf/ubuntu/cinelerra/i686/./Packages.gz](http://www.kiberpipa.org/~gandalf/ubuntu/cinelerra/i686/./Packages.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
david@linuxpc:~/Desktop$

---

### Post by jeremy on 2006-12-15
> **dad311 said:**
> Has anyone tried LiVES?

[http://lives.sourceforge.net/index.php?do=home](http://lives.sourceforge.net/index.php?do=home)

I tried it, I thought that DiES would be a better name!

---

### Post by DoctorMO on 2006-12-15
> I tried it, I thought that DiES would be a better name!

It's not even version 1 yet!

---

### Post by steven8 on 2006-12-15
> [QUOTE]Quote:
I tried it, I thought that DiES would be a better name!  

It's not even version 1 yet![/QUOTE]

Well, maybe they could make that change when it goes 1.0! :-)  Lives looks nice, though.

---

### Post by LewisDre4m on 2009-12-16
I see this question was written a while ago but to my surprise not too much updated info is out there considering how much things have changed.

There are several different options for different things but If I can just write my personal preference and what I use it for I hope this helps someone.

For basic all the way through to advanced video editing "Pitivi" Is the best hands down. I also believe it is the future of video editing on Linux especially now it has good funding. 

It is the nicest looking editor with a easy interface and I find the program very stable.

Hope this helps 

LewisDre4m

---

### Post by plurworldinc on 2009-12-16
Since I am also a huge fan of Sony Vegas, the closes thing I have found was Kdenlive. If you are coming from Vegas and want a program that comes with a very little to no learning curve to get started with.

---

### Post by gmjs on 2009-12-16
I've not tried it, but it reads very well on the website:

[http://www.openshotvideo.com/]("http://www.openshotvideo.com/")

---

### Post by Excedio on 2009-12-16
Why do I feel one of these coming?
 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=78059&stc=1&d=1216310936[/IMG]

---

### Post by sudoer541 on 2009-12-16
the best video editing is open shot! look @ my sig! Njoy!

---

### Post by Gizenshya on 2009-12-16
thanks for bumping the thread, it is a good one to work from.

Others please also post your experiences and opinions on recent developments.

The only one I've used so far is avidemux, which is ok.  It doesn't have too much functionality, but it is ok.  Well, and it somehow corrupts every video I make with purple pixels at scene transitions, like it doesn't make key frames properly at transitions or something.  If I can figure that out it'll be great for general editing.  I love how I can get to the exact frame I want, and everything seems very intuitive.  I've tried doing stuff like that with Premeire and finally got frustrated and gave up (though it was 6.5 atm...).

I'm going to make a decision to install one based on what people say here :)

---

### Post by danielph on 2009-12-17
Over 3 years since I last posted on this thread. Where did that go? I have mostly been using Kino for editing purely to get work done. It is stable and easy to use. For the future kdenlive is looking like my favourite. It is maturing nicely and becoming more stable.

---

### Post by mgmiller on 2009-12-19
I have tried a lot of linux video editors over the last few years.  The best by far is the current version of openshot.  They have a .deb for installing, or the best way is to add their ppa repository and let it update itself with everything else.  

The development speed is nothing short of amazing over the last year.  It does all kinds of effects, even chroma keying.  The interface is fairly straight forward and easy to learn.  The best way is to read the openshot blog.  Every time a new feature is added, it's explained in detail in the blog.

[http://www.openshotvideo.com/](http://www.openshotvideo.com/)

---

### Post by cne007 on 2009-12-19
you can try kdeenlive, it<s for kde but works fine under gnome.

[http://www.kdenlive.org/features](http://www.kdenlive.org/features)

---

### Post by pluto4ps on 2009-12-20
Kdenlive is the best....

---

### Post by diablo75 on 2009-12-20
I like Kdenlive myself.  Used it to make a slide show (but I would recommend against using the built in "create a slideshow" feature; it's unreliable/unstable/unpredictable.  It's easier to just drag and drop individual pictures in to the timeline and apply the transitions manually.  A show with about 120 pictures took me about 30 minutes to make and the results were worth the effort.

Editing video, from the looks of the tutorial videos I've seen on the net, are also a snap.  Really the only thing Kdenlive doesn't have going for it are more advanced effects, the likes of things you would find in Adobe After Effects (the true king of video editing software, IMO).  Kdenlive works great for most projects.

---

