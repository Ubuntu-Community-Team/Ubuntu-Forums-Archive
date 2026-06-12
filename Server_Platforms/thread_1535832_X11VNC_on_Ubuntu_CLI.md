---
title: "X11VNC on Ubuntu CLI"
date: 2010-07-21
forum: Server Platforms
---

### Post by wesg on 2010-07-21
My Ubuntu server does not have a GUI. Is it possible for me to run x11vnc to connect to the server from my laptop to set up software? Specifically I'm trying to configure MythTV because x11 forwarding did not work so well.

---

### Post by arrrghhh on 2010-07-21
I don't think that will work unless you have X installed.  Why doesn't forwarding X work?  I do that with dolphin if I'm feelin lazy.

---

### Post by gobbledigook on 2010-07-21
sure you can,

```
sudo apt-get install x11vnc
```

```
x11vnc -display :0
```

that will start it and you can connect using a vnc client such as tightvnc, there is fairly good documentation at the [**_x11vn_**]("http://www.karlrunge.com/x11vnc/") site, just scroll down a bit... and do make sure you have a basic gui installed on the server ;)

---

### Post by krunge on 2010-07-21
Since you don't seem to want to view a GUI on physical hardware for this server, why not use the 'vncserver' package instead of x11vnc?  vncserver will create a virtual (RAM only) display that can be viewed via VNC.

Installing the x11vnc and xvfb packages can be used to emulate 'vncserver', but might be more difficult for you to setup.  I can show you how to run x11vnc+xvfb if you want.

---

### Post by arrrghhh on 2010-07-21
Huh, so what are you greeted with if you do use x11vnc... A terminal session in a VNC window I assume?  Or just a blank window that gets populated when programs that use X run?

---

### Post by krunge on 2010-07-21
> Huh, so what are you greeted with if you do use x11vnc... 

I assume you mean if one uses the x11vnc+xvfb method I alluded to.  If you point x11vnc to the physical display (e.g. DISPLAY=:0 ) you are of course greeted with whatever is on the physical display. 
> A terminal session in a VNC window I assume?  Or just a blank window that gets populated when programs that use X run?
The x11vnc+xvfb scheme can greet you with anything, but it might require some configuration.  It can even greet you with gdm or kdm login panel if you want  it to.  Or if you supply '-env FD_SESS=gnome' a gnome session is started, '-env FD_SESS=kde' for KDE, etc.  By default it will look in places like ~/.dmrc to try to guess the user's preferred desktop, then it tries ~/.xsession, etc.

---

### Post by arrrghhh on 2010-07-22
This is assuming I have KDE or Gnome installed.  Does this also require X to be installed?  I think that was the whole point, to do this without X...

---

### Post by krunge on 2010-07-23
> This is assuming I have KDE or Gnome installed.  Does this also require X to be installed?  I think that was the whole point, to do this without X...
I'm not sure.

What does 'without X' mean?  Does that exclude installing 'Xvfb' or 'xterm'?  

Do you just want to see an xterm running in Xvfb server naked without any window manager? (not even twm) [I think this is what x11vnc -env FD_SESS=failsafe will actually do]

Sorry if I missed the point of what you or the other posters want to achieve.

---

### Post by arrrghhh on 2010-07-23
I'm talking without X as in without X.org?  X11?  The display server basically?  No window manager, nothing...  Text-based console only!

---

### Post by krunge on 2010-07-23
> I'm talking without X as in without X.org?  X11?  The display server basically?
To me X.org and X11 are just software files on the hard disk that may or may not be used.  I understand that you might think about them differently.
>   No window manager, nothing...  Text-based console only!
OK, what next?  I still don't understand your question...

---

### Post by arrrghhh on 2010-07-23
> **krunge said:**
> To me X.org and X11 are just software files on the hard disk that may or may not be used.  I understand that you might think about them differently.

OK, what next?  I still don't understand your question...

I don't get what you mean by either of these comments.  I was wondering how x11-vnc would work without x11 installed...

That's my question.  What would you get?  A console view with the local login?  A blank window that only populates when something related to X runs?  Without X installed, how would that even work?!?

---

### Post by krunge on 2010-07-23
> I was wondering how x11vnc would work without x11 installed...
x11vnc can export the linux text console by either of these methods:
```

x11vnc -rawfb console
x11vnc -rawfb vt1

```
The latter does not require the kernel framebuffer device to be configured. Both commands would need to be run as root.

Note that once the 'x11vnc' package is installed that will install some X11 libraries (e.g. libX11.so.6 and libXtst.so.6), but it probably won't install any other parts of X.org.

So at this point the only way for x11vnc to export an X11 desktop is remotely:
```
x11vnc -noshm -display someothermachine:0
```
(of course one would need to have the permission from the X server on someothermachine to do this.)

As I alluded in my first post in this thread, if one installs the 'xvfb' package then one can run a virtual X server on the same machine. I imagine 'apt-get install xvfb' brings in a good deal of X.org.  So at this point one could start a bare X server like this:
```
Xvfb :3
```
and attach x11vnc to it via:
```
x11vnc -display :3
```
But there won't be any apps running on it or even a window manager. One could run those on another machine with DISPLAY set properly (that is how Xterminals and linux terminal servers work; usually with a physical display instead of Xvfb.)

Well, then you could add apps and windows managers etc to the machine.  I.e. work your way up bit by bit via 'apt-get'. xterm might already be installed due to x11vnc's dependencies.

Anyway, those are some of the things one could do with it.

---

### Post by arrrghhh on 2010-07-23
Based on your post, it sounds like x11-vnc package would install a fair bit of X.org.  Probably more than you assume.

I wouldn't do this if you don't have X installed.  Just seems like a bad idea.  Forwarding X is real easy.

I know the OP started this because of an issue with forwarding X but I'm we didn't really ever look into that issue.

So, what was that issue?  I don't have any issues forwarding X.  Works great.

---

### Post by krunge on 2010-07-23
> Based on your post, it sounds like x11vnc package would install a fair bit of X.org.
Of course.  More if you install xvfb (and desktop) which I suggested to the OP since it seemed like he needed to have a GUI to admin the system.

But the OP exited long ago after his first post. I suggest we put this thread to sleep since I don't think we are helping anybody at this point.

---

### Post by arrrghhh on 2010-07-24
> **krunge said:**
> Of course.  More if you install xvfb (and desktop) which I suggested to the OP since it seemed like he needed to have a GUI to admin the system.

But the OP exited long ago after his first post. I suggest we put this thread to sleep since I don't think we are helping anybody at this point.

Agreed, I was curious for my own knowledge.

---

### Post by wesg on 2010-07-29
Hi everyone, thanks for the replies, just remembered the thread now. 

From what it sounds like, there are ways to do what I want, but with caveats. I asked the whole thing because X forwarding resulted in a terrible way to interact with the server... slow inputs, garbled video, etc. 

I install x11vnc then started a session on display :0 now how would I connect to that session and run the X application I need?

---

### Post by wesg on 2010-07-29
> **krunge said:**
> Installing the x11vnc and xvfb packages can be used to emulate 'vncserver', but might be more difficult for you to setup.  I can show you how to run x11vnc+xvfb if you want.

Am I too late to find out how this works? I don't have *any GUI* installed, though... does that affect it?

---

### Post by gobbledigook on 2010-07-30
> **gobbledigook said:**
>  you can connect using a vnc client such as tightvnc

As you have installed and started x11vnc with no problems, you just need to connect to it, if you use tightvnc (a vnc viewer) then you can just point it toward the ip of the server and it should connect with authenticaion (if enabled)

let us know what you see?

---

### Post by arrrghhh on 2010-07-30
> **wesg said:**
> Am I too late to find out how this works? I don't have *any GUI* installed, though... does that affect it?

From the back and forth that we had earlier, it sounds like you'll have to install quite a bit of X11 - if not all of it to have this working.  Kinda defeats the purpose of running w/o a GUI if you ask me, but that's really your decision.  Sure it's possible, but do you want to do it?

---

### Post by war59312 on 2010-08-17
Hi,

Sweet, thanks guys got x11vnc working perfectly now.

That said, x11vnc 0.9.11 is out now and would love to upgrade.

So does anyone have a trusted PPA for x11vnc ?

I would just build it myself but a bit over my pay grade at the moment. ;)

> *** A working X window system build environment is required to build x11vnc.  ***

Thanks,

Will

 
> New in the 0.9.11 x11vnc release:

    The source tree is synchronized with the most recent libvncclient
        (this only affects -reflect mode.)  The build is fixed
        for incompatibilities when using an external LibVNCServer
        (e.g.  ./configure --with-system-libvncserver...)

    The SSL enabled Java VNC Viewer Makefile has been modified so
        that the jar files that are built are compatible back
        to Java 1.4.

    In -reflect mode cursor position updates are now handled
        correctly.

    In -create/-unixpw mode, the env. var. FD_USERPREFS may be set
        to a filename in the user's home directory that includes
        default username:options values (so the options do not
        need to be typed every time at the login prompt.)

  miscellaneous new features and changes:

    An option -always_inject is provided: Even if there is no
        displacement (dx = dy = 0) for a VNC mouse event force
        the pointer to the indicated x,y position anyway.

    New java viewer debugging and workaround applet parameters:
        debugKeyboard mapF5_to_atsign forbid_Ctrl_Alt 

    You can set X11VNC_AVAHI_NAME, X11VNC_AVAHI_HOST, and/or
        X11VNC_AVAHI_PORT environment variables to override the
        default values. For example: -env X11VNC_AVAHI_NAME=wally

    When opening the X11 display extra XAUTHLOCALHOSTNAME settings
        are attempted.> New in the 0.9.10 x11vnc release:

    IPv6 is now supported for all usage modes: forward and reverse
        connections, SSL and unencrypted, etc.

    The included SSL enabled Java VNC viewer applet now supports
        Chained SSL Certificates (x11vnc -ssl always has.)
        The applet autodects x11vnc and set GET=1 for faster
        connecting via HTTPS.

    A demo CGI script 'desktop.cgi' shows how to create an
        SSL encrypted, multi-user x11vnc web login desktop
        service.  The user logs into a secure web site and gets
        his/her own virtual desktop and his browser accesses it
        with the SSL Java VNC Viewer applet.

    A serverCert Java Viewer applet parameter is provided.
        Use an authenticated HTTPS browser connection to set
        this parameter (the user could set it locally too.)
        The onetimekey tool has -certonly option for this scheme.

    The Xdummy script (use Xorg 'dummy' driver instead of Xvfb)
        no longer requires being run as root.


  miscellaneous new features and changes:

    In the Java viewer applet, debugCerts and debugKeyboard parameters
        are provided.  The debugging output of the applet is more
        readable.  Some corner-case bugs (e.g. socket exceptions)
        are now handled gracefully.  Parameters forbid_Ctrl_Alt
        and mapF5_to_atsign are added.

    The amount of time to wait for HTTPS applet downloads to finish
        can be set in env. var. X11VNC_HTTPS_DOWNLOAD_WAIT_TIME.

    The -xkb mode is automatically enabled if there are more than
        4 keysyms per key.

    -coe is now an alias for -connect_or_exit.

    The -input_eagerly option enables this LibVNCServer feature
        (it is like -allinput.)

    The "%" unix password verification tricks for the -unixpw
        option are now documented.  They also run a command
        in UNIXPW_CMD.

    In -create (-svc, etc.) modes, a warning is printed out if Xvfb
        cannot be found.  Xvfb '+kb' option is checked for.
        The -env CREATE_DISPLAY_OUTPUT=/tmp/mydebug.txt debugging
        option is documented.  Try to preserve user's PATH
        if possible.

        In XDMCP connection mode, a test for GDM listening only
        on IPv6 (::1) is performed.  The interface can also be
        specified via FD_XDMCP_IF.

    The example scripts connect_switch, ultravnc_repeater.pl, inet6to4
        have settings to let them run reliably for long times
        as daemons.  They also support IPv6.

    IPv6 notes: for some very esoteric cases (e.g. -chatwindow)
        IPv4 localhost may be required for local IPC.  A demo
        transition tool 'inet6to4' is also included (can be
        used for other apps.)  x11vnc options related to IPv6:
        -listen6, -6, -no6, -noipv4, -noipv6, and -connect,
        -proxy.

    Use STUNNEL_LISTEN in -stunnel mode to have it listen on a
        particular interface.  Also STUNNEL_PROG.

    New remote control query options: pointer_x, pointer_y,
        pointer_same, pointer_root, and pointer_mask. A demo
        script using them misc/panner.pl is provided.

    Remote control change of -clip option will not create new
        framebuffer if the size has not changed (for panner.pl)

    The X11VNC_DISABLE_SSL_CLIENT_MODE env. var. can be set to
        disable SSL client role in reverse connections.  This
        means the VNC viewer side must be in SSL client role.
        UltraVNC repeater operation can benefit from this.

        The SSL_INIT_TIMEOUT is increased to 1 hour if 'repeater'
        is detected in a reverse connect string.

    The X property X11VNC_TRAP_XRANDR can be set on a desktop to
        force x11vnc to use the -xrandr screen size change
        trapping code.

    The -sslScripts option prints out the SSL certificate management
        scripts.

    Suggest '-auth guess' and '-findauth' if X connection fails.

    The TightVNC sercurity type (TightVNC features enabler) now
        works for RFB version 3.8.

    RECORD scroll detection is now working with the new gtk/gdk scroll
        mechanism.  Set X11VNC_SCROLL_MUST_EQUAL to disable.


For more information:

    [http://www.karlrunge.com/x11vnc/](http://www.karlrunge.com/x11vnc/)
    [http://www.karlrunge.com/x11vnc/x11vnc_opts.html](http://www.karlrunge.com/x11vnc/x11vnc_opts.html)
           x11vnc -help | less

===========================================================================

ChangeLog:

2010-05-01  Karl Runge <runge@karlrunge.com>
        * x11vnc: X11VNC_DISABLE_SSL_CLIENT_MODE option to disable SSL
          client role in reverse connections.  Improvements to logging in
          ultravnc_repeater, ULTRAVNC_REPEATER_NO_RFB option.  Increase
          SSL timeout and print message if 'repeater' mode is detected for
          reverse SSL connection.  Fix RECORD scroll XCopyArea detection
          with recent gtk/gdk library; set X11VNC_SCROLL_MUST_EQUAL
          to disable.  Limit logging of RECORD error messages.

2010-04-25  Karl Runge <runge@karlrunge.com>
        * x11vnc: incorporate new ultravnc_dsm_helper.c, add pointer_mask
          remote control query.  Cut openssl default -ping delay.

2010-04-18  Karl Runge <runge@karlrunge.com>
        * x11vnc/misc: improvements to demo scripts
        * x11vnc: Alias -coe for -connect_or_exit.  more accurate
          dotted_ip() and -listen6.  Improvements to ipv6 mode.
          http interface for X11VNC_HTTP_LISTEN_LOCALHOST.  Print
          warning about missing Xvfb, Xdummy, or Xvnc in -create.
          Fix __LINUX_VIDEODEV2_H / HAVE_V4L2.  Always print out info
          about Xinerama screens.
        * x11vnc/misc/enhanced_tightvnc_viewer: check for host cmd.
          fix stunnel mode w/o proxy.  Update to stunnel 4.33, Fix
          build.unix with new stunnel on Solaris. ipv6 support for
          unix ssvncviewer

2010-04-09  Karl Runge <runge@karlrunge.com>
        * classes/ssl: debugging and workarounds for java viewer
        * x11vnc/misc: sync ssvnc, improve util scripts.
        * x11vnc: exit(1) for -connect_or_exit failure, quiet query
          mode for grab_state, etc. ipv6 support. STUNNEL_LISTEN for
          particular interface. -input_eagerly in addition to -allinput.
          quiet Xinerama message.

2010-03-20  Karl Runge <runge@karlrunge.com>
        * classes/ssl: Many improvements to Java SSL applet, onetimekey
          serverCert param, debugging printout, user dialogs, catch
          socket exceptions, autodetect x11vnc for GET=1.
        * x11vnc: misc/scripts: desktop.cgi, inet6to4, panner.pl.
          X11VNC_HTTPS_DOWNLOAD_WAIT_TIME, -unixpw %xxx documented, and
          can run user cmd in UNIXPW_CMD. FD_XDMCP_IF for create script,
          autodetect dm on udp6 only.  Queries: pointer_x, pointer_y,
          pointer_same, pointer_root.  Switch on -xkd if keysyms per key >
          4 in all cases.  daemon mode improvements for connect_switch,
          inet6to4, ultravnc_repeater.pl.  Dynamic change of -clip do
          not create new fb if WxH is unchanged.

2010-02-22  Karl Runge <runge@karlrunge.com>
        * classes/ssl: Java SSL applet viewer now works with certificate
          chains.
        * x11vnc: Printout option -sslScripts.  Suggest -auth guess
          in error message.  Set fake_screen width and height.  Test
          for +kb in Xvfb.

2010-01-02  Karl Runge <runge@karlrunge.com>
        * x11vnc: small tweaks to Xdummy, rx11vnc*.  Apply
          SMALL_FOOTPRINT to -appshare text.  Copyright year change.

2009-12-29  Karl Runge <runge@karlrunge.com>
        * x11vnc: rename -create_x to -create_xsrv.  Hopefully
          done fixing Xdummy.

2009-12-28  Karl Runge <runge@karlrunge.com>
        * x11vnc: Fix problems in --without-x builds.  Fix crash
          with -QD query for dbus info.  Adjust window size for
          small screens in -gui.  Improve F1 help for xdm, etc.
          include ssvnc 1.0.25 source.

2009-12-24  Karl Runge <runge@karlrunge.com>
        * x11vnc: prepare_x11vnc_dist.sh for 0.9.10. -xdummy_xvfb,
          -svc_xdummy_xvfb and -create_x shorthand. lxde session.
          Xdummy improvements and root no longer required.

---

### Post by war59312 on 2011-01-02
Bump.

Anyone have a trusted x11vnc PPA ?

---

