---
title: "Recommendations for remote control web interface"
date: 2010-06-16
forum: Server Platforms
---

### Post by Arthur_D on 2010-06-16
Hi, I want to set up a home computer as server. I've installed Ubuntu Server Edition 10.04, and can access it through SSH. However, I would like to have a browser based interface for managing things, such as installing a phpBB forum and stuff like that. Also, I want my friends to be able to share files on my home server as well. I know I can do it by using FTP, but I would rather not have them to install a FTP program.

Any idea about what I should use?
Thanks for taking the time. :)

---

### Post by arrrghhh on 2010-06-16
Well the management interfaces I can think of aren't so good for installing/compiling software... Webmin is the one I use, but recently it has come under fire and I believe Ubuntu is officially recommending people use eBox.  Never used it myself, but it looks like a great replacement for Webmin... so I probably should switch to it.

With that said, I don't really have any recommendations for you on the FTP thing.  If they're just doing pictures, Gallery2 is pretty cool... but if you want general file access, you can do something like ajaXplorer.  Not real sure what you want to achieve tho.

---

### Post by Arthur_D on 2010-06-16
Thanks, I will look into eBox a bit more than I have already (barely looked at it). :)

About file sharing; I want to have separate folders for each of my friends, where they only have read+write access to their own folder, but read access on all the other ones. This is for music making collaboration. We will share MIDI's, WAV's, MP3's and such, and we'll use a phpBB forum to discuss things (not only music).

I welcome more suggestions as well. :)

---

### Post by arrrghhh on 2010-06-16
Well if you're setting up a full phpBB forum, isn't there an upload feature in most of those?

I'm honestly not sure what you could use, short of a custom php config for uploading... I'm not aware of any drop-in tools that would do that for you (I'm not sure ajaXplorer is really what you'd want for this...)

---

### Post by Arthur_D on 2010-06-16
Yes, phpBB got an upload feature, but I think it would quickly get very unorganized and hard to find the stuff people are looking for. I'd really like something better.

Thanks for your help anyway, I can't expect people to know everything. In the case I don't get any high recommendations, I'll try to investigate myself on this topic - just thought there might be some good standard open source interface everyone would recommend.
Alright, I'll admit I haven't done enough researching on my own. :p
If anyone would still like to help me out, I'd be glad for any advice I could get. ;)

---

### Post by constellanation on 2010-06-16
it sounds like you want something like dropbox?

---

### Post by Arthur_D on 2010-06-16
Yes, sort of, but I'd like to run it on my own server. Then I'll have complete control of the data, and I can use as much space as I want (not literally, of course, but you get the idea - WAV files will quickly fill up 2GB).

---

### Post by constellanation on 2010-06-16
i haven't tried any of this, but i just built a server and this sounds like an interesting project for me as well ;)

how about this [https://help.ubuntu.com/community/iFolder](https://help.ubuntu.com/community/iFolder)

---

### Post by Arthur_D on 2010-06-16
Sounds good (still not totally sure if it does what I want), but this page really scares me: [https://help.ubuntu.com/community/iFolderInstall](https://help.ubuntu.com/community/iFolderInstall) :confused:
Really easy to use; maybe - but a pain to set up, it seems.

I'll check it out some more before deciding though - thanks for the suggestion. :)

---

### Post by constellanation on 2010-06-16
yeah it looks like a bit of an intimidating install, atleast for some one like me, however right now i can't seem to find anything else that seems to fit the bill other then just opening up a folder on your server to ftp...

---

### Post by edenCC on 2010-06-17
Nice for me to know eBox :p
Anyway, It's highly suggested to use SSH, what you need to do might be just spend some weeks on it to get familiar with it.
That's it, the linux way to manage services.  :guitar:

---

