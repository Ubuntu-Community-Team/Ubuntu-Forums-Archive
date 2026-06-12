---
title: "Hydrogen quandary"
date: 2010-05-07
forum: Ubuntu Studio
---

### Post by mango42 on 2010-05-07
Whilst I appreciate this might be better asked on the Hydrogen mailing list, I thought I would try here first...

Pattern Mode. Okay, so I have generated the first pattern; I then want to *clone* into the second pattern slot so I can create a small variation; I then want to clone it again - but there doesn't appear to be a 'clone' option and I still haven't fully figured out how, where and why Hydrogen saves stuff.

:confused:

Is there a quick, ergonomic way to do this? Perhaps I'm just being dense?

---

### Post by c00kie55 on 2010-05-07
sorry dont you mean copy?

iam using ver 0.9.5-svn1728 and its easy just select a pattern right click and select copy
a new pattern will come at bottom of the pattern list you can move that up, down and rename even copy it so it becomes copy of the copied pattern
but you have to be in song mode to hear a  variation

---

### Post by sgx on 2010-05-07
> **mango42 said:**
> Whilst I appreciate this might be better asked on the Hydrogen mailing list, I thought I would try here first...

Pattern Mode. Okay, so I have generated the first pattern; I then want to *clone* into the second pattern slot so I can create a small variation; I then want to clone it again - but there doesn't appear to be a 'clone' option and I still haven't fully figured out how, where and why Hydrogen saves stuff.

:confused:

Is there a quick, ergonomic way to do this? Perhaps I'm just being dense?
HI, you can right click on pattern 2 from the list of patterns on the left (not its icon on the grid) , and choose a new pattern from ones you have saved. This can be a folder wherever its convenient. Save pattern 1 first if you want to load it as a template. Lots of features in hydrogen,
no density required ;)

here is my tip on kit design, for people who missed it.

--------------------------------------------------------------------------

A simple new 'no brainer' how2 guide for Hydrogen 9.4 drumkits!

Make a folder called something like a1samples in your user directory (so its convieniently at the top of file-requestor lists).
Fill it with the samples for your new kit, .wav, flac, whatever Hydrogen can take.
Start hydrogen, then

1. load a drumkit that contains as many, or more drums than the kit you will be making, (the limit is 32).
2. select the first drum in the kit you loaded. (its probably already selected)
3. click the 'Instrument' button on the right side of the gui, a third of the way down.
4. click the 'Layers button' below that.
5. click the 'Delete Layer' button, even further below (this will soon remove the first drum in the kit you started from)
6. click the 'Load Layer' button, this will open a file browser, so browse to your asamples folder, and select a sample for the first drum in your kit. 
7. click the check-box by 'Filename to instrument name'.
8. click the 'Open' button. Now the name changes for the first drum in the list of the kit you started with, to the name of its replacement.
9. select the second drum from the kit you started with, and repeat steps 4 through 9 incrementally, and keep doing this repetitious process till you use all the samples you intend to.
10. now go to the Instruments menu, and choose 'Export library', and give it a name in the popup that appears.
11. now again in the Instruments menu, choose 'Save library'. Give it a name, fill in more info if desired, in the other fields, and you're done. And ready to make the next one!

Remember, Computer Music Magazine dvds are bristling with samples, just waiting for new creative homes.

As a bonus, there is Gamelan drumkit out there for Hydrogen, if you are good at google, you can find it, and the free samples it was made from. There are more than 50 samples, so with audacity skills, the extra samples could make a second kit! The kit itself uses 32 of them, and is a hair over 18 megs of melodic goodness!

Another good thing for Hydrogen drums, you can run extra instances of Hydrogen, and have different kits with diverse instruments playing the same beats, or syncopated beats.
And of course your FX options can grow along the same lines. For example,
make a kit of white/pink noise elements, and share the song with a brash 626 kit, and an accoustic kit with some reverb/delay on it.
You may find a specialized percussion soundfont, start timemachine, and record the sounds at the different velocities you can muster from your kkeyboard/gear, and go back with audacity, and slice out the ones you want for a custom kit.
Do another recording while different delay taps are utilized, soon, you'll have a very beneficial library to get ingrained in your memory, and migrate to your music.

when hydrogen is running, you can connect it to rakarrack, and if you're good with the mouse, you can drag the rakarrack EQ (start around 500 hz) and other sliders back and forth, while recording with timemachine, to liven up beats that might lean towards being static or lifeless. Then you can edit the best parts into some dynamic tracks for later productions, using audacity to

select all
copy
fast-forward
paste

Cheers

---

### Post by KoRnholio on 2010-05-07
> **c00kie55 said:**
> sorry dont you mean copy?

iam using ver 0.9.5-svn1728 and its easy just select a pattern right click and select copy
a new pattern will come at bottom of the pattern list you can move that up, down and rename even copy it so it becomes copy of the copied pattern
but you have to be in song mode to hear a  variation

I have that too. Although my version is 0.9.5-svnsomething, I wouldn't be surprised if that feature has been in there for a long time.

---

### Post by fedexnman on 2010-05-07
hydrogen kicks butt, step sequencer, sample import, and its free, computer music mag always has pretty cool drum samples each month too, to play with.

---

### Post by mango42 on 2010-05-08
Thanks, particularly to **sgx** - I suspected it was me being 'awkward' ):P And yes, I do have a pet folder for patterns, called 'Hydrogenation' but Hydrogen doesn't seem to want to go there by default.

I certainly had no intention of 'knocking' Hydrogen in any way, as I totally agree that it seems, even on these early attempts, to be an amazing program, with some marvelous samples built in and endless possibilities as a sampler/sequencer/beat-box.

But... I still reckon, for those 'heat-of-the-moments' when playing up to 4 keyboards live whilst running QTractor+Hydrogen+Plugins+keeping a careful eye on xruns, a 'clone' function in those right-click-on-pattern-list menus would do wonders for on-the-fly creativity. Whereas 'stop what you're doing, think of a name, think of a folder, save pattern, move to next empty pattern space, right-click to load previous pattern, remember where the heck it was saved to, navigate to it, reload into new pattern' - hmm, just doesn't cut it like instantaneous 'clone' could, IMO...

Caveat lector - no criticism implied! :guitar:

---

### Post by AutoStatic on 2010-05-08
mango42, which version are you using? I'm using the 0.9.5 svn version also and I can simply copy patterns on the fly. And saving patterns to folders? I don't grasp that, patterns are part of a project and projects can be saved in specific folders, yes. But not patterns.

---

### Post by KoRnholio on 2010-05-08
> **mango42 said:**
> Thanks, particularly to **sgx** - I suspected it was me being 'awkward' ):P And yes, I do have a pet folder for patterns, called 'Hydrogenation' but Hydrogen doesn't seem to want to go there by default.

I certainly had no intention of 'knocking' Hydrogen in any way, as I totally agree that it seems, even on these early attempts, to be an amazing program, with some marvelous samples built in and endless possibilities as a sampler/sequencer/beat-box.

But... I still reckon, for those 'heat-of-the-moments' when playing up to 4 keyboards live whilst running QTractor+Hydrogen+Plugins+keeping a careful eye on xruns, a 'clone' function in those right-click-on-pattern-list menus would do wonders for on-the-fly creativity. Whereas 'stop what you're doing, think of a name, think of a folder, save pattern, move to next empty pattern space, right-click to load previous pattern, remember where the heck it was saved to, navigate to it, reload into new pattern' - hmm, just doesn't cut it like instantaneous 'clone' could, IMO...

Caveat lector - no criticism implied! :guitar:

It might just be a matter of upgrading Hydrogen. I have Philip Johnsson's PPA for Karmic, which has a newer version of Hydrogen which *does* have this clone/copy feature you're wishing for.  Check it out here:

[https://launchpad.net/~philip5/+archive/extra](https://launchpad.net/~philip5/+archive/extra)

I assume you can also build the latest Hydrogen from source, but Philip's PPA is much easier.

---

### Post by mango42 on 2010-05-09
> **KoRnholio said:**
> It might just be a matter of upgrading Hydrogen. I have Philip Johnsson's PPA for Karmic, which has a newer version of Hydrogen which *does* have this clone/copy feature you're wishing for.  Check it out here:

[https://launchpad.net/~philip5/+archive/extra](https://launchpad.net/~philip5/+archive/extra)

I assume you can also build the latest Hydrogen from source, but Philip's PPA is much easier.

You assume incorrectly,**KoRnholio** ;-) I gave up coding for good back in the early nineties, for health/sanity reasons, so PPA generators have my total gratitude and undivided attention.

Okay. I seem to have created a mini-storm-in-a-coffee-cup here, all because I didn't have the latest version - now sorted and yes, **copy** does pretty much what I expected.

Thanks once again for all the helpful prompting.

@**AutoStatic**: I was working more along the lines of generating 'stock' patterns for use in various 'songs' - hence the idea of a pattern directory, housing various sub-folders by genre. I still have a great deal to learn about synth drums/machines, being well 'old school', not really knowing what to do without a pair of sticks in my hands ;-)

---
mango uno - an all-round mediocre noodler having a lot of fun, thanks to UbuntuStudio and this community :guitar:

---

### Post by sgx on 2010-05-09
I re-use saved patterns, saved songs, saved midi files, then make long jamtracks imported as media files into Reaper, stack up a few synths, and let 'er rip! A finished song that just needs a few jiggles and bangles here and there is pretty easy to fix, creating them on the fly in hydro.
Just don't forget to use non-percussion samples, vocal pads, ambient
tunnels, distant vibraphones, shreds you got lucky with, etc :)
Cheers

---

