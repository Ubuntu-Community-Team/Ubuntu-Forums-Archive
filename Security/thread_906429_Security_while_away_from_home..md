---
title: "Security while away from home."
date: 2008-08-31
forum: Security
---

### Post by Tylazene on 2008-08-31
What would be a good way to stay secure online while away from home? Away from home meaning at a relatives house using their (windows) PC. I need to pay bills and other financial transactions online while on vacation but have no laptop. I was thinking of using a bare bones Ubuntu or Puppy live cd and boot from that. I would only be online about 5 to 10 minutes then hop off. 

Am I safe from being hacked or getting a key logger? Maybe I'm paranoid but I was thinking of even unplugging the hard drive and then boot to the CD. Is this feasible?

---

### Post by Rhubarb on 2008-08-31
Using the Ubuntu live CD should help, even better would be to install ubuntu onto a large usb drive, make sure it's up-to-date.

Using the live CD / usb drive will stop software key loggers (disconnecting the hard drive is unnecessary), but it won't stop hardware key loggers.

Unless you don't trust your relatives / relative's computer technician / the relative's computer hardware-wise, there shouldn't be much to worry about.

If need be, you can follow the keyboard cable to the back of the computer, if there's an in-line connector you should be safe.

If you want even more security, you could "ssh -X" from the live cd to your home, and open up firefox through the sshed line.

---

### Post by aysiu on 2008-08-31
I don't see how the hard drive is relevant. Honestly, most of the security in those instances has to do with how well your bank and credit card companies set up their websites.

---

### Post by Tylazene on 2008-08-31
I'm not worried about hardware keyloggers but any software that might be on my sisters PC. God knows what viruses/spyware she might have. 

I was thinking that using a read only CD would prevent any infection. Only if something got into the ram over the internet could cause a problem. But then it would only be for that session. Am I right?

---

### Post by rogeriopvl on 2008-08-31
> **Tylazene said:**
> I'm not worried about hardware keyloggers but any software that might be on my sisters PC. God knows what viruses/spyware she might have. 

I was thinking that using a read only CD would prevent any infection. Only if something got into the ram over the internet could cause a problem. But then it would only be for that session. Am I right?

Yes. Although I really doubt that "something gets into the ram over the internet" using Ubuntu, unless you install every thing that you see on the web.

---

### Post by Tylazene on 2008-08-31
Great! Thanks guys. Just another reason Ubuntu (and this forum) is so cool.

---

### Post by lovinglinux on 2008-08-31
Take a look at [Moka5]("http://www.mokafive.com/") service. Maybe that suit your needs.

---

