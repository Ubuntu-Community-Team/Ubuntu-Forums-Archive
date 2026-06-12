---
title: "Issues with Blender and Makehuman"
date: 2012-10-02
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by damvcoool on 2012-10-02
Hello all,

I think is great that MakeHuman is now included in the Qualtal repository, however it seems that this build is not compatible with the Blender on the repository for quantal.

When I export a model using the MHX, the problem seems to be that MakeHuman 0.6 exports to blender 2.4 and 2.5 but not 2.6, this is a known issue on Makehuman (See [http://www.makehuman.org/node/241](http://www.makehuman.org/node/241)) so the question is why not include MakeHuman 0.7(SVN).

Also there seems to be a lot of plugings missing in blender, for example i cannot export or import any Collada(dae) file into/out of blender since this plugin is missing. Cycles is missing too.

here is the list of bugs.
[https://bugs.launchpad.net/ubuntu/+source/blender/+bug/1058777](https://bugs.launchpad.net/ubuntu/+source/blender/+bug/1058777)
[https://bugs.launchpad.net/ubuntu/+source/blender/+bug/999024](https://bugs.launchpad.net/ubuntu/+source/blender/+bug/999024)
[https://bugs.launchpad.net/ubuntu/+source/makehuman/+bug/1058767](https://bugs.launchpad.net/ubuntu/+source/makehuman/+bug/1058767)

Temporary workaround for blender use this (actually the workaround maynot work as it seems that this repository does not have blender build for Quantal
[https://launchpad.net/~irie/+archive/blender?field.series_filter=quantal](https://launchpad.net/~irie/+archive/blender?field.series_filter=quantal)

---

