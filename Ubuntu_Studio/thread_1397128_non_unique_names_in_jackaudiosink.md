---
title: "non unique names in jackaudiosink"
date: 2010-02-02
forum: Ubuntu Studio
---

### Post by prince.buster on 2010-02-02
Hello you Linux Audio Officianados you ..

I'm having some trouble with the jackaudiosink in gstreamer. I'm writing small python scripts that play multiple files simultaneously and there seems to be problems with the (jack) port name allocation in jackaudiosink. 

I'm unsure whether the problem is due to a bug in the jackaudiosink or my disgustingly hacked multithreading scripts. Would appreciate some feedback on this. If there is a bug I'd be very keen to help iron it out. Does the jackaudiosink have anybody maintaining it?

In particular, I think the problem boils down to this:

```
jez@X31:~$ gst-launch audiotestsrc ! jackaudiosink audiotestsrc ! jackaudiosink
Setting pipeline to PAUSED ...
Pipeline is PREROLLING ...
ERROR: from element /GstPipeline:pipeline0/GstJackAudioSink:jackaudiosink1: Could not get/set settings from/on resource.
Additional debug info:
[B]gstjackaudiosink.c(517): gst_jack_ring_buffer_acquire (): /GstPipeline:pipeline0/GstJackAudioSink:jackaudiosink1:
Cannot allocate more Jack ports[/B]
ERROR: pipeline doesn't want to preroll.
Setting pipeline to NULL ...
Freeing pipeline ...

```

Jackaudiosink seems incapable of instantiating itself twice within the same process ...

If I run the two pipelines separately, it works:

```
jez@X31:~$ gst-launch audiotestsrc ! jackaudiosink &
[1] 19724
jez@X31:~$ Setting pipeline to PAUSED ...
Pipeline is PREROLLING ...
Pipeline is PREROLLED ...
Setting pipeline to PLAYING ...
New clock: GstAudioSinkClock
gst-launch audiotestsrc ! jackaudiosink &
[2] 19729
jez@X31:~$ Setting pipeline to PAUSED ...
Pipeline is PREROLLING ...
Pipeline is PREROLLED ...
Setting pipeline to PLAYING ...
New clock: GstAudioSinkClock
^C

```

The script I am working on is:
```
#!/usr/bin/env python

# randomgst.py
# arguments: a directory containing sound files
# the script plays the sound files in random order

import sys, os, time, thread, gobject, pygst, random
pygst.require("0.10")
import gst

NUM_PLAYERS = 4

class Player:
  
  id = 0
  
  def __init__(self):
    self.player = gst.element_factory_make("playbin", "player")
    fakesink = gst.element_factory_make("fakesink", "fakesink")
    jackaudiosink = gst.element_factory_make("jackaudiosink", "jackaudiosink" + str(Player.id))
    Player.id+=1
    self.player.set_property("video-sink", fakesink)
    self.player.set_property("audio-sink", jackaudiosink)
    bus = self.player.get_bus()
    bus.add_signal_watch()
    bus.connect("message", self.on_message)
    thread.start_new_thread(self.start, ())

  def on_message(self, bus, message):
    t = message.type
    if t == gst.MESSAGE_EOS:
      self.player.set_state(gst.STATE_NULL)
      self.playmode = False
    elif t == gst.MESSAGE_ERROR:
      self.player.set_state(gst.STATE_NULL)
      err, debug = message.parse_error()
      #print "Error: %s" % err, debug
      print "file skipped: " + self.filename
      self.playmode = False

  def get_directory(self, argv):
    if len(argv) == 1:
      directory = "./"
    else:
      directory = argv[1]
    # relative or absolute?
    if directory[0] != '/': #relative
	    directory = os.getcwd() + directory[1:]
    return directory

  def start(self):
    directory = self.get_directory(sys.argv)
    while True:
      filenames = os.listdir(directory)
      random.shuffle(filenames)
      for self.filename in filenames:
	filepath = directory + "/" + self.filename
	if os.path.isfile(filepath):
	  uri = "file:///" + filepath
	  self.playmode = True
	  self.player.set_property("uri", uri) 
	  self.player.set_state(gst.STATE_PLAYING)
	  #print "playing " + self.filename
	  while self.playmode:
	    time.sleep(1)    
    time.sleep(1)
    loop.quit()

players = []
for i in range(0, NUM_PLAYERS):
  players.append(Player())

gobject.threads_init()
# keeps the program going
loop = gobject.MainLoop()
loop.run()

```

It generates the following messages in the qjackctl message dialog:

```
14:22:42.205 JACK connection change.
14:22:42.424 JACK connection graph change.
14:22:42.608 JACK connection change.
port_name "script.py:out_jackaudiosink1_1" already exists
port_name "script.py:out_jackaudiosink1_1" already exists
port_name "script.py:out_jackaudiosink1_1" already exists

```

---

