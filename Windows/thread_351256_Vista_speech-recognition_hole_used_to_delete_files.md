---
title: "Vista speech-recognition hole used to delete files"
date: 2007-02-01
forum: Windows
---

### Post by Phatfiddler on 2007-02-01
Microsoft has admitted that a hole in the voice-recognition program could allow the deletion of folders and files without the users' permission.  It has become clear that commands could be sent to your PC as an mp3 file.  Say you visit a site, and suddenly, an mp3 plays, commanding your system to delete files, and then empty the recycle bin, therefore removing your files.  Say you download an mp3, and when you play it, it commands the same thing.

Apparently "voice-recognition" doesn't include recognizing the difference between users.....

[Original News Document]("http://news.bbc.co.uk/2/hi/technology/6320865.stm")

---

### Post by BigDave708 on 2007-02-01
Unbelievable. It took an entire two days to find a flaw.

---

### Post by %hMa@?b&lt;C on 2007-02-01
> **BigDave708 said:**
> Unbelievable. It took an entire two days to find a flaw.
technically one day, because the disks did not go on sale until ~9 in the morinng.

---

### Post by Brunellus on 2007-02-01
this is going to the microsoft forum.

---

### Post by delfick on 2007-02-01
lol :D :D :D :D

---

### Post by pichalsi on 2007-02-01
Now this is hillarious... Maybe a feature? :P

---

### Post by raul_ on 2007-02-01
Definitely a feature. Imagine erasing files with your voice...how futuristic :rolleyes:

---

### Post by 3rdalbum on 2007-02-01
Try playing the Macy Gray song "I Try" in Windows Vista with voice recognition enabled. At one particular point in the first verse, Windows Media Player stops playing.

---

### Post by meng on 2007-02-01
My favorite paragraph from the article:
> The firm has pointed out that in order for the flaw to be exploited the speech recognition feature would need to be activated and configured and both microphone and speakers would have to be switched on.
So your computer is only vulnerable if it's working to begin with!

---

### Post by erlyrisa on 2007-02-01
See how easy it is for microsoft to advertise thier product -...

whoops Voice Recog has a flaw in it on Vista!
-Public.... Does Can you talke to Vista? .. Cool, I think I'll buy it!

-Don't think they didn't know this flaw - the speech .net framework has been around for a good while now and is freely useable (even on XP)

-They have left the SAPI driver open to looping throught the sound card being able to listen to output on purpuse so that you can program TAPI functions more easily. They have also left all modem voice connections open to the sound card so that you don't have to dick around telling it to open channels

-They are also doing this to make the piont to hardware manufacturers to incorporate DRM into thier products (Seems like the soundcard/chip manufacturers probably didn't agree to having to have to deal with HDMI copyright protection) so Msoft shows off to the manufacturers by leaving the hole to say - see look, this it what happens if we don't incorporate keyed handshaking encrytion with the sound device aswell.

-The truth is out there!:guitar:

---

### Post by Trebuchet on 2007-02-01
> **meng said:**
> My favorite paragraph from the article:

So your computer is only vulnerable if it's working to begin with!That is amusing. I haven't had a mic hooked up to my system in nearly 7 years. I'm sure that long before I see the need for one again, MS will have patched this little glitch.

I can see it now:

"Maybe I should just reformat the drive," he thought out loud. "Hey, what's my new PC doing...? Aw, crap!"

---

### Post by Trebuchet on 2007-02-01
> **erlyrisa said:**
> See how easy it is for microsoft to advertise thier product -...

whoops Voice Recog has a flaw in it on Vista!
-Public.... Does Can you talke to Vista? .. Cool, I think I'll buy it!

-Don't think they didn't know this flaw - the speech .net framework has been around for a good while now and is freely useable (even on XP)

-They have left the SAPI driver open to looping throught the sound card being able to listen to output on purpuse so that you can program TAPI functions more easily. They have also left all modem voice connections open to the sound card so that you don't have to dick around telling it to open channels

-They are also doing this to make the piont to hardware manufacturers to incorporate DRM into thier products (Seems like the soundcard/chip manufacturers probably didn't agree to having to have to deal with HDMI copyright protection) so Msoft shows off to the manufacturers by leaving the hole to say - see look, this it what happens if we don't incorporate keyed handshaking encrytion with the sound device aswell.

-The truth is out there!:guitar:There's another reason I've resisted putting any .NET software on my XP system.

---

### Post by rayt5 on 2007-02-01
Oh come on. I'll admit that it might be a hole, but it's such a *small* hole.  I mean, first off, the software doesn't even work properly a lot of the time if it's not dead quiet (see link below), secondly, what are the odds of an mp3 playing while the person isn't there to see what is happening? Or if they are there AND speech recognition happens to also be on (which can be turned off with one click), what are the odds of it working properly with someone talking over it, or even if they are not, what are the odds that the mp3 voice will closely match the voice that the software is already configured to?

[http://www.youtube.com/watch?v=2Y_Jp6PxsSQ]("http://www.youtube.com/watch?v=2Y_Jp6PxsSQ")

---

### Post by Phatfiddler on 2007-02-02
^  Thats a very old demonstration that was done when they first developed the system.  It has improved a lot since then.  It can even work with heavy accents as can be seen here:

[http://www.youtube.com/watch?v=Uy9dRkCzRRQ](http://www.youtube.com/watch?v=Uy9dRkCzRRQ)

---

### Post by burek on 2007-02-02
> Microsoft has admitted that a hole in the voice-recognition program could allow the deletion of folders and files without the users' permission. It has become clear that commands could be sent to your PC as an mp3 file. Say you visit a site, and suddenly, an mp3 plays, commanding your system to delete files, and then empty the recycle bin, therefore removing your files. Say you download an mp3, and when you play it, it commands the same thing.

Apparently "voice-recognition" doesn't include recognizing the difference between users.....

lol
  
I just talked with a team / salesman from Microsoft selling  in the middle of the street . They were just saying it was highly Safe ! !   lol

---

### Post by raul_ on 2007-02-02
> **rayt5 said:**
> secondly, what are the odds of an mp3 playing while the person isn't there to see what is happening? Or if they are there AND speech recognition happens to also be on (which can be turned off with one click), what are the odds of it working properly with someone talking over it, or even if they are not, what are the odds that the mp3 voice will closely match the voice that the software is already configured to?
[http://www.youtube.com/watch?v=2Y_Jp6PxsSQ]("http://www.youtube.com/watch?v=2Y_Jp6PxsSQ")

A lot of sites play embebbed videos/music. It's a new step for the virus sites. Sure people could be careful but imagine you have some sort of spyware that opens a new page every now and then and plays one of those files when you happen do be at school. Annoying huh?

Oh but wait...just turn off the computer when you get out...

Oh but wait...just don't use it at all :D

---

### Post by rayt5 on 2007-02-02
> **raul_ said:**
> A lot of sites play embebbed videos/music. It's a new step for the virus sites. Sure people could be careful but imagine you have some sort of spyware that opens a new page every now and then and plays one of those files when you happen do be at school. Annoying huh?

Haha... good point.

The only problem with that is that the voice recognition would also have to be left on all day, and that is literally disabled with one click. I mean i can see if they figured out how to get around that problem, it would be a big deal.
I've actually played around with Vista a bit (my roommate has it), and any attempted malicious voice commands would not be faster than the one-click disable.  So in other words, if the user is present, it will not happen, and if a user leaves voice command on all day and ALSO sets the computer not to lock itself after a certain amount of time, then they pretty much have it coming to them. That is like the Linux equivalent of logging on as root 24/7 and then giving shady programs from third party repositories full permissions.

---

### Post by Phatfiddler on 2007-02-03
"Here's $500 for the first documented case of someone using the white courtesy phone in an airport to page Mr Shootdown, Reese Sett, Sleep Now, or whatever and blanking all the laptops in a concourse.  An extra $500 if it's DC National..."

lol:twisted: 

[Source]("http://lists.immunitysec.com/pipermail/dailydave/2007-January/004004.html")

---

### Post by rayt5 on 2007-02-03
From that article: "You can actually activate voice command mode by saying a certain phrase."

Oh! I forgot about that! lol. Vista voice recognition *does* have voice enabling... wow, so yeah... hmm now the more I think about it the easier it would be to mess with somebody's computer if nobody was around...

---

### Post by raul_ on 2007-02-04
Well yes...but if you leave the computer on while you're away you pretty much have it coming :rolleyes: (i just love that argument)

---

### Post by Trebuchet on 2007-02-04
> **raul_ said:**
> Well yes...but if you leave the computer on while you're away you pretty much have it coming :rolleyes: (i just love that argument)Seriously. I either put my modem in standby or block 'net access with my firewall anytime I leave my system untended for any length of time. Nor do I generally permit sound effects to play when I'm on websites since I usually am listening to music while on the computer.

Voice control is like any other tool: It can be abused. If potential abuse is our sole criteria for what not to use, we'd better roll back civilization because that fire stuff can be used to commit arson as well as cook and keep warm.

Seems to me that it would be simple enough to change the voice activation word to something else easily enough - the audio equivalent of a password - to enable voice control on a Vista machine.

---

### Post by raul_ on 2007-02-04
I was being ironic. Honestly, i just like to leave my pc download stuff while i'm in college. I think the argument "Oh but everybody knows that you have to use firewall,anti-virus,can't leave your pc  on if you're not in the room,gotta be careful with the sites you visit, don't open e-mails, etc etc....if you don't do these things OF COURSE you're going to get a virus..DUHH"...what's the logic of that? 

Since i'm with Linux i really don't give a crap about what sites i visit, what mails i get, or if i leave my pc on. Maybe i'm just careless or lucky but in 1 year nothing whatsoever happened to my system

---

### Post by erlyrisa on 2007-02-09
My XP machinee has been running non-stop for 5years - no viruses, no resets.

I do dtp with corelDraw on it and occassionally do WebPub on it.

-It is also the server for all info for all me other computers that get switched off.
-It is also the server for the printer (and of course it has tobe becuase there is no driver for me linux machine - which I still can't print with and I have had 4 printers in that time)
-It is also only a P3-1G 256Mb (was 128 - so I lie, I have switched it off a time or two)

So - a little thing about sound being able to instruct a computer - hmm again I say, can't wait to get me hands on Vista.

PS - My Linux machine sometimes resets at night when I am not watching - Is some-one hacking me? -it only happens once in a blue moon, thing is My XP machine has never done this.

PPS: I like linux, I have Ubuntu Running 24/7 ,but don't knock Msoft so much - it's just as good.

---

### Post by Brunellus on 2007-02-09
> **erlyrisa said:**
> My XP machinee has been running non-stop for 5years - no viruses, no resets.

I do dtp with corelDraw on it and occassionally do WebPub on it.

-It is also the server for all info for all me other computers that get switched off.
-It is also the server for the printer (and of course it has tobe becuase there is no driver for me linux machine - which I still can't print with and I have had 4 printers in that time)
-It is also only a P3-1G 256Mb (was 128 - so I lie, I have switched it off a time or two)

So - a little thing about sound being able to instruct a computer - hmm again I say, can't wait to get me hands on Vista.

PS - My Linux machine sometimes resets at night when I am not watching - Is some-one hacking me? -it only happens once in a blue moon, thing is My XP machine has never done this.

PPS: I like linux, I have Ubuntu Running 24/7 ,but don't knock Msoft so much - it's just as good.
if you have been running XP without a reboot for five years, then you haven't applied a single security patch in all that time.  If you were running on a local area network with me, I would disconnect your computer from the network--forcibly if necessary.

---

