---
title: "Video card + Linux + GRID"
date: 2009-09-28
forum: Wine
---

### Post by Capt. Blackwood on 2009-09-28
Ok so i install Race Driver Grid in windows, and it runs in Ubuntu :D.

I was reading this [http://appdb.winehq.org/objectManager.php?sClass=version&iId=14834](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14834)

and these entries:
I recommend to set:
HKCU/Software/Wine/Direct3D/Multisampling=enabled
HKCU/Software/Wine/Direct3D/VideoMemorySize=YourVideoRAMSize
How do i put this in through the wine Regedit. I know if i installed via wine those entries might be there...but i'm using 1.1.30 and have to do this manually.

It's also kinda laggy in the control department...handles like i'm drunk.

---

### Post by castlefox on 2009-09-29
What are your hardware specs ?

Is there any way to tell how many frames per sec you are getting?

---

### Post by Capt. Blackwood on 2009-09-30
Motherboard: Asus Commando
Processor: Intel Core 2 Duo Processer @ 2x 2.67gHz
Ram: 3x 1GB corsair PC6400 DDR2 RAM
GPU: Asus nVidia GeForce 9800 GT
Sound: Soundblaster X-Fi Fatality Champion.

OS: Ubuntu 9.04 Jaunty

Running default drivers on all parts.


FPS: 20-30

Game's stuff has NOT been tweaked yet

---

### Post by castlefox on 2009-10-01
You might want to update your graphic driver for the nVidia GeForce 9800 GT.  


What resolution are you trying to play the game at?

---

### Post by Capt. Blackwood on 2009-10-02
Got better my config :D
      
&#8722;
<hardware_settings_config version="39">
&#8722;
<cpu>
<threadStrategy parallelUpdateRender="true" workerMapFile="system/workerMap2Core.xml" forceFeedbackProcessor="1" dvdStorageProcessor="1" dataSetMonitorProcessor="0" renderProcessor="0" updateProcessor="1" fileStreamProcessor="1"/>
</cpu>
&#8722;
<audio_card>
<audio mixing="default" reverbs="1" voices="120" creation="auto"/>
</audio_card>
&#8722;
<graphics_card>
&#8722;
<resolution width="1280" height="1024" aspect="normal" fullscreen="true" vsync="0" oldWidth="1280" oldHeight="1024">
<refreshRate rate="60"/>
</resolution>
<gamma level="1.0"/>
&#8722;
<multisampling option="4xmsaa">
<back_buffer level="4xmsaa"/>
<colour_target level="4xmsaa"/>
<minimap level="4xmsaa"/>
<dynamic_envmap level="0"/>
<static_envmap level="0"/>
<rear_view_mirror level="0"/>
</multisampling>
<textures lod="0"/>
</graphics_card>
<graphics_detail level="high"/>
<wind particles="true" groundcover="true"/>
<shadows enabled="true" size="2048" maskQuality="2"/>
<headlights headlightQuality="2"/>
<particles enabled="true" collisions="true" max="4000"/>
<crowd enabled="true"/>
<cloth enabled="true"/>
<postprocess enabled="true" blur="true"/>
<groundcover enabled="true" layers="4"/>
<trees visibility="2000" low="180" high="60" lodQuality="2"/>
<vehicles characterQuality="3" lodQuality="2"/>
<reflections faces="6" size="256" forceBilinear="true"/>
<mirrors enabled="true" forceBilinear="true" width="512" height="128"/>
<skidmarks enabled="true"/>
<dynamic_ambient_occ enabled="true"/>
<track_reflections enabled="true"/>
<physics environmentalDamage="true" vehicleDamage="true"/>
<input device_type="auto"/>
<motion enabled="false" ip="127.0.0.1" port="20777" delay="1" extradata="0"/>
</hardware_settings_config>

Also i'm runnin the 180 driver for my card. IF somebody could tell me how to drop the latest one in...i'd appreciate it. I tried and busted the kernel.

---

