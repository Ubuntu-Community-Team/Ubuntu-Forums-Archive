---
title: "Dynamic library inconsistencies with OpenGL/C++ &amp; nVidia &amp; freeglut"
date: 2014-10-11
forum: Ubuntu Application Development
---

### Post by guidry2 on 2014-10-11
I am using Ubuntu 14.04 with nVidia Driver installed.
When I try to run the very basic GL tutorial.
And build it with **g++ -Wall -std=c++0x -o "tutorial"  "tutorial.cpp" -lglut -lGLEW -lGL** 


    #include <string>
    #include <GL/gl.h>
    #include <GL/glut.h>
    
    static void displayFunc(void){
        glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);
        glutSwapBuffers();
    }
    
    int main(int argc,char **argv){ 
        std::string nimportequoi;
    
        glutInit(&argc, argv);
        glutInitDisplayMode(GLUT_RGBA | GLUT_DOUBLE | GLUT_DEPTH);
    
        if(glutCreateWindow("") == 0) return 1;
    
        glutDisplayFunc(displayFunc);
        glutMainLoop();
        return 0;
    }


Then the error message occured:

    Inconsistency detected by ld.so: dl-version.c: 224: _dl_check_map_versions: Assertion `needed != ((void *)0)' failed!

There are quite a few people using Ubuntu 14.04 withe NV driver installed.

This problem has been existed from quite a long time.

For a long term service version, it a shame to have such basic bug not resolved.

And this gives some many users and developers headaches.

When could this bug be resolved?

Is it too hard for Ubuntu team to resolve this "hard" problem?

How should we confirm ourselves to invest time and energy on Ubuntu apps  developing?
A lot of people are losing patience.

You can find more problems like this in this tutorial series, start from Tutorial 4,
when freeglut is with c++ std :

OpenGL Step by Step : 
[http://ogldev.atspace.co.uk/index.html](http://ogldev.atspace.co.uk/index.html)

Bug since 2013-11-06, almost a year ago!!!!! 
   See:

[Dynamic library inconsistencies with OpenGL/C++][1]


  [1]: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-319/+bug/1248642](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-319/+bug/1248642)


ps.
OpenGL Step by Step's  tutorial 03 is no problem while tutorial 04 onward are:

    ldd tutorial03 
        linux-gate.so.1 =>  (0xb7739000)
        libglut.so.3 => /usr/lib/i386-linux-gnu/libglut.so.3 (0xb76d9000)
        libGLEW.so.1.10 => /usr/lib/i386-linux-gnu/libGLEW.so.1.10 (0xb766b000)
        libGL.so.1 => /usr/lib/nvidia-331/libGL.so.1 (0xb7566000)
        libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xb73b6000)
        libX11.so.6 => /usr/lib/i386-linux-gnu/libX11.so.6 (0xb7282000)
        libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xb723c000)
        libXi.so.6 => /usr/lib/i386-linux-gnu/libXi.so.6 (0xb722b000)
        libXxf86vm.so.1 => /usr/lib/i386-linux-gnu/libXxf86vm.so.1 (0xb7224000)
        libnvidia-tls.so.331.38 => /usr/lib/nvidia-331/tls/libnvidia-tls.so.331.38 (0xb7220000)
        libnvidia-glcore.so.331.38 => /usr/lib/nvidia-331/libnvidia-glcore.so.331.38 (0xb4fdc000)
        libXext.so.6 => /usr/lib/i386-linux-gnu/libXext.so.6 (0xb4fc9000)
        libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xb4fc4000)
        /lib/ld-linux.so.2 (0xb773a000)
        libxcb.so.1 => /usr/lib/i386-linux-gnu/libxcb.so.1 (0xb4fa1000)
        libXau.so.6 => /usr/lib/i386-linux-gnu/libXau.so.6 (0xb4f9d000)
        libXdmcp.so.6 => /usr/lib/i386-linux-gnu/libXdmcp.so.6 (0xb4f96000)

    ldd tutorial04
        linux-gate.so.1 =>  (0xb77c2000)
        libglut.so.3 => /usr/lib/i386-linux-gnu/libglut.so.3 (0xb7762000)
        libGL.so.1 => /usr/lib/nvidia-331/libGL.so.1 (0xb765e000)
        libstdc++.so.6 => /usr/lib/i386-linux-gnu/libstdc++.so.6 (0xb7574000)
        libgcc_s.so.1 => /lib/i386-linux-gnu/libgcc_s.so.1 (0xb7557000)
        libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xb73a7000)
        libX11.so.6 => /usr/lib/i386-linux-gnu/libX11.so.6 (0xb7273000)
        libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xb722d000)
        libXi.so.6 => /usr/lib/i386-linux-gnu/libXi.so.6 (0xb721b000)
        libXxf86vm.so.1 => /usr/lib/i386-linux-gnu/libXxf86vm.so.1 (0xb7215000)
        libnvidia-tls.so.331.38 => /usr/lib/nvidia-331/tls/libnvidia-tls.so.331.38 (0xb7211000)
        libnvidia-glcore.so.331.38 => /usr/lib/nvidia-331/libnvidia-glcore.so.331.38 (0xb4fcd000)
        libXext.so.6 => /usr/lib/i386-linux-gnu/libXext.so.6 (0xb4fba000)
        libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xb4fb4000)
        /lib/ld-linux.so.2 (0xb77c3000)
        libxcb.so.1 => /usr/lib/i386-linux-gnu/libxcb.so.1 (0xb4f92000)
        libXau.so.6 => /usr/lib/i386-linux-gnu/libXau.so.6 (0xb4f8e000)
        libXdmcp.so.6 => /usr/lib/i386-linux-gnu/libXdmcp.so.6 (0xb4f87000)

After comparing the two, I guess, the main culprits maybe libstdc++ or libgcc which makes the system to look up libGL.so in the   /usr/lib/i386-linux-gnu/mesa folder which owns the  same hierarchy /usr/lib/i386-linux-gnu/, and then mistakenly complain two version of GL libs coexist. 

When will the issue "Dynamic library inconsistencies with OpenGL/C++" be resolved?

---

### Post by TheFu on 2014-10-11
Did you follow the solution in the bug?

```
export LD_PRELOAD=/usr/lib/x86_64-linux-gnu/mesa/libGL.so.1

```

For developers, this sort of thing is extremely common.

---

### Post by guidry2 on 2014-10-12
Hi~
Yes, I've tried export LD_PRELOAD=/usr/lib/x86_64-linux-gnu/mesa/libGL.so.1  you mentioned.
but that yields to Segfault, Mesa's libGl isn't compatable with my nVidia 331 driver.
So I finally copy my nVidia 331's  libGL.so to /usr/lib/i86-linux-gnu/mesa/ and replace the mesa's libGL.so.2 
and that  get the problem around in my computer.
But if I want to my CAI program to be distributed to my students whose vidio cards would vary. How can I build my 3D CAI app and
have that app able to run on every student's Ubuntu 14.04 Desktop? Elementary students are not able to use bash commands to fine-tune
the running enviroment.  So how? Thank you!
Regards,
Bill

---

