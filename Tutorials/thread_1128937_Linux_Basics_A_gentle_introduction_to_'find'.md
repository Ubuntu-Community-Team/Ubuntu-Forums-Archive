---
title: "Linux Basics: A gentle introduction to 'find'"
date: 2009-04-18
forum: Tutorials
---

### Post by andrew.46 on 2009-04-18
This guide has been converted to a wiki:

[https://help.ubuntu.com/community/find](https://help.ubuntu.com/community/find)

Support is still available in this thread so feel free to ask any questions :).

---

### Post by FakeOutdoorsman on 2009-05-01
Yet another excellent guide.  Good job, Andrew.

---

### Post by graysky on 2009-05-01
Nice guide... can you add searching within files?  For example, there are a number of documents in a given directory.  You want to find a keyword within them.

---

### Post by andrew.46 on 2009-05-01
Hi FakeOutdoorsman,

> **FakeOutdoorsman said:**
> Yet another excellent guide.  Good job, Andrew.

Thanks very much! I plan about a dozen of these in a series, partly because it fills a need and partly because with vdpau, FFmpeg-mt, PPA archives, impending rc3 release etc I will be slipping out of the MPlayer business soon :-).

Andrew

---

### Post by andrew.46 on 2009-05-01
Hi graysky,

> **graysky said:**
> Nice guide... can you add searching within files?  For example, there are a number of documents in a given directory.  You want to find a keyword within them.

There is an immense amount of material omitted in this guide, in part because this is intended to be an *introduction* only. But definitely I shall consider adding something like this in the near future. A 'real world' example of the usage of grep that you mentioned could be in my case finding all of the html files that mention 'slrn' in my offline website:

```

$ **[COLOR="Red"]find $HOME/html/andrews-corner -exec grep -q 'slrn' '{}' \; -print[/COLOR]**
/home/andrew/html/andrews-corner/leafnode.html
/home/andrew/html/andrews-corner/index.html
/home/andrew/html/andrews-corner/slrn.html
/home/andrew/html/andrews-corner/custom_os.patch
/home/andrew/html/andrews-corner/mutt.html

```

Fantastic program!!

Andrew

---

### Post by graysky on 2009-05-03
Very cool.

How can I add an alias to my ~/.bashrc that will allow me to do this on the shell just by typing the alias and word or phrase?

For example, the alias might be called [color=blue]lookfor[/color] and what comes after that could be what you wanna search for inside the files in the current directory.

Example:

```
$ lookfor lsrn
```

That would then do this:
```
find ./ -exec grep -q 'slrn' '{}' \; -print
```

How can I do that?

Also, how would you handle a group of words?

---

### Post by andrew.46 on 2009-05-03
Hi graysky,

> **graysky said:**
> 

How can I add an alias to my ~/.bashrc that will allow me to do this on the shell just by typing the alias and word or phrase?

An interesting question, and one that I had to do a little research on before I could answer properly :-). An actual *alias* would not do as bash aliases are not really meant to contain variables. What you ask for can be set as a bash *function* instead:

```

lookfor() {
  find . -exec grep -q "$1" '{}' \; -print 
}

```

This would search the working directory and subdirectories with the syntax:

```
lookfor search_term
```

which is what you specified. However a better idea would be to use two variables, the first being the path to search and the second being the search term:

```
lookfor() {
  find "$1" -exec grep -q "$2" '{}' \; -print 
}
```

and the syntax would then be:

```
lookfor path search_term
```

Place this in ~/.bashrc and have a play with it. Mind you this starts moving towards a shell script which would of course be much more flexible.

> Also, how would you handle a group of words?

I am not entirely sure what you mean there, although I sense that your needs are slipping further away from 'find' and leaning more towards grep :-). In fact perhaps a simpler search with 'find' piped to grep would be better. Can you provide a specific example of what you need?

All the best,

Andrew

---

### Post by paulstephen4 on 2009-05-04
Superb guide, its really very helpful for me, Thanks andrew for sharing with us.

---

### Post by andrew.46 on 2009-05-05
Hi paulstephen4,

> **paulstephen4 said:**
> Superb guide, its really very helpful for me, Thanks andrew for sharing with us.

Thank you *very* much for your kind words,

Andrew

---

### Post by Slowspeed on 2009-07-27
Thank you for a clear and concise intro guide. I have been weening myself off of gui now that I built a home server and appreciate this type of reference material.

---

### Post by andrew.46 on 2009-07-28
Hi Slowspeed,

> **Slowspeed said:**
> Thank you for a clear and concise intro guide. I have been weening myself off of gui now that I built a home server and appreciate this type of reference material.

It is totally my pleasure :-). I am in the process of rewriting and expanding this material for the Ubuntu Community Wiki at the moment:

find - Community Documentation
[https://help.ubuntu.com/community/find](https://help.ubuntu.com/community/find)

About another week of work to go on that one yet...

Andrew

---

### Post by FakeOutdoorsman on 2010-02-01
I think this is an understated guide.  Passing the results of *find* to other utilities just creates so many possibilities.

---

### Post by andrew.46 on 2012-04-09
This guide has been converted to a wiki:

[https://help.ubuntu.com/community/find](https://help.ubuntu.com/community/find)

Support is still available in this thread so feel free to ask any questions :).

---

### Post by rainbowcats on 2012-04-09
Heh, thanks for this one :) I've never used find for anything other than searching by file names! (until now)

---

### Post by andrew.46 on 2012-04-09
> **rainbowcats said:**
> Heh, thanks for this one :) I've never used find for anything other than searching by file names! (until now)

Glad to hear the wiki has been useful to you :).

---

### Post by kevdog on 2012-04-09
Off topic, but I'm up for an awk primer.  Fantastic find guide. I'm glad its being promoted again.

---

### Post by andrew.46 on 2012-04-09
> **kevdog said:**
> Off topic, but I'm up for an awk primer.  Fantastic find guide. I'm glad its being promoted again.

Well, actually this guide was turned into a wiki a while back but I have just now altered the guide in line with the new way of doing things :). As for an awk primer, I wish I had this knowledge!!

---

### Post by George Heine on 2012-04-17
> Support is still available in this thread so feel free to ask any questions :smile:.Just noticed this thread when reading through the changes to Tutorials and Tips.

Maybe this is more of a shell-scripting question, but here goes:  I have a script "newest.sh" in ~/bin that looks like

```
format='%T@\t%s\t%Tx %TH:%TM:%TS\t%p\n';
find $* -printf "$format" | sort -k1n|cut -f2-

```Basiically, it uses "find -printf" to get the time in seconds since the epoch, sorts by this field, then clips it off.  The result is a list of all the files in the selected location, sorted from oldest to newest.   Works like a charm, EXCEPT if I am trying to match a specific part of a file name,  and there is a match in the top-level directory.  

For example: typing 
```
newest.sh . -iname \*.pdf
```in a directory which happens to contain a file named "file.pdf" results in the error

```
find: paths must precede expression: file.pdf
```How can I insulate the argument to "-iname" from being interpreted by the shell?


Thanks for any help.

---

### Post by andrew.46 on 2012-04-17
Oddly enough I cannot duplicate this error:

```

andrew@skamandros~/media/YouTube$ **[COLOR="Red"]newest.sh [/COLOR]**
17981740	05/28/2009 01:42:49.0000000000	./Armistice_Day_1920_Homecoming_Of_An_Unknown_Warrior2.flv
44465312	09/04/2009 09:45:32.0000000000	./Ruttie_Jinnah.flv
19841820	03/23/2010 11:15:28.0000000000	./Cold_Chisel_Bow_River.mp4
20235169	04/28/2010 17:55:55.0000000000	./ashtanga_yoga_demo.mp4
438626221	12/02/2010 12:00:58.0000000000	./The_Art_Of_Piano_Great_Pianists_Of_The_20Th_Century.flv
475711968	12/23/2010 23:59:27.0000000000	./Gary_Yourofsky.flv
12730971	02/23/2011 14:17:30.0000000000	./Zenga_Zenga.flv
93765772	08/03/2011 07:06:54.0000000000	./Dr_Swami_Shankardev_Rotation_Through_Chakras_Guided_Meditation.mp4
79	12/13/2011 18:42:44.0000000000	./template
0	04/18/2012 08:42:19.3180826960	./file.pdf
4096	04/18/2012 08:42:19.3180826960	.
andrew@skamandros~/media/YouTube$ **[COLOR="Red"]newest.sh . -iname \*.pdf[/COLOR]**
0	04/18/2012 08:42:19.3180826960	./file.pdf


```

So I have to admit that I am not entirely sure what is happening here...

---

### Post by erind on 2012-04-17
> **George Heine said:**
> 
[...]

For example: typing 
```
newest.sh . -iname \*.pdf
```in a directory which happens to contain a file named "file.pdf" results in the error

```
find: paths must precede expression: file.pdf
```How can I insulate the argument to "-iname" from being interpreted by the shell?


Thanks for any help.

The problem here is not '-iname', but the stripping of the backslash from the shell, causing the unwanted expansion of '*.pdf' after **find**'s '-iname' option, and the command line would have looked like:

    ```
find . -iname file.pdf other_file.pdf ...

```which is a syntax error, (but it'd have worked fine if it were only *one* pdf file in the search path). One way to avoid shell quoting issues is using **"$@"**:

```
#!/bin/bash
set -x

format="%T@\t%s\t%Tx %TH:%TM:%TS\t%p\n"

find "$@" -printf "$format" | sort -k1n | cut -f2-

```Or using arrays:

```
...
arr=("$@")

find "${arr[@]}" -printf "$format" | sort -k1n | cut -f2-
```And running it:

```
./newest.sh . -iname "*.pdf"

```*P.S.* For more convenience, I'd use quotes instead of backslashes when escaping special characters in the command line, for example:

```
./newest.sh "dir with space/" -iname "*.pdf" -type f 
```

---

### Post by George Heine on 2012-04-18
Thanks, erind, for a clear and concise explanation.  Tried both your examples and they both worked.    Any reason to prefer one over the other?

---

### Post by erind on 2012-04-18
Although in this case the first option (**"$@"**) is simpler, with arrays I've noticed an easier handling of individual tokens, as far as shell quoting is concerned. This quote from *mywiki.wooledge.org* nicely sums it up:

> Arrays are basically indexed lists of strings. **They are very convenient for their ability to store multiple strings together without relying on a delimiter to split them apart (which is tedious when done correctly and error-prone when not)**.From:  [http://mywiki.wooledge.org/BashGuide/Parameters](http://mywiki.wooledge.org/BashGuide/Parameters)

---

### Post by chickenPie4breakfast on 2012-05-08
has anyone mentioned that there is a typo in the very first line? two within within's

---

### Post by paichkash on 2012-08-09
i am confused by the following part of that wiki
> It is important to get into the habit of quoting patterns in your search as seen above or your search results can be a little unpredictable. Such a search can be much more sophisticated though. For example if you wished to search for all of the ogg files in your home directory, **some of which you think might be named 'OGG' rather than 'ogg', you would run**: 

```
find $HOME -iname '*.ogg' 
```

Here the option '-iname' performs a case-insensitive search while the wildcard character '*' matches any character, or number of characters, or zero characters. 
so in this particular case does it matters to use -name or -iname if we were to search for all files that are .ogg or .OGG ? 

i mean we are using the * doesnt that means 'anything' [case or type of char doesnt matter ?] or is the iname for the .ogg there to make that case insensitive ?

thanks ... i would recomend this note/tip to be added to that great wiki..

---

### Post by drmrgd on 2012-08-09
The 'iname' bit allows the search to be case-insensitive (thus matching either 'ogg' or 'OGG'.  The '*' operator allows any text that comes before the '.ogg' bit.  The two are exclusive, though.  Let's say you have two files called 'file.ogg' and 'file.OGG'.  If you search by:

```
find $HOME -name '*.ogg'
```

You'll only get 'file.ogg' as a result.  If you use -iname, though, you'll get both files as a result, because now the search doesn't care about upper or lowercase file names.  Does that make more sense?

---

### Post by paichkash on 2012-08-09
^^ thanks ... on first read i got the impression that it wont matter to use either iname or name and so were two of my collegues.. we were mistaken by the * .. whearas the .ogg is also a part of the search pattern..

thanks again ..

---

### Post by ads52 on 2012-08-12
> **chickenPie4breakfast said:**
> has anyone mentioned that there is a typo in the very first line? two within within's

I have corrected this small blunder :).

---

### Post by JohnnyC35 on 2013-07-12
I'm looking to be able to find a bunch of pdfs, move those pdfs to another directory, keep the directory structure, and remove the previous structures.
So far I have been able to use the find command and copy the files while keeping the structure:

 find /home/john/books1/ -regex ".*\(pdf\|epub\|mobi\)$" -type f -exec cp '{}' /home/john/temp/ ';'

but if I use mv I get all the files in one directory...

 find /home/john/books1/ -regex ".*\(pdf\|epub\|mobi\)$" -type f -exec mv -b '{}' /home/john/temp/ ';'


Am I stuck using 'cp'? Which is fine, I just need to find a way to then delete them...

 find /home/john/books1/ -regex ".*\(pdf\|epub\|mobi\)$" -type f -exec rm '{}' /home/john/temp/ ';'

I plan to also have this in a cron job but that shouldn't be a problem once I have figured out the script

Thanks for any help :)

---

