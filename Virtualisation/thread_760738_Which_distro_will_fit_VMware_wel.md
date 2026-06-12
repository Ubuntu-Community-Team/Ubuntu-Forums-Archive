---
title: "Which distro will fit VMware wel?"
date: 2008-04-20
forum: Virtualisation
---

### Post by Fzang on 2008-04-20
I have a laptop with 2.2 GHz processor and 2 gigs of RAM, running windows vista basic...

Which distro would go well along with VMware? I tried ubuntu but it seems to be a bit laggy and slightly blurry...

I know that some of the "old machine" distros would probably work well, but they just give me an impression of being lin95

Are there any distros specifically designed to run virtually?

---

### Post by kwacka on 2008-04-20
I doubt that there are any designed to run under VMware.

How much memory do you have assigned to virtual machines?

---

### Post by Shazaam on 2008-04-20
What I have found regarding vm (virtual machine) slowdowns is that they are usually caused by allocating too much physical memory to the vm. A good rule of thumb is to allocate no more than half of your physical ram to the vm. Even less if you run multiple vm's at once. When you give a vm too much memory you slow down the host which then slows down the guest. Set up correctly all distro's should run fine as a vm.
The amount of actual physical memory installed is a consideration too.

---

