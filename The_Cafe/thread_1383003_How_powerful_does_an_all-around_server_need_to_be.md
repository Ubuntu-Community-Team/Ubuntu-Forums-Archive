---
title: "How powerful does an all-around server need to be?"
date: 2010-01-16
forum: The Cafe
---

### Post by TheOrangePeanut on 2010-01-16
I'm interested in purchasing a machine to act as a central server for all of my computer needs.  Some things I intend to do with it include:

Webserver (most likely Apache)
Host databases (probably using Mysql)
Version control server (SVN or GIT, I haven't decided which yet.)
General file server (store all of my music, videos, documents, etc)
Movie center (I plan to hook it up to my TV and watch movies and whatever directly from the computer)

Eventually I would like to be able to record TV programs or something like a DVR, but that isn't high priority.  I only have basic cable now so theres not even anything worth recording.

This stuff doesn't look too processor intensive, so would something like an Atom be able to handle all of that?

Also, I will be mostly watching 720p videos from the machine, so it must be able to handle high def.  I'm leaning toward an Nvidia Ion machine, but if I need more power then I will build it myself. 

What is the opinions of this board?

---

### Post by handy on 2010-01-16
How many people &/or how many different tasks the server will be required to do at once has an effect, as does the speed of you LAN.

I would go for the lowest power drawing device that will also supply the video horsepower you require.

I have an old PIII 700Mhz, 256MB RAM, 8GB HDD, that runs headless 24/7 as a firewall/router, at $0.19.64 cents per kilowatt, I'm up for $55-/year in Oz dollars.  The HDD does next to nothing, it just sits there at idle for a good 95% of the time.

I used a Power-Mate to test what it costs to run.  

I may end up replacing the PIII with an Atom board, but I'm hanging out for the under-clocked Athlon 2000, which outperforms the Atom & uses less energy, I don't know when it is going to hit the streets though.

---

### Post by MaxIBoy on 2010-01-16
> **TheOrangePeanut said:**
> I'm interested in purchasing a machine to act as a central server for all of my computer needs.  Some things I intend to do with it include:

Webserver (most likely Apache)
Host databases (probably using Mysql)
Version control server (SVN or GIT, I haven't decided which yet.)
General file server (store all of my music, videos, documents, etc)
**Movie center (I plan to hook it up to my TV and watch movies and whatever directly from the computer)**This last one will be the major limiting factor, as it uses up far more resources than anything else on your list. However, if you already have another computer, you can store your movies and stuff on the server and then mount the server's filesystem using [sshfs]("http://fuse.sourceforge.net/sshfs.html"). That way, you don't need to set up any fancy video streaming software on the server, you can just view and play files on the server as if they are on your other computer. 

If the server itself doesn't have to play videos, I would suggest something along the lines of a PII with 256 Mb RAM at the absolute most. I have a home server which I use as a torrent slave, Git repository, webserver, game server, print server, and backup server. I'm nowhere close to using the full 192 Mb RAM I have on it, and the PII stays under 30% most of the time. I watch videos from it all the time, but they aren't actually being rendered on the machine so the 3DFX Voodoo isn't a limiting factor at all. I got the machine free in exchange for rescuing files from it, and all it needed was a new hard drive (cheap) and a new NIC (very cheap.) I just blow the dust out of it every couple of months, and if the power goes out I need to turn it back on. Other than that, it might as well be in another state for all the maintenance it requires.

Of course if you expect a lot of traffic on that website (more than 15-20 people on it at once,) you would want a newer CPU (think PIII.) However, if you use nginx instead of Apache, not only will your server be way easier to set up (took me 30 minutes the first time I ever did it,) but it will also tax your resources a lot less. I really cannot recommend nginx enough for home webserver use.

---

### Post by markp1989 on 2010-01-16
everything except the htpc side can be achieved using a sheeva plug : see here [http://ubuntuforums.org/showthread.php?t=1082489](http://ubuntuforums.org/showthread.php?t=1082489)

one thing you could do is set up the sheeva plug with a usb hard drive attached to it, to do all your serving tasks.

then buy some cheap p3 or similar, install geexbox  on that, mount the hard drive on the sheeva plug  over the network then use that to play videos.

my first media pc was running geexbox on a 600mhz P3


edit: another posibility would be an atom based machine (like you sugested), with an nvidia-ion intergraded gpu. 

i have read reports of the acer aspire revo being used as a htpc because of its size (and that it can be mounted on the back of alot of tvs/monitors) hdmi out with ability to play 720p videos (i never tried this, might have to steal my sisters one and give it a test) 

revo is here: [http://www.ebuyer.com/product/167153](http://www.ebuyer.com/product/167153)   or here [http://www.ebuyer.com/product/172708](http://www.ebuyer.com/product/172708) (same range, just with higher spec) 
geexbox here: [http://www.geexbox.org/en/index.html](http://www.geexbox.org/en/index.html)

---

### Post by plutozzz on 2010-01-18
> **markp1989 said:**
> i have read reports of the acer aspire revo being used as a htpc because of its size (and that it can be mounted on the back of alot of tvs/monitors) hdmi out with ability to play 720p videos (i never tried this, might have to steal my sisters one and give it a test)

I have deployed a few of the dual-core Atom (330) Revo systems at my office, I tested them with some 1080P x264 MKV files with CoreAVC decoder installed, they handled playback effortlessly thanks to the Nvidia CUDA acceleration of the ION chipset.

Not only that, they make a great office workstation for the typical user. I replaced Pentium 4 2.8ghz systems and everyone is happy with the Revo's.

I would say the average home server is probably overpowered for what is used for, unless it is transcoding HD video from one format to another. I'm currently awaiting my Sheeva Plug system, hoping it will take the place of my current server/nas.

---

### Post by sandyd on 2010-01-18
a tonidoplug should be able to handle all of that stuff. I got one at home and it sucks up really little power and makes no noise at all. although the storage is 512mb, you can expand it by plugging in a usb drive.

---

### Post by markp1989 on 2010-01-18
> **plutozzz said:**
> I have deployed a few of the dual-core Atom (330) Revo systems at my office, I tested them with some 1080P x264 MKV files with CoreAVC decoder installed, they handled playback effortlessly thanks to the Nvidia CUDA acceleration of the ION chipset.

Not only that, they make a great office workstation for the typical user. I replaced Pentium 4 2.8ghz systems and everyone is happy with the Revo's.


thats nice, i almost brought 1 when building my htpc/server but the 2.5" hard drive limit stoped me, if they made a similar spec machine with a slightly bigger case for enough space for 2 full size hard drives i would def buy one. 

> **plutozzz said:**
> I would say the average home server is probably overpowered for what is used for, unless it is transcoding HD video from one format to another. I'm currently awaiting my Sheeva Plug system, hoping it will take the place of my current server/nas.

I have been looking at 1 of the sheeva plugs , they are a excellent idea, i want one, but i cant think of a use for it.  the only one i can think of is for home automation, but i cannot afford the x10 hardware :(

---

