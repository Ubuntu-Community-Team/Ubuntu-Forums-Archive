---
title: "Is there temporary internet folder in Ubuntu?"
date: 2009-05-16
forum: The Cafe
---

### Post by powerdvd on 2009-05-16
I would like to collect the flv files after i watch clips in Youtube.

Usually i found the files in MS window temporary internet folder.

In ubuntu environment, is there a  temporary internet folder exist?

Thanks
regards

---

### Post by Name change on 2009-05-16
I think that all (not just intenet) temporary files are in /tmp

---

### Post by Chemical Imbalance on 2009-05-16
> **powerdvd said:**
> I would like to collect the flv files after i watch clips in Youtube.

Usually i found the files in MS window temporary internet folder.

In ubuntu environment, is there a  temporary internet folder exist?

Thanks
regards

I'm not sure which one you want, but there is a cache in the .mozilla folder in your /home/"username" folder [press ctrl+h to see hidden folders (the period in front of a file name means it is hidden)].

There is also /tmp.

---

### Post by OutOfReach on 2009-05-16
/tmp is what you're looking for

---

### Post by Icehuck on 2009-05-16
Maybe my system is just goofy, but my temp files for Firefox are sitting in my ~/.mozilla folder and not in /tmp. Using an unmodified Ubuntu 8.10

---

### Post by ad_267 on 2009-05-16
> **Icehuck said:**
> Maybe my system is just goofy, but my temp files for Firefox are sitting in my ~/.mozilla folder and not in /tmp. Using an unmodified Ubuntu 8.10

The flv files end up in /tmp, separate to things like cached images which are in ~/.mozilla. They're cleared as soon as you browse away from a video though, so you have to make sure you copy the flv file from /tmp before you leave the web page.

---

### Post by GeneralZod on 2009-05-16
If you want a more direct way of doing this, you can install youtube-dl - it's a command-line tool for downloading youtube flv files, but is quite easy to use :) Alternatively, I think I've heard of a Firefox extension that does this more seamlessy.

---

### Post by Sealbhach on 2009-05-16
I use a Firefox add-on called NetVideoHunter, which I find very straightforward to use.


.

---

### Post by Farab on 2009-05-16
goto ~/.mozilla/firefox/*.default/Cache
then sort them by size and find your file in top of the files...

put any name you find in ~/.mozilla/firefox instead of "*".

---

### Post by wersdaluv on 2009-05-16
All flv files sit on my /tmp/

---

### Post by gn2 on 2009-05-16
I use [Media Converter]("https://addons.mozilla.org/en-US/firefox/addon/8189"), it's veratile and offers a range of on the fly conversion options.

---

### Post by lovinglinux on 2009-05-16
[Video DownloadHelper](https://addons.mozilla.org/en-US/firefox/addon/3006) extension.

---

### Post by MaxIBoy on 2009-05-16
You have a few options, depending on the website.

[LIST]
[*]**Youtube:** If you go to the address bar and replace "youtube" with "pwnyoutube," it'll take you to a page to download that video.
[*]**Some misc. sites:** Look in /tmp for the video. Some media player gadgets have protection against this kind of thing but a lot of the time it works.
[*]**Homegrown DIY embedding:** Go into the page source, find the URL of the embedded video, and go to that. This will take you to the media player gadget taking up the whole page. Copy the URL of this page into a text editor, look for other URLs embedded in it. You kind of need an eye for it, but it's easy when you get used to it. For example, the URL "[FONT=Lucida Console]http://www.some_website.com/a-video.flv[/FONT]" might look like "[FONT=Lucida Console]http%3A%2F%2Fwww.some_website.com%2Fa-video.flv[/FONT]," as in "[FONT=Lucida Console]the_url_of_some_media_player_gadget&play=http%3A%2F%2Fwww.some_website.com%2Fa-video.flv[/FONT]."
[*]**Blip.tv:** Kind of a variation on the above, you have to jump through a few  more hoops. Basically, each video has its own RSS feed somewhere, with the video in a few different levels of quality. Find the URL of the RSS feed using the URL of the media player gadget, and you can just right-click and download the version with the best quality.
[/LIST]
I do this a lot, especially for big videos, because I'd prefer to just let it download and then watch it as many times as I want, instead of letting it buffer.

---

### Post by HavocXphere on 2009-05-16
> **lovinglinux said:**
> [Video DownloadHelper](https://addons.mozilla.org/en-US/firefox/addon/3006) extension.
+1 on that.:KS

---

### Post by Chemical Imbalance on 2009-05-17
There's also some greasemonkey scripts that do the trick: [http://userscripts.org/](http://userscripts.org/)

Just install the Greasemonkey addon and search for youtube scripts.

There's dozens of youtube-download sites out there too.

---

