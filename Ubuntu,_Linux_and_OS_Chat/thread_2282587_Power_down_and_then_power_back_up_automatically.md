---
title: "Power down and then power back up automatically"
date: 2015-06-15
forum: Ubuntu, Linux and OS Chat
---

### Post by John_Wells on 2015-06-15
Hi.

I have been flitting with Linux for a few years now but would like to get a better understanding of it and what I can get it to do. One project I have in mind is to use it for a remote headless data server. One thing I would like to be able to do is remotely do a power down and restart, so rather than issue a reboot command or a shutdown -r I would like to simulate someone holding the power button till the machine completely powers down and then pressing it again for it to do a cold start effectively. Now I know I can use the sudo shutdown -P to make the system power down but I am stuck at how to make the system automatically power back up as if someone had pressed the power button, and if this could be done after say a 30second delay of the system powering down even better. I suppose i could get a very long stick or ring someone to press the button for me but where is the challenge in that :)

I have done some google searching but I guess I maybe using the wrong search terminology as the results are generally about using the reboot command or 
shutdown -r which is not what I am after.

Thanks in advance

Sorry realised I have put this into the wrong section, mods please move if necessary.

---

### Post by grahammechanical on 2015-06-15
May I suggest that you go to the motherboard user guide and check out the settings in the BIOS/UEFI boot system utility? My BIOS motherboard has a section called APM configuration. There is a setting there called Restore On AC Power Loss. The description says this:

"When set to Power Off, the system goes into an off state after an AC power loss. When set to Power On, the system goes on after an AC power loss. When set to Last State, the system goes into either off or on state, whatever the system state was before that AC power loss."

Regards.

---

### Post by John_Wells on 2015-06-15
Thanks for the reply and useful info I shall go and do some delving.

---

### Post by Old_Grey_Wolf on 2015-06-15
Sense you don't mind doing some google searches, google on the phrase "wake-on-lan". It might be what you are looking for.

---

### Post by zeke2135 on 2015-06-15
This is what I use for a music server I have at home. This may not be what you want, because it only suspends, but maybe you could substitute a different command for pm-suspend. On my server it is executed by powernap when the server is idle. It suspends if it executes between 10pm and 7am, when the server wakes up. It calculates the time delay for waking at 7am for the two cases between 10pm and midnight and after midnight. 
```

h=$(date +%k)
m=$(date +%M)
if [ $h -ge 22 ]; then
    wake=$(( ((24 + 7  - $h) * 60 - $m) * 60 ))
    rtcwake -m no -s $wake
    pm-suspend
elif [ $h -le 6 ]; then
    wake=$(( ((7 - $h) * 60 -$m) * 60 ))
    rtcwake -m no -s $wake
    pm-suspend
fi

```

---

### Post by John_Wells on 2015-06-30
> **zeke2135 said:**
> This is what I use for a music server I have at home. This may not be what you want, because it only suspends, but maybe you could substitute a different command for pm-suspend. On my server it is executed by powernap when the server is idle. It suspends if it executes between 10pm and 7am, when the server wakes up. It calculates the time delay for waking at 7am for the two cases between 10pm and midnight and after midnight. 
```

h=$(date +%k)
m=$(date +%M)
if [ $h -ge 22 ]; then
    wake=$(( ((24 + 7  - $h) * 60 - $m) * 60 ))
    rtcwake -m no -s $wake
    pm-suspend
elif [ $h -le 6 ]; then
    wake=$(( ((7 - $h) * 60 -$m) * 60 ))
    rtcwake -m no -s $wake
    pm-suspend
fi

```
Thanks Zeke will give it a go and see what transpires, though at the moment the best solution seems to be if the Bios supports scheduled boot which makes sense as how can linux start itself if it isn't running :)

---

### Post by zeke2135 on 2015-06-30
Well, if I'm not mistaken I guess you could put a script in /etc/pm/sleep.d that tells it to reboot on resume, but that is starting to seem like a kludge.

---

