---
title: "What is so difficult about a weather app?"
date: 2013-10-22
forum: The Cafe
---

### Post by coldraven on 2013-10-22
I cannot believe that a simple thing like a weather app is hard to find.
The app in the Software Centre is broken even though Launchpad says that it's fixed. When trying to add a location you get to "Apply" then it hangs and generates "Ubuntu had an internal error".

indicator-weather 11.11.28-0ubuntu1.3
I'm running a fully updated Ubuntu 12.04
```
$ uname -a
Linux snappy 3.8.0-32-generic #47~precise1-Ubuntu SMP Wed Oct 2 16:19:35 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```
I have reported this at Launchpad but I still cannot find a solution.

On AskUbuntu there are various answers but none of these "weather" apps show me want I want to know. 
[http://askubuntu.com/questions/149707/is-there-a-desktop-weather-app](http://askubuntu.com/questions/149707/is-there-a-desktop-weather-app)
I want to know the wind speed and direction for the day. Where I live the weather is determined by the speed and direction of the wind and it changes quite often.
The technical term for it is "hyper-oceanic". For the current wind direction I can look out of the window, I want to know what it's going to do later.

Maybe I should learn how to setup Conky :)
Any ideas? </moderate_rant_level>

---

### Post by Docaltmed on 2013-10-22
my-weather-indicator is pretty comprehensive.

```
sudo apt-get install my-weather-indicator
```

---

### Post by monkeybrain20122 on 2013-10-22
> **Docaltmed said:**
> my-weather-indicator is pretty comprehensive.

```
sudo apt-get install my-weather-indicator
```

You need to add the ppa first. It is not in the repository as far as I remember.

---

### Post by Docaltmed on 2013-10-22
ah, you are correct, monkeybrain. It's been a while and I forgot. It's the atareao repository.

```
sudo add-apt-repository ppa:atareao/atareao
sudo apt-get update
sudo apt-get install my-weather-indicator
```

---

### Post by buzzingrobot on 2013-10-22
Weather  apps aren't especially difficult.  I assume their apparent dearth is due to lack of interest. It's isn't unusual in FOSS for small single-purpose apps to be written more or less as learning experiences and then abandoned.

Every one I've seen works the same way:  Ask the user to identify a location, grab the current forecast/conditions from an online source, parse the text that's returned, and display it in a pop up adorned with cute weather images.

A large number of shell script incarnations of these are scattered across the web that can be executed in a terminal.  Not as pretty, but probably more informative.

I just point my browser at a good weather site.  Here in the U.S. it's one of the NOAA sites, in the UK it's the Met Office, and so on.

---

### Post by Yellow Pasque on 2013-10-22
One of the tough things is that free weather providers (like weather.com) will shut down their services, so there are some good weather applets/scripts out there that are currently broken until they're updated to a new provider. I had a tough time finding a good weather app in KDE, but at least the xfce weather app works nicely.

---

### Post by SeijiSensei on 2013-10-22
I just use the [ForecastFox]("http://www.getforecastfox.com/") plug-in for Firefox.  It's very configurable.  I get a few icons in the status bar at the bottom of the Firefox window.

There are also a couple of "widgets" in KDE for weather.  Out of curiosity I installed the "Weather Forecast" widget into the panel.  It's fairly functional as well, though configuration was a bit mysterious to start with.  If you right-click the widget and choose Settings, you'll see a dialog box with an empty field to specify the weather station to monitor.  It turns out you need to type in a city name, then press Search to get a list of options.

I use [WeatherBug]("http://weather.weatherbug.com/") on my Android phone, which taps into a network of small weather stations.  The one for my community is located at the high school about half-a-mile away; can't get much more local than that.  My daughter attends college in Philadephia.  The station for her is located at a private school across the street from her campus.  Apps like the KDE widget rely on things like NOAA where the stations are at airports.  For Boston, that's at Logan Airport which is out in the harbor and often has different weather from those of us more inland.  There is a beta [desktop WeatherBug app]("http://weather.weatherbug.com/labs/linux.html") for Linux, but the site says it is currently not available for downloading.

---

### Post by ian-weisser on 2013-10-22
> **Temüjin said:**
> [...]free weather providers (like weather.com) will shut down their services, so there are some good weather applets/scripts out there that are currently broken[...]

Exactly. And most free providers (when available) offer different types of data. Also, data type and quality varies from continent to continent.

So a developer has two choices: Either create a quite complex three-layer application (provider plug-in, abstraction, display), or create a very simple two-layer application (single-provider, display). No big surprise that after looking at the issues, most developers decided upon the latter.

---

### Post by buzzingrobot on 2013-10-22
Commerical sites, like weather.com, have an interest in not making it easy for third-parties to collect and repackage their data.  They want to make sure their ads get through.

What I want more than an applet that provides the current conditions and a forecast -- I get that by plugging my zipcode into weather.gov once a day -- is something that alerts me to localized severe and dangerous weather. E.g., if a tornado or severe thunderstorm warning is issued near me, I want something to beep and popup.  There are phone apps for this, usually from local TV stations, but I'm not aware of any on Linux.

---

### Post by coldraven on 2013-10-22
Thanks for all the replies and tips. Maybe I should just install bigger windows :)

---

### Post by tgalati4 on 2013-10-22
Why rely on others?  Install your own super-computer weather forecasting system and predict your own weather.

Some interesting apps in this thread:  [http://ubuntuforums.org/archive/index.php/t-226686.html](http://ubuntuforums.org/archive/index.php/t-226686.html)

---

### Post by ian-weisser on 2013-10-22
> **buzzingrobot said:**
> [...]I get that by plugging my zipcode into weather.gov once a day[...]

So you use NOAA data. The USA is one of those data-rich environments, and pulling customized information from the National Weather Service is easy. All you need are the customized http and ftp URLs.

> **buzzingrobot said:**
> What I want [...] is something that alerts me  to localized severe and dangerous weather. E.g., if a tornado or severe  thunderstorm warning is issued near me, I want something to beep and  popup.  There are phone apps for this, usually from local TV stations,  but I'm not aware of any on Linux.

Easy in the United States, which is divided into alert zones roughly matching most counties, and has a public RSS feed of alerts.

Ugh. One of these days, I really do need to get back to work on my US weather application...

---

### Post by buzzingrobot on 2013-10-22
> **ian-weisser said:**
> 

Easy in the United States, which is divided into alert zones roughly matching most counties, and has a public RSS feed of alerts.



Right, and I have the local one in my reader. The reader, thought, doesn't go "BZZZT!" when a new alert has been issued. I know how to conjure one up by hand, but I'm too lazy.

I hafta say my favorite weather applet was the old Gnome 2 (now Mate) gizmo, the one with the radar map that simply displayed the text of the current local forecast. Much more informative than the current trend of taking up most of the space with big graphics to illustrate the current weather.

---

### Post by SeijiSensei on 2013-10-23
The ForecastFox addon puts an icon the browser's status bar for the radar.  If you hover over it, you get a nicely-sized pop-up window.  If you click it, it takes you to the AccuWeather radar page for your location.

The temperature and forecast are not superimposed, though.  You have to hover over the adjacent icon for that.

If you have a browser open nearly all the time, as I do, ForecastFox is pretty convenient.

---

### Post by GWBouge on 2013-10-24
> **SeijiSensei said:**
> The ForecastFox addon puts an icon the browser's status bar for the radar.  If you hover over it, you get a nicely-sized pop-up window.  If you click it, it takes you to the AccuWeather radar page for your location.

Another vote here for ForecastFox.  I started using it just because it was the only one I found that gave a radar without having to goto a website, but like you said, if you've got a browser open all the time anyways it's really convenient.

> The temperature and forecast are not superimposed, though.  You have to hover over the adjacent icon for that.

Does it not give you those options?  I don't usually have the forecast enabled (just current temp and radar), but here's a screenshot with current temp, and 2-day day/night forecast:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=247195&d=1382591098[/IMG]

---

### Post by SeijiSensei on 2013-10-24
I hide the texts that accompany the icons to save space.  Then you'll see the forecast but have to hover over the icon to pop up details.

However I just discovered you can select the number of days out for which the temperature is hidden.  I just added it to the most current icon.

---

### Post by ikt on 2013-10-24
[http://www.omgubuntu.co.uk/2012/10/gorgeous-new-weather-app-stormcloud-arrives-on-ubuntu](http://www.omgubuntu.co.uk/2012/10/gorgeous-new-weather-app-stormcloud-arrives-on-ubuntu)

Stormcloud is pretty neat, I used it before switching to Pocket Weather on my phone.

---

### Post by coldraven on 2013-10-25
> **SeijiSensei said:**
> The ForecastFox addon puts an icon the browser's status bar for the radar.  If you hover over it, you get a nicely-sized pop-up window.  If you click it, it takes you to the AccuWeather radar page for your location.

The temperature and forecast are not superimposed, though.  You have to hover over the adjacent icon for that.

If you have a browser open nearly all the time, as I do, ForecastFox is pretty convenient.

I just tried forecastfox but I did not like it's reliance on javascript. When I enabled it I saw that it uses Google APIs, I'm not keen on giving my location to them. (I use NoScript extensively)
I will just look at the BBC for my weather although the NSA/GCHQ probably have a feed there already they don't bombard me with adverts :(

MagicSeaweed have good animated wind speed charts, it's a surfer site.
[http://magicseaweed.com/MSW-Surf-Chart/1/?imageScale=wind&chartType=WMAG#](http://magicseaweed.com/MSW-Surf-Chart/1/?imageScale=wind&chartType=WMAG#)

---

### Post by RichardET on 2013-10-25
> **Docaltmed said:**
> ah, you are correct, monkeybrain. It's been a while and I forgot. It's the atareao repository.

```
sudo add-apt-repository ppa:atareao/atareao
sudo apt-get update
sudo apt-get install my-weather-indicator
```

I added this - its pretty good.

---

### Post by ian-weisser on 2013-10-25
> **buzzingrobot said:**
> What I want [...] is something that alerts me to localized severe and dangerous weather. E.g., if a tornado or severe thunderstorm warning is issued near me, I want something to beep and popup.  There are phone apps for this, usually from local TV stations, but I'm not aware of any on Linux.

Aha! I finally found it. I wrote something along those lines recently for NOAA data.
A shell script that does the alert popup is at the bottom of [http://cheesehead-techblog.blogspot.com/2012/09/us-national-weather-service-info-feeds.html](http://cheesehead-techblog.blogspot.com/2012/09/us-national-weather-service-info-feeds.html)
It does not do the sound, though that would be very easy to add.

---

### Post by buzzingrobot on 2013-10-25
> **ian-weisser said:**
> Aha! I finally found it. I wrote something along those lines recently for NOAA data.
A shell script that does the alert popup is at the bottom of [http://cheesehead-techblog.blogspot.com/2012/09/us-national-weather-service-info-feeds.html](http://cheesehead-techblog.blogspot.com/2012/09/us-national-weather-service-info-feeds.html)
It does not do the sound, though that would be very easy to add.

Cool! Thanks, Ian. I shall play with your code.

---

### Post by b|ackhole on 2013-10-27
> **Docaltmed said:**
> 

```
sudo add-apt-repository ppa:atareao/atareao
sudo apt-get update
sudo apt-get install my-weather-indicator
```

So I installed this to check it out and I like how it stays neat up in the top and shows the temprature and a small icon representing the weather.  However I had earlier gotten a a wiget that sits on my desktop for weather that I liked.  It's actually the *only* thing I use out of Screenlets ([https://apps.ubuntu.com/cat/applications/screenlets/](https://apps.ubuntu.com/cat/applications/screenlets/)) because I could not for the life of me get Conkey to run smoothly no matter how I tried.

---

### Post by b|ackhole on 2013-10-27
I figured out how to edit images, so this is what it looks like on my desktop with Screenelts' weather app:

[IMG]http://i.imgur.com/to1wn6m.png[/IMG]

Note, I just have the widget's transparency down a bit so it's subtle, and expanded to a full forecast.

---

### Post by Uncle Spellbinder on 2013-10-27
I can't endorse ForecastFox. It uses AccuWeather as it's weather source and is notoriously inaccurate. Sometimes by as many as 10 degrees (F).

---

### Post by tgalati4 on 2013-10-27
I've noticed that AccuWeather's forcast is based on zipcode (in the US) and if you don't live near the center of the zipcode, then your forecast could be off due to microclimate effects.  Try choosing a neighboring zipcode that more closely matches your microclimate and you will see more consistent forecasts.

---

### Post by ian-weisser on 2013-10-27
In the US, the NWS National Digital Forecast Database ( [http://www.nws.noaa.gov/ndfd/](http://www.nws.noaa.gov/ndfd/) ) SOAP server contains a point forecast for every cell in a 2km x 2km grid covering the entire lower 48 states, including inland water and lakes. Some elements are also available for Alaska, Hawaii, Puerto Rico, Etc.

Use Lat/Lon to specify the grid you want. Example: 
[http://graphical.weather.gov/xml/SOAP_server/ndfdXMLclient.php?whichClient=NDFDgen&lat=38.99&lon=-77.01&product=glance&begin=2004-01-01T00%3A00%3A00&end=2016-09-04T00%3A00%3A00&Unit=e&maxt=maxt&pop12=pop12&sky=sky&wx=wx&wwa=wwa](http://graphical.weather.gov/xml/SOAP_server/ndfdXMLclient.php?whichClient=NDFDgen&lat=38.99&lon=-77.01&product=glance&begin=2004-01-01T00%3A00%3A00&end=2016-09-04T00%3A00%3A00&Unit=e&maxt=maxt&pop12=pop12&sky=sky&wx=wx&wwa=wwa)

The return is XML, your program picks out the data you want.
Free, of course.
Very handy for picking out critical data programmatically: High probability of precip, high winds, etc.

---

### Post by rosswmcgee on 2013-10-28
Switch to Ubuntu gnome and put the app on your tool bar. I have used Ubuntu 12.04 for a long time and finally decided I like the Gnome desktop best. I had the same

problem with weather and did all kinds of fixes that worked for awhile then crashed. No problems with Gnome. Remember win/alt is how you move icons on the tool bar in Gnome

---

### Post by neu5eeCh on 2013-10-31
A little late to this conversation, but was looking for a solution to the same problem [at about the same time]("http://ubuntuforums.org/showthread.php?t=2183650"). I'm running Netrunner (modified Kubuntu) after using XFCE for several cycles. The XFCE4-Panel provides the XFCE4-Weather-Plugin -- the best weather applet I've ever used. Since XFCE is modular, it dawned on me that I could install the XFCE panel (very lightweight) and then have access to the applet. It's not as elegant looking as some others, but its far more comprehensive (including wind speed, direction, etc...), and better laid out than any other weather app I'm aware of.

---

