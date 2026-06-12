---
title: "No Breezy Backports yet?  Wonder why..."
date: 2005-10-28
forum: Ubuntu Backports
---

### Post by TheDocMan on 2005-10-28
It came across my mind that ... if the backports project would have not gone "official" and stayed indepentant, would we still be waiting for it to start back up for breezy?

---

### Post by tzutolin on 2005-10-28
[QUOTE=TheDocMan]It came across my mind that ... if the backports project would have not gone "official" and stayed indepentant, would we still be waiting for it to start back up for breezy?[/QUOTE]
Yeah, I can't wait to see it :KS

---

### Post by kvidell on 2005-10-28
Backports was a project that took the bleeding-edge packages from what was at the time the development release(s) of Breezy and made the compatible with the, at the time, stable Hoary...

When Dapper Drake goes public in it's development, I'm sure the backports folks will be happy to start up again and make a Dapper->Breezy Backports project. (There may be some chatter about it here[[1](http://ubuntuforums.org/forumdisplay.php?f=47)], but I haven't read up on it myself yet.)

Even if it was an independant project still, they'd need to source from _something_, and that something would have to be the Dapper Repositories.
- Kev

[1]: [http://ubuntuforums.org/forumdisplay.php?f=47](http://ubuntuforums.org/forumdisplay.php?f=47)

---

### Post by Seth on 2005-10-28
Dapper has very few new packages at this point. If you want something that's already in Dapper I'd be happy to build it for you :)

---

### Post by Kyral on 2005-10-28
On that note I had to delete my VLC packages because I was running out of Webspace. Seth you mind hosting them for me? I also built the Mono that someone requested.

(Just like yours, Dapper sources + Breezy PBuilder. Damn I love PBuilder :D)

---

### Post by Pablo_Escobar on 2005-10-28
IMO if someone is so eager to get bleeding edge, why not to compile it Yourself ?
If I want to have some new version of app I just download the source code, neccesary dev packages and get to compiling.

---

### Post by TheDocMan on 2005-10-28
No, I'm not that in need of the bleeding edge packages that I'm whining about it.  I'm just curious.  And anyhow, I had thought originally that some of the backports were taking from debian unstable and testing, not just the "next" version of ubuntu, which probably does have newer versions of some of the packages.

---

### Post by kvidell on 2005-10-29
[QUOTE=TheDocMan]No, I'm not that in need of the bleeding edge packages that I'm whining about it.  I'm just curious.  And anyhow, I had thought originally that some of the backports were taking from debian unstable and testing, not just the "next" version of ubuntu, which probably does have newer versions of some of the packages.[/QUOTE]
Probably? :-P That's the whole point of doing a next version :-P
It has all the latest happy packages.
- Kev

---

### Post by MetalMusicAddict on 2005-10-29
[QUOTE=TheDocMan]It came across my mind that ... if the backports project would have not gone "official" and stayed indepentant, would we still be waiting for it to start back up for breezy?[/QUOTE]
If you had searched the fourms 1st you would have had the answers to your questions. ;)

---

### Post by rdenatale on 2005-11-07
[QUOTE=Seth]Dapper has very few new packages at this point. If you want something that's already in Dapper I'd be happy to build it for you :)[/QUOTE]
Well, I think that one thing that needs to be backported to Breezy is the REAL openoffice2. 

The official oo2 came out not long AFTER breezy was released. So Breezy is still on the 1.9.129 stream.

I'm trying to cope right now with an OO2 crash when I try to delete a record from the bibliography database. I THINK it got fixed in the official OO2 release.

I think that the breezy oo2 is more on the bleeding edge than it should be, it got released with blood still on the knife.

---

### Post by linbetwin on 2005-11-07
[quote=Seth]Dapper has very few new packages at this point. If you want something that's already in Dapper I'd be happy to build it for you :)[/quote]
 
I dist-upgraded to Dapper hoping to find a new Gnopernicus magnifier. The one in Breezy is not very useful and that's the main reason I can't switch to Ubuntu and still use XP as my main OS. But I didn't find Gnopernicus 0.12 in the Dapper repos.
 
Seth, I would be very grateful if you could build Gnopernicus version 0.12 for me! It's on [gnome]("ftp://ftp.gnome.org/mirror/gnome.org/sources/gnopernicus/0.12/") ftp. [Gnome-mag]("ftp://ftp.gnome.org/mirror/gnome.org/sources/gnome-mag/0.12/") is a dependency. Thank you.
 
I posted a [thread]("http://ubuntuforums.org/showthread.php?t=86436") about this a while ago.

---

### Post by Seth on 2005-11-07
As stated in Backports guidelines, only packages that are in an Ubuntu distro (in this case Dapper) will be backported to an earlier release (Breezy). Sorry.

---

### Post by Seth on 2005-11-07
With regards to OOo2, Doko built it.
[http://ubuntuforums.org/showthread.php?t=83308]("http://ubuntuforums.org/showthread.php?t=83308")

---

### Post by rdenatale on 2005-11-07
[QUOTE=Seth]With regards to OOo2, Doko built it.
[http://ubuntuforums.org/showthread.php?t=83308]("http://ubuntuforums.org/showthread.php?t=83308")[/QUOTE]
Well, I tried to follow that thread and I can't seem to get it to work.

There were several requests for a deb line which actually works and I never saw a reply.  The repository doesn't seem to be set up with a distribution or sections.  Synaptic doesn't seem to like it.

---

### Post by jetpeach on 2005-11-07
I would also like a simpler way (preferably with backports) to change to the stable release of OO2.  I'm unconfortable using the release canditate when there is the final version out...

---

### Post by duffman25 on 2005-11-08
[QUOTE=rdenatale]Well, I tried to follow that thread and I can't seem to get it to work.

There were several requests for a deb line which actually works and I never saw a reply.  The repository doesn't seem to be set up with a distribution or sections.  Synaptic doesn't seem to like it.[/QUOTE]

I've correctly upgraded both a 386 & amd64 machine with doko's ooo2 repo & I'm running the final version. In that thread there are 2 ways of doing the upgrade, I used the indications of adding the doko repo & all went fine. BTW the packages seem to be perfectly stable for me & the final version of 002 appears to be more stable, so I think it's worth the upgrade. If you want I can help you with the procedure.

---

### Post by jBilbo on 2005-11-08
[QUOTE=Seth]Dapper has very few new packages at this point. If you want something that's already in Dapper I'd be happy to build it for you :)[/QUOTE]

Would be great a avidemux backport from dapper :D

---

### Post by rdenatale on 2005-11-08
[QUOTE=duffman25]I've correctly upgraded both a 386 & amd64 machine with doko's ooo2 repo & I'm running the final version. In that thread there are 2 ways of doing the upgrade, I used the indications of adding the doko repo & all went fine. BTW the packages seem to be perfectly stable for me & the final version of 002 appears to be more stable, so I think it's worth the upgrade. If you want I can help you with the procedure.[/QUOTE]

Please do. This response is much like the others I found in the thread. Several people seemed to have problems, while others said, "it worked for me."  What was the exact deb line you put into synaptic to make it work. 

I'd still really like to see this in an official backports repository. I'm not very happy just throwing in repositories willy nilly, for fear of problems down the road.

---

### Post by Seth on 2005-11-08
OOo2 should hit backports when they open. I have my suspicions about why they haven't yet, but I'll keep them to myself.

This line worked for me when I added it directly to /etc/apt/sources.list:

 deb [http://people.ubuntu.com/~doko/OOo2 ./]("http://people.ubuntu.com/%7Edoko/OOo2%20./")

There's a space between OOo2 and ./ :)

Then sudo apt-get update && sudo apt-get upgrade and you've got OOo2 :)

---

### Post by eyebrowman92 on 2005-11-08
this is probably a stupid question but what excactly are backports?

---

### Post by duffman25 on 2005-11-08
[QUOTE=rdenatale]Please do. This response is much like the others I found in the thread. Several people seemed to have problems, while others said, "it worked for me."  What was the exact deb line you put into synaptic to make it work. 

I'd still really like to see this in an official backports repository. I'm not very happy just throwing in repositories willy nilly, for fear of problems down the road.[/QUOTE]

What architecture are you using? x86, amd64 or ppc? The line you add depends on that. Here's what you need to do:

So, first open your sourcer.list:
```

sudo gedit /etc/apt/sources.list

```
secondly, add the appropiate line for ooo2. If you are using a x86 machine (pentium & athlonxp friends) it's this:
```

deb http://people.ubuntu.com/~doko/OOo2 ./

```
for amd64:
```

deb http://people.ubuntu.com/~doko/OOo2-amd64 ./

```
for ppc:
```

deb http://people.ubuntu.com/~doko/OOo2-powerpc ./

```
Then, save the file & update:
```

sudo apt-get update
sudo apt-get dist-upgrade

```
& everything should work.

To see what architecture is yours, do this:
launch a terminal & type:
```

uname -a

```

You'll see a line with something line 386, amd64 which tells you the architecture of the machine. This was taken from this howto:
[http://ubuntuforums.org/showthread.php?t=80392](http://ubuntuforums.org/showthread.php?t=80392)

---

### Post by duffman25 on 2005-11-08
[QUOTE=eyebrowman92]this is probably a stupid question but what excactly are backports?[/QUOTE]
read this:
[http://ubuntuforums.org/showthread.php?t=40291](http://ubuntuforums.org/showthread.php?t=40291)

---

### Post by Seth on 2005-11-08
[QUOTE=jBilbo]Would be great a avidemux backport from dapper :D[/QUOTE]
Here it is for you :)

[http://sethkinast.com/ubuntu/breezy/backports/avidemux_2.0.42-0.0ubuntu3~ubp5.10_i386.deb](http://sethkinast.com/ubuntu/breezy/backports/avidemux_2.0.42-0.0ubuntu3~ubp5.10_i386.deb)

Please test, as I don't have a Breezy machine to test it on.

---

### Post by rdenatale on 2005-11-08
[QUOTE=Seth]OOo2 should hit backports when they open. I have my suspicions about why they haven't yet, but I'll keep them to myself.

This line worked for me when I added it directly to /etc/apt/sources.list:

 deb [http://people.ubuntu.com/~doko/OOo2 ./]("http://people.ubuntu.com/%7Edoko/OOo2%20./")

There's a space between OOo2 and ./ :)

Then sudo apt-get update && sudo apt-get upgrade and you've got OOo2 :)[/QUOTE]

If I put:
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

into my /etc/apt/sources.list, then synaptic blows up when I launch it. with the following messages.

> W: Couldn't stat source package list [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages (/var/lib/apt/lists/people.ubuntu.com_%7edoko_OOo2_._Packages) - stat (2 No such file or directory)

Now for some reason the email version I got from watching this thread had the line as:

deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./ ([http://people.ubuntu.com/%7Edoko/OOo2%20./](http://people.ubuntu.com/%7Edoko/OOo2%20./))

I get > E: Malformed line 35 in source list /etc/apt/sources.list (absolute dist)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

And "unquoting" the ~ and space doesn't make a difference. Not that I expected that it would.

I haven't tried using apt-get from the command line, but I really don't want to put anything in my sources.list which doesn't work with synaptic.

---

### Post by Seth on 2005-11-08
That blowup is because you haven't hit Reload in Synaptic. That's all. And use the first version (the one I posted), not the weird parenthetical. That's not valid apt syntax.

This is why it's easier to just type sudo apt-get update && sudo apt-get upgrade. Forget Synaptic for stuff like this. Synaptic is great for searching for things to install, but for upgrades or installing single package, learn to use apt-get. It's simple, quick, and easy.

---

### Post by rdenatale on 2005-11-08
[QUOTE=Seth]That blowup is because you haven't hit Reload in Synaptic. That's all. And use the first version (the one I posted), not the weird parenthetical. That's not valid apt syntax.

This is why it's easier to just type sudo apt-get update && sudo apt-get upgrade. Forget Synaptic for stuff like this. Synaptic is great for searching for things to install, but for upgrades or installing single package, learn to use apt-get. It's simple, quick, and easy.[/QUOTE]

Thanks, that seems to work.

I'm not against using apt-get, it's just that I tend to be careful about setting up repositorys. Maybe it's because I'm a recent convert from Redhat/Fedora, and have gotten burned by the RPM 'port' of apt-get in the past.

---

### Post by jdong on 2005-11-08
Official Breezy Backports still needs porting work at the server side (archive.ubuntu.com) that is **completely out of my control**. Since everyone's partying and busy at UBZ, it'll be a bit before the architecture would be ready. Already, there are 5 or so packages queued for backporting.


Sorry for the wait.

---

### Post by duffman25 on 2005-11-08
[QUOTE=jdong]Official Breezy Backports still needs porting work at the server side (archive.ubuntu.com) that is **completely out of my control**. Since everyone's partying and busy at UBZ, it'll be a bit before the architecture would be ready. Already, there are 5 or so packages queued for backporting.


Sorry for the wait.[/QUOTE]
Ok, no problem jdong, we appreciate your efforts. One thing, if there's so much trouble with the porting work in the server side maybe it would be wise for you to discuss this issues once mark & the rest of dev's come from ubz so for dapper this kind of problems won't happen again, what do you think?

---

### Post by jdong on 2005-11-08
Yes, this definitely needs to be discussed. During the last month of Breezy development, I was reassured time and time again that breezy-backports would be available as soon as Dapper opened. However, nearly a month has passed and there still isn't a breezy-backports branch.

I truly hope its is just a one-time fluke... I could just open up another Mirrormax tree, but the last thing I want to do is piss off every Ubuntu developer again :)

---

### Post by `GooZ´ on 2005-11-08
Thanks alot for the info, jdong. I hope they will be up soon :)

---

### Post by loon on 2005-11-08
[QUOTE=jdong]Yes, this definitely needs to be discussed. During the last month of Breezy development, I was reassured time and time again that breezy-backports would be available as soon as Dapper opened. However, nearly a month has passed and there still isn't a breezy-backports branch.

I truly hope its is just a one-time fluke... I could just open up another Mirrormax tree, but the last thing I want to do is piss off every Ubuntu developer again :)[/QUOTE]

Piss off every Ubuntu developer for "partying" and leaving us hung out to dry.

Or make every Ubuntu user happy?? hhrrrmmm...

---

### Post by jdong on 2005-11-08
Partying is a very broad term with many different meanings. I'm not downplaying on the importance of UBZ.... I'm just saying it's taking precedence over everything else.

From past experience, I've learned that maintaining simultaneous repos is a recipe for disaster. If you badly badly need a package to be backported, feel free to do it for yourself... Nobody's stopping you from doing that.

---

### Post by jBilbo on 2005-11-08
[QUOTE=Seth]Here it is for you :)

[http://sethkinast.com/ubuntu/breezy/backports/avidemux_2.0.42-0.0ubuntu3~ubp5.10_i386.deb](http://sethkinast.com/ubuntu/breezy/backports/avidemux_2.0.42-0.0ubuntu3~ubp5.10_i386.deb)

Please test, as I don't have a Breezy machine to test it on.[/QUOTE]

Wow thank you very much!, you're fast... really fast :D :KS 

I tested it and seems to run fine, i'll continuing testing in next hours/days and report any issue :)

---

### Post by Seth on 2005-11-08
I'm glad I could help you :) Please don't hesitate to ask for something else to be backported until the real thing opens. (Although my packages are backported to spec and so are perfectly safe to use, even before the real backports open.)

---

### Post by jdong on 2005-11-08
Seth, careful with your naming convention... The current ones won't act properly with official Backports. Currently, we use ~breezy1 trailers, so using ~breezy0.1, 0.2, and so on would be considered safe for unofficial builds.

---

### Post by Seth on 2005-11-08
I must've not gotten the memo on that changing from ~5.10. Thanks, will do that in the future.

---

