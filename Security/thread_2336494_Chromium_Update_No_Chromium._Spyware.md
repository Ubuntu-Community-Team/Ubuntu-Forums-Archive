---
title: "Chromium Update? No Chromium. Spyware?"
date: 2016-09-08
forum: Security
---

### Post by barkester-b on 2016-09-08
My Ubuntu 14.04 keeps asking me to install the security update yet the only update on the list is less than 1k. and is for a program I neither want nor have, Chromium browser.

    I do know there is expensive software that mimics exactly this in order to install spyware. Naturally, I didn't install and won't. I do however think this may be an exploit on Ubuntu that should be watched for. I watch my updater with a new eye now.

   Personally, I hate all things Google and try my best to keep them off my computer, so I notice them. Anyone know why Ubuntu would need their help to keep my computer secure? A good explanation would change all.

   C U on the web.

---

### Post by ian-weisser on 2016-09-08
The specific wording of the message, and the specific package name involved, would help.
Are you getting a notification from update-notifier? Some other application? Not sure?

---

### Post by howefield on 2016-09-09
> **barkester-b said:**
> My Ubuntu 14.04 keeps asking me to install the security update yet the only update on the list is less than 1k. and is for a program I neither want nor have, Chromium browser.

I'm guessing the package is chromium-codecs-ffmpeg-extra which has had a recent update, would that be correct ?

---

### Post by barkester-b on 2016-09-10
Howefield is correct. Here's the full as I've turned it down twice since last post and its again awaiting its turn to update that which shouldn't exist on my machine.

"Extra ffmpeg codecs for the Chromium Browser" is the exact quote. Its listed as a security update. It is 893kb.

Just weird is all. Has anybody noticed where it gets installed so I might remove whatever is requesting it? 

Thanks for any info. I'll just keep unchecking it for now.

Good morning from Vietnam.

---

### Post by &amp;KyT$0P# on 2016-09-10
This command should give you all the information you want to know -
```
apt-get -s purge 'chromium-codecs*'
```

Please post its output here if you have any further questions.

---

### Post by night_sky2 on 2016-09-10
If you install Ubuntu Restricted Extras than you get the Chromium codecs. Since Chromium is open-source, it doesn't have any built-in. So they are included in the extras package.

---

### Post by howefield on 2016-09-11
> **barkester-b said:**
> Howefield is correct. Here's the full as I've turned it down twice since last post and its again awaiting its turn to update that which shouldn't exist on my machine.

Try...

```
apt rdepends chromium-codecs-ffmpeg-extra
```

If it hasn't come from the[ Ubuntu Restricted Extras package]("http://packages.ubuntu.com/xenial/ubuntu-restricted-addons") perhaps you have installed the Opera browser ?

> Good morning from Vietnam.

Likewise from a surprisingly sunny south west Scotland. :)

---

### Post by barkester-b on 2016-09-11
Looking like I did let the extra packages get by. I recently reinstalled both my OSs and figured the list of extras was short and could delete them later, which I did try to do.

   Never found Google anything, though so far as installed programs. Deleted JAVA fine (dislike PUAs).

   Never dug thru my and vet codecs before, so should make a hopefully short project when I get around to it One more thing for a hobbyist to piddle with.

  
   Thanks all.

---

### Post by barkester-b on 2016-09-15
Here's Halogen' terminal feedback for :[COLOR=#000000][FONT=&quot]apt-get -s purge 'chromium-codecs*'[/FONT][/COLOR] . I looked up regex, but as a chump couldn't find whats useful. Any clues?

NOTE: This is only a simulation!
      apt-get needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'chromium-codecs-ffmpeg' for regex 'chromium-codecs*'
Note, selecting 'chromium-codecs-ffmpeg-extra' for regex 'chromium-codecs*'
Note, selecting 'chromium-codecs-ffmpeg-extra-dbg' for regex 'chromium-codecs*'
Note, selecting 'chromium-codecs-ffmpeg-dbg' for regex 'chromium-codecs*'
Package 'chromium-codecs-ffmpeg' is not installed, so not removed
Package 'chromium-codecs-ffmpeg-dbg' is not installed, so not removed
Package 'chromium-codecs-ffmpeg-extra-dbg' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-34 linux-headers-4.4.0-34-generic
  linux-image-4.4.0-34-generic linux-image-extra-4.4.0-34-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  chromium-codecs-ffmpeg-extra*
0 upgraded, 0 newly installed, 1 to remove and 3 not upgraded.
Purg chromium-codecs-ffmpeg-extra [51.0.2704.79-0ubuntu0.14.04.1.1121]
 

This update is bizarre. I was offline 2 days after moving and it still came on. Makes me wonder if it downloaded already and is just waiting for permission to install. Super-persistant.

---

### Post by CantankRus on 2016-09-15
It already knows there is an update. Doesn't matter you have been offline.
There is nothing suspicious about the update unless you have added random third party ppas.
Command to show all enabled repositories...
```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*.list
```

Where is the update coming from....
```
apt policy chromium-codecs-ffmpeg-extra
```
eg
```
**[COLOR="#006400"]glen@Xenial:~$[/COLOR] apt policy chromium-codecs-ffmpeg-extra**
chromium-codecs-ffmpeg-extra:
  Installed: 52.0.2743.116-0ubuntu0.16.04.1.1250
  Candidate: 52.0.2743.116-0ubuntu0.16.04.1.1250
  Version table:
 *** 52.0.2743.116-0ubuntu0.16.04.1.1250 500
        **500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe amd64 Packages**
        500 [http://ftp.iinet.net.au/pub/ubuntu](http://ftp.iinet.net.au/pub/ubuntu) xenial-updates/universe amd64 Packages
        100 /var/lib/dpkg/status
     49.0.2623.108-0ubuntu1.1233 500
        500 [http://ftp.iinet.net.au/pub/ubuntu](http://ftp.iinet.net.au/pub/ubuntu) xenial/universe amd64 Packages
```

Just let it update. :P

---

### Post by &amp;KyT$0P# on 2016-09-16
> **barkester-b said:**
> I looked up regex, but as a chump couldn't find whats useful. 
There at least two different kinds of regex in Ubuntu.  What context are you looking to use the regex in?

> Any clues?
Yep.
That command was a simulation of uninstalling the package(s) you don't want, showing you what would happen -
> ```

NOTE: This is only a simulation!
      apt-get needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'chromium-codecs-ffmpeg' for regex 'chromium-codecs*'
Note, selecting 'chromium-codecs-ffmpeg-extra' for regex 'chromium-codecs*'
Note, selecting 'chromium-codecs-ffmpeg-extra-dbg' for regex 'chromium-codecs*'
Note, selecting 'chromium-codecs-ffmpeg-dbg' for regex 'chromium-codecs*'
Package 'chromium-codecs-ffmpeg' is not installed, so not removed
Package 'chromium-codecs-ffmpeg-dbg' is not installed, so not removed
Package 'chromium-codecs-ffmpeg-extra-dbg' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-34 linux-headers-4.4.0-34-generic
  linux-image-4.4.0-34-generic linux-image-extra-4.4.0-34-generic
Use 'apt-get autoremove' to remove them.
[B][COLOR="#FF0000"]The following packages will be REMOVED:
  chromium-codecs-ffmpeg-extra*[/COLOR][/B]
0 upgraded, 0 newly installed, **[COLOR="#FF0000"]1 to remove[/COLOR]** and 3 not upgraded.
Purg chromium-codecs-ffmpeg-extra [51.0.2704.79-0ubuntu0.14.04.1.1121]
 
```

See the parts I highlighted in red?  Notice how it doesn't want to make any additional changes?
That's your OK to try actually uninstalling it -
```
sudo apt-get purge chromium-codecs-ffmpeg-extra
```

In the (I'd think unlikely) event that something breaks due to that uninstallation, just replace [FONT=Courier New]purge[/FONT] with [FONT=Courier New]install[/FONT] in that command and problem should be solved.

---

### Post by barkester-b on 2016-09-18
Thanks for all the theories. Bizarre that not one of the repliers could tell me what it updated. Guess I'll just go on ignoring it's requests. As an "important security update", maybe I'll get to see an epic failure, but I doubt it. I have OSs on USB and files are backed up so no harm. Should a missing codec update crash my machine, it will be a story to tell.

    Years on the net, the most obvious ruses for getting garbage on machines is to say "Security Update!" Google would be a great name to use and I've both seen it's name used without consent and as a paid accomplice. The majority trust it which makes it a perfect Trojan. Similar reason for why I don't use Windows really.

    I'm sorry, but there's no way I can believe that a Google codec for a machine with no Google software could possibly be classified as a "security update".  I don't even have Opera preferring Yandex. Just smells wrong in every way. As I'm unable to extend my faith and trust in billion-dollar Amer. corporations, I must, with them, ask for verification which is what I'm doing in the only way I know in the time I have for such a side project. No verification means rejection. 

   Could be Ubuntu is just getting too mainstream for me, if Google has become an integral important piece of the Ubuntu base and thats why it doesn't point to an app or program. May be time to move on soon. I will miss the convenience. Ubuntu does make things easy.  

   Just run as is for now. I find if I leave the resultant update pop-ups open in the background they don't multiply and I've been getting used to them.

   Thanks for the theories. Learned a bit.

---

### Post by CantankRus on 2016-09-18
> 
**_chromium-codecs-ffmpeg-extra_**
This package contains the multi-threaded ffmpeg codecs needed for the HTML5
<audio> and <video> tags. In addition to the patent-free ogg, vorbis and
theora codecs, aac/ac3/mpeg4audio/h264/mov/mp3 are also included.  See
chromium-codecs-ffmpeg if you prefer only the patent-free codecs

> **_chromium-codecs-ffmpeg_**
This package contains the multi-threaded ffmpeg codecs needed for the HTML5
<audio> and <video> tags. Only the free ogg, vorbis and theora codecs are
included. See chromium-codecs-ffmpeg-extra for additional codecs


Chromium doesn't mean google.
google-chrome is built from the open source chromium-browser.
Somewhere along the line you have installed the patented codec package to get something to work.

You can remove the package if you have no need for aac,ac3,mpeg4audio,h264,mov and mp3, which I doubt you want to do.
You won't be able to play html5 content on some sites and youtube will revert to using flash if installed.
Not removing and not updating is a security risk.

In windows you can install crap from all over the internet but you still trust windows update.
As I said, this package comes from the Ubuntu repositories.
If you don't trust the official Ubuntu repositories you may as well disconnect from the internet.
You're barkestering up the wrong tree. :P

---

### Post by howefield on 2016-09-19
+1 to all that CantankRus said and just to add that you don't have to sit in the dark bleating about security update ruses, view the changelogs for any package at packages.ubuntu.com and follow the CVEs for the information that you want.

---

