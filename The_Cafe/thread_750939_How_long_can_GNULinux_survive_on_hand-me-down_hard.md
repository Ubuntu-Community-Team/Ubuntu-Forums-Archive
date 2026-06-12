---
title: "How long can GNU/Linux survive on hand-me-down hardware?"
date: 2008-04-10
forum: The Cafe
---

### Post by BetterSense on 2008-04-10
Face the facts...linux grew up in the shadow of MS and has always depended on the early MS decision to open up the hardware to third-parties, in contrast to the Macs. It's the existence of cheap PC hardware that has allowed it to get where it is today. 

But today, hardware compatibility is still a sticking point, as manufacturers continue to make products for MS and linux devs try to back-engineer drivers for them. OR, the manufacturers (such as Nvidia) throw the linux crowd a bone by releasing binary drivers, which violate the spirit of the thing. The status quo remains the same, we build our linux computers with hardware designed for MS. 

What if Nvidia just released a GFX card with good documentation and open source drivers? They don't do that because they compete with ATI. But how long will it be before companies spring up that are content to just build hardware, and send it out free and clear? What if companies built hardware with no regard to the DRM interests of microsoft et al and released some very powerful stuff that was completely open?

They'd go out of business because their product wouldn't be Vista-certified, that's what. But how big must linux market share get before it becomes profitable to do just that? Look at the WRT54G router....everyone buys it so that they can instantly install 3rd party firmware, which the manufacturer is completely not liable for, so that they can turn the Xmit power up past FCC regs. It seems like a good business model to release hardware with sweet hackability and specs (and perhaps a token driver for it), so that the OS community can run with it.

---

### Post by Ocxic on 2008-04-10
you don't need open source drivers, yes they are a good thing but asking the dev's to keep up with every new piece of hardware that comes out is just too much.. just because it's not open source doesn't make it a bad thing.

the reason proprietary drivers are not open source is because there is more information relating to the hardware then what is just owned by Nvidia/ATI etc.. other companies and organizations also have code/specifications that would be needed to be released as well.

it's just like saying your not gonna use Photoshop because it's not open source, yes there is Gimp and it is a great piece of software but it's still not a good as Photoshop.

---

### Post by BetterSense on 2008-04-10
> you don't need open source drivers, yes they are a good thing but asking the dev's to keep up with every new piece of hardware that comes out is just too much..

The manufacturers could release open source drivers, but of course they can't/won't....but why couldn't there be a company that DID?

Imagine that 90% of desktop users ran linux. Would that whole population STILL be using proprietary drivers? Or would a 'Linux certified FOSH' sticker on the box be a better selling point than 'Vista ready'?

The status quo is what it is because of the relative obscurity of linux, but at what point would/will/could that begin to change?

---

### Post by tamoneya on 2008-04-10
currently the trend is rising software prices and falling hardware prices.  as the ratio of software price: hardware price linux becomes more and more attractive.  Its market share has been going up in the past couple months according to web statistics.

---

### Post by Saint Angeles on 2008-04-10
> **BetterSense said:**
> Face the facts...linux grew up in the shadow of MS and has always depended on the early MS decision to open up the hardware to third-parties, in contrast to the Macs. It's the existence of cheap PC hardware that has allowed it to get where it is today.
linux - 1991 (i think)

and from what i've seen, linux has looked WAY slicker and advanced than windows.

i remember in 1999 (I was on windows 98 SE) and my buddy was showing me his desktop with enlightenment. it was doing stuff that vista can't compete with now (9 years later)

in 2018 when microsoft has something comparable to compiz... all the microsoft fanboys will "oooh" and "aaah" while i laugh inside with my virtual hologram spinning reality linux software.

windows is the way it is because of its 3rd party developers and hardware support (all acquiered through illegal monopolistic practices).

---

### Post by dasunst3r on 2008-04-10
You're right.  Linux did grow up in the shadows of Microsoft.  The cards were stacked against it.  But in running any distribution, I would like you to appreciate the obstacles it overcame.

I, like many others, am grateful that nVidia writes drivers for Linux (they're darn good at that).  By helping us, they help themselves because they have a significant head start compared to ATi.  Indeed, I had a laptop that had an ATi card, and the drivers were horrible!  When I shopped for a new laptop last year, that carried a significant amount of weight because I *required* that my laptop is equipped with an nVidia graphics card.  What can nVidia say about my money?  It's surely better in their pocket than ATi's, right? ;)

This may sound convoluted, but hardware incompatibilities serve as a small blessing for me.  I feel that it has forced me to buy better hardware.  This ultimately leads to a better computing experience in both Linux *and* Windows.  To me, the open-sourcing of drivers is a sign of good will, and you must recognize that good will goes a long, long way.

I am confident that as long as there is a community of users and developers, GNU/Linux will be here.  You don't need to look far to see that there are people who benefit financially from Linux and open-source.  Finally, as I mentioned earlier, good will goes a long way in ensuring loyalty and profitability.

---

### Post by saulgoode on 2008-04-10
> **BetterSense said:**
> What if Nvidia just released a GFX card with good documentation and open source drivers? ...

Do you mean [like...](http://www.phoronix.com/scan.php?page=news_item&px=NjI3NQ)?

70% of the computing market is NOT the desktop, and Linux+BSD dominates that non-desktop market. Ignore at your own peril.

---

### Post by mridkash on 2008-04-10
Interesting discussion.

I also support the open source drivers thing.
I prefer gadgets which can be used without being bound to one company. Like cameras which have standard usb port, mobile phones which can be charged using a standard charger, or memory cards which can be used in many devices.

Similarly, I want my computer hardware, a graphics card which can be used in any computer regardless of OS, like a keyboard or mouse.

---

### Post by toupeiro on 2008-04-10
> **saulgoode said:**
> Do you mean [like...](http://www.phoronix.com/scan.php?page=news_item&px=NjI3NQ)?

70% of the computing market is NOT the desktop, and Linux+BSD dominates that non-desktop market. Ignore at your own peril.

peril?  wow...

I don't even know that you can truthfully make that statement.

Unless something has changed rather drastically, Solaris still holds the non-desktop/corporate UNIX majority, and its roots since the SunOS to Solaris changeover (somewhere around 2.0) have been system V, not BSD.  Even RedHat and SuSE's fundamental toolsets come from System V which hold the lions share of enterprise linux today.  If you work out of init states in UNIX or Linux (rc0.d, rc1.d etc etc..)  you are using System V init states.  BSD never adopted multiple init states.

As far as drivers,  I make it a point wherever possible, to boycott using vendors that make hardware only for windows.  There is a guideline and ISO/IEEE standard for IBM/PC hardware development, and that does not include Windows framework requirements.  This puts the task more on me to do my research well, but if you're the kind of person who gets his new PC in parts from Fryes rather than Dell.com, you should be well versed in what to look for.  Companies like Logitech and Creative have not gotten much business from me over the last several years.  I admit I did buy a Zen, but it works in linux, whereas their late model Soundblaster cards don't do much work at all in any operating system you run them in.

---

### Post by swoll1980 on 2008-04-10
microsoft didn't create the harware standard IBM did. MS was IBM compatable not the other way around

---

### Post by toupeiro on 2008-04-10
> **swoll1980 said:**
> microsoft didn't create the harware standard IBM did. MS was IBM compatable not the other way around

yes, thats pretty much what I was getting at....

---

### Post by billgoldberg on 2008-04-10
> **BetterSense said:**
> Face the facts...linux grew up in the shadow of MS and has always depended on the early MS decision to open up the hardware to third-parties, in contrast to the Macs. It's the existence of cheap PC hardware that has allowed it to get where it is today. 

But today, hardware compatibility is still a sticking point, as manufacturers continue to make products for MS and linux devs try to back-engineer drivers for them. OR, the manufacturers (such as Nvidia) throw the linux crowd a bone by releasing binary drivers, which violate the spirit of the thing. The status quo remains the same, we build our linux computers with hardware designed for MS. 

What if Nvidia just released a GFX card with good documentation and open source drivers? They don't do that because they compete with ATI. But how long will it be before companies spring up that are content to just build hardware, and send it out free and clear? What if companies built hardware with no regard to the DRM interests of microsoft et al and released some very powerful stuff that was completely open?

They'd go out of business because their product wouldn't be Vista-certified, that's what. But how big must linux market share get before it becomes profitable to do just that? Look at the WRT54G router....everyone buys it so that they can instantly install 3rd party firmware, which the manufacturer is completely not liable for, so that they can turn the Xmit power up past FCC regs. It seems like a good business model to release hardware with sweet hackability and specs (and perhaps a token driver for it), so that the OS community can run with it.

I don't see why manufactures bringing out open source drivers would make them vista uncertified. They choose to bring out propitiatory drivers, but they could make them open source, it might even be better for them.

And I'm pretty sure linux wasn't build as an answer to MS, but as an answer to sun's operating system (could be wrong).

Linux might be behind on the desktop, but it has always been master on the servers.

---

### Post by bigbrovar on 2008-04-10
i think with time attitude would change .. imagine even ATI made an open source driver .. with time Nvidia would not be able to resist the urge to follow suit .. and with companies like dell,asus,hp acer and others shipping linux as  mainstream computer .. there  would have to choose hardware with open source drivers which would be fully compactible with this pc .. with time hardware vendors would start making open source drivers for linux.. but we users too have a role to play.. we should vote with our pocket.. dont think that it wont make a different.. the Computer hardware industry is very competitive and every company is looking for something to give them an edge ..if company believes that it can make money by befriending linux users it would make its hardware drivers open .. this companies dont share the loffty ideas of Linux all the want is money and more money .. lets vote with our pocket buy only from hardware makers that have make open source drivers ..ignore and boycott close source hardware if u can ..

---

### Post by Extreme Coder on 2008-04-10
What most people here seem to forget that companies are already opening up their drivers, most importantly ATi, which have improved their driver's quality by a lot, and are opening up docs for their cards.
And I just read yesterday on Phoronix, that VIA is planning to make better Linux drivers and open up docs as well.. and Intel recently opened documentation for their latest IGP.

---

