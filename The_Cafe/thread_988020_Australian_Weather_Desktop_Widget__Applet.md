---
title: "Australian Weather Desktop Widget / Applet ?"
date: 2008-11-20
forum: The Cafe
---

### Post by Rodney9 on 2008-11-20
Hello, I am after a desktop applet, widget or something similar for local city weather here in Australia.

The Weather Report Panel in Gnome is used by weather.com and takes it's forecast from the airport, which is at least 30 Km's away, and so does the forecastfox in firefox and also the Weather Applet in Awn.

They are always incorrect for the metro area, so I would like one that uses capital cities, or even better uses [http://www.bom.gov.au](http://www.bom.gov.au) , Australia's Bureau of Meteorology.

So is there any Australian city weather widget/applet for Linux as in windows and mac ?

Rodney

---

### Post by stinger30au on 2008-11-20
u asked this same question no more then 2 weeks ago dude

with firefox install the forcastfox addon


[https://addons.mozilla.org/en-US/firefox/addon/398](https://addons.mozilla.org/en-US/firefox/addon/398)

---

### Post by stinger30au on 2008-11-20
heres your  original thread

[http://ubuntuforums.org/showthread.php?t=974875](http://ubuntuforums.org/showthread.php?t=974875)

---

### Post by Rodney9 on 2008-11-20
> **stinger30au said:**
> u asked this same question no more then 2 weeks ago dude

with firefox install the forcastfox addon


[https://addons.mozilla.org/en-US/firefox/addon/398](https://addons.mozilla.org/en-US/firefox/addon/398)

> Well I have tried it for a week now and it is always a few degrees out , today it has never gone over 27 even when we reached 32. 
I posted this 4 days ago, the other day it said it was fine and sunny in the middle of a thunderstorm.

I want something accurate and local.

---

### Post by cdekter on 2008-11-20
The main obstacle to using the BOM site for weather data feed is that they don't provide all the information necessary - there is no current condition synopsis (e.g. thundery showers, partly cloudy, fine, etc)

Edit: if there is a Google gadget that could fulfil this need, there are ways of running those in Linux... maybe look into that.

---

### Post by handy on 2008-11-20
> **Rodney9 said:**
> I posted this 4 days ago, the other day it said it was fine and sunny in the middle of a thunderstorm.

I want something accurate and local.

Do you want weather forecasting, or feedback telling you what the weather is doing in your location now?  They are two very different things.

Forecasting will NOT give you accuracy for your current weather situation, as that is not what forecasting does.

If you want to access your current local weather situation, you are going to have to spend some money on sensors that you place outside your house that feed data back to your computer.

There is software available to handle this situation on Linux, but I can't remember what it is called.

---

### Post by mrgnash on 2008-11-20
[This](http://www.weather.com/outlook/travel/businesstraveler/local/ASXX0075?from=enhsearch_loc) is for Melbourne metro, not the airport. Just extract the code (ASXX0075), and use it with your favorite weather-monitoring application/applet/whatever.

---

### Post by Rodney9 on 2008-11-21
> **handy said:**
> Do you want weather forecasting, or feedback telling you what the weather is doing in your location now?  They are two very different things.

Forecasting will NOT give you accuracy for your current weather situation, as that is not what forecasting does.

If you want to access your current local weather situation, you are going to have to spend some money on sensors that you place outside your house that feed data back to your computer.

There is software available to handle this situation on Linux, but I can't remember what it is called.
 
I hope you can remember.

I just want a desktop applet/widget that gives the correct temperature now for Brisbane metro.
(Gnome, forcastfox, Awn and weather-util all use the airport only) 

and if possible the forecast from from [http://www.bom.gov.au/products/IDQ10095.shtml](http://www.bom.gov.au/products/IDQ10095.shtml)

mac and windows have, I presumed Linux would also, but I can't find one.

Rodney.

---

### Post by Rodney9 on 2008-12-03
Any News ?

---

### Post by Rodney9 on 2008-12-12
Anyone know ???

---

### Post by Herman on 2008-12-12
> If you want to access your current local weather situation, you are going to have to spend some money on sensors that you place outside your house that feed data back to your computer.

There is software available to handle this situation on Linux, but I can't remember what it is called.:) he-he, well out here in the bush we're out in it most of the time,  so we can feel it. 
If we're inside and we want to know what the weather's doing currently, we just stick our head out a window and have a look. 

:) ...I don't suppose that's the answer you're looking for though.

For a forecast, (like for the next three or four days), I like [Elders Weather]("http://www.eldersweather.com.au/") page, enter your postcode or name of town in the 'local weather' field for a specific weather forecast for your area.

Really what you need to do is learn how to read clouds and develop an awareness of the winds. That takes practice though.
If you can get your hands on the '[Small Ships Manual]("http://www.boatbooks-aust.com.au/product_info.php?products_id=19487&osCsid=1e4a6c79e9998e754362b8bf8ce01ace&pic=Y")', (Marine Board of Queensland), that has some good information in it. 
Even better, I have a book from the Australian Bureau of Meteorlogy called '[The Wonders of the Weather]("http://www.bom.gov.au/climate/student_teachers/wonders.shtml")', by Bob Crowther. I got it at an ABC shop. It's great, it's entertaining as well as scientific, while at the same time admitting that science doesn't yet have all the answers.

I searched Synaptic Package Manager and found GKrellWeather listed there, would that be anything like what you're looking for?
> GKrellWeather is a plugin for GKrellM that monitors the weather information
given a METAR station identification code. Features include:
 - Temperature, dew point, pressure, relative humidity, sky condition,
   wind direction and speed.
 - Temperatures in degrees Farenheit or Celsius
 - Pressure in kPa, hPa or mmHg
 - Wind speeds in kmph, mps or beaufort scale

---

### Post by Herman on 2009-01-11
:) Hey Rodney9, 
Here's a link you might be interested in, [eldersweather.com.au/radar=qld]("http://www.eldersweather.com.au/radar.jsp?lt=state&lc=qld").
It updates frequently.

---

### Post by thisllub on 2009-01-12
[http://www.bom.gov.au/products/IDQ60900.shtml](http://www.bom.gov.au/products/IDQ60900.shtml)

---

### Post by k3lt01 on 2009-01-14
Take a look at this [link]("http://ubuntuforums.org/showthread.php?t=203274&highlight=australian+weather")

---

### Post by Rodney9 on 2009-11-03
The Gnome weather report in Gnome 2.28.1 still uses the airport weather details.

The airport here in Brisbane is 30 km's away on the coast, the weather there is much differant than in the city.

Temperatures can vary 5 degrees and the wind can be from a totally different direction, the airport might have a storm or fog when Brisbane is clear.

So this panel add-on is useless, it has been the same for several years, with this latest version I hoped they fixed it.

Are there any other desktop widgets or something similar for local weather here in Brisbane, Australia yet ?

Rodney

---

### Post by cariboo on 2009-11-04
HAve you had a look at Gnome-do docky? See the screen shot.

---

### Post by Rodney9 on 2009-11-04
> **cariboo907 said:**
> HAve you had a look at Gnome-do docky? See the screen shot.

No I Haven't, how do you get it started ?

Thank You

---

### Post by Rodney9 on 2009-11-04
I worked out how to start docky, but it uses the airport readings as well.

---

### Post by k3lt01 on 2009-11-04
Rodney, please don't go double posting for the same issue.

You have been given multiple answers in two threads, maybe do a simple search yourself if that doesn't help then you may be out of luck unfortunately.

---

