---
title: "My very first Ubuntu..."
date: 2006-05-16
forum: Testimonials &amp; Experiences
---

### Post by ProgressiveBastion on 2006-05-16
Well I'm sitting in my office here behind the Redwood Curtain in Northern California, and ran across this forum. I wanted to find some place to give some feedback. Looks like I found it...

Well I tried weeks ago to get Breezy installed but I had a issue with my OEM installed DVD burning program (yet another reason to look for a viable alternative) they let you burn CD's but you have to upgrade (4 a US$ fee) to their so called 'Primo' package in order to get .ISO's to be burned as a CD image. But as usual the Free/Open Source crowd has a perfect solution. I did the old reliable & highly proven method called: R.T.F.M. (read the frigging manual) and used a app I was familiar with (but not installed on this machine) that the install Ubuntu page provided a link to. 

I formatted my C:\ drive I burned a CD image, put it into my CD tray & guess what happened? It worked. It recognised everything. (my sound card is inaudible & is the only aspect of the install not working perfectly) I can hear it but it's on super, super low volume. Still excellent results. I remember my first experience with Linux 7 or so years ago with a RedHat install. That was a nightmare. Days & Days of trying this or that. This was before I learned the reliable & highly effective practice of R.T.F.M.! But even after trying to install & R.T.F.M.ing the thing to death it still took days to get a stable & secure OS up & working.

So other than not have volume control Ubuntu really rocks. I plan on learning how to get Breezy (if possible) to run my SMTP/POP server, & a bunch of bit torrents I host over at my [Broadcast Machine]("http://www.ProgressiveBastion.com/bm/" title="ProgressiveBastion.com Free TV 4 the people: Channel List") which is part of my RW progressive blogger & activist website. So Sound functions in many ways would be cool but not mission critical since I'm looking for Torrent & POP applications. *Anyone have any ideas on what works really good on Ubuntu when it comes to Torrent & POP server apps?* If so I'd appreciate your input 2 this 2 day old newbie...

By the way I'm running a 400ish MHz machine w/ 256 mg RAM that a Intel based board & chip-set. And the machine who my partners father gave it to us had a Windblows 98 OS installed on it. We dumped it 4 XP but XP and the old machine made "EVERYTHING" really slow & dumpy, so we dumped it 4 Ubuntu!

Now we have a machine that scoots right along. And I'm looking forward to 'NOT" having to reboot 4 times a day. And the cost was right; recycled machine + Ubuntu = 10 hrs total labour of love = 0 $USD, and priceless experience with a machine that hasn't had to be rebooted (except for updates) in 2 days. A miracle because I'm a lets go in and mess/muck about with EVERYTHING to see what it will or won't do. This install is a 99 out of 100. Thanks people! I can't (but I will) wait to start burning Live & Install disks so to get them into our lending library that we run for our friends here in Arcata, CA. 

Thanks too everyone who helped make this project a reality, I've totally changed my companies direction last year by switching everything to Open-Source when possible. Mostly for philosophical & political reasons but the lessening of cash outlay has also been a blessing. *By the way since I'm new returner to desktop Linux, does anyone have any experience with Office OneNote application?* I'm looking for a equivalent on Ubuntu/Linux! It's about the only reason I can think of not to totally dump Winblows. 

Next up for myself! Making my professional Workstation w/ 2.4 GHz & 1gb ram a dual boot *until I can find a descent replacement for OneNote*... wish me success.

peace Michael Scott

---

### Post by Lord Illidan on 2006-05-16
Erm, about the sound.

Try entering ```
alsamixer
``` at the terminal.

Adjust your volumes. PCM and WAVE give distorted output when they are TOO high up. Aim for 75 - 85%. Master can be carried up to 100.

Press q to exit.

[code]sudo alsactl store[code] will save your settings after you are done.

---

### Post by Sef on 2006-05-16
> But as usual the Free/Open Source crowd has a perfect solution. I did the old reliable & highly proven method called: R.T.F.M. (read the frigging manual)

In Ubuntu (and some other forums), there is PTQ (Post the Question.)

---

### Post by Bharath on 2006-09-04
Hi,

Check out [http://memoranda.sourceforge.net/](http://memoranda.sourceforge.net/) for Onenote replacement. Memoranda has more than 50% of the functionalities of OneNote.

Bharath

---

