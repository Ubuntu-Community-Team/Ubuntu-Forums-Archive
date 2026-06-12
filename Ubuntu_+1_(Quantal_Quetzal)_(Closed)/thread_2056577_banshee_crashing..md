---
title: "banshee crashing."
date: 2012-09-11
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by humanisfood on 2012-09-11
banshee is crashing. anyone else having this issue?

```
damien@damien-GA-770TA-UD3:~$ banshee
[Info  17:59:54.680] Running Banshee 2.4.1: [Ubuntu quantal (development branch) (linux-gnu, x86_64) @ 2012-09-11 17:12:51 UTC]
[Info  17:59:55.525] Updating web proxy from GConf
[Info  17:59:55.645] All services are started 0.777137
[Info  17:59:56.200] AmazonMP3 store redirect URL: [https://one.ubuntu.com/music/store/amz/](https://one.ubuntu.com/music/store/amz/)
[Info  17:59:56.808] nereid Client Started
[Info  17:59:56.902] GStreamer version 0.10.36.0, gapless: True, replaygain: False
[Info  18:00:06.062] Uncached artwork size 175 requested
Stacktrace:

  at (wrapper managed-to-native) Gtk.Application.gtk_main () <0xffffffff>
  at Gtk.Application.Run () <0x0000b>
  at Banshee.Gui.GtkBaseClient.Run () <0x0005f>
  at Banshee.Gui.GtkBaseClient.Startup () <0x00049>
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.CleanRoomStartup/StartupInvocationHandler) <0x0008e>
  at Banshee.Gui.GtkBaseClient.Startup<T> () <0x0006b>
  at Banshee.Gui.GtkBaseClient.Startup<T> (string[]) <0x000ff>
  at Nereid.Client.Main (string[]) <0x00017>
  at (wrapper runtime-invoke) <Module>.runtime_invoke_void_object (object,intptr,intptr,intptr) <0xffffffff>
  at (wrapper managed-to-native) System.AppDomain.ExecuteAssembly (System.AppDomain,System.Reflection.Assembly,string[]) <0xffffffff>
  at System.AppDomain.ExecuteAssemblyInternal (System.Reflection.Assembly,string[]) <0x00047>
  at System.AppDomain.ExecuteAssembly (string,System.Security.Policy.Evidence,string[]) <0x00037>
  at (wrapper remoting-invoke-with-check) System.AppDomain.ExecuteAssembly (string,System.Security.Policy.Evidence,string[]) <0xffffffff>
  at System.AppDomain.ExecuteAssembly (string) <0x0001f>
  at (wrapper remoting-invoke-with-check) System.AppDomain.ExecuteAssembly (string) <0xffffffff>
  at Booter.Booter.BootClient (string) <0x0006b>
  at Booter.Booter.Main () <0x001db>
  at (wrapper runtime-invoke) object.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

[Warn  18:00:21.270] Could not read GConf key sources.MusicLibrarySource-Library.current_filters - System.NullReferenceException: Object reference not set to an instance of an object (in `gconf-sharp')
  at (wrapper managed-to-native) GConf.Client:gconf_client_get (intptr,string,intptr&)
  at GConf.Client.Get (System.String key) [0x00000] in <filename unknown>:0 
  at Banshee.GnomeBackend.GConfConfigurationClient.TryGet[String[]] (System.String namespace, System.String key, System.String[]& result) [0x00000] in <filename unknown>:0 
    banshee() [0x4961e9]
    banshee() [0x4e6d1f]
    banshee() [0x41dcb7]
    /lib/x86_64-linux-gnu/libpthread.so.0(+0xfcb0) [0x7f3ec5f7dcb0]
    /lib/x86_64-linux-gnu/libdbus-1.so.3(+0x26d1c) [0x7f3eb5ec1d1c]
    /lib/x86_64-linux-gnu/libdbus-1.so.3(+0x26d89) [0x7f3eb5ec1d89]
    /lib/x86_64-linux-gnu/libdbus-1.so.3(+0x26fda) [0x7f3eb5ec1fda]
    /lib/x86_64-linux-gnu/libdbus-1.so.3(+0x1595a) [0x7f3eb5eb095a]
    /lib/x86_64-linux-gnu/libdbus-1.so.3(+0x15dd8) [0x7f3eb5eb0dd8]
    /lib/x86_64-linux-gnu/libdbus-1.so.3(+0x15cec) [0x7f3eb5eb0cec]
    /lib/x86_64-linux-gnu/libdbus-1.so.3(+0x161de) [0x7f3eb5eb11de]
    /lib/x86_64-linux-gnu/libdbus-1.so.3(+0x162ed) [0x7f3eb5eb12ed]
    /lib/x86_64-linux-gnu/libdbus-1.so.3(+0x131b8) [0x7f3eb5eae1b8]
    /lib/x86_64-linux-gnu/libdbus-1.so.3(+0x1aeae) [0x7f3eb5eb5eae]
    /lib/x86_64-linux-gnu/libdbus-1.so.3(+0x23282) [0x7f3eb5ebe282]
    /lib/x86_64-linux-gnu/libdbus-1.so.3(+0x233b3) [0x7f3eb5ebe3b3]
    /lib/x86_64-linux-gnu/libdbus-1.so.3(+0xb794) [0x7f3eb5ea6794]
    /lib/x86_64-linux-gnu/libdbus-1.so.3(dbus_connection_get_dispatch_status+0x2e) [0x7f3eb5ea731e]
    /usr/lib/x86_64-linux-gnu/libdbus-glib-1.so.2(+0xac53) [0x7f3eb60e9c53]
    /lib/x86_64-linux-gnu/libglib-2.0.so.0(g_main_context_prepare+0x168) [0x7f3ec2a4c678]
    /lib/x86_64-linux-gnu/libglib-2.0.so.0(+0x47d0b) [0x7f3ec2a4cd0b]
    /lib/x86_64-linux-gnu/libglib-2.0.so.0(g_main_loop_run+0x72) [0x7f3ec2a4d242]
    /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0(gtk_main+0xa7) [0x7f3eb9294df7]
    [0x41727c45]

Debug info from gdb:

Could not attach to process.  If your uid matches the uid of the target
process, check the setting of /proc/sys/kernel/yama/ptrace_scope, or try
again as the root user.  For more details, see /etc/sysctl.d/10-ptrace.conf
ptrace: Operation not permitted.
No threads.

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted (core dumped)
```

---

### Post by jpeddicord on 2012-09-11
It has been crashing for me for the past few weeks, and I've been unable to pinpoint the cause. Sometimes it is at startup, sometimes when changing songs, and sometimes just out of the blue. The stacktraces I get (or don't get) seem different every time.

There are a few bugs open on Launchpad, but I'm not really sure which one is a good master. Going to try some digging tonight and see if there is something easy to reproduce.

---

### Post by mc4man on 2012-09-11
Happens here also, most typically first time in a session though not limited to that.

Banshee.exe crashed with SIGSEGV in dbus_connection_send_with_reply_and_block()

(will see what shows after a retrace

---

### Post by VinDSL on 2012-09-11
> **humanisfood said:**
> banshee is crashing. anyone else having this issue?
> **jpeddicord said:**
> It has been crashing for me for the past few weeks, and I've been unable to pinpoint the cause.
Dittos!

Hold on...

Okay, Banshee is working, at the moment, in GS 3.5.91-1

Here's a dump:

```
exec -a banshee mono  /usr/lib/banshee/Banshee.exe    --redirect-log --play-enqueued

[Info  15:58:25.885] Running Banshee 2.4.1: [Ubuntu quantal (development branch) (linux-gnu, i686) @ 2012-07-06 14:13:32 UTC]
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configurations from ~/.fonts.conf is deprecated.
[Info  15:58:37.356] Updating web proxy from GConf
[Info  15:58:37.671] All services are started 8.792906
[Info  15:58:40.062] nereid Client Started
[Info  15:58:40.523] GStreamer version 0.10.36.0, gapless: False, replaygain: False
Abort Download Error:  Invalid parameter
Full thread dump:

"Threadpool worker" tid=0x0xa83f9b40 this=0x0xfb4dc8 thread handle 0x785 state : interrupted state owns ()

"HyenaSqliteConnection (/home/vindsl/.config/banshee-1/banshee.db)" tid=0x0xb3b95b40 this=0x0x563f0 thread handle 0x414 state : interrupted state owns ()
  at (wrapper managed-to-native) System.Threading.WaitHandle.WaitOne_internal (System.Threading.WaitHandle,intptr,int,bool) <0xffffffff>
  at System.Threading.WaitHandle.WaitOne () <0x0005f>
  at Hyena.Data.Sqlite.HyenaSqliteConnection.ProcessQueue () <0x00231>
  at System.Threading.Thread.StartInternal () <0x00057>
  at (wrapper runtime-invoke) object.runtime_invoke_void__this__ (object,intptr,intptr,intptr) <0xffffffff>

"Threadpool worker" tid=0x0xa8061b40 this=0x0x4aa5e8 thread handle 0x6e9 state : interrupted state owns ()

"IO Threadpool worker" tid=0x0xa851bb40 this=0x0x3e42a0 thread handle 0x68d state : interrupted state owns ()

"<threadpool thread>" tid=0x0xa853cb40 this=0x0x3e4348 thread handle 0x68c state : interrupted state owns ()

"Threadpool worker" tid=0x0xa8b4eb40 this=0x0x1bc9d8 thread handle 0x640 state : interrupted state owns ()
  at (wrapper managed-to-native) System.Threading.WaitHandle.WaitAny_internal (System.Threading.WaitHandle[],int,bool) <0xffffffff>
  at System.Threading.WaitHandle.WaitAny (System.Threading.WaitHandle[],System.TimeSpan,bool) <0x00103>
  at System.Threading.RegisteredWaitHandle.Wait (object) <0x000a7>
  at (wrapper runtime-invoke) <Module>.runtime_invoke_void__this___object (object,intptr,intptr,intptr) <0xffffffff>
```

Guess I run Banshee until it crashes, and report back.

Heh!  "A watched pot never boils," right?  :D

---

### Post by VinDSL on 2012-09-11
> **mc4man said:**
> (will see what shows after a retrace
You probably already know this, but...

I'll toss this out there, for general consumption. ;)

SOURCE:  [http://banshee.fm/contribute/file-bugs/](http://banshee.fm/contribute/file-bugs/)
> If your bug involves unexpected behavior, a crash, or an error of any kind, it's a good idea to attach the Banshee log to the bug you file. To get this log file, please follow the instructions for your operating system.

On Linux and Mac OS X, open a terminal and run this command:
```
kill -s QUIT $(pidof banshee); cp ~/.config/banshee-1/log ~/Desktop/banshee.log
```
and attach the banshee.log file that is now on your Desktop. The kill -s QUIT part of that command doesn't actually close Banshee; it tells Banshee to output more information useful for debugging.

Handy diagnostic tool...

---

### Post by mc4man on 2012-09-11
Looks like this bug which should have some new packages shortly
[https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/1048341](https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/1048341)
( gconf packages

---

### Post by VinDSL on 2012-09-11
> **mc4man said:**
> Looks like this bug which should have some new packages shortly[...]
Banshee didn't crash, for me, but it started using 100% CPU, twice.

When this happens, the only thing you can do is killall Banshee, and restart it.

For giggles, I installed the "hyperair PPA" fixes, and restarted.

So far, so good.  Nice find! ;)

---

### Post by mc4man on 2012-09-11
> **VinDSL said:**
> Banshee didn't crash, for me, but it started using 100% CPU, twice.

When this happens, the only thing you can do is killall Banshee, and restart it.

For giggles, I installed the "hyperair PPA" fixes, and restarted.

So far, so good.  Nice find! ;)
The one thing Mr. Jin (hyperair) did that's a bit weird is he versioned his test ppa packages higher than what the fix released are packages are.
So Ubuntu repos has published the new ones @ 3.2.5-0ubuntu3, the testers are 3.2.5-0ubuntu3~ppa1
No big deal but still...

---

### Post by VinDSL on 2012-09-11
Yep!

Example...
```
vindsl@Zuul:~$ apt-cache policy gconf2
gconf2:
  Installed: 3.2.5-0ubuntu3~ppa1
  Candidate: 3.2.5-0ubuntu3~ppa1
  Version table:
 *** 3.2.5-0ubuntu3~ppa1 0
        500 http://ppa.launchpad.net/hyperair/test-11048341-fix/ubuntu/ quantal/main i386 Packages
        100 /var/lib/dpkg/status
     3.2.5-0ubuntu2 0
        500 http://mirrors.se.eu.kernel.org/ubuntu/ quantal/main i386 Packages
vindsl@Zuul:~$ 

```

Is Banshee working for you?

Working great here...

---

### Post by mc4man on 2012-09-11
> **VinDSL said:**
> Yep!

Example...
```
vindsl@Zuul:~$ apt-cache policy gconf2
gconf2:
  Installed: 3.2.5-0ubuntu3~ppa1
  Candidate: 3.2.5-0ubuntu3~ppa1
  Version table:
 *** 3.2.5-0ubuntu3~ppa1 0
        500 http://ppa.launchpad.net/hyperair/test-11048341-fix/ubuntu/ quantal/main i386 Packages
        100 /var/lib/dpkg/status
     3.2.5-0ubuntu2 0
        500 http://mirrors.se.eu.kernel.org/ubuntu/ quantal/main i386 Packages
vindsl@Zuul:~$ 

```

Is Banshee working for you?

Working great here...
Yeah, works fine - nice to have a psuedo default player that know how to get album art ect on a relatively consistent basis.

---

### Post by VinDSL on 2012-09-11
> **mc4man said:**
> Yeah, works fine - nice to have a psuedo default player that know how to get album art ect on a relatively consistent basis.
Agreed!

I like Banshee just fine, but I find myself using Guayadeque more, these days.

I had another "China Syndrome" event.  This time I was watching closely, and it happened when Banshee was auto-downloading a podcast.

CPU usage climbed n' climbed until my meter was pegged @ 100% on both cores.  Banshee playback started stumbling, and the whole machine became unresponsive.  Still, it didn't crash...

I'm testing it again, as I type.  I judge that I'm safe, until it downloads another podcast.  :)

---

### Post by humanisfood on 2012-09-12
kept up with all the updates and banshee is working great now. yesterday a bunch of pulseaudio updates showed up. perhaps that did the trick.

---

### Post by thotz on 2012-09-19
Yes I had also crashes, but for now everything is fine :)

---

