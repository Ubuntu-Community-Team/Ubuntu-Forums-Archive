---
title: "Sports conky"
date: 2010-07-17
forum: The Cafe
---

### Post by halflifez on 2010-07-17
How to display mlb standings on conky:

Python script:
[B]#!/usr/bin/env python

import os

filename = "http://scores.espn.go.com/mlb/standings | egrep -A6 'American League'"
cmd = os.popen("lynx -nonumbers -dump %s" % filename)

output = cmd.read()
cmd.close()
print output[/B]

Save as (RANDOM FILE NAME-R1).py

Under TEXT in conky:
[B]${color F8F8FF}MLB ${hr 2}$color
${font freemono:size=8}${execi 30 python ~/.conky/conkyparts/(RANDOM FILE NAME-R1).py}[/B]

Output is shown in diagram attached.

Enjoy ;)

---

