---
title: "save terminal responce to string in python"
date: 2012-09-27
forum: Ubuntu Application Development
---

### Post by Jordiston on 2012-09-27
im not sure if this is supposed to be simple or really complicated or if its possible (really hope so), 
but i want to be able to send out a command to the terminal from python which i can do like so.

import os

os.system("clear")
os.system("amixer get Master")

when running this in terminal the terminal come's up with this.

Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 87
  Mono: Playback 42 [48%] [-33.75dB] [on]
jordiston@JordistonUbuntu:~$ 

In bash I can easily save this to a string, but is their anyway for python?

---

### Post by spjackson on 2012-09-27
```

import subprocess

output = subprocess.check_output("amixer get Master", shell=True)
print(output)

```

---

### Post by Jordiston on 2012-09-27
THANK YOU!! Worked perfectly.
 I'm using it to make an indicator for alsa sound volume. I deleted pulseaudio and theirs no indicator for  people that only use alsa.

It's working good now. I am still wondering though if theirs any drawback on using this method. like if its slower or bad in anyway and if their'd be a better way to do this Or if its good like this.

It doesn't take a percent off of my cpu and i have a timer that controls how fast it checks.

---

