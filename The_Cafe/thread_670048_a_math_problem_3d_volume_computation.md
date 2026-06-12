---
title: "a math problem: 3d volume computation"
date: 2008-01-17
forum: The Cafe
---

### Post by nephritiri on 2008-01-17
i came here to hear your opinions and suggestions and for your help.
owww... im nver good in math...

this may be more mathematical than ubuntu-ish... i need your help.

im currently developing a program to render a volume from a sequence of binary 2D images. i use C++ and a class library we use in school for computer graphics.

what im doing in 3d rendering is voxel-based.i use space carving algo. i am now able to render the volume but one of my main goals is this: compute the volume of the original object through those 2D input images.

iv researched about the calibration in this kind of processing but im all tangled up. i admit that im nver good in math.

the idea is, if 1 voxel is 1cm^3, and if the total of voxels are 500, that means the 3d object ive rendered is 500cm^3.

but it was just based on the images and the volume iv rendered, how will i transform that to the real world? (true volume)

one more thing,the orig dimensions of the imgs are 640x480. but coz i only hav limited comp. resources (single-core,512mb ram),i scaled them down to 267x200. with the same ratio of 1.35.

so, iv scaled the images down... 1 voxel in 267x200 is how many voxels in 640x480? is it 2.4? (640/267, 480/200)

so, if i hav 500 voxels in 267x200, is it equivalent to 1200 voxels in 640x480?

then... if it is (if it is...), i have 1200 voxels...1200cm^3
what if i precomputed the real world object and it has a dimension of(in cm) w=16, h=11, d=31...a volume of 5,456 cm^3... then what? how can i transform computation from those voxels to real world? how will i know that im right?

will it be right to set 1 voxel to 1 cm^3? and so, if it is, i have a ratio of 4.55 (5456/1200)--ratio of real world and images?

oh no... am i making any sense?pls..help me.

---

### Post by red_Marvin on 2008-01-17
If you have the real volume of the object and the amount of voxels you can get the the volume of each voxel easily:
x amount of voxels result in y volume
1 voxel result in ? volume.

(Actual calculation left as an exercice to the reader as I suspect this is homework, but it should help some)

Note that this only works if rounding error when converting from real world object to bitmaps is neglible.

---

### Post by nephritiri on 2008-01-17
given the V real object is 5456 cm3, and a total of 1200 voxels,

1200 voxels result in 5456 cm3 in the real world
therefore,
the volume of 1 voxel is 4.55 cm3 (5456/1200) ?
and 1200 voxels x 4.55 cm3 result in almost 5460 cm3. am i ryt?

---

### Post by red_Marvin on 2008-01-17
That is correct.

---

