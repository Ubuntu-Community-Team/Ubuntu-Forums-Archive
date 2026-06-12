---
title: "Jack Weirdness"
date: 2009-11-22
forum: Ubuntu Studio
---

### Post by dawiba on 2009-11-22
UbuntuStudio 9.10/Saffire LE

I tried to start a new project today for the first time in a few days, but Jack wouldn't start. It had worked last time I used the computer, but no joy this time.

So I checked all the settings that I knew how to do, but couldn't see anything wrong or anything that had changed. I was able to get it to start with my USB card but not my Firewire card.

Then I remembered reading somewhere very recently that updates can cause problems, e.g. Jack not working. I remembered having done an update the other day and that I hadn't tried to start Jack or do any recording since then. So I opened Studio Controls, unchecked everything and then went into Groups and removed myself from both audio and video. Next, I rebooted and reinstated all the previous settings, rebooted and hey presto, Jack started first time. I've tried it a few times again to make sure and it starts first time every time.

I feel as if I'm hallucinating, because I haven't actually changed anything. All I've done is re-set my settings.

Anyone else had this? Will it happen every time there's an update?

Am I just imagining this?

Is it time for a new computer and soundcard :) (don't feel you have to choose this one ;))

---

### Post by trulan on 2009-11-22
Sounds typical.  Don't throw your computer out the window just yet.

Mine actually wiped the @audio - rtprio line, which is not refreshed when resetting Ubuntu Studio Controls.  I had to put it back in manually to get things to work.  It did it with an update a few days ago.

---

### Post by bluesscream on 2009-11-22
Had the same probs not only one time. It even happened that /etc/security/limits was overwritten and the line @audio - rtprio 99 was gone.
Or properties of /dev/raw1394 were resetted and more.
Guess this happens with automatical updates. I don't check them every single time as thoroughly I should...

---

### Post by sgx on 2009-11-23
Its good luck to maintain copies of important textfiles for new setups, or reinstalls. Also, having apt save your /var/apt/cache contents, and
burning them to disk can save downloads, and preserve the odd file that gets deleted from new repositories, or one one that works that got replaced by new versions that don't. The .wine folder is another good one to back up, especially if you collected extra .dlls to enable certain vsts
and winxxx apps to function.
Putting /home on an separate partition, takes the pain out reinstall and needlessly redoing lots of personal settings and eyecandy.
Cheers

---

### Post by dawiba on 2009-11-23
@sgx - I generally do keep settings, work and home folder backed up to an external drive. I don't use Wine or vst's, so that shouldn't be an issue. I usually don't change anything from the default install, other than the usual settings changes to enable my firewire card, so eye candy and personal settings are not an issue either. However, it's good sensible advice and is always worth repeating, so thanks.

@trulan/bluesscream - the thing that puzzled me was that everything I checked, including /etc/security/limits.conf, was as it should be.

Anyway, I checked again this morning before posting and Jack started first time. I guess it might not be Jack's fault as it's only behaving as it should in response to settings it sees (I just wish I could see them too!).

However, I was doing some drums last night for a track and I was trying to use LinuxDSP plugins (compressor and eq), but they seemed to crash randomly (nothing else was affected). I've managed to use these plugins before without any problems, so I tried a few times, but it was the same every time so I ended up using the Calf compressor which worked fine.

I guess I'll just need to blame it on the Large Hadron Collider and keep plugging away.

Thanks for the replies.

---

### Post by dawiba on 2009-11-24
For those that are interested:
```

sudo chmod 775 /path/to/plugin
```

sorted the problem with LinuxDSP plugins.

(it was in the manual :redface:)

---

### Post by AutoStatic on 2009-11-25
How about those plugins, are they workable? Didn't try them out yet. I did write a script to download and install them all, if anyone is interested I'll post it.

---

### Post by dawiba on 2009-11-25
> **AutoStatic said:**
> How about those plugins, are they workable? Didn't try them out yet. I did write a script to download and install them all, if anyone is interested I'll post it.

If you're asking if they are any good/easy to use, then I think so.

I really like all of the eq's. I think they're well laid out and work in a way that's easy to hear what they're doing when you tweak the knobs.

The compressor is good too, although just now I prefer using the Calf compressor (from the Jack plugin pack in the menu).

There is a patchbay which works perfectly, but I don't use it as I'm happy to use the connect tab in Jack.

The reverb is really nice as is the valve pre-amp.

There are some guitar effects pedal plugins which I like as well. Be warned though, the distortion plugin is really heavy on your processor.

Overall, distortion effect aside, the plugins are reasonably processor friendly.

I find the plugins look good with sensible and easy to use layouts. I don't use the LV2 or native Linux vst versions as I don't think the version of Ardour that ships with Ubuntu Studio supports them.

Bear in mind, these are just my opinions and you should always try for yourself, it's easy to download and try them. The developer has been on a drive lately to get donations, so if you do download and use them, try to give a donation (true of lots of Linux software).

Bear in mind, these are just my opinions and you should always try for yourself, but I find the plugins to be good to use and easily on a par with anything you'll find on other platforms.

I have them in my menu for ease of access (see screenshot).

I've also attached a screenshot of a couple, although you can see them all on the plugin website.

---

### Post by AutoStatic on 2009-11-26
Thanks for the feedback! I like Calf too, the Calf pack contains some real nice stuff. What I don't like about LinuxDSP is that the plugins are closed source, so no, I will never consider donating as long as it stays that way. But they do look good and I was really curious if anyone was using them.

---

