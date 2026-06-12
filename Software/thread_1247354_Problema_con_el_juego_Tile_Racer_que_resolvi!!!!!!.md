---
title: "Problema con el juego Tile Racer que resolvi!!!!!!!"
date: 2009-08-22
forum: Software
---

### Post by Kondorfire on 2009-08-22
Es que el juego Tile Racer me hacia fallar el puntero del mouse, sabia que era problema de configuracion de pantalla del juego pero al hacer los cambios no lograba llegar al boton de "save" para aplicar los cambios ya que el puntero no llegaba abajo hasta el boton!!!!!!!
Logre solucionarlo mediante un archivo .cfg que consegui en otro foro del juego.
Solo hay que armar un archivo con extension .cfg y llamarlo "tileracer"
Aca coloco el contenido:
> <GameConfig>
    <Video>
        <Renderer name="OpenGL Rendering Subsystem" />
        <Resolution value="800 x 600" />
        <ColourDepth value="32" />
        <Aspect name="4:3" value="1.33333" />
        <AA value="2" />
        <Fullscreen enable="true" />
        <VSync enable="false" />
    </Video>
    <Graphics>
        <Texture quality="2" />
        <Vegetation enable="true">
            <Grass density="0.565934" />
            <Tree density="0.666" />
        </Vegetation>
        <Shadow enable="true" quality="1" />
        <HDR enable="true" fading="60" />
        <MotionBlur enable="false" />
        <AdvancedSky enable="false" />
        <LightMaps enable="true" />
    </Graphics>
    <Audio enable="true" volume="0.626374">
        <Sounds enable="true" volume="0.582418" />
        <Music enable="true" volume="0.587912" />
    </Audio>
    <Input>
        <Player>
            <Accelerate type="1" data="200" />
            <Brake type="1" data="208" />
            <Left type="1" data="203" />
            <Right type="1" data="205" />
            <Handbrake type="1" data="57" />
            <ChangeCamera type="1" data="46" />
            <ResetCar type="1" data="20" />
        </Player>
        <General>
            <ResetGame type="1" data="19" />
        </General>
    </Input>
    <Resources file="resources_high.cfg" />
</GameConfig>

Luego el archivo lo colocan en " /home/nombreusuario/.TileRacer/0.7"
y arrancan el juego.
Este problema solo pasa si tenes resolucion de 800x600.
Espero les sirva!
Kondor!

---

