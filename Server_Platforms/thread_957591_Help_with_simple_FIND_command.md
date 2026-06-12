---
title: "Help with simple FIND command"
date: 2008-10-24
forum: Server Platforms
---

### Post by LoonyLuke on 2008-10-24
Hi Guys,

Have been searching for ages about this. I need to produce a list of all files in */var/www/viovet* directory that have been changed in last 62 mins. I can use the following command:

```
find /var/www/viovet -cmin -62 -print
```

This works fine, but files in the */var/www/viovet/navmenu* and */var/www/viovet/cache* dirs are very often changing and so I don't want these to appear in the list.

I have tried a number of different commands, such as

```
find /var/www/viovet -path '/var/www/viovet/navmenu' -prune -o -path '/var/www/viovet/cache' -prune -cmin -62 -print
```

and

```
find /var/www/viovet -name navmenu -o -name cache -cmin -62 -print
```

If somebody could help me get the correct code that would be great! Thanks!

Just for the reference, the reason for this command is that it will be run every 60 mins and email me a list of any changes (if any) so that I can find certain hacking attempts. (I don't want the above dir to show as I don't want the email to be sent if those are the only changes).

Cheers,

Luke

---

### Post by lykwydchykyn on 2008-10-25
You could pipe the output through "grep -v navmenu" and "grep -v cache".

---

### Post by ubuntwinkel on 2010-10-11
This is waaay too late, but this thread helped me correct the complex search I was trying (and failing) to do.  

Applying what finally worked for me to the problem Luke presented, he should try:

```
find -iname '/var/www/viovet/*' -a -not -wholename '/var/www/viovet/navmenu/*' -a -not -wholename '/var/www/viovet/cache/*' -a -cmin -62 -print
```

[INDENT]**-iname** specifies a case-insensitive name.   
**-a** and **-not** need to be together (I got stuck when I assumed that -not implied -a)
**-wholename** specifies the file name including path.  The **-path** test might work in place of -wholename, but I didn't use it in the method which worked for me, so I don't know. 
[/INDENT]

I suspect this might work as well, but I don't know how to test it:

```
find /var/www/viovet -a -not -wholename '/var/www/viovet/navmenu/*' -a -not -wholename '/var/www/viovet/cache/*' -a -cmin -62 -print
```

The complete command which I used successfully after finding this post is as follows:

```
find . -iname \*.avi -a -size +100M -a -not -wholename './Videos/*' -a -not -wholename './install/*'
```

This finds all the files in the current folder ending in .avi which are not in either the Videos sub-directory or in the install sub-directory.  

Hope this helps someone.

---

