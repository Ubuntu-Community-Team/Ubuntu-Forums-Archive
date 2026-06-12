---
title: "Useful Tips for iPhone (and iTouch) Users"
date: 2009-05-13
forum: Tutorials
---

### Post by xrecar on 2009-05-13
Hey everyone. I'm supposing that you're reading this because you either own an iPhone or iPod Touch, or plan to buy one or something related to an iPhone or iTouch... This is based on my own personal experience and I'd like to share these tips with you.

**Battery Drain when syncing**
The iPhone and iTouch use a lot of battery life when syncing over SSH since the screen needs to be left on or otherwise the wifi connection will be lost. This is a problem for many, and this is why there is an app on Cydia called Insomnia.

Insomnia, allows to lock the screen and shut the screen down while still using the wifi. This saves up a lot of battery when syncing. I recommend it a lot because it works and I use it on my 3G.

**Converting video:**
Sometimes it gets annoying to transfer video from ubuntu to the iPhone or iTouch, it's even more annoying trying to convert it (specially if it was downloaded from youtube).

Install these packages through synaptic:
[LIST]
[*]ffmpeg
[*]libavcodec-unstripped-52
[/LIST]
These will save you a lot of google time, then to convert simply open up a terminal and cd to your video directory and type 
```
ffmpeg -i name-of-your-file.flv name-of-your-new-file.mp4
```
The resulting mp4 file can be transfered via GTKPOD to your device.

**Transfering music and video:**
I personally use GTKPOD, it's the best application so far and I even have ALL (yes, all) of my album covers fully working on my 3G. I had to add some of the covers manually since I didn't have the meta-data written on them, this is why it's so convenient. It allows you to batch edit full albums.

Go to synaptic and get the package gtkpod-aac. This will allow you to transfer videos through GTKPOD since it's the same gtkpod package with mp4 and aac transfer capabilites, reason why it's more convenient than the normal gtkpod package.

**Managing your music:**
My two favorite programs are Songbird and Banshee. Both for their user interface and for their ability to get album art. Each album I download through songbird gets its album art fetched automatically and I don't need to edit it later (the meta-data) on GTKPOD. I think that it was unnecessary to add this last part, but I still did :P

**For Songbird Users:**
Songbird remote is a great application, it allows you to control Songbrid through your iPhone or iTouch. I personally use it, So if you can, give it a try. NOTE THAT it only controls songbird, it doesn't allow you to sync your music to the iPhone or iTouch.

**Ubuntu Look and Feel**
The repos of BigBoss and ModMyi have nice ubuntu themes (for winterboard), check them out.
Also, be sure to check out fontswap, ubuntu categories and ubuntu titling font, all of these available on cydia on the BigBoss and ModMyi repos. They will make your phone look and feel a lot like ubuntu.

**Jamendo is always Good:**
I actually have 2 full albums downloaded from Jamendo on my 3G and other songs, so it's a nice way to discover music. Try it, you'll find yourself buying less music on iTunes and supporting more independent artists.

**when wall charging**:
remember that your device actually heats up while wall charging, and even more when the screen is on and the wifi (many people do this to sync), so don't leave your iPhone connected to the wall for more than the necessary time, and if you're syncing wirelessly, install insomnia through cydia, this reduces A LOT the temperature when syncing over SSH and wall charging.

Happy syncing =)

---

### Post by jpeddicord on 2009-05-13
Nice set of tips; approved and thank you for your contribution.

---

### Post by Ryuki_NdranC on 2009-05-13
Thanks for the tips, i knew some, but i didn't knew that now the sync with songbird can be done perfectly (as you seem to say) without itunes. I guess i'll give it a try, the only thing that bothers me is the ssh sync... is soooo slow, and my ipod touch 2G data is over 21 GBs last time i checked.

I read somewhere now its possible to use itunes under virtualbox and get it sync via USB perfectly, have you ever tried this? What are your thoughs about it?

---

### Post by xrecar on 2009-05-13
@jacobmp92 Thanks a lot =)

> **Ryuki_NdranC said:**
> Thanks for the tips, i knew some, but i didn't knew that now the sync with songbird can be done perfectly (as you seem to say) without itunes. I guess i'll give it a try, the only thing that bothers me is the ssh sync... is soooo slow, and my ipod touch 2G data is over 21 GBs last time i checked.

You're welcome.
No, the sync can't be done yet in songbird, not with the iPhone or iTouch, or at least not over SSH. I do, however, manage my music collection with songbird since it writes the meta-data on the songs (including album art) and this way I don't have to manually edit later over GTKPOD. GTKPOD is the best app so far to manage the iPhone and iTouch in my opinion.

On the other hand, there is a team already working on syncing the iPhone and iTouch with libiphone and ifuse, a driver being developed to sync without SSH and over the cable, which will probably allow syncing via cable with other programs such as songbird, rhythmbox and banshee. In the current state it supports syncing of your data.

> **Ryuki_NdranC said:**
> 
I read somewhere now its possible to use itunes under virtualbox and get it sync via USB perfectly, have you ever tried this? What are your thoughs about it?

Yes, it is possible and I've read about many users doing this, however, I haven't tried it. If you ever try it, I'd like the feedback.

One more thing: I like your forum signature.

---

### Post by Ryuki_NdranC on 2009-05-14
[QUOTE=xrecar]You're welcome.
No, the sync can't be done yet in songbird, not with the iPhone or iTouch, or at least not over SSH. I do, however, manage my music collection with songbird since it writes the meta-data on the songs (including album art) and this way I don't have to manually edit later over GTKPOD. GTKPOD is the best app so far to manage the iPhone and iTouch in my opinion.[/QUOTE]

Oh then i totally misread what you said. You use songbird as a music database-like manager and use GTKPOD for the actual syncing? I'm sorry if i seem a little bit off, but i just got my ipod touch 2g and a new laptop (installing ubuntu jaunty right now) and so far i just know the theoretical part of my soon to be itouch under linux experience.

I must ask though... I'm a neat freak with a big OCD when it comes to have all my music and videos organized with all sort of meta-tags and album arts etc. Is songbird gonna be able to deliver in the same (or better) way that itunes does? and if so, will GTKPOD allow me to sync that to my itouch in the exact same way it is set in songbird?

[QUOTE=xrecar]On the other hand, there is a team already working on syncing the iPhone and iTouch with libiphone and ifuse, a driver being developed to sync without SSH and over the cable, which will probably allow syncing via cable with other programs such as songbird, rhythmbox and banshee. In the current state it supports syncing of your data.[/QUOTE]

That would make my year.

[QUOTE=xrecar]Yes, it is possible and I've read about many users doing this, however, I haven't tried it. If you ever try it, I'd like the feedback.[/QUOTE]

I'm going to do just that plus GTKPOD/songbird combo and see the whole pros/cons chart, probably is gonna take me a week (on finals right now) but i will. Expect my reply.

[QUOTE=xrecar]One more thing: I like your forum signature.[/QUOTE]

This old thing? ;) I had a bunch of them written down somewhere, but i lost it, don't mean to sound like such a fanboy, but it's my little way to blow off some steam after a day with vista.

---

### Post by switch10 on 2009-05-14
thank you so much for this!!  now i dont need windows at all anymore!!

---

### Post by lost_soul on 2009-05-14
Hello,

For the record I was able to Sync without errors using Itunes via Winxp running on my VirtualBox 2.2.2.
Also I was able to flash the Rom and update the Software, however Quickpwn did not function, when checking the readme file it stated having issue with virtual environments.

So yes you can sync via virtualBox and can upgrade your software, but no jailbreaking.

---

### Post by xrecar on 2009-05-14
> **Ryuki_NdranC said:**
> Oh then i totally misread what you said. You use songbird as a music database-like manager and use GTKPOD for the actual syncing?
Excatly

> **Ryuki_NdranC said:**
> 
I'm sorry if i seem a little bit off, but i just got my ipod touch 2g and a new laptop (installing ubuntu jaunty right now) and so far i just know the theoretical part of my soon to be itouch under linux experience.
Oh, excellent. Jaunty is Great!

> **Ryuki_NdranC said:**
> 
I must ask though... I'm a neat freak with a big OCD when it comes to have all my music and videos organized with all sort of meta-tags and album arts etc. Is songbird gonna be able to deliver in the same (or better) way that itunes does? and if so, will GTKPOD allow me to sync that to my itouch in the exact same way it is set in songbird?

Yes, as far as I know, songbird fetches album data from various sources, which means that if it can't find it on last.fm, for example, it will search another source. And if it doesn't find the info, It allows you to manually edit it.

And yes, GTKPOD does allow you to sync it in the exact way, and, if for any reason anything goes wrong, you can manually edit it later, and batch-edit a full album too.

> **lost_soul said:**
> Hello,
So yes you can sync via virtualBox and can upgrade your software, but no jailbreaking.

Oh, thanks for the 411

---

### Post by rob356 on 2009-05-14
> [quote]On the other hand, there is a team already working on syncing the iPhone and iTouch with libiphone and ifuse, a driver being developed to sync without SSH and over the cable, which will probably allow syncing via cable with other programs such as songbird, rhythmbox and banshee. In the current state it supports syncing of your data.
That would make my year.[/quote]

This will be even easier to do with the 3.0 software, because the new API's allow music library access, and allow dock connector access, so all one would need to do is create an app that would talk to songbird/rhythmbox/banshee. That wouldn't even require jailbreaking. :D

---

### Post by xxxfresca on 2009-05-14
Plenty of useful tips in there as promised. I was thinking about buying an iPhone.

---

### Post by lmicu on 2009-05-14
I connected my iphone with gtkpod-aac and I see th iphone but I can't sync anything, meaning I can't see the songs that were written on iphone in my "ipod" program. Does the gtkpod makes the songs visible in ipod part of the iphone?

I have Jaunty Jackalope and the GTKPOD is 0.99.14

Any ideas?

PS: When I hit save I get "could't find the ipod firewire id"

---

### Post by xrecar on 2009-05-15
> **lmicu said:**
> I connected my iphone with gtkpod-aac and I see th iphone but I can't sync anything, meaning I can't see the songs that were written on iphone in my "ipod" program. Does the gtkpod makes the songs visible in ipod part of the iphone?

I have Jaunty Jackalope and the GTKPOD is 0.99.14

Any ideas?

PS: When I hit save I get "could't find the ipod firewire id"

Hmm... if you can see it, this means that you have already mounted your iPhone. Have you changed the DBVersion key? 
Are you able to see the iPhone mounted as a removable storage device?

---

### Post by lmicu on 2009-05-16
> **xrecar said:**
> Hmm... if you can see it, this means that you have already mounted your iPhone. Have you changed the DBVersion key? 
Are you able to see the iPhone mounted as a removable storage device?


I can not see my iphone as a mass storage device, I can see it in $/media/ipod but i can only see few folders and cannot really change it. 
I did change my DBVesrion key to 2 by following this link 

[http://gtkpod.wikispaces.com/Sysinfo+File#iPhoneiTouch](http://gtkpod.wikispaces.com/Sysinfo+File#iPhoneiTouch) 

I am still unable to sync my songs on my iPhone. I do not recevice the error anymore, just that after gtkpod says it's all synced I am going in the iPod app and ... no songs.

PS: For a while my iPod start crashing (the app) and I could not even started it, but them I went and deleted the contents of the folder on my iPhone ( /private/var/mobile/Media/iTunes_Control/iTunes ) and since then it is working, I did check to see if this changed the DBVersion key back to 4 but it did not, it is still 2.

---

### Post by Ryuki_NdranC on 2009-05-16
> **lost_soul said:**
> Hello,

For the record I was able to Sync without errors using Itunes via Winxp running on my VirtualBox 2.2.2.
Also I was able to flash the Rom and update the Software, however Quickpwn did not function, when checking the readme file it stated having issue with virtual environments.

So yes you can sync via virtualBox and can upgrade your software, but no jailbreaking.

I can confirm this now. :D Tried with windows xp performance edition on my vbox and the sync was flawlessly. It seemed a little slow though, but i'm not sure, might be just me. Took me about 2 hours of syncing to transfer about 15 GB of music and videos over the usb cable... i'm not so sure if this is normal, i might try again in a friend's pc later (with vista).

---

### Post by lost_soul on 2009-05-17
Regarding the slow transfer rate, I thought I was the only one with that problem (since i've set the RAM to 384 MB) thought that was the issue.. 
I guess something is going on, btw on VirtualBox you can set filters for the USB so it will detect your Iphone automatically instead of choosing it to connect.

---

### Post by Ryuki_NdranC on 2009-05-18
> **lost_soul said:**
> Regarding the slow transfer rate, I thought I was the only one with that problem (since i've set the RAM to 384 MB) thought that was the issue.. 
I guess something is going on, btw on VirtualBox you can set filters for the USB so it will detect your Iphone automatically instead of choosing it to connect.

Thx for the tip although i already knew that... I don't know why some USB devices like my external HDD are gray-out but that's complitely off topic :).

Regarding the ram... well i don't know if it has anything to do with it but i have 2 GB of ram assigned to the guest vbox. I haven't really gotten too much into it since im investigating other stuff atm.

---

### Post by Ryuki_NdranC on 2009-05-18
This seems rather pointless by now since i'm on the verge of giving up. Consider this reply as an "omg... really????" question.

I successfully mounted my ipod touch 2g with ipod-convenience and changed my DBversion (or w/e) to 2 (so i can sync with 2.x firmware), but i find myself really disappointed on the fact that there is absolutely no way to sync other than using amarok or gtkpod...

Really???

Not even a clue that someone out there is working on it. I personally try to stay away from kde apps when im on gnome (besides i tried amarok 2 and was all buggy and couldn't play any music from my pc).

I was growing fond of banshee and even songbird... /sigh too bad.

---

### Post by Ryuki_NdranC on 2009-05-19
lawl.... yeah just what i need.... a windows app to substitute another windows app.

---

### Post by spacemind on 2012-03-28
Hi there 

"For Songbird Users:
Songbird remote is a great application, it allows you to control Songbrid through your iPhone or iTouch. I personally use it, So if you can, give it a try. NOTE THAT it only controls songbird, it doesn't allow you to sync your music to the iPhone or iTouch."


Anyone has this working ? songbird under ubuntu 10.04 and the songbird remote in iphone ?

I cant get it working.

---

### Post by howefield on 2012-03-28
Old thread closed.

Please start a new thread if required.

---

