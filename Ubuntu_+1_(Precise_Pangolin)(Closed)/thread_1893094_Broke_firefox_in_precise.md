---
title: "Broke firefox in precise"
date: 2011-12-09
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by leeper69 on 2011-12-09
Hi I am using ubuntu precise and have run into another problem firefox will open and run a google search but when loged on to any other web site if I try to open a link or do just about anything on the page firefox becomes unresponsive and the screen fades the only way to get firefox to respond is to try to shut it down witch will give me a popup menu with the choise force firefox to quit. this is happening in Gnome, KDE,and Ubuntu desktops. has anyone else had problems with firefox? This problem is not generating a bug report so I wll try removing firefox and reinstalling it.

---

### Post by Elfy on 2011-12-09
Thread moved to Ubuntu +1 (Precise Pangolin).

---

### Post by Harry33 on 2011-12-09
I have not experienced any kind of freezing with Precise Firefox.
The latest version is 9.0 beta5.
However, because I need to access my web bank, I use the release version 8.0.

Here:
[https://launchpad.net/ubuntu/+source/firefox/8.0+build1-0ubuntu1](https://launchpad.net/ubuntu/+source/firefox/8.0+build1-0ubuntu1)

Try that version. Just download the correct architecture and install it with dpkg:
sudo dpkg -i *.deb

---

### Post by irv on 2011-12-10
Firefox has slowed somewhat in precise, but when it turns gray, I get it a few seconds and it will respond. It crashed one time on me but I was opening multi-browsers windows to see if I could crash it.

One thing I notice the first time you open two browser windows and then close one, you can not open another one again. It just never opens. I am not sure if this is a bug. From that point on all you can have open is one browser window.

---

### Post by ventrical on 2011-12-10
I can confirm that FF is fubarred at current time just after yesterdays update. The major bug is that it will hardly scroll at all .. only in big, huge blocks... a real slowdown..

---

### Post by irv on 2011-12-10
Rebooted and try opening two browser windows and when I go to open the second one I get this message:

[ATTACH]208862[/ATTACH]

Maybe compiz has something to do with some of the problems.

---

### Post by MoreOrLess on 2011-12-10
For those having issues, what video card/driver are you using?

---

### Post by irv on 2011-12-10
> **MoreOrLess said:**
> For those having issues, what video card/driver are you using?

I am using Gallium 0.4 on ATI RS690 on a Dell Inspiron 1521 laptop.

---

### Post by sgage on 2011-12-10
> **irv said:**
> Rebooted and try opening two browser windows and when I go to open the second one I get this message:

[ATTACH]208862[/ATTACH]

Maybe compiz has something to do with some of the problems.

I believe FF has some issues with compiz - I couldn't rearrange tabs in compiz, but no problem in mutter or metacity.

Also had a glitch with Thunderbird - If I tried to drag a message to another folder, I had to drag it several folders above the one I wanted to highlight it for dropping. This too went away in mutter or metacity.

Nvidia 8500 GT with latest proprietary drivers.

---

### Post by Jay Car on 2011-12-10
After an update late last night Firefox crashed several times. Whenever that happens I always try disabling add-ons, one at a time, to see if any of them might be the problem (though I really don't have a lot of extensions installed). 

When I opened the add-ons tab the Flash-aid extension was grayed-out with a note that it was incompatible with FF 9, so I uninstalled, then reinstalled it and it seemed to accept it.  Then I disabled the "Ubuntu Firefox Modifications" extension (I usually do that anyway), and restarted FF.  It's been working great since then. 

The graphics card on this computer is an Nvidia GeForce GT 520. 

So far, so good. :)

---

### Post by irv on 2011-12-10
> **sgage said:**
> I believe FF has some issues with compiz - I couldn't rearrange tabs in compiz, but no problem in mutter or metacity.

Also had a glitch with Thunderbird - If I tried to drag a message to another folder, I had to drag it several folders above the one I wanted to highlight it for dropping. This too went away in mutter or metacity.

Nvidia 8500 GT with latest proprietary drivers.

This brings up another question. If I use the replace --metacity or --mutter will this disable Ubuntu Unity Plugin in compiz settings manager? I use this to size the icons in the dash. I was wondering if this would make my icons big again?

---

### Post by ventrical on 2011-12-10
> **Harry33 said:**
> I have not experienced any kind of freezing with Precise Firefox.
The latest version is 9.0 beta5.
However, because I need to access my web bank, I use the release version 8.0.

Here:
[https://launchpad.net/ubuntu/+source/firefox/8.0+build1-0ubuntu1](https://launchpad.net/ubuntu/+source/firefox/8.0+build1-0ubuntu1)

Try that version. Just download the correct architecture and install it with dpkg:
sudo dpkg -i *.deb


But your link points to the .tar.gz files.  No  *.deb there .

How do we get to the . deb file harry33?

---

### Post by sgage on 2011-12-10
> **irv said:**
> This brings up another question. If I use the replace --metacity or --mutter will this disable Ubuntu Unity Plugin in compiz settings manager? I use this to size the icons in the dash. I was wondering if this would make my icons big again?

Yes - Unity IS a compiz plugin. I usually use Gnome Classic (No Effects) which uses metacity, or Gnome Shell, which uses mutter.

Not sure about the icons...

---

### Post by ventrical on 2011-12-10
Ok.. I got it fixed, closed all tabs and marked in synaptic for re-installation !!

Perfect !

:)

thanks!

---

### Post by irv on 2011-12-10
I found that when I switch from Unity to Gnome3 the problem of opening more that one browser windows goes away. This would tell me that most likely the problem is with compiz seeing Gnome3 uses metacity.

---

### Post by Harry33 on 2011-12-10
> **ventrical said:**
> But your link points to the .tar.gz files.  No  *.deb there .

How do we get to the . deb file harry33?

First you have to choose the architecture, like AMD64 or i386.

---

### Post by ventrical on 2011-12-11
> **Harry33 said:**
> First you have to choose the architecture, like AMD64 or i386.


Yes, yes ... but then we come to a bunch of files  - so which one ???

---

### Post by Harry33 on 2011-12-11
> **ventrical said:**
> Yes, yes ... but then we come to a bunch of files  - so which one ???

Exactly the same firefox packages that you have installed from the beta version.
You may have all these three (atleast the first one is necessary).

[firefox_8.0+build1-0ubuntu1_i386.deb]("https://launchpad.net/ubuntu/+source/firefox/8.0+build1-0ubuntu1/+build/2907578/+files/firefox_8.0%2Bbuild1-0ubuntu1_i386.deb")

[firefox-branding_8.0+build1-0ubuntu1_i386.deb]("https://launchpad.net/ubuntu/+source/firefox/8.0+build1-0ubuntu1/+build/2907578/+files/firefox-branding_8.0%2Bbuild1-0ubuntu1_i386.deb")

[firefox-gnome-support_8.0+build1-0ubuntu1_i386.deb]("https://launchpad.net/ubuntu/+source/firefox/8.0+build1-0ubuntu1/+build/2907578/+files/firefox-gnome-support_8.0%2Bbuild1-0ubuntu1_i386.deb")

Check with Synaptic, which ones you have installed.

---

### Post by ventrical on 2011-12-11
> **Harry33 said:**
> Exactly the same firefox packages that you have installed from the beta version.
You may have all these three (atleast the first one is necessary).

[firefox_8.0+build1-0ubuntu1_i386.deb]("https://launchpad.net/ubuntu/+source/firefox/8.0+build1-0ubuntu1/+build/2907578/+files/firefox_8.0%2Bbuild1-0ubuntu1_i386.deb")

[firefox-branding_8.0+build1-0ubuntu1_i386.deb]("https://launchpad.net/ubuntu/+source/firefox/8.0+build1-0ubuntu1/+build/2907578/+files/firefox-branding_8.0%2Bbuild1-0ubuntu1_i386.deb")

[firefox-gnome-support_8.0+build1-0ubuntu1_i386.deb]("https://launchpad.net/ubuntu/+source/firefox/8.0+build1-0ubuntu1/+build/2907578/+files/firefox-gnome-support_8.0%2Bbuild1-0ubuntu1_i386.deb")

Check with Synaptic, which ones you have installed.


 I have the 9.0~b5 builds .. no ff 8.x

  Thanks for your reply.

 However , as I  rep[lied in an earlier post I had resolved the problem by closing all tabs and uninstalling/reinstalling ff.

 And also thanks for posting the links to  ff 8.0

---

### Post by leeper69 on 2011-12-21
Firefox seems to be working for me now after updating and upgrading. I am using Nvida 9500 with nvita latest driver.

---

### Post by ventrical on 2011-12-21
All is well here too.

---

