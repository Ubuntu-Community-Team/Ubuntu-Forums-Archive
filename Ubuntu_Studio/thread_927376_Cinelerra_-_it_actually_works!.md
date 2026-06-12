---
title: "Cinelerra - it actually works!"
date: 2008-09-22
forum: Ubuntu Studio
---

### Post by gali98 on 2008-09-22
As most older users know, cinelerra is a non-linear video editor for linux.
When it works, it has a lot of very good features not found even in commercial products.
I wasn't sure if most people knew, but Heroine Virtual released version 4 of cinelerra, and it just works.
Here is the link.
[http://www.heroinewarrior.com/cinelerra.php](http://www.heroinewarrior.com/cinelerra.php)
(this link has been down. download here...) It's back! I think they update their site...
This is still another link to the download:
[http://sourceforge.net/project/showfiles.php?group_id=13554&package_id=50184&release_id=619071](http://sourceforge.net/project/showfiles.php?group_id=13554&package_id=50184&release_id=619071)
It has a download section for 32 and 64bit ubuntu packages. Now there is only one package that you just extract and run.
Did I mention it works? :)

So if some of you newer ones are finding the present video editors for linux lacking, you might try it.
Though it does have a steep learning curve, it has amazing features.

Also here is a little tidbit of info you might want to keep an eye on.
The reason Cinelerra has always been buggy is because most distros will not support it. The reason being the story behind the source code is kind of shady. The online company calling itself heroine virtual releases the source, but it can't really be confirmed and it has caused controversy.
The community of cinelerra has its own branch of code. What finally happened is that the community decided to start over from scratch. This is very good, because while it may take a few years for it to mature, it will be a lot better supported, and we won't have to worry about code licensing.
If you want to check it out, here is the very beta site:
[http://lumiera.org/index.html](http://lumiera.org/index.html)
And here is the community site for Cinelerra:
[http://cinelerra.org/](http://cinelerra.org/)

Just thought I would let y'all know, that despite its hard past, cinelerra works pretty well now. Enjoy!
Kory

---

### Post by Erlander on 2008-09-23
Will Cenelerra accept AVCHD from a high definition hard disc video camera?

Rob

---

### Post by gali98 on 2008-09-23
Best thing to do would be to check at the community site. I have not used cinelerra much, I only know a bit about it. My guess is probably.. The only way to really know is to try :)
Kory

---

### Post by rylleman on 2008-09-24
Yes, it actually works pretty well now.
I've been testing CinelerraCV on my 64-bit Ubuntu Studio for the last few nights without a single crash! Always in the past when I've tried it out I've given up after an hour or so because it crashed so frequently.
Now I can really try it in depth to see what it actually can do, exciting.
But why does it have to be so ugly!? It's like a scarecrow of video editors. Horrible...

---

### Post by cotcot on 2008-09-24
> **Erlander said:**
> Will Cenelerra accept AVCHD from a high definition hard disc video camera?

Rob
Is not possible. I convert them to .avi.

I tried the version 4 mentioned by the 1st poster.
On 32 bit it failed.
On 64 bit it seems OK except for my avi's of 1440x1080. Its is the format I use converting my avchd's. 
So I stick to blender VSE.

---

### Post by gali98 on 2008-09-24
What do you mean by failed?
I use 64bit and it works great!
It is pretty ugly :) But I kinda like the green myself....
My whole point in this post was for the many people who had given up on cinelerra in the past because it was too buggy to have another chance at it..
Kory

---

### Post by cotcot on 2008-09-25
Failed means that cinelerra could not start. Meanwhile I found out why. I renamed .bcast that belongs to the cinelerra version I compiled myself (and works very good, without crashing) so that the version 4 could create a new .bcast. Now it runs fine.

I fully agree with your point that this version 4 makes seems to be a good answer on a common critic that cinelerra is sensitive to crashing.

---

### Post by gali98 on 2008-09-25
Glad you got it working!
Kory

---

### Post by skullmunky on 2008-09-25
Wow, it does!  At least better than previous versions.  I did freeze it after about 5 mins just doing some regular editing tasks like scrubbing and moving clips.  But still, getting better!

I'd be interested to hear success stories from people who have done editing work with cinelerra.  As inspiration. :)

---

### Post by Crafty Kisses on 2008-09-26
Glad to hear you got it working! :)

---

### Post by cor2y on 2008-09-26
It hasn't crashed once but i do have the problem of no audio playback when previewing clips but it renders out correctly with audio so i assume its a pulse audio thing, pulse audo manager doesn't list cinelerra when cinelerra is running and i have this message via the terminal.
> 
Cinelerra 4 (C)2008 Adam Williams

Cinelerra is free software, covered by the GNU General Public License,
and you are welcome to change it and/or distribute copies of it under
certain conditions. There is absolutely no warranty for Cinelerra.
AudioOSS::open_output: Device or resource busy
SNDCTL_DSP_SETFRAGMENT 2 failed.
SNDCTL_DSP_SETFMT 2 failed
SNDCTL_DSP_CHANNELS 2 failed
SNDCTL_DSP_SPEED 2 failed
AudioOSS::open_output: Device or resource busy
SNDCTL_DSP_SETFRAGMENT 2 failed.
SNDCTL_DSP_SETFMT 2 failed
SNDCTL_DSP_CHANNELS 2 failed
SNDCTL_DSP_SPEED 2 failed
AudioOSS::open_output: Device or resource busy
SNDCTL_DSP_SETFRAGMENT 2 failed.
SNDCTL_DSP_SETFMT 2 failed
SNDCTL_DSP_CHANNELS 2 failed
SNDCTL_DSP_SPEED 2 failed

And this error on launch
> 
MWindow::init_shm:/proc/system/kernel/shmmax is 0x2000000
It should be at least 0x7ffffff for Cinelerra

---

### Post by p221072 on 2008-09-26
Yes, it's true it works but thee are few ascpects that really annoy me.
The worst is that you cannot render to mpeg2 dvd compliant with audio and video multiplexed.
You have to do 2 separate export and then join them using ffmpeg from command line! (thus adding antother rendering passage)
Do you think this is normal for it shoould be a mature project?

---

### Post by paulmerchant on 2008-09-26
> **p221072 said:**
> Yes, it's true it works but thee are few ascpects that really annoy me.
The worst is that you cannot render to mpeg2 dvd compliant with audio and video multiplexed.
You have to do 2 separate export and then join them using ffmpeg from command line! (thus adding antother rendering passage)
Do you think this is normal for it shoould be a mature project?

From my experience, it's normal on at least a few other NLE's to export audio and video separately when going to mpeg2. This is because the next step is usually not multiplexing them with ffmpeg, but compiling an actual DVD.

---

### Post by gali98 on 2008-09-26
@cor2y
you might try running 
padsp cinelerra

and one of the things with cinelerra is that this version (the one that works) comes from the company itself. They clearly state that they will develop what they need, and that is it. They will release the source, but they won't develop what they need.
You may be able to some of the stuff you are talking about in the community version.
I can't wait until the cinelerra rewrite comes out. But that will be a while.....
Kory

---

### Post by gali98 on 2008-10-04
Bump! (Just wanted to let people know :))tx2
I think a lot of people gave up on cinelerra a forgot about it.
Kory

---

### Post by roaldz on 2008-10-05
Looks like [http://www.heroinewarrior.com/](http://www.heroinewarrior.com/) is down now..

---

### Post by gali98 on 2008-10-05
It sure is.... hmm... if someone needs me to, I can upload the file.
Kory

Edit:Never Mind.. the packages are still on sourceforge here:
[http://sourceforge.net/project/showfiles.php?group_id=13554&package_id=50184&release_id=619071](http://sourceforge.net/project/showfiles.php?group_id=13554&package_id=50184&release_id=619071)

---

### Post by eldragon on 2008-10-05
ive downloaded the cinelerra-cv a couple of days ago to find out the interface will freeze after a couple of minutes. 

is this the release you are talking about? or is the cinelerra4 a newer version?

---

### Post by roaldz on 2008-10-06
Cinelerra4 has crashed on me already, it has trouble loading videos. Videos I made with cinelerra!
Does someone know if it´s needed to compile and install the libmpeg3 and quicktime4linux libs?

---

### Post by gali98 on 2008-10-12
@eldragon

No.. I think what you are referring to the communtity version.
Just follow this link and download it.
[http://sourceforge.net/project/showfiles.php?group_id=13554&package_id=50184&release_id=619071](http://sourceforge.net/project/showfiles.php?group_id=13554&package_id=50184&release_id=619071)
just download the i686 or amd64 package. (second and third package on that page)
and unzip it. It is already built.
run the binary "cinelerra" in the folder that you unzip and thats it.
If you don't want a random folder on you desktop, I suggest putting it in /opt then creating a shortcut to it or something.

@roaldz
As far as I can guess, you should not have to compile anything. I think they are statically linked in this package.
Did you follow the steps above?
Kory

---

### Post by eldragon on 2008-10-15
> **gali98 said:**
> @eldragon

No.. I think what you are referring to the communtity version.
Just follow this link and download it.
[http://sourceforge.net/project/showfiles.php?group_id=13554&package_id=50184&release_id=619071](http://sourceforge.net/project/showfiles.php?group_id=13554&package_id=50184&release_id=619071)
just download the i686 or amd64 package. (second and third package on that page)
and unzip it. It is already built.
run the binary "cinelerra" in the folder that you unzip and thats it.
If you don't want a random folder on you desktop, I suggest putting it in /opt then creating a shortcut to it or something.

@roaldz
As far as I can guess, you should not have to compile anything. I think they are statically linked in this package.
Did you follow the steps above?
Kory

same problems with that version, i think its related to a cinelerra bug related to newer libc6 libraries....

---

### Post by Bartje on 2008-10-16
I'll wait for lumiera... and if that doesn't work, maybe I'll give it yet another try. In the mean time... Blender...

---

### Post by gali98 on 2008-10-16
Yes Blender is also very awesome!
The movie editor is often an overlooked feature.
It's interface is a bit old and confusing, but it has some really cool features.
I have actually been playing with realtime cloth and softbody physics the last few days
[http://www.blender.org/features-gallery/feature-videos/?video=realtime_cloth](http://www.blender.org/features-gallery/feature-videos/?video=realtime_cloth)
Its really fun...
Kory

---

### Post by gali98 on 2008-11-01
bump!

---

