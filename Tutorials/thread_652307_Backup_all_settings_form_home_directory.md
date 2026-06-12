---
title: "Backup all settings form home directory"
date: 2007-12-28
forum: Tutorials
---

### Post by capink on 2007-12-28
I made this little script to backup all the settings stored in my home directory. This script will backup only the settings and will exclude the following:

- Visible Files and directories that don't start with "." (i.e files like music) that are present on the top level of your home directory tree. These files and directories can be listed by typing the command:

```
ls ~
```

- Unecessary files like cache and history. These are defined in the variable exclude_pattern within the script.


**_How to run the script:_**

1. Copy the script below to a file and name it home-bakcup.sh or any name you want.

```
#!/bin/sh

# This script will backup the config files in the home directory to
# a file $backup_file stored in $target


# backup filename
backup_file=backup.tar.gz

# directory where backup.tar.gz will be stored
target=$HOME

# any filename containig any keyword form this variable
# in it's pathname will be excluded
exlude_pattern="cache gnome log recently serverauth thumb xsession-errors snapshot Snapshot tmp Temp temp history History _bak Cache Log gconf trash Trash"

# any filename resembling an exact keyword form this variable
# will be excluded
exclude_name=`ls $HOME`

# define more files to backup
#include="/etc/fstab /etc/apt/sources.list /etc/X11/xorg.conf /etc/resolve.conf /etc/apt/sources.list"

tar cvzp --exclude=*`echo $exlude_pattern | sed 's/ /* --exclude=*/g'` --exclude=`echo $exclude_name | sed 's/ / --exclude=/g'` --exclude=${backup_file} -f ${target}/backup.tar.gz $HOME $include

```


2. Make the script excutable:

```
chmod u+x /path/to/home-backup.sh
```

3. To backup your settings type:

```
/path/to/home-backup.sh
```

4. To restore you settings type:

```
sudo tar xvpf ~/backup.tar.gz  --same-owner -C /
```



**_Notes:_**

- This script primarily saves the settings in the user's home directory. However if you want to backup some other files like fstab or xorg.conf, you can do so by uncommenting the include variable and adding the full name of the file you want to backup:

```
include="/etc/fstab /etc/apt/sources.list /etc/X11/xorg.conf /etc/resolve.conf /etc/apt/sources.list"
```

Or if you want to backup the entire /etc :

```
include="/etc"
```

- The contents of the include variable must be enclosed within double quotes.

- If for some reason any of the files on your home directory is not readable (e.g. owned by root), the script may fail to complete unless you run it with sudo:

```
sudo /path/to/home-backup.sh
```

- When restoring we must use sudo if we backed up any of the file in /etc

---

### Post by yo_bhan on 2011-10-24
wow great...
maybe sometimes very usesfull

---

### Post by lisati on 2011-10-24
Did anyone notice when this thread was created?

---

