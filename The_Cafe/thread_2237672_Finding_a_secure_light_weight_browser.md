---
title: "Finding a **secure light weight browser"
date: 2014-08-03
forum: The Cafe
---

### Post by linuxyogi on 2014-08-03
Hi,

My PC is quite old now but since all I do is watch videos, browse the web and download files I will wait for major hardware failure before upgrading.

I have managed to find a lighter alternative for all apps that I need.

I am using mplayer (cli) in place of vlc, Deluge in place of Vuze, Claws-Mail in place of Thunderbird.

But I just cant find a good lightweight browser which is secure.

I mean which lightweight browser has a noscript equivalent ? I at least found none. Apart from blocking scripts noscript has a feature called ABE (Application Boundary Enforcer) which prevents remote sites from accessing local resources. Although very rarely but I have got this notification.

I am worried about the fact that if I switch to a light weight browser some malicious activity may run without my knowledge coz there is no noscript there to alert me or to prevent that .

Adblocking is another issue but some lightweight browsers include ad blocking plugins. 

Can you think of any lightweight browser which can match the security of Firefox+Noscript+Bluhell/Adblock ?

---

### Post by vasa1 on 2014-08-03
Re. Bluhell: [http://www.wilderssecurity.com/threads/im-just-blown-away-by-bluhell-firewall.364244/#post-2374807](http://www.wilderssecurity.com/threads/im-just-blown-away-by-bluhell-firewall.364244/#post-2374807)

---

### Post by rv_happy on 2014-08-05
> **linuxyogi said:**
> 
Can you think of any lightweight browser which can match the security of Firefox+Noscript+Bluhell/Adblock ?

Midori has adblock, Flash block and custom scripts. I haven't  tried it in ages but the Arch wiki has some useful info: [https://wiki.archlinux.org/index.php/Midori](https://wiki.archlinux.org/index.php/Midori)

In the end it might be better to reduce all unnecessary system services at start up, perhaps just run a window manager on its own without any panels and  devote as much of the system as possible to the browsing session?

---

### Post by linuxyogi on 2014-08-05
> **rv_happy said:**
> Midori has adblock, Flash block and custom scripts. 

Yes, I have already installed Midori. I have enabled adblocking but it doesn't seem to have anything like Noscript which asks confirmation for individual scripts. You can either enable scripts or disable them.


[IMG]http://ibin.co/1VlVuPivIoaX[/IMG]



> **rv_happy said:**
> In the end it might be better to reduce all unnecessary system services  at start up, perhaps just run a window manager on its own without any  panels and  devote as much of the system as possible to the browsing  session?

My PC specs :

AMD ATHLON 64 X 2 5600+ 
Ram : 2GB
Nvidia 6150SE

The only thing thats making the system slow are the modern browsers like Firefox and Chromium. Otherwise even when I do multitasking for example with Midori,Claws-Mails, mplayer there is no significant slowdown under default Lubuntu or Manjaro XFCE session.

---

### Post by mastablasta on 2014-08-05
remove flash. problem solved :P

seriously those specs should handle any browser. I am not sure what the issue is.
Celeron 3300 (I think this one is probably weaker than yours), 1,2GB ram, old Radeon 9600 - 256MB - Kubuntu -  work fluently with any browser (until recent overheating issue), default desktop effects enabled.

---

### Post by linuxyogi on 2014-08-05
> **mastablasta said:**
> remove flash. problem solved :P

seriously those specs should handle any browser. I am not sure what the issue is.
Celeron 3300 (I think this one is probably weaker than yours), 1,2GB ram, old Radeon 9600 - 256MB - Kubuntu -  work fluently with any browser (until recent overheating issue), default desktop effects enabled.

The thing is I dont watch TV anymore. I got a huge collection of videos on my HDD. 

So the following apps run on my system (multitasking) :

mplayer
Deluge(Occasionally) 
Web Browser (For Facebook sound alerts)
Claws-Mail (Configured with audio notification)

While all these apps are active and I try to play 1080p videos the sound gets distorted and suppose I ry to minimize the mplayer window which was playing for sometime I find that the system has become very unstable. 
Then I usually do ALT+F2> xkill then kill each app. 

How you manage to run Kubuntu on a system with only 1.2GB of Ram I have no idea.

Does Mhz matters ? Mine is 333 MHz.

---

### Post by rv_happy on 2014-08-05
333 MHz is a bit on the slow side but check your hard drive. A relatively cheap SSD could massively improve performance. Multitasking is largely controlled by the processor anyway, not so much by RAM.

Have you looked into using a Facebook client rather than running a full browser just to keep an eye on notifications?

---

### Post by linuxyogi on 2014-08-05
> **rv_happy said:**
> 333 MHz is a bit on the slow side but check your hard drive. A relatively cheap SSD could massively improve performance. Multitasking is largely controlled by the processor anyway, not so much by RAM.

Have you looked into using a Facebook client rather than running a full browser just to keep an eye on notifications?

Some months back I went to #ubuntu on freenode and asked about the name of the Facebook client package. Some said the project is no longer in development and others suggested a package (I don't remember the name) which I found out will function under the Unity DE only.

If you know of any open source Facebook client which will work under Lubuntu please give me the link.

---

### Post by linuxyogi on 2014-08-05
Found an app in the Manjaro repos. Its called Facebook-for-linux. Will search for the same in the Ubuntu repos as soon as I reboot.

[IMG]http://ibin.co/1Vqj5JqjvO7l[/IMG]

---

### Post by vasa1 on 2014-08-05
> **linuxyogi said:**
> ... Will search for the same in the Ubuntu repos as soon as I reboot.
...
[https://launchpad.net/facebookwindoof](https://launchpad.net/facebookwindoof).

---

### Post by linuxyogi on 2014-08-06
> **vasa1 said:**
> [https://launchpad.net/facebookwindoof](https://launchpad.net/facebookwindoof).


The Facebook-for-linux project is dead.

[IMG]http://ibin.co/1Vr8pNUAyx3p[/IMG]





But the link you gave me is actually a fork of the above project only. Look, its the same thing. Thanks a lot.

[IMG]http://ibin.co/1Vr9n0luiA4v[/IMG]

---

### Post by vasa1 on 2014-08-06
> **linuxyogi said:**
> ...
But the link you gave me is actually a fork of the above project only. Look, its the same thing. Thanks a lot.
...
It may pull in a lot of **qt** stuff. So, if you do add the ppa, check for dependencies!

---

### Post by vasa1 on 2014-08-06
No one has mentioned **xombrero** ... Here's a bit from **apt-cache show xombrero**:> Description: Minimalist's web browser
 xombrero is a minimalist web browser with sophisticated security features
 designed-in, rather than through an add-on after-the-fact.  In particular, it
 provides both persistent and per-session controls for scripts and cookies,
 making it easy to thwart tracking and scripting attacks.
 .
 In addition to providing a familiar mouse-based interface like other web
 browsers, it offers a set of vi-like keyboard commands for users who prefer to
 keep their hands on their keyboard.
 .
 The default settings provide a secure environment.  With simple keyboard
 commands, the user can whitelist specific sites, allowing cookies and scripts
 from those sites.


To get a recent version you'll need to add a ppa: [https://launchpad.net/~unit193/+archive/ubuntu/xombrero](https://launchpad.net/~unit193/+archive/ubuntu/xombrero)

The reason I didn't mention it before is because I feel it's a technically difficult browser to tweak. I tried and gave up. Xombrero users seem to be the strong, silent type who are comfortable with *vi*. Now I use it in its default mode to open unknown sites (because I don't want to bloat my Adblock Plus custom filter list with exceptions).

---

### Post by user1397 on 2014-08-06
I've gotta ask, what is the main reason why you feel the need to use the NoScript extension.  I found it to be way too annoying and intrusive for everyday browsing.

I currently use chromium with adblock+ and nothing else, and I can't complain.  Am I missing something here?

---

### Post by mastablasta on 2014-08-06
yes you are. if you have scripts running automatically then malware can be run automatically when you access the site. though many site (including mine) use java scripts to give a better look and feel for the user some certain sites do have malicious scripts. in firefox no script add-on enables you to select sites or scripts on sites you will allow to be run.

I am not sure what the addblock plugin does in chromium. it could be doing the same thing or it could be just blocking the adds. but I am sure you can check the features of that add-on if you are interested.

---

### Post by rv_happy on 2014-08-06
How much malware actually targets Linux though? Whilst it is technically possible, is it worth worrying about to the extent of running noscript all the time? Genuine question.

---

### Post by vasa1 on 2014-08-06
> **rv_happy said:**
> How much malware actually targets Linux though? Whilst it is technically possible, is it worth worrying about to the extent of running noscript all the time? Genuine question.
Browser malware could be platform-agnostic; social engineering certainly is. And NoScript won't prevent users parting with goodies; that's up to the user's commonsense.

Anyway, I don't use NoScript at all but then I try to browse safely as well.

---

### Post by mooreted on 2014-08-06
I just use Chrome and turn off Javascript. I turn it on for sites where I absolutely need it. That seems to stop all the annoying crud the Internet has become for me.

---

### Post by user1397 on 2014-08-06
[quote=mooreted][COLOR=#000000]I just use Chrome and turn off Javascript. I turn it on for sites where I absolutely need it. That seems to stop all the annoying crud the Internet has become for me.[/quote][/COLOR]

Yea I just don't see the point of NoScript when you can just do that in every major browser.  Still, way too annoying for me.  I just have adblock for annoying ads, and then just use common sense/safe browsing.  As far as I know, I haven't encountered a single piece of malware from browsing the internet for as long as I can remember.

---

### Post by pqwoerituytrueiwoq on 2014-08-06
i just read something that may help you
[http://ubuntuforums.org/showthread.php?t=2238206](http://ubuntuforums.org/showthread.php?t=2238206)
think offloading the filtering process would help?

when your browser gets slow run this and see if it speeds back up (warning: seems to crash chromium)
[FONT=courier new]pkill -f flashplayer[/FONT]

---

### Post by mastablasta on 2014-08-07
> **ubuntuman001 said:**
> [/COLOR]

Yea I just don't see the point of NoScript when you can just do that in every major browser.  Still, way too annoying for me.  I just have adblock for annoying ads, and then just use common sense/safe browsing.  As far as I know, I haven't encountered a single piece of malware from browsing the internet for as long as I can remember.

no script prevents java scripts on sites. but it also allows on site you tell it to. with it you can also allow only certain script on certain site and nothing else. e.g. you allow script that displays pictures (picture viewer) and disable all other scripts such as add scripts, socialising scripts etc. if you turn script off in browser it's either all on or all off. no middle ground.

I picked up a malware once. long time ago. it just installed itself. 

safe browsing is what exactly? reputable sites? you could consider wall street journal safe, but if it was hacked and someone uploaded malicious scritp it wont' be safe anymore. as soon as you step on it the script would launch and install malware.

and this malware is OS agnostic. 

I am not saying noscript it is a bullet proof protection. I am saying it is an extra layer. addblock plugins are usually doing similar/same thing as no script, but not always (they might be blocking only adds) which is why I suggested into looking at the features.

---

### Post by vasa1 on 2014-08-07
> **mastablasta said:**
> ...
safe browsing is what exactly? reputable sites? you could consider wall street journal safe, but if it was hacked and someone uploaded malicious scritp it wont' be safe anymore. as soon as you step on it the script would launch and install malware.

and this malware is OS agnostic. 

I am not saying noscript it is a bullet proof protection. I am saying it is an extra layer. addblock plugins are usually doing similar/same thing as no script, but not always (they might be blocking only adds) which is why I suggested into looking at the features.
The thing is how people use NoScript. Most sites have so many scripts running. It would take a very knowledgeable person to know what to allow and what not to allow.

Do you know more details about how the malware would install?

---

### Post by linuxyogi on 2014-08-07
> **vasa1 said:**
> No one has mentioned **xombrero** ... Here's a bit from **apt-cache show xombrero**:

To get a recent version you'll need to add a ppa: [https://launchpad.net/~unit193/+archive/ubuntu/xombrero](https://launchpad.net/~unit193/+archive/ubuntu/xombrero)

The reason I didn't mention it before is because I feel it's a technically difficult browser to tweak. I tried and gave up. Xombrero users seem to be the strong, silent type who are comfortable with *vi*. Now I use it in its default mode to open unknown sites (because I don't want to bloat my Adblock Plus custom filter list with exceptions).


I have used Xombrero. Problem with Xombrero is that neither can it remember passwords nor does your logins persist. I use long complex passwords. Its impossible to remember them.

---

### Post by mastablasta on 2014-08-07
> **vasa1 said:**
> The thing is how people use NoScript. Most sites have so many scripts running. It would take a very knowledgeable person to know what to allow and what not to allow.


which is why no script blocks all by default. and then you see for example BBC videos script and you know that will be needed to view videos.

> 
Do you know more details about how the malware would install?

wish I had more knowledge about these scripts. My site was hacked last month via plugin and just yesterday I got a message that someone changes java scripts. I am hoping to have a programer look at them later today to see if anything malicious was added. however in this case I have a feeling that "someone" was me enabling and then disabeling a plugin feature. at least I am hoping they didn't get back in or that I haven't overlooked a backdoor.

anyway as I understand these are small programs that can do many things. including introducing malware to computer.

like I said it is not 100 % protection, but at least I get scripts blocked by default and then only unblock if I need any.

---

### Post by vasa1 on 2014-08-07
> **linuxyogi said:**
> I have used Xombrero. Problem with Xombrero is that neither can it remember passwords nor does your logins persist. I use long complex passwords. Its impossible to remember them.I think the Xombrero devs regarded storing passwords and persistent logins as risks.

---

### Post by linuxyogi on 2014-08-07
> **ubuntuman001 said:**
> I've gotta ask, what is the main reason why you feel the need to use the NoScript extension.  I found it to be way too annoying and intrusive for everyday browsing.

I currently use chromium with adblock+ and nothing else, and I can't complain.  Am I missing something here?

All security tools will limit you in some way. If you create a very strict apparmor profile for Chromium that will create annoyance too.

I use bluhell just to avoid the ads not for security reasons.

Apparmor may be easy for some people but I tried a lot and gave up.

Blocking scripts may be the primary focus of Noscript but as I mentioned before it  has Application Boundary Enforcer and anti-*Clickjacking* protection too.

---

### Post by vasa1 on 2014-08-07
> **linuxyogi said:**
> ...
Blocking scripts may be the primary focus of Noscript but as I mentioned before it also has Application Boundary Enforcer and anti-*Clickjacking* protection too.
Since NoScript's functionality is important to you why don't you just use Firefox? You said it's heavy/sluggish on your system? Maybe you could provide more details in another thread and people could help you with it?

---

### Post by linuxyogi on 2014-08-07
> **vasa1 said:**
> Since NoScript's functionality is important to you why don't you just use Firefox? You said it's heavy/sluggish on your system? Maybe you could provide more details in another thread and people could help you with it?

Frankly I am still using Firefox most of the times and the only reason is Noscript I just don't feel safe browsing without it.

If you ask me I will create a thread but what's the point ?

I see only two options, one is to add Ram to my existing system and the other is to go for a full upgrade. I mean we cant possibly make Firefox any lighter. 

I will be assembling a new PC in middle of 2015 so it doesn't feel right to buy legacy peripheral (DDR2) that too at a comparatively high price. 

I will continue using Firefox/Noscript but multitasking with it will create instability.

I have configured my phone's mail client and Facebook app so it will take care of those and I dont need to use Firefox and mplayer together.

---

### Post by linuxyogi on 2014-09-29
Finally I a found a way. Using Midori with  NoJS (NoScript alternative), 

Cookie Security Manager (Not sure if this can be compared with Ghostery),

Advertisement blocker (Uses the Adblock Plus blocklists)

Also, I learned that using a 64 bit distro with less than 4GB of ram 

will make the system run slow coz 64 bit uses more more memory 

on idle state. So installed 32 bit.

System is very responsive and stable now.

---

