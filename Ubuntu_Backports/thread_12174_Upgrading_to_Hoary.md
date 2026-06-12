---
title: "Upgrading to Hoary"
date: 2005-01-22
forum: Ubuntu Backports
---

### Post by jdong on 2005-01-22
If you directly upgrade from Warty+Backports to Hoary, you may run into trouble on the way.

If you'd like to upgrade to Hoary, following the following instructions:


1. Run the given command:
```

apt-show-versions -b | grep warty-backports | cut -d ' ' -f 1 | awk -F/ '{print $1;}' |grep -v grepmap | grep -v wine | xargs --replace="{}" apt-get install {}/warty -s

```
Examine the output of what's being done. It should simulate the downgrade of all installed backports (staging and stable) to Warty packages.

2. Run
```

apt-show-versions -b | grep warty-backports | cut -d ' ' -f 1 | awk -F/ '{print $1;}' |grep -v grepmap | grep -v wine | xargs --replace="{}" apt-get install {}/warty -y --force-yes

```
This will actually do the downgrade, instead of just simulating.

3. Run
```
apt-show-versions -i; apt-show-versions -b | grep warty-backports
```
This will show you exactly what backports are left after that ordeal. Deal with them by hand...

4. Remove backports from your /etc/apt/sources.list, or disable Backports from Synaptic. Follow the installation directions in reverse, basically.

5. Run an **apt-get update**

6. Change from Warty sources to Hoary ones in /etc/apt/sources.list.

7. Run apt-get update

8. Run **apt-get dist-upgrade**

9. Add Hoary Backports sources.

---

### Post by poofyhairguy on 2005-01-22
[QUOTE=jdong]If you directly upgrade from Warty+Backports to Hoary, you may run into trouble on the way.

If you'd like to upgrade to Hoary, following the following instructions:


1. Run the given command:
```

apt-show-versions -b | grep warty-backports | cut -d ' ' -f 1 | awk -F/ '{print $1;}' |grep -v grepmap | grep -v wine | xargs --replace="{}" apt-get install {}/warty -s

```
Examine the output of what's being done. It should simulate the downgrade of all installed backports (staging and stable) to Warty packages.

2. Run
```

apt-show-versions -b | grep warty-backports | cut -d ' ' -f 1 | awk -F/ '{print $1;}' |grep -v grepmap | grep -v wine | xargs --replace="{}" apt-get install {}/warty -y --force-yes

```
This will actually do the downgrade, instead of just simulating.

3. Run
```
apt-show-versions -i; apt-show-versions -b | grep warty-backports
```
This will show you exactly what backports are left after that ordeal. Deal with them by hand...

4. Remove backports from your /etc/apt/sources.list, or disable Backports from Synaptic. Follow the installation directions in reverse, basically.

5. Run an **apt-get update**

6. Change from Warty sources to Hoary ones in /etc/apt/sources.list.

7. Run apt-get update

8. Run **apt-get dist-upgrade**

9. Add Hoary Backports sources.[/QUOTE]


When Hoary comes around, will you do something differently to make upgrades go smoother?

I'll look for ideas through Google.

---

### Post by YokoZar on 2005-01-22
You could create a metapackage "backports" that conflicted with all the Warty version backports.  That way prioritizing upgrading the backports package would remove the Warty backports and upgrade them to the most recent non-conflicted ones, presumably the Hoary ones.  APT is smart that way.

---

### Post by jdong on 2005-01-22
[QUOTE=YokoZar]You could create a metapackage "backports" that conflicted with all the Warty version backports.  That way prioritizing upgrading the backports package would remove the Warty backports and upgrade them to the most recent non-conflicted ones, presumably the Hoary ones.  APT is smart that way.[/QUOTE]


Now there's an interesting idea. But it's gonna take some time to make happen. With me installing Hoary AMD64 and such in preparation for Hoary backports, it's gonna be a few weeks before I can have the time to do so.

My other method was to use the "~" (less than) operator for the ubp tag. I remember a while ago, Daniel Stone was talking about using it. He said it would come in the future -- I want to know if Hoary's dpkg has it.

---

### Post by akurashy on 2005-01-25
in a weird way i cant use apt-show-versions
and im right now updating to horay =/

---

### Post by jdong on 2005-01-25
You must install apt-show-versions first. It's in Universe.

---

### Post by akurashy on 2005-01-25
kk i think i wont stop the current download and i fix up firefox later O_o

anyway can you gimme the link of hoary backports to redownload firefox later

---

### Post by jdong on 2005-01-25
It seems like Warty's dpkg already makes "foo~4.10ubp1" smaller than "foo". Perfect.

Now if only I knew that 3 months ago.

---

### Post by akurashy on 2005-01-25
ok i updated to hoary
some things failed 
anyway i cant find synaptic package now =/

---

### Post by Technoviking on 2005-02-05
Where are the hoary backports?

---

### Post by DJ_Max on 2005-02-05
[QUOTE=Mike Basinger]Where are the hoary backports?[/QUOTE]
Check out [http://ubuntu-bp.sourceforge.net/](http://ubuntu-bp.sourceforge.net/)

---

### Post by WW on 2005-02-06
I'm no apt guru, but couldn't pinning be used to upgrade to hoary?  Something like: set the pin of the hoary repositories to >1000, then do a dist-upgrade, then put the pins back to normal.  Apt experts, what do you think?

---

### Post by Anubis on 2005-02-06
[QUOTE=DJ_Max]Check out [http://ubuntu-bp.sourceforge.net/](http://ubuntu-bp.sourceforge.net/)[/QUOTE]


Basic Usage Info:
Add a line to your /etc/apt/sources.list like this:
deb [http://ubuntu-bp.sourceforge.net/ubuntu](http://ubuntu-bp.sourceforge.net/ubuntu) warty-backports main universe

If for Hoarty why is it stll named Warty?

---

### Post by dcstar on 2005-02-07
[QUOTE=Anubis]Basic Usage Info:
Add a line to your /etc/apt/sources.list like this:
deb [http://ubuntu-bp.sourceforge.net/ubuntu](http://ubuntu-bp.sourceforge.net/ubuntu) warty-backports main universe
.........[/QUOTE]
I believe the backports repository URL has recently changed to:

[http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/)

And there is an additional repository to "warty-backports": "warty-backports-staging" that contains software which is on the way to the main backports repository.

---

### Post by jdong on 2005-02-07
[QUOTE=dcstar]I believe the backports repository URL has recently changed to:

[http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/)

And there is an additional repository to "warty-backports": "warty-backports-staging" that contains software which is on the way to the main backports repository.[/QUOTE]

This information is correct. I'll post a sticky announcement very soon.

---

### Post by senectus on 2005-02-07
is there any way to upgrade/install from the live cd?

---

### Post by RastaMahata on 2005-03-18
well, this doesnt work...
I do the fist command in the "howto" and this is what I get, life 20 times:
"E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?"

so I tried to do it with sudo, but it gave me the same result.. any suggestions?

---

### Post by kleeman on 2005-03-19
Open a root terminal and run the commands. Had the same prob here...

---

### Post by trinoo on 2005-03-20
[QUOTE=akurashy]ok i updated to hoary
some things failed 
anyway i cant find synaptic package now =/[/QUOTE]
i cant find synaptic package too after the upgrade :(

---

### Post by Grey on 2005-03-21
I just tried the easy way of upgrading to hoary from jdong... but it just didn't work for me.  The first command gave me absolutely no results...  the third command gave me a list of backports a mile long.  I love the warty backports... but it's really ruining my day now.   ](*,) 

I've tried running the command in both a regular and root terminal, and still nothing, either way.  Might there be special prequisites that I don't have?  I'm just not familiar  enough with Linux to figure out what went wrong yet.

---

### Post by Grey on 2005-03-25
*bump*

Since this thread has become unstickified, and ignored for the last little while, I was wondering if anyone has the answer to my question?  I ran the first command as root, and it didn't work.  Just gave me a blank line.  What could possibly be wrong?

---

### Post by jdong on 2005-03-25
Just directly switch everything from warty to hoary in sources.list and dist-upgrade. Hoary has newer versions of everything included in backports!

---

### Post by kleeman on 2005-03-26
Just tried this (in practise mode  :lol: ) and found one exception: the synaptic package in backports appears to be 0.56 but hoary only has 0.55.....Any comments?

---

### Post by jdong on 2005-03-26
Hmm, how'd that happen? ;)

Roll it back after upgrading completely, with "apt-get install synaptic/hoary"

---

### Post by Grey on 2005-03-27
Just upgraded to hoary.  (Before reading the newest two posts).  I did notice that synaptic caused problems, but I did manage to get upgraded sucessfully after a few problems (synaptic crashed halfway through the upgrade, and a few packages wouldn't upgrade, such as firestarter, and the pc wouldn't boot when I rebooted after finishing upgrading (x.org issues)), but I got it all worked out in the end, and can vouch for everything working more or less like it should.  (after dealing with synaptic).

---

### Post by senectus on 2005-03-27
I just upgraded a machine as well.. went pretty well..
How do I tell if it's using Xfree or x.org ?

---

### Post by Grey on 2005-03-27
[QUOTE=senectus]I just upgraded a machine as well.. went pretty well..
How do I tell if it's using Xfree or x.org ?[/QUOTE]
 check in /etc/X11, and if you see xorg.conf, and it's being used, then you are running x.org... at least, that's the way I did it.  I had to explicitly mention that I wanted to install x.org when upgrading to Hoary though (which involves removing xfree86).

---

### Post by senectus on 2005-03-27
[QUOTE=Grey]check in /etc/X11, and if you see xorg.conf, and it's being used, then you are running x.org... at least, that's the way I did it.  I had to explicitly mention that I wanted to install x.org when upgrading to Hoary though (which involves removing xfree86).[/QUOTE]

Sorry if this sounds dumb.. but how do I tell if it's in use?
the ls -l of /etc/X11/ is:
root@white-rose:/etc/X11 # ls -l
total 46
drwxr-xr-x   2 root root  1128 2005-03-27 17:19 app-defaults
drwxr-xr-x   3 root root    80 2004-12-17 19:11 applnk
drwxr-xr-x   2 root root   176 2005-03-27 16:03 cursors
-rw-r--r--   1 root root    13 2004-11-29 22:08 default-display-manager
drwxr-xr-x   7 root root   168 2004-11-29 22:06 fonts
lrwxrwxrwx   1 root root     6 2005-03-27 16:52 gdm -> ../gdm
-rw-r--r--   1 root root 17371 2004-11-17 22:27 rgb.txt
drwxr-xr-x   4 root root   120 2005-03-27 17:18 rstart
drwxr-xr-x   3 root root    80 2004-12-17 19:11 susewm
drwxr-xr-x   2 root root   176 2005-03-27 17:19 sysconfig
lrwxrwxrwx   1 root root    17 2005-03-27 18:10 X -> /usr/bin/X11/Xorg
-rw-r--r--   1 root root  3289 2004-11-30 18:57 XF86Config-4
drwxr-xr-x   2 root root   104 2005-03-27 17:17 xinit
drwxr-xr-x  10 root root   576 2005-03-27 16:50 xkb
-rw-r--r--   1 root root  3289 2005-03-27 18:10 xorg.conf
drwxr-xr-x   2 root root   112 2005-03-27 17:18 Xresources
drwxr-xr-x   2 root root    80 2005-03-27 17:17 xserver
-rwxr-xr-x   1 root root  3911 2004-11-17 22:29 Xsession
drwxr-xr-x   2 root root   352 2005-03-27 17:19 Xsession.d
-rw-r--r--   1 root root   234 2004-11-17 22:29 Xsession.options
drwxr-xr-x   2 root root    80 2005-03-27 17:17 xsm
-rw-------   1 root root   771 2004-11-29 22:07 Xwrapper.config

---

### Post by Grey on 2005-03-27
[QUOTE=senectus]Sorry if this sounds dumb.. but how do I tell if it's in use?
the ls -l of /etc/X11/ is:
root@white-rose:/etc/X11 # ls -l
total 46
drwxr-xr-x   2 root root  1128 2005-03-27 17:19 app-defaults
drwxr-xr-x   3 root root    80 2004-12-17 19:11 applnk
drwxr-xr-x   2 root root   176 2005-03-27 16:03 cursors
-rw-r--r--   1 root root    13 2004-11-29 22:08 default-display-manager
drwxr-xr-x   7 root root   168 2004-11-29 22:06 fonts
lrwxrwxrwx   1 root root     6 2005-03-27 16:52 gdm -> ../gdm
-rw-r--r--   1 root root 17371 2004-11-17 22:27 rgb.txt
drwxr-xr-x   4 root root   120 2005-03-27 17:18 rstart
drwxr-xr-x   3 root root    80 2004-12-17 19:11 susewm
drwxr-xr-x   2 root root   176 2005-03-27 17:19 sysconfig
lrwxrwxrwx   1 root root    17 2005-03-27 18:10 X -> /usr/bin/X11/Xorg
-rw-r--r--   1 root root  3289 2004-11-30 18:57 XF86Config-4
drwxr-xr-x   2 root root   104 2005-03-27 17:17 xinit
drwxr-xr-x  10 root root   576 2005-03-27 16:50 xkb
-rw-r--r--   1 root root  3289 2005-03-27 18:10 xorg.conf
drwxr-xr-x   2 root root   112 2005-03-27 17:18 Xresources
drwxr-xr-x   2 root root    80 2005-03-27 17:17 xserver
-rwxr-xr-x   1 root root  3911 2004-11-17 22:29 Xsession
drwxr-xr-x   2 root root   352 2005-03-27 17:19 Xsession.d
-rw-r--r--   1 root root   234 2004-11-17 22:29 Xsession.options
drwxr-xr-x   2 root root    80 2005-03-27 17:17 xsm
-rw-------   1 root root   771 2004-11-29 22:07 Xwrapper.config[/QUOTE]
 well, I would think that the mere presence of xorg.conf would indicate that it's installed and working.  In my case, my configuration file was hopelessly broken upon installation of warty, so I copied my XF86Config-4 file into my xorg.conf file in recovery mode, and that did the trick.  And thus, I knew that x.org was in use.

I am not sure what the real way of checking is... I'm still too much of a newbie to know that.  Sorry.

---

### Post by Psquared on 2005-03-29
[QUOTE=jdong]Just directly switch everything from warty to hoary in sources.list and dist-upgrade. Hoary has newer versions of everything included in backports![/QUOTE]

I didn't have any backports installed so I just did the above. However, in addition to changing "warty" to "hoary" I commented out all the 3rd party repos like merillat. The upgrade just didn't take and I am back in Warty.

By not taking I mean it downloaded all the packages but gave me some error about a sound problem with instructions on how to modify an emu .... conf file -- which didn't work anyway -- and then hung up. It would not continue. Now maybe I didn't wait long enough, but I thought perhaps it had to restart so I closed the terminal window and restarted. Voila -- still in warty.

Any thoughts?? [-o<

---

### Post by jdong on 2005-04-08
Well, nobody expects such a massive upgrade to be 100% effortless; it does take a bit of work with APT to get the transition. This is not Backports' fault.

---

### Post by mendicant on 2005-04-08
[QUOTE=Grey]And thus, I knew that x.org was in use.

I am not sure what the real way of checking is... I'm still too much of a newbie to know that.  Sorry.[/QUOTE]

You can use xdpyinfo to check:

% xpdyinfo | less
name of display:    :0.0
version number:    11.0
vendor string:    The X.Org Foundation
vendor release number:    60802000
X.Org version: 6.8.2
...

---

### Post by poofyhairguy on 2005-04-08
I succeed moving a Backport using Warty to Hoary, here is how:


These are the directions to upgrade to Hoary on all computers with a broadband connection.

First, edit your sources.list file. Put this line in the terminal:

sudo gedit /etc/apt/sources.list

Then when gedit comes up, replace what is in the sources.list file with everything here:

> &#65279;deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe 
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe 

save gedit for sources.list and exit.

then in the console put this:

sudo apt-get remove synaptic

say yes to whatever, then it do its thing, then put in this:

sudo apt-get update

then when its done, put in this:

sudo apt-get dist-upgrade

this is the big one. The full update. It should work, but it will take a while to download the new Hoary files and install them. Expect to download 500+ megs each time. It takes 26 minutes to do this on my 300mhz laptop, then than 10min on my P4.

NOTE: It is not advisable to do other things with the computer once all the packages are finished downloading and they start installing (after sudo apt-get dist-upgrade command) like web browsing and music and such. The computer is replacing those programs, and if you use them they will crash and hang. just stick to the console after all the Hoary packages are downloaded.

then when its done, put in this:

sudo apt-get install ubuntu-desktop

If it says something like "already is current version", then you are upgraded. Reboot into Hoary.

---

### Post by jdong on 2005-04-08
I'll make a Hoary Synaptic override package. :)

---

### Post by jdong on 2005-04-08
I am now committing a virtually identical copy of Hoary's Synaptic into Hoary Backports, with version number "0.56+revertedto+officialhoary+0.55+cvs20050406-1~5.04ubp1", which will override the badly numbered Warty Backports version of Synaptic.

With this modification, upgrades from Warty to Hoary should take place 100% smoothly, with every backported package overridden by Hoary or Hoary Backports packages.

---

### Post by crane on 2005-04-08
Thanks!! \\:D/

---

