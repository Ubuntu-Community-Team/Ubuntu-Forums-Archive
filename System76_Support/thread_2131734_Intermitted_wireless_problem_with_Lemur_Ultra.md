---
title: "Intermitted wireless problem with Lemur Ultra"
date: 2013-04-02
forum: System76 Support
---

### Post by krpasundarananda on 2013-04-02
Hello,

Since I bought this computer last year I have been having trouble with wireless.

It connects but after some time (sometimes minutes, sometimes hours) the connection breaks. Sometimes using F11 to turn off and on the power resolves the problem sometimes a full reset seems to be needed. It is a very frustrating problem that makes me want to go back to Mac... Anyhow not yet giving up :-)

Other computers (Mac & Windows) have no problem at all to have a stable connection with the same wireless router. Resetting the router does not help in any way. Even plugging in an external usb wifi card (one that works fine with other computers) is not solving the problem. So it seems the problem is software related.

In an earlier discussion directly with support last year I was told to reinstall Ubuntu. Doing this did not solve the problem. The computer has the Ubuntu LTS version 12.04 installed, and all updates are applied.

Any help would be really appriciated.

Sincerely,
Dada Krpasundarananda

---

### Post by isantop on 2013-04-02
If you've reinstalled Ubuntu, there isn't really a way it can be software related. This is the only case like this that we've had.

I'm putting my money on a bad router. Does it happen on any other networks?

---

### Post by krpasundarananda on 2013-04-02
Well, the thing is that no other computer has trouble connecting to the same router. (And we have a lot of people passing through who all connect without trouble with phones, tablets, notebook computers and what not)

Further more the USB Wifi card I have has the same trouble on the Lemur and no problem when connected to other computers and the same router.

That said the problem is worse with the internal card than with the external one. It is a bit better when closer to the router. Maybe there is software signal processing that is different in the wifi driver on the Lemur then on commercial operating systems? Would there be alternative drivers?
 
Could it help to upgrade Ubuntu to the latest version or better stay with the LTS version. 

Thanks so much.

---

### Post by isantop on 2013-04-03
We're not hearing reports of this on other Lemurs, so assuming your software is good (which is likely since you reinstalled), you shouldn't be having trouble.

I've seen cases before where a router would get finicky and develop problems with one specific computer. Does the laptop work correctly on other networks?

---

### Post by krpasundarananda on 2013-04-04
I found an article about trouble of similar trouble and turning off the n mode solved the problem.

[INDENT]"The Intel drivers often barf on wireless n mode - you could try this
[http://ubuntuforums.org/showthread.p...hlight=iwlwifi](http://ubuntuforums.org/showthread.p...hlight=iwlwifi)"[/INDENT]

Not sure if that applies but I will try it and see.

My partner (who is actually using the computer) did not remember if there was trouble in other places. So maybe it's indeed some bad chemistry between our home router and the lemur...
If not resolved with disabeling the n mode we'll see if telmex can provide a new modem.

Thanks so much!
Dada K

---

