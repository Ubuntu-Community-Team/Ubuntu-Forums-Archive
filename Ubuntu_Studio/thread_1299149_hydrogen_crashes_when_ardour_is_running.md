---
title: "hydrogen crashes when ardour is running"
date: 2009-10-23
forum: Ubuntu Studio
---

### Post by junglejuice on 2009-10-23
does any body else have this problem?
i start ardour it's running fine (on ubuntu studio 9.04). load a track (what ever track does not make a difference) then try to start hydrogen and it just won't start. i get this error from hydrogen
```
cannot deliver port registration request
Segmentation fault
```
could some one please point me in the right direction?

---

### Post by AutoStatic on 2009-10-24
Are you using JACK? And what kind of soundcard? Did it work with previous Ubuntu versions?

---

### Post by junglejuice on 2009-10-24
hi autostatic
yes i am using jack and i have a sound blaster audigy. i can't remember having this problem with other versions of ubuntu. 
i discovered that if i start jack, then ardour, then start hydrogen with it using alsa. once everything is running then switching hydrogen to use jack. that seems finicky but it works. i need ardour and hydrogen to use jack transport cause they need to play bak in sync. do you perhaps know of an easier way to do this? because it means switching hydrogen back and fourth between different sound devices something i'd rather not have to do.
thanks for the reply
jj

---

### Post by junglejuice on 2009-10-24
[COLOR="Blue"]SORRY ignore this post its a repeat of previous post[/COLOR]
hi autostatic
yes i am using jack and i have a sound blaster audigy. i can't remember having this problem with other versions of ubuntu. 
i discovered that if i start jack, then ardour, then start hydrogen with it using alsa. once everything is running then switching hydrogen to use jack. that seems finicky but it works. i need ardour and hydrogen to use jack transport cause they need to play bak in sync. do you perhaps know of an easier way to do this? because it means switching hydrogen back and fourth between different sound devices something i'd rather not have to do.
thanks for the reply
jj

---

### Post by sgx on 2009-10-25
> **junglejuice said:**
> hi autostatic
yes i am using jack and i have a sound blaster audigy. i can't remember having this problem with other versions of ubuntu. 
i discovered that if i start jack, then ardour, then start hydrogen with it using alsa. once everything is running then switching hydrogen to use jack. that seems finicky but it works. i need ardour and hydrogen to use jack transport cause they need to play bak in sync. do you perhaps know of an easier way to do this? because it means switching hydrogen back and fourth between different sound devices something i'd rather not have to do.
thanks for the reply
jj
Did you try setting up a lash session, and saving it once everything is connected? Thats the purpose of lash if I recall, to ease the sometimes tedious connections process. lash and liblash should be in the repositories. I think you'll need a small read, to get it going

here is the page

[http://savannah.nongnu.org/projects/lash](http://savannah.nongnu.org/projects/lash)

Cheers

---

### Post by junglejuice on 2009-10-25
awesome thanks sgx! will give it a read :) that's the best thing about these forums, all the new stuff that i've learned from them. you rock!

---

