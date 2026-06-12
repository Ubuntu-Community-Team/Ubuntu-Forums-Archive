---
title: "Rosetta Stone is it possible on ubuntu ?"
date: 2010-02-09
forum: Wine
---

### Post by verachion on 2010-02-09
I am almost there with this new operating system just one hurdle to go, one that I have been putting off until now. 

I am currently doing a language course in Spanish and I am using a programme called Rosetta Stone, the exe file and the language disks are on ISO's is there any way of installing these iso's using a virtual drive. I have been using alcohol soft on windows.

First question is: How can I install the application launcher of rosettta stone on ubuntu via an iso ?

---

### Post by NCLI on 2010-02-09
> **verachion said:**
> I am almost there with this new operating system just one hurdle to go, one that I have been putting off until now. 

I am currently doing a language course in Spanish and I am using a programme called Rosetta Stone, the exe file and the language disks are on ISO's is there any way of installing these iso's using a virtual drive. I have been using alcohol soft on windows.

First question is: How can I install the application launcher of rosettta stone on ubuntu via an iso ?

Install gmount-iso from the Software Store ;)

IIRC, Rosetta Stone works fine under Linux, using Wine(Also availible in the Software Center). You can check compatibility [here]("appdb.winehq.org").

---

### Post by verachion on 2010-02-09
> **NCLI said:**
> Install gmount-iso from the Software Store ;)

IIRC, Rosetta Stone works fine under Linux, using Wine(Also availible in the Software Center). You can check compatibility [here]("http://appdb.winehq.org").

I have installed Rosetta using wine, and I have now used gmount for the language disks, how do I point rosetta stone to the language disks? at the moment it is saying that it can't find them?

---

### Post by achase79 on 2010-02-09
in the winecfg program set up a new drive setting pointing a drive letter to the mountpoint of the iso.

---

### Post by verachion on 2010-02-09
> **achase79 said:**
> in the winecfg program set up a new drive setting pointing a drive letter to the mountpoint of the iso.

AT the moment the mounted iso is in documents 'mounted rosetta level 3 iso' folder, I went in to winecfg and created a new drive (E) I pointed it to the folder in my documents however, still no luck in finding it? what am I doing wrong

---

### Post by achase79 on 2010-02-09
did you set the cdrom setting for that e: drive?  You may also have to enter the id information for the cdrom in that area as well.

---

### Post by verachion on 2010-02-10
> **achase79 said:**
> did you set the cdrom setting for that e: drive?  You may also have to enter the id information for the cdrom in that area as well. 

Could you or anyone tell me how to do this and let me know what the id information is, again I have been on ubunu for less than a week I do not understand these things yet. If you/anyone could show me I would appreciate it.

---

### Post by verachion on 2010-02-10
I am trying to install Rosetta Stone language pack on to ubuntu 

I have done the following:

1. **Mounted an ISO to my documents using Gmount-ISO**
2. **I have gone in to winecfg and created a couple of cdrom drives** (as in the screenshot) 

Now, I need to point rosetta stone application to the ISO so that it can load the languages. How do I do this?

Its simple when you know how.

---

### Post by verachion on 2010-02-10
I have installed Rosetta Stone, and tried to use my headset, my microphone works but I don't have any sound? does anyone have any idea how to rectify this at all ?

---

### Post by cariboo on 2010-02-11
Please don't create multiple threads about the same problem. I have merged your 3 threads.

---

### Post by lindude on 2010-05-17
In Ubuntu 10.04, Rosetta Stone V3.3.7 works fine in Wine 1.1.44 except for the microphone! 
This is a know bug in wine for a long time.
[Bug 14559 -  Rosetta stone v3 microphone detection]("http://bugs.winehq.org/show_bug.cgi?id=14559")
So it's not really much use.
From what I've read it seems to has something to do with pulseaudio, (I could be wrong about that).

---

### Post by andrea000 on 2010-05-18
My mic works fine in wine 1.1.42

---

### Post by lindude on 2010-05-18
> **andrea000 said:**
> My mic works fine in wine 1.1.42

could you please explain how you set it up?
Thanks

---

### Post by mellowtothemax on 2010-05-19
This is what I did to get it working.

If you have the cds inserted then wine should automatically pick them up.  

If you are using .iso files then you need to mount the image using loop option.  I used furious iso mount and has the option loop or fuse.  You will notice a new directory in your home folder.

I then run winecfg and under 'drives' tab choose a new drive and point to the directory in your home folder that furious iso mounted.

For each language cd you need to do this seperately.  Just point the drive letter in winecfg to the new directories.

Every time you run winecfg make sure Rosetta application is closed.

The microphone works fine for me.

---

### Post by lindude on 2010-05-19
Hi mellowtothemax,
I had no problem installing it everything installed fine. Sound work's it's just the mic wont work.
I installed it all via cd didn't need to do anything with winecfg.
I have tried playing with the audio setting in winecfg to make the mic register.
If I switch the sound drivers in winecfg for ALSA to OSS, Rosetta recognizes that there is the USB mic but not the built in one, but still no sounds come through it.
I have play with all the different possible combination of setting in the sound preferences, switching between the "input" options and "choose a device to configure", but nothing. The levels in the sound preferences show that sounds are coming in through the the USB and built in mic's but for some reason Rosetta cant get the sounds even when it recognizes there is a mic.
Thanks

---

### Post by mellowtothemax on 2010-05-19
My laptop has a built in mic and was picked up by rosetta app.

I am assuming the mic works with other applications on your system, but if not try playing around with alsamixer (specifically mic section).

Install 'gnome alsa mixer','pulse audio device chooser' and 'pulseaudio volume control' for additional control over your sound devices.

Also make sure you have the latest version of wine.  It is recommended to use playonlinux to install window programs for beginners because if something is messed up in the wine configuration you can just delete the culprit prefix without affecting the other applications.

I cannot guarantee that this will work because as I said I didn't have audio problems.

Ubuntu 10.04 Dell Studio XPS 1640

---

### Post by lindude on 2010-05-19
Thanks for your advice mellowtothemax.
I was enjoying not having pulseaudio volume control, I had it on 9.10 and before. I did install it for a quick play but couldn't get it to work either. 
I'll install it again as well as 'gnome alsa mixer', and reinstall rosetta via playinlinux. 
See how things go then.
Cheers

I'm using Ubuntu 10.04 on a Dell XPS M1210.

---

### Post by mellowtothemax on 2010-05-19
This is what shows up on the preferences panel within Rosetta.  See attachment.

'Front mic' is the camera integrated one for me.

---

### Post by lindude on 2010-05-20
Thanks again mellowtothemax,
I tried removing wine and using POL bu still no joy, I couldn't get it to recognize any mic's so I went back to Wine. The 2 mic's are recognized but neither will work. Th first, (even thought it says USB), is the built in mic the second is the Headset mic.
I hope you can use .png pic's

file:///home/beefcake/Documents/Rosetta%20Stone%20Version%203_001.jpeg
[IMG]http://file:///home/beefcake/Documents/Screenshot-Rosetta%20Stone%20Version%203.png[/IMG]
[IMG]http://file:///home/beefcake/Documents/Rosetta%20Stone%20Version%203_001.jpeg[/IMG]

I guess I'll look a little more then look into a virtual windows system.
Thanks

---

### Post by andrea000 on 2010-05-20
> **lindude said:**
> could you please explain how you set it up?
Thanks
It worked as soon as i installed Rosetta stone all i
had to do was the male female set up in Rosetta stone
and Rosetta stone should ask you to do that.thats all
i done.

---

### Post by lindude on 2010-05-20
Hi andrea000,
Yeah, it asked me that. Sound works shows the mic as there it just won't work, the mic shows sound coming through in the sound settings.

---

### Post by lindude on 2010-05-20
See attachment.

Hi mellowtothemax,
Could you please tell me how you were able to add the pic to your post. 
I tried but with no joy.
I took screen shot in png and jpeg and dropped them into the, "insert image" tool but neither seem to work.
I also tried dropping the pic straight into the post.
Thanks

---

### Post by mellowtothemax on 2010-05-20
Attach files using the 'manage attachments' further down on the 'reply to thread page'.

I understand your problem, which is very strange.  Does the microphone work with any other application?

---

### Post by lindude on 2010-05-20
Hi mellowtothemax,
Thanks before mentioned pic attached.

The mic's both works fine in skype and they both show to be picking up sounds in the sound in the, "sound preferences".

---

### Post by mellowtothemax on 2010-05-20
Sorry I really do not know what the cause of this is, it is above my level of expertise.

I just know from past experiences that if something doesn't work straight away as it should in wine it can be a nightmare to pin point the problem.  

I can imagine that there could be a problem if you have updated Ubuntu from previous releases and wine has been somehow corrupted.

or

There could be a problem with the specific hardware on the machine and compatibility with the audio driver that only affects wine.

Maybe ask for help at winehq. 

Have you tried running it through a virtual machine?

---

### Post by Grenage on 2010-05-20
When I installed it on my machine, I encountered the same problem.  Eventually I found a blog that gave a few lines of terminal code, and that fixed it right away.  I have not been able to find the blog, I've just looked.

I considered not posting, but I'm just letting you know that it's definitely possible.

---

### Post by lindude on 2010-05-20
Hi Grenage,
Thanks for your post, i you do happen to come accross it please post a link.
Thanks

---

### Post by lindude on 2010-05-20
Hi  mellowtothemax,
I did have an upgrade to 10.04, it was so buggy I a fresh install. When I did the fresh install I thought I'd get rid of my window partition because of all the positive things I'd read about wine and Rosetta. Rosetta was the only reason I had the windows partition. 
I dig a little deeper into the wine problem thanks to Grenage's post. If still no joy I guess I'll be looking into a virtual machine. 
Thanks

---

### Post by tango_ninja on 2010-05-21
> **lindude said:**
> Hi Grenage,
Thanks for your post, i you do happen to come accross it please post a link.
Thanks

I'm still trying to make my Rosetta Stone mic work via WINE as well and have another thread set up.... however, in my searches I have found a few methods that seem to work for others.  Check out this thread for more info: [http://ubuntuforums.org/showthread.php?t=1489077](http://ubuntuforums.org/showthread.php?t=1489077)

One of these fixes may work for you.

---

### Post by prince.buster on 2010-06-24
a bug report for the microphone problem may be found [here]("http://bugs.winehq.org/show_bug.cgi?id=14559"). please register and vote for the bug - this will contribute to it being fixed by the wine developers ASAP

---

