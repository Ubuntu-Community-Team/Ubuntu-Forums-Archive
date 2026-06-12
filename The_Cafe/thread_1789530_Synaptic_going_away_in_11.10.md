---
title: "Synaptic going away in 11.10?"
date: 2011-06-23
forum: The Cafe
---

### Post by toupeiro on 2011-06-23
Is this a really bad and horribly belated April fools joke? (emphasis on joke)

[http://techie-buzz.com/foss/synaptics-removed-ubuntu-11-10.html](http://techie-buzz.com/foss/synaptics-removed-ubuntu-11-10.html)

---

### Post by compmodder26 on 2011-06-23
kinda stupid if you ask me.  But nevertheless all it takes to get it on your computer is a simple "sudo apt-get install synaptic"

---

### Post by NightwishFan on 2011-06-23
Even if not the default it will still be in the repos. I do not see much of a downside of having it not the default.

---

### Post by LowSky on 2011-06-23
I hate the Software center... its slow, and it hangs every time I try to use it. Plus trying to install a DEB used to be easy, you clicked on it and Gdebi handled the work, now it loads the software center and asks me dumb questions about trusting the source.

Synaptic is fast and pretty user friendly if you ask me.

I'm tired of buggy software being used in Ubuntu.

---

### Post by 3Miro on 2011-06-23
I installed the Alpha 1 the other day, Synaptic was there by default.

The .iso was a bigger than what you can fit on a CD (had to use USB), but this is normal for an Alpha. Some software would be removed, but currently Synaptic is part of Alpha 1.

---

### Post by NightwishFan on 2011-06-23
> I'm tired of buggy software being used in Ubuntu.
Likewise.

---

### Post by cariboo on 2011-06-23
Synaptic isn't going anywhere, it just won't be installed by default, as was proposed when the Software Center was first released. Old news is old news.

---

### Post by LowSky on 2011-06-24
> **cariboo907 said:**
> Synaptic isn't going anywhere, it just won't be installed by default, as was proposed when the Software Center was first released. Old news is old news.

But Software Center was supposed to be awesome, and it has not lived up to the task. Its buggy, intrusive, and is replacing applications that were simple and fluid. And I hate installing great applications I have used for years that now suddenly are not included... Cough... Pidgin...cough

---

### Post by wolfen69 on 2011-06-24
The devs are trying to shave MB's wherever possible to keep the image under 700mb. I don't blame them. Casual users will be satisfied with the software center, and more advanced users will apt-get synaptic. In ubuntu's case, it's no big deal.

If Canonical makes a DVD the norm, they will lose some users who don't have dvd burners, or have limited bandwidth.

---

### Post by doorknob60 on 2011-06-24
Personally, I much prefer Synaptic to the software center, but they have a lot to fit on a 700 MB CD, so no point in having two GUI package managers, easy enough to install Synaptic after the fact :) And yeah Software Center is obviously better for newbies, so i can't say I disagree with this decision, it's fine with me.

---

### Post by christopher.wortman on 2011-06-24
I agree with Canonicals decision to remove synaptic, I didn't even know it was there. Also they should remove LibreOffice by default, and only have it as an "install on demand" because I rarely use office. Having it on the Live CD is kinda pointless.

---

### Post by wolfen69 on 2011-06-24
> **LowSky said:**
> But Software Center was supposed to be awesome, and it has not lived up to the task. Its buggy, intrusive, and is replacing applications that were simple and fluid. And I hate installing great applications I have used for years that now suddenly are not included... Cough... Pidgin...cough

You do realize that if they make it perfect *for you*, other people will be ticked off? There is no way to please everyone ootb. How long does it take to install anyway? <facepalm>

---

### Post by wolfen69 on 2011-06-24
> **christopher.wortman said:**
> I agree with Canonicals decision to remove synaptic, I didn't even know it was there. Also they should remove LibreOffice by default, and only have it as an "install on demand" because I rarely use office. Having it on the Live CD is kinda pointless.

Again, another example of someone saying it should be tailored to *their* usage patterns. It doesn't work that way.

---

### Post by beew on 2011-06-24
I never use the software centre, it is a piece of crap. It is slow, bulky and on startup uses close to 100% cpu on my older machine. I think Synaptic is really easy to use and full of functions so I have no idea how it would be considered not user friendly enough to new users, even idiots can use it after a few minutes! It is a lot more intuitive than say, navigating around Unity.

Just one more thing to do after intsall: sudo apt-get install synaptic. Not a big deal to me. Since 10.10 I am installing gdebi myself anyway,it is handy for installing .deb packages by right clicking, without it the Software Centre would do the job, but with gdebi I would have finished installing by the time SC starts.

Unfortunately  the new users would be stuck with the SC without anyone to tell them, just like most new users after 10.04 do not know about gdebi (I wouldn't have known if I haven't used it in 10.04, nobody really mentions it in the forum, always the Software Centre, screw the SC)

Note to myself: In the future when I answer questions on the forum  regarding installing softwares by new users the first step would always  be "sudo apt-get install synaptic"

P.S.Actually I would like to remove the Software Centre, but doing so would remove the Ubuntu desktop. Now in 10.04 and 10.10 UD is just a meta package and it is harmless to remove it (I did it with 10.04) but with Unity I am a bit hesitant, it may not work the same way. Anyone has tried removing the Ubuntu desktop?

---

### Post by beew on 2011-06-24
Oh, if you use Kubuntu you would have to install Synaptic yourself anyway. The kpackagekit is yet another piece of trash.

What I don't understand is why do they keep making horrible, slow and bloated applications defaults while there are much better ones if you know your way around. Way to get new users. I think most people who would give Linux even a try understand there is a bit of a learning curve, dumbing down to the point of making things a lot slower, bloated and with less options is shooting oneself on the foot, the new user would not be able to see the strength of Linux. And Synaptic is hardly a power user tool.

---

### Post by beew on 2011-06-24
> **cariboo907 said:**
> Synaptic isn't going anywhere, it just won't be installed by default, as was proposed when the Software Center was first released. Old news is old news.


Yes, but new users wouldn't know that you can install synaptic with just one line of command and people giving advice in the forum would be saying things like "Open the Software Centre and wait a minute for it to start.." instead of "firing up Synaptic..". I hardly hear anyone telling new users to install gdebi in order to install .deb (you can always use dpkg -i but I am talking about one click installing) I am lucky to have started using Ubuntu before the massive dumbing down so I know there are better options around, the new users would not be so lucky.

---

### Post by Primefalcon on 2011-06-24
I agree with the decision, the users that want it, will either just use apt-get or even the software center to install synaptic.

---

### Post by beew on 2011-06-24
> **Primefalcon said:**
> I agree with the decision, the users that want it, will either just use apt-get or even the software center to install synaptic.

How would the user want it if he/she doesn't know that it exists?

With applications like media players and photo managers the users will likely look around to find what suit their need best but with system sofwares like package manager new users will usually just use the default. It would be a pity if all they know is the bloatware with few functions known as the Software Centre.

---

### Post by Paqman on 2011-06-24
> **doorknob60 said:**
> no point in having two GUI package managers

True. I still use Synaptic a lot, but I don't see why it *needs* to be on the CD.

---

### Post by Dustin2128 on 2011-06-24
Not a fan of the decision, but not my problem, I got off the ubuntu train 3 or 4 versions ago. Except for the server- really great there imho. I get as much uptime as my electrical company can handle (typically 3 days ;))!

---

### Post by cariboo on 2011-06-24
> **beew said:**
> Yes, but new users wouldn't know that you can install synaptic with just one line of command and people giving advice in the forum would be saying things like "Open the Software Centre and wait a minute for it to start.." instead of "firing up Synaptic..". I hardly hear anyone telling new users to install gdebi in order to install .deb (you can always use dpkg -i but I am talking about one click installing) I am lucky to have started using Ubuntu before the massive dumbing down so I know there are better options around, the new users would not be so lucky.

I'm not sure what kind of hardware you use, but even on my two year old system [noparse](AMD Athlon II X2 240 CPU, 2GiB ram and Nvidia GT218)[/noparse] the software center loads instantly. 

I don't understand why people complain about having to install extra packages, most of us set up a system to the way we like it, then use something like:

```
dpkg --get-selections > installed-software
```

to create a list of installed packages, then use:

```
dpkg --set-selections < installed-software
```

followed by:

```
dselect
```

to finish setting up the system after the initial install.

You don't even have to wait while the packages are installed, you can do something else as Linux is a true multitasking system.

---

### Post by beew on 2011-06-24
> **cariboo907 said:**
> I'm not sure what kind of hardware you use, but even on my two year old system [noparse](AMD Athlon II X2 240 CPU, 2GiB ram and Nvidia GT218)[/noparse] the software center loads instantly. 

I don't understand why people complain about having to install extra packages, most of us set up a system to the way we like it, then use something like:

```
dpkg --get-selections > installed-software
```to create a list of installed packages, then use:

```
dpkg --set-selections < installed-software
```followed by:

```
dselect
```to finish setting up the system after the initial install.

You don't even have to wait while the packages are installed, you can do something else as Linux is a true multitasking system.

Yeah I know that but I was talking about new user experience. 

My hardware consists of 2 laptops. A 1.5 year old laptop which I use as my main machine. SC "holds up" but hardly stellar. Synaptic does the same job much faster and installing .deb I use gdebi, like I said the installation would be finished by the time the SC is ready. (I know about dpkg but we are talking about one click install)

My other machine is a 6 year old hand me down. SC is a monster there. 

I am curious that you said "even on my two year old system". A two year old system is quite new for most people I know. We don't change computer every year even if we have the money, bad for the environment. :)

---

### Post by Paqman on 2011-06-24
> **cariboo907 said:**
> 
I don't understand why people complain about having to install extra packages, most of us set up a system to the way we like it, then use something like:

```
dpkg --get-selections > installed-software
```

to create a list of installed packages, then use:

```
dpkg --set-selections < installed-software
```

followed by:

```
dselect
```


Or even better, use [apt-clone](apt:apt-clone). In addition to your packages from the repos it saves your sources list, manually installed packages, and a whole bunch of other neat stuff.

---

### Post by speedwell68 on 2011-06-24
There is no drama here really, for those that know it'll be synaptic and gdebi for those that know and the USC for those that don't.

---

### Post by cariboo on 2011-06-24
> **beew said:**
> Yeah I know that but I was talking about new user experience. 

My hardware consists of 2 laptops. A 1.5 year old laptop which I use as my main machine. SC "holds up" but hardly stellar. Synaptic does the same job much faster and installing .deb I use gdebi, like I said the installation would be finished by the time the SC is ready. (I know about dpkg but we are talking about one click install)

My other machine is a 6 year old hand me down. SC is a monster there. 

I am curious that you said "even on my two year old system". A two year old system is quite new for most people I know. We don't change computer every year even if we have the money, bad for the environment. :)

New users are going to use the default install, until they get comfortable with their system, the most they may do is change the background, and that's about it, it's only the geeks/nerds that start looking for ways to make Ubuntu fit the way they use a system.

I have about 10 systems that are in weekly use they range from an Apple G4 (release year 1999) to a Compaq Mini 110  (release year 2010). Seven of the systems run Ubuntu/Debian, of the other 3, 2 run XP, and the other runs OSX. The latest addition to the local network is a P4, added today, runs a [Turnkey Linux ]("http://www.turnkeylinux.org/")dokuwiki appliance.

BTW all computers are bad for the environment no matter how old/new they are. If you fancy yourself a  treehugger/environmentalist, you wouldn't own your own computer, shared systems are the way to go.

---

### Post by nothingspecial on 2011-06-24
](*,)](*,)](*,)](*,)](*,)](*,)](*,)

It's not even July and it's started already.........

---

### Post by Grenage on 2011-06-24
A new user types "Libre Office" in Software Centre, and they are presented with a few simple choices.

A new user types "Libre Office" into Synaptic, and they are presented with an immense list of irrelevant packages - plus the one or two they really need.

Software centre is absolutely the right direction to take, and you'd have to be completely myopic to think otherwise.  I use apt from a terminal, but that doesn't mean most users will want to.

---

### Post by 3rdalbum on 2011-06-24
Removing Synaptic from the default install has been planned for a long time. By the time Ubuntu 11.10 is released, the Software Center should be a lot more capable than it is now. Power users can still install Synaptic, and they don't even have to use Software Center to install Synaptic.

It's a smart idea to save some space on the CD. Let's face it, Synaptic is very useful, but it's probably a bit too geeky for the default Ubuntu install.

---

### Post by frankbooth on 2011-06-24
> **grenage said:**
> a new user types "libre office" in software centre, and they are presented with a few simple choices.

A new user types "libre office" into synaptic, and they are presented with an immense list of irrelevant packages - plus the one or two they really need.

Software centre is absolutely the right direction to take, and you'd have to be completely myopic to think otherwise.  I use apt from a terminal, but that doesn't mean most users will want to.

+1

---

### Post by LowSky on 2011-06-24
my whole point is bloat. software center runs poorly. Try to install multiple applications and it chokes. i'm running great hardware and i can watch sc stall. 

btw: typing libre office gets no hits in sc. type libreoffice you get 11.

the same thing occurs in synaptic, except I get 391 packages listed with libreoffice, including language packs... very important to some I might think...

i hate the argument that its better for new users.. how much user testing is really being done. i don't see canonical doing new user test groups. what about the old users, why alienate your user base? its business 101, its cheaper to keep your current customers than to get new ones.

---

### Post by Paqman on 2011-06-24
> **LowSky said:**
> my whole point is bloat. software center runs poorly. Try to install multiple applications and it chokes. i'm running great hardware and i can watch sc stall. 

No-one's forcing you to use it.

> 
i hate the argument that its better for new users.. how much user testing is really being done. i don't see canonical doing new user test groups. what about the old users, why alienate your user base? its business 101, its cheaper to keep your current customers than to get new ones.

Canonical does do usability testing. I know, I've done some.

I really don't see how tweaking the default set of apps on the CD is going to "alienate" existing users. People always wail and gnash their teeth when their favourite app gets chopped from the CD, but does it really matter? The defaults are there for new users, anybody who's been using Ubuntu for a while will have a wee list of stuff to install on a new system anyway. If you want GIMP and Synaptic, just install them.

---

### Post by Zero2Nine on 2011-06-24
It's not a big problem (synaptic is only an apt-get away) but it seems like another effort to 'dumb down' Ubuntu a little. Remove configuration options, remove a tool for more control over package installation etc. Again no big issue, in the end everything can still be customized one way or another but the ootb experience gets more limited. Maybe that's a smart move, time will tell.

---

### Post by toupeiro on 2011-06-24
What mechanism is there in ubuntu other than synaptic to select repository mirrors for packages, including the built in latency selector?  I've yet to find anything in software center to replicate this.  for example, I only get about 90-100K/sec for the "Default US server"  I get about 20mbit from utexas.edu.  Ubuntu already removed software sources from the menu, so the only way I know to get to this now is synaptic.

---

### Post by Ric_NYC on 2011-06-24
How to fix the "broken packages" without Synaptic?

---

### Post by Grenage on 2011-06-24
> **toupeiro said:**
> What mechanism is there in ubuntu other than synaptic to select repository mirrors for packages, including the built in latency selector?  I've yet to find anything in software center to replicate this.  for example, I only get about 90-100K/sec for the "Default US server"  I get about 20mbit from utexas.edu.  Ubuntu already removed software sources from the menu, so the only way I know to get to this now is synaptic.

Synaptic will still be available, just not installed by default.

---

### Post by Paqman on 2011-06-24
> **toupeiro said:**
> Ubuntu already removed software sources from the menu, so the only way I know to get to this now is synaptic.

You can also get to Software Sources from Update Manager or Software Centre.

---

### Post by Quadunit404 on 2011-06-24
> **Ric_NYC said:**
> How to fix the "broken packages" without Synaptic?

Exactly. If you have broken packages and the USC detects it, it attempts to reinstall the dependencies of the broken packages rather than give you the option to remove the broken packages (good if you want to remove something and you got the broken packages from said removal) or reinstall them (which, as I said, if you want to remove something and don't want it back, you get back whatever you removed even if you don't want it. That's led me to not rely on the USC for fixing APT after it breaks.

Unless this changes before October, Synaptic will become one of the first apps I add to a fresh installation. Along with Opera and Skype and the like.

---

### Post by bruno9779 on 2011-06-24
> **Paqman said:**
> You can also get to Software Sources from Update Manager or Software Centre.

Software sources is still installed. You can re-enable the icon by right-clicking the menu bar and choosing edit menus.

Nonetheless I am not liking the direction that Ubuntu is taking lately.
11.04 is the fist upgrade I reversed since my first 7.04 install. by the look of things, 11.10 will be the second one.

I love synaptic. SC is NOT a viable replacement to it. No purge function (completely remove in synaptic), no fix broken packages, no view over different version/smaller libraries, no double filtering (ctrl+f and serch bar do that), no lock version and many more.

Unless SC is getting a very major update, NOT INSTALLING SYNAPTIC BY DEFAULT IS A CRAPPY IDEA!!

---

### Post by el_koraco on 2011-06-24
> **toupeiro said:**
> What mechanism is there in ubuntu other than synaptic to select repository mirrors for packages, including the built in latency selector?  I've yet to find anything in software center to replicate this.  for example, I only get about 90-100K/sec for the "Default US server"  I get about 20mbit from utexas.edu.  Ubuntu already removed software sources from the menu, so the only way I know to get to this now is synaptic.

Software Center - Edit - Software Sources. The software sources selection list is not a part of Synaptic, but a separate debian package, called software-properties-gtk (or kde). You can invoke it from the run dialog (or krunner) without even opening Synaptic. Just gksudo software-properties-gtk (or kde).

---

### Post by Ric_NYC on 2011-06-24
[IMG]http://postimage.org/image/36bewwfno/[/IMG]

---

### Post by Roasted on 2011-06-24
I remember when Ubuntu announced they were removing Gimp from the default installation.

Whoaaaaa that was a massive outburst...

The more time goes on, the more software I find to use outside of Ubuntu's default install. This is for good reason, since I find it absolutely remarkable Ubuntu still fits all of this stuff onto a 700mb CD.

If they remove Synaptic from the default install, I'm perfectly fine with it. Love it or hate it, Software Center is easier to use for first time users. Why have two applications on the default install that do the same thing?

While I may not be gung-ho about seeing it gone, I certainly won't shed a tear when I realize I just have to run a quick apt-get to get it back.

Speaking of which, does anybody else out there have a Google Doc like I do with a long "sudo apt-get install...." command with like 70 applications you use following? I find it so handy to use with each new install I do. One command and blam - I've got tons of applications to use just like that. Adding Synaptic to it is hardly an issue.

---

### Post by malspa on 2011-06-24
> **Roasted said:**
> While I may not be gung-ho about seeing it gone, I certainly won't shed a tear when I realize I just have to run a quick apt-get to get it back.

I certainly won't, either!

> **Roasted said:**
> Speaking of which, does anybody else out there have a Google Doc like I do with a long "sudo apt-get install...." command with like 70 applications you use following? I find it so handy to use with each new install I do. One command and blam - I've got tons of applications to use just like that. Adding Synaptic to it is hardly an issue.

That's a great idea!

---

### Post by Paqman on 2011-06-24
> **Roasted said:**
> 
Speaking of which, does anybody else out there have a Google Doc like I do with a long "sudo apt-get install...." command with like 70 applications you use following? I find it so handy to use with each new install I do. One command and blam - I've got tons of applications to use just like that. Adding Synaptic to it is hardly an issue.

Yep, have been meaning for ages to put it into a proper script and automate all my post-install stuff. One click setup ftw.

---

### Post by Linuxratty on 2011-06-24
> **NightwishFan said:**
> Even if not the default it will still be in the repos. 

 But for how long!?  First they take away my old,reliable Gnome and replace it with an over sized cell phone interface,now they take away my Synaptic!
What bloody next!? Yeah,I know it's easy as falling off a log to get it back,but that's not the point.What worries me is they will kill it.

---

### Post by el_koraco on 2011-06-24
> **Paqman said:**
> Yep, have been meaning for ages to put it into a proper script and automate all my post-install stuff. One click setup ftw.


The last time you use an old install

```
dpkg --get-selections > programs
```

On the new install 

```
sudo dpkg --set-selections < programs
sudo apt-get -y update
sudo apt-get dselect upgrade
```

---

### Post by el_koraco on 2011-06-24
> **Linuxratty said:**
> But for how long!?  First they take away my old,reliable Gnome and replace it with an over sized cell phone interface,now they take away my Synaptic!
What bloody next!?

Synaptic is a Debian tool. Even if by some miracle the nasty people at Canonical removed it from Ubuntu, you could still use the package from Debian.

---

### Post by Paqman on 2011-06-24
> **Linuxratty said:**
> But for how long!?

A long, long, long time. Removing something from the CD has never meant it gets dropped from the repos. Why would it?

Ubuntu didn't take Gnome 2 away from you btw. Gnome did.

---

### Post by Paqman on 2011-06-24
> **el_koraco said:**
> The last time you use an old install

```
dpkg --get-selections > programs
```

On the new install 

```
sudo dpkg --set-selections < programs
sudo apt-get -y update
sudo apt-get dselect upgrade
```

There's an even better tool than that available now: apt-clone.

---

### Post by toupeiro on 2011-06-24
Thanks for all the replies.  I will check when I get home from work.  Admittedly I haven't checked it in 11.04, it was a previous version, and I didn't see this functionality

---

### Post by Mr. Picklesworth on 2011-06-24
> **el_koraco said:**
> The last time you use an old install

```
dpkg --get-selections > programs
```

On the new install 

```
sudo dpkg --set-selections < programs
sudo apt-get -y update
sudo apt-get dselect upgrade
```

There is a problem with that: you're manually installing all your automatically installed packages. Ends up creating some bloat in the long run, since they won't be removed automatically if you remove their dependants. aptitude, and I'm sure a few other tools, will output your package list with each package annotated to describe stuff like how it was installed. You can then use a little regex magic to grab only the manually installed ones.
(Sorry, I forget the exact details, but they're floating around somewhere).

And don't worry, folks: apt-get will always be there out of the box for your advanced package management needs.

---

### Post by cgroza on 2011-06-24
> **christopher.wortman said:**
> I agree with Canonicals decision to remove synaptic, I didn't even know it was there. Also they should remove LibreOffice by default, and only have it as an "install on demand" because I rarely use office. Having it on the Live CD is kinda pointless.
Ubuntu does not spin around you. I use it and I need it for my school work.

---

### Post by cgroza on 2011-06-24
> **beew said:**
> How would the user want it if he/she doesn't know that it exists?

With applications like media players and photo managers the users will likely look around to find what suit their need best but with system sofwares like package manager new users will usually just use the default. It would be a pity if all they know is the bloatware with few functions known as the Software Centre.
The new users will be more happy with the software centre. They will be able to navigate through apps more easily, and I do not think average Joe cares about synaptic anyway.

---

### Post by Primefalcon on 2011-06-24
> **beew said:**
> How would the user want it if he/she doesn't know that it exists?

With applications like media players and photo managers the users will likely look around to find what suit their need best but with system sofwares like package manager new users will usually just use the default. It would be a pity if all they know is the bloatware with few functions known as the Software Centre.
The thing is the software center is a lot easier tool to use, and for the people that know about synaptic, its probably too complicated of a tool anyhow, the software center is a simple tool that does the job very well....

Synaptic is still going to be on my list of things to install and I am fine with this.... I use the software center a lot anyhow simply because of simplicity of searching and listing only the main packages by default (you can still see the dependencies by clicking sow technical items).

Simple fact is 700mb isn't a lot of space, they need to cut bloat where they can.

Another item I would look at cutting if I were in their shoes is eye of gnome, Shotwell does a great job as an image previewer as well. Better IMO that eog! try it, right click a picture and open with shotwell it has all the simplicity of eog for image viewing!

---

### Post by FreeTheBee on 2011-06-24
It seems canonical really wants to refresh the Ubuntu userbase. 

When I started using Ubuntu a few years ago, synaptic was one of the key features I really appreciated. The software center looks fine, but I never use it, because it is too much of a black box for me. In my view removing synaptic is another step towards dumbing down Ubuntu, which is a sad development imho.

---

### Post by Primefalcon on 2011-06-24
Canonical are going to go for mass adoption here, and for that they need the base install to be easy for complete "computer newbs".

Fact is if you don't like unity or gnome3, use XFCE or whatever, if you ant synaptic install that... Ubuntu is still Linux and is no less configurable, but the base setup needs to be intuitive and really for new users synaptic is not!

Dumbing down the base setup IMO is a good thing! People need to stop being elitist, really!

---

### Post by uRock on 2011-06-24
I have never really liked Ubuntu Software Center, but I have never had any errors with it. I do like that it removes a program and all of its dependencies, unlike Synaptic. I do prefer to use Synaptic when installing software because it lets you see what is being done, whereas USC only shows the progress bar.

As for the argument about new users not knowing that it can be installed, well chances are they never knew it existed and will never need it.

---

### Post by shobon on 2011-06-24
I can't remember the last time I used Synaptic, even before the Software Center~

People should familiarize themselves with apt-get and dpkg.

---

### Post by toupeiro on 2011-06-24
> **shobon said:**
> I can't remember the last time I used Synaptic, even before the Software Center~

People should familiarize themselves with apt-get and dpkg.

there are plenty of reasons to use synaptic, like marking some things for upgrade, removal, and install in a single action, isolating some dependencies, grabbing other dependencies, all before the actual download.  Its an administrative tool for package management via repositories.  apt is focused more purely on install/uninstall and cache management _when you already know exactly what you are looking for_ and dpkg is just a debian package handler.  synaptic has a purpose and a value to many, even if you yourself are exempt from it.

to be honest, I actually like the software center in the form its matured into today and get positive feedback from users about it as well, I am just not sure it can do everything synaptic can.

---

### Post by beew on 2011-06-24
> **Primefalcon said:**
> 

Simple fact is 700mb isn't a lot of space, they need to cut bloat where they can.


They could cut the SC. :) I think they are pushing it simply because it is a Canonical creation.

---

### Post by beew on 2011-06-24
> **cgroza said:**
> The new users will be more happy with the software centre. They will be able to navigate through apps more easily, and I do not think average Joe cares about synaptic anyway.

Well not my experience, I have introduced Ubuntu to some Windows users and most find Synaptic easy to use and fast. The SC is pretty but slow especially if you have to install a bunch of stuffs (Does it still prompt for password for each install?) The new users are not that dumb, you know.

---

### Post by beew on 2011-06-24
> **shobon said:**
> I can't remember the last time I used Synaptic, even before the Software Center~

People should familiarize themselves with apt-get and dpkg.

Well then why use any GUI at all?  You can do everything from a terminal. I know how to use apt-get and dpkg but they are good only if you know the exact name of what you want to install and don't make typos.  A good gui package manager has its place.

---

### Post by uRock on 2011-06-24
> **beew said:**
> They could cut the SC. :) I think they are pushing it simply because it is a Canonical creation.

They are pushing it because it works well for installing and removing applications whereas Synaptic is only good for installing applications. Also, USC doesn't clutter the window with depedancy selections when searching for software.
[ATTACH]195876[/ATTACH][ATTACH]195877[/ATTACH]

---

### Post by beew on 2011-06-24
> **Primefalcon said:**
> 

Dumbing down the base setup IMO is a good thing! People need to stop being elitist, really!

And people need to stop treating new users as idiots. I think most people who take the trouble to venture out of their comfort zone of WIndows and Mac would expect to have to learn something new and Synaptic is hardly a super difficult power tool (in more "elitist" circles it is considered a tool for dummies, see **shobon'**s post above) Please don't patronize new users like that. I was a new user about a year ago (see my join date) and I would have been offended by such attitude.

---

### Post by beew on 2011-06-24
> **uRock said:**
> They are pushing it because it works well for installing and removing applications whereas Synaptic is only good for installing applications. Also, USC doesn't clutter the window with depedancy selections when searching for software.
[ATTACH]195876[/ATTACH][ATTACH]195877[/ATTACH]

Synaptic is good for both, there is an autoremovable category in synaptic for things that are installed as dependencies and is no longer needed.

---

### Post by Primefalcon on 2011-06-24
Simple fact most users don't care about any of this crap, they only care about getting stuff done and want to learn as little as possible... And the software center is easier to use

It's already been stated that the software center will eventually replace the gdeb (already done), add/remove (already done) synaptic (being done now), and the update manager (has yet to be done).... so there's bloat removal (one program replacing many)

And one single easy interface that doesn't force the user to have to wonder wtf glibsync0.13.whatever is, is a good thing....

---

### Post by FreeTheBee on 2011-06-24
I don't think the "you can install something else if you don't like it" attitude is any less elitist than disliking the current process off dumbing things down. To me the recent decisions imply that the current users are of less importance than the possible new users out there. And with that Ubuntu is drifting away from the OS I enjoyed using for the past years. 

Also, I wonder if it actually works. I doubt very much I would have stuck with linux had I been confronted with unity and had I not seen the advantage of a package manager like synaptic. I was already used to using MikTeX in windows to handle my LaTeX packages. The idea of handling all my installed software in such a away was one of the major features that got me hooked. Nowadays I use apt much more, so in my experience synaptic was the newbie friendly tool.

---

### Post by Primefalcon on 2011-06-24
> **FreeTheBee said:**
> so in my experience synaptic was the newbie friendly tool.
Your also frankly more advanced than the typical computer user

---

### Post by uRock on 2011-06-24
> **beew said:**
> Synaptic is good for both, there is an autoremovable category in synaptic for things that are installed as dependencies and is no longer needed.

This isn't done automatically. I recently installed a bunch of burner programs and went to synaptic to remove them and it did not offer to uninstall the dependencies. This negates the argument of having Synaptic for new users since they would have to search for the function you are referring to.

In the screenshot I have marked Audacity for Complete Removal. I see no options anywhere to tell it to remover the dependency. Do we expect the new user to open a terminal and run the autoremove command in hopes to remove the dependencies or wouldn't it just be easier to remove Audacity via the USC and let it remove the dependencies?
[ATTACH]195878[/ATTACH]

---

### Post by el_koraco on 2011-06-24
> **beew said:**
> Well then why use any GUI at all?  You can do everything from a terminal. I know how to use apt-get and dpkg but they are good only if you know the exact name of what you want to install and don't make typos.  A good gui package manager has its place.

Without going into the post you referred to, I don't think it is necessarily elitist to point users to managing packages via CLI, at least in Ubuntu. I've had problems resulting from the use of USC and Update Manager, even Gdebi, which never occured with apt-get. Of course, you can make the mistake of using aptitude in the terminal, which leads to the *smart* dependency resolution situations in which critical components are uninstalled if you're not paying attention...

In general, USC needs more work done to beat Synaptic in the GUI department. I think that's because it doesn't use apt directly, but aptdaemon.

---

### Post by uRock on 2011-06-24
> **beew said:**
> And people need to stop treating new users as idiots. I think most people who take the trouble to venture out of their comfort zone of WIndows and Mac would expect to have to learn something new and Synaptic is hardly a super difficult power tool (in more "elitist" circles it is considered a tool for dummies, see **shobon'**s post above) Please don't patronize new users like that. I was a new user about a year ago (see my join date) and I would have been offended by such attitude.

This article may be of interest for you. [http://www.pcworld.com/businesscenter/article/229187/30_days_with_ubuntu_linux_day_1.html](http://www.pcworld.com/businesscenter/article/229187/30_days_with_ubuntu_linux_day_1.html) After all, Ubuntu is being installed on machines and not everyone buying them will be looking to learn more about how the tool works. 

Are people who buy their first electric screwdriver expected to take it apart and know how it works just to change the driver bit or should the chuck key just work?

---

### Post by beew on 2011-06-24
> **uRock said:**
> This isn't done automatically. I recently installed a bunch of burner programs and went to synaptic to remove them and it did not offer to uninstall the dependencies. This negates the argument of having Synaptic for new users since they would have to search for the function you are referring to.

In the screenshot I have marked Audacity for Complete Removal. I see no options anywhere to tell it to remover the dependency. Do we expect the new user to open a terminal and run the autoremove command in hopes to remove the dependencies or wouldn't it just be easier to remove Audacity via the USC and let it remove the dependencies?
[ATTACH]195878[/ATTACH]

In Synaptic there is a category of autoremovable (if such files are present) I cannot give you a screenshot now because my system is clean and the category doesn't show up.

If the new users are as dumb as you think they wouldn't care about removing unneeded dependencies, they don't take up must space anyway as Linux is so small comparing to Windows standard. A  lot of Windows users have tons of clutters in their boxes, the 'average Windows user" doesn't even know about CCleaner. Always going for the lowest common denominator is not a good strategy.

---

### Post by Primefalcon on 2011-06-24
Not to mention people will remember gui for if the problems happens again... also if they forget small details such, the gui has menus ad limited enough options that the user could fumble his way through it.

With the CLI, it's not just harder to remember but if the user forgets a small detail... it'll stop him dead.... and he'll run back off to windows and tell everyone to stay away from that Linux bs! Whereas if he stayed, he me could recommend it to a lot of people..... which means larger user base, and more uptake to people who might not have tried it.....

---

### Post by beew on 2011-06-24
> **uRock said:**
> 

Are people who buy their first electric screwdriver expected to take it apart and know how it works just to change the driver bit or should the chuck key just work?

If that is the attitude why bother with Linux?? 

It is probably safe to say that > 90% of computer users (and 100% of the lowest denominator users you have in mind) have not heard of Linux, let alone Ubuntu. And since most computers don't come with Ubuntu preinstalled the new user would have to find out about Ubuntu, download the iso and burn a CD or make a live usb and then partition and install, that is quite a lot of work for the lowest denominator users you have in mind so it is not going to happen. (This can happen if some advanced users set things up for them but the advanced users are being dismissed lately)

Believe it or not Linux appeals to a different demographic than the "below average users" whom you guys want to appeal to. They would just get a Mac if they want to be babysat all the time (or Windows if they can't afford that but there is still a more technical supports than Linux because chances are many people you know would use it)

---

### Post by uRock on 2011-06-24
I don't see the point in expecting new users to notice the option you are talking about. I have seen it under the status of Installed(Autoremovable), but I have never used the option. I think it is way easier to use USC for non-power users.

---

### Post by FreeTheBee on 2011-06-24
> **Primefalcon said:**
> Your also frankly more advanced than the typical computer user

Yes, I was not a complete computer noob, but still a newbie to linux. My point is mainly that I fear Ubuntu is going towards simplistic and not simple and intuitive. I think having the software center next to synaptic is fine, but I don't see the point of removing the latter.

> **Primefalcon said:**
> Simple fact most users don't care about any of this crap, they only care about getting stuff done and want to learn as little as possible...

With the risk of sounding elitist ;-) Are these really the users you want to target. I mean this from a practical point of view, not in a demeaning way. Why would someone who just wants things to work, switch to linux? This person will most likely buy a complete system, which will come with a windows license anyway. And in general things do just work in windows. All the familiar software can be installed as well. So, there is little reason to look for alternatives. Especially when it turns out that ms office is not in the software center nor are several other common tools.

I think people with some interest in computers are much more likely to be curious about this beast called linux. I would say make the initial steps easy, but don't try to hide all the underlying things. When I started using Ubuntu I was very happy when everything just worked out of the box and that I could start using it immediately. It was also quite clear that there were loads of options that I could look into, if I ever felt like it. I considered this a good thing, not a complication.

---

### Post by beew on 2011-06-24
> **FreeTheBee said:**
> Yes, I was not a complete computer noob, but still a newbie to linux. My point is mainly that I fear Ubuntu is going towards simplistic and not simple and intuitive. I think having the software center next to synaptic is fine, but I don't see the point of removing the latter.



With the risk of sounding elitist ;-) Are these really the users you want to target. I mean this from a practical point of view, not in a demeaning way. Why would someone who just wants things to work, switch to linux? This person will most likely buy a complete system, which will come with a windows license anyway. And in general things do just work in windows. All the familiar software can be installed as well. So, there is little reason to look for alternatives. Especially when it turns out that ms office is not in the software center nor are several other common tools.

I think people with some interest in computers are much more likely to be curious about this beast called linux. I would say make the initial steps easy, but don't try to hide all the underlying things. When I started using Ubuntu I was very happy when everything just worked out of the box and that I could start using it immediately. It was also quite clear that there were loads of options that I could look into, if I ever felt like it. I considered this a good thing, not a complication.

Exactly how I feel, but you put it better!

---

### Post by BrokenKingpin on 2011-06-24
I think this is the way it should be going. Synaptic is good, but probably not the best for new users. The Ubuntu Software Center is really nice and easy to use, but just a little slow.

I also hope the Software Center eventually replaces the update manager as well. I do not see the need for three applications just to handle package management, so I am glad to see them trying to cover it off with one application.

---

### Post by Primefalcon on 2011-06-24
Fact is, this I the way Ubuntu is going, and I do support them in this!

This needs to happen if Linux ever hopes to be anything other than a flat growth OS as Adobe calls it.... Mark Shuttleworth, Jane Silber and Canonical know this....

---

### Post by beew on 2011-06-24
> **Primefalcon said:**
> Fact is, this I the way Ubuntu is going, and I do support them in this!

This needs to happen if Linux ever hopes to be anything other than a flat growth OS as Adobe calls it.... Mark Shuttleworth, Jane Silber and Canonical know this....

This is just an assertion. There is no evidence or argument to suggest that dumbing down and copycating would increase market share. 

First of all you have to understand what is the reason behind the so called flat growth (which is debatable if you look outside North America,  China has a large market and Linux is growing there everyday) and address it properly.  You are prescribing the medicine without even making a diagnosis. 

I would think hardware and software support and lack of marketing would be a lot more important factors than Ubuntu being "too hard"(again too hard according to whom and what the target audience is) For one thing, nobody knows about Linux or Ubuntu, especially the demographic you are now trying to target and it is lost cause no matter how much you dumb down.

BTW, Taiwan actually has a state agency to test hardware for Linux compatibility and they have concrete plans and timetable to switch to open source. Initiatives like this would go much further in increasing Linux adoption than cosmetic changes and hiding advanced options from users.

---

### Post by nothingspecial on 2011-06-24
](*,)](*,)](*,)](*,)](*,)

Just tailor it to your needs.

That is the point.

It has always been the point.

We offer you this, with the option to do whatever you want too with it.

These conversations are ridiculous.

---

### Post by SunnyRabbiera on 2011-06-24
This is another stupid move in my eyes as USC STILL needs work, it still needs the ability to refresh package repositories WITHOUT use of commandline.
Ubuntu developers have all gone insane, no wonder why I want a new distribution to come in and shake things up.
Mageia is looking pretty good right about now, as is openSUSE, or the ubuntu spinoffs such as linux mint.

---

### Post by Ric_NYC on 2011-06-24
> **SunnyRabbiera said:**
> This is another stupid move in my eyes as USC STILL needs work, it still needs the ability to refresh package repositories WITHOUT use of commandline.
Ubuntu developers have all gone insane, no wonder why I want a new distribution to come in and shake things up.
**Mangeia* is looking pretty good right about now**, as is openSUSE, or the ubuntu spinoffs such as linux mint.



Thanks for the info!

---

### Post by kleovoulinos on 2011-06-24
> **LowSky said:**
> I hate the Software center... its slow, and it hangs every time I try to use it. Plus trying to install a DEB used to be easy, you clicked on it and Gdebi handled the work, now it loads the software center and asks me dumb questions about trusting the source.

Synaptic is fast and pretty user friendly if you ask me.

I'm tired of buggy software being used in Ubuntu.

I am sure you're right about the Software Center, it's slow-paced and the .deb packages have truly become a huge pain! I tried installing an application and it actually did not work! It'ts true that there will not be a Synaptic Package Manager in 11.10, as the new patch of Ubuntu Software Center 5 will upgrade the USC heavily. Hopefully it will include both in a huge speed of course! :KS

---

### Post by SunnyRabbiera on 2011-06-24
> **Ric_NYC said:**
> Thanks for the info!

Spelling error on my part, also its a new distribution so I am bound to mess up the name.

Anyway another reason why this rings bad decision is dependency resolvent, something software center still REALLY lacks in

---

### Post by Dustin2128 on 2011-06-24
> **Linuxratty said:**
> But for how long!?  First they take away my old,reliable Gnome and replace it with an over sized cell phone interface,now they take away my Synaptic!
What bloody next!? Yeah,I know it's easy as falling off a log to get it back,but that's not the point.What worries me is they will kill it.
Canonical puts out a great product, but IMO the future of newbie-friendly distros is linux mint. Very, very easy to get a former windows user setup. If you dislike the direction ubuntu is going though, just do what I did and do a distro hop. Debian, mint, arch, they're all options, the first being somewhat newbie friendly and the second being very. Arch is basically like gentoo without compiling- build it from the ground up but it doesn't take 3 weeks to compile all your packages.

---

### Post by nothingspecial on 2011-06-24
@@@@@ insert jumping up and down, angry smiley @@@@@

everybody, stop being silly.

This was/is/always_will_be a distro that caters for people who haven't tried it yet.

That is the whole point.

That is bug no 1

That is what MS (Shuttleworth not microsoft) is trying to do. That is what he has always been trying to do.

The whole idea is to spread the word of free software, which, as we are all here, he seems to be doing well.

We are **_[SIZE="3"]NOT[/SIZE]_** being forced into anything. We never have been.

Ubuntu is a project that is trying to show the ordinary computer user that there is an alternative. Ubuntu, as it develops, will always try to make it as easy as possible for someone who knows nothing of the internal workings of an operating system etc to use it ------- why do you not see that? 

At the same time, it will always be configurable so YOU can use it as you wish.

Whatever is on the cd does not matter.

For goodness sake ](*,)

---

### Post by wolfen69 on 2011-06-24
> **FreeTheBee said:**
> 

With the risk of sounding elitist ;-) Are these really the users you want to target.

In a nutshell, yes. 

I really don't know why people get their panties in a bunch over this stuff. Their is so much choice and possibilities in linux and ubuntu, it makes my head spin. 

Everybody has their own opinion of what should be default, and what should be developed. At the end of the day it's Shuttleworth's business, and he can do as he pleases. The man devotes his life to producing an operating system using *his own money* and give it to everyone for *free*. Sheesh! I feel we all owe him a debt of gratitude. He has single handedly moved linux forward by leaps and bounds that otherwise would not have happened at the rate it did. 

If I don't like disro(X), I simply find one that suits me. No need for backstabbing and whining. Let's all wake up and concentrate on the important things like bug reporting, writing code, and contributing in some way. Posting in recurring discussions and arguing accomplishes little to nothing. Probably closer to nothing. 

Every time ubuntu changes something that can be easily overcome, people flip out. I just don't don't get it. :confused: Are these things life changing or something? Am I missing out by not being upset over this?
> **nothingspecial said:**
> 

everybody, stop being silly.

Whatever is on the cd does not matter.

For goodness sake ](*,)
Well said.



The only way to affect change is to get directly involved. Bottom line. Now let's all play nice and have a group hug.
[IMG]http://static.tvtropes.org/pmwiki/pub/images/GroupHug.jpg[/IMG]

---

### Post by wolfen69 on 2011-06-24
> **nothingspecial said:**
> 
This was/is/always_will_be a distro that caters for people who haven't tried it yet.


*And* a point should be made that it is also for the hard core user too. Just download the 12mb net-install and build it up from scratch. That's pretty advanced if you ask me. Ubuntu can work for *all* levels of users. That's the beauty of it. ;)

---

### Post by Primefalcon on 2011-06-24
> **wolfen69 said:**
> In a nutshell, yes. 

I really don't know why people get their panties in a bunch over this stuff. Their is so much choice and possibilities in linux and ubuntu, it makes my head spin. 

Everybody has their own opinion of what should be default, and what should be developed. At the end of the day it's Shuttleworth's business, and he can do as he pleases. The man devotes his life to producing an operating system using *his own money* and give it to everyone for *free*. Sheesh! I feel we all owe him a debt of gratitude. He has single handedly moved linux forward by leaps and bounds that otherwise would not have happened at the rate it did. 

If I don't like disro(X), I simply find one that suits me. No need for backstabbing and whining. Let's all wake up and concentrate on the important things like bug reporting, writing code, and contributing in some way. Posting in recurring discussions and arguing accomplishes little to nothing. Probably closer to nothing. 

Every time ubuntu changes something that can be easily overcome, people flip out. I just don't don't get it. :confused: Are these things life changing or something? Am I missing out by not being upset over this?

Well said.



The only way to affect change is to get directly involved. Bottom line. Now let's all play nice and have a group hug.
[IMG]http://static.tvtropes.org/pmwiki/pub/images/GroupHug.jpg[/IMG]
Wow! Perfectly Said!

---

### Post by Paqman on 2011-06-25
> **beew said:**
> 
I would think hardware and software support and lack of marketing would be a lot more important factors than Ubuntu being "too hard"(again too hard according to whom and what the target audience is) For one thing, nobody knows about Linux or Ubuntu, especially the demographic you are now trying to target and it is lost cause no matter how much you dumb down.


Indeed, but Linux has a chicken and egg problem. We can't get good support and marketing from the OEMs until we demonstrate we've got a product that appeals to a wide market, and we can't get that product to a wide market to develop it into one that does without the support of the OEMs.

You may disagree with some details of Canonical's vision, but their overarching goal is get the Dells, Toshibas and HPs of the world to take a real punt on Ubuntu and ship it in quantity with a proper marketing push. 

Continuing to produce a product which appeals solely to Linux's traditional geek user base will change nothing, and we'll be stuck at 1% forever. Some people are fine with that idea, of course. There will always be distros that cater to those folks. I think Ubuntu does a decent job of still doing so, but that may not always be the case.

---

### Post by Bandit on 2011-06-25
Software Centre has come along way. Its very user friendly and a nice feature I enjoy is being to able to browse more packaged while others install. Synaptic cant do that and is not newb friendly.

That said, SC is still little to buggy as of 11.04. I dont see it being fully rock stable by 11.10. But I guess the Devs hope to get in a few more bug reports by removing Syn from the base install. But what ever they can do TO get SC rockstable by 12.04LTS should be done.

---

### Post by donkyhotay on 2011-06-25
I generally use synaptic over the software center. I understand the reason they are getting rid of synaptic by default and personally don't have a problem with it so long as it remains in the repos. Now if they were to remove it from the repos for some reason...

---

### Post by Bart_D on 2011-06-25
The most user-friendly Linux distro is PinGuy OS.....NOT Linux Mint.

> **toupeiro said:**
> Is this a really bad and horribly belated April fools joke? (emphasis on joke)

[http://techie-buzz.com/foss/synaptics-removed-ubuntu-11-10.html](http://techie-buzz.com/foss/synaptics-removed-ubuntu-11-10.html)

GOOD Riddance!

From the point of view of a New/Average user, I see ZERO need for Synaptic.

Go Software Center! I'm sure that the Software Center will be improved to the point where it becomes a FULL replacement for Synaptic, even for Advanced/Power Users.

---

### Post by ZarathustraDK on 2011-06-25
Ubuntu is supposed to be THE noob-friendly distro out there, so from that point of view scrapping Synaptic for Software Center makes sense.

That's not to rip on Synaptic though, it's a nice frontend with more granular access to packages, it's just confusing to new users or even detrimental to them. I'd say dicking around in Synaptic without knowing what you're doing as a new user has the potential to cause more grief/breakage than doing it in Software Center.

As a poweruser you can just apt-get install synaptic if you need it, and if you don't know how, then you're not a poweruser ;) . I possess enough self-reflection to know that if I wanted a power-user centered out-of-the-box-experience, then I'd probably not go with Ubuntu.

Actually, "poweruser-centered out-of-the-box-experience" is not a far cry from being an oxymoron IMHO.

---

### Post by Linuxratty on 2011-06-25
> **el_koraco said:**
> Synaptic is a Debian tool. Even if by some miracle the nasty people at Canonical removed it from Ubuntu, you could still use the package from Debian.

 And that is indeed my master plan. Mwhahahahaha!

---

### Post by cgroza on 2011-06-25
I remember that 2 years ago, just installed Ubuntu for the first time, I went to Synaptic to install something, and somehow I lost my XServer. I was stuck at the command line.

---

### Post by beew on 2011-06-25
> **ZarathustraDK said:**
> Ubuntu is supposed to be THE noob-friendly distro out there, so from that point of view scrapping Synaptic for Software Center makes sense.

That's not to rip on Synaptic though, it's a nice frontend with more granular access to packages, it's just confusing to new users or even detrimental to them. I'd say dicking around in Synaptic without knowing what you're doing as a new user has the potential to cause more grief/breakage than doing it in Software Center.

As a poweruser you can just apt-get install synaptic if you need it, and if you don't know how, then you're not a poweruser ;) . I possess enough self-reflection to know that if I wanted a power-user centered out-of-the-box-experience, then I'd probably not go with Ubuntu.

Actually, "poweruser-centered out-of-the-box-experience" is not a far cry from being an oxymoron IMHO.

I was using Synaptic since I started using Ubuntu, I have no idea why some of you think it is soooo advanced. It is very noob friendly and it is actually called an idiot tool in some other distros. Look, if you expect the new user to be able to download an iso, burn it to a CD or make a live iso and then install Ubuntu, probably doing some partitioning with gparted, then I can't see how Synaptic would be confusing and hard.

I think it has nothing to do with the alleged difficulty of Synaptic, they push the SC because it is a Canonical creation and they want to push a one size fit all solution and that would be it. How hard is it to use gdebi? I would have never known about it if it was removed when I was new.

---

### Post by Paqman on 2011-06-25
> **beew said:**
> 
they push the SC because it is a Canonical creation and they want to push a one size fit all solution and that would be it.

Of course. That's why they built it. It's supposed to replace Add/Remove, Synaptic, Update Manager and Gdebi. Three down, one to go.

I think you'll find with Synaptic dropping off the default list, that it's done so because Software Centre now has most/all of it's features. That's always been the plan anyway.

---

### Post by Ric_NYC on 2011-06-25
[B]Synaptic Software Center Comparison
[/B]


[https://wiki.ubuntu.com/SoftwareCenter/SynapticSoftwareCenterComparison](https://wiki.ubuntu.com/SoftwareCenter/SynapticSoftwareCenterComparison)

---

### Post by Gremlinzzz on 2011-06-25
Don't need it,
Bottom line is there s three ways to install programs.
if one has to go the pick should be and will be Synaptic.
like I told Bob Dylan (The Times They Are A Changing:D

---

### Post by pratikk on 2011-06-25
> **wolfen69 said:**
> The devs are trying to shave MB's wherever possible to keep the image under 700mb. I don't blame them. Casual users will be satisfied with the software center, and more advanced users will apt-get synaptic. In ubuntu's case, it's no big deal.

If Canonical makes a DVD the norm, they will lose some users who don't have dvd burners, or have limited bandwidth.

I would welcome a move to DVDs, since almost everyone has a burner now and the huge update after a CD install is as much a deterrent as the Windows update. Also, I would like to build an image of my main machine with everything I need installed and configured which I can copy to other machines (I use several), and that's not possible in CD sizes. 

And as a casual user, I don't like the software centre because it's opaque. It doesn't show me what else is being (un)installed, apart from the selected package. Oh. Maybe I'm not entirely a casual user.

---

### Post by beew on 2011-06-25
> **pratikk said:**
> I would welcome a move to DVDs, since almost everyone has a burner now and the huge update after a CD install is as much a deterrent as the Windows update. Also, I would like to build an image of my main machine with everything I need installed and configured which I can copy to other machines (I use several), and that's not possible in CD sizes. 

And as a casual user, I don't like the software centre because it's opaque. It doesn't show me what else is being (un)installed, apart from the selected package. Oh. Maybe I'm not entirely a casual user.

No, I think DVD is a bad idea, take longer to download, longer to install and probably you wouldn't want a lot of stuffs in it anyway. I don't like the fact that they take out things such as Synaptic and gdebi, I would think that a better way to trim down the iso would be to take out SC, which is slow, bloated, lacks functions and plainly annoying.

But I would rather having to install Synaptic myself than to have to install a dvd and end up removing/replacing most things in there.

---

### Post by capink on 2011-06-25
> **beew said:**
> Look, if you expect the new user to be able to download an iso, burn it to a CD or make a live iso and then install Ubuntu, probably doing some partitioning with gparted, then I can't see how Synaptic would be confusing and hard.


I don't think that is the kind of user ubuntu is targeting. They are trying to make the distro more accessible for people who are buying it preinstalled. They already have deals with dell and asus. And I'm sure they are looking for other OEMs as well.

---

### Post by SunnyRabbiera on 2011-06-25
> **Ric_NYC said:**
> [B]Synaptic Software Center Comparison
[/B]


[https://wiki.ubuntu.com/SoftwareCenter/SynapticSoftwareCenterComparison](https://wiki.ubuntu.com/SoftwareCenter/SynapticSoftwareCenterComparison)

This points out one of the reasons to keep synaptic:
broken packages

A LOT of users here are current Windows users thus would be used to the windows way of things, like installing programs from web pages as opposed to repositories.
This can cause severe dependency issues.

Also another mission critical bug is that software center does not support refreshing repositories, this is bad for beginners as well

---

### Post by Paqman on 2011-06-25
> **pratikk said:**
> I would welcome a move to DVDs

There's already a [DVD image]("http://www.ubuntu.com/download/ubuntu/alternative-download#dvd"). There's also talk of creating a 1.5GB image that would be good for putting on a 2GB USB stick. Some of the packages dropped from the CD image like GIMP and Synaptic would presumably be good candidates for the 1.5GB one.

---

### Post by beew on 2011-06-25
> **capink said:**
> I don't think that is the kind of user ubuntu is targeting. They are trying to make the distro more accessible for people who are buying it preinstalled. They already have deals with dell and asus. And I'm sure they are looking for other OEMs as well.

Two points.

1. There are not that many OEM manufacturers for Ubuntu so most Ubuntu users would be the kind who download and install it himself/herself or with a friend's help.

2. The OEMS use customized isos which are not supported by Canonical (or only partially). So if you have an asus netbook it will be running 10.10 even after eol, presumably Asus would be supporting it. Theoretically if you  install a copy  "normal' Ubuntu on these OEM machines it may not even run,--there is no guarantee that it will. So you are talking about something entirely different here. 

I heard that Dell's even switched off the software centre in its Ubuntu netbooks(Ubuntu 8.04) a few years ago so users wouldn't be able to install and update through normal routes, if I am wrong I stand corrected but I wouldn't be surprised.

---

### Post by uRock on 2011-06-25
> **beew said:**
> Two points.

1. There are not that many OEM manufacturers for Ubuntu so most Ubuntu users would be the kind who download and install it himself/herself or with a friend's help.

2. The OEMS use a customized isos which are not supported by Canonical (or only partially). So if you have an asus netbook it will be running 10.10 even after eol, presumably Asus would be supporting it. Theoretically if you  install a copy  "normal' Ubuntu on these OEM machines it may not even run,--there is no guarantee that it will. So you are talking about something entirely different here. 

I heard that Dell's even switched off the software centre in its Ubuntu netbooks(Ubuntu 8.04) a few years ago so users wouldn't be able to install and update through normal routes, if I am wrong I stand corrected but I wouldn't be surprised.
Got references?

---

### Post by beew on 2011-06-25
> **uRock said:**
> Got references?

Reference for what? 

That most Ubuntu users install it himself?

That OEMs use customized isos and machines that work with these customized installs are not guranteed to work with normal install?  (see Ubuntu's hardware compatibility page)

That Asus is shipping with 10.10?

All are well known.

---

### Post by bruno9779 on 2011-06-25
I am all for a full release on DVD or 1.5 GB as suggested above, and a reduced CD one.

The average first time user is bound to catch the difference quickly coming from Windows (Basic, home, pro, ultimate etc). Making it clear that an upgrade is free would sort things out.

---

### Post by uRock on 2011-06-25
> **beew said:**
> Reference for what? 

That most Ubuntu users install it himself?

That OEMs use customized isos and machines that work with these customized installs are not guranteed to work with normal install?  (see Ubuntu's hardware compatibility page)

That Asus is shipping with 10.10?

All are well known.

Reference for your statements that Custom versions of ubuntu used by Asus are not supported in part or whole by ubuntu and that Dell versions of Ubuntu have USC removed.

Well known to you doesn't make it the statements factual.

---

### Post by beew on 2011-06-25
> **uRock said:**
> Reference for your statements that Custom versions of ubuntu used by Asus are not supported in part or whole by ubuntu and that Dell versions of Ubuntu have USC removed.

Well known to you doesn't make it the statements factual.

[http://bits.quintanasegui.com/2008/12/30/dell-sells-ubuntu-boxes-that-cannot-run-ubuntu/](http://bits.quintanasegui.com/2008/12/30/dell-sells-ubuntu-boxes-that-cannot-run-ubuntu/)

---

### Post by uRock on 2011-06-25
> **beew said:**
> [http://bits.quintanasegui.com/2008/12/30/dell-sells-ubuntu-boxes-that-cannot-run-ubuntu/](http://bits.quintanasegui.com/2008/12/30/dell-sells-ubuntu-boxes-that-cannot-run-ubuntu/)

Yeah, we know Dell blocked update manager from upgrading. That still doesn't cover your claims about Asus or USC being removed, which IIRC 8.04 didn't offer USC anyway. 

Being Dell supported a warranty, added codecs for media playback and made custom alterations to drivers, I can see why they would block upgrades.

---

### Post by capink on 2011-06-25
Even if dell blocked. The point here is not about the OEMs canonical already has. It is about trying to make ubuntu more attractive for the OEMs they are yet to have deals with. Because in the long run, this can bring more users than those who download the ISO and install it themselves.

---

### Post by uRock on 2011-06-25
> **capink said:**
> Even if dell blocked. The point here is not about the OEMs canonical already has. It is about trying to make ubuntu more attractive for the OEMs they are yet to have deals with. Because in the long run, this can bring more users than those who download the ISO and install it themselves.

Agreed. Ubuntu Software Center makes it easier to install/remove applications, without worrying about dependencies.

---

### Post by PRC09 on 2011-06-25
> Even if dell blocked. The point here is not about the OEMs canonical already has. It is about trying to make ubuntu more attractive for the OEMs they are yet to have deals with. Because in the long run, this can bring more users than those who download the ISO and install it themselves.


I guess we can exclude HP from the list as it is going with its own...


[http://macdailynews.com/2011/03/09/hp-ceo-apotheker-all-hp-pcs-will-dual-boot-windows-and-webos-starting-in-2012/](http://macdailynews.com/2011/03/09/hp-ceo-apotheker-all-hp-pcs-will-dual-boot-windows-and-webos-starting-in-2012/)

---

### Post by tumbes2000 on 2011-06-25
> **Grenage said:**
> A new user types "Libre Office" in Software Centre, and they are presented with a few simple choices.

A new user types "Libre Office" into Synaptic, and they are presented with an immense list of irrelevant packages - plus the one or two they really need.
Software centre is absolutely the right direction to take, and you'd have to be completely myopic to think otherwise.  I use apt from a terminal, but that doesn't mean most users will want to.

I completely agree

---

### Post by Bart_D on 2011-06-25
> **Grenage said:**
> A new user types "Libre Office" in Software Centre, and they are presented with a few simple choices.

A new user types "Libre Office" into Synaptic, and **_they are presented with an immense list of irrelevant packages_ - plus the one or two they really need.**

Software centre is absolutely the right direction to take, and you'd have to be completely myopic to think otherwise.  I use apt from a terminal, but that doesn't mean most users will want to.

**EXACTLY! ****I'm not a psycho!**

Well said, good sir, well said!

---

### Post by beew on 2011-06-26
> **uRock said:**
> Agreed. Ubuntu Software Center makes it easier to install/remove applications, without worrying about dependencies.

How do you have to "worry about dependencies" in Synaptic? You choose the package, click apply and that's it. Synaptic  shows you the dependencies but you can ignore them and just click apply like you would with the SC,--some times at your own peril, but you don't have to "worry" any more than you do in the SC, except when conflicts do happen you get no info from SC, so you don't even know what hits you.

---

### Post by uRock on 2011-06-26
> **beew said:**
> How do you have to "worry about dependencies" in Synaptic? You choose the package, click apply and that's it. Synaptic  shows you the dependencies but you can ignore them and just click apply like you would with the SC,--some times at your own peril, but you don't have to "worry" any more than you do in the SC, except when conflicts do happen you get no info from SC, so you don't even know what hits you.
I already showed you that removing a package in Synaptic only removes the one package and not the dependencies. It leaves them sitting there taking up valuable root partition space and depending on which package it is, it will still have an effect on the system. As for install errors, I have yet to have USC run into any problems installing software.

What about searching for software? You search for an app in USC and you find the app. You search for an app in Synaptic and the actual app may be buried 20 packages below somewhere in the list. How is that helpful to new users who have no idea what they are looking at?

---

### Post by FlameReaper on 2011-06-26
For new users, Synaptic is an overload of information, and most of them won't like that.

It's like telling someone "To install this software on Windows you need this DLL and that DLL"... which they don't want to be bothered with, they just want the program to install already, knowledge about what and which dependencies be damned.

If this is done by someone who knows about how programs and dependencies work but just decides to not care we might have some sense into telling them off about it. But for new users? Hmm.

As long as Synaptic is still available in the repositories, I'm cool.

---

### Post by beew on 2011-06-26
> **uRock said:**
> I already showed you that removing a package in Synaptic only removes the one package and not the dependencies. It leaves them sitting there taking up valuable root partition space and depending on which package it is, it will still have an effect on the system. As for install errors, I have yet to have USC run into any problems installing software.

I have already answered that. 

1) Synaptic has the option to autoremove 

2) the kind of below average new users that you seem to think Ubuntu should cater to couldn't care less about unremoved dependencies, it is not like they take up lots of space anyway. If they are as computer illiterate that you make them out to be they wouldn't even know what dependencies are.

If someone knows enough to be bothered by unremoved obsolete dependency packages  he/she would not find Synaptic difficult to use.

> What about searching for software? You search for an app in USC and you find the app. You search for an app in Synaptic and the actual app may be buried 20 packages below somewhere in the list. How is that helpful to new users who have no idea what they are looking at?I am not sure what you are talking about. I have never had a problem searching for apps, either by functional category, status or by origin. There are explanations for what the packages are (well some explanations anyway) so it has cover the minimal search ability of the SC and more.

---

### Post by beew on 2011-06-26
> **uRock said:**
> Yeah, we know Dell blocked update manager from upgrading. That still doesn't cover your claims about Asus or USC being removed, which IIRC 8.04 didn't offer USC anyway. 

Being Dell supported a warranty, added codecs for media playback and made custom alterations to drivers, I can see why they would block upgrades.

True that they didn't close down the SC but I have said I didn't remember the details. 

My main points, however still stand, that OEM Ubuntu install (for Dell at least, and there are only a few examples to go by ) is non standard Ubuntu with its own choice of apps (Asus seems to be the same) and the standard iso may not even install on such a machine and it has its own repository and update route (not the standard one).  So I am not seeing what OEM users have to do with changes made in the standard iso, as they probably don't use it anyway.

---

### Post by Paqman on 2011-06-26
> **beew said:**
> How do you have to "worry about dependencies" in Synaptic? You choose the package, click apply and that's it. 

How do you know which package is the core one, which is a dependent lib, and which is an optional extra?

I'm not a new user, but quite often when installing something in Synaptic I have to do a bit of digging into the dependencies to find out which is the main package I have to install. I'm sure you find the same. Quite often it's not at all straightforward to figure out which package you actually want from the heap of cryptically named nonsense presented to you.

Sometimes having all the associated packages exposed to you *is* useful, tbh it's often this exact feature that leads me to use Synaptic instead of another tool. But most of the time it's just unnecessary noise and complexity, and for someone not familiar with Linux package and dependency systems it's going to be confusing.

Synaptic is a good tool, but it does have significant weaknesses.

---

### Post by Lucradia on 2011-06-26
You can't "fully" get rid of something without getting rid of the base. In the case of synaptics, you have to get rid of apt-get. Thus disallowing the use of apt-add-repository, and those fancy "ppa/whatever" things.

---

### Post by uRock on 2011-06-26
> **beew said:**
> 2) the kind of below average new users that you seem to think Ubuntu should cater to couldn't care less about unremoved dependencies, it is not like they take up lots of space anyway. If they are as computer illiterate that you make them out to be they wouldn't even know what dependencies are.

There are GUI applications where you uninstall the main package via Synaptic, but other parts are left behind and still functioning. Like UNE, I installed the UNE package on my netbook, then after removing it, the netbook menu was still there and working after a restart. Autoremove still doesn't detect this as an autoremovable dependency on my netbook.

---

