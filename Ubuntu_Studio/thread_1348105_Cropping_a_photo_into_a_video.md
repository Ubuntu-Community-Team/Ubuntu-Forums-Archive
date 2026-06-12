---
title: "Cropping a photo into a video"
date: 2009-12-06
forum: Ubuntu Studio
---

### Post by kafka201 on 2009-12-06
So I was trying to add a photo to a video I think the most famous is adding Leonidas' head to a video which I can't find at the moment.  I'm pretty clueless to editing video but it does seem like this would be a decent start.  Any tutorials someone can point me too?  I've checked google but I'm just coming up with Windows and Mac things, even adding Ubuntu into the search.  

To sum up I just want to add a photo to a video.  The photo will move around in the video.  That's all.

---

### Post by kayosiii on 2009-12-08
Cinelerra supports that via camera automation in the compositor window...
I shall try and track down a tutorial.

---

### Post by VertexPusher on 2009-12-09
Blender can do that too.

Create an empty scene, add a plane, map the photo onto the plane as a texture and turn off shading so that the colors remain unchanged. Add a camera, set it to orthographic mode and make it face the plane. Now you can move the photo around and keyframe its location. Import the scene into the video sequence editor and use it as an overlay for the original video.

---

