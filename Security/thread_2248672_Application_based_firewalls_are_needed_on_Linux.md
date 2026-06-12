---
title: "Application based firewalls are needed on Linux"
date: 2014-10-16
forum: Security
---

### Post by MADDSNIPER on 2014-10-16
Ive been trying to switch over to Linux from Windows full time and im  finding advice from people such as, ""Firewalls" at the application  level don't exist on Linux because they essentially are of no use."

and,  "There really is not much of a point in having an application based  firewall in linux. the problem in windows was all the spyware that  called home. We do not have to deal with such things. Especially if you  only use the packages in the repos." very interesting.

One of the  things I was struggling to find on Linux was a music player that  rivaled the likes of winamp. I tried many things, one of the ones i  liked the most was clementine which is in most repos and comes installed  with alot of linux distros. I used clementine on linux for a while then  decided to try it on my windows machine as well. To my horror every mp3  i played through clementine on windows caused it to try to connect to  the internet without my aproval. There was no option anywhere to turn  this feature off. I was easily able to block this in windows with my  application based software firewall but on Linux i didnt even know it  was happening. What was being sent out over the internet without my  permission? well i found this site to help me with that:

[http://thesimplecomputer.info/choosing- ... sic-player]("http://thesimplecomputer.info/choosing-a-linux-music-player")

This guy does some nice reviews of linux music players, I'll paste some notes from it:

"Beatbox  was built with the Last.fm API but unfortunately no way to turn it off.  This means that the player will make a TLS encrypted connection to  ws.audioscrobbler.com for every track change. This is also when the  lyrics plugins are disabled and a Last.fm account was not being used."

"Wireshark  revealed Amarok as the most talkative of all players here. On launch it  connects to Last.fm, Mangnatune and Internet Archive but when you play a  track, there’s a hemmorhage of web traffic.

Youtube, Myspace,  Harvard, Rolling Stone, RIAA (…confused??), Associated Press, WordPress,  Wikipedia, MTV, USA Television and Huffington Post are contacted simply  by playing a song. And those are just the ones you’d likely recognize;  there were many more hostnames which you’d be forgiven for not knowing."

"I  did catch some internet activity from Clementine. A few seconds after  launching, the player connects to Magnatune and Google. If you don’t use  it, Magnatune can be disabled which will stop that connection. The  Google call, however, persisted even when all the extras were disabled.  Clementine sends a GET request to a 1e100 server wanting my geolocation  (by IP address) info and Google responds with the date and time, my city  name, latitude & longditude and country. This happens every time  Clementine starts and the developers said it’s used by the Songkick API  to find concerts in your area for artists you’re listening to."

"Guayadeque  has intelligent playlists where it can add tracks from your library to a  currently opened playlist based on what’s already in it. Wireshark  showed how this works; Guayadeque asks audioscrobbler.com for similar  tracks to the playing song and is then served a list. If any artists or  albums on the list match what’s in your library, they’re added to the  playlist. Guayadeque also has bulk editing ID3 tags which is incredibly  useful if you’ve ever assigned tags to hundreds of albums.

Again  courtesy of Wireshark, there’s no way to turn off lyric or cover art  fetching. You can hide the tabs from view in Guayadeque, but GET  requests are still sent out to lyrics.com, lyricsmania.com,  images.amazon.com, coveralia.com, loudson.gs, lettras.mus.br, among  many, many others. The player tries a lot of different sources for  lyrics and cover art before giving up so Guayadeque will spit out a lot  of internet traffic if you listen to lesser-known artists."

"each  time Juke changed a track, it contacted lyrics.wikia.com. This was  despite the lyrics option being unchecked and the pane hidden from view  so there’s no way to disable that. Sloppy."

"On track changes,  Audioscrobbler, lyrics sites and Google Translate are contacted.  Nightingale is set to translate lyric text by default but these  connections can be stopped by disabling the relevant services. The  inital connections when the program is launched, however, cannot be  disabled as easily. You could either use UFW like with Beatbox &  Clementine, set Nightingale’s proxy (in Network Settings) to 127.0.0.1  on port 80 or remove ~/.Nightingale and rebuild its profile without  metrics reporting."

"It probably goes without saying by now that  Tomahawk is not a good choice for people with pay-by-bandwidth internet  plans. The only way to keep Tomahawk offline is to either block it in  ufw or disable the internet connection."


Thoughts?

---

### Post by HermanAB on 2014-10-16
Howdy,

Basically, UNIX is not Windows.  Deep down, everything is different.

You don't need a firewall for various reasons:
a. The Linux network stack is strong enough and doesn't need special filters.
b. You have complete control over what processes and services you run.
c. SELinux / AppArmor provides strong, granular security.
d. If you still want to make an application based filter, then you can do so, if you know what you are doing.

One method to make an application based netfilter rule, is to launch an application as a unique group, then mark all packets related to that group and then filtering based on the marks.

So, what you want, is both not really needed and can be done anyway if you really want to.

---

### Post by thnewguy on 2014-10-16
I find it really disappointing that people don't think there is any reason to have application based firewalls on Linux. There are lots of cases where an application-aware firewall makes sense. This is especially true of cases where applications report home on a common port, like 80, looking like just another web page request. There is a stronh demand for application-aware firewalls on Linux (has been for over a decade), sadly it's not something it looks like we are going to get.

As Herman pointed out, there are work arounds. One being the use of something like AppArmor to limit an application's access to the network.

Another way to go would be to monitor your network traffic and spot the name/IP of the server your media player is contacting. Then block all traffic going out to the address. This would be a lot easier than messingwith AppArmor.

Perhaps the easiest approach though is to take advantage of a Linux feature which allows you to block command run by a specific user. If you can set up your application so that it runs as a specific user, let's call that user "dummy" then you can block all network access made by programs run with "dummy" permissions. Here is an example: [http://www.ubuntugeek.com/disable-internet-access-for-particular-user-in-ubuntu.html](http://www.ubuntugeek.com/disable-internet-access-for-particular-user-in-ubuntu.html)

---

### Post by HermanAB on 2014-10-17
It is very easy to block an app with iptables.  Launch the app with sg, then make two iptables rules, the first to mark packets based on the group and the second to filter the marked packets.

---

### Post by vasa1 on 2014-10-17
> **HermanAB said:**
> ...  Launch the app with sg, ...
What is "sg"?

---

### Post by Lars Noodén on 2014-10-17
> **vasa1 said:**
> What is "sg"?

[sg](http://manpages.ubuntu.com/manpages/utopic/en/man1/sg.1.html) launches a program under a different group.

---

### Post by vasa1 on 2014-10-17
> **Lars Noodén said:**
> [sg](http://manpages.ubuntu.com/manpages/utopic/en/man1/sg.1.html) launches a program under a different group.Thanks :)

---

### Post by Lars Noodén on 2014-10-17
> **MADDSNIPER said:**
> ""Firewalls" at the application  level don't exist on Linux because they essentially are of no use."

I would agree that they are not much use.  But if you want to play with them you can try the groups method mentioned above.  There were once some options to match program name or PID but those have since been taken out of iptables.  If you can find the discussion of that, it might be interesting.  

However, sometime in the future apparmor might gain the capability to limit network access.

[https://bugs.launchpad.net/apparmor/+bug/796588](https://bugs.launchpad.net/apparmor/+bug/796588)

---

