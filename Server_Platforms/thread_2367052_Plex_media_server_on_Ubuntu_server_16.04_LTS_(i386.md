---
title: "Plex media server on Ubuntu server 16.04 LTS (i386) failed"
date: 2017-07-25
forum: Server Platforms
---

### Post by vidar-78 on 2017-07-25
I have problems with installing the plex media server on Ubuntu 16.04 (i386).


This is what I get when I run the plexmediaserver.service:


plexmediaserver.service - Plex Media Server for Linux
   Loaded: loaded (/etc/systemd/system/plexmediaserver.service; enabled; vendor preset: enabled)
   Active: inactive (dead) (Result: exit-code) since sø. 2017-07-23 21:47:12 CEST; 19s ago
  Process: 2015 ExecStartPre=/bin/sh -c /usr/bin/test -d "${PLEX_MEDIA_SERVER_APPLICATION_SUPPORT_DIR}" || /bin/m


juli 23 21:47:07 Lidarende-Ubuntu systemd[1]: plexmediaserver.service: Failed with result 'exit-code'.
juli 23 21:47:12 Lidarende-Ubuntu systemd[1]: plexmediaserver.service: Service hold-off time over, scheduling res
juli 23 21:47:12 Lidarende-Ubuntu systemd[1]: Stopped Plex Media Server for Linux.
juli 23 21:47:12 Lidarende-Ubuntu systemd[1]: plexmediaserver.service: Start request repeated too quickly.
juli 23 21:47:12 Lidarende-Ubuntu systemd[1]: Failed to start Plex Media Server for Linux.




This is what I did to install it:


echo deb [https://downloads.plex.tv/repo/deb/](https://downloads.plex.tv/repo/deb/) public main | sudo tee /etc/apt/sources.list.d/plexmediaserver.list
curl [https://downloads.plex.tv/plex-keys/PlexSign.key](https://downloads.plex.tv/plex-keys/PlexSign.key) | sudo apt-key add -
sudo apt update
sudo apt install plexmediaserver -y




Can anyone help me find the issue(s) with this installation?


Regards


Vidar Oeveraas

---

### Post by again? on 2017-07-25
You could try the solution here which had a similar error.
[https://askubuntu.com/a/859745](https://askubuntu.com/a/859745)

---

### Post by darkod on 2017-07-25
You can also simply download the .deb file from the Plex website, and install it with:
```
sudo dpkg -i filename.deb
```

When you want to update it, you can do the same. There is no need to use a repository and to frequently update it. You can select which way you want to do it, whatever works best for you.

---

### Post by TheFu on 2017-08-19
Beware that Plex corporate has decided to change their privacy policy next month. [https://www.plex.tv/about/privacy-policy-update-notice/](https://www.plex.tv/about/privacy-policy-update-notice/) Each person will need to decide if that change is allowable in their environment.

I've skimmed it. They are interested in file metadata EXCLUDING file names - resolution, codecs, tracks, etc., length of time used, and 3rd party service use.  So if you are using Plex via Alexa, they want to know that.

> This information may include metadata about the media (such as title, duration, author, cover art, dates associated with the media, and other relevant information) and information about the media itself (such as resolution, bit rate, format, location, etc.).

I don't mind the 2nd group, but the 1st group is an invasion of privacy.

---

### Post by again? on 2017-08-19
> **TheFu said:**
> Beware that Plex corporate has decided to change their privacy policy next month. [https://www.plex.tv/about/privacy-policy-update-notice/](https://www.plex.tv/about/privacy-policy-update-notice/) Each person will need to decide if that change is allowable in their environment.

I've skimmed it. They are interested in file metadata EXCLUDING file names - resolution, codecs, tracks, etc., length of time used, and 3rd party service use.  So if you are using Plex via Alexa, they want to know that.



I don't mind the 2nd group, but the 1st group is an invasion of privacy.
So are you reaching for your pitchfork? :)
I don't like this change.
Have you ever looked at [Emby]("https://emby.media/about.html")(Media Browser)?
Found this posted on the [emby community forum]("https://emby.media/community/index.php?/topic/50099-plex-privacy-issues-and-the-plan-at-emby/") today.
> We cannot tell the future but we do allow you to opt out of our statistics collection.
It is also worth noting that our statistics are very different from theirs.  All we are doing is trying to see how many people are using which apps so that we can properly gauge their respective audiences and apply our resources accordingly.
The other guys collect a bunch of stuff about the media you are playing (not actually which media but metadata about it like its format, bitrate, etc.).  We have never tracked or collected that and have no plans to.

---

### Post by again? on 2017-08-22
Seems they have backtracked ...
[https://www.plex.tv/about/privacy-policy-changes/](https://www.plex.tv/about/privacy-policy-changes/)

---

### Post by TheFu on 2017-08-22
> **guber2 said:**
> Seems they have backtracked ...
[https://www.plex.tv/about/privacy-policy-changes/](https://www.plex.tv/about/privacy-policy-changes/)

If we can believe them. 

I've found either people believe that *privacy* is very important or they don't.  
I've not seen many change their minds.

We all have to decide how much of a trade-off we will accept between the convenience of Plex and whatever level of privacy we end up getting - which almost never matches what we are told.

---

### Post by again? on 2017-08-22
Yes, think I'll stick with Plex. Can't find anything else that easily allows me to cast my PC files to my TV(chromecast)
using my phone.
Had a look at Emby but it uses the mono .NET framework which I don't want on my system.

---

