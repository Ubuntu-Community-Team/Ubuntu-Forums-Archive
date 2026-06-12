---
title: "Can I make my VMs see each others?"
date: 2009-11-08
forum: Virtualisation
---

### Post by moe19790 on 2009-11-08
hi,

i`m using Sun VM, and i do have about 3 v-machines... i want them to see each others.. how can i do that? i`ve noticed that even when i run them, they are getting the same IP?! how is that?!

thank you

---

### Post by moe19790 on 2009-11-13
Bump

---

### Post by fjgaude on 2009-11-13
What is your host OS, and what are the guest OSs?

---

### Post by cgb on 2009-11-13
This shouldn't be a problem for them to see each other and share folders but the process involved does depend on the OS's used.  You will want to make sure the network adapter is setup as Bridged in the Virtualbox settings.

---

### Post by moe19790 on 2009-11-14
well, i`m doing this as experimental before i do apply it, so what matters here is the concept. 

the host is Ubuntu 9.04 i`m using Sun V-Box 3.06

guests are

1- fedora 11
2- xp
3- mandriva

---

### Post by fjgaude on 2009-11-14
What program created the VMs?

With vmware player 3.0 you can setup shares and each VM will be able to see the shares. I'm sure workstation 7.0 does it too.

With vmware server 1.0.10 you can use Samba and see the files on the host after you make sure you have either NAT or Bridged net connection.

I've never tried to have two or more VMs running under the same host and actually have desktop connection between them. You might play around and see if it is possible.

---

### Post by fjgaude on 2009-11-14
As a matter of curiosity I opened two instincts of VMware Player 3.0, with WinXP and Xbuntu 9.10 playing... and it works... through Samba I was able to see each desktop from the other, through Windows Workgroup. Interesting!

My host is Ubuntu 9.10 64-bit.

Thought you would be happy.

---

### Post by moe19790 on 2009-11-15
this is great, i`ll try to see if it will work with Sun V-Box as well :)

---

### Post by fjgaude on 2009-11-15
Just to let you know that Server doesn't work with 9.10 host. At least it is very difficult to get it to do it. 9.04, 8.10 work fine. Player 3.0 seems to work with all of the Ubuntu versions.

---

