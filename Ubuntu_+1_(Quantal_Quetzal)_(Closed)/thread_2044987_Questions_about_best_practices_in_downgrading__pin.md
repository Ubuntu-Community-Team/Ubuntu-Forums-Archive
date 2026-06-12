---
title: "Questions about best practices in downgrading / pinning"
date: 2012-08-20
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by effenberg0x0 on 2012-08-20
Our current problems with Xserver leaved me with a couple doubts:

**Pinning package versions**
1) What is the difference between using the following methods (a,b,c):
a) Using "dpkg --set-selections" (or manually editing /var/lib/dpkg/status to set status "HOLD" on the desired package/version).
b) Using /etc/apt/preferences (despite the fact that it is useful for specifying priority indexes)
c) Use "Lock Version" / "Force Version" on Synaptic

2) How does these options relate? Does apt-get respect what is set in 
/var/lib/dpkg/status? Does dpkg -i respect what is set in /etc/apt/preferences? What about synaptic and aptitude? 

**Upgrading deps/rdeps after pinning**
1) After installing the desired Xserver version from a deb with dpkg -i and pinning it using one of the methods above, is there any difference in using apt-get dist-upgrade or synaptic "normal" upgrade?

Sorry for the lame questions, I think I never had to worry about the specifics of downgrading. I just want to consolidate some ideas and write a wiki about it or something.

Regards,
Effenberg

---

### Post by ventrical on 2012-08-20
mac4man and harry33 had some good workarounds on this a couple of weeks ago and the "force version" in synaptic worked great in downgrading to xserver-xorg 1.12

Now, you can't even do that through synaptic.  Today , after upgrading yet another previous install, I got the same  (firefox won't start, loop back to gdm). The only way to get a temp fix was to remove nvidia-current. I tired some of the methods just previously mentioned in  the recent forum where this debate has been taking place and now I can't mount that filesystem from root using GRUB recovery. Downloading the Precise *.deb was a destroyer for  one of my installs. But I know thats why I am here. This is development release - where breakage *will* occur! :)

---

### Post by xebian on 2012-08-20
> **effenberg0x0 said:**
> Our current problems with Xserver leaved me with a couple doubts:

**Pinning package versions**
1) What is the difference between using the following methods (a,b,c):
a) Using "dpkg --set-selections" (or manually editing /var/lib/dpkg/status to set status "HOLD" on the desired package/version).
b) Using /etc/apt/preferences (despite the fact that it is useful for specifying priority indexes)
c) Use "Lock Version" / "Force Version" on Synaptic

2) How does these options relate? Does apt-get respect what is set in 
/var/lib/dpkg/status? Does dpkg -i respect what is set in /etc/apt/preferences? What about synaptic and aptitude? 

**Upgrading deps/rdeps after pinning**
1) After installing the desired Xserver version from a deb with dpkg -i and pinning it using one of the methods above, is there any difference in using apt-get dist-upgrade or synaptic "normal" upgrade?

Sorry for the lame questions, I think I never had to worry about the specifics of downgrading. I just want to consolidate some ideas and write a wiki about it or something.

Regards,
Effenberg


Why re-invent the wheel?  Just google apt pinning and you will get several good sites - wiki.debian.org, wikipedia, and ubuntu wiki to name a few.

---

### Post by effenberg0x0 on 2012-08-20
> **ventrical said:**
> mac4man and harry33 had some good workarounds on this a couple of weeks ago and the "force version" in synaptic worked great in downgrading to xserver-xorg 1.12

Now, you can't even do that through synaptic.  

Today , after upgrading yet another previous install, I got the same  (firefox won't start, loop back to gdm). The only way to get a temp fix was to remove nvidia-current. I tired some of the methods just previously mentioned in  the recent forum where this debate has been taking place and now I can mount that filesystem from root using GRUB recovery. Downloading the Precise *.deb was a destroyer for  one of my installs. But I know thats why I am here. This is development release - where breakage *will* occur! :)

Hi Ventrical, IMO we need to discuss and define best practices for downgrading packages. As I mentioned in the first post in this thread, there are many ways to do things and the differences aren't totally clear. Almost all recent threads here are now about this same issue. Downgrading is not something we're used to doing. I couldn't find good documentation for that, not even in Debian.
 
About Synaptic: I think "Force Version" will query your dpkg status for for available versions. So considering your dpkg status file is up-to-date with the existing repos (apt-get update), you will only be able to see the versions that are there. It would be the same as running something like this:
```
[16:58:07] ahsl@AL-DESK01:[~]: apt-show-versions -a xorg
xorg 1:7.6+12ubuntu1 hold ok installed
xorg 1:7.7+1ubuntu1 quantal archive.ubuntu.com
No stable version
xorg/quantal upgradeable from 1:7.6+12ubuntu1 to 1:7.7+1ubuntu1

```
One would only be able to Lock/Force a version, via Synaptic, if this version is available in the configured sources and the system dpkg status is up-to-date. If this is correct, then prior to trying to lock/fix a version one should apt-get update to default sources and query dpkg status to see which versions are available.

Suppose you add a precise repo to your quantal sources, apt-get update and query xorg versions. You'll find a PP version of xorg available. You would be able to do something like apt-get install xorg=<pp version number> and pin it, then remove pp repos from sources and apt-get update again. Or if the goal is just to roll back one version, without going into PP realms, there's no need to add anything pp to your sources.

WHat I did was actually different: I went directly to Launchpad via browser and got a deb for the version I wanted. After I installed and pinned it, my system obviously was broken, because all related packages had to be downgraded too. Fixing those deps then is doable:
- By also downloading/installing all their debs for the correct releases;
- Trusting synaptic "fix broken deps" will downgrade them to correct versions
- Trusting apt-get dist-upgrade will do the same

So, the real deal here is not just downgrading one package, but them querying this package to see what it depends on and what depends on it, and then fix these other packages accordingly. To do this manually or through some GUI tool will depend on each one's preferences. 

Example: You can have a look at info like depends, rdepends, breaks/conflicts, provides, etc using dpkg-query:
```
dpkg-query -W -f="Package:${Package}\nVersion:${Version}\nDepends:${Depends}\nRdepends:${Pre-Depends}\n\n' xorg

```Another possibility:
```
dpkg --print-avail xorg
```
Yet another one:
```
apt-cache show xorg
```
And a more complete one:
```
apt-cache showpkg xorg

```

Regards,
Effenberg

---

### Post by effenberg0x0 on 2012-08-20
> **xebian said:**
> Why re-invent the wheel?  Just google apt pinning and you will get several good sites - wiki.debian.org, wikipedia, and ubuntu wiki to name a few.

Yes, there are lots of tutorials. Some mention pinning via dpkg, some mention doing it via apt preferences. Which is better? Which is or will be deprecated? Why? This sort of info I couldn't find in reliable official sources. I can't really say if the different tutorials I found online are all correct, I didn't read/compared all of them, don't know the people who wrote them or when they were written. The info in Ubuntu Wiki is clearly outdated and incomplete. Considering the above, the fact that we are contributors to Ubuntu and this is an interesting subject in testing, looking into the future and also considering our very real need for improving our technical and formal documentation, I do not feel like such a small effort would be reinventing the wheel. That is, of course, my personal opinion. 

Regards,
Effenberg

---

### Post by Sworddragon on 2012-08-20
/etc/apt/preferences has the advantage that you still uses apt and the dependencies will be resolved if your pinnings are correct. Before I downgraded to the XServer 1.11.4 from Precise I tried to pin to the previous version from Quantal (which you have downloaded from Launchpad). But it seemed that this version wasn't available anymore with apt so I decided to downgrade to the Precise version.

---

### Post by kansasnoob on 2012-08-21
> **effenberg0x0 said:**
> Our current problems with Xserver leaved me with a couple doubts:

**Pinning package versions**
1) What is the difference between using the following methods (a,b,c):
a) Using "dpkg --set-selections" (or manually editing /var/lib/dpkg/status to set status "HOLD" on the desired package/version).
b) Using /etc/apt/preferences (despite the fact that it is useful for specifying priority indexes)
c) Use "Lock Version" / "Force Version" on Synaptic

2) How does these options relate? Does apt-get respect what is set in 
/var/lib/dpkg/status? Does dpkg -i respect what is set in /etc/apt/preferences? What about synaptic and aptitude? 

**Upgrading deps/rdeps after pinning**
1) After installing the desired Xserver version from a deb with dpkg -i and pinning it using one of the methods above, is there any difference in using apt-get dist-upgrade or synaptic "normal" upgrade?

Sorry for the lame questions, I think I never had to worry about the specifics of downgrading. I just want to consolidate some ideas and write a wiki about it or something.

Regards,
Effenberg

I prefer using "echo <packagename> hold | sudo dpkg --set-selections" because setting "lock" in synaptic is overridden by apt, but I recently had to figure out how to "hold" a number of packages and asked a question:

[http://ubuntuforums.org/showthread.php?t=2022112](http://ubuntuforums.org/showthread.php?t=2022112)

That introduced me to using a "for loop" :)

And it enabled me to do this:

[http://ubuntuforums.org/showpost.php?p=12093593&postcount=20](http://ubuntuforums.org/showpost.php?p=12093593&postcount=20)

The brilliance of our various members never ceases to amaze me :D

---

### Post by ventrical on 2012-08-22
> **effenberg0x0 said:**
> Hi Ventrical, IMO we need to discuss and define best practices for downgrading packages. As I mentioned in the first post in this thread, there are many ways to do things and the differences aren't totally clear. Almost all recent threads here are now about this same issue. Downgrading is not something we're used to doing. I couldn't find good documentation for that, not even in Debian.
 
About Synaptic: I think "Force Version" will query your dpkg status for for available versions. So considering your dpkg status file is up-to-date with the existing repos (apt-get update), you will only be able to see the versions that are there. It would be the same as running something like this:
```
[16:58:07] ahsl@AL-DESK01:[~]: apt-show-versions -a xorg
xorg 1:7.6+12ubuntu1 hold ok installed
xorg 1:7.7+1ubuntu1 quantal archive.ubuntu.com
No stable version
xorg/quantal upgradeable from 1:7.6+12ubuntu1 to 1:7.7+1ubuntu1

```One would only be able to Lock/Force a version, via Synaptic, if this version is available in the configured sources and the system dpkg status is up-to-date. If this is correct, then prior to trying to lock/fix a version one should apt-get update to default sources and query dpkg status to see which versions are available.


  This was a problem with me a while back  during Precise testing. I *locked* versions in synaptic and then when I <sudo apt-get update/upgrade> or use synaptic to update it ripped the locked versions right out!

 Ok.. let me  take a back-step here.

Suppose I have Kernel 3.4.0-1 of Quantal release (in which Unity 2D is still functional and Nautilus is at a stage where when I click properties/permissions I still get <ventrical> as oppossed to <me>. Now, without  getting any ppas or making any changes to sources.list how do I simply pin them?

---

### Post by effenberg0x0 on 2012-08-22
@Ventrical: Just jump to the last topic (Pinning the Packages Versions) if you need a fast answer :) The text below is my own attempt at studying and learning about this subject.

If you already have those packages installed, we don't have to talk about sources.list, PPAs or manual download/install of packages .deb file. In your example, there's no need to downgrade from non-working/not-wanted packages versions to working/preferred packages versions: You already have them working in your install, you just want to keep them from being upgraded (replaced by more recent releases of their packages). That's the pure definition of pinning. All we discussed about sources.list, PPAs, installing manually downloaded .deb files with dpkg -i were hacks to downgrade.

Ok, now let's pretend we don't know which exact packages provide kernel and Nautilus. We need to query something to get this information and we have some alternatives.

**FINDING THE RIGHT PACKAGES**
**1)** dpkg --search <string> or dpkg-query --search <string>
This will search the dpkg information stored in your PC at /var/lib/dpkg/status. Just nano this file to understand what it is about and how it is organized. <string> can be a part of the file name you are looking for (you can't use a regular expression).

dpkg-query is just a frontend for dpkg. Have a look at "man dpkg-query" and you will see some interesting options there.

Try to run dpkg --search nautilus. You will get a lot of output on console, because there are many references to this word in packages informations. We need to be more specific.

What is executed when we run nautilus? We can find this with the command "whereis".
```

$ whereis nautilus
nautilus: /usr/bin/nautilus /usr/lib/nautilus /usr/bin/X11/nautilus /usr/share/nautilus /usr/share/man/man1/nautilus.1.gz

```
We got 5 answers. The one we want is the first (inside bin, the binary executable of nautilus). If we investigate, we can see that the first answer (the binary for nautilus) is in one package, while the fourth answer (/usr/share/nautilus) comes from another package.
```

dpkg --search /usr/bin/nautilus
nautilus: /usr/bin/nautilus

$ dpkg --search /usr/share/nautilus
nautilus-data: /usr/share/nautilus

```

**2)** apt-file search <string>
apt-file creates a local database of information about packages available at repos. By using it, we are not limited the information we have stored locally (in /var/lib/dpkg/status). We need to let it create a database that we can then query later. 
```

$ apt-file search nautilus
E: The cache is empty. You need to run 'apt-file update' first.

```
The database needs to be created. Let's do it.
```

$ sudo apt-file update 

```
The first time you run the command above, it will take some time to get information from the servers mentioned in your sources and populate a local database.
```

$ apt-file search nautilus 

```
Again, you will get a lot of output and for the same reasons I mentioned previously. We need to trim things down. Lucky for us, apt-file supports the use of regular expressions (REGEX)
```

$ apt-file search -x "/usr/bin/nautilus$"
nautilus: /usr/bin/nautilus
nautilus-dbg: /usr/lib/debug/usr/bin/nautilus

```

**3)** apt-cache search <REGEX>
apt-cache will not build a new database and will rely on information already stored locally. The advantage over dpkg --search is that it also supports regular expressions.
As you probably expect at this point, you will also get a lot of output if you just search for "nautilus", as I explained previously. And I jus said it supports REGEX, so let's try it. I'll list only the lines that start (^) with the word nautilus using REGEX.
```

$ apt-cache search '^nautilus'
nautilus-sendto - integrates Evolution and Pidgin into the Nautilus file manager
nautilus-compare - Context menu comparison extension for Nautilus file manager
nautilus-emblems - emblems property page for nautilus
nautilus-gtkhash - nautilus extension for computing checksums and more using gtkhash
nautilus-ideviceinfo - utility showing information of idevices on nautilus
nautilus-image-manipulator - Resize and send images from Nautilus
nautilus-open-terminal - nautilus plugin for opening terminals in arbitrary paths
nautilus-qdigidoc - Nautilus file manager support for QDigiDoc client
nautilus-script-audio-convert - A nautilus audio converter script
nautilus-script-collection-svn - Nautilus subversion management scripts
nautilus-script-debug - Simple nautilus debugging script
nautilus-script-manager - A simple management tool for nautilus scripts
nautilus-wallpaper - Nautilus extension. Add a "set as wallpaper" entry in context menu
nautilus-wipe - Secure deletion extension for Nautilus
nautilus-dropbox - Dropbox integration for Nautilus
nautilus - file manager and graphical shell for GNOME
nautilus-dbg - file manager and graphical shell for GNOME - debugging version
nautilus-sendto-empathy - GNOME multi-protocol chat and call client (nautilus-sendto plugin)
nautilus-share - Nautilus extension to share folder using Samba
nautilus-actions - nautilus extension to configure programs to launch
nautilus-bzr - Bazaar (bzr) integration for nautilus
nautilus-clamscan - Antivirus scanning for Nautilus
nautilus-filename-repairer - Nautilus extension for filename encoding repair
nautilus-image-converter - nautilus extension to mass resize or rotate images
nautilus-pastebin - Nautilus extension to send files to a pastebin
nautilus-scripts-manager - simple tool for nautilus scripts management
nautilus-data - data files for nautilus

```
One of the packages above provide /usr/bin/nautilus. We know it's the package named "nautilus" (16th line). 

**4)** Finally, we can use packages.ubuntu.com. It's pretty much self-explanatory. JUst type "nautilus" in the search box, mark "package names only", get some results, filter them by Ubuntu release, etc. 

Going back to your example we aleady know that, unsurprisingly, the packages named "nautilus" is the package that provides nautilus. If you use any of the methods above, you will find out the kernel is provided by the linux-image* file. 

One thing to note is that you can investiate which packages depend on the nautilus and kernel packages and which packages they depend on using dpkg-query. You can use many different syntax. Here's an example:
```

$ dpkg-query -S nautilus

```
You can also use -W and -f options to fully customize the output. Another example:
```

dpkg-query -W -f='\nThe package named ${Package} provides:\n${Provides}\n\nIt depends on the following packages:\n${Depends}\n\n' linux-image-$(uname -r)

```

**EDIT:** I have piped the output of the command "uname -r" to the string "linux-image-" instead of manually typing the full package name in the command above, because I assume one would pin the kernel that is currently in use, i.e. the one currently loaded. Its just a lazy trick to avoid typing and eventual typos (which are actually frequent for me).

**FINDING OUT THE VERSION CURRENTLY INSTALLED**
Suppose you didn't new the version of the nautilus and kernel packages you want to pin. In order to find out, you can also do that in different ways, which include simply using nano to edit /var/lib/dpkg/status and search for status information about the packages. The easy way I'll use here relies on dpkg-query, which will do exactly that for us.

```

$ dpkg-query -W nautilus
nautilus	1:3.5.5-0ubuntu3
$ dpkg-query -W linux-image-$(uname -r)
linux-image-3.5.0-10-generic	3.5.0-10.10

```

**PINNING THE PACKAGES VERSIONS**
Again, you could go hardcore and manually edit (nano, gedit) /var/lib/dpkg/status to set the desired packages versions to a "Hold" status. If you use the dpkg --set-selections command it will do exactly that for you (as I mentioned in my first post in this thread).

We can also do it using apt. You have to open /etc/apt/preferences in any editor (nano, gedit, etc). You need root permissions to edit it. 

```

$ sudo nano /etc/apt/preferences

```
There are many ways to write instructions to apt preferences. Have a look at man apt_preferences to learn some. Here's one way to do it:
```

Package: nautilus
Pin: version 1:3.5.5-0ubuntu3
Pin-Priority: 1001

Package: linux-image-3.5.0-10-generic
Pin: version 3.5.0-10.10
Pin-Priority: 1001

```
After setting apt-preferences with the instructions above, you will be warned about new versions when you run apt-get update && apt-get upgrade, but more recent releases of this packages (as well as the packages that depend on them) will not be upgraded.

OBS: Sorry for the wall of text. This is not meant to be a "tutorial thread", as it would go against current UF policy. I'm studying the subject myself and writting a wiki page, so I already had the content above in drafts.

Regards,
Effenberg

---

### Post by mc4man on 2012-08-22
My self still think in a dev install the easiest way to downgrade is to simply acquire the needed packages & use dpkg, doesn't seem a "hack", just common sense.
As far as pinning that's just personal choice I guess - obviously the easiest method is just to not upgrade packages one has downgraded

As in the example of nautilus one would still need to understated the various nautilus packages & relationships. So what will happen if you downgrade  the nautilus package itself or  pin an earlier version & let others update?

---

### Post by effenberg0x0 on 2012-08-23
> **mc4man said:**
> My self still think in a dev install the easiest way to downgrade is to simply acquire the needed packages & use dpkg, doesn't seem a "hack", just common sense.
As far as pinning that's just personal choice I guess - obviously the easiest method is just to not upgrade packages one has downgraded
I agree with you. I find it easier to just get the deb I want via wget and dpkg install it. 
> **mc4man said:**
> 
As in the example of nautilus one would still need to understated the various nautilus packages & relationships. So what will happen if you downgrade  the nautilus package itself or  pin an earlier version & let others update?

Yep, which is why I mentioned looking at depends/rdepends via dpkg-query. That's where I'm not too confident yet. It's a question I also have, which I am about to test (as soon as I finish some other stuff). I believe that if "nautilus version n" pkg is pinned, packages that depend on "nautilus version n+1" will show on apt-get update&&apt-get upgrade but they won't be upgraded, because dependencies are not met (nautilus version n+1 won't ever be installed unless the pin is removed). I'm considering looking at the solutions proposed by aptitude --full-resolver to verify this in more detail.

However, I'm just guessing. I haven't tested it enough times to be completely sure.

Another example, using the situation proposed by Ventrical: We pinned linux-image*, but we haven't pinned linux-headers*, etc. 


Regards,
Effenberg

---

### Post by mc4man on 2012-08-23
I mentioned nautilus because it's a decent ex.
You'll notice nautilus's dep on nautilus-data - 
>=1:3.5, <1:3.6
That doesn't guarantee  that nautilus 3.5.3 (last pre-me), will actually work with nautilus-data 3.5.X where X is >3
or that any 3.5.X will work with ..data 3.5.X when the X's are different

---

### Post by effenberg0x0 on 2012-08-23
> **mc4man said:**
> I mentioned nautilus because it's a decent ex.
You'll notice nautilus's dep on nautilus-data - 
>=1:3.5, <1:3.6

I see, I haven't seen this until you mentioned it:
```

Package: nautilus
Version: 1:3.5.5-0ubuntu3
Depends: [...]nautilus-data (>= 1:3.5), nautilus-data (<< 1:3.6)[...]

```
> **mc4man said:**
> 
That doesn't guarantee  that nautilus 3.5.3 (last pre-me), will actually work with nautilus-data 3.5.X where X is >3
or that any 3.5.X will work with ..data 3.5.X when the X's are different
Sorry, you lost me :) Let me try to understand: It says it needs 3.5.* <= x < 3.6.*. Ok, we have the following at [https://launchpad.net/ubuntu/quantal/amd64/nautilus-data:](https://launchpad.net/ubuntu/quantal/amd64/nautilus-data:)

```
3.5.1-0ubuntu1
3.5.1-0ubuntu2
3.5.1-0ubuntu3
3.5.1-0ubuntu4
3.5.1-0ubuntu5
3.5.1-0ubuntu6
3.5.2-0ubuntu2
3.5.2-0ubuntu3
3.5.3-0ubuntu1
3.5.4-0ubuntu1
3.5.4-0ubuntu2
3.5.4-0ubuntu3
3.5.5-0ubuntu1
3.5.5-0ubuntu2
3.5.5-0ubuntu3
3.5.90-0ubuntu1

```

All of them are within the range, so we wouldn't have broken deps with any of them. All were deleted / superseeded and the latest (1:3.5.90-0ubuntu1) is on repos right now. But it still fits the range. Then why wouldn't it work? 

Do you mean work in the sense of the programs that are within the pkgs functioning correctly or work in the sense of broken/not-broken deps?

Regards,
Effenberg

PS: It's late and I'm very tired. I'm not even [understanding Ubuntu pictograms]("http://ubuntuforums.org/showthread.php?t=2043650") anymore. I'm obviously missing something you already said... I'll look at it again after a night of sleep.

---

### Post by mc4man on 2012-08-23
I guess the simplest demo would be just mismatch versions of nautilus & nautilus-data. So for instance 
3.5.5-0ubuntu3 <nautilus> pinned or downgraded
3.5.90-0ubuntu1 <nautilus-data> current version

or in the example of ventrical, he likely had 
3.5.3-0ubuntu1 <nautilus> pinned
so then up nautilus-data, not pinned,  to current of  3.5.90-0ubuntu1

At least here on re-login nautilus would fail

So here where I'm always altering nautilus a bit I keep all source packages at same source version (3 - 6 packages depending on whether -dev's ,dbg are installed), irregardless of whether the deps require or not

---

### Post by ventrical on 2012-08-23
> **mc4man said:**
> My self still think in a dev install the easiest way to downgrade is to simply acquire the needed packages & use dpkg, doesn't seem a "hack", just common sense.
As far as pinning that's just personal choice I guess - obviously the easiest method is just to not upgrade packages one has downgraded

As in the example of nautilus one would still need to understated the various nautilus packages & relationships. So what will happen if you downgrade  the nautilus package itself or  pin an earlier version & let others update?

Thanks mac4man and effenberg. I tired to do this with a version of Edubuntu but I used a different method. I tried to use synaptic to pin and 'force' versions but that did not work as it had busted pipes and depends to other objects and modules. I am going to study effenbergs script a little bit more. I think it is important. Also with xsever-xorg. I had it working and then when the nvidia-current driver would not work with 1.13 it really broke one of my desktops pretty bad. My fault because I skipped a few steps.

@effenberg

Don't worry too much about giving me instrutions and even if I bork a desktop because I have so many PCs running. I import all my important stuff so I'm not loosing any data if I scratch any particular desktop. Thanks very much. I think this is an interesting subject that some of us should keep investigating.

---

### Post by bmbaker on 2012-10-10
thanks for these great posts :-)
just spent a few days  having to do upgrades using synaptic instead of the terminal because of the nvidia-current weirdness!
i locked the package in synaptic then discovered it didn't transfer over into apt-get!
i fast google-search and 3 different ubuntu references to this and one other thread :-)
super :-)

---

