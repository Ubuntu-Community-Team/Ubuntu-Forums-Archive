---
title: "Pidgin 2.2.0 Released!!"
date: 2007-09-14
forum: The Cafe
---

### Post by Kosimo on 2007-09-14
[http://www.pidgin.im/](http://www.pidgin.im/)

Very easy to install:

Download the source code:

Then:
> ./configure
make
sudo make install

It takes some time to compile.

Enjoy!


EDIT: 
Now Pidgin 2.2.0 is available at [www.getdeb.net](www.getdeb.net) just download the two debs and installs first the DATA one.

---

### Post by zolero on 2007-09-14
Thanks for the announce Kosimo. I'll give it a try.

---

### Post by Kingsley on 2007-09-14
Why don't they ever have a .deb compiled for Ubuntards and lazy people :(?

---

### Post by IainR on 2007-09-14
I'm new to this so I may have missed something obvious....

Downloaded pidgin-2.2.0.tar.bz2 then tried ./configure with the following result:
nathan@nathan-laptop:~$ ./configure
bash: ./configure: No such file or directory

so tried extracting then ./configure but got the same result.

Please point me in the right direction

---

### Post by urk_nono on 2007-09-14
Could you post a detailed install receipy? I'm a nooblet

---

### Post by Kingsley on 2007-09-14
> **IainR said:**
> I'm new to this so I may have missed something obvious....

Downloaded pidgin-2.2.0.tar.bz2 then tried ./configure with the following result:
nathan@nathan-laptop:~$ ./configure
bash: ./configure: No such file or directory

so tried extracting then ./configure but got the same result.

Please point me in the right direction
You need to untar the thing you downloaded and cd into the directory.

```
tar xjvf pidgin*
```

---

### Post by ryno519 on 2007-09-14
If you have some trouble with the ./configure not finding all of the dependencies, try this.

> 
tar xjvf pidgin-2.2.0.tar.bz2

cd pidgin-2.2.0

sudo apt-get build-dep gaim

sudo apt-get install libnss3-0d

./configure

make

sudo make install


That should do it.

---

### Post by IainR on 2007-09-14
> **Kingsley said:**
> You need to untar the thing you downloaded and cd into the directory.

```
tar xjvf pidgin*
```

Hmmm, think I,m tying myself in knots here!

nathan@nathan-laptop:~$ tar xjvf pidgin*
tar: pidgin*: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

---

### Post by urk_nono on 2007-09-14
> **ryno519 said:**
> If you have some trouble with the ./configure not finding all of the dependencies, try this.



That should do it.

You da man.

---

### Post by cawill on 2007-09-14
What are the improvement's over the old version? Can't seem to find the release notes yet.

EDIT: Found it: [http://www.pidgin.im/ChangeLog]("http://www.pidgin.im/ChangeLog")

---

### Post by Kingsley on 2007-09-14
> **cawill said:**
> What are the improvement's over the old version? Can't seem to find the release notes yet.
[http://www.pidgin.im/ChangeLog](http://www.pidgin.im/ChangeLog)

---

### Post by ryno519 on 2007-09-14
It looks like they fixed a lot of things people have been complaining about with Pidgin lately.

---

### Post by ryno519 on 2007-09-14
If you're getting an error along the lines of "libpurple.so. cannot be found, yadda yadda yadda" here's a possible solution. It seems to be because libpurple was installed in /usr/local/lib instead of /usr/lib, so you can either re-install with the correct configuration options or use this simple hack.

```

sudo ln -s /usr/local/lib/libpurple.so.0 /usr/lib/

```

---

### Post by Kosimo on 2007-09-14
For who's having problems compiling....

Just saying that in a few days we'll have pidgin 2.2.0 deb's in getdeb.net

---

### Post by Spike-X on 2007-09-14
I'm guessing it'll end up in the repos for automatic update too?

---

### Post by ryno519 on 2007-09-14
> **Spike-X said:**
> I'm guessing it'll end up in the repos for automatic update too?

Mmmmmmmaybe for Gutsy, but probably not.

[http://www.getdeb.net](http://www.getdeb.net) will have it on there eventually.

---

### Post by Kosimo on 2007-09-14
> **ryno519 said:**
> Mmmmmmmaybe for Gutsy, but probably not.

[http://www.getdeb.net](http://www.getdeb.net) will have it on there eventually.


We're working on it 

[http://ubuntuforums.org/showthread.php?t=551105](http://ubuntuforums.org/showthread.php?t=551105)

---

### Post by Alkaif on 2007-09-14
so i tried to make a debian package for it, for the first time and you know what, i dont mind hitting on temporary road blocks but for some reason this error always comes up:

dpkg-deb: subprocess paste killed by signal (Broken pipe)


after the debian package is made :(.

does anyone know how to fix that?

---

### Post by cwhisperer on 2007-09-15
hi,

install from source worked fine, some libs to install manually that's all...

seems like old sounds are missing, any idea how to fix this...? regards

---

### Post by Gargamella on 2007-09-15
I saw the changelog, they added myspaceIM plugin...so fast

nice job pidgin team!!

---

### Post by zanglang on 2007-09-15
I've just uploaded it onto my Launchpad PPA for it to be built. I suspect the packages would work on Feisty as well, so if anyone is keen to try, here's my repository: :)
> deb [http://ppa.launchpad.net/zanglang/ubuntu](http://ppa.launchpad.net/zanglang/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/zanglang/ubuntu](http://ppa.launchpad.net/zanglang/ubuntu) gutsy main

There are only i386 packages for now. A minor bug with Launchpad caused the AMD64 builds to fail, and I'm not too sure how it all works yet, so hopefully it may be some time until it gets rebuilt soon.

---

### Post by MagnetiK on 2007-09-15
Your packtage doesn't work du to other dependencies

---

### Post by zolero on 2007-09-15
Yeah.
Dependency is libatk1.0

---

### Post by jimbo99 on 2007-09-15
So where's the package for ubuntu.  Ubuntu is top of the line so one would expect these guys to have the release out immediately if not sooner.  In fact, I don't believe there's an official ubuntu package for any version of pidgin.

---

### Post by mthei on 2007-09-15
Feisty users: 
For those who want to replace GAIM with Pidgin without removing the ubuntu-desktop package (which will cause you to no longer be able to upgrade versions of Ubuntu), you can install a repository from here: [http://ubuntuforums.org/showpost.php?p=2722318&postcount=6](http://ubuntuforums.org/showpost.php?p=2722318&postcount=6)

This will change GAIM to Pidgin, so you won't be stuck with both on your computer. It's up to date, so this new version is already there.

---

### Post by chantra on 2007-09-15
Hi Guys,
You can find a .deb package for Feisty of pidgin 2.2.0 on my repo [http://repository.debuntu.org]("http://repository.debuntu.org"), it is a port of the gutsy package.

---

### Post by dbloom on 2007-09-15
anyone having trouble compiling v2.2.0?  i've compiling it myself since the first version, but now i'm getting an error with ssl-gnutls.c.  see below.

> ssl-gnutls.c: In function 'ssl_gnutls_handshake_cb':
ssl-gnutls.c:166: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
ssl-gnutls.c:166: error: 'cert_list' undeclared (first use in this function)
ssl-gnutls.c:166: error: (Each undeclared identifier is reported only once
ssl-gnutls.c:166: error: for each function it appears in.)
ssl-gnutls.c:167: warning: ISO C90 forbids mixed declarations and code
ssl-gnutls.c:168: error: 'gnutls_session_t' undeclared (first use in this function)
ssl-gnutls.c:168: error: expected ';' before 'session'
ssl-gnutls.c:169: warning: ISO C90 forbids mixed declarations and code
ssl-gnutls.c:172: error: 'session' undeclared (first use in this function)
ssl-gnutls.c:185: error: 'gnutls_x509_crt_t' undeclared (first use in this function)
ssl-gnutls.c:185: error: expected ';' before 'cert'
ssl-gnutls.c:187: error: 'cert' undeclared (first use in this function)
ssl-gnutls.c: At top level:
ssl-gnutls.c:366: warning: type defaults to 'int' in declaration of 'gnutls_datum_t'
ssl-gnutls.c:366: error: expected ';', ',' or ')' before 'dt'
ssl-gnutls.c: In function 'ssl_gnutls_get_peer_certificates':
ssl-gnutls.c:377: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
ssl-gnutls.c:377: error: 'cert_list' undeclared (first use in this function)
ssl-gnutls.c:378: warning: ISO C90 forbids mixed declarations and code
ssl-gnutls.c:392: error: implicit declaration of function 'x509_import_from_datum'
ssl-gnutls.c:392: warning: nested extern declaration of 'x509_import_from_datum'
ssl-gnutls.c:393: warning: initialization makes pointer from integer without a cast
ssl-gnutls.c: At top level:
ssl-gnutls.c:415: error: expected specifier-qualifier-list before 'gnutls_x509_crt_t'
ssl-gnutls.c: In function 'x509_crtdata_delref':
ssl-gnutls.c:441: error: 'x509_crtdata_t' has no member named 'crt'
ssl-gnutls.c: At top level:
ssl-gnutls.c:460: warning: type defaults to 'int' in declaration of 'gnutls_datum_t'
ssl-gnutls.c:460: error: expected ';', ',' or ')' before 'dt'
ssl-gnutls.c: In function 'x509_import_from_file':
ssl-gnutls.c:495: error: 'gnutls_datum_t' undeclared (first use in this function)
ssl-gnutls.c:495: error: expected ';' before 'dt'
ssl-gnutls.c:513: error: 'dt' undeclared (first use in this function)
ssl-gnutls.c:518: warning: assignment makes pointer from integer without a cast
ssl-gnutls.c: In function 'x509_export_certificate':
ssl-gnutls.c:536: error: 'gnutls_x509_crt_t' undeclared (first use in this function)
ssl-gnutls.c:536: error: expected ';' before 'crt_dat'
ssl-gnutls.c:537: warning: ISO C90 forbids mixed declarations and code
ssl-gnutls.c:548: error: 'crt_dat' undeclared (first use in this function)
ssl-gnutls.c:548: error: 'x509_crtdata_t' has no member named 'crt'
ssl-gnutls.c: In function 'x509_certificate_signed_by':
ssl-gnutls.c:643: error: 'gnutls_x509_crt_t' undeclared (first use in this function)
ssl-gnutls.c:643: error: expected ';' before 'crt_dat'
ssl-gnutls.c:644: error: expected ';' before 'issuer_dat'
ssl-gnutls.c:645: warning: ISO C90 forbids mixed declarations and code
ssl-gnutls.c:657: error: 'crt_dat' undeclared (first use in this function)
ssl-gnutls.c:657: error: 'x509_crtdata_t' has no member named 'crt'
ssl-gnutls.c:658: error: 'issuer_dat' undeclared (first use in this function)
ssl-gnutls.c:658: error: 'x509_crtdata_t' has no member named 'crt'
ssl-gnutls.c: In function 'x509_sha1sum':
ssl-gnutls.c:730: error: 'gnutls_x509_crt_t' undeclared (first use in this function)
ssl-gnutls.c:730: error: expected ';' before 'crt_dat'
ssl-gnutls.c:731: warning: ISO C90 forbids mixed declarations and code
ssl-gnutls.c:736: error: 'crt_dat' undeclared (first use in this function)
ssl-gnutls.c:736: error: 'x509_crtdata_t' has no member named 'crt'
ssl-gnutls.c: In function 'x509_cert_dn':
ssl-gnutls.c:757: error: 'gnutls_x509_crt_t' undeclared (first use in this function)
ssl-gnutls.c:757: error: expected ';' before 'cert_dat'
ssl-gnutls.c:758: warning: ISO C90 forbids mixed declarations and code
ssl-gnutls.c:764: error: 'cert_dat' undeclared (first use in this function)
ssl-gnutls.c:764: error: 'x509_crtdata_t' has no member named 'crt'
ssl-gnutls.c: In function 'x509_issuer_dn':
ssl-gnutls.c:787: error: 'gnutls_x509_crt_t' undeclared (first use in this function)
ssl-gnutls.c:787: error: expected ';' before 'cert_dat'
ssl-gnutls.c:788: warning: ISO C90 forbids mixed declarations and code
ssl-gnutls.c:794: error: 'cert_dat' undeclared (first use in this function)
ssl-gnutls.c:794: error: 'x509_crtdata_t' has no member named 'crt'
ssl-gnutls.c: In function 'x509_common_name':
ssl-gnutls.c:818: error: 'gnutls_x509_crt_t' undeclared (first use in this function)
ssl-gnutls.c:818: error: expected ';' before 'cert_dat'
ssl-gnutls.c:819: warning: ISO C90 forbids mixed declarations and code
ssl-gnutls.c:826: error: 'cert_dat' undeclared (first use in this function)
ssl-gnutls.c:826: error: 'x509_crtdata_t' has no member named 'crt'
ssl-gnutls.c: In function 'x509_check_name':
ssl-gnutls.c:858: error: 'gnutls_x509_crt_t' undeclared (first use in this function)
ssl-gnutls.c:858: error: expected ';' before 'crt_dat'
ssl-gnutls.c:864: error: 'crt_dat' undeclared (first use in this function)
ssl-gnutls.c:864: error: 'x509_crtdata_t' has no member named 'crt'
ssl-gnutls.c: In function 'x509_times':
ssl-gnutls.c:876: error: 'gnutls_x509_crt_t' undeclared (first use in this function)
ssl-gnutls.c:876: error: expected ';' before 'crt_dat'
ssl-gnutls.c:878: warning: ISO C90 forbids mixed declarations and code
ssl-gnutls.c:884: error: 'crt_dat' undeclared (first use in this function)
ssl-gnutls.c:884: error: 'x509_crtdata_t' has no member named 'crt'
make[5]: *** [ssl_gnutls_la-ssl-gnutls.lo] Error 1
make[5]: Leaving directory `/home/dave/MyDownloads/pidgin-2.2.0/libpurple/plugins/ssl'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/dave/MyDownloads/pidgin-2.2.0/libpurple/plugins'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/dave/MyDownloads/pidgin-2.2.0/libpurple'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/dave/MyDownloads/pidgin-2.2.0/libpurple'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/dave/MyDownloads/pidgin-2.2.0'
make: *** [all] Error 2


let me know if anyone's fixed (or got passed) this somehow.  thanks!

--db

---

### Post by Chang An on 2007-09-15
They still did not fix the QQ protocol.  It still says the password is wrong.

---

### Post by blithen on 2007-09-15
> **Kingsley said:**
> Why don't they ever have a .deb compiled for Ubuntards and lazy people :(?

That is what getdeb.net is for >_>

---

### Post by drFUNK on 2007-09-15
> **chantra said:**
> Hi Guys,
You can find a .deb package for Feisty of pidgin 2.2.0 on my repo [http://repository.debuntu.org]("http://repository.debuntu.org"), it is a port of the gutsy package.

Thanks! This star is for you: :KS

---

### Post by blithen on 2007-09-15
> **chantra said:**
> Hi Guys,
You can find a .deb package for Feisty of pidgin 2.2.0 on my repo [http://repository.debuntu.org]("http://repository.debuntu.org"), it is a port of the gutsy package.

Thanks! This helped, and it updated a few other things. You rock!

---

### Post by FuturePilot on 2007-09-15
I hope this update doesn't break anything
system-config-lvm 1.1.1
Anyone have any problems?

---

### Post by blithen on 2007-09-15
> **FuturePilot said:**
> I hope this update doesn't break anything
system-config-lvm 1.1.1
Anyone have any problems?
With pidgin?
Or the dudes repo site?
I have no problems with both.

---

### Post by FuturePilot on 2007-09-15
> **blithen said:**
> With pidgin?
Or the dudes repo site?
I have no problems with both.

I added that repo and it wanted to update system-config-lvm 1.1.1. 
I don't know, but it sounds pretty low in the system. How about after a reboot?

---

### Post by blithen on 2007-09-15
No problems still.
I think the dude is legit.

---

### Post by FuturePilot on 2007-09-15
Lol Never mind. I got it all sorted out. It's all good now. Thanks for the repo chantra!:D

I don't even have system-config-lvm installed:lolflag: :-s

Whoohoo Pidgin 2.2.0\\:D/

---

### Post by blithen on 2007-09-15
> **FuturePilot said:**
> Lol Never mind. I got it all sorted out. It's all good now. Thanks for the repo chantra!:D

I don't even have system-config-lvm installed:lolflag: :-s

Whoohoo Pidgin 2.2.0\\:D/
>_> xD!

---

### Post by bluehue on 2007-09-15
It installed fine but when I click on my e-mail account to activate it I get the following error:
```

SSL support is needed for MSN. Please install a supported SSL library.

Pidgin will not attempt to reconnect the account until you correct the error and re-enable the account.

```
Any ideas how to fix this?

---

### Post by ryno519 on 2007-09-15
> **bluehue said:**
> It installed fine but when I click on my e-mail account to activate it I get the following error:
```

SSL support is needed for MSN. Please install a supported SSL library.

Pidgin will not attempt to reconnect the account until you correct the error and re-enable the account.

```
Any ideas how to fix this?

You need to install an NSS library and recompile it. Alternatively you can just use the .deb listed above.

---

### Post by transatlant1c on 2007-09-16
> **Kosimo said:**
> [http://www.pidgin.im/](http://www.pidgin.im/)

Very easy to install:

Download the source code:

Then:


It takes some time to compile.

Enjoy!

Your the **** man. Downloaded and compiled perfectly. Works 100% no problems. Thanks a bunch!!

---

### Post by ludavicious on 2007-09-16
Nice work people! Thanks for the guides! :KS Pidgin 2.2.0 is working.

---

### Post by altonbr on 2007-09-16
> **Kingsley said:**
> Why don't they ever have a .deb compiled for Ubuntards and lazy people :(?

That's explained here: [http://developer.pidgin.im/wiki/WhyPackagesExist](http://developer.pidgin.im/wiki/WhyPackagesExist)

Basically it's because few-to-none of their developers use Debian or Ubuntu.

> **Spike-X said:**
> I'm guessing it'll end up in the repos for automatic update too?

Gusty is usually quite good at uploading the newest software, but as this thread says: [http://ubuntuforums.org/showthread.php?t=551105](http://ubuntuforums.org/showthread.php?t=551105), we're past the UVF.

I've went a step further and followed the FreezeExectionProcess: [https://wiki.ubuntu.com/FreezeExceptionProcess#head-9523bc4076ff011324d67cddc97969ec609618d6](https://wiki.ubuntu.com/FreezeExceptionProcess#head-9523bc4076ff011324d67cddc97969ec609618d6) and uploaded a diffstat, diff for ChangeLog and diff of the whole directory to Launchpad: [https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/139686](https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/139686)

If this doesn't help, I don't know what will.

---

### Post by bigbrovar on 2007-09-16
i eventaully was able to compile and install it and everything worked fine till i enabled the musictracker plugin now pidgin just freezes everytime i start and i have to forcefully shut it down...the painfull thing is that i cant even disable the musictranker plugin which i suspect is the cus of the problem. :(




But does that mean that musictracker wont work with this version of pidgin  anybody experiencing similar problems or is there something am not doing right

---

### Post by Kosimo on 2007-09-16
Hey guys, 
already available at [http://www.getdeb.net/](http://www.getdeb.net/)  

just download the two debs (and install first data one)

Don't forget to uninstall any older version.

---

### Post by Gremlinzzz on 2007-09-16
> **Kosimo said:**
> Hey guys, 
already available at [http://www.getdeb.net/](http://www.getdeb.net/)  

just download the two debs (and install first data one)

Don't forget to uninstall any older version.

Thanks worked :guitar:

---

### Post by bluehue on 2007-09-17
> **ryno519 said:**
> You need to install an NSS library and recompile it. Alternatively you can just use the .deb listed above.Thanks! 

For any one having this same issue with SSL and MSN, remove your current Pidgin installation and do the following:
```

sudo apt-get install libnss-dev libnspr-dev

```Then reinstall Pidgin and it should work :)

---

### Post by chantra on 2007-09-17
> **FuturePilot said:**
> I added that repo and it wanted to update system-config-lvm 1.1.1. 
I don't know, but it sounds pretty low in the system. How about after a reboot?

Weird, if it was upgraded, it means that you had the package already there.
grep system-config-lvm /var/log/dpkg.log
should reveal a former installed package.

---

### Post by ryno519 on 2007-09-17
Quick question for those who installed from source. Is the spellchecking feature working for you?

---

### Post by OisinT on 2007-09-19
hm... what does this mean?

```
configure: error:

You must have libxml2 >= 2.6.0 development headers installed to build.

oisint@OisinT1:~/Desktop/pidgin-2.2.0$ make
make: *** No targets specified and no makefile found.  Stop.
oisint@OisinT1:~/Desktop/pidgin-2.2.0$ sudo make install
make: *** No rule to make target `install'.  Stop.
oisint@OisinT1:~/Desktop/pidgin-2.2.0$ 

```

---

### Post by akudewan on 2007-09-19
> **dbloom said:**
> anyone having trouble compiling v2.2.0?  i've compiling it myself since the first version, but now i'm getting an error with ssl-gnutls.c.  see below.



let me know if anyone's fixed (or got passed) this somehow.  thanks!

--db
I'm having a similar problem. Have anyone found a fix ?

---

### Post by macogw on 2007-09-19
Don't use the one from getdeb.net.  Compile it.  The getdeb ones are not built properly, in my experience.  I had Pidgin eating >700mb within 5 seconds of starting last week using GetDeb's, but I compiled it and it's fine.

To get all the dependencies, do "sudo apt-get build-dep gaim"

---

### Post by Samuelh3 on 2007-09-19
I originally installed pidgin 2.2 and using the compiled method. I am very new to Linux and would like to uninstall it. How do I do this?

Thanks,

SH

Nevermind I figured it out.

---

### Post by derekr44 on 2007-09-19
> **Kingsley said:**
> Why don't they ever have a .deb compiled for Ubuntards and lazy people :(?

That is so me :lolflag:

---

### Post by Luffield on 2007-09-19
Version 2.20 is in the Gutsy repositories now.

---

### Post by chantra on 2007-09-20
> **Samuelh3 said:**
> I originally installed pidgin 2.2 and using the compiled method. I am very new to Linux and would like to uninstall it. How do I do this?

Thanks,

SH

Nevermind I figured it out.

If you still have the directory where you compile the source, "cd" back there and run:
$sudo make uninstall

Hope this helps

---

### Post by altonbr on 2007-09-20
> **derekr44 said:**
> That is so me :lolflag:

[http://ubuntuforums.org/showpost.php?p=3374986&postcount=42](http://ubuntuforums.org/showpost.php?p=3374986&postcount=42)

---

### Post by wersdaluv on 2007-09-20
[http://repository.debuntu.org/#howtouse](http://repository.debuntu.org/#howtouse)

---

### Post by Neo4 on 2007-09-20
I've just installed pidgin 2.2.0 and missed two things:

change the font and color of the conversation

and show my picture and my friend's (big size not that tiny pic on the top of the window)

it is possible to change this?

thanks

---

### Post by altonbr on 2007-09-21
> **Neo4 said:**
> I've just installed pidgin 2.2.0 and missed two things:

change the font and color con conversation

and sow my picture and my friend's (big size not that tiny pic on the top of the window)

it is possible to change this?

thanks

That tiny pic problem is a huge complaint from the community as they've changed it in 2.1.x and 2.2.x. I've tried to make a ticket here:[http://developer.pidgin.im/ticket/3135](http://developer.pidgin.im/ticket/3135) and I'm open to your suggestions.

The other two sound like build problems. Are you using the official Gusty version or GetDeb's?

---

### Post by hanzomon4 on 2007-09-21
Great, MySpace IM support!!!

Now I can IM all my folks that only use myspace

---

### Post by Neo4 on 2007-09-21
> **altonbr said:**
> That tiny pic problem is a huge complaint from the community as they've changed it in 2.1.x and 2.2.x. I've tried to make a ticket here:[http://developer.pidgin.im/ticket/3135](http://developer.pidgin.im/ticket/3135) and I'm open to your suggestions.

The other two sound like build problems. Are you using the official Gusty version or GetDeb's?

no i'm using the getdeb's I don't have ubuntu gusty but still feisty. But now I can change the color and font after reinstall pidgin.

Thanks for the help

---

### Post by dietrying on 2007-09-21
is anyone able to send filetransfers to psi or other jabber clients without tweaking? It doesn't happen on my system......with gajim it is no problem.....i will have to use both clients until this is fixed. If there is a good solution for this, please tell me.....

---

### Post by bruce89 on 2007-09-21
Just use pbuilder to backport stuff. Once PPAs are non-beta, I'll backport stuff that I use.

---

### Post by stalker145 on 2007-09-21
WOOT!!

MySpace IM :)

---

### Post by Shaggmire on 2007-09-21
> **ryno519 said:**
> If you have some trouble with the ./configure not finding all of the dependencies, try this.



That should do it.

ok, now what? it said it installed but i cant find it anywhere

---

### Post by ryno519 on 2007-09-21
> **Shaggmire said:**
> ok, now what? it said it installed but i cant find it anywhere

Should be able running it by simply typing pidgin into the command line. It should have added it to the menu under the internet submenu as well.

---

### Post by OisinT on 2007-09-23
> **OisinT said:**
> hm... what does this mean?

```
configure: error:

You must have libxml2 >= 2.6.0 development headers installed to build.

oisint@OisinT1:~/Desktop/pidgin-2.2.0$ make
make: *** No targets specified and no makefile found.  Stop.
oisint@OisinT1:~/Desktop/pidgin-2.2.0$ sudo make install
make: *** No rule to make target `install'.  Stop.
oisint@OisinT1:~/Desktop/pidgin-2.2.0$ 

```


I'm still having this problem... anyone?

---

### Post by dhega on 2007-09-23
well i have tried pidgin and (gaim)
many many times, and everytime i think that they should have done something about the crappy filetransfers, but NOTHING has happened for years?

I mean in AMSN it works flawlessy, but in pigdin its so crappy i can not even use it!


So, whats the deal? will this never be improved? Cause if thats the case im not going to use it .

---

### Post by bruce89 on 2007-09-23
> **dhega said:**
> So, whats the deal? will this never be improved? Cause if thats the case im not going to use it .

IF THEY DON'T IMPLEMENT MY FEATURE NOW, I'M LEAVING posts are not good.

Implement it youself, it'd be fairly straightforward to see how AMSN do it.

---

### Post by dhega on 2007-09-23
yea i was tired and such when i wrote that post.

But i cannot implement it myself!

I just wonder, since there are alot of people using pidgin!
Are you not concerned about filetransfers at all?

---

### Post by bruce89 on 2007-09-23
> **dhega said:**
> yea i was tired and such when i wrote that post.

But i cannot implement it myself!

I just wonder, since there are alot of people using pidgin!
Are you not concerned about filetransfers at all?

Some people are, but it's not up to me.

---

### Post by zanglang on 2007-09-24
> **OisinT said:**
> I'm still having this problem... anyone?

For this error you're just missing *libxml2-dev*. Just do 'sudo apt-get build-dep pidgin' to install all development headers necessary for Pidgin.

---

### Post by zanglang on 2007-09-24
> **dhega said:**
> well i have tried pidgin and (gaim)
many many times, and everytime i think that they should have done something about the crappy filetransfers, but NOTHING has happened for years?

I mean in AMSN it works flawlessy, but in pigdin its so crappy i can not even use it!


So, whats the deal? will this never be improved? Cause if thats the case im not going to use it .

Well, how is it not working? What is your network setup, as well as the recipient's? Are the file transfers going through firewalls in either direction? Were there any debug message errors when you try to do so? If it works for others, what exactly is making yours not work?

If you'd really like to see it fixed, bring it up to the Pidgin developers' attention, be cooperative and provide as much info as possible. Even if you're unable to contribute code to the situation, simply complaining in a small forum thread where no Pidgin developer is bound to read will not cause anything to happen at all.

---

### Post by WishMaster on 2007-09-24
MSNP14 is supported now (according to the completed milestone).
Anyone has a .deb with the updated/working MSN protocol?

---

### Post by tombott on 2007-09-24
> **macogw said:**
> Don't use the one from getdeb.net.  Compile it.  The getdeb ones are not built properly, in my experience.  I had Pidgin eating >700mb within 5 seconds of starting last week using GetDeb's, but I compiled it and it's fine.

To get all the dependencies, do "sudo apt-get build-dep gaim"

I don't think it's very helpful to make a statement like that, certainly discuss your problems but to say 'Don't use the one from getdeb.net' isn't useful!

You might want too look at the setup of your machine.

I have installed the .deb from getdeb.net on 4 different machines without any problems at all.

---

### Post by stalker145 on 2007-09-24
> **macogw said:**
> Don't use the one from getdeb.net.  Compile it.  The getdeb ones are not built properly, in my experience.  I had Pidgin eating >700mb within 5 seconds of starting last week using GetDeb's, but I compiled it and it's fine.

To get all the dependencies, do "sudo apt-get build-dep gaim"

> **tombott said:**
> I don't think it's very helpful to make a statement like that, certainly discuss your problems but to say 'Don't use the one from getdeb.net' isn't useful!

You might want too look at the setup of your machine.

I have installed the .deb from getdeb.net on 4 different machines without any problems at all.

I have to agree with tombott that this falls into the YMMV category. I installed the most recent version from getdeb two days ago (*just* before my last post) and the only issue that I've had with it is staying off IM ;)

I have done file transfers and direct IM on AIM and chatted on MySpace and Yahoo. Everything that I need it for works... so far.

I'm sorry if it doesn't work for you, macogw. I am glad, though, that you found a solution.

---

### Post by Polygon on 2007-09-24
i compiled pidgin myself and yesterday i was talking to a guy on msn , and pidgin crashed about 10 times in a two hour period. I think this might be a bug however....

and i have had no problems with getdeb packages, i have several of them installed

---

