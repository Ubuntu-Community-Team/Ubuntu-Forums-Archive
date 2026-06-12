---
title: "run bash script from web interface"
date: 2009-09-14
forum: Server Platforms
---

### Post by b-boy on 2009-09-14
Hi guys I have apache2 installed and I want to run a few bash commands. I hvae tried a few examples but it does not work for me. 

so here is the tutorial i followed [http://www.yolinux.com/TUTORIALS/LinuxTutorialCgiShellScript.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialCgiShellScript.html)

but basically here is the code in this file /var/www/cgi-bin/cat-a-text-page

```
#!/bin/sh
CAT=/bin/cat
COLCRT=/usr/bin/colcrt

echo Content-type: text/plain
echo ""

if [[ -x $CAT && -x $COLCRT ]]
then
        $CAT $1 | $COLCRT
else
        echo Cannot find command on this system.
fi
```

and on my index.html

```
<A HREF="/cgi-bin/cat-a-text-page?**/home/user1/public_html/text-file.txt**">Text of link</A>
```

all that happens when iclik on the link is it shows the bash script and not the output of the script.


Just a note the cgi-bin dir I created by my-self as it was not there and the part in the html code that is bold does not exist

---

### Post by koenn on 2009-09-14
for stuff like that to work you need apache with cgi enabled (it's probably a module, don't know if it's included by default), and your apache config will/must indicate where the cgi-bin directory is located (probably with something like 'ScriptAlias' or so). 

If you get just the contents of the scipt, that's an indication that the script is not executed, and the above is the first thing to check. 

Also, the script expects a parameter ($1). You simply used the sample URL from the tut, with a sample filename that doesn't exist on your system (!?) 

If you want a web app (or script) to display the contents of a file, you  better tell it which file, make sure that file exists, and has a content to show. 
But that is probably just problem no. 2. First check that you actually have cgi, and where the *real* cgi-bin directory is located

---

### Post by b-boy on 2009-09-15
yes it does seem the CGI is not enabled I will try and get that working thanks for the info

---

