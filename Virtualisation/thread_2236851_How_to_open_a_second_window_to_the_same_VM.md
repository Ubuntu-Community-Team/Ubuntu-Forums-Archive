---
title: "How to open a second window to the same VM?"
date: 2014-07-29
forum: Virtualisation
---

### Post by bulrush2 on 2014-07-29
I have VirtualBox 4.3.14, running Ubuntu server 14.04 under Windows 7. 

I have multiple VMs on Vbox. How do I open another terminal window to my Ubuntu 14.04 VM? 

I sourced my .dir_colors file and it's taking far too long to quit. And I can't break into it with ^C or any other keys. I would like to use a second window for other things too. Like editing, since I don't have X windows going yet. 

Thank you.

---

### Post by dave131 on 2014-07-29
Can you use putty or something like that and just ssh into it?

---

### Post by bulrush2 on 2014-07-29
> **dave131 said:**
> Can you use putty or something like that and just ssh into it?

No, in this case Ubuntu server is running on the same PC as Windows 7. And VirtualBox controls the creation of all terminal windows AFAIK. 

Even if I could ssh into the Ubuntu server VM, how would I do that? It's not like windows has "localhost" defined as the Ubuntu VM. But I installed Ubuntu server as a true server on another machine, so I'll mark this thread closed.

---

### Post by Tadaen_Sylvermane on 2014-08-02
You can ssh from the host machine. Just set the guest network card to bridged. Then ssh as if it was another physical machine on the network. Easy.

Is how I first played with and learned basic ssh stuff, on a single computer with virtualbox

---

### Post by dave131 on 2014-08-03
> **Tadaen_Sylvermane said:**
> You can ssh from the host machine. Just set the guest network card to bridged. Then ssh as if it was another physical machine on the network. Easy.

Is how I first played with and learned basic ssh stuff, on a single computer with virtualbox

That's exactly what I was *trying* to say - thanks for making it clear for the op!

---

