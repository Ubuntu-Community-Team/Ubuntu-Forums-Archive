---
title: "firefox in repos vs installing from mozillas website"
date: 2009-11-06
forum: The Cafe
---

### Post by mamamia88 on 2009-11-06
which do you think is better and why?  will i get better performance if i download and install directly from mozilla?

---

### Post by Firestem4 on 2009-11-06
The biggest difference I can see from the Repo's and the website itself is ease of installation and updates. The Repo versions are frozen until the next release comes along so if you want the newer Firefox's you have to get it directly from Mozilla or elsewhere (places like swiftweasel, iceweasel, swiftox, etc) or other Firefox remixes that are easy to use and offer different qualities. (EG: Iceweasel is completely free of licensed material; Swiftweasel follows in that nature but is also compiled for specific architectures so they will run more efficiently.)

---

### Post by wojox on 2009-11-06
I download Firefox from Mozilla. It screams in comparison to the repo's. Couldn't really tell you why. I just had to restart Firefox from an update. It's pretty cake to unpack and set up.

---

### Post by SunnyRabbiera on 2009-11-06
The easiest thing to do is to use a PPA, PPA will offer more up to date software but it wont rely on installing firefox manually.

---

### Post by Sealbhach on 2009-11-06
I use Swiftweasel: [http://swiftweasel.tuxfamily.org/about.php](http://swiftweasel.tuxfamily.org/about.php)

I find it pretty good, they're PGO builds so they're supposed to be better than ordinary Firefox.

.

---

### Post by FuturePilot on 2009-11-06
I just use the one in the repos. It integrates with the package manager and it has native 64bit builds.

---

### Post by mamamia88 on 2009-11-06
i'm going to give the mozilla version a chance to see if it's faster i can always go back to repo version right?

---

### Post by wojox on 2009-11-06
Sure just download it to your home directory, unpack it and run. If you don't like it just delete the folder.

---

### Post by mamamia88 on 2009-11-06
i used these directions seems faster so far might be in my head though [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by oldsoundguy on 2009-11-06
If you are using 9.10, FF will get updated as long as the build continues (but not UPGRADED) .. you will get all of the applicable security patches. (such as the one that came out yesterday). 

If you are running an older build or an UPGRADE comes out (4.0, for instance), an easy way to maintain upgrades is to use Ubuntuzilla (a python script available from the Ubuntuzilla site). That will take also care of the updates (patches).

---

### Post by mamamia88 on 2009-11-06
ok 64 bit flash isn't working in this version anyone have any help for me?

---

### Post by FuturePilot on 2009-11-06
> **mamamia88 said:**
> ok 64 bit flash isn't working in this version anyone have any help for me?

Because it's a 32bit version of Firefox. Mozilla doesn't provide 64bit builds. You could try running the 32bit version of Flash with it, though I don't know how that will work out. Never tried it.

---

### Post by mamamia88 on 2009-11-06
dang i'm just going back to repo version of firefox if i can't get flash working

---

### Post by Xbehave on 2009-11-06
> **FuturePilot said:**
> Because it's a 32bit version of Firefox. Mozilla doesn't provide 64bit builds. You could try running the 32bit version of Flash with it, though I don't know how that will work out. Never tried it.
You can find stable 64bit nightly builds at the [mozilla ftp]("ftp://ftp.mozilla.org/pub/firefox/nightly/latest-firefox-3.5.x/firefox-3.5.6pre.en-US.linux-x86_64.tar.bz2").

Note: Running it in your home is a bad idea from a security perspective as malware no longer needs to get root to get into your firefox, I put Firefox in /opt

---

### Post by FuturePilot on 2009-11-06
> **Xbehave said:**
> You can find stable 64bit nightly builds at the [mozilla ftp]("ftp://ftp.mozilla.org/pub/firefox/nightly/latest-firefox-3.5.x/firefox-3.5.6pre.en-US.linux-x86_64.tar.bz2").


:-s when did they start this? 

Perhaps the OP may want to try that.

---

### Post by mamamia88 on 2009-11-06
ok thanks i will try that now

---

### Post by Xbehave on 2009-11-06
> **FuturePilot said:**
> :-s when did they start this? 

Perhaps the OP may want to try that.
I used it for 3.0 so it's been around for a while. It is always a nightly, not too bad if you are trying out the betas but once a version is released i usually go with repo version just to avoid having to update it (especially as i need to kdesu it to update)

---

### Post by mamamia88 on 2009-11-06
my bad how exactly do i go about installing that version in /opt?

---

### Post by squilookle on 2009-11-06
I downloaded it from Mozilla and run it from my home directory. 

It works fine, and I like the fact that I can update to the latest version by clicking "Check for updates" from the Tools menu. 

I put a launcher in my Cairo dock and on my Openbox menu, and it fits in with my desktop perfectly well too :)

---

### Post by wojox on 2009-11-06
Unpack it:

```
tar xjf firefox-*.tar.bz2
```

Then:

```
sudo mv firefox /opt/
```

---

### Post by mamamia88 on 2009-11-06
ok i tried it runs fine but i have to run firefox script from terminal works alright but is there anyway i can get a regular 64 bit version and not a testing version but the current build?

---

### Post by Xbehave on 2009-11-06
> **mamamia88 said:**
> my bad how exactly do i go about installing that version in /opt?
as wojox said, plus I chown root.root the entire folder so i have to kdesu it to update (upto you if you do that).

there are 3 ways to "replace the usual firefox":

**the easy way:**
```
sudo ln -sfv /opt/firefox/firefox /usr/bin/ 
```
it shouldn't break anything but it can cause problems under weird circumstances.

**the GUI way:**
varies by desktop but just make new shortcuts to /opt/firefox/firefox that don't touch/care about the lower systems

**the path way:**
```
sudo mkdir /opt/bin
sudo ln -sv /opt/firefox/firefox /opt/bin
```
then change your $PATH to contain /opt/bin before /usr/bin by editing /etc/profile? (maybe its best to edit another file)

Personally i do it the easy way and have never had any problems.

---

### Post by wojox on 2009-11-06
Just make a icon in Applications > Internet

Open System > Preferences > Main Menu

Click Internet on left and +New Item

Name: Firefox

Command: /opt/firefox/firefox

Icon: /opt/firefox/icons

---

### Post by mamamia88 on 2009-11-06
> **wojox said:**
> Just make a icon in Applications > Internet

Open System > Preferences > Main Menu

Click Internet on left and +New Item

Name: Firefox

Command: /opt/firefox/firefox

Icon: /opt/firefox/icons

oh i know how to do that but is there a non daily version but the current version in 64 bit?

---

### Post by wojox on 2009-11-06
Talking to a buddy who said to install Firefox-3.5 from the repo's:

```
sudo apt-get install firefox-3.5
```

Then download 64 bit Flash:

```
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
```

Unpack it:

```
tar xvfz libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
```

Move it:

```
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/libflashplayer.so
```

---

### Post by gradinaruvasile on 2009-11-07
One difference between the repo version and the one from mozilla's site is that the repo version supports the font rendering settings from Gnome, the other one only the system wide font rendering (not that good).
Anyoune know if the version from the site will be upgraded runtime(to, say, 4.0) ?
I use Seamonkey 2.0 from mozilla's site (the same style generic Linux build as Firefox), its rock solid, better than Firefox in this regard (its also based on the firefox 3.5 engine and its updated along with it).

---

