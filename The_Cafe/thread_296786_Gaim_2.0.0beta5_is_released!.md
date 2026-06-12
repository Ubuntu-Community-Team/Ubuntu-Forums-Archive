---
title: "Gaim 2.0.0beta5 is released!"
date: 2006-11-10
forum: The Cafe
---

### Post by Cynical on 2006-11-10
Its been out for a few hours now, apparently several stability changes have been made. Thought some of you might want to try it out.


[http://sourceforge.net/project/showfiles.php?group_id=235&package_id=253&release_id=462444](http://sourceforge.net/project/showfiles.php?group_id=235&package_id=253&release_id=462444)

---

### Post by beuno on 2006-11-10
Any debs for ubuntu yet?

---

### Post by jdong on 2006-11-10
[http://packages.qa.debian.org/g/gaim.html](http://packages.qa.debian.org/g/gaim.html)

Keep a watch on Debian's GAIM packagers for updated packages. You can use prevu to compile it when it comes out by feeding the URL to the .dsc file via the command line (prevu dsc_url)

---

### Post by dyntryx on 2006-11-10
I've never made a .deb package before, so I can't make guarantees. Also, I used the command "./configure --enable-gnutls=yes" when I made this one because I wanted SSL for MSN support.  So, I don't know if that makes a difference.  None-the-less, here it is: [linky linky linky!]("http://bellepointe.org/gaim_2.0.0beta5-1_i386.deb").  Try it if you like.  Also, if it doesn't work.. here's a quick guide to do it yourself:

Grab the source from [here]("http://sourceforge.net/project/showfiles.php?group_id=235&package_id=253&release_id=462444").  Extract it somewhere.  Use the console to go to the directory where you extracted the source.  Issue these commands:
```
sudo apt-get remove gaim
sudo apt-get install build-essential libgtk2.0-dev libgtk2.0-0 libglib2.0-dev libglib2.0-0 libxml-parser-perl libxml-perl libgnutls-dev libgnutls13
./configure --enable-gnutls=yes
sudo make
sudo make install
```
Alternatively, if you don't need MSN, you can just issue "./configure" without the "--enable-gnutls=yes".
I'm no professional, so I don't know how helpful that is.  If anyone wants to correct my procedure or offer a better way, feel free.  Enjoy beta 5 everyone. :)

EDIT:
Something else people who haven't used the beta may be wondering about is the status selector.  If you're status selector doesn't display correctly when Gaim is positioned toward the bottom of the screen, here's the fix.

Create or edit the file ".gtkrc-2.0" in your user's home directory (/home/<username>).  Add these lines to that file:
```
# Customize the New 2.0.0 Status Selector
style "gaim-statusbox-style" {
    # This is a work-around that keeps you from having to scroll
    # if the status selector is at the bottom of the screen.
        GtkComboBox::appears-as-list = 1

    # Depending on your theme and/or GTK+ version, one of
    # the following blocks should eliminate excess padding.
    # The second approach is probably more universally
    # applicable, but the first removes more padding for
    # some people.

    # Eliminate Padding Approach 1
        xthickness = 0
        ythickness = 0

    # Eliminate Padding Approach 2
        xthickness = 2
        ythickness = 2
    GtkWidget::focus-line-width = 0
    GtkWidget::focus-padding = 0
}
widget "*gaim_gtkblist_statusbox*" style "gaim-statusbox-style"
```
That should fix it.  See ya. =)

---

### Post by beercz on 2006-11-10
> **dyntryx said:**
> I've never made a .deb package before, so I can't make guarantees. Also, I used the command "./configure --enable-gnutls=yes" when I made this one because I wanted SSL for MSN support.  So, I don't know if that makes a difference.  None-the-less, here it is: [linky linky linky!]("http://bellepointe.org/gaim_2.0.0beta5-1_i386.deb").  Try it if you like.  

Thanks for this dyntryx.  I downloaded your deb file and installed it, it seems to work OK, I will try it some more tomorrow. I will let you know.

Thanks again.

---

### Post by bruenig on 2006-11-10
I've never seen something in beta for a decade, this has to be a record of some sorts.

---

### Post by Patrick K. on 2006-11-11
My Gaim is working just fine as it is. I'll wait for REPO updates.

---

### Post by chikko on 2006-11-11
the file you published works, but it affects the update manager - it claims that beta5 is OLDER than beta3.1, and requests install -f.
the updater is a little more important for me, so i guess i'm sticking to beta3.1 for now.. :???:

---

### Post by saracen on 2006-11-11
jdong: where do we get prevu from?

---

### Post by picpak on 2006-11-11
Can someone please make a deb with gaim, gaim-data, etc?

---

### Post by jdong on 2006-11-11
> **saracen said:**
> jdong: where do we get prevu from?

Search the forums for prevu, there's a HOWTO I wrote with that info.

---

### Post by jdong on 2006-11-11
> **picpak said:**
> Can someone please make a deb with gaim, gaim-data, etc?

As I said, please wait for Debian Sid packages of beta5 to arrive. It's a matter of waiting a few days at most... is it really worth the potential of breaking your system for that little a wait?

---

### Post by dyntryx on 2006-11-11
> **chikko said:**
> the file you published works, but it affects the update manager - it claims that beta5 is OLDER than beta3.1, and requests install -f.
the updater is a little more important for me, so i guess i'm sticking to beta3.1 for now.. :???:

Yeah, you're right.  Not sure how to fix that, really.  You could open the console and use the command:
```
sudo aptitude hold gaim
```
That would probably at least keep it from bugging you about upgrades.  Although if you opened the Adept Package Manager, it would still list it as "upgradable".  It just wouldn't try to auto-upgrade it... if that helps any. :-?

> **beercz said:**
> Thanks for this dyntryx. I downloaded your deb file and installed it, it seems to work OK, I will try it some more tomorrow. I will let you know.

Thanks again.

Glad to see it at least works for some people.

Like jdong said, you guys can always wait for the Debian Sid packages.  I just happened to get mine working, and thought I'd share. :)

---

### Post by jdong on 2006-11-11
Since we are all soooooo impatient, I'll roll up some safe beta5 packages that are done in the same way as Debian's gaim packages....

You'll have to build them yourself with prevu though, so get your prevu's downloaded and init'ed.

---

### Post by jdong on 2006-11-11
Ok, I've built a beta5 source package based off Debian's beta4 package, but dropped 3 patches (as they fail to apply, presumably already fixed stuff in beta5)

You can build it with prevu by pointing it to:
```

prevu http://buntudot.org/people/~jdong/gaim/gaim_2.0.0+beta5-0jdong1.dsc

```
Then, a simple 'apt-get update; apt-get dist-upgrade' will upgrade gaim for you, if you allowed prevu-init to add itself to sources.list. If not, look for debs in /var/cache/prevu/edgy-debs


I will not distribute binary packages at this time... it's quite simple to build the source packages.


These should be safer than checkinstalled .debs because they use the same packaging style as Debian's packages. However, I am not a uber-skilled packager by any measure, so all the usual disclaimers about installing 3rd party packages applies. When Debian's beta5 package comes out, you're highly encouraged to prevu it and override these packages.


I have tested prevu'ing these packages on Edgy, they build and install fine. I am using the package right now, and so far so good.

---

### Post by GStubbs43 on 2006-11-11
Hi, I tried to use prevu, but when I did ```
prevu http://buntudot.org/people/~jdong/gaim/gaim_2.0.0+beta5-0jdong1.dsc
```, I got this back:
```

Traceback (most recent call last):
  File "/usr/bin/prevu", line 60, in ?
    print "Package %s:\n%s ==> %s" % (sys.argv[1],getsrcver(sys.argv[1]),buildbackportver(sys.argv[1]))
  File "/usr/bin/prevu", line 16, in buildbackportver
    raise NoSuchPackageException, "Source package %s couldn't be found" % pkg
__main__.NoSuchPackageException: Source package http://buntudot.org/people/~jdong/gaim/gaim_2.0.0+beta5-0jdong1.dsc couldn't be found

```

---

### Post by jdong on 2006-11-11
You need a 0.4.x series prevu release, please download updated sourceforge package. If you're coming from an older prevu release, you also need to re-run prevu-init.

---

### Post by GStubbs43 on 2006-11-11
> **jdong said:**
> You need a 0.4.x series prevu release, please download updated sourceforge package. If you're coming from an older prevu release, you also need to re-run prevu-init.

Ahhh... Thanks, I didn't realize there was a newer version. I'm trying it now! :-D

---

### Post by DigitalDuality on 2006-11-11
d

---

### Post by tjansson on 2006-11-12
Strange - I tried to make a .deb file with checkinstall but it fails in the end og checkinstall. I compiled with "./configure --enable-gnutls=yes; make; checkinstall"
> 
....
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/man/man1" || mkdir -p -- "/usr/local/man/man1"
mkdir: cannot create directory `/usr/local/man': File exists
make[2]: *** [install-man1] Error 1
make[2]: Leaving directory `/home/tjansson/gaim-2.0.0beta5/doc'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/tjansson/gaim-2.0.0beta5/doc'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.


---

### Post by jdong on 2006-11-12
Do not checkinstall gaim -- the resultant package will conflict with the existing way gaim is packaged (into several differently-named packages)

If you want to try gaim, use prevu to build the dsc file I gave.

---

### Post by foureight84 on 2006-11-12
i use checkinstall with gaim and it works just fine. you just need to specify the version name so that when you run apt-get dist-upgrade it won't install and older version.

make sure your checkinstall package version reads "1:2.0.0+beta5-1ubuntu9-1" without the ""

---

### Post by shining on 2006-11-13
It's now in debian sid.

---

### Post by jdong on 2006-11-13
The Debian Sid package also has a few sound-related patches that are worth getting; it's a good idea to prevu that package instead.

---

### Post by beuno on 2006-11-13
What's the URL for the SID prevu?
The one previously mentioned seems no longer to be there (I get 404)

---

### Post by jdong on 2006-11-13
Search up gaim on packages.qa.debian.org

---

### Post by beuno on 2006-11-13
I found it here:

[http://ftp.debian.org/debian/pool/main/g/gaim/gaim_2.0.0+beta5-1.dsc](http://ftp.debian.org/debian/pool/main/g/gaim/gaim_2.0.0+beta5-1.dsc)

but I get the following:

```
E: Could not open file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy_main_source_Sources - open (2 No such file or directory)
E: Could not open file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy_main_source_Sources - open (2 No such file or directory)
Traceback (most recent call last):
  File "/usr/bin/prevu", line 60, in ?
    print "Package %s:\n%s ==> %s" % (sys.argv[1],getsrcver(sys.argv[1]),buildbackportver(sys.argv[1]))
  File "/usr/bin/prevu", line 16, in buildbackportver
    raise NoSuchPackageException, "Source package %s couldn't be found" % pkg
__main__.NoSuchPackageException: Source package http://ftp.debian.org/debian/pool/main/g/gaim/gaim_2.0.0+beta5-1.dsc couldn't be found
```

---

### Post by jdong on 2006-11-13
That error has already been posted. Please update your prevu to 0.4.1 to get support for building from .dsc.

---

### Post by beuno on 2006-11-13
I saw it but since I had downloaded the latest version I thought it was covered.
Here's the link for the lastest prevu:
[http://prdownloads.sourceforge.net/ubuntu-bp/prevu_0.4.1-0ubuntu1_all.deb?download](http://prdownloads.sourceforge.net/ubuntu-bp/prevu_0.4.1-0ubuntu1_all.deb?download)

Seemed to work ok after installing the newer version and doing a "sudo prevu-init" (this REALLY takes a while).

Thanks!

---

### Post by jdong on 2006-11-13
prevu-init downloads the debs necessary to initialize a mini Ubuntu environment, so yeah, it'll take a bit of time. Fortunately you only need to do it once.

---

### Post by beuno on 2006-11-13
I've uploaded the debs:

[http://www.uluga.com.ar/archivos/gaim-data_2.0.0+beta5-1~6.10prevu1_all.deb](http://www.uluga.com.ar/archivos/gaim-data_2.0.0+beta5-1~6.10prevu1_all.deb)
[http://www.uluga.com.ar/archivos/gaim_2.0.0+beta5-1~6.10prevu1_i386.deb](http://www.uluga.com.ar/archivos/gaim_2.0.0+beta5-1~6.10prevu1_i386.deb)

I'm not sure if you need any additional dependencies, it's been built with "prevu", so it's provided *as-is*.

---

### Post by hexion on 2006-11-13
Or you can add this repository...

deb [http://repository.debuntu.org/](http://repository.debuntu.org/) edgy multiverse

They updated gaim some hours ago ;)

---

### Post by ciscosurfer on 2006-11-13
> **hexion said:**
> Or you can add this repository...

deb [http://repository.debuntu.org/](http://repository.debuntu.org/) edgy multiverse

They updated gaim some hours ago ;)And to think, I just got prevu all setup, created my new backported gaim beta 5 .deb's via Debian Sid...oh well, such is life.

@jdong,
Fantastic work on your prevu program -- well done!!!

---

### Post by eyelessfade on 2006-11-13
Have anyone made deb package of the last gaim-encryption?

Update: Seems that the Sid package works fine

---

### Post by jdong on 2006-11-13
You can prevu gaim-encryption from Debian Sid, too... just run a sudo prevu-update, then feed prevu the dsc.

---

### Post by ciscosurfer on 2006-11-13
> **jdong said:**
> You can prevu gaim-encryption from Debian Sid, too... just run a sudo prevu-update, then feed prevu the dsc.

Can you give us a link to the Debian Sid .dsc files...I'm trying to find it over there and I'm having a hard time (am I supposed to be looking here: [http://packages.qa.debian.org/g/gaim.html](http://packages.qa.debian.org/g/gaim.html) ?)

Links to guification and encryption and any others.

Thanks!

---

### Post by beuno on 2006-11-13
> **hexion said:**
> Or you can add this repository...

deb [http://repository.debuntu.org/](http://repository.debuntu.org/) edgy multiverse

They updated gaim some hours ago ;)

MUCH better   ;D
I guess I should learn to stay still for a few days.

---

### Post by jdong on 2006-11-13
> **ciscosurfer said:**
> Can you give us a link to the Debian Sid .dsc files...I'm trying to find it over there and I'm having a hard time (am I supposed to be looking here: [http://packages.qa.debian.org/g/gaim.html](http://packages.qa.debian.org/g/gaim.html) ?)

Links to guification and encryption and any others.

Thanks!


Go to the [http://packages.qa.debian.org/](http://packages.qa.debian.org/) homepage, and type in the name of the package you're looking for.

---

### Post by eyelessfade on 2006-11-13
uhm [http://packages.qa.debian.org/g/]("http://packages.qa.debian.org/g/")

---

### Post by eyelessfade on 2006-11-13
Had to find my self another computer do do the work. My laptop don't have enough space for prevu :)

Anyway the gaim-encryption compile went well, but the system want to overwrite my nice gaim-encryption_3.0~beta6-1~6.10prevu1_i386.deb with a old one. How do I stop it from doing that?

---

### Post by ciscosurfer on 2006-11-13
> **jdong said:**
> Go to the [http://packages.qa.debian.org/](http://packages.qa.debian.org/) homepage, and type in the name of the package you're looking for.Thanks.  I obviously need to take a break from my computer--I'm losing it! ](*,)

---

### Post by jdong on 2006-11-13
> **eyelessfade said:**
> Had to find my self another computer do do the work. My laptop don't have enough space for prevu :)

Anyway the gaim-encryption compile went well, but the system want to overwrite my nice gaim-encryption_3.0~beta6-1~6.10prevu1_i386.deb with a old one. How do I stop it from doing that?
This is a case of Debian-Ubuntu packaging conflicts... Ubuntu called their package 3.0+betaX, while Debian is now going by 3.0~betaX.

The best way to handle this is to "dget -x" the .dsc file, cd into the directory, edit debian/changelog and change the ~ to a "+", save & exit, then run prevu.

---

### Post by ciscosurfer on 2006-11-13
Can't you also just place a 'hold' on the older file?

---

### Post by jdong on 2006-11-13
Yeah, as long as you EVENTUALLY remember to unhold it like 4 months down the road :D

---

### Post by marcozs on 2006-11-14
Hey guys I found the debs for edgy at this website:
[http://www.howforge.com/gaim-2-0-0-beta-5-for-ubuntu-edgy-eft-its-time-to-upgrade](http://www.howforge.com/gaim-2-0-0-beta-5-for-ubuntu-edgy-eft-its-time-to-upgrade)
Dowloading now and trying them... has anyone made the deb for guifications???

---

### Post by zachtib on 2006-11-14
> **marcozs said:**
> Hey guys I found the debs for edgy at this website:
[http://www.howforge.com/gaim-2-0-0-beta-5-for-ubuntu-edgy-eft-its-time-to-upgrade](http://www.howforge.com/gaim-2-0-0-beta-5-for-ubuntu-edgy-eft-its-time-to-upgrade)
Dowloading now and trying them... has anyone made the deb for guifications???
I'd reccomend using gaim-libnotify instead, version 0.12 was recently released, and adds support for gaim2b4+  i have it installed and its working fine on beta5

---

### Post by Jbloudg20 on 2006-11-14
I built my own .deb from source, and now the sound for GAIM wont work. Any reccomendations?

---

### Post by jdong on 2006-11-14
Gaim available from Feisty... uploaded today by Sebastien Bacher... haven't checked if it prevus or not.

---

### Post by marcozs on 2006-11-15
> **zachtib said:**
> I'd reccomend using gaim-libnotify instead, version 0.12 was recently released, and adds support for gaim2b4+  i have it installed and its working fine on beta5

Have you got a deb of libnotify for gaim2b5? 
Why do you reccomend it? I like the colorfull guification :)

---

### Post by sigmabetatooth on 2006-11-15
> **hexion said:**
> Or you can add this repository...

deb [http://repository.debuntu.org/](http://repository.debuntu.org/) edgy multiverse

They updated gaim some hours ago ;)

I added the repository to my source list but when I update or upgrade I receive the following message.

> 
W: GPG error: [http://repository.debuntu.org](http://repository.debuntu.org) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0E466170BCF1FC29
W: You may want to run apt-get update to correct these problems


Any idea where I might get this alleged PUBKEY.

---

### Post by shining on 2006-11-15
> **sigmabetatooth said:**
> 
Any idea where I might get this alleged PUBKEY.

[http://repository.debuntu.org/#authentificate](http://repository.debuntu.org/#authentificate)

---

### Post by sigmabetatooth on 2006-11-15
> **shining said:**
> [http://repository.debuntu.org/#authentificate](http://repository.debuntu.org/#authentificate)

That helped. TY!

---

### Post by duffman25 on 2006-11-15
> **sigmabetatooth said:**
> That helped. TY!

I would love to have this in the universe repo instead of having to use 3rd party repositories.

I think this plugin makes more sense than the guifications since there are a lot of apps using libnotify and it makes the desktop more consistent.

Any MOTU wants to do the job? ;) I'd be greatly appreciated

---

### Post by zachtib on 2006-11-15
> **marcozs said:**
> Have you got a deb of libnotify for gaim2b5? 
Why do you reccomend it? I like the colorfull guification :)

i like the fact that libnotify integrates nicer into the rest of the operating system and provides a more unified look.

I have a checkinstall build, but not a 'real' deb.  just grab the source, and ```
./configure && make && checkinstall -D 
```
it yourself, it should build fine

---

### Post by duffman25 on 2006-11-16
> **zachtib said:**
> i like the fact that libnotify integrates nicer into the rest of the operating system and provides a more unified look.

I have a checkinstall build, but not a 'real' deb.  just grab the source, and ```
./configure && make && checkinstall -D 
```
it yourself, it should build fine

I would prefere if it was included in the next release, so I don't have to roll my own deb,  but thanks for the info

---

