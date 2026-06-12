---
title: "Chromium freezes after being a left alone after sometime"
date: 2016-06-17
forum: Ubuntu Studio
---

### Post by Responsive on 2016-06-17
If I open Chromium and say go to the shops for a few minutes. Then come back. Chromium then becomes frozen and I have to close it down and open again.

I tried removing and installing it again. 

I googled it and some people have problems with chrome on Ubuntu, but didnt see a solution to this specific problem.

anyone else have problems with chromium in ubuntu studios?

---

### Post by Responsive on 2016-06-19
trying

```
chromium-browser --disable -gpu
```

then this pops up.


```
Created new window in existing browser session.
```
so using chromium in this new window. waiting to see if if it doesn't crash all day.

---

### Post by Responsive on 2016-06-19
so far hasnt crashed.

---

### Post by vasa1 on 2016-06-19
> **Responsive said:**
> ...
I tried removing and installing it again. 
...
Can you try with another profile? It should be in *~/.config/chromium-browser* or something like that. 
First ensure that Chromium is thoroughly closed. ```
pgrep chromium-browser
``` should give no output.
Temporarily rename that folder and see if your problem disappears. If it does, it means there's something about your old profile that was to blame. We can take things further after that.

Another thing you could try without first renaming the folder mentioned above is to disable all extensions you've added. Does the problem go away?

---

### Post by Responsive on 2016-06-21
Renamed "/home/myName/.config/chromium/"

[COLOR=#000000][FONT=Ubuntu Mono][I]pgrep chromium-browser

[/I]Returns no output.

waiting to see if it crashes today.


[/FONT][/COLOR]

---

### Post by Responsive on 2016-06-28
chromium still crashing. any solutions?

---

### Post by Responsive on 2016-07-07
anyone suggest how o fix this? i think its pretty bad that chromium doesnt work on ubuntu.

---

### Post by hathalud on 2016-07-30
I was having this issue too. (My first day on Ubuntu Studio after 5+ years in normal Ubuntu.) I found that by disabling the hardware acceleration in Chrome's Advanced Settings it stopped freezing on me. The article I read blamed it on being an older graphics card, but I've got a brand new AMD R9 380 Fury in my system, so I know that's not the case. At least it works now. :) Hope you get yours fixed too.

---

