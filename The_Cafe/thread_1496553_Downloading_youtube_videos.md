---
title: "Downloading youtube videos"
date: 2010-05-29
forum: The Cafe
---

### Post by spibou on 2010-05-29
For the last few weeks every time I've tried downloading a youtube video I get a window opening with a message saying that an untrusted Java applet must run and ask me whether I trust it. Naturally I've answered no which means I can't download. I have noticed this with [http://www.kissyoutube.com](http://www.kissyoutube.com) , [http://www.downloadyoutubevideos.com](http://www.downloadyoutubevideos.com) and others. Anyone knows why this is happening and how to get around it ?

Apart from that it would be great if there was a command line tool for downloading youtube videos. You would do ```
utility www.youtube.com/something file
```and the tool would save the video in file.

---

### Post by antenna on 2010-05-29
There is a command line tool in the repos called youtube-dl.  Of course the problem is that as soon as youtube changes something it breaks and will not work until the app and then the repo is updated. (It may or may not work at the moment).  It's not really in youtube's interests to have those sites and tools like this working.

---

### Post by odiseo77 on 2010-05-29
You can use clive (*clive [youtube url]*),but it doesn't work 100% of the times for me. What I do is to watch the video, wait for it to buffer completely, and then check /tmp; in my case the video is always saved there (temporarily) when I use firefox. So far this method has always worked for me. (By the way, I think the video in /tmp is in flv format, even if it doesn't have an extension).

---

### Post by vrasidas on 2010-05-29
If you are using firefox [_flashgot_]("http://flashgot.net/") works great for youtube and other tube sites. I dont think it has a cli version though sorry.

---

### Post by Random_Dude on 2010-05-29
There's and add-on for firefox called Video DownloadHelper which works great:
[https://addons.mozilla.org/en-US/firefox/addon/3006/](https://addons.mozilla.org/en-US/firefox/addon/3006/)

Cheers :cool:

---

### Post by WinterRain on 2010-05-29
After you view a video, you can retrieve them from your /tmp folder. Just remember that /tmp only holds 1 at a time.

---

### Post by spibou on 2010-05-29
> **antenna said:**
> There is a command line tool in the repos called youtube-dl.  Of course the problem is that as soon as youtube changes something it breaks and will not work until the app and then the repo is updated. (It may or may not work at the moment).
I'll try youtube-dl but I don't understand how it is possible for a browser to be able to get the video but for a command line tool to possibly fail. In other words, if a change on youtube might break the command line tools why does it not also break browser support ?

> **odiseo77 said:**
>  What I do is to watch the video, wait for it to buffer completely, and then check /tmp; in my case the video is always saved there (temporarily) when I use firefox. So far this method has always worked for me. (By the way, I think the video in /tmp is in flv format, even if it doesn't have an extension).
I assume you need to have the Flash plugin installed for this to work, right ?

---

### Post by Bölvaður on 2010-05-29
> **WinterRain said:**
> After you view a video, you can retrieve them from your /tmp folder. Just remember that /tmp only holds 1 at a time.
Incorrect, it just keeps what you got open atm.
If you rename a video and browse away from the video, it will still remain there. But if you keep the same file name it will be destroyed the moment you browse away from the video.
Of course you can copy and rename these videos to any place you want.

---

### Post by odiseo77 on 2010-05-29
> **spibou said:**
> I assume you need to have the Flash plugin installed for this to work, right ?

Yes, you still need the flash plugin to make it work. Also remember that, as WinterRain says, /tmp only holds one video at a time.

---

### Post by undecim on 2010-05-29
I use 1-click youtube video download addon for Firefox on the family HTPC.

---

### Post by Shining Arcanine on 2010-05-29
> **antenna said:**
> There is a command line tool in the repos called youtube-dl.  Of course the problem is that as soon as youtube changes something it breaks and will not work until the app and then the repo is updated. (It may or may not work at the moment).  It's not really in youtube's interests to have those sites and tools like this working.

I had no idea that tool existed. I just installed that tool on my system. Thanks for telling people about it. :)

---

### Post by FuturePilot on 2010-05-29
youtube-dl

---

### Post by spibou on 2010-05-31
I have now tried youtube-dl .Very useful programme. Now if only they were to add support for [http://www.judovision.org](http://www.judovision.org)

---

