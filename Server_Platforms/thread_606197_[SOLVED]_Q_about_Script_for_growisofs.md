---
title: "[SOLVED] Q about Script for growisofs"
date: 2007-11-07
forum: Server Platforms
---

### Post by cocophone on 2007-11-07
I'm needing some help writing a script to backup several directories to a DVD.  I'm using growisofs using graft-points.

I would like to use a variable to pass a list of directories and their graft-points to growisofs.  Right now I have all the directories listed on one line of the script.  My script failed when I typed a return after each graft-point.

```
#!/bin/bash

# Calculate the week number using the date command:

WEEKOFFSET=$[ $(date +"%V") % 2 ]

# Test if we have a remainder.  If not, this is an even week so send a message.
# Else, do nothing.

if [ $WEEKOFFSET -eq "1" ]; then

 growisofs -dvd-compat -Z /dev/dvd -joliet-long -R -V "Data_01_to_E" -graft-points "/client_data/01-Numbers/=/mnt/drive_g/01-Numbers/" "/client_data/A/=/mnt/drive_g/A/" "/client_data/B/=/mnt/drive_g/B/" "/client_data/C/=/mnt/drive_g/C/" "/client_data/D/=/mnt/drive_g/D/" "/client_data/E/=/mnt/drive_g/E/" 
fi

```

---

### Post by koenn on 2007-11-08
You could try something like
```

MYLIST="\
		"/client_data/A/=/mnt/drive_g/A/" 			\
		"/client_data/B/=/mnt/drive_g/B/" 			\
		"/client_data/C/=/mnt/drive_g/C/" 			\
		"/client_data/D/=/mnt/drive_g/D/" 			\
		"/client_data/E/=/mnt/drive_g/E/"			\
	" #closing quote

for ITEM in $MYLIST ; do echo "$ITEM" ; done

echo $MYLIST

```
note that the " " around the "path=path" items are not preserved. If your grwoisofs statement requires them, you could try it this way (note the backslashes)
```

MYLIST="\
		\"/client_data/A/=/mnt/drive_g/A/\" 			\
		\"/client_data/B/=/mnt/drive_g/B/\" 			\
		\"/client_data/C/=/mnt/drive_g/C/\" 			\
		\"/client_data/D/=/mnt/drive_g/D/\" 			\
		\"/client_data/E/=/mnt/drive_g/E/\"			\
	" #closing quote

echo $MYLIST

```

What you do is use backslashes to escape (the interpretation of)
1- end of line characters
2- quotes

---

### Post by cocophone on 2007-11-08
I think I'm part way to getting it to work, but I'm getting this error message:

> 
Setting input-charset to 'UTF-8' from locale.
genisoimage: No such file or directory. Invalid node - '/mnt/drive_g/S"'.
:-( write failed: Input/output error


Here is the script that I tried:

> 
#!/bin/bash

MYLIST="\
\"/client_data/S/=/mnt/drive_g/S\" \
\"/client_data/T/=/mnt/drive_g/T\" \
" #closing quote

echo "My List  $MYLIST"

# Calculate the week number using the date command:

WEEKOFFSET=$[ $(date +"%V") % 2 ]

# Test if we have a remainder.  If not, this is an even week so send a message.
# Else, do nothing.

if [ $WEEKOFFSET -eq "1" ]; then
 growisofs -dvd-compat -Z /dev/dvd -joliet-long -R -V "Data_S_to_T" -graft-points $MYLIST

fi


The script works if I do it this way, but the script would get messy if I need to backup say 10 different directories

> 
#!/bin/bash

# Calculate the week number using the date command:

WEEKOFFSET=$[ $(date +"%V") % 2 ]

# Test if we have a remainder.  If not, this is an even week so send a message.
# Else, do nothing.

if [ $WEEKOFFSET -eq "1" ]; then
# echo "burn dvd"
growisofs -dvd-compat -Z /dev/dvd -joliet-long -R -V "Data_S_to_T" -graft-points "/client_data/S/=/mnt/drive_g/S/" "/client_data/T/=/mnt/drive_g/T/"

fi



---

### Post by MJN on 2007-11-08
I've only taken a quick glance at what you're doing here but try wrapping your $MYLIST in quotes i.e. "$MYLIST". This will preserve the spaces (and other characters) which I'm assuming are important the command.

Mathew

---

### Post by koenn on 2007-11-08
in your second script (without MYLIST), your paths all have trailing slashes (i.e. they end in / ). In the values for MYLIST in the first script, your not using trailing slashes : eg /mnt/drive_g/T
the \ doesn't count : it's there to escape the ", i.e. you should interprete \" as 1 single character : "
Try again with
```

MYLIST="\
     \"/client_data/S/=/mnt/drive_g/S**/**\"    \
     \"/client_data/T/=/mnt/drive_g/T**/**\"    \
" #closing quote

```

edit - MJN's suggestion of using quotes around $MYLIST is also a good idea

---

### Post by cocophone on 2007-11-08
I put the double quote around "$MYLIST" and fiixed the trailing /

Now I'm getting this error message


```

My List  "/client_data/S/=/mnt/drive_g/S/" "/client_data/T/=/mnt/drive_g/T/"
Executing 'genisoimage -joliet-long -R -V Data_S_to_T -graft-points "/client_data/S/=/mnt/drive_g/S/" "/client_data/T/=/mnt/drive_g/T/" | builtin_dd of=/dev/dvd obs=32k seek=0'

Setting input-charset to 'UTF-8' from locale.
genisoimage: No such file or directory. Invalid node - '/mnt/drive_g/S/" "/client_data/T/=/mnt/drive_g/T/"'.
:-( write failed: Input/output error
```



The error message drops the /client_data/S/=

Also genisoimage is linked to mkisofs 

when I type genisoimage -version I get 
> 
mkisofs 2.01.01a33 (i686-pc-linux-gnu) Copyright (C) 1993-1997 Eric Youngdale (C) 1997-2007 Jörg Schilling


---

### Post by cocophone on 2007-11-09
This is how I got it to work for me.  I removed the double quotes from the graft-points listed in MYLIST.

This DID NOT work for me

```

#!/bin/bash

MYLIST="\
\"/client_data/S/=/mnt/drive_g/S\" \
\"/client_data/T/=/mnt/drive_g/T\" \
" #closing quote

echo "My List $MYLIST"

# Calculate the week number using the date command:

WEEKOFFSET=$[ $(date +"%V") % 2 ]

# Test if we have a remainder. If not, this is an even week so send a message.
# Else, do nothing.

if [ $WEEKOFFSET -eq "1" ]; then
growisofs -dvd-compat -Z /dev/dvd -joliet-long -R -V "Data_S_to_T" -graft-points $MYLIST

fi

```


This DID work for me

```

#!/bin/bash
# Calculate the week number using the date command:

WEEKOFFSET=$[ $(date +"%V") % 2 ]

# Test if we have a remainder.  If not, this is an even week so send a message.
# Else, do nothing.

if [ $WEEKOFFSET -eq "1" ]; then

 growisofs -Z /dev/dvd -joliet-long -R -V "Data_S_to_T" -graft-points \
/client_data/S/=/mnt/drive_g/S/ \
/client_data/T/=/mnt/drive_g/T/ 

fi


```

All the examples that I found had all used double quotes around each graft-point.  But when I tried to put each graft-points on its own line to make the script more readable for example, if there was 10 different graft-points, the graft-points were not passed correctly to genisoimage by growisofs

---

### Post by koenn on 2007-11-10
So, then, does it also work if you use a variable in which the graftpoints are not double-quoted, such as

```

GRFTPNTS=/client_data/S/=/mnt/drive_g/S/    \
                /client_data/T/=/mnt/drive_g/T/     \
                 /client_data/A/=/mnt/drive_g/A/ 

```
?

---

### Post by cocophone on 2007-11-10
> **koenn said:**
> So, then, does it also work if you use a variable in which the graftpoints are not double-quoted, such as

```

GRFTPNTS=/client_data/S/=/mnt/drive_g/S/    \
                /client_data/T/=/mnt/drive_g/T/     \
                 /client_data/A/=/mnt/drive_g/A/ 

```
?

I decided not to try that, because it would not simplify my script.  I would have the graft-points listed at the top of my script exactly as they are listed below.  My goal was to have an easy to read script even if I wanted to have as many as 10 graft-points.

---

### Post by koenn on 2007-11-10
It would allow you to maintain all variables neatly at the head of the script, but you're right, in such a short script and given that that list only is used once throughout the script, that's a minor detail. 

glad to see you got it working.

---

