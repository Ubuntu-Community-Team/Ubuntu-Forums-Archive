---
title: "Google Calendar on desktop"
date: 2013-01-17
forum: The Cafe
---

### Post by EarnestLearner on 2013-01-17
Hello all!

I am trying to get my Google Calendar to display on my desktop using Conky, however it is only displaying my calendar partially. I am running Ubuntu 12.10 with Xfce 4.10 desktop environment.

Here is my current conkyrc file:

```
alignment top_right
background no
border_width 0
cpu_avg_samples 2
default_color white
default_outline_color white
default_shade_color white
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades no
use_xft yes
xftfont DejaVu Sans Mono:size=12
gap_x 5
gap_y 60
minimum_size 5 5
net_avg_samples 2
double_buffer yes
out_to_console no
out_to_stderr no
extra_newline no
own_window yes
own_window_class Conky
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
stippled_borders 0
update_interval 1.0
uppercase no
use_spacer none
show_graph_scale no
show_graph_range no
text_buffer_size 8096

TEXT
${execi 300 gcalcli --nc --cals=owner calw 4}
```

Note: When I run Conky, I get the following output in my terminal:

```
Conky: desktop window (1200003) is subwindow of root window (dc)
Conky: window type - override
Conky: drawing to created window (0x3e00001)
Conky: drawing to double buffer
Traceback (most recent call last):
  File "/usr/bin/gcalcli", line 1524, in <module>
    BowChickaWowWow()
  File "/usr/bin/gcalcli", line 1469, in BowChickaWowWow
    gcal.CalQuery(args[0], count=int(args[1]))
  File "/usr/bin/gcalcli", line 1011, in CalQuery
    self._GraphEvents(cmd, start, count, eventList)
  File "/usr/bin/gcalcli", line 712, in _GraphEvents
    PrintMsg(CLR_NRM(), line + "\n")
  File "/usr/bin/gcalcli", line 239, in PrintMsg
    sys.stdout.write(unicode(msg, 'UTF-8'))
TypeError: decoding Unicode is not supported
Traceback (most recent call last):
  File "/usr/bin/gcalcli", line 1524, in <module>
    BowChickaWowWow()
  File "/usr/bin/gcalcli", line 1469, in BowChickaWowWow
    gcal.CalQuery(args[0], count=int(args[1]))
  File "/usr/bin/gcalcli", line 1011, in CalQuery
    self._GraphEvents(cmd, start, count, eventList)
  File "/usr/bin/gcalcli", line 712, in _GraphEvents
    PrintMsg(CLR_NRM(), line + "\n")
  File "/usr/bin/gcalcli", line 239, in PrintMsg
    sys.stdout.write(unicode(msg, 'UTF-8'))
TypeError: decoding Unicode is not supported


```

Here is a screenshot of my desktop: [http://imgur.com/Ntiu0](http://imgur.com/Ntiu0)

Much thanks!

---

### Post by EarnestLearner on 2013-01-17
10char

---

### Post by Gremlinzzz on 2013-01-18
:popcorn: I am not interested in conky so wont be much help,but have you tried posting on a conky site like (The monster conky thread) 

[http://crunchbang.org/forums/viewtopic.php?id=16909](http://crunchbang.org/forums/viewtopic.php?id=16909)

They might be better qualified.

---

### Post by Petro Dawg on 2013-01-18
I am interested in Conky, but haven't yet done much with calendars.  Re-post your question [here]("http://ubuntuforums.org/showthread.php?t=281865&page=2148"), and I guarantee someone will answer with a great solution rather quickly.

---

