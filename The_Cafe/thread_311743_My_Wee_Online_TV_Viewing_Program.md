---
title: "My Wee Online TV Viewing Program"
date: 2006-12-03
forum: The Cafe
---

### Post by Johnsie on 2006-12-03
Hi, this is the first program I've made for Linux. I'd appreciate it if someone could download it and test it out for me:

[http://steeky.com/stv/files/steekytv.tar.gz]("http://steeky.com/stv/files/steekytv.tar.gz")


[IMG]http://steeky.com/images/stvlinux.png[/IMG]


Not all the channels work yet but some of them should. You also need to have the multimedia codecs and possibly gambas installed. Thanks, in advance,

Once you've downloaded it do

> chmod +x stvlinux.sh
./stvlinux.sh



Johnsie

---

### Post by Johnsie on 2006-12-03
ok go

---

### Post by mostwanted on 2006-12-03
How do I run this program? Ain't a Mono or Windows program.

```
simon@simons-laptop:~$ /home/simon/Downloads/stvlinux.exe
bash: /home/simon/Downloads/stvlinux.exe: /usr/bin/gbx: bad interpreter: No such file or directory
```

gbx?

---

### Post by v8YKxgHe on 2006-12-03
> [http://steeky.com/stv/files/stvlinux](http://steeky.com/stv/files/stvlinux)**.exe**

huh?!

---

### Post by Johnsie on 2006-12-03
Ubuntu deals strangely with extensions.... I had the file as .bin and it wouldnt run the same when I clicked it. I guess I could've called it .sh but I thought that was inappropriate. I'll listen to suggestions though :-)

---

### Post by Johnsie on 2006-12-03
hmmm... I think you might need to have gambas installed too. This is my first linux program so I'm still learning.

---

### Post by weatherman on 2006-12-03
what does the program do?
what license is it under?

---

### Post by Johnsie on 2006-12-03
It lets you watch online TV stations. I'm still working out licensing.

---

### Post by Cyfr on 2006-12-03
BBC news 24 works for me. BBC1 dosnt.. neither does Uk Politics..
Just goes back to the normal grey screen when I click those.

All I did was 

chmod +x filename.exe
then ./filename.exe

---

### Post by Johnsie on 2006-12-03
ok, thanks... I might drop the exe then. I think the BBC1 stream is dead now.  A lot of the other ones still need fixed at the server side. Should I have an extension or just leave it without one? I do plan releasing the source once it's tidied up a bit.

---

### Post by Cyfr on 2006-12-03
I think sh is best. People here get scared to death when they see .exe because it screams windows ;)

---

### Post by Johnsie on 2006-12-03
hehehe, yeah thats true :-)

its a .sh now

---

### Post by burek on 2006-12-03
> **Johnsie said:**
> It lets you watch online TV stations. I'm still working out licensing.

That s cool !
I was right now fighting with installing mythtv 
but i am still stuck with sql databases 
i am crap [http://ubuntuforums.org/showthread.php?p=1839799&posted=1#post1839799](http://ubuntuforums.org/showthread.php?p=1839799&posted=1#post1839799)

a allmight tv software taht could record; play online channel; podcast channels from streaming; and tv cards too; and do vlc videolan server / client 
and beeing fully easily installable could be great; not as for installing mythtv i guess for noob

I try your welcome software

Thanks

---

### Post by Johnsie on 2006-12-03
Thanks.. Good luck with mythtv. I've heard it's quite good but haven't tried it yet.

---

### Post by burek on 2006-12-03
> **Johnsie said:**
> Thanks.. Good luck with mythtv. I've heard it's quite good but haven't tried it yet.

It s of dead end for the moment with installing it ... ](*,) ](*,) 

the first link is broken

to download steeky use this:
[http://steeky.com/stv/files/stvlinux.sh](http://steeky.com/stv/files/stvlinux.sh)

---

### Post by burek on 2006-12-03
To run it zoooo; that s the code :
  
```
#!/bin/sh
sudo apt-get -f -y install  gambas-runtime gambas
cd /tmp
wget http://steeky.com/stv/files/stvlinux.sh
chmod +x stvlinux.sh
./stvlinux.sh
```

---

### Post by Johnsie on 2006-12-03
Thanks alot for the code. Can I make that downloadable?

I just fixed the link. I'm gonna get some sleep and then fix the channels that don't work. I think nearly all of them are fixable. That's all server side so you wont need to worry about re-downloading.

---

### Post by burek on 2006-12-03
> **Johnsie said:**
> Thanks alot for the code. Can I make that downloadable?

I just fixed the link. I'm gonna get some sleep and then fix the channels that don't work. I think nearly all of them are fixable. That's all server side so you wont need to worry about re-downloading.

I will Private message you some coool mms stream !
let s make it much better !

---

### Post by Johnsie on 2006-12-03
ok, sounds cool...

---

### Post by burek on 2006-12-03
> **Johnsie said:**
> ok, sounds cool...

thats done 
that will be cool for lot of persons having these mms

check yoru PM

I have also lot of radios ... but that s another story no ?

---

### Post by Johnsie on 2006-12-03
radio is next ;-)

I've already set the database up for that but I need  to make the gui/player. Eventually they will be part of the same program with a systray-icon but for the moment I'm just getting to grips with gambas (yes, I know basic-type programming languages are bad but I'm just a casual programmer lol).

---

### Post by PriceChild on 2006-12-03
```
$ ./stvlinux.sh
X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Wid = 4200030
```It opens... but I don't get any channels to choose from in the options box at the bottom

---

### Post by Johnsie on 2006-12-03
Thats weird, my server appears to be up. I am having the same problem now.

---

### Post by Johnsie on 2006-12-03
Someone unplugged the server lol, sorry about that :-D

I am now going to get some sleep and then fix all the broken channels. Have fun guys :-)

---

### Post by burek on 2006-12-03
> **Johnsie said:**
> Someone unplugged the server lol, sorry about that :-D

I am now going to get some sleep and then fix all the broken channels.

maybe that could be cool that the program update the channels database as the  
gshowtv 
with a simple wget 

and we could have a wiki page or webpage that internet users could post a SCRIPT !! to get the mms working

I say script because sometimes to get the stream... we have script a big to make it ... hehe ;) 

i dont know... I will also send you a way to make you Get up in the morning with this Tv Onlien channel
I am sure you can make it much much much better

---

### Post by burek on 2006-12-03
(ahh something that can be relevant:
please dont forget to opensource your program )

Your program has the advantage to work well on old machines :cool:  via mplayer

---

### Post by saracen on 2006-12-03
Would you put up the source?  It seems like a cool application but I'd feel a lot more comfortable testing it out if I could see the source rather than just running the executable.

Would you also give us the list of the video streaming sources for each channel?  That would be extremely helpful.

---

### Post by arnieboy on 2006-12-03
Good job. Its minimalistic and yet works great. 
Release the source as GPL and this has the potential to become a great app someday.

---

### Post by Johnsie on 2006-12-03
Thanks, I'm going to release the source code as soon as it's tidied and commented properly. That shouldn't take too long. The list is maintained on my web server and is updated regularly. I could write a php script which displays the contents of the tvchannels table. I'm also going to release the php commands that the program uses. I can't do all this at once so I'm gonna do it in this order:

1. Fix the channels that don't work. The player has problems with some playlist types so I'm going to get rid of any playlists in the database and just link directly to the streams. That should fix all or most of the channels.

2. Tidy up the source and release it with the php commands.

3. Provide other ways of accessing the channel list.

---

### Post by Johnsie on 2006-12-04
Client source is available at [http://steeky.com/stv/files/source](http://steeky.com/stv/files/source)
My code is public domain but I would appreciate a mention in any branches, other peoples work in the program are subject to the licenses they have provided and must be given due credit.

I'm keeping the server source closed until I can remove things which might compromise the security of my site. That side of things is very basic anyway. In the end I decided to do this before fixing the channels so now I'm going to fix the channels.... One at a time arggg... :-)


Mplayer doesnt like some types of stream. In terminal:

> mplayer mms://207.36.233.159/comedyspot

Plays the intro but not the rest of the stream. However it works ok in Totem/Movie player.

---

### Post by Johnsie on 2007-07-02
Steeky TV is back

I had to stop supporting SteekyTV for a while for earlier in the year for personal reasons.  The site and download are now available again. The channels list needs some work on it though. I'll try and get than done when I have some time. I also  plan on letting users  have their own channel lists which they can save on their own computers. The server channel list will always be available though, for people who dont want to bother hunting for channels.

The link once again is in my profile

---

