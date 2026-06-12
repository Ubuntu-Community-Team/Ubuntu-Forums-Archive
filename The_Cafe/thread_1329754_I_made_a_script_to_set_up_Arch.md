---
title: "I made a script to set up Arch"
date: 2009-11-17
forum: The Cafe
---

### Post by thegreenblob on 2009-11-17
I made a script that sets up Arch Linux to a basic openbox setup from a base install, and thought I'd share it.

I mainly made it cause I was bored the other day and needed something to do, but I also plan on using it on my desktop when I reinstall because I've sorta got a ton of clutter on it and reinstalling is an easy way to get rid of it. :P

Basically to use it what you do is, install Arch, but don't make a user account or anything, and then get the script on there via the internet or a flash drive, make sure you have a working internet connection, and at least one pacman server uncommented, and then run,

```
chmod +x /location/of/script.sh
and then
./script.sh
```

And then you'll be asked a few questions but for the most part it does things automatically.

And you'll probably have to either modify the script to install your video driver or do it after it's done since it only installs the generic vesa driver.

So yeah that's about it. The script and screenshots are attached, feel free to comment, make a suggestion, ask a question or use the script if you like.

Oh and for anyone wondering why I didn't post this on an Arch forum, it's because, well... I'm not a member there, I'm already a member here, and there's a lot of Arch users here too :P lol. But if anyone wants too they can post it over there.

---

### Post by markp1989 on 2009-11-17
> **thegreenblob said:**
> I made a script that sets up Arch Linux to a basic openbox setup from a base install, and thought I'd share it.

I mainly made it cause I was bored the other day and needed something to do, but I also plan on using it on my desktop when I reinstall because I've sorta got a ton of clutter on it and reinstalling is an easy way to get rid of it. :P

Basically to use it what you do is, install Arch, but don't make a user account or anything, and then get the script on there via the internet or a flash drive, make sure you have a working internet connection, and at least one pacman server uncommented, and then run,

```
chmod +x /location/of/script.sh
and then
./script.sh
```

And then you'll be asked a few questions but for the most part it does things automatically.

And you'll probably have to either modify the script to install your video driver or do it after it's done since it only installs the generic vesa driver.

So yeah that's about it. The script and screenshots are attached, feel free to comment, make a suggestion, ask a question or use the script if you like.

Oh and for anyone wondering why I didn't post this on an Arch forum, it's because, well... I'm not a member there, I'm already a member here, and there's a lot of Arch users here too :P lol. But if anyone wants too they can post it over there.

i havnt got time to test the install tonight, but somtime tomorrow i will give it a go in a virtual pc, sounds good. i have got a working arch already but this sounds like it would be usefull.

---

### Post by adsinclair on 2009-11-17
Very nice! I will give it a try.

---

### Post by Sealbhach on 2009-11-17
Looks good, but how would I get it into my Arch system so I could run it? wget it from somewhere or off a USB or something?

.

---

### Post by markp1989 on 2009-11-17
> **Sealbhach said:**
> Looks good, but how would I get it into my Arch system so I could run it? wget it from somewhere or off a USB or something?

.

i do all my installs from a usb stick, so i was just gona stick the script on the usb drive with the rest of the install files.

---

### Post by thegreenblob on 2009-11-17
> **Sealbhach said:**
> Looks good, but how would I get it into my Arch system so I could run it? wget it from somewhere or off a USB or something?

.

Yeah, a flash drive, wgetting from somewhere, external hard drive, using ssh/sftp to get it off another machine, etc. Plenty of ways.

---

### Post by sisco311 on 2009-11-17
> **Sealbhach said:**
> Looks good, but how would I get it into my Arch system so I could run it? wget it from somewhere or off a USB or something?

.

Do you format all the partitions when are doing a fresh install?

---

### Post by -grubby on 2009-11-17
I decided to host it: [http://static.nathangrubb.org/openboxarch.sh](http://static.nathangrubb.org/openboxarch.sh)

---

### Post by thegreenblob on 2009-11-17
> **-grubby said:**
> I decided to host it: [http://static.nathangrubb.org/openboxarch.sh](http://static.nathangrubb.org/openboxarch.sh)

Ah, nice. Now people can just wget it.

Thanks for hosting it. :popcorn:

---

### Post by Sealbhach on 2009-11-17
> **sisco311 said:**
> Do you format all the partitions when are doing a fresh install?

No, usually just / and use /home but not format it.

.

---

### Post by sisco311 on 2009-11-17
> **Sealbhach said:**
> No, usually just / and use /home but not format it.

.

then download the script to your /home partition.

if you wget it from the net, read the script before you run it. ;)

---

### Post by phrostbyte on 2009-11-17
you can replace your two if statements with this:

```

if [[ "$REPLY" =~ ^[yY] ]]; then

```


Anyway I love this idea, I was planning to make something some similar but I am inexperienced with Arch. Perhaps this can be made into a script with many installation targets. :)

You might want to add some error checking, I think if they just hit ENTER when they put in a username it will still go ahead and install.

---

### Post by thegreenblob on 2009-11-17
> **phrostbyte said:**
> you can replace your two if statements with this:

```

if [[ "$REPLY" =~ ^[yY] ]]; then

```

Good call. I'll replace it with that.

> **phrostbyte said:**
> Anyway I love this idea, I was planning to make something some similar but I am inexperienced with Arch. Perhaps this can be made into a script with many installation targets. :)

Yeah, shouldn't be too hard.

> **phrostbyte said:**
> You might want to add some error checking, I think if they just hit ENTER when they put in a username it will still go ahead and install.

That's why I added the, ```
setterm -blank 0
``` at the top. As far as actual error checking goes, I'm not really sure how to implement that. ](*,)

---

### Post by thegreenblob on 2009-11-18
> **thegreenblob said:**
> As far as actual error checking goes, I'm not really sure how to implement that. ](*,)

Spoke a little too soon. Thought of a simple way to prevent people from putting in blank usernames. Script updated.

```
echo "What do you want your username to be?"
echo ""
read -p "> "
if [ "$REPLY" == '' ]; then
    echo "You did not type in a username. Please run the script again but this"
    echo "time type in a username as it is essential for the script to complete"
    echo "properly."
    exit;
else
    USERNAME=$REPLY;
fi
```

:)

---

### Post by gn2 on 2009-11-18
Did you post this in the Arch forums?

---

### Post by ~sHyLoCk~ on 2009-11-18
> **gn2 said:**
> Did you post this in the Arch forums?

I don't think his script will be well-received in the Arch forum. However, go ahead post it in the community contribution if you like. ;)
Good effort though.

---

### Post by gn2 on 2009-11-18
> **~sHyLoCk~ said:**
> I don't think his script will be well-received in the Arch forum. 

That's what I was wondering, whether it was perceived as heresy over there or not.

---

### Post by RiceMonster on 2009-11-18
> **thegreenblob said:**
> Spoke a little too soon. Thought of a simple way to prevent people from putting in blank usernames. Script updated.

```
echo "What do you want your username to be?"
echo ""
read -p "> "
if [ "$REPLY" == '' ]; then
    echo "You did not type in a username. Please run the script again but this"
    echo "time type in a username as it is essential for the script to complete"
    echo "properly."
    exit;
else
    USERNAME=$REPLY;
fi
```

:)

Instead of doing 
```
if [ "$REPLY" == ''];
```

I'd do 
```
if [ -z "$REPLY" ];
```

Also, you didn't need to write echo again for that line break. Just do it like this:
```
echo -e "time type in a username as it is essential for the script to complete\nproperly"
```

Just being a bit picky ;)

---

### Post by john_spiral on 2009-11-18
Would be nice to have a choice of D.E, enlightenment(e16/e17)/LXDE/fluxbox....

---

### Post by alphaniner on 2009-11-18
> **john_spiral said:**
> Would be nice to have a choice of D.E, enlightenment(e16/e17)/LXDE/fluxbox....

[IMG]http://whatitslikeontheinside.com/uploaded_images/Make-It-So-776665.jpg[/IMG]

---

### Post by john_spiral on 2009-11-18
that made me laugh!

I was being cheeky

---

### Post by alphaniner on 2009-11-18
Picardisms are always good for a laugh.

---

### Post by phrostbyte on 2009-11-18
> **thegreenblob said:**
> Spoke a little too soon. Thought of a simple way to prevent people from putting in blank usernames. Script updated.

```
echo "What do you want your username to be?"
echo ""
read -p "> "
if [ "$REPLY" == '' ]; then
    echo "You did not type in a username. Please run the script again but this"
    echo "time type in a username as it is essential for the script to complete"
    echo "properly."
    exit;
else
    USERNAME=$REPLY;
fi
```

:)

You can do something like

```

read -p "> "
while [[ -z "$REPLY" ]]; do
   echo "error: no username entered"
   read -p "> "
done

```

That should make if they just hit ENTER it re-prompts them until they type something.

---

### Post by thegreenblob on 2009-11-18
> **gn2 said:**
> Did you post this in the Arch forums?
> **~sHyLoCk~ said:**
> I don't think his script will be well-received in the Arch forum. However, go ahead post it in the community contribution if you like. ;)
Good effort though.
> **gn2 said:**
> That's what I was wondering, whether it was perceived as heresy over there or not.

I wasn't going to simply because I wasn't a member, but now you guys got me kinda scared to. :-\" lol

> **RiceMonster said:**
> Also, you didn't need to write echo again for that line break. Just do it like this:

Just being a bit picky ;)

I like using seperate lines better. Makes it easier to read while writing it. At least IMO. But thanks. :)

> **phrostbyte said:**
> You can do something like

```

read -p "> "
while [[ -z "$REPLY" ]]; do
   echo "error: no username entered"
   read -p "> "
done

```

That should make if they just hit ENTER it re-prompts them until they type something.

Oh wow, that's awesome. I can't believe I've never heard of "while" before. :o, going to update the script with this, thanks!

---

### Post by earthpigg on 2009-11-18
love the idea. posting in this thread so i can find it in the future if i need it.

you should try getting it in the AUR.

---

### Post by handy on 2009-11-19
I too think that it is great effort, & good fun for scripters.

Though personally I'd rather use the standard installation method, as I quite enjoy it.

---

### Post by ~sHyLoCk~ on 2009-11-19
> **thegreenblob said:**
> I wasn't going to simply because I wasn't a member, but now you guys got me kinda scared to. :-\" lol

Don't listen to me, go ahead and share your knowledge.

Good luck:popcorn:

---

### Post by pwnst*r on 2009-11-19
damn, nice work!

---

### Post by LookTJ on 2009-11-19
> **earthpigg said:**
> 

you should try getting it in the AUR.
I'll be happy to put in a PKGBUILD file., just need a webhost volunteer :P, I wouldn't mind hosting it myself, but I wouldn't guarantee uptime. I turn my pc off so I can sleep(in my room).

---

### Post by gn2 on 2009-11-19
Open a Skydrive account and host it there for free?

[http://skydrive.live.com/](http://skydrive.live.com/)

---

### Post by LookTJ on 2009-11-19
> **gn2 said:**
> Open a Skydrive account and host it there for free?

[http://skydrive.live.com/](http://skydrive.live.com/)
Already have one through my edu address, we could make files public? I have to check and report back. :)

---

### Post by thegreenblob on 2009-11-22
> **LookTJ said:**
> I'll be happy to put in a PKGBUILD file., just need a webhost volunteer :P, I wouldn't mind hosting it myself, but I wouldn't guarantee uptime. I turn my pc off so I can sleep(in my room).

This should work.

[http://openboxarch.110mb.com/openboxarch.sh](http://openboxarch.110mb.com/openboxarch.sh)

---

### Post by Pasdar on 2009-11-22
> **thegreenblob said:**
> This should work.

[http://openboxarch.110mb.com/openboxarch.sh](http://openboxarch.110mb.com/openboxarch.sh)

Great scripts. There is quite some redundancy, but it doesn't matter in this case, since you'll only use it once anyway. Other than that its a great thing that can be edited by lazy people like me to suite my own preferences. (Installing KDE and programs I like).

Thx! :KS

---

### Post by kaivalagi on 2009-11-23
> **LookTJ said:**
> I'll be happy to put in a PKGBUILD file., just need a webhost volunteer :P, I wouldn't mind hosting it myself, but I wouldn't guarantee uptime. I turn my pc off so I can sleep(in my room).

Already hosted at post 8 by -grubby: [http://ubuntuforums.org/showpost.php?p=8338141&postcount=8](http://ubuntuforums.org/showpost.php?p=8338141&postcount=8)

You could always put the script into the AUR package...I think (new to Arch and AUR PKGBUILDs :) )

---

### Post by thegreenblob on 2009-11-23
> **Pasdar said:**
> Great scripts. There is quite some redundancy, but it doesn't matter in this case, since you'll only use it once anyway. Other than that its a great thing that can be edited by lazy people like me to suite my own preferences. (Installing KDE and programs I like).

Thx! :KS

You're welcome. :popcorn: 

> **kaivalagi said:**
> Already hosted at post 8 by -grubby: [http://ubuntuforums.org/showpost.php?p=8338141&postcount=8](http://ubuntuforums.org/showpost.php?p=8338141&postcount=8)

You could always put the script into the AUR package...I think (new to Arch and AUR PKGBUILDs :) )

Yeah but it's been updated twice, so I thought it'd be easier to just host it on a free 110mb account so I can update it right away.

And if anyone cares or wants a higher res screenshot, I used it to set up my desktop, and then installed my nvidia drivers, so I attached a higher res screenshot on how it looks when the script is done.

edit: forum seemed to have resized image so uploaded to imageshack.

[[IMG]http://img412.imageshack.us/img412/586/200911230304471680x1050.th.png[/IMG]](http://img412.imageshack.us/img412/586/200911230304471680x1050.png)

---

### Post by thegreenblob on 2009-11-29
Updated script.

Had a nasty problem with slim filling up my / partition with it's logfile. :o

So I changed the script to change the logfile location for it to /dev/null.

---

### Post by omns on 2009-12-10
This is a lovely script thegreenblob :D Just wanted to let you know that I have a small reproduction of this script and how-to on [my blog]("http://dtx.omnsproject.org/?p=186") with plans to modify it a bit for Xfce and pekwm installs.

---

### Post by thegreenblob on 2009-12-10
> **omns said:**
> This is a lovely script thegreenblob :D Just wanted to let you know that I have a small reproduction of this script and how-to on [my blog]("http://dtx.omnsproject.org/?p=186") with plans to modify it a bit for Xfce and pekwm installs.

Thanks! Glad you like it. :)

And to anyone that's interested, I added some things to the script. It now does the following.

* Chooses default GTK theme so apps don't look yucky :P
* Changes Openbox Theme to match
* At the end it now asks you if you want to do extra stuff, if you choose yes it will,
* ask you if you want to install flash
* ask you if you want to install yaourt
* ask you if you want to install common media codecs
* ask you if you want to be able to play encrypted dvds

Hope everyone liked the changes. :P I've attached the new script, I call it "beta" because I haven't tested it yet. But it *should* work. If in doubt just use the old one. ;) And I haven't uploaded it to the 110mb account because it seems to be down at the time of me posting this.

edit: 110mb back up here's link for people that want to wget it: [http://openboxarch.110mb.com/openboxarch-beta.sh](http://openboxarch.110mb.com/openboxarch-beta.sh)

---

### Post by omns on 2009-12-11
^ This just keeps getting better. I'll give these extra features a test over the weekend :)

---

### Post by enseyn on 2009-12-15
First off, thank you so much thegreenblob, I love your script and have greatly enjoyed playing around with it. I have been altering it to automate a lot of the programs and settings that I've always just done manually and was hoping if anyone could point out any problems. I have not tested it yet, so I just wanted to know if anyone sees any obvious problems that I might be overlooking.

The main things I changed were setting up nvidia driver, usage of yaourt, and my menu.xml.

I plan on testing it in the next couple days, Just let me know how bad I messed things up ;)

---

### Post by thegreenblob on 2009-12-15
> **enseyn said:**
> First off, thank you so much thegreenblob, I love your script and have greatly enjoyed playing around with it. I have been altering it to automate a lot of the programs and settings that I've always just done manually and was hoping if anyone could point out any problems. I have not tested it yet, so I just wanted to know if anyone sees any obvious problems that I might be overlooking.

The main things I changed were setting up nvidia driver, usage of yaourt, and my menu.xml.

I plan on testing it in the next couple days, Just let me know how bad I messed things up ;)

Glad you like it. :) And I looked over the script, I think you have a problem at this point:

> pacman -S ... yaourt --noconfirm
yaourt -Syu --noconfirm
yaourt -S vbaexpress gnome-specimen fontypython snes9x-gtk adeskbar --noconfirm

You're trying to install and use yaourt without adding the archlinuxfr repos, from my understanding yaourt isn't in the main repos. I could be wrong though, but that's the impression I got from the wiki.

---

### Post by enseyn on 2009-12-15
Thanks, I have always installed yaourt from the AUR builds so I am guessing you are right, I will have to change that, Thanks :)

---

### Post by phrostbyte on 2009-12-16
This code:

```

if [ "$REPLY" == '' ]; then
    clear;
else
    clear;
fi

```

can be replaced with:

```
clear
```

It's functionally equivalent. :D

I like how you integrated 64-bit flash in your script as an autoinstall. If the version numbers change, you will probably have to update your script accordingly. There may be a way to prevent this to happening using wget's crawling features, but I am not sure how. Don't worry too much though, Adobe is really really slow with the flash updates especially to the 64-bit version. :)

---

### Post by thegreenblob on 2009-12-16
> **phrostbyte said:**
> It's functionally equivalent. :D

Changed it, Thanks. I'm not sure why I was thinking that needed to be there... lol.

> **phrostbyte said:**
> I like how you integrated 64-bit flash in your script as an autoinstall. If the version numbers change, you will probably have to update your script accordingly. There may be a way to prevent this to happening using wget's crawling features, but I am not sure how. Don't worry too much though, Adobe is really really slow with the flash updates especially to the 64-bit version. :)

Yeah I'm not really worried about it. I believe the last 64 bit flash update (before the one that was this month) was in like 2008.

---

### Post by Tibuda on 2009-12-16
> **thegreenblob said:**
> Yeah I'm not really worried about it. I believe the last 64 bit flash update (before the one that was this month) was in like 2008.

No, "The latest alpha refresh for was released on December 8, 2009": [http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)

EDIT: Run this on the terminal to find the last download available:
```
wget -q http://labs.adobe.com/downloads/flashplayer10_64bit.html -O- | grep 'http\(.*\)\.so\.tar\.gz' -o
```

---

### Post by thegreenblob on 2009-12-16
> **danielrmt said:**
> No, "The latest alpha refresh for was released on December 8, 2009": [http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)

I was referring to the refresh that was before the December 8th one.

> **danielrmt said:**
> EDIT: Run this on the terminal to find the last download available:
```
wget -q http://labs.adobe.com/downloads/flashplayer10_64bit.html -O- | grep 'http\(.*\)\.so\.tar\.gz' -o
```

Awesome, even less worrying about it. :) Will add this to the script. Thanks.

---

### Post by Tibuda on 2009-12-16
> **thegreenblob said:**
> I was referring to the refresh that was before the December 8th one.

I think I should read stuff twice before replying!

---

### Post by enseyn on 2009-12-17
So this is how i should install and implement yaourt, right?
```
echo "[archlinuxfr]
Server = http://repo.archlinux.fr/$(uname -m)" >> /etc/pacman.conf
pacman -Sy yaourt --noconfirm
yaourt -Syu --noconfirm
yaourt -S vbaexpress gnome-specimen fontypython snes9x-gtk adeskbar --noconfirm
```

---

### Post by thegreenblob on 2009-12-17
> **enseyn said:**
> So this is how i should install and implement yaourt, right?

Yeah, seems about right.

---

### Post by kelvin spratt on 2009-12-17
Add this to etc/ pacman.conf [http://archlinux.fr/yaourt-en#Utilisation](http://archlinux.fr/yaourt-en#Utilisation)
But why would anybody want to make this script. Arch is easy to set up.
you can use Larchin to make live installable CDs.
or use [http://godane.wordpress.com/](http://godane.wordpress.com/) to obtain a live Installable XFCE desktop install disk.
or [http://chakra-project.org/download-iso.html](http://chakra-project.org/download-iso.html) for KDE4.
or [http://www.kahelos.org/downloads.php](http://www.kahelos.org/downloads.php) for Gnome.

---

### Post by enseyn on 2009-12-17
> **kelvin spratt said:**
> 
But why would anybody want to make this script. Arch is easy to set up.
you can use Larchin to make live installable CDs.

Yes, Arch is easy to set up, I've already done it 4 times in the past month just to experiment with different set ups. I guess the reason why I am trying out a scripted set-up if just to do it, no other reason. Trying to learn a little, and think about things in different ways. This is definitely not the easiest way to set up an arch system, but it is a quick short-cut to automate a lot of the redundant operations I have been doing repeatedly. I guess I am saying why not make a script? I know very little about scripting, and just fidgeting with this one has help me learn a lot about how a good one might be built. simple, direct, and efficient.

---

### Post by omns on 2010-01-17
> **kelvin spratt said:**
> but why would anybody want to make this script. 

Because some people enjoy using scripts like this :) I'm adapting this to install an xfce setup suited to my needs. It will be available at my [DTX blog]("http://dtx.omnsproject.org/") when complete.

---

