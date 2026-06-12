---
title: "Apache vhosts loading slow"
date: 2010-10-23
forum: Server Platforms
---

### Post by heinemann on 2010-10-23
Hello guys,

I have an urgent issue with my apache. Since last night approximately 50% of my vhosts are responding very slowly. That means I see a blank page for 1 minute and then the content comes up real quick. 

I restored the httpd.conf file but it didn't solve the problem. Do you guys have any ideas? I am a little bit helpless.

---

### Post by kevinatkins on 2010-10-23
This could be a result of any number of issues. A DNS problem springs to mind but without further information it's difficult to offer helpful advice. Please could you elaborate - it would be useful if you could post your Apache config files and further information relating to your setup - network, etc.

---

### Post by heinemann on 2010-10-23
> **kevinatkins said:**
> This could be a result of any number of issues. A DNS problem springs to mind but without further information it's difficult to offer helpful advice. Please could you elaborate - it would be useful if you could post your Apache config files and further information relating to your setup - network, etc.

Which config files do you need? The server is a VPS hosted by A2Hosting. They assume that this issues are on my site.

---

### Post by heinemann on 2010-10-23
I got a solution. For any reason I need to replace "motallyTrack($motally_params);"  with "//motallyTrack($motally_params);"
in all the /var/www/html/ folders.

Can I use something like sed for it or do I have to do that manually?

---

### Post by SeijiSensei on 2010-10-24
Script to replace all instances of string1 with string2 in filespec.  Create as /usr/local/bin/replaceall.  Use single quotes around the entries like this:

```
replaceall 'string1' 'string2' 'filespec'
```

Note this uses the underscore character as the delimiter for sed.  If you need to replace underscores you need to modify the sed command below.

```

#!/bin/bash

if [ "$1" = "" ]
then
    echo "Syntax: replaceall 'string1' 'string2' 'filespec'"
    exit 1
fi

WD=`pwd`
NOW=`date +%s`
TMP=~/.replaceall
FILES=`ls $3`
mkdir -p $TMP/$NOW 2>/dev/null

echo "Replacing '$1' with '$2' in:
for i in $FILES;
do
   TEST=`grep "$1" $i`
   #echo "Checking $i; TEST=$TEST"
   if [ "$TEST" != "" ] 
   then
      echo $i
      # save backup copies
      cp $i $TMP/$NOW/$i.bak
      (sed "s_$1_$2_g" $i > $i.new) && (rm -f $i; mv $i.new $i)
   fi
done

cd $WD

echo ""

exit 0

```

---

