---
title: "Dota 2 &amp; Portal 2 crash with Bumblebee"
date: 2014-04-04
forum: Ubuntu Development Version
---

### Post by jmmL on 2014-04-04
At some point in the last week one of the updates has made Dota 2 crash when using bumblebee. Has anyone else experienced the same thing?

Just using Intel's GPU works fine (but obviously frame-rates are awful). I think the relevant bit of the output of the terminal is: 

```

ERROR: ld.so: object '/home/jmml/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/home/jmml/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/home/jmml/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/home/jmml/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/home/jmml/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
pid 3123 != 3113, skipping destruction (fork without exec?)
ERROR: ld.so: object '/home/jmml/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/home/jmml/Steam/ubuntu12_64/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS64): ignored.
Using breakpad crash handler
Setting breakpad minidump AppID = 570
Forcing breakpad minidump interfaces to load
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Steam_SetMinidumpSteamID:  Caching Steam ID:  76561197996440674 [API loaded yes]
Steam_SetMinidumpSteamID:  Setting Steam ID:  76561197996440674
SDL video target is 'x11'
SDL failed to create GL compatibility profile (whichProfile=0!
This system supports the OpenGL extension GL_EXT_framebuffer_object.
This system supports the OpenGL extension GL_EXT_framebuffer_blit.
This system supports the OpenGL extension GL_EXT_framebuffer_multisample.
This system DOES NOT support the OpenGL extension GL_APPLE_fence.
This system supports the OpenGL extension GL_NV_fence.
This system supports the OpenGL extension GL_ARB_sync.
This system supports the OpenGL extension GL_EXT_draw_buffers2.
This system supports the OpenGL extension GL_EXT_bindable_uniform.
This system DOES NOT support the OpenGL extension GL_APPLE_flush_buffer_range.
This system supports the OpenGL extension GL_ARB_map_buffer_range.
This system supports the OpenGL extension GL_ARB_vertex_buffer_object.
This system supports the OpenGL extension GL_ARB_occlusion_query.
This system DOES NOT support the OpenGL extension GL_APPLE_texture_range.
This system DOES NOT support the OpenGL extension GL_APPLE_client_storage.
This system DOES NOT support the OpenGL extension GL_ARB_uniform_buffer.
This system supports the OpenGL extension GL_ARB_vertex_array_bgra.
This system supports the OpenGL extension GL_EXT_vertex_array_bgra.
This system supports the OpenGL extension GL_ARB_framebuffer_object.
This system DOES NOT support the OpenGL extension GL_GREMEDY_string_marker.
This system supports the OpenGL extension GL_ARB_debug_output.
This system supports the OpenGL extension GL_EXT_direct_state_access.
This system supports the OpenGL extension GL_NV_bindless_texture.
This system DOES NOT support the OpenGL extension GL_AMD_pinned_memory.
This system supports the OpenGL extension GL_EXT_framebuffer_multisample_blit_scaled.
This system supports the OpenGL extension GL_EXT_texture_sRGB_decode.
This system supports the OpenGL extension GL_NVX_gpu_memory_info.
This system DOES NOT support the OpenGL extension GL_ATI_meminfo.
This system supports the OpenGL extension GL_EXT_texture_compression_s3tc.
This system supports the OpenGL extension GL_EXT_texture_compression_dxt1.
This system DOES NOT support the OpenGL extension GL_ANGLE_texture_compression_dxt3.
This system DOES NOT support the OpenGL extension GL_ANGLE_texture_compression_dxt5.
This system DOES NOT support the OpenGL extension GLX_EXT_swap_control_tear.
GL_NV_bindless_texture: DISABLED
GL_AMD_pinned_memory: DISABLED
GL_EXT_texture_sRGB_decode: AVAILABLE
GL_NVX_gpu_memory_info: AVAILABLE
GL_ATI_meminfo: UNAVAILABLE
GL_NVX_gpu_memory_info: Total Dedicated: 2097152, Total Avail: 2097152, Current Avail: 2080232
GL_MAX_SAMPLES_EXT: 32
Adding VPK file: /home/jmml/Steam/SteamApps/common/dota 2 beta/dota/sound_vo_english
Adding VPK file: /home/jmml/Steam/SteamApps/common/dota 2 beta/dota/pak01
Adding VPK file: /home/jmml/Steam/SteamApps/common/dota 2 beta/platform/pak01
Did not detect any valid joysticks.
WARNING: unable to link Test_StartScript and Test_StartScript because one or more is a ConCommand.
WARNING: unable to link Test_RandomChance and Test_RandomChance because one or more is a ConCommand.
WARNING: unable to link Test_LoopForNumSeconds and Test_LoopForNumSeconds because one or more is a ConCommand.
WARNING: unable to link Test_Loop and Test_Loop because one or more is a ConCommand.
WARNING: unable to link Test_LoopCount and Test_LoopCount because one or more is a ConCommand.
WARNING: unable to link Test_StartLoop and Test_StartLoop because one or more is a ConCommand.
WARNING: unable to link log_flags and log_flags because one or more is a ConCommand.
WARNING: unable to link log_color and log_color because one or more is a ConCommand.
WARNING: unable to link log_verbosity and log_verbosity because one or more is a ConCommand.
WARNING: unable to link log_level and log_level because one or more is a ConCommand.
WARNING: unable to link log_dumpchannels and log_dumpchannels because one or more is a ConCommand.
Load a scaleform font provider?
Creating D3D9 device with D3DCREATE_MULTITHREADED
IDirect3DDevice9::Create: BackBufWidth: 1920, BackBufHeight: 1080, D3DFMT: 3, BackBufCount: 1, MultisampleType: 0, MultisampleQuality: 0
GL sampler object usage: DISABLED

 ##### swap interval = 0     swap limit = 1 #####
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  15 (X_QueryTree)
  Resource id in failed request:  0x20000a
  Serial number of failed request:  131
  Current serial number in output stream:  131
```

The full output is here: [http://pastebin.com/aRd7GVv8](http://pastebin.com/aRd7GVv8)

If anyone could lend a hand I'd much appreciate it!

---

### Post by 23dornot23d on 2014-04-04
The full output is here: [http://pastebin.com/aRd7GVv8](http://pastebin.com/aRd7GVv8)

Not sure - but the first two errors that come up in pastebin seem to point to modules not loading up

and a search on them shows that other people are having all sorts of problems with the same two modules not loading

but I always start with the first errors I see - as often ones succeeding them can be caused from initial problems but steam

is something I have never run or tried - maybe the steam forums have some help on this ..........

I did a search to see what I could find on those first two errors - [https://www.google.co.uk/search?client=ubuntu&channel=fs&q=Gtk-Message:+Failed+to+load+module+%22overlay-scrollbar%22+Gtk-Message:+Failed+to+load+module+%22unity-gtk-module%22&ie=utf-8&oe=utf-8&gfe_rd=cr&ei=ISo_U7S_KIna4wa_nIGgCA&gws_rd=cr#channel=fs&q=Gtk-Message%3A+Failed+to+load+module+%22overlay-scrollbar%22+Gtk-Message%3A+Failed+to+load+module+%22unity-gtk-module%22&start=10](https://www.google.co.uk/search?client=ubuntu&channel=fs&q=Gtk-Message:+Failed+to+load+module+%22overlay-scrollbar%22+Gtk-Message:+Failed+to+load+module+%22unity-gtk-module%22&ie=utf-8&oe=utf-8&gfe_rd=cr&ei=ISo_U7S_KIna4wa_nIGgCA&gws_rd=cr#channel=fs&q=Gtk-Message%3A+Failed+to+load+module+%22overlay-scrollbar%22+Gtk-Message%3A+Failed+to+load+module+%22unity-gtk-module%22&start=10)

Seems to be to do with some support being dropped ...... reading some of the reports .....

But not sure if this pastebin is trying to give people a answer or not ........ [http://pastebin.com/zzWRNB3T](http://pastebin.com/zzWRNB3T)

Probably only Paper trails .... until someone else spots this thread that used steam or understands what is going on here .....

---

### Post by jmmL on 2014-04-04
I'm reasonably sure that the gtk-message and the (numerous) LIBDBUSMENU-GLIB-WARNING errors aren't to do with the crash - I've seen them before when running steam in a terminal.

I feel like this part of the log might be where the crash lies, but I'm really not sure
```

X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  15 (X_QueryTree)
  Resource id in failed request:  0x20000a
  Serial number of failed request:  131
  Current serial number in output stream:  131
*** ConVar "mat_displacementmap" was not unregistered! Shutdown crash imminent!

```

---

### Post by 23dornot23d on 2014-04-04
Searched on the part you think may be the problem and found this [http://askubuntu.com/questions/146656/cant-run-assault-cube](http://askubuntu.com/questions/146656/cant-run-assault-cube)

its old 2012 but it may give some clues as to what might be causing that error

> 
Serial number of failed request:  131


some information points to re-installation of bumblebee if you recently did a kernel upgrade .......

Also that then led to checking the bumblebee conf files out ......... which are in this directory ........

> 
keith@keith-laptop:~$ cd /etc/bumblebee/
keith@keith-laptop:/etc/bumblebee$ ls
bumblebee.conf  xorg.conf.d  xorg.conf.nouveau  xorg.conf.nvidia



---

### Post by jmmL on 2014-04-05
I've reinstalled bumblebee, but unfortunately that didn't seem to do anything.

I also can't see anything untoward in /etc/bumblebee.

Running "optirun glxspheres64" works as intended, but not Dota or Portal.

---

### Post by 23dornot23d on 2014-04-05
Running all the different commands I can find to see what the differences are as I see on one of the sites you mention
to use different methods to run their own commands.

I actually just upgraded my 64 bit Asus using this blog and am getting good results ....

[http://mylinuxexplore.blogspot.fr/2014/03/solved-nvidia-cant-access-secondary-gpu.html](http://mylinuxexplore.blogspot.fr/2014/03/solved-nvidia-cant-access-secondary-gpu.html)

Seeing optirun is working ...... giving different framerates on my own system - but I am not using the virualgl package yet ......... 
which is what I am going to try next but have made a backup of my system ......... before hand.
This you must have installed as its the one that has the glxspheres test in one of its directories.

Update - video showing it running - and it seems good -  [http://youtu.be/tSLee4Nf4xE](http://youtu.be/tSLee4Nf4xE)

Big differences now in frame rates .......

```

keith@keith-K53SV:~$ PRIMUS_UPLOAD=2 primusrun glxspheres64
Polygons in scene: 62464
Visual ID of window: 0x20
Context is Direct
OpenGL Renderer: GeForce GT 540M/PCIe/SSE2
61.748680 frames/sec - 54.669811 Mpixels/sec
59.837549 frames/sec - 52.977772 Mpixels/sec
59.833466 frames/sec - 52.974157 Mpixels/sec
59.755219 frames/sec - 52.904881 Mpixels/sec
59.910755 frames/sec - 53.042586 Mpixels/sec
keith@keith-K53SV:~$ optirun glxspheres64
Polygons in scene: 62464
Visual ID of window: 0x20
Context is Direct
OpenGL Renderer: GeForce GT 540M/PCIe/SSE2
126.303422 frames/sec - 111.823998 Mpixels/sec
121.698474 frames/sec - 107.746961 Mpixels/sec
120.531802 frames/sec - 106.714036 Mpixels/sec
132.536913 frames/sec - 117.342881 Mpixels/sec
keith@keith-K53SV:~$ 


```

Not sure now if the game is the problem - as bumblebee seems to be working well ........ it comes down to how
all the things interact with each other - the game / bumblebee / the graphics setup that uses the onboard Nvidia chip and how
it addresses it I guess ........ but the test works ok so - does that not point the error to being with the game setup or configuration.

Maybe try different configs .... or prefix options for it - see if you get any differences ....... maybe if you do then that will point to
what might be wrong here ..........

____________________________________________________

The games themselves I cannot test - because I do not login to these games sites - personal preference as I find games are just distractions.

Have you tried using any of the different options / prefixes and if so which ones .......... some put the game in its own window or use different
rendering methods from what I can tell ........

( Not messed with games online - so this is all new to me .... )

But I am finding there are many different ways to configure and run them also there are some settings in bumblebee
one I just followed precisely here and my own system seems to be working better - but I cannot switch solely into
the faster graphics mode.

 ......... running primus and optirun seems to use the better speeds by using the faster graphics chip
from what I have read and then renders it faster in virtual frames 

The errors below are just as I exit the tests ........ 

```

keith@keith-K53SV:~$ PRIMUS_UPLOAD=2 primusrun glxgears
300 frames in 5.0 seconds = 59.902 FPS
300 frames in 5.0 seconds = 59.847 FPS
300 frames in 5.0 seconds = 59.858 FPS
primus: warning: dropping a frame to avoid deadlock
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
      after 37 requests (37 known processed) with 0 events remaining.
primus: warning: dropping a frame to avoid deadlock
primus: warning: timeout waiting for display worker
keith@keith-K53SV:~$ primusrun glxgears
293 frames in 5.0 seconds = 58.414 FPS
300 frames in 5.0 seconds = 59.861 FPS
300 frames in 5.0 seconds = 59.849 FPS
primus: warning: dropping a frame to avoid deadlock
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
      after 37 requests (37 known processed) with 0 events remaining.
primus: warning: dropping a frame to avoid deadlock
primus: warning: timeout waiting for display worker
keith@keith-K53SV:~$ optirun glxgears
293 frames in 5.0 seconds = 58.497 FPS
300 frames in 5.0 seconds = 59.857 FPS
300 frames in 5.0 seconds = 59.857 FPS
primus: warning: dropping a frame to avoid deadlock
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
      after 37 requests (37 known processed) with 0 events remaining.
primus: warning: dropping a frame to avoid deadlock
primus: warning: timeout waiting for display worker
keith@keith-K53SV:~$ 


```

Search I did was here and have looked at many setups now ....... how we determine whether its the games that are causing the errors
or the setup of bumblebee or something to do with the graphics setup in Ubuntu is the thing to track down .

[https://www.google.co.uk/search?client=ubuntu&channel=fs&q=optirun+-b+primus&ie=utf-8&oe=utf-8&gl=uk&gws_rd=cr&q=optirun+-b+primus+2014&start=10](https://www.google.co.uk/search?client=ubuntu&channel=fs&q=optirun+-b+primus&ie=utf-8&oe=utf-8&gl=uk&gws_rd=cr&q=optirun+-b+primus+2014&start=10)

Your error message is the thing to track down and work out what fires that error up ....... the game or something else.

Seems its in a window and crashes out of it ........ but maybe something happens previous to this to cause it to do it ........

Maybe its the Font ........ 
( I know in Windows if the Fonts are not there then often the software just crashes out - often I just got across to Windows and grab their full Font directory
   and add it so that some programs will run - that others cannot get to run ) ..... but thats in wine .......

```

[COLOR=#ff0000]**Load a scaleform font provider?**[/COLOR]

Creating D3D9 device with D3DCREATE_MULTITHREADED
IDirect3DDevice9::Create: BackBufWidth: 1920,  BackBufHeight: 1080, D3DFMT: 3, BackBufCount: 1, MultisampleType: 0,  MultisampleQuality: 0
[COLOR=#ff0000]**GL sampler object usage: DISABLED**[/COLOR]

 
 ##### swap interval = 0     swap limit = 1 #####
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  15 (X_QueryTree)
  Resource id in failed request:  0x20000a
  Serial number of failed request:  131
  Current serial number in output stream:  131


```

What upgrades have occured - I see one of the games upgraded its system - but its hard to tell what it did as its own forums mainly talk about
games - but not a lot on the upgrades or problems encountered .......

Will leave this at the end so others can see what it is you think is causing the problem .... but there is the full text too to the pastbin you did 

so will put that here too ........ [http://pastebin.com/aRd7GVv8](http://pastebin.com/aRd7GVv8)



```

X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  15 (X_QueryTree)
  Resource id in failed request:  0x20000a
  Serial number of failed request:  131
  Current serial number in output stream:  131
*** ConVar "mat_displacementmap" was not unregistered! Shutdown crash imminent!

```

---

