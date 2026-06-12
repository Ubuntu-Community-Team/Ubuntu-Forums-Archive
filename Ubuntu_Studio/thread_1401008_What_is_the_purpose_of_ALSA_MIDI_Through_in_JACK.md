---
title: "What is the purpose of ALSA MIDI Through in JACK?"
date: 2010-02-07
forum: Ubuntu Studio
---

### Post by mango42 on 2010-02-07
Perhaps I am being dense or suffering some kind of mental block but I have found zero information on this most fundamental of features, found listed in JACK's Connection and Patchbay panels.

Where does one 'Through' *to* in a virtual environment, where all programs that recognise JACK have their own INs and OUTs listed?

What have *you* used it for?

---

### Post by robeast on 2010-02-07
Simply to use MIDI devices and connections with programs that use JACK--that's how I understand it anyway. Convenient to have all the connections in the same place so you don't have to manage 2 patch bays.

---

### Post by AutoStatic on 2010-02-08
Hello mango42, it can be useful when you have an USB keyboard and a softsynth with JACK MIDI only (like [Yoshimi]("http://yoshimi.sourceforge.net/")). Then after firing up **a2jmidid** you can connect your keyboard to the Yoshimi JACK MIDI port with the help of the MIDI Through ports. Of course you can export your keyboard too with **a2jmidid -e hw-id-of-keyboard** also.
And besides, my guess it's there for legacy reasons too since most MIDI devices have a MIDI Through port. I'm not a MIDI guru so can't tell out of my head what the purpose is of MIDI Through.

---

### Post by trulan on 2010-02-08
Would routing a midi device through the 'through' port enable it to obey Jack transport?  I'm just learning the ins and outs of midi so that's an honest question, not a statement.

---

### Post by mango42 on 2010-02-08
Many thanks for the responses though I am none the wiser ;-)

I have worked with MIDI for over 20 years now and I'm quite used to being baffled but this ALSA midi thru has me beat so far. I have tried various combinations in JACK's Patchbay - perhaps I should get some screenshots together to clarify my dilemma?

Thanks also for the reminder about **a2jmidid** as I am looking forward to trying **Yoshimi** 'real soon now'.

This is probably not good 'board' ethic here but could I direct the attention of firewire enthusiasts to my unanswered query at:-

[http://ubuntuforums.org/showthread.php?p=8783076#post8783076](http://ubuntuforums.org/showthread.php?p=8783076#post8783076)

Meanwhile I continue my explorations of DAWs - tending towards the excellent Senhor Capela's **Qtractor** at the moment, if only because he brought us GUI bliss in the form of **QJackCtl**...

---

### Post by AutoStatic on 2010-02-08
Maybe this will make things a bit clearer: [http://www.youtube.com/watch?v=18G8G9pRAxE](http://www.youtube.com/watch?v=18G8G9pRAxE)

As you can see I hook up the Virtual Keyboard to Arpage in the JACK MIDI tab. But I could also hook it up to the MIDI Through input port in the ALSA tab and then connect Arpage to the MIDI Through output port in the JACK MIDI tab.

---

### Post by mango42 on 2010-02-08
> **AutoStatic said:**
> Maybe this will make things a bit clearer: 

A youtube clip is worth a thousand screen dumps? ;-)

Your mouse movements are almost as fast as your music <big grin> but from what you so clearly demonstrate, it's obvious I am making a difficulty out of a possible non-issue. Is this a facet of years of expecting an OS & DAW to fight you all the way, I wonder?

Shrugs off redundant mindset; starts jamming...

Thanks, as always, AutoStatic :)

---

### Post by AutoStatic on 2010-02-08
> **mango42 said:**
> A youtube clip is worth a thousand screen dumps? ;-):D I had already uploaded it for another purpose.

> **mango42 said:**
> Your mouse movements are almost as fast as your music <big grin>Hey, stop making fun of my carpal repetitive strain tunnel injury syndrome ;) I got it because of years of shredding. That's why I turned to using computers. But it's not making much of a difference I guess :roll:

> **mango42 said:**
> but from what you so clearly demonstrate, it's obvious I am making a difficulty out of a possible non-issue. Is this a facet of years of expecting an OS & DAW to fight you all the way, I wonder?Maybe, maybe. But you never know, some day you might end up in a situation where it might come in handy ;)

> **mango42 said:**
> Shrugs off redundant mindset; starts jamming...

Thanks, as always, AutoStatic :)You're welcome, have fun jamming!

---

### Post by markbuntu on 2010-02-12
patchage is really helpful for getting the big picture of how everything is connected up all wrong and fixing it click click click.....

---

### Post by robeast on 2010-02-12
> **AutoStatic said:**
> 
Hey, stop making fun of my carpal repetitive strain tunnel injury syndrome ;) I got it because of years of shredding. That's why I turned to using computers. But it's not making much of a difference I guess :roll:!

WTF?!? You don't STOP shredding! Stevie Vai will visit you in the night and molest you with his guitar's head stock.

---

### Post by AutoStatic on 2010-02-13
Oh then I don't have to worry because those wizard necks and headstocks don't make such a big impact. I would be more afraid if it were Slash or some other LP player. 6 kgs of wood and a big ol' Gibson headstock hurt way more.

But let's not drift away too much ;)

---

### Post by mango42 on 2010-02-13
> **markbuntu said:**
> patchage is really helpful for getting the big picture of how everything is connected up all wrong and fixing it click click click.....

Thanks for the suggestion.

Reminds me of that old saw: "logic is mankind's most developed method yet for going utterly wrong with complete confidence"

When I've figured out why arpage doesn't arp and yoshimi doesn't er shimi I'll check to see whether patchage still folds on startup... ;-)

---

### Post by trulan on 2010-02-19
I moved to Jack2 (from frasten's ppa) specifically because patchage doesn't seem to like the version of Jack in 9.10.  I had been looking for a Karmic build of Jack 0.118 but everything I found was either the original 0.116 (with which, as you said, patchage always folds on startup) or Jack2 (with which patchage works).  I get more xruns in jack2, but they are much smaller.  Whatever that's worth...

---

