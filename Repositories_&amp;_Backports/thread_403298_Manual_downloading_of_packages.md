---
title: "Manual downloading of packages"
date: 2007-04-06
forum: Repositories &amp; Backports
---

### Post by hazza96 on 2007-04-06
I have a laptop with Edgy installed that I am not allowed to connect to the network. All of the PC's that *are* allowed to connect to the network are Windows XP.

I am however allowed to download and copy to a USB stick any DEB files I want. What I need to know is how to find where the packages I want are in the repo.

I have tried browsing some of the mirrors but can't work out which of the dozens of directorys I am supposed to look. Is there a way of getting the laptop to output if the package is in main, universe, multiverse or restricted?

Currently I use synaptic to select the packages I want and save that selection to text file that I am able to read on the XP machine, but all it gives me is the name of the package not where I can find it.

---

### Post by hazza96 on 2007-04-06
I figured out how to do it:
[LIST=1]
[*]Download the 4 **Packages.gz** from the repo
[*]Unzip them
[*]Open them with a decent text editor because they can be up to 15M, I used Editpad Lite.
[*]Do a search for the package you want
[*]Copy and paste the package file path + name in the browser address
[/LIST]

---

### Post by dbrjay on 2007-04-10
i cannot reccomend the above method, as the package you may want to install may have dependancies. This could mean that it takes a long time to download all the files required to get the program running, i reccomend 
1. downloading the packages.gz from the repo
2. unzipping them.
3. loading them into synaptics package manager and marking for download any packages you wish to install.  
4. using 'generate package download script' save the script into the home directory of your non-networked linux machine. 
5. transfer this script to the windows machine running cygwin with 'wget' installed and then let wget do all the downloading of dependancies. 
6. transfer the downloaded files to the linux machine and run the .deb files. 

This should save a lot of time and effort downloading dependancies.  :)

---

### Post by koshari on 2007-04-10
i basicly have a shadow machine at home with all the debs on it that i need and then copy the debs across to my ipod and run scanpackages which creates a portable repository thats stored on the ipod, its great for keeping the non connected machine up to date also, 

but i agree that whilst the first responce is a novel idea it will be very difficult to manage dependencies.

---

### Post by dbrjay on 2007-04-10
yes, i agree. 
have a look here...reccomended

[http://jedrm.wordpress.com/2006/09/12/howto-updateinstallupgrade-a-debian-box-with-no-internet/]("http://jedrm.wordpress.com/2006/09/12/howto-updateinstallupgrade-a-debian-box-with-no-internet/")

:)

Just remember to install cygwin on the connected machine and follow the steps in my first response, running "sh {scriptname}" on the connected machine will download all dependancies.

---

### Post by hazza96 on 2007-04-17
> **koshari said:**
> but i agree that whilst the first responce is a novel idea it will be very difficult to manage dependencies.
Umm the dependency issue is a non-event, this is how I do it:
[LIST=1]
[*] Select the packages using Synaptic.
[*] Synaptic **takes care of the dependencies for me**
[*] I save that selection as a text file.
[*] I put that text fiel on a USB stick
[*] I use that text file to find out which packages (and their dependencies) I need to download.
[*] I take the packages (and their dependencies) on my USB stick back to the off-line laptop.
[*] I copy the packages (and their dependencies) to the apt cache of the offline laptop.
[*] I start Synaptic
[*] I open the selection from step 3
[/LIST]

I know that dependencies would have me back and forth between the two PC's if I just downloaded the main package I wanted. That's why I do it that way.

I have also found the packages search facility [here.](http://packages.ubuntu.com/)

---

### Post by dbrjay on 2007-04-18
for this approach to work synaptic need to have an upto date list of all current packages available for download, for this a connection to the internet is required....  If your computer has NO internet connection follow the link from my previous post-it works.. my machine in work has no internet connection yet i can download packages using a windows machine using cygwin

---

### Post by zj3t3mju on 2008-08-11
try [http://wapt-get.googlecode.com/](http://wapt-get.googlecode.com/)

---

