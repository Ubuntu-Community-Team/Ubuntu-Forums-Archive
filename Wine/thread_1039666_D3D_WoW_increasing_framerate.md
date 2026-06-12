---
title: "D3D WoW increasing framerate"
date: 2009-01-14
forum: Wine
---

### Post by EnderEcho on 2009-01-14
I'm currently running WoW in D3D mode and I'm only getting 1.1 fps. Its unplayable.

Its better than it was before in opengl mode though the jumbled graphics were indecipherable.

Any suggestions? Everything is running at lowest possible setting.

---

### Post by hikaricore on 2009-01-14
It's your hardware man, please do not make duplicate threads of topics you've already inquired on.

---

### Post by EnderEcho on 2009-01-14
Its not a duplicate thread if its on a different issue. The previous thread was about open gl mode. Now this is D3D. Its not just the hardware either because it seems people have gotten 20-30 FPS on intel cards. 

This is addressing the issue of FPS.

---

### Post by hikaricore on 2009-01-14
Let me be straight with you here.

It's highly unlikely that you'll be able to run WoW at and reasonable framerate with your current Intel integrated chipset.
Intel hardware and drivers are hit and miss.  The hardware often relies too much on directx, and no matter what mode you're
running the game in, Linux is still converting the output to OpenGL.  There is no getting around this and no you can't use
directx under WINE actually it's only API conversion.

As for a duplicate thread, you asked the exact same question in your previous thread making it a repeat post.
If you must make more threads do not ask questions you've already asked.

---

### Post by EnderEcho on 2009-01-14
Did you read the previous thread?

The question I asked was about getting Intel to work in OpenGl and solving a very different issue.

Currently, I am asking a general question about D3D and framerates. You have told me before about my situation with Intel. I appreciate that help. I ended up figuring out how to get the display to work on my own by switching to D3D and tweaking WINE cfg.

No offense, but telling me intel doesnt have good drivers didnt help any. You said I hit a dead end before. Clearly with my progress I have not.

So now basically what you have done with this thread is killed any chance of me getting help with FPS and D3D. 

Maybe there is someone out there who has improved framerate with an intel card. Its unlikely this thread will be of any help to me now that you have made it about reposting. The only way I would get help is if I reposted this thread sans your lack of help. I'm aware of the issues of reposting and as a result I won't. Now the ubuntu forums are dead for me on this issue and I will continue to try and research on my own.

Thanks.

---

### Post by hikaricore on 2009-01-14
I'm not trying to be harsh on ya, but what I'm saying is that even in D3D mode you're using OpenGL.

I don't think your hardware can properly handle OpenGL in a Linux environment with the driver you are using.
Just because you're running the game in D3D mode it doesn't change the fact that Linux does not use DirectX in any way shape or form.

I'm just trying to be direct here with you.

By no means take this as the end word, someone may be able to help you.
I just wanted you to fully understand the situation and why you're having the issue you are.

---

### Post by OrbJinzo on 2009-01-15
like hikaricore its your hardware your not gonna be able to get more then out of your PC. Get over it or reinstall windows. Intel chips are like ATI chipsets they dont run well for gaming in linux

---

### Post by EnderEcho on 2009-01-15
I guess I was confused about how OpenGL and D3D worked in WINE. It sounds like more of an emulation than it claims to be. 

Thanks for the help H.

OrbJinzo I don't see how you felt your post was at all necessary. I didn't realize that these forums were for telling people to get over it or to reinstall windows.

---

### Post by hikaricore on 2009-01-16
The tone and resolution OrbJinzo offered was his own and does not reflect the opinions of Ubuntu Forums.

I have issued him a warning.

---

### Post by OrbJinzo on 2009-01-16
I apologize for my tone but you just reached your limit with your hardware in terms of linux. Intel based video chipsets are meant mainly for windows. As far as i know there is no linux drivers for intel based chipsets.

---

### Post by binbash on 2009-01-16
If you want to play wow on linux, you should go for opengl not d3d

---

### Post by CarpKing on 2009-01-16
> **OrbJinzo said:**
> As far as i know there is no linux drivers for intel based chipsets.

Actually Intel's official Linux drivers are open source, and are generally considered the best, for desktop use at least.  Wine tends to work best on Nvidia, though, and Intel graphics aren't the most powerful to begin with.

---

### Post by EnderEcho on 2009-01-16
Would you be able to point me in the right direction for a good Open source driver for an intel 4500HD chipset?

I run it in D3D because OpenGL has scrambled graphics and I can't resolve it.

It seems there are a lot of different opinions on whether or not intel will actually work for WoW. I would settle for 15 FPS, but rockin 1.1 is just no good.

---

