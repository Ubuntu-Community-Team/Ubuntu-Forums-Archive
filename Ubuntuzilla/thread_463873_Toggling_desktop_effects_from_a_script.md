---
title: "Toggling desktop effects from a script"
date: 2007-06-04
forum: Ubuntuzilla
---

### Post by max.spicer on 2007-06-04
Hi,

Is there any way of toggling desktop effects from the command line?  I've discovered that Oracle's SQL Developer tool will only run with Desktop Effects disabled, so would like to write a launcher script for it that turns them off, runs it, and then turns them back on when it terminates.

Cheers,

Max

---

### Post by eentonig on 2007-06-04
Beryl?

Try this. 

You'll have to go through to see if it works and adapt it here and there

> #!/bin/bash
#Script made the 12/1/2007 by Ecthelion
# 
br=0
if ps -A | grep "beryl-manager" > /dev/null
then br=1
fi

(NO_ARGS=0
echo "You are running the beryl_on_off script";
if [ $# -eq "$NO_ARGS" ] # Script invoked with no command-line args?
then
if [ $br = 1 ]
then #Shutdown Beryl
killall beryl-manager;
killall beryl;
#killall emerald;
gnome-terminal -e "metacity --replace" && sleep 1 &
echo "Metacity vervangt Beryl" & sleep 2;
killall gnome-terminal;
else #Startup Beryl
gnome-terminal -e "beryl-manager" & sleep 2
#gnome-terminal -e "beryl-manager" && sleep1 &
#gnome-terminal -e "emerald --replace" & sleep 2
echo "Emerald & Beryl zijn geladen" & sleep 5;
fi
fi

while getopts ":O:" Option
do
case $Option in
O ) if [ "ff" = "$OPTARG" ]
then
if [ $br = 1 ]
then
echo "Beryl wordt afgesloten";
killall beryl-manager;
gnome-terminal -e "metacity --replace" & sleep 1
#killall metacity;
else
echo "Beryl staat niet aan"
fi

elif [ "n" = "$OPTARG" ]
then
if [ $br = 1 ]
then
echo "Beryl draait reeds"
else
echo "Bezig met opstarten van Beryl";
gnome-terminal -e "beryl-manager" & sleep 10


fi

else
echo "Verkeerd argument ingegeven, kies voor -On / -Off";
#echo "Ingegeven argument zou dit moeten zijn: \"$OPTARG\" ";
fi ;;
* ) echo "Unimplemented option chosen." ;; # DEFAULT
esac
done
exit 0
) &

---

### Post by nanotube on 2007-06-04
thanks eentonig for your cool script. :)

but ehrm, max, this question has nothing to do with the ubuntuzilla project, you probably should have posted it in the general-questions or in the desktop-effects section of the ubuntu forums. :)

---

### Post by max.spicer on 2007-06-04
Whoops, sorry - I completely forgot which forum I was posting to!  ;-)

Max

> **nanotube said:**
> thanks eentonig for your cool script. :)

but ehrm, max, this question has nothing to do with the ubuntuzilla project, you probably should have posted it in the general-questions or in the desktop-effects section of the ubuntu forums. :)

---

