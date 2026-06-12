---
title: "Who-buntu?"
date: 2010-06-28
forum: The Cafe
---

### Post by Whistling Nixie on 2010-06-28
Recently I've been experimenting with different desktop environments, such as Xfce and KDE. Hence I converted my Ubuntu Karmic to Xubuntu, then Kubuntu. I've had to turn my back on KDE, as it was frying my laptop, and Xfce didn't allow me to mount my camera! So I'm back to good old GNOME. Now, I've tried uninstalling the other desktops, but obviously haven't succeeded in doing so. 

Here's the strange thing. When I boot up, the boot menu shows the Linux options as "Linux Mint", followed by the Xfce mouse (as per Xubuntu), then the Kubuntu login screen comes up. From there, I can easily log into GNOME. Now, which version of Ubuntu 9.10 do I now have? It seems to be some sort of "Frankenbuntu", although I don't mind if everything continues to work fine.

---

### Post by chessnerd on 2010-06-29
Ah DE hopping. Been there, my friend. And my concerns for Xfce and KDE are identical to yours.

I'm not sure what you have there. One way to find out is under System>Administration>Software Sources. Under "Installable From CD-ROM/DVD" it should tell you your Ubuntu version.

To remove those desktop environments completely, if you wish to do so, I'd suggest using Synaptic. However, I will give you one warning: read the "Mark additional changes" dialog to check to make sure that nothing important is being removed. If you doubt it, don't remove it, and double check if you aren't sure. If you do mess up, Syanptics keeps a history of changes under File>History.

First, that KDE/Kubuntu login screen is called "kdm." Search for that and remove it and you should then have good old gdm, the Gnome/Ubuntu login manager, back.

Next, if you want to remove Xfce, search for "Xfce" and "Xfce4" and remove all relevant packages there. Xfce should then be gone.

After that, you must ask yourself a question: do you have any KDE/Qt applications that you use in Gnome? 

If the answer is "no" search Qt and remove everything you find. That should wipe KDE from your system completely because almost all KDE programs depend on Qt. You should still search KDE after that, but you probably won't find anything that isn't marked for deletion already.

If the answer is "yes" then you have two options:

1. Remove that stuff anyway and just reinstall the applications later.
2. Check the additional changes when removing that stuff and make sure your application(s) are not in the list.

After that, Xfce and KDE should have been purged from your systems.

---

### Post by aphatak on 2010-06-29
Actually, Frankenbuntu sounds like a pretty good name.  I have most of my computers with Gnome and KDE desktops, and I was thinking of calling them Twinbuntu!:lolflag:

---

### Post by Starks on 2010-06-29
This might help you...

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)
[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

Purges other DEs.

---

### Post by Primefalcon on 2010-06-29
I was modding around a while back and well here's a combo gnome/kde DE I had running

[http://i48.tinypic.com/v6jhb4.jpg]("http://i48.tinypic.com/v6jhb4.jpg")

---

### Post by Stancel on 2010-06-29
You should just stick to GNOME if you're looking for merely a different visual look (having two panels does look stupid to most people) you can do that too, GNOME is very customizable visually. Just go to the Gnome Look website. It only takes a bit of tweaking and you can get your desktop to look nice like Windows 7. [here]("http://gnome-look.org/content/show.php/Lucid+Start+Here+Button?content=125229") is a good example I found.

---

### Post by Whistling Nixie on 2010-06-29
> **Stancel said:**
> You should just stick to GNOME if you're looking for merely a different visual look (having two panels does look stupid to most people) you can do that too, GNOME is very customizable visually. Just go to the Gnome Look website.
True, although I think KDE looks even better. But stability and computer lifespan are more important than eye-candy, so GNOME wins out.

Thanks, everyone... it's sorted.

---

