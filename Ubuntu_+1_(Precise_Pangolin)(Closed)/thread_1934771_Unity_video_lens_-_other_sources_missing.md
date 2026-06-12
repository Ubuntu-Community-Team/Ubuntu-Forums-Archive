---
title: "Unity video lens - other sources missing?"
date: 2012-03-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by blackplague1347 on 2012-03-02
I installed the 12.04 beta today. So far so (very) good. I've been reading a few articles online about the new features. One of them is the videos lens. When I look at screenshots of this feature, there are several video sources listed. When I look at the video lens, however, the only place I seem to be able to search is "My Videos." 

Do I have to enable other sources or something? I apologize, but this is the first I've really taken interest in Unity Lenses, so I'm unfamiliar with them.

---

### Post by grahammechanical on 2012-03-02
Have you ran an update since installing? You most probably need to.

You have the Standard Video lens but you lack the video remote scope, which only just recently has been added.

So, there are lenses and Scopes.

Open the Ubuntu Software Centre and search for unity-scope-video-remote. You should be able to download version 0.3.3-0ubuntu1

Regards.

---

### Post by blackplague1347 on 2012-03-03
Well that was easy. Thanks!

Eventually I'll learn my lesson. This isn't the first time I've posted a problem to a forum only to find out that "update everything" would take care of it  :D

---

### Post by x-shaney-x on 2012-03-03
Dunno. I have a newly installed and updated beta install and the lens isn't working properly.
Only lists "My videos" in sources and anything entered in the search box results in nothing.

So no working music or video lens at the moment

---

### Post by grahammechanical on 2012-03-03
@x-shaney-x

If you only have My Videos in the Dash Video lens then you do not have the video scope called unity-scope-video-remote. You need that. It acts like a search engine.

My second point is that you will not see any results either in the music lens or the video lens until you actually access some music or videos.

The Dash music lens remembers recently accessed music files. It is the same with the other lenses.

I have had the video lens and the video scope installed for a couple of days but there was nothing showing. This morning I accessed the BBC iplayer service to listen to a radio show and now the video scope is showing all kinds of stuff from the sources listed in the video scope.

Regards.

---

### Post by x-shaney-x on 2012-03-03
```
$ apt-cache policy unity-scope-video-remote
unity-scope-video-remote:
  Installed: 0.3.3-0ubuntu1
  Candidate: 0.3.3-0ubuntu1
  Version table:
 *** 0.3.3-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status
```

I know the video scope doesn't normally show anything other than recently accessed vids by default but it isn't displaying anything through searches either.
I should mention I had a 12.04 testing install up until a coupleo of days ago and video WAS working in that.  There was an update to the video lens packages earlier today and I think that may have broken things.

The music lens (in oneiric) shows a fair selection of music in your library normally.  I believe in pangolin it is not yet working at all (not just for me).

---

