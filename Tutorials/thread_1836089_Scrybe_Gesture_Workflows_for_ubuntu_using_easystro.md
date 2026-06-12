---
title: "Scrybe Gesture Workflows for ubuntu using easystroke"
date: 2011-08-30
forum: Tutorials
---

### Post by Enterpart on 2011-08-30
Some of you will be familiar with Easystroke and know of its potential, but did you know you can use the main feature of Scrybe using Easystroke that is highlight a word/phrase - perform a gesture and a website of your choice pops up with your search already.

Well you will now. Very simple you will need two applications.
 If you haven't already got Easystroke just download from terminal
```
sudo apt-get install easystroke
```

now download xsel
```
sudo apt-get install xsel
```

now a command that will search a phrase in youtube and just pop up the window with the search completed

```
google-chrome "http://www.youtube.com/results?search_query=`xsel -p | tr [:space:] +`&aq=f"
```

If your using firefox then replace google-chrome with firefox

now use whatever gesture you like lets say a gesture in shape of a y.

then your good to go. Test with this "Never Gonna Give You Up"
Enjoyed that :p

the way it works is using this 
```
`xsel -p | tr [:space:] +`
``` 
in the url
in place of what ever search term you used and xsel stores whatever you highlighted in x selection.

the neat thing is once you highlighted a phrase you can use it to access more websites without having to go back to highlighting the phrase again. but once a new phrase is selected whatever search you perform will use that phrase.

if you dont know how I knew what to type to get that url then its simple. go to youtube.com
then type test
now whatever comes in the url after you typed that copy and past it in your command in easystroke but replace "test" with "`xsel -p | tr [:space:] +`"

you can even use on word documents, you dont have to highlight on internet

for convenience sake I'll give you a list of the ones I use

**Google Search**
```
google-chrome "http://www.google.co.uk/search?sourceid=chrome&ie=UTF-8&q=`xsel -p | tr [:space:] +`"
```

**Wikipedia**
```
google-chrome "http://en.wikipedia.org/w/index.php?title=Special:Search&search=`xsel -p | tr [:space:] +`"
```

**Google Images**
```
google-chrome "http://www.google.co.uk/images?hl=en&source=hp&biw=999&bih=581&q=`xsel -p | tr [:space:] +`&gbv=2&aq=f&aqi=&aql=&oq="
```

**Google News**
google-chrome ```
"http://www.google.co.uk/#hl=en&sugexp=llsfp&xhr=t&q=`xsel -p | tr [:space:] +`&cp=3&um=1&ie=UTF-8&tbo=u&tbs=nws:1&source=og&sa=N&tab=wn&fp=2c94a2341fe34a2f"
```

**Amazon**
```
google-chrome "http://www.amazon.co.uk/s/ref=nb_sb_noss?url=search-alias%3Daps&field-keywords=`xsel -p | tr [:space:] +`&x=0&y=0"
```

**Bing Maps**
```
google-chrome "http://maps.google.co.uk/maps?hl=en&q=`xsel -p | tr [:space:] +`&um=1&ie=UTF-8&sa=N&tab=wl"

```
Easystroke is being developed by Tom Jaeger so thankyou Tom and if you have any more hints anyone please write them here

[http://sourceforge.net/apps/trac/easystroke/wiki/TipsAndTricks](http://sourceforge.net/apps/trac/easystroke/wiki/TipsAndTricks)

NOW WE HAVE SCRYBE FOR OUR FAV OS UBUNTU :D

ENTERPART

---

### Post by Sef on 2011-08-30
Moved to Tips and Tutorials.

---

### Post by durand on 2011-08-31
> Thankz durand, you can tell Im a newbie, not use to writting here and thankz for the tips glad you enjoyed that
 
I've got one more tip if your searching on a website with with several other tabs open and use a gesture with this code it will open a new tab at the end (in chrome) and after closing that tab your stuck at the tab at the far right and have to look through to find the one your at
 
the way around is insert the code
--new-window after google-chrome this will open in a new window
 
e.g
 
```
google-chrome --new-window "http://www.youtube.com/results?search_query=`xsel -p | tr [:space:] +`&aq=f"
```
 
and after closing your back on the tab you was on 


Thanks but I use opera anyway :)

---

### Post by Enterpart on 2011-11-02
you can even add in more functionality by adding 8 tap zones controlling key strokes or any commands plus control firefox chrome

[http://ubuntuforums.org/showthread.php?t=1859936]("http://ubuntuforums.org/showthread.php?t=1859936")

---

