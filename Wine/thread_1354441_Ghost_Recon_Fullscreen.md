---
title: "Ghost Recon Fullscreen?"
date: 2009-12-13
forum: Wine
---

### Post by Spectre5 on 2009-12-13
I just installed Ghost Recon on WINE and the installation went perfectly.  However, when I start the game, it shows up in a small 640x480 window.  I've tried changing the wine config settings for graphics among other settings, but it still shows up as a tiny window.  I have changed the resolution in-game, tried maximizing the window, turning compiz off, and setting various values for the emulate a virtual desktop setting (including turning it off).

Nothing seems to have had any effect on game and it always shows up as 640x480.  How can I run a game in fullscreen?  I've installed Urban Terror (native installation) and it runs in full screen just fine when I start the executable.

Thanks!

---

### Post by Spectre5 on 2009-12-13
Ok...some improvement.  I was just looking at the starting menu which does stay tiny as mentioned.  But if I actually start a mission, then the in-game res goes up to whatever it set as the in-game resolution (the window re-sizes to 800x600 or 1024x768 or whatever.  However - it is still not fullscreen - what do I need to do to get full screen?

---

### Post by beastrace91 on 2009-12-13
Wine version, video card, and gfx driver version?

Also just so I'm clear is [this](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3666) the Ghost Recon you are referring to?

Regards,
~Jeff

---

### Post by R0CKY44 on 2009-12-14
The starting menu is hard coded to 640x480, there's nothing you can do about that.

Open options.xml in the root folder and you'll see a fullscreen tag, check it is set correctly.

---

### Post by Spectre5 on 2009-12-15
> **beastrace91 said:**
> Wine version, video card, and gfx driver version?

Also just so I'm clear is [this](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3666) the Ghost Recon you are referring to?

Regards,
~Jeff

Sorry - I should have included that information in the my post, I feel like an idiot.  And yes - that is the ghost recon I'm referring to.

Wine: 1.1.31 (the wine1.2 package from the repos)
Video Card: nVidia 9500GT with 185.18.36 drivers

---

### Post by Spectre5 on 2009-12-15
> **R0CKY44 said:**
> The starting menu is hard coded to 640x480, there's nothing you can do about that.

Open options.xml in the root folder and you'll see a fullscreen tag, check it is set correctly.

Yes - the starting menu stays 640x480 and you're right - there is nothingI can do about it (as far as I can tell).  When I go into a game though, then the window increases to whatever resolution I hat set in the game - i.e. 800x600 or 1024x768, etc.  But it doesn't go full screen.

In the options.xml, I have the Fullscreen value set to true (see code below).  I've also tried changing the video resolution and bit depth.
```

	<Graphics>
		<FullScreen>TRUE</FullScreen>
		<VideoResolution Width = "1280" Height = "1024" BitDepth = "16"/>
		<ShowFrameRate>FALSE</ShowFrameRate>
		<UsePrimaryDisplay>FALSE</UsePrimaryDisplay>
		<UseDisplayDeviceGuid>FALSE</UseDisplayDeviceGuid>
		<DisplayDeviceGuid>{00000000-0000-0000-0000-000000000000}</DisplayDeviceGuid>
		<CompressTextures>TRUE</CompressTextures>
		<HumanShadowDetail>1</HumanShadowDetail>
		<VehicleShadowDetail>1</VehicleShadowDetail>
		<BulletHoleMax>100</BulletHoleMax>
		<Gamma>0.500000</Gamma>
		<DefaultMipMapping>FALSE</DefaultMipMapping>
		<MipMapLODBias>-0.500000</MipMapLODBias>
		<ShowDeadBodies>TRUE</ShowDeadBodies>
		<CharVertexWeight>TRUE</CharVertexWeight>
		<ParticleDetail>2</ParticleDetail>
		<UITextureDetail>2</UITextureDetail>
		<LevelTextureDetail>2</LevelTextureDetail>
		<CharacterTextureDetail>2</CharacterTextureDetail>
		<EffectTextureDetail>2</EffectTextureDetail>
		<ZBufferBits>24</ZBufferBits>
		<TreeModelDetail>HIGH</TreeModelDetail>
		<CharacterModelDetail>HIGH</CharacterModelDetail>
	</Graphics>

```

Thanks for the ideas- any others?  Also, why is that the main menu cannot be made full screen?  I'm just curious, since it doesn't really matter anyways.

---

### Post by Soulcage on 2009-12-15
Is emulate virtual desktop enabled? You will need to close all windows programs after you turn it off (wineserver -k).

---

### Post by Spectre5 on 2009-12-15
> **Soulcage said:**
> Is emulate virtual desktop enabled? You will need to close all windows programs after you turn it off (wineserver -k).

YA, I've tried it with virtual desktop enabled and disabled.

---

