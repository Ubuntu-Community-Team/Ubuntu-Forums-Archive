---
title: "openshot does not find blender"
date: 2013-12-14
forum: Ubuntu Studio
---

### Post by edfast on 2013-12-14
Hello guys, I wonder if anyone else out there has this same problem... Trying to add a 3D title to my openshop project, the 3D editor warns that it cannot open/find Blender. The path to Blender given in preferences is simply 'blender', so I try switching to '/usr/bin/blender' but just get another error message: 'No frame was found in the output from Blender'. Now, how should I interpret that, let alone do with it?

So how do you other aspiring, or seasoned, editors manage?

---

### Post by graemeleigh333 on 2014-08-06
have exactly this problem myself. did anyone resilve this issue?

---

### Post by JoeDaddy on 2015-01-03
Found this on another site and it worked for me.  Very simple solution!  "I'm using Ubuntu 14.04.1 and needed to change the location of blender  from the default of 'blender' to '/usr/bin/blender' since this is the  path used to access blender.  **From a terminal screen type 'which  blender' (omitting quotes)** will display the path to the blender  executable.**  Enter the** **entire output line including the / at the  beginning into the Blender location line of preferences.**" Thanks to [rdgreenlaw (rgreenlaw)]("https://launchpad.net/%7Ergreenlaw") at [https://answers.launchpad.net/openshot/+question/249837](https://answers.launchpad.net/openshot/+question/249837)

---

