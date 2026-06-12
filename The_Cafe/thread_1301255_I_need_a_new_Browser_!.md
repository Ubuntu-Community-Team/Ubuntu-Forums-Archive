---
title: "I need a new Browser !"
date: 2009-10-25
forum: The Cafe
---

### Post by Jean-Danjou on 2009-10-25
Bonjour,
I am looking for a New Web browser who will work in Ubuntu.
Firefox 3.5, is lovely, as he give me the time to make a cup of tea while it start ! Sometimes it's even ready before the tea ! But the main Problem is before Tea got drink, Firefox had already crashed many time ! Saying that it is unstable will be an under statement !!!
So, any one knows a browser who does not take the all day to switch on and does not crash every 2 mn ?...And don't mention Opera 10 please, as it is not Mr Ubuntu best mate!

Merci !

---

### Post by shadow120 on 2009-10-25
ive been having problems with this 3.5 also.  Epiphany is almost the same as firefox but is more stable at the moment

---

### Post by gnuisancev3 on 2009-10-25
I have had wonderful experiences with Chromium.  I currently don't use it because i can't go without my vertical tab bar in firefox, but god is it fast.

---

### Post by novafluxx on 2009-10-25
If you are running Kubuntu, even if you're not, you can try Arora. Its WebKit based, and from my brief experience is pretty neat.

Chomium or Chrome may be up your ally too, if you're willing to run beta software.

---

### Post by segamaster222 on 2009-10-25
Seamonkey? Flock?

---

### Post by ad_267 on 2009-10-25
Midori or Chromium are other options. For both of these you're probably best to use their PPAs, which will be more up to date.

Chromium: 
[https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

Midori: 
[https://launchpad.net/~midori/+archive/ppa](https://launchpad.net/~midori/+archive/ppa)
[https://launchpad.net/~webkit-team/+archive/ppa](https://launchpad.net/~webkit-team/+archive/ppa)

---

### Post by Barriehie on 2009-10-25
I compiled mine and once a week clean up the sqlite db.'s and now it's VERY fast.  Something to consider.  I've tried about every browser out there in regards to speed and always end up coming back to FF... :)  Haven't had any crash type issues so I can't help you there.

Barrie

---

### Post by fluffman86 on 2009-10-25
Try backing up and then deleting your ~/.mozilla folder.  Sometimes problems with firefox are best fixed with a new profile.

Otherwise, Chromium rocks.

---

### Post by garvinrick4 on 2009-10-25
Chromium by far. 
deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main 

 Admin to Software Sources.
Third party software and add. Or other software in 9.10.   Copy and paste.

deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) karmic main  sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 4E5E17B5


Take your choice, do not forget to add key in Terminal.

---

### Post by darco on 2009-10-25
Opera 10 is another good alternative....

[http://www.opera.com/download/](http://www.opera.com/download/)


darco

*edit* heh, didnt see the "dont mention Opera' ..oh well

---

### Post by jpmelos on 2009-10-25
Just in defence of Firefox 3.5... I installed it in Jaunty (Shiretoko) and it is working great. It never crashed, and runs smooth (as smooth as any other stable version of Firefox).

---

### Post by segamaster222 on 2009-10-25
> **darco said:**
> Opera 10 is another good alternative....

[http://www.opera.com/download/](http://www.opera.com/download/)


darco

*edit* heh, didnt see the "dont mention Opera' ..oh well

Thank you for informing me Opera is for Ubuntu :)

---

### Post by lovinglinux on 2009-10-25
Firefox starting slow is usually because of extensions, since the browser needs to load all extension chrome pages and scripts upon start. Additionally, some extensions are configured to execute special function when loaded. If those functions include writing or reading databases, then they can slow down Firefox startup process considerably.

One thing that helps is to avoid starting Firefox with a sidebar opened. Optimizing the databases also improves performance considerably.

Take a look at my tutorial [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by Cope57 on 2009-10-26
[Galeon]("http://galeon.sourceforge.net") is a standards compliant web browser, which integrates well with the GNOME desktop environment.  It does not include an email client, irc bot, website designer etc., therefore has a moderate resource usage.  Internally the program uses Mozilla's Gecko rendering engine to display the web pages so is fully feature complete and standards compliant, as well as rendering pages quickly.

---

### Post by RichardLinx on 2009-10-26
What's wrong with Opera 10?

---

### Post by cariboo on 2009-10-26
> **fluffman86 said:**
> Try backing up and then deleting your ~/.mozilla folder.  Sometimes problems with firefox are best fixed with a new profile.

Otherwise, Chromium rocks.

+1 for creating a new profile in Firefox if it is crashing. 

If you type: **browser** in the search window, not quick search, in synaptic you'll find a whole list of different browsers to try out.

---

### Post by Exodist on 2009-10-26
Opera 10 isnt a bad alternative. There is also that Google Chrome thing.

---

### Post by joey-elijah on 2009-10-26
Chromium is a great choice, but be careful as it is the development version and things do break.

you might prefer using Google Chrome instead as it's "stable snapshots" of Chromium. 

[http://dev.chromium.org/getting-involved/dev-channel#TOC-Linux](http://dev.chromium.org/getting-involved/dev-channel#TOC-Linux)

---

### Post by Khakilang on 2009-10-26
> **Cope57 said:**
> [Galeon]("http://galeon.sourceforge.net") is a standards compliant web browser, which integrates well with the GNOME desktop environment.  It does not include an email client, irc bot, website designer etc., therefore has a moderate resource usage.  Internally the program uses Mozilla's Gecko rendering engine to display the web pages so is fully feature complete and standards compliant, as well as rendering pages quickly.

I try to install but it keep giving broken dependenceis which I have no idea how to solve. So I keep my Firefox 3.5 (Shiretoko) which is working great. But I also install Chromium just in case and also I can test which one perform better.

---

### Post by misfitpierce on 2009-10-26
Midori is pretty decent although based off Webkit like Google Chrome Browser,Safari, and Arora. Firefox runs off Gecko rendering engine and as said Epiphany is built off Gecko firefox rendering engine and you can find it in add/remove programs or the software center on karmic or w.e.

---

### Post by Hallvor on 2009-10-26
Epiphany. Very stable and lighter than FF. Integrates very well on a Gnome desktop.

---

### Post by Jean-Danjou on 2009-10-26
Bonjour.
Thanks for all the replies,
Havnt decide whats gonna be next browser yet, but got a better idea!
(Shiretoko) was working fine on Ubuntu 9.04, but is now gone from synaptique. Seamonkey, I tried yesterday, and it was crashing faster than Mozilla!lol, And as Opera 10, it's a lovely browser, but since it wasn't working properly on 9.04. I am not too sure what to expect...
Anyway, thx again, and I will now try your suggestions ! :)

Merci !

---

### Post by 3rdalbum on 2009-10-26
I didn't have any problems with Opera 10 on Ubuntu 9.04, nor on 8.10, nor on 9.10, nor on my new smartphone :-)

Maybe give it another try? I use Opera 10 on my netbook as it's much faster than Firefox (my netbook has a slow SSD, which Firefox absolutely hammers).

---

### Post by RichardLinx on 2009-10-26
I'll also recommend you give Opera another try. It's been working fine for me on Ubuntu 9.04.

---

### Post by ceciliaFX on 2009-10-26
> **RichardLinx said:**
> What's wrong with Opera 10?

absolutely nothing. in fact on my Ubuntu 8.10 I had upgraded to Opera 10 and it was faster and more stable than my previous Opera version (9.64, i think).

yesterday there was an update to the Ubuntu kernel (2.6.27-15) and opera speed improved. wow.

---

### Post by JillSwift on 2009-10-26
Slow FireFox starts are sometimes due to bloated cache databases.

You might renew it's pep by:
```
sudo apt-get install sqlite3
```Then use this BASH script:
```
#!/bin/bash
killall firefox
killall firefox-bin
cd /home/yui/.mozilla/firefox/[COLOR=Red]y3cyj5zj.default[/COLOR]/
for i in *.sqlite; do echo "VACUUM;" | sqlite3 $i ; done
exit 0
```Replace the code in [COLOR=Red]red[/COLOR] with the profile you use. This removes the kruft from the databases. It helped me, and running this every month or so keeps FF peppy and loading in reasonable times.

---

### Post by timjohn7 on 2009-10-26
Despite your request not to mention Opera 10, I have to recommend it!  It is superb, fast, stable, flexible and full-featured.
I run Iron as an alternative, but have been a fervent Opera supporter since my Windows days and it has run excellently since I installed 7.04.
Install the .deb file from the Opera site and set Flash and jre to the .mozilla directory and it will work flawlessly.
Please give it another try!

---

