---
title: "&quot;Randr extension not present&quot; not solvable with xinerama?"
date: 2009-05-13
forum: System76 Support
---

### Post by jbraswell on 2009-05-13
Ever since I upgraded to Jaunty, I've had problems with various GUIs.  For example, whenever I try to open the display preference GUI, I get the above message about Randr; file-save dialog boxes take ~10 seconds to open; my Sony mp3 player no longer gets recognized when I plug it in; etc; etc.

Every forum post I can find tells me to disable Xinerama, which indeed solves the issue, but I just can't bring myself to accept that as the only solution.  I need to drag things between my monitors, dangit.  (The only reason I upgraded to Jaunty, in fact, was to get rid of the infamous dual monitor "artifact" that infested various parts of the screen with ATI cards.)  

So, any other solution to this?  I'm using fglrx with a Raedon HD 4800 card.  

Thanks for any help.

---

### Post by thomasaaron on 2009-05-13
Did you try from a Jaunty live CD just to make sure it isn't something that got hosed in the upgrade?

---

### Post by jbraswell on 2009-05-14
That's how I did it originally, yes.  

Is there some way to check for installation errors that would cause this?

---

### Post by thomasaaron on 2009-05-14
I'm not getting that error on our shop Wild Dog, which has a fresh Jaunty image.

Did you do a fresh install of Jaunty or upgrade via Update Manager?

---

### Post by jbraswell on 2009-05-15
I did upgrade via the update manager.  So I should download and burn a CD and reinstall?

---

### Post by thomasaaron on 2009-05-15
I would.

Other things I can think of, if you want to give them a shot, would be re-installing xserver-xorg, libxrandr2 (the randr extension library), and maybe x11-xserver-utils.

sudo apt-get --reinstall install xserver-xorg libxrandr2 x11-xserver-utils

---

### Post by jbraswell on 2009-05-15
Well, the x reinstall didn't seem to work, so I'll try a reinstall.

---

### Post by metasparks on 2009-05-24
Did you ever figure out how to resolve this?

---

### Post by jbraswell on 2009-05-24
Not yet.  I just found time today to attempt a reinstall, but when I ran a check on the install CD I burnt, it found an error. (I sure wish the install CD checker told you which file it found an error with.)  So, I guess I have to try again.  

*sigh*

---

### Post by jbraswell on 2009-05-26
Ugh.  So, I did a complete re-install yesterday, according to these directions: [URL="http://hehe2.net/linuxhowto/howto-fresh-ubuntu-install-without-losing-your-current-settings/"]. 

Everything looked OK at first, so once I copied the contents of my old home directory into the new one, I restarted my machine.  (fglrx drivers were not activated.) 

However, since I restarted, I can no longer see anything on my screen...just one giant "artifact."  I don't really have a clue what to do now.  Any ideas?

Thanks

---

### Post by jdb on 2009-05-26
> **jbraswell said:**
> Ugh.  So, I did a complete re-install yesterday, according to these directions: [URL="http://hehe2.net/linuxhowto/howto-fresh-ubuntu-install-without-losing-your-current-settings/"]. 

Everything looked OK at first, so once I copied the contents of my old home directory into the new one, I restarted my machine.  (fglrx drivers were not activated.) 

However, since I restarted, I can no longer see anything on my screen...just one giant "artifact."  I don't really have a clue what to do now.  Any ideas?

Thanks

The hidden files & folders (start with a dot) contain the configurations for all your installed applications.
For most of the applications you reinstalled you're better off with the fresh settings that come with a new install.

If you decide to re-install again you might try only copying the non-hidden folders from your old home directory.
If there is some application you really fine tuned that you don't want to re-configure, just copy the hidden folder or file for that application.

jdb

---

### Post by jbraswell on 2009-05-26
That doesn't seem like it could be the culprit with the current problem, though, right?  This seems like it has to be some video card/driver issue, although I don't know how.  

Man, I have to say that I'm pretty disappointed so far with Ubuntu and its ease-of-use claims.  I realize (and welcome) that there's a DIY element to Linux, but since buying this machine, I haven't once had a single configuration where things worked right.  

I'll try to post my xorg.conf later.

---

### Post by jbraswell on 2009-05-27
> **jbraswell said:**
> That doesn't seem like it could be the culprit with the current problem, though, right?  This seems like it has to be some video card/driver issue, although I don't know how.  

Man, I have to say that I'm pretty disappointed so far with Ubuntu and its ease-of-use claims.  I realize (and welcome) that there's a DIY element to Linux, but since buying this machine, I haven't once had a single configuration where things worked right.  

I'll try to post my xorg.conf later.

Since this problem doesn't really match the thread title, I made a new one here: [http://ubuntuforums.org/showthread.php?p=7352943#post7352943]("http://ubuntuforums.org/showthread.php?p=7352943#post7352943")

---

### Post by jbraswell on 2009-05-27
Sorry, I decided to kill that thread.  I re-installed again, and decided not to copy over the home directory, *or* restore my old packages.  I just wanted to start again from scratch.

---

### Post by jbraswell on 2009-05-28
Finally got things back up and running on the second re-install. 

I want to activate fglrx, but I'm nervous.  I don't care about 3D acceleration at all, but I do want the Xinerama effect where windows maximize in their own screen...is this possible with the free drivers?

---

### Post by thomasaaron on 2009-05-28
I've not been able to accomplish it with free drivers.

---

### Post by jbraswell on 2009-05-28
Hmm, that sucks.  

Out of curiosity, is there a reason System76 doesn't use Nvidia cards?  I only ask because the weight of opinions on these forums seems to be that they're a "happier" choice?  However, I don't want to go out and buy one if my impression is incorrect.

---

### Post by thomasaaron on 2009-05-28
nVidia cards are great, and we've used them in the past. We've received a lot of requests for them, though, and I'm sure we'll sell them again in the future.

Dollar for dollar, though, our testing indicates ATI cards provide higher performance than nVidia cards. Also, ATI catalyst is far superior to nvidia-settings.

For what it's worth, that's why we made the switch.

---

### Post by jbraswell on 2009-05-28
Gotcha.  

I'll give fglrx another try then.  You guys don't happen to have a dual monitor, wild dog xorg.conf available, do you?

---

### Post by thomasaaron on 2009-05-29
I could make one, but it would not match your monitors. But I suppose you could use it as a template.

ATI Catylist will make one for you when you configure your dual monitors. There's no manual tweaking of the config file involved.

---

