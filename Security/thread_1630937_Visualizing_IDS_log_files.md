---
title: "Visualizing IDS log files"
date: 2010-11-25
forum: Security
---

### Post by emiller12345 on 2010-11-25
This is a neat little script that I whipped up to hopefully help in the viewing of IDS data.  Just load in a log file and it will parse it and create a nice picture of the data over a 24 hour period.  Sequential port scans will show up nicely as dotted lines on an angle, even if they take an exceptionally long time. This plots port number verses time.

I'm posting this in hopes that it might be useful to someone, but its still a beta and may have problems.

```
#!/bin/bash
# lightstorm-time-port version 0.1
# Used to parse a log file to visualize ip stats
#     usage ./lightstorm-time-port -f logfile.log
#
# logfile must already be in format:
# 0830:192.168.1.100:80:tcp
# 2214:91.189.90.40:443:tcp
# 1301:208.67.222.220:53:udp
# 2214:91.189.90.40::icmp
# ...
# 
#Copyright (C) 2010  by emi11er12345
#
#This program is free software; you can redistribute it and/or
#modify it under the terms of the GNU General Public License
#as published by the Free Software Foundation; either version 2
#of the License, or (at your option) any later version.
#
#This program is distributed in the hope that it will be useful,
#but WITHOUT ANY WARRANTY; without even the implied warranty of
#MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#GNU General Public License for more details.
#
#You should have received a copy of the GNU General Public License
#along with this program; if not, write to the Free Software
#Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301, USA.
REDFG="\e[0;31m"
BLUEFG="\e[0;34m"
GREENFG="\e[0;32m"
YELLOWFG="\e[1;33m"
WHITEFG="\e[1;37m"
BLACKFG="\e[0;30m"
DARKGRAYFG="\e[1;30"
LIGHTBLUEFG="\e[1;34m"
LIGHTGREENFG="\e[1;32m"
CYANFG="\e[0;36m"
LIGHTCYANFG="\e[1;36m"
LIGHTREDFG="\e[1;31m"
PURPLEFG="\e[0;35m"
LIGHTPURPLEFG="\e[1;35m"
BROWNFG="\e[0;33m"
LIGHTGRAYFG="\e[0;37m"
RESET="\e[0m"

REDCIRCLES=""
BLUECIRCLES=""
YELLOWCIRCLES=""
FILE=""

usage()
{
    echo -e "$REDFG""Usage: $0 [args]
   -h        Help Message
   -f FILE   Log file to parse (Must be in format \"HHMM:xxx.xxx.xxx.xxx:port:proto\")
             $RESET""i.e.\n             "$WHITEFG"1135"$BROWNFG":"$LIGHTGRAYFG"192.168.1.100"$BROWNFG":"$CYANFG"80"$BROWNFG":"$GREENFG"tcp""$RESET"
}

if [ $EUID -eq 0 ]; then
    echo -e "$REDFG""Don't run this as root silly! It's not needed.""$RESET" 1>&2
    exit 1
fi

while getopts “f:” OPTION
do
    case $OPTION in
        f)
                 FILE=$OPTARG
            ;;
        ?|*)
            usage
            exit 1
            ;;
    esac
done

if [ -z "$FILE" ]; then
    usage
    exit 1    
fi 

if [ ! -e $FILE ]; then
    echo -e "$REDFG""Error File does not exist.""$RESET" 1>&2
    usage
    exit 1
fi

if [ ! -f $FILE ]; then
    echo -e "$REDFG""Error File is not a regular file.""$RESET" 1>&2
    usage
    exit 1
fi

INCOMING="$(cat $FILE)"


cir(){
    #ASSERT correct time format
    if [ "${#1}" -ne 4 ]; then
        echo -e "$REDFG""ERR: time format""$RESET" 1>&2
        exit 1
    fi

    s=$1
    MINUTE=${s#${s%?}}
    s=${s%?}
    MINUTE=${s#${s%?}}$MINUTE
    if [ $MINUTE -gt 59 ]; then
        TMP=""
        continue;
    fi
    s=${s%?}
    HOUR=${s#${s%?}}
    s=${s%?}
    HOUR=${s#${s%?}}$HOUR
    if [ $HOUR -gt 23 ]; then
        TMP=""
        continue;
    fi

    TIME=$(echo "scale=0; ($HOUR*100 + ($MINUTE*100/60))*812/2400" | bc -l)
    PORT=$(echo "scale=0; $2*388/65535" | bc -l)
    TMP="circle $TIME,$PORT $TIME,$(($PORT+1)) "
}

GREYLINES="line 66,0 66,390 line 132,0 132,390 line 198,0 198,390 line 264,0 264,390 \
line 330,0 330,390 line 396,0 396,390 line 462,0 462,390 line 528,0 528,390 \
line 594,0 594,390 line 660,0 660,390 line 726,0 726,390"


for i in $INCOMING; do
    if [ -n "$(echo $i | grep tcp )" ]; then
        #ASSERT correct time format
        TIME=$(echo $i | awk -F: '{print $1}')
        if [ "${#TIME}" -eq 1 ]; then
            TIME="000$TIME"
        fi
        if [ "${#TIME}" -eq 2 ]; then
            TIME="00$TIME"
        fi
        if [ "${#TIME}" -eq 3 ]; then
            TIME="0$TIME"
        fi
        if [ "${#TIME}" -ne 4 ]; then
            continue;
        fi
        PORT=$(echo $i | awk -F: '{print $3}')
        echo -e "$WHITEFG$TIME$BROWNFG:$LIGHTGRAYFG$(echo $i | awk -F: '{print $2}')$BROWNFG:$GREENFG$(echo $i | awk -F: '{print $3}')    $REDFG""tcp$RESET";
        cir $TIME $PORT
        REDCIRCLES=$REDCIRCLES$TMP
    fi
    if [ -n "$(echo $i | grep udp )" ]; then
        #ASSERT correct time format
        TIME=$(echo $i | awk -F: '{print $1}')
        if [ "${#TIME}" -eq 1 ]; then
            TIME="000$TIME"
        fi
        if [ "${#TIME}" -eq 2 ]; then
            TIME="00$TIME"
        fi
        if [ "${#TIME}" -eq 3 ]; then
            TIME="0$TIME"
        fi
        if [ "${#TIME}" -ne 4 ]; then
            continue;
        fi
        PORT=$(echo $i | awk -F: '{print $3}')
        echo -e "$WHITEFG$TIME$BROWNFG:$LIGHTGRAYFG$(echo $i | awk -F: '{print $2}')$BROWNFG:$GREENFG$(echo $i | awk -F: '{print $3}')    $BLUEFG""udp$RESET";
        cir $TIME $PORT
        BLUECIRCLES=$BLUECIRCLES$TMP
    fi
    if [ -n "$(echo $i | grep icmp )" ]; then
        #ASSERT correct time format
        TIME=$(echo $i | awk -F: '{print $1}')
        if [ "${#TIME}" -eq 1 ]; then
            TIME="000$TIME"
        fi
        if [ "${#TIME}" -eq 2 ]; then
            TIME="00$TIME"
        fi
        if [ "${#TIME}" -eq 3 ]; then
            TIME="0$TIME"
        fi
        if [ "${#TIME}" -ne 4 ]; then
            continue;
        fi

        echo -e "$WHITEFG$TIME$BROWNFG:$LIGHTGRAYFG$(echo $i | awk -F: '{print $2}')$BROWNFG    $YELLOWFG""icmp$RESET";
        cir $TIME 32768
        YELLOWCIRCLES=$YELLOWCIRCLES$TMP
    fi
done

#echo -e "$REDFG""convert -size 800x390 xc:black -fill grey5 -draw \"$GREYLINES\" -fill red -draw \"$REDCIRCLES\" -fill blue -draw \"$BLUECIRCLES\" -fill yellow -draw \"$YELLOWCIRCLES\" test.png && evince test.png && rm test.png""$RESET"

convert -size 800x390 xc:black -fill grey5 -draw "$GREYLINES" -fill red -draw "$REDCIRCLES" \
-fill blue -draw "$BLUECIRCLES" -fill yellow -draw "$YELLOWCIRCLES" test.png && evince test.png && rm test.png

```

---

### Post by Kinstonian on 2010-11-26
How about a link to the image it creates?  You might want to post it to [http://secviz.org/](http://secviz.org/) as well.

---

### Post by emiller12345 on 2010-11-26
Thats a good idea. If you comment out or delete the last " && rm test.png" of the script, it will leave the picture named test.png where ever you execute the script from. I just hate leaving little remains of scripts all over my computer. I think I will repost it to the site you recommend also.

---

### Post by emiller12345 on 2011-07-24
UPDATE: v0.2 is now available
[http://digitalmagican.wordpress.com/2011/07/24/lightstorm-time-plot-v0-2-released/](http://digitalmagican.wordpress.com/2011/07/24/lightstorm-time-plot-v0-2-released/)
v0.2 can read a directory of pcaps directly with the use of tshark

example:

[IMG]http://digitalmagican.files.wordpress.com/2011/07/lightstorm-20110723.png?w=510&h=248[/IMG]

red = TCP
blue = UDP
yellow = ICMP

I didn't start the capture till around 10am, which is why there is no data before that

---

### Post by Kinstonian on 2011-07-25
Cool, I can't write bash scripts, so I don't know how far you can go by creating data visualizations with shell scripts.  Learning Python or similar would allow you to use ChartDirector, matplotlib, etc. packages to create a bigger variety of charts.

Another option would be to use bash scripts to save the output in CSV and import that into something like Calc or R.  I would think you could keep it all automated by using bash scripts to run an R script.  Then again, I'm not familiar with writing bash shell scripts.

---

