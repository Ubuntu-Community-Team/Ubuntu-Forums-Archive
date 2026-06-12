---
title: "Strange Memory/Crashing Issues with Pangolin 7"
date: 2011-01-02
forum: System76 Support
---

### Post by excalq on 2011-01-02
I have a Pangolin 7 that I purchased about half a year ago. I'm still running 10.04. Just the last week, I've started having frequent crashing of applications, tabs dying in Chrome, and many segfaults and such occurring. This usually starts happening after several hours of stability, and it usually gets bad enough that I have to reboot before being able to do anything.

What is going on here? I ran MemTest86+ overnight and found no errors. my harddrive's SMART utility also reports no errors.
This issue still happens with swap disabled. It has the hallmarks of memory corruption, as near as I can tell, or at least some hardware issue. Where do I go from here? I'm not sure what else I can do to diagnose the issue.

Here is a sample of errors I receive while trying to open my browsers once this problem starts happening:

```

arthur@jormungandr:~$ google-chrome 
[4978:4978:12279427024:ERROR:chrome/browser/browser_main_posix.cc(217)] Failed to create shutdown detector task.
Segmentation fault

arthur@jormungandr:~$ chromium-browser 
/usr/lib/chromium-browser/chromium-browser: error while loading shared libraries: cannot make segment writable for relocation: Cannot allocate memory

arthur@jormungandr:~$ firefox 
terminate called after throwing an instance of 'std::bad_alloc'
  what():  std::bad_alloc
ExceptionHandler::GenerateDump waitpid failed:No child processes

```

---

### Post by excalq on 2011-01-03
Something odd is that hitting CTRL-ALT-BACKSPACE and restarting my X session seems to help, and buy a few more hours of stability. Maybe its time to just install 10.10 fresh and redo the whole system...

---

