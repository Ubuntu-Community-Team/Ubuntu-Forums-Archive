---
title: "[SOLVED] Kernel Recompiling - any real advantages?"
date: 2007-08-22
forum: Server Platforms
---

### Post by southernman on 2007-08-22
I am genuinely curious if there are any real advantages to recompiling the stock server kernels. Are there any?

The machine this would be done for is a Dell Dimension v350 - 192MB RAM - PII 350

I built a custom kernel on my desktop, which is much more modern than the Dell, and didn't really notice any speed difference.

signed - dangerously curious!

---

### Post by Tyl3r on 2007-08-22
Depends on the way you configured it, with the time you'll do it always better.
There are some advantages, not huge, but there are :)

---

### Post by southernman on 2007-08-22
Thanks Tyler... I'll give it a shot and see if there is a noticeable difference.

---

### Post by cookfromfrozen on 2007-08-23
if you are running a desktop then i don't recommend rolling your own kernel at all.  if anything you may see a decrease in performance since the stock ubuntu kernel has (or at least did have) the -ck performance patches which aren't in the vanilla kernel from kernel.org

it will almost certainly break binary blobs like the ati drivers.  you'd need to compile those yourself.  

if you want a fully supported system you cannot use your own kernel.

for servers, though, that typicxally don't need binary drivers or X servers, there are advantages to compiling your own kernel.  you can apply security patches like grsecurity, and you can reduce your attack surface by removing modules and features you don't need.  if your server offers remote shells, you can also keep the kernel up to the very latest, patching all those little local DoS vulnerabilities that there seem to be so many of

---

