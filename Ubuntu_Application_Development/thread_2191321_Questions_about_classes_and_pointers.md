---
title: "Questions about classes and pointers"
date: 2013-12-02
forum: Ubuntu Application Development
---

### Post by slooksterpsv on 2013-12-02
I'm going through an profiling some of my code cause as it is its taking 10%-15% of my cpu just to run the program. Now I think that may be at 800MHz which would be good considering that's only 80-120mhz total. Here's my questions though:

I have a class called Camera which I use to store cordinate data as well as shift the Camera on a 2D plane. The camera is used to tell where to draw the map or what portion of a map to draw and how to follow the player around on the screen e.g.

Player is always at 320x240 on the screen, but if they go up and there's no more map data player can move all the way to 0,0 or if they go to the bottom right of the map 640,480. Now right now Camera is in a class as I have some functions to pull data from it to use with enemies, tiles, etc. Here's how I'm initializing the camera

Camera* camera = new Camera();

From there on anything that needs to access the camera goes through via pointing to what it needs:

camera->GetX();

I have a feeling this is inefficient and if I need to get data I can pass the address to the camera to pull data for other functions. I think that when creating a new pointer and sending that pointer to another object it's just duplicating the data, e.g. in my enemy class:

Enemy* enemy = new Enemy(camera);

Enemy has a private Camera* camPtr object in it to store information for the camera passed to it. I'm wondering if doing the following would help with CPU and memory efficiency:

Camera camera;
//camera functions whatever I need to call.

Enemy* enemy = new Enemy(&camera);
camPtr = camera;

or
camPtr = &camera;

Am I wrong? Or did I miss something. If it doesn't make sense feel free to ask more questions. The camera class initializes no data, it is just needed to store cordinates and perform some tranformation properties to objects.

---

