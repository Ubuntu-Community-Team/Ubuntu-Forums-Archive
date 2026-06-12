---
title: "Starting app at boot and prompt"
date: 2006-08-17
forum: Server Platforms
---

### Post by Kurdt on 2006-08-17
Hi :) 

I am running a security cam server with *webcam_server* (from webcamserver.sourceforge.net) works fine and is very useful, but i need it to start at boot, so i made a script copying and modifying skeleton, the thing is that when you run this program it do not release the prompt, see:

```
andresgd@pc009:~$ webcam_server
[](that's the cursor)
```

the problem is that the same happens with my home made startup script:

```
andresgd@pc009:/etc/init.d$ ./webcamDoor start
Starting webcam:[] 
```

The program works, but i know that this is not just right. how can i force the program to release the prompt ?

I hope this isn't some stupid question, and thanks :)

---

### Post by gerbman on 2006-08-17
Not a stupid question, but a simple one...put a "&" at the end of the command that starts the program. It will run the process in the background, leaving the terminal free.

---

### Post by Kurdt on 2006-08-17
Hey thanks!

It works :) but how would i put this on the script?

```
DAEMON=/usr/local/bin/webcam_server
```

i put ```
DAEMON=/usr/local/bin/webcam_server &
```

but that character it's interpreted different inside the script (i noticed when i run it)

---

### Post by LordHunter317 on 2006-08-17
That causes the shell to perform the assignment 'DAEMON=blah' in the background.

You have to append the & when you expand daemon.  However, that won't work either because unless the server actually runs as a daemon (in which case, you wouldn't have to do that) it will get killed when the init process finishes.

Use start-stop-daemon.  Read the manpage.  You'll want the --background switch.

---

### Post by Kurdt on 2006-08-18
Thanks!! i used --background and now it's working fine :)

---

### Post by NetBSD on 2006-09-20
[QUOTE=webcam_server -h]
usage: webcam_server [options]

     option             description [default value]

     -a                 - test mode (fps) [no]
     -c "caption"       - caption text [%Y-%m-%d %H:%M:%S], "" for none
     -d video_device    - v4l compliant device [/dev/video]
     -Ds                - disable stream support [no]
     -Dh                - disable http support [no]
     -fh                - flip image horizontally
     -fv                - flip image vertically
     -g geometry        - change default geometry (WIDTHxHEIGHT) [320x240]
     -G gamma           - gamma correction (-100-100) [0]
     -h                 - this help screen
     -l logfile         - log to file [/var/log/webcam_server.log]
     -mb                - maximum bytes per connection [0 (disabled)]
     -ms                - maximum seconds per connection [0 (disabled)]
     -mf                - maximum frames per connection [0 (disabled)]
     -n                 - force use of read() system call, rather than mmap
     -p tcp_port        - tcp listen port [8888]
     -q jpeg_quality    - jpeg compression quality (0-100) [60]
     -r                 - if camera init fails, retry forever [no]
     -R value           - rotate image value*90 degrees CCW (0-3) [0]
     -s                 - daemon mode [no]
     -tf R,G,B          - text forground colour [255,255,255]
     -tb R,G,B          - text background colour [0,0,0]
     -tt R,G,B          - transparency colour [128,0,128]
                          (set -tf or -tb to this to make transparent)
     -T x,y             - xy-position of text [0,0]
     -v                 - verbose [no]
     -x                 - swap RGB -> BGR [no]
[/QUOTE]

tells you right there, -s for daemon mode

---

