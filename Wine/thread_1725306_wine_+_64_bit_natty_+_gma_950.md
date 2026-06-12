---
title: "wine + 64 bit natty + gma 950"
date: 2011-04-09
forum: Wine
---

### Post by thgergo on 2011-04-09
I have a dell d620 laptop, intel gma 950 in it. Firstly native linux games like tuxkart is working like a charm with it. But with wine, it just falling back to mesa software rasterizer. To sum up, after a day I figured out whats the problem, wine tries to load 64bit dri libraries, but it fails. When I copy the contents of /usr/lib32/dri to /lib/lib64/dri, GPU accelerated rendering with wine begins to work, but obviously native 64bit applications give up working:)
I have to mention I use this ppa [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu), to get the latest intel drivers. I think its not an issue, because before I have added this ppa, same problems occured, it has falled back to software renderer.

And here comes my second problem:
I used to try world of warcraft with this configuration, with direct3d mode. Currently its very slow, its around 5-10 max fps, its approx the third performance in windows xp. So I have tried to switch to opengl mode, just like in my desktop pc with an nvidia card, but it simply crashes out at startup. I have read that, the current mesa intel driver is not handling very well the opengl extensions, so I have googled how to disable some of them. So I added a new key to HKEY_CURRENT_USER\Software\Wine\OpenGL, a DisabledExtensions with GL_ARB_fragment_program value. I have do this my simply copying the names from "glxinfo" output. So finally I got it work, more than double fps as it was in directx mode. The problem with this, it still crashes out within a minute, so I think I have to explore more disabling more openGL extensions :/
Anyone have tried this?

---

### Post by VonSpyder on 2011-09-13
are you able to run opengl with your gma950?

---

### Post by thgergo on 2011-10-20
Yes, I was able to run it with opengl mode. It seemed, when the game loads many textures things etc, it had simply crashed out. In very basic wilderness areas it even seemed stable. Perhaps it tried to allocate more than the GMA-s reservable ~224MB ram?
I have tested it again, I had same results opengl mode today, but the direct3D mode fails to run.

---

