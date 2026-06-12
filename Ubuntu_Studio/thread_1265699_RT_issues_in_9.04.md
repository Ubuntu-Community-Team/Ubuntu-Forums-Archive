---
title: "RT issues in 9.04"
date: 2009-09-13
forum: Ubuntu Studio
---

### Post by kvk on 2009-09-13
Running 64 bit Ubuntu Studio 9.04
Intel Core 2 Duo E8400 3.0 ghz
Video Card: GeForce 7100/nForce 630i
Audio: Presonus FP10
4 GB Ram
RT kernel: 2.6.28.3.1
Ardour 1:2.7.1

I had JACK/Ardour up and running fine on 8.10 on this same machine, but upgrading to 9.04 has produced issues. I am able to start JACK on the vanilla kernel, although the X-runs begin immediately, of course. But in switching to the RT kernel, JACK immediately terminates itself, or else runs for a few seconds before completely shutting itself off, including closing the qjackctl gui. Once it does so, however, I am unable to start it again without restarting the computer, as it returns an error that the server is already running. 

When starting JACK from the terminal, I use:

```
jackd -R -P89 -p128 -dfirewire -dhw:0 -r44100 -p32 -n2
```

which worked under 8.10.

I have tried removing the memlock setting, or setting it to different values, with no change. 

I had considered:

1. Rolling back to a previous RT kernel, as there seem to be some issues with the current one (I do get the occasional freeze, as mentioned by others);

2. Completely rolling back to 8.10 (a hassle with re-constructing some programs, but not enormously so- all my data are one one drive and the OS/applications on the other);

3. Dual installing 9.04 and 8.10 (which appears problematic, since the partitioner wants to install one or the other, as opposed to making two separate partitions).

4. Rolling forward to the Karmic Koala RT kernel- apparently it is more stable??

I did notice that Stochastic had indicated the necessity of compiling one's own RT kernel under Jaunty- perhaps that is the solution??

Thanks so much!!

---

