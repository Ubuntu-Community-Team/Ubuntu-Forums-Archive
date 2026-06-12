---
title: "rdesktop/xrdp: error - problem connecting (to 127.0.0.1 5910)"
date: 2006-08-24
forum: Server Platforms
---

### Post by mikko.ostlund on 2006-08-24
Hi!

Abstract: I have installed xrdp in Fedora Core 5, but fail to connect to
it with "rdesktop localhost". I'm hoping someone can help me to get it
working.

Details about my system:
   * "uname -a":    Linux desktop 2.6.17-1.2174_FC5 #1 Tue Aug 8 15:30:55 \
                    EDT 2006 i686 i686 i386 GNU/Linux
   * Gnome version: 2.4.13
       Distributor: Red Hat, Inc
        Build date: 08/02/2006
   * rdesktop version: 1.4.1
   * xrdp version: 0.3.1
   * Firewall: "Disabled" (in dialog "System"->"Administration"->
                  ->"Security Level and Firewall")
   * SELinux: "Disabled" (in the same dialog as the firewall above)

Details about how I installed xrdp:
1. I browsed to
    http://sourceforge.net/project/showfiles.php?group_id=112022&package_id=195021&release_id=435591"
   and downloaded "xrdp-0.3.1.tar.gz".
2. I unpzipped it with "gunzip xrdp-0.3.1.tar.gz".
3. I untared it with "tar xvf xrdp-0.3.1.tar".
4. I entered the xrdp-0.3.1 directory with "cd xrdp-0.3.1".
5. I built the whole project by running "make" in the xrdp-0.3.1 directory.
6. I switched to the root user with "su".
7. I installed everything with "make install".

Details about how I ran it and how the problem occurred:
1. I started xrdp by running, still logged in as root, "/usr/local/xrdp/xrdpstart.sh".
2. In another terminal window, logged in as a normal user, I ran "rdesktop localhost".
3. A window, titled "rdesktop - localhost", appeared.
4. Inside the "rdesktop - localhost" window a subwindow appeared. The title of the subwindow was "Connection Log".
5. In the subwindow, the following text appeared:
   "started connecting
    connecting to sesman
    sending login info to sesman
    receiving sesman header
    receiving sesman data
    sesman started a session
    connecting to 127.0.0.1 5910
    error - problem connecting"
6. End of story; nothing further happened.

Contents of file "/usr/local/xrdp/sesman.log":
    [20060824-16:27:30] [DEBUG] starting sesman with pid 3727
    [20060824-16:27:30] [DEBUG] listening...
    [20060824-16:27:39] [DEBUG] granted TS access to user mikko
    [20060824-16:27:39] [DEBUG] starting Xvnc session...
    [20060824-16:27:41] [DEBUG] session 3730 - user mikko - terminated

The following files contained nothing (size 0 bytes):
    "/usr/local/xrdp/sesman.boot.log"
    "/usr/local/xrdp/xrdp.boot.log"

The user "hela" of this forum, seems to have got around the problem by
installing "kubuntu-desktop" (refer to the posting
[http://www.ubuntuforums.org/showthread.php?t=239616)](http://www.ubuntuforums.org/showthread.php?t=239616)), but I would like to
see the problem actually solved for the Gnome desktop.

Appreciating any attempts to shed some light on this,

   Mikko
   Stockholm, Sweden

---

### Post by sbassett on 2006-08-24
> **mikko.ostlund said:**
> 

Appreciating any attempts to shed some light on this,

   Mikko
   Stockholm, Sweden

Found this little tidbit, don't know if you tried this or not yet:

/usr/local/xrdp/startwm.sh 

should look like this 
 
```
#!/bin/sh 
 
gnome-session  
```

Make sure you make a backup of startwm.sh before anything.

---

### Post by mikko.ostlund on 2006-08-24
Yeah, I already tried that; no visible difference. Thanks anyway, Sbassett!

I made the following experiment to get more information.
I made the file "/usr/local/xrdp/startwm.sh" look like this
(the dashed lines just symbolize the beginning and the end
of the file):

-----------------------------------------------------
#!/bin/sh
gnome-session >/home/mikko/gnome_session_log.txt 2>&1
-----------------------------------------------------

(I.e. I redirected the standard output and standard error of
gnome-session to the file "gnome_session_log.txt" in my home directory.)

Having run "/usr/local/xrdp/xrdpstart.sh", followed by "rdesktop localhost",
again, the contents of the file "/home/mikko/gnome_session_log.txt" was
as follows:

[mikko@desktop ~]$ cat gnome_session_log.txt
SESSION_MANAGER=local/desktop:/tmp/.ICE-unix/4355
The program 'gnome_segv2' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 470 error_code 8 request_code 72 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Window manager warning: Log level 32: could not find XKB extension.
Window manager warning: Lost connection to the display ':10.0';
most likely the X server was shut down or you killed/destroyed
the window manager.
[mikko@desktop ~]$


It is obvious that something is wrong, but what? Can anyone help
me here?

Mikko

---

### Post by mikko.ostlund on 2006-08-26
I appologize for having added this thread to Ubuntuforums;
it's a Fedora Core 5 issue. It was by mistake; I have an
Ubuntu laptop from which I want to rdesktop to a Fedora
Core 5 desktop. However, the Ubuntu is not yet involved
here. This thread is (at least so far) only about the
problem I saw then running "rdesktop localhost" on the
Fedora.

---

