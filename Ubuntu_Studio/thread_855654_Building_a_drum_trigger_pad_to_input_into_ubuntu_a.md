---
title: "Building a drum trigger pad to input into ubuntu and play samples."
date: 2008-07-10
forum: Ubuntu Studio
---

### Post by darkline on 2008-07-10
Hi all,

I don't even really know if this is possible, but if it is it would save me a lot of money (which of course i am short of) and make my music making far better:).

I would like to build a drum trigger pad and use it to play samples on my computer.
Building a trigger pad to set off a simple DC signal seems simple some pieces of rubber held apart with bare wires inside would work. Or i may be able to go advanced and do something like [this]("http://www.electronicdrums.com/pads/pads2.htm").

The part i don't know how to do is use this signal to set off a sample in my computer. I don't have a drum controller or MIDI interface atm. 

Is it possible to do this? I'm guessing if i can get the input into the computer some coding can be done to set off the samples. (I have a limited knowledge of coding, a way off doing this though).

I realise this may be impossible but.. if any help is forthcoming THANK YOU!!!:D

D.

---

### Post by Stochastic on 2008-07-10
> **darkline said:**
> Building a trigger pad to set off a simple DC signal seems simple some pieces of rubber held apart with bare wires inside would work. Or i may be able to go advanced and do something like [this]("http://www.electronicdrums.com/pads/pads2.htm").

The part i don't know how to do is use this signal to set off a sample in my computer. I don't have a drum controller or MIDI interface atm.

The problem with what you're describing is that computers work with binary digital signals (010011010110) and you're talking about triggering an analog voltage signal.  If you were to just feed that analog signal into a serial port on your PC then you'd need to code up a timing mechanism, make sure all the voltage levels are not about to damage anything (even if you hit 6 drums at once), then somehow translate all that data to a readable form for musical software (most likely hydrogen) - multichanneled and all.  This is not impossible, but in the end, that link you showed is the much simpler route and describes it in good detail.  It will most likely be the cheaper route too.

Getting a MIDI converter for your piezo contact microphones will not be that expensive either, as they've been around since the 80s, and haven't changed much in their basic technology.  ([check e-bay]("http://cgi.ebay.com/Aphex-Impulse-drum-trigger-to-midi-unit_W0QQitemZ160260180979QQcmdZViewItem?hash=item160260180979&_trksid=p3286.m14.l1318") or your local music store)

Then you just need a $20 USB MIDI adapter to send the MIDI data to Hydrogen.

---

### Post by slackwarebilly on 2008-07-13
I was you once. And I've been trying stuff like that for years. Here's where I got: the pads you see on that other site are what work the best, but drum modules are expensive (I got mine for 100 USD). I tried DC pads I designed triggering a hacked keyboard input, which kind of works, but is not very practical and effective for music making. I thought it was annoying to have to trigger 8 pads on my M-audio Delta 1010LT, but if you only need one or two, this could work. Do not buy a drum module, just make the pads with piezos and trigger with your computer. This [http://www.radioshack.com/product/index.jsp?productId=2062402&cp=&sr=1&origkw=piezo&kw=piezo&parentPage=search]("http://www.radioshack.com/product/index.jsp?productId=2062402&cp=&sr=1&origkw=piezo&kw=piezo&parentPage=search")
is the part you need. Radioshack stores have them in the drawers of electrical components in the "buzzers" drawer or seomthing. The box may say "piezo transducer." Basically just wire whatever jack you need for your sound card to the piezo. You will have to figure out which conductor is which for making it work, but it's just a matter of experimentation. You have a 50/50 chance of getting it right the first time. The LADSPA plugin you need for this is [http://sourceforge.net/projects/ladspa-trigger/]("http://sourceforge.net/projects/ladspa-trigger/")
Compile it, and I hope you know how to use ardour or something, because I don't want to explain jack and routing. Anyways, one last note on the piezos. The site you saw would have you believe that you need to make fancy pads to have a good drum. For the feel of adrum, yes, for the function of a drum (louder in the center softer at the edges) you can just attach the piezo to any hard surface. There is no need to take the cover off the piezo or "shell" it (unless you really want to, but it involves breaking plastic). My current setup is 8 pads that consist of an unshelled piezo attached to either cd's or plastic pads all on a rack I built. Just make sure you have lots of cardboard and duct tape before you start :D Before you make an actual pad, I recommend just wiring the piezo like I said, and seeing if you can get it working with the plugin. To test you just hit the thing. Make sure you have a sample loaded. There are also drum trigger plugins for windows, but I don't remember what they are. Hope this helps, and have fun with it. Although they may be using drum modules, you can get an idea of what's possible on youtube. [http://www.youtube.com/watch?v=wNGdwyxlKyI]("http://www.youtube.com/watch?v=wNGdwyxlKyI")

---

### Post by darkline on 2008-07-15
Thank you very much slackwarebilly!! Exactly the kind of think i was looking for.

When i get round to buying the piezos and building the things and everyything this will (hopefully) help a lot.

Im sure i can work out how to use ardour, i played about with it before but never properly. How hard can it be?:P

Thanks

---

### Post by hugoazevedo on 2009-11-17
> **darkline said:**
> Thank you very much slackwarebilly!! Exactly the kind of think i was looking for.

When i get round to buying the piezos and building the things and everyything this will (hopefully) help a lot.

Im sure i can work out how to use ardour, i played about with it before but never properly. How hard can it be?:P

Thanks

I know this is a pretty old thread, but I was curious - Did you manage to get this working, Darkline? If so, could you possibly describe it in as much detail as you can be bothered? ;)

Many thanks!

---

