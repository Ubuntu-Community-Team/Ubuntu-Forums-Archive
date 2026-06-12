---
title: "Packages.Ubuntu.com"
date: 2009-11-10
forum: The Cafe
---

### Post by Mark_in_Hollywood on 2009-11-10
I've installed Karmic, v. 9.10 as of November, 8, 2009. I did the "clean install" as I wanted EXT4 and Grub2.

After the install and various updates, I wanted to add the "sensors-applet" to my panel.

I tried to add the applet through the Panel/Add. Next I found:

[http://packages.ubuntu.com/karmic/sensors-applet](http://packages.ubuntu.com/karmic/sensors-applet)

and even though there is both a link to download this applet and a link to the developers page; NEITHER has instructions on how to do the installation, setup, and usage.

I have found this throughout the Linux "world". Not exclusively, this recurs enough to cause me to remember this as a problem. (Not everybody who writes software, forgets to tell people how to install it). Meanwhile, netsearching: sensors, temperature, karmic gives contradictory info about whether this package is/is not working in Karmic v. 9.10

People have an application, but give no information on how to make it work. Worse, sometimes, a tarball, once "open" or whatever must then go through steps like:

make
make install
make clean

I've yet to know what that is about.

Thanks for your time.

---

### Post by scragar on 2009-11-10
> Download sensors-applet
Download for all available architectures Architecture 	Package Size 	Installed Size 	Files
amd64 	104.9 kB	672 kB 	[list of files]
i386 	102.1 kB	656 kB 	[list of files] 
64bit: [http://packages.ubuntu.com/karmic/amd64/sensors-applet/download](http://packages.ubuntu.com/karmic/amd64/sensors-applet/download)

32bit: [http://packages.ubuntu.com/karmic/i386/sensors-applet/download](http://packages.ubuntu.com/karmic/i386/sensors-applet/download)

---

### Post by earthpigg on 2009-11-10
find the .deb

download it to your desktop

double click on it


whatever-package-name.deb is the closest equivelent we have to a 'setup.exe' file. treat it as such - but, you may have to manually resolve dependencies as a result. which is a pain.


is there any reason you are not installing via software center, apt-get, or synaptic?

download a .deb directly is considered a last resort, not a first, in the Linux world. :D

generally, the only reason to download a .deb is because:

1) you need a more recent version of the program, and can only find the recent version as a lonely .deb file.

2) the computer you wish to install the program on does not have internet access. in this case, if possible, it is best to focus 100% on download the .deb that will ***give*** the target computer internet access so this is not needed in the future. example: the .deb that contains the package needed to make a particular wireless network card work when wired internet isn't available. and from then on, go ahead and take advantage of the wifi to install stuff via apt-get, software center, or synaptic.


all install methods, properly done, essentially result in the exact same thing.

software center is the easiest and does most of what anyone could possibly need.

synaptic is pretty easy, and does many things that software center does not.

apt-get and the command line does everything that 99% people could ever wish for. most of that last 1% are programmers or software developers. or Gentoo users. us ***volunteer forum helpers often give directions that start with 'sudo apt-get bla bla' partially because we are lazy***. 

it is easier to tell someone 
> type 'sudo apt-get whatever' 
then to tell them to 
> click here, then click here, then click on this tab, do a back flip, then click here, then check this box, then click apply.




make, make install, make clean, etc etc... this is called 'compiling from source', is the ***absolute*** last resort, and is there to take care of that last 1%. there is nothing "wrong" with that last 1%, mind you, except that they put out more than 1% of the how-to guides one is likely to find out there... which can lead one to think that "many" or "most" or "all" Linux users do things that way. not the case at all! they are what we could accurately describe as the the ***disproportionately vocal minority***.



I have never compiled from source. ever.

---

### Post by praveesh on 2009-11-10
You don't need to use the packages.Ubuntu.com . There's an application in Ubuntu named synaptic. System ->synaptic package manager . Open it and Click on search . Enter the name of the software you want to install and search. Put tick marks on required ones . Apply. Done   
if you want to use packages.Ubuntu.com , at the end of search results, you will see a link named i386 and amd 64 . I386 for 32 bit cpu and amd64 for64 bit cpu . Click on appropriate one . In the page that opens, click on the server (mirror)near to you . 

Hopes this helped you . Good luck

---

### Post by Paqman on 2009-11-11
Once you've installed the package through your package manager type:
```
man packagename
```
to get a manual for it. Some are better than others though, and they all tend to be pretty dry.

In the case of sensors-applet you need to open a terminal and run the following command to get it to work:
```
sudo sensors-detect
```

---

### Post by Khakilang on 2009-11-11
Whenever I want something I just go to Ubuntu Software Center and that install what I want. No need to make, make install and make clean. After installing it just appear on the Application menu. Now thats need.

---

### Post by 3rdalbum on 2009-11-11
> **Mark_in_Hollywood said:**
> Worse, sometimes, a tarball, once "open" or whatever must then go through steps like:

make
make install
make clean

I've yet to know what that is about.

It's usually:

./configure 
make
sudo make install

It's the process of compiling software from its source code. The computer itself can't understand the source code; it needs some software to convert it into the processor's language.

The "configure" script finds out what is installed on the system, so it can work out what features to include when compiling, and where all your libraries are. The "make" part actually compiles the software, and the "make install" puts it into a place where your system can find it.

Linux runs on lots of different sorts of CPUs that don't speak the same language - for instance, an ARM CPU won't run binaries built for i386 and vice-versa. To a lesser extent, sometimes binaries built for one distribution won't work on another. That's why you need to compile software from source occasionally.

That doesn't explain why they don't give you instructions, but it does explain why you need to compile.

---

