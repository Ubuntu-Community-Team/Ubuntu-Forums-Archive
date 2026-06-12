---
title: "Little tiny suggestion"
date: 2006-04-17
forum: The Cafe
---

### Post by Mr. Picklesworth on 2006-04-17
I don't know where to discuss feature suggestions, so I'm doing it here.

In the network setup application, I notice that the WEP key field is a password field.
This is nearly unbearable for 128-bit keys, and I find myself having to copy and paste them from a text file so that I know I am typing the right thing.

Now, I realize that there is a threat that some prying eyes could peer over my shoulders and memorize all 25 characters so they can break into my network... but then those same greedy (and nearby) eyes could also easily find my WEP key stored in a completely unprotected file at /etc/network/interfaces.


Of course, there's still lots of people with ASCII WEP keys or small WEP keys, so perhaps a good middle ground would be a "password field" check box so whiners like myself would be able to happily pound out WEP keys while reading them, and smart people could type them while feeling completely safe from that scary neighbour with a telescope.

Anyway, just an idea.
What do you think? Should fields for ginormous passwords that are rarely entered and easily figured out be unreadable?

---

### Post by localzuk on 2006-04-17
Well, your suggestion is the same way Kgpg and various other GPG front ends handle it. I think it is a good idea. Why not suggest it on launchpad.net?

---

### Post by towsonu2003 on 2006-04-17
[QUOTE=localzuk]launchpad.net[/QUOTE]
file as if it's a bug, than change its priority to "wishlist"

[quote=Mr. Picklesworth]
my WEP key stored in a completely unprotected file at /etc/network/interfaces[/quote]
isn't that a security vulnerability/bug?

---

### Post by xXx 0wn3d xXx on 2006-04-17
[QUOTE=towsonu2003]file as if it's a bug, than change its priority to "wishlist"


isn't that a security vulnerability/bug?[/QUOTE]
I can also confirm that my wep key is completly visable on breezy under /etc/network/interfaces. I don't consider it a major security vulnerability but it is a vulnerability.

---

### Post by Iandefor on 2006-04-17
I like it. Go for it!

---

### Post by towsonu2003 on 2006-04-18
[QUOTE=MasterChief1234]I can also confirm that my wep key is completly visable on breezy under /etc/network/interfaces. I don't consider it a major security vulnerability but it is a vulnerability.[/QUOTE]
I'd file a bug, but I don't have wireless (hence a wep key). May be later when I get one... hopefully... wireless.......... arrr....

---

### Post by prizrak on 2006-04-18
Considering how useless WEP keys are, why bother? :) There is no need to encrypt or mask an encryption key as it would only be a vulnerability if someone gets access to your computer at which point it won't matter much if your wireless is compromised :) Good suggestion though, there is no point in masking the key while you are entering it, since chances are you are entering it from somewhere that is plainly visible anyways.

---

### Post by towsonu2003 on 2006-04-18
[QUOTE=prizrak]Considering how useless WEP keys are, why bother? :) [/QUOTE]
point taken :)

---

