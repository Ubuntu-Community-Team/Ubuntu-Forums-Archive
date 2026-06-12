---
title: "Delta3D, DirectX and Linux?"
date: 2009-10-15
forum: The Cafe
---

### Post by Slug71 on 2009-10-15
So why do Linux Distros not include Delta3D by default to give us DirectX for Linux? It seems like a good project that is already widely used and works/has been tested on Windows, Mac OSX and Linux.

Having a DirectX engine for Linux gets spoken about a lot and this seems like the solution yet i havent seen any talk about this project. Its completely open source and licensed under LGPL and GPL.

Would be awesome if Linux Distros could start including this by default and im sure gamers would be very happy too.


I have filed a wishlist bug request for this #452281, so feel free to add to it and you can learn more about Delta3D with the link below.

[http://www.delta3d.org/](http://www.delta3d.org/)

---

### Post by Slug71 on 2009-10-15
Could a mod actually change the title of this thread to "Delta3D, DirectX for Linux"? Pleeeaase? [-o<

---

### Post by cariboo on 2009-10-15
Fixed

---

### Post by Slug71 on 2009-10-15
> **cariboo907 said:**
> Fixed

Thanks cariboo907. :)

---

### Post by JDShu on 2009-10-15
I guess since Delta3D is a developer tool, there is no need to include it in default installations. The people who need it will get it for themselves.

I think I'm missing something, but nothing on the site seems to suggest any relation between Delta3D and DirectX...

---

### Post by qamelian on 2009-10-15
> **JDShu said:**
> I guess since Delta3D is a developer tool, there is no need to include it in default installations. The people who need it will get it for themselves.

I think I'm missing something, but nothing on the site seems to suggest any relation between Delta3D and DirectX...
And you're right. It has nothing to do with DirectX. It's just a cross-platform set of APIs.

---

### Post by Slug71 on 2009-10-15
> **qamelian said:**
> And you're right. It has nothing to do with DirectX. It's just a cross-platform set of APIs.

DirectX is too a set of APIs, D3D being one of them.

A C/P from the site in the 'About' section:

> Delta3D is a widely used and well-supported open source **GAME** and simulation engine. Delta3D is a fully-featured game engine appropriate for a wide variety of uses including training, education, visualization, and entertainment. Delta3D is unique because it offers features specifically suited to the Modeling and Simulation and DoD communities such as High Level Architecture (HLA), After Action Review (AAR), large scale terrain support, and SCORM Learning Management System (LMS) integration.

The Delta3D Engine

Delta3D is an Open Source engine which can be used for games, simulations, or other graphical applications. Its modular design integrates other well-known Open Source projects such as Open Scene Graph, Open Dynamics Engine, Character Animation Library, and OpenAL. Rather than bury the underlying modules, Delta3D integrates them together in an easy-to-use API -- always allowing access to the important underlying components. This provides a high-level API while still allowing the end user the optional, low-level functionality.



---

### Post by j.bell730 on 2009-10-15
[OpenGL]("http://en.wikipedia.org/wiki/OpenGL") is also a set of APIs, but that doesn't mean it's compatible with DirectX.

---

### Post by JDShu on 2009-10-15
I believe Delta3D and DirectX are two different sets of APIs. If you look on the Delta3D website, it actually uses OpenGL for rendering. DirectX is the API that Microsoft introduced to do the same (broadly speaking) job.

---

### Post by Slug71 on 2009-10-15
> **j.bell730 said:**
> [OpenGL]("http://en.wikipedia.org/wiki/OpenGL") is also a set of APIs, but that doesn't mean it's compatible with DirectX.

OpenGL is comparable to D3D, not DirectX.

---

### Post by Xbehave on 2009-10-15
> **Slug71 said:**
> OpenGL is comparable to D3D, not DirectX.
openGL is comparable to directX, it is a direct competitor to directX's graphics APIs (directX also contains other APIs but it is mainly graphics APIs). While the entirety of directX is more comparable to SDL, saying openGL is not comparable to directX makes it sound like you don't really know what your posting about. (edit: actually he does i just don't know how to read)

---

### Post by Slug71 on 2009-10-15
> **Xbehave said:**
> openGL is comparable to directX, it is a direct competitor to directX's graphics APIs (directX also contains other APIs but it is mainly graphics APIs). While the entirety of directX is more comparable to SDL, saying openGL is not comparable to directX makes it sound like you don't really know what your posting about.

C/P from Wikipedia:

OpenGL (Open Graphics Library) is a standard specification defining a cross-language, cross-platform API for writing applications that produce 2D and 3D computer graphics. The interface consists of over 250 different function calls which can be used to draw complex three-dimensional scenes from simple primitives. OpenGL was developed by Silicon Graphics Inc. (SGI) in 1992[1] and is widely used in CAD, virtual reality, scientific visualization, information visualization, and flight simulation. It is also used in video games, **where it competes with Direct3D on Microsoft Windows platforms (see Direct3D vs. OpenGL).** OpenGL is managed by the non-profit technology consortium, the Khronos Group.[/B]

:roll:

---

### Post by JDShu on 2009-10-15
> **Slug71 said:**
> C/P from Wikipedia:

OpenGL (Open Graphics Library) is a standard specification defining a cross-language, cross-platform API for writing applications that produce 2D and 3D computer graphics. The interface consists of over 250 different function calls which can be used to draw complex three-dimensional scenes from simple primitives. OpenGL was developed by Silicon Graphics Inc. (SGI) in 1992[1] and is widely used in CAD, virtual reality, scientific visualization, information visualization, and flight simulation. It is also used in video games, **where it competes with Direct3D on Microsoft Windows platforms (see Direct3D vs. OpenGL).** OpenGL is managed by the non-profit technology consortium, the Khronos Group.[/b]

:roll:

ok, I think I'm detecting some confusion here and "a failure to communicate"

What Xbehave meant by D3D is Delta 3D

The wikipedia article says that openGL competes with Direct3D

Delta 3D and Direct 3D are two different things. Direct 3D is a part of DirectX, which is a Microsoft API. Delta 3D is an open source API that utilized OpenGL. Delta 3D IS NOT Direct3D

Edit: Actually I reread the thread and realized that you probably do understand this, in which case this thread is just a bunch of general confusion :P

---

### Post by Xbehave on 2009-10-15
I think the confusion is because you said D3D which could have meant delta3D, i do apologise as you clearly do know what you are talking about.

openGL is directly comparable with Direct3D (which is also known as directX)
SDL is directly comparable with the directX
delta3D sounds like yet another set of libraries based around openGL looking to compete with directX (confusingly the wiki article calls it a game engine). 

As mentioned before it is not included with ubuntu because like its competitors, its up to game developers to use it.

---

### Post by Bölvaður on 2009-10-15
I think the biggest confusion is that Delta3D does not need to be installed on the user computer. Just on the computer that compiled the game.

---

### Post by keiichidono on 2009-10-15
While we're here, I'd like to take the time to solve some physics questions for you guys. Like, why is the sky blue. Well, it's blue because science said it should be blue. Good day ya'll.

---

### Post by Frak on 2009-10-15
> **Xbehave said:**
> openGL is directly comparable with Direct3D (which is also known as directX)

No it's not. Direct3D has left OpenGL in the dust. It'd be wrong to compare them. Also, DirectX != Direct3D, Direct3D is a component of DirectX. (Notice the X, as in the variable 'x')

---

### Post by Slug71 on 2009-10-15
> **Xbehave said:**
> I think the confusion is because you said D3D which could have meant delta3D, i do apologise as you clearly do know what you are talking about.

Yeh i probably should have been a little more clear about that. Apologies.

> **Xbehave said:**
> openGL is directly comparable with Direct3D (which is also known as directX)

DirectX does NOT = Direct3D. Direct3D is as already mentioned a component(API) of DirectX.
OpenGL is comparable to Direct3D though.

> **Xbehave said:**
> SDL is directly comparable with the directX

Im not sure this is correct either. 
SDL uses DirectX. Or vice versa.

> **Xbehave said:**
> delta3D sounds like yet another set of libraries based around openGL looking to compete with directX (confusingly the wiki article calls it a game engine).

That it is.

---

### Post by Bölvaður on 2009-10-15
> **CalvinB said:**
> While we're here, I'd like to take the time to solve some physics questions for you guys. Like, why is the sky blue. Well, it's blue because science said it should be blue. Good day ya'll.

you might be closer to the answer than you'd think. the sky can be of any colour we desire, just like we can push water down any way we want on north/south pole just by forcing it.
often the sky is black, red, purple, blue, blue/yellow... but if you want pink I guess we can arrange that with some pink screens and many strong search lights.

---

