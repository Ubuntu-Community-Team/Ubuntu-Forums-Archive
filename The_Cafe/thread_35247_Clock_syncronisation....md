---
title: "Clock syncronisation..."
date: 2005-05-18
forum: The Cafe
---

### Post by renedox on 2005-05-18
I have turned off the clock syncronisation thing but still, everytime ubuntu starts up, it tries to syncronise the clock. I am on dial up so, it takes ages for it to time out.

May I ask why this feature is turned on by default? I find it really annoying :S

Is there anyway I can turn this feature off and have it stay off?

---

### Post by lao_V on 2005-05-18
How did you go about disabling this before?

You can skip a boot-up service temporarily by pressing Ctrl-C or to remove it permanently type  ```
sudo chmod -x /etc/init.d/ntpdate
```

---

### Post by jdong on 2005-05-18
Should be common sense, but if you want to re-enable it, replace "-x" with "+x" ;-)

---

### Post by nocturn on 2005-05-18
or

install rcconf (sudo aptitude install rcconf)

And disable/enable it from there.

---

### Post by SNo0py on 2005-05-18
[QUOTE=lao_V]How did you go about disabling this before?

You can skip a boot-up service temporarily by pressing Ctrl-C or to remove it permanently type  ```
sudo chmod -x /etc/init.d/ntpdate
```[/QUOTE]
Why not removing all rc-links in the rc-levels? Isn't that the nicer solution?

---

### Post by nocturn on 2005-05-18
That's what rcconf does...

---

### Post by lao_V on 2005-05-18
[QUOTE=SNo0py]Why not removing all rc-links in the rc-levels? Isn't that the nicer solution?[/QUOTE]

I haven't used rcconf so not sure how it works. Usually with linux, there's more then one way of doing things. Changing the permission obviously doesn't delete the link which is handy when you want to enable that service again.

---

### Post by tread on 2005-05-18
There is also Ubuntu Bootup Manager which can be found under 3rd party projects on this same forum.

---

### Post by renedox on 2005-05-18
[QUOTE=tread]There is also Ubuntu Bootup Manager which can be found under 3rd party projects on this same forum.[/QUOTE]
 Thanks for the help.

A friend actually setup my ubuntu and turned off the clock syncronisation for me, I don't know how he did it. When I told him that it has come back, he didn't know what to do because he uses gentoo...

---

### Post by jdong on 2005-05-18
Try the Ubuntu Bootup Manager mentioned, or any of the other methods mentioned here. They all work.


More proof that just because he went through Gentoo install hell doesn't mean he's an automatic Linux guru ;)

---

