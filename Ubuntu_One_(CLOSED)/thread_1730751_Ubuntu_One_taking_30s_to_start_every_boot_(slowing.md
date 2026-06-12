---
title: "Ubuntu One taking 30s to start every boot (slowing everything down))"
date: 2011-04-16
forum: Ubuntu One (CLOSED)
---

### Post by Muster Mark on 2011-04-16
Hello,

Here is my issue, ubuntu one takes like 30s to start all of the sudden (it used to be almost instantaneous on log in).  This is an issue for two reasons:  first is the fact that system performance is drastically compromised while ubuntuone-syncdaemon starts since it is accessing the disk as much as it absolutely can, which means that other programs also take forever to launch; second, when it finally does start, I am prompted to unlock the keyring, which interrupts whatever I am doing in a fairly annoying fashion and prevents the screen from locking properly if the computer is suspended.

While ubuntuone-syncdaemon is taking its merry time to launch, the status of the process is "uninterruptable," and an entire processing core is used at 100% with IOwait, as it is furiously accessing the hard drive.

Is their any way I can get u1 back to original, unobtrusive self?  Could this be indicative of a hard drive issue?

Thanks so much

---

### Post by duanedesign on 2011-04-20
Could you please run the following command in a Terminal and post the output.

```
find ~/.local/share/ubuntuone/syncdaemon/fsm/ -type d -empty | wc -l
```

Sometimes if their are a lot of empty folders this can increase the time it takes for syncdaemon to start. If you find the number returned by this command is close to a thousand or more you can run this command to clear them out.

```
find ~/.local/share/ubuntuone/syncdaemon -depth -type d -empty -delete
```


Their is an issue with the syncdaemon taking a long time to start for users who have lots of files. The version of Ubuntu One in Natty and the nightlies PPA fixes this issue. If you are on Maverick you can upgrade to the nighlies PPA. Just be aware that you can not downgrade once you upgrade.

Here are the steps to upgrade.

```
sudo add-apt-repository ppa:ubuntuone/nightlies 
```

```
sudo apt-get update; sudo apt-get upgrade; sudo apt-get install ubuntuone-control-panel 
```

---

### Post by Muster Mark on 2011-05-03
Thanks for the suggestions, very helpful.  It turned out I had 1043 empty folders, so I ran your command for deleting them.  it was successful, but hasn't resulted in any increase in performance unfortunately.  I wasn't planning on leaving 10.10 any time soon, since It had been quite stable for me, but I guess I will give 11.04 a go.

---

