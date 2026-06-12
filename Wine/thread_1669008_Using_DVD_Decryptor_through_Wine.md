---
title: "Using DVD Decryptor through Wine"
date: 2011-01-17
forum: Wine
---

### Post by Segofam on 2011-01-17
Hi all,
Using WIINE 1.3.11
Having installed DVD Decryptor 3.5.4.0
I can not get DVD Decryptor to recognise D: drive / DVD drive.
Can anyone tell me if the program is not compatible, or if it is, would you let me know how to get DVD Decryptor to search and recognise my D: drive?
Kind regards,
Scott

---

### Post by cascade9 on 2011-01-17
It should work- 

[http://appdb.winehq.org/appview.php?versionId=2587](http://appdb.winehq.org/appview.php?versionId=2587)

There are a few hints on how to get it working on that page ;) 

You should be able to rip to .vob with a linux native DVD ripper, which would be easier than anything via WINE.

---

### Post by Segofam on 2011-01-17
> **cascade9 said:**
> 
You should be able to rip to .vob with a linux native DVD ripper, which would be easier than anything via WINE.

Hi and thank you, I got it going with this added note to link you sent:

"The following comments are owned by whoever posted them. WineHQ is not responsible for what they say.

	
Configure DVD Decrypter to use DVD Drive
by Kelly on Sunday August 1st 2010, 16:07
all the above never worked so here is what worked for me. go into DVD decrypters Menu and Select i/o and select aspi and it will pick up your drive and you don't need to add DVD Decrypter to your wine aplications and select windows nt 4.0 as it works without it and you don't need to autodetect your drive."

This worked straight up :-)


As I am still a Newbie, what would be a Linux native DVD ripper that you would use?

There are a few childrens videos that seem to have a hundred vob files in them and those DVD do not rip. What would you suggest to RIP them?

Kind regards,

Scott

---

### Post by handy on 2011-01-17
For those that don't know, (as I didn't until I had to solve the problem myself) DVD Decryptor will break all forms of copy protection that the makers of DVDs use. (At least last time I looked anyway.)

Rarely do we ever need to use such a powerful tool to backup our DVDs, though in less than 1% of the time we do.

Usually HandBrake does the job as smooth as can be.

---

### Post by cascade9 on 2011-01-17
@handy- true, DVD Decryptor will get though most DVD content protection. I used to use DVD Decryptor or DVD shrink with windows to do DVD ripping 100% of the time, using autoGK afterward to convert to .avi. There are other tools, but most of them I didnt trust (WMP, etc), were paid only software, or both. 

@ Segofam- Are you tring to just egt .vob files, or do you want to convert to .avi, etc? I tend to use DVD:rip or K9Copy, but I'veI have never ripped to .vob with linux. So far I've never had any need. I'm sure that DVD:rip, K9copy or nmost (all?) the other linux native rippers will go straight to .vob if thats what you want.

---

### Post by handy on 2011-01-17
I'm probably missing something? Quite often I get told that I am! :)

"But" yes I know, the bits surrounding the "but" can be the crux of the biscuit (as Frank Zappa, used to say).

If you have one of the libdvdcss libraries installed, &, you use Handbrake, then you will be able to rip a backup, directly from the DVD in your optical drive to a location of your choice into either .mp4 or .mkv format.

Personally I use .mp4 & add subtitles from either:

[http://www.findsubtitles.com/](http://www.findsubtitles.com/) (I kill the advertising page with Adblock Plus.)

or use:

[http://www.moviesubtitles.org/](http://www.moviesubtitles.org/)

If I need to. I do that because I am somewhat hearing impaired.

---

### Post by cogadh on 2011-01-17
I'm with Handy on this. Running  DVD Decryptor through Wine seems like the long way around when, as long as you already have libdvdcss installed, you can pretty much do what you need/want to do natively. 

Unless we are both missing something.:confused:

---

### Post by handy on 2011-01-17
> **cogadh said:**
> ...
Unless we are both missing something.:confused:

There is at least one form of copy protection that is thankfully rarely found on DVDs that no Linux native rippers can deal with. I have found DVD Fab Decryptor to be the only one that can backup such disks.

I find the DFD team's marketing & prices to be completely off putting. But that may be just me who feels like that...

That said, their software is the only software that I have found that works with all DVD protection methods.

So, if anyone does find that no native software will do the job & the Wine solutions - DVDShrink, SmartRipper also don't do the job, then you are going to have to get a hold of a copy of DVD Fab Decryptor, as there is little chance that it won't do the job for you.

---

### Post by Segofam on 2011-01-17
Thanks for the response people, I am going to explain myself a little...

I am fairly new to Linux (Ubuntu 10.4) but have seen the light and am trying to do everything using Linux as I am fed up with that other OS and programs freezing, stalling, crashing etc.

I have been using K9, an excellent program to rip and convert to .avi, but there are these childrens DVD that I buy for my 3 year old girl that I cannot backup. These particuluar DVD's - when you open the DVD - seem to have 40 to 50 .vob files that all for appearance sake, look like they are all the size of what the main movie should be.

To burn the .avi I have been using Brasero Disc Burner. When I saw the Jaybob.org site, there was a program called Vidomi, I am trying to run that in Wine too, at this point I don't know if it works, I will find out soon enough!

If you know how, would you tell me how to back them up on DVD?

Sincerely,
Scott.

Now to go and start another thread regarding Digsby ;-)

---

### Post by Segofam on 2011-01-17
> **handy said:**
> 
Usually HandBrake does the job as smooth as can be.

I have not heard of HandBranke, thanks for that, I will give it ago too :)

> **cascade9 said:**
> @ Segofam- Are you tring to just egt .vob files, or do you want to convert to .avi, etc?

I buy childrens DVD's for my 3 year old girl, and when you open up the DVD's there are about 40 -50 .vob files, that for appearance sake - appear to be as big as what one main movie would be, and there-in lays my main problem. How do I back up that type of DVD?

> **handy said:**
> If you have one of the libdvdcss libraries installed, &, you use Handbrake, then you will be able to rip a backup, directly from the DVD in your optical drive to a location of your choice into either .mp4 or .mkv format.

I will check out those sire you added.
I have libdvdcss2 installed, I am guessing it's the same thing!?

> **cogadh said:**
> I'm with Handy on this. Running  DVD Decryptor through Wine seems like the long way around when, as long as you already have libdvdcss installed, you can pretty much do what you need/want to do natively. 

Unless we are both missing something.:confused:

Once i figured out how to use programs in wine, I was am pretty happy to click an icon on my desktop and have it open, but yeah, I agree, it was along way to learn something. At this point, if it works, I am happy ;-)

> **handy said:**
> I have found DVD Fab Decryptor to be the only one that can backup such disks.

I find the DFD team's marketing & prices to be completely off putting. But that may be just me who feels like that...

That said, their software is the only software that I have found that works with all DVD protection methods.

Looks like I am going to have to give HandBrake and DVD Fab Decryptor a go!

Thanks for the feed back people, I appreciate your efforts.

Kind regards,

Scott.

---

### Post by handy on 2011-01-17
I use HandBrakeCLI. There is also a GUI version available. What I did once I worked out how to use the CLI version is I added the command line to an alias in ~/.bashrc like so:

```
alias hb="echo handbrake-cli -t --main-feature -i /media/dvd -o NAME.HERE.mp4 -e x264 -b 1000 -B 192 -s 1 --subtitle-burn" 
```

The above command doesn't work when I call it by typing "hb" but it gives me the command that I can then copy & edit if required.

Also, typing "HandBrakeCLI --help" at the command prompt will give you a very informative list of parameters to use.

You can also scan the DVD with hb, & quite easily see what the length of each title is & then rip those that you desire individually by inputting the desired title number after the "-t" in place of "--main-feature". This may be useful in your current situation where the DVD is trying to make life difficult for you.

You may find the CLI version is a bit much at this early stage of Linux use. But once you use it a little in combination with using the alias function it really is an incredibly impressive piece of software. It loves CPUs that are multi-core also. :)

---

### Post by cascade9 on 2011-01-18
> **Segofam said:**
> I have not heard of HandBranke, thanks for that, I will give it ago too :)

I buy childrens DVD's for my 3 year old girl, and when you open up the DVD's there are about 40 -50 .vob files, that for appearance sake - appear to be as big as what one main movie would be, and there-in lays my main problem. How do I back up that type of DVD?

If yuo can just view .vob files on the disc, its probably not an encrypted DVD (almost all teh commercially pressed DVDs are encrypted, but not all of them). 

They should rip just fine with handbrake, DVD:rip, K9copy, etc.. 

> **Segofam said:**
> I will check out those sire you added.
I have libdvdcss2 installed, I am guessing it's the same thing!?

Yes. 

> **Segofam said:**
> Once i figured out how to use programs in wine, I was am pretty happy to click an icon on my desktop and have it open, but yeah, I agree, it was along way to learn something. At this point, if it works, I am happy ;-)

Sometimes it does seem 'easier' to use tools you are familiar with in WINE, but its not as great an idea as it seems. WINE is more buggy than linux native programs, slower (with everything I've tried anyway) and you've got the added work of finding the programs, d/ling them, installing them, etc.. 

> **Segofam said:**
> Looks like I am going to have to give HandBrake and DVD Fab Decryptor a go!

Thanks for the feed back people, I appreciate your efforts.

Kind regards,

Scott.

Handbrake is a nice linux native program, well worth a try (but that doesnt mean that the other DVD rippers arent worth trying either). DVD Fab Decryptor- I've never had a need. Its likely that you wont either. Keep it in mind in case you ever hit a DVD you cant rip with a linux native program, or DVDshrink/DVD Decryptor, but hopefully that never happens.

---

### Post by Segofam on 2011-01-19
Ok!
Found the Handbrake site, but how do you download it from here: [https://edge.launchpad.net/~stebbins/+archive/handbrake-releases](https://edge.launchpad.net/~stebbins/+archive/handbrake-releases)
...yeah!!! out'a my league here people.
If anyone wants to hold my hand and walk me through the valley of death here I would be really grateful!
(Death is a little over the top isn't it)
After clicking everything on the above link, I came across this link: [https://edge.launchpad.net/~stebbins/+archive/handbrake-releases/+packages](https://edge.launchpad.net/~stebbins/+archive/handbrake-releases/+packages)
But I have no idea which one I should download. I could take a guess!
I have a MSI 601 with Ubuntu 10.4 on it.
Scott

---

### Post by cascade9 on 2011-01-19
For a newbie (sorry about that term), handbrake is going to be alot harder to install than a DVD ripper that is in the ubuntu repositories. DVD:rip is in the repos, and there are probably others (I havent searched for them) 

You should be able to see what DVD rippers are avaible from the software centre. Or just install from CLI- 

sudo apt-get install dvdrip

---

### Post by Segofam on 2011-01-19
scott@scott-laptop:~$ sudo apt-get install dvdrip
[sudo] password for scott: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package dvdrip is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  dvdrip-utils
E: Package dvdrip has no installation candidate
scott@scott-laptop:~$

I am guessing that one is out of date or something!

Scott.

---

### Post by Segofam on 2011-01-19
scott@scott-laptop:~$ sudo apt-get install dvdrip
[sudo] password for scott: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package dvdrip is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  dvdrip-utils
E: Package dvdrip has no installation candidate
scott@scott-laptop:~$

I am guessing that one is out of date or something!

I did manage to download DVD::rip for the Ubuntu Software Centre. Is that what people call the 'repo'?

Scott.

---

### Post by handy on 2011-01-19
There is a GUI version of HandBrake (which is what most people use). Surely it exist in the Ubuntu repos?

Use synaptic & search for handbrake? 

Doing so really should present you with the option of installing the GUI version of HandBrake. 

Quite possibly the GUI version will be the only the option available in synaptic...

---

### Post by cascade9 on 2011-01-19
@ Hany- not as far as I can see. Its not in the ubuntu standard repos- 

>    You have searched for packages that names contain *handbrake* in all suites, all sections, and all architectures.       Sorry, your search gave no results[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=handbrake](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=handbrake)

There are also threads here on how to add a PPA for handbrake- 

[http://ubuntuforums.org/showthread.php?t=1669789](http://ubuntuforums.org/showthread.php?t=1669789)

> **Segofam said:**
> scott@scott-laptop:~$ sudo apt-get install dvdrip
[sudo] password for scott: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package dvdrip is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  dvdrip-utils
E: Package dvdrip has no installation candidate
scott@scott-laptop:~$

I am guessing that one is out of date or something!

I have no idea why that failed, since its into the repo-

[http://packages.ubuntu.com/maverick/dvdrip](http://packages.ubuntu.com/maverick/dvdrip)

.... maybe somebody else does? 

> **Segofam said:**
> I did manage to download DVD::rip for the Ubuntu Software Centre. Is that what people call the 'repo'?

'Repos' are where linux distros store software that can be installed on your system.  Not everything will be in a distros repos, and what is (and isnt) there is up to the distro. 

If something isnt in the repo, you can normally install it by other methods- manually d/ling and installing or adding a PPA (personal pacakge archive). Addign a PPA is like adding an extra repo for software that hasnt been made avaible (for whatever reason) by the the distro. 

Because they are added by the user, PPA are more 'dangerous' than just using the standard repos. Not that adding a PPA is at all dangerous in most cases.

---

### Post by handy on 2011-01-19
I find it hard to understand why Ubuntu does not have HandBrake in its repos?

There exists a Windows, OS X, & a Linux version of both the GUI & CLI, HandBrake packages. 

HandBrake is not at all new; it has been around for years; is incredibly stable, reliable, functional & is licensed GPL... 

From my experience HandBrake has no peer.

Why on earth isn't it available in the Ubuntu repos?

---

### Post by Segofam on 2011-01-19
Ok!

So...by adding the 'PPA' (Personal Package Archive (I have seen that acronym around lots)) - which I am sure is done through the Update Manager - will download and install the Handbrake program?

Thanks again people for your help here, I know it's tedious to follow a growing thread, but it is really appreciated by me, and I am sure many others :)

Sincerely,

Scott

---

### Post by JohnAStebbins on 2011-01-19
> **handy said:**
> I find it hard to understand why Ubuntu does not have HandBrake in its repos?

There exists a Windows, OS X, & a Linux version of both the GUI & CLI, HandBrake packages. 

HandBrake is not at all new; it has been around for years; is incredibly stable, reliable, functional & is licensed GPL... 

From my experience HandBrake has no peer.

Why on earth isn't it available in the Ubuntu repos?
The repository maintainers are very picky about how packages must be built.  They frown upon statically linking libraries that are already available dynamically in the package archive.  HandBrake statically links several libraries for a variety of reasons.  We strongly discourage distributions from dynamically linking these libraries.  It causes mysterious bugs and a real support nightmare on the HandBrake forums.  So this puts the HandBrake maintainers and the distribution maintainers at an impasse.  We each have valid reasons for our rules, and the rules are contradictory.

---

### Post by Segofam on 2011-01-19
> **cascade9 said:**
> 
There are also threads here on how to add a PPA for handbrake- 

[http://ubuntuforums.org/showthread.php?t=1669789](http://ubuntuforums.org/showthread.php?t=1669789)

If something isnt in the repo, you can normally install it by other methods- manually d/ling and installing or adding a PPA (personal pacakge archive). Addign a PPA is like adding an extra repo for software that hasnt been made avaible (for whatever reason) by the the distro. 

Because they are added by the user, PPA are more 'dangerous' than just using the standard repos. Not that adding a PPA is at all dangerous in most cases.

Hmmm...so if I add the PPA, then I a gathering here that it will download, execute and install the program?

I like the sound of that!

> **handy said:**
> HandBrake is not at all new; it has been around for years; is incredibly stable, reliable, functional & is licensed GPL... 

From my experience HandBrake has no peer.

I am quite eager to try this program (Handbrake) now!

...Ok!

So...by adding the 'PPA' (Personal Package Archive (I have seen that  acronym around lots)) - which I am sure is done through the Update  Manager - will download and install the Handbrake program?

Thanks again people for your help here, I know it's tedious to follow a  growing thread, but it is really appreciated by me, and I am sure many  others :smile:

Sincerely,

Scott

---

### Post by JohnAStebbins on 2011-01-19
> **cascade9 said:**
> For a newbie (sorry about that term), handbrake is going to be alot harder to install than a DVD ripper that is in the ubuntu repositories. DVD:rip is in the repos, and there are probably others (I havent searched for them) 

You should be able to see what DVD rippers are avaible from the software centre. Or just install from CLI- 

sudo apt-get install dvdrip

It's not hard to install handbrake.  It can be hard to find the necessary information to do so. From a terminal window:
```

sudo add-apt-repository ppa:stebbins/handbrake-releases
sudo apt-get update
sudo apt-get install handbrake-gtk

```

---

### Post by Segofam on 2011-01-19
> **JohnAStebbins said:**
> It's not hard to install handbrake.  It can be hard to find the necessary information to do so. From a terminal window:
```

sudo add-apt-repository ppa:stebbins/handbrake-releases
sudo apt-get update
sudo apt-get install handbrake-gtk

```

...and there it is, up in my Applications :)

I am guessing this post came from the Creator!
Is this information on the website?

Being a newbie - and proud of it - I have much to learn. Thank you all for your input and help.

@ John: If this program is as good as I hear that it is! then that command line info above would be of benefit to you if it was on the website, as I found it hard - as a newbie - to understand what it was that I was looking at and searching for.

...again, thanks so much for your help ;-)

Sincerely,

Scott

---

### Post by handy on 2011-01-20
> **JohnAStebbins said:**
> The repository maintainers are very picky about how packages must be built.  They frown upon statically linking libraries that are already available dynamically in the package archive.  HandBrake statically links several libraries for a variety of reasons.  We strongly discourage distributions from dynamically linking these libraries.  It causes mysterious bugs and a real support nightmare on the HandBrake forums.  So this puts the HandBrake maintainers and the distribution maintainers at an impasse.  We each have valid reasons for our rules, and the rules are contradictory.

This is a perfect example of the head banging against the wall phenomaly! ?


Anyway, thanks very much for presenting the OP with the handbrake solution. :)

---

### Post by Segofam on 2011-01-20
> **JohnAStebbins said:**
> From a terminal window:
```

sudo add-apt-repository ppa:stebbins/handbrake-releases
sudo apt-get update
sudo apt-get install handbrake-gtk

```

This has actually fixed my initial problem of backing up the DVD which is great.
But what do you suggest to convert that .m4v file so that it will  play on my Kogan Digital TV through the USB!?

ffmpeg doesn't seem to do it :-/

Scott

---

### Post by cascade9 on 2011-01-20
> **handy said:**
> This is a perfect example of the head banging against the wall phenomaly! ?

Anyway, thanks very much for presenting the OP with the handbrake solution. :smile:

Ahh, handy, I like your style sometimes. ;) 

I'm suprised myself. Even more so because I didnt think I'd find a program as popular as handbrake would be in the debian repos, but not ubuntus. 

> **Segofam said:**
> This has actually fixed my initial problem of backing up the DVD which is great.
But what do you suggest to convert that .m4v file so that it will  play on my Kogan Digital TV through the USB!?

ffmpeg doesn't seem to do it :-/

Scott

ffmpeg should do it. Maybe you've got the commands wrong, or maybe that $%^&$%& m4v is DRMed. If I recall correctly, sometimes videos that have 'issues' with the m4v filename work if you change the file to mp4. 

I can never remember the commands, so I tend to use GUIs for most things. If you want to try a GUI for Fmpeg, winFF works, and is in the ubuntu repos so it should be easy to install ;) 

BTW, since you are new you might not know about this site- 

[http://gtk-apps.org/](http://gtk-apps.org/)

If you are using a GTK based DE, like gnome (standard ubuntu) lxde or xfce its got a lot of nice programs to check out (warning! just because its there doesnt mean it will be easy to install, or anywhere near up to date).

For KDE, there is this- 

[http://kde-apps.org/](http://kde-apps.org/)

---

### Post by Segofam on 2011-01-20
> **cascade9 said:**
> If I recall correctly, sometimes videos that have 'issues' with the m4v filename work if you change the file to mp4.

If you want to try a GUI for Fmpeg, winFF works, and is in the ubuntu repos so it should be easy to install ;) 

BTW, since you are new you might not know about this site- 

[http://gtk-apps.org/](http://gtk-apps.org/)


I changed the file extension, still didn't convert with ffmpeg in the command prompt. I have been using command prompt for a little while with ffmpeg, and when I put the .m4v in (whether changed or  not) did not work!
There is still plenty I don't know about ffmpeg though!

I installed winFF but it wants to connect to FFplay.exe, but I can't find it :-/
Any suggestions on where to find it?

Thanks for the url too by the way, will check that out :)

Scott

---

### Post by cascade9 on 2011-01-20
> **Segofam said:**
> I changed the file extension, still didn't convert with ffmpeg in the command prompt. I have been using command prompt for a little while with ffmpeg, and when I put the .m4v in (whether changed or  not) did not work!
There is still plenty I don't know about ffmpeg though!

Can you play the file? If you cant play it, then its probbly DRMed (therefore, unplayable without some DRM-removal tool......and I wouldnt ask about one of them here, the admins/mods get antsie over that sort of thing) 

> **Segofam said:**
> I installed winFF but it wants to connect to FFplay.exe, but I can't find it :-/
Any suggestions on where to find it?

Thanks for the url too by the way, will check that out :)

Scott

Did you install it from the ubuntu repos? Asking for FFplay.exe sounds like its a windows version.

---

### Post by handy on 2011-01-20
> **cascade9 said:**
> Can you play the file? If you cant play it, then its probbly DRMed (therefore, unplayable without some DRM-removal tool......and I wouldnt ask about one of them here, the admins/mods get antsie over that sort of thing) 

If handbrake processed the DVD & made a backup file, then it should have removed any protection via libdvdcss(2).


Segofam, I'm probably misunderstanding your current problem but you may find the following useful in the future anyway. :)

DeVeDe is a great piece of software for converting a variety of movie file formats into the DVD format that home entertainment system DVD players use. I expect that it IS in the Ubuntu repos.

This is an informative page on DeVeDe:

[http://blogcritics.org/scitech/article/making-dvds-with-devede-in-linux/](http://blogcritics.org/scitech/article/making-dvds-with-devede-in-linux/)

---

### Post by cascade9 on 2011-01-20
> **handy said:**
> If handbrake processed the DVD & made a backup file, then it should have removed any protection via libdvdcss(2).

I'd assumed that it was a d/led/purchased .m4v, not a rip. ;)

---

### Post by handy on 2011-01-20
> **cascade9 said:**
> I'd assumed that it was a d/led/purchased .m4v, not a rip. ;)

Oh? My knowledge on this subject really is quite limited actually. Ripping backups with DVDShrink (lots of work in the past), SmartRipper (very rarely), DVD Fab Decryptor (extremely rarely), HandBrake-CLI (my tool of choice these days), & also extremely rarely, formatting a movie file into that which a standard DVD player can handle using DeVeDe.

So I know that there exists a whole world of different movie formats, tools for the job, jobs for the tools & more, that I don't actually know anything about. 

I'm very happy & grateful for the ones that I do use these days. Even though I have such a very limited variety (thankfully) of tasks for which I need them. :)

Which brings to my mind again the fact that FOSS is just absolutely amazing. :D

---

### Post by Segofam on 2011-01-21
> **handy said:**
> If handbrake processed the DVD & made a backup file, then it should have removed any protection via libdvdcss(2).


Segofam, I'm probably misunderstanding your current problem but you may find the following useful in the future anyway. :)

DeVeDe is a great piece of software for converting a variety of movie file formats into the DVD format that home entertainment system DVD players use. I expect that it IS in the Ubuntu repos.

This is an informative page on DeVeDe:

[http://blogcritics.org/scitech/article/making-dvds-with-devede-in-linux/](http://blogcritics.org/scitech/article/making-dvds-with-devede-in-linux/)

@ Handy: I backup the DVD's I _**buy**_ my 3 year old girl, but everynow and then, one will not back up! Thankfully I now have HandBrake - very impressed so far - and it has backed up the 3 DVD's so far -there are more - that other programs like Nero, K9, DVD Clone, Cloner DVD (there are more) have not been able to back up. The problem I am facing now is that HandBrake's two file extensions are .m4v and .mkv which are apparently the latest formats.
I read somewhere that .avi has not been supported since 2005, I think it was on the HandBrake forum, or maybe Stephen mentioned it earlier!
Now the issue is that my USB stick, when plugged into my Kogan DTV, does not recognise those two formats, and sadly, neither does my DVD player. I emailed Kogan, and they said that the USB stick when used by the Kogan DTV, will only accept .avi

DeVeDe I have not heard of, so there-fore never tried! But by the time you have read this, I am hoping to have tried it.

My command line knowledge of ffmpeg is ok at best, and I have not been able to get it to recognise either of then new formats.

Thanks for the info :)

Will let you know how it goes.

Kind regards,
Scott.

---

### Post by cascade9 on 2011-01-21
> **handy said:**
> Oh? My knowledge on this subject really is quite limited actually. Ripping backups with DVDShrink (lots of work in the past), SmartRipper (very rarely), DVD Fab Decryptor (extremely rarely), HandBrake-CLI (my tool of choice these days), & also extremely rarely, formatting a movie file into that which a standard DVD player can handle using DeVeDe.

Segofams post (below yours) let me figure it out... 

He wants to rip to .avi for use on TV. Handbrake only rips to .mkv, .mp4, m4v, so he wants to convert them. Nothing to do with DRMed m4vs, sorry about that. ;) 

BTW, there are DRMEd m4vs (and m4as), thanks apple.   

> **Segofam said:**
> @ Handy: I backup the DVD's I _**buy**_ my 3 year old girl, but everynow and then, one will not back up! Thankfully I now have HandBrake - very impressed so far - and it has backed up the 3 DVD's so far -there are more - that other programs like Nero, K9, DVD Clone, Cloner DVD (there are more) have not been able to back up. The problem I am facing now is that HandBrake's two file extensions are .m4v and .mkv which are apparently the latest formats.
I read somewhere that .avi has not been supported since 2005, I think it was on the HandBrake forum, or maybe Stephen mentioned it earlier!
Now the issue is that my USB stick, when plugged into my Kogan DTV, does not recognise those two formats, and sadly, neither does my DVD player. I emailed Kogan, and they said that the USB stick when used by the Kogan DTV, will only accept .avi

Which basicly means......dont use handbrake. 

You could always rip to .mkv or .mp4 then transcode to .avi, but that will just add time and degrade quality. As for getting .mkv or .mp4 to play on your TV, not really possible from everything I've seen. 

> **Segofam said:**
> DeVeDe I have not heard of, so there-fore never tried! But by the time you have read this, I am hoping to have tried it.

DeVeDe is for making VCD (video CDs), sVCD (super video CDs) etc.. from video files. It wont rip DVDs. In a lot of ways, with blank DVDs being not much more than blank CDs, its easier to just do a DVD->DVD copy.

---

### Post by handy on 2011-01-21
Segofam, it is unfortunate that you need .avi format, as it has not been held in high regard for a quite a number of years now. Which is why the HandBrake team dumped support for it amongst other formats.

I mentioned DeVeDe in case you needed to make a movie file playable on a standard DVD player. Such a video file doesn't have to have been obtained illegally. For example, you can even make the likes of YouTube vids playable on a DVD player via the use of DeVeDe.


Back to your original problem though:

If you can convert these DVDs for your daughter, to an .avi file, does that solve your problem completely?

---

### Post by Segofam on 2011-01-21
> **cascade9 said:**
> 
Did you install it from the ubuntu repos? Asking for FFplay.exe sounds like its a windows version.

I can play the .m4v and the .mkv files on my laptop!
..and I went through Ubuntu 10.4's Application>Ubuntu Software Centre to find winFF. Everytime I go to do something with  it, it comes up with "Could not find FFplay."
Sorry about putting the .exe in :-/

On another desk top I am using DeVeDe and that for all accounts appears to be changing the format to MPEG4 which I think is an .avi!?

If this works for me, then my issued will be solved :)

Scott.

---

### Post by Segofam on 2011-01-21
> **handy said:**
> 
Back to your original problem though:

If you can convert these DVDs for your daughter, to an .avi file, does that solve your problem completely?

Yes it will!

I am not into copying video's from other people's DVD's or P2P downloads etc or from Video stores, everyone needs to pay for what they want to see otherwise, in the long term, there will be no actors because no one supports them. Don't take that to deeply, but the scenario is there.
I just copy what I have bought, as my sticky not caring 3 year olds fingers have wrecked a few DVD's and we are  not made of money, we work hard to get what we have. If I could afford to buy the same DVD over and over I probably would.

Sincerely,

Scott.

---

### Post by Segofam on 2011-01-21
HandBrake has backed up the DVD's that no other backup program could do!

DeVeDe has converted the .m4v and .mkv files to DivX/MPEG-4 (.avi) which plays off my USB stick into my DTV :)

Having played it just a few minutes ago, the sound was excellent, the video quality needs to be adjusted somehow as it was very pixalated.

I don't have any knowledge on how to make it better, but I changed the bitrate setting from 592 to 1592 just to see what happens, this was with an .mkv file, the other file .m4v seems to automatically have a higher bitrate of 5000+!!! Not sure but I think I am well and truly on the right track now.
Scott.

---

### Post by cascade9 on 2011-01-21
> **handy said:**
> Segofam, it is unfortunate that you need .avi format, as it has not been held in high regard for a quite a number of years now. Which is why the HandBrake team dumped support for it amongst other formats.

.avi might have been surpased by other formats for size/quality, etc, but that doesnt help those of us who have a TV, DVDplayer or settop box which suports only .avi. 

> **Segofam said:**
> I can play the .m4v and the .mkv files on my laptop!
..and I went through Ubuntu 10.4's Application>Ubuntu Software Centre to find winFF. Everytime I go to do something with  it, it comes up with "Could not find FFplay."
Sorry about putting the .exe in :-/

No problem ;) 

I still dont know why its giving you that message though :( 

> **Segofam said:**
> On another desk top I am using DeVeDe and that for all accounts appears to be changing the format to MPEG4 which I think is an .avi!?

Nah, its not .avi. Basicly, DeVeDE should let you burn a disc that will play on most DVD players, but its not DVD format either.....Once you start looking into formats/containers things get very messy and complicated. 

Basicly- .avi is a 'container'. mp4 (and m4v/m4a) is a container as well.

Standalone players (like DVD players) that say they 'support .avi' normally means 'plays Xvid/Dvix with MP3 audio  in a .avi container'. Some players will also play other sound formats (like DTS or AC3), and some players will play Xvid/Divx video in a diferent container (like mp4/m4v). 

Converting straight to .avi is better than going .mkv/.m4v-> avi. Less conversions, less loss of quality, less CPU time, less sodding around.

---

### Post by Segofam on 2011-01-21
> **cascade9 said:**
> Basicly- .avi is a 'container'. mp4 (and m4v/m4a) is a container as well.

Thanks for the explanation, I was wondering what the 'container' was. It has come up in many threads, and I was lost as to what it was, but now I know.

Scott.

Quick end note:
After using HandBrake to backup, I found that if I converted to MPEG-4 using DeVeDe and compressing to 700meg CD size, it would really pixalate badly. But when I put the settings on 4.7 gig, the quality was really good.

All in all, I am very happy with the end result.

Thank you all for your help.

Kind regards,

Scott.

---

### Post by handy on 2011-01-21
> **Segofam said:**
> 
...

Quick end note:
After using HandBrake to backup, I found that if I converted to MPEG-4 using DeVeDe and compressing to 700meg CD size, it would really pixalate badly. But when I put the settings on 4.7 gig, the quality was really good.

All in all, I am very happy with the end result.

Thank you all for your help.

Kind regards,

Scott.

I'm glad you found a solution. :)

---

### Post by Geffers on 2011-02-07
> **handy said:**
> For those that don't know, (as I didn't until I had to solve the problem myself) DVD Decryptor will break all forms of copy protection that the makers of DVDs use. (At least last time I looked anyway.)


Has always worked for me using DVDs, tried it to remove DRM protection and that does not appear to work :(

Geffers

---

### Post by Segofam on 2011-02-07
Hi there Geffers,
I actually got away from DVD Decryptor and am now using HandBrake to recode, and then to turn them to avi or mpeg4 I am using DeVeDe. HandBrake worked where other programs failed, including DVD Decryptor!
Regards,
Scott

---

### Post by Geffers on 2011-02-07
Hi Scot,

I was recommended handbrake when I needed to convert some ts files for playback on TV, it has a good reputation but I had problems with it (can't recall what now) so did not persist.

I'll have to give it another go.

Geffers

---

### Post by Segofam on 2011-02-07
> **Geffers said:**
> I'll have to give it another go.

Geffers
Geffers,
If you read back through the thread, you will see that the Creator of HandBrake got involved, and gave some command line.
I had spent much time using various programs, but as soon as he gave the command line info, it worked straightup!
Perhaps - if you want - you could check out the HandBrake Forums!
Regards,
Scott.

---

### Post by Segofam on 2011-02-07
> **JohnAStebbins said:**
> It's not hard to install handbrake.  It can be hard to find the necessary information to do so. From a terminal window:
```

sudo add-apt-repository ppa:stebbins/handbrake-releases
sudo apt-get update
sudo apt-get install handbrake-gtk

```

Geffers,
Try the quoted commands by JohnAStebbins.
Scott

---

### Post by handy on 2011-02-07
> **Segofam said:**
> Hi there Geffers,
I actually got away from DVD Decryptor and am now using HandBrake to recode, and then to turn them to avi or mpeg4 I am using DeVeDe. HandBrake worked where other programs failed, including DVD Decryptor!
Regards,
Scott

Just a smallish point here. But you can use HandBrake to create .mp4 files (I do) instead of .mkv. What effect that will have on your resulting encoding time with DeVeDe (if it is still needed you'll have to test & find out?) I don't know. I find that I get better quality visuals in movies using .mp4 as opposed to .mkv.

---

### Post by Segofam on 2011-02-08
Hi Handy,
I didn't know that, perhaps I should search through the settings more too!
If I can't figure it out, you know I am going to come back here to solve that now too don't you!? ;-)
Cheers,
Scott

---

### Post by handy on 2011-02-08
> **Segofam said:**
> Hi Handy,
I didn't know that, perhaps I should search through the settings more too!
If I can't figure it out, you know I am going to come back here to solve that now too don't you!? ;-)
Cheers,
Scott

If you are using the GUI for HandBrake, I can't help you as I've never even seen it.

If you are using HandBrake-CLI then I can help you as adding .mp4 to the end of your output file name is enough, as seen in the following command string:

```
HandBrakeCLI -t --main-feature -i /media/dvd -o NAME.HERE.mp4 -e x264 -b 1000 -B 192 -s 1 --subtitle-burn 
```

---

### Post by Segofam on 2011-02-08
G'day Handy,
I do use the GUI, but I am happy to try the CLI also, if it lets me!
However, the GUI can actually be set for MPEG-4, but like I said, I will give the CLI ago also, just because :)
Scott

---

### Post by Geffers on 2011-02-08
> **Segofam said:**
> Geffers,
If you read back through the thread, you will see that the Creator of HandBrake got involved, and gave some command line.
I had spent much time using various programs, but as soon as he gave the command line info, it worked straightup!
Perhaps - if you want - you could check out the HandBrake Forums!
Regards,
Scott.

Scott,

Thanks very much for the offer, I'll check out this thread first before you go wading through the handbrake forum.

For a while my only Ubuntu access is via a netbook so not the best for any video conversion - though it does work :p

Geffers

---

### Post by mips on 2011-03-28
Ubuntu 10.10 64 bit

Trying to install DVD Decrypter in WINE and when I start it it says:
> **Download and installation process for GOM Player**

Please wait...

This carries on but there is no network connectivity on my router or System Monitor.

Later it just stops with:
> **No Internet connection detected**

Softonic Downloader needs an internet connection to function. Please connect and try again.

Any ideas?

---

