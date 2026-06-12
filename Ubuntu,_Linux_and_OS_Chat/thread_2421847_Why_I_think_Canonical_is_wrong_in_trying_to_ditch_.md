---
title: "Why I think Canonical is wrong in trying to ditch 32-bit app support"
date: 2019-06-27
forum: Ubuntu, Linux and OS Chat
---

### Post by ardouronerous on 2019-06-27
I understand why Canonical is ditching support for 32-bit PCs and laptops, since almost all PCs and laptops sold today are 64-bit, my 32-bit PC just bit the dust and I got myself a 64-bit used laptop, so I understand Canonical's reasoning for that one.

However, ditching support for 32-bit applications was and is a big mistake, there are hardware drivers that are 32-bit, like my Canon PIXMA iP2700 printer, which I bought in 2015, the Linux driver provided by Canon is 32-bit and in order to install and run my printer, I had to enable 32-bit support in Lubuntu 64-bit by running these commands in the Terminal:

```
sudo dpkg --add-architecture i386
sudo apt-get update
```

Besides from hardware drivers, 32-bit app support is crucial for emulation software like WINE, which needs 32-bit libraries to run old software, like my old SAPI5 TTS voice and screen reader software, both of which are 32-bit, and for old Windows games, and speaking of game support, Valve's Steam requires these 32-bit libraries to run their games, especially 32-bit games that were purchased by the user, Canonical would be alienating a lot of these users.

For a case scenario, I once read a story about a Linux user that was  diagnosed with throat cancer and part of his throat had to be removed,  thus losing the ability to speak, his solution was to purchase an IVONA  voice and install it with WINE so he can speak with his laptop, similar  to Stephen Hawkings, the IVONA voice he purchased was 32-bit only.

---

