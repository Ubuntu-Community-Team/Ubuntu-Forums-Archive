---
title: "No sound recording or skype ability"
date: 2012-06-14
forum: System76 Support
---

### Post by oxman on 2012-06-14
No sound recording or skype ability. 
Bonobo Pro
Ubuntu 12.04

I am unable to record sounds or use skype with my system. When I attempt to record using the ubuntu recorder the playback is white noise. Any help is appreciated.

---

### Post by isantop on 2012-06-14
> **oxman said:**
> No sound recording or skype ability. 
Bonobo Pro
Ubuntu 12.04

I am unable to record sounds or use skype with my system. When I attempt to record using the ubuntu recorder the playback is white noise. Any help is appreciated.

Download the latest version of the System76 driver from [http://www.planet76.com/](http://www.planet76.com/). It will always be the second link from the bottom.

After that, go ahead and install the package, then click on the device menu (power icon in the far top right) and choose "system settings". Then, click on System76 Driver.

From here, choose "Restore System" and see if that fixes it. You'll need to reboot after the restore is complete for the changes to take effect.

---

### Post by oxman on 2012-06-15
Isantop, thank you for the reply.

I followed your suggestions but there is still no joy. Any other suggestions would be appreciated.

---

### Post by oxman on 2012-06-21
Any other options?

---

### Post by isantop on 2012-06-21
> **oxman said:**
> Any other options?

What drivers were installed on your machine? You can check by expanding the details section. 

Are you sure it still isn't working on sound recorder at least? Skype uses different settings, so that could be different. Sound Recorder should give you something though. Can you take a screenshot of the input tab of your sound settings window.

---

### Post by oxman on 2012-06-21
You lost me. Only dialog for details is in Settings and there is no info on the sound driver there.  Pulseaudio 1:1.1-0ubuntu15.1 what you are looking for?

Sound recorder gives me white noise only on play back.

Attached is my input.

---

### Post by isantop on 2012-06-22
> **oxman said:**
> You lost me. Only dialog for details is in Settings and there is no info on the sound driver there.  Pulseaudio 1:1.1-0ubuntu15.1 what you are looking for?

Sound recorder gives me white noise only on play back.

Attached is my input.

Sorry, the details section of the System76 driver.

---

### Post by oxman on 2012-06-22
Thank you for your time. Here's a snapshot of the 76 Driver details.

---

### Post by oxman on 2012-06-25
Hi isantop, 
Any chance to look at the driver version yet?

---

### Post by isantop on 2012-06-25
> **oxman said:**
> Hi isantop, 
Any chance to look at the driver version yet?

We're not in the office on weekends, so this was my first chance.

It looks like your system shouldn't require any sound fixes. Are you sure you're not able to record using sound recorder? There shouldn't be any problems with that (skype uses configuration independent from the system configuration).

---

### Post by oxman on 2012-06-25
isantop, 

Hey, I hope all is well with you regarding the fires. I used to live near Loveland Pass years ago.

Please check out the recorder settings images and the associated sound wave related to a recording with those settings.

---

### Post by isantop on 2012-06-26
> **oxman said:**
> isantop, 

Hey, I hope all is well with you regarding the fires. I used to live near Loveland Pass years ago.

Please check out the recorder settings images and the associated sound wave related to a recording with those settings.

The fires are a pretty huge distance away from where I'm at. I just wish it would rain to keep them from breaking out so badly. It's been over 100 F every day for the past four days.

If you plug in an external microphone, does that make a difference? If so, then you likely have a hardware problem with your internal Mic, and we should bring the system in for repair.

---

### Post by tarahmarie on 2012-06-28
[http://thecowgirlcoder.com/2012/06/28/how-to-get-the-microphone-working-in-skype-with-kubuntu-12-04-and-likely-with-previous-versions/](http://thecowgirlcoder.com/2012/06/28/how-to-get-the-microphone-working-in-skype-with-kubuntu-12-04-and-likely-with-previous-versions/)

---

### Post by oxman on 2012-06-28
> **isantop said:**
> The fires are a pretty huge distance away from where I'm at. I just wish it would rain to keep them from breaking out so badly. It's been over 100 F every day for the past four days.

If you plug in an external microphone, does that make a difference? If so, then you likely have a hardware problem with your internal Mic, and we should bring the system in for repair.

Amazing isontop, we are soaking wet and way below average temperature for this time of year. The garden is languishing because of it.

I plugged in a microphone and voilà I have sound recording. I suppose I should have checked the mic when I purchased the unit. What next? Is this something I can change out?

---

### Post by oxman on 2012-06-29
> **tarahmarie said:**
> [http://thecowgirlcoder.com/2012/06/28/how-to-get-the-microphone-working-in-skype-with-kubuntu-12-04-and-likely-with-previous-versions/](http://thecowgirlcoder.com/2012/06/28/how-to-get-the-microphone-working-in-skype-with-kubuntu-12-04-and-likely-with-previous-versions/)
Thanks for the "heads up" taramarie.

---

### Post by tarahmarie on 2012-06-29
> **oxman said:**
> Thanks for the "heads up" taramarie.

No worries. It's not a fix, but at least it gets sound working.

---

### Post by oxman on 2012-07-01
Isantop, Is the mic something I can fix without voiding the warranty?

---

### Post by tarahmarie on 2012-07-02
> **oxman said:**
> Isantop, Is the mic something I can fix without voiding the warranty?

What warranty are you talking about?

---

### Post by isantop on 2012-07-02
> **oxman said:**
> Isantop, Is the mic something I can fix without voiding the warranty?

Unlikely; it involves pretty major disassembly to get to it. I'd recommend sending it in.

---

### Post by oxman on 2012-07-09
> **isantop said:**
> Unlikely; it involves pretty major disassembly to get to it. I'd recommend sending it in.

groan! I'll do that when I have a window of opportunity. Too many lappy projects going at once at the moment. Just contact the 76 site or call?

---

### Post by isantop on 2012-07-10
> **oxman said:**
> groan! I'll do that when I have a window of opportunity. Too many lappy projects going at once at the moment. Just contact the 76 site or call?

Contacting us via the site is the best way. You'll need to end up doing that anyway.

---

### Post by erichgamba on 2012-11-07
Have you tried to start skype with the following command?

PULSE_SERVER=127.0.0.1 skype

---

