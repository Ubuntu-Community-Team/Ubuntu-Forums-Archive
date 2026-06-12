---
title: "rFactor on Vbox WinXP  “No DirectX 9.0c video adapters found.”"
date: 2008-10-19
forum: Virtualisation
---

### Post by olhat on 2008-10-19
Rfactor on Vbox WinXP  “No DirectX 9.0c video adapters found.”


I installed my rFactor game to my VirtualBox Windows XP3 without problems but when I try to run the game I do get the following error message:
“Rfactor   Video setup v1.5
Hardware Error

No DirectX 9.0c video adapters found. Contact your video card vendor for updated drivers. Visit the links below for technical support and downloads.”


I have installed this DirectX 9.0c a couple of times and every time I get the message that the installation went fine. I ran dxdiag and it tells me that I DO HAVE DirectX 9.0c. Can I somehow inform rFactor that I have it and it should not try to find nVidia original drivers or should I have no expectation on being able to run it?

---

### Post by olhat on 2008-10-19
Surely an insignificant question but interests me a lot.  If Virtualbox does not handle games well then how about VMWare or CrossOver?

---

### Post by b0b138 on 2008-10-20
vbox does not support 3d graphics. The virtual graphics card in your vm cant do it. 

vmware 6.5 has some support for 3d graphics, though I couldn't get it to work with my card.

---

### Post by Thelasko on 2008-10-20
b0b138 is correct, Vbox doesn't support hardware video rendering.  If you want games, your best bet is Wine.  Just remember, don't install DirectX in Wine, it will break it.

---

