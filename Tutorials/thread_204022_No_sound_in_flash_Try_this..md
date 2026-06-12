---
title: "No sound in flash? Try this."
date: 2006-06-26
forum: Tutorials
---

### Post by calx on 2006-06-26
After weeks of searching for a solution, this has finally got sound in flash working for me. :-D 

[https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/29760]("https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/29760")


# Flash also looks for /usr/lib/libesd.so.1
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

# Flash expects /tmp/.esd/socket to exist.
sudo mkdir -p /tmp/.esd/
sudo touch /tmp/.esd/socket

---

### Post by Dr. Nick on 2006-06-26
Thanks for this,

I was sorta stumped as to why sound worked in firefox but not epiphany. That fixed it all up for me

---

### Post by mustang on 2006-06-26
Oh my god! You are my saviour!!! I have tried for hours and I always got choppy sound when playing flash video. It is **finally** fixed. I can now watch youtube and google videos without having to download them and convert. 

Thank you so much calx. You made my day!

---

### Post by flibble on 2006-06-26
Yeeee Haaaaaaa! I've read so many posts about this, including all the "can't be fixed, wait for flash 9, yadda yadda". This fix works perfectly for me on dapper. Now I can watch all that pointless, moronic flash content! Thank you.

---

### Post by souled on 2006-06-26
I'm currently using this asound.conf to get my optical out working: ```
pcm.!default {
        type plug
        slave.pcm "dmixer"
}

pcm.dmixer  {
        type dmix
        ipc_key 1024
        slave {
                pcm "hw:0,1"
                format S32_LE
                period_time 0
                period_size 1024

# increased buffer_size because in my system 1024 cause bad
# audio performance (for totem media player and mplayer)
                buffer_size 8096

                rate 44100
        }
        bindings {
                0 0
                1 1
        }
}

ctl.dmixer {
        type hw
        card 0
        device 1
}

#

```

The commands provided in this howto don't enable sound for me in Flash. Can anyone help me with this?

---

### Post by bluecrayon on 2006-06-26
THANK YOU! I've tried so many different tips on this forum and this finally worked. Now to get surround sound working...

---

### Post by Dr. Nick on 2006-06-27
Very odd.

Before running this I had sound with flash in firefox but not epiphany.

After I have sound in epiphany but now no sound in firefox.

Its not a huge problem now, just a bit puzzled. Anyone notice similar, or have ideas as to a fix? I may just undo it for now since I use FF more than epiphany

---

### Post by mohasr on 2006-06-27
I also had no sound in flash videos , but I noticed that if I played some audio file in totem then watched the flash video the sound works ...

---

### Post by BlacKsheep88 on 2006-06-27
Now I can't play flash videos period

---

### Post by userundefine on 2006-06-27
Impressive work !

Edit: I'm experiencing out-of-sync audio with flash sound, it's off by about a half-second.  Anyone else getting this?

---

### Post by popdog on 2006-06-27
Excellent, this worked perfectly for me thanks!  I think in my case having two soundcards (one Audigy 2 ZS and an onboard one) caused the problems.

---

### Post by krye on 2006-06-27
Worked PERFECTLY here. Thanks a lot!!

---

### Post by BlackwaterPark on 2006-06-27
[QUOTE=userundefine]Impressive work !

Edit: I'm experiencing out-of-sync audio with flash sound, it's off by about a half-second.  Anyone else getting this?[/QUOTE]

Yeah I am too, you can notice the lag issue when you are playing something and you close the tab - the sound keeps going for that fraction of a second

---

### Post by MetalMusicAddict on 2006-06-27
Works here also.
[QUOTE=userundefine]Impressive work !

Edit: I'm experiencing out-of-sync audio with flash sound, it's off by about a half-second.  Anyone else getting this?[/QUOTE]
For me some things go out of sink but somethings dont.

---

### Post by unixping on 2006-06-28
I agree with these guys, your commands fixed the problem of getting sound. But now it's all out of sync.....anyone?

---

### Post by DTPHawk on 2006-06-28
I am currently experiencing the same problem. I was browsing videos at youtube.com and noticed a sync problem immediatly. Hope we see a fix soon. Thanks alot

---

### Post by markmark on 2006-06-28
[QUOTE=DTPHawk]I am currently experiencing the same problem. I was browsing videos at youtube.com and noticed a sync problem immediatly. Hope we see a fix soon. Thanks alot[/QUOTE]Out of sync sound in flash has been a problem for a loooooooong time. [This]("http://ubuntuforums.org/showthread.php?t=186594") is a solution that worked for some people.

---

### Post by kjkrum on 2006-06-28
[QUOTE=userundefine]Edit: I'm experiencing out-of-sync audio with flash sound, it's off by about a half-second.  Anyone else getting this?[/QUOTE]

Yes.  But I also get the exact same problem with Firefox on WinXP.

---

### Post by Xzallion on 2006-06-28
This didn't work for me. :(

---

### Post by monomaniacpat on 2006-06-29
I tried the aoss solution but couldn't get it to load with firefox automatically. This worked first time - thanks!:grin:

---

### Post by spockrock on 2006-06-29
this works thank you so much!

---

### Post by spockrock on 2006-07-04
ok I have to do this everytime I reboot anyway I can do this without having to do it everytime at I restart ubuntu?

---

### Post by nrayever on 2006-07-15
it's not working for me. i have a intel hda sound card on my laptop, and i have to restart firefox several time before listening to flash sound.

---

### Post by Polygon on 2006-07-16
> **spockrock said:**
> ok I have to do this everytime I reboot anyway I can do this without having to do it everytime at I restart ubuntu?

i also have to re-enter the commands every time i reboot, oh well, 1 minutes is enough to have flash working again!

---

### Post by CronoDekar on 2006-07-16
Try putting the commands in /etc/rc.local to get it working on bootup .  I had got a different set of instructions which got Flash sound working for me (though still with frequent lag), and this is what I put in it:

mkdir /tmp/.esd ln -s /tmp/.esd-1000/socket /tmp/.esd/

---

### Post by lnicolao on 2006-07-31
Great solution!
Changing firefox config to aoss or calling "aoss firefox %u" would eventually crash my FireFox. This seems to be working so far.

---

### Post by mkquist on 2006-08-28
[-o<  just a quick Thankyou, that much closer to being all sorted out..  \\:D/

---

### Post by rko618 on 2006-08-28
I only get no sound in flash if I am running another application that has sound (like a music player). If I close the music player and restart firefox then flash sound usually works.  Will this fix my problem?

---

### Post by Scythe!? on 2006-08-28
> **userundefine said:**
> Impressive work !

Edit: I'm experiencing out-of-sync audio with flash sound, it's off by about a half-second.  Anyone else getting this?

Yep, I'm getting out of sync audio too.

---

### Post by Scythe!? on 2006-08-28
> **CronoDekar said:**
> Try putting the commands in /etc/rc.local to get it working on bootup .  I had got a different set of instructions which got Flash sound working for me (though still with frequent lag), and this is what I put in it:

mkdir /tmp/.esd ln -s /tmp/.esd-1000/socket /tmp/.esd/
How do I put the commands into /etc/rc.local? what do i have to do?

---

### Post by cvmostert on 2006-08-30
> **calx said:**
> After weeks of searching for a solution, this has finally got sound in flash working for me. :-D 

[https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/29760]("https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/29760")


# Flash also looks for /usr/lib/libesd.so.1
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

# Flash expects /tmp/.esd/socket to exist.
sudo mkdir -p /tmp/.esd/
sudo touch /tmp/.esd/socket

Thank you, it worked for me aswell... now i just have to get my screen to stop blinking when i start and stop playing a video file....

cheers

---

### Post by rynop on 2006-10-03
THANK YOU!!!! i have searched for this fix for so long its not even funny

---

### Post by VCSkier on 2006-10-05
this worked great for me.  thanks!

---

### Post by chakkid on 2006-10-21
a 1000 thanks for ya!:) :) :) i subscribed this thread, hoe you don't mind:P.

---

### Post by askreet on 2006-11-16
Worked for me, thanks a bunch!

---

### Post by uboltun on 2007-01-01
Thanks a bunch, worked for me too.

---

### Post by wilem on 2007-01-10
This worked for me as well.

<3

---

### Post by HiP.P on 2007-01-18
Cheers man worked for me

> **calx said:**
> After weeks of searching for a solution, this has finally got sound in flash working for me. :-D 

[https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/29760]("https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/29760")


# Flash also looks for /usr/lib/libesd.so.1
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

# Flash expects /tmp/.esd/socket to exist.
sudo mkdir -p /tmp/.esd/
sudo touch /tmp/.esd/socket

---

### Post by mohdridha on 2007-01-23
but my files point to other files

```

kapla@mrn: /usr/lib$ ls -l libesd*
-rw-r--r-- 1 root root   37834 2006-03-28 19:43 libesd.a
-rw-r--r-- 1 root root     833 2006-03-28 19:43 libesd.la
lrwxrwxrwx 1 root root      16 2007-01-03 04:14 libesd.so -> libesd.so.0.2.36
lrwxrwxrwx 1 root root      16 2006-12-12 05:35 libesd.so.0 -> libesd.so.0.2.36
-rw-r--r-- 1 root root   37400 2006-03-28 19:43 libesd.so.0.2.36

```

i dont have this file libesd.so.1

so i cant make this link:
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

[quote=calx]
# Flash expects /tmp/.esd/socket to exist.
sudo mkdir -p /tmp/.esd/
sudo touch /tmp/.esd/socket
[/quote]

Is this a must do thing?:confused:

---

### Post by uboltun on 2007-03-21
Worked for version 7 but vesion 9 - still no sound ...

---

### Post by dcroxton on 2007-03-24
I still get no sound.

I just discovered this way to get IE running on Linux:  [http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page).  And Flash works fine in IE -- weird.

I'm glad I have a way to view flash content in Linux now.  However, it is frustrating to have to run IE to do it.  I will be glad when this issue is sorted out.

Sincerely,
Derek

---

### Post by treeby on 2007-05-01
now i have no sound AND no video...how do i undo this? thanks anyway...

---

### Post by avelez89 on 2007-07-21
I also experienced no sound in Flash although sound seemed to worked in all other applications.

If you have 2 sound cards this might be the cause of your problem (it was the cause of mine.) I have an Intel Integrated sound card and an Audigy2 sound card. Although i had selected Audigy2 sound cards as my default through System >> Preferences >> Sound the issue still persisted.
I then had to change my default sound card through the Terminal using the following guide:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_change_default_soundcard](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_change_default_soundcard)

---

### Post by SLA_leandrin on 2007-07-29
Hi.
I've tryied everything, but the only solution that worked for me is installing PulseAudio, now flash sound works excellent in youtube.
Give it a try.

I've followed [this guide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_PulseAudio_Sound_Server")

Bye!!!:)

---

### Post by aaaantoine on 2007-08-04
> **SLA_leandrin said:**
> Hi.
I've tryied everything, but the only solution that worked for me is installing PulseAudio, now flash sound works excellent in youtube.
Give it a try.

I've followed [this guide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_PulseAudio_Sound_Server")

Bye!!!:)

The libflashsupport file they link to is for i386.  From what I've seen, there's no AMD64 version.

I tried to compile the source of libflashsupport but it requires some header files:

```

flashsupport.c:193:25: error: openssl/ssl.h: No such file or directory
flashsupport.c:218:17: error: esd.h: No such file or directory
flashsupport.c:225:26: error: pulse/simple.h: No such file or directory
flashsupport.c:226:25: error: pulse/error.h: No such file or directory

```

---

### Post by Xizorbg on 2007-09-08
Hey Guys-

This is my asound.conf-


using SPDIF cannot get sound on flash using this fixit.....

any ideas?
# asound.conf for an M-Audio Revolution and an Audigy.
# (The Audigy/emu10k1 stuff should be easy to remove if you don't need it...)

pcm.revolution {
    type hw
    card 0
}

pcm.emu10k1 {
    type hw
    card 1
}

# ICE1712 dmix:
pcm.ossmix {
    type dmix
    ipc_key 1024
    slave {
    pcm "hw:0,0"
        format S32_LE
        period_time 0
        period_size 1024
        buffer_size 9000 # buffer size < 6653, but pow(x, 2)
        rate 44100 # we want to play CDs only
    }
    bindings {
        0 0
        1 1
    }
}
#######################################
# Allow reading from the default device.
# Also known as record or capture.
pcm.dsnooper {
    type dsnoop
    ipc_key 2048
    slave.pcm "revolution"

    bindings {
    0 0
    1 1
    }
}

# This is what we want as our default device
# a fully duplex (read/write) audio device.
pcm.duplex {
    type asym
    playback.pcm "ossmix"
    capture.pcm "dsnooper"
}

pcm.softvol {
    type softvol
    slave.pcm "duplex"
    control {
        name "PCM Volume"
    card 0
    }
}
#######################################
# Everything running through softvol -> dmixed, so redefine "default":
pcm.!default {
    type plug
    #slave.pcm "ossmix"
    slave.pcm "duplex"
    slave.pcm "softvol"
    slave.pcm "spdif"
}

# OSS via aoss should d(mix)stroyed:
pcm.dsp {
    type plug
    #slave.pcm "ossmix"
    slave.pcm "duplex"
}

ctl.mixer {
    type hw
    card 0
}

---

### Post by bitwise5 on 2007-11-08
Common solution I've seen is to try and use esd; I was hoping to avoid this. I had flash working fine under fiesty, using ALSA, so why not with gusty?
Because my old config files were still hanging around my home directory. oops.
```

~$ mv ~/.asoundrc ~/.asoundrc.old
~$ mv ~/.asoundrc.asoundconf ~/.asoundrc.asoundconf.old

```

Restart firefox, that's it.

---

### Post by Defrector on 2007-11-08
ack.

I've been wrestling with this problem ever since upgrading to kubuntu 7.10. Tried the firefoxrc fix, it seemed to work, then sound in flash broke again for firefox. Thought the conf file was reverted somehow but it was the way I left it.

I tried the eossd wrapper or whatever it is called and that didn't work.

Tried some other tricks found on the forums involving linking and moving directories around... again it fixed it, then after some  everyday desktop use it randomly broke again. It's as if the fixes were one-shot and some gremlin in the system found another way to break it!

So far the #1 solution for me has been to just use Konqueror for sound-related flash. It seems to work fine in there.

... but this has gotta be fixed sometime... From what I've read in other posts, the implementors and developers are aware and working on the issue... though they all seem to have their own flavor of temporarily fixing it until the issue is ironed out!

---

### Post by Defrector on 2007-11-09
I spoke too soon. Flash sound on Konqueror just went out as well. I think it may have to do with using wine for other programs and then launching a browser, maybe with grabbing the dsp or sound daemon or something; don't know for sure. I double checked to see if flash in firefox had sound again but alas it didn't.

In a last ditch effort I got IE4Linux and am using that for flash-based stuff. It's working quite well, for now. Perhaps it is immune to the issue until the flash->firefox/mozilla sound issue irons out. Perhaps windows firefox will run in wine w/o flash sound issues too? Something to try. If THAT manages to fail then I think I need therapy. :)

---

### Post by JustAboutRealJAR on 2007-11-09
> **calx said:**
> After weeks of searching for a solution, this has finally got sound in flash working for...

Updated for Gutsy at [http://ubuntuforums.org/showthread.php?t=590989]("http://ubuntuforums.org/showthread.php?t=590989")

---

### Post by helpdeskdan on 2007-12-09
Another Thkx - worked great

---

### Post by ladgrove on 2008-02-11
For 64-bit Ubuntu users who still have no sound in Flash after trying all the aforementioned solutions, it may prove worthwhile to visit [www.alsa-project.org](www.alsa-project.org) & download & install the newest:

alsa-driver-1.0.16
alsa-lib-1.0.16 
alsa-firmware-1.0.16.

For anyone uncertain on how to do this, it's just a matter of extracting the downloaded files either graphically by right clicking on the file and choosing extract, or in the terminal by typing:

```
tar -jxvf alsa-driver-1.0.16.tar.bz2 
```

Once the files are extracted, change to the appropriate folder, there'll be 3 in this case for the driver, lib & firmware, and start by doing 

```
sudo ./configure
sudo make
sudo make install
```

This will update your alsa firmware, drivers and libraries. Also, I tried another solution, which did not work prior to doing this update, but as I now have sound for flash in 64-bit Ubuntu, I may as well include it. Edit your firefoxrc file by doing:
 
```
sudo gedit /etc/firefox/firefoxrc
```

and edit the line that says

```
FIREFOX_DSP=""
```
 
to
```

FIREFOX_DSP="aoss"
```

Again, I'm not sure this is actually helping, but as it worked for my setup, it may as well be mentioned. 

Then, in Menu/Preferences/Sound, choose autodetect or manually select your soundcard and reboot.

Hopefully, you may now have sound working in Flash. If you don't, keep searching Google, because I tried every other solution available and this was the only one that worked for me, so I'm not certain I can offer further advice, but I hope this works for you.

---

### Post by ladgrove on 2008-02-12
As an update to my previous post above, after updating the ALSA components as mentioned, I now have 2 choices for Device in Sound/Preferences. Interestingly, when I select the ALSA mixer, I get sound in all other applications but not flash & when I select the OSS mixer, I get sound in flash and all other applications except for view mpegs etc in MPlayer.

This is not so bothersome for me, and as I don't use flash all that much, I'm happy to manually switch whenever it suits my needs, that's the price you pay for using 64-bit. However, I'm not much of a hacker, but I'm quite certain these preferences could be automatically switched somehow when FireFox or Mplayer are loaded.

If I find a solution to this, I'll post it ASAP.

Cheers, sorry for the dual posts.

---

### Post by neroblue on 2008-05-05
Hi, 
I had a similar problem and all the fixes I found wouldn't work for me. In the end a not very smart but easy solution worked!

I didn't have any problems with the sound in Flash until I messed around different audio plugins to listen to online radio stations.

Next day I start the laptop and there's no sound any more in Flash videos. Rhythmbox and VLC media player were fine. 

I uninstalled all the real media, windows media and gstreamer plugins I had installed (gstreamer "bad" being one of them, the only one I remember because of the funny name). It still didn't work. Then I uninstalled Totem Video Player and voila! I could play Flash movies with sound!

I had to install also gstreamer "ugly" later for my music player to work too, and that&#347; it.

Hope this helps anybody,

Cheers!

---

### Post by cim on 2008-05-13
I have another solution to this, I have Ubuntu Hardy 8.04 installed and found another way to fix the no sound problem. 

1. System > Administration > Synaptic Package Manager
2. Search: pulseaudio
3. Check the box of libflashsupport
4. Apply

You may or may not restart Firefox, enjoy.

---

### Post by kladdert on 2008-05-14
Thanx man. Cheers :)

Worked perfectly after rebbot. Recommended!

---

### Post by cim on 2008-05-15
No problem, I am a newbie also so I am just trying to help out lol.

---

### Post by amisdar on 2008-05-21
> **cim said:**
> I have another solution to this, I have Ubuntu Hardy 8.04 installed and found another way to fix the no sound problem. 

1. System > Administration > Synaptic Package Manager
2. Search: pulseaudio
3. Check the box of libflashsupport
4. Apply

You may or may not restart Firefox, enjoy.

Great! This trick fixed my *Ubuntu Hardy 8.04* sound problem! :-)

Thank you!

---

### Post by cim on 2008-05-28
You are welcomed! =]

---

### Post by psyke83 on 2008-05-28
For Hardy users, this guide is obsolete. With the inclusion of PulseAudio, Flash has some issues that are not yet resolved officially, but my guide gives a "preview" of official fixes. Please see my guide here: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by mastersync on 2008-06-03
It works but my default sound (mp3s, videos) doesn't work. How do i reverse this ?

---

### Post by Dedors on 2008-06-18
fix worked

thanks

---

### Post by nachosDP on 2008-07-18
i did this and now flash is not working at all and tried everything i could think of to get it back( which is uninstalling and reinstalling it in different ways). i am faily new to ubuntu. if i go to a flash video it says install the missing plugins. ok . then it says adobe flash player and i click next then it says adobe flash player -- not avalable  and install is grayed out and there is only a manual install option which takes you to adobes web site and i follow the instructions for a tar.gz copy and paste the code to the terminal and it says NO! you are useing a 64bit and then nothing. please help

---

### Post by JustAboutRealJAR on 2008-07-19
Adobe still refuses to compile their flash player for 64 bit linux, so you have to run the 32 bit version of flash instead. needless to say, it's a bit of a hack, but it works just fine.

There are instructions on how to do it over here: [http://ubuntuforums.org/showthread.php?t=772490]("http://ubuntuforums.org/showthread.php?t=772490")

hope it helps... :)

---

### Post by nachosDP on 2008-07-21
> **nachosDP said:**
> i did this and now flash is not working at all and tried everything i could think of to get it back( which is uninstalling and reinstalling it in different ways). i am faily new to ubuntu. if i go to a flash video it says install the missing plugins. ok . then it says adobe flash player and i click next then it says adobe flash player -- not avalable  and install is grayed out and there is only a manual install option which takes you to adobes web site and i follow the instructions for a tar.gz copy and paste the code to the terminal and it says NO! you are useing a 64bit and then nothing. please help

this worked to get flash back but only in 64bit firefox:

sudo aptitude purge mozilla-plugin-gnash && sudo aptitude install flashplugin-nonfree libflashsupport

****this is all one line of code*****

---

### Post by iaskedalice09 on 2008-08-30
The OP's fix didn't work for me, but this did.

In terminal, type

sudo apt-get install libflashsupport

Restart Firefox, and voila!

---

### Post by r337ard on 2008-10-12
> **iaskedalice09 said:**
> The OP's fix didn't work for me, but this did.

In terminal, type

sudo apt-get install libflashsupport

Restart Firefox, and voila!

Woot, this worked perfectly for me.  Thank you!

---

### Post by Blinkiz on 2008-10-16
> **iaskedalice09 said:**
> The OP's fix didn't work for me, but this did.

In terminal, type

sudo apt-get install libflashsupport

Restart Firefox, and voila!

Nice, thanks! Worked for me under ubuntu 8.04.1

---

### Post by billybigrigger on 2008-10-20
worked for getting flash sound to work in both firefox and opera

gl

---

### Post by psyke83 on 2008-10-20
Just to note: this guide is horribly outdated. Flash 9 does not even support ESD by default anymore.

For Hardy/PulseAudio users, libflashsupport is suboptimal (it works, but causes constant crashes). This is covered in excruciating detail [here]("http://ubuntuforums.org/showthread.php?t=789578").

In summary: don't use Flash 9 if possible. Upgrade to Flash 10 (which is now at the final release), and **ensure PulseAudio is configured properly**. See the link above for more information and access to updated packages in my PPA.

P.S. Moderator(s), can we please move this thread to the outdated section? Rationale: the OP's instructions do nothing, and other advice amounts to increasing instability, and spam/duplicates of [bug #192888]("https://bugs.launchpad.net/bugs/192888").

---

### Post by everlearner on 2008-10-21
> **iaskedalice09 said:**
> The OP's fix didn't work for me, but this did.

In terminal, type

sudo apt-get install libflashsupport

Restart Firefox, and voila!

It works for me under Ubuntu 8.04.  Thanks^^

everlearner

---

### Post by teamsah on 2008-11-07
> **mastersync said:**
> It works but my default sound (mp3s, videos) doesn't work. How do i reverse this ?

i've same problem..help

---

### Post by RhubarbnCustard on 2008-11-08
worked for me - thanks

---

### Post by Jajo on 2008-11-26
hi, i've just installed intrepid, and no sound, i've installed flashplugin-nonfree and flashplugin-nonfree-extrasound, but i still have no sound on gnome; using intrepid at 64bit i had no sound with gnome and no problems with xfce, how can i solve?

i've intrepid32 on a amd64 3200 with an audigy2 zs and, in Preferences -> Sound, if i set something different from OSS or alsa multichannel playback, i have no sound or bad playing, and, of course, no sound in flash vids

---

### Post by Jajo on 2008-11-26
ps: flash works good even in kde

---

### Post by psyke83 on 2008-11-26
To the recent posters and new readers:

Don't follow the OP's instructions, and don't install libflashsupport!

Why?
[LIST]
[*]The OP's instructions are hopelessly outdated - recent Flash releases don't even supports ESD output anymore, so the instructions make no sense.
[*]The libflashsupport library was a necessary evil to get Flash 9 working with PulseAudio, but it causes extreme instability in Firefox. Flash 10 no longer needs this buggy library, so you are advised to upgrade.
[/LIST]

You should upgrade to Flash 10 *and* configure PulseAudio correctly. This is the only way to guarantee that sound mixing will work on your system (and without crashes).

See: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by Jajo on 2008-11-26
i followed your guide, and pulseaudio uses this device Audigy 2 ZS [SB0350]: ADC Capture/Standard PCM Playback. it plays, but just with my front speakers!

the device chooser doesn't even let me choose another device, and i don't know how to set it up..

---

### Post by SimonDay on 2009-01-04
ok, by the looks of itit's a brilliant thing that works, but i'm new with linux and it makes no sence to me at all, any chance someone could go threw it step by step?

---

### Post by forestwalkerjoe on 2009-02-14
i know that not every thing can work for each persons system.. i tried the below solve and .. well, it didnt work for me. 
i did however try 3 others.. the last test i did solved it.. and it think it address's the Glitch in this version of ubuntu very nicely. 
i am running on IBIX 810. 
here is the link to [my solve]("http://ubuntuforums.org/showthread.php?p=6734814#post6734814"). 
I am not good with linking and getting every thing to open.. so if you cant see the other links on this post i am setting up.. write back. BUT this really did solve nearly every thing. 

Good Luck

FWJ

---

### Post by emrys.r on 2009-04-18
> **iaskedalice09 said:**
> The OP's fix didn't work for me, but this did.

In terminal, type

sudo apt-get install libflashsupport

Restart Firefox, and voila!



AWSOME! nice one. 2 second fix. tried a few others with no luck.

This should be moved to the top of the list!

---

### Post by psyke83 on 2009-04-20
> **emrys.r said:**
> AWSOME! nice one. 2 second fix. tried a few others with no luck.

This should be moved to the top of the list!

Please spread the word, libflashsupport causes serious instability in Firefox. Stop using it, and upgrade to Flash 10 instead.

See: [https://bugs.launchpad.net/bugs/192888](https://bugs.launchpad.net/bugs/192888)

---

### Post by msetts on 2009-04-29
Thanks so much! This is a perfect fix!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by msetts on 2009-04-30
actually, this did work, until i rebooted my computer again, now having the same problem!

---

### Post by mrbabinga on 2009-05-29
I had sound issues since I upgraded to 9.04.  Uninstalled Swfdec and problems disappeared.

mrbabinga

---

### Post by pdadad on 2009-07-18
Deleting libflashsupport then re-installing flash 10 fixed Firefox but not Opera, which is no show stopper for me, in Ubuntu 8.04.  Thanks for the post!

---

### Post by BrionS on 2009-08-31
> **mrbabinga said:**
> I had sound issues since I upgraded to 9.04.  Uninstalled Swfdec and problems disappeared.

I think this is actually the more elegant (and permanent) solution.  It works for me and I don't need to create a script to keep re-installing a hack on each boot.

How libswfdec (swfdec-mozilla) got installed I'm not sure, but removing still allows Flash 10 to play but also enables the sound.

I'm running 9.04 and had sound in Flash until a few package-manager updates ago when suddenly it stopped.  I think swfdec-mozilla is contending with the real Flash player (nonfree) and the result is lost sound.  Removing swfdec-mozilla fixes this problem and I recommend trying that approach first! :guitar:

---

### Post by omrsafetyo on 2009-10-02
Tried the instructions on the first page.. 
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
sudo mkdir -p /tmp/.esd/
sudo touch /tmp/.esd/socket

no luck..

Went to /usr/lib and did a find for the file that was linked..
/usr/lib$ find /usr/lib* -name "libesd*"
/usr/lib/libesd.so.0

hmm.. my link points to nothing! alsa wasn't even installed yet...

sudo apt-get install libesd-alsa0

Still no luck...

sudo apt-get install flashplugin-nonfree-extrasound

Still no...

Clicked on the sound icon and opened the mixer.. unmuted LFE and turned the volume up - and magically it works!

Just thought I would share my experience in case it helps someone else.

---

### Post by po-90260 on 2009-10-07
> **BrionS said:**
> I think this is actually the more elegant (and permanent) solution.  It works for me and I don't need to create a script to keep re-installing a hack on each boot.

How libswfdec (swfdec-mozilla) got installed I'm not sure, but removing still allows Flash 10 to play but also enables the sound.



I'm new to ubuntu but I used unix 20 years ago. 
I just installed 9.04 on an old PC. I hear sound in Youtube but there's none in Flash 10.  
How do I check if I have this libswfdec? How do I remove it?  It's not listed in "Add/remove applications list". I seriously don't know my way around this product. Windows has brain deadened me I guess.

---

### Post by frazerr on 2009-10-18
> **po-90260 said:**
> I'm new to ubuntu but I used unix 20 years ago.   
How do I check if I have this libswfdec? How do I remove it?  It's not listed in "Add/remove applications list". I seriously don't know my way around this product. Windows has brain deadened me I guess.

Hi. "Add/remove applications" only shows applications.  It is the simple interface that hides most packages away from new users.

You want to go to System/Administration/Synaptic Package manager.

this will do everything you need

---

### Post by po-90260 on 2009-10-29
Synaptic package manager it lists 9 files begining with libswfdec

---

### Post by jac0117 on 2010-04-09
awesome... thanks this worked for me!

---

### Post by ben2talk on 2010-04-27
> **flibble said:**
> Yeeee Haaaaaaa! I've read so many posts about this, including all the "can't be fixed, wait for flash 9, yadda yadda". This fix works perfectly for me on dapper. Now I can watch all that pointless, moronic flash content! Thank you.

Amazing - but I'm using Flash 10 and this fix didn't work for me.

---

### Post by williamslewis on 2010-04-27
I was looking for this thing for almost a month and thank God I have finally reached here. Thanks for sharing such an informative tutorial

---

### Post by Rob-e on 2010-10-12
I was having this problem with ubuntu 10.10, I had to go to sound preferences and the output tab and pick my BT headset, for some reason other apps used it but flash used the selected one.

(posting here because its the first search result I got)

---

### Post by lkjoel on 2011-08-01
Thanks a lot for this! It fixed my flash sound!

---

### Post by Fedek86 on 2011-10-17
> **calx said:**
> After weeks of searching for a solution, this has finally got sound in flash working for me. :-D 

[https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/29760](https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/29760)


# Flash also looks for /usr/lib/libesd.so.1
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

# Flash expects /tmp/.esd/socket to exist.
sudo mkdir -p /tmp/.esd/
sudo touch /tmp/.esd/socket

this still working for me!! thanks!

---

### Post by Ronalddig on 2011-11-14
It worked for me

Thx :)

---

### Post by UNubTu on 2011-12-09
Also worked for me on Oneiric.  Although, I had to also start a Youtube movie and then while it was running, open up Sound Settings, Applications, and uncheck the Mute button next to ALSA plug-in [npviewer.bin].  Now that I think about it, I am not sure if creating the link files really solved the problem or if the Mute box being checked was my problem all along.  But I don't want to risk deleting the links now that it is working  :D

---

### Post by tmnuwan12 on 2011-12-11
I had some issues with flash. It was nothing to do with sound but with image cluttering and slow response. But I did a kernal upgrade and it works ok now...I think this would help if someone got any other issue with flash. I think kernal update would help..Thanks

---

