---
title: "Does installing DEB files through USC in 11.04 work for anyone?"
date: 2011-05-02
forum: The Cafe
---

### Post by Shmantiv_Radio on 2011-05-02
I've reinstalled the OS 3 times with 3 different ISOs and this problem happens everytime.

Does it work for *anyone*?

---

### Post by nothingspecial on 2011-05-02
Well it didn't work for me

but ```
sudo dpkg -i blah.deb
```

does, so you don't need to keep reinstalling

---

### Post by Shmantiv_Radio on 2011-05-02
> **nothingspecial said:**
> Well it didn't work for me

but ```
sudo dpkg -i blah.deb
```

does, so you don't need to keep reinstalling

Thanks, but I know about dpkg lol, it's what I've had to use. The reinstalling was for other reasons not this.

---

### Post by cariboo on 2011-05-02
I personally don't like using the Software Center, so I installed gdebi, and set it as the default action to install debs.

The reason I don't like using the Software Center for installing debs, is that there is very little feedback during the install process, but it does work for me.

---

### Post by Shmantiv_Radio on 2011-05-02
> **cariboo907 said:**
> I personally don't like using the Software Center, so I installed gdebi, and set it as the default action to install debs.

The reason I don't like using the Software Center for installing debs, is that there is very little feedback during the install process, but it does work for me.

Someone else did recommend this, but given how unstable USC is for me ATM, I don't want to break anything.

What's the exact command you used to install Gdebi?

---

### Post by Legendary_Bibo on 2011-05-03
> **Shmantiv_Radio said:**
> Someone else did recommend this, but given how unstable USC is for me ATM, I don't want to break anything.

What's the exact command you used to install Gdebi?

```
sudo apt-get install gdebi
```

---

### Post by Shmantiv_Radio on 2011-05-03
> **Legendary_Bibo said:**
> ```
sudo apt-get install gdebi
```

Are you using GDebi in 11.04 instead of USC?

---

### Post by Legendary_Bibo on 2011-05-03
> **Shmantiv_Radio said:**
> Are you using GDebi in 11.04 instead of USC?

I'm not using 11.04. I never update the distro right away, I always wait 2-3 months when they have several of the bugs worked out.

---

### Post by Shmantiv_Radio on 2011-05-03
> **Legendary_Bibo said:**
> I'm not using 11.04. I never update the distro right away, I always wait 2-3 months when they have several of the bugs worked out.

Then I'll wait for Cairbo's reply as he's using 11.04.

Thanks anyway.

---

### Post by Legendary_Bibo on 2011-05-03
> **Shmantiv_Radio said:**
> Then I'll wait for Cairbo's reply as he's using 11.04.

Thanks anyway.

That's the command to install gdebi, that's what you were asking, Cariboo will just tell you the same command.

---

### Post by jerenept on 2011-05-03
> **Shmantiv_Radio said:**
> Then I'll wait for Cairbo's reply as he's using 11.04.

Thanks anyway.

I use 11.04, and I can assure you this is the correct command.

---

### Post by Shmantiv_Radio on 2011-05-03
> **jerenept said:**
> I use 11.04, and I can assure you this is the correct command.

Ok then I'll give it a go. :neutral:

---

### Post by Legendary_Bibo on 2011-05-03
> **Shmantiv_Radio said:**
> Ok then I'll give it a go. :neutral:

You might want to keep support requests in the Absolute Beginners next time.

---

### Post by Shmantiv_Radio on 2011-05-03
> **Legendary_Bibo said:**
> You might want to keep support requests in the Absolute Beginners next time.

This thread didn't start as any kind of support thing.

---

### Post by Legendary_Bibo on 2011-05-03
> **Shmantiv_Radio said:**
> This thread didn't start as any kind of support thing.

Your first post certainly sounded like it.

---

### Post by Shmantiv_Radio on 2011-05-03
> **Legendary_Bibo said:**
> Your first post certainly sounded like it.

A support thread would have been something like 

> I've reinstalled the OS 3 times with 3 different ISOs and this problem happens everytime.

*Detailed description of problem*

Help!


Thankfully I know how to use dpkg in Terminal. I was just curious how well it worked for others.

---

### Post by el_koraco on 2011-05-03
Dude, it seems like Natty really doesn't like you. i'm surprised you're sticking with it.

---

### Post by Shmantiv_Radio on 2011-05-03
> **el_koraco said:**
> Dude, it seems like Natty really doesn't like you. i'm surprised you're sticking with it.

I'm kind of in a catch 22. Natty is the only version of Ubuntu that gives me stable WIFI, and I'm not willing to waste any more of our download quota on more Linux ISOs. I'll give Natty until the end of the month (also when I get payed), and if it still hasn't improved stability wise, I'll just buy a USB DVD Drive and the cheapest version of Windows 7 I can find and be done with it.

---

### Post by kaldor on 2011-05-03
> **cariboo907 said:**
> I personally don't like using the Software Center, so I installed gdebi, and set it as the default action to install debs.

The reason I don't like using the Software Center for installing debs, is that there is very little feedback during the install process, but it does work for me.

Agreed.

Waiting 15+ seconds to load a simple .deb in USC is really not needed.

---

### Post by speedwell68 on 2011-05-03
> **kaldor said:**
> Agreed.

Waiting 15+ seconds to load a simple .deb in USC is really not needed.

Agreed, it is too slow for it's own good.  I use Gdebi for installing *.deb files, by far the best compromise.  For everything else I use a combination of apt-get in the terminal,Ubuntu Tweak, USC or the Synaptic Package Manager, depends on what I am doing really.

But I can confirm that Gdebi works perfectly in 11.04.  You can either keep *.DEB files associated with USC and right click on them and choose "Open with Gdebi" from the menu or change the file association so it works by just clicking on the file.  I changed the file association using Ubuntu Tweak.

---

### Post by el_koraco on 2011-05-03
> **Shmantiv_Radio said:**
> I'm kind of in a catch 22. Natty is the only version of Ubuntu that gives me stable WIFI, and I'm not willing to waste any more of our download quota on more Linux ISOs. I'll give Natty until the end of the month (also when I get payed), and if it still hasn't improved stability wise, I'll just buy a USB DVD Drive and the cheapest version of Windows 7 I can find and be done with it.

I higlhy doubt Natty will improve much by the end of the month. End of the year is more like it.

---

### Post by beew on 2011-05-03
Don't know if it works because I don't install .deb with the USC. I think the USC is slow and bloated and when start up uses a lot of cpu. If you want right click install of .deb files install gdebi, it is much faster than the USC. For other task like installing from repositories and updating I always sue Synaptic, much faster and with a lot more options. The USC is garbage, bloatware.

---

### Post by beew on 2011-05-03
> **Shmantiv_Radio said:**
> I'm kind of in a catch 22. Natty is the only version of Ubuntu that gives me stable WIFI, and I'm not willing to waste any more of our download quota on more Linux ISOs. I'll give Natty until the end of the month (also when I get payed), and if it still hasn't improved stability wise, I'll just buy a USB DVD Drive and the cheapest version of Windows 7 I can find and be done with it.

Don't know what card you have but wifi works out of the box for me for all Ubuntus since 10.04 and I have a few different machines with different cards. Maybe you can get a usb wifi card. This one is about $15 and works on all Ubuntu versions I have tried (11.04, 10.10, 10.04)

[http://www.cty.ca/ProductDetails.asp?pid=3267](http://www.cty.ca/ProductDetails.asp?pid=3267)

---

### Post by Shmantiv_Radio on 2011-05-03
> **beew said:**
> Don't know what card you have but wifi works out of the box for me for all Ubuntus since 10.04 and I have a few different machines with different cards. Maybe you can get a usb wifi card. This one is about $15 and works on all Ubuntu versions I have tried (11.04, 10.10, 10.04)

[http://www.cty.ca/ProductDetails.asp?pid=3267](http://www.cty.ca/ProductDetails.asp?pid=3267)

Thanks but a USB dongle is not really practicable. My only PC is a netbook and I would quite likely forget about the dongle and stuff it in a bag and bend the thing up. I may possibly look into replacing the internal WIFI adaptor if I can, but I'm not a fan of opening my PC up.

---

