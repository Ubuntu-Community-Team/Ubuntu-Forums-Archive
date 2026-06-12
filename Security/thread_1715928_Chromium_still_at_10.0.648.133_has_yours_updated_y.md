---
title: "Chromium still at 10.0.648.133? has yours updated yet?"
date: 2011-03-27
forum: Security
---

### Post by nrundy on 2011-03-27
There was a security update (to fix compromised HTTPS certificates) to Chromium on 17 March (10.0.648.151) but my Chromium still hasn't updated. 

Did Ubuntu drop the ball here or is this just affecting my box?

I'm considering switching to Google Chrome--to get security updates promptly.

---

### Post by Enigmapond on 2011-03-27
You can get daily builds by adding this repo:
[https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

I have been using it faithfully and have had no problems. The current version is 12.0.716.0.

---

### Post by nrundy on 2011-03-27
so you aren't running the stable version at all?

is anyone running the stable version? could you check what version you're at?

---

### Post by squenson on 2011-03-27
My version is: 10.0.648.133 (77742) Ubuntu 10.10

---

### Post by nrundy on 2011-03-27
uh. not good.

---

### Post by kherring7383 on 2011-03-27
Once you add the stable version ppa and run update manager you should now have several updates to apply. Chromium will update to version is 12.0.716.0

---

### Post by Enigmapond on 2011-03-27
The current stable version is 10.0.648.204 as per the repo. But the daily builds have been just great.

---

### Post by nrundy on 2011-03-27
> **kherring7383 said:**
> Once you add the stable version ppa and run update manager you should now have several updates to apply. Chromium will update to version is 12.0.716.0

what?

I just ran the update manager before posting. And I looked in Synaptic. Is says 133 is latest. and update manager says I'm fully up to date. hence my post: trying to figure out if something is wrong with my box. version 12 is not the stable version

---

### Post by Enigmapond on 2011-03-27
Here's the master PPA with all the versions...
[https://launchpad.net/chromium-project](https://launchpad.net/chromium-project)

I don't think you are using the proper repo for current versions. Update to the Stable Daily Builds...

---

### Post by Dark_Stang on 2011-03-27
The google hosted repository is here.
[http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) 

They have the stable, beta, and dev releases (10, 11, and 12 respectively) posted.

---

### Post by nrundy on 2011-03-27
no no, guys. I am talking about CHROMIUM. the ubuntu distribution of chromium is still stuck at 133. there is no "PPA" for chromium from ubuntu.

---

### Post by Enigmapond on 2011-03-27
> **nrundy said:**
> no no, guys. I am talking about CHROMIUM. the ubuntu distribution of chromium is still stuck at 133. there is no "PPA" for chromium from ubuntu.

Ok with all due respect, you need to get your facts straight. The PPA's I listed prior ARE from the team working on the Chromium Project FOR Ubuntu. My version, although bleeding edge, is 12.0.716.0 (79503) Ubuntu 10.04 and you can get the most stable version from the 2nd PPA listed on that page.

---

### Post by nrundy on 2011-03-27
I am speaking to the updates that come via the non-ppa for chromium. They come from Ubuntu as a result of Chromium being installed from Ubuntu Software Center--they are not Daily builds

---

### Post by Enigmapond on 2011-03-27
The ONLY way to get proper updates, and you would know this if you did just a little research, is to update the PPA. But, as you say there is none...I guess you are going to be stuck at that version for quite some time...
[http://www.liberiangeek.net/2010/05/how-to-install-chromium-google-chrome-in-ubuntu-10-04-lucid-lynx/](http://www.liberiangeek.net/2010/05/how-to-install-chromium-google-chrome-in-ubuntu-10-04-lucid-lynx/)

Good Luck.

---

### Post by nrundy on 2011-03-27
I've been getting updates  prior to 133 and I never installed the PPA. So that's what I was basing my posts on. I installed it from the Ubuntu Software Center by one click.

I'm trying to install the PPA now, but cannot get to the signed key page. Are you able to navigate to the key page?

[http://keyserver.ubuntu.com:11371/pks/lookup?search=0xFBEF0D696DE1C72BA5A835FE5A9BF3BB4E5E17B5&op=index](http://keyserver.ubuntu.com:11371/pks/lookup?search=0xFBEF0D696DE1C72BA5A835FE5A9BF3BB4E5E17B5&op=index)

---

### Post by nrundy on 2011-03-27
I thought installation of a PPA was not necessary to receive Security updates?

---

### Post by Enigmapond on 2011-03-28
It's just that the main repos are sometimes slow at getting the updates. Would you rather get milk from a market or straight from the cow?...:) Which would be fresher?...LOL

---

### Post by nrundy on 2011-03-28
> **Enigmapond said:**
> It's just that the main repos are sometimes slow at getting the updates. Would you rather get milk from a market or straight from the cow?...:) Which would be fresher?...LOL

hey thanks for all your posts Enigmapond. I really appreciate all your help in this matter :)

Assuming i understand correctly, the main repos work. But to insure I get timely updates, you guys recommend installing the Chromium PPA instead of using the main repo from Ubuntu. I follow correclty?

---

### Post by Enigmapond on 2011-03-28
That would be my recommendation. No problem with the help and hope it all works out for you.

Cheers!

---

### Post by nrundy on 2011-03-28
a major complaint I have with Chromium/Chrome is that sometimes I am unable to highlight text on webpages by dragging the mmouse. Do you ever have this problem?

I'm trying to figure out if it's a chrome bug or something specific to my box. I never have this problem in Firefox.

---

### Post by Enigmapond on 2011-03-28
No I have never encountered that problem.

---

