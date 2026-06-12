---
title: "Good Bye, Weather Indicator"
date: 2012-06-14
forum: The Cafe
---

### Post by buzzingrobot on 2012-06-14
Good bye, little Weather Indicator.  I have removed you from my startup roster. You are a crashy little thing, aren't you?

I guess I'll just look out the window from now on.

---

### Post by VE6EFR on 2012-06-14
I had the same problem. Would run fine for a few hours then crash. No worries though since there are other ways we can get weather data. But it was nice to have it available at a glance.

---

### Post by buzzingrobot on 2012-06-14
> **VE6EFR said:**
> I had the same problem. Would run fine for a few hours then crash. No worries though since there are other ways we can get weather data. But it was nice to have it available at a glance.

I came across this little BASH script that displays weather in a terminal.  Replace the question marks with a zip/post code:

```
curl -s "http://api.wunderground.com/auto/wui/geo/ForecastXML/index.xml?query=${@:-?????}"|perl -ne '/<title>([^<]+)/&&printf "%s: ",$1;/<fcttext>([^<]+)/&&print $1,"\n " ' | fmt -t;
```There are any number of similar scripts around that grab the weather and parse out the relevant text.  I suppose if I was clever I could run this as a cron job and use a notification for the display.

---

### Post by scouser73 on 2012-06-14
It never worked for me when I had installed it.

---

### Post by hansdown on 2012-06-14
> **buzzingrobot said:**
> Good bye, little Weather Indicator.  I have removed you from my startup roster. You are a crashy little thing, aren't you?

I guess I'll just look out the window from now on.

The last time it worked well for me, was 10.04.

The one in mint13 cinnamon is very sleek.

---

### Post by Mikeb85 on 2012-06-14
I could usually have it running for several days at a time before it crashed...  Still always would crash in the end though.

---

### Post by Roasted on 2012-06-14
Neat little terminal trick. I threw together a bash script, put this command in, and added read; exit on the end. Then I set up a hot key (CTRL ALT M) to launch:

```
"gnome-terminal -e weather"
```

and it brings up a terminal with the weather. Once I hit enter, it closes, thanks to the addition of read; exit.

```
#!/bin/bash
curl -s "http://api.wunderground.com/auto/wui/geo/ForecastXML/index.xml?query=${@:-?????}"|perl -ne '/<title>([^<]+)/&&printf "%s: ",$1;/<fcttext>([^<]+)/&&print $1,"\n " ' | fmt -t; read; exit

```

---

### Post by Frogs Hair on 2012-06-14
Check out my weather indicator at the link. Indicator-weather is listed, just go further down the page . I have used this prior to 12.04.    [http://askubuntu.com/questions/30334/what-application-indicators-are-available](http://askubuntu.com/questions/30334/what-application-indicators-are-available)

---

### Post by BigSilly on 2012-06-14
> **Frogs Hair said:**
> Check out my weather indicator at the link. Indicator-weather is listed, just go further down the page . I have used this prior to 12.04.    [http://askubuntu.com/questions/30334/what-application-indicators-are-available](http://askubuntu.com/questions/30334/what-application-indicators-are-available)

That's excellent, thank you. :)  Just installed on 12.04 no problem.

---

### Post by VE6EFR on 2012-06-14
> **Frogs Hair said:**
> Check out my weather indicator at the link. Indicator-weather is listed, just go further down the page . I have used this prior to 12.04.    [http://askubuntu.com/questions/30334/what-application-indicators-are-available](http://askubuntu.com/questions/30334/what-application-indicators-are-available)

I'm pretty sure that's the one that I was running that was crashing all the time on 12.04 LTS. Maybe the OP can chime in to confirm if that was the same one they were running.

---

### Post by BigSilly on 2012-06-14
> **VE6EFR said:**
> I'm pretty sure that's the one that I was running that was crashing all the time on 12.04 LTS. Maybe the OP can chime in to confirm if that was the same one they were running.

It's the same one? D'oh!

I'll keep an eye on it. Thanks for the heads up.

---

### Post by Frogs Hair on 2012-06-14
Indicator-weather from the repository and My Weather Indicator are both listed at the link.

---

### Post by buzzingrobot on 2012-06-14
> **VE6EFR said:**
> I'm pretty sure that's the one that I was running that was crashing all the time on 12.04 LTS. Maybe the OP can chime in to confirm if that was the same one they were running.

Nope, that's a different one.

---

### Post by PC_load_letter on 2012-06-15
> **hansdown said:**
> The last time it worked well for me, was 10.04.

The one in mint13 cinnamon is very sleek.

I was just about to post exactly that :D Not only it looks purdy but it's very stable, even more so than Cinnamon itself LOL

---

### Post by VE6EFR on 2012-06-15
I have installed the one that Frogs Hair provided the link to. It has been running without a problem so far. It's possible that the one that I was running previously that had stability issues was a different weather indicator.

I did find one thing that is rather odd. The source for the current weather doesn't seem to be very accurate. At least not for Edmonton, AB. There is a 3 degree C difference in what the weather indicator is showing (just refreshed) than what is showing on the Environment Canada website. I have changed the prefs to grab from yahoo to Google and it is still not showing the correct temp.

---

### Post by Kantis on 2012-06-15
Haven't used Weather Indicator in ages. ForecastFox does the job just fine.

---

### Post by VE6EFR on 2012-06-15
I spoke too soon. Got the error message when I returned to my computer that there was a problem and then it shut itself down.

---

### Post by darrenn on 2012-06-15
Works perfect on 10.04 hopefully, eventually they will fix it on 12.04.

---

### Post by Bandit on 2012-06-15
I just spars the text from a weather website and use it with conky to display a 5 day forcast.

---

### Post by fisch246 on 2012-06-16
I actually miss the weather indicator from 10.04, I used it quite a bit. Never crashed for me. Yet I don't want to go back to 10.04 because I hated the panel system back then. So buggy.

---

### Post by Frogs Hair on 2012-06-16
I have used both indicators I wrote about with no problems on 12.04 . I have tried Opera widgets and Screenlets on other releases also.
There are two more options at the link. [http://askubuntu.com/questions/149707/desktop-weather-app-for-ubuntu-12-04](http://askubuntu.com/questions/149707/desktop-weather-app-for-ubuntu-12-04)

---

### Post by scouser73 on 2012-06-16
Managed to get Weather Indicator extension up and running under Gnome 3.

---

### Post by Primefalcon on 2012-06-16
try my-weather-indicator

its a bit more comprehensive

---

