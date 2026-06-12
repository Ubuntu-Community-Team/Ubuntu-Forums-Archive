---
title: "lighdm/unity greeter gets replaced with gdm on upgrade"
date: 2014-02-09
forum: Ubuntu Development Version
---

### Post by ventrical on 2014-02-09
Just updated/upgrade an install that originally had unity greeter /lightdm. Now it has gdm.

 Thats all folks :)

 regards..

Oh joy .. oh rapture ?? :)lol  are we to actually get some breakage after the long polar vortex ? :) lol

---

### Post by Hazzabin on 2014-02-10
I'm sure the polar vortex has affected all the devs brains :p  ):P

---

### Post by ventrical on 2014-02-10
> **Hazzabin said:**
> I'm sure the polar vortex has affected all the devs brains :p  ):P


lol... makes me think of that character .. Mr. Freeze .. from the batman sequels  :) lol

---

### Post by rrnbtter on 2014-02-10
Greetings,
I saw the GDM when it came in on the update, but how would one know that it is being used. 

 pstree -s $(pidof X)
init&#9472;&#9472;&#9472;lightdm&#9472;&#9472;&#9472;Xorg

No question there were greeter problems, but I'm not seeing a difference and my greeter has been working ok for a few days prior to the current update.

---

### Post by ventrical on 2014-02-10
> **rrnbtter said:**
> Greetings,
I saw the GDM when it came in on the update, but how would one know that it is being used. 

 pstree -s $(pidof X)
init&#9472;&#9472;&#9472;lightdm&#9472;&#9472;&#9472;Xorg

No question there were greeter problems, but I'm not seeing a difference and my greeter has been working ok for a few days prior to the current update.

Thanks for the reply. There are a lot of changes going on with mir compositor and xorg and so these things are par for the course.  I think it is something specific to this machine that is a problem that I did not fix a while back. So I am about to try and fix that now .

Regards..

---

