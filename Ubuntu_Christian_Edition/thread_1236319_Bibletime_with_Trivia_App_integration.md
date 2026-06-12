---
title: "Bibletime with Trivia App integration"
date: 2009-08-10
forum: Ubuntu Christian Edition
---

### Post by Aronzak on 2009-08-10
This is a small addition to the trivia app that lets the second trivia window have a second button called 'lookup' that will pass the Bible passage to Bibletime, letting a user see the context of the trivia question. I haven't figured out a way to do this with Xiphos (included by default).  Would it be possible to include Bibletime by default? Or maybe can anyone work on Xiphos to add the ability to pass in a verse to lookup, like with bibletime's --open-default-bible?

```
#!/bin/sh
#Bible trivia for Linux
#Originally written by D.M. Bartusik <dmcb48@earthlink.net> 1-Jan-2001
# Re-written and debianize by David Kuntadi <d.kuntadi@gmail.com>
# Small addition by Aronzak

TODAY=`date +"%m%d"`
DATA=`grep $TODAY /usr/share/trivia/trivia.dat`
echo $DATA
HOUR=`date +"%H"`
if [ $HOUR -le 11 ]
    then TOD="Morning"
    elif [ $HOUR -ge 12 -a $HOUR -lt 18 ]
    then TOD="Afternoon"
    else
    TOD="Evening"
fi
echo $DATA | awk -F"|" '{printf("%s\n\nAnswer: %s",$2,$3)}' > $HOME/.cache/trivia2

text2=`cat $HOME/.cache/trivia2`
echo $text2
zenity --question --width=530 --height=200 --title="Bible Trivia - Good $TOD!  It's `date +"%A, %B %e, %Y"`" --ok-label=lookup --cancel-label=dismiss --text="$text2"

rc=$?
if [ "${rc}" = "1" ]; then
echo "Program terminated."
else
bibletime --open-default-bible "`grep \( $HOME/.cache/trivia2 | sed 's/^[^(]*//' | tr -d '()'`"
fi
#rm $HOME/.cache/trivia
```

---

### Post by benthorp on 2009-08-13
OK - there isn't an easy way to do it, but I've put together a little script that edits the session tab file and launches gnomesword.

A few provisos at this point:
1. If you've never opened gs then it might not have the file created, which would be bad ;)
2. I'm using stock Ubuntu, so it's still called gnomesword2 and not xiphos, but should be hard to play with it

Just save it as gnomesword_launch.py (or whatever) and then run:

```

$ python gnomesword_launch 1 John 3:16

```
```

#!/usr/bin/env python

# Short script to fool xiphos (nee gnomesword2) to opening at a passage

import re, sys, os

if (len(sys.argv) == 1) :
    print "Launching GnomeSword..."
    os.system("gnomesword2")
else:
    myverse = " ".join(sys.argv[1:])
    print "Launching GnomeSword to "+myverse
    
    # Read in the last open tabs file
    tabs_file = os.path.expanduser("~/.gnomesword/tabs/.last_session_tabs")
    tabs_data = open(tabs_file, 'r').readlines()

    output_data = ""
    added = False

    for line in tabs_data:
        if ((line.split()[0] != "<tab") or (added)) :
            output_data += line
        else:
            # Add a new tab based on current tab
            newline = re.sub('text_commentary_key=".*?"', 'text_commentary_key="'+myverse+'"', line)
            output_data += newline
            output_data += line
            added = True

    # Overwrite the tabs file
    output = open(tabs_file, 'w')
    output.write(output_data)
    output.close()
    
    # Launch gnomesword
    os.system("gnomesword2")

```Should be easy to integrate now.

---

