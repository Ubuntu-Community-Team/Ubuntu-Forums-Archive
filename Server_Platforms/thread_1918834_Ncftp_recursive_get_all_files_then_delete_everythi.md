---
title: "Ncftp recursive get all files then delete everything"
date: 2012-02-01
forum: Server Platforms
---

### Post by psychotix on 2012-02-01
Hi,

I'm using ncftpget to get all the files in a remote ftp directory tree, then delete all the files after they have been downloaded.

```
ncftpget -u username -p lamepass -R -DD ftp://10.0.1.14
```This works great, except it leave all the empty directories intact.  

Does anyone have a simple way of clearing out all these empty remote directories?  with ncftp would be great but, I'd like to hear of any other way.

THanks,

---

### Post by psychotix on 2012-02-02
```

#!/bin/bash

# Script for retrieving all files on a an ftp server then deleting them.
#
# Requires ncftp and stock ftp client.
#
# We have to do some funkyness since there is no easy way of recursively deleting
#   remote directories.  We use ncftp to download all files and delete them on successfull
#   download. This ,however, leaves empty directories.  So we download the empty directory
#   tree to FSTREEDIR to list all directories to delete(we can't trust the download directory
#   because other directories may exist there). Those directories are then passed to the
#   usual ftp client to delete. 

# @todo - store credentials in a file

FTPSERVER=10.0.1.150
DOWNLOADDIR=/tmp/dl
FSTREEDIR=$DOWNLOADDIR/fstree
USERNAME=bart
PASSWORD=dude
DELETEREMOTEFILES=1


if [ $DELETEREMOTEFILES -eq 1 ]
 then
  DELFILESFLAG="-DD"
 else
  DELFILESFLAG=""
fi

echo "Downloading Reports...
"

cd $DOWNLOADDIR
ncftpget -u $USERNAME -p $PASSWORD -R $DELFILESFLAG ftp://$FTPSERVER


# Delete Files after download
if [ $DELETEREMOTEFILES -eq 1 ]
 then
    echo "Deleting Remote Reports...
    "
 
    RMSTRING=""
    
    # if fstree dir exists empty it and recreate it
    if [ ! -d "$FSTREEDIR" ]; then 
      mkdir $FSTREEDIR
    else
      rm -rf $FSTREEDIR/*
    fi

    # Copy remote directory structure to FSTREEDIR
    cd $FSTREEDIR
    ncftpget -u $USERNAME -p $PASSWORD -R $DELFILESFLAG ftp://$FTPSERVER

    # Generate list of directories to delete
    for D in `find $FSTREEDIR -type d| sort -r`
    do
      if [ ! "$D" = "$FSTREEDIR" ]; then
        RMSTRING="$RMSTRING 
        rmdir ${D#$FSTREEDIR/}"
      fi
    done

# Delete remote file structure
ftp -i -n <<EOF
open $FTPSERVER
user $USERNAME $PASSWORD
$RMSTRING
EOF

    # delete old FSTREEDIR
    rm -rf $FSTREEDIR

fi


```

---

