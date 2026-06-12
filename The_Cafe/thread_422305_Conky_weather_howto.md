---
title: "Conky weather howto?"
date: 2007-04-25
forum: The Cafe
---

### Post by jackmc on 2007-04-25
can someone give me a hand setting up a conky weather section? Ic ant figure it out...

---

### Post by nphx on 2007-04-25
I don't have that complex of a conky script, but you can check out this thread it has conky scripts with screenshots:

[http://ubuntuforums.org/showthread.php?t=281865&highlight=conky](http://ubuntuforums.org/showthread.php?t=281865&highlight=conky)

And here are the variables for conky:
[http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)

---

### Post by jackmc on 2007-04-25
That thread gave me the idea to do it :)

I cant figure it out though :(

---

### Post by nphx on 2007-04-25
Here is a nice howto from suse forums:

[http://www.suseforums.net/index.php?showtopic=24669](http://www.suseforums.net/index.php?showtopic=24669)

Conky just displays output from scripts. Grap the script for the weather and conky and put them together.

---

### Post by reclusivemonkey on 2007-04-25
[http://conky.sourceforge.net/screenshots.html](http://conky.sourceforge.net/screenshots.html)

On the next to bottom row, the first example (dark blue) has a weather section. Its got a weather.tar.gz for you to download; I presume you just change the location code. HTH

---

### Post by jackmc on 2007-04-25
still cant get it to work :(

my weather section comes up blank. I'll have another snoop around.

---

### Post by halitech on 2007-04-25
do you have curl install and have the weather.sh script to look in the correct location?

---

### Post by jackmc on 2007-04-25
> **halitech said:**
> do you have curl install and have the weather.sh script to look in the correct location?

Thanks, thats what I needed :)

---

### Post by jedinyt on 2007-06-24
I was trying to put weather too in my conky and i have an output 
No location provided.  

here's in my weather.sh

LOCID$=$94015

here's in my .conkyrc

${execi 1800 /home/jacen/weather/weather.sh 94015}

Please help...thanks!

---

### Post by scapalexis888 on 2007-08-05
heres a guide:

[http://gnome-look.org/content/show.php/My+Conky+Config?content=62536&PHPSESSID=9f24f7fdf3](http://gnome-look.org/content/show.php/My+Conky+Config?content=62536&PHPSESSID=9f24f7fdf3)

Just follow the instructions from the author (6th comment)

---

### Post by brjschwedler on 2007-11-28
If you would like an alternate data source other than weather.com, I have put together a script that will pull from the National Weather Service and display data from there.
You can download it at [http://www.meteor.iastate.edu/~bschwedl/nwsweather.tar.gz]("http://www.meteor.iastate.edu/~bschwedl/nwsweather.tar.gz")
It works the same way as the other weather script, but pulls from the Weather Service Source.

---

### Post by rrr0321 on 2008-01-04
I am also struggling to get the weather to appear in Conky. When Conky launches it displays 'No Location Provided'. I have read every post that I can find on this subject with no luck. I attach all of my Conky scripts to this post in the hope someone can help me figure out what is wrong.

---

### Post by John.Michael.Kane on 2008-01-04
> **rrr0321 said:**
> I am also struggling to get the weather to appear in Conky. When Conky launches it displays 'No Location Provided'. I have read every post that I can find on this subject with no luck. I attach all of my Conky scripts to this post in the hope someone can help me figure out what is wrong.

Have you tried?
```
http://xoap.weather.com/search/search?where=[your city entered here] 
```

The above outputs your location id.

You would then add that location id/zip to your weather.sh file where it says
```
LOCID=
```

Next you would add a line to your conky pointing to your weather folder. while making sure to add your zip or location id to it as shown below .

Example line.
```
${execi 60 ~/Documents/weather/weather.sh "your zip or location id"}
```

You will also need to install curl.
```
gksudo aptitude install curl
```

Also make sure 'weather.sh' executable as well,To do so simply right click on it go to properties > permissions > check 'execute' box

---

### Post by ODF on 2008-01-04
How come Montréal is not there ? Its the second biggest city in Canada, it can't be hehe.

---

### Post by MikeCheck on 2008-03-27
I am struggling to get a forecast for the current day.  I can get tomorrow's forecast. but I want today's.  Has anyone been able to accomplish this?

---

### Post by andrewabc on 2008-03-27
Any Canadian users want environment canada weather forecasts and satellite and radar possibilities? I would definitely like this. Especially radar.
Something simple to implement such as [yahoo widget for canadian radar?](http://widgets.yahoo.com/widgets/weather-radar-for-canada)

---

### Post by MikeCheck on 2008-03-31
> **MikeCheck said:**
> I am struggling to get a forecast for the current day.  I can get tomorrow's forecast. but I want today's.  Has anyone been able to accomplish this?

I am still trying this.  Does anyone have suggestions?  Looking at where the data is coming from([http://xoap.weather.com/weather/local/50014?dayf=3&unit=s](http://xoap.weather.com/weather/local/50014?dayf=3&unit=s)), it seems like I could just replace d="1" with d="0"
That doesn't work for some reason.  Any other suggestions?

---

### Post by Jaymac on 2008-05-07
Might not be relevant anymore, but I came across this thread whilst looking for the conkyrc thread :)

> **jedinyt said:**
> I was trying to put weather too in my conky and i have an output 
No location provided.  

here's in my weather.sh

LOCID$=$94015

here's in my .conkyrc

${execi 1800 /home/jacen/weather/weather.sh 94015}

Please help...thanks!

You can probably leave the LOCID as it is:

```
LOCID=$1
```

This way, it will call it from the code passed in your second line... 

```
${execi 1800 /home/jacen/weather/weather.sh 94015}
```

I've attached my weather.sh file to show you what I mean.  The only lines I have edited are the following:

```
# s=standard units, m=metric units
UNITS=m

# where this script and the XSLT lives
RUNDIR=/home/john/.conky/
```

Here is the line from my conkyrc:

```
${execi 1800 /home/john/.conky/weather.sh UKXX0025}
```

---

### Post by Craig73 on 2008-07-13
> **andrewabc said:**
> Any Canadian users want environment canada weather forecasts and satellite and radar possibilities? I would definitely like this. Especially radar.
Something simple to implement such as [yahoo widget for canadian radar?](http://widgets.yahoo.com/widgets/weather-radar-for-canada)

Did you figure this out? 

You can get an RSS feed of the weather forcast from Environment Canada ([http://www.weatheroffice.gc.ca](http://www.weatheroffice.gc.ca)) by finding your forcast and clicking on the CSS link at the at the bottom ([http://www.weatheroffice.gc.ca/rss/city/on-82_e.xml](http://www.weatheroffice.gc.ca/rss/city/on-82_e.xml))

I found a script elsewhere that parses XML for Conky so a script should be straight forward...

---

### Post by andrewabc on 2008-07-14
> **Craig73 said:**
> Did you figure this out? 

You can get an RSS feed of the weather forcast from Environment Canada ([http://www.weatheroffice.gc.ca](http://www.weatheroffice.gc.ca)) by finding your forcast and clicking on the CSS link at the at the bottom ([http://www.weatheroffice.gc.ca/rss/city/on-82_e.xml](http://www.weatheroffice.gc.ca/rss/city/on-82_e.xml))

I found a script elsewhere that parses XML for Conky so a script should be straight forward...

I hope someone is able to do it :)
I don't have any programming skills. :O

---

### Post by ben2talk on 2009-04-08
The instructions are a little vague - I'm totally stuck after looking and messing for three or four hours now...

---

### Post by tonytraductor on 2009-05-09
I just did
${execi 300 weather -i -v HVN}

Works fine.

You need to have weather installed.
(apt-get weather)

---

### Post by DeMus on 2009-10-10
This is my present conky screen, with the weather forecast at the bottom.
I also include my .conkyrc file.

---

### Post by carloscmt on 2011-05-09
how do you start your conkyforecast? what do you type on terminal? I am a beginner. Thank You.

---

