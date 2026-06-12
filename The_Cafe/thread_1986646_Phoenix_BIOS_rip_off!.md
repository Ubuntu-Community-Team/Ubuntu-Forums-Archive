---
title: "Phoenix BIOS rip off!"
date: 2012-05-25
forum: The Cafe
---

### Post by yeehi on 2012-05-25
During installation of Ubuntu 12.04, I received an error message mentioning the BIOS. (Sorry, I can't remember what it was! I will check it out the next time i install.)

I decided to see if I could update the BIOS. I went to the Phoenix site and used their BiosAgent tool and discovered that my BIOS was out of date. (As were a few other drivers.)

To download the update I need to subscribe to BIOSAgentPlus and pay $29.95! That subscription only lasts for a year, too. 

What a rip off!

Shouldn't the BIOS be provided as a free download as part of the service for the hardware?

Can i get the BIOS update for free somehow?

Thank you!

---

### Post by lkraemer on 2012-05-25
Why not go to the Motherboard Manufacture's site and download their BIOS
for your specific motherboard along with the updated drivers?

Be sure to download their BIOS installation software also, and back up
your original BIOS as their documentation states.


lk

---

### Post by Haneef Mubarak on 2012-05-25
That's not what I see... What country are you in? BTW: [http://biosagentplus.com/join.php?bounce=http%3A%2F%2Fbiosagentplus.com%2F%3Fref%3D752]("http://biosagentplus.com/join.php?bounce=http%3A%2F%2Fbiosagentplus.com%2F%3Fref%3D752")

---

### Post by HalfNote5 on 2012-05-25
It seems as though you may have stumbled upon a third-party site.  Happens all the time when you're hunting down drivers (a-la "Download all your drivers now! Only $10!")- people hoping to turn a quick buck selling you something you can get for free...

So here's the deal - if it's an ASUS motherboard, you'll wanna go to ASUS.com.  If it's an Intel board, intel.com.  MSI and Gigabyte also supply free bios updates, as do most manufacturers. You can google the manufacturer directly. Most BIOS updates are under "Support"  "downloads" or "drivers" depending on the manufacturer/site.

You've simply been redirected to a third-party's advertisement in your travels.

---

### Post by oldos2er on 2012-05-25
Moved to Community Cafe.

---

### Post by CharlesA on 2012-05-25
> **HalfNote5 said:**
> It seems as though you may have stumbled upon a third-party site.  Happens all the time when you're hunting down drivers (a-la "Download all your drivers now! Only $10!")- people hoping to turn a quick buck selling you something you can get for free...

So here's the deal - if it's an ASUS motherboard, you'll wanna go to ASUS.com.  If it's an Intel board, intel.com.  MSI and Gigabyte also supply free bios updates, as do most manufacturers. You can google the manufacturer directly. Most BIOS updates are under "Support"  "downloads" or "drivers" depending on the manufacturer/site.

You've simply been redirected to a third-party's advertisement in your travels.

This x 9000.

It happens all the time.

---

### Post by Bandit on 2012-05-25
BIOS updates are provided by the motherboard manufacturers. I have never seen them ever charge a red penny. Its all part of their customer service you get when you purchase the board.

Now if you are getting misdirected to another site from within the motherboards manufacturers main website. That could be likely caused by sypware or DNS spoofing on Windows. 

Never download Drivers or BIOS updates from any site other then the manufacturers website. You run the risk of viruses, spyware, trojans or even identity theft.

---

### Post by yeehi on 2012-05-31
I didn't go to third party organizations. The only websites I visited were:

1) The manufacturers - Clevo They didn't have the BIOS and didn't send it to me by e-mail when I asked.

2) The Vendors - Novatech They supplied me a BIOS update by e-mail. They said that they don't give out the BIOS freely and I needed to supply a reason for the need. (I got an error message during installation of Ubuntu 12.04.)

3) The BIOS company - Phoenix They wanted money for supplying BIOS files.

The BIOS I received from Novatech were, according to Novatech, the latest. I did get a small revision from 1.02.23 to 1.02.27. However, using the Phoenix BiosAgent tool I could see that there was a more recent revision to the BIOS.

So, how do you feel about having an out of date BIOS on your laptop? I hear that it shouldn't really matter, but it irks me.

---

### Post by CharlesA on 2012-05-31
Perhaps if you post what error you are getting during install you can get past it.

What make/model of laptop are you using?

---

### Post by yeehi on 2012-05-31
Thank you for your interest.

My laptop is a Clevo W76TUN.
It is sold by Novatech. The Novatech stock number is nnb-801

I tried a new installation of Ubuntu 12.04 with the "latest" BIOS that I was given by Novatech. I got the same error message. I tried to write it down while it was still on the screen:

```
Piix4=Smbus 7.0 SmBus base address uninitialised. Update BIOS
```

Something like that.

Despite the error, the installation went ahead OK. It is not nice to get an error message during installation though.

I would deeply love to get the latest BIOS from Phoenix, just to satisfy the itch, but there is no way I am paying $30.00 for it.

---

### Post by CharlesA on 2012-05-31
If it installs fine, run with it.

I've run into a similar message on a couple virtual machines and the install has always completed ok.

---

### Post by HalfNote5 on 2012-05-31
First off, check this out. It might fix that for you without you having to update your BIOS:

[http://finster.co.uk/2010/11/16/virtualbox-piix4_smbus-error/](http://finster.co.uk/2010/11/16/virtualbox-piix4_smbus-error/)

Secondly, looking at Clevo/Novatech, it looks like Novatech should be the one to supply you with the BIOS, with Clevo as a backup source; not phoenix directly.  A lot of motherboard manufacturers USE phoenix bioses, but they can customize them for their particular systems, and thus, you probably wouldn't want it directly from phoenix anyway (although a stock BIOS wouldn't hurt anything, you might lose special tweaks/pre-programmed settings particular to that unit).

It's a bummer that Novatech is being such a pain about it, but really the good news is it looks like your BIOS probably isn't the problem after all. :)

---

### Post by yeehi on 2012-05-31
I typed:

```
 lsmod | grep i2c_piix4
```

in a terminal.
I didn't get any response. It just gave me the prompt again.
What does that mean?

Also, isn't it too late to do these things? I have to do them _after_ Ubuntu is installed, but the error happens during installation...

---

### Post by CharlesA on 2012-05-31
It just means that kernel module isn't loaded. If Ubuntu installs ok, don't worry about it.

---

### Post by yeehi on 2012-05-31
Thank you HalfNote5!

It is nice to know that though the BIOS from Phoenix is not the latest, perhaps I have the latest BIOS tweaked for my particular laptop. That makes me relax a little.

The link you posted was interesting. Thanks again!

---

