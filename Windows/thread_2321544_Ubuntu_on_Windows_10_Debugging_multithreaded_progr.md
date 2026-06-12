---
title: "Ubuntu on Windows 10: Debugging multithreaded programs with gdb"
date: 2016-04-23
forum: Windows
---

### Post by aseering on 2016-04-23
Hi all,

I originally posted this on Microsoft forums [here]("https://social.msdn.microsoft.com/Forums/en-US/555a916e-bf7d-450c-8e10-af0b84737b62/windows-bash-cant-debug-multithreaded-applications-with-gdb?forum=windbg"), but was directed back to this forum as a more appropriate location.  Let me know if I should direct my question elsewhere.  For context, I'm normally an Ubuntu/Linux user, but in this instance I'm trying out the new beta release of Ubuntu on Windows 10 (aka "Windows Bash", etc).  Note that this issue doesn't reproduce on Ubuntu/Linux.


I'm seeing lots of crashes in more complicated Linux applications running on Windows.  (Did I mention that it's really cool that I'm running Linux applications on Windows?)  I'm trying to track down exactly what's going on.  gdb is my first go-to tool for debugging applications under Linux; I think it wouldn't be too much to say that it's the standard Linux tool for lots of types of debugging.  But I'm finding that it can't debug even the simplest of threaded applications on Windows Bash.  (It has no such problem under a real Linux kernel.)
Here's a minimal reproducer:


```

#include<pthread.h>

// Make thread spin indefinitely
void*spin(void* no_arg)
{
    while(1);
    return NULL;
}

int main()
{
    pthread_t spin_thread;
    pthread_create(&spin_thread, NULL, spin, NULL);
    while(1);
    return0;
}

```

To compile, write to a file and run "gcc <filename> -lpthread -g".  Then, to test, do "gdb ./a.out".  Once you get to the gdb prompt, type "run".  What I see is:
(gdb) run
Starting program: /mnt/c/Users/[me]/linwrapper/a.out
warning: Error disabling address space randomization: Success
warning: linux_ptrace_test_ret_to_nx: PTRACE_KILL waitpid returned -1: Interrupted system call
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".
[New Thread 0x7ff5ff600700 (LWP 414)]
Cannot find user-level thread for LWP 410: generic error
(gdb)

On a real Linux kernel, "run" doesn't return until you hit Ctrl-C, because the command spins forever.  It certainly doesn't error out.
I write and work with a lot of code in C/C++.  And threads are pretty much unavoidable these days.  And I'm not going to pretend that my code never has bugs :-)  Is there a good way to debug multithreaded Linux apps in Windows Bash?

Thanks!

---

### Post by TheFu on 2016-04-23
It works as expected on Linux, but doesn't work on Windows.  That tells me it is a Windows issue.  I'd file a bug report with the Windows Bash-for-Linux team.  OTOH, that sounds like alpha code, so probably just wait for the next few updates and maybe they will fix it.  I don't know how that is implemented on Windows (Won't have Win10 here - er --- ever).   MSFT will need full thread support if they hope to get docker working well under Windows (which I think is the main reason for this effort).

OTOH, what do I know? Nothing.

---

### Post by aseering on 2016-04-26
Yeah, I kinda figured that would be the response here...  (And, yeah, real Ubuntu is great; but I personally have to use Windows sometimes, and this feature has the potential to make things much easier for me.)  But the folks on MSDN and Windows Insider forums both seemed really insistent that I should ask in the Ubuntu forums, so I figured I ought to at least make the effort.

For future reference, there appears to be a Github bug-tracker for BashOnWindows these days:

[https://github.com/Microsoft/BashOnWindows/](https://github.com/Microsoft/BashOnWindows/)

This specific issue was already posted there:

[https://github.com/Microsoft/BashOnWindows/issues/204](https://github.com/Microsoft/BashOnWindows/issues/204)

I've followed up there.

---

### Post by TheFu on 2016-04-26
So Bash On Windows isn't just about bash?  The intent is to provide a full-unix-like environment, for people AND programs?   Would be great if the full Linux-API was provided AND behaved as expected - though I never plan to touch Windows in any serious way again. But if it pays the mortgage, I don't have any issue with folks doing that. ;)  If they made BashOnWindows work for Win7, I'd be interested - that's the newest Win-anything I've seen.

I need to review the intention of the BashOnWindows subsystem. 

[https://blogs.windows.com/buildingapps/2016/03/30/run-bash-on-ubuntu-on-windows/](https://blogs.windows.com/buildingapps/2016/03/30/run-bash-on-ubuntu-on-windows/)
> This is not a server platform upon which you will host websites, run server infrastructure, etc. 
The primary goal for this stuff appears to be to support core Linux user-space CLI tools.  BTW, I love the tone of the 3 articles I've read so far from MSFT.  Can't wait for a real ssh, sftp, ssh-copy-id to work on Windows. I miss select/paste every time I'm forced there.  Tried to get remote powershell working, always failed.  After all, a GUI is just there to let me have more xterms open. ;)

I was a cross-platform C/C++ guy for about a decade and wrote MT code for about 12+ platforms, including Windows.  It has been a long time, but I wrote a thread library to hide the differences between how Windows, Mac, AIX, and all the other Unixen handled threads. They were pretty close already, if my memory is true.  Had more issues writing a dynamic cross-platform shared library loader - HP-UX was weird. Again, could be my selective memory, so don't quote me. What I recall was that C/C++ for servers was already fairly cross-platform.  Just don't use the win32 API and all that code recompiled with minor issues.  For lurkers, the '/' as a directory separator has worked almost forever on all the main platforms - even in a cmd.exe shell.  Try it. It works.  There are slight differences between allowed characters in file/directories, but those don't happen too often.  

BTW - last time I used gdb, I don't think it supported MT debugging. It has been that long.

---

### Post by howefield on 2016-04-26
Thread moved to the "*Windows*" sub forum which is probably more appropriate, at least for now.

---

### Post by aseering on 2016-04-26
Yeah -- the name "Windows Bash" is confusing IMO, and hides how much dev work they've done here.  I think of it as kind of like what Wine is for Linux, except in reverse.  Like Wine, lots of apps don't work properly yet, but Microsoft seems to be making progress quickly.  (They seem to have lots of syscalls working well, but /proc and /dev are pretty sparse in the initial release.)  Linux is, of course, much more open than Windows; hopefully it'll eventually be quite robust.

The reason that it might have made sense to ask this question in the Ubuntu forums is that the chroot that Microsoft is bundling is provided by Canonical, and is a mostly-stock Ubuntu 14.04 image.  So this is Ubuntu's gdb binary trying to connect to an executable compiled with Ubuntu's build of gcc, all installed by doing "apt-get"'s against the standard Ubuntu repositories.  Just, not on an Ubuntu-packaged kernel :-)

---

### Post by TheFu on 2016-04-26
Agreed.  This is good for MSFT and for Linux. Plus anything that doesn't require Mono/.NET is a plus to me. ;)  
Threading would definitely be a feature of the kernel, not user-space.  You've provided a simple test for the MSFT guys around MT support of their modified kernel.  That should help, but MT code has all sorts of strange, unknowable-before-the-issue-happens problems.  Even simple MT code can cause non-homogeneity data. That's bad.  I did about 5yrs of MT coding for a real-time system.  We took extreme steps to ensure data on different threads wasn't mixed in time, except when it was safe to do it. Plus this wasn't just multi-threaded, but multi-priority code.  High priority threads could interrupt lower priorities mid-instruction.   We had checklists for the checklists to help prevent bugs. That mostly worked, but sometimes ... well, 7-levels of testing would find most bugs.

---

### Post by vikram91 on 2017-03-07
So what was the resolution? It looks like it is fixed in insider preview builds? (See [here]("https://github.com/Microsoft/BashOnWindows/issues/875"))

---

### Post by QIII on 2017-03-07
Rest In Peace, old thread.

---

