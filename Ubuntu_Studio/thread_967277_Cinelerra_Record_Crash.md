---
title: "Cinelerra Record Crash"
date: 2008-11-01
forum: Ubuntu Studio
---

### Post by jelkimantis on 2008-11-01
I tried searching for this thread, because i'm sure that I'm not the only one with this problem, but cinelerra crashes on record.

```
    recordthread.C: ~RecordThread: 52
    recordthread.C: ~RecordThread: 54
    recordthread.C: ~RecordThread: 56
    record.C: run: 487
    recordthread.C: ~RecordThread: 42
    recordthread.C: ~RecordThread: 44
    recordthread.C: ~RecordThread: 46
    recordthread.C: ~RecordThread: 48
    recordthread.C: ~RecordThread: 50
    recordthread.C: ~RecordThread: 52
    recordthread.C: ~RecordThread: 54
    recordthread.C: ~RecordThread: 56
    record.C: run: 492
    record.C: run: 495
    RecordGUI::~RecordGUI 1
    RecordGUI::~RecordGUI 2
signal_entry: lock table size=13
    0x8c41460 TransportQue::output_lock PlaybackEngine::run 
    0x8cee958 TransportQue::output_lock PlaybackEngine::run 
    0x8ceef90 MainIndexes::input_lock MainIndexes::run 1 
    0x8d5d728 ResourceThread::draw_lock ResourceThread::run 
    0x8566678 BC_Synchronous::next_command BC_Synchronous::run 
    0x8c661f0 BC_WindowBase::event_condition BC_WindowBase::get_event 
    0x8a1e690 BC_WindowBase::event_condition BC_WindowBase::get_event 
    0x8b460d8 BC_WindowBase::event_condition BC_WindowBase::get_event 
    0x8d8e278 BC_WindowBase::event_condition BC_WindowBase::get_event 
    0x8c42af8 BC_WindowBase::event_condition BC_WindowBase::get_event 
    0x8be2428 BC_WindowBase::event_condition BC_WindowBase::get_event 
    0x8cf0da0 BC_WindowBase::event_condition BC_WindowBase::get_event 
    0x8d24de0 Record::window_lock Record::run 4 *
BC_Signals::dump_buffers: buffer table size=0
BC_Signals::delete_temps: deleting 0 temp files
SigHandler::signal_handler total files=0
Aborted

```
is what I get from the CL when this thing barfs.  The capture occurs, but it's really annoying to capture, restart, edit (or capture more) and repeat the cycle.  Any insight into this problem would be great.

jsl

---

