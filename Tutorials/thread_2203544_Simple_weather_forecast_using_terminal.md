---
title: "Simple weather forecast using terminal"
date: 2014-02-04
forum: Tutorials
---

### Post by barryww1956 on 2014-02-04
I installed the weather-util package and any dependencies:
```
sudo apt-get install weather
```

I first created a "/scripts" directory in my home folder:
```
barry@barry:~$ mkdir scripts
```

Then I created a simple bash script which I called "forecast", saving in the new folder.  Just cut and paste the code below into a text file, naming it "forecast".  Change the zip code (shown below as 74012) to whatever you want:
```
#!/bin/bash
clear
echo "Today's date is `date`"
echo "Here are your local weather conditions and forecast:"
weather --forecast -a --no-cache-data 74012 | more
echo ""
echo "**************************************END********************************
```

I then made the script executable. Open a terminal, change to the "scripts" directory you created above and type:
```
chmod +x forecast
```

Then I added a PATH variable to my .bashrc file located in my home folder:
```
barry@barry:~$export PATH=~/scripts:$PATH
``` 

Whenever I want to see a quick forecast, I open up a terminal and simply type 
```
forecast
```
which yields the following (hope the screenshot works):[IMG]file:///home/barry/Pictures/Screenshot.png[/IMG]
*edit: well the screenshot doesn't want to load....will work on later....B*

---

### Post by Lars Noodén on 2014-02-04
Cool.

Alternately, if you make a *~/bin* directory and put the script there, then next time you log in, it should be in your $PATH.  

With printing the date, you can [use parentheses instead of backticks](http://mywiki.wooledge.org/BashFAQ/082).  But it's also possible to use [date](http://manpages.ubuntu.com/manpages/saucy/en/man1/date.1posix.html) by itself.  

```

[s]date +'Today's date is %a %b %e %T %Z %Y'[/s]
date +"Today's date is %a %b %e %T %Z %Y"

```

You might also look at using [conky](http://ubuntuforums.org/showthread.php?t=281865) for posting weather info, but that's outside of the terminal and on the desktop GUI.

---

### Post by barryww1956 on 2014-02-04
The man pages on weather gives some other things to play with too.  Lots of ways to accomplish the same thing in Linux is there not?  I like that cause there should be at least one that works even for me.  Don't guess I can post a screenshot as this is only my second post, if I read the rules right I need at least ten.  I'll eventually get there.  I like terminal apps like these due to their low overhead, and my laptop is due for replacement.  But that's another subject.

---

### Post by tgalati4 on 2014-02-04
A little correction:

```
date +"Today's date is %a %b %e %T %Z %Y"
```

The apostrophe needs quotes as the delimiter, otherwise the *date* command (within bash) gets confused.

---

