---
title: "No Sound in Spotify with WINE"
date: 2010-10-31
forum: Wine
---

### Post by achookang on 2010-10-31
Spotify has suddenly stopped working for me. It used to work fine about a month ago. The only recent change is that I have upgraded Ubuntu to 10.10 (previously I had 10.04) I don't think (AFAIK) that I changed the version of WINE (1.2) or Spotify Windows client.

Now when I try to play a song on Spotify I get the error "There is a problem with your sound card. Spotify can't play music"

If I open the WINE config and play the "test sound" on the Audio tab I get "Audio test failed!" It doesn't matter which driver I choose (OSS/ALSA etc or what settings for Direct Sound I try I always get the Fail message. 

Any help would be greatly appreciated.

Hardware: Acer Aspire 1363 laptop, Sempron AMD processor, 0.5GB RAM, 60GB HDD
OS: Ubuntu 10.10
WINE versions: Originally 1.2 also tried upgrading to 1.3.6 developer version 
Spotify version: 0.4.8.242

---

### Post by Refalm on 2010-11-02
Not a direct solution to your problem, but if you have Spotify Premium or Unlimited, you can use the Linux client:

[https://www.spotify.com/en/download/previews/](https://www.spotify.com/en/download/previews/)

On Wine:
Try setting the hardware acceleration from "Full" to "Emulate" in the sound options.

---

### Post by achookang on 2010-11-02
Thanks Refalm,

Unfortunately (or fortunately depending how you see it) I have Spotify Free, so I think the native linux client is not available for that type of account. I've also tried all the various permutations of the settings for hardware acceleration, to no avail....


thanks anyway

---

### Post by jimothy on 2010-12-21
go into the wine config panel (winecfg in terminal) , go to the audio tab and change sound to alsa only,,, untick anything else, ok or apply . close spotify and reopen.

Should be fine now..

---

### Post by achookang on 2010-12-21
Hi Jimothy

Thanks for the suggestions, but doing that (or any other option in the audio tab of Wine Config) still give an error.

I'm sure it is something to do with the latest version of Ubuntu as it worked fine when I was on the previous verisons (Koala or Lynx)

---

### Post by Spyderkid on 2010-12-23
You need to go into

Wine > Wine configuration > Audio  THEN...

> Tick the ALSA driver
> choose Emulation on Hardware Acceleration
> Make the default sample rate 44100 (IF IT ISN'T ALREADY)
> Make the default bits per sample 16 (IF IT ISN'T ALREADY)

[B][U]And then try again.
 if it doesn't work then you will have to un-install and install again[/U][/B]

_________________

*And hey presto your dreams come true!*

---

### Post by achookang on 2010-12-23
Thanks Spyderkid and others.

I am almost cerain that I had already tried these suggestions, but I did them again and it is working now.  Maybe upgrades to Ubuntu in the meantime>
 
Anyway, I now can use Spotify again :)


Thanks :p

---

### Post by msbealo on 2011-02-07
I had the same problem and solved it thanks.

I uninstalled wine because starting Spotify was really slow and taking more than 30 seconds/a minute to get going.

I deleted the .wine directory, reinstalled wine and then install Spotify.

Before installing Spotify the sound test worked fine, after the installation there was no sound. 

I uninstalled Spotify and did various combinations before realising that if you choose the right sound driver and then CLOSE the configuration window (not just click apply) then when you reopen it the sound test works. 

Once this works you can play cool music on Spotify.

Mark

P.S. This solved the slow loading problem.

---

### Post by Photodeus on 2011-03-22
> **achookang said:**
> Spotify has suddenly stopped working for me. It used to work fine about a month ago. The only recent change is that I have upgraded Ubuntu to 10.10 (previously I had 10.04) I don't think (AFAIK) that I changed the version of WINE (1.2) or Spotify Windows client.

Now when I try to play a song on Spotify I get the error "There is a problem with your sound card. Spotify can't play music"

If I open the WINE config and play the "test sound" on the Audio tab I get "Audio test failed!" It doesn't matter which driver I choose (OSS/ALSA etc or what settings for Direct Sound I try I always get the Fail message. 


I tried reloading my alsa audio drivers....
```
# alsa reload 
```
/sbin/alsa: Warning: Processes using sound devices: 3311(pulseaudio). 

```
# (sudo) alsa force-reload
```

This did the trick and Spotify plays audio again on Ubuntu 10.10 for me.

---

### Post by stephenhau on 2011-06-03
Thanks, changing to 'emulation' as you suggested fixed it for me :)

> **Spyderkid said:**
> You need to go into

Wine > Wine configuration > Audio  THEN...

> Tick the ALSA driver
> choose Emulation on Hardware Acceleration
> Make the default sample rate 44100 (IF IT ISN'T ALREADY)
> Make the default bits per sample 16 (IF IT ISN'T ALREADY)

[B][U]And then try again.
 if it doesn't work then you will have to un-install and install again[/U][/B]

_________________

*And hey presto your dreams come true!*

---

### Post by fgmart on 2011-07-23
Hey all, 

I was getting the same "Audio test failed!" alert from the Sound configuration, regardless of which driver I tried.

I solved it by removing my .wine subdir.  Then the audio test worked.

Then I reinstalled Spotify and everything's fine!

I'm using the ALSA driver, with Emulation, 44100 sample rate, and 16 bits per sample.

---

### Post by Bromden on 2011-10-11
> **fgmart said:**
> Hey all, 

I was getting the same "Audio test failed!" alert from the Sound configuration, regardless of which driver I tried.

I solved it by removing my .wine subdir.  Then the audio test worked.

Then I reinstalled Spotify and everything's fine!

I'm using the ALSA driver, with Emulation, 44100 sample rate, and 16 bits per sample.
Thank you i solved my audio problem too with this solution. You just had to delete the user.reg file. :)

---

### Post by keyshawn on 2011-10-18
> **Photodeus said:**
> I tried reloading my alsa audio drivers....
```
# alsa reload 
```/sbin/alsa: Warning: Processes using sound devices: 3311(pulseaudio). 

```
# (sudo) alsa force-reload
```This did the trick and Spotify plays audio again on Ubuntu 10.10 for me.

This also ended up working for me on 11.04, thanks !:popcorn:

---

### Post by gengoro on 2011-11-25
Switching from Full to Emulation worked for me (10.04). Thanks all for the suggestions.

---

