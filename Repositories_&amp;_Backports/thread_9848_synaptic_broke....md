---
title: "synaptic broke..."
date: 2005-01-02
forum: Repositories &amp; Backports
---

### Post by maxim_86ualb2 on 2005-01-02
after upgrading Gaim.. last night.... Ifound out that today synaptic doesnt work...could it be that gaim downloaded some newer libs that took over some libs that synaptic used.... every time I try to download something it just exits...so what I am doing now it using apt-get to update apt & synaptic.... I hope this will fix it.... since I am somewhat new to linux... 

So guys if you know that this wont help can you tell me ... coz the update is 40megs... and I am on a 64K @ this time..... I have 1M after 12tho....

---

### Post by Rancoras on 2005-01-02
Are you using warty or hoary?  Was the update to Gaim a security update?  more information would be helpful.

---

### Post by Sensebend on 2005-01-03
Could you post what the error message synaptic gives you, the easiest way todo this would be to start synaptic from a gnome terminal, and run the command sudo synaptic. As always the more information you can provide the better.

---

### Post by maxim_86ualb2 on 2005-01-03
it was from warty to hoary, well now most of gnome is gone to I am kinda only geting 1/2 an X but well got almost everything workiing ... still have to reinstall gnome :) 

well I just put in 

apt-get install gaim

that was it.... I am not a linux Pro.... I can make it with a couple of tutorials here & ther.... 

well I dono what update that was...the only thing I know is that it was hoary

---

### Post by Rancoras on 2005-01-03
Yet more proof that mixing warty and hoary packages is a bad idea.  The two branches have diverged too much.  Unless you know every package that was upgraded or installed in that process, it's going to be difficult to undo the damage without a reinstall.  The backports project probably would have been the better option to get the latest Gaim.

---

### Post by maxim_86ualb2 on 2005-01-03
now I know...but I am updating everything..... but peace by peace.... 320megs it a bit to mush for one hit... well I think I will finish in 2 days.... gnome is almost done....

---

### Post by Sensebend on 2005-01-03
Don't mix hoary and warty packages if you can avoid it . Try to run just warty, warty + backports or hoary.

---

### Post by maxim_86ualb2 on 2005-01-03
will upgrading the system fix this ????

---

### Post by Rancoras on 2005-01-03
If you mean upgrading completely to hoary, it might, no guarantees.

---

### Post by maxim_86ualb2 on 2005-01-03
[QUOTE=Rancoras]If you mean upgrading completely to hoary, it might, no guarantees.[/QUOTE]
 I hope it will work....  or I would resort to removing everything expet the core via synaptic & starting something like LFS...

---

