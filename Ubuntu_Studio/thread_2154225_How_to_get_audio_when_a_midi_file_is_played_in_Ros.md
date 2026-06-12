---
title: "How to get audio when a midi file is played in Rosegarden"
date: 2013-06-14
forum: Ubuntu Studio
---

### Post by gdesilva on 2013-06-14
Hi,

Just wondering if someone can shed some light on the tricks needed to get a midi file to play in Rosegarden. I have timidity installed and running as a daemon. Rosegarden can see the four timidity midi ports but when I play a midi file there is no audio. Sometimes after restarting timidity I can get the audio going but even that has not been consistent. I am sure I have missed some setting - did follow the doco on setting up timidity.

Any help is greatly appreciated.


EDIT: After many many hours I have worked out that I can get midi files to play in Rosegarden if I use Qsynth or ZynAddSubFX. The same goes for Virtual Keyboard or any other midi app. They all work with Qsynth and ZynAddSubFX but none of them work with Timidity. So it looks like it is to do with Timidity itself.

---

### Post by gdesilva on 2013-06-18
OK here is the solution.

1. start Qjackctl which is the front end to jackd daemon.
2. In the Qjackctl set up I have set a). server path - jackd b). driver - alsa c). midi driver - seq and using the default audio interfaces.
3. Now start timidity with the following command -> timidity -iAvt -B2,8 -Oj 
    The important option being -Oj (output to jack - the default script is -Os - ie to alsa) 
4. Open any midi app, including Rosegarden.
5. In Qjackctl click connections tab and simply connect Rosegarden (or your midi app) to Timidity

This should enable one to play midi files through Rosegarden or any other midi app.

Hope this helps someone.

---

