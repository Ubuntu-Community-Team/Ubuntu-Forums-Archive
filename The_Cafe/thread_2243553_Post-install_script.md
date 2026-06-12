---
title: "Post-install script"
date: 2014-09-09
forum: The Cafe
---

### Post by Dragonbite on 2014-09-09
I've put together a script to install and apply some of the settings I find I usually do after each Linux installation in one form or another.

The idea is that after installing Ubuntu from a Live DVD/USB media, I would run this script to install additional applications, clean up the shopping lens and etc.

I wanted to put this out to find out if you have any neat code snippits you regularly use, or if I have something wrong with my code, to find out about it before I run it next, or to inspire anybody to put together a shell script for the next time they install Ubuntu.

We'll say the file name is **customize_for_me.sh** and after copying either through the Internet or sneakernet, and have run ```
sudo chmod +x customize_for_me.sh
``` and is run by ```
sudo ./customize_for_me.sh
```

So, the code I have for this script is below.  Interested in your thoughts and input.
```

#!/bin/bash

	###########################################################
	# The purpose of this script is to automate some of the   #
	# regular procedures performed when first setting up an   #
	# Ubuntu desktop.                                         #
	# This script assumes that the full Ubuntu desktop has    #
	# been installed and the script is run from a sudo        #
	# account.                                                #
	#.........................................................#
	# This script assumes that it has been refreshed and      #
	# updated fully before starting.                          #
	###########################################################

#.......................................................
# Add Repositories
#.......................................................

# WebUpD8te's Java repository

sudo add-apt-repository ppa:webupd8team/java

# Enable partner repositories

sudo add-apt-repository "deb http://archive.canonical.com/ $(lsb_release -sc) partner"

#.......................................................
# 	Refresh repositories
#.......................................................

sudo apt-get update

#.......................................................
# 	Install applications
#.......................................................

sudo apt-get install pithos kpat geary leafpad skype virtualbox wallch 

#.......................................................
# 	Install Java (auto-accept Oracle license)
#.......................................................

echo oracle-java7-installer shared/accepted-oracle-license-v1-1 select true | sudo /usr/bin/debconf-set-selections

#.......................................................
# 	Download Minecraft
#.......................................................

cd ~/
wget https://s3.amazonaws.com/Minecraft.Download/launcher/Minecraft.jar

#.......................................................
#   Disable shopping lense
#.......................................................

gsettings set com.canonical.Unity.Lenses disabled-scopes "['more_suggestions-amazon.scope', 'more_suggestions-u1ms.scope', 'more_suggestions-populartracks.scope', 'music-musicstore.scope', 'more_suggestions-ebay.scope', 'more_suggestions-ubuntushop.scope', 'more_suggestions-skimlinks.scope']"


#done.

```

---

### Post by user1397 on 2014-09-09
I always run these commands after my initial setup, if anything out of paranoia (hehe)

```
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get autoclean
```never really understood the difference between clean and autoclean..

---

### Post by Dragonbite on 2014-09-10
> **ubuntuman001 said:**
> I always run these commands after my initial setup, if anything out of paranoia (hehe)

```
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get autoclean
```never really understood the difference between clean and autoclean..

Are those to clear out any left over "crud" from installing?

---

### Post by user1397 on 2014-09-10
from the man pages:

```
[COLOR=#000000][I]clean 
clean clears out the local repository of retrieved package files.[/I][/COLOR]
[COLOR=#000000]*It removes everything but the lock file from*[/COLOR]
[COLOR=#000000]*/var/cache/apt/archives/ and /var/cache/apt/archives/partial/. When*[/COLOR]
[COLOR=#000000]*APT is used as a dselect(1) method, clean is run automatically.*[/COLOR]
[COLOR=#000000]*Those who do not use dselect will likely want to run apt-get clean*[/COLOR]
[COLOR=#000000]*from time to time to free up disk space.*[/COLOR]

[COLOR=#000000]*autoclean*[/COLOR]
[COLOR=#000000]*Like clean, autoclean clears out the local repository of retrieved*[/COLOR]
[COLOR=#000000]*package files. The difference is that it only removes package files*[/COLOR]
[COLOR=#000000]*that can no longer be downloaded, and are largely useless. This*[/COLOR]
[COLOR=#000000]*allows a cache to be maintained over a long period without it*[/COLOR]
[COLOR=#000000]*growing out of control. The configuration option*[/COLOR]
[COLOR=#000000]*APT::Clean-Installed will prevent installed packages from being*[/COLOR]
[COLOR=#000000]*erased if it is set to off.*[/COLOR]

[COLOR=#000000]*autoremove*[/COLOR]
[COLOR=#000000]*autoremove is used to remove packages that were automatically*[/COLOR]
[COLOR=#000000]*installed to satisfy dependencies for some package and that are no*[/COLOR]
[COLOR=#000000]*more needed.
```*[/COLOR]

---

### Post by frankmorris2 on 2014-09-12
Hello,

I would make a suggestion for the repositories: add the official VirtualBox repository to install the latest and updated version.

The instructions are located here: [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

Also, I would enjoy this kind of script on github (comments, issues, wiki, pull requests, all managed together).

Just my 2 cents.

Have a nice day.

---

