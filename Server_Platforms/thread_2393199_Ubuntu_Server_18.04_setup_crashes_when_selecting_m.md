---
title: "Ubuntu Server 18.04 setup crashes when selecting manual drive partitioning"
date: 2018-05-30
forum: Server Platforms
---

### Post by nnvt on 2018-05-30
Hi there!

I'm trying to install Ubuntu Server 18.04 on an old laptop board I had laying around (previously ran Server 17.10). I can't seem to progress past the "filesystem setup" part, I click on manual and a bunch of python errors show only for it to bring me back to the start screen.

I have the setup on a 120gb ssd that also holds the partition the OS will be installed on. That's the only drive in the system.

I took some burst photos with my phone to see what it was and it seems to be ui related, there are errors in the following files: "widget.py" and "listbox.py". For widget.py it says "in cached_render canv = ...". I'm not sure if these are logged somewhere, I checked the syslog file but it's not in there.

The ISO is definitely not corrupted and I tried to write the ISO in dd mode, via etcher on macos and via rufus on windows.

Any ideas on what could be causing this?

EDIT: found the log:
> 2018-05-30 23:24:03,155 subiquity.ui.filesystem.filesystem:114 FileSystemView init complete()2018-05-30 23:24:03,158 subiquitycore.core:350 Exception in controller.run():
Traceback (most recent call last):
  File "/snap/subiquity/346/lib/python3.6/site-packages/subiquitycore/core.py", line 348, in run
    self.common['loop'].run()
  File "/snap/subiquity/346/usr/lib/python3/dist-packages/urwid/main_loop.py", line 286, in run
    self._run()
  File "/snap/subiquity/346/usr/lib/python3/dist-packages/urwid/main_loop.py", line 384, in _run
    self.event_loop.run()
  File "/snap/subiquity/346/usr/lib/python3/dist-packages/urwid/main_loop.py", line 788, in run
    self._loop()
  File "/snap/subiquity/346/usr/lib/python3/dist-packages/urwid/main_loop.py", line 816, in _loop
    self._entering_idle()
  File "/snap/subiquity/346/usr/lib/python3/dist-packages/urwid/main_loop.py", line 777, in _entering_idle
    callback()
  File "/snap/subiquity/346/usr/lib/python3/dist-packages/urwid/main_loop.py", line 572, in entering_idle
    self.draw_screen()
  File "/snap/subiquity/346/usr/lib/python3/dist-packages/urwid/main_loop.py", line 586, in draw_screen
    canvas = self._topmost_widget.render(self.screen_size, focus=True)
  File "/snap/subiquity/346/usr/lib/python3/dist-packages/urwid/widget.py", line 144, in cached_render
    canv = fn(self, size, focus=focus)
  File "/snap/subiquity/346/usr/lib/python3/dist-packages/urwid/wimp.py", line 638, in render
    self._update_overlay(size, focus)
  File "/snap/subiquity/346/usr/lib/python3/dist-packages/urwid/wimp.py", line 618, in _update_overlay
    canv = self._original_widget.render(size, focus=focus)
  File "/snap/subiquity/346/usr/lib/python3/dist-packages/urwid/widget.py", line 144, in cached_render
    canv = fn(self, size, focus=focus)
  File "/snap/subiquity/346/usr/lib/python3/dist-packages/urwid/widget.py", line 1765, in render
    canv = get_delegate(self).render(size, focus=focus)
  File "/snap/subiquity/346/usr/lib/python3/dist-packages/urwid/widget.py", line 144, in cached_render
    canv = fn(self, size, focus=focus)
  File "/snap/subiquity/346/usr/lib/python3/dist-packages/urwid/decoration.py", line 226, in render
    canv = self._original_widget.render(size, focus=focus)
  File "/snap/subiquity/346/usr/lib/python3/dist-packages/urwid/widget.py", line 144, in cached_render
    canv = fn(self, size, focus=focus)
  File "/snap/subiquity/346/usr/lib/python3/dist-packages/urwid/container.py", line 1086, in render
    focus and self.focus_part == 'body')
  File "/snap/subiquity/346/usr/lib/python3/dist-packages/urwid/widget.py", line 144, in cached_render
    canv = fn(self, size, focus=focus)
  File "/snap/subiquity/346/usr/lib/python3/dist-packages/urwid/widget.py", line 1765, in render
    canv = get_delegate(self).render(size, focus=focus)
  File "/snap/subiquity/346/usr/lib/python3/dist-packages/urwid/widget.py", line 144, in cached_render
    canv = fn(self, size, focus=focus)
  File "/snap/subiquity/346/usr/lib/python3/dist-packages/urwid/container.py", line 1529, in render
    canv = w.render((maxcol, rows), focus=focus and item_focus)
  File "/snap/subiquity/346/usr/lib/python3/dist-packages/urwid/widget.py", line 144, in cached_render
    canv = fn(self, size, focus=focus)
  File "/snap/subiquity/346/usr/lib/python3/dist-packages/urwid/decoration.py", line 567, in render
    canv = self._original_widget.render((maxcol,)+size[1:], focus)
  File "/snap/subiquity/346/usr/lib/python3/dist-packages/urwid/widget.py", line 144, in cached_render
    canv = fn(self, size, focus=focus)
  File "/snap/subiquity/346/lib/python3.6/site-packages/subiquitycore/ui/container.py", line 407, in render
    visible = self.ends_visible(size, focus)
  File "/snap/subiquity/346/usr/lib/python3/dist-packages/urwid/listbox.py", line 1611, in ends_visible
    focus=focus )
  File "/snap/subiquity/346/usr/lib/python3/dist-packages/urwid/listbox.py", line 353, in calculate_visible
    self._set_focus_complete( (maxcol, maxrow), focus )
  File "/snap/subiquity/346/lib/python3.6/site-packages/subiquitycore/ui/container.py", line 381, in _set_focus_complete
    super()._set_focus_complete(size, focus)
  File "/snap/subiquity/346/usr/lib/python3/dist-packages/urwid/listbox.py", line 718, in _set_focus_complete
    (maxcol,maxrow), focus)
  File "/snap/subiquity/346/usr/lib/python3/dist-packages/urwid/listbox.py", line 688, in _set_focus_first_selectable
    (maxcol, maxrow), focus=focus)
  File "/snap/subiquity/346/usr/lib/python3/dist-packages/urwid/listbox.py", line 420, in calculate_visible
    n_rows = next.rows( (maxcol,) )
  File "/snap/subiquity/346/usr/lib/python3/dist-packages/urwid/widget.py", line 204, in cached_rows
    return fn(self, size, focus)
  File "/snap/subiquity/346/usr/lib/python3/dist-packages/urwid/decoration.py", line 615, in rows
    return self._original_widget.rows((maxcol-left-right,), focus=focus)
AttributeError: 'int' object has no attribute 'rows'

---

### Post by LHammonds on 2018-05-31
Which ISO image did you download?

ubuntu-18.04-server-amd64.iso (which is called "alternative")
ubuntu-18.04-live-server-amd64.iso (which is the default but uses the desktop "live" installer)

LHammonds

---

### Post by kra28 on 2019-02-06
> **LHammonds said:**
> Which ISO image did you download?

ubuntu-18.04-server-amd64.iso (which is called "alternative")
ubuntu-18.04-live-server-amd64.iso (which is the default but uses the desktop "live" installer)

LHammonds

Hello,
  I have the same problem for the iso file ubuntu-18.04.1-live-server-amd64.iso.

Thank you for an answer,

Michal

---

