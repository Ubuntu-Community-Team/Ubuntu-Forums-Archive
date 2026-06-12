---
title: "How to use sopcast effortlessly"
date: 2008-06-14
forum: Tutorials
---

### Post by chick on 2008-06-14
I have figured out a way to setup Sopcast and VLC such that multiple streams can be openned and closed in mass and effortlessly. After setting up, clicking on a sop:// URL from your browser will start the stream and VLC, and quiting VLC will get that stream automatically killed.

Without further ado, here's how:
[LIST=1]
[*] Install sp-sc-auth and VLC, if you haven't already.
```

sudo apt-get install vlc
wget http://download.sopcast.org/download/sp-auth.tgz
tar xzvf sp-auth.tgz
sudo cp sp-auth/sp-sc-auth /usr/bin/

```
[*] Install my 'sopcast' script, check [https://launchpad.net/sopcast.sh](https://launchpad.net/sopcast.sh) for new version
```

wget http://launchpad.net/sopcast.sh/main/0.6/+download/sopcast.tar.gz
tar xzvf sopcast.tar.gz
sudo cp sopcast/sopcast /usr/bin/

```
[*] Configure your browser to handle the sop:// protocol,
[LIST]
[*]for Firefox, go to the URL 'about:config', right click and chose New -> String, put 'network.protocol-handler.app.sop', then value "sopcast",
[*]for Opera, go to Preferences/Advanced/Programs -> Add, then put 'sop' in Protocol and 'sopcast' under Open with other application.
[/LIST]
[*] Point your browser to [http://www.sopcast.com/channel/chlist.jsp](http://www.sopcast.com/channel/chlist.jsp) or [http://www.myp2p.eu/](http://www.myp2p.eu/) for lists of streams. A single click would open the stream after 20 seconds.
[/LIST]

If you prefer mplayer or something else, do this
```

sudo sed -i 's/vlc/mplayer/' /usr/bin/sopcast

```

If you have problems, open browser from a terminal and you will see error messages.

Enjoy!

---

### Post by fox_cream on 2008-07-01
Cheers for this mate.  Absolutely amazing.  Solved my sopcast problems instantly.  When the season starts I can now watch the footy on the TV through the xbox.  Ace.

Firefox 3 no longer requires the editing of the About:config.  You can pick the application from a list in a popup box.

---

### Post by jualin on 2008-07-01
thank you dude, i was trying to do this the other day, but I have been to lazy to find a solution. Thank you again!

---

### Post by piercleo on 2008-07-08
Arg sounded too perfect to be true. When i click on a sopcast link, the firefox popup appears, I chose sopcast but then nothing happens. Have tryed to reboot firefox, and computer.

How can I identify where the problem comes from ?

PierC

---

### Post by unicorn_2003_1 on 2008-07-09
The VLC window won't instantly popup, you'll have to wait for a few seconds, on my machine, that's like 10 seconds or so, depending on the channel. Most likely, VLC will be opened after sopcast has been buffered to a certain percentage, like 40%. If the channel you clicked on is slow to buffer, it'll take a lot of time and you may think it's just dead.

Thanks chick, you're my bro!

---

### Post by piercleo on 2008-07-10
Thank you but i let a LOT of time and still no answer... so weird !

---

### Post by nikhilgupta on 2008-07-11
Here is a possible improvement to this wrapper:

Improvements:

1) Monitor sopcast's progress and start player as soon as buffer is more than 70% full.
3) Use mplayer :)
2) Prompt to restart player if it dies (This happens for me sometimes with mplayer.) 

Additional commands used:

mkfifo
sp-sc instead of sp-sc-auth
awk 
sed
zenity

-Thanks.

---

### Post by Timon&amp;Pumba on 2008-07-11
There is also: [http://code.google.com/p/gsopcast/]("http://code.google.com/p/gsopcast/"), which uses mplayer and allows for some customization.

---

### Post by lacostranostra on 2008-07-11
> **chick said:**
> I have figured out a way to setup Sopcast and VLC such that multiple streams can be openned and closed in mass and effortlessly. After setting up, clicking on a sop:// URL from your browser will start the stream and VLC, and quiting VLC will get that stream automatically killed.

Without further ado, here's how:
[LIST=1]
[*] Install sp-sc-auth and VLC, if you haven't already.
```

sudo apt-get install vlc
wget http://download.sopcast.org/download/sp-auth.tgz
tar xzvf sp-auth.tgz
sudo cp sp-auth/sp-sc-auth /usr/bin/

```
[*] Install my 'sopcast' script, check [https://launchpad.net/sopcast.sh](https://launchpad.net/sopcast.sh) for new version
```

wget http://launchpad.net/sopcast.sh/main/0.6/+download/sopcast.tar.gz
tar xzvf sopcast.tar.gz
sudo cp sopcast/sopcast /usr/bin/

```
[*] Configure your browser to handle the sop:// protocol,
[LIST]
[*]for Firefox, go to the URL 'about:config', right click and chose New -> String, put 'network.protocol-handler.app.sop', then value "sopcast",
[*]for Opera, go to Preferences/Advanced/Programs -> Add, then put 'sop' in Protocol and 'sopcast' under Open with other application.
[/LIST]
[*] Point your browser to [http://www.sopcast.com/channel/chlist.jsp](http://www.sopcast.com/channel/chlist.jsp) or [http://www.myp2p.eu/](http://www.myp2p.eu/) for lists of streams. A single click would open the stream (after 20 second).
[/LIST]

Enjoy!

has anyone been able to install this on hardy x86? pls provide install instructions.

---

### Post by unicorn_2003_1 on 2008-07-11
Yes, it works on Hardy. Been using this for days and it works fine, though a GUI would be even better. Plus, the sopcast website or the channel list seems to be down at this time.

---

### Post by chick on 2008-07-13
piercleo, if open your browser from a terminal there will be error messages. Post the lines that begin with 'sopcast:' and we'll see what the problem is.

---

### Post by NovruzeliH on 2008-07-13
very usefull thanks alot :p

---

### Post by chick on 2008-07-13
> **nikhilgupta said:**
> 
1) Monitor sopcast's progress and start player as soon as buffer is more than 70% full.

That's cool, but I do hate the fact that sp-sc throws everything to stdout instead of stderr (and it really does churn out lots of crap ...) If you let the stream on for days like i do this will fill up the harddrive. not cool. It really is bad programming from them.

> **nikhilgupta said:**
> 
3) Use mplayer :)
2) Prompt to restart player if it dies (This happens for me sometimes with mplayer.) 

Haha I'm not so sure that's an improvement :p

---

### Post by chick on 2008-07-13
I actually don't think a GUI is any better here, because all a GUI does is read the channel URL off the official website in XML. If the website goes down the channel URL from a GUI will also go outdated anyway.

Plus, since this is P2P there will be streams from all over the net like trackers for bittorrent, e.g. [www.myp2p.eu](www.myp2p.eu) has lots of sport streams that the official website doesn't have.

---

### Post by c-m on 2008-09-10
followed the guide flawlessly, clicking on a sopcast link does absolutley nothing. How can i tell what is wrong?

---

### Post by chick on 2008-09-11
> **c-m said:**
> followed the guide flawlessly, clicking on a sopcast link does absolutley nothing. How can i tell what is wrong?

Most likely the link doesn't work :p

If you open browser from a terminal you will see error output.

---

### Post by c-m on 2008-09-11
Thats the thing i did open the browser from the terminal firefox runs but I still have a command prompt i.e i can still use the same terminal tab to run other programs and do other things while firefox is running. Hence I get no output at all.

Ever come across that?


> carl@carl-desktop:~$ firefox
carl@carl-desktop:~$ 

---

### Post by the_poolster on 2008-09-13
I installed qsopcast and it worked fine, until that is the channel list (actually, the whole [www.sopcast.org](www.sopcast.org)) went down. Qsopcast was useless and the Liverpool v. Man U game had started already. I found a program called sopcaster which seems very simple and you can just paste the sop:// address directly in. All my problems were sorted by this and it is installable for dummies (like me!).

[http://petepr.drivehq.com/humpty/](http://petepr.drivehq.com/humpty/)

---

### Post by skathrein on 2008-09-14
Thanks for the great script!  I love that it closes sp-sc-auth when VLC closes.  The only two things I had to change as far as your instructions were the following:
1. In the new firefox string, I had to make the value "/usr/bin/sopcast" instead of just "sopcast."
2. I also had to tell firefox to open the link using sopcast by pointing it to /urs/bin/sopcast instead of just using the default sopcast.
After that, it all worded perfectly.

---

### Post by chick on 2008-09-16
> **c-m said:**
> Thats the thing i did open the browser from the terminal firefox runs but I still have a command prompt i.e i can still use the same terminal tab to run other programs and do other things while firefox is running. Hence I get no output at all.


I meant run firefox from the terminal and click on a sop:// link.

---

### Post by c-m on 2008-09-17
> **chick said:**
> I meant run firefox from the terminal and click on a sop:// link.

That is the output form clicking on a sop:// link - absolutely nothing.


In firefox I have this string and the value as "sopcast" without the quotes.

network.protocol-handler.app.sop

---

### Post by JohnJackson on 2008-09-17
I found that I needed to put in /usr/bin/sopcast instead of sopcast for this to work.

---

### Post by c-m on 2008-09-17
> **JohnJackson said:**
> I found that I needed to put in /usr/bin/sopcast instead of sopcast for this to work.


Thanks - tried that but it still didn't make any difference. still nothing happens when clicking on a spocast link and there is no feedback from the terminal.

---

### Post by chick on 2008-09-17
> **c-m said:**
> Thanks - tried that but it still didn't make any difference. still nothing happens when clicking on a spocast link and there is no feedback from the terminal.

This probably means the script has not been invoked. If you have Firefox 3 (which you should anyway), try setting the protocol handler from the menu (Tool/Options/Applications). 

Also try invoking the script manually. That is, in the terminal, execute 'sopcast sop://link'.

---

### Post by c-m on 2008-09-22
> **chick said:**
> This probably means the script has not been invoked. If you have Firefox 3 (which you should anyway), try setting the protocol handler from the menu (Tool/Options/Applications). 

Also try invoking the script manually. That is, in the terminal, execute 'sopcast sop://link'.


I do run FF3 but there is nothing in Edit/Options/Applications its just blank and you cannot create or change anything there.

Here is my terminal output:

```
carl@carl-desktop:~$ sopcast sop://broker.sopcast.com:3912/40299
sopcast: starting stream sop://broker.sopcast.com:3912/40299 on port 40299
sopcast: VLC failed to start

```

---

### Post by chinobar on 2008-09-23
c-m, i had the same problem, turned out i didn't have vlc installed... :P

Thanks for a great script, works perfectly now!

---

### Post by flyguy97 on 2009-01-06
Hello all,

I created a new SopCast front-end and would love it if people would help test it out a bit. It features a built-in player and a channel guide with the ability to bookmark favorite channels. Currently the only available language is English, but I'm working with a few people to try and bring support for Japanese and Chinese as well. Let me know what needs improvement, and please, be honest.

[http://code.google.com/p/sopcast-player]("http://code.google.com/p/sopcast-player")

[[IMG]http://sopcast-player.googlecode.com/files/Player.gif[/IMG]]("http://code.google.com/p/sopcast-player")

---

### Post by skathrein on 2009-01-07
Looks good but can't get the deb to install.  I'm getting an error regarding vlc dependency even though VLC is already installed and the medibuntu repository has been added.  I'm still running hardy so wondered if that is the problem.  Thanks.

---

### Post by flyguy97 on 2009-01-07
I am actually working on hammering out a deb that will include Hardy as I'm typing this. The problem is the version of VLC, the medibuntu repository includes the 0.8.x player, I wrote my program on Intrepid which has the 0.9.x player. If you want to give a try installing 0.9.x on Hardy try [http://ubuntuforums.org/showthread.php?t=986781]("http://ubuntuforums.org/showthread.php?t=986781"). I don't know if this works as I have never tried it, but its worth a try. You can get updates on my project by going to this [thread]("http://ubuntuforums.org/showthread.php?t=1032901"), or by going to my [google code project homepage]("http://code.google.com/p/sopcast-player/").

> **skathrein said:**
> Looks good but can't get the deb to install.  I'm getting an error regarding vlc dependency even though VLC is already installed and the medibuntu repository has been added.  I'm still running hardy so wondered if that is the problem.  Thanks.

---

### Post by flyguy97 on 2009-01-18
Everything is working with Hardy now, please be sure to visit the installation section of my [project page]("http://code.google.com/p/sopcast-player") for instructions on adding a needed PPA to satisfy the VLC requirement. Let me know how it works out for you.

> **flyguy97 said:**
> I am actually working on hammering out a deb that will include Hardy as I'm typing this. The problem is the version of VLC, the medibuntu repository includes the 0.8.x player, I wrote my program on Intrepid which has the 0.9.x player. If you want to give a try installing 0.9.x on Hardy try [http://ubuntuforums.org/showthread.php?t=986781]("http://ubuntuforums.org/showthread.php?t=986781"). I don't know if this works as I have never tried it, but its worth a try. You can get updates on my project by going to this [thread]("http://ubuntuforums.org/showthread.php?t=1032901"), or by going to my [google code project homepage]("http://code.google.com/p/sopcast-player/").

---

### Post by joshua_james on 2009-09-13
Sorry to bring up an old thread, but when I try to play a vid, the choose a program screen comes up and it won't let me choose sopcast

---

### Post by drainplugofideas on 2009-09-19
I opted to go for the GUI version I found off of google code. I tried this install but wasn't able to get it working. Probably no fault of the program though. Now when I watch sopcast there's two windows both playing the same video. I would like to keep the one with the gui. How can I uninstall the vlc screen?

---

### Post by ssdt on 2009-11-09
Same for me. please help anyone on this issue.

---

### Post by calcio1 on 2009-11-22
How can I stream sopcast to my tv through fuppes?

---

### Post by flyguy97 on 2009-12-03
> **drainplugofideas said:**
> I opted to go for the GUI version I found off of google code. I tried this install but wasn't able to get it working. Probably no fault of the program though. Now when I watch sopcast there's two windows both playing the same video. I would like to keep the one with the gui. How can I uninstall the vlc screen?

dradinplugofideas,

I created a launchpad ppa that eases installation/upgrades, you can find the instructions for installation at [http://code.google.com/p/sopcast-player/wiki/Installation]("http://code.google.com/p/sopcast-player/wiki/Installation"). The issue you referenced in your post has been fixed.

Cheers,
Jason

---

### Post by wharsmetoothpicson on 2009-12-04
Flyguy,

Thanks for the effort in getting the Sopcast GUI off the ground. I have a problem though.

I've added the PPA to my system, however when I try to install the Sopcast Player package I get the following error:

E: Couldn't find package sopcast-player

Any help would be appreciate. I'm a totally Linux noob ^_^

---

### Post by kimme on 2010-07-15
This webpage tells how to install Sopcast in Lucid (10.04) easily.

[http://www.webupd8.org/2010/06/linux-sopcast-player-041-released.html](http://www.webupd8.org/2010/06/linux-sopcast-player-041-released.html)

---

### Post by torrit on 2012-03-10
VLC says that:   p, li { white-space: pre-wrap;:  > VLC can't open MRL 'http://localhost:68445/tv.asf'.


terminal output:
> marcin@torrit-P31-ES3G:~$ opera
sopcast: starting stream sop://broker.sopcast.com:3912/68445 on port 68445
sopcast: VLC not running, killing stream sop://broker.sopcast.com:3912/68445


of course the last line appears after i close VLC.
What's the problem? How do I fix it?

---

### Post by torrit on 2012-03-10
ok i just added one line (18) in "sopcast" and it works
apparently there was a problem with port

>  17 PORT=${1##*/}
 18 PORT=8908

now it works perfectly. thanks for the great script!

---

### Post by shadow of the locust on 2012-03-11
> **kimme said:**
> This webpage tells how to install Sopcast in Lucid (10.04) easily.

[http://www.webupd8.org/2010/06/linux-sopcast-player-041-released.html](http://www.webupd8.org/2010/06/linux-sopcast-player-041-released.html)

Awesome. Thank you.

---

### Post by jao_madn on 2012-05-14
> **torrit said:**
> ok i just added one line (18) in "sopcast" and it works
apparently there was a problem with port



now it works perfectly. thanks for the great script!

Were the same problem
```

PORT=${1##*/} doestn work on mine
PORT=$((RANDOM%10000+9999)) i used this one to produce random number from 10000
 to 19999, a  five digit number which i observe got a better success rate when i tried,
 as we all know few of this 5 digit port used most often

```

---

