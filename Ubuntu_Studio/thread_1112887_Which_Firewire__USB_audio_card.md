---
title: "Which Firewire / USB audio card?"
date: 2009-04-01
forum: Ubuntu Studio
---

### Post by aepuras on 2009-04-01
Hi,

I'm thinking of buying a decent(cheep and performant :D) audio card for my laptop to use with my MIDI keyboard and my guitar.

Can anyone help me with this decision?

Cheers,
Adrian

---

### Post by aepuras on 2009-04-01
I was thinking of something like Edirol FA-66.

[http://www.rolandus.com/products/productdetails.aspx?ObjectId=731&ParentId=114](http://www.rolandus.com/products/productdetails.aspx?ObjectId=731&ParentId=114)

Anyone using one of those??

---

### Post by Stochastic on 2009-04-01
With FFADO support just about to land in Jaunty, I'd highly recommend choosing a card that has a supported rating from this list: [http://www.ffado.org/?q=devicesupport/list](http://www.ffado.org/?q=devicesupport/list)

I personally have a Presonus card and am really enjoying the preamps & overall sound quality.

I've never liked the sound of Edirol, but that's just my personal preference.

The Edirol FA-66 is listed as fully supported.  Presonus has a similar card in the similar pricerange that should work just fine.

---

### Post by fedexnman on 2009-04-01
ffado support when ??

---

### Post by pedrogent on 2009-04-04
> **fedexnman said:**
> ffado support when ??

ditto. it is SO frustrating trying to get a decent audio interface working with linux. i'm forced to run windows to get good sound. then when i need to do everything else i switch back to linux...

how long oh lord? how long?

---

### Post by babarosa on 2009-04-04
Hi, 

my precise advice:

If you can grab one, purchase a "Terratec Phase88 Rack Firewire". They are available at very low prices (e.g. €299,-), offer fine audio quality and work very well with _ffado thus gnu/linux-systems_.
You'll get 4 analog and 1 digital in- and outputs with 2 phantom powered XLR-Ins in a 1 height 19" unit.

Regards,
Michael

---

### Post by Stochastic on 2009-04-04
> **fedexnman said:**
> ffado support when ??

As I said, ffado is in the repos in Jaunty.
Jaunty's official release is set for April 23rd (just a couple weeks from now).

For earlier versions of ubuntu there is the freebob driver (what ffado evolved from).

> **pedrogent said:**
> ditto. it is SO frustrating trying to get a decent audio interface working with linux. i'm forced to run windows to get good sound. then when i need to do everything else i switch back to linux...

how long oh lord? how long?

Pedrogent, there are countless excellent audio cards that work in Ubuntu (even before ffado support), and countless others that never will.  Your comment really isn't specific enough for anyone here to help you get things working.  I've been recording in Linux for the past five years with excellent quality results - no windows needed.

---

### Post by fedexnman on 2009-04-05
thx stochastic on the ffado update, im new to linux and ubuntu, i noticed ur a real help on the forums here too.    ive been playin with ardour on a macbook , n plan on building a new pc. ( using n windows xp n ubuntu 9.04 partition ) the effects seem descent in ardour n i know midi n vst n vsti  with wine is coming soon. thx this is pretty exciting news for linux audio..:guitar:

---

### Post by pedrogent on 2009-04-08
> **Stochastic said:**
> As I said, ffado is in the repos in Jaunty.
Pedrogent, there are countless excellent audio cards that work in Ubuntu (even before ffado support), and countless others that never will.  Your comment really isn't specific enough for anyone here to help you get things working.  I've been recording in Linux for the past five years with excellent quality results - no windows needed.

Well, if someone can help me get an M-Audio FireWire Solo up & running I'm all ears (or eyes). It's the one thing holding me back from full-time Linux use.

I've seen the "WestCoastSuccess" method but it didn't work for me.

Any idea if ffado is going to bring me joy? It'd be great if it does.

:guitar:

---

### Post by Stochastic on 2009-04-08
> **pedrogent said:**
> Well, if someone can help me get an M-Audio FireWire Solo up & running I'm all ears (or eyes). It's the one thing holding me back from full-time Linux use.

I've seen the "WestCoastSuccess" method but it didn't work for me.

Any idea if ffado is going to bring me joy? It'd be great if it does.

:guitar:

Hmm, [the ffado device listings]("http://www.ffado.org/?q=devicesupport%2Flist&filter0=audio&filter1=&op2=OR") show that your card might work with ffado.  

M-Audio was very pro-linux a while back and released their chipsets freely (even hosted some linux drivers for a while) but I think the makers of ProTools took that company over and their policies toward open hardware greatly diminished.  Because of all this, their firewire line is very poorly supported while their older PCI line (and possibly USB) is quite stable (like a rock) in Linux.

This is a perfect case where you should phone up the company and request a driver for your OS.  Maybe even include the line "I know you used to have a download site for Linux," and upon the probable rejection of your request, I might also suggest a quick witted, "well good thing I still have the return receipt!" (even if you don't)  The only way companies will support open hardware standards is if they see their bottom line improving because of it.

---

### Post by pedrogent on 2009-04-08
> **Stochastic said:**
> Hmm, [the ffado device listings]("http://www.ffado.org/?q=devicesupport%2Flist&filter0=audio&filter1=&op2=OR") show that your card might work with ffado.  

This is a perfect case where you should phone up the company and request a driver for your OS....  The only way companies will support open hardware standards is if they see their bottom line improving because of it.

First, this is great news if indeed my card does get supported under Linux. It would make me extremely happy to be able to do away with Windows.

Second, I, like huge numbers of other people waited 21 - that's right: 21 - months for M-Audio to release a driver of any nature for Vista for the FireWire Solo (as well as many other of their products). 21 months! Many of said people wrote to M-Audio and were stonewalled for said 21 months.

It's worth joining up the M-Audio user forums just to see the response we got.

So, yeh, I've done the phoning up the company bit with these folks. It would be fair to say they're not moved by such things. It would also be fair to say the Linux community will be receiving [COLOR="Red"]**ZERO**[/COLOR] input from them driver wise. They couldn't even be bothered for Vista!

---

