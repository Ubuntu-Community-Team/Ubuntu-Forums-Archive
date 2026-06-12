---
title: "apt-get install php5-gd issues"
date: 2007-05-24
forum: Server Platforms
---

### Post by hawzor on 2007-05-24
Hi all, new Ubuntu convert from Debian.

Just did a base install of Dapper Drake and selected LAMP server. This thus kindly gave me Apache2 and php5. Now, word is that php5 "contains" all of the GDlib code, so no special packages should be required to get gd image handling. This appears to be false. A quick phpinfo(); reveals no gdlib in my system. My gd-dependent scripts are dysfunctional.

OK, no problem. I read around and see: [http://ubuntuforums.org/showthread.php?t=66922](http://ubuntuforums.org/showthread.php?t=66922)

I infer that the right thing to do is to:

 **sudo apt-get install php[COLOR="SeaGreen"]*5*[/COLOR]-gd  **(at least one other location I found recommends same  [http://www.nabble.com/GDLib-for-PHP-t1124914.html](http://www.nabble.com/GDLib-for-PHP-t1124914.html) )

Here is the beef after running the above:

 [COLOR="Navy"]The following packages have unmet dependencies:
   php5-gd: Depends: php5-common (= 5.1.2-1ubuntu3) but 5.1.2-1ubuntu3.1 is to be installed
 E: Broken packages[/COLOR]

So to be sure, I run **sudo apt-get install php5-common **and get:

 [COLOR="navy"]php5-common is already the newest version.
 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/COLOR]

Remaining calm...  The second link above suggests running **sudo apt-cache search gd | grep lib **and then apt installing the libs. This is where it goes off the tracks. There are only about a bazillion libs in that found set, so, really no way.

I assume I have simply done something very impractical for a very commonly used tool. The latest advice on this apt-get matter would be much appreciated, thanks!

BTW, found this other link [http://ubuntuforums.org/showthread.php?t=264889&highlight=gdlib](http://ubuntuforums.org/showthread.php?t=264889&highlight=gdlib) but it refers to a manual compilation method that I dearly wish to avoid. I want to stick with apt-get throughout on this new clean box, and I think I ought to be able to, no?

---

### Post by turinglabs on 2007-05-25
> **hawzor said:**
> 
 [COLOR="Navy"]The following packages have unmet dependencies:
   php5-gd: Depends: php5-common (= 5.1.2-1ubuntu3) but 5.1.2-1ubuntu3.1 is to be installed
 E: Broken packages[/COLOR]


Has it been a while since you've run 'apt-get update'? You might try  'apt-get update && apt-get -f install' to see if apt will fix this for you. It may be that you need to put a hold on the php5-common package to prevent apt (echo "php5-common hold" | dpkg --set-selections) from trying to upgrade it, or (last resort) force a manual install of the php5-gd package with something like 'dpkg -i --force-depends-version <package filename>'.

---

### Post by hawzor on 2007-05-25
Thanks for the tip set Doug (turinglabs). So here is what happened:

First, sorry for not saying so in my original post but I actually had just run apt-get update seconds before doing the strokes above, and my sources.list is wide open to the universe and multiverse (I only commented out Dapper Drake CD lines).

Then I ran your first suggestion:

**sudo apt-get update && apt-get -f install**

And got:[COLOR="Navy"] Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 36 not upgraded.[/COLOR]

Checked for gdlib anyway in phpinfo(). Zippo. Bleh. Restart Apache. Nada.

I went to tip #2:

[B]sudo echo "php5-common hold" | dpkg --set-selections
sudo apt-get install php5-gd[/B]

And got a BOATLOAD of installation blat that I didn't get before. So something was cooking for ~150 lines. Somewhere in between it said:

...
[COLOR="navy"]Setting up libapache2-mod-php5 (5.1.2-1ubuntu3.8) ...
 * Forcing reload of apache 2.0 web server...
[ ok ][/COLOR]...

And then the install came to rest. I checked gdlib by phpinfo(), and it appeared to have accomplished ***nothing***. I then ***restarted ***Apache manually to be sure, and hotdang! there it was, just like I planned it that way.

Mr. Doug Maxwell, your eliteness outgrabes! Thanks very much!


**NB:** this large set of updates that I was able to pull with this command set obviously contained some network security "enhancements" that changed my ifconfigs. Reboot the box to be sure things are nice and stable, and behold how the eth0 interface changes. Will require some extra legwork...

---

### Post by turinglabs on 2007-05-28
No problem, I'm glad it worked for you. You might want to submit a bug against php5-gd, it probably just needs its control file updated. I looked to see if there were any bug reports when I first read your post, but I didn't see any for specifically this problem.

---

