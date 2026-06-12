---
title: "Videos player wont show video"
date: 2019-05-17
forum: Ubuntu/Debian BASED
---

### Post by ray42 on 2019-05-17
Everything used to be fine. I can only get sound now. I think the player is called Totem?

---

### Post by oldos2er on 2019-05-17
What distro are you running?

---

### Post by ray42 on 2019-05-24
Pop 18.04 LTS

---

### Post by ray42 on 2019-05-28
bump

---

### Post by Frogs Hair on 2019-05-28
Try the following commands one at a time.

```
sudo apt install libdvdnav4 libdvdread4 gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly libdvd-pkg 
``````
sudo dpkg-reconfigure libdvd-pkg

```

---

### Post by SeijiSensei on 2019-05-29
Or try another video player like SMPlayer with mpv as the engine. 

```
sudo apt install smplayer mpv
```

---

### Post by ray42 on 2019-05-29
Hmm, both these report that everything is installed and already at the latest version?

---

### Post by ray42 on 2019-05-29
Thanks, I also use VLC but I like the simplicity of Totem for quick views

---

### Post by ray42 on 2019-05-30
I have some errors when I run Totem in terminal.


```
(totem:3586): GLib-CRITICAL **: 18:24:30.704: g_key_file_load_from_file: assertion 'file != NULL' failed


(totem:3586): Cogl-WARNING **: 18:26:13.085: Shader compilation failed:
0:90(21): warning: `cogl_layer0' used uninitialized
0:103(21): warning: `cogl_layer1' used uninitialized
0:116(21): warning: `cogl_layer2' used uninitialized
0:127(16): error: no function with name 'clutter_gst_sample_video3'




(totem:3586): Cogl-WARNING **: 18:26:13.085: Failed to link GLSL program:
error: linking with uncompiled/unspecialized shader




(totem:3586): Cogl-WARNING **: 18:26:13.085: driver/gl/cogl-pipeline-progend-glsl.c:384: GL error (1282): Invalid operation




(totem:3586): Cogl-WARNING **: 18:26:13.085: driver/gl/cogl-pipeline-progend-glsl.c:399: GL error (1282): Invalid operation




(totem:3586): Cogl-WARNING **: 18:26:13.085: driver/gl/cogl-pipeline-progend-glsl.c:409: GL error (1282): Invalid operation




(totem:3586): Cogl-WARNING **: 18:26:13.085: driver/gl/cogl-pipeline-progend-glsl.c:384: GL error (1282): Invalid operation




(totem:3586): Cogl-WARNING **: 18:26:13.085: driver/gl/cogl-pipeline-progend-glsl.c:399: GL error (1282): Invalid operation




(totem:3586): Cogl-WARNING **: 18:26:13.085: driver/gl/cogl-pipeline-progend-glsl.c:409: GL error (1282): Invalid operation




(totem:3586): Cogl-WARNING **: 18:26:13.085: driver/gl/cogl-pipeline-progend-glsl.c:384: GL error (1282): Invalid operation




(totem:3586): Cogl-WARNING **: 18:26:13.085: driver/gl/cogl-pipeline-progend-glsl.c:399: GL error (1282): Invalid operation




(totem:3586): Cogl-WARNING **: 18:26:13.085: driver/gl/cogl-pipeline-progend-glsl.c:409: GL error (1282): Invalid operation




(totem:3586): Cogl-WARNING **: 18:26:13.085: driver/gl/cogl-pipeline-progend-glsl.c:384: GL error (1282): Invalid operation




(totem:3586): Cogl-WARNING **: 18:26:13.085: driver/gl/cogl-pipeline-progend-glsl.c:399: GL error (1282): Invalid operation




(totem:3586): Cogl-WARNING **: 18:26:13.085: driver/gl/cogl-pipeline-progend-glsl.c
```

---

### Post by ray42 on 2019-06-29
Bump

I have noticed that it does play .wbm files. Is there any video codecs missing?

---

### Post by ray42 on 2019-08-08
bump

---

### Post by uRock on 2019-08-08
Have you created a bug report with Totem? You said you also use VLC, does the video format in question work on VLC? Plan C might be to use FFMPEG to convert to another format.

---

### Post by ray42 on 2019-09-09
I think this is local as it works with other login

---

