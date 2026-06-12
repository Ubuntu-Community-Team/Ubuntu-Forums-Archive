---
title: "no character rendering"
date: 2010-12-26
forum: Wine
---

### Post by thissideup on 2010-12-26
heya.

so, a pretty strange bug is bothering me all day. regardless which game i try to run, no character whatsoever will be rendered. neither the pc nor any npc or mobs (try to battle fiends that way..). everything else runs fine and as expected. also, if the characters are carrying something (like swords), they will fly around, with noone carrying them. 

the strangest thing about it, is that the exact same thing happens regardless of the game. i tested it with prince of persia: warrior within, f.e.a.r. and dragon age: beginning. which, to my knowledge, all run on pretty different engines.

also, i've tried it on the current stable (1.2 afaik) and dev release of wine (1.3.10). i also reinstalled my fglxr-drivers. but nothing's changing.

so, specs-time:
amd phenon II quad-core (2.5 ghz or something?)
ati mobile radeon 5000 hd (i dont know the exact model and fglxrinfo just gives me 5000 series)
4 gig ram
all in a nice low-budget acer notebook.

could it just be the current ati drivers or something? 
well, in any case, looking forward for any advice whatsoever.

cheers!
alex.

---

### Post by qubodup on 2010-12-29
Vampire The Masquerade Bloodlines (Source Engine) won't show character models when shaders are eneabled. When they are disabled (see winecfg configuration below) characters are shown.
[[IMG]http://img402.imageshack.us/img402/2378/201012291458131920x1200.png[/IMG]](http://img402.imageshack.us/i/201012291458131920x1200.png/)
[SIZE="1"]Uploaded with [ImageShack.us](http://imageshack.us)[/SIZE]

Fallout New Vegas unfortunately won't run without shaders. I only see eyes, mouth and headgear.

It seems to be related to radeon/catalyst driver.. :(

What's your driver version?

I'm at 10.12 on Arch Linux.

There seems to be a solution according to [http://appdb.winehq.org/objectManager.php?sClass=version&iId=21692](http://appdb.winehq.org/objectManager.php?sClass=version&iId=21692)

> Solving the missing textures problem
by Coucouf on Tuesday November 9th 2010, 7:05
I had the missing textures bug for characters models on Ubuntu 10.04 with a Radeon HD5770 and the latest Catalyst (10.10) driver.

I tried to install the former Catalyst 10.9 and it solved the problem for me.
It can be downloaded here (yeah, they screwed up their URL):
support.amd.com/us/gpudownload/linux/10-8/Pages/radeon_linux.aspx 
Didn't test yet.

---

### Post by thissideup on 2010-12-29
heya.

yeah, i cant actually test the pixel shaders option just now (could have thought of that myself.. ;P). but i assume it will be the cause of the issue. ive read something about some calls that amd pushes to segments of the graphics card that are faulty with some cards. or something or other.

however, sacrificing hardware accelerated pixel shading is really something i dont really want to have now. 

but yeah, everything seems to point to the graphics driver. maybe some time ill try the older releases, but ill send an email to amd about that anyhow, and after that, i guess its hoping, that they will resolve the issue.

cheers!

---

### Post by qubodup on 2010-12-29
Please let us know of any progress or reply by ati/amd. Perhaps you could post the ticket number (and an email address to use) so that me and lurkers of this forum could try to add more weight to the issue by sending 'fanmail' :)

PS: my gfx card info:
> $ fglrxinfo
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 5700 Series 
OpenGL version string: 4.1.10362 Compatibility Profile Context

---

### Post by marcoil on 2011-01-05
I've had the same problem with other games, non-appearing characters, on my ATI HD5450. I fixed it setting UseGLSL to 'disabled' in the windows registry.

Seems like Wine detects that the card is capable of GLSL but then somehow the driver messes it up, or has a non-compatible implementation of it. Switching back to ARB shaders works for me.

---

### Post by qubodup on 2011-01-05
> **marcoil said:**
> I fixed it setting UseGLSL to 'disabled' in the windows registry.
Thanks for letting us know of the fix! I assume you used following method?
    * Start wine regedit 
    * Create key "HKEY_CURRENT_USER/Software/wine/Direct3D", create string "UseGLSL", set value to "disabled"

For hat games did this fix your problem?

---

### Post by qubodup on 2011-01-15
[CENTER]**[SIZE="7"]Here is the fix![/SIZE]**[/CENTER]
> **qubodup said:**
> 
    * Start **wine regedit** 
    * Create key "**HKEY_CURRENT_USER/Software/wine/Direct3D**", create string "**UseGLSL**", set value to "**disabled**"

Ok, I tested it and it fixed the problem in Drakensang for example. Nice and thanks!

---

### Post by thissideup on 2011-01-16
why yes, that also did the trick for me. 

thanks guys!

---

### Post by yaddoshi on 2011-01-28
Disabling UseGLSL also fixes the same issue in Star Trek Online, but has the unwanted side effect of disabling reflections and lighting effects as well, making the game appear to be running in Low graphics mode.  I didn't buy my Radeon 5670 just to run it in Low graphics mode, I could have done that with my Radeon 2600 and gotten almost the same performance boost.  Bleah.

There is a ticket open about this at AMD here: [http://ati.cchtml.com/show_bug.cgi?id=25](http://ati.cchtml.com/show_bug.cgi?id=25)

At least they are aware at AMD and are working on it, maybe this will be fixed with the next driver release.  In the meantime, has anyone had success by downgrading their drivers to an earlier release?  I'm running Catalyst 11.1 right now (just came out on the 26th) and the problem is still present.

I wouldn't label this issue as solved, or at least not satisfactorily solved anyway.

---

### Post by qubodup on 2011-01-30
@yaddoshi: Thanks for letting us know! I'm curious to see how long it will take for this to get resolved :)

I changed my wording to "fix" :)

---

### Post by yaddoshi on 2011-02-14
It looks like this will be fixed with the next release of Catalyst drivers!  I can't wait until they're available - AMD rocks.  [http://ati.cchtml.com/show_bug.cgi?id=25#c9](http://ati.cchtml.com/show_bug.cgi?id=25#c9)

---

### Post by qubodup on 2011-02-14
awesome!

---

### Post by yaddoshi on 2011-02-17
I upgraded to Catalyst 11.2 - the new drivers were just released on Tuesday.  Sadly, I still need to disable UseGLSL for character models to render.  Bummer.

---

### Post by qubodup on 2011-02-17
> **yaddoshi said:**
> I upgraded to Catalyst 11.2 - the new drivers were just released on Tuesday.  Sadly, I still need to disable UseGLSL for character models to render.  Bummer.

Same here I'm afraid.

---

### Post by def_init_ on 2011-02-28
Here is Jan Lamecki's script which I've just tried and I *finally* have all the textures in New Vegas. If you don't know what to do with it here's the instructions (note, you'll need to grab the fglrx-dev package from your synaptic.)


[LIST=1]
[*]Save code below as "amd-fix.c" in your home folder
[*]copy this and paste to terminal:  gcc -m32 -fPIC -shared -o libAMD-Fix.so amd-fix.c
[*]put this in terminal LD_PRELOAD=/home/**[PATH TO]**libAMD-Fix.so wine C:\\Program\    Files\\Steam\\Steam.exe
[/LIST]


```
#define _GNU_SOURCE (1)
#include <dlfcn.h>
#include <stdio.h>
#include <string.h>
#include <stdint.h>
#include <GL/gl.h>

void *(*_real_glXGetProcAddressARB)(__const GLubyte *procName);
void *glXGetProcAddressARB(const GLubyte *procName) {
    //fprintf(stderr, "JACHOR: glGetProcAddressARB(\"%s\")\n", procName);
    if(procName && strcmp((const char*)procName, "glGetIntegerv")==0) {
        fprintf(stderr, "JACHOR: redirecting glXGetProcAddressARB(\"glGetIntegerv\")\n");
        return glGetIntegerv;
    }
    return _real_glXGetProcAddressARB(procName);
}

extern void *__libc_dlsym (void *handle, __const char *name);
void *dlsym (void *handle, __const char *name) {
    //fprintf(stderr, "JACHOR: dlsym(0x%016llx, \"%s\")\n", (unsigned long long)((uintptr_t)handle), name);
    if(name && strcmp(name, "dlsym")==0) {
        fprintf(stderr, "JACHOR: redirecting dlsym\n");
        return dlsym;
    }
    if(name && strcmp(name, "glXGetProcAddressARB")==0) {
        void *h = __libc_dlsym(handle, "glXGetProcAddressARB");
        if(h && !_real_glXGetProcAddressARB)
            _real_glXGetProcAddressARB = h;
        fprintf(stderr, "JACHOR: redirecting glXGetProcAddressARB\n");
        return glXGetProcAddressARB;
    }
    if(name && strcmp(name, "glGetIntegerv")==0) {
        fprintf(stderr, "JACHOR: redirecting glGetIntegerv\n");
        return glGetIntegerv;
    }
    return __libc_dlsym(handle, name);
}


static void GLAPIENTRY (*_real_glGetIntegerv)( GLenum pname, GLint *params );
static volatile int _was_initialized = 0;

static void _initialize() {
    if(_was_initialized)
        return;
    _real_glGetIntegerv = _real_glXGetProcAddressARB((const GLubyte*)"glGetIntegerv");
    _was_initialized = 1;
}

static void clamp_int(GLint *v, GLint max) {
    if(*v > max)
        *v = max;
}

GLAPI void GLAPIENTRY glGetIntegerv( GLenum pname, GLint *params ) {
    if(!_was_initialized)
        _initialize();

    //fprintf(stderr, "JACHOR: glGetIntegerv(%d, <..>)\n", (int)pname);
    _real_glGetIntegerv(pname, params);

    if(pname == GL_MAX_FRAGMENT_UNIFORM_COMPONENTS) {
        clamp_int(params, 1024);
        fprintf(stderr, "JACHOR: GL_MAX_FRAGMENT_UNIFORM_COMPONENTS: %d\n", *params);
    }
    if(pname == GL_MAX_VERTEX_UNIFORM_COMPONENTS) {
        clamp_int(params, 1024);
        fprintf(stderr, "JACHOR: GL_MAX_VERTEX_UNIFORM_COMPONENTS: %d\n", *params);
    }
    if(pname == GL_MAX_GEOMETRY_UNIFORM_COMPONENTS) {
        clamp_int(params, 1024);
        fprintf(stderr, "JACHOR: GL_MAX_FRAGMENT_UNIFORM_COMPONENTS: %d\n", *params);
    }
}

```

---

### Post by yaddoshi on 2011-03-03
Thank you for posting this, def_init_!

I had a couple errors while trying to compile libAMD-Fix.iso so I had to install the [FONT="Courier New"]mesa-common-dev[/FONT] and [FONT="Courier New"]libc6-dev-i386[/FONT] packages.  Some people may also need to install [FONT="Courier New"]build-essentials[/FONT] if they haven't already.

Also, one other caveat - make sure you include the -m32 flag in the gcc command - I had changed mine to -m64 when I first ran into the compile errors, and Star Trek Online generated preload failed error messages on startup.  I had to recompile before the problem was resolved.

Thanks again!  I finally get to use my birthday present (radeon 5670) to its full potential.  Kudos to you sir!
:biggrin:

(psst...don't forget to reenable UseGLSL for your game)

> **def_init_ said:**
> Here is Jan Lamecki's script which I've just tried and I *finally* have all the textures in New Vegas. If you don't know what to do with it here's the instructions (note, you'll need to grab the fglrx-dev package from your synaptic.)


[LIST=1]
[*]Save code below as "amd-fix.c" in your home folder
[*]copy this and paste to terminal:  gcc -m32 -fPIC -shared -o libAMD-Fix.so amd-fix.c
[*]put this in terminal LD_PRELOAD=/home/**[PATH TO]**libAMD-Fix.so wine C:\\Program\    Files\\Steam\\Steam.exe
[/LIST]

---

