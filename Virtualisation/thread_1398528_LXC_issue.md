---
title: "LXC issue"
date: 2010-02-04
forum: Virtualisation
---

### Post by stlsaint on 2010-02-04
So i read the big thread here...[http://ubuntuforums.org/showthread.php?t=1382823](http://ubuntuforums.org/showthread.php?t=1382823)
and i have been silently following lxc in the shadows, so today i attempted to install on karmic server setup using this guide:[http://www.stgraber.org/category/lxc](http://www.stgraber.org/category/lxc)
as you can see it is very small and doesnt go nearly in depth of what most other lxc guides do but i was looking for a quick test run and i thought this would suite fine. All runs fine until i try and enter the container and i get this: 
```
stlsaint@otherserver:/var/lib/lxc/ubuntu$ lxc-console -n ubuntu
lxc-console: failed to connect to the tty service
```
Again i havent put a boat load of effort into lxc just yet as i am still using proxmox for production server but i was wondering if this issue was a simple one or not?

---

### Post by bodhi.zazen on 2010-02-04
I have lxc working in Ubuntu and am working on documenting what I have done.

You can start with this:

[http://blog.bodhizazen.net/linux/lxc-linux-containers/](http://blog.bodhizazen.net/linux/lxc-linux-containers/)

I have a post in both Ubuntu and Fedora containers , about 75 % done , should be able to post them in the next day or so.

Then add to the Ubuntu wiki and bug reports.

---

### Post by stlsaint on 2010-02-05
Alright well i did as your post said and i think i have everything up and running after a few road blocks on the networking side. So i ran lxc-create...etc etc and it create my hostname dir in my /lxc but when i run the console command i get the same error message i had in my original post.

---

### Post by bodhi.zazen on 2010-02-05
OK, assuming your host is up, try this now =)

[http://blog.bodhizazen.net/linux/lxc-configure-ubuntu-lucid-containers/](http://blog.bodhizazen.net/linux/lxc-configure-ubuntu-lucid-containers/)

---

