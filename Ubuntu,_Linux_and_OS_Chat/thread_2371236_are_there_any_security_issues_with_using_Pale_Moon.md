---
title: "are there any security issues with using Pale Moon on Xubuntu?"
date: 2017-09-12
forum: Ubuntu, Linux and OS Chat
---

### Post by ardouronerous on 2017-09-12
I took a bold step and installed Pale Moon.
This is my first time installing a Internet browser that's not part of Ubuntu's repos, so you can understand my apprehension.

I've installed Pale Moon like this:

```
sudo sh -c "echo 'deb http://download.opensuse.org/repositories/home:/stevenpusser/xUbuntu_16.04/ /' > /etc/apt/sources.list.d/palemoon.list"
wget -nv http://download.opensuse.org/repositories/home:stevenpusser/xUbuntu_16.04/Release.key -O Release.key
sudo apt-key add - < Release.key
sudo apt-get update
sudo apt-get install palemoon
```
Source: [https://software.opensuse.org/download.html?project=home:stevenpusser&package=palemoon](https://software.opensuse.org/download.html?project=home:stevenpusser&package=palemoon)

I've been using Pale Moon for a couple of hours now and I've very impressed, and these are the things that impressed me:

1) it's faster and more responsive than Firefox and Chromium
2) the memory usage is lower than the aforementioned browsers
3) all my bookmarks are available in the address bar, while in the aforementioned browsers, not all my bookmarks are listed, I have to manually search for the bookmarks.
4) the addons that I used in Firefox are also available in Pale Moon's addon site.

Now, because this browser isn't part of Ubuntu's repos, are there any security issues with using Pale Moon on Xubuntu?

---

### Post by vasa1 on 2017-09-12
> **ardouronerous said:**
> ...
Now, because this browser isn't part of Ubuntu's repos, are there any security issues with using Pale Moon on Xubuntu?How can anyone here give you an assurance that there are no security "issues" with Pale Moon or anything else for that matter?

If your asking for opinions, I'd stay away from browsers made by small teams.

---

### Post by ardouronerous on 2017-09-12
I'm looking for experiences from people who had or are using Pale Moon, but it is not my main browser though.

My main browser is Chromium because Firefox's memory usage is atrocious.

---

### Post by wildmanne39 on 2017-09-12
Do they have regular updates that you can receive like firefox does?

---

### Post by ardouronerous on 2017-09-12
[FONT=sans-serif][COLOR=#000000]I cannot really answer that because this is my first time installing Pale Moon, so I have no experience in their update cycle.

But what I can tell you is that the version that is installed on my system now is [/COLOR][/FONT][COLOR=#000000][FONT=sans-serif]27.4.2, and it was released on [/FONT][/COLOR][COLOR=#000000][FONT=sans-serif]August 22, 2017, so I'm using the latest version.[/FONT][/COLOR]

---

### Post by vasa1 on 2017-09-12
Moved here because it's a better fit here: Pale Moon isn't a browser provided by the repos.

---

### Post by missmoondog on 2017-09-12
they have very regular updates which usually get uploaded to the repository very shortly after firefox does, provided it's worth an update, and yes, you get those updates through synaptic or the software updater just like normal. palemoon is the same thing as firefox just with some of the crap code removed.

been using palemoon as my main browser for a long time (years) on both windows and linux simply because it blows any other browser away and the  extensions i use work in it.

heck, even use a version of it on a couple real old machines, that i let some of the in laws kids use, that don't support sse2!!

---

### Post by ardouronerous on 2017-09-12
So Pale Moon gets updated regularly? Thank for the clarification.

I'm having a blast with Pale Moon, It's blazing fast and the memory is much better than Firefox.

Right now, I have 4 tabs loaded with Ubuntu Forums, Youtube playing a video, Wikipedia and Devinantart and according to Task Manager, Pale Moon goes up to 400+MiB RSS, while Firefox with the same tabs running goes up to 700+MiB RSS.

I have no idea why Firefox is such a memory hog, and I'll come back to it when it reaches version 57 and see if there are improvements to memory.

I have no idea why Pale Moon isn't part of Ubuntu repos, but it should be.

---

### Post by bluemagoo on 2017-09-12
> **vasa1 said:**
> How can anyone here give you an assurance that there are no security "issues" with Pale Moon or anything else for that matter?

If your asking for opinions, I'd stay away from browsers made by small teams.

+1

---

### Post by missmoondog on 2017-09-13
it gets updated regularly provided you have added the repository and the key, which it looks like you have done. firefox has ALWAYS been a memory hog and probably always will be. 

i totally agree that it should be part of ubuntu also :)

---

### Post by ardouronerous on 2017-09-13
actually the first time I tried to install Pale Moon, I didn't add the key at first, so I got a validation error, so I aborted the install and added the key and the installation went smoothly.

I also noticed Pale Moon handles watching Youtube videos in 720p HD very well when compared to Firefox, in Firefox, watching Youtube in HD causes the video to freeze while the audio continues, forcing me to select 480p.

---

### Post by yoshii on 2017-09-16
I have had a lot of success with PaleMoon and PaleMoon portable on Windows, yet on Linux last year my PaleMoon Linux install got corrupted while netinstalling and I had some wierd OS issues after that.  So I quit using it at all.  However, TahrPup v6 comes with it, and I tried it long enough to install FireFox and it was OK for that time.  At least it can install alot of the best Mozilla addons.  But I will stick with FireFox and maybe every so often try QupZilla for fun.

---

### Post by ChuangTzu on 2017-09-17
be wary of using a web browser with a small team and not included by many distros.  Seamonkey is an exception as its been around for a very long time and it is used by a few distros.

---

### Post by vasa1 on 2017-09-18
Re. Seamonkey, [The State of the SeaMonkey Union!]("https://blog.seamonkey-project.org/2017/05/02/the-state-of-the-seamonkey-union/")

---

