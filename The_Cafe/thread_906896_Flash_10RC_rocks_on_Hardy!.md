---
title: "Flash 10RC rocks on Hardy!"
date: 2008-08-31
forum: The Cafe
---

### Post by kansasnoob on 2008-08-31
I couldn't really figure out where to post this so hopefully one of the forum staff members will pick up on this, but I just installed Flash 10 Release Candidate and after a punishing test drive it seems to work quite well.

I used the deb file from here:

[http://tombuntu.com/index.php/2008/08/28/test-drive-adobe-flash-player-10-rc-in-ubuntu/](http://tombuntu.com/index.php/2008/08/28/test-drive-adobe-flash-player-10-rc-in-ubuntu/)

I should note that I began by removing the flash 10 beta using the following command in terminal:

```
cd ~/.mozilla
rm flashplayer.xpt libflashplayer.so
```

Of course if you are using Flash 9 which is Hardy's default you would remove it using synaptic or just go to terminal and:

```
sudo apt-get remove --purge flashplugin-nonfree
```

Note: if you're unsure which version of Flash you have installed you can either click on Tools > Add-Ons at the top of Firefox or type ABOUT:PLUGINS in the URL box.

I should also note that I'd previously removed libflashsupport and nspluginwrapper which had been part of an earlier work-around for Firefox crashes related to Flash and Pulseaudio along with following this tutorial in its entirety:

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

Finally I'd note that if everything is already working well leave it be! I mess around all the time, but I like messing around and I don't get frustrated if I break my stuff - I just keep notes and start over again, and again, and again!

---

### Post by Vadi on 2008-09-02
Glad to hear!

---

### Post by HittingSmoke on 2008-09-02
Heh, I wish this was here when I tried to upgrade a week ago. I had a hell of a time tracking down the right info.

So far the only problem I've had is a hand full of sites that dont recognize Flash as being installed after I upgraded. The only one that's bugging me is Myspace Video.

Also it seems to be crashing on different (however, less) sites than Flash 9 did for me.

Over all it was worth it for the sites I use. Smoother video and working full screen mode.

---

### Post by empty_spaces on 2008-09-02
Upgraded 2 hours ago to Flash 10RC from Flash 10 beta. Tested some of the usual sites that cause FF to crash, no crashes so far. I've got my fingers crossed.

---

### Post by kansasnoob on 2008-09-02
I should rewrite that though. It's bass-ackwards. You should start with:

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

And if flash is still giving you problems remove all possible previous flash plugins:

```
cd ~/.mozilla
rm flashplayer.xpt libflashplayer.so
```

```
sudo apt-get remove --purge flashplugin-nonfree
```

Then go to:

[http://tombuntu.com/index.php/2008/08/28/test-drive-adobe-flash-player-10-rc-in-ubuntu/](http://tombuntu.com/index.php/2008/08/28/test-drive-adobe-flash-player-10-rc-in-ubuntu/)

Or, since I noticed some confusion with finding the .deb just go here for Flash 10 RC:

[http://launchpadlibrarian.net/16766494/flashplugin-nonfree_10.0.1.218%2B10.0.0.569ubuntu1%7Eppa2_i386.deb](http://launchpadlibrarian.net/16766494/flashplugin-nonfree_10.0.1.218%2B10.0.0.569ubuntu1%7Eppa2_i386.deb)

That should just install like you're falling down and can't stop!

I did have a problem once where gnash had not yet been removed, but it's a darn solid flash! No crashes!

---

### Post by coolbrook on 2008-09-02
Can you scroll [www.tsn.ca](www.tsn.ca) without FF crashing?  EASports crashes too.  There's a fair bit of flickering on mlb.com and ESPN isn't detecting it.  I'm looking forward to the final release.

---

### Post by tuxxy on 2008-09-02
> **coolbrook said:**
> Can you scroll [www.tsn.ca](www.tsn.ca) without FF crashing?  EASports crashes too.  There's a fair bit of flickering on mlb.com and ESPN isn't detecting it.  I'm looking forward to the final release.

Funy how I can run all those sites fine and yes scroll tsn.ca perfectly and im on Flash 9 with 64bit :)

dont think I wanna update either by the sounds of this lol

---

### Post by kansasnoob on 2008-09-02
> **tuxxy said:**
> Funy how I can run all those sites fine and yes scroll tsn.ca perfectly and im on Flash 9 with 64bit :)

dont think I wanna update either by the sounds of this lol


The last line of my op says, "Finally I'd note that if everything is already working well leave it be! I mess around all the time,"

And my .deb links for Flash 10 RC are i386 only! Otherwise you'd need nspluginwrapper.

---

### Post by kansasnoob on 2008-09-02
> **coolbrook said:**
> Can you scroll [www.tsn.ca](www.tsn.ca) without FF crashing?  EASports crashes too.  There's a fair bit of flickering on mlb.com and ESPN isn't detecting it.  I'm looking forward to the final release.

Yes!

But as I said, I wrote that somewhat backwards. start with:

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

Then work thru the rest if necessary.

---

### Post by Jompa on 2008-09-06
It works better now, but still some crashes now and then.

---

### Post by dysonsphere23 on 2008-09-06
I did everything from the Pulse Audio-Flash Fix post and could not get videos from Google Video to play.  They all say "video not available".  They worked when I had Flash 9 installed, although I was experiencing quite a few random crashes on all Flash sites.

So I tried the fix from this thread and get this:

dysonsphere@Sirius:~$ cd ~/.mozilla
[email]dysonsphere@Sirius:~/.mozi[/email]lla$ rm flashplayer.xpt libflashplayer.so
rm: cannot remove `flashplayer.xpt': No such file or directory
rm: cannot remove `libflashplayer.so': No such file or directory

if they are not there then where are they?

and why might they install to a different place for me?

Thanks for all your work, much appreciated.

---

### Post by mike1234 on 2008-09-06
> **coolbrook said:**
> Can you scroll [www.tsn.ca]("http://www.tsn.ca") without FF crashing?  EASports crashes too.  There's a fair bit of flickering on mlb.com and ESPN isn't detecting it.  I'm looking forward to the final release.

 Scrolls fine for me and I have non-free version that comes with Ubu 8.04.

M.

---

### Post by wariskampar on 2008-09-06
Under FF3>Addon>Plugin, I found 2 Shockwave Flash plugins, 10 and 9 respectively. can I remove 9 safely. So far, I have yet to experience crash (please define crash).
ps: since I repaired my PulseAudio, my system hardly crash:) Yay!!

---

### Post by roadrun777 on 2008-09-06
I don't know why all that is necessary in those other links.
Seems like a lot of work. I personally don't like having my browser embedded into the operating system. 

I usually uninstall everything I can find having to do with flash or browser support using synaptic (or apt if I am already in a console).
Then I log into ftp.mozilla.org and find the latest nightly firefox for linux and download the tarball for my cpu architecture to a folder in my home dir.
I then unpack it to its own folder (for ex. firefox3), then I delete mozilla-xremote-client.
Then you rename your .mozilla folder to .mozilla-bak, and run create a desktop launcher pointing to firefox and run it.
It should make a new .mozilla with a new profile.
You then download the latest flash10 RC from adobes site, grab the tar file.
Unpack it and open a console (non-root) and run the install script.
./flashplayer-installer

Then it installs it into your new profile and your good to go. You get 
the latest security fixes with the latest flash10 and it runs great.

You should note that if you forgot to rename the .mozilla folder, it will probably crash. As the newer nightly builds of firefox change the profile structure, so you really need a fresh profile if you use the latest firefox.

As far as the sound issue goes, I always assumed ad*be flash just used the default system sound settings? I have only had sound issues on a few of the beta test builds of ubuntu.

So what is the advantage to integrating firefox with the OS so heavily?

---

### Post by zmjjmz on 2008-09-07
Yeah, I have yet for Flash 10 to crash on me.

---

### Post by doorknob60 on 2008-09-07
Flash 10 hasn't crashed on me either, but then again Flash 9 never crashed on me in Debian, not even once, it's just that flash 10 works better with full screen and stuff. And now I use Kubuntu intrepid so flash 10 is already in the ropos :D Anyways, I just need Flash not to cover those menus -.- That's real annoying...

---

### Post by mrgnash on 2008-09-07
Sounds good... but until they come out with a 64bit version, I'll be sticking with swfdec (and maybe even then...)

---

