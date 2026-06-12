---
title: "Games on Linux: Direct X is Evil"
date: 2007-07-02
forum: Ubuntu Gamers Arena
---

### Post by cprofitt on 2007-07-02
I am sure this has been discussed before, but I could not find it in the search.

It appears to me that the reason Linux and Mac-in-toys have no games is that Microsoft was successful in getting developers to use DirectX. This killed the use of OpenGL as the default 3D API in my opinion and made it much more difficult to "port" or "recompile" applications for OSes other than Windows.

My real question is how does this get changed? How does the community start getting game manufactures off the virtual crack called DirectX and back on the wholesome OpenGL (or other API)? I would think this would make it more possible for games to be multi-OS.

Thoughts?

---

### Post by donkyhotay on 2007-07-03
Do the same thing they did, bribe as many software development companies to force their programmers to use openGL instead of directX. Course this requires having more money then microsoft does...

---

### Post by hikaricore on 2007-07-03
Some links of interest:

[http://en.wikipedia.org/wiki/Reality_Lab](http://en.wikipedia.org/wiki/Reality_Lab)
[http://www.steve-lacey.com/blogarchives/2007/01/murky_direct3d.shtml](http://www.steve-lacey.com/blogarchives/2007/01/murky_direct3d.shtml)
[http://en.wikipedia.org/wiki/Comparison_of_Direct3D_and_OpenGL](http://en.wikipedia.org/wiki/Comparison_of_Direct3D_and_OpenGL)

---

### Post by cprofitt on 2007-07-05
> **hikaricore said:**
> Some links of interest:

[http://en.wikipedia.org/wiki/Reality_Lab](http://en.wikipedia.org/wiki/Reality_Lab)
[http://www.steve-lacey.com/blogarchives/2007/01/murky_direct3d.shtml](http://www.steve-lacey.com/blogarchives/2007/01/murky_direct3d.shtml)
[http://en.wikipedia.org/wiki/Comparison_of_Direct3D_and_OpenGL](http://en.wikipedia.org/wiki/Comparison_of_Direct3D_and_OpenGL)

Good links... and confirms that DirectX killed OpenGL -- just not via any shady dealings from Microsoft.

Obviously DirectX has driven the industry to achieve better 3D graphics... but how do we get an API that can be used on Linux or Mac -- is this one area that the open software community just falls down on?

---

### Post by justin whitaker on 2007-07-05
> **PrivateVoid said:**
> Good links... and confirms that DirectX killed OpenGL -- just not via any shady dealings from Microsoft.

Obviously DirectX has driven the industry to achieve better 3D graphics... but how do we get an API that can be used on Linux or Mac -- is this one area that the open software community just falls down on?

Many of the API calls are working on WINE, and the Wine team, with Codeweaver's help, are really getting good at supporting DX9 titles. There is a bit of lag though.

---

### Post by cprofitt on 2007-07-05
Justin:

I agree... I just wish that there was an API that was good that could be used on OSX, Linux or Windows... I think PC gaming would be better if more PCs could be used for gaming than just windows boxes.

With the recent support improving from Nvidia and ATI I am hoping developers might take notice.

---

### Post by compiledkernel on 2007-07-05
It is or has been my understanding that Khronos has been working on the OpenGL API to create a more competitive edge on DX. DX 10's Vista only nature (and the statement by Wine Devs that DX10 is so modular that it can actually be implemented with some level of ease) means that the DX days are probably numbered as the top graphics API of preference. 

[http://www.khronos.org/](http://www.khronos.org/)

---

### Post by cprofitt on 2007-07-06
compliled -- dude that would be awesome; checked the link out and it does indeed look good. I will have to start throwing my weight around (lol) and support these things more. I already got four of the technicians who work with me to convert their home computers to Ubuntu (or at least Ubuntu/WinXP - for gaming).

I had the straw that broke the camels back placed on my back last week and will be switching to Linux (Ubuntu I believe) regardless of some of my concerns -- and will just work through the concerns.

---

### Post by Azrael Nightwalker on 2007-07-15
OpenGL 3.0 target release date is October 2007 so things might change for better pretty soon.
OpenGL 3.0 is said to be comparable with DirectX 10 in terms of 3D functionality.

---

### Post by rocknrolf77 on 2007-07-23
> **Azrael Nightwalker said:**
> OpenGL 3.0 target release date is October 2007 so things might change for better pretty soon.
OpenGL 3.0 is said to be comparable with DirectX 10 in terms of 3D functionality.

You said BETTER didn't you ;)

---

### Post by soxs on 2007-08-22
> **Azrael Nightwalker said:**
> OpenGL 3.0 target release date is October 2007 so things might change for better pretty soon.
OpenGL 3.0 is said to be comparable with DirectX 10 in terms of 3D functionality.
This sounds great!
Can you give me some link/more info?

---

### Post by bvanaerde on 2007-08-22
OpenGL 3.0 is also called OpenGL Longs Peak.
More info can be found on the [OpenGL pipeline newsletters]("http://www.opengl.org/pipeline/").

---

### Post by vexorian on 2007-08-23
projects like SDL must be promoted.

---

### Post by hikaricore on 2007-08-23
> **vexorian said:**
> projects like SDL must be promoted.

Just curious, did you just post a general and vague comment to increase your post count?

---

### Post by vexorian on 2007-08-23
I just tried to replyto the question in the first post, sorry if the quality of my reply was offensive to the staff.

If you really think that post may affect too much the measure of skill post count is, feel free to delete that post, I for some reason don't have rights over my own posts and can't delete it myself.

---

---

### Post by cprofitt on 2007-08-26
Vexorian:

Liked my sig, heh? Nice improvement -- it made me smile.

---

### Post by KingHanco on 2007-09-05
I hate to say this. Direct X is better than SDL. This is why Wine have Direct X and not SDL support. Soon as Wine get to where all games can run on it without any games problems then I will dropping XP right off of my machine. Right now not all games will runs on Wine right. It might takes 10 years or so for Wine runs everything without any problems. Just hope Bill Gates don't shutdown Wine because it runs windows games and Direct X.

---

### Post by cogadh on 2007-09-05
AFAIK, Wine does support SDL, it just passes SDL calls through to the native SDL support in Linux, just like it does with OpenGL. The only reason Wine focuses on DX support is because there is no native DX support in Linux. It has absolutely nothing to do with one being better than the other.

---

### Post by compiledkernel on 2007-09-06
The only reason one might say SDL is of a lesser quality than something like DirectX (even though I firmly believe they are two seperate animals) is because of SDL's age. Its still very new , unlike its two siblings, OpenGL and DirectX (though directx could be considered the unwanted child of the three).

---

