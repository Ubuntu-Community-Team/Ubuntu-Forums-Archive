---
title: "Blender 2.57b and External renderers HELP Thread"
date: 2011-06-22
forum: Ubuntu Studio
---

### Post by checoimg on 2011-06-22
Hi everyone I started this thread because I've been looking on how to adapt some external rendering programs to Blender 2.57b under Ubuntu Studio Natty amd64.

SO I think many users may like to have the workarounds and tips on how to do this. I still don't have any solutions but here is the ones I will be trying to make to work.

I don't have experience using this Open Source renderers I want to test em any example escenes for Aqsis or Sunflow will be appreciated wich are the ones that  are installed in my computer.

As soon as I get anything on Yafray, Luxrender and integrating this  to Blender 2.57b I will post here.

Of course anyone is welcome to post an answer.

---

### Post by checoimg on 2011-07-03
Regarding Luxrender I fond this thread at Blender community.

[http://www.blender.org/forum/viewtopic.php?t=20260](http://www.blender.org/forum/viewtopic.php?t=20260)

There a user posted two links:

Luxrender forum thread for intallation.

[http://www.luxrender.net/forum/viewtopic.php?f=11&t=4516](http://www.luxrender.net/forum/viewtopic.php?f=11&t=4516)

Luxrender site download section.

[http://www.luxrender.net/en_GB/standalone](http://www.luxrender.net/en_GB/standalone)

---

### Post by checoimg on 2011-07-06
I used : "sudo blender" And voila there was Luxrender I just have to know how to install the tar.bz2 file.

Posted to LQ : [http://www.linuxquestions.org/questions/showthread.php?t=890284&referrerid=600877](http://www.linuxquestions.org/questions/showthread.php?t=890284&referrerid=600877)

---

### Post by Pablo_F on 2011-07-06
Hi, 
> 
I just have to know how to install the tar.bz2 file.

Did you follow the instructions here?

[http://www.luxrender.net/wiki/index.php?title=LuxBlend_2.5_installation_instructions](http://www.luxrender.net/wiki/index.php?title=LuxBlend_2.5_installation_instructions)

To extract the files, right button on the compressed file.
To copy the luxrender folder to the destination directory, you must do it as administrator. You can copy it graphically if you launch "gksudo nautilus".

Note that the destination directory in those instructions (/usr/lib/blender/scripts/addons) could be wrong. 

Do in a terminal:

sudo updatedb
(wait...)
locate blender | less

to figure out the right location. This could be:

/usr/share/blender/2.57/scripts/addons/

or similar.

Cheers, Pablo

---

### Post by checoimg on 2011-07-07
Thanks Pablo! let me get to work on that now. i have been working other ways like running from terminal it said it was looking for luxrender ion the tmp/luxrender folder but from there I could only render the geometry with gray materials. When I get back home I'll finish reading the guide and execute the steps.

---

### Post by checoimg on 2011-07-11
> **Pablo_F said:**
> Hi, 


Did you follow the instructions here?

[http://www.luxrender.net/wiki/index.php?title=LuxBlend_2.5_installation_instructions](http://www.luxrender.net/wiki/index.php?title=LuxBlend_2.5_installation_instructions)

To extract the files, right button on the compressed file.
To copy the luxrender folder to the destination directory, you must do it as administrator. You can copy it graphically if you launch "gksudo nautilus".

Note that the destination directory in those instructions (/usr/lib/blender/scripts/addons) could be wrong. 

Do in a terminal:

sudo updatedb
(wait...)
locate blender | less

to figure out the right location. This could be:

/usr/share/blender/2.57/scripts/addons/

or similar.

Cheers, Pablo

I don't see installatoin instruction for Luxrender itself in order to get Luxblend to work along with Luxrender.

---

### Post by Pablo_F on 2011-07-13
Hi, 

Honestly, I don't use blender so I can't even tell the difference between luxrender and luxblend. Anyway, this is from the lux-v08 README file:

> Help, questions, troubleshooting:
--------------------------------
If you encounter any problems or have questions regarding LuxRender or 
LuxBlend, please visit our forums at [http://www.luxrender.net/forum](http://www.luxrender.net/forum) and 
don't hesitate to ask if your problem isn't addressed already. And don't 
miss the wiki ([http://www.luxrender.net/wiki](http://www.luxrender.net/wiki)) with its many useful 
documentation.

Cheers, Pablo

---

### Post by checoimg on 2011-07-13
> **Pablo_F said:**
> Hi, 

Honestly, I don't use blender so I can't even tell the difference between luxrender and luxblend. Anyway, this is from the lux-v08 README file:



Cheers, Pablo

he difference is that luxblend is an scene exporter to use what is done inside of blender. 

Thank you for your attention Pablo I haven't much time to work on this cause it's working in windows so I just use it there.

---

### Post by gabrielaca on 2011-07-14
checoimg: better try an integrated version of Blender go to [HTML]http://www.graphicall.org/[/HTML] and on the top rigth select your OS (check on the penguin for ubuntu) and if 32 or 64 bits, then also check blender and yes thats rigth LUXRENDER, and you get at least 45 diferent version, flavours and truncks, i recomend fishes releases they are very stable (cycles is a expermental internal blender renderer) this [HTML]http://www.graphicall.org/59[/HTML] release  is fresh 2 days ago; happy blending and luxrendering,:popcorn:

---

### Post by mateoarmenta on 2011-07-18
Hello,
I am also having a lot of problems trying to integrate an external renderer (in this case yafaray) with Blender.

Finally, I downloaded a complete package (Blender 2.58+Yafaray) from Graphicall.

I`ve got two problems:
The executable ("blender", with a diamond shaped icon) won`t execute. I double click on it and nothing happens. I have the "allow execute file as program" tick on. If uncheck it, an error message will come stating that the file cant be opened as it is not a folder. But with the tick in place, nothing happens.

Second, in case I get the executable file to execute, what can I do to "install install" it? I mean, for it to appear in the Applications lenses, etc... like if it is a normal program installed through a .deb file. I wouldn`t like to look for the folder and double click the executable everytime I want to run Blender and Yafaray.

Thanks for your help,

---

### Post by gabrielaca on 2011-07-19
mateoarmenta, i am having the same trouble here w/yafaray, but found this 

```
sudo apt-get install libpython3.2 libopenal1 libfftw3-3 libilmbase6 libopenexr6 libavformat52 libavdevice52 libswscale0
```

havent tried yet, maybe tonite, ill let you know if this works.

_i am on Ubuntu 11.04 64b_ my avatar is wrong.

---

### Post by mateoarmenta on 2011-07-19
Thanks for your tip Gabriel. However, the terminal tells me that I already have all those packages, and that they are all up to date. 

It`s nice to hear I am not the only one having problems with this executable.

Quite difficult getting Yafaray in Blender 2.5, eh?

I am also running Ubuntu 11.04, but the 32bit version.

Regards,

PD: OK, the "config" file, in the "2.58" folder, opens up! Blender look quite different from the regular 2.5 Blender though, like if it has been themed . Yafaray appears in Addons/Render, and it is checked. It doesn`t appear though in the Render Engine selection tab though.

---

### Post by mateoarmenta on 2011-07-21
I`ve got another build from Graphicall (Blender + Luxblend) working succesfully, so it the other build (the one with yafaray) has got some type of problem....

A shame really, as I think it is the only Ubuntu+Blender+Yafaray build in Graphicall. I`ll have to wait until somebody else uploads another Yafaray build.

Regards,

---

### Post by checoimg on 2011-07-21
> **mateoarmenta said:**
> I`ve got another build from Graphicall (Blender + Luxblend) working succesfully, so it the other build (the one with yafaray) has got some type of problem....

A shame really, as I think it is the only Ubuntu+Blender+Yafaray build in Graphicall. I`ll have to wait until somebody else uploads another Yafaray build.

Regards,

Thank you mateoarmenta, would you please post the link to download?

---

### Post by checoimg on 2011-07-21
> **mateoarmenta said:**
> Thanks for your tip Gabriel. However, the terminal tells me that I already have all those packages, and that they are all up to date. 

It`s nice to hear I am not the only one having problems with this executable.

Quite difficult getting Yafaray in Blender 2.5, eh?

I am also running Ubuntu 11.04, but the 32bit version.

Regards,

PD: OK, the "config" file, in the "2.58" folder, opens up! Blender look quite different from the regular 2.5 Blender though, like if it has been themed . Yafaray appears in Addons/Render, and it is checked. It doesn`t appear though in the Render Engine selection tab though.

Reainstall the Packages with synaptic sometimes it downloads some more bits. ;)

---

### Post by mateoarmenta on 2011-07-21
I don't quite remember the specific build I downloaded... maybe this one? 

[http://www.graphicall.org/60](http://www.graphicall.org/60)

The thing is that after installing this build you`ve got to install Luxrender separately (the build only includes LuxBlend) Then, under LuxRender settings, in Blender, you have to provide the correct path to the standalone LuxRender folder for the program to work.

Have in mind that the OpenCL version of LuxRender does not work in my computer; I used the No OpenCL version instead. Luxrender takes an awful amount of time to render... maybe it is because I am using a No OpenCL version? (I've got no idea what OpenCL is) 

I`ll wait for a Yafaray build I think, and in the mean time continue to use Sketchup+ Vray.

Regards,

---

### Post by mateoarmenta on 2011-08-13
I haven't been able to get Yafaray to work with Blender 2.5x.....

I`ve been thinking, does somebody know if Blender 2.5+ Yafaray are being included in the official Oneiric Ocelot repositories (the 11.04 repositories include Blender 2.49+ Yafray... i`ve got no idea if Yafray works there) ? At this point, I think that is my only chance of ever getting Yafaray to work in my computer.

Regards,

---

### Post by ursaminor on 2011-08-18
> **mateoarmenta said:**
> I haven't been able to get Yafaray to work with Blender 2.5x.....

I`ve been thinking, does somebody know if Blender 2.5+ Yafaray are being included in the official Oneiric Ocelot repositories (the 11.04 repositories include Blender 2.49+ Yafray... i`ve got no idea if Yafray works there) ? At this point, I think that is my only chance of ever getting Yafaray to work in my computer.

Regards,

Check [http://www.graphicall.org/]("http://www.graphicall.org/") for a Blender/Yafaray build - Blender and Yafaray have been combined into one package for easy install and use.

---

### Post by gabrielaca on 2011-08-20
ok guys, i was having all the troubles we where talking about in past posts, but i came to a solver solution, cant remember how i got there, within graphicall.org, and it all came down to _*dependencies*_, A LOT of dependencies, i installed them all and now every night build, flavor or trunk works just fine for me (sorry havent tried yafaray yet) but it works just fine with the rest.

```
sudo apt-get install scons g++ build-essential yasm gettext libx11-dev libxi-dev libsndfile1-dev libpng12-dev libfftw3-dev libgl1-mesa-dev libopenexr-dev libopenjpeg-dev zlib1g-dev libopenal-dev libalut-dev libvorbis-dev libjpeg62-dev libglu1-mesa-dev libsdl-dev libfreetype6-dev libsdl1.2-dev libtiff4-dev libsamplerate0 libsamplerate0-dev libavdevice-dev libtheora-dev libavformat-dev libavutil-dev libavcodec-dev libjack-dev libpython3.1 libogg-dev libfaac-dev libfaad-dev libswscale-dev libx264-dev libmp3lame-dev freeglut3-dev libglew1.5-dev libboost-all-dev subversion python3.1-dev python3.1-dbg
```


i meant Libs.

---

### Post by gabrielaca on 2011-08-20
more news, happy to report that yafaray IS working fine, get the build [HTML]http://www.graphicall.org/megasoft78[/HTML] you need from him, also install the libs that mentioned there, and youre ready RAY.

just tried myself and it works.

---

### Post by checoimg on 2011-09-01
> **gabrielaca said:**
> more news, happy to report that yafaray IS working fine, get the build [HTML]http://www.graphicall.org/megasoft78[/HTML] you need from him, also install the libs that mentioned there, and youre ready RAY.

just tried myself and it works.

Thank you very much Gabrielaca! :D

I haven't had the time to test it for I still don't know how to setup the materials. I will see how to get some tutorials about it or get some scene samples like Test257 from blender website and when I do I will post the images.

Well I will go now to the Yafray website to seee if they have a Test file for mterials. See you soon guys! Keep Ubuntuing!

---

### Post by checoimg on 2011-09-01
Got it! there's an examples page on the site.

[http://www.yafaray.org/download/examples]("http://www.yafaray.org/download/examples")

I'm downloading and then I will do the tests.

Keep Ubuntuing!

---

### Post by checoimg on 2011-09-15
just gray colors ... :(

---

### Post by checoimg on 2011-09-15
It was easy to get here. :) Just some time for the render. The sphere was gray and the scene is from a link posted before.

[IMG]http://i1085.photobucket.com/albums/j436/checo_evo/yafray_mat_ex.jpg[/IMG]

---

