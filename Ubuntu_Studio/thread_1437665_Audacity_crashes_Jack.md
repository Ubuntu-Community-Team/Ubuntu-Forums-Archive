---
title: "Audacity crashes Jack"
date: 2010-03-24
forum: Ubuntu Studio
---

### Post by siabost on 2010-03-24
Using Ubuntu-studio 64bit 9.10 on AMD 64bit Desktop.

Audacity seems to work fine on it's own but start Jack then Audacity, set Audacity preferences to work with Jack wait a few seconds and they both crash.
In those few seconds I can see that Audacity doesn't show in Jack's connections tabs.

Jack & Ardour/Hydrogen etc seem to work fine so I suspect the problem is with Audacity.

I had a similar problem in 64Studio 2.1 with Audacity except in that case it crashed immediately. Reportedly the problem was solved in 64Studio V3 but I haven't tried that yet as it's still at beta-3 version.

Any solutions for Ubuntu-studio?

Thanks.

---

### Post by mango42 on 2010-03-24
I hope this doesn't come over as facetious but why not just run that truly excellent application, **Audacity**, without Jack support until full integration *is* eventually achieved?

---

### Post by siabost on 2010-03-24
Hi mango42,

That's what I am doing presently but as I use Ardour as my main recording tool I'd quite like to mix down directly to Audacity rather than to a file first.

But if I have to wait... I have to wait:)

---

### Post by trulan on 2010-03-24
It scares me to run Ardour and Audacity at the same time.  A much lighter-weight and more stable app to use for mixing down from Ardour is Jack Time Machine.  It is called time machine because it starts recording 10 seconds before you click on it.  So you have to load the file it outputs into Audacity and trim the start off.  For serious mixdowns, I don't actually use the time machine feature because it tends to put a click at the 10 second mark.

Time Machine will output a .w64 file in your home directory, and then you can load that file up in Audacity and trim it to meet your needs.  

Edit:  I re-read your post - missed the part about not wanting to mix down to a file.  Sorry, I don't have a better solution for you.  I've never been overly impressed with Audacity's stability in Linux, especially when using Jack.

---

### Post by mango42 on 2010-03-25
> **trulan said:**
> I've never been overly impressed with Audacity's stability in Linux, especially when using Jack.

Hi **trulan**

If you treat Audacity like Wavelab **3** on windows98, ie: before all the bells, whistles and 'integration' crept in, it seems to work very well, for me at least. I'm well impressed, especially with it's smooth handling of mp3s (or perhaps that's down to its good LAME support?)

As for Ardour, the GUI not reading the physical screen resolution correctly rather puts me off (**Its** window is bigger than **my** screen. Or is this just an artifact of my 1024x768 window onto the cyberworld not being big enough for Ardours base resolution? Hmm... very off-putting, whatever.

Patiently waiting for the day Ffado or you announce support for my Focusrite Saffire 40 ;-)

---

### Post by trulan on 2010-03-25
> **mango42 said:**
> Patiently waiting for the day Ffado or you announce support for my Focusrite Saffire 40 ;-)
It looks like it's coming.  Ffado calls it 'expirimental' on the support page.  There are a few users reporting success:
[FONT=Lucida Calligraphy][SIZE=2][COLOR=olive][COLOR=olive][FONT=&quot][/FONT][/COLOR][/COLOR][/SIZE][/FONT]_[http://www.ffado.org/?q=node/862](http://www.ffado.org/?q=node/862)_

---

### Post by mango42 on 2010-03-25
> **trulan said:**
> It looks like it's coming.  Ffado calls it 'expirimental' on the support page.  There are a few users reporting success:
[FONT=Lucida Calligraphy][SIZE=2][COLOR=olive][COLOR=olive][FONT=&quot][/FONT][/COLOR][/COLOR][/SIZE][/FONT]_[http://www.ffado.org/?q=node/862](http://www.ffado.org/?q=node/862)_

Brilliant - thanks for that - that ffado page went 'active' whilst I wasn't looking ;-)

---

### Post by AutoStatic on 2010-03-25
I have no big issues with Audacity (or rather PortAudio) and JACK. What are your JACK settings siabost? And what kind of soundcard? Yeah, sometimes Audacity just decides to call it a day which upsets the sound modules so I have to restart them. But that happens rarely and only when I do heavy editing (like constantly repeating stuff or repeatedly skipping to the beginning of a song or selection).

---

### Post by asuastrophysics on 2010-12-21
I'm sorry to bring back an old thread. I seem to be having the same problem described by the OP. I'll be recording tracks with Jack running, then I'll export them as *.wav format from SnooperLooper, open them in Audacity, trim them....and then my entire computer goes crazy. My dual-core processor usage surges to 100%. I can't click, move, or execute any sort of command in a GUI terminal. 

I then have to CTRL+ALT+F5 to get to TTY and completely restart GDM, loosing all of my unsaved musical work in the process. :(

Is there some other program comparable to Audacity that doesn't completely crash both my sound system and X? Something more reliable and stable?

---

### Post by AutoStatic on 2010-12-22
Yes there is, ReZound. Workflow is a bit different but ReZound has solid JACK support so it works way better with JACK. And it's not being maintained anymore unfortunately :(

---

