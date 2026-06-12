---
title: "Discordian date on top panel?"
date: 2010-11-04
forum: The Cafe
---

### Post by t0p on 2010-11-04
On my top panel the date is displayed, as according to the [Gregorian calendar]("http://en.wikipedia.org/wiki/Gregorian_calendar") (ie Thu 4 Nov).

As I prefer Eris to Greg, I'd like to have the [Discordian calendar]("http://en.wikipedia.org/wiki/Discordian_calendar") date displayed (as can be discovered through the use of the **ddate** command):

```

 t0p@deimos:~$ ddate
Today is Pungenday, the 16th day of The Aftermath in the YOLD 3176

```

As I have to live in Greg's world, I'd like the Discordian date to appear alongside the Gregorian date.

So how do I do that then?

---

### Post by CharlesA on 2010-11-04
Can you add a second date applet to the top panel and modify it the way you want?

---

### Post by koenn on 2010-11-04
according to this ; [http://people.gnome.org/~tvachon/doc/tutorial.html](http://people.gnome.org/~tvachon/doc/tutorial.html)
it shouldn't be too hard to create one - a panel applet is apparently just a piece of python script that's been processed with gebb
So if you can get a py script to run ddate (through some sort of system object probably), your practically there.

---

### Post by JustinR on 2010-11-04
Hi this article will help:
[http://www.omgubuntu.co.uk/2010/10/how-to-customize-the-clock-applet-in-ubuntu/](http://www.omgubuntu.co.uk/2010/10/how-to-customize-the-clock-applet-in-ubuntu/)

Go to - GConf-Editor:

Go to Apps > Panel > Applets > clock_screen_* > prefs:

Change the 'format' key to 'custom'.
In the 'custom_format' key type 'ddate'.

If 'ddate' doesn't work you could try other variations, like having a script output the 'ddate' command to the clock applet.

---

