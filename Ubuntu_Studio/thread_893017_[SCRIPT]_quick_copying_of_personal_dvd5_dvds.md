---
title: "[SCRIPT] quick copying of personal dvd5 dvds"
date: 2008-08-17
forum: Ubuntu Studio
---

### Post by Alteran on 2008-08-17
I made a script recently that makes backing up your movies and or games for PERSONAL USE! quick and easy.
I wasn't sure where to put this.
requires dd and growisofs
```

#!/bin/bash

# if no path is given exit
if [ `expr length "$1"` == 0 ]; then
echo -e "You have not given a filename.\nPlease use copy-dvd path/to/file.iso"
exit
else
 echo -e "Copying to $1... \n "

 #copy dvd to $1
 #change /dev/scd1 to your dvd drive
 dd if=/dev/scd1 of=$1 

echo ""
echo "####################"
echo "# Copying finished #"
echo "####################"

#burn?

echo -e "Burn $1 to dvd? \n <yes|no>" 
read BURN

# burn the iso after its finished ripping
if [ $BURN = yes ]; then
# change /dev/scd0 to your dvd burner
growisofs -dvd-compat -Z /dev/scd0=$1

echo ""
echo "################"
echo "# Burning Done #"
echo "################"

else
echo "###############"
echo "# Didn't Burn #"
echo "###############"
echo "Your iso $1 is ready"
exit
fi

#remove iso

echo -e "Remove $1? \n <yes|no>" 
read REMOVE

if [ $REMOVE = yes ]; then
 rm -rf $1
echo "$1 was deleted"
else 
echo "$1 was NOT deleted" 
 fi
fi

```

---

### Post by jpeddicord on 2008-08-22
Moved out of Tutorials & Tips as it is a script, not necessarily a tutorial.

---

### Post by Alteran on 2008-08-22
Thanks =)

---

