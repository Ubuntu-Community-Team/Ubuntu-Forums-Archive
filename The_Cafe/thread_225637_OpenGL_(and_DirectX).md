---
title: "OpenGL (and DirectX)"
date: 2006-07-30
forum: The Cafe
---

### Post by The Noble on 2006-07-30
The next windows OS is going to have DirectX10, which looks like it is going to be spectacular for really high-end games. We are "stuck" with OpenGL (not like that is a bad thing...), so how does OpenGL stack up to DirectX(8 or 9, or 10 if you have the knowledge)? I have not seen many OpenGL games recently, so it is hard to really determine power and functionality (although UT 2007 supposedly uses it). Does anyone have any experience with both to talk about the differences?

My main goal of this thread is a mere discussion of thoughts on OpenGL, and how it will be used in the coming years. This can be a dynamic talk, either stating facts, debating, or just merely contributing beliefs. :D I'm sure that people may have questions on OpenGL, so ask questions if you have any.

My question is: Is OpenGL being worked on actively? Will we see any improvements in the future?

---

### Post by jpkotta on 2006-07-30
I don't know much about OpenGL vs. DirectX.  As far as I know, they're equivalent, except Microsoft controls DirectX (and as usual, is trying to replace the alternative it doesn't control with the one it does).  This podcast is an interview with an OpenGL programmer, and he discusses some of the differences between the two.

[http://www.twit.tv/floss/ryan_gordon](http://www.twit.tv/floss/ryan_gordon)

---

### Post by dtfinch on 2006-07-30
OpenGL is easier to compare with Direct3D rather than DirectX as a whole, since DirectX also has DirectInput, DirectSound, DirectShow, etc.

Doom 3 and Quake 2, 3, and 4 use OpenGL, as do the dozens of popular games using their game engines.

I like OpenGL because it's simple. I've tried learning Direct3D, even bought a book on it, but gave up early on after seeing some of the examples. It requires too much boilerplate coding to create even the simplest of demos.

The only problem is that Microsoft is at war with OpenGL, because it's cross platform. The video drivers (produced by manufacturers) that come with Windows XP are stripped of their OpenGL support, and an extremely slow software renderer is supplied instead. OEM's will go through the trouble of pre-installing the full manufacturers' drivers for customers, but anyone who buys Windows retail will either download and install the manufacturer's drivers themselves, or be fooled into thinking that OpenGL games are broken. In Windows Vista, Microsoft is making it so that OpenGL will have to be implemented as a wrapper over Direct3D, ensuring that it'll be slower.

The OpenGL specification is maintained by SGI and updated every couple years as necessary to keep up with technology. Hardware vendors maintain their own implementations and can add their own extensions to support any features not defined in the latest spec. Direct3D on the other hand comes from a single vendor, but that works pretty well so long as you're using Windows. Vendors have a much easier time (I suspect) developing drivers for DirectX, because they only have to maintain a low level interface, but they're locked into following Microsoft's feature roadmap.

[http://en.wikipedia.org/wiki/Direct3D_vs._OpenGL](http://en.wikipedia.org/wiki/Direct3D_vs._OpenGL)

---

### Post by Kimm on 2006-07-30
As far as I know SDL can use both OpenGL and DirectX.
This means that this is not good bye too crossplatform games with full hardware acceleration. Problem is; most game developers dont use SDL (the only comertial game I know about is Never Winter Nights).
But that doesnt mean that that wount change in the future.

---

### Post by beniwtv on 2006-07-30
OpenGL does - and will ever do - anything that DX can. You know OpenGL is made by SGI. SGI makes supercomputers used for rendering 3D, in movies, 3D animations, etc...

So what's the point? Unless M$ can catch up and conquer the supecomputer market, wich I don't think will happen, OpenGL will be equal o superior then DX.

Furthermore, as somebody pointed already out, OpenGL is easier at some point,  but I can't really see why DX should be superior. For example, go to [http://irrlicht.sf.net](http://irrlicht.sf.net) and download the engine for windows. Try the demo apps with both DX and OpenGL. Pretty the same.

In addidtion, there are much games that use OpenGL. And they can converted to linux games easier than if they were DX games (OpenGL is crossplattform.)

I don't see your point, really. Just IMHO.

---

### Post by NESFreak on 2006-07-30
The ps3 uses openGL. OpenGL is only for grafics so you should (as mentioned above compare openGl vs direct3d and directDraw). Opengl uses plugins wich is why if there is a new tech you dont have to get a new gpu that follows new standarts. So openGL is cheaper and has new tech (like when pixelshaders came out) first.

---

### Post by G Morgan on 2006-07-30
OpenGL and SDL are tremendously flawed in the fact that the worlds greatest marketing machine hates them.

---

### Post by B0rsuk on 2006-07-30
Congratulations, you have been successfully brainwashed by Micro$oft. No, please don't bother backing up your statements.

---

### Post by dio525i on 2006-07-30
> **B0rsuk said:**
> Congratulations, you have been successfully brainwashed by Micro$oft. No, please don't bother backing up your statements.


ROTFLMFAO

---

### Post by forrestcupp on 2006-08-02
> **dio525i said:**
> ROTFLMFAO

Didn't you have time to type the words out?

I could be wrong, but I think Half-life 2 uses opengl, and that is the best game I've ever seen on any platform, graphically.

---

### Post by G Morgan on 2006-08-02
> **B0rsuk said:**
> Congratulations, you have been successfully brainwashed by Micro$oft. No, please don't bother backing up your statements.

I haven't been brainwashed by MS, I correctly identified them as a marketing machine afterall. I like SDL, it lets me play games on Linux.

---

### Post by dio525i on 2006-08-02
> **forrestcupp said:**
> Didn't you have time to type the words out?


who pissed in your coffee?

---

### Post by Jucato on 2006-08-03
Excuse me, but getting back on topic...

I've been silently watching this topic with interest. Recently I've come across  this article, and a particular part startled me, mainly because I didn't know about it:

[http://www.linuxjournal.com/node/1000072](http://www.linuxjournal.com/node/1000072)
> 
 I can't help but wonder if the either Novell or the author is aware of the fact that Microsoft owns the patent on OpenGL. SGI used to own the patent, but Microsoft snagged it in one of the infamous "bail-out" deals Microsoft loves to make with struggling competitors. No doubt Microsoft coveted the patent for OpenGL because it was the only credible competition for DirectX. Should OpenGL-based games ever pose a threat to its PC and Xbox game market strategy, Microsoft now has the ability to cause trouble for the competition. Microsoft has hinted at waging patent wars against Linux, and this may be one that it has in mind.

This is coming from a very famous and (IMHO) credible Linux writer, so it's definitely no FUD from Microsoft.

I can't seem to find any "definitive" statement on the net regarding this. Googling only yields articles that are almost 4 years old. If this were true, that Microsoft owns the OpenGL patent and at the same time owns DirectX, wouldn't that be troublesome for Linux?

---

### Post by G Morgan on 2006-08-03
I was told by a games developer I know that MS own the patent for OpenGL as well. It's a question of the license though surely, if the license grants the right to use then the patent is irrelevant.

Anyway no software patents in the EU so no problem for me.

---

### Post by schurtek on 2006-08-03
Here is the official website for OpenGL... from the guys who invented and keep working on it... problem is Microsoft (shudder) don't want to keep up, so you must download the latest version manually...

[http://www.sgi.com/products/software/opengl/](http://www.sgi.com/products/software/opengl/)

---

### Post by NESFreak on 2006-08-03
how come i never heared of microsoft owning opengl at all?
[http://en.wikipedia.org/wiki/OpenGL_Architecture_Review_Board](http://en.wikipedia.org/wiki/OpenGL_Architecture_Review_Board)
[http://en.wikipedia.org/wiki/Khronos_Group](http://en.wikipedia.org/wiki/Khronos_Group)

---

### Post by jc87 on 2006-08-03
> **forrestcupp said:**
> Didn't you have time to type the words out?

I could be wrong, but I think Half-life 2 uses opengl, and that is the best game I've ever seen on any platform, graphically.

Direct3d unfortunally , but many even better looking than half-life2 use OpenGl , and more will come:rolleyes:

---

### Post by Jucato on 2006-08-03
> **NESFreak said:**
> how come i never heared of microsoft owning opengl at all?
[http://en.wikipedia.org/wiki/OpenGL_Architecture_Review_Board](http://en.wikipedia.org/wiki/OpenGL_Architecture_Review_Board)
[http://en.wikipedia.org/wiki/Khronos_Group](http://en.wikipedia.org/wiki/Khronos_Group)

Me, too. I never knew that until I saw that article by coincidence. That's why I'm looking for confirmation. 

@G Morgan: If MS owns the patent, wouldn't they have the power to change the license later on if the current license proves unfavorable to them?

---

### Post by G Morgan on 2006-08-03
Right firstly I've heard that MS own the patent from another source that I consider knowledgible (like I said the guy is a games dev). That it was confirmed by another person that seems to consider his source as trustworthy I consider that enough to at least give credance to the idea.

As for licensing, it depends on the license. If originally SGI released the source open on a license that permitted patent use royalty free for all time then any code derived from the code on that license would still have all the rights irrespective of the change of ownership. It's like a contract, MS would still be required to uphold old contracts.

My thinking is:
1. MS thought they could close down SDL but failed due to licensing arrangements
2. Irrespective MS bought so they could import code into DX.

Either way I'd have though an alternative would be useful but prehaps people don't consider it a real issue (not to mention that software patents don't exist in most of the world).

---

