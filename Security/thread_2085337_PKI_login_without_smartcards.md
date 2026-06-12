---
title: "PKI login without smartcards?"
date: 2012-11-17
forum: Security
---

### Post by algernon83 on 2012-11-17
I use PKI login for SSH on my home and work. I use a DSA key on a USB memory stick. Since I don't have smart card hardware at either location -- and setting this up entails a lot of research that I haven't finished -- I'd like to get my feet wet by setting up PKI log-on for desktop sessions on my home network.

Is this possible in Ubuntu? I realize it's less secure than a proper smart card infrastructure for various reasons, but it seems like a good learning exercise and a step up from passwords.

---

### Post by Bachstelze on 2012-11-20
Since you seem to be able to use USB, you could use a token like [this](http://www.gooze.eu/feitian-epass-pki-token), which is basically a smart-card-and-reader combo in USB form and is indistiguishable to the OS from a "real" smart card.

(Also you might be interested in my [tutorial](http://ubuntuforums.org/showthread.php?t=1557180).)

---

### Post by algernon83 on 2012-11-20
Thank you, Bachstelze. When I'm ready to invest in hardware, I think I would prefer to use a proper smart card; however, your tutorial will be a big help. In fact, I wasn't aware that my country (the USA) has an emerging standard for an ID card; I thought only the Department of Defense used smart cards. So, I'll read a bit more, but a PIV-compatible card sounds like the way to go. Thank you again for your advice.

---

