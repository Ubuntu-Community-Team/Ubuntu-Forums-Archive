---
title: "Better to change Flash Player plug-in to &quot;Ask to Activate&quot; in Firefox"
date: 2015-05-16
forum: Ubuntu, Linux and OS Chat
---

### Post by amr-maro on 2015-05-16
Hello everyone. I want to share my experience. I changed the Flash Player plug-in in Firefox to "Ask to Activate" instead of "Always Activate". It means that it will stay disabled until you actually need it. I save resources by doing that. I was surprised to find the websites that ask to activate Flash Player without any apparent reason for it.

Another thing is to install the extension "HTML5 Video Everywhere!". It replaces Flash video player with Firefox native video player. So I don't even need to activate the Flash Player and use HTML5 instead. It doesn't work for all websites, especially legacy websites, but it works in Youtube and many others.

Hope everyone tries that and tell me their experience.

---

### Post by night_sky2 on 2015-05-16
I use the Fresh Player Plugin so as to be able to convert the latest pepperflash into NPAPI plugin compatible in Firefox. Works great for me. No more older flash version.

[http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html](http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html)

---

### Post by monkeybrain20122 on 2015-05-16
Yes, this feature (set flash to "ask to activate") has been available for a long time (Firefox 24, 25 something like that) Some people on the forum still advise installing flashblock, which is unnecessary with this feature.

I think Youtube would use html5 as default if you disable flash, but IMO a better way is to use Smtube to browse Youtube with a player like mpv or Smplayer as backend. [https://launchpad.net/~rvm/+archive/ubuntu/ppa](https://launchpad.net/~rvm/+archive/ubuntu/ppa) (a new version has just come out a few days ago and it is really sweet)

 Html5 is not exactly very efficient on Firefox so if the reason of not using flash is resources than it doesn't really get you very far (HTML5 works better on Chrome) Another option would be Viewtube, it is a greasemonkey script (need the greasemonkey addon) and use it with gecko-mediaplayer.  It plays flash on many supported sites in gnome-mplayer.  [http://isebaro.com/viewtube/?ln=en](http://isebaro.com/viewtube/?ln=en) With these methods you can use hardware acceleration on many newer graphic cards.

---

### Post by amr-maro on 2015-05-16
> **night_sky2 said:**
> I use the Fresh Player Plugin so as to be able to convert the latest pepperflash into NPAPI plugin compatible in Firefox. Works great for me. No more older flash version.

[http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html](http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html)

Well, I think if you have to install Chrome to use Pepper Flash, then it'd better to use Chrome after all :)

And the idea is to disable flash at all unless only needed.

---

### Post by amr-maro on 2015-05-16
> **monkeybrain20122 said:**
> a better way is to use Smtube to browse Youtube with a player like mpv or Smplayer as backend.

I use Smtube with Totem. It's really good.

> Html5 is not exactly very efficient on Firefox so if the reason of not using flash is resources than it doesn't really get you very far (HTML5 works better on Chrome)

You're right. The idea is to disable flash at all unless only needed, not only in videos, but also useless animations.

---

### Post by ajgreeny on 2015-05-16
I am one of those users who still prefers to use flashblock, and to set the flash plugin to "Always activate".

Doing that means that it is possible to allow flash items individually as on some pages there may be several flash items wanting to play.  It also means that I can whitelist or disable flashblock on specific pages or domains, which I find much more flexible that the default of "Ask to activate" which I don't find as useful.

---

### Post by mikodo on 2015-05-16
Thank you, folks. I was still using flash, but knew I wanted to change. You've "set me down the path", to doing this.

So, set Flash Player plug-in in Firefox to "Ask to Activate".

Installed [https://launchpad.net/~rvm/+archive/ubuntu/ppa](https://launchpad.net/~rvm/+archive/ubuntu/ppa)

Stuck a SMplayer launcher in my panel.

Now, I just copy the url I want, open SMplayer, paste in the url and hit play.

I'm sure I'll learn better ways to do this like, learn more about the "YouTube Browser for SMplayer". I like its theater view.

And, smtube searching .. " works a treat".

---

### Post by monkeybrain20122 on 2015-05-16
> **mikodo said:**
> Thank you, folks. I was still using flash, but knew I wanted to change. You've "set me down the path", to doing this.

So, set Flash Player plug-in in Firefox to "Ask to Activate".

Installed [https://launchpad.net/~rvm/+archive/ubuntu/ppa](https://launchpad.net/~rvm/+archive/ubuntu/ppa)

Stuck a SMplayer launcher in my panel.

Now, I just copy the url I want, open SMplayer, paste in the url and hit play.

I'm sure I'll learn better ways to do this like, learn more about the "YouTube Browser for SMplayer". I like its theater view.

Hey you don't need to copy the url into smplayer. Just use the youtube browser (called Smtube) It has pretty good search facility and more will be added (This is a totally reworked new version it is actually a webapp) You can choose and add backend player from View > Settings (I have mpv+ytdl, there are other choices like mpv, vlc, smplayer, gnome-mplayer, totem etc but I removed some)

Edited: to get 1080p is a bit tricky, have to use youtube-dl with mpv, hence mpv+ytdl, you need to highlight mpv+ytdl in the settings window and then choose Edit amd enter the parameter
 --ytdl-format=bestvideo+bestaudio %u

Of course you need to have up to date mpv  and also up to date version of youtube-dl. The Ubuntu stock versions of both are as usual outdated and useless. You can search for it, mc4man has a ppa with mpv (I compiled it myself), youtube-dl from webupd8's ppa.

---

### Post by mikodo on 2015-05-16
^^^ Thank you, monkeybrain20122.

---

### Post by night_sky2 on 2015-05-17
> **amr-maro said:**
> Well, I think if you have to install Chrome to use Pepper Flash, then it'd better to use Chrome after all :)

You don't need to install Google chrome at all. Just install the pepperflash-nonfree package from the Ubuntu Software Center. You can then install the Fresh Player Plugin which serves as a wrapper to convert the PPAPI pepperflash plugin to NPAPI for compatibility in Firefox. Voilà. You have the latest version of flash player running in the Firefox browser and by installing the ppa on the webup8 website (link provided above) that means you will receive the latest Fresh Player Plugin updates in your Ubuntu Update manger. :)

> **amr-maro said:**
> And the idea is to disable flash at all unless only needed.

You can set shockwave to ''Ask to Activate'' with pepperflash and the Fresh Player plugin as well.

---

### Post by monkeybrain20122 on 2015-05-17
But there are some stupid sites where if flash is set to 'ask to activate' they simply won't play instead of asking you to activate flash. Just come across one now
[http://music.cbc.ca/#!/blogs/2013/5/Margo-Timmins-on-Mothers-Day](http://music.cbc.ca/#!/blogs/2013/5/Margo-Timmins-on-Mothers-Day)

There is no popup, no option to activate flash, play buttons simply not clickable. Thought that because FF's flash 11 was outdated. But set flash to 'always activated' and reload the page the play button is now clickable. So flash is used not just to stream the audio, but also for the button.

---

### Post by night_sky2 on 2015-05-17
> **mikodo said:**
> Now, I just copy the url I want, open SMplayer, paste in the url and hit play.

I'm sure I'll learn better ways to do this like, learn more about the "YouTube Browser for SMplayer". I like its theater view.

And, smtube searching .. " works a treat".

I am doing this with Youtube videos in VLC Media Player once a while, because you can set the VLC player at any size you want by streching it, unlike the Youtube player. But I can't do without Flash Player at this point in time, I am one of those people who watch quite a lot of videos hosted on legacy streaming website. There are no way to play these in a Media Player like VLC, and anyway I don't think it would inconvenient to do this every time. The Fresh Player Plugin has solved the issue of the old 11.2 Adobe flash plugin which is becoming outdated, so I guess I am all set in Firefox.

---

### Post by monkeybrain20122 on 2015-05-17
> **night_sky2 said:**
>  I am one of those people who watch quite a lot of videos hosted on legacy streaming website. There are no way to play these in a Media Player like VLC, and anyway I don't think it would inconvenient to do this every time. The Fresh Player Plugin has solved the issue of the old 11.2 Adobe flash plugin which is becoming outdated, so I guess I am all set in Firefox.

Actually mpv+ytdl works for a lot more streaming sites than vlc [https://rg3.github.io/youtube-dl/supportedsites.html](https://rg3.github.io/youtube-dl/supportedsites.html)
You can use Smplayer as a front end.

[http://www.webupd8.org/2015/01/how-to-install-smplayer-with-mpv.html](http://www.webupd8.org/2015/01/how-to-install-smplayer-with-mpv.html)

[http://blog.smplayer.info/how-to-play-a-1080p-video-from-youtube-with-smplay](http://blog.smplayer.info/how-to-play-a-1080p-video-from-youtube-with-smplay)

for this to work for sites other than Youtube, change 
> --ytdl-format=bestvideo+bestaudio

to
> --ytdl-format=best,bestvideo+bestaudio

or just 
> --ytdl-format=best


The bestvideo+bestaudio is for Youtube if 1080p or higher is desired. Otherwise just best would get 720p max.

---

### Post by Bucky Ball on 2015-05-17
I always have flash and java (IcedTea) set to 'Ask to activate'.

---

### Post by monkeybrain20122 on 2015-05-17
Jut found this mpv+ytdl addon for Firefox [https://addons.mozilla.org/en-US/firefox/addon/watch-with-mpv/?src=cb-dl-created](https://addons.mozilla.org/en-US/firefox/addon/watch-with-mpv/?src=cb-dl-created) so no need to cut and paste url into Smlayer for non Youtube sites. :)

---

### Post by amr-maro on 2015-05-17
> **night_sky2 said:**
> You don't need to install Google chrome at all. Just install the pepperflash-nonfree package from the Ubuntu Software Center.

This is the package description from Debian: "This package will download Chrome from Google, and unpack it to make the included Pepper Flash Player available for use with Chromium." [https://packages.debian.org/unstable/pepperflashplugin-nonfree](https://packages.debian.org/unstable/pepperflashplugin-nonfree)

The problem is you cannot distribute Pepper Flash alone because there isn't a license for that. It's always bundled with Chrome.

---

### Post by night_sky2 on 2015-07-09
> **amr-maro said:**
> Hello everyone. I want to share my experience. I changed the Flash Player plug-in in Firefox to "Ask to Activate" instead of "Always Activate". It means that it will stay disabled until you actually need it. I save resources by doing that. I was surprised to find the websites that ask to activate Flash Player without any apparent reason for it.

The thing with 'Ask To Activate' in Firefox is that an annoying ''Allow Flash player to [X] website..'' popup bar appears over and over again.

I can't disable that bar.

---

### Post by amr-maro on 2015-07-09
> **night_sky2 said:**
> The thing with 'Ask To Activate' in Firefox is that an annoying ''Allow Flash player to [X] website..'' popup bar appears over and over again.

I can't disable that bar.

You will learn to ignore it. That also shows you how many websites were using Flash for no apparent reason. You will also use that bar to activate Flash when you really need it.

---

### Post by night_sky2 on 2015-07-09
> **amr-maro said:**
> You will learn to ignore it. That also shows you how many websites were using Flash for no apparent reason. You will also use that bar to activate Flash when you really need it.

But Flash can be activated by clicking the 'lego brick' icon on the left side of the adress bar, which makes the popup ''allow flash'' bar quite redundant and annoying.

Pending a solution, I use the FlashDisable addon for Firefox: [https://addons.mozilla.org/fr/firefox/addon/flashdisable/](https://addons.mozilla.org/fr/firefox/addon/flashdisable/)
In this way, I avoid this popup bar of ''ask to activate'' and can disable/enable-reload flash in one click. Besides, this has the convenience
 of defaulting Youtube and Dailymotion to the HTML5 player, because websites don't detect flash player in my browser at all unless I enable it.
 It saves ressources as well while browsing the web. I suggest you give it a try. The addon has virtually no impact on my system either.

---

