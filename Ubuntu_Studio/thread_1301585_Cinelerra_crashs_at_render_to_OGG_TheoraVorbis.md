---
title: "Cinelerra crashs at render to OGG Theora/Vorbis"
date: 2009-10-26
forum: Ubuntu Studio
---

### Post by biker3 on 2009-10-26
Hi. When I try to render in OGG Theora/Vorbis, Cinelerra crashs. The problem doesn't happen if only render video tracks, it only happen if I check render audio tracks also.

This is the output in console:
```
Cinelerra 4.1 (C)2009 Adam Williams

Cinelerra is free software, covered by the GNU General Public License,
and you are welcome to change it and/or distribute copies of it under
certain conditions. There is absolutely no warranty for Cinelerra.
The Vorbis encoder could not set up a mode according to
the requested quality or bitrate.

signal_entry: got SIGSEGV my pid=4901 execution table size=16:
    render.C: ~RenderWindow: 1105
    formattools.C: ~FormatTools: 59
    formattools.C: ~FormatTools: 61
    formattools.C: ~FormatTools: 63
    formattools.C: ~FormatTools: 65
    formattools.C: ~FormatTools: 68
    formattools.C: ~FormatTools: 70
    formattools.C: ~FormatTools: 72
    formattools.C: ~FormatVThread: 600
    formattools.C: ~FormatVThread: 602
    formattools.C: ~FormatVThread: 604
    formattools.C: ~FormatTools: 74
    formattools.C: ~FormatTools: 76
    render.C: ~RenderWindow: 1107
    render.C: ~RenderWindow: 1109
    render.C: ~RenderWindow: 1111
signal_entry: lock table size=14
    0x25bb310 RemoveThread::input_lock RemoveThread::run 
    0x258e3b0 BC_Synchronous::next_command BC_Synchronous::run 
    0x374e4f0 TransportQue::output_lock PlaybackEngine::run 
    0x374f000 MainIndexes::input_lock MainIndexes::run 1 
    0x37e0000 ResourceThread::draw_lock ResourceThread::run 
    0x367ee30 TransportQue::output_lock PlaybackEngine::run 
    0x381cb30 BC_Repeater::pause_lock BC_Repeater::run 
    0x360f2b0 BC_WindowBase::event_condition BC_WindowBase::get_event 
    0x36b0580 BC_WindowBase::event_condition BC_WindowBase::get_event 
    0x33ec840 BC_WindowBase::event_condition BC_WindowBase::get_event 
    0x3546c90 BC_WindowBase::event_condition BC_WindowBase::get_event 
    0x3680cf0 BC_WindowBase::event_condition BC_WindowBase::get_event 
    0x381e970 BC_WindowBase::event_condition BC_WindowBase::get_event 
    0x3750e90 BC_WindowBase::event_condition BC_WindowBase::get_event 
BC_Signals::dump_buffers: buffer table size=0
BC_Signals::delete_temps: deleting 0 temp files
SigHandler::signal_handler total files=0
Abortado
```
Does anyone know this problem?
I have tried with average bitrate and variable bitrate, with min bitrate, avg bitrate and max bitrate at 56, 96 and 128, respectively, and 56000, 96000 and 128000, respectively. But the problem persists.

Thanks

---

### Post by kayosiii on 2009-10-28
You will probably get more response from the mailing lists on the cinelerra cvs website (assuming you are running the cvs version).

[http://cvs.cinelerra.org/](http://cvs.cinelerra.org/)

---

### Post by biker3 on 2009-10-28
Thanks, I will look there :)

---

