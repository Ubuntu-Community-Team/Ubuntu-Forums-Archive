---
title: "scripting question"
date: 2009-01-05
forum: Server Platforms
---

### Post by JKParton on 2009-01-05
this should be rather interesting...

i am working on a script that i found online, i want to outfit it with some modifications, but being that i dont know scripting like i should, i need some help.

on this script, it waits for a cd to be inputed into the drive before it writes. 

what i would like to do is make the script wait for the original  cd, make an iso image of it that is stored on the hard drive, and then burn it to multiple devices.
ive got most of the commands for it that i want to use

- dd if=/dev/scd0 for=/cd.iso (i know i can use cat but i prefer dd) and then the script below
   
 #can someone also point me in the right direction as in regards    to created scripts that require user input..

```

#!/bin/bash

#Copyright David Stark 2004
#Program to initiate cdrecord on multiple devices, recording on successive 
#blanks until SIGINT (Ctrl-C) is received.

#User help
if [ $# == 0 ] || [ $1 == "-h" ] || [ $1 == "--help" ]
    then
    echo "This program starts cdrecord to burn one image file to multiple devices,"
    echo "ejecting the cd when recording has finished. When a blank CD is inserted"
    echo "into any of the specified drives, recording of the image begins again."
    echo ""
    echo "Usage: $0 image devicelist"
    echo ""
    echo "'image' is the name of the image to be burned."
    echo "'devicelist' must be a list of devices which cdrecord understands -"
    echo "                                   see 'man cdrecord' for details."
    echo ""
    echo "Do Ctrl-C to terminate when recording is finished."
    exit 0
fi

#Arg check
if [ $# -lt 2 ]
    then
    echo "Not enough arguments. See '$0 -h' for help."
    exit 1
fi
if ! [ -e $1 ]
    then
    echo "$1 does not exist. Exiting."
    exit 1
fi

ISOFILE=$1

burndrive()
{
    echo "Please insert a blank CD into $1 to begin."
    while true
      do
      sleep 2
      STATUS=`cdrecord -V --inq dev=$1 2>&1`
      echo $STATUS | grep "medium not present" &> /dev/null
      if [ $? != 0 ]
	  then
	  echo "CD loaded on $1. Continuing."
	  cdrecord --eject dev=$1 -data $ISOFILE &> /dev/null
	  case $? in
	      0)
		  echo "Burning completed successfully on drive $1."
		  echo "Insert a blank disc to continue on $1.";;
	      254)
		  echo "Disc in $1 is not blank."
		  echo "Please insert a blank disc in $1.";;
	      *)
		  echo "Unknown error on $1.";;
	  esac
      fi
    done
}

for go in $*
do
  if [ $go == $1 ]
      then
      echo -n
  else
      burndrive $go &
      PIDLIST="$PIDLIST $!" #Collect subshell PIDs
  fi
done

#Kill subshells, then exit
trap "kill -9 $PIDLIST; exit 0" SIGINT

#This sleep loop is just to retain control of the console -
#for message output, and to catch Ctrl-C
while true
  do
  sleep 1000
done
```

if you know of anything better, let me know.

---

### Post by dantrevino on 2009-02-19
what user input do you want?  are you trying to loop through devices?

---

