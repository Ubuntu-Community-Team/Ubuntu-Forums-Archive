---
title: "Finally pulled the plug on the Windows box today."
date: 2007-12-02
forum: The Cafe
---

### Post by dwasifar on 2007-12-02
Linux has been my primary OS for a long time.  I use it on my main desktop, my laptop, a small server in the basement, and I always have an experimental machine set up to play with the latest interesting distro (right now it's running gOS).  But over at the end of my desk there has always been a Windows machine running for those few things I couldn't do in Linux.

For a long time now that list has only had two entries:

- DVDFab HD Decrypter. 
- QuickBooks.

Last week I decided to solve those last two problems. 

I've never had a problem running DVD Decrypter or DVDShrink under Wine, but DVDFab Decrypter always caused spontaneous reboots as soon as it started scanning a disc.  No one else on the forums was reporting this problem; everyone seemed to be fine running it under Wine.  So I thought, maybe this is just a hardware compatibility thing.  I swapped in a different DVD burner et voila - problem number one solved.  I wish it were faster, but I think that may be just an issue with the cheap burner I swapped in, so I'll try a Plextor or something like that and see what I get.

Quickbooks 2000 was a different story.  It would not install completely under Wine, because it was trying to install IE5 and failing, and then failing to run because of the missing IE5.  As an experiment I tried installing IE using the scripts at ies4linux, but that didn't help, probably because it doesn't install to the right place.  Forum and google searches failed to reveal anyone successfully running QB under Wine.  So I decided to bite the bullet, compromise a little, and install Crossover Office Standard.  This worked pretty well, leaving me with only two minor issues: PDF printing from Quickbooks, and a missing Times New Roman font.  The font was easily brought over from Windows, and the PDF printing was resolved by installing kdeprint and editing a file in cxoffice's configuration to use that as the default printer. 

So that was it.  The last two pieces were in place, and I shut down the Windows box.  Ironically, it installed a security update as it was shutting down.

Now the only Windows running in my house is on the laptop belonging to my consulting client.  No way to get away from that, unfortunately; I'm obliged to run their machine to connect to their systems and do the work.  But that doesn't really count.  For all intents and purposes I am Windows-free.

I feel strangely like this calls for cake, noisemakers, and paper hats.

---

### Post by Incense on 2007-12-02
Congratulations! :guitar:

BTW Have you looked into k9copy for your dvd shrinking/decrypting needs?

---

### Post by Linuxratty on 2007-12-02
Excellent news!
 No Windows here either...

---

### Post by dwasifar on 2007-12-02
> **Incense said:**
> Congratulations! :guitar:


Thanks :)

> **Incense said:**
> BTW Have you looked into k9copy for your dvd shrinking/decrypting needs?

Yes, I have; I've tried it a couple of times.  But I find that DVDFab HD Decrypter is usually more on the bleeding edge when it comes to handling new copy protection variants.

---

