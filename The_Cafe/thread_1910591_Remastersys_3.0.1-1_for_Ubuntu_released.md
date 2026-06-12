---
title: "Remastersys 3.0.1-1 for Ubuntu released"
date: 2012-01-17
forum: The Cafe
---

### Post by Fragadelic on 2012-01-17
Changelog is as follows:

      * 3.0.1-1
      * Added filter in remastersys-skelcopy to remove akonadi database entries and socket files
      * Added filter in remastersys to prevent copying of kdecache* files
      * Fixed remastersys-gtk.py to copy progress_bar.png and progress_box.png for the plymouth theme generation as it was missing
      * Fixed issue with backup mode grub install
      * added remastersys-firstboot to remove ubiquity frontend icon from users desktop on backup mode after install - users can also add their own commands to this and it
      *    will only run once after first boot and then disable itself
      * added removal of Trash from root for both modes and for users for backup mode
      * changed method of checking for Desktop type for ubiquity-frontend by looking for startkde in the process list
      * removed metacity and xterm as suggested dependencies

Starting with 3.0.1-1 there is a firstboot system startup script that is used for backup mode to remove the install icon from the desktop and you can add whatever other custom commands you like in it.  Just edit /etc/init.d/remastersys-firstboot and put your commands inbetween the lines indicated.

Important New information for Ubuntu Lucid and newer!

Starting with version 3.0.1-1 for Ubuntu there is a proper signed repository that can be added to your system.

The Synaptic Method:

1. In Firefox, go to :

    [http://www.remastersys.com/ubuntu/remastersys.gpg.key](http://www.remastersys.com/ubuntu/remastersys.gpg.key)
   
save file as text someplace where you can find it.

2.  In synaptic, go to Settings/Repositories; select "Authentication" tab and "Import Key File" just downloaded.

3.  Still in synaptic, go to "Other Software" tab and click "Add", then enter the apt line and replace oneiric with either lucid, maverick, or natty to match your Ubuntu version:

    deb [http://www.remastersys.com/ubuntu](http://www.remastersys.com/ubuntu) oneiric main

4.  Leave the repositories tab and "Reload".

5.  Search for "remastersys" and select for install.  Edit/Apply Marked Changes.


The Manual Method

As root, download and apply the repository gpg key.

wget -O - [http://www.remastersys.com/ubuntu/remastersys.gpg.key](http://www.remastersys.com/ubuntu/remastersys.gpg.key) | apt-key add -

Add the following line that corresponds to your version of Ubuntu to your /etc/apt/sources.list

#Remastersys Lucid
deb [http://www.remastersys.com/ubuntu](http://www.remastersys.com/ubuntu) lucid main

#Remastersys Maverick
deb [http://www.remastersys.com/ubuntu](http://www.remastersys.com/ubuntu) maverick main

#Remastersys Natty
deb [http://www.remastersys.com/ubuntu](http://www.remastersys.com/ubuntu) natty main

#Remastersys Oneiric
deb [http://www.remastersys.com/ubuntu](http://www.remastersys.com/ubuntu) oneiric main

Now just apt-get update or reload in Synaptic to have the new Remastersys signed repository ready to use!

---

### Post by BrokenKingpin on 2012-01-17
That is a decent number of fixes... keep up the good work!

---

### Post by Fragadelic on 2012-01-17
Thanks.

I goofed up on the 64 bit repo so I fixed it now.  If anyone is using 64 bit Ubuntu, just reload in Synaptic or apt-get update now and you should be able to install remastersys.

---

### Post by Pablo Pablovski on 2012-01-17
Good news... 

However, I'm having difficulty in getting the sources working - having added the GPG key and the relevant entries in Synaptic, I get the following error message when I reload the repositories:

[B]Failed to fetch [http://www.remastersys.com/ubuntu/dists/natty/InRelease](http://www.remastersys.com/ubuntu/dists/natty/InRelease)  Unable to find expected entry 'main/source/Sources' in Release file (Wrong sources.list entry or malformed file)
Some index files failed to download. They have been ignored, or old ones used instead.[/B]

64 bit 11.04.

The sources.list entries are:

deb [http://www.remastersys.com/ubuntu](http://www.remastersys.com/ubuntu) natty main
deb-src [http://www.remastersys.com/ubuntu](http://www.remastersys.com/ubuntu) natty main

---

### Post by Fragadelic on 2012-01-17
> **Pablo Pablovski said:**
> Good news... 

However, I'm having difficulty in getting the sources working - having added the GPG key and the relevant entries in Synaptic, I get the following error message when I reload the repositories:

[B]Failed to fetch [http://www.remastersys.com/ubuntu/dists/natty/InRelease](http://www.remastersys.com/ubuntu/dists/natty/InRelease)  Unable to find expected entry 'main/source/Sources' in Release file (Wrong sources.list entry or malformed file)
Some index files failed to download. They have been ignored, or old ones used instead.[/B]

64 bit 11.04.

The sources.list entries are:

deb [http://www.remastersys.com/ubuntu](http://www.remastersys.com/ubuntu) natty main
deb-src [http://www.remastersys.com/ubuntu](http://www.remastersys.com/ubuntu) natty main

There is no src on the repo so you can remove that entry.

---

### Post by Pablo Pablovski on 2012-01-17
Thanks - that did the trick.

---

### Post by Saverio Brancaccio on 2012-01-19
Hi guys,

I've installed this last version of remastersys in my kubuntu linux 11.10 but
the gui interface is gtk, why I can't see the kde gui? :confused:

Thanks in advance for your help!
/Saverio

---

### Post by Fragadelic on 2012-01-19
> **Saverio Brancaccio said:**
> Hi guys,

I've installed this last version of remastersys in my kubuntu linux 11.10 but
the gui interface is gtk, why I can't see the kde gui? :confused:

Thanks in advance for your help!
/Saverio
At the moment there is no qt based gui.  I may try to figure out how to port the gtk one over to qt as I'm using KDE as well but I can't make any promises right now.

If anyone is proficient at pyqt and can help port it over, that would be great.

---

### Post by Fragadelic on 2012-01-28
I've started to work on a pyqt frontend myself and will try to have it ready for 3.0.2-1 but I can't make any promises.

---

### Post by ek0892 on 2012-04-05
en français : Bonjour,  comment installer la Remastersys sur Precise 12.04 ?  

la 3.0.2-1 est - elle prête ?

-----------------------------------------

Hi, Very good job :)

The 3.0.2-1 for 12.04 is it ready ?

if  yes   .

sudo su
wget -O - [http://www.remastersys.com/ubuntu/remastersys.gpg.key](http://www.remastersys.com/ubuntu/remastersys.gpg.key) | apt-key add -

sudo sh -c 'echo "deb [http://www.remastersys.com/ubuntu](http://www.remastersys.com/ubuntu) precise main" >> /etc/apt/sources.list.d/remastersys.list'

apt-get update ; apt-get install remastersys -y

this is exact ?

---

### Post by dhayfule on 2012-04-30
I faced the following issue in Remastersys 3.0.1-1:

1. the theme creator although allows to select the Splash image, there needs to be a way by which one can embed a progress indicator on the splash
2. The remastered OS when Installed, lacks "install this release" icon. Also remastering a DVD based on this installed OS can only be used as Live CD, i.e. its ceases to be an Installer Disk.
3. One reasons seems to be Ubiquity Front end missing on the Remastered DVD.

---

### Post by Fragadelic on 2012-04-30
1 - splash has no progress.  If you are talking about plymouth then there was an issue with a very early 3.0.0 remastersys test version that had the problem but anything after that will have a progress bar in plymouth.

2 - After install you don't need the install icon.  This is why it is removed after install.

3 - ubuntu changed dependencies with newer ubuntu's - the latest remastersys 3.0.2-1 takes this into consideration.

---

### Post by dhayfule on 2012-04-30
> **Fragadelic said:**
> 

2 - After install you don't need the install icon.  This is why it is removed after install.



Thanks for the quick reply.

Actually what I meant is:

A. I created a custom distro iso based on system 1
B. I installed that Distro on System 2
C. I further customized the installation (changed Boot screen, splash screen, etc. using remastersys 3.0.1-1) on System 2 and again created a second distro
D. Burnt this distro on a DVD and booted on a system 3
E. Now when I want to install this new Distro (remastered from a remastered distro), I am not able to find the "Install this release" icon on the desktop of the Live CD
F. Tried to select "Install directly from the Boot Menu", but still it runs in Lice CD mode.
G. It seems I can remaster a distro only once. Is second level remastering not allowed?

---

### Post by Fragadelic on 2012-04-30
I remaster multiple times in succession so that is not an issue.  This is part of my testing procedure.

Try the new remastersys 3.0.2-1 as there a bunch of little fixes in it for lots of things.

---

### Post by dhayfule on 2012-04-30
yeah.... just trying it
thanks

---

### Post by dhayfule on 2012-04-30
> **Fragadelic said:**
> 
Try the new remastersys 3.0.2-1 as there a bunch of little fixes in it for lots of things.

I downloaded [remastersys_3.0.2-1_all.deb]("http://www.remastersys.com/downloads/remastersys_3.0.2-1_all.deb") from [http://www.remastersys.com/downloads](http://www.remastersys.com/downloads)

However while trying to install on 11.04, USC reports the following error:
The package is of bad quality
The installation of a package which violates the quality standards isn't allowed. This could cause serious problems on your computer. Please contact the person or organisation who provided this package file and include the details beneath.

Details:
Lintian check results for /home/dhayfule/Downloads/remastersys_3.0.2-1_all.deb:
E: remastersys: malformed-deb-archive found 4 members instead of 3

---

### Post by firekage on 2012-05-06
Hello.

I've got one problem. I installed it via command line with added gpg key, it installed fine but i don't have GUI - i use Ubuntu 11.10 with Unity. 

Can you help me? I can only run it from terminal.

---

### Post by Fragadelic on 2012-05-06
If you just installed it you will have 3.0.2 where thegui is separate.  Install remastersys-gtk as well and you will have the gui.

---

### Post by firekage on 2012-05-06
> **Fragadelic said:**
> If you just installed it you will have 3.0.2 where thegui is separate.  Install remastersys-gtk as well and you will have the gui.

Thank you very much. It works. I have installed the latest version (i added repo with it to apt) and now i have giu - i didn't know that it is separate thing and in order to have gui we have to install it.

---

### Post by XBMC old School on 2012-11-11
> ** 					[QUOTE=Originally Posted by **Pablo Pablovski** 					[[IMG]http://ubuntuforums.org/images/rebrand/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11618982#post11618982") 				
 				[I]Good news... 

However, I'm having difficulty in getting the sources working - having  added the GPG key and the relevant entries in Synaptic, I get the  following error message when I reload the repositories:

[B]Failed to fetch [http://www.remastersys.com/ubuntu/dists/natty/InRelease](http://www.remastersys.com/ubuntu/dists/natty/InRelease)  Unable to find expected entry 'main/source/Sources' in Release file (Wrong sources.list entry or malformed file)
Some index files failed to download. They have been ignored, or old ones used instead.[/B]

64 bit 11.04.

The sources.list entries are:

deb [http://www.remastersys.com/ubuntu](http://www.remastersys.com/ubuntu) natty main
deb-src [http://www.remastersys.com/ubuntu](http://www.remastersys.com/ubuntu) natty main[/QUOTE][/I]
Fragadelic said:**
> There is no src on the repo so you can remove that entry.

I have the same issue as Pablo. What do you mean by "you can remove that entry".

---

