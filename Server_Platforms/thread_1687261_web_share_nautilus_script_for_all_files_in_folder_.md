---
title: "web share nautilus script for all files in folder only needs zenity not working"
date: 2011-02-13
forum: Server Platforms
---

### Post by swimfish on 2011-02-13
i have this folder web share script.  it gets past all checks but when it comes to advancing past making the files in a dir publishable over webshare (zenity only requirement its a nautilus-script)  it simply goes back and forth with only option to cancel, nothing ever gets published to the web.  [http://pastebin.com/iPXqhM2w](http://pastebin.com/iPXqhM2w)

i would absolutely love to get this to work as i really only need is a dropbox replacement.  

for those simple things that mean so much, any improvements that can be made to the script, like it hosting the folder on port 80, i  can only offer through snail mail a 4GB flash drive with Ubuntu LTS or 10.10 either 386 or amd64 desktop edition with the rest of the extraneous space as persistance.  or i can offer a bluetooth dongle (if you are gracious i'd rather part with the dongle ;)  anyway, can anyone get this script up and running ?

thank you

---

### Post by swimfish on 2011-02-18
i'd like to bump this in the hopes someone can solve it -- its such a simple script, and it offers to share one directory under port 8080 (originally 8000) i tweaked it so many people would love to have this nautilus-script working, some people, do not have a need for full blown apache2, much less, a lamp setup. 

thank you

share a directory on 8080 is what that does

```

#!/bin/bash 
#Title=share-http-here
#Title[fr]=partage-http-ici

#==============================================================================
#                                 share-http-here
#
#  author  : SLK
#  version : v2010122001
#  license : Distributed under the terms of GNU GPL version 2 or later
#
#==============================================================================
#
#  description :
#    nautilus-script : shares the current (or selected) dir with http on
#    port 8080
#
#  informations :
#    - a script for use (only) with Nautilus. 
#    - to use, copy to your ${HOME}/.gnome2/nautilus-scripts/ directory.
#
#  WARNINGS :
#    - this script must be executable.
#    - package "zenity" must be installed
#
#  THANKS :
#    http://blog.rom1v.com/2009/12/creer-un-serveur-http-en-10-secondes/
#
#==============================================================================

#==============================================================================
#                                                                     CONSTANTS

# 0 or 1  - 1: doesn't share but displays a message
DRY_RUN=0

ETH='eth0'

#------>                                       some labels used for zenity [en]
z_title='share this folder with http on :8080'
z_no_ip="ip not found for interface ${ETH}\nEXIT"
z_port_used="port 8080 already used\nEXIT"
z_confirm_share="do you want to share the folder"
z_from="it will be accessible from a browser at:"
z_sharing="sharing"
z_err_gvfs="cannot acces to directory - check gvfs\nEXIT"
z_err_uri="cannot access to directory - uri not known\nEXIT"

#------>                                       some labels used for zenity [fr]
#z_title='partager ce repertoire en http sur :8000'
#z_no_ip="ip non trouvee pour l'interface ${ETH}\nEXIT"
#z_port_used="le port :8000 est deja utilise\nEXIT"
#z_confirm_share="partager le repertoire"
#z_from="il sera accessible depuis un navigateur a :"
#z_sharing="partage"
#z_err_gvfs="impossible d'acceder au repertoire - verifiez gvfs\nEXIT"
#z_err_uri="impossible d'acceder au repertoire - uri inconnue\nEXIT"

#==============================================================================
#                                                                INIT VARIABLES

# may depends of your system : (current settings for debian, ubuntu)

GVFSMOUNT='/usr/bin/gvfs-mount'
GREP='/bin/grep'
IFCONFIG='/sbin/ifconfig'
KILL='/bin/kill'
LSOF='/usr/bin/lsof'
PERL='/usr/bin/perl'
PYTHON='/usr/bin/python2.5'
ZENITY='/usr/bin/zenity'

#==============================================================================
#                                                                          MAIN


# retrieve the first object selected or the current uri
if [ "$NAUTILUS_SCRIPT_SELECTED_URIS" == "" ] ; then
    uri_first_object=`echo -e "$NAUTILUS_SCRIPT_CURRENT_URI" \
      | $PERL -ne 'print;exit'`
else
    uri_first_object=`echo -e "$NAUTILUS_SCRIPT_SELECTED_URIS" \
      | $PERL -ne 'print;exit'`
fi

type_uri=`echo "$uri_first_object" \
  | $PERL -pe 's~^(.+?)://.+$~$1~'`

# try to get the full path of the uri (local path or gvfs mount ?)
if [ $type_uri == "file" ] ; then
    
    filepath_object=`echo "$uri_first_object" \
      | $PERL -pe '
        s~^file://~~;
        s~%([0-9A-Fa-f]{2})~chr(hex($1))~eg'`
    
elif [ $type_uri == "smb" -o $type_uri == "sftp" ] ; then
    if [ -x $GVFSMOUNT ] ; then
        
        # host (and share for smb) are matching a directory in ~/.gvfs/
        
        host_share_uri=`echo "$uri_first_object" \
          | $PERL -pe '
            s~^(smb://.+?/.+?/).*$~$1~;
            s~^(sftp://.+?/).*$~$1~;
            '`
        
        path_gvfs=`${GVFSMOUNT} -l  \
          | $GREP "$host_share_uri" \
          | $PERL -ne 'print/^.+?:\s(.+?)\s->.+$/'`
        
        # now let's create the local path
        path_uri=`echo "$uri_first_object" \
          | $PERL -pe '
            s~^smb://.+?/.+?/~~;
            s~^sftp://.+?/~~;
            s~%([0-9A-Fa-f]{2})~chr(hex($1))~eg'`
        
        filepath_object="${HOME}/.gvfs/${path_gvfs}/${path_uri}"
        
    else
        $ZENITY --error --title "$z_title" --width "320" \
          --text="$z_err_gvfs"
        
        exit 1
    fi
else
    $ZENITY --error --title "$z_title" --width "320" \
      --text="$z_err_uri"
    
    exit 1
fi


# try to retrieve ip address
ip=`$IFCONFIG $ETH 2>/dev/null \
  | $PERL -ne 'print /add?r:(\S+)/'`
[ "$ip" == "" ] && { 
    $ZENITY --error --title "$z_title" --width "320" \
      --text="$z_no_ip"
    
    exit 1
}

### CHECK : is port 8000 free ?

$LSOF -i :8080 >/dev/null 2>&1
[ "$?" == "0" ] && { 
    $ZENITY --error --title "$z_title" --width "320" \
      --text="$z_port_used"
    
    exit 1
}


# if object is file : share his directory
if [ -d "$filepath_object" ] ; then
    dirpath_share="$filepath_object"
else
    dirpath_share=`echo "$filepath_object" \
      | $PERL -pe 's|[^/]+$||'`
fi


$ZENITY --question --title "$z_title" --width "320" \
  --text="$z_confirm_share 
\"$dirpath_share\"
$z_from 
\"http://$ip:8080\"" \
  || exit 0


### DRY RUN : noop

[ $DRY_RUN -eq 1 ] && {
    $ZENITY --info --title "$z_title" --width "320" \
      --text="DRY RUN
cmd: $PYTHON -m SimpleHTTPServer
sharing $dirpath_share"
    exit 0
}


### GO : let's share

cd $dirpath_share
$PYTHON -m SimpleHTTPServer &
pid=$!
$ZENITY --progress --title "$z_title" --width "320" \
  --text "$z_sharing \"$dirpath_share\" - \"http://$ip:8080\"" --pulsate --auto-close
$KILL $pid


exit 0


### EOF



```

i do notice that $PYTHON -m SimpleHTTPServer &
pid=$!

is in the script and i have yet to ever been instructed to install anything but zenity.  
thanks !

---

### Post by swimfish on 2011-02-18
something is ok about part of the script 

bobcat@oceana:~/scripts$ sudo python -m SimpleHTTPServer 80
[sudo] password for bobcat: 
Serving HTTP on 0.0.0.0 port 80 ...
localhost.localdomain - - [18/Feb/2011 10:01:28] code 404, message File not found
localhost.localdomain - - [18/Feb/2011 10:01:28] "GET /scrape?info_hash=%B0%C9h%06%90%D0%929%DD%FC%0ER%95%B8%7F%C95%C5W%8E HTTP/1.1" 404 -

---

