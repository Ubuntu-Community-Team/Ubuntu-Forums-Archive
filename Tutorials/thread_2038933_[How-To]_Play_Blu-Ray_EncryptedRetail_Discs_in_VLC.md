---
title: "[How-To] Play Blu-Ray Encrypted/Retail Discs in VLC On Linux"
date: 2012-08-07
forum: Tutorials
---

### Post by pinguy on 2012-08-07
This will play pretty much any Blu-ray released before 2012.

After that its a bit hit and miss because most blu-rays released in 2012 are using BD+ protection, and as of yet only AACS has been cracked using VLC (*but BD+ has been cracked. But at the moment libbdplus hasn't been made public because of legal concerns*). Also most of FOX blu-rays use BD+ so they don't work.

I have tested many blu-rays and nearly all of them work:
[list]
[*]Inception
[*]The Dark Knight 
[*]Toy Story 3
[*]District 9
[*]Inglourious Basterds
[*]Watchmen
[*]Plus many others working.
[/list]
The only ones I couldn't get working are the X-MEN Quadrilogy box-set and ALIEN Anthology box-set. These are the only ones in my collection using BD+

To get Blu-ray's to work in VLC run these commands:

```
sudo add-apt-repository ppa:n-muench/vlc
sudo apt-get update
sudo apt-get install vlc libaacs0 libbluray-bdj libbluray1
sudo apt-get dist-upgrade
```

Now we need to make a aacs folder and download the keys:

```
cd ~/
mkdir -p ~/.config/aacs/
cd ~/.config/aacs/ && wget http://vlc-bluray.whoknowsmy.name/files/KEYDB.cfg
```

Thats it. Blu-rays will now play. 

To play them in VLC. Open VLC and hit Ctrl+d or select Media > Open Disc... 

[img]http://img6.imagebanana.com/img/nv3avf71/OpenMedia_213.png[/img]

Make sure "no disc menus" is selected. Now click on Browse.. and select the disc.

[img]http://img6.imagebanana.com/img/qi07ifx5/SelectadeviceoraVIDEO_TSdirectory_21.png[/img]

[img]http://img6.imagebanana.com/img/yxoer10r/OpenMedia_217.png[/img]

Then just click play.

[img]http://img6.imagebanana.com/img/mki91rnw/DISTRICT_9VLCmediaplayer_216.png[/img]

For BD+ Blu-rays you can crack them in Linux but you need to pay for a piece of software, [DVDFab HD Decrypter 8](http://www.dvdfab.com/) (*comes with a 30 day free trial*). This works fine in Wine 1.4 and can rip BD+ encrypted Blu-rays.

[IMG]http://i50.tinypic.com/35i0s5c.png[/IMG]

---

### Post by ads52 on 2012-08-18
Should not have to buy software for bd+ disks, on my own system I have had great success with *makemkv* which has a nice option to stream the bluray title (UPNP) so either MPlayer or vlc can playback. But I will admit that I have not tested this with a *great* range of blurays....

---

### Post by pinguy on 2012-08-20
> **ads52 said:**
> Should not have to buy software for bd+ disks, on my own system I have had great success with *makemkv* which has a nice option to stream the bluray title (UPNP) so either MPlayer or vlc can playback. But I will admit that I have not tested this with a *great* range of blurays....

The BD+ feature in makemkv costs money. £46.77 GBP

[http://www.makemkv.com/buy/](http://www.makemkv.com/buy/)

However there is a big catch (their words not mine) MakeMKV needs the BD+ decryption keys to be able to de-encrypt BD+
[http://www.makemkv.com/svq/](http://www.makemkv.com/svq/)

They have a list of BD+ keys but it isn't very impressive: [http://www.makemkv.com/forum2/viewtopic.php?f=1&t=612](http://www.makemkv.com/forum2/viewtopic.php?f=1&t=612)

So BD+ decryption in MakeMKV is about as useful as it is in VLC, and VLC can't even de-encrypt BD+

Why would anyone pay $50 for something that VLC can do for free?

If you want to pay for software to rip BD+ Blu-rays get DVDFab HD Decrypter 8. It works fine in Wine and you don't have to go though all the hassle of having to find the SVQ keys.

---

### Post by jq1801 on 2013-05-01
has anyone tried to use the free dvdfab passkey lite to play blurays?

---

### Post by gravier on 2013-06-16
I was struggling for a long time finding something working on ubuntu. At least for watching DVD fab didn't worked for me, also they have this annoying restriction if you don't use HDMI or any other digital output for some blu-rays they just show green screen (encrypt or something).
Just recently I found Aisee-soft Blu-ray Player, which to my surprise works even with wine with some minor flaws, and you can get it for about ~20$ with a discount. Which is not so bad when you think about supporting someone that allows you to workaround all the rules that some big boys think of, e.g. blocking the content you paid for.

Cheers!

---

### Post by coldraven on 2013-06-16
My cunning plan is not to buy any Blu-ray discs and not having a TV or HDMI equipment.
I will have plenty of movies to watch for the first time if I ever get into an old folks home :)
Don't buy the hype!

---

