---
title: "Munin reporting incorrectly"
date: 2007-12-21
forum: Server Platforms
---

### Post by mellowd on 2007-12-21
Anyone else having a problem like this with Munin? I'm currently monitoring my server and the S.M.A.R.T values for drive sda plugin is currently showing my hdd temp as 108 celcius. This is definately wrong as if I check the SMART value directly on the server it shows 42 Celcius. Now 42 C = 108 F so at least I know it's attempting to show it in Fahrenheit, but the graph is saying its Celcius. So how do I fix this? I've checked the plugin through Vim and can't seem to see where this value needs to be changed.

---

