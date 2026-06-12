---
title: "cp with progress bar in a terminal script"
date: 2006-12-11
forum: Tutorials
---

### Post by pabix on 2006-12-11
Hi all!

I've just finished writing a small Bash script to watch with a progress gauge the **copy of a single file**. (name it *gcp*)

**[COLOR="Red"]Use it at your own risk[/COLOR]**

See this console extract:

```

$ gcp pres.tex pres.tex2
0                                                       100%
|===========================================================| Done.

```

Features:
[LIST]
[*]detection of terminal width
[*]if second argument is a directory, copies to the directory
[*]customization of gauge refresh rate
[*]customization of width of gauge
[/LIST]

I leave it here as attachment w/o warranty. [COLOR="Red"]Most recent version will be on [http://forum.ubuntu-fr.org/viewtopic.php?id=82447]("http://forum.ubuntu-fr.org/viewtopic.php?id=82447").[/COLOR]

Enjoy!

Benoit

EDIT. 12.11.2006 - 18.36 protection for file names containing spaces.

---

### Post by brennydoogles on 2007-08-15
How would i edit this for use with the dd command if i wanted to?? Here is the script that I would like to integrate it into if at all possible.....

---

### Post by oldsquaw on 2009-02-14
I can't seem to get the progress bar to run.  Any thoughts?

---

### Post by mic159 on 2009-05-06
I have made some bugfixes and other alterations.

Bigfix: Was backspacing the whole line, but when writing the bar, it would only write up to the end of the current progress. Causing it to go back onto previous line in ssh sessions. Solution: write whole line every refresh.

Optimization: Only update line when there is a change in the number of '=' to write.

Feature: Returns '1' when an error occurs, '0' normally.


Surely there must be another way to see if cp is still running other than it looking for that file? can you do it with PIDs?
Possibly even grep the output of the current processes running to see if its still there.

Also, there needs to be handling for Control-C, which stops cp.
Because at the moment, cp still keeps going in the background, even if you Control-C.

Other than that, Nice script dude :)

```
#!/bin/bash
#                           __    _            __            
#   ____ __________ _____  / /_  (_)________ _/ /  _________ 
#  / __ `/ ___/ __ `/ __ \/ __ \/ / ___/ __ `/ /  / ___/ __ \
# / /_/ / /  / /_/ / /_/ / / / / / /__/ /_/ / /  / /__/ /_/ /
# \__, /_/   \__,_/ .___/_/ /_/_/\___/\__,_/_/   \___/ .___/ 
#/____/          /_/                                /_/      
                                        
# by Pabix (mortgat ... GMAIL ... com)

# BSD License
#
# Redistribution and use in source and binary forms, with or
#   without modification, are permitted provided that the following
#   conditions are met:
#
# *  Redistributions of source code must retain the above
#    copyright notice, this list of conditions and the following
#    disclaimer.
#
# *  Redistributions in binary form must reproduce the above
#    copyright notice, this list of conditions and the following
#    disclaimer in the documentation and/or other materials
#    provided with the distribution.
#
# THIS SOFTWARE IS PROVIDED BY THE AUTHOR ``AS IS'' AND ANY
# EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO,
# THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A
# PARTICULAR PURPOSE ARE DISCLAIMED.  IN NO EVENT SHALL THE AUTHOR
# BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL,
# EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED
# TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE,
# DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND
# ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT
# LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING
# IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF
# THE POSSIBILITY OF SUCH DAMAGE.

DEBUG=0

#       _       _           _     
#  __ _| | ___ | |__   __ _| |___ 
# / _` | |/ _ \| '_ \ / _` | / __|
#| (_| | | (_) | |_) | (_| | \__ \
# \__, |_|\___/|_.__/ \__,_|_|___/
# |___/                           

# Success message
FINISHED="[Done]"

# Message when copy aborted
FINISHEDERROR="[Fail]"

# Calculates number of available columns on the terminal
COLUMNS=$( stty -a | head -n 1 | awk '{print $7}' | rev | cut -b 2- | rev )

# Calculates width of gauge using last value
COLS=$((${COLUMNS} -${#FINISHED} - 5))

# Default refresh delay
DELAY=0.1

# Echo ($2), repeated ($1) times
function multiecho(){
    debug $1 columns times $2
    for i in $(seq 1 $1)
    do
        echo -n -e "$2"
    done
}

# Display help
function usage(){
    cat << EOF
    gcp [options] source destination
        copy source file to destination file using a graphical gauge.
                Only ONE source file is allowed at a time.

        options:

        -c (n) : use (n) columns to display
        -d     : use debug options
        -h     : display help
        -r (t) : use (t) seconds refresh delay
EOF
}

#             _   _                 
#  ___  _ __ | |_(_) ___  _ __  ___ 
# / _ \| '_ \| __| |/ _ \| '_ \/ __|
#| (_) | |_) | |_| | (_) | | | \__ \
# \___/| .__/ \__|_|\___/|_| |_|___/
#      |_|                          

# Parsing options
while getopts "c:dr:h" option
do
    case $option in
        c)
        COLS=$OPTARG
        ;;
        d)
        DEBUG=1
        ;;
        r)
        DELAY=$OPTARG
        ;;
        h)
        usage
        exit 0
        ;;
        *)
        ;;
    esac
done
shift $((OPTIND-1));

# Checks number of options correct
if [[ $# -ne 2 ]]
then
    usage
    exit 1
fi

sourcefile=$1
if [[ ! -e "$sourcefile" ]]
then
    usage
    exit 1
fi
destinationfile=$2

# Checking that destination is a regular file.
if [[ -d "$destinationfile" ]]
then
    destinationfile=${destinationfile%\/}"/"$(basename ${sourcefile})    
fi

# Warning if destination exists
if [[ -e "$destinationfile" ]]
then
    echo WARNING: $destinationfile exists!
fi
shift 2

#     _      _                 
#  __| | ___| |__  _   _  __ _ 
# / _` |/ _ \ '_ \| | | |/ _` |
#| (_| |  __/ |_) | |_| | (_| |
# \__,_|\___|_.__/ \__,_|\__, |
#                        |___/ 

DEBUGFILE=`tempfile`
if [[ "$DEBUG" = "1" ]]
then
    function debug(){
        echo $@ >> $DEBUGFILE
    }
else
    function debug(){
        :
    }
fi

debug $COLS columns
debug source file : $sourcefile
debug destination : $destinationfile


#     _ _           _             
#  __| (_)___ _ __ | | __ _ _   _ 
# / _` | / __| '_ \| |/ _` | | | |
#| (_| | \__ \ |_) | | (_| | |_| |
# \__,_|_|___/ .__/|_|\__,_|\__, |
#            |_|            |___/ 

# Backspace
RET_ARR="\010"
# sufficient backspacing to go back
KILLLINE=${RET_ARR}${RET_ARR}
for i in $(seq 1 $COLS)
do
    KILLLINE=${KILLLINE}${RET_ARR}
done

# Rule
echo -n "0"
multiecho $(($COLS-4)) " "
echo '100%' ; 

# Gauge
echo -n "|"
multiecho $COLS " "
echo -n "|"

#                 _       
# _ __ ___   __ _(_)_ __  
#| '_ ` _ \ / _` | | '_ \ 
#| | | | | | (_| | | | | |
#|_| |_| |_|\__,_|_|_| |_|
#                         

# Indicator of working cp
INDFILE=`tempfile`

# Invoking cp
(nice cp "$sourcefile" "$destinationfile" ; rm $INDFILE) &

# Grabbing source size
SOURCEFILESIZE=$(($(ls -o "$sourcefile" | awk '{print $4}') + 1))
DESTFILESIZE=0
debug source file size : $SOURCEFILESIZE
LASTPERCENT=0

# MAIN LOOP
while [[ -e "$INDFILE" ]]
do
    sleep $DELAY

    # Grabbing destination size
    DESTFILESIZE=$(($(ls -o "$destinationfile" | awk '{print $4}') + 1))
    PERCENTAGE=$(($COLS * $DESTFILESIZE / $SOURCEFILESIZE ))
    REST=$(($COLS - $PERCENTAGE))

    # Only update when changed
    if [[ $LASTPERCENT -ne $PERCENTAGE ]]
    then

        # Displaying gauge
        echo -e -n $KILLLINE"|"
        multiecho $PERCENTAGE "="
        multiecho $REST " "
        echo -n "|"

        LASTPERCENT=$PERCENTAGE
    fi
done

#           _ _   
#  _____  _(_) |_ 
# / _ \ \/ / | __|
#|  __/>  <| | |_ 
# \___/_/\_\_|\__|
#                 

# Checks sizes of destination and source
DESTFILESIZE=$(($(ls -o "$destinationfile" | awk '{print $4}') + 1))
if [[ "$DESTFILESIZE" != "$SOURCEFILESIZE" ]]
then
    echo -e "\033[30m!!! $FINISHEDERROR.\033[0m"
else
    echo " $FINISHED"
fi

# Debugfile is empty if no debug option specified
cat $DEBUGFILE
rm $DEBUGFILE

if [[ "$DESTFILESIZE" != "$SOURCEFILESIZE" ]]
then
    exit 1
else
    exit 0
fi

```

---

### Post by frenchn00b on 2010-01-23
thanks for the nice script.

But if " cp " is running into the backgroup while copying ... that's not so good. I would rather not use it. We shall target a perfect solution.

There is alternative using rsync. Have you checked in that direction ? with rsync this one ctrl c works


also:
[http://chris-lamb.co.uk/2008/01/24/can-you-get-cp-to-give-a-progress-bar-like-wget/](http://chris-lamb.co.uk/2008/01/24/can-you-get-cp-to-give-a-progress-bar-like-wget/)

---

### Post by ibuclaw on 2010-01-23
> **frenchn00b said:**
> thanks for the nice script.

But if " cp " is running into the backgroup while copying ... That's not so good. I would rather not use it. We shall target a perfect solution.

There is alternative using rsync. Have you checked in that direction ? With rsync this one ctrl c works


also:
[http://chris-lamb.co.uk/2008/01/24/can-you-get-cp-to-give-a-progress-bar-like-wget/](http://chris-lamb.co.uk/2008/01/24/can-you-get-cp-to-give-a-progress-bar-like-wget/)

+1

---

### Post by shane2peru on 2010-01-29
I'm pretty surprised so ingenuitive person hasn't perfected this.  Seems like as old as cli is, this would be normal. :)  Apparently it is tougher than it looks.  I would love to see something like this.

Shane

---

### Post by h6w on 2010-04-17
> Bigfix: Was backspacing the whole line, but when writing the bar, it would only write up to the end of the current progress. Causing it to go back onto previous line in ssh sessions. Solution: write whole line every refresh.


The problem with this approach is that programs like "watch" will filter out the backspaces, and the result is that you will end up with =s all over the screen.

This is only important if you're using gcp repeatedly in a script and then "watch"ing it, tho.

---

### Post by cadogan281 on 2010-07-28
does anyone have a finished version of this script?i tried to copy and past the new version in a .sh file and added the right permissions,but when click the "run in terminal" ,the terminal window just closes.i also tried to run it from the terminal window,but that didnt work.iam a newb to making scripts,please help.

---

### Post by nosebreaker on 2011-01-06
I second the rsync option.  For me I just did:
user@ubuntu:/home/user$ sudo rsync --progress *.avi /home/user2

And it copies all .avi files from /home/user to /home/user2 (sudo is needed for me since user doesn't have permissions to user2's home directory, it might not be needed in your situation).

That cp script only does one file at a time, rsync will do multiple files.

---

### Post by shane2peru on 2011-01-06
> **nosebreaker said:**
> I second the rsync option.  For me I just did:
user@ubuntu:/home/user$ sudo rsync --progress *.avi /home/user2

And it copies all .avi files from /home/user to /home/user2 (sudo is needed for me since user doesn't have permissions to user2's home directory, it might not be needed in your situation).

That cp script only does one file at a time, rsync will do multiple files.

True but rsync carries lots of permissions with it I believe.  So copying that way is ok, but you are going to have to go back and do some clean up to make sure permissions/ownership are correct.  If you do a ```
ls -l /home/user2/*.avi 
```  They are all owned by user1 or possibly root.  They may or may not be accessible to user2 depending on permissions.  They may even be owned by root since sudo was used.  So you will have to go back and ```
sudo chown user2:user2 /home/user2/*.avi 
``` to make sure user2 owns them, can play them and delete them.  Otherwise not a bad option.

Shane

---

### Post by poiuz on 2011-07-12
No, rsync is one hell of a tool, but it only does what it is told to. So permissions and ownerships are not preserved when the corresponding options are not set.

For example ```
rsync -pgo src dst
``` does preserve permissions, group and owner, but ```
rsync --progress src dst
``` does not.

---

### Post by DanCar on 2012-02-18
Don't forget the -r switch on rsync for recursive.
-v for verbose.

---

### Post by oldos2er on 2012-02-18
Poor old thread just wants to sleep. Closed.

---

