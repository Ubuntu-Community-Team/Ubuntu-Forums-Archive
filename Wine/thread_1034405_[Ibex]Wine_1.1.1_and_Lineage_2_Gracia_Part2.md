---
title: "[Ibex]Wine 1.1.1 and Lineage 2 Gracia Part2"
date: 2009-01-08
forum: Wine
---

### Post by lon_ton_sai_vat on 2009-01-08
I'm playing on a private server. I'm using wine version 1.1.1 ( I used 1.1.12 before but i got the wineserver crash error ) .

I got a critical error window when run l2.exe using wine . Here is the message :

```
2009.1.8 21:57:16
OS : Windows XP 5.1 (Build: 2600)
CPU : AuthenticAMD Unknown processor @ 3012 MHz with 1897MB RAM
Video : Direct3D HAL (0)
PosCode : LS1:0:0:0 1/0

You have triggered a bug in the DirectX 9.0 runtime. Please install DirectX 8.1b (or later) for a fix. See Release Notes for instructions on how to obtain it.
IsShadow=0,PrimitiveType=0,IndexBuffer=0x9E334D0,Base=0,Min=0,Max=65364,First=0,NumPrimitives=115776

History: FD3DRenderInterface::DrawPrimitive <- ATerrainInfo::Render <- this=Lobby01.TerrainInfo0 <- RenderTerrain <- RenderLevel <- FLevelSceneNode::Render <- FPlayerSceneNode::Render <- UGameEngine::Draw <- UWindowsViewport::Repaint <- UWindowsClient::Tick <- ClientTick <- UGameEngine::Tick <- UpdateWorld <- MainLoop


```

What should I do now ? Please help me. I'm playing at revlineage2.com

Thank you very much.

---

### Post by lon_ton_sai_vat on 2009-01-08
Please, anybody help me :(

---

### Post by orlox on 2009-01-09
It seems you need some tweaks to get it going. Check out on appdb:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14365]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=14365")

---

### Post by Largaroth on 2009-01-12
Up ! ^^'. I'm having trouble with Lineage II aswell, I've got Wine 1.1.12 because when I try to configure 1.1.11 (before installation) it tells me I'm missing Xlib/Xfree86 i think.

But the problem im having might be really easy to solve... Basically, when I try to install the game, it prompts me for disc0 :/ (though it's Lineage C5 Blood Oath I'm trying to install)
Also, when I try unzipping C5 and CT2 (Gracia part 2) I get an error : null :S any suggestions ?

---

### Post by smo0th on 2009-01-18
lon_ton_sai_vat and Largaroth,

I second olrox's suggestion, search on [http://appdb.winehq.org/](http://appdb.winehq.org/) for the lineage version you are using and follow their howto, I use gracia 2 and installed the tweaked system from [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=14365"), still I cannot play in every server but there are some servers in which I can play at full. I'm still looking for answers on how to play in any server, so if you find something please post back :)

---

### Post by Ryuki_NdranC on 2009-01-19
> **smo0th said:**
> lon_ton_sai_vat and Largaroth,

I second olrox's suggestion, search on [http://appdb.winehq.org/](http://appdb.winehq.org/) for the lineage version you are using and follow their howto, I use gracia 2 and installed the tweaked system from [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=14365"), still I cannot play in every server but there are some servers in which I can play at full. I'm still looking for answers on how to play in any server, so if you find something please post back :)

Is that "tweaked system folder" just for the server promoted there? Or it should work for most private servers?

Any other place where i can get this system folder because the download link is down :/

Thx in advance :)

---

### Post by smo0th on 2009-01-23
I have tested it in private servers and succeeded in one Gracia 2 server and one Interlude server, but there were others where I couldn't pass the server selection screen, so it depends on how the private server is configured, or we should apply different patches/configurations depending on the server :shock:

---

