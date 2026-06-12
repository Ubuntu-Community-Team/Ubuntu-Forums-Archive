---
title: "Map updates for garmin - is it possible?"
date: 2010-06-30
forum: Wine
---

### Post by laoshi on 2010-06-30
In order to avoid using windows for updating the maps for my Garmin nüvi 265w I have done as follows:
- installed wine
- installed Firefox for Windows in wine
- installed the garmin communicator plugin 2.9.2.0

So far so good. And when the gps is plugged in via usb it does as a matter of fact show up as .wine/dosdevices/h:

But the communicator plugin does not recognize it. Is there a workaround for this?

I have tried google and the search function in this forum, but all solutions seem to recommend windows in virtualbox, which I would rather avoid. Or else softlinking /dev/ttyUSB - which does not exist in Ubuntu 10.04.

So any suggestions would be appreciated.

---

### Post by David Oxland on 2010-11-24
Bump
I'm looking for this too.
Any thing to get Garmin going in Ubuntu
Thanks

---

### Post by foobar66 on 2010-11-26
> **David Oxland said:**
> Bump
I'm looking for this too.
Any thing to get Garmin going in Ubuntu
Thanks

Look here:
[http://www.gpspassion.com/forumsen/topic.asp?TOPIC_ID=121878](http://www.gpspassion.com/forumsen/topic.asp?TOPIC_ID=121878)

---

### Post by foobar66 on 2010-11-26
> **David Oxland said:**
> Bump
I'm looking for this too.
Any thing to get Garmin going in Ubuntu
Thanks

And if you want to use MapSource, look here:
[http://ubuntuforums.org/showthread.php?t=1483930&highlight=mapsource](http://ubuntuforums.org/showthread.php?t=1483930&highlight=mapsource)

---

### Post by Handssolow on 2011-02-05
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7502](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7502)

The report is of a Garmin sports GPS, not sure if it works with Garmin car satnavs.

---

### Post by laoshi on 2011-02-14
This procedure works for software update on my garmin nüvi265w, using Firefox in wine.
The map update is not coming along.
I have tried installing IE on PlayOnLinux - and when I tried to update my maps I got an error message saying that I was using wrong version of .NET.
Experimenting I have now succeeded in messing up wine. Will try to sort it out again in order to have those maps updated!

---

### Post by Handssolow on 2011-02-14
Glad you've had at least some success laoshi.
Here are some reports of development work on recognition of TomTom satnavs. I'd say it's the most encouraging news I've seen for some time and if successful might also help owners of Garmins.

[http://bugs.winehq.org/show_bug.cgi?id=7711](http://bugs.winehq.org/show_bug.cgi?id=7711)

I've installed .NETs and IE under Wine in the past but I suspect you'll not get much further with your Garmin updates. It's the way Wine currently handles removable drives.

---

### Post by RT236 on 2011-03-22
> **laoshi said:**
> This procedure works for software update on my garmin nüvi265w, using Firefox in wine.
The map update is not coming along.
I have tried installing IE on PlayOnLinux - and when I tried to update my maps I got an error message saying that I was using wrong version of .NET.
Experimenting I have now succeeded in messing up wine. Will try to sort it out again in order to have those maps updated!

I have this working perfectly now for a Garmin nuvi 255.  I just did a complete maps update from the Garmin website and it worked flawlessly.  However, I am using VirtualBox 4.0.4. I tried and tried to do it via Wine but I got stuck as you did. I just could not get Microsoft .NET Framework to install under Wine.  It kept hanging with a blue Icon with .NET on it.

Here's what I had to do as I posted just now in the Forums.  Here's the link.  [http://ubuntuforums.org/showthread.php?t=1712447&highlight=garmin+gps+virtualbox](http://ubuntuforums.org/showthread.php?t=1712447&highlight=garmin+gps+virtualbox)  After doing this one needs to log out and back in to update the changes.

I hope this might help some.

---

