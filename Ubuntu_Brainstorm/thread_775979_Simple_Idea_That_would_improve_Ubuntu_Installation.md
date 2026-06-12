---
title: "Simple Idea That would improve Ubuntu Installations"
date: 2008-04-30
forum: Ubuntu Brainstorm
---

### Post by jdholifield on 2008-04-30
...Well the idea seems simple to me.  I bet other people would appreciate it.

You know in the installation the screen where you are supposed to pic your timezome ?  It seems to me that there are really not enough choices for timezones.  For example, I live in Alabama and there is not a city in Alabama for me to easily choose and I can't easily choose GMT-5.

I really have no idea what it would take to implement something like that, but it seems that if there were more choices of cities that would go a long way toward making it better.

---

### Post by smartboyathome on 2008-04-30
I think that as long as you have a choice of city in your country/timezone, then it is fine, as it doesn't really set your location. Though maybe it is just me, as maybe that is confusing.

---

### Post by jdholifield on 2008-04-30
Yes its confusing.  For example, I have to select Chicago to get the correct timezone, but Chicago is a thousand miles away from where I live, I've never been there, and I have no idea at all if its in the same timezone as me or what.  

Ubuntu should either add a reasonable number of cities to the map thing that you pick with, or else just add something where I can pick GMT-5 and be done with it without having to be a geography expert to get the right timezone.

---

### Post by Mason Smith on 2008-04-30
You can always change your timezone after installation, If you live in the United States your three choices are Central, Eastern and Pacific. You just select the timezone that best matches yours.

---

### Post by Neon Lights on 2008-05-01
I really think it should just be a map of the world split into timezones, and you just click in your timezone.

---

### Post by CREEPING DEATH on 2008-05-01
> **Mason Smith said:**
> You can always change your timezone after installation, If you live in the United States your three choices are Central, Eastern and Pacific. You just select the timezone that best matches yours.

What about Mountain?!?!?!?!?

CD

---

### Post by ccw on 2008-05-01
> **jdholifield said:**
> ...Well the idea seems simple to me.  I bet other people would appreciate it.

You know in the installation the screen where you are supposed to pic your timezome ?  It seems to me that there are really not enough choices for timezones.  For example, I live in Alabama and there is not a city in Alabama for me to easily choose and I can't easily choose GMT-5.

I really have no idea what it would take to implement something like that, but it seems that if there were more choices of cities that would go a long way toward making it better.

Adding every city into the mix would make it exceedingly complex and prone to errors...

Here is information about the underlying database:

[http://en.wikipedia.org/wiki/Tzdata](http://en.wikipedia.org/wiki/Tzdata)
[http://en.wikipedia.org/wiki/Tzdata#Names_of_time_zones](http://en.wikipedia.org/wiki/Tzdata#Names_of_time_zones)
[http://en.wikipedia.org/wiki/List_of_zoneinfo_timezones](http://en.wikipedia.org/wiki/List_of_zoneinfo_timezones)

---

### Post by Talon2 on 2008-05-03
> **jdholifield said:**
> 
You know in the installation the screen where you are supposed to pic your timezome ?  It seems to me that there are really not enough choices for timezones.  For example, I live in Alabama and there is not a city in Alabama for me to easily choose and I can't easily choose GMT-5.

I really have no idea what it would take to implement something like that, but it seems that if there were more choices of cities that would go a long way toward making it better.

I suggested this after 7.04 and 7.10.  Others have suggested this.  Nothing has happened.

The fundamental issue here is that the required information is not what is being asked for.  The required information is:  What time zone do you want to set?  However that is not what is being presented to the user.  I live in Arkansas (USA) and I am not interested in selecting Chicago.  I know exactly what time zone I live in and would prefer to answer that question.

---

### Post by Talon2 on 2008-05-03
> **Mason Smith said:**
> If you live in the United States your three choices are Central, Eastern and Pacific. You just select the timezone that best matches yours.

Ummm... 

The United States uses nine standard time zones. From east to west they are Atlantic Standard Time (AST), Eastern Standard Time (EST), Central Standard Time (CST), Mountain Standard Time (MST), Pacific Standard Time (PST), Alaskan Standard Time (AKST), Hawaii-Aleutian Standard Time (HST), Samoa standard time (UTC-11) and Chamorro Standard Time (UTC+10).

...and there should not be any "select the time zone that best matches yours" as you should be able to select the EXACT time zone that is yours.  All time zones around the world have names or descriptions that make selecting your time zone a fairly simple process--if only Ubuntu was designed this way.

---

### Post by Talon2 on 2008-05-03
> **Neon Lights said:**
> I really think it should just be a map of the world split into timezones, and you just click in your timezone.

Bingo!  I agree with this statement.  Does anyone know what project contains this part of the installer so we can make some noise?

---

### Post by smartboyathome on 2008-05-04
The problem with just splitting the map into timezones is that it would leave out the other half that this portion of the installer does: select your language based on where you live. It would be better to have it divided into country/timezone, not just timezone.

---

### Post by [h2o] on 2008-05-04
Physical timezones (equally large areas of the globe) are not always followed by the countries that are situated in them.
Look at [http://www.worldtimezone.net/wtz008.php](http://www.worldtimezone.net/wtz008.php) for one example:
France and Spain which are located in the GMT+0 zone, is actually using the same time as Germany which is clearly in the GMT+1 zone.

Add to that daylight savings time, which I think might differ between quite a lot of countries, and you quickly realize that just using a "GMT+X" timezone is really not an option for a lot of people.

---

### Post by Neon Lights on 2008-05-04
I'm confused...France and Spain /are/ in GMT+1, along with Germany. Time zones aren't split straight down, they're curved.

---

### Post by [h2o] on 2008-05-04
> **Neon Lights said:**
> I'm confused...France and Spain /are/ in GMT+1, along with Germany. Time zones aren't split straight down, they're curved.
Which was kind of my point :)

There are political reasons why that is the case. Exactly which I do not know, but that is not really intersting either. What is interesting is that just splitting the world into timezones and letting people choose a "GMT+X" option is just not a good idea.

---

### Post by Talon2 on 2008-05-05
> **'[h2o] said:**
> Which was kind of my point :)
What is interesting is that just splitting the world into timezones and letting people choose a "GMT+X" option is just not a good idea.

h2o, I respectfully submit that the world is already split into time zones.  The operating system has code in it that uses time zone information.  The installer should be asking for the information that it needs which is time zone, not some city.  What we have in the installer is somebody's great idea that is really not so great because it takes a rather simple concept and turns it into something that is far more complicated than is necessary.

---

### Post by [h2o] on 2008-05-05
> **Talon2 said:**
> h2o, I respectfully submit that the world is already split into time zones.  The operating system has code in it that uses time zone information.  The installer should be asking for the information that it needs which is time zone, not some city.  What we have in the installer is somebody's great idea that is really not so great because it takes a rather simple concept and turns it into something that is far more complicated than is necessary.

Did you actually read what I wrote? Choosing a timezone is not a good solution.
Look at the link I gave in my previous post and think for a moment how happy European users would be if you only chose a timezone and not country.

The time used by a country (or part of a country even) is decided by many factors:
* Physical location
* Politics (might be a good idea to have the same time in the entire country, or same as neighbours)
* Daylight savings time

To me, the current setup works quite well. But then we have the same time in the entire country (Sweden), so I just choose "Sweden/Stockholm" and be done with it.
If the "Country/City" does not work for people in the US, then perhaps you could figure out another "Country/X" identifier that could work (X being timezone, state, or whatever).

---

### Post by smartboyathome on 2008-05-05
Also, no one else is considering that it sets your locale based on what city you choose. For example, one time I chose Vancouver, British Columbia (I live in washington, that is closer than california), and Ubuntu was set to Canadian English. I had to do dirty workarounds to fix it. I think that it should say (don't know if it does) "Please select the appropriate city that is in your country and timezone".

---

### Post by ccw on 2008-05-06
> **Talon2 said:**
> I live in Arkansas (USA) and I am not interested in selecting Chicago.

Now that's ridiculous. You are not pledging allegiance to the Windy City.

I live in the Philly burbs and select New York City without any reservation.

Here's how the zone info is divided up:

1) Country
2) Time zone
3) regionalized daylight saving/ summer time rules
4) Pick a representative city within the region.

3 is particularly important... In the US for example:
Arizona is in mountain time, but doesn't observe DST, except on the navajo reservation. There's weirdness in Indiana and Kentucky, territories in the Carribean don't observe DST, there's a bill in the Florida legislature to abolish DST there, etc, etc.

Its constantly changing, Most updates for the tzdata package are because some political entity changed time rules somewhere.

---

### Post by zekopeko on 2008-05-06
i don't know why all the fuss. Mac OS X has this whole "mess" figured rather nicely ([http://upload.wikimedia.org/wikibooks/en/6/69/Tiger_System_Preferences_Date_&_Time_Time_Zone.png](http://upload.wikimedia.org/wikibooks/en/6/69/Tiger_System_Preferences_Date_&_Time_Time_Zone.png)).

so why don't we just do it like they do it? take picture like the following ([http://www.theodora.com/maps/new9/time_zones_4.jpg](http://www.theodora.com/maps/new9/time_zones_4.jpg)). strip all of the info that we don't need and simply highlight all of the cities in the specific/selected timezone and be done with it. easy as pie.

---

### Post by jdholifield on 2008-05-06
> **ccw said:**
> Now that's ridiculous. You are not pledging allegiance to the Windy City.

Its not ridiculous.

Sure its the same Time Zone, but to someone performing the install its not at all clear what you're expected to do.

If you gave your mother an Ubuntu CD to install on her computer, would she know "Well this city is in my timezone" or would she wonder what the heck she was supposed to do ?

It seems to me that the Ubuntu team has taken great pains to make it easy to install, but choosing a city is confusing and makes that portion of the installer stick out like a sore thumb.

---

### Post by smartboyathome on 2008-05-06
> **zekopeko said:**
> i don't know why all the fuss. Mac OS X has this whole "mess" figured rather nicely ([http://upload.wikimedia.org/wikibooks/en/6/69/Tiger_System_Preferences_Date_&_Time_Time_Zone.png](http://upload.wikimedia.org/wikibooks/en/6/69/Tiger_System_Preferences_Date_&_Time_Time_Zone.png)).

so why don't we just do it like they do it? take picture like the following ([http://www.theodora.com/maps/new9/time_zones_4.jpg](http://www.theodora.com/maps/new9/time_zones_4.jpg)). strip all of the info that we don't need and simply highlight all of the cities in the specific/selected timezone and be done with it. easy as pie.

This is basically how we have it. Only difference would be to highlight the timezone (which, in all honestly, shouldn't be that hard to even code in, we already have the zoom portion coded).

---

### Post by newb1e on 2008-05-06
Maybe I know nothing, but, could the installer just ask "What time is this? I need to synchronize my clock":D then based on that, make a list of available cities for the user to choose (make sure every country/region has at least a city in a timezone).

Would it be more user-friendly than presenting a world map?

---

### Post by zekopeko on 2008-05-06
no we don't have it like the macosx. you zoom and select the city. the timezone is then selected automatically. first select the timezone ala the first pic and simply then allow the user to zoom the relevant part of the highlighted zone so that he can find the blasted city that he lives in or is near.
if the user doesn't know what timezone he is in then what is he doing with a complex thing as a computer in the first place?

EDIT: ok to show the uber-coolness of macosx timezone selector. you can click on the approximate location of your location and it simply selects the timezone you are in

---

### Post by qamelian on 2008-05-06
> **zekopeko said:**
> no we don't have it like the macosx. you zoom and select the city. the timezone is then selected automatically. first select the timezone ala the first pic and simply then allow the user to zoom the relevant part of the highlighted zone so that he can find the blasted city that he lives in or is near.
if the user doesn't know what timezone he is in then what is he doing with a complex thing as a computer in the first place?

EDIT: ok to show the uber-coolness of macosx timezone selector. you can click on the approximate location of your location and it simply selects the timezone you are in
I think you might be surprised how many people don't have a clue what time zone they live in! :)

---

### Post by Gina on 2008-05-06
I think there are a lot of people in the world who don't know where their country is on a world map too - and that includes this country (UK, England, Scotland, Wales etc.).  But people need some way of setting it up.  The Alternate CD asks you which country you live in (and presumably for the bigger countries like the USA, which state).

But I still think the previous map/zoom method was far easier than the Hardy method.

---

### Post by ccw on 2008-05-06
> **zekopeko said:**
> i don't know why all the fuss. Mac OS X has this whole "mess" figured rather nicely ([http://upload.wikimedia.org/wikibooks/en/6/69/Tiger_System_Preferences_Date_&_Time_Time_Zone.png](http://upload.wikimedia.org/wikibooks/en/6/69/Tiger_System_Preferences_Date_&_Time_Time_Zone.png)).

so why don't we just do it like they do it? take picture like the following ([http://www.theodora.com/maps/new9/time_zones_4.jpg](http://www.theodora.com/maps/new9/time_zones_4.jpg)). strip all of the info that we don't need and simply highlight all of the cities in the specific/selected timezone and be done with it. easy as pie.

The "Closest City" isn't the proper question: There's a good chunk of New Mexico that should choose Denver as its representative city in Mountain time, but is closer in proximity to Phoenix.

---

### Post by ccw on 2008-05-06
> **jdholifield said:**
> Its not ridiculous.

Sure its the same Time Zone, but to someone performing the install its not at all clear what you're expected to do.

If you gave your mother an Ubuntu CD to install on her computer, would she know "Well this city is in my timezone" or would she wonder what the heck she was supposed to do ?

It seems to me that the Ubuntu team has taken great pains to make it easy to install, but choosing a city is confusing and makes that portion of the installer stick out like a sore thumb.

Are there screenshots of the time zone selection process in Hardy (it changed right?). My machines are upgraded, last version I've installed fresh is gutsy. I want to make sure we are discussing the same process.

Edit: nevermind: from what I gather: the concept didn't change, the behavior within the process got modified (weird scrolling map type stuff).

---

### Post by kragen on 2008-05-07
The "you need to specify your language as well as your time zone" doesn't really justify why you select a city rather than a time zone:

1) Most time zones have more than one city in them
2) Plenty of cities have residents speaking multiple languages

The whole concept of a one-to-one relationship between time zones and cities, or languages and cities is completely absurd.

In addition, clicking on the city is more difficult from a usability point of view, as the city is smaller - the only reason the zoom feature is needed is because selecting a city is too difficult when the map is zoomed out.
(The zoom feature is also unintuitive and difficult to use)

In short:
We need two pieces of information here, so ask two questions.

How about two levels of highlighting? The time zone you are in is highlighted, as well as the country you are in. Admittedly this will definitely need a zoom feature of sorts.

---

### Post by Ripfox on 2008-05-07
> **jdholifield said:**
> Yes its confusing.  For example, I have to select Chicago to get the correct timezone, but Chicago is a thousand miles away from where I live, I've never been there, and I have no idea at all if its in the same timezone as me or what.  

Ubuntu should either add a reasonable number of cities to the map thing that you pick with, or else just add something where I can pick GMT-5 and be done with it without having to be a geography expert to get the right timezone.

+1

---

### Post by ccw on 2008-05-07
> **kragen said:**
> 
In short:
We need two pieces of information here, so ask two questions.


No: as pointed out multiple times in this thread: There are 3 pieces of information:

Country
Time zone
If and when DST/summer time is observed (which varies all over the place, and changes quite frequently)

Yeah: selecting a time zone is easy... Unfortunately, there's more to it than that.

---

### Post by Talon2 on 2008-05-08
> **jdholifield said:**
> Its not ridiculous.

Sure its the same Time Zone, but to someone performing the install its not at all clear what you're expected to do.

If you gave your mother an Ubuntu CD to install on her computer, would she know "Well this city is in my timezone" or would she wonder what the heck she was supposed to do ?

It seems to me that the Ubuntu team has taken great pains to make it easy to install, but choosing a city is confusing and makes that portion of the installer stick out like a sore thumb.

+1

---

