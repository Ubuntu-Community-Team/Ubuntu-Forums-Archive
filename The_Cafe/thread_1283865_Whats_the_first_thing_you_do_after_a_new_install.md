---
title: "Whats the first thing you do after a new install?"
date: 2009-10-06
forum: The Cafe
---

### Post by carnagex420x on 2009-10-06
Just a random thought, but whats the first thing you do with your system after a fresh new install? Start stripping stuff from it, start adding to it, or just make it pretty?

-I strip it BTW

---

### Post by slakkie on 2009-10-06
Install zsh, openssh-server, install my shell profile (.vimrc, screenprofiles, all kind of functions I would like to have access too), install screen.

If it is a GUI system, logout from the GUI, copy a .kde dir over from one of my boxes and login again. 

Install multimedia codecs (have a script which does that).

But I don't really do this often, only when testing Ubuntu in a VM and then usually I don't copy the .kde dir, I'll just use Gnome (just to annoy myself ;)).

---

### Post by RichardLinx on 2009-10-06
Add to it, followed by getting rid of a few unwanted applications that come with it (When it comes to Ubuntu anyway) then I run:
```
sudo apt-get autoremove
```
```
sudo apt-get autoclean
```
It's one of the commands that stuck with me even though as of 8.10 Ubuntu has a GUI tool to do exactly what those commands do - CLI is faster in this case.

---

### Post by lisati on 2009-10-06
Apply updates, then (re)install/configure Samba

---

### Post by Sean Moran on 2009-10-06
Strip might not be quite the right word.  More like take a copy of it while still fresh to rsync back if I want to try some experimental config and things start to bulge from there as new applications get used.  Then I can just put it back if I don't like the end result of the changes.

The ultimate goal is to have the custom install process handle the config so well that Skype might be the only commercial package to add and everything already setup on .iso and saved just the way I like it before install.  Only problem is, I still haven't worked out the exact way I want it to be yet.  I've changed the top panel around 100 times by now, and what looked perfect last night now looks rather second-rate this morning.

---

### Post by hoppipolla on 2009-10-06
with Ubuntu... I pretty much just use it.

It really does do most things "out of the box".

I guess I do replace a few programs though - Rhythmbox with Banshee, Firefox with Chromium... and I'll tend to install a few tools such as parcellite and gufw. This is all pretty optional though, I'd be happy using it without those changes :)

---

### Post by Bezmotivnik on 2009-10-06
Pray, mostly.

---

### Post by siimo on 2009-10-06
I normally use the server install to install minimal packages then X and XFCE.  If i do a desktop install however, i stripe it bare and yes I take extreme measures to ensure I get rid of all the bloatware I don't need e.g. remove X. [Which in turn removes all X applications] Then install X and XFCE.

---

### Post by NoaHall on 2009-10-06
Install graphics card driver, use my stored .debs to install Opera, Songbird, and Skype. Then bootchart, edit .bashrc to add some aliases, and links to some  useful scripts I made, install aMSN, delete bottom panel on every screen, add AWN, change theme

---

### Post by HappinessNow on 2009-10-06
Smoke a cigarette...oh wait wrong answer.

Go to sleep.

---

### Post by crepito on 2009-10-06
Normally i use the alternative CD in order to have a basic system after install. Than, i just add what i want. That way i don't need to remove stuff that i don't use.

---

### Post by ctrlmd on 2009-10-06
update

---

### Post by beercz on 2009-10-06
Login

---

### Post by PhoHammer on 2009-10-06
I usually just configure/customise it, but I need to start remembering to strip it of
all the "junk" I don't use...

---

### Post by swoll1980 on 2009-10-06
*drum roll* Restart it!

________________________________________BA-ZING!!

---

### Post by Jesus_Valdez on 2009-10-06
Come here to the ubuntuforums and look for the multimedia [HOWTO] and fix whatever pulseaudio did wrong this time.

---

### Post by starcannon on 2009-10-06
The first thing I do is:

[LIST=1]
[*]Add Medibuntu repo's
[*]Install ubuntu-restricted-extras
[*]Get updates
[*]Reboot
[*]Enable proprietary hardware drivers
[*]Reboot
[*]Install any additional software I need from repos
[*]Install MS Office using wine.
[*]Start computing, and tune as I go.
[/LIST]
My installs take a total of about 2 hours from the time I the install CD in, until the time I get MS Office installed. Not bad I don't think. I could make it quicker by remastering my install, that would leave a lot less stuff to download, I may do that one of these days. I think that could get my install down to an hourish.

---

### Post by koleoptero on 2009-10-06
I order a pizza and some beers and celebrate the occasion.

---

### Post by Kingsley on 2009-10-06
I make sure my Windows and music/video partitions are mounted and reading correctly. Then, I get the codecs installed.

---

### Post by openfly on 2009-10-06
First thing I do after provisioning an Ubuntu system is I go straight away to the nearest playground and kick a toddler in the knee.

---

### Post by ice60 on 2009-10-06
look for the 0-days then pwn every one on ubuntuforums lol

---

### Post by mharrison on 2009-10-06
Typically, I remove all of the programs that I won't be using....install the ones I do want, run update, reboot, install NVidia driver, reboot, start restoring my data.  

Runs me about 40 minutes, depending on how fast the copy from my server takes.

---

### Post by anonymous_user on 2009-10-06
I install the minimal Ubuntu ISO, I add apps, I strip some packages, then I customize.

---

### Post by Bachstelze on 2009-10-06
Add to it. Usually the first run is:

```
sudo apt-get install zsh vim openssh-server build-essential ghc6 php5-cli
```

plus xorg if it's for a desktop.

---

### Post by Cam42 on 2009-10-06
Enable metacity compositing, install GNOME Do, turn on Docky, move both panels down to the bottom, copy all my music from a flash drive, find some cool wallpaper, install/configure conky.

---

### Post by SuperSonic4 on 2009-10-06
Update

no version will ever be totally up to date

---

### Post by Bachstelze on 2009-10-06
> **SuperSonic4 said:**
> Update

no version will ever be totally up to date

Wrong. The minimal CD will install an up-to-date version, since all packages will be downloaded in the first place.

---

### Post by PhoHammer on 2009-10-06
> **koleoptero said:**
> I order a pizza and some beers and celebrate the occasion.

Memo to self: replicate koleoptero's post-install celebration.

---

### Post by undecim on 2009-10-06
I used to strip it down some after a fresh install, but now that I have a computer that can do it without missing a beat, I prettify all out: Compiz (360 degree panorama skydome from inside a transparent cube), Gnome Do, AWN, etc...

I still have yet to see any video tearing or jerkiness from it at all, even when running two flash videos on adjacent desktops and moving the cube around with it like that.

Oh, and having a touchscreen makes it all twice as awesome. Though it's supposed to be a multi-touch screen, I can't get that functionality working with compiz (yet!)

---

### Post by TwiceOver on 2009-10-06
I would say beyond getting all the devices working properly and update && upgrade...

I remove the bottom panel, delete the ff and help icon from the top panel.  Add trash, running apps, and workspace switcher to the top panel.

Just kinda feels funky with two panels so the bottom one has to go ASAP.

---

### Post by samjh on 2009-10-06
For Ubuntu, I remove programs I don't use: Evolution, Ekiga, Gnome Games, Tomboy, F-Spot.

---

### Post by Grifulkin on 2009-10-06
Minimal FTW and then Add programs then customize.

---

### Post by wilee-nilee on 2009-10-06
A personalized happy dance, oh then I brag to my friends. ;)

---

### Post by carnagex420x on 2009-10-07
> **samjh said:**
> For Ubuntu, I remove programs I don't use: Evolution, Ekiga, Gnome Games, Tomboy, F-Spot.

Agreed. Bluez, CUPS, and the Media Players go too. I like to get rid of everything before I start adding the stuff I want to it.

---

### Post by donniezazen on 2009-10-07
Install Medibuntu.

---

### Post by toupeiro on 2009-10-07
Install PostGRES and MySQL, install latest release of gnome-do, add medibuntu, install some studio packages like rosegarden and audacity, install Handbrake, update wine to the latest version (for WoW), configure evolution for all my google services.

Then its a mixed bag of other things.

---

