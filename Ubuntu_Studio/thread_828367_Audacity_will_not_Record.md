---
title: "Audacity will not Record"
date: 2008-06-13
forum: Ubuntu Studio
---

### Post by phildaman46 on 2008-06-13
I've had this problem since Ubuntu 7.04 and I can't find any solutions in this forum. My Recording Device in Audacity is, "ALSA: HDA NVidia: ALC883 Analog (hw:0,0). Everything in my Volume Control is unmuted. Under the Recording tab I have "Capture" and "Capture 1" all on max volume.

---

### Post by Lostincyberspace on 2008-06-13
do you hear sound when you speak into the mike?

do you have the mike plugged in? I know stupid but I made the mistake the first time I used mine.

I had problem with upgrades so I know do full installs now with a seperate /home to keep all my settings.

---

### Post by phildaman46 on 2008-06-14
I'm not using a mic. I'm testing to see if I can record what I'm playing, But I can't. When I record, I get little waves but no sound comes out of it.

---

### Post by sultanoswing on 2008-06-14
> **phildaman46 said:**
> I'm not using a mic. I'm testing to see if I can record what I'm playing, But I can't. When I record, I get little waves but no sound comes out of it.

If I recall, it's a known error with audacity on Ubuntu. Try the latest beta version, it worked for me when I was having a similar problem.

[http://audacity.sourceforge.net/download/features-1.3-a](http://audacity.sourceforge.net/download/features-1.3-a)

[http://audacity.sourceforge.net/download/](http://audacity.sourceforge.net/download/) (roll your own)

...and a hardy version:

[http://packages.ubuntu.com/hardy/audacity](http://packages.ubuntu.com/hardy/audacity)

---

### Post by Tin Arm on 2008-06-17
> **phildaman46 said:**
> I'm not using a mic. I'm testing to see if I can record what I'm playing, But I can't. When I record, I get little waves but no sound comes out of it.


I was having problems too. Try this possibl
e solution at [http://www.seoras.com/2008/05/26/how-to-record-streaming-audio-with-audacity-in-ubuntu-804-hardy-heron/](http://www.seoras.com/2008/05/26/how-to-record-streaming-audio-with-audacity-in-ubuntu-804-hardy-heron/)

It worked for me.

---

### Post by bufsabre666 on 2008-06-17
have you tried switching your recording device?

---

### Post by phildaman46 on 2008-06-18
> **Tin Arm said:**
> I was having problems too. Try this possibl
e solution at [http://www.seoras.com/2008/05/26/how-to-record-streaming-audio-with-audacity-in-ubuntu-804-hardy-heron/](http://www.seoras.com/2008/05/26/how-to-record-streaming-audio-with-audacity-in-ubuntu-804-hardy-heron/)

It worked for me.

That link didn't help. It says something about setting a Mix option in the Switches tab which I don't have.

---

### Post by phildaman46 on 2008-06-18
> **bufsabre666 said:**
> have you tried switching your recording device?

Yes, I tried all that and I get nothing.

---

### Post by derjames on 2008-08-04
> **phildaman46 said:**
> That link didn't help. It says something about setting a Mix option in the Switches tab which I don't have.


Perhaps in your system are called 'Capture' 'Capture1' and 'Digital' once you select them they will appear on the Recording tab, I my case their level was all down and in consequence I could not record any sound, just set the appropriate level according to your system. 

cheers

---

### Post by RH9R on 2008-08-06
DerJames! You Are Mighty!
 
The digital/capture/capture1 did the trick.
 
Thank You!!

---

### Post by phildaman46 on 2008-08-09
> **derjames said:**
> Perhaps in your system are called 'Capture' 'Capture1' and 'Digital' once you select them they will appear on the Recording tab, I my case their level was all down and in consequence I could not record any sound, just set the appropriate level according to your system. 

cheers

Um...Like I said on my first post, Capture 1 and 2 are both to the max. I have Digital to the max too. All I get is very low volume and static.

---

### Post by phildaman46 on 2008-11-16
Still no luck in Audacity in Ubuntu 8.10. I uploaded a zip with a little audio clip inside from The Terminator DVD that I recorded in Audacity. From the mp3 you will hear hissing and you can barely hear the characters talking. This is how good recording is in Audacity in Ubuntu. I also get this with the basic Sound Recorder that comes with Ubuntu.

---

