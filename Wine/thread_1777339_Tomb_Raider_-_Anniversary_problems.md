---
title: "Tomb Raider - Anniversary problems"
date: 2011-06-07
forum: Wine
---

### Post by 3602 on 2011-06-07
So I'm having problems with this game despite a Platinum rating on AppDB.
When I run the game, I hear sound but I get no graphics. Two out of ten times x.org would crash and restart itself, much like a log-out.
What to do?

Thank you very much.

---

### Post by 3602 on 2011-06-07
xterm printout:
```
 wine tra.exe
fixme:ole:CoInitializeSecurity (0x453138,-1,(nil),(nil),6,2,(nil),64,(nil)) - stub!
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:gameux:GameExplorerImpl_VerifyAccess (0x14bd08, L"C:\\Program Files\\Tomb Raider - Anniversary\\tra.exe", 0xe8f394)
fixme:win:EnumDisplayDevicesW ((null),0,0xe8eea4,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x11923280,0x11923cf0): stub
fixme:advapi:RegisterTraceGuidsW (0x3d24d0, 0x3dd6e8, {7c830ece-5fb3-417a-a1bd-508f45277356}, 1, 0xe8efcc, (null), (null), 0x3dd6f0,): stub
fixme:wbemprox:wbem_locator_ConnectServer 0x1260aa80, L"\\\\.\\root\\cimv2", (null), (null), (null), 0x00000000, (null), (nil), 0xe8ed78)
fixme:wbemprox:wbem_locator_ConnectServer 0x13175320, L"\\\\.\\root\\cimv2", (null), (null), (null), 0x00000000, (null), (nil), 0xe8ed88)
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #1:
fixme:d3d_shader:print_glsl_info_log     Vertex shader(s) linked.
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #4:
fixme:d3d_shader:print_glsl_info_log     Vertex shader(s) linked.
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #7:
fixme:d3d_shader:print_glsl_info_log     Vertex shader(s) linked, fragment shader(s) linked.
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #13:
fixme:d3d_shader:print_glsl_info_log     Vertex shader(s) linked, fragment shader(s) linked.
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #14:
fixme:d3d_shader:print_glsl_info_log     Vertex shader(s) linked, fragment shader(s) linked.
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #17:
fixme:d3d_shader:print_glsl_info_log     Fragment shader(s) linked.
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #19:
fixme:d3d_shader:print_glsl_info_log     Fragment shader(s) linked.
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #21:
fixme:d3d_shader:print_glsl_info_log     Fragment shader(s) linked.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #23:
fixme:d3d_shader:print_glsl_info_log     Vertex shader(s) linked.

```

---

### Post by 3602 on 2011-06-07
Well, installed DirectX 9.0c and still not running.
Here's to my money!

---

### Post by 3602 on 2011-06-08
Bump after total system re-install.

---

### Post by 3602 on 2011-06-10
Bump.

EDIT: Even with POL, *twice installed*, just audio, no video. I cam somehow "blindly" control the game because I can hear distinctive sounds when I press the arrow keys.

---

### Post by 3602 on 2011-06-10
Marking solved. I installed Windows.

---

### Post by GTMoraes on 2011-06-12
Or just create a little creepy partition with windoze xp for playing. With a shutdown time of less than 5 seconds and boot-up of 20, you won't feel Ubuntu shutting down, and then starting up when you're done gaming.

---

### Post by 3602 on 2011-06-13
> **GTMoraes said:**
> Or just create a little creepy partition with windoze xp for playing. With a shutdown time of less than 5 seconds and boot-up of 20, you won't feel Ubuntu shutting down, and then starting up when you're done gaming.
Exactly what I did. Now I just need a little tweak to bring down the 30-second NT loader...
Anyway, XP... What the heck? I installed HL2 and its episodes plus TRA and now I have little disk space left (sliced it 40GB; now 10GB left). Hmm... When I find more good games (or games that I've been itching to play for years, like said TRA) I should probably boot Gparted again and slice a D:/ disk.

---

### Post by GTMoraes on 2011-06-13
God, how it would be nice if XP could read my 250GB XFS Partition. I've only left it with a 20gb slice, and by himself, almost took everything.

On a side note:
Heh, I'm particularly itching to play Portal 2, looks outstanding.
Just need to find a place to buy it, without taking my eyes off

---

### Post by 3602 on 2011-06-14
Heck I just checked and I got only 7GB left. 
During the last couple of days of heavy HL2-ing (read: 8AM to 2AM sessions) I am left heavily imprinted (read: traumatized) as whenever I leave the TV or my room, my left hand would uncontrollably do a "press F6" gesture... If you don't know, that's the default key for quick-save.
Should stop thinking about Alyx and go take a walk or somethin'. Right now, it is a good thing that Episode 3 is not out.

---

### Post by GTMoraes on 2011-06-14
> **3602 said:**
> Heck I just checked and I got only 7GB left. 
During the last couple of days of heavy HL2-ing (read: 8AM to 2AM sessions) I am left heavily imprinted (read: traumatized) as whenever I leave the TV or my room, my left hand would uncontrollably do a "press F6" gesture... If you don't know, that's the default key for quick-save.
Should stop thinking about Alyx and go take a walk or somethin'. Right now, it is a good thing that Episode 3 is not out.

gosh, I have the same feeling, specially when I'm going to do a fast maneuver on the road..

Or, when I was still playing the sims, while on a waiting Line, I had a feeling to press Num3 (The Sims's super speed).

Do you know what this means?



















Nothing.

---

