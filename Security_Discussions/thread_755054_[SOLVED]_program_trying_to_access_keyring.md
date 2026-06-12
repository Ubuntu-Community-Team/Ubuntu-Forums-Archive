---
title: "[SOLVED] program trying to access keyring"
date: 2008-04-14
forum: Security Discussions
---

### Post by tjwoosta on 2008-04-14
i dont really know whats going on, but i just restarted my computer and something strange happened that ive never seen before.

when my computer starts up i have to manually start wlan0 because i had to find a hacked up driver for my reatlek rtl8187b wireless card

so today after i did ./wlan0up  i got a message saying that /usr/bin/nm-applet is trying to access my keyring manager 
(since ive never heard of this before today, i clicked deny)

after clicking deny i notice that everything is still working fine, so i have no clue what it was that was trying to access my keyring

also when i go to keyring manager   i get this message
> 
Allow Application access to keyring?
The application 'Keyring Manager' (/usr/bin/gnome-keyring-manager) wants to access the password for 'Passphrase for wireless network 07FX08114063' in the default keyring

i clicked deny agian

that is my wireless network that its trying to get the password for but ive never used the keyring befor and my computer has always rememberd  the password for my network before without doing what its asking

so basically my question is, why am i now getting a message when i start up asking ot access the keyring when i never use the keyring and obviously my computer connects to everything fine without me saying allow?

could this actaully be a security threat or is this just some simple thing that im paranoid about?

---

### Post by The Tronyx on 2008-04-15
For the sake of brevity I will spare you the details but I do not believe this is a significant threat, if any at all.

/usr/bin/nm-applet is the network manager appled which helps you find and select which wireless networks you want to connect to are.  

I absolutely know what you mean about a hacked up driver though.  My Toshiba has that same card and I actually just ended up buying another wireless card for use with it since I had so much trouble with the card.  Sorry, I am getting off topic.

I will say one thing that I hope will assuage your concerns.  Whenever you are using a modified driver for something like wireless, do not expect it to do 'normal,' or 'planned' things.  I do not think you have anything to worry about though I must admit I am not familiar with the intricacies of the keyring manager.  I hope that in the event that I am mistaken and this does turn out to be a significant issue that someone can help clear it up for you/us.

---

### Post by tjwoosta on 2008-04-16
thanks, it must be something to do with my wireless card  then (i hope)

its just strange how it just started happening now

---

### Post by The Tronyx on 2008-04-16
> **tjwoosta said:**
> thanks, it must be something to do with my wireless card  then (i hope)

its just strange how it just started happening now

No problem, sorry I couldn't give a more authoritative answer though.  I had tried to use that same driver previously but only for around a day.  It was a little shaky so I just grabbed a new card.

Keep me/us posted if you have other questions and good luck with the wireless!:)

---

