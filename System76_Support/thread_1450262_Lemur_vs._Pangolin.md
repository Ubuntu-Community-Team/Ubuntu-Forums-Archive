---
title: "Lemur vs. Pangolin"
date: 2010-04-08
forum: System76 Support
---

### Post by stangdaman on 2010-04-08
I'm considering going with a System76 laptop here soon and was just wondering what the performance difference is between the Lemur and the Pangolin assuming you go with the default processor. Has anyone had experience with both?

---

### Post by thomasaaron on 2010-04-09
There is a lot of difference in the performance. The base Pangolin has a faster CPU and more powerful graphics.

---

### Post by stangdaman on 2010-04-09
I'm sorry. Perhaps that's too broad a question. I realize that the hardware is better in the Pangolin. I guess the nature of my question is how noticeable the difference in performance is and if the trade of of the smaller sleeker form factor would be worth putting up with the performance difference. I also realize that this is a question that is different for each user I'm just trying to get a general feel of other people's opinions. I am more leaning towards the Pangolin because I would like a laptop with a bit of kick but I also like the idea of a slim laptop too.

---

### Post by satsujinka on 2010-04-09
Well it really depends on what you want to do. If you're into virtual machines than you'll want the pangolin for the virtual i/o support. If you want to play any modern (last 2-3 years) commercial games you'll want the pangolin. The lemur should be able to handle anything else (not fast, maybe not even acceptably, but it can do it.) So if lightweight is really important and you aren't doing either of my two examples, go with the lemur.

---

### Post by stangdaman on 2010-04-10
Thanks for the input. I've never, really, owned a laptop and am kind of new to linux. I have an older desktop running opensuse right now and I've loved it hence my interest in a linux laptop. 

I don't really do much gaming so that's not really a concern. I do build HTPCs and do some audio recording so I may mess around with Audacity on the laptop.I have a UMPC (Raon Everun) right now that I will not be abandoning as well but for the most part the laptop will be doing office tasks, video and audio editing. The last two items are things the UMPC either can't handle or the really small form factor is not too suitable for.

---

### Post by satsujinka on 2010-04-10
Well, technically, the lemur can do video and audio editing... Though it's going to be like pulling teeth. Just based on that alone I'd say that you should go with the pangolin, unless you really need the smaller form factor (which it doesn't sound like.)

---

### Post by stangdaman on 2010-04-10
Cool, again, thanks for the input. On that note any good video editing software you would suggest. Maybe I can start messing around with it on the desktop right now.

---

### Post by isantop on 2010-04-10
When we start shipping pangolins with 10.04 after release, they will include the PiTiVi editor. It's good, and fairly powerful, and may suit your needs well.

---

### Post by bigcat42 on 2010-04-26
I'm in the same boat as the original poster- looking to get a System76 laptop, and I'm considering either a Lemur or a Pangolin. It will mostly be used for surfing the internet, playing flash games, watching videos. And most importantly it needs to be well suited for DJing (simultaneously run two music players, probably Banshee and Audacious, with no hiccups, also reasonably sized screen). I would also like it to be fairly portable, whether for just hanging in a coffee shop or carrying it on a trip.

I'm currently using a Dell Vostro 1500. I like the 15.6" screen size, but the battery dies too quick for my tastes, and it's frickin heavy (I believe over 8 pounds). I'm currently leaning towards the Lemur as the portability is attractive and I don't need all that much speed. On the other hand, Pangolin does offer an impressive bump in hardware power and screen size for a seemingly small bump in weight.

Thoughts? Suggestions?

---

### Post by thomasaaron on 2010-04-26
The battery life on the Pangolin is about 1.5 - 1.75 hours. The Lemur's battery life is about 3 hours.

---

### Post by satsujinka on 2010-04-26
@bigcat42
The lemur should be able to do what you need. The pangolin's main advantage over the lemur is raw power (cpu/gpu.) Which doesn't really effect audio playback. The raw power of the pangolin may increase responsiveness of running banshee and audacious concurrently, but it shouldn't be too noticeable. Switching from alsa to oss would probably make a larger difference. That said, what are the specs of your Vostro? How does banshee and audacious run on it? If they run fine and your vostro isn't too much different in terms of cpu then I would think the lemur would work fine. But both would work fine, and it really just depends on how much you need those extra hours of battery life.

---

### Post by stangdaman on 2010-05-08
Well I finally bit the bullet and bought the Pangolin. I just ordered it today and am already antsy to get my hands on it. I stuck with the i5 even though I thought about upgrading to an i7 got the higher resolution display, a solid state drive and 6 gb RAM. 

The SSD is the part I'm pretty curious about. I'd like to see how the SSD effects boot times, loading programs and things like that. It will be a little hard to compare though since my other linux PC is so old it will be pretty difficult to determine what performance boost is from the SSD and what is from just newer better hardware all around.

---

### Post by bigcat42 on 2010-05-11
Thanks, satsujinka.

Finally pulled the trigger on a new Lemur. Ultimately the light weight and battery life are far more important to me than pure speed. Now I'm just anxiously waiting for it to arrive...

---

### Post by stangdaman on 2010-05-19
So, I got my Pangolin today, which I am typing on right now, and so far so good. I'm still trying to get a few things working. I can't seem to get the webcam to work for one. I ran the system76 driver installer and installed camorama but when I try to start it up I get a could not connect to video device error.

---

### Post by thomasaaron on 2010-05-20
Camorama isn't compatible with your camera.

You'll need to use Cheese or Skype. Also, press Fn and F10 simultaneously to turn the camera on.

---

### Post by stangdaman on 2010-05-20
It does work with that. Thank you.

---

### Post by stangdaman on 2010-05-20
ok, one more question. I was trying to enable compiz but I can't enable more than one desktop. When I try it just reverts back t0 1. I'm sure there's just some setting I'm not aware of. Any suggestions?

---

### Post by thomasaaron on 2010-05-21
Compiz comes enabled on the machine.

To create multiple desktops, right click the desktop switcher in the lower right corner of the screen and select "Preferences" from the resulting sub-menu.

Once you add more desktops, you can switch between them by clicking in the window switcher (lower right corner of the screen) or by pressing Ctrl-Alt-[left arrow | right arrow].

To *configure* different effects with Compiz, go to Applications > Ubuntu Software Center and install "Advanced Desktop Effects Settings. You'll see it if you search for "compiz".

---

### Post by stangdaman on 2010-05-21
Thanks, I had already installed that but for some reason it doesn't give me the option to add desktops when I right click. There are four there though. I can use ctrl alt to switch between them I just didn't know that that was the command for it. As long as it's working I'm good. Thanks.

---

### Post by stangdaman on 2010-05-21
Ok, more. Sorry for the annoying and pretty simply questions. I'm trying to access my folders that are shared on my xp machine. I'm got samba and my workgroup is correct but when I go to "places" "network" "windows network" and then my workgroup I get this message "failed to mount location failed to retrieve shared list from server." Any suggestions?

---

### Post by stangdaman on 2010-05-24
I just figured I'd give this a little bump since I posted it at the beginning of the weekend and it might be a bit buried by now.

---

### Post by thomasaaron on 2010-05-24
Hey, Stangdaman.

Did it prompt you for a username or password prior to giving you that error? If so, it would be the username/password on the machine with the shared folder.

---

### Post by stangdaman on 2010-05-24
No, it doesn't ask for a username or password. However, I just tried to check it to give more detail and now I can view all of them. I have no idea what has changed.

---

