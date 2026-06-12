---
title: "Adobe To Revive NPAPI Flash For Firefox browser!"
date: 2016-09-10
forum: The Cafe
---

### Post by night_sky2 on 2016-09-10
Wow. Just wow. Is this even real? Omg.

[http://www.pcworld.com/article/3116409/linux/adobe-revives-flash-for-firefox-on-linux-after-axing-it-four-years-ago.html](http://www.pcworld.com/article/3116409/linux/adobe-revives-flash-for-firefox-on-linux-after-axing-it-four-years-ago.html)


There is absolutely no reason for me now to use Chrome on Ubuntu. Firefox all the way!

---

### Post by ajgreeny on 2016-09-10
Even using Firefox it has been possible to continue using flash PPAPI plugin (I currently have version 22.0.0.229) by adding the various versions of **freshplayer** that have been available for some time.

I realise that flash is dying, but there are still some sites that just will not work without it, BBC-iPlayer for one here in UK, but generally it is no longer needed, with html5 beginning to take over on many sites.

---

### Post by 6975 on 2016-09-10
Yeah I've been with freshplayerplugin long ago thanks to webupd8 guidance & freshplayer author.
It support all browsers qupzilla, midori is not exceptions.

---

### Post by night_sky2 on 2016-09-10
> **ajgreeny said:**
> Even using Firefox it has been possible to continue using flash PPAPI plugin (I currently have version 22.0.0.229) by adding the various versions of **freshplayer** that have been available for some time.

I realise that flash is dying, but there are still some sites that just will not work without it, BBC-iPlayer for one here in UK, but generally it is no longer needed, with html5 beginning to take over on many sites.

Right but this is kind of a hack. The NPAPI flash plugin for Firefox-based browsers was stuck at version 11.2 since 2012. Some websites (like BBC) had stopped supporting this version. Now it will be updated to version 23 pretty soon, with many improvements and security fixes. This is good news for Firefox users who still need to rely on flash. ;)

---

### Post by night_sky2 on 2016-09-10
> **6975 said:**
> Yeah I've been with freshplayerplugin long ago thanks to webupd8 guidance & freshplayer author.
It support all browsers qupzilla, midori is not exceptions.

The Fresh Player plugin will probably die eventually. The project was brought about by the fact that Adobe had ceased to release newer versions of Flash for Firefox. There was no other viable option than to take Google's pepperflash and create a wrapper for use in other browsers. But not all features of pepperflash work in Firefox anyway..

I just can't see how it's relevant anymore. It served it's purpose.

---

### Post by monkeybrain20122 on 2016-09-11
Just have to login to say a big "Who cares??" Most of the web is moving away from flash nowadays and I can watch almost all flash content on Firefox with the[ mpv-addon]("https://addons.mozilla.org/en-US/firefox/addon/watch-with-mpv/") which performs a lot better than flash. Even though I had the freshplayer plugin installed up to 15.10 but I have disabled flash on Firefox most of the time. I have only flash 11.2 in 16.04 just because it was installed along with Ubuntu-restricted-extras. But I have disabled flash in Firefox the whole time and I haven't felt I have missed anything.

---

### Post by &amp;KyT$0P# on 2016-09-12
> **monkeybrain20122 said:**
> Just have to login to say a big "Who cares??" [...] Even though I had the freshplayer plugin installed up to 15.10 but I have disabled flash on Firefox most of the time. I have only flash 11.2 in 16.04 just because it was installed along with Ubuntu-restricted-extras. But I have disabled flash in Firefox the whole time and I haven't felt I have missed anything.
Well, lucky you.
Flash is necessary for one specific website I visit and also for playing all those local .swf files (mostly games and such).

So, as to who cares? - I do, and judging by the comments on this thread and elsewhere I am not alone.

As much as I'd love to see Flash removed from the Web, it's still a much needed technology.  Happy to see this news! :D

---

### Post by pqwoerituytrueiwoq on 2016-09-12
> **night_sky2 said:**
> The Fresh Player plugin will probably die eventually. The project was brought about by the fact that Adobe had ceased to release newer versions of Flash for Firefox. There was no other viable option than to take Google's pepperflash and create a wrapper for use in other browsers. But not all features of pepperflash work in Firefox anyway..

I just can't see how it's relevant anymore. It served it's purpose.

pepper flash has the ever so coveted hardware acceleration, it is not as good as say running the video from say mplayer, but far better than adobe flash using 80+% of the CPU

---

### Post by coldraven on 2016-09-13
I hope that this will fix the "Autoplay" problem on the BBC news site. It just will not stay off! 
It's really annoying to watch a video about a volcano and then find that the BBC will play every video ever made on that subject :(
</rant>

---

### Post by ajgreeny on 2016-09-14
I have just seen flash version 23 has come to me in updates to 14.04.

I tested the need for the freshplayer plugin but removing that package put me back to flash version 11.2 in FF so the NPAPI plugin situation is not yet fully working without the freshplayer package.
Perhaps it will need a new version of FF before it all works as it should?

---

### Post by pqwoerituytrueiwoq on 2016-09-16
did you restart firefox after that update?
i had installed the beta copy by replacing the 11.2 libflashplayer.so file that and it worked, firefox actually picked it over the wrapper, i assume cause it was a high version number at the time

---

