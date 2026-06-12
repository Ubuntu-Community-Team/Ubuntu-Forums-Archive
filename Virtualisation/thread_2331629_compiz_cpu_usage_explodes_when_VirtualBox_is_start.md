---
title: "compiz cpu usage explodes when VirtualBox is started"
date: 2016-07-24
forum: Virtualisation
---

### Post by dean.w.schulze on 2016-07-24
Running Ubuntu 15.10 with VirtualBox 5.1.2 and a Win10 guest OS.  When I start VirtualBox (just VB, not the guest OS) compiz cpu usage goes over 150% and stays there for several minutes.  When running the Win10 guest it is typically 160% with short bursts below 40% but then back to over 150%.

It looks like compiz is defective.  I understand compiz is part of Unity.  Do I need to switch desktops to get rid of compiz, or is there a fix for it?

Thanks.

---

### Post by bapoumba on 2016-07-24
*Thread moved to **Virtualisation**.*
Your question may be better suited here.

---

### Post by MAFoElffen on 2016-07-26
I'm a but confused.by your percentages. One hundred percent of one CPU would be complete CPU utilization. How did you figure results of 150%. One and a half CPU's? As you explained this, this is happening on your host right?

Just before you start VirtualBox, open a terminal and do this
```

ps -eo pcpu,pid,user,args | sort -k 1 -r | head -n 5 >> ~/Documents/result.txt

```
Start VirtualBox.. Then while it is running, go back to the terminal and run this again
```

ps -eo pcpu,pid,user,args | sort -k 1 -r | head -n 5 >> ~/Documents/result.txt

```
Then post the contents of the file here, within code tags.

---

### Post by izznogooood on 2016-07-26
Tip:
How many CPU Core's did you allocate to this Virtual machine?
I have "8" Core's but i typically only allocate 1 or 2 (2 if its windows10 and I am working in it). Depending on what i use it for. If I'm testing a new system I might go as high as 4 but this drags my hole system down.
If you allocate halv or more it will significantly slow your machine!
--------------------

And I'm not sure what you mean by Compiz CPU%? Did you use "glances" or something simulere to see Compiz drawing that much power.

(PS: Depending what monitoring system you have 150% might not be bad, as glances will show 100% pr CPU. Meaning I often when converting or other CPU specific jobs have a load of 600%+)

And last but not least, is your system up to date? And is 5.1.2 in the ubuntu repositories?

---

### Post by dean.w.schulze on 2016-07-27
I have 8 cores and I allocate 3 CPUs to the guest OS.  I determine CPU usage from top.  I noticed that compiz stays very high (> 150%) when playing an mp4 video.  I can understand that, but I can't understand why it is so high when I run VirtualBox.

I'll create the log file you suggested above and post it this evening.

---

### Post by dean.w.schulze on 2016-07-28
The results are below, but those commands didn't capture much of anything about compiz.  I ran the second command several times including once when compiz was using 280% CPU, but it didn't add anything to the file about compiz.

```

%CPU   PID USER     COMMAND 5.3  7833 dean     /opt/google/chrome/chrome --type=renderer --force-fieldtrials=*UMA-Population-Restrict/normal/*UMA-Uniformity-Trial-1-Percent/group_18/*UMA-Uniformity-Trial-10-Percent/group_01/*UMA-Uniformity-Trial-100-Percent/group_01/*UMA-Uniformity-Trial-20-Percent/group_02/*UMA-Uniformity-Trial-5-Percent/group_05/*UMA-Uniformity-Trial-50-Percent/group_01/*UMA_CheckStates/NoChecks/ --primordial-pipe-token=27E8A3ED4532D45A02D72392753C656B --lang=en-US --enable-offline-auto-reload --enable-offline-auto-reload-visible-only --enable-pinch --num-raster-threads=4 --content-image-texture-target=3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553 --video-image-texture-target=3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553 --disable-accelerated-video-decode --disable-webrtc-hw-encoding --disable-gpu-compositing --mojo-channel-token=19759DD49EDF9E544524BC23CAD13FA6 --mojo-application-channel-token=E8DB0E073CFE711F6168C79DA484F7A8 --channel=7279.22.161339948 --v8-natives-passed-by-fd --v8-snapshot-passed-by-fd
 2.8  7279 dean     /opt/google/chrome/chrome
 2.1   831 root     /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
11.5  1604 dean     compiz
%CPU   PID USER     COMMAND
85.3 11024 dean     /usr/lib/virtualbox/VirtualBox --comment Win10Guest --startvm cfb9bf58-1908-47ad-a3db-3e6e6d66b1e0 --no-startvm-errormsgbox
 5.3  7833 dean     /opt/google/chrome/chrome --type=renderer --force-fieldtrials=*UMA-Population-Restrict/normal/*UMA-Uniformity-Trial-1-Percent/group_18/*UMA-Uniformity-Trial-10-Percent/group_01/*UMA-Uniformity-Trial-100-Percent/group_01/*UMA-Uniformity-Trial-20-Percent/group_02/*UMA-Uniformity-Trial-5-Percent/group_05/*UMA-Uniformity-Trial-50-Percent/group_01/*UMA_CheckStates/NoChecks/ --primordial-pipe-token=27E8A3ED4532D45A02D72392753C656B --lang=en-US --enable-offline-auto-reload --enable-offline-auto-reload-visible-only --enable-pinch --num-raster-threads=4 --content-image-texture-target=3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553 --video-image-texture-target=3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553 --disable-accelerated-video-decode --disable-webrtc-hw-encoding --disable-gpu-compositing --mojo-channel-token=19759DD49EDF9E544524BC23CAD13FA6 --mojo-application-channel-token=E8DB0E073CFE711F6168C79DA484F7A8 --channel=7279.22.161339948 --v8-natives-passed-by-fd --v8-snapshot-passed-by-fd
 2.8  7279 dean     /opt/google/chrome/chrome
 2.1   831 root     /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
%CPU   PID USER     COMMAND
 5.3  7833 dean     /opt/google/chrome/chrome --type=renderer --force-fieldtrials=*UMA-Population-Restrict/normal/*UMA-Uniformity-Trial-1-Percent/group_18/*UMA-Uniformity-Trial-10-Percent/group_01/*UMA-Uniformity-Trial-100-Percent/group_01/*UMA-Uniformity-Trial-20-Percent/group_02/*UMA-Uniformity-Trial-5-Percent/group_05/*UMA-Uniformity-Trial-50-Percent/group_01/*UMA_CheckStates/NoChecks/ --primordial-pipe-token=27E8A3ED4532D45A02D72392753C656B --lang=en-US --enable-offline-auto-reload --enable-offline-auto-reload-visible-only --enable-pinch --num-raster-threads=4 --content-image-texture-target=3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553 --video-image-texture-target=3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553 --disable-accelerated-video-decode --disable-webrtc-hw-encoding --disable-gpu-compositing --mojo-channel-token=19759DD49EDF9E544524BC23CAD13FA6 --mojo-application-channel-token=E8DB0E073CFE711F6168C79DA484F7A8 --channel=7279.22.161339948 --v8-natives-passed-by-fd --v8-snapshot-passed-by-fd
 2.7  7279 dean     /opt/google/chrome/chrome
 2.1   831 root     /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
 125 11024 dean     /usr/lib/virtualbox/VirtualBox --comment Win10Guest --startvm cfb9bf58-1908-47ad-a3db-3e6e6d66b1e0 --no-startvm-errormsgbox
%CPU   PID USER     COMMAND
89.7 11024 dean     /usr/lib/virtualbox/VirtualBox --comment Win10Guest --startvm cfb9bf58-1908-47ad-a3db-3e6e6d66b1e0 --no-startvm-errormsgbox
 5.3  7833 dean     /opt/google/chrome/chrome --type=renderer --force-fieldtrials=*UMA-Population-Restrict/normal/*UMA-Uniformity-Trial-1-Percent/group_18/*UMA-Uniformity-Trial-10-Percent/group_01/*UMA-Uniformity-Trial-100-Percent/group_01/*UMA-Uniformity-Trial-20-Percent/group_02/*UMA-Uniformity-Trial-5-Percent/group_05/*UMA-Uniformity-Trial-50-Percent/group_01/*UMA_CheckStates/NoChecks/ --primordial-pipe-token=27E8A3ED4532D45A02D72392753C656B --lang=en-US --enable-offline-auto-reload --enable-offline-auto-reload-visible-only --enable-pinch --num-raster-threads=4 --content-image-texture-target=3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553 --video-image-texture-target=3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553 --disable-accelerated-video-decode --disable-webrtc-hw-encoding --disable-gpu-compositing --mojo-channel-token=19759DD49EDF9E544524BC23CAD13FA6 --mojo-application-channel-token=E8DB0E073CFE711F6168C79DA484F7A8 --channel=7279.22.161339948 --v8-natives-passed-by-fd --v8-snapshot-passed-by-fd
 2.7  7279 dean     /opt/google/chrome/chrome
 2.1   831 root     /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
%CPU   PID USER     COMMAND
 5.3  7833 dean     /opt/google/chrome/chrome --type=renderer --force-fieldtrials=*UMA-Population-Restrict/normal/*UMA-Uniformity-Trial-1-Percent/group_18/*UMA-Uniformity-Trial-10-Percent/group_01/*UMA-Uniformity-Trial-100-Percent/group_01/*UMA-Uniformity-Trial-20-Percent/group_02/*UMA-Uniformity-Trial-5-Percent/group_05/*UMA-Uniformity-Trial-50-Percent/group_01/*UMA_CheckStates/NoChecks/ --primordial-pipe-token=27E8A3ED4532D45A02D72392753C656B --lang=en-US --enable-offline-auto-reload --enable-offline-auto-reload-visible-only --enable-pinch --num-raster-threads=4 --content-image-texture-target=3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553 --video-image-texture-target=3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553,3553 --disable-accelerated-video-decode --disable-webrtc-hw-encoding --disable-gpu-compositing --mojo-channel-token=19759DD49EDF9E544524BC23CAD13FA6 --mojo-application-channel-token=E8DB0E073CFE711F6168C79DA484F7A8 --channel=7279.22.161339948 --v8-natives-passed-by-fd --v8-snapshot-passed-by-fd
 4.0 11187 dean     /usr/lib/virtualbox/VirtualBox
 2.7  7279 dean     /opt/google/chrome/chrome
 2.1   831 root     /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch



```

---

### Post by mc4man on 2016-07-28
I'd probably install sysstat, then monitor compiz for a bit & see.
Could go like - 
get the pid
```
ps axu |grep compiz |grep -v grep
```
monitor for x number of reports  x sec apart, below examples  6 reports 10 sec apart, XXXX is pid #
```
pidstat -h -r -u -v -p XXXX 10 6 | tee ~/compiz1.log
```
(- you can set # of reports & time to suit, you can also do multiple pids at once, comma separated, e.g. XXXX,XXXX 
Your terminal needs to be wide for this set of options, man pidstat to see.

---

### Post by MAFoElffen on 2016-07-30
The story I saw from your output was:

Compiz was not taking the biggest slice as you described. Chrome takes up a major slice of your cpu. And while VirtualBox is starting,... %expliitive!!!% <-- I had to say that as censored when I saw how much VirtualBox was using when starting!!!

I see that a surprise. Around 90% CPU to start? It releases after, and Chrom returns as the major resource user, but that seems like a lot of resources to initialize.

---

### Post by benjamin-c-burns on 2017-07-16
> **MAFoElffen said:**
> I'm a but confused.by your percentages. One hundred percent of one CPU would be complete CPU utilization. How did you figure results of 150%. One and a half CPU's? As you explained this, this is happening on your host right?

Just before you start VirtualBox, open a terminal and do this
```

ps -eo pcpu,pid,user,args | sort -k 1 -r | head -n 5 >> ~/Documents/result.txt

```
Start VirtualBox.. Then while it is running, go back to the terminal and run this again
```

ps -eo pcpu,pid,user,args | sort -k 1 -r | head -n 5 >> ~/Documents/result.txt

```
Then post the contents of the file here, within code tags.

I think you wanted

```

ps -eo pcpu,pid,user,args | sort -k 1 -n -r | head -n 5

```

Note the "-n" added to the "sort" command.

Better yet, ditch sort altogether and let ps do the work.

```

ps -eo pcpu,pid,user,args --sort -pcpu | head -n 5

```

---

