---
title: "Possible to &quot;upgrade&quot; from Debian?"
date: 2006-03-27
forum: Server Platforms
---

### Post by chapterthree on 2006-03-27
Hey All,

I'm going to be buying a dedicated server soon for hosting, and I would prefer to use Ubuntu.  Unfortunately it looks like some of the companies I may go with do not offer Ubuntu.  (I have an email into sales to see if they will install Ubuntu for me, but for now I'm going to assume the answer is no.)

If they can't offer Ubuntu, is it possible to "upgrade" from Debian to Ubuntu?

---

### Post by o_fortuna on 2006-03-27
[QUOTE=chapterthree]Hey All,

I'm going to be buying a dedicated server soon for hosting, and I would prefer to use Ubuntu.  Unfortunately it looks like some of the companies I may go with do not offer Ubuntu.  (I have an email into sales to see if they will install Ubuntu for me, but for now I'm going to assume the answer is no.)

If they can't offer Ubuntu, is it possible to "upgrade" from Debian to Ubuntu?[/QUOTE]
Yeah, technically, although it might be difficult. All you have to do is edit the /etc/apt/sources.list file with this command (in the terminal):
```
sudo gedit /etc/apt/sources.list
```
And change to the Ubuntu repositories ([here]("http://www.ubuntuforums.org/showthread.php?t=92672") is a good example of an ubuntu-ified sources.list).

Then, to finally change to Ubuntu, put this in the command line:
```
sudo apt-get update
sudo apt-get dist-upgrade
```
NOTE: This will probably give you errors, although if you havn't installed a bunch of stuff on top of the default Debian it shouldn't be a disaster. This is something an experienced user should do since the probability of something going wrong is pretty high.

---

### Post by chapterthree on 2006-03-27
Come to think about it... I'm a tard :)  I have VMware, so I'm going to build a simple Debian image and try to upgrade it to Ubuntu and see how it goes :)

---

### Post by chapterthree on 2006-03-28
Well, that was... painless :o
The upgrade went very smoothly.  It is an ugly way to go though, and I'm skeptical on some things.  It feels like upgrading from Win98 to WinXP or something.  Sure, you're running XP now, but you know there is still some crap laying around from 98 :)

Anyway, just thought I'd share my experiences.  I think I'm gonna try to convince them to install Ubuntu for me, otherwise I'll just stick with the Debian base.

---

### Post by tbrownaw on 2006-03-28
One thing to be careful about is, a couple of times i've had updates temporarily leave networking broken. Not a serious problem for my laptop, but I'd imagine it would be for a machine buried in a datacenter somewhere. IIRC, this didn't happen when I upgraded Debian->Ubuntu, but later when I was poking at things to make them more like a standard Ubuntu (...actually, this might also have not been until I upgraded to Dapper, in which case it might have been more due to the experimentalness than the upgrading).

---

### Post by hagen00 on 2006-03-29
I'm all for Ubuntu...don't get me wrong, but if you have a server then Debian is a damn fine choice to begin with. Nothing wrong with Ubuntu as a server either (although I and many others will prefer Debian), but to risk "upgrading" a Debian installation to Ubuntu for a server seems very strange.

---

### Post by Lord Illidan on 2006-03-29
I agree with Hagen00. Why upgrade to Ubuntu? Is Debian bothering you in some way?

---

### Post by chapterthree on 2006-03-29
My main reasoning for looking into this was the out-dated packages that are contained within the Debian repos.

After my little test run here, I do not plan to try to upgrade to Ubuntu from Debian.  It was just too mess, and after some thought it is just not necessary.  I think I'll just use backports.org if I need some updated package that is not available in the Debian repos.

---

### Post by hagen00 on 2006-03-30
What Debian are you using? I agree that Stable (Sarge) is fairly "out of date". But i hear that Testing is much more up to date and is still extremely stable! And Debian Unstable pretty much has any package you will require, even some of the bleeding edge ones. While i don't recommend you use Debian Unstable as a server, it is possible to mix your sources. I.e. run Debian Stable but then get a few packages from Testing or Unstable. 

There are quite a few tutorials on that if you Google a bit. I did play with that once (having sources from stable and testing) and i must admit it didn't quite work for me. But it's definitely possible.

---

