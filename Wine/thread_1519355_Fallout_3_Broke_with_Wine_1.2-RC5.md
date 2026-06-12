---
title: "Fallout 3 Broke with Wine 1.2-RC5"
date: 2010-06-28
forum: Wine
---

### Post by realdude19 on 2010-06-28
I just Want to know how the heck I can get this danged game to Run?!?! 

I had it working Fine then I inadvertently allowed and update to Wine and now its broken again... 

I had everything working... well at least to a playable point... now I cant even get the launcher to run without it crashing.

Any ideas? Btw Footstep sounds dont work or music, I heard there is a patch... but I cant get it to work. I have never applied a patch before.

Thanks in advance for any help.
Just let me know what info you need and it is yours. ty again

---

### Post by hikaricore on 2010-06-28
This isn't the wine forum..

Just downgrade back to the version you had before and it should work.

---

### Post by realdude19 on 2010-06-29
I realize that this isnt the wine forums. 
But I also know that this is is a great forum to find others using Ubuntu that will have a idea about programs as they partain to Ubuntu.

I guess i should have worded my question better...

How do I downgrade wine in ubuntu? i know how to use the repositories to install and uninstall programs but I also know that only the latest release is kept there. 

so how do i do this. and also if you DO know then maybe you would also know how to apply a patch to wine in Ubuntu. 

If not then that is ok. I will be posting this EXACT Thread in the wine forums. 

Thanks for your time and frustration with me. 

Oh and just for a laugh. I work at BestBuy in the Geek squad and I had the funniest run in today with a Blond gal.

She came in to complain about her laptop. 

"It Just stopped working. I cant get it to turn back on. I think I need a new Battery." she said.

I then replied to her, "ok Well lets take a look at it and see what the problem is."

She nodded her head.

"May I see your Power adapter?"

She replied "Whats that?" 

I then explained it to her. After I finished she suddenly turned bright red in the face, with Eyes wide open she grabbed her stuff and Left the store.

I had to go to the back room to let out a long and well deserved laugh!

---

### Post by dtfinch on 2010-06-29
Oblivion's affected too (by the sound issue), but no other games I'm aware of.

This is the bug report:
[http://bugs.winehq.org/show_bug.cgi?id=23249](http://bugs.winehq.org/show_bug.cgi?id=23249)

There is a patch mentioned in the bug report (21609) that preceded it, followed by many people claiming that the patch didn't work. I haven't bothered trying to apply it, because it looks like it's already in rc3 and later, and I'm on rc5 which isn't working. I only upgraded because the 1.1.42 in the repository had the same issue.

---

### Post by hikaricore on 2010-06-29
What I meant is that you posted in G&L.
Since that point your post has been moved.

I stopped reading shortly after the first line of your thread because I saw a squirrel.

---

### Post by realdude19 on 2010-07-01
> **hikaricore said:**
> What I meant is that you posted in G&L.
Since that point your post has been moved.

I stopped reading shortly after the first line of your thread because I saw a squirrel.

Fair enough. I know the feeling. And thanks for pointing me in the right direction.

Ok so I understand that there was a patch, but I had no idea it was incorporated in the RC3+ versions of wine. thanks for the info.

But why on earth would upgrading to RC5 break my game? I mean is there a way to install it that allows it to work that I don't know about?

I would roll it back to the last version (if I knew how) but that has me bewildered I have tried Googleing it but to no avail. 

I guess Fallout 3 and Oblivion are a lost cause in wine for me. to bad though, I love those games.

---

### Post by dtfinch on 2010-07-01
They did just commit a new fix that should be in rc6, mentioned in the bug report, which is now closed. Could wait for that to come out or try building it from the source.

---

### Post by realdude19 on 2010-07-01
Thanks dtfinch.

I downloaded the new Kernal and had to reinstall all my nvidia drivers so I wiped out all the nvidia drivers and reminants I had and installed nvidia-current.

so far all is working like a charm. I guess reseting my xorg.conf was all I needed. 

I am going to try Oblivion here in a few to see if its working. 
Sadly though the sound effects are all still broken, I hope the next wine release addresses that.

Thanks again.

---

### Post by dtfinch on 2010-07-01
The patch seems to work. I got impatient and built from the source, even though rc6 ought be out early next week (just a guess).

This ought to do it:
```
sudo apt-get build-dep wine
git clone git://source.winehq.org/git/wine.git ~/wine-git
cd ~/wine-git
./configure --prefix=/opt/winegit
make
sudo make install
```

You'd probably need to install build-essential too, unless build-dep does so automatically.

I had it install to /opt/winegit because I wanted to leave the repository version intact.

Then I made my oblivion launch script use "/opt/winegit/bin/wine" instead of just "wine". My first run crashed for some reason, while loading the saved game (never happened to me before on Wine), but the second try worked, and sound effects worked.

UPDATE: Wine 1.2rc6 has just been released today (Friday), a bit sooner than I expected. It's not in the ppa repository yet, but I expect it will be soon.

---

### Post by realdude19 on 2010-07-05
> **dtfinch said:**
> The patch seems to work. I got impatient and built from the source, even though rc6 ought be out early next week (just a guess).

This ought to do it:
```
sudo apt-get build-dep wine
git clone git://source.winehq.org/git/wine.git ~/wine-git
cd ~/wine-git
./configure --prefix=/opt/winegit
make
sudo make install
```

You'd probably need to install build-essential too, unless build-dep does so automatically.

I had it install to /opt/winegit because I wanted to leave the repository version intact.

Then I made my oblivion launch script use "/opt/winegit/bin/wine" instead of just "wine". My first run crashed for some reason, while loading the saved game (never happened to me before on Wine), but the second try worked, and sound effects worked.

UPDATE: Wine 1.2rc6 has just been released today (Friday), a bit sooner than I expected. It's not in the ppa repository yet, but I expect it will be soon.

Awesome News! Thanks Bud. So just to clarify you have all sounds in Oblivion and Fallout 3? (footsteps, Music, etc)

---

### Post by asdfoo on 2010-07-06
the make install step isn't necessary, you can run direct from the build directory if you don't want to interfere with packaged wine

---

### Post by dtfinch on 2010-07-06
1.2rc6 has been in the ppa repository for a few days.

[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

You can get it by adding "ppa:ubuntu-wine/ppa" to your Software Sources. I assumed you already added it since you had rc5.

I only have Oblivion and sound works now. I don't have Fallout to test, but they use the same engine and were the main two games on the bug report.

---

