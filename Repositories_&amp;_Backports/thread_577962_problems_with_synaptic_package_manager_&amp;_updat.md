---
title: "problems with synaptic package manager &amp; update manager &amp; editing sources.list file"
date: 2007-10-16
forum: Repositories &amp; Backports
---

### Post by mrdes on 2007-10-16
hi ...
simply when i try to access any of these i got these errors :
1- synaptic package manager
error=
[COLOR="Red"]E: Malformed line 4 in source list /etc/apt/sources.list (URI)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
[/COLOR]

2- update manager
error=
[COLOR="Red"]Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 4 in source list /etc/apt/sources.list (URI), E:The list of sources could not be read.[/COLOR]

3- editing sources.list :
error=
[COLOR="Red"]Could not open the file /etc/apt/sources.list.
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.[/COLOR]


so , would some one help me with that ?:confused:
thanks
SEE ATTACHMENTS

---

### Post by magicfab on 2007-10-16
It seems your sources.list file was corrupted after you modified it somehow.

1) Open a terminal window - Applications > Accessories > Terminal
2) Open the sources.list file for editing as super-user:
gksudo gedit /etc/sources.list
3) Replace its content with the following:

# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty main restricted 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe multiverse

4) Use the following command to update your packages information:
sudo apt-get update

Come back and let us know what happens.

Cheers,

---

### Post by mrdes on 2007-10-16
[B]thanks ..
[COLOR="Navy"][problem solved][/COLOR][/B]

---

