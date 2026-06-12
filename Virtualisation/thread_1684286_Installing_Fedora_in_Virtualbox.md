---
title: "Installing Fedora in Virtualbox"
date: 2011-02-08
forum: Virtualisation
---

### Post by zhogan85 on 2011-02-08
I have been trying to install Fedora in virtualbox, just to play around with another distribution, but I keep running into the same problem. I create the Fedora machine, and then I make it so the machine boots from the Fedora .iso. But thats where I am stuck. A blue screen comes up with a Fedora logo and it says automatic boot in [ ] seconds. Once it boots however, I get three errors.

2.4869991 ERROR: Unable to locate IOAPIC GSI 1
2.4909991 ERROR: Unable to locate IOAPIC GSI 12
2.4929991 ERROR: Unable to locate IOAPIC GSI 7

(The numbers at the beginning I think changed each time)

It then appears to be loading, with a bar across the bottom of the screen but once the bar finishes loading, nothing happens.

I am completely stuck and would appreciate any help you can offer.

---

### Post by zhogan85 on 2011-02-08
Sorry, I forgot to say that I am running Ubuntu Netbook 10.10 and am trying to install Fedora 14. Let me know if I left out any other crucial information.

---

### Post by zhogan85 on 2011-02-12
I solved the problem. I think it was a mistake on my part, I didn't assign the VM enough RAM. Those errors apparently were not causing the problem.

---

