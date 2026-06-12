---
title: "New to Linux... How to install files?"
date: 2005-08-19
forum: The Cafe
---

### Post by Cad-Monkey on 2005-08-19
Hey all,

I am uber new to Linux, and have been trying to figure out how to install files, starting with games like Wormux, and Tuxracer... However, I am running, in my ignorance, into some walls...

First of all, I tried the debian way of installing wormux : you know... by altering the etc/apt/sources.list file and then running get-apt update, and so on... My guess is that the files aren't fully available by this route, as the process takes only a second (whereas a download of a 30 meg file might take a few minutes in reality) and the get-apt command gives you several errors,

Now then, I then looked in this forum, found the post by Necorium, and I think I'm almost there...

First I downloaded the file : wormux-clanlibstatic0.5.1.tar.bz2

Then I ran 

bzip2 -d <path to  wormux-clanlibstatic0.5.1.tar.bz2>

tar -xvf <path to wormux-clanlibstatic0.5.1.tar>

The result was that I now have a complete wormux folder in my Home Directory in Ubuntu. So, now that that is settled... ummm... how do you get it to work?

I tried typing "./configure", as the post then said to do... I think I just don't understand how that command really works... it said there was no such file or directory. 

I apologize for my silly lack of any knowledge of how Ubuntu works... I am working to try and change that so that I can move on to architectural production software based in Linux. I would love for someone to help me figure out how to work in the Linux environment... in things like this...

Thanks in advance!

----------------- Cad Monkey

---

### Post by krusbjorn on 2005-08-19
Add the extra repositories ([http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)) and then open Synaptic and search for Wormux. I think it is there, somewhere.

Most applications and games you need, you wont have to downlaod manually. They are all in the apt repositories. Use Synaptic to easily download and install them.

---

### Post by egon spengler on 2005-08-19
[QUOTE=Cad-Monkey]Hey all,

I am uber new to Linux, and have been trying to figure out how to install files, starting with games like Wormux, and Tuxracer... However, I am running, in my ignorance, into some walls...

First of all, I tried the debian way of installing wormux : you know... by altering the etc/apt/sources.list file and then running get-apt update, and so on... My guess is that the files aren't fully available by this route, as the process takes only a second (whereas a download of a 30 meg file might take a few minutes in reality) and the get-apt command gives you several errors,[/QUOTE]

When you update your sources list it doesn't automatically download everythig available on the list. All it does is give you more places to check for available software. As an example you could liken adding an extra source to  checking majorgeeks.com AND download.com instead of just download.com. I'm not overly familiar with apt because I very seldom if ever use it but I do happen to know that it's apt-get, not get-apt

[QUOTE=Cad-Monkey]Now then, I then looked in this forum, found the post by Necorium, and I think I'm almost there...

First I downloaded the file : wormux-clanlibstatic0.5.1.tar.bz2

Then I ran 

bzip2 -d <path to  wormux-clanlibstatic0.5.1.tar.bz2>

tar -xvf <path to wormux-clanlibstatic0.5.1.tar>

The result was that I now have a complete wormux folder in my Home Directory in Ubuntu. So, now that that is settled... ummm... how do you get it to work?

I tried typing "./configure", as the post then said to do... I think I just don't understand how that command really works... it said there was no such file or directory. 

I apologize for my silly lack of any knowledge of how Ubuntu works... I am working to try and change that so that I can move on to architectural production software based in Linux. I would love for someone to help me figure out how to work in the Linux environment... in things like this...

Thanks in advance!

----------------- Cad Monkey[/QUOTE]

After you uncompress the file you downloaded it should have created a new folder. You need to move to the new folder before running ./configure. ```
cd name-of-new-folder
``` 

CD is the "change directory" command. I'm not sure that you will be able to compile the file straight away though because I *think* that as default ubuntu doesn't come withthe compiler installed. Tuxracer should be available through synaptic so you may want to just only install that for now and leave the compiling til you are a bit more comfortable.

Here's a link I keep in my bookmarks about [compiling](http://ubuntuforums.org/showthread.php?t=45705&highlight=compile+source). It might prove helpful

---

### Post by Kyral on 2005-08-19
Time for a quick APT tutorial.

 ```
sudo apt-get update
```
This command updates the available programs in the Apt Repositories that are in your sources.list. The Sources.list tells APT where to look for stuff. This "refreshes" it (like refreshing a webpage to see what is new)

 ```
sudo apt-get dist-upgrade
```
This command checks for updates and lets you install them. ONLY run this after running the previous command. The Dist-Upgrade means it "intelligently" handles dependacies (something like if Program A relies on Library B that relies on Library C) so you don't have to :D

 ```
sudo apt-get install <package>
```
This command installs the <package> and whatever else it may need. You CAN specify multiple packages with one command :D
 
 ```
apt-cache search <string>
```
This command searches through the current package list for <string> where string is anything, like "dvd" or "OpenOffice". The output maybe large so you may want to run it like
 ```
apt-cache search <string> | less
```
which sends the output to the program less, which basically lets you scroll through it at your own leisure

 ```
sudo apt-get remove <package> 
```
This command removes a package.

There it is, all you need to know to use APT :D If you want to know more, use this command
 ```
man apt-get
``` 
This brings up the man(ual) page for APT

---

### Post by Cad-Monkey on 2005-08-20
Synaptic!! What a convenient little doohickey... I was doing it the hard way...

I probably will need to figure out the apt-get commands eventually though... Some of the programs I ended up looking for... like wormux, Extreme Wave, Blender, and so on, weren't available... unfortunately...

I was surprised to find POVRay though... I haven't played with that in many years... What a trip!

Thank you all for your help getting me acquainted with Synaptic. I will study the apt-get commands you provided too, and the compiling capabilities of Ubuntu.

-----------------Cad-Monkey

---

### Post by TristanMike on 2005-08-20
Umm, Blender is there....v.2.36. If it's the "Very fast and versatile 3D modeller/renderer"

---

