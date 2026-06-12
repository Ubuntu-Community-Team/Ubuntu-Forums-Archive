---
title: "Ubuntu Studio is out."
date: 2007-05-10
forum: The Cafe
---

### Post by MetalMusicAddict on 2007-05-10
Someone has hijacked the [http://mirror.imbrandon.com/ubuntustudio/7.04](http://mirror.imbrandon.com/ubuntustudio/7.04) mirror. **[COLOR="Red"]IT IS BULL$H!T.[/COLOR]** Dont pay for downloads. This should be sorted soon. Its just some *** trying to make money.

We will let you guys know when its clear.

Well, its out...  [http://ubuntustudio.org](http://ubuntustudio.org)

> [SIZE="1"]Ubuntu Studio is a multimedia editing/creation flavour of Ubuntu. It's built for the GNU/Linux audio, video, and graphic enthusiast or professional.

The Ubuntu Studio team is proud to announce its first release: 7.04 for Intel i386-compatible processors. With this release, which you can download for DVD in little over 860 MiB, we offer a feature that is somewhat reminiscent of Ubuntu Server: on installation, you can choose between the Audio, Graphics or Video tasks; and choose also to install a number of plugins, which for this release is mainly aimed at audio production.

We have endeavored to keep as many of our packages in the standard Ubuntu repositories as possible. Certain packages, such as wired and our art packages, are kept in an external repository and fully up to Ubuntu packaging standards. Be aware however, that this is only a temporary solution and we will be pushing all our packages into Ubuntu for the next release.

The Audio task also provides a different kernel to the Video and Graphics tasks, which has low latency to enable easy JACK work, and for Gutsy we will be providing a fully realtime enabled setup. We have built upon the usability and support of Ubuntu as a foundation, and are certain that this was a wise choice, for we have access to a wide range of packages in the repository, and a stable base system.

For the video task, we have chosen the GStreamer-based PiTiVi as our central NLE. PiTiVi is written in Ubuntu's favourite scripting language, Python, and the GStreamer back-end enables it to use all the GStreamer-compatible codecs that are installed, and thus taking advantage of Feisty's Easy Codec Installation. It also uses our favourite widget set, GTK+, and thus keeps with the theme and flow of the Ubuntu Studio desktop, and tries also to stay usable in any environment, in keeping with Ubuntu Studio's aim that media production should be simple and accessible.

We have also packaged Ardour 2, which will debut on our disc. Our theme is heavily based around the dark style of Ardour and many other audio applications, and we are trying to have a release that is as integrated as possible with all of our applications and tasks.

Finally, the Graphics task deserves some attention. We have included a very wide range of very high quality applications that are also very well known. What we have done is added to this selection (with Enblend, for example), and brought them all together into a coherent set. Some main packages to note are the GIMP, Inkscape, Blender, Hugin and Scribus, which are all provided with a default install of the Ubuntu Studio Graphics task.

As our wiki page at [https://wiki.ubuntu.com/UbuntuStudio](https://wiki.ubuntu.com/UbuntuStudio) states: "Our aim is to make it more accessible for new users to get into the tools that GNU/Linux has to offer for multimedia creation/production. We also want to spotlight what's out there. Show users tools they might not have know existed." We have certainly fulfilled that aim with our first release with 7.04, and can only continue to improve.

Thanks to all who helped in Ubuntu Studios creation! Bring on the show![/SIZE]

The list of thank you's is really too large to get into. The team just sends a big THANX to the Ubuntu community. ;)

-Cory \m/

---

### Post by Wiebelhaus on 2007-05-10
sweet , grats and thanks.

---

### Post by ticopelp on 2007-05-10
Awesome! Thanks for the heads-up!

---

### Post by greenpete on 2007-05-10
Yeah, at last!
Thanks guys I really can't wait to try out the video editing app's.
Thanks so much for all your time and effort!

Peter:)

---

### Post by John.Michael.Kane on 2007-05-10
Cool! Will have to test it out.

Thanks.

---

### Post by MetalMusicAddict on 2007-05-10
***_MMA_ collapses from 6 months of no sleep. Goes into week-long coma.

---

### Post by greenpete on 2007-05-10
> **MetalMusicAddict said:**
> ***_MMA_ collapses from 6 months of no sleep. Goes into week-long coma.

No you must stay awake and celebrate your creation with us all!
Thanks MMA!

Peter:)

---

### Post by John.Michael.Kane on 2007-05-10
MetalMusicAddict I installed using the meta packages from the repos since i don't have dvd disks right now.

 I like how you give endusers darn near every program they would need to get going out of the box. + a low lat kernel to boot.  Nice theme/wallpapers too

Nice job.

---

### Post by tehkain on 2007-05-10
Wow just wow. Great stuff man. Now I need to find a project to use this power on.

---

### Post by caish5 on 2007-05-10
So, how do i install their theme?

---

### Post by justin whitaker on 2007-05-10
Fantastic work MMA! 


EDIT:

Wow, that sure is pretty, and has most of the packages I use. Might have to think about a full reinstall to get the fully Ubuntu Studio love.

---

### Post by atlien on 2007-05-10
Really don't know what to say about this.  Simply fantastic.  My video cam has been waiting, waiting, waiting for this!!!!!!

---

### Post by DoctorMO on 2007-05-10
Now I know where you've been hiding MMA

---

### Post by greenpete on 2007-05-10
> **caish5 said:**
> So, how do i install their theme?

I'm running it now!
If you gou go to the download page you will see the terminal commands to run...
sudo su -c 'echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list'

and

wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add - && sudo apt-get update

then run..
sudo apt-get install ubuntustudio-theme

Hope this helps, it worked for me!

Peter

P.S. Then change your theme in the normal way!

---

### Post by ticopelp on 2007-05-10
I can't seem to install it. I did:

```
sudo su -c 'echo deb http://archive.ubuntustudio.org/ubuntustudio feisty main >> /etc/apt/sources.list'

``` 

I then got an update from the update manager that there were new updates available.

But when I tried to install them,  I got this message:

> Please insert the disk labeled:
Ubuntu Studio 7.04 _Feisty Fawn_ - Release i386 (20070415)
in drive /cdrom/

I have DVD drive and a CD-ROM drive on my machine, but it demands I put the DVD in the CDROM drive, which, for obvious reasons, won't work. 

Any suggestions?

Edit: Trying to install using apt-get from the repositories results in the same prompt for the CD, again for the wrong drive. :/

---

### Post by MetalMusicAddict on 2007-05-10
[LIST]
[*]sudo su -c 'echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list'
[*]wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add - && sudo apt-get update
[/LIST]

Doing those 2 commands should get you access to our repo and it will pull that packages from there.

The only way you should get:
> Please insert the disk labeled:
Ubuntu Studio 7.04 _Feisty Fawn_ - Release i386 (20070415)
in drive /cdrom/
Is if you installed from our disk.

EDIT: Yes. If you did those commands right you will pull from our repo. I just did it on Etch. (just the wallpapers though)

---

### Post by maniacmusician on 2007-05-10
> **ticopelp said:**
> I can't seem to install it. I did:

```
sudo su -c 'echo deb http://archive.ubuntustudio.org/ubuntustudio feisty main >> /etc/apt/sources.list'

``` 

I then got an update from the update manager that there were new updates available.

But when I tried to install them,  I got this message:



I have DVD drive and a CD-ROM drive on my machine, but it demands I put the DVD in the CDROM drive, which, for obvious reasons, won't work. 

Any suggestions?

Edit: Trying to install using apt-get from the repositories results in the same prompt for the CD, again for the wrong drive. :/
Open your /etc/apt/sources.list and comment out all the CD entries at the top

---

### Post by maniacmusician on 2007-05-10
> **MetalMusicAddict said:**
> [LIST]
[*]sudo su -c 'echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list'
[*]wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add - && sudo apt-get update
[/LIST]

Doing those 2 commands should get you access to our repo and it will pull that packages from there.

Tho lony way you should get:

Is if you installed from our disk.
or if he installed originally using the Ubuntu disc and never commented out the CD entry.

---

### Post by greenpete on 2007-05-10
> **ticopelp said:**
> I can't seem to install it. I did:

```
sudo su -c 'echo deb http://archive.ubuntustudio.org/ubuntustudio feisty main >> /etc/apt/sources.list'

``` 

I then got an update from the update manager that there were new updates available.

But when I tried to install them,  I got this message:



I have DVD drive and a CD-ROM drive on my machine, but it demands I put the DVD in the CDROM drive, which, for obvious reasons, won't work. 

Any suggestions?

Edit: Trying to install using apt-get from the repositories results in the same prompt for the CD, again for the wrong drive. :/

Did you run...

wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add - && sudo apt-get update

as well? If not it's beyond me! Sorry.

Peter

---

### Post by ticopelp on 2007-05-10
> **MetalMusicAddict said:**
> [LIST]
Doing those 2 commands should get you access to our repo and it will pull that packages from there.

Tho lony way you should get:

Is if you installed from our disk.

I tried to install from disc first; when I put the DVD in, it said there were packages found on the DVD and asked if I wanted to open a package manager. I said yes, Synaptic fired up, popped up an error message about a missing GPG key (which I didn't save, unfortunately) and that was the end of that. 

> Open your /etc/apt/sources.list and comment out all the CD entries at the top

I will try this. Thanks very much.

---

### Post by ticopelp on 2007-05-10
Okay, that did the trick, and I am now downloading from the repos. Thanks for your help!

I'm still not sure how to get it running from DVD, but I guess I won't worry about it for now. :)

---

### Post by Mateo on 2007-05-10
I don't mean to be Mr Negative, but what's the point?  Aren't all of those applications available in the repos?  So what's different about this?

---

### Post by John.Michael.Kane on 2007-05-10
> **Mateo said:**
> I don't mean to be Mr Negative, but what's the point?  Aren't all of those applications available in the repos?  So what's different about this?

Please do not turn this thread into a what is the point thread.

This should explain why they made this version
[https://wiki.ubuntu.com/UbuntuStudio](https://wiki.ubuntu.com/UbuntuStudio)

---

### Post by human on 2007-05-11
Simply awesome. I love it already! 


My thanks goes out to all those who contributed to this project and put their hard work into this.

---

### Post by dhruva023 on 2007-05-11
great job man,

its away some

---

### Post by cmmike1 on 2007-05-11
I'm downloading it via torrent and i will seed it for a while for you guys. Best of luck.

---

### Post by hanzomon4 on 2007-05-11
Great news!!! 

Congrats I've been waiting so long for this, best of all for me I just fixed a sound issue I've been having with Ubuntu for over a year!! Do you think Jokosher will be read by Gusty? It doesn't matter I finally have a ubuntustudio.. YaY!!!!! :mrgreen:

EDIT:Can I seed torrents from the CLI? I ask because my family shares this computer and an X session wouldn't last as long as my TTYs.

---

### Post by jfinkels on 2007-05-11
Congratulations!

---

### Post by caish5 on 2007-05-11
```

I'm running it now!
If you gou go to the download page you will see the terminal commands to run...
sudo su -c 'echo deb http://archive.ubuntustudio.org/ubuntustudio feisty main >> /etc/apt/sources.list'

and

wget -q http://archive.ubuntustudio.org/ubuntustudio.gpg -O- | sudo apt-key add - && sudo apt-get update

then run..
sudo apt-get install ubuntustudio-theme

Hope this helps, it worked for me!

Peter

P.S. Then change your theme in the normal way!

```

Thanks, I knew that i was just having isues with the theme  menu. But all good now!

---

### Post by D!mon on 2007-05-11
are there any plans to release amd64 repos too? I want to install ya awesome theme :)

---

### Post by pirothezero on 2007-05-11
I will try to get a dnb friend of mine who makes some tunes as a hobby to try this out. I don't know if it would have/be able to have the modules of all the stuff he uses though.

I am curious to see what kind of work he can make from it.

---

### Post by Visceral Monkey on 2007-05-11
All I can say is, whoever did the artwork/splash and theme for this is awesome. It looks 10X better than the drab standard Ubuntu stuff.

---

### Post by hanzomon4 on 2007-05-11
Ah!! Seeding on the CLI with rtorrent

---

### Post by reclusivemonkey on 2007-05-11
I have absolutely zero creative talent, but I am very excited to see this released. Well done to everyone involved, it looks like there has been a huge amount of love poured into this. Excellent work!

---

### Post by xyz on 2007-05-11
Thank you. Looking forward to digging into it.

---

### Post by xyz on 2007-05-11
Why do I get this:

>  wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add - && sudo apt-get update
OK
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_US
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_US
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_US
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US    
Get:2 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release.gpg [189B]                   
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Translation-en_US                 
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Translation-en_US             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                         
Get:3 [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty Release.gpg [191B]                   
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty/main Translation-en_US                 
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release                                
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty/restricted Translation-en_US           
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty/universe Translation-en_US
Get:4 [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty Release.gpg [189B]
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages       
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:5 [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty-updates Release.gpg [191B]           
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty-updates/main Translation-en_US         
Ign [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty-updates/restricted Translation-en_US   
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty Release                      
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty-updates Release                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources              
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages                      
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Sources                           
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Sources                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources   
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_US   
Hit [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty Release                  
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty/main Packages               
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty/restricted Packages
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty/main Sources
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty/restricted Sources
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty/universe Packages
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty/universe Sources
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages
Hit [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Packages
Fetched 5B in 1s (4B/s)
Reading package lists... Done


---

### Post by maniacmusician on 2007-05-11
> **D!mon said:**
> are there any plans to release amd64 repos too? I want to install ya awesome theme :)
no 64-bit this time around

---

### Post by tgoose on 2007-05-11
Awesome news! Now I just need to get a second computer working..!

---

### Post by Gargamella on 2007-05-11
I think I will need to try it before judging, anyway the theme is awesome (i like murrine very much), I would like to know how to link my electric guitar and record on ubuntu...I am a noob in this field.
I think I will try it just to learn something.

Exellent job Ubuntu studio team!

---

### Post by aeiah on 2007-05-11
ah ive been looking forward to this. its a shame 64bit isnt supported in this release but not to worry, it looks like its a fantastic start. cant wait to have a play with it this weekend 8) 

so thankyou everyone who's been working on it

---

### Post by Smu on 2007-05-11
Hi!

Ubuntu studio looks great! I'm currently running Kubuntu Feisty and I would like to install all the Video and audio packages from ubuntu studio. How is this done?  And if I would install the complete Ubuntu Studio, would it mess up my current Kubuntu?

---

### Post by aeiah on 2007-05-11
> **Smu said:**
> Hi!

Ubuntu studio looks great! I'm currently running Kubuntu Feisty and I would like to install all the Video and audio packages from ubuntu studio. How is this done?  And if I would install the complete Ubuntu Studio, would it mess up my current Kubuntu?

once you've added the source list you should find them in the repository. if you were to install the complete ubuntu studio, you should either overwrite kubuntu, or dual boot like you would windows and linux (or triple boot...)

---

### Post by aeiah on 2007-05-11
oh, and ubuntustudio.org is down for me. im assuming its struggling a little. does anyone care to attatch the .torrent for the iso in here to give the server a fighting chance? :KS

---

### Post by bowmanr on 2007-05-11
Just to say "thank you" for your work. Looking forward to getting home, downloading, installing and getting to grips with Ardour.

Thank you very much.
Robert

---

### Post by Smu on 2007-05-11
Here's the torrent... :guitar:

---

### Post by misfitpierce on 2007-05-11
Yup and im helping seed.. More and more seeders are seeding it so download up and seed it at least a few weeks to get it widespread :)

---

### Post by Mechanical on 2007-05-11
Just found this out on digg.com and am loving it!  Thanks for all your hard work.

---

### Post by sengoku on 2007-05-11
absolute awesomeness :)

superb work cory, it looks amazing, and i've just installed it on my laptop with great success.

i have only one question - would it be at all possible to get an up-to-date copy of alsa-firmware in the repo at some time? i have an echo indigo io in my lappie (as i suspect a few musicians do) and all it takes it downloading alsa-firmware and doing ./configure && make && sudo make install, and the card starts working on the next reboot :)

either way, excellent work. thanks for enabling all the realtime and low latency stuff by default, and the colour scheme is just sexy :D

peace, love, and all that

---

### Post by D!mon on 2007-05-11
> **maniacmusician said:**
> no 64-bit this time around

Is it possible to install Ubuntu Studio theme on a 64bit? maybe compile from sources or something?

---

### Post by stijngysemans on 2007-05-11
and now the website is down :(

---

### Post by reclusivemonkey on 2007-05-11
> **stijngysemans said:**
> and now the website is down :(

The digg effect... torrents should be flying by now!

---

### Post by stijngysemans on 2007-05-11
> **reclusivemonkey said:**
> The digg effect... torrents should be flying by now!
yes, i'm also using the torrent now! better!

---

### Post by Sandsound on 2007-05-11
> **MetalMusicAddict said:**
> ***_MMA_ collapses from 6 months of no sleep. Goes into week-long coma.

Sleep tight :-) you and the rest of the team deserve it... Great job =D>

---

### Post by tikal26 on 2007-05-11
anyone knows if they are realeasing a 64 version of ubuntu studio?

---

### Post by BuffaloX on 2007-05-11
My wife is running it now, so she is busy.

It looks awesome.
Her desktop even looks better than my customized Beryl.

Sorry but I'm a sucker for cool desktops.
I know there are plenty "better" reasons for me to do the upgrade.

---

### Post by diskotek on 2007-05-11
after i opened ubuntustudio torrent file my my azureus dumped! i had this failure, anyone know something about it?

```
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  Internal Error (53484152454432554E54494D450E435050020F), pid=5691, tid=3084716944
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0-b105 mixed mode, sharing)
# An error report file with more information is saved as hs_err_pid5691.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)

```

---

### Post by BuffaloX on 2007-05-11
> **tikal26 said:**
> anyone knows if they are realeasing a 64 version of ubuntu studio?

No 64 bit version, this has already been discussed.

---

### Post by stijngysemans on 2007-05-11
> **diskotek said:**
> after i opened ubuntustudio torrent file my my azureus dumped! i had this failure, anyone know something about it?

```
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  Internal Error (53484152454432554E54494D450E435050020F), pid=5691, tid=3084716944
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0-b105 mixed mode, sharing)
# An error report file with more information is saved as hs_err_pid5691.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)

```
i use kTorrent, Azureus doesn't work fine for me in ubuntu!

---

### Post by DC@DR on 2007-05-11
This is awesome! Congrats, and thanks :-)

---

### Post by diskotek on 2007-05-11
may be i need to move to ktorrent...

---

### Post by spliskin on 2007-05-11
awesome!!! I've been waiting so long for this!!

many many thanks to the UbuntuStudio team! :guitar:  :popcorn:

---

### Post by enderokc on 2007-05-11
could someone please help me find the torrent?? or put the torrent file in a .zip format so I can download  it from my windows machine?? I tried searching the torrents and it doesnt come up.

any help would be great.

---

### Post by heimo on 2007-05-11
> **enderokc said:**
> could someone please help me find the torrent?? or put the torrent file in a .zip format so I can download  it from my windows machine?? I tried searching the torrents and it doesnt come up.

any help would be great.

Looks like it has been posted on this same thread as an archive. I have no idea if this is valid file. Probably is.
[http://ubuntuforums.org/showpost.php?p=2633944&postcount=45](http://ubuntuforums.org/showpost.php?p=2633944&postcount=45)

---

### Post by misfitpierce on 2007-05-11
Here is a ZIP... anything to help you get off windows :)

---

### Post by enderokc on 2007-05-11
Thanks!!

---

### Post by atlien on 2007-05-11
Been using Studio for the past 6 hours now. 

Get it.

---

### Post by moffatt666 on 2007-05-11
Sweet!  Now to find a use for it!

---

### Post by kdragon on 2007-05-11
how do i install it
i'm dual boot XP pro and Feisty 7.04 now

---

### Post by eriqk on 2007-05-11
Very cool! I think I can make some friends Very Happy with this. Oh, and myself, too.
/me starts seeding

Groet Erik

---

### Post by MetalMusicAddict on 2007-05-11
The site is seeing "The Digg effect" soon to be followed by "The /. effect". So ATM the site is down and we will have a simple page up soon.

Here are the links to the images:
[LIST]
[*][http://download.linuxaudio.org/ubuntustudio](http://download.linuxaudio.org/ubuntustudio)
[*][http://mirror.imbrandon.com/ubuntustudio/7.04](http://mirror.imbrandon.com/ubuntustudio/7.04)
[*][http://intelligentdancemusic.com/ubuntustudio](http://intelligentdancemusic.com/ubuntustudio)
[*][http://aehunter.net/Files/UbuntuStudio/](http://aehunter.net/Files/UbuntuStudio/)
[*][http://mir.zyrianes.net/ubuntustudio/7.04](http://mir.zyrianes.net/ubuntustudio/7.04)
[*][http://www.velmont.net/UbuntuStudio_7.04.torrent](http://www.velmont.net/UbuntuStudio_7.04.torrent)
[*][http://www.ubuntugids.be/UbuntuStudio_7.04.torrent](http://www.ubuntugids.be/UbuntuStudio_7.04.torrent)
[/LIST]

---

### Post by Macintosh Sauce on 2007-05-11
[COLOR="DarkGreen"]Downloading now to give it a whirl...[/COLOR]

---

### Post by altonbr on 2007-05-11
> **enderokc said:**
> could someone please help me find the torrent?? or put the torrent file in a .zip format so I can download  it from my windows machine?? I tried searching the torrents and it doesnt come up.

any help would be great.

WinRAR, 7Zip, WinZIP can all open a gunziped file. Gunzip isn't just for Windows.

> **MetalMusicAddict said:**
> The site is seeing "The Digg effect" soon to be followed by "The /. effect". So ATM the site is down and we will have a simple page up soon.

Here are the links to the images:
[LIST]
[*][http://download.linuxaudio.org/ubuntustudio](http://download.linuxaudio.org/ubuntustudio)
[*][http://mirror.imbrandon.com/ubuntustudio/7.04](http://mirror.imbrandon.com/ubuntustudio/7.04)
[*][http://intelligentdancemusic.com/ubuntustudio](http://intelligentdancemusic.com/ubuntustudio)
[*][http://aehunter.net/Files/UbuntuStudio/](http://aehunter.net/Files/UbuntuStudio/)
[*][http://mir.zyrianes.net/ubuntustudio/7.04](http://mir.zyrianes.net/ubuntustudio/7.04)
[*][http://www.velmont.net/UbuntuStudio_7.04.torrent](http://www.velmont.net/UbuntuStudio_7.04.torrent)
[*][http://www.ubuntugids.be/UbuntuStudio_7.04.torrent](http://www.ubuntugids.be/UbuntuStudio_7.04.torrent)
[/LIST]

Why is it getting resolved to 'nowhere'? It takes me to a German site sometimes...

---

### Post by John.Michael.Kane on 2007-05-11
> **altonbr said:**
> WinRAR, 7Zip, WinZIP can all open a gunziped file. Gunzip isn't just for Windows.



Why is it getting resolved to 'nowhere'? It takes me to a German site sometimes...

Those servers are probably getting hammered.

This one from the link you quoted seems to work.
[http://mirror.imbrandon.com/ubuntustudio/7.04/](http://mirror.imbrandon.com/ubuntustudio/7.04/)

---

### Post by sonnet on 2007-05-11
Hi guys I have a problem,if I click on [www.ubuntustudio.org](www.ubuntustudio.org) website i get not results.
Is the site down?
Can anyone post me a direct link to download or to the torrent file?
So there's no 64 edition?

---

### Post by MetalMusicAddict on 2007-05-11
> **sonnet said:**
> So there's no 64 edition?

Not yet.

---

### Post by stijngysemans on 2007-05-11
i'm installing it right now.
i'm really excited about this project, specially with the inclusion of the low-latency drivers!
let's :guitar:

---

### Post by heimo on 2007-05-11
> **sonnet said:**
> Is the site down?
Yes.

> **sonnet said:**
> 
Can anyone post me a direct link to download or to the torrent file?

It has been attached in this thread at least twice.

---

### Post by lakersforce on 2007-05-11
So when will the site be up?

---

### Post by kinetek on 2007-05-11
Heres a link to the official torrent from the website before it went down. 
I started seeding the torrent about 4am.
(Uploaded: 31299.4 MB)

[UbuntuStudio_7.04.torrent]("http://kinetek.org/xtra/UbuntuStudio_7.04.torrent")

---

### Post by raublekick on 2007-05-11
> **Smu said:**
> Here's the torrent... :guitar:

thank you, thank you, thank you! 

the site isn't working for me either (opendns returns some straaaange results)

i hope this will get the input on my pcmcia sound card working!

---

### Post by tgrisier on 2007-05-11
> **diskotek said:**
> may be i need to move to ktorrent...

I used to use utorrent when I was with that other OS and was tickled to find Ktorrent.  Looks like it and works like it.  It is waaaayyy better than anything else out there.  I don't think you'll be disappointed.

---

### Post by residualbit on 2007-05-11
all the downloads are alternate installs? is thats all thats out?

---

### Post by kpolice on 2007-05-11
Can anybody share the icons/theme ?

I don't use Ubuntu but I like them.

thx

---

### Post by mech7 on 2007-05-11
what is exactly different on this version other then theme ?

---

### Post by Visceral Monkey on 2007-05-11
I have a dumb question. Seeing as the .iso is dvd size only and I do not have a dvd burner, I'd like to try to install it using the .iso file in vm machine like vmware or virtualbox. However, how do I get it to install to the actual physical hard disk itself on a new partition and not a virtual drive? It seems it won't "see" my hard disks while installing it via vm. Anyone?

---

### Post by Bungo Pony on 2007-05-11
As a musician, I can assure you that I need to change my pants ;)

I can't wait to install it!

---

### Post by stkobe on 2007-05-11
To visceral monkey. I'm pretty sure that you cannot install it to your physical HardDrive from within a VM. You can only install it to a VM drive and by doing that you'll only be able to use ubuntustudio as a VM. Since the ustudio site is down, I'm not sure if they have  a CD version but if they do that might be an option. Also I've seen hacks somewhere for fitting 900MB onto a 700MB Cd, oh and also I think but not 100% sure that they do have physical 900MB CD media out there that you could purchase. Otherwise you might have to have someone burn it for you.

---

### Post by jariku on 2007-05-11
> **Visceral Monkey said:**
> I have a dumb question. Seeing as the .iso is dvd size only and I do not have a dvd burner, I'd like to try to install it using the .iso file in vm machine like vmware or virtualbox. However, how do I get it to install to the actual physical hard disk itself on a new partition and not a virtual drive? It seems it won't "see" my hard disks while installing it via vm. Anyone?

Try to install it with this howto: [http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html](http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html)

---

### Post by Hollunder on 2007-05-11
Or install Feisty and get the missing packages from the repos

Question: Is there a Ubuntu Studio board yet? Will there be one?

---

### Post by MetalMusicAddict on 2007-05-11
> **Hollunder said:**
> Question: Is there a Ubuntu Studio board yet? Will there be one?
The Ubuntu Forums will be used for general support and the "Multimedia Production" section will be the place to ask specific questions for things.

We will not have a Ubuntu Studio forums because it can create redundant, basic questions.


PS. Damn. Time to change my Avatar. :(

---

### Post by 71CH on 2007-05-11
anybody know how to upgrade from feisty using the repos?

---

### Post by Bakerconspiracy on 2007-05-11
Is anyone else getting a 403?

---

### Post by John.Michael.Kane on 2007-05-11
> **71CH said:**
> anybody know how to upgrade from feisty using the repos?

On their site it list these two commands

Command one:
sudo su -c 'echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list'

Command Two:
wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add - && sudo apt-get update

Next step open synaptic, and do a search for these files.

# ubuntustudio-desktop
# ubuntustudio-audio
# ubuntustudio-audio-plugins
# ubuntustudio-graphics
# ubuntustudio-video
# ubuntustudio-artwork
# ubuntustudio-gdm-theme
# ubuntustudio-icon-theme
# ubuntustudio-look
# ubuntustudio-session-splashes
# ubuntustudio-sounds
# ubuntustudio-screensaver
# ubuntustudio-theme
# ubuntustudio-wallpapers
# usplash-theme-ubuntustudio
# wired

If you have an nvidia card make sure you install linux-restricted-modules-2.6.20-15-lowlatency

Then you can reboot, and log in to ubuntustudio.

Hope this helps

If you have any issues just make a thread.

---

### Post by atlien on 2007-05-11
The last part of that last post was crucial.  If you have Nvidia card, you need linux-restricted-modules-2.6.20-15-lowlatency

Otherwise you won't be able to log into new UbuntuStudio upgrade after you install it.  At least I wasn't until I did that last step.  Was a little scared for a second, too.  lol

---

### Post by Visceral Monkey on 2007-05-11
> **MetalMusicAddict said:**
> The Ubuntu Forums will be used for general support and the "Multimedia Production" section will be the place to ask specific questions for things.

We will not have a Ubuntu Studio forums because it can create redundant, basic questions.


PS. Damn. Time to change my Avatar. :(

Ouch. No problem, i've removed it.

---

### Post by adarkmethod on 2007-05-11
i am :(

so... where can i get this now... seems like we've destroyed their website

---

### Post by MetalMusicAddict on 2007-05-11
> **Visceral Monkey said:**
> Ouch. No problem, i've removed it.

You didnt *have* to. I can always make a new one. ;)

---

### Post by episodic on 2007-05-11
> **atlien said:**
> The last part of that last post was crucial.  If you have Nvidia card, you need linux-restricted-modules-2.6.20-15-lowlatency

Otherwise you won't be able to log into new UbuntuStudio upgrade after you install it.  At least I wasn't until I did that last step.  Was a little scared for a second, too.  lol



If I have an 'older' geforce 3 nvidia card with the standard old 3d drivers - can I still do this? Thanks for any and all thoughts.

---

### Post by bren21 on 2007-05-11
What's with the 403 error when I try to access the website? I want it, I want it :(

---

### Post by kinetek on 2007-05-11
Well, I finally took the time to get it installed.

Easy installer (although the keyboard map detection was lengthy).
The theme is fantastic, and reminds me of an old blackbox theme I used.

I was surprised to see that my M-Audio Audiophile USB soundcard got detected. Just telling XMMS to use ALSA with the first USB Device got playback going.

I'll be posting later about how my other M-Audio gear (Trigger Finger, Oxygen) installs.

NVIDIA low-latency driver installed automatically. And this box is using a Geforce FX5200 128MB AGP.

New favorite distro?  Yeaaahh!

---

### Post by Hollunder on 2007-05-11
I'd be interested in how well your USB-soundcard works with jack.

---

### Post by Mblackwell on 2007-05-11
Yeah, so of course I automatically grabbed the audio meta since I wanted to mess with Ardour 2, but it won't start. It complains that it can't connect to JACK. Crazy thing is, the JACK Control Kit can't either. But running jackd -d alsa from the terminal works fine, it spits out:

```

jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback

```

And sits there, returning no errors. Ardour STILL won't start. Granted I haven't rebooted since installing the meta, and YES I'm running linux-lowlatency (have been since I installed Feisty).

---

### Post by JerseyShoreComputer on 2007-05-11
> **MetalMusicAddict said:**
> [LIST]
[*]sudo su -c 'echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list'
[*]wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add - && sudo apt-get update
[/LIST]

Doing those 2 commands should get you access to our repo and it will pull that packages from there.

The only way you should get:

Is if you installed from our disk.

EDIT: Yes. If you did those commands right you will pull from our repo. I just did it on Etch. (just the wallpapers though)

MMA has got it all correct. I just followed this and then used Synaptic Package Manager to install it. Less then 10 minutes later i am running Ubuntu Studio right now! it is pretty cool, thanks MMA!!

:guitar:

---

### Post by MetalMusicAddict on 2007-05-11
Mblackwell. Your question should be asked in "Multimedia Creation".

But to answer:

From a terminal: **sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'**

Then logout/in.

---

### Post by Patrick-Ruff on 2007-05-11
website isn't working . . .

---

### Post by Visceral Monkey on 2007-05-11
Sorry about the avatar. I was under the impression it was the logo for Ubuntu studio and was GPL, which is why I just clicked/saved and used it as an avatar. I certainly didn't mean to steal anything.  I thought it was the same thing as using the normal Ubuntu logo as an avatar.

---

### Post by MetalMusicAddict on 2007-05-11
> **Visceral Monkey said:**
> Sorry about the avatar. I was under the impression it was the logo for Ubuntu studio and was GPL, which is why I just clicked/saved and used it as an avatar. I certainly didn't mean to steal anything.  I thought it was the same thing as using the normal Ubuntu logo.

I never said you couldnt use it. :) I just want to have my own and you grabbed it. Oh well. Ill make another.

The logo is actually under the same license as the Ubuntu ones since Canonical is protecting it.

---

### Post by Acksys on 2007-05-11
Looks like a great job on this. Great to have all this stuff finally working for me together.

---

### Post by diskotek on 2007-05-11
> **MetalMusicAddict said:**
> I never said you couldnt use it. :) I just want to have my own and you grabbed it. Oh well. Ill make another.

The logo is actually under the same license as the Ubuntu ones since Canonical is protecting it.

i would like to use that avatar-logo &#305;n my website to spread-the-word. i'm still trying to re-configure linux-audio logo.... :(

---

### Post by bren21 on 2007-05-11
There seems to be a minor defect on the look of certain buttons on the task bar, it is not a big deal but I thought I might as well point it out. If you look at the attached image, you will see that two of the buttons mess up the gradient.

---

### Post by MetalMusicAddict on 2007-05-11
> **bren21 said:**
> There seems to be a minor defect on the look of certain buttons on the task bar, it is not a big deal but I thought I might as well point it out. If you look at the attached image, you will see that two of the buttons mess up the gradient.

Yeah. It seems random. Happens sometimes to me. Try adjusting your panel size a little or a logout/in might fix.

---

### Post by slimdog360 on 2007-05-11
403 forbidden, website get a pounding did it?

---

### Post by viper on 2007-05-12
Grab the torrent from here
[http://www.desktoplinux.com/news/NS7380291045.html](http://www.desktoplinux.com/news/NS7380291045.html)

---

### Post by 71CH on 2007-05-12
does upgrading from feisty mess anything up like beryl?

---

### Post by Frak on 2007-05-12
kudos, bout to have fun with this :)

---

### Post by ceelo on 2007-05-12
I got a broken X server error when I installed it. :(  I also had to install via text mode, was there a graphical installer for anyone?

---

### Post by Visceral Monkey on 2007-05-12
I've got some weird video lag. I've installed Ubuntu Studio and then used the Envy script for my 8800gts. But now, for some reason I get odd lag sometimes when opening or moving windows, with or without using berly. Do I need to not be using the low latency kernel with an 8800gts?

---

### Post by ceelo on 2007-05-12
Well I took a look at my UbuntuStudio's xorg.conf file from my Debian install and it seems it detected all of my hardware as generic. So I just copied my Debian xorg.conf file over the UbuntuStudio one and everything is working now. Huzzah! :guitar:

---

### Post by jariku on 2007-05-12
I installed Ubuntu Studio last night and so far I've been pleased (I haven't actually done anything useful yet, just been installing the stuff I need and configuring gnome). I did a clean install and wiped my Foresight Linux installation to make space for Ubuntu Studio goodness.

I'll move my Audacity projects from my laptop to this new setup soon and maybe one day I'll learn how to use the rest of the stuff that's included. :) 

Great job anyway, thanks!

---

### Post by starcraft.man on 2007-05-12
Hmmm, I was gonna install Ubuntu studio to give it a try today, and wanted to get a copy of the ISO... the site seems to be down though and its returning

error id: "bad_httpd_conf"

The site overloaded by users? down for maintenance?

---

### Post by lepz on 2007-05-12
I just installed it and really like it. looks really sleek, I havnt played with anything yet but first impressions AWESOME! 

Thank you everyone involved. :popcorn:

---

### Post by Kulgan on 2007-05-12
I had the same problem as ceelo on Dell laptop, solved it the same way. 

I saw the screenshots, of course, and loved the theme :D Actually using it seems to take some getting used to (all of about 5 hours, by now; less than it took to get used to linux the very first time!)

It's ubuntu, so it works, and it's got all the media management software I was trying to find in ubuntu. So it's perfect :D 

Thanks a lot. You've clearly put a lot of effort into making things work together, and that effort has yielded results. THANK YOU!

---

### Post by happy-and-lost on 2007-05-12
Nice. Runs a bit faster and much smoother with Compiz than normal Ubuntu. Good work :D

Theme's nice, but the Metacity borders are probably a bit fat for people at lower res... in any case...

Thanks!

---

### Post by ygarl on 2007-05-12
Yeah... appears temporily deceased, chaps.
I have a funny feeling that Ubustu is a LITTLE more popular than people thought it would be... which means that people have been looking for a really slick multimedia distro which isn't live for a long time!

Agnula was a good theory, but it's so out of date now it's starting to grow fungi!
Dyne:bolic works OK, but is a live distro which has no additional repos for other stuff (like Nvidia drivers etc...).
This is the best thing for studio recording on Linux - well - ever!

---

### Post by rajeev1204 on 2007-05-12
hi

Can anyone tell me how i can use a similar glossy theme ( i mean where can i get it )  for my default feisty desktop 



thanks

---

### Post by jiminycricket on 2007-05-12
[http://www.belutz.net/2007/05/11/installing-ubuntu-studio-theme/](http://www.belutz.net/2007/05/11/installing-ubuntu-studio-theme/)

[Ubustu ]("http://www.ubustu.com/globe/2007/05/11/download-mirrors-for-ubuntu-studio/")just posted about Ubuntustudio.org mirrors.

---

### Post by altonbr on 2007-05-12
> **Bungo Pony said:**
> As a musician, I can assure you that I need to change my pants ;)

I can't wait to install it!

My thread on VMWare player: [http://ubuntuforums.org/showthread.php?t=342631](http://ubuntuforums.org/showthread.php?t=342631)
VMWare Server: [http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)

---

### Post by homerj742 on 2007-05-12
Question, can you install these apps if you already installed Feisty?

---

### Post by aeiah on 2007-05-12
> **homerj742 said:**
> Question, can you install these apps if you already installed Feisty?

yes, they should be in the repos if you search for 'ubuntustudio'

---

### Post by jrcortez on 2007-05-12
No downloads anywhere! ubuntustudio.org has crashed im assuming because i cant get to it and theres only one mirror working at ubustu. I tried downloading it there but it was running HORRIBLY slow.

---

### Post by Frak on 2007-05-12
Use the torrent

---

### Post by Kulgan on 2007-05-12
Is [this]("http://mirror.imbrandon.com/ubuntustudio/7.04/") the mirror you were using?

---

### Post by jrcortez on 2007-05-12
Yes, thats the mirror i was using and i tried using the torrent but it was running just as slow.

---

### Post by zepfan on 2007-05-12
> **ceelo said:**
> I got a broken X server error when I installed it. :(  I also had to install via text mode, was there a graphical installer for anyone?

I've got the exact same problem. I've got a Dell 9300 laptop with a resolution of 1400x900 on an ati mobile radeon x300 64mb. I've installed a couple of *buntu's and never had this problem. Anyone have advice?

---

### Post by MetalMusicAddict on 2007-05-12
You guys are so nuts for it everythings slow. Just the way it is. The torrent I'm told is quite fast atm. Make sure you have your ports set right.

---

### Post by Frak on 2007-05-12
I can vouch for its speed, I got 1.5MB/s on it. The torrent is fine.

---

### Post by tehkain on 2007-05-12
Love the thing more and mroe each day. Anyone working on a firefox theme using the icons?

---

### Post by Tahi_Kiwi on 2007-05-12
I'm amazed that so many have been able to download Ubuntu Studio. Since Thursday, I have not even been able to access the main  Web site [http://ubuntustudio.org/](http://ubuntustudio.org/). It's always been "permission denied" or "unavailable".

The down mirrors at [http://www.ubustu.com/globe/2007/05/11/download-mirrors-for-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/11/download-mirrors-for-ubuntu-studio/) show a bunch of dead mirrors.

Has there been any official word on why nearly everything about Ubuntu Studio is down?

---

### Post by ffxr on 2007-05-12
the torrent has been linked on this thread about 6 times.

here: [http://www.ubuntugids.be/UbuntuStudio_7.04.torrent](http://www.ubuntugids.be/UbuntuStudio_7.04.torrent)

my first impressions are that its REALLY good btw.

& thanks to the developers, a lot of thought and effort has obviously went into the creation of this beautiful distro.

---

### Post by MetalMusicAddict on 2007-05-12
> **Tahi_Kiwi said:**
> Has there been any official word on why nearly everything about Ubuntu Studio is down?

Its been said a hundred times in many threads. You guys are so crazy for it you took the site down and most of the mirrors. The torrent should be fine.

The site will be back up soon as well as more mirrors.

---

### Post by jsmanness on 2007-05-12
Hello,

Could someone please tell me which partitioning option I need to select in order to partition my HD 50% XP and 50% ubuntustudio? I currently just have XP and I'm afraid to wipe my HD clean.

Thank you,

Jon

---

### Post by altonbr on 2007-05-12
> **rajeev1204 said:**
> hi

Can anyone tell me how i can use a similar glossy theme ( i mean where can i get it )  for my default feisty desktop 



thanks

There's a glossy theme in Ubuntu Feisty named "Glossy". It's fully customizable too. I'm not sure if this is the one you are referring to as I'm in the process of installing UbuntuStudio via VMWare Sever, but I use the glossy theme on my current Feisty build in a nice pastel mid-night blue.

---

### Post by hanzomon4 on 2007-05-12
Yeah the theme is good but could use some work, it actually reminds me of my favorite windowblinds/osx theme - [Shinobi](http://www.macthemes.net/articles/reviews/000065.php) 




[IMG]http://www.mathgamehouse.com/mt/themes/shinobi/preview.jpg[/IMG]

---

### Post by Frak on 2007-05-12
I just used UbuntuStudio and I am VERY PLEASED!
It has to be the most visualy beautiful distro I've used, and because its based off of Ubuntu, I know its quality.
Best Distro I've ever used, UbuntuStudio fills the vanity gap.
Kudos :) :) :) :)

---

### Post by MetalMusicAddict on 2007-05-12
***_MMA_ just hopes people find it as productive as pretty. (It has some visual quirks trust me, you'll find 'em)

---

### Post by Frak on 2007-05-12
Yes I found the quirks, but they don't bother me enough to make a difference, and yes, I do edit video and music for a local band (small profit, but its better than nothing, and a good hobbie), and I like the packages that are on this that I never knew existed. It has become very helpful in the arts portion of my work :).

---

### Post by jrcortez on 2007-05-12
Okay so i finally got the .ISO to download from a mirror i found using google and i burnt the dvd. I put it in a Pentium 4 Gateway and it booted up and i checked the cd for defects and everything was good but i didnt want to load it on that machine so i then put it in my Pentium 3 Sony Vaio. it starts to boot from the dvd then goes to a black screen. any ideas?

---

### Post by jiminycricket on 2007-05-12
Some reviews from tuxmachines:


[http://www.tuxmachines.org/node/16287](http://www.tuxmachines.org/node/16287)
> Ubuntu Studio 7.04 was finally released yesterday to what seemed like quite a bit of excitement. Ubuntu Studio is a version that focuses on multimedia creation and manipulation with what appears to me as an emphasis on music. At the time of this writing the official website seems to be experiencing a bit of trouble, perhaps due to the high traffic. In any case, sometimes the early bird does gets his worm and this time I was up early.

[http://www.thepcspy.com/articles/linux/review_ubuntu_studio_704](http://www.thepcspy.com/articles/linux/review_ubuntu_studio_704)
> Ubuntu Studio is a variant of Ubuntu that concentrates on three creative tasks: video editing, audio recording and graphics. The review covers the included software (or lack thereof, in some places), its installation and the theme used.

---

### Post by pixeldotz on 2007-05-13
[cries] i love ubuntu studio.

 - my alesis USB pnp mixer now works out-of-the-box (fresh installs of ALL other versions of ubuntu would not detect it.

- hp psc with scanner now works out-of-the-box (same as above, even with all the guides and installation stuff it would never work.

side note: does anyone know how i would migrate all my drivers and settings for my network from my 6.10 install over to ustudio? it took me forever to get my bcm wireless installed and working flawlessly and i would rather not have to go through that again.

---

### Post by Kulgan on 2007-05-13
Just a few questions about Compiz...

I have a really really boring Intel video card, no fancy nvida/ati drivers for me. 

I installed compiz from the repositories, as well as all the dependencies, then installed compiz-extras. I also installed desktop-effects to turn it on and off. That's all I did.

I get the box for desktop-effects, with the button, like in Fiesty, and the two options below. The wobbling works, and the windows bounce when I maximise them. The desktops do not, however, rotate on the nice cube thing (they just change without the box), nor can I zoom out to get multiple desktops in a strip. Previewing open windows by Ctrl-Alt-Up works. Opacity works, but I have to set it through individual programs, like in terminal, because none of the shortcuts that should be added to the shortcut settings box are there. 

None of the plugins from compiz-extras appear to be working either. 

I know I am most likely doing it all wrong, but is there someone who can tell me *what* it is I'm doing wrong. And mebbe how to fix it? 

Thanks,
-K

---

### Post by mpgarate on 2007-05-13
Im really excited!!!

-I can easily make music, video, images ect
-awesome theme
-im getting a new computer in 3 days, so perfect timing
-my hp psc also works now, and I didnt have to do anything!

YOU ROCK

any word on the site? its been down almost 24 hours i belive

---

### Post by %hMa@?b&lt;C on 2007-05-13
nice!!! love the work you put in.

just a heads up to everyone else. you dont need to down the entire iso, just add the ubuntustudio repos and do an "aptitude search ubuntustudio" and install those packages

---

### Post by MetalMusicAddict on 2007-05-13
> **mpgarate said:**
> any word on the site? its been down almost 24 hours i belive
It will be back up soon trust me. The Digg effect totally made Dreamhost flip out. Digg and Slashdot traffic will be blocked now.
> **jeffc313 said:**
> just a heads up to everyone else. you dont need to down the entire iso, just add the ubuntustudio repos and do an "aptitude search ubuntustudio" and install those packages

Well, this wont really get you our settings which are needed if you do sound work. We set some things when you install from our disk.

Also ubuntustudio-desktop will conflict with some things in ubuntu-desktop. ie: the -sounds. Though some people might want those. :)

---

### Post by brim4brim on 2007-05-13
I added the repos and installed the theme via Synaptic but it isn't showing up in the list of themes.

When I do a search for Ubuntu studio on my hard disk, I do see some UbuntuStudio stuff but a lot of it appears to be missing.  I didn't install Ubuntustudio-desktop, just theme, icons, splash and things like that.

Any idea what's wrong?

---

### Post by the.dark.lord on 2007-05-13
> **maniacmusician said:**
> no 64-bit this time around

*shakes his fist*

---

### Post by mpgarate on 2007-05-13
is 64 bit for amd 64?

---

### Post by m.musashi on 2007-05-13
Any thoughts on how I might be able to have Ubuntu Studio running on an edubuntu thin-client? If I understand correctly, Ubuntu Studio is using a different kernel so I'm not sure how you would do this. I am setting a thin-client up at my school and I think our music teachers and students could really benefit from this. I'd appreciate any feedback.

Also, I saw that hydrogen is part of the install, but  I need something to replace Finale. Is there such a thing? Sorry if that's a dumb question but I'm not a musician (lack of parental encouragement - long story) and my knowledge is rather cursory. 

Thanks.

---

### Post by NESFreak on 2007-05-13
> Site Temporarily Unavailable
We apologize for the inconvenience. Please contact the webmaster/ tech support immediately to have them rectify this.

error id: "bad_httpd_conf" 

I've recently heard canonical would start protecting it's trademarks. Which basically means every non-official whateverbuntu distro should change it's name. (here's marks post on his blog [http://www.markshuttleworth.com/archives/112](http://www.markshuttleworth.com/archives/112))

Wondering what this project is going to be named.

---

### Post by Kulgan on 2007-05-13
Or if it could just go official (I thought it was... it's definitely a grand improvement on the official Fiesty... )

-K

---

### Post by mpgarate on 2007-05-13
no 64 bit support - does that mean it will not run on my new amd 64 dual core?

---

### Post by heimo on 2007-05-13
> **mpgarate said:**
> no 64 bit support - does that mean it will not run on my new amd 64 dual core?

Both AMD and Intel 64 bit chips are able to run 32 bit code / operating systems.

---

### Post by mpgarate on 2007-05-13
i dont really know what im talking about here... but is it capable of it? and should I use the 64 version if/when its availible?

---

### Post by jariku on 2007-05-13
**You will be able to run it** in with your 64 bit processor and **if there's ever a 64 bit version, you'll get some benefits** from using that one instead of the 32 bit version.

---

### Post by Frak on 2007-05-13
> **mpgarate said:**
> i dont really know what im talking about here... but is it capable of it? and should I use the 64 version if/when its availible?
Only run 64 bit versions if your ready for some programs to be incompatable. x86/x64 are not cross compatable unfortunately. You can though install the 32-bit and be just fine, it will run 100%.

---

### Post by Incense on 2007-05-13
Any thoughts of putting out a Kubuntu studio? Studio looks amazing, and I would love to see what you would do under KDE. Thanks for all the work you put in to this.

---

### Post by Shibby73 on 2007-05-13
I am very excited to try this out!

I have a technical question on installing.

1st I did have an ubuntu install on a partition of my HDD and was dual booting into WINXP and UBUNTU.
However, when playing with some beryl install I messed up my configs and X-org stuff and trying to fix all of that messed up the Ubuntu I had installed too much for my intellect to fix.  I don't know how to wipe that partition so I can install again and with Ubuntu 7 (fiesty) or UbuntuStudio.

Please help.

Also this is on my laptop, I don't have a DVD burner, what should I do?

Basically I could download to my WinXP and burn a CD... but not a DVD and install from the CD/DVD drive.

Any help is appreciated, I really want to try this out ASAP.

Thank you,

Steve (shibby73)

---

### Post by ffxr on 2007-05-13
Shibby73, its probably gonna save you a whole load of hassle if you can find someone to burn the DVD for you.

as regards, removing your old install of ubuntu, the installation of ubuntustudio will make this really easy, as long as your careful , and it will especially easy if you have ubuntu and xp on seperate hard disks.

---

### Post by elchato on 2007-05-13
[www.ubuntustudio.org](www.ubuntustudio.org) temporarily unavailable?


...?

---

### Post by maniacmusician on 2007-05-13
> **Incense said:**
> Any thoughts of putting out a Kubuntu studio? Studio looks amazing, and I would love to see what you would do under KDE. Thanks for all the work you put in to this.
Not anytime in the near future. Probably never.

> **elchato said:**
> [www.ubuntustudio.org](www.ubuntustudio.org) temporarily unavailable?


...?

the digg effect. Took down their servers. it happens.

---

### Post by luisbg on 2007-05-13
sudo su -c 'echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list'
wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add - && sudo apt-get update


sudo apt-get isntall ubuntustudio-desktop


that should make the trick =)

---

### Post by sclough on 2007-05-13
> **MetalMusicAddict said:**
> 

Well, this wont really get you our settings which are needed if you do sound work. We set some things when you install from our disk.

Also ubuntustudio-desktop will conflict with some things in ubuntu-desktop. ie: the -sounds. Though some people might want those. :)

Ok, for someone that wants to install studio on a machine without a DVD drive, can someone clear this up for me.  If I want to end up with a studio install, not just themes and looks, should I just do a server install so that the desktop package is not installed and then apt-get the ubuntustudio-desktop meta package (or whatever it's called)?  If I try to install the meta package from xubuntu or ubuntu is it going to work correctly?  It sounds like there are many things that conflict between vanilla ubuntu and studio and it's not clear that if I run the meta package it will overlay everything correctly.

---

### Post by chunchengch on 2007-05-14
I have a nVidia GeForce GO 7300 (128MB) video card, I can set resolution 1200 x 800 out of the box for Feisty Fawn and Windows Vista, while Ubuntustudio limits it to only 1024 x 768, I tried to modify in **System>Preferences>Screen Resolution**, but there are only three options 1024x768, 800x600, 640x480.
how can I change it?

By the way, there are many options to boot Ubuntustudio, but I don't understand what is the difference between options "Ubuntu, kernel 2.6.20-15-lowlatency" and "Ubuntu, kernel 2.6.20-15-generic"?

---

### Post by TNBY963 on 2007-05-14
> **sclough said:**
> Ok, for someone that wants to install studio on a machine without a DVD drive, can someone clear this up for me. 

Hi, 
I would suggest that you download the normal Feisty Fawn (if you don't have it installed already), because it fits on a normal cd. Then, when you installed feisty, just add the ubuntustudio repositories and install all the ubuntustudio packages you need (instructions to do this can be found here: [http://www.ubustu.com/globe/2007/05/11/download-mirrors-for-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/11/download-mirrors-for-ubuntu-studio/)) It's what I did, and I have everything now. The theme, all the programs and the lowlatency kernel.
The only downside to this approuch is that you have to have a working internet connection.

Btw, using this method also gives you the benefit of a nice graphical installer instead of the spartan server install.

I don't think that installing the xubuntu desktop metapackage would cause any problems, but I haven't been able tot try this, so this is speculation. But it's worth a try

Greetz

Gert

---

### Post by TNBY963 on 2007-05-14
> **MetalMusicAddict said:**
> 
Well, this wont really get you our settings which are needed if you do sound work. We set some things when you install from our disk.

Also ubuntustudio-desktop will conflict with some things in ubuntu-desktop. ie: the -sounds. Though some people might want those. :)
Hi MMA,

first off, excellent work. I've already made a lot of my friends (also musicians) very jealous.

But what do you mean with "some things"? I tried to install via the dvd, but after the install I couldn't get X to start. I tried a lot of stuff and then decided I would just install Feisty and use the repo's.
I'd like to take advantage of the full ubuntu studio experience, so are there some settings wich I miss now? And by sounds, do you mean the click when selecting something and startup and shutdown sounds, 'cause I have those.

Thanks again for all the hard work. For a first distro, this is really really good!

Greetz

Gert

---

### Post by sclough on 2007-05-14
> **TNBY963 said:**
>  It's what I did, and I have everything now. The theme, all the programs and the lowlatency kernel.
The only downside to this approuch is that you have to have a working internet connection.



Thanks, I'll try that.

---

### Post by MetalMusicAddict on 2007-05-14
> **NESFreak said:**
> I've recently heard canonical would start protecting it's trademarks. Which basically means every non-official whateverbuntu distro should change it's name. (here's marks post on his blog [http://www.markshuttleworth.com/archives/112](http://www.markshuttleworth.com/archives/112))

Wondering what this project is going to be named.
We are as official as Xubuntu and our name/logo is fully protected by Canonical.
> **TNBY963 said:**
> Hi MMA,

first off, excellent work. I've already made a lot of my friends (also musicians) very jealous.

But what do you mean with "some things"?
"some things"= Letting a user start JACK as a user instead of being root. Heres the command to set if you didnt install from our disk:
```
sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'
```
> I tried to install via the dvd, but after the install I couldn't get X to start. I tried a lot of stuff and then decided I would just install Feisty and use the repo's.
I'd like to take advantage of the full ubuntu studio experience, so are there some settings wich I miss now? And by sounds, do you mean the click when selecting something and startup and shutdown sounds, 'cause I have those.

Thanks again for all the hard work. For a first distro, this is really really good!

Greetz

Gert
The thing about the X issue is our installer is _exactly_ like Ubuntu but we add the tasksel options at the end. I have no clue what up with X other than the right driver isnt being selected.

What GFX card are you using?

---

### Post by mjitkop on 2007-05-14
> **chunchengch said:**
> By the way, there are many options to boot Ubuntustudio, but I don't understand what is the difference between options "Ubuntu, kernel 2.6.20-15-lowlatency" and "Ubuntu, kernel 2.6.20-15-generic"?

I was just wondering the same thing too. I'll watch this thread for an answer to this question. :)

---

### Post by justin whitaker on 2007-05-14
Ok, the website is down, and the Torrent on distrowatch throws an error. Where do I get this without bogarting someone's bandwidth?

---

### Post by Kulgan on 2007-05-14
> Ok, the website is down, and the Torrent on distrowatch throws an error. Where do I get this without bogarting someone's bandwidth?
[Here]("http://ubuntustudio.org/files/UbuntuStudio_7.04.torrent")?

---

### Post by TNBY963 on 2007-05-14
> **MetalMusicAddict said:**
> ]
The thing about the X issue is our installer is _exactly_ like Ubuntu but we add the tasksel options at the end. I have no clue what up with X other than the right driver isnt being selected.

What GFX card are you using?

Hi MMA,

thanks for your response. It's very kind.

I use an ATI MobilityRadeon X600. It's a laptop from HP. I bought it before I got started with Linux, otherwise I would have had different hardware (but a new pc is on the way, following the specs on the ardour page!)

I think I must have messed something up with the screen resolutions. I'm not sure though. It installed correctly, but when I rebooted I got the splash screen and after that the message that there were some problems with X. I'm sorry, but I can't remember what it was. I should have written it down.
I tried sudo dpkg reconfigure xorg.conf (or whatever the command is) from the command line and I selected all the defaults. But when It came to choose between 16 bit or something else it wouldn't save the config file. So I didn't know what else to do then reinstall feisty.

I just started using linux in the summer of 2006 and I'm still learning all the ins and outs. 

Greetz

Gert

---

### Post by mpgarate on 2007-05-14
SITE IS BACK UP!

at least I just got a connection

lets try and go easy and not kill em over there bandwidth wise :p



- and if its as official as xubuntu, will it get a link on the front ubuntu page, if so when?

---

### Post by Kulgan on 2007-05-14
If you think it's something to do with the xorg conf, you could always boot up a live cd of some kind and take that conf...

---

### Post by MetalMusicAddict on 2007-05-14
> **mpgarate said:**
> - and if its as official as xubuntu, will it get a link on the front ubuntu page, if so when?
We're still working out things like this. :)

---

### Post by MetalMusicAddict on 2007-05-14
Someone has hijacked the [http://mirror.imbrandon.com/ubuntustudio/7.04](http://mirror.imbrandon.com/ubuntustudio/7.04) mirror. **[COLOR="Red"]IT IS BULL$H!T.[/COLOR]** Dont pay for downloads. This should be sorted soon. Its just some @ss trying to make money.

We will let you guys know when its clear.

---

### Post by Shibby73 on 2007-05-14
Very nice looking install.  Looks like a ton of work!

Some issues to consider:
1) I needed to buy a DVD burner just to install this
2) I don't know anything about multimedia stuff like Jack and all of these tools
3) Jack server?  Ok what is that and where do I get it just to try out most of these applications that appear to work together. About the only thing audio I got to work was hydrogen with its drum sounds.
4) People will inevitably compare this to APPLE, and to be honest I was much more impressed with the FREE stuff that comes on the MAC (at a huge price of course) when walking in their store.
5) Support, instructions?  The Ubuntu board doesn't even have a forum dedicated to Ubuntustudio, but I sure can find the Christian Ubuntu edition forum easily.
6) What and how could I show this to someone who is considering buying a Mac and ever win them over?  Certainly not because it is free... or useful... or well supported.  They would basically have to be a nut about free open source and figuring things out perusing the internet for help as tediously as I have and I am an impatient *******.

Just my 6 cents here.  Looking forward to figuring out how to use all (or some) of this stuff BEFORE I try to show it off to anyone else.

Thanks,  

-Steve

[http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

---

### Post by Geoff Leopard on 2007-05-15
Hi Steve

Please don't take this the wrong way, but you can't blame the Ubuntu Studio team if you don't know about 'multimedia stuff'. The Apple offerings (as an audio engineer I am thinking of Garageband in particular) look great and work well, but more serious users will be far more interested in Ardour2. Jack is launched with Jack Control (included), which you just need to launch and start.

To be honest, people who are familiar with audio software will see parallels in Jack Control's patching to the way they already work; when you realise that all the software can work with each other and be routed in any order you start to see that the strength of the system is in its interoperability.

It could be seen as pretty rude to say that this software is not useful, especially as it seems like you don't know what you're talking about. I can tell you that it is **very **useful indeed.

G

---

### Post by MetalMusicAddict on 2007-05-15
Just a note. imbrandon's mirror is good now. Clear your cache. :)

---

### Post by sclough on 2007-05-15
Not to go on and on about this, but it would be extremely helpful if someone like MMA who knows what they are doing :)  could post on the wiki or a thread exactly what to do if you are installing Studio in some way other than the DVD.  For example, I'll have to install Feisty from the CD and then use apt-get to pull in the packages.  I'm planning on just doing a plain server install to avoid any conflicts with the standard desktop packages and the studio desktop packages.  So far it seems like this should work except that the sounds aren't the ubuntu studio sounds (I assume this is the bootup sounds, etc), and you have to mode a change to permissions to allow JACK to run as a non-root user.

For people like me that are dense would it be possible to get someone on the studio dev team to post a list of the things that need to be done if you install in an alternate way?  It would be very appreciated:D

---

### Post by profjohn on 2007-05-15
I was able to get the theme on my 64bit feisty by browsing directly to their repository and downloading all of their packages which are of the form *_all.deb, which is basically all the artwork then installed them, it works fine.

[http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/)

---

### Post by John.Michael.Kane on 2007-05-15
> **sclough said:**
> Not to go on and on about this, but it would be extremely helpful if someone like MMA who knows what they are doing :)  could post on the wiki or a thread exactly what to do if you are installing Studio in some way other than the DVD.  For example, I'll have to install Feisty from the CD and then use apt-get to pull in the packages.  I'm planning on just doing a plain server install to avoid any conflicts with the standard desktop packages and the studio desktop packages.  So far it seems like this should work except that the sounds aren't the ubuntu studio sounds (I assume this is the bootup sounds, etc), and you have to mode a change to permissions to allow JACK to run as a non-root user.

For people like me that are dense would it be possible to get someone on the studio dev team to post a list of the things that need to be done if you install in an alternate way?  It would be very appreciated:D

If you doing the studio install from a server install.

Run these two commands the prompt:
```
sudo su -c 'echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list'
```

```
wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add - && sudo apt-get update
```



Run this to install UbuntuStudio.
```
sudo aptitude install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video ubuntustudio-artwork ubuntustudio-gdm-theme ubuntustudio-icon-theme ubuntustudio-look ubuntustudio-session-splashes ubuntustudio-sounds ubuntustudio-screensaver ubuntustudio-theme ubuntustudio-wallpapers usplash-theme-ubuntustudio wired 
```

If you have a nvidia card you will also need this
```
sudo aptitude install linux-restricted-modules-2.6.20-15-lowlatency
```

Then you can reboot, and log in to ubuntustudio.

Hope this helps

If you have any issues just make a thread.

---

### Post by misfitpierce on 2007-05-15
64 bit processors run 32 bit same as 32 bit processors just 64 bit has its speed advantages! so you can run it fine.

---

### Post by Hillbilly Tilley on 2007-05-15
Hello All,

I installed the audio, audio-plugins, graphics, and video from the ubuntu studio repos using the instructions in the wiki.  After installation and reboot I went to check for updates and I get two of these errors

```
http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.bz2: Sub-process bzip2 returned an error code (2)
```

Anyone know what this is and how to fix it.

Thanx,
            Hillbilly

---

### Post by justin whitaker on 2007-05-15
> **Kulgan said:**
> [Here]("http://ubuntustudio.org/files/UbuntuStudio_7.04.torrent")?

Thanks for the link! I got my download last night. Now I just have to decide: audio, or graphics? :)

---

### Post by Kulgan on 2007-05-15
All :D

---

### Post by sclough on 2007-05-15
> **SD-Plissken said:**
> 
Then you can reboot, and log in to ubuntustudio.

Hope this helps

If you have any issues just make a thread.

Thanks.  I'll assume for now all I need to do after install is that one fix for Jack that MMA mentioned and I'll be good.  I'll start another thread if I find any other problems.

---

### Post by Shibby73 on 2007-05-15
> **Geoff Leopard said:**
> Hi Steve

Please don't take this the wrong way, but you can't blame the Ubuntu Studio team if you don't know about 'multimedia stuff'. The Apple offerings (as an audio engineer I am thinking of Garageband in particular) look great and work well, but more serious users will be far more interested in Ardour2. Jack is launched with Jack Control (included), which you just need to launch and start.

To be honest, people who are familiar with audio software will see parallels in Jack Control's patching to the way they already work; when you realise that all the software can work with each other and be routed in any order you start to see that the strength of the system is in its interoperability.

It could be seen as pretty rude to say that this software is not useful, especially as it seems like you don't know what you're talking about. I can tell you that it is **very **useful indeed.

G

I didn't blame anyone for anything. My apologies for appearing rude.  

What I WAS saying, and yes it was partly out of sheer frustration... WAS that to show the utility (usefulness) of these tools, or provoke interest in exploring learning them or converting for a while (if not longer) to Linux from say WIN or MAC ... one needs INSTRUCTIONS and probably a great demonstration or tutorial.  That was my "criticism" but was really a suggestion and a question for guidance on where to get this help.  

After all the work and expense (DVD burner and DVDs, >$100 really not that expensive), not to mention risk to my system (if I had fouled up) in getting this stunning looking install up and running, I was disappointed that I couldn't even find a good demonstration to show off to anyone else.  

No I am not a music professional, but I am good at tinkering around and showing things to people who may be more enlightened than myself.  I was hoping to walk into work and be like, yeah this is why I didn't have a beer with you guys lastnight, look what I got FOR FREE!  Isn't this the coolest thing ever.  And Hey reconsider buying that MAC you were talking about I told you this Ubuntu can do anything...

Garageband I believe was what a Mac salesperson showed me, in a few seconds we had some music playing with all sorts of tracks.  That IS the COMPETITION to emulate and beat if you want people to explore linux and ubuntu and that was my understanding of what  UbuntuStudio is working towards.  So is there a support forum that gives instruction so we can make our own demo and get Jack and everything working famously together?

I don't think I am taking anything the wrong way when noticing that I don't know what I am doing and am frustrated but instead I'm told I could be seen as being rude but not offered any direction to the help that may be available (which is exactly what I was complaining about). We have moderators saying don't post hey Ubuntustudio is cool in X place and no mention of where to go for support or help using the fancy thing. 

Sure your a professional you don't need help it is a great tool, etc... but is it aimed only at YOU or also the amateur "enthusiast"?  A great tool is USELESS without instructions to the "enthusiast" I mean I randomly clicked buttons and couldn't get it all to work, is it broken, are there links to help, is there a demo to see if it was installed correctly?  Please don't take my reply the wrong way and if your not going to reply with a link to guide me or other people who may like to try something out for the first time then don't reply.:lolflag:

---

### Post by MetalMusicAddict on 2007-05-15
Ubuntu Studio was created by linux multimedia people for linux multimedia people. We already know alot of these apps and places to look for answers.

That being said we know new-to-linux people will try this (we dont recommend it) and we will try to provide resources aimed at new users as they develop. Lots of the info is not very cohesive. Scattered around a bit.

---

### Post by Tomosaur on 2007-05-15
I like creating music on Linux - and don't get me wrong, there are some really great apps out there, but what annoys me is, frankly, the sheer range of choice. There's a LOT of stuff, and although much of it is truly great, I'm yet to find something that I can honestly say I'm totally happy with.

I tend to record stuff and then mix it all together using Audacity - which, although fine for most things I need, is incredibly annoying in that it makes sequencing so difficult. Although it's fine if I'm recording everything myself (because I can just record, playback and record, playback and record ad infinitum), if I want to incorporate samples and such, Audacity just doesn't cut it. Cutting and inserting silence is not how we should be sequencing I'm afraid (yes, I'm aware Audacity isn't supposed to be a sequencer :P). The best I've used so far for this is Sony SoundAcid on Windows - but obviously, I can't use that on Linux (and SA has it's own limitations).

My latest stuff is making use of strings and other things for which I essentially need midi synths as I don't have my own string section (unfortunately!). I recently used Reason on Windows which does exactly what I need but if anyone knows of something which can do the same or similar on Linux I'd be very grateful.

Reason also uses a system kind of like Jack. The UI looks like a rack of synths and sequencers etc. If you hit tab, the view changes to the 'back' of all of the elements, and you can connect it all with cables (animated too!). It really is a neat touch, and seems more friendly than what I currently use with Jack (Jack Control).

I'm not averse to using a bunch of a different programs and connecting them with Jack, but I really would appreciate a utility which lets me do it 'all in one place' as it were, similar to Reason.

---

### Post by Drophere on 2007-05-15
> **MetalMusicAddict said:**
> Ubuntu Studio was created by linux multimedia people for linux multimedia people. We already know alot of these apps and places to look for answers.

That being said we know new-to-linux people will try this (we dont recommend it) and we will try to provide resources aimed at new users as they develop. Lots of the info is not very cohesive. Scattered around a bit.

Ah, now I understand. :) I had got the impression from the pre-launch hype that Ubuntu Studio was going to be the "boot and run" linux audio solution I'd been looking for, but it appears it's a fair way off that. Thanks for the clarification.

I'll keep watching the progress and look forward to being able to migrate to Linux once the hardware driver issues are sorted.

---

### Post by PartisanEntity on 2007-05-15
Sorry I am sure this has been covered in the thread, but I couldn't find it, do I use the repos mentioned on ubuntustudio.org to install the meta-package?

---

### Post by John.Michael.Kane on 2007-05-15
> **PartisanEntity said:**
> Sorry I am sure this has been covered in the thread, but I couldn't find it, do I use the repos mentioned on ubuntustudio.org to install the meta-package?

Yes you use the ubuntu studio repos. this post should help.
[http://ubuntuforums.org/showpost.php?p=2660460&postcount=190](http://ubuntuforums.org/showpost.php?p=2660460&postcount=190)

---

### Post by Shibby73 on 2007-05-15
> **MetalMusicAddict said:**
> Ubuntu Studio was created by linux multimedia people for linux multimedia people. We already know alot of these apps and places to look for answers.

That being said we know new-to-linux people will try this (we dont recommend it) and we will try to provide resources aimed at new users as they develop. Lots of the info is not very cohesive. Scattered around a bit.

Well I think you guys who know how to use this stuff could really be an enormous benefit to Linux and UbuntuStudio!  
:guitar: 

Imagine you guys recording a video of using this new composition of tools! That would be something fantastic to link us to.  To keep our juices flowing and interest in watching things evolve. I mean that got me to try out beryl (which was a mistake on my machine but I jumped in knowing it was beta and may not work).  I really love the Ubuntu and Linux community, everyone working together to help each other.  A couple months ago there was no support for my EVDO card I was kinda bummed.  I've been hoping to get a linux os down and eventually get a new fancy tablet pc and put the best Ubuntu on it and use my EVDO to connect to the internet, now Motion makes a tablet that takes a PCMIA EVDO card and NOW there may be some linux apps that could really work out well on a tablet.

I am very excited.  I am no sound recorder, no great photographer, but I love playing with all of these tools and LEARNING the whole time.  Thank you for helping clarify what is going on and the stage these products are in during development.

1) Unify the scattered information
2) Make (using the UbuntuStudio's tools perhaps) a video/demo of the tools in use.
3) Spread the word while the drivers etc get worked out.

Looking forward to seeing what unfolds!
:popcorn:

---

### Post by D!mon on 2007-05-19
> **profjohn said:**
> I was able to get the theme on my 64bit feisty by browsing directly to their repository and downloading all of their packages which are of the form *_all.deb, which is basically all the artwork then installed them, it works fine.

[http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/)

It worked for me too, now with UbuntuStudio theme!!! :cool: Btw, do u use Heliodor as a window decorator? With Heliodor my desktop looks like screenshots.

Anyway, 64bit repo will be greatly appreciated!:rolleyes:

---

### Post by ThinkBuntu on 2007-05-20
Are there any plans to include a sheet music composer in U.Studio? And are there any programs out there to do this besides the very unfriendly Lilypond?

---

### Post by Kulgan on 2007-05-20
Denemo is included. It's quite nice once you get used to it.

---

### Post by reclusivemonkey on 2007-05-20
> **ThinkBuntu said:**
> Are there any plans to include a sheet music composer in U.Studio? And are there any programs out there to do this besides the very unfriendly Lilypond?

Looking at the Rosegarden site, it seems that can do it;

[http://www.rosegardenmusic.com/](http://www.rosegardenmusic.com/)

Don't ask me any more though, I can't even play the triangle... ;-)

---

### Post by ThinkBuntu on 2007-05-20
> **Kulgan said:**
> Denemo is included. It's quite nice once you get used to it.

I installed Ubuntu Studio today and I'm very impressed. I did discover this app as well :^)
Apparently, it plays nice with LilyPond, which is music to my ears.

I have notices my wireless performance is worse than with plain ol' Ubuntu Feisty. I may consider doing an install of Feisty and just adding the Studio repos; after that I'd install the programs that came with this off the install disc.

---

### Post by MetalMusicAddict on 2007-05-20
> **ThinkBuntu said:**
> I have notices my wireless performance is worse than with plain ol' Ubuntu Feisty.
We use the exact packages Ubuntu uses for wifi support. Should be no difference.

---

### Post by ThinkBuntu on 2007-05-20
> **MetalMusicAddict said:**
> We use the exact packages Ubuntu uses for wifi support. Should be no difference.

Could it have anything to do with the "low latency" kernel? For that matter, out of curiosity, what does a low latency kernel do? I'm thinking maybe I'd get better performance using the module built for the vanilla kernel.

---

### Post by ThinkBuntu on 2007-05-20
One other quick question. Is there anything in particular that I'd be missing out on if I just installed the packages off the CD and enabled the Studio repos on a plain Ubuntu install? Don't get me wrong, I really enjoy this Ubuntu version, just curious.

---

### Post by rko618 on 2007-05-21
I love the web page design! Good Job.  I really hope people find UStudio to be a valuable asset.

---

### Post by mjitkop on 2007-05-21
No Desktop Effects in Ubuntu Studio? :confused:

---

### Post by sclough on 2007-05-21
I haven't gotten the desktop effects option on the menu either, but I assumed it was because it seems like my ati card doesn't support aiglx and I need to get XGL running and just haven't gotten xgl running with the fglrx drivers yet.  Is desktop effects missing in studio?  (I don't know why it would be)

---

### Post by jariku on 2007-05-21
Desktop effects are a dependency of the ubuntu-desktop metapackage which is not installed by default in Ubuntu Studio (unlike 'vanilla' Ubuntu). If you want the desktop effects in Ubuntu Studio, just install the desktop-effects package. It's working fine with my old Radeon card and open source drivers.

---

### Post by MetalMusicAddict on 2007-05-21
> **ThinkBuntu said:**
> Could it have anything to do with the "low latency" kernel? For that matter, out of curiosity, what does a low latency kernel do? I'm thinking maybe I'd get better performance using the module built for the vanilla kernel.
I wouldnt think so since I run the kernel on my laptop (dont do this unless you plug it in all the time) but it could also be a HW issue.
> **ThinkBuntu said:**
> One other quick question. Is there anything in particular that I'd be missing out on if I just installed the packages off the CD and enabled the Studio repos on a plain Ubuntu install? Don't get me wrong, I really enjoy this Ubuntu version, just curious.
You shouldnt miss anything.
> **mjitkop said:**
> No Desktop Effects in Ubuntu Studio? :confused:
Nope. Its not what this project is aiming for. If a user does want them its easy enough to install themselves.

---

### Post by ThinkBuntu on 2007-05-21
> **MetalMusicAddict said:**
> I wouldnt think so since I run the kernel on my laptop (dont do this unless you plug it in all the time) but it could also be a HW issue.
Well, I added all the software from the Wiki onto a plain 7.04 install. I'll be at my local coffee shop tonight, so I'll let you know if I notice a difference. Probably just silliness on my part though.

---

### Post by sclough on 2007-05-21
> **MetalMusicAddict said:**
>  not what this project is aiming for. If a user does want them its easy enough to install themselves.

Not to sound smart, because I really appreciate all the work on Studio, but why not just include this package in the install since the same people that are interested in graphics and video on Linux would be the same crowd that wants the option to enable some eye candy?

---

### Post by diskotek on 2007-05-21
i think i won't install any 3d desktop effects for ubuntustudio. because it's aimed on video- sound & graphic processing. i think it would be faster without without glx.

---

### Post by sk8dork on 2007-05-21
thought i'd mention here that i've created a theme for fluxbox heavily based on the ubuntu studio theme for gnome. i prefer fluxbox over gnome, but i really like the ubuntu studio theme, so i run gnome-settings-daemon to utilize the innards of the gnome ubustu theme and use my fluxbox theme for the window manager. i think it looks pretty good so far. [link]("http://www.sk8dork.com/pics/ubustu-fluxboxtheme4.png") 

i could make it available to all if anyone actually wants it, and if the ubuntu studio guys don't mind.

---

### Post by MetalMusicAddict on 2007-05-21
> **sk8dork said:**
> I could make it available to all if anyone actually wants it, and if the ubuntu studio guys don't mind.

Sure. Could you PM me about this?

---

### Post by Mars73 on 2007-05-21
This looks very interesting!
I'm a musician myself and have used quite a few programs like Cubase, Vegas, Soundforge.
A few weeks ago I installed Ubuntu and now I've totally converted to Ubuntu, in my case Kubuntu Feisty Fawn.
For most 'simple'  applications like mail and internet it's fairly easy to use but 'special' programs like the above mentioned and Photoshop etc is something else.
I saw the possibilities of upgrading a normal Feisty installation to Ubuntu Studio, has anyone done this? Did it go smoothly?
How good is the soundcard recognition? I would like to use my Echo Audio Gina card for it.
Is it installable on Kubuntu?
I will definitely read some more about it and hopefully get my Echo Gina audio card up and running with Ubuntu Studio.

---

### Post by arijarot on 2007-05-24
> **greenpete said:**
> 
P.S. Then change your theme in the normal way!

I did everything and sudo apt-get install ubuntustudio-theme installed fine, but when I go to the themes options in system/prefrerences, there is no theme there to choose from except for the default ones. any ideas?


This is the best ubuntu theme I have ever seem! It should, at the very least, be included as a default theme option.

---

### Post by sk8dork on 2007-05-24
find the theme folder in your system. it should be something like /usr/share/themes/UbuntuStudio
drag that folder over into the themes window. it will ask you if you want to apply the new theme, click yes. now save the theme name. you should also open the theme manager as root and do the same thing, since root has different settings. now anything you do that needs the admin password should look the same and not stick out like a sore thumb.

---

### Post by arijarot on 2007-05-24
> **sk8dork said:**
> find the theme folder in your system. it should be something like /usr/share/themes/UbuntuStudio
drag that folder over into the themes window. it will ask you if you want to apply the new theme, click yes. now save the theme name. you should also open the theme manager as root and do the same thing, since root has different settings. now anything you do that needs the admin password should look the same and not stick out like a sore thumb.

Thank you, sk8dork

---

### Post by blackspyder on 2007-05-25
big thanks to the Ubuntu Studio Team. I love it!!!!!!!!

---

### Post by hakimaki on 2007-05-27
I did a fresh install of ubuntu studio to replace my plain ubuntu install and am loving it.  Being not much of a gamer, I only dual booted with XP for my music software.  I still need to get an audio interface (prefereably firewire) to try out in ubuntu before I can totally rid myself of windoze.  

PS - My ubuntu studio install runs faster than my my regular feisty install did... I like!

---

### Post by dbbolton on 2007-06-05
openbox users:

i made a theme that integrates well with Ubuntu Studio.

[link](http://box-look.org/content/show.php/show.php?content=59671)

---

### Post by sk8dork on 2007-06-05
> **dbbolton said:**
> openbox users:

i made a theme that integrates well with Ubuntu Studio.

[link](http://box-look.org/content/show.php/show.php?content=59671)

not bad. 
could you tell me the main differences between openbox and fluxbox? i'm curious because i use fluxbox, and i also created a fluxbox ubuntustudio theme (on previous page, not completed yet). i've never tried openbox.

---

### Post by dbbolton on 2007-06-05
> **sk8dork said:**
> not bad. 
could you tell me the main differences between openbox and fluxbox? i'm curious because i use fluxbox, and i also created a fluxbox ubuntustudio theme (on previous page, not completed yet). i've never tried openbox.
i really can't tell you the difference, because i've never used fluxbox. i tried it briefly after i had been using openbox for awhile, and i didn't see anything that made me want to keep using it. openbox seemed easier to tweak, to me.

---

### Post by burt_57 on 2007-06-07
robert@robert-desktop:~$ sudo su -c 'echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list'
Password:
robert@robert-desktop:~$ wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add - && sudo apt-get update
gpg: no valid OpenPGP data found.
robert@robert-desktop:~$ 
 
Why do I get this when I try waht you said? :(

---

### Post by burt_57 on 2007-06-07
> **SD-Plissken said:**
> Yes you use the ubuntu studio repos. this post should help.
[http://ubuntuforums.org/showpost.php?p=2660460&postcount=190](http://ubuntuforums.org/showpost.php?p=2660460&postcount=190)
Thank you now it is downloading... from the address you post will see what happen when all
download are finish and I reboot ;)

---

### Post by sk8dork on 2007-06-07
> **burt_57 said:**
> robert@robert-desktop:~$ sudo su -c 'echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list'
Password:
robert@robert-desktop:~$ wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add - && sudo apt-get update
gpg: no valid OpenPGP data found.
robert@robert-desktop:~$ 
 
Why do I get this when I try waht you said? :(

it looks like you copied everything directly...should work, as i just tried it myself.

nevermind, looks like you got it.

---

### Post by burt_57 on 2007-06-07
> **sk8dork said:**
> it looks like you copied everything directly...should work, as i just tried it myself.

nevermind, looks like you got it.

Look at my new Avatar :guitar:

---

### Post by burt_57 on 2007-06-07
Hello to all who are using Ubuntustudio.
Am glad I have found it........I love it.
Now if only I could play my favorite PC games on it,
Windows Xp would be out.
Bravo to whom is reponsible for this great upgrade :popcorn:

---

### Post by burt_57 on 2007-06-07
> **justin whitaker said:**
> Fantastic work MMA! 


EDIT:

Wow, that sure is pretty, and has most of the packages I use. Might have to think about a full reinstall to get the fully Ubuntu Studio love.
Would a full install rid the Ubuntu 7 , i386.... which I don't mind.
Just love this new look

---

### Post by andy_cowman on 2007-06-07
Just been setting it up and I love it!!

Was trying Freespire last week and found it very frustrating, then back to ubuntu through Ubuntu Studio. Its faster on my machine than normal ubuntu which I dont understand but am happy about. Installed WINE and for the first time I just doubled clicked photoshop 7s setup.exe and it just installed it and added it to the gnome menu! Not important I know but it just works.

CNR is rubbish, Long live Synaptic! 

Anyone know how to add a polished finish to the grey theme?

---

### Post by arijarot on 2007-06-08
> **greenpete said:**
> I'm running it now!
If you gou go to the download page you will see the terminal commands to run...
sudo su -c 'echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list'

and

wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add - && sudo apt-get update

then run..
sudo apt-get install ubuntustudio-theme

Hope this helps, it worked for me!

Peter

P.S. Then change your theme in the normal way!

I followed this and everything worked fine, but the theme is not in there. I tried to reinstall ```
sudo apt-get install ubuntustudio-theme 
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntustudio-theme is already the newest version.
The following packages were automatically installed and are no longer required:
  libstdc++2.10-glibc2.2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.

``` but, it's obviously on my system... any idea how to make it show up in the sys>prefs>theme?

---

### Post by obleak on 2007-06-09
can the guys at ubuntustudio have a look at installing a better gtk1.2 theme then the default?
something that matches the gnome theme would be cool :)

[https://bugs.launchpad.net/bugs/71071](https://bugs.launchpad.net/bugs/71071)

---

### Post by sk8dork on 2007-06-09
> **arijarot said:**
> I followed this and everything worked fine, but the theme is not in there. I tried to reinstall ```
sudo apt-get install ubuntustudio-theme 
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntustudio-theme is already the newest version.
The following packages were automatically installed and are no longer required:
  libstdc++2.10-glibc2.2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.

``` but, it's obviously on my system... any idea how to make it show up in the sys>prefs>theme?

read post 223 on the previous page (page 23)

---

### Post by arijarot on 2007-06-09
> **sk8dork said:**
> read post 223 on the previous page (page 23)

:oops: I guess that's twice that I've asked now. lol. thanks again...

---

### Post by sk8dork on 2007-06-19
> **dbbolton said:**
> i really can't tell you the difference, because i've never used fluxbox. i tried it briefly after i had been using openbox for awhile, and i didn't see anything that made me want to keep using it. openbox seemed easier to tweak, to me.

i decided to try out openbox this past weekend. i installed the version from the feisty repos and i liked some things but didn't like other things. all the things i didn't like were fixed in the latest release, 3.4.2 (feisty deb from the openbox site), and then some. i think i prefer openbox tons over fluxbox. i think i'm going to try my hand at maybe tweaking your ubuntustudio ob theme or creating one from scratch. 

having used and played with fluxbox quite a bit, i feel like i can comfortably outline differences between the two and explain why openbox is now the box of choice for me. i won't go into that kind of detail here, though. a few points on the new version of openbox over the one in the repos: the menus do not move if there is no more room on the desktop. each submenu simply appears in the ideal position without rearranging the previous menus and the mouse (this is now more like the way fluxbox menus behaved). this latest version of openbox is supposedly, and apparently, faster than before. things seem a lot more steady and stable too. my panel of choice is currently pypanel. 

oh, and your theme looks smoother in the new version of openbox. the gradient you have set for the title bars is softer, which may or may not be what you were going for.

if anyone is using the version of openbox from the repos i highly recommend renaming ~/.config/openbox to ~/.config/openboxold or something similar, uninstall the old version of openbox and obconf, removing any of the .desktop entries that you created for your login manager, and downloading and installing the latest debs for openbox and obconf from the openbox site: [[link]]("http://icculus.org/openbox/index.php/Openbox:Download")

---

### Post by noctis_vulpes on 2007-11-09
Um... I'm trying to install Ubuntu Studio theme on Feisty... Every singly googled information is essentially the same as this post:

[http://ubuntuforums.org/showpost.php?p=2660460&postcount=190](http://ubuntuforums.org/showpost.php?p=2660460&postcount=190)

except that it's not working. There doesn't seem to be a host named archive.ubuntustudio.org, and I can't find any information as to what I need to change in order to get this theme installed. Any idea waht I need to do?

// Sorry about posting the same thing in Desktop section. I can't figure out how to delete this post. T.T

---

### Post by KillerBob-it on 2007-12-26
> **noctis_vulpes said:**
> Um... I'm trying to install Ubuntu Studio theme on Feisty... Every singly googled information is essentially the same as this post:

[http://ubuntuforums.org/showpost.php?p=2660460&postcount=190](http://ubuntuforums.org/showpost.php?p=2660460&postcount=190)

except that it's not working. There doesn't seem to be a host named archive.ubuntustudio.org, and I can't find any information as to what I need to change in order to get this theme installed. Any idea waht I need to do?

I have the same problem
[http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) doesn't work and I can't install Realtime Kernel

---

### Post by Endolith on 2007-12-27
> **KillerBob-it said:**
> I have the same problem
[http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) doesn't work and I can't install Realtime Kernel

Remove archive.ubuntustudio.org from your repositories.  See [http://ubuntuforums.org/showthread.php?t=592639](http://ubuntuforums.org/showthread.php?t=592639)

He really should have explained that a little more clearly...

---

### Post by Endolith on 2007-12-27
> **burt_57 said:**
> 
Now if only I could play my favorite PC games on it,
Windows Xp would be out.

Run them in Wine.  [http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by toupeiro on 2007-12-27
Sorry if this was covered in this thread, but

if I have a box running **studio**-feisty, will a network based distro-upgrade successfully apply studio-gutsy?  I would assume there are more updates to the distro than just the themes like all the incorporated gutsy upgrades plus the studio specific apps?

---

### Post by qntal on 2007-12-30
Hi guys. I recently did a Ubuntu Studio 7.10 fresh install and it seems I can't get my ATI drivers to work with aiglx.

I've an ATI Radeon 9700 (R300). Can't get Direct Rendering and only 500fps in glxgears.

Is there a compatibility issue with the newest ATI drivers and realtime kernel?

---

### Post by dizzyheadmusic on 2008-01-23
I'm surprised that there's not much talk in this thread about Ubuntu Studio 7.10 and I assume that's a good thing? That must mean that it's working well. I'll be installing it on a Dell Inspiron 9200 pretty soon.

---

### Post by BuffaloX on 2008-01-24
My wife uses it, She is very happy about Ubuntu Studio 7.10.
Personally I use Ubuntu with some Studio add ons like rt kernel.

---

