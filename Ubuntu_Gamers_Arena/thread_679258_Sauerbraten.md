---
title: "Sauerbraten"
date: 2008-01-26
forum: Ubuntu Gamers Arena
---

### Post by Elena678 on 2008-01-26
hello, i installed Sauerbraten with the package manager. but when i try to run it my screen is going black for 2 sec, and it turns back to the desktop, do somebody know what's the problem??

greetings

---

### Post by Perfect Storm on 2008-01-27
Try launch it from the terminal, please post the output.

---

### Post by matthewschwimmer on 2008-01-28
me@me-laptop:/usr/games$ sauerbraten 
init: sdl
init: enet
init: video: mode
init: video: misc
init: console
init: gl
Renderer: Mesa DRI Intel(R) 965GM 4.1.3002 x86/MMX/SSE2 (Tungsten Graphics, Inc)
Driver: 1.4 Mesa 7.0.1
WARNING: Using floating point vertexes. (use "/floatvtx 0" to disable)
Rendering using the OpenGL 1.5 assembly shader path.
WARNING: No occlusion query support! (large maps may be SLOW)
WARNING: No framebuffer object support. (reflective water may be slow)
Segmentation fault (core dumped)

I even tried it with -opengl (i thought it was a good idea at the time), but nothing different happened.

---

### Post by Perfect Storm on 2008-01-29
Make sure that **xserver-xorg-video-intel** is installed.

afterwards
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

pick the right driver that fit your video card.

---

### Post by matthewschwimmer on 2008-01-29
I did> sudo dpkg-reconfigure -phigh xserver-xorg, but all I get is> xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080129163016

---

### Post by Perfect Storm on 2008-01-29
Okay boot up in safemode and the commands.

---

### Post by matthewschwimmer on 2008-01-30
Huh? What is safemode? Is> $ sudo susafemode? Because if it is, I still got the> xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080129224459message.

---

### Post by Perfect Storm on 2008-01-30
you can choose safemode when Ubuntu boots up and you see the countdown menu, hit esc. and choose failsafe

---

### Post by matthewschwimmer on 2008-01-30
haha, thats funny. The only time my computer froze was in safemode.

Anyways, I still got the same message. Do you think I am doing something wrong?

---

### Post by Perfect Storm on 2008-01-30
No, but I might suspect that sauerbraten uses some 3D stuff which intel cards doesn't support.
I'm no expert on intel cards.

Do other 3D suff (games, effects etc) work?

---

### Post by matthewschwimmer on 2008-01-30
Yeah, I can get alien arena, tremulous, warsow, and some other ones too. Sauerbraten and regnum are the only ones giving me problems.

---

### Post by Elena678 on 2008-01-31
sorry for the late response, i could not find the command to run it in the terminal, this is what i see when i run it in the terminal:
```
init: sdl
init: enet
init: video: mode
init: video: misc
init: console
init: gl
Renderer: Mesa GLX Indirect (Mesa project: www.mesa3d.org)
Driver: 1.2 (2.1 Mesa 7.0.1)
WARNING: No vertex_buffer_object extension! (geometry heavy maps will be SLOW)
Rendering using the OpenGL 1.5 assembly shader path.
WARNING: No occlusion query support! (large maps may be SLOW)
COMPILE ERROR (VS:caustic) - (null)
!!ARBvp1.0
    OPTION ARB_position_invariant;
        ATTRIB opos = vertex.position; 

        DP3 result.texcoord[0].x, opos, state.texgen.object.s;
        DP3 result.texcoord[0].y, opos, state.texgen.object.t;
        
    TEMP fogplane;
    MAD fogplane, state.matrix.modelview.row[2], program.env[9].x, program.env[9].yyzw;
    DP4 result.fogcoord, -opos, fogplane;

        END
    [2]Q
        
    !!ARBfp1.0
    
    OPTION ARB_precision_hint_fastest;
    


        OPTION ARB_fog_linear;
        
    TEMP caustic, caustic2;
    TEX caustic, fragment.texcoord[0], texture[0], 2D;
    TEX caustic2, fragment.texcoord[0], texture[1], 2D;
    LRP result.color, program.env[0], caustic2, caustic;

        END
    MP  COMPILE ERROR (VS:caustic) - (null)Qp&#65533;÷p&#65533;÷he, light, cam, bump, invfresnel, temp, dudv;

        ATTRIB projtc = fragment.texcoord[0];
        ATTRIB tc1 = fragment.texcoord[1];
        ATTRIB tc2 = fragment.texcoord[2];
        ATTRIB camts = fragment.texcoord[3];
        

        
        DP3 cam.w, camts, camts;
        RSQ cam.w, cam.w;
        MUL cam.xyz, cam.w, camts;

        

        TEX dudv, tc1, texture[2], 2D;
        MAD dudv.xy, dudv, 2, -1;

        
    TEMP reflect, refract;

    MAD temp, dudv, 0.4, projtc;
    TXP reflect, temp, texture[0], 2D;
    TXP refract, temp, texture[3], 2D;

    MAD temp, dudv, 0.025, tc2;
    TEX bump, temp, texture[1], 2D;
    MAD bump.xyz, bump, 2, -1;


        

        
    DP3_SAT invfresnel, cam, bump;
    MAD invfresnel, invfresnel, 0.5, 0.5;
    LRP result.color, invfresnel, refract, reflect;


        END
      ]
P8
    spec = $arg2
    distort = $arg3
    combine = $arg4
    shader 1 $arg1 [
        @vpstart
        TEMP tc;
        PARAM campos = program.env[0];
        PARAM seconds = program.env[1];
        @(if $spec [result "PARAM lightpos = program.env[2];"])

        DP4 result.texcoord[0].x, state.matrix.texture.row[0], opos;
        DP4 result.texcoord[0].y, state.matrix.texture.row[1], opos;
        DP4 result.texcoord[0].z, state.matrix.texture.row[2], opos;
        DP4 result.texcoord[0].w, state.matrix.texture.row[3], opos;
        MUL tc, vertex.texcoord[0], 0.1;
        MAD result.texcoord[1], seconds, 0.04, tc;
        MAD result.texcoord[2], seconds, -0.02, tc;
        SUB result.texcoord[3], campos, opos;
        @(if $spec [result "SUB result.texcoord[4], lightpos, opos;"])
 
        MOV result.color, vertex.color;

        @fogcoord

        END
    ] [
        @fpstart
        OPTION ARB_fog_linear;
        TEMP he, light, cam, bump, invfresnel, temp, dudv;

        ATTRIB projtc = fragment.texcoord[0];
        ATTRIB tc1 = fragment.texcoord[1];
        ATTRIB tc2 = fragment.texcoord[2];
        ATTRIB camts = fragment.texcoord[3];
        @(if $spec [result "ATTRIB lightts = fragment.texcoord[4];"])

        @(normalize cam camts)
        @(if $spec [result [
            @(normalize light lightts)
            ADD he, cam, light;
            @(normalize he he)
        ]])

        TEX dudv, tc1, texture[2], 2D;
        MAD dudv.xy, dudv, 2, -1;

        @distort

        @(if $spec [result [
            PARAM specfactor = 96;

            DP3_SAT he, he, bump;
            POW he, he.x, specfactor.w;
    
            MUL light, program.env[4], light.w;
            RCP_SAT light, light.x;
            MAD light, light, -program.env[3], program.env[3];
        ]])

        @combine

        END
    ]
    qH&#1585;÷3 ca (3 cam.w, camts, camts;
        RSQ %2;
)&#65533;&#65533;÷&#65533;&#65533;÷&#65533;&#65533;÷&#65533;&#65533;÷at&#65533;p&#65533;  
            TEX scaled, fragment.texcoord[1], texture[1], RECT;
            DP3 t, scaled, { 0.3, 0.5, 0.2, 1 };    
            MUL t, t, t;
            MUL t, t, scaled;
            MAD sample, t, program.env[0].x, sample;
          
            TEX scaled, fragment.texcoord[2], texture[2], RECT;
            DP3 t, scaled, { 0.3, 0.5, 0.2, 1 };    
            MUL t, t, t;
            MUL t, t, scaled;
            MAD sample, t, program.env[0].x, sample;
          
            TEX scaled, fragment.texcoord[3], texture[3], RECT;
            DP3 t, scaled, { 0.3, 0.5, 0.2, 1 };    
            MUL t, t, t;
            MUL t, t, scaled;
            MAD sample, t, program.env[0].x, sample;
          
            TEX scaled, fragment.texcoord[4], texture[4], RECT;
            DP3 t, scaled, { 0.3, 0.5, 0.2, 1 };    
            MUL t, t, t;
            MUL t, t, scaled;
            MAD sample, t, program.env[0].x, sample;
          
            TEX scaled, fragment.texcoord[5], texture[5], RECT;
            DP3 t, scaled, { 0.3, 0.5, 0.2, 1 };    
            MUL t, t, t;
            MUL t, t, scaled;
            MAD sample, t, program.env[0].x, sample;
          
            TEX scaled, fragment.texcoord[6], texture[6], RECT;
            DP3 t, scaled, { 0.3, 0.5, 0.2, 1 };    
            MUL t, t, t;
            MUL t, t, scaled;
            MAD sample, t, program.env[0].x, sample;
        &#65533;&#65533;
        
    !!ARBfp1.0
    
    OPTION ARB_precision_hint_fastest;
    


        OPTION ARB_fog_linear;
        TEMP he, light, cam, bump, invfresnel, temp, dudv;

        ATTRIB projtc = fragment.texcoord[0];
        ATTRIB tc1 = fragment.texcoord[1];
        ATTRIB tc2 = fragment.texcoord[2];
        ATTRIB camts = fragment.texcoord[3];
        ATTRIB lightts = fragment.texcoord[4];

        
        DP3 cam.w, camts, camts;
        RSQ cam.w, cam.w;
        MUL cam.xyz, cam.w, camts;

        
            
        DP3 light.w, lightts, lightts;
        RSQ light.w, light.w;
        MUL light.xyz, light.w, lightts;

            ADD he, cam, light;
            
        DP3 he.w, he, he;
        RSQ he.w, he.w;
        MUL he.xyz, he.w, he;

        

        TEX dudv, tc1, texture[2], 2D;
        MAD dudv.xy, dudv, 2, -1;

        
    TEMP reflect, refract;

    MAD temp, dudv, 0.025, tc2;
    TEX bump, temp, texture[1], 2D;
    MAD bump.xyz, bump, 2, -1;
    TEX dudv, temp, texture[2], 2D;
    MAD dudv.xy, dudv, 2, -1;

    RCP temp.w, projtc.w;
    MUL temp.xyz, projtc, temp.wwww; 
    MAD temp.xy, dudv, 0.01, temp;

    TEX reflect, temp, texture[0], 2D;
    TEX refract, temp, texture[3], 2D;


        
            PARAM specfactor = 96;

            DP3_SAT he, he, bump;
            POW he, he.x, specfactor.w;
    
            MUL light, program.env[4], light.w;
            RCP_SAT light, light.x;
            MAD light, light, -program.env[3], program.env[3];
        

        
    DP3_SAT invfresnel, cam, bump;
    MAD invfresnel, invfresnel, 0.5, 0.5;
    LRP temp, invfresnel, refract, reflect;
    MAD result.color, he, light, temp;


        END
    1&#65533;Segmenteringsfel (core dumped)

```

---

### Post by blastradius on 2008-04-26
Same problem here although I'm running an ATI Radeon 9600, no probs with 3D but same brief black screen and then back to the desktop.

Here's what I got when I ran it fron the command line:-

eric@blastradius:~$ sudo dpkg-reconfigure -phigh xserver-xorg
[sudo] password for eric:
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080426132926
eric@blastradius:~$ sauerbraten
init: sdl
init: enet
init: video: mode
init: video: misc
init: console
init: gl
Renderer: Mesa DRI R300 20060815 AGP 8x TCL (DRI R300 Project)
Driver: 1.3 Mesa 7.0.1
Rendering using the OpenGL 1.5 assembly shader path.
WARNING: No occlusion query support! (large maps may be SLOW)
WARNING: No framebuffer object support. (reflective water may be slow)
WARNING: Non-power-of-two textures not supported!
Segmentation fault (core dumped)

---

### Post by blastradius on 2008-04-27
I've just found exactly the same problem with Frets on Fire!

---

### Post by cleatus on 2008-05-01
Newbie question what do i need to do to get this running.....here is output when I run sauerbraten....
Using home directory: /home/jason/.sauerbraten
init: sdl
init: enet
init: video: mode
init: video: misc
init: gl
Renderer: GeForce4 MX 4000/PCI/SSE (NVIDIA Corporation)
Driver: 1.2 (1.5.8 NVIDIA 96.43.05)
WARNING: No vertex_buffer_object extension! (geometry heavy maps will be SLOW)
WARNING: No occlusion query support! (large maps may be SLOW)
WARNING: No shader support! Using fixed function fallback. (no fancy visuals for you)
WARNING: Using NVIDIA texgen bug workaround. (use "/nvidia_texgen_bug 0" to disable if unnecessary)
WARNING: No framebuffer object support. (reflective water may be slow)
WARNING: Non-power-of-two textures not supported!
init: console
init: gl: effects
init: world
init: sound
init: cfg
Could not set gamma (card/driver doesn't support it?)
sdl: Gamma correction not supported on this visual
init: localconnect
init: mainloop
read map packages/base/metl4.ogz (0.4 seconds)
Mining Station by metlslime
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  148 (GLX)
  Minor opcode of failed request:  2 (X_GLXRenderLarge)
  Serial number of failed request:  801
  Current serial number in output stream:  803
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6e82767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb6e8281e]
#2 /usr/lib/libX11.so.6 [0xb794f518]
#3 /usr/lib/libX11.so.6(XESetCloseDisplay+0x31) [0xb79328d1]
#4 /usr/lib/libGL.so.1 [0xb7d294d5]
#5 /lib/tls/i686/cmov/libc.so.6(exit+0xd4) [0xb7a25084]
#6 /usr/lib/libX11.so.6 [0xb794863e]
#7 /usr/lib/libSDL-1.2.so.0 [0xb7e745a6]
#8 /usr/lib/libX11.so.6(_XError+0xfe) [0xb794873e]
#9 /usr/lib/libX11.so.6 [0xb794fe5c]
#10 /usr/lib/libX11.so.6(_XReply+0x15a) [0xb795021a]
#11 /usr/lib/libGL.so.1 [0xb7d418c6]
#12 /usr/lib/libGLU.so.1(gluBuild2DMipmaps+0x63) [0xb7c92c13]
#13 ./sauer_client [0x80d0d7f]

---

### Post by failte200 on 2008-08-19
I too get the segfault (AMD x2-64, ATI proprietary driver) but ONLY WHEN I FIRE A GUN.  I can walk around to my heart's content, change maps, play with options... whatever, right until I click the mouse to fire a gun.

Weird.

And I was really looking forward to a game with monsters, too, rather than the now-typical pure-Deathmatch-type games.  Guess I'll have to give Doom another shot.  Never gotten it to work, either.

One thing I've learned - Compiz will trash 3D-games.  Too bad.

---

### Post by dppowell on 2008-08-27
bump?

---

### Post by MattressVon on 2008-12-22
This does the trick:

[http://gaming.gwos.org/doku.php/guides:64bit:sauerbraten](http://gaming.gwos.org/doku.php/guides:64bit:sauerbraten)

:guitar:

---

