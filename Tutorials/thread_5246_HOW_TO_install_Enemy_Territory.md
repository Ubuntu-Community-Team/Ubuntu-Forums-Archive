---
title: "HOW TO: install Enemy Territory"
date: 2004-11-16
forum: Tutorials
---

### Post by nehalem on 2004-11-16
**First, Install the Nvidia or ATI driver:**

Here is Ubuntu's instructions - [http://wiki.ubuntulinux.org/BinaryDriverHowto](http://wiki.ubuntulinux.org/BinaryDriverHowto) 
More info on installing the ATI driver [here](http://ubuntuforums.org/showthread.php?t=3567) 

**Second, download and install the game:**
I went to fileshack.com personally but there is a lot of places.

To install go to Applications->System Tools->Root Terminal
Navigate to wherever you downloaded the file.
Simply run the file (*./et-linux-2.56-2.x86.run*)
and it should bring up a GUI to help you through the process.  I pretty much kept everything as default (by default PB is selected, keep this intact since you can't join a lot of servers without it).

Installed!

Simply type "et" from the command line to launch.  Also the games section on your Applications Menu should have Enemy Territory as well (I had to log out for it to take effect)

**Troubleshooting**
_Sound Issues_
I found that sound did not work for my setup, giving me the following error:
*/dev/dsp: Input/output error Could not mmap /dev/dsp*
To resolve this issue I simply typed from root terminal the following:
*echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss*
For more info on this click [here](http://alsa.opensrc.org/index.php?page=FAQ023) 

_Permission Errors:_ 
Use this command:
[I]chmod +x et-linux-2.56-2.x86.run
su -c "./et-linux-2.56-2.x86.run"[/I]
Thanks Ichabob

**Final Words**
This is not by any means comprehensive.  It would be nice to have common commands that are useful as well as more troubleshooting tips (since I didn't have any other problems I can't really help here) since I'm sure there exists a lot more common issues.  Please post anything here and I'll try to make the necessary changes to this post so the most up-to-date and correct info is on the first post.

Thanks.

P.S. - With my 9800 Pro I was able to play this game perfectly so even with the inferior ATI drivers so just about anyone should be able to enjoy this game.  Have Fun!

---

### Post by DaGr8Gatzby on 2004-11-16
Hey I installed Quake 3 Arena Today but it stops at Sound Initialization in the console....any ideas?

---

### Post by IchaBOB on 2004-11-24
[QUOTE=nehalem]

**Second, download and install the game:**
I went to fileshack.com personally but there is a lot of places.

To install go to Applications->System Tools->Root Terminal
Navigate to wherever you downloaded the file.
Simply run the file (*./et-linux-2.56-2.x86.run*)
and it should bring up a GUI to help you through the process.[/QUOTE]


When I try and run it through the ROOT Terminal, I get permission denied... 
any tips?
Thx

---

### Post by IchaBOB on 2004-11-24
chmod +x et-linux-2.56-2.x86.run
 su -c "./et-linux-2.56-2.x86.run"

---

### Post by easy_target on 2004-12-06
Okay I tried to install this way but I could only get a "permission denied" message. So I tried installing it with sudo and it did everything fine (I think it installed the game under /usr/games/et)
It runs fine but with no sounds!! I tried the echo parameter but it didn't work either. I tried running it as super user and everything works fine again. 
What should I do? It bothers me having this game running as super user. Are there any problems security-wise? Please give me some advice.

Thanks in advance Ubuntu Community!

---

### Post by nehalem on 2004-12-07
Well I don't wouldn't worry too much about it security wise but I can understand the annoyance.  When you try to run it as your user, in the terminal, what does it say?  I'm  sure it will give some error on the CLI that should point us in the right direction (it may be as simply as giving your user access to certain files).

---

### Post by easy_target on 2004-12-11
I still have to play the game as super user if I want the maps to be downloaded automatically. My sound works fine. I can't produce a desktop link on the applications menu without braking the sound. What's the problem? Heeeellllppppp!!!!!  :-(

---

### Post by nehalem on 2004-12-12
Ok, I think I can give some insight:
_Sound_ 
I can't start hardly any games from the menu with sound.  As far as I can tell it's when you start an application the system plays it's sound, using the device and thus the game when starting cant' access the sound device.  This is only a limitation generally on on board sound, does this describe your setup?

_Downloading Maps_ 
Have you verified that the directory that it downloads maps to is chmoded for access by your user?

---

### Post by Tonio on 2004-12-19
Hello,

I download it from fileshack.com, done as you said, but got this : 

```
root@ubuntu:/mnt/atchoum/Softs/linux # ls -l | grep et
-rwxr-xr-x    1 tonio    tonio    30920500 2004-12-19 16:52 et-linux-2.56-2.x86.run
root@ubuntu:/mnt/atchoum/Softs/linux # ./et-linux-2.56-2.x86.run
bash: ./et-linux-2.56-2.x86.run: /bin/sh: bad interpreter: Permission non accordée
root@ubuntu:/mnt/atchoum/Softs/linux # su -c "./et-linux-2.56-2.x86.run"
bash: ./et-linux-2.56-2.x86.run: /bin/sh: bad interpreter: Permission non accordée
root@ubuntu:/mnt/atchoum/Softs/linux #
``` 

Any idea?

PS:Sorry for english, I don't speak very well.

---

### Post by Ste on 2004-12-19
[QUOTE=Tonio]Hello,

I download it from fileshack.com, done as you said, but got this : 

```
root@ubuntu:/mnt/atchoum/Softs/linux # ls -l | grep et
-rwxr-xr-x    1 tonio    tonio    30920500 2004-12-19 16:52 et-linux-2.56-2.x86.run
root@ubuntu:/mnt/atchoum/Softs/linux # ./et-linux-2.56-2.x86.run
bash: ./et-linux-2.56-2.x86.run: /bin/sh: bad interpreter: Permission non accordée
root@ubuntu:/mnt/atchoum/Softs/linux # su -c "./et-linux-2.56-2.x86.run"
bash: ./et-linux-2.56-2.x86.run: /bin/sh: bad interpreter: Permission non accordée
root@ubuntu:/mnt/atchoum/Softs/linux #
``` 

Any idea?

PS:Sorry for english, I don't speak very well.[/QUOTE]
 Permission Errors:
Use this command:
chmod +x et-linux-2.56-2.x86.run
su -c "./et-linux-2.56-2.x86.run"

Did you follow this step ?

---

### Post by Tonio on 2004-12-19
Yep, I follow this step, as you can read in my previous message.

I think : */bin/sh: bad interpreter* is the important part of the error message, but I don't know what to do.

---

### Post by AlvaroBF on 2004-12-26
$ sudo sh et-linux.... .run

---

### Post by headspace on 2005-03-10
I successfully installed everything, but when I go to run ET all it does is fade to black before signing me out. I have similar problems when I try running quake.

Any ideas?

---

### Post by bored2k on 2005-03-10
[QUOTE=headspace]I successfully installed everything, but when I go to run ET all it does is fade to black before signing me out. I have similar problems when I try running quake.

Any ideas?[/QUOTE]
 Video card problem? not supporting 3d on linux? If you can try Counter-Strike, you can make it use software for faster performance on non-d3d/opengl environment.

---

### Post by Nano on 2005-03-13
[QUOTE=bored2k]Video card problem? not supporting 3d on linux? If you can try Counter-Strike, you can make it use software for faster performance on non-d3d/opengl environment.[/QUOTE]
 This is amazingly addicting!
Last night we were two teams of 30 players each...

I woke up this morning thinking about it...

---

### Post by AmeTsuchi on 2005-03-13
[QUOTE=headspace]I successfully installed everything, but when I go to run ET all it does is fade to black before signing me out. I have similar problems when I try running quake.

Any ideas?[/QUOTE]

I have the exact same problem. What's odd is that ET was once working fine for me. I then tried updating to Hoary and after having some problems there did a clean install of Warty. But now, for some reason, running ET switches the video mode then kills the X server. I can't see the output of the program, so I don't know what error is being given. I'd appreciate any help with this!

Edit: nvidia is set up and glxgears reports 4134 FPS, so OpenGL must be working.

Edit2: This issue has been resolved: [http://ubuntuforums.org/showthread.php?p=93986#post93986](http://ubuntuforums.org/showthread.php?p=93986#post93986)

---

### Post by bored2k on 2005-03-13
[QUOTE=Nano]This is amazingly addicting!
Last night we were two teams of 30 players each...

I woke up this morning thinking about it...[/QUOTE]
 lol, we dont get that many people on a single server on Counter-Strike :(. Its a slow paced game and tries hard to be completely different than a no brainer shooter .

ET is good though/.

---

### Post by Chris- on 2005-03-18
```
Received signal 11, exiting...
[root@localhost chris]# Mutex destroy failure: Device or resource busy
ICE default IO error handler doing an exit(), pid = 7344, errno = 0
```

Any idea whats wrong please.

---

### Post by Chris- on 2005-03-18
[QUOTE=Chris-]```
Received signal 11, exiting...
[root@localhost chris]# Mutex destroy failure: Device or resource busy
ICE default IO error handler doing an exit(), pid = 7344, errno = 0
```

Any idea whats wrong please.[/QUOTE]

Fixed the problem.

---

### Post by Chris- on 2005-03-20
My computer keeps doing a restart while play ET, how to get ride of it please.

---

### Post by GrayFox^ on 2005-04-20
Thanks for the great installation guide. It helped me (a complete total newbie) get the install done smoothly and seamlessly. You might want to update your fisrt post to reflect the changes of an update that was released (2.60). I managed to install it by following your guide and just switching the filenames.

---

### Post by XplOzIOn on 2005-04-30
Ok my problem is about downloading maps and stuff... i did a chown -R user:user on the .../game/et but it still wont download anything... help please

---

### Post by jonascus on 2005-05-07
ok i put my nvidia video card in to my computer and then started it back up and it goes to this black screen asking me to log in so i log in thinking that it will go to the k desktop but it dosnt can anyone help me please

---

### Post by Manc on 2005-05-07
I've just installed ET on my PC and I've come across a rather annoying issue. Basically Every time ET loads I have to create a profile and it won't let me enable Punkbuster!

I installed the game as specified at the top of the thread and it worked fine

However I've just tried to play the game I can't! I think it some form of permisson issue
, I'm pretty sure there will be a work-around (or its me being a numpty) for the issue, surely I don't to install the gaeverytime I want to play  :roll: 

I'm very happy with the performance of the game,  don't get me wrong (first taste of linux gamaing). Yet I feel I'm suffering here from my lack of Linux know-how,  and my Windoze way of thinking :/

---

### Post by crane on 2005-05-07
[QUOTE=XplOzIOn]Ok my problem is about downloading maps and stuff... i did a chown -R user:user on the .../game/et but it still wont download anything... help please[/QUOTE]

Sorry, I missed this post.

You should have a hidden file called .etwolf make sure you have permission to write to this file as well as the bas install folder. Are you getting any kind of error. 

Try starting it in a terminal. Once it's running, go to a place and try to download a map (you are talking about ingame right) then shut of the game but don't close the terminal window. Now scroll back and see if you can find an error.

---

### Post by crane on 2005-05-07
[QUOTE=jonascus]ok i put my nvidia video card in to my computer and then started it back up and it goes to this black screen asking me to log in so i log in thinking that it will go to the k desktop but it dosnt can anyone help me please[/QUOTE]


You should search the forums for help. You may not get the help you need by posting in this thread. That aside.  What was your previos card? what is your driver set to? And have you installed the nvidia drivers?

---

### Post by crane on 2005-05-07
[QUOTE=Manc]I've just installed ET on my PC and I've come across a rather annoying issue. Basically Every time ET loads I have to create a profile and it won't let me enable Punkbuster!

I installed the game as specified at the top of the thread and it worked fine

However I've just tried to play the game I can't! I think it some form of permisson issue
, I'm pretty sure there will be a work-around (or its me being a numpty) for the issue, surely I don't to install the gaeverytime I want to play  :roll: 

I'm very happy with the performance of the game,  don't get me wrong (first taste of linux gamaing). Yet I feel I'm suffering here from my lack of Linux know-how,  and my Windoze way of thinking :/[/QUOTE]

What errors are you getting? Can you run/play the game using sudo command?
I know this may be a dumb question but how are you starting the game?(what command?)

---

### Post by Manc on 2005-05-08
I've been starting the game when I have problems via the shortcut in the drop-down application menu in Gnome!

If I do this again (install the game again) it works fine :/

> chmod +x et-linux-2.56-2.x86.run
su -c "./et-linux-2.56-2.x86.run" 

bit stumped  :roll:

---

### Post by kb00heda on 2005-05-08
nehalem:

Thanks for this nice howto! It worked nice for me under Hoary, the only thing being I had sound issues, both on the stationary machine and on the laptop. However, they were resolved using the tips at the link you provided. Thoughtful of you to include that one!

So... happy shooting, I guess! :)

---

### Post by crane on 2005-05-08
[QUOTE=Manc]I've been starting the game when I have problems via the shortcut in the drop-down application menu in Gnome!

If I do this again (install the game again) it works fine :/
ese
 

bit stumped  :roll:[/QUOTE]

So when you installed with
[color=blue]sh et-linux-2.56-2.x86.run[/color]
You had all the problems?

what is the -c switch for the su command do?

---

### Post by Kakalto on 2005-05-20
Hey guys,

I noticed that if I run et as my user, no sound comes out. But if I run as root, I have sound. I'm quite new to ubuntu, so could someone please tell me how to fix it?

I tried the "echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss" thing, but it didn't work.

But when I ran it as root user, then closed it, I noticed this section:

```
------- sound initialization -------
------------------------------------
----- Sound Info -----
sound system is muted
    1 stereo
32768 samples
   16 samplebits
    1 submission_chunk
44100 speed
0x0xaf3de000 dma buffer
No background file.
----------------------
Sound memory manager started
Sys_LoadDll(/root/.etwolf/etmain/ui.mp.i386.so)...
Sys_LoadDll(/root/.etwolf/etmain/ui.mp.i386.so) failed:
"/root/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xad84cf40
Sys_LoadDll(ui) succeeded!

```
Apart from the fact that "sound system is muted", it fails to load ui.mp.i386.so.

Could someone please help me?

---

### Post by strwrsxprt on 2005-05-26
How do you uninstall it?

---

### Post by quick_snack on 2005-06-14
The following lines i got when i tried to start et:
```
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x30
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
Received signal 11, exiting...
```
After that my screen was set in 800x600 mode or something and i had to change it back manually.

What could be wrong? I use a Ati Rage 128 Pro embedded video adapter.

I really would like to play  :|

---

### Post by quick_snack on 2005-06-17
bump ! no one?

---

### Post by allforcarrie on 2005-06-17
sweet.

---

### Post by allforcarrie on 2005-06-17
I am getting an  arror that it couln't connect ot a server.... WTF????

---

### Post by jago25_98 on 2005-06-30
quick_snack:

glxinfo |grep direct

---

### Post by quick_snack on 2005-07-01
Thanx. Due to an other thread I changed the colordepth of my Ati Rage 128 Pro adapter from 24 to 16. 

The outcome of your command is:
```
direct rendering: Yes
```

ET will play now but very, very slow.

---

### Post by npkamen on 2005-07-01
Hi there, I keep getting this error,

```
/dev/dsp: Input/output error
Could not mmap /dev/dsp
```


any ideas?

---

### Post by MappyH on 2005-07-01
Please Note: No need to install as Root or Sudo

download to home folder and run install as Normal user, When it asks for Root password just press cancel.

ArmericasArmy installs as normal user too  :)

---

### Post by sOnIc on 2005-07-01
Hi!

When i try to start et i got following lines:
```
root@ubuntu:~ # et
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/root/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Received signal 11, exiting...
```
After that nothing happen, any suggestions?  ](*,)
Cheers sOnIc

---

### Post by Yagisan on 2005-07-03
[QUOTE=sOnIc]Hi!

When i try to start et i got following lines:
```
root@ubuntu:~ # et
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/root/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Received signal 11, exiting...
```
After that nothing happen, any suggestions?  ](*,)
Cheers sOnIc[/QUOTE]
I got the same error to on my amd64 hoary system. I can get et to load (haven't tried playing it yet) by making the following change.
```
sudo nano /usr/local/games/enemy-territory/et
```
and adding the following line
```
export LD_ASSUME_KERNEL=2.4.2
```
right before the line that says
```
exec ./et.x86 "$@"
```

---

### Post by sOnIc on 2005-07-03
Hi, **Yagisan**

Tks, i will try it :wink:

_*EDIT*:_ Now my computer freeze when i lunch ET (black screen), suggestions?

---

### Post by Yagisan on 2005-07-03
[QUOTE=sOnIc]Hi, **Yagisan**

Tks, i will try it :wink:

_*EDIT*:_ Now my computer freeze when i lunch ET (black screen), suggestions?[/QUOTE]
Try updating punkbuster
```
cd /usr/local/games/enemy-territory/pb/
sudo chmod +x pbweb.x86
sudo ./pbweb.x86
```
delete the ~/.etwolf directory 
```
cd ~
rm -r .etwolf/
```
and then load et again.

---

### Post by sOnIc on 2005-07-04
Hi!
Yagisan tks m8!
 
EDIT: Same problem :|  nothing happen, computer freeze when i lunch ET (black screen) ](*,)

---

### Post by Yagisan on 2005-07-04
[QUOTE=sOnIc]Hi!
Yagisan tks m8!
 
EDIT: Same problem :|  nothing happen, computer freeze when i lunch ET (black screen) ](*,)[/QUOTE]
I just reread your post, are you running this as root ? you should not need to run as root.

My 14 month old daughter just caused me to have a black screen lockup too. She pressed the reset button on my router causing the Internet to become unavailable when I started up et. As a result et hung until I pressed Control+C. Make sure your Internet connection is running before starting et and let us know how it goes.

---

### Post by sOnIc on 2005-07-04
Hi!

```
sonic@ubuntu:~$ ping -c 3  google.pt
PING google.pt (216.239.59.104) 56(84) bytes of data.
64 bytes from 216.239.59.104: icmp_seq=2 ttl=239 time=234 ms
64 bytes from 216.239.59.104: icmp_seq=3 ttl=239 time=476 ms

--- google.pt ping statistics ---
3 packets transmitted, 2 received, 33% packet loss, time 2050ms
rtt min/avg/max/mdev = 234.231/355.272/476.314/121.042 ms
```

```
sonic@ubuntu:~$ et
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/sonic/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 1280x1024
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce 6600 GT/AGP/SSE2
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_NV_fog_distance
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
...using GLX_SGI_swap_control
...using GLX_SGI_video_sync
XF86 Gamma extension initialized

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce 6600 GT/AGP/SSE2
GL_VERSION: 1.5.3 NVIDIA 71.74
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_depth_bounds_test GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_vertex_array GL_HP_occlusion_test GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum
GLX_EXTENSIONS: GLX_EXT_visual_info GLX_EXT_visual_rating GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_SGI_video_sync GLX_SGI_swap_control GLX_ARB_multisample GLX_NV_float_buffer GLX_ARB_get_proc_address
GL_MAX_TEXTURE_SIZE: 4096
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU:
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------
Received signal 2, exiting...
```

Same problem :-| , black screen again :-x
I will try to install everything again step by step and post all console commands ;-)
One more time tks m8

---

### Post by Yagisan on 2005-07-04
G'day
```
------- sound initialization -------
Received signal 2, exiting...
```

That's the source of your final problem, it's conflicting with something sound related.

I have an idea, but I haven't had a chance to try it here (It is 2:20am here and I need sleep).

First we will need to install some more software```
sudo apt-get install esound-clients
``` then we need to edit our et launch script```
sudo nano /usr/local/games/enemy-territory/et
``` and add the following line ```
esddsp --mmap et.x86
``` on the line just before ```
exec ./et.x86 "$@"
``` Let us know how it goes

Yagisan
&#23665;&#32650;&#12373;&#12435;

---

### Post by sOnIc on 2005-07-04
Ok i will try it ;-) 

```
sonic@ubuntu:~$ sudo apt-get install esound-clients
A Ler Listas de Pacotes... Pronto
Construindo Árvore de Dependências... Pronto
Os seguintes NOVOS pacotes serão instalados:
  esound-clients
0 actualizados, 1 novos instalados, 0 a remover e 0 não actualizados.
É necessário obter 35,6kB de arquivos.
Depois descompactar, 172kB adicionais de espaço em disco serão utilizados.
Obter:1 http://pt.archive.ubuntu.com hoary/main esound-clients 0.2.35-2ubuntu2 [35,6kB]
Obtidos 35,6kB em 0s (40,4kB/s)

Preconfiguring packages ...
A seleccionar pacote previamente des-seleccionado esound-clients
(A ler a base de dados ... 60621 ficheiros e directórios actualmente instalados.)
A descompactar esound-clients (desde .../esound-clients_0.2.35-2ubuntu2_amd64.deb) ...
A instalar esound-clients (0.2.35-2ubuntu2) ...
``` 

```
sonic@ubuntu:~$ sudo emacs /usr/local/games/enemy-territory/et

#!/bin/sh
# Needed to make symlinks/shortcuts work.
# the binaries must run with correct working directory
cd "/usr/local/games/enemy-territory"
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:.
export LD_ASSUME_KERNEL=2.4.2
exec ./et.x86 "$@"
esddsp --mmap et.x86
```

```
sonic@ubuntu:~$ et
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/sonic/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 1280x1024
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce 6600 GT/AGP/SSE2
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_NV_fog_distance
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
...using GLX_SGI_swap_control
...using GLX_SGI_video_sync
XF86 Gamma extension initialized

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce 6600 GT/AGP/SSE2
GL_VERSION: 1.5.3 NVIDIA 71.74
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_depth_bounds_test GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_vertex_array GL_HP_occlusion_test GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum
GLX_EXTENSIONS: GLX_EXT_visual_info GLX_EXT_visual_rating GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_SGI_video_sync GLX_SGI_swap_control GLX_ARB_multisample GLX_NV_float_buffer GLX_ARB_get_proc_address
GL_MAX_TEXTURE_SIZE: 4096
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU:
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------
Received signal 2, exiting...
``` 

Black screen again :| 
Ok, go to sleep tomorrow we continue :razz: ,and tks

---

### Post by Yagisan on 2005-07-04
Please try like this
```
#!/bin/sh
# Needed to make symlinks/shortcuts work.
# the binaries must run with correct working directory
cd "/usr/local/games/enemy-territory"
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:.
export LD_ASSUME_KERNEL=2.4.2
esddsp --mmap et.x86
exec ./et.x86 "$@"
```Goodnight.

Yagisan
&#23665;&#32650;&#12373;&#12435;

---

### Post by sOnIc on 2005-07-04
Same... [-X 
But you can play ET ??

Cheers sOnIc

---

### Post by Yagisan on 2005-07-05
Yes I can play ET, but not without problems. I have no sound, and I haven't gotten around to fixing it yet.

This is the output I get when starting ET
```
jamie@workhorse:~$ et
/bin/sh: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/jamie/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
execing profiles/Yagisan/etconfig.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 6: 1024 768
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 1024x768
Using 4/4/4 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce4 MX 440/AGP/SSE2
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_NV_fog_distance
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
...using GLX_SGI_swap_control
...using GLX_SGI_video_sync
XF86 Gamma extension initialized

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce4 MX 440/AGP/SSE2
GL_VERSION: 1.5.3 NVIDIA 71.74
GL_EXTENSIONS: GL_ARB_imaging GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_paletted_texture GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shared_texture_palette GL_EXT_stencil_wrap GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_vertex_array GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_fence GL_NV_fog_distance GL_NV_light_max_exponent GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_register_combiners GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_NV_texture_rectangle GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_SGIS_generate_mipmap GL_SGIS_multitexture GL_SGIS_texture_lod GL_SUN_slice_accum
GLX_EXTENSIONS: GLX_EXT_visual_info GLX_EXT_visual_rating GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_SGI_video_sync GLX_SGI_swap_control GLX_ARB_get_proc_address
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 2

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(0-bits)
MODE: 6, 1024 x 768 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU:
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_LINEAR
picmip: 0
texture bits: 32
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------
/dev/dsp: Input/output error
Could not mmap /dev/dsp
------------------------------------
Sound memory manager started
Sys_LoadDll(/home/jamie/.etwolf/etmain/ui.mp.i386.so)...
Sys_LoadDll(/home/jamie/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/jamie/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0x60074f40
Sys_LoadDll(ui) succeeded!
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: localhost.localdomain
Alias: localhost
Alias: workhorse
IP: 127.0.0.1
Started tty console (use +set ttycon 0 to disable)
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console
jamie@workhorse:~$
```
You can see my errors are
**/bin/sh: error while loading shared libraries: libdl.so.2: cannot open shared object **
and
[b]------- sound initialization -------
/dev/dsp: Input/output error
Could not mmap /dev/dsp[/b]
I can fix the first error by making my et file look like this```
#!/bin/sh
# Needed to make symlinks/shortcuts work.
# the binaries must run with correct working directory
cd "/usr/local/games/enemy-territory"
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:.
export LD_ASSUME_KERNEL=2.4.2
export LD_PRELOAD="/lib32/libdl.so.2"
exec ./et.x86 "$@"
``` and the second error can be fixed by running as root```
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
```
I even loaded up vmware and did an i386 install of et, editted the et file (LD__ASSUME_KERNEL), updated punkbuster, and then promptly (right now) ran into your problem. I'll look into what is causing it.

OK. This is a quick hack, that will stop all your sound but it will let et start. Before running et run this
```
sudo killall esd
```or if you don't mind no sound start et like this```

et +set s_initsound 0
```

---

### Post by sOnIc on 2005-07-05
Tks Yagisan, i love u man!!! :-P now i can play ET

Tks a lot :grin:

---

### Post by fabiuu on 2005-07-11
hi, i have a sucky connection (15k)

so i left my pc downloading et, and now that it's finnaly done, when i try to run it it gives me a checksum error!  ](*,) 

is there anything i could do to correct the file? i used 

wget -r <name of the file>

tks a lot.

---

### Post by Muk on 2005-07-16
i am getting following problems when isntalling ET, was wondering if you people could help me out a little:


--------
root@muk:/home/jack # ./et-linux-2.55.x86.run
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.55...........................................................................................................................................................................................................................................................................................................
/root/.setup7431: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
./setup.sh: line 143:  7455 Segmentation fault      "$setup" "$@" 2>>$NULL
The setup program seems to have failed on x86/glibc-2.1

See [http://zerowing.idsoftware.com/linux/](http://zerowing.idsoftware.com/linux/) for troubleshooting
root@muk:/home/jack #
-------------------------------

thx

jack

---

### Post by pt123 on 2005-07-16
> echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

Is there a way so you don't to type this everytime you want to play ET with sound.

---

### Post by WishMaster on 2005-07-17
I start ET from console, and then my screen gets black.
Nothing happens.

This is my "error-log".
Any suggestions?
([system specs](http://users.pandora.be/Nyx/ubuntu.html) 
- Intel i855GM chipset 400 MHz FSB with integrated graphics
- 15" TFT display designed for 1400x1050 with 1 ext. VGA port)

> ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/root/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 1280x1024
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: Mesa DRI Intel(R) 852GM/855GM 20041217 x86/MMX/SSE2
Initializing OpenGL extensions
...GL_S3_s3tc not found
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...GL_NV_fog_distance not found
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
... GLX_SGI_swap_control not found
... GLX_SGI_video_sync not found
XF86 Gamma extension initialized

GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Intel(R) 852GM/855GM 20041217 x86/MMX/SSE2
GL_VERSION: 1.3 Mesa 6.2.1
GL_EXTENSIONS: GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_cull_vertex GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_histogram GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_client_storage GL_APPLE_packed_pixels GL_ATI_blend_equation_separate GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_NV_vertex_program1_1 GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays
GLX_EXTENSIONS: GLX_ARB_get_proc_address GLX_ARB_multisample GLX_EXT_import_context GLX_EXT_visual_info GLX_EXT_visual_rating GLX_MESA_allocate_memory GLX_OML_swap_method GLX_SGI_make_current_read GLX_SGIS_multisample GLX_SGIX_fbconfig 
GL_MAX_TEXTURE_SIZE: 1024
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: disabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------


---

### Post by Yagisan on 2005-07-19
Have you tried the other suggestions in this thread ? eg ```
et +set s_initsound 0
```

---

### Post by BeSerKa on 2005-07-19
> /root/.setup7431: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
./setup.sh: line 143: 7455 Segmentation fault "$setup" "$@" 2>>$NULL
The setup program seems to have failed on x86/glibc-2.1

Thats the exact Same error message as I just got then.

My Ubuntu Hoary 5.04 has been updated

It has The Nvidia GFX drivers it has opengl running

Im totally stumped why I get that message.

Its strange cos It seems not many people get this error.

---

### Post by BeSerKa on 2005-07-19
oh ok Im a newbie,

I just went to the synaptic package manger downloaded the libgtk1.2 and now it works

---

### Post by DancingSun on 2005-07-20
[QUOTE=BeSerKa]Thats the exact Same error message as I just got then.

My Ubuntu Hoary 5.04 has been updated

It has The Nvidia GFX drivers it has opengl running

Im totally stumped why I get that message.

Its strange cos It seems not many people get this error.[/QUOTE]

I got this error as well:

```
./setup.sh: line 143: 28527 Segmentation fault      "$setup" "$@" 2>>$NULL
The setup program seems to have failed on x86/glibc-2.0
```

---

### Post by soul on 2005-07-20
When I type et it launches to a black screen then closes back to the desktop. This is what it says in the terminal. I'm really confused about what it means, but I'm sure my nvidia drivers are up to date. I also tried to do "et +set r_allowSoftwareGL 1" but that didn't work.  ](*,) someone help me please.

> tony@ubuntu:~$ et
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/tony/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 16 depth, 0 stencil display.
GL_RENDERER: Mesa GLX Indirect


***********************************************************
 You are using software Mesa (no hardware acceleration)!
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Received signal 11, exiting...


---

### Post by soul on 2005-07-21
Anyone?

---

### Post by Yagisan on 2005-07-22
Could you give us a bit more info about your system please, eg what arch, what release, cpu, videocard, the output from "et +set r_allowSoftwareGL 1".

It looks like et is dying when it tries to set the video resolution.

---

### Post by soul on 2005-07-22
[QUOTE=Yagisan]Could you give us a bit more info about your system please, eg what arch, what release, cpu, videocard, the output from "et +set r_allowSoftwareGL 1".

It looks like et is dying when it tries to set the video resolution.[/QUOTE]
I'm using  Hoary 5.04 (hopefully that's not the problem, I thought it would work on that too) I'm not sure about my CPU :( and my video card is a nvidia geforce mx 420 (I've played HL2 on it so that shouldn't be too much of a problem and I'm pretty sure I have current drivers) and when I type et +set r_allowSoftwareGL 1 it goes to a black screen (probably about 800x600) and I can scroll to the rest of my screen with my mouse but it says the following in the terminal

> tony@ubuntu:~$ et +set r_allowSoftwareGL 1
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/tony/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 16 depth, 0 stencil display.
GL_RENDERER: Mesa GLX Indirect
...using software Mesa (r_allowSoftwareGL==1).
Initializing OpenGL extensions
...GL_S3_s3tc not found
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...GL_EXT_compiled_vertex_array not found
...GL_NV_fog_distance not found
... GL_EXT_texture_filter_anisotropic not found
Initializing GLX extensions
... GLX_SGI_swap_control not found
... GLX_SGI_video_sync not found
XF86 Gamma extension initialized

GL_VENDOR: Mesa project: [www.mesa3d.org](www.mesa3d.org)
GL_RENDERER: Mesa GLX Indirect
GL_VERSION: 1.2 (1.5 Mesa 6.2.1)
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_imaging GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_ATI_texture_mirror_once GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_vertex_array GL_IBM_texture_mirrored_repeat GL_NV_blend_square GL_NV_texgen_reflection GL_NV_texture_rectangle GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow
GLX_EXTENSIONS: GLX_ARB_multisample GLX_EXT_visual_info GLX_EXT_visual_rating GLX_EXT_import_context GLX_SGIX_fbconfig GLX_ARB_get_proc_address
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 8

PIXELFORMAT: color(24-bits) Z(16-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU:
rendering primitives: multiple glArrayElement
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 0
multitexture: enabled
compiled vertex arrays: disabled
texenv add: disabled
compressed textures: disabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------


---

### Post by Yagisan on 2005-07-22
[QUOTE=soul]and my video card is a nvidia geforce mx 420[/QUOTE] Thank You. That was the magic clue needed. Based on the error It would seem you're not using the nvidia binary drivers.

Please follow the guide here [http://www.ubuntuguide.org/#installnvidiadriver](http://www.ubuntuguide.org/#installnvidiadriver) to install the binary drivers then try to run et again.

---

### Post by USAOwnz on 2005-07-24
How do you exit X server?

---

### Post by Chris- on 2005-07-24
[chris@localhost ~]$ sh et-linux-2.60.x86.run
: No such file or directory 1: ?
: command not foundun: line 2:
et-linux-2.60.x86.run: line 3: =: command not found
: command not foundun: line 3:
: command not foundun: line 4:
et-linux-2.60.x86.run: line 5: syntax error near unexpected token `{'
et-linux-2.60.x86.run: line 5: `if($servername=="fileshack1.sfo.speakeasy.net") { $location = "Sa' Francisco, CA"; }

Any ideas what going on?  I've download the game from fileshack.com

---

### Post by Chris- on 2005-07-24
[QUOTE=USAOwnz]How do you exit X server?[/QUOTE]

Type *init 3* in the Terminal.

---

### Post by Yagisan on 2005-07-24
[QUOTE=Chris-][chris@localhost ~]$ sh et-linux-2.60.x86.run
: No such file or directory 1: ?
: command not foundun: line 2:
et-linux-2.60.x86.run: line 3: =: command not found
: command not foundun: line 3:
: command not foundun: line 4:
et-linux-2.60.x86.run: line 5: syntax error near unexpected token `{'
et-linux-2.60.x86.run: line 5: `if($servername=="fileshack1.sfo.speakeasy.net") { $location = "Sa' Francisco, CA"; }

Any ideas what going on?  I've download the game from fileshack.com[/QUOTE]
There is something wrong with that file. Delete it and get the bittorret download from [http://zerowing.idsoftware.com/](http://zerowing.idsoftware.com/)

---

### Post by Chris- on 2005-07-24
[QUOTE=Yagisan]There is something wrong with that file. Delete it and get the bittorret download from [http://zerowing.idsoftware.com/](http://zerowing.idsoftware.com/)[/QUOTE]

I downloaded the bittorret, but what should I do now? never downloaded anything in bittorret format.

---

### Post by USAOwnz on 2005-07-24
I keep running into this error.

---

### Post by USAOwnz on 2005-07-24
Installed it, but now I can't seem to play it. It just goes black. Am I supposed to install something else?

---

### Post by USAOwnz on 2005-07-24
[QUOTE=Chris-]I downloaded the bittorret, but what should I do now? never downloaded anything in bittorret format.[/QUOTE]Umm... how about sh"./etfilenamehere"
./ being your where you put the enemy territory download.

---

### Post by soul on 2005-07-24
[QUOTE=Yagisan]Thank You. That was the magic clue needed. Based on the error It would seem you're not using the nvidia binary drivers.

Please follow the guide here [http://www.ubuntuguide.org/#installnvidiadriver](http://www.ubuntuguide.org/#installnvidiadriver) to install the binary drivers then try to run et again.[/QUOTE]
alright, now I have nvidia drivers, but when I start up ET it goes to a black screen then just goes back to my normal desktop ](*,)

---

### Post by Chris- on 2005-07-25
[QUOTE=USAOwnz]Umm... how about sh"./etfilenamehere"
./ being your where you put the enemy territory download.[/QUOTE]

Still getting the error, I'm now re-downloading it from 3Dgames, I do not have a clue f what to do to the torrent file.

---

### Post by Chris- on 2005-07-25
Gonna take over 9hours due of going over download limit.  If anyone has any clue about the torrent file, please let me know :/

---

### Post by DancingSun on 2005-07-25
[QUOTE=Chris-]Gonna take over 9hours due of going over download limit.  If anyone has any clue about the torrent file, please let me know :/[/QUOTE]
You need to open the torrent file with a bittorrent client.  Ubuntu comes with a very basic one.  It is under the Applications menu --> Internet --> GNOME BitTorrent.

---

### Post by Chris- on 2005-07-25
I'm using another OS :/

---

### Post by DancingSun on 2005-07-25
[QUOTE=Chris-]I'm using another OS :/[/QUOTE]
Well, then you'll need to download a BitTorrent client then.  If you have Java working, I'd recommend [Azureus](http://azureus.sourceforge.net/) .

---

### Post by Fisheke on 2005-07-27
I've just (yesterday) installed Ubuntu, and pretty much everything is up and running.. so i thought "let's play a game".. Managed to get ET running with the "+sset s_initsound 0".. but playing without sound ain't all that great, now is it?
Is there any solution to this?
System: 3200+ (32bit), nforce2, geforce3, hoary hedgehog...

---

### Post by Yagisan on 2005-07-27
[QUOTE=Fisheke]I've just (yesterday) installed Ubuntu, and pretty much everything is up and running.. so i thought "let's play a game".. Managed to get ET running with the "+sset s_initsound 0".. but playing without sound ain't all that great, now is it?
Is there any solution to this?
System: 3200+ (32bit), nforce2, geforce3, hoary hedgehog...[/QUOTE] From post number 51 above, [quote=Yagisan]echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss [/quote] as root, ie sudo su, then run that command.

---

### Post by Shiven on 2005-07-28
Hate to be the bringer of bad news, but 

echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

Is hardly a solution. The sound is crackly, proformance suffers and its really freaking annoying.

I've had ET running with full sound using the intel8x0 sound module, but two slight differences to my current setup- i was using alsa drivers (probably a year ago), and i was running gentoo. 

The problem lies in the alsa-oss emulation, and if you're using the intel8x0 you'll probably have to remove the ubuntu system sounds (because dmix (if you're using an asound rc) cannot operate two sounds when one is alsa and one is oss- they both must use the same system to play two sounds). 

I know this provided little to this conversation, but hopefully i've given someone some focus to find this error, or at least made it so this wasn't a total waste of time ^-^

I'm going to try out some of what i've said here, and i'll get back to you if i can get it working.

Shiven

EDIT:
Problem solved. If you goto System -> Preferances -> Sound, then disable both:
Enable sound server startup
Sounds for events

_THEN_:
open up applications -> system tools -> configuration
goto system -> gstreamer -> 0.8 -> default
double click "audiosink" and change "esdsink" to "alsasink"
audiosrc should be "alsasrc", just in case yours is different (mine was not)

admittantly this isn't a clean hack... but it worked for me and another box i maintain. the alsasink is so that you can run rhythmbox and other audio-using programs to run using alsas native sink instead of esd.

you may find that you have sound happening. Seems my problem was caused with the sound being played through alsa to say that i've clicked on the icon (or run it through the console), then the oss tried to play over the top, and as stated before dmix cannot handle both alsa and oss output, thus allowing me to have sound in ET.

On a seperate note: i couldn't get sound in ET running on gentoo in my last install (say 4 days ago) except through the fix to proc. Thank god for ubuntu ^-^

I really hope this helps someone, i've tried to document it as best i could, i need some feedback ^-^

---

### Post by Fisheke on 2005-07-28
Shiven,
you are a saint ! :)
I don't understand much of the sound-issues, but you solution just works perfectly for me :). (although, don't ask me what i just did :p)

---

### Post by Shiven on 2005-08-01
[QUOTE=Fisheke]Shiven,
you are a saint ! :)
I don't understand much of the sound-issues, but you solution just works perfectly for me :). (although, don't ask me what i just did :p)[/QUOTE]

lol, good to know it wasn't just me being lucky! ^-^

Nice to know i helped someone ^-^

---

### Post by Navyblue on 2005-08-02
I have installed Enemy Territories and I could not start the game, I get this message after typing "et" at the console.

```

Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: Mesa GLX Indirect


***********************************************************
 You are using software Mesa (no hardware acceleration)!
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Received signal 11, exiting...

```

I am able to start the game by adding "+set r_allowSoftwareGL 1" as suggested but the game is crawling and definitely not playable. I have installed the fglrx driver. How do I enable the hardware openGL?

I have installed the fglrx driver for my ATI 9550. My OpenGL screen saver is much faster now compared to before I installed the fglrx. My glxgears score is above 1000 FPS, so I suppose it is working? Does ET only work with driver from xfree86?

Btw, I did not choose enable the kernel framebuffer device in the /etc/X11/xorg.conf as I can't even start X when I do so.

Thanks in advance.

---

### Post by Shiven on 2005-08-02
That means that your video card is not configured correctly at all. run this command:

glxinfo | grep Direct

and see if the output is yes. if it is not, then your ati drivers are up to shiznit. 

If it does say yes, run glxinfo and paste it into here, might be something else i'm missing...

Might i add that atis + linux = no fun...

---

### Post by Navyblue on 2005-08-03
[QUOTE=Shiven]That means that your video card is not configured correctly at all. run this command:

glxinfo | grep Direct

and see if the output is yes. if it is not, then your ati drivers are up to shiznit. 

If it does say yes, run glxinfo and paste it into here, might be something else i'm missing...

Might i add that atis + linux = no fun...[/QUOTE]
 When I typed that command nothing appeared.

But I have solve the problem by following the method in this link

[http://ubuntuforums.org/showthread.php?t=20268](http://ubuntuforums.org/showthread.php?t=20268)

Thanks. :)

---

### Post by floflooo on 2005-08-29
Do some of you have keyboard problems in the game?

My laptop keyboard works perfectly with Ubuntu, except when playing ET. For exmple, if I press on Enter, the game directly goes in windowed mode (hence I do not speak anymore except using the quickchat combinations). Or once I press on Alt to sprint, the sprint always stays on...  :-|

---

### Post by metlock on 2005-09-05
Howdy, installed Enemy Territory on Kubuntu...it comes up on the screen, sound is present, but run very slow and sound stutters. My mouse can move but there is a definite lag.

Any ideas or suggestions?

---

### Post by Shiven on 2005-09-05
[QUOTE=metlock]Howdy, installed Enemy Territory on Kubuntu...it comes up on the screen, sound is present, but run very slow and sound stutters. My mouse can move but there is a definite lag.

Any ideas or suggestions?[/QUOTE]

does your computer meet the minimum specifications? that'd be my first pick...

secondly is your video card actually working? a good test for this is 
glxinfo | grep Direct 

(that capital is necessary), if it says "no" then your videocard needs tweaking...

if it says yes (this only applies if running an ati card), 
run glxinfo | grep vendor

if it comes up with mesa, your video card needs tweaking...


i can't think of anything else thats a necessity...  if its still not working after correcting any of these issues post back with some details on the box specs...

---

### Post by gerbman on 2005-09-07
[QUOTE=sOnIc]Hi!

```
sonic@ubuntu:~$ ping -c 3  google.pt
PING google.pt (216.239.59.104) 56(84) bytes of data.
64 bytes from 216.239.59.104: icmp_seq=2 ttl=239 time=234 ms
64 bytes from 216.239.59.104: icmp_seq=3 ttl=239 time=476 ms

--- google.pt ping statistics ---
3 packets transmitted, 2 received, 33% packet loss, time 2050ms
rtt min/avg/max/mdev = 234.231/355.272/476.314/121.042 ms
```

```
sonic@ubuntu:~$ et
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/sonic/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 1280x1024
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce 6600 GT/AGP/SSE2
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_NV_fog_distance
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
...using GLX_SGI_swap_control
...using GLX_SGI_video_sync
XF86 Gamma extension initialized

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce 6600 GT/AGP/SSE2
GL_VERSION: 1.5.3 NVIDIA 71.74
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_depth_bounds_test GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_vertex_array GL_HP_occlusion_test GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum
GLX_EXTENSIONS: GLX_EXT_visual_info GLX_EXT_visual_rating GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_SGI_video_sync GLX_SGI_swap_control GLX_ARB_multisample GLX_NV_float_buffer GLX_ARB_get_proc_address
GL_MAX_TEXTURE_SIZE: 4096
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU:
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------
Received signal 2, exiting...
```

Same problem :-| , black screen again :-x
I will try to install everything again step by step and post all console commands ;-)
One more time tks m8[/QUOTE]


Disable the Ubuntu sound server.  It is conflicting with resources the game needs.  "System", "Preferences", "Sound", uncheck "Enable sound server startup"

---

### Post by bryan986 on 2005-09-21
Ok I got my ET Installed and running, but when I   try to connect to any servers, it just gets stuck at "Awaiting Challenge" :(

---

### Post by Greeface on 2005-10-05
So is there no way to have sound in ET then?

---

### Post by DancingSun on 2005-10-05
[QUOTE=Greeface]So is there no way to have sound in ET then?[/QUOTE]
Search the forums, there's more than one way to get sound in ET.

---

### Post by gerbman on 2005-10-05
[QUOTE=Greeface]So is there no way to have sound in ET then?[/QUOTE]
All I had to do is what I posted above
```
Disable the Ubuntu sound server. It is conflicting with resources the game needs. "System", "Preferences", "Sound", uncheck "Enable sound server startup"
```

---

### Post by Greeface on 2005-10-05
Yeah, it didn't work for me.

EDIT:  Ah ha!  I figured it out!  I think I needed to restart to be able to get it to work.  Thanks a bunch. ~Greeface

EDIT EDIT:  dang, when I restarted it stopped working.  Back where i started again.

---

### Post by Misike on 2005-10-17
[QUOTE=easy_target]I still have to play the game as super user if I want the maps to be downloaded automatically. My sound works fine. I can't produce a desktop link on the applications menu without braking the sound. What's the problem? Heeeellllppppp!!!!!  :-([/QUOTE]

I've got the same problem!
When I started et from terminal as normal user the sound works well, but if i use the menu item the game starts but with no sound :(

Any advise?

Thanks!

Misike

ps.: the guide is very good, takes 5 minutes to install the game.. :)

---

### Post by xsence on 2005-11-01
is there a way to remove this game from my system?

thanks in advance

---

### Post by gerbman on 2005-11-01
[QUOTE=xsence]is there a way to remove this game from my system?

thanks in advance[/QUOTE]

But it's such a good game!! ;) I think you just need to remove the folder.  On my system, the folder is at /usr/local/games/enemy-territory.  ET also creates a folder in your home directory called '.etwolf'.  Remove that too, if you'd like.

---

### Post by shreevatsa on 2005-11-19
I am on Breezy. I can get sound to work by doing ```
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss

``` as root, but I can't get video to work. I see a black screen with a small resolution (I mean, my mouse pointer looks huge), then switches to a higher resolution, and stops. I can hear sound playing, but I can't see anything except the black screen.
glxinfo | grep direct says "direct rendering: Yes". I'm not very sure about what video card I have (sorry), but glxinfo | grep vendor says ```
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc

``` so I guess that must be it. 
I looked at [http://ubuntuforums.org/showpost.php?p=35109&postcount=23](http://ubuntuforums.org/showpost.php?p=35109&postcount=23) as it seems relevant to my issue, but the highest resolution I have is 1280x1024 which is what I'm using, anyway; so I can't possibly remove that.
Here's the complete output when I run et (got this by redirected stderr to a file):
```

ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/shreevatsa/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: Mesa DRI Intel(R) 845G 20050225
Initializing OpenGL extensions
...GL_S3_s3tc not found
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...GL_NV_fog_distance not found
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
... GLX_SGI_swap_control not found
... GLX_SGI_video_sync not found
XF86 Gamma extension initialized

GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Intel(R) 845G 20050225
GL_VERSION: 1.3 Mesa 6.3.2
GL_EXTENSIONS: GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_cull_vertex GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_histogram GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_client_storage GL_APPLE_packed_pixels GL_ATI_blend_equation_separate GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_NV_vertex_program1_1 GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays
GLX_EXTENSIONS: GLX_ARB_get_proc_address GLX_ARB_multisample GLX_EXT_import_context GLX_EXT_visual_info GLX_EXT_visual_rating GLX_MESA_allocate_memory GLX_OML_swap_method GLX_SGI_make_current_read GLX_SGIS_multisample GLX_SGIX_fbconfig
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU:
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: disabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------
------------------------------------
----- Sound Info -----
sound system is muted
    1 stereo
32768 samples
   16 samplebits
    1 submission_chunk
48000 speed
0x0xace85000 dma buffer
No background file.
----------------------
Sound memory manager started
Sys_LoadDll(/home/shreevatsa/.etwolf/etmain/ui.mp.i386.so)...
Sys_LoadDll(/home/shreevatsa/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/shreevatsa/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xab2f3f40
Sys_LoadDll(ui) succeeded!
Found high quality video and fast CPU
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: localhost.localdomain
Alias: localhost
Alias: ubuntuhere
Alias: ubuntuhere
IP: 127.0.0.1
IP: 192.168.1.71
Started tty console (use +set ttycon 0 to disable)
execing preset_high.cfg
r_colorbits will be changed upon restarting.
r_depthbits will be changed upon restarting.
r_picmip will be changed upon restarting.
r_mode will be changed upon restarting.
r_texturebits will be changed upon restarting.
RE_Shutdown( 1 )
Hunk_Clear: reset the hunk ok
----- Initializing Renderer ----
-------------------------------
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 6: 1024 768
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 1024x768
Using 4/4/4 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: Mesa DRI Intel(R) 845G 20050225
Initializing OpenGL extensions
...GL_S3_s3tc not found
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...GL_NV_fog_distance not found
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
... GLX_SGI_swap_control not found
... GLX_SGI_video_sync not found
XF86 Gamma extension initialized

GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Intel(R) 845G 20050225
GL_VERSION: 1.3 Mesa 6.3.2
GL_EXTENSIONS: GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_cull_vertex GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_histogram GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_client_storage GL_APPLE_packed_pixels GL_ATI_blend_equation_separate GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_NV_vertex_program1_1 GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays
GLX_EXTENSIONS: GLX_ARB_get_proc_address GLX_ARB_multisample GLX_EXT_import_context GLX_EXT_visual_info GLX_EXT_visual_rating GLX_MESA_allocate_memory GLX_OML_swap_method GLX_SGI_make_current_read GLX_SGIS_multisample GLX_SGIX_fbconfig GLX_SGIX_visual_select_group
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 4

PIXELFORMAT: color(32-bits) Z(24-bit) stencil(0-bits)
MODE: 6, 1024 x 768 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU:
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_LINEAR
picmip: 0
texture bits: 32
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: disabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----
Sys_LoadDll(/home/shreevatsa/.etwolf/etmain/ui.mp.i386.so)...
Sys_LoadDll(/home/shreevatsa/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/shreevatsa/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xab251f40
Sys_LoadDll(ui) succeeded!
Resolving etmaster.idsoftware.com
etmaster.idsoftware.com resolved to 192.246.40.60:27951
execing preset_normal_ui.cfg
execing preset_high_ui.cfg
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 1431 requests (1430 known processed) with 2 events remaining.

```
The last two lines only appeared after I killed X.
I've also tried export LD_ASSUME_KERNEL=2.4.2, but it has no effect.

---

### Post by lysis on 2005-11-23
i just installed enemy territory and i got this error after clicking the "start" button at the end of the installation.

```
------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
Xlib:  extension "XFree86-DGA" missing on display ":0.0".
Failed to detect XF86DGA Mouse
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 16 depth, 0 stencil display.
GL_RENDERER: Mesa GLX Indirect


***********************************************************
 You are using software Mesa (no hardware acceleration)!
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XFree86-VidModeExtension Activated at 640x480
Received signal 11, exiting...

```
any suggestions?

---

### Post by lysis on 2005-11-23
well i noticed it was using Mesa, so i re-installed ATi's driver and now i can get it to run.  i chmod and chowned the ENTIRE enemy-territory DIRECTORY and ALL files using the -R switch.

EVERY time i load the game it makes me make a profile, and it doesn't connect to the server i'm trying to connect to.

"Could not write to hunkusage.dat"  

It won't allow me to enable punkbuster.  *sigh*

---

### Post by lysis on 2005-11-24
any ideas on this stuff guys?

---

### Post by gerbman on 2005-11-27
[QUOTE=lysis]any ideas on this stuff guys?[/QUOTE]

Does it tell you where it's looking for "hunkusage.dat"?

---

### Post by lysis on 2005-11-30
[QUOTE=gerbman]Does it tell you where it's looking for "hunkusage.dat"?[/QUOTE]
nope. it didn't say.  the game popped up an in-game error saying this, i pressed ok, and then it closed the game.

---

### Post by phido on 2006-01-04
too late?

[I]Did u do that:
Verify that the directory that it downloads maps to is chmoded for access by your user! If you do not do this, you'll be unable to download and install the maps & other files you need to join games! 
 sudo chown -R user:user ~/.etwolf/
Replace user:user with your own user name & user group (usually the same name, in Ubuntu).
[https://wiki.ubuntu.com/EnemyTerritory]("https://wiki.ubuntu.com/EnemyTerritory")
[/I]

---

### Post by Jimmey on 2006-02-17
[quote=MyKonsole]james@ubuntu:~/ET$ ./et
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/james/.etwolf/etmain
/home/james/enemy-territory/etmain/pak2.pk3 (22 files)
/home/james/enemy-territory/etmain/pak1.pk3 (10 files)
/home/james/enemy-territory/etmain/pak0.pk3 (3725 files)
/home/james/enemy-territory/etmain/mp_bin.pk3 (6 files)
/home/james/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
execing profiles/James/etconfig.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension:  Ignored on non-fullscreen/Voodoo
Using 8/8/8 Color bits, 16 depth, 0 stencil display.
GL_RENDERER: Mesa GLX Indirect


***********************************************************
 You are using software Mesa (no hardware acceleration)!
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension:  Ignored on non-fullscreen/Voodoo
Received signal 11, exiting...
 [/quote] That's what I'm getting - I am using an Intel graphics card. Whenever I do use > +set r_allowSoftwareGL 1, it runs, SLOWLY. It took me about 20 minutes to quit the game. Any help's greatly appreciated. Thankyou

---

### Post by floflooo on 2006-02-17
[QUOTE=Jimmey][COLOR="Red"]You are using software Mesa (no hardware acceleration)![/COLOR][/QUOTE]
I guess that's your problem! You need to have your graphic card driver properly installed, i.e with 3D hardware acceleration enabled.

---

### Post by Ouaaahhhh on 2006-02-18
Only ATI radeon version 8.16.20 (RV250) for radeon M9/9000 work with enemy terrritory or WarSoW.  Et Failed to start menu after upragding to 8.18.8 or 18.22.5. 
Ouaaahhhh

---

### Post by maybeme on 2006-02-20
I can start the game (even the dedicated server from ingame without my config) , but when I try to start the dedicated server from the command line with my config I get this:

```
maybeme@ETSERVER:~$ /usr/local/games/enemy-territory/et +exec server.cfg ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/maybeme/.etwolf/etmain/venice.pk3 (330 files)
/home/maybeme/.etwolf/etmain/supplydepot2.pk3 (46 files)
/home/maybeme/.etwolf/etmain/password2_final.pk3 (101 files)
/home/maybeme/.etwolf/etmain/goldrush2_wx.pk3 (37 files)
/home/maybeme/.etwolf/etmain/caen.pk3 (82 files)
/home/maybeme/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
4359 files in pk3 files
execing default.cfg
couldn't exec language.cfg
execing profiles/Server/etconfig.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce2 MX/AGP/SSE
Initializing OpenGL extensions
...using GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_NV_fog_distance
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
...using GLX_SGI_swap_control
...using GLX_SGI_video_sync
XF86 Gamma extension initialized

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce2 MX/AGP/SSE
GL_VERSION: 1.5.3 NVIDIA 71.74
GL_EXTENSIONS: GL_ARB_imaging GL_ARB_multitexture GL_ARB_point_parameters GL_ARB _point_sprite GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_c ompression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_com bine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_recta ngle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program G L_ARB_vertex_shader GL_ARB_window_pos GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_a bgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_ EXT_clip_volume_hint GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_draw_r ange_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_ EXT_paletted_texture GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_r escale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_share d_texture_palette GL_EXT_stencil_wrap GL_EXT_texture_compression_s3tc GL_EXT_tex ture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_textur e_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_l od_bias GL_EXT_texture_object GL_EXT_vertex_array GL_IBM_rasterpos_clip GL_IBM_t exture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_fence GL_NV _fog_distance GL_NV_light_max_exponent GL_NV_packed_depth_stencil GL_NV_pixel_da ta_range GL_NV_point_sprite GL_NV_register_combiners GL_NV_texgen_reflection GL_ NV_texture_env_combine4 GL_NV_texture_rectangle GL_NV_vertex_array_range GL_NV_v ertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_SGIS_generate _mipmap GL_SGIS_multitexture GL_SGIS_texture_lod GL_SUN_slice_accum
GLX_EXTENSIONS: GLX_EXT_visual_info GLX_EXT_visual_rating GLX_SGIX_fbconfig GLX_ SGIX_pbuffer GLX_SGI_video_sync GLX_SGI_swap_control GLX_ARB_get_proc_address
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 2

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU:
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------
------------------------------------
----- Sound Info -----
sound system is muted
    1 stereo
32768 samples
   16 samplebits
    1 submission_chunk
22050 speed
0x0xaef3c000 dma buffer
No background file.
----------------------
Sound memory manager started
Sys_LoadDll(/home/maybeme/.etwolf/etmain/ui.mp.i386.so)...
Sys_LoadDll(/home/maybeme/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/maybeme/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xad3aaf40
Sys_LoadDll(ui) succeeded!
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: localhost.localdomain
Alias: localhost
Alias: ETSERVER
IP: 127.0.0.1
Started tty console (use +set ttycon 0 to disable)
execing server.cfg
dedicated will be changed upon restarting.
sv_maxclients will be changed upon restarting.
g_gametype will be changed upon restarting.
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
Received signal 11, exiting...
Shutdown tty console

```

My server.cfg:
```
//Enemy Territory Server Config


//General Settings
set sv_hostname "^8DVH^1!^wFrag Server"
set dedicated "2"
set sv_maxclients "16"
set g_password ""
set sv_privateclients "2"
set sv_privatepassword "SENSORED"
set rconpassword "SENSORED"
set refereePassword "SENSORED"
set server_motd0 "^8DVH^1!^wFrag Server"
set server_motd1 "^8Have Fun!"
set server_motd2 "^1Happy Fragging!"
set server_motd3 "www.dvh-clan.be"
set server_motd4 "^wNo sk, tk, bleeding or camping"
set server_motd5 "^wWatch your language"
set sv_maxRate "0"
set sv_dl_maxRate "42000"
set sv_allowDownload "0"
set sv_wwwDownload "1"
set sv_wwwBaseURL "http://home.scarlet.be/~vdsteen/maps/"
set sv_wwwDlDisconnected "0"
set sv_wwwFallbackURL ""
set sv_pure "1"
set developer "0"
set g_gametype "2"
set net_ip "81.11.248.53"
set net_port "27960"

//Last Man Standing Settings
set g_lms_teamForceBalance "1"
set g_lms_roundlimit "3"
set g_lms_matchlimit "2"
set g_lms_followTeamOnly "1"
set g_lms_lockTeams "0"

//Vote Settings
set g_allowVote "1"
set vote_limit "6"
set vote_percent "66"
set vote_allow_comp "0"
set vote_allow_pub "0"
set vote_allow_kick "1"
set vote_allow_map "0"
set vote_allow_matchreset "1"
set vote_allow_mutespecs "1"
set vote_allow_nextmap "0"
set vote_allow_referee "0"
set vote_allow_shuffleteams "1"
set vote_allow_swapteams "1"
set vote_allow_friendlyfire "0"
set vote_allow_timelimit "0"
set vote_allow_warmupdamage "1"
set vote_allow_antilag "0"
set vote_allow_balancedteams "0"
set vote_allow_muting "1"

//Misc Settings
set g_heavyWeaponRestriction "100"
set g_antilag "1"
set g_altStopwatchMode "0"
set g_autofireteams "0"
set g_complaintlimit "6"
set g_ipcomplaintlimit "3"
set g_fastres "0"
set g_friendlyFire "1"
set g_minGameClients "0"
set g_maxlives "0"
set g_alliedmaxlives "0"
set g_axismaxlives "0"
set g_teamforcebalance "1"
set g_noTeamSwitching "0"
set g_voiceChatsAllowed "5"
set g_doWarmup "1"
set g_warmup "60"
set g_spectatorInactivity "0"
set sv_floodProtect "1"
set sv_minping "0"
set sv_maxping "0"
set match_latejoin "1"
set match_minplayers "0"
set match_mutespecs "0"
set match_readypercent "66"
set match_timeoutcount "5"
set match_warmupDamage "1"
set team_maxplayers "0"
set team_nocontrols "0"
set com_watchdog "60"
set com_watchdog_cmd ""
set g_useralliedrespawntime ""
set g_useraxisrespawntime ""
set g_covertopsChargeTime ""
set g_engineerChargeTime ""
set g_LTChargeTime ""
set g_soldierChargeTime ""
set g_medicChargeTime ""
set g_disableComplaints "1"
set g_gravity "800"
set g_inactivity "0"
set g_knifeonly "0"
set g_log ""
set g_speed "320"

//PunkBuster Settings
pb_sv_enable
set PB_SV_MsgPrefix "^3PunkBuster Server"
set PB_SV_Sleep "60"
set PB_SV_KickLen "2"
set PB_SV_CvarFreq "6"
set PB_SV_MinName "0"
set PB_SV_MaxDlRate "1"
set PB_SV_MaxConDls "3"
set PB_SV_AutoSs "0"
set PB_SV_AutoSsFrom "60"
set PB_SV_AutoSsTo "1200"
set PB_SV_CQC "1"
set PB_SV_ScoreKick "0"

```

Any ideas?

grtz

EDIT: When I use /usr/local/games/enemy-territory/et +set dedicated 2 +set fs_game +exec server.cfg +set net_ip 192.168.2.105
 I get ```
execing server.cfg
sv_maxclients will be changed upon restarting.
g_gametype will be changed upon restarting.
Hitch warning: 869 msec frame time
Segmentatie fout

```

When I use /usr/local/games/enemy-territory/etded +set dedicated 2 +set fs_game +exec server.cfg +set net_ip 192.168.2.105
I get
```
execing server.cfg
sv_maxclients will be changed upon restarting.
g_gametype will be changed upon restarting.
Received signal 11, exiting...
Shutdown tty console

```

---

### Post by Jimmey on 2006-02-21
I downloaded and installed the drivers ( For all you Intel users, it's 10x easier to download Intel drivers designed for SuSe, and use Alien to convert the .rpm packaged into a .deb ), and got ET working - Slightly.

When I started the game, it was 600x480 in a 1024x768 screen, in the bottom left hand side: the rest was black. Then, when I tried to start a map, it said:
> Cannot write to hunkusage.dat
So, I followed the instructions posted somewhere on this forum:
> sudo chown -R user:user ~/.etwolf/.
Now, whenever I start the game, I can hear the sound, but, can't see anything, other than black. I have to press ` and type "exit" to get back to the menu.

Any help is greatly appreciated.

---

### Post by mztriz on 2006-02-26
```
mztriz@Ava:~$ sudo et
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/mztriz/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Segmentation fault



```

---

### Post by gerbman on 2006-02-27
EDIT: bad post

---

### Post by Jimmey on 2006-02-27
Everything's now good in the hood, except:

I've only a 64MB graphics card, and so I'm restricted to 800x600 resolution if I want to play, which, in Windows, was fine, I could set it to that, and It'd be a little more blocky, but that was okay..

With Ubuntu, I set it to 800x600 and it goes, as I've described, into an 800x600 size corner, with the rest of the screen being black, although it's on the full screen setting. I want to know how to get ET to work at 800x600, actually full screen. Please, can anyone help?

---

### Post by mrstimpson on 2006-03-30
I downloaded et - I have no idea of terminal command yet, first day of linux ubuntu and realized enemy teritory linux is x86. so i guess no go for me running ubuntu on ppc? nevermind good info here though :(

---

### Post by eRoot on 2006-05-01
Finally I've got ET working with sound. Great!

But, unfortunately, another problem is bugging me now. Whenever I have played for a while, ET crashes and I return to the desktop. It seems to be happening at random.
Here is the output I get:
```
The Allies have breached the Depot Gate!
ormi^7 was blasted by chcem byc w ^0ZUCHACH^7's support fire
-------- UNRECOVERABLE ERROR --------
This may be due to a bug in etpro
Information to be used in a bug report is being generated:
------------- CUT HERE --------------
Version: etpro 3.2.4
Platform: Linux
Build: Nov 24 2005 17:58:02
Signal: Segmentation violation (11)
Signal code: 1
fault address: (nil)
Load addresses:
0xb7f50000 /lib/tls/i686/cmov/libdl.so.2
0xb7e6a000 /usr/lib/libX11.so.6
0xb7e5d000 /usr/lib/libXext.so.6
0xb7e3b000 /lib/tls/i686/cmov/libm.so.6
0xb7d0c000 /lib/tls/i686/cmov/libc.so.6
0xb7f63000 /lib/ld-linux.so.2
0xb7d08000 /usr/lib/libXau.so.6
0xae444000 /lib/tls/i686/cmov/libnss_compat.so.2
0xae42f000 /lib/tls/i686/cmov/libnsl.so.1
0xae426000 /lib/tls/i686/cmov/libnss_nis.so.2
0xae41c000 /lib/tls/i686/cmov/libnss_files.so.2
0xacb7c000 /usr/lib/libGL.so.1
0xacb6a000 /lib/tls/i686/cmov/libpthread.so.0
0xac2dc000 /usr/lib/xorg/modules/dri/atiogl_a_dri.so
0xac222000 /usr/lib/libstdc++.so.5
0xac21a000 /lib/tls/i686/cmov/librt.so.1
0xac210000 /lib/libgcc_s.so.1
0xa3208000 /usr/lib/libXcursor.so.1
0xae450000 /usr/lib/libXrender.so.1
0xa3204000 /usr/lib/libXfixes.so.3
0x9db15000 /root/.etwolf/pb/pbcl.so
0xa2ff8000 /lib/tls/i686/cmov/libnss_dns.so.2
0xa2fe5000 /lib/tls/i686/cmov/libresolv.so.2
0x9d6f9000 /root/.etwolf/pb/pbag.so
0x9d496000 /root/.etwolf/pb/pbsv.so
0x9e6b2000 /root/.etwolf/etpro/ui.mp.i386.so
0x970ee000 /root/.etwolf/etpro/cgame.mp.i386.so
EIP: ae65ff2c
edi:af2349e0 esi:af234960 ebp:ae65ff2c esp:bff767d0
eax:00000000 ebx:00000000 ecx:00000000 edx:08e3bf34
stack:
00001d80 453e8000 9b604d18 081132b2 ae65ff2c 08e8e994 08e8ebdc 3ff00000
00000000 3f7fffcc 00000000 08113489 00000001 000dfc89 971c79cc 0011c28c
0000004c bff76840 42804001 0811bda6 bff76840 00000000 0000023c 9712f065
3f800000 3f800000 3f800000 00000000 44f302a1 c408f3a2 42804001 be6f46ce
code:
00 00 00 00 00 00 00 00 46 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
00 00 a3 38 6d 3f dc 2e 10 3e 0a 78 b2 3e 86 e0 88 3e c0 66 cf 3e 9a d3 5f bf 
Stack trace:
1 entries
/root/.etwolf/etpro/cgame.mp.i386.so[0x9710ba52]
------------- CUT HERE --------------
Trying to clean up...
Received signal 11, exiting...
X Error of failed request: BadValue (integer parameter out of range for opera tion)
  Major opcode of failed request: 135
  Minor opcode of failed request: 10
  Serial number of failed request: 1452
Shutdown tty console
Segmentation fault
root@box:/home/barry#
```
Does anybody have a clue what it is, that is causing this?

---

### Post by eRoot on 2006-05-01
deleted -- Still looking for a fix.

---

### Post by jonnyfive on 2006-05-04
I have shared video ram. I don't have nvidia or ati. It's like sis or something. Anyways. I installed enemy territory and it was running and everything but it is so choppy on the opening screen and the options screen that I can barely do anything. I move the mouse and there is about  5 second delay before it is moved on the screen. What can I do?
I have enemy territory installed on this computer on my winxp partition and it works great, so I don't see why I wouldn't be able to run it linux..


Thanks.

---

### Post by floflooo on 2006-05-04
[QUOTE=jonnyfive]I have enemy territory installed on this computer on my winxp partition and it works great, so I don't see why I wouldn't be able to run it linux...[/QUOTE]
Find proper drivers with 3d hardware acceleration for your card and install them. That should take care of your problem (provided such drivers exist).

---

### Post by jonnyfive on 2006-05-04
[QUOTE=floflooo]Find proper drivers with 3d hardware acceleration for your card and install them. That should take care of your problem (provided such drivers exist).[/QUOTE]

Thank you for your help! I have a sis graphics card or whatever but I don't really know where to start looking for drivers for it for linux. Can you give me any suggestions?

---

### Post by floflooo on 2006-05-04
No idea... Nvidia has decent drivers, ATI has drivers, and I don't know about Sis.
Try to Google it!

---

### Post by pepolez on 2006-05-05
The process was fairly simple for me. I simply installed the restricted nvidia modules for my GFX card, Installed opengl, chmodded /dev/dsp to 777, installed et as root with default options, started artsd and then started et using 'artsdsp -m et'.

only problem i have is a little bit of a performance hit from artsd and the occasional segfault (although i attribute the segfaults to buggy et linux coding).

---

### Post by Citro on 2006-05-10
Hi

If I mark a server as favourite is it supposed to stay as a favourite until I delete it??

For me its gone if I restart ET.

Thanks.

---

### Post by line-of-sight on 2006-05-14
Looks like I have the same problem as a few other people here:

3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 4/4/4 Color bits, 16 depth, 0 stencil display.
GL_RENDERER: Mesa GLX Indirect


***********************************************************
 You are using software Mesa (no hardware acceleration)!
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Received signal 11, exiting...


I'm using an ATI Rage 128 PF/PRO.  Anyone know how I can configure it properly? Or at least where I can read up on configuring video drivers. I believe the binary driver howtos don't apply to this model or...?

---

### Post by pbmax on 2006-05-30
Fairly Newbish at this. Using Kubuntu 5.10 I have read all 13 pages of this thread.

I got the NVIDIA drivers working and can play ET as user, but with no sound,

this works
```
chmod 777 /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

```
but only if I switch to root first.  (Sudo doesn't seem to make a difference)
but then I still have to be root to play with sound.

What really chaps my hide is that the chmod doesn't stick.  I have to redo it every bootup.  I thought chmod would make it open for me to run as user, but no joy.

I tried making a shell script with the above commands. (with sudo and with sudo -i) to run from user, but it doesn't seem to work.

My only workaround right now is to logout as user. console login as root. startx. run the /proc fix, then run ET.  I'm willing to do it to play, but is there an easier way?
thanks pb

edit:

here's what I did that works:

etsound.sh
```
sudo chmod 777 /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

``` 
in my home/user folder

then run 
```
etsound.sh
kdesu et
```
in ternimal. It asks for password twice, but it works.

pb

---

### Post by pepolez on 2006-06-01
[QUOTE=Citro]Hi

If I mark a server as favourite is it supposed to stay as a favourite until I delete it??

For me its gone if I restart ET.

Thanks.[/QUOTE]

I *do* have this problem though ;)

Oh, and to answer the inevitable question 'I try to start et using artsd and artsdsp and it says artsdsp is for binaries only'
I first got this problem when upgrading to dapper, but it was easily fixed, I just had to add artsdsp in the et executable, eg:
```

#!/bin/sh
## Location: /usr/local/games/enemy-territory/et

## Get into correct working directory
cd "/usr/local/games/enemy-territory"

## Not sure what this does, exports the library path into a global scope maybe? *shrug*
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:.

## Start et with artsdsp -m
exec artsdsp -m ./et.x86 "$@"


```

Personally though, now that I use an XGL window manager and stuff, which screws up most opengl apps, plus a few other things. I execute et in a second X server with this script:
```

#!/bin/bash
## Location: /usr/local/bin/x.et

## Start another X server, pipe anything not returned by et to /dev/null (otherwise
## something presses enter until we kill the terminal we executed it from
xinit /usr/local/games/enemy-territory/et $* -- :1 > /dev/null

```

This script will start a SECOND X server for enemy territory, without a window manager or anything thus avoiding the XGL problem. The enemy territory executable remains as stated above. The second X server will be automatically terminated when et exits.

Also, you *should* be able to access your first X server while playing with CTRL + ALT +F7 (and then switch back with CTRL + ALT +F8). Switching between X servers in this situation has varying outcomes, the worst being both X servers crash and you have to CTRL + ALT + BACKSPACE.

Occasionally I have a problem when I enter a game and any mouse movement is interperted as wild spinning of the mouse around a point. Weirdly enough, the menus are fine, it's just when you get up to the limbo menu and beyond that it's a problem.

I've heard of varying levels of success with this procedure, but I doubt it will totally **** up  your system :)

Thanks to a few posters in various XGL and openGL related threads for their help. Don't be afraid to search the forums or even google.

---

### Post by pbmax on 2006-06-14
My video isn't liking ET much right now.  Any suggestions on how to fix this:

[img]http://phillbecker.com/phill/2006-06-13-235504-railgun.jpg[/img]

My nvidia drivers are installed.  Where else should I look?
Using Xubuntu Dapper now.  It didn't work on the KDE desktop either
thanks
pb

Edit: Solved
The legacy Nvidia drivers work, even though the GeForce4 is listed for the newer drivers.

---

### Post by tshirtz1013 on 2006-06-22
This fixed my no sound in Enemy Territory. I use a Soundblaster Audigy and am running dapper. I also have an onboard sound card available. I tried everything posted here with no great luck so finally, I attacked ET, what I found was that mpost of my apps try to use "/dev/dsp" for sound.... ahaha !! My Audigy is attached to dsp1 so I pressed the tilde key to bring up the console in ET and then typed at the prompt > snddevice "/dev/dsp1"  and viola...upon restart of et I had sound. I hope this helps some people. 

:)

---

### Post by Oblong_Cheese on 2006-06-22
[QUOTE=tshirtz1013]I hope this helps some people. 

:)[/QUOTE]

It helped me!

But UT2004demo gives me the same error! How can I fix it? :(

---

### Post by Qstosh on 2006-07-06
[QUOTE=Tonio]Hello,

I download it from fileshack.com, done as you said, but got this : 

```
root@ubuntu:/mnt/atchoum/Softs/linux # ls -l | grep et
-rwxr-xr-x    1 tonio    tonio    30920500 2004-12-19 16:52 et-linux-2.56-2.x86.run
root@ubuntu:/mnt/atchoum/Softs/linux # ./et-linux-2.56-2.x86.run
bash: ./et-linux-2.56-2.x86.run: /bin/sh: bad interpreter: Permission non accordée
root@ubuntu:/mnt/atchoum/Softs/linux # su -c "./et-linux-2.56-2.x86.run"
bash: ./et-linux-2.56-2.x86.run: /bin/sh: bad interpreter: Permission non accordée
root@ubuntu:/mnt/atchoum/Softs/linux #
``` 

Any idea?

PS:Sorry for english, I don't speak very well.[/QUOTE]

try with this:

```
wget http://ftp.freenet.de/pub/4players/hosted/et/official/et-linux-2.60.x86.run
```

next

```
sudo sh et-linux-2.60.x86.run
```
write root password and all will be ok

---

### Post by Qstosh on 2006-07-07
> **Jimmey said:**
> That's what I'm getting - I am using an Intel graphics card. Whenever I do use , it runs, SLOWLY. It took me about 20 minutes to quit the game. Any help's greatly appreciated. Thankyou

you really didn't installed drivers

---

### Post by Qstosh on 2006-07-07
> **lysis said:**
> well i noticed it was using Mesa, so i re-installed ATi's driver and now i can get it to run.  i chmod and chowned the ENTIRE enemy-territory DIRECTORY and ALL files using the -R switch.

EVERY time i load the game it makes me make a profile, and it doesn't connect to the server i'm trying to connect to.

"Could not write to hunkusage.dat"  

It won't allow me to enable punkbuster.  *sigh*

you must log in as root (terminal user@user:~$ su root [if the authentication is failure then : sudo passwd{ and change password}]) and then start game.

---

### Post by Theimon on 2006-08-14
Sorry for bumping this thread.......

I'm running Dapper AMD64 together with a nVidia 6600 128MB video card. Glx drivers installed and working. I installed ET v2.55 and I'm able to start the game. I hear sound and it goes full screen without troubles, so no problem there (customizing all settings is not my biggest worry atm).
The actual problem I do get is that when I quit ET, Ubuntu will go back to the Desktop with ET's resolution so I get a massive useless Desktop. Only solution so far is restarting X but then I lose all open programs and have to start them all over again.......

Any suggestions/help is appreciated..

---

### Post by pbmax on 2006-08-17
Everything used to work. Now I get no sound.  I've turned off KDE sound manager, but still no good.

I get this error not
```
------- sound initialization -------
=: No such file or directory
Could not open =
------------------------------------
Sound memory manager started
Sys_LoadDll(/phill/.etwolf/etmain/ui.mp.i386.so)...
Sys_LoadDll(/phill/.etwolf/etmain/ui.mp.i386.so) failed:
"/phill/.etwolf/et
```

any suggestions?

---

### Post by pbmax on 2006-08-17
> **lysis said:**
> well i noticed it was using Mesa, so i re-installed ATi's driver and now i can get it to run.  i chmod and chowned the ENTIRE enemy-territory DIRECTORY and ALL files using the -R switch.

EVERY time i load the game it makes me make a profile, and it doesn't connect to the server i'm trying to connect to.

"Could not write to hunkusage.dat"  

It won't allow me to enable punkbuster.  *sigh*

If you installed as "root" instead of with sudo, the .etwolf folder will be in the /root directory instead of /home/user.

make sure you can see hidden directories, then copy the .etwolf folder into you user folder. Be sure to set the permissions so you can use it.
pb

---

### Post by d10b on 2006-09-03
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/root/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)est &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)                        &#9474;
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)now?                   &#9474;
/usr/local/games/enemy-territory/etmain                                            &#9474;
                                  &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508;
----------------------            &#9474;             < Yes >       < No  >              &#9474;
38 files in pk3 files             &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
----- CL_Shutdown -----
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: Couldn't load default.cfg - I am missing essential files - verify your installation?


I get this after running the game after install :(

---

### Post by LensCap on 2006-09-04
Anyone have this error before?

```

/home/willum/.setup10338: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
./setup.sh: line 143: 10365 Segmentation fault      "$setup" "$@" 2>>$NULL
The setup program seems to have failed on x86/glibc-2.1

```

This is for the 2.55 Installation of ET, if that matters.  Everything up to date on Ubuntu Dapper.

EDIT: that problem was fixed by getting the older libgtk, but now I have a new one:

"Xlib:  extension "GLX" missing on display ":0.0"."

I have the nvidia-glx installed (GeForce MX440), and running et pops up that error many times as well as leaving my screen at a different resolution.

---

### Post by fatsheep on 2006-09-09
I just added a section to the wiki page on ET after my experiences with sound trouble: "A Startup Script for Sound Problems".  

Link: [https://help.ubuntu.com/community/EnemyTerritory#head-6b2a51bfefebc91c4a6f5e722307dff66009766b](https://help.ubuntu.com/community/EnemyTerritory#head-6b2a51bfefebc91c4a6f5e722307dff66009766b)

---

### Post by Ajguy on 2006-09-11
I just tried installing the game and got this error:

Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 16 depth, 0 stencil display.
GL_RENDERER: Mesa GLX Indirect


***********************************************************
 You are using software Mesa (no hardware acceleration)!
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Received signal 11, exiting...


Far as I know all drivers are installed correctly. Anyone know what's going on?

---

### Post by Kauna on 2006-09-21
Hi!

I'm sorry to lift up this ages old thread, but I have just a few days ago installed Ubuntu and am now struggling to install WolfET. How do I exactly do it? In the first post it was said to go to *applications -> system tools -> root terminal*, but the only *system tools* I'm able to find is under *Add/Remove...* and I don't quite know what to do there.

Please help me out if you can. :oops:

Now I think I got a bit further.. or not?

> Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.55...........................................................................................................................................................................................................................................................................................................
This installation doesn't support glibc-2.0 on Linux / unknown
(tried to run setup)
See [http://zerowing.idsoftware.com/linux/](http://zerowing.idsoftware.com/linux/) for troubleshooting
The setup program seems to have failed on unknown/glibc-2.0

See [http://zerowing.idsoftware.com/linux/](http://zerowing.idsoftware.com/linux/) for troubleshooting

---

### Post by lmok on 2006-09-21
Hello,

I recently installed Ubuntu Dapper, and so far I had no problems.
Anyway, I wanted to install ET, and I managed to do so without problems using this great guide.
But, I do have a problem with the game:

The game itself runs fine, although the sound doesn't work. But that's not a big deal as I found a command to fix it (in this thread, ofcourse(: ). 
The main problem is that when I go to the server list menu and hit the "Refresh List" button, the game freezes for about 20 seconds and returns no servers at all. Thus, I can't really play online.

I'm not sure if it's related to the installation, or perhaps to some configuration file or maybe even to my router.

If anyone knows how to fix this problem, it would be lovely (:


-lmok

---

### Post by Somniis on 2006-09-23
In response to Imok, ET seems to do that sometimes.  I had it installed in Windows (just today dropped it entirely for Ubuntu ;) ) and it would do what you are saying.  Download the All-Seeing Eye and run it with wine.. not sure if it works, but that will give you access to the game servers without having to go in-game to do it.

---

### Post by trekkypj on 2006-09-23
Just wanted to say thanks a lot for your guide here...

I just got ATI 3D working on my laptop so I installed ET to test it. Had the sound problems but the script (linked from here) worked brilliantly. You do have to use the second script as the first one doesn't fix the problem.

Am using a HP Pavilion dv5000 with Dapper and if you use the 'longer' script it should work no problems. ;)

I get a funny noise every time I quit ET using this. Doesn't seem to affect anything, but is this normal? Kind of a high pitched squeak...

---

### Post by Linux N00b on 2006-10-01
Now it's saying /home/alex/.setup18427: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
./setup.sh: line 143: 18459 Segmentation fault      "$setup" "$@" 2>>$NULL
The setup program seems to have failed on x86/glibc-2.1

---

### Post by HAL90000 on 2006-10-02
root@ZARDOZ:/home/hal9000# ./et-linux-2.60.x86.run
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.60 Full Install..............................................................................................................................................................................................................................................................................................................................
/root/.setup7318: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

Enemy Territory 2.60 Installation
 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;


        &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; Installing... &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
        &#9474; /usr/local/games/enemy-territory//EULA_Wolfenstein_Enemy_    &#9474;
        &#9474; Territory.txt                                                &#9474;
        &#9474;                                                              &#9474;
        &#9474;                                                              &#9474;
        &#9474;                                                              &#9474;
        &#9474;  &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  &#9474;
        &#9474;  &#9474;                          100%                          Warning: kbuildsycoca is unable to register with DCOP.&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;  &#9474;
        &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;kbuildsycoca running...&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
                                                                 kdeinit: Aborting. $DISPLAY is not set.
                        There was an error setting up inter-process communications for KDE. The message returned by the system was:

                                                   Could not read network connec
              &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; Request &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
              &#9474; Installation complete!                         &#9474;
              &#9474; Would you like to start now?heck that the "dcopserver" p
              &#9474;
              &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508;
              &#9474;             < Yes >       < No  >            nvalid Serv
              &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;



                                                Installing symlink /usr/local/bin/etded -> /usr/local/games/enemy-territory//etded
                                                  Removing existing et symlink
                                                                              Installing symlink /usr/local/bin/et -> /usr/local/games/enemy-territory//et
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/root/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Error couldn't open the X display
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
Error couldn't open the X display
...WARNING: could not set the given mode (3)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem

root@ZARDOZ:/home/hal9000#

This is the error I get when running the install in root...
Thanx in advance...
I'm Running Kubuntu / Dapper drake

---

### Post by Somniis on 2006-10-20
Hi all!  Having some performance issues with ET that I can't seem to figure out.

The issue is this: when I click any button that goes to another screen (e.g. when clicking to stop the video which plays on start-up) it freezes for a few minutes and then continues.  It has done this with the buttons: "Enable Punkbuster", "Play", and when joining a server.  I recently did a fresh install of Ubuntu (6.06), but I have played ET fine without this problem on Ubuntu before.

The sound and everything else works.. just the annoying pauses for 3-4min everytime a button is clicked.  Anyone else have this problem? ](*,)

EDIT: To HAL above: you probably need to download the libgtk-1.2 package.  Have you tried that?

---

### Post by royalez on 2006-10-30
hi all
sorry to bother everyone with me newbie questions but i can not run the et.run file in the terminal i type the filename et-linux-2.56-2.x86.run in my terminal and it comes back (bash: et-linux-2.56-2.x86.run: command not found) the file is in my home directory
is there something that i am not typing before the filename?

---

### Post by Darkfrost101 on 2006-11-03
Hi everyone, im pretty new to linux, but im pretty good with computers (Well, my IT teachers at school ask me for help with stuff.... so funny :D)

I tried to install ET, and im having a few problems, i have it all installed fine, but its runs stupidly slow, so im trying to install the ATI drivers thingy :)

I have a ATI Radeon Xpress 200M, which i think needs the drivers, and im having a spot of trouble installing them, im using Dapper, and i got to this bit:


root@jacob-laptop:/home/jacob# sudo apt-get update
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release.gpg [189B]
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release
Get: 4 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/universe Packages
Fetched 4B in 8s (0B/s)
Reading package lists... Done

I noticed the
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release.gpg [189B]
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get: 4 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]

What do i do here?
I think its meant to download and install them automaticly.. But no matter how many times i do it, they are still there....
Any help please?

Thanks, Darkfrost :)

---

### Post by Theimon on 2006-11-04
> **royalez said:**
> hi all
sorry to bother everyone with me newbie questions but i can not run the et.run file in the terminal i type the filename et-linux-2.56-2.x86.run in my terminal and it comes back (bash: et-linux-2.56-2.x86.run: command not found) the file is in my home directory
is there something that i am not typing before the filename?

You have to make it executable. do the following in the terminal:
```
chmod +x et-linux-2.56-2.x86.run
``` 
and then run nthe script again. 
[SIZE="1"](this info could be read in the first post of this topic.....)[/SIZE]

---

### Post by lespea on 2006-11-05
Here's an odd problem I'm experiencing. I installed ET just fine using sudo and the script, then launched it and my sound worked out of the box... !!!. But here's the kicker... every 30 seconds or so the game will hang for about 1 to .5 seconds. Now this might not seem like a "big deal" but I started loosing firefights a lot because I would freeze at the worst possible times.

So anyways I launched et through the console and waited at the menu until it "froze" then immediately quit. There was nothing shown that indicated a single thing had happened! Does this mean that it's a problem with my install and not the game or something?

---

### Post by Gujs on 2006-11-05
Hello,

I installed the game, it works great! But i have a problem when I exit the game. My desktop stays on the same resolution, that et was played ( 1024x768 ) and don't go back to 1600x1200. I have to restart X to get it back.

I have an ati Radeon 9500 card? 
Please help, it is really annoying!

Gujs

---

### Post by Theimon on 2006-11-05
> **Gujs said:**
> Hello,

I installed the game, it works great! But i have a problem when I exit the game. My desktop stays on the same resolution, that et was played ( 1024x768 ) and don't go back to 1600x1200. I have to restart X to get it back.

I have an ati Radeon 9500 card? 
Please help, it is really annoying!

Gujs

I have the exact same thing. I don't restart X though. When you go to System - Preferences - Screen Resolution, adjust the resolution there. it will give you a dialogue if you want to keep the old setting or take on the new one. Click "Keep old resolution" and it will revert back to your original res. In your case 1600x1200.

---

### Post by Gujs on 2006-11-05
Thanks for the hint!

How about specifying refresh rate to et. I have Syscmaster monitor which is giving me a horrible sound when refresh rate specified to 60Hz. I would like to have it at least 85Hz!

Thanks

---

### Post by Theimon on 2006-11-05
> **Gujs said:**
> Thanks for the hint!

How about specifying refresh rate to et. I have Syscmaster monitor which is giving me a horrible sound when refresh rate specified to 60Hz. I would like to have it at least 85Hz!

Thanks

I'm afraid I can't answer that one.


Edit: Anyone found a good working Minimizer for ET? I found etswitch through some searching but version 0.1.8 won't compile en version 0.1.14 crashes my X, making me have to do "dpkg-reconfigure xserver-xorg" to get my settings back. Any suggestions?

---

### Post by justinjstark on 2006-11-10
Just an FYI: Here's a nice quick bittorrent download of ET for anybody interested.

[http://www.bittorrent.com/detail.html?infohash=243223AE5A39909DB07A338980F00DD868251F05&per_page=10&search=linux&index=9](http://www.bittorrent.com/detail.html?infohash=243223AE5A39909DB07A338980F00DD868251F05&per_page=10&search=linux&index=9)

---

### Post by Jimmey on 2006-11-21
For the ET minimiser question, there's a bit of a hack-ish solution. 

It only really works if you have more than one user account on the Ubuntu machine (so if you're desperate, you might want to set up a new one).

Right. You've logged in to one of your user accounts. Before you play ET, press CTRL + ALT + L. This will lock your screen. A small menu will pop up, from which you can select "switch user".

When you do this, it doesn't matter which user you select. If you hit "Okay", a GDM screen will pop up. You can log in, now (either as your seperate user, or as yourself, again.) Once you're logged in, you can use CTRL + ALT + F7 to revert back to your previous login. Unlock the screen.

Now, when you want to switch, you can press CTRL + ALT + F10(you might have to check this, but I'm pretty sure it's on TTY10. If this doesn't work, try CTRL + ALT + F8-11).

This works in-game.

---

### Post by Theimon on 2006-11-23
It is kinda hack-ish, but it seems like the only possible way. Too bad there isn't a Linux equivalent to the Windows minimizer and this is one of those moments where I can kick myslef for being unable to program/code anything. Otherwise this would be the first thing I'd build.
Anyway, thx for the suggestion :)

---

### Post by qrm on 2006-11-23
have the resolution problem too...

Someone previosly asked how to specify refreshrate in ET:
type into ingame terminal (shift + tilde)

/r_displayrefresh 100

---

### Post by g33knik on 2006-12-01
I have downloaded et-linux-2.55.x86.run. When I goto terminal and use the sudo command before et-linux-2.55.x86.run, (and i am going to where the file is stored), I get "chmod: cannot access `et-linux-2.56-2.x86.run': No such file or directory". Any thoughts.

---

### Post by thelostsoul on 2006-12-02
If I may, I'd like to post my guide to installing the current version of ET...
The full linux install guide:

*Preliminary: Ensure your proper graphics card drivers are installed and that they support OpenGL.*


**1.  Download ET 2.60:**
```
wget "http://ftp.freenet.de/pub/4players/hosted/et/official/et-linux-2.60.x86.run"
```

**2.  Install ET:**
```
chmod +x et-linux-2.60.x86.run
sudo ./et-linux-2.60.x86.run
```
[i]NOTE: MAKE SURE THE INSTALL DIRECTORY IS "/usr/local/games/enemy-territory"
RECOMMENDED: Install using default settings[/i]

**3.  Update to 2.60b:*** *RECOMMENDED, BUT NOT NECESSARY**
```
wget "http://ftp.freenet.de/pub/4players/hosted/et/official/ET-2.60b-linux.zip"
unzip ET-2.60b-linux.zip -d ~/Desktop/260b
cd ~/Desktop
sudo cp "/usr/local/games/enemy-territory/et.x86" "/usr/local/games/enemy-territory/et.x86.bak"
sudo cp "/usr/local/games/enemy-territory/etded.x86" "/usr/local/games/enemy-territory/etded.x86.bak"
sudo cp "260b/Enemy Territory 2.60b/linux/et.x86" "/usr/local/games/enemy-territory/et.x86"
sudo cp "260b/Enemy Territory 2.60b/linux/etded.x86" "/usr/local/games/enemy-territory/etded.x86"
```
(hopefully you can figure out how to revert back to 2.60 if needed based on the 3rd and 4th steps from the bottom)

**4.  Fix your link:** [i](skip if using KDE)
NOTE: This step recommended only to avoid future update confusionsm it is not necessary[/i]
	_In GNOME:_
		Right click on your menu and hit "Edit Menus"
		Click "other" on the left
		Right on "enemy-territory" in the right and hit "Properties"
		Highlight the entire content of the "Command" box, hit your delete key
		Type "sudo et" into the "Command" box
		Check the "Run command in terminal" checkbox
	_In KDE:_
		*To be created.  Post if you can figure out how to duplicate the GNOME steps in KDE.  I only use GNOME.*

**5.  Update PB:** **Necessary to play on many servers**
```
sudo rm -r /root/.etwolf/pb
sudo rm -r ~/.etwolf/pb
cd /usr/local/games/enemy-territory/pb
sudo chmod +x pbweb.x86 
sudo ./pbweb.x86
```
	[i]NOTE: This step may take a very long time
	NOTE: When you attempt to connect to a server, you will be asked to re-enable punkbuster.  Click "Enable PunkBuster"
	NOTE: If you continue to receive update errors in-game, visit this site to update manually:
		[http://evenbalance.com/index.php?page=pbsetup.php](http://evenbalance.com/index.php?page=pbsetup.php)	[/i]

**6.  Run ET:**
	_In GNOME:_ Applications -> other -> enemy-territory
	_In KDE:_ Type "sudo et" in a console window
	_In a terminal window:_ Type "sudo et" in a console window


@g33knik, try my method, but substitute the 2.60/.60b steps/links accordingly...

---

### Post by haxer on 2006-12-03
This setup of yours deosnt work for me .. sudo cp steps came back with errors !!

---

### Post by thelostsoul on 2006-12-03
These?
> sudo cp "/usr/local/games/enemy-territory/et.x86" "/usr/local/games/enemy-territory/et.x86.bak"
sudo cp "/usr/local/games/enemy-territory/etded.x86" "/usr/local/games/enemy-territory/etded.x86.bak"
sudo cp "260b/Enemy Territory 2.60b/linux/et.x86" "/usr/local/games/enemy-territory/et.x86"
sudo cp "260b/Enemy Territory 2.60b/linux/etded.x86" "/usr/local/games/enemy-territory/etded.x86"

And all of them?

Did you install to /usr/local/games/enemy-territory?

And if you're refering to only the last 2 of them, then did you do the step before them... cd ~/Desktop?

Assuming you installed 2.60 into /usr/local/games/enemy-territory, you should be able to copy and paste those lines exactly...

---

### Post by thelostsoul on 2006-12-03
Attached to this message is a script I made to run and use as an installation. ** If you read the Read Me and follow it 100%, you should have no problems at all.**

However, the script doesn't perform steps 4 or 6 on my original guide, so if you want to start the game using the shortcuts on your computer, perform them accordingly.  Otherwise I recommend you start ET in the console by typing "sudo et".

---

### Post by ~LoKe on 2006-12-03
I tried to manually set my resolution in the config file to 2560x1024, to run it on dual monitors, but it didn't work.

Anyone know how?

---

### Post by thelostsoul on 2006-12-03
You want the game to show up part on one screen and part on the other?

I'm not sure that's possible, but your best bet is probably to check the ET website:
[http://enemy-territory.com](http://enemy-territory.com)

I have never heard of this being done, so I really don't think its possible, its worth a look if you really want to do it...

---

### Post by Jimmey on 2006-12-04
You shouldn't need to sudo et.

---

### Post by thelostsoul on 2006-12-04
> **Jimmey said:**
> You shouldn't need to sudo et.

As I said in my original post, it isn't necessary, but PunkBuster has issues update if you don't sudo ET, and you'll likely be kicked.  It's just to avoid possible complications...

---

### Post by Theimon on 2006-12-06
You can update Punkbuster by using a small tool available at punkbuster's website ( [http://websec.evenbalance.com/downloads/linux/pbsetup.run](http://websec.evenbalance.com/downloads/linux/pbsetup.run) ). Run the script as sudo, it will show you some sort of dialog, point the program to all your ET folders (/usr/local/games AND ~/.etwolf), click update and it will check your installs and update when needed.
I had some punkbuster-trouble myself when playing on our clan server, after using this little prog the game worked like a charm. :)
So no need to do "sudo et"

---

### Post by ~LoKe on 2006-12-06
> **thelostsoul said:**
> You want the game to show up part on one screen and part on the other?

I'm not sure that's possible, but your best bet is probably to check the ET website:
[http://enemy-territory.com](http://enemy-territory.com)

I have never heard of this being done, so I really don't think its possible, its worth a look if you really want to do it...

Yeah, that's how I've got UT2004 running.

---

### Post by thelostsoul on 2006-12-06
@Theimon: You are right, to an extent.  I did mention that updater and use it in the script I made, however, PB is a very strange program, and I had an issue where it was trying to remove a file from my PB directory, but couldn't because I wasn't su...therefore after PB sent a bunch of errors to the console, I was kicked.  This was after using the updater, mind.

Therefore, I will continue to recommend using "sudo et", stating that it is not necessary, but a way to avoid possible confusions in the future.


@Loke:  Well, ET is based on the Quake III engine, which I believe is older than the UT04 engine (don't hold me to that one though), but it still may be possible, I just have never heard of this being done.  ET is a fairly old game and not overly advanced (compared to today's games).  However, as I said before, its probably best to check the enemy-territory.com forums for this.  Just make sure you have the latest drivers installed for your card.  I know the latest Nvidia's support dual-screens, I just don't know if ET does...

---

### Post by BLAST3R on 2006-12-08
I am keeping running into this error:
```

root@redefining-webdesign:/home/server1# sudo sh ./et-linux-2.60.x86.run
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.60 Full Install..............................................................................................................................................................................................................................................................................................................................
./setup.sh: line 191: /root/.setup6493: No such file or directory
./setup.sh: line 191: /root/.setup6493: No such file or directory
root@redefining-webdesign:/home/server1#

```

Any suggestions :(?

It is ment to be installed as dedicated server (on my server system). (So console installation)
I won't PLAY on it, but just run the dedi..

---

### Post by thelostsoul on 2006-12-11
Sorry about my late response here, but did you chmod +x it?

You may want to try using my script to install unless you plan on installing it to a directory other than /usr/local/games/enemy-territory (in which case you could alter the script if you know how...)

---

### Post by BLAST3R on 2006-12-11
Thanks for your reaction!
I will try your script as soon I have received my RAM :) 

Thanks already!
Blast3r

---

### Post by BLAST3R on 2006-12-11
Nope! The same error as above!!

It doesn't seem to be able to create a folder :S?:mad:

---

### Post by thelostsoul on 2006-12-11
Okay, here's what I'm seeing as possible issues:

/root/ does not exist.  This should be your root account's home folder thought and since you are logged in as root, it should exist.

You do not have access to the /root/ folder.  Since you are logged in as root, you should be able to access all files, however.  My guess is either something is altering in your system, possibly requiring a reinstall, or you need to chown the directory.


Basically, just make sure /root/ exists and that the root user can edit it with full privs.

---

### Post by BLAST3R on 2006-12-11
I am logged in as sudo -i.
I've already chown'ed the directory to everyone's access.
The folder exists..

The only special about my ubuntu installation, is that I use the server version, without graphical interface, and it is **64BIT!**

Maybe that's part of the cause of this problem?

I already saw others having this problem.

But I have a chance it works after a reinstall?

Maybe I WILL do a re-install when I have my S-ATA harddrive :).

But i'll try to reinstall.. 
Any other things I can try if it doesn't work?:)

---

### Post by thelostsoul on 2006-12-11
Oh, so you are doing all of this via the command line and you have no gdm?

If that's the case, then you will be unable to install ET because they have a graphical installer.

You may be able to use the 2.55 installer though (from what I remember it was entirely command based).


However, I do believe that the 64bit issue is a problem.  I have a friend who said he could not install ET because of this problem.  He said he was going to install the 32bit version, however, and see what happens.  I'll let you know what he says...

I'll also ask him if that's the error he gets when installing.

---

### Post by rko618 on 2006-12-12
Installation seemed to go fine however when I attempt to run the game it crashes Xorg.  I have noticed other games like Tuxtyping do this too and I have to run the games not a full screen.  So if I had a guess I'd say my configuration has problems whenever it tries to run something full screen.

My setup:
Nvidia 7900gs
Ubuntu 6.10 64-bit
Using Nvidia beta driver

Any ideas?

---

### Post by Theimon on 2006-12-12
As far as I know, ET is a 32bits application. I have had Ubuntu 64bits installed but for ET I had to create/emulate a 32bit environment for it to work (which it didn't).
I reverted to the i386 version of Ubuntu. The amount and quality of software and drivers for the 64bits version are too small at this point to be installed on a production machine.

@rko618: same goes for you regarding the 64bits part, but maybe take a look at the video driver. You state it is a beta so try a regular release

---

### Post by ~LoKe on 2006-12-12
> **rko618 said:**
> Installation seemed to go fine however when I attempt to run the game it crashes Xorg.  I have noticed other games like Tuxtyping do this too and I have to run the games not a full screen.  So if I had a guess I'd say my configuration has problems whenever it tries to run something full screen.

My setup:
Nvidia 7900gs
Ubuntu 6.10 64-bit
Using Nvidia beta driver

Any ideas?

You need the new beta driver, 9631 I think.

---

### Post by thelostsoul on 2006-12-13
9631 is the current official version as of December 4, 2006.  So installing from nvidia.com will give you the 9631 version.

The current beta, 97xx is only to add support for the Nvidia 8 series cards and will likely be of no use.

---

### Post by Hubris2 on 2007-01-03
Any more thoughts on missing sound?  I've followed just about every tip I've been able to read, and nothing has worked.  I get " /dev/dsp: Input/output error
Could not mmap /dev/dsp "

I can kill esd, follow the 
sudo -i
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
exit

or anything else....I simply get no sound in the game.  Sound works fine otherwise.

Anything else I can try?

---

### Post by gcamaro32 on 2007-01-31
I am a complete noob at linux so forgive me if this question has already been answered or i'm making an obvious mistake.

Below is what i attempted step by step to get ET installed, but as you'll see, i get an error every single time. I'm hoping for some help by supplying what i did step by step. 

```
gh057@gh057-desktop:~/Desktop$ ./et-linux-2.55.x86.run 
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.55...........................................................................................................................................................................................................................................................................................................
It is recommended to install as the super user
Please enter the root password or hit enter to continue as is
Password: 
su: Authentication failure
Sorry.
/home/gh057/.setup32742: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
The setup program seems to have failed on x86/glibc-2.1

See http://zerowing.idsoftware.com/linux/ for troubleshooting
gh057@gh057-desktop:~/Desktop$ chmod +x et-linux-2.55.x86.run 
gh057@gh057-desktop:~/Desktop$ su -c "./et-linux-2.55.x86.run" 
Password: 
su: Authentication failure
Sorry.
gh057@gh057-desktop:~/Desktop$ sudo -i
Password:
root@gh057-desktop:~# cd /home/gh057/Desktop/
root@gh057-desktop:/home/gh057/Desktop# ls
et-linux-2.55.x86.run
root@gh057-desktop:/home/gh057/Desktop# ./et-linux-2.55.x86.run 
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.55...........................................................................................................................................................................................................................................................................................................
/root/.setup462: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
The setup program seems to have failed on x86/glibc-2.1

See http://zerowing.idsoftware.com/linux/ for troubleshooting
root@gh057-desktop:/home/gh057/Desktop# chmod +x et-linux-2.55.x86.run 
root@gh057-desktop:/home/gh057/Desktop# su -c "./et-linux-2.55.x86.run" 
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.55...........................................................................................................................................................................................................................................................................................................
/root/.setup554: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
The setup program seems to have failed on x86/glibc-2.1

See http://zerowing.idsoftware.com/linux/ for troubleshooting

```

---

### Post by Theimon on 2007-01-31
> **gcamaro32 said:**
> 

```
gh057@gh057-desktop:~/Desktop$ ./et-linux-2.55.x86.run 
/root/.setup554: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
The setup program seems to have failed on x86/glibc-2.1


```

Open up Synaptic and search for GTK. There are 2 versions namely: 1.2 and 2.0. The latter is installed by default being a more recent release. Install libgtk+1.2 as well and then rerun the ET installation:
```
sudo ./et-linux-2.55.x86.run
```

---

### Post by gcamaro32 on 2007-01-31
THANK YOU! 

As frustrated as i am because it seemed so simple, i am very appreciative.

---

### Post by Theimon on 2007-01-31
> **gcamaro32 said:**
> THANK YOU! 

As frustrated as i am because it seemed so simple, i am very appreciative.

Happy killing 8-)

---

### Post by adza on 2007-02-06
I have successfully installed ET, having successully accquired my first couple of linux frags! hehe (playing as 1lll33t1st_linux).. i've experienced similar issues during install etc as described in this thread and have all been resolved, however i have one final problem (sort of) that is now bugging me.... 

I am running an apple 20" cinema widescreen display and there isn't a resolution setting in the options that fits my display size.. in windows, the graphics card seems to accomodate for this and fits the game to the screen size automatically... Is there a way i can either a) force ET to run at 1650 * 1080
               b) do the same 'fit to screen' type of adjustment that happens in windows?

This is not a huge issue, as i am playing at standard res no probs, merely an annoyance, any help here would be sweet :)

---

### Post by Theimon on 2007-02-06
Maybe you can force it by creating an autoexec.cfg. Go to your ~/.etwolf folder, create a new empty document, and place the following in it: ```
seta r_customwidth "1650"
seta r_customheight "1080"
```
Save the file as autoexec.cfg and exit. Then start ET, it will automatically look for the autoexec file and use the settings. If you think it didn't pick up anything, open the in-game console (with ~) and type /exec autoexec.cfg

---

### Post by adza on 2007-02-06
sweet, i will try that.. i've tried adding cg_setview 100 to the autoexec last night, but it didn't seem to do anything... i will try when i get home (as i'm posting from work at the moment hehe - i'm just watching scripts run at the minute anyway!)

---

### Post by adza on 2007-02-07
nope... no good unfortunately.... :S

---

### Post by jharris on 2007-02-07
@adza, you've entered the wrong settings m8 - it's 1680 x 1050 for a 20" Widescreen ;) When playing W:ET, drop down the console and type in:
```
r_mode -1
r_customheight 1050
r_customwidth 1680
vid_restart
```
Now all should look good. Using 1650 x 1080 will give you some weird image displacement, plus the r_mode being set to -1 will suit the widescreen's field of view more appropriately.

---

### Post by Theimon on 2007-02-07
I forgot the r_mode -1, I even copied those from my own autoexec.....hmmm....oh well, it was 4AM at that time... ;)

---

### Post by adza on 2007-02-08
thx gi's :) .... i know i got the res wrong... entered in the autoexec correctly however, didn't do the r_mode -1 thingy though... will give that a go.... :P

---

### Post by adza on 2007-02-08
oh yes... fraggin away nicely... thanks guys!

---

### Post by jimbo2150 on 2007-02-10
Ahh! ET NO MORE!

After that last patch update (which I noticed has some 'linux' core updates) has broken my ET!

Whenever I go to run the program, the window showing with just black inside pops up for a split-second then disappears (I assume crashed). No 'crash' message appears though.

Anyone else getting this problem after the recent patch update? Any fixes?

---

### Post by Theimon on 2007-02-10
> **jimbo2150 said:**
> Ahh! ET NO MORE!

After that last patch update (which I noticed has some 'linux' core updates) has broken my ET!

Whenever I go to run the program, the window showing with just black inside pops up for a split-second then disappears (I assume crashed). No 'crash' message appears though.

Anyone else getting this problem after the recent patch update? Any fixes?

Try running it from terminal and see if it leaves any error messages.

---

### Post by jimbo2150 on 2007-02-10
> **Theimon said:**
> Try running it from terminal and see if it leaves any error messages.
Found out: Could not load openGL.

This update broke my driver install. It is reporting MESA again. Gatta look into that. Thanks.

---

### Post by adza on 2007-02-10
I am currently getting 50-60 fps in linux but in my winblows install it consistently runs 90+ fps? is there anyway that i could increase the performance in linux? i have the latest nvidia drivers etc...

---

### Post by Marktrix on 2007-02-25
Hello,

i installed the game it runs :)

But i have Version 2.6, the most server want 2.6b

So i downloaded the patch and copyed it into the games folder.

After that i always get kicked by the punkbuster :( 

EDIT: Reinstall punkbuster , now works fine

---

### Post by bingo87 on 2007-03-20
> **Marktrix said:**
> Hello,

i installed the game it runs :)

But i have Version 2.6, the most server want 2.6b

So i downloaded the patch and copyed it into the games folder.

After that i always get kicked by the punkbuster :( 

EDIT: Reinstall punkbuster , now works fine

I have the same problem, but i don't know how to reinstall Punkbuster on ubuntu :s.
can someone help me with this?

greetz,
bingo87

---

### Post by TH3_D0ct0R on 2007-03-22
ok i went thro all 20 pages of this HOW TO and no one else seemed to have the check sum problem
```
william@william-desktop:~$ sudo ./et-linux-2.60.x86.run
Verifying archive integrity...Error in MD5 checksums: 297e5edcd66316bf2eabd4492e8e0f45 is different from b8b59bc515d86cc845fb52f5d2c14423

```
idk what to do
 you can yell at me tell me im a dumb noob if ya want...cuz i prolly messed sumthing up...i just wanna know how to install it

thank you
[INDENT]TH3_D0ct0R[/INDENT]

EDIT: I FIXED IT!!!!!!!!!!!!!! I just right clicked on it and went to permissions and made it executable by everyone and then hit cancel and double clicked it and it openned up the installer...still running but it looks good...fill ya in lata

---

### Post by TH3_D0ct0R on 2007-03-23
alright..i got it workin...and im a noob...so ill tell all the other noobs who are at the end of this thread and are all like :confused: 

first off i downloaded the et-linux-2.60.x86.run from 

[http://www.truecombatelite.net/component/option,com_remository/Itemid,40/]("http://www.truecombatelite.net/component/option,com_remository/Itemid,40/") 

it took me about two hours...next i right-clicked on the file and i went to permissions and then made it executable by everyone...then i hit the cancel button and then double clicked on the file and it brought up an error message asking me what to do with ithis file...the options were "run in terminal", "display", "cancel", and finally "run"
 i hit the run button and a GUI popped up and said...verifiying archive...............(with the periods :P) and then brought me threw the steps

I DID MESS UP THO!!! i installed it into my home folder rather than /usr/games/et---but that wasnt too bad it took me a little while to find it tho (i just had to do a search of the system)

but i started it up and there was no sound so i followed the directions at the begining of this post
and at this website 

[http://www.katanoon.nl/ubu-e/install.php]("http://www.katanoon.nl/ubu-e/install.php")

under the "Fixing sound issues" section
that fixed the sound issue but i still couldnt get into any servers becuase it said i didnt have punkbuster... so i went to this website 

[http://evenbalance.com/index.php?page=pbsetup.php]("http://http://evenbalance.com/index.php?page=pbsetup.php") 

and downloaded the pbsetup.run (and again had to go into properties and change it to executable) i followed the instructions on the website to add a game and punk buster for it (i had to update it twice)

and then i played....and i suck at it :(:P but it doesnt matter cuz it was fun


lucky fraggin
[INDENT]TH3_D0ct0R[/INDENT]

...ps if you have any question feel free to reply or send me a pm w/e (its better to reply so everyone can benefit from the knowledge gained...

---

### Post by corevette on 2007-03-25
Adza - i'm also having the same problem....

i receive a moderate FPS rate.....with an ATI X1300.

but when i play the game on windows with a 128 mb video card...it runs very smoothly...any way to fix this?

---

### Post by bravemosquito on 2007-03-27
Help! I just realized when tried to play ET 2.60b online (root or non-priv. user) the serverlist isn't refreshing again. Just I suspected the reason is iptables. Now I'm using iptables 1.3.6 on Feisty and even flushing them (iptables -F) doesn't help... :confused:

Also I have a bug which makes cpu on 100% load and games control freezes:

[[IMG]http://img48.imageshack.us/img48/460/etbuggs8.th.jpg[/IMG]](http://img48.imageshack.us/my.php?image=etbuggs8.jpg)

---

### Post by lakersforce on 2007-04-14
Whenever I play, after a while the game terminates with a "signal 11"...and thats if Im lucky...most of the time my computer just freezes. Any suggestions?

I remember once I had 6.06 ET ran fine, but not on 6.10 or 7.04.

---

### Post by kane77 on 2007-04-19
I have problem installing. when I try to run the installer I get this: 
```

root@kane-desktop:/home/kane# ./et-linux-2.60.x86.run 
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.60 Full Install...........
..................................................................................................
............................................................................................
........................................................................................................
.............
./setup.sh: 278: /root/.setup9339: not found
./setup.sh: 289: /root/.setup9339: not found

```

this happens when I run the installer as any user (myself or root) the numbers are different each time (of the .setupXXXX)

I am running amd64 feisty (kernel 2.6.20-15)... Last time I installed (it was on dapper amd64, there were no problems...)

---

### Post by tehbr0ken on 2007-04-19
So I tried installing it and this is what I get so far:

root@Br0ken:/home/dan/Desktop/tcetest# sudo ./et-linux-2.55.x86.run Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.55...........
This installation doesn't support glibc-2.0 on Linux / unknown
(tried to run setup)
See [http://zerowing.idsoftware.com/linux/](http://zerowing.idsoftware.com/linux/) for troubleshooting
The setup program seems to have failed on unknown/glibc-2.0

See [http://zerowing.idsoftware.com/linux/](http://zerowing.idsoftware.com/linux/) for troubleshooting
root@Br0ken:/home/dan/Desktop/tcetest#

any suggestions???

---

### Post by bravemosquito on 2007-04-19
> **tehbr0ken said:**
> any suggestions???

Yeah, use 2.60

---

### Post by Archel on 2007-04-20
I keep getting the 'su Authentication Failed' message. Any help?

---

### Post by lakersforce on 2007-04-21
> **BLAST3R said:**
> I am keeping running into this error:
```

root@redefining-webdesign:/home/server1# sudo sh ./et-linux-2.60.x86.run
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.60 Full Install..............................................................................................................................................................................................................................................................................................................................
./setup.sh: line 191: /root/.setup6493: No such file or directory
./setup.sh: line 191: /root/.setup6493: No such file or directory
root@redefining-webdesign:/home/server1#

```

Any suggestions :(?

It is ment to be installed as dedicated server (on my server system). (So console installation)
I won't PLAY on it, but just run the dedi..

I found the solution! Look here: [http://ubuntuforums.org/showthread.php?t=416871](http://ubuntuforums.org/showthread.php?t=416871)

---

### Post by whirl on 2007-05-02
um heya o/

I appreciate all the comments here for they got me started with this..

So the thing is I can go into etpro server but in matter of seconds it kicks me out saying "Violation (Game integrity) #20006"

It has something to do with the pb cause it might not get connection or something.. So I tried to dl this pbsetup.run but I cant run it 

comp@comp:~$ cd /home/comp/Download
comp@comp:~/Download$ sh pbsetup.run
pbsetup.run: 18: Syntax error: "(" unexpected
comp@comp:~/Download$

What should I do?

Thanks mates o/

---

### Post by TH3_D0ct0R on 2007-05-02
whirl 
about the pbsetup go to this website [http://www.evenbalance.com/index.php?page=pbsetup.php]("http://www.evenbalance.com/index.php?page=pbsetup.php") 
dl the linux one and then right click and go to properties and set it as executable for all users and it should work

if it doesnt work tell me...

p.s. also on the website is how to use the pb setup (if you need help w/ that)

---

### Post by kenji4life on 2007-05-05
I run the file, et-linux-2.60.x86.run from my desktop (all permissions read/write) 
i run straight and it opens a windowed terminal which says verifying file integrity... 
it stays open for a second and then the window closes and nothing happens. 

I am running 7.04 on an amd athlon 1.4 ghz with 768 mb ram and a 20 gb hard drive
clean install, pretty much unmodified
I am trying to install ET and ETF so that I can host my clan's ETF server on my fios connection.

dedicated is only thing I'll be using, as I don't need/want to game on this machine.

Any help would be great. 

Thanks

P.S. running the etf 1.6 file does the exact same thing so I think I'm doing something wrong??

---

### Post by Theimon on 2007-05-06
> **kenji4life said:**
> I run the file, et-linux-2.60.x86.run from my desktop (all permissions read/write) 
i run straight and it opens a windowed terminal which says verifying file integrity... 
it stays open for a second and then the window closes and nothing happens. 

I am running 7.04 on an amd athlon 1.4 ghz with 768 mb ram and a 20 gb hard drive
clean install, pretty much unmodified
I am trying to install ET and ETF so that I can host my clan's ETF server on my fios connection.

dedicated is only thing I'll be using, as I don't need/want to game on this machine.

Any help would be great. 

Thanks

P.S. running the etf 1.6 file does the exact same thing so I think I'm doing something wrong??

So you run the file by doubleclicking it? Try to run it from the terminal, that way you can pick up errors as you go. I'm thinking this might mean your system lacks glib1.2 but we can't know for sure at this time.

---

### Post by WishMaster on 2007-05-09
I have a dual boot: WinXP - Ubuntu Feisty
I have ET on both OS'es.

Now I am downloading all the playermaps in duplicate: playermap in windows and the same one in Ubuntu.

Isn't is possible to "redirect" my Ubuntu-playermaps to the windows one? (with a symlink or so?)

I can mount my Windows-ET-folder: /mnt/F-schijf/Games/Enemy Territory (which is NTFS...)

Any suggestions?

---

### Post by fakie_flip on 2007-05-09
try it and see what happens. if it doesnt work, then remove the symbolic links. you might want to copy them over to save yourself time from downloading.

ln -s /windows/path/to/playermap.pk3 /home/yourusername/.etwolf/somewhere_in_here

---

### Post by fakie_flip on 2007-05-09
> **whirl said:**
> um heya o/

I appreciate all the comments here for they got me started with this..

So the thing is I can go into etpro server but in matter of seconds it kicks me out saying "Violation (Game integrity) #20006"

It has something to do with the pb cause it might not get connection or something.. So I tried to dl this pbsetup.run but I cant run it 

comp@comp:~$ cd /home/comp/Download
comp@comp:~/Download$ sh pbsetup.run
pbsetup.run: 18: Syntax error: "(" unexpected
comp@comp:~/Download$

What should I do?

Thanks mates o/

./pbsetup

did you install the game as root? if so do this

sudo ./pbsetup

---

### Post by _mikko_ on 2007-05-09
Hi! i got this problem when i'm connecting to server. I can't heard sounds. Could someone help me?

------- sound initialization -------
/dev/dsp: Invalid argument
Could not open /dev/dsp
------------------------------------
Sound memory manager started
Sys_LoadDll(/home/mikko/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/mikko/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/mikko/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xee115f40  
Sys_LoadDll(ui) succeeded!
--- Common Initialization Complete ---
Opening IP socket: localhost:27960

My sounds works normaly, I can listen music etc. 
My ubuntu is feisty.
I have amd 64bit.
I would be very thankful if someone could solve my problem.

Mikko

---

### Post by fakie_flip on 2007-05-11
> **_mikko_ said:**
> Hi! i got this problem when i'm connecting to server. I can't heard sounds. Could someone help me?

------- sound initialization -------
/dev/dsp: Invalid argument
Could not open /dev/dsp
------------------------------------
Sound memory manager started
Sys_LoadDll(/home/mikko/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/mikko/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/mikko/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xee115f40  
Sys_LoadDll(ui) succeeded!
--- Common Initialization Complete ---
Opening IP socket: localhost:27960

My sounds works normaly, I can listen music etc. 
My ubuntu is feisty.
I have amd 64bit.
I would be very thankful if someone could solve my problem.

Mikko

Yes, I can help. Use my script. Open a terminal with your favorite text editor. I use vim, but you might want to use something easier like nano or gedit.
```

gedit start-et &
```

Copy and paste this code, and then click save in gedit.

```
#!/bin/bash
if [[ ! $(grep 'et.x86' /proc/asound/card0/pcm0p/oss) ]]; then
 gksudo "bash -c 'echo \"et.x86 0 0 direct\" >> /proc/asound/card0/pcm0p/oss'"
fi
if [[ ! $(grep 'et.x86' /proc/asound/card0/pcm0c/oss) ]]; then
 gksudo "bash -c 'echo \"et.x86 0 0 disable\" >> /proc/asound/card0/pcm0c/oss'"
fi
et
exit 0
```

Now go back to the terminal. Make the script executable.

```
chmod -c u+x start-et
```

Now run the script from terminal to test it.

```
./start-et
```

If it worked, open Alacarte menu editor. Run in terminal:

```
alacarte &
```

Look in Games under Applications and find Enemy Territory. Right click it and choose edit. Change the command that it runs. Choose browse and find the script. After that, click okay on everything.

Also don't have other apps that use the sound like Amarok and Skype opened while playing et because they can take the sound away from et.

---

### Post by Yellowbelly on 2007-05-29
I just downloaded ET so I could play True combat or whatever and I have the et 2.55 game full wilth the 2.6 patch needed to playTCE. I'm used to installers and I have no clue whatsoever with this text based stuff. So far I have the .run file in my home folder (/home/bripod) and now I don't know what to do. 1st page of the thread says to put such and such code in but nothing works remotely. Why can't they make installers for everything just like windows? Linux will never become a mainstream OS until it's somewhat easy to use.

---

### Post by Shadowmeph on 2007-05-31
ok I followed the instruction I get to a point and then receive this error 

&#9472;&#9472; Failed permissions 
No write permission to /usr/local/games   

oh and as if you can't tell I am a total nooby with this OS I am a windows guy slowly moving to this I just wanted to try playing ET through feisty fawn because I heard that playing through linux is much better then playing through windows. anyway any help would be greatly appreciated

---

### Post by Yellowbelly on 2007-05-31
I found an easier way. If you go to the .run's properties, I forgot which tab it's under but you can select to run it as an executable file so check that and start it up and it'll install it just fine. Now the problem with me is that I can't get the 2.60b update to play TC:E. For some reason it doesn't want to run or open or do anything.

---

### Post by Shadowmeph on 2007-05-31
> **Yellowbelly said:**
> I found an easier way. If you go to the .run's properties, I forgot which tab it's under but you can select to run it as an executable file so check that and start it up and it'll install it just fine. Now the problem with me is that I can't get the 2.60b update to play TC:E. For some reason it doesn't want to run or open or do anything.
I am not sure how I did it but I did finally manage to get it installed but now when I try to start it all I get is a quick flash of black screen then it goes back to my desk top not sure why that is or how to check what it is

---

### Post by Pugwash on 2007-05-31
> **fakie_flip said:**
> Yes, I can help. Use my script. Open a terminal with your favorite text editor. I use vim, but you might want to use something easier like nano or gedit.
```

gedit start-et &
```

Copy and paste this code, and then click save in gedit.

```
#!/bin/bash
if [[ ! $(grep 'et.x86' /proc/asound/card0/pcm0p/oss) ]]; then
 gksudo "bash -c 'echo \"et.x86 0 0 direct\" >> /proc/asound/card0/pcm0p/oss'"
fi
if [[ ! $(grep 'et.x86' /proc/asound/card0/pcm0c/oss) ]]; then
 gksudo "bash -c 'echo \"et.x86 0 0 disable\" >> /proc/asound/card0/pcm0c/oss'"
fi
et
exit 0
```

Now go back to the terminal. Make the script executable.

```
chmod -c u+x start-et
```

Now run the script from terminal to test it.

```
./start-et
```

If it worked, open Alacarte menu editor. Run in terminal:

```
alacarte &
```

Look in Games under Applications and find Enemy Territory. Right click it and choose edit. Change the command that it runs. Choose browse and find the script. After that, click okay on everything.

Also don't have other apps that use the sound like Amarok and Skype opened while playing et because they can take the sound away from et.


Hi, this script works well, thanks. But are you running et as root here? Isn't that unsafe?

---

### Post by Shadowmeph on 2007-05-31
to be totally honest I am a noob at this but I am following ( muddling through) your instructions and I receive this error ./start-et: line 8: et: command not found

---

### Post by Pugwash on 2007-05-31
What happens when you type "et" at the terminal?

---

### Post by Shadowmeph on 2007-05-31
> **Pugwash said:**
> What happens when you type "et" at the terminal?
I got mad and I did a total reinstall of everything I can get et up and running but with no sound also i can't find where the et directory is lol because I have a bunch of et maps I was going to load into the directory also mess with my et config but no idea where  it installed lol ok I found et its in the Other menu nut to sure why that is though

---

### Post by Pugwash on 2007-06-01
> **Shadowmeph said:**
> I got mad and I did a total reinstall of everything I can get et up and running but with no sound also i can't find where the et directory is lol because I have a bunch of et maps I was going to load into the directory also mess with my et config but no idea where  it installed lol ok I found et its in the Other menu nut to sure why that is though

Ok, firstly the et directly is located (at least for me) in /usr/local/games/ . Secondly double check the script, I think you might have pasted it in wrong.

---

### Post by userundefine on 2007-06-01
Everyone with sound problems should check [the thread]("http://ubuntuforums.org/showthread.php?t=362231") in the Gaming forum.  Nullkey has done some fabulous work and sound works brilliantly with his solution.

---

### Post by Shadowmeph on 2007-06-01
> **Pugwash said:**
> Ok, firstly the et directly is located (at least for me) in /usr/local/games/ . Secondly double check the script, I think you might have pasted it in wrong.
right on now I have sound thank you so much :) now I just have to figure out how to get all my maps from a disk into the et main directory . but the main thing is I have sound:). 
is there a linux ver of et min out there I have a simple one for windows but I don't think it will work linux, I will just do a search thank you again you made my day.

---

### Post by Danwright on 2007-06-01
i managed to install ET and get sound, but u am having a few problems, first of all i cant get the resolution right, it is either in full screen mode with 1/2 the screen black or in a window and i cannot see the whole window. i cant find any solution to this problem atthe moment... any ideas?


thanks

---

### Post by Pugwash on 2007-06-05
> **Shadowmeph said:**
> right on now I have sound thank you so much :) now I just have to figure out how to get all my maps from a disk into the et main directory . but the main thing is I have sound:). 
is there a linux ver of et min out there I have a simple one for windows but I don't think it will work linux, I will just do a search thank you again you made my day.

Glad I could could help. I've not come across et min, so I can't help you out there. I'm sure somebody here knows.

---

### Post by Pugwash on 2007-06-05
> **Danwright said:**
> i managed to install ET and get sound, but u am having a few problems, first of all i cant get the resolution right, it is either in full screen mode with 1/2 the screen black or in a window and i cannot see the whole window. i cant find any solution to this problem atthe moment... any ideas?


thanks

Have you tried going into options, and looking there?

---

### Post by Exakun on 2007-06-07
I've been playing W:ET for a while in linux and I figured I might be able to help out some people with two things.

First, DO NOT RUN THE GAME AS ROOT OR SUDO. I can't stress enough how silly this is, and how many times I've heard people say they do it. This undermines the security aspect of permissions by allowing a program that downloads files to your computer root access. Instead, chmod 777 your enemy-territory directory. That way, the game only has authority to run its own files and download files necessary for playing.

Second, for custom resolutions, there should be a file in your /.../enemy-territory/etmain directory called "autoexec.cfg". if you want a custom resolution, then it needs to contain the following:
```
set r_mode -1
set r_customwidth X
set r_customheight Y
```
Where X and Y are the width and height of your monitor in pixels, respectively. This should fix resolution problems, though making sure your video card has the proper drivers installed would also be important.

Another thing to note - I only need to do the oss direct/disable commands once between reboots. Each subsequent run has fully working sound with Teamspeak running as well. I wonder if it would be possible to invoke these on startup? It would be more practical for me than a run script.

---

### Post by galvao on 2007-06-08
Hi. I was wondering if you can help me:

I've installed my graphics card (Nvidia 6200) via envy and I keep getting the following error message whenever I try to run ET or any other 3D accelerated game:
```

...loading libGL.so.1: QGL_Init: dlopen libGL.so.1 failed: libGL.so.1: cannot open shared object file: No such file or directory 
failed
```I've already tried to create the symbolic link, as:

```

ln -s /usr/lib/libGL.so /usr/lib/libGL.so.1

```But I keep getting the same error message nevertheless.

Any thoughts?

TIA,

---

### Post by doublecheese on 2007-06-11
I'm having a hard time finding where Enemy Territory stores all the files I download.  Just about every game you try to join requires a download.  The only problem is that my Enemy Territory folder isn't getting any larger.  It's installed at "/usr/local/games/enemy-territory" and my etmain folder is isn't quite 260MB.  Where do the mods you download go?

---

### Post by galvao on 2007-06-11
Hi.

The files are stored at your home directory:

cd ~/username/.etwolf

Oh, BTW, I've got it working here. Thing is there was a huge mess involving wrong drivers, etc... The method linked in this Tutorial is EXTREMELY simple and it works!

Regards,

---

### Post by Youngviking on 2007-06-14
I tried to install it and it gave me this:

```
This installation doesn't support glibc-2.0 on Linux / unknown
(tried to run setup)
See http://zerowing.idsoftware.com/linux/ for troubleshooting
The setup program seems to have failed on unknown/glibc-2.0

See http://zerowing.idsoftware.com/linux/ for troubleshooting

```

---

### Post by galvao on 2007-06-14
Hi.

I'm not an expert, but I'd say that maybe your glibc is outdated?

Try running Synaptic and checking for upgrades, or simply typing:

```

sudo apt-get upgrade

```Important: this will upgrade your entire Ubunu installation, so be carefull if you have any specific settings on your box.

Regards,

---

### Post by PoisoN2003 on 2007-06-14
I get an error after starting the install

> poison@poison-desktop:~/Desktop$ sudo '/home/poison/Desktop/et-linux-2.55.x86.run' 
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.55...........................................................................................................................................................................................................................................................................................................
/home/poison/.setup17153: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
The setup program seems to have failed on x86/glibc-2.1



Any idea how i can fix this? i tried looking in repos but i cant find what it needs

---

### Post by Youngviking on 2007-06-14
You can't use 2.55 with an x86_64 computer, but you can install 2.60 and 2.60b.

---

### Post by hanzj on 2007-06-20
I got W:ET on my comp. Sound is working. But when I join game, i go the screen where a file/map is being downloaded. But it just stays there. Even a 22kb file stays at "Estimating time".

What's wrong?

It's not "hanging", i don't think. I can hit Esc key to go back.

---

### Post by ScreWe on 2007-06-20
i recieve a problem wen installing... i click run and the game acts like its going to open the screen turns black for a bit and then goes to the desktop... and this is the console i got as i was installing and wen i ran it

```
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed

Warning: kbuildsycoca is unable to register with DCOP.

kbuildsycoca running...

X Error: BadDevice, invalid or uninitialized input device 167

  Major opcode:  144

  Minor opcode:  3

  Resource id:  0x0

Failed to open device

X Error: BadDevice, invalid or uninitialized input device 167

  Major opcode:  144

  Minor opcode:  3

  Resource id:  0x0

Failed to open device

Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed

kbuildsycoca running...

Reusing existing ksycoca

kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"

kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop

kio (KSycoca): ERROR: No database available!

Reusing existing ksycoca

kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"

kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop

kio (KSycoca): ERROR: No database available!

Removing existing etded symlink

Installing symlink /usr/local/bin/etded -> /usr/local/games/enemy-territory/etded

Removing existing et symlink

Installing symlink /usr/local/bin/et -> /usr/local/games/enemy-territory/et

ET 2.55 linux-i386 May 27 2003

----- FS_Startup -----

Current search path:

/root/.etwolf/etmain

/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)

/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (4 files)

/usr/local/games/enemy-territory/etmain



----------------------

3729 files in pk3 files

execing default.cfg

couldn't exec language.cfg

couldn't exec autoexec.cfg

Hunk_Clear: reset the hunk ok



------- Input Initialization -------

Joystick is not active.

------------------------------------

Bypassing CD checks

----- Client Initialization -----

----- Initializing Renderer ----

-------------------------------

----- Client Initialization Complete -----

----- R_Init -----

...loading libGL.so.1: Initializing OpenGL display

...setting mode 4: 800 600

Using XFree86-VidModeExtension Version 2.2

XF86DGA Mouse (Version 2.0) initialized

XFree86-VidModeExtension Activated at 800x600

Using 8/8/8 Color bits, 16 depth, 0 stencil display.

Xlib:  extension "XFree86-DRI" missing on display ":0.0".

GL_RENDERER: Mesa GLX Indirect





***********************************************************

 You are using software Mesa (no hardware acceleration)!   

 Driver DLL used: libGL.so.1

 If this is intentional, add

       "+set r_allowSoftwareGL 1"

 to the command line when starting the game.

***********************************************************

...WARNING: could not set the given mode (4)

Initializing OpenGL display

...setting mode 3: 640 480

Using XFree86-VidModeExtension Version 2.2

XF86DGA Mouse (Version 2.0) initialized

XFree86-VidModeExtension Activated at 640x480

Received signal 11, exiting...

Press Return to close this window...
```

---

### Post by TH3_D0ct0R on 2007-06-22
@ Screwe i think the problem is this line here

```
You are using software Mesa (no hardware acceleration)!   

 Driver DLL used: libGL.so.1

 If this is intentional, add

       "+set r_allowSoftwareGL 1"

 to the command line when starting the game.


```
 you dont seem to have a video card or do not have the driver installed...if you have one install the driver(if you dont know how just ask...)...if you dont or dont know add "+set r_allowSoftwareGL 1" to the command line when starting the game..(hint hint i took it straight from that code)..

all the best

Th3 D0ct0R

---

### Post by ScreWe on 2007-06-22
i did the "+set r_allowSoftwareGL 1"


and BOY was it laggy :/...... soo

i use a ATI Radeon 9250 512 vram... so how do i go about installing the drivers?

---

### Post by blanky on 2007-06-22
Hey guys, has anyone tried using the ATI drivers installed through the 'restricted driver manager' with ET? That's how I installed my drivers (*I loved how easy it was*) and I installed and played and things look okay but it's kind of like a slide show. Also, my sound wont work. What's weird is my sound used to work fine other times that I had tried it, but that was on previous versions like on Breezy.

---

### Post by smithman89 on 2007-07-16
Okay, so i dont have this problem when i run et in dapper, it seems it only happens in feisty.  Its weird, at first my brightness would go really dark about every 10 minutes.  But now it has gotten bad, my brightness goes from 1.3 to an unknown very dark setting (unknown cause the gamma settings still say 1.3) every 2 minutes.  Is anyone having this problem?  Ive been trying everything and the thing i cant understand is that the values dont change, just the running gamma gets very dark.  Any ideas?

---

### Post by Jimmey on 2007-07-17
I have the same problem. Do you have an nVidia card?

Edit:

Well, obviously, you do. I think it's an nVidia problem. I'm going to download the nVidia configuration tools and take a look in a minute.

---

### Post by Yellowbelly on 2007-07-17
I don't have sound with the 2.6 patch. I d/led and installed 2.55 and it ran perfectly. Upgraded to 2.6 which is needed and now I don't have sound. There's a thread over on the TC:E forums on how to fix it but I don't know what it means, some guy named "glza" figured it out but I can't get on the boards because they won't activate my account for some reason. Here's the link: [http://www.truecombatelite.net/forum/viewtopic.php?t=7761&start=30](http://www.truecombatelite.net/forum/viewtopic.php?t=7761&start=30)

---

### Post by crjackson on 2007-07-18
Okay - I installed 2.6 and it has no sound.  I enabled the mouse but it also doesn't work properly (likly just a config. issue).

After reading all the problems with this game - especially the sound, I just want to remove it.

Is there a proper way to remove this thing, or do I just delete it's folders?  I don't want any garbage left behind.

Thanks...

---

### Post by XRGB48 on 2007-07-19
I have an ASRock motherboard with the onboard sound chip C-Media CM6501 that is identified as an USB sound card in FeistyFawn. At first I had no sound at all. Then I run "asoundconf set-default-card default" and now I have sound in Ubuntu. The question is how do I get EnemyTerritory to use the USB sound card?

I get this error in the console
------- sound initialization -------
/dev/dsp: No such file or directory
Could not open /dev/dsp

I thought this would help but it makes no difference
sudo su
echo "et.x86 0 0 direct" > /proc/asound/card2/pcm0p/oss

In /proc/asound I do not have card0 but I hav card1 with no pcm0c and pcm0p directories and card2 that have them.
The command ls /dev/dsp* returns /dev/dsp2

---

### Post by crjackson on 2007-07-19
> **crjackson said:**
> Okay - I installed 2.6 and it has no sound.  I enabled the mouse but it also doesn't work properly (likly just a config. issue).

After reading all the problems with this game - especially the sound, I just want to remove it.

Is there a proper way to remove this thing, or do I just delete it's folders?  I don't want any garbage left behind.

Thanks...

**[SIZE="3"]So No One knows then?[/SIZE]**

---

### Post by smithman89 on 2007-07-28
I found the answer to my own question about the brightness in Enemy Territory on Feisty.  It seems that the screensaver actually interferes with the game, being probably because et captures all buttons and mouse movements except for ctrl alt backspace.  The bug ticket i read said that you should turn your activate screensaver time delay to the maximum, 2 hours, so that it will not dim the screen.  This ensures that for at least 2 hours, your screen should stay at the brightness you want it to be.  Thank god i found this, i can finally use just feisty, instead of having to use my previous version to play et.  Happy gaming everyone!

---

### Post by Jamester64 on 2007-07-29
So how would I uninstall ET ?

---

### Post by crjackson on 2007-07-29
**@Jamester64**

As you can see I've been begging for an answer to that one, but no one seems to know.

---

### Post by darksidedude on 2007-07-29
i installed it ok but when i try to run it its not found ( everything was default)

---

### Post by Theimon on 2007-07-31
> **crjackson said:**
> **@Jamester64**

As you can see I've been begging for an answer to that one, but no one seems to know.

Just remove the folders and symlinks. If you installed everything by default that would be:
/usr/local/games/enemy-territory
/home/*username*/.etwolf
/usr/bin/et
/usr/bin/etded

(correct me if I missed out on anything.)

---

### Post by crjackson on 2007-08-01
> **Theimon said:**
> Just remove the folders and symlinks. If you installed everything by default that would be:
/usr/local/games/enemy-territory
/home/*username*/.etwolf
/usr/bin/et
/usr/bin/etded

(correct me if I missed out on anything.)

Thank you very much.  I had given up...

---

### Post by moondy on 2007-10-07
I've downloaded 'et-linux-2.60.x86.run' to my desktop. 

Now when i want to install it in the terminal is claims it cant find it.

I typed in:
'chmod +x et-linux-2.60.x86.run
sudo ./et-linux-2.60.x86.run'

and it comes up:
'~$ chmod +x et-linux-2.60.x86.run
chmod: cannot access `et-linux-2.60.x86.run': No such file or directory'

Any advice?

---

### Post by Waappu on 2007-10-07
> **moondy said:**
> I've downloaded 'et-linux-2.60.x86.run' to my desktop. 

Now when i want to install it in the terminal is claims it cant find it.

I typed in:
'chmod +x et-linux-2.60.x86.run
sudo ./et-linux-2.60.x86.run'

and it comes up:
'~$ chmod +x et-linux-2.60.x86.run
chmod: cannot access `et-linux-2.60.x86.run': No such file or directory'

Any advice?

If your file is in desktop open terminal and type

```
cd ~/Desktop
sudo chmod +x et-linux-2.60.x86.run
sudo ./et-linux-2.60.x86.run'

```

---

### Post by moondy on 2007-10-08
Sorry i feel like an idoit but nothing seems to happen...

I do what you say and i get no understandable response. 
> moondy@ubuntu:~$ cd ~/Desktop
moondy@ubuntu:~/Desktop$ sudo chmod +x et-linux-2.60.x86.run
moondy@ubuntu:~/Desktop$ sudo ./et-linux-2.60.x86.run'
> cd ~/Desktop
> sudo chmod +x et-linux-2.60.x86.run
> sudo ./et-linux-2.60.x86.run'
sudo: ./et-linux-2.60.x86.run
cd ~/Desktop
sudo chmod +x et-linux-2.60.x86.run
sudo ./et-linux-2.60.x86.run: command not found


---

### Post by Waappu on 2007-10-08
> **moondy said:**
> Sorry i feel like an idoit but nothing seems to happen...

I do what you say and i get no understandable response.

Hi

This should work

Open terminal

type```
cd ~
```
now you should be in your home dir

type in terminal for download ET package
```
wget -c ftp://ftp.peliplaneetta.net/pelidemot/3d-raiskinta-toiminta/et-linux-2.60.x86.run
```

and then install package```
sudo sh et-linux-2.60.x86.run
```

Edit:

I refer this page
[http://www.ubuntu-fi.org/Wiki/Enemy_Territory](http://www.ubuntu-fi.org/Wiki/Enemy_Territory)

---

### Post by reed026 on 2007-10-09
I seem to be having a problem with glibc, however I have glibc installed, so I don't know what the problem is, unless I have used the wrong commands to install.

> root@reed-home:/home/reed# sh /home/reed/Desktop/et-linux-2.55.x86.run
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.55...........................................................................................................................................................................................................................................................................................................
/root/.setup18975: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
The setup program seems to have failed on x86/glibc-2.1

See [http://zerowing.idsoftware.com/linux/](http://zerowing.idsoftware.com/linux/) for troubleshooting

---

### Post by Littl3King on 2007-10-16
/root/.setup27677: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
The setup program seems to have failed on x86/glibc-2.1


^
|
|
|  

This is my error for installing the enemy territory...  i am using this command as a su when recieving this error -- 

sh et-linux-2.55.x86.run

PLZ HELP ME :) Thank you.
I'll just be waiting... hopefully not long.  :)
 :popcorn:

---

### Post by pbmax on 2007-10-16
The binary install is pretty old, so it uses an older set of libraries.
Use your package manager to install ```
libgtk-1.2
```

I've also noticed that settings get stored in the /~/.etwolf so keep that in mind if you cant find settings or configs sometimes.
pb

---

### Post by Littl3King on 2007-10-16
fair enough..thank you...installation works now brother thanks for your help...and the quick post :P :)

---

### Post by -Sal- on 2007-10-20
Hi,
I've just installed Ubuntu 7.10 and Enemy Territory. Everything works fine except pbsetup.run which i have downloaded from evenbalance.com.. Simply I can't find a way to start that file.
 enabled: allow exec file as a program.. double click without result..
I've also tried with chmod and ./pbsetup.run .. sudo sh pbsetup.run .. but have no any result.
BTW.. I'm playing ET about one year ago using suse, pclinuxos or ubuntu 6.06 as well as ubuntu 7.04.. was everything just fine till 7.10
Any suggestions pls
Greetz

---

### Post by Lord C on 2007-10-20
Tried both Methods [here]("https://help.ubuntu.com/community/EnemyTerritory"). Still cannot get sound working ingame

> ------- sound initialization -------
------------------------------------
----- Sound Info -----
sound system is muted
    1 stereo
32768 samples
   16 samplebits
    1 submission_chunk
22050 speed
0xaf54e000 dma buffer
No background file.
----------------------
Sound memory manager started

Sound works in other games,
If I type killall esd; et; esd I hear the esd sound when the game is exited.

And I tried
sudo -i
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
exit
With no luck.

Any further advice?

[Edit]
This guide worked:
[http://ubuntuforums.org/showthread.php?t=362231](http://ubuntuforums.org/showthread.php?t=362231)
[/Edit]

---

### Post by Rajca on 2007-10-21
> **-Sal- said:**
> Hi,
I've just installed Ubuntu 7.10 and Enemy Territory. Everything works fine except pbsetup.run which i have downloaded from evenbalance.com.. Simply I can't find a way to start that file.
 enabled: allow exec file as a program.. double click without result..
I've also tried with chmod and ./pbsetup.run .. sudo sh pbsetup.run .. but have no any result.
BTW.. I'm playing ET about one year ago using suse, pclinuxos or ubuntu 6.06 as well as ubuntu 7.04.. was everything just fine till 7.10
Any suggestions pls
Greetz
So, go to your ET/pb directory, it should be /usr/local/games/enemy-territory/pb and run pbweb.x86 if it won't work allow executing. It should download some files and replace old. Than copy pbweb.x86 to .etwolf/pb in your home directory and than run it. It works. I tried and i can play with pb.
To show hidden files(with dots in front)- Ctrl+H(nautilus)
Solution by: [px33@ubuntu.pl]("http://forum.ubuntu.pl/profile.php?mode=viewprofile&u=9359")

---

### Post by -Sal- on 2007-10-21
@Rajca
Thanks a lot mate.. at last I've got updated punkbuster thanks to your advice.
Greetz

---

### Post by Peli on 2007-10-21
Hey Raja I have the same problem, I can't play et because my pb won't update.

I don't know what you mean by the ./etwolf/pb folder in your "HOME" directory, I went in my home directory, I don't see ./etwolf

---

### Post by Greeface on 2007-10-21
It's hidden because it has a dot in front of it.  If using Nautilus hit ctrl+h to see the hidden files.

/home/user/.etwolf

---

### Post by WraCkeR on 2007-10-24
Hi everyone :)

I have few broblems with this ET.. And I dont know what I have maked wrong ...

I have ATi Xpress 1150 shared... 
and I m using Ubuntu 7.4  

**glxgears**
more than 8200 frames 

**glxinfo | grep "rendering"**
direct rendering: Yes 

**fglrxinfo **
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6849 Release

I put there log from** ./et ** 

```
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/root/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
execing autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode -1: 1024 768
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 1024x768
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: ATI Radeon Xpress Series
Initializing OpenGL extensions
...GL_S3_s3tc not found
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...GL_NV_fog_distance not found
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
... GLX_SGI_swap_control not found
... GLX_SGI_video_sync not found
XF86 Gamma extension initialized

GL_VENDOR: ATI Technologies Inc.
GL_RENDERER: ATI Radeon Xpress Series
GL_VERSION: 2.0.6849 Release
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_shader GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_envmap_bumpmap GL_ATI_fragment_shader GL_ATI_meminfo GL_ATI_separate_stencil GL_ATI_texture_env_combine3 GL_ATI_texture_float GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_object GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texgen_reflection GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_KTX_buffer_region GL_NV_blend_square GL_NV_texgen_reflection GL_SGIS_generate_mipmap GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_WIN_swap_hint WGL_EXT_swap_control 
GLX_EXTENSIONS: GLX_ARB_get_proc_address GLX_ARB_multisample
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 8

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: -1, 1024 x 768 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: disabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------
------------------------------------
----- Sound Info -----
sound system is muted
    1 stereo
32768 samples
   16 samplebits
    1 submission_chunk
22050 speed
0x0xaae8a000 dma buffer
No background file.
----------------------
Sound memory manager started
Sys_LoadDll(/root/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/root/.etwolf/etmain/ui.mp.i386.so) failed:
"/root/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xa92f8f40  
Sys_LoadDll(ui) succeeded!
Found high quality video and fast CPU
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: wracker
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
execing preset_high.cfg
r_colorbits will be changed upon restarting.
r_depthbits will be changed upon restarting.
r_picmip will be changed upon restarting.
r_mode will be changed upon restarting.
r_texturebits will be changed upon restarting.
RE_Shutdown( 1 )
Hunk_Clear: reset the hunk ok
----- Initializing Renderer ----
-------------------------------
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 6: 1024 768
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 1024x768
Received signal 11, exiting...
Shutdown tty console

```

If someone know how to fix or where is problem pls answer...
thx ahead..

and sry for my english ... I think that my english is not so good :}

---

### Post by Rog-Mahal on 2007-11-04
I get an odd error message when I try to install et.

```
./setup.sh: 278: /home/roger/.setup8746: not found
./setup.sh: 289: /home/roger/.setup8746: not found

```

Then the install aborts. Are there some packages that I am missing in order to build it correctly? I have used this installer several times on other machines, this is the first time I have had any problems with it.

---

### Post by Jimmey on 2007-11-06
Are you running 64 bit? You need the 32bit compatibility packages installed.

---

### Post by Rog-Mahal on 2007-11-06
Yes, I am running 64bit, I got the compatability libraries. Thanks :) I do have another question though. When I'm running et, my screen constantly blacks out in places and it runs very slowly. Is this a problem with my display settings? or is my hardware not beefy enough to support it? It runs, but it's almost unplayable.

---

### Post by Jimmey on 2007-11-07
I have occasionally had problems where the game's gamma setting seems to dim down to a setting where it is almost impossible to play. I discovered that this is a problem with the screensaver. If you set your screensaver to come on only after two hours of idleness, then you shouldn't experience this problem for the first two hours of play. And it can be rectified by fiddling with the gamma slider in the game settings.

I  also had a problem where my FPS would drop to unplayably low levels. This was a sound problem. When I was using the standard echo et.x86 /proc/oss (or whatever it is :-P), the game would occasionally lag to the max. The fix for this, I've found, is et-sdl-sound.

Maybe these are your problems?

---

### Post by outkast08 on 2007-11-10
Help please i was able to play this game under Feisty but now I did a fresh install of Ubuntu Gutsy I can't create profile. I remember I was able to go through this in Feisty by running *sudo chown -R user:user ~/.etwolf*
It always says 
Creation Error:
Can't Create profile. Please
select your connection type.
I you are unsure what to 
select. Choose Modem.

---

### Post by Rog-Mahal on 2007-11-10
Unfortunately, turning my screensaver off didn't help. I'm not sure how to describe the problem. It's not that my screen dims too much; there are just these rectangular flickering blocks that get bigger and more frequent when I move the mouse and ruin the game play. In game I sometimes lag really badly, so I will try the sound fix. Thanks for your help

---

### Post by outkast08 on 2007-11-11
:roll: how stupid of me... I forgot to select a connection type...

---

### Post by domer.pdo on 2007-11-14
Installed the game according your walkthrough and get kicked from every server (Due the game integrity).
Do anybody know, what does it mean?

---

### Post by tuesday20102001 on 2007-11-24
> **tshirtz1013 said:**
> This fixed my no sound in Enemy Territory. I use a Soundblaster Audigy and am running dapper. I also have an onboard sound card available. I tried everything posted here with no great luck so finally, I attacked ET, what I found was that mpost of my apps try to use "/dev/dsp" for sound.... ahaha !! My Audigy is attached to dsp1 so I pressed the tilde key to bring up the console in ET and then typed at the prompt  and viola...upon restart of et I had sound. I hope this helps some people. 

:)

All I can say is thank you, i have been looking for a fix for hours with no success. I use a sound blaster pci card as well ca0106. But my sound with et definitely works. here is what I did to get my sound to work:

Successful steps for getting sound to work: wolfenstein enemy territory starts with no sound.  couple of script files will fix this issue.

Step1: create a script to run wet: text file  name: wolfenstein.sh (or what name you like) and place it in the following directory: /usr/share/games/enemy-territory/ (or where ever you have the directory enemy-territory).

Step2: insert the following code in text file: 
#!/bin/bash
#this command will kill all artsd applications prior to running et
killall -9 artsd
#note this is the directory which i have the game file at
cd /usr/share/games/enemy-territory
./et
exit0
#
Step 2.1: save the file and give it executable permissions (command in terminal: chmod a+x wolfenstein.sh)

Step3 (this will execute a command on startup so you dont have to do it as root prior to starting the game every time you reboot): Create a text file in /etc/init.d called etsoundoss.sh (or another appropriate name)
insert the following in text file:
#!/bin/bash
#prevents having to type this command as root everytime computer is rebooted
#place file in /etc/init.d
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
exit0

Step 3.2: give the file executable permissions (command line: chmod a+x etsoundoss.sh)

Step4: create a symbolic link to file:
cd /etc/rc2.d/
ln -s /etc/init.d/etsoundoss.sh /etc/rc2.d/S13etsoundoss
(note:the S13 naming is meant to start after alsa).

Step 5 create a desktop shortcut if you like (so you don't have to open the terminal to start the application):
menu editor
new application
name the application
command: sh /usr/share/games/enemy-territory/WolfensteinEt.sh

Thanks to everyone for posting and providing helpful information on various sites to contribute to this post.

---

### Post by syczu on 2007-12-05
> **domer.pdo said:**
> Installed the game according your walkthrough and get kicked from every server (Due the game integrity).
Do anybody know, what does it mean?

Update your Et with 2.60 and 2.60b patches.

---

### Post by tuesday20102001 on 2008-01-11
Refining firewall rules, and Just wanted to confirm if I have the correct port number use for Wolfenstein ET :
UDP: 27950 - 27952
UDP: 27960
UDP: 27965
TCP: 27952
TCP: 27960
TCP: 27965

Couldn't find a ubuntu thread specific for this subject.

---

### Post by CLomax on 2008-01-13
This is how I did it, and it worked for me very well.

1. Open terminal.

2. Drag .run file onto terminal, it should read something like '/home/USERNAME/Desktop/et-linux-2.60.x86.run' (With apostrophae)

3. Add sudo in front and leave the apostrophae ( sudo '/home/USERNAME/Desktop/et-linux-2.60.x86.run' ) and press enter.

Would like to see if it works for anyone else.

EDIT:  I keep getting an invalid GUID

---

### Post by Waappu on 2008-01-13
> **CLomax said:**
> This is how I did it, and it worked for me very well.

1. Open terminal.

2. Drag .run file onto terminal, it should read something like '/home/USERNAME/Desktop/et-linux-2.60.x86.run' (With apostrophae)

3. Add sudo in front and leave the apostrophae ( sudo '/home/USERNAME/Desktop/et-linux-2.60.x86.run' ) and press enter.

Would like to see if it works for anyone else.

EDIT:  I keep getting an invalid GUID

Works well if you add ```
sudo sh
``` before path&file

---

### Post by 1467 on 2008-02-13
every time i enter ./configure
or ./ any thing i get  "./configure: No such file or directory"
plz help

---

### Post by Mouldy_Taco on 2008-02-18
My ET cannot find the server-specific mods that alter sounds and uniforms and such.  I have checked the drive myself and see these mods in the correct folder.  Any idea what to do with that?

---

### Post by bewilkinson on 2008-03-08
Verify that the directory for downloaded maps is accessible and writable by your user. If you do not do this, you will be unable to download and install the maps and other files you need to join games!

sudo chown -R user:group ~/.etwolf/

Replace user:group with your own username and group (usually these are the same).

---

### Post by odielag on 2008-05-08
> **Rog-Mahal said:**
> I get an odd error message when I try to install et.

```
./setup.sh: 278: /home/roger/.setup8746: not found
./setup.sh: 289: /home/roger/.setup8746: not found

```

Then the install aborts. Are there some packages that I am missing in order to build it correctly? I have used this installer several times on other machines, this is the first time I have had any problems with it.

I have the same problem. Supposedly this user installed 32 bit compatibility stuff but I don't know what they're referring to. I've skimmed this entire thread, so I know other people have had this problem. What should I do?

---

### Post by odielag on 2008-05-09
I closed all my windows and tried again, and it installed! wewt! now to get the sound working.

---

### Post by Rocky88 on 2008-05-14
I've run into a little problem, read through the entire topic to one similar to mine, couldn't find anything, so here goes:

```
rocky@rocky-laptop:~$ sudo et
ET 2.60b linux-i386 May  8 2006
----- FS_Startup -----
Current search path:
/home/rocky/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
execing profiles/Pull/etconfig.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 16 depth, 0 stencil display.
GL_RENDERER: Mesa GLX Indirect


***********************************************************
 You are using software Mesa (no hardware acceleration)!   
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Received signal 11, exiting...

```

Installed the game, upgraded to the 2.60b version, updated PB. Now, when I force the game by typing the following:

```
et +set r_allowSoftwareGL 1
```

The game starts up all right, except that it's too slow. I know it's vague, but it seems to stutter almost every second.

Gfx Card details:
```
01:00.0 VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Unknown device 30a5
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at d1000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at d0000000 (64-bit, non-prefetchable) [size=16M]
	Capabilities: <access denied>
```

Any ideas?

---

### Post by tuesday20102001 on 2008-05-18
Thanks for the patch on 2.60b

If your having trouble executing the new files: etded.x86  et.x86, change permissions to the file so you are not running them as root (chown username file name) move the old files in the old directory to another location (desktop or other folder). copy the new files to the et directory (/usr/share /games or where ever it is installed. Pretty straight forward, enjoy.

---

### Post by tuesday20102001 on 2008-05-18
> **odielag said:**
> I have the same problem. Supposedly this user installed 32 bit compatibility stuff but I don't know what they're referring to. I've skimmed this entire thread, so I know other people have had this problem. What should I do?

I assume you are referring to a 64bit Ubuntu installation?

---

### Post by jheigl on 2008-07-03
Ok, I have just read thru all of these pages and have tried everything to get sound working...to no avail. I get the error here:

/dev/dsp: Input/output error
Could not mmap /dev/dsp

I did what was suggested in these forums and still cannot get sound. Now, I am a complete Linux/ubuntu newbie, so please do not think that I did everything correctly when following the steps to get the sound. One problem off the bat was when I was trying to create the start-et file and place it in /usr/local/games, it went in, but when I went to do the stuff in terminal for that file, it said no such file. 

Can someone please walk me through, step by step, as if it was how to get ET sound for dummies? I just started with Linux at the beginning of the week, so I am a complete newbie. I would really appreciate anyone willing to take the time. Thanks!

---

### Post by AJCF on 2008-07-03
I get Permission Denied when trying that echo fix for the no sound problem, what do I need to do? :confused:

---

### Post by xSpitxFirex on 2008-07-08
hello i just downloaded Ubuntu and can not figure out how to install WolfET. I am not sure how to do the commands in the Terminal, perhaps someone can post an example to instal Wolfenstein: Enemy Territory?

---

### Post by tuesday20102001 on 2008-07-17
> **AJCF said:**
> I get Permission Denied when trying that echo fix for the no sound problem, what do I need to do? :confused:

use the whoami command in terminal to determine which user you are. your probably not using the sudo command or are not a sudo user.

---

### Post by tuesday20102001 on 2008-07-17
> **xSpitxFirex said:**
> hello i just downloaded Ubuntu and can not figure out how to install WolfET. I am not sure how to do the commands in the Terminal, perhaps someone can post an example to instal Wolfenstein: Enemy Territory?

read though this tutorial for installing rtcw:
[https://help.ubuntu.com/community/Games/Native/ReturnToCastleWolfensteinEnemyTerritory](https://help.ubuntu.com/community/Games/Native/ReturnToCastleWolfensteinEnemyTerritory)

this thread and above forum has pretty much everything you need to get the game running.

---

### Post by Powerkid89 on 2008-07-29
"Downloading Maps

Verify that the directory for downloaded maps is accessible and writable by your user. If you do not do this, you will be unable to download and install the maps and other files you need to join games!

sudo chown -R user:group ~/.etwolf/

Replace user:group with your own username and group (usually these are the same). "
what do i do?

---

### Post by NaqoyqatZ on 2008-08-02
Hello,

I'm a newb. I'm stuck on the installer still. I've searched and read post after post, but can't find anything related to my problem. When I run the installer, here's is what I get:

bryan@bryan-ubuntu:~$ ./et-linux-2.60.x86.run
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.60 Full Install..............................................................................................................................................................................................................................................................................................................................
./setup.sh: 273: /home/bryan/.setup6761: not found
./setup.sh: 278: /home/bryan/.setup6761: not found
./setup.sh: 289: /home/bryan/.setup6761: not found
bryan@bryan-ubuntu:~$ 

Any suggestions?

Thanks,
Naq

EDIT: Nevermind...figured it out. I muffed the libgtk1.2 install somehow.

---

### Post by attila_66 on 2008-10-06
Finally I got my Enemy Territory Back Interpid Ibex!!!!
First because of this install problem (I am using 64 bit)

attila@ubuntuattilas:~$ sudo ./et-linux-2.60.x86.run
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.60 Full Install........................................... .................................................. .................................................. .................................................. .................................................. .................................................. .........................
./setup.sh: 278: /home/attila/.setup7028: not found
./setup.sh: 289: /home/attila/.setup7028: not found
attila@ubuntuattilas:~$

I installed some lib32 compatibility packages
Dont ask which one dont remember.
But i installed one then tried no success
Installed other one tried
Finally succeeded.

I installed the program.

While running program

can't find libX11.so.6

problem appeard.
Little search on the web found that have to install
ia32-lib-sdl
ia32-libs
lib32asound2

libraries has to be installed.
Installed these libraries..

And the game started..

---

### Post by clearshot on 2008-10-15
Hello
I've recently upgraded to Ibex and I have installed ET through Playdeb.
I also installed UrbanTerror and Alien Arena.

ET starts and connects alright, but maybe 50 seconds into a round, the graphics will go all messed up and stay that way. Sometimes it happens in the menus. Basically all of the walls and menus go weird colours; the models seem to stay regular.

I'm on a Dell 1525N (which I would never recommend to anyone ever) and I think it's an Intel card.

Other than the graphics problem, the game runs fine.

---

### Post by namaster on 2008-10-19
Any idea how to stop screen flickering? It flickers too much. That doesn't used to happen in old version of ubunutu. After i upgraded to 8.4.1 their seems to be a problem.

---

### Post by saravanan.2407 on 2008-10-19
where could i download the Enemy Territory ??

---

### Post by namaster on 2008-10-19
> **saravanan.2407 said:**
> where could i download the Enemy Territory ??

On the first page i guess their is download link? 

Or use this link:
[https://help.ubuntu.com/community/EnemyTerritory](https://help.ubuntu.com/community/EnemyTerritory)

---

### Post by soelk on 2008-10-21
> **namaster said:**
> Any idea how to stop screen flickering? It flickers too much. That doesn't used to happen in old version of ubunutu. After i upgraded to 8.4.1 their seems to be a problem.

Have you tried to disable the "extra" visual effects in System->Preferences->Appearance? Do other 3-d apps like Google Earth flicker? In that case, try setting the effects to "none". Compiz fusion causes flicker with many video cards.

---

### Post by MaindotC on 2008-10-23
When I start the game the screen goes black for a bit and seems to try and change into 640x480 mode but I get the following output:

```

amd64@amd64-desktop:/usr/local/games/enemy-territory$ ./et
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/amd64/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: ATI RADEON X850 XT Platinum Edition
Initializing OpenGL extensions
...GL_S3_s3tc not found
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...GL_EXT_compiled_vertex_array not found
...GL_NV_fog_distance not found
... GL_EXT_texture_filter_anisotropic not found
Initializing GLX extensions
... GLX_SGI_swap_control not found
... GLX_SGI_video_sync not found
XF86 Gamma extension initialized

GL_VENDOR: ATI Technologies Inc.
GL_RENDERER: ATI RADEON X850 XT Platinum Edition
GL_VERSION: 1.4 (2.1.7769 Release)
GL_EXTENSIONS: GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_object GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_ATI_draw_buffers GL_ATI_texture_env_combine3 GL_ATIX_texture_env_combine3 GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_NV_blend_square GL_NV_texgen_reflection GL_NV_texture_rectangle GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SGIX_shadow_ambient GL_SUN_multi_draw_arrays 
GLX_EXTENSIONS: GLX_ARB_get_proc_address GLX_ARB_multisample GLX_EXT_import_context GLX_EXT_visual_info GLX_EXT_visual_rating GLX_OML_swap_method GLX_SGIS_multisample GLX_SGIX_fbconfig GLX_SGIX_visual_select_group GLX_EXT_texture_from_pixmap 
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 8

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: multiple glArrayElement
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 0
multitexture: enabled
compiled vertex arrays: disabled
texenv add: disabled
compressed textures: disabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------
------------------------------------
----- Sound Info -----
sound system is muted
    1 stereo
32768 samples
   16 samplebits
    1 submission_chunk
22050 speed
0x0xf2c1d000 dma buffer
No background file.
----------------------
Sound memory manager started
Sys_LoadDll(/home/amd64/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/amd64/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/amd64/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xef57ff40  
Sys_LoadDll(ui) succeeded!
Found high quality video and fast CPU
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: amd64-desktop
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
Couldn't write etconfig.cfg.
execing preset_high.cfg
r_colorbits will be changed upon restarting.
r_depthbits will be changed upon restarting.
r_picmip will be changed upon restarting.
r_mode will be changed upon restarting.
r_texturebits will be changed upon restarting.
RE_Shutdown( 1 )
Received signal 11, exiting...
DOUBLE SIGNAL FAULT: Received signal 2, exiting...
Shutdown tty console
amd64@amd64-desktop:/usr/local/games/enemy-territory$

```

Is this a video card configuration issue?

---

### Post by tuesday20102001 on 2008-10-29
It is also possible to install this program on a 64bit install of ubuntu with the following dependency: "ia32-libs" . also noted here: [http://ubuntuforums.org/showthread.php?t=416871](http://ubuntuforums.org/showthread.php?t=416871) .

---

### Post by tuesday20102001 on 2008-10-29
> **saravanan.2407 said:**
> where could i download the Enemy Territory ??
[www.splashdamage.com/](www.splashdamage.com/)

---

### Post by danny_discus on 2008-11-07
Hey I installed this and everything works great except when I press my left and right mouse buttons at the same time nothing happens.  Anytips on how to unbind mouse2 in Ubuntu? Ran xev and when I press both buttons down it shows as mouse2.

---

### Post by allpur on 2009-01-30
Hi to one and all, being very new to Ubuntu i can't get the sound to work in ET but here it in everything else. is there or does anyone have a made up file they could send me, or a step by step guide on how to make the file/files to work. i have got a headache looking and try things to work.

Many thanks Allpur


Edit Edit......

Ok i've managed to get this to work

 "sudo chmod 777 /proc/asound/card0/pcm0p/oss"

followed by

 "echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss"

in Terminal.

How do i get this into a script.  I've put my ET files in to " Places/home folder/myusername/usr/local/games/enemy-territory" where the "et.x86" is. AT the moment i have to do one line at a time then run ET.

Allpur

---

### Post by Hb_Kai on 2009-02-10
Scratch what I've edited out, I've done it now. 

When I try to run it in Terminal it says:

0x0
[0x082e4381]
[0x0819d6da]
[0x0819b782]
[0x0819c092]
[0x0819c26e]
[0x082e459e]
[0xb7dfe685]
[0x0804bd31]
********************
FATAL ERROR: Couldn't load fs.chk
********************
--------------- BSE Shutdown ----------------
---------------------------------------------
idRenderSystem::Shutdown()
Sys_Error: Couldn't load fs.chk
garry@ubuntu:/usr/local/games/etqw$ 


I've tried to run it from the Desktop folder and /usr/local/games/etqw folder with the etqw file and this is all that shows up. 

What is it and why does it do this?

---

### Post by xchecker on 2009-03-07
How do you open the Enemy Territory doc with sound and play? I NEED HELP! PLZ! I think it is et-sdl-sound, is that correct? if it's not please correct me and post it on the page:o

---

### Post by whitbeck on 2009-03-11
I have install et but when I go to run it the program changes my screen resolution and I get the following message:


ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/drew/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain


Is there a patch that I am missing?
----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 16 depth, 0 stencil display.
GL_RENDERER: Mesa GLX Indirect


***********************************************************
 You are using software Mesa (no hardware acceleration)!   
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
X Error of failed request: BadValue (integer parameter out of range for operation)
  Major opcode of failed request: 134
  Minor opcode of failed request: 10
  Serial number of failed request: 55
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Received signal 11, exiting...

Is there a patch I am missing?

---

### Post by coolness on 2009-03-31
Listen people, i tried to install that game were talking about here. And it worked! But thats not the issue here. The sound doesn't work. Well i tried the command the guy who posted this how to told to do. and i get the following:
chang@LAIVA:~$ echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
bash: /proc/asound/card0/pcm0p/oss: Permission denied
chang@LAIVA:~$ 
What should i do? i tried sudo but its the same, and i dont have a root terminal in my ubuntu hardy. Maby i should try to download it?

---

### Post by mcweck on 2009-04-02
> **coolness said:**
> Listen people, i tried to install that game were talking about here. And it worked! But thats not the issue here. The sound doesn't work. Well i tried the command the guy who posted this how to told to do. and i get the following:
chang@LAIVA:~$ echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
bash: /proc/asound/card0/pcm0p/oss: Permission denied
chang@LAIVA:~$ 
What should i do? i tried sudo but its the same, and i dont have a root terminal in my ubuntu hardy. Maby i should try to download it?

i wrote a copy paste how to at my HomePage: [How to get sound in ET working ]("http://www.hirntot.org/index.php?option=com_content&view=article&id=97&Itemid=109")it includes a small hack to disable the screensaver while gaming (darkens the screen in game if you don't disable it)

---

### Post by mcweck on 2009-04-02
> **whitbeck said:**
> I have install et but when I go to run it the program changes my screen resolution and I get the following message:


ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/drew/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain


Is there a patch that I am missing?
----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 16 depth, 0 stencil display.
GL_RENDERER: Mesa GLX Indirect


***********************************************************
[COLOR="Red"]**_ You are using software Mesa (no hardware acceleration)!_** [/COLOR]  
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
X Error of failed request: BadValue (integer parameter out of range for operation)
  Major opcode of failed request: 134
  Minor opcode of failed request: 10
  Serial number of failed request: 55
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Received signal 11, exiting...

Is there a patch I am missing?

First at all you should install a gl driver then you should be able to play.

---

### Post by paradroid90 on 2009-05-18
Hi,

Having problems running the Punkbuster set up with sudo command

Any help with command line/shell commands to get the install/updater working you see Enemy Territory installed without Punkbuster??????

Any help would be appricated

---

### Post by crjackson on 2009-05-18
> **paradroid90 said:**
> Hi,

Having problems running the Punkbuster set up with sudo command

Any help with command line/shell commands to get the install/updater working you see Enemy Territory installed without Punkbuster??????

Any help would be appricated

Punkbuster should have been installed by default unless you started clicking on some of the little square check boxes before you clicked install.

Have a look at an install guide I wrote quite some time back. It still works. You made needed to delete the game from you system a re-install.  I haven't messed with it in a long time so ymmv.

[**Install guide**]("http://buck-nasty.blogspot.com/2008/08/enemy-territory-wolfenstein-complete.html")

[**Sound Fix**]("http://buck-nasty.blogspot.com/2008/08/wolfenstein-enemy-territory-no-sound.html")

To uninstall ET:
```
sudo rm -rf /usr/local/games/enemy-territory/ && sudo rm -f /usr/local/bin/et && rm -rf $HOME/.etwolf
```

---

### Post by crjackson on 2009-05-18
> **coolness said:**
> Listen people, i tried to install that game were talking about here. And it worked! But thats not the issue here. The sound doesn't work. Well i tried the command the guy who posted this how to told to do. and i get the following:
chang@LAIVA:~$ echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
bash: /proc/asound/card0/pcm0p/oss: Permission denied
chang@LAIVA:~$ 
What should i do? i tried sudo but its the same, and i dont have a root terminal in my ubuntu hardy. Maby i should try to download it?


**As root user** (open a terminal and type: **sudo -i**) Then type:
sudo echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

---

### Post by crjackson on 2009-05-18
> **allpur said:**
> Hi to one and all, being very new to Ubuntu i can't get the sound to work in ET but here it in everything else. is there or does anyone have a made up file they could send me, or a step by step guide on how to make the file/files to work. i have got a headache looking and try things to work.

Many thanks Allpur


Edit Edit......

Ok i've managed to get this to work

 "sudo chmod 777 /proc/asound/card0/pcm0p/oss"

followed by

 "echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss"

in Terminal.

How do i get this into a script.  I've put my ET files in to " Places/home folder/myusername/usr/local/games/enemy-territory" where the "et.x86" is. AT the moment i have to do one line at a time then run ET.

Allpur

Go to my [**Install Guide**]("http://buck-nasty.blogspot.com/2008/08/enemy-territory-wolfenstein-complete.html") & my [**Sound Fix**]("http://buck-nasty.blogspot.com/2008/08/wolfenstein-enemy-territory-no-sound.html") Guide.

---

### Post by crjackson on 2009-05-18
> **whitbeck said:**
> I have install et but when I go to run it the program changes my screen resolution and I get the following message:


ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/drew/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain


Is there a patch that I am missing?
----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 16 depth, 0 stencil display.
GL_RENDERER: Mesa GLX Indirect


***********************************************************
 You are using software Mesa (no hardware acceleration)!   
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
X Error of failed request: BadValue (integer parameter out of range for operation)
  Major opcode of failed request: 134
  Minor opcode of failed request: 10
  Serial number of failed request: 55
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Received signal 11, exiting...

Is there a patch I am missing?

@whitbeck

I haven't had a chance to try Jaunty vs ET yet. I replied to your post in my blog. I'll have a look at it in a few days. There may be a problem with the XFree86 and Jaunty's video structure. I'll get back with you and if I find a solution I'll post it.

---

### Post by nutsandbolts on 2009-05-25
Few questions

Where can I put my cfg?
How do I install the 2.6b patch, whenever I try to move it, it gives me "permission denied".

---

### Post by Hobgoblin on 2009-05-25
> **nutsandbolts said:**
> 
How do I install the 2.6b patch, whenever I try to move it, it gives me "permission denied".

Use sudo to give you root permissions.

---

### Post by stalker01 on 2009-05-26
hi i got et installed and the patch following everything i could find in this thread just having trouble with server list im only getting a list of like 10 servers all over 255 ping was wondering if there is something i can do to get my normal servers that i did 1ns play on windows,
and was allso wondering how i can chmod the whole et folders so i can copy over my etconfig atm i cant add any files into etmain.
any help would be greatfull thanks

---

### Post by errors on 2009-05-30
Btw i cant that any screenshots or even make a demo :S anyone knows the solution for that?

Thx in advance.

---

### Post by xfearxnxloathing on 2009-06-12
i dont understand..

---

### Post by Jeneral22 on 2009-06-19
Just an FYI for all of us... 

I upgraded to Jaunty and haven't been able to run Enemy Territory for very long before it freezes my pc with a looping sound. The problem appears to by the ATI Radeon 3850 and the ATI Driver. I am currently using the 9.5 Catalyst driver and the 9.6 just came out with a warning that there is a problem with ET and the 9.6 driver.

I found this thread because I was looking for a solution to this problem. Game is a blast when you get a chance to play.

---

### Post by Pax-Man on 2009-06-19
Thank you for this guide. I've looking forward to play this game :D

---

### Post by arkangelas45 on 2009-06-22
Hi. I download this game from fileshack. And i try to install. I go to terminal and enter sudo sh ./et-linux-2.60.x86.run. And disapear error.
Verifying archive integrity...Error in MD5 cheksums: a9bc2c9debbbb6c5880ac123fefdea is different from b8b59bc515d86cc845fb52fb52f5d2c14423. How i can to try fix this error? And install game?

---

### Post by Jeneral22 on 2009-06-24
Arkangel,

I think you have a bad download on your hands. Try googling and downloading from another site. It is a fun and addicting game. Don't get too stuck on any one server until you have tried a few. People are people and when you find a good "home" it will be even more fun!

Best of luck.

---

### Post by gotthardt on 2009-07-02
For MUCH better performance in ETQW (and more) - use the 2.6.30 kernel instead of 2.6.28
Installation instructions here:
[> Install 2.6.30 <]("http://www.ramoonus.nl/2009/06/10/linux-kernel-2-6-30-installation-guide-for-ubuntu-and-debian-linux/")

---

### Post by giddensdb on 2009-07-19
broc@broc-laptop:~$ et
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/broc/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
X Error of failed request: BadMatch (invalid parameter attributes)
  Major opcode of failed request: 1
  Minor opcode of failed request: 0
  Serial number of failed request: 41
X Error of failed request: BadWindow (invalid Window parameter)
  Major opcode of failed request: 18
  Minor opcode of failed request: 0
  Serial number of failed request: 42
X Error of failed request: BadWindow (invalid Window parameter)
  Major opcode of failed request: 18
  Minor opcode of failed request: 0
  Serial number of failed request: 43
X Error of failed request: BadWindow (invalid Window parameter)
  Major opcode of failed request: 8
  Minor opcode of failed request: 0
  Serial number of failed request: 44
X Error of failed request: BadWindow (invalid Window parameter)
  Major opcode of failed request: 12
  Minor opcode of failed request: 0
  Serial number of failed request: 45
X Error of failed request: BadWindow (invalid Window parameter)
  Major opcode of failed request: 18
  Minor opcode of failed request: 0
  Serial number of failed request: 48
X Error of failed request: BadDrawable (invalid Pixmap or Window parameter)
  Major opcode of failed request: 136
  Minor opcode of failed request: 7
  Serial number of failed request: 53
X Error of failed request: BadValue (integer parameter out of range for operation)
  Major opcode of failed request: 154
  Minor opcode of failed request: 26
  Serial number of failed request: 53
Received signal 11, exiting...
Segmentation fault (core dumped)
broc@broc-laptop:~$

---

### Post by oogmsn on 2009-08-08
Hey guys - I'm using dual screen, when I tried to run this it just set my dual screen back to 'mirror' and then nothing happens..so I tried using the terminal and run 'et' - what I get is as per below.
Could someone help to advise me on what went wrong?? Sorri still struggling with Ubuntu...

And..initially I thought that it might be a graphic card issue and tried installing the 'xorg-driver-fglrx' from Synaptic (since looking at the instruction listed in some of the posts - my System > Hardware Drivers showing up blank)..but I ran into issue where my screen becomes corrupted after i reboot and hence need to uninstall it from the recovery mode...

Any kind advice is deeply appreciated!

> ------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
X Error of failed request: BadMatch (invalid parameter attributes)
  Major opcode of failed request: 1
  Minor opcode of failed request: 0
  Serial number of failed request: 41
X Error of failed request: BadWindow (invalid Window parameter)
  Major opcode of failed request: 18
  Minor opcode of failed request: 0
  Serial number of failed request: 42
X Error of failed request: BadWindow (invalid Window parameter)
  Major opcode of failed request: 18
  Minor opcode of failed request: 0
  Serial number of failed request: 43
X Error of failed request: BadWindow (invalid Window parameter)
  Major opcode of failed request: 8
  Minor opcode of failed request: 0
  Serial number of failed request: 44
X Error of failed request: BadWindow (invalid Window parameter)
  Major opcode of failed request: 12
  Minor opcode of failed request: 0
  Serial number of failed request: 45
X Error of failed request: BadWindow (invalid Window parameter)
  Major opcode of failed request: 18
  Minor opcode of failed request: 0
  Serial number of failed request: 48
X Error of failed request: BadDrawable (invalid Pixmap or Window parameter)
  Major opcode of failed request: 136
  Minor opcode of failed request: 7
  Serial number of failed request: 53
X Error of failed request: BadValue (integer parameter out of range for operation)
  Major opcode of failed request: 154
  Minor opcode of failed request: 26
  Serial number of failed request: 53
Received signal 11, exiting...
Segmentation fault


---

### Post by taha116 on 2009-08-18
Help! i need to uninstall enemy territory, how can i do this?

---

### Post by Philabrow on 2009-08-24
> **taha116 said:**
> Help! i need to uninstall enemy territory, how can i do this?
Try this 
sudo rm -rf /usr/local/games/enemy-territory/ && sudo rm -f /usr/local/bin/et && rm -rf $HOME/.etwolf

---

### Post by Philabrow on 2009-08-24
I have trouble installing the game the file is fine it would appear, but when I try to install it does this
```
philip@philip-laptop:~/Desktop$ sudo sh ./et-linux-2.60.x86.run
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.60 Full Install..............................................................................................................................................................................................................................................................................................................................................................................Extraction failed.
Signal caught, cleaning up

```Please can some one help, thanks in advance.

---

### Post by dakis on 2009-08-25
Hello.

I'm new in linux world..

I have install Ubuntu 9.04 and i try to install Enemy Territory (et-linux-2.60.x86.run) i have make this steps

chmod +x et-linux-2.60.x86.run
./et-linux-2.60.x86.run

and when ask me in what dir i want to istall the defauld dir is usr/local/games
i press enter and tell me i dont have permition to write on that dir :( i change dir and i have the same problem.. what can i do ?:confused:


Sorry for my engilsh :(

---

### Post by Waappu on 2009-08-26
> **dakis said:**
> Hello.

I'm new in linux world..

I have install Ubuntu 9.04 and i try to install Enemy Territory (et-linux-2.60.x86.run) i have make this steps

chmod +x et-linux-2.60.x86.run
./et-linux-2.60.x86.run

and when ask me in what dir i want to istall the defauld dir is usr/local/games
i press enter and tell me i dont have permition to write on that dir :( i change dir and i have the same problem.. what can i do ?:confused:


Sorry for my engilsh :(

Try run installer as root with this command```
sudo ./et-linux-2.60.x86.run
```
and install select default dir.

If you can not use sudo. Then install game to your homefolder e.g. ~/home/et

---

### Post by dakis on 2009-08-26
> **Waappu said:**
> Try run installer as root with this command```
sudo ./et-linux-2.60.x86.run
```and install select default dir.

If you can not use sudo. Then install game to your homefolder e.g. ~/home/et


ok id did it!! :) tnx a lot :D

now about update pb ? i do that steps:

chmod +x pbweb.x86
./pbweb.x86
on pb dir and i get that msg

Attempting to download htm/lc-00001.htm (please wait)

**ERROR from Web Server: 302 Found
etc...

:(


------
[http://www.evenbalance.com/index.php?page=pbsetup.php](http://www.evenbalance.com/index.php?page=pbsetup.php)

download the For 32-bit Linux Games (Command-line only version)

uzip pbsetup.zip
chmod +x pbsetup.run
sudo ./pbsetup.run -vvv -ag et -u

---

### Post by waxyfresh on 2009-09-02
I cant get my sound to work: [http://pastebin.com/m1330bb32](http://pastebin.com/m1330bb32)

---

### Post by aonegodman on 2009-09-05
Help! Found "et-linux-2.60.x86.run" file in my home directory and clicked on it. It opened a "dos" type window and started to unpack archive and begin installation of program. When it got to window asking where to install it had something like - usr/local/games/enemy-territory. I selected ok, but comes back with error saying I don't have permission to write to that directory. I went Terminal and did the "sudo su" thing, but this didn't help. Any direction greatly appreciated. Thanks.

---

### Post by aonegodman on 2009-09-05
ok I was able to install the program inside Terminal using the original syntax presented at the front of this thread(i.e. su -c ".et-linux-2.60.x86.run") error was from wrong filename since I had a newer version of game. Doh! Next problem now is simply the sound is choppy and so is running of program, it takes mouse movements about 15 sec to catch up. Must be other element needing to be installed. Please direct. Thanks again.

---

### Post by aonegodman on 2009-09-05
ok ok ok, went back and checked for graphics driver. Found and installed driver 96 for my nVidea card, rebooted, restarted game and all cleared up including sound. Went online and played in a game somewhere in Texas I think. But I have no clue as to what is going on in this game or even who the enemy is. I didn't realize this was a multiplayer only game to start with. Graphics are not the greatest but tolerable ok. Any suggestions for similar first person - single shooter games? Thanks.

---

### Post by Sammel on 2009-09-06
I get kicked from all server with Punkbuster with following error:

PunkBuster kicked player 'Gaidini' (for 0 minutes) ... PB GUID AUTH: UNKN

I am using Ubuntu 9.04.
I have tried everything from this page: [https://help.ubuntu.com/community/EnemyTerritory]("https://help.ubuntu.com/community/EnemyTerritory")

What should I do to make this game work?

---

### Post by aonegodman on 2009-09-06
Hey I'm new to this also, but I noticed after starting game and going online that you are presented with a listing of active servers to choose from. I also noticed that above this listing there is a legend to explain what the graphic icons next to each server means. One of them stands for Allows Use of Punkbuster or something like that. You might try choosing only those servers to try and play from. Just a thought. Good luck with that.

---

### Post by Waappu on 2009-09-07
Hi

Check if these help you
[https://help.ubuntu.com/community/EnemyTerritory#Punkbuster%20update](https://help.ubuntu.com/community/EnemyTerritory#Punkbuster%20update)
[http://adammichaelroach.com/blog/050409/wolfenstein-enemy-territory-ubuntu-linux-jaunty-jackalope-904](http://adammichaelroach.com/blog/050409/wolfenstein-enemy-territory-ubuntu-linux-jaunty-jackalope-904)

---

### Post by moster on 2009-09-07
I installed everything like it said in this post and worked just fine. But, last time I installed it. It waited for some time on some stuff I entered.
[http://adammichaelroach.com/blog/050409/wolfenstein-enemy-territory-ubuntu-linux-jaunty-jackalope-904]("http://adammichaelroach.com/blog/050409/wolfenstein-enemy-territory-ubuntu-linux-jaunty-jackalope-904")

For sound, go to preferences and set everything to max quality.

---

### Post by Sammel on 2009-09-08
I followed that guide from [http://adammichaelroach.com](http://adammichaelroach.com) until updating PunkBuster:
> 
**ERROR from Web Server: 302 Found

Attempting to download htm/la-00001.htm (please wait)

**ERROR from Web Server: 302 Found

Attempting to download htm/lc-00001.htm (please wait)


But it wont update. Just keeps doing that.
What could I do about it?

---

### Post by moster on 2009-09-08
> **Sammel said:**
> I followed that guide from [http://adammichaelroach.com](http://adammichaelroach.com) until updating PunkBuster:


But it wont update. Just keeps doing that.
What could I do about it?

yes... I had problems too. Try in another time of day.

Without .pk3 (maps) files, game is only 40 MB. I could send it to you if you think you can use it to overwrite yours or something.

---

### Post by cvtmih on 2009-09-09
Hello , 

I'm getting kicked from all PB servers for PunkBuster kicked player 'etplayer' (for 0 minutes) ... PB GUID AUTH: UNKN

This appeared after the last PB updates for ET , I've tried everything but I still get this kick , and as I see all other linux users get it too. Please if there is any trick or way to fix it help :<

---

### Post by Kedaeus_Sendre on 2009-10-09
I've gone through all of the sound "fixes" from the tutorial and still don't have sound. 

The message I get every time I start it up is:

```

------- sound initialization -------
/dev/dsp: No such file or directory
Could not open /dev/dsp
------------------------------------

```

Anyone know what this is?

---

### Post by Gonzo_Dark on 2009-10-31
> **Kedaeus_Sendre said:**
> I've gone through all of the sound "fixes" from the tutorial and still don't have sound. 

The message I get every time I start it up is:

```

------- sound initialization -------
/dev/dsp: No such file or directory
Could not open /dev/dsp
------------------------------------

```

Anyone know what this is?




open your terminal and type: sudo gedit /etc/init.d/et-sound
then a blank page will apear, you need to copy paste this into the blank page:

> #!/bin/sh
#Bug in Wolfenstein ET
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss 

and then use the codes below, one at a time:

> sudo chmod 755 /etc/init.d/et-sound
sudo update-rc.d et-sound defaults
sudo /etc/init.d/et-sound start

enjoy.

testet to work on Ubuntu 8.04, 8.10, 9.04 and the new 9.10.

// GonzoDark

---

### Post by 1/0 on 2009-11-06
> **cvtmih said:**
> hello , 

i'm getting kicked from all pb servers for punkbuster kicked player 'etplayer' (for 0 minutes) ... Pb guid auth: Unkn

this appeared after the last pb updates for et , i've tried everything but i still get this kick , and as i see all other linux users get it too. Please if there is any trick or way to fix it help :<

+1

---

### Post by pribina on 2009-12-06
I've recently installed Ubuntu 9.10 Karmic Koala on Acer Aspire 3680  laptop with an Intel GPU on board. Most of the games work fine but I can't start Enemy Territory on this system. When I start the game it loads everything, the screen resoulution changes but soon after that game shuts down. Here is an output from a console:

```
ET 2.60b linux-i386 May  8 2006
----- FS_Startup -----
Current search path:
/home/anthrax/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: Mesa DRI Intel(R) 945GM GEM 20090712 2009Q2 RC3 x86/MMX/SSE2
Initializing OpenGL extensions
...GL_S3_s3tc not found
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...GL_NV_fog_distance not found
...ignoring GL_EXT_texture_filter_anisotropic
Initializing GLX extensions
... GLX_SGI_swap_control not found
...using GLX_SGI_video_sync
XF86 Gamma extension initialized

GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Intel(R) 945GM GEM 20090712 2009Q2 RC3 x86/MMX/SSE2
GL_VERSION: 1.4 Mesa 7.6.1-rc2
GL_EXTENSIONS: GL_ARB_copy_buffer GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_half_float_pixel GL_ARB_map_buffer_range GL_ARB_multisample GL_ARB_multitexture GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_sync GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_array_object GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_cull_vertex GL_EXT_compiled_vertex_array GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_framebuffer_object GL_EXT_framebuffer_blit GL_EXT_fog_coord GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_client_storage GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ATI_blend_equation_separate GL_ATI_texture_env_combine3 GL_ATI_separate_stencil GL_IBM_multimode_draw_arrays GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texture_env_combine4 GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_NV_vertex_program1_1 GL_OES_read_format GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays
GLX_EXTENSIONS: GLX_ARB_get_proc_address GLX_ARB_multisample GLX_EXT_import_context GLX_EXT_visual_info GLX_EXT_visual_rating GLX_MESA_copy_sub_buffer GLX_MESA_swap_frame_usage GLX_OML_swap_method GLX_SGI_video_sync GLX_SGIS_multisample GLX_SGIX_fbconfig GLX_SGIX_visual_select_group GLX_EXT_texture_from_pixmap 
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 8

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: disabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----

------- sound initialization -------
------------------------------------
----- Sound Info -----
sound system is muted
    1 stereo
32768 samples
   16 samplebits
    1 submission_chunk
44100 speed
0x0xb60b7000 dma buffer
No background file.
----------------------
Sound memory manager started
Sys_LoadDll(/home/anthrax/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/anthrax/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/anthrax/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0x2d9df40  
Sys_LoadDll(ui) succeeded!
Found high quality video and fast CPU
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: anthrax-karmic
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
execing preset_high.cfg
r_colorbits will be changed upon restarting.
r_depthbits will be changed upon restarting.
r_picmip will be changed upon restarting.
r_mode will be changed upon restarting.
r_texturebits will be changed upon restarting.
RE_Shutdown( 1 )
Hunk_Clear: reset the hunk ok
----- Initializing Renderer ----
-------------------------------
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 6: 1024 768
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 1024x768
Using 4/4/4 Color bits, 24 depth, 0 stencil display.
Received signal 11, exiting...
Shutdown tty console
```

Can somebody help?

---

### Post by no0ne on 2009-12-23
Just stumbled into an old Enemy Territory installation and noticed that I had noticeably less PunkBuster-releated problems on that particular machine. So I compared it to a fresh install to get as much out of it as possible:

([Grab your files]("ftp://ftp.idsoftware.com/idstuff/et/") off the idSoftware ftp server.)

0. Make your installer executable with ```
chmod +x <filename>
```, install game into default directory (/usr/local/games/enemy-territory/ by default). (To start [the installer]("ftp://ftp.idsoftware.com/idstuff/et/linux/et-linux-2.60.x86.run") use ```
sh ./<filename>
```).

1. Update to 2.60b - ([multiOS version of the patch]("ftp://ftp.idsoftware.com/idstuff/et/ET-2.60b.zip")).

2. Install [etpro]("http://etpro.anime.net") by extracting the archive to ~/.etwolf/etpro .

3. Place (previous) configs in .etwolf/etmain & .etwolf/etpro, autoexec and related scripts tp the first and player profile with the related etconfig.cfg to ~/.etwolf/etpro/profiles/<profilename>/. Still recommend having your settings as an autoexec.cfg for ET tends to reset rendering options after an unexpected closing of the game.)

4. Install esound: 
```
sudo apt-get install esound
```
and setup oss:
Check your loaded modules by running:
```
lsmod | grep snd
```
check for and if neccessary modprobe to tryout the following modules:
snd_seq_oss, snd_mixer_oss, snd_pcm_oss. To make them loaded by default add them to your /etc/modules, one on each line followed by linechange. (Remember to close all non-oss audio applications before running et. If you need to use non-oss audio applications theres [the sdl]("https://help.ubuntu.com/community/EnemyTerritory#Method%204").)

5. Copy the contents of /usr/local/games/enemy-territory/pb/ to ~/.etwolf/pb. Download to both forementioned directories the PunkBuster GUI updater[pbupdate.run]("http://www.evenbalance.com/index.php?page=pbsetup.php"). Make both also executable (chmod +x), add Enemy Territory "twice", the tool suggests both locations right. Update both by checking for updates. (The punkbuster installation in .etwolf is primary but both seems to work best.

6 Remember to set the permissions for directories according to the following(, which reduced tremendously PunkBuster-releated trouble, such as "violation game-integrity", "GUID AUTH: UNKN" etc):

~/.etwolf : should be set correctly (user:user) by default, but check it by running ls -al. also permissions 751 (chmod -R).

/usr/share/games/enemy-territory: 

```
chmod -R user:root /usr/local/games/enemy-territory
``` 

set permissions accordingly, here's mine:

```

drwxr-xr-x 6 user root     4096 2009-05-19 21:56 .
drwxr-xr-x 3 root  root     4096 2009-05-19 21:44 ..
-rwxr-xr-x 1 user root   705000 2009-05-19 21:04 2_60_etded.x86
-rwxr-xr-x 1 user root  1538888 2009-05-19 21:04 2_60_et.x86
-rw-r--r-- 1 user root     3691 2009-05-19 21:45 CHANGES
drwxr-xr-x 3 user root     4096 2009-05-19 21:45 Docs
-rwxr-xr-x 1 user root      208 2009-05-19 21:45 et
-rwxr-xr-x 1 user root      211 2009-05-19 21:45 etded
-rwxr-xr-x 1 user root   709216 2009-05-19 22:16 etded.x86
drwxr-xr-x 3 user root     4096 2009-05-19 21:58 etmain
drwxr-xr-x 6 user root    4096 2009-05-19 21:21 etpro
-rwxr-xr-x 1 user root  1604328 2009-05-19 22:15 et.x86
-rw-r--r-- 1 user root     1290 2009-05-19 21:45 ET.xpm
-rw-r--r-- 1 user root    14550 2009-05-19 21:45 EULA_Wolfenstein_Enemy_Territory.txt
-rw-r--r-- 1 user root      287 2009-05-19 21:45 openurl.sh
drwxrwxr-x 4 user root     4096 2009-12-16 22:31 pb
-rw-r--r-- 1 user user     206 2009-05-19 21:56 pbcl.db

```

7. Remember: To start the game with etpro;
```
et +set fs_game etpro

```

Probably my favourite game, now running pretty nicely on Kubuntu Karmic i686. [My cfg]("http://koti.kapsi.fi/~no_one/etcfg/No_OnE.cfg.zip") to set an example, hardware dependent gfx commented out by default. Remember to [configure your mouse]("http://ubuntuforums.org/showpost.php?p=8462984&postcount=4"), chances are you'll need a good one to keep up ;)

@pribina: Your ET Client is executing a default configuration script for the program to detect settings and as a part of it changing rendering and graphics options(, which seems to fail with a status 11). In short the script could be so outdated or you might have some problems with your graphics drivers. So check those and more importantly configure the game by making a textfile called "autoexec.cfg" in your ~/.wolfet/etmain and setting average graphics properties.

---

### Post by jgardner16 on 2009-12-24
Every time I download enemy territory and I get md5 checksum error.  
I have tried running like sudo su ./enemy_territory and just executing the file always they same.  I have downloaded 4 times now.  I am using Ubuntu 9.1 any ideas?

---

### Post by dannyboy79 on 2009-12-27
when i go to install esound i get this:

The following packages are BROKEN:
  pulseaudio-esound-compat 
The following NEW packages will be installed:
  esound 
The following packages will be REMOVED:
  abiword-common{u} blop{u} caps{u} cmt{u} dvipdfmx{u} freebirth-data{u} giblib1{u} gstreamer0.10-gnonlin{u} guile-1.8{u} kdelibs-data{u} 
  kdelibs4c2a{u} libaiksaurus-1.2-0c2a{u} libaiksaurus-1.2-data{u} libaiksaurusgtk-1.2-0c2a{u} libaubio2{u} libaudclient2{u} 
  libaudcore1{u} libaudid3tag2{u} libaudutil1{u} libavahi-qt3-1{u} libbinio1ldbl{u} libdjconsole-data{u} libdjconsole0{u} libftgl2{u} 
  libgdome2-0{u} libgdome2-cpp-smart0c2a{u} libgoocanvas-common{u} libgoocanvas3{u} libgtkmathview0c2a{u} liblink-grammar4{u} 
  liblualib50{u} libmpeg3-1{u} libmxml1{u} libots0{u} libprojectm-data{u} libprojectm2{u} libresid-builder0c2a{u} libsad2{u} 
  libsidplay2{u} libsigc++-1.2-5c2{u} libstk0c2a{u} libt1-5{u} libvamp-hostsdk2{u} libvamp-sdk1{u} libwv-1.2-3{u} lilypond{u} 
  lilypond-data{u} lilypond-doc{u} link-grammar-dictionaries-en{u} lmodern{u} mixxx-data{u} mscore-common{u} python-pygoocanvas{u} 
  python-qt4-dbus{u} python-twisted{u} python-twisted-lore{u} python-twisted-mail{u} python-twisted-news{u} python-twisted-runner{u} 
  python-twisted-words{u} stk{u} tap-plugins{u} tex-common{u} texinfo{u} texlive-base{u} texlive-base-bin{u} texlive-base-bin-doc{u} 
  texlive-common{u} texlive-doc-base{u} winbind{u} wine{u} wine-gecko{u} 
0 packages upgraded, 1 newly installed, 72 to remove and 0 not upgraded.
Need to get 23.7kB of archives. After unpacking 541MB will be freed.
The following packages have unmet dependencies:
  pulseaudio-esound-compat: Conflicts: esound but 0.2.41-5 is to be installed.
The following actions will resolve these dependencies:

Remove the following packages:
pulseaudio-esound-compat

Leave the following dependencies unresolved:
pulseaudio recommends pulseaudio-esound-compat
Score is -81

i don't care that it will remove all that stuff i don't think but I am concerned about enemy territory playing nice in pulseaudio is the pulseaudio-esound-compat will be removed.

---

### Post by dannyboy79 on 2009-12-29
bump, please see previous thread

---

### Post by dannyboy79 on 2009-12-30
anyone using enemy territoy in karmic? please help with pulseaudio-esound-compat questions

---

### Post by davygrvy on 2009-12-30
ditto.  audio not working.  pulseaudio-esound-compat installed.

"Could not open /dev/dsp"

$ ls -la /dev/dsp
crw-rw----+ 1 root audio 14, 3 2009-12-27 14:59 /dev/dsp

Yes, users are all part of the 'audio' group.

---

### Post by davygrvy on 2009-12-31
Working on a solution now: [http://nullkey.ath.cx/et-sdl-sound/](http://nullkey.ath.cx/et-sdl-sound/)

Will compile from source as I'm on amd_64 (2.6.31-16-generic #52-Ubuntu SMP Thu Dec 3 22:07:16 UTC 2009 x86_64 GNU/Linux) here.  Will post results in a few.

EDIT: no soup for me, but came close.  Apparently the CRC for my build of ET isn't the known one the author used, so the rewrites are probably located in the wrong places.

FYI, don't rebuild et-sdl-sound for -m64 as it is a shared library and won't load into ET as it is build as a 32-bit target.

---

### Post by swatsbiz on 2010-02-19
How-a-bout this method for installing TC:E ?

[http://tavinho-mx.blogspot.com/2009/12/install-true-combatelite-on-ubuntu-910.html](http://tavinho-mx.blogspot.com/2009/12/install-true-combatelite-on-ubuntu-910.html)

enjoy

---

### Post by Doctor Drive on 2010-02-21
[deleted]...

---

### Post by aktheus on 2010-03-22
I've finally installed and run ET, after doing the 4th option to enable sound ([https://help.ubuntu.com/community/EnemyTerritory](https://help.ubuntu.com/community/EnemyTerritory)) but now, i cant quit. i have to reset my laptop once i've finished playing, maybe God is telling me to not quit, but i would like to close the program properly.
thank dont know if it is the proper place to ask...

New ubuntu(linux) user.

---

### Post by Jart44 on 2010-05-27
Hi,
I'm trying to uninstall Wlfenstein ET here:[https://help.ubuntu.com/community/EnemyTerritory#Troubleshooting](https://help.ubuntu.com/community/EnemyTerritory#Troubleshooting) but I get permission denied in my terminal box
Any help would be appreciated.

---

### Post by eexpress on 2010-06-01
part of my et.bash, can solv sound.

```
f='/proc/asound/card0/pcm0p/oss'

grep 'et.x86' $f
if [ $? -ne 0 ]; then
echo "****-----add sound programe-----"
sudo -s 'echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss'
fi

```

btw: I always offline from servers(become zoombie), more than one time every map. sometimes, after game quit, also can see lot of web transfer with server/isp, when i use iftop to look up. ping too high? or 1G ram is too small?

use 10.04. asus laptop. J20C?

---

### Post by tuesday20102001 on 2010-06-23
current distro: Xubuntu 9.10:

the fix for sound that works for me:
et-sdl-sound

I used the old package for this hack: [http://nullkey.ath.cx/~stuff/et-sdl-sound/et-sdl-sound.tar.gz](http://nullkey.ath.cx/~stuff/et-sdl-sound/et-sdl-sound.tar.gz)

Extract sound to preferred location: /usr/share/game/enemy-territory/


###Optional: required if game install in different directory

Modify et-sdl-sound: Sudo vim /usr/share/games/enemy-territory/et-sdl-sound

# Do not touch anything below this line!
SCRIPT_NAME='et-sdl-sound'
GAME_BIN='et.x86'
#change the following line to the current install directory

GAME_DIR='/usr/local/share/games/enemy-territory'

ET_SDL_SOUND_LIB=''\


##!wq to save and close file

###now you will have to start the game from the new et-sdl-sound file

sh ./usr/share/games/enemy-territory/et-sdl-sound/et-sdl-sound
___________________________________________________________

Sound should be working :popcorn:

---

### Post by old_codger on 2010-07-13
> **aktheus said:**
> I've finally installed and run ET, after doing the 4th option to enable sound ([https://help.ubuntu.com/community/EnemyTerritory](https://help.ubuntu.com/community/EnemyTerritory)) but now, i cant quit. i have to reset my laptop once i've finished playing, maybe God is telling me to not quit, but i would like to close the program properly.
thank dont know if it is the proper place to ask...

New ubuntu(linux) user.

That might be related to something I've noticed, (and I have to run a shell script 'thingy' to get sound working as well:(), that the application puts me back to my screensaver when it finishes... unless I've been playing for only a minute or so. So maybe your screen saver or power saving is active and fails to respond properly?

Might be worth investigating.

Maybe check out your log files?

---

### Post by Sefianix on 2010-11-06
I've reinstalled ET (after giving up a while back) to see if I could get it to run completely in kubuntu Lucid 64bit.  I installed through getdeb binaries.  I have sound and all comes up but my mouse is stuck in the upper left.  I have to use the keyboard to quit the game.  I could give the output I get when i run **et** on the commandline if someone can give me the command for capturing output.  Please somebody assist me with this.  ](*,)

---

### Post by ngrieb on 2011-09-11
I'm having problems with sound on ET and its derivatives (TC:E and TC:CQB). I have attempted the fixes, and my problem is I get these error messages:
```

------- sound initialization -------
/dev/dsp: No such file or directory
Could not open /dev/dsp

```

I have tried the script fix:
```

sudo apt-get install libsdl1.2debian-alsa
To get and make the script installable

wget -q -O - http://nullkey.kapsi.fi/et-sdl-sound/et-sdl-sound.gz | gzip -d > et-sdl-sound && chmod a+x et-sdl-sound

```
, which does work for et when running the et-sdl-sound code with the alsa setup, but how do I produce the sound lib and preload it so that I don't have to run the script every time? Also how can I modify this script to work with True Combat: Elite? 

Thanks for your help.

---

### Post by xdarkknight on 2011-10-16
Ok, I've installed everything (no sound yet..., to be fixed later) it boots, pulls up server lists and allows me to attempt to enter.  HOWEVER, every server I try it starts to load, then kicks me out, back to the main menu with an error message saying > "You have an invalid GUID. This may be a temporary problem. You should try reconnecting."  So I click "Reconnect" and it boots me back to the menu and error message.

Also, I want to try out TC:E and CQB at some point, but... I go back to the original problem.

I know this is an incredibly geriatric thread, and therefore things like "libgtk1.2" no longer apply (as we're now on libgtk v. 3.0).

The game is a bit aged, but it looks good and if penguspy is right, it's a killer game.
______________________
xdk
---------------------------------
*it's a shame about the misconception of open sourced software.  It's meant to be open **source**, not open* ***ended****!*

---

### Post by namocypaktu on 2012-05-30
Hello everybody it's my first post here, few days ago I try to install ET on my ubuntu, but I can't do it ;o Before I haven't got problem with it, can u help me?

```
michal@ubuntu:~$ ./et-linux-2.55.x86.run
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.55.............................................................................................................................................
It is recommended to install as the super user
Please enter the root password or hit enter to continue as is
Password: 
su: Authentication failure
The setup program seems to have failed on x86/unknown

See http://zerowing.idsoftware.com/linux/ for troubleshooting
```

For sure I installed (libglib1.2 ; libgtk1.2-common ; libgtk1.2), and I have 32 bit version of ubuntu.

---

### Post by paulbuede on 2013-02-04
So, synaptic has Enemy Territory, I installed it that way, sound works, but mouse doesn't.  The mouse starts in the upper left corner and as soon as I start to move the mouse it slides quickly off the bottom right and never comes back.... Any ideas on that?  I have seen stuff here and there about DGA being a problem and maybe needing to edit my xfree config file, but not sure what to do?  I am running ubuntu 12.10 64bit.

Thanks

---

