---
title: "Last.fm clients"
date: 2009-04-30
forum: The Cafe
---

### Post by Metallion on 2009-04-30
Recently I've grown addicted to last.fm... Only to find out that my beloved Amarok 1.4 doesn't work with it any more and the Amarok team has no intention to fix it.

Now I know I could just use the official client and until now that has indeed worked really well but one thing I miss a lot is the OSD, that little bubble that Amarok shows on screen every time a new song starts to play.

Can anyone reccomend me some other players that work with last.fm and have this notification bubble when a new songs starts? It's annoying having to bring up another window every time I want to know what song is playing. :)

---

### Post by notwen on 2009-04-30
Ever consider running conky along the edge of a screen using one of the gazillion scripts that display media player info?  This all of course depends on which media player you end up using(along w/ it's compatibility w/ the last.fm client).  =]

---EDIT---
This only resolves the problem of not knowing which song is currently playing FYI.

---

### Post by Sealbhach on 2009-04-30
Have you tried Banshee? It brings up the bubble.


.

---

### Post by timzak on 2009-04-30
I really like vagalume.  It works well with the new osd-notify.  I see a black bubble pop up in the upper right with album cover art and song title whenever a new song starts playing.

vagalume is in the repos starting with 8.10.  8.04 and earlier it's not in the repos.

I think vagalume doesn't have as many dependencies as lastfm too.

---

### Post by Bios Element on 2009-04-30
Actually, If your in Turnhout, Belgium then I've got some bad news for you. I'm pretty sure you have to pay to use Last.fm after 10 songs or something like that.

---

### Post by happysmileman on 2009-04-30
Are you sure Amarok is the problem?

Last.fm recently stopped offering free music streaming to anyone outside of the USA, UK or Germany due to legal issues, so no player will work with last.fm if you aren't a subscriber. (You get 30 free songs but I'm not sure if you can use any player to play them)

And if you are a subscriber any players should work just as they always have.

---

### Post by SuperSonic4 on 2009-04-30
My amarok 1.4 is syncing fine but as has been said it might be a last fm issue

---

### Post by Metallion on 2009-05-01
Don't worry, it's not the last.fm subscription issue. I simply paid for that. If I choose to pay in dollars, it only costs me 2.37 euro a month. That's only like one proper beer. :)

I am sure the problem is Amarok. Amarok 1.4 still uses or rather tries to use an old protocol that last.fm doesn't support any more. Check this thread if you want to see the developers say they have no intentions to fix this. [http://amarok.kde.org/forum/index.php/topic,16510.0.html](http://amarok.kde.org/forum/index.php/topic,16510.0.html)

I think I'm going to give that vagalume a try. I'm not a big fan of banshee I'm afraid. I'm still hoping that the old interface will be integrated into Amarok 2 as an option so I can start using that.

Edit: So far I'm liking vagalume. I don't like the small main window since I have a habit of maximizing the media player in its own workspace but I can tolerate it for now. The notifications are what I wanted really and they're working well. I did have to build my own notify-osd because I'm still on Intrepid. In case anyone wants the deb, here it is.

---

