---
title: "Firefox 2 or 3"
date: 2008-07-04
forum: The Cafe
---

### Post by dodle on 2008-07-04
As of right now I am still stuck on Firefox 2 because most of the extensions and themes that I like do not work with 3.  When more addons get upgraded I'll switch to Firefox 3.

---

### Post by mrgnash on 2008-07-04
Alright...

---

### Post by ukripper on 2008-07-04
Firefox 3 is much better in memory usage and most addons and plugins work fine except themes (I ain't that bother) that is all I care about.

in return i get better performance and memory management which is what i want.

---

### Post by Ozor Mox on 2008-07-04
I like Firefox 3 and have very few problems with it aside the occasional Flash-related crash. But then, I don't use many extensions at the moment...

---

### Post by ukripper on 2008-07-04
Just to emphasise - Update your Firefox 2.0(if you are running) through update manager or apt as there is a critical vulnerability updates available for 7.10,7.04 and 6.06

[http://ubuntuforums.org/showthread.php?t=847368](http://ubuntuforums.org/showthread.php?t=847368)

[http://www.ubuntu.com/usn/usn-619-1](http://www.ubuntu.com/usn/usn-619-1)

---

### Post by dodle on 2008-07-04
Wow, I'm surprised at the results.  I thought more people would like ff2 better.  

Some of the addons that I would like to use but can't with ff3 are [OpenDownload]("https://addons.mozilla.org/en-US/firefox/addon/207"), [Vista-aero]("https://addons.mozilla.org/en-US/firefox/addon/4988"), and I wish that [FoxFilter]("https://addons.mozilla.org/en-US/firefox/addon/207") was available for linux.

---

### Post by Kevbert on 2008-07-04
Firefox 3 isn't really an option for me at the moment as I was having hard lockups when viewing video (Mr Reset Button was getting worn out).  I'm using Firefox 2.0.0.15.

---

### Post by cardinals_fan on 2008-07-04
Opera

---

### Post by gn2 on 2008-07-04
Since RC1 I prefer FF3, all the add-ons I need now work with FF3.

Pleasantly surprised how good it is since RC1, I did not like FF3 when it was a Beta release and even wrote a how-to to revert back to FF2.

---

### Post by Kingsley on 2008-07-04
Firefox 3 walks all over Firefox 2 and other web browsers.

Here's a good fix to make more of your older favorite extensions work in FF3:
[http://lifehacker.com/355973/make-your-extensions-work-with-the-firefox-3-beta](http://lifehacker.com/355973/make-your-extensions-work-with-the-firefox-3-beta)

---

### Post by gameryoshi600 on 2008-07-04
I use it cause I think firefox 3 is not in the repos for pclinuxos 2007.

---

### Post by ukripper on 2008-07-04
> **gameryoshi600 said:**
> I use it cause I think firefox 3 is not in the repos for pclinuxos 2007.

You can use this method to install on PClinux as FIREFOX3 is not in gutsy either and i have installed using the method in link
[http://ubuntuforums.org/showthread.php?t=833036](http://ubuntuforums.org/showthread.php?t=833036)

All you need to do is to cut and paste these commands in your terminal:

First, back up your bookmarks and settings:

cp -R ~/.mozilla ~/.mozilla.backup


Download Firefox from the [WWW] Firefox website, and change to the directory you downloaded it to.

(e.g., download it to desktop, the open a terminal and type:

cd /[your home directory name]/Desktop)


Install it to /opt/firefox (make sure the /opt directory exists first):

sudo tar -jxvf firefox-3.0.tar.bz2 -C /opt
rm firefox-3.0.tar.bz2

*

Link to your plugins and remove totem-mozilla as it doesn't seem to work with Firefox 1.5.x or 2.x:

sudo mv /opt/firefox/plugins /opt/firefox/plugins.bak
sudo ln -s /usr/lib/firefox/plugins /opt/firefox/plugins
sudo rm /usr/lib/firefox/plugins/libtotem_mozilla.*

*

To ensure it is used as the default version, modify the symbolic link in /usr/bin:

sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox

The dpkg-divert command will move the original system-wide /usr/bin/firefox to a new name. The ln command will place a symlink to the newly installed Firefox in /usr/bin.
*

Try it out:

firefox &

*

Running Firefox in terminal may cause errors to show but don't worry about that, it will still work once Firefox is restarted. The reason for these errors is because Firefox 3 is checking for updates, which is not abnormal activity. Also, running this command make take a some time to execute. Please be patient.
*

If you want to keep the original Ubuntu icon for Firefox, enter this command:

sudo cp /usr/share/pixmaps/firefox.xpm /opt/firefox/chrome/icons/default/default.xpm

Some users may find the icon with a different extension, they should use this command:

*

sudo cp /usr/share/pixmaps/firefox.png /opt/firefox/chrome/icons/default/default.xpm

---

### Post by dodle on 2008-07-04
> **Kingsley said:**
> Firefox 3 walks all over Firefox 2 and other web browsers.

Here's a good fix to make more of your older favorite extensions work in FF3:
[http://lifehacker.com/355973/make-your-extensions-work-with-the-firefox-3-beta](http://lifehacker.com/355973/make-your-extensions-work-with-the-firefox-3-beta)
Thanks for the link Kingsley.  That worked, but the themes looked kinda funky.  I did some more searching around and found this:

[http://daniel1992.wordpress.com/2008/02/03/how-to-install-incompatible-addons-in-firefox-3/]("http://daniel1992.wordpress.com/2008/02/03/how-to-install-incompatible-addons-in-firefox-3/")

I think I like this method better, as far as extensions go.  But it looks like I'll just have to wait for themes to be updated.

---

### Post by kenono on 2008-07-04
It's FF3 for me, I really like the integrating desktop themes as well as the "Awesome Bar".

I feel it's must faster too. A quality improvement on what was already a quality piece of software.

---

### Post by BuffaloX on 2008-07-04
FF3 is supposedly better, I don't know never had problems with either FF2, or FF3.

---

### Post by lukjad on 2008-07-04
I'm using Firefox 3 but think Firefox 2 was a bit better, at least in the fact that it didn't crash so much. Does that make me for Firefox 2 since I haven't tried it in this release so cannot be sure it is better or worse? I don't know.

---

### Post by nkri on 2008-07-04
I love Firefox 3 because it looks better (the Ubuntu version, NOT windows or mac), is easier to customize, has better features, and is faster, but I definitely agree about the add-ons: that is the biggest problem, and one of the most important to some people, that FF3 has, in my opinion.  I've never had a crash, error, or failiure of any kind in 2 or 3 (except for bugs in Piclens in Windows, which they fixed), as opposed to plenty in IE7.

---

### Post by samjh on 2008-07-04
FF3: better integration with desktop environment, better features, faster performance.

---

### Post by BWF89 on 2008-07-04
The 'awesome bar' is a really good idea. Now if I'm looking for something it's a lot faster to search through my bookmarks. I don't use tags though.

It's kinda nice that the interface integrates better to the OSX environment.

---

### Post by Polygon on 2008-07-04
why is this even a poll? firefox 3 stomps all over firefox 2 in every aspect

---

### Post by danbuter on 2008-07-04
Firefox 3, because I only use one or two extensions.

---

### Post by Mr. Picklesworth on 2008-07-04
I have to admit, Firefox 3 converted me from Epiphany. That is quite a feat.
Granted, I'm still going back when WebKit gets into Epiphany in full; the reason I switched was because it kept hanging on me with XULRunner. (I still prefer having proper GTK widgets that scale correctly when I resize the various dialogs).

Firefox 3, however, is one amazing browser. I miss the Awesome Bar now every time I must use another browser.

---

### Post by K.Mandla on 2008-07-04
Firefox 3, which is working fine for me -- Flash too -- in Crux.

---

### Post by dodle on 2008-07-24
I was really starting to like Firefox 3 because a lot of the extensions and themes have been update.  But now I am having a really annoying right-click issue with it.

---

