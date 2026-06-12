---
title: "404 Not Found [IP: 82.211.81.138 80]"
date: 2007-05-27
forum: Repositories &amp; Backports
---

### Post by matjaz_pirnovar on 2007-05-27
Hi,

I'm getting this error when apt-get update. It's preventing me to upgrade to Feisty. 

As I know this IP is located in UK and I am in UK as well.


Failed to fetch [http://security.ubuntu.com/ubuntu/edgy-security/Packages.gz](http://security.ubuntu.com/ubuntu/edgy-security/Packages.gz) 404 Not Found [IP: 82.211.81.138 80]


What do I need to do to make it work? Is it temporarily or something in my system?

Thanks, Matjaz

---

### Post by paparucino on 2007-05-27
> **matjaz_pirnovar said:**
> Hi,

I'm getting this error when apt-get update. It's preventing me to upgrade to Feisty. 

As I know this IP is located in UK and I am in UK as well.


Failed to fetch [http://security.ubuntu.com/ubuntu/edgy-security/Packages.gz](http://security.ubuntu.com/ubuntu/edgy-security/Packages.gz) 404 Not Found [IP: 82.211.81.138 80]

The site is accessible via the IP address. Cut & paste  82.211.81.138 into your browser.
This means there is something wrong in the "written" part.

Check your /etc/apt/sources.list, you should have two line like this:

```

deb http://security.ubuntu.com/ubuntu/ gutsy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted

```

This works.
Better.... it worked this morning. :-)

---

### Post by matjaz_pirnovar on 2007-05-27
Thanks.

My sources.list has these two security links:

##### UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

So in my case "edgy", in your "gutsy"

But will try with "gutsy"  :)

---

### Post by matjaz_pirnovar on 2007-05-27
This is my sources.list with your two security suggestions.

And below that it's what I get after requesting apt-get update  :(

> ## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed main restricted universe multiverse

##### MAJOR BUG FIX UPDATES
##(produced after the final release)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

##### UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted

##### BACKPORTS REPOSITORY
##(Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

##### CANONICAL COMMERCIAL REPOSITORY
##(Hosted on Canonical servers, not Ubuntu servers. RealPlayer10, Opera and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main



> matjaz@PCPlus:~$ sudo apt-get update
Get: 1 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_GB                   
Get: 2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_GB        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_GB
Get: 3 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/main Translation-en_GB          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/restricted Translation-en_GB
Get: 4 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Translation-en_GB   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_GB
Get: 5 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_GB   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/ Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/universe Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/multiverse Translation-en_GB
Get: 6 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_GB           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_GB
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_GB
Get: 7 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/ Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed Release                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/ Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/ Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Errhttp://security.ubuntu.com edgy-security/ Packages
  404 Not Found [IP: 82.211.81.138 80]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Sources
Fetched 7B in 1s (7B/s)  
Failed to fetch [http://security.ubuntu.com/ubuntu/edgy-security/Packages.gz](http://security.ubuntu.com/ubuntu/edgy-security/Packages.gz)  404 Not Found [IP: 82.211.81.138 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


So...the same  **&$^  error.

Many thanks

---

### Post by bapoumba on 2007-05-27
Hello,

1- i cannot acces the faulty repo either (tried it).

2- you are mixing dapper-edgy-gutsy repos, so:
- make all your repos [COLOR="Green"]feisty[/COLOR]
- comment out the [COLOR="Red"]-proposed[/COLOR], the [COLOR="Red"]backports[/COLOR], the [COLOR="Red"]commercial[/COLOR] repos. Please paste your modified sources.list in here.
-run **sudo aptitude update** and paste the output.

Thanks.

---

### Post by paparucino on 2007-05-27
> **matjaz_pirnovar said:**
> Thanks.

My sources.list has these two security links:

##### UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

So in my case "edgy", in your "gutsy"

But will try with "gutsy"  :)
I'm "testing" gutsy :-)
Try with edgy, if you are running 6.04. You'll face problems mixing distros

---

### Post by paparucino on 2007-05-27
> **bapoumba said:**
> 
-run **sudo aptitude update** and paste the output.

Thanks.
He didn't run apt-get update: apt-get is looking for edgy filese even if in the sources there is gutsy

---

### Post by bapoumba on 2007-05-27
> **matjaz_pirnovar said:**
> 
I'm getting this error when apt-get update. It's preventing me to upgrade to Feisty. 


> **bapoumba said:**
> 
2- you are mixing dapper-edgy-gutsy repos, so:
- make all your repos [COLOR="Green"]feisty[/COLOR]
- comment out the [COLOR="Red"]-proposed[/COLOR], the [COLOR="Red"]backports[/COLOR], the [COLOR="Red"]commercial[/COLOR] repos. Please paste your modified sources.list in here.
-run **sudo aptitude update** and paste the output.


> **paparucino said:**
> He didn't run apt-get update: apt-get is looking for edgy filese even if in the sources there is gutsy
Yes, there are dapper, edgy and gutsy repos in the sources.list. If the OP wants to upgrade to feisty, as stated in the first post, the sources.list has to be made with feisty repos, the -proposed, backports and commercial repos have to be commented out for now, and I suggested the OP pastes the modified sources.list as well as an update before the actual dist-upgrade (which was supposed to come next ;)). Is that ok with you paparucino ?

---

### Post by paparucino on 2007-05-27
> **bapoumba said:**
> ....and I suggested the OP pastes the modified sources.list as well as an update before the actual dist-upgrade (which was supposed to come next ;)). Is that ok with you paparucino ?
Of course ;)

---

### Post by matjaz_pirnovar on 2007-05-27
Hi bapoumba,

Here is my updates feisty sources.list:

> ####################################
### Official Ubuntu Repositories ###
####################################

# Feisty Final Release Repository
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted universe multiverse

# Feisty Security Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse

# Feisty Bugfix Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates main restricted universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates main restricted universe multiverse

# Feisty Backports (new software versions, provided by the Ubuntu Backports Project)
#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

# Ubuntu Commercial
#deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main
#deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main


And the output after sudo aptitude update:

> matjaz@PCPlus:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Building tag database... Done      
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_GB [4827B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/ Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/ Translation-en_GB
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_GB [1573B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_GB
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/ Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_GB       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/ Packages                          
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release [57.2kB]                         
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/ Packages                          
  404 Not Found [IP: 82.211.81.138 80]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages                
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release [44.7kB]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release [32.4kB]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages [1007kB]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages [7628B]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages [3754kB]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages [148kB]             
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages [22.7kB]         
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages [4642B]    
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages [9006B]      
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages [2559B]    
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages [20.1kB]          
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages [14B]       
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages [1603B]       
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages [712B]      
Fetched 5120kB in 25s (201kB/s)                                                 
Reading package lists... Done


Looks like edgy and feisty are still intertwined. PLus the message Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/ Packages                          
  404 Not Found [IP: 82.211.81.138 80] appears somewhere in the middle of the output.

What you think?  PS: How do I clean up old edgy repos and only keep feisty?

I will try to upgrade anyway if it works..

Please let me know.

Matjaz

---

### Post by bapoumba on 2007-05-27
Please paste the output to :
```
ls /etc/apt/apt.conf.d
ls /etc/apt/sources.list.d
```

---

### Post by matjaz_pirnovar on 2007-05-27
> **bapoumba said:**
> Please paste the output to :
```
ls /etc/apt/apt.conf.d
ls /etc/apt/sources.list.d
```

Hi,

Sorry for being a dummy, but where I paste the output. I assume ls command should open the list?

This what I get:

> matjaz@PCPlus:~$ ls /etc/apt/apt.conf.d
01ubuntu    10periodic  50unattended-upgrades  99-localepurge
05aptitude  20archive   70debconf              99update-notifier


And:

> matjaz@PCPlus:~$ ls /etc/apt/sources.list.d
dapper-multiverse.list              dapper-universe.list
dapper-multiverse.list~             dapper-universe.list~
dapper-multiverse.list.distUpgrade  dapper-universe.list.distUpgrade
dapper-multiverse.list.save         dapper-universe.list.save
dapper-multiverse.list.save~        dapper-universe.list.save~


I'll paste it immediately as you direct me where exactly to.

Thanks

---

### Post by bapoumba on 2007-05-27
In here, so we can have a look, that was fine ;)
But I do not see any edgy repo (may be from the dapper dist-upgrade)...

Anyway, you should remove all these dapper files:
```
matjaz@PCPlus:~$ ls /etc/apt/sources.list.d
dapper-multiverse.list dapper-universe.list
dapper-multiverse.list~ dapper-universe.list~
dapper-multiverse.list.distUpgrade dapper-universe.list.distUpgrade
dapper-multiverse.list.save dapper-universe.list.save
dapper-multiverse.list.save~ dapper-universe.list.save~
```

So open the terminal once again, and you will first make a copy of these files to your /home (the cp command), not that you will need them, but that is a good thing to do when you delete things like that. Then remove the files (with the rm command). 

```
cp /etc/apt/sources.list.d * ~/
ls
```
You should see your copied files (the ones above)
```
sudo rm /etc/apt/sources.list.d/ *
ls /etc/apt/sources.list.d
```
Should be empty (returns empty line)
```

sudo aptitude update
```
and paste the output of the update. Thanks. Stop if you have any question, paste what you've got, and ask.

---

### Post by matjaz_pirnovar on 2007-05-27
Hi there,

Great thanks. I followed your instruction and kind of get what we're doing. But the old sources.list still remains. 
Here is the sequence of what I did:

> matjaz@PCPlus:~$ cp /etc/apt/sources.list.d * ~/
cp: omitting directory `/etc/apt/sources.list.d'
cp: omitting directory `amsn_received'
cp: omitting directory `Desktop'
cp: `gtkorphan_0.4.2-2_all.deb' and `/home/matjaz/gtkorphan_0.4.2-2_all.deb' are the same file
cp: omitting directory `MatjazFile'
cp: omitting directory `Other'
cp: `plugin_stack.trace' and `/home/matjaz/plugin_stack.trace' are the same file
cp: `Screenshot-1.png' and `/home/matjaz/Screenshot-1.png' are the same file
cp: `Screenshot-2.png' and `/home/matjaz/Screenshot-2.png' are the same file
cp: `Screenshot-3.png' and `/home/matjaz/Screenshot-3.png' are the same file
cp: `Screenshot.png' and `/home/matjaz/Screenshot.png' are the same file
cp: omitting directory `skype-rec'
cp: `skype-rec-1.0.tar.gz' and `/home/matjaz/skype-rec-1.0.tar.gz' are the same file
cp: `skype-rec.rc' and `/home/matjaz/skype-rec.rc' are the same file
cp: `skype-rec.rc~' and `/home/matjaz/skype-rec.rc~' are the same file
cp: omitting directory `vmware'
cp: `w32codecs_20060611-1plf1_i386.deb' and `/home/matjaz/w32codecs_20060611-1plf1_i386.deb' are the same file
cp: `Wizzairconfirm.png' and `/home/matjaz/Wizzairconfirm.png' are the same file
cp: omitting directory `workspace'
cp: omitting directory `XXX'
matjaz@PCPlus:~$ ls
amsn_received              skype-rec
Desktop                    skype-rec-1.0.tar.gz
gtkorphan_0.4.2-2_all.deb  skype-rec.rc
MatjazFile                 skype-rec.rc~
Other                      vmware
plugin_stack.trace         w32codecs_20060611-1plf1_i386.deb
Screenshot-1.png           Wizzairconfirm.png
Screenshot-2.png           workspace
Screenshot-3.png           XXX
Screenshot.png
matjaz@PCPlus:~$ sudo rm /etc/apt/sources.list.d/ *
Password:
rm: cannot remove `/etc/apt/sources.list.d/': Is a directory
rm: cannot remove `amsn_received': Is a directory
rm: cannot remove `Desktop': Is a directory
rm: cannot remove `MatjazFile': Is a directory
rm: cannot remove `Other': Is a directory
rm: cannot remove `skype-rec': Is a directory
rm: cannot remove `vmware': Is a directory
rm: cannot remove `workspace': Is a directory
rm: cannot remove `XXX': Is a directory
matjaz@PCPlus:~$ ls /etc/apt/sources.list.d
dapper-multiverse.list              dapper-universe.list
dapper-multiverse.list~             dapper-universe.list~
dapper-multiverse.list.distUpgrade  dapper-universe.list.distUpgrade
dapper-multiverse.list.save         dapper-universe.list.save
dapper-multiverse.list.save~        dapper-universe.list.save~
matjaz@PCPlus:~$ 


It looks like it didn't remove them Is it because of this: 
rm: cannot remove `/etc/apt/sources.list.d/': Is a directory  ?


many thanks
M

---

### Post by matjaz_pirnovar on 2007-05-27
Don't really know why dapper repos were not removed..hm

---

### Post by bapoumba on 2007-05-27
Hum. Please go see in your ~/.Trash if there are any files of your own (**ls ~/.Trash**), and from the trash applet (on a panel on your desktop if you have one). I'm very sorry there was a space too many when I typed the rm command. Move back the files to your /home if applicable.

```
sudo rm /etc/apt/sources.list.d/*
ls /etc/apt/sources.list.d
```
removes the dapper files in /etc/sources.list.d and makes sure its empty.
```
sudo aptitude update
```

I'm sending you a PM.

---

### Post by matjaz_pirnovar on 2007-05-28
> **bapoumba said:**
> Hum. Please go see in your ~/.Trash if there are any files of your own (**ls ~/.Trash**), and from the trash applet (on a panel on your desktop if you have one). I'm very sorry there was a space too many when I typed the rm command. Move back the files to your /home if applicable.

```
sudo rm /etc/apt/sources.list.d/*
ls /etc/apt/sources.list.d
```
removes the dapper files in /etc/sources.list.d and makes sure its empty.
```
sudo aptitude update
```

I'm sending you a PM.

Hi there,

Great. This worked.

I get clean sources.list.

See:

> matjaz@PCPlus:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Building tag database... Done      
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_GB [4827B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_GB
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_GB [1573B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_GB
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages
Fetched 6403B in 1s (4198B/s)
Reading package lists... Done


Now I guess it is done?  Should I comment the repos we uncommented before (backports, commercial etc.)?  I'll wait for your confirmation I can upgrade...

Regards,
Matjaz

---

### Post by matjaz_pirnovar on 2007-05-28
Plus I tried first steps of Upgrading to feisty and is going well, no Error 404 IP...  any more (I didn't yet fully upgrade).

My Trash contains some old protected Easy Ubuntu sources list from last year I can't get rid off.. Any advice how to delete it? It doesn't interfere I think, but makes me feel uncomfortable now  ;)

Regards,
M

---

### Post by bapoumba on 2007-05-28
Ok. *relief*

In your first post you state you want to upgrade to feisty.
Now your sources.list is feisty and update works. Which version of ubuntu are you running? :
```
lsb_release -cd
```
Will tell you if you are unsure.
Next step depends on this answer.

If running edgy and wishing to upgrade to feisty:
1- Backup all your personal files. Copy them to a safe place, other than this computer (usb drive, cd, dvd, network server ....) Backup anything precious,  files that you cannot loose. (upgrading is _always_ risky, no matter what)
2- Do you have a separate /home partition? A separate /home will remain unchanged by the upgrade. Backup is just in case something goes wrong. If your /home is not sseparate and on your / (sytem) partition, then your /home will be erased by the upgrade, and started over afresh. Backup is mandatory in that case.

If already running feisty: will be easy.

---

### Post by matjaz_pirnovar on 2007-05-28
Great! Thanks!

I'm using Edgy (6.10).

So I'm going to upgrade in about half an hour. I made backups yes on CD. Don't know if I have "standalone" /home file...

A question: Do I need to comment those backports, commercial and proposed in feisty sources.list as we did before? Or upgrade should take care of it?

Thanks. M

---

### Post by bapoumba on 2007-05-28
Yes, comment them out. Keep only main, restricted, universe, multiverse.
For you /home:
```
~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=671c9026-99b7-4b8c-9456-2c893897de48 [COLOR="Red"]/[/COLOR]               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=36cd4898-7cc2-4bac-b482-fd7fcef827c3 [COLOR="Red"]/home[/COLOR]           ext3    defaults        0       2
# /dev/hda3
UUID=35f61872-a12a-4b97-a938-daf3fdb21b04 none            [COLOR="Red"]swap[/COLOR]    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```
You see here I have a root (/) partition and a /home partition, plus a swap partition.
There are tutorials to move /home on a different partition if you wish to do so:
[http://psychocats.net/ubuntu/separatehome]("http://psychocats.net/ubuntu/separatehome")

To upgrade to feisty:
```
sudo aptitude update
sudo aptitude dist-upgrade
```
Sometimes the dist-upgrade has to be run 2 or 3 times in a row to be complete, untill there is nothing left to dist-upgrade.

---

### Post by matjaz_pirnovar on 2007-05-28
Cool.

Thanks bapoumba for all your help.

Was cool to get so quick and good responses. Long live Ubuntu ;)

Wish me luck with upgrade.
Matjaz

---

### Post by bapoumba on 2007-05-28
I wish you luck. Please report here if you have any question, and if you upgraded successfully too :)

---

### Post by matjaz_pirnovar on 2007-05-29
> **bapoumba said:**
> I wish you luck. Please report here if you have any question, and if you upgraded successfully too :)

Yep. Upgraded successfully via online (approx. 4 h altogether). And my sources.list now looks clean :D (Thank god that dreadful IP Error 404  disappeared)

Have a miriad of questions...but don't present problems at the moment. I will definitely ask/post more...

Cheers.  :)

---

### Post by bapoumba on 2007-05-29
\o/ congratulations!

---

