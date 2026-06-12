---
title: "Jack latency - ubuntu realtime, ubuntu low latency, arch i686"
date: 2011-04-25
forum: Ubuntu Studio
---

### Post by dawidmt on 2011-04-25
I need low latency audio on linux. I tried ubuntu studio with realtime kernel and ubuntu with linux-lowlatency kernel (from here [https://launchpad.net/~abogani/+archive/ppa]("https://launchpad.net/%7Eabogani/+archive/ppa")). Set jack to realtime and jack started properly. Results are worse than on my i686 arch linux without realtime (BFS kernel, if it's matters). I set jack to 44100hz and 128 frames/peroid and select realtime and soft mode (on arch - realtime deselected). On both ubuntu i get much xruns (approx 1 err/10s), that makes recording impossible. On arch xruns occurs very rarely. Am I doing sth wrong with ubuntu or BFS (or sth else) on my arch does matter?

---

### Post by trulan on 2011-04-26
My first guess would be that your CPU frequency scaling is set up differently in Arch, and that Ubuntu has the cpu set to ondemand, effectively slowing down your system.  It's best to set the CPU governor to performance if you want to use low latency.

In the brief testing that I've done with it, BFS showed no benefit for low latency audio.  It theoretically could help, but it didn't seem to here.

---

### Post by raboofje on 2011-04-26
There's various configuration parameters that might influence JACK performance and xruns.

To look at a few and get some recommendations, I once wrote a small script you can get from [http://code.google.com/p/realtimeconfigquickscan/](http://code.google.com/p/realtimeconfigquickscan/) . Indeed, the CPU governor is an interesting candidate.

---

### Post by dawidmt on 2011-04-28
> **raboofje said:**
> There's various configuration parameters that might influence JACK performance and xruns.

To look at a few and get some recommendations, I once wrote a small script you can get from [http://code.google.com/p/realtimeconfigquickscan/](http://code.google.com/p/realtimeconfigquickscan/) . Indeed, the CPU governor is an interesting candidate.

Thank you for the script. It was very useful for me :)

---

