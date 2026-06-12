---
title: "Can anyone double check this BASH text-adventure?"
date: 2009-06-05
forum: The Cafe
---

### Post by BslBryan on 2009-06-05
This is driving me nuts!  

I'm programming a very very simple text adventure game to pass the time.  For some reason, something very small (I'm sure) is holding me back from letting it progress.  

I am making it with Ubuntu/Linux users in mind, so I don't want to give away too much, but I'm forced to give away one ending.  SPOILER ALERT! ;)
```
#!/bin/bash

clear
echo "You find yourself standing in front of"
echo "the cheerful man in Best Buy.  He asks you whether or not"
echo "you need help.  Turns out he works here."
echo ""
echo "You say that you are looking for a new computer,"
echo "and would like to be pointed in that direction."
echo "He kindly points you to them, and lets you go off on your way."
echo ""
echo "While browsing, three different laptops catch your eye."
echo "You see a Dell Latitude D630 with Ubuntu 9.04 (1),"
echo "a MacBook Pro (2), and an HP HDX 16t running Vista (3)"
read -p "Which do you choose? (1/2/3) "
if [ "$REPLY" = "1" ] ; then 
  BR="1"
fi
if [ "$REPLY" = "2" ] ; then 
  BR="2"
fi
if [ "$REPLY" = "3" ] ; then 
  BR="3"
fi
if [ "$BR" = "3" ]; then
  clear
  echo "You happily make your purchase, and get home safely." 
  echo "You open up the box, and read the manual that begins,"
  echo "'Open the box and retrieve the manaul.'"
  echo ""
  echo "You follow the instructions, and in no time at all have"
  echo "a perfectly functioning computer."
  echo "However, before you can use anything, you must register"
  echo "all of your products."
  echo ""
  echo "You register half of your products via internet in two and a half"
  echo "hours, but it's worth it.  Your computer is now good"
  echo "enough to fine-tune to your needs."
  echo ""
  echo "You download a PDF viewer and the Flash codec."
  echo ""
  echo "..."
  echo "For some reason, nothing is happening."
  echo "Press 4 to press Ctrl+Alt+Del."
fi  
if [ "$REPLY" = "4" ] ; then 
   R="1"
fi
if [ "$R" = "1" ]; then
clear
  echo "You press Ctrl+Alt+Del, a trick you learned from your cousin,"
  echo "and suddenly you see a blue screen."
  echo "You are prompted to reboot, and before you have time to think,"
  echo "the computer reboots by itself."
  echo "Windows does a disk check, and suggests you run Norton Antivirus."
  echo ""
  echo "In order to run Norton Antivirus, you must register the software."
  echo "In an attempt to register the software, your computer, overcome by"
  echo "viruses and malware, gives up.  Poor little fella."
  echo ""
  echo "You return to Best Buy the following day and get a full refund."
  echo "You buy the computer that you want, and live happily ever after."
  echo "Winning Game Ending 1/2!"
fi
```

What happens is it never lets me input "4" so it can continue to the next screen.  

At first, I had two options, one for shooting the computer, and the other to press CTRL+ALT+DEL, and had the same problem. 

 I've tried a lot of different stuff, and it just takes me back to my terminal prompt.  

What do you guys think?

---

### Post by koenn on 2009-06-05
you're missing a 'read'

---

