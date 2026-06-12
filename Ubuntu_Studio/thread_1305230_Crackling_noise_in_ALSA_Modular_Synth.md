---
title: "Crackling noise in ALSA Modular Synth"
date: 2009-10-29
forum: Ubuntu Studio
---

### Post by Vigh on 2009-10-29
Hi ive managed to connect my usb midi keyboard via JACK but i am getting a strong crackling noise on each of the presets in ALSA Modular Synth, how can I fix this?

---

### Post by gareththegeek on 2009-10-30
Are you getting any xRuns from Jack?

---

### Post by Vigh on 2009-10-30
what do you mean by xRuns? Im also having the same issue with Horgand 1.07 so its obviously something to do with my sound installation/setup. How do I properly set up ALSA and use JACK properly. I am getting midi signals to the programs which is fantastic was easy to set up but getting crackling noises.

---

### Post by candyiz4kidz on 2009-10-31
are u using ubuntu studios realtime kernel? in my experience those crackles tend to be latency issues more often then not. if ur using regular ole ubuntu's kernel install the ubuntu studio extras package from the package manager, it will optimize your settings for you. otherwise, some where in the software you're using there is going to be a buffer size or latency setting.

---

### Post by Vigh on 2009-10-31
yes i have installed rt-kernel but unfortunately jack server fails with rt kernel

---

### Post by gareththegeek on 2009-11-02
> what do you mean by xRuns?
If you run Jack using QJackCtl you can open the messages windows to see if any xruns are listed. AFAIK XRuns occurs when jack can't keep up with the speed the audio data is coming to the sound card. Realtime priority helps with this.

[https://help.ubuntu.com/community/UbuntuStudioPreparation]("https://help.ubuntu.com/community/UbuntuStudioPreparation") Explains about xruns.

> jack server fails with rt kernel
In what way does it fail?

---

### Post by Vigh on 2009-11-02
I fixed my rt-kernel issues but im trying to set up wine asio now and I am missing glibc-2.8 so I cant registry the wineasio.dll unfortunately

---

