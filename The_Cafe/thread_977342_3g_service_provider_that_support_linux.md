---
title: "3g service provider that support linux"
date: 2008-11-10
forum: The Cafe
---

### Post by derrek.cooper on 2008-11-10
morning folks.. I live on the east coast in the US. Looking to purchase a 3G USB card that supports Linux? 

Anyone have a recommendation? 

Not sure this is even possible?

cheers.
derrek

---

### Post by Nevon on 2008-11-10
I live in Sweden, so I'm not sure what's available where you are. But generally the Huawei E220 is pretty much guaranteed to work. I have a Huawei E180, and that also works out of the box.

---

### Post by derrek.cooper on 2008-11-10
it works out of the box with ubuntu? who is the provider in sweden?

---

### Post by WorldTripping on 2008-11-10
I'm currently using a Huawei E620 USB Modem on my Intrepid laptop.

The new network manager in 8.10 picks up the modem while booting and is good to go by the time the desktop has loaded (I know this as I have conky scripts to collect mail etc.)

When I was using it on 8.04 I had to install the software provided to get the USB working, but I have not needed to since upgrading to 8.10

In the UK, my provider is Vodaphone, so I got the USB for free on an 18 month contract.

Sorry, dont know any Swedish providors.

---

### Post by mips on 2008-11-10
> **derrek.cooper said:**
> it works out of the box with ubuntu? who is the provider in sweden?

Provider is not really an issue in most cases. At most you need to know the APN, DNS settings etc

---

### Post by Nevon on 2008-11-10
> **derrek.cooper said:**
> it works out of the box with ubuntu? who is the provider in sweden?

There are several providers, but it doesn't really matter what provider you go with as long as you know the number to dial, the APN, the username and the password. Those things you should be able to get from the tech support.

---

### Post by derrek.cooper on 2008-11-10
i am confused? in the states if you "sign up" for a 3g account with a provider, they have their own cards that they support. So, if I were to purchase a USB card for my ubuntu box, it may or may not be supported by the provider.

perhaps I am wrong?

---

### Post by mips on 2008-11-10
> **derrek.cooper said:**
> i am confused? in the states if you "sign up" for a 3g account with a provider, they have their own cards that they support. So, if I were to purchase a USB card for my ubuntu box, it may or may not be supported by the provider.

perhaps I am wrong?

If the cards use the same 'language"/protocol/spec then it should work with the provider. You guys have a weird cell provider setup in the USA where everything is locked in and branded.

Which provider would you prefer using?

---

### Post by Nevon on 2008-11-10
> **derrek.cooper said:**
> i am confused? in the states if you "sign up" for a 3g account with a provider, they have their own cards that they support. So, if I were to purchase a USB card for my ubuntu box, it may or may not be supported by the provider.

perhaps I am wrong?

It shouldn't really matter what USB model you're using, as long as you can put your SIM card in it. For example, if you were to sign up with Three you would typically get a usb modem, a sim card and a CD with the windows drivers. I think that network manager lacks support for unlocking your sim card using the pin code you get from your provider, so you might have to stick your sim card in a 3G phone and remove the pin code. Anyway, efter having done that, you would just stick the sim card in the modem and then plug it in to your computer. Then as you boot up ubuntu, you should get a prompt saying: "Hey, we see you've plugged in a 3G modem. Would you like to go through a wizard that will set it all up for you?" 

That wizard already has the configuration for a lot of providers all set up for you, so most likely that's all you have to do.

---

