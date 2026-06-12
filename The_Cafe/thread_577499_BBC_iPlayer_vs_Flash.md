---
title: "BBC iPlayer vs Flash"
date: 2007-10-16
forum: The Cafe
---

### Post by stevebakerj on 2007-10-16
As seen on BirminghamLug list:

"The BBC has also confirmed that users of Apple Mac and Linux machines
will be able to use its TV catch-up service from the end of the year.

The broadcaster has signed a deal with Adobe to provide Flash video
for the whole of the BBC's video services, including a streaming
version of its iPlayer. "

Source: [http://news.bbc.co.uk/1/hi/technology/7045123.stm](http://news.bbc.co.uk/1/hi/technology/7045123.stm)

As well as Windows users having DRMed Windows Media Files that explode
after 30 days, it seems like we will get .flv files ala YouTube,
Google Video et al.

This is interesting because if one downloads the .flv files to disk
then they will work in Mplayer or Totem forever. At least that is how
it works with YouTube. Until the recent release of Gnash, manually
downloading the .flv file was the only way to watch YouTube using only
Free/Open Source Software.

---

### Post by Dixon Bainbridge on 2007-10-16
I always wondered why the hell the bbc were making an app for this iplayer (please, no more fricking apps call i-something... its lame and ghey), when they could just have used flash from the start and be multiplatform instantly.

Or have I missed something?

---

### Post by DoctorMO on 2007-10-16
I have to say that there are a lot of US companies putting the BBC to shame over this issue. Just look at the NBC Heroes for how to really do this sort of thing.

---

### Post by oswaldkelso on 2007-10-22
> **Dixon Bainbridge said:**
> I always wondered why the hell the bbc were making an app for this iplayer (please, no more fricking apps call i-something... its lame and ghey), when they could just have used flash from the start and be multiplatform instantly.

Or have I missed something?

Well it leaves linux ppc users up a flagpole with the floods rising! I doubt very much if the iplayer will work on linux ppc so it will be getting stuff either via MOL, dual booting or  bittorrent. 

Content providers need to wake up. Gone are the days of 1 and 2 channels, there is lots of content and it gets old very quickly. There is no need for drm because  as we are seeing with Mira, podcasting and vodcasting, its getting easier and easier for people to make content. There is only so many hours in the day and so many file formats as corporate media suppliers keep trying  lock people in that one day someone will use a google model and provide a service that people want and make an awful lot of money by providing something for free
 There you go Google TV once it starts the floodgates will open. Drm will be dead (if its not already) as the present member of the Hollywood cartel rush to provide unencumbered content.

---

### Post by Johnsie on 2007-10-22
I dont think this'll make it much easier to download the flv files. There's already a few flash video sites where you cannot download the flv files. Also, it would be easy for adobe to make a special player for the BBC that is different to the standard flash player.

---

### Post by helliewm on 2007-11-04
See my thread here you can watch BBC programmes videos etc. I stumbled across this by accident.


[http://ubuntuforums.org/showthread.php?t=602477]("http://ubuntuforums.org/showthread.php?t=602477")

---

### Post by bruce89 on 2007-11-04
> **helliewm said:**
> See my thread here you can watch BBC programmes videos etc. I stumbled across this by accident.


[http://ubuntuforums.org/showthread.php?t=602477]("http://ubuntuforums.org/showthread.php?t=602477")

It's called putting the telly on.

---

### Post by MonkeyBoy on 2007-11-04
> **helliewm said:**
> See my thread here you can watch BBC programmes videos etc. I stumbled across this by accident.


[http://ubuntuforums.org/showthread.php?t=602477]("http://ubuntuforums.org/showthread.php?t=602477")

This is because the Beeb puts all its clips etc on it's site as streaming rms which are easy to run with mplayer or realplayer.  The problem is that there isn't a lot of content available this way.  Just a load of trailers and a couple of full shows.  The iPlayer is more about being able to watch anything they have broadcast.

---

### Post by fluteflute on 2007-12-12
linux iPlayer streaming has gone live today!

bbc.co.uk/iplayer

---

### Post by helliewm on 2007-12-12
Wow I don't believe it!

---

### Post by floke on 2007-12-12
Excellent!

** Goes off to watch the Mighty Boosh that keep missing... **

---

### Post by musther on 2007-12-17
All we need now is a way to download the flv's, shouldn't be too hard.

---

### Post by macogw on 2007-12-17
> **musther said:**
> All we need now is a way to download the flv's, shouldn't be too hard.

Just use the Unplug Firefox extension

---

### Post by musther on 2007-12-17
Doesn't work, it may well in the future, but not yet.

---

### Post by Lostincyberspace on 2007-12-17
This sucks I cant watch doctor who since I'm not in the uk.

---

### Post by musther on 2007-12-17
You just need a proxy in the UK.

The easiest way is:

  Get someone in the UK to give you an account, and make sure they've got an SSH server running.  They'll need a fast internet connection.

  Start an SSH connection like so:
ssh -l username -CN -D 9999 the-host.net
change username and the-host.net appropriately.  -C makes it use compression, -N makes it non-interactive, simply an SSH data tunnel, and -D 9999 puts it on port 9999.

  Open firefox and tell it to use a socks 5 proxy, the address is localhost, the port is 9999.  

  You can use a proxy addon for firefox to make switching to the proxy and back again easier.

---

### Post by Lostincyberspace on 2007-12-17
That is all fine and dandy if you know some one there. Every one I knew who lived over there has moved away.

---

### Post by musther on 2007-12-17
True.  I'm lucky, I know somebody with a web hosting company.

---

### Post by macogw on 2007-12-17
> **Lostincyberspace said:**
> This sucks I cant watch doctor who since I'm not in the uk.

I can't watch Doctor Who since PBS long since stopped showing it late at night.  And I don't want to watch the new stuff that's on in the UK.  "My doctor" is Tom Baker.

---

### Post by musther on 2007-12-17
Is this going to turn into a Dr Who thread?  lol

The new stuff is really good btw

---

### Post by getaboat on 2007-12-17
Hmmmm the linux iplayer is OK - the sound in particular is good - but with my UK standard broadband connection (3-4Mb) - full screen picture quality is poor - and I don't want to watch tv through a letterbox. It's Ok for 5mins or so for You Tube but not for a sit-down-and-watch program. Roll-on the downloads. Still good on the Beeb for not ignoring Linux.

---

