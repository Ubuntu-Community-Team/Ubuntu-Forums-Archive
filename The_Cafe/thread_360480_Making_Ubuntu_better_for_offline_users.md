---
title: "Making Ubuntu better for offline users"
date: 2007-02-13
forum: The Cafe
---

### Post by v8YKxgHe on 2007-02-13
Hey,

Ubuntu, if you don't have an internet connection, can be a right pain. For example, my friend brought his laptop into college and installed Ubuntu on it with my help, I then told him about Beryl and he instantly wanted to try it. His first 'reaction' was to go to the Beryl website, download a file, copy it to his memory stick then to the laptop, double click on it and install it. However, we all know this isn't the case.

I said to him, for it to work you'll need to install the ATI fglrx drivers and XGL ... could be fun with no internet connection. I went onto the Ubuntu Packages website and downloaded the xorg-driver-fglrx but of course it depends on other things and quite simply didn't work, neither did XGL because I would have had to manually download _all_ these extra dependency files.

What I think would be a great way to fix this is to add a feature to the [Ubuntu Package]("http://packages.ubuntu.com/") website that will automatically archive all needed dependencies for a package, then offer this as a download to the user - instead of manually having to download every dependency. 

So, if I wanted to download Frozen Bubble for my friend I would search for "Frozen Bubble" it checks the dependencies of what the package needs, then it make an archive on-the-fly which contains frozen-bubble, frozen-bubble-data and any other files it depends on. I can then put this on CD or memory stick and give it to my friend, he then just double clicks on a metapackage .deb file which will also install the extra dependencies ... if that makes sense?

What do people think?

Regards

---

### Post by FrostDust on 2007-02-13
The problem with this, though, is that it would waste a lot of bandwidth downloading dependencies that your friend may, and probably, already has. But, as you said, for offline users there should be an easier way to install stuff.

---

### Post by v8YKxgHe on 2007-02-13
True, there would be no way of knowing what packages he already has installed, so it could be downloading extra dependencies he doesn't need, but it would still make it far easier to install packages for offline users.

---

### Post by justin whitaker on 2007-02-13
How about an ISO that has updates? You could package up a bunch of stuff in an Automatix type menu...

---

### Post by anaconda on 2007-02-13
how about the klik -system?

It is easy and all fprograms are 1-file downloads 
[http://klik.atekon.de/](http://klik.atekon.de/)

Might want to download them to a similar (eg. ubuntu) system and to a USB-memory from there..

---

### Post by v8YKxgHe on 2007-02-13
> **anaconda said:**
> how about the klik -system?

It is easy and all fprograms are 1-file downloads 
[http://klik.atekon.de/](http://klik.atekon.de/)

Might want to download them to a similar (eg. ubuntu) system and to a USB-memory from there..

But that assumes you have another Linux distro with internet connection. The way to make Ubuntu better for offline users needs to be platform independent, so for example at College (which run WinXP) I could just pop into Ubuntu Packages, download a archive that was made on-the-fly for say Frozen Bubble, I then put the archive on memory stick, transfer to Ubuntu laptop, install, done. No need for another "middle man" program.

---

### Post by online14230 on 2007-02-16
Ive been looking for a long time for a win based program that would do exactly that: create an archive on the fly, adding all dependencies... it seems none exist. I think you have a great idea there, because I have the same problem: I have no internet connection on my ububox. THIS is why Ive started learning C++...

---

### Post by adam.tropics on 2007-02-16
I understand your problem, but packaging like that to my mind kind of goes against the way Linux is built. Packages are intentionally kept small by using shared libraries etc etc.

Also, trying to create a windows program that does this packaging is surely gonna be a tough one. There are just too many things to account for. What OS version is the package for. Is its destination a standard install. Has the user previously added to the install possibly causing yet more potential dependency problems and so on.

I am not sure of the best solution. I like the idea of each release having an optional (kept up to date) dvd available for purchase at minimum cost providing a basic repo for offline use, (I believe, though I can't remember where, there is one for Ubuntu somewhere) but even this would leave a few areas, where you would simply have to bite the bullet and get online if you wanted to try the latest and greatest.

---

### Post by FrostDust on 2007-02-18
I was thinking before, and came up with a solution to your friend's problem. Basically, when you clicked in Synaptic to install a program, it would make a list of all of the dependencies needed, including dependencies of dependencies, etc. and save this list to a flash drive, CD-RW, or whatever.

You would then bring it to a computer with internet access, and go to the Ubuntu website. After uploading the list of the programs you need, all of the required programs will be downloaded to your flash drive, which you can then bring back to the first computer, and install everything.

---

### Post by Polygon on 2007-02-18
basically what synaptic downloads and installs are just .deb files. So you should just be able to open up synaptic, find what you need and then save it to a cd / usb key (there is some option to just download the files, but not install) and then give it to your friend.

---

### Post by banjobacon on 2007-02-18
> **FrostDust said:**
> I was thinking before, and came up with a solution to your friend's problem. Basically, when you clicked in Synaptic to install a program, it would make a list of all of the dependencies needed, including dependencies of dependencies, etc. and save this list to a flash drive, CD-RW, or whatever.

You would then bring it to a computer with internet access, and go to the Ubuntu website. After uploading the list of the programs you need, all of the required programs will be downloaded to your flash drive, which you can then bring back to the first computer, and install everything.

This would also be great for keeping computers of dial-up users up to date, as updates can sometimes be very large.

Synaptic has a an option in the File menu label "Generate package download script". I've never used it, but I guess it's kind of obvious what it does. I doubt the script would work on Windows, though.

I think a web interface is a good idea, though, as it might be more convenient at times. Imagine some friend tells you about a cool program and you want to download it. Instead of going home, generating a download script and then finding a computer with internet access, you can just get the packages from the website. Downloading redundant packages shouldn't be that much of a problem, as the computer used to download the packages would probably have broadband. Users would have to specify if they're running Ubuntu, Kubuntu or whatever, and that would give the system a decent idea of what needs to be downloaded.

---

### Post by aysiu on 2007-02-18
Some of us (not so much me--I just kind of stirred better folks to action) put together an add-on CD.

It was mainly spearheaded by CompShrink and called UbuntuPlus. You can find more info on it [here](http://ubuntuforums.org/showthread.php?t=183933). There's a Dapper version and a Breezy version. Anyone really interested in offline users should contribute to this project by making an Edgy CD or hosting the ISO images.

---

### Post by v8YKxgHe on 2007-02-19
> **banjobacon said:**
> 
I think a web interface is a good idea, though, as it might be more convenient at times. Imagine some friend tells you about a cool program and you want to download it. Instead of going home, generating a download script and then finding a computer with internet access, you can just get the packages from the website. Downloading redundant packages shouldn't be that much of a problem, as the computer used to download the packages would probably have broadband. Users would have to specify if they're running Ubuntu, Kubuntu or whatever, and that would give the system a decent idea of what needs to be downloaded.

Exactly, the web interface would allow for anyone to just quickly and easily grab any file they want (with all dependencies) then install them.

> Some of us (not so much me--I just kind of stirred better folks to action) put together an add-on CD.
The trouble with a CD method is that it assumes you either:
a) Have another Ubuntu or other distro online
b) You have a blank CD and a place to burn the CD to

Basically, I think what I'm after is a web-based apt-get/Synaptic that will just let you download a file, get _all_ dependencies, bundle them up and offer it as a download. That's very simple for a user to get files from.

---

### Post by aysiu on 2007-02-19
I don't think assuming you have a blank CD and a CD burner is that much of an assumption, especially since the add-on CD contains a lot of software you'll want to install later. Even if *you* don't have a CD burner, you may have a friend or a university that does. The CD needs to be burnt only once. Individual packages would have to be downloaded and transferred many times.

It's not a terrible idea you have (the more methods, the merrier), but someone would actually have to implement that. An add-on CD is easier to maintain.

---

### Post by The Grum on 2007-02-22
Going back to the original idea, what about having a tool in Ubuntu that generates a list of what needs to be downloaded? Or maybe integrate it into add/remove and synaptic (detects the machine is offline and offers to generate a "get-me" list).

Then you move that file to a machine with a working connection and the "Ubuntu Package Getter" tool. It downloads and packages up the needed files from the list for copying back to the offline machine via usb stick or whatever.

(Not sure how the packages would get installed. Some easy way to add the new files as a temporary repository? Maybe have a specific folder to copy the files to before running apt-get again?)

A Windows version of the tool would be great for people who are dual booting, maybe even include it on the CD with the other Windows apps.

---

### Post by shining on 2007-02-22
I think the best way is to use a distribution that comes on 1 or 2 DVD, with all the softwares you need.
You can see the contents of the dvd of ubuntu edgy there:
[http://cdimage.ubuntulinux.org/releases/edgy/release/ubuntu-6.10-dvd-i386.list](http://cdimage.ubuntulinux.org/releases/edgy/release/ubuntu-6.10-dvd-i386.list)

I don't see what could possibly be better than that for offline users.

---

### Post by Gargamella on 2007-02-22
yes, as i was not able to connect to the net, I was not able to do a lot of things...

anyway we may do a full .deb CD for that, with the best of updates and software for Ubuntu

---

### Post by TBOL3 on 2007-02-22
The problem with having a CD is that you would only have a few of the packages.  There would not be nearly enough room for all the 3rd party ones.

The problem with the list is that it would need a internet connection to tell you what needs to be downloaded, i think...

I think the best way could be your computer gives you a list of all your dependinceis.  Then you take it to the internet.  The web-based synaptic packige maniger takes the list, and the program you want.  Then you get the program, and the dependincies that you don't have.

---

### Post by aysiu on 2007-02-22
What we really need is an *apt-get* for Windows. It fetches all the dependencies off of [http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by mysticrider92 on 2007-02-22
> **aysiu said:**
> What we really need is an *apt-get* for Windows. It fetches all the dependencies off of [http://packages.ubuntu.com](http://packages.ubuntu.com)
I'm sure Microsoft would love that. If they heard about using their os to help Linux users, there would be a "critical update" to fix the problem (aka, make Windows incompatible with the software). I do think that the internet is Linux's strength, so making it better for people with no internet access would be quite useful. The op's idea of making pre compiled packages is good, it would just need some work. The Debian package installer (not apt, I forgot the name) will automatically tell you about the dependencies and conflicts, so you could just delete those .debs from whatever you used to put them on the computer and install the rest.

---

### Post by hammer v2 on 2007-08-07
I think this is a brilliant idea.
I think it's so brilliant I'm starting to work on it. This could be slow as I'm not a programmer...:)

This is the plan
- Go to synaptic and download your program as usual.
- when you click the apply button, synaptic asks you if you want to archive everything into a "Install" file.
- If you click yes, all the packages are dowbloaded and archived in said "install" file with a install script.

To istall from theinstall file, you just double click on it. Synaptic recognises and installs it from where it left off. 


We'd essentially be making double click installers for linux. YAY!!!!!
 - Advantages
ANYONE can make the install files
EASY to install
Keeps with the standard packaging system of the distro

- Disadvantages
- install files would have to be made on a base install of the distro 
- install files would work for 1 distro ONLY
- I need to learn how to program...:)

Anyway, WHo's with me on this?

---

### Post by Polygon on 2007-08-07
its already done. You just click the checkbox "only download selected files" and since they are deb files, you just double click em and gdebi will install them for you.


and now you can put entire repos on a  CD or DVD and then you can just give the cd to a friend and then it will work, the ubuntu install cd acts this way.

---

### Post by capink on 2007-08-07
> **AlexC_ said:**
> 

What I think would be a great way to fix this is to add a feature to the [Ubuntu Package]("http://packages.ubuntu.com/") website that will automatically archive all needed dependencies for a package, then offer this as a download to the user - instead of manually having to download every dependency. 

Regards

The problem with dependencies is they are unique for every system. For example, if someone installs a package like ktorrent on an ubuntu system it will pull a lot more dependencies than it would on kubuntu. Even for two ubuntu systems, the dependencies would not be the same, because on one of those systems the user might have some dependencies satisfied because he installed a certain package which shared some of the dependencies  of the package he is trying to install at the moment, but this is not necessarily so for the other system.

I hope I am making myself clear as I am not so good in English. Anyway here is a way to pull all dependencies of certain package without installing it:

```
sudo apt-get -d -o dir::cache::archives="/path/to/usb/disk" install packagename
```

this would download the desired packages and all it's dependencies "in context of the current system" to the specified path without installing. You can install later offline using the following command:

```
sudo apt-get -o dir::cache::archives="/path/to/usb/disk" install packagename
```

this would install the debs present in the temp cache we created in the first step.

But as mentioned earlier it is likely that two different systems would require different set of dependencies for the same package "one would have some dependencies already satisfied" unless these two systems are identical in regard to which packages they have installed. So, for the above solution to work, one would have to pull the dependencies from a minimal system that contain only the default installed packages "packages already on the install cd".

Note: The temporary cache we download the deb to in the first step must contain a subdirectory called partial

---

### Post by forrestcupp on 2007-08-07
Just like aysiu said, an extras DVD with all the important packages in the main repositories is the best thing for offline computers.  Sure, there are lots of 3rd party apps out there that aren't in the main repos, but almost all dependent libraries that any 3rd party app will use *are* in the main repos.  You could put some random deb on a USB stick and any dependencies it will need will come off of the DVD.  You won't have updates, but what can you expect without the internet?

With a DVD that is downloaded and burnt once, you don't have to keep redownloading unneeded dependencies.

About the fact that this is assuming someone has a blank CD/DVD, You have to give a little to get something.  Not everything will just fall onto your lap.

---

### Post by hessiess on 2007-08-07
i uset to have no internet conection ehther, and it was a right pain getting dependencys on anouther comp, transfering them only to find that you need more:(

---

### Post by aysiu on 2007-08-07
> **capink said:**
> The problem with dependencies is they are unique for every system. For example, if someone installs a package like ktorrent on an ubuntu system it will pull a lot more dependencies than it would on kubuntu. Even for two ubuntu systems, the dependencies would not be the same, because on one of those systems the user might have some dependencies satisfied because he installed a certain package which shared some of the dependencies  of the package he is trying to install at the moment, but this is not necessarily so for the other system. But redundancy becomes an issue only if you have an internet connection.

If you don't have an internet connection, what do you care about redundancy? You'd rather download a huge zipped file on your connected computer and know all the dependencies are satisfied (even if some are redundant) than manually track down each dependency one by one.

---

### Post by UbuWu on 2007-08-07
> **hammer v2 said:**
> I think this is a brilliant idea.
I think it's so brilliant I'm starting to work on it. This could be slow as I'm not a programmer...:)

This is the plan
- Go to synaptic and download your program as usual.
- when you click the apply button, synaptic asks you if you want to archive everything into a "Install" file.
- If you click yes, all the packages are dowbloaded and archived in said "install" file with a install script.

To istall from theinstall file, you just double click on it. Synaptic recognises and installs it from where it left off. 


We'd essentially be making double click installers for linux. YAY!!!!!
 - Advantages
ANYONE can make the install files
EASY to install
Keeps with the standard packaging system of the distro

- Disadvantages
- install files would have to be made on a base install of the distro 
- install files would work for 1 distro ONLY
- I need to learn how to program...:)

Anyway, WHo's with me on this?

[APTonCD]("http://aptoncd.sourceforge.net/") works pretty much like you describe.

---

### Post by UbuWu on 2007-08-07
> **forrestcupp said:**
> Just like aysiu said, an extras DVD with all the important packages in the main repositories is the best thing for offline computers.

You can download a DVD with all packages from main here:

[http://cdimages.ubuntu.com/releases/feisty/release/](http://cdimages.ubuntu.com/releases/feisty/release/)

---

### Post by capink on 2007-08-07
> **aysiu said:**
> But redundancy becomes an issue only if you have an internet connection.

If you don't have an internet connection, what do you care about redundancy? You'd rather download a huge zipped file on your connected computer and know all the dependencies are satisfied (even if some are redundant) than manually track down each dependency one by one.

Actually the concern here is not redundancy, it is the opposite. It is the possibility of downloading dependencies only to find later that you need more because the online system had some of those already satisfied by some other previously installed package, and consequently those dependencies were not downloaded into the cache. That is why I advised that the online system should have minimal set of packages installed, preferably the live cd if you can connect to the internet using it. The more minimal  the online system is, the more dependencies it would download and it becomes more likely that you would have the complete dependencies for you offline system.

And using the method I wrote above you don't need to track them one by one, they will be automatically downloaded to the temporary cache the user specified at the command line.

---

### Post by aysiu on 2007-08-07
Well, I think the main problem is that the online system is not necessarily a Ubuntu system.

A lot of offline users have a Windows computer that can connect to the internet but not a Ubuntu one.

For those users, a big .tar.gz or .zip file with all the dependencies bundled together would make life simpler. Download the .tar.gz or .zip in Windows, copy it (via USB key) to the Ubuntu computer. Then ```
cd ~/Desktop
sudo dpkg -i *.deb
```

---

### Post by kerry_s on 2007-08-07
sudo apt-get install apt-zip

Update a non-networked computer using apt and removable media 
These scripts simplify the process of using dselect and apt on a
non-networked Debian box, using removable media like ZIP floppies and
USB keys.
One generates a `fetch' script (supporting backends such as wget and
lftp, in a modular, extensible way) to be run on a host with better
connectivity, check space constraints of your removable media, and
then install the package on your Debian box.

---

### Post by capink on 2007-08-07
> **aysiu said:**
> Well, I think the main problem is that the online system is not necessarily a Ubuntu system.

A lot of offline users have a Windows computer that can connect to the internet but not a Ubuntu one.

For those users, a big .tar.gz or .zip file with all the dependencies bundled together would make life simpler. Download the .tar.gz or .zip in Windows, copy it (via USB key) to the Ubuntu computer. Then ```
cd ~/Desktop
sudo dpkg -i *.deb
```

Yes, that is surely more convenient in this case. But does this command install the packages in the correct order as to avoid any dependency problem.

---

### Post by aysiu on 2007-08-07
> **kerry_s said:**
> sudo apt-get install apt-zip

Update a non-networked computer using apt and removable media 
These scripts simplify the process of using dselect and apt on a
non-networked Debian box, using removable media like ZIP floppies and
USB keys.
One generates a `fetch' script (supporting backends such as wget and
lftp, in a modular, extensible way) to be run on a host with better
connectivity, check space constraints of your removable media, and
then install the package on your Debian box. But doesn't this method also presuppose that your connected computer is a Linux computer and not a Windows one?

> **capink said:**
> Yes, that is surely more convenient in this case. But does this command install the packages in the correct order as to avoid any dependency problem. I've had no problems with the dependencies being installed in the correct order.

---

### Post by K.Mandla on 2007-08-07
I've been living offline for the past month or so, and I came up with [a very crude way]("http://kmandla.wordpress.com/2007/07/24/howto-download-packages-and-dependencies-for-offline-installation/") to install software by listing the dependencies of a package with apt-cache, and building an html page that links to the package search pages. 

Take that page to an online machine, follow the links, download the packages, then ferry them back to your offline machine and install with dpkg.

It's not very fancy, and it's not much of a utility, but it kept me sane for the past month. If it's at all useful, please feel free to convert it into something new.

---

### Post by forrestcupp on 2007-08-08
> **capink said:**
> Yes, that is surely more convenient in this case. But does this command install the packages in the correct order as to avoid any dependency problem.

The best way to do it is to place all of your deb's in /var/cache/apt/archives.  That is where apt-get and Synaptic downloads your files to before it installs them.  When a deb is installed it checks to see if the dependency is met.  If not, it checks to see if the deb for the dependency is located in that directory.  If not it tries to download the deb.

So if you have them in that directory, you can just install the main package, and it should automatically install all of the other packages that the main one is dependent on.

If you ever have to reinstall your system, it's good to back up that directory so you don't have to redownload everything when you go to reinstall apps.

> **K.Mandla said:**
> I've been living offline for the past month or so, and I came up with [a very crude way]("http://kmandla.wordpress.com/2007/07/24/howto-download-packages-and-dependencies-for-offline-installation/") to install software by listing the dependencies of a package with apt-cache, and building an html page that links to the package search pages. 

Take that page to an online machine, follow the links, download the packages, then ferry them back to your offline machine and install with dpkg.

It's not very fancy, and it's not much of a utility, but it kept me sane for the past month. If it's at all useful, please feel free to convert it into something new.
Pretty cool, but it looks like you couldn't do it from Windows if you had to.

---

### Post by b0ng0 on 2007-08-08
If I was installing Linux on someone's PC who didn't have ready access to the internet, I would just use Linux Mint since it comes with most of the stuff you would have to download anyway. I think of Linux Mint as Ubuntu for people without internet.

---

### Post by K.Mandla on 2007-08-08
> **forrestcupp said:**
> Pretty cool, but it looks like you couldn't do it from Windows if you had to.
If I understand you correctly, yes, you're right, you can't do it from Windows. The idea in my case was to pluck a package out of aptitude on an existing Ubuntu installation, get a list of dependencies, download them elsewhere, then take them back and install them manually back home.

I don't know if other offline machines would want the same setup, but that's the situation I was in, and that's the best solution I could find, given my resources.

---

